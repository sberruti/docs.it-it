---
title: Panoramica dell'utilizzo dei controlli
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, controls
- controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: fddbe951-4485-459d-a5fd-665ea346dbc1
ms.openlocfilehash: bcd0e81b730c2fc7b741662ae803633de4f6199e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141731"
---
# <a name="overview-of-using-controls-in-windows-forms"></a><span data-ttu-id="adbe9-102">Cenni preliminari sull'utilizzo di controlli in Windows Form</span><span class="sxs-lookup"><span data-stu-id="adbe9-102">Overview of Using Controls in Windows Forms</span></span>
<span data-ttu-id="adbe9-103">In questo argomento vengono descritti gli elementi essenziali di un'applicazione Windows Form e viene fornito un semplice esempio che utilizza i controlli e gestisce gli eventi in un'applicazione Windows Form.This topic describes the essential elements of a Windows Forms application and provides a simple example that uses controls and handles events in a Windows Forms application.</span><span class="sxs-lookup"><span data-stu-id="adbe9-103">This topic describes the essential elements of a Windows Forms application and provides a simple example that uses controls and handles events in a Windows Forms application.</span></span>  
  
## <a name="simple-windows-forms-applications"></a><span data-ttu-id="adbe9-104">Applicazioni Windows Form semplici</span><span class="sxs-lookup"><span data-stu-id="adbe9-104">Simple Windows Forms Applications</span></span>  
 <span data-ttu-id="adbe9-105">Come minimo, un'applicazione Windows Form è costituita dai seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="adbe9-105">At a minimum, a Windows Forms application consists of the following elements:</span></span>  
  
- <span data-ttu-id="adbe9-106">Una o più classi <xref:System.Windows.Forms.Form?displayProperty=nameWithType>che derivano da .</span><span class="sxs-lookup"><span data-stu-id="adbe9-106">One or more classes that derive from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="adbe9-107">Metodo `Main` che richiama `static` il`shared` metodo ( <xref:System.Windows.Forms.Application.Run%2A> in Visual <xref:System.Windows.Forms.Form> Basic) e vi passa un'istanza.</span><span class="sxs-lookup"><span data-stu-id="adbe9-107">A `Main` method that invokes the `static` (`shared` in Visual Basic) <xref:System.Windows.Forms.Application.Run%2A> method and passes a <xref:System.Windows.Forms.Form> instance to it.</span></span> <span data-ttu-id="adbe9-108">Il <xref:System.Windows.Forms.Application.Run%2A> metodo elabora i messaggi dal sistema operativo all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="adbe9-108">The <xref:System.Windows.Forms.Application.Run%2A> method processes messages from the operating system to the application.</span></span>  
  
 <span data-ttu-id="adbe9-109">Nell'esempio di codice riportato di seguito vengono illustrati gli elementi essenziali di un'applicazione Windows Form.The following code example shows the essential elements of a Windows Forms application.</span><span class="sxs-lookup"><span data-stu-id="adbe9-109">The following code example shows the essential elements of a Windows Forms application.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
  
Public Class MyForm  
   Inherits Form  
  
   Public Sub New()  
      Me.Text = "Hello World"  
   End Sub 'New  
  
   <STAThread()> _  
   Public Shared Sub Main()  
      Dim aform As New MyForm()  
      ' The Application.Run method processes messages from the operating system
      ' to your application. If you comment out the next line of code,
      ' your application will compile and execute, but because it is not in the  
      ' message loop, it will exit after an instance of the form is created.  
      Application.Run(aform)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
  
public class MyForm : Form {  
  
