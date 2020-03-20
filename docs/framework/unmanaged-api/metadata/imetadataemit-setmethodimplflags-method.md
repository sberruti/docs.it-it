---
title: Metodo IMetaDataEmit::SetMethodImplFlags
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
ms.openlocfilehash: 7ed7770f26ea4620d79f3be3f67e72f73c75057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175629"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="9b0d2-102">Metodo IMetaDataEmit::SetMethodImplFlags</span><span class="sxs-lookup"><span data-stu-id="9b0d2-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="9b0d2-103">Imposta o aggiorna la firma dei metadati dell'implementazione del metodo ereditato a cui fa riferimento il token specificato.</span><span class="sxs-lookup"><span data-stu-id="9b0d2-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0d2-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="9b0d2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b0d2-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="9b0d2-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="9b0d2-106">[in] Token per il metodo da modificare.</span><span class="sxs-lookup"><span data-stu-id="9b0d2-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="9b0d2-107">[in] Combinazione dei valori dell'enumerazione [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) che specifica le funzionalità di implementazione del metodo.</span><span class="sxs-lookup"><span data-stu-id="9b0d2-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b0d2-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9b0d2-108">Requirements</span></span>  
 <span data-ttu-id="9b0d2-109">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b0d2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b0d2-110">**Intestazione:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9b0d2-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b0d2-111">**Biblioteca:** Utilizzato come risorsa in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b0d2-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b0d2-112">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b0d2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b0d2-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="9b0d2-113">See also</span></span>

- [<span data-ttu-id="9b0d2-114">Interfaccia IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="9b0d2-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9b0d2-115">Interfaccia IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="9b0d2-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
