---
title: configurazione di applicazioni Internet
ms.date: 03/30/2017
helpviewer_keywords:
- downloading Internet resources, default proxy
- sending data, default proxy
- receiving data, default proxy
- downloading Internet resources, configuring Internet applications
- protocol-specific modules
- custom authentication modules
- receiving data, configuring Internet applications
- configuration settings [.NET Framework], Internet applications
- requesting data from Internet, configuring Internet applications
- requesting data from Internet, default proxy
- response to Internet request, default proxy
- Internet, configuring Internet applications
- response to Internet request, configuring Internet applications
- default proxy
- network resources, default proxy
- sending data, configuring Internet applications
- network resources, configuring Internet applications
- Internet, default proxy
ms.assetid: bb707c72-eed2-4a82-8800-c9e68df2fd4f
ms.openlocfilehash: ee4dc87383153ae4e8df0a3bed7cce5220e65405
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048627"
---
# <a name="configuring-internet-applications"></a>configurazione di applicazioni Internet
L'elemento [ \<](../configure-apps/file-schema/network/system-net-element-network-settings.md) di configurazione system.Net elemento> (impostazioni di rete) contiene informazioni di configurazione di rete per le applicazioni. Utilizzando l'elemento [ \<system.Net elemento> (impostazioni di rete),](../configure-apps/file-schema/network/system-net-element-network-settings.md) è possibile impostare i server proxy, impostare i parametri di gestione delle connessioni e includere moduli di richiesta e autenticazione personalizzati nell'applicazione.  
  
 L'elemento [ \<defaultProxy> Element (Impostazioni di rete)](../configure-apps/file-schema/network/defaultproxy-element-network-settings.md) `GlobalProxySelection` definisce il server proxy restituito dalla classe. Qualsiasi <xref:System.Net.HttpWebRequest> la cui proprietà <xref:System.Net.HttpWebRequest.Proxy%2A> non sia impostata su un valore specifico usa il proxy predefinito. Oltre a impostare l'indirizzo del proxy, è possibile creare un elenco di indirizzi di server che non usano il proxy. È anche possibile indicare che il proxy non deve essere usato per gli indirizzi locali.  
  
 È importante notare che le impostazioni di Microsoft Internet Explorer vengono combinate con le impostazioni di configurazione, che hanno la precedenza.  
  
 L'esempio seguente imposta l'indirizzo del server proxy predefinito su `http://proxyserver`, indica che il proxy non deve essere usato per gli indirizzi locali e specifica che tutte le richieste ai server presenti nel dominio contoso.com devono ignorare il proxy.  
  
```xml  
<configuration>  
    <system.net>  
        <defaultProxy>  
            <proxy  
                usesystemdefault = "false"  
                proxyaddress = "http://proxyserver:80"  
                bypassonlocal = "true"  
            />  
            <bypasslist>  
                <add address="http://[a-z]+\.contoso\.com/" />  
            </bypasslist>  
        </defaultProxy>  
    </system.net>  
</configuration>  
```  
  
 Utilizzare l'elemento [ \<connectionManagement> Element (Network Settings)](../configure-apps/file-schema/network/connectionmanagement-element-network-settings.md) per configurare il numero di connessioni permanenti che è possibile effettuare a un server specifico o a tutti gli altri server. L'esempio seguente configura l'applicazione in modo da usare due connessioni persistenti al server `www.contoso.com`, quattro connessioni persistenti al server con indirizzo IP 192.168.1.2 e una connessione persistente a tutti gli altri server.  
  
```xml  
<configuration>  
    <system.net>  
        <connectionManagement>  
            <add address="http://www.contoso.com" maxconnection="2" />  
            <add address="192.168.1.2" maxconnection="4" />  
            <add address="*" maxconnection="1" />  
        </connectionManagement>  
    </system.net>  
</configuration>  
```  
  
 I moduli di autenticazione personalizzati vengono configurati con l'elemento [ \<authenticationModules> Element (Impostazioni di rete).](../configure-apps/file-schema/network/authenticationmodules-element-network-settings.md) I moduli di autenticazione personalizzati devono implementare l'interfaccia <xref:System.Net.IAuthenticationModule>.  
  
 L'esempio seguente configura un modulo di autenticazione personalizzato.  
  
```xml  
<configuration>  
    <system.net>  
        <authenticationModules>  
            <add type="MyAuthModule, MyAuthModule.dll" />  
        </authenticationModules>  
    </system.net>  
</configuration>  
```  
  
 È possibile utilizzare l'elemento [ \<webRequestModules> elemento (impostazioni di rete)](../configure-apps/file-schema/network/webrequestmodules-element-network-settings.md) per configurare l'applicazione per l'utilizzo di moduli personalizzati specifici del protocollo per richiedere informazioni dalle risorse Internet.You can use the webRequestModules from Element (Network Settings) element (Network Settings) element to configure your application to use custom protocol-specific modules to request information from Internet resources. I moduli specificati devono implementare l'interfaccia <xref:System.Net.IWebRequestCreate>. È possibile eseguire l'override dei moduli HTTP, HTTPS e di richiesta di file predefiniti specificando il modulo personalizzato nel file di configurazione, come nell'esempio seguente.  
  
```xml  
<configuration>  
    <system.net>  
        <webRequestModules>  
            <add  
                prefix="HTTP"  
                type = "MyHttpRequest.dll, MyHttpRequestCreator"  
            />  
        </webRequestModules>  
    </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche

- [Programmazione di rete in .NET Framework](index.md)
- [Schema delle impostazioni di rete](../configure-apps/file-schema/network/index.md)
- [\<elemento> system.Net (impostazioni di rete)](../configure-apps/file-schema/network/system-net-element-network-settings.md)
