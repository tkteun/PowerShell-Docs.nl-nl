---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: SendConfigurationApplyAsync-methode
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941542"
---
# <a name="sendconfigurationapplyasync-method"></a>SendConfigurationApplyAsync-methode

Hiermee wordt het configuratie document asynchroon verzonden naar het beheerde knoop punt en wordt de configuratie agent gebruikt om de configuratie toe te passen.

## <a name="syntax"></a>Syntaxis

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>Parameters

*ConfigurationData* \[in\] de omgevings gegevens voor de configuratie.

*geforceerd* \[in\] op **waar** om te zorgen dat de configuratie wordt gestopt.

*jobId* \[in\] de id van de taak waarvoor de configuratie moet worden verzonden.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
