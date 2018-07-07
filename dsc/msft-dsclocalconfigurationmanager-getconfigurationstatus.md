---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetConfigurationStatus-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893056"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>De GetConfigurationStatus-methode van de klasse MSFT_DSCLocalConfigurationManager

De geschiedenis van de configuratie-status ophalen.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a>Parameters

*Alle* \[in\] **waar** als deze methode informatie over de configuratie op de machine wordt uitgevoerd retourneren moet, met inbegrip van de configuratie van toepassing en de consistentiecontrole.

*configurationStatus* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de **MSFT_DSCConfigurationStatus** klasse waarin de instellingen worden gedefinieerd.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)