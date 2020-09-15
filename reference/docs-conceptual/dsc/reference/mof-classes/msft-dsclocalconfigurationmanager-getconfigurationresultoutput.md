---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: GetConfigurationResultOutput-methode
ms.openlocfilehash: 9c81082c28b2ffcc329264d29784782deaa9779d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464074"
---
# <a name="getconfigurationresultoutput-method"></a>GetConfigurationResultOutput-methode

Hiermee wordt de uitvoer van de configuratie agent opgehaald die is gekoppeld aan een specifieke taak.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>Parameters

**jobId** \[ in \] de id van de taak waarvoor uitvoer gegevens moeten worden opgehaald.

**resumeOutputBookmark** \[ in \] geeft aan dat de uitvoer een voortzetting van een vorige blad wijzer moet zijn.

**uitvoer** \[ \] de uitvoer voor de opgegeven taak.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
