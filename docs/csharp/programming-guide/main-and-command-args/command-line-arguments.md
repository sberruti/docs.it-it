---
title: Argomenti della riga di comando - Guida per programmatori C#
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: d6775263e6f1afb227aa263b01d60f5181da74f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093510"
---
# <a name="command-line-arguments-c-programming-guide"></a>Argomenti della riga di comando (Guida per programmatori C#)

È possibile inviare argomenti al metodo `Main` definendo il metodo in uno dei modi seguenti:

[!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  

[!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]

> [!NOTE]
> Per abilitare gli argomenti `Main` della riga di comando nel metodo in `Main` un'applicazione Windows Form, è necessario modificare manualmente la firma di in *program.cs*. Il codice generato da Progettazione Windows Form crea un `Main` senza un parametro di input. È anche possibile usare <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> o <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> per accedere agli argomenti della riga di comando da qualsiasi punto in un'applicazione console o Windows.

Il parametro del metodo `Main` è una matrice <xref:System.String> che rappresenta gli argomenti della riga di comando. In genere si determina se gli argomenti esistono eseguendo il test della proprietà `Length`, ad esempio:

[!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]

È anche possibile convertire gli argomenti stringa in tipi numerici con la classe <xref:System.Convert> o il metodo `Parse`. Ad esempio, l'istruzione seguente converte `string` in un numero `long` con il metodo <xref:System.Int64.Parse%2A>:

```csharp
long num = Int64.Parse(args[0]);
```

È anche possibile usare il tipo C# `long`, che fa da alias per `Int64`:

```csharp
long num = long.Parse(args[0]);
```

Nella classe `Convert` il metodo `ToInt64` consente di eseguire la stessa operazione:

```csharp
long num = Convert.ToInt64(s);
```

Per altre informazioni, vedere <xref:System.Int64.Parse%2A> e <xref:System.Convert>.

## <a name="example"></a>Esempio

L'esempio seguente illustra come usare gli argomenti della riga di comando in un'applicazione console. L'applicazione accetta un argomento in fase di esecuzione, lo converte in un numero intero e calcola il fattoriale del numero. Se non viene specificato nessun argomento, l'applicazione produce un messaggio che descrive l'uso corretto del programma.

Per compilare ed eseguire l'applicazione al prompt dei comandi, seguire questa procedura:

1. Incollare il codice seguente in qualsiasi editor di testo, quindi salvare il file come file di testo con il nome *Factorial.cs*.

     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]

2. Dalla schermata **Start** o dal menu **Start**, aprire una finestra **Prompt dei comandi per gli sviluppatori** di Visual Studio e selezionare la cartella contenente il file appena creato.

3. Immettere il seguente comando per compilare l'applicazione.
  
     `csc Factorial.cs`  
  
     Se l'applicazione non contiene errori di compilazione, viene creato un file eseguibile denominato *Factorial.exe.If* your application has no compilation errors, an executable file that's named Factorial.exe is created.
  
4. Immettere il comando seguente per calcolare il fattoriale di 3:
  
     `Factorial 3`  
  
5. Il comando produce il seguente output: `The factorial of 3 is 6.`

> [!NOTE]
> Quando si esegue un'applicazione in Visual Studio, è possibile specificare argomenti della riga di comando nella [Pagina Debug, Progettazione progetti](/visualstudio/ide/reference/debug-page-project-designer).

## <a name="see-also"></a>Vedere anche

- <xref:System.Environment?displayProperty=nameWithType>
- [Guida per programmatori C#](../index.md)
- [Main() e argomenti della riga di comando](index.md)
- [Come visualizzare gli argomenti della riga di comando](how-to-display-command-line-arguments.md)
- [Valori restituiti da Main()](main-return-values.md)
- [Classi](../classes-and-structs/classes.md)
