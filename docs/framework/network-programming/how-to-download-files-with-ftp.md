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
# <a name="how-to-download-files-with-ftp"></a>Procedura: Scaricare file con FTP

Questo esempio illustra come scaricare un file da un server FTP.

## <a name="example"></a>Esempio

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
