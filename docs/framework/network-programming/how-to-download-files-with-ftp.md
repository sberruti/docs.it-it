---
title: 'Procedura: Scaricare file con FTP'
description: Questo articolo contiene un esempio che illustra come scaricare un file da un server FTP.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
ms.assetid: 892548b8-954a-4f6a-9bca-2ae620c3700f
ms.openlocfilehash: a0941d42de71029be9aab2fdbc69f8434fb73e2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "65632978"
---
# <a name="how-to-download-files-with-ftp"></a><span data-ttu-id="2b3d2-103">Procedura: Scaricare file con FTP</span><span class="sxs-lookup"><span data-stu-id="2b3d2-103">How to: Download files with FTP</span></span>

<span data-ttu-id="2b3d2-104">Questo esempio illustra come scaricare un file da un server FTP.</span><span class="sxs-lookup"><span data-stu-id="2b3d2-104">This sample shows how to download a file from an FTP server.</span></span>

## <a name="example"></a><span data-ttu-id="2b3d2-105">Esempio</span><span class="sxs-lookup"><span data-stu-id="2b3d2-105">Example</span></span>

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
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/test.htm");
            request.Method = WebRequestMethods.Ftp.DownloadFile;

            // This example assumes the FTP site uses anonymous logon.
            request.Credentials = new NetworkCredential("anonymous","janeDoe@contoso.com");

            FtpWebResponse response = (FtpWebResponse)request.GetResponse();

            Stream responseStream = response.GetResponseStream();
            StreamReader reader = new StreamReader(responseStream);
            Console.WriteLine(reader.ReadToEnd());

            Console.WriteLine($"Download Complete, status {response.StatusDescription}");

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
            Dim request As FtpWebRequest = CType(WebRequest.Create("ftp://www.contoso.com/test.htm"), FtpWebRequest)
            request.Method = WebRequestMethods.Ftp.DownloadFile

            ' This example assumes the FTP site uses anonymous logon.
            request.Credentials = New NetworkCredential("anonymous", "janeDoe@contoso.com")

            Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)

            Dim responseStream As Stream = response.GetResponseStream()
            Dim reader As StreamReader = New StreamReader(responseStream)
            Console.WriteLine(reader.ReadToEnd())

            Console.WriteLine($"Download Complete, status {response.StatusDescription}")

            reader.Close()
            response.Close()
        End Sub
    End Module
End Namespace
```
