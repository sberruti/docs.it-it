---
title: Enumerazione VariableLocationType
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: 1aa59ee559abff8006f0ac63a812e4315aa48154
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790305"
---
# <a name="variablelocationtype-enumeration"></a>Enumerazione VariableLocationType
Indica il tipo di percorso nativo di una variabile.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Descrizione|  
|------------|-----------------|  
|`VLT_REGISTER`|La variabile si trova in un registro.|  
|`VLT_REGISTER_RELATIVE`|La variabile si trova in una posizione di memoria relativa al registro.|  
|`VLT_INVALID`|La variabile non è archiviata in un registro o in una posizione di memoria relativa al registro.|  
  
## <a name="remarks"></a>Note  
 Un membro dell'enumerazione `VariableLocationType` viene restituito dal metodo [ICorDebugVariableHome:: GetLocationType](icordebugvariablehome-getlocationtype-method.md) .  
  
## <a name="requirements"></a>Requisiti di  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Enumerazioni di debug](debugging-enumerations.md)
