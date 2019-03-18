---
title: Convertire un'app Windows Forms in .NET Core 3.0
description: Illustra come convertire un'applicazione Windows Forms .NET Framework in .NET Core 3.0 per Windows.
author: Thraka
ms.date: 03/01/2019
ms.custom: ''
ms.openlocfilehash: 89540ebbed834f41ce9d84c32e69e6f5e1ab0a21
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2019
ms.locfileid: "57681496"
---
# <a name="how-to-port-a-windows-forms-desktop-app-to-net-core"></a><span data-ttu-id="2b37c-103">Procedura: Convertire un'app desktop Windows Forms in .NET Core</span><span class="sxs-lookup"><span data-stu-id="2b37c-103">How to: Port a Windows Forms desktop app to .NET Core</span></span>

<span data-ttu-id="2b37c-104">Questo articolo descrive come convertire un'app desktop basata su Windows Forms da .NET Framework a .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2b37c-104">This article describes how to port your Windows Forms-based desktop app from .NET Framework to .NET Core 3.0.</span></span> <span data-ttu-id="2b37c-105">.NET Core SDK 3.0 include il supporto per le applicazioni Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2b37c-105">The .NET Core 3.0 SDK includes support for Windows Forms applications.</span></span> <span data-ttu-id="2b37c-106">Windows Forms è ancora un framework solo per Windows e supporta l'esecuzione solo in Windows.</span><span class="sxs-lookup"><span data-stu-id="2b37c-106">Windows Forms is still a Windows-only framework and only runs on Windows.</span></span> <span data-ttu-id="2b37c-107">Questo esempio usa l'interfaccia della riga di comando di .NET Core SDK per creare e gestire il progetto.</span><span class="sxs-lookup"><span data-stu-id="2b37c-107">This example uses the .NET Core SDK CLI to create and manage your project.</span></span>

<span data-ttu-id="2b37c-108">In questo articolo vengono usati vari nomi per identificare i tipi di file usati per la migrazione.</span><span class="sxs-lookup"><span data-stu-id="2b37c-108">In this article, various names are used to identify types of files used for migration.</span></span> <span data-ttu-id="2b37c-109">Durante la migrazione del progetto personale i file verranno denominati in modo diverso, pertanto abbinarli mentalmente a quelli elencati di seguito:</span><span class="sxs-lookup"><span data-stu-id="2b37c-109">When migrating your project, your files will be named differently, so mentally match them to the ones listed below:</span></span>

| <span data-ttu-id="2b37c-110">File</span><span class="sxs-lookup"><span data-stu-id="2b37c-110">File</span></span> | <span data-ttu-id="2b37c-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2b37c-111">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="2b37c-112">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="2b37c-112">**MyApps.sln**</span></span> | <span data-ttu-id="2b37c-113">Nome del file di soluzione.</span><span class="sxs-lookup"><span data-stu-id="2b37c-113">The name of the solution file.</span></span> |
| <span data-ttu-id="2b37c-114">**MyForms.csproj**</span><span class="sxs-lookup"><span data-stu-id="2b37c-114">**MyForms.csproj**</span></span> | <span data-ttu-id="2b37c-115">Nome del progetto Windows Forms di .NET Framework da convertire.</span><span class="sxs-lookup"><span data-stu-id="2b37c-115">The name of the .NET Framework Windows Forms project to port.</span></span> |
| <span data-ttu-id="2b37c-116">**MyFormsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="2b37c-116">**MyFormsCore.csproj**</span></span> | <span data-ttu-id="2b37c-117">Nome del nuovo progetto .NET Core creato.</span><span class="sxs-lookup"><span data-stu-id="2b37c-117">The name of the new .NET Core project you create.</span></span> |
| <span data-ttu-id="2b37c-118">**MyAppCore.exe**</span><span class="sxs-lookup"><span data-stu-id="2b37c-118">**MyAppCore.exe**</span></span> | <span data-ttu-id="2b37c-119">Eseguibile dell'app Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b37c-119">The .NET Core Windows Forms app executable.</span></span> |

## <a name="prerequisites"></a><span data-ttu-id="2b37c-120">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="2b37c-120">Prerequisites</span></span>

- <span data-ttu-id="2b37c-121">[Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=winforms+core) per tutte le operazioni di progettazione che si vogliono eseguire.</span><span class="sxs-lookup"><span data-stu-id="2b37c-121">[Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=winforms+core) for any designer work you want to do.</span></span>

  <span data-ttu-id="2b37c-122">Installare i carichi di lavoro di Visual Studio seguenti:</span><span class="sxs-lookup"><span data-stu-id="2b37c-122">Install the following Visual Studio workloads:</span></span>
  - <span data-ttu-id="2b37c-123">Sviluppo per desktop .NET</span><span class="sxs-lookup"><span data-stu-id="2b37c-123">.NET desktop development</span></span>
  - <span data-ttu-id="2b37c-124">Sviluppo multipiattaforma .NET Core</span><span class="sxs-lookup"><span data-stu-id="2b37c-124">.NET cross-platform development</span></span>

