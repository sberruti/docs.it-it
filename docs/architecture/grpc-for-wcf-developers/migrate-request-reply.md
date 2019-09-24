---
title: Eseguire la migrazione di un servizio WCF Request/Reply a gRPC-gRPC per sviluppatori WCF
description: Informazioni su come eseguire la migrazione di un semplice servizio request/reply da WCF a gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ac9eecf66a7ac37a1df9714e6383f7eaebae4781
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184309"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>Eseguire la migrazione di un servizio WCF Request/Reply a una RPC unaria gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Questa sezione illustra come eseguire la migrazione di un servizio request/reply di base in WCF a un servizio RPC unario in ASP.NET Core gRPC. Questi servizi sono i tipi di servizio più semplici sia Windows Communication Foundation (WCF) che gRPC, quindi è un ottimo punto di partenza. Dopo la migrazione del servizio, si apprenderà come generare una libreria client dallo stesso `.proto` file per utilizzare il servizio da un'applicazione client .NET.

## <a name="the-wcf-solution"></a>Soluzione WCF

La [soluzione PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) include un semplice servizio di portfolio Request/Reply per scaricare un singolo portfolio o tutti i portafogli per un determinato trader. Il servizio è definito nell'interfaccia `IPortfolioService` con un `ServiceContract` attributo:

```csharp
[ServiceContract]
public interface IPortfolioService
{
    [OperationContract]
    Task<Portfolio> Get(Guid traderId, int portfolioId);

    [OperationContract]
    Task<List<Portfolio>> GetAll(Guid traderId);
}
```

Il `Portfolio` modello è una classe C# semplice contrassegnata con [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), incluso un elenco `PortfolioItem` di oggetti. Questi modelli sono definiti nel `TraderSys.PortfolioData` progetto, insieme a una classe di repository che rappresenta un'astrazione di accesso ai dati.

```csharp
[DataContract]
public class Portfolio
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public Guid TraderId { get; set; }

    [DataMember]
    public List<PortfolioItem> Items { get; set; }
}

[DataContract]
public class PortfolioItem
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public int ShareId { get; set; }

    [DataMember]
    public int Holding { get; set; }

    [DataMember]
    public decimal Cost { get; set; }
}
```

L' `ServiceContract` implementazione usa una classe `DataContract` di repository fornita tramite l'inserimento di dipendenze che restituisce istanze dei tipi.

```csharp
public class PortfolioService : IPortfolioService
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }

    public async Task<Portfolio> Get(Guid traderId, int portfolioId)
    {
        return await _repository.GetAsync(traderId, portfolioId);
    }

    public async Task<List<Portfolio>> GetAll(Guid traderId)
    {
        return await _repository.GetAllAsync(traderId);
    }
}
```

## <a name="the-portfoliosproto-file"></a>File portfolios. proto

Se sono state seguite le istruzioni riportate nella sezione precedente, è necessario disporre di un `portfolios.proto` progetto gRPC con un file simile al seguente.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

Il primo passaggio consiste nel migrare `DataContract` le classi ai rispettivi equivalenti protobuf.

## <a name="convert-the-datacontracts-to-grpc-messages"></a>Convertire i DataContract in messaggi gRPC

La `PortfolioItem` classe verrà prima convertita in un messaggio protobuf, poiché la `Portfolio` classe dipende da essa. La classe è molto semplice e tre delle proprietà sono mappate direttamente ai tipi di dati gRPC. La `Cost` proprietà, che rappresenta il prezzo pagato per le condivisioni di acquisto, `decimal` è un campo e gRPC supporta `float` solo `double` o per i numeri reali, che non sono adatti per la valuta. Poiché i prezzi per le condivisioni variano di un minimo di un centesimo, il costo `int32` può essere espresso come uno dei centesimi.

