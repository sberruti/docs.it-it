---
title: MDA bindingFailure
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
ms.openlocfilehash: e3a9a915d25cbe5f052f039055167cf3ae4bf424
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216923"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="bf571-102">MDA bindingFailure</span><span class="sxs-lookup"><span data-stu-id="bf571-102">bindingFailure MDA</span></span>

<span data-ttu-id="bf571-103">L'assistente al debug gestito `bindingFailure` viene attivato quando si verifica un errore nel caricamento di un assembly.</span><span class="sxs-lookup"><span data-stu-id="bf571-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>

## <a name="symptoms"></a><span data-ttu-id="bf571-104">Sintomi</span><span class="sxs-lookup"><span data-stu-id="bf571-104">Symptoms</span></span>

<span data-ttu-id="bf571-105">Il codice ha tentato di caricare un assembly usando un riferimento statico o uno dei metodi loader, ad esempio <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> o <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bf571-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bf571-106">L'assembly non viene caricato e viene generata un'eccezione <xref:System.IO.FileNotFoundException> o <xref:System.IO.FileLoadException>.</span><span class="sxs-lookup"><span data-stu-id="bf571-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>

## <a name="cause"></a><span data-ttu-id="bf571-107">Causa</span><span class="sxs-lookup"><span data-stu-id="bf571-107">Cause</span></span>

<span data-ttu-id="bf571-108">Quando il runtime non è in grado di caricare un assembly, si verifica un errore di binding,</span><span class="sxs-lookup"><span data-stu-id="bf571-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="bf571-109">che può essere il risultato di una delle situazioni descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="bf571-109">A binding failure might be the result of one of the following situations:</span></span>

- <span data-ttu-id="bf571-110">Common Language Runtime (CLR) non è in grado di trovare l'assembly richiesto.</span><span class="sxs-lookup"><span data-stu-id="bf571-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="bf571-111">I motivi, in questo caso, possono essere diversi: è possibile, ad esempio, che l'assembly non sia stata installata o che l'applicazione non sia stata correttamente configurata per trovare l'assembly.</span><span class="sxs-lookup"><span data-stu-id="bf571-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>

- <span data-ttu-id="bf571-112">Uno scenario comune relativo a questo problema è il passaggio di un tipo a un altro dominio applicazione, in cui viene richiesto a CLR di caricare l'assembly contenente il tipo nell'altro dominio applicazione.</span><span class="sxs-lookup"><span data-stu-id="bf571-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="bf571-113">Se questo è configurato diversamente dal dominio applicazione originale, è possibile che il runtime non riesca a caricare l'assembly.</span><span class="sxs-lookup"><span data-stu-id="bf571-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="bf571-114">È possibile, ad esempio, che i due domini applicazione abbiano valori diversi per la proprietà <xref:System.AppDomain.BaseDirectory%2A>.</span><span class="sxs-lookup"><span data-stu-id="bf571-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>

- <span data-ttu-id="bf571-115">L'assembly richiesto è danneggiato o non è un assembly.</span><span class="sxs-lookup"><span data-stu-id="bf571-115">The requested assembly is corrupted or is not an assembly.</span></span>

- <span data-ttu-id="bf571-116">Il codice con cui si tenta di caricare l'assembly non ha le autorizzazioni di sicurezza dell'accesso al codice necessarie per caricare assembly.</span><span class="sxs-lookup"><span data-stu-id="bf571-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>

- <span data-ttu-id="bf571-117">Nelle credenziali utente non sono infatti incluse le autorizzazioni necessarie per la lettura del file.</span><span class="sxs-lookup"><span data-stu-id="bf571-117">The user credentials do not provide the required permissions to read the file.</span></span>

## <a name="resolution"></a><span data-ttu-id="bf571-118">Risoluzione</span><span class="sxs-lookup"><span data-stu-id="bf571-118">Resolution</span></span>

<span data-ttu-id="bf571-119">La prima cosa da fare è determinare il motivo per cui CLR non è stato in grado di eseguire il binding all'assembly richiesto.</span><span class="sxs-lookup"><span data-stu-id="bf571-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="bf571-120">Possono essere molti i motivi per cui il runtime non è riuscito a trovare o a caricare l'assembly richiesto, come illustrato negli scenari elencati nella sezione Causa.</span><span class="sxs-lookup"><span data-stu-id="bf571-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="bf571-121">Per eliminare la causa dell'errore di binding, sono consigliate le azioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="bf571-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>

