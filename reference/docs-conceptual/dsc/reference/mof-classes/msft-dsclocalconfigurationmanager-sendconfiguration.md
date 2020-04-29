---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: SendConfiguration-methode
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941549"
---
# <a name="sendconfiguration-method"></a>SendConfiguration-methode

Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en opgeslagen als een wijziging in behandeling.

## <a name="syntax"></a>Syntaxis

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Parameters

*ConfigurationData* \[in\] de omgevings gegevens voor de configuratie.

*geforceerd* \[in\] op **waar** om te zorgen dat de configuratie wordt gestopt.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
