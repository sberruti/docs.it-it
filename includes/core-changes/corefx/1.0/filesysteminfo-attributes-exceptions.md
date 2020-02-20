---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449401"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="daf22-101">UnauthorizedAccessException generata da FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="daf22-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="daf22-102">In .NET Core viene generata un'<xref:System.UnauthorizedAccessException> quando il chiamante tenta di impostare un valore di attributo di file ma non dispone dell'autorizzazione di scrittura.</span><span class="sxs-lookup"><span data-stu-id="daf22-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="daf22-103">Descrizione della modifica</span><span class="sxs-lookup"><span data-stu-id="daf22-103">Change description</span></span>

<span data-ttu-id="daf22-104">In .NET Framework, viene generata un'<xref:System.ArgumentException> quando il chiamante tenta di impostare un valore di attributo di file in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> ma non dispone dell'autorizzazione di scrittura.</span><span class="sxs-lookup"><span data-stu-id="daf22-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="daf22-105">In .NET Core viene invece generata un'<xref:System.UnauthorizedAccessException>.</span><span class="sxs-lookup"><span data-stu-id="daf22-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="daf22-106">In .NET Core viene ancora generata un'<xref:System.ArgumentException> se il chiamante tenta di impostare un attributo di file non valido.</span><span class="sxs-lookup"><span data-stu-id="daf22-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="daf22-107">Versione introdotta</span><span class="sxs-lookup"><span data-stu-id="daf22-107">Version introduced</span></span>

<span data-ttu-id="daf22-108">1.0</span><span class="sxs-lookup"><span data-stu-id="daf22-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="daf22-109">Azione consigliata</span><span class="sxs-lookup"><span data-stu-id="daf22-109">Recommended action</span></span>

<span data-ttu-id="daf22-110">Modificare le istruzioni `catch` per intercettare un <xref:System.UnauthorizedAccessException> anziché, o in aggiunta, un <xref:System.ArgumentException>, se necessario.</span><span class="sxs-lookup"><span data-stu-id="daf22-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="daf22-111">Category</span><span class="sxs-lookup"><span data-stu-id="daf22-111">Category</span></span>

<span data-ttu-id="daf22-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="daf22-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="daf22-113">API interessate</span><span class="sxs-lookup"><span data-stu-id="daf22-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
