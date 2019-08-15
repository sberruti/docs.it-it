---
title: Usare i dati nelle app ASP.NET Core
description: Progettare applicazioni Web moderne con ASP.NET Core e Azure | Usare i dati nelle app ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 9f765acce89bec1fd73e9c43a6e7d75d78be785d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68672818"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="49db4-103">Uso dei dati nelle app ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49db4-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="49db4-104">"I dati sono un elemento prezioso che dura più a lungo dei sistemi"</span><span class="sxs-lookup"><span data-stu-id="49db4-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="49db4-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="49db4-105">Tim Berners-Lee</span></span>

<span data-ttu-id="49db4-106">L'accesso ai dati è una questione importante in quasi tutte le applicazioni software.</span><span class="sxs-lookup"><span data-stu-id="49db4-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="49db4-107">ASP.NET Core supporta un'ampia gamma di opzioni di accesso ai dati, tra cui Entity Framework Core (e anche Entity Framework 6) e può usare qualsiasi framework di accesso ai dati .NET.</span><span class="sxs-lookup"><span data-stu-id="49db4-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="49db4-108">La scelta del tipo di framework di accesso ai dati da usare dipende dalle esigenze dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="49db4-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="49db4-109">Scegliere in base ai progetti ApplicationCore e UI e incapsulare i dettagli di implementazione in Infrastructure per creare un software testabile e poco accoppiato.</span><span class="sxs-lookup"><span data-stu-id="49db4-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="49db4-110">Entity Framework Core (per database relazionali)</span><span class="sxs-lookup"><span data-stu-id="49db4-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="49db4-111">Se si scrive una nuova applicazione ASP.NET ASP.NET Core che deve usare dati relazionali, è consigliabile che l'applicazione usi Entity Framework Core (EF Core) per accedere ai dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="49db4-112">EF Core è un mapper relazionale a oggetti che consente agli sviluppatori .NET di salvare in modo permanente gli oggetti in/da un'origine dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="49db4-113">In questo modo la maggior parte del codice per l'accesso ai dati che in genere gli sviluppatori devono scrivere non è più necessaria.</span><span class="sxs-lookup"><span data-stu-id="49db4-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="49db4-114">Come ASP.NET Core, EF Core è stato completamente riscritto per poter supportare le applicazioni multipiattaforma modulari.</span><span class="sxs-lookup"><span data-stu-id="49db4-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="49db4-115">Viene aggiunto all'applicazione come pacchetto NuGet, configurato all'avvio e richiesto tramite l'inserimento di dipendenze ovunque sia necessario.</span><span class="sxs-lookup"><span data-stu-id="49db4-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="49db4-116">Per usare EF Core con un database di SQL Server, eseguire il comando dell'interfaccia della riga di comando dotnet seguente:</span><span class="sxs-lookup"><span data-stu-id="49db4-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="49db4-117">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span><span class="sxs-lookup"><span data-stu-id="49db4-117">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="49db4-118">Per aggiungere il supporto per un'origine dati InMemory per il test:</span><span class="sxs-lookup"><span data-stu-id="49db4-118">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="49db4-119">add package Microsoft.EntityFrameworkCore.SqlServer</span><span class="sxs-lookup"><span data-stu-id="49db4-119">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="49db4-120">DbContext</span><span class="sxs-lookup"><span data-stu-id="49db4-120">The DbContext</span></span>

<span data-ttu-id="49db4-121">Per usare EF Core è necessaria una sottoclasse di <xref:Microsoft.EntityFrameworkCore.DbContext>.</span><span class="sxs-lookup"><span data-stu-id="49db4-121">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="49db4-122">Questa classe contiene le proprietà che rappresentano raccolte di entità che l'applicazione userà.</span><span class="sxs-lookup"><span data-stu-id="49db4-122">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="49db4-123">L'esempio eShopOnWeb include un oggetto CatalogContext contenente raccolte per elementi, marchi e i tipi:</span><span class="sxs-lookup"><span data-stu-id="49db4-123">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

<span data-ttu-id="49db4-124">DbContext deve avere un costruttore che accetta DbContextOptions e deve passare questo argomento al costruttore DbContext di base.</span><span class="sxs-lookup"><span data-stu-id="49db4-124">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="49db4-125">Si noti che se l'applicazione contiene una sola classe DbContext, è possibile passare un'istanza di DbContextOptions, ma se ne contiene più di una, è necessario usare il tipo generico DbContextOptions\<T>, passando il tipo DbContext come parametro generico.</span><span class="sxs-lookup"><span data-stu-id="49db4-125">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="49db4-126">Configurazione di EF Core</span><span class="sxs-lookup"><span data-stu-id="49db4-126">Configuring EF Core</span></span>

<span data-ttu-id="49db4-127">Nell'applicazione ASP.NET Core EF Core sarà generalmente configurato nel metodo ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="49db4-127">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="49db4-128">EF Core usa un oggetto DbContextOptionsBuilder, che supporta diversi metodi di estensione utili che consentono di semplificarne la configurazione.</span><span class="sxs-lookup"><span data-stu-id="49db4-128">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="49db4-129">Per configurare CatalogContext in modo che usi un database di SQL Server con una stringa di connessione definita in Configuration, aggiungere il codice seguente a ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="49db4-129">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="49db4-130">Per usare il database in memoria:</span><span class="sxs-lookup"><span data-stu-id="49db4-130">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="49db4-131">Dopo aver installato EF Core, aver creato un tipo figlio DbContext e averlo configurato in ConfigureServices, è possibile usare EF Core.</span><span class="sxs-lookup"><span data-stu-id="49db4-131">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="49db4-132">È possibile richiedere un'istanza del tipo DbContext in qualsiasi servizio in cui è necessario e iniziare a usare le entità persistenti tramite LINQ come se si trovassero semplicemente in una raccolta.</span><span class="sxs-lookup"><span data-stu-id="49db4-132">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="49db4-133">EF Core converte le espressioni LINQ in query SQL per archiviare e recuperare i dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-133">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="49db4-134">È possibile visualizzare le query eseguite da EF Core configurando un logger e verificando che il livello sia impostato almeno su Information, come illustrato nella Figura 8-1.</span><span class="sxs-lookup"><span data-stu-id="49db4-134">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="49db4-135">Figura 8-1: registrazione delle query di EF Core nella console</span><span class="sxs-lookup"><span data-stu-id="49db4-135">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="49db4-136">Recupero e archiviazione dei dati</span><span class="sxs-lookup"><span data-stu-id="49db4-136">Fetching and storing Data</span></span>

