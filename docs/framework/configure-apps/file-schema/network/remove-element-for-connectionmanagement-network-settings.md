---
title: Elemento <remove> per connectionManagement (impostazioni di rete)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 39ce85c3c15a2d4bdfce801a35e9ca088bd5091b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154738"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a>\<rimuovi> elemento per connectionManagement (impostazioni di rete)
Rimuove un indirizzo IP o un nome DNS dall'elenco di gestione delle connessioni.  

[**\<>di configurazione**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.net**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>connectionManagement**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rimuovere>**

## <a name="syntax"></a>Sintassi  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributes  
  
|**Attributo**|**Descrizione**|  
|-------------------|---------------------|  
|`address`|Un indirizzo IP o un nome DNS.|  
  
### <a name="child-elements"></a>Elementi figlio  
 No.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|**Elemento**|**Descrizione**|  
|-----------------|---------------------|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Specifica il numero massimo di connessioni a un host di rete.|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento `remove` rimuove la voce dell'elenco di gestione delle connessioni per il server specificato.  
  
 Il valore `address` dell'attributo deve essere un indirizzo IP o un nome host valido.  
  
## <a name="configuration-files"></a>File di configurazione  
 Questo elemento può essere usato nel file di configurazione dell'applicazione o nel file di configurazione del computer (Machine.config).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono rimosse tutte `www.adventure-works.com` le voci dell'elenco di gestione delle `www.contoso.com` connessioni per il server e quindi viene configurata un'applicazione per l'utilizzo di quattro connessioni al server e di due connessioni a tutti gli altri server.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Schema delle impostazioni di rete](index.md)
