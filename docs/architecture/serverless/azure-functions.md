---
title: Funzioni di Azure-app senza server
description: Funzioni di Azure offre funzionalità senza server tra più linguaggiC#(, JavaScript, Java) e piattaforme per fornire codice di scalabilità immediata basato sugli eventi.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920970"
---
# <a name="azure-functions"></a><span data-ttu-id="1ad5f-103">Funzioni di Azure</span><span class="sxs-lookup"><span data-stu-id="1ad5f-103">Azure Functions</span></span>

<span data-ttu-id="1ad5f-104">Funzioni di Azure offre un'esperienza di calcolo senza server.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="1ad5f-105">Una funzione viene richiamata da un *trigger* , ad esempio l'accesso a un endpoint HTTP o un timer, ed esegue un blocco di codice o logica di business.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="1ad5f-106">Le funzioni supportano inoltre *associazioni* specializzate che si connettono a risorse come l'archiviazione e le code.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logo di funzioni di Azure](./media/azure-functions-logo.png)

<span data-ttu-id="1ad5f-108">Sono disponibili due versioni del Framework di funzioni di Azure.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="1ad5f-109">La versione legacy supporta il .NET Framework completo e il nuovo Runtime supporta le applicazioni .NET Core multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="1ad5f-110">Sono supportate altre C# lingue oltre ad esempio F#JavaScript, e Java.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="1ad5f-111">Le funzioni create nel portale forniscono una sintassi di scripting avanzata.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="1ad5f-112">Le funzioni create come progetti autonomi possono essere distribuite con funzionalità e supporto completo per la piattaforma.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="1ad5f-113">Per altre informazioni, vedere la [documentazione di funzioni di Azure](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="1ad5f-114">Funzioni V1 e V2</span><span class="sxs-lookup"><span data-stu-id="1ad5f-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="1ad5f-115">Sono disponibili due versioni del runtime di funzioni di Azure: 1. x e 2. x.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="1ad5f-116">La versione 1. x è disponibile a livello generale (GA).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="1ad5f-117">Supporta lo sviluppo .NET dal portale o dai computer Windows e usa il .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="1ad5f-118">1. x supporta C#, JavaScript e F#, con supporto sperimentale per Python, php, typescript, batch, bash e PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="1ad5f-119">[La versione 2. x è ora disponibile](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/)a livello generale.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="1ad5f-120">Si avvale di .NET Core e supporta lo sviluppo multipiattaforma sui computer Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="1ad5f-121">2. x aggiunge un supporto di prima classe per Java ma non supporta ancora direttamente nessuno dei linguaggi sperimentali.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="1ad5f-122">La versione 2. x usa un nuovo modello di estendibilità dell'associazione che consente estensioni di terze parti per la piattaforma, il controllo delle versioni indipendente delle associazioni e un ambiente di esecuzione più semplificato.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="1ad5f-123">**Si è verificato un problema noto in 1. x con supporto per il [Reindirizzamento dell'associazione](https://github.com/Azure/azure-functions-host/issues/992).**</span><span class="sxs-lookup"><span data-stu-id="1ad5f-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="1ad5f-124">Il problema è specifico per lo sviluppo in .NET.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="1ad5f-125">Sono interessati i progetti con dipendenze dalle librerie che hanno una versione diversa rispetto alle librerie incluse nel Runtime.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="1ad5f-126">Il team di funzioni si è impegnato a compiere un progressi concreto sul problema.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="1ad5f-127">Il team affronterà i reindirizzamenti di binding in 2. x prima di passare alla disponibilità generale.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="1ad5f-128">L'istruzione ufficiale del team con correzioni e soluzioni alternative consigliate è disponibile qui: [risoluzione degli assembly in funzioni di Azure](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="1ad5f-129">Per ulteriori informazioni, vedere [compare 1. x e 2. x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="1ad5f-130">Supporto del linguaggio di programmazione</span><span class="sxs-lookup"><span data-stu-id="1ad5f-130">Programming language support</span></span>

