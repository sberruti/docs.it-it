---
title: <CompatSortNLSVersion> Elemento
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
ms.openlocfilehash: 30afeb2ab9380db75cbeb723ea15a23e4313c9e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154270"
---
# <a name="compatsortnlsversion-element"></a>\<Elemento di> CompatSortNLSVersion
Specifica che nel runtime devono essere utilizzati ordinamenti legacy quando si eseguono confronti di stringhe.  
  
[**\<>di configurazione**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>di runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>CompatSortNLSVersion**  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<CompatSortNLSVersion
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributes  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`enabled`|Attributo obbligatorio.<br /><br /> Specifica l'ID delle impostazioni locali di cui deve essere utilizzato l'ordinamento.|  
  
## <a name="enabled-attribute"></a>Attributo enabled  
  
|valore|Descrizione|  
|-----------|-----------------|  
|4096|ID impostazioni locali mediante il quale viene rappresentato un ordinamento alternativo. In questo caso, 4096 rappresenta l'ordinamento di .NET Framework 3.5 e versioni precedenti.|  
  
### <a name="child-elements"></a>Elementi figlio  
 No.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`configuration`|Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.|  
|`runtime`|Contiene informazioni sulle opzioni di inizializzazione in fase di esecuzione.|  
  
## <a name="remarks"></a>Osservazioni  
 Poiché le operazioni di confronto tra <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> stringhe, ordinamento e utilizzo di maiuscole e minuscole eseguite dalla classe <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> in <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> .NET Framework 4 sono conformi allo standard Unicode 5.1, i risultati dei metodi di confronto tra stringhe, ad esempio e possono differire dalle versioni precedenti di .NET Framework. Se l'applicazione dipende dal comportamento legacy, è possibile ripristinare le regole di confronto e ordinamento delle stringhe utilizzate in .NET Framework 3.5 e versioni precedenti includendo l'elemento `<CompatSortNLSVersion>` nel file di configurazione dell'applicazione.  
  
> [!IMPORTANT]
> Per il ripristino del confronto di stringhe legacy e delle regole di ordinamento è necessaria inoltre la disponibilità della libreria di collegamento dinamico sort00001000.dll nel sistema locale.  
  
 È inoltre possibile utilizzare l'ordinamento delle stringhe legacy e le regole di confronto in un dominio dell'applicazione specifico passando la stringa "NetFx40_Legacy20SortingBehavior" al metodo <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> quando si crea il dominio dell'applicazione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene creata un'istanza di due oggetti <xref:System.String> e viene chiamato il metodo <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> per confrontarle utilizzando le convenzioni delle impostazioni cultura correnti.  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 Quando si esegue l'esempio in .NET Framework 4, viene visualizzato l'output seguente:
  
```console
sta follows a in the sort order.  
```  
  
 Questo è completamente diverso dall'output che viene visualizzato quando si esegue l'esempio in.NET Framework 3.5:
  
```console
sta equals a in the sort order.  
```  
  
 Tuttavia, se si aggiunge il file di configurazione seguente alla directory dell'esempio e quindi si esegue l'esempio in .NET Framework 4, l'output sarà identico a quello prodotto dall'esempio quando viene eseguito in .NET Framework 3.5.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche

- [Schema delle impostazioni di runtime](index.md)
- [Schema del file di configurazione](../index.md)
