---
title: Metodo ICorDebugILFrame::SetIP
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 466fe421f4ff3f8983159ccb38503b75551c87bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788550"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="476ed-102">Metodo ICorDebugILFrame::SetIP</span><span class="sxs-lookup"><span data-stu-id="476ed-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="476ed-103">Imposta il puntatore all'istruzione nella posizione di offset specificata nel codice MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="476ed-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476ed-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="476ed-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="476ed-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="476ed-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="476ed-106">Posizione dell'offset nel codice MSIL.</span><span class="sxs-lookup"><span data-stu-id="476ed-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="476ed-107">Note</span><span class="sxs-lookup"><span data-stu-id="476ed-107">Remarks</span></span>  
 <span data-ttu-id="476ed-108">Le chiamate a `SetIP` invalidano immediatamente tutti i frame e le catene per il thread corrente.</span><span class="sxs-lookup"><span data-stu-id="476ed-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="476ed-109">Se il debugger necessita di informazioni sul frame dopo una chiamata a `SetIP`, deve eseguire una nuova analisi dello stack.</span><span class="sxs-lookup"><span data-stu-id="476ed-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="476ed-110">[ICorDebug](icordebug-interface.md) tenterà di impedire la stack frame in uno stato valido.</span><span class="sxs-lookup"><span data-stu-id="476ed-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="476ed-111">Tuttavia, anche se il frame è in uno stato valido, potrebbero essere presenti problemi come le variabili locali non inizializzate.</span><span class="sxs-lookup"><span data-stu-id="476ed-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="476ed-112">Il chiamante è responsabile di garantire l'coerenza del programma in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="476ed-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="476ed-113">Nelle piattaforme a 64 bit il puntatore all'istruzione non può essere spostato all'esterno di un blocco `catch` o `finally`.</span><span class="sxs-lookup"><span data-stu-id="476ed-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="476ed-114">Se `SetIP` viene chiamato per eseguire tale spostamento su una piattaforma a 64 bit, viene restituito un valore HRESULT che indica un errore.</span><span class="sxs-lookup"><span data-stu-id="476ed-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="476ed-115">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="476ed-115">Requirements</span></span>  
 <span data-ttu-id="476ed-116">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="476ed-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="476ed-117">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="476ed-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="476ed-118">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="476ed-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="476ed-119">**Versioni .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="476ed-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
