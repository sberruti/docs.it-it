---
ms.openlocfilehash: 10811a90887624a731c58d557e1dd196ae2c9207
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "76508551"
---
### <a name="removed-controls"></a><span data-ttu-id="60fcf-101">Controlli rimossi</span><span class="sxs-lookup"><span data-stu-id="60fcf-101">Removed controls</span></span>

<span data-ttu-id="60fcf-102">A partire da .NET Core 3.1, alcuni controlli Windows Form non sono più disponibili.</span><span class="sxs-lookup"><span data-stu-id="60fcf-102">Starting in .NET Core 3.1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="60fcf-103">Descrizione modifica:</span><span class="sxs-lookup"><span data-stu-id="60fcf-103">Change description</span></span>

<span data-ttu-id="60fcf-104">A partire da .NET Core 3.1, vari controlli Windows Form non sono più disponibili.</span><span class="sxs-lookup"><span data-stu-id="60fcf-104">Starting with .NET Core 3.1, various Windows Forms controls are no longer available.</span></span> <span data-ttu-id="60fcf-105">I controlli di sostituzione con una migliore progettazione e supporto sono stati introdotti in .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="60fcf-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="60fcf-106">I controlli deprecati sono stati rimossi in precedenza dalle caselle degli strumenti della finestra di progettazione, ma erano ancora disponibili per l'utilizzo.</span><span class="sxs-lookup"><span data-stu-id="60fcf-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span>

<span data-ttu-id="60fcf-107">I seguenti tipi non sono più disponibili:</span><span class="sxs-lookup"><span data-stu-id="60fcf-107">The following types are no longer available:</span></span>

- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.Menu.MenuItemCollection>
- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.ToolBar>
- <xref:System.Windows.Forms.ToolBarAppearance>
- <xref:System.Windows.Forms.ToolBarButton>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs>
- <xref:System.Windows.Forms.ToolBarButtonStyle>
- <xref:System.Windows.Forms.ToolBarTextAlign>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.DataGridBoolColumn>
- <xref:System.Windows.Forms.DataGridCell>
- <xref:System.Windows.Forms.DataGridColumnStyle>
- <xref:System.Windows.Forms.DataGridLineStyle>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter>
- <xref:System.Windows.Forms.DataGridTableStyle>
- <xref:System.Windows.Forms.DataGridTextBox>
- <xref:System.Windows.Forms.DataGridTextBoxColumn>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.GridTablesFactory>
- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.IDataGridEditingService>
- <xref:System.Windows.Forms.DataGrid.HitTestType>
- <xref:System.Windows.Forms.Design.IMenuEditorService>

#### <a name="version-introduced"></a><span data-ttu-id="60fcf-108">Versione introdotta</span><span class="sxs-lookup"><span data-stu-id="60fcf-108">Version introduced</span></span>

<span data-ttu-id="60fcf-109">3.1</span><span class="sxs-lookup"><span data-stu-id="60fcf-109">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="60fcf-110">Azione consigliata</span><span class="sxs-lookup"><span data-stu-id="60fcf-110">Recommended action</span></span>

<span data-ttu-id="60fcf-111">Ogni controllo rimosso ha un controllo di sostituzione consigliato.</span><span class="sxs-lookup"><span data-stu-id="60fcf-111">Each removed control has a recommended replacement control.</span></span> <span data-ttu-id="60fcf-112">Fare riferimento alla tabella seguente:</span><span class="sxs-lookup"><span data-stu-id="60fcf-112">Refer to the following table:</span></span>

