---
title: Tipo di dati SByte
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: 01a0a4a261213d7e6e2016bf49128092e5b22308
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400792"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="af490-102">SByte data type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af490-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="af490-103">Contiene interi con segno a 8 bit (1 byte) compresi in un valore compreso tra -128 e 127.</span><span class="sxs-lookup"><span data-stu-id="af490-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="af490-104">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="af490-104">Remarks</span></span>

<span data-ttu-id="af490-105">Utilizzare `SByte` il tipo di dati per contenere valori `Integer` integer che non richiedono `Short`l'intera larghezza dei dati o anche la metà della larghezza dei dati di .</span><span class="sxs-lookup"><span data-stu-id="af490-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="af490-106">In alcuni casi, Common Language Runtime potrebbe `SByte` essere in grado di comprimere le variabili strettamente insieme e risparmiare il consumo di memoria.</span><span class="sxs-lookup"><span data-stu-id="af490-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="af490-107">Il valore predefinito di `SByte` è 0.</span><span class="sxs-lookup"><span data-stu-id="af490-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="af490-108">Assegnazioni letterali</span><span class="sxs-lookup"><span data-stu-id="af490-108">Literal assignments</span></span>

<span data-ttu-id="af490-109">È possibile dichiarare `SByte` e inizializzare una variabile assegnandole un valore letterale decimale, un valore letterale esadecimale, un valore letterale ottale o (a partire da Visual Basic 2017) un valore letterale binario.</span><span class="sxs-lookup"><span data-stu-id="af490-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="af490-110">Nell'esempio seguente, i numeri interi uguali a -102 rappresentati come valori letterali decimali, esadecimali e binari vengono assegnati ai `SByte` valori.</span><span class="sxs-lookup"><span data-stu-id="af490-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="af490-111">Questo esempio richiede la `/removeintchecks` compilazione con l'opzione del compilatore.</span><span class="sxs-lookup"><span data-stu-id="af490-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="af490-112">Utilizzare il `&h` `&H` prefisso o per indicare un valore `&b` `&B` letterale esadecimale, il prefisso o per indicare un valore letterale binario e il prefisso `&o` o `&O` per indicare un valore letterale ottale.</span><span class="sxs-lookup"><span data-stu-id="af490-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="af490-113">I valori letterali decimali non hanno prefissi.</span><span class="sxs-lookup"><span data-stu-id="af490-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="af490-114">A partire da Visual Basic 2017, è `_`anche possibile utilizzare il carattere di sottolineatura, , come separatore di cifre per migliorare la leggibilità, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="af490-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="af490-115">A partire da Visual Basic 15.5, è`_`inoltre possibile utilizzare il carattere di sottolineatura ( ) come separatore iniziale tra il prefisso e le cifre esadecimali, binarie o ottali.</span><span class="sxs-lookup"><span data-stu-id="af490-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="af490-116">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="af490-116">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="af490-117">Se il valore letterale integer è esterno all'intervallo di `SByte`, vale a dire se è minore di <xref:System.SByte.MinValue?displayProperty=nameWithType> o maggiore di <xref:System.SByte.MaxValue?displayProperty=nameWithType>, si verifica un errore di compilazione.</span><span class="sxs-lookup"><span data-stu-id="af490-117">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="af490-118">Quando un valore letterale integer non ha alcun suffisso, viene dedotto un [Integer.When](integer-data-type.md) an integer literal has no suffix, an Integer is inferred.</span><span class="sxs-lookup"><span data-stu-id="af490-118">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="af490-119">Se il valore letterale integer `Integer` non è compreso nell'intervallo del tipo, viene dedotto [un valore Long.](long-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="af490-119">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="af490-120">Ciò significa che, negli esempi precedenti, `0b10011010` i valori letterali numerici e vengono interpretati <xref:System.SByte.MaxValue?displayProperty=nameWithType> `0x9A` come interi con segno a 32 bit con un valore di 156, che supera .</span><span class="sxs-lookup"><span data-stu-id="af490-120">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="af490-121">Per compilare correttamente codice come questo che `SByte`assegna un numero intero non decimale a un oggetto , è possibile effettuare una delle seguenti operazioni:</span><span class="sxs-lookup"><span data-stu-id="af490-121">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="af490-122">Disabilitare i controlli dei limiti `/removeintchecks` integer eseguendo la compilazione con l'opzione del compilatore.</span><span class="sxs-lookup"><span data-stu-id="af490-122">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="af490-123">Utilizzare un [carattere tipo](../../programming-guide/language-features/data-types/type-characters.md) per definire in modo `SByte`esplicito il valore letterale che si desidera assegnare all'oggetto .</span><span class="sxs-lookup"><span data-stu-id="af490-123">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="af490-124">Nell'esempio seguente viene `Short` assegnato un `SByte`valore letterale negativo a un oggetto .</span><span class="sxs-lookup"><span data-stu-id="af490-124">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="af490-125">Si noti che, per i numeri negativi, è necessario impostare il bit più in ordine della parola più in ordine superiore del valore letterale numerico.</span><span class="sxs-lookup"><span data-stu-id="af490-125">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="af490-126">Nel caso del nostro esempio, questo è `Short` il bit 15 del valore letterale.</span><span class="sxs-lookup"><span data-stu-id="af490-126">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="af490-127">Suggerimenti per la programmazione</span><span class="sxs-lookup"><span data-stu-id="af490-127">Programming tips</span></span>

