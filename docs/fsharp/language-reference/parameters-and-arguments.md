---
title: Parametri e argomenti
description: Informazioni sul supporto del linguaggio F , per la definizione di parametri e il passaggio di argomenti a funzioni, metodi e proprietà.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400197"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="12319-103">Parametri e argomenti</span><span class="sxs-lookup"><span data-stu-id="12319-103">Parameters and Arguments</span></span>

<span data-ttu-id="12319-104">In questo argomento viene descritto il supporto del linguaggio per la definizione di parametri e il passaggio di argomenti a funzioni, metodi e proprietà.</span><span class="sxs-lookup"><span data-stu-id="12319-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="12319-105">Include informazioni su come passare per riferimento e su come definire e utilizzare metodi che possono accettare un numero variabile di argomenti.</span><span class="sxs-lookup"><span data-stu-id="12319-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="12319-106">Parametri e argomenti</span><span class="sxs-lookup"><span data-stu-id="12319-106">Parameters and Arguments</span></span>

<span data-ttu-id="12319-107">Il termine *parametro* viene utilizzato per descrivere i nomi per i valori che si prevede di fornire.</span><span class="sxs-lookup"><span data-stu-id="12319-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="12319-108">Il termine *argomento* viene utilizzato per i valori forniti per ogni parametro.</span><span class="sxs-lookup"><span data-stu-id="12319-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="12319-109">I parametri possono essere specificati in formato tupla o sottoposto a currying o in una combinazione dei due.</span><span class="sxs-lookup"><span data-stu-id="12319-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="12319-110">È possibile passare argomenti utilizzando un nome di parametro esplicito.</span><span class="sxs-lookup"><span data-stu-id="12319-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="12319-111">I parametri dei metodi possono essere specificati come facoltativi e viene assegnato un valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="12319-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="12319-112">Modelli di parametroParameter Patterns</span><span class="sxs-lookup"><span data-stu-id="12319-112">Parameter Patterns</span></span>

