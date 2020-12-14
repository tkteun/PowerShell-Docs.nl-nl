---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: a84dee14872ad5a7d0f7bac8e0057dc527855074
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890396"
---
# <span data-ttu-id="e053b-102">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="e053b-102">Find-RoleCapability</span></span>

## <span data-ttu-id="e053b-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e053b-103">SYNOPSIS</span></span>
<span data-ttu-id="e053b-104">Hiermee vindt u functie mogelijkheden in modules.</span><span class="sxs-lookup"><span data-stu-id="e053b-104">Finds role capabilities in modules.</span></span>

## <span data-ttu-id="e053b-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e053b-105">SYNTAX</span></span>

### <span data-ttu-id="e053b-106">Alles</span><span class="sxs-lookup"><span data-stu-id="e053b-106">All</span></span>

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="e053b-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e053b-107">DESCRIPTION</span></span>

<span data-ttu-id="e053b-108">De `Find-RoleCapability` cmdlet zoekt geregistreerde opslag plaatsen om de Power shell-functies en-modules te vinden.</span><span class="sxs-lookup"><span data-stu-id="e053b-108">The `Find-RoleCapability` cmdlet searches registered repositories to find PowerShell role capabilities and modules.</span></span>

<span data-ttu-id="e053b-109">Voor elke functie die door wordt gevonden `Find-RoleCapability` , wordt een **PSGetRoleCapabilityInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e053b-109">For each role capability found by `Find-RoleCapability`, a **PSGetRoleCapabilityInfo** object is returned.</span></span> <span data-ttu-id="e053b-110">**PSGetRoleCapabilityInfo** -objecten kunnen naar de `Install-Module` of cmdlets in de pijp lijn worden verzonden `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="e053b-110">**PSGetRoleCapabilityInfo** objects can be sent down the pipeline to the `Install-Module` or `Save-Module` cmdlets.</span></span>

<span data-ttu-id="e053b-111">Met Power shell-functie functies definieert u welke opdrachten en toepassingen beschikbaar zijn voor een gebruiker op een JEA-eind punt (genoeg aan het beheer).</span><span class="sxs-lookup"><span data-stu-id="e053b-111">PowerShell role capabilities define which commands and applications are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="e053b-112">Functie mogelijkheden worden gedefinieerd door bestanden met een `.psrc` extensie.</span><span class="sxs-lookup"><span data-stu-id="e053b-112">Role capabilities are defined by files with a `.psrc` extension.</span></span>

## <span data-ttu-id="e053b-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e053b-113">EXAMPLES</span></span>

### <span data-ttu-id="e053b-114">Voor beeld 1: functie mogelijkheden zoeken</span><span class="sxs-lookup"><span data-stu-id="e053b-114">Example 1: Find role capabilities</span></span>

<span data-ttu-id="e053b-115">`Find-RoleCapability` Hiermee vindt u functie mogelijkheden in elke geregistreerde opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e053b-115">`Find-RoleCapability` finds role capabilities in each registered repository.</span></span> <span data-ttu-id="e053b-116">Als u een specifieke opslag plaats wilt doorzoeken, gebruikt u de para meter **opslagplaats** .</span><span class="sxs-lookup"><span data-stu-id="e053b-116">To search a specific repository, use the **Repository** parameter.</span></span>

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="e053b-117">Voor beeld 2: functie mogelijkheden op naam zoeken</span><span class="sxs-lookup"><span data-stu-id="e053b-117">Example 2: Find role capabilities by name</span></span>

<span data-ttu-id="e053b-118">`Find-RoleCapability` Hiermee zoekt u functie mogelijkheden op naam.</span><span class="sxs-lookup"><span data-stu-id="e053b-118">`Find-RoleCapability` finds role capabilities by name.</span></span> <span data-ttu-id="e053b-119">Gebruik komma's om een matrix met namen van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="e053b-119">Use commas to separate an array of names.</span></span>

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="e053b-120">Voor beeld 3: de module van een functie mogelijkheid zoeken en opslaan</span><span class="sxs-lookup"><span data-stu-id="e053b-120">Example 3: Find and save a role capability's module</span></span>

<span data-ttu-id="e053b-121">De `Find-RoleCapability` cmdlet vindt een functie en verzendt het object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e053b-121">The `Find-RoleCapability` cmdlet finds a role capability and sends the object down the pipeline.</span></span>
<span data-ttu-id="e053b-122">`Save-Module` Hiermee wordt de module van de functie capaciteit opgeslagen in een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="e053b-122">`Save-Module` saves the role capability's module to a file system.</span></span> <span data-ttu-id="e053b-123">`Get-ChildItem` Hiermee wordt de inhoud van de map van de module weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e053b-123">`Get-ChildItem` displays the contents of the module's directory.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

