---
title: "Procedura: deserializzare le proprietà dei dati dell'istanza"
ms.date: 03/30/2017
ms.assetid: b13a3508-1b97-4359-b336-03d85fa23bc4
ms.openlocfilehash: 8142671fc1bc154337019e025d8443f0570106b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143083"
---
# <a name="how-to-deserialize-instance-data-properties"></a><span data-ttu-id="c7b97-102">Procedura: deserializzare le proprietà dei dati dell'istanza</span><span class="sxs-lookup"><span data-stu-id="c7b97-102">How to: Deserialize Instance Data Properties</span></span>
<span data-ttu-id="c7b97-103">È possibile che si presentino situazioni in cui un utente o un amministratore del flusso di lavoro desideri esaminare manualmente lo stato di un'istanza persistente del flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="c7b97-103">There may be situations when a user or workflow administrator may want to manually inspect the state of a persisted workflow instance.</span></span> <span data-ttu-id="c7b97-104"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> fornisce una visualizzazione sulla tabella delle istanze che espone le quattro colonne indicate di seguito:</span><span class="sxs-lookup"><span data-stu-id="c7b97-104"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> provides a view on the Instances table that exposes the following four columns:</span></span>  
  
- <span data-ttu-id="c7b97-105">ReadWritePrimitiveDataProperties</span><span class="sxs-lookup"><span data-stu-id="c7b97-105">ReadWritePrimitiveDataProperties</span></span>  
  
- <span data-ttu-id="c7b97-106">WriteOnlyPrimitiveDataProperties</span><span class="sxs-lookup"><span data-stu-id="c7b97-106">WriteOnlyPrimitiveDataProperties</span></span>  
  
- <span data-ttu-id="c7b97-107">ReadWriteComplexDataProperties</span><span class="sxs-lookup"><span data-stu-id="c7b97-107">ReadWriteComplexDataProperties</span></span>  
  
- <span data-ttu-id="c7b97-108">WriteOnlyComplexDataProperties</span><span class="sxs-lookup"><span data-stu-id="c7b97-108">WriteOnlyComplexDataProperties</span></span>  
  
 <span data-ttu-id="c7b97-109">Le proprietà dei dati primitivi fanno riferimento alle proprietà i cui tipi .NET Framework sono considerati "comuni" (ad esempio, Int32 e String), mentre le proprietà di dati complesse fanno riferimento a tutti gli altri tipi.</span><span class="sxs-lookup"><span data-stu-id="c7b97-109">Primitive data properties refer to properties whose .NET Framework types are considered to be "common" (for example, Int32 and String), while complex data properties refer to all other types.</span></span> <span data-ttu-id="c7b97-110">Un'enumerazione esatta di tipi primitivi viene trovata in un secondo momento in questo esempio di codice.</span><span class="sxs-lookup"><span data-stu-id="c7b97-110">An exact enumeration of primitive types is found later in this code example.</span></span>  
  
 <span data-ttu-id="c7b97-111">Le proprietà Read/Write si riferiscono a proprietà che vengono restituite di nuovo all'esecuzione del flusso di lavoro quando un'istanza viene caricata.</span><span class="sxs-lookup"><span data-stu-id="c7b97-111">Read/write properties refer to properties that are returned back to the Workflow Runtime when an instance is loaded.</span></span> <span data-ttu-id="c7b97-112">Le proprietà WriteOnly vengono scritte nel database e quindi non vengono mai rilette.</span><span class="sxs-lookup"><span data-stu-id="c7b97-112">WriteOnly properties are written to the database and then never read again.</span></span>  
  
 <span data-ttu-id="c7b97-113">In questo esempio viene fornito il codice che consente a un utente di deserializzare le proprietà dei dati primitivi.</span><span class="sxs-lookup"><span data-stu-id="c7b97-113">This example provides code that enables a user to deserialize primitive data properties.</span></span> <span data-ttu-id="c7b97-114">Data una matrice di byte letta dalla colonna ReadWritePrimitiveDataProperties o WriteOnlyPrimitiveDataProperties, questo codice <xref:System.Collections.Generic.Dictionary%602> convertirà l'oggetto binario di grandi dimensioni (BLOB) in un oggetto di tipo \<XName, oggetto> in cui ogni coppia di valori di chiave rappresenta un nome di proprietà e il valore corrispondente.</span><span class="sxs-lookup"><span data-stu-id="c7b97-114">Given a byte array read from either the ReadWritePrimitiveDataProperties or WriteOnlyPrimitiveDataProperties column, this code will convert the binary large object (BLOB) into a <xref:System.Collections.Generic.Dictionary%602> of type \<XName, object> where each key value pair represents a property name and its corresponding value.</span></span>  
  
 <span data-ttu-id="c7b97-115">In questo esempio non viene illustrato come deserializzare le proprietà dei dati complessi perché questa operazione non è attualmente supportata.</span><span class="sxs-lookup"><span data-stu-id="c7b97-115">This example does not demonstrate how to deserialize complex data properties because this is currently not a supported operation.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.IO.Compression;  
