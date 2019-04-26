---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-WindowsOptionalFeature-Resource
ms.openlocfilehash: 390caefd2ad190afc651b22ed1beb5cf1d604527
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076751"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>DSC-WindowsOptionalFeature-Resource

> Van toepassing op: Windows PowerShell 5.0

De **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat de optionele functies zijn ingeschakeld op een doelknooppunt.

## <a name="syntax"></a>Syntaxis

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Description   |
|---|---|
| Naam| Geeft aan dat de naam van de functie die u wilt ervoor zorgen is ingeschakeld of uitgeschakeld.|
| Zorg ervoor dat| Hiermee geeft u op of de functie is ingeschakeld. Om ervoor te zorgen dat de functie is ingeschakeld, stel deze eigenschap in op 'Inschakelen' om ervoor te zorgen dat de functie is uitgeschakeld, de eigenschap instellen op 'Uitschakelen'.|
| Bron| Niet geïmplementeerd.|
| NoWindowsUpdateCheck| Hiermee geeft u op of DISM neemt contact op met Windows Update (WU) bij het zoeken naar de bronbestanden bevat een functie in te schakelen. Als $true, DISM geen contact opnemen met WU.|
| RemoveFilesOnDisable| Ingesteld op **$true** te verwijderen van alle bestanden die zijn gekoppeld aan de functie wanneer deze is uitgeschakeld (dat wil zeggen, wanneer **Zorg ervoor dat** is ingesteld op 'Ontbreekt').|
| Logniveau| Het maximale uitvoerniveau op dat wordt weergegeven in de logboeken. De toegestane waarden zijn: "ErrorsOnly' (alleen fouten worden vastgelegd), 'ErrorsAndWarning' (fouten en waarschuwingen worden geregistreerd), en 'ErrorsAndWarningAndInformation' (fouten, waarschuwingen en gegevens voor foutopsporing worden geregistreerd).|
| Logboekpad| Het pad naar een logboekbestand waar u de resourceprovider voor aanmelding van de bewerking.|
| DependsOn| Hiermee geeft u op dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|