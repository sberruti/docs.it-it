---
title: Modifiche di rilievo-.NET Framework a .NET Core
description: Elenca le modifiche di rilievo da .NET Framework a .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: 9f4ecc8a9de7279bb4b222b3df77e1eb17b33f0a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937397"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="e5aeb-103">Modifiche di rilievo per la migrazione da .NET Framework a .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5aeb-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="e5aeb-104">Se si esegue la migrazione di un'app da .NET Framework a .NET Core, le modifiche di rilievo elencate in questo articolo potrebbero interessare l'utente.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="e5aeb-105">Le modifiche di rilievo sono raggruppate per categoria e all'interno di tali categorie dalla versione di .NET Core introdotte in.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core they were introduced in.</span></span>

> [!NOTE]
> <span data-ttu-id="e5aeb-106">Questo articolo non è un elenco completo delle modifiche di rilievo tra .NET Framework e .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="e5aeb-107">Di seguito sono riportate le modifiche di rilievo più importanti che verranno acquisite.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="e5aeb-108">CoreFx</span><span class="sxs-lookup"><span data-stu-id="e5aeb-108">CoreFx</span></span>

<span data-ttu-id="e5aeb-109">Modifiche di rilievo:</span><span class="sxs-lookup"><span data-stu-id="e5aeb-109">Breaking changes:</span></span>

- [<span data-ttu-id="e5aeb-110">Modificare il valore predefinito di UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="e5aeb-110">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)

***

### <a name="net-core-21"></a><span data-ttu-id="e5aeb-111">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e5aeb-111">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="e5aeb-112">Windows Form</span><span class="sxs-lookup"><span data-stu-id="e5aeb-112">Windows Forms</span></span>

<span data-ttu-id="e5aeb-113">È stato aggiunto il supporto Windows Forms a .NET Core nella versione 3,0.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-113">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="e5aeb-114">Se si esegue la migrazione di un'app Windows Forms da .NET Framework a .NET Core, le modifiche di rilievo elencate qui potrebbero influire sull'app.</span><span class="sxs-lookup"><span data-stu-id="e5aeb-114">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

<span data-ttu-id="e5aeb-115">Modifiche di rilievo:</span><span class="sxs-lookup"><span data-stu-id="e5aeb-115">Breaking changes:</span></span>

- [<span data-ttu-id="e5aeb-116">Controlli rimossi</span><span class="sxs-lookup"><span data-stu-id="e5aeb-116">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="e5aeb-117">Evento CellFormatting non generato se viene visualizzata la descrizione comando</span><span class="sxs-lookup"><span data-stu-id="e5aeb-117">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="e5aeb-118">Control. DefaultFont modificato in Segoe UI 9 PT</span><span class="sxs-lookup"><span data-stu-id="e5aeb-118">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="e5aeb-119">Modernizzazione di FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="e5aeb-119">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="e5aeb-120">SerializableAttribute rimosso da alcuni tipi di Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5aeb-120">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="e5aeb-121">Opzione di compatibilità AllowUpdateChildControlIndexForTabControls non supportata</span><span class="sxs-lookup"><span data-stu-id="e5aeb-121">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="e5aeb-122">Opzione di compatibilità DomainUpDown. UseLegacyScrolling non supportata</span><span class="sxs-lookup"><span data-stu-id="e5aeb-122">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="e5aeb-123">Opzione di compatibilità DoNotLoadLatestRichEditControl non supportata</span><span class="sxs-lookup"><span data-stu-id="e5aeb-123">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="e5aeb-124">Opzione di compatibilità DoNotSupportSelectAllShortcutInMultilineTextBox non supportata</span><span class="sxs-lookup"><span data-stu-id="e5aeb-124">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="e5aeb-125">Opzione di compatibilità DontSupportReentrantFilterMessage non supportata</span><span class="sxs-lookup"><span data-stu-id="e5aeb-125">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="e5aeb-126">Opzione di compatibilità EnableVisualStyleValidation non supportata</span><span class="sxs-lookup"><span data-stu-id="e5aeb-126">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="e5aeb-127">Opzione di compatibilità UseLegacyContextMenuStripSourceControlValue non supportata</span><span class="sxs-lookup"><span data-stu-id="e5aeb-127">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="e5aeb-128">Opzione di compatibilità UseLegacyImages non supportata</span><span class="sxs-lookup"><span data-stu-id="e5aeb-128">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="e5aeb-129">Modifica dell'accesso per AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="e5aeb-129">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="e5aeb-130">API duplicate rimosse da Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5aeb-130">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="e5aeb-131">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="e5aeb-131">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="e5aeb-132">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e5aeb-132">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9 pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a><span data-ttu-id="e5aeb-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e5aeb-133">See also</span></span>

- [<span data-ttu-id="e5aeb-134">API che generano sempre eccezioni in .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5aeb-134">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="e5aeb-135">.NET Framework tecnologie non disponibili in .NET Core</span><span class="sxs-lookup"><span data-stu-id="e5aeb-135">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
