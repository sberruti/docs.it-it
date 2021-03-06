---
title: 'Procedura: aprire file con il componente OpenFileDialogHow to: Open files with the OpenFileDialog component'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: ca69de19ab1b9ae387002898145fe99e35a7b6b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182123"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Procedura: aprire file con OpenFileDialogHow to: Open files with the OpenFileDialog

Il <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> componente apre la finestra di dialogo Windows per l'esplorazione e la selezione dei file. Per aprire e leggere i file <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> selezionati, è possibile utilizzare <xref:System.IO.StreamReader?displayProperty=nameWithType> il metodo o creare un'istanza della classe . Negli esempi seguenti vengono illustrati entrambi gli approcci.

In .NET Framework, per <xref:System.Windows.Forms.FileDialog.FileName%2A> ottenere o impostare la <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> proprietà richiede un livello di privilegio concesso dalla classe. Gli esempi <xref:System.Security.Permissions.FileIOPermission> eseguono un controllo delle autorizzazioni e possono generare un'eccezione a causa di privilegi insufficienti se eseguiti in un contesto parzialmente attendibile. Per ulteriori informazioni, vedere [Nozioni di base sulla sicurezza dall'accesso](../../misc/code-access-security-basics.md)di codice .

È possibile compilare ed eseguire questi esempi come app .NET Framework dalla riga di comando di C o Visual Basic. Per ulteriori informazioni, vedere [Compilazione da riga di comando con csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) o [Compilazione dalla riga di comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

A partire da .NET Core 3.0, è anche possibile compilare ed eseguire gli esempi come app Windows .NET Core da una cartella con un nome di * \<cartella* Windows Form .NET Core> file di progetto csproj.

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Esempio: leggere un file come flusso con StreamReaderExample: Read a file as a stream with StreamReader  
  
Nell'esempio riportato <xref:System.Windows.Forms.Button> di seguito <xref:System.Windows.Forms.Control.Click> viene utilizzato <xref:System.Windows.Forms.OpenFileDialog> il <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> gestore eventi del controllo Windows Form per aprire il metodo con il metodo . Dopo che l'utente sceglie **OK**un file e <xref:System.IO.StreamReader> seleziona OK , un'istanza della classe legge il file e ne visualizza il contenuto nella casella di testo del modulo. Per ulteriori informazioni sulla lettura da <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>flussi di file, vedere e .  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Esempio: aprire un file da una selezione filtrata con OpenFile

Nell'esempio seguente <xref:System.Windows.Forms.Button> viene <xref:System.Windows.Forms.Control.Click> utilizzato il gestore eventi del controllo per aprire l'oggetto <xref:System.Windows.Forms.OpenFileDialog> con un filtro che mostra solo i file di testo. Dopo che l'utente sceglie un **OK**file <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> di testo e seleziona OK , il metodo viene utilizzato per aprire il file nel Blocco note.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.OpenFileDialog>
- [Componente OpenFileDialog](openfiledialog-component-windows-forms.md)
