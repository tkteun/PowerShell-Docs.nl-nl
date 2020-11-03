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
# <a name="about_desiredstateconfiguration"></a><span data-ttu-id="14099-104">about_DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="14099-104">about_DesiredStateConfiguration</span></span>

## <a name="short-description"></a><span data-ttu-id="14099-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="14099-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="14099-106">In dit onderwerp vindt u een korte inleiding tot de Power shell-functie desired state Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="14099-106">Provides a brief introduction to the PowerShell Desired State Configuration (DSC) feature.</span></span>

## <a name="long-description"></a><span data-ttu-id="14099-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="14099-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="14099-108">DSC is een beheer platform in Power shell waarmee u configuratie gegevens kunt implementeren en beheren voor software Services, en het beheren van de omgeving waarin deze services worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="14099-108">DSC is a management platform in PowerShell that enables deploying and managing configuration data for software services, and managing the environment in which these services run.</span></span>

<span data-ttu-id="14099-109">DSC biedt een set Power shell-taal extensies, nieuwe cmdlets en resources die u kunt gebruiken om op te geven hoe u de status van uw software omgeving wilt configureren.</span><span class="sxs-lookup"><span data-stu-id="14099-109">DSC provides a set of PowerShell language extensions, new cmdlets, and resources that you can use to declaratively specify how you want the state of your software environment to be configured.</span></span> <span data-ttu-id="14099-110">Het biedt ook een manier om bestaande configuraties te onderhouden en te beheren.</span><span class="sxs-lookup"><span data-stu-id="14099-110">It also provides a means to maintain and manage existing configurations.</span></span>

<span data-ttu-id="14099-111">DSC is geïntroduceerd in Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="14099-111">DSC is introduced in PowerShell 4.0.</span></span>

<span data-ttu-id="14099-112">Voor gedetailleerde informatie over DSC, Zie [Power shell desired state Configuration Overview](/powershell/scripting/dsc/overview/overview) (Engelstalig) in de TechNet-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="14099-112">For detailed information about DSC, see [PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview) in the TechNet Library.</span></span>

## <a name="developing-dsc-resources-with-classes"></a><span data-ttu-id="14099-113">DSC-RESOURCES ONTWIKKELEN MET KLASSEN</span><span class="sxs-lookup"><span data-stu-id="14099-113">DEVELOPING DSC RESOURCES WITH CLASSES</span></span>

