---
title: Esecuzione di operazioni batch tramite oggetti DataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: 62a61051e5b9d896f8a89ed3d2745859fc07a7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149258"
---
# <a name="performing-batch-operations-using-dataadapters"></a>Esecuzione di operazioni batch tramite oggetti DataAdapter
Il supporto batch in ADO.NET consente a un tipo <xref:System.Data.Common.DataAdapter> di raggruppare le operazioni INSERT, UPDATE e DELETE da un tipo <xref:System.Data.DataSet> o <xref:System.Data.DataTable> e di inviarle al server in batch, anziché inviare una singola operazione alla volta. La riduzione nel numero di percorsi di andata e ritorno al server determina in genere un notevole miglioramento delle prestazioni. Gli aggiornamenti batch sono supportati per i provider di dati .NET di SQL Server (<xref:System.Data.SqlClient>) e Oracle (<xref:System.Data.OracleClient>).  
  
 Per l'aggiornamento di un database con modifiche provenienti da un <xref:System.Data.DataSet>, nelle versioni precedenti di ADO.NET il metodo `Update` di un `DataAdapter` eseguiva gli aggiornamenti del database una riga alla volta. Scorrendo le righe nella <xref:System.Data.DataTable> specificata, ciascuna riga <xref:System.Data.DataRow> veniva esaminata per rilevare eventuali modifiche. Se la riga era stata modificata, veniva chiamato il comando appropriato `UpdateCommand`, `InsertCommand` o `DeleteCommand`, in base al valore della proprietà <xref:System.Data.DataRow.RowState%2A> per quella determinata riga. Ogni aggiornamento di riga comportava un percorso di andata e ritorno in rete al database.  
  
 A partire da ADO.NET 2.0, <xref:System.Data.Common.DbDataAdapter> espone una proprietà <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A>. Impostando `UpdateBatchSize` su un valore intero positivo, gli aggiornamenti vengono inviati al database come batch della dimensione specificata. Ad esempio, impostando `UpdateBatchSize` su 10, verranno raggruppate 10 istruzioni separate e inviate come singolo batch. Impostando `UpdateBatchSize` su 0, il <xref:System.Data.Common.DataAdapter> utilizzerà la dimensione di batch massima che il server è in grado di gestire. Se invece si imposta il valore su 1, gli aggiornamenti batch vengono disabilitati, in quanto le righe vengono inviate una alla volta.  
  
 Le prestazioni risulteranno ridotte se si esegue un batch di dimensioni molto elevate. Pertanto, prima di implementare l'applicazione è consigliabile verificare quale sia la dimensione ottimale per i batch.  
  
## <a name="using-the-updatebatchsize-property"></a>Utilizzo della proprietà UpdateBatchSize  
 Quando gli aggiornamenti batch sono abilitati, il valore della proprietà <xref:System.Data.IDbCommand.UpdatedRowSource%2A> dei comandi `UpdateCommand`, `InsertCommand` e `DeleteCommand` di Data Adapter deve essere impostato su <xref:System.Data.UpdateRowSource.None> o su <xref:System.Data.UpdateRowSource.OutputParameters>. Quando si esegue un aggiornamento batch, il valore <xref:System.Data.IDbCommand.UpdatedRowSource%2A> o <xref:System.Data.UpdateRowSource.FirstReturnedRecord> della proprietà <xref:System.Data.UpdateRowSource.Both> del comando non è valido.  
  
 Nella procedura seguente viene illustrato l'uso della proprietà `UpdateBatchSize`. La procedura accetta due <xref:System.Data.DataSet> argomenti, un oggetto con colonne che rappresentano i campi **ProductCategoryID** e **Name** nella tabella **Production.ProductCategory** e un numero intero che rappresenta la dimensione del batch (il numero di righe nel batch). Il codice crea un nuovo oggetto <xref:System.Data.SqlClient.SqlDataAdapter>, impostandone le proprietà <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> e <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A>. Nel codice si presuppone che l'oggetto <xref:System.Data.DataSet> contenga righe modificate. La proprietà `UpdateBatchSize` viene impostata e viene eseguito l'aggiornamento.  
  
```vb  
Public Sub BatchUpdate( _  
  ByVal dataTable As DataTable, ByVal batchSize As Int32)  
    ' Assumes GetConnectionString() returns a valid connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    ' Connect to the AdventureWorks database.  
    Using connection As New SqlConnection(connectionString)  
        ' Create a SqlDataAdapter.  
        Dim adapter As New SqlDataAdapter()  
  
        'Set the UPDATE command and parameters.  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Production.ProductCategory SET " _  
          & "Name=@Name WHERE ProductCategoryID=@ProdCatID;", _  
          connection)  
        adapter.UpdateCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",  _  
          SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.UpdateCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the INSERT command and parameter.  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);", _  
  connection)  
        adapter.InsertCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.InsertCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the DELETE command and parameter.  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Production.ProductCategory " _  
          & "WHERE ProductCategoryID=@ProdCatID;", connection)  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID", _  
           SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None  
  
        ' Set the batch size.  
        adapter.UpdateBatchSize = batchSize  
  
        ' Execute the update.  
        adapter.Update(dataTable)  
    End Using  
End Sub  
```  
  
