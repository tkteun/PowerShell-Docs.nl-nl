---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-WindowsOptionalFeature-Resource
ms.openlocfilehash: d9b8cc316255f06d2de71fedc47ce4472cc8b382
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
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

|  Eigenschap  |  Beschrijving   | 
|---|---| 
| Naam| Geeft de naam van de functie die u wilt zorgen is ingeschakeld of uitgeschakeld.| 
| Zorg ervoor dat| Hiermee geeft u op of de functie is ingeschakeld. Om ervoor te zorgen dat de functie is ingeschakeld, stel deze eigenschap in op 'Inschakelen' om ervoor te zorgen dat de functie is uitgeschakeld, de eigenschap instellen op 'Uitschakelen'.|
| Bron| Niet geïmplementeerd.|
| NoWindowsUpdateCheck| Hiermee geeft u op of DISM neemt contact op met Windows Update (WU) bij het zoeken naar de bronbestanden van een functie in te schakelen. Als $true, DISM niet contact opneemt met WU.|
| RemoveFilesOnDisable| Ingesteld op **$true** verwijderen van alle bestanden die zijn gekoppeld aan de functie wanneer deze is uitgeschakeld (dat wil zeggen, wanneer **Zorg ervoor dat** is ingesteld op 'Afwezig').|
| Logniveau| Het maximale uitvoerniveau op die wordt weergegeven in de logboeken. De toegestane waarden zijn: 'ErrorsOnly' (alleen fouten worden geregistreerd), 'ErrorsAndWarning' (fouten en waarschuwingen worden geregistreerd), en 'ErrorsAndWarningAndInformation' (fouten, waarschuwingen en foutopsporingsinformatie worden geregistreerd).|
| Logboekpad| Het pad naar een logboekbestand waar u de resourceprovider aan te melden van de bewerking.| 
| dependsOn| Specificeert dat de configuratie van een andere resource moet worden uitgevoerd voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.| 
 



