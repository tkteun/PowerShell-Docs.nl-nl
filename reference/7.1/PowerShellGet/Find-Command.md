---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: 1cd86a1c9abe6c8a4af9f68ed17ea1876ff1bd20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250881"
---
# <span data-ttu-id="c468b-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="c468b-103">Find-Command</span></span>

## <span data-ttu-id="c468b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c468b-104">SYNOPSIS</span></span>
<span data-ttu-id="c468b-105">Hiermee vindt u Power shell-opdrachten in modules.</span><span class="sxs-lookup"><span data-stu-id="c468b-105">Finds PowerShell commands in modules.</span></span>

## <span data-ttu-id="c468b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c468b-106">SYNTAX</span></span>

### <span data-ttu-id="c468b-107">Alles</span><span class="sxs-lookup"><span data-stu-id="c468b-107">All</span></span>

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="c468b-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c468b-108">DESCRIPTION</span></span>

<span data-ttu-id="c468b-109">`Find-Command`Met de cmdlet vindt u Power shell-opdrachten zoals cmdlets, aliassen, functies en werk stromen.</span><span class="sxs-lookup"><span data-stu-id="c468b-109">The `Find-Command` cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="c468b-110">`Find-Command` Hiermee worden modules in geregistreerde opslag plaatsen gezocht.</span><span class="sxs-lookup"><span data-stu-id="c468b-110">`Find-Command` searches modules in registered repositories.</span></span>

<span data-ttu-id="c468b-111">Voor elke opdracht die door wordt gevonden `Find-Command` , wordt een **PSGetCommandInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c468b-111">For each command found by `Find-Command`, a **PSGetCommandInfo** object is returned.</span></span> <span data-ttu-id="c468b-112">Het **PSGetCommandInfo** -object kan via de pijp lijn naar de cmdlet worden verzonden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="c468b-112">The **PSGetCommandInfo** object can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="c468b-113">`Install-Module` installeert de module die de opdracht bevat.</span><span class="sxs-lookup"><span data-stu-id="c468b-113">`Install-Module` installs the module that contains the command.</span></span>

## <span data-ttu-id="c468b-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c468b-114">EXAMPLES</span></span>

### <span data-ttu-id="c468b-115">Voor beeld 1: alle opdrachten in een opgegeven opslag plaats zoeken</span><span class="sxs-lookup"><span data-stu-id="c468b-115">Example 1: Find all commands in a specified repository</span></span>

<span data-ttu-id="c468b-116">De `Find-Command` cmdlet zoekt een geregistreerde opslag plaats voor modules.</span><span class="sxs-lookup"><span data-stu-id="c468b-116">The `Find-Command` cmdlet searches a registered repository for modules.</span></span>

```powershell
Find-Command -Repository PSGallery | Select-Object -First 10
```

```output
Name                                Version    ModuleName          Repository
----                                -------    ----------          ----------
Disable-AzureRmDataCollection       5.8.3      AzureRM.profile     PSGallery
Disable-AzureRmContextAutosave      5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmDataCollection        5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmContextAutosave       5.8.3      AzureRM.profile     PSGallery
Remove-AzureRmEnvironment           5.8.3      AzureRM.profile     PSGallery
Get-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Set-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Add-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Get-AzureRmSubscription             5.8.3      AzureRM.profile     PSGallery
Connect-AzureRmAccount              5.8.3      AzureRM.profile     PSGallery
```

<span data-ttu-id="c468b-117">`Find-Command` gebruikt de para meter **opslagplaats** om de naam van de geregistreerde opslag plaats op te geven.</span><span class="sxs-lookup"><span data-stu-id="c468b-117">`Find-Command` uses the **Repository** parameter to specify a registered repository's name.</span></span> <span data-ttu-id="c468b-118">De objecten worden naar beneden verzonden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c468b-118">The objects are sent down the pipeline.</span></span> <span data-ttu-id="c468b-119">`Select-Object` de objecten worden ontvangen en de **eerste** para meter wordt gebruikt om de eerste tien resultaten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c468b-119">`Select-Object` receives the objects and uses the **First** parameter to display the first 10 results.</span></span>

### <span data-ttu-id="c468b-120">Voor beeld 2: een opdracht op naam zoeken</span><span class="sxs-lookup"><span data-stu-id="c468b-120">Example 2: Find a command by name</span></span>

<span data-ttu-id="c468b-121">`Find-Command` kan de naam van een opdracht gebruiken om de module in een opslag plaats te vinden.</span><span class="sxs-lookup"><span data-stu-id="c468b-121">`Find-Command` can use the name of a command to locate the module in a repository.</span></span> <span data-ttu-id="c468b-122">Het is mogelijk dat een opdracht naam bestaat in meerdere **ModuleNames**.</span><span class="sxs-lookup"><span data-stu-id="c468b-122">It's possible that a command name exists in multiple **ModuleNames**.</span></span>

```powershell
Find-Command -Repository PSGallery -Name Get-TargetResource
```

