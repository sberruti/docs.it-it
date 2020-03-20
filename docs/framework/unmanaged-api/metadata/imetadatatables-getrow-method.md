---
title: Metodo IMetaDataTables::GetRow
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177112"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="226e2-102">Metodo IMetaDataTables::GetRow</span><span class="sxs-lookup"><span data-stu-id="226e2-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="226e2-103">Ottiene la riga in corrispondenza dell'indice di riga specificato, nella tabella in corrispondenza dell'indice di tabella specificato.</span><span class="sxs-lookup"><span data-stu-id="226e2-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="226e2-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="226e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="226e2-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="226e2-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="226e2-106">[in] Indice della tabella da cui verrà recuperata la riga.</span><span class="sxs-lookup"><span data-stu-id="226e2-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="226e2-107">[in] Indice della riga da ottenere.</span><span class="sxs-lookup"><span data-stu-id="226e2-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="226e2-108">[fuori] Puntatore a un puntatore alla riga.</span><span class="sxs-lookup"><span data-stu-id="226e2-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="226e2-109">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="226e2-109">Remarks</span></span>  

  <span data-ttu-id="226e2-110">Non è consigliabile utilizzare questo metodo, perché non restituisce risultati coerenti.</span><span class="sxs-lookup"><span data-stu-id="226e2-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="226e2-111">Per informazioni sulla tabella GUID, vedere la documentazione di Common Language Infrastructure (CLI), in particolare "Partition II: Metadata Definition and Semantics".</span><span class="sxs-lookup"><span data-stu-id="226e2-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="226e2-112">La documentazione è disponibile online; vedere [ECMA c'è e Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) e Standard [ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="226e2-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="226e2-113">Requisiti</span><span class="sxs-lookup"><span data-stu-id="226e2-113">Requirements</span></span>  
 <span data-ttu-id="226e2-114">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="226e2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="226e2-115">**Intestazione:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="226e2-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="226e2-116">**Biblioteca:** Utilizzato come risorsa in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="226e2-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="226e2-117">**Versioni di .NET Framework**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="226e2-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226e2-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="226e2-118">See also</span></span>

- [<span data-ttu-id="226e2-119">Interfaccia IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="226e2-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="226e2-120">Interfaccia IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="226e2-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
