---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: PerformRequiredConfigurationChecks-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 687c92f2dac5e8855731713e81390ac67615231e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>PerformRequiredConfigurationChecks-methode van de klasse MSFT_DSCLocalConfigurationManager

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

*Vlaggen* \[in\]  
Een bitmasker waarmee het type van een consistentiecontrole uit te voeren. De volgende waarden geldig zijn en kunnen worden gecombineerd met behulp van een bitwise **of** bewerking:

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


 

 



