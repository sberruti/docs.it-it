---
title: Metodo ISymUnmanagedWriter::DefineSequencePoints
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
ms.openlocfilehash: 63ba108bc234e566450bb019afc63acb4e75ad1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427992"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a>Metodo ISymUnmanagedWriter::DefineSequencePoints
Definisce un gruppo di punti di sequenza nel metodo corrente. Ogni riga iniziale e colonna iniziale definiscono l'inizio di un'istruzione all'interno di un metodo. Ogni riga finale e colonna finale definiscono la fine di un'istruzione all'interno di un metodo. Le matrici devono essere ordinate in ordine crescente di offset. L'offset viene sempre misurato dall'inizio del metodo, espresso in byte.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a>Parametri  
 `document`  
 in Oggetto documento per il quale vengono definiti i punti di sequenza.  
  
 `spCount`  
 in `ULONG32` che indica le dimensioni di ognuno dei buffer `offsets`, `lines`, `columns`, `endLines`e `endColumns`.  
  
 `offsets`  
 in Offset dei punti di sequenza misurato a partire dall'inizio del metodo.  
  
 `lines`  
 in Numeri di riga iniziali dei punti di sequenza.  
  
 `columns`  
 in Numeri di colonna iniziali dei punti di sequenza.  
  
 `endLines`  
 in Numeri di riga finali dei punti di sequenza. Questo parametro è facoltativo.  
  
 `endColumns`  
 in Numeri di colonna finali dei punti di sequenza. Questo parametro è facoltativo.  
  
## <a name="return-value"></a>Valore restituito  
 S_OK se il metodo ha esito positivo; in caso contrario, E_FAIL o un altro codice di errore.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