<span data-ttu-id="49db4-137">Per recuperare i dati da EF Core, accedere alla proprietà appropriata e usare LINQ per filtrare il risultato.</span><span class="sxs-lookup"><span data-stu-id="49db4-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="49db4-138">È anche possibile usare LINQ per eseguire una proiezione e trasformare il risultato da un tipo a un altro.</span><span class="sxs-lookup"><span data-stu-id="49db4-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="49db4-139">Nell'esempio seguente viene recuperato l'oggetto CatalogBrands. Viene ordinato per nome, filtrato per la proprietà Enabled e proiettato in un tipo SelectListItem:</span><span class="sxs-lookup"><span data-stu-id="49db4-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="49db4-140">Nell'esempio precedente è importante aggiungere la chiamata a ToListAsync per eseguire immediatamente la query.</span><span class="sxs-lookup"><span data-stu-id="49db4-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="49db4-141">In caso contrario, l'istruzione assegnerà a brandItems un IQueryable\<SelectListItem> che verrà eseguito solo dopo che è stato enumerato.</span><span class="sxs-lookup"><span data-stu-id="49db4-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="49db4-142">Esistono vantaggi e svantaggi nella restituzione di risultati IQueryable dai metodi.</span><span class="sxs-lookup"><span data-stu-id="49db4-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="49db4-143">La query costruita da EF Core può essere ulteriormente modificata, ma può anche generare errori che si verificano solo in fase di esecuzione, se alla query vengono aggiunte operazioni che EF Core non può convertire.</span><span class="sxs-lookup"><span data-stu-id="49db4-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="49db4-144">È generalmente preferibile passare i filtri al metodo che esegue l'accesso ai dati e restituire una raccolta in memoria (ad esempio, List\<T>) come risultato.</span><span class="sxs-lookup"><span data-stu-id="49db4-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="49db4-145">EF Core tiene traccia delle modifiche apportate alle entità che vengono recuperate dalla persistenza.</span><span class="sxs-lookup"><span data-stu-id="49db4-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="49db4-146">Per salvare le modifiche a un'entità rilevata, chiamare semplicemente il metodo SaveChanges in DbContext, assicurandosi che sia la stessa istanza di DbContext usata per recuperare l'entità.</span><span class="sxs-lookup"><span data-stu-id="49db4-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="49db4-147">L'aggiunta e la rimozione delle entità avvengono direttamente nella proprietà DbSet appropriata, con una chiamata a SaveChanges per eseguire i comandi di database.</span><span class="sxs-lookup"><span data-stu-id="49db4-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="49db4-148">Nell'esempio seguente vengono dimostrate le operazioni di aggiunta, aggiornamento e rimozione delle entità dalla persistenza.</span><span class="sxs-lookup"><span data-stu-id="49db4-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

<span data-ttu-id="49db4-149">EF Core supporta sia metodi sincroni che asincroni per il recupero e il salvataggio.</span><span class="sxs-lookup"><span data-stu-id="49db4-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="49db4-150">Nelle applicazioni Web è consigliabile usare il modello asincrono/awaiter con i metodi asincroni. In questo modo i thread del server Web non saranno bloccati in attesa che le operazioni di accesso ai dati siano completate.</span><span class="sxs-lookup"><span data-stu-id="49db4-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="49db4-151">Recupero dei dati correlati</span><span class="sxs-lookup"><span data-stu-id="49db4-151">Fetching related data</span></span>

