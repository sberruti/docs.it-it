---
title: Creare un'app elenco di corrispondenze di gioco con Infer.NET e la programmazione probabilistica
description: Informazioni su come usare la programmazione probabilistica con Infer.NET per creare un'app elenco di corrispondenze di gioco basata su una versione semplificata di TrueSkill.
ms.date: 10/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: ceeb0f43e03c7ce93f105498f44bf243eec86bbf
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152468"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="1090d-103">Creare un'app elenco di corrispondenze di gioco con Infer.NET e la programmazione probabilistica</span><span class="sxs-lookup"><span data-stu-id="1090d-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

<span data-ttu-id="1090d-104">Questa guida pratica descrive la programmazione probabilistica tramite Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="1090d-104">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="1090d-105">La programmazione probabilistica è un approccio di apprendimento automatico in cui modelli personalizzati vengono espressi come programmi.</span><span class="sxs-lookup"><span data-stu-id="1090d-105">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="1090d-106">Permette di integrare informazioni specifiche di un dominio nei modelli e rendere il sistema di apprendimento automatico maggiormente interpretabile.</span><span class="sxs-lookup"><span data-stu-id="1090d-106">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="1090d-107">Supporta anche l'inferenza online, ovvero il processo di apprendere man mano che arrivano nuovi dati.</span><span class="sxs-lookup"><span data-stu-id="1090d-107">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="1090d-108">Infer.NET viene usato in diversi prodotti Microsoft, tra cui Azure, Xbox e Bing.</span><span class="sxs-lookup"><span data-stu-id="1090d-108">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="1090d-109">Che cos'è la programmazione probabilistica?</span><span class="sxs-lookup"><span data-stu-id="1090d-109">What is probabilistic programming?</span></span>

<span data-ttu-id="1090d-110">La programmazione probabilistica permette di creare modelli statistici di processi reali.</span><span class="sxs-lookup"><span data-stu-id="1090d-110">Probabilistic programming allows us to create statistical models of real-world processes.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="1090d-111">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="1090d-111">Prerequisites</span></span>

