---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetConfiguration-methode
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942711"
---
# <a name="getconfiguration-method"></a>GetConfiguration-methode

Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de **Get** -methode van de configuratie agent gebruikt om de configuratie toe te passen.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a>Parameters

*configurationData* \[in @ no__t-2 geeft aan welke configuratie gegevens moeten worden verzonden.

*configuraties* \[out @ no__t-2 bij Return, bevat een Inge sloten instantie van de configuraties.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MANAGE** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
