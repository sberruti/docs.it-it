---
title: 'Procedura: dichiarare una proprietà con livelli di accesso misti'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
ms.openlocfilehash: d74e23f33fbf7d9d29ab84b9b1bd4fc08863ac48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349688"
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Procedura: dichiarare una proprietà con livelli di accesso misti (Visual Basic)
Se si desidera che le procedure `Get` e `Set` su una proprietà dispongano di livelli di accesso diversi, è possibile utilizzare il livello più permissivo nell'istruzione `Property` e il livello più restrittivo nell'istruzione `Get` o `Set`. Si utilizzano livelli di accesso misti su una proprietà quando si desidera che determinate parti del codice siano in grado di ottenere il valore della proprietà e che alcune altre parti del codice siano in grado di modificare il valore.  
  
 Per altre informazioni sui livelli di accesso, vedere [livelli di accesso in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Per dichiarare una proprietà con livelli di accesso misti  
  
1. Dichiarare la proprietà in modo normale e specificare il livello di accesso meno restrittivo, ad esempio `Public`, nell'istruzione `Property`.  
  
2. Dichiarare la `Get` o la routine `Set` specificando il livello di accesso più restrittivo, ad esempio `Friend`.  
  
3. Non specificare un livello di accesso nell'altra routine della proprietà. Si presuppone il livello di accesso dichiarato nell'istruzione `Property`. È possibile limitare l'accesso solo a una delle routine della proprietà.  
  
     [!code-vb[VbVbcnProcedures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#10)]  
  
     Nell'esempio precedente, la procedura `Get` ha lo stesso accesso `Protected` della proprietà stessa, mentre la procedura di `Set` ha accesso `Private`. Una classe derivata da `employee` può leggere il valore `salary`, ma solo la classe `employee` può impostarla.  
  
## <a name="see-also"></a>Vedere anche

- [Routine](./index.md)
- [Routine Property](./property-procedures.md)
- [Parametri e argomenti delle routine](./procedure-parameters-and-arguments.md)
- [Istruzione Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Differenze tra proprietà e variabili in Visual Basic](./differences-between-properties-and-variables.md)
- [Procedura: Creare una proprietà](./how-to-create-a-property.md)
- [Procedura: Chiamare una routine di proprietà](./how-to-call-a-property-procedure.md)
- [Procedura: dichiarare e chiamare una proprietà predefinita in Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Procedura: Inserire un valore in una proprietà](./how-to-put-a-value-in-a-property.md)
- [Procedura: Ottenere un valore da una proprietà](./how-to-get-a-value-from-a-property.md)
