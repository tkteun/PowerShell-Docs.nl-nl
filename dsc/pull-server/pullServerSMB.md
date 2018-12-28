---
ms.date: 04/11/2018
keywords: DSC, powershell, configuratie en installatie
title: Een DSC SMB-pull-server instellen
ms.openlocfilehash: 722120369df9ff383a02c69111e0bacf2e2e76a5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403905"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="490a0-103">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="490a0-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="490a0-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="490a0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="490a0-105">De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="490a0-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="490a0-106">Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="490a0-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="490a0-107">Een DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull-server is een computer die als host fungeert voor SMB-bestandsshares die DSC-configuratiebestanden en DSC-resources beschikbaar zijn voor doelknooppunten maken wanneer deze knooppunten om ze vragen.</span><span class="sxs-lookup"><span data-stu-id="490a0-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="490a0-108">Voor het gebruik van een SMB-pull-server voor DSC, hebt u naar:</span><span class="sxs-lookup"><span data-stu-id="490a0-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="490a0-109">Instellen van een SMB-bestandsshare op een server met PowerShell 4.0 of hoger</span><span class="sxs-lookup"><span data-stu-id="490a0-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="490a0-110">Een client met PowerShell 4.0 of hoger om op te halen uit dat SMB-share configureren</span><span class="sxs-lookup"><span data-stu-id="490a0-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="490a0-111">Een SMB-bestandsshare maken met behulp van de resource xSmbShare</span><span class="sxs-lookup"><span data-stu-id="490a0-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="490a0-112">Er zijn een aantal manieren om een SMB-bestandsshare instellen, maar laten we kijken hoe u dit doen kunt met behulp van DSC.</span><span class="sxs-lookup"><span data-stu-id="490a0-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="490a0-113">De resource xSmbShare installeren</span><span class="sxs-lookup"><span data-stu-id="490a0-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="490a0-114">Roep de [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet voor het installeren van de **xSmbShare** module.</span><span class="sxs-lookup"><span data-stu-id="490a0-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="490a0-115">`Install-Module` is opgenomen in de **PowerShellGet** module die is opgenomen in PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="490a0-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="490a0-116">U kunt downloaden de **PowerShellGet** -module voor PowerShell 3.0 en 4.0 op [PackageManagement PowerShell-Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="490a0-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="490a0-117">De **xSmbShare** bevat de DSC-resource **xSmbShare**, die kan worden gebruikt om een SMB-bestandsshare te maken.</span><span class="sxs-lookup"><span data-stu-id="490a0-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="490a0-118">Maak de map- en -share</span><span class="sxs-lookup"><span data-stu-id="490a0-118">Create the directory and file share</span></span>

<span data-ttu-id="490a0-119">De volgende configuratie maakt gebruik van de **bestand** resource die u wilt maken van de map voor de share en de **xSmbShare** resource voor het instellen van de SMB-share:</span><span class="sxs-lookup"><span data-stu-id="490a0-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

<span data-ttu-id="490a0-120">De configuratie maakt de map `C:\DscSmbShare`, als deze nog niet bestaat, en vervolgens die map als een SMB-bestandsshare gebruikt.</span><span class="sxs-lookup"><span data-stu-id="490a0-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="490a0-121">**FullAccess** moet worden gegeven aan een account dat moet schrijven of verwijderen van de bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="490a0-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="490a0-122">**ReadAccess** moet krijgen tot alle client-knooppunten die configuraties en/of DSC-resources uit de share ophalen.</span><span class="sxs-lookup"><span data-stu-id="490a0-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="490a0-123">DSC wordt uitgevoerd als het systeem-account standaard, zodat de computer zelf toegang tot de share hebben moet.</span><span class="sxs-lookup"><span data-stu-id="490a0-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="490a0-124">Geeft toegang tot bestandssysteem naar de pull-client</span><span class="sxs-lookup"><span data-stu-id="490a0-124">Give file system access to the pull client</span></span>

