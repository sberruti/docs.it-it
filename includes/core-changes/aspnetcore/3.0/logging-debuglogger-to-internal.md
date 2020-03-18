---
ms.openlocfilehash: 958dede03e1c15f69f4ee676f13713ff43c29e96
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394396"
---
### <a name="logging-debuglogger-class-made-internal"></a><span data-ttu-id="b3710-101">Registrazione: la classe DebugLogger resa internaLogging: DebugLogger class made internal</span><span class="sxs-lookup"><span data-stu-id="b3710-101">Logging: DebugLogger class made internal</span></span>

<span data-ttu-id="b3710-102">Prima di ASP.NET Core `DebugLogger`3.0, `public`il modificatore di accesso 'era .</span><span class="sxs-lookup"><span data-stu-id="b3710-102">Prior to ASP.NET Core 3.0, `DebugLogger`'s access modifier was `public`.</span></span> <span data-ttu-id="b3710-103">In ASP.NET Core 3.0, il `internal`modificatore di accesso è cambiato in .</span><span class="sxs-lookup"><span data-stu-id="b3710-103">In ASP.NET Core 3.0, the access modifier changed to `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b3710-104">Versione introdotta</span><span class="sxs-lookup"><span data-stu-id="b3710-104">Version introduced</span></span>

<span data-ttu-id="b3710-105">3.0</span><span class="sxs-lookup"><span data-stu-id="b3710-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b3710-106">Motivo della modifica</span><span class="sxs-lookup"><span data-stu-id="b3710-106">Reason for change</span></span>

<span data-ttu-id="b3710-107">La modifica è in corso per:</span><span class="sxs-lookup"><span data-stu-id="b3710-107">The change is being made to:</span></span>

* <span data-ttu-id="b3710-108">Applicare la coerenza con altre `ConsoleLogger`implementazioni del logger, ad esempio .</span><span class="sxs-lookup"><span data-stu-id="b3710-108">Enforce consistency with other logger implementations such as `ConsoleLogger`.</span></span>
* <span data-ttu-id="b3710-109">Ridurre la superficie dell'API.</span><span class="sxs-lookup"><span data-stu-id="b3710-109">Reduce the API surface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b3710-110">Azione consigliata</span><span class="sxs-lookup"><span data-stu-id="b3710-110">Recommended action</span></span>

<span data-ttu-id="b3710-111">Utilizzare <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` il metodo di estensione per abilitare la registrazione di debug.</span><span class="sxs-lookup"><span data-stu-id="b3710-111">Use the <xref:Microsoft.Extensions.Logging.DebugLoggerFactoryExtensions.AddDebug%2A> `ILoggingBuilder` extension method to enable debug logging.</span></span> <span data-ttu-id="b3710-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider>è anche `public` ancora nel caso in cui il servizio deve essere registrato manualmente.</span><span class="sxs-lookup"><span data-stu-id="b3710-112"><xref:Microsoft.Extensions.Logging.Debug.DebugLoggerProvider> is also still `public` in the event the service needs to be registered manually.</span></span>

#### <a name="category"></a><span data-ttu-id="b3710-113">Category</span><span class="sxs-lookup"><span data-stu-id="b3710-113">Category</span></span>

<span data-ttu-id="b3710-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b3710-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b3710-115">API interessate</span><span class="sxs-lookup"><span data-stu-id="b3710-115">Affected APIs</span></span>

<xref:Microsoft.Extensions.Logging.Debug.DebugLogger?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.Extensions.Logging.Debug.DebugLogger`

-->
