---
ms.openlocfilehash: ad624a665dbe8e989ea05acc20213809e515e6ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802541"
---
### <a name="incorrect-code-generation-when-passing-and-comparing-uint16-values"></a>Generazione di codice non corretto per il passaggio e il confronto di valori UInt16

|   |   |
|---|---|
|Dettagli|A causa di modifiche introdotte in .NET Framework 4.7, in alcuni casi il codice generato dal compilatore JIT nelle applicazioni in esecuzione in .NET Framework 4.7 confrontano in modo non corretto due valori <code>T:System.UInt16</code>. Per altre informazioni, vedere [Issue #11508: Silent bad codegen when passing and comparing ushort args](https://github.com/dotnet/coreclr/issues/11508) (Problema n. 11508: Generazione automatica di codice non valido quando si passano e confrontano argomenti ushort) su GitHub.com.|
|Suggerimento|Se si verificano problemi nel confronto di valori senza segno a 16 bit in .NET Framework 4.7, eseguire l'aggiornamento a .NET Framework 4.7.1.|
|Scope|Microsoft Edge|
|Versione|4.7|
|Type|Runtime|
