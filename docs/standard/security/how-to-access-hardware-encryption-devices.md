---
title: 'Procedura: accedere ai dispositivi di crittografia hardware'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
ms.openlocfilehash: d6ee22fd9fb0c11e22ac01ff83b3269e37e37763
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706175"
---
# <a name="how-to-access-hardware-encryption-devices"></a>Procedura: accedere ai dispositivi di crittografia hardware
È possibile usare la classe <xref:System.Security.Cryptography.CspParameters> per accedere ai dispositivi di crittografia hardware. Questa classe può essere usata, ad esempio, per integrare l'applicazione in uso con una smart card, un generatore di numeri casuali hardware o per l'implementazione hardware di un determinato algoritmo di crittografia.  
  
 La classe <xref:System.Security.Cryptography.CspParameters> crea un provider del servizio di crittografia (CSP, Cryptographic Service Provider) che accede a un dispositivo di crittografia hardware installato correttamente.  È possibile verificare la disponibilità di un CSP esaminando la chiave del Registro di sistema (Regedit.exe): HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Per firmare i dati mediante una scheda di chiavi  
  
1. Creare una nuova istanza della classe <xref:System.Security.Cryptography.CspParameters>, passando il tipo di provider integer e il nome del provider al costruttore.  
  
2. Passare i flag appropriati alla proprietà <xref:System.Security.Cryptography.CspParameters.Flags%2A> dell'oggetto <xref:System.Security.Cryptography.CspParameters> appena creato.  Passare, ad esempio, il flag <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer>.  
  
3. Creare una nuova istanza di una classe <xref:System.Security.Cryptography.AsymmetricAlgorithm> (ad esempio, la classe <xref:System.Security.Cryptography.RSACryptoServiceProvider>), passando l'oggetto <xref:System.Security.Cryptography.CspParameters> al costruttore.  
  
4. Firmare i dati mediante uno dei metodi `Sign` e verificarli mediante uno dei metodi `Verify`.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Per generare un numero casuale usando un generatore di numeri casuali hardware  
  
1. Creare una nuova istanza della classe <xref:System.Security.Cryptography.CspParameters>, passando il tipo di provider integer e il nome del provider al costruttore.  
  
2. Creare una nuova istanza della classe <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, passando l'oggetto <xref:System.Security.Cryptography.CspParameters> al costruttore.  
  
3. Creare un valore casuale usando il metodo <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> o <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A>.  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente illustra come firmare i dati mediante una smart card.  L'esempio di codice crea un oggetto <xref:System.Security.Cryptography.CspParameters> che espone una smart card, quindi inizializza un oggetto <xref:System.Security.Cryptography.RSACryptoServiceProvider> mediante il CSP  e infine firma e verifica alcuni dati.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
  
- Includere gli spazi dei nomi <xref:System> e <xref:System.Security.Cryptography>.  
  
- È necessario avere un lettore di smart card e driver installati nel computer.  
  
- È necessario inizializzare l'oggetto <xref:System.Security.Cryptography.CspParameters> usando informazioni specifiche del lettore di smart card.  Per altre informazioni, vedere la documentazione relativa al lettore.
