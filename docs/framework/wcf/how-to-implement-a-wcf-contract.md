---
title: 'Esercitazione: Implementare un contratto di servizio di Windows Communication FoundationTutorial: Implement a Windows Communication Foundation service contract'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: debdeeac7064f5bae21622b2d9de84a4d8a0e66f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184064"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="dc311-102">Esercitazione: Implementare un contratto di servizio di Windows Communication FoundationTutorial: Implement a Windows Communication Foundation service contract</span><span class="sxs-lookup"><span data-stu-id="dc311-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="dc311-103">Questa esercitazione descrive la seconda delle cinque attività necessarie per creare un'applicazione Windows Communication Foundation (WCF) di base.</span><span class="sxs-lookup"><span data-stu-id="dc311-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="dc311-104">Per una panoramica delle esercitazioni, vedere [Esercitazione: Introduzione alle applicazioni Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="dc311-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="dc311-105">Il passaggio successivo per la creazione di un'applicazione WCF consiste nell'aggiungere il codice per implementare l'interfaccia del servizio WCF creata nel passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="dc311-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="dc311-106">In questo passaggio viene `CalculatorService` creata una classe `ICalculator` denominata che implementa l'interfaccia definita dall'utente.</span><span class="sxs-lookup"><span data-stu-id="dc311-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="dc311-107">Ogni metodo nel codice seguente chiama un'operazione della calcolatrice e scrive testo nella console per testarlo.</span><span class="sxs-lookup"><span data-stu-id="dc311-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="dc311-108">In questa esercitazione verranno illustrate le procedure per:</span><span class="sxs-lookup"><span data-stu-id="dc311-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="dc311-109">Aggiungere il codice per implementare il contratto di servizio WCF.</span><span class="sxs-lookup"><span data-stu-id="dc311-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="dc311-110">Compilare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="dc311-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="dc311-111">Aggiungere codice per implementare il contratto di servizio WCFAdd code to implement the WCF service contract</span><span class="sxs-lookup"><span data-stu-id="dc311-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="dc311-112">In **GettingStartedLib**aprire il file **Service1.cs** o **Service1.vb** e sostituirne il codice con il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="dc311-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

## <a name="edit-appconfig"></a><span data-ttu-id="dc311-113">Modifica App.config</span><span class="sxs-lookup"><span data-stu-id="dc311-113">Edit App.config</span></span>

<span data-ttu-id="dc311-114">Modificare **App.config** in **GettingStartedLib** per riflettere le modifiche apportate al codice.</span><span class="sxs-lookup"><span data-stu-id="dc311-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="dc311-115">Per i progetti di Visual C:</span><span class="sxs-lookup"><span data-stu-id="dc311-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="dc311-116">Cambia linea 14 in`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="dc311-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="dc311-117">Cambia linea 17 in`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="dc311-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="dc311-118">Cambia linea 22 in`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="dc311-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="dc311-119">Per i progetti di Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="dc311-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="dc311-120">Cambia linea 14 in`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="dc311-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="dc311-121">Cambia linea 17 in`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="dc311-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="dc311-122">Cambia linea 22 in`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="dc311-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="dc311-123">Compilare il codice</span><span class="sxs-lookup"><span data-stu-id="dc311-123">Compile the code</span></span>

<span data-ttu-id="dc311-124">Compilare la soluzione per verificare che non siano presenti errori di compilazione.</span><span class="sxs-lookup"><span data-stu-id="dc311-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="dc311-125">Se si utilizza Visual Studio, scegliere **Compila soluzione** dal menu **Compila** (o premere **CTRL**+**MAIUSC**+**B**).</span><span class="sxs-lookup"><span data-stu-id="dc311-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc311-126">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="dc311-126">Next steps</span></span>

<span data-ttu-id="dc311-127">In questa esercitazione sono state illustrate le procedure per:</span><span class="sxs-lookup"><span data-stu-id="dc311-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="dc311-128">Aggiungere il codice per implementare il contratto di servizio WCF.</span><span class="sxs-lookup"><span data-stu-id="dc311-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="dc311-129">Compilare la soluzione.</span><span class="sxs-lookup"><span data-stu-id="dc311-129">Build the solution.</span></span>

<span data-ttu-id="dc311-130">Passare all'esercitazione successiva per informazioni su come eseguire il servizio WCF.</span><span class="sxs-lookup"><span data-stu-id="dc311-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc311-131">Esercitazione: Ospitare ed eseguire un servizio WCF di baseTutorial: Host and run a basic WCF service</span><span class="sxs-lookup"><span data-stu-id="dc311-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