<span data-ttu-id="1ad5f-131">Le lingue seguenti sono supportate in disponibilità generale (GA), anteprima o sperimentale.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="1ad5f-132">Lingua:</span><span class="sxs-lookup"><span data-stu-id="1ad5f-132">Language</span></span>      |<span data-ttu-id="1ad5f-133">1. x</span><span class="sxs-lookup"><span data-stu-id="1ad5f-133">1.x</span></span>         |<span data-ttu-id="1ad5f-134">2.x</span><span class="sxs-lookup"><span data-stu-id="1ad5f-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="1ad5f-135">**C#**</span><span class="sxs-lookup"><span data-stu-id="1ad5f-135">**C#**</span></span>        |<span data-ttu-id="1ad5f-136">Disponibilità a livello generale</span><span class="sxs-lookup"><span data-stu-id="1ad5f-136">GA</span></span>          |<span data-ttu-id="1ad5f-137">Preview</span><span class="sxs-lookup"><span data-stu-id="1ad5f-137">Preview</span></span>  |
|<span data-ttu-id="1ad5f-138">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="1ad5f-138">**JavaScript**</span></span>|<span data-ttu-id="1ad5f-139">Disponibilità a livello generale</span><span class="sxs-lookup"><span data-stu-id="1ad5f-139">GA</span></span>          |<span data-ttu-id="1ad5f-140">Preview</span><span class="sxs-lookup"><span data-stu-id="1ad5f-140">Preview</span></span>  |
|<span data-ttu-id="1ad5f-141">**F#**</span><span class="sxs-lookup"><span data-stu-id="1ad5f-141">**F#**</span></span>        |<span data-ttu-id="1ad5f-142">Disponibilità a livello generale</span><span class="sxs-lookup"><span data-stu-id="1ad5f-142">GA</span></span>          |         |
|<span data-ttu-id="1ad5f-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="1ad5f-143">**Java**</span></span>      |            |<span data-ttu-id="1ad5f-144">Preview</span><span class="sxs-lookup"><span data-stu-id="1ad5f-144">Preview</span></span>  |
|<span data-ttu-id="1ad5f-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="1ad5f-145">**Python**</span></span>    |<span data-ttu-id="1ad5f-146">Sperimentale</span><span class="sxs-lookup"><span data-stu-id="1ad5f-146">Experimental</span></span>|         |
|<span data-ttu-id="1ad5f-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="1ad5f-147">**PHP**</span></span>       |<span data-ttu-id="1ad5f-148">Sperimentale</span><span class="sxs-lookup"><span data-stu-id="1ad5f-148">Experimental</span></span>|         |
|<span data-ttu-id="1ad5f-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="1ad5f-149">**TypeScript**</span></span>|<span data-ttu-id="1ad5f-150">Sperimentale</span><span class="sxs-lookup"><span data-stu-id="1ad5f-150">Experimental</span></span>|         |
|<span data-ttu-id="1ad5f-151">**Batch**</span><span class="sxs-lookup"><span data-stu-id="1ad5f-151">**Batch**</span></span>     |<span data-ttu-id="1ad5f-152">Sperimentale</span><span class="sxs-lookup"><span data-stu-id="1ad5f-152">Experimental</span></span>|         |
|<span data-ttu-id="1ad5f-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="1ad5f-153">**Bash**</span></span>      |<span data-ttu-id="1ad5f-154">Sperimentale</span><span class="sxs-lookup"><span data-stu-id="1ad5f-154">Experimental</span></span>|         |
|<span data-ttu-id="1ad5f-155">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="1ad5f-155">**PowerShell**</span></span>|<span data-ttu-id="1ad5f-156">Sperimentale</span><span class="sxs-lookup"><span data-stu-id="1ad5f-156">Experimental</span></span>|         |

