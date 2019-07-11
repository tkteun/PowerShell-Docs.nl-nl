---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De RemoveConfiguration-methode
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734384"
---
# <a name="removeconfiguration-method"></a>De RemoveConfiguration-methode

Hiermee verwijdert u de configuratiebestanden.

## <a name="syntax"></a>Syntaxis

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>Parameters

*Fase* \[in\] geeft aan welke configuratiedocument te verwijderen. De volgende waarden zijn geldig:

|Waarde |Description |
|:--- |:---|
|**1** | De **huidige** configuratiedocument (current.mof). |
|**2** | De **in behandeling** configuratiedocument (pending.mof).  |
|**4** | De **vorige** configuratiedocument (previous.mof). |

*Afdwingen dat* \[in\] **waar** om af te dwingen van het verwijderen van de configuratie.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