- <span data-ttu-id="af490-128">**Conformità a CLS.**</span><span class="sxs-lookup"><span data-stu-id="af490-128">**CLS Compliance.**</span></span> <span data-ttu-id="af490-129">Il `SByte` tipo di dati non fa parte di [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), pertanto il codice conforme a CLS non può utilizzare un componente che lo utilizza.</span><span class="sxs-lookup"><span data-stu-id="af490-129">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="af490-130">**Ampliamento.**</span><span class="sxs-lookup"><span data-stu-id="af490-130">**Widening.**</span></span> <span data-ttu-id="af490-131">Il `SByte` tipo di `Short`dati `Integer` `Long`si `Decimal` `Single`allarga `Double`a , , , , e .</span><span class="sxs-lookup"><span data-stu-id="af490-131">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="af490-132">Ciò significa `SByte` che è possibile eseguire la <xref:System.OverflowException?displayProperty=nameWithType> conversione in uno qualsiasi di questi tipi senza che si verifichi un errore.</span><span class="sxs-lookup"><span data-stu-id="af490-132">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="af490-133">**Digitare caratteri.**</span><span class="sxs-lookup"><span data-stu-id="af490-133">**Type Characters.**</span></span> <span data-ttu-id="af490-134">`SByte`non dispone di alcun carattere di tipo letterale o tipo di identificatore.</span><span class="sxs-lookup"><span data-stu-id="af490-134">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="af490-135">**Tipo di framework.**</span><span class="sxs-lookup"><span data-stu-id="af490-135">**Framework Type.**</span></span> <span data-ttu-id="af490-136">Il tipo corrispondente in .NET Framework è la struttura <xref:System.SByte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="af490-136">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="af490-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="af490-137">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="af490-138">Tipi di dati</span><span class="sxs-lookup"><span data-stu-id="af490-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="af490-139">Funzioni di conversione del tipo</span><span class="sxs-lookup"><span data-stu-id="af490-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="af490-140">Riepilogo della conversione</span><span class="sxs-lookup"><span data-stu-id="af490-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="af490-141">Tipo di dati Short</span><span class="sxs-lookup"><span data-stu-id="af490-141">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)
- [<span data-ttu-id="af490-142">Tipo di dati IntegerInteger Data Type</span><span class="sxs-lookup"><span data-stu-id="af490-142">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="af490-143">Tipo di dati Long</span><span class="sxs-lookup"><span data-stu-id="af490-143">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="af490-144">Utilizzo efficiente dei tipi di dati</span><span class="sxs-lookup"><span data-stu-id="af490-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
