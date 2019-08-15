---
title: Architettura orientata ai servizi
description: Informazioni sulle differenze fondamentali tra microservizi e architettura orientata ai servizi.
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674928"
---
# <a name="service-oriented-architecture"></a><span data-ttu-id="71dda-103">Architettura orientata ai servizi</span><span class="sxs-lookup"><span data-stu-id="71dda-103">Service-oriented architecture</span></span>

<span data-ttu-id="71dda-104">Architettura orientata ai servizi è un termine molto usato che può avere significati diversi a seconda delle persone.</span><span class="sxs-lookup"><span data-stu-id="71dda-104">Service-oriented architecture (SOA) was an overused term and has meant different things to different people.</span></span> <span data-ttu-id="71dda-105">In generale, architettura orientata ai servizi significa strutturare l'applicazione scomponendola in più servizio (comunemente servizi HTTP) che possono essere classificati in diversi tipi, come sottosistemi o livelli.</span><span class="sxs-lookup"><span data-stu-id="71dda-105">But as a common denominator, SOA means that you structure your application by decomposing it into multiple services (most commonly as HTTP services) that can be classified as different types like subsystems or tiers.</span></span>

<span data-ttu-id="71dda-106">Tali servizi possono ora essere distribuiti come contenitori Docker per risolvere alcuni problemi di distribuzione, poiché tutte le dipendenze sono incluse nell'immagine del contenitore.</span><span class="sxs-lookup"><span data-stu-id="71dda-106">Those services can now be deployed as Docker containers, which solves deployment issues, because all the dependencies are included in the container image.</span></span> <span data-ttu-id="71dda-107">Se, tuttavia, è necessario ridimensionare le applicazioni con architettura orientata ai servizi e la distribuzione è basata su host Docker singoli, possono verificarsi problemi di scalabilità e disponibilità.</span><span class="sxs-lookup"><span data-stu-id="71dda-107">However, when you need to scale up SOA applications, you might have scalability and availability challenges if you're deploying based on single Docker hosts.</span></span> <span data-ttu-id="71dda-108">In questo caso, può essere utile usare il software di clustering Docker o un agente di orchestrazione, come illustrato nelle sezioni successive in cui vengono descritti gli approcci di distribuzione per i microservizi.</span><span class="sxs-lookup"><span data-stu-id="71dda-108">This is where Docker clustering software or an orchestrator can help you, as explained in later sections where deployment approaches for microservices are described.</span></span>

<span data-ttu-id="71dda-109">I contenitori Docker sono utili (ma non necessari) sia per le architetture orientate ai servizi tradizionali sia per le architetture di microservizi più avanzate.</span><span class="sxs-lookup"><span data-stu-id="71dda-109">Docker containers are useful (but not required) for both traditional service-oriented architectures and the more advanced microservices architectures.</span></span>

<span data-ttu-id="71dda-110">I microservizi derivano dall'architettura orientata ai servizi, ma quest'ultima è diversa dall'architettura di microservizi.</span><span class="sxs-lookup"><span data-stu-id="71dda-110">Microservices derive from SOA, but SOA is different from microservices architecture.</span></span> <span data-ttu-id="71dda-111">I broker centralizzati di grandi dimensioni, gli agenti di orchestrazione centralizzati a livello dell'organizzazione e il [bus di servizio aziendale](https://en.wikipedia.org/wiki/Enterprise_service_bus) (ESB, Enterprise Service Bus) sono funzionalità tipiche dell'architettura orientata ai servizi.</span><span class="sxs-lookup"><span data-stu-id="71dda-111">Features like large central brokers, central orchestrators at the organization level, and the [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) are typical in SOA.</span></span> <span data-ttu-id="71dda-112">Ma nella maggior parte dei casi, sono considerate come antipattern nella community dei microservizi.</span><span class="sxs-lookup"><span data-stu-id="71dda-112">But in most cases, these are anti-patterns in the microservice community.</span></span> <span data-ttu-id="71dda-113">Alcuni infatti sostengono che "l'architettura dei microservizi è un'architettura orientata ai servizi progettata correttamente".</span><span class="sxs-lookup"><span data-stu-id="71dda-113">In fact, some people argue that "The microservice architecture is SOA done right."</span></span>

<span data-ttu-id="71dda-114">Questa guida fa riferimento ai microservizi, in quanto l'approccio dell'architettura orientato ai servizi è meno rigoroso rispetto ai requisiti e alle tecniche usati in un'architettura di microservizi.</span><span class="sxs-lookup"><span data-stu-id="71dda-114">This guide focuses on microservices, because a SOA approach is less prescriptive than the requirements and techniques used in a microservice architecture.</span></span> <span data-ttu-id="71dda-115">Se si è in grado di creare un'applicazione basata su microservizi, si riuscirà anche a creare una più semplice applicazione orientata ai servizi.</span><span class="sxs-lookup"><span data-stu-id="71dda-115">If you know how to build a microservice-based application, you also know how to build a simpler service-oriented application.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="71dda-116">[Precedente](docker-application-state-data.md)
>[Successivo](microservices-architecture.md)</span><span class="sxs-lookup"><span data-stu-id="71dda-116">[Previous](docker-application-state-data.md)
[Next](microservices-architecture.md)</span></span>