---
title: Metodo ICorDebugProcess5::EnumerateGCReferences
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: a97c14d83f99c847bb8569a33e175ab6eb5bccd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178616"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>Metodo ICorDebugProcess5::EnumerateGCReferences
Ottiene un enumeratore per tutti gli oggetti che devono essere sottoposti a garbage collection in un processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `enumerateWeakReferences`  
 [in] Valore booleano che indica se devono essere enumerati anche i riferimenti deboli. Se `enumerateWeakReferences` `true`è `ppEnum` , l'enumeratore include sia riferimenti sicuri che riferimenti deboli. Se `enumerateWeakReferences` `false`è , l'enumeratore include solo riferimenti sicuri.  
  
 `ppEnum`  
 [fuori] Puntatore all'indirizzo di un [oggetto ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) che è un enumeratore per gli oggetti da eseguire la garbage collection.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo fornisce un modo per determinare la catena di rooting completa per qualsiasi oggetto gestito in un processo e può essere utilizzato per determinare il motivo per cui un oggetto è ancora attivo.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICorDebugProcess5](icordebugprocess5-interface.md)
- [Interfacce di debug](debugging-interfaces.md)
