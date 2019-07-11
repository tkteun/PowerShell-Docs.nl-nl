---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendMetaConfigurationApply-methode
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727039"
---
# <a name="sendmetaconfigurationapply-method"></a>De SendMetaConfigurationApply-methode

Hiermee stelt de Local Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie van Agent.

## <a name="syntax"></a>Syntaxis

```mof
uint32 SendMetaConfigurationApply(
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
