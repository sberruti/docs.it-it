---
title: Convalida di XML Schema (XSD) con XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 6bd7525b77d4154193b57f8e6589cb865ace5fd6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709881"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a>Convalida di XML Schema (XSD) con XmlSchemaSet
È possibile eseguire la convalida di documenti XML rispetto a uno schema XSD (XML Schema Definition Language) usando un tipo <xref:System.Xml.Schema.XmlSchemaSet>.  
  
## <a name="validating-xml-documents"></a>Convalida di documenti XML  
 I documenti XML vengono convalidati mediante il metodo <xref:System.Xml.XmlReader.Create%2A> della classe <xref:System.Xml.XmlReader>. Per convalidare un documento XML è necessario costruire un oggetto <xref:System.Xml.XmlReaderSettings> che contenga uno schema XSD (XML Schema Definition Language) con il quale convalidare il documento XML.  
  
> [!NOTE]
> Lo spazio dei nomi <xref:System.Xml.Schema> contiene metodi di estensione che semplificano la convalida di un albero XML rispetto a un file XSD quando si usano [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) e [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md). Per ulteriori informazioni sulla convalida di documenti XML con LINQ to XML, vedere [How to Validate Using XSD (LINQ to XML)C#()](../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) e [How to: Validate Using XSD (LINQ to XML) (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md).
  
 È possibile aggiungere un singolo schema o un set di schemi (ad esempio <xref:System.Xml.Schema.XmlSchemaSet>) a un <xref:System.Xml.Schema.XmlSchemaSet> passandone uno come parametro al metodo <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> di <xref:System.Xml.Schema.XmlSchemaSet>. Durante la convalida di un documento lo spazio dei nomi di destinazione del documento deve corrispondere allo spazio dei nomi di destinazione dello schema del set di schemi.  
  
 Di seguito viene riportato un esempio di documento XML.  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 Lo schema seguente convalida il documento XML di esempio.  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 Nell'esempio di codice seguente lo schema precedente viene aggiunto alla proprietà <xref:System.Xml.Schema.XmlSchemaSet> di <xref:System.Xml.XmlReaderSettings.Schemas%2A> dell'oggetto <xref:System.Xml.XmlReaderSettings>. L'oggetto <xref:System.Xml.XmlReaderSettings> viene passato come parametro al metodo <xref:System.Xml.XmlReader.Create%2A> dell'oggetto <xref:System.Xml.XmlReader> che convalida il documento XML precedente.  
  
 La proprietà <xref:System.Xml.XmlReaderSettings.ValidationType%2A> dell'oggetto <xref:System.Xml.XmlReaderSettings> è impostata su `Schema` per imporre la convalida del documento XML mediante il metodo <xref:System.Xml.XmlReader.Create%2A> dell'oggetto <xref:System.Xml.XmlReader>. Un tipo <xref:System.Xml.Schema.ValidationEventHandler> viene aggiunto all'oggetto <xref:System.Xml.XmlReaderSettings> per gestire qualunque evento <xref:System.Xml.Schema.XmlSeverityType.Warning> o <xref:System.Xml.Schema.XmlSeverityType.Error> generato da errori rilevati durante il processo di convalida del documento XML e dello schema.  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a>Vedere anche

- [XmlSchemaSet per la compilazione di schemi](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Uso di schemi XML](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
