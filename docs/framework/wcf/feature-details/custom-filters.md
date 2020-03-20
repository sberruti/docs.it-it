---
title: Filtri personalizzati
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ae020173544372c3ce097c8ac57e53f3fde37514
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185215"
---
# <a name="custom-filters"></a>Filtri personalizzati
I filtri personalizzati consentono di definire la logica corrispondente che non è possibile conseguire utilizzando i filtri messaggi forniti dal sistema. È ad esempio possibile creare un filtro personalizzato che esegue l'hash di un particolare elemento del messaggio, quindi esamina il valore per determinare se il filtro debba restituire True o False.  
  
## <a name="implementation"></a>Implementazione  
 Un filtro personalizzato rappresenta un'implementazione della classe di base astratta <xref:System.ServiceModel.Dispatcher.MessageFilter>. In caso di implementazione del filtro personalizzato, il costruttore può facoltativamente accettare un solo parametro stringa. Tale parametro contiene le informazioni di configurazione passate al costruttore MessageFilter per fornire qualsiasi valore o configurazione necessaria al filtro al runtime per eseguire corrispondenze. Potrebbe ad esempio essere utilizzato per fornire un valore che il filtro cerca all'interno del messaggio valutato. Nell'esempio seguente viene illustrata un'implementazione di base di un filtro messaggi personalizzato che accetta un parametro stringa:  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
> In un'implementazione effettiva, il Match metodo(i) contiene la logica che esaminerà il messaggio per determinare se questo filtro messaggi deve restituire **true** o **false**.  
  
### <a name="performance"></a>Prestazioni  
 Quando si implementa un filtro personalizzato, è importante considerare la durata di tempo massima richiesta per il completamento della valutazione di un messaggio da parte del filtro. Poiché un messaggio può essere valutato rispetto a più filtri prima che venga individuata una corrispondenza, è importante assicurarsi che non si verifichi il timeout della richiesta del client prima della valutazione di tutti i filtri. Un filtro personalizzato deve pertanto contenere solo il codice necessario per valutare il contenuto o gli attributi di un messaggio in modo da determinare se corrisponde o meno ai criteri di filtro.  
  
 In generale, quando si implementa un filtro personalizzato è necessario evitare quanto segue:  
  
- I/O, ad esempio salvataggio dei dati su disco o in un database.  
  
- Elaborazione non necessaria, ad esempio cicli su più record in un documento.  
  
- Operazioni di blocco, ad esempio chiamate che comportano l'acquisizione di un blocco su risorse condivise o l'esecuzione di ricerche in un database.  
  
 Prima di utilizzare un filtro personalizzato in un ambiente di produzione, è necessario eseguire test delle prestazioni per determinare la durata di tempo media richiesta dal filtro per la valutazione di un messaggio. In combinazione con il tempo di elaborazione medio degli altri filtri utilizzati nella tabella dei filtri, sarà in tal modo possibile determinare in maniera accurata il valore di timeout massimo che deve essere specificato dall'applicazione client.  
  
## <a name="usage"></a>Uso  
 Per utilizzare il filtro personalizzato con il servizio di routing, è necessario aggiungerlo alla tabella dei filtri specificando una nuova voce di filtro di tipo "Personalizzato", il nome completo del tipo di messaggio e il nome dell'assembly.  Come nel caso di altri elementi MessageFilters, è possibile specificare la stringa filterData che verrà passata al costruttore del filtro personalizzato.  
  
 Negli esempi seguenti viene illustrato l'utilizzo di un filtro personalizzato con il servizio di routing:  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"
            customType="CustomAssembly.MyMessageFilter,
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
