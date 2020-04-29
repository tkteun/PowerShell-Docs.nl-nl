---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: PerformRequiredConfigurationChecks-methode
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942683"
---
# <a name="performrequiredconfigurationchecks-method"></a>PerformRequiredConfigurationChecks-methode

Start een consistentie controle met behulp van de taak planner.

## <a name="syntax"></a>Syntaxis

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Parameters

*Vlaggen* \[in\] een bitmasker die het type consistentie controle opgeeft dat moet worden uitgevoerd. De volgende waarden zijn geldig en kunnen worden gecombineerd met behulp van een bitsgewijze **or** -bewerking:

|Waarde |Beschrijving |
|:--- |:---|
|**1** | Een normale consistentie controle. |
|**2** | Een voortzetting van een consistentie controle na het opnieuw opstarten. Deze waarde mag niet worden gecombineerd met andere waarden. |
|**4** | De configuratie moet worden opgehaald van de pull-server die is opgegeven in de-configuratie voor het knoop punt. Deze waarde moet altijd worden gecombineerd met **1**, voor een waarde van **5**. |
|**achtste** | Status verzenden naar de rapport server. |

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
