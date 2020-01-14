---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937012"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a><span data-ttu-id="22fb4-101">Opzione di compatibilità DomainUpDown. UseLegacyScrolling non supportata</span><span class="sxs-lookup"><span data-stu-id="22fb4-101">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>

<span data-ttu-id="22fb4-102">L'opzione di compatibilità `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`, introdotta in .NET Framework 4.7.1, non è supportata in Windows Forms in .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="22fb4-102">The `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch, which was introduced in .NET Framework 4.7.1, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="22fb4-103">Descrizione delle modifiche</span><span class="sxs-lookup"><span data-stu-id="22fb4-103">Change description</span></span>

<span data-ttu-id="22fb4-104">A partire da .NET Framework 4.7.1, l'opzione di compatibilità `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` consente agli sviluppatori di rifiutare esplicitamente le azioni di <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> e <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> indipendenti.</span><span class="sxs-lookup"><span data-stu-id="22fb4-104">Starting with the .NET Framework 4.7.1, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` compatibility switch allowed developers to opt-out of independent <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> actions.</span></span> <span data-ttu-id="22fb4-105">Il cambio ha ripristinato il comportamento legacy, in cui il <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> viene ignorato se è presente il testo del contesto e lo sviluppatore deve usare <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> azione sul controllo prima dell'azione di <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="22fb4-105">The switch restored the legacy behavior, in which the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> is ignored if context text is present, and the developer is required to use <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> action on the control before the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action.</span></span> <span data-ttu-id="22fb4-106">Per ulteriori informazioni, vedere [\<elemento > AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span><span class="sxs-lookup"><span data-stu-id="22fb4-106">For more information, see [\<AppContextSwitchOverrides> element](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).</span></span>

<span data-ttu-id="22fb4-107">In .NET Core, l'opzione `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` non è supportata.</span><span class="sxs-lookup"><span data-stu-id="22fb4-107">In .NET Core, the `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="22fb4-108">Versione introdotta</span><span class="sxs-lookup"><span data-stu-id="22fb4-108">Version introduced</span></span>

<span data-ttu-id="22fb4-109">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="22fb4-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="22fb4-110">Azione consigliata</span><span class="sxs-lookup"><span data-stu-id="22fb4-110">Recommended action</span></span>

<span data-ttu-id="22fb4-111">Rimuovere l'opzione.</span><span class="sxs-lookup"><span data-stu-id="22fb4-111">Remove the switch.</span></span> <span data-ttu-id="22fb4-112">L'opzione non è supportata e non è disponibile alcuna funzionalità alternativa.</span><span class="sxs-lookup"><span data-stu-id="22fb4-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="22fb4-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="22fb4-113">Category</span></span>

<span data-ttu-id="22fb4-114">Windows Form</span><span class="sxs-lookup"><span data-stu-id="22fb4-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22fb4-115">API interessate</span><span class="sxs-lookup"><span data-stu-id="22fb4-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
