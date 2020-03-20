---
title: 'Procedura dettagliata: utilizzo del controllo MaskedTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182070"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="46172-102">Procedura dettagliata: utilizzo del controllo MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="46172-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="46172-103">Le attività illustrate nella procedura dettagliata sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="46172-103">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="46172-104">Inizializzazione <xref:System.Windows.Forms.MaskedTextBox> del controllo</span><span class="sxs-lookup"><span data-stu-id="46172-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
- <span data-ttu-id="46172-105">Utilizzo <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> del gestore eventi per avvisare l'utente quando un carattere non è conforme alla maschera</span><span class="sxs-lookup"><span data-stu-id="46172-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
- <span data-ttu-id="46172-106">L'assegnazione di <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> un tipo <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> alla proprietà e l'utilizzo del gestore eventi per avvisare l'utente quando il valore che sta tentando di eseguire il commit non è valido per il tipoAssigning a type to the property and using the event handler to alert the user when the value they're attempting to commit is not valid for the type</span><span class="sxs-lookup"><span data-stu-id="46172-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="46172-107">Creazione del progetto e aggiunta di un controlloCreating the Project and Adding a Control</span><span class="sxs-lookup"><span data-stu-id="46172-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="46172-108">Per aggiungere un controllo MaskedTextBox al form</span><span class="sxs-lookup"><span data-stu-id="46172-108">To add a MaskedTextBox control to your form</span></span>  
  
1. <span data-ttu-id="46172-109">Aprire il modulo in cui <xref:System.Windows.Forms.MaskedTextBox> si desidera inserire il controllo.</span><span class="sxs-lookup"><span data-stu-id="46172-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2. <span data-ttu-id="46172-110">Trascinare <xref:System.Windows.Forms.MaskedTextBox> un controllo dalla **Casella degli strumenti** al form.</span><span class="sxs-lookup"><span data-stu-id="46172-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3. <span data-ttu-id="46172-111">Fare clic con il pulsante destro del mouse sul controllo e scegliere **Proprietà**.</span><span class="sxs-lookup"><span data-stu-id="46172-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="46172-112">Nella finestra **Proprietà** selezionare la proprietà **Maschera** e fare clic sul pulsante **...** (ellini) accanto al nome della proprietà.</span><span class="sxs-lookup"><span data-stu-id="46172-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4. <span data-ttu-id="46172-113">Nella finestra di dialogo **Maschera di input,** selezionare la maschera **Data breve** e fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="46172-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5. <span data-ttu-id="46172-114">Nella finestra **Proprietà** <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> impostare `true`la proprietà su .</span><span class="sxs-lookup"><span data-stu-id="46172-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="46172-115">Questa proprietà genera un breve e-beep da suonare ogni volta che l'utente tenta di immettere un carattere che viola la definizione della maschera.</span><span class="sxs-lookup"><span data-stu-id="46172-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="46172-116">Per un riepilogo dei caratteri supportati dalla proprietà Mask, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vedere la sezione Osservazioni della proprietà.</span><span class="sxs-lookup"><span data-stu-id="46172-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="46172-117">Avvisare l'utente di errori di input</span><span class="sxs-lookup"><span data-stu-id="46172-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="46172-118">Aggiungere un suggerimento per l'input maschera rifiutato</span><span class="sxs-lookup"><span data-stu-id="46172-118">Add a balloon tip for rejected mask input</span></span>  
  
1. <span data-ttu-id="46172-119">Tornare alla casella degli <xref:System.Windows.Forms.ToolTip> **strumenti** e aggiungere a al form.</span><span class="sxs-lookup"><span data-stu-id="46172-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2. <span data-ttu-id="46172-120">Creare un gestore <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> eventi per <xref:System.Windows.Forms.ToolTip> l'evento che genera l'oggetto quando si verifica un errore di input.</span><span class="sxs-lookup"><span data-stu-id="46172-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="46172-121">Il suggerimento del fumetto rimane visibile per cinque secondi o finché l'utente non fa clic su di esso.</span><span class="sxs-lookup"><span data-stu-id="46172-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="46172-122">Avvisare l'utente di un tipo non valido</span><span class="sxs-lookup"><span data-stu-id="46172-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="46172-123">Aggiungere un suggerimento per tipi di dati non validiAdd a balloon tip for invalid data types</span><span class="sxs-lookup"><span data-stu-id="46172-123">Add a balloon tip for invalid data types</span></span>  
  
1. <span data-ttu-id="46172-124">Nel gestore <xref:System.Windows.Forms.Form.Load> eventi del form <xref:System.Type> assegnare <xref:System.DateTime> un oggetto <xref:System.Windows.Forms.MaskedTextBox> che <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> rappresenta il tipo alla proprietà del controllo:</span><span class="sxs-lookup"><span data-stu-id="46172-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2. <span data-ttu-id="46172-125">Aggiungere un gestore eventi per l'evento <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted>:</span><span class="sxs-lookup"><span data-stu-id="46172-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="46172-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="46172-126">See also</span></span>

- <xref:System.Windows.Forms.MaskedTextBox>
- [<span data-ttu-id="46172-127">Controllo MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="46172-127">MaskedTextBox Control</span></span>](maskedtextbox-control-windows-forms.md)
