---
title: Protezione di microservizi e applicazioni Web .NET
description: Protezione di microservizi e applicazioni Web .NET - Informazioni sulle opzioni di autenticazione per le applicazioni Web ASP.NET Core.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 0894465858e3503e2eddb5299b404f7ba95fdd6a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296475"
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="a9ac0-103">Proteggere i microservizi e le applicazioni Web .NET</span><span class="sxs-lookup"><span data-stu-id="a9ac0-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="a9ac0-104">La protezione dei microservizi e delle applicazioni Web è un argomento molto vasto e con un gran numero di aspetti diversi. Questa sezione si concentra sull'autenticazione, l'autorizzazione e i segreti dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="a9ac0-105">Implementare l'autenticazione in microservizi e applicazioni Web .NET</span><span class="sxs-lookup"><span data-stu-id="a9ac0-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="a9ac0-106">In molti casi è necessario che le risorse e le API pubblicate da un servizio siano limitate a determinati utenti o client attendibili.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="a9ac0-107">Il primo passaggio per prendere questo tipo di decisioni sull'attendibilità a livello di API è l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="a9ac0-108">L'autenticazione è il processo con il quale si verifica in modo affidabile l'identità di un utente.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="a9ac0-109">In scenari con microservizi, l'autenticazione viene in genere gestita a livello centrale.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="a9ac0-110">Se si usa un gateway API il gateway è un ottimo strumento per l'autenticazione, come illustrato nella figura 9-1.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="a9ac0-111">Se si usa questo approccio, assicurarsi che i singoli microservizi non possano essere raggiunti direttamente (senza il gateway API), a meno che non sia presente un sistema di sicurezza aggiuntivo per autenticare i messaggi, indipendentemente dal fatto che provengano dal gateway.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![Quando il gateway API centralizza l'autenticazione, aggiunge le informazioni utente al momento dell'inoltro delle richieste ai microservizi.](./media/image1.png)

<span data-ttu-id="a9ac0-113">**Figura 9-1**.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-113">**Figure 9-1**.</span></span> <span data-ttu-id="a9ac0-114">Autenticazione centralizzata con un gateway API</span><span class="sxs-lookup"><span data-stu-id="a9ac0-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="a9ac0-115">Se è possibile accedere direttamente ai servizi, per autenticare gli utenti è possibile usare un servizio di autenticazione come Azure Active Directory o un microservizio di autenticazione dedicato con funzione di servizio token di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-115">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="a9ac0-116">Le decisioni sull'attendibilità vengono condivise tra i servizi con i token di sicurezza o i cookie.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-116">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="a9ac0-117">(Questi token possono essere condivisi tra le applicazioni ASP.NET Core, se necessario, implementando la [condivisione dei cookie](/aspnet/core/security/cookie-sharing).) Questo scenario è illustrato nella figura 9-2.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-117">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Quando l'accesso ai i microservizi è diretto, l'attendibilità, che include autenticazione e autorizzazione, viene gestita da un token di sicurezza emesso da un microservizio dedicato, condiviso tra i microservizi.](./media/image2.png)

<span data-ttu-id="a9ac0-119">**Figura 9-2**.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-119">**Figure 9-2**.</span></span> <span data-ttu-id="a9ac0-120">Autenticazione mediante microservizio di identità; l'attendibilità è condivisa con un token di autorizzazione</span><span class="sxs-lookup"><span data-stu-id="a9ac0-120">Authentication by identity microservice; trust is shared using an authorization token</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="a9ac0-121">Autenticazione tramite ASP.NET Core Identity</span><span class="sxs-lookup"><span data-stu-id="a9ac0-121">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="a9ac0-122">Il meccanismo principale in ASP.NET Core per identificare gli utenti di un'applicazione è il sistema di appartenenze [ASP.NET Core Identity](/aspnet/core/security/authentication/identity).</span><span class="sxs-lookup"><span data-stu-id="a9ac0-122">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="a9ac0-123">ASP.NET Core Identity archivia informazioni sugli utenti (comprese le informazioni di accesso, i ruoli e le attestazioni) in un archivio dati configurato dallo sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-123">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="a9ac0-124">In genere l'archivio dati di ASP.NET Core Identity è un archivio Entity Framework incluso nel pacchetto `Microsoft.AspNetCore.Identity.EntityFrameworkCore`.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-124">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="a9ac0-125">È tuttavia possibile usare archivi personalizzati o altri pacchetti di terze parti per archiviare le informazioni sull'identità in Archiviazione tabelle di Azure, in CosmosDB o in altre posizioni.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-125">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

