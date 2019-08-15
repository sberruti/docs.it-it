---
title: Implementazione dei tentativi di chiamate HTTP con backoff esponenziale con Polly
description: Informazioni su come gestire gli errori HTTP con Polly e HttpClientFactory.
ms.date: 01/07/2019
ms.openlocfilehash: aa500b5525eff9f0bbf91bf98de8945f7c84704f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674568"
---
# <a name="implement-http-call-retries-with-exponential-backoff-with-httpclientfactory-and-polly-policies"></a><span data-ttu-id="9f007-103">Implementazione dei tentativi di chiamate HTTP con backoff esponenziale con i criteri di Polly e HttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="9f007-103">Implement HTTP call retries with exponential backoff with HttpClientFactory and Polly policies</span></span>

<span data-ttu-id="9f007-104">L'approccio consigliato per i tentativi con backoff esponenziale prevede l'uso di librerie .NET più avanzate, ad esempio la [libreria open source Polly](https://github.com/App-vNext/Polly).</span><span class="sxs-lookup"><span data-stu-id="9f007-104">The recommended approach for retries with exponential backoff is to take advantage of more advanced .NET libraries like the open-source [Polly library](https://github.com/App-vNext/Polly).</span></span>

<span data-ttu-id="9f007-105">Polly è una libreria .NET che fornisce funzionalità di resilienza e di gestione degli errori temporanei.</span><span class="sxs-lookup"><span data-stu-id="9f007-105">Polly is a .NET library that provides resilience and transient-fault handling capabilities.</span></span> <span data-ttu-id="9f007-106">È possibile implementare queste funzionalità applicando i criteri di Polly, ad esempio Retry, Circuit Breaker, Bulkhead Isolation, Timeout e Fallback.</span><span class="sxs-lookup"><span data-stu-id="9f007-106">You can implement those capabilities by applying Polly policies such as Retry, Circuit Breaker, Bulkhead Isolation, Timeout, and Fallback.</span></span> <span data-ttu-id="9f007-107">La libreria Polly è compatibile con .NET 4.x e .NET Standard Library 1.0, che supporta .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9f007-107">Polly targets .NET 4.x and the .NET Standard Library 1.0 (which supports .NET Core).</span></span>

<span data-ttu-id="9f007-108">L'uso della libreria Polly con il proprio codice personalizzato con HttpClient, tuttavia, può essere un'operazione estremamente complessa.</span><span class="sxs-lookup"><span data-stu-id="9f007-108">However, using Polly’s library with your own custom code with HttpClient can be significantly complex.</span></span> <span data-ttu-id="9f007-109">Nella versione originale di eShopOnContainers si è verificato un [blocco predefinito di ResilientHttpClient](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) basato su Polly.</span><span class="sxs-lookup"><span data-stu-id="9f007-109">In the original version of eShopOnContainers, there was a [ResilientHttpClient building-block](https://github.com/dotnet-architecture/eShopOnContainers/commit/0c317d56f3c8937f6823cf1b45f5683397274815#diff-e6532e623eb606a0f8568663403e3a10) based on Polly.</span></span> <span data-ttu-id="9f007-110">Con il rilascio di [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), tuttavia, la comunicazione HTTP resiliente è diventata molto più semplice da implementare, quindi il blocco predefinito è stato deprecato in eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9f007-110">But with the release of [HttpClientFactory](use-httpclientfactory-to-implement-resilient-http-requests.md), resilient HTTP communication has become much simpler to implement, so that building-block was deprecated from eShopOnContainers.</span></span> 

<span data-ttu-id="9f007-111">I passaggi seguenti mostrano come usare i tentativi HTTP con Polly integrato in HttpClientFactory, come spiegato nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="9f007-111">The following steps show how you can use Http retries with Polly integrated into HttpClientFactory, which is explained in the previous section.</span></span>

<span data-ttu-id="9f007-112">**Fare riferimento ai pacchetti di ASP.NET Core 2.2**</span><span class="sxs-lookup"><span data-stu-id="9f007-112">**Reference the ASP.NET Core 2.2 packages**</span></span>

<span data-ttu-id="9f007-113">`HttpClientFactory` è disponibile sin da .NET Core 2.1, tuttavia è consigliabile usare i pacchetti di ASP.NET Core 2.2 più recenti da NuGet nel progetto.</span><span class="sxs-lookup"><span data-stu-id="9f007-113">`HttpClientFactory` is available since .NET Core 2.1 however we recommend you to use the latest ASP.NET Core 2.2 packages from NuGet in your project.</span></span> <span data-ttu-id="9f007-114">In genere è necessario il metapacchetto `AspNetCore` e il pacchetto di estensione `Microsoft.Extensions.Http.Polly`.</span><span class="sxs-lookup"><span data-stu-id="9f007-114">You typically need the `AspNetCore` metapackage, and the extension package `Microsoft.Extensions.Http.Polly`.</span></span>

<span data-ttu-id="9f007-115">**Configurare un client con i criteri di ripetizione di Polly, in Startup**</span><span class="sxs-lookup"><span data-stu-id="9f007-115">**Configure a client with Polly’s Retry policy, in Startup**</span></span>

<span data-ttu-id="9f007-116">Come illustrato nelle sezioni precedenti, è necessario definire una configurazione HttpClient client denominata o tipizzata nel metodo Startup.ConfigureServices(...) standard, ma ora si aggiunge il codice incrementale che specifica i criteri dei tentativi HTTP con backoff esponenziale, come riportato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9f007-116">As shown in previous sections, you need to define a named or typed client HttpClient configuration in your standard Startup.ConfigureServices(...) method, but now, you add incremental code specifying the policy for the Http retries with exponential backoff, as below:</span></span>

```csharp
//ConfigureServices()  - Startup.cs
services.AddHttpClient<IBasketService, BasketService>()
        .SetHandlerLifetime(TimeSpan.FromMinutes(5))  //Set lifetime to five minutes
        .AddPolicyHandler(GetRetryPolicy());
```

<span data-ttu-id="9f007-117">Il metodo **AddPolicyHandler()** aggiunge i criteri agli oggetti `HttpClient` che verranno usati.</span><span class="sxs-lookup"><span data-stu-id="9f007-117">The **AddPolicyHandler()** method is what adds policies to the `HttpClient` objects you'll use.</span></span> <span data-ttu-id="9f007-118">In questo caso si aggiungono i criteri di Polly per i tentativi HTTP con backoff esponenziale.</span><span class="sxs-lookup"><span data-stu-id="9f007-118">In this case, it's adding a Polly’s policy for Http Retries with exponential backoff.</span></span>

<span data-ttu-id="9f007-119">Per avere un approccio più modulare, i criteri di ripetizione HTTP possono essere definiti in un metodo separato nel file `Startup.cs`, come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="9f007-119">To have a more modular approach, the Http Retry Policy can be defined in a separate method within the `Startup.cs` file, as shown in the following code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2,
                                                                    retryAttempt)));
}
```

<span data-ttu-id="9f007-120">Con Polly è possibile definire i criteri di ripetizione con il numero di tentativi, la configurazione del backoff esponenziale e le azioni da eseguire quando si verifica un'eccezione HTTP, ad esempio la registrazione dell'errore.</span><span class="sxs-lookup"><span data-stu-id="9f007-120">With Polly, you can define a Retry policy with the number of retries, the exponential backoff configuration, and the actions to take when there's an HTTP exception, such as logging the error.</span></span> <span data-ttu-id="9f007-121">In questo caso, i criteri vengono configurati per provare sei volte con un tentativo esponenziale, a partire da due secondi.</span><span class="sxs-lookup"><span data-stu-id="9f007-121">In this case, the policy is configured to try six times with an exponential retry, starting at two seconds.</span></span> 

<span data-ttu-id="9f007-122">quindi proveranno per sei volte e i secondi tra ogni tentativo saranno esponenziali, a partire da due secondi.</span><span class="sxs-lookup"><span data-stu-id="9f007-122">so it will try six times and the seconds between each retry will be exponential, starting on two seconds.</span></span>

## <a name="add-a-jitter-strategy-to-the-retry-policy"></a><span data-ttu-id="9f007-123">Aggiungere una strategia di instabilità ai criteri di ripetizione</span><span class="sxs-lookup"><span data-stu-id="9f007-123">Add a jitter strategy to the retry policy</span></span>

<span data-ttu-id="9f007-124">I normali criteri di ripetizione possono influire sul sistema quando scalabilità e concorrenza sono elevate e sono presenti molti conflitti.</span><span class="sxs-lookup"><span data-stu-id="9f007-124">A regular Retry policy can impact your system in cases of high concurrency and scalability and under high contention.</span></span> <span data-ttu-id="9f007-125">Per risolvere i picchi di tentativi simili provenienti da molti client in caso di interruzioni parziali, una soluzione alternativa efficace consiste nell'aggiungere una strategia di instabilità all'algoritmo o ai criteri di ripetizione.</span><span class="sxs-lookup"><span data-stu-id="9f007-125">To overcome peaks of similar retries coming from many clients in case of partial outages, a good workaround is to add a jitter strategy to the retry algorithm/policy.</span></span> <span data-ttu-id="9f007-126">Ciò può migliorare le prestazioni complessive del sistema end-to-end grazie all'aggiunta di casualità nel backoff esponenziale.</span><span class="sxs-lookup"><span data-stu-id="9f007-126">This can improve the overall performance of the end-to-end system by adding randomness to the exponential backoff.</span></span> <span data-ttu-id="9f007-127">Permette di diluire i picchi quando si verificano problemi.</span><span class="sxs-lookup"><span data-stu-id="9f007-127">This spreads out the spikes when issues arise.</span></span> <span data-ttu-id="9f007-128">Quando si usano criteri Polly semplici, il codice per implementare l'instabilità potrebbe somigliare a quello nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="9f007-128">When you use a plain Polly policy, code to implement jitter could look like the following example:</span></span>

```csharp
Random jitterer = new Random(); 
Policy
  .Handle<HttpResponseException>() // etc
  .WaitAndRetry(5,    // exponential back-off plus some jitter
      retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt))  
                    + TimeSpan.FromMilliseconds(jitterer.Next(0, 100)) 
  );