<span data-ttu-id="12319-113">I parametri forniti a funzioni e metodi sono, in generale, modelli separati da spazi.</span><span class="sxs-lookup"><span data-stu-id="12319-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="12319-114">Ciò significa che, in linea di principio, qualsiasi modello descritto in [Espressioni](match-expressions.md) di corrispondenza può essere utilizzato in un elenco di parametri per una funzione o un membro.</span><span class="sxs-lookup"><span data-stu-id="12319-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="12319-115">I metodi usano in genere la forma di tupla di passaggio di argomenti.</span><span class="sxs-lookup"><span data-stu-id="12319-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="12319-116">Ciò consente di ottenere un risultato più chiaro dal punto di vista di altri linguaggi .NET perché il formato della tupla corrisponde al modo in cui gli argomenti vengono passati nei metodi .NET.</span><span class="sxs-lookup"><span data-stu-id="12319-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="12319-117">Il formato sottoposto a currysima viene `let` utilizzato più spesso con le funzioni create tramite associazioni.</span><span class="sxs-lookup"><span data-stu-id="12319-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="12319-118">Lo pseudocodice seguente mostra esempi di tuple e argomenti sottoposti a currying.</span><span class="sxs-lookup"><span data-stu-id="12319-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="12319-119">Le forme combinate sono possibili quando alcuni argomenti sono in tuple e altri no.</span><span class="sxs-lookup"><span data-stu-id="12319-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="12319-120">Altri modelli possono essere usati anche negli elenchi di parametri, ma se il modello di parametro non corrisponde a tutti i possibili input, potrebbe esserci una corrispondenza incompleta in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="12319-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="12319-121">L'eccezione `MatchFailureException` viene generata quando il valore di un argomento non corrisponde ai modelli specificati nell'elenco di parametri.</span><span class="sxs-lookup"><span data-stu-id="12319-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="12319-122">Il compilatore genera un avviso quando un modello di parametro consente corrispondenze incomplete.</span><span class="sxs-lookup"><span data-stu-id="12319-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="12319-123">Almeno un altro modello è in genere utile per gli elenchi di parametri, ovvero il modello con caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="12319-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="12319-124">Utilizzare il modello con caratteri jolly in un elenco di parametri quando si desidera semplicemente ignorare gli argomenti forniti.</span><span class="sxs-lookup"><span data-stu-id="12319-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="12319-125">Nel codice seguente viene illustrato l'utilizzo del modello con caratteri jolly in un elenco di argomenti.</span><span class="sxs-lookup"><span data-stu-id="12319-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="12319-126">Il modello con caratteri jolly può essere utile ogni volta che non sono necessari gli argomenti passati, ad esempio nel punto di ingresso principale di un programma, quando non si è interessati agli argomenti della riga di comando normalmente forniti come matrice di stringhe, come nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="12319-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="12319-127">Altri modelli che vengono talvolta `as` utilizzati negli argomenti sono il modello e i modelli di identificatore associati alle unioni discriminate e ai modelli attivi.</span><span class="sxs-lookup"><span data-stu-id="12319-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="12319-128">È possibile utilizzare il modello di unione discriminato caso singolo come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="12319-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="12319-129">L'output è indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="12319-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="12319-130">I modelli attivi possono essere utili come parametri, ad esempio quando si trasforma un argomento in un formato desiderato, come nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="12319-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="12319-131">È possibile `as` utilizzare il modello per archiviare un valore corrispondente come valore locale, come illustrato nella riga di codice seguente.</span><span class="sxs-lookup"><span data-stu-id="12319-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="12319-132">Un altro modello utilizzato occasionalmente è una funzione che lascia l'ultimo argomento senza nome fornendo, come corpo della funzione, un'espressione lambda che esegue immediatamente una corrispondenza del modello sull'argomento implicito.</span><span class="sxs-lookup"><span data-stu-id="12319-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="12319-133">Un esempio è la seguente riga di codice.</span><span class="sxs-lookup"><span data-stu-id="12319-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="12319-134">Questo codice definisce una funzione che `true` accetta un elenco generico e restituisce se l'elenco è vuoto e `false` in caso contrario.</span><span class="sxs-lookup"><span data-stu-id="12319-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="12319-135">L'uso di tali tecniche può rendere il codice più difficile da leggere.</span><span class="sxs-lookup"><span data-stu-id="12319-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="12319-136">Occasionalmente, i modelli che implicano corrispondenze incomplete sono utili, ad esempio, se si sa che gli elenchi nel programma hanno solo tre elementi, è possibile utilizzare un modello simile al seguente in un elenco di parametri.</span><span class="sxs-lookup"><span data-stu-id="12319-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="12319-137">L'uso di modelli con corrispondenze incomplete è meglio riservato per la prototipazione rapida e altri usi temporanei.</span><span class="sxs-lookup"><span data-stu-id="12319-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="12319-138">Il compilatore genererà un avviso per tale codice.</span><span class="sxs-lookup"><span data-stu-id="12319-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="12319-139">Tali modelli non possono coprire il caso generale di tutti i possibili input e pertanto non sono adatti per le API dei componenti.</span><span class="sxs-lookup"><span data-stu-id="12319-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="12319-140">Argomenti denominati</span><span class="sxs-lookup"><span data-stu-id="12319-140">Named Arguments</span></span>

<span data-ttu-id="12319-141">Gli argomenti per i metodi possono essere specificati in base alla posizione in un elenco di argomenti delimitati da virgole oppure possono essere passati a un metodo in modo esplicito fornendo il nome, seguito da un segno di uguale e dal valore da passare.</span><span class="sxs-lookup"><span data-stu-id="12319-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="12319-142">Se specificati specificando il nome, possono essere visualizzati in un ordine diverso da quello utilizzato nella dichiarazione.</span><span class="sxs-lookup"><span data-stu-id="12319-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="12319-143">Gli argomenti denominati possono rendere il codice più leggibile e più adattabile a determinati tipi di modifiche nell'API, ad esempio un riordinamento dei parametri del metodo.</span><span class="sxs-lookup"><span data-stu-id="12319-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="12319-144">Gli argomenti denominati sono consentiti solo per i metodi, non per `let`le funzioni associate, i valori di funzione o le espressioni lambda.</span><span class="sxs-lookup"><span data-stu-id="12319-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="12319-145">Nell'esempio di codice riportato di seguito viene illustrato l'utilizzo di argomenti denominati.</span><span class="sxs-lookup"><span data-stu-id="12319-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="12319-146">In una chiamata a un costruttore di classe, è possibile impostare i valori delle proprietà della classe utilizzando una sintassi simile a quella degli argomenti denominati.</span><span class="sxs-lookup"><span data-stu-id="12319-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="12319-147">Nell'esempio seguente viene illustrata questa sintassi.</span><span class="sxs-lookup"><span data-stu-id="12319-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="12319-148">Per ulteriori informazioni, vedere [Costruttori (F )](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="12319-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="12319-149">Parametri facoltativi</span><span class="sxs-lookup"><span data-stu-id="12319-149">Optional Parameters</span></span>

