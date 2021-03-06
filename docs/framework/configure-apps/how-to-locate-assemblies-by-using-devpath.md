---
title: 'Procedura: Individuare assembly usando DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912992"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Procedura: Individuare assembly usando DEVPATH
Gli sviluppatori potrebbero voler assicurarsi che un assembly condiviso che compilano funzioni correttamente con più applicazioni. Anziché inserire continuamente l'assembly nel Global Assembly Cache durante il ciclo di sviluppo, lo sviluppatore può creare una variabile di ambiente DEVPATH che punti alla directory di output di compilazione per l'assembly.  
  
 Si supponga, ad esempio, che si stia compilando un assembly condiviso denominato MySharedAssembly e che la directory di output sia C:\MySharedAssembly\Debug. È possibile inserire C:\MySharedAssembly\Debug nella variabile DEVPATH. È quindi necessario specificare l' [ \<elemento > DevelopmentMode](./file-schema/runtime/developmentmode-element.md) nel file di configurazione del computer. Questo elemento indica al Common Language Runtime di utilizzare DEVPATH per individuare gli assembly.  
  
 L'assembly condiviso deve essere individuabile dal runtime.  Per specificare una directory privata per la risoluzione dei riferimenti ad assembly, usare l' [ \<elemento codeBase >](./file-schema/runtime/codebase-element.md) o [ \<l'elemento >](./file-schema/runtime/probing-element.md) di probe in un file di configurazione, come descritto in [specifica della posizione di un assembly](specify-assembly-location.md).  È anche possibile inserire l'assembly in una sottodirectory della directory dell'applicazione. Per altre informazioni, vedere [Modalità di individuazione di assembly del runtime](../deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
> Si tratta di una funzionalità avanzata, destinata solo allo sviluppo.  
  
 Nell'esempio seguente viene illustrato come fare in modo che il runtime cerchi gli assembly nelle directory specificate dalla variabile di ambiente DEVPATH.  
  
## <a name="example"></a>Esempio  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 Per impostazione predefinita, questa impostazione è false.  
  
> [!NOTE]
> Usare questa impostazione solo in fase di sviluppo. Il runtime non controlla le versioni in assembly con nome sicuro presenti in DEVPATH. Usa semplicemente il primo assembly trovato.  
  
## <a name="see-also"></a>Vedere anche

- [Configurazione di app tramite file di configurazione](index.md)
