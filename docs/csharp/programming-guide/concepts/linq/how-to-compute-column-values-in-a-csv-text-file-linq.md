---
title: Come calcolare i valori delle colonne in un file di testo CSV (LINQ) (C
ms.date: 07/20/2015
ms.assetid: 4747f37a-a198-4df2-8efe-5b0731e0ea27
ms.openlocfilehash: 458950d58b15dcd572329228d76d85881043e07a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169350"
---
# <a name="how-to-compute-column-values-in-a-csv-text-file-linq-c"></a><span data-ttu-id="1c736-102">Come calcolare i valori delle colonne in un file di testo CSV (LINQ) (C</span><span class="sxs-lookup"><span data-stu-id="1c736-102">How to compute column values in a CSV text file (LINQ) (C#)</span></span>
<span data-ttu-id="1c736-103">In questo esempio viene illustrato come eseguire i calcoli di aggregazione quali Sum, Average, Min e Max nelle colonne di un file con estensione csv.</span><span class="sxs-lookup"><span data-stu-id="1c736-103">This example shows how to perform aggregate computations such as Sum, Average, Min, and Max on the columns of a .csv file.</span></span> <span data-ttu-id="1c736-104">I principi di esempio riportati di seguito possono essere applicati ad altri tipi di testo strutturati.</span><span class="sxs-lookup"><span data-stu-id="1c736-104">The example principles that are shown here can be applied to other types of structured text.</span></span>  
  
## <a name="to-create-the-source-file"></a><span data-ttu-id="1c736-105">Per creare il file di origine</span><span class="sxs-lookup"><span data-stu-id="1c736-105">To create the source file</span></span>  
  
1. <span data-ttu-id="1c736-106">Copiare le righe seguenti in un file denominato scores.csv e salvarlo nella cartella del progetto.</span><span class="sxs-lookup"><span data-stu-id="1c736-106">Copy the following lines into a file that is named scores.csv and save it in your project folder.</span></span> <span data-ttu-id="1c736-107">Si supponga che la prima colonna rappresenti degli ID studente e che le colonne successive rappresentino i punteggi di quattro esami.</span><span class="sxs-lookup"><span data-stu-id="1c736-107">Assume that the first column represents a student ID, and subsequent columns represent scores from four exams.</span></span>  
  
    ```csv
    111, 97, 92, 81, 60  
    112, 75, 84, 91, 39  
    113, 88, 94, 65, 91  
    114, 97, 89, 85, 82  
    115, 35, 72, 91, 70  
    116, 99, 86, 90, 94  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    119, 68, 79, 88, 92  
    120, 99, 82, 81, 79  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    ```  
  
## <a name="example"></a><span data-ttu-id="1c736-108">Esempio</span><span class="sxs-lookup"><span data-stu-id="1c736-108">Example</span></span>  
  
```csharp  
class SumColumns  
{  
    static void Main(string[] args)  
    {  
        string[] lines = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Specifies the column to compute.  
        int exam = 3;  
  
        // Spreadsheet format:  
        // Student ID    Exam#1  Exam#2  Exam#3  Exam#4  
        // 111,          97,     92,     81,     60  
  
        // Add one to exam to skip over the first column,  
        // which holds the student ID.  
        SingleColumn(lines, exam + 1);  
        Console.WriteLine();  
        MultiColumns(lines);  
  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    static void SingleColumn(IEnumerable<string> strs, int examNum)  
    {  
        Console.WriteLine("Single Column Query:");  
  
        // Parameter examNum specifies the column to
        // run the calculations on. This value could be  
        // passed in dynamically at runtime.
  
        // Variable columnQuery is an IEnumerable<int>.  
        // The following query performs two steps:  
        // 1) use Split to break each row (a string) into an array
        //    of strings,
        // 2) convert the element at position examNum to an int  
        //    and select it.  
        var columnQuery =  
            from line in strs  
            let elements = line.Split(',')  
            select Convert.ToInt32(elements[examNum]);  
  
        // Execute the query and cache the results to improve  
        // performance. This is helpful only with very large files.  
        var results = columnQuery.ToList();  
  
        // Perform aggregate calculations Average, Max, and  
        // Min on the column specified by examNum.  
        double average = results.Average();  
        int max = results.Max();  
        int min = results.Min();  
  
        Console.WriteLine("Exam #{0}: Average:{1:##.##} High Score:{2} Low Score:{3}",  
                 examNum, average, max, min);  
    }  
  
    static void MultiColumns(IEnumerable<string> strs)  
    {  
        Console.WriteLine("Multi Column Query:");  
  
        // Create a query, multiColQuery. Explicit typing is used  
        // to make clear that, when executed, multiColQuery produces
        // nested sequences. However, you get the same results by  
        // using 'var'.  
  
        // The multiColQuery query performs the following steps:  
        // 1) use Split to break each row (a string) into an array
        //    of strings,
        // 2) use Skip to skip the "Student ID" column, and store the
        //    rest of the row in scores.  
        // 3) convert each score in the current row from a string to  
        //    an int, and select that entire sequence as one row
        //    in the results.  
        IEnumerable<IEnumerable<int>> multiColQuery =  
            from line in strs  
            let elements = line.Split(',')  
            let scores = elements.Skip(1)  
            select (from str in scores  
                    select Convert.ToInt32(str));  
  
        // Execute the query and cache the results to improve  
        // performance.
        // ToArray could be used instead of ToList.  
        var results = multiColQuery.ToList();  
  
        // Find out how many columns you have in results.  
        int columnCount = results[0].Count();  
  
        // Perform aggregate calculations Average, Max, and  
        // Min on each column.
        // Perform one iteration of the loop for each column
        // of scores.  
        // You can use a for loop instead of a foreach loop
        // because you already executed the multiColQuery
        // query by calling ToList.  
        for (int column = 0; column < columnCount; column++)  
        {  
            var results2 = from row in results  
                           select row.ElementAt(column);  
            double average = results2.Average();  
            int max = results2.Max();  
            int min = results2.Min();  
  
            // Add one to column because the first exam is Exam #1,  
            // not Exam #0.  
            Console.WriteLine("Exam #{0} Average: {1:##.##} High Score: {2} Low Score: {3}",  
                          column + 1, average, max, min);  
        }  
    }  
}  
/* Output:  
    Single Column Query:  
    Exam #4: Average:76.92 High Score:94 Low Score:39  
  
    Multi Column Query:  
    Exam #1 Average: 86.08 High Score: 99 Low Score: 35  
    Exam #2 Average: 86.42 High Score: 94 Low Score: 72  
    Exam #3 Average: 84.75 High Score: 91 Low Score: 65  
    Exam #4 Average: 76.92 High Score: 94 Low Score: 39  
 */  
```  
  
 <span data-ttu-id="1c736-109">La query funziona usando il metodo <xref:System.String.Split%2A> per convertire ogni riga di testo in una matrice.</span><span class="sxs-lookup"><span data-stu-id="1c736-109">The query works by using the <xref:System.String.Split%2A> method to convert each line of text into an array.</span></span> <span data-ttu-id="1c736-110">Ogni elemento della matrice rappresenta una colonna.</span><span class="sxs-lookup"><span data-stu-id="1c736-110">Each array element represents a column.</span></span> <span data-ttu-id="1c736-111">Infine, il testo in ogni colonna viene convertito in una rappresentazione numerica.</span><span class="sxs-lookup"><span data-stu-id="1c736-111">Finally, the text in each column is converted to its numeric representation.</span></span> <span data-ttu-id="1c736-112">Se il file è un file con valori delimitati da tabulazioni, aggiornare solo l'argomento nel metodo `Split` in `\t`.</span><span class="sxs-lookup"><span data-stu-id="1c736-112">If your file is a tab-separated file, just update the argument in the `Split` method to `\t`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c736-113">Compilazione del codice</span><span class="sxs-lookup"><span data-stu-id="1c736-113">Compiling the Code</span></span>  
 <span data-ttu-id="1c736-114">Creare un progetto di applicazione console C# con direttive `using` per gli spazi dei nomi System.Linq e System.IO.</span><span class="sxs-lookup"><span data-stu-id="1c736-114">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c736-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1c736-115">See also</span></span>

- [<span data-ttu-id="1c736-116">LINQ e stringhe (C#)</span><span class="sxs-lookup"><span data-stu-id="1c736-116">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="1c736-117">Directory di file e LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="1c736-117">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
