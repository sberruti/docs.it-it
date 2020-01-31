---
title: Metodo ICorDebug::EnumerateProcesses
ms.date: 03/30/2017
api_name:
- ICorDebug.EnumerateProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type:
- apiref
ms.openlocfilehash: c2a176764332eed6affda704c8bfaf546ef70880
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788996"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="d41a8-102">Metodo ICorDebug::EnumerateProcesses</span><span class="sxs-lookup"><span data-stu-id="d41a8-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="d41a8-103">Ottiene un enumeratore per i processi di cui è in corso il debug.</span><span class="sxs-lookup"><span data-stu-id="d41a8-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d41a8-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d41a8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d41a8-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="d41a8-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="d41a8-106">Puntatore all'indirizzo di un oggetto ICorDebugProcessEnum che rappresenta l'enumeratore per i processi di cui è in corso il debug.</span><span class="sxs-lookup"><span data-stu-id="d41a8-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d41a8-107">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="d41a8-107">Requirements</span></span>  
 <span data-ttu-id="d41a8-108">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d41a8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d41a8-109">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d41a8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d41a8-110">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d41a8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d41a8-111">**Versioni .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d41a8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d41a8-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d41a8-112">See also</span></span>

- [<span data-ttu-id="d41a8-113">Interfaccia ICorDebug</span><span class="sxs-lookup"><span data-stu-id="d41a8-113">ICorDebug Interface</span></span>](icordebug-interface.md)
