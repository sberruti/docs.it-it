---
title: Clausola orderby (Riferimento C#)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: cd76b2c33fe1a1a986bc05e3c3ed5f22809686ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173575"
---
# <a name="orderby-clause-c-reference"></a>Clausola orderby (Riferimento C#)

In un'espressione di query, la clausola `orderby` fa in modo che la sequenza o la sottosequenza (gruppo) restituita venga ordinata in modo crescente o decrescente. È possibile specificare più chiavi per eseguire una o più operazioni di ordinamento secondarie. L'ordinamento viene eseguito dall'operatore di confronto predefinito per il tipo dell'elemento. Per impostazione predefinita, l'ordinamento è crescente. È possibile specificare anche un operatore di confronto personalizzato, che sarà tuttavia disponibile solo se si usa la sintassi basata sul metodo. Per altre informazioni, vedere [Ordinamento dei dati](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Esempio

Nell'esempio seguente, la prima query ordina le parole alfabeticamente a partire da A, la seconda ordina le stesse parole in ordine decrescente. La parola chiave `ascending` è il valore di ordinamento predefinito e può essere omessa.

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Esempio

Nell'esempio seguente viene eseguito un ordinamento primario sui cognomi degli studenti e quindi un ordinamento secondario sui nomi.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Osservazioni

In fase di compilazione, la clausola `orderby` viene convertita in una chiamata al metodo <xref:System.Linq.Enumerable.OrderBy%2A>. Eventuali chiavi multiple nella clausola `orderby` vengono convertite in chiamate al metodo <xref:System.Linq.Enumerable.ThenBy%2A>.

## <a name="see-also"></a>Vedere anche

- [Guida di riferimento a C](../index.md)
- [Parole chiave di query (LINQ)Query Keywords (LINQ)](query-keywords.md)
- [LINQ in C#](../../linq/index.md)
- [Clausola group](group-clause.md)
- [Language Integrated Query (LINQ)](../../programming-guide/concepts/linq/index.md)
