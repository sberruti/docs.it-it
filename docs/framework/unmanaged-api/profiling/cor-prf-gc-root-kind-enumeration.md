---
title: Enumerazione COR_PRF_GC_ROOT_KIND
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: bff45e6f6f57b95d07ac5073cb70020818cce000
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867165"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="65e42-102">Enumerazione COR_PRF_GC_ROOT_KIND</span><span class="sxs-lookup"><span data-stu-id="65e42-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="65e42-103">Indica il tipo di Garbage Collection radice esposto dal callback [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="65e42-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e42-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="65e42-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="65e42-105">Membri</span><span class="sxs-lookup"><span data-stu-id="65e42-105">Members</span></span>  
  
|<span data-ttu-id="65e42-106">Member</span><span class="sxs-lookup"><span data-stu-id="65e42-106">Member</span></span>|<span data-ttu-id="65e42-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="65e42-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="65e42-108">La radice è una variabile nello stack.</span><span class="sxs-lookup"><span data-stu-id="65e42-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="65e42-109">La radice è una voce nella coda del finalizzatore.</span><span class="sxs-lookup"><span data-stu-id="65e42-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="65e42-110">La radice è un handle Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="65e42-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="65e42-111">Il tipo di radice non è specificato.</span><span class="sxs-lookup"><span data-stu-id="65e42-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65e42-112">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="65e42-112">Requirements</span></span>  
 <span data-ttu-id="65e42-113">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65e42-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65e42-114">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65e42-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65e42-115">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65e42-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65e42-116">**Versioni .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65e42-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e42-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="65e42-117">See also</span></span>

- [<span data-ttu-id="65e42-118">Enumerazioni di profilatura</span><span class="sxs-lookup"><span data-stu-id="65e42-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