<span data-ttu-id="e053b-124">`Find-RoleCapability` maakt gebruik van de para meter **name** om de functie van **algemene Lev1** te specificeren.</span><span class="sxs-lookup"><span data-stu-id="e053b-124">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="e053b-125">Het object wordt via de pijp lijn verzonden.</span><span class="sxs-lookup"><span data-stu-id="e053b-125">The object is sent down the pipeline.</span></span> <span data-ttu-id="e053b-126">`Save-Module` gebruikt de para meter **Path** voor de locatie van het bestands systeem om de module op te slaan.</span><span class="sxs-lookup"><span data-stu-id="e053b-126">`Save-Module` uses the **Path** parameter for the file system location to save the module.</span></span> <span data-ttu-id="e053b-127">Nadat de module is opgeslagen, `Get-ChildItem` geeft u het **pad** van de module op en geeft u de inhoud van de map van de **JeaExamples** -module weer.</span><span class="sxs-lookup"><span data-stu-id="e053b-127">After the module is saved, `Get-ChildItem` specifies the module's **Path** and displays the contents of the **JeaExamples** module's directory.</span></span>

### <span data-ttu-id="e053b-128">Voor beeld 4: de module van een functie mogelijkheid zoeken en installeren</span><span class="sxs-lookup"><span data-stu-id="e053b-128">Example 4: Find and install a role capability's module</span></span>

<span data-ttu-id="e053b-129">`Find-RoleCapability` zoekt de module en verzendt het object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e053b-129">`Find-RoleCapability` finds the module and sends the object down the pipeline.</span></span> <span data-ttu-id="e053b-130">`Install-Module` installeert de module.</span><span class="sxs-lookup"><span data-stu-id="e053b-130">`Install-Module` installs the module.</span></span> <span data-ttu-id="e053b-131">Na de installatie, gebruikt `Get-InstalledModule` u om de resultaten te bekijken.</span><span class="sxs-lookup"><span data-stu-id="e053b-131">After the installation, use `Get-InstalledModule` to see the results.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

<span data-ttu-id="e053b-132">`Find-RoleCapability` maakt gebruik van de para meter **name** om de functie van **algemene Lev1** te specificeren.</span><span class="sxs-lookup"><span data-stu-id="e053b-132">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="e053b-133">Het object wordt via de pijp lijn verzonden.</span><span class="sxs-lookup"><span data-stu-id="e053b-133">The object is sent down the pipeline.</span></span> <span data-ttu-id="e053b-134">`Install-Module` maakt gebruik van de para meter **uitgebreid** om status berichten tijdens de installatie weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e053b-134">`Install-Module` uses the **Verbose** parameter to display status messages during the installation.</span></span> <span data-ttu-id="e053b-135">Nadat de installatie is voltooid, wordt `Get-InstalledModule` met de uitvoer bevestigd dat de **JeaExamples** -module is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e053b-135">After the install is finished, the `Get-InstalledModule` output confirms that the **JeaExamples** module was installed.</span></span>

## <span data-ttu-id="e053b-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e053b-136">PARAMETERS</span></span>

### <span data-ttu-id="e053b-137">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="e053b-137">-AllowPrerelease</span></span>

<span data-ttu-id="e053b-138">Bevat resources die zijn gemarkeerd als een prerelease in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="e053b-138">Includes resources marked as a prerelease in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-139">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="e053b-139">-AllVersions</span></span>

<span data-ttu-id="e053b-140">Geeft aan dat met deze cmdlet alle versies van een module worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="e053b-140">Indicates that this cmdlet gets all versions of a module.</span></span> <span data-ttu-id="e053b-141">Met de para meter **AllVersions** worden alle beschik bare versies van een module weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e053b-141">The **AllVersions** parameter displays each of a module's available versions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-142">-Filter</span><span class="sxs-lookup"><span data-stu-id="e053b-142">-Filter</span></span>

<span data-ttu-id="e053b-143">Zoekt bronnen op basis van de zoek syntaxis van de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="e053b-143">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="e053b-144">Geef bijvoorbeeld woorden op waarnaar u wilt zoeken in de  eigenschappen van module **naam en beschrijving** .</span><span class="sxs-lookup"><span data-stu-id="e053b-144">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-145">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e053b-145">-MaximumVersion</span></span>

<span data-ttu-id="e053b-146">Hiermee geeft u de maximum versie van de module op die in resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="e053b-146">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="e053b-147">De **MaximumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="e053b-147">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-148">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e053b-148">-MinimumVersion</span></span>

