---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfigurationResultOutput-methode
description: GetConfigurationResultOutput-methode
ms.openlocfilehash: 7c885109b3078189b7ac653733a5fb24db66312e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644705"
---
# <a name="getconfigurationresultoutput-method"></a>GetConfigurationResultOutput-methode

Hiermee wordt de uitvoer van de configuratie agent opgehaald die is gekoppeld aan een specifieke taak.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
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

**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
