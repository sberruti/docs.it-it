---
title: Aggiungere e rimuovere nodi con il controllo TreeView usando la finestra di progettazione
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 7edf09539719ec76fa3f650254c5c84ff0bc3af7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732245"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="85a62-102">Procedura: aggiungere e rimuovere nodi nel controllo TreeView Windows Form mediante la finestra di progettazione</span><span class="sxs-lookup"><span data-stu-id="85a62-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>

<span data-ttu-id="85a62-103">Poiché il controllo Windows Forms <xref:System.Windows.Forms.TreeView> Visualizza i nodi in modo gerarchico, quando si aggiunge un nodo è necessario prestare attenzione a ciò che è il nodo padre.</span><span class="sxs-lookup"><span data-stu-id="85a62-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>

<span data-ttu-id="85a62-104">Per la procedura seguente è necessario un progetto di **applicazione Windows** con un modulo contenente un controllo <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="85a62-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="85a62-105">Per informazioni sulla configurazione di un progetto di questo tipo, vedere [procedura: creare un progetto Windows Forms Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [procedura: aggiungere controlli a Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="85a62-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="85a62-106">Per aggiungere o rimuovere nodi nella finestra di progettazione</span><span class="sxs-lookup"><span data-stu-id="85a62-106">To add or remove nodes in the designer</span></span>

1. <span data-ttu-id="85a62-107">Selezionare il controllo <xref:System.Windows.Forms.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="85a62-107">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>

2. <span data-ttu-id="85a62-108">Nella finestra **Proprietà** fare clic sui **puntini** di sospensione (![pulsante con i puntini di sospensione (...) nel pulsante finestra proprietà di Visual Studio.](./media/visual-studio-ellipsis-button.png)) accanto alla proprietà <xref:System.Windows.Forms.TreeView.Nodes%2A>.</span><span class="sxs-lookup"><span data-stu-id="85a62-108">In the **Properties** window, click the **Ellipsis** (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>

     <span data-ttu-id="85a62-109">Viene visualizzato l' **Editor TreeNode** .</span><span class="sxs-lookup"><span data-stu-id="85a62-109">The **TreeNode Editor** appears.</span></span>

3. <span data-ttu-id="85a62-110">Per aggiungere nodi, è necessario che esista un nodo radice. Se non è presente, è necessario innanzitutto aggiungere una radice facendo clic sul pulsante **Aggiungi radice** .</span><span class="sxs-lookup"><span data-stu-id="85a62-110">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="85a62-111">È quindi possibile aggiungere nodi figlio selezionando la radice o qualsiasi altro nodo e facendo clic sul pulsante **Aggiungi figlio** .</span><span class="sxs-lookup"><span data-stu-id="85a62-111">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>

4. <span data-ttu-id="85a62-112">Per eliminare i nodi, selezionare il nodo da eliminare, quindi fare clic sul pulsante **Elimina** .</span><span class="sxs-lookup"><span data-stu-id="85a62-112">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>

## <a name="see-also"></a><span data-ttu-id="85a62-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="85a62-113">See also</span></span>

- [<span data-ttu-id="85a62-114">Controllo TreeView</span><span class="sxs-lookup"><span data-stu-id="85a62-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="85a62-115">Panoramica sul controllo TreeView</span><span class="sxs-lookup"><span data-stu-id="85a62-115">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="85a62-116">Procedura: Impostare icone per il controllo TreeView di Windows Form</span><span class="sxs-lookup"><span data-stu-id="85a62-116">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="85a62-117">Procedura: Scorrere tutti i nodi di un controllo TreeView di Windows Form</span><span class="sxs-lookup"><span data-stu-id="85a62-117">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="85a62-118">Procedura: Individuare il nodo di TreeView scelto</span><span class="sxs-lookup"><span data-stu-id="85a62-118">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="85a62-119">Procedura: Aggiungere informazioni personalizzate a un controllo TreeView o ListView (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="85a62-119">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
