---
ms.openlocfilehash: ac929a8b3e9a7d56122f5699c51819ad483d1f5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235614"
---
### <a name="binaryformatter-can-fail-to-find-type-from-loadfrom-context"></a>BinaryFormatter potrebbe non trovare il tipo dal contesto LoadFrom

|   |   |
|---|---|
|Dettagli|A partire da .NET Framework 4.5, diverse modifiche di <xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> potrebbero causare differenze nella deserializzazione quando si usa <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> per deserializzare tipi caricati nel contesto LoadFrom. Queste modifiche sono dovute ai nuovi modi con cui <xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> ora carica un tipo che determina un comportamento diverso quando <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> tenta di eseguire la deserializzazione per quel tipo in un secondo momento. Il binder di serializzazione predefinito non esegue automaticamente la ricerca del contesto LoadFrom, anche se in alcuni casi potrebbe aver funzionato in base al comportamento precedente di XmlSerializer. A causa delle modifiche, quando un tipo viene caricato da un assembly caricato in un contesto diverso potrebbe essere generato <xref:System.IO.FileNotFoundException?displayProperty=name>.|
|Suggerimento|Se si verifica questa eccezione, la proprietà <code>Binder</code> di <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> può essere impostata su un binder personalizzato che troverà il tipo corretto.<pre><code class="lang-csharp">var formatter = new BinaryFormatter { Binder = new TypeFinderBinder() }&#13;&#10;</code></pre>Binder personalizzato:<pre><code class="lang-csharp">public class TypeFinderBinder : SerializationBinder&#13;&#10;{&#13;&#10;private static readonly string s_assemblyName = Assembly.GetExecutingAssembly().FullName;&#13;&#10;&#13;&#10;public override Type BindToType(string assemblyName, string typeName)&#13;&#10;{&#13;&#10;return Type.GetType(String.Format(CultureInfo.InvariantCulture, &quot;{0}, {1}&quot;, typeName, s_assemblyName));&#13;&#10;}&#13;&#10;}&#13;&#10;</code></pre>|
|Ambito|Microsoft Edge|
|Versione|4.5|
|Tipo|Runtime|
|API interessate|<ul><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
