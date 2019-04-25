---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Methoden voor het rechtstreeks aanroepen van DSC-resources
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079622"
---
# <a name="calling-dsc-resource-methods-directly"></a>Methoden voor het rechtstreeks aanroepen van DSC-resources

>Van toepassing op: Windows PowerShell 5.0

U kunt de [sleutelwoorden Invoke-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet voor het rechtstreeks aanroepen van de functies of methoden van een DSC-resource (de **Get-TargetResource**, **Set TargetResource**, en  **Test-TargetResource** functies van een resource op basis van MOF of de **ophalen**, **ingesteld**, en **Test** methoden van een resource op basis van een klasse).
Dit kan worden gebruikt door derden die DSC-resources wilt gebruiken, of als een handig hulpmiddel tijdens het ontwikkelen van resources.

Deze cmdlet wordt doorgaans gebruikt in combinatie met een eigenschap metaconfiguration `refreshMode = 'Disabled'`, maar deze kan worden gebruikt, ongeacht wat **refreshMode** is ingesteld op.

Bij het aanroepen van de **sleutelwoorden Invoke-dscresource bieden** cmdlet, u opgeven welke methode of functie aan te roepen met behulp van de **methode** parameter. U de eigenschappen van de resource opgeven door een hash-tabel als de waarde van de **eigenschap** parameter.

Hier volgen enkele voorbeelden van het rechtstreeks aanroepen van resourcemethoden:

## <a name="ensure-a-file-is-present"></a>Zorg ervoor dat een bestand aanwezig is

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Test of een bestand aanwezig is

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>De inhoud van bestand ophalen

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Opmerking:** Samengestelde resourcemethoden direct aan te roepen wordt niet ondersteund. In plaats daarvan de methoden van de onderliggende resources die gezamenlijk de samengestelde resource aanroept.

## <a name="see-also"></a>Zie ook
- [Een aangepaste DSC-resource met MOF schrijven](../resources/authoringResourceMOF.md)
- [Schrijven van een aangepaste DSC-resource met de PowerShell-klassen](../resources/authoringResourceClass.md)
- [Foutopsporing voor DSC-resources](../troubleshooting/debugResource.md)