---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: acd8f380f1c49eb008563398c2c3de3fce5477f9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186674"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a>De SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager

Het configuratiebestand voor asynchroon verzendt naar het beheerde knooppunt en gebruik van de configuratie-Agent voor de configuratie.

<a name="syntax"></a>Syntaxis
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a>Parameters
----------

*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.

*Force* \[in\] **true** om af te dwingen van de configuratie te stoppen.

*jobId* \[in\] de ID van de taak voor voor het verzenden van de configuratie.

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