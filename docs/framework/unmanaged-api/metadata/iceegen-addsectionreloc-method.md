---
title: Metodo ICeeGen::AddSectionReloc
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: 129750644962cee3206b9e38cbeaa77d38dddd71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176110"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="8f42b-102">Metodo ICeeGen::AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="8f42b-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="8f42b-103">Aggiunge un'istruzione .reloc alla base di codice.</span><span class="sxs-lookup"><span data-stu-id="8f42b-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="8f42b-104">Questo metodo è obsoleto e non deve essere utilizzato.</span><span class="sxs-lookup"><span data-stu-id="8f42b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f42b-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8f42b-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f42b-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="8f42b-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="8f42b-107">[in] Sezione di codice in memoria a cui aggiungere un'istruzione .reloc.</span><span class="sxs-lookup"><span data-stu-id="8f42b-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="8f42b-108">[in] Offset della sezione.</span><span class="sxs-lookup"><span data-stu-id="8f42b-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="8f42b-109">[in] Sezione a `offset` cui si riferisce.</span><span class="sxs-lookup"><span data-stu-id="8f42b-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="8f42b-110">[in] Uno dei [valori di CeeSectionRelocType,](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) che indica il tipo di istruzione .reloc da aggiungere.</span><span class="sxs-lookup"><span data-stu-id="8f42b-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f42b-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="8f42b-111">Requirements</span></span>  
 <span data-ttu-id="8f42b-112">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f42b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f42b-113">**Intestazione:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8f42b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f42b-114">**Biblioteca:** Utilizzato come risorsa in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f42b-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f42b-115">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f42b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f42b-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8f42b-116">See also</span></span>

- [<span data-ttu-id="8f42b-117">Interfaccia ICeeGen</span><span class="sxs-lookup"><span data-stu-id="8f42b-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
