---
title: System.Delegate e la parola chiave `delegate`
description: Informazioni sulle classi in .NET che supportano i delegati e su come tali informazioni vengono mappate alla parola chiave 'delegate'.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.openlocfilehash: 87fdf19c4ea810c5ac4409fe16c3cba9d5fc6574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146281"
---
# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate e la parola chiave `delegate`

[Indietro](delegates-overview.md)

In questo articolo vengono illustrate le classi in .NET `delegate` che supportano i delegati e come eseguire il mapping di tali argomenti alla parola chiave.

## <a name="define-delegate-types"></a>Definire i tipi delegati

Iniziamo con la parola chiave "delegate" che è essenzialmente quello che si userà per lavorare con i delegati. Il codice che il compilatore genera quando si usa la parola chiave `delegate` eseguirà il mapping alle chiamate ai metodi che richiamano i membri delle classi <xref:System.Delegate> e <xref:System.MulticastDelegate>.

Per definire un tipo delegato si usa una sintassi simile alla definizione di una firma di metodo. È sufficiente aggiungere la parola chiave `delegate` alla definizione.

Si continuerà a usare il metodo List.Sort() come esempio. Il primo passaggio consiste nel creare un tipo per il delegato di confronto:

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

Il compilatore genera una classe, derivata da `System.Delegate` che corrisponde alla firma usata (in questo caso, un metodo che restituisce un valore integer e ha due argomenti). Il tipo di quel delegato è `Comparison`. Il tipo delegato `Comparison` è un tipo generico. Per informazioni dettagliate sui generics, vedere [qui](programming-guide/generics/index.md).

Si noti che può sembrare che la sintassi dichiari una variabile, ma in effetti viene dichiarato un *tipo*. È possibile definire tipi delegato all'interno di classi, direttamente all'interno di spazi dei nomi o anche nello spazio dei nomi globale.

> [!NOTE]
> La dichiarazione di tipi delegato (o altri tipi) direttamente nello spazio dei nomi globale non è consigliata.

Il compilatore genera anche gestori di aggiunta e rimozione per questo nuovo tipo in modo che i client di questa classe siano in grado di aggiungere e rimuovere metodi dall'elenco delle chiamate di un'istanza. Il compilatore impone che la firma del metodo aggiunto o rimosso corrisponda alla firma usata per la dichiarazione del metodo.

## <a name="declare-instances-of-delegates"></a>Dichiarare istanze di delegatiDeclare instances of delegates

Dopo aver definito il delegato è possibile creare un'istanza di quel tipo.
Come per tutte le variabili in C#, non è possibile dichiarare le istanze di delegato direttamente in uno spazio dei nomi o nello spazio dei nomi globale.

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

Il tipo della variabile è `Comparison<T>`, il tipo delegato definito in precedenza. Il nome della variabile è `comparator`.

 Il frammento di codice riportato sopra dichiara una variabile membro all'interno di una classe. È anche possibile dichiarare variabili delegato che sono variabili locali o argomenti per i metodi.

## <a name="invoke-delegates"></a>Richiamare delegati

Per richiamare i metodi inclusi nell'elenco chiamate di un delegato, chiamare quel delegato. All'interno del metodo `Sort()` il codice chiamerà il metodo di confronto per determinare l'ordine in cui inserire gli oggetti:

```csharp
int result = comparator(left, right);
```

Nella riga precedente il codice *richiama* il metodo associato al delegato.
La variabile viene trattata come nome di metodo e per richiamarla viene usata usando la sintassi di chiamata di metodo normale.

Quella riga di codice presuppone che non esista alcuna garanzia che una destinazione sia stata aggiunta al delegato. Se non sono state associate destinazioni, la riga precedente causerebbe la generazione di `NullReferenceException`. Gli idiomi usati per risolvere questo problema sono più complessi rispetto a un semplice controllo null e sono trattati più avanti in questa [serie](delegates-patterns.md).

## <a name="assign-add-and-remove-invocation-targets"></a>Assegnare, aggiungere e rimuovere destinazioni di chiamataAssign, add, and remove invocation targets

Questo è il modo in cui viene definito un tipo delegato e in cui le istanze dei delegati vengono dichiarate e richiamate.

Gli sviluppatori che vogliono usare il metodo `List.Sort()` devono definire un metodo la cui firma corrisponda alla definizione di tipo delegato e assegnare il metodo al delegato usato dal metodo di ordinamento. Questa assegnazione consente di aggiungere il metodo all'elenco delle chiamate dell'oggetto delegato.

Si supponga di voler ordinare un elenco di stringhe in base alla lunghezza. La funzione di confronto potrebbe essere la seguente:

```csharp
private static int CompareLength(string left, string right) =>
    left.Length.CompareTo(right.Length);
```

