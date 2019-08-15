---
title: Immagini Docker .NET ufficiali
description: Architettura di microservizi .NET per applicazioni .NET in contenitori | Immagini Docker .NET ufficiali
ms.date: 01/07/2019
ms.openlocfilehash: b184e8f3606da8448a06a1cad90688958ecbce3a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675708"
---
# <a name="official-net-docker-images"></a><span data-ttu-id="ee6a2-103">Immagini Docker .NET ufficiali</span><span class="sxs-lookup"><span data-stu-id="ee6a2-103">Official .NET Docker images</span></span>

<span data-ttu-id="ee6a2-104">Le immagini Docker .NET ufficiali sono immagini Docker create e ottimizzate da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-104">The Official .NET Docker images are Docker images created and optimized by Microsoft.</span></span> <span data-ttu-id="ee6a2-105">Sono disponibili pubblicamente nei repository Microsoft nell'[hub Docker](https://hub.docker.com/u/microsoft/).</span><span class="sxs-lookup"><span data-stu-id="ee6a2-105">They are publicly available in the Microsoft repositories on [Docker Hub](https://hub.docker.com/u/microsoft/).</span></span> <span data-ttu-id="ee6a2-106">Ogni repository può contenere più immagini, a seconda delle versioni di .NET e a seconda del sistema operativo e delle relative versioni, ad esempio Linux Debian, Linux Spline, Windows Nano Server, Windows Server Core e così via.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-106">Each repository can contain multiple images, depending on .NET versions, and depending on the OS and versions (Linux Debian, Linux Alpine, Windows Nano Server, Windows Server Core, etc.).</span></span>

<span data-ttu-id="ee6a2-107">Da .NET Core 2.1, tutte le immagini .NET Core, tra cui ASP.NET Core, sono disponibili nell'hub Docker nel repository di immagini .NET Core: https://hub.docker.com/_/microsoft-dotnet-core/</span><span class="sxs-lookup"><span data-stu-id="ee6a2-107">Since .NET Core 2.1, all the .NET Core images, including for ASP.NET Core are available at Docker Hub at the .NET Core image repo: https://hub.docker.com/_/microsoft-dotnet-core/</span></span>

<span data-ttu-id="ee6a2-108">La maggior parte dei repository di immagini fornisce contrassegni completi che consentono di selezionare sia una versione specifica del framework che un sistema operativo (distribuzione di Linux o versione di Windows).</span><span class="sxs-lookup"><span data-stu-id="ee6a2-108">Most image repos provide extensive tagging to help you select not just a specific framework version, but also to choose an OS (Linux distro or Windows version).</span></span>

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a><span data-ttu-id="ee6a2-109">Ottimizzazioni delle immagini .NET Core e Docker per lo sviluppo e la produzione</span><span class="sxs-lookup"><span data-stu-id="ee6a2-109">.NET Core and Docker image optimizations for development versus production</span></span>

<span data-ttu-id="ee6a2-110">Quando si creano immagini Docker per gli sviluppatori, è opportuno concentrare l'attenzione sugli scenari principali seguenti:</span><span class="sxs-lookup"><span data-stu-id="ee6a2-110">When building Docker images for developers, Microsoft focused on the following main scenarios:</span></span>

- <span data-ttu-id="ee6a2-111">Immagini usate per *sviluppare* e compilare app .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-111">Images used to *develop* and build .NET Core apps.</span></span>

- <span data-ttu-id="ee6a2-112">Immagini usate per *eseguire* app .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-112">Images used to *run* .NET Core apps.</span></span>

<span data-ttu-id="ee6a2-113">Perché sono disponibili più immagini?</span><span class="sxs-lookup"><span data-stu-id="ee6a2-113">Why multiple images?</span></span> <span data-ttu-id="ee6a2-114">Durante lo sviluppo, la compilazione e l'esecuzione di applicazioni in contenitori, è necessario tenere conto di diverse priorità.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-114">When developing, building, and running containerized applications, you usually have different priorities.</span></span> <span data-ttu-id="ee6a2-115">Fornendo immagini diverse per queste attività separate, Microsoft consente di ottimizzare i processi per lo sviluppo, la compilazione e la distribuzione di app.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-115">By providing different images for these separate tasks, Microsoft helps optimize the separate processes of developing, building, and deploying apps.</span></span>

