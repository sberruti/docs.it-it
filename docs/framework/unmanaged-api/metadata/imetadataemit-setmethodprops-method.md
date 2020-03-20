---
title: Metodo IMetaDataEmit::SetMethodProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: 9662a14b4ea97aed16968083489324d46c38dda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177517"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="f11f8-102">Metodo IMetaDataEmit::SetMethodProps</span><span class="sxs-lookup"><span data-stu-id="f11f8-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="f11f8-103">Imposta o aggiorna la funzionalità, archiviata in corrispondenza dell'indirizzo virtuale relativo specificato, di un metodo definito da una precedente chiamata a [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="f11f8-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f11f8-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f11f8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f11f8-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="f11f8-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="f11f8-106">[in] Token per il metodo da modificare.</span><span class="sxs-lookup"><span data-stu-id="f11f8-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="f11f8-107">[in] Attributi del membro.</span><span class="sxs-lookup"><span data-stu-id="f11f8-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="f11f8-108">[in] Indirizzo del codice.</span><span class="sxs-lookup"><span data-stu-id="f11f8-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="f11f8-109">[in] Flag di implementazione per il metodo.</span><span class="sxs-lookup"><span data-stu-id="f11f8-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f11f8-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="f11f8-110">Requirements</span></span>  
 <span data-ttu-id="f11f8-111">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f11f8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f11f8-112">**Intestazione:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f11f8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f11f8-113">**Biblioteca:** Utilizzato come risorsa in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f11f8-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f11f8-114">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f11f8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f11f8-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f11f8-115">See also</span></span>

- [<span data-ttu-id="f11f8-116">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="f11f8-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f11f8-117">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="f11f8-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
