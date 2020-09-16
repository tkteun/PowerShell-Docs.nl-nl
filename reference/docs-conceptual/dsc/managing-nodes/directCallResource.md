---
ms.date: 08/11/2020
keywords: DSC, Power shell, configuratie, installatie
title: Methoden voor het rechtstreeks aanroepen van DSC-resources
ms.openlocfilehash: 029a278c938e414820e172b85fac3cb3ad4b4afa
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162491"
---
# <a name="calling-dsc-resource-methods-directly"></a>Methoden voor het rechtstreeks aanroepen van DSC-resources

>Van toepassing op: Windows Power shell 5,0

U kunt de cmdlet [invoke-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) gebruiken om de functies of methoden van een DSC-resource rechtstreeks aan te roepen (de `Get-TargetResource` `Set-TargetResource` functies,, en `Test-TargetResource` van een op MOF gebaseerde resource, of de methoden **Get**, **set**en **test** van een bron op basis van een klasse). Dit kan worden gebruikt door derden die DSC-resources willen gebruiken of als handig hulp middel bij het ontwikkelen van resources.

> [!NOTE]
> In Power shell 7.0 + `Invoke-DscResource` biedt geen ondersteuning meer voor het aanroepen van WMI DSC-resources. Dit omvat de **Bestands** -en **logboek** bronnen in **PSDesiredStateConfiguration**.

Deze cmdlet wordt doorgaans gebruikt in combi natie met een eigenschap `refreshMode = 'Disabled'` **refreshMode** , maar kan ook worden gebruikt, ongeacht de waarde die is ingesteld op.

Wanneer u de `Invoke-DscResource` cmdlet aanroept, geeft u op welke methode of functie u wilt aanroepen met behulp van de **methode** parameter. U geeft de eigenschappen van de resource op door een hashtabel door te geven als de waarde van de **eigenschaps** parameter.

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

>[!NOTE]
> Het rechtstreeks aanroepen van samengestelde resource methoden wordt niet ondersteund. In plaats daarvan roept u de methoden van de onderliggende resources aan waaruit de samengestelde resource is samengesteld.

## <a name="see-also"></a>Zie ook

- [Een aangepaste DSC-resource schrijven met MOF](../resources/authoringResourceMOF.md)
- [Een aangepaste DSC-resource schrijven met Power shell-klassen](../resources/authoringResourceClass.md)
- [Foutopsporing voor DSC-resources](../troubleshooting/debugResource.md)
