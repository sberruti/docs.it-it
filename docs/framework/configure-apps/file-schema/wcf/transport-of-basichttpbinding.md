---
title: <transport> di <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: c563339e4f854cc4e60f92dd5b8c0b39112dc000
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736116"
---
# <a name="transport-of-basichttpbinding"></a>\<> di trasporto di \<BasicHttpBinding >
Definisce proprietà che controllano i parametri di autenticazione per il trasporto HTTP.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**Binding**](bindings.md)\<
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**basicHttpBinding**](basichttpbinding.md)\<
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**Binding** >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**sicurezza**](security-of-basichttpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**Transport** >  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|clientCredentialType|-Specifica il tipo di credenziale da usare quando si esegue l'autenticazione client usando l'autenticazione HTTP.  Il valore predefinito è `None`. L'attributo è di tipo <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|-Specifica il tipo di credenziale da usare quando si esegue l'autenticazione client dall'interno di un dominio usando un proxy su HTTP. Questo attributo è applicabile solo quando l'attributo `mode` dell'elemento `security` padre è `Transport` o `TransportCredentialsOnly`. L'attributo è di tipo <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|realm|Stringa che specifica l'area di autenticazione usata dallo schema di autenticazione HTTP per l'autenticazione digest o di base. Il valore predefinito è una stringa vuota.|  
|policyEnforcement|Questa enumerazione specifica il momento in cui deve essere applicato l'oggetto <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.<br /><br /> 1. Never: il criterio non viene mai applicato (la protezione estesa è disabilitata).<br />2. WhenSupported: i criteri vengono applicati solo se il client supporta la protezione estesa.<br />3. always: i criteri vengono sempre applicati. L'autenticazione dei client che non supportano la protezione estesa avrà esito negativo.|  
|protectionScenario|Questa enumerazione specifica lo scenario di protezione applicato dai criteri.|  
  
## <a name="clientcredentialtype-attribute"></a>Attributo clientCredentialType  
  
|Value|Descrizione|  
|-----------|-----------------|  
|Nessuno|I messaggi non vengono protetti durante il trasferimento.|  
|Basic|Specifica l'autenticazione di base.|  
|Digest|Specifica l'autenticazione digest.|  
|Ntlm|Specifica l'autenticazione NTLM quando possibile e se l'autenticazione di Windows non riesce.|  
|WINDOWS|Specifica l'autenticazione integrata di Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>Attributo proxyCredentialType  
  
|Value|Descrizione|  
|-----------|-----------------|  
|Nessuno|-I messaggi non vengono protetti durante il trasferimento.|  
|Basic|Specifica l'autenticazione di base come definita da RFC 2617 – HTTP Authentication: Basic and Digest Authentication.|  
|Digest|Specifica l'autenticazione digest come definita da RFC 2617 – HTTP Authentication: Basic and Digest Authentication.|  
|Ntlm|Specifica l'autenticazione NTLM quando possibile e se l'autenticazione di Windows non riesce.|  
|WINDOWS|Specifica l'autenticazione integrata di Windows.|  
|Certificato|Esegue l'autenticazione client mediante un certificato. Questa opzione funziona solo se l'attributo `Mode` dell'elemento `security` padre è impostato su Transport, mentre non funzionerà se viene impostato su TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[\<security >](security-of-basichttpbinding.md)|Definisce le funzionalità di sicurezza per il [> BasicHttpBinding di\<](basichttpbinding.md).|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente è dimostrato l'uso della sicurezza del trasporto SSL con l'associazione di base. Per impostazione predefinita, l'associazione di base supporta la comunicazione HTTP.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [Protezione di servizi e client](../../../wcf/feature-details/securing-services-and-clients.md)
- [Associazioni](../../../wcf/bindings.md)
- [Configurazione di associazioni fornite dal sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Uso di associazioni per configurare servizi e client](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding >](bindings.md)
