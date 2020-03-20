---
title: 'Procedura: Elencare il contenuto della directory con FTP'
description: Questo articolo contiene un esempio che mostra come elencare il contenuto delle directory di un server FTP.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
ms.assetid: 130c64c9-7b7f-4672-9b3b-d946bd2616c5
ms.openlocfilehash: 924e6731ce585f127af319fdbfbdc8c12e61c46d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "61642620"
---
# <a name="how-to-list-directory-contents-with-ftp"></a><span data-ttu-id="a8d48-103">Procedura: Elencare il contenuto della directory con FTP</span><span class="sxs-lookup"><span data-stu-id="a8d48-103">How to: List directory contents with FTP</span></span>

<span data-ttu-id="a8d48-104">Questo esempio mostra come elencare il contenuto delle directory di un server FTP.</span><span class="sxs-lookup"><span data-stu-id="a8d48-104">This sample shows how to list the directory contents of an FTP server.</span></span>

## <a name="example"></a><span data-ttu-id="a8d48-105">Esempio</span><span class="sxs-lookup"><span data-stu-id="a8d48-105">Example</span></span>

```csharp
using System;
using System.IO;
using System.Net;

namespace Examples.System.Net
{
    public class WebRequestGetExample
    {
        public static void Main ()
        {
            // Get the object used to communicate with the server.
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/");
            request.Method = WebRequestMethods.Ftp.ListDirectoryDetails;

            // This example assumes the FTP site uses anonymous logon.
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");

            FtpWebResponse response = (FtpWebResponse)request.GetResponse();

            Stream responseStream = response.GetResponseStream();
            StreamReader reader = new StreamReader(responseStream);
            Console.WriteLine(reader.ReadToEnd());

            Console.WriteLine($"Directory List Complete, status {response.StatusDescription}");

            reader.Close();
            response.Close();
        }
    }
}
```

```vb
Imports System.IO
Imports System.Net

Namespace Examples.System.Net
    Public Module WebRequestGetExample
        Public Sub Main()
            ' Get the object used to communicate with the server.
            Dim request As FtpWebRequest = CType(WebRequest.Create("ftp://www.contoso.com/"), FtpWebRequest)
            request.Method = WebRequestMethods.Ftp.ListDirectoryDetails

            ' This example assumes the FTP site uses anonymous logon.
            request.Credentials = New NetworkCredential("anonymous", "janeDoe@contoso.com")

            Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)

            Dim responseStream As Stream = response.GetResponseStream()
            Dim reader As StreamReader = New StreamReader(responseStream)
            Console.WriteLine(reader.ReadToEnd())

            Console.WriteLine($"Directory List Complete, status {response.StatusDescription}")

            reader.Close()
            response.Close()
        End Sub
    End Module
End Namespace
```

<span data-ttu-id="a8d48-106">Se è necessario elencare una directory specifica, aggiungere semplicemente la directory alla fine dell'URI usato nel metodo <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="a8d48-106">If you need to list a specific directory, just add the directory to the end of the URI you're using in the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method:</span></span>

```csharp
FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/your_preferred_directory");
```

```vb
Dim request As FtpWebRequest = CType(WebRequest.Create("ftp://www.contoso.com/your_preferred_directory"), FtpWebRequest)
```
