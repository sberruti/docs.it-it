---
title: Enumerazione COR_PRF_REJIT_FLAGS
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177093"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="833ed-102">Enumerazione COR_PRF_REJIT_FLAGS</span><span class="sxs-lookup"><span data-stu-id="833ed-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="833ed-103">Contiene valori che indicano il funzionamento dell'API [ICorProfilerInfo10::RequestReJITWithInliners.](icorprofilerinfo10-requestrejitwithinliners-method.md)</span><span class="sxs-lookup"><span data-stu-id="833ed-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="833ed-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="833ed-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="833ed-105">Members</span><span class="sxs-lookup"><span data-stu-id="833ed-105">Members</span></span>  
  
|<span data-ttu-id="833ed-106">Membro</span><span class="sxs-lookup"><span data-stu-id="833ed-106">Member</span></span>|<span data-ttu-id="833ed-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="833ed-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="833ed-108">I metodi ReJITted non verranno bloccati inline in altri metodi.</span><span class="sxs-lookup"><span data-stu-id="833ed-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="833ed-109">Ricevere `GetFunctionParameters` callback per tutti i metodi che inline i metodi richiesti per essere ReJITted.</span><span class="sxs-lookup"><span data-stu-id="833ed-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="833ed-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="833ed-110">Requirements</span></span>  
 <span data-ttu-id="833ed-111">**Piattaforme:** Consultate [Sistemi operativi supportati da .NET Core.](../../../core/install/dependencies.md?pivots=os-windows)</span><span class="sxs-lookup"><span data-stu-id="833ed-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="833ed-112">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="833ed-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="833ed-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="833ed-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="833ed-114">**Versioni di .NET Framework:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="833ed-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="833ed-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="833ed-115">See also</span></span>

- [<span data-ttu-id="833ed-116">Enumerazioni di profilatura</span><span class="sxs-lookup"><span data-stu-id="833ed-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