<span data-ttu-id="a9ac0-126">Il codice seguente proviene dal modello di progetto applicazione Web di ASP.NET Core con l'autenticazione dell'account utente singolo selezionata.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-126">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="a9ac0-127">Illustra come configurare ASP.NET Core Identity tramite EntityFramework.Core nel metodo Startup.ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-127">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="a9ac0-128">Dopo la configurazione, ASP.NET Core Identity può essere abilitato chiamando app.UseIdentity nel metodo `Startup.Configure` del servizio.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-128">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s `Startup.Configure` method.</span></span>

<span data-ttu-id="a9ac0-129">L'uso di ASP.NET Core Identity consente diversi scenari:</span><span class="sxs-lookup"><span data-stu-id="a9ac0-129">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="a9ac0-130">Creazione di nuove informazioni utente usando il tipo UserManager (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="a9ac0-130">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="a9ac0-131">Autenticazione degli utenti tramite il tipo SignInManager.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-131">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="a9ac0-132">È possibile usare `signInManager.SignInAsync` per l'accesso diretto o `signInManager.PasswordSignInAsync` per confermare che la password dell'utente sia corretta e quindi consentire l'accesso.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-132">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="a9ac0-133">Identificazione di un utente in base alle informazioni archiviate in un cookie (che viene letto dal middleware di ASP.NET Core Identity) in modo che le successive richieste provenienti da un browser includeranno l'identità e le attestazioni dell'utente connesso.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-133">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="a9ac0-134">ASP.NET Core Identity supporta inoltre l'[autenticazione a due fattori](/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="a9ac0-134">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="a9ac0-135">Per scenari di autenticazione che usano dell'archivio dati degli utenti locale e vengono salvano in modo permanente l'identità tra le richieste tramite dei cookie (come avviene per le applicazioni web MVC), ASP.NET Identity Core è una soluzione consigliata.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-135">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="a9ac0-136">Eseguire l'autenticazione tramite provider esterni</span><span class="sxs-lookup"><span data-stu-id="a9ac0-136">Authenticate with external providers</span></span>

