---
title: Metodo ICorDebugProcess6::GetExportStepInfo
ms.date: 03/30/2017
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
ms.openlocfilehash: 6580fdaacaea17fcf886bfd7ac5e236925acf453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178522"
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>Metodo ICorDebugProcess6::GetExportStepInfo
Fornisce informazioni sulle funzioni di runtime esportate per consentire l'esecuzione di codice gestito seguendo un'istruzione alla volta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,
    [out] CorDebugCodeInvokeKind* pInvokeKind,
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
## <a name="parameters"></a>Parametri  
 pszExportName  
 [in] Il nome di una funzione di runtime di esportazione così come è scritta nella tabella di esportazione PE.  
  
 invokeKind  
 [fuori] Puntatore a un membro dell'enumerazione [CorDebugCodeInvokeKind](cordebugcodeinvokekind-enumeration.md) che descrive come la funzione esportata richiamerà il codice gestito.  
  
 invokePurpose  
 [fuori] Puntatore a un membro dell'enumerazione [CorDebugCodeInvokePurpose](cordebugcodeinvokepurpose-enumeration.md) che descrive il motivo per cui la funzione esportata chiamerà codice gestito.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo può restituire i valori elencati nella seguente tabella.  
  
|Valore restituito|Descrizione|  
|------------------|-----------------|  
|`S_OK`|La chiamata al metodo è stata completata correttamente.|  
|`E_POINTER`|`pInvokeKind`o `pInvokePurpose` è **null**.|  
|Altri valori di `HRESULT` con errori.|A seconda dei casi.|  
  
## <a name="remarks"></a>Osservazioni  
  
> [!NOTE]
> Questo metodo è disponibile solo con .NET Native.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugProcess6](icordebugprocess6-interface.md)
- [Interfacce di debug](debugging-interfaces.md)
