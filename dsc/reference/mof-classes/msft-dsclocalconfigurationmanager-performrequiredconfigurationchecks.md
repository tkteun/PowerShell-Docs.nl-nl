---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De PerformRequiredConfigurationChecks-methode
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734403"
---
# <a name="performrequiredconfigurationchecks-method"></a>De PerformRequiredConfigurationChecks-methode

Een consistentiecontrole starten met behulp van de Taakplanner.

## <a name="syntax"></a>Syntaxis

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Parameters

*Vlaggen* \[in\] een bitmasker waarmee het type van een consistentiecontrole uit te voeren. De volgende waarden geldig zijn en kunnen worden gecombineerd met behulp van een bitwise **of** bewerking:

|Waarde |Description |
|:--- |:---|
|**1** | Een normale consistentiecontrole uit. |
|**2** | Een voortzetting van een consistentiecontrole uit na het opnieuw opstarten. Deze waarde moet niet worden gecombineerd met andere waarden. |
|**4** | De configuratie moet worden opgehaald uit de pull-server die is opgegeven in de metaconfiguration voor het knooppunt. Deze waarde moet altijd worden gecombineerd met **1**, voor een waarde van **5**. |
|**8** | De status verzenden naar de rapportserver. |

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
