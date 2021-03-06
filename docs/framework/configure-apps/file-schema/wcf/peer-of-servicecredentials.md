---
title: <peer> di <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397635"
---
# <a name="peer-of-servicecredentials"></a>\<peer > di \<ServiceCredentials >
Specifica le credenziali correnti per un nodo peer.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamenti >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamento >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> di serviceCredentials**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> peer**  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti attributi, elementi figlio ed elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|DESCRIZIONE|  
|-------------|-----------------|  
|[\<> certificato](certificate-of-peer.md)|Specifica un certificato X.509 da usare per firmare e crittografare i messaggi di servizi peer-to-peer. .|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|Specifica le opzioni di autenticazione dei mittenti di messaggi.|  
|[\<peerAuthentication>](peerauthentication.md)|Specifica le opzioni di autenticazione dei servizi peer.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Specifica la credenziale da usare nell'autenticazione del servizio e le impostazioni relative alla convalida delle credenziali client.|  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [Reti peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md)
- [Autenticazione del messaggio Peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [Peer Channel autenticazione personalizzata](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [Protezione di applicazioni del canale peer](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [Protezione di servizi e client](../../../wcf/feature-details/securing-services-and-clients.md)
