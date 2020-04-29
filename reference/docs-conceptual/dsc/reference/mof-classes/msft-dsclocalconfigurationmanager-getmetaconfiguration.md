---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetMetaConfiguration-methode
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941563"
---
# <a name="getmetaconfiguration-method"></a>GetMetaConfiguration-methode

Hiermee haalt u de lokale Configuration Manager-instellingen op die worden gebruikt voor het beheren van de configuratie agent.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a>Parameters

*MetaConfiguration* \[De meta-\] configuratie out voor Return bevat een Inge sloten instantie van de klasse **MSFT_DSCMetaConfiguration** die de instellingen definieert.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
