---
title: 'Mitigazione: Supporto di tocco e stilo basato su puntatore'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 023c38f66611bd0022699d3f62d90c3923585012
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094475"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Mitigazione: Supporto di tocco e stilo basato su puntatore

Le applicazioni WPF destinate a .NET Framework 4,7 e sono in esecuzione in Windows a partire da Windows 10 Creators Update possono abilitare uno stack di tocco/stilo WPF basato su `WM_POINTER`facoltativo.

## <a name="impact"></a>Impatto

Gli sviluppatori che non attivano in modo esplicito il supporto tocco/stilo basato su puntatore non dovrebbero riscontrare alcuna modifica nel comportamento di tocco/stilo WPF.

Di seguito sono riportati problemi noti correnti con lo stack tocco/stilo basato su `WM_POINTER`:

- Nessun supporto per l'input penna in tempo reale.

   Anche se i plug-in della stilo e dell'input penna continuano a funzionare, essi vengono elaborati nel thread dell'interfaccia utente, il che può comportare un peggioramento delle prestazioni.

- Modifiche del comportamento dovuti alla promozione da eventi di tocco/stilo agli eventi del mouse.

  - La modifica potrebbe avere un comportamento diverso.

  - L'opzione Trascina selezione non dà la risposta appropriata per l'input tocco. (Questa operazione non influisce sull'input della stilo.)

  - L'opzione Trascina selezione non può essere avviata per gli eventi di tocco/stilo.

      Questo può potenzialmente bloccare l'applicazione fino a quando non viene rilevato l'input del mouse. Gli sviluppatori dovranno quindi avviare l'opzione di trascinamento della selezione dagli eventi del mouse.

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a>Consenso esplicito al supporto di tocco/stilo basato su WM_POINTER

Gli sviluppatori che desiderano abilitare questo stack possono aggiungere quanto segue al file *app. config* dell'applicazione.

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Rimuovendo questa voce o impostandone il valore su `false`, questo stack facoltativo viene disattivato.

## <a name="see-also"></a>Vedere anche

- [Compatibilità delle applicazioni](application-compatibility.md)
