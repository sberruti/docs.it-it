---
title: Installare .NET Core in openSUSE 15-Package Manager-.NET Core
description: Usare uno Gestione pacchetti per installare .NET Core SDK e Runtime in openSUSE 15.
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: ae0f6664c0545ceb047cd9b110fe3f26740e5816
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116152"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="3a870-103">Gestione pacchetti openSUSE 15-installare .NET Core</span><span class="sxs-lookup"><span data-stu-id="3a870-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="3a870-104">Questo articolo descrive come usare un gestore di pacchetti per installare .NET Core in openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="3a870-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span> <span data-ttu-id="3a870-105">Se si sta installando il runtime, si consiglia di installare il [runtime di ASP.NET Core](#install-the-aspnet-core-runtime), perché include sia .NET Core che ASP.NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="3a870-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="3a870-106">Registrare la chiave Microsoft e il feed</span><span class="sxs-lookup"><span data-stu-id="3a870-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="3a870-107">Prima di installare .NET, è necessario:</span><span class="sxs-lookup"><span data-stu-id="3a870-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="3a870-108">Registrare la chiave Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3a870-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="3a870-109">Registrare il repository del prodotto.</span><span class="sxs-lookup"><span data-stu-id="3a870-109">Register the product repository.</span></span>
- <span data-ttu-id="3a870-110">Installare le dipendenze necessarie.</span><span class="sxs-lookup"><span data-stu-id="3a870-110">Install required dependencies.</span></span>

<span data-ttu-id="3a870-111">Questa operazione deve essere eseguita una volta sola per ogni computer.</span><span class="sxs-lookup"><span data-stu-id="3a870-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="3a870-112">Aprire un terminale ed eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="3a870-112">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="3a870-113">Installare il .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="3a870-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="3a870-114">Aggiornare i prodotti disponibili per l'installazione, quindi installare il .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="3a870-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="3a870-115">Nel terminale eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="3a870-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="3a870-116">Installare il runtime di ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3a870-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="3a870-117">Aggiornare i prodotti disponibili per l'installazione, quindi installare il runtime di ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3a870-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="3a870-118">Nel terminale eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="3a870-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="3a870-119">Installare il runtime di .NET Core</span><span class="sxs-lookup"><span data-stu-id="3a870-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="3a870-120">Aggiornare i prodotti disponibili per l'installazione, quindi installare il runtime di .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3a870-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="3a870-121">Nel terminale eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="3a870-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="3a870-122">Come installare altre versioni</span><span class="sxs-lookup"><span data-stu-id="3a870-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