### <a name="during-development-and-build"></a><span data-ttu-id="ee6a2-116">Durante lo sviluppo e la compilazione</span><span class="sxs-lookup"><span data-stu-id="ee6a2-116">During development and build</span></span>

<span data-ttu-id="ee6a2-117">Durante lo sviluppo, ciò che conta è la velocità di iterazione delle modifiche e la possibilità di eseguire il debug delle modifiche.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-117">During development, what is important is how fast you can iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="ee6a2-118">Le dimensioni dell'immagine non sono importanti quanto la possibilità di apportare modifiche al codice e visualizzare rapidamente tali modifiche.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-118">The size of the image is not as important as the ability to make changes to your code and see the changes quickly.</span></span> <span data-ttu-id="ee6a2-119">Durante il processo di sviluppo e compilazione, alcuni strumenti e "contenitori di agente di compilazione" usano l'immagine .NET Core (*mcr.microsoft.com/dotnet/core/sdk:2.2*) di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-119">Some tools and "build-agent containers", use the development .NET Core image (*mcr.microsoft.com/dotnet/core/sdk:2.2*) during development and build process.</span></span> <span data-ttu-id="ee6a2-120">Durante la compilazione all'interno di un contenitore Docker, gli aspetti importanti sono gli elementi necessari per compilare l'app.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-120">When building inside a Docker container, the important aspects are the elements that are needed in order to compile your app.</span></span> <span data-ttu-id="ee6a2-121">Tra questi, il compilatore e le eventuali altre dipendenze di .NET.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-121">This includes the compiler and any other .NET dependencies.</span></span>

<span data-ttu-id="ee6a2-122">Perché questo tipo di immagine di compilazione è importante?</span><span class="sxs-lookup"><span data-stu-id="ee6a2-122">Why is this type of build image important?</span></span> <span data-ttu-id="ee6a2-123">Questa immagine non viene distribuita nell'ambiente di produzione.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-123">You do not deploy this image to production.</span></span> <span data-ttu-id="ee6a2-124">È piuttosto un'immagine usata per compilare il contenuto inserito in un'immagine di produzione.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-124">Instead, it is an image you use to build the content you place into a production image.</span></span> <span data-ttu-id="ee6a2-125">Questa immagine può essere usata nell'ambiente di integrazione continua (CI, Continuous Integration) o di compilazione quando si eseguono compilazioni Docker in più fasi.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-125">This image would be used in your continuous integration (CI) environment or build environment when using Docker Multi-stage builds.</span></span>

### <a name="in-production"></a><span data-ttu-id="ee6a2-126">In produzione</span><span class="sxs-lookup"><span data-stu-id="ee6a2-126">In production</span></span>

<span data-ttu-id="ee6a2-127">Ciò che conta nella produzione è quanto velocemente è possibile distribuire e avviare i contenitori basati su un'immagine .NET Core di produzione.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-127">What is important in production is how fast you can deploy and start your containers based on a production .NET Core image.</span></span> <span data-ttu-id="ee6a2-128">Di conseguenza, l'immagine solo runtime basata su *mcr.microsoft.com/dotnet/core/aspnet:2.2* è di piccole dimensioni, in modo da poter attraversare velocemente la rete dal registro Docker agli host Docker.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-128">Therefore, the runtime-only image based on *mcr.microsoft.com/dotnet/core/aspnet:2.2* is small so that it can travel quickly across the network from your Docker registry to your Docker hosts.</span></span> <span data-ttu-id="ee6a2-129">Il contenuto è pronto per l'esecuzione, rendendo minimo l'intervallo tra l'avvio del contenitore e l'elaborazione dei risultati.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-129">The contents are ready to run, enabling the fastest time from starting the container to processing results.</span></span> <span data-ttu-id="ee6a2-130">Nel modello Docker, non è necessario eseguire la compilazione dal codice C\#, come quando si eseguono i comandi dotnet build o dotnet publish con il contenitore di compilazione.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-130">In the Docker model, there is no need for compilation from C\# code, as there is when you run dotnet build or dotnet publish when using the build container.</span></span>

