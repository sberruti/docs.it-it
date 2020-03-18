---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937099"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a><span data-ttu-id="228df-101">Non è supportata l'opzione di compatibilità DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="228df-101">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>

<span data-ttu-id="228df-102">L'opzione `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` di compatibilità, introdotta in .NET Framework 4.6.1, non è supportata in Windows Form in .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="228df-102">The `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch, which was introduced in .NET Framework 4.6.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="228df-103">Descrizione modifica:</span><span class="sxs-lookup"><span data-stu-id="228df-103">Change description</span></span>

<span data-ttu-id="228df-104">A partire da .NET Framework 4.6.1, l'opzione `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` di compatibilità risolve le possibili <xref:System.IndexOutOfRangeException> eccezioni quando il <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> messaggio viene chiamato con un'implementazione personalizzata. <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="228df-104">Starting with the .NET Framework 4.6.1, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` compatibility switch addresses possible <xref:System.IndexOutOfRangeException> exceptions when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> message is called with a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="228df-105">Per altre informazioni, vedere [Mitigazione: Implementazioni IMessageFilter.PreFilterMessage personalizzate](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span><span class="sxs-lookup"><span data-stu-id="228df-105">For more information, see [Mitigation: Custom IMessageFilter.PreFilterMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).</span></span>

<span data-ttu-id="228df-106">In .NET Core `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` l'opzione non è supportata.</span><span class="sxs-lookup"><span data-stu-id="228df-106">In .NET Core, the `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="228df-107">Versione introdotta</span><span class="sxs-lookup"><span data-stu-id="228df-107">Version introduced</span></span>

<span data-ttu-id="228df-108">3.0 Anteprima 9</span><span class="sxs-lookup"><span data-stu-id="228df-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="228df-109">Azione consigliata</span><span class="sxs-lookup"><span data-stu-id="228df-109">Recommended action</span></span>

<span data-ttu-id="228df-110">Rimuovere l'interruttore.</span><span class="sxs-lookup"><span data-stu-id="228df-110">Remove the switch.</span></span> <span data-ttu-id="228df-111">L'opzione non è supportata e non sono disponibili funzionalità alternative.</span><span class="sxs-lookup"><span data-stu-id="228df-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="228df-112">Category</span><span class="sxs-lookup"><span data-stu-id="228df-112">Category</span></span>

<span data-ttu-id="228df-113">Windows Form</span><span class="sxs-lookup"><span data-stu-id="228df-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="228df-114">API interessate</span><span class="sxs-lookup"><span data-stu-id="228df-114">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
