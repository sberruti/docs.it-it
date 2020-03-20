---
title: Associazione HTTP WS 2007 Federation
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: bf61e64733859d96adf42fbacf08266eca1f5b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183177"
---
# <a name="ws-2007-federation-http-binding"></a>Associazione HTTP WS 2007 Federation

In questo esempio viene descritto l'utilizzo di <xref:System.ServiceModel.WS2007FederationHttpBinding>, un'associazione standard che è possibile utilizzare per compilare scenari federati che supportano la versione 1.3 della specifica WS-Trust.

> [!NOTE]
> La procedura di installazione e le istruzioni di compilazione per questo esempio si trovano alla fine di questo argomento.

L'esempio è costituito da un programma client basato su console (*Client.exe*), un programma di servizio token di sicurezza basato su console (*Securitytokenservice.exe*) e un programma di servizio basato su console (*Service.exe*). Il servizio implementa un contratto che definisce un modello di comunicazione request/reply. Il contratto viene definito dall'interfaccia `ICalculator` che espone operazioni matematiche (`Add`, `Subtract`, `Multiply` e `Divide`). Il client riceve un token di protezione dal servizio token di sicurezza (STS), esegue richieste sincrone al servizio per un'operazione matematica specificata. Il servizio risponde quindi fornendo il risultato. L'attività del client è visibile nella finestra della console.

L'esempio rende disponibile il contratto `ICalculator` utilizzando l'elemento `ws2007FederationHttpBinding`. La configurazione di questa associazione sul client è illustrata nel codice seguente:The configuration of this binding on the client is shown in the following code:

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Endpoint address and binding for Security Token Service -->
          <issuer address ="http://localhost:8000/sts/windows"
                  binding ="ws2007HttpBinding" />
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

