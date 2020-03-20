---
title: 'Mitigazione: Implementazioni IMessageFilter.PreFilterMessage personalizzate'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400120"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="098e5-102">Mitigazione: Implementazioni IMessageFilter.PreFilterMessage personalizzate</span><span class="sxs-lookup"><span data-stu-id="098e5-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="098e5-103">Nelle app di Windows Forms destinate a versioni di .NET Framework a partire da .NET Framework 4.6.1, un'implementazione di <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> personalizzata può filtrare in modo sicuro i messaggi quando il metodo <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> viene chiamato se l'implementazione <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="098e5-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="098e5-104">Esegue una o entrambe le opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="098e5-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="098e5-105">Aggiunge un filtro messaggio chiamando il metodo <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="098e5-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="098e5-106">Rimuove un filtro messaggio chiamando il metodo <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="098e5-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="098e5-107">ProcessOnStatus.</span><span class="sxs-lookup"><span data-stu-id="098e5-107">method.</span></span>

- <span data-ttu-id="098e5-108">**E** immette i messaggi chiamando il metodo <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="098e5-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="098e5-109">Impatto</span><span class="sxs-lookup"><span data-stu-id="098e5-109">Impact</span></span>

<span data-ttu-id="098e5-110">Questa modifica riguarda solo app Windows Forms destinate a versioni di .NET Framework a partire da .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="098e5-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="098e5-111">Per le app Windows Form destinate a versioni precedenti di .NET Framework, questo tipo di implementazioni in alcuni casi genera un'eccezione <xref:System.IndexOutOfRangeException> quando viene chiamato il metodo <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="098e5-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="098e5-112">Strategia di riduzione del rischio</span><span class="sxs-lookup"><span data-stu-id="098e5-112">Mitigation</span></span>

<span data-ttu-id="098e5-113">Se questa modifica è indesiderabile, le app destinate a .NET Framework 4.6.1 o versione successiva possono rifiutarne esplicitamente aggiungendo l'impostazione di configurazione seguente alla sezione [ \<di runtime>](../configure-apps/file-schema/runtime/runtime-element.md) del file di configurazione dell'app:</span><span class="sxs-lookup"><span data-stu-id="098e5-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="098e5-114">Inoltre, le app destinate a versioni precedenti di .NET Framework ma in esecuzione in .NET Framework 4.6.1 o [ \<](../configure-apps/file-schema/runtime/runtime-element.md) versione successiva possono acconsentire esplicitamente a questo comportamento aggiungendo l'impostazione di configurazione seguente alla sezione runtime>del file di configurazione dell'app:</span><span class="sxs-lookup"><span data-stu-id="098e5-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="098e5-115">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="098e5-115">See also</span></span>

- [<span data-ttu-id="098e5-116">Compatibilità tra le versioni</span><span class="sxs-lookup"><span data-stu-id="098e5-116">Application compatibility</span></span>](application-compatibility.md)
