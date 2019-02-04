---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC WindowsOptionalFeatureSet-Resource
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683945"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC WindowsOptionalFeatureSet-Resource

> Van toepassing op: Windows PowerShell 5.0

De **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat de optionele functies zijn ingeschakeld op een doelknooppunt.
Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die roept de [WindowsOptionalFeature-resource](windowsOptionalFeatureResource.md) voor elke functie die is opgegeven in de `Name` eigenschap.

Gebruik deze resource als u wilt configureren van een aantal optionele functies van Windows naar dezelfde toestand.

## <a name="syntax"></a>Syntaxis

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| Naam| Geeft aan dat de naam van de functies die u wilt ervoor zorgen zijn ingeschakeld of uitgeschakeld.|
| Zorg ervoor dat| Hiermee geeft u op of de functies zijn ingeschakeld. Om ervoor te zorgen dat de functies zijn ingeschakeld en stel deze eigenschap in op 'Inschakelen' om ervoor te zorgen dat de functies zijn uitgeschakeld, de eigenschap instellen op 'Uitschakelen'.|
| Bron| Niet geïmplementeerd.|
| NoWindowsUpdateCheck| Hiermee geeft u op of DISM neemt contact op met Windows Update (WU) bij het zoeken naar de bronbestanden voor de functies inschakelen. Als $true, DISM geen contact opnemen met WU.|
| RemoveFilesOnDisable| Ingesteld op **$true** te verwijderen van alle bestanden die zijn gekoppeld aan de functies wanneer ze worden uitgeschakeld (dat wil zeggen, wanneer **Zorg ervoor dat** is ingesteld op 'Ontbreekt').|
| Logniveau| Het maximale uitvoerniveau op dat wordt weergegeven in de logboeken. De toegestane waarden zijn: "ErrorsOnly' (alleen fouten worden vastgelegd), 'ErrorsAndWarning' (fouten en waarschuwingen worden geregistreerd), en 'ErrorsAndWarningAndInformation' (fouten, waarschuwingen en gegevens voor foutopsporing worden geregistreerd).|
| Logboekpad| Het pad naar een logboekbestand waar u de resourceprovider voor aanmelding van de bewerking.|
| DependsOn| Hiermee geeft u op dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|