<span data-ttu-id="12319-150">È possibile specificare un parametro facoltativo per un metodo utilizzando un punto interrogativo prima del nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="12319-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="12319-151">I parametri facoltativi vengono interpretati come il tipo di opzione F, pertanto è possibile `match` eseguire `Some` `None`una query in modo regolare in cui vengono eseguite query sui tipi di opzione, utilizzando un'espressione con e .</span><span class="sxs-lookup"><span data-stu-id="12319-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="12319-152">I parametri facoltativi sono consentiti solo `let` sui membri, non sulle funzioni create tramite associazioni.</span><span class="sxs-lookup"><span data-stu-id="12319-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="12319-153">È possibile passare i valori facoltativi esistenti `?arg=None` `?arg=Some(3)` al `?arg=arg`metodo in base al nome del parametro, ad esempio o o .</span><span class="sxs-lookup"><span data-stu-id="12319-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="12319-154">Ciò può essere utile quando si compila un metodo che passa argomenti facoltativi a un altro metodo.</span><span class="sxs-lookup"><span data-stu-id="12319-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="12319-155">È inoltre possibile `defaultArg`utilizzare una funzione , che imposta un valore predefinito di un argomento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="12319-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="12319-156">La `defaultArg` funzione accetta il parametro facoltativo come primo argomento e il valore predefinito come secondo.</span><span class="sxs-lookup"><span data-stu-id="12319-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="12319-157">Nell'esempio seguente viene illustrato l'utilizzo di parametri facoltativi.</span><span class="sxs-lookup"><span data-stu-id="12319-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="12319-158">L'output è indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="12319-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="12319-159">Ai fini dell'interoperabilità di C e `[<Optional; DefaultParameterValue<(...)>]` Visual Basic è possibile utilizzare gli attributi in F , in modo che i chiamanti vedranno un argomento come facoltativo.</span><span class="sxs-lookup"><span data-stu-id="12319-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="12319-160">Ciò equivale a definire l'argomento come `MyMethod(int i = 3)`facoltativo in C , come in .</span><span class="sxs-lookup"><span data-stu-id="12319-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="12319-161">È inoltre possibile specificare un nuovo oggetto come valore di parametro predefinito.</span><span class="sxs-lookup"><span data-stu-id="12319-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="12319-162">Ad esempio, `Foo` il membro `CancellationToken` potrebbe avere un optional come input invece:For example, the member could have an optional as input instead:</span><span class="sxs-lookup"><span data-stu-id="12319-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="12319-163">Il valore fornito `DefaultParameterValue` come argomento deve corrispondere al tipo del parametro.</span><span class="sxs-lookup"><span data-stu-id="12319-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="12319-164">Ad esempio, non è consentito quanto segue:</span><span class="sxs-lookup"><span data-stu-id="12319-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="12319-165">In questo caso, il compilatore genera un avviso e ignorerà entrambi gli attributi del tutto.</span><span class="sxs-lookup"><span data-stu-id="12319-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="12319-166">Si noti `null` che il valore predefinito deve essere annotato in tipo, altrimenti il `[<Optional; DefaultParameterValue(null:obj)>] o:obj`compilatore deduce il tipo errato, ad esempio .</span><span class="sxs-lookup"><span data-stu-id="12319-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="12319-167">Passaggio per riferimentoPassing by Reference</span><span class="sxs-lookup"><span data-stu-id="12319-167">Passing by Reference</span></span>

