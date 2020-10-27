---
ms.date: 07/17/2020
ms.topic: reference
title: GetMetaConfiguration-methode
description: GetMetaConfiguration-methode
ms.openlocfilehash: deca6b8ec342a34543bbe0e1fabbc2a740a88feb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644725"
---
# <a name="getmetaconfiguration-method"></a>GetMetaConfiguration-methode

Hiermee haalt u de lokale Configuration Manager-instellingen op die worden gebruikt voor het beheren van de configuratie agent.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a>Parameters

- **Configuratie** \[ out \] on return bevat een Inge sloten exemplaar van de klasse **MSFT_DSCMetaConfiguration** die de instellingen definieert.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