Nella [ \<>di ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` sicurezza , il valore specifica la modalità di protezione da utilizzare. In questo `message` esempio viene utilizzata la sicurezza, motivo per cui il [ \<>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) del messaggio viene specificato all'interno del [ \<>di sicurezza ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). L'elemento [ \<>dell'autorità di certificazione](../../configure-apps/file-schema/wcf/issuer.md) all'interno del [ \<messaggio>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifica l'indirizzo e l'associazione per il servizio token di sicurezza che rilascia un token di sicurezza al client in modo che il client possa eseguire l'autenticazione al `ICalculator` servizio.
  
La configurazione di questa associazione nel servizio è illustrata nel codice seguente:The configuration of this binding on the service is shown in the following code:

```xml
<bindings>
  <ws2007FederationHttpBinding>
    <binding name="ServiceFed" >
      <security mode ="Message">
        <message issuedKeyType ="SymmetricKey"
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >
          <!-- Metadata address for Security Token Service -->
          <issuerMetadata address ="http://localhost:8000/sts/mex" >
            <identity>
              <certificateReference storeLocation ="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType ="FindBySubjectDistinguishedName"
                                    findValue ="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </ws2007FederationHttpBinding>
</bindings>
```

Nella [ \<>di ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) `security` sicurezza , il valore specifica la modalità di protezione da utilizzare. In questo `message` esempio viene utilizzata la sicurezza, motivo per cui il [ \<>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) del messaggio viene specificato all'interno del [ \<>di sicurezza ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). L'elemento [ \<issuerMetadata>](../../configure-apps/file-schema/wcf/issuermetadata.md) di all'interno del `ws2007FederationHttpBinding` [ \<messaggio>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) specifica l'indirizzo e l'identità di un endpoint che può essere utilizzato per recuperare i metadati per il servizio token di sicurezza.

Il comportamento per il servizio è illustrato nel codice seguente:The behavior for the service is shown in the following code:

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name ="ServiceBehaviour" >
      <serviceDebug includeExceptionDetailInFaults ="true"/>
      <serviceMetadata httpGetEnabled ="true"/>
      <serviceCredentials>
        <issuedTokenAuthentication>
          <knownCertificates>
            <add storeLocation ="LocalMachine"
                 storeName="TrustedPeople"
                 x509FindType="FindBySubjectDistinguishedName"
                 findValue="CN=STS" />
          </knownCertificates>
        </issuedTokenAuthentication>
        <serviceCertificate storeLocation ="LocalMachine"
                            storeName ="My"
                            x509FindType ="FindBySubjectDistinguishedName"
                            findValue ="CN=localhost"/>
      </serviceCredentials>
    </behavior>
  </serviceBehaviors>
</behaviors>
```
  
Il [ \<>issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) consente al servizio di specificare vincoli sui token che consente ai client di presentare durante l'autenticazione. Questa configurazione specifica che i token firmati da un certificato il cui nome di soggetto è CN=STS possono essere accettati dal servizio.

Il servizio token di sicurezza rende disponibile un singolo endpoint utilizzando l'oggetto <xref:System.ServiceModel.WS2007HttpBinding> standard. Il servizio risponde alle richieste dei client per i token. Se il client viene autenticato utilizzando un account di Windows, il servizio pubblica un token che contiene il nome utente del client come attestazione. Come parte del processo di creazione del token, il servizio token di sicurezza firma il token utilizzando la chiave privata associata al certificato CN=STS . Crea, inoltre, una chiave simmetrica e la crittografa utilizzando la chiave pubblica associata al certificato CN=localhost. Nel restituire il token al client, il servizio token di sicurezza restituisce anche la chiave simmetrica. Il client presenta il token emesso al servizio `ICalculator` e dimostra che conosce la chiave simmetrica firmando il messaggio con quella chiave.

Quando si esegue l'esempio, la richiesta per il token di sicurezza viene visualizzata nella finestra della console del servizio token di sicurezza. Le richieste e le risposte dell'operazione vengono visualizzate nella finestra della console del client e in quella del servizio. Premere INVIO in una delle finestre della console per arrestare l'applicazione.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

Il file *Setup.bat* incluso in questo esempio consente di configurare il server e il servizio token di sicurezza con i certificati pertinenti per l'esecuzione di un'applicazione self-hosted. Il file batch crea due certificati, nell'archivio certificati di LocalMachine/TrustedPeople. Il primo certificato ha un nome soggetto di CN=STS e viene utilizzato dal servizio token di sicurezza per firmare i token di protezione emessi al client. Il secondo certificato ha un nome soggetto di CN=localhost e viene utilizzato dal servizio token di sicurezza per crittografare una chiave in modo che il servizio non possa decrittografarla.

## <a name="to-set-up-build-and-run-the-sample"></a>Per impostare, compilare ed eseguire l'esempio
  
1. Assicurarsi di aver eseguito la procedura di [installazione una tantera per Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aprire un prompt dei comandi per sviluppatori per Visual Studio con privilegi di amministratore ed eseguire il file Setup.bat per creare i certificati necessari.

 Questo file batch utilizza *Certmgr.exe* e Makecert.exe, distribuiti con Windows SDK. Tuttavia, è necessario eseguire *Setup.bat* dall'interno di un prompt dei comandi di Visual Studio per consentire allo script di trovare questi strumenti.

1. Per compilare l'edizione in C# o Visual Basic .NET della soluzione, seguire le istruzioni in [Building the Windows Communication Foundation Samples](building-the-samples.md).

2. Per eseguire l'esempio in una configurazione a singolo o tra computer, seguire le istruzioni in Esecuzione di [Windows Communication Foundation Samples](running-the-samples.md). Se si utilizza Windows Vista, è necessario eseguire *Service.exe*, *Client.exe*e *SecurityTokenService.exe* con privilegi elevati (fare clic con il pulsante destro del mouse sui file e quindi **scegliere Esegui come amministratore**).

> [!IMPORTANT]
> È possibile che gli esempi siano già installati nel computer. Verificare la directory seguente (impostazione predefinita) prima di continuare.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se questa directory non esiste, passare a [Windows Communication Foundation (WCF) e Windows Workflow Foundation (WF) Esempi per .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) per scaricare tutti gli esempi e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (WCF). Questo esempio si trova nella directory seguente.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
