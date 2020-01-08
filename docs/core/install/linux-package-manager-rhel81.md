---
title: Installare .NET Core in Linux RHEL 8,1 Package Manager-.NET Core
description: Usare uno Gestione pacchetti per installare .NET Core SDK e Runtime in RHEL 8,1.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 8674b5d9d0f0ee384ca6798a7ea699bad67c5e5e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341179"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="a5d08-103">Gestione pacchetti RHEL 8,1-installare .NET Core</span><span class="sxs-lookup"><span data-stu-id="a5d08-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="a5d08-104">Questo articolo descrive come usare un gestore di pacchetti per installare .NET Core in RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="a5d08-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span> <span data-ttu-id="a5d08-105">.NET Core 3,1 non è ancora disponibile per RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="a5d08-105">.NET Core 3.1 is not yet available for RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="a5d08-106">RHEL 8,0 non include .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="a5d08-106">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="a5d08-107">Usare il comando `yum upgrade` per eseguire l'aggiornamento a RHEL 8,1.</span><span class="sxs-lookup"><span data-stu-id="a5d08-107">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="a5d08-108">Registrare la sottoscrizione di Red Hat</span><span class="sxs-lookup"><span data-stu-id="a5d08-108">Register your Red Hat subscription</span></span>

<span data-ttu-id="a5d08-109">Per installare .NET Core da Red Hat in RHEL, è prima necessario registrarsi usando Red Hat Subscription Manager.</span><span class="sxs-lookup"><span data-stu-id="a5d08-109">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="a5d08-110">Se questa operazione non è stata eseguita nel sistema o se non si è certi, vedere la [documentazione del prodotto Red Hat per .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="a5d08-110">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="a5d08-111">Installare il .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a5d08-111">Install the .NET Core SDK</span></span>

<span data-ttu-id="a5d08-112">Dopo la registrazione con Gestione sottoscrizioni, si è pronti per installare e abilitare la .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a5d08-112">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="a5d08-113">Nel terminale eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="a5d08-113">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="a5d08-114">Installare il runtime di ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a5d08-114">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="a5d08-115">Dopo la registrazione con Gestione sottoscrizioni, si è pronti per installare e abilitare il runtime di ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5d08-115">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="a5d08-116">Nel terminale eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="a5d08-116">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="a5d08-117">Installare il runtime di .NET Core</span><span class="sxs-lookup"><span data-stu-id="a5d08-117">Install the .NET Core Runtime</span></span>

<span data-ttu-id="a5d08-118">Dopo la registrazione con Subscription Manager, si è pronti per installare e abilitare il runtime di .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5d08-118">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="a5d08-119">Nel terminale eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="a5d08-119">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a><span data-ttu-id="a5d08-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a5d08-120">See also</span></span>

- [<span data-ttu-id="a5d08-121">Uso di .NET Core 3,0 in Red Hat Enterprise Linux 8</span><span class="sxs-lookup"><span data-stu-id="a5d08-121">Using .NET Core 3.0 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
