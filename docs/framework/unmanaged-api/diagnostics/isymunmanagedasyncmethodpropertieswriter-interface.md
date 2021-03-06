---
title: Interfaccia ISymUnmanagedAsyncMethodPropertiesWriter
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: db065357e22ac576600a3ca61dda0882b9206a86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129159"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>Interfaccia ISymUnmanagedAsyncMethodPropertiesWriter
Consente di definire informazioni facoltative sul metodo asincrono per ogni simbolo di metodo. Usare sempre con un metodo aperto; ovvero tra le chiamate al [Metodo OpenMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) e il [Metodo CloseMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).  
  
## <a name="syntax"></a>Sintassi  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Metodi  
 Per l'interfaccia sono disponibili i seguenti metodi:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Definire un gruppo di operazioni di attesa asincrone nel metodo corrente.<br /><br /> Ogni offset yield corrisponde a un'istruzione return di await, che identifica un potenziale rendimento. Ogni coppia `breakpointMethod`/`breakpointOffset` identifica la posizione in cui l'operazione asincrona riprenderà; potrebbe trovarsi in un metodo diverso.|  
|[Metodo DefineCatchHandlerILOffset](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Imposta l'offset il per il gestore catch generato dal compilatore che esegue il wrapping di un metodo asincrono.<br /><br /> L'offset il dell'oggetto catch generato viene utilizzato dal debugger per gestire l'oggetto Catch come se fosse un codice non utente, anche se potrebbe verificarsi in un metodo del codice utente. In particolare, viene usato in risposta a un evento di eccezione **CatchHandlerFound** .|  
|[Metodo DefineKickoffMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Imposta il metodo iniziale che avvia l'operazione asincrona.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Vedere anche

- [Interfacce dell'archivio simboli di diagnostica](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
