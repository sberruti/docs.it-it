---
title: Installare .NET Core in Debian 10-Package Manager-.NET Core
description: Usare uno Gestione pacchetti per installare .NET Core SDK e Runtime in Debian 10.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 1280758e7ea9300d83fa01532f3b051c6e1c0c67
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451073"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="30da6-103">Gestione pacchetti Debian 10-installare .NET Core</span><span class="sxs-lookup"><span data-stu-id="30da6-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="30da6-104">Questo articolo descrive come usare un gestore di pacchetti per installare .NET Core in Debian 10.</span><span class="sxs-lookup"><span data-stu-id="30da6-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span> <span data-ttu-id="30da6-105">Se si sta installando il runtime, si consiglia di installare il [runtime di ASP.NET Core](#install-the-aspnet-core-runtime), perché include sia .NET Core che ASP.NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="30da6-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="30da6-106">Registrare la chiave e il feed Microsoft</span><span class="sxs-lookup"><span data-stu-id="30da6-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="30da6-107">Prima di installare .NET, è necessario:</span><span class="sxs-lookup"><span data-stu-id="30da6-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="30da6-108">Registrare la chiave Microsoft</span><span class="sxs-lookup"><span data-stu-id="30da6-108">Register the Microsoft key</span></span>
- <span data-ttu-id="30da6-109">registrare il repository del prodotto</span><span class="sxs-lookup"><span data-stu-id="30da6-109">register the product repository</span></span>
- <span data-ttu-id="30da6-110">Installare le dipendenze necessarie</span><span class="sxs-lookup"><span data-stu-id="30da6-110">Install required dependencies</span></span>

<span data-ttu-id="30da6-111">Questa operazione deve essere eseguita solo una volta per ogni computer.</span><span class="sxs-lookup"><span data-stu-id="30da6-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="30da6-112">Aprire un terminale ed eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="30da6-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="30da6-113">Installare il .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="30da6-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="30da6-114">Aggiornare i prodotti disponibili per l'installazione, quindi installare il .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="30da6-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="30da6-115">Nel terminale eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="30da6-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="30da6-116">Installare il runtime di ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="30da6-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="30da6-117">Aggiornare i prodotti disponibili per l'installazione, quindi installare il runtime di ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="30da6-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="30da6-118">Nel terminale eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="30da6-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="30da6-119">Installare il runtime di .NET Core</span><span class="sxs-lookup"><span data-stu-id="30da6-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="30da6-120">Aggiornare i prodotti disponibili per l'installazione, quindi installare il runtime di .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30da6-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="30da6-121">Nel terminale eseguire i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="30da6-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="30da6-122">Come installare altre versioni</span><span class="sxs-lookup"><span data-stu-id="30da6-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]