<span data-ttu-id="a9ac0-137">ASP.NET Core supporta anche l'uso di [provider di autenticazione esterni](/aspnet/core/security/authentication/social/) per consentire agli utenti di accedere tramite flussi di [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2).</span><span class="sxs-lookup"><span data-stu-id="a9ac0-137">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="a9ac0-138">Ciò significa che gli utenti possono accedere con processi di autenticazione esistenti di provider come Microsoft, Google, Facebook o Twitter e associare queste identità a un'identità di ASP.NET Core nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-138">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="a9ac0-139">Per usare l'autenticazione esterna, includere il middleware di autenticazione appropriato nella pipeline di elaborazione della richiesta HTTP dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-139">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="a9ac0-140">Questo middleware è responsabile della gestione delle richieste di route URI dal provider di autenticazione, dell'acquisizione di informazioni di identità e della messa a disponibile delle stesse tramite il metodo SignInManager.GetExternalLoginInfo.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-140">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="a9ac0-141">Alcuni provider di autenticazione esterni comuni e i pacchetti NuGet associati sono elencati nella tabella seguente:</span><span class="sxs-lookup"><span data-stu-id="a9ac0-141">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="a9ac0-142">**Provider**</span><span class="sxs-lookup"><span data-stu-id="a9ac0-142">**Provider**</span></span>  | <span data-ttu-id="a9ac0-143">**Pacchetto**</span><span class="sxs-lookup"><span data-stu-id="a9ac0-143">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="a9ac0-144">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="a9ac0-144">**Microsoft**</span></span> | <span data-ttu-id="a9ac0-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="a9ac0-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="a9ac0-146">**Google**</span><span class="sxs-lookup"><span data-stu-id="a9ac0-146">**Google**</span></span>    | <span data-ttu-id="a9ac0-147">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="a9ac0-147">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="a9ac0-148">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="a9ac0-148">**Facebook**</span></span>  | <span data-ttu-id="a9ac0-149">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="a9ac0-149">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="a9ac0-150">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="a9ac0-150">**Twitter**</span></span>   | <span data-ttu-id="a9ac0-151">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="a9ac0-151">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="a9ac0-152">In tutti i casi il middleware è registrato con una chiamata a un metodo di registrazione simile a `app.Use{ExternalProvider}Authentication` in `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-152">In all cases, the middleware is registered with a call to a registration method similar to `app.Use{ExternalProvider}Authentication` in `Startup.Configure`.</span></span> <span data-ttu-id="a9ac0-153">Questi metodi di registrazione accettano un oggetto di opzioni che contiene un ID applicazione e informazioni segrete (una password, ad esempio), in base alle esigenze dal provider.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-153">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="a9ac0-154">I provider di autenticazione esterni richiedono la registrazione dell'applicazione (come spiegato nella [documentazione di ASP.NET Core](/aspnet/core/security/authentication/social/)) per poter informare l'utente di quale applicazione richiede l'accesso alla sua identità.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-154">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="a9ac0-155">Dopo la registrazione del middleware in `Startup.Configure` è possibile richiedere agli utenti di accedere da qualsiasi azione del controller.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-155">Once the middleware is registered in `Startup.Configure`, you can prompt users to sign in from any controller action.</span></span> <span data-ttu-id="a9ac0-156">Per fare ciò si crea un oggetto `AuthenticationProperties` che include il nome del provider di autenticazione e un URL di reindirizzamento.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-156">To do this, you create an `AuthenticationProperties` object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="a9ac0-157">È quindi possibile restituire una risposta Challenge che passa l'oggetto `AuthenticationProperties`.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-157">You then return a Challenge response that passes the `AuthenticationProperties` object.</span></span> <span data-ttu-id="a9ac0-158">Nel codice seguente viene illustrato un esempio.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-158">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="a9ac0-159">Il parametro redirectUrl include l'URL a cui il provider esterno deve reindirizzare l'utente dopo l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-159">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="a9ac0-160">L'URL deve rappresentare un'azione che connetterà l'utente in base alle informazioni di identità esterne, come nell'esempio semplificato seguente:</span><span class="sxs-lookup"><span data-stu-id="a9ac0-160">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

```csharp
// Sign in the user with this external login provider if the user
// already has a login.
var result = await _signInManager.ExternalLoginSignInAsync(info.LoginProvider, info.ProviderKey, isPersistent: false);

if (result.Succeeded)
{
    return RedirectToLocal(returnUrl);
}
else
{
    ApplicationUser newUser = new ApplicationUser
    {
        // The user object can be constructed with claims from the
        // external authentication provider, combined with information
        // supplied by the user after they have authenticated with
        // the external provider.
        UserName = info.Principal.FindFirstValue(ClaimTypes.Name),
        Email = info.Principal.FindFirstValue(ClaimTypes.Email)
    };
    var identityResult = await _userManager.CreateAsync(newUser);
    if (identityResult.Succeeded)
    {
        identityResult = await _userManager.AddLoginAsync(newUser, info);
        if (identityResult.Succeeded)
        {
            await _signInManager.SignInAsync(newUser, isPersistent: false);
        }
        return RedirectToLocal(returnUrl);
    }
}
```

<span data-ttu-id="a9ac0-161">Se quando si crea il progetto di applicazione Web ASP.NET Code in Visual Studio si sceglie l'opzione di autenticazione **Account utente individuali**, tutto il codice necessario per l'accesso con un provider esterno è già presente nel progetto, come illustrato nella figura 9-3.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-161">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 9-3.</span></span>