<span data-ttu-id="e053b-149">Hiermee geeft u de minimale versie van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="e053b-149">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="e053b-150">De **MinimumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="e053b-150">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-151">-Module naam</span><span class="sxs-lookup"><span data-stu-id="e053b-151">-ModuleName</span></span>

<span data-ttu-id="e053b-152">Hiermee geeft u de naam op van de module waarin u wilt zoeken naar functie mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="e053b-152">Specifies the name of the module in which to search for role capabilities.</span></span> <span data-ttu-id="e053b-153">De standaard instelling is alle modules.</span><span class="sxs-lookup"><span data-stu-id="e053b-153">The default is all modules.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-154">-Name</span><span class="sxs-lookup"><span data-stu-id="e053b-154">-Name</span></span>

<span data-ttu-id="e053b-155">Hiermee geeft u de naam van een functie mogelijkheid.</span><span class="sxs-lookup"><span data-stu-id="e053b-155">Specifies the name of a role capability.</span></span> <span data-ttu-id="e053b-156">De standaard waarde is alle functie mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="e053b-156">The default is all role capabilities.</span></span> <span data-ttu-id="e053b-157">Gebruik komma's om een matrix met resource namen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="e053b-157">Use commas to separate an array of resource names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-158">-Proxy</span><span class="sxs-lookup"><span data-stu-id="e053b-158">-Proxy</span></span>

<span data-ttu-id="e053b-159">Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="e053b-159">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-160">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="e053b-160">-ProxyCredential</span></span>

<span data-ttu-id="e053b-161">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven in de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="e053b-161">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-162">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="e053b-162">-Repository</span></span>

<span data-ttu-id="e053b-163">Hiermee geeft u een opslag plaats voor het zoeken naar functie mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="e053b-163">Specifies a repository to search for role capabilities.</span></span> <span data-ttu-id="e053b-164">Gebruik komma's om een matrix van de namen van opslag plaatsen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="e053b-164">Use commas to separate an array of repository names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-165">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e053b-165">-RequiredVersion</span></span>

<span data-ttu-id="e053b-166">Hiermee geeft u het exacte versie nummer van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="e053b-166">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="e053b-167">De **RequiredVersion** -en **MinimumVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="e053b-167">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-168">-Tag</span><span class="sxs-lookup"><span data-stu-id="e053b-168">-Tag</span></span>

<span data-ttu-id="e053b-169">Hiermee geeft u labels op waarmee modules in een opslag plaats worden gecategoriseerd.</span><span class="sxs-lookup"><span data-stu-id="e053b-169">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="e053b-170">Gebruik komma's om een matrix met tags te scheiden.</span><span class="sxs-lookup"><span data-stu-id="e053b-170">Use commas to separate an array of tags.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e053b-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e053b-171">CommonParameters</span></span>

<span data-ttu-id="e053b-172">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e053b-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e053b-173">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e053b-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e053b-174">INVOER</span><span class="sxs-lookup"><span data-stu-id="e053b-174">INPUTS</span></span>

### <span data-ttu-id="e053b-175">System. URI</span><span class="sxs-lookup"><span data-stu-id="e053b-175">System.Uri</span></span>

### <span data-ttu-id="e053b-176">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="e053b-176">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="e053b-177">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e053b-177">OUTPUTS</span></span>

### <span data-ttu-id="e053b-178">PSGetRoleCapabilityInfo</span><span class="sxs-lookup"><span data-stu-id="e053b-178">PSGetRoleCapabilityInfo</span></span>

<span data-ttu-id="e053b-179">De `Find-RoleCapability` cmdlet retourneert een **PSGetRoleCapabilityInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="e053b-179">The `Find-RoleCapability` cmdlet returns a **PSGetRoleCapabilityInfo** object.</span></span>

## <span data-ttu-id="e053b-180">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e053b-180">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e053b-181">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="e053b-181">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="e053b-182">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="e053b-182">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="e053b-183">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="e053b-183">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="e053b-184">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e053b-184">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="e053b-185">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e053b-185">RELATED LINKS</span></span>

[<span data-ttu-id="e053b-186">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="e053b-186">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="e053b-187">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="e053b-187">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="e053b-188">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="e053b-188">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="e053b-189">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="e053b-189">New-PSRoleCapabilityFile</span></span>](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[<span data-ttu-id="e053b-190">Save-Module</span><span class="sxs-lookup"><span data-stu-id="e053b-190">Save-Module</span></span>](Save-Module.md)
