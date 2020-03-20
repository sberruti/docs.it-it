---
title: Oggetti LOB Oracle
ms.date: 03/30/2017
ms.assetid: 272e8e1e-a31f-475a-8c2a-ae8e1286bdab
ms.openlocfilehash: 62525fed85525e26b7c61208fe44b108de562fb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149427"
---
# <a name="oracle-lobs"></a><span data-ttu-id="35d59-102">Oggetti LOB Oracle</span><span class="sxs-lookup"><span data-stu-id="35d59-102">Oracle LOBs</span></span>
<span data-ttu-id="35d59-103">Il provider di dati .NET <xref:System.Data.OracleClient.OracleLob> Framework per Oracle include la classe , utilizzata per lavorare con i tipi di dati **LOB** Oracle.</span><span class="sxs-lookup"><span data-stu-id="35d59-103">The .NET Framework Data Provider for Oracle includes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle **LOB** data types.</span></span>  
  
 <span data-ttu-id="35d59-104">Un **OracleLob** può essere <xref:System.Data.OracleClient.OracleType> uno dei seguenti tipi di dati:</span><span class="sxs-lookup"><span data-stu-id="35d59-104">An **OracleLob** may be one of these <xref:System.Data.OracleClient.OracleType> data types:</span></span>  
  
|<span data-ttu-id="35d59-105">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="35d59-105">Data type</span></span>|<span data-ttu-id="35d59-106">Descrizione</span><span class="sxs-lookup"><span data-stu-id="35d59-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35d59-107">**Blob**</span><span class="sxs-lookup"><span data-stu-id="35d59-107">**Blob**</span></span>|<span data-ttu-id="35d59-108">Tipo di dati **BLOB** Oracle che contiene dati binari con una dimensione massima di 4 gigabyte.</span><span class="sxs-lookup"><span data-stu-id="35d59-108">An Oracle **BLOB** data type that contains binary data with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="35d59-109">Viene eseguito il mapping a una **matrice** di tipo **Byte**.</span><span class="sxs-lookup"><span data-stu-id="35d59-109">This maps to an **Array** of type **Byte**.</span></span>|  
|<span data-ttu-id="35d59-110">**Clob**</span><span class="sxs-lookup"><span data-stu-id="35d59-110">**Clob**</span></span>|<span data-ttu-id="35d59-111">Tipo di dati **CLOB** Oracle che contiene dati di tipo carattere, in base al set di caratteri predefinito nel server, con una dimensione massima di 4 gigabyte.</span><span class="sxs-lookup"><span data-stu-id="35d59-111">An Oracle **CLOB** data type that contains character data, based on the default character set on the server, with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="35d59-112">Viene eseguito il mapping a **String**.</span><span class="sxs-lookup"><span data-stu-id="35d59-112">This maps to **String**.</span></span>|  
|<span data-ttu-id="35d59-113">**Nclob**</span><span class="sxs-lookup"><span data-stu-id="35d59-113">**NClob**</span></span>|<span data-ttu-id="35d59-114">Tipo di dati **NCLOB** Oracle che contiene dati di tipo carattere, basato sul set di caratteri nazionale sul server con una dimensione massima di 4 gigabyte.</span><span class="sxs-lookup"><span data-stu-id="35d59-114">An Oracle **NCLOB** data type that contains character data, based on the national character set on the server with a maximum size of 4 gigabytes.</span></span> <span data-ttu-id="35d59-115">Viene eseguito il mapping a **String**.</span><span class="sxs-lookup"><span data-stu-id="35d59-115">This maps to **String**.</span></span>|  
  
 <span data-ttu-id="35d59-116">Un **OracleLob** differisce da un <xref:System.Data.OracleClient.OracleBFile> in quanto i dati vengono archiviati sul server anziché in un file fisico nel sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="35d59-116">An **OracleLob** differs from an <xref:System.Data.OracleClient.OracleBFile> in that the data is stored on the server instead of in a physical file in the operating system.</span></span> <span data-ttu-id="35d59-117">Può anche essere un oggetto di lettura/scrittura, a differenza di un **OracleBFile**, che è sempre di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="35d59-117">It can also be a read-write object, unlike an **OracleBFile**, which is always read-only.</span></span>  
  
