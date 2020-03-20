---
title: Enumerazione ASM_NAME
ms.date: 03/30/2017
api_name:
- ASM_NAME
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_NAME
helpviewer_keywords:
- ASM_NAME enumeration [.NET Framework fusion]
ms.assetid: c8b65b19-d777-428f-bc0c-0d84c78a37bc
topic_type:
- apiref
ms.openlocfilehash: fb77fe470829570d5abe291249eb7ef9023e6b14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178303"
---
# <a name="asm_name-enumeration"></a><span data-ttu-id="6e224-102">Enumerazione ASM_NAME</span><span class="sxs-lookup"><span data-stu-id="6e224-102">ASM_NAME Enumeration</span></span>
<span data-ttu-id="6e224-103">Indica la versione, la compilazione, le impostazioni cultura, la firma e così via, dell'assembly le cui proprietà verranno recuperate o impostate dai metodi [IAssemblyName.](iassemblyname-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6e224-103">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](iassemblyname-interface.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e224-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="6e224-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_NAME_PUBLIC_KEY = 0,  
    ASM_NAME_PUBLIC_KEY_TOKEN,  
    ASM_NAME_HASH_VALUE,  
    ASM_NAME_NAME,  
    ASM_NAME_MAJOR_VERSION,  
    ASM_NAME_MINOR_VERSION,  
    ASM_NAME_BUILD_NUMBER,  
    ASM_NAME_REVISION_NUMBER,  
    ASM_NAME_CULTURE,  
    ASM_NAME_PROCESSOR_ID_ARRAY,  
    ASM_NAME_OSINFO_ARRAY,  
    ASM_NAME_HASH_ALGID,  
    ASM_NAME_ALIAS,  
    ASM_NAME_CODEBASE_URL,  
    ASM_NAME_CODEBASE_LASTMOD,  
    ASM_NAME_NULL_PUBLIC_KEY,  
    ASM_NAME_NULL_PUBLIC_KEY_TOKEN,  
    ASM_NAME_CUSTOM,  
    ASM_NAME_NULL_CUSTOM,
    ASM_NAME_MVID,  
    ASM_NAME_FILE_MAJOR_VERSION,  
    ASM_NAME_FILE_MINOR_VERSION,  
    ASM_NAME_FILE_BUILD_NUMBER,  
    ASM_NAME_FILE_REVISION_NUMBER,  
    ASM_NAME_RETARGET,  
    ASM_NAME_SIGNATURE_BLOB,  
    ASM_NAME_CONFIG_MASK,  
    ASM_NAME_ARCHITECTURE,  
    ASM_NAME_MAX_PARAMS  
  
} ASM_NAME;  
```  
  
## <a name="requirements"></a><span data-ttu-id="6e224-105">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6e224-105">Requirements</span></span>  
 <span data-ttu-id="6e224-106">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e224-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e224-107">**Intestazione:** Fusione.h</span><span class="sxs-lookup"><span data-stu-id="6e224-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6e224-108">**Biblioteca:** Incluso come risorsa in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e224-108">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e224-109">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e224-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e224-110">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6e224-110">See also</span></span>

- [<span data-ttu-id="6e224-111">Interfaccia IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="6e224-111">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="6e224-112">Enumerazioni Fusion</span><span class="sxs-lookup"><span data-stu-id="6e224-112">Fusion Enumerations</span></span>](fusion-enumerations.md)
