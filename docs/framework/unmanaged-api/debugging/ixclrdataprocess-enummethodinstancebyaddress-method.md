---
title: Metodo IXCLRDataProcess::EnumMethodInstanceByAddress
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 825cb8ea94bee980f9e10b90cddf04db32c1a33f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491909"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="770c8-102">Metodo IXCLRDataProcess::EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="770c8-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="770c8-103">Enumera le istanze di metodo di questo processo iniziando in corrispondenza di un offset di indirizzo.</span><span class="sxs-lookup"><span data-stu-id="770c8-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="770c8-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="770c8-104">Syntax</span></span>

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

### <a name="parameters"></a><span data-ttu-id="770c8-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="770c8-105">Parameters</span></span>

<span data-ttu-id="770c8-106">`handle` [in] Handle per l'enumerazione delle istanze di metodo.</span><span class="sxs-lookup"><span data-stu-id="770c8-106">`handle` [in] A handle for enumerating the method instances.</span></span>

<span data-ttu-id="770c8-107">`mod` [out] L'istanza del metodo enumerate.</span><span class="sxs-lookup"><span data-stu-id="770c8-107">`mod` [out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="770c8-108">Note</span><span class="sxs-lookup"><span data-stu-id="770c8-108">Remarks</span></span>

<span data-ttu-id="770c8-109">Il metodo specificato fa parte di `IXCLRDataProcess` interfaccia e corrisponde al 28 slot della tabella di metodo virtuale.</span><span class="sxs-lookup"><span data-stu-id="770c8-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="770c8-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="770c8-110">Requirements</span></span>

<span data-ttu-id="770c8-111">**Piattaforme:** Vedere [Requisiti di sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="770c8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="770c8-112">**Intestazione:** nessuno</span><span class="sxs-lookup"><span data-stu-id="770c8-112">**Header:** None</span></span>   
<span data-ttu-id="770c8-113">**Libreria:** nessuno</span><span class="sxs-lookup"><span data-stu-id="770c8-113">**Library:** None</span></span>   
<span data-ttu-id="770c8-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="770c8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="770c8-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="770c8-115">See also</span></span>
- [<span data-ttu-id="770c8-116">Enumerazione CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="770c8-116">CLRDataSourceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="770c8-117">Debug</span><span class="sxs-lookup"><span data-stu-id="770c8-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="770c8-118">IXCLRDataProcess Interface</span><span class="sxs-lookup"><span data-stu-id="770c8-118">IXCLRDataProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)