---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: TestConfiguration-methode
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942585"
---
# <a name="testconfiguration-method"></a>TestConfiguration-methode

Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de huidige configuratie gecontroleerd op basis van het document.

## <a name="syntax"></a>Syntaxis

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>Parameters

*configurationData* \[in @ no__t-2-omgevings gegevens voor de confuguration.

*InDesiredState* \[out @ no__t-2 bij Return geeft aan of het beheerde knoop punt zich in de staat bevindt die is opgegeven in het configuratie document.

*ResourcesInDesiredState* \[out @ no__t-2 bij Return bevat een Inge sloten instantie van de klasse **MSFT_ResourceInDesiredState** waarmee resources worden opgegeven die de gewenste status hebben.

*ResourcesNotInDesiredState* \[out @ no__t-2 bij Return bevat een Inge sloten instantie van de klasse **MSFT_ResourceNotInDesiredState** waarmee resources worden opgegeven die niet de gewenste status hebben.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MANAGE** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
