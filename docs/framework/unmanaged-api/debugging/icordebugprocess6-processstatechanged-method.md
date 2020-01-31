---
title: Metodo ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: b6665df550a2d07a3fa84c3f2b6bf07f459cd713
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792209"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="5b858-102">Metodo ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="5b858-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="5b858-103">Notifica a [ICorDebug](icordebug-interface.md) che il processo è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="5b858-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b858-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5b858-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b858-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="5b858-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="5b858-106">in Membro dell'enumerazione [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="5b858-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b858-107">Note</span><span class="sxs-lookup"><span data-stu-id="5b858-107">Remarks</span></span>  
 <span data-ttu-id="5b858-108">Il debugger chiama questo metodo per notificare a [ICorDebug](icordebug-interface.md) che il processo è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="5b858-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b858-109">Questo metodo è disponibile solo con .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5b858-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b858-110">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="5b858-110">Requirements</span></span>  
 <span data-ttu-id="5b858-111">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b858-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b858-112">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b858-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b858-113">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b858-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b858-114">**Versioni .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b858-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b858-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5b858-115">See also</span></span>

- [<span data-ttu-id="5b858-116">Interfaccia ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="5b858-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="5b858-117">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="5b858-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
