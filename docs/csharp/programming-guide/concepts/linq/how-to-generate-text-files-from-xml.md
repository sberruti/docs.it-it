---
title: Come generare file di testo da XML (C#)
ms.date: 07/20/2015
ms.assetid: 9ad283f7-7cac-42ff-bf32-92aa866e6883
ms.openlocfilehash: 9ca76cf955e07bdcc8e095b30f6fadc74edba739
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345924"
---
# <a name="how-to-generate-text-files-from-xml-c"></a><span data-ttu-id="7efbf-102">Come generare file di testo da XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7efbf-102">How to generate text files from XML (C#)</span></span>
<span data-ttu-id="7efbf-103">In questo esempio viene illustrato come generare un file CSV con valori delimitati da virgole da un file XML.</span><span class="sxs-lookup"><span data-stu-id="7efbf-103">This example shows how to generate a comma-separated values (CSV) file from an XML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7efbf-104">Esempio</span><span class="sxs-lookup"><span data-stu-id="7efbf-104">Example</span></span>  
 <span data-ttu-id="7efbf-105">Nella versione C# di questo esempio viene usata la sintassi del metodo e l'operatore `Aggregate` per generare un file CSV da un documento XML in un'unica espressione.</span><span class="sxs-lookup"><span data-stu-id="7efbf-105">The C# version of this example uses method syntax and the `Aggregate` operator to generate a CSV file from an XML document in a single expression.</span></span> <span data-ttu-id="7efbf-106">Per altre informazioni, vedere [Sintassi di query e sintassi di metodi in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="7efbf-106">For more information, see [Query Syntax and Method Syntax in LINQ](./query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="7efbf-107">Questo esempio usa il documento XML seguente: [File XML di esempio: clienti e ordini (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="7efbf-107">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
string csv =  
    (from el in custOrd.Element("Customers").Elements("Customer")  
    select  
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}",  
            (string)el.Attribute("CustomerID"),  
            (string)el.Element("CompanyName"),  
            (string)el.Element("ContactName"),  
            (string)el.Element("ContactTitle"),  
            (string)el.Element("Phone"),  
            (string)el.Element("FullAddress").Element("Address"),  
            (string)el.Element("FullAddress").Element("City"),  
            (string)el.Element("FullAddress").Element("Region"),  
            (string)el.Element("FullAddress").Element("PostalCode"),  
            (string)el.Element("FullAddress").Element("Country"),  
            Environment.NewLine  
        )  
    )  
    .Aggregate(  
        new StringBuilder(),  
        (sb, s) => sb.Append(s),  
        sb => sb.ToString()  
    );  
Console.WriteLine(csv);  
```  
  
 <span data-ttu-id="7efbf-108">L'output del codice è il seguente:</span><span class="sxs-lookup"><span data-stu-id="7efbf-108">This code produces the following output:</span></span>  
  
```output  
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA  
```  
  
## <a name="see-also"></a><span data-ttu-id="7efbf-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7efbf-109">See also</span></span>

- <span data-ttu-id="7efbf-110">[Projections and Transformations (LINQ to XML) (C#)](how-to-work-with-dictionaries-using-linq-to-xml.md) (Proiezioni e trasformazioni (LINQ to XML) in C#)</span><span class="sxs-lookup"><span data-stu-id="7efbf-110">[Projections and Transformations (LINQ to XML) (C#)](how-to-work-with-dictionaries-using-linq-to-xml.md)</span></span>
