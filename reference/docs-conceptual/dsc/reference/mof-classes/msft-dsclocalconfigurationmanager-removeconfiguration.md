---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: RemoveConfiguration-methode
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941556"
---
# <a name="removeconfiguration-method"></a>RemoveConfiguration-methode

Hiermee verwijdert u de configuratie bestanden.

## <a name="syntax"></a>Syntaxis

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>Parameters

*Fase* \[in @ no__t-2 geeft aan welk configuratie document moet worden verwijderd. De volgende waarden zijn geldig:

|Value |Description |
|:--- |:---|
|**1** | Het **huidige** configuratie document (huidige. MOF). |
|**2** | Het **in behandeling zijnde** configuratie document (in behandeling. MOF).  |
|**4** | Het **vorige** configuratie document (vorige. MOF). |

*Force* \[in @ no__t-2 **True** om het verwijderen van de configuratie af te dwingen.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MANAGE** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
