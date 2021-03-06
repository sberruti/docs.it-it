---
title: Modifiche di rilievo di Windows Form
description: Vengono elencate le modifiche di rilievo in Windows Form per .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 7fba78382d011bc9d489924fa185a44e598c5a76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399098"
---
# <a name="breaking-changes-in-windows-forms"></a>Modifiche di rilievo in Windows FormBreaking changes in Windows Forms

Il supporto di Windows Form è stato aggiunto a .NET Core nella versione 3.0.Windows Forms support was added to .NET Core in version 3.0. In questo articolo vengono elencate le modifiche di rilievo per Windows Form dalla versione di .NET Core in cui sono state introdotte. Se si sta aggiornando un'app Windows Form da .NET Framework o da una versione precedente di .NET Core (3.0 o versione successiva), questo articolo è applicabile all'utente.

In questa pagina sono documentate le seguenti modifiche di rilievo:

- [Controlli rimossi](#removed-controls)
- [Evento CellFormatting non generato se è visualizzata la descrizione comando](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control.DefaultFont modificato in Segoe UI 9 pt](#default-control-font-changed-to-segoe-ui-9-pt)
- [Modernizzazione di FolderBrowserDialog](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute rimosso da alcuni tipi di Windows Form](#serializableattribute-removed-from-some-windows-forms-types)
- [Opzione di compatibilità AllowUpdateChildControlIndexForTabControls non supportata](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [Opzione di compatibilità DomainUpDown.UseLegacyScrolling non supportata](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [Opzione di compatibilità DoNotLoadLatestRichEditControl non supportata](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [L'opzione di compatibilità DoNotSupportSelectAllShortcutInMultilineTextBox non è supportata](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [Non è supportata l'opzione di compatibilità DontSupportReentrantFilterMessage](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [EnableVisualStyleValidation opzione di compatibilità non supportata](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [Opzione di compatibilità UseLegacyContextMenuStripSourceControlValue non supportata](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [Opzione di compatibilità UseLegacyImages non supportata](#uselegacyimages-compatibility-switch-not-supported)
- [Modifica dell'accesso per AccessibleObject.RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [API duplicate rimosse da Windows Form](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a>Vedere anche

- [Convertire un'app Windows Form in .NET Core](../porting/winforms.md)
