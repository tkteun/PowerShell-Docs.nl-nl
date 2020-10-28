---
ms.date: 07/14/2020
ms.topic: reference
title: ApplyConfiguration-methode
description: ApplyConfiguration-methode
ms.openlocfilehash: aa99221b33d39c3ecc70156a11eaee10b540e2dc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664274"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration-methode

Maakt gebruik van de configuratie agent om de in behandeling zijnde configuratie toe te passen.

Als er geen configuratie in behandeling is, past deze methode de huidige configuratie opnieuw toe.

## <a name="syntax"></a>Syntaxis

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parameters

### <a name="force"></a>verkopers

Als dit het **geval** is, wordt de huidige configuratie opnieuw toegepast, zelfs als er een configuratie in behandeling is.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
