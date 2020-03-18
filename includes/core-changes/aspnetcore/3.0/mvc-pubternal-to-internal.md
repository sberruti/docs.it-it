---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901834"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="acb6f-101">MVC: i tipi "Pubternal" sono cambiati in interni</span><span class="sxs-lookup"><span data-stu-id="acb6f-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="acb6f-102">In ASP.NET Core 3.0, tutti i tipi "pubternal" in MVC sono stati aggiornati in modo che siano `public` in uno spazio dei nomi supportato o `internal` in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="acb6f-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="acb6f-103">Descrizione modifica:</span><span class="sxs-lookup"><span data-stu-id="acb6f-103">Change description</span></span>

<span data-ttu-id="acb6f-104">In ASP.NET Core, i tipi "pubternal" vengono dichiarati come `public` ma risiedono in uno `.Internal`spazio dei nomi con suffisso .suffix.</span><span class="sxs-lookup"><span data-stu-id="acb6f-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="acb6f-105">Sebbene questi `public`tipi siano , non hanno criteri di supporto e sono soggetti a modifiche di rilievo.</span><span class="sxs-lookup"><span data-stu-id="acb6f-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="acb6f-106">Sfortunatamente, l'uso accidentale di questi tipi è stato comune, con conseguente interruzione delle modifiche a questi progetti e limitando la capacità di mantenere il framework.</span><span class="sxs-lookup"><span data-stu-id="acb6f-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="acb6f-107">Versione introdotta</span><span class="sxs-lookup"><span data-stu-id="acb6f-107">Version introduced</span></span>

<span data-ttu-id="acb6f-108">3.0</span><span class="sxs-lookup"><span data-stu-id="acb6f-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="acb6f-109">Comportamento precedente</span><span class="sxs-lookup"><span data-stu-id="acb6f-109">Old behavior</span></span>

<span data-ttu-id="acb6f-110">Alcuni tipi in `public` MVC `.Internal` erano ma in uno spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="acb6f-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="acb6f-111">Questi tipi non avevano una politica di supporto e sono stati soggetti a modifiche di rilievo.</span><span class="sxs-lookup"><span data-stu-id="acb6f-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="acb6f-112">Nuovo comportamento</span><span class="sxs-lookup"><span data-stu-id="acb6f-112">New behavior</span></span>

<span data-ttu-id="acb6f-113">Tutti questi tipi vengono `public` aggiornati per essere `internal`in uno spazio dei nomi supportato o contrassegnati come .</span><span class="sxs-lookup"><span data-stu-id="acb6f-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="acb6f-114">Motivo della modifica</span><span class="sxs-lookup"><span data-stu-id="acb6f-114">Reason for change</span></span>

<span data-ttu-id="acb6f-115">L'uso accidentale dei tipi "pubternal" è stato comune, con conseguente modifiche di rilievo a questi progetti e limitando la capacità di mantenere il framework.</span><span class="sxs-lookup"><span data-stu-id="acb6f-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="acb6f-116">Azione consigliata</span><span class="sxs-lookup"><span data-stu-id="acb6f-116">Recommended action</span></span>

<span data-ttu-id="acb6f-117">Se si utilizzano tipi che `public` sono diventati veramente e sono stati spostati in un nuovo spazio dei nomi supportato, aggiornare i riferimenti in modo che corrispondano ai nuovi spazi dei nomi.</span><span class="sxs-lookup"><span data-stu-id="acb6f-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="acb6f-118">Se si utilizzano tipi che `internal`sono stati contrassegnati come , è necessario trovare un'alternativa.</span><span class="sxs-lookup"><span data-stu-id="acb6f-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="acb6f-119">I tipi "pubternal" in precedenza non erano mai supportati per l'uso pubblico.</span><span class="sxs-lookup"><span data-stu-id="acb6f-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="acb6f-120">Se in questi spazi dei nomi sono presenti tipi specifici critici per le app, presentare un problema in [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="acb6f-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span> <span data-ttu-id="acb6f-121">È possibile tenere conto `public`della creazione dei tipi richiesti.</span><span class="sxs-lookup"><span data-stu-id="acb6f-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="acb6f-122">Category</span><span class="sxs-lookup"><span data-stu-id="acb6f-122">Category</span></span>

<span data-ttu-id="acb6f-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="acb6f-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="acb6f-124">API interessate</span><span class="sxs-lookup"><span data-stu-id="acb6f-124">Affected APIs</span></span>

<span data-ttu-id="acb6f-125">Questa modifica include i tipi negli spazi dei nomi seguenti:This change includes types in the following namespaces:</span><span class="sxs-lookup"><span data-stu-id="acb6f-125">This change includes types in the following namespaces:</span></span>

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
