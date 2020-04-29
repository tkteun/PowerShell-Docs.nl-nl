---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetConfigurationResultOutput-methode
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941570"
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

*jobId* \[in\] de id van de taak waarvoor uitvoer gegevens moeten worden opgehaald.

*resumeOutputBookmark* \[in\] geeft aan dat de uitvoer een voortzetting van een vorige blad wijzer moet zijn.

*uitvoer* \[van\] de uitvoer voor de opgegeven taak.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
