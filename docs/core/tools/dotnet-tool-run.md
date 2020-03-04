---
title: comando DotNet Tool Run
description: Il comando DotNet Tool Run richiama uno strumento locale.
ms.date: 02/14/2020
ms.openlocfilehash: 76830b8a8088fbf21f14ab0722b9547eabde7ba4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156959"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="fd1f0-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="fd1f0-103">dotnet tool run</span></span>

<span data-ttu-id="fd1f0-104">**Questo articolo si applica a:** ✔️ .net core 3,0 SDK e versioni successive</span><span class="sxs-lookup"><span data-stu-id="fd1f0-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fd1f0-105">Nome</span><span class="sxs-lookup"><span data-stu-id="fd1f0-105">Name</span></span>

<span data-ttu-id="fd1f0-106">`dotnet tool run`: richiama uno strumento locale.</span><span class="sxs-lookup"><span data-stu-id="fd1f0-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fd1f0-107">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="fd1f0-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>
dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="fd1f0-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="fd1f0-108">Description</span></span>

<span data-ttu-id="fd1f0-109">Il comando `dotnet tool run` Cerca i file manifesto degli strumenti che rientrano nell'ambito della directory corrente.</span><span class="sxs-lookup"><span data-stu-id="fd1f0-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="fd1f0-110">Quando viene trovato un riferimento allo strumento specificato, viene eseguito lo strumento.</span><span class="sxs-lookup"><span data-stu-id="fd1f0-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="fd1f0-111">Per ulteriori informazioni, vedere [Invoke a local Tool](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="fd1f0-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="fd1f0-112">Argomenti</span><span class="sxs-lookup"><span data-stu-id="fd1f0-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="fd1f0-113">Nome del comando dello strumento da eseguire.</span><span class="sxs-lookup"><span data-stu-id="fd1f0-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="fd1f0-114">Opzioni</span><span class="sxs-lookup"><span data-stu-id="fd1f0-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="fd1f0-115">Stampa una breve guida per il comando.</span><span class="sxs-lookup"><span data-stu-id="fd1f0-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="fd1f0-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="fd1f0-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="fd1f0-117">Esegue lo strumento locale `dotnetsay`.</span><span class="sxs-lookup"><span data-stu-id="fd1f0-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd1f0-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fd1f0-118">See also</span></span>

- [<span data-ttu-id="fd1f0-119">Strumenti di .NET Core</span><span class="sxs-lookup"><span data-stu-id="fd1f0-119">.NET Core tools</span></span>](global-tools.md)
