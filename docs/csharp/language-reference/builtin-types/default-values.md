---
title: Valori predefiniti dei C# tipi- C# Reference
description: Informazioni sui valori predefiniti dei C# tipi, ad esempio bool, Char, int, float, Double e altro.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 2447db25e837cdcd6d67847b8677d7d44da551a9
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964944"
---
# <a name="default-values-of-c-types-c-reference"></a><span data-ttu-id="68d5d-103">Valori predefiniti dei C# tipi (C# riferimento)</span><span class="sxs-lookup"><span data-stu-id="68d5d-103">Default values of C# types (C# reference)</span></span>

<span data-ttu-id="68d5d-104">La tabella seguente mostra i valori predefiniti dei tipi C#:</span><span class="sxs-lookup"><span data-stu-id="68d5d-104">The following table shows the default values of C# types:</span></span>

|<span data-ttu-id="68d5d-105">Tipo di</span><span class="sxs-lookup"><span data-stu-id="68d5d-105">Type</span></span>|<span data-ttu-id="68d5d-106">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="68d5d-106">Default value</span></span>|
|---------|------------------|
|<span data-ttu-id="68d5d-107">Qualsiasi tipo riferimento</span><span class="sxs-lookup"><span data-stu-id="68d5d-107">Any reference type</span></span>|`null`|
|<span data-ttu-id="68d5d-108">Qualsiasi [tipo numerico integrale incorporato](integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="68d5d-108">Any [built-in integral numeric type](integral-numeric-types.md)</span></span>|<span data-ttu-id="68d5d-109">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="68d5d-109">0 (zero)</span></span>|
|<span data-ttu-id="68d5d-110">Qualsiasi [tipo numerico a virgola mobile incorporato](floating-point-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="68d5d-110">Any [built-in floating-point numeric type](floating-point-numeric-types.md)</span></span>|<span data-ttu-id="68d5d-111">0 (zero)</span><span class="sxs-lookup"><span data-stu-id="68d5d-111">0 (zero)</span></span>|
|[<span data-ttu-id="68d5d-112">bool</span><span class="sxs-lookup"><span data-stu-id="68d5d-112">bool</span></span>](bool.md)|`false`|
|[<span data-ttu-id="68d5d-113">char</span><span class="sxs-lookup"><span data-stu-id="68d5d-113">char</span></span>](char.md)|<span data-ttu-id="68d5d-114">`'\0'` (U+0000)</span><span class="sxs-lookup"><span data-stu-id="68d5d-114">`'\0'` (U+0000)</span></span>|
|[<span data-ttu-id="68d5d-115">enum</span><span class="sxs-lookup"><span data-stu-id="68d5d-115">enum</span></span>](enum.md)|<span data-ttu-id="68d5d-116">Valore prodotto dall'espressione `(E)0`, dove `E` è l'identificatore di enumerazione.</span><span class="sxs-lookup"><span data-stu-id="68d5d-116">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="68d5d-117">struct</span><span class="sxs-lookup"><span data-stu-id="68d5d-117">struct</span></span>](../keywords/struct.md)|<span data-ttu-id="68d5d-118">Valore prodotto impostando tutti i campi dei tipi valore sui rispettivi valori predefiniti e tutti i campi dei tipi riferimento su `null`.</span><span class="sxs-lookup"><span data-stu-id="68d5d-118">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|<span data-ttu-id="68d5d-119">Qualsiasi [tipo valore nullable](nullable-value-types.md)</span><span class="sxs-lookup"><span data-stu-id="68d5d-119">Any [nullable value type](nullable-value-types.md)</span></span>|<span data-ttu-id="68d5d-120">Un'istanza per la quale la proprietà <xref:System.Nullable%601.HasValue%2A> è `false` e la proprietà <xref:System.Nullable%601.Value%2A> non è definita.</span><span class="sxs-lookup"><span data-stu-id="68d5d-120">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span> <span data-ttu-id="68d5d-121">Il valore predefinito è noto anche come valore *null* di un tipo di valore Nullable.</span><span class="sxs-lookup"><span data-stu-id="68d5d-121">That default value is also known as the *null* value of a nullable value type.</span></span>|

<span data-ttu-id="68d5d-122">Usare l'[operatore predefinito](../operators/default.md) per produrre il valore predefinito di un tipo, come illustrato nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="68d5d-122">Use the [default operator](../operators/default.md) to produce the default value of a type, as the following example shows:</span></span>

```csharp
int a = default(int);
```

<span data-ttu-id="68d5d-123">A partire da C# 7.1 è possibile usare il [ valore letterale `default`](../operators/default.md#default-literal) per inizializzare una variabile con il valore predefinito del relativo tipo:</span><span class="sxs-lookup"><span data-stu-id="68d5d-123">Beginning with C# 7.1, you can use the [`default` literal](../operators/default.md#default-literal) to initialize a variable with the default value of its type:</span></span>

```csharp
int a = default;
```

<span data-ttu-id="68d5d-124">Per un tipo valore, anche il costruttore senza parametri implicito produce il valore predefinito del tipo, come mostrato nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="68d5d-124">For a value type, the implicit parameterless constructor also produces the default value of the type, as the following example shows:</span></span>

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

<span data-ttu-id="68d5d-125">In fase di esecuzione, se l'istanza di <xref:System.Type?displayProperty=nameWithType> rappresenta un tipo di valore, è possibile usare il metodo <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> per richiamare il costruttore senza parametri per ottenere il valore predefinito del tipo.</span><span class="sxs-lookup"><span data-stu-id="68d5d-125">At run time, if the <xref:System.Type?displayProperty=nameWithType> instance represents a value type, you can use the <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> method to invoke the parameterless constructor to obtain the default value of the type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="68d5d-126">Specifiche del linguaggio C#</span><span class="sxs-lookup"><span data-stu-id="68d5d-126">C# language specification</span></span>

<span data-ttu-id="68d5d-127">Per altre informazioni, vedere le sezioni seguenti delle [specifiche del linguaggio C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="68d5d-127">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="68d5d-128">Valori predefiniti</span><span class="sxs-lookup"><span data-stu-id="68d5d-128">Default values</span></span>](~/_csharplang/spec/variables.md#default-values)
- [<span data-ttu-id="68d5d-129">Costruttori predefiniti</span><span class="sxs-lookup"><span data-stu-id="68d5d-129">Default constructors</span></span>](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a><span data-ttu-id="68d5d-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="68d5d-130">See also</span></span>

- [<span data-ttu-id="68d5d-131">Riferimenti per C#</span><span class="sxs-lookup"><span data-stu-id="68d5d-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="68d5d-132">Costruttori</span><span class="sxs-lookup"><span data-stu-id="68d5d-132">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)