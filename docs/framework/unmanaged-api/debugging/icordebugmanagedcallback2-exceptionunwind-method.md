---
title: Metodo ICorDebugManagedCallback2::ExceptionUnwind
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: 482afd09ce370fb1247864b9ac2032ee7e3a1dca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788283"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="a060b-102">Metodo ICorDebugManagedCallback2::ExceptionUnwind</span><span class="sxs-lookup"><span data-stu-id="a060b-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="a060b-103">Fornisce una notifica di stato durante il processo di rimozione dell'eccezione.</span><span class="sxs-lookup"><span data-stu-id="a060b-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a060b-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="a060b-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a060b-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="a060b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a060b-106">in Puntatore a un oggetto ICorDebugAppDomain che rappresenta il dominio applicazione contenente il thread in cui è stata generata l'eccezione.</span><span class="sxs-lookup"><span data-stu-id="a060b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a060b-107">in Puntatore a un oggetto ICorDebugThread che rappresenta il thread in cui è stata generata l'eccezione.</span><span class="sxs-lookup"><span data-stu-id="a060b-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="a060b-108">in Valore dell'enumerazione CorDebugExceptionUnwindCallbackType che specifica l'evento che viene segnalato dal callback durante la fase di rimozione.</span><span class="sxs-lookup"><span data-stu-id="a060b-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a060b-109">in Valore dell'enumerazione [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) che specifica informazioni aggiuntive sull'eccezione.</span><span class="sxs-lookup"><span data-stu-id="a060b-109">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a060b-110">Note</span><span class="sxs-lookup"><span data-stu-id="a060b-110">Remarks</span></span>  
 <span data-ttu-id="a060b-111">`ExceptionUnwind` viene chiamato in diversi punti durante la fase di rimozione del processo di gestione delle eccezioni.</span><span class="sxs-lookup"><span data-stu-id="a060b-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="a060b-112">`ExceptionUnwind` può essere chiamato più volte durante la rimozione di una singola eccezione.</span><span class="sxs-lookup"><span data-stu-id="a060b-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="a060b-113">Se `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, il puntatore all'istruzione si troverà nel frame foglia del thread, in corrispondenza del punto di sequenza precedente (le istruzioni potrebbero essere diverse prima di) l'istruzione che ha generato l'eccezione.</span><span class="sxs-lookup"><span data-stu-id="a060b-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a060b-114">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="a060b-114">Requirements</span></span>  
 <span data-ttu-id="a060b-115">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a060b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a060b-116">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a060b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a060b-117">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a060b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a060b-118">**Versioni .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a060b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a060b-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a060b-119">See also</span></span>

- [<span data-ttu-id="a060b-120">Interfaccia ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="a060b-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="a060b-121">Interfaccia ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="a060b-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
