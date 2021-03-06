---
title: '#Direttiva ExternalSource'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343824"
---
# <a name="externalsource-directive"></a>Direttiva #ExternalSource

Indica un mapping tra le righe specifiche del codice sorgente e il testo esterno all'origine.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Parti  

 `StringLiteral`  
 Percorso dell'origine esterna.  
  
 `IntLiteral`  
 Il numero di riga della prima riga dell'origine esterna.  
  
 `LogicalLine`  
 Riga in cui si è verificato l'errore nell'origine esterna.  
  
 `#End ExternalSource`  
 Termina il blocco `#ExternalSource`.  
  
## <a name="remarks"></a>Osservazioni  

 Questa direttiva viene utilizzata solo dal compilatore e dal debugger.  
  
 Un file di origine può includere direttive di origine esterne, che indicano un mapping tra righe specifiche di codice nel file di origine e testo esterno all'origine, ad esempio un file aspx. Se durante la compilazione vengono rilevati errori nel codice sorgente designato, vengono identificati come provenienti dall'origine esterna.  
  
 Le direttive external source non hanno alcun effetto sulla compilazione e non possono essere annidate. Sono destinate esclusivamente all'uso interno da parte dell'applicazione.  
  
## <a name="see-also"></a>Vedere anche

- [Compilazione condizionale](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
