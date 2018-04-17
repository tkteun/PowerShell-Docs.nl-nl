---
ms.date: 04/11/2018
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Een DSC SMB-pull-server instellen
ms.openlocfilehash: e4e313746e95af86c5d17a8de0549451b1399b6c
ms.sourcegitcommit: ece1794c94be4880a2af5a2605ed4721593643b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2018
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Een DSC SMB-pull-server instellen

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> De Pull-Server (Windows-onderdeel *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om de nieuwe functies en mogelijkheden bieden. Het verdient aanbeveling om te beginnen met een overgang clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen vermeld [hier](pullserver.md#community-solutions-for-pull-service).

Een DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull-server is een computer die als host fungeert voor SMB-bestandsshares die DSC-configuratiebestanden en DSC-resources beschikbaar voor de doelknooppunten wanneer die knooppunten van deze vragen.

Wilt gebruiken een SMB-pull-server voor DSC, moet u u:
- Instellen van een SMB-bestandsshare op een server met PowerShell 4.0 of hoger
- Een client waarop PowerShell 4.0 of hoger wordt uitgevoerd voor het ophalen van SMB-share configureren

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>De resource xSmbShare gebruiken voor het maken van een SMB-bestandsshare

Er zijn een aantal manieren op een SMB-bestandsshare instellen, maar bekijken we hoe u dit doen kunt met behulp van DSC.

### <a name="install-the-xsmbshare-resource"></a>De resource xSmbShare installeren

Roep de [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet voor het installeren van de **xSmbShare** module.
>**Opmerking**: **Install-Module** is opgenomen in de **PowerShellGet** module die is opgenomen in PowerShell 5.0. U kunt downloaden via de **PowerShellGet** -module voor PowerShell 3.0 en 4.0 op [PackageManagement PowerShell-Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186). De **xSmbShare** bevat de DSC-resource **xSmbShare**, die kan worden gebruikt voor het maken van een SMB-bestandsshare.

### <a name="create-the-directory-and-file-share"></a>De directory en bestandsshare maken

De volgende configuratie gebruikt de [bestand](fileResource.md) resource toe aan de map voor de share maken en de **xSmbShare** resource voor het instellen van de SMB-share:

```powershell
Configuration SmbShare {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare

    Node localhost {

        File CreateFolder {

            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

    }

}
```

De configuratie maakt u de map `C:\DscSmbShare` als dat niet al bestaat en wordt vervolgens die map als een SMB-bestandsshare. **FullAccess** moet krijgen tot een account dat moet kunnen om te schrijven of verwijderen van de bestandsshare en **ReadAccess** worden besteed aan de client knooppunten die configuraties en/of DSC-resources van de share (dit is omdat ophalen DSC als het systeem-account wordt standaard uitgevoerd, zodat de computer zelf heeft toegang tot de share).


### <a name="give-file-system-access-to-the-pull-client"></a>Geeft toegang tot bestandssysteem naar de pull-client

Geeft **ReadAccess** naar een client kan knooppunt dat knooppunt toegang tot de SMB-share, maar niet aan de bestanden of mappen in die share. U moet expliciet client knooppunten toegang verlenen tot de SMB-sharemap en submappen. We kunt dit doen met DSC door toe te voegen met behulp van de **cNtfsPermissionEntry** resource, die is opgenomen in de [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module. De volgende configuratie wordt toegevoegd een **cNtfsPermissionEntry** blok die ReadAndExecute toegang aan de pull-client verleent:

```powershell
Configuration DSCSMB {

Import-DscResource -ModuleName PSDesiredStateConfiguration
Import-DscResource -ModuleName xSmbShare
Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost {

        File CreateFolder {

            DestinationPath = 'DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'

        }

        xSMBShare CreateShare {

            Name = 'DscSmbShare'
            Path = 'DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'

        }

        cNtfsPermissionEntry PermissionSet1 {

        Ensure = 'Present'
        Path = 'C:\DSCSMB'
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

Sla alle configuratie MOF-bestanden en/of de DSC-resources die u wilt dat de client-knooppunten ophalen van de SMB-share-map.

Elke configuratie MOF-bestand moet de naam _ConfigurationID_MOF, waarbij _ConfigurationID_ is de waarde van de **ConfigurationID** eigenschap van het doelknooppunt LCM. Zie voor meer informatie over het instellen van pull-clients [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).

>**Opmerking:** moet u configuratie-ID's gebruiken als u een SMB-pull-server. Namen worden niet ondersteund voor SMB.

Elke resource module moet worden ingepakt en met de naam op basis van de volgende patroon `{Module Name}_{Module Version}.zip`. Bijvoorbeeld, een module met de naam xWebAdminstration met een moduleversie van 3.1.2.0 de naam 'xWebAdministration_3.2.1.0.zip'. Elke versie van een module moet worden opgenomen in een enkel zip-bestand. Omdat er slechts één versie van een resource in elke zip-bestand in WMF 5.0 met de indeling van de module hebt toegevoegd wordt ondersteuning voor meerdere moduleversies van de in een enkele map wordt niet ondersteund. Dit betekent dat voordat verpakking van DSC-resource-modules voor gebruik met pull-server moet u een kleine wijziging aanbrengt in de mapstructuur. De standaardindeling van modules met van DSC-resource in WMF 5.0 is ' {Modulemap}\{moduleversie} \DscResources\{DSC-Resourcemap}\'. Pakketten voor de pull-server te verwijderen en daarna de **{moduleversie}** map zodat het pad ' {Modulemap} \DscResources\{DSC-Resourcemap}\'. Met deze wijziging van de map zip zoals hierboven wordt beschreven en plaats deze zip-bestanden in de map van SMB-share.

## <a name="creating-the-mof-checksum"></a>Maken van de controlesom MOF
Een configuratie MOF-bestand moet worden gekoppeld aan een bestand controlesom zodat een LCM in een doelknooppunt kunt de configuratie valideren.
Aanroepen voor het maken van een controlesom, de [nieuw DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet. De cmdlet heeft een **pad** parameter waarmee de map waarin de configuratie van de MOF zich bevindt. De cmdlet maakt een controlesom-bestand met de naam `ConfigurationMOFName.mof.checksum`, waarbij `ConfigurationMOFName` is de naam van het mof-bestand voor configuratie.
Als er meer dan één configuratie MOF-bestanden in de opgegeven map, wordt een controlesom gemaakt voor elke configuratie in de map.

De controlesom bestand moet aanwezig zijn in dezelfde map als het MOF-bestand voor configuratie (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` standaard), en hebben dezelfde naam als de `.checksum` extensie toegevoegd.

>**Opmerking**: als u het MOF-bestand van de configuratie op een manier wijzigt, moet u ook het bestand controlesom opnieuw.

## <a name="setting-up-a-pull-client-for-smb"></a>Een pull-client voor SMB instellen

Als u een client die Hiermee configuraties en/of bronnen van een SMB-share instelt, die u configureert de client lokale Configuration Manager (LCM) met **ConfigurationRepositoryShare** en **ResourceRepositoryShare** blokken die de share waaruit de pull-configuraties en DSC-resources opgeven.

Zie voor meer informatie over het configureren van de LCM [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).

>**Opmerking:** voor eenvoud, in dit voorbeeld wordt de **PSDscAllowPlainTextPassword** om toe te staan voor het doorgeven van een wachtwoord als leesbare tekst voor de **referentie** parameter. Zie voor meer informatie over het doorgeven van referenties veiliger [Referentieopties in de configuratiegegevens](configDataCredentials.md).

>**Opmerking:** moet u een **ConfigurationID** in de **instellingen** blok van een metaconfiguratie voor een SMB-pull-server, zelfs als u alleen binnenhalen van resources.

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

Speciale dankzij het volgende:

- Mike F. Robbins, waarvan berichten over het gebruik van SMB voor DSC geholpen informeren over de inhoud in dit onderwerp. Zijn blog loopt [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, auteur van de **cNtfsAccessControl** module. De bron voor deze module is op https://github.com/SNikalaichyk/cNtfsAccessControl.

## <a name="see-also"></a>Zie ook
- [Windows PowerShell Desired State Configuration-overzicht](overview.md)
- [Configuraties doorvoeren](enactingConfigurations.md)
- [Een pull-client instellen met behulp van het configuratie-id](pullClientConfigID.md)