<span data-ttu-id="490a0-125">Geeft **ReadAccess** naar een client kan knooppunt dat knooppunt toegang tot de SMB-share, maar niet aan de bestanden of mappen in die share.</span><span class="sxs-lookup"><span data-stu-id="490a0-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="490a0-126">U moet expliciet client knooppunten toegang verlenen tot de SMB-share-map en submappen.</span><span class="sxs-lookup"><span data-stu-id="490a0-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="490a0-127">We kunnen dit doen met DSC door toe te voegen met behulp van de **cNtfsPermissionEntry** -resource, die is opgenomen in de [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span><span class="sxs-lookup"><span data-stu-id="490a0-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="490a0-128">De volgende configuratie voegt een **cNtfsPermissionEntry** blok dat ReadAndExecute toegang wordt verleend aan de pull-client:</span><span class="sxs-lookup"><span data-stu-id="490a0-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="490a0-129">Het plaatsen van configuraties en resources</span><span class="sxs-lookup"><span data-stu-id="490a0-129">Placing configurations and resources</span></span>

<span data-ttu-id="490a0-130">Sla configuratie MOF-bestanden en/of DSC-resources die u wilt dat knooppunten van de client om op te halen in de SMB-share-map.</span><span class="sxs-lookup"><span data-stu-id="490a0-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="490a0-131">Een MOF-configuratiebestand moet de naam *ConfigurationID*.mof, waar *ConfigurationID* is de waarde van de **ConfigurationID** eigenschap van het doelknooppunt LCM.</span><span class="sxs-lookup"><span data-stu-id="490a0-131">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="490a0-132">Zie voor meer informatie over het instellen van pull-clients [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="490a0-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="490a0-133">Als u een SMB-pull-server, moet u configuratie-ID's gebruiken.</span><span class="sxs-lookup"><span data-stu-id="490a0-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="490a0-134">Namen worden niet ondersteund voor SMB.</span><span class="sxs-lookup"><span data-stu-id="490a0-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="490a0-135">Elke resource-module moet worden ingepakt en met de naam op basis van het volgende patroon `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="490a0-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="490a0-136">Bijvoorbeeld, een module met de naam xWebAdminstration met de moduleversie van een van 3.1.2.0 zou worden met de naam 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="490a0-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="490a0-137">Elke versie van een module moet worden opgenomen in een enkel zip-bestand.</span><span class="sxs-lookup"><span data-stu-id="490a0-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="490a0-138">Verschillende versies van een module in een zip-bestand worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="490a0-138">Separate versions of a module in a zip file are not supported.</span></span> <span data-ttu-id="490a0-139">Voordat verpakking van DSC-resource-modules voor gebruik met pull-server moet u een kleine wijziging aanbrengen in de mapstructuur.</span><span class="sxs-lookup"><span data-stu-id="490a0-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="490a0-140">De standaardnotatie van modules met DSC-resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="490a0-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="490a0-141">Pakketten voor de pull-server te verwijderen en daarna de `{Module version}` map, zodat het pad wordt `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="490a0-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="490a0-142">Met deze wijziging, zip-de map, zoals hierboven beschreven en plaatst deze zip-bestanden op de SMB-share-map.</span><span class="sxs-lookup"><span data-stu-id="490a0-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="490a0-143">Het maken van de controlesom MOF</span><span class="sxs-lookup"><span data-stu-id="490a0-143">Creating the MOF checksum</span></span>

<span data-ttu-id="490a0-144">Een MOF-configuratiebestand moet worden gekoppeld aan een bestand controlesom zodat een LCM op een doelknooppunt kan de configuratie valideren.</span><span class="sxs-lookup"><span data-stu-id="490a0-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="490a0-145">Aanroepen voor het maken van een controlesom, de [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="490a0-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="490a0-146">De cmdlet voert een `Path` parameter waarmee de map waarin de configuratie van de MOF zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="490a0-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="490a0-147">De cmdlet maakt een controlesom-bestand met de naam `ConfigurationMOFName.mof.checksum`, waarbij `ConfigurationMOFName` is de naam van de mof-configuratiebestand.</span><span class="sxs-lookup"><span data-stu-id="490a0-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="490a0-148">Als er meer dan één configuratie MOF-bestanden in de opgegeven map, wordt een controlesom gemaakt voor elke configuratie in de map.</span><span class="sxs-lookup"><span data-stu-id="490a0-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="490a0-149">Het bestand controlesom moet aanwezig zijn in dezelfde map als het MOF-configuratiebestand (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` standaard), en hebben dezelfde naam als de `.checksum` extensie toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="490a0-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="490a0-150">Als u het MOF-configuratiebestand op geen enkele manier wijzigt, moet u ook het bestand controlesom opnieuw maken.</span><span class="sxs-lookup"><span data-stu-id="490a0-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="490a0-151">Instellen van een pull-client voor SMB</span><span class="sxs-lookup"><span data-stu-id="490a0-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="490a0-152">Als u een client die wordt opgehaald van configuraties en/of bronnen van een SMB-share instelt, configureert u van de client lokaal Configuration Manager (LCM) met **ConfigurationRepositoryShare** en **ResourceRepositoryShare** blokken die de share van die voor het ophalen van configuraties en DSC-resources opgeven.</span><span class="sxs-lookup"><span data-stu-id="490a0-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="490a0-153">Zie voor meer informatie over het configureren van de LCM [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="490a0-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="490a0-154">Voor het gemak in dit voorbeeld wordt de **PSDscAllowPlainTextPassword** om toe te staan een wachtwoord als leesbare tekst aan te geven de **referentie** parameter.</span><span class="sxs-lookup"><span data-stu-id="490a0-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="490a0-155">Zie voor meer informatie over het doorgeven van referenties veiliger [Referentieopties in de configuratiegegevens](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="490a0-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span>
>
> <span data-ttu-id="490a0-156">U **moet** geven een **ConfigurationID** in de **instellingen** blokkeren van een metaconfiguration voor een SMB-pull-server, zelfs als u alleen binnenhalen van resources.</span><span class="sxs-lookup"><span data-stu-id="490a0-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="490a0-157">Bevestigingen</span><span class="sxs-lookup"><span data-stu-id="490a0-157">Acknowledgements</span></span>

<span data-ttu-id="490a0-158">Speciale dankzij de volgende personen:</span><span class="sxs-lookup"><span data-stu-id="490a0-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="490a0-159">Mike F. Robbins, waarvan berichten over het gebruik van SMB voor DSC geholpen informeren over de inhoud in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="490a0-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="490a0-160">Zijn blog loopt [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="490a0-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="490a0-161">Serge Nikalaichyk, auteur van de **cNtfsAccessControl** module.</span><span class="sxs-lookup"><span data-stu-id="490a0-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="490a0-162">De bron voor deze module is op [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="490a0-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="490a0-163">Zie ook</span><span class="sxs-lookup"><span data-stu-id="490a0-163">See also</span></span>

[<span data-ttu-id="490a0-164">Windows PowerShell Desired State Configuration-overzicht</span><span class="sxs-lookup"><span data-stu-id="490a0-164">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="490a0-165">Configuraties doorvoeren</span><span class="sxs-lookup"><span data-stu-id="490a0-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="490a0-166">Een pull-client instellen met behulp van het configuratie-id</span><span class="sxs-lookup"><span data-stu-id="490a0-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
