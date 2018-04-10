---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De PerformRequiredConfigurationChecks-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9cc4384088fcc39b09979b8ae4d023fc46307b13
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>De PerformRequiredConfigurationChecks-methode van de klasse MSFT_DSCLocalConfigurationManager

Een consistentiecontrole begint met het gebruik van Taakplanner.

<a name="syntax"></a>Syntaxis
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a>Parameters
----------

*Vlaggen* \[in\] een bitmasker waarmee het type van een consistentiecontrole uit te voeren. De volgende waarden geldig zijn en kunnen worden gecombineerd met behulp van een bitwise **of** bewerking:

|Value |Beschrijving |
|:--- |:---|
|**1** | Een normale consistentiecontrole. |
|**2** | Een vervolg van een consistentiecontrole uit na het opnieuw opstarten. Deze waarde moet niet worden gecombineerd met andere waarden. |
|**4** | De configuratie moet worden opgehaald uit de pull-server die is opgegeven in de metaconfiguratie voor het knooppunt. Deze waarde moet altijd worden gecombineerd met **1**, voor een waarde van **5**. |
|**8** | Status verzenden naar de rapportserver. |

## <a name="return-value"></a>Retourwaarde
------------

Retourneert nul geslaagd; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Zie ook


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)