- <span data-ttu-id="2b37c-125">Un progetto Windows Forms funzionante in una soluzione che viene compilata ed eseguita senza problemi.</span><span class="sxs-lookup"><span data-stu-id="2b37c-125">A working Windows Forms project in a solution that builds and runs without issue.</span></span>
- <span data-ttu-id="2b37c-126">Il progetto deve essere codificato in C#.</span><span class="sxs-lookup"><span data-stu-id="2b37c-126">Your project must be coded in C#.</span></span> 
- <span data-ttu-id="2b37c-127">Installare l'anteprima più recente di [.NET Core 3.0](https://aka.ms/netcore3download).</span><span class="sxs-lookup"><span data-stu-id="2b37c-127">Install the latest [.NET Core 3.0](https://aka.ms/netcore3download) preview.</span></span>


>[!NOTE]
><span data-ttu-id="2b37c-128">**Visual Studio 2017** non supporta progetti .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2b37c-128">**Visual Studio 2017** doesn't support .NET Core 3.0 projects.</span></span> <span data-ttu-id="2b37c-129">**Visual Studio 2019 Preview/RC** supporta i progetti .NET Core 3.0, ma non supporta ancora la finestra di progettazione visiva per i progetti Windows Forms .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2b37c-129">**Visual Studio 2019 Preview/RC** supports .NET Core 3.0 projects but doesn't yet support the visual designer for .NET Core 3.0 Windows Forms projects.</span></span> <span data-ttu-id="2b37c-130">Per usare la finestra di progettazione visiva, è necessario avere un progetto Windows Forms .NET nella soluzione che condivide i file di modulo con il progetto .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b37c-130">To use the visual designer, you must have a .NET Windows Forms project in your solution that shares the forms files with the .NET Core project.</span></span>

### <a name="consider"></a><span data-ttu-id="2b37c-131">Consider</span><span class="sxs-lookup"><span data-stu-id="2b37c-131">Consider</span></span>

<span data-ttu-id="2b37c-132">Per la conversione di un'applicazione Windows Forms di .NET Framework, esistono alcuni aspetti da considerare.</span><span class="sxs-lookup"><span data-stu-id="2b37c-132">When porting a .NET Framework Windows Forms application, there are a few things you must consider.</span></span>

01. <span data-ttu-id="2b37c-133">Controllare che l'applicazione sia un buon candidato per la migrazione.</span><span class="sxs-lookup"><span data-stu-id="2b37c-133">Check that your application is a good candidate for migration.</span></span>

    <span data-ttu-id="2b37c-134">Usare [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) per determinare se sarà possibile eseguire la migrazione del progetto a .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2b37c-134">Use the [.NET Portability Analyzer](../../standard/analyzers/portability-analyzer.md) to determine if your project will migrate to .NET Core 3.0.</span></span> <span data-ttu-id="2b37c-135">Se il progetto presenta problemi con .NET Core 3.0, l'analizzatore consente di identificarli.</span><span class="sxs-lookup"><span data-stu-id="2b37c-135">If your project has issues with .NET Core 3.0, the analyzer helps you identify those problems.</span></span>

01. <span data-ttu-id="2b37c-136">Si usa una versione diversa di Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2b37c-136">You're using a different version of Windows Forms.</span></span>

    <span data-ttu-id="2b37c-137">In concomitanza con il rilascio di .NET Core 3.0 Preview 1, Windows Forms è stato reso disponibile come open source su GitHub.</span><span class="sxs-lookup"><span data-stu-id="2b37c-137">When .NET Core 3.0 Preview 1 was released, Windows Forms went open-source on GitHub.</span></span> <span data-ttu-id="2b37c-138">Il codice per .NET Core Windows Forms è un fork della base di codice di .NET Framework Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2b37c-138">The code for .NET Core Windows Forms is a fork of the .NET Framework Windows Forms code base.</span></span> <span data-ttu-id="2b37c-139">È possibile che esistano alcune differenze che non consentono la conversione dell'app.</span><span class="sxs-lookup"><span data-stu-id="2b37c-139">It's possible some differences exist and your app won't port.</span></span>

