---
title: 'Procedura: associare dati al controllo MaskedTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
- data binding [Windows Forms], MaskedTextBox control [Windows Forms]
- MaskedTextBox control [Windows Forms], binding data
ms.assetid: 34b29f07-e8df-48d4-b08b-53fcca524708
ms.openlocfilehash: 0cbb239e24b254c37c453486590185e934adf482
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142173"
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a><span data-ttu-id="cbbd3-102">Procedura: associare dati al controllo MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="cbbd3-102">How to: Bind Data to the MaskedTextBox Control</span></span>
<span data-ttu-id="cbbd3-103">È possibile associare <xref:System.Windows.Forms.MaskedTextBox> dati a un controllo come per qualsiasi altro controllo Windows Form.You can bind data to a control just as you can to any other Windows Forms control.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-103">You can bind data to a <xref:System.Windows.Forms.MaskedTextBox> control just as you can to any other Windows Forms control.</span></span> <span data-ttu-id="cbbd3-104">Tuttavia, se il formato dei dati nel database non corrisponde al formato previsto dalla definizione della maschera, sarà necessario riformattare i dati.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-104">However, if the format of your data in the database does not match the format expected by your mask definition, you will need to reformat the data.</span></span> <span data-ttu-id="cbbd3-105">Nella procedura seguente viene illustrato <xref:System.Windows.Forms.Binding.Format> come <xref:System.Windows.Forms.Binding.Parse> eseguire <xref:System.Windows.Forms.Binding> questa operazione utilizzando gli eventi e della classe per visualizzare campi separati per il numero di telefono e il database delle estensioni telefoniche come un singolo campo modificabile.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-105">The following procedure demonstrates how to do this using the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events of the <xref:System.Windows.Forms.Binding> class to display separate phone number and phone extension database fields as a single editable field.</span></span>  
  
 <span data-ttu-id="cbbd3-106">La procedura seguente richiede l'accesso a un database di SQL Server con il database di esempio Northwind installato.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-106">The following procedure requires that you have access to a SQL Server database with the Northwind sample database installed.</span></span>  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a><span data-ttu-id="cbbd3-107">Per associare dati a un controllo MaskedTextBoxTo bind data to a MaskedTextBox control</span><span class="sxs-lookup"><span data-stu-id="cbbd3-107">To bind data to a MaskedTextBox control</span></span>  
  
1. <span data-ttu-id="cbbd3-108">Creare un nuovo progetto Windows Form.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-108">Create a new Windows Forms project.</span></span>  
  
2. <span data-ttu-id="cbbd3-109">Trascinare <xref:System.Windows.Forms.TextBox> due controlli nel form; nominarli `FirstName` `LastName`e .</span><span class="sxs-lookup"><span data-stu-id="cbbd3-109">Drag two <xref:System.Windows.Forms.TextBox> controls onto your form; name them `FirstName` and `LastName`.</span></span>  
  
3. <span data-ttu-id="cbbd3-110">Trascinare <xref:System.Windows.Forms.MaskedTextBox> un controllo nel form; denominarlo `PhoneMask`.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control onto your form; name it `PhoneMask`.</span></span>  
  
4. <span data-ttu-id="cbbd3-111">Impostare <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> la `PhoneMask` `(000) 000-0000 x9999`proprietà di su .</span><span class="sxs-lookup"><span data-stu-id="cbbd3-111">Set the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property of `PhoneMask` to `(000) 000-0000 x9999`.</span></span>  
  
