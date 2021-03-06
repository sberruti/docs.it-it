---
title: Metodo ICorDebugStepper::SetInterceptMask
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: 9792abb4ee38a45aae59eaf79f1f0499539bd2ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791759"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>Metodo ICorDebugStepper::SetInterceptMask
Imposta un valore che specifica i tipi di codice sottoposti a istruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `mask`  
 in Combinazione di valori dell'enumerazione CorDebugIntercept che specifica i tipi di codice.  
  
## <a name="remarks"></a>Note  
 Se viene impostato il bit per un intercettore, il stepper verrà completato quando viene rilevato il tipo di codice di intercettazione specificato. Se il bit è deselezionato, il codice di intercettazione verrà ignorato.  
  
 Il metodo `SetInterceptMask` può avere interazioni impreviste con [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (dal punto di vista dell'utente). Se, ad esempio, l'unica parte visibile (ovvero non interna) del codice di inizializzazione della classe non dispone di informazioni di mapping e non STOP_NO_MAPPING_INFO è impostato (vedere il metodo [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) e l'enumerazione CorDebugUnmappedStop), il gestore di istruzioni eseguirà il passaggio dell'inizializzazione della classe. Per impostazione predefinita, verrà utilizzato solo il valore INTERCEPT_NONE dell'enumerazione `CorDebugIntercept`.  
  
## <a name="requirements"></a>Requisiti di  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
