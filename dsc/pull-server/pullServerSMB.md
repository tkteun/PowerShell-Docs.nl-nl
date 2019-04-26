---
ms.date: 04/11/2018
keywords: DSC, powershell, configuratie en installatie
title: Een DSC SMB-pull-server instellen
ms.openlocfilehash: 9d087a08861b2f4683e81efd1e25f857b8b75e07
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079282"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Een DSC SMB-pull-server instellen

Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden. Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).

Een DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull-server is een computer die als host fungeert voor SMB-bestandsshares die DSC-configuratiebestanden en DSC-resources beschikbaar zijn voor doelknooppunten maken wanneer deze knooppunten om ze vragen.

Voor het gebruik van een SMB-pull-server voor DSC, hebt u naar:

- Instellen van een SMB-bestandsshare op een server met PowerShell 4.0 of hoger
- Een client met PowerShell 4.0 of hoger om op te halen uit dat SMB-share configureren

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Een SMB-bestandsshare maken met behulp van de resource xSmbShare

Er zijn een aantal manieren om een SMB-bestandsshare instellen, maar laten we kijken hoe u dit doen kunt met behulp van DSC.

### <a name="install-the-xsmbshare-resource"></a>De resource xSmbShare installeren

Roep de [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet voor het installeren van de **xSmbShare** module.

> [!NOTE]
> `Install-Module` is opgenomen in de **PowerShellGet** module die is opgenomen in PowerShell 5.0. U kunt downloaden de **PowerShellGet** -module voor PowerShell 3.0 en 4.0 op [PackageManagement PowerShell-Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
> De **xSmbShare** bevat de DSC-resource **xSmbShare**, die kan worden gebruikt om een SMB-bestandsshare te maken.

### <a name="create-the-directory-and-file-share"></a>Maak de map- en -share

De volgende configuratie maakt gebruik van de **bestand** resource die u wilt maken van de map voor de share en de **xSmbShare** resource voor het instellen van de SMB-share:

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

De configuratie maakt de map `C:\DscSmbShare`, als deze nog niet bestaat, en vervolgens die map als een SMB-bestandsshare gebruikt. **FullAccess** moet worden gegeven aan een account dat moet schrijven of verwijderen van de bestandsshare. **ReadAccess** moet krijgen tot alle client-knooppunten die configuraties en/of DSC-resources uit de share ophalen.

> [!NOTE]
> DSC wordt uitgevoerd als het systeem-account standaard, zodat de computer zelf toegang tot de share hebben moet.

### <a name="give-file-system-access-to-the-pull-client"></a>Geeft toegang tot bestandssysteem naar de pull-client

Geeft **ReadAccess** naar een client kan knooppunt dat knooppunt toegang tot de SMB-share, maar niet aan de bestanden of mappen in die share. U moet expliciet client knooppunten toegang verlenen tot de SMB-share-map en submappen. We kunnen dit doen met DSC door toe te voegen met behulp van de **cNtfsPermissionEntry** -resource, die is opgenomen in de [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module. De volgende configuratie voegt een **cNtfsPermissionEntry** blok dat ReadAndExecute toegang wordt verleend aan de pull-client:

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a>Het plaatsen van configuraties en resources

Sla configuratie MOF-bestanden en/of DSC-resources die u wilt dat knooppunten van de client om op te halen in de SMB-share-map.

Een MOF-configuratiebestand moet de naam *ConfigurationID*.mof, waar *ConfigurationID* is de waarde van de **ConfigurationID** eigenschap van het doelknooppunt LCM. Zie voor meer informatie over het instellen van pull-clients [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).

> [!NOTE]
> Als u een SMB-pull-server, moet u configuratie-ID's gebruiken. Namen worden niet ondersteund voor SMB.

Elke resource-module moet worden ingepakt en met de naam op basis van het volgende patroon `{Module Name}_{Module Version}.zip`. Bijvoorbeeld, een module met de naam xWebAdminstration met de moduleversie van een van 3.1.2.0 zou worden met de naam 'xWebAdministration_3.2.1.0.zip'. Elke versie van een module moet worden opgenomen in een enkel zip-bestand. Verschillende versies van een module in een zip-bestand worden niet ondersteund. Voordat verpakking van DSC-resource-modules voor gebruik met pull-server moet u een kleine wijziging aanbrengen in de mapstructuur.

De standaardnotatie van modules met DSC-resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.

Pakketten voor de pull-server te verwijderen en daarna de `{Module version}` map, zodat het pad wordt `{Module Folder}\DscResources\{DSC Resource Folder}\`. Met deze wijziging, zip-de map, zoals hierboven beschreven en plaatst deze zip-bestanden op de SMB-share-map.

## <a name="creating-the-mof-checksum"></a>Het maken van de controlesom MOF

Een MOF-configuratiebestand moet worden gekoppeld aan een bestand controlesom zodat een LCM op een doelknooppunt kan de configuratie valideren.
Aanroepen voor het maken van een controlesom, de [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet. De cmdlet voert een `Path` parameter waarmee de map waarin de configuratie van de MOF zich bevindt. De cmdlet maakt een controlesom-bestand met de naam `ConfigurationMOFName.mof.checksum`, waarbij `ConfigurationMOFName` is de naam van de mof-configuratiebestand.
Als er meer dan één configuratie MOF-bestanden in de opgegeven map, wordt een controlesom gemaakt voor elke configuratie in de map.

Het bestand controlesom moet aanwezig zijn in dezelfde map als het MOF-configuratiebestand (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` standaard), en hebben dezelfde naam als de `.checksum` extensie toegevoegd.

> [!NOTE]
> Als u het MOF-configuratiebestand op geen enkele manier wijzigt, moet u ook het bestand controlesom opnieuw maken.

## <a name="setting-up-a-pull-client-for-smb"></a>Instellen van een pull-client voor SMB

Als u een client die wordt opgehaald van configuraties en/of bronnen van een SMB-share instelt, configureert u van de client lokaal Configuration Manager (LCM) met **ConfigurationRepositoryShare** en **ResourceRepositoryShare** blokken die de share van die voor het ophalen van configuraties en DSC-resources opgeven.

Zie voor meer informatie over het configureren van de LCM [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).

> [!NOTE]
> Voor het gemak in dit voorbeeld wordt de **PSDscAllowPlainTextPassword** om toe te staan een wachtwoord als leesbare tekst aan te geven de **referentie** parameter. Zie voor meer informatie over het doorgeven van referenties veiliger [Referentieopties in de configuratiegegevens](../configurations/configDataCredentials.md).
>
> U **moet** geven een **ConfigurationID** in de **instellingen** blokkeren van een metaconfiguration voor een SMB-pull-server, zelfs als u alleen binnenhalen van resources.

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a>Bevestigingen

Speciale dankzij de volgende personen:

- Mike F. Robbins, waarvan berichten over het gebruik van SMB voor DSC geholpen informeren over de inhoud in dit onderwerp. Zijn blog loopt [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, auteur van de **cNtfsAccessControl** module. De bron voor deze module is op [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).

## <a name="see-also"></a>Zie ook

[Windows PowerShell Desired State Configuration-overzicht](../overview/overview.md)

[Configuraties doorvoeren](enactingConfigurations.md)

[Een pull-client instellen met behulp van het configuratie-id](pullClientConfigID.md)
