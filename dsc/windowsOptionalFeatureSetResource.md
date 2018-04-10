---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-WindowsOptionalFeatureSet Resource
ms.openlocfilehash: 3329e0d0f1988a2ee20eb848da943ff1b22bd4df
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC-WindowsOptionalFeatureSet Resource

> Van toepassing op: Windows PowerShell 5.0

De **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om ervoor te zorgen dat de optionele functies zijn ingeschakeld op een doelknooppunt.
Deze bron is een [samengestelde bron](authoringResourceComposite.md) die roept de [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) voor elke functie die is opgegeven in de `Name` eigenschap.

Gebruik deze bron als u wilt een aantal optionele functies van Windows naar dezelfde toestand configureren.

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
| Naam| Geeft de naam van de functies die u wilt zorgen zijn ingeschakeld of uitgeschakeld.|
| Zorg ervoor dat| Hiermee geeft u op of de functies zijn ingeschakeld. Om ervoor te zorgen dat de functies zijn ingeschakeld, stel deze eigenschap in op 'Inschakelen' om ervoor te zorgen dat de functies zijn uitgeschakeld, de eigenschap instellen op 'Uitschakelen'.|
| Bron| Niet geïmplementeerd.|
| NoWindowsUpdateCheck| Hiermee geeft u op of DISM neemt contact op met Windows Update (WU) bij het zoeken naar de bronbestanden voor de functies inschakelen. Als $true, DISM niet contact opneemt met WU.|
| RemoveFilesOnDisable| Ingesteld op **$true** verwijderen van alle bestanden die zijn gekoppeld aan de functies als ze zijn uitgeschakeld (dat wil zeggen, wanneer **Zorg ervoor dat** is ingesteld op 'Afwezig').|
| Logniveau| Het maximale uitvoerniveau op die wordt weergegeven in de logboeken. De toegestane waarden zijn: 'ErrorsOnly' (alleen fouten worden geregistreerd), 'ErrorsAndWarning' (fouten en waarschuwingen worden geregistreerd), en 'ErrorsAndWarningAndInformation' (fouten, waarschuwingen en foutopsporingsinformatie worden geregistreerd).|
| Logboekpad| Het pad naar een logboekbestand waar u de resourceprovider aan te melden van de bewerking.|
| dependsOn| Specificeert dat de configuratie van een andere resource moet worden uitgevoerd voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is __ResourceName__ en het type __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.|