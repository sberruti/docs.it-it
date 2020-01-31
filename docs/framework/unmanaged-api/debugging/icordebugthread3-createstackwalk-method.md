---
title: Metodo ICorDebugThread3::CreateStackWalk
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
ms.openlocfilehash: 64f6bc9abb8105cdfa942c2aaca71994e8a91765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791407"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="bdf01-102">Metodo ICorDebugThread3::CreateStackWalk</span><span class="sxs-lookup"><span data-stu-id="bdf01-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="bdf01-103">Crea un oggetto [ICorDebugStackWalk](icordebugstackwalk-interface.md) per il thread il cui stack si vuole rimuovere.</span><span class="sxs-lookup"><span data-stu-id="bdf01-103">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdf01-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="bdf01-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdf01-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="bdf01-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="bdf01-106">out Puntatore all'indirizzo dell'oggetto [ICorDebugStackWalk](icordebugstackwalk-interface.md) per il thread di cui si desidera rimuovere lo stack.</span><span class="sxs-lookup"><span data-stu-id="bdf01-106">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bdf01-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="bdf01-107">Return Value</span></span>  
 <span data-ttu-id="bdf01-108">Questo metodo restituisce gli specifici HRESULT seguenti, nonché gli errori di HRESULT che indicano la mancata riuscita del metodo.</span><span class="sxs-lookup"><span data-stu-id="bdf01-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bdf01-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bdf01-109">HRESULT</span></span>|<span data-ttu-id="bdf01-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="bdf01-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bdf01-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bdf01-111">S_OK</span></span>|<span data-ttu-id="bdf01-112">Creazione dell'oggetto `ICorDebugStackWalk` completata.</span><span class="sxs-lookup"><span data-stu-id="bdf01-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="bdf01-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bdf01-113">E_FAIL</span></span>|<span data-ttu-id="bdf01-114">L'oggetto `ICorDebugStackWalk` non è stato creato.</span><span class="sxs-lookup"><span data-stu-id="bdf01-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="bdf01-115">Eccezioni</span><span class="sxs-lookup"><span data-stu-id="bdf01-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdf01-116">Note</span><span class="sxs-lookup"><span data-stu-id="bdf01-116">Remarks</span></span>  
 <span data-ttu-id="bdf01-117">Se il metodo `CreateStackWalk` ha esito positivo, il contesto dell'oggetto `ICorDebugStackWalk` restituito viene impostato sul contesto corrente del thread.</span><span class="sxs-lookup"><span data-stu-id="bdf01-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdf01-118">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="bdf01-118">Requirements</span></span>  
 <span data-ttu-id="bdf01-119">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdf01-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdf01-120">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdf01-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdf01-121">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdf01-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdf01-122">**Versioni .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdf01-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf01-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bdf01-123">See also</span></span>

- [<span data-ttu-id="bdf01-124">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="bdf01-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="bdf01-125">Debug</span><span class="sxs-lookup"><span data-stu-id="bdf01-125">Debugging</span></span>](index.md)
