---
title: Metodo ICorProfilerInfo2::GetObjectGeneration
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
ms.openlocfilehash: b75de955e3b6857c9cc1b5411df4b0f262c4cb9a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862698"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="8fe76-102">Metodo ICorProfilerInfo2::GetObjectGeneration</span><span class="sxs-lookup"><span data-stu-id="8fe76-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="8fe76-103">Ottiene il segmento dell'heap che contiene l'oggetto specificato.</span><span class="sxs-lookup"><span data-stu-id="8fe76-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe76-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8fe76-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fe76-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="8fe76-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="8fe76-106">in ID dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="8fe76-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="8fe76-107">out Puntatore a una struttura di [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) , che descrive un intervallo, ovvero un blocco, della memoria all'interno della generazione che è in fase di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="8fe76-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="8fe76-108">Questo intervallo contiene l'oggetto specificato.</span><span class="sxs-lookup"><span data-stu-id="8fe76-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fe76-109">Note</span><span class="sxs-lookup"><span data-stu-id="8fe76-109">Remarks</span></span>  
 <span data-ttu-id="8fe76-110">Il metodo `GetObjectGeneration` può essere chiamato da qualsiasi callback del profiler, purché Garbage Collection non sia in corso.</span><span class="sxs-lookup"><span data-stu-id="8fe76-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="8fe76-111">Ovvero può essere chiamato da qualsiasi callback, ad eccezione di quelli che si verificano tra [ICorProfilerCallback2:: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) e [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="8fe76-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe76-112">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="8fe76-112">Requirements</span></span>  
 <span data-ttu-id="8fe76-113">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fe76-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe76-114">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8fe76-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8fe76-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fe76-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fe76-116">**Versioni .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe76-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe76-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8fe76-117">See also</span></span>

- [<span data-ttu-id="8fe76-118">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="8fe76-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="8fe76-119">Interfaccia ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="8fe76-119">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
