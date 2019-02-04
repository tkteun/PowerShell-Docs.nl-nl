---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683903"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>De RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

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

|Waarde |Beschrijving |
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