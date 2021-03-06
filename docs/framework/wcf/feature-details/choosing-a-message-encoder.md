---
title: Scelta di un codificatore di messaggi
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: 93024258ddcf76444d48a19c071b0a18248ea46b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645469"
---
# <a name="choosing-a-message-encoder"></a>Scelta di un codificatore di messaggi
In questo argomento vengono descritti i criteri per la scelta tra i codificatori di messaggi che sono inclusi in Windows Communication Foundation (WCF): file binario, testo e Message Transmission Optimization Mechanism (MTOM).  
  
 In WCF, specificare la modalità di trasferimento dati attraverso una rete tra endpoint per mezzo di una *associazione*, che è costituito da una sequenza di *elementi di associazione*. Un codificatore di messaggi è rappresentato da un elemento di associazione di codifica dei messaggi nello stack dell'associazione. Un'associazione include elementi facoltativi di associazione del protocollo, ad esempio un elemento di associazione di sicurezza o un elemento di associazione di messaggistica affidabile, un elemento di associazione di codifica dei messaggi obbligatorio e un elemento di associazione di trasporto obbligatorio.  
  
 L'elemento di associazione di codifica dei messaggi si trova sotto gli elementi facoltativi binding del protocollo e sopra l'elemento associazione del trasporto obbligatorio. Sul lato in uscita, un codificatore di messaggi serializza <xref:System.ServiceModel.Channels.Message> in uscita e lo passa al trasporto. Sul lato in ingresso, un codificatore di messaggi riceve il formato serializzato di un <xref:System.ServiceModel.Channels.Message> dal trasporto e lo passa al livello di protocollo superiore, se presente. In caso contrario, lo passa all'applicazione.  
  
 In caso di connessione a un client o a un server preesistente, potrebbe non essere possibile scegliere una particolare codifica dei messaggi dato che questi devono essere codificati come previsto dall'altro lato. Tuttavia, se si sta scrivendo un servizio WCF, è possibile esporre il servizio tramite più endpoint, ognuna delle quali Usa una diversa codifica dei messaggi. In tal modo i client possono scegliere la migliore codifica per conversare con il servizio sull'endpoint, e possono avere la flessibilità di scegliere la migliore codifica per se stessi. L'utilizzo di più endpoint consente anche di combinare i vantaggi di codifiche del messaggio diverse con altri elementi di associazione.  
  
## <a name="system-provided-encoders"></a>Codificatori forniti dal sistema  
 WCF include tre codificatori di messaggi, che sono rappresentati dalle tre classi seguenti:  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, il codificatore dei messaggi di testo, supporta codifica XML semplice e codifica SOAP. La modalità di codifica XML semplice del codificatore dei messaggi di testo è chiamata POX (Plain Old XML) per distinguerla dalla codifica SOAP basata su testo. Per abilitare POX, impostare la proprietà <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> su <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Usare il codificatore di messaggi di testo per interoperare con gli endpoint non WCF.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, il codificatore di messaggi binario, utilizza un formato binario compresso è ottimizzato per WCF alla comunicazione di WCF e pertanto non è interoperativo. Questo è anche il codificatore ad alte prestazioni la maggior parte di tutti i codificatori di WCF.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, l'elemento di associazione, specifica la codifica dei caratteri e la versione dei messaggi che utilizzano MTOM. MTOM è una tecnologia efficiente per la trasmissione di dati binari nei messaggi di WCF. Il codificatore MTOM cerca di creare un equilibrio tra efficienza e interoperabilità. La codifica MTOM trasmette la maggior parte del codice XML in formato testo, ma ottimizza grandi blocchi di dati binari trasmettendoli senza introdurre modifiche e senza convertirli in formato testo. In termini di efficienza, tra i codificatori di WCF, MTOM è (il più lento) compresi tra testo e binari (il più veloce).  
  
## <a name="how-to-choose-a-message-encoder"></a>Come scegliere un codificatore di messaggi  
 Nella tabella seguente vengono descritti i fattori comuni utilizzati per scegliere un codificatore di messaggi. Dare la priorità ai fattori che sono importanti per l'applicazione, quindi scegliere i codificatori più efficienti per tali fattori. Tenere anche conto di eventuali fattori aggiuntivi non elencati in questa tabella e qualsiasi codificatore di messaggi personalizzato che può essere richiesto nell'applicazione.  
  