- <span data-ttu-id="bf571-122">Determinare la causa usando i dati forniti dall'assistente al debug gestito `bindingFailure`:</span><span class="sxs-lookup"><span data-stu-id="bf571-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>

  - <span data-ttu-id="bf571-123">Eseguire [Fuslogvw.exe (Visualizzatore log binding assembly)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) per leggere i log degli errori prodotti dal binder di assembly.</span><span class="sxs-lookup"><span data-stu-id="bf571-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>

  - <span data-ttu-id="bf571-124">Determinare se l'assembly si trova nella posizione richiesta.</span><span class="sxs-lookup"><span data-stu-id="bf571-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="bf571-125">Nel caso dei metodi <xref:System.Reflection.Assembly.LoadFrom%2A> e <xref:System.Reflection.Assembly.LoadFile%2A>, la posizione richiesta può essere determinata facilmente.</span><span class="sxs-lookup"><span data-stu-id="bf571-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="bf571-126">Nel caso del metodo <xref:System.Reflection.Assembly.Load%2A>, che esegue il binding usando l'identità dell'assembly, è necessario cercare gli assembly corrispondenti all'identità specificata nella Global Assembly Cache e nel percorso di analisi della proprietà <xref:System.AppDomain.BaseDirectory%2A> del dominio applicazione.</span><span class="sxs-lookup"><span data-stu-id="bf571-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>

- <span data-ttu-id="bf571-127">Risolvere la causa in base ai risultati del passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="bf571-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="bf571-128">Di seguito sono elencate le possibili opzioni di risoluzione:</span><span class="sxs-lookup"><span data-stu-id="bf571-128">Possible resolution options are the following:</span></span>

  - <span data-ttu-id="bf571-129">Installare l'assembly richiesto nella Global Assembly Cache e chiamare il metodo</span><span class="sxs-lookup"><span data-stu-id="bf571-129">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="bf571-130"><xref:System.Reflection.Assembly.Load%2A> per caricare l'assembly in base all'identità.</span><span class="sxs-lookup"><span data-stu-id="bf571-130"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="bf571-131">Copiare l'assembly richiesto nella directory dell'applicazione e chiamare il metodo <xref:System.Reflection.Assembly.Load%2A> per caricare l'assembly in base all'identità.</span><span class="sxs-lookup"><span data-stu-id="bf571-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="bf571-132">Riconfigurare il dominio applicazione in cui si è verificato l'errore di binding per includere il percorso dell'assembly modificando la proprietà <xref:System.AppDomain.BaseDirectory%2A> o aggiungendo percorsi di analisi privati.</span><span class="sxs-lookup"><span data-stu-id="bf571-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>

  - <span data-ttu-id="bf571-133">Modificare l'elenco di controllo di accesso per il file in modo da consentirne la lettura all'utente connesso.</span><span class="sxs-lookup"><span data-stu-id="bf571-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="bf571-134">Effetto sull'ambiente di esecuzione</span><span class="sxs-lookup"><span data-stu-id="bf571-134">Effect on the Runtime</span></span>

<span data-ttu-id="bf571-135">L'assistente al debug gestito non ha alcun effetto su CLR.</span><span class="sxs-lookup"><span data-stu-id="bf571-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="bf571-136">Si limita a generare un report dei dati relativi agli errori di binding.</span><span class="sxs-lookup"><span data-stu-id="bf571-136">It only reports data about binding failures.</span></span>

## <a name="output"></a><span data-ttu-id="bf571-137">Output</span><span class="sxs-lookup"><span data-stu-id="bf571-137">Output</span></span>

<span data-ttu-id="bf571-138">L'assistente al debug gestito segnala l'assembly in cui si è verificato l'errore di caricamento, inclusi il percorso richiesto e/o il nome visualizzato, il contesto di binding, il dominio applicazione in cui è stato richiesto il caricamento e il motivo dell'errore.</span><span class="sxs-lookup"><span data-stu-id="bf571-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>

<span data-ttu-id="bf571-139">È possibile che, se non è disponibile in CLR, il nome visualizzato o il percorso richiesto non sia definito.</span><span class="sxs-lookup"><span data-stu-id="bf571-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="bf571-140">Se la chiamata non riuscita faceva riferimento al metodo <xref:System.Reflection.Assembly.Load%2A>, è probabile che il runtime non sia stato in grado di determinare il nome visualizzato dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="bf571-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>

## <a name="configuration"></a><span data-ttu-id="bf571-141">Configurazione</span><span class="sxs-lookup"><span data-stu-id="bf571-141">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="bf571-142">Esempio</span><span class="sxs-lookup"><span data-stu-id="bf571-142">Example</span></span>

<span data-ttu-id="bf571-143">L'esempio di codice seguente mostra una situazione che può comportare l'attivazione dell'assistente al debug gestito:</span><span class="sxs-lookup"><span data-stu-id="bf571-143">The following code example demonstrates a situation that can activate this MDA:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.Reflection;
namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            // This call attempts to load a nonexistent assembly.
            // The call will throw a System.IO.FileNotFound exception
            // and cause the activation of the bindingFailure MDA
            // if it is registered.
            Assembly.Load("NonExistentAssembly");
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="bf571-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bf571-144">See also</span></span>

- [<span data-ttu-id="bf571-145">Diagnostica degli errori tramite gli assistenti al debug gestito</span><span class="sxs-lookup"><span data-stu-id="bf571-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