```csharp  
public static void BatchUpdate(DataTable dataTable,Int32 batchSize)  
{  
    // Assumes GetConnectionString() returns a valid connection string.  
    string connectionString = GetConnectionString();  
  
    // Connect to the AdventureWorks database.  
    using (SqlConnection connection = new
      SqlConnection(connectionString))  
    {  
  
        // Create a SqlDataAdapter.  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        // Set the UPDATE command and parameters.  
        adapter.UpdateCommand = new SqlCommand(  
            "UPDATE Production.ProductCategory SET "  
            + "Name=@Name WHERE ProductCategoryID=@ProdCatID;",
            connection);  
        adapter.UpdateCommand.Parameters.Add("@Name",
           SqlDbType.NVarChar, 50, "Name");  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",
           SqlDbType.Int, 4, "ProductCategoryID");  
         adapter.UpdateCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the INSERT command and parameter.  
        adapter.InsertCommand = new SqlCommand(  
            "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);",
            connection);  
        adapter.InsertCommand.Parameters.Add("@Name",
          SqlDbType.NVarChar, 50, "Name");  
        adapter.InsertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the DELETE command and parameter.  
        adapter.DeleteCommand = new SqlCommand(  
            "DELETE FROM Production.ProductCategory "  
            + "WHERE ProductCategoryID=@ProdCatID;", connection);  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID",
          SqlDbType.Int, 4, "ProductCategoryID");  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the batch size.  
        adapter.UpdateBatchSize = batchSize;  
  
        // Execute the update.  
        adapter.Update(dataTable);  
    }  
}  
```  
  
## <a name="handling-batch-update-related-events-and-errors"></a>Gestione di eventi ed errori relativi all'aggiornamento batch  
 Il **DataAdapter** dispone di due eventi correlati all'aggiornamento: **RowUpdating** e **RowUpdated**. In versioni precedenti di ADO.NET quando l'elaborazione batch è disabilitata, ciascuno di questi eventi viene generato una volta per ogni riga elaborata. **RowUpdating** viene generato prima dell'aggiornamento e **RowUpdated** viene generato dopo il completamento dell'aggiornamento del database.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Modifiche al comportamento degli eventi con aggiornamenti batch  
 Quando l'elaborazione batch è abilitata, in un'unica operazione di database vengono aggiornate più righe. Pertanto, si verifica un solo evento `RowUpdated` per ogni batch, mentre l'evento `RowUpdating` si verifica per ogni riga elaborata. Quando l'elaborazione batch è disabilitata, i due eventi vengono generati con interfoliazione uno-a-uno, dove un evento `RowUpdating` e un evento `RowUpdated` vengono generati per una riga e un evento `RowUpdating` e un evento `RowUpdated` per la riga successiva, fino all'elaborazione di tutte le righe.  
  
### <a name="accessing-updated-rows"></a>Accesso alle righe aggiornate  
 Quando l'elaborazione batch è disabilitata, è possibile accedere alla riga aggiornata mediante la proprietà <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> della classe <xref:System.Data.Common.RowUpdatedEventArgs>.  
  
 Quando l'elaborazione batch è abilitata, viene generato un unico evento `RowUpdated` per più righe. Pertanto, il valore della proprietà `Row` per ciascuna riga è null. Gli eventi `RowUpdating` vengono comunque generati per ogni riga. Il metodo <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> della classe <xref:System.Data.Common.RowUpdatedEventArgs> consente di accedere alle righe elaborate mediante la copia dei riferimenti alle righe in una matrice. Se non viene elaborata nessuna riga, `CopyToRows` genera un'eccezione <xref:System.ArgumentNullException>. Usare la proprietà <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> per restituire il numero di righe elaborate prima di chiamare il metodo <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>.  
  
### <a name="handling-data-errors"></a>Gestione degli errori di dati  
 I risultati dell'esecuzione batch sono identici a quelli ottenuti eseguendo le singole istruzioni una alla volta. Le istruzioni vengono eseguite nell'ordine in base al quale sono state aggiunte al batch. La gestione degli errori è la stessa sia in modalità batch sia quando la modalità batch è disabilitata. Ogni riga viene elaborata separatamente. Solo le righe che sono state elaborate correttamente nel database verranno aggiornate nell'oggetto <xref:System.Data.DataRow> corrispondente all'interno di <xref:System.Data.DataTable>.  
  
 Il provider di dati e il server database back-end determinano i costrutti SQL supportati per l'esecuzione batch. Se per l'esecuzione viene inviata un'istruzione non supportata, è possibile che venga generata un'eccezione.  
  
## <a name="see-also"></a>Vedere anche

- [DataAdapter e DataReader](dataadapters-and-datareaders.md)
- [Aggiornamento di origini dati con DataAdapter](updating-data-sources-with-dataadapters.md)
- [Gestione di eventi DataAdapter](handling-dataadapter-events.md)
- [Panoramica di ADO.NET](ado-net-overview.md)
