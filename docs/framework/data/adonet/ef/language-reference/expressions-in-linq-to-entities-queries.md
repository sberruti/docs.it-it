---
title: Espressioni in query di LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: e625ac3968542c65e737093c0ac292de4c2ffa37
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854467"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Espressioni in query di LINQ to Entities
Un'espressione è un frammento di codice che può restituire un singolo valore, oggetto, metodo o spazio dei nomi. Le espressioni possono contenere un valore letterale, una chiamata al metodo, un operatore e i relativi operandi oppure un nome semplice, ad esempio il nome di una variabile, un membro di un tipo, un parametro di un metodo, uno spazio dei nomi o un tipo. Le espressioni possono usare operatori che a loro volta usano altre espressioni come parametri oppure chiamate a metodi i cui parametri sono a loro volta altre chiamate a metodi. Le espressioni possono pertanto essere da semplici a molto complesse.  
  
 Nelle query LINQ to Entities, le espressioni possono contenere qualsiasi elemento consentito dai tipi all' <xref:System.Linq.Expressions> interno dello spazio dei nomi, incluse le espressioni lambda. Le espressioni che possono essere utilizzate nelle query LINQ to Entities sono un superset delle espressioni che possono essere utilizzate per eseguire query sul Entity Framework. le espressioni che fanno parte di query sul Entity Framework sono limitate alle operazioni supportate da `ObjectQuery<T>` e origine dati sottostante.  
  
 Nell'esempio seguente il confronto nella clausola `Where` è un'espressione:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> Costrutti di linguaggio specifici, ad C# `unchecked`esempio, non hanno significato in LINQ to Entities.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Espressioni costanti](constant-expressions.md)  
  
 [Espressioni di confronto](comparison-expressions.md)  
  
 [Confronti Null](null-comparisons.md)  
  
 [Espressioni di inizializzazione](initialization-expressions.md)  
  
 [Relazioni, proprietà di navigazione e chiavi esterne](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Vedere anche

- [ADO.NET Entity Framework](../index.md)