<span data-ttu-id="14099-114">Vanaf Power shell 5,0 kunt u DSC-resources ontwikkelen met behulp van klassen.</span><span class="sxs-lookup"><span data-stu-id="14099-114">Starting in PowerShell 5.0, you can develop DSC resources by using classes.</span></span>
<span data-ttu-id="14099-115">Zie [about_Classes](about_Classes.md)en [Schrijf een aangepaste DSC-resource met Power shell-klassen](/previous-versions//dn948461(v=technet.10)) op micro soft TechNet voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="14099-115">For more information, see [about_Classes](about_Classes.md), and [Writing a custom DSC resource with PowerShell classes](/previous-versions//dn948461(v=technet.10)) on Microsoft TechNet.</span></span>

## <a name="using-dsc"></a><span data-ttu-id="14099-116">DSC GEBRUIKEN</span><span class="sxs-lookup"><span data-stu-id="14099-116">USING DSC</span></span>

<span data-ttu-id="14099-117">Als u DSC wilt gebruiken om uw omgeving te configureren, moet u eerst een Power shell-script blok definiëren met behulp van het sleutel woord Configuration, gevolgd door een id, die wordt gevolgd door het paar accolades dat de blok kering opwaardeert.</span><span class="sxs-lookup"><span data-stu-id="14099-117">To use DSC to configure your environment, first define a PowerShell script block using the Configuration keyword, followed by an identifier, which is in turn followed by the pair of curly braces delimiting the block.</span></span> <span data-ttu-id="14099-118">Binnen het configuratie blok kunt u knoop punten definiëren die de gewenste configuratie status opgeven voor elk knoop punt (computer) in de omgeving.</span><span class="sxs-lookup"><span data-stu-id="14099-118">Inside the configuration block you can define node blocks that specify the desired configuration state for each node (computer) in the environment.</span></span> <span data-ttu-id="14099-119">Een knooppunt blok begint met het sleutel woord node, gevolgd door de naam van de doel computer, die een variabele kan zijn.</span><span class="sxs-lookup"><span data-stu-id="14099-119">A node block starts with the Node keyword, followed by the name of the target computer, which can be a variable.</span></span> <span data-ttu-id="14099-120">Nadat de computer naam is bereikt, moet u de accolades die het knooppunt blok begrenzen, hebben.</span><span class="sxs-lookup"><span data-stu-id="14099-120">After the computer name, come the curly braces that delimit the node block.</span></span> <span data-ttu-id="14099-121">Binnen het knooppunt blok kunt u resource blokken definiëren voor het configureren van specifieke resources.</span><span class="sxs-lookup"><span data-stu-id="14099-121">Inside the node block, you can define resource blocks to configure specific resources.</span></span> <span data-ttu-id="14099-122">Een resource blok begint met de type naam van de resource, gevolgd door de id die u voor dat blok wilt opgeven, gevolgd door de accolades die het blok beperken, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="14099-122">A resource block starts with the type name of the resource, followed by the identifier you want to specify for that block, followed by the curly braces that delimit the block, as shown in the following example.</span></span>

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

<span data-ttu-id="14099-123">Als u een configuratie wilt maken, roept u het configuratie blok op dezelfde manier aan als een Power shell-functie, waarbij u eventuele verwachte para meters kunt door geven (twee in het bovenstaande voor beeld).</span><span class="sxs-lookup"><span data-stu-id="14099-123">To create a configuration, invoke the Configuration block the same way you would invoke a PowerShell function, passing in any expected parameters you may have defined (two in the example above).</span></span> <span data-ttu-id="14099-124">In dit geval geldt het volgende:</span><span class="sxs-lookup"><span data-stu-id="14099-124">For example, in this case:</span></span>

```powershell
MyWebConfig -MachineName "TestMachine" -WebsiteFilePath `
  "\\filesrv\WebFiles" -OutputPath "C:\Windows\system32\temp"
# OutputPath is optional
```

<span data-ttu-id="14099-125">Hiermee genereert u een MOF-bestand per knoop punt op het pad dat u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="14099-125">This generates a MOF file per node at the path you specify.</span></span> <span data-ttu-id="14099-126">Met deze MOF-bestanden wordt de gewenste configuratie voor elk knoop punt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="14099-126">These MOF files specify the desired configuration for each node.</span></span> <span data-ttu-id="14099-127">Gebruik vervolgens de volgende cmdlet voor het parseren van de configuratie-MOF-bestanden, verzend elk knoop punt de bijbehorende configuratie en pas deze configuraties toe.</span><span class="sxs-lookup"><span data-stu-id="14099-127">Next, use the following cmdlet to parse the configuration MOF files, send each node its corresponding configuration, and enact those configurations.</span></span> <span data-ttu-id="14099-128">Houd er rekening mee dat u geen afzonderlijk MOF-bestand hoeft te maken voor DSC-resources op basis van een klasse.</span><span class="sxs-lookup"><span data-stu-id="14099-128">Note that you do not need to create a separate MOF file for class-based DSC resources.</span></span>

```powershell
Start-DscConfiguration -Verbose -Wait -Path "C:\Windows\system32\temp"
```

## <a name="using-dsc-to-maintain-configuration-state"></a><span data-ttu-id="14099-129">DSC GEBRUIKEN OM DE CONFIGURATIE STATUS TE ONDERHOUDEN</span><span class="sxs-lookup"><span data-stu-id="14099-129">USING DSC TO MAINTAIN CONFIGURATION STATE</span></span>

<span data-ttu-id="14099-130">Met DSC is configuratie idempotent.</span><span class="sxs-lookup"><span data-stu-id="14099-130">With DSC, configuration is idempotent.</span></span> <span data-ttu-id="14099-131">Dit betekent dat als u DSC gebruikt om dezelfde configuratie meermaals te gebruiken, de resulterende configuratie status altijd hetzelfde is.</span><span class="sxs-lookup"><span data-stu-id="14099-131">This means that if you use DSC to enact the same configuration more than once, the resulting configuration state will always be the same.</span></span> <span data-ttu-id="14099-132">Als u vermoedt dat alle knoop punten in uw omgeving mogelijk zijn overgebracht van de gewenste configuratie status, kunt u dezelfde DSC-configuratie opnieuw uitvoeren om deze weer in de gewenste staat te brengen.</span><span class="sxs-lookup"><span data-stu-id="14099-132">Because of this, if you suspect that any nodes in your environment may have drifted from the desired state of configuration, you can enact the same DSC configuration again to bring them back to the desired state.</span></span> <span data-ttu-id="14099-133">U hoeft het configuratie script niet te wijzigen om alleen de resources te adresseren waarvan de status is overplaatst van de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="14099-133">You do not need to modify the configuration script to address only those resources whose state has drifted from the desired state.</span></span>

<span data-ttu-id="14099-134">In het volgende voor beeld ziet u hoe u kunt controleren of de werkelijke status van de configuratie op een bepaald knoop punt is overgegaan van de laatste DSC-configuratie die is uitgevaardigd op het knoop punt.</span><span class="sxs-lookup"><span data-stu-id="14099-134">The following example shows how you can verify whether the actual state of configuration on a given node has drifted from the last DSC configuration enacted on the node.</span></span> <span data-ttu-id="14099-135">In dit voor beeld controleren we de configuratie van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="14099-135">In this example we are checking the configuration of the local computer.</span></span>

```powershell
$session = New-CimSession -ComputerName "localhost"
Test-DscConfiguration -CimSession $session
```

## <a name="built-in-dsc-resources"></a><span data-ttu-id="14099-136">INGEBOUWDE DSC-RESOURCES</span><span class="sxs-lookup"><span data-stu-id="14099-136">BUILT-IN DSC RESOURCES</span></span>

<span data-ttu-id="14099-137">U kunt de volgende ingebouwde bronnen gebruiken in uw configuratie scripts:</span><span class="sxs-lookup"><span data-stu-id="14099-137">You can use the following built-in resources in your configuration scripts:</span></span>

|<span data-ttu-id="14099-138">Naam</span><span class="sxs-lookup"><span data-stu-id="14099-138">Name</span></span>                  |<span data-ttu-id="14099-139">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="14099-139">Properties</span></span>                                         |
|----------------------|---------------------------------------------------|
|<span data-ttu-id="14099-140">Bestand</span><span class="sxs-lookup"><span data-stu-id="14099-140">File</span></span>                  |<span data-ttu-id="14099-141">{Doelpad, kenmerken, controlesom, inhoud...}</span><span class="sxs-lookup"><span data-stu-id="14099-141">{DestinationPath, Attributes, Checksum, Content...}</span></span>|
|<span data-ttu-id="14099-142">Archiveren</span><span class="sxs-lookup"><span data-stu-id="14099-142">Archive</span></span>               |<span data-ttu-id="14099-143">{Doel, pad, controlesom, referentie...}</span><span class="sxs-lookup"><span data-stu-id="14099-143">{Destination, Path, Checksum, Credential...}</span></span>       |
|<span data-ttu-id="14099-144">Omgeving</span><span class="sxs-lookup"><span data-stu-id="14099-144">Environment</span></span>           |<span data-ttu-id="14099-145">{Name, DependsOn, verzeker, Path...}</span><span class="sxs-lookup"><span data-stu-id="14099-145">{Name, DependsOn, Ensure, Path...}</span></span>                 |
|<span data-ttu-id="14099-146">Groep</span><span class="sxs-lookup"><span data-stu-id="14099-146">Group</span></span>                 |<span data-ttu-id="14099-147">{GroupName, referentie, DependsOn, beschrijving...}</span><span class="sxs-lookup"><span data-stu-id="14099-147">{GroupName, Credential, DependsOn, Description...}</span></span> |
|<span data-ttu-id="14099-148">Logboek</span><span class="sxs-lookup"><span data-stu-id="14099-148">Log</span></span>                   |<span data-ttu-id="14099-149">{Message, DependsOn, PsDscRunAsCredential}</span><span class="sxs-lookup"><span data-stu-id="14099-149">{Message, DependsOn, PsDscRunAsCredential}</span></span>         |
|<span data-ttu-id="14099-150">Pakket</span><span class="sxs-lookup"><span data-stu-id="14099-150">Package</span></span>               |<span data-ttu-id="14099-151">{Name, Path, ProductId, arguments...}</span><span class="sxs-lookup"><span data-stu-id="14099-151">{Name, Path, ProductId, Arguments...}</span></span>              |
|<span data-ttu-id="14099-152">Register</span><span class="sxs-lookup"><span data-stu-id="14099-152">Registry</span></span>              |<span data-ttu-id="14099-153">{Sleutel, waardenaam, DependsOn, zorg ervoor dat...}</span><span class="sxs-lookup"><span data-stu-id="14099-153">{Key, ValueName, DependsOn, Ensure...}</span></span>             |
|<span data-ttu-id="14099-154">Script</span><span class="sxs-lookup"><span data-stu-id="14099-154">Script</span></span>                |<span data-ttu-id="14099-155">{GetScript, SetScript, TestScript, referentie...}</span><span class="sxs-lookup"><span data-stu-id="14099-155">{GetScript, SetScript, TestScript, Credential...}</span></span>  |
|<span data-ttu-id="14099-156">Service</span><span class="sxs-lookup"><span data-stu-id="14099-156">Service</span></span>               |<span data-ttu-id="14099-157">{Naam, BuiltInAccount, referentie, afhankelijkheden...}</span><span class="sxs-lookup"><span data-stu-id="14099-157">{Name, BuiltInAccount, Credential, Dependencies...}</span></span>|
|<span data-ttu-id="14099-158">Gebruiker</span><span class="sxs-lookup"><span data-stu-id="14099-158">User</span></span>                  |<span data-ttu-id="14099-159">{UserName, DependsOn, Description, disabled...}</span><span class="sxs-lookup"><span data-stu-id="14099-159">{UserName, DependsOn, Description, Disabled...}</span></span>    |
|<span data-ttu-id="14099-160">WaitForAll</span><span class="sxs-lookup"><span data-stu-id="14099-160">WaitForAll</span></span>            |<span data-ttu-id="14099-161">{Nodenaam, ResourceName, DependsOn, PsDscRunAsC...}</span><span class="sxs-lookup"><span data-stu-id="14099-161">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span></span>|
|<span data-ttu-id="14099-162">WaitForAny</span><span class="sxs-lookup"><span data-stu-id="14099-162">WaitForAny</span></span>            |<span data-ttu-id="14099-163">{Nodenaam, ResourceName, DependsOn, PsDscRunAsC...}</span><span class="sxs-lookup"><span data-stu-id="14099-163">{NodeName, ResourceName, DependsOn, PsDscRunAsC...}</span></span>|
|<span data-ttu-id="14099-164">WaitForSome</span><span class="sxs-lookup"><span data-stu-id="14099-164">WaitForSome</span></span>           |<span data-ttu-id="14099-165">{NodeCount, nodenaam, ResourceName, DependsOn...}</span><span class="sxs-lookup"><span data-stu-id="14099-165">{NodeCount, NodeName, ResourceName, DependsOn...}</span></span>  |
|<span data-ttu-id="14099-166">WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="14099-166">WindowsFeature</span></span>        |<span data-ttu-id="14099-167">{Naam, referentie, DependsOn, zorg ervoor dat...}</span><span class="sxs-lookup"><span data-stu-id="14099-167">{Name, Credential, DependsOn, Ensure...}</span></span>           |
|<span data-ttu-id="14099-168">WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="14099-168">WindowsOptionalFeature</span></span>|<span data-ttu-id="14099-169">{Name, DependsOn, verzeker u ervan, LogLevel...}</span><span class="sxs-lookup"><span data-stu-id="14099-169">{Name, DependsOn, Ensure, LogLevel...}</span></span>             |
|<span data-ttu-id="14099-170">WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="14099-170">WindowsProcess</span></span>        |<span data-ttu-id="14099-171">{Arguments, pad, referentie, DependsOn...}</span><span class="sxs-lookup"><span data-stu-id="14099-171">{Arguments, Path, Credential, DependsOn...}</span></span>        |

<span data-ttu-id="14099-172">Voer de cmdlet uit om een lijst met beschik bare DSC-resources op uw systeem te verkrijgen `Get-DscResource` .</span><span class="sxs-lookup"><span data-stu-id="14099-172">To get a list of available DSC resources on your system, run the `Get-DscResource` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="14099-173">In Power shell-versies onder 7,0 worden `Get-DscResource` op klassen gebaseerde DSC-resources niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="14099-173">In PowerShell versions below 7.0, `Get-DscResource` does not find Class based DSC resources.</span></span>

<span data-ttu-id="14099-174">In het voor beeld in dit onderwerp ziet u hoe u de bestands-en WindowsFeature-resources gebruikt.</span><span class="sxs-lookup"><span data-stu-id="14099-174">The example in this topic demonstrates how to use the File and WindowsFeature resources.</span></span> <span data-ttu-id="14099-175">Als u alle eigenschappen wilt weer geven die u met een resource kunt gebruiken, plaatst u de cursor in het sleutel woord resource (bijvoorbeeld bestand) in het configuratie script in Power shell ISE, houdt u <kbd>CTRL</kbd> + <kbd>spatie balk</kbd> ingedrukt.</span><span class="sxs-lookup"><span data-stu-id="14099-175">To see all properties that you can use with a resource, insert the cursor in the resource keyword (for example, File) within your configuration script in PowerShell ISE, hold down <kbd>CTRL</kbd>+<kbd>SPACEBAR</kbd></span></span>

## <a name="find-more-resources"></a><span data-ttu-id="14099-176">MEER BRONNEN ZOEKEN</span><span class="sxs-lookup"><span data-stu-id="14099-176">FIND MORE RESOURCES</span></span>

<span data-ttu-id="14099-177">U kunt een groot aantal andere beschik bare DSC-resources downloaden, installeren en lezen die zijn gemaakt door de gebruikers community van Power shell en DSC, en door micro soft.</span><span class="sxs-lookup"><span data-stu-id="14099-177">You can download, install, and learn about many other available DSC resources that have been created by the PowerShell and DSC user community, and by Microsoft.</span></span> <span data-ttu-id="14099-178">Ga naar de [PowerShell Gallery](https://www.powershellgallery.com/) om te bladeren en meer te weten te komen over beschik bare DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="14099-178">Visit the [PowerShell Gallery](https://www.powershellgallery.com/) to browse and learn about available DSC resources.</span></span>

## <a name="see-also"></a><span data-ttu-id="14099-179">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="14099-179">SEE ALSO</span></span>

[<span data-ttu-id="14099-180">Overzicht van desired state Configuration van Power shell</span><span class="sxs-lookup"><span data-stu-id="14099-180">PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)

[<span data-ttu-id="14099-181">Ingebouwde Power shell desired state Configuration-resources</span><span class="sxs-lookup"><span data-stu-id="14099-181">Built-In PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/resources)

[<span data-ttu-id="14099-182">Aangepaste Power shell-configuratie bronnen voor desired state bouwen</span><span class="sxs-lookup"><span data-stu-id="14099-182">Build Custom PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/authoringResource)