- <span data-ttu-id="1090d-112">Configurazione di un ambiente di sviluppo locale</span><span class="sxs-lookup"><span data-stu-id="1090d-112">Local development environment setup</span></span>

  <span data-ttu-id="1090d-113">Questa guida pratica presuppone la presenza di un computer che possa essere usato per lo sviluppo.</span><span class="sxs-lookup"><span data-stu-id="1090d-113">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="1090d-114">L'esercitazione su .NET [Get started with .NET in 10 minutes](https://www.microsoft.com/net/core) (Iniziare a usare .NET in 10 minuti) contiene istruzioni per la configurazione dell'ambiente di sviluppo locale in Mac, PC o Linux.</span><span class="sxs-lookup"><span data-stu-id="1090d-114">The .NET [Get Started in 10 minutes](https://www.microsoft.com/net/core) tutorial has instructions for setting up your local development environment on Mac, PC, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="1090d-115">Creare l'app</span><span class="sxs-lookup"><span data-stu-id="1090d-115">Create your app</span></span>

1. <span data-ttu-id="1090d-116">Aprire un nuovo prompt dei comandi ed eseguire i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="1090d-116">Open a new command prompt and run the following commands:</span></span>

```console
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="1090d-117">Il comando `dotnet` crea un'applicazione `new` di tipo `console`.</span><span class="sxs-lookup"><span data-stu-id="1090d-117">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="1090d-118">Il parametro `-o` crea una directory denominata `myApp` in cui viene archiviata l'app, popolata con i file necessari.</span><span class="sxs-lookup"><span data-stu-id="1090d-118">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="1090d-119">Il comando `cd myApp` permette di passare alla directory dell'app appena creata.</span><span class="sxs-lookup"><span data-stu-id="1090d-119">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="1090d-120">Installare il pacchetto Infer.NET</span><span class="sxs-lookup"><span data-stu-id="1090d-120">Install Infer.NET package</span></span>

<span data-ttu-id="1090d-121">Per usare Infer.NET, è necessario installare il pacchetto `Microsoft.ML.Probabilistic.Compiler`.</span><span class="sxs-lookup"><span data-stu-id="1090d-121">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="1090d-122">Al prompt dei comandi eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="1090d-122">In your command prompt, run the following command:</span></span>

```console
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="1090d-123">Progettare il modello</span><span class="sxs-lookup"><span data-stu-id="1090d-123">Design your model</span></span>

<span data-ttu-id="1090d-124">L'esempio usa partite di ping pong o calcio giocate in ufficio.</span><span class="sxs-lookup"><span data-stu-id="1090d-124">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="1090d-125">Sono disponibili i partecipanti e il risultato di ogni partita.</span><span class="sxs-lookup"><span data-stu-id="1090d-125">We have the participants and outcome of each match.</span></span>  <span data-ttu-id="1090d-126">Si vuole dedurre le abilità del giocatore da questi dati.</span><span class="sxs-lookup"><span data-stu-id="1090d-126">We want to infer the player's skills from this data.</span></span> <span data-ttu-id="1090d-127">Si presuppone che ogni giocatore abbia un'abilità latente normalmente distribuita e che le sue prestazioni in una partita specifica siano una versione accentuata di questa abilità.</span><span class="sxs-lookup"><span data-stu-id="1090d-127">We’ll assume that each player has a normally distributed latent skill and their performance in a given match is a noisy version of this skill.</span></span> <span data-ttu-id="1090d-128">I dati vincolano le prestazioni del vincitore come migliori delle prestazioni del giocatore sconfitto.</span><span class="sxs-lookup"><span data-stu-id="1090d-128">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="1090d-129">Si tratta di una versione semplificata del celebre modello [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/), che supporta anche squadre, pareggi e altre estensioni.</span><span class="sxs-lookup"><span data-stu-id="1090d-129">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="1090d-130">Una [versione avanzata](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) di questo modello viene usata per il matchmaking nei vendutissimi titoli Halo e Gears of War.</span><span class="sxs-lookup"><span data-stu-id="1090d-130">An [advanced version](https://www.microsoft.com/en-us/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="1090d-131">È necessario elencare le abilità del giocatore dedotte, insieme alla rispettiva varianza, ovvero la misura di incertezza riguardo alle abilità.</span><span class="sxs-lookup"><span data-stu-id="1090d-131">We need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="1090d-132">*Dati di esempio dei risultati di gioco*</span><span class="sxs-lookup"><span data-stu-id="1090d-132">*Game result sample data*</span></span>

<span data-ttu-id="1090d-133">Partita</span><span class="sxs-lookup"><span data-stu-id="1090d-133">Game</span></span> |<span data-ttu-id="1090d-134">Vincitori</span><span class="sxs-lookup"><span data-stu-id="1090d-134">Winner</span></span> | <span data-ttu-id="1090d-135">Sconfitti</span><span class="sxs-lookup"><span data-stu-id="1090d-135">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="1090d-136">1</span><span class="sxs-lookup"><span data-stu-id="1090d-136">1</span></span> | <span data-ttu-id="1090d-137">Giocatore 0</span><span class="sxs-lookup"><span data-stu-id="1090d-137">Player 0</span></span> | <span data-ttu-id="1090d-138">Giocatore 1</span><span class="sxs-lookup"><span data-stu-id="1090d-138">Player 1</span></span>
 <span data-ttu-id="1090d-139">2</span><span class="sxs-lookup"><span data-stu-id="1090d-139">2</span></span> | <span data-ttu-id="1090d-140">Giocatore 0</span><span class="sxs-lookup"><span data-stu-id="1090d-140">Player 0</span></span> | <span data-ttu-id="1090d-141">Giocatore 3</span><span class="sxs-lookup"><span data-stu-id="1090d-141">Player 3</span></span>
 <span data-ttu-id="1090d-142">3</span><span class="sxs-lookup"><span data-stu-id="1090d-142">3</span></span> | <span data-ttu-id="1090d-143">Giocatore 0</span><span class="sxs-lookup"><span data-stu-id="1090d-143">Player 0</span></span> | <span data-ttu-id="1090d-144">Giocatore 4</span><span class="sxs-lookup"><span data-stu-id="1090d-144">Player 4</span></span>
 <span data-ttu-id="1090d-145">4</span><span class="sxs-lookup"><span data-stu-id="1090d-145">4</span></span> | <span data-ttu-id="1090d-146">Giocatore 1</span><span class="sxs-lookup"><span data-stu-id="1090d-146">Player 1</span></span> | <span data-ttu-id="1090d-147">Giocatore 2</span><span class="sxs-lookup"><span data-stu-id="1090d-147">Player 2</span></span>
 <span data-ttu-id="1090d-148">5</span><span class="sxs-lookup"><span data-stu-id="1090d-148">5</span></span> | <span data-ttu-id="1090d-149">Giocatore 3</span><span class="sxs-lookup"><span data-stu-id="1090d-149">Player 3</span></span> | <span data-ttu-id="1090d-150">Giocatore 1</span><span class="sxs-lookup"><span data-stu-id="1090d-150">Player 1</span></span>
 <span data-ttu-id="1090d-151">6</span><span class="sxs-lookup"><span data-stu-id="1090d-151">6</span></span> | <span data-ttu-id="1090d-152">Giocatore 4</span><span class="sxs-lookup"><span data-stu-id="1090d-152">Player 4</span></span> | <span data-ttu-id="1090d-153">Giocatore 2</span><span class="sxs-lookup"><span data-stu-id="1090d-153">Player 2</span></span>

<span data-ttu-id="1090d-154">Osservando più attentamente i dati di esempio, si noterà che i giocatori 3 e 4 hanno entrambi una vittoria e una sconfitta.</span><span class="sxs-lookup"><span data-stu-id="1090d-154">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="1090d-155">Si osserveranno ora le classificazioni usando la programmazione probabilistica.</span><span class="sxs-lookup"><span data-stu-id="1090d-155">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="1090d-156">Si noti anche la presenza di un giocatore 0, perché gli elenchi di corrispondenze sono in base zero per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="1090d-156">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="1090d-157">Scrivere codice</span><span class="sxs-lookup"><span data-stu-id="1090d-157">Write some code</span></span>

<span data-ttu-id="1090d-158">Dopo aver progettato il modello, è possibile esprimerlo come programma probabilistico tramite l'API di modellazione Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="1090d-158">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="1090d-159">Aprire `Program.cs` nell'editor di testo preferito e sostituire tutto il contenuto con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="1090d-159">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

```csharp
namespace myApp

{
    using System;
    using System.Linq;
    using Microsoft.ML.Probabilistic;
    using Microsoft.ML.Probabilistic.Distributions;
    using Microsoft.ML.Probabilistic.Models;

    class Program
    {

        static void Main(string[] args)
        {
            // The winner and loser in each of 6 samples games
            var winnerData = new[] { 0, 0, 0, 1, 3, 4 };
            var loserData = new[] { 1, 3, 4, 2, 1, 2 };

            // Define the statistical model as a probabilistic program 
            var game = new Range(winnerData.Length);
            var player = new Range(winnerData.Concat(loserData).Max() + 1);
            var playerSkills = Variable.Array<double>(player);
            playerSkills[player] = Variable.GaussianFromMeanAndVariance(6, 9).ForEach(player);

            var winners = Variable.Array<int>(game);
            var losers = Variable.Array<int>(game);

            using (Variable.ForEach(game))
            {
                // The player performance is a noisy version of their skill
                var winnerPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[winners[game]], 1.0);
                var loserPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[losers[game]], 1.0);

                // The winner performed better in this game
                Variable.ConstrainTrue(winnerPerformance > loserPerformance);
            }

            // Attach the data to the model
            winners.ObservedValue = winnerData;
            losers.ObservedValue = loserData;

            // Run inference
            var inferenceEngine = new InferenceEngine();
            var inferredSkills = inferenceEngine.Infer<Gaussian[]>(playerSkills);

            // The inferred skills are uncertain, which is captured in their variance
            var orderedPlayerSkills = inferredSkills
               .Select((s, i) => new { Player = i, Skill = s })
               .OrderByDescending(ps => ps.Skill.GetMean());

            foreach (var playerSkill in orderedPlayerSkills)
            {
                Console.WriteLine($"Player {playerSkill.Player} skill: {playerSkill.Skill}");
            }
        }
    }
}
```

## <a name="run-your-app"></a><span data-ttu-id="1090d-160">Eseguire l'app</span><span class="sxs-lookup"><span data-stu-id="1090d-160">Run your app</span></span>

<span data-ttu-id="1090d-161">Al prompt dei comandi eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="1090d-161">In your command prompt, run the following command:</span></span>

```console
dotnet run
```

## <a name="results"></a><span data-ttu-id="1090d-162">Risultati</span><span class="sxs-lookup"><span data-stu-id="1090d-162">Results</span></span>

<span data-ttu-id="1090d-163">I risultati saranno simili ai seguenti:</span><span class="sxs-lookup"><span data-stu-id="1090d-163">Your results should be similar to the following:</span></span>

```
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

<span data-ttu-id="1090d-164">Nei risultati si noti che in base al modello il giocatore 3 è in posizione leggermente superiore rispetto al giocatore 4.</span><span class="sxs-lookup"><span data-stu-id="1090d-164">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="1090d-165">Il motivo è che la vittoria del giocatore 3 sul giocatore 1 è più significativa rispetto alla vittoria del giocatore 4 sul giocatore 2: notare infatti che il giocatore 1 batte il giocatore 2.</span><span class="sxs-lookup"><span data-stu-id="1090d-165">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="1090d-166">Il giocatore 0 è il campione assoluto.</span><span class="sxs-lookup"><span data-stu-id="1090d-166">Player 0 is the overall champ!</span></span>  

## <a name="keep-learning"></a><span data-ttu-id="1090d-167">Per continuare ad apprendere</span><span class="sxs-lookup"><span data-stu-id="1090d-167">Keep learning</span></span>

<span data-ttu-id="1090d-168">La progettazione di modelli statistici è una competenza di per sé.</span><span class="sxs-lookup"><span data-stu-id="1090d-168">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="1090d-169">Il team di Microsoft Research Cambridge ha redatto un [libro online gratuito](http://mbmlbook.com/), che offre una pratica introduzione all'articolo.</span><span class="sxs-lookup"><span data-stu-id="1090d-169">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="1090d-170">Il capitolo 3 di questo libro descrive più dettagliatamente il modello TrueSkill.</span><span class="sxs-lookup"><span data-stu-id="1090d-170">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="1090d-171">Dopo aver ideato un modello, è possibile trasformarlo in codice usando la [vasta documentazione](https://dotnet.github.io/infer/) nel sito Web Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="1090d-171">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1090d-172">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="1090d-172">Next steps</span></span>

<span data-ttu-id="1090d-173">Visitare il repository GitHub per Infer.NET per continuare ad acquisire familiarità e trovare altri esempi.</span><span class="sxs-lookup"><span data-stu-id="1090d-173">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="1090d-174">Repository GitHub dotnet/infer</span><span class="sxs-lookup"><span data-stu-id="1090d-174">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)