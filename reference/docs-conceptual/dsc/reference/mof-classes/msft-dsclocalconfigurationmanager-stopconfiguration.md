---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: StopConfiguration-methode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941528"
---
# <a name="stopconfiguration-method"></a>StopConfiguration-methode

Hiermee stopt u de configuratie wijziging die wordt uitgevoerd.

## <a name="syntax"></a>Syntaxis

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parameters

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
