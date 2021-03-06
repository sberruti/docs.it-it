---
title: Modifiche di rilievo - .NET Framework a .NET CoreBreaking changes - .NET Framework to .NET Core
titleSuffix: ''
description: Vengono elencate le modifiche di rilievo da .NET Framework a .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: f712be14d7debc4b3008f8459e6ee925754b25f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449400"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Modifiche di rilievo per la migrazione da .NET Framework a .NET Core

Se si esegue la migrazione di un'app da .NET Framework a .NET Core, le modifiche di rilievo elencate in questo articolo potrebbero influire sull'utente. Le modifiche di rilievo sono raggruppate per categoria e all'interno di tali categorie, in base alla versione di .NET Core in cui sono state introdotte.

> [!NOTE]
> Questo articolo non è un elenco completo delle modifiche di rilievo tra .NET Framework e .NET Core.This article is not a complete list of breaking changes between .NET Framework and .NET Core. I cambiamenti di rilievo più importanti vengono aggiunti qui quando veniamo a conoscenza di loro.

## <a name="corefx"></a>CoreFx

- [Modifica del valore predefinito di UseShellExecute](#change-in-default-value-of-useshellexecute)
- [UnauthorizedAccessException generata da FileSystemInfo.Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a>Crittografia

- [Il parametro booleano di SignedCms.ComputeSignature è rispettato](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a>Windows Form

Il supporto di Windows Form è stato aggiunto a .NET Core nella versione 3.0.Windows Forms support was added to .NET Core in version 3.0. Se stai eseguendo la migrazione di un'app Windows Form da .NET Framework a .NET Core, le modifiche di rilievo elencate di seguito potrebbero influire sull'app.

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

### <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="see-also"></a>Vedere anche

- [API che generano sempre eccezioni in .NET Core](unsupported-apis.md)
- [Tecnologie di .NET Framework non disponibili in .NET Core](../porting/net-framework-tech-unavailable.md)