<span data-ttu-id="49db4-152">Dopo aver recuperato le entità, EF Core compila tutte le proprietà archiviate direttamente con l'entità appropriata nel database.</span><span class="sxs-lookup"><span data-stu-id="49db4-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="49db4-153">Le proprietà di navigazione, ad esempio elenchi di entità correlate, non vengono popolate e il loro valore può essere impostato su Null.</span><span class="sxs-lookup"><span data-stu-id="49db4-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="49db4-154">In questo modo, EF Core non recupererà più dati del necessario, requisito particolarmente importante per le applicazioni Web, che devono elaborare velocemente le richieste e restituire le risposte in modo efficiente.</span><span class="sxs-lookup"><span data-stu-id="49db4-154">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="49db4-155">Per includere le relazioni con un'entità tramite il _caricamento eager_, specificare la proprietà usando il metodo di estensione Include nella query, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="49db4-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="49db4-156">È possibile includere più relazioni, ma anche relazioni secondarie usando ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="49db4-156">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="49db4-157">EF Core eseguirà una singola query per recuperare il set di entità ottenuto.</span><span class="sxs-lookup"><span data-stu-id="49db4-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="49db4-158">In alternativa è possibile includere proprietà di navigazione di proprietà di navigazione passando una stringa separata da "." al metodo di estensione `.Include()`, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="49db4-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include(“Items.Products”)
```

<span data-ttu-id="49db4-159">Oltre a incapsulare la logica di filtro, una specifica può indicare la forma dei dati da restituire, incluse le proprietà da popolare.</span><span class="sxs-lookup"><span data-stu-id="49db4-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="49db4-160">L'esempio eShopOnWeb include diverse specifiche che illustrano l'incapsulamento di informazioni di caricamento eager nella specifica.</span><span class="sxs-lookup"><span data-stu-id="49db4-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="49db4-161">Di seguito è visualizzato un esempio d'uso della specifica come parte di una query:</span><span class="sxs-lookup"><span data-stu-id="49db4-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="49db4-162">Il _caricamento esplicito_ è un'altra opzione per caricare i dati correlati.</span><span class="sxs-lookup"><span data-stu-id="49db4-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="49db4-163">Il caricamento esplicito consente di caricare dati aggiuntivi in un'entità che è già stata recuperata.</span><span class="sxs-lookup"><span data-stu-id="49db4-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="49db4-164">Poiché prevede una richiesta separata al database, non è consigliabile per le applicazioni Web, che devono ridurre al minimo il numero round trip al database per ogni richiesta.</span><span class="sxs-lookup"><span data-stu-id="49db4-164">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="49db4-165">Il _caricamento lazy_ è una funzionalità che consente di caricare automaticamente i dati correlati ai quali l'applicazione fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="49db4-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="49db4-166">EF Core ha aggiunto il supporto per il caricamento posticipato nella versione 2.1.</span><span class="sxs-lookup"><span data-stu-id="49db4-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="49db4-167">Il caricamento posticipato non è abilitato per impostazione predefinita e richiede l'installazione di `Microsoft.EntityFrameworkCore.Proxies`.</span><span class="sxs-lookup"><span data-stu-id="49db4-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="49db4-168">Come con il caricamento esplicito, il caricamento posticipato in genere deve essere disabilitato per le applicazioni Web poiché comporta delle query di database aggiuntive eseguite all'interno di ogni richiesta Web.</span><span class="sxs-lookup"><span data-stu-id="49db4-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="49db4-169">Purtroppo, il sovraccarico generato dal caricamento posticipato spesso non viene rilevato in fase di sviluppo, quando la latenza è poca e spesso i set di dati usati per il test sono piccoli.</span><span class="sxs-lookup"><span data-stu-id="49db4-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="49db4-170">Tuttavia nell'ambiente di produzione, con più utenti, più dati e latenza maggiore, le richieste di database aggiuntive spesso possono causare una riduzione delle prestazioni delle applicazioni Web che fanno largo uso del caricamento posticipato.</span><span class="sxs-lookup"><span data-stu-id="49db4-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

<span data-ttu-id="49db4-171">[Avoid Lazy Loading Entities in Web Applications](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications) (Evitare il caricamento posticipato nelle applicazioni Web)</span><span class="sxs-lookup"><span data-stu-id="49db4-171">[Avoid Lazy Loading Entities in Web Applications](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)</span></span>

### <a name="encapsulating-data"></a><span data-ttu-id="49db4-172">Incapsulamento dei dati</span><span class="sxs-lookup"><span data-stu-id="49db4-172">Encapsulating data</span></span>

<span data-ttu-id="49db4-173">EF Core supporta diverse funzionalità che consentono al modello di incapsulare correttamente il proprio stato.</span><span class="sxs-lookup"><span data-stu-id="49db4-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="49db4-174">Un problema comune nei modelli di dominio è che espongono le proprietà di navigazione della raccolta come tipi elenco accessibili pubblicamente.</span><span class="sxs-lookup"><span data-stu-id="49db4-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="49db4-175">Di conseguenza i collaboratori possono modificare il contenuto di questi tipi di raccolta e ignorare importanti regole di business relative alla raccolta stessa, con il rischio di lasciare l'oggetto in uno stato non valido.</span><span class="sxs-lookup"><span data-stu-id="49db4-175">This allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="49db4-176">La soluzione è esporre l'accesso in sola lettura alle raccolte correlate e specificare in modo esplicito metodi che definiscono le modalità di modifica di queste raccolte da parte dei client, come nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="49db4-176">The solution to this is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

<span data-ttu-id="49db4-177">Si noti che questo tipo di entità non espone una proprietà `List` o `ICollection` pubblica, ma espone un tipo `IReadOnlyCollection` che esegue il wrapping del tipo List (Elenco) sottostante.</span><span class="sxs-lookup"><span data-stu-id="49db4-177">Note that this entity type doesn’t expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="49db4-178">Quando si usa questo criterio è possibile indicare a Entity Framework Core di usare il campo sottostante nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="49db4-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="49db4-179">Un altro approccio per il miglioramento del modello di dominio è l'uso di oggetti valore per i tipi che non dispongono di identità e si distinguono solo per le relative proprietà.</span><span class="sxs-lookup"><span data-stu-id="49db4-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="49db4-180">L'uso di questi tipi come proprietà delle entità consente di mantenere la logica specifica per l'oggetto valore nella posizione appropriata, evitando duplicazioni di logica tra più entità che usano lo stesso concetto.</span><span class="sxs-lookup"><span data-stu-id="49db4-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="49db4-181">In Entity Framework Core è possibile rendere persistenti gli oggetti valore nella stessa tabella dell'entità di appartenenza, configurando il tipo come entità di proprietà come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="49db4-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="49db4-182">In questo esempio la proprietà `ShipToAddress` è di tipo `Address`.</span><span class="sxs-lookup"><span data-stu-id="49db4-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="49db4-183">`Address` è un oggetto valore con diverse proprietà, quali `Street` e `City`.</span><span class="sxs-lookup"><span data-stu-id="49db4-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="49db4-184">Entity Framework Core esegue il mapping dell'oggetto `Order` alla relativa tabella con una sola colonna per ogni proprietà `Address`, facendo precedere al nome di ogni colonna il nome della proprietà.</span><span class="sxs-lookup"><span data-stu-id="49db4-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="49db4-185">In questo esempio la tabella `Order` includerebbe colonne come `ShipToAddress_Street` e `ShipToAddress_City`.</span><span class="sxs-lookup"><span data-stu-id="49db4-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span>

[<span data-ttu-id="49db4-186">EF Core 2.2 introduce il supporto delle raccolte di entità di proprietà</span><span class="sxs-lookup"><span data-stu-id="49db4-186">EF Core 2.2 introduces support for collections of owned entities</span></span>](https://docs.microsoft.com/ef/core/what-is-new/ef-core-2.2#collections-of-owned-entities)

### <a name="resilient-connections"></a><span data-ttu-id="49db4-187">Connessioni resilienti</span><span class="sxs-lookup"><span data-stu-id="49db4-187">Resilient connections</span></span>

<span data-ttu-id="49db4-188">In alcuni casi è possibile che le risorse esterne, ad esempio i database SQL, non siano disponibili.</span><span class="sxs-lookup"><span data-stu-id="49db4-188">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="49db4-189">In caso di indisponibilità temporanea, le applicazioni possono usare la logica di ripetizione per evitare che sia generata un'eccezione.</span><span class="sxs-lookup"><span data-stu-id="49db4-189">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="49db4-190">Questa tecnica è comunemente nota come _resilienza della connessione_.</span><span class="sxs-lookup"><span data-stu-id="49db4-190">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="49db4-191">È possibile implementare i [tentativi con backoff esponenziale ](https://docs.microsoft.com/azure/architecture/patterns/retry), vale a dire una tecnica che tenta di ripetere un'operazione con un tempo di attesa che aumenta esponenzialmente, fino a quando non viene raggiunto il numero massimo di tentativi.</span><span class="sxs-lookup"><span data-stu-id="49db4-191">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="49db4-192">Questa tecnica si basa sul presupposto che le risorse cloud potrebbero essere non disponibili in modo intermittente per brevi periodi, generando l'errore di alcune richieste.</span><span class="sxs-lookup"><span data-stu-id="49db4-192">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="49db4-193">Per il database SQL di Azure, Entity Framework Core fornisce già la logica per i tentativi e la resilienza della connessione di database interna.</span><span class="sxs-lookup"><span data-stu-id="49db4-193">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="49db4-194">È tuttavia necessario abilitare la strategia di esecuzione di Entity Framework per ogni connessione DbContext per ottenere connessioni di EF Core resilienti.</span><span class="sxs-lookup"><span data-stu-id="49db4-194">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="49db4-195">Ad esempio, il codice seguente a livello della connessione di EF Core consente connessioni SQL resilienti per le quali vengono effettuati ulteriori tentativi in caso di mancata connessione.</span><span class="sxs-lookup"><span data-stu-id="49db4-195">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30),
            errorNumbersToAdd: null);
        });
    });
}
//...
```

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="49db4-196">Strategie di esecuzione e transazioni esplicite usando BeginTransaction e più oggetti DbContext</span><span class="sxs-lookup"><span data-stu-id="49db4-196">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="49db4-197">Quando nelle connessioni di EF Core sono abilitati i tentativi, ogni operazione che viene eseguita con EF Core diventa un'unica operazione con possibilità di ritentare.</span><span class="sxs-lookup"><span data-stu-id="49db4-197">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="49db4-198">Per ogni query e per ogni chiamata a SaveChanges verranno eseguiti altri tentativi come una sola unità nel caso in cui si verifichi un errore temporaneo.</span><span class="sxs-lookup"><span data-stu-id="49db4-198">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="49db4-199">Se tuttavia il codice avvia una transazione tramite BeginTransaction, viene definito un gruppo di operazioni personalizzato che deve essere considerato come un'unità. Se si verifica un errore, verrà eseguito il rollback di tutto ciò che si trova all'interno della transazione.</span><span class="sxs-lookup"><span data-stu-id="49db4-199">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="49db4-200">Se si tenta di eseguire la transazione quando si usa una strategia di esecuzione (criteri di ripetizione) di EF e si includono numerosi oggetti SaveChanges da più oggetti DbContext, verrà restituita un'eccezione simile alla seguente.</span><span class="sxs-lookup"><span data-stu-id="49db4-200">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="49db4-201">System.InvalidOperationException: La strategia di esecuzione configurata 'SqlServerRetryingExecutionStrategy' non supporta le transazioni avviate dall'utente.</span><span class="sxs-lookup"><span data-stu-id="49db4-201">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="49db4-202">Usare la strategia di esecuzione restituita da 'DbContext.Database.CreateExecutionStrategy()' per eseguire tutte le operazioni nella transazione come un'unità con possibilità di ritentare.</span><span class="sxs-lookup"><span data-stu-id="49db4-202">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="49db4-203">La soluzione prevede di richiamare manualmente la strategia di esecuzione di EF con un delegato che rappresenta tutte le operazioni che devono essere eseguite.</span><span class="sxs-lookup"><span data-stu-id="49db4-203">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="49db4-204">Se si verifica un errore temporaneo, la strategia di esecuzione richiamerà nuovamente il delegato.</span><span class="sxs-lookup"><span data-stu-id="49db4-204">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="49db4-205">Nel codice seguente viene illustrato come implementare questo approccio:</span><span class="sxs-lookup"><span data-stu-id="49db4-205">The following code shows how to implement this approach:</span></span>

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy();
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();

        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
        await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

