---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfigurationApplyAsync-methode
description: SendConfigurationApplyAsync-methode
ms.openlocfilehash: 92c9d03a7653e72b1ff04084caea4a8b5aadb0e5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644792"
---
# <a name="sendconfigurationapplyasync-method"></a>SendConfigurationApplyAsync-methode

Hiermee wordt het configuratie document asynchroon verzonden naar het beheerde knoop punt en wordt de configuratie agent gebruikt om de configuratie toe te passen.

## <a name="syntax"></a>Syntaxis

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>Parameters

**ConfigurationData** \[ in \] de omgevings gegevens voor de configuratie.

**forceren** \[ in \] **True** om te zorgen dat de configuratie wordt gestopt.

**jobId** \[ in \] de id van de taak waarvoor de configuratie moet worden verzonden.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
