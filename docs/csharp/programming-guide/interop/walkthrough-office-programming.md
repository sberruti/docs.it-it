---
title: 'Procedura dettagliata: programmazione di Office (C# e Visual Basic)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
ms.openlocfilehash: 6c27442cb5c0c4172f503c945849e47560c2b33d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635353"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>Procedura dettagliata: programmazione di Office (C# e Visual Basic)

Visual Studio offre funzionalità di C# e Visual Basic che migliorano la programmazione di Microsoft Office. Tra le utili funzionalità di C# sono disponibili gli argomenti denominati e facoltativi e i valori restituiti di tipo `dynamic`. Nella programmazione COM è possibile omettere la parola chiave `ref` e accedere alle proprietà indicizzate. Le funzionalità di Visual Basic includono le proprietà implementate automaticamente, le istruzioni nelle espressioni lambda e gli inizializzatori di insieme.

Entrambi i linguaggi consentono di incorporare informazioni sul tipo, in modo da distribuire gli assembly che interagiscono con i componenti COM senza distribuire assembly di interoperabilità primari (PIA) al computer dell'utente. Per altre informazioni, vedere [Procedura dettagliata: Incorporamento dei tipi da assembly gestiti](../../../standard/assembly/embed-types-visual-studio.md).

In questa procedura dettagliata queste funzionalità vengono illustrate nel contesto della programmazione di Office, ma molte di esse sono utili anche nella programmazione generale. Nella procedura dettagliata si usa un componente aggiuntivo di Excel per creare una cartella di lavoro di Excel. A questo punto si crea un documento di Word contenente un collegamento alla cartella di lavoro. Infine, si visualizzerà come la dipendenza dell'assembly di interoperabilità primario può essere abilitata e disabilitata.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata è necessario aver installato Microsoft Office Excel o Microsoft Office Word nel computer.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-set-up-an-excel-add-in-application"></a>Per impostare un componente aggiuntivo di Excel

1. Avviare Visual Studio.

2. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.

3. Nel riquadro **Modelli installati** espandere **Visual Basic** o **Visual C#** , espandere **Office** e scegliere l'anno della versione del prodotto Office.

4. Nel riquadro **Modelli** fare clic su **Excel \<versione > Componente aggiuntivo**.

5. Verificare che nella parte superiore del riquadro **Modelli** sia visualizzato **.NET Framework 4**, o una versione successiva, nella casella **Framework di destinazione**.

6. Se opportuno, digitare un nome per il progetto nella casella **Nome**.

7. Fare clic su **OK**.

8. Il nuovo progetto verrà visualizzato in **Esplora soluzioni**.

### <a name="to-add-references"></a>Per aggiungere riferimenti

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome del progetto e quindi scegliere **Aggiungi riferimento**. Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.

2. Nella scheda **Assembly** selezionare **Microsoft.Office.Interop.Excel**, versione `<version>.0.0.0` (per conoscere il numero versione del prodotto Office, vedere [Versioni Microsoft](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)) nell'elenco **Nome componente**. Tenere premuto CTRL e selezionare **Microsoft.Office.Interop.Word**, `version <version>.0.0.0`. Se gli assembly non sono visibili, può essere necessario verificare che siano installati e visualizzati (vedere [Procedura: Installare assembly di interoperabilità primari di Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).

3. Fare clic su **OK**.

### <a name="to-add-necessary-imports-statements-or-using-directives"></a>Per aggiungere istruzioni Imports o le direttive using necessarie

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file **ThisAddIn.vb** o **ThisAddIn.cs** e quindi scegliere **Visualizza codice**.

