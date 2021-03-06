---
title: 'Procedura: Riempire una forma con un colore a tinta unita'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: d6fe7a252029ff80f21d99f7342fabb1d29fbe24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781290"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>Procedura: Riempire una forma con un colore a tinta unita
Per riempire una forma con un colore a tinta unita, creare un <xref:System.Drawing.SolidBrush> dell'oggetto, quindi passarlo <xref:System.Drawing.SolidBrush> oggetto come argomento a uno dei metodi di riempimento del <xref:System.Drawing.Graphics> classe. Nell'esempio seguente viene illustrato come compilare un'ellisse con il colore rosso.  
  
## <a name="example"></a>Esempio  
 Nel codice seguente, il <xref:System.Drawing.SolidBrush.%23ctor%2A> costruttore accetta un <xref:System.Drawing.Color> oggetto come unico argomento. I valori utilizzati per il <xref:System.Drawing.Color.FromArgb%2A> metodo rappresentano i componenti alfa, rossi, verdi e blu del colore. Ognuno di questi valori deve essere compreso tra 0 e 255. I primi 255 indica che il colore è completamente opaco, e il secondo 255 indica che il componente rossa alla piena intensità. Gli due zeri indicano che i componenti verdi e blu abbiano un'intensità pari a 0.  
  
 I quattro numeri (0, 0, 100, 60) passato al <xref:System.Drawing.Graphics.FillEllipse%2A> metodo specificare il percorso e le dimensioni del rettangolo di delimitazione dell'ellisse. Il rettangolo dispone di un angolo superiore sinistro del (0, 0), la larghezza è pari a 100 e altezza pari a 60.  
  
 [!code-csharp[System.Drawing.UsingABrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio precedente è progettato per l'uso con Windows Form e richiede <xref:System.Windows.Forms.PaintEventArgs> `e`, ovvero un parametro del <xref:System.Windows.Forms.Control.Paint> gestore dell'evento.  
  
## <a name="see-also"></a>Vedere anche

- [Uso di un oggetto Brush per il riempimento di forme](using-a-brush-to-fill-shapes.md)
