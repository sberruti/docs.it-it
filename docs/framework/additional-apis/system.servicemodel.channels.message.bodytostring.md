---
title: Metodo Message. BodyToString (System. ServiceModel. Channels)
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 9f1f852c0bd82299fd40afe66a5f90cd7c0335cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215501"
---
# <a name="messagebodytostring-method"></a><span data-ttu-id="c99fc-102">Message. BodyToString, metodo</span><span class="sxs-lookup"><span data-stu-id="c99fc-102">Message.BodyToString Method</span></span>

<span data-ttu-id="c99fc-103">Converte il corpo del messaggio in una stringa chiamando il metodo <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c99fc-103">Converts the message body into a string by calling the <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> method.</span></span>

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a><span data-ttu-id="c99fc-104">Parametri</span><span class="sxs-lookup"><span data-stu-id="c99fc-104">Parameters</span></span>

- <span data-ttu-id="c99fc-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span><span class="sxs-lookup"><span data-stu-id="c99fc-105">`writer` <xref:System.Xml.XmlDictionaryWriter></span></span>\
  <span data-ttu-id="c99fc-106">Writer utilizzato per convertire il corpo del messaggio in una stringa.</span><span class="sxs-lookup"><span data-stu-id="c99fc-106">The writer that is used to convert the message body to a string.</span></span>

## <a name="remarks"></a><span data-ttu-id="c99fc-107">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="c99fc-107">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="c99fc-108">Il `Message.BodyToString` metodo è interno e non deve essere usato direttamente nel codice.</span><span class="sxs-lookup"><span data-stu-id="c99fc-108">The `Message.BodyToString` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="c99fc-109">Microsoft non supporta l'utilizzo di questo metodo in un'applicazione di produzione in qualsiasi circostanza.</span><span class="sxs-lookup"><span data-stu-id="c99fc-109">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="c99fc-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="c99fc-110">Requirements</span></span>

<span data-ttu-id="c99fc-111">**Spazio dei nomi:** <xref:System.ServiceModel.Channels></span><span class="sxs-lookup"><span data-stu-id="c99fc-111">**Namespace:** <xref:System.ServiceModel.Channels></span></span>

<span data-ttu-id="c99fc-112">**Assembly:** System. ServiceModel. dll</span><span class="sxs-lookup"><span data-stu-id="c99fc-112">**Assembly:** System.ServiceModel.dll</span></span>

<span data-ttu-id="c99fc-113">**Versioni .NET Framework:** Disponibile a partire da 3,0.</span><span class="sxs-lookup"><span data-stu-id="c99fc-113">**.NET Framework versions:** Available since 3.0.</span></span>
