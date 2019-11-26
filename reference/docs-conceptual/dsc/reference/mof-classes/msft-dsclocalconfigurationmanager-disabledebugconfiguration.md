---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: DisableDebugConfiguration-methode
ms.openlocfilehash: e3eab98c734b3fd1593ceb2b5d4b40fa69a3bf97
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942718"
---
# <a name="disabledebugconfiguration-method"></a>DisableDebugConfiguration-methode

Hiermee schakelt u fout opsporing voor DSC-resources uit.

## <a name="syntax"></a>Syntaxis

```mof
uint32 DisableDebugConfiguration();
```

## <a name="parameters"></a>Parameters

Deze methode heeft geen para meters.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MANAGE** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)