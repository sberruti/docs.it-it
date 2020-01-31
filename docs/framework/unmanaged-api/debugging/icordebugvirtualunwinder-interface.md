---
title: Interfaccia ICorDebugVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 065f71e45c2a56dbaa16a45f70958ca3dea80c48
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790832"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="218a0-102">Interfaccia ICorDebugVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="218a0-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="218a0-103">Fornisce metodi che facilitano lo svuotamento dello stack.</span><span class="sxs-lookup"><span data-stu-id="218a0-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="218a0-104">Metodi</span><span class="sxs-lookup"><span data-stu-id="218a0-104">Methods</span></span>  
  
|<span data-ttu-id="218a0-105">Metodo</span><span class="sxs-lookup"><span data-stu-id="218a0-105">Method</span></span>|<span data-ttu-id="218a0-106">Name</span><span class="sxs-lookup"><span data-stu-id="218a0-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="218a0-107">Metodo GetContext</span><span class="sxs-lookup"><span data-stu-id="218a0-107">GetContext Method</span></span>](icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="218a0-108">Ottiene il contesto corrente di questo agente di rimozione.</span><span class="sxs-lookup"><span data-stu-id="218a0-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="218a0-109">Metodo Next</span><span class="sxs-lookup"><span data-stu-id="218a0-109">Next Method</span></span>](icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="218a0-110">Avanza fino al contesto del chiamante.</span><span class="sxs-lookup"><span data-stu-id="218a0-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="218a0-111">Note</span><span class="sxs-lookup"><span data-stu-id="218a0-111">Remarks</span></span>  
 <span data-ttu-id="218a0-112">I membri dell'interfaccia `ICorDebugVirtualUnwinder` sono implementati dal debugger per agevolare lo svuotamento dello stack.</span><span class="sxs-lookup"><span data-stu-id="218a0-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="218a0-113">Questa interfaccia è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="218a0-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="218a0-114">Se questa interfaccia viene implementata per scenari ICorDebug al di fuori di .NET Native, sarà ignorata da Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="218a0-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="218a0-115">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="218a0-115">Requirements</span></span>  
 <span data-ttu-id="218a0-116">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="218a0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="218a0-117">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="218a0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="218a0-118">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="218a0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="218a0-119">**Versioni .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="218a0-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="218a0-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="218a0-120">See also</span></span>

- [<span data-ttu-id="218a0-121">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="218a0-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="218a0-122">Debug</span><span class="sxs-lookup"><span data-stu-id="218a0-122">Debugging</span></span>](index.md)
