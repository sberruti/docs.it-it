---
title: Metodo ICorDebugModule::IsDynamic
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 45b1d0c0a3199227ab644ba8732198dd14b1cb4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793002"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="e7bc3-102">Metodo ICorDebugModule::IsDynamic</span><span class="sxs-lookup"><span data-stu-id="e7bc3-102">ICorDebugModule::IsDynamic Method</span></span>
<span data-ttu-id="e7bc3-103">Ottiene un valore che indica se il modulo è dinamico.</span><span class="sxs-lookup"><span data-stu-id="e7bc3-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7bc3-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="e7bc3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7bc3-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="e7bc3-105">Parameters</span></span>  
 `pDynamic`  
 <span data-ttu-id="e7bc3-106">[out] `true` se il modulo è dinamico; in caso contrario, `false`.</span><span class="sxs-lookup"><span data-stu-id="e7bc3-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7bc3-107">Note</span><span class="sxs-lookup"><span data-stu-id="e7bc3-107">Remarks</span></span>  
 <span data-ttu-id="e7bc3-108">Un modulo dinamico può aggiungere nuove classi ed eliminare le classi esistenti anche dopo il caricamento del modulo.</span><span class="sxs-lookup"><span data-stu-id="e7bc3-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="e7bc3-109">I callback [ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) e [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) indicano al debugger quando una classe è stata aggiunta o eliminata.</span><span class="sxs-lookup"><span data-stu-id="e7bc3-109">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7bc3-110">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="e7bc3-110">Requirements</span></span>  
 <span data-ttu-id="e7bc3-111">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7bc3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7bc3-112">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7bc3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7bc3-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7bc3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7bc3-114">**Versioni .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7bc3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
