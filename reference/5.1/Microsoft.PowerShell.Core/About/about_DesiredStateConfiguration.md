---
description: In dit onderwerp vindt u een korte inleiding tot de Power shell-functie desired state Configuration (DSC).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_desiredstateconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_DesiredStateConfiguration
ms.openlocfilehash: 2f043104c67078b98355b3e54171a8993e534837
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253151"
---
# <a name="about_desiredstateconfiguration"></a>about_DesiredStateConfiguration

## <a name="short-description"></a>KORTE BESCHRIJVING

In dit onderwerp vindt u een korte inleiding tot de Power shell-functie desired state Configuration (DSC).

## <a name="long-description"></a>LANGE BESCHRIJVING

DSC is een beheer platform in Power shell waarmee u configuratie gegevens kunt implementeren en beheren voor software Services, en het beheren van de omgeving waarin deze services worden uitgevoerd.

DSC biedt een set Power shell-taal extensies, nieuwe cmdlets en resources die u kunt gebruiken om op te geven hoe u de status van uw software omgeving wilt configureren. Het biedt ook een manier om bestaande configuraties te onderhouden en te beheren.

DSC is geïntroduceerd in Power Shell 4,0.

Voor gedetailleerde informatie over DSC, Zie [Power shell desired state Configuration Overview](/powershell/scripting/dsc/overview/overview) (Engelstalig) in de TechNet-bibliotheek.

## <a name="developing-dsc-resources-with-classes"></a>DSC-RESOURCES ONTWIKKELEN MET KLASSEN

Vanaf Power shell 5,0 kunt u DSC-resources ontwikkelen met behulp van klassen.
Zie [about_Classes](about_Classes.md)en [Schrijf een aangepaste DSC-resource met Power shell-klassen](/previous-versions//dn948461(v=technet.10)) op micro soft TechNet voor meer informatie.

## <a name="using-dsc"></a>DSC GEBRUIKEN

Als u DSC wilt gebruiken om uw omgeving te configureren, moet u eerst een Power shell-script blok definiëren met behulp van het sleutel woord Configuration, gevolgd door een id, die wordt gevolgd door het paar accolades dat de blok kering opwaardeert. Binnen het configuratie blok kunt u knoop punten definiëren die de gewenste configuratie status opgeven voor elk knoop punt (computer) in de omgeving. Een knooppunt blok begint met het sleutel woord node, gevolgd door de naam van de doel computer, die een variabele kan zijn. Nadat de computer naam is bereikt, moet u de accolades die het knooppunt blok begrenzen, hebben. Binnen het knooppunt blok kunt u resource blokken definiëren voor het configureren van specifieke resources. Een resource blok begint met de type naam van de resource, gevolgd door de id die u voor dat blok wilt opgeven, gevolgd door de accolades die het blok beperken, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
Configuration MyWebConfig {
    # Parameters are optional
    param ($MachineName, $WebsiteFilePath)
    # A Configuration block can have one or more Node blocks
    Node $MachineName
    {
        # Next, specify one or more resource blocks
        # WindowsFeature is one of the resources you can use in a Node block
        # This example ensures the Web Server (IIS) role is installed
        WindowsFeature IIS
        {
            # To ensure that the role is not installed, set Ensure to "Absent"
            Ensure = "Present"
            Name = "Web-Server" # Use the Name property from Get-WindowsFeature
        }

        # You can use the File resource to create files and folders
        # "WebDirectory" is the name you want to use to refer to this instance
        File WebDirectory
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File"
            Recurse = $true
            SourcePath = $WebsiteFilePath
            DestinationPath = "C:\inetpub\wwwroot"

            # Ensure that the IIS block is successfully run first before
            # configuring this resource
            DependsOn = "[WindowsFeature]IIS"  # Use for dependencies
        }
    }
}
```

Als u een configuratie wilt maken, roept u het configuratie blok op dezelfde manier aan als een Power shell-functie, waarbij u eventuele verwachte para meters kunt door geven (twee in het bovenstaande voor beeld). In dit geval geldt het volgende:

```powershell
MyWebConfig -MachineName "TestMachine" -WebsiteFilePath `
  "\\filesrv\WebFiles" -OutputPath "C:\Windows\system32\temp"
# OutputPath is optional
```

Hiermee genereert u een MOF-bestand per knoop punt op het pad dat u opgeeft. Met deze MOF-bestanden wordt de gewenste configuratie voor elk knoop punt opgegeven. Gebruik vervolgens de volgende cmdlet voor het parseren van de configuratie-MOF-bestanden, verzend elk knoop punt de bijbehorende configuratie en pas deze configuraties toe. Houd er rekening mee dat u geen afzonderlijk MOF-bestand hoeft te maken voor DSC-resources op basis van een klasse.

