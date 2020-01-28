---
title: Personalizzare le celle e le colonne nel controllo DataGridView estendendo il comportamento e l'aspetto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: be01e085d4fa74c0c49f0a0494183482875c6a09
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744069"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>Procedura: personalizzare celle e colonne nel controllo DataGridView di Windows Form estendendone il comportamento e l'aspetto
Il controllo <xref:System.Windows.Forms.DataGridView> offre diversi metodi per personalizzare l'aspetto e il comportamento mediante proprietà, eventi e classi correlate. In alcune situazioni è possibile che i requisiti relativi alle celle non possano essere soddisfatti mediante le funzioni fornite. In questi casi per estendere le funzionalità è possibile creare una propria classe <xref:System.Windows.Forms.DataGridViewCell> personalizzata.  
  
 La classe <xref:System.Windows.Forms.DataGridViewCell> personalizzata può essere creata derivandola dalla classe di base <xref:System.Windows.Forms.DataGridViewCell> o da una delle relative classi derivate. Sebbene sia possibile visualizzare qualsiasi tipo di cella in qualsiasi tipo di colonna, in genere viene creata anche una classe <xref:System.Windows.Forms.DataGridViewColumn> personalizzata per la visualizzazione del tipo di cella. Le classi di colonna derivano da <xref:System.Windows.Forms.DataGridViewColumn> o da uno dei tipi derivati.  
  
 Nell'esempio di codice riportato di seguito viene creata la classe di cella personalizzata `DataGridViewRolloverCell` in grado di rilevare il passaggio in ingresso e in uscita del mouse sui bordi delle celle. Quando il mouse è all'interno dei bordi della cella, viene disegnato un rettangolo interno. Poiché questo nuovo tipo è derivato da <xref:System.Windows.Forms.DataGridViewTextBoxCell>, si comporta da tutti gli altri punti di vista come la classe di base. La classe di colonna correlata è `DataGridViewRolloverColumn`.  
  
 Per usare queste classi, creare un form contenente un controllo <xref:System.Windows.Forms.DataGridView>, aggiungere uno o più oggetti `DataGridViewRolloverColumn` all'insieme <xref:System.Windows.Forms.DataGridView.Columns%2A> e popolare il controllo con righe contenenti valori.  
  
> [!NOTE]
> L'esempio non funzionerà correttamente se si aggiungono righe vuote. Le righe vuote vengono create, ad esempio, quando si aggiungono righe al controllo mediante l'impostazione della proprietà <xref:System.Windows.Forms.DataGridView.RowCount%2A>. Poiché le righe aggiunte in questo modo vengono automaticamente condivise, non vengono create istanze degli oggetti `DataGridViewRolloverCell` finché non si selezionano le singole celle, rendendo di conseguenza le righe associate non più condivise.  
  
 Dato che richiede l'uso di righe non condivise, questo tipo di personalizzazione delle celle non è adatto per insiemi di dati di grandi dimensioni. Per ulteriori informazioni sulla condivisione delle righe, vedere [procedure consigliate per la scalabilità del controllo Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
> [!NOTE]
> Quando si deriva dalla classe <xref:System.Windows.Forms.DataGridViewCell> o <xref:System.Windows.Forms.DataGridViewColumn> e si aggiungono nuove proprietà alla classe derivata, accertarsi di eseguire l'override del metodo `Clone` per copiare le nuove proprietà durante le operazioni di clonazione. È anche necessario chiamare il metodo `Clone` della classe base in modo che le proprietà della classe base vengano copiate nella nuova cella o colonna.  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>Per personalizzare celle e colonne nel controllo DataGridView  
  
1. Derivare una nuova classe di cella, denominata `DataGridViewRolloverCell`, dal tipo <xref:System.Windows.Forms.DataGridViewTextBoxCell>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. Eseguire l'override del metodo <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> nella classe `DataGridViewRolloverCell` . Eseguire l'override chiamando prima l'implementazione della classe di base, che gestisce la funzionalità della casella di testo inserita, quindi usando il metodo <xref:System.Windows.Forms.Control.PointToClient%2A> del controllo per trasformare la posizione del cursore (coordinate dello schermo) nelle coordinate dell'area client <xref:System.Windows.Forms.DataGridView>. Se le coordinate del mouse rientrano nei contorni della cella, disegnare il rettangolo interno.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. Eseguire l'override dei metodi <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> e <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> nella classe `DataGridViewRolloverCell` per forzare le celle a ridisegnarsi all'ingresso o all'uscita del mouse.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. Derivare una nuova classe, denominata `DataGridViewRolloverCellColumn`, dal tipo <xref:System.Windows.Forms.DataGridViewColumn>. Nel costruttore assegnare un nuovo oggetto `DataGridViewRolloverCell` alla relativa proprietà <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>Esempio  
 L'esempio di codice completo comprende un piccolo form di prova che illustra il comportamento del tipo di cella personalizzato.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
- Riferimenti agli assembly System, System.Windows.Forms e System.Drawing.  
 
## <a name="see-also"></a>Vedere anche

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Personalizzazione del controllo DataGridView di Windows Form](customizing-the-windows-forms-datagridview-control.md)
- [Architettura del controllo DataGridView](datagridview-control-architecture-windows-forms.md)
- [Tipi di colonne nel controllo DataGridView di Windows Form](column-types-in-the-windows-forms-datagridview-control.md)
- [Procedure consigliate per ridimensionare il controllo DataGridView di Windows Form](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
