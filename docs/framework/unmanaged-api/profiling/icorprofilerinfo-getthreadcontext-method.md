---
title: Metodo ICorProfilerInfo::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
ms.openlocfilehash: f8eff85392d355ea54980ac6b29e3c4cebb1b240
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869595"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="3cb7b-102">Metodo ICorProfilerInfo::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="3cb7b-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="3cb7b-103">Ottiene l'identità del contesto attualmente associata al thread specificato.</span><span class="sxs-lookup"><span data-stu-id="3cb7b-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cb7b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="3cb7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cb7b-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="3cb7b-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="3cb7b-106">in ID del thread.</span><span class="sxs-lookup"><span data-stu-id="3cb7b-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="3cb7b-107">out Puntatore all'ID del contesto attualmente associato al thread specificato.</span><span class="sxs-lookup"><span data-stu-id="3cb7b-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="3cb7b-108">Se al thread non è attualmente associato alcun contesto, questa funzione restituirà CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="3cb7b-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cb7b-109">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="3cb7b-109">Requirements</span></span>  
 <span data-ttu-id="3cb7b-110">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cb7b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cb7b-111">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3cb7b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3cb7b-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cb7b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cb7b-113">**Versioni .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cb7b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb7b-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3cb7b-114">See also</span></span>

- [<span data-ttu-id="3cb7b-115">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="3cb7b-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
