---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfiguration-methode
description: GetConfiguration-methode
ms.openlocfilehash: a49f810bd227142c8c3ae4de45f69450400e4e8c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650877"
---
# <a name="getconfiguration-method"></a>GetConfiguration-methode

Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de **Get** -methode van de configuratie agent gebruikt om de configuratie toe te passen.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a>Parameters

**configurationData** \[ in \] geeft de configuratie gegevens op die moeten worden verzonden.

**configuraties** \[ out \] on return bevat een Inge sloten exemplaar van de configuraties.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
