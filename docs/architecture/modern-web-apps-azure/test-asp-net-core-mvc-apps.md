---
title: Testare app ASP.NET Core MVC
description: Progettare applicazioni Web moderne con ASP.NET Core e Azure | Testare app ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 941c73f9a8b7b4c4336adfaec45775feec738f51
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68672878"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="36816-103">Testare app ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="36816-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="36816-104">*"Non vi piace fare lo unit test dei vostri prodotti? Molto probabilmente non piacerà neanche ai vostri clienti."*</span><span class="sxs-lookup"><span data-stu-id="36816-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="36816-105">\_- Anonimo-</span><span class="sxs-lookup"><span data-stu-id="36816-105">\_- Anonymous-</span></span>

<span data-ttu-id="36816-106">Qualsiasi software, indipendentemente dalla complessità, può generare errori imprevisti dopo che è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="36816-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="36816-107">È quindi assolutamente necessario sottoporre a test tutte le applicazioni che non siano banali o poco importanti.</span><span class="sxs-lookup"><span data-stu-id="36816-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="36816-108">Il test manuale è il modo più lento, meno affidabile e più costoso per testare il software,</span><span class="sxs-lookup"><span data-stu-id="36816-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="36816-109">ma se le applicazioni non sono progettate per essere testabili, è l'unico modo disponibile.</span><span class="sxs-lookup"><span data-stu-id="36816-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="36816-110">Le applicazioni create secondo i principi architetturali descritti nel [capitolo 4](architectural-principles.md) devono supportare gli unit test. Le applicazioni ASP.NET Core supportano anche l'integrazione automatizzata e i test funzionali.</span><span class="sxs-lookup"><span data-stu-id="36816-110">Applications written following the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable, and ASP.NET Core applications support automated integration and functional testing as well.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="36816-111">Tipi di test automatizzati</span><span class="sxs-lookup"><span data-stu-id="36816-111">Kinds of automated tests</span></span>

<span data-ttu-id="36816-112">Esistono molti tipi di test automatizzati per le applicazioni software.</span><span class="sxs-lookup"><span data-stu-id="36816-112">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="36816-113">Il test più semplice e di livello più basso è lo unit test.</span><span class="sxs-lookup"><span data-stu-id="36816-113">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="36816-114">A un livello leggermente superiore si trovano i test di integrazione e i test funzionali.</span><span class="sxs-lookup"><span data-stu-id="36816-114">At a slightly higher level there are integration tests and functional tests.</span></span> <span data-ttu-id="36816-115">Altri tipi di test, come i test dell'interfaccia utente, i test di carico, test di stress e gli smoke test, non rientrano nell'ambito di questo documento.</span><span class="sxs-lookup"><span data-stu-id="36816-115">Other kinds of tests, like UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="36816-116">Unit test</span><span class="sxs-lookup"><span data-stu-id="36816-116">Unit tests</span></span>

<span data-ttu-id="36816-117">Uno unit test verifica una sola parte della logica dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="36816-117">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="36816-118">Un modo per descrivere meglio questo tipo di test consiste nell'elencare alcune caratteristiche che non ha.</span><span class="sxs-lookup"><span data-stu-id="36816-118">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="36816-119">Uno unit test non verifica il funzionamento del codice con le dipendenze e l'infrastruttura. Questo tipo di verifica viene effettuato dai test di integrazione.</span><span class="sxs-lookup"><span data-stu-id="36816-119">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="36816-120">Uno unit test non verifica il framework in cui è scritto il codice: si presuppone infatti che funzioni. Se invece si rilevano problemi, è necessario segnalare un bug e scrivere codice per una soluzione alternativa.</span><span class="sxs-lookup"><span data-stu-id="36816-120">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="36816-121">Uno unit test viene eseguito completamente in memoria e all'interno di un processo.</span><span class="sxs-lookup"><span data-stu-id="36816-121">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="36816-122">Non comunica con il file system, con la rete o con un database.</span><span class="sxs-lookup"><span data-stu-id="36816-122">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="36816-123">Gli unit test devono solo testare il codice.</span><span class="sxs-lookup"><span data-stu-id="36816-123">Unit tests should only test your code.</span></span>

<span data-ttu-id="36816-124">Gli unit test interessano solo una singola unità di codice, senza dipendenze esterne. La loro esecuzione, quindi, deve essere estremamente rapida</span><span class="sxs-lookup"><span data-stu-id="36816-124">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="36816-125">e consentire l'esecuzione di gruppi di centinaia di unit test in pochi secondi.</span><span class="sxs-lookup"><span data-stu-id="36816-125">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="36816-126">È necessario eseguirli spesso, idealmente prima di ogni push a un repository di controllo del codice sorgente condiviso e sicuramente in corrispondenza di ogni compilazione automatizzata eseguita nel server di compilazione.</span><span class="sxs-lookup"><span data-stu-id="36816-126">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="36816-127">Test di integrazione</span><span class="sxs-lookup"><span data-stu-id="36816-127">Integration tests</span></span>

