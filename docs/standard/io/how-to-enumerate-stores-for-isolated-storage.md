---
title: 'Procedura: Enumerare gli archivi per lo spazio di memorizzazione isolato'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
ms.openlocfilehash: 3ba38093e9e978c89cdb2bb7a584ed9e04c1096d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707528"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="d4594-102">Procedura: Enumerare gli archivi per lo spazio di memorizzazione isolato</span><span class="sxs-lookup"><span data-stu-id="d4594-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="d4594-103">È possibile enumerare tutti gli archivi isolati dell'utente corrente utilizzando il metodo statico <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d4594-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="d4594-104">Questo metodo accetta un valore <xref:System.IO.IsolatedStorage.IsolatedStorageScope> e restituisce un enumeratore <xref:System.IO.IsolatedStorage.IsolatedStorageFile>.</span><span class="sxs-lookup"><span data-stu-id="d4594-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="d4594-105">Per enumerare gli archivi, è necessario avere l'autorizzazione <xref:System.Security.Permissions.IsolatedStorageFilePermission> con il valore <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> specificato.</span><span class="sxs-lookup"><span data-stu-id="d4594-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="d4594-106">Se si chiama il metodo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> con il valore <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>, viene restituita una matrice di oggetti <xref:System.IO.IsolatedStorage.IsolatedStorageFile> definiti per l'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="d4594-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4594-107">Esempio</span><span class="sxs-lookup"><span data-stu-id="d4594-107">Example</span></span>  
 <span data-ttu-id="d4594-108">L'esempio di codice seguente ottiene uno spazio di memorizzazione isolato in base all'utente e all'assembly, crea alcuni file e recupera i file usando il metodo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="d4594-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d4594-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d4594-109">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="d4594-110">Spazio di memorizzazione isolato</span><span class="sxs-lookup"><span data-stu-id="d4594-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
