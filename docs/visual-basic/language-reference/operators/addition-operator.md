---
title: + Operatore
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 12c14b3be0562a31470ddbd2d5489ccdbdf3b62b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350285"
---
# <a name="-operator-visual-basic"></a>Operatore + (Visual Basic)
Somma due numeri o restituisce il valore positivo di un'espressione numerica. Può essere usato anche per concatenare due espressioni stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```vb
expression1 + expression2
```
  
oppure

```vb  
+expression1  
```  
  
## <a name="parts"></a>Parti  
  
|Termine|Definizione|  
|---|---|  
|`expression1`|Obbligatoria. Qualsiasi espressione numerica o stringa.|  
|`expression2`|Obbligatorio a meno che l'operatore `+` non calcoli un valore negativo. Qualsiasi espressione numerica o stringa.|  
  
## <a name="result"></a>Risultato  
 Se `expression1` e `expression2` sono entrambi numerici, il risultato è la somma aritmetica.  
  
 Se `expression2` è assente, l'operatore `+` è l'operatore di identità *unario* per il valore non modificato di un'espressione. In questo senso, l'operazione consiste nel mantenere il segno di `expression1`, quindi il risultato è negativo se `expression1` è negativo.  
  
 Se `expression1` e `expression2` sono entrambe stringhe, il risultato è la concatenazione dei relativi valori.  
  
 Se `expression1` e `expression2` sono di tipi misti, l'azione eseguita dipende dai relativi tipi, dal relativo contenuto e dall'impostazione dell' [istruzione Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). Per ulteriori informazioni, vedere le tabelle in "osservazioni".  
  
## <a name="supported-types"></a>Tipi supportati  
 Tutti i tipi numerici, inclusi i tipi senza segno e a virgola mobile e `Decimal`e `String`.  
  
## <a name="remarks"></a>Osservazioni  
 In generale, `+` esegue l'aggiunta aritmetica, quando possibile, e concatena solo quando entrambe le espressioni sono stringhe.  
  
 Se nessuna delle due espressioni è una `Object`, Visual Basic esegue le azioni seguenti.  
  
|Tipi di dati delle espressioni|Azione per compilatore|  
|---|---|  
|Entrambe le espressioni sono tipi di dati numerici (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`o `Double`)|Aggiungi. Il tipo di dati del risultato è un tipo numerico appropriato per i tipi di dati di `expression1` e `expression2`. Vedere le tabelle "aritmetiche di interi" nei [tipi di dati dei risultati dell'operatore](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Entrambe le espressioni sono di tipo `String`|Concatenare.|  
|Un'espressione è un tipo di dati numerico e l'altra è una stringa|Se `Option Strict` è `On`, genera un errore del compilatore.<br /><br /> Se `Option Strict` è `Off`, convertire in modo implicito il `String` in `Double` e aggiungere.<br /><br /> Se non è possibile convertire il `String` in `Double`, generare un'eccezione <xref:System.InvalidCastException>.|  
|Un'espressione è un tipo di dati numerico e l'altra [non è nulla](../../../visual-basic/language-reference/nothing.md)|Aggiungere, con `Nothing` valore pari a zero.|  
|Un'espressione è una stringa e l'altra è `Nothing`|Concatenate, con `Nothing` valore "".|  
  
 Se un'espressione è un'espressione `Object`, Visual Basic esegue le azioni seguenti.  
  
|Tipi di dati delle espressioni|Azione per compilatore|  
|---|---|  
|`Object` espressione include un valore numerico e l'altro è un tipo di dati numerico|Se `Option Strict` è `On`, genera un errore del compilatore.<br /><br /> Se `Option Strict` è `Off`, aggiungere.|  
|`Object` espressione include un valore numerico e l'altro è di tipo `String`|Se `Option Strict` è `On`, genera un errore del compilatore.<br /><br /> Se `Option Strict` è `Off`, convertire in modo implicito il `String` in `Double` e aggiungere.<br /><br /> Se non è possibile convertire il `String` in `Double`, generare un'eccezione <xref:System.InvalidCastException>.|  
|`Object` espressione include una stringa e l'altra è un tipo di dati numerico|Se `Option Strict` è `On`, genera un errore del compilatore.<br /><br /> Se `Option Strict` è `Off`, convertire in modo implicito la stringa `Object` `Double` e aggiungere.<br /><br /> Se non è possibile convertire la stringa `Object` in `Double`, generare un'eccezione <xref:System.InvalidCastException>.|  
|`Object` espressione include una stringa e l'altra è di tipo `String`|Se `Option Strict` è `On`, genera un errore del compilatore.<br /><br /> Se `Option Strict` è `Off`, convertire in modo implicito `Object` in `String` e concatenare.|  
  
 Se entrambe le espressioni sono `Object` espressioni, Visual Basic esegue le azioni seguenti (solo`Option Strict Off`).  
  
|Tipi di dati delle espressioni|Azione per compilatore|  
|---|---|  
|Entrambe le espressioni `Object` contengono valori numerici|Aggiungi.|  
|Entrambe `Object` espressioni sono di tipo `String`|Concatenare.|  
|Una `Object` espressione include un valore numerico e l'altra include una stringa|Converte in modo implicito la stringa `Object` in `Double` e Aggiungi.<br /><br /> Se la stringa `Object` non può essere convertita in un valore numerico, generare un'eccezione <xref:System.InvalidCastException>.|  
  
 Se un'espressione `Object` restituisce [Nothing](../../../visual-basic/language-reference/nothing.md) o <xref:System.DBNull>, l'operatore `+` lo considera come un `String` con un valore di "".  
  
> [!NOTE]
> Quando si usa l'operatore di `+`, potrebbe non essere possibile determinare se si verificherà la concatenazione dell'aggiunta o della stringa. Usare l'operatore `&` per la concatenazione per eliminare l'ambiguità e per fornire codice autodocumentato.  
  
## <a name="overloading"></a>Overload  
 L'operatore `+` può essere sottoposto a *Overload*, il che significa che una classe o una struttura può ridefinire il comportamento quando un operando ha il tipo della classe o della struttura. Se il codice usa questo operatore su una classe o una struttura di questo tipo, assicurarsi di comprendere il comportamento ridefinito. Per altre informazioni, vedere [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene usato l'operatore `+` per aggiungere numeri. Se gli operandi sono entrambi numerici, Visual Basic calcola il risultato aritmetico. Il risultato aritmetico rappresenta la somma dei due operandi.  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 È anche possibile usare l'operatore `+` per concatenare le stringhe. Se gli operandi sono entrambe stringhe, Visual Basic li concatena. Il risultato della concatenazione rappresenta una singola stringa costituita dal contenuto dei due operandi uno dopo l'altro.  
  
 Se gli operandi sono di tipo misto, il risultato dipende dall'impostazione dell' [istruzione Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md). Nell'esempio seguente viene illustrato il risultato quando `Option Strict` viene `On`.  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 Nell'esempio seguente viene illustrato il risultato quando `Option Strict` viene `Off`.  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 Per evitare ambiguità, è consigliabile usare l'operatore `&` anziché `+` per la concatenazione.  
  
## <a name="see-also"></a>Vedere anche

- [Operatore &](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [Operatori di concatenazione](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Operatori aritmetici](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Elenco degli operatori per funzionalità](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Precedenza tra gli operatori in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatori aritmetici in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Istruzione Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