<span data-ttu-id="1ad5f-157">Per ulteriori informazioni, vedere [linguaggi supportati](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="1ad5f-158">Piani di servizio app</span><span class="sxs-lookup"><span data-stu-id="1ad5f-158">App service plans</span></span>

<span data-ttu-id="1ad5f-159">Le funzioni sono supportate da un *piano di servizio app*.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="1ad5f-160">Il piano definisce le risorse usate dall'app per le funzioni.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="1ad5f-161">È possibile assegnare piani a un'area, determinare le dimensioni e il numero di macchine virtuali che verranno usate e scegliere un piano tariffario.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="1ad5f-162">Per un vero approccio senza server, le app per le funzioni possono usare il piano a **consumo** .</span><span class="sxs-lookup"><span data-stu-id="1ad5f-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="1ad5f-163">Il piano a consumo eseguirà il ridimensionamento automatico del back-end in base al carico.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="1ad5f-164">Per altre informazioni, vedere [piani di servizio app](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="1ad5f-165">Creare la prima funzione</span><span class="sxs-lookup"><span data-stu-id="1ad5f-165">Create your first function</span></span>

<span data-ttu-id="1ad5f-166">Esistono tre modi comuni per creare app per le funzioni.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-166">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="1ad5f-167">Funzioni di script nel portale.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-167">Script functions in the portal.</span></span>
- <span data-ttu-id="1ad5f-168">Creare le risorse necessarie usando l'interfaccia della riga di comando di Azure.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-168">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="1ad5f-169">Consente di compilare localmente le funzioni usando l'IDE preferito e di pubblicarle in Azure.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="1ad5f-170">Per altre informazioni sulla creazione di una funzione con script nel portale, vedere [creare la prima funzione nel portale di Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="1ad5f-171">Per compilare dall'interfaccia della riga di comando di Azure, vedere [creare la prima funzione usando l'interfaccia della](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)riga di comando di Azure.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="1ad5f-172">Per creare una funzione da Visual Studio, vedere [creare la prima funzione con Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="1ad5f-173">Informazioni sui trigger e sulle associazioni</span><span class="sxs-lookup"><span data-stu-id="1ad5f-173">Understand triggers and bindings</span></span>

<span data-ttu-id="1ad5f-174">Le funzioni vengono richiamate da un *trigger* e possono avere esattamente una.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="1ad5f-175">Oltre a richiamare la funzione, alcuni trigger vengono utilizzati anche come associazioni.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="1ad5f-176">È anche possibile definire più associazioni oltre al trigger.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="1ad5f-177">Le *associazioni* forniscono una modalità dichiarativa per connettere i dati al codice.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="1ad5f-178">Possono essere passati (input) o ricevere dati (output).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="1ad5f-179">I trigger e le associazioni facilitano l'utilizzo delle funzioni.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="1ad5f-180">Le associazioni rimuovono l'overhead della creazione manuale di connessioni di database o file system.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="1ad5f-181">Tutte le informazioni necessarie per le associazioni sono contenute in un file *Functions. JSON* speciale per gli script o dichiarati con attributi nel codice.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="1ad5f-182">Alcuni trigger comuni includono:</span><span class="sxs-lookup"><span data-stu-id="1ad5f-182">Some common triggers include:</span></span>

- <span data-ttu-id="1ad5f-183">Archiviazione BLOB: richiamare la funzione quando un file o una cartella viene caricata o modificata nello spazio di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="1ad5f-184">HTTP: richiama la funzione come un'API REST.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-184">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="1ad5f-185">Queue: richiama la funzione quando gli elementi sono presenti in una coda.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-185">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="1ad5f-186">Timer: richiamare la funzione a cadenza regolare.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="1ad5f-187">Di seguito sono riportati alcuni esempi di binding:</span><span class="sxs-lookup"><span data-stu-id="1ad5f-187">Examples of bindings include:</span></span>

- <span data-ttu-id="1ad5f-188">CosmosDB: consente di connettersi facilmente al database per caricare o salvare i file.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-188">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="1ad5f-189">Archiviazione tabelle: usare l'archiviazione di chiave/valore dall'app per le funzioni.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-189">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="1ad5f-190">Archiviazione code: è possibile recuperare facilmente elementi da una coda o inserire nuovi elementi nella coda.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="1ad5f-191">Il file *Functions. JSON* di esempio seguente definisce un trigger e un'associazione:</span><span class="sxs-lookup"><span data-stu-id="1ad5f-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

<span data-ttu-id="1ad5f-192">In questo esempio, la funzione viene attivata da una modifica all'archiviazione BLOB nel contenitore `images`.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="1ad5f-193">Le informazioni per il file vengono passate, quindi il trigger funge anche da Binding.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="1ad5f-194">Esiste un'altra associazione per inserire le informazioni in una coda denominata `images`.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="1ad5f-195">Di seguito è C# riportato lo script per la funzione:</span><span class="sxs-lookup"><span data-stu-id="1ad5f-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="1ad5f-196">L'esempio è una funzione semplice che accetta il nome del file che è stato modificato o caricato nell'archivio BLOB e lo inserisce in una coda per l'elaborazione successiva.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="1ad5f-197">Per un elenco completo dei trigger e delle associazioni, vedere [concetti relativi a trigger e associazioni di funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="1ad5f-198">Proxy</span><span class="sxs-lookup"><span data-stu-id="1ad5f-198">Proxies</span></span>

<span data-ttu-id="1ad5f-199">I proxy forniscono la funzionalità di reindirizzamento per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="1ad5f-200">I proxy espongono un endpoint ed eseguire il mapping dell'endpoint a un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="1ad5f-201">Con i proxy è possibile:</span><span class="sxs-lookup"><span data-stu-id="1ad5f-201">With proxies, you can:</span></span>

- <span data-ttu-id="1ad5f-202">Reindirizzare una richiesta in ingresso a un altro endpoint.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-202">Reroute an incoming request to another endpoint.</span></span>
- <span data-ttu-id="1ad5f-203">Modificare la richiesta in ingresso prima che venga passata.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-203">Modify the incoming request before it's passed along.</span></span>
- <span data-ttu-id="1ad5f-204">Modificare o fornire una risposta.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-204">Modify or provide a response.</span></span>

<span data-ttu-id="1ad5f-205">I proxy vengono usati per scenari come:</span><span class="sxs-lookup"><span data-stu-id="1ad5f-205">Proxies are used for scenarios such as:</span></span>

- <span data-ttu-id="1ad5f-206">Semplificazione, abbreviazione o modifica dell'URL.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-206">Simplifying, shortening, or changing the URL.</span></span>
- <span data-ttu-id="1ad5f-207">Fornire un prefisso API coerente a più servizi back-end.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-207">Providing a consistent API prefix to multiple back-end services.</span></span>
- <span data-ttu-id="1ad5f-208">Simulazione di una risposta a un endpoint in fase di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-208">Mocking a response to an endpoint being developed.</span></span>
- <span data-ttu-id="1ad5f-209">Fornire una risposta statica a un endpoint noto.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-209">Providing a static response to a well-known endpoint.</span></span>
- <span data-ttu-id="1ad5f-210">Mantenere coerente un endpoint API mentre viene spostato o migrato il back-end.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="1ad5f-211">I proxy vengono archiviati come definizioni JSON.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="1ad5f-212">Ecco un esempio:</span><span class="sxs-lookup"><span data-stu-id="1ad5f-212">Here is an example:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

<span data-ttu-id="1ad5f-213">Il proxy `Domain Redirect` accetta una route abbreviata e ne esegue il mapping alla risorsa della funzione più lunga.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="1ad5f-214">La trasformazione ha un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="1ad5f-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="1ad5f-215">Il proxy `Root` esegue qualsiasi operazione inviata all'URL radice (`https://--shorturl--/`) e la reindirizza al sito della documentazione.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="1ad5f-216">Un esempio di uso di proxy è illustrato nel video [Azure: portare l'app nel cloud con funzioni di Azure senza server](https://channel9.msdn.com/events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="1ad5f-217">In tempo reale, viene eseguita la migrazione di un'applicazione ASP.NET Core in esecuzione su SQL Server locale al cloud di Azure.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="1ad5f-218">I proxy vengono usati per eseguire il refactoring di un progetto API Web tradizionale per l'uso di funzioni.</span><span class="sxs-lookup"><span data-stu-id="1ad5f-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="1ad5f-219">Per altre informazioni sui proxy, vedere [usare proxy di funzioni di Azure](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span><span class="sxs-lookup"><span data-stu-id="1ad5f-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1ad5f-220">[Precedente](azure-serverless-platform.md)
>[Successivo](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="1ad5f-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
