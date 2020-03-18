---
title: Come popolare una struttura ad albero XML dal file system (C
ms.date: 07/20/2015
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: beb44be1a787fa09b091aa48022dbb5b10c4632b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345776"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-c"></a><span data-ttu-id="785ee-102">Come popolare una struttura ad albero XML dal file system (C</span><span class="sxs-lookup"><span data-stu-id="785ee-102">How to populate an XML tree from the file system (C#)</span></span>
<span data-ttu-id="785ee-103">Un'applicazione utile e comune degli alberi XML è data dall'utilizzo come archivio dati nome/valore gerarchico.</span><span class="sxs-lookup"><span data-stu-id="785ee-103">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="785ee-104">È possibile popolare un albero XML con dati gerarchici e quindi eseguirvi query, trasformarla e, se necessario, serializzarla.</span><span class="sxs-lookup"><span data-stu-id="785ee-104">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="785ee-105">In questo scenario di utilizzo molte delle caratteristiche semantiche specifiche di XML, quali gli spazi dei nomi e il comportamento degli spazi vuoti, non sono rilevanti.</span><span class="sxs-lookup"><span data-stu-id="785ee-105">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="785ee-106">L'albero XML viene invece usato come piccolo database gerarchico in memoria per singolo utente.</span><span class="sxs-lookup"><span data-stu-id="785ee-106">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="785ee-107">Esempio</span><span class="sxs-lookup"><span data-stu-id="785ee-107">Example</span></span>  
 <span data-ttu-id="785ee-108">Nell'esempio seguente un albero XML viene popolato dal file system locale tramite la ricorsione.</span><span class="sxs-lookup"><span data-stu-id="785ee-108">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="785ee-109">Viene quindi eseguita una query sull'albero per calcolare le dimensioni totali di tutti i file dell'albero.</span><span class="sxs-lookup"><span data-stu-id="785ee-109">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
```csharp  
class Program  
{  
    static XElement CreateFileSystemXmlTree(string source)  
    {  
        DirectoryInfo di = new DirectoryInfo(source);  
        return new XElement("Dir",  
            new XAttribute("Name", di.Name),  
            from d in Directory.GetDirectories(source)  
            select CreateFileSystemXmlTree(d),  
            from fi in di.GetFiles()  
            select new XElement("File",  
                new XElement("Name", fi.Name),  
                new XElement("Length", fi.Length)  
            )  
        );  
    }  
  
    static void Main(string[] args)  
    {  
        XElement fileSystemTree = CreateFileSystemXmlTree("C:/Tmp");  
        Console.WriteLine(fileSystemTree);  
        Console.WriteLine("------");  
        long totalFileSize =  
            (from f in fileSystemTree.Descendants("File")  
             select (long)f.Element("Length")).Sum();  
        Console.WriteLine("Total File Size:{0}", totalFileSize);  
    }  
}  
```  
  
 <span data-ttu-id="785ee-110">In questo esempio viene prodotto un output simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="785ee-110">This example produces output similar to the following:</span></span>  
  
```xml  
<Dir Name="Tmp">  
  <Dir Name="ConsoleApplication1">  
    <Dir Name="bin">  
      <Dir Name="Debug">  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe</Name>  
          <Length>9568</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>  
          <Length>473</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="obj">  
      <Dir Name="Debug">  
        <Dir Name="TempPE" />  
        <File>  
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>  
          <Length>322</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="Properties">  
      <File>  
        <Name>AssemblyInfo.cs</Name>  
        <Length>1454</Length>  
      </File>  
    </Dir>  
    <File>  
      <Name>ConsoleApplication1.csproj</Name>  
      <Length>2546</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.sln</Name>  
      <Length>937</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.suo</Name>  
      <Length>10752</Length>  
    </File>  
    <File>  
      <Name>Program.cs</Name>  
      <Length>269</Length>  
    </File>  
  </Dir>  
</Dir>  
------  
Total File Size:59089  
```  
