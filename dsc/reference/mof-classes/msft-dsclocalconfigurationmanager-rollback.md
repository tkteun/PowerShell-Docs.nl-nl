---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De RollBack-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048305"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>De RollBack-methode van de klasse MSFT_DSCLocalConfigurationManager

De configuratie teruggedraaid naar een eerdere versie.

## <a name="syntax"></a>Syntaxis

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a>Parameters

*configurationNumber* \[in\] Hiermee geeft u de aangevraagde configuratie.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)