> [!NOTE]
> Ricordarsi di `camelCase` usare per i nomi di `.proto` campo nel file C# . il generatore di codice li `PascalCase` convertirà in per l'utente e gli utenti di altre lingue ti ringrazieranno per il rispetto dei diversi standard di codifica.

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 shareId = 2;
    int32 holding = 3;
    int32 costCents = 4;
}
```

La `Portfolio` classe è leggermente più complessa. Nel codice WCF, lo sviluppatore usava un oggetto `Guid` per la `TraderId` proprietà e contiene un oggetto `List<PortfolioItem>`. In protobuf, che non dispone di un tipo di `UUID` prima classe, è necessario usare `string` un oggetto `traderId` per il campo e analizzarlo nel proprio codice. Per l'elenco di elementi, usare la `repeated` parola chiave nel campo.

```protobuf
message Portfolio {
    int32 id = 1;
    string traderId = 2;
    repeated PortfolioItem items = 3;
}
```

Ora che i messaggi di dati sono disponibili, è possibile dichiarare gli endpoint RPC del servizio.

## <a name="convert-the-servicecontract-to-a-grpc-service"></a>Convertire il ServiceContract in un servizio gRPC

Il metodo `Get` WCF accetta due parametri: `Guid traderId` e `int portfolioId`. i metodi del servizio gRPC possono assumere un solo parametro, pertanto è necessario creare un messaggio per contenere i due valori. È pratica comune denominare questi oggetti richiesta con lo stesso nome del metodo e del suffisso `Request`. Anche in `string` questo caso, viene usato `traderId` per il campo `Guid`anziché.

Il servizio può solo restituire un `Portfolio` messaggio direttamente, ma anche in questo caso potrebbe influito sulla compatibilità con le versioni precedenti. È consigliabile definire messaggi `Request` separati e `Response` per ogni metodo in un servizio, anche se molti di essi sono uguali, quindi dichiarare un `GetResponse` messaggio con un solo `Portfolio` campo.

Nell'esempio seguente viene illustrata la dichiarazione del metodo del servizio gRPC `GetRequest` utilizzando il messaggio:

```protobuf
message GetRequest {
    string traderId = 1;
    int32 portfolioId = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

Il metodo `GetAll` WCF accetta un solo parametro, `traderId`, quindi potrebbe sembrare che uno possa specificare `string` come tipo di parametro, ma gRPC richiede un tipo di messaggio definito. Questo requisito consente di applicare la pratica dell'utilizzo di messaggi personalizzati per tutti gli input e output, per la compatibilità con le versioni precedenti.

Anche il metodo WCF ha restituito `List<Portfolio>`un oggetto, ma per lo stesso motivo non consente i tipi di parametro semplici, `repeated Portfolio` gRPC non consentirà come tipo restituito. In alternativa, creare `GetAllResponse` un tipo per eseguire il wrapping dell'elenco.

> [!WARNING]
> Si può essere tentati di creare un `PortfolioList` messaggio o simile e usarlo in più metodi del servizio, ma è necessario resistere a questa tentazione. È impossibile capire in che modo i vari metodi di un servizio possono evolvere in futuro, quindi tenere i messaggi specifici e separati.

```protobuf
message GetAllRequest {
    string traderId = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

Se si salva il progetto con queste modifiche, la destinazione di compilazione gRPC viene eseguita in background e genera tutti i tipi di messaggio protobuf e una classe di base che è possibile ereditare per implementare il servizio.

Aprire la `Services/GreeterService.cs` classe ed eliminare il codice di esempio. A questo punto è possibile aggiungere l'implementazione del servizio portfolio. La classe base generata sarà nello `Protos` spazio dei nomi e verrà generata come classe annidata. gRPC crea una classe statica con lo stesso nome del servizio nel `.proto` file e quindi una classe base con il suffisso `Base` all'interno della classe statica, quindi l'identificatore completo per il tipo di base è `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

La classe base dichiara `virtual` i metodi per `Get` e `GetAll` di cui è possibile eseguire l'override per implementare il servizio. I metodi sono `virtual` `abstract` piuttosto che, se non vengono implementati, il servizio può restituire un codice di stato `Unimplemented` gRPC esplicito, in modo analogo a `NotImplementedException` quanto si C# potrebbe generare un'eccezione nel codice normale.

La firma per tutti i metodi del servizio unario gRPC in ASP.NET Core è coerente. Sono disponibili due parametri: il primo è il tipo di messaggio dichiarato nel `.proto` file e il secondo è un oggetto `ServerCallContext` che funziona in modo analogo all'oggetto `HttpContext` da ASP.NET Core. Esiste infatti un metodo di estensione chiamato `GetHttpContext` `ServerCallContext` sulla classe che è possibile usare per ottenere l'oggetto sottostante `HttpContext`, sebbene non sia necessario usarlo spesso. Si esaminerà `ServerCallContext` più avanti in questo capitolo e anche nel capitolo che illustra l'autenticazione.

Il tipo restituito del metodo è un `Task<T>` oggetto `T` dove è il tipo di messaggio di risposta. Tutti i metodi del servizio gRPC sono asincroni.

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>Eseguire la migrazione della libreria PortfolioData a .NET Core

A questo punto, il progetto richiede il repository di portfolio e i modelli contenuti `TraderSys.PortfolioData` nella libreria di classi nella soluzione WCF. Il modo più semplice per includerli è creare una nuova libreria di classi usando la finestra di dialogo **nuovo progetto** di Visual Studio con il modello *libreria di classi (.NET standard)* o dalla riga di comando usando il interfaccia della riga di comando di .NET Core, eseguendo i comandi seguenti dalla directory che contiene il `TraderSys.sln` file.

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

Una volta creata e aggiunta la libreria alla soluzione, eliminare il file generato `Class1.cs` e copiare i file dalla libreria della soluzione WCF nella cartella della nuova libreria di classi, mantenendo la struttura di cartelle.

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

I file di progetto .NET moderni includono `.cs` automaticamente i file in o nella propria directory, pertanto non è necessario aggiungerli in modo esplicito al progetto. L'unico passaggio rimanente consiste nel rimuovere `DataContract` gli `DataMember` attributi e dalle `Portfolio` classi `PortfolioItem` e in modo che siano classi C# obsolete.

```csharp
public class Portfolio
{
    public int Id { get; set; }
    public Guid TraderId { get; set; }
    public List<PortfolioItem> Items { get; set; }
}

public class PortfolioItem
{
    public int Id { get; set; }
    public int ShareId { get; set; }
    public int Holding { get; set; }
    public decimal Cost { get; set; }
}
```

## <a name="use-aspnet-core-dependency-injection"></a>USA ASP.NET Core inserimento delle dipendenze

A questo punto è possibile aggiungere un riferimento a questa libreria al progetto di applicazione gRPC e `PortfolioRepository` utilizzare la classe usando l'inserimento di dipendenze nell'implementazione del servizio gRPC. Nell'applicazione WCF, l'inserimento delle dipendenze è stato fornito dal contenitore IoC Autofac. ASP.NET Core con inserimento delle dipendenze cotto in; il repository può essere registrato nel `ConfigureServices` metodo `Startup` nella classe.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register the repository class as a scoped service (instance per request)
        services.AddScoped<IPortfolioRepository, PortfolioRepository>();

        services.AddGrpc();
    }

    // ...
}
```

È `IPortfolioRepository` ora possibile specificare l'implementazione come parametro del costruttore `PortfolioService` nella classe, come indicato di seguito:

```csharp
public class PortfolioService : Protos.Portfolios.PortfoliosBase
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }
}
```

## <a name="implement-the-grpc-service"></a>Implementare il servizio gRPC

Ora che i messaggi e il servizio sono stati dichiarati `portfolios.proto` nel file, è necessario implementare i metodi del servizio `PortfolioService` nella classe che eredita dalla classe generata `Portfolios.PortfoliosBase` da gRPC. I metodi vengono dichiarati come `virtual` nella classe di base. Se non si esegue l'override, restituirà il codice di stato "non implementato" di gRPC per impostazione predefinita.

Iniziare implementando il `Get` metodo. L'override predefinito è simile all'esempio seguente:

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

Il primo problema è che `request.TraderId` è una stringa e il servizio richiede un. `Guid` Anche se il formato previsto per la stringa è `UUID`, il codice deve gestire la possibilità che un chiamante abbia inviato un valore non valido e rispondere in modo appropriato. Il servizio può rispondere con errori generando un' `RpcException`eccezione e usare il codice `InvalidArgument` di stato standard per esprimere il problema.

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    return base.Get(request, context);
}
```

