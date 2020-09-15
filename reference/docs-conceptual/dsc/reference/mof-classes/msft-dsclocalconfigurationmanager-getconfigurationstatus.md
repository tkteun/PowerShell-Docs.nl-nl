---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: GetConfigurationStatus-methode
ms.openlocfilehash: c2c478151428052d656832fb4079f12d666a910d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464044"
---
# <a name="getconfigurationstatus-method"></a>GetConfigurationStatus-methode

De geschiedenis van de configuratie status ophalen.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
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

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
