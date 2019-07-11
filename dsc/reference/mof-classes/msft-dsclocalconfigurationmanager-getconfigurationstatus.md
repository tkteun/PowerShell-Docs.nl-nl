---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetConfigurationStatus-methode
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734510"
---
# <a name="getconfigurationstatus-method"></a>De GetConfigurationStatus-methode

De geschiedenis van de configuratie-status ophalen.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a>Parameters

*Alle* \[in\] **waar** als deze methode informatie over de configuratie op de machine wordt uitgevoerd retourneren moet, met inbegrip van de configuratie van toepassing en de consistentiecontrole.

*configurationStatus* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de **MSFT_DSCConfigurationStatus** klasse waarin de instellingen worden gedefinieerd.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
