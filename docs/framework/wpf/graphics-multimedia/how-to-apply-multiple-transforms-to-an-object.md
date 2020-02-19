---
title: 'Procedura: applicare più trasformazioni a un oggetto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 544d0a26f24e5ad4ed7e2e3cfa25f8e15d1be446
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452831"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="3a5b6-102">Procedura: applicare più trasformazioni a un oggetto</span><span class="sxs-lookup"><span data-stu-id="3a5b6-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="3a5b6-103">Questo esempio illustra come usare un <xref:System.Windows.Media.TransformGroup> per raggruppare due o più oggetti <xref:System.Windows.Media.Transform> in un singolo <xref:System.Windows.Media.Transform>composito.</span><span class="sxs-lookup"><span data-stu-id="3a5b6-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a5b6-104">Esempio</span><span class="sxs-lookup"><span data-stu-id="3a5b6-104">Example</span></span>  
 <span data-ttu-id="3a5b6-105">Nell'esempio seguente viene usato un <xref:System.Windows.Media.TransformGroup> per applicare una <xref:System.Windows.Media.ScaleTransform> e un <xref:System.Windows.Media.RotateTransform> a una <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="3a5b6-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3a5b6-106">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3a5b6-106">See also</span></span>

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [<span data-ttu-id="3a5b6-107">Cenni preliminari sulle trasformazioni</span><span class="sxs-lookup"><span data-stu-id="3a5b6-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="3a5b6-108">2-D Transforms Sample (Esempio di trasformazioni 2D)</span><span class="sxs-lookup"><span data-stu-id="3a5b6-108">2-D Transforms Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