01. <span data-ttu-id="2b37c-140">[Windows Compatibility Pack][compat-pack] può essere utile per la migrazione.</span><span class="sxs-lookup"><span data-stu-id="2b37c-140">The [Windows Compatibility Pack][compat-pack] may help you migrate.</span></span>

    <span data-ttu-id="2b37c-141">Alcune API che sono disponibili in .NET Framework non sono disponibili in .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="2b37c-141">Some APIs that are available in .NET Framework aren't available in .NET Core 3.0.</span></span> <span data-ttu-id="2b37c-142">[Windows Compatibility Pack][compat-pack] aggiunge molte di queste API e può essere utile per rendere l'app Windows Forms compatibile con .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b37c-142">The [Windows Compatibility Pack][compat-pack] adds many of these APIs and may help your Windows Forms app become compatible with .NET Core.</span></span>

01. <span data-ttu-id="2b37c-143">Aggiornare i pacchetti NuGet usati dal progetto.</span><span class="sxs-lookup"><span data-stu-id="2b37c-143">Update the NuGet packages used by your project.</span></span>

    <span data-ttu-id="2b37c-144">È sempre consigliabile usare le versioni più recenti dei pacchetti NuGet prima di qualsiasi migrazione.</span><span class="sxs-lookup"><span data-stu-id="2b37c-144">It's always a good practice to use the latest versions of NuGet packages before any migration.</span></span> <span data-ttu-id="2b37c-145">Se l'applicazione fa riferimento a pacchetti NuGet, aggiornarli alla versione più recente.</span><span class="sxs-lookup"><span data-stu-id="2b37c-145">If your application is referencing any NuGet packages, update them to the latest version.</span></span> <span data-ttu-id="2b37c-146">Verificare che l'applicazione venga compilata correttamente.</span><span class="sxs-lookup"><span data-stu-id="2b37c-146">Ensure your application builds successfully.</span></span> <span data-ttu-id="2b37c-147">Dopo l'aggiornamento, se sono presenti errori di pacchetto, effettuare il downgrade del pacchetto alla versione più recente che non causa problemi al codice.</span><span class="sxs-lookup"><span data-stu-id="2b37c-147">After upgrading, if there are any package errors, downgrade the package to the latest version that doesn't break your code.</span></span>

01. <span data-ttu-id="2b37c-148">Visual Studio 2019 Preview/RC non supporta ancora la finestra di progettazione dei moduli per .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2b37c-148">Visual Studio 2019 Preview/RC doesn't yet support the Forms Designer for .NET Core 3.0</span></span>

    <span data-ttu-id="2b37c-149">Attualmente, è necessario mantenere il file di progetto .NET Framework Windows Forms esistente se si vuole usare la finestra di progettazione dei moduli da Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2b37c-149">Currently, you need to keep your existing .NET Framework Windows Forms project file if you want to use the Forms Designer from Visual Studio.</span></span>

## <a name="create-a-new-sdk-project"></a><span data-ttu-id="2b37c-150">Creare un nuovo progetto SDK</span><span class="sxs-lookup"><span data-stu-id="2b37c-150">Create a new SDK project</span></span>

<span data-ttu-id="2b37c-151">Il nuovo progetto .NET Core 3.0 creato deve essere in una directory diversa dal progetto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b37c-151">The new .NET Core 3.0 project you create must be in a different directory from your .NET Framework project.</span></span> <span data-ttu-id="2b37c-152">Se si trovano entrambi nella stessa directory, è possibile che si verifichino conflitti con i file generati nella directory **obj**.</span><span class="sxs-lookup"><span data-stu-id="2b37c-152">If they're both in the same directory, you may run into conflicts with the files that are generated in the **obj** directory.</span></span> <span data-ttu-id="2b37c-153">In questo esempio, si creerà una directory denominata **MyFormsAppCore** nella directory **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="2b37c-153">In this example, we'll create a directory named **MyFormsAppCore** in the **SolutionFolder** directory:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore      <--- New folder for core project
```

<span data-ttu-id="2b37c-154">Successivamente, è necessario creare il progetto **MyFormsCore.csproj** nella directory **MyFormsAppCore**.</span><span class="sxs-lookup"><span data-stu-id="2b37c-154">Next, you need to create the **MyFormsCore.csproj** project in the **MyFormsAppCore** directory.</span></span> <span data-ttu-id="2b37c-155">È possibile creare questo file manualmente usando l'editor di testo preferito.</span><span class="sxs-lookup"><span data-stu-id="2b37c-155">You can create this file manually by using the text editor of choice.</span></span> <span data-ttu-id="2b37c-156">Incollare il codice XML seguente:</span><span class="sxs-lookup"><span data-stu-id="2b37c-156">Paste in the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="2b37c-157">Se non si vuole creare manualmente il file di progetto, è possibile usare Visual Studio o .NET Core SDK per generare il progetto.</span><span class="sxs-lookup"><span data-stu-id="2b37c-157">If you don't want to create the project file manually, you can use Visual Studio or the .NET Core SDK to generate the project.</span></span> <span data-ttu-id="2b37c-158">Tuttavia, è necessario eliminare tutti gli altri file generati dal modello di progetto, ad eccezione del file di progetto.</span><span class="sxs-lookup"><span data-stu-id="2b37c-158">However, you must delete all other files generated by the project template except for the project file.</span></span> <span data-ttu-id="2b37c-159">Per usare l'SDK, eseguire il comando seguente dalla directory **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="2b37c-159">To use the SDK, run the following command from the **SolutionFolder** directory:</span></span>

```cli
dotnet new winforms -o MyFormsAppCore -n MyFormsCore
```

<span data-ttu-id="2b37c-160">Dopo aver creato **MyFormsCore.csproj**, la struttura della directory dovrebbe essere simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="2b37c-160">After you create the **MyFormsCore.csproj**, your directory structure should look like the following:</span></span>

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
└───MyFormsAppCore
    └───MyFormsCore.csproj
```

