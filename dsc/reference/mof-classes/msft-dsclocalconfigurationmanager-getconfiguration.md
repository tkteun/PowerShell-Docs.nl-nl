---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetConfiguration-methode
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734520"
---
# <a name="getconfiguration-method"></a>De GetConfiguration-methode

Het configuratiebestand voor verzendt naar de beheerd knooppunt en maakt gebruik van de **ophalen** methode van de Agent configureren om toe te passen van de configuratie.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a>Parameters

*configurationData* \[in\] Hiermee geeft u de configuratiegegevens te verzenden.

*configuraties* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de configuraties.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
