---
title: Metodo IMetaDataImport::CountEnum
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: b780ca513d8a0b4f88e66594e86e9ff8290f6523
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177353"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="1ff6a-102">Metodo IMetaDataImport::CountEnum</span><span class="sxs-lookup"><span data-stu-id="1ff6a-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="1ff6a-103">Ottiene il numero di elementi nell'enumerazione recuperati dall'enumeratore specificato.</span><span class="sxs-lookup"><span data-stu-id="1ff6a-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ff6a-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="1ff6a-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ff6a-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="1ff6a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="1ff6a-106">[in] Handle per l'enumeratore.</span><span class="sxs-lookup"><span data-stu-id="1ff6a-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="1ff6a-107">[fuori] Numero di elementi enumerati.</span><span class="sxs-lookup"><span data-stu-id="1ff6a-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ff6a-108">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="1ff6a-108">Remarks</span></span>  
 <span data-ttu-id="1ff6a-109">L'handle `hEnum` specificato da viene `Enum`ottenuto da una precedente chiamata *a Name,* ad esempio [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md).</span><span class="sxs-lookup"><span data-stu-id="1ff6a-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ff6a-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1ff6a-110">Requirements</span></span>  
 <span data-ttu-id="1ff6a-111">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ff6a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ff6a-112">**Intestazione:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1ff6a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ff6a-113">**Biblioteca:** Incluso come risorsa in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1ff6a-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ff6a-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ff6a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff6a-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1ff6a-115">See also</span></span>

- [<span data-ttu-id="1ff6a-116">Interfaccia IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="1ff6a-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1ff6a-117">Interfaccia IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="1ff6a-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
