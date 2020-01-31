---
title: Funzione FunctionLeave
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: a9ab8c81c995bbec41db217c904e03dd70351aee
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866884"
---
# <a name="functionleave-function"></a><span data-ttu-id="afe54-102">Funzione FunctionLeave</span><span class="sxs-lookup"><span data-stu-id="afe54-102">FunctionLeave Function</span></span>
<span data-ttu-id="afe54-103">Notifica al profiler che una funzione sta per tornare al chiamante.</span><span class="sxs-lookup"><span data-stu-id="afe54-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afe54-104">La funzione `FunctionLeave` è deprecata nel .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="afe54-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="afe54-105">Continuerà a funzionare, ma comporterà una riduzione delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="afe54-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="afe54-106">Usare invece la funzione [FunctionLeave2](functionleave2-function.md) .</span><span class="sxs-lookup"><span data-stu-id="afe54-106">Use the [FunctionLeave2](functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afe54-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="afe54-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afe54-108">Parametri</span><span class="sxs-lookup"><span data-stu-id="afe54-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="afe54-109">\[in] identificatore della funzione che restituisce.</span><span class="sxs-lookup"><span data-stu-id="afe54-109">\[in] The identifier of the function that is returning.</span></span>

## <a name="remarks"></a><span data-ttu-id="afe54-110">Note</span><span class="sxs-lookup"><span data-stu-id="afe54-110">Remarks</span></span>  
 <span data-ttu-id="afe54-111">La funzione `FunctionLeave` è un callback. è necessario implementarla.</span><span class="sxs-lookup"><span data-stu-id="afe54-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="afe54-112">L'implementazione deve usare l'attributo della classe di archiviazione `__declspec`(`naked`).</span><span class="sxs-lookup"><span data-stu-id="afe54-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="afe54-113">Il motore di esecuzione non salva i registri prima di chiamare questa funzione.</span><span class="sxs-lookup"><span data-stu-id="afe54-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="afe54-114">In ingresso è necessario salvare tutti i registri utilizzati, inclusi quelli nell'unità a virgola mobile (FPU).</span><span class="sxs-lookup"><span data-stu-id="afe54-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="afe54-115">All'uscita è necessario ripristinare lo stack scegliendo tutti i parametri di cui è stato eseguito il push dal chiamante.</span><span class="sxs-lookup"><span data-stu-id="afe54-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="afe54-116">L'implementazione di `FunctionLeave` non deve bloccarsi perché ritarda Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="afe54-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="afe54-117">L'implementazione non deve tentare un Garbage Collection perché lo stack potrebbe non essere in uno stato descrittivo Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="afe54-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="afe54-118">Se viene effettuato un tentativo di Garbage Collection, il runtime si bloccherà fino a quando `FunctionLeave` non restituisce.</span><span class="sxs-lookup"><span data-stu-id="afe54-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="afe54-119">Inoltre, la funzione `FunctionLeave` non deve chiamare nel codice gestito o in alcun modo causare un'allocazione di managed memory.</span><span class="sxs-lookup"><span data-stu-id="afe54-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afe54-120">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="afe54-120">Requirements</span></span>  
 <span data-ttu-id="afe54-121">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afe54-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afe54-122">**Intestazione:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="afe54-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="afe54-123">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afe54-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afe54-124">**Versioni .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="afe54-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe54-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="afe54-125">See also</span></span>

- [<span data-ttu-id="afe54-126">Funzione FunctionEnter2</span><span class="sxs-lookup"><span data-stu-id="afe54-126">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="afe54-127">Funzione FunctionLeave2</span><span class="sxs-lookup"><span data-stu-id="afe54-127">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="afe54-128">Funzione FunctionTailcall2</span><span class="sxs-lookup"><span data-stu-id="afe54-128">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="afe54-129">Metodo SetEnterLeaveFunctionHooks2</span><span class="sxs-lookup"><span data-stu-id="afe54-129">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="afe54-130">Funzioni statiche globali di profilatura</span><span class="sxs-lookup"><span data-stu-id="afe54-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
