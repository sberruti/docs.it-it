---
title: Metodo ICorProfilerModuleEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
ms.openlocfilehash: 772a7c08c934fda59a2764e1fbe22d3d2b08a620
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861502"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="5daa6-102">Metodo ICorProfilerModuleEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="5daa6-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="5daa6-103">Ottiene il numero di moduli gestiti caricati nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5daa6-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5daa6-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5daa6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5daa6-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="5daa6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5daa6-106">out Numero di moduli di runtime nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="5daa6-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5daa6-107">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="5daa6-107">Requirements</span></span>  
 <span data-ttu-id="5daa6-108">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5daa6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5daa6-109">**Intestazione:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5daa6-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5daa6-110">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5daa6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5daa6-111">**Versioni .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5daa6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5daa6-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5daa6-112">See also</span></span>

- [<span data-ttu-id="5daa6-113">Interfaccia ICorProfilerModuleEnum</span><span class="sxs-lookup"><span data-stu-id="5daa6-113">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="5daa6-114">Interfacce di profilatura</span><span class="sxs-lookup"><span data-stu-id="5daa6-114">Profiling Interfaces</span></span>](profiling-interfaces.md)
