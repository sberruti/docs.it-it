---
title: 'Esercitazione: Creare una soluzione .NET Core in macOS usando Visual Studio CodeTutorial: Create a .NET Core solution in macOS using Visual Studio Code'
description: Questo documento specifica i passaggi e il flusso di lavoro da seguire per creare una soluzione .NET Core usando Visual Studio Code.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156595"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a>Esercitazione: Creare una soluzione .NET Core in macOS usando Visual Studio CodeTutorial: Create a .NET Core solution in macOS using Visual Studio Code

Questo documento specifica i passaggi e il flusso di lavoro da seguire per creare una soluzione .NET Core per macOS. Si imparerà come creare progetti, unit test, usare gli strumenti di debug e incorporare librerie di terze parti tramite [NuGet](https://www.nuget.org/).

> [!NOTE]
> In questo articolo [Visual Studio Code](https://code.visualstudio.com) viene usato su macOS.

## <a name="prerequisites"></a>Prerequisites

Installare [.NET Core SDK](https://dotnet.microsoft.com/download). .NET Core SDK include la versione più recente del framework e del runtime di .NET Core.

Installare [Visual Studio Code](https://code.visualstudio.com). Nel corso di questo articolo, si installeranno anche le estensioni di Visual Studio Code che migliorano l'esperienza di sviluppo in .NET Core.

Installare l'estensione Di Visual Studio Code C, aprendo Visual Studio Code e premendo <kbd>Fn</kbd>+<kbd>F1</kbd> per aprire la tavolozza Visual Studio Code. Digitare **ext install** per visualizzare l'elenco delle estensioni. Selezionare l'estensione C#. Riavviare Visual Studio Code per attivare l'estensione. Per altre informazioni, vedere la [documentazione dell'estensione C# di Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="get-started"></a>Introduzione

In questa esercitazione si creeranno tre progetti: un progetto di libreria, i test per tale progetto e un'applicazione console che usa la libreria. È possibile [visualizzare o scaricare l'origine](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) di questo articolo nel repository dotnet/samples su GitHub.You can view or download the source for this article at the dotnet/samples repository on GitHub. Per istruzioni sul download, vedere [Esempi ed esercitazioni](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Avviare Visual Studio Code. Premere <kbd>CTRL</kbd> <kbd>\`</kbd> (il carattere di backquote o backtick) o selezionare **Visualizza** > **terminale** dal menu per aprire un terminale incorporato in Visual Studio Code. È comunque possibile aprire una shell esterna con il comando **Esplora risorse Apri nel prompt dei comandi** **(Apri nel terminale** su macOS o Linux) se si preferisce lavorare al di fuori del codice di Visual Studio.

Iniziare creando un file di soluzione, che funge da contenitore per uno o più progetti .NET Core. Nel terminale, [`dotnet new`](../tools/dotnet-new.md) eseguire il comando per creare una nuova soluzione *golden.sln* all'interno di una nuova cartella denominata *golden*:

```dotnetcli
dotnet new sln -o golden
```

Passare alla nuova cartella *di elementi dorati* ed eseguire il comando seguente per creare un progetto di libreria, che produce due file,*library.csproj* e *Class1.cs*, nella cartella della *libreria:*

```dotnetcli
dotnet new classlib -o library
```

Eseguire [`dotnet sln`](../tools/dotnet-sln.md) il comando per aggiungere il progetto *library.csproj* appena creato alla soluzione:

```dotnetcli
dotnet sln add library/library.csproj
```

Il file *library.csproj* contiene le informazioni seguenti:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

I metodi della libreria serializzano e deserializzano gli oggetti in formato JSON. Per supportare la serializzazione e la deserializzazione JSON, aggiungere un riferimento al `Newtonsoft.Json` pacchetto NuGet. Il comando `dotnet add` aggiunge nuovi elementi a un progetto. Per aggiungere un riferimento a un [`dotnet add package`](../tools/dotnet-add-package.md) pacchetto NuGet, usare il comando e specificare il nome del pacchetto:

```dotnetcli
dotnet add library package Newtonsoft.Json
```

Questa operazione aggiunge `Newtonsoft.Json` e le relative dipendenze al progetto di libreria. In alternativa, modificare manualmente il file *library.csproj* e aggiungere il nodo seguente:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

Esegui [`dotnet restore`](../tools/dotnet-restore.md), ([si veda nota nota](#dotnet-restore-note)) che ripristina le dipendenze e crea una cartella *obj* all'interno della *libreria* contenente tre file, incluso un file *project.assets.json:*

```dotnetcli
dotnet restore
```

Nella cartella *libreria*, rinominare il file *Class1.cs* in *Thing.cs*. Sostituire il codice con il codice seguente:

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

La classe `Thing` contiene un metodo pubblico, `Get`, che restituisce la somma di due numeri, ma esegue tale operazione convertendo la somma in una stringa e deserializzandola in un intero. In questo modo si utilizzano diverse funzionalità moderne [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)di C, ad [ `using static` esempio direttive,](../../csharp/language-reference/keywords/using-static.md)membri con corpo di espressione e [interpolazione di stringhe](../../csharp/language-reference/tokens/interpolated.md).

Compilare la [`dotnet build`](../tools/dotnet-build.md) libreria con il comando . Viene prodotto un file *library.dll* in *golden/library/bin/Debug/netstandard1.4*:

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a>Creare il progetto di test

Compilare un progetto di test per la libreria. Dalla cartella *golden*, creare un nuovo progetto di test:

```dotnetcli
dotnet new xunit -o test-library
```

Aggiungere il progetto di test alla soluzione:

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

Aggiungere un riferimento a progetto alla libreria creata nella sezione precedente, in modo che il compilatore possa trovare e utilizzare il progetto di libreria. Utilizzare [`dotnet add reference`](../tools/dotnet-add-reference.md) il comando:

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

In alternativa, modificare manualmente il file *test-library.csproj* e aggiungere il nodo seguente:

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

Ora che le dipendenze sono state configurate correttamente, creare i test per la libreria. Aprire *UnitTest1.cs* e sostituirne il contenuto con il codice seguente:

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing()
        {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

Si noti che si afferma che il valore 42 non è uguale a 19+23 (o 42) quando si crea lo unit test (`Assert.NotEqual`) per la prima volta, operazione che avrà esito negativo. Un passaggio importante nella creazione di unit test consiste nel creare il test perché abbia esito negativo una volta, per confermarne la logica.

Dalla cartella *golden*, eseguire i comandi seguenti:

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

Questi comandi eseguiranno la ricerca in modo ricorsivo di tutti i progetti per ripristinare le dipendenze, compilarli e attivare il Test Runner xUnit per eseguire i test. Il singolo test non riesce, come previsto.

Modificare il file *UnitTest1.cs* e modificare l'asserzione da `Assert.NotEqual` a `Assert.Equal`. Eseguire il comando seguente dalla cartella *golden* per eseguire nuovamente il test, che questa volta ha esito positivo:

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a>Creare l'applicazione console

L'applicazione console creata tramite i passaggi seguenti stabilisce una dipendenza sul progetto di libreria creato in precedenza e ne richiama il metodo di libreria quando è in esecuzione. Usando questo modello di sviluppo, è possibile vedere come creare librerie riutilizzabili per più progetti.

Creare una nuova applicazione console dalla cartella *golden*:

```dotnetcli
dotnet new console -o app
```

Aggiungere il progetto di applicazione console alla soluzione:

```dotnetcli
dotnet sln add app/app.csproj
```

Creare la dipendenza dalla libreria eseguendo il `dotnet add reference` comando:

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

Eseguire `dotnet restore` ([vedere la nota](#dotnet-restore-note)) per ripristinare le dipendenze dei tre progetti nella soluzione. Aprire *Program.cs* e sostituire il contenuto del metodo `Main` con la riga seguente:

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

Aggiungere due `using` direttive all'inizio del file *Program.cs*:

```csharp
using static System.Console;
using Library;
```

Eseguire il `dotnet run` comando seguente per avviare l'eseguibile, dove l'opzione `-p` in `dotnet run` specifica il progetto dell'applicazione principale. L'applicazione produce la stringa "The answer is 42" (la risposta è 42).

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a>Eseguire il debug dell'applicazione

Impostare un punto di interruzione nell'istruzione `WriteLine` nel metodo `Main`. A tale scopo, premere il tasto <kbd>Fn</kbd>+<kbd>F9</kbd> quando il cursore si trova sulla `WriteLine` riga o facendo clic con il mouse sul margine sinistro sulla riga in cui si desidera impostare il punto di interruzione. Verrà visualizzato un cerchio rosso sul margine accanto alla riga di codice. Quando viene raggiunto il punto di interruzione, l'esecuzione del codice si interrompe *prima* che venga eseguita la riga del punto di interruzione.

Aprire la scheda debugger selezionando l'icona Debug nella barra degli strumenti Codice di Visual Studio, selezionando **Visualizza** > **debug** dalla barra dei menu o utilizzando i tasti di scelta rapida <kbd>&#8679;</kbd> <kbd>&#8984;</kbd> <kbd>D</kbd>:

![Debugger di Visual Studio Code](./media/using-on-macos/visual-studio-code-debugger.png)

Premere il pulsante per la riproduzione per avviare l'applicazione nel debugger. Sono stati creati sia un progetto di test che un'applicazione in questo progetto. Il debugger chiede quale progetto si desidera avviare. Seleziona il progetto "app". L'applicazione inizia l'esecuzione e procede fino al punto di interruzione, in cui si arresta. Eseguire un'istruzione nel metodo `Get` e assicurarsi di aver passato gli argomenti corretti. Confermare che la risposta è 42.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
