---
title: Metodo ICorDebugRegisterSet2::GetRegisters
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
ms.openlocfilehash: 54a5fb50a0177fe9886582c112f16ce871ea9df4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792067"
---
# <a name="icordebugregisterset2getregisters-method"></a>Metodo ICorDebugRegisterSet2::GetRegisters
Ottiene il valore di ogni registro (per la piattaforma in cui è attualmente in esecuzione il codice) specificato dalla maschera di bit specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `maskCount`  
 in Dimensione, in byte, della matrice `mask`.  
  
 `mask`  
 in Matrice di byte, ogni bit corrispondente a un registro. Se il bit è 1, verrà recuperato il valore del registro corrispondente.  
  
 `regCount`  
 in Numero di valori di registro da recuperare.  
  
 `regBuffer`  
 out Matrice di oggetti `CORDB_REGISTER`, ognuno dei quali riceve il valore di un registro.  
  
## <a name="remarks"></a>Note  
 Il metodo `GetRegisters` restituisce una matrice di valori dai registri specificati dalla maschera. La matrice non contiene valori di registri il cui bit mask non è impostato. Pertanto, le dimensioni della matrice di `regBuffer` devono essere uguali al numero di 1 nella maschera. Se il valore di `regCount` è troppo piccolo per il numero di registri indicato dalla maschera, i valori dei registri con numero superiore verranno troncati dal set. Se `regCount` è troppo grande, gli elementi `regBuffer` non utilizzati non verranno modificati.  
  
 Se un registro non disponibile è indicato dalla maschera, viene restituito un valore indeterminato per tale registro.  
  
 Il metodo `ICorDebugRegisterSet2::GetRegisters` è necessario per le piattaforme con più di 64 registri. Ad esempio, IA64 ha 128 registri per utilizzo generico e 128 registri a virgola mobile, quindi è necessario più di 64 bit nella maschera di bit.  
  
 Se non si dispone di più di 64 registri, come nel caso di piattaforme come x86, il metodo `GetRegisters` converte effettivamente i byte nella matrice `mask` byte in un `ULONG64` e quindi chiama il metodo [ICorDebugRegisterSet:: GetRegisters](icordebugregisterset-getregisters-method.md) , che accetta la maschera di `ULONG64`.  
  
## <a name="requirements"></a>Requisiti di  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugRegisterSet2](icordebugregisterset2-interface.md)
- [Interfaccia ICorDebugRegisterSet](icordebugregisterset-interface.md)
