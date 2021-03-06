---
title: 'Procedura: Ridimensionare un modello tridimensionale'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 6d668de08201d819ce9f8752bedf6c388a6bc718
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769330"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a>Procedura: Ridimensionare un modello tridimensionale
Questo esempio illustra come ridimensionare un oggetto 3D. Per ridimensionare un oggetto 3D, usare un <xref:System.Windows.Media.Media3D.ScaleTransform3D>. Il <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, e <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> proprietà ridimensionano l'elemento in base al fattore specificato. Ad esempio, un <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> valore pari a 1,5 adatta a un oggetto al 150% della sua larghezza originale. Oggetto <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> valore pari a 0,5 riduce l'altezza di un oggetto del 50%. Il codice seguente viene illustrato l'utilizzo un <xref:System.Windows.Media.Media3D.ScaleTransform3D> come la trasformazione per un <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Esempio  
 Il codice seguente illustra l'intero esempio.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Vedere anche

- [Aggiungere un'animazione alle conversioni tridimensionali](how-to-animate-3-d-translations.md)
- [Creare una scena tridimensionale](how-to-create-a-3-d-scene.md)
- [Panoramica sulla grafica tridimensionale](3-d-graphics-overview.md)
