---
title: <message> Questo errore potrebbe inoltre essere dovuto all'unione di un riferimento al file con un riferimento progetto all'assembly '<assemblyname>'
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 951f90a9209ff31896f4426ceb75f05b012897a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921017"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>\<messaggio > Questo errore potrebbe inoltre essere dovuto all'unione di un riferimento al file con un riferimento progetto all'assembly '\<assemblyname >'
\<messaggio > Questo errore potrebbe inoltre essere dovuto all'unione di un riferimento al file con un riferimento progetto all'assembly '\<assemblyname >. In questo caso, provare a sostituire il riferimento file a '\<assemblyfilename >' nel progetto '\<projectname1 >' con un riferimento al progetto '\<projectname2 >'.  
  
 Il codice del progetto accede a un membro di un altro progetto, ma la configurazione della soluzione non supporta il compilatore Visual Basic risolvere il riferimento.  
  
 Per accedere a un tipo definito in un altro assembly, il compilatore Visual Basic deve avere un riferimento a tale assembly. Deve trattarsi di un riferimento unico, non ambiguo, che non generi riferimenti circolari tra i progetti.  
  
 **ID errore:** BC30971  
  
## <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1. Determinare quale progetto produce l'assembly migliore per il progetto a cui fare riferimento. Per questa decisione si potrebbero usare criteri quali la facilità di accesso al file e la frequenza di aggiornamenti.  
  
2. Nelle proprietà del progetto aggiungere un riferimento al progetto contenente l'assembly che definisce il tipo in uso.  
  
## <a name="see-also"></a>Vedere anche

- [Gestione dei riferimenti in un progetto](/visualstudio/ide/managing-references-in-a-project)
- [Riferimenti a elementi dichiarati](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Gestione delle proprietà di progetti e soluzioni](/visualstudio/ide/managing-project-and-solution-properties)
- [Risoluzione dei problemi relativi ai riferimenti interrotti](/visualstudio/ide/troubleshooting-broken-references)
