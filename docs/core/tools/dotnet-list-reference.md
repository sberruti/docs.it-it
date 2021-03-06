---
title: Comando dotnet list reference
description: Il comando dotnet list reference offre un'opzione utile per visualizzare un elenco dei riferimenti da progetto a progetto.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503708"
---
# <a name="dotnet-list-reference"></a>dotnet list reference

**Questo articolo si applica a:** ✔️ .NET Core 2.x SDK e versioni successive

## <a name="name"></a>Nome

`dotnet list reference`: visualizza un elenco dei riferimenti da progetto a progetto.

## <a name="synopsis"></a>Riepilogo

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a>Descrizione

Il comando `dotnet list reference` offre un'opzione utile per visualizzare un elenco dei riferimenti al progetto per un progetto o una soluzione specificata.

## <a name="arguments"></a>Argomenti

* **`PROJECT | SOLUTION`**

  Specifica il file di progetto o di soluzione da usare per l'elenco dei riferimenti. Se non specificato, il comando cerca un file di progetto nella directory corrente.

## <a name="options"></a>Opzioni

* **`-h|--help`**

  Stampa una breve guida per il comando.

## <a name="examples"></a>Esempi

* Visualizzare l'elenco dei riferimenti al progetto per il progetto specificato:

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* Visualizzare l'elenco dei riferimenti al progetto per il progetto nella directory corrente:

  ```dotnetcli
  dotnet list reference
  ```
