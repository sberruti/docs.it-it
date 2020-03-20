---
title: Errore durante la gestione delle attività asincrone
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: c63ce231687b03bdba57edd38c32270eabeff834
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182945"
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="0dabc-102">Errore durante la gestione delle attività asincrone</span><span class="sxs-lookup"><span data-stu-id="0dabc-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="0dabc-103">Fornire la gestione degli errori in <xref:System.Activities.AsyncCodeActivity> implica risolvere gli errori tramite il sistema di callback dell'attività.</span><span class="sxs-lookup"><span data-stu-id="0dabc-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="0dabc-104">In questo argomento viene descritto come restituire un errore generato in un'unica operazione asincrona all'host, usando come esempio l'attività SendMail.</span><span class="sxs-lookup"><span data-stu-id="0dabc-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="0dabc-105">Restituisce un errore generato in un'attività asincrona all'host</span><span class="sxs-lookup"><span data-stu-id="0dabc-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="0dabc-106">La restituzione all'host di un errore in un'operazione asincrona nell'esempio di attività SendMail include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="0dabc-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="0dabc-107">Aggiungere una proprietà Exception alla classe `SendMailAsyncResult`.</span><span class="sxs-lookup"><span data-stu-id="0dabc-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="0dabc-108">Copiare l'errore generato a tale proprietà nel gestore eventi `SendCompleted`.</span><span class="sxs-lookup"><span data-stu-id="0dabc-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="0dabc-109">Generare l'eccezione nel gestore eventi `EndExecute`.</span><span class="sxs-lookup"><span data-stu-id="0dabc-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="0dabc-110">Di seguito è riportato il codice risultante.</span><span class="sxs-lookup"><span data-stu-id="0dabc-110">The resulting code is as follows.</span></span>  
  
```csharp  
class SendMailAsyncResult : IAsyncResult  
        {  
            …  
            public Exception Error { get; set; }
            …  
            void SendCompleted(object sender, AsyncCompletedEventArgs e)  
            {  
                Error = e.Error;  
                this.asyncWaitHandle.Set();  
                callback(this);  
            }  
         }  
  
    public sealed class SendMail: AsyncCodeActivity  
    {  
         …  
        protected override void EndExecute(AsyncCodeActivityContext context, IAsyncResult result)  
        {  
            SendMailAsyncResult sendMailResult = result as SendMailAsyncResult;  
            if (sendMailResult != null && sendMailResult.Error != null)  
                throw sendMailResult.Error;
        }  
    }  
```
