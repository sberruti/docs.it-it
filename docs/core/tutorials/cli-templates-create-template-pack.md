---
title: Creare un pacchetto di modelli per dotnet new
description: Informazioni su come creare un file csproj che compilerà un pacchetto di modelli per il comando dotnet new.
author: thraka
ms.date: 06/25/2019
ms.topic: tutorial
ms.author: adegeo
ms.openlocfilehash: df8c33856195ba7feacd32203e4a885997b50ad2
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67870630"
---
# <a name="tutorial-create-a-template-pack"></a><span data-ttu-id="b1453-103">Esercitazione: Creare un pacchetto di modelli</span><span class="sxs-lookup"><span data-stu-id="b1453-103">Tutorial: Create a template pack</span></span>

<span data-ttu-id="b1453-104">Con .NET Core è possibile creare e distribuire modelli per generare progetti, file e persino risorse.</span><span class="sxs-lookup"><span data-stu-id="b1453-104">With .NET Core, you can create and deploy templates that generate projects, files, even resources.</span></span> <span data-ttu-id="b1453-105">Questa esercitazione è la terza parte di una serie che illustra come creare, installare e disinstallare i modelli da usare con il comando `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="b1453-105">This tutorial is part three of a series that teaches you how to create, install, and uninstall, templates for use with the `dotnet new` command.</span></span>

<span data-ttu-id="b1453-106">In questa parte della serie si apprenderà come:</span><span class="sxs-lookup"><span data-stu-id="b1453-106">In this part of the series you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="b1453-107">Creare un progetto _.csproj\* per compilare un pacchetto di modelli</span><span class="sxs-lookup"><span data-stu-id="b1453-107">Create a _.csproj\* project to build a template pack</span></span>
> * <span data-ttu-id="b1453-108">Configurare il file di progetto per la creazione del pacchetto</span><span class="sxs-lookup"><span data-stu-id="b1453-108">Configure the project file for packing</span></span>
> * <span data-ttu-id="b1453-109">Installare un modello da un file di pacchetto NuGet</span><span class="sxs-lookup"><span data-stu-id="b1453-109">Install a template from a NuGet package file</span></span>
> * <span data-ttu-id="b1453-110">Disinstallare un modello in base all'ID del pacchetto</span><span class="sxs-lookup"><span data-stu-id="b1453-110">Uninstall a template by package ID</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1453-111">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="b1453-111">Prerequisites</span></span>

* <span data-ttu-id="b1453-112">Completare la [parte 1](cli-templates-create-item-template.md) e la [parte 2](cli-templates-create-project-template.md) di questa serie di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="b1453-112">Complete [part 1](cli-templates-create-item-template.md) and [part 2](cli-templates-create-project-template.md) of this tutorial series.</span></span>

  <span data-ttu-id="b1453-113">Questa esercitazione usa i due modelli creati nelle prime due parti di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="b1453-113">This tutorial uses the two templates created in the first two parts of this tutorial.</span></span> <span data-ttu-id="b1453-114">È possibile usare un modello diverso, a condizione di copiare il modello come cartella nella cartella _working\templates\\_ .</span><span class="sxs-lookup"><span data-stu-id="b1453-114">It's possible you can use a different template as long as you copy the template as a folder into the _working\templates\\_ folder.</span></span>

* <span data-ttu-id="b1453-115">Aprire un terminale e passare alla cartella _working\templates\\_ .</span><span class="sxs-lookup"><span data-stu-id="b1453-115">Open a terminal and navigate to the _working\templates\\_ folder.</span></span>

## <a name="create-a-template-pack-project"></a><span data-ttu-id="b1453-116">Creare un progetto per il pacchetto di modelli</span><span class="sxs-lookup"><span data-stu-id="b1453-116">Create a template pack project</span></span>

<span data-ttu-id="b1453-117">Un pacchetto di modelli è costituito da uno o più modelli assemblati in un file.</span><span class="sxs-lookup"><span data-stu-id="b1453-117">A template pack is one or more templates packaged into a file.</span></span> <span data-ttu-id="b1453-118">Quando si installa o disinstalla un pacchetto, vengono aggiunti o rimossi rispettivamente tutti i modelli contenuti nel pacchetto.</span><span class="sxs-lookup"><span data-stu-id="b1453-118">When you install or uninstall a pack, all templates contained in the pack are added or removed, respectively.</span></span> <span data-ttu-id="b1453-119">Nelle parti precedenti di questa serie di esercitazioni sono stati utilizzati solo i singoli modelli.</span><span class="sxs-lookup"><span data-stu-id="b1453-119">The previous parts of this tutorial series only worked with individual templates.</span></span> <span data-ttu-id="b1453-120">Per condividere un modello non incluso in un pacchetto, è necessario copiare la cartella del modello e installarla tramite tale cartella.</span><span class="sxs-lookup"><span data-stu-id="b1453-120">To share a non-packed template, you have to copy the template folder and install via that folder.</span></span> <span data-ttu-id="b1453-121">Dato che un pacchetto di modelli può includere più di un modello ed è un singolo file, la condivisione è più semplice.</span><span class="sxs-lookup"><span data-stu-id="b1453-121">Because a template pack can have more than one template in it, and is a single file, sharing is easier.</span></span>

<span data-ttu-id="b1453-122">I pacchetti di modelli sono rappresentati da un file di pacchetto NuGet (con estensione _nupkg_).</span><span class="sxs-lookup"><span data-stu-id="b1453-122">Template packs are represented by a NuGet package (_.nupkg_) file.</span></span> <span data-ttu-id="b1453-123">Come per qualsiasi altro pacchetto NuGet è possibile caricare il pacchetto di modelli in un feed NuGet.</span><span class="sxs-lookup"><span data-stu-id="b1453-123">And, like any NuGet package, you can upload the template pack to a NuGet feed.</span></span> <span data-ttu-id="b1453-124">Il comando `dotnet new -i` supporta l'installazione del pacchetto di modelli da un feed di pacchetti NuGet.</span><span class="sxs-lookup"><span data-stu-id="b1453-124">The `dotnet new -i` command supports installing template pack from a NuGet package feed.</span></span> <span data-ttu-id="b1453-125">È anche possibile installare un pacchetto di modelli direttamente da un file con estensione _nupkg_.</span><span class="sxs-lookup"><span data-stu-id="b1453-125">Additionally, you can install a template pack from a _.nupkg_ file directly.</span></span>

<span data-ttu-id="b1453-126">Normalmente si usa un file di progetto C# per compilare il codice e generare un file binario.</span><span class="sxs-lookup"><span data-stu-id="b1453-126">Normally you use a C# project file to compile code and produce a binary.</span></span> <span data-ttu-id="b1453-127">Tuttavia, il progetto può essere usato anche per generare un pacchetto di modelli.</span><span class="sxs-lookup"><span data-stu-id="b1453-127">However, the project can also be used to generate a template pack.</span></span> <span data-ttu-id="b1453-128">Modificando le impostazioni del file _.csproj_, è possibile evitare la compilazione del codice e includere invece tutti gli asset dei modelli come risorse.</span><span class="sxs-lookup"><span data-stu-id="b1453-128">By changing the settings of the _.csproj_, you can prevent it from compiling any code and instead include all the assets of your templates as resources.</span></span> <span data-ttu-id="b1453-129">Quando il progetto viene compilato, viene prodotto un pacchetto NuGet del pacchetto di modelli.</span><span class="sxs-lookup"><span data-stu-id="b1453-129">When this project is built, it produces a template pack NuGet package.</span></span>

<span data-ttu-id="b1453-130">Il pacchetto che verrà creato includerà il [modello di elemento](cli-templates-create-item-template.md) e il [modello di pacchetto](cli-templates-create-project-template.md) creati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="b1453-130">The pack you'll create will include the [item template](cli-templates-create-item-template.md) and [package template](cli-templates-create-project-template.md) previously created.</span></span> <span data-ttu-id="b1453-131">Dato che i due modelli sono stati raggruppati nella cartella _working\templates\\_ , è possibile usare la cartella _working_ per il file con estensione _csproj_.</span><span class="sxs-lookup"><span data-stu-id="b1453-131">Because we grouped the two templates into the _working\templates\\_ folder, we can use the _working_ folder for the _.csproj_ file.</span></span>

<span data-ttu-id="b1453-132">Nel terminale passare alla cartella _working_.</span><span class="sxs-lookup"><span data-stu-id="b1453-132">In your terminal, navigate to the _working_ folder.</span></span> <span data-ttu-id="b1453-133">Creare un nuovo progetto e impostare il nome su `templatepack` e la cartella di output sulla cartella corrente.</span><span class="sxs-lookup"><span data-stu-id="b1453-133">Create a new project and set the name to `templatepack` and the output folder to the current folder.</span></span>

```console
dotnet new console -n templatepack -o .
```

<span data-ttu-id="b1453-134">Il parametro `-n` imposta il nome del file _csproj_ su _templatepack.csproj_ e il parametro `-o` crea i file nella directory corrente.</span><span class="sxs-lookup"><span data-stu-id="b1453-134">The `-n` parameter sets the _.csproj_ filename to _templatepack.csproj_ and the `-o` parameters creates the files in the current directory.</span></span> <span data-ttu-id="b1453-135">Viene visualizzato un risultato simile all'output seguente.</span><span class="sxs-lookup"><span data-stu-id="b1453-135">You should see a result similar to the following output.</span></span>

```console
C:\working> dotnet new console -n templatepack -o .
The template "Console Application" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on .\templatepack.csproj...
  Restore completed in 52.38 ms for C:\working\templatepack.csproj.

