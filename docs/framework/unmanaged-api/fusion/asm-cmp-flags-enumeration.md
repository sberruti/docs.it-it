---
title: Enumerazione ASM_CMP_FLAGS
ms.date: 03/30/2017
api_name:
- ASM_CMP_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CMP_FLAGS
helpviewer_keywords:
- ASM_CMP_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 4d1e6700-d4be-4fbd-8796-bfb4c07abbc8
topic_type:
- apiref
ms.openlocfilehash: 7ca4d7fe32b71401c16e64314bd8b4a9eb0f7766
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178330"
---
# <a name="asm_cmp_flags-enumeration"></a>Enumerazione ASM_CMP_FLAGS
Indica la versione, la compilazione, le impostazioni cultura, la firma e così via, di due assembly da confrontare con il metodo [IAssemblyName::IsEqual](iassemblyname-isequal-method.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum {  
  
    ASM_CMPF_NAME                   = 0x1,  
    ASM_CMPF_MAJOR_VERSION          = 0x2,  
    ASM_CMPF_MINOR_VERSION          = 0x4,  
    ASM_CMPF_BUILD_NUMBER           = 0x8,  
    ASM_CMPF_REVISION_NUMBER        = 0x10,  
  
    ASM_CMPF_VERSION                =
                 ASM_CMPF_MAJOR_VERSION |
                 ASM_CMPF_MINOR_VERSION |
                 ASM_CMPF_BUILD_NUMBER  |
                 ASM_CMPF_REVISION_NUMBER,  
  
    ASM_CMPF_PUBLIC_KEY_TOKEN       = 0x20,  
    ASM_CMPF_CULTURE                = 0x40,  
    ASM_CMPF_CUSTOM                 = 0x80,  
    ASM_CMPF_DEFAULT                = 0x100,  
    ASM_CMPF_RETARGET               = 0x200,  
    ASM_CMPF_ARCHITECTURE           = 0x400,  
    ASM_CMPF_CONFIG_MASK            = 0x800,  
    ASM_CMPF_MVID                   = 0x1000,  
    ASM_CMPF_SIGNATURE              = 0x2000,  
  
    ASM_CMPF_IL_ALL                 =
                 ASM_CMPF_NAME             |
                 ASM_CMPF_VERSION          |
                 ASM_CMPF_PUBLIC_KEY_TOKEN |
                 ASM_CMPF_CULTURE,  
  
    ASM_CMPF_IL_NO_VERSION          =
                 ASM_CMPF_NAME             |
                 ASM_CMPF_PUBLIC_KEY_TOKEN |
                 ASM_CMPF_CULTURE  
  
} ASM_CMP_FLAGS;  
```  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../get-started/system-requirements.md).  
  
 **Intestazione:** Fusione.h  
  
 **Biblioteca:** Incluso come risorsa in MsCorEE.dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia IAssemblyName](iassemblyname-interface.md)
- [Enumerazioni Fusion](fusion-enumerations.md)
