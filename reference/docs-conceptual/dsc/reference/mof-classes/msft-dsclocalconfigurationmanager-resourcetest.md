---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: ResourceTest-methode
ms.openlocfilehash: ff06fd645a94055e79aa0f8d20f2f06e16483720
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942641"
---
# <a name="resourcetest-method"></a>ResourceTest-methode

Roept rechtstreeks de **test** methode van een DSC-resource aan.

## <a name="syntax"></a>Syntaxis

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Parameters

*ResourceType* \[Resource type\] in de naam van de resource die moet worden aangeroepen.

Module naam voor de module die de resource bevat die moet worden aangeroepen. *ModuleName* \[\]

*resource Property* \[in\] Hiermee geeft u de naam van de resource eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde. Gebruik de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) om de bron eigenschappen en hun typen te detecteren.

*InDesiredState* \[InDesiredState\] op retour waarde deze eigenschap is ingesteld op **True** als het doel knooppunt de gewenste status heeft.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
