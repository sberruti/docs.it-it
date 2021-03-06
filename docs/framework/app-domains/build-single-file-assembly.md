---
title: 'Procedura: compilare un assembly a file singolo .NET Framework'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: af1bfb89b01a316a858cbb45bf19a26a16d90016
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119942"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>Procedura: compilare un assembly a file singolo .NET Framework

Un assembly su singolo file, che rappresenta il tipo di assembly più semplice, contiene le informazioni e l'implementazione relative al tipo, oltre al [manifesto dell'assembly](../../standard/assembly/manifest.md). È possibile usare i compilatori della riga di comando o Visual Studio per creare un assembly a file singolo destinato al .NET Framework. Per impostazione predefinita, il compilatore crea un file di assembly con estensione *exe* .

> [!NOTE]
> È possibile usare Visual Studio per C# e Visual Basic solo per creare assembly con un singolo file. Per creare assembly con più file, è necessario usare i compilatori della riga di comando o Visual C++.

Le procedure seguenti illustrano come creare assembly su singolo file usando i compilatori della riga di comando.

## <a name="create-an-assembly-with-an-exe-extension"></a>Creare un assembly con estensione exe

Al prompt dei comandi digitare il seguente comando:

\<*comando compilatore*> \<*nome modulo*>

In questo comando *comando compilatore* è il comando del compilatore per il linguaggio usato nel modulo di codice e *nome modulo* è il nome del modulo di codice da compilare nell'assembly.

Nell'esempio seguente viene creato un assembly denominato *Decode. exe* da un modulo di codice denominato `myCode`.

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Creare un assembly con estensione exe e specificare il nome del file di output

Al prompt dei comandi digitare il seguente comando:

\<*comando compilatore*>  **/out:** \<*nome file*> \<*nome modulo*>

In questo comando *comando compilatore* è il comando del compilatore per il linguaggio usato nel modulo di codice, *nome file* è il nome del file di output e *nome modulo* è il nome del modulo di codice da compilare nell'assembly.

Nell'esempio seguente viene creato un assembly denominato MyAssembly *. exe* da un modulo di codice denominato `myCode`.

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>Creazione di assembly di librerie
 Un assembly di librerie è simile a una libreria di classi. L'assembly contiene tipi a cui altri assembly faranno riferimento, ma non ha alcun punto di ingresso per avviare l'esecuzione.

Per creare un assembly di librerie, digitare il comando seguente al prompt dei comandi:

\<*comando compilatore*>  **-t:library** \<*nome modulo*>

In questo comando *comando compilatore* è il comando del compilatore per il linguaggio usato nel modulo di codice e *nome modulo* è il nome del modulo di codice da compilare nell'assembly. È possibile usare anche altre opzioni del compilatore, ad esempio l'opzione **-out:** .

Nell'esempio seguente viene creato un assembly di libreria denominato *myCodeAssembly. dll* da un modulo di codice denominato `myCode`.

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Vedere anche

- [Creazione di assembly](../../standard/assembly/create.md)
- [Assembly su più file](multifile-assemblies.md)
- [Procedura: compilare un assembly su più file](build-multifile-assembly.md)
- [Programma con assembly](../../standard/assembly/program.md)