using System.Xml.Linq;  
using System.Xml;  
using System.Globalization;  
using System.Data.SqlClient;  
  
namespace PropertyReader  
{  
    class Program  
    {  
        const string ConnectionString = @"Data Source=localhost;Initial Catalog=Persistence;Integrated Security=True;Asynchronous Processing=True";  
        static void Main(string[] args)  
        {  
            string queryString = "SELECT TOP 10 * FROM [System.Activities.DurableInstancing].[Instances]";  
  
            using (SqlConnection connection =  
                       new SqlConnection(ConnectionString))  
            {  
                SqlCommand command =  
                    new SqlCommand(queryString, connection);  
                connection.Open();  
  
                SqlDataReader reader = command.ExecuteReader();  
  
                byte encodingOption;  
  
                while (reader.Read())  
                {  
                    if (reader["ReadWritePrimitiveDataProperties"] != DBNull.Value)  
                    {  
                        encodingOption = (byte)reader["EncodingOption"];  
                        Console.WriteLine("Printing the ReadWritePrimitiveDataProperties of the instance with Id:" + reader["InstanceId"]);  
                        foreach (KeyValuePair<XName, object> pair in (Dictionary<XName, object>)ReadDataProperties((byte[])reader["ReadWritePrimitiveDataProperties"], encodingOption))  
                        {  
                            Console.WriteLine("{0}, {1}" , pair.Key, pair.Value);  
                        }  
                        Console.WriteLine();  
                    }  
                    if (reader["WriteOnlyPrimitiveDataProperties"] != DBNull.Value)  
                    {  
                        encodingOption = (byte)reader["EncodingOption"];  
                        Console.WriteLine("Printing the WriteOnlyPrimitiveDataProperties of the instance with Id:" + reader["InstanceId"]);  
                        foreach (KeyValuePair<XName, object> pair in (Dictionary<XName, object>)ReadDataProperties((byte[])reader["WriteOnlyPrimitiveDataProperties"], encodingOption))  
                        {  
                            Console.WriteLine("{0}, {1}", pair.Key, pair.Value);  
                        }  
                        Console.WriteLine();  
                    }  
                }  
  
                // Call Close when done reading.  
                reader.Close();  
            }  
  
            Console.ReadLine();  
  
        }  
  
        static Dictionary<XName, object> ReadDataProperties(byte[] serializedDataProperties, byte encodingOption)  
        {  
            if (serializedDataProperties != null)  
            {  
                Dictionary<XName, object> propertyBag = new Dictionary<XName, object>();  
                bool isCompressed = (encodingOption == 1);  
  
                using (MemoryStream memoryStream = new MemoryStream(serializedDataProperties))  
                {  
                    // if the instance state is compressed using GZip algorithm  
                    if (isCompressed)  
                    {  
                        // decompress the data using the GZip
                        using (GZipStream stream = new GZipStream(memoryStream, CompressionMode.Decompress))  
                        {  
                            // create an XmlReader object and pass it on to the helper method ReadPrimitiveDataProperties  
                            using (XmlReader reader = XmlDictionaryReader.CreateBinaryReader(stream, XmlDictionaryReaderQuotas.Max))  
                            {  
                                // invoke the helper method  
                                ReadPrimitiveDataProperties(reader, propertyBag);  
                            }  
                        }  
                    }  
                    else  
                    {  
                        // if the instance data is not compressed
                        // create an XmlReader object and pass it on to the helper method ReadPrimitiveDataProperties  
                        using (XmlReader reader = XmlDictionaryReader.CreateBinaryReader(memoryStream, XmlDictionaryReaderQuotas.Max))  
                        {  
                            // invoke the helper method  
                            ReadPrimitiveDataProperties(reader, propertyBag);  
                        }  
                    }  
                    return propertyBag;  
                }  
            }  
  
            return null;  
        }  
  
