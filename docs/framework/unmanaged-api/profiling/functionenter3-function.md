---
title: Funzione FunctionEnter3
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: 3ba014cbae4a71713f29968f0137ac053033c661
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866957"
---
# <a name="functionenter3-function"></a><span data-ttu-id="bf1bb-102">Funzione FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="bf1bb-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="bf1bb-103">Notifica al profiler che il controllo viene passato a una funzione.</span><span class="sxs-lookup"><span data-stu-id="bf1bb-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf1bb-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bf1bb-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf1bb-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="bf1bb-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="bf1bb-106">\[in] identificatore della funzione a cui viene passato il controllo.</span><span class="sxs-lookup"><span data-stu-id="bf1bb-106">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="bf1bb-107">Note</span><span class="sxs-lookup"><span data-stu-id="bf1bb-107">Remarks</span></span>  
 <span data-ttu-id="bf1bb-108">La funzione di callback `FunctionEnter3` notifica al profiler che le funzioni vengono chiamate, ma non supporta l'ispezione degli argomenti.</span><span class="sxs-lookup"><span data-stu-id="bf1bb-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="bf1bb-109">Usare il [Metodo ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) per registrare l'implementazione di questa funzione.</span><span class="sxs-lookup"><span data-stu-id="bf1bb-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="bf1bb-110">La funzione `FunctionEnter3` è un callback. è necessario implementarla.</span><span class="sxs-lookup"><span data-stu-id="bf1bb-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="bf1bb-111">L'implementazione deve usare l'`__declspec(naked)` attributo della classe di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="bf1bb-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="bf1bb-112">Il motore di esecuzione non salva i registri prima di chiamare questa funzione.</span><span class="sxs-lookup"><span data-stu-id="bf1bb-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="bf1bb-113">In ingresso è necessario salvare tutti i registri utilizzati, inclusi quelli nell'unità a virgola mobile (FPU).</span><span class="sxs-lookup"><span data-stu-id="bf1bb-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="bf1bb-114">All'uscita è necessario ripristinare lo stack scegliendo tutti i parametri di cui è stato eseguito il push dal chiamante.</span><span class="sxs-lookup"><span data-stu-id="bf1bb-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf1bb-115">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="bf1bb-115">Requirements</span></span>  
 <span data-ttu-id="bf1bb-116">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf1bb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf1bb-117">**Intestazione:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="bf1bb-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="bf1bb-118">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf1bb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf1bb-119">**Versioni .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf1bb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf1bb-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bf1bb-120">See also</span></span>

- [<span data-ttu-id="bf1bb-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="bf1bb-121">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="bf1bb-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="bf1bb-122">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="bf1bb-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bf1bb-123">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="bf1bb-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bf1bb-124">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="bf1bb-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bf1bb-125">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="bf1bb-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="bf1bb-126">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="bf1bb-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="bf1bb-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="bf1bb-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="bf1bb-128">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="bf1bb-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="bf1bb-129">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="bf1bb-130">Funzioni statiche globali di profilatura</span><span class="sxs-lookup"><span data-stu-id="bf1bb-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
