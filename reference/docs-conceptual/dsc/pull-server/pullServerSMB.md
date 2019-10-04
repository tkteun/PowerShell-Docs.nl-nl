---
ms.date: 04/11/2018
keywords: DSC, Power shell, configuratie, installatie
title: Een DSC SMB-pull-server instellen
ms.openlocfilehash: 25705d9ae06b3ce8daa352142cc0b84793ab6359
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941689"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="b089b-103">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="b089b-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="b089b-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="b089b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b089b-105">De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden.</span><span class="sxs-lookup"><span data-stu-id="b089b-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b089b-106">Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.</span><span class="sxs-lookup"><span data-stu-id="b089b-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b089b-107">Een DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) -pull-server is een computer die als host fungeert voor de SMB-bestands shares die DSC-configuratie bestanden en DSC-resources beschikbaar maken voor doel knooppunten wanneer deze knoop punten hen vragen.</span><span class="sxs-lookup"><span data-stu-id="b089b-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="b089b-108">Als u een SMB-pull-server voor DSC wilt gebruiken, moet u het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="b089b-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="b089b-109">Een SMB-bestands share instellen op een server waarop Power Shell 4,0 of hoger wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="b089b-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="b089b-110">Een client met Power Shell 4,0 of hoger configureren om deze SMB-share op te halen</span><span class="sxs-lookup"><span data-stu-id="b089b-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="b089b-111">De xSmbShare-Resource gebruiken voor het maken van een SMB-bestands share</span><span class="sxs-lookup"><span data-stu-id="b089b-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="b089b-112">Er zijn een aantal manieren om een SMB-bestands share in te stellen, maar we bekijken hoe u dit kunt doen met behulp van DSC.</span><span class="sxs-lookup"><span data-stu-id="b089b-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="b089b-113">De xSmbShare-resource installeren</span><span class="sxs-lookup"><span data-stu-id="b089b-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="b089b-114">Roep de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) aan om de **xSmbShare** -module te installeren.</span><span class="sxs-lookup"><span data-stu-id="b089b-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="b089b-115">`Install-Module`is opgenomen in de **PowerShellGet** -module, die is opgenomen in power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="b089b-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="b089b-116">U kunt de **PowerShellGet** -module voor power Shell 3,0 en 4,0 downloaden van [Package Management Power shell-modules preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="b089b-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="b089b-117">De **xSmbShare** bevat de DSC-resource **xSmbShare**, die kan worden gebruikt voor het maken van een SMB-bestands share.</span><span class="sxs-lookup"><span data-stu-id="b089b-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="b089b-118">De map en bestands share maken</span><span class="sxs-lookup"><span data-stu-id="b089b-118">Create the directory and file share</span></span>

<span data-ttu-id="b089b-119">De volgende configuratie maakt gebruik van de **Bestands** resource voor het maken van de map voor de share en de **xSmbShare** -resource om de SMB-share in te stellen:</span><span class="sxs-lookup"><span data-stu-id="b089b-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

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

<span data-ttu-id="b089b-120">De-configuratie maakt de `C:\DscSmbShare`map, als deze nog niet bestaat, en gebruikt deze map als een SMB-bestands share.</span><span class="sxs-lookup"><span data-stu-id="b089b-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="b089b-121">**FullAccess** moet worden opgegeven voor alle accounts die moeten worden geschreven of verwijderd uit de bestands share.</span><span class="sxs-lookup"><span data-stu-id="b089b-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="b089b-122">**ReadAccess** moet worden toegewezen aan alle client knooppunten die configuraties en/of DSC-resources van de share ophalen.</span><span class="sxs-lookup"><span data-stu-id="b089b-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="b089b-123">DSC wordt standaard uitgevoerd als het systeem account, zodat de computer zelf toegang moet hebben tot de share.</span><span class="sxs-lookup"><span data-stu-id="b089b-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="b089b-124">Bestands systeem toegang verlenen tot de pull-client</span><span class="sxs-lookup"><span data-stu-id="b089b-124">Give file system access to the pull client</span></span>

<span data-ttu-id="b089b-125">Door **ReadAccess** aan een client knooppunt toe te wijzen, kan dat knoop punt toegang krijgen tot de SMB-share, maar niet op bestanden of mappen binnen die share.</span><span class="sxs-lookup"><span data-stu-id="b089b-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="b089b-126">U moet expliciet client knooppunten toegang verlenen tot de SMB share-map en de submappen.</span><span class="sxs-lookup"><span data-stu-id="b089b-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="b089b-127">We kunnen dit doen met DSC door toe te voegen met behulp van de **cNtfsPermissionEntry** -resource, die is opgenomen in de [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) -module.</span><span class="sxs-lookup"><span data-stu-id="b089b-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="b089b-128">De volgende configuratie voegt een **cNtfsPermissionEntry** -blok toe dat ReadAndExecute toegang verleent aan de pull-client:</span><span class="sxs-lookup"><span data-stu-id="b089b-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

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

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="b089b-129">Configuraties en resources plaatsen</span><span class="sxs-lookup"><span data-stu-id="b089b-129">Placing configurations and resources</span></span>

<span data-ttu-id="b089b-130">Sla de configuratie-MOF-bestanden en/of DSC-resources op die door client knooppunten moeten worden opgehaald in de map SMB share.</span><span class="sxs-lookup"><span data-stu-id="b089b-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="b089b-131">Elk configuratie MOF-bestand moet de naam *ConfigurationID*. MOF hebben, waarbij *ConfigurationID* de waarde is van de eigenschap **ConfigurationID** van de LCM van het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="b089b-131">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="b089b-132">Zie [een pull-client instellen met behulp van de configuratie-ID](pullClientConfigID.md)voor meer informatie over het instellen van pull-clients.</span><span class="sxs-lookup"><span data-stu-id="b089b-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b089b-133">U moet configuratie-Id's gebruiken als u een SMB-pull-server gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b089b-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="b089b-134">Configuratie namen worden niet ondersteund voor SMB.</span><span class="sxs-lookup"><span data-stu-id="b089b-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="b089b-135">Elke resource module moet een gezipte en een naam hebben op basis van `{Module Name}_{Module Version}.zip`het volgende patroon.</span><span class="sxs-lookup"><span data-stu-id="b089b-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="b089b-136">Een module met de naam xWebAdminstration met een module versie van 3.1.2.0 zou bijvoorbeeld ' xWebAdministration_ 3.2.1.0. zip ' worden genoemd.</span><span class="sxs-lookup"><span data-stu-id="b089b-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="b089b-137">Elke versie van een module moet zich in één ZIP-bestand bevinden.</span><span class="sxs-lookup"><span data-stu-id="b089b-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="b089b-138">Afzonderlijke versies van een module in een zip-bestand worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b089b-138">Separate versions of a module in a zip file are not supported.</span></span> <span data-ttu-id="b089b-139">Voordat u DSC-resource modules inpakt voor gebruik met een pull-server, moet u een kleine wijziging aanbrengen in de mapstructuur.</span><span class="sxs-lookup"><span data-stu-id="b089b-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="b089b-140">De standaard indeling van modules met DSC-resource in WMF 5,0 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`is.</span><span class="sxs-lookup"><span data-stu-id="b089b-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="b089b-141">Voordat u de pull-server kunt inpakken, `{Module version}` verwijdert u gewoon de map `{Module Folder}\DscResources\{DSC Resource Folder}\`, zodat het pad wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b089b-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="b089b-142">Ga met deze wijziging naar de map die hierboven is beschreven en plaats deze zip-bestanden in de map SMB share.</span><span class="sxs-lookup"><span data-stu-id="b089b-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="b089b-143">De MOF-controlesom maken</span><span class="sxs-lookup"><span data-stu-id="b089b-143">Creating the MOF checksum</span></span>

<span data-ttu-id="b089b-144">Een configuratie-MOF-bestand moet worden gekoppeld aan een controlesom bestand zodat een LCM op een doel knooppunt de configuratie kan valideren.</span><span class="sxs-lookup"><span data-stu-id="b089b-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="b089b-145">Als u een controlesom wilt maken, roept u de cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) aan.</span><span class="sxs-lookup"><span data-stu-id="b089b-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="b089b-146">De cmdlet neemt een `Path` para meter op die de map specificeert waarin de configuratie-MOF zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="b089b-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="b089b-147">De cmdlet maakt een controlesom bestand `ConfigurationMOFName.mof.checksum`met de naam, waarbij `ConfigurationMOFName` de naam is van het MOF-configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="b089b-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="b089b-148">Als er meer dan één configuratie-MOF-bestanden in de opgegeven map zijn, wordt er een controlesom gemaakt voor elke configuratie in de map.</span><span class="sxs-lookup"><span data-stu-id="b089b-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="b089b-149">Het controlesom bestand moet zich in dezelfde map bevinden als het MOF-bestand van`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` de configuratie (standaard) en dezelfde naam hebben als de `.checksum` extensie is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b089b-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="b089b-150">Als u het MOF-configuratie bestand op een wille keurige manier wijzigt, moet u het controlesom bestand ook opnieuw maken.</span><span class="sxs-lookup"><span data-stu-id="b089b-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="b089b-151">Een pull-client voor SMB instellen</span><span class="sxs-lookup"><span data-stu-id="b089b-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="b089b-152">Als u een client wilt instellen die configuraties en/of resources van een SMB-share ophaalt, configureert u de lokale Configuration Manager (LCM) van de client met **ConfigurationRepositoryShare** -en **ResourceRepositoryShare** -blokken waarmee de share wordt opgegeven voor het ophalen van configuraties en DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="b089b-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="b089b-153">Zie [een pull-client instellen met behulp van de configuratie-ID](pullClientConfigID.md)voor meer informatie over het configureren van de LCM.</span><span class="sxs-lookup"><span data-stu-id="b089b-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b089b-154">Voor het gemak gebruikt dit voor beeld de **PSDscAllowPlainTextPassword** om het wacht woord voor een lees bare tekst door te geven aan de para meter **Credential** .</span><span class="sxs-lookup"><span data-stu-id="b089b-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="b089b-155">Zie voor informatie over het veiliger door geven van referenties de [Opties voor referenties in configuratie gegevens](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="b089b-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span>
>
> <span data-ttu-id="b089b-156">U **moet** een **ConfigurationID** opgeven in het **instellingen** blok van een-configuratie voor een SMB-pull-server, zelfs als u alleen resources ophaalt.</span><span class="sxs-lookup"><span data-stu-id="b089b-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

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

## <a name="acknowledgements"></a><span data-ttu-id="b089b-157">Bevestigingen</span><span class="sxs-lookup"><span data-stu-id="b089b-157">Acknowledgements</span></span>

<span data-ttu-id="b089b-158">Speciale dank aan de volgende personen:</span><span class="sxs-lookup"><span data-stu-id="b089b-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="b089b-159">Mike F. Robbins, wier berichten over het gebruik van SMB voor DSC hebben bijgedragen aan de inhoud in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="b089b-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="b089b-160">Zijn blog bevindt zich op [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="b089b-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="b089b-161">Serge Nikalaichyk, die de **cNtfsAccessControl** -module heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b089b-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="b089b-162">De bron voor deze module bevindt zich op [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="b089b-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="b089b-163">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b089b-163">See also</span></span>

[<span data-ttu-id="b089b-164">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="b089b-164">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)

[<span data-ttu-id="b089b-165">Configuraties doorvoeren</span><span class="sxs-lookup"><span data-stu-id="b089b-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="b089b-166">Een pull-client instellen met behulp van het configuratie-id</span><span class="sxs-lookup"><span data-stu-id="b089b-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