<span data-ttu-id="49db4-206">Il primo oggetto DbContext è \_catalogContext e il secondo oggetto DbContext si trova all'interno dell'oggetto \_integrationEventLogService.</span><span class="sxs-lookup"><span data-stu-id="49db4-206">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="49db4-207">Alla fine, l'azione Commit viene eseguita su più oggetti DbContext tramite una strategia di esecuzione di EF.</span><span class="sxs-lookup"><span data-stu-id="49db4-207">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="49db4-208">Riferimenti a Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="49db4-208">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="49db4-209">**Documentazione di Entity Framework**</span><span class="sxs-lookup"><span data-stu-id="49db4-209">**EF Core Docs**</span></span>  
>   <https://docs.microsoft.com/ef/>
> - <span data-ttu-id="49db4-210">**EF Core: dati correlati**</span><span class="sxs-lookup"><span data-stu-id="49db4-210">**EF Core: Related Data**</span></span>  
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - <span data-ttu-id="49db4-211">**Avoid Lazy Loading Entities in ASP.NET Applications** (Evitare il caricamento lazy di entità in applicazioni ASPNET)</span><span class="sxs-lookup"><span data-stu-id="49db4-211">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="49db4-212">EF Core o micro ORM?</span><span class="sxs-lookup"><span data-stu-id="49db4-212">EF Core or micro-ORM?</span></span>

