---
title: Enumerazione LoggingLevelEnum
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
ms.openlocfilehash: 1677798abdb8994d34c82a71e97a2c858209c18e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790382"
---
# <a name="logginglevelenum-enumeration"></a>Enumerazione LoggingLevelEnum
Indica il livello di gravità di un messaggio descrittivo scritto nel registro eventi quando un thread gestito registra un evento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>Membri  
  
|Member|Descrizione|  
|------------|-----------------|  
|`LTraceLevel0`|Il messaggio è un livello di traccia 0.|  
|`LTraceLevel1`|Il messaggio è un livello di traccia 1.|  
|`LTraceLevel2`|Il messaggio è un livello di traccia 2.|  
|`LTraceLevel3`|Il messaggio è un livello di traccia 3.|  
|`LTraceLevel4`|Il messaggio è un livello di traccia 4.|  
|`LStatusLevel0`|Il messaggio è un livello di stato 0.|  
|`LStatusLevel1`|Il messaggio è un livello di stato 1.|  
|`LStatusLevel2`|Il messaggio è un livello di stato 2.|  
|`LStatusLevel3`|Il messaggio è un livello di stato 3.|  
|`LStatusLevel4`|Il messaggio è un livello di stato 4.|  
|`LWarningLevel`|Il messaggio è un livello di avviso.|  
|`LErrorLevel`|Il messaggio è un livello di errore.|  
|`LPanicLevel`|Il messaggio è un livello di panico.|  
  
## <a name="remarks"></a>Note  
 Il Common Language Runtime (CLR) chiama il metodo [ICorDebugManagedCallback:: LogMessage](icordebugmanagedcallback-logmessage-method.md) per notificare al debugger che un thread gestito ha registrato un evento. CLR passa un valore dell'enumerazione `LoggingLevelEnum` per indicare il livello di gravità del messaggio scritto dal thread gestito nel registro eventi.  
  
## <a name="requirements"></a>Requisiti di  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Diagnostics.EventLog>
- [Enumerazioni di debug](debugging-enumerations.md)
