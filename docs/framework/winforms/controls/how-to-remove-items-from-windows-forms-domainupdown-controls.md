---
title: Rimuovere elementi da controlli DomainUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: e52af5c5add4fda93e2b51c8afdb90c92e8d2f62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735773"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a><span data-ttu-id="696ab-102">Procedura: rimuovere elementi dai controlli DomainUpDown Windows Form</span><span class="sxs-lookup"><span data-stu-id="696ab-102">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>
<span data-ttu-id="696ab-103">È possibile rimuovere elementi dal controllo Windows Forms <xref:System.Windows.Forms.DomainUpDown> chiamando il metodo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> o <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> della classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>.</span><span class="sxs-lookup"><span data-stu-id="696ab-103">You can remove items from the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control by calling the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class.</span></span> <span data-ttu-id="696ab-104">Il metodo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> rimuove un elemento specifico, mentre il metodo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> rimuove un elemento in base alla relativa posizione.</span><span class="sxs-lookup"><span data-stu-id="696ab-104">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method removes a specific item, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method removes an item by its position.</span></span>  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="696ab-105">Per rimuovere un elemento</span><span class="sxs-lookup"><span data-stu-id="696ab-105">To remove an item</span></span>  
  
- <span data-ttu-id="696ab-106">Usare il metodo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> della classe <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> per rimuovere un elemento in base al nome.</span><span class="sxs-lookup"><span data-stu-id="696ab-106">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to remove an item by name.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     <span data-ttu-id="696ab-107">oppure</span><span class="sxs-lookup"><span data-stu-id="696ab-107">-or-</span></span>  
  
- <span data-ttu-id="696ab-108">Usare il metodo <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> per rimuovere un elemento in base alla relativa posizione.</span><span class="sxs-lookup"><span data-stu-id="696ab-108">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method to remove an item by its position.</span></span>  
  
    ```vb  
    ' Removes the first item in the list.  
    DomainUpDown1.Items.RemoveAt(0)  
    ```  
  
    ```csharp  
    // Removes the first item in the list.  
    domainUpDown1.Items.RemoveAt(0);  
    ```  
  
    ```cpp  
    // Removes the first item in the list.  
    domainUpDown1->Items->RemoveAt(0);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="696ab-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="696ab-109">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [<span data-ttu-id="696ab-110">Controllo DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="696ab-110">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
- [<span data-ttu-id="696ab-111">Panoramica sul controllo DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="696ab-111">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)
