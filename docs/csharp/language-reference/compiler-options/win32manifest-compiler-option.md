---
title: -win32manifest (opzioni del compilatore C#)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 24677b145974af03e6ddcac1b9bab5907ab70c7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "69924679"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (opzioni del compilatore C#)
Usare l'opzione **-win32manifest** per specificare un file manifesto dell'applicazione Win32 definito dall'utente da incorporare nel file PE (Portable Executable) di un progetto.  
  
## <a name="syntax"></a>Sintassi  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Argomenti  
 `filename`  
 Nome e percorso del file manifesto personalizzato.  
  
## <a name="remarks"></a>Osservazioni  
 Per impostazione predefinita, il compilatore Visual C# incorpora un manifesto dell'applicazione che specifica il livello di esecuzione richiesto "asInvoker". Viene creato il manifesto nella stessa cartella in cui viene compilato l'eseguibile, in genere la cartella bin\Debug o bin\Release quando si utilizza Visual Studio. Se si desidera fornire un manifesto personalizzato, ad esempio per specificare un livello di esecuzione richiesto "highestAvailable" o "requireAdministrator", utilizzare questa opzione per specificare il nome del file.  
  
> [!NOTE]
> Questa opzione e l'opzione [-win32res (opzioni del compilatore C#)](./win32res-compiler-option.md) si escludono a vicenda. Se si tenta di usare entrambe le opzioni nella stessa riga di comando si otterrà un errore di compilazione.  
  
 Un'applicazione senza un manifesto che specifichi il livello di esecuzione richiesto è soggetta alla virtualizzazione dei file e del Registro di sistema con la funzionalità Controllo account utente in Windows. Per altre informazioni, vedere [Controllo dell'account utente](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 L'applicazione sarà sottoposta a virtualizzazione se una di queste condizioni è vera:  
  
- Si usa l'opzione **-nowin32manifest** e non si specifica un manifesto in una fase successiva della compilazione o come parte di un file di risorse di Windows (con estensione res) usando l'opzione **-win32res**.  
  
- Si indica un manifesto personalizzato che non specifica un livello di esecuzione richiesto.  
  
 Visual Studio crea un file manifesto predefinito e lo memorizza nelle directory di debug e versione insieme al file eseguibile. Per aggiungere un manifesto personalizzato, crearne uno in qualsiasi editor di testo e quindi aggiungere il file al progetto. In alternativa, fare clic con il pulsante destro del mouse sull'icona **Progetto** in **Esplora soluzioni**, fare clic su **Aggiungi nuovo elemento** e quindi scegliere **File manifesto applicazione**. Dopo aver aggiunto il file manifesto nuovo o esistente, il file apparirà nell'elenco a discesa **Manifesto**. Per altre informazioni, vedere [Pagina dell'applicazione, Progettazione progetti (C )](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 È possibile inserire il manifesto dell'applicazione come passaggio personalizzato dopo la compilazione o come parte di un file di risorse Win32 usando l'opzione [-nowin32manifest (opzioni del compilatore C#)](./nowin32manifest-compiler-option.md). Usare la stessa opzione se si vuole che l'applicazione sia sottoposta alla virtualizzazione dei file o del Registro di sistema in Windows Vista. Ciò impedirà al compilatore di creare e incorporare un manifesto predefinito nel file eseguibile portabile (PE).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il manifesto predefinito che il compilatore Visual C# inserisce in un file PE.  
  
> [!NOTE]
> Il compilatore inserisce un nome di applicazione standard "MyApplication.app" nel file XML. Si tratta di una soluzione alternativa per consentire l'esecuzione delle applicazioni in Windows Server 2003 Service Pack 3.  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>Vedere anche

- [Opzioni del compilatore C](./index.md)
- [-nowin32manifest (opzioni del compilatore C](./nowin32manifest-compiler-option.md)
- [Gestione delle proprietà di progetti e soluzioni](/visualstudio/ide/managing-project-and-solution-properties)
