---
title: Modifica di dati di grandi dimensioni (max)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 00a4ae83270bb74e9703faebfc93e26b5c069478
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174277"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Modifica di dati con valori elevati (massimi) in ADO.NET
I tipi di dati LOB (Large Object) sono quelli che superano la dimensione massima di 8 kilobyte (KB) per le righe. SQL Server include l'identificatore `max` per i tipi di dati `varchar`, `nvarchar` e `varbinary` per consentire l'archiviazione di valori di dimensioni fino a 2^32 byte. Le colonne della tabella e le variabili Transact-SQL possono specificare tipi di dati `varchar(max)`, `nvarchar(max)`o `varbinary(max)`. In ADO.NET i tipi di dati `max` possono essere recuperati da un `DataReader` e possono inoltre essere specificati come parametri di input e di output senza richiedere una gestione speciale. Per i tipi di dati `varchar` di grandi dimensioni, è possibile recuperare e aggiornare i dati in modo incrementale.  
  
 I tipi di dati `max` possono essere usati per eseguire confronti, ad esempio per le variabili Transact-SQL, e per le concatenazioni. Si possono usare anche nelle clausole DISTINCT, ORDER BY, GROUP BY di un'istruzione SELECT, nonché in aggregazioni, join e sottoquery.  
  
 La tabella seguente fornisce i collegamenti alla documentazione online di SQL Server.  
  
 **Documentazione di SQL Server**  
  
1. [Utilizzo di tipi di dati per valori di grandi dimensioni](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))  
  
## <a name="large-value-type-restrictions"></a>Restrizioni per i tipi di valori di grandi dimensioni  
 Per i tipi di dati `max` vengono applicate le restrizioni seguenti, che non esistono per i tipi di dati più piccoli:  
  
- Un `sql_variant` non può contenere un tipo di dati `varchar` di grandi dimensioni.  
  
- Non è possibile specificare colonne `varchar` di grandi dimensioni come colonna chiave in un indice. Sono consentite in una colonna inclusa in un indice non cluster.  
  
- Le colonne `varchar` di grandi dimensioni non possono essere usate come colonne chiave di partizionamento.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Uso di tipi di valori di grandi dimensioni in Transact-SQL  
 La funzione `OPENROWSET` di Transact-SQL è un metodo monouso per la connessione e l'accesso ai dati remoti. Include tutte le informazioni di connessione necessarie per l'accesso remoto ai dati da un'origine dati OLE DB. È possibile fare riferimento a `OPENROWSET` nella clausola FROM di una query come se fosse un nome di tabella. È inoltre possibile farvi riferimento come tabella di destinazione di un'istruzione INSERT, UPDATE o DELETE, soggetta alle funzionalità del provider OLE DB.  
  
 La funzione `OPENROWSET` include il provider di set di righe `BULK`, che consente di leggere i dati direttamente da un file senza caricare i dati in una tabella di destinazione. Ciò consente di usare `OPENROWSET` in una semplice istruzione INSERT SELECT.  
  
 Gli argomenti dell'opzione `OPENROWSET BULK` forniscono un controllo notevole sul punto in cui iniziare e terminare la lettura dei dati, sulla gestione degli errori e sull'interpretazione dei dati. Ad esempio, è possibile specificare che il file di dati venga letto come riga singola, set di righe a colonna singola di tipo `varbinary`, `varchar` o `nvarchar`. Per la sintassi e le opzioni complete, vedere documentazione online di SQL Server.  
  
 Nell'esempio seguente viene inserita una foto nella tabella ProductPhoto del database di esempio AdventureWorks. Se si usa il provider `BULK OPENROWSET`, è necessario fornire l'elenco di colonne denominato anche se non si inseriscono valori in ogni colonna. La chiave primaria in questo caso è definita come colonna Identity e può essere omessa dall'elenco di colonne. Si noti che è necessario specificare anche un nome di correlazione alla fine dell'istruzione `OPENROWSET`, che in questo caso è ThumbnailPhoto. Questo è correlato alla colonna della tabella `ProductPhoto` in cui viene caricato il file.  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,
    ThumbnailPhotoFilePath,
    LargePhoto,
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>Aggiornamento di dati tramite UPDATE .WRITE  
 L'istruzione UPDATE di Transact-SQL usa una nuova sintassi di WRITE per la modifica del contenuto delle colonne `varchar(max)`, `nvarchar(max)` o `varbinary(max)`. In questo modo è possibile eseguire aggiornamenti parziali dei dati. La sintassi di UPDATE.WRITE è illustrata di seguito in forma abbreviata:  
  
 UPDATE  
  
 * \<>dell'oggetto* .  
  
 SET  
  
 : *column_name* . - WRITE @Offset ( @Length *espressione* , , )  
  
 Il metodo WRITE specifica che una sezione del valore di *column_name* verrà modificato. L'espressione corrisponde al valore che verrà copiato in *column_name*, l'argomento `@Offset` al punto di inizio in cui verrà scritta l'espressione e l'argomento `@Length` alla lunghezza della sezione nella colonna.  
  
