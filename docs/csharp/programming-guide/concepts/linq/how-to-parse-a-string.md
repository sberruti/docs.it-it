---
title: Come analizzare una stringa (C )How to parse a string (C
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 79821eb9e5cd7187ac3c2a93f85eaae45c5c48ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345804"
---
# <a name="how-to-parse-a-string-c"></a>Come analizzare una stringa (C )How to parse a string (C

Questo argomento illustra come analizzare una stringa per creare una struttura ad albero XML in C#.

## <a name="example"></a>Esempio

Il seguente codice in c'è viene illustrato come analizzare una stringa XML:The following C's code shows how to parse an XML string:

```csharp
XElement contacts = XElement.Parse(
    @"<Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type=""home"">206-555-0144</Phone>
            <Phone Type=""work"">425-555-0145</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>10</NetWorth>
        </Contact>
        <Contact>
            <Name>Gretchen Rivas</Name>
            <Phone Type=""mobile"">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>");
Console.WriteLine(contacts);
```

Il `Contacts` nodo radice `Contact` ha due nodi. Per accedere ad alcuni dati specifici nel codice XML analizzato, utilizzate il metodo [XElement.Elements(),](xref:System.Xml.Linq.XContainer.Elements) che in questo caso restituisce gli elementi figlio del nodo radice. `Contacts` L'esempio seguente stampa `Contact` il primo nodo nella console:

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a>Vedere anche

- [Come trovare un elemento con un attributo specifico (c'è)How to find an element with a specific attribute (C](how-to-find-an-element-with-a-specific-attribute.md)
