---
title: Supporto di automazione interfaccia utente per il tipo di controllo Pane
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Pane control type
- Pane control type
- control types, Pane
ms.assetid: 79761191-4449-4630-899c-9cbdb8867d3f
ms.openlocfilehash: 0a445d0631fe6a24d8e9b5cb21cd78f260465486
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741599"
---
# <a name="ui-automation-support-for-the-pane-control-type"></a>Supporto di automazione interfaccia utente per il tipo di controllo Pane
> [!NOTE]
> Questa documentazione è destinata agli sviluppatori di .NET Framework che vogliono usare le classi gestite di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definite nello spazio dei nomi <xref:System.Windows.Automation>. Per informazioni aggiornate su [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vedere [Windows Automation API: automazione interfaccia utente](/windows/win32/winauto/entry-uiauto-win32).  
  
 In questo argomento vengono fornite informazioni sul supporto di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] per il tipo di controllo Pane. In [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]un tipo di controllo è un set di condizioni che un controllo deve soddisfare per usare la proprietà <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Le condizioni includono linee guida specifiche per la struttura ad albero di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , i valori delle proprietà di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] e i pattern di controllo.  
  
 Il tipo di controllo Pane viene usato per rappresentare un oggetto all'interno di una finestra cornice o finestra documento. Gli utenti possono spostarsi tra controlli riquadro e all'interno del contenuto del riquadro corrente, ma non possono spostarsi tra gli elementi in riquadri diversi. In questo modo i controlli riquadro rappresentano un livello di raggruppamento inferiore rispetto alle finestre e documenti, ma superiore ai singoli controlli. L'utente si sposta tra i riquadri premendo TAB, F6 o CTRL+TAB, a seconda del contesto. Il tipo di controllo Pane non richiede metodi di spostamento specifici tramite tastiera.  
  
 Nelle sezioni seguenti vengono definiti la struttura ad albero, le proprietà, i pattern di controllo e gli eventi di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] per il tipo di controllo Pane. I requisiti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] si applicano a tutti i controlli elenco, sia [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 che [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struttura ad albero di automazione interfaccia utente obbligatoria  
 Nella tabella seguente viene illustrata la visualizzazione controlli e la visualizzazione contenuto dell'albero di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] relativo ai controlli riquadro e viene descritto il possibile contenuto di ogni visualizzazione. Per altre informazioni sull'albero di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , vedere [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Visualizzazione controlli|Visualizzazione contenuto|  
|------------------|------------------|  
|Pane|Pane|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Proprietà di automazione interfaccia utente obbligatorie  
 La tabella seguente elenca le proprietà di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] il cui valore o la cui definizione è particolarmente rilevante per i controlli riquadro. Per ulteriori informazioni sulle proprietà di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], vedere [UI Automation Properties for clients](ui-automation-properties-for-clients.md).  
  
|Proprietà di[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Valore|Note|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Vedere le note.|Il valore di questa proprietà deve essere univoco in tutti i controlli in un'applicazione.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Vedere le note.|Il rettangolo più esterno che contiene l'intero controllo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Vedere le note.|Se il controllo può ricevere lo stato attivo, deve supportare questa proprietà.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Vedere le note.|Il valore di questa proprietà deve essere sempre un titolo chiaro, conciso e significativo.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Vedere le note.|Questa proprietà espone un punto selezionabile del controllo riquadro che fa sì che il riquadro assuma lo stato attivo quando viene selezionato.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Vedere le note.|I controlli riquadro in genere non hanno un'etichetta statica. Se è presente un'etichetta di testo statico, l'etichetta deve essere esposta tramite questa proprietà.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Pane|Questo valore è uguale per tutti i framework dell' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"pane"|Stringa localizzata corrispondente al tipo di controllo Pane.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Il controllo Pane viene sempre incluso nella visualizzazione contenuto dell'albero di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Il controllo Pane viene sempre incluso nella visualizzazione controlli dell'albero di [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Il testo della Guida per i controlli riquadro deve illustrare la finalità del riquadro e l'interrelazione del riquadro con altri riquadri. La descrizione si rende necessaria se la finalità e la relazione dei riquadri non è evidente in base al valore di `NameProperty`. "|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|Vedere le note.|Se una combinazione di tasti specifica sposta lo stato attivo sul riquadro, le informazioni devono essere esposte tramite questa proprietà.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Pattern di controllo obbligatori per l'automazione interfaccia utente  
 La tabella seguente elenca i pattern di controllo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] che devono essere supportati da tutti i controlli di modifica. Per altre informazioni sui pattern di controllo, vedere [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md).  
  
|Pattern di controllo|Supporto|Note|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|A seconda dei casi|Implementare questo pattern di controllo se il controllo riquadro può essere spostato, ridimensionato o ruotato sullo schermo.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|Mai|Se è necessario implementare questo pattern di controllo, il controllo deve essere basato sul tipo di controllo <xref:System.Windows.Automation.ControlType.Window> .|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|A seconda dei casi|Implementare questo pattern di controllo se il controllo riquadro può essere ancorato.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|A seconda dei casi|Implementare questo pattern di controllo se il controllo riquadro supporta lo scorrimento.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Eventi di automazione interfaccia utente obbligatori  
 La tabella seguente elenca gli eventi dell' [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] che devono essere supportati da tutti i controlli riquadro. Per altre informazioni sugli eventi, vedere [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|o[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Supporto/valore|Note|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|Mai|nessuna|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|Mai|nessuna|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent>|Richiesto|nessuna|  
|Evento di modifica della proprietà<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> .|Richiesto|nessuna|  
|Evento di modifica della proprietà<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> .|Richiesto|nessuna|  
|Evento di modifica della proprietà<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> .|Richiesto|nessuna|  
|Evento di modifica della proprietà<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> .|A seconda dei casi|nessuna|  
|Evento di modifica della proprietà<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> .|A seconda dei casi|nessuna|  
|Evento di modifica della proprietà<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> .|A seconda dei casi|nessuna|  
|Evento di modifica della proprietà<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> .|A seconda dei casi|nessuna|  
|Evento di modifica della proprietà<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> .|A seconda dei casi|nessuna|  
|Evento di modifica della proprietà<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> .|A seconda dei casi|nessuna|  
|Evento di modifica della proprietà<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty> .|Mai|nessuna|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Richiesto|nessuna|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Richiesto|nessuna|  
  
<a name="Pane_Control_Type_Example"></a>   
## <a name="pane-control-type-example"></a>Esempio di tipo di controllo Pane  
 Nell'immagine seguente viene illustrato un controllo che implementa il tipo di controllo Pane.  
  
 ![Screenshot della finestra dell'applet con due riquadri](./media/uiauto-pane.GIF "uiauto_pane")  
  
|Albero di[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] - Visualizzazione controlli|Albero di[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] - Visualizzazione contenuto|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>Pane</li><li>Tree (pattern Scroll)<br /><br /> <ul><li>TreeItem</li><li>Pane</li><li>Edit (pattern Scroll)</li></ul></li></ul>|-Riquadro<br />-Tree (pattern scroll)<br />-TreeItem<br />- ... Riquadro<br />-Modifica<br />-(Pattern scroll)|  
  
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Automation.ControlType.Pane>
- [Panoramica dei tipi di controllo per l'automazione interfaccia utente](ui-automation-control-types-overview.md)
- [Panoramica di automazione interfaccia utente](ui-automation-overview.md)
