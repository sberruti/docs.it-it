---
title: Classi non sealed
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6804a79e8beee1d42e313509966b46239e66c25f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743558"
---
# <a name="unsealed-classes"></a>Classi non sealed
Le classi sealed non possono essere ereditate da e impediscono l'estensibilità. Al contrario, le classi che possono essere ereditate da sono denominate classi non sealed.

 ✔️ CONSIGLIABILE utilizzare classi non sealed senza membri virtuali o protetti aggiunti come un ottimo modo per offrire un'estendibilità economica ma molto apprezzata a un Framework.

 Gli sviluppatori spesso desiderano ereditare da classi non sealed per aggiungere pratici membri, ad esempio costruttori personalizzati, nuovi metodi o overload del metodo. Ad esempio, `System.Messaging.MessageQueue` non è sealed e quindi consente agli utenti di creare code personalizzate per impostazione predefinita su un determinato percorso della coda o di aggiungere metodi personalizzati che semplificano l'API per scenari specifici.

 Per impostazione predefinita, le classi sono non sealed nella maggior parte dei linguaggi di programmazione ed è anche l'impostazione predefinita consigliata per la maggior parte delle classi nei Framework. L'estendibilità garantita dai tipi non sealed è molto apprezzata dagli utenti del Framework e piuttosto economica da fornire a causa dei costi di test relativamente bassi associati ai tipi non sealed.

 *Parti © 2005, 2009 Microsoft Corporation. Tutti i diritti riservati.*

 *Ristampato con l'autorizzazione di Pearson Education, Inc. da [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2a edizione](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) di Krzysztof Cwalina and Brad Abrams, pubblicato il 22 ottobre 2008 da Addison-Wesley Professional nella collana Microsoft Windows Development Series.*

## <a name="see-also"></a>Vedere anche

- [Linee guida per la progettazione di Framework](../../../docs/standard/design-guidelines/index.md)
- [Progettazione finalizzata all'estensibilità](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Sealing](../../../docs/standard/design-guidelines/sealing.md)
