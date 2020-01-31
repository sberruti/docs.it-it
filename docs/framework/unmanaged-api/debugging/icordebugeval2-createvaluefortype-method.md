---
title: Metodo ICorDebugEval2::CreateValueForType
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: 8632799b68ae8f92835d1774472bc1432d886f3b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793476"
---
# <a name="icordebugeval2createvaluefortype-method"></a><span data-ttu-id="b05ed-102">Metodo ICorDebugEval2::CreateValueForType</span><span class="sxs-lookup"><span data-stu-id="b05ed-102">ICorDebugEval2::CreateValueForType Method</span></span>
<span data-ttu-id="b05ed-103">Ottiene un puntatore a un nuovo ICorDebugValue del tipo specificato, con un valore iniziale pari a zero o null.</span><span class="sxs-lookup"><span data-stu-id="b05ed-103">Gets a pointer to a new ICorDebugValue of the specified type, with an initial value of zero or null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b05ed-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="b05ed-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b05ed-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="b05ed-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="b05ed-106">in Puntatore a un oggetto ICorDebugType che rappresenta il tipo.</span><span class="sxs-lookup"><span data-stu-id="b05ed-106">[in] Pointer to an ICorDebugType object that represents the type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b05ed-107">out Puntatore all'indirizzo di un `ICorDebugValue` oggetto che rappresenta il valore.</span><span class="sxs-lookup"><span data-stu-id="b05ed-107">[out] Pointer to the address of an `ICorDebugValue` object that represents the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b05ed-108">Note</span><span class="sxs-lookup"><span data-stu-id="b05ed-108">Remarks</span></span>  
 <span data-ttu-id="b05ed-109">`CreateValueForType` generalizza [ICorDebugEval:: CreateValue](icordebugeval-createvalue-method.md) consentendo di specificare un tipo di oggetto arbitrario, inclusi i tipi costruiti, ad esempio `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="b05ed-109">`CreateValueForType` generalizes [ICorDebugEval::CreateValue](icordebugeval-createvalue-method.md) by allowing you to specify an arbitrary object type, including constructed types such as `List<int>`.</span></span> <span data-ttu-id="b05ed-110">L'unico scopo di questo metodo è generare un valore che può essere passato a una valutazione di funzione.</span><span class="sxs-lookup"><span data-stu-id="b05ed-110">The only purpose of this method is to generate a value that can be passed to a function evaluation.</span></span>  
  
 <span data-ttu-id="b05ed-111">Il tipo deve essere una classe o un tipo valore.</span><span class="sxs-lookup"><span data-stu-id="b05ed-111">The type must be a class or a value type.</span></span> <span data-ttu-id="b05ed-112">Non è possibile usare questo metodo per creare valori di stringa o di matrice.</span><span class="sxs-lookup"><span data-stu-id="b05ed-112">You cannot use this method to create array values or string values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b05ed-113">Requisiti di</span><span class="sxs-lookup"><span data-stu-id="b05ed-113">Requirements</span></span>  
 <span data-ttu-id="b05ed-114">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b05ed-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b05ed-115">**Intestazione:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b05ed-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b05ed-116">**Libreria:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b05ed-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b05ed-117">**Versioni .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b05ed-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
