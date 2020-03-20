---
title: Metodo ISymENCUnmanagedMethod::GetDocumentsForMethod
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
ms.openlocfilehash: 97f0d81c389ffd0bd8a69df2ca39322d726f98bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176630"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="45a37-102">Metodo ISymENCUnmanagedMethod::GetDocumentsForMethod</span><span class="sxs-lookup"><span data-stu-id="45a37-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="45a37-103">Ottiene i documenti in cui questo metodo contiene righe.</span><span class="sxs-lookup"><span data-stu-id="45a37-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45a37-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="45a37-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45a37-105">Parametri</span><span class="sxs-lookup"><span data-stu-id="45a37-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="45a37-106">[in] Lunghezza del buffer a `pcDocs`cui punta .</span><span class="sxs-lookup"><span data-stu-id="45a37-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="45a37-107">[fuori] Puntatore a `ULONG32` un che riceve la dimensione, in caratteri, del buffer necessario per contenere i documenti.</span><span class="sxs-lookup"><span data-stu-id="45a37-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="45a37-108">[in] Buffer che contiene i documenti.</span><span class="sxs-lookup"><span data-stu-id="45a37-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45a37-109">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="45a37-109">Return Value</span></span>  
 <span data-ttu-id="45a37-110">S_OK se il metodo ha esito positivo; in caso contrario, un codice di errore.</span><span class="sxs-lookup"><span data-stu-id="45a37-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45a37-111">Requisiti</span><span class="sxs-lookup"><span data-stu-id="45a37-111">Requirements</span></span>  
 <span data-ttu-id="45a37-112">**Intestazione:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="45a37-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45a37-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="45a37-113">See also</span></span>

- [<span data-ttu-id="45a37-114">Interfaccia ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="45a37-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
