---
title: 'Procedura: richiamare una finestra di dialogo di stampa'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 6d7bc322079718d17a921ef34af79145b021e3a7
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636094"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="060ad-102">Procedura: richiamare una finestra di dialogo di stampa</span><span class="sxs-lookup"><span data-stu-id="060ad-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="060ad-103">Per consentire la stampa dall'applicazione, è possibile creare e aprire semplicemente un oggetto <xref:System.Windows.Controls.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="060ad-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="060ad-104">Esempio</span><span class="sxs-lookup"><span data-stu-id="060ad-104">Example</span></span>  
 <span data-ttu-id="060ad-105">Il controllo <xref:System.Windows.Controls.PrintDialog> fornisce un singolo punto di ingresso per [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configurazione e invio di processi XPS.</span><span class="sxs-lookup"><span data-stu-id="060ad-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and XPS job submission.</span></span> <span data-ttu-id="060ad-106">Il controllo è facile da usare ed è possibile crearne un'istanza usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup o codice.</span><span class="sxs-lookup"><span data-stu-id="060ad-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="060ad-107">Nell'esempio seguente viene illustrato come creare un'istanza di e come aprire il controllo nel codice e come stamparlo.</span><span class="sxs-lookup"><span data-stu-id="060ad-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="060ad-108">Viene inoltre illustrato come assicurarsi che la finestra di dialogo fornisca all'utente la possibilità di impostare un intervallo specifico di pagine.</span><span class="sxs-lookup"><span data-stu-id="060ad-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="060ad-109">Nel codice di esempio si presuppone che esista un file FixedDocumentSequence. XPS nella radice dell'unità C:.</span><span class="sxs-lookup"><span data-stu-id="060ad-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="060ad-110">Una volta aperta la finestra di dialogo, gli utenti saranno in grado di effettuare una selezione tra le stampanti installate nel computer.</span><span class="sxs-lookup"><span data-stu-id="060ad-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="060ad-111">Hanno inoltre la possibilità di selezionare il writer di [documenti XPS Microsoft](https://go.microsoft.com/fwlink/?LinkId=147319) per creare un file XPS (XML Paper Specification) anziché stampare.</span><span class="sxs-lookup"><span data-stu-id="060ad-111">They will also have the option of selecting the [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319) to create an XML Paper Specification (XPS) file instead of printing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="060ad-112">Il controllo <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> di WPF, descritto in questo argomento, non dovrebbe essere confuso con il componente <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> di Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="060ad-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of WPF, which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="060ad-113">In modo esplicito, è possibile usare il metodo <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> senza mai aprire la finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="060ad-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="060ad-114">In questo senso, il controllo può essere usato come componente di stampa non visibile.</span><span class="sxs-lookup"><span data-stu-id="060ad-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="060ad-115">Per motivi di prestazioni, tuttavia, sarebbe preferibile usare il metodo <xref:System.Printing.PrintQueue.AddJob%2A> o uno dei molti metodi <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> e <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> della <xref:System.Windows.Xps.XpsDocumentWriter>.</span><span class="sxs-lookup"><span data-stu-id="060ad-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="060ad-116">Per ulteriori informazioni, vedere la pagina relativa alla [stampa di file XPS](how-to-programmatically-print-xps-files.md) e a livello di codice.</span><span class="sxs-lookup"><span data-stu-id="060ad-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="060ad-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="060ad-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="060ad-118">Documenti in WPF</span><span class="sxs-lookup"><span data-stu-id="060ad-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="060ad-119">Panoramica della stampa</span><span class="sxs-lookup"><span data-stu-id="060ad-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="060ad-120">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="060ad-120">Microsoft XPS Document Writer</span></span>](https://go.microsoft.com/fwlink/?LinkId=147319)
