---
title: Tipi riferimento nullable
description: In questo articolo viene fornita una panoramica dei tipi di riferimento nullable, aggiunti in C . Si apprenderà come la funzionalità offra sicurezza contro le eccezioni dei riferimenti Null, per progetti nuovi ed esistenti.
ms.technology: csharp-null-safety
ms.date: 02/19/2019
ms.openlocfilehash: bb4c2b6951a38eeb705c7de50ef5d9645350e336
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399427"
---
# <a name="nullable-reference-types"></a>Tipi riferimento nullable

In C# 8.0 sono stati introdotti i **tipi riferimento nullable** e i **tipi riferimento non nullable** che consentono di creare istruzioni importanti sulle proprietà delle variabili dei tipi riferimento:

- **Non si presume che un riferimento sia Null**. Quando le variabili non devono essere Null, il compilatore applica regole che garantiscono che sia sicuro dereferenziare queste variabili senza prima controllare che non siano Null:
  - La variabile deve essere inizializzata come valore non Null.
  - Alla variabile non può mai essere assegnato il valore `null`.
- **Un riferimento potrebbe essere Null**. Quando le variabili possono essere Null, il compilatore applica regole diverse per assicurarsi che sia stata verificata correttamente la presenza di un riferimento Null:
  - La variabile può essere dereferenziata solo quando il compilatore può garantire che il valore non sia Null.
  - Queste variabili possono essere inizializzate con il valore predefinito `null` e possono ricevere l'assegnazione del valore `null` in un altro codice.

Questa nuova funzionalità offre vantaggi significativi rispetto alla gestione delle variabili di riferimento nelle versioni precedenti di C# in cui la finalità della progettazione non poteva essere determinata dalla dichiarazione di variabile. Il compilatore non offriva sicurezza contro le eccezioni dei riferimenti Null per i tipi riferimento:

- **Un riferimento può essere Null**. Non viene generato alcun avviso quando un tipo di riferimento viene inizializzato su null o null viene successivamente assegnato.
- **Si suppone che un riferimento sia non Null**. Il compilatore non genera avvisi quando i tipi riferimento sono dereferenziati. Con i riferimenti nullable, il compilatore genera avvisi quando si dereferenzia una variabile che potrebbe essere Null.

Con l'aggiunta di tipi riferimento nullable, è possibile dichiarare in modo più chiaro la finalità. Il valore `null` è il modo corretto di indicare che una variabile non fa riferimento a un valore. Non usare questa funzionalità per rimuovere tutti i valori `null` dal codice. È invece consigliabile dichiarare la finalità al compilatore e agli altri sviluppatori che leggono il codice. Dichiarando la finalità, il compilatore informa l'utente quando scrive codice non coerente con tale finalità.

Viene inserita una nota in un **tipo riferimento nullable** usando la stessa sintassi dei [tipi valore nullable](language-reference/builtin-types/nullable-value-types.md): viene aggiunto `?` al tipo della variabile. La dichiarazione della variabile seguente, ad esempio, rappresenta una variabile di stringa nullable, `name`:

```csharp
string? name;
```

Le variabili in cui `?` non viene aggiunto al nome del tipo sono **tipi riferimento non nullable**, incluse tutte le variabili dei tipi riferimento nel codice esistente quando questa funzionalità è abilitata.

Il compilatore usa l'analisi statica per determinare se un riferimento nullable è notoriamente non null. Il compilatore genera un avviso se si dereferenzia un riferimento nullable quando potrebbe essere null. È possibile eseguire l'override di questo comportamento utilizzando l'operatore `!` di [perdono null](language-reference/operators/null-forgiving.md) dopo un nome di variabile. Se ad esempio si è certi che la variabile `name` non sia Null, ma il compilatore genera un avviso, è possibile scrivere il codice seguente per eseguire l'override dell'analisi del compilatore:

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Supporto dei valori Null dei tipi

Qualsiasi tipo riferimento può avere una delle quattro tipologie di *supporto dei valori Null*, che descrive quando vengono generati gli avvisi:

- *Nonnullable*: Null non può essere assegnato a variabili di questo tipo. Non è necessario verificare la presenza di valori Null nelle variabili di questo tipo prima della dereferenziazione.
- *Nullable*: Null può essere assegnato a variabili di questo tipo. Se si dereferenziano le variabili di questo tipo senza prima verificare la presenza di valori `null`, viene generato un avviso.
- *Oblivious*: Questo è lo stato precedente a C . Le variabili di questo tipo possono essere dereferenziate o assegnate senza avvisi.
- *Sconosciuto*: In genere per i parametri di tipo in cui i vincoli non indicano al compilatore che il tipo deve essere *nullable* o *non nullable.*

Il supporto dei valori Null di un tipo in una dichiarazione di variabile viene controllato dal *contesto nullable* in cui viene dichiarata la variabile.

## <a name="nullable-contexts"></a>Contesti nullable

I contesti nullable consentono il controllo con granularità fine di come il compilatore interpreta le variabili dei tipi riferimento. Il contesto di **annotazione nullable** di qualsiasi riga di origine specificata è abilitato o disabilitato. È possibile pensare al compilatore precedente a C , 8.0 come la compilazione di tutto il codice in un contesto nullable disabilitato: qualsiasi tipo di riferimento può essere null. Il **contesto degli avvisi nullable** può anche essere abilitato o disabilitato. Il contesto degli avvisi nullable specifica gli avvisi generati dal compilatore usando l'analisi del flusso.