<span data-ttu-id="49db4-213">EF Core è un'ottima soluzione per la gestione della persistenza. In pratica incapsula i dettagli del database dagli sviluppatori dell'applicazione. Non è tuttavia l'unica possibilità.</span><span class="sxs-lookup"><span data-stu-id="49db4-213">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="49db4-214">Esiste un'alternativa open source comune denominata [Dapper](https://github.com/StackExchange/Dapper). Si tratta di un micro ORM.</span><span class="sxs-lookup"><span data-stu-id="49db4-214">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="49db4-215">Un micro ORM è uno strumento semplice e meno completo per il mapping di oggetti in strutture di dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-215">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="49db4-216">Nel caso di Dapper, è stato progettato per focalizzarsi sulle prestazioni, anziché sul completo incapsulamento delle query sottostanti usate per recuperare e aggiornare i dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-216">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="49db4-217">Poiché non estrae le istruzioni SQL dallo sviluppatore, Dapper è un prodotto CTM (close to the meta) e consente agli sviluppatori di scrivere le query esatte da usare per una determinata operazione di accesso ai dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-217">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="49db4-218">EF Core offre due importanti funzionalità che lo distinguono da Dapper ma che al tempo stesso gravano sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="49db4-218">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="49db4-219">La prima è la conversione di espressioni LINK in SQL.</span><span class="sxs-lookup"><span data-stu-id="49db4-219">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="49db4-220">Queste conversioni vengono memorizzate nella cache. Ciononostante, la prima volta che vengono eseguite si verifica un sovraccarico delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="49db4-220">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="49db4-221">La seconda funzionalità importante è il rilevamento delle modifiche nelle entità. In questo modo è possibile generare istruzioni di aggiornamento in modo efficiente.</span><span class="sxs-lookup"><span data-stu-id="49db4-221">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="49db4-222">Questo comportamento può essere disattivato per query specifiche tramite l'estensione AsNotTracking.</span><span class="sxs-lookup"><span data-stu-id="49db4-222">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="49db4-223">EF Core genera anche query SQL che sono generalmente molto efficienti e in ogni caso perfettamente accettabili dal punto di vista delle prestazioni. Se è tuttavia necessario eseguire un controllo dettagliato sulla query specifica, è anche possibile passare un'istruzione SQL personalizzata (o eseguire una stored procedure) tramite EF Core.</span><span class="sxs-lookup"><span data-stu-id="49db4-223">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="49db4-224">In questo caso, le prestazioni offerte da Dapper sono leggermente più elevate rispetto a EF Core.</span><span class="sxs-lookup"><span data-stu-id="49db4-224">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="49db4-225">Julie Lerman presenta alcuni dati relativi alle prestazioni nel suo articolo [Dapper, Entity Framework e app ibride](https://msdn.microsoft.com/magazine/mt703432.aspx) pubblicato da MSDN a maggio 2016.</span><span class="sxs-lookup"><span data-stu-id="49db4-225">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="49db4-226">Dati benchmark aggiuntivi sulle prestazioni di una serie di metodi di accesso ai dati sono disponibili sul [sito di Dapper](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="49db4-226">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="49db4-227">Per conoscere le diversità in termini di sintassi tra Dapper ed EF Core, considerare queste due versioni dello stesso metodo per recuperare un elenco di elementi:</span><span class="sxs-lookup"><span data-stu-id="49db4-227">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

<span data-ttu-id="49db4-228">Per compilare oggetti grafici più complessi con Dapper, è necessario scrivere le query associate. Non è invece possibile aggiungere un oggetto Include come EF Core prevede.</span><span class="sxs-lookup"><span data-stu-id="49db4-228">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="49db4-229">A tale scopo, sono supportati diversi tipi di sintassi, tra cui la funzione denominata Multi Mapping, che consente di eseguire il mapping di singole righe su più oggetti con mapping.</span><span class="sxs-lookup"><span data-stu-id="49db4-229">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="49db4-230">Ad esempio, data una classe Post con una proprietà Owner di tipo User, l'istruzione SQL seguente restituirà tutti i dati necessari:</span><span class="sxs-lookup"><span data-stu-id="49db4-230">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="49db4-231">Ogni riga restituita include i dati sia di User sia di Post.</span><span class="sxs-lookup"><span data-stu-id="49db4-231">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="49db4-232">Poiché i dati di User sono collegati ai dati di Post tramite la proprietà Owner, è necessario usare la funzione seguente:</span><span class="sxs-lookup"><span data-stu-id="49db4-232">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="49db4-233">Il listato di codice completo per restituire una raccolta di oggetti Post con la proprietà Owner popolata e i dati di User associati sarà il seguente:</span><span class="sxs-lookup"><span data-stu-id="49db4-233">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="49db4-234">Poiché Dapper offre una capacità di incapsulamento ridotta, è necessario che gli sviluppatori sappiano come archiviare i dati, eseguire una query sui dati in modo efficiente e scrivere altro codice per recuperare i dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-234">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="49db4-235">Quando viene modificato il modello, anziché creare semplicemente una nuova migrazione (un'altra funzionalità di EF Core) e/o aggiornare le informazioni di mapping in un unico punto di un oggetto DbContext, è necessario aggiornare tutte le query interessate.</span><span class="sxs-lookup"><span data-stu-id="49db4-235">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="49db4-236">Queste query non offrono garanzie durante la compilazione, pertanto possono interrompersi durante l'esecuzione in risposta alle modifiche al modello o al database, compromettendo il rilevamento rapido degli errori.</span><span class="sxs-lookup"><span data-stu-id="49db4-236">These queries have no compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="49db4-237">A fronte di questi compromessi, Dapper offre prestazioni molto elevate.</span><span class="sxs-lookup"><span data-stu-id="49db4-237">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="49db4-238">Per la maggior parte delle applicazioni e per molte parti di quasi tutte le applicazioni, le prestazioni di EF Core risultano accettabili.</span><span class="sxs-lookup"><span data-stu-id="49db4-238">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="49db4-239">Di conseguenza, i vantaggi offerti agli sviluppatori dal punto della produttività superano il relativo sovraccarico delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="49db4-239">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="49db4-240">Per le query che usano la memorizzazione nella cache, la query effettiva può essere eseguita in brevissimo tempo. In questi casi le differenze in termini di prestazioni di query si riducono e diventano discutibili.</span><span class="sxs-lookup"><span data-stu-id="49db4-240">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="49db4-241">SQL o NoSQL</span><span class="sxs-lookup"><span data-stu-id="49db4-241">SQL or NoSQL</span></span>

