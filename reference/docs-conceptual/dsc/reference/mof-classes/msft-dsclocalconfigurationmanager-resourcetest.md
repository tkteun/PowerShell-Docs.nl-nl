---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceTest-methode
description: ResourceTest-methode
ms.openlocfilehash: cbac53ea96a59ec92fa840f75cd264a3125b965a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650670"
---
# <a name="resourcetest-method"></a>ResourceTest-methode

Roept rechtstreeks de **test** methode van een DSC-resource aan.

## <a name="syntax"></a>Syntaxis

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Parameters

**Resource type** \[ in \] de naam van de resource die moet worden aangeroepen.

**Module naam** \[ in \] de naam van de module die de resource bevat die moet worden aangeroepen.

**_resource Property_* \[ in \] geeft de naam van de bron eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde. Gebruik de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) om de bron eigenschappen en hun typen te detecteren.

*InDesiredState* *  InDesiredState \[ \]Deze eigenschap wordt ingesteld op **True** als het doel knooppunt de gewenste status heeft.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