Restore succeeded.
```

<span data-ttu-id="b1453-136">Aprire poi il file _templatepack.csproj_ nell'editor preferito e sostituire il contenuto con il codice XML seguente:</span><span class="sxs-lookup"><span data-stu-id="b1453-136">Next, open the _templatepack.csproj_ file in your favorite editor and replace the content with the following XML:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>

    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="b1453-137">Le impostazioni `<PropertyGroup>` nel codice XML precedente sono suddivise in tre gruppi.</span><span class="sxs-lookup"><span data-stu-id="b1453-137">The `<PropertyGroup>` settings in the XML above is broken into three groups.</span></span> <span data-ttu-id="b1453-138">Il primo gruppo gestisce le proprietà necessarie per un pacchetto NuGet.</span><span class="sxs-lookup"><span data-stu-id="b1453-138">The first group deals with properties required for a NuGet package.</span></span> <span data-ttu-id="b1453-139">Le tre impostazioni `<Package` riguardano le proprietà del pacchetto NuGet per identificare il pacchetto in un feed NuGet.</span><span class="sxs-lookup"><span data-stu-id="b1453-139">The three `<Package` settings have to do with the NuGet package properties to identify your package on a NuGet feed.</span></span> <span data-ttu-id="b1453-140">In particolare, il valore `<PacakgeId>` viene usato per disinstallare il pacchetto di modelli con un nome singolo anziché con un percorso di directory.</span><span class="sxs-lookup"><span data-stu-id="b1453-140">Specifically the `<PacakgeId>` value is used to uninstall the template pack with a single name instead of a directory path.</span></span> <span data-ttu-id="b1453-141">Può anche essere usato per installare il pacchetto di modelli da un feed NuGet.</span><span class="sxs-lookup"><span data-stu-id="b1453-141">It can also be used to install the template pack from a NuGet feed.</span></span> <span data-ttu-id="b1453-142">Le impostazioni rimanenti, come `<Title>` e `<Tags>`, si riferiscono ai metadati visualizzati nel feed NuGet.</span><span class="sxs-lookup"><span data-stu-id="b1453-142">The remaining settings such as `<Title>` and `<Tags>` have to do with metadata displayed on the NuGet feed.</span></span> <span data-ttu-id="b1453-143">Per altre informazioni sulle impostazioni di NuGet, vedere le [proprietà di NuGet e MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="b1453-143">For more information about NuGet settings, see [NuGet and MSBuild properties](/nuget/reference/msbuild-targets).</span></span>

<span data-ttu-id="b1453-144">L'impostazione `<TargetFramework>` deve essere impostata in modo che MSBuild venga eseguito correttamente quando si esegue il comando pack per compilare il progetto e crearne il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="b1453-144">The `<TargetFramework>` setting must be set so that MSBuild will run properly when you run the pack command to compile and pack the project.</span></span>

<span data-ttu-id="b1453-145">Le ultime tre impostazioni riguardano la configurazione corretta del progetto per includere i modelli nella cartella appropriata nel pacchetto NuGet quando viene creato.</span><span class="sxs-lookup"><span data-stu-id="b1453-145">The last three settings have to do with configuring the project correctly to include the templates in the appropriate folder in the NuGet pack when it's created.</span></span>

<span data-ttu-id="b1453-146">`<ItemGroup>` contiene due impostazioni.</span><span class="sxs-lookup"><span data-stu-id="b1453-146">The `<ItemGroup>` contains two settings.</span></span> <span data-ttu-id="b1453-147">In primo luogo, l'impostazione `<Content>` include tutto il contenuto della cartella _templates_.</span><span class="sxs-lookup"><span data-stu-id="b1453-147">First, the `<Content>` setting includes everything in the _templates_ folder as content.</span></span> <span data-ttu-id="b1453-148">Viene anche impostata per escludere qualsiasi cartella _bin_ o cartella _obj_ per impedire l'inclusione di codice compilato (se i modelli sono stati testati e compilati).</span><span class="sxs-lookup"><span data-stu-id="b1453-148">It's also set to exclude any _bin_ folder or _obj_ folder to prevent any compiled code (if you tested and compiled your templates) from being included.</span></span> <span data-ttu-id="b1453-149">In secondo luogo, l'impostazione `<Compile>` esclude tutti i file di codice dalla compilazione indipendentemente da dove si trovano.</span><span class="sxs-lookup"><span data-stu-id="b1453-149">Second, the `<Compile>` setting excludes all code files from compiling no matter where they're located.</span></span> <span data-ttu-id="b1453-150">Questa impostazione impedisce che il progetto usato per creare un pacchetto di modelli provi a compilare il codice nella gerarchia di cartelle _templates_.</span><span class="sxs-lookup"><span data-stu-id="b1453-150">This setting prevents the project being used to create a template pack from trying to compile the code in the _templates_ folder hierarchy.</span></span>

## <a name="build-and-install"></a><span data-ttu-id="b1453-151">Compilare e installare</span><span class="sxs-lookup"><span data-stu-id="b1453-151">Build and install</span></span>

<span data-ttu-id="b1453-152">Salvare questo file e quindi eseguire il comando pack</span><span class="sxs-lookup"><span data-stu-id="b1453-152">Save this file and then run the pack command</span></span>

```console
dotnet pack
```

<span data-ttu-id="b1453-153">Questo comando compilerà il progetto e creerà un pacchetto NuGet nella cartella _working\bin\Debug_.</span><span class="sxs-lookup"><span data-stu-id="b1453-153">This command will build your project and create a NuGet package in This should be the _working\bin\Debug_ folder.</span></span>

```console
C:\working> dotnet pack
Microsoft (R) Build Engine version 16.2.0-preview-19278-01+d635043bd for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 123.86 ms for C:\working\templatepack.csproj.

  templatepack -> C:\working\bin\Debug\netstandard2.0\templatepack.dll
  Successfully created package 'C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg'.