Quando è presente un valore `Guid` appropriato per `traderId`, è possibile usare il repository per recuperare il portfolio e restituirlo al client.

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>Eseguire il mapping di modelli interni a messaggi gRPC

Il codice precedente non funziona effettivamente perché il repository restituisce il proprio modello `Portfolio`poco, ma gRPC richiede *il* proprio messaggio `Portfolio`protobuf. Analogamente al mapping di tipi di Entity Framework ai tipi di trasferimento dei dati, la soluzione migliore consiste nel fornire la conversione tra i due. Una posizione ideale per inserire il codice è la classe generata da protobuf, che viene dichiarata come `partial` classe in modo che possa essere estesa.

```csharp
namespace TraderSys.Portfolios.Protos
{
    public partial class PortfolioItem
    {
        public static PortfolioItem FromRepositoryModel(PortfolioData.Models.PortfolioItem source)
        {
            if (source is null) return null;

            return new PortfolioItem
            {
                Id = source.Id,
                ShareId = source.ShareId,
                Holding = source.Holding,
                CostCents = (int)(source.Cost * 100)
            };
        }
    }

    public partial class Portfolio
    {
        public static Portfolio FromRepositoryModel(PortfolioData.Models.Portfolio source)
        {
            if (source is null) return null;

            var target = new Portfolio
            {
                Id = source.Id,
                TraderId = source.TraderId.ToString(),
            };

            target.Items.AddRange(source.Items.Select(PortfolioItem.FromRepositoryModel));

            return target;
        }
    }
}
```