2. Aggiungere le seguenti istruzioni `Imports` (Visual Basic) o direttive `using` (C#) all'inizio del file di codice, se non sono già presenti.

     [!code-csharp[csOfficeWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#1)]

     [!code-vb[csOfficeWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#1)]

### <a name="to-create-a-list-of-bank-accounts"></a>Per creare un elenco di conti correnti bancari

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome del progetto, fare clic su **Aggiungi**e quindi su **Classe**. Denominare la classe Account.vb se si usa Visual Basic, Account.cs se si usa C#. Fare clic su **Aggiungi**.

2. Sostituire la definizione della classe `Account` con il codice seguente. Le definizioni delle classi usano le *proprietà implementate automaticamente*. Per altre informazioni, vedere [Proprietà implementate automaticamente](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).

     [!code-csharp[csOfficeWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/account.cs#2)]

     [!code-vb[csOfficeWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/account.vb#2)]

3. Per creare un elenco `bankAccounts` contenente due conti, aggiungere il codice seguente al metodo `ThisAddIn_Startup` nei file *ThisAddIn.vb* o *ThisAddIn.cs*. Le dichiarazioni dell'elenco usano gli  *inizializzatori di insieme*. Per altre informazioni, vedere [Inizializzatori di insieme](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

     [!code-csharp[csOfficeWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#3)]

     [!code-vb[csOfficeWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#3)]

### <a name="to-export-data-to-excel"></a>Per esportare dati in Excel

1. Nello stesso file, aggiungere il metodo seguente alla classe `ThisAddIn`. Il metodo configura una cartella di lavoro di Excel e vi esporta i dati.

     [!code-csharp[csOfficeWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#4)]

     [!code-vb[csOfficeWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#4)]

     In questo metodo vengono usati due nuove funzionalità di C#. Entrambe queste funzionalità sono già esistenti in Visual Basic.

    - Il metodo [Add](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) usa un *parametro facoltativo* per specificare un modello particolare. I parametri facoltativi, una novità di C# 4, consentono di omettere l'argomento per il parametro se si vuole usare il valore predefinito del parametro. Poiché nessun argomento viene inviato nell'esempio precedente, `Add` usa il modello predefinito e crea una nuova cartella di lavoro. L'istruzione equivalente nelle precedenti versioni di C# richiede un argomento segnaposto: `excelApp.Workbooks.Add(Type.Missing)`.

         Per altre informazioni, vedere [Argomenti denominati e facoltativi](../classes-and-structs/named-and-optional-arguments.md).

    - Le proprietà `Range` e `Offset` dell'oggetto [Range](<xref:Microsoft.Office.Interop.Excel.Range>) usano la funzionalità delle *proprietà indicizzate*. Questa funzionalità consente di usare tali proprietà dai tipi COM con la tipica sintassi di C# seguente. Le proprietà indicizzate consentono anche di usare la proprietà `Value` dell'oggetto `Range`, eliminando la necessità di usare la proprietà `Value2`. La proprietà `Value` è indicizzata, ma l'indice è facoltativo. Nell'esempio seguente sono presenti sia argomenti facoltativi sia proprietà indicizzate.

         [!code-csharp[csOfficeWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#5)]

         Nelle versioni precedenti del linguaggio, è necessaria la seguente sintassi speciale.

         [!code-csharp[csOfficeWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#6)]

         Non è possibile creare proprietà indicizzate personalizzate. La funzionalità supporta solo l'utilizzo di proprietà indicizzate esistenti.

         Per ulteriori informazioni, vedere [come utilizzare le proprietà indicizzate nella programmazione dell'interoperabilità COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md).

2. Aggiungere il seguente codice alla fine di `DisplayInExcel` per regolare la larghezza delle colonne in modo da adattarle al contenuto.

     [!code-csharp[csOfficeWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#7)]

     [!code-vb[csOfficeWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#7)]

     Queste aggiunte dimostrano un'altra nuova funzionalità di C#: considerare i valori `Object` restituiti dagli host COM, ad esempio Office, come se il tipo fosse [dynamic](../../language-reference/builtin-types/reference-types.md). Ciò avviene automaticamente quando l'opzione **Incorpora tipi di interoperabilità** è impostata sul valore predefinito, `True`o, in modo equivalente, quando si fa riferimento all'assembly tramite l'opzione del compilatore [-link](../../language-reference/compiler-options/link-compiler-option.md) . Il tipo `dynamic` consente l'associazione tardiva, già disponibile in Visual Basic, ed evita il cast esplicito richiesto in C# 3.0 e versioni precedenti del linguaggio.

     Ad esempio, `excelApp.Columns[1]` restituisce `Object` e `AutoFit` è un metodo [Range](<xref:Microsoft.Office.Interop.Excel.Range>) di Excel. In assenza di `dynamic`, è necessario eseguire il cast dell'oggetto restituito da `excelApp.Columns[1]` come istanza di `Range` prima di chiamare il metodo `AutoFit`.

     [!code-csharp[csOfficeWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#8)]

     Per altre informazioni sull'incorporamento di tipi di interoperabilità, vedere le procedure "Per trovare il riferimento all'assembly di interoperabilità primari" e "Per ripristinare la dipendenza di assembly di interoperabilità primario" più avanti in questo argomento. Per altre informazioni su `dynamic`, vedere [dynamic](../../language-reference/builtin-types/reference-types.md) o [Uso del tipo dinamico](../types/using-type-dynamic.md).

### <a name="to-invoke-displayinexcel"></a>Per richiamare DisplayInExcel

1. Aggiungere il codice seguente alla fine del metodo `ThisAddIn_StartUp`. La chiamata a `DisplayInExcel` contiene due argomenti. Il primo argomento è il nome dell'elenco di conti da elaborare. Il secondo argomento è un'espressione lambda su più righe che definisce la modalità con cui i dati saranno elaborati. I valori `ID` e `balance` per ogni conto vengono visualizzati in celle adiacenti e la riga viene visualizzata in rosso se il saldo è inferiore a zero. Per altre informazioni, vedere [Espressioni lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

     [!code-csharp[csOfficeWalkthrough#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#9)]

     [!code-vb[csOfficeWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#9)]

2. Premere F5 per eseguire il programma. Viene visualizzato un foglio di lavoro di Excel che contiene i dati dei conti.

### <a name="to-add-a-word-document"></a>Per aggiungere un documento di Word

1. Aggiungere il seguente codice alla fine del metodo `ThisAddIn_StartUp` per creare un documento di Word contenente un collegamento alla cartella di lavoro di Excel.

     [!code-csharp[csOfficeWalkthrough#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#10)]

     [!code-vb[csOfficeWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#10)]

     In questo codice vengono illustrate diverse nuove funzionalità di C#: la possibilità di omettere la parola chiave `ref` nella programmazione COM, gli argomenti denominati e gli argomenti facoltativi. Queste funzionalità sono già esistenti in Visual Basic. Il metodo [PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) ha sette parametri, ognuno dei quali è definito come parametro per riferimento facoltativo. Gli argomenti denominati e facoltativi consentono di indicare i parametri a cui si vuol accedere per nome e di inviare argomenti solo a tali parametri. In questo esempio gli argomenti vengono inviati per indicare che deve essere creato un collegamento alla cartella di lavoro negli Appunti (parametro `Link`), e che il collegamento deve essere visualizzato nel documento di Word come icona (parametro `DisplayAsIcon`). Visual C# consente anche di omettere la parola chiave `ref` per questi argomenti.

### <a name="to-run-the-application"></a>Per eseguire l'applicazione

1. Premere F5 per eseguire l'applicazione. Excel viene avviato e viene visualizzata una tabella che contiene le informazioni dei due conti in `bankAccounts`. Quindi verrà visualizzato un documento di Word contenente un collegamento alla tabella di Excel.

### <a name="to-clean-up-the-completed-project"></a>Per pulire il progetto completato

1. In Visual Studio fare clic su **Pulisci soluzione** nel menu **Compila**. In caso contrario, il componente aggiuntivo verrà eseguito ogni volta che si apre Excel nel computer.

### <a name="to-find-the-pia-reference"></a>Per trovare il riferimento all'assembly di interoperabilità primario

1. Eseguire nuovamente l'applicazione, ma non fare clic su **Pulisci soluzione**.

2. Selezionare **Start**. Individuare **Microsoft Visual Studio \<versione >** e aprire un prompt dei comandi per gli sviluppatori.

3. Digitare `ildasm` nella finestra del Prompt dei comandi per gli sviluppatori di Visual Studio e premere INVIO. Verrà visualizzata la finestra IL DASM.

4. Nel menu **File** della finestra IL DASM selezionare **File** > **Apri**. Fare doppio clic su **Visual Studio \<versione>** e su **Progetti**. Aprire la cartella per il progetto e cercare nella cartella bin/Debug il file *nome progetto*.dll. Fare doppio clic su *nome progetto*.dll. Una nuova finestra consente di visualizzare gli attributi del progetto, oltre ai riferimenti ad altri moduli e assembly. Notare che gli spazi dei nomi `Microsoft.Office.Interop.Excel` e `Microsoft.Office.Interop.Word` sono inclusi nell'assembly. Per impostazione predefinita in Visual Studio, il compilatore importa i tipi necessari da un assembly di interoperabilità primario a cui si fa riferimento nell'assembly.

     Per altre informazioni, vedere [Procedura: Visualizzare il contenuto dell'assembly](../../../standard/assembly/view-contents.md).

5. Fare doppio clic sull'icona **MANIFESTO**. Viene visualizzata una finestra che include un elenco di assembly che contengono gli elementi a cui fa riferimento il progetto. `Microsoft.Office.Interop.Excel` e `Microsoft.Office.Interop.Word` non sono inclusi nell'elenco. Poiché i tipi che è necessario importare nell'assembly per il progetto, i riferimenti a un assembly di interoperabilità primario non sono necessari. Ciò rende più semplice la distribuzione. Gli assembly di interoperabilità primari non devono essere presenti nel computer dell'utente e, poiché un'applicazione non richiede la distribuzione di una versione specifica di un assembly di interoperabilità primario, è possibile progettare applicazioni compatibili con più versioni di Office, a condizione che le API necessarie siano presenti in tutte le versioni.

     Poiché la distribuzione di assembly di interoperabilità primari non è più necessaria, è possibile creare un'applicazione in scenari avanzati che sia compatibile con più versioni di Office, incluse le versioni precedenti. Tuttavia, questo metodo funziona solo se il codice non usa alcuna API che non sia disponibile nella versione di Office che si sta usando. Non è sempre chiaro se una particolare API fosse disponibile in una versione precedente e per tale motivo l'utilizzo di versioni precedenti di Office non è consigliato.

    > [!NOTE]
    > Non sono stati pubblicati PIA prima di Office 2003. Di conseguenza, l'unico modo per generare un assembly di interoperabilità per Office 2002 o versioni precedenti consiste nell'importare il riferimento COM.

6. Chiudere la finestra del manifesto e l'assembly.

### <a name="to-restore-the-pia-dependency"></a>Per ripristinare la dipendenza di assembly di interoperabilità primario

1. In **Esplora soluzioni** fare clic sul pulsante **Mostra tutti i file**. Espandere la cartella **Riferimenti** e scegliere **Microsoft.Office.Interop.Excel**. Premere F4 per visualizzare la finestra **Proprietà**.

2. Nella finestra **Proprietà** impostare la proprietà **Incorpora tipi di interoperabilità** da **True** a **False**.

3. Ripetere i passaggi 1 e 2 di questa procedura per `Microsoft.Office.Interop.Word`.

4. In C#, commentare le due chiamate `Autofit` alla fine del metodo `DisplayInExcel`.

5. Premere F5 per verificare che il progetto sia ancora eseguito correttamente.

6. Ripetere i passaggi da 1 a 3 della procedura precedente per aprire la finestra dell'assembly. Notare che `Microsoft.Office.Interop.Word` e `Microsoft.Office.Interop.Excel` non sono più presenti nell'elenco di assembly incorporati.

7. Fare doppio clic sull'icona **MANIFESTO** e scorrere l'elenco degli assembly di riferimento. Sia `Microsoft.Office.Interop.Word` sia `Microsoft.Office.Interop.Excel` sono inclusi nell'elenco. Poiché l'applicazione fa riferimento agli assembly di interoperabilità primari di Excel e Word e la proprietà **Incorpora tipi di interoperabilità** è impostata su **False**, entrambi gli assembly devono esistere nel computer dell'utente finale.

8. In Visual Studio fare clic su **Pulisci soluzione** nel menu **Compila** per pulire il progetto completato.

## <a name="see-also"></a>Vedere anche

- [Proprietà implementate automaticamente (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Proprietà implementate automaticamente (C#)](../classes-and-structs/auto-implemented-properties.md)
- [Inizializzatori di raccolta](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Inizializzatori di oggetto e di raccolta](../classes-and-structs/object-and-collection-initializers.md)
- [Parametri facoltativi](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [Passaggio di argomenti in base alla posizione e al nome](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)
- [Argomenti denominati e facoltativi](../classes-and-structs/named-and-optional-arguments.md)
- [Associazione anticipata e tardiva](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Uso del tipo dinamico](../types/using-type-dynamic.md)
- [Espressioni lambda (Visual Basic)](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Espressioni lambda (C#)](../statements-expressions-operators/lambda-expressions.md)
- [Come usare le proprietà indicizzate nella programmazione dell'interoperabilità COM](./how-to-use-indexed-properties-in-com-interop-rogramming.md)
- [Procedura dettagliata: Incorporamento delle informazioni sui tipi da assembly di Microsoft Office in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ee317478(v%3dvs.120))
- [Procedura dettagliata: Incorporamento dei tipi da assembly gestiti](../../../standard/assembly/embed-types-visual-studio.md)
- [Procedura dettagliata: creazione del primo componente aggiuntivo VSTO per Excel](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)
- [Interoperabilità COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Interoperabilità](./index.md)
