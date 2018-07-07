---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ApplyConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892604"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>De ApplyConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

Gebruik de configuratie van Agent voor de configuratie die in behandeling is.

Als er geen configuratie in behandeling is, wordt deze methode de huidige configuratie opnieuw toegepast.

## <a name="syntax"></a>Syntaxis

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parameters

*afdwingen dat* \[in\] als dit **waar**, de huidige configuratie is toegepast, zelfs als er een configuratie in behandeling.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)