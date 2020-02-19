---
title: Modifiche di rilievo della crittografia
description: Elenca le modifiche di rilievo correlate alla crittografia in .NET Core.
ms.date: 02/10/2020
ms.openlocfilehash: c25eefa8e3ee01ed7a1df4ec4aa9225f2c347a4d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449219"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="7c790-103">Modifiche di rilievo della crittografia</span><span class="sxs-lookup"><span data-stu-id="7c790-103">Cryptography breaking changes</span></span>

<span data-ttu-id="7c790-104">In questa pagina sono documentate le modifiche di rilievo seguenti:</span><span class="sxs-lookup"><span data-stu-id="7c790-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="7c790-105">Modifica</span><span class="sxs-lookup"><span data-stu-id="7c790-105">Breaking change</span></span> | <span data-ttu-id="7c790-106">Versione introdotta</span><span class="sxs-lookup"><span data-stu-id="7c790-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="7c790-107">Il valore predefinito di EnvelopedCms è AES-256 Encryption</span><span class="sxs-lookup"><span data-stu-id="7c790-107">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="7c790-108">3.0</span><span class="sxs-lookup"><span data-stu-id="7c790-108">3.0</span></span> |
| [<span data-ttu-id="7c790-109">Dimensioni minime per la generazione della chiave RSAOpenSsl aumentata</span><span class="sxs-lookup"><span data-stu-id="7c790-109">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="7c790-110">3.0</span><span class="sxs-lookup"><span data-stu-id="7c790-110">3.0</span></span> |
| [<span data-ttu-id="7c790-111">.NET Core 3,0 preferisce OpenSSL 1.1. x a OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="7c790-111">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="7c790-112">3.0</span><span class="sxs-lookup"><span data-stu-id="7c790-112">3.0</span></span> |
| [<span data-ttu-id="7c790-113">Migliore convalida degli argomenti nel costruttore Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="7c790-113">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor) | <span data-ttu-id="7c790-114">3.0</span><span class="sxs-lookup"><span data-stu-id="7c790-114">3.0</span></span> |
| [<span data-ttu-id="7c790-115">Il parametro booleano di SignedCms. ComputeSignature è rispettato</span><span class="sxs-lookup"><span data-stu-id="7c790-115">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="7c790-116">2.1</span><span class="sxs-lookup"><span data-stu-id="7c790-116">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="7c790-117">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7c790-117">.NET Core 3.0</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="7c790-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7c790-118">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