Il metodo viene dichiarato come metodo privato. Va bene. Può essere opportuno evitare che questo metodo sia parte dell'interfaccia pubblica. Può comunque essere usato come metodo di confronto se collegato a un delegato. Il codice chiamante avrà questo metodo associato all'elenco di destinazione dell'oggetto delegato e potrà accedere usando quel delegato.

La relazione si crea passando tale metodo al metodo `List.Sort()`:

```csharp
phrases.Sort(CompareLength);
```

Si noti che viene usato il nome del metodo, senza parentesi. L'uso del metodo come argomento indica al compilatore di convertire il riferimento al metodo in un riferimento che possa essere usato come destinazione della chiamata al delegato e di associare tale metodo come destinazione di chiamata.

Si può anche procedere in modo esplicito dichiarando una variabile di tipo `Comparison<string>` ed eseguendo un'assegnazione:

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

Quando il metodo usato come destinazione di delegato è un metodo piccolo spesso si usa la sintassi dell'[espressione lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) per eseguire l'assegnazione:

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

L'utilizzo delle espressioni lambda per le destinazioni dei delegati è illustrato più avanti in una [sezione successiva.](delegates-patterns.md)

L'esempio Sort() di solito associa un singolo metodo di destinazione al delegato. Tuttavia, gli oggetti delegati supportano gli elenchi delle chiamate con più metodi di destinazione associati a un oggetto delegato.

## <a name="delegate-and-multicastdelegate-classes"></a>Classi Delegate e MulticastDelegate

Il supporto del linguaggio descritto in precedenza offre le funzionalità e il supporto in genere necessari quando si lavora con i delegati. Tali funzionalità si basano su due classi di .NET Core Framework: <xref:System.Delegate> e <xref:System.MulticastDelegate>.

La `System.Delegate` classe e la relativa `System.MulticastDelegate`singola sottoclasse diretta, , forniscono il supporto del framework per la creazione di delegati, la registrazione dei metodi come destinazioni del delegato e la chiamata di tutti i metodi registrati come destinazione del delegato.

È interessante notare che le classi `System.Delegate` e `System.MulticastDelegate` non sono tipi di delegati. Offrono la base per tutti i tipi di delegati specifici. Lo stesso processo di progettazione del linguaggio stabilisce che non è possibile dichiarare una classe che derivi da `Delegate` o `MulticastDelegate`. Le regole del linguaggio C# lo proibiscono.

Al contrario, il compilatore C# crea istanze di una classe derivata da `MulticastDelegate` quando si usa la parola chiave del linguaggio C# per dichiarare i tipi di delegati.

Questa progettazione ha le sue radici nella prima versione di C# e .NET. Uno degli obiettivi per il team di progettazione era assicurarsi che il linguaggio applicasse l'indipendenza dai tipi nell'uso dei delegati. Ciò significava garantire che i delegati venissero richiamati con il tipo e il numero di argomenti corretti. E che ogni tipo restituito fosse correttamente indicato in fase di compilazione. I delegati facevano parte della versione 1.0 di .NET, precedente ai generics.

Il modo migliore di applicare l'indipendenza dai tipi per il compilatore era creare le classi delegate concrete che rappresentavano la firma del metodo in uso.

Anche se non è possibile creare direttamente le classi derivate, vengono usati i metodi definiti per queste classi. Vediamo quali sono i metodi più comuni da usare quando si lavora con i delegati.

Il primo è più importante aspetto da ricordare è che ogni delegato con cui si lavora è derivato da `MulticastDelegate`. Un delegato multicast significa che si possono richiamare più destinazioni di metodo quando la chiamata è effettuata attraverso un delegato. Nella progettazione originale si è ritenuto utile distinguere i delegati in cui era possibile associare e richiamare un solo metodo di destinazione dai delegati in cui era possibile associare e richiamare più metodi di destinazione. Tale distinzione si è rivelata in pratica meno utile del previsto. Le due classi differenti erano già state create e sono rimaste nel framework dalla versione pubblica iniziale.

I metodi che si usano più di frequente con i delegati sono `Invoke()` e `BeginInvoke()` / `EndInvoke()`. `Invoke()` richiamerà tutti i metodi che sono stati associati a un'istanza particolare del delegato. Come osservato in precedenza, in genere i delegati vengono richiamati usando la sintassi di chiamata di metodo per la variabile delegato. Come si vedrà [più avanti in questa serie](delegates-patterns.md), sono disponibili modelli che funzionano direttamente con questi metodi.

Ora che hai visto la sintassi del linguaggio e le classi che supportano i delegati, esaminiamo come vengono utilizzati, creati e richiamati fortemente i delegati tipati.

[Avanti](delegates-strongly-typed.md)
