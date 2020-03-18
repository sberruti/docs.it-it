---
title: Serializzazione in base a un XmlReader (richiamo di XSLT) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: b079fe05fa8c230f644e011dcb62ec54f55cae60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "66487186"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="4a8d5-102">Serializzazione in base a un XmlReader (richiamo di XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="4a8d5-102">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="4a8d5-103">Quando si usano le funzionalità di interoperabilità <xref:System.Xml?displayProperty=nameWithType> di [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], è possibile usare <xref:System.Xml.Linq.XNode.CreateReader%2A> per creare un oggetto <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="4a8d5-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="4a8d5-104">Il modulo che legge dall'oggetto <xref:System.Xml.XmlReader> creato legge i nodi dell'albero XML e li elabora di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="4a8d5-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="4a8d5-105">Richiamo di una trasformazione XSLT</span><span class="sxs-lookup"><span data-stu-id="4a8d5-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="4a8d5-106">Un possibile utilizzo di questo metodo è il richiamo di una trasformazione XSLT.</span><span class="sxs-lookup"><span data-stu-id="4a8d5-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="4a8d5-107">È possibile creare un albero XML, creare un oggetto <xref:System.Xml.XmlReader> dall'albero XML, creare un nuovo documento e infine creare un oggetto <xref:System.Xml.XmlWriter> per scrivere nel documento.</span><span class="sxs-lookup"><span data-stu-id="4a8d5-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="4a8d5-108">È quindi possibile richiamare la trasformazione XSLT passandovi <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4a8d5-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="4a8d5-109">Dopo il completamento della trasformazione, il nuovo albero XML viene popolato con i relativi risultati.</span><span class="sxs-lookup"><span data-stu-id="4a8d5-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
    <xsl:template match='/Parent'>  
        <Root>  
            <C1>  
            <xsl:value-of select='Child1'/>  
            </C1>  
            <C2>  
            <xsl:value-of select='Child2'/>  
            </C2>  
        </Root>  
    </xsl:template>  
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="4a8d5-110">Nell'esempio viene prodotto l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="4a8d5-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a8d5-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4a8d5-111">See also</span></span>

- [<span data-ttu-id="4a8d5-112">Serializzazione di alberi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="4a8d5-112">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
