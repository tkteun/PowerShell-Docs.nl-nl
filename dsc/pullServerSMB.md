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
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="47968-103">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="47968-103">Setting up a DSC SMB pull server</span></span>

><span data-ttu-id="47968-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="47968-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47968-105">De Pull-Server (Windows-onderdeel *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om de nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="47968-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="47968-106">Het verdient aanbeveling om te beginnen met een overgang clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen vermeld [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="47968-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="47968-107">Een DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull-server is een computer die als host fungeert voor SMB-bestandsshares die DSC-configuratiebestanden en DSC-resources beschikbaar voor de doelknooppunten wanneer die knooppunten van deze vragen.</span><span class="sxs-lookup"><span data-stu-id="47968-107">A DSC [SMB](https://technet.microsoft.com/library/hh831795.aspx) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="47968-108">Wilt gebruiken een SMB-pull-server voor DSC, moet u u:</span><span class="sxs-lookup"><span data-stu-id="47968-108">To use an SMB pull server for DSC, you have to:</span></span>
- <span data-ttu-id="47968-109">Instellen van een SMB-bestandsshare op een server met PowerShell 4.0 of hoger</span><span class="sxs-lookup"><span data-stu-id="47968-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="47968-110">Een client waarop PowerShell 4.0 of hoger wordt uitgevoerd voor het ophalen van SMB-share configureren</span><span class="sxs-lookup"><span data-stu-id="47968-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="47968-111">De resource xSmbShare gebruiken voor het maken van een SMB-bestandsshare</span><span class="sxs-lookup"><span data-stu-id="47968-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="47968-112">Er zijn een aantal manieren op een SMB-bestandsshare instellen, maar bekijken we hoe u dit doen kunt met behulp van DSC.</span><span class="sxs-lookup"><span data-stu-id="47968-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="47968-113">De resource xSmbShare installeren</span><span class="sxs-lookup"><span data-stu-id="47968-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="47968-114">Roep de [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet voor het installeren van de **xSmbShare** module.</span><span class="sxs-lookup"><span data-stu-id="47968-114">Call the [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet to install the **xSmbShare** module.</span></span>
><span data-ttu-id="47968-115">**Opmerking**: **Install-Module** is opgenomen in de **PowerShellGet** module die is opgenomen in PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="47968-115">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="47968-116">U kunt downloaden via de **PowerShellGet** -module voor PowerShell 3.0 en 4.0 op [PackageManagement PowerShell-Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="47968-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span> <span data-ttu-id="47968-117">De **xSmbShare** bevat de DSC-resource **xSmbShare**, die kan worden gebruikt voor het maken van een SMB-bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="47968-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="47968-118">De directory en bestandsshare maken</span><span class="sxs-lookup"><span data-stu-id="47968-118">Create the directory and file share</span></span>

<span data-ttu-id="47968-119">De volgende configuratie gebruikt de [bestand](fileResource.md) resource toe aan de map voor de share maken en de **xSmbShare** resource voor het instellen van de SMB-share:</span><span class="sxs-lookup"><span data-stu-id="47968-119">The following configuration uses the [File](fileResource.md) resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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

<span data-ttu-id="47968-120">De configuratie maakt u de map `C:\DscSmbShare` als dat niet al bestaat en wordt vervolgens die map als een SMB-bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="47968-120">The configuration creates the directory `C:\DscSmbShare` if it doesn't already exists, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="47968-121">**FullAccess** moet krijgen tot een account dat moet kunnen om te schrijven of verwijderen van de bestandsshare en **ReadAccess** worden besteed aan de client knooppunten die configuraties en/of DSC-resources van de share (dit is omdat ophalen DSC als het systeem-account wordt standaard uitgevoerd, zodat de computer zelf heeft toegang tot de share).</span><span class="sxs-lookup"><span data-stu-id="47968-121">**FullAccess** should be given to any account that needs to write to or delete from the file share, and **ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share ( this is because DSC runs as the system account by default, so the computer itself has to have access to the share).</span></span>


### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="47968-122">Geeft toegang tot bestandssysteem naar de pull-client</span><span class="sxs-lookup"><span data-stu-id="47968-122">Give file system access to the pull client</span></span>

<span data-ttu-id="47968-123">Geeft **ReadAccess** naar een client kan knooppunt dat knooppunt toegang tot de SMB-share, maar niet aan de bestanden of mappen in die share.</span><span class="sxs-lookup"><span data-stu-id="47968-123">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="47968-124">U moet expliciet client knooppunten toegang verlenen tot de SMB-sharemap en submappen.</span><span class="sxs-lookup"><span data-stu-id="47968-124">You have to explicitly grant client nodes access to the SMB share folder and sub-folders.</span></span> <span data-ttu-id="47968-125">We kunt dit doen met DSC door toe te voegen met behulp van de **cNtfsPermissionEntry** resource, die is opgenomen in de [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span><span class="sxs-lookup"><span data-stu-id="47968-125">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="47968-126">De volgende configuratie wordt toegevoegd een **cNtfsPermissionEntry** blok die ReadAndExecute toegang aan de pull-client verleent:</span><span class="sxs-lookup"><span data-stu-id="47968-126">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="47968-127">Configuraties en resources plaatsen</span><span class="sxs-lookup"><span data-stu-id="47968-127">Placing configurations and resources</span></span>

<span data-ttu-id="47968-128">Sla alle configuratie MOF-bestanden en/of de DSC-resources die u wilt dat de client-knooppunten ophalen van de SMB-share-map.</span><span class="sxs-lookup"><span data-stu-id="47968-128">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="47968-129">Elke configuratie MOF-bestand moet de naam _ConfigurationID_MOF, waarbij _ConfigurationID_ is de waarde van de **ConfigurationID** eigenschap van het doelknooppunt LCM.</span><span class="sxs-lookup"><span data-stu-id="47968-129">Any configuration MOF file must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="47968-130">Zie voor meer informatie over het instellen van pull-clients [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="47968-130">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="47968-131">**Opmerking:** moet u configuratie-ID's gebruiken als u een SMB-pull-server.</span><span class="sxs-lookup"><span data-stu-id="47968-131">**Note:** You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="47968-132">Namen worden niet ondersteund voor SMB.</span><span class="sxs-lookup"><span data-stu-id="47968-132">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="47968-133">Elke resource module moet worden ingepakt en met de naam op basis van de volgende patroon `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="47968-133">Each resource module needs to be zipped and named according the the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="47968-134">Bijvoorbeeld, een module met de naam xWebAdminstration met een moduleversie van 3.1.2.0 de naam 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="47968-134">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="47968-135">Elke versie van een module moet worden opgenomen in een enkel zip-bestand.</span><span class="sxs-lookup"><span data-stu-id="47968-135">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="47968-136">Omdat er slechts één versie van een resource in elke zip-bestand in WMF 5.0 met de indeling van de module hebt toegevoegd wordt ondersteuning voor meerdere moduleversies van de in een enkele map wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="47968-136">Since there is only a single version of a resource in each zip file the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="47968-137">Dit betekent dat voordat verpakking van DSC-resource-modules voor gebruik met pull-server moet u een kleine wijziging aanbrengt in de mapstructuur.</span><span class="sxs-lookup"><span data-stu-id="47968-137">This means that before packaging up DSC resource modules for use with pull server you need to make a small change to the directory structure.</span></span> <span data-ttu-id="47968-138">De standaardindeling van modules met van DSC-resource in WMF 5.0 is ' {Modulemap}\{moduleversie} \DscResources\{DSC-Resourcemap}\'.</span><span class="sxs-lookup"><span data-stu-id="47968-138">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="47968-139">Pakketten voor de pull-server te verwijderen en daarna de **{moduleversie}** map zodat het pad ' {Modulemap} \DscResources\{DSC-Resourcemap}\'.</span><span class="sxs-lookup"><span data-stu-id="47968-139">Before packaging up for the pull server simply remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span> <span data-ttu-id="47968-140">Met deze wijziging van de map zip zoals hierboven wordt beschreven en plaats deze zip-bestanden in de map van SMB-share.</span><span class="sxs-lookup"><span data-stu-id="47968-140">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="47968-141">Maken van de controlesom MOF</span><span class="sxs-lookup"><span data-stu-id="47968-141">Creating the MOF checksum</span></span>
<span data-ttu-id="47968-142">Een configuratie MOF-bestand moet worden gekoppeld aan een bestand controlesom zodat een LCM in een doelknooppunt kunt de configuratie valideren.</span><span class="sxs-lookup"><span data-stu-id="47968-142">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="47968-143">Aanroepen voor het maken van een controlesom, de [nieuw DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="47968-143">To create a checksum, call the [New-DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet.</span></span> <span data-ttu-id="47968-144">De cmdlet heeft een **pad** parameter waarmee de map waarin de configuratie van de MOF zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="47968-144">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="47968-145">De cmdlet maakt een controlesom-bestand met de naam `ConfigurationMOFName.mof.checksum`, waarbij `ConfigurationMOFName` is de naam van het mof-bestand voor configuratie.</span><span class="sxs-lookup"><span data-stu-id="47968-145">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="47968-146">Als er meer dan één configuratie MOF-bestanden in de opgegeven map, wordt een controlesom gemaakt voor elke configuratie in de map.</span><span class="sxs-lookup"><span data-stu-id="47968-146">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="47968-147">De controlesom bestand moet aanwezig zijn in dezelfde map als het MOF-bestand voor configuratie (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` standaard), en hebben dezelfde naam als de `.checksum` extensie toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="47968-147">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

><span data-ttu-id="47968-148">**Opmerking**: als u het MOF-bestand van de configuratie op een manier wijzigt, moet u ook het bestand controlesom opnieuw.</span><span class="sxs-lookup"><span data-stu-id="47968-148">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="47968-149">Een pull-client voor SMB instellen</span><span class="sxs-lookup"><span data-stu-id="47968-149">Setting up a pull client for SMB</span></span>

<span data-ttu-id="47968-150">Als u een client die Hiermee configuraties en/of bronnen van een SMB-share instelt, die u configureert de client lokale Configuration Manager (LCM) met **ConfigurationRepositoryShare** en **ResourceRepositoryShare** blokken die de share waaruit de pull-configuraties en DSC-resources opgeven.</span><span class="sxs-lookup"><span data-stu-id="47968-150">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="47968-151">Zie voor meer informatie over het configureren van de LCM [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="47968-151">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

><span data-ttu-id="47968-152">**Opmerking:** voor eenvoud, in dit voorbeeld wordt de **PSDscAllowPlainTextPassword** om toe te staan voor het doorgeven van een wachtwoord als leesbare tekst voor de **referentie** parameter.</span><span class="sxs-lookup"><span data-stu-id="47968-152">**Note:** For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="47968-153">Zie voor meer informatie over het doorgeven van referenties veiliger [Referentieopties in de configuratiegegevens](configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="47968-153">For information about passing credentials more securely, see [Credentials Options in Configuration Data](configDataCredentials.md).</span></span>

><span data-ttu-id="47968-154">**Opmerking:** moet u een **ConfigurationID** in de **instellingen** blok van een metaconfiguratie voor een SMB-pull-server, zelfs als u alleen binnenhalen van resources.</span><span class="sxs-lookup"><span data-stu-id="47968-154">**Note:** You must specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="47968-155">Bevestigingen</span><span class="sxs-lookup"><span data-stu-id="47968-155">Acknowledgements</span></span>

<span data-ttu-id="47968-156">Speciale dankzij het volgende:</span><span class="sxs-lookup"><span data-stu-id="47968-156">Special thanks to the following:</span></span>

- <span data-ttu-id="47968-157">Mike F. Robbins, waarvan berichten over het gebruik van SMB voor DSC geholpen informeren over de inhoud in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="47968-157">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="47968-158">Zijn blog loopt [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="47968-158">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="47968-159">Serge Nikalaichyk, auteur van de **cNtfsAccessControl** module.</span><span class="sxs-lookup"><span data-stu-id="47968-159">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="47968-160">De bron voor deze module is op https://github.com/SNikalaichyk/cNtfsAccessControl.</span><span class="sxs-lookup"><span data-stu-id="47968-160">The source for this module is at https://github.com/SNikalaichyk/cNtfsAccessControl.</span></span>

## <a name="see-also"></a><span data-ttu-id="47968-161">Zie ook</span><span class="sxs-lookup"><span data-stu-id="47968-161">See also</span></span>
- [<span data-ttu-id="47968-162">Windows PowerShell Desired State Configuration-overzicht</span><span class="sxs-lookup"><span data-stu-id="47968-162">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="47968-163">Configuraties doorvoeren</span><span class="sxs-lookup"><span data-stu-id="47968-163">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="47968-164">Een pull-client instellen met behulp van het configuratie-id</span><span class="sxs-lookup"><span data-stu-id="47968-164">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)