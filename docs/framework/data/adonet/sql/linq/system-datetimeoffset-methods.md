---
title: Metodi System.DateTimeOffset
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 2e29cf02d4f7e8004782264bf940bb1faf393269
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781557"
---
# <a name="systemdatetimeoffset-methods"></a>Metodi System.DateTimeOffset
Una volta eseguito il mapping nel modello a oggetti o nel file di mapping esterno, LINQ to SQL consente di chiamare la maggior parte degli operatori, delle proprietà e dei metodi <xref:System.DateTimeOffset?displayProperty=nameWithType> dalle query LINQ to SQL.  
  
 Gli unici metodi non supportati sono quelli ereditati da <xref:System.Object?displayProperty=nameWithType> che non hanno senso nel contesto delle query LINQ to SQL, ad esempio `Finalize`, `GetHashCode`, `GetType` e `MemberwiseClone`. Questi metodi non sono supportati in quanto LINQ to SQL non è in grado di convertirli per l'esecuzione in SQL Server.  
  
> [!NOTE]
> La struttura di <xref:System.DateTimeOffset?displayProperty=nameWithType> CLR (Common Language Runtime) e la possibilità da eseguire il mapping a una colonna `DATETIMEOFFSET` SQL con LINQ to SQL richiedono .NET Framework 3.5 SP1 o versione successiva. La colonna `DATETIMEOFFSET` SQL è disponibile solo in Microsoft SQL Server 2008 e versioni successive.  
  
## <a name="sqlmethods-date-and-time-methods"></a>Metodi SQLMethods relativi a data e ora  
 Oltre ai metodi offerti dalla struttura di <xref:System.DateTimeOffset>, LINQ to SQL offre i metodi della classe <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> elencati nella tabella seguente per l'uso di data e ora.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Vedere anche

- [Concetti relativi alle query](query-concepts.md)
- [Creazione del modello a oggetti](creating-the-object-model.md)
- [Mapping del tipo SQL-CLR](sql-clr-type-mapping.md)
