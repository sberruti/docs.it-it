---
title: Enumerazione CorDebugSetContextFlag
ms.date: 03/30/2017
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
ms.openlocfilehash: a443332e4f2b0351e99754fae610af39268bb105
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789273"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="4f13a-102">Enumerazione CorDebugSetContextFlag</span><span class="sxs-lookup"><span data-stu-id="4f13a-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="4f13a-103">Indica se il contesto proviene dal frame attivo (o foglia) sullo stack o se è stato calcolato dalla rimozione da un altro frame.</span><span class="sxs-lookup"><span data-stu-id="4f13a-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f13a-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4f13a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="4f13a-105">Membri</span><span class="sxs-lookup"><span data-stu-id="4f13a-105">Members</span></span>  
  
|<span data-ttu-id="4f13a-106">Member</span><span class="sxs-lookup"><span data-stu-id="4f13a-106">Member</span></span>|<span data-ttu-id="4f13a-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="4f13a-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4f13a-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="4f13a-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="4f13a-109">Il contesto è il contesto attivo del thread.</span><span class="sxs-lookup"><span data-stu-id="4f13a-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="4f13a-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="4f13a-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="4f13a-111">Il contesto è stato calcolato dalla rimozione da un altro frame.</span><span class="sxs-lookup"><span data-stu-id="4f13a-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f13a-112">Note</span><span class="sxs-lookup"><span data-stu-id="4f13a-112">Remarks</span></span>  
 <span data-ttu-id="4f13a-113">`CorDebugSetContextFlag` fornisce i valori utilizzati dal metodo [ICorDebugStackWalk:: secontext](icordebugstackwalk-setcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4f13a-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f13a-114">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="4f13a-114">Requirements</span></span>  
 <span data-ttu-id="4f13a-115">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f13a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f13a-116">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f13a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f13a-117">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f13a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f13a-118">**Versioni .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f13a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f13a-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4f13a-119">See also</span></span>

- [<span data-ttu-id="4f13a-120">Enumerazioni di debug</span><span class="sxs-lookup"><span data-stu-id="4f13a-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="4f13a-121">Debug</span><span class="sxs-lookup"><span data-stu-id="4f13a-121">Debugging</span></span>](index.md)
