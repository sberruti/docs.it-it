---
title: Abilitare le operazioni di trascinamento della selezione con il controllo RichTextBoxEnable Drag-and-Drop Operations with RichTextBox Control
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
ms.openlocfilehash: 27e5c18598552c465ef17f5e58069bc10e401c09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182356"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Procedura: abilitare operazioni di trascinamento con il controllo RichTextBox Windows Form
Le operazioni di trascinamento della selezione del controllo <xref:System.Windows.Forms.RichTextBox> di Windows Form vengono eseguite gestendo gli eventi <xref:System.Windows.Forms.RichTextBox.DragEnter> e <xref:System.Windows.Forms.RichTextBox.DragDrop> . Quindi, le operazioni di trascinamento della selezione risultano molto semplici con il controllo <xref:System.Windows.Forms.RichTextBox> .  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>Per abilitare le operazioni di trascinamento in un controllo RichTextBox  
  
1. Impostare la proprietà <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> del controllo <xref:System.Windows.Forms.RichTextBox> su `true`.  
  
2. Scrivere il codice nel gestore eventi per l'evento <xref:System.Windows.Forms.RichTextBox.DragEnter> . Usare un'istruzione `if` per assicurarsi che i dati trascinati siano di un tipo accettabile (in questo caso, testo). La proprietà <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> può essere impostata su uno qualsiasi dei valori dell'enumerazione <xref:System.Windows.Forms.DragDropEffects> .  
  
    ```vb  
    Private Sub RichTextBox1_DragEnter(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
          e.Effect = DragDropEffects.Copy  
       Else  
          e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    ```cpp  
    private:  
       void richTextBox1_DragEnter(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          if (e->Data->GetDataPresent(DataFormats::Text))  
             e->Effect = DragDropEffects::Copy;  
          else  
             e->Effect = DragDropEffects::None;  
       }  
    ```  
  
     (Visual Cè e Visual C Inserire il codice seguente nel costruttore del form per registrare il gestore eventi.  
  
    ```csharp  
    this.richTextBox1.DragEnter += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragEnter);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragEnter += gcnew  
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragEnter);  
    ```  
  
3. Scrivere codice per gestire l'evento <xref:System.Windows.Forms.RichTextBox.DragDrop> . Usare il metodo <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> per recuperare i dati trascinati.  
  
     Nell'esempio seguente il codice imposta la proprietà <xref:System.Windows.Forms.RichTextBox.Text%2A> del controllo <xref:System.Windows.Forms.RichTextBox> uguale ai dati trascinati. Se il testo è già presente nel controllo <xref:System.Windows.Forms.RichTextBox> , il testo trascinato viene inserito nel punto di inserimento.  
  
    ```vb  
    Private Sub RichTextBox1_DragDrop(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragDrop  
       Dim i As Int16
       Dim s As String  
  
       ' Get start position to drop the text.  
       i = RichTextBox1.SelectionStart  
       s = RichTextBox1.Text.Substring(i)  
       RichTextBox1.Text = RichTextBox1.Text.Substring(0, i)  
  
       ' Drop the text on to the RichTextBox.  
       RichTextBox1.Text = RichTextBox1.Text + _  
          e.Data.GetData(DataFormats.Text).ToString()  
       RichTextBox1.Text = RichTextBox1.Text + s  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       int i;  
       String s;  
  
       // Get start position to drop the text.  
       i = richTextBox1.SelectionStart;  
       s = richTextBox1.Text.Substring(i);  
       richTextBox1.Text = richTextBox1.Text.Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       richTextBox1.Text = richTextBox1.Text +
          e.Data.GetData(DataFormats.Text).ToString();  
       richTextBox1.Text = richTextBox1.Text + s;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void richTextBox1_DragDrop(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          int i;  
          String ^s;  
  
       // Get start position to drop the text.  
       i = richTextBox1->SelectionStart;  
       s = richTextBox1->Text->Substring(i);  
       richTextBox1->Text = richTextBox1->Text->Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       String ^str = String::Concat(richTextBox1->Text, e->Data  
       ->GetData(DataFormats->Text)->ToString());
       richTextBox1->Text = String::Concat(str, s);  
       }  
    ```  
  
     (Visual Cè e Visual C Inserire il codice seguente nel costruttore del form per registrare il gestore eventi.  
  
    ```csharp  
    this.richTextBox1.DragDrop += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragDrop);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragDrop += gcnew
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragDrop);  
    ```  
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a>Per testare la funzionalità di trascinamento della selezione nell'applicazione  
  
1. Salvare e compilare l'applicazione. Durante l'esecuzione, eseguire WordPad.  
  
     WordPad è un editor di testo installato da Windows che consente operazioni di trascinamento della selezione. È accessibile premendo **Start** , selezionando **Esegui**e digitando `WordPad` nella casella di testo della finestra di dialogo **Esegui** , quindi facendo clic su **OK**.  
  
2. Una volta aperto WordPad, digitare una stringa di testo al suo interno. Usando il mouse, selezionare il testo e quindi trascinarlo sul controllo <xref:System.Windows.Forms.RichTextBox> nell'applicazione Windows.  
  
     Quando si passa il mouse sul controllo <xref:System.Windows.Forms.RichTextBox> (e, di conseguenza, si genera l'evento <xref:System.Windows.Forms.RichTextBox.DragEnter> ), il puntatore del mouse cambia ed è possibile rilasciare il testo selezionato nel controllo <xref:System.Windows.Forms.RichTextBox> .  
  
     Quando si rilascia il pulsante del mouse, il testo selezionato viene rilasciato (ossia, viene generato l'evento <xref:System.Windows.Forms.RichTextBox.DragDrop> ) e viene inserito all'interno del controllo <xref:System.Windows.Forms.RichTextBox> .  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.RichTextBox>
- [Procedura: eseguire operazioni di trascinamento e rilascio tra applicazioni](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [Controllo RichTextBox](richtextbox-control-windows-forms.md)
- [Controlli da utilizzare in Windows Form](controls-to-use-on-windows-forms.md)
