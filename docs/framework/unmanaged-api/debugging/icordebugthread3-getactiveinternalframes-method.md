---
title: Metodo ICorDebugThread3::GetActiveInternalFrames
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
ms.openlocfilehash: 25cd3e05bc80dd39d2ca558bb4dd5fb77d255f5a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791404"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="62ac4-102">Metodo ICorDebugThread3::GetActiveInternalFrames</span><span class="sxs-lookup"><span data-stu-id="62ac4-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="62ac4-103">Restituisce una matrice di frame interni (oggetti[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) nello stack.</span><span class="sxs-lookup"><span data-stu-id="62ac4-103">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ac4-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="62ac4-104">Syntax</span></span>  
  
```cpp 
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="62ac4-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="62ac4-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="62ac4-106">in Numero di frame interni previsti in `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="62ac4-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="62ac4-107">out Puntatore a un `ULONG32` che contiene il numero di frame interni nello stack.</span><span class="sxs-lookup"><span data-stu-id="62ac4-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="62ac4-108">[in, out] Puntatore all'indirizzo di una matrice di frame interni nello stack.</span><span class="sxs-lookup"><span data-stu-id="62ac4-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62ac4-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="62ac4-109">Return Value</span></span>  
 <span data-ttu-id="62ac4-110">Questo metodo restituisce gli specifici HRESULT seguenti, nonché gli errori di HRESULT che indicano la mancata riuscita del metodo.</span><span class="sxs-lookup"><span data-stu-id="62ac4-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="62ac4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62ac4-111">HRESULT</span></span>|<span data-ttu-id="62ac4-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="62ac4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62ac4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="62ac4-113">S_OK</span></span>|<span data-ttu-id="62ac4-114">Creazione dell'oggetto [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) completata.</span><span class="sxs-lookup"><span data-stu-id="62ac4-114">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="62ac4-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="62ac4-115">E_INVALIDARG</span></span>|<span data-ttu-id="62ac4-116">`cInternalFrames` non è zero e `ppInternalFrames` è `null`o `pcInternalFrames` è `null`.</span><span class="sxs-lookup"><span data-stu-id="62ac4-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="62ac4-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="62ac4-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="62ac4-118">`ppInternalFrames` è inferiore al numero di frame interni.</span><span class="sxs-lookup"><span data-stu-id="62ac4-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="62ac4-119">Eccezioni</span><span class="sxs-lookup"><span data-stu-id="62ac4-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62ac4-120">Note</span><span class="sxs-lookup"><span data-stu-id="62ac4-120">Remarks</span></span>  
 <span data-ttu-id="62ac4-121">I frame interni sono strutture di dati inserite nello stack dal runtime per archiviare i dati temporanei.</span><span class="sxs-lookup"><span data-stu-id="62ac4-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="62ac4-122">Quando si chiama per la prima volta `GetActiveInternalFrames`, è necessario impostare il parametro `cInternalFrames` su 0 (zero) e il parametro `ppInternalFrames` su null.</span><span class="sxs-lookup"><span data-stu-id="62ac4-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="62ac4-123">Quando `GetActiveInternalFrames` viene restituito per la prima volta, `pcInternalFrames` contiene il conteggio dei frame interni nello stack.</span><span class="sxs-lookup"><span data-stu-id="62ac4-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="62ac4-124">`GetActiveInternalFrames` deve quindi essere chiamato una seconda volta.</span><span class="sxs-lookup"><span data-stu-id="62ac4-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="62ac4-125">È necessario passare il conteggio appropriato (`pcInternalFrames`) nel parametro `cInternalFrames` e specificare un puntatore a una matrice di dimensioni appropriate in `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="62ac4-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="62ac4-126">Usare il metodo [ICorDebugStackWalk:: GetFrame](icordebugthread3-getactiveinternalframes-method.md) per restituire gli stack frame effettivi.</span><span class="sxs-lookup"><span data-stu-id="62ac4-126">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62ac4-127">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="62ac4-127">Requirements</span></span>  
 <span data-ttu-id="62ac4-128">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62ac4-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62ac4-129">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62ac4-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62ac4-130">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62ac4-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62ac4-131">**Versioni .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62ac4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ac4-132">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="62ac4-132">See also</span></span>

- [<span data-ttu-id="62ac4-133">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="62ac4-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="62ac4-134">Debug</span><span class="sxs-lookup"><span data-stu-id="62ac4-134">Debugging</span></span>](index.md)
