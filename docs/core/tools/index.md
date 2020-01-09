---
title: Strumenti dell'interfaccia della riga di comando di .NET Core
description: Panoramica degli strumenti e delle funzionalità dell'interfaccia della riga di comando di .NET Core.
ms.date: 08/14/2017
ms.openlocfilehash: b3bffb47ff973bd0da90e3f943e817756e563138
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714143"
---
# <a name="net-core-command-line-interface-cli-tools"></a>Strumenti dell'interfaccia della riga di comando di .NET Core

L'interfaccia della riga di comando di .NET Core è una nuova toolchain multipiattaforma per lo sviluppo di applicazioni .NET. È un elemento di base su cui possono essere costruiti altri strumenti di livello più elevato, come gli ambienti di sviluppo integrato (IDE, Integrated Development Environment), gli editor e gli agenti di orchestrazione della compilazione.

## <a name="installation"></a>Installazione di

È possibile usare programmi di installazione nativi o script della shell di installazione:

- I programmi di installazione nativi sono destinati essenzialmente ai computer degli sviluppatori e si avvalgono del meccanismo di installazione nativo di ogni piattaforma supportata, ad esempio i pacchetti DEB in Ubuntu o i bundle MSI in Windows. Questi programmi installano e configurano l'ambiente in modo da poter essere immediatamente usato dallo sviluppatore ma richiedono privilegi amministrativi sul computer. È possibile visualizzare le istruzioni di installazione nel sito Web [.NET Core installation guide](https://aka.ms/dotnetcoregs) (Guida all'installazione di .NET Core).
- Gli script vengono usati principalmente per configurare i server di compilazione o quando si vuole installare gli strumenti senza privilegi amministrativi. Con l'installazione degli script non vengono installati nel computer anche i prerequisiti, che devono essere installati manualmente. Per altre informazioni, vedere l'[argomento di riferimento sugli script di installazione](dotnet-install-script.md). Per informazioni su come configurare l'interfaccia della riga di comando nel server di compilazione di integrazione continua (CI, Continuous Integration), vedere [Uso di .NET Core SDK e dei relativi strumenti in integrazione continua](using-ci-with-cli.md).

Per impostazione predefinita, l'interfaccia della riga di comando viene installata in modalità side-by-side (SxS). Pertanto, in un unico computer possono coesistere più versioni degli strumenti dell'interfaccia della riga di comando. La procedura per determinare la versione usata in un computer in cui sono installate più versioni è illustrata nella sezione [Driver](#driver).

## <a name="cli-commands"></a>Comandi dell'interfaccia della riga di comando

Per impostazione predefinita vengono installati i comandi seguenti:

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Comandi di base**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [build](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migrate](dotnet-migrate.md)
- [clean](dotnet-clean.md)
- [sln](dotnet-sln.md)
- [help](dotnet-help.md)
- [store](dotnet-store.md)

**Comandi per la modifica dei progetti**

- [add package](dotnet-add-package.md)
- [add reference](dotnet-add-reference.md)
- [remove package](dotnet-remove-package.md)
- [remove reference](dotnet-remove-reference.md)
- [list reference](dotnet-list-reference.md)

**Comandi avanzati**

- [nuget delete](dotnet-nuget-delete.md)
- [nuget locals](dotnet-nuget-locals.md)
- [nuget push](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [dotnet install script](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Comandi di base**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [build](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migrate](dotnet-migrate.md)
- [clean](dotnet-clean.md)
- [sln](dotnet-sln.md)

**Comandi per la modifica dei progetti**

- [add package](dotnet-add-package.md)
- [add reference](dotnet-add-reference.md)
- [remove package](dotnet-remove-package.md)
- [remove reference](dotnet-remove-reference.md)
- [list reference](dotnet-list-reference.md)

**Comandi avanzati**

- [nuget delete](dotnet-nuget-delete.md)
- [nuget locals](dotnet-nuget-locals.md)
- [nuget push](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [dotnet install script](dotnet-install-script.md)

---

L'interfaccia della riga di comando adotta un modello di estendibilità che consente di specificare altri strumenti per i progetti. Per altre informazioni, vedere l'argomento [Modello di estendibilità dell'interfaccia della riga di comando di .NET Core](extensibility.md).

## <a name="command-structure"></a>Struttura dei comandi

La struttura dei comandi dell'interfaccia della riga di comando è composta dal [driver ("dotnet")](#driver), dal [comando](#command) e, in alcuni casi, dagli [argomenti](#arguments) e dalle [opzioni](#options). Questo modello può essere osservato nella maggior parte delle operazioni eseguite dalla riga di comando, inclusa la creazione di una nuova app console e la relativa esecuzione dalla riga di comando, come illustrato dai comandi seguenti quando vengono eseguiti da una directory denominata *my_app*:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>Driver

Il driver, denominato [dotnet](dotnet.md), ha due compiti: eseguire un'[app dipendente dal framework](../deploying/index.md) ed eseguire un comando. 

Per eseguire un'applicazione dipendente dal framework, specificare l'app dopo il driver, ad esempio `dotnet /path/to/my_app.dll`. Se si esegue il comando dalla cartella in cui si trova la DLL dell'app, è sufficiente eseguire `dotnet my_app.dll`. Se si vuole usare una versione specifica del runtime .NET Core, usare l'opzione `--fx-version <VERSION>` (vedere il riferimento per il [comando dotnet](dotnet.md)).

Nel momento in cui si fornisce un comando al driver, `dotnet.exe` avvia il processo di esecuzione del comando dell'interfaccia della riga di comando. Ad esempio:

```dotnetcli
dotnet build
```

Come prima operazione, il driver determina la versione dell'SDK da usare. Se non è presente nessuna voce ['global.json'](global-json.md) viene usata la versione più recente disponibile del SDK. Può essere una versione di anteprima o una versione stabile, a seconda di qual è la più recente disponibile nel computer.  Dopo aver determinato la versione del SDK il driver esegue il comando.

### <a name="command"></a>Comando

Il comando esegue un'azione. Ad esempio, `dotnet build` compila il codice. `dotnet publish` pubblica il codice. I comandi vengono implementati come un'applicazione console usando una convenzione `dotnet {command}`.

### <a name="arguments"></a>Argomenti

Gli argomenti passati alla riga di comando sono gli argomenti per il comando richiamato. Quando si esegue `dotnet publish my_app.csproj`, ad esempio, l'argomento `my_app.csproj` indica il progetto da pubblicare e viene passato al comando `publish`.

### <a name="options"></a>Options

Le opzioni passate alla riga di comando sono le opzioni per il comando richiamato. Quando si esegue `dotnet publish --output /build_output`, ad esempio, l'opzione `--output` e il relativo valore vengono passati al comando `publish`.

## <a name="migration-from-projectjson"></a>Migrazione da project.json

Se si sono usati gli strumenti della Preview 2 per generare progetti basati su *project.json*, consultare l'argomento [dotnet migrate](dotnet-migrate.md) per informazioni sulla migrazione del progetto in MSBuild/ *.csproj* per l'uso con gli strumenti di rilascio. Per i progetti .NET Core creati prima del rilascio degli strumenti della Preview 2, aggiornare manualmente il progetto seguendo le istruzioni disponibili in [Migrazione da DNX all'interfaccia della riga di comando di .NET Core (project.json)](../migration/from-dnx.md) e usare `dotnet migrate` o aggiornare direttamente i progetti.

## <a name="see-also"></a>Vedere anche

- [Repository GitHub dotnet/CLI](https://github.com/dotnet/cli/)
- [.NET Core installation guide](https://aka.ms/dotnetcoregs) (Guida all'installazione di .NET Core)
