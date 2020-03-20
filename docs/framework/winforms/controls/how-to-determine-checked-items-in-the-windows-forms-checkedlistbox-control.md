---
title: Determinare gli elementi selezionati nel controllo CheckedListBoxDetermine Checked Items in CheckedListBox Control
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 5d93a63e9c1c6aae91ecfe83590c59450a565afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182198"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a><span data-ttu-id="7a038-102">Procedura: rilevare gli elementi selezionati nel controllo CheckedListBox di Windows Form</span><span class="sxs-lookup"><span data-stu-id="7a038-102">How to: Determine Checked Items in the Windows Forms CheckedListBox Control</span></span>
<span data-ttu-id="7a038-103">Quando si presentano dati <xref:System.Windows.Forms.CheckedListBox> in un controllo Windows Form, <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> è possibile scorrere l'insieme <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> archiviato nella proprietà oppure scorrere l'elenco utilizzando il metodo per determinare quali elementi vengono controllati.</span><span class="sxs-lookup"><span data-stu-id="7a038-103">When presenting data in a Windows Forms <xref:System.Windows.Forms.CheckedListBox> control, you can either iterate through the collection stored in the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> property, or step through the list using the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method to determine which items are checked.</span></span> <span data-ttu-id="7a038-104">Il <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metodo accetta un numero di `true` indice `false`dell'elemento come argomento e restituisce o .</span><span class="sxs-lookup"><span data-stu-id="7a038-104">The <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method takes an item index number as its argument and returns `true` or `false`.</span></span> <span data-ttu-id="7a038-105">Contrariamente a quanto ci <xref:System.Windows.Forms.ListBox.SelectedItems%2A> <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> si potrebbe aspettare, le proprietà e non determinano quali elementi vengono controllati; determinano quali elementi sono evidenziati.</span><span class="sxs-lookup"><span data-stu-id="7a038-105">Contrary to what you might expect, the <xref:System.Windows.Forms.ListBox.SelectedItems%2A> and <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> properties do not determine which items are checked; they determine which items are highlighted.</span></span>  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a><span data-ttu-id="7a038-106">Per determinare gli elementi selezionati in un controllo CheckedListBoxTo determine checked items in a CheckedListBox control</span><span class="sxs-lookup"><span data-stu-id="7a038-106">To determine checked items in a CheckedListBox control</span></span>  
  
1. <span data-ttu-id="7a038-107">Scorrere la <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> raccolta, a partire da 0 poiché la raccolta è in base zero.</span><span class="sxs-lookup"><span data-stu-id="7a038-107">Iterate through the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, starting at 0 since the collection is zero-based.</span></span> <span data-ttu-id="7a038-108">Si noti che questo metodo fornisce il numero di articolo nell'elenco degli elementi selezionati, non l'elenco complessivo.</span><span class="sxs-lookup"><span data-stu-id="7a038-108">Note that this method will give you the item number in the list of checked items, not the overall list.</span></span> <span data-ttu-id="7a038-109">Quindi, se il primo elemento dell'elenco non è selezionato e il secondo elemento è selezionato, il codice seguente visualizzerà testo come "Elemento controllato 1 - MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="7a038-109">So if the first item in the list is not checked and the second item is checked, the code below will display text like "Checked Item 1 = MyListItem2".</span></span>  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x < checkedListBox1.CheckedItems.Count ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
       MessageBox.Show(s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x < checkedListBox1->CheckedItems->Count; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - <span data-ttu-id="7a038-110">- oppure -</span><span class="sxs-lookup"><span data-stu-id="7a038-110">or -</span></span>  
  
2. <span data-ttu-id="7a038-111">Eseguire la <xref:System.Windows.Forms.CheckedListBox.Items%2A> raccolta un'istruzione alla volta, a partire <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> da 0 poiché la raccolta è in base zero e chiamare il metodo per ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="7a038-111">Step through the <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, starting at 0 since the collection is zero-based, and call the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method for each item.</span></span> <span data-ttu-id="7a038-112">Si noti che questo metodo vi darà il numero di elemento nell'elenco complessivo, quindi se il primo elemento nell'elenco non è selezionato e il secondo elemento è selezionato, verrà visualizzato qualcosa di simile "Elemento 2 - MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="7a038-112">Note that this method will give you the item number in the overall list, so if the first item in the list is not checked and the second item is checked, it will display something like "Item 2 = MyListItem2".</span></span>  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
    ```  
  
    ```csharp  
    int i;  
    string s;
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7a038-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7a038-113">See also</span></span>

- [<span data-ttu-id="7a038-114">Controlli Windows Form usati per elencare opzioni</span><span class="sxs-lookup"><span data-stu-id="7a038-114">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