```Output
Name                  Version    ModuleName                      Repository
----                  -------    ----------                      ----------
Get-TargetResource    3.1.0.0    xPowerShellExecutionPolicy      PSGallery
Get-TargetResource    1.0.0      xInternetExplorerHomePage       PSGallery
Get-TargetResource    1.2.0.0    SystemLocaleDsc                 PSGallery
```

<span data-ttu-id="c468b-123">`Find-Command` gebruikt de para meter **opslagplaats** om te zoeken in de **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="c468b-123">`Find-Command` uses the **Repository** parameter to search the **PSGallery**.</span></span> <span data-ttu-id="c468b-124">De para meter **name** specificeert de opdracht **Get-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="c468b-124">The **Name** parameter specifies the command **Get-TargetResource**.</span></span>

### <span data-ttu-id="c468b-125">Voor beeld 3: opdrachten zoeken op naam en de module installeren</span><span class="sxs-lookup"><span data-stu-id="c468b-125">Example 3: Find commands by name and install the module</span></span>

<span data-ttu-id="c468b-126">`Find-Command` kan de opdracht en module vinden en vervolgens het object naar verzenden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="c468b-126">`Find-Command` can locate the command and module, then send the object to `Install-Module`.</span></span> <span data-ttu-id="c468b-127">Als een opdracht is opgenomen in meerdere modules, gebruikt u de `Find-Command` module cmdlets **-name** para meter.</span><span class="sxs-lookup"><span data-stu-id="c468b-127">If a command is included in multiple modules, use the `Find-Command` cmdlets **Module-Name** parameter.</span></span>
<span data-ttu-id="c468b-128">Anders kunnen modules geïnstalleerd zijn die u niet wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="c468b-128">Otherwise, modules might be installed that you didn't want to install.</span></span>

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

<span data-ttu-id="c468b-129">`Find-Command` maakt gebruik van de para meter **name** om de opdracht **Get-TargetResource** op te geven.</span><span class="sxs-lookup"><span data-stu-id="c468b-129">`Find-Command` uses the **Name** parameter to specify the command **Get-TargetResource**.</span></span> <span data-ttu-id="c468b-130">De **opslagplaats** parameter zoekt in de **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="c468b-130">The **Repository** parameter searches the **PSGallery**.</span></span> <span data-ttu-id="c468b-131">De para meter **module** naam geeft de module op die u wilt installeren, **SystemLocaleDsc**.</span><span class="sxs-lookup"><span data-stu-id="c468b-131">The **ModuleName** parameter specifies the module you want to install, **SystemLocaleDsc**.</span></span> <span data-ttu-id="c468b-132">Het object wordt naar de pijp lijn verzonden `Install-Module` en de module is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c468b-132">The object is sent down the pipeline to `Install-Module` and the module is installed.</span></span> <span data-ttu-id="c468b-133">Nadat de installatie is voltooid, kunt u gebruiken `Get-InstalledModule` om de resultaten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c468b-133">After the installation finishes, you can use `Get-InstalledModule` to display the results.</span></span>

### <span data-ttu-id="c468b-134">Voor beeld 4: een opdracht zoeken en de module opslaan</span><span class="sxs-lookup"><span data-stu-id="c468b-134">Example 4: Find a command and save its module</span></span>

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

