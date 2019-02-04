---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683938"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

Het configuratiebestand voor verzendt naar de beheerd knooppunt en wordt deze opgeslagen als een wijziging in behandeling.

## <a name="syntax"></a>Syntaxis

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Parameters

*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.

*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)