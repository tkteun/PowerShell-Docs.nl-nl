---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: PerformRequiredConfigurationChecks-methode
ms.openlocfilehash: ea4294ffdcb2580fa7b39b18966b642d58073eb6
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464448"
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

**Vlaggen** \[ in \] een bitmasker waarmee wordt aangegeven welk type consistentie controle moet worden uitgevoerd. De volgende waarden zijn geldig en kunnen worden gecombineerd met behulp van een bitsgewijze **or** -bewerking:

|Waarde |Beschrijving |
|:--- |:---|
|**1** | Een normale consistentie controle. |
|**2** | Een voortzetting van een consistentie controle na het opnieuw opstarten. Deze waarde mag niet worden gecombineerd met andere waarden. |
|**4** | De configuratie moet worden opgehaald van de pull-server die is opgegeven in de-configuratie voor het knoop punt. Deze waarde moet altijd worden gecombineerd met **1**, voor een waarde van **5**. |
|**8** | Status verzenden naar de rapport server. |

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
