---
title: Collegamento all'origine e librerie .NET
description: Procedure consigliate per l'uso del collegamento all'origine per migliorare il debug per le librerie .NET.
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744543"
---
# <a name="source-link"></a>Collegamento all'origine

Il collegamento all'origine è una tecnologia che consente il debug del codice sorgente degli assembly .NET da NuGet da parte degli sviluppatori. Il collegamento all'origine viene eseguito durante la creazione del pacchetto NuGet e incorpora i metadati di controllo del codice sorgente all'interno degli assembly e del pacchetto. Gli sviluppatori che scaricano il pacchetto e che hanno abilitato il collegamento all'origine in Visual Studio possono eseguire istruzione per istruzione il relativo codice sorgente. Il collegamento all'origine fornisce i metadati di controllo del codice sorgente per creare una straordinaria esperienza di debug.

## <a name="source-link-demo"></a>Demo del collegamento all'origine

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Uso del collegamento all'origine

Le istruzioni per l'uso del collegamento all'origine sono reperibili nel repository GitHub [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md).

È possibile usare [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) per confermare che i metadati di collegamento all'origine siano stati incorporati correttamente nel pacchetto. Controllare `Repository` che i metadati siano presenti con un identificatore di commit e che i file con estensione pdb si trovino con la DLL di ogni destinazione.

![Collegamento di origine in Esplora pacchetti NuGetSource Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Collegamento di origine in Esplora pacchetti NuGetSource Link in NuGet Package Explorer")

✔️ VALUTARE l'uso del collegamento all'origine per aggiungere metadati di controllo del codice sorgente agli assembly e ai pacchetti NuGet.

> [!TIP]
> È possibile migliorare ulteriormente l'esperienza di debug di uno sviluppatore tramite l'aggiunta di attributi del debugger ai tipi in uso.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> può personalizzare la modalità di visualizzazione di una classe o di un campo nelle finestre delle variabili del debugger.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> indica al debugger di eseguire il codice un'istruzione alla volta anziché eseguire un'istruzione nel codice.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> controlla se viene visualizzato un membro nelle finestre delle variabili del debugger.

✔️ VALUTARE la pubblicazione dei file di simboli (`*.pdb`).

> Per ottenere un'esperienza di debug ottimale, la libreria deve pubblicare i file di simboli oltre a usare il collegamento all'origine. Per altre informazioni sui file di simboli e i pacchetti di simboli, vedere [Pacchetti di simboli](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Successivo](dependencies.md)
>[precedente](publish-nuget-package.md)
