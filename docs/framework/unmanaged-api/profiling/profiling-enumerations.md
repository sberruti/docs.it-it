---
title: Enumerazioni di profilatura
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: 1a9781fa1b4b608152faa7d5edc80bd4866f0c81
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868135"
---
# <a name="profiling-enumerations"></a><span data-ttu-id="51e4f-102">Enumerazioni di profilatura</span><span class="sxs-lookup"><span data-stu-id="51e4f-102">Profiling Enumerations</span></span>
<span data-ttu-id="51e4f-103">Questa sezione descrive le enumerazioni non gestite usate dall'API di profilatura.</span><span class="sxs-lookup"><span data-stu-id="51e4f-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51e4f-104">In questa sezione</span><span class="sxs-lookup"><span data-stu-id="51e4f-104">In This Section</span></span>  
 [<span data-ttu-id="51e4f-105">Enumerazione COR_PRF_CLAUSE_TYPE</span><span class="sxs-lookup"><span data-stu-id="51e4f-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="51e4f-106">Indica il tipo di clausola di eccezione in cui il codice è appena entrato o da cui è appena uscito.</span><span class="sxs-lookup"><span data-stu-id="51e4f-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="51e4f-107">Enumerazione COR_PRF_CODEGEN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="51e4f-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="51e4f-108">Definisce i flag di generazione del codice che possono essere impostati con il metodo [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) .</span><span class="sxs-lookup"><span data-stu-id="51e4f-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="51e4f-109">Enumerazione COR_PRF_FINALIZER_FLAGS</span><span class="sxs-lookup"><span data-stu-id="51e4f-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="51e4f-110">Descrive il finalizzatore per un oggetto.</span><span class="sxs-lookup"><span data-stu-id="51e4f-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="51e4f-111">Enumerazione COR_PRF_GC_GENERATION</span><span class="sxs-lookup"><span data-stu-id="51e4f-111">COR_PRF_GC_GENERATION Enumeration</span></span>](cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="51e4f-112">Identifica una generazione di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="51e4f-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="51e4f-113">Enumerazione COR_PRF_GC_REASON</span><span class="sxs-lookup"><span data-stu-id="51e4f-113">COR_PRF_GC_REASON Enumeration</span></span>](cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="51e4f-114">Indica il motivo per cui è in corso la Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="51e4f-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="51e4f-115">Enumerazione COR_PRF_GC_ROOT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="51e4f-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="51e4f-116">Indica le proprietà della radice di un Garbage Collector.</span><span class="sxs-lookup"><span data-stu-id="51e4f-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="51e4f-117">Enumerazione COR_PRF_GC_ROOT_KIND</span><span class="sxs-lookup"><span data-stu-id="51e4f-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="51e4f-118">Indica il tipo di Garbage Collector radice esposto dal callback [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="51e4f-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="51e4f-119">Enumerazione COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="51e4f-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="51e4f-120">Fornisce i flag oltre a quelli disponibili nell'enumerazione [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) che il profiler può specificare al metodo [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) durante il caricamento.</span><span class="sxs-lookup"><span data-stu-id="51e4f-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="51e4f-121">Enumerazione COR_PRF_JIT_CACHE</span><span class="sxs-lookup"><span data-stu-id="51e4f-121">COR_PRF_JIT_CACHE Enumeration</span></span>](cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="51e4f-122">Indica il risultato della ricerca di una funzione memorizzata nella cache.</span><span class="sxs-lookup"><span data-stu-id="51e4f-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="51e4f-123">Enumerazione COR_PRF_MISC</span><span class="sxs-lookup"><span data-stu-id="51e4f-123">COR_PRF_MISC Enumeration</span></span>](cor-prf-misc-enumeration.md)  
 <span data-ttu-id="51e4f-124">Contiene valori costanti che specificano identificatori speciali.</span><span class="sxs-lookup"><span data-stu-id="51e4f-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="51e4f-125">Enumerazione COR_PRF_MODULE_FLAGS</span><span class="sxs-lookup"><span data-stu-id="51e4f-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="51e4f-126">Specifica le proprietà di un modulo.</span><span class="sxs-lookup"><span data-stu-id="51e4f-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="51e4f-127">Enumerazione COR_PRF_MONITOR</span><span class="sxs-lookup"><span data-stu-id="51e4f-127">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="51e4f-128">Contiene i valori usati per specificare il comportamento, le funzionalità o gli eventi ai quali il profiler intende effettuare la sottoscrizione.</span><span class="sxs-lookup"><span data-stu-id="51e4f-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="51e4f-129">Enumerazione COR_PRF_RUNTIME_TYPE</span><span class="sxs-lookup"><span data-stu-id="51e4f-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="51e4f-130">Contiene valori che indicano la versione di Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="51e4f-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="51e4f-131">Enumerazione COR_PRF_SNAPSHOT_INFO</span><span class="sxs-lookup"><span data-stu-id="51e4f-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="51e4f-132">Specifica la quantità di dati da passare di nuovo con uno snapshot dello stack in ogni chiamata alla funzione `StackSnapshotCallback` del profiler.</span><span class="sxs-lookup"><span data-stu-id="51e4f-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="51e4f-133">Enumerazione COR_PRF_STATIC_TYPE</span><span class="sxs-lookup"><span data-stu-id="51e4f-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="51e4f-134">Indica se un campo è statico e, in tal caso, la qualità statica che si applica al campo.</span><span class="sxs-lookup"><span data-stu-id="51e4f-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="51e4f-135">Enumerazione COR_PRF_SUSPEND_REASON</span><span class="sxs-lookup"><span data-stu-id="51e4f-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="51e4f-136">Indica il motivo per cui il runtime è stato sospeso.</span><span class="sxs-lookup"><span data-stu-id="51e4f-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="51e4f-137">Enumerazione COR_PRF_TRANSITION_REASON</span><span class="sxs-lookup"><span data-stu-id="51e4f-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="51e4f-138">Indica il motivo di una transizione da codice gestito a codice non gestito o viceversa.</span><span class="sxs-lookup"><span data-stu-id="51e4f-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="51e4f-139">Sezioni correlate</span><span class="sxs-lookup"><span data-stu-id="51e4f-139">Related Sections</span></span>  
 [<span data-ttu-id="51e4f-140">Panoramica della profilatura</span><span class="sxs-lookup"><span data-stu-id="51e4f-140">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="51e4f-141">Interfacce di profilatura</span><span class="sxs-lookup"><span data-stu-id="51e4f-141">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="51e4f-142">Funzioni statiche globali di profilatura</span><span class="sxs-lookup"><span data-stu-id="51e4f-142">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="51e4f-143">Strutture di profilatura</span><span class="sxs-lookup"><span data-stu-id="51e4f-143">Profiling Structures</span></span>](profiling-structures.md)
