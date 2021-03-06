---
title: Metodo ICorDebugILFrame2::EnumerateTypeParameters
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
ms.openlocfilehash: 715ff5d4a06b53361d550f04e5154023d0b641bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095114"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>Metodo ICorDebugILFrame2::EnumerateTypeParameters
Ottiene un oggetto ICorDebugTypeEnum che contiene i parametri di <xref:System.Type> in questo frame.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametri  
 `ppTyParEnum`  
 Puntatore all'indirizzo di un oggetto interfaccia ICorDebugTypeEnum che consente l'enumerazione dei parametri di tipo.  
  
 L'elenco dei parametri di tipo include i parametri di tipo di classe, se presenti, seguiti dai parametri di tipo del metodo, se presenti.  
  
## <a name="remarks"></a>Note  
 Usare il metodo [IMetaDataImport2:: EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) per determinare il numero di parametri di tipo di classe e i parametri di tipo di metodo contenuti nell'elenco.  
  
 I parametri di tipo non sono sempre disponibili.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** CorDebug.idl, CorDebug.h  
  
 **Libreria:** CorGuids.lib  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
