---
title: Associare il controllo a un oggetto Factory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 2b4d9aca3345a0cb1e7e995f66a8982dee983ca8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745086"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="25d0a-102">Procedura: associare un controllo Windows Form a un oggetto Factory</span><span class="sxs-lookup"><span data-stu-id="25d0a-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="25d0a-103">Quando si compilano controlli che interagiscono con i dati, è a volte necessario associare un controllo a un oggetto o metodo che genera altri oggetti.</span><span class="sxs-lookup"><span data-stu-id="25d0a-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="25d0a-104">Tale oggetto o metodo è definito factory.</span><span class="sxs-lookup"><span data-stu-id="25d0a-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="25d0a-105">L'origine dati, ad esempio, potrebbe essere il valore restituito da una chiamata al metodo anziché un oggetto in memoria o un tipo.</span><span class="sxs-lookup"><span data-stu-id="25d0a-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="25d0a-106">È possibile associare un controllo a tale tipo di origine dati purché l'origine restituisca una raccolta.</span><span class="sxs-lookup"><span data-stu-id="25d0a-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="25d0a-107">È possibile associare facilmente un controllo a un oggetto factory usando il controllo <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="25d0a-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25d0a-108">Esempio</span><span class="sxs-lookup"><span data-stu-id="25d0a-108">Example</span></span>  
 <span data-ttu-id="25d0a-109">Nell'esempio seguente viene dimostrato come associare un controllo <xref:System.Windows.Forms.DataGridView> a un metodo factory mediante un controllo <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="25d0a-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="25d0a-110">Il metodo factory, denominato `GetOrdersByCustomerId`, restituisce tutti gli ordini di un dato cliente nel database Northwind.</span><span class="sxs-lookup"><span data-stu-id="25d0a-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="25d0a-111">Compilazione del codice</span><span class="sxs-lookup"><span data-stu-id="25d0a-111">Compiling the Code</span></span>  
 <span data-ttu-id="25d0a-112">L'esempio presenta i requisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="25d0a-112">This example requires:</span></span>  
  
- <span data-ttu-id="25d0a-113">Riferimenti agli assembly System, System.Data, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="25d0a-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d0a-114">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25d0a-114">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="25d0a-115">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="25d0a-115">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="25d0a-116">Procedura: associare un controllo Windows Form a un tipo</span><span class="sxs-lookup"><span data-stu-id="25d0a-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
