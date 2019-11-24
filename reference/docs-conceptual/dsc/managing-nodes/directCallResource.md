---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Methoden voor het rechtstreeks aanroepen van DSC-resources
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942249"
---
# <a name="calling-dsc-resource-methods-directly"></a>Methoden voor het rechtstreeks aanroepen van DSC-resources

>Van toepassing op: Windows Power shell 5,0

U kunt de cmdlet [invoke-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) gebruiken om de functies of methoden van een DSC-resource rechtstreeks aan te roepen (de functies **Get-TargetResource**, **set-TargetResource**en **test-TargetResource** van een op een MOF gebaseerde resource, of de methoden **Get**, **set**en **test** van een op een klasse gebaseerde bron).
Dit kan worden gebruikt door derden die DSC-resources willen gebruiken of als handig hulp middel bij het ontwikkelen van resources.

Deze cmdlet wordt doorgaans gebruikt in combi natie met een `refreshMode = 'Disabled'`eigenschap voor de **refreshMode** , maar kan worden gebruikt, ongeacht de waarde die is ingesteld op.

Wanneer u de cmdlet **invoke-dscresource bieden** aanroept, geeft u op welke methode of functie u wilt aanroepen met behulp van de **methode** parameter. U geeft de eigenschappen van de resource op door een hashtabel door te geven als de waarde van de **eigenschaps** parameter.

Hier volgen enkele voor beelden van het rechtstreeks aanroepen van resource methoden:

## <a name="ensure-a-file-is-present"></a>Controleren of een bestand aanwezig is

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

## <a name="get-the-contents-of-file"></a>De inhoud van het bestand ophalen

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Opmerking:** Het rechtstreeks aanroepen van samengestelde resource methoden wordt niet ondersteund. In plaats daarvan roept u de methoden van de onderliggende resources aan waaruit de samengestelde resource is samengesteld.

## <a name="see-also"></a>Zie ook
- [Een aangepaste DSC-resource schrijven met MOF](../resources/authoringResourceMOF.md)
- [Een aangepaste DSC-resource schrijven met Power shell-klassen](../resources/authoringResourceClass.md)
- [Foutopsporing voor DSC-resources](../troubleshooting/debugResource.md)