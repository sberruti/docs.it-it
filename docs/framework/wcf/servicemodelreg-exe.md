---
title: Strumento di registrazione ServiceModel (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183098"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="f59fe-102">Strumento di registrazione ServiceModel (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="f59fe-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="f59fe-103">Questo strumento da riga di comando offre la possibilità di gestire la registrazione di componenti WCF e WF in un singolo computer.</span><span class="sxs-lookup"><span data-stu-id="f59fe-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="f59fe-104">In condizioni normali l'utilizzo di questo strumento non è consigliabile perché i componenti WCF e WF vengono configurati quando installati.</span><span class="sxs-lookup"><span data-stu-id="f59fe-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="f59fe-105">Tuttavia, se si verificano problemi con l'attivazione del servizio, si può tentare la registrazione dei componenti tramite questo strumento.</span><span class="sxs-lookup"><span data-stu-id="f59fe-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f59fe-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="f59fe-106">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="f59fe-107">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="f59fe-107">Remarks</span></span>  
 <span data-ttu-id="f59fe-108">Lo strumento si trova nel percorso seguente:</span><span class="sxs-lookup"><span data-stu-id="f59fe-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="f59fe-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f59fe-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="f59fe-110">Quando lo strumento di registrazione ServiceModel viene eseguito in Windows Vista, la finestra di dialogo **Funzionalità Windows** potrebbe non riflettere l'opzione **attivazione HTTP di Windows Communication Foundation** in Microsoft **.NET Framework 3.0** è attivata.</span><span class="sxs-lookup"><span data-stu-id="f59fe-110">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="f59fe-111">È possibile accedere alla finestra di dialogo **Funzionalità Windows** facendo clic sul **pulsante Start**, quindi scegliere **Esegui** e digitando **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="f59fe-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="f59fe-112">Nella tabella riportata di seguito sono descritte le opzioni che possono essere utilizzate con ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="f59fe-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="f59fe-113">Opzione</span><span class="sxs-lookup"><span data-stu-id="f59fe-113">Option</span></span>|<span data-ttu-id="f59fe-114">Descrizione</span><span class="sxs-lookup"><span data-stu-id="f59fe-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="f59fe-115">Installa tutti i componenti WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="f59fe-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="f59fe-116">Disinstalla tutti i componenti WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="f59fe-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="f59fe-117">Ripristina tutti i componenti WCF e WF.</span><span class="sxs-lookup"><span data-stu-id="f59fe-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="f59fe-118">Installa tutti i componenti WCF e WF specificati con -c.</span><span class="sxs-lookup"><span data-stu-id="f59fe-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="f59fe-119">Disinstalla tutti i componenti WCF e WF specificati con -c.</span><span class="sxs-lookup"><span data-stu-id="f59fe-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="f59fe-120">Installa o disinstalla un componente:</span><span class="sxs-lookup"><span data-stu-id="f59fe-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="f59fe-121">- httpnamespace – Prenotazione spazio dei nomi HTTP</span><span class="sxs-lookup"><span data-stu-id="f59fe-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="f59fe-122">- tcpportsharing – Servizio di condivisione porta TCP</span><span class="sxs-lookup"><span data-stu-id="f59fe-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="f59fe-123">- tcpactivation – Servizio di attivazione TCP (non supportato in .NET 4 Client Profile)</span><span class="sxs-lookup"><span data-stu-id="f59fe-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="f59fe-124">- namedpipeactivation : servizio di attivazione named pipe (non supportato in .NET 4 Client Profile</span><span class="sxs-lookup"><span data-stu-id="f59fe-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="f59fe-125">- msmqactivation – Servizio di attivazione MSMQ (non supportato in .NET 4 Client Profile</span><span class="sxs-lookup"><span data-stu-id="f59fe-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="f59fe-126">- etw – manifesti di traccia eventi ETW (Windows Vista o versioni successive)</span><span class="sxs-lookup"><span data-stu-id="f59fe-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="f59fe-127">Modalità non interattiva (solo registrazione errori visualizzata)</span><span class="sxs-lookup"><span data-stu-id="f59fe-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="f59fe-128">Modalità dettagliata.</span><span class="sxs-lookup"><span data-stu-id="f59fe-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="f59fe-129">Elimina le informazioni di copyright e il messaggio di avvio.</span><span class="sxs-lookup"><span data-stu-id="f59fe-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="f59fe-130">Visualizza il testo della Guida</span><span class="sxs-lookup"><span data-stu-id="f59fe-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="f59fe-131">Correzione dell’errore FileLoadException </span><span class="sxs-lookup"><span data-stu-id="f59fe-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="f59fe-132">Se nel computer sono state installate versioni `FileLoadFoundException` precedenti di WCF, è possibile che venga visualizzato un errore quando si esegue lo strumento ServiceModelReg per registrare una nuova installazione.</span><span class="sxs-lookup"><span data-stu-id="f59fe-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="f59fe-133">Ciò può verificarsi anche se sono stati rimossi manualmente file dall’installazione precedente, ma sono state mantenute intatte le impostazioni machine.config.</span><span class="sxs-lookup"><span data-stu-id="f59fe-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="f59fe-134">Verrà visualizzato un messaggio di errore simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="f59fe-134">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="f59fe-135">È necessario notare dal messaggio di errore che è stato installato l’assembly System.ServiceModel Versione 2.0.0.0 di una precedente versione di Customer Technology Preview (CTP).</span><span class="sxs-lookup"><span data-stu-id="f59fe-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="f59fe-136">La versione corrente dell'assembly System.ServiceModel rilasciata è invece 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="f59fe-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="f59fe-137">Pertanto, questo problema si verifica quando si desidera installare la versione ufficiale di WCF in un computer in cui è stata installata una versione precedente CTP di WCF, ma non completamente disinstallato.</span><span class="sxs-lookup"><span data-stu-id="f59fe-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="f59fe-138">ServiceModelReg.exe non può eseguire la pulizia di voci della versione precedente, né può registrare voci della versione nuova.</span><span class="sxs-lookup"><span data-stu-id="f59fe-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="f59fe-139">L'unica soluzione consiste nel modificare manualmente machine.config. È possibile individuare questo file nel percorso seguente.</span><span class="sxs-lookup"><span data-stu-id="f59fe-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="f59fe-140">Se si esegue WCF in un computer a 64 bit, è necessario modificare anche lo stesso file in questa posizione.</span><span class="sxs-lookup"><span data-stu-id="f59fe-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="f59fe-141">Individuare tutti i nodi XML in questo file che fanno riferimento a "System.ServiceModel, Version .</span><span class="sxs-lookup"><span data-stu-id="f59fe-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="f59fe-142">Per risolvere il problema, salvare il file e ripetere l'esecuzione di ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="f59fe-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f59fe-143">Esempi</span><span class="sxs-lookup"><span data-stu-id="f59fe-143">Examples</span></span>  
 <span data-ttu-id="f59fe-144">Negli esempi seguenti viene illustrato come utilizzare le opzioni più comuni dello strumento ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="f59fe-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