<span data-ttu-id="2b37c-161">È opportuno aggiungere il progetto **MyFormsCore.csproj** alla soluzione **MyApps.sln** con Visual Studio o l'interfaccia della riga di comando di .NET Core dalla directory **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="2b37c-161">You'll want to add the **MyFormsCore.csproj** project to **MyApps.sln** with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet sln add .\MyFormsAppCore\MyFormsCore.csproj
```

## <a name="fix-assembly-info-generation"></a><span data-ttu-id="2b37c-162">Correggere la generazione delle informazioni sull'assembly</span><span class="sxs-lookup"><span data-stu-id="2b37c-162">Fix assembly info generation</span></span>

<span data-ttu-id="2b37c-163">I progetti Windows Forms che sono stati creati con .NET Framework includono un file `AssemblyInfo.cs` che contiene gli attributi dell'assembly, ad esempio la versione dell'assembly da generare.</span><span class="sxs-lookup"><span data-stu-id="2b37c-163">Windows Forms projects that were created with .NET Framework include an `AssemblyInfo.cs` file, which contains assembly attributes such as the version of the assembly to be generated.</span></span> <span data-ttu-id="2b37c-164">I progetti in stile SDK generano automaticamente queste informazioni in base al file di progetto SDK.</span><span class="sxs-lookup"><span data-stu-id="2b37c-164">SDK-style projects automatically generate this information for you based on the SDK project file.</span></span> <span data-ttu-id="2b37c-165">La presenza di entrambi i tipi di "informazioni sull'assembly" crea un conflitto.</span><span class="sxs-lookup"><span data-stu-id="2b37c-165">Having both types of "assembly info" creates a conflict.</span></span> <span data-ttu-id="2b37c-166">Per risolvere questo problema, disabilitare la generazione automatica, che impone l'uso del file `AssemblyInfo.cs` esistente nel progetto.</span><span class="sxs-lookup"><span data-stu-id="2b37c-166">Resolve this problem by disabling automatic generation, which forces the project to use your existing `AssemblyInfo.cs` file.</span></span>

<span data-ttu-id="2b37c-167">Sono disponibili tre impostazioni da aggiungere al nodo `<PropertyGroup>` principale.</span><span class="sxs-lookup"><span data-stu-id="2b37c-167">There are three settings to add to the main `<PropertyGroup>` node.</span></span> 

- <span data-ttu-id="2b37c-168">**GenerateAssemblyInfo**\\</span><span class="sxs-lookup"><span data-stu-id="2b37c-168">**GenerateAssemblyInfo**\\</span></span>
<span data-ttu-id="2b37c-169">Quando si imposta questa proprietà su `false`, non verranno generati gli attributi dell'assembly.</span><span class="sxs-lookup"><span data-stu-id="2b37c-169">When you set this property to `false`, it won't generate the assembly attributes.</span></span> <span data-ttu-id="2b37c-170">Ciò consente di evitare il conflitto con il file `AssemblyInfo.cs` esistente dal progetto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b37c-170">This avoids the conflict with the existing `AssemblyInfo.cs` file from the .NET Framework project.</span></span>

- <span data-ttu-id="2b37c-171">**AssemblyName**\\</span><span class="sxs-lookup"><span data-stu-id="2b37c-171">**AssemblyName**\\</span></span>
<span data-ttu-id="2b37c-172">Il valore di questa proprietà è il file binario di output creato durante la compilazione.</span><span class="sxs-lookup"><span data-stu-id="2b37c-172">The value of this property is the output binary created when you compile.</span></span> <span data-ttu-id="2b37c-173">Non è necessario aggiungere un'estensione al nome.</span><span class="sxs-lookup"><span data-stu-id="2b37c-173">The name doesn't need an extension added to it.</span></span> <span data-ttu-id="2b37c-174">Ad esempio, `MyCoreApp` produce `MyCoreApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="2b37c-174">For example, using `MyCoreApp` produces `MyCoreApp.exe`.</span></span>

