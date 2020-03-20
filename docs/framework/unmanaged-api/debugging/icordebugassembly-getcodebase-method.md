---
title: Metodo ICorDebugAssembly::GetCodeBase
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetCodeBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetCodeBase
helpviewer_keywords:
- GetCodeBase method [.NET Framework debugging]
- ICorDebugAssembly::GetCodeBase method [.NET Framework debugging]
ms.assetid: 48adc154-9058-4fef-9c43-e9aad80e4dbf
topic_type:
- apiref
ms.openlocfilehash: b348f29884eb7d359c5dd6df27af49cd748477c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178973"
---
# <a name="icordebugassemblygetcodebase-method"></a><span data-ttu-id="734bb-102">Metodo ICorDebugAssembly::GetCodeBase</span><span class="sxs-lookup"><span data-stu-id="734bb-102">ICorDebugAssembly::GetCodeBase Method</span></span>
<span data-ttu-id="734bb-103">Questo metodo non è implementato nella versione corrente di .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="734bb-103">This method is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="734bb-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="734bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeBase (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR szName[]  
);  
```