| <span data-ttu-id="60fcf-113">Controllo rimosso (API)</span><span class="sxs-lookup"><span data-stu-id="60fcf-113">Removed control (API)</span></span> | <span data-ttu-id="60fcf-114">Sostituzione consigliata</span><span class="sxs-lookup"><span data-stu-id="60fcf-114">Recommended replacement</span></span> | <span data-ttu-id="60fcf-115">API associate rimosse</span><span class="sxs-lookup"><span data-stu-id="60fcf-115">Associated APIs that are removed</span></span> |
|-|-|-|
| <span data-ttu-id="60fcf-116">DataGrid</span><span class="sxs-lookup"><span data-stu-id="60fcf-116">DataGrid</span></span> | <span data-ttu-id="60fcf-117">DataGridView</span><span class="sxs-lookup"><span data-stu-id="60fcf-117">DataGridView</span></span> | <span data-ttu-id="60fcf-118">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, DataGridTableStyle, DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span><span class="sxs-lookup"><span data-stu-id="60fcf-118">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, DataGridTableStyle, DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span></span> |
| <span data-ttu-id="60fcf-119">ToolBar</span><span class="sxs-lookup"><span data-stu-id="60fcf-119">ToolBar</span></span> | <span data-ttu-id="60fcf-120">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="60fcf-120">ToolStrip</span></span> | <span data-ttu-id="60fcf-121">ToolBarAspetto</span><span class="sxs-lookup"><span data-stu-id="60fcf-121">ToolBarAppearance</span></span> |
| <span data-ttu-id="60fcf-122">Toolbarbutton</span><span class="sxs-lookup"><span data-stu-id="60fcf-122">ToolBarButton</span></span> | <span data-ttu-id="60fcf-123">Toolstripbutton</span><span class="sxs-lookup"><span data-stu-id="60fcf-123">ToolStripButton</span></span> | <span data-ttu-id="60fcf-124">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButtonStyle, ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="60fcf-124">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButtonStyle, ToolBarTextAlign</span></span>|
| <span data-ttu-id="60fcf-125">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="60fcf-125">ContextMenu</span></span> | <span data-ttu-id="60fcf-126">ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="60fcf-126">ContextMenuStrip</span></span> | |
| <span data-ttu-id="60fcf-127">Menu</span><span class="sxs-lookup"><span data-stu-id="60fcf-127">Menu</span></span> | <span data-ttu-id="60fcf-128">ToolStripDropDown, ToolStripDropDownMenu</span><span class="sxs-lookup"><span data-stu-id="60fcf-128">ToolStripDropDown, ToolStripDropDownMenu</span></span> | <span data-ttu-id="60fcf-129">Menuitemcollection</span><span class="sxs-lookup"><span data-stu-id="60fcf-129">MenuItemCollection</span></span> |
| <span data-ttu-id="60fcf-130">MainMenu</span><span class="sxs-lookup"><span data-stu-id="60fcf-130">MainMenu</span></span> | <span data-ttu-id="60fcf-131">MenuStrip</span><span class="sxs-lookup"><span data-stu-id="60fcf-131">MenuStrip</span></span> | |
| <span data-ttu-id="60fcf-132">MenuItem</span><span class="sxs-lookup"><span data-stu-id="60fcf-132">MenuItem</span></span> | <span data-ttu-id="60fcf-133">ToolStripMenuItem</span><span class="sxs-lookup"><span data-stu-id="60fcf-133">ToolStripMenuItem</span></span> | |

#### <a name="category"></a><span data-ttu-id="60fcf-134">Category</span><span class="sxs-lookup"><span data-stu-id="60fcf-134">Category</span></span>

<span data-ttu-id="60fcf-135">Windows Form</span><span class="sxs-lookup"><span data-stu-id="60fcf-135">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="60fcf-136">API interessate</span><span class="sxs-lookup"><span data-stu-id="60fcf-136">Affected APIs</span></span>

- <xref:System.Windows.Forms.Menu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Menu.MenuItemCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MainMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ContextMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MenuItem?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarAppearance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarTextAlign?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridBoolColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridCell?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridColumnStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridLineStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTableStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBox?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBoxColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridColumnStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTablesFactory?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTableStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.IDataGridEditingService?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid.HitTestType?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Design.IMenuEditorService?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `T:System.Windows.Forms.Menu`
- `T:System.Windows.Forms.Menu.MenuItemCollection`
- `T:System.Windows.Forms.MainMenu`
- `T:System.Windows.Forms.ContextMenu`
- `T:System.Windows.Forms.MenuItem`
- `T:System.Windows.Forms.ToolBar`
- `T:System.Windows.Forms.ToolBarAppearance`
- `T:System.Windows.Forms.ToolBarButton`
- `T:System.Windows.Forms.ToolBar.ToolBarButtonCollection`
- `T:System.Windows.Forms.ToolBarButtonClickEventArgs`
- `T:System.Windows.Forms.ToolBarButtonStyle`
- `T:System.Windows.Forms.ToolBarTextAlign`
- `T:System.Windows.Forms.DataGrid`
- `T:System.Windows.Forms.DataGridBoolColumn`
- `T:System.Windows.Forms.DataGridCell`
- `T:System.Windows.Forms.DataGridColumnStyle`
- `T:System.Windows.Forms.DataGridLineStyle`
- `T:System.Windows.Forms.DataGridParentRowsLabelStyle`
- `T:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter`
- `T:System.Windows.Forms.DataGridTableStyle`
- `T:System.Windows.Forms.DataGridTextBox`
- `T:System.Windows.Forms.DataGridTextBoxColumn`
- `T:System.Windows.Forms.GridColumnStylesCollection`
- `T:System.Windows.Forms.GridTablesFactory`
- `T:System.Windows.Forms.GridTableStylesCollection`
- `T:System.Windows.Forms.IDataGridEditingService`
- `T:System.Windows.Forms.DataGrid.HitTestType`
- `T:System.Windows.Forms.Design.IMenuEditorService`

-->
