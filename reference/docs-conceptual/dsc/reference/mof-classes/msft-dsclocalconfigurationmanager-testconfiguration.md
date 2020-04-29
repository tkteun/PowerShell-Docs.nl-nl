---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: TestConfiguration-methode
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
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

*configurationData* \[in\] omgevings gegevens voor de confuguration.

*InDesiredState* \[out\] bij retour, geeft aan of het beheerde knoop punt zich in de status bevindt die is opgegeven in het configuratie document.

*ResourcesInDesiredState* \[out\] on return bevat een Inge sloten instantie van de klasse **MSFT_ResourceInDesiredState** waarmee resources worden opgegeven die de gewenste status hebben.

*ResourcesNotInDesiredState* \[out\] on return bevat een Inge sloten instantie van de klasse **MSFT_ResourceNotInDesiredState** waarmee resources worden opgegeven die niet de gewenste status hebben.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
