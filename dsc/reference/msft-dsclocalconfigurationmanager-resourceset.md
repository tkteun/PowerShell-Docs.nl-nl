---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404321"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a>De ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager

Rechtstreeks roept de **ingesteld** methode van een DSC-resource.

## <a name="syntax"></a>Syntaxis

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a>Parameters

*ResourceType* \[in\] de naam van de resource om aan te roepen.

*ModuleName* \[in\] de naam van de module met de resource om aan te roepen.

*resourceProperty* \[in\] Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hash-tabel als de sleutel en waarde, respectievelijk. Gebruik de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet voor het detecteren van resource-eigenschappen en het bijhorende type.

*RebootRequired* \[uit\] bij resultaat, deze eigenschap is ingesteld op **waar** als het doelknooppunt moet opnieuw worden opgestart.

## <a name="return-value"></a>Retourwaarde

Retourneert nul op succes; Anders retourneert een foutcode.

## <a name="remarks"></a>Opmerkingen

Dit is een statische methode.

## <a name="requirements"></a>Vereisten

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Zie ook

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)