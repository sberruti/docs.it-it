---
ms.openlocfilehash: 33c262ebe131aade2b32d824395721f098640cf9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857473"
---
### <a name="connection-pool-blocking-period-for-azure-sql-databases-is-removed"></a>Il periodo di blocco del pool di connessioni per i database SQL di Azure è stato rimosso

|   |   |
|---|---|
|Dettagli|A partire da .NET Framework 4.6.2, in caso di richieste di apertura connessioni a database SQL di Azure noti (*.database.windows.net, *.database.chinacloudapi.cn, *.database.usgovcloudapi.net, *.database.cloudapi.de), il periodo di blocco del pool di connessioni viene rimosso ed eventuali errori di apertura connessioni non vengono memorizzati nella cache. Dopo gli errori di connessione del transiente, verranno effettuati tentativi quasi istantanei per ripetere le richieste di connessione aperte. Questa modifica consente di ritentare immediatamente l'apertura di una connessione ai database SQL di Azure, migliorando così le prestazioni delle app abilitate per il cloud. Per tutti gli altri tentativi di connessione continua a essere applicato il periodo di blocco del pool di connessioni.<p/>In .NET Framework 4.6.1 e versioni precedenti, se un'applicazione rileva un errore di connessione temporanea mentre si connette a un database, non è possibile ritentare subito la connessione, perché il pool di connessioni memorizza l'errore nella cache e lo rigenera per un periodo compreso tra 5 secondi e 1 minuto. Per altre informazioni, vedere [Pool di connessioni SQL Server (ADO.NET)](~/docs/framework/data/adonet/sql-server-connection-pooling.md). Questo comportamento può causare problemi con le connessioni a database SQL di Azure, che spesso hanno esito negativo in caso di errori temporanei che vengono generalmente ripristinati nell'arco di pochi secondi. Con la funzionalità di blocco del pool di connessioni, l'app non può connettersi al database per un periodo esteso, anche se il database è disponibile e il rendering dell'app deve essere eseguito entro pochi secondi.|
|Suggerimento|Se questo comportamento non è auspicabile, il periodo di blocco del pool di connessioni può essere configurato impostando la proprietà <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> introdotta in .NET Framework 4.6.2. Il valore della proprietà è un membro dell'enumerazione <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=name> che può assumere uno dei tre valori seguenti:<ul><li><xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.Auto></li><li><xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock></li></ul>È possibile ripristinare il comportamento precedente impostando la proprietà <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod?displayProperty=name> su <xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>.|
|Scope|Minorenne|
|Versione|4.6.2|
|Type|Runtime|
|API interessate|<ul><li><xref:System.Data.Common.DbConnection.OpenAsync?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
