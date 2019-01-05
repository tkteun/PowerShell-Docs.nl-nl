---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De PerformRequiredConfigurationChecks-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048340"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>De PerformRequiredConfigurationChecks-methode van de klasse MSFT_DSCLocalConfigurationManager

Een consistentiecontrole starten met behulp van de Taakplanner.

## <a name="syntax"></a>Syntaxis

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Parameters

*Vlaggen* \[in\] een bitmasker waarmee het type van een consistentiecontrole uit te voeren. De volgende waarden geldig zijn en kunnen worden gecombineerd met behulp van een bitwise **of** bewerking:

|Waarde |Beschrijving |
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