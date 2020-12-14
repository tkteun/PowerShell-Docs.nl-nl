---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: a24d66aa1ce9e353e41cc7a686ee9f910a7106fc
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889256"
---
# <span data-ttu-id="73e03-102">Find-Command</span><span class="sxs-lookup"><span data-stu-id="73e03-102">Find-Command</span></span>

## <span data-ttu-id="73e03-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="73e03-103">SYNOPSIS</span></span>
<span data-ttu-id="73e03-104">Hiermee vindt u Power shell-opdrachten in modules.</span><span class="sxs-lookup"><span data-stu-id="73e03-104">Finds PowerShell commands in modules.</span></span>

## <span data-ttu-id="73e03-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="73e03-105">SYNTAX</span></span>

### <span data-ttu-id="73e03-106">Alles</span><span class="sxs-lookup"><span data-stu-id="73e03-106">All</span></span>

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="73e03-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="73e03-107">DESCRIPTION</span></span>

<span data-ttu-id="73e03-108">`Find-Command`Met de cmdlet vindt u Power shell-opdrachten zoals cmdlets, aliassen, functies en werk stromen.</span><span class="sxs-lookup"><span data-stu-id="73e03-108">The `Find-Command` cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="73e03-109">`Find-Command` Hiermee worden modules in geregistreerde opslag plaatsen gezocht.</span><span class="sxs-lookup"><span data-stu-id="73e03-109">`Find-Command` searches modules in registered repositories.</span></span>

<span data-ttu-id="73e03-110">Voor elke opdracht die door wordt gevonden `Find-Command` , wordt een **PSGetCommandInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="73e03-110">For each command found by `Find-Command`, a **PSGetCommandInfo** object is returned.</span></span> <span data-ttu-id="73e03-111">Het **PSGetCommandInfo** -object kan via de pijp lijn naar de cmdlet worden verzonden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="73e03-111">The **PSGetCommandInfo** object can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="73e03-112">`Install-Module` installeert de module die de opdracht bevat.</span><span class="sxs-lookup"><span data-stu-id="73e03-112">`Install-Module` installs the module that contains the command.</span></span>

## <span data-ttu-id="73e03-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="73e03-113">EXAMPLES</span></span>

### <span data-ttu-id="73e03-114">Voor beeld 1: alle opdrachten in een opgegeven opslag plaats zoeken</span><span class="sxs-lookup"><span data-stu-id="73e03-114">Example 1: Find all commands in a specified repository</span></span>

<span data-ttu-id="73e03-115">De `Find-Command` cmdlet zoekt een geregistreerde opslag plaats voor modules.</span><span class="sxs-lookup"><span data-stu-id="73e03-115">The `Find-Command` cmdlet searches a registered repository for modules.</span></span>

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

<span data-ttu-id="73e03-116">`Find-Command` gebruikt de para meter **opslagplaats** om de naam van de geregistreerde opslag plaats op te geven.</span><span class="sxs-lookup"><span data-stu-id="73e03-116">`Find-Command` uses the **Repository** parameter to specify a registered repository's name.</span></span> <span data-ttu-id="73e03-117">De objecten worden naar beneden verzonden via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="73e03-117">The objects are sent down the pipeline.</span></span> <span data-ttu-id="73e03-118">`Select-Object` de objecten worden ontvangen en de **eerste** para meter wordt gebruikt om de eerste tien resultaten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="73e03-118">`Select-Object` receives the objects and uses the **First** parameter to display the first 10 results.</span></span>

### <span data-ttu-id="73e03-119">Voor beeld 2: een opdracht op naam zoeken</span><span class="sxs-lookup"><span data-stu-id="73e03-119">Example 2: Find a command by name</span></span>

<span data-ttu-id="73e03-120">`Find-Command` kan de naam van een opdracht gebruiken om de module in een opslag plaats te vinden.</span><span class="sxs-lookup"><span data-stu-id="73e03-120">`Find-Command` can use the name of a command to locate the module in a repository.</span></span> <span data-ttu-id="73e03-121">Het is mogelijk dat een opdracht naam bestaat in meerdere **ModuleNames**.</span><span class="sxs-lookup"><span data-stu-id="73e03-121">It's possible that a command name exists in multiple **ModuleNames**.</span></span>

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

<span data-ttu-id="73e03-122">`Find-Command` gebruikt de para meter **opslagplaats** om te zoeken in de **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="73e03-122">`Find-Command` uses the **Repository** parameter to search the **PSGallery**.</span></span> <span data-ttu-id="73e03-123">De para meter **name** specificeert de opdracht **Get-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="73e03-123">The **Name** parameter specifies the command **Get-TargetResource**.</span></span>