5. <span data-ttu-id="cbbd3-112">Aggiungere le seguenti importazioni dello spazio dei nomi al form.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-112">Add the following namespace imports to the form.</span></span>  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6. <span data-ttu-id="cbbd3-113">Fare clic con il pulsante destro del mouse sul form e **scegliere Visualizza codice**.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-113">Right-click the form and choose **View Code**.</span></span> <span data-ttu-id="cbbd3-114">Inserire questo codice in qualsiasi punto della classe del form.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-114">Place this code anywhere in your form class.</span></span>  
  
    ```csharp  
    Binding currentBinding, phoneBinding;  
    DataSet employeesTable = new DataSet();  
    SqlConnection sc;  
    SqlDataAdapter dataConnect;  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        DoMaskBinding();  
    }  
  
    private void DoMaskBinding()  
    {  
        try  
        {  
            sc = new SqlConnection("Data Source=CLIENTUE;Initial Catalog=NORTHWIND;Integrated Security=SSPI");  
            sc.Open();  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
  
        dataConnect = new SqlDataAdapter("SELECT * FROM Employees", sc);  
        dataConnect.Fill(employeesTable, "Employees");  
  
        // Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        // before adding them to the control - otherwise, we won't get a Format event on the
        // initial load.
        try  
        {  
            currentBinding = new Binding("Text", employeesTable, "Employees.FirstName");  
            firstName.DataBindings.Add(currentBinding);  
  
            currentBinding = new Binding("Text", employeesTable, "Employees.LastName");  
            lastName.DataBindings.Add(currentBinding);  
  
            phoneBinding =new Binding("Text", employeesTable, "Employees.HomePhone");  
            // We must add the event handlers before we bind, or the Format event will not get called  
            // for the first record.  
            phoneBinding.Format += new ConvertEventHandler(phoneBinding_Format);  
            phoneBinding.Parse += new ConvertEventHandler(phoneBinding_Parse);  
            phoneMask.DataBindings.Add(phoneBinding);  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
    }  
    ```  
  
    ```vb  
    Dim WithEvents CurrentBinding, PhoneBinding As Binding  
    Dim EmployeesTable As New DataSet()  
    Dim sc As SqlConnection  
    Dim DataConnect As SqlDataAdapter  
  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        DoMaskedBinding()  
    End Sub  
  
    Private Sub DoMaskedBinding()  
        Try  
            sc = New SqlConnection("Data Source=SERVERNAME;Initial Catalog=NORTHWIND;Integrated Security=SSPI")  
            sc.Open()  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Exit Sub  
        End Try  
  
        DataConnect = New SqlDataAdapter("SELECT * FROM Employees", sc)  
        DataConnect.Fill(EmployeesTable, "Employees")  
  
        ' Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        ' before adding them to the control - otherwise, we won't get a Format event on the
        ' initial load.  
        Try  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.FirstName")  
            firstName.DataBindings.Add(CurrentBinding)  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.LastName")  
            lastName.DataBindings.Add(CurrentBinding)  
            PhoneBinding = New Binding("Text", EmployeesTable, "Employees.HomePhone")  
            PhoneMask.DataBindings.Add(PhoneBinding)  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Application.Exit()  
        End Try  
    End Sub  
    ```  
  
7. <span data-ttu-id="cbbd3-115">Aggiungere gestori eventi <xref:System.Windows.Forms.Binding.Format> <xref:System.Windows.Forms.Binding.Parse> per gli eventi `PhoneNumber` e `Extension` per combinare <xref:System.Data.DataSet>e separare i campi e dall'oggetto associato.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-115">Add event handlers for the <xref:System.Windows.Forms.Binding.Format> and <xref:System.Windows.Forms.Binding.Parse> events to combine and separate the `PhoneNumber` and `Extension` fields from the bound <xref:System.Data.DataSet>.</span></span>  
  
    ```csharp  
    private void phoneBinding_Format(Object sender, ConvertEventArgs e)  
    {  
        String ext;  
  
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        if (currentRow["Extension"] == null)
        {  
            ext = "";  
        } else
        {  
            ext = currentRow["Extension"].ToString();  
        }  
  
        e.Value = e.Value.ToString().Trim() + " x" + ext;  
    }  
  
    private void phoneBinding_Parse(Object sender, ConvertEventArgs e)  
    {  
        String phoneNumberAndExt = e.Value.ToString();  
  
        int extIndex = phoneNumberAndExt.IndexOf("x");  
        String ext = phoneNumberAndExt.Substring(extIndex).Trim();  
        String phoneNumber = phoneNumberAndExt.Substring(0, extIndex).Trim();  
  
        //Get the current binding object, and set the new extension manually.
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        // Remove the "x" from the extension.  
        currentRow["Extension"] = ext.Substring(1);  
  
        //Return the phone number.  
        e.Value = phoneNumber;  
    }  
    ```  
  
    ```vb  
    Private Sub PhoneBinding_Format(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Format  
        Dim Ext As String  
  
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        If (CurrentRow("Extension") Is Nothing) Then  
            Ext = ""  
        Else  
            Ext = CurrentRow("Extension").ToString()  
        End If  
  
        e.Value = e.Value.ToString().Trim() & " x" & Ext  
    End Sub  
  
    Private Sub PhoneBinding_Parse(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Parse  
        Dim PhoneNumberAndExt As String = e.Value.ToString()  
  
        Dim ExtIndex As Integer = PhoneNumberAndExt.IndexOf("x")  
        Dim Ext As String = PhoneNumberAndExt.Substring(ExtIndex).Trim()  
        Dim PhoneNumber As String = PhoneNumberAndExt.Substring(0, ExtIndex).Trim()  
  
        ' Get the current binding object, and set the new extension manually.
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        ' Remove the "x" from the extension.  
        CurrentRow("Extension") = CObj(Ext.Substring(1))  
  
        ' Return the phone number.  
        e.Value = PhoneNumber  
    End Sub  
    ```  
  
