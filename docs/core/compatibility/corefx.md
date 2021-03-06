---
title: Modifiche di rilievo della libreria di classi base
description: Elenca le modifiche di rilievo in .NET CoreFx, la libreria di classi base.
ms.date: 09/20/2019
ms.openlocfilehash: 56a3cf4f4c00a79752d5a98bb086bb9f8c0614b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147575"
---
# <a name="corefx-breaking-changes"></a>Modifiche di rilievo CoreFx

CoreFx provides the primitives and other general types used by .NET Core.

In questa pagina sono documentate le seguenti modifiche di rilievo:

| Modifica | Versione introdotta |
| - | :-: |
| [API che segnalano ora la versione del report e non la versione del file](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [Le istanze di EncoderFallbackBuffer personalizzate non possono eseguire il fallback in modo ricorsivoCustom EncoderFallbackBuffer instances cannot fallback recursively](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [Formattazione a virgola mobile e modifiche del comportamento di analisi](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [Le operazioni di analisi a virgola mobile non hanno più esito negativo o generano un'eccezione OverflowException](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [InvalidAsynchronousStateException spostato in un altro assembly](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [NET Core 3.0 segue le procedure consigliate di Unicode quando si sostituiscono sequenze di byte UTF-8 in formato non corretto](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | 3.0 |
| [TypeDescriptionProviderAttribute spostato in un altro assembly](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [La voce non gestisce più gli archivi con dimensioni di voce incoerenti](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [Tipo di eccezione del serializzatore JSON modificato da JsonException a NotSupportedException](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | 3.0 |
| [Modifica della semantica di (stringa)null in Utf8JsonWriter](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | 3.0 |
| [I metodi JsonEncodedText.Encode hanno un argomento JavaScriptEncoder aggiuntivo](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | 3.0 |
| [Firma JsonFactoryConverter.CreateConverter modificata](#jsonfactoryconvertercreateconverter-signature-changed) | 3.0 |
| [Modifiche all'API JsonElement](#jsonelement-api-changes) | 3.0 |
| [FieldInfo.SetValue genera un'eccezione per i campi statici di solo init](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [Campi privati aggiunti ai tipi struct predefinitiPrivate fields added to built-in struct types](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [Modifica del valore predefinito di UseShellExecute](#change-in-default-value-of-useshellexecute) | 2.1 |
| [Versioni OpenSSL su macOS](#openssl-versions-on-macos) | 2.1 |
| [UnauthorizedAccessException generata da FileSystemInfo.Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
