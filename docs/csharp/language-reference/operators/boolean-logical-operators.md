---
title: Operatori logici booleani - Riferimenti per C#
description: Informazioni sugli operatori C# che eseguono operazioni logiche di negazione, congiunzione (AND) e disgiunzione inclusiva ed esclusiva (OR) con operandi booleani.
ms.date: 09/27/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: 930329b922f585ac4763e6a66d3b192ae839f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399497"
---
# <a name="boolean-logical-operators-c-reference"></a>Operatori logici booleani (Riferimenti per C#)

Gli operatori seguenti eseguono operazioni logiche con gli operandi [bool:](../builtin-types/bool.md)

- Operatore unario [ `!` (negazione logica).](#logical-negation-operator-)
- Binary [ `&` (LOGICAL AND)](#logical-and-operator-), [ `|` (OR logico)](#logical-or-operator-)e [ `^` (OR esclusivo logico).](#logical-exclusive-or-operator-) Questi operatori valutano sempre entrambi gli operandi.
- Operatori binari [ `&&` (AND logici condizionali)](#conditional-logical-and-operator-) e [ `||` (OR logico condizionale).](#conditional-logical-or-operator-) Questi operatori valutano l'operando di destra solo se è necessario.

Per gli operandi dei tipi `&` `|` [numerici integrali](../builtin-types/integral-numeric-types.md), gli operatori , e `^` eseguono operazioni logiche bit per bit. Per altre informazioni, vedere [Operatori di scorrimento e bit per bit](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Operatore di negazione logica !

L'operatore `!` del prefisso unario calcola la negazione logica dell'operando. Vale a dire, produce `true` se l'operando restituisce `false` e `false` se l'operando restituisce `true`:

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

A partire dalla versione 8.0 di `!` C, l'operatore suffisso unario è l'operatore di [perdono null](null-forgiving.md).

## <a name="logical-and-operator-"></a>Operatore logico AND&amp;

L'operatore `&` calcola l'AND logico dei relativi operandi. Il risultato di `x & y` è `true` se `x` e `y` restituiscono `true`. In caso contrario, il risultato è `false`.

L'operatore `&` valuta entrambi gli operandi anche se l'operando di sinistra restituisce `false`, in modo che il risultato dell'operazione sia `false` indipendentemente dal valore dell'operando di destra.

Nell'esempio seguente l'operando di destra dell'operatore `&` è una chiamata a un metodo, che viene eseguita indipendentemente dal valore dell'operando di sinistra:

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

L'[operatore AND condizionale logico](#conditional-logical-and-operator-) `&&` calcola anche l'AND logico dei relativi operandi, ma non valuta l'operando di destra se l'operando di sinistra restituisce `false`.

Per gli operandi dei tipi `&` [numerici integrali,](../builtin-types/integral-numeric-types.md)l'operatore calcola l'operatore logico bit per [bit](bitwise-and-shift-operators.md#logical-and-operator-) dei relativi operandi. L'operatore unario `&` è l'[operatore address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Operatore OR esclusivo logico: ^

L'operatore `^` calcola l'OR esclusivo logico, noto anche come XOR logico, dei relativi operandi. Il risultato di `x ^ y` è `true` se `x` restituisce `true` e `y` restituisce `false` oppure `x` restituisce `false` e `y` restituisce `true`. In caso contrario, il risultato è `false`. Vale a dire, per gli operandi `bool`, l'operatore `^` calcola lo stesso risultato dell'[operatore di disuguaglianza](equality-operators.md#inequality-operator-) `!=`.

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

Per gli operandi dei tipi `^` [numerici integrali,](../builtin-types/integral-numeric-types.md)l'operatore calcola l'operatore logico bit per bit [orendo](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) degli operandi.

## <a name="logical-or-operator-"></a>Operatore OR logico |

L'operatore `|` calcola l'OR logico dei relativi operandi. Il risultato di `x | y` è `true` se `x` o `y` restituisce `true`. In caso contrario, il risultato è `false`.

L'operatore `|` valuta entrambi gli operandi anche se l'operando di sinistra restituisce `true`, in modo che il risultato dell'operazione sia `true` indipendentemente dal valore dell'operando di destra.

Nell'esempio seguente l'operando di destra dell'operatore `|` è una chiamata a un metodo, che viene eseguita indipendentemente dal valore dell'operando di sinistra:

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

L'[operatore OR condizionale logico](#conditional-logical-or-operator-) `||` calcola anche l'OR logico dei relativi operandi, ma non valuta l'operando di destra se l'operando di sinistra restituisce `true`.

Per gli operandi dei tipi `|` [numerici integrali,](../builtin-types/integral-numeric-types.md)l'operatore calcola l'operatore logico bit per [bit](bitwise-and-shift-operators.md#logical-or-operator-) dei relativi operandi.

## <a name="conditional-logical-and-operator-"></a>Operatore AND logico condizionale&amp;&amp;

L'operatore AND condizionale logico `&&`, chiamato anche operatore AND logico di "corto circuito", calcola l'AND logico dei relativi operandi. Il risultato di `x && y` è `true` se `x` e `y` restituiscono `true`. In caso contrario, il risultato è `false`. Se `x` è `false`, `y` non viene valutato.

Nell'esempio seguente l'operando di destra dell'operatore `&&` è una chiamata a un metodo, che non viene eseguita se l'operando di sinistra restituisce `false`:

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

[L'operatore logico AND](#logical-and-operator-) `&` calcola anche l'operatore logico AND degli operandi, ma valuta sempre entrambi gli operandi.

## <a name="conditional-logical-or-operator-"></a>Operatore OR condizionale logico ||

L'operatore OR condizionale logico `||`, chiamato anche operatore OR logico di "corto circuito", calcola l'OR logico dei relativi operandi. Il risultato di `x || y` è `true` se `x` o `y` restituisce `true`. In caso contrario, il risultato è `false`. Se `x` è `true`, `y` non viene valutato.

Nell'esempio seguente l'operando di destra dell'operatore `||` è una chiamata a un metodo, che non viene eseguita se l'operando di sinistra restituisce `true`:

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

[L'operatore](#logical-or-operator-) `|` logico OR calcola anche l'OR logico degli operandi, ma valuta sempre entrambi gli operandi.

## <a name="nullable-boolean-logical-operators"></a>Operatori logici booleani nullable

Per `bool?` gli operandi, gli `&` operatori e `|` supportano la logica a tre valori. La semantica di questi operatori è definita dalla tabella seguente:  
  
|x|y|x&y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|false|false|true|  
|true|Null|Null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|Null|false|Null|  
|Null|true|Null|true|  
|Null|false|false|Null|  
|Null|Null|Null|Null|  

Il comportamento di questi operatori è diverso dal comportamento tipico degli operatori con tipi valore nullable. In genere un operatore definito per gli operandi di un tipo valore può essere usato anche con gli operandi del tipo valore nullable corrispondente. Tale operatore `null` produce se uno dei relativi `null`operandi restituisce . Tuttavia, `&` `|` gli operatori e possono produrre non null anche se `null`uno degli operandi restituisce . Per altre informazioni sul comportamento dell'operatore con tipi di valore nullable, vedere la sezione [Operatori sollevati](../builtin-types/nullable-value-types.md#lifted-operators) dell'articolo [Tipi di valore nullable.](../builtin-types/nullable-value-types.md)

È inoltre possibile `!` `^` utilizzare `bool?` gli operatori e con gli operandi, come illustrato nell'esempio seguente:You can also use the and operators with operands, as the following example shows:

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

Gli operatori `&&` logici condizionali e `||` non supportano `bool?` gli operandi.

## <a name="compound-assignment"></a>Assegnazione composta

Per un operatore binario `op`, un'espressione di assegnazione composta in formato

```csharp
x op= y
```

equivale a

```csharp
x = x op y
```

con la differenza che `x` viene valutato una sola volta.

Gli operatori `&`, `|` e `^` supportano l'assegnazione composta, come illustrato nell'esempio seguente:

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

Gli operatori condizionali logici `&&` e `||` non supportano l'assegnazione composta.

## <a name="operator-precedence"></a>Precedenza degli operatori

Nell'elenco seguente gli operatori logici sono ordinati dalla precedenza più elevata a quella più bassa:

- Operatore di negazione logica `!`
- Operatore AND logico `&`
- Operatore OR esclusivo logico `^`
- Operatore OR logico `|`
- Operatore AND condizionale logico `&&`
- Operatore OR condizionale logico `||`

Usare le parentesi, `()`, per cambiare l'ordine di valutazione imposto dalla precedenza tra gli operatori:

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

Per l'elenco completo degli operatori di C, ordinati in base al livello di precedenza, vedere la sezione [Precedenza](index.md#operator-precedence) degli operatori dell'articolo Operatori di [C.](index.md)

## <a name="operator-overloadability"></a>Overload degli operatori

Un tipo definito dall'utente `&` `|`può `^` [eseguire l'overload](operator-overloading.md) degli `!`operatori , , e . Quando viene eseguito l'overload di un operatore binario, viene anche eseguito in modo implicito l'overload dell'operatore di assegnazione composta corrispondente. Un tipo definito dall'utente non può eseguire in modo esplicito l'overload di un operatore di assegnazione composta.

Un tipo definito dall'utente non può eseguire l'overload degli operatori condizionali logici `&&` e `||`. Tuttavia, se un tipo definito dall'utente esegue l'overload degli [operatori true e false](true-false-operators.md) e dell'operatore `&` o `|` in un determinato modo, l'operazione `&&` o `||` può essere valutata per gli operandi di quel tipo. Per altre informazioni, vedere la sezione [Operatori logici condizionali definiti dall'utente](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) di [Specifica del linguaggio C#](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>Specifiche del linguaggio C#

Per altre informazioni, vedere le sezioni seguenti delle [specifiche del linguaggio C#](~/_csharplang/spec/introduction.md):

- [Operatore di negazione logica](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Operatori logici](~/_csharplang/spec/expressions.md#logical-operators)
- [Operatori logici condizionali](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Assegnazione composta](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento su C#](../index.md)
- [Operatori C#](index.md)
- [Operatori di spostamento e bit per bit](bitwise-and-shift-operators.md)