<span data-ttu-id="12319-168">Il passaggio di un valore F , per riferimento, implica byrefs , che sono tipi puntatore [gestiti.](byrefs.md)</span><span class="sxs-lookup"><span data-stu-id="12319-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="12319-169">Le indicazioni per il tipo da utilizzare sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="12319-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="12319-170">Utilizzare `inref<'T>` se è sufficiente leggere il puntatore.</span><span class="sxs-lookup"><span data-stu-id="12319-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="12319-171">Utilizzare `outref<'T>` se è necessario scrivere solo nel puntatore.</span><span class="sxs-lookup"><span data-stu-id="12319-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="12319-172">Utilizzare `byref<'T>` se è necessario leggere e scrivere nel puntatore.</span><span class="sxs-lookup"><span data-stu-id="12319-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

<span data-ttu-id="12319-173">Poiché il parametro è un puntatore e il valore è modificabile, tutte le modifiche apportate al valore vengono mantenute dopo l'esecuzione della funzione.</span><span class="sxs-lookup"><span data-stu-id="12319-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="12319-174">È possibile usare una tupla `out` come valore restituito per archiviare tutti i parametri nei metodi della libreria .NET.</span><span class="sxs-lookup"><span data-stu-id="12319-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="12319-175">In alternativa, è `out` possibile considerare `byref` il parametro come parametro.</span><span class="sxs-lookup"><span data-stu-id="12319-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="12319-176">Nell'esempio di codice riportato di seguito vengono illustrate entrambe le modalità.</span><span class="sxs-lookup"><span data-stu-id="12319-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="12319-177">Matrici di parametri</span><span class="sxs-lookup"><span data-stu-id="12319-177">Parameter Arrays</span></span>

<span data-ttu-id="12319-178">Occasionalmente è necessario definire una funzione che accetta un numero arbitrario di parametri di tipo eterogeneo.</span><span class="sxs-lookup"><span data-stu-id="12319-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="12319-179">Non sarebbe pratico creare tutti i possibili metodi di overload per tenere conto di tutti i tipi che potrebbero essere utilizzati.</span><span class="sxs-lookup"><span data-stu-id="12319-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="12319-180">Le implementazioni di .NET forniscono il supporto per tali metodi tramite la funzionalità di matrice di parametri.</span><span class="sxs-lookup"><span data-stu-id="12319-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="12319-181">Un metodo che accetta una matrice di parametri nella firma può essere fornito con un numero arbitrario di parametri.</span><span class="sxs-lookup"><span data-stu-id="12319-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="12319-182">I parametri vengono inseriti in una matrice.</span><span class="sxs-lookup"><span data-stu-id="12319-182">The parameters are put into an array.</span></span> <span data-ttu-id="12319-183">Il tipo degli elementi della matrice determina i tipi di parametro che possono essere passati alla funzione.</span><span class="sxs-lookup"><span data-stu-id="12319-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="12319-184">Se si definisce `System.Object` la matrice di parametri con il tipo di elemento, il codice client può passare valori di qualsiasi tipo.</span><span class="sxs-lookup"><span data-stu-id="12319-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="12319-185">In F , le matrici di parametri possono essere definite solo nei metodi.</span><span class="sxs-lookup"><span data-stu-id="12319-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="12319-186">Non possono essere utilizzati in funzioni autonome o funzioni definite nei moduli.</span><span class="sxs-lookup"><span data-stu-id="12319-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="12319-187">Per definire una matrice `ParamArray` di parametri, utilizzare l'attributo .</span><span class="sxs-lookup"><span data-stu-id="12319-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="12319-188">L'attributo `ParamArray` può essere applicato solo all'ultimo parametro.</span><span class="sxs-lookup"><span data-stu-id="12319-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="12319-189">Nel codice riportato di seguito viene illustrata la chiamata a un metodo .NET che accetta una matrice di parametri e la definizione di un tipo in F , che dispone di un metodo che accetta una matrice di parametri.</span><span class="sxs-lookup"><span data-stu-id="12319-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="12319-190">Quando viene eseguito in un progetto, l'output del codice precedente è il seguente:</span><span class="sxs-lookup"><span data-stu-id="12319-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="12319-191">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="12319-191">See also</span></span>

- [<span data-ttu-id="12319-192">Membri</span><span class="sxs-lookup"><span data-stu-id="12319-192">Members</span></span>](./members/index.md)
