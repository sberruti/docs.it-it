---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152450"
---
# <a name="x509securitytokenhandlerrequirement"></a>\<x509SecurityTokenHandlerRequirement>
Fornisce una configurazione <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> facoltativa per la classe o le classi derivate.  
  
[**\<>di configurazione**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>system.identityModel**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>di identitàConfigurazione**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<aggiungere>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributes  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|certificateValidationMode|Valore <xref:System.ServiceModel.Security.X509CertificateValidationMode> che specifica la modalità di convalida da utilizzare per il certificato X.509. Il valore predefinito è "PeerOrChainTrust".|  
|MapToWindows (finestra di lavoro su MapToWindows|Specifica se il gestore di token deve eseguire il mapping del token di convalida a un account Windows utilizzando l'attestazione UPN in ingresso. Il valore predefinito è "false".|  
|revocationMode|Valore <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> che specifica la modalità di revoca da utilizzare per il certificato X.509. Il valore predefinito è "Online".|  
|trustedStoreLocation|Valore <xref:System.Security.Cryptography.X509Certificates.StoreLocation> che specifica l'archivio certificati X.509. Il valore predefinito è "LocalMachine".|  
|certificateValidator|Tipo personalizzato che deriva <xref:System.IdentityModel.Selectors.X509CertificateValidator>da . Se `certificateValidationMode` l'attributo è "Custom", un'istanza di questo tipo viene utilizzata per la convalida del certificato dell'autorità emittente.|  
  
### <a name="child-elements"></a>Elementi figlio  
 nessuno  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<aggiungere>](add.md)|Aggiunge il gestore del token di sicurezza specificato alla raccolta di gestori di token.|  
  
## <a name="example"></a>Esempio  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
