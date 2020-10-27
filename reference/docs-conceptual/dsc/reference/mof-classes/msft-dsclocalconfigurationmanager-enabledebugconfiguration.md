---
ms.date: 07/17/2020
ms.topic: reference
title: EnableDebugConfiguration-methode
description: EnableDebugConfiguration-methode
ms.openlocfilehash: 536366e6e1627a249f3bc2dc19bfd8ff3de42117
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644771"
---
# <a name="enabledebugconfiguration-method"></a>EnableDebugConfiguration-methode

Hiermee schakelt u fout opsporing voor DSC-resources in.

## <a name="syntax"></a>Syntaxis

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a>Parameters

**BreakAll** \[ in \] stelt een onderbrekings punt in op elke regel in het bron script.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
