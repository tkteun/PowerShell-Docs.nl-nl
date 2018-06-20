---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b4d4c901268344ba67d77e4dc982042bfc2abd78
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222204"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

Het configuratiebestand voor verzendt naar het beheerde knooppunt en wordt deze opgeslagen als een wijziging in behandeling.

<a name="syntax"></a>Syntaxis
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a>Parameters
----------

*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.

*Force* \[in\] **true** om af te dwingen van de configuratie te stoppen.

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