```

<span data-ttu-id="b1453-154">Installare quindi il file del pacchetto di modelli con il comando `dotnet new -i PATH_TO_NUPKG_FILE`.</span><span class="sxs-lookup"><span data-stu-id="b1453-154">Next, install the template pack file with the `dotnet new -i PATH_TO_NUPKG_FILE` command.</span></span>

```console
C:\working> dotnet new -i C:\working\bin\Debug\AdatumCorporation.Utility.Templates.1.0.0.nupkg
Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name            Language          Tags
-------------------------------------------------------------------------------------------------------------------------------
Example templates: string extensions              stringext             [C#]              Common/Code
Console Application                               console               [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync          [C#]              Common/Console/C#8
Class library                                     classlib              [C#], F#, VB      Common/Library
```

<span data-ttu-id="b1453-155">Se il pacchetto NuGet è stato caricato in un feed NuGet, è possibile usare il comando `dotnet new -i PACKAGEID`, dove `PACKAGEID` è uguale all'impostazione `<PackageId>` dal file _csproj_.</span><span class="sxs-lookup"><span data-stu-id="b1453-155">If you uploaded the NuGet package to a NuGet feed, you can use the `dotnet new -i PACKAGEID` command where `PACKAGEID` is the same as the `<PackageId>` setting from the _.csproj_ file.</span></span> <span data-ttu-id="b1453-156">Questo ID di pacchetto è uguale all'identificatore del pacchetto NuGet.</span><span class="sxs-lookup"><span data-stu-id="b1453-156">This package ID is the same as the NuGet package identifier.</span></span>

## <a name="uninstall-the-template-pack"></a><span data-ttu-id="b1453-157">Disinstallare il pacchetto di modelli</span><span class="sxs-lookup"><span data-stu-id="b1453-157">Uninstall the template pack</span></span>

<span data-ttu-id="b1453-158">Indipendentemente da come è stato installato il pacchetto di modelli, ovvero con il file _.nupkg_ direttamente o dal feed NuGet, la procedura per rimuovere un pacchetto di modelli è la stessa.</span><span class="sxs-lookup"><span data-stu-id="b1453-158">No matter how you installed the template pack, either with the _.nupkg_ file directly or by NuGet feed, removing a template pack is the same.</span></span> <span data-ttu-id="b1453-159">Usare il `<PackageId>` del modello che si vuole disinstallare.</span><span class="sxs-lookup"><span data-stu-id="b1453-159">Use the `<PackageId>` of the template you want to uninstall.</span></span> <span data-ttu-id="b1453-160">È possibile ottenere un elenco dei modelli installati eseguendo il comando `dotnet new -u`.</span><span class="sxs-lookup"><span data-stu-id="b1453-160">You can get a list of templates that are installed by running the `dotnet new -u` command.</span></span>

```console
C:\working> dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      dotnet gitignore file (gitignore)
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)

... cut to save space ...

  NUnit3.DotNetNew.Template
    Templates:
      NUnit 3 Test Project (nunit) C#
      NUnit 3 Test Item (nunit-test) C#
      NUnit 3 Test Project (nunit) F#
      NUnit 3 Test Item (nunit-test) F#
      NUnit 3 Test Project (nunit) VB
      NUnit 3 Test Item (nunit-test) VB
  AdatumCorporation.Utility.Templates
    Templates:
      Example templates: async project (consoleasync) C#
      Example templates: string extensions (stringext) C#
```

<span data-ttu-id="b1453-161">Eseguire `dotnet new -u AdatumCorporation.Utility.Templates` per disinstallare il modello.</span><span class="sxs-lookup"><span data-stu-id="b1453-161">Run `dotnet new -u AdatumCorporation.Utility.Templates` to uninstall the template.</span></span> <span data-ttu-id="b1453-162">Il comando `dotnet new` restituirà informazioni che dovrebbero omettere i modelli installati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="b1453-162">The `dotnet new` command will output help information that should omit the templates you previously installed.</span></span>

<span data-ttu-id="b1453-163">La procedura è stata completata.</span><span class="sxs-lookup"><span data-stu-id="b1453-163">Congratulations!</span></span> <span data-ttu-id="b1453-164">È stato installato e disinstallato un pacchetto di modelli.</span><span class="sxs-lookup"><span data-stu-id="b1453-164">you've installed and uninstalled a template pack.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="b1453-165">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="b1453-165">Next steps</span></span>

<span data-ttu-id="b1453-166">Per altre informazioni sui modelli, la maggior parte delle quali è già nota, vedere l'articolo [Modelli personalizzati per dotnet new](../tools/custom-templates.md).</span><span class="sxs-lookup"><span data-stu-id="b1453-166">To learn more about templates, most of which you've already learned, see the [Custom templates for dotnet new](../tools/custom-templates.md) article.</span></span>

* [<span data-ttu-id="b1453-167">Wiki del repository GitHub dotnet/templating</span><span class="sxs-lookup"><span data-stu-id="b1453-167">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)
* [<span data-ttu-id="b1453-168">Repository GitHub dotnet/dotnet-template-samples</span><span class="sxs-lookup"><span data-stu-id="b1453-168">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)
* <span data-ttu-id="b1453-169">Lo schema [*template.JSON* nell'archivio di schemi JSON](http://json.schemastore.org/template)</span><span class="sxs-lookup"><span data-stu-id="b1453-169">[*template.json* schema at the JSON Schema Store](http://json.schemastore.org/template)</span></span>