---
title: Elemento <bypasslist> (impostazioni di rete)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154946"
---
# <a name="bypasslist-element-network-settings"></a>\<bypasslist> elemento (impostazioni di rete)
Fornisce un set di espressioni regolari che descrivono gli indirizzi che non utilizzano un proxy.  

[**\<>di configurazione**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.net**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>defaultProxy**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<elenco di>**

## <a name="syntax"></a>Sintassi  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributes  
 No.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|**Elemento**|**Descrizione**|  
|-----------------|---------------------|  
|[aggiungi](add-element-for-bypasslist-network-settings.md)|Aggiunge un indirizzo IP o un nome DNS all'elenco di esclusione proxy.|  
|[Chiaro](clear-element-for-bypasslist-network-settings.md)|Cancella l'elenco dei bypass.|  
|[rimozione](remove-element-for-bypasslist-network-settings.md)|Rimuove un indirizzo IP o un nome DNS dall'elenco di esclusione proxy.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|**Elemento**|**Descrizione**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Configura il server proxy Hypertext Transfer Protocol (HTTP).|  
  
## <a name="remarks"></a>Osservazioni  
 L'elenco di esclusione contiene <xref:System.Net.WebRequest> espressioni regolari che descrivono gli URI a cui accedono direttamente le istanze anziché tramite il server proxy.  
  
 Prestare attenzione quando si specifica un'espressione regolare per questo elemento. L'espressione regolare "[a-z]-contoso\\.com"\\corrisponde a qualsiasi host nel dominio contoso.com, ma corrisponde anche a qualsiasi host nel dominio contoso.com.cpandl.com. Per trovare una corrispondenza solo con un host nel dominio contoso.com,\\utilizzare\\un ancoraggio (sezione "): "[a-z] .  
  
 Per ulteriori informazioni sulle espressioni regolari, vedere . [Espressioni regolari di .NET Framework](../../../../standard/base-types/regular-expressions.md).  
  
## <a name="configuration-files"></a>File di configurazione  
 Questo elemento può essere usato nel file di configurazione dell'applicazione o nel file di configurazione del computer (Machine.config).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono aggiunti due indirizzi all'elenco di esclusione. Il primo ignora il proxy per tutti i server nel dominio contoso.com; il secondo ignora il proxy per tutti i server i cui indirizzi IP iniziano con 192.168.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Schema delle impostazioni di rete](index.md)
