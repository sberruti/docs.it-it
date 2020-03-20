---
title: Metodo GetScope2
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
ms.openlocfilehash: 40df78cdf99c2e0f53be9664f3f5c6386b6c6f93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179401"
---
# <a name="getscope2-method"></a><span data-ttu-id="4374e-102">Metodo GetScope2</span><span class="sxs-lookup"><span data-stu-id="4374e-102">GetScope2 Method</span></span>
<span data-ttu-id="4374e-103">Ottiene un ambito di importazione.</span><span class="sxs-lookup"><span data-stu-id="4374e-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4374e-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4374e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="4374e-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="4374e-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4374e-106">ID dell'assembly di destinazione.</span><span class="sxs-lookup"><span data-stu-id="4374e-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4374e-107">ID del file da cui eseguire l'importazione.</span><span class="sxs-lookup"><span data-stu-id="4374e-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="4374e-108">Ambito in base zero da importare.</span><span class="sxs-lookup"><span data-stu-id="4374e-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="4374e-109">Riceve il puntatore [all'interfaccia IMetaDataImport2 per l'ambito](../metadata/imetadataimport2-interface.md) indicato.</span><span class="sxs-lookup"><span data-stu-id="4374e-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4374e-110">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4374e-110">Return Value</span></span>  
 <span data-ttu-id="4374e-111">Restituisce S_OK se il metodo ha esito positivo.</span><span class="sxs-lookup"><span data-stu-id="4374e-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4374e-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4374e-112">Requirements</span></span>  
 <span data-ttu-id="4374e-113">Richiede alink.h.</span><span class="sxs-lookup"><span data-stu-id="4374e-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4374e-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4374e-114">See also</span></span>

- [<span data-ttu-id="4374e-115">Interfaccia IALink2</span><span class="sxs-lookup"><span data-stu-id="4374e-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4374e-116">Interfaccia IALink</span><span class="sxs-lookup"><span data-stu-id="4374e-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4374e-117">API Alink</span><span class="sxs-lookup"><span data-stu-id="4374e-117">ALink API</span></span>](index.md)