8. <span data-ttu-id="cbbd3-116">Aggiungere <xref:System.Windows.Forms.Button> due controlli al form.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-116">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span> <span data-ttu-id="cbbd3-117">`previousButton` Denominarli `nextButton`e .</span><span class="sxs-lookup"><span data-stu-id="cbbd3-117">Name them `previousButton` and `nextButton`.</span></span> <span data-ttu-id="cbbd3-118">Fare doppio clic su <xref:System.Windows.Forms.Control.Click> ogni pulsante per aggiungere un gestore eventi e compilare i gestori eventi come illustrato nell'esempio di codice seguente.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-118">Double-click each button to add a <xref:System.Windows.Forms.Control.Click> event handler, and fill in the event handlers as shown in the following code example.</span></span>  
  
    ```csharp  
    private void previousButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position - 1;  
    }  
  
    private void nextButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position + 1;  
    }  
    ```  
  
    ```vb  
    Private Sub PreviousButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles PreviousButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position - 1  
    End Sub  
  
    Private Sub NextButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles NextButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position + 1  
    End Sub  
    ```  
  
9. <span data-ttu-id="cbbd3-119">Eseguire l'esempio.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-119">Run the sample.</span></span> <span data-ttu-id="cbbd3-120">Modificare i dati e utilizzare i pulsanti **Precedente** e **Successivo** per <xref:System.Data.DataSet>verificare che i dati siano mantenuti correttamente nel file .</span><span class="sxs-lookup"><span data-stu-id="cbbd3-120">Edit the data, and use the **Previous** and **Next** buttons to see that the data is properly persisted to the <xref:System.Data.DataSet>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbbd3-121">Esempio</span><span class="sxs-lookup"><span data-stu-id="cbbd3-121">Example</span></span>  
 <span data-ttu-id="cbbd3-122">L'esempio di codice seguente è il listato di codice completo risultante dal completamento della procedura precedente.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-122">The following code example is the full code listing that results from completing the previous procedure.</span></span>  
  
 [!code-cpp[MaskedTextBoxData#1](~/samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](~/samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cbbd3-123">Compilazione del codice</span><span class="sxs-lookup"><span data-stu-id="cbbd3-123">Compiling the Code</span></span>  
  
- <span data-ttu-id="cbbd3-124">Creare un progetto di Visual C,NET o Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-124">Create a Visual C# or Visual Basic project.</span></span>  
  
- <span data-ttu-id="cbbd3-125">Aggiungere <xref:System.Windows.Forms.TextBox> i <xref:System.Windows.Forms.MaskedTextBox> controlli e al form, come descritto nella procedura precedente.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-125">Add the <xref:System.Windows.Forms.TextBox> and <xref:System.Windows.Forms.MaskedTextBox> controls to the form, as described in the previous procedure.</span></span>  
  
- <span data-ttu-id="cbbd3-126">Aprire il file di codice sorgente per il modulo predefinito del progetto.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-126">Open the source code file for the project's default form.</span></span>  
  
- <span data-ttu-id="cbbd3-127">Sostituire il codice sorgente in questo file con il codice elencato nella precedente sezione "Codice".</span><span class="sxs-lookup"><span data-stu-id="cbbd3-127">Replace the source code in this file with the code listed in the previous "Code" section.</span></span>  
  
- <span data-ttu-id="cbbd3-128">Compilare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="cbbd3-128">Compile the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbbd3-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cbbd3-129">See also</span></span>

- [<span data-ttu-id="cbbd3-130">Procedura dettagliata: utilizzo del controllo MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="cbbd3-130">Walkthrough: Working with the MaskedTextBox Control</span></span>](walkthrough-working-with-the-maskedtextbox-control.md)