## <a name="creating-retrieving-and-writing-to-a-lob"></a><span data-ttu-id="35d59-118">Creazione, recupero e scrittura di un LOB</span><span class="sxs-lookup"><span data-stu-id="35d59-118">Creating, Retrieving, and Writing to a LOB</span></span>  
 <span data-ttu-id="35d59-119">Nell'esempio in Cè riportato di seguito viene illustrato come creare loB in una tabella Oracle e quindi recuperarle e scriverle sotto forma di oggetti **OracleLob.**</span><span class="sxs-lookup"><span data-stu-id="35d59-119">The following C# example demonstrates how you can create LOBs in an Oracle table, and then retrieve and write to them in the form of **OracleLob** objects.</span></span> <span data-ttu-id="35d59-120">Nell'esempio viene <xref:System.Data.OracleClient.OracleDataReader> illustrato l'utilizzo dell'oggetto e dei metodi **OracleLob** **Read** e **Write.**</span><span class="sxs-lookup"><span data-stu-id="35d59-120">The example demonstrates using the <xref:System.Data.OracleClient.OracleDataReader> object and the **OracleLob** **Read** and **Write** methods.</span></span> <span data-ttu-id="35d59-121">Nell'esempio vengono utilizzati i tipi di dati Oracle **BLOB**, **CLOB**e **NCLOB** .</span><span class="sxs-lookup"><span data-stu-id="35d59-121">The example uses Oracle **BLOB**, **CLOB**, and **NCLOB** data types.</span></span>  
  
```csharp  
using System;  
using System.IO;
using System.Text;
using System.Data;
using System.Data.OracleClient;  
  
// LobExample  
public class LobExample  
{  
   public static int Main(string[] args)  
   {  
      //Create a connection.  
      OracleConnection conn = new OracleConnection(  
         "Data Source=Oracle8i;Integrated Security=yes");  
      using(conn)  
      {  
         //Open a connection.  
         conn.Open();  
         OracleCommand cmd = conn.CreateCommand();  
  
         //Create the table and schema.  
         CreateTable(cmd);  
  
         //Read example.  
         ReadLobExample(cmd);  
  
         //Write example  
         WriteLobExample(cmd);  
      }  
  
      return 1;  
   }  
  
   // ReadLobExample  
   public static void ReadLobExample(OracleCommand cmd)  
   {  
      int actual = 0;  
  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs values (1, 'AA', 'AAA', N'AAAA')";  
      // Select some data.  
      cmd.CommandText = "SELECT * FROM tablewithlobs";  
      OracleDataReader reader = cmd.ExecuteReader();  
      using(reader)  
      {  
         //Obtain the first row of data.  
         reader.Read();  
  
         //Obtain the LOBs (all 3 varieties).  
         OracleLob blob = reader.GetOracleLob(1);  
         OracleLob clob = reader.GetOracleLob(2);  
         OracleLob nclob = reader.GetOracleLob(3);  
  
         //Example - Reading binary data (in chunks).  
         byte[] buffer = new byte[100];  
         while((actual = blob.Read(buffer, 0, buffer.Length)) >0)  
            Console.WriteLine(blob.LobType + ".Read(" + buffer + ", " +
              buffer.Length + ") => " + actual);  
  
         // Example - Reading CLOB/NCLOB data (in chunks).  
         // Note: You can read character data as raw Unicode bytes
         // (using OracleLob.Read as in the above example).  
         // However, because the OracleLob object inherits directly
         // from the .NET stream object,
         // all the existing classes that manipluate streams can
         // also be used. For example, the
         // .NET StreamReader makes it easier to convert the raw bytes
         // into actual characters.  
         StreamReader streamreader =
           new StreamReader(clob, Encoding.Unicode);  
         char[] cbuffer = new char[100];  
         while((actual = streamreader.Read(cbuffer,
           0, cbuffer.Length)) >0)  
            Console.WriteLine(clob.LobType + ".Read(  
              " + new string(cbuffer, 0, actual) + ", " +
              cbuffer.Length + ") => " + actual);  
  
         // Example - Reading data (all at once).  
         // You could use StreamReader.ReadToEnd to obtain
         // all the string data, or simply  
         // call OracleLob.Value to obtain a contiguous allocation
         // of all the data.  
         Console.WriteLine(nclob.LobType + ".Value => " + nclob.Value);  
      }  
   }  
  
   // WriteLobExample  
   public static void WriteLobExample(OracleCommand cmd)  
   {  
      //Note: Updating LOB data requires a transaction.  
      cmd.Transaction = cmd.Connection.BeginTransaction();  
  
      // Select some data.  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs values (1, 'AA', 'AAA', N'AAAA')";  
      cmd.CommandText = "SELECT * FROM tablewithlobs FOR UPDATE";  
      OracleDataReader reader = cmd.ExecuteReader();  
      using(reader)  
      {  
         // Obtain the first row of data.  
         reader.Read();  
  
         // Obtain a LOB.  
         OracleLob blob = reader.GetOracleLob(1/*0:based ordinal*/);  
  
         // Perform any desired operations on the LOB
         // (read, position, and so on).  
  
         // Example - Writing binary data (directly to the backend).  
         // To write, you can use any of the stream classes, or write  
         // raw binary data using
         // the OracleLob write method. Writing character vs. binary
         // is the same;  
         // however note that character is always in terms of
         // Unicode byte counts  
         // (for example, even number of bytes - 2 bytes for every  
         // Unicode character).  
         byte[] buffer = new byte[100];  
         buffer[0] = 0xCC;  
         buffer[1] = 0xDD;  
         blob.Write(buffer, 0, 2);  
         blob.Position = 0;  
         Console.WriteLine(blob.LobType + ".Write(  
           " + buffer + ", 0, 2) => " + blob.Value);  
  
         // Example - Obtaining a temp LOB and copying data
         // into it from another LOB.  
         OracleLob templob = CreateTempLob(cmd, blob.LobType);  
         long actual = blob.CopyTo(templob);  
         Console.WriteLine(blob.LobType + ".CopyTo(  
            " + templob.Value + ") => " + actual);  
  
         // Commit the transaction now that everything succeeded.  
         // Note: On error, Transaction.Dispose is called
         // (from the using statement)  
         // and will automatically roll back the pending transaction.  
         cmd.Transaction.Commit();  
      }  
   }  
  
   // CreateTempLob  
   public static OracleLob CreateTempLob(  
     OracleCommand cmd, OracleType lobtype)  
   {  
      //Oracle server syntax to obtain a temporary LOB.  
      cmd.CommandText = "DECLARE A " + lobtype + "; "+  
                     "BEGIN "+  
                        "DBMS_LOB.CREATETEMPORARY(A, FALSE); "+  
                        ":LOC := A; "+  
                     "END;";  
  
      //Bind the LOB as an output parameter.  
      OracleParameter p = cmd.Parameters.Add("LOC", lobtype);  
      p.Direction = ParameterDirection.Output;  
  
      //Execute (to receive the output temporary LOB).  
      cmd.ExecuteNonQuery();  
  
      //Return the temporary LOB.  
      return (OracleLob)p.Value;  
   }  
  
   // CreateTable  
   public static void CreateTable(OracleCommand cmd)  
   {  
      // Table Schema:  
      // "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      // "INSERT INTO tablewithlobs VALUES (1, 'AA', 'AAA', N'AAAA')";  
      try  
      {  
         cmd.CommandText   = "DROP TABLE tablewithlobs";  
         cmd.ExecuteNonQuery();  
      }  
      catch(Exception)  
      {  
      }  
  
      cmd.CommandText =
        "CREATE TABLE tablewithlobs (a int, b BLOB, c CLOB, d NCLOB)";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText =
        "INSERT INTO tablewithlobs VALUES (1, 'AA', 'AAA', N'AAAA')";  
      cmd.ExecuteNonQuery();  
   }  
}  
```  
  