### <span data-ttu-id="73e03-124">Voor beeld 3: opdrachten zoeken op naam en de module installeren</span><span class="sxs-lookup"><span data-stu-id="73e03-124">Example 3: Find commands by name and install the module</span></span>

<span data-ttu-id="73e03-125">`Find-Command` kan de opdracht en module vinden en vervolgens het object naar verzenden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="73e03-125">`Find-Command` can locate the command and module, then send the object to `Install-Module`.</span></span> <span data-ttu-id="73e03-126">Als een opdracht is opgenomen in meerdere modules, gebruikt u de `Find-Command` module cmdlets **-name** para meter.</span><span class="sxs-lookup"><span data-stu-id="73e03-126">If a command is included in multiple modules, use the `Find-Command` cmdlets **Module-Name** parameter.</span></span>
<span data-ttu-id="73e03-127">Anders kunnen modules geïnstalleerd zijn die u niet wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="73e03-127">Otherwise, modules might be installed that you didn't want to install.</span></span>

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

<span data-ttu-id="73e03-128">`Find-Command` maakt gebruik van de para meter **name** om de opdracht **Get-TargetResource** op te geven.</span><span class="sxs-lookup"><span data-stu-id="73e03-128">`Find-Command` uses the **Name** parameter to specify the command **Get-TargetResource**.</span></span> <span data-ttu-id="73e03-129">De **opslagplaats** parameter zoekt in de **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="73e03-129">The **Repository** parameter searches the **PSGallery**.</span></span> <span data-ttu-id="73e03-130">De para meter **module** naam geeft de module op die u wilt installeren, **SystemLocaleDsc**.</span><span class="sxs-lookup"><span data-stu-id="73e03-130">The **ModuleName** parameter specifies the module you want to install, **SystemLocaleDsc**.</span></span> <span data-ttu-id="73e03-131">Het object wordt naar de pijp lijn verzonden `Install-Module` en de module is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="73e03-131">The object is sent down the pipeline to `Install-Module` and the module is installed.</span></span> <span data-ttu-id="73e03-132">Nadat de installatie is voltooid, kunt u gebruiken `Get-InstalledModule` om de resultaten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="73e03-132">After the installation finishes, you can use `Get-InstalledModule` to display the results.</span></span>

### <span data-ttu-id="73e03-133">Voor beeld 4: een opdracht zoeken en de module opslaan</span><span class="sxs-lookup"><span data-stu-id="73e03-133">Example 4: Find a command and save its module</span></span>

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

