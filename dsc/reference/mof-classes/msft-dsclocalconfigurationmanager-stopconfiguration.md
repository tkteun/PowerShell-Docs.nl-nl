---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048174"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>De StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

Hiermee stopt u de wijziging in de configuratie die wordt uitgevoerd.

## <a name="syntax"></a>Syntaxis

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parameters

*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)