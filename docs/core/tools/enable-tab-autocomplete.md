---
title: Attivare il completamento con tasto TAB
description: Questo articolo illustra come abilitare il completamento tramite tasto TAB nell'interfaccia della riga di comando di .NET Core per PowerShell, Bash e zsh.
author: thraka
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 6614f11a9c4eb1b1aac4dd8dac8d05d15262bd0c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626008"
---
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a><span data-ttu-id="f2565-103">Come abilitare il completamento tramite TAB per l'interfaccia della riga di comando di .NET Core</span><span class="sxs-lookup"><span data-stu-id="f2565-103">How to enable TAB completion for the .NET Core CLI</span></span>

<span data-ttu-id="f2565-104">**Questo articolo si applica a:** ✔️ .net core 2,1 SDK e versioni successive</span><span class="sxs-lookup"><span data-stu-id="f2565-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="f2565-105">Questo articolo descrive come configurare il completamento tramite TAB per tre shell: PowerShell, Bash e zsh.</span><span class="sxs-lookup"><span data-stu-id="f2565-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="f2565-106">Per altre shell, fare riferimento alla relativa documentazione per informazioni su come configurare il completamento tramite tasto TAB.</span><span class="sxs-lookup"><span data-stu-id="f2565-106">For other shells, refer to their documentation on how to configure tab completion.</span></span>

<span data-ttu-id="f2565-107">Una volta configurato, il completamento tramite tasto TAB per la interfaccia della riga di comando di .NET Core viene attivato digitando un comando `dotnet` nella shell, quindi premendo il tasto TAB.</span><span class="sxs-lookup"><span data-stu-id="f2565-107">Once set up, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="f2565-108">La riga di comando corrente viene inviata al comando `dotnet complete` e i risultati vengono elaborati dalla shell.</span><span class="sxs-lookup"><span data-stu-id="f2565-108">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="f2565-109">Per testare i risultati senza abilitazione del completamento tramite TAB, inviare direttamente un elemento al comando `dotnet complete`.</span><span class="sxs-lookup"><span data-stu-id="f2565-109">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="f2565-110">Ad esempio,</span><span class="sxs-lookup"><span data-stu-id="f2565-110">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="f2565-111">Se questo comando non funziona, assicurarsi che sia installato .NET Core 2.0 SDK o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="f2565-111">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="f2565-112">Se è installata la versione appropriata ma il comando non funziona, assicurarsi che il comando `dotnet` risolva in .NET Core 2.0 SDK o una versione successiva.</span><span class="sxs-lookup"><span data-stu-id="f2565-112">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="f2565-113">Usare il comando `dotnet --version` per verificare la versione di `dotnet` in cui risolve il percorso corrente.</span><span class="sxs-lookup"><span data-stu-id="f2565-113">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="f2565-114">Per altre informazioni, vedere [Selezionare la versione di .NET Core da usare](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="f2565-114">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="f2565-115">Esempi</span><span class="sxs-lookup"><span data-stu-id="f2565-115">Examples</span></span>

<span data-ttu-id="f2565-116">Gli esempi seguenti visualizzano risultati del completamento tramite TAB:</span><span class="sxs-lookup"><span data-stu-id="f2565-116">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="f2565-117">Input</span><span class="sxs-lookup"><span data-stu-id="f2565-117">Input</span></span>                                | <span data-ttu-id="f2565-118">diventa</span><span class="sxs-lookup"><span data-stu-id="f2565-118">becomes</span></span>                                                                     | <span data-ttu-id="f2565-119">perché</span><span class="sxs-lookup"><span data-stu-id="f2565-119">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="f2565-120">`add` è il primo sottocomando in ordine alfabetico.</span><span class="sxs-lookup"><span data-stu-id="f2565-120">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="f2565-121">Il completamento tramite TAB rileva la corrispondenza delle sottostringhe e `--help` viene per prima in ordine alfabetico.</span><span class="sxs-lookup"><span data-stu-id="f2565-121">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="f2565-122">Se si preme TAB una seconda volta, viene visualizzato il suggerimento successivo.</span><span class="sxs-lookup"><span data-stu-id="f2565-122">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="f2565-123">I risultati vengono restituiti in ordine alfabetico.</span><span class="sxs-lookup"><span data-stu-id="f2565-123">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="f2565-124">Il completamento tramite TAB è compatibile con i file di progetto.</span><span class="sxs-lookup"><span data-stu-id="f2565-124">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="f2565-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2565-125">PowerShell</span></span>

<span data-ttu-id="f2565-126">Per aggiungere il completamento tramite TAB a **PowerShell** per l'interfaccia della riga di comando di .NET Core, creare o modificare il profilo memorizzato nella variabile `$PROFILE`.</span><span class="sxs-lookup"><span data-stu-id="f2565-126">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="f2565-127">Per altre informazioni, vedere [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) (Come creare un profilo) e [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy) (Profili e criteri di esecuzione).</span><span class="sxs-lookup"><span data-stu-id="f2565-127">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="f2565-128">Aggiungere il codice seguente al profilo:</span><span class="sxs-lookup"><span data-stu-id="f2565-128">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="f2565-129">barra rovesciata</span><span class="sxs-lookup"><span data-stu-id="f2565-129">bash</span></span>

<span data-ttu-id="f2565-130">Per aggiungere il completamento tramite TAB alla shell **bash** per l'interfaccia della riga di comando di .NET Core, aggiungere il codice seguente al file `.bashrc`:</span><span class="sxs-lookup"><span data-stu-id="f2565-130">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a><span data-ttu-id="f2565-131">zsh</span><span class="sxs-lookup"><span data-stu-id="f2565-131">zsh</span></span>

<span data-ttu-id="f2565-132">Per aggiungere il completamento tramite TAB alla shell **zsh** per l'interfaccia della riga di comando di .NET Core, aggiungere il codice seguente al file `.zshrc`:</span><span class="sxs-lookup"><span data-stu-id="f2565-132">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
