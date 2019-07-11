---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetMetaConfiguration-methode
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734443"
---
# <a name="getmetaconfiguration-method"></a>De GetMetaConfiguration-methode

De lokale Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie van Agent worden opgehaald.

## <a name="syntax"></a>Syntaxis

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a>Parameters

*MetaConfiguration* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de **MSFT_DSCMetaConfiguration** klasse waarin de instellingen worden gedefinieerd.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
