---
title: "Procedura: Visualizzare la Guida in un'applicazione Windows"
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: 2f9c0a9791db28cebd055ca446fdff16b9e276a4
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959605"
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Procedura: Visualizzare la Guida in un'applicazione Windows

È possibile rendere utilizzare il <xref:System.Windows.Forms.HelpProvider> componente collegare gli argomenti della Guida all'interno di un file della Guida a controlli specifici in un Windows Form. Il file della Guida può essere in formato HTML o HTMLHelp 1. x o versione successiva.

## <a name="provide-help"></a>Fornire la Guida

1. In Visual Studio, dai **casella degli strumenti**, trascinare un <xref:System.Windows.Forms.HelpProvider> al form.

     Il componente verrà posizionato sulla barra delle applicazioni in basso in Progettazione Windows Form.

2. Nel **delle proprietà** impostare nella finestra di <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> proprietà al file della Guida con estensione chm, col o htm.

3. Selezionare un altro controllo disponibile nel form e nella **delle proprietà** impostare nella finestra di <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> proprietà.

     Questa è la stringa passata attraverso il <xref:System.Windows.Forms.HelpProvider> componente al file della Guida per richiamare l'argomento della Guida appropriato.

4. Nel **proprietà** impostare nella finestra di <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> proprietà su un valore il <xref:System.Windows.Forms.HelpNavigator> enumerazione.

     Questa impostazione determina il modo in cui la proprietà **HelpKeyword** viene passata al sistema della Guida. La tabella seguente elenca le impostazioni possibili e le relative descrizioni.

    |Nome del membro|Descrizione|
    |-----------------|-----------------|
    |AssociateIndex|Specifica che l'indice di un argomento specificato viene eseguito nell'URL specificato.|
    |Find|Specifica che viene visualizzata la pagina di ricerca di un URL specificato.|
    |Indice|Specifica che viene visualizzato l'indice di un URL specificato.|
    |KeywordIndex|Specifica una parola chiave da cercare e l'azione da eseguire nell'URL specificato.|
    |TableOfContents|Specifica che viene visualizzato il sommario del file della Guida HTML 1.0.|
    |Argomento|Specifica che viene visualizzato l'argomento a cui fa riferimento l'URL specificato.|

 In fase di esecuzione, premere F1 quando il controllo, ovvero per cui sono state impostate le **HelpKeyword** e **HelpNavigator** le proprietà, ovvero ha lo stato attivo verrà aperto il file della Guida è associata a tale <xref:System.Windows.Forms.HelpProvider> componente.

 Attualmente, il **HelpNamespace** proprietà supporta i file della Guida nei tre formati seguenti: HTMLHelp 1.x, HTMLHelp 2.0 e HTML. Pertanto, è possibile impostare la proprietà **HelpNamespace** su un indirizzo http://, ad esempio una pagina Web. In tal caso, nel browser predefinito verrà visualizzata la pagina Web con la stringa specificata nella proprietà **HelpKeyword** usata come ancoraggio. L'ancoraggio viene usato per passare direttamente a una parte specifica di una pagina HTML.

> [!IMPORTANT]
> Assicurarsi di verificare tutte le informazioni inviate da un client prima di usarle nell'applicazione, dal momento che utenti malintenzionati potrebbero tentare di inviare script eseguibili, istruzioni SQL o altro codice. Prima di visualizzare l'input di un utente, archiviarlo in un database o usarlo, assicurarsi che non contenga informazioni potenzialmente pericolose. Un modo per effettuare questo controllo consiste nell'usare un'espressione regolare per cercare parole chiave come "SCRIPT" quando si riceve input da un utente.

È anche possibile usare il <xref:System.Windows.Forms.HelpProvider> componente per visualizzare la Guida rapida, anche se è stato configurato per visualizzare i file della Guida per i controlli nei Windows Form. Per altre informazioni, vedere [Procedura: Visualizzare la Guida rapida](how-to-display-pop-up-help.md).

## <a name="see-also"></a>Vedere anche

- [Procedura: Visualizzare la Guida rapida](how-to-display-pop-up-help.md)
- [Visualizzazione della Guida relativa a un controllo tramite le descrizioni comandi](control-help-using-tooltips.md)
- [Integrazione della Guida dell'utente in Windows Form](integrating-user-help-in-windows-forms.md)
- [Windows Form](../index.md)