        // reads the primitive data properties from the XML stream  
        // invoked by the ReadDataProperties method  
        static void ReadPrimitiveDataProperties(XmlReader reader, Dictionary<XName, object> propertyBag)  
        {  
            const string xmlElementName = "Property";  
  
            if (reader.ReadToDescendant(xmlElementName))  
            {  
                do  
                {  
                    // get the name of the property  
                    reader.MoveToFirstAttribute();  
                    string propertyName = reader.Value;  
  
                    // get the type of the property  
                    reader.MoveToNextAttribute();  
                    PrimitiveType type = (PrimitiveType)Int32.Parse(reader.Value, CultureInfo.InvariantCulture);  
  
                    // get the value of the property  
                    reader.MoveToNextAttribute();  
                    object propertyValue = ConvertStringToNativeType(reader.Value, type);  
  
                    // add the name and value of the property to the property bag  
                    propertyBag.Add(propertyName, propertyValue);  
                }  
  
                while (reader.ReadToNextSibling(xmlElementName));  
            }  
        }  
  
        // invoked by the ReadPrimitiveDataProperties method  
        // Given a property value as parsed from an XML attribute, and the .NET Type of the Property, recreates the actual property value  
        // (e.g. Given a property value of "1" and a PrimitiveType of Int32, this method will return an object of type Int32 with value 1)  
        static object ConvertStringToNativeType(string value, PrimitiveType type)  
        {  
            switch (type)  
            {  
                case PrimitiveType.Bool:  
                    return XmlConvert.ToBoolean(value);  
                case PrimitiveType.Byte:  
                    return XmlConvert.ToByte(value);  
                case PrimitiveType.Char:  
                    return XmlConvert.ToChar(value);  
                case PrimitiveType.DateTime:  
                    return XmlConvert.ToDateTime(value, XmlDateTimeSerializationMode.RoundtripKind);  
                case PrimitiveType.DateTimeOffset:  
                    return XmlConvert.ToDateTimeOffset(value);  
                case PrimitiveType.Decimal:  
                    return XmlConvert.ToDecimal(value);  
                case PrimitiveType.Double:  
                    return XmlConvert.ToDouble(value);  
                case PrimitiveType.Float:  
                    return float.Parse(value, CultureInfo.InvariantCulture);  
                case PrimitiveType.Guid:  
                    return XmlConvert.ToGuid(value);  
                case PrimitiveType.Int:  
                    return XmlConvert.ToInt32(value);  
                case PrimitiveType.Long:  
                    return XmlConvert.ToInt64(value);  
                case PrimitiveType.SByte:  
                    return XmlConvert.ToSByte(value);  
                case PrimitiveType.Short:  
                    return XmlConvert.ToInt16(value);  
                case PrimitiveType.String:  
                    return value;  
                case PrimitiveType.TimeSpan:  
                    return XmlConvert.ToTimeSpan(value);  
                case PrimitiveType.Type:  
                    return Type.GetType(value);  
                case PrimitiveType.UInt:  
                    return XmlConvert.ToUInt32(value);  
                case PrimitiveType.ULong:  
                    return XmlConvert.ToUInt64(value);  
                case PrimitiveType.Uri:  
                    return new Uri(value);  
                case PrimitiveType.UShort:  
                    return XmlConvert.ToUInt16(value);  
                case PrimitiveType.XmlQualifiedName:  
                    return new XmlQualifiedName(value);  
                case PrimitiveType.Null:  
                case PrimitiveType.Unavailable:  
                default:  
                    return null;  
            }  
        }  
        // .NET Types which SQL Workflow Instance Store considers to be Primitive. Any other .NET type not listed in this enumeration is a "Complex" property.  
        enum PrimitiveType  
        {  
            Bool = 0,  
            Byte,  
            Char,  
            DateTime,  
            DateTimeOffset,  
            Decimal,  
            Double,  
            Float,  
            Guid,  
            Int,  
            Null,  
            Long,  
            SByte,  
            Short,  
            String,  
            TimeSpan,  
            Type,  
            UInt,  
            ULong,  
            Uri,  
            UShort,  
            XmlQualifiedName,  
            Unavailable = 99  
        }  
    }  
}  
```