```

## <a name="additional-resources"></a><span data-ttu-id="9f007-129">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="9f007-129">Additional resources</span></span>

- <span data-ttu-id="9f007-130">**Retry pattern** (Modello di ripetizione dei tentativi)</span><span class="sxs-lookup"><span data-stu-id="9f007-130">**Retry pattern**</span></span>  
  [https://docs.microsoft.com/azure/architecture/patterns/retry](/azure/architecture/patterns/retry)

- <span data-ttu-id="9f007-131">**Polly e HttpClientFactory**</span><span class="sxs-lookup"><span data-stu-id="9f007-131">**Polly and HttpClientFactory**</span></span>  
  <https://github.com/App-vNext/Polly/wiki/Polly-and-HttpClientFactory>

- <span data-ttu-id="9f007-132">**Polly (libreria .NET con funzionalità di resilienza e di gestione degli errori temporanei)**</span><span class="sxs-lookup"><span data-stu-id="9f007-132">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <https://github.com/App-vNext/Polly>

- <span data-ttu-id="9f007-133">**Marc Brooker. Jitter: Making Things Better With Randomness** (Instabilità: come migliorare l'esecuzione con la casualità)</span><span class="sxs-lookup"><span data-stu-id="9f007-133">**Marc Brooker. Jitter: Making Things Better With Randomness**</span></span>  
  <https://brooker.co.za/blog/2015/03/21/backoff.html>

>[!div class="step-by-step"]
><span data-ttu-id="9f007-134">[Precedente](explore-custom-http-call-retries-exponential-backoff.md)
>[Successivo](implement-circuit-breaker-pattern.md)</span><span class="sxs-lookup"><span data-stu-id="9f007-134">[Previous](explore-custom-http-call-retries-exponential-backoff.md)
[Next](implement-circuit-breaker-pattern.md)</span></span>