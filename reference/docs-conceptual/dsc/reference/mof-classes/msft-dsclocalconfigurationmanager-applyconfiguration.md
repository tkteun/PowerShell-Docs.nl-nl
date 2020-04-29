---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: ApplyConfiguration-methode
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941598"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration-methode

Maakt gebruik van de configuratie agent om de in behandeling zijnde configuratie toe te passen.

Als er geen configuratie in behandeling is, past deze methode de huidige configuratie opnieuw toe.

## <a name="syntax"></a>Syntaxis

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parameters

*Force* \[in\] als dit **waar**is, wordt de huidige configuratie opnieuw toegepast, zelfs als er een configuratie in behandeling is.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
