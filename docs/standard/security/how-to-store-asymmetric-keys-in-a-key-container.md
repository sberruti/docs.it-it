---
title: 'Procedura: archiviare chiavi asimmetriche in un contenitore di chiavi'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET Framework], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET Framework]
- encryption [.NET Framework], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
ms.openlocfilehash: 8ca4c4c5b1257411ecdf86858040bf428a9e6ce0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706058"
---
# <a name="how-to-store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="ebe46-102">Procedura: archiviare chiavi asimmetriche in un contenitore di chiavi</span><span class="sxs-lookup"><span data-stu-id="ebe46-102">How to: Store Asymmetric Keys in a Key Container</span></span>
<span data-ttu-id="ebe46-103">Le chiavi private asimmetriche non devono essere mai archiviate in modalità verbatim o in testo normale nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="ebe46-103">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="ebe46-104">Se è necessario archiviare una chiave privata, è opportuno usare un contenitore di chiavi.</span><span class="sxs-lookup"><span data-stu-id="ebe46-104">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="ebe46-105">Per altre informazioni sui contenitori di chiavi, vedere[Informazioni sui contenitori di chiavi RSA a livello di computer e utente](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ebe46-105">For more information on key containers, see [Understanding Machine-Level and User-Level RSA Key Containers](https://docs.microsoft.com/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span></span>  
  
### <a name="to-create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="ebe46-106">Per creare una chiave asimmetrica e salvarla in un contenitore di chiavi</span><span class="sxs-lookup"><span data-stu-id="ebe46-106">To create an asymmetric key and save it in a key container</span></span>  
  
1. <span data-ttu-id="ebe46-107">Creare una nuova istanza di una classe <xref:System.Security.Cryptography.CspParameters> e passare il nome a cui si desidera chiamare il contenitore di chiavi nel campo <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ebe46-107">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>  
  
2. <span data-ttu-id="ebe46-108">Creare una nuova istanza di una classe che deriva dalla classe <xref:System.Security.Cryptography.AsymmetricAlgorithm> (in genere **RSACryptoServiceProvider** o **DSACryptoServiceProvider**) e passare l'oggetto **CspParameters** creato in precedenza al relativo costruttore.</span><span class="sxs-lookup"><span data-stu-id="ebe46-108">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
### <a name="to-delete-the-key-from-a-key-container"></a><span data-ttu-id="ebe46-109">Per eliminare la chiave da un contenitore di chiavi</span><span class="sxs-lookup"><span data-stu-id="ebe46-109">To delete the key from a key container</span></span>  
  
1. <span data-ttu-id="ebe46-110">Creare una nuova istanza di una classe **CspParameters** e passare il nome da usare per il contenitore di chiavi al campo **CspParameters.KeyContainerName**.</span><span class="sxs-lookup"><span data-stu-id="ebe46-110">Create a new instance of a **CspParameters** class and pass the name that you want to call the key container to the **CspParameters.KeyContainerName** field.</span></span>  
  
2. <span data-ttu-id="ebe46-111">Creare una nuova istanza di una classe derivata dalla classe **AsymmetricAlgorithm** (in genere **RSACryptoServiceProvider** o **DSACryptoServiceProvider**), quindi passare l'oggetto **CspParameters** creato in precedenza al rispettivo costruttore.</span><span class="sxs-lookup"><span data-stu-id="ebe46-111">Create a new instance of a class that derives from the **AsymmetricAlgorithm** class (usually **RSACryptoServiceProvider** or **DSACryptoServiceProvider**) and pass the previously created **CspParameters** object to its constructor.</span></span>  
  
3. <span data-ttu-id="ebe46-112">Impostare la proprietà **PersistKeyInCSP** della classe derivata da **AsymmetricAlgorithm** su **false** (**False** in Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ebe46-112">Set the **PersistKeyInCSP** property of the class that derives from **AsymmetricAlgorithm** to **false** (**False** in Visual Basic).</span></span>  
  
4. <span data-ttu-id="ebe46-113">Chiamare il metodo **Clear** della classe derivata da **AsymmetricAlgorithm**.</span><span class="sxs-lookup"><span data-stu-id="ebe46-113">Call the **Clear** method of the class that derives from **AsymmetricAlgorithm**.</span></span> <span data-ttu-id="ebe46-114">Questo metodo rilascia tutte le risorse della classe e cancella il contenitore di chiavi.</span><span class="sxs-lookup"><span data-stu-id="ebe46-114">This method releases all resources of the class and clears the key container.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebe46-115">Esempio</span><span class="sxs-lookup"><span data-stu-id="ebe46-115">Example</span></span>  
 <span data-ttu-id="ebe46-116">Il seguente esempio illustra come creare una chiave asimmetrica, salvarla in un contenitore di chiavi, recuperare la chiave in un secondo momento ed eliminarla dal contenitore.</span><span class="sxs-lookup"><span data-stu-id="ebe46-116">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>  
  
 <span data-ttu-id="ebe46-117">Si noti che il codice del metodo `GenKey_SaveInContainer` è simile a quello del metodo `GetKeyFromContainer`.</span><span class="sxs-lookup"><span data-stu-id="ebe46-117">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span>  <span data-ttu-id="ebe46-118">Quando si specifica un nome di contenitore di chiavi per un oggetto <xref:System.Security.Cryptography.CspParameters> e lo si passa a un oggetto <xref:System.Security.Cryptography.AsymmetricAlgorithm> con la proprietà <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> o la proprietà <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> impostata su true, si verifica quanto segue.</span><span class="sxs-lookup"><span data-stu-id="ebe46-118">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to true, the following occurs.</span></span>  <span data-ttu-id="ebe46-119">Se un contenitore di chiavi con il nome specificato non esiste, ne sarà creato uno e la chiave sarà resa persistente.</span><span class="sxs-lookup"><span data-stu-id="ebe46-119">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>  <span data-ttu-id="ebe46-120">Se esiste un contenitore di chiavi con il nome specificato, la chiave nel contenitore sarà caricata automaticamente nell'oggetto <xref:System.Security.Cryptography.AsymmetricAlgorithm> corrente.</span><span class="sxs-lookup"><span data-stu-id="ebe46-120">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>  <span data-ttu-id="ebe46-121">Il codice nel metodo `GenKey_SaveInContainer` rende quindi permanente la chiave poiché è eseguito per primo, mentre il codice nel metodo `GetKeyFromContainer` carica la chiave poiché è eseguito per secondo.</span><span class="sxs-lookup"><span data-stu-id="ebe46-121">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it is run second.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
 _  
  
Public Class StoreKey  
  
    Public Shared Sub Main()  
        Try  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
  
            ' Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer")  
  
            ' Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer")  
        Catch e As CryptographicException  
            Console.WriteLine(e.Message)  
        End Try  
    End Sub  
  
    Public Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        ' name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key added to container:  {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub GetKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container MyKeyContainerName.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : {0}", rsa.ToXmlString(True))  
    End Sub  
  
    Public Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)  
        ' Create the CspParameters object and set the key container   
        '  name used to store the RSA key pair.  
        Dim cp As New CspParameters()  
        cp.KeyContainerName = ContainerName  
  
        ' Create a new instance of RSACryptoServiceProvider that accesses  
        ' the key container.  
        Dim rsa As New RSACryptoServiceProvider(cp)  
  
        ' Delete the key entry in the container.  
        rsa.PersistKeyInCsp = False  
  
        ' Call Clear to release resources and delete the key from the container.  
        rsa.Clear()  
  
        Console.WriteLine("Key deleted.")  
    End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
  
public class StoreKey  
  
{  
    public static void Main()  
    {  
        try  
        {  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Retrieve the key from the container.  
            GetKeyFromContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
  
            // Create a key and save it in a container.  
            GenKey_SaveInContainer("MyKeyContainer");  
  
            // Delete the key from the container.  
            DeleteKeyFromContainer("MyKeyContainer");  
        }  
        catch(CryptographicException e)  
        {  
            Console.WriteLine(e.Message);  
        }  
  
    }  
  
    public static void GenKey_SaveInContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key added to container: \n  {0}", rsa.ToXmlString(true));  
    }  
  
    public static void GetKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container MyKeyContainerName.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Display the key information to the console.  
        Console.WriteLine("Key retrieved from container : \n {0}", rsa.ToXmlString(true));  
    }  
  
    public static void DeleteKeyFromContainer(string ContainerName)  
    {  
        // Create the CspParameters object and set the key container   
        // name used to store the RSA key pair.  
        CspParameters cp = new CspParameters();  
        cp.KeyContainerName = ContainerName;  
  
        // Create a new instance of RSACryptoServiceProvider that accesses  
        // the key container.  
        RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(cp);  
  
        // Delete the key entry in the container.  
        rsa.PersistKeyInCsp = false;  
  
        // Call Clear to release resources and delete the key from the container.  
        rsa.Clear();  
  
        Console.WriteLine("Key deleted.");  
    }  
}  
```  
  
```console  
Key added to container:  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key retrieved from container :  
<RSAKeyValue> Key Information A</RSAKeyValue>  
Key deleted.  
Key added to container:  
<RSAKeyValue> Key Information B</RSAKeyValue>  
Key deleted.  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebe46-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ebe46-122">See also</span></span>

- [<span data-ttu-id="ebe46-123">Generazione di chiavi per crittografia e decrittografia</span><span class="sxs-lookup"><span data-stu-id="ebe46-123">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="ebe46-124">Crittografia di dati</span><span class="sxs-lookup"><span data-stu-id="ebe46-124">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)
- [<span data-ttu-id="ebe46-125">Decrittografia di dati</span><span class="sxs-lookup"><span data-stu-id="ebe46-125">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)
- [<span data-ttu-id="ebe46-126">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="ebe46-126">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