<span data-ttu-id="ee6a2-131">In questa immagine ottimizzata si inseriscono solo i binari e altro contenuto necessari per eseguire l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-131">In this optimized image you put only the binaries and other content needed to run the application.</span></span> <span data-ttu-id="ee6a2-132">Ad esempio, il contenuto creato dal comando dotnet publish contiene solo i file JS e CSS, le immagini e i file binari .NET compilati.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-132">For example, the content created by dotnet publish contains only the compiled .NET binaries, images, .js, and .css files.</span></span> <span data-ttu-id="ee6a2-133">Nel corso del tempo, si vedranno immagini contenenti pacchetti pre-JIT (la compilazione dal linguaggio intermedio al codice nativo che avviene in fase di esecuzione).</span><span class="sxs-lookup"><span data-stu-id="ee6a2-133">Over time, you will see images that contain pre-jitted (the compilation from IL to native that occurs at runtime) packages.</span></span>

<span data-ttu-id="ee6a2-134">Anche se sono presenti più versioni delle immagini .NET Core e ASP.NET Core, tutte queste versioni condividono uno o più livelli, incluso il livello di base.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-134">Although there are multiple versions of the .NET Core and ASP.NET Core images, they all share one or more layers, including the base layer.</span></span> <span data-ttu-id="ee6a2-135">La quantità di spazio su disco necessaria per archiviare un'immagine è quindi ridotta ed è costituita solo dal valore differenziale tra l'immagine personalizzata e l'immagine di base.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-135">Therefore, the amount of disk space needed to store an image is small; it consists only of the delta between your custom image and its base image.</span></span> <span data-ttu-id="ee6a2-136">Ne consegue quindi che il pull dell'immagine dal registro è veloce.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-136">The result is that it is quick to pull the image from your registry.</span></span>

<span data-ttu-id="ee6a2-137">Durante l'esplorazione dei repository di immagini .NET nell'hub Docker, si troveranno più versioni delle immagini classificate o contrassegnate con tag.</span><span class="sxs-lookup"><span data-stu-id="ee6a2-137">When you explore the .NET image repositories at Docker Hub, you will find multiple image versions classified or marked with tags.</span></span> <span data-ttu-id="ee6a2-138">Questi tag consentono di decidere l'immagine da usare a seconda della versione necessaria, come quelle nella tabella seguente:</span><span class="sxs-lookup"><span data-stu-id="ee6a2-138">These tags help to decide which one to use, depending on the version you need, like those in the following table:</span></span>

| <span data-ttu-id="ee6a2-139">Image</span><span class="sxs-lookup"><span data-stu-id="ee6a2-139">Image</span></span>                                       | <span data-ttu-id="ee6a2-140">Commenti</span><span class="sxs-lookup"><span data-stu-id="ee6a2-140">Comments</span></span>                                                                                          |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ee6a2-141">mcr.microsoft.com/dotnet/core/aspnet:**2.2**</span><span class="sxs-lookup"><span data-stu-id="ee6a2-141">mcr.microsoft.com/dotnet/core/aspnet:**2.2**</span></span> | <span data-ttu-id="ee6a2-142">ASP.NET Core, con ottimizzazioni ASP.NET Core e solo runtime, in Linux e Windows (multiarchitettura)</span><span class="sxs-lookup"><span data-stu-id="ee6a2-142">ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)</span></span> |
| <span data-ttu-id="ee6a2-143">mcr.microsoft.com/dotnet/core/sdk:**2.2**</span><span class="sxs-lookup"><span data-stu-id="ee6a2-143">mcr.microsoft.com/dotnet/core/sdk:**2.2**</span></span>    | <span data-ttu-id="ee6a2-144">.NET Core, con SDK inclusi, in Linux e Windows (multiarchitettura)</span><span class="sxs-lookup"><span data-stu-id="ee6a2-144">.NET Core, with SDKs included, on Linux and Windows (multi-arch)</span></span>                                  |

> [!div class="step-by-step"]
> <span data-ttu-id="ee6a2-145">[Precedente](net-container-os-targets.md)
> [Successivo](../architect-microservice-container-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="ee6a2-145">[Previous](net-container-os-targets.md)
[Next](../architect-microservice-container-applications/index.md)</span></span>