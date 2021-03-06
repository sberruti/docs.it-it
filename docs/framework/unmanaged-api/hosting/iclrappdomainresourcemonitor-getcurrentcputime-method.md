---
title: Metodo ICLRAppDomainResourceMonitor::GetCurrentCpuTime
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
ms.openlocfilehash: de57fec05c338e51d0691ccfa0d0bffb334848de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126793"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a>Metodo ICLRAppDomainResourceMonitor::GetCurrentCpuTime
Ottiene il tempo totale del processore utilizzato da tutti i thread durante l'esecuzione nel dominio dell'applicazione corrente, dal momento in cui è stato creato il dominio dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a>Parametri  
 `dwAppDomainId`  
 in ID del dominio applicazione richiesto.  
  
 `pMilliseconds`  
 out Puntatore al tempo totale del processore utilizzato da tutti i thread durante l'esecuzione nel dominio dell'applicazione corrente dopo la creazione del dominio dell'applicazione. Questo parametro può essere `null`.  
  
## <a name="return-value"></a>Valore restituito  
  
|HRESULT|Descrizione|  
|-------------|-----------------|  
|S_OK|Metodo completato correttamente.|  
|COR_E_APPDOMAINUNLOADED|Il dominio applicazione è stato scaricato o non esiste.|  
|E_FAIL|Il monitoraggio delle risorse del dominio applicazione non è abilitato.<br /><br /> oppure<br /><br /> Tutti gli altri errori.|  
  
## <a name="remarks"></a>Note  
 Questo metodo è l'equivalente non gestito della proprietà <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> gestita.  
  
## <a name="requirements"></a>Requisiti  
 **Piattaforme:** vedere [Requisiti di sistema di .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Intestazione:** Metahost. h  
  
 **Libreria:** Incluso come risorsa in MSCorEE. dll  
  
 **Versioni di .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Vedere anche

- [Interfaccia ICLRAppDomainResourceMonitor](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [Interfacce di hosting](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Monitoraggio delle risorse del dominio dell'applicazione](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
