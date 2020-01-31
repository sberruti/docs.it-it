---
title: Metodo ICorProfilerObjectEnum::Skip
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
ms.openlocfilehash: 096489fcdc9d604e003386501c22967b45ba6d7f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861110"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="73fd8-102">Metodo ICorProfilerObjectEnum::Skip</span><span class="sxs-lookup"><span data-stu-id="73fd8-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="73fd8-103">Sposta in avanti il cursore dell'enumeratore dalla posizione corrente, in modo che il numero di elementi specificato venga ignorato.</span><span class="sxs-lookup"><span data-stu-id="73fd8-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73fd8-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="73fd8-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73fd8-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="73fd8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="73fd8-106">in Numero di elementi da ignorare.</span><span class="sxs-lookup"><span data-stu-id="73fd8-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73fd8-107">Note</span><span class="sxs-lookup"><span data-stu-id="73fd8-107">Remarks</span></span>  
 <span data-ttu-id="73fd8-108">La nuova posizione del cursore di questo enumeratore è: (posizione corrente) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="73fd8-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73fd8-109">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="73fd8-109">Requirements</span></span>  
 <span data-ttu-id="73fd8-110">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73fd8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73fd8-111">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73fd8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73fd8-112">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73fd8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73fd8-113">**Versioni .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73fd8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fd8-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="73fd8-114">See also</span></span>

- [<span data-ttu-id="73fd8-115">Interfaccia ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="73fd8-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
