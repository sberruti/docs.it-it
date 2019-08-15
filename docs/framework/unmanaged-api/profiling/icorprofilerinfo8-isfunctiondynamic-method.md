---
title: ICorProfilerInfo8::IsFunctionDynamic
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 71c4e749368dce65d5250b9ab78fd8713e9d61a0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973871"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="7cf33-102">Metodo ICorProfilerInfo8:: IsFunctionDynamic</span><span class="sxs-lookup"><span data-stu-id="7cf33-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>
  
  <span data-ttu-id="7cf33-103">Determina se una funzione non dispone di metadati associati.</span><span class="sxs-lookup"><span data-stu-id="7cf33-103">Determines if a function does not have associated metadata.</span></span>    
  
## <a name="syntax"></a><span data-ttu-id="7cf33-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7cf33-104">Syntax</span></span>  
  
```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```  
  
#### <a name="parameters"></a><span data-ttu-id="7cf33-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="7cf33-105">Parameters</span></span>  
 `functionId` \
  <span data-ttu-id="7cf33-106">in  Oggetto `FunctionID` che identifica la funzione in questione.</span><span class="sxs-lookup"><span data-stu-id="7cf33-106">[in]  The `FunctionID` that identifies the function in question.</span></span>

  `isDynamic` \
  <span data-ttu-id="7cf33-107">out Puntatore a un oggetto `BOOL` che conterrà un valore che indica se la funzione non dispone di metadati.</span><span class="sxs-lookup"><span data-stu-id="7cf33-107">[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="7cf33-108">Note</span><span class="sxs-lookup"><span data-stu-id="7cf33-108">Remarks</span></span>  
 <span data-ttu-id="7cf33-109">Una funzione è considerata dinamica se non dispone di metadati.</span><span class="sxs-lookup"><span data-stu-id="7cf33-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="7cf33-110">Alcuni metodi come gli stub IL o i metodi LCG non dispongono di metadati associati che possono essere recuperati tramite le API IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="7cf33-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="7cf33-111">Questi metodi possono essere rilevati dai profiler tramite i puntatori all'istruzione oppure ascoltando [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="7cf33-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="7cf33-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="7cf33-112">Requirements</span></span>  
 <span data-ttu-id="7cf33-113">**Piattaforme** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cf33-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cf33-114">**Intestazione:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7cf33-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cf33-115">**Libreria** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cf33-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cf33-116">**Versioni .NET Framework:** [! INCLUDi[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span><span class="sxs-lookup"><span data-stu-id="7cf33-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf33-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7cf33-117">See also</span></span>
- [<span data-ttu-id="7cf33-118">Interfaccia ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="7cf33-118">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
