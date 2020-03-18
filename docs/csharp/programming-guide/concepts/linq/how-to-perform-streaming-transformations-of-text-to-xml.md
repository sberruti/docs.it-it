---
title: Come eseguire trasformazioni di streaming di testo in xml (C )How to perform streaming transformations of text to XML (C
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 496535b7f868095a62be2b72b1eea2b082e00a44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345800"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="0d081-102">Come eseguire trasformazioni di streaming di testo in xml (C )How to perform streaming transformations of text to XML (C</span><span class="sxs-lookup"><span data-stu-id="0d081-102">How to perform streaming transformations of text to XML (C#)</span></span>

<span data-ttu-id="0d081-103">Uno degli approcci disponibili per l'elaborazione di un file di testo consiste nello scrivere un metodo di estensione che genera un flusso del file di testo, una riga alla volta, tramite il costrutto `yield return`.</span><span class="sxs-lookup"><span data-stu-id="0d081-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="0d081-104">È quindi possibile scrivere una query LINQ che elabora il file di testo in modo posticipato lazy.</span><span class="sxs-lookup"><span data-stu-id="0d081-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="0d081-105">Se poi si usa <xref:System.Xml.Linq.XStreamingElement> per il flusso di output, è possibile creare una trasformazione del file di testo in XML che usa una quantità minima di memoria, indipendentemente dalle dimensioni del file di testo di origine.</span><span class="sxs-lookup"><span data-stu-id="0d081-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

 <span data-ttu-id="0d081-106">È necessario tener conto di alcune considerazioni in relazione alle trasformazioni di flusso.</span><span class="sxs-lookup"><span data-stu-id="0d081-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="0d081-107">Le trasformazioni di flusso sono ideali nelle situazioni in cui è possibile elaborare l'intero file una sola volta e se è possibile elaborare le righe nell'ordine in cui sono riportate nel documento di origine.</span><span class="sxs-lookup"><span data-stu-id="0d081-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="0d081-108">Se è necessario elaborare il file più volte o ordinare le righe prima che sia possibile elaborarle, si perderanno molti dei vantaggi associati all'utilizzo di una tecnica di flusso.</span><span class="sxs-lookup"><span data-stu-id="0d081-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>

## <a name="example"></a><span data-ttu-id="0d081-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="0d081-109">Example</span></span>

 <span data-ttu-id="0d081-110">Il file di testo seguente, People.txt, è l'origine di questo esempio.</span><span class="sxs-lookup"><span data-stu-id="0d081-110">The following text file, People.txt, is the source for this example.</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 <span data-ttu-id="0d081-111">Nel codice seguente è contenuto un metodo di estensione che genera il flusso delle righe del file di testo in modo posticipato.</span><span class="sxs-lookup"><span data-stu-id="0d081-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
        while ((line = source.ReadLine()) != null)
        {
            yield return line;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
            from line in sr.Lines()
            let items = line.Split(',')
            where !line.StartsWith("#")
            select new XElement("Person",
                       new XAttribute("ID", items[0]),
                       new XElement("First", items[1]),
                       new XElement("Last", items[2]),
                       new XElement("Occupation", items[3])
                   )
        );
        Console.WriteLine(xmlTree);
        sr.Close();
    }
}
```

 <span data-ttu-id="0d081-112">Nell'esempio viene prodotto l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="0d081-112">This example produces the following output:</span></span>

```xml
<Root>
  <Person ID="1">
    <First>Tai</First>
    <Last>Yee</Last>
    <Occupation>Writer</Occupation>
  </Person>
  <Person ID="2">
    <First>Nikolay</First>
    <Last>Grachev</Last>
    <Occupation>Programmer</Occupation>
  </Person>
  <Person ID="3">
    <First>David</First>
    <Last>Wright</Last>
    <Occupation>Inventor</Occupation>
  </Person>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="0d081-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0d081-113">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
