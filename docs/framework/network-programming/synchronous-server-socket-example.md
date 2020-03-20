---
title: Esempio di socket server sincrono
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronous server sockets
- sockets, code examples
- sockets, synchronous server sockets
ms.assetid: 5916c764-879f-4716-99fb-1d21c6237f1c
ms.openlocfilehash: e8924051a7087ac26793722457f934e58a75f23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180656"
---
# <a name="synchronous-server-socket-example"></a><span data-ttu-id="772f8-102">Esempio di socket server sincrono</span><span class="sxs-lookup"><span data-stu-id="772f8-102">Synchronous Server Socket Example</span></span>
<span data-ttu-id="772f8-103">Il programma di esempio seguente crea un server che riceve le richieste di connessione dai client.</span><span class="sxs-lookup"><span data-stu-id="772f8-103">The following example program creates a server that receives connection requests from clients.</span></span> <span data-ttu-id="772f8-104">Il server viene compilato con un socket sincrono, quindi l'esecuzione dell'applicazione server viene sospesa durante l'attesa di una connessione da un client.</span><span class="sxs-lookup"><span data-stu-id="772f8-104">The server is built with a synchronous socket, so execution of the server application is suspended while it waits for a connection from a client.</span></span> <span data-ttu-id="772f8-105">L'applicazione riceve una stringa dal client, visualizza la stringa nella console e quindi la restituisce al client.</span><span class="sxs-lookup"><span data-stu-id="772f8-105">The application receives a string from the client, displays the string on the console, and then echoes the string back to the client.</span></span> <span data-ttu-id="772f8-106">La stringa del client deve contenere la stringa "\<EOF>" per segnalare la fine del messaggio.</span><span class="sxs-lookup"><span data-stu-id="772f8-106">The string from the client must contain the string "\<EOF>" to signal the end of the message.</span></span>  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
Imports Microsoft.VisualBasic  
  
Public Class SynchronousSocketListener  
  
    ' Incoming data from the client.  
    Public Shared data As String = Nothing  
  
    Public Shared Sub Main()  
        ' Data buffer for incoming data.  
        Dim bytes() As Byte = New [Byte](1024) {}  
  
        ' Establish the local endpoint for the socket.  
        ' Dns.GetHostName returns the name of the
        ' host running the application.  
        Dim ipHostInfo As IPHostEntry = Dns.GetHostEntry(Dns.GetHostName())  
        Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
        Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
  
        ' Create a TCP/IP socket.  
        Dim listener As New Socket(ipAddress.AddressFamily, _  
            SocketType.Stream, ProtocolType.Tcp)  
  
        ' Bind the socket to the local endpoint and
        ' listen for incoming connections.  
  
        listener.Bind(localEndPoint)  
        listener.Listen(10)  
  
        ' Start listening for connections.  
        While True  
            Console.WriteLine("Waiting for a connection...")  
            ' Program is suspended while waiting for an incoming connection.  
            Dim handler As Socket = listener.Accept()  
            data = Nothing  
  
            ' An incoming connection needs to be processed.  
            While True  
                Dim bytesRec As Integer = handler.Receive(bytes)  
                data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
                If data.IndexOf("<EOF>") > -1 Then  
                    Exit While  
                End If  
            End While  
            ' Show the data on the console.  
            Console.WriteLine("Text received : {0}", data)  
            ' Echo the data back to the client.  
            Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
            handler.Send(msg)  
            handler.Shutdown(SocketShutdown.Both)  
            handler.Close()  
        End While  
    End Sub  
  
End Class 'SynchronousSocketListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class SynchronousSocketListener {  
  
    // Incoming data from the client.  
    public static string data = null;  
  
    public static void StartListening() {  
        // Data buffer for incoming data.  
        byte[] bytes = new Byte[1024];  
  
        // Establish the local endpoint for the socket.  
        // Dns.GetHostName returns the name of the
        // host running the application.  
        IPHostEntry ipHostInfo = Dns.GetHostEntry(Dns.GetHostName());  
        IPAddress ipAddress = ipHostInfo.AddressList[0];  
        IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
  
        // Create a TCP/IP socket.  
        Socket listener = new Socket(ipAddress.AddressFamily,  
            SocketType.Stream, ProtocolType.Tcp );  
  
        // Bind the socket to the local endpoint and
        // listen for incoming connections.  
        try {  
            listener.Bind(localEndPoint);  
            listener.Listen(10);  
  
            // Start listening for connections.  
            while (true) {  
                Console.WriteLine("Waiting for a connection...");  
                // Program is suspended while waiting for an incoming connection.  
                Socket handler = listener.Accept();  
                data = null;  
  
                // An incoming connection needs to be processed.  
                while (true) {  
                    int bytesRec = handler.Receive(bytes);  
                    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
                    if (data.IndexOf("<EOF>") > -1) {  
                        break;  
                    }  
                }  
  
                // Show the data on the console.  
                Console.WriteLine( "Text received : {0}", data);  
  
                // Echo the data back to the client.  
                byte[] msg = Encoding.ASCII.GetBytes(data);  
  
                handler.Send(msg);  
                handler.Shutdown(SocketShutdown.Both);  
                handler.Close();  
            }  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        Console.WriteLine("\nPress ENTER to continue...");  
        Console.Read();  
  
    }  
  
    public static int Main(String[] args) {  
        StartListening();  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="772f8-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="772f8-107">See also</span></span>

- [<span data-ttu-id="772f8-108">Esempio di socket client sincrono</span><span class="sxs-lookup"><span data-stu-id="772f8-108">Synchronous Client Socket Example</span></span>](synchronous-client-socket-example.md)
- [<span data-ttu-id="772f8-109">Uso di un socket server sincrono</span><span class="sxs-lookup"><span data-stu-id="772f8-109">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="772f8-110">Esempi di codice socket</span><span class="sxs-lookup"><span data-stu-id="772f8-110">Socket Code Examples</span></span>](socket-code-examples.md)
