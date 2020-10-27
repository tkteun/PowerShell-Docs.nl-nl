---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfigurationStatus-methode
description: GetConfigurationStatus-methode
ms.openlocfilehash: fe25d17069d9011e931ac50fec27cb9ebafba365
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650858"
---
# <a name="getconfigurationstatus-method"></a>GetConfigurationStatus-methode

De geschiedenis van de configuratie status ophalen.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a>Parameters

**Alle** \[ in \] **True** als deze methode informatie moet retour neren over alle configuratie runs op de computer, met inbegrip van de configuratie toepassing en de consistentie controle.

**configurationStatus** \[ out \] on return bevat een Inge sloten exemplaar van de klasse **MSFT_DSCConfigurationStatus** die de instellingen definieert.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
