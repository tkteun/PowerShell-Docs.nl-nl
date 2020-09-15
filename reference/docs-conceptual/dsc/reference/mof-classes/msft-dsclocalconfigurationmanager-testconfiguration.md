---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: TestConfiguration-methode
ms.openlocfilehash: 0611c4d5543c49b879bef9b60cafdd0b055c9b86
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464295"
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

**configurationData** \[ in \] omgevings gegevens voor de configuratie.

**InDesiredState** \[ \] Hiermee geeft u op of het beheerde knoop punt zich in de status bevindt die is opgegeven in het configuratie document.

**ResourcesInDesiredState** \[ out \] on return bevat een Inge sloten exemplaar van de klasse **MSFT_ResourceInDesiredState** die resources opgeeft die de gewenste status hebben.

**ResourcesNotInDesiredState** \[ out \] on return bevat een Inge sloten exemplaar van de **MSFT_ResourceNotInDesiredState** -klasse waarmee resources worden opgegeven die niet de gewenste status hebben.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
