---
title: elemento <security> di <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: b85c54c6507313522286e0c66504cfd0c8afb2b0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738731"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a>\<elemento > Security di \<ws2007FederationHttpBinding >
Definisce le impostazioni di sicurezza dell'elemento [\<> WS2007FederationHttpBinding](ws2007federationhttpbinding.md) .  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**Binding**](bindings.md)\<
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**WS2007FederationHttpBinding**](ws2007federationhttpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**Binding** >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**sicurezza** >  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`mode`|Parametro facoltativo. Specifica il tipo di sicurezza applicata. Il valore predefinito è `Message`. L'attributo è di tipo <xref:System.ServiceModel.WSFederationHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>Attributo mode  
  
|Value|Descrizione|  
|-----------|-----------------|  
|Nessuno|Il messaggio SOAP non viene protetto durante il trasferimento.|  
|Messaggio|L'integrità, la riservatezza e l'autenticazione server e client sono fornite usando la sicurezza dei messaggi SOAP. Per impostazione predefinita, il corpo viene crittografato e firmato. Il servizio deve essere configurato con un certificato. L'autenticazione client è basata sul token rilasciato al client da un servizio token di sicurezza.|  
|TransportWithMessageCredential|Integrità, riservatezza e autenticazione server sono fornite tramite HTTPS. Il servizio deve essere configurato con un certificato. L'autenticazione client è fornita tramite la sicurezza dei messaggi SOAP ed è basata sul token rilasciato al client da un servizio token di sicurezza.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<message >](message-of-ws2007httpbinding.md)|Definisce le impostazioni di sicurezza per il messaggio. L'elemento è di tipo <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<binding >](bindings.md)|Definisce tutte le funzionalità di associazione della [\<wsDualHttpBinding >](wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [Procedura: Creare una classe WSFederationHttpBinding](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Protezione di servizi e client](../../../wcf/feature-details/securing-services-and-clients.md)
- [Selezione di un tipo di credenziale](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Associazioni](../../../wcf/bindings.md)
- [Configurazione di associazioni fornite dal sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Uso di associazioni per configurare servizi e client](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding >](bindings.md)