|Se|Risultato|  
|--------|----------|  
|L'espressione è impostata su NULL.|Il valore di `@Length` viene ignorato e il valore di *column_name* viene troncato in base al valore specificato di `@Offset`.|  
|`@Offset` è NULL|L'operazione di aggiornamento aggiunge l'espressione alla fine del valore di *column_name* esistente e il valore di `@Length` viene ignorato.|  
|`@Offset` è maggiore della lunghezza del valore column_name|SQL Server restituisce un errore.|  
|`@Length` è NULL|L'operazione di aggiornamento rimuove tutti i dati da `@Offset` fino al termine del valore `column_name`.|  
  
> [!NOTE]
> Né `@Offset` né `@Length` possono essere un numero negativo.  
  
## <a name="example"></a>Esempio  
 Questo esempio di Transact-SQL aggiorna un valore parziale in DocumentSummary, una colonna `nvarchar(max)` nella tabella Document del database AdventureWorks. La parola 'components' viene sostituta con la parola 'features' specificando la parola sostitutiva, la posizione iniziale (offset) della parola da sostituire nei dati esistenti e il numero di caratteri da sostituire (lunghezza). Nell'esempio sono incluse istruzioni SELECT prima e dopo l'istruzione UPDATE per confrontare i risultati.  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a>Uso di tipi di valori di grandi dimensioni in ADO.NET  
 È possibile usare tipi di valore di grandi dimensioni in ADO.NET specificandoli come oggetti <xref:System.Data.SqlClient.SqlParameter> in un oggetto <xref:System.Data.SqlClient.SqlDataReader> per restituire un set di risultati oppure usando un oggetto <xref:System.Data.SqlClient.SqlDataAdapter> per compilare un oggetto `DataSet`/`DataTable`. Non esiste alcuna differenza tra l'uso di un tipo di dati per valori di grandi dimensioni e l'uso del tipo di dati correlato per valori più piccoli.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Uso di GetSqlBytes per recuperare i dati  
 È possibile usare il metodo `GetSqlBytes` dell'oggetto <xref:System.Data.SqlClient.SqlDataReader> per recuperare il contenuto di una colonna `varbinary(max)`. Il seguente frammento di codice presuppone un oggetto <xref:System.Data.SqlClient.SqlCommand> denominato `cmd` che seleziona dati `varbinary(max)` da una tabella e un oggetto <xref:System.Data.SqlClient.SqlDataReader> denominato `reader` che recupera i dati come <xref:System.Data.SqlTypes.SqlBytes>.  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Uso di GetSqlChars per il recupero di dati  
 È possibile usare il metodo `GetSqlChars` dell'oggetto <xref:System.Data.SqlClient.SqlDataReader> per recuperare il contenuto di una colonna `varchar(max)` o `nvarchar(max)`. Il seguente frammento di codice presuppone un oggetto <xref:System.Data.SqlClient.SqlCommand> denominato `cmd` che seleziona dati `nvarchar(max)` da una tabella e un oggetto <xref:System.Data.SqlClient.SqlDataReader> denominato `reader` che recupera i dati.  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Uso di GetSqlBinary per il recupero di dati  
 È possibile usare il metodo `GetSqlBinary` di un oggetto <xref:System.Data.SqlClient.SqlDataReader> per recuperare il contenuto di una colonna `varbinary(max)`. Il seguente frammento di codice presuppone un oggetto <xref:System.Data.SqlClient.SqlCommand> denominato `cmd` che seleziona dati `varbinary(max)` da una tabella e un oggetto <xref:System.Data.SqlClient.SqlDataReader> denominato `reader` che recupera i dati come flusso <xref:System.Data.SqlTypes.SqlBinary>.  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>Uso di GetBytes per il recupero di dati  
 Il metodo `GetBytes` di un oggetto <xref:System.Data.SqlClient.SqlDataReader> legge un flusso di byte dall'offset di colonna specificato in una matrice di byte, a partire dall'offset di matrice specificato. Il frammento di codice seguente presuppone l'uso di un oggetto <xref:System.Data.SqlClient.SqlDataReader> denominato `reader` che recupera i byte in una matrice di byte. Si noti che, a differenza di `GetSqlBytes`, `GetBytes` richiede una dimensione per il buffer della matrice.  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>Uso di GetValue per il recupero di dati  
 Il metodo `GetValue` di un oggetto <xref:System.Data.SqlClient.SqlDataReader> legge il valore dall'offset di colonna specificato in una matrice. Il frammento di codice seguente presuppone l'uso di un oggetto <xref:System.Data.SqlClient.SqlDataReader> denominato `reader` che recupera i dati binari dall'offset della prima colonna, quindi i dati di tipo stringa dall'offset della seconda colonna.  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Conversione da tipi di valore di grandi dimensioni a tipi CLR  
 È possibile convertire il contenuto di una colonna `varchar(max)` o `nvarchar(max)` usando uno qualsiasi dei metodi di conversione stringhe, ad esempio `ToString`. Il frammento di codice seguente presuppone l'uso di un oggetto <xref:System.Data.SqlClient.SqlDataReader> denominato `reader` che recupera i dati.  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a>Esempio  
 Il codice seguente recupera il nome e l'oggetto `LargePhoto` dalla tabella `ProductPhoto` nel database `AdventureWorks` e li salva in un file. L'assembly deve essere compilato con un riferimento allo spazio dei nomi <xref:System.Drawing>.  Il metodo <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> di <xref:System.Data.SqlClient.SqlDataReader> restituisce un oggetto <xref:System.Data.SqlTypes.SqlBytes> che espone una proprietà `Stream`. Questa viene usata nel codice per creare un nuovo oggetto `Bitmap`, che verrà quindi salvato come `ImageFormat` GIF.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Utilizzo dei parametri di tipi di valore di grandi dimensioni  
 I tipi di valore di grandi dimensioni possono essere usati negli oggetti <xref:System.Data.SqlClient.SqlParameter> nello stesso modo in cui si usano i tipi di valore più piccoli negli oggetti <xref:System.Data.SqlClient.SqlParameter>. È possibile recuperare tipi di valore di grandi dimensioni come valori <xref:System.Data.SqlClient.SqlParameter>, come illustrato nell'esempio seguente. Il codice presuppone che la seguente stored procedure GetDocumentSummary esista nel database di esempio AdventureWorks. La stored procedure accetta un parametro di input denominato @DocumentID e restituisce il contenuto della colonna DocumentSummary nel parametro di output @DocumentSummary.  
  
```sql
CREATE PROCEDURE GetDocumentSummary
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a>Esempio  
 Il codice ADO.NET crea oggetti <xref:System.Data.SqlClient.SqlConnection> e <xref:System.Data.SqlClient.SqlCommand> per eseguire la stored procedure GetDocumentSummary e recuperare il riepilogo del documento, archiviato come tipo di valore di grandi dimensioni. Il codice passa un valore per il parametro di input @DocumentID e i risultati restituiti nel parametro di output @DocumentSummary vengono visualizzati nella finestra della console.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Vedere anche

- [SQL Server Binary and Large-Value Data](sql-server-binary-and-large-value-data.md)
- [Mapping dei tipi di dati SQL Server](../sql-server-data-type-mappings.md)
- [Operazioni sui dati di SQL Server in ADO.NET](sql-server-data-operations.md)
- [Panoramica di ADO.NET](../ado-net-overview.md)
