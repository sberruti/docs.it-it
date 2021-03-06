---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: f9e33c78235f637e0aa0622d9d8cc30255722beb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319679"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
Determina se un oggetto `String` di caratteri specifico corrisponde a un criterio specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>argomenti  
 `match`  
 Espressione [!INCLUDE[esql](../../../../../../includes/esql-md.md)] che restituisce una `String`.  
  
 `pattern`  
 Criterio da confrontare con l'oggetto `String` specificato.  
  
 `escape`  
 Carattere di escape.  
  
 NOT  
 Specifica la negazione del risultato di LIKE.  
  
## <a name="return-value"></a>Valore restituito  
 `true` se `string` corrisponde al criterio; in caso contrario, `false`.  
  
## <a name="remarks"></a>Note  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] espressioni che utilizzano l'operatore LIKE vengono valutate in modo analogo alle espressioni che utilizzano l'uguaglianza come criteri di filtro. Tuttavia, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] espressioni che usano l'operatore LIKE possono includere sia valori letterali che caratteri jolly.  
  
 Nella tabella seguente viene descritta la sintassi del modello `string`.  
  
|Carattere jolly|Descrizione|Esempio|  
|------------------------|-----------------|-------------|  
|%|Qualsiasi `string` di zero o più caratteri.|`title like '%computer%'` trova tutti i titoli con la parola `"computer"` in qualsiasi punto del titolo.|  
|_ (carattere di sottolineatura)|Qualsiasi carattere singolo.|`firstname like '_ean'` trova tutti i nomi di quattro lettere che terminano con `"ean` ", ad esempio Dean o Sean.|  
|[ ]|Qualsiasi carattere singolo compreso nell'intervallo ([a-f]) o nel set ([abcdef]) specificato.|`lastname like '[C-P]arsen'` trova i cognomi che terminano con "Assn" e iniziano con qualsiasi carattere singolo compreso tra C e P, ad esempio Carsen o Larsen.|  
|[^]|Qualsiasi carattere singolo non compreso nell'intervallo ([^a-f]) o nel set ([^abcdef]) specificato.|`lastname like 'de[^l]%'` trova tutti i cognomi che iniziano con "de" e non includono "l" come lettera seguente.|  
  
> [!NOTE]
> La clausola ESCAPE e l'operatore LIKE [!INCLUDE[esql](../../../../../../includes/esql-md.md)] non possono essere applicati ai valori `System.DateTime` o `System.Guid`.  
  
 LIKE supporta i criteri di ricerca ASCII e Unicode. Quando tutti i parametri sono caratteri ASCII, viene eseguita una ricerca ASCII. Se uno o più argomenti sono di tipo Unicode, tutti gli argomenti vengono convertiti in Unicode e viene eseguita una ricerca Unicode. Quando si usa il formato Unicode con LIKE, gli spazi finali sono significativi, a differenza del formato non Unicode, in cui gli spazi finali non sono significativi. La sintassi della stringa di modello di [!INCLUDE[esql](../../../../../../includes/esql-md.md)] è identica a quella di Transact-SQL.  
  
 Un criterio può includere caratteri normali e caratteri jolly. Durante la ricerca i caratteri normali devono corrispondere esattamente ai caratteri specificati nell'oggetto `string` di caratteri. I caratteri jolly possono tuttavia corrispondere a frammenti arbitrari della stringa di caratteri. Quando viene usato con i caratteri jolly, l'operatore LIKE è più flessibile rispetto agli operatori di confronto tra stringhe = e !=.  
  
> [!NOTE]
> Se la destinazione è costituita da un provider specifico, è possibile usare estensioni specifiche del provider. Tali costrutti possono tuttavia essere trattati in modo diverso, ad esempio da altri provider. SqlServer supporta ad esempio i modelli [first-last] e [^first-last], dove il primo consente di trovare una corrispondenza esatta di un carattere compreso tra il primo e l'ultimo, mentre il secondo consente di trovare una corrispondenza esatta di un carattere non compreso tra il primo e l'ultimo.  
  
### <a name="escape"></a>Escape  
 Usando la clausola ESCAPE, è possibile cercare stringhe di caratteri che includono uno o più dei caratteri jolly speciali descritti nella tabella nella sezione precedente. Si presupponga, ad esempio, che diversi documenti includano il valore letterale "100%" nel titolo e che si desideri cercare tutti i documenti di questo tipo. Poiché la percentuale (%) il carattere è un carattere jolly, quindi è necessario utilizzare la clausola escape [!INCLUDE[esql](../../../../../../includes/esql-md.md)] per eseguire correttamente la ricerca. Di seguito viene illustrato un esempio di questo filtro.  
  
```sql  
"title like '%100!%%' escape '!'"  
```  
  
 In questa espressione di ricerca il carattere jolly di percentuale (%) immediatamente successivo al carattere punto esclamativo (!) viene trattato come valore letterale anziché come carattere jolly. È possibile utilizzare qualsiasi carattere come carattere di escape, ad eccezione dei caratteri jolly [!INCLUDE[esql](../../../../../../includes/esql-md.md)] e della parentesi quadra (`[ ]`). Nell'esempio precedente il carattere punto esclamativo (!) è il carattere di escape.  
  
## <a name="example"></a>Esempio  
 Le due query seguenti [!INCLUDE[esql](../../../../../../includes/esql-md.md)] usano gli operatori LIKE e ESCAPE per determinare se una stringa di caratteri specifica corrisponde a un modello specificato. La prima query cerca la `Name` che inizia con i caratteri `Down_`. In questa query viene usata l'opzione ESCAPE perché la sottolineatura (`_`) è un carattere jolly. Senza l'opzione ESCAPE, tramite la query verrebbe eseguita una ricerca di qualsiasi valore `Name` che inizia con la parola `Down` seguita da qualsiasi carattere singolo diverso dal carattere di sottolineatura. Le query sono basate sul modello Sales di AdventureWorks. Per compilare ed eseguire questa query, effettuare le operazioni seguenti:  
  
1. Attenersi alla procedura descritta in [procedura: eseguire una query che restituisce i risultati di PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Passare la query seguente come argomento al metodo `ExecutePrimitiveTypeQuery` :  
  
 [!code-sql[DP EntityServices Concepts#LIKE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#like)]  
  
## <a name="see-also"></a>Vedere anche

- [Riferimento a Entity SQL](entity-sql-reference.md)
