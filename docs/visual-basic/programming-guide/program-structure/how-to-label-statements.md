---
title: 'Procedura: etichettare le istruzioni'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: be116ac8046c43e89e44c2d9127c6131e4dfaa52
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347374"
---
# <a name="how-to-label-statements-visual-basic"></a>Procedura: etichettare le istruzioni (Visual Basic)

I blocchi di istruzioni sono costituiti da righe di codice delimitate da due punti. Le righe di codice precedute da una stringa di identificazione o un numero intero sono *denominate etichettate*. Le etichette di istruzione vengono usate per contrassegnare una riga di codice per identificarla per l'uso con istruzioni come `On Error Goto`.

Le etichette possono essere identificatori Visual Basic validi, ad esempio quelli che identificano gli elementi di programmazione, o valori letterali integer. Un'etichetta deve essere visualizzata all'inizio di una riga di codice sorgente e deve essere seguita da due punti, indipendentemente dal fatto che sia seguita da un'istruzione nella stessa riga.

Il compilatore identifica le etichette controllando se l'inizio della riga corrisponde a qualsiasi identificatore già definito. In caso contrario, il compilatore presuppone che si tratta di un'etichetta.

Le etichette hanno uno spazio di dichiarazione e non interferiscono con altri identificatori. L'ambito di un'etichetta è il corpo del metodo. La dichiarazione di etichetta ha la precedenza in qualsiasi situazione ambigua.

> [!NOTE]
> Le etichette possono essere utilizzate solo su istruzioni eseguibili all'interno di metodi.

## <a name="to-label-a-line-of-code"></a>Per etichettare una riga di codice

Posizionare un identificatore, seguito da due punti, all'inizio della riga del codice sorgente.

Ad esempio, le righe di codice seguenti sono contrassegnate rispettivamente con `Jump` e `120`:

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a>Vedere anche

- [Istruzioni](../../../visual-basic/programming-guide/language-features/statements.md)
- [Nomi di elementi dichiarati](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Struttura del programma e convenzioni di scrittura del codice](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
