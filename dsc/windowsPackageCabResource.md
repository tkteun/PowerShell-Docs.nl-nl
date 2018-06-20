---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC-WindowsPackageCab Resource
ms.openlocfilehash: 8c4de193c8ea787dd125436f86aa0b5eafdb1509
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190346"
---
# <a name="dsc-windowspackagecab-resource"></a>DSC-WindowsPackageCab Resource

> Van toepassing op: Windows PowerShell 5.1 en hoger

De **WindowsPackageCab** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme om te installeren of verwijderen van Windows-CAB-pakketten in een doelknooppunt.

Het doelknooppunt moet de DISM-PowerShell-module geïnstalleerd hebben. Zie voor informatie [Gebruik DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).


## <a name="syntax"></a>Syntaxis

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| Naam| Geeft de naam van het pakket voor u wilt een specifieke status zorgen.|
| Zorg ervoor dat| Hiermee wordt aangegeven of het pakket is geïnstalleerd. Deze eigenschap instellen op 'Afwezig' controleert u dat het pakket niet is geïnstalleerd (of het pakket verwijderen als deze is geïnstalleerd). Instellen om "" (de standaardwaarde) om te controleren of dat het pakket is geïnstalleerd.|
| Pad| Geeft het pad waar het pakket zich bevindt.|
| Logboekpad| Hiermee geeft u het volledige pad waar u de provider een logboekbestand om te installeren of verwijderen van het pakket opslaan.|
| dependsOn | Hiermee wordt aangegeven dat de configuratie van een andere resource uitvoeren moet voordat deze bron is geconfigureerd. Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is ' DependsOn = '[ ResourceType] ResourceName' ''.|

## <a name="example"></a>Voorbeeld

De volgende voorbeeldconfiguratie parameters nodig heeft, en zorgt ervoor dat het CAB-bestand opgegeven door de `$Name` parameter is geïnstalleerd.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```