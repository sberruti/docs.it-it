---
title: Installare .NET Core in Linux RHEL 7 Package Manager-.NET Core
description: Usare uno Gestione pacchetti per installare .NET Core SDK e Runtime in RHEL 7.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: bcc41bfcd7c6d03038952e3faaf07952c3deb69d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715541"
---
# <a name="rhel-7-package-manager---install-net-core"></a>Gestione pacchetti RHEL 7-installare .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Questo articolo descrive come usare un gestore di pacchetti per installare .NET Core in RHEL 7. .NET Core 3,1 non è ancora disponibile per RHEL 7.

## <a name="register-your-red-hat-subscription"></a>Registrare la sottoscrizione di Red Hat

Per installare .NET Core da Red Hat in RHEL, è prima necessario registrarsi usando Red Hat Subscription Manager. Se questa operazione non è stata eseguita nel sistema o se non si è certi, vedere la [documentazione del prodotto Red Hat per .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="install-the-net-core-sdk"></a>Installare il .NET Core SDK

Dopo la registrazione con Gestione sottoscrizioni, si è pronti per installare e abilitare la .NET Core SDK. Nel terminale eseguire i comandi seguenti per abilitare il canale DotNet di RHEL 7 e installare.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a>Installare il runtime di ASP.NET Core

Dopo la registrazione con Gestione sottoscrizioni, si è pronti per installare e abilitare il runtime di ASP.NET Core. Nel terminale eseguire i comandi seguenti.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a>Installare il runtime di .NET Core

Dopo la registrazione con Subscription Manager, si è pronti per installare e abilitare il runtime di .NET Core. Nel terminale eseguire i comandi seguenti.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a>Vedere anche

- [Uso di .NET Core 3,0 in Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)
