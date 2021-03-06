---
ms.openlocfilehash: 94c582d25ae1cd2249ed2e3774134a86cf77327b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "73085528"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>L'impostazione dell'app "dataAnnotations:dataTypeAttribute:disableRegEx" è attivata per impostazione predefinita in .NET Framework 4.7.2

|   |   |
|---|---|
|Dettagli|In .NET Framework 4.6.1 è stata introdotta un'impostazione dell'app (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>) che consente agli utenti di disattivare l'uso delle espressioni regolari negli attributi del tipo di dati (ad esempio <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>, <xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> e <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>). In questo modo si riducono le vulnerabilità di sicurezza, ad esempio evitando la possibilità di un attacco Denial of Service tramite espressioni regolari specifiche.<br/>In .NET Framework 4.6.1 questa impostazione dell'app per disattivare l'uso di RegEx era <code>false</code> per impostazione predefinita. A partire da .NET Framework 4.7.2, <code>true</code> questa opzione di configurazione è impostata su per impostazione predefinita per ridurre ulteriormente la vulnerabilità sicura per le applicazioni Web destinate a .NET Framework 4.7.2 e versioni successive.|
|Suggerimento|Se si nota che le espressioni regolari nell'applicazione Web non funzionano dopo l'aggiornamento a .NET Framework 4.7.2, è possibile assegnare all'impostazione <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> il valore <code>false</code> per ripristinare il comportamento precedente.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Scope|Minorenne|
|Versione|4.7.2|
|Type|Runtime|