![Finestra di dialogo per la nuova applicazione Web ASP.NET Core, con il pulsante di modifica dell'autenticazione evidenziato.](./media/image3.png)

<span data-ttu-id="a9ac0-163">**Figura 9-3**.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-163">**Figure 9-3**.</span></span> <span data-ttu-id="a9ac0-164">Selezione di un'opzione per l'uso dell'autenticazione esterna quando si crea un progetto di applicazione Web</span><span class="sxs-lookup"><span data-stu-id="a9ac0-164">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="a9ac0-165">Oltre all'autenticazione esterna dei provider elencati in precedenza, sono disponibili pacchetti di terze parti che forniscono middleware per l'uso di molti altri provider di autenticazione esterni.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-165">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="a9ac0-166">Per un elenco, vedere il repository [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) in GitHub.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-166">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="a9ac0-167">È anche possibile creare middleware di autenticazione esterna personalizzato per risolvere esigenze particolari.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-167">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="a9ac0-168">Eseguire l'autenticazione con bearer token</span><span class="sxs-lookup"><span data-stu-id="a9ac0-168">Authenticate with bearer tokens</span></span>

<span data-ttu-id="a9ac0-169">L'autenticazione con ASP.NET Core Identity (o Identity più provider di autenticazione esterni) funziona bene per molti scenari di applicazioni Web in cui è appropriato archiviare le informazioni dell'utente in un cookie.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-169">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="a9ac0-170">In altri scenari, tuttavia, i cookie non sono un mezzo naturale per salvare in modo permanente e trasmettere i dati.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-170">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="a9ac0-171">Ad esempio, in un'API Web di ASP.NET Core che espone endpoint RESTful a cui potrebbero accedere applicazioni a pagina singola, client nativi o anche da altre API Web, in genere è consigliabile usare l'autenticazione con bearer token.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-171">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="a9ac0-172">Questi tipi di applicazioni non usano i cookie, ma possono recuperare facilmente un bearer token e includerlo nell'intestazione di autorizzazione delle richieste successive.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-172">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="a9ac0-173">Per consentire l'autenticazione del token, ASP.NET Core supporta diverse opzioni di utilizzo di [OAuth 2.0](https://oauth.net/2/) e [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="a9ac0-173">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="a9ac0-174">Eseguire l'autenticazione con un provider di identità OpenID Connect o OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="a9ac0-174">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="a9ac0-175">Se le informazioni dell'utente sono archiviate in Azure Active Directory o in un'altra soluzione di identità che supporta OpenID Connect o OAuth 2.0, è possibile usare il pacchetto **Microsoft.AspNetCore.Authentication.OpenIdConnect** per eseguire l'autenticazione tramite il flusso di lavoro di OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-175">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="a9ac0-176">Ad esempio per eseguire l'autenticazione con il microservizio Identity.Api in eshopOnContainers, un'applicazione Web ASP.NET Core può usare il middleware del pacchetto, come illustrato nell'esempio semplificato seguente in `Startup.cs`:</span><span class="sxs-lookup"><span data-stu-id="a9ac0-176">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = OpenIdConnectDefaults.AuthenticationScheme;
    })
    .AddCookie()
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl;
        options.SignedOutRedirectUri = callBackUrl;
        options.ClientSecret = "secret";
        options.SaveTokens = true;
        options.GetClaimsFromUserInfoEndpoint = true;
        options.RequireHttpsMetadata = false;
        options.Scope.Add("openid");
        options.Scope.Add("profile");
        options.Scope.Add("orders");
        options.Scope.Add("basket");
        options.Scope.Add("marketing");
        options.Scope.Add("locations");
        options.Scope.Add("webshoppingagg");
        options.Scope.Add("orders.signalrhub");
    });
}
```

<span data-ttu-id="a9ac0-177">Si noti che quando si usa questo flusso di lavoro il middleware di ASP.NET Core Identity non è necessario, perché tutte le operazioni di archiviazione e autenticazione delle informazioni degli utenti vengono gestite dal servizio di gestione delle identità.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-177">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="a9ac0-178">Rilasciare token di sicurezza da un servizio ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a9ac0-178">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="a9ac0-179">Se si vuole rilasciare token di sicurezza per gli utenti locali di ASP.NET Core Identity anziché usare un provider di identità esterna, è possibile avvalersi di alcune utili librerie di terze parti.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-179">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="a9ac0-180">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) e [OpenIddict](https://github.com/openiddict/openiddict-core) sono provider OpenID Connect che si integrano facilmente con ASP.NET Core Identity per il rilascio di token di sicurezza da un servizio ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-180">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="a9ac0-181">La [documentazione di IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) contiene istruzioni dettagliate per l'uso della libreria.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-181">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="a9ac0-182">Di seguito sono indicate le operazioni di base per usare IdentityServer4 per il rilascio di token.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-182">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="a9ac0-183">Chiamare app.UseIdentityServer nel metodo Startup.Configure per aggiungere IdentityServer4 alla pipeline di elaborazione delle richieste HTTP dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-183">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="a9ac0-184">In questo modo, la libreria fornisce richieste agli endpoint OpenID Connect e OAuth2 come /connect/token.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-184">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="a9ac0-185">IdentityServer4 viene configurato in Startup.ConfigureServices tramite una chiamata a services.AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-185">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="a9ac0-186">Il server delle identità viene configurato impostando i dati seguenti:</span><span class="sxs-lookup"><span data-stu-id="a9ac0-186">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="a9ac0-187">Le [credenziali](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) da usare per la firma.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-187">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="a9ac0-188">Le [risorse di identità e API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) a cui gli utenti potrebbero richiedere l'accesso:</span><span class="sxs-lookup"><span data-stu-id="a9ac0-188">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="a9ac0-189">Le risorse API rappresentano dati protetti o funzionalità a cui l'utente può accedere con un token di accesso.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-189">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="a9ac0-190">Un esempio di risorsa API è un'API o un set di API Web che richiede l'autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-190">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="a9ac0-191">Le risorse di identità rappresentano informazioni (attestazioni) che vengono fornite a un client per identificare un utente.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-191">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="a9ac0-192">Le attestazioni possono includere il nome utente, l'indirizzo di posta elettronica e così via.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-192">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="a9ac0-193">I [client](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) che si connetteranno per richiedere i token.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-193">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="a9ac0-194">Il meccanismo di archiviazione delle informazioni degli utenti, ad esempio [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) o un sistema alternativo.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-194">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="a9ac0-195">Quando si specificano i client e le risorse da usare con IdentityServer4, è possibile passare una raccolta <xref:System.Collections.Generic.IEnumerable%601> del tipo appropriato ai metodi che accettano archivi di client o risorse in memoria.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-195">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="a9ac0-196">In alternativa, per scenari più complessi, è possibile fornire tipi di provider di client o risorse tramite l'inserimento delle dipendenze.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-196">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="a9ac0-197">Un esempio di configurazione per IdentityServer4 che usa le risorse e i client in memoria forniti da un tipo IClientStore personalizzato è simile al codice seguente:</span><span class="sxs-lookup"><span data-stu-id="a9ac0-197">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a><span data-ttu-id="a9ac0-198">Usare i token di sicurezza</span><span class="sxs-lookup"><span data-stu-id="a9ac0-198">Consume security tokens</span></span>

<span data-ttu-id="a9ac0-199">L'autenticazione con un endpoint OpenID Connect o l'emissione di token di sicurezza propri coprono alcuni scenari.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-199">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="a9ac0-200">Ma occorre considerare anche i casi in cui un servizio necessita semplicemente di limitare l'accesso agli utenti che hanno token di sicurezza validi forniti da un servizio diverso.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-200">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="a9ac0-201">Per questo scenario è disponibile il middleware di autenticazione che gestisce i token JWT nel pacchetto **Microsoft.AspNetCore.Authentication.JwtBearer**.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-201">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="a9ac0-202">JWT è l'acronimo di "[JSON Web Token (token Web JSON)](https://tools.ietf.org/html/rfc7519)" ed è un formato di token di sicurezza comune, definito da RFC 7519, per la comunicazione di attestazioni di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-202">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="a9ac0-203">Un esempio semplificato dell'uso del middleware con questi token può essere simile a questo frammento di codice, tratto dal microservizio Ordering.Api di eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-203">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

<span data-ttu-id="a9ac0-204">I parametri in questo caso sono:</span><span class="sxs-lookup"><span data-stu-id="a9ac0-204">The parameters in this usage are:</span></span>

- <span data-ttu-id="a9ac0-205">`Audience` rappresenta il destinatario del token in ingresso o la risorsa a cui il token concede l'accesso.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-205">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="a9ac0-206">Se il valore specificato in questo parametro non corrisponde al parametro nel token, il token verrà rifiutato.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-206">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="a9ac0-207">`Authority` è l'indirizzo del server di autenticazione che emette i token.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-207">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="a9ac0-208">Il middleware di autenticazione del bearer token JWT usa questo URI per ottenere la chiave pubblica che può essere usata per convalidare la firma del token.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-208">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="a9ac0-209">Il middleware verifica anche che il parametro `iss` nel token corrisponda a questo URI.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-209">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="a9ac0-210">Un altro parametro, `RequireHttpsMetadata`, è utile per i test. Impostando questo parametro su false è possibile testare l'applicazione in ambienti in cui non sono presenti certificati.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-210">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="a9ac0-211">Nelle distribuzioni effettive, i bearer token JWT devono sempre essere passati solo su HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-211">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="a9ac0-212">Con questo middleware, i token JWT vengono estratti automaticamente dalle intestazioni di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-212">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="a9ac0-213">Vengono quindi deserializzati, convalidati (tramite i valori nei parametri `Audience` e `Authority`) e archiviati come informazioni utente alle quali fare riferimento in seguito con azioni MVC o filtri di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-213">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="a9ac0-214">Il middleware di autenticazione con bearer token JWT può supportare anche scenari più avanzati, ad esempio l'uso di un certificato locale per convalidare un token se l'autorità non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-214">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="a9ac0-215">Per questo scenario è possibile specificare un oggetto `TokenValidationParameters` nell'oggetto `JwtBearerOptions`.</span><span class="sxs-lookup"><span data-stu-id="a9ac0-215">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a9ac0-216">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="a9ac0-216">Additional resources</span></span>

- <span data-ttu-id="a9ac0-217">**Condivisione dei cookie tra applicazioni** </span><span class="sxs-lookup"><span data-stu-id="a9ac0-217">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="a9ac0-218">**Introduzione all'identità** </span><span class="sxs-lookup"><span data-stu-id="a9ac0-218">**Introduction to Identity** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="a9ac0-219">**Rick Anderson. Autenticazione a due fattori con SMS** </span><span class="sxs-lookup"><span data-stu-id="a9ac0-219">**Rick Anderson. Two-factor authentication with SMS** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="a9ac0-220">**Abilitazione dell'autenticazione con Facebook, Google e altri provider esterni** </span><span class="sxs-lookup"><span data-stu-id="a9ac0-220">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="a9ac0-221">**Michell Anicas. An Introduction to OAuth 2 (Introduzione a OAuth 2)**  </span><span class="sxs-lookup"><span data-stu-id="a9ac0-221">**Michell Anicas. An Introduction to OAuth 2** </span></span>\
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="a9ac0-222">**AspNet.Security.OAuth.Providers** (repository GitHub per i provider OAuth ASP.NET) </span><span class="sxs-lookup"><span data-stu-id="a9ac0-222">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="a9ac0-223">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app (Integrazione di Azure AD in un'app Web ASP.NET Core)**  </span><span class="sxs-lookup"><span data-stu-id="a9ac0-223">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app** </span></span>\
  <https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/>

- <span data-ttu-id="a9ac0-224">**IdentityServer4. Documentazione ufficiale** </span><span class="sxs-lookup"><span data-stu-id="a9ac0-224">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="a9ac0-225">[Precedente](../implement-resilient-applications/monitor-app-health.md)
>[Successivo](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="a9ac0-225">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>