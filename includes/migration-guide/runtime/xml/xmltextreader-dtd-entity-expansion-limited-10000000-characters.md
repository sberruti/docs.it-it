---
ms.openlocfilehash: 1f5bc43dcba15c28c179b23352558411f511c82f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235615"
---
### <a name="xmltextreader-dtd-entity-expansion-is-limited-to-10000000-characters"></a>L'espansione XmlTextReader dell'entità DTD è limitata a 10.000.000 di caratteri

|   |   |
|---|---|
|Dettagli|L'espansione dell'entità DTD è ora limitata a 10.000.000 di caratteri. Il caricamento di file XML senza espansione o con espansione limitata dell'entità DTD non è interessato dall'operazione. I file con entità DTD che si espandono oltre 10.000.000 di caratteri non vengono caricati e generano un'eccezione.|
|Suggerimento|Se il limite di espansione dell'entità DTD di 10.000.000 è troppo basso, il valore può essere sostituito con la proprietà <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities>. Un oggetto <xref:System.Xml.XmlReaderSettings?displayProperty=name> con il valore <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=name> appropriato può essere passato a <code>XmlReader.Create</code> che accetta <xref:System.Xml.XmlReaderSettings?displayProperty=name> (ad esempio <xref:System.Xml.XmlReader.Create(System.String,System.Xml.XmlReaderSettings)>)|
|Ambito|Microsoft Edge|
|Versione|4.5|
|Tipo|Runtime|
|API interessate|<ul><li><xref:System.Xml.XmlTextReader?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.Stream,System.Xml.XmlNodeType,System.Xml.XmlParserContext)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.IO.TextReader,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.Stream,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.IO.TextReader,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNameTable)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.String,System.Xml.XmlNodeType,System.Xml.XmlParserContext)?displayProperty=nameWithType></li><li><xref:System.Xml.XmlTextReader.%23ctor(System.Xml.XmlNameTable)?displayProperty=nameWithType></li></ul>|