- <span data-ttu-id="2b37c-175">**RootNamespace**\\</span><span class="sxs-lookup"><span data-stu-id="2b37c-175">**RootNamespace**\\</span></span>
<span data-ttu-id="2b37c-176">Spazio dei nomi predefinito usato dal progetto.</span><span class="sxs-lookup"><span data-stu-id="2b37c-176">The default namespace used by your project.</span></span> <span data-ttu-id="2b37c-177">Deve corrispondere allo spazio dei nomi predefinito del progetto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b37c-177">This should match the default namespace of the .NET Framework project.</span></span>

<span data-ttu-id="2b37c-178">Aggiungere questi tre elementi al nodo `<PropertyGroup>` nel file `MyFormsCore.csproj`:</span><span class="sxs-lookup"><span data-stu-id="2b37c-178">Add these three elements to the `<PropertyGroup>` node in the `MyFormsCore.csproj` file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreApp</AssemblyName>
    <RootNamespace>WindowsFormsApp1</RootNamespace>
  </PropertyGroup>

</Project>
```

## <a name="add-source-code"></a><span data-ttu-id="2b37c-179">Aggiungere codice sorgente</span><span class="sxs-lookup"><span data-stu-id="2b37c-179">Add source code</span></span>

<span data-ttu-id="2b37c-180">Il progetto **MyFormsCore.csproj** per il momento non compila alcun codice.</span><span class="sxs-lookup"><span data-stu-id="2b37c-180">Right now, the **MyFormsCore.csproj** project doesn't compile any code.</span></span> <span data-ttu-id="2b37c-181">Per impostazione predefinita, i progetti .NET Core includono automaticamente tutto il codice sorgente nella directory corrente e in eventuali directory figlio.</span><span class="sxs-lookup"><span data-stu-id="2b37c-181">By default, .NET Core projects automatically include all source code in the current directory and any child directories.</span></span> <span data-ttu-id="2b37c-182">È necessario configurare il progetto per includere il codice dal progetto .NET Framework usando un percorso relativo.</span><span class="sxs-lookup"><span data-stu-id="2b37c-182">You must configure the project to include code from the .NET Framework project using a relative path.</span></span> <span data-ttu-id="2b37c-183">Se il progetto .NET Framework usava file **resx** per le icone e le risorse dei moduli, sarà necessario includere anche questi.</span><span class="sxs-lookup"><span data-stu-id="2b37c-183">If your .NET Framework project used **.resx** files for icons and resources for your forms, you'll need to include those too.</span></span> 

<span data-ttu-id="2b37c-184">Aggiungere il nodo `<ItemGroup>` seguente al progetto.</span><span class="sxs-lookup"><span data-stu-id="2b37c-184">Add the following `<ItemGroup>` node to your project.</span></span> <span data-ttu-id="2b37c-185">Ogni istruzione include un criterio GLOB per i file che include le directory figlio.</span><span class="sxs-lookup"><span data-stu-id="2b37c-185">Each statement includes a file glob pattern that includes child directories.</span></span>

```xml
  <ItemGroup>
    <Compile Include="..\MyFormsApp\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
  </ItemGroup>
```

<span data-ttu-id="2b37c-186">In alternativa, è possibile creare una voce `<Compile>` o `<EmbeddedResource>` per ogni file nel progetto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b37c-186">Alternatively, you can create a `<Compile>` or `<EmbeddedResource>` entry for each file in your .NET Framework project.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="2b37c-187">Aggiungere pacchetti NuGet</span><span class="sxs-lookup"><span data-stu-id="2b37c-187">Add NuGet packages</span></span>

<span data-ttu-id="2b37c-188">Aggiungere al progetto .NET Core ogni pacchetto NuGet a cui fa riferimento il progetto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b37c-188">Add each NuGet package referenced by the .NET Framework project to the .NET Core project.</span></span> 

<span data-ttu-id="2b37c-189">È molto probabile che l'app Windows Forms di .NET Framework includa un file **packages.config** che contiene un elenco di tutti i pacchetti NuGet a cui fa riferimento il progetto.</span><span class="sxs-lookup"><span data-stu-id="2b37c-189">Most likely your .NET Framework Windows Forms app has a **packages.config** file that contains a list of all of the NuGet packages that are referenced by your project.</span></span> <span data-ttu-id="2b37c-190">È possibile esaminare questo elenco per determinare quali pacchetti NuGet aggiungere al progetto .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b37c-190">You can look at this list to determine which NuGet packages to add to the .NET Core project.</span></span> <span data-ttu-id="2b37c-191">Ad esempio, se il progetto .NET Framework fa riferimento ai pacchetti NuGet `MetroFramework`, `MetroFramework.Design` e `MetroFramework.Fonts`, aggiungerli al progetto con Visual Studio o l'interfaccia della riga di comando di .NET Core dalla directory **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="2b37c-191">For example, if the .NET Framework project referenced the `MetroFramework`, `MetroFramework.Design`, and `MetroFramework.Fonts` NuGet packages, add each to the project with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Design
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package MetroFramework.Fonts
```