```powershell
Start-DscConfiguration -Verbose -Wait -Path "C:\Windows\system32\temp"
```

## <a name="using-dsc-to-maintain-configuration-state"></a>DSC GEBRUIKEN OM DE CONFIGURATIE STATUS TE ONDERHOUDEN

Met DSC is configuratie idempotent. Dit betekent dat als u DSC gebruikt om dezelfde configuratie meermaals te gebruiken, de resulterende configuratie status altijd hetzelfde is. Als u vermoedt dat alle knoop punten in uw omgeving mogelijk zijn overgebracht van de gewenste configuratie status, kunt u dezelfde DSC-configuratie opnieuw uitvoeren om deze weer in de gewenste staat te brengen. U hoeft het configuratie script niet te wijzigen om alleen de resources te adresseren waarvan de status is overplaatst van de gewenste status.

In het volgende voor beeld ziet u hoe u kunt controleren of de werkelijke status van de configuratie op een bepaald knoop punt is overgegaan van de laatste DSC-configuratie die is uitgevaardigd op het knoop punt. In dit voor beeld controleren we de configuratie van de lokale computer.

```powershell
$session = New-CimSession -ComputerName "localhost"
Test-DscConfiguration -CimSession $session
```

## <a name="built-in-dsc-resources"></a>INGEBOUWDE DSC-RESOURCES

U kunt de volgende ingebouwde bronnen gebruiken in uw configuratie scripts:

|Naam                  |Eigenschappen                                         |
|----------------------|---------------------------------------------------|
|Bestand                  |{Doelpad, kenmerken, controlesom, inhoud...}|
|Archiveren               |{Doel, pad, controlesom, referentie...}       |
|Omgeving           |{Name, DependsOn, verzeker, Path...}                 |
|Groep                 |{GroupName, referentie, DependsOn, beschrijving...} |
|Logboek                   |{Message, DependsOn, PsDscRunAsCredential}         |
|Pakket               |{Name, Path, ProductId, arguments...}              |
|Register              |{Sleutel, waardenaam, DependsOn, zorg ervoor dat...}             |
|Script                |{GetScript, SetScript, TestScript, referentie...}  |
|Service               |{Naam, BuiltInAccount, referentie, afhankelijkheden...}|
|Gebruiker                  |{UserName, DependsOn, Description, disabled...}    |
|WaitForAll            |{Nodenaam, ResourceName, DependsOn, PsDscRunAsC...}|
|WaitForAny            |{Nodenaam, ResourceName, DependsOn, PsDscRunAsC...}|
|WaitForSome           |{NodeCount, nodenaam, ResourceName, DependsOn...}  |
|WindowsFeature        |{Naam, referentie, DependsOn, zorg ervoor dat...}           |
|WindowsOptionalFeature|{Name, DependsOn, verzeker u ervan, LogLevel...}             |
|WindowsProcess        |{Arguments, pad, referentie, DependsOn...}        |

Voer de cmdlet uit om een lijst met beschik bare DSC-resources op uw systeem te verkrijgen `Get-DscResource` .

> [!NOTE]
> In Power shell-versies onder 7,0 worden `Get-DscResource` op klassen gebaseerde DSC-resources niet gevonden.

In het voor beeld in dit onderwerp ziet u hoe u de bestands-en WindowsFeature-resources gebruikt. Als u alle eigenschappen wilt weer geven die u met een resource kunt gebruiken, plaatst u de cursor in het sleutel woord resource (bijvoorbeeld bestand) in het configuratie script in Power shell ISE, houdt u <kbd>CTRL</kbd> + <kbd>spatie balk</kbd> ingedrukt.

## <a name="find-more-resources"></a>MEER BRONNEN ZOEKEN

U kunt een groot aantal andere beschik bare DSC-resources downloaden, installeren en lezen die zijn gemaakt door de gebruikers community van Power shell en DSC, en door micro soft. Ga naar de [PowerShell Gallery](https://www.powershellgallery.com/) om te bladeren en meer te weten te komen over beschik bare DSC-resources.

## <a name="see-also"></a>ZIE OOK

[Overzicht van desired state Configuration van Power shell](/powershell/scripting/dsc/overview/overview)

[Ingebouwde Power shell desired state Configuration-resources](/powershell/scripting/dsc/resources/resources)

[Aangepaste Power shell-configuratie bronnen voor desired state bouwen](/powershell/scripting/dsc/resources/authoringResource)
