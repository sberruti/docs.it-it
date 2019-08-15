---
title: Uso delle classi di enumerazione anziché dei tipi enum
description: Architettura di microservizi .NET per applicazioni .NET in contenitori | Informazioni su come è possibile usare le classi di enumerazione anziché i tipi enum per risolvere alcune limitazioni di questi tipi.
ms.date: 10/08/2018
ms.openlocfilehash: 10b4c2f7b9f079ed535111e65b8154791f6575cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674188"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="666c9-103">Usare le classi di enumerazione anziché i tipi enum</span><span class="sxs-lookup"><span data-stu-id="666c9-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="666c9-104">Le [enumerazioni](../../../../docs/csharp/language-reference/keywords/enum.md) (o *tipi enum*) sono un sottile wrapper del linguaggio per un tipo integrale.</span><span class="sxs-lookup"><span data-stu-id="666c9-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="666c9-105">È possibile limitarne l'uso quando si archivia un valore da un set di valori chiuso.</span><span class="sxs-lookup"><span data-stu-id="666c9-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="666c9-106">La classificazione in base alle dimensioni (piccole, medie e grandi) rappresenta un buon esempio.</span><span class="sxs-lookup"><span data-stu-id="666c9-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="666c9-107">L'uso delle enumerazioni per il flusso di controllo o per astrazioni più potenti può indicare difetti di programmazione noti come [code smell](https://deviq.com/code-smells/).</span><span class="sxs-lookup"><span data-stu-id="666c9-107">Using enums for control flow or more robust abstractions can be a [code smell](https://deviq.com/code-smells/).</span></span> <span data-ttu-id="666c9-108">Questo tipo di utilizzo determina un codice fragile con molte istruzioni del flusso di controllo che verificano i valori dell'enumerazione.</span><span class="sxs-lookup"><span data-stu-id="666c9-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="666c9-109">In alternativa, è possibile creare classi di enumerazione che abilitano tutte le funzionalità avanzate di un linguaggio orientato a oggetti.</span><span class="sxs-lookup"><span data-stu-id="666c9-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="666c9-110">Tuttavia, questo non è un argomento strategico e in molti casi, per semplicità è comunque possibile continuare a usare i normali [tipi enum](../../../csharp/language-reference/keywords/enum.md) se si preferisce.</span><span class="sxs-lookup"><span data-stu-id="666c9-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/keywords/enum.md) if that's your preference.</span></span> <span data-ttu-id="666c9-111">Comunque, l'uso delle classi di enumerazione è più strettamente correlato a concetti aziendali.</span><span class="sxs-lookup"><span data-stu-id="666c9-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="666c9-112">Implementare una classe di base di enumerazione</span><span class="sxs-lookup"><span data-stu-id="666c9-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="666c9-113">Il microservizio degli ordini nell'app eShopOnContainers fornisce un'implementazione della classe di base di enumerazione di esempio, come mostrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="666c9-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration(int id, string name) 
    {
        Id = id; 
        Name = name; 
    }

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public | 
                                         BindingFlags.Static | 
                                         BindingFlags.DeclaredOnly); 

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj) 
    {
        var otherValue = obj as Enumeration; 

        if (otherValue == null) 
            return false;

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id); 

    // Other utility methods ... 
}
```

<span data-ttu-id="666c9-114">È possibile usare questa classe come un tipo in qualsiasi entità o oggetto valore, come per la classe `CardType` : `Enumeration` seguente:</span><span class="sxs-lookup"><span data-stu-id="666c9-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    public CardType(int id, string name)
        : base(id, name)
    {
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="666c9-115">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="666c9-115">Additional resources</span></span>

- <span data-ttu-id="666c9-116">**Enum's are evil—update** \ (Gli enum sono il male: aggiornamento)</span><span class="sxs-lookup"><span data-stu-id="666c9-116">**Enum’s are evil—update** \</span></span>
  <https://www.planetgeek.ch/2009/07/01/enums-are-evil/>

- <span data-ttu-id="666c9-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It** \ (In che modo gli enum diffondono malattie e come curarle)</span><span class="sxs-lookup"><span data-stu-id="666c9-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It** \</span></span>
  <https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/>

- <span data-ttu-id="666c9-118">**Jimmy Bogard. Enumeration classes** \ (Classi di enumerazione)</span><span class="sxs-lookup"><span data-stu-id="666c9-118">**Jimmy Bogard. Enumeration classes** \</span></span>
  <https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/>

- <span data-ttu-id="666c9-119">**Steve Smith. Enum Alternatives in C#**  \ (Alternative agli enum in C#)</span><span class="sxs-lookup"><span data-stu-id="666c9-119">**Steve Smith. Enum Alternatives in C#** \</span></span>
  <https://ardalis.com/enum-alternatives-in-c>

- <span data-ttu-id="666c9-120">**Enumeration.cs.**</span><span class="sxs-lookup"><span data-stu-id="666c9-120">**Enumeration.cs.**</span></span> <span data-ttu-id="666c9-121">Base Enumeration class in eShopOnContainers \ (Classe di enumerazione di base in eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="666c9-121">Base Enumeration class in eShopOnContainers \</span></span>
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs>

- <span data-ttu-id="666c9-122">**CardType.cs**.</span><span class="sxs-lookup"><span data-stu-id="666c9-122">**CardType.cs**.</span></span> <span data-ttu-id="666c9-123">Classe di enumerazione di esempio in eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="666c9-123">Sample Enumeration class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs>
    
- <span data-ttu-id="666c9-124">**SmartEnum**.</span><span class="sxs-lookup"><span data-stu-id="666c9-124">**SmartEnum**.</span></span> <span data-ttu-id="666c9-125">Ardalis - Classi che consentono di produrre enum fortemente tipizzati e più intelligenti in .NET.</span><span class="sxs-lookup"><span data-stu-id="666c9-125">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  <https://www.nuget.org/packages/Ardalis.SmartEnum/>

>[!div class="step-by-step"]
><span data-ttu-id="666c9-126">[Precedente](implement-value-objects.md)
>[Successivo](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="666c9-126">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>