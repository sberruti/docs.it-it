---
title: Trasferimento
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: e0ebfff97cd33e7a588a1ab92399a97a0fbec039
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185702"
---
# <a name="transfer"></a><span data-ttu-id="8a195-102">Trasferimento</span><span class="sxs-lookup"><span data-stu-id="8a195-102">Transfer</span></span>
<span data-ttu-id="8a195-103">In questo argomento viene descritto il trasferimento nel modello di traccia delle attività di Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8a195-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="8a195-104">Definizione di trasferimento</span><span class="sxs-lookup"><span data-stu-id="8a195-104">Transfer Definition</span></span>  
 <span data-ttu-id="8a195-105">I trasferimenti tra le attività rappresentano le relazioni causali tra eventi nelle attività correlate all'interno di endpoint.</span><span class="sxs-lookup"><span data-stu-id="8a195-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="8a195-106">Due attività sono correlate con i trasferimenti quando controllano i flussi tra queste attività, ad esempio, una chiamata al metodo che supera i limiti di attività.</span><span class="sxs-lookup"><span data-stu-id="8a195-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="8a195-107">In WCF, quando i byte sono in ingresso nel servizio, l'attività Listen At viene trasferita all'attività Receive Bytes in cui viene creato l'oggetto messaggio.</span><span class="sxs-lookup"><span data-stu-id="8a195-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="8a195-108">Per un elenco degli scenari di analisi end-to-end e della rispettiva progettazione di attività e tracciatura, vedere Scenari di [traccia end-to-end](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="8a195-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="8a195-109">Per emettere tracce di trasferimento, usare l'impostazione `ActivityTracing` nell'origine di traccia, come illustrato nel codice di configurazione seguente.</span><span class="sxs-lookup"><span data-stu-id="8a195-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="8a195-110">Utilizzo del trasferimento per correlare le attività all'interno di endpoint</span><span class="sxs-lookup"><span data-stu-id="8a195-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="8a195-111">Attività e trasferimenti consentono all'utente di individuare probabilisticamente la causa radice di un errore.</span><span class="sxs-lookup"><span data-stu-id="8a195-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="8a195-112">Se, ad esempio, vi sono trasferimenti tra le attività M e N rispettivamente nei componenti M e N e si verifica un arresto anomalo in N subito dopo il trasferimento a M, se ne può dedurre che ciò è probabilmente dovuto a N che passa indietro i dati a M.</span><span class="sxs-lookup"><span data-stu-id="8a195-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="8a195-113">Una traccia di trasferimento viene emessa dall'attività M all'attività N quando è presente un flusso di controllo tra M e N. N, ad esempio, esegue un lavoro per M a causa di una chiamata al metodo che attraversa i limiti delle attività.</span><span class="sxs-lookup"><span data-stu-id="8a195-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="8a195-114">N potrebbe esistere già o può essere stato creato.</span><span class="sxs-lookup"><span data-stu-id="8a195-114">N may already exist or has been created.</span></span> <span data-ttu-id="8a195-115">N viene generato da M quando N è una nuova attività che esegue dei lavori per M.</span><span class="sxs-lookup"><span data-stu-id="8a195-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="8a195-116">Un trasferimento da M a N potrebbe non essere seguito da un trasferimento da N a M. Ciò accade perché M può generare lavoro in N e non tiene traccia di quando N lo completa.</span><span class="sxs-lookup"><span data-stu-id="8a195-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="8a195-117">Di fatto, M può terminare prima che N completi l'attività.</span><span class="sxs-lookup"><span data-stu-id="8a195-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="8a195-118">Ciò si verifica nell'attività "Open ServiceHost" (M) che genera le attività del listener (N) e quindi termina.</span><span class="sxs-lookup"><span data-stu-id="8a195-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="8a195-119">Un ritrasferimento da N a M significa che N ha completato il lavoro correlato a M.</span><span class="sxs-lookup"><span data-stu-id="8a195-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="8a195-120">N può continuare a eseguire altre elaborazioni non correlate a M, ad esempio, un'attività dell'autenticatore esistente (N) che continua a ricevere richieste di accesso (M) da diverse attività di accesso.</span><span class="sxs-lookup"><span data-stu-id="8a195-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="8a195-121">Tra attività M e N non esiste necessariamente una relazione di annidamento. Ciò è dovuto a due ragioni.</span><span class="sxs-lookup"><span data-stu-id="8a195-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="8a195-122">Innanzitutto, quando l'attività M non controlla l'elaborazione effettiva eseguita in N anche se M ha avviato N. In secondo luogo, quando N esiste già.</span><span class="sxs-lookup"><span data-stu-id="8a195-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="8a195-123">Esempio di trasferimenti</span><span class="sxs-lookup"><span data-stu-id="8a195-123">Example of Transfers</span></span>  
 <span data-ttu-id="8a195-124">Seguono due esempi del trasferimento.</span><span class="sxs-lookup"><span data-stu-id="8a195-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="8a195-125">Quando si crea un host del servizio, il costruttore ottiene il controllo dal codice chiamante oppure il codice chiamante viene trasferito al costruttore.</span><span class="sxs-lookup"><span data-stu-id="8a195-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="8a195-126">Al termine dell'esecuzione, il costruttore restituisce il controllo al codice chiamante oppure trasferisce di nuovo l'esecuzione al codice chiamante.</span><span class="sxs-lookup"><span data-stu-id="8a195-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="8a195-127">Questo è il caso di una relazione annidata.</span><span class="sxs-lookup"><span data-stu-id="8a195-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="8a195-128">Quando un listener inizia a elaborare i dati di trasporto, crea un nuovo thread e consegna all'attività di ricezione byte il contesto appropriato per l'elaborazione, passando controllo e dati.</span><span class="sxs-lookup"><span data-stu-id="8a195-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="8a195-129">Quando quel thread ha terminato di elaborare la richiesta, l'attività di ricezione byte non passa indietro nulla al listener.</span><span class="sxs-lookup"><span data-stu-id="8a195-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="8a195-130">In questo caso, vi è un trasferimento in ingresso ma nessun trasferimento in uscita della nuova attività del thread.</span><span class="sxs-lookup"><span data-stu-id="8a195-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="8a195-131">Le due attività sono correlate ma non annidate.</span><span class="sxs-lookup"><span data-stu-id="8a195-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="8a195-132">Sequenza di trasferimento di attività</span><span class="sxs-lookup"><span data-stu-id="8a195-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="8a195-133">Una sequenza di trasferimento di attività ben formata comprende i passaggi seguenti.</span><span class="sxs-lookup"><span data-stu-id="8a195-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="8a195-134">Iniziare una nuova attività, che consiste nel selezionare un nuovo gAId.</span><span class="sxs-lookup"><span data-stu-id="8a195-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="8a195-135">Emettere una traccia di trasferimento a quel nuovo gAId dall'ID attività corrente</span><span class="sxs-lookup"><span data-stu-id="8a195-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="8a195-136">Impostare il nuovo ID in TLS</span><span class="sxs-lookup"><span data-stu-id="8a195-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="8a195-137">Emettere una traccia di inizio per indicare l'inizio della nuova attività.</span><span class="sxs-lookup"><span data-stu-id="8a195-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="8a195-138">Il ritorno all'attività originale è costituito dai passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="8a195-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="8a195-139">Emettere una traccia di trasferimento al gAId originale</span><span class="sxs-lookup"><span data-stu-id="8a195-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="8a195-140">Emettere una traccia di interruzione per indicare la fine della nuova attività</span><span class="sxs-lookup"><span data-stu-id="8a195-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="8a195-141">Impostare TLS sul vecchio gAId.</span><span class="sxs-lookup"><span data-stu-id="8a195-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="8a195-142">Nell'esempio di codice seguente viene illustrato come procedere.</span><span class="sxs-lookup"><span data-stu-id="8a195-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="8a195-143">In questo esempio si presuppone che venga effettuata una chiamata di blocco durante il trasferimento alla nuova attività e sono incluse tracce di sospensione/ripresa.</span><span class="sxs-lookup"><span data-stu-id="8a195-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a195-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8a195-144">See also</span></span>

- [<span data-ttu-id="8a195-145">Configurazione delle funzionalità di traccia</span><span class="sxs-lookup"><span data-stu-id="8a195-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="8a195-146">Uso del visualizzatore di tracce dei servizi per la visualizzazione di tracce correlate e la risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="8a195-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="8a195-147">Scenari di analisi end-to-end</span><span class="sxs-lookup"><span data-stu-id="8a195-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="8a195-148">Strumento Visualizzatore di tracce dei servizi (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="8a195-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
