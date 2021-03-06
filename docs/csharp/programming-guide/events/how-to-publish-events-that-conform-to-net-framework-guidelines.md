---
title: Come pubblicare gli eventi conformi alle linee guida di .NET Framework - Guida per programmatori C
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 90c079b9f7dbf2a1d963b7eee4447145d7a10432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167534"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Come pubblicare gli eventi conformi alle linee guida di .NET Framework (Guida per programmatori C
La procedura seguente illustra come aggiungere eventi che seguono lo schema .NET Framework standard a classi e struct. Tutti gli eventi della libreria di classi .NET Framework si basano sul delegato <xref:System.EventHandler> che è definito nel modo seguente:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> .NET Framework 2.0 introduce una versione generica di questo delegato, <xref:System.EventHandler%601>. Negli esempi seguenti viene illustrato l'uso di entrambe le versioni.  
  
 Anche se gli eventi nelle classi che vengono definite possono essere basati su qualsiasi tipo di delegato valido, inclusi i delegati che restituiscono un valore, è in genere consigliabile basare gli eventi sullo schema .NET Framework usando <xref:System.EventHandler>, come illustrato nell'esempio riportato di seguito.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Per pubblicare eventi basati sul modello EventHandler  
  
1. (Salta questo passaggio e vai al passaggio 3a se non devi inviare dati personalizzati con il tuo evento.) Dichiarare la classe per i dati personalizzati in un ambito visibile sia alle classi del server di pubblicazione che a quelle del sottoscrittore. Aggiungere i membri necessari per contenere i dati di evento personalizzati. In questo esempio viene restituita una semplice stringa.  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }
    }  
    ```  
  
2. (Saltare questo passaggio se si <xref:System.EventHandler%601> utilizza la versione generica di .) Dichiarare un delegato nella classe di pubblicazione. Assegnargli un nome che termini con *EventHandler*. Il secondo parametro specifica il tipo EventArgs personalizzato.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. Dichiarare l'evento nella classe di pubblicazione usando uno dei passaggi seguenti.  
  
    1. Se non si ha una classe EventArgs personalizzata, il tipo di evento sarà il delegato EventHandler non generico. Non è necessario dichiarare il delegato perché è già dichiarato nello spazio dei nomi <xref:System>, incluso quando si crea il progetto C#. Aggiungere il codice seguente alla classe dell'editore.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. Se si usa la versione non generica di <xref:System.EventHandler> e si ha una classe personalizzata derivata da <xref:System.EventArgs>, dichiarare l'evento all'interno della classe di pubblicazione e usare il delegato del passaggio 2 come tipo.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. Se si usa la versione generica, non è necessario un delegato personalizzato. Al contrario, nella classe di pubblicazione specificare il tipo di evento come `EventHandler<CustomEventArgs>`, sostituendo il nome della classe racchiuso tra parentesi acute.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Esempio  
 L'esempio seguente illustra i passaggi precedenti usando una classe EventArgs personalizzata e <xref:System.EventHandler%601> come tipo di evento.  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Delegate>
- [Guida per programmatori C#](../index.md)
- [Events](./index.md)
- [Delegati](../delegates/index.md)