|Fattore|Descrizione|Codificatori che supportano questo fattore|  
|------------|-----------------|---------------------------------------|  
|Set di caratteri supportati|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> e <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> supportano solo l'Unicode UTF8 e UTF16 (*big-endian* e *little-endian*) codifiche. Se sono richieste altre codifiche, ad esempio UTF7 o ASCII, deve essere utilizzato un codificatore personalizzato. Per un codificatore personalizzato di esempio, vedere [codificatore di messaggi personalizzato](https://go.microsoft.com/fwlink/?LinkId=119857).|Testo|  
|Ispezione|L'ispezione è la capacità di esaminare i messaggi durante la trasmissione. Le codifiche di testo, con o senza l'utilizzo di SOAP, consentono a numerose applicazioni di ispezionare e analizzare i messaggi senza utilizzare strumenti specializzati. Si noti che l'utilizzo della sicurezza del trasferimento, a livello di messaggio o di trasporto, influisce sulla capacità di ispezionare i messaggi. La riservatezza evita che un messaggio venga esaminato, mentre l'integrità lo protegge dalle modifiche.|Testo|  
|Affidabilità|L'affidabilità è la flessibilità di un codificatore nei confronti degli errori di trasmissione. L'affidabilità può essere fornita anche a livello di messaggio, trasporto o applicazione. Tutti i codificatori di WCF standard presuppongono che un altro livello stia fornendo l'affidabilità. Il codificatore non ha grandi capacità di recupero da un errore di trasmissione.|nessuno|  
|Semplicità|La semplicità rappresenta la facilità con cui è possibile creare codificatori e decodificatori per una specifica di codifica. Le codifiche di testo sono particolarmente vantaggiose per la semplicità. La codifica di testo POX, inoltre, ha anche il vantaggio che non richiede supporto per l'elaborazione di SOAP.|Testo (POX)|  
|Dimensione|La codifica determina la quantità di sovraccarico imposto sul contenuto. La dimensione dei messaggi codificati è direttamente correlata alla velocità effettiva massima delle operazioni del servizio. Le codifiche binarie in genere sono più compatte di quelle di testo. Quando la dimensione del messaggio è importante, prendere in considerazione anche la compressione del contenuto del messaggio durante la codifica. La compressione aumenta tuttavia gli oneri di elaborazione sia per il mittente che per il destinatario del messaggio.|Binario|  
|Flusso|Il flusso consente alle applicazioni di iniziare a elaborare un messaggio prima che sia arrivato tutto. Per utilizzare in modo efficiente un flusso, è necessario che i dati importanti di un messaggio siano disponibili all'inizio del messaggio, affinché l'applicazione ricevente non debba attenderne l'arrivo. Le applicazioni che utilizzano il trasferimento tramite flussi, inoltre, devono organizzare i dati nel messaggio in modo incrementale affinché il contenuto non abbia dipendenze in avanti. In molti casi, è necessario trovare un compromesso tra l'utilizzo di un flusso e la riduzione massima delle dimensioni di trasferimento di quel contenuto.|nessuno|  
|Supporto di strumenti di terze parti|Le aree di supporto per una codifica comprendono sviluppo e diagnosi. Gli sviluppatori di terze parti hanno investito massicciamente in librerie e toolkit per la gestione dei messaggi codificati nel formato POX.|Testo (POX)|  
|Interoperabilità|Questo fattore si riferisce alla capacità di un codificatore di WCF per interagire con i servizi non WCF.|Testo<br /><br /> MTOM (parziale)|  
  
Nota: Quando si utilizza il codificatore binario, usare l'impostazione IgnoreWhitespace durante la creazione di un elemento XMLReader avrà alcun effetto.  Ad esempio, se si effettua quanto riportato di seguito in un'operazione del servizio:  

```csharp
public void OperationContract(XElement input)
{
    Console.WriteLine("{0}", input.Value);
    int counter = 0;
    var xreader = input.CreateReader();
    var reader = XmlReader.Create(xreader, new XmlReaderSettings() { IgnoreWhitespace = true });
    while (reader.Read())
    {
        counter++;
    }

    Console.WriteLine("Read {0} lines with reader", counter);
}
```  
  
L'impostazione IgnoreWhitespace viene ignorata.  
  
## <a name="compression-and-the-binary-encoder"></a>Compressione e codificatore binario

A partire da WCF 4.5, il codificatore binario WCF aggiunge il supporto per la compressione. Questo consente di utilizzare l'algoritmo gzip/deflate per inviare messaggi compressi da un client WCF, nonché rispondere con messaggi compressi da un servizio WCF self-hosted. Questa funzionalità consente la compressione sui trasporti TCP e HTTP. Un servizio WCF ospitato da IIS può sempre essere abilitato per l'invio di risposte compresse configurando il server host di IIS. Il tipo di compressione è configurato con la proprietà <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType>. Questa proprietà è impostata su uno dei valori dell'enumerazione <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>:

- <xref:System.ServiceModel.Channels.CompressionFormat.Deflate>
- <xref:System.ServiceModel.Channels.CompressionFormat.GZip>
- <xref:System.ServiceModel.Channels.CompressionFormat.None>
  
Poiché questa proprietà viene esposta solo su binaryMessageEncodingBindingElement, sarà necessario creare un'associazione personalizzata simile al seguente per usare questa funzionalità:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Il client sia il servizio prevede l'accettazione inviare e ricevere messaggi compressi e pertanto la proprietà compressionFormat deve essere configurata sull'elemento binaryMessageEncoding sia client di servizio. Viene generata un'eccezione ProtocolException se per la compressione è configurato un solo lato, vale a dire o il servizio o il client. Pertanto, è necessario considerare con attenzione l'abilitazione della compressione. La compressione è particolarmente utile se la larghezza di banda della rete costituisce un collo di bottiglia. Nel caso in cui la CPU sia un collo di bottiglia, la compressione diminuirà la velocità effettiva. È necessario effettuare prove appropriate in un ambiente simulato per verificare eventuali vantaggi per l'applicazione  
  
## <a name="see-also"></a>Vedere anche

- [Associazioni](../../../../docs/framework/wcf/feature-details/bindings.md)
