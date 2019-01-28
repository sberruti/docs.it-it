---
title: Private Protected (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 70f725712d52ad055ff69046096da10b8edfb67c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701144"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="0e2b3-102">Private Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e2b3-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="0e2b3-103">La combinazione delle parole chiave `Private Protected` è un modificatore di accesso ai membri.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="0e2b3-104">Oggetto `Private Protected` membro è accessibile da tutti i membri nella classe che contiene, nonché per i tipi derivati dalla classe che contiene, ma solo se vengono trovati nell'assembly che lo contiene.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span> 

<span data-ttu-id="0e2b3-105">È possibile specificare `Private Protected` solo in membri di classi; non è possibile applicare `Private Protected` ai membri di una struttura perché le strutture non possono essere ereditate.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="0e2b3-106">Il `Private Protected` modificatore di accesso è supportato da Visual Basic 15.5 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="0e2b3-107">Per usarla, è possibile aggiungere l'elemento seguente al progetto Visual Basic (\*vbproj) file.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="0e2b3-108">Tempo come Visual Basic 15.5 o versione successiva è installato nel sistema, consente di sfruttare i vantaggi di tutte le funzionalità di linguaggio supportati dalla versione più recente del compilatore Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="0e2b3-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="0e2b3-109">Per altre informazioni, vedere [impostando la versione del linguaggio Visual Basic](../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="0e2b3-109">For more information see [setting the Visual Basic language version](../../language-reference/configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0e2b3-110">In Visual Studio, selezionare la Guida F1 nei `private protected` vengono fornite informazioni per una [privati](private.md) oppure [protetto](protected.md).</span><span class="sxs-lookup"><span data-stu-id="0e2b3-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="0e2b3-111">L'IDE sceglie il token single sotto il cursore anziché la parola composta.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="0e2b3-112">Regole</span><span class="sxs-lookup"><span data-stu-id="0e2b3-112">Rules</span></span>

- <span data-ttu-id="0e2b3-113">**Contesto della dichiarazione.**</span><span class="sxs-lookup"><span data-stu-id="0e2b3-113">**Declaration Context.**</span></span> <span data-ttu-id="0e2b3-114">È possibile usare `Private Protected` solo a livello di classe.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="0e2b3-115">Ciò significa che il contesto della dichiarazione per un `Protected` elemento deve essere una classe e non può essere un file di origine, lo spazio dei nomi, interfaccia, modulo, struttura o procedure.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="0e2b3-116">Comportamento</span><span class="sxs-lookup"><span data-stu-id="0e2b3-116">Behavior</span></span>

- <span data-ttu-id="0e2b3-117">**Livello di accesso.**</span><span class="sxs-lookup"><span data-stu-id="0e2b3-117">**Access Level.**</span></span> <span data-ttu-id="0e2b3-118">Tutto il codice in una classe possa accedere ai relativi elementi.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-118">All code in a class can access its elements.</span></span> <span data-ttu-id="0e2b3-119">Codice in qualsiasi classe che deriva da una classe base ed è contenuta nello stesso assembly possa accedere a tutte le `Private Protected` gli elementi della classe di base.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="0e2b3-120">Tuttavia il codice in qualsiasi classe che deriva da una classe base ed è contenuta in un assembly diverso non può accedere la classe di base `Private Protected` elementi.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="0e2b3-121">**Modificatori di accesso.**</span><span class="sxs-lookup"><span data-stu-id="0e2b3-121">**Access Modifiers.**</span></span> <span data-ttu-id="0e2b3-122">Le parole chiave che specificano il livello di accesso vengono chiamate *modificatori di accesso*.</span><span class="sxs-lookup"><span data-stu-id="0e2b3-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="0e2b3-123">Per un confronto tra i modificatori di accesso, vedere [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0e2b3-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>
  
 <span data-ttu-id="0e2b3-124">Il modificatore `Private Protected` può essere usato nei contesti seguenti:</span><span class="sxs-lookup"><span data-stu-id="0e2b3-124">The `Private Protected` modifier can be used in these contexts:</span></span>  
  
 <span data-ttu-id="0e2b3-125">[Istruzione Class](../../../visual-basic/language-reference/statements/class-statement.md) di una classe annidata</span><span class="sxs-lookup"><span data-stu-id="0e2b3-125">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) of a nested class</span></span>  
  
 [<span data-ttu-id="0e2b3-126">Istruzione Const</span><span class="sxs-lookup"><span data-stu-id="0e2b3-126">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="0e2b3-127">Istruzione Declare</span><span class="sxs-lookup"><span data-stu-id="0e2b3-127">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="0e2b3-128">[Istruzione Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) di un delegato annidata in una classe</span><span class="sxs-lookup"><span data-stu-id="0e2b3-128">[Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) of a delegate nested in a class</span></span>  
  
 [<span data-ttu-id="0e2b3-129">Istruzione Dim</span><span class="sxs-lookup"><span data-stu-id="0e2b3-129">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 <span data-ttu-id="0e2b3-130">[Istruzione Enum](../../../visual-basic/language-reference/statements/enum-statement.md) di un eumeration annidata in una classe</span><span class="sxs-lookup"><span data-stu-id="0e2b3-130">[Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) of an eumeration nested in a class</span></span> 
  
 [<span data-ttu-id="0e2b3-131">Istruzione Event</span><span class="sxs-lookup"><span data-stu-id="0e2b3-131">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="0e2b3-132">Istruzione Function</span><span class="sxs-lookup"><span data-stu-id="0e2b3-132">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 <span data-ttu-id="0e2b3-133">[Istruzione Interface](../../../visual-basic/language-reference/statements/interface-statement.md) di un'interfaccia è annidata in una classe</span><span class="sxs-lookup"><span data-stu-id="0e2b3-133">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) of an interface nested in a class</span></span> 
  
 [<span data-ttu-id="0e2b3-134">Istruzione Property</span><span class="sxs-lookup"><span data-stu-id="0e2b3-134">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 <span data-ttu-id="0e2b3-135">[Struttura istruzione](../../../visual-basic/language-reference/statements/structure-statement.md) di una struttura annidata in una classe</span><span class="sxs-lookup"><span data-stu-id="0e2b3-135">[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) of a structure nested in a class</span></span> 
  
 [<span data-ttu-id="0e2b3-136">Istruzione Sub</span><span class="sxs-lookup"><span data-stu-id="0e2b3-136">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="0e2b3-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0e2b3-137">See also</span></span>

- [<span data-ttu-id="0e2b3-138">Public</span><span class="sxs-lookup"><span data-stu-id="0e2b3-138">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="0e2b3-139">Protected</span><span class="sxs-lookup"><span data-stu-id="0e2b3-139">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="0e2b3-140">Friend</span><span class="sxs-lookup"><span data-stu-id="0e2b3-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="0e2b3-141">Private</span><span class="sxs-lookup"><span data-stu-id="0e2b3-141">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="0e2b3-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="0e2b3-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="0e2b3-143">Livelli di accesso in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0e2b3-143">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="0e2b3-144">Routine</span><span class="sxs-lookup"><span data-stu-id="0e2b3-144">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="0e2b3-145">Strutture</span><span class="sxs-lookup"><span data-stu-id="0e2b3-145">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0e2b3-146">Oggetti e classi</span><span class="sxs-lookup"><span data-stu-id="0e2b3-146">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)