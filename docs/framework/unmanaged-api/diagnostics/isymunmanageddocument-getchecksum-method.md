---
title: Metodo ISymUnmanagedDocument::GetCheckSum
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
ms.openlocfilehash: 52e1fc20fbe1d8709c21cacde926cf8bebb49425
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449209"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a>Metodo ISymUnmanagedDocument::GetCheckSum
Ottiene il checksum.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a>Parametri  
 `cData`  
 in Lunghezza del buffer fornito dal parametro `data`  
  
 `pcData`  
 out Dimensioni e lunghezza del checksum, in byte.  
  
 `data`  
 out Buffer che riceve il checksum.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK se il metodo ha esito positivo; in caso contrario, un codice di errore.  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ISymUnmanagedDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
