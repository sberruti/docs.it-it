---
title: Installazione accodamento messaggi (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 8ecbd07adfb6bfb4e9898f9b8508809480d17e16
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921094"
---
# <a name="installing-message-queuing-msmq"></a>Installazione accodamento messaggi (MSMQ)
Le procedure seguenti mostrano come installare Accodamento messaggi 4.0 e Accodamento messaggi 3.0.  
  
> [!NOTE]
> Accodamento messaggi 4,0 non è disponibile in Windows XP e Windows Server 2003.  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Per installare la versione 4.0 del sistema di accodamento dei messaggi in Windows Server 2008 o in Windows Server 2008 R2  
  
1. In Server Manager fare clic su **funzionalità**.  
  
2. Nel riquadro di destra in **Riepilogo funzionalità**fare clic su **Aggiungi funzionalità**.  
  
3. Nella finestra risultante espandere **Accodamento messaggi**.  
  
4. Espandere **Servizi Accodamento messaggi**.  
  
5. Fare clic su **integrazione servizi directory** (per i computer aggiunti a un dominio), quindi fare clic su **supporto http**.  
  
6. Fare clic su **Avanti**, quindi su **Installa**.  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Per installare la versione 4.0 del sistema di accodamento dei messaggi in Windows 7 o in windows Vista  
  
1. Aprire il **Pannello di controllo**.  
  
2. Fare clic su **programmi** e quindi in **programmi e funzionalità**fare clic **su attivazione e disattivazione delle funzionalità Windows**.  
  
3. Espandere Microsoft Message Queue (MSMQ) Server, espandere Componenti di base di Microsoft Message Queue (MSMQ) Server, quindi selezionare le caselle di controllo per l'installazione delle funzionalità di Accodamento messaggi seguenti:  
  
    - Integrazione dei Servizi di dominio Active Directory MSMQ (per computer aggiunti a un Dominio).  
  
    - Supporto HTTP MSMQ.  
  
4. Fare clic su **OK**.  
  
5. Se viene richiesto di riavviare il computer, fare clic su **OK** per completare l'installazione.  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Per installare la versione 3.0 di Accodamento messaggi in Windows XP o Windows Server 2003  
  
1. Aprire il **Pannello di controllo**.  
  
2. Fare clic su **Aggiungi Rimuovi programmi** , quindi su **Aggiungi componenti di Windows**.  
  
3. Selezionare Accodamento messaggi e fare clic su **Dettagli**.  
  
    > [!NOTE]
    > Se si esegue Windows Server 2003, selezionare Server applicazioni per accedere a Accodamento messaggi.  
  
4. Assicurarsi che l'opzione Supporto HTTP MSMQ sia selezionata nella pagina dei dettagli.  
  
5. Fare clic su **OK** per chiudere la pagina dei dettagli, quindi fare clic su **Avanti**. Completare l'installazione.  
  
6. Se viene richiesto di riavviare il computer, fare clic su **OK** per completare l'installazione.  
  
## <a name="see-also"></a>Vedere anche

- [Istruzioni di configurazione](../../../../docs/framework/wcf/samples/set-up-instructions.md)
