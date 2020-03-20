---
title: Enumerazione CorPinvokeMap
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176149"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="57204-102">Enumerazione CorPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="57204-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="57204-103">Specifica le opzioni per una chiamata PInvoke.</span><span class="sxs-lookup"><span data-stu-id="57204-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57204-104">Sintassi</span><span class="sxs-lookup"><span data-stu-id="57204-104">Syntax</span></span>  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="57204-105">Members</span><span class="sxs-lookup"><span data-stu-id="57204-105">Members</span></span>  
  
|<span data-ttu-id="57204-106">Membro</span><span class="sxs-lookup"><span data-stu-id="57204-106">Member</span></span>|<span data-ttu-id="57204-107">Descrizione</span><span class="sxs-lookup"><span data-stu-id="57204-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="57204-108">Utilizzare ogni nome di membro come specificato.</span><span class="sxs-lookup"><span data-stu-id="57204-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="57204-109">Riservato.</span><span class="sxs-lookup"><span data-stu-id="57204-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="57204-110">Riservato.</span><span class="sxs-lookup"><span data-stu-id="57204-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="57204-111">Esegue il marshalling delle stringhe come stringhe di caratteri a più byte.</span><span class="sxs-lookup"><span data-stu-id="57204-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="57204-112">Esegue il marshalling delle stringhe come caratteri Unicode a 2 byte.</span><span class="sxs-lookup"><span data-stu-id="57204-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="57204-113">Esegue automaticamente il marshalling delle stringhe in modo appropriato per il sistema operativo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="57204-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="57204-114">Il valore predefinito è Unicode in Windows NT, Windows 2000, Windows XP e nella famiglia Windows Server 2003. l'impostazione predefinita è ANSI in Windows 98 e Windows Me.</span><span class="sxs-lookup"><span data-stu-id="57204-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="57204-115">Riservato.</span><span class="sxs-lookup"><span data-stu-id="57204-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="57204-116">Eseguire il mapping ottimale dei caratteri Unicode che non dispongono di una corrispondenza esatta nel set di caratteri ANSI.</span><span class="sxs-lookup"><span data-stu-id="57204-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="57204-117">Non eseguire il mapping più adatto dei caratteri Unicode.</span><span class="sxs-lookup"><span data-stu-id="57204-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="57204-118">In questo caso, tutti i caratteri di cui non è possibile mappare verranno sostituiti da un '?'.</span><span class="sxs-lookup"><span data-stu-id="57204-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="57204-119">Riservato.</span><span class="sxs-lookup"><span data-stu-id="57204-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="57204-120">Riservato.</span><span class="sxs-lookup"><span data-stu-id="57204-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="57204-121">Generare un'eccezione quando il gestore di marshalling di interoperabilità rileva un carattere di cui non è possibile eseguire il marshalling.</span><span class="sxs-lookup"><span data-stu-id="57204-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="57204-122">Non generare un'eccezione quando il gestore di marshalling di interoperabilità rileva un carattere di cui non è possibile eseguire il codificatore.</span><span class="sxs-lookup"><span data-stu-id="57204-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="57204-123">Riservato</span><span class="sxs-lookup"><span data-stu-id="57204-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="57204-124">Consentire al chiamato di chiamare la `SetLastError` funzione Win32 prima di restituire dal metodo con attributi.</span><span class="sxs-lookup"><span data-stu-id="57204-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="57204-125">Riservato</span><span class="sxs-lookup"><span data-stu-id="57204-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="57204-126">Utilizzare la convenzione di chiamata della piattaforma predefinita.</span><span class="sxs-lookup"><span data-stu-id="57204-126">Use the default platform calling convention.</span></span> <span data-ttu-id="57204-127">In Windows, ad esempio, l'impostazione predefinita è `StdCall` e in Windows CE .NET è `Cdecl`.</span><span class="sxs-lookup"><span data-stu-id="57204-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="57204-128">Utilizzare `Cdecl` la convenzione di chiamata.</span><span class="sxs-lookup"><span data-stu-id="57204-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="57204-129">In questo caso, il chiamante pulisce lo stack.</span><span class="sxs-lookup"><span data-stu-id="57204-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="57204-130">In questo modo `varargs` le funzioni di chiamata con (vale a dire, funzioni che accettano un numero variabile di parametri).</span><span class="sxs-lookup"><span data-stu-id="57204-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="57204-131">Utilizzare `StdCall` la convenzione di chiamata.</span><span class="sxs-lookup"><span data-stu-id="57204-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="57204-132">In questo caso, il chiamato pulisce lo stack.</span><span class="sxs-lookup"><span data-stu-id="57204-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="57204-133">Si tratta della convenzione predefinita per chiamare funzioni non gestite tramite platform invoke.</span><span class="sxs-lookup"><span data-stu-id="57204-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="57204-134">Utilizzare `ThisCall` la convenzione di chiamata.</span><span class="sxs-lookup"><span data-stu-id="57204-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="57204-135">In questo caso, il `this` primo parametro è il puntatore e viene archiviato nel registro ECX.</span><span class="sxs-lookup"><span data-stu-id="57204-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="57204-136">Altri parametri vengono inseriti nello stack.</span><span class="sxs-lookup"><span data-stu-id="57204-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="57204-137">La `ThisCall` convenzione di chiamata viene utilizzata per chiamare metodi su classi esportate da una DLL non gestita.</span><span class="sxs-lookup"><span data-stu-id="57204-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="57204-138">Riservato.</span><span class="sxs-lookup"><span data-stu-id="57204-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="57204-139">Riservato.</span><span class="sxs-lookup"><span data-stu-id="57204-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57204-140">Requisiti</span><span class="sxs-lookup"><span data-stu-id="57204-140">Requirements</span></span>  
 <span data-ttu-id="57204-141">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57204-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57204-142">**Intestazione:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="57204-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="57204-143">**Versioni di .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57204-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57204-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="57204-144">See also</span></span>

- [<span data-ttu-id="57204-145">Enumerazioni dei metadati</span><span class="sxs-lookup"><span data-stu-id="57204-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
