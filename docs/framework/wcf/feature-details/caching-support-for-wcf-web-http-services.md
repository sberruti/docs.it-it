---
title: Supporto di memorizzazione nella cache per servizi HTTP Web WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 5964c58ce28f67815774741815bba0fcbe3b2de7
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964229"
---
# <a name="caching-support-for-wcf-web-http-services"></a>Supporto di memorizzazione nella cache per servizi HTTP Web WCF

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] consente di utilizzare il meccanismo dichiarativo di memorizzazione nella cache già disponibile in ASP.NET nei servizi HTTP Web WCF. In questo modo è possibile memorizzare nella cache le risposte inviate dalle operazioni del servizio HTTP Web WCF. Se un utente invia un'operazione HTTP GET al servizio configurato per la memorizzazione nella cache, ASP.NET restituisce la risposta memorizzata nella cache e il metodo del servizio non viene chiamato. Se la cache scade, al successivo tentativo di invio di un'operazione HTTP GET da parte dell'utente, viene chiamato il metodo del servizio e la risposta viene nuovamente memorizzata nella cache. Per ulteriori informazioni sulla memorizzazione nella cache ASP.NET, vedere [Cenni preliminari sulla memorizzazione nella cache ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
## <a name="basic-web-http-service-caching"></a>Memorizzazione nella cache del servizio HTTP Web di base  
 Per abilitare la memorizzazione nella cache del servizio HTTP WEB, è innanzitutto necessario abilitare la compatibilità ASP.NET applicando <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> al servizio, impostando <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> su <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> o <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 .NET Framework 4 introduce un nuovo attributo denominato <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> che consente di specificare un nome di profilo della cache. L'attributo è applicato a un'operazione del servizio. Nell'esempio seguente <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> viene applicato a un servizio per abilitare la compatibilità ASP.NET e l'operazione `GetCustomer` viene configurata per la memorizzazione nella cache. L'attributo <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> specifica un profilo cache che contiene le impostazioni della cache da utilizzare.  
  
```csharp
[ServiceContract] 
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
 È inoltre necessario abilitare la modalità di compatibilità ASP.NET nel file Web.config, come indicato nell'esempio seguente.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> Se la modalità di compatibilità ASP.NET non è abilitata e viene utilizzato <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, verrà generata un'eccezione.  
  
 Il nome di profilo cache specificato da <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifica un profilo cache aggiunto al file di configurazione Web.config. Il profilo della cache viene definito con in un <`outputCacheSetting`> elemento, come illustrato nell'esempio di configurazione seguente.  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 Si tratta dello stesso elemento di configurazione disponibile per le applicazioni ASP.NET. Per ulteriori informazioni sui profili della cache ASP.NET, vedere <xref:System.Web.Configuration.OutputCacheProfile>. Per i servizi HTTP Web, gli attributi più importanti del profilo cache sono `cacheDuration` e `varyByParam`. Entrambi gli attributi sono obbligatori. `cacheDuration` imposta la quantità di tempo in secondi necessaria per la memorizzazione nella cache di una risposta. `varyByParam` consente di specificare un parametro della stringa di query utilizzato per memorizzare risposte nella cache. Tutte le richieste effettuate con valori del parametro della stringa di query diversi vengono memorizzate nella cache separatamente. Ad esempio, una volta effettuata una richiesta iniziale di `http://MyServer/MyHttpService/MyOperation?param=10`, tutte le richieste successive effettuate con lo stesso URI verrebbero restituite dalla risposta memorizzata nella cache (purché la durata della cache non sia trascorsa). Le risposte per una richiesta analoga ma con valore diverso per quanto riguarda il parametro della stringa di query vengono memorizzate nella cache separatamente. Se non si desidera questo tipo di comportamento di memorizzazione nella cache, impostare `varyByParam` su "none".  
  