Il contesto di annotazione nullable e il contesto di avviso nullable possono essere impostati per un progetto usando l'elemento `Nullable` nel file con estensione *csproj.* Questo elemento configura come il compilatore interpreta il supporto dei valori Null dei tipi e quali avvisi vengono generati. Le impostazioni valide sono:

- `enable`: il contesto di annotazione nullable è **abilitato.** Il contesto dell'avviso nullable è **enabled**.
  - Le variabili di un tipo riferimento, ad esempio `string`, sono non nullable.  Tutti gli avvisi relativi al supporto dei valori Null sono abilitati.
- `warnings`: il contesto di annotazione nullable è **disabilitato.** Il contesto dell'avviso nullable è **enabled**.
  - Le variabili di un tipo riferimento sono indipendenti dai valori. Tutti gli avvisi relativi al supporto dei valori Null sono abilitati.
- `annotations`: il contesto di annotazione nullable è **abilitato.** Il contesto dell'avviso nullable è **disabled**.
  - Le variabili di un tipo di riferimento, ad esempio string, non sono nullable. Tutti gli avvisi relativi al supporto dei valori Null sono disabilitati.
- `disable`: il contesto di annotazione nullable è **disabilitato.** Il contesto dell'avviso nullable è **disabled**.
  - Le variabili di un tipo riferimento sono indipendenti dai valori, come nelle versioni precedenti di C#. Tutti gli avvisi relativi al supporto dei valori Null sono disabilitati.

**Esempio**:

```xml
<Nullable>enable</Nullable>
```

È anche possibile usare le direttive per impostare questi stessi contesti ovunque nel progetto:

- `#nullable enable`: imposta il contesto di annotazione nullable e il contesto di avviso nullable su **enabled**.
- `#nullable disable`: imposta il contesto di annotazione nullable e il contesto di avviso nullable su **disabled**.
- `#nullable restore`: ripristina il contesto di annotazione nullable e il contesto di avviso nullable alle impostazioni del progetto.
- `#nullable disable warnings`: imposta il contesto di avviso nullable su **disabled**.
- `#nullable enable warnings`: imposta il contesto di avviso nullable su **enabled**.
- `#nullable restore warnings`: ripristina il contesto di avviso nullable alle impostazioni del progetto.
- `#nullable disable annotations`: imposta il contesto di annotazione nullable su **disabled**.
- `#nullable enable annotations`: imposta il contesto di annotazione nullable su **enabled**.
- `#nullable restore annotations`: ripristina il contesto di avviso di annotazione alle impostazioni del progetto.

Per impostazione predefinita, i contesti di annotazione e avviso nullable sono **disabilitati.** Ciò significa che il codice esistente viene compilato senza modifiche e senza generare nuovi avvisi.

## <a name="nullable-annotation-context"></a>Contesto dell'annotazione nullable

Il compilatore usa le regole seguenti in un contesto di annotazione nullable disabilitato:

- Non è possibile dichiarare riferimenti nullable in un contesto disabilitato.
- A tutte le variabili di riferimento può essere assegnato un valore null.
- Non vengono generati avvisi quando una variabile di un tipo riferimento viene dereferenziata.
- L'operatore null-forgiving non può essere usato in un contesto disabilitato.

Il comportamento è lo stesso delle versioni precedenti di C#.

Il compilatore usa le regole seguenti in un contesto di annotazione nullable abilitato:

- Qualsiasi variabile di un tipo riferimento è un **riferimento non nullable**.
- Qualsiasi riferimento non nullable può essere dereferenziato in modo sicuro.
- Qualsiasi tipo riferimento nullable (indicato da `?` dopo il tipo nella dichiarazione della variabile) può essere null. L'analisi statica determina se il valore è non null quando viene dereferenziato. In caso contrario, il compilatore genera un avviso.
- È possibile usare l'operatore null-forgiving per dichiarare che un riferimento nullable non è Null.

In un contesto di annotazione nullable abilitato il carattere `?` aggiunto al tipo riferimento dichiara un **tipo riferimento nullable**. **L'operatore** `!` di perdono null può essere aggiunto a un'espressione per dichiarare che l'espressione non è null.

## <a name="nullable-warning-context"></a>Contesto dell'avviso nullable

Il contesto dell'avviso nullable è diverso dal contesto dell'annotazione nullable. Gli avvisi possono essere abilitati anche quando le nuove annotazioni sono disabilitate. Il compilatore usa l'analisi statica del flusso per determinare lo **stato null** di qualsiasi riferimento. Lo stato null è **not null** o **maybe null** quando il *contesto dell'avviso nullable* non è **disabled**. Se si dereferenzia un riferimento quando il compilatore ha determinato che è **maybe null**, il compilatore genera un avviso. Lo stato di un riferimento è **maybe null** a meno che il compilatore non riesca a determinare una di due condizioni:

1. La variabile è stata assegnata in modo definito a un valore non null.
1. La variabile o l'espressione è stata confrontata con null prima di dereferenziarla.

Il compilatore genera avvisi ogni volta che si dereferenzia una variabile o un'espressione in uno stato **forse null** quando è abilitato il contesto di avviso nullable. Inoltre, gli avvisi vengono generati quando una variabile o un'espressione **forse null** viene assegnata a un tipo di riferimento non nullable in un contesto di annotazione nullable abilitato.

## <a name="see-also"></a>Vedere anche

- [Specifica dei tipi di riferimento nullable Draft nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Introduzione all'esercitazione sui riferimenti nullable](tutorials/nullable-reference-types.md)
- [Eseguire la migrazione di una base di codice esistente a riferimenti nullable](tutorials/upgrade-to-nullable-references.md)
