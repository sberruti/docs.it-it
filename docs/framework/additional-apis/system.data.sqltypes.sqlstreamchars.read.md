---
title: Metodo SqlStreamChars.Read (Char [], Int32, Int32) (System.Data.SqlTypes)
author: douglaslMS
ms.author: douglasl
ms.date: 12/20/2018
ms.technology:
- dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: ce89e5f757034b79d5a60a1abbd49fdb2fdf3f06
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222116"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a><span data-ttu-id="24807-102">Metodo SqlStreamChars.Read (Char [], Int32, Int32)</span><span class="sxs-lookup"><span data-stu-id="24807-102">SqlStreamChars.Read(Char[], Int32, Int32) Method</span></span>

<span data-ttu-id="24807-103">Quando sottoposto a override in una classe derivata, legge il successivo set di caratteri dal flusso di input.</span><span class="sxs-lookup"><span data-stu-id="24807-103">When overridden in a derived class, reads the next set of characters from the input stream.</span></span> <span data-ttu-id="24807-104">L'assembly contenente questo metodo ha una relazione di tipo friend SQLAccess.</span><span class="sxs-lookup"><span data-stu-id="24807-104">The assembly that contains this method has a friend relationship with SQLAccess.dll.</span></span> <span data-ttu-id="24807-105">Si tratta per l'uso da SQL Server.</span><span class="sxs-lookup"><span data-stu-id="24807-105">It's intended for use by SQL Server.</span></span> <span data-ttu-id="24807-106">Per altri database, usare il meccanismo di hosting fornito da tale database.</span><span class="sxs-lookup"><span data-stu-id="24807-106">For other databases, use the hosting mechanism provided by that database.</span></span>

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a><span data-ttu-id="24807-107">Parametri</span><span class="sxs-lookup"><span data-stu-id="24807-107">Parameters</span></span>

`buffer`\
<span data-ttu-id="24807-108">Matrice di caratteri da leggere.</span><span class="sxs-lookup"><span data-stu-id="24807-108">A char array to read.</span></span>

`offset`\
<span data-ttu-id="24807-109">Un offset relativo all'origine.</span><span class="sxs-lookup"><span data-stu-id="24807-109">An offset relative to origin.</span></span>

`count`\
<span data-ttu-id="24807-110">Il numero di caratteri da leggere dal flusso corrente.</span><span class="sxs-lookup"><span data-stu-id="24807-110">The number of characters to be read from the current stream.</span></span>

## <a name="returns"></a><span data-ttu-id="24807-111">Valore restituito</span><span class="sxs-lookup"><span data-stu-id="24807-111">Returns</span></span>

<xref:System.Int32>\
<span data-ttu-id="24807-112">Numero complessivo di caratteri letti nel buffer.</span><span class="sxs-lookup"><span data-stu-id="24807-112">The total number of characters read into the buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="24807-113">Note</span><span class="sxs-lookup"><span data-stu-id="24807-113">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="24807-114">Il `SqlStreamChars.Read` metodo è privato e non deve essere utilizzato direttamente nel codice.</span><span class="sxs-lookup"><span data-stu-id="24807-114">The `SqlStreamChars.Read` method is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="24807-115">Microsoft non supporta l'uso di questo campo in un'applicazione di produzione in alcuna circostanza.</span><span class="sxs-lookup"><span data-stu-id="24807-115">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="24807-116">Requisiti</span><span class="sxs-lookup"><span data-stu-id="24807-116">Requirements</span></span>

<span data-ttu-id="24807-117">**Spazio dei nomi:** <xref:System.Data.SqlTypes></span><span class="sxs-lookup"><span data-stu-id="24807-117">**Namespace:** <xref:System.Data.SqlTypes></span></span>

<span data-ttu-id="24807-118">**Assembly:** System. Data (in System)</span><span class="sxs-lookup"><span data-stu-id="24807-118">**Assembly:** System.Data (in System.Data.dll)</span></span>

<span data-ttu-id="24807-119">**Versioni di .NET framework:** Disponibile dalla 2.0.</span><span class="sxs-lookup"><span data-stu-id="24807-119">**.NET Framework versions:** Available since 2.0.</span></span>