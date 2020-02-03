---
title: Cenni preliminari sul componente ColorDialog
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 48d9d5072335908f85e65933dadafb1b69f28528
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736972"
---
# <a name="colordialog-component-overview-windows-forms"></a><span data-ttu-id="921e6-102">Cenni preliminari sul componente ColorDialog (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="921e6-102">ColorDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="921e6-103">Il componente Windows Forms <xref:System.Windows.Forms.ColorDialog> è una finestra di dialogo preconfigurata che consente all'utente di selezionare un colore da una tavolozza e di aggiungere colori personalizzati alla tavolozza.</span><span class="sxs-lookup"><span data-stu-id="921e6-103">The Windows Forms <xref:System.Windows.Forms.ColorDialog> component is a pre-configured dialog box that allows the user to select a color from a palette and to add custom colors to that palette.</span></span> <span data-ttu-id="921e6-104">È la stessa finestra di dialogo visualizzata in altre applicazioni basate su Windows per selezionare i colori.</span><span class="sxs-lookup"><span data-stu-id="921e6-104">It is the same dialog box that you see in other Windows-based applications to select colors.</span></span> <span data-ttu-id="921e6-105">e costituisce una semplice soluzione, utilizzabile nell'applicazione basata su Windows creata, per evitare di configurare una propria finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="921e6-105">Use it within your Windows-based application as a simple solution in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="921e6-106">Il colore selezionato nella finestra di dialogo viene restituito nella proprietà <xref:System.Windows.Forms.ColorDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="921e6-106">The color selected in the dialog box is returned in the <xref:System.Windows.Forms.ColorDialog.Color%2A> property.</span></span> <span data-ttu-id="921e6-107">Se la proprietà <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> è impostata su `false`, il pulsante "Definisci colori personalizzati" è disabilitato e l'utente è limitato ai colori predefiniti della tavolozza.</span><span class="sxs-lookup"><span data-stu-id="921e6-107">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `false`, the "Define Custom Colors" button is disabled and the user is restricted to the predefined colors in the palette.</span></span> <span data-ttu-id="921e6-108">Se la proprietà <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> è impostata su `true`, l'utente non sarà in grado di selezionare i colori dimessi.</span><span class="sxs-lookup"><span data-stu-id="921e6-108">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors.</span></span> <span data-ttu-id="921e6-109">Per visualizzare la finestra di dialogo, è necessario chiamare il relativo metodo <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="921e6-109">To display the dialog box, you must call its <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="921e6-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="921e6-110">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="921e6-111">Componente ColorDialog</span><span class="sxs-lookup"><span data-stu-id="921e6-111">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
- [<span data-ttu-id="921e6-112">Controlli e componenti della finestra di dialogo</span><span class="sxs-lookup"><span data-stu-id="921e6-112">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
- [<span data-ttu-id="921e6-113">Procedura: Modificare l'aspetto del componente ColorDialog di Windows Form</span><span class="sxs-lookup"><span data-stu-id="921e6-113">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
