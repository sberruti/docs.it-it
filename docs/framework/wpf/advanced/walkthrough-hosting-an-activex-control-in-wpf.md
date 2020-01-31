---
title: Ospitare un controllo ActiveX in WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 4ca40c0f6e62fd413e7f305649c5c01ddc152b2a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794139"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="42d4f-102">Procedura dettagliata: hosting di un controllo ActiveX in WPF</span><span class="sxs-lookup"><span data-stu-id="42d4f-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="42d4f-103">Per consentire una migliore interazione con i browser, è possibile utilizzare i controlli Microsoft ActiveX nell'applicazione basata su [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42d4f-103">To enable improved interaction with browsers, you can use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="42d4f-104">In questa procedura dettagliata viene illustrato come è possibile ospitare Microsoft Windows Media Player come controllo in una pagina di [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42d4f-104">This walkthrough demonstrates how you can host the Microsoft Windows Media Player as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="42d4f-105">Le attività illustrate nella procedura dettagliata sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="42d4f-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="42d4f-106">Creazione del progetto.</span><span class="sxs-lookup"><span data-stu-id="42d4f-106">Creating the project.</span></span>

- <span data-ttu-id="42d4f-107">Creazione del controllo ActiveX.</span><span class="sxs-lookup"><span data-stu-id="42d4f-107">Creating the ActiveX control.</span></span>

- <span data-ttu-id="42d4f-108">Hosting del controllo ActiveX in una pagina WPF.</span><span class="sxs-lookup"><span data-stu-id="42d4f-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="42d4f-109">Al termine di questa procedura dettagliata, si apprenderà come usare i controlli Microsoft ActiveX nell'applicazione basata su [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42d4f-109">When you have completed this walkthrough, you will understand how to use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="42d4f-110">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="42d4f-110">Prerequisites</span></span>
 <span data-ttu-id="42d4f-111">Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="42d4f-111">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="42d4f-112">Microsoft Windows Media Player installato nel computer in cui è installato Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="42d4f-112">Microsoft Windows Media Player installed on the computer where Visual Studio is installed.</span></span>

- <span data-ttu-id="42d4f-113">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="42d4f-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="42d4f-114">Creazione del progetto</span><span class="sxs-lookup"><span data-stu-id="42d4f-114">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="42d4f-115">Per creare e impostare il progetto</span><span class="sxs-lookup"><span data-stu-id="42d4f-115">To create and set up the project</span></span>

1. <span data-ttu-id="42d4f-116">Creare un progetto di applicazione WPF denominato `HostingAxInWpf`.</span><span class="sxs-lookup"><span data-stu-id="42d4f-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2. <span data-ttu-id="42d4f-117">Aggiungere un progetto libreria di controlli Windows Forms alla soluzione e denominare il progetto `WmpAxLib`.</span><span class="sxs-lookup"><span data-stu-id="42d4f-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3. <span data-ttu-id="42d4f-118">Nel progetto WmpAxLib aggiungere un riferimento all'assembly di Windows Media Player, denominato wmp. dll.</span><span class="sxs-lookup"><span data-stu-id="42d4f-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4. <span data-ttu-id="42d4f-119">Aprire la **casella degli strumenti**.</span><span class="sxs-lookup"><span data-stu-id="42d4f-119">Open the **Toolbox**.</span></span>

5. <span data-ttu-id="42d4f-120">Fare clic con il pulsante destro del mouse nella **casella degli strumenti**, quindi **scegliere Scegli elementi**.</span><span class="sxs-lookup"><span data-stu-id="42d4f-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6. <span data-ttu-id="42d4f-121">Fare clic sulla scheda **componenti com** , selezionare il controllo **Media Player Windows** , quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="42d4f-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="42d4f-122">Il controllo Media Player Windows viene aggiunto alla **casella degli strumenti**.</span><span class="sxs-lookup"><span data-stu-id="42d4f-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7. <span data-ttu-id="42d4f-123">In Esplora soluzioni fare clic con il pulsante destro del mouse sul file **UserControl1** e quindi scegliere **Rinomina**.</span><span class="sxs-lookup"><span data-stu-id="42d4f-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8. <span data-ttu-id="42d4f-124">Modificare il nome in `WmpAxControl.vb` o `WmpAxControl.cs`, a seconda del linguaggio.</span><span class="sxs-lookup"><span data-stu-id="42d4f-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="42d4f-125">Se viene richiesto di rinominare tutti i riferimenti, fare clic su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="42d4f-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="42d4f-126">Creazione del controllo ActiveX</span><span class="sxs-lookup"><span data-stu-id="42d4f-126">Creating the ActiveX Control</span></span>
<span data-ttu-id="42d4f-127">Visual Studio genera automaticamente una classe wrapper <xref:System.Windows.Forms.AxHost> per un controllo Microsoft ActiveX quando il controllo viene aggiunto a un'area di progettazione.</span><span class="sxs-lookup"><span data-stu-id="42d4f-127">Visual Studio automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a Microsoft ActiveX control when the control is added to a design surface.</span></span> <span data-ttu-id="42d4f-128">La procedura seguente consente di creare un assembly gestito denominato AxInterop. WMPLib. dll.</span><span class="sxs-lookup"><span data-stu-id="42d4f-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

### <a name="to-create-the-activex-control"></a><span data-ttu-id="42d4f-129">Per creare il controllo ActiveX</span><span class="sxs-lookup"><span data-stu-id="42d4f-129">To create the ActiveX control</span></span>

1. <span data-ttu-id="42d4f-130">Aprire WmpAxControl. vb o WmpAxControl.cs nel Progettazione Windows Form.</span><span class="sxs-lookup"><span data-stu-id="42d4f-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="42d4f-131">Dalla **casella degli strumenti**aggiungere il controllo Windows Media Player nell'area di progettazione.</span><span class="sxs-lookup"><span data-stu-id="42d4f-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3. <span data-ttu-id="42d4f-132">Nella Finestra Proprietà impostare il valore della proprietà <xref:System.Windows.Forms.Control.Dock%2A> del controllo Media Player di Windows su <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="42d4f-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4. <span data-ttu-id="42d4f-133">Compilare il progetto libreria di controlli WmpAxLib.</span><span class="sxs-lookup"><span data-stu-id="42d4f-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="42d4f-134">Hosting del controllo ActiveX in una pagina WPF</span><span class="sxs-lookup"><span data-stu-id="42d4f-134">Hosting the ActiveX Control on a WPF Page</span></span>

### <a name="to-host-the-activex-control"></a><span data-ttu-id="42d4f-135">Per ospitare il controllo ActiveX</span><span class="sxs-lookup"><span data-stu-id="42d4f-135">To host the ActiveX control</span></span>

1. <span data-ttu-id="42d4f-136">Nel progetto HostingAxInWpf aggiungere un riferimento all'assembly di interoperabilità ActiveX generato.</span><span class="sxs-lookup"><span data-stu-id="42d4f-136">In the HostingAxInWpf project, add a reference to the generated ActiveX interoperability assembly.</span></span>

     <span data-ttu-id="42d4f-137">Questo assembly è denominato AxInterop. WMPLib. dll ed è stato aggiunto alla cartella debug del progetto WmpAxLib quando è stato importato il controllo Media Player di Windows.</span><span class="sxs-lookup"><span data-stu-id="42d4f-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2. <span data-ttu-id="42d4f-138">Aggiungere un riferimento all'assembly WindowsFormsIntegration, denominato WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="42d4f-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="42d4f-139">Aggiungere un riferimento all'assembly Windows Forms, denominato System. Windows. Forms. dll.</span><span class="sxs-lookup"><span data-stu-id="42d4f-139">Add a reference to the Windows Forms assembly, which is named System.Windows.Forms.dll.</span></span>

4. <span data-ttu-id="42d4f-140">Aprire MainWindow. XAML in WPF Designer.</span><span class="sxs-lookup"><span data-stu-id="42d4f-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5. <span data-ttu-id="42d4f-141">Denominare l'elemento <xref:System.Windows.Controls.Grid> `grid1`.</span><span class="sxs-lookup"><span data-stu-id="42d4f-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. <span data-ttu-id="42d4f-142">Nella visualizzazione progettazione o nella visualizzazione XAML Selezionare l'elemento <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="42d4f-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7. <span data-ttu-id="42d4f-143">Nella Finestra Proprietà fare clic sulla scheda **eventi** .</span><span class="sxs-lookup"><span data-stu-id="42d4f-143">In the Properties window, click the **Events** tab.</span></span>

8. <span data-ttu-id="42d4f-144">Fare doppio clic sull'evento <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="42d4f-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="42d4f-145">Inserire il codice seguente per gestire l'evento <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="42d4f-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="42d4f-146">Questo codice crea un'istanza del controllo <xref:System.Windows.Forms.Integration.WindowsFormsHost> e aggiunge un'istanza del controllo `AxWindowsMediaPlayer` come figlio.</span><span class="sxs-lookup"><span data-stu-id="42d4f-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="42d4f-147">Premere F5 per compilare ed eseguire l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="42d4f-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42d4f-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="42d4f-148">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="42d4f-149">Progettare XAML in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="42d4f-149">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="42d4f-150">Procedura dettagliata: Hosting di controlli Windows Form compositi in WPF</span><span class="sxs-lookup"><span data-stu-id="42d4f-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="42d4f-151">Procedura dettaglia: hosting di un controllo WPF composito in Windows Form</span><span class="sxs-lookup"><span data-stu-id="42d4f-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