<span data-ttu-id="49db4-242">I database relazionali, ad esempio SQL Server, hanno tradizionalmente dominato il mercato in termini di archiviazione dei dati persistenti, ma non sono l'unica soluzione disponibile.</span><span class="sxs-lookup"><span data-stu-id="49db4-242">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="49db4-243">I database NoSQL come [MongoDB](https://www.mongodb.com/what-is-mongodb) offrono un approccio diverso per l'archiviazione degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="49db4-243">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="49db4-244">Anziché eseguire il mapping di oggetti in tabelle e righe, è possibile serializzare l'intero oggetto grafico e memorizzare il risultato.</span><span class="sxs-lookup"><span data-stu-id="49db4-244">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="49db4-245">I vantaggi di questo approccio sono, almeno inizialmente, le prestazioni e la semplicità.</span><span class="sxs-lookup"><span data-stu-id="49db4-245">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="49db4-246">È certamente più semplice archiviare un singolo oggetto serializzato con una chiave, rispetto a decomporre l'oggetto in molte tabelle con relazioni e aggiornare le righe che potrebbero essere state modificate dall'ultima volta in cui l'oggetto è stato recuperato dal database.</span><span class="sxs-lookup"><span data-stu-id="49db4-246">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="49db4-247">Analogamente, il recupero e la deserializzazione di un singolo oggetto da un archivio basato su chiavi è in genere molto più veloce e più semplice rispetto all'uso di join complessi o più query di database necessari per comporre completamente lo stesso oggetto da un database relazionale.</span><span class="sxs-lookup"><span data-stu-id="49db4-247">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="49db4-248">La mancanza di blocchi, transazioni o di uno schema fisso rende i database NoSQL anche particolarmente adatti ai fini della scalabilità su molti computer, che supportano set di dati di grandi dimensioni.</span><span class="sxs-lookup"><span data-stu-id="49db4-248">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="49db4-249">Di contro, nei comunemente detti database NoSQL non mancano gli svantaggi.</span><span class="sxs-lookup"><span data-stu-id="49db4-249">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="49db4-250">Nei database relazionali viene applicata la normalizzazione per garantire coerenza ed evitare la duplicazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-250">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="49db4-251">In questo modo si riducono le dimensioni totali del database e si assicura che gli aggiornamenti ai dati condivisi siano immediatamente disponibili in tutto il database.</span><span class="sxs-lookup"><span data-stu-id="49db4-251">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="49db4-252">In un database relazionale è possibile che una tabella Address faccia riferimento a una tabella Country usando l'ID, in modo che se il nome di un paese/area geografica è stato modificato, i record relativi agli indirizzi possano usare l'aggiornamento senza dover essere a loro volta aggiornati.</span><span class="sxs-lookup"><span data-stu-id="49db4-252">In a relational database, an Address table might reference a Country table by ID, such that if the name of a country/region were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="49db4-253">In un database NoSQL la tabella Address e la relativa tabella Country associata potrebbero essere invece serializzate come parte di molti oggetti archiviati.</span><span class="sxs-lookup"><span data-stu-id="49db4-253">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="49db4-254">Per poter aggiornare il nome del paese o dell'area geografica è necessario aggiornare tutti questi oggetti anziché una sola riga.</span><span class="sxs-lookup"><span data-stu-id="49db4-254">An update to a country/region name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="49db4-255">I database relazionali possono anche garantire l'integrità relazionale tramite l'applicazione di regole, come le chiavi esterne.</span><span class="sxs-lookup"><span data-stu-id="49db4-255">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="49db4-256">I database NoSQL non offrono solitamente vincoli di questo genere sui dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-256">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="49db4-257">Un altro aspetto complesso che i database NoSQL devono gestire è il controllo delle versioni.</span><span class="sxs-lookup"><span data-stu-id="49db4-257">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="49db4-258">Quando le proprietà di un oggetto vengono modificate, non è possibile eseguire la deserializzazione degli oggetti dalle versioni precedenti in cui sono archiviati.</span><span class="sxs-lookup"><span data-stu-id="49db4-258">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="49db4-259">Di conseguenza, è necessario aggiornare tutti gli oggetti esistenti con una versione (precedente) serializzata dell'oggetto per rispettare il nuovo schema.</span><span class="sxs-lookup"><span data-stu-id="49db4-259">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="49db4-260">Concettualmente non è diverso da quanto accade in un database relazionale dove, in seguito a modifiche allo schema, è talvolta necessario aggiornare script e mapping.</span><span class="sxs-lookup"><span data-stu-id="49db4-260">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="49db4-261">Spesso però il numero delle modifiche da apportare in un database NoSQL è molto più elevato, in quanto è necessaria una maggiore duplicazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-261">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="49db4-262">Nei database NoSQL è possibile archiviare più versioni di oggetti, requisito che non è solitamente supportato dai database relazionali a schema fisso.</span><span class="sxs-lookup"><span data-stu-id="49db4-262">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="49db4-263">Tuttavia, in questo caso il codice dell'applicazione deve tenere conto dell'esistenza delle versioni precedenti degli oggetti, aumentando così la complessità.</span><span class="sxs-lookup"><span data-stu-id="49db4-263">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="49db4-264">In genere nei database NoSQL non vengono applicate le [ACID](https://en.wikipedia.org/wiki/ACID), vale a dire che sono vantaggiosi rispetto ai database relazionali in termini sia di prestazioni che di scalabilità.</span><span class="sxs-lookup"><span data-stu-id="49db4-264">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="49db4-265">Sono database ideali per data set e oggetti di dati di dimensioni molto grandi che non sono particolarmente adatti per essere archiviati in strutture tabella normalizzate.</span><span class="sxs-lookup"><span data-stu-id="49db4-265">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="49db4-266">Non esiste un motivo per cui un'applicazione non possa usare sia i database relazionali sia i database NoSQL a seconda dell'utilità.</span><span class="sxs-lookup"><span data-stu-id="49db4-266">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="49db4-267">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="49db4-267">Azure DocumentDB</span></span>

<span data-ttu-id="49db4-268">Azure DocumentDB è un servizio di database NoSQL completamente gestito che offre l'archiviazione di dati privi di schema basata sul cloud.</span><span class="sxs-lookup"><span data-stu-id="49db4-268">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="49db4-269">DocumentDB garantisce prestazioni rapide e prevedibili, disponibilità elevata, scalabilità elastica e distribuzione globale.</span><span class="sxs-lookup"><span data-stu-id="49db4-269">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="49db4-270">Nonostante sia un database NoSQL, gli sviluppatori possono applicare le note funzionalità avanzate di query SQL su dati JSON.</span><span class="sxs-lookup"><span data-stu-id="49db4-270">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="49db4-271">Tutte le risorse in DocumentDB vengono archiviate come documenti JSON.</span><span class="sxs-lookup"><span data-stu-id="49db4-271">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="49db4-272">Le risorse sono gestite come _elementi_, vale a dire documenti che contengono metadati, e come _feed_, ovvero raccolte di elementi.</span><span class="sxs-lookup"><span data-stu-id="49db4-272">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="49db4-273">Figura 8-2: illustra la relazione tra le diverse risorse di DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="49db4-273">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>

![Relazione gerarchica tra le risorse di DocumentDB, un database NoSQL JSON](./media/image8-2.png)

<span data-ttu-id="49db4-275">**Figura 8-2.**</span><span class="sxs-lookup"><span data-stu-id="49db4-275">**Figure 8-2.**</span></span> <span data-ttu-id="49db4-276">Organizzazione delle risorse di DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="49db4-276">DocumentDB resource organization.</span></span>

<span data-ttu-id="49db4-277">Il linguaggio di query di DocumentDB è costituito da un'interfaccia semplice ma potente che consente di eseguire query sui documenti JSON.</span><span class="sxs-lookup"><span data-stu-id="49db4-277">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="49db4-278">Il linguaggio supporta un subset di grammatica SQL ANSI e offre totale integrazione di oggetti, matrici, costruzione di oggetti e chiamate JavaScript.</span><span class="sxs-lookup"><span data-stu-id="49db4-278">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="49db4-279">**Riferimenti a DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="49db4-279">**References – DocumentDB**</span></span>

- <span data-ttu-id="49db4-280">Introduzione a DocumentDB</span><span class="sxs-lookup"><span data-stu-id="49db4-280">DocumentDB Introduction</span></span>  
  <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a><span data-ttu-id="49db4-281">Altre opzioni di persistenza</span><span class="sxs-lookup"><span data-stu-id="49db4-281">Other persistence options</span></span>

<span data-ttu-id="49db4-282">Oltre alle opzioni di archiviazione con database relazionali e NoSQL, le applicazioni ASP.NET Core possono usare l'archiviazione di Azure per archiviare una varietà di formati di dati e file in modelli scalabili, basati sul cloud.</span><span class="sxs-lookup"><span data-stu-id="49db4-282">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="49db4-283">L'archiviazione di Azure è altamente scalabile. È quindi possibile iniziare archiviando piccole quantità di dati per poi aumentare l'archiviazione a centinaia di terabyte, se richiesto dall'applicazione.</span><span class="sxs-lookup"><span data-stu-id="49db4-283">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="49db4-284">L'archiviazione di Azure supporta quattro tipi di dati:</span><span class="sxs-lookup"><span data-stu-id="49db4-284">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="49db4-285">Archiviazione BLOB per l'archiviazione di testo non strutturato o dati binari, detta anche archiviazione di oggetti.</span><span class="sxs-lookup"><span data-stu-id="49db4-285">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="49db4-286">Archiviazione tabelle per set di dati strutturati, accessibile tramite chiavi di riga.</span><span class="sxs-lookup"><span data-stu-id="49db4-286">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="49db4-287">Archiviazione code per messaggistica affidabile basata su coda.</span><span class="sxs-lookup"><span data-stu-id="49db4-287">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="49db4-288">Archiviazione file per l'accesso a file condivisi tra macchine virtuali di Azure e applicazioni locali.</span><span class="sxs-lookup"><span data-stu-id="49db4-288">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="49db4-289">**Riferimenti ad archiviazione di Azure**</span><span class="sxs-lookup"><span data-stu-id="49db4-289">**References – Azure Storage**</span></span>

- <span data-ttu-id="49db4-290">Introduzione ad Archiviazione di Azure</span><span class="sxs-lookup"><span data-stu-id="49db4-290">Azure Storage Introduction</span></span>  
  <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a><span data-ttu-id="49db4-291">Memorizzazione nella cache</span><span class="sxs-lookup"><span data-stu-id="49db4-291">Caching</span></span>

<span data-ttu-id="49db4-292">Nelle applicazioni Web è necessario che ogni richiesta Web sia completata nel minor tempo possibile.</span><span class="sxs-lookup"><span data-stu-id="49db4-292">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="49db4-293">A tale scopo è consigliabile limitare il numero di chiamate esterne che il server deve effettuare per completare la richiesta.</span><span class="sxs-lookup"><span data-stu-id="49db4-293">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="49db4-294">La memorizzazione nella cache comporta l'archiviazione di una copia di dati nel server, vale a dire un altro archivio dati che può essere sottoposto a query più facilmente rispetto all'origine dei dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-294">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="49db4-295">Le applicazioni Web, soprattutto le applicazioni Web tradizionali non SPA, devono compilare l'intera interfaccia utente con ogni richiesta.</span><span class="sxs-lookup"><span data-stu-id="49db4-295">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="49db4-296">Così succede spesso che molte delle stesse query sul database vengano eseguite ripetutamente tra una richiesta utente e quella successiva.</span><span class="sxs-lookup"><span data-stu-id="49db4-296">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="49db4-297">Nella maggior parte dei casi i dati raramente cambiano. Non c'è quindi motivo di richiederli costantemente dal database.</span><span class="sxs-lookup"><span data-stu-id="49db4-297">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="49db4-298">ASP.NET Core supporta la memorizzazione nella cache delle risposte, per le pagine intere, e la memorizzazione nella cache dei dati, che consente un comportamento di memorizzazione nella cache più granulare.</span><span class="sxs-lookup"><span data-stu-id="49db4-298">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="49db4-299">Quando si implementa la memorizzazione nella cache, è importante considerare i concetti in modo separato.</span><span class="sxs-lookup"><span data-stu-id="49db4-299">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="49db4-300">Non implementare la logica della memorizzazione nella cache nella logica di accesso ai dati o nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="49db4-300">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="49db4-301">Incapsulare invece la memorizzazione nella cache nelle classi e usare la configurazione per gestirne il comportamento.</span><span class="sxs-lookup"><span data-stu-id="49db4-301">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="49db4-302">Applicando così i principi di aperto/chiuso (OCP) e di singola responsabilità (SRP), sarà più facile gestire l'uso della memorizzazione nella cache nell'applicazione man mano che cresce.</span><span class="sxs-lookup"><span data-stu-id="49db4-302">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="49db4-303">Memorizzazione nella cache delle risposte di ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="49db4-303">ASP.NET Core response caching</span></span>

<span data-ttu-id="49db4-304">ASP.NET Core supporta due livelli di memorizzazione nella cache delle risposte.</span><span class="sxs-lookup"><span data-stu-id="49db4-304">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="49db4-305">Il primo livello non memorizza tutto nella cache nel server, ma aggiunge le intestazioni HTTP che indicano ai client e ai server proxy di memorizzare le risposte nella cache.</span><span class="sxs-lookup"><span data-stu-id="49db4-305">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="49db4-306">Questa istruzione viene implementata aggiungendo l'attributo ResponseCache ai singoli controller o azioni:</span><span class="sxs-lookup"><span data-stu-id="49db4-306">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }

    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="49db4-307">L'esempio precedente comporterà l'aggiunta della seguente intestazione alla risposta, indicando ai client di memorizzare nella cache il risultato fino a 60 secondi.</span><span class="sxs-lookup"><span data-stu-id="49db4-307">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="49db4-308">Cache-Control: public,max-age=60</span><span class="sxs-lookup"><span data-stu-id="49db4-308">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="49db4-309">Per aggiungere la memorizzazione nella cache in memoria sul lato server per l'applicazione, è necessario fare riferimento al pacchetto Microsoft.AspNetCore.ResponseCaching NuGet e quindi aggiungere il middleware di memorizzazione nella cache delle risposte.</span><span class="sxs-lookup"><span data-stu-id="49db4-309">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="49db4-310">Il middleware è configurato sia in ConfigureServices che in Configure in Startup:</span><span class="sxs-lookup"><span data-stu-id="49db4-310">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

<span data-ttu-id="49db4-311">Il middleware di memorizzazione nella cache delle risposte memorizzerà autenticamente le risposte sulla base di una serie di condizioni personalizzabili.</span><span class="sxs-lookup"><span data-stu-id="49db4-311">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="49db4-312">Per impostazione predefinita, vengono memorizzate nella cache solo risposte con codice di stato 200 (OK) tramite i metodi GET o HEAD.</span><span class="sxs-lookup"><span data-stu-id="49db4-312">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="49db4-313">È anche necessario che le richieste abbiano una risposta con intestazione pubblica Cache-Control e non includano le intestazioni Authorization o Set-Cookie.</span><span class="sxs-lookup"><span data-stu-id="49db4-313">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="49db4-314">Vedere l'[elenco completo delle condizioni di memorizzazione nella cache usato dal middleware di memorizzazione nella cache delle risposte](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="49db4-314">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="49db4-315">Memorizzazione nella cache dei dati</span><span class="sxs-lookup"><span data-stu-id="49db4-315">Data caching</span></span>

<span data-ttu-id="49db4-316">Anziché memorizzare nella cache tutte le risposte Web oppure oltre ad abilitare tale funzionalità, è possibile memorizzare nella cache i risultati delle singole query sui dati.</span><span class="sxs-lookup"><span data-stu-id="49db4-316">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="49db4-317">A tale scopo, è possibile usare la memorizzazione nella cache in memoria nel server Web, oppure una [cache distribuita](/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="49db4-317">For this, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="49db4-318">In questa sezione sarà illustrato come implementare la memorizzazione nella cache in memoria.</span><span class="sxs-lookup"><span data-stu-id="49db4-318">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="49db4-319">Aggiungere il supporto per la memorizzazione nella cache in memoria (o per la cache distribuita) in ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="49db4-319">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="49db4-320">Controllare che sia stato aggiunto anche il pacchetto NuGet Microsoft.Extensions.Caching.Memory.</span><span class="sxs-lookup"><span data-stu-id="49db4-320">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="49db4-321">Dopo aver aggiunto il servizio, le richieste vengono inviate a IMemoryCache tramite l'inserimento di dipendenze ogni volta che è necessario accedere alla cache.</span><span class="sxs-lookup"><span data-stu-id="49db4-321">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="49db4-322">In questo esempio CachedCatalogService usa lo schema progettuale Proxy (o Decorator), offrendo un'implementazione alternativa di ICatalogService che controlla l'accesso (o ne aggiunge il comportamento) all'implementazione di CatalogService sottostante.</span><span class="sxs-lookup"><span data-stu-id="49db4-322">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly string _itemsKeyTemplate = "items-{0}-{1}-{2}-{3}";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }

    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }

    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = String.Format(_itemsKeyTemplate, pageIndex, itemsPage, brandID, typeId);
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }

    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

