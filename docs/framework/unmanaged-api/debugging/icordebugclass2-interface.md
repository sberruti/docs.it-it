---
title: Interfaccia ICorDebugClass2
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: 795e9f4862992d95eeef98a986545cca47d828c6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784137"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="7f7c2-102">Interfaccia ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="7f7c2-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="7f7c2-103">Rappresenta una classe generica oppure una classe con un parametro di metodo di tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="7f7c2-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="7f7c2-104">Questa interfaccia estende [ICorDebugClass](icordebugclass-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7f7c2-104">This interface extends [ICorDebugClass](icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f7c2-105">Metodi</span><span class="sxs-lookup"><span data-stu-id="7f7c2-105">Methods</span></span>  
  
|<span data-ttu-id="7f7c2-106">Metodo</span><span class="sxs-lookup"><span data-stu-id="7f7c2-106">Method</span></span>|<span data-ttu-id="7f7c2-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="7f7c2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f7c2-108">Metodo GetParameterizedType</span><span class="sxs-lookup"><span data-stu-id="7f7c2-108">GetParameterizedType Method</span></span>](icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="7f7c2-109">Ottiene la dichiarazione del tipo per questa classe.</span><span class="sxs-lookup"><span data-stu-id="7f7c2-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="7f7c2-110">Metodo SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="7f7c2-110">SetJMCStatus Method</span></span>](icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="7f7c2-111">Per ogni metodo di questa classe, imposta un valore che indica se il metodo è codice definito dall'utente.</span><span class="sxs-lookup"><span data-stu-id="7f7c2-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f7c2-112">Note</span><span class="sxs-lookup"><span data-stu-id="7f7c2-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f7c2-113">Questa interfaccia non supporta la chiamata in modalità remota, tra computer o tra processi.</span><span class="sxs-lookup"><span data-stu-id="7f7c2-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f7c2-114">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="7f7c2-114">Requirements</span></span>  
 <span data-ttu-id="7f7c2-115">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f7c2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f7c2-116">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f7c2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f7c2-117">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f7c2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f7c2-118">**Versioni .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f7c2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7c2-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7f7c2-119">See also</span></span>

- [<span data-ttu-id="7f7c2-120">Interfaccia ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="7f7c2-120">ICorDebugClass Interface</span></span>](icordebugclass-interface.md)
- [<span data-ttu-id="7f7c2-121">Interfacce di debug</span><span class="sxs-lookup"><span data-stu-id="7f7c2-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
