---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c68d17d38336dec08e078366ea5f2071fcf7c5a8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189734"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>De RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

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

*Fase* \[in\] geeft aan welke configuratie-document te verwijderen. De volgende waarden zijn geldig:

|Value |Beschrijving |
|:--- |:---|
|**1** | De **huidige** configuratie document (current.mof). |
|**2** | De **in behandeling** configuratie document (pending.mof).  |
|**4** | De **vorige** configuratie document (previous.mof). |

*Force* \[in\] **true** om af te dwingen van het verwijderen van de configuratie.

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