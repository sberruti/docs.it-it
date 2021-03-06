---
title: Elemento <TimeSpan_LegacyFormatMode>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: 9d9eedf52f5d711412e4549e39e6ea23abb68ff3
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968902"
---
# <a name="timespan_legacyformatmode-element"></a>\<TimeSpan_LegacyFormatMode elemento >

Determina se il runtime conserva il comportamento legacy nelle operazioni di formattazione con valori <xref:System.TimeSpan?displayProperty=nameWithType>.

[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp; **&nbsp;&nbsp;\<TimeSpan_LegacyFormatMode >**  

## <a name="syntax"></a>Sintassi

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi

Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`enabled`|Attributo obbligatorio.<br /><br /> Specifica se il runtime usa il comportamento di formattazione legacy con valori <xref:System.TimeSpan?displayProperty=nameWithType>.|

## <a name="enabled-attribute"></a>Attributo enabled

|Value|Descrizione|
|-----------|-----------------|
|`false`|Il runtime non ripristina il comportamento di formattazione legacy.|
|`true`|Il runtime ripristina il comportamento di formattazione legacy.|

### <a name="child-elements"></a>Elementi figlio

Nessuna.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|`configuration`|Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.|
|`runtime`|Contiene informazioni sulle opzioni di inizializzazione in fase di esecuzione.|

## <a name="remarks"></a>Note

A partire da .NET Framework 4, la struttura <xref:System.TimeSpan?displayProperty=nameWithType> implementa l'interfaccia <xref:System.IFormattable> e supporta le operazioni di formattazione con stringhe di formato standard e personalizzate. Se un metodo di analisi rileva un identificatore di formato non supportato o una stringa di formato, viene generata un'<xref:System.FormatException>.

Nelle versioni precedenti del .NET Framework la struttura <xref:System.TimeSpan> non implementava <xref:System.IFormattable> e non supportava le stringhe di formato. Tuttavia, molti sviluppatori presumevano erroneamente che <xref:System.TimeSpan> supportasse un set di stringhe di formato e le usavaro nelle [operazioni di formattazione composita](../../../../standard/base-types/composite-formatting.md) con metodi come <xref:System.String.Format%2A?displayProperty=nameWithType>. In genere, se un tipo implementa <xref:System.IFormattable> e supporta le stringhe di formato, le chiamate ai metodi di formattazione con stringhe di formato non supportate in genere generano una <xref:System.FormatException>. Tuttavia, poiché <xref:System.TimeSpan> non implementa <xref:System.IFormattable>, il runtime ignora la stringa di formato e chiama invece il metodo <xref:System.TimeSpan.ToString?displayProperty=nameWithType>. Ciò significa che, anche se le stringhe di formato non hanno effetto sull'operazione di formattazione, la loro presenza non ha restituito un <xref:System.FormatException>.

Per i casi in cui il codice legacy passa un metodo di formattazione composita e una stringa di formato non valida e tale codice non può essere ricompilato, è possibile usare l'elemento `<TimeSpan_LegacyFormatMode>` per ripristinare il comportamento di <xref:System.TimeSpan> legacy. Quando si imposta l'attributo `enabled` di questo elemento su `true`, il metodo di formattazione composita genera una chiamata a <xref:System.TimeSpan.ToString?displayProperty=nameWithType> anziché <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>e non viene generata un'<xref:System.FormatException>.

## <a name="example"></a>Esempio

Nell'esempio seguente viene creata un'istanza di un oggetto <xref:System.TimeSpan> e viene effettuato un tentativo di formattarlo con il metodo <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> utilizzando una stringa di formato standard non supportata.

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

Quando si esegue l'esempio in .NET Framework 3,5 o in una versione precedente, viene visualizzato l'output seguente:

```console
12:30:45
```

Questa operazione è notevolmente diversa rispetto all'output se si esegue l'esempio in .NET Framework 4 o versione successiva:

```console
Invalid Format
```

Tuttavia, se si aggiunge il file di configurazione seguente alla directory dell'esempio e quindi si esegue l'esempio in .NET Framework 4 o versione successiva, l'output sarà identico a quello prodotto dall'esempio quando viene eseguito in .NET Framework 3,5.

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Vedere anche

- [Schema delle impostazioni di runtime](index.md)
- [Schema dei file di configurazione](../index.md)
