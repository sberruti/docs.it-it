---
title: Messaggi in coda eliminati al secondo
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 6ec762d7e5dd7daf63b5df76e1ffb48957538538
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164034"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="425a6-102">Messaggi in coda eliminati al secondo</span><span class="sxs-lookup"><span data-stu-id="425a6-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="425a6-103">Nome contatore: messaggi in coda eliminati al secondo</span><span class="sxs-lookup"><span data-stu-id="425a6-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="425a6-104">Descrizione</span><span class="sxs-lookup"><span data-stu-id="425a6-104">Description</span></span>  
 <span data-ttu-id="425a6-105">Numero di messaggi eliminati dal trasporto in coda di questo servizio al secondo.</span><span class="sxs-lookup"><span data-stu-id="425a6-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="425a6-106">Questo contatore è del tipo di contatore delle prestazioni [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), il cui valore viene calcolato utilizzando la formula seguente.</span><span class="sxs-lookup"><span data-stu-id="425a6-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="425a6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="425a6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
