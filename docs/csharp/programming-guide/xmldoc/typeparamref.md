---
title: <typeparamref>- Guida alla programmazione in C
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789655"
---
# <a name="typeparamref-c-programming-guide"></a>\<> di typeparamref (Guida per programmatori C

## <a name="syntax"></a>Sintassi

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Parametri

- `name`

  Nome del parametro di tipo. Racchiudere il nome tra virgolette doppie (" ").

## <a name="remarks"></a>Osservazioni

Per altre informazioni sui parametri di tipo in tipi e metodi generici, vedere [Generics](../generics/index.md).

Usare questo tag per consentire ai consumer del file di documentazione di formattare la parola in un modo specifico, ad esempio in corsivo.

Compilare con [-doc](../../language-reference/compiler-options/doc-compiler-option.md) per elaborare i commenti relativi alla documentazione in un file.

## <a name="example"></a>Esempio

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Vedere anche

- [Guida alla programmazione in C](../index.md)
- [Tag consigliati per i commenti relativi alla documentazione](./recommended-tags-for-documentation-comments.md)
