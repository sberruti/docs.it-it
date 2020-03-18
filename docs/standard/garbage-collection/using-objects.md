---
title: Uso di oggetti che implementano IDisposable
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: c5232aa89064c514e71f3a18bc754159e9c9b15b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160281"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="af2bc-102">Uso di oggetti che implementano IDisposable</span><span class="sxs-lookup"><span data-stu-id="af2bc-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="af2bc-103">Il recupero della memoria usata dagli oggetti gestiti viene eseguito dal Garbage Collector di Common Language Runtime, ma i tipi che usano le risorse non gestite implementano l'interfaccia <xref:System.IDisposable> per consentire il recupero di tale memoria non gestita.</span><span class="sxs-lookup"><span data-stu-id="af2bc-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="af2bc-104">Dopo avere utilizzato un oggetto che implementa <xref:System.IDisposable>, è necessario chiamare l'implementazione <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="af2bc-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="af2bc-105">Questa operazione può essere eseguita in due modi:</span><span class="sxs-lookup"><span data-stu-id="af2bc-105">You can do this in one of two ways:</span></span>  
  
- <span data-ttu-id="af2bc-106">Con l'istruzione `using` in C# o l'istruzione `Using` in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="af2bc-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
- <span data-ttu-id="af2bc-107">Implementando un blocco `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="af2bc-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="af2bc-108">Istruzione using</span><span class="sxs-lookup"><span data-stu-id="af2bc-108">The using statement</span></span>

<span data-ttu-id="af2bc-109">L'istruzione `using` in C# e l'istruzione `Using` in Visual Basic semplificano il codice da scrivere per creare e pulire un oggetto.</span><span class="sxs-lookup"><span data-stu-id="af2bc-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="af2bc-110">L'istruzione `using` ottiene una o più risorse, esegue le istruzioni specificate ed elimina l'oggetto in modo automatico.</span><span class="sxs-lookup"><span data-stu-id="af2bc-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="af2bc-111">L'istruzione `using` è comunque utile solo per gli oggetti usati nell'ambito del metodo in cui vengono costruiti.</span><span class="sxs-lookup"><span data-stu-id="af2bc-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="af2bc-112">Nell'esempio seguente viene utilizzata l'istruzione `using` per creare e rilasciare un oggetto <xref:System.IO.StreamReader?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af2bc-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="af2bc-113">Si noti che, anche se la classe <xref:System.IO.StreamReader> implementa l'interfaccia <xref:System.IDisposable>, a indicare che utilizza una risorsa non gestita, nell'esempio non viene chiamato il metodo <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="af2bc-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="af2bc-114">Quando nel compilatore C# o Visual Basic viene rilevata l'istruzione `using`, viene generato il linguaggio intermedio (IL) equivalente al codice seguente, che contiene un blocco `try/finally` in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="af2bc-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="af2bc-115">L'istruzione `using` C# è consente anche di acquisire più risorse in un'unica istruzione, che equivale internamente all'uso di più istruzioni `using` annidate.</span><span class="sxs-lookup"><span data-stu-id="af2bc-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="af2bc-116">Nell'esempio seguente viene creata l'istanza di due oggetti <xref:System.IO.StreamReader> per leggere il contenuto di due diversi file.</span><span class="sxs-lookup"><span data-stu-id="af2bc-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="af2bc-117">Blocco try/finally</span><span class="sxs-lookup"><span data-stu-id="af2bc-117">Try/finally block</span></span>

<span data-ttu-id="af2bc-118">Anziché eseguire il wrapping di un blocco `try/finally` in un'istruzione `using`, è possibile implementare direttamente il blocco `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="af2bc-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="af2bc-119">La scelta può essere espressione dello stile di codifica personale oppure essere dovuta a uno dei seguenti motivi:</span><span class="sxs-lookup"><span data-stu-id="af2bc-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
- <span data-ttu-id="af2bc-120">Includere un blocco `catch` per gestire eventuali eccezioni generate nel blocco `try`.</span><span class="sxs-lookup"><span data-stu-id="af2bc-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="af2bc-121">In caso contrario, tutte le eccezioni generate dall'istruzione `using` non vengono gestite, analogamente alle eccezioni generate all'interno del blocco `using` se un blocco `try/catch` non è presente.</span><span class="sxs-lookup"><span data-stu-id="af2bc-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
- <span data-ttu-id="af2bc-122">Creare un'istanza di un oggetto che implementa <xref:System.IDisposable> il cui ambito non è locale rispetto al blocco in cui viene dichiarato.</span><span class="sxs-lookup"><span data-stu-id="af2bc-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="af2bc-123">L'esempio seguente è simile a quello precedente, con la differenza che in questo viene usato un blocco `try/catch/finally` per creare un'istanza di un oggetto <xref:System.IO.StreamReader>, utilizzarla ed eliminarla e per gestire le eccezioni generate dal costruttore <xref:System.IO.StreamReader> e dal relativo metodo <xref:System.IO.StreamReader.ReadToEnd%2A>.</span><span class="sxs-lookup"><span data-stu-id="af2bc-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="af2bc-124">Si noti che il codice nel blocco `finally` controlla che l'oggetto che implementa <xref:System.IDisposable> non sia `null` prima di chiamare il metodo <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="af2bc-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="af2bc-125">L'omissione di tale controllo può provocare un'eccezione <xref:System.NullReferenceException> in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="af2bc-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="af2bc-126">È possibile usare questo modello di base se si decide di implementare o è necessario implementare un blocco `try/finally`, poiché il linguaggio di programmazione non supporta un'istruzione `using` ma consente chiamate dirette al metodo <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="af2bc-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="af2bc-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="af2bc-127">See also</span></span>

- [<span data-ttu-id="af2bc-128">Pulizia delle risorse non gestite</span><span class="sxs-lookup"><span data-stu-id="af2bc-128">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="af2bc-129">Istruzione using (Riferimenti per C</span><span class="sxs-lookup"><span data-stu-id="af2bc-129">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="af2bc-130">Istruzione using (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af2bc-130">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
