---
title: Elemento <remove> per schemeSettings (impostazioni URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: faf254174527ea74638442a139841eb2365d1e5d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089158"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a>\<rimuovere > elemento per schemeSettings (impostazioni URI)
Rimuove un'impostazione dello schema per un nome di schema.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[**uri\<** ](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<SchemeSettings**](schemesettings-element-uri-settings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**rimuovere >**

## <a name="syntax"></a>Sintassi  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|name|Nome dello schema a cui si applica questa impostazione. Gli unici valori supportati sono Name = "http" e Name = "https".|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuna.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento \<schemeSettings> (impostazioni URI)](schemesettings-element-uri-settings.md)|Specifica come verrà analizzato un <xref:System.Uri> per schemi specifici.|  
  
## <a name="remarks"></a>Note  
 Per impostazione predefinita, la classe <xref:System.Uri?displayProperty=nameWithType> Annulla il carattere di escape per la percentuale di delimitatori di percorso codificati prima di eseguire la compressione del percorso. Questa operazione è stata implementata come meccanismo di sicurezza da attacchi come i seguenti:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Se questo URI viene passato a moduli che non gestiscono correttamente la percentuale di caratteri codificati, potrebbe verificarsi il seguente comando eseguito dal server:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Per questo motivo, <xref:System.Uri?displayProperty=nameWithType> classe First Annulla l'escape dei delimitatori di percorso e quindi applica la compressione del percorso. Il risultato del passaggio dell'URL dannoso precedente a <xref:System.Uri?displayProperty=nameWithType> costruttore della classe comporta l'URI seguente:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Questo comportamento predefinito può essere modificato in modo da non delimitatore di percorso codificato con percentuale di escape utilizzando l'opzione di configurazione schemeSettings per uno schema specifico.  
  
## <a name="configuration-files"></a>File di configurazione  
 Questo elemento può essere usato nel file di configurazione dell'applicazione o nel file di configurazione del computer (Machine.config).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrata una configurazione utilizzata dalla classe <xref:System.Uri> che rimuove qualsiasi impostazione dello schema per lo schema http.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [Schema delle impostazioni di rete](index.md)