   public MyForm() {  
      this.Text = "Hello World";  
   }  
   [STAThread]  
   public static void Main(string[] args) {  
     MyForm aform = new MyForm();  
// The Application.Run method processes messages from the operating system
// to your application. If you comment out the next line of code,
// your application will compile and execute, but because it is not in the // message loop, it will exit after an instance of the form is created.  
      Application.Run(aform);  
   }  
}  
```  
  
## <a name="using-controls-in-a-windows-forms-application"></a><span data-ttu-id="adbe9-110">Utilizzo di controlli in un'applicazione Windows FormUsing Controls in a Windows Forms Application</span><span class="sxs-lookup"><span data-stu-id="adbe9-110">Using Controls in a Windows Forms Application</span></span>  
 <span data-ttu-id="adbe9-111">Nell'esempio di codice riportato di seguito viene illustrata una semplice applicazione che illustra come le applicazioni Windows Form utilizzano i controlli e gestiscono gli eventi.</span><span class="sxs-lookup"><span data-stu-id="adbe9-111">The following code example shows a simple application that illustrates how Windows Forms applications use controls and handle events.</span></span> <span data-ttu-id="adbe9-112">L'esempio è costituito da tre pulsanti in un form; ogni pulsante cambia il colore di sfondo quando si fa clic.</span><span class="sxs-lookup"><span data-stu-id="adbe9-112">The example consists of three buttons on a form; each button changes the background color when clicked.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.ComponentModel  
Imports System.Windows.Forms  
Imports System.Resources  
Imports System.Drawing  
  
Public Class MyForm  
   Inherits Form  
   Private red As Button  
   Private blue As Button  
   Private green As Button  
  
   Public Sub New()  
      InitializeComponent()  
   End Sub  
  
   Protected Overloads Overrides Sub Dispose(disposing as Boolean)  
      MyBase.Dispose(disposing)  
   End Sub  
  
   ' InitializeComponent is a helper method for the constructor.
   ' It is included for consistency with code that is
   ' auto-generated by the Windows Forms designer in Visual Studio.
   Private Sub InitializeComponent()  
  
      ' Creates three buttons, sets their properties, and attaches  
      ' an event handler to each button.  
      red = New Button()  
      red.Text = "Red"  
      red.Location = New Point(100, 50)  
      red.Size = New Size(50, 50)  
      AddHandler red.Click, AddressOf button_Click  
      Controls.Add(red)  
  
      blue = New Button()  
      blue.Text = "Blue"  
      blue.Location = New Point(100, 100)  
      blue.Size = New Size(50, 50)  
      AddHandler blue.Click, AddressOf button_Click  
      Controls.Add(blue)  
  
      green = New Button()  
      green.Text = "Green"  
      green.Location = New Point(100, 150)  
      green.Size = New Size(50, 50)  
      AddHandler green.Click, AddressOf button_Click  
      Controls.Add(green)  
   End Sub  
  
   ' Event handler.  
   Private Sub button_Click(sender As Object, e As EventArgs)  
      If sender Is red Then  
         Me.BackColor = Color.Red  
      Else  
         If sender Is blue Then  
            Me.BackColor = Color.Blue  
         Else  
            Me.BackColor = Color.Green  
         End If  
      End If
   End Sub  
  
   ' The STAThreadAttribute informs the common language runtime that  
   ' Windows Forms uses the single-threaded apartment model.  
   <STAThread()> _  
   Public Shared Sub Main()  
      Application.Run(New MyForm())  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.ComponentModel;  
using System.Windows.Forms;  
using System.Resources;  
using System.Drawing;  
  
public class MyForm : Form {  
   private Button red;  
   private Button blue;  
   private Button green;  
  
   public MyForm() : base() {
      InitializeComponent();
   }  
  
   protected override void Dispose(bool disposing) {  
      base.Dispose(disposing);  
   }  
  
// InitializeComponent is a helper method for the constructor.
// It is included for consistency with code that is
// auto-generated by the Windows Forms designer in Visual Studio.
   private void InitializeComponent() {  
  
// A delegate for the click event of a button. The argument to
// the constructor contains a reference to the method that performs the
// event handling logic.  
      EventHandler handler = new EventHandler(button_Click);  
  
// Creates three buttons, sets their properties, and attaches  
// an event handler to each button.  
  
      red = new Button();  
      red.Text = "Red";  
      red.Location = new Point(100, 50);  
      red.Size = new Size(50, 50);  
      red.Click +=handler;  
      Controls.Add(red);  
  
      blue = new Button();  
      blue.Text = "Blue";  
      blue.Location = new Point(100, 100);  
      blue.Size = new Size(50, 50);  
      blue.Click += handler;  
      Controls.Add(blue);  
  
      green = new Button();  
      green.Text = "Green";  
      green.Location = new Point(100, 150);  
      green.Size = new Size(50, 50);  
      green.Click += handler;  
      Controls.Add(green);
      }  
  
   // Event handler.  
   private void button_Click(object sender, EventArgs e) {  
            if (sender == red) this.BackColor = Color.Red ;  
                  else if (sender == blue) this.BackColor = Color.Blue;  
                  else this.BackColor = Color.Green;  
        }  
   // The STAThreadAttribute informs the common language runtime that  
   // Windows Forms uses the single-threaded apartment model.  
  [STAThread]  
   public static void Main(string[] args) {  
   Application.Run(new MyForm());  
   }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="adbe9-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="adbe9-113">See also</span></span>

- [<span data-ttu-id="adbe9-114">Sviluppo di controlli Windows Form personalizzati con .NET Framework</span><span class="sxs-lookup"><span data-stu-id="adbe9-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="adbe9-115">Nozioni fondamentali sullo sviluppo di controlli Windows Form</span><span class="sxs-lookup"><span data-stu-id="adbe9-115">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
