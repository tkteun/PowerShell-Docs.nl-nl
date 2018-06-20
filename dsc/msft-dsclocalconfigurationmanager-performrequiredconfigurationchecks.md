---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De PerformRequiredConfigurationChecks-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c3fdaa23875815b1cf5cbf0b6e21c633e00664aa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186691"
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