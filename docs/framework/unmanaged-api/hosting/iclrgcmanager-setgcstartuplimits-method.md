---
title: Metodo ICLRGCManager::SetGCStartupLimits
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
ms.openlocfilehash: 645b64c8b536029663c350bdcde9a716a715aab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178090"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="4c110-102">Metodo ICLRGCManager::SetGCStartupLimits</span><span class="sxs-lookup"><span data-stu-id="4c110-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="4c110-103">Imposta la dimensione di un segmento di Garbage Collection e la dimensione massima della generazione 0 del sistema di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="4c110-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4c110-104">A partire da .NET Framework 4.5.NET Framework 4.5, `DWORD` è possibile impostare la dimensione del segmento e la dimensione massima della generazione 0 su valori maggiori rispetto all'utilizzo del metodo [ICLRGCManager2::SetGCStartupLimitsEx.](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)</span><span class="sxs-lookup"><span data-stu-id="4c110-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c110-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="4c110-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c110-106">Parametri</span><span class="sxs-lookup"><span data-stu-id="4c110-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="4c110-107">[in] Dimensione specificata di un segmento di Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="4c110-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="4c110-108">La dimensione minima del segmento è 4 MB.</span><span class="sxs-lookup"><span data-stu-id="4c110-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="4c110-109">I segmenti possono essere aumentati in incrementi di 1 MB o superiore.</span><span class="sxs-lookup"><span data-stu-id="4c110-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="4c110-110">[in] Dimensione massima specificata per la generazione 0.</span><span class="sxs-lookup"><span data-stu-id="4c110-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="4c110-111">La dimensione minima di generazione 0 è 64 KB.</span><span class="sxs-lookup"><span data-stu-id="4c110-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c110-112">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="4c110-112">Return Value</span></span>  
  
|<span data-ttu-id="4c110-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c110-113">HRESULT</span></span>|<span data-ttu-id="4c110-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="4c110-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c110-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c110-115">S_OK</span></span>|<span data-ttu-id="4c110-116">`SetGCStartupLimits`restituito con successo.</span><span class="sxs-lookup"><span data-stu-id="4c110-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="4c110-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4c110-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4c110-118">Common Language Runtime (CLR) non è stato caricato in un processo oppure CLR si trova in uno stato in cui non può eseguire codice gestito o elaborare correttamente la chiamata.</span><span class="sxs-lookup"><span data-stu-id="4c110-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4c110-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4c110-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4c110-120">Timeout della chiamata.</span><span class="sxs-lookup"><span data-stu-id="4c110-120">The call timed out.</span></span>|  
|<span data-ttu-id="4c110-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4c110-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4c110-122">Il chiamante non è proprietario del blocco.</span><span class="sxs-lookup"><span data-stu-id="4c110-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4c110-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4c110-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4c110-124">Un evento è stato annullato mentre un thread bloccato o una fibra era in attesa su di esso.</span><span class="sxs-lookup"><span data-stu-id="4c110-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4c110-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4c110-125">E_FAIL</span></span>|<span data-ttu-id="4c110-126">Si è verificato un errore irreversibile sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="4c110-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4c110-127">Dopo che un metodo restituisce E_FAIL, CLR non è più utilizzabile all'interno del processo.</span><span class="sxs-lookup"><span data-stu-id="4c110-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4c110-128">Le chiamate successive ai metodi di hosting restituiscono HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4c110-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c110-129">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="4c110-129">Remarks</span></span>  
 <span data-ttu-id="4c110-130">I valori `SetGCStartupLimits` impostati possono essere specificati una sola volta.</span><span class="sxs-lookup"><span data-stu-id="4c110-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="4c110-131">Le chiamate `SetGCStartupLimits` successive a vengono ignorate.</span><span class="sxs-lookup"><span data-stu-id="4c110-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c110-132">Requisiti</span><span class="sxs-lookup"><span data-stu-id="4c110-132">Requirements</span></span>  
 <span data-ttu-id="4c110-133">**Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c110-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c110-134">**Intestazione:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c110-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c110-135">**Biblioteca:** Incluso come risorsa in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c110-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c110-136">**Versioni di .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c110-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c110-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4c110-137">See also</span></span>

- [<span data-ttu-id="4c110-138">Gestione automatica della memoria</span><span class="sxs-lookup"><span data-stu-id="4c110-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="4c110-139">Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="4c110-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="4c110-140">Interfaccia ICLRControl</span><span class="sxs-lookup"><span data-stu-id="4c110-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="4c110-141">Interfaccia ICLRGCManager</span><span class="sxs-lookup"><span data-stu-id="4c110-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
