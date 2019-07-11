---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfiguration-methode
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734319"
---
# <a name="sendconfiguration-method"></a>De SendConfiguration-methode

Het configuratiebestand voor verzendt naar de beheerd knooppunt en wordt deze opgeslagen als een wijziging in behandeling.

## <a name="syntax"></a>Syntaxis

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Parameters

*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.

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
