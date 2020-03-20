---
title: TCP-UDP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
ms.openlocfilehash: d35278ab7feb42453b5a0adbc86c47b7ac3ff5ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047105"
---
# <a name="tcp-udp"></a><span data-ttu-id="20ddc-102">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="20ddc-102">TCP-UDP</span></span>
<span data-ttu-id="20ddc-103">Le applicazioni possono usare servizi TCP (Transmission Control Protocol) e UDP (User Datagram Protocol) con le classi <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener> e <xref:System.Net.Sockets.UdpClient>.</span><span class="sxs-lookup"><span data-stu-id="20ddc-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="20ddc-104">Queste classi protocollo sono basate sulla classe <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> e possono gestire i dettagli del trasferimento dei dati.</span><span class="sxs-lookup"><span data-stu-id="20ddc-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="20ddc-105">Le classi protocollo usano i metodi sincroni della classe **Socket** per fornire un accesso semplice e diretto ai servizi di rete senza il sovraccarico di gestione delle informazioni sullo stato o senza conoscere i dettagli di configurazione per socket specifici del protocollo.</span><span class="sxs-lookup"><span data-stu-id="20ddc-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="20ddc-106">Per usare i metodi **Socket** asincroni, è possibile usare i metodi asincroni forniti dalla classe <xref:System.Net.Sockets.NetworkStream>.</span><span class="sxs-lookup"><span data-stu-id="20ddc-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="20ddc-107">Per accedere alle funzionalità della classe **Socket** non esposte dalle classi protocollo, è necessario usare la classe **Socket**.</span><span class="sxs-lookup"><span data-stu-id="20ddc-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="20ddc-108">**TcpClient** e **TcpListener** rappresentano la rete tramite la classe **NetworkStream**.</span><span class="sxs-lookup"><span data-stu-id="20ddc-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="20ddc-109">Si usa il metodo <xref:System.Net.Sockets.TcpClient.GetStream%2A> per restituire il flusso di rete e quindi si chiamano i metodi <xref:System.Net.Sockets.NetworkStream.Read%2A> e <xref:System.Net.Sockets.NetworkStream.Write%2A> del flusso.</span><span class="sxs-lookup"><span data-stu-id="20ddc-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="20ddc-110">Il socket sottostante delle classi protocollo non è di proprietà di **NetworkStream**, quindi la sua chiusura non influisce sul socket.</span><span class="sxs-lookup"><span data-stu-id="20ddc-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="20ddc-111">La classe **UdpClient** usa una matrice di byte per contenere il datagramma UDP.</span><span class="sxs-lookup"><span data-stu-id="20ddc-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="20ddc-112">Si usa il metodo <xref:System.Net.Sockets.UdpClient.Send%2A> per inviare i dati alla rete e il metodo <xref:System.Net.Sockets.UdpClient.Receive%2A> per ricevere un datagramma in ingresso.</span><span class="sxs-lookup"><span data-stu-id="20ddc-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ddc-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="20ddc-113">See also</span></span>

- [<span data-ttu-id="20ddc-114">Uso dei servizi TCP</span><span class="sxs-lookup"><span data-stu-id="20ddc-114">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="20ddc-115">Uso dei servizi UDP</span><span class="sxs-lookup"><span data-stu-id="20ddc-115">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="20ddc-116">Uso di flussi nella rete</span><span class="sxs-lookup"><span data-stu-id="20ddc-116">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="20ddc-117">Uso di un socket server asincrono</span><span class="sxs-lookup"><span data-stu-id="20ddc-117">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="20ddc-118">Uso di un socket client asincrono</span><span class="sxs-lookup"><span data-stu-id="20ddc-118">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="20ddc-119">Uso di protocolli applicativi</span><span class="sxs-lookup"><span data-stu-id="20ddc-119">Using Application Protocols</span></span>](using-application-protocols.md)
