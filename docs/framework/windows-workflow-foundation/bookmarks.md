---
title: Segnalibri - WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: c5bd8130ee623599e80014777baf92986c3b6969
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183016"
---
# <a name="bookmarks"></a>Segnalibri
I segnalibri rappresentano il meccanismo che consente a un'attività di attendere passivamente l'input senza mantenere un thread del flusso di lavoro. Quando un'attività segnala che sta attendendo stimoli, può creare un segnalibro. Ciò indica al runtime che l'esecuzione dell'attività non deve essere considerata completa anche quando viene restituito il metodo attualmente in esecuzione (che ha creato l'oggetto <xref:System.Activities.Bookmark>).  
  
## <a name="bookmark-basics"></a>Informazioni introduttive sul segnalibro  
 Un oggetto <xref:System.Activities.Bookmark> rappresenta un punto in cui l'esecuzione può essere ripresa (e attraverso cui è possibile recapitare l'input) all'interno di un'istanza del flusso di lavoro. In genere, viene assegnato un nome a un oggetto <xref:System.Activities.Bookmark> e il codice esterno (host o estensione) è responsabile della ripresa del segnalibro con i dati attinenti. Quando un oggetto <xref:System.Activities.Bookmark> viene ripreso, l'esecuzione del flusso di lavoro pianifica il delegato <xref:System.Activities.BookmarkCallback> associato a tale oggetto <xref:System.Activities.Bookmark> al momento della creazione.  
  
## <a name="bookmark-options"></a>Opzioni del segnalibro  
 La classe <xref:System.Activities.BookmarkOptions> specifica il tipo di oggetto <xref:System.Activities.Bookmark> in corso di creazione. I valori possibili che non si escludono a vicenda sono <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume> e <xref:System.Activities.BookmarkOptions.NonBlocking>. Usare il valore <xref:System.Activities.BookmarkOptions.None>, ovvero l'impostazione predefinita, quando si crea un oggetto <xref:System.Activities.Bookmark> che si presume debba essere ripreso una sola volta. Usare il valore <xref:System.Activities.BookmarkOptions.MultipleResume> quando si crea un oggetto <xref:System.Activities.Bookmark> che può essere ripreso più volte. Usare un valore <xref:System.Activities.BookmarkOptions.NonBlocking> quando si crea un oggetto <xref:System.Activities.Bookmark> che potrebbe non essere mai ripreso. A differenza dei segnalibri creati usando l'oggetto <xref:System.Activities.BookmarkOptions> predefinito, i segnalibri <xref:System.Activities.BookmarkOptions.NonBlocking> non impediscono il completamento di un'attività.  
  
## <a name="bookmark-resumption"></a>Ripresa del segnalibro  
 I segnalibri possono essere ripresi dal codice all'esterno di un flusso di lavoro usando uno degli overload <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>. In questo esempio viene creata un'attività `ReadLine`. In caso di esecuzione, l'attività `ReadLine` crea un oggetto <xref:System.Activities.Bookmark>, registra un callback, quindi attende la ripresa dell'oggetto <xref:System.Activities.Bookmark>. Una volta ripresa, l'attività `ReadLine` assegna i dati passati con l'oggetto <xref:System.Activities.Bookmark> al relativo argomento <xref:System.Activities.Activity%601.Result%2A>.  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 In questo esempio viene creato un flusso di lavoro che usa l'attività `ReadLine` per rilevare il nome dell'utente e visualizzarlo nella finestra della console. L'applicazione host esegue il lavoro effettivo di rilevamento dell'input e lo passa al flusso di lavoro riprendendo l'oggetto <xref:System.Activities.Bookmark>.  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 Quando l'attività `ReadLine` viene eseguita, crea un oggetto <xref:System.Activities.Bookmark> denominato `UserName` e attende la ripresa del segnalibro. L'host raccoglie i dati desiderati, quindi riprende l'oggetto <xref:System.Activities.Bookmark>. Il flusso di lavoro viene ripreso, ne viene visualizzato il nome, quindi viene completato. Si noti che non è necessario alcun codice di sincronizzazione per la ripresa del segnalibro. Un oggetto <xref:System.Activities.Bookmark> può essere ripreso solo quando il flusso di lavoro è inattivo e, in caso contrario, la chiamata al metodo <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> viene bloccata finché il flusso di lavoro non diventa inattivo.  
  
## <a name="bookmark-resumption-result"></a>Risultato della ripresa del segnalibro  
 Il metodo <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> restituisce un valore dell'enumerazione <xref:System.Activities.BookmarkResumptionResult> per indicare i risultati della richiesta di ripresa del segnalibro. I possibili valori restituiti sono <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady> e <xref:System.Activities.BookmarkResumptionResult.NotFound>. Gli host e le estensioni possono usare questo valore per stabilire come procedere.
