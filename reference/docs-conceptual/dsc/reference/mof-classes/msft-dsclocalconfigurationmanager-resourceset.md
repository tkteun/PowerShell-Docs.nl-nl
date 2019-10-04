---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: ResourceSet-methode
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942648"
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

Resource *type* \[in @ no__t-2 de naam van de resource die moet worden aangeroepen.

*Module* naam \[in @ no__t-2 de name van de module die de resource bevat die moet worden aangeroepen.

*resource property* \[in @ no__t-2 geeft de naam van de bron eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde. Gebruik de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) om de bron eigenschappen en hun typen te detecteren.

*RebootRequired* \[out @ no__t-2 bij Return wordt deze eigenschap ingesteld op **True** als het doel knooppunt opnieuw moet worden opgestart.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MANAGE** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
