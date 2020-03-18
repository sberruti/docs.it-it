---
title: Come eseguire il codice di pulitura utilizzando infine - Guida per programmatori C
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705275"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="230e4-102">Come eseguire il codice di pulitura utilizzando finally (Guida per programmatori C</span><span class="sxs-lookup"><span data-stu-id="230e4-102">How to execute cleanup code using finally (C# Programming Guide)</span></span>
<span data-ttu-id="230e4-103">Lo scopo di un'istruzione `finally` consiste nel garantire che la pulizia necessaria di oggetti, in genere oggetti che contengono risorse esterne, venga eseguita immediatamente, anche se viene generata un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="230e4-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="230e4-104">Un esempio di questo tipo di pulizia è la chiamata di <xref:System.IO.Stream.Close%2A> in un oggetto <xref:System.IO.FileStream> immediatamente dopo l'uso, invece di aspettare che l'oggetto venga sottoposto a Garbage Collection da Common Language Runtime, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="230e4-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a><span data-ttu-id="230e4-105">Esempio</span><span class="sxs-lookup"><span data-stu-id="230e4-105">Example</span></span>  
 <span data-ttu-id="230e4-106">Per trasformare il codice precedente in un'istruzione `try-catch-finally`, il codice di pulitura viene separato dal codice di lavoro, come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="230e4-106">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 <span data-ttu-id="230e4-107">Poiché può verificarsi un'eccezione in qualsiasi momento all'interno del blocco `try` prima della chiamata a `OpenWrite()`, oppure la chiamata a `OpenWrite()` stessa potrebbe non riuscire, non esiste alcuna garanzia che il file sia aperto quando si tenta di chiuderlo.</span><span class="sxs-lookup"><span data-stu-id="230e4-107">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="230e4-108">Il blocco `finally` aggiunge un controllo per verificare che l'oggetto <xref:System.IO.FileStream> non sia `null` prima di chiamare il metodo <xref:System.IO.Stream.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="230e4-108">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="230e4-109">Senza il controllo di `null`, il blocco `finally` potrebbe generare la propria eccezione <xref:System.NullReferenceException>, ma la generazione di eccezioni nei blocchi `finally` deve essere evitata, se possibile.</span><span class="sxs-lookup"><span data-stu-id="230e4-109">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="230e4-110">Una connessione di database è un altro elemento ideale da chiudere in un blocco `finally`.</span><span class="sxs-lookup"><span data-stu-id="230e4-110">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="230e4-111">Poiché il numero di connessioni consentite in un server di database è talvolta limitato, è necessario chiudere le connessioni di database il più rapidamente possibile.</span><span class="sxs-lookup"><span data-stu-id="230e4-111">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="230e4-112">Se viene generata un'eccezione prima che la connessione venga chiusa, l'uso del blocco `finally` è preferibile rispetto all'attesa di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="230e4-112">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="230e4-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="230e4-113">See also</span></span>

- [<span data-ttu-id="230e4-114">Guida per programmatori C#</span><span class="sxs-lookup"><span data-stu-id="230e4-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="230e4-115">Eccezioni e gestione delle eccezioni</span><span class="sxs-lookup"><span data-stu-id="230e4-115">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="230e4-116">Gestione delle eccezioni</span><span class="sxs-lookup"><span data-stu-id="230e4-116">Exception Handling</span></span>](./exception-handling.md)
- [<span data-ttu-id="230e4-117">Istruzione using</span><span class="sxs-lookup"><span data-stu-id="230e4-117">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
- [<span data-ttu-id="230e4-118">try-catch</span><span class="sxs-lookup"><span data-stu-id="230e4-118">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="230e4-119">try...finally</span><span class="sxs-lookup"><span data-stu-id="230e4-119">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="230e4-120">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="230e4-120">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
