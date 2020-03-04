---
title: Istruzioni C# - Panoramica del linguaggio C#
description: Le azioni di un programma C# vengono create mediante istruzioni
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159104"
---
# <a name="statements"></a><span data-ttu-id="da2a4-103">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="da2a4-103">Statements</span></span>

<span data-ttu-id="da2a4-104">Le azioni di un programma vengono espresse mediante *istruzioni*.</span><span class="sxs-lookup"><span data-stu-id="da2a4-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="da2a4-105">C# supporta numerosi tipi di istruzioni, alcune delle quali sono definite in termini di istruzioni nidificate.</span><span class="sxs-lookup"><span data-stu-id="da2a4-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="da2a4-106">Un *blocco* consente di scrivere più istruzioni nei contesti in cui ne è consentita una sola.</span><span class="sxs-lookup"><span data-stu-id="da2a4-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="da2a4-107">Un blocco è costituito da un elenco di istruzioni scritte tra i delimitatori `{` e `}`.</span><span class="sxs-lookup"><span data-stu-id="da2a4-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="da2a4-108">Le *istruzioni di dichiarazione* vengono usate per dichiarare le costanti e le variabili locali.</span><span class="sxs-lookup"><span data-stu-id="da2a4-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="da2a4-109">Le *istruzioni di espressione* vengono usate per valutare le espressioni.</span><span class="sxs-lookup"><span data-stu-id="da2a4-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="da2a4-110">Le espressioni che possono essere usate come istruzioni includono le chiamate ai metodi, le allocazioni di oggetti mediante l'operatore `new`, le assegnazioni mediante `=` e gli operatori di assegnazione composta, le operazioni di incremento e decremento mediante gli operatori `++` e `--` e le espressioni `await`.</span><span class="sxs-lookup"><span data-stu-id="da2a4-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="da2a4-111">Le *istruzioni di selezione* vengono usate per selezionare una tra più istruzioni che è possibile eseguire sulla base del valore di alcune espressioni.</span><span class="sxs-lookup"><span data-stu-id="da2a4-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="da2a4-112">Questo gruppo contiene le istruzioni `if` e `switch`.</span><span class="sxs-lookup"><span data-stu-id="da2a4-112">This group contains the `if` and `switch` statements.</span></span>

<span data-ttu-id="da2a4-113">Le *istruzioni di iterazione* vengono usate per eseguire più volte un'istruzione nidificata.</span><span class="sxs-lookup"><span data-stu-id="da2a4-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="da2a4-114">Questo gruppo contiene le istruzioni `while`, `do`, `for`e `foreach`.</span><span class="sxs-lookup"><span data-stu-id="da2a4-114">This group contains the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="da2a4-115">Le *istruzioni di spostamento* vengono usate per trasferire il controllo.</span><span class="sxs-lookup"><span data-stu-id="da2a4-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="da2a4-116">Questo gruppo contiene le istruzioni `break`, `continue`, `goto`, `throw`, `return`e `yield`.</span><span class="sxs-lookup"><span data-stu-id="da2a4-116">This group contains the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="da2a4-117">L'istruzione `try`...`catch` viene usata per rilevare le eccezioni che si verificano durante l'esecuzione di un blocco, mentre l'istruzione `try`...`finally` viene usata per specificare il codice di finalizzazione che viene eseguito sempre, indipendentemente dal fatto che si sia verificata un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="da2a4-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="da2a4-118">Le istruzioni `checked` e `unchecked` vengono usate per verificare il contesto di controllo dell'overflow per le conversioni e le operazioni aritmetiche di tipo integrale.</span><span class="sxs-lookup"><span data-stu-id="da2a4-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="da2a4-119">L'istruzione `lock` viene usata per ottenere il blocco a esclusione reciproca per un oggetto specificato, eseguire un'istruzione e quindi rilasciare il blocco.</span><span class="sxs-lookup"><span data-stu-id="da2a4-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="da2a4-120">L'istruzione `using` viene usata per ottenere una risorsa, eseguire un'istruzione e quindi eliminare la risorsa.</span><span class="sxs-lookup"><span data-stu-id="da2a4-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="da2a4-121">Di seguito vengono elencati i tipi di istruzione che è possibile usare e viene offerto un esempio di ciascuna.</span><span class="sxs-lookup"><span data-stu-id="da2a4-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="da2a4-122">Dichiarazione di variabile locale:</span><span class="sxs-lookup"><span data-stu-id="da2a4-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="da2a4-123">Dichiarazione di costante locale:</span><span class="sxs-lookup"><span data-stu-id="da2a4-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="da2a4-124">Istruzione di espressione:</span><span class="sxs-lookup"><span data-stu-id="da2a4-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="da2a4-125">Istruzione `if`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="da2a4-126">Istruzione `switch`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="da2a4-127">Istruzione `while`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="da2a4-128">Istruzione `do`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="da2a4-129">Istruzione `for`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="da2a4-130">Istruzione `foreach`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="da2a4-131">Istruzione `break`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="da2a4-132">Istruzione `continue`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="da2a4-133">Istruzione `goto`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="da2a4-134">Istruzione `return`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="da2a4-135">Istruzione `yield`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="da2a4-136">Istruzioni `throw` e istruzioni `try`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="da2a4-137">Istruzioni `checked` e `unchecked`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="da2a4-138">Istruzione `lock`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="da2a4-139">Istruzione `using`:</span><span class="sxs-lookup"><span data-stu-id="da2a4-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
><span data-ttu-id="da2a4-140">[Precedente](expressions.md)
>[Successivo](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="da2a4-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
