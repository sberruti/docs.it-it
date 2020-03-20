---
title: Metodo IMetaDataEmit::SetCustomAttributeValue
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
ms.openlocfilehash: 25b7f478ae0bd05b82fa960561fb8534efe2b4db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175668"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="20e44-102">Metodo IMetaDataEmit::SetCustomAttributeValue</span><span class="sxs-lookup"><span data-stu-id="20e44-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="20e44-103">Imposta o aggiorna il valore di un attributo personalizzato definito da una precedente chiamata a [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="20e44-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20e44-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="20e44-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20e44-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="20e44-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="20e44-106">[in] Token dell'attributo personalizzato di destinazione.</span><span class="sxs-lookup"><span data-stu-id="20e44-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="20e44-107">[in] Puntatore alla matrice che contiene l'attributo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="20e44-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="20e44-108">[in] Dimensione, in byte, dell'attributo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="20e44-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20e44-109">Requisiti</span><span class="sxs-lookup"><span data-stu-id="20e44-109">Requirements</span></span>  
 <span data-ttu-id="20e44-110">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20e44-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20e44-111">**Intestazione:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="20e44-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20e44-112">**Biblioteca:** Utilizzato come risorsa in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20e44-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20e44-113">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20e44-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20e44-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="20e44-114">See also</span></span>

- [<span data-ttu-id="20e44-115">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="20e44-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="20e44-116">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="20e44-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
