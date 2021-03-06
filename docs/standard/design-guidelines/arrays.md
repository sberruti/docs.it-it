---
title: Matrici
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: d4a1f379a88231654c710b1df7b505316377c915
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741796"
---
# <a name="arrays"></a>Matrici
✔️ preferiscono usare le raccolte su matrici in API pubbliche. La sezione [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) fornisce informazioni dettagliate su come scegliere tra le raccolte e le matrici.

 ❌ non utilizzano campi di matrice di sola lettura. Il campo stesso è di sola lettura e non può essere modificato, ma è possibile modificare gli elementi della matrice.

 ✔️ CONSIGLIABILE utilizzare matrici di matrici anziché matrici multidimensionali.

 Una matrice irregolare è una matrice con elementi che sono anche matrici. Le matrici che costituiscono gli elementi possono avere dimensioni diverse, causando uno spazio meno sprecato per alcuni set di dati (ad esempio, una matrice di tipo sparse) rispetto alle matrici multidimensionali. Inoltre, CLR ottimizza le operazioni sugli indici su matrici di matrici, in modo che possano presentare prestazioni di runtime migliori in alcuni scenari.

 *Parti © 2005, 2009 Microsoft Corporation. Tutti i diritti riservati.*

 *Ristampato con l'autorizzazione di Pearson Education, Inc. da [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2a edizione](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) di Krzysztof Cwalina and Brad Abrams, pubblicato il 22 ottobre 2008 da Addison-Wesley Professional nella collana Microsoft Windows Development Series.*

## <a name="see-also"></a>Vedere anche

- <xref:System.Array>
- [Linee guida per la progettazione di Framework](../../../docs/standard/design-guidelines/index.md)
- [Linee guida per l'uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
