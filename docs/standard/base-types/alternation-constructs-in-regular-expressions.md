---
title: Costrutti di alternanza nelle espressioni regolari .NET
description: Informazioni su come usare i costrutti di alternanza per la corrispondenza condizionale nelle espressioni regolari.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- either/or matching
- alternative matching patterns
- regular expressions, alternation constructs
- alternation constructs
- optional matching patterns
- constructs, alternation
- .NET Framework regular expressions, alternation constructs
ms.assetid: 071e22e9-fbb0-4ecf-add1-8d2424f9f2d1
ms.openlocfilehash: 02664bd2812f89649ec933483161263bae530a75
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159689"
---
# <a name="alternation-constructs-in-regular-expressions"></a>Costrutti di alternanza nelle espressioni regolari

I costrutti di alternanza modificano un'espressione regolare per abilitare la corrispondenza di tipo either/or o condizionale. .NET supporta tre costrutti di alternanza:

- [Criteri di ricerca con &#124;](#Either_Or)
- [Corrispondenza condizionale con (?(espressione)yes&#124;no)](#Conditional_Expr)
- [Corrispondenza condizionale in base a un gruppo di acquisizione valido](#Conditional_Group)

<a name="Either_Or"></a>
## <a name="pattern-matching-with-124"></a>Criteri di ricerca con &#124;

È possibile usare la barra verticale (`|`) per trovare la corrispondenza con uno qualsiasi di una serie di criteri, dove i singoli criteri sono separati dal carattere `|` .

Analogamente alla classe di caratteri positivi, il carattere `|` può essere usato per trovare la corrispondenza con uno qualsiasi tra diversi caratteri singoli. L'esempio seguente usa sia una classe di caratteri positivi sia criteri di ricerca di tipo either/or con il carattere `|` per individuare le occorrenze delle parole "gray" o "grey" in una stringa. In questo caso il carattere `|` produce un'espressione regolare più dettagliata.

[!code-csharp[RegularExpressions.Language.Alternation#1](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation1.cs#1)]
[!code-vb[RegularExpressions.Language.Alternation#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation1.vb#1)]

L'espressione regolare che usa il carattere `|`, `\bgr(a|e)y\b`, viene interpretata come illustrato nella tabella seguente:

|Modello|Descrizione|  
|-------------|-----------------|  
|`\b`|Inizia dal confine di una parola.|  
|`gr`|Corrisponde ai caratteri "gr".|  
|<code>(a&#124;e)</code>|Corrisponde a una "a" o una "e".|  
|`y\b`|Corrisponde a una "y" in un confine di parola.|  

Il carattere `|` può essere usato anche per trovare una corrispondenza di tipo either/or con più caratteri o sottoesspressioni, che possono includere qualsiasi combinazione di valori letterali carattere ed elementi del linguaggio di espressioni regolari. (La classe di caratteri non fornisce questa funzionalità). Nell'esempio seguente viene usato il carattere `|` per estrarre un numero di previdenza sociale (SSN) statunitense, ovvero un numero a 9 cifre con formato *ddd*-*DD*-*dddd*o un numero di identificazione del datore di lavoro (EIN) statunitense, che è un numero a 9 cifre con formato *GG*-*ddddddd*.

[!code-csharp[RegularExpressions.Language.Alternation#2](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation2.cs#2)]
[!code-vb[RegularExpressions.Language.Alternation#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation2.vb#2)]  

L'espressione regolare `\b(\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` viene interpretata come illustrato nella tabella seguente:
  
|Modello|Descrizione|  
|-------------|-----------------|  
|`\b`|Inizia dal confine di una parola.|  
|<code>(\d{2}-\d{7}&#124;\d{3}-\d{2}-\d{4})</code>|Corrisponde a una delle due opzioni seguenti: due cifre decimali seguite da un trattino seguito da sette cifre decimali oppure tre cifre decimali, un trattino, due cifre decimali, un altro trattino e quattro cifre decimali.|  
|`\d`|Termina la corrispondenza sul confine di parola.|  
  
<a name="Conditional_Expr"></a>
## <a name="conditional-matching-with-an-expression"></a>Corrispondenza condizionale con un'espressione

Questo elemento del linguaggio tenta di trovare una corrispondenza con uno di due criteri, a seconda della possibilità di trovare una corrispondenza con un criterio iniziale. La relativa sintassi è la seguente:  

`(?(` *espressione* `)` *sì* `|` *No* `)`

dove *espressione* è il criterio iniziale per la corrispondenza, *sì* è il criterio di corrispondenza se viene trovata una corrispondenza per *espressione* e *no* è il criterio facoltativo di corrispondenza se non viene trovata una corrispondenza per *espressione* . Il motore delle espressioni regolari considera *espressione* come un'asserzione di larghezza zero, ovvero questo motore non avanza nel flusso di input dopo aver valutato *espressione*. Questo costrutto è pertanto equivalente a quanto segue:

`(?(?=` *espressione* `)` *sì* `|` *No* `)`

dove `(?=`*espressione*`)` è un costrutto di asserzione di larghezza zero. Per ulteriori informazioni, vedere [costrutti di raggruppamento](grouping-constructs-in-regular-expressions.md). Poiché il motore delle espressioni regolari interpreta *espressione* come un ancoraggio (un'asserzione di larghezza zero), *Expression* deve essere un'asserzione di larghezza zero (per altre informazioni, vedere [ancoraggi](anchors-in-regular-expressions.md)) o una sottoespressione anch ' essa contenuta in *Yes*. In caso contrario, non è possibile trovare una corrispondenza per il criterio *yes*.  
  
> [!NOTE]
> Se *Expression* è un gruppo di acquisizione denominato o numerato, il costrutto di alternanza viene interpretato come un test di acquisizione. Per ulteriori informazioni, vedere la sezione successiva, [corrispondenza condizionale basata su un gruppo Capture valido](#Conditional_Group). In altre parole, il motore delle espressioni regolari non tenta di trovare la corrispondenza con la sottostringa acquisita, ma verifica invece la presenza o l'assenza del gruppo.  
  
L'esempio seguente è una variante dell'esempio visualizzato nella sezione relativa ai [criteri di ricerca either/or con &#124;](#Either_Or). L'esempio usa la corrispondenza condizionale per determinare se i primi tre caratteri dopo un confine di parola sono due cifre seguite da un trattino. In caso affermativo, viene effettuato un tentativo di trovare una corrispondenza con un identificativo del datore di lavoro (EIN) degli Stati Uniti. In caso contrario, viene effettuato un tentativo di trovare una corrispondenza con un numero di previdenza sociale (SSN) degli Stati Uniti.

[!code-csharp[RegularExpressions.Language.Alternation#3](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation3.cs#3)]
[!code-vb[RegularExpressions.Language.Alternation#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation3.vb#3)]

Il criterio di ricerca di espressioni regolari `\b(?(\d{2}-)\d{2}-\d{7}|\d{3}-\d{2}-\d{4})\b` viene interpretato come illustrato nella tabella seguente:

|Modello|Descrizione|  
|-------------|-----------------|  
|`\b`|Inizia dal confine di una parola.|  
|`(?(\d{2}-)`|Determina se i tre caratteri successivi sono costituiti da due cifre seguite da un trattino.|  
|`\d{2}-\d{7}`|Se il criterio precedente viene soddisfatto, trova la corrispondenza con due cifre seguite da un trattino seguito da sette cifre.|  
|`\d{3}-\d{2}-\d{4}`|Se il criterio precedente non viene soddisfatto, trova la corrispondenza con tre cifre decimali, un trattino, due cifre decimali, un altro trattino e quattro cifre decimali.|  
|`\b`|Trova la corrispondenza di un confine di parola.|  

<a name="Conditional_Group"></a>
## <a name="conditional-matching-based-on-a-valid-captured-group"></a>Corrispondenza condizionale in base a un gruppo acquisito valido

Tramite questo elemento di linguaggio viene effettuato un tentativo di corrispondenza con uno dei due modelli, a seconda dell'effettiva corrispondenza con un gruppo di acquisizione specificato. La relativa sintassi è la seguente:

`(?(` *nome* `)` *sì* `|` *No* `)`

o

`(?(` *numero* `)` *sì* `|` *No* `)`

dove *nome* è il nome e *numero* è il numero di un gruppo di acquisizione, *sì* è l'espressione di cui trovare la corrispondenza se per *nome* o *numero* è disponibile una corrispondenza e *no* è l'espressione facoltativa di cui trovare la corrispondenza in caso contrario.

Se *nome* non corrisponde al nome di un gruppo di acquisizione usato nel criterio di espressione regolare, il costrutto di alternanza viene interpretato come un test di espressione, come illustrato nella sezione precedente. In genere, ciò significa che *espressione* restituisce `false`. Se *numero* non corrisponde a un gruppo di acquisizione numerato usato nel criterio di espressione regolare, il motore delle espressioni regolari genera un'eccezione <xref:System.ArgumentException>.

L'esempio seguente è una variante dell'esempio visualizzato nella sezione relativa ai [criteri di ricerca either/or con &#124;](#Either_Or). L'esempio usa un gruppo di acquisizione denominato `n2` costituito da due cifre seguite da un trattino. Il costrutto di alternanza verifica se per questo gruppo di acquisizione è presente una corrispondenza nella stringa di input. In caso affermativo, il costrutto di alternanza tenta di trovare la corrispondenza con le ultime sette cifre delle nove cifre di un identificativo del datore di lavoro (EIN) degli Stati Uniti. In caso contrario, tenta di trovare la corrispondenza con le nove cifre di un numero di previdenza sociale (SSN) degli Stati Uniti.

[!code-csharp[RegularExpressions.Language.Alternation#4](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation4.cs#4)]
[!code-vb[RegularExpressions.Language.Alternation#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation4.vb#4)]

Il criterio di ricerca di espressioni regolari `\b(?<n2>\d{2}-)?(?(n2)\d{7}|\d{3}-\d{2}-\d{4})\b` viene interpretato come illustrato nella tabella seguente:

|Modello|Descrizione|  
|-------------|-----------------|  
|`\b`|Inizia dal confine di una parola.|  
|`(?<n2>\d{2}-)?`|Corrisponde a zero o una occorrenza di due cifre seguite da un trattino. Il nome di questo gruppo di acquisizione è `n2`.|  
|`(?(n2)`|Verificare se per `n2` è stata individuata una corrispondenza nella stringa di input.|  
|`\d{7}`|Se per `n2` è stata individuata una corrispondenza, far corrispondere sette cifre decimali.|  
|<code>&#124;\d{3}-\d{2}-\d{4}</code>|Se per `n2` non è stata trovata alcuna corrispondenza, far corrispondere tre cifre decimali, un trattino, due cifre decimali, un altro trattino e quattro cifre decimali.|  
|`\b`|Trova la corrispondenza di un confine di parola.|  

Nell'esempio seguente è illustrata una variante di questo esempio che usa un gruppo numerato anziché un gruppo denominato. Il criterio di espressione regolare è `\b(\d{2}-)?(?(1)\d{7}|\d{3}-\d{2}-\d{4})\b`.

[!code-csharp[RegularExpressions.Language.Alternation#5](~/samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.alternation/cs/alternation5.cs#5)]
[!code-vb[RegularExpressions.Language.Alternation#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.alternation/vb/alternation5.vb#5)]

## <a name="see-also"></a>Vedere anche

- [Linguaggio di espressioni regolari - Riferimento rapido](regular-expression-language-quick-reference.md)
