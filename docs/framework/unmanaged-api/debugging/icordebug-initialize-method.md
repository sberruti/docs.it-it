---
title: Metodo ICorDebug::Initialize
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
ms.openlocfilehash: 3d27cf1987d7e9896885f87857554f4039c8d714
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788985"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="9c0da-102">Metodo ICorDebug::Initialize</span><span class="sxs-lookup"><span data-stu-id="9c0da-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="9c0da-103">Inizializza l'oggetto `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="9c0da-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c0da-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9c0da-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9c0da-105">Note</span><span class="sxs-lookup"><span data-stu-id="9c0da-105">Remarks</span></span>  
 <span data-ttu-id="9c0da-106">Il debugger deve chiamare `Initialize` al momento della creazione per inizializzare i servizi di debug.</span><span class="sxs-lookup"><span data-stu-id="9c0da-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="9c0da-107">Questo metodo deve essere chiamato prima di chiamare qualsiasi altro metodo in `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="9c0da-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c0da-108">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="9c0da-108">Requirements</span></span>  
 <span data-ttu-id="9c0da-109">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c0da-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c0da-110">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c0da-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c0da-111">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c0da-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c0da-112">**Versioni .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c0da-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0da-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9c0da-113">See also</span></span>

- [<span data-ttu-id="9c0da-114">Interfaccia ICorDebug</span><span class="sxs-lookup"><span data-stu-id="9c0da-114">ICorDebug Interface</span></span>](icordebug-interface.md)
