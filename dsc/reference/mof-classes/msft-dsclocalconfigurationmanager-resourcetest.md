---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ResourceTest-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048293"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>De ResourceTest-methode van de klasse MSFT_DSCLocalConfigurationManager

Rechtstreeks roept de **Test** methode van een DSC-resource.

## <a name="syntax"></a>Syntaxis

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Parameters

*ResourceType* \[in\] de naam van de resource om aan te roepen.

*ModuleName* \[in\] de naam van de module met de resource om aan te roepen.

*resourceProperty* \[in\] Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hash-tabel als de sleutel en waarde, respectievelijk. Gebruik de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet voor het detecteren van resource-eigenschappen en het bijhorende type.

*InDesiredState* \[uit\] bij resultaat, deze eigenschap is ingesteld op **waar** als het doelknooppunt in de gewenste status.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)