<span data-ttu-id="c468b-135">`Find-Command` maakt gebruik van de para meters **name** en **repository** om te zoeken naar de opdracht **invoke-ScriptAnalyzer** in de **PSGallery** -opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="c468b-135">`Find-Command` uses the **Name** and **Repository** parameters to search for the command **Invoke-ScriptAnalyzer** in the **PSGallery** repository.</span></span> <span data-ttu-id="c468b-136">Het object wordt naar de pijp lijn verzonden `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="c468b-136">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="c468b-137">De para meter **Path** bepaalt de locatie waar de module moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c468b-137">The **Path** parameter determines the location to save the module.</span></span> <span data-ttu-id="c468b-138">**Uitgebreid** is een optionele para meter, maar de status uitvoer wordt weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="c468b-138">**Verbose** is an optional parameter, but displays status output in the PowerShell console.</span></span> <span data-ttu-id="c468b-139">De uitgebreide uitvoer is handig voor het oplossen van problemen.</span><span class="sxs-lookup"><span data-stu-id="c468b-139">The verbose output is beneficial for troubleshooting.</span></span>

## <span data-ttu-id="c468b-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c468b-140">PARAMETERS</span></span>

### <span data-ttu-id="c468b-141">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="c468b-141">-AllowPrerelease</span></span>

<span data-ttu-id="c468b-142">Bevat modules die zijn gemarkeerd als een prerelease in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="c468b-142">Includes modules marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="c468b-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="c468b-143">-AllVersions</span></span>

<span data-ttu-id="c468b-144">Geeft aan dat met deze cmdlet alle versies van een module worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c468b-144">Indicates that this cmdlet gets all versions of a module.</span></span>

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

### <span data-ttu-id="c468b-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="c468b-145">-Filter</span></span>

<span data-ttu-id="c468b-146">Hiermee zoekt u naar modules op basis van de zoek syntaxis van de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="c468b-146">Finds modules based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="c468b-147">Geef bijvoorbeeld woorden op waarnaar u wilt zoeken in de **ModuleName** eigenschappen van module **naam en beschrijving** .</span><span class="sxs-lookup"><span data-stu-id="c468b-147">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="c468b-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="c468b-148">-MaximumVersion</span></span>

<span data-ttu-id="c468b-149">Hiermee geeft u de maximum versie van de module op die in resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="c468b-149">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="c468b-150">De **MaximumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="c468b-150">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="c468b-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="c468b-151">-MinimumVersion</span></span>

<span data-ttu-id="c468b-152">Hiermee geeft u de minimale versie van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="c468b-152">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="c468b-153">De **MinimumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="c468b-153">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="c468b-154">-Module naam</span><span class="sxs-lookup"><span data-stu-id="c468b-154">-ModuleName</span></span>

<span data-ttu-id="c468b-155">Hiermee geeft u de naam van een module op die moet worden gezocht naar opdrachten.</span><span class="sxs-lookup"><span data-stu-id="c468b-155">Specifies the name of a module to search for commands.</span></span> <span data-ttu-id="c468b-156">De standaard instelling is alle modules.</span><span class="sxs-lookup"><span data-stu-id="c468b-156">The default is all modules.</span></span>

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

### <span data-ttu-id="c468b-157">-Name</span><span class="sxs-lookup"><span data-stu-id="c468b-157">-Name</span></span>

<span data-ttu-id="c468b-158">Hiermee geeft u de naam van de opdracht waarnaar moet worden gezocht in een opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="c468b-158">Specifies the command name to search for in a repository.</span></span> <span data-ttu-id="c468b-159">Gebruik komma's om een matrix van opdracht namen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="c468b-159">Use commas to separate an array of command names.</span></span>

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

### <span data-ttu-id="c468b-160">-Proxy</span><span class="sxs-lookup"><span data-stu-id="c468b-160">-Proxy</span></span>

<span data-ttu-id="c468b-161">Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="c468b-161">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="c468b-162">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="c468b-162">-ProxyCredential</span></span>

<span data-ttu-id="c468b-163">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="c468b-163">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="c468b-164">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="c468b-164">-Repository</span></span>

<span data-ttu-id="c468b-165">Hiermee geeft u de opslag plaats om naar opdrachten te zoeken.</span><span class="sxs-lookup"><span data-stu-id="c468b-165">Specifies the repository to search for commands.</span></span> <span data-ttu-id="c468b-166">Gebruik komma's om een matrix van de namen van opslag plaatsen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="c468b-166">Use commas to separate an array of repository names.</span></span> <span data-ttu-id="c468b-167">De standaard instelling is alle opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="c468b-167">The default is all repositories.</span></span>

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

### <span data-ttu-id="c468b-168">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c468b-168">-RequiredVersion</span></span>

<span data-ttu-id="c468b-169">Hiermee geeft u de versie van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="c468b-169">Specifies the version of the module to include in the results.</span></span>

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

### <span data-ttu-id="c468b-170">-Tag</span><span class="sxs-lookup"><span data-stu-id="c468b-170">-Tag</span></span>

<span data-ttu-id="c468b-171">Hiermee geeft u labels op waarmee modules in een opslag plaats worden gecategoriseerd.</span><span class="sxs-lookup"><span data-stu-id="c468b-171">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="c468b-172">Gebruik komma's om een matrix met tags te scheiden.</span><span class="sxs-lookup"><span data-stu-id="c468b-172">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="c468b-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c468b-173">CommonParameters</span></span>

<span data-ttu-id="c468b-174">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c468b-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c468b-175">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c468b-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c468b-176">INVOER</span><span class="sxs-lookup"><span data-stu-id="c468b-176">INPUTS</span></span>

## <span data-ttu-id="c468b-177">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c468b-177">OUTPUTS</span></span>

### <span data-ttu-id="c468b-178">PSGetCommandInfo</span><span class="sxs-lookup"><span data-stu-id="c468b-178">PSGetCommandInfo</span></span>

<span data-ttu-id="c468b-179">`Find-Command` Hiermee wordt een **PSGetCommandInfo** -object uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c468b-179">`Find-Command` outputs a **PSGetCommandInfo** object.</span></span>

## <span data-ttu-id="c468b-180">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c468b-180">NOTES</span></span>

## <span data-ttu-id="c468b-181">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c468b-181">RELATED LINKS</span></span>

[<span data-ttu-id="c468b-182">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="c468b-182">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="c468b-183">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="c468b-183">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="c468b-184">Save-Module</span><span class="sxs-lookup"><span data-stu-id="c468b-184">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="c468b-185">Select-Object</span><span class="sxs-lookup"><span data-stu-id="c468b-185">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="c468b-186">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="c468b-186">Uninstall-Module</span></span>](Uninstall-Module.md)

