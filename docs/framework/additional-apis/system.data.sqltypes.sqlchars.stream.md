---
title: Proprietà SqlChars.Stream (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/19/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlChars.Stream
- System.Data.SqlTypes.SqlChars.get_Stream
- System.Data.SqlTypes.SqlChars.set_Stream
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: d756b78a7cdbc12562e474ca3d2c9a1f3529f6bf
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223052"
---
# <a name="sqlcharsstream-property"></a><span data-ttu-id="6ad47-102">Proprietà SqlChars.Stream</span><span class="sxs-lookup"><span data-stu-id="6ad47-102">SqlChars.Stream Property</span></span>

<span data-ttu-id="6ad47-103">Ottiene o imposta il flusso di caratteri.</span><span class="sxs-lookup"><span data-stu-id="6ad47-103">Gets or sets the character stream.</span></span> <span data-ttu-id="6ad47-104">L'assembly che contiene questa proprietà ha una relazione di tipo friend SQLAccess.</span><span class="sxs-lookup"><span data-stu-id="6ad47-104">The assembly that contains this property has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="6ad47-105">Si tratta per l'uso da SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6ad47-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="6ad47-106">Per altri database, usare il meccanismo di hosting fornito da tale database.</span><span class="sxs-lookup"><span data-stu-id="6ad47-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
internal SqlStreamChars Stream { get; set; }
```

## <a name="property-value"></a><span data-ttu-id="6ad47-107">Valore della proprietà</span><span class="sxs-lookup"><span data-stu-id="6ad47-107">Property value</span></span>

`System.Data.SqlTypes.SqlStreamChars`\
<span data-ttu-id="6ad47-108">Il flusso di caratteri.</span><span class="sxs-lookup"><span data-stu-id="6ad47-108">The character stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ad47-109">Note</span><span class="sxs-lookup"><span data-stu-id="6ad47-109">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="6ad47-110">Il `SqlChars.Stream` proprietà sono interna e non deve essere utilizzato direttamente nel codice.</span><span class="sxs-lookup"><span data-stu-id="6ad47-110">The `SqlChars.Stream` property is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="6ad47-111">Microsoft non supporta l'uso di questa proprietà in un'applicazione di produzione in alcuna circostanza.</span><span class="sxs-lookup"><span data-stu-id="6ad47-111">Microsoft does not support the use of this property in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6ad47-112">Requisiti</span><span class="sxs-lookup"><span data-stu-id="6ad47-112">Requirements</span></span>

<span data-ttu-id="6ad47-113">**Spazio dei nomi:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="6ad47-113">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="6ad47-114">**Assembly:** System. Data (in System)</span><span class="sxs-lookup"><span data-stu-id="6ad47-114">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="6ad47-115">**Versioni di .NET framework:** Disponibile dalla 2.0.</span><span class="sxs-lookup"><span data-stu-id="6ad47-115">**.NET Framework versions:** Available since 2.0.</span></span>