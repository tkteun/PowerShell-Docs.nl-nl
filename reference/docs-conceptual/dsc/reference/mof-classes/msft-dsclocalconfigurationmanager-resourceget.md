---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: ResourceGet-methode
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942676"
---
# <a name="resourceget-method"></a>ResourceGet-methode

Roept rechtstreeks de **Get** -methode van een DSC-resource aan.

## <a name="syntax"></a>Syntaxis

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a>Parameters

*ResourceType* \[Resource type\] in de naam van de resource die moet worden aangeroepen.

Module naam voor de module die de resource bevat die moet worden aangeroepen. *ModuleName* \[\]

*resource Property* \[in\] Hiermee geeft u de naam van de resource eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde. Gebruik de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) om de bron eigenschappen en hun typen te detecteren.

*configuraties* \[uit\] op retour, bevat een Inge sloten exemplaar van de configuraties.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
