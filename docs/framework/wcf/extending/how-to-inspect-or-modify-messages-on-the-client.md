---
title: 'Procedura: ispezionare o modificare i messaggi sul client'
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: db1a99d2ed1f765e39815e6b6c70d6ada1db1d15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185530"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a>Procedura: ispezionare o modificare i messaggi sul client
È possibile esaminare o modificare i messaggi in <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> ingresso o in uscita in un client WCF implementando un e inserendolo nel runtime client. Per ulteriori informazioni, vedere [Estensione dei client](extending-clients.md). La funzionalità equivalente nel servizio è <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>. Per un esempio di codice completo, vedere l'esempio [Message Inspectors.For](../samples/message-inspectors.md) a complete code example.  
  
### <a name="to-inspect-or-modify-messages"></a>Per ispezionare o modificare i messaggi  
  
1. Implementare l'interfaccia <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
2. Implementare <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> o <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> in base all'ambito in cui si desidera inserire il controllo dei messaggi client. <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>consente di modificare il comportamento a livello di endpoint. <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>consente di modificare il comportamento a livello di contratto.  
  
3. Inserire il comportamento prima di chiamare il metodo <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> o <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> su <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Per informazioni dettagliate, consultate [Configurazione ed estensione del runtime con comportamenti.](configuring-and-extending-the-runtime-with-behaviors.md)  
  
## <a name="example"></a>Esempio  
 Negli esempi di codice seguenti vengono illustrati, nell'ordine:  
  
- Un'implementazione del controllo client.  
  
- Un comportamento dell'endpoint che inserisce il controllo.  
  
- Una classe derivata da <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>che consente di aggiungere il comportamento in un file di configurazione.  
  
- Un file di configurazione che aggiunge il comportamento dell'endpoint che inserisce il controllo dei messaggi client nel runtime del client.  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"
                      binding="wsHttpBinding"
                      behaviorConfiguration="clientInspectorsAdded"
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Configurazione ed estensione del runtime con i comportamenti](configuring-and-extending-the-runtime-with-behaviors.md)