<span data-ttu-id="36816-128">Incapsulare il codice che interagisce con l'infrastruttura, ad esempio con database e file system, è una buona idea, ma una parte di codice di questo tipo sarà comunque presente e sarà probabilmente necessario testarla.</span><span class="sxs-lookup"><span data-stu-id="36816-128">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="36816-129">È anche necessario verificare che i livelli del codice interagiscano nel modo previsto quando le dipendenze dell'applicazione sono completamente risolte.</span><span class="sxs-lookup"><span data-stu-id="36816-129">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="36816-130">Questo è compito dei test di integrazione.</span><span class="sxs-lookup"><span data-stu-id="36816-130">This is the responsibility of integration tests.</span></span> <span data-ttu-id="36816-131">I test di integrazione tendono a essere più lenti e più difficili da configurare rispetto agli unit test, perché spesso dipendono da dipendenze esterne e dall'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="36816-131">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="36816-132">Di conseguenza, è consigliabile evitare di testare all'interno di test di integrazione le parti di codice che possono essere testate tramite unit test.</span><span class="sxs-lookup"><span data-stu-id="36816-132">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="36816-133">Se è possibile testare uno scenario specifico con uno unit test, è consigliabile usare uno unit test.</span><span class="sxs-lookup"><span data-stu-id="36816-133">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="36816-134">Se non è possibile, è consigliabile prendere in considerazione l'uso di un test di integrazione.</span><span class="sxs-lookup"><span data-stu-id="36816-134">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="36816-135">Rispetto agli unit test, i test di integrazione prevedono una configurazione più complessa e procedure di disinstallazione più elaborate.</span><span class="sxs-lookup"><span data-stu-id="36816-135">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="36816-136">Un test di integrazione eseguito a fronte un database, ad esempio, deve prevedere il modo di riportare il database a uno stato noto prima dell'esecuzione di ogni test.</span><span class="sxs-lookup"><span data-stu-id="36816-136">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="36816-137">Man mano che vengono aggiunti nuovi test e lo schema del database cambia, questi script di test tendono ad aumentare di dimensioni e complessità.</span><span class="sxs-lookup"><span data-stu-id="36816-137">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="36816-138">In molti sistemi di grandi dimensioni non è pratico eseguire gruppi completi di test di integrazione nelle workstation degli sviluppatori prima di archiviare le modifiche nel controllo del codice sorgente condiviso.</span><span class="sxs-lookup"><span data-stu-id="36816-138">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="36816-139">In questi casi, è possibile eseguire i test di integrazione in un server di compilazione.</span><span class="sxs-lookup"><span data-stu-id="36816-139">In these cases, integration tests may be run on a build server.</span></span>

<span data-ttu-id="36816-140">La classe di implementazione `LocalFileImageService` implementa la logica per il recupero e la restituzione dei byte di un file di immagine da una cartella specifica, dato un ID:</span><span class="sxs-lookup"><span data-stu-id="36816-140">The `LocalFileImageService` implementation class implements the logic for fetching and returning the bytes of an image file from a particular folder given an id:</span></span>

