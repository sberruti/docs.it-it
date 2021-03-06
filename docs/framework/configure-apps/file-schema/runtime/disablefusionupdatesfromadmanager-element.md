---
title: <disableFusionUpdatesFromADManager> Elemento
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117448"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<elemento > disableFusionUpdatesFromADManager
Specifica se è disabilitato il comportamento predefinito, ovvero consentire all'host di runtime di eseguire l'override delle impostazioni di configurazione per un dominio applicazione.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<disableFusionUpdatesFromADManager >**  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|enabled|Attributo obbligatorio.<br /><br /> Specifica se la capacità predefinita di eseguire l'override delle impostazioni Fusion è disabilitata.|  
  
## <a name="enabled-attribute"></a>Attributo enabled  
  
|Value|Descrizione|  
|-----------|-----------------|  
|0|Non disabilitare la possibilità di eseguire l'override delle impostazioni Fusion. Si tratta del comportamento predefinito, a partire da .NET Framework 4.|  
|1|Disabilitare la possibilità di eseguire l'override delle impostazioni Fusion. In questo modo viene ripristinato il comportamento delle versioni precedenti del .NET Framework.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuna.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`configuration`|Elemento radice in ciascun file di configurazione usato in Common Language Runtime e nelle applicazioni .NET Framework.|  
|`runtime`|Contiene informazioni sull'associazione degli assembly e sull'operazione di Garbage Collection.|  
  
## <a name="remarks"></a>Note  
 A partire da .NET Framework 4, il comportamento predefinito consiste nel consentire all'oggetto <xref:System.AppDomainManager> di eseguire l'override delle impostazioni di configurazione usando la proprietà <xref:System.AppDomainSetup.ConfigurationFile%2A> o il metodo <xref:System.AppDomainSetup.SetConfigurationBytes%2A> dell'oggetto <xref:System.AppDomainSetup> passato all'implementazione del metodo <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> , nella sottoclasse di <xref:System.AppDomainManager>. Per il dominio applicazione predefinito, le impostazioni modificate sostituiscono le impostazioni specificate dal file di configurazione dell'applicazione. Per gli altri domini applicazione, eseguono l'override delle impostazioni di configurazione passate al metodo <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> o <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>.  
  
 È possibile passare le nuove informazioni di configurazione o passare null (`Nothing` in Visual Basic) per eliminare le informazioni di configurazione passate.  
  
 Non passare le informazioni di configurazione sia alla proprietà <xref:System.AppDomainSetup.ConfigurationFile%2A> sia al metodo <xref:System.AppDomainSetup.SetConfigurationBytes%2A>. Se si passano le informazioni di configurazione a entrambe, le informazioni passate alla proprietà <xref:System.AppDomainSetup.ConfigurationFile%2A> vengono ignorate, perché il metodo <xref:System.AppDomainSetup.SetConfigurationBytes%2A> esegue l'override delle informazioni di configurazione dal file di configurazione dell'applicazione. Se si usa la proprietà <xref:System.AppDomainSetup.ConfigurationFile%2A>, è possibile passare null (`Nothing` in Visual Basic) al metodo <xref:System.AppDomainSetup.SetConfigurationBytes%2A> per eliminare tutti i byte di configurazione specificati nella chiamata al metodo <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> o <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>.  
  
 Oltre alle informazioni di configurazione, è possibile modificare le impostazioni seguenti nell'oggetto <xref:System.AppDomainSetup> passato all'implementazione del metodo <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A><xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>e <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 In alternativa all'uso dell'elemento `<disableFusionUpdatesFromADManager>`, è possibile disabilitare il comportamento predefinito creando un'impostazione del registro di sistema o impostando una variabile di ambiente. Nel registro di sistema creare un valore DWORD denominato `COMPLUS_disableFusionUpdatesFromADManager` in `HKCU\Software\Microsoft\.NETFramework` o `HKLM\Software\Microsoft\.NETFramework`, quindi impostare il valore su 1. Nella riga di comando impostare la variabile di ambiente `COMPLUS_disableFusionUpdatesFromADManager` su 1.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come disabilitare la possibilità di eseguire l'override delle impostazioni Fusion utilizzando l'elemento `<disableFusionUpdatesFromADManager>`.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Vedere anche

- [Schema delle impostazioni di runtime](index.md)
- [Schema dei file di configurazione](../index.md)
- [Come il runtime individua gli assembly](../../../deployment/how-the-runtime-locates-assemblies.md)
