---
title: Metodo IMetaDataEmit::DefineTypeRefByName
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
ms.openlocfilehash: 23a6931b31ea2d7e4e8d1cb3dc8adf3a51216315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175746"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="96f48-102">Metodo IMetaDataEmit::DefineTypeRefByName</span><span class="sxs-lookup"><span data-stu-id="96f48-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="96f48-103">Ottiene un token di metadati per un tipo definito nell'ambito specificato, che non rientra nell'ambito corrente.</span><span class="sxs-lookup"><span data-stu-id="96f48-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96f48-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="96f48-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96f48-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="96f48-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="96f48-106">[in] Token che specifica l'ambito di risoluzione.</span><span class="sxs-lookup"><span data-stu-id="96f48-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="96f48-107">I seguenti tipi di token sono validi:</span><span class="sxs-lookup"><span data-stu-id="96f48-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="96f48-108">`mdModuleRef`, se il tipo è definito nello stesso assembly in cui è definito il chiamante.</span><span class="sxs-lookup"><span data-stu-id="96f48-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="96f48-109">`mdAssemblyRef`, se il tipo è definito in un assembly diverso da quello in cui è definito il chiamante.</span><span class="sxs-lookup"><span data-stu-id="96f48-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="96f48-110">`mdTypeRef`, se il tipo è un tipo annidato.</span><span class="sxs-lookup"><span data-stu-id="96f48-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="96f48-111">`mdModule`, se il tipo è definito nello stesso modulo in cui è definito il chiamante.</span><span class="sxs-lookup"><span data-stu-id="96f48-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="96f48-112">Null, se il tipo è definito globalmente.</span><span class="sxs-lookup"><span data-stu-id="96f48-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="96f48-113">[in] Nome del tipo di destinazione in Unicode.</span><span class="sxs-lookup"><span data-stu-id="96f48-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="96f48-114">[fuori] Puntatore al `mdTypeRef` token assegnato al tipo.</span><span class="sxs-lookup"><span data-stu-id="96f48-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96f48-115">Requisiti</span><span class="sxs-lookup"><span data-stu-id="96f48-115">Requirements</span></span>  
 <span data-ttu-id="96f48-116">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96f48-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96f48-117">**Intestazione:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="96f48-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96f48-118">**Biblioteca:** Utilizzato come risorsa in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96f48-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96f48-119">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96f48-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96f48-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="96f48-120">See also</span></span>

- [<span data-ttu-id="96f48-121">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="96f48-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="96f48-122">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="96f48-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