## <a name="creating-a-temporary-lob"></a><span data-ttu-id="35d59-122">Creazione di un LOB temporaneo</span><span class="sxs-lookup"><span data-stu-id="35d59-122">Creating a Temporary LOB</span></span>  
 <span data-ttu-id="35d59-123">Nell'esempio C# seguente viene illustrato come creare un LOB temporaneo.</span><span class="sxs-lookup"><span data-stu-id="35d59-123">The following C# example demonstrates how to create a temporary LOB.</span></span>  
  
```csharp  
OracleConnection conn = new OracleConnection(  
  "server=test8172; integrated security=yes;");  
conn.Open();  
  
OracleTransaction tx = conn.BeginTransaction();  
  
OracleCommand cmd = conn.CreateCommand();  
cmd.Transaction = tx;  
cmd.CommandText =
  "declare xx blob; begin dbms_lob.createtemporary(  
  xx, false, 0); :tempblob := xx; end;";  
cmd.Parameters.Add(new OracleParameter("tempblob",  
  OracleType.Blob)).Direction = ParameterDirection.Output;  
cmd.ExecuteNonQuery();  
OracleLob tempLob = (OracleLob)cmd.Parameters[0].Value;  
tempLob.BeginBatch(OracleLobOpenMode.ReadWrite);  
tempLob.Write(tempbuff,0,tempbuff.Length);  
tempLob.EndBatch();  
cmd.Parameters.Clear();  
cmd.CommandText = "myTable.myProc";  
cmd.CommandType = CommandType.StoredProcedure;
cmd.Parameters.Add(new OracleParameter(  
  "ImportDoc", OracleType.Blob)).Value = tempLob;  
cmd.ExecuteNonQuery();  
  
tx.Commit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="35d59-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="35d59-124">See also</span></span>

- [<span data-ttu-id="35d59-125">Oracle e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="35d59-125">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="35d59-126">Panoramica di ADO.NET</span><span class="sxs-lookup"><span data-stu-id="35d59-126">ADO.NET Overview</span></span>](ado-net-overview.md)
