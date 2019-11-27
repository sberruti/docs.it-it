---
title: Elemento GCLOHThreshold
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451220"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="694ae-102">Elemento GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="694ae-102">GCLOHThreshold element</span></span>

<span data-ttu-id="694ae-103">Specifica la dimensione della soglia, in byte, che fa in modo che il Garbage Collector inserisca gli oggetti nell'heap degli oggetti grandi (LOH).</span><span class="sxs-lookup"><span data-stu-id="694ae-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

<span data-ttu-id="694ae-104">[\<configuration>](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="694ae-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="694ae-105">&nbsp;&nbsp;[\<runtime >](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="694ae-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="694ae-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold ></span><span class="sxs-lookup"><span data-stu-id="694ae-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span></span>

## <a name="syntax"></a><span data-ttu-id="694ae-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="694ae-107">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="694ae-108">Attributi</span><span class="sxs-lookup"><span data-stu-id="694ae-108">Attributes</span></span>

|<span data-ttu-id="694ae-109">Attributo</span><span class="sxs-lookup"><span data-stu-id="694ae-109">Attribute</span></span>|<span data-ttu-id="694ae-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="694ae-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="694ae-111">Attributo obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="694ae-111">Required attribute.</span></span><br /><br /><span data-ttu-id="694ae-112">Specifica le dimensioni della soglia che determinano l'uso degli oggetti nell'heap degli oggetti grandi.</span><span class="sxs-lookup"><span data-stu-id="694ae-112">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="694ae-113">attributo enabled</span><span class="sxs-lookup"><span data-stu-id="694ae-113">enabled attribute</span></span>

|<span data-ttu-id="694ae-114">Value</span><span class="sxs-lookup"><span data-stu-id="694ae-114">Value</span></span>|<span data-ttu-id="694ae-115">Descrizione</span><span class="sxs-lookup"><span data-stu-id="694ae-115">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="694ae-116">Dimensione della soglia, in byte, che fa sì che gli oggetti vadano nell'heap degli oggetti grandi.</span><span class="sxs-lookup"><span data-stu-id="694ae-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="694ae-117">Elemento figlio</span><span class="sxs-lookup"><span data-stu-id="694ae-117">Child elements</span></span>

<span data-ttu-id="694ae-118">Nessuno.</span><span class="sxs-lookup"><span data-stu-id="694ae-118">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="694ae-119">Elementi padre</span><span class="sxs-lookup"><span data-stu-id="694ae-119">Parent elements</span></span>

|<span data-ttu-id="694ae-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="694ae-120">Element</span></span>|<span data-ttu-id="694ae-121">Descrizione</span><span class="sxs-lookup"><span data-stu-id="694ae-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="694ae-122">Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="694ae-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="694ae-123">Contiene informazioni sull'associazione degli assembly e sull'operazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="694ae-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="694ae-124">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="694ae-124">Remarks</span></span>

<span data-ttu-id="694ae-125">Questa impostazione è stata introdotta in .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="694ae-125">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="694ae-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="694ae-126">See also</span></span>

- [<span data-ttu-id="694ae-127">Schema delle impostazioni della fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="694ae-127">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="694ae-128">Schema dei file di configurazione</span><span class="sxs-lookup"><span data-stu-id="694ae-128">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="694ae-129">Principi fondamentali di Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="694ae-129">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="694ae-130">Opzioni di configurazione della fase di esecuzione di NET Core per GC</span><span class="sxs-lookup"><span data-stu-id="694ae-130">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)