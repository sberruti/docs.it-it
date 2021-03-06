---
title: Metodo ICorDebugManagedCallback::LoadModule
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 21a97f140a41f8f380c1334652bc2417e19659c6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777129"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a>Metodo ICorDebugManagedCallback::LoadModule
Notifica al debugger che un modulo Common Language Runtime (CLR) è stato caricato correttamente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `pAppDomain`  
 in Puntatore a un oggetto ICorDebugAppDomain che rappresenta il dominio applicazione in cui è stato caricato il modulo.  
  
 `pModule`  
 in Puntatore a un oggetto ICorDebugModule che rappresenta il modulo CLR.  
  
## <a name="remarks"></a>Note  
 Il callback `LoadModule` fornisce un tempo appropriato per esaminare i metadati per il modulo, impostare i flag del compilatore JIT (just-in-Time) o abilitare o disabilitare i callback di caricamento delle classi per il modulo.  
  
## <a name="requirements"></a>Requisiti di  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Metodo UnloadModule](icordebugmanagedcallback-unloadmodule-method.md)
- [Interfaccia ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)
