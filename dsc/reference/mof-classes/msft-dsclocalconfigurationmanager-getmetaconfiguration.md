---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685996"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>De GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

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