> [!NOTE]
> È possibile usare una libreria come [automapper](https://automapper.org/) per gestire questa conversione dalle classi del modello interno ai tipi protobuf, purché vengano configurate le conversioni di tipi di livello inferiore `string` , `decimal` ad esempio /o `Guid` /e il mapping dell'elenco. `double`

Con il codice di conversione sul posto, `Get` l'implementazione del metodo può essere completata.

```csharp
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}

```

L'implementazione del `GetAll` metodo è simile. Si noti che `repeated` i campi dei messaggi protobuf vengono generati `readonly` come proprietà di `RepeatedField<T>`tipo, quindi è necessario aggiungervi elementi usando il `AddRange` metodo, come nell'esempio seguente:

```csharp
public override async Task<GetAllResponse> GetAll(GetAllRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolios = await _repository.GetAllAsync(traderId);

    var response = new GetAllResponse();
    response.Portfolios.AddRange(portfolios.Select(Portfolio.FromRepositoryModel));

    return response;
}
```

Dopo aver eseguito la migrazione del servizio WCF Request/Reply a gRPC, è possibile esaminare la creazione di un client dal `.proto` file.

## <a name="generate-client-code"></a>Genera codice client

Creare una libreria di classi .NET Standard nella stessa soluzione per contenere il client. Si tratta principalmente di un esempio di creazione di codice client, ma è possibile creare un pacchetto di tale libreria usando NuGet e distribuirla in un repository interno per poter utilizzare altri team .NET. Procedere e aggiungere una nuova libreria di classi .NET standard chiamata `TraderSys.Portfolios.Client` alla soluzione ed eliminare il `Class1.cs` file.

> [!CAUTION]
> Il pacchetto NuGet [Grpc .NET. client](https://www.nuget.org/packages/Grpc.Net.Client) richiede .net core 3,0 (o un altro .NET standard Runtime conforme a 2,1). Le versioni precedenti di .NET Framework e .NET Core sono supportate dal pacchetto NuGet [Grpc. Core](https://www.nuget.org/packages/Grpc.Core) .

In Visual Studio 2019 è possibile aggiungere riferimenti ai servizi gRPC in modo analogo al modo in cui si aggiungono i riferimenti al servizio ai progetti WCF nelle versioni precedenti di Visual Studio. I riferimenti al servizio e servizi connessi vengono tutti gestiti nella stessa interfaccia utente ora, a cui è possibile accedere facendo clic con il pulsante destro `TraderSys.Portfolios.Client` del mouse sul nodo **dipendenze** del progetto in Esplora soluzioni e selezionando **Aggiungi servizio connesso**. Nella finestra degli strumenti visualizzata selezionare la sezione **riferimenti al servizio** e fare clic su **Aggiungi nuovo riferimento al servizio gRPC**.

![Interfaccia utente di Servizi connessi in Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

Individuare `portfolios.proto` il file `TraderSys.Portfolios` nel progetto, lasciare il **tipo di classe da generare** come **client**, quindi fare clic su **OK**.

![Finestra di dialogo Aggiungi nuovo riferimento al servizio gRPC in Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> Si noti che questa finestra di dialogo fornisce anche un campo URL. Se l'organizzazione gestisce una directory di `.proto` file accessibile dal Web, è possibile creare i client semplicemente impostando questo indirizzo URL.

Quando si usa la funzionalità **Aggiungi servizio connesso** di Visual Studio `portfolios.proto` , il file viene aggiunto al progetto di libreria di classi come *file collegato*, anziché copiato, quindi le modifiche apportate al file nel progetto di servizio verranno applicate automaticamente nel progetto client. L' `<Protobuf>` elemento`csproj` nel file ha un aspetto simile al seguente:

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

### <a name="use-the-portfolios-service-from-a-client-application"></a>Usare il servizio portfolio da un'applicazione client

Il codice seguente è un breve esempio di utilizzo del client generato in un'applicazione console. Una esplorazione più dettagliata del codice client di gRPC è alla fine di questo capitolo.

```csharp
public class Program
{
    public async Task Main(string[] args)
    {
        GetResponse response;

        using (var channel = GrpcChannel.ForAddress("https://localhost:5001"))
        {
            var client = new Protos.Portfolios.PortfoliosClient(channel);

            response = await client.GetAsync(new GetRequest
            {
                TraderId = args[0],
                PortfolioId = int.Parse(args[1])
            });
        }

        foreach (var item in response.Portfolio.Items)
        {
            Console.WriteLine($"Holding {item.Holding} of Share ID {item.ShareId}.");
        }
    }
}
```

A questo punto, è stata eseguita la migrazione di un'applicazione WCF di base a un servizio ASP.NET Core gRPC e è stato creato un client per utilizzare il servizio da un'applicazione .NET. Nella sezione successiva si tratteranno i servizi "duplex" più necessari.

>[!div class="step-by-step"]
>[Precedente](create-project.md)
>[Successivo](migrate-duplex-services.md)