<span data-ttu-id="2b37c-192">I comandi precedenti consentono di aggiungere i riferimenti NuGet seguenti al progetto **MyFormsCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="2b37c-192">The previous commands would add the following NuGet references to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="MetroFramework" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Design" Version="1.2.0.3" />
    <PackageReference Include="MetroFramework.Fonts" Version="1.2.0.3" />
  </ItemGroup>
```

## <a name="port-control-libraries"></a><span data-ttu-id="2b37c-193">Convertire le librerie di controlli</span><span class="sxs-lookup"><span data-stu-id="2b37c-193">Port control libraries</span></span>

<span data-ttu-id="2b37c-194">Se è necessario convertire un progetto di libreria di controlli di Windows Forms, le istruzioni sono le stesse valide per la conversione di un progetto di app Windows Forms di .NET Framework, fatta eccezione per alcune impostazioni.</span><span class="sxs-lookup"><span data-stu-id="2b37c-194">If you have a Windows Forms Controls library project to port, the directions are the same as porting a .NET Framework Windows Forms app project, except for a few settings.</span></span> <span data-ttu-id="2b37c-195">Inoltre, anziché compilare un file eseguibile, si esegue la compilazione in una raccolta.</span><span class="sxs-lookup"><span data-stu-id="2b37c-195">And instead of compiling to an executable, you compile to a library.</span></span> <span data-ttu-id="2b37c-196">La differenza tra il progetto eseguibile e il progetto di libreria, oltre ai percorsi dei GLOB per i file che includono il codice sorgente, è minima.</span><span class="sxs-lookup"><span data-stu-id="2b37c-196">The difference between the executable project and the library project, besides paths for the file globs that include your source code, is minimal.</span></span>

<span data-ttu-id="2b37c-197">Riprendendo l'esempio del passaggio precedente, è possibile procedere espandendo i progetti e i file usati.</span><span class="sxs-lookup"><span data-stu-id="2b37c-197">Using the previous step's example, lets expand what projects and files we're working with.</span></span>

| <span data-ttu-id="2b37c-198">File</span><span class="sxs-lookup"><span data-stu-id="2b37c-198">File</span></span> | <span data-ttu-id="2b37c-199">Descrizione</span><span class="sxs-lookup"><span data-stu-id="2b37c-199">Description</span></span> |
| ---- | ----------- |
| <span data-ttu-id="2b37c-200">**MyApps.sln**</span><span class="sxs-lookup"><span data-stu-id="2b37c-200">**MyApps.sln**</span></span> | <span data-ttu-id="2b37c-201">Nome del file di soluzione.</span><span class="sxs-lookup"><span data-stu-id="2b37c-201">The name of the solution file.</span></span> |
| <span data-ttu-id="2b37c-202">**MyControls.csproj**</span><span class="sxs-lookup"><span data-stu-id="2b37c-202">**MyControls.csproj**</span></span> | <span data-ttu-id="2b37c-203">Nome del progetto per controlli Windows Forms di .NET Framework da convertire.</span><span class="sxs-lookup"><span data-stu-id="2b37c-203">The name of the .NET Framework Windows Forms Controls project to port.</span></span> |
| <span data-ttu-id="2b37c-204">**MyControlsCore.csproj**</span><span class="sxs-lookup"><span data-stu-id="2b37c-204">**MyControlsCore.csproj**</span></span> | <span data-ttu-id="2b37c-205">Nome del nuovo progetto di libreria .NET Core creato.</span><span class="sxs-lookup"><span data-stu-id="2b37c-205">The name of the new .NET Core library project you create.</span></span> |
| <span data-ttu-id="2b37c-206">**MyCoreControls.dll**</span><span class="sxs-lookup"><span data-stu-id="2b37c-206">**MyCoreControls.dll**</span></span> | <span data-ttu-id="2b37c-207">Libreria di controlli Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b37c-207">The .NET Core Windows Forms Controls library.</span></span> |

```
SolutionFolder
├───MyApps.sln
├───MyFormsApp
│   └───MyForms.csproj
├───MyFormsAppCore
│   └───MyFormsCore.csproj
│
├───MyFormsControls
│   └───MyControls.csproj
└───MyFormsControlsCore
    └───MyControlsCore.csproj   <--- New project for core controls
