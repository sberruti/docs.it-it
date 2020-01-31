---
title: Metodo ICorProfilerCallback::ExceptionSearchFilterEnter
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
ms.openlocfilehash: 710dbe70b0a2498a3d521cdc813c4ead7ba6442e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866429"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="bd1dd-102">Metodo ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="bd1dd-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="bd1dd-103">Notifica al profiler che è iniziata l'esecuzione di un filtro eccezioni definito dall'utente per la fase di ricerca della gestione delle eccezioni.</span><span class="sxs-lookup"><span data-stu-id="bd1dd-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd1dd-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bd1dd-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd1dd-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="bd1dd-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="bd1dd-106">\[in] ID della funzione che contiene il filtro.</span><span class="sxs-lookup"><span data-stu-id="bd1dd-106">\[in] The ID of the function that contains the filter.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd1dd-107">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="bd1dd-107">Requirements</span></span>  
 <span data-ttu-id="bd1dd-108">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd1dd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd1dd-109">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd1dd-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd1dd-110">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd1dd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd1dd-111">**Versioni .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd1dd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1dd-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bd1dd-112">See also</span></span>

- [<span data-ttu-id="bd1dd-113">Interfaccia ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="bd1dd-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="bd1dd-114">Metodo ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="bd1dd-114">ExceptionSearchFilterLeave Method</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)
