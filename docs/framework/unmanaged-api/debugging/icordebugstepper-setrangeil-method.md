---
title: Metodo ICorDebugStepper::SetRangeIL
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: b3153a88867d249aad8365bb774348fb8c9d57d5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791756"
---
# <a name="icordebugsteppersetrangeil-method"></a>Metodo ICorDebugStepper::SetRangeIL
Imposta un valore che specifica se le chiamate a [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) passano valori di argomento relativi al codice nativo o rispetto al codice MSIL (Microsoft Intermediate Language) del metodo di cui è in corso il passaggio.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `bIL`  
 in Impostare su `true` per specificare che gli intervalli sono relativi al codice MSIL. Impostare su `false` per specificare che gli intervalli sono relativi al codice nativo. Il valore predefinito è `true`.  
  
## <a name="requirements"></a>Requisiti di  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
