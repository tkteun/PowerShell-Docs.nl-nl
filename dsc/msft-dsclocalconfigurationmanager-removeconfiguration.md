---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

Hiermee verwijdert u de configuratiebestanden.

<a name="syntax"></a>Syntaxis
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a>Parameters
----------

*Fase* \[in\]  
Hiermee geeft u op welke configuratie-document te verwijderen. De volgende waarden zijn geldig:

|Value |Beschrijving |
|:--- |:---|
|**1** | De **huidige** configuratie document (current.mof). |
|**2** | De **in behandeling** configuratie document (pending.mof).  |
|**4** | De **vorige** configuratie document (previous.mof). |

*Force* \[in\]  
**de waarde True** om af te dwingen van het verwijderen van de configuratie.

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


 

 