```

<span data-ttu-id="2b37c-208">Tenere conto delle differenze tra il progetto `MyControlsCore.csproj` e il progetto `MyFormsCore.csproj` creato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="2b37c-208">Consider the differences between the `MyControlsCore.csproj` project and the previously created `MyFormsCore.csproj` project.</span></span>

```diff
 <Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

   <PropertyGroup>
-    <OutputType>WinExe</OutputType>
     <TargetFramework>netcoreapp3.0</TargetFramework>
     <UseWindowsForms>true</UseWindowsForms>

     <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
-    <AssemblyName>MyCoreApp</AssemblyName>
-    <RootNamespace>WindowsFormsApp1</RootNamespace>
+    <AssemblyName>MyCoreControls</AssemblyName>
+    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
   </PropertyGroup>

   <ItemGroup>
-    <Compile Include="..\MyFormsApp\**\*.cs" />
-    <EmbeddedResource Include="..\MyFormsApp\**\*.resx" />
+    <Compile Include="..\MyFormsControls\**\*.cs" />
+    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
   </ItemGroup>

 </Project>
```

<span data-ttu-id="2b37c-209">Di seguito è riportato un esempio dell'aspetto del file di progetto di libreria di controlli Windows Forms .NET Core:</span><span class="sxs-lookup"><span data-stu-id="2b37c-209">Here is an example of what the .NET Core Windows Forms Controls library project file would look like:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <UseWindowsForms>true</UseWindowsForms>

    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <AssemblyName>MyCoreControls</AssemblyName>
    <RootNamespace>WindowsFormsControlLibrary1</RootNamespace>
  </PropertyGroup>
  
  <ItemGroup>
    <Compile Include="..\MyFormsControls\**\*.cs" />
    <EmbeddedResource Include="..\MyFormsControls\**\*.resx" />
  </ItemGroup>
  
</Project>
```

<span data-ttu-id="2b37c-210">Come si può notare, il nodo `<OutputType>` è stato rimosso e per questo il compilatore produce una libreria anziché un file eseguibile per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="2b37c-210">As you can see, the `<OutputType>` node was removed, which defaults the compiler to produce a library instead of an executable.</span></span> <span data-ttu-id="2b37c-211">Sono stati modificati `<AssemblyName>` e `<RootNamespace>`.</span><span class="sxs-lookup"><span data-stu-id="2b37c-211">The `<AssemblyName>` and `<RootNamespace>` were changed.</span></span> <span data-ttu-id="2b37c-212">In particolare, `<RootNamespace>` deve corrispondere allo spazio dei nomi della libreria di controlli Windows Forms da convertire.</span><span class="sxs-lookup"><span data-stu-id="2b37c-212">Specifically the `<RootNamespace>` should match the namespace of the Windows Forms Controls library you are porting.</span></span> <span data-ttu-id="2b37c-213">E, infine, i nodi `<Compile>` e `<EmbeddedResource>` sono stati modificati in modo da puntare alla cartella della libreria di controlli Windows Forms da convertire.</span><span class="sxs-lookup"><span data-stu-id="2b37c-213">And finally, the `<Compile>` and `<EmbeddedResource>` nodes were adjusted to point to the folder of the Windows Forms Controls library you are porting.</span></span>

<span data-ttu-id="2b37c-214">Successivamente, nel progetto **MyFormsCore.csproj** .NET Core principale aggiungere un riferimento alla nuova libreria di controlli Windows Forms .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b37c-214">Next, in the main .NET Core **MyFormsCore.csproj** project add reference to the new .NET Core Windows Forms Control library.</span></span> <span data-ttu-id="2b37c-215">Aggiungere un riferimento con Visual Studio o con l'interfaccia della riga di comando di .NET Core dalla directory **SolutionFolder**:</span><span class="sxs-lookup"><span data-stu-id="2b37c-215">Add a reference with either Visual Studio or the .NET Core CLI from the **SolutionFolder** directory:</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj reference .\MyFormsControlsCore\MyControlsCoreProject.csproj
```

<span data-ttu-id="2b37c-216">Il comando precedente consente di aggiungere il codice seguente al progetto **MyFormsCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="2b37c-216">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\MyFormsControlsCore\MyControlsCoreProject.csproj" />
  </ItemGroup>
```

## <a name="problems-compiling"></a><span data-ttu-id="2b37c-217">Problemi di compilazione</span><span class="sxs-lookup"><span data-stu-id="2b37c-217">Problems compiling</span></span>

