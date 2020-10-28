---
ms.date: 07/17/2020
ms.topic: reference
title: SendMetaConfigurationApply-methode
description: SendMetaConfigurationApply-methode
ms.openlocfilehash: 27c58819c0249ace011c475e500e565e5daed9bb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648962"
---
# <a name="sendmetaconfigurationapply-method"></a>SendMetaConfigurationApply-methode

Hiermee stelt u de lokale Configuration Manager-instellingen in die worden gebruikt voor het beheren van de configuratie agent.

## <a name="syntax"></a>Syntaxis

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Parameters

**ConfigurationData** \[ in \] de omgevings gegevens voor de configuratie.

**forceren** \[ in \] **True** om te zorgen dat de configuratie wordt gestopt.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
