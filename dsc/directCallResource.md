---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Methoden voor het rechtstreeks aanroepen van DSC-resources
ms.openlocfilehash: 3ec3a3a8da615f45f3fdd28b1c1e46e312507ed5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="calling-dsc-resource-methods-directly"></a>Methoden voor het rechtstreeks aanroepen van DSC-resources

>Van toepassing op: Windows PowerShell 5.0

U kunt de [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) cmdlet rechtstreeks aanroepen van de functies of methoden van een DSC-resource (de **Get-TargetResource**, **Set TargetResource**, en  **Test-TargetResource** functies van een bron op basis van MOF of de **ophalen**, **ingesteld**, en **Test** methoden van een bron op basis van een klasse).
Dit kan worden gebruikt door derden die DSC-resources wilt gebruiken of als een nuttig hulpmiddel bij het ontwikkelen van resources.

Deze cmdlet wordt doorgaans gebruikt in combinatie met een eigenschap metaconfiguratie `refreshMode = 'Disabled'`, maar deze kan worden gebruikt, wat er ook **refreshMode** is ingesteld op.

Bij het aanroepen van de **Invoke-DscResource** cmdlet u opgeven welke methode of functie aan te roepen met behulp van de **methode** parameter. U de eigenschappen van de resource opgeven door een hashtabel wordt doorgegeven als de waarde van de **eigenschap** parameter.

Hier volgen enkele voorbeelden van methoden van de resource direct aan te roepen:

## <a name="ensure-a-file-is-present"></a>Zorg ervoor dat een bestand aanwezig is

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Testen of een bestand aanwezig is

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

>**Opmerking:** rechtstreeks aanroepen van methoden van de samengestelde bron wordt niet ondersteund. Roep in plaats daarvan de methoden van de onderliggende resources die gezamenlijk de samengestelde bron.

## <a name="see-also"></a>Zie ook
- [Schrijven van een aangepaste DSC-resource met MOF](authoringResourceMOF.md)
- [Schrijven van een aangepaste DSC-resource met PowerShell-klassen](authoringResourceClass.md)
- [Foutopsporing voor DSC-resources](debugResource.md)