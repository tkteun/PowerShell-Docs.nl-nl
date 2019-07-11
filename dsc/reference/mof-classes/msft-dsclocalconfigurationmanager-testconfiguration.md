---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De TestConfiguration-methode
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726957"
---
# <a name="testconfiguration-method"></a>De TestConfiguration-methode

Het configuratiebestand voor verzendt naar de beheerd knooppunt en controleert of de huidige configuratie op basis van het document.

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

*configurationData* \[in\] omgevingsgegevens voor de confuguration.

*InDesiredState* \[uit\] bij resultaat, geeft aan of de beheerde knooppunt in de status die is opgegeven door het configuratiebestand.

*ResourcesInDesiredState* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de **MSFT_ResourceInDesiredState** klasse waarmee bronnen die zich in de gewenste status.

*ResourcesNotInDesiredState* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de **MSFT_ResourceNotInDesiredState** klasse die Hiermee geeft u de resources die zich niet in de gewenste status.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
