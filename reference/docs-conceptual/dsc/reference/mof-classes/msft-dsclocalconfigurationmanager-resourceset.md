---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: ResourceSet-methode
ms.openlocfilehash: c015960b2a5ffca0d28b714d571aa616400555bd
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464045"
---
# <a name="resourceset-method"></a>ResourceSet-methode

Roept rechtstreeks de **ingestelde** methode van een DSC-resource aan.

## <a name="syntax"></a>Syntaxis

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a>Parameters

**Resource type** \[ in \] de naam van de resource die moet worden aangeroepen.

**Module naam** \[ in \] de naam van de module die de resource bevat die moet worden aangeroepen.

**resource Property** \[ in \] geeft de naam van de bron eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde. Gebruik de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) om de bron eigenschappen en hun typen te detecteren.

**RebootRequired** \[ \] Deze eigenschap wordt ingesteld op **True** als het doel knooppunt opnieuw moet worden opgestart.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
