---
title: Istruzioni C# - Panoramica del linguaggio C#
description: Le azioni di un programma C# vengono create mediante istruzioni
ms.date: 02/27/2020
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: ced13b1bfd17977acb98bf33c0a477161cf08a93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159104"
---
# <a name="statements"></a>Istruzioni

Le azioni di un programma vengono espresse mediante *istruzioni*. C# supporta numerosi tipi di istruzioni, alcune delle quali sono definite in termini di istruzioni nidificate.

Un *blocco* consente di scrivere più istruzioni nei contesti in cui ne è consentita una sola. Un blocco è costituito da un elenco di istruzioni scritte tra i delimitatori `{` e `}`.

Le *istruzioni di dichiarazione* vengono usate per dichiarare le costanti e le variabili locali.

Le *istruzioni di espressione* vengono usate per valutare le espressioni. Le espressioni che possono essere usate come istruzioni includono le chiamate ai metodi, le allocazioni di oggetti mediante l'operatore `new`, le assegnazioni mediante `=` e gli operatori di assegnazione composta, le operazioni di incremento e decremento mediante gli operatori `++` e `--` e le espressioni `await`.

Le *istruzioni di selezione* vengono usate per selezionare una tra più istruzioni che è possibile eseguire sulla base del valore di alcune espressioni. Questo gruppo `if` contiene `switch` le istruzioni e .

Le *istruzioni di iterazione* vengono usate per eseguire più volte un'istruzione nidificata. Questo gruppo `while`contiene `do` `for`le `foreach` istruzioni , , e .

Le *istruzioni di spostamento* vengono usate per trasferire il controllo. Questo gruppo `break`contiene `continue` `goto`le `throw` `return`istruzioni `yield` , , , , e .

L'istruzione `try`...`catch` viene usata per rilevare le eccezioni che si verificano durante l'esecuzione di un blocco, mentre l'istruzione `try`...`finally` viene usata per specificare il codice di finalizzazione che viene eseguito sempre, indipendentemente dal fatto che si sia verificata un'eccezione.

Le istruzioni `checked` e `unchecked` vengono usate per verificare il contesto di controllo dell'overflow per le conversioni e le operazioni aritmetiche di tipo integrale.

L'istruzione `lock` viene usata per ottenere il blocco a esclusione reciproca per un oggetto specificato, eseguire un'istruzione e quindi rilasciare il blocco.

L'istruzione `using` viene usata per ottenere una risorsa, eseguire un'istruzione e quindi eliminare la risorsa.

Di seguito vengono elencati i tipi di istruzione che è possibile usare e viene offerto un esempio di ciascuna.

* Dichiarazione di variabile locale:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* Dichiarazione di costante locale:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* Istruzione di espressione:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* Istruzione `if`:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* Istruzione `switch`:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* Istruzione `while`:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* Istruzione `do`:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* Istruzione `for`:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* Istruzione `foreach`:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* Istruzione `break`:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* Istruzione `continue`:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* Istruzione `goto`:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* Istruzione `return`:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* Istruzione `yield`:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* Istruzioni `throw` e istruzioni `try`:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* Istruzioni `checked` e `unchecked`:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* Istruzione `lock`:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* Istruzione `using`:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
>[Successivo](expressions.md)
>[precedente](classes-and-objects.md)
