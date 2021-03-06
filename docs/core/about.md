---
title: Informazioni su .NET Core
description: Informazioni su .NET Core.
ms.date: 09/17/2019
ms.openlocfilehash: 89740b67b294650f78cf36361548c2fe24ac80cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147360"
---
# <a name="about-net-core"></a>Informazioni su .NET Core

.NET Core ha le caratteristiche seguenti:

- **Multipiattaforma:** Funziona su [sistemi operativi](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, macOS e Linux.
- **Coerenza in tutte le architetture:** esegue il codice con lo stesso comportamento in molteplici architetture, tra cui x64, x86 e ARM.
- **Strumenti da riga di comando:** include strumenti da riga di comando facili da usare per lo sviluppo locale e in scenari di integrazione continua.
- **Implementazione flessibile:** Può essere incluso nell'app o installato side-by-side (installazioni a livello di utente o di sistema). Può essere usato con i [contenitori Docker](docker/introduction.md).
- **Compatibile:** .NET Core è compatibile con .NET Framework, Xamarin e Mono, tramite [.NET Standard](../standard/net-standard.md).
- **Open source:** la piattaforma .NET Core è open source e usa le licenze MIT e Apache 2. .NET Core è un progetto [.NET Foundation](https://dotnetfoundation.org/).
- **Supportato da Microsoft:** .NET Core è supportato da Microsoft, in base al [Supporto di .NET Core](https://dotnet.microsoft.com/platform/support/policy).

## <a name="languages"></a>Languages

È possibile usare i linguaggi C#, Visual Basic e F# per scrivere librerie e applicazioni per .NET Core. Questi linguaggi possono essere utilizzati nell'editor di testo preferito o nell'ambiente di sviluppo integrato (IDE), tra cui:These languages can be used in your favorite text editor or Integrated Development Environment (IDE), including:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://code.visualstudio.com/download)
- Sublime Text
- Vim

Questa integrazione è fornita, in parte, dai contributori dei progetti [OmniSharp](https://www.omnisharp.net/) e [Ionide.](http://ionide.io)

## <a name="apis"></a>API

.NET Core espone API per molti scenari, tra cui i seguenti:

- Tipi primitivi, <xref:System.Boolean?displayProperty=nameWithType> ad <xref:System.Int32?displayProperty=nameWithType>esempio e .
- Raccolte, ad esempio <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> e <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Tipi di utilità, ad esempio <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> e <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Tipi di dati, ad esempio <xref:System.Data.DataSet?displayProperty=nameWithType> e [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Tipi ad alte prestazioni, ad <xref:System.Numerics.Vector?displayProperty=nameWithType> esempio e [Pipelines](../standard/io/pipelines.md).

.NET Core assicura la compatibilità con le API .NET Framework e Mono tramite l'implementazione della specifica [.NET Standard](../standard/net-standard.md).

## <a name="frameworks"></a>Framework

.NET Core è la base di molteplici framework:

- [ASP.NET Core](/aspnet/core/)
- [Piattaforma UWP (Universal Windows Platform) di Windows 10](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Composizione

.NET Core è costituito dalle parti seguenti:

- Il [runtime di .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), che fornisce un sistema di tipi, il caricamento di assembly, un Garbage Collector, l'interoperabilità nativa e altri servizi di base. Le [librerie del framework .NET Core](https://github.com/dotnet/runtime/tree/master/src/libraries) forniscono tipi di dati primitivi, tipi di composizione dell'app e utilità fondamentali.
- Il [runtime ASP.NET Core](https://github.com/dotnet/aspnetcore), che fornisce un framework per la creazione di moderne applicazioni connesse a Internet basate su cloud, ad esempio app Web, app IoT e back-end per dispositivi mobili.
- L'SDK di [.NET Core](https://github.com/dotnet/sdk) e i compilatori di linguaggio ([Roslyn](https://github.com/dotnet/roslyn) e [F](https://github.com/microsoft/visualfsharp)) che consentono l'esperienza di sviluppo di .NET Core.
- Il [comando dotnet](./tools/dotnet.md), utilizzato per avviare le app .NET Core e i comandi cli. Seleziona il runtime e ospita il runtime, fornisce un criterio di caricamento dell'assembly e avvia app e strumenti.

Questi componenti sono distribuiti nei modi seguenti:

- [Runtime di .NET Core](https://dotnet.microsoft.com/download): include il runtime e le librerie del framework .NET Core.
- [Runtime di ASP.NET Core](https://dotnet.microsoft.com/download): include il runtime e le librerie dei framework ASP.NET Core e .NET Core.
- [.NET Core SDK:](https://dotnet.microsoft.com/download) include l'interfaccia della riga di comando di .NET Core, il runtime ASP.NET Core e il runtime e il framework .NET Core.

### <a name="open-source"></a>Aprire origine

[.NET Core](https://github.com/dotnet/core) è open source ([licenza MIT](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) ed è stato offerto alla [.NET Foundation](https://dotnetfoundation.org) da Microsoft nel 2014. È ora uno dei progetti .NET Foundation più attivi. Può essere utilizzato da individui e aziende, anche per scopi personali, accademici o commerciali. Più aziende utilizzano .NET Core come parte di app, strumenti, nuove piattaforme e servizi di hosting. Alcune di queste società apportano contributi significativi a .NET Core su GitHub e forniscono indicazioni sull'uso del prodotto come parte del gruppo [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Progettato per l'adattabilità

.NET Core è stato creato come un prodotto simile ma unico rispetto ad altri prodotti .NET. È stato progettato per consentire un'ampia adattabilità a nuove piattaforme e carichi di lavoro e ha diverse porte del sistema operativo e della CPU disponibili (e può essere portato a molti altri).

Il prodotto è suddiviso in più parti, in modo che queste possano essere adattate a nuove piattaforme in momenti diversi. Il runtime e le librerie di base specifiche della piattaforma devono essere trasferite come elementi univoci. Le librerie indipendenti dalla piattaforma dovrebbero funzionare in modo indipendente su tutte le piattaforme, per costruzione. C'è una distorsione del progetto verso la riduzione delle implementazioni specifiche della piattaforma per aumentare l'efficienza degli sviluppatori, preferendo il codice C' indipendente dalla piattaforma ogni volta che un algoritmo o un'API può essere implementato in full o in-part in questo modo.

In genere, viene richiesto come implementare .NET Core al fine di supportare più sistemi operativi e se sono disponibili implementazioni separate o viene usata [la compilazione condizionale](https://en.wikipedia.org/wiki/Conditional_compilation). Sono disponibili entrambe le opzioni, con una forte preferenza per la compilazione condizionale.

Si può vedere nel grafico seguente che la stragrande maggioranza delle [librerie .NET Core](https://github.com/dotnet/runtime/tree/master/src/libraries) è codice indipendente dalla piattaforma che viene condiviso tra tutte le piattaforme. Il codice indipendente dalla piattaforma può essere implementato come assembly portabile individuale usato su tutte le piattaforme.

![CoreFX: righe di codice per ogni piattaforma](../images/corefx-platforms-loc.png)

Le implementazioni Windows e Unix hanno dimensioni simili. Windows ha un'implementazione più grande poiché le librerie .NET Core implementano alcune funzionalità solo per Windows, ad esempio [Microsoft.Win32.Registry,](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry) ma non implementa ancora molti concetti solo Unix. Vedrai anche che la maggior parte delle implementazioni Linux e macOS sono condivise tra un'implementazione Unix, mentre le implementazioni specifiche di Linux e macOS sono di dimensioni all'incirca simili.

C'è una combinazione di librerie specifiche della piattaforma e indipendenti dalla piattaforma in .NET Core.There's a mix of platform-specific and platform-neutral libraries in .NET Core. È possibile visualizzarne le caratteristiche in alcuni esempi:

- [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) è specifica della piattaforma. È basata su sottosistemi del sistema operativo, quali ad esempio lo strumento di gestione della memoria e l'utilità di pianificazione thread.
- [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) e [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) sono specifiche della piattaforma, dato che le API di archiviazione e crittografia sono diverse in ogni sistema operativo.
- [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) e [System.Linq](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) sono indipendenti dalla piattaforma, dato che creano e operano su strutture di dati.

## <a name="comparisons-to-other-net-implementations"></a>Confronto con altre implementazioni di .NET

È probabilmente più semplice comprendere le dimensioni e la forma di .NET Core confrontandolo con le implementazioni .NET esistenti.

### <a name="comparison-with-net-framework"></a>Confronto con .NET Framework

La piattaforma .NET è stata annunciata per la prima volta da Microsoft nel 2000 e da quel momento ha conosciuto una notevole evoluzione. .NET Framework è stata l'implementazione di .NET principale prodotta da Microsoft durante questo periodo di quasi due decenni.

Differenze principali tra .NET Core e .NET Framework:

- **I modelli di app** -- .NET Core non supportano tutti i modelli di app di .NET Framework. In particolare non supporta Web Form ASP.NET e ASP.NET MVC, ma supporta ASP.NET Core MVC. E a partire da .NET Core 3.0, .NET Core supporta anche WPF e Windows Form solo in Windows.
- **API**: .NET Core contiene un ampio sottoinsieme della libreria di classi base di .NET Framework, con caratteristiche diverse. I nomi degli assembly sono ad esempio diversi e i membri esposti sui tipi sono diversi nei casi principali. In some cases, these differences require changes to port source to .NET Core. Per ulteriori informazioni, vedere [Analizzatore di portabilità .NET](../standard/analyzers/portability-analyzer.md). .NET Core implementa la specifica API [.NET Standard](../standard/net-standard.md).
- **Sottosistemi**: .NET Core implementa un sottoinsieme dei sottosistemi di .NET Framework, al fine di ottenere un'implementazione più semplice e un modello di programmazione. Ad esempio, la sicurezza dall'accesso di codice (CAS) non è supportata, mentre la reflection è supportata.
- **Piattaforme**: .NET Framework supporta Windows e Windows Server, mentre .NET Core supporta anche macOS e Linux.
- **Open Source**: .NET Core è open source, mentre in [.NET Framework è open source un sottoinsieme di sola lettura](https://github.com/microsoft/referencesource).

Sebbene .NET Core sia univoco e presenti differenze significative rispetto a .NET Framework e ad altre implementazioni di .NET, è semplice condividere il codice tra queste implementazioni, usando tecniche di condivisione di origine o binaria.

Poiché .NET Core supporta l'installazione side-by-side e il relativo runtime è completamente indipendente da .NET Framework, può essere installato nei computer in cui è presente .NET Framework senza alcun problema.

### <a name="comparison-with-mono"></a>Confronto con Mono

[Mono](https://www.mono-project.com/) è l'implementazione multipiattaforma originale di .NET. E 'iniziato come un'alternativa [open-source](https://github.com/mono/mono) a .NET Framework e la transizione a dispositivi mobili di destinazione come dispositivi iOS e Android è diventato popolare. Può essere considerato un duplicato della community di .NET Framework. Il team di progetto Mono si è basato sugli [standard .NET](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) aperti (in particolare ECMA 335) pubblicati da Microsoft per fornire un'implementazione compatibile.

Le differenze principali tra .NET Core e Mono sono:

- **App-models** -- Mono supporta un sottoinsieme dei modelli di app di .NET Framework (ad esempio, Windows Form) e alcuni altri per lo sviluppo per dispositivi mobili (ad esempio, [Xamarin.iOS](https://www.xamarin.com/platform)) tramite il prodotto Xamarin. .NET Core non supporta Xamarin.
- **API**: Mono supporta un [ampio sottoinsieme](http://docs.go-mono.com/?link=root%3a%2fclasslib) delle API di .NET Framework e usa gli stessi nomi di assembly e le stesse caratteristiche.
- **Piattaforme**: Mono supporta molte piattaforme e CPU.
- **Open source**: Mono e .NET Core usano entrambi la licenza MIT e sono progetti di .NET Foundation.
- **Obiettivo**: l'obiettivo principale di Mono negli ultimi anni sono le piattaforme per dispositivi mobili, mentre quello di .NET Core sono i carichi di lavoro cloud e desktop.

## <a name="the-future"></a>il futuro

È stato annunciato che .NET 5 sarà la prossima versione di .NET Core e rappresenta un'unificazione della piattaforma. Il progetto mira a migliorare .NET in diversi modi chiave:

- Produrre un singolo runtime .NET e framework che può essere utilizzato ovunque e che ha un comportamento di runtime uniforme ed esperienze di sviluppatore.
- Espandere le funzionalità di .NET sfruttando al meglio .NET Core, .NET Framework, Xamarin e Mono.
- Compilare il prodotto da un'unica base di codice che gli sviluppatori (Microsoft e la community) possono lavorare ed espandersi insieme e che migliora tutti gli scenari.

Per ulteriori informazioni sulle pianificazioni per .NET 5, vedere Introduzione a [.NET 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/).