## <a name="sql-cache-dependency"></a>Dipendenza dalla cache SQL  
 È inoltre possibile memorizzare nella cache le risposte di un servizio HTTP Web con una dipendenza della cache SQL. Se il servizio HTTP Web WCF dipende da dati archiviati in un database SQL, potrebbe risultare opportuno memorizzare nella cache la risposta del servizio e invalidare la risposta memorizzata nella cache quando i dati nella tabella del database SQL vengono modificati. Questo comportamento viene completamente configurato all'interno del file Web.config. È innanzitutto necessario definire una stringa di connessione nell'elemento <`connectionStrings`>.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 È quindi necessario abilitare la dipendenza della cache SQL all'interno di un elemento <`caching`> all'interno dell'elemento <`system.web`> come illustrato nell'esempio di configurazione seguente.  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 In questo caso viene abilitata la dipendenza della cache SQL e viene impostato un tempo di polling di 1000 millisecondi. Ogni volta che scade il tempo di polling, viene verificata la presenza di aggiornamenti nella tabella di database. Se vengono rilevate modifiche, il contenuto della cache viene rimosso e, la volta successiva in cui l'operazione del servizio viene richiamata, viene memorizzata nella cache una nuova risposta. All'interno dell'elemento <`sqlCacheDependency`> aggiungere i database e fare riferimento alle stringhe di connessione all'interno dell'elemento <`databases`> come illustrato nell'esempio seguente.  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 Successivamente, è necessario configurare le impostazioni della cache di output all'interno dell'<`caching`> elemento, come illustrato nell'esempio seguente.  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 In questo caso la durata della cache è impostata su 60 secondi, `varyByParam` è impostato su none e `sqlDependency` è impostato su un elenco con valori delimitati da punti e virgola di coppie di nomi/tabelle del database separate dai due punti. Se i dati in `MyTable` vengono modificati, la risposta memorizzata nella cache per l'operazione del servizio viene rimossa e, se si richiama l'operazione, una nuova risposta viene generata, memorizzata nella cache e restituita al client.  
  
> [!IMPORTANT]
> Per ASP.NET accedere a un database SQL, è necessario usare lo [strumento di registrazione ASP.NET SQL Server](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)). È inoltre necessario consentire l'accesso dell'account utente appropriato al database e alla tabella. Per ulteriori informazioni, vedere [accesso SQL Server da un'applicazione Web](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).  
  
## <a name="conditional-http-get-based-caching"></a>Memorizzazione nella cache basata su HTTP GET condizionale  
 Negli scenari HTTP Web un HTTP GET condizionale viene spesso usato dai servizi per implementare la memorizzazione nella cache HTTP intelligente, come descritto nella [specifica http](https://www.w3.org/Protocols/rfc2616/rfc2616.html). A tale scopo, il servizio deve impostare il valore dell'intestazione ETag nella risposta HTTP. Deve inoltre verificare l'intestazione If-None-Match nella richiesta HTTP per controllare se una o più delle intestazioni ETag specificate corrisponde all'intestazione ETag corrente.  
  
 Per le richieste GET e HEAD, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> utilizza un valore ETag e lo verifica rispetto all'intestazione If-None-Match della richiesta. Se l'intestazione è presente e viene individuata una corrispondenza, viene generata un'eccezione <xref:System.ServiceModel.Web.WebFaultException> con codice di stato HTTP 304 (non modificato) e viene aggiunta un'intestazione ETag alla risposta con l'intestazione ETag corrispondente.  
  
 Un overload del metodo <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> utilizza la data di un'ultima modifica e la controlla rispetto all'intestazione If-Modified-Since della richiesta. Se l'intestazione è presente e la risorsa non è stata ancora modificata, viene generata un'eccezione <xref:System.ServiceModel.Web.WebFaultException> con codice di stato HTTP 304 (non modificato).  
  
 Per le richieste PUT, POST e DELETE, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> utilizza il valore ETag corrente di una risorsa. Se il valore ETag corrente è null, il metodo verifica che il valore dell'intestazione If-None-Match sia "*".  Se il valore ETag corrente non è un valore predefinito, il metodo controlla il valore ETag corrente rispetto all'intestazione If- Match della richiesta. In entrambi i casi, il metodo genera un'eccezione <xref:System.ServiceModel.Web.WebFaultException> con codice di stato HTTP 412 (precondizione non riuscita) se l'intestazione prevista non è presente nella richiesta o il relativo valore non soddisfa il controllo condizionale e imposta l'intestazione ETag della risposta sul valore ETag corrente.  
  
 Entrambi i metodi `CheckConditional` e il metodo <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> verificano che il valore ETag impostato nell'intestazione della risposta sia valido in base alla specifica HTTP. Ciò include la possibilità di racchiudere il valore ETag tra virgolette, se non già presenti, e di utilizzare i caratteri di escape per eventuali virgolette interne. Il confronto ETag debole non è supportato.  
  
 Nell'esempio seguente viene illustrato come utilizzare i metodi.  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;
        
        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a>Considerazioni sulla sicurezza  
 Le risposte a richieste che richiedono autorizzazione non devono essere memorizzate nella cache, perché l'autorizzazione non viene effettuata quando la risposta viene servita dalla cache.  La memorizzazione nella cache di tali risposte introdurrebbe una grave vulnerabilità per la sicurezza.  In genere, le richiede che richiedono autorizzazione forniscono dati specifici per gli utenti, pertanto la memorizzazione nella cache sul lato server non è vantaggiosa.  In tali situazioni, risulta più appropriata la memorizzazione nella cache sul lato client o, semplicemente, non eseguire alcuna memorizzazione nella cache.