<span data-ttu-id="2b37c-218">Se si riscontrano problemi durante la compilazione dei progetti, è possibile che siano in uso alcune API solo per Windows disponibili in .NET Framework, ma non in .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b37c-218">If you have problems compiling your projects, you may be using some Windows-only APIs that are available in .NET Framework but not available in .NET Core.</span></span> <span data-ttu-id="2b37c-219">È possibile provare ad aggiungere il pacchetto NuGet [Windows Compatibility Pack][compat-pack] al progetto.</span><span class="sxs-lookup"><span data-stu-id="2b37c-219">You can try adding the [Windows Compatibility Pack][compat-pack] NuGet package to your project.</span></span> <span data-ttu-id="2b37c-220">Questo pacchetto può essere eseguito solo in Windows e aggiunge circa 20.000 API Windows ai progetti .NET Core e .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2b37c-220">This package only runs on Windows and adds about 20,000 Windows APIs to .NET Core and .NET Standard projects.</span></span>

```cli
dotnet add .\MyFormsAppCore\MyFormsCore.csproj package Microsoft.Windows.Compatibility
```

<span data-ttu-id="2b37c-221">Il comando precedente consente di aggiungere il codice seguente al progetto **MyFormsCore.csproj**:</span><span class="sxs-lookup"><span data-stu-id="2b37c-221">The previous command adds the following to the **MyFormsCore.csproj** project:</span></span>

```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="2.0.1" />
  </ItemGroup>
```

## <a name="windows-forms-designer"></a><span data-ttu-id="2b37c-222">Progettazione Windows Form</span><span class="sxs-lookup"><span data-stu-id="2b37c-222">Windows Forms Designer</span></span>

<span data-ttu-id="2b37c-223">Come descritto in dettaglio in questo articolo, Visual Studio 2019 Preview/RC supporta solo la finestra di progettazione dei moduli nei progetti .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b37c-223">As detailed in this article, Visual Studio 2019 Preview/RC only supports the Forms Designer in .NET Framework projects.</span></span> <span data-ttu-id="2b37c-224">È possibile creare un progetto .NET Core affiancato per testare il progetto .NET Core mentre si usa progetto .NET Framework per la progettazione dei moduli.</span><span class="sxs-lookup"><span data-stu-id="2b37c-224">By creating a side-by-side .NET Core project, you can test your project with .NET Core while you use the .NET Framework project to design forms.</span></span> <span data-ttu-id="2b37c-225">Il file di soluzione include sia i progetti .NET Framework che .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b37c-225">Your solution file includes both the .NET Framework and .NET Core projects.</span></span> <span data-ttu-id="2b37c-226">Aggiungere e progettare i moduli e i controlli nel progetto .NET Framework e, in base ai criteri GLOB per i file aggiunti ai progetti .NET Core, qualsiasi file nuovo o modificato verrà incluso automaticamente nei progetti .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b37c-226">Add and design your forms and controls in the .NET Framework project, and based on the file glob patterns we added to the .NET Core projects, any new or changed files will automatically be included in the .NET Core projects.</span></span>

<span data-ttu-id="2b37c-227">Quando Visual Studio 2019 supporterà la finestra di progettazione per Windows Forms, sarà possibile copiare e incollare il contenuto del file di progetto .NET Core nel file di progetto .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b37c-227">Once Visual Studio 2019 supports the Windows Forms Designer, you can copy/paste the content of your .NET Core project file into the .NET Framework project file.</span></span> <span data-ttu-id="2b37c-228">Eliminare quindi i criteri GLOB per i file aggiunti con gli elementi `<Source>` e `<EmbeddedResource>`.</span><span class="sxs-lookup"><span data-stu-id="2b37c-228">Then delete the file glob patterns added with the `<Source>` and `<EmbeddedResource>` items.</span></span> <span data-ttu-id="2b37c-229">Correggere i percorsi per qualsiasi riferimento del progetto usato dall'app.</span><span class="sxs-lookup"><span data-stu-id="2b37c-229">Fix the paths to any project reference used by your app.</span></span> <span data-ttu-id="2b37c-230">In questo modo il progetto .NET Framework viene effettivamente aggiornato a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b37c-230">This effectively upgrades the .NET Framework project to a .NET Core project.</span></span>
 
## <a name="next-steps"></a><span data-ttu-id="2b37c-231">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="2b37c-231">Next steps</span></span>

* <span data-ttu-id="2b37c-232">Vedere altre informazioni su [Windows Compatibility Pack][compat-pack].</span><span class="sxs-lookup"><span data-stu-id="2b37c-232">Read more about the [Windows Compatibility Pack][compat-pack].</span></span>
* <span data-ttu-id="2b37c-233">Guardare un [video sulla conversione](https://www.youtube.com/watch?v=upVQEUc_KwU) del progetto Windows Forms di .NET Framework in .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2b37c-233">Watch a [video on porting](https://www.youtube.com/watch?v=upVQEUc_KwU) your .NET Framework Windows Forms project to .NET Core.</span></span>

[compat-pack]: windows-compat-pack.md