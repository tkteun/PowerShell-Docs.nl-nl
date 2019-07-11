---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ApplyConfiguration-methode
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727176"
---
# <a name="applyconfiguration-method"></a>De ApplyConfiguration-methode

Gebruik de configuratie van Agent voor de configuratie die in behandeling is.

Als er geen configuratie in behandeling is, wordt deze methode de huidige configuratie opnieuw toegepast.

## <a name="syntax"></a>Syntaxis

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parameters

*afdwingen dat* \[in\] als dit **waar**, de huidige configuratie is toegepast, zelfs als er een configuratie in behandeling.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
