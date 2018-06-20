---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 46eec896df643996bea5f2c371a9294034caae6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218413"
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>De GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

Verzendt het configuratie-document naar het beheerde knooppunt en maakt gebruik van de **ophalen** methode van de configuratie-Agent de configuratie toepassen.

<a name="syntax"></a>Syntaxis
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a>Parameters
----------

*configurationData* \[in\] Hiermee geeft u de configuratiegegevens te verzenden.

*configuraties* \[uit\] op return bevat een ingesloten exemplaar van de configuraties.

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