---
title: Controllo di accesso
description: Informazioni su come controllare l'accesso agli elementi di programmazione, ad esempio tipi, metodi e funzioni, nel F# linguaggio di programmazione.
ms.date: 05/16/2016
ms.openlocfilehash: fe204a883a440794fdd033c54d6d8d4fb68e0ce2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425104"
---
# <a name="access-control"></a>Controllo di accesso

Il *controllo di accesso* si riferisce alla dichiarazione dei client che possono usare determinati elementi di programma, ad esempio tipi, metodi e funzioni.

## <a name="basics-of-access-control"></a>Nozioni di base sul controllo di accesso

In F#è possibile applicare gli identificatori di controllo di accesso `public`, `internal`e `private` a moduli, tipi, metodi, definizioni di valore, funzioni, proprietà e campi espliciti.

- `public` indica che l'entità può accedere a tutti i chiamanti.

- `internal` indica che è possibile accedere all'entità solo dallo stesso assembly.

- `private` indica che è possibile accedere all'entità solo dal tipo o dal modulo di inclusione.

> [!NOTE]
> L'identificatore di accesso `protected` non viene usato F#in, sebbene sia accettabile se si usano tipi creati in linguaggi che supportano `protected` l'accesso. Se pertanto si esegue l'override di un metodo protetto, il metodo rimane accessibile solo all'interno della classe e dei relativi discendenti.

In generale, l'identificatore viene inserito davanti al nome dell'entità, tranne quando viene usato un identificatore `mutable` o `inline`, che viene visualizzato dopo l'identificatore di controllo di accesso.

Se non viene usato alcun identificatore di accesso, il valore predefinito è `public`, ad eccezione dei binding `let` in un tipo, che sono sempre `private` al tipo.

Le firme F# in forniscono un altro meccanismo per controllare F# l'accesso agli elementi del programma. Le firme non sono necessarie per il controllo di accesso. Per altre informazioni, vedere [Firme](signature-files.md).

## <a name="rules-for-access-control"></a>Regole per il controllo di accesso

Il controllo di accesso è soggetto alle regole seguenti:

- Dichiarazioni di ereditarietà (ovvero l'uso di `inherit` per specificare una classe di base per una classe), dichiarazioni di interfaccia (ovvero specificando che una classe implementa un'interfaccia) e i membri astratti hanno sempre la stessa accessibilità del tipo di inclusione. Pertanto, non è possibile utilizzare un identificatore di controllo di accesso in questi costrutti.

- L'accessibilità per i singoli casi in un'unione discriminata è determinata dall'accessibilità dell'unione discriminata. Ovvero un particolare case di Unione non è meno accessibile dell'Unione stessa.

- L'accessibilità per i singoli campi di un tipo di record è determinata dall'accessibilità del record stesso. Ovvero, una particolare etichetta di record non è meno accessibile del record stesso.

## <a name="example"></a>Esempio

Il codice seguente illustra l'uso degli identificatori di controllo di accesso. Nel progetto sono presenti due file, `Module1.fs` e `Module2.fs`. Ogni file è implicitamente un modulo. Sono pertanto presenti due moduli, `Module1` e `Module2`. In `Module1`viene definito un tipo privato e un tipo interno. Non è possibile accedere al tipo privato dal `Module2`, ma il tipo interno può essere.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

Il codice seguente verifica l'accessibilità dei tipi creati in `Module1.fs`.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Vedere anche

- [Riferimenti per il linguaggio F#](index.md)
- [Firme](signature-files.md)