<span data-ttu-id="49db4-323">Per configurare l'applicazione in modo che usi la versione del servizio memorizzata nella cache, consentendo tuttavia ancora al servizio di ottenere l'istanza di CatalogService necessaria nel relativo costruttore, aggiungere quanto segue in ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="49db4-323">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="49db4-324">A questo punto, le chiamate al database per recuperare i dati del catalogo verranno eseguite una sola volta al minuto, anziché a ogni richiesta.</span><span class="sxs-lookup"><span data-stu-id="49db4-324">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="49db4-325">In base al traffico destinato al sito, questa configurazione può avere un impatto significativo sul numero di query inviate al database e sul tempo medio di caricamento della home page che attualmente dipende da tutte e tre le query esposte da questo servizio.</span><span class="sxs-lookup"><span data-stu-id="49db4-325">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="49db4-326">Quando viene implementata la memorizzazione nella cache si verifica un problema correlato ai _dati non aggiornati_ , vale a dire i dati che sono stati modificati nell'origine, ma nella cache è rimasta una versione non aggiornata.</span><span class="sxs-lookup"><span data-stu-id="49db4-326">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="49db4-327">Un modo semplice per risolvere questo problema è usare durate della cache ridotte. Infatti, per un'applicazione occupata il vantaggio aggiuntivo di estendere la durata di memorizzazione nella cache dei dati è limitato.</span><span class="sxs-lookup"><span data-stu-id="49db4-327">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="49db4-328">Si consideri ad esempio una pagina che esegue un'unica query al database, richiedendola 10 volte al secondo.</span><span class="sxs-lookup"><span data-stu-id="49db4-328">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="49db4-329">Se questa pagina rimane memorizzata nella cache per un minuto, il numero di query al database ogni minuto diminuirà da 600 a 1, pari a una riduzione del 99,8%.</span><span class="sxs-lookup"><span data-stu-id="49db4-329">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="49db4-330">Se invece la durata della cache fosse di un'ora, la riduzione complessiva sarebbe del 99,997%, ma la probabilità e la potenziale durata dei dati non aggiornati aumentano considerevolmente.</span><span class="sxs-lookup"><span data-stu-id="49db4-330">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="49db4-331">Un altro approccio consiste nel rimuovere in modo proattivo le voci della cache quando vengono aggiornati i dati in esse contenuti.</span><span class="sxs-lookup"><span data-stu-id="49db4-331">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="49db4-332">È possibile rimuovere ogni singola voce se si conosce la relativa chiave:</span><span class="sxs-lookup"><span data-stu-id="49db4-332">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="49db4-333">Se l'applicazione espone la funzionalità per l'aggiornamento delle voci memorizzate nella cache, è possibile rimuovere le voci della cache corrispondenti nel codice che esegue gli aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="49db4-333">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="49db4-334">In alcuni casi potrebbero esistere numerose voci diverse che dipendono da un set di dati specifico.</span><span class="sxs-lookup"><span data-stu-id="49db4-334">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="49db4-335">In questo caso può essere utile creare dipendenze tra le voci della cache, usando un oggetto CancellationChangeToken,</span><span class="sxs-lookup"><span data-stu-id="49db4-335">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="49db4-336">che consente di annullare la validità di più voci della cache in una sola volta, annullando il token.</span><span class="sxs-lookup"><span data-stu-id="49db4-336">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

<span data-ttu-id="49db4-337">La memorizzazione nella cache può migliorare notevolmente le prestazioni delle pagine Web che richiedono più volte gli stessi valori dal database.</span><span class="sxs-lookup"><span data-stu-id="49db4-337">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="49db4-338">Assicurarsi di misurare le prestazioni di accesso ai dati e delle pagine prima di applicare la memorizzazione nella cache e applicarla solo dove si ritiene sia necessario un miglioramento.</span><span class="sxs-lookup"><span data-stu-id="49db4-338">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="49db4-339">La memorizzazione nella cache consuma le risorse di memoria del server Web e aumenta la complessità dell'applicazione, pertanto è importante non eseguire anzitempo l'ottimizzazione con questa tecnica.</span><span class="sxs-lookup"><span data-stu-id="49db4-339">Caching consumes web server memory resources and increases the complexity of the application, so it’s important you don’t prematurely optimize using this technique.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="49db4-340">[Precedente](develop-asp-net-core-mvc-apps.md)
>[Successivo](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="49db4-340">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>