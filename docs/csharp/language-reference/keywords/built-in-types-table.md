---
title: Tabella dei tipi predefiniti - Riferimenti per C#
description: Parole chiave per i tipi C# incorporati
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: f26da848d58426472d2c2ab755ecadfd267b096a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734478"
---
# <a name="built-in-types-table-c-reference"></a>Tabella dei tipi incorporati (Riferimenti per C#)

Nella tabella seguente vengono illustrate le parole chiave per C# i tipi incorporati, ovvero alias di tipi predefiniti nello spazio dei nomi <xref:System>:

|Tipo C#|Tipo .NET|  
|--------------|-------------------------|  
|[bool](../builtin-types/bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](../builtin-types/integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](../builtin-types/integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](../builtin-types/char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](../builtin-types/floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](../builtin-types/floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](../builtin-types/floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](../builtin-types/integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](../builtin-types/integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](../builtin-types/integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](../builtin-types/integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](../builtin-types/reference-types.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](../builtin-types/integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](../builtin-types/integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](../builtin-types/reference-types.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Note

Tutti i tipi nella tabella, ad eccezione di `object` e `string`, sono detti tipi semplici.

I tipi .NET e i relativi alias per le parole chiave per i tipi C# sono intercambiabili. Ad esempio, è possibile dichiarare una variabile integer, usando le seguenti dichiarazioni:

```csharp
int x = 123;
System.Int32 y = 123;
```

Usare l'operatore [typeof](../operators/type-testing-and-cast.md#typeof-operator) per ottenere l'istanza <xref:System.Type?displayProperty=nameWithType> che rappresenta il tipo specificato:

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a>Vedere anche

- [Riferimenti per C#](../index.md)
- [Parole chiave di C#](index.md)
- [Tipi di valore](../builtin-types/value-types.md)
- [Tipi riferimento](reference-types.md)
- [Valori predefiniti dei C# tipi](../builtin-types/default-values.md)
- [dynamic](../builtin-types/reference-types.md#the-dynamic-type)
