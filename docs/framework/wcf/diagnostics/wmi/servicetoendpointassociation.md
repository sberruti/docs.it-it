---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 3d23a3ee10c47e04ea7bdba202ea5063c0d84fac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048231"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation
Esegue il mapping di un servizio a un endpoint.  
  
## <a name="syntax"></a>Sintassi  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>Metodi  
 La classe ServiceToEndpointAssociation non definisce metodi.  
  
## <a name="properties"></a>Proprietà  
 La classe ServiceToEndpointAssociation dispone delle proprietà seguenti:  
  
### <a name="ref"></a>ref  
 Tipo di dati: Service  
  
 Tipo di accesso: Sola lettura  
Qualificatori: Chiave  
  
 Servizio associato all'endpoint.  
  
### <a name="ref"></a>ref  
 Tipo di dati: Endpoint  
  
 Tipo di accesso: Sola lettura  
Qualificatori: Chiave  
  
 Endpoint associato al servizio.  
  
## <a name="requirements"></a>Requisiti  
  
|MOF|Dichiarato in Servicemodel.mof.|  
|---------|-----------------------------------|  
|Spazio dei nomi|Definito in root\ServiceModel|