```csharp
public class LocalFileImageService : IImageService
{
    private readonly IHostingEnvironment _env;
    public LocalFileImageService(IHostingEnvironment env)
    {
        _env = env;
    }
    public byte[] GetImageBytesById(int id)
    {
        try
        {
            var contentRoot = _env.ContentRootPath + "//Pics";
            var path = Path.Combine(contentRoot, id + ".png");
            return File.ReadAllBytes(path);
        }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

### <a name="functional-tests"></a><span data-ttu-id="36816-141">Test funzionali</span><span class="sxs-lookup"><span data-stu-id="36816-141">Functional tests</span></span>

<span data-ttu-id="36816-142">I test di integrazione vengono scritti dal punto di vista dello sviluppatore per verificare che alcuni componenti del sistema interagiscano correttamente.</span><span class="sxs-lookup"><span data-stu-id="36816-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="36816-143">I test funzionali vengono scritti dal punto di vista dell'utente e verificano la correttezza del sistema in base ai relativi requisiti.</span><span class="sxs-lookup"><span data-stu-id="36816-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="36816-144">Il brano seguente presenta un'analogia utile a chiarire il concetto di test funzionale rispetto agli unit test:</span><span class="sxs-lookup"><span data-stu-id="36816-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="36816-145">"Spesso lo sviluppo di un sistema viene paragonato alla costruzione di una casa.</span><span class="sxs-lookup"><span data-stu-id="36816-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="36816-146">Questa analogia non è completamente corretta, ma è possibile estenderla per consentire la comprensione delle differenze tra unit test e test funzionali.</span><span class="sxs-lookup"><span data-stu-id="36816-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="36816-147">Uno unit test può essere paragonato a un ispettore che visita il cantiere di un'abitazione.</span><span class="sxs-lookup"><span data-stu-id="36816-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="36816-148">L'ispettore concentra l'attenzione sulle varie parti interne della casa: le fondamenta, gli infissi, l'impianto elettrico, quello idraulico e così via,</span><span class="sxs-lookup"><span data-stu-id="36816-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="36816-149">per assicurarsi (testare) che le parti della casa funzionino correttamente e in modo sicuro, ovvero soddisfino le normative edilizie (il codice di compilazione).</span><span class="sxs-lookup"><span data-stu-id="36816-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="36816-150">In questo scenario, i test funzionali sono paragonabili al proprietario della casa che visita questo stesso cantiere.</span><span class="sxs-lookup"><span data-stu-id="36816-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="36816-151">Il proprietario presuppone che gli impianti interni della casa funzionino come si deve, dato che di questo si occupa l'ispettore.</span><span class="sxs-lookup"><span data-stu-id="36816-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="36816-152">Il proprietario concentra l'attenzione sulla qualità della vita in quella casa,</span><span class="sxs-lookup"><span data-stu-id="36816-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="36816-153">preoccupandosi dell'aspetto della casa stessa, dell'adeguatezza delle dimensioni delle stanze, della capacità della casa di soddisfare le esigenze della famiglia e dell'orientamento delle finestre, che devono lasciar entrare il sole del mattino.</span><span class="sxs-lookup"><span data-stu-id="36816-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="36816-154">Il proprietario esegue il test funzionale della casa.</span><span class="sxs-lookup"><span data-stu-id="36816-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="36816-155">Il suo punto di vista è quello dell'utente finale.</span><span class="sxs-lookup"><span data-stu-id="36816-155">He has the user's perspective.</span></span> <span data-ttu-id="36816-156">L'ispettore esegue gli unit test della casa.</span><span class="sxs-lookup"><span data-stu-id="36816-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="36816-157">Il suo punto di vista è quello del compilatore."</span><span class="sxs-lookup"><span data-stu-id="36816-157">He has the builder's perspective."</span></span>

<span data-ttu-id="36816-158">Fonte: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html) (Unit test e test funzionali)</span><span class="sxs-lookup"><span data-stu-id="36816-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="36816-159">Gli sviluppatori possono sbagliare in due modi: creando una cosa nel modo sbagliato o creando la cosa sbagliata.</span><span class="sxs-lookup"><span data-stu-id="36816-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="36816-160">Gli unit test consentono di verificare che si stia creando qualcosa nel modo corretto. I test funzionali consentono di verificare che si stia creando la cosa giusta.</span><span class="sxs-lookup"><span data-stu-id="36816-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="36816-161">Dato che i test funzionali operano a livello di sistema, possono richiedere un certo grado di automazione dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="36816-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="36816-162">Analogamente ai test di integrazione, in genere usano anche un certo tipo di infrastruttura di test.</span><span class="sxs-lookup"><span data-stu-id="36816-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="36816-163">Ciò li rende più lenti e meno solidi degli unit test e dei test di integrazione.</span><span class="sxs-lookup"><span data-stu-id="36816-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="36816-164">Per avere la certezza che il sistema funzioni come gli utenti si aspettano, è necessario avere solo il numero di test funzionali strettamente necessario.</span><span class="sxs-lookup"><span data-stu-id="36816-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="36816-165">Piramide dei test</span><span class="sxs-lookup"><span data-stu-id="36816-165">Testing Pyramid</span></span>

<span data-ttu-id="36816-166">La piramide dei test, un esempio della quale è illustrato nella Figura 9-1, è stato trattato da Martin Fowler.</span><span class="sxs-lookup"><span data-stu-id="36816-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![](./media/image9-1.png)

<span data-ttu-id="36816-167">Figura 9-1 Piramide dei test</span><span class="sxs-lookup"><span data-stu-id="36816-167">Figure 9-1 Testing Pyramid</span></span>

<span data-ttu-id="36816-168">I diversi livelli della piramide e le dimensioni relative rappresentano i diversi tipi di test e il numero di test che è consigliabile scrivere per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="36816-168">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="36816-169">Come si può notare, è consigliabile avere una base ampia di unit test, supportata da un livello di test di integrazione di dimensioni inferiori, con un livello di dimensioni ancora inferiori di test funzionali.</span><span class="sxs-lookup"><span data-stu-id="36816-169">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="36816-170">Ogni livello in linea di principio deve contenere solo test che non possono essere eseguiti in modo adeguato a un livello inferiore.</span><span class="sxs-lookup"><span data-stu-id="36816-170">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="36816-171">Tenere presente la piramide dei test quando si deve decidere il tipo di test necessario per uno scenario specifico.</span><span class="sxs-lookup"><span data-stu-id="36816-171">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="36816-172">Cosa testare</span><span class="sxs-lookup"><span data-stu-id="36816-172">What to test</span></span>

<span data-ttu-id="36816-173">Un problema comune agli sviluppatori che non hanno dimestichezza con la scrittura di test automatizzati è decidere che cosa testare.</span><span class="sxs-lookup"><span data-stu-id="36816-173">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="36816-174">Un buon punto di partenza è il test della logica condizionale.</span><span class="sxs-lookup"><span data-stu-id="36816-174">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="36816-175">Ovunque sia presente un metodo il cui comportamento cambia in base a un'istruzione condizionale (if-else, switch e così via), è necessario creare almeno un paio di test che confermino la correttezza del comportamento per determinate condizioni.</span><span class="sxs-lookup"><span data-stu-id="36816-175">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, etc.), you should be able to come up at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="36816-176">Se il codice prevede condizioni di errore, è consigliabile scrivere almeno un test per il percorso corretto attraverso il codice (senza errori) e almeno un test per il percorso non corretto (con errori o risultati atipici) per confermare che l'applicazione si comporti come previsto in caso di errori.</span><span class="sxs-lookup"><span data-stu-id="36816-176">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="36816-177">Provare infine a concentrarsi sul test delle operazioni che possono non riuscire, piuttosto che su metriche quali il code coverage.</span><span class="sxs-lookup"><span data-stu-id="36816-177">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="36816-178">Un code coverage maggiore è meglio di un code coverage minore, in genere,</span><span class="sxs-lookup"><span data-stu-id="36816-178">More code coverage is better than less, generally.</span></span> <span data-ttu-id="36816-179">ma il tempo impiegato a scrivere qualche test in più per un metodo molto complesso e di importanza critica è di solito meglio impiegato rispetto al tempo speso a scrivere test per le proprietà automatiche per migliorare la metrica di code coverage.</span><span class="sxs-lookup"><span data-stu-id="36816-179">However, writing a few more tests of a very complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="36816-180">Organizzazione dei progetti di test</span><span class="sxs-lookup"><span data-stu-id="36816-180">Organizing test projects</span></span>

<span data-ttu-id="36816-181">È possibile organizzare i progetti di test nel modo che si ritiene più efficiente per le proprie esigenze.</span><span class="sxs-lookup"><span data-stu-id="36816-181">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="36816-182">È consigliabile suddividere i test per tipo (unit test, test di integrazione) e per oggetto del test (progetto, spazio dei nomi).</span><span class="sxs-lookup"><span data-stu-id="36816-182">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="36816-183">Se questa suddivisione debba essere realizzata tramite cartelle all'interno di un unico progetto di test o tramite più progetti di test è una decisione che viene presa a livello di progettazione.</span><span class="sxs-lookup"><span data-stu-id="36816-183">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="36816-184">Un solo progetto è la soluzione più semplice, ma per progetti di grandi dimensioni con molti test o per eseguire set diversi di test più facilmente, è consigliabile avere più progetti di test diversi.</span><span class="sxs-lookup"><span data-stu-id="36816-184">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="36816-185">Molti team organizzano i progetti di test in base al progetto sottoposto a test. Per le applicazioni che non si limitano a un numero ridotto di progetti, questa soluzione può comportare un numero elevato di progetti di test, soprattutto se questi vengono ancora suddivisi in base al tipo di test che contengono.</span><span class="sxs-lookup"><span data-stu-id="36816-185">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="36816-186">Un approccio di compromesso può essere di avere un progetto per tipo di test per applicazione, con cartelle all'interno dei progetti di test per indicare il progetto e la classe sottoposti a test.</span><span class="sxs-lookup"><span data-stu-id="36816-186">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="36816-187">Un approccio comune consiste nell'organizzare i progetti dell'applicazione in una cartella 'src' e i progetti di test dell'applicazione in una cartella 'tests' parallela.</span><span class="sxs-lookup"><span data-stu-id="36816-187">A common approach is to organize the application projects under a ‘src' folder, and the application's test projects under a parallel ‘tests' folder.</span></span> <span data-ttu-id="36816-188">Nel caso si ritenga utile questo tipo di organizzazione, Visual Studio consente di creare cartelle della soluzione corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="36816-188">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![](./media/image9-2.png)

<span data-ttu-id="36816-189">Figura 9-2 Organizzazione dei test nella soluzione</span><span class="sxs-lookup"><span data-stu-id="36816-189">Figure 9-2 Test organization in your solution</span></span>

<span data-ttu-id="36816-190">È possibile usare qualsiasi framework di test si preferisca.</span><span class="sxs-lookup"><span data-stu-id="36816-190">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="36816-191">Il framework xUnit, in cui sono scritti tutti i test di ASP.NET Core ed EF Core, funziona in modo efficiente.</span><span class="sxs-lookup"><span data-stu-id="36816-191">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="36816-192">È possibile aggiungere un progetto di test xUnit in Visual Studio usando il modello illustrato nella figura 9-3 oppure usando il comando dotnet new xunit nell'interfaccia della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="36816-192">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using dotnet new xunit.</span></span>

![](./media/image9-3.png)

<span data-ttu-id="36816-193">Figura 9-3 aggiungere un progetto di test xUnit in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="36816-193">Figure 9-3 Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="36816-194">Denominazione dei test</span><span class="sxs-lookup"><span data-stu-id="36816-194">Test naming</span></span>

<span data-ttu-id="36816-195">È consigliabile assegnare ai test nomi coerenti che indichino il tipo di test eseguito.</span><span class="sxs-lookup"><span data-stu-id="36816-195">You should name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="36816-196">Un approccio molto efficace è assegnare alle classi di test nomi basati sulla classe e sul metodo testato.</span><span class="sxs-lookup"><span data-stu-id="36816-196">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="36816-197">Il risultato è un numero elevato di classi di test, ma la funzione di ogni test è estremamente chiara.</span><span class="sxs-lookup"><span data-stu-id="36816-197">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="36816-198">Con il nome della classe di test impostato per identificare la classe e il metodo da sottoporre a test, è possibile usare il nome di ogni metodo di test per specificare il comportamento sottoposto a test.</span><span class="sxs-lookup"><span data-stu-id="36816-198">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="36816-199">Deve essere incluso il comportamento previsto e l'eventuale input o gli eventuali presupposti che devono generare questo comportamento.</span><span class="sxs-lookup"><span data-stu-id="36816-199">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="36816-200">Ecco alcuni esempi di nomi di test:</span><span class="sxs-lookup"><span data-stu-id="36816-200">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="36816-201">Una variante di questo approccio consiste nel terminare ogni nome di classe di test con "Should" e nel modificare leggermente i tempi verbali:</span><span class="sxs-lookup"><span data-stu-id="36816-201">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="36816-202">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="36816-202">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="36816-203">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="36816-203">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="36816-204">Alcuni team trovano il secondo approccio più chiaro, anche se leggermente più prolisso.</span><span class="sxs-lookup"><span data-stu-id="36816-204">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="36816-205">In ogni caso, è consigliabile usare una convenzione di denominazione che consenta di comprendere il comportamento del test. In questo modo, se uno o più test hanno esito negativo, risulta evidente dai nomi quali casi non sono riusciti.</span><span class="sxs-lookup"><span data-stu-id="36816-205">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="36816-206">Evitare di denominare i test in modo generico, ad esempio ControllerTests.Test1, perché questi nomi non hanno alcun valore quando vengono visualizzati nei risultati dei test.</span><span class="sxs-lookup"><span data-stu-id="36816-206">Avoid naming you tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="36816-207">Se si segue una convenzione di denominazione simile a quella illustrata sopra, che genera molte classi di test di piccole dimensioni, è consigliabile organizzare ulteriormente i test tramite cartelle e spazi dei nomi.</span><span class="sxs-lookup"><span data-stu-id="36816-207">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="36816-208">La figura 9-4 illustra un approccio di organizzazione dei test per cartella all'interno di diversi progetti di test.</span><span class="sxs-lookup"><span data-stu-id="36816-208">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![](./media/image9-4.png)

<span data-ttu-id="36816-209">**Figura 9-4.**</span><span class="sxs-lookup"><span data-stu-id="36816-209">**Figure 9-4.**</span></span> <span data-ttu-id="36816-210">Organizzazione delle classi di test per cartella in base alla classe da testare.</span><span class="sxs-lookup"><span data-stu-id="36816-210">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="36816-211">È ovvio che, se per una classe di applicazione specifica vengono testati molti metodi (e quindi esistono molte classi di test), può essere utile inserirli in una cartella corrispondente alla classe stessa.</span><span class="sxs-lookup"><span data-stu-id="36816-211">Of course, if a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="36816-212">Questo tipo di organizzazione è analogo all'organizzazione di file in cartelle in un altro contesto.</span><span class="sxs-lookup"><span data-stu-id="36816-212">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="36816-213">Se si hanno più di tre o quattro file correlati in una cartella contenente molti altri file, è spesso utile spostare i primi in una sottocartella specifica.</span><span class="sxs-lookup"><span data-stu-id="36816-213">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="36816-214">Unit test di app ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="36816-214">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="36816-215">In un'applicazione ASP.NET Core ben progettata, la maggior parte della complessità e della logica di business viene incapsulata in entità di business e in una varietà di servizi.</span><span class="sxs-lookup"><span data-stu-id="36816-215">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="36816-216">L'app ASP.NET Core MVC stessa, con i controller, i filtri, i ViewModel e le visualizzazioni, deve richiedere un numero molto ridotto di unit test.</span><span class="sxs-lookup"><span data-stu-id="36816-216">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="36816-217">Buona parte delle funzionalità di un'azione specifica si trova all'esterno del metodo di azione stesso.</span><span class="sxs-lookup"><span data-stu-id="36816-217">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="36816-218">Il test del funzionamento del routing o la gestione globale degli errori non può essere eseguita in modo efficiente con uno unit test.</span><span class="sxs-lookup"><span data-stu-id="36816-218">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="36816-219">Analogamente, non è possibile eseguire unit test di filtri, inclusi i filtri di convalida di modelli, di autenticazione e di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="36816-219">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested.</span></span> <span data-ttu-id="36816-220">Senza queste origini di comportamento, la maggior parte dei metodi di azione sarebbero incredibilmente piccoli e delegherebbero la maggior parte delle proprie funzioni a servizi che possono essere testati indipendentemente dal controller che li usa.</span><span class="sxs-lookup"><span data-stu-id="36816-220">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="36816-221">In alcuni casi, per eseguire lo unit test del codice è necessario effettuare il refactoring di quest'ultimo.</span><span class="sxs-lookup"><span data-stu-id="36816-221">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="36816-222">Spesso ciò comporta l'identificazione di astrazioni e l'uso dell'inserimento di dipendenze per accedere all'astrazione nel codice che si vuole testare, anziché la scrittura di codice direttamente a fronte dell'infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="36816-222">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="36816-223">Si consideri ad esempio, questo semplice metodo di azione per la visualizzazione di immagini:</span><span class="sxs-lookup"><span data-stu-id="36816-223">For example, consider this simple action method for displaying images:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

<span data-ttu-id="36816-224">Il testing unità di questo metodo è reso difficile dalla dipendenza diretta da `System.IO.File`, usato per leggere dal file system.</span><span class="sxs-lookup"><span data-stu-id="36816-224">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="36816-225">È possibile testare questo comportamento per assicurarsi che funzioni come previsto, ma facendo questo con file reali si esegue un test di integrazione.</span><span class="sxs-lookup"><span data-stu-id="36816-225">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="36816-226">Si noti che non è possibile applicare uno unit test alla route di questo metodo. Più avanti si vedrà come eseguire questa operazione con un test funzionale.</span><span class="sxs-lookup"><span data-stu-id="36816-226">It's worth noting you can't unit test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="36816-227">Se non è possibile eseguire direttamente lo unit test del comportamento del file system e non è possibile testare la route, cosa è possibile testare?</span><span class="sxs-lookup"><span data-stu-id="36816-227">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="36816-228">Dopo aver effettuato il refactoring per rendere possibile l'esecuzione di unit test, si possono individuare alcuni test case e comportamenti mancanti, ad esempio la gestione degli errori.</span><span class="sxs-lookup"><span data-stu-id="36816-228">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="36816-229">Che cosa fa il metodo quando non trova un file?</span><span class="sxs-lookup"><span data-stu-id="36816-229">What does the method do when a file isn't found?</span></span> <span data-ttu-id="36816-230">Cosa deve fare?</span><span class="sxs-lookup"><span data-stu-id="36816-230">What should it do?</span></span> <span data-ttu-id="36816-231">In questo esempio, il metodo sottoposto a refactoring ha l'aspetto seguente:</span><span class="sxs-lookup"><span data-stu-id="36816-231">In this example, the refactored method looks like this:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")\]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

<span data-ttu-id="36816-232">\_logger e \_imageService sono entrambi inseriti come dipendenze.</span><span class="sxs-lookup"><span data-stu-id="36816-232">The \_logger and \_imageService are both injected as dependencies.</span></span> <span data-ttu-id="36816-233">È ora possibile verificare che lo stesso ID che viene passato al metodo di azione venga passato a \_imageService, e che i byte risultanti vengano restituiti come parte di FileResult.</span><span class="sxs-lookup"><span data-stu-id="36816-233">Now you can test that the same id that is passed to the action method is passed to the \_imageService, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="36816-234">È anche possibile verificare che la registrazione degli errori venga eseguita come previsto e che venga restituito un risultato NotFound se l'immagine manca, presupponendo che questo rappresenti un comportamento importante dell'applicazione, in altre parole, che non sia solo codice temporaneo aggiunto dallo sviluppatore per diagnosticare un problema.</span><span class="sxs-lookup"><span data-stu-id="36816-234">You can also test that error logging is happening as expected, and that a NotFound result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="36816-235">La logica effettiva del file è stata spostata in un servizio di implementazione separato ed è stata migliorata perché venga restituita un'eccezione specifica dell'applicazione in caso di mancanza di un file.</span><span class="sxs-lookup"><span data-stu-id="36816-235">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="36816-236">È possibile testare questa implementazione in modo indipendente, usando un test di integrazione.</span><span class="sxs-lookup"><span data-stu-id="36816-236">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="36816-237">Nella maggior parte dei casi è opportuno usare i gestori di eccezioni globali nei controller, per ridurre al minimo la quantità di codice e di conseguenza la necessità di esecuzione di unit test.</span><span class="sxs-lookup"><span data-stu-id="36816-237">In most cases, you’ll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="36816-238">È consigliabile eseguire la maggior parte dei test di azioni dei controller mediante i test funzionali e la classe `TestServer` descritta di seguito.</span><span class="sxs-lookup"><span data-stu-id="36816-238">You should do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="36816-239">Test di integrazione di app ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="36816-239">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="36816-240">La maggior parte dei test di integrazione nelle app ASP.NET Core dovrebbe riguardare test dei servizi e degli altri tipi di implementazione definiti nel progetto di infrastruttura.</span><span class="sxs-lookup"><span data-stu-id="36816-240">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="36816-241">Ad esempio, è possibile [verificare che EF Core abbia completato l'aggiornamento e il recupero dei dati previsti](https://docs.microsoft.com/ef/core/miscellaneous/testing/) da classi di accesso di dati che si trovano nel progetto Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="36816-241">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](https://docs.microsoft.com/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="36816-242">Il modo migliore per verificare che il progetto ASP.NET Core MVC funzioni correttamente è l'esecuzione di test funzionali sull'app in esecuzione in un host di test.</span><span class="sxs-lookup"><span data-stu-id="36816-242">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="36816-243">Test funzionale di app ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="36816-243">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="36816-244">Per le applicazioni ASP.NET Core, la classe `TestServer` semplifica notevolmente la scrittura di test funzionali.</span><span class="sxs-lookup"><span data-stu-id="36816-244">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="36816-245">Si configura un elemento `TestServer` usando direttamente `WebHostBuilder` (come nella procedura standard usata per l'applicazione) o con il tipo `WebApplicationFactory` (disponibile a partire dalla versione 2.1).</span><span class="sxs-lookup"><span data-stu-id="36816-245">You configure a `TestServer` using a `WebHostBuilder` directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="36816-246">È consigliabile cercare la corrispondenza più esatta possibile tra l'host di test e l'host di produzione, in modo che i test abbiano un comportamento simile a quello dell'app in produzione.</span><span class="sxs-lookup"><span data-stu-id="36816-246">You should try to match your test host to your production host as closely as possible, so your tests will exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="36816-247">La classe `WebApplicationFactory` è utile per configurare ContentRoot di TestServer, che viene usata da ASP.NET Core per trovare una risorsa statica come Views.</span><span class="sxs-lookup"><span data-stu-id="36816-247">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="36816-248">È possibile generare test funzionali semplici creando una classe di test che implementa IClassFixture \<WebApplicationFactoryTEntry\<>>, dove TEntry è la classe Startup dell'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="36816-248">You can create simple functional tests by creating a test class that implements IClassFixture\<WebApplicationFactory\<TEntry>> where TEntry is your web application's Startup class.</span></span> <span data-ttu-id="36816-249">In questo modo, la fixture di test può creare un client usando il metodo CreateClient della factory:</span><span class="sxs-lookup"><span data-stu-id="36816-249">With this in place, your test fixture can create a client using the factory's CreateClient method:</span></span>

```cs
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BaseWebTest(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

<span data-ttu-id="36816-250">Spesso, prima dell'esecuzione di ogni test è necessario eseguire un'ulteriore configurazione del sito, ad esempio la configurazione dell'applicazione per l'uso di un archivio dati in memoria e il seeding dell'applicazione con i dati di test.</span><span class="sxs-lookup"><span data-stu-id="36816-250">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="36816-251">A tale scopo, è necessario creare una sottoclasse di WebApplicationFactory\<TEntry> ed eseguire l'override del metodo ConfigureWebHost.</span><span class="sxs-lookup"><span data-stu-id="36816-251">To do this, you should create your own subclass of WebApplicationFactory\<TEntry> and override its ConfigureWebHost method.</span></span> <span data-ttu-id="36816-252">L'esempio seguente è tratto dal progetto FunctionalTests di eShopOnWeb e viene usato come parte dei test sull'applicazione Web principale.</span><span class="sxs-lookup"><span data-stu-id="36816-252">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

```cs
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web.Controllers
{
    public class CustomWebApplicationFactory<TStartup>
    : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.ConfigureServices(services =>
            {
                // Create a new service provider.
                var serviceProvider = new ServiceCollection()
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory 
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<CustomWebApplicationFactory<TStartup>>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

<span data-ttu-id="36816-253">I test possono usare questa WebApplicationFactory personalizzata per creare un client e formulare quindi le richieste all'applicazione usando questa istanza del client.</span><span class="sxs-lookup"><span data-stu-id="36816-253">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="36816-254">L'applicazione avrà effettuato il seeding dei dati utilizzabili come parte delle asserzioni del test.</span><span class="sxs-lookup"><span data-stu-id="36816-254">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="36816-255">Il test seguente verifica che la home page dell'applicazione eShopOnWeb si carichi correttamente e includa un elenco di prodotti già aggiunto all'applicazione come parte dei dati iniziali.</span><span class="sxs-lookup"><span data-stu-id="36816-255">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

```cs
using Microsoft.eShopWeb.FunctionalTests.Web.Controllers;
using Microsoft.eShopWeb.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    public class HomePageOnGet : IClassFixture<CustomWebApplicationFactory<Startup>>
    {
        public HomePageOnGet(CustomWebApplicationFactory<Startup> factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse);
        }
    }
}
```

<span data-ttu-id="36816-256">Questo test funzionale interessa tutto lo stack dell'applicazione ASP.NET Core MVC / Razor Pages, inclusi tutti i middleware, i filtri, i binder e così via eventualmente presenti.</span><span class="sxs-lookup"><span data-stu-id="36816-256">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="36816-257">Verifica che una determinata route ("/") restituisca il codice di stato riuscito e l'output HTML previsti.</span><span class="sxs-lookup"><span data-stu-id="36816-257">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="36816-258">Questa verifica viene eseguita senza la configurazione di un server Web reale ed è quindi possibile evitare gran parte degli inconvenienti che l'uso di un server Web reale può comportare (ad esempio, problemi con le impostazioni del firewall).</span><span class="sxs-lookup"><span data-stu-id="36816-258">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="36816-259">I test funzionali eseguiti su TestServer sono in genere più lenti rispetto ai test di integrazione e agli unit test, ma sono molto più veloci rispetto a test eseguiti attraverso la rete per un server Web.</span><span class="sxs-lookup"><span data-stu-id="36816-259">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="36816-260">È consigliabile usare test funzionali per garantire che lo stack front-end dell'applicazione funzioni come previsto.</span><span class="sxs-lookup"><span data-stu-id="36816-260">You should use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="36816-261">Questi test sono particolarmente utili quando si trova la duplicazione nei controller o nelle pagine e la si risolve aggiungendo filtri.</span><span class="sxs-lookup"><span data-stu-id="36816-261">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="36816-262">In teoria questo refactoring non modifica il comportamento dell'applicazione e ciò sarà verificabile tramite un gruppo di test funzionali.</span><span class="sxs-lookup"><span data-stu-id="36816-262">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="36816-263">Riferimenti: testare app ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="36816-263">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="36816-264">**Test e debug in ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="36816-264">**Testing in ASP.NET Core**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="36816-265">**Convenzione di denominazione di unit test**</span><span class="sxs-lookup"><span data-stu-id="36816-265">**Unit Test Naming Convention**</span></span>  
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="36816-266">**Test di EF Core**</span><span class="sxs-lookup"><span data-stu-id="36816-266">**Testing EF Core**</span></span>  
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>

>[!div class="step-by-step"]
><span data-ttu-id="36816-267">[Precedente](work-with-data-in-asp-net-core-apps.md)
>[Successivo](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="36816-267">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>