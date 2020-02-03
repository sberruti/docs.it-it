---
title: Seleziona un elemento nel controllo ListView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 57e985af9d0347510d7d7782f68d5b414d36e077
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743226"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="4645d-102">Procedura: selezionare un elemento nel controllo ListView Windows Form</span><span class="sxs-lookup"><span data-stu-id="4645d-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="4645d-103">In questo esempio viene illustrato come selezionare a livello di codice un elemento in un controllo Windows Forms <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="4645d-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="4645d-104">La selezione di un elemento a livello di codice non modifica automaticamente lo stato attivo sul controllo <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="4645d-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="4645d-105">Per questo motivo, in genere è necessario impostare l'elemento come attivo quando si seleziona un elemento.</span><span class="sxs-lookup"><span data-stu-id="4645d-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4645d-106">Esempio</span><span class="sxs-lookup"><span data-stu-id="4645d-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4645d-107">Compilazione del codice</span><span class="sxs-lookup"><span data-stu-id="4645d-107">Compiling the Code</span></span>  
 <span data-ttu-id="4645d-108">L'esempio presenta i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="4645d-108">This example requires:</span></span>  
  
- <span data-ttu-id="4645d-109">Controllo <xref:System.Windows.Forms.ListView> denominato `listView1` che contiene almeno un elemento.</span><span class="sxs-lookup"><span data-stu-id="4645d-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
- <span data-ttu-id="4645d-110">Riferimenti agli spazi dei nomi <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4645d-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4645d-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4645d-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
