---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048261"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>De EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager

U kunt foutopsporing van DSC-resource.

## <a name="syntax"></a>Syntaxis

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a>Parameters

*BreakAll* \[in\] een onderbrekingspunt instellen op elke regel in het resource-script.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)