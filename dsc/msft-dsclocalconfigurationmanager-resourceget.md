---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: ResourceGet-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2c055b3fab468f85c9e2f91cf1eaf1a4353b4660
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a>ResourceGet-methode van de klasse MSFT_DSCLocalConfigurationManager

Rechtstreeks roept de **ophalen** methode van een DSC-resource.

<a name="syntax"></a>Syntaxis
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a>Parameters
----------

*ResourceType* \[in\]  
De naam van de bron aan te roepen.

*ModuleName* \[in\]  
De naam van de module met de bron aan te roepen.

*resourceProperty* \[in\]  
Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hashtabel als de sleutel en waarde, respectievelijk. Gebruik de [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet voor het detecteren van de resource-eigenschappen en hun typen.

*configuraties* \[uit\]  
Bevat een ingesloten exemplaar van de configuraties op return.

## <a name="return-value"></a>Retourwaarde
------------

Retourneert nul geslaagd; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Zie ook


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



