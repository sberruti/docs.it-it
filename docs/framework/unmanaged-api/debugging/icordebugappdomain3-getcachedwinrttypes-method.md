---
title: Metodo ICorDebugAppDomain3::GetCachedWinRTTypes
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
ms.openlocfilehash: e5fd1730bbe5b6f2905691dce41a7f503227534a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179074"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a>Metodo ICorDebugAppDomain3::GetCachedWinRTTypes
Ottiene un enumeratore per tutti i tipi di Windows Runtime memorizzati nella cache.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCachedWinRTTypes (
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a>Parametri  
 `ppGuidToTypeEnum`  
 [fuori] Puntatore a un oggetto interfaccia [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) in grado di enumerare le rappresentazioni gestite dei tipi di Windows Runtime attualmente caricati nel dominio applicazione.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** Windows Runtime  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugAppDomain3](icordebugappdomain3-interface.md)
