---
ms.date: 04/11/2018
keywords: DSC, Power shell, configuratie, installatie
title: Een DSC SMB-pull-server instellen
ms.openlocfilehash: 25705d9ae06b3ce8daa352142cc0b84793ab6359
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324864"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Een DSC SMB-pull-server instellen

Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

> [!IMPORTANT]
> De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden. Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.

Een DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) -pull-server is een computer die als host fungeert voor de SMB-bestands shares die DSC-configuratie bestanden en DSC-resources beschikbaar maken voor doel knooppunten wanneer deze knoop punten hen vragen.

Als u een SMB-pull-server voor DSC wilt gebruiken, moet u het volgende doen:

- Een SMB-bestands share instellen op een server waarop Power Shell 4,0 of hoger wordt uitgevoerd
- Een client met Power Shell 4,0 of hoger configureren om deze SMB-share op te halen

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>De xSmbShare-Resource gebruiken voor het maken van een SMB-bestands share

Er zijn een aantal manieren om een SMB-bestands share in te stellen, maar we bekijken hoe u dit kunt doen met behulp van DSC.

### <a name="install-the-xsmbshare-resource"></a>De xSmbShare-resource installeren

Roep de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) aan om de **xSmbShare** -module te installeren.

> [!NOTE]
> `Install-Module`is opgenomen in de **PowerShellGet** -module, die is opgenomen in power shell 5,0. U kunt de **PowerShellGet** -module voor power Shell 3,0 en 4,0 downloaden van [Package Management Power shell-modules preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
> De **xSmbShare** bevat de DSC-resource **xSmbShare**, die kan worden gebruikt voor het maken van een SMB-bestands share.

### <a name="create-the-directory-and-file-share"></a>De map en bestands share maken

De volgende configuratie maakt gebruik van de **Bestands** resource voor het maken van de map voor de share en de **xSmbShare** -resource om de SMB-share in te stellen:

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

De-configuratie maakt de `C:\DscSmbShare`map, als deze nog niet bestaat, en gebruikt deze map als een SMB-bestands share. **FullAccess** moet worden opgegeven voor alle accounts die moeten worden geschreven of verwijderd uit de bestands share. **ReadAccess** moet worden toegewezen aan alle client knooppunten die configuraties en/of DSC-resources van de share ophalen.

> [!NOTE]
> DSC wordt standaard uitgevoerd als het systeem account, zodat de computer zelf toegang moet hebben tot de share.

### <a name="give-file-system-access-to-the-pull-client"></a>Bestands systeem toegang verlenen tot de pull-client

Door **ReadAccess** aan een client knooppunt toe te wijzen, kan dat knoop punt toegang krijgen tot de SMB-share, maar niet op bestanden of mappen binnen die share. U moet expliciet client knooppunten toegang verlenen tot de SMB share-map en de submappen. We kunnen dit doen met DSC door toe te voegen met behulp van de **cNtfsPermissionEntry** -resource, die is opgenomen in de [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) -module. De volgende configuratie voegt een **cNtfsPermissionEntry** -blok toe dat ReadAndExecute toegang verleent aan de pull-client:

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

## <a name="placing-configurations-and-resources"></a>Configuraties en resources plaatsen

Sla de configuratie-MOF-bestanden en/of DSC-resources op die door client knooppunten moeten worden opgehaald in de map SMB share.

Elk configuratie MOF-bestand moet de naam *ConfigurationID*. MOF hebben, waarbij *ConfigurationID* de waarde is van de eigenschap **ConfigurationID** van de LCM van het doel knooppunt. Zie [een pull-client instellen met behulp van de configuratie-ID](pullClientConfigID.md)voor meer informatie over het instellen van pull-clients.

> [!NOTE]
> U moet configuratie-Id's gebruiken als u een SMB-pull-server gebruikt. Configuratie namen worden niet ondersteund voor SMB.

Elke resource module moet een gezipte en een naam hebben op basis van `{Module Name}_{Module Version}.zip`het volgende patroon. Een module met de naam xWebAdminstration met een module versie van 3.1.2.0 zou bijvoorbeeld ' xWebAdministration_ 3.2.1.0. zip ' worden genoemd. Elke versie van een module moet zich in één ZIP-bestand bevinden. Afzonderlijke versies van een module in een zip-bestand worden niet ondersteund. Voordat u DSC-resource modules inpakt voor gebruik met een pull-server, moet u een kleine wijziging aanbrengen in de mapstructuur.

De standaard indeling van modules met DSC-resource in WMF 5,0 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`is.

Voordat u de pull-server kunt inpakken, `{Module version}` verwijdert u gewoon de map `{Module Folder}\DscResources\{DSC Resource Folder}\`, zodat het pad wordt gewijzigd. Ga met deze wijziging naar de map die hierboven is beschreven en plaats deze zip-bestanden in de map SMB share.

## <a name="creating-the-mof-checksum"></a>De MOF-controlesom maken

Een configuratie-MOF-bestand moet worden gekoppeld aan een controlesom bestand zodat een LCM op een doel knooppunt de configuratie kan valideren.
Als u een controlesom wilt maken, roept u de cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) aan. De cmdlet neemt een `Path` para meter op die de map specificeert waarin de configuratie-MOF zich bevindt. De cmdlet maakt een controlesom bestand `ConfigurationMOFName.mof.checksum`met de naam, waarbij `ConfigurationMOFName` de naam is van het MOF-configuratie bestand.
Als er meer dan één configuratie-MOF-bestanden in de opgegeven map zijn, wordt er een controlesom gemaakt voor elke configuratie in de map.

Het controlesom bestand moet zich in dezelfde map bevinden als het MOF-bestand van`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` de configuratie (standaard) en dezelfde naam hebben als de `.checksum` extensie is toegevoegd.

> [!NOTE]
> Als u het MOF-configuratie bestand op een wille keurige manier wijzigt, moet u het controlesom bestand ook opnieuw maken.

## <a name="setting-up-a-pull-client-for-smb"></a>Een pull-client voor SMB instellen

Als u een client wilt instellen die configuraties en/of resources van een SMB-share ophaalt, configureert u de lokale Configuration Manager (LCM) van de client met **ConfigurationRepositoryShare** -en **ResourceRepositoryShare** -blokken waarmee de share wordt opgegeven voor het ophalen van configuraties en DSC-resources.

Zie [een pull-client instellen met behulp van de configuratie-ID](pullClientConfigID.md)voor meer informatie over het configureren van de LCM.

> [!NOTE]
> Voor het gemak gebruikt dit voor beeld de **PSDscAllowPlainTextPassword** om het wacht woord voor een lees bare tekst door te geven aan de para meter **Credential** . Zie voor informatie over het veiliger door geven van referenties de [Opties voor referenties in configuratie gegevens](../configurations/configDataCredentials.md).
>
> U **moet** een **ConfigurationID** opgeven in het **instellingen** blok van een-configuratie voor een SMB-pull-server, zelfs als u alleen resources ophaalt.

```powershell
$secpasswd = ConvertTo-SecureString "Pass1Word" -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential ("TestUser", $secpasswd)

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

Speciale dank aan de volgende personen:

- Mike F. Robbins, wier berichten over het gebruik van SMB voor DSC hebben bijgedragen aan de inhoud in dit onderwerp. Zijn blog bevindt zich op [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, die de **cNtfsAccessControl** -module heeft gemaakt. De bron voor deze module bevindt zich op [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).

## <a name="see-also"></a>Zie ook

[Overzicht van desired state Configuration voor Windows Power shell](../overview/overview.md)

[Configuraties doorvoeren](enactingConfigurations.md)

[Een pull-client instellen met behulp van het configuratie-id](pullClientConfigID.md)
