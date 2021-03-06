---
title: 'Procedura: Rimuovere caratteri non validi da una stringa'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
ms.openlocfilehash: cc90e6609f9335b7e2f08271e5540b182901e8c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127645"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a>Procedura: Rimuovere caratteri non validi da una stringa
L'esempio seguente usa il metodo statico <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> per rimuovere i caratteri non validi da una stringa.  
  
## <a name="example"></a>Esempio  
 È possibile usare il metodo `CleanInput` definito in questo esempio per rimuovere i caratteri potenzialmente dannosi che sono stati inseriti in un campo di testo che accetta l'input dell'utente. In questo caso, `CleanInput` rimuove tutti i caratteri non alfanumerici tranne punto (.), simboli "at" (@) e trattini (-) e restituisce la stringa restante. È tuttavia possibile modificare l'espressione regolare in modo che rimuova i caratteri che non devono essere inclusi in una stringa di input.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Il criterio di espressione regolare `[^\w\.@-]` corrisponde a qualsiasi carattere che non è un carattere alfanumerico, un punto, un simbolo @ o un trattino. Un carattere alfanumerico è qualsiasi lettera, numero decimale o connettore di punteggiatura, ad esempio un carattere di sottolineatura. Qualsiasi carattere che corrisponde a questo criterio viene sostituito da <xref:System.String.Empty?displayProperty=nameWithType>, ovvero la stringa definita dal criterio di sostituzione. Per consentire ulteriori caratteri nell'input dell'utente, aggiungere tali caratteri alla classe di caratteri nel criterio di espressione regolare. Ad esempio, il criterio di espressione regolare `[^\w\.@-\\%]` consente anche un simbolo di percentuale e una barra rovesciata in una stringa di input.  
  
## <a name="see-also"></a>Vedere anche

- [Espressioni regolari .NET](../../../docs/standard/base-types/regular-expressions.md)
