---
title: 'Esempi di sintassi delle query basate su metodo: Conversione'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: a78588cb4bd09f8a8a8ce8ed4a60dd45fce1d386
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397488"
---
# <a name="method-based-query-syntax-examples-conversion"></a>Esempi di sintassi delle query basate su metodo: Conversione
Negli esempi di questo argomento viene illustrato come usare i <xref:System.Linq.Enumerable.ToArray%2A>metodi <xref:System.Linq.Enumerable.ToDictionary%2A> , <xref:System.Linq.Enumerable.ToList%2A> e per eseguire query sul [modello Sales di AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) usando la sintassi delle query basate su metodo. Il modello Sales di AdventureWorks usato in questi esempi è compilato in base alle tabelle Contact, Address, Product, SalesOrderHeader e SalesOrderDetail del database di esempio AdventureWorks.  
  
 Negli esempi di questo argomento vengono utilizzate le `using` istruzioni seguenti: / `Imports`  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a>ToArray  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene usato il metodo <xref:System.Linq.Enumerable.ToArray%2A> per restituire immediatamente una matrice da una sequenza.  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a>ToDictionary  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene usato il metodo <xref:System.Linq.Enumerable.ToDictionary%2A> per restituire immediatamente un dizionario da una sequenza e un'espressione chiave correlata.  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a>ToList  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene usato il metodo <xref:System.Linq.Enumerable.ToList%2A> per restituire immediatamente un oggetto <xref:System.Collections.Generic.List%601>, dove `T` è di tipo <xref:System.Data.DataRow>, da una sequenza.  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a>Vedere anche

- [Query in LINQ to Entities](queries-in-linq-to-entities.md)
