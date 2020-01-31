---
title: Metodo ICorProfilerInfo::GetHandleFromThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: 038f922eaaeb7d660cfbdcc0facb89677bdd154e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863543"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="d3798-102">Metodo ICorProfilerInfo::GetHandleFromThread</span><span class="sxs-lookup"><span data-stu-id="d3798-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="d3798-103">Esegue il mapping dell'ID di un thread a un handle di thread Win32.</span><span class="sxs-lookup"><span data-stu-id="d3798-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3798-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d3798-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3798-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="d3798-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d3798-106">in ID del thread di cui eseguire il mapping.</span><span class="sxs-lookup"><span data-stu-id="d3798-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="d3798-107">out Puntatore a un handle di thread Win32.</span><span class="sxs-lookup"><span data-stu-id="d3798-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3798-108">Note</span><span class="sxs-lookup"><span data-stu-id="d3798-108">Remarks</span></span>  
 <span data-ttu-id="d3798-109">Il profiler deve chiamare la funzione Win32 `DuplicateHandle` sull'handle prima di usarlo.</span><span class="sxs-lookup"><span data-stu-id="d3798-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3798-110">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="d3798-110">Requirements</span></span>  
 <span data-ttu-id="d3798-111">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3798-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3798-112">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d3798-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3798-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3798-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3798-114">**Versioni .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3798-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3798-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d3798-115">See also</span></span>

- [<span data-ttu-id="d3798-116">Interfaccia ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="d3798-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
