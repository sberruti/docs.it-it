---
title: 'Procedura: Installare un assembly nella Global Assembly Cache'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de5ae03ab885c4368e39b6339b5a14d1082e6df5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972935"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Procedura: Installare un assembly nella Global Assembly Cache

Gli assembly condivisi da più applicazioni vengono archiviati nella Global Assembly Cache (GAC). Installare un assembly nella [Global Assembly Cache](gac.md) con uno dei componenti seguenti: 

- [Windows Installer](#windows-installer)
- [Strumento Global assembly cache](#global-assembly-cache-tool)

> [!IMPORTANT]
> È possibile installare solo assembly con nome sicuro in Global Assembly Cache. Per informazioni sulla creazione di un assembly con nome sicuro, vedere [Procedura: Firmare un assembly con un nome sicuro](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), il motore di installazione di Windows, è la scelta consigliata per aggiungere gli assembly alla Global Assembly Cache. Windows Installer ottiene il conteggio dei riferimenti degli assembly nella Global Assembly Cache e altre utili funzionalità. Per creare un pacchetto di installazione per Windows Installer, usare l'[estensione WiX Toolset per Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Global Assembly Cache (strumento)

È possibile utilizzare l' [utilità Global Assembly Cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) per aggiungere assembly al Global assembly cache e visualizzare il contenuto del Global assembly cache.

   > [!NOTE]
   > *Gacutil.exe* è progettato esclusivamente per lo sviluppo. Non usarlo per installare assembly di produzione nella Global Assembly Cache.

La sintassi per usare *gacutil.exe* per installare un assembly nella Global Assembly Cache è la seguente:

```cmd
gacutil -i <assembly name>
```

In questo comando *\<nome assembly>* è il nome dell'assembly da installare nella Global Assembly Cache.

Se *gacutil. exe* non è presente nel percorso di sistema, usare il [prompt dei comandi per gli sviluppatori per la  *\<versione*di Visual Studio >](../tools/developer-command-prompt-for-vs.md).

L'esempio seguente consente di installare un assembly con nome file *hello.dll* nella Global Assembly Cache.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> Nelle versioni precedenti di .NET Framework, l'estensione della shell di Windows *Shfusion.dll* consente di installare gli assembly trascinandoli in Esplora file. A partire da .NET Framework 4, *Shfusion.dll* è obsoleto.

## <a name="see-also"></a>Vedere anche

- [Usare gli assembly e i Global Assembly Cache](working-with-assemblies-and-the-gac.md)
- [Procedura: Rimuovere un assembly dalla Global Assembly Cache](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil. exe (strumento Global assembly cache)](../tools/gacutil-exe-gac-tool.md)
- [Procedura: Firmare un assembly con un nome sicuro](../../standard/assembly/sign-strong-name.md)