---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: 00b3bacbb82ee2316896581d2aa9c5998bd8d448
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249489"
---
# <span data-ttu-id="7b3b6-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="7b3b6-103">Find-RoleCapability</span></span>

## <span data-ttu-id="7b3b6-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7b3b6-104">SYNOPSIS</span></span>
<span data-ttu-id="7b3b6-105">Hiermee vindt u functie mogelijkheden in modules.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-105">Finds role capabilities in modules.</span></span>

## <span data-ttu-id="7b3b6-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7b3b6-106">SYNTAX</span></span>

### <span data-ttu-id="7b3b6-107">Alles</span><span class="sxs-lookup"><span data-stu-id="7b3b6-107">All</span></span>

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="7b3b6-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7b3b6-108">DESCRIPTION</span></span>

<span data-ttu-id="7b3b6-109">De `Find-RoleCapability` cmdlet zoekt geregistreerde opslag plaatsen om de Power shell-functies en-modules te vinden.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-109">The `Find-RoleCapability` cmdlet searches registered repositories to find PowerShell role capabilities and modules.</span></span>

<span data-ttu-id="7b3b6-110">Voor elke functie die door wordt gevonden `Find-RoleCapability` , wordt een **PSGetRoleCapabilityInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-110">For each role capability found by `Find-RoleCapability`, a **PSGetRoleCapabilityInfo** object is returned.</span></span> <span data-ttu-id="7b3b6-111">**PSGetRoleCapabilityInfo** -objecten kunnen naar de `Install-Module` of cmdlets in de pijp lijn worden verzonden `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="7b3b6-111">**PSGetRoleCapabilityInfo** objects can be sent down the pipeline to the `Install-Module` or `Save-Module` cmdlets.</span></span>

<span data-ttu-id="7b3b6-112">Met Power shell-functie functies definieert u welke opdrachten en toepassingen beschikbaar zijn voor een gebruiker op een JEA-eind punt (genoeg aan het beheer).</span><span class="sxs-lookup"><span data-stu-id="7b3b6-112">PowerShell role capabilities define which commands and applications are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="7b3b6-113">Functie mogelijkheden worden gedefinieerd door bestanden met een `.psrc` extensie.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-113">Role capabilities are defined by files with a `.psrc` extension.</span></span>

## <span data-ttu-id="7b3b6-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7b3b6-114">EXAMPLES</span></span>

### <span data-ttu-id="7b3b6-115">Voor beeld 1: functie mogelijkheden zoeken</span><span class="sxs-lookup"><span data-stu-id="7b3b6-115">Example 1: Find role capabilities</span></span>

<span data-ttu-id="7b3b6-116">`Find-RoleCapability` Hiermee vindt u functie mogelijkheden in elke geregistreerde opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-116">`Find-RoleCapability` finds role capabilities in each registered repository.</span></span> <span data-ttu-id="7b3b6-117">Als u een specifieke opslag plaats wilt doorzoeken, gebruikt u de para meter **opslagplaats** .</span><span class="sxs-lookup"><span data-stu-id="7b3b6-117">To search a specific repository, use the **Repository** parameter.</span></span>

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

### <span data-ttu-id="7b3b6-118">Voor beeld 2: functie mogelijkheden op naam zoeken</span><span class="sxs-lookup"><span data-stu-id="7b3b6-118">Example 2: Find role capabilities by name</span></span>

<span data-ttu-id="7b3b6-119">`Find-RoleCapability` Hiermee zoekt u functie mogelijkheden op naam.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-119">`Find-RoleCapability` finds role capabilities by name.</span></span> <span data-ttu-id="7b3b6-120">Gebruik komma's om een matrix met namen van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-120">Use commas to separate an array of names.</span></span>

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="7b3b6-121">Voor beeld 3: de module van een functie mogelijkheid zoeken en opslaan</span><span class="sxs-lookup"><span data-stu-id="7b3b6-121">Example 3: Find and save a role capability's module</span></span>

<span data-ttu-id="7b3b6-122">De `Find-RoleCapability` cmdlet vindt een functie en verzendt het object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-122">The `Find-RoleCapability` cmdlet finds a role capability and sends the object down the pipeline.</span></span>
<span data-ttu-id="7b3b6-123">`Save-Module` Hiermee wordt de module van de functie capaciteit opgeslagen in een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-123">`Save-Module` saves the role capability's module to a file system.</span></span> <span data-ttu-id="7b3b6-124">`Get-ChildItem` Hiermee wordt de inhoud van de map van de module weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-124">`Get-ChildItem` displays the contents of the module's directory.</span></span>

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

<span data-ttu-id="7b3b6-125">`Find-RoleCapability` maakt gebruik van de para meter **name** om de functie van **algemene Lev1** te specificeren.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-125">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="7b3b6-126">Het object wordt via de pijp lijn verzonden.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-126">The object is sent down the pipeline.</span></span> <span data-ttu-id="7b3b6-127">`Save-Module` gebruikt de para meter **Path** voor de locatie van het bestands systeem om de module op te slaan.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-127">`Save-Module` uses the **Path** parameter for the file system location to save the module.</span></span> <span data-ttu-id="7b3b6-128">Nadat de module is opgeslagen, `Get-ChildItem` geeft u het **pad** van de module op en geeft u de inhoud van de map van de **JeaExamples** -module weer.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-128">After the module is saved, `Get-ChildItem` specifies the module's **Path** and displays the contents of the **JeaExamples** module's directory.</span></span>

### <span data-ttu-id="7b3b6-129">Voor beeld 4: de module van een functie mogelijkheid zoeken en installeren</span><span class="sxs-lookup"><span data-stu-id="7b3b6-129">Example 4: Find and install a role capability's module</span></span>

<span data-ttu-id="7b3b6-130">`Find-RoleCapability` zoekt de module en verzendt het object omlaag in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-130">`Find-RoleCapability` finds the module and sends the object down the pipeline.</span></span> <span data-ttu-id="7b3b6-131">`Install-Module` installeert de module.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-131">`Install-Module` installs the module.</span></span> <span data-ttu-id="7b3b6-132">Na de installatie, gebruikt `Get-InstalledModule` u om de resultaten te bekijken.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-132">After the installation, use `Get-InstalledModule` to see the results.</span></span>

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

<span data-ttu-id="7b3b6-133">`Find-RoleCapability` maakt gebruik van de para meter **name** om de functie van **algemene Lev1** te specificeren.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-133">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="7b3b6-134">Het object wordt via de pijp lijn verzonden.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-134">The object is sent down the pipeline.</span></span> <span data-ttu-id="7b3b6-135">`Install-Module` maakt gebruik van de para meter **uitgebreid** om status berichten tijdens de installatie weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-135">`Install-Module` uses the **Verbose** parameter to display status messages during the installation.</span></span> <span data-ttu-id="7b3b6-136">Nadat de installatie is voltooid, wordt `Get-InstalledModule` met de uitvoer bevestigd dat de **JeaExamples** -module is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-136">After the install is finished, the `Get-InstalledModule` output confirms that the **JeaExamples** module was installed.</span></span>

## <span data-ttu-id="7b3b6-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7b3b6-137">PARAMETERS</span></span>

### <span data-ttu-id="7b3b6-138">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="7b3b6-138">-AllowPrerelease</span></span>

<span data-ttu-id="7b3b6-139">Bevat resources die zijn gemarkeerd als een prerelease in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-139">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="7b3b6-140">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="7b3b6-140">-AllVersions</span></span>

<span data-ttu-id="7b3b6-141">Geeft aan dat met deze cmdlet alle versies van een module worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-141">Indicates that this cmdlet gets all versions of a module.</span></span> <span data-ttu-id="7b3b6-142">Met de para meter **AllVersions** worden alle beschik bare versies van een module weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-142">The **AllVersions** parameter displays each of a module's available versions.</span></span>

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

### <span data-ttu-id="7b3b6-143">-Filter</span><span class="sxs-lookup"><span data-stu-id="7b3b6-143">-Filter</span></span>

<span data-ttu-id="7b3b6-144">Zoekt bronnen op basis van de zoek syntaxis van de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-144">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="7b3b6-145">Geef bijvoorbeeld woorden op waarnaar u wilt zoeken in de **ModuleName** eigenschappen van module **naam en beschrijving** .</span><span class="sxs-lookup"><span data-stu-id="7b3b6-145">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="7b3b6-146">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="7b3b6-146">-MaximumVersion</span></span>

<span data-ttu-id="7b3b6-147">Hiermee geeft u de maximum versie van de module op die in resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-147">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="7b3b6-148">De **MaximumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-148">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="7b3b6-149">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="7b3b6-149">-MinimumVersion</span></span>

<span data-ttu-id="7b3b6-150">Hiermee geeft u de minimale versie van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-150">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="7b3b6-151">De **MinimumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-151">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="7b3b6-152">-Module naam</span><span class="sxs-lookup"><span data-stu-id="7b3b6-152">-ModuleName</span></span>

<span data-ttu-id="7b3b6-153">Hiermee geeft u de naam op van de module waarin u wilt zoeken naar functie mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-153">Specifies the name of the module in which to search for role capabilities.</span></span> <span data-ttu-id="7b3b6-154">De standaard instelling is alle modules.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-154">The default is all modules.</span></span>

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

### <span data-ttu-id="7b3b6-155">-Name</span><span class="sxs-lookup"><span data-stu-id="7b3b6-155">-Name</span></span>

<span data-ttu-id="7b3b6-156">Hiermee geeft u de naam van een functie mogelijkheid.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-156">Specifies the name of a role capability.</span></span> <span data-ttu-id="7b3b6-157">De standaard waarde is alle functie mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-157">The default is all role capabilities.</span></span> <span data-ttu-id="7b3b6-158">Gebruik komma's om een matrix met resource namen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-158">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="7b3b6-159">-Proxy</span><span class="sxs-lookup"><span data-stu-id="7b3b6-159">-Proxy</span></span>

<span data-ttu-id="7b3b6-160">Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-160">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="7b3b6-161">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="7b3b6-161">-ProxyCredential</span></span>

<span data-ttu-id="7b3b6-162">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven in de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-162">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="7b3b6-163">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="7b3b6-163">-Repository</span></span>

<span data-ttu-id="7b3b6-164">Hiermee geeft u een opslag plaats voor het zoeken naar functie mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-164">Specifies a repository to search for role capabilities.</span></span> <span data-ttu-id="7b3b6-165">Gebruik komma's om een matrix van de namen van opslag plaatsen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-165">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="7b3b6-166">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="7b3b6-166">-RequiredVersion</span></span>

<span data-ttu-id="7b3b6-167">Hiermee geeft u het exacte versie nummer van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-167">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="7b3b6-168">De **RequiredVersion** -en **MinimumVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-168">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="7b3b6-169">-Tag</span><span class="sxs-lookup"><span data-stu-id="7b3b6-169">-Tag</span></span>

<span data-ttu-id="7b3b6-170">Hiermee geeft u labels op waarmee modules in een opslag plaats worden gecategoriseerd.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-170">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="7b3b6-171">Gebruik komma's om een matrix met tags te scheiden.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-171">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="7b3b6-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7b3b6-172">CommonParameters</span></span>

<span data-ttu-id="7b3b6-173">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7b3b6-174">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7b3b6-175">INVOER</span><span class="sxs-lookup"><span data-stu-id="7b3b6-175">INPUTS</span></span>

### <span data-ttu-id="7b3b6-176">System. URI</span><span class="sxs-lookup"><span data-stu-id="7b3b6-176">System.Uri</span></span>

### <span data-ttu-id="7b3b6-177">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="7b3b6-177">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="7b3b6-178">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7b3b6-178">OUTPUTS</span></span>

### <span data-ttu-id="7b3b6-179">PSGetRoleCapabilityInfo</span><span class="sxs-lookup"><span data-stu-id="7b3b6-179">PSGetRoleCapabilityInfo</span></span>

<span data-ttu-id="7b3b6-180">De `Find-RoleCapability` cmdlet retourneert een **PSGetRoleCapabilityInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="7b3b6-180">The `Find-RoleCapability` cmdlet returns a **PSGetRoleCapabilityInfo** object.</span></span>

## <span data-ttu-id="7b3b6-181">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7b3b6-181">NOTES</span></span>

## <span data-ttu-id="7b3b6-182">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7b3b6-182">RELATED LINKS</span></span>

[<span data-ttu-id="7b3b6-183">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="7b3b6-183">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="7b3b6-184">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="7b3b6-184">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="7b3b6-185">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="7b3b6-185">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="7b3b6-186">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="7b3b6-186">New-PSRoleCapabilityFile</span></span>](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[<span data-ttu-id="7b3b6-187">Save-Module</span><span class="sxs-lookup"><span data-stu-id="7b3b6-187">Save-Module</span></span>](Save-Module.md)
