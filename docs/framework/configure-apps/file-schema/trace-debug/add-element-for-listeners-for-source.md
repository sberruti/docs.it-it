---
title: <add>Elemento <listeners> per<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153685"
---
# <a name="add-element-for-listeners-for-source"></a>\<aggiungere>elemento \<per i \<listener> per i> di origineAdd a Element for listeners> for source>
Aggiunge un listener alla raccolta `Listeners` per un'origine di traccia.  

[**\<>di configurazione**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.diagnostics**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<fonti>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>di ascoltatori**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<aggiungere>**

## <a name="syntax"></a>Sintassi  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributes  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`type`|Attributo obbligatorio, a meno che non `sharedListeners` si faccia riferimento a un listener nell'insieme, nel qual caso è sufficiente farvi riferimento in base al nome (vedere l'esempio ). [Example](#example)<br /><br /> Specifica il tipo di listener. È necessario utilizzare una stringa che soddisfi i requisiti specificati in Specifica di nomi di [tipo completi](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Attributo facoltativo.<br /><br /> Stringa passata al costruttore per la classe specificata. Viene <xref:System.Configuration.ConfigurationException> generata un'eccezione se la classe non dispone di un costruttore che accetta una stringa.|  
|`name`|Attributo facoltativo.<br /><br /> Specifica il nome del listener.|  
|`traceOutputOptions`|Attributo facoltativo.<br /><br /> Specifica il <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> valore della proprietà per il listener di traccia.|  
|[attributi personalizzati]|Attributi facoltativi.<br /><br /> Specifica il valore per gli attributi <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> specifici del listener identificati dal metodo per tale listener. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>è un esempio di un <xref:System.Diagnostics.DelimitedListTraceListener> attributo aggiuntivo univoco per la classe.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<>di filtro](filter-element-for-add-for-listeners-for-source.md)|Aggiunge un filtro a un listener nella raccolta `Listeners` per un'origine di traccia.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`configuration`|Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.|  
|`system.diagnostics`|Specifica i listener di traccia per raccogliere, archiviare e indirizzare i messaggi, oltre al livello di impostazione di un'opzione di traccia.|  
|`sources`|Contiene le origini di traccia che avviano i messaggi di traccia.|  
|`source`|Specifica un'origine di traccia che avvia i messaggi di traccia.|  
|`listeners`|Specifica i listener che raccolgono, archiviano e instradano i messaggi.|  
  
## <a name="remarks"></a>Osservazioni  
 Le classi listener fornite con .NET <xref:System.Diagnostics.TraceListener> Framework derivano dalla classe .  
  
 Se non si `name` specifica l'attributo <xref:System.Diagnostics.TraceListener.Name%2A> del listener di traccia, il valore predefinito della proprietà del listener di traccia è una stringa vuota (""). Se l'applicazione dispone di un solo listener, è possibile aggiungerlo senza specificare un nome ed è possibile rimuoverlo specificando una stringa vuota per il nome. Tuttavia, se l'applicazione dispone di più listener, è necessario specificare un nome univoco per ogni <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> listener di traccia, che consente di identificare e gestire i singoli listener di traccia nella raccolta.  
  
> [!NOTE]
> L'aggiunta di più listener di traccia dello stesso tipo e con lo stesso nome `Listeners` comporta l'aggiunta di un solo listener di traccia di tale tipo e nome alla raccolta. Tuttavia, è possibile aggiungere a livello `Listeners` di codice più listener identici alla raccolta.  
  
 Il valore `initializeData` dell'attributo dipende dal tipo di listener creato. Non tutti i listener di `initializeData`traccia richiedono l'impostazione di .  
  
> [!NOTE]
> Quando si `initializeData` utilizza l'attributo, è possibile che venga visualizzato l'avviso del compilatore "L'attributo 'initializeData' non è dichiarato". Questo avviso viene generato perché le impostazioni di <xref:System.Diagnostics.TraceListener>configurazione vengono convalidate rispetto alla classe base astratta , che non riconosce l'attributo `initializeData` . In genere, è possibile ignorare questo avviso per le implementazioni del listener di traccia che dispongono di un costruttore che accetta un parametro.  
  
 Nella tabella seguente vengono illustrati i listener di traccia inclusi in .NET Framework e viene descritto il valore dei relativi `initializeData` attributi.  
  
|Classe listener di traccia|valore dell'attributo initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|Valore `useErrorStream` per <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> il costruttore.  Impostare `initializeData` l'attributo su "`true`" per scrivere la traccia e l'output di debug nel flusso di errore standard; impostarlo su`false`" " per scrivere nel flusso di output standard.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|Nome del file in cui scrive <xref:System.Diagnostics.DelimitedListTraceListener>.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|Nome di un'origine del log eventi esistente.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|Nome del file in <xref:System.Diagnostics.EventSchemaTraceListener> cui viene scritto il file.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|Nome del file in <xref:System.Diagnostics.TextWriterTraceListener> cui viene scritto il file.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|Nome del file in <xref:System.Diagnostics.XmlWriterTraceListener> cui viene scritto il file.|  
  
## <a name="configuration-file"></a>File di configurazione  
 Questo elemento può essere utilizzato nel file di configurazione del computer (Machine.config) e nel file di configurazione dell'applicazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio riportato `<add>` di seguito viene `console` illustrato `textListener` come `Listeners` utilizzare gli `TraceSourceApp`elementi per aggiungere i listener e all'insieme per l'origine di traccia. Il `textListener` listener scrive l'output di traccia nel file myListener.log.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [Schema delle impostazioni di traccia e debug](index.md)
- [Listener di traccia](../../../debug-trace-profile/trace-listeners.md)