<span data-ttu-id="73e03-134">`Find-Command` maakt gebruik van de para meters **name** en **repository** om te zoeken naar de opdracht **invoke-ScriptAnalyzer** in de **PSGallery** -opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="73e03-134">`Find-Command` uses the **Name** and **Repository** parameters to search for the command **Invoke-ScriptAnalyzer** in the **PSGallery** repository.</span></span> <span data-ttu-id="73e03-135">Het object wordt naar de pijp lijn verzonden `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="73e03-135">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="73e03-136">De para meter **Path** bepaalt de locatie waar de module moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="73e03-136">The **Path** parameter determines the location to save the module.</span></span> <span data-ttu-id="73e03-137">**Uitgebreid** is een optionele para meter, maar de status uitvoer wordt weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="73e03-137">**Verbose** is an optional parameter, but displays status output in the PowerShell console.</span></span> <span data-ttu-id="73e03-138">De uitgebreide uitvoer is handig voor het oplossen van problemen.</span><span class="sxs-lookup"><span data-stu-id="73e03-138">The verbose output is beneficial for troubleshooting.</span></span>

## <span data-ttu-id="73e03-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73e03-139">PARAMETERS</span></span>

### <span data-ttu-id="73e03-140">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="73e03-140">-AllowPrerelease</span></span>

<span data-ttu-id="73e03-141">Bevat modules die zijn gemarkeerd als een prerelease in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="73e03-141">Includes modules marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="73e03-142">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="73e03-142">-AllVersions</span></span>

<span data-ttu-id="73e03-143">Geeft aan dat met deze cmdlet alle versies van een module worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="73e03-143">Indicates that this cmdlet gets all versions of a module.</span></span>

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

### <span data-ttu-id="73e03-144">-Filter</span><span class="sxs-lookup"><span data-stu-id="73e03-144">-Filter</span></span>

<span data-ttu-id="73e03-145">Hiermee zoekt u naar modules op basis van de zoek syntaxis van de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="73e03-145">Finds modules based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="73e03-146">Geef bijvoorbeeld woorden op waarnaar u wilt zoeken in de  eigenschappen van module **naam en beschrijving** .</span><span class="sxs-lookup"><span data-stu-id="73e03-146">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="73e03-147">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="73e03-147">-MaximumVersion</span></span>

<span data-ttu-id="73e03-148">Hiermee geeft u de maximum versie van de module op die in resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="73e03-148">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="73e03-149">De **MaximumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="73e03-149">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="73e03-150">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="73e03-150">-MinimumVersion</span></span>

<span data-ttu-id="73e03-151">Hiermee geeft u de minimale versie van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="73e03-151">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="73e03-152">De **MinimumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="73e03-152">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="73e03-153">-Module naam</span><span class="sxs-lookup"><span data-stu-id="73e03-153">-ModuleName</span></span>

<span data-ttu-id="73e03-154">Hiermee geeft u de naam van een module op die moet worden gezocht naar opdrachten.</span><span class="sxs-lookup"><span data-stu-id="73e03-154">Specifies the name of a module to search for commands.</span></span> <span data-ttu-id="73e03-155">De standaard instelling is alle modules.</span><span class="sxs-lookup"><span data-stu-id="73e03-155">The default is all modules.</span></span>

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

### <span data-ttu-id="73e03-156">-Name</span><span class="sxs-lookup"><span data-stu-id="73e03-156">-Name</span></span>

<span data-ttu-id="73e03-157">Hiermee geeft u de naam van de opdracht waarnaar moet worden gezocht in een opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="73e03-157">Specifies the command name to search for in a repository.</span></span> <span data-ttu-id="73e03-158">Gebruik komma's om een matrix van opdracht namen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="73e03-158">Use commas to separate an array of command names.</span></span>

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

### <span data-ttu-id="73e03-159">-Proxy</span><span class="sxs-lookup"><span data-stu-id="73e03-159">-Proxy</span></span>

<span data-ttu-id="73e03-160">Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="73e03-160">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="73e03-161">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="73e03-161">-ProxyCredential</span></span>

<span data-ttu-id="73e03-162">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="73e03-162">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="73e03-163">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="73e03-163">-Repository</span></span>

<span data-ttu-id="73e03-164">Hiermee geeft u de opslag plaats om naar opdrachten te zoeken.</span><span class="sxs-lookup"><span data-stu-id="73e03-164">Specifies the repository to search for commands.</span></span> <span data-ttu-id="73e03-165">Gebruik komma's om een matrix van de namen van opslag plaatsen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="73e03-165">Use commas to separate an array of repository names.</span></span> <span data-ttu-id="73e03-166">De standaard instelling is alle opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="73e03-166">The default is all repositories.</span></span>

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

### <span data-ttu-id="73e03-167">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="73e03-167">-RequiredVersion</span></span>

<span data-ttu-id="73e03-168">Hiermee geeft u de versie van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="73e03-168">Specifies the version of the module to include in the results.</span></span>

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

### <span data-ttu-id="73e03-169">-Tag</span><span class="sxs-lookup"><span data-stu-id="73e03-169">-Tag</span></span>

<span data-ttu-id="73e03-170">Hiermee geeft u labels op waarmee modules in een opslag plaats worden gecategoriseerd.</span><span class="sxs-lookup"><span data-stu-id="73e03-170">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="73e03-171">Gebruik komma's om een matrix met tags te scheiden.</span><span class="sxs-lookup"><span data-stu-id="73e03-171">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="73e03-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73e03-172">CommonParameters</span></span>

<span data-ttu-id="73e03-173">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="73e03-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73e03-174">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73e03-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="73e03-175">INVOER</span><span class="sxs-lookup"><span data-stu-id="73e03-175">INPUTS</span></span>

## <span data-ttu-id="73e03-176">UITVOER</span><span class="sxs-lookup"><span data-stu-id="73e03-176">OUTPUTS</span></span>

### <span data-ttu-id="73e03-177">PSGetCommandInfo</span><span class="sxs-lookup"><span data-stu-id="73e03-177">PSGetCommandInfo</span></span>

<span data-ttu-id="73e03-178">`Find-Command` Hiermee wordt een **PSGetCommandInfo** -object uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="73e03-178">`Find-Command` outputs a **PSGetCommandInfo** object.</span></span>

## <span data-ttu-id="73e03-179">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="73e03-179">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73e03-180">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="73e03-180">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="73e03-181">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="73e03-181">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="73e03-182">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="73e03-182">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="73e03-183">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73e03-183">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="73e03-184">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="73e03-184">RELATED LINKS</span></span>

[<span data-ttu-id="73e03-185">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="73e03-185">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="73e03-186">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="73e03-186">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="73e03-187">Save-Module</span><span class="sxs-lookup"><span data-stu-id="73e03-187">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="73e03-188">Select-Object</span><span class="sxs-lookup"><span data-stu-id="73e03-188">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="73e03-189">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="73e03-189">Uninstall-Module</span></span>](Uninstall-Module.md)
