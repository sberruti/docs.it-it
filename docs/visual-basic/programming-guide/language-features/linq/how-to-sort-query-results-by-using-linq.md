---
title: 'Procedura: ordinare i risultati di una query tramite LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- sorting query results, multiple columns
- sorting data [Visual Basic]
- sorting data [LINQ in Visual Basic]
- sorting query results [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], sorting results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 07a4584d-9fd8-4a1d-b7d9-ccf2efa5c84e
ms.openlocfilehash: 020e4a3800515329b29e2941baf50d3d8add4605
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354161"
---
# <a name="how-to-sort-query-results-by-using-linq-visual-basic"></a>Procedura: ordinare i risultati di query utilizzando LINQ (Visual Basic)
LINQ (Language-Integrated Query) consente di accedere facilmente alle informazioni sul database ed eseguire query.  
  
 Nell'esempio seguente viene illustrato come creare una nuova applicazione che esegue query su un database di SQL Server e ordina i risultati in base a più campi utilizzando la clausola `Order By`. Il tipo di ordinamento per ogni campo può essere ordine crescente o decrescente. Per ulteriori informazioni, vedere [clausola ORDER BY](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Negli esempi di questo argomento viene utilizzato il database di esempio Northwind. Se questo database non è presente nel computer di sviluppo, è possibile scaricarlo dal Microsoft Download Center. Per istruzioni, vedere [download di database di esempio](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Per creare una connessione a un database  
  
1. In Visual Studio aprire **Esplora server**/**Esplora database** scegliendo **Esplora server**/**Esplora database** dal menu **Visualizza** .  
  
2. Fare clic con il pulsante destro del mouse su **connessioni dati** in **Esplora server**/**Esplora database** , quindi scegliere **Aggiungi connessione**.  
  
3. Specificare una connessione valida al database di esempio Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Per aggiungere un progetto che contiene un file di LINQ to SQL  
  
1. In Visual Studio scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**. Selezionare Visual Basic **Windows Forms applicazione** come tipo di progetto.  
  
2. Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**. Selezionare il modello di elemento **classi LINQ to SQL** .  
  
3. Denominare il file `northwind.dbml`. Fare clic su **Add**. Il Object Relational Designer (O/R Designer) viene aperto per il file Northwind. dbml.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>Per aggiungere tabelle a query in Progettazione relazionale di O/R  
  
1. In **Esplora server**/**Esplora database**espandere la connessione al database Northwind. Espandere la cartella **tabelle** .  
  
     Se la finestra di progettazione di O/R è stata chiusa, è possibile riaprirla facendo doppio clic sul file Northwind. dbml aggiunto in precedenza.  
  
2. Fare clic sulla tabella Customers e trascinarla nel riquadro sinistro della finestra di progettazione. Fare clic sulla tabella Orders e trascinarlo nel riquadro sinistro della finestra di progettazione.  
  
     La finestra di progettazione crea nuovi oggetti `Customer` e `Order` per il progetto. Si noti che la finestra di progettazione rileva automaticamente le relazioni tra le tabelle e crea le proprietà figlio per gli oggetti correlati. Ad esempio, IntelliSense indicherà che l'oggetto `Customer` dispone di una proprietà `Orders` per tutti gli ordini correlati a tale cliente.  
  
3. Salvare le modifiche e chiudere la finestra di progettazione.  
  
4. Salvare il progetto.  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>Per aggiungere codice per eseguire query sul database e visualizzare i risultati  
  
1. Dalla **casella degli strumenti**trascinare un controllo <xref:System.Windows.Forms.DataGridView> nel Windows Form predefinito per il progetto Form1.  
  
2. Fare doppio clic su Form1 per aggiungere codice all'evento `Load` del modulo.  
  
3. Quando sono state aggiunte tabelle a Progettazione relazionale oggetti, nella finestra di progettazione è stato aggiunto un oggetto <xref:System.Data.Linq.DataContext> al progetto. Questo oggetto contiene il codice necessario per accedere a tali tabelle e per accedere a oggetti e raccolte singoli per ogni tabella. L'oggetto <xref:System.Data.Linq.DataContext> per il progetto viene denominato in base al nome del file con estensione dbml. Per questo progetto, l'oggetto <xref:System.Data.Linq.DataContext> è denominato `northwindDataContext`.  
  
     È possibile creare un'istanza del <xref:System.Data.Linq.DataContext> nel codice ed eseguire una query sulle tabelle specificate da O/R Designer.  
  
     Aggiungere il codice seguente all'evento `Load` per eseguire una query sulle tabelle esposte come proprietà del contesto dati e ordinare i risultati. La query ordina i risultati in base al numero di ordini dei clienti, in ordine decrescente. I clienti che hanno lo stesso numero di ordini sono ordinati in base al nome della società in ordine crescente (impostazione predefinita).  
  
     [!code-vb[VbLINQToSQLHowTos#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form4.vb#10)]  
  
4. Premere F5 per eseguire il progetto e visualizzare i risultati.  
  
## <a name="see-also"></a>Vedere anche

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Query](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Metodi DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
