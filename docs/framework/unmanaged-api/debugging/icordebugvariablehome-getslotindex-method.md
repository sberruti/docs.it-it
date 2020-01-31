---
title: 'Metodo ICorDebugVariableHome:: GetSlotIndex'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 542bfa05c55ef224d1b9111f9af6c069e9e23542
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790977"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="cae59-102">Metodo ICorDebugVariableHome:: GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="cae59-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="cae59-103">Ottiene l'indice di slot gestito di una variabile locale.</span><span class="sxs-lookup"><span data-stu-id="cae59-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cae59-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="cae59-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cae59-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="cae59-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="cae59-106">out Puntatore all'indice di slot di una variabile locale.</span><span class="sxs-lookup"><span data-stu-id="cae59-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cae59-107">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="cae59-107">Return Value</span></span>  
 <span data-ttu-id="cae59-108">Il metodo restituisce i valori seguenti.</span><span class="sxs-lookup"><span data-stu-id="cae59-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="cae59-109">Valore</span><span class="sxs-lookup"><span data-stu-id="cae59-109">Value</span></span>|<span data-ttu-id="cae59-110">Descrizione</span><span class="sxs-lookup"><span data-stu-id="cae59-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="cae59-111">La chiamata al metodo ha restituito un valore di indice di slot in `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="cae59-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="cae59-112">L'istanza corrente di [ICorDebugVariableHome](icordebugvariablehome-interface.md) rappresenta un argomento della funzione.</span><span class="sxs-lookup"><span data-stu-id="cae59-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cae59-113">Note</span><span class="sxs-lookup"><span data-stu-id="cae59-113">Remarks</span></span>  
 <span data-ttu-id="cae59-114">Lo slot-index può essere usato per recuperare i metadati per la variabile locale.</span><span class="sxs-lookup"><span data-stu-id="cae59-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cae59-115">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="cae59-115">Requirements</span></span>  
 <span data-ttu-id="cae59-116">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cae59-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cae59-117">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cae59-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cae59-118">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cae59-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cae59-119">**Versioni .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cae59-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae59-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="cae59-120">See also</span></span>

- [<span data-ttu-id="cae59-121">Interfaccia ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="cae59-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
