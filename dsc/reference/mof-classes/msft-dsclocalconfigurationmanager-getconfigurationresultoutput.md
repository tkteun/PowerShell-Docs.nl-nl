---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetConfigurationResultOutput-methode
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727128"
---
# <a name="getconfigurationresultoutput-method"></a>De GetConfigurationResultOutput-methode

Hiermee haalt u de uitvoer van de Configuration-Agent die is gekoppeld aan een specifieke taak.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a>Parameters

*jobId* \[in\] de ID van de taak waarvoor u uitvoergegevens op te halen.

*resumeOutputBookmark* \[in\] geeft aan dat de uitvoer er een voortzetting van een vorige bladwijzer moet.

*uitvoer* \[uit\] de uitvoer voor de gespecificeerde taak.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
