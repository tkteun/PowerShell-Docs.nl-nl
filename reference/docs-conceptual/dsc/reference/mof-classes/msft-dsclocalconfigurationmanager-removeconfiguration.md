---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: RemoveConfiguration-methode
ms.openlocfilehash: ef15c873d8dfaf28e5cdeb611b72a70921c099be
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464346"
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

**Fase** \[ in \] geeft aan welk configuratie document moet worden verwijderd. De volgende waarden zijn geldig:

|Waarde |Beschrijving |
|:--- |:---|
|**1** | Het **huidige** configuratie document (huidige. MOF). |
|**2** | Het **in behandeling zijnde** configuratie document (in behandeling. MOF).  |
|**4** | Het **vorige** configuratie document (vorige. MOF). |

*Forceren* \[ in \] **True** om het verwijderen van de configuratie af te dwingen.

## <a name="return-value"></a>Retourwaarde

Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore. MOF

**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
