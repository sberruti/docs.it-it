---
title: Interfaccia ICorPublishProcessEnum
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 188ff8feabd704d828256a09aca20f9db2227f2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790505"
---
# <a name="icorpublishprocessenum-interface"></a>Interfaccia ICorPublishProcessEnum
Sottoclasse dell'interfaccia [ICorPublishEnum](icorpublishenum-interface.md) che fornisce i metodi per attraversare una raccolta di oggetti [ICorPublishProcess](icorpublishprocess-interface.md) .  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo Next](icorpublishprocessenum-next-method.md)|Ottiene il numero specificato di istanze di `ICorPublishProcess` dalla raccolta, a partire dalla posizione corrente.|  
  
## <a name="remarks"></a>Note  
 L'interfaccia `ICorPublishProcessEnum` implementa i metodi dell'interfaccia astratta, [ICorPublishEnum](icorpublishenum-interface.md).  
  
 Un'istanza di `ICorPublishProcessEnum` viene creata dal metodo [ICorPublish:: EnumProcesses](icorpublish-enumprocesses-method.md) . L'attraversamento della raccolta di oggetti `ICorPublishProcess` si basa sui criteri di filtro specificati al momento della creazione dell'istanza di `ICorPublishProcessEnum`.  
  
## <a name="requirements"></a>Requisiti di  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorPub. idl, CorPub. h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfacce di debug](debugging-interfaces.md)
- [Coclasse CorpubPublish](corpubpublish-coclass.md)
