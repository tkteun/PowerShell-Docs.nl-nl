---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: e1cb814d349d6b77885ebaaf176a7c3153d93eb5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889367"
---
# <span data-ttu-id="6e7b6-102">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="6e7b6-102">Find-DscResource</span></span>

## <span data-ttu-id="6e7b6-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6e7b6-103">SYNOPSIS</span></span>
<span data-ttu-id="6e7b6-104">Zoekt naar desired state Configuration (DSC)-resources.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-104">Finds Desired State Configuration (DSC) resources.</span></span>

## <span data-ttu-id="6e7b6-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6e7b6-105">SYNTAX</span></span>

### <span data-ttu-id="6e7b6-106">Alles</span><span class="sxs-lookup"><span data-stu-id="6e7b6-106">All</span></span>

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="6e7b6-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6e7b6-107">DESCRIPTION</span></span>

<span data-ttu-id="6e7b6-108">De `Find-DscResource` cmdlet zoekt geregistreerde opslag plaatsen om DSC-resources in modules te vinden.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-108">The `Find-DscResource` cmdlet searches registered repositories to find DSC resources contained in modules.</span></span> <span data-ttu-id="6e7b6-109">Standaard `Find-DscResource` doorzoekt alle geregistreerde opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-109">By default `Find-DscResource` searches all registered repositories.</span></span>

<span data-ttu-id="6e7b6-110">Voor elke module die door wordt gevonden `Find-DscResource` , wordt een **PSGetDscResourceInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-110">For each module found by `Find-DscResource`, a **PSGetDscResourceInfo** object is returned.</span></span>
<span data-ttu-id="6e7b6-111">**PSGetDscResourceInfo** -objecten kunnen naar de-cmdlet worden verzonden door de pijp lijn `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="6e7b6-111">**PSGetDscResourceInfo** objects can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="6e7b6-112">`Install-Module` installeert de module.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-112">`Install-Module` installs the module.</span></span>

## <span data-ttu-id="6e7b6-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6e7b6-113">EXAMPLES</span></span>

### <span data-ttu-id="6e7b6-114">Voor beeld 1: alle DSC-resources zoeken</span><span class="sxs-lookup"><span data-stu-id="6e7b6-114">Example 1: Find all DSC resources</span></span>

<span data-ttu-id="6e7b6-115">`Find-DscResource` Hiermee worden DSC-resources uit de geregistreerde opslag plaatsen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-115">`Find-DscResource` returns DSC resources from registered repositories.</span></span> <span data-ttu-id="6e7b6-116">Als u een specifieke opslag plaats wilt doorzoeken, gebruikt u de para meter **opslagplaats** .</span><span class="sxs-lookup"><span data-stu-id="6e7b6-116">To search a specific repository, use the **Repository** parameter.</span></span>

```powershell
Find-DscResource
```

```Output
Name                           Version    ModuleName                     Repository
----                           -------    ----------                     ----------
Carbon_Privilege               2.8.1      Carbon                         PSGallery
Carbon_ScheduledTask           2.8.1      Carbon                         PSGallery
Carbon_Service                 2.8.1      Carbon                         PSGallery
PackageManagement              1.4        PackageManagement              PSGallery
PackageManagementSource        1.4        PackageManagement              PSGallery
PSModule                       2.1.4      PowerShellGet                  PSGallery
PSRepository                   2.1.4      PowerShellGet                  PSGallery
xArchive                       8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xDSCWebService                 8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xEnvironment                   8.7.0.0    xPSDesiredStateConfiguration   PSGallery
```

### <span data-ttu-id="6e7b6-117">Voor beeld 2: een DSC-resource op naam zoeken</span><span class="sxs-lookup"><span data-stu-id="6e7b6-117">Example 2: Find a DSC resource by name</span></span>

<span data-ttu-id="6e7b6-118">`Find-DscResource` DSC-resources zoeken op naam.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-118">`Find-DscResource` locates DSC resources by name.</span></span> <span data-ttu-id="6e7b6-119">Gebruik komma's om een matrix met resource namen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-119">Use commas to separate an array of resource names.</span></span>

```powershell
Find-DscResource -Name xWebsite, xWebApplication, xWebSiteDefaults
```

```Output
Name               Version    ModuleName            Repository
----               -------    ----------            ----------
xWebApplication    2.6.0.0    xWebAdministration    PSGallery
xWebsite           2.6.0.0    xWebAdministration    PSGallery
xWebSiteDefaults   2.6.0.0    xWebAdministration    PSGallery
```

<span data-ttu-id="6e7b6-120">`Find-DscResource` maakt gebruik van de para meter **name** om de opgegeven matrix van DSC-resources te zoeken.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-120">`Find-DscResource` uses the **Name** parameter to find the specified array of DSC resources.</span></span>

### <span data-ttu-id="6e7b6-121">Voor beeld 3: een DSC-resource zoeken en installeren</span><span class="sxs-lookup"><span data-stu-id="6e7b6-121">Example 3: Find a DSC resource and install it</span></span>

<span data-ttu-id="6e7b6-122">`Find-DscResource` zoekt een DSC-resource en stuurt het object omlaag in de pijp lijn die moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-122">`Find-DscResource` locates a DSC resource and sends the object down the pipeline to be installed.</span></span>
<span data-ttu-id="6e7b6-123">Na de installatie gebruikt `Get-InstalledModule` u om de resultaten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-123">After the installation, use `Get-InstalledModule` to view the results.</span></span>

<span data-ttu-id="6e7b6-124">Er kunnen meerdere resources van dezelfde module naar de pijp lijn worden verzonden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="6e7b6-124">Multiple resources from the same module can be sent down the pipeline to the `Install-Module`.</span></span>
<span data-ttu-id="6e7b6-125">`Install-Module` probeert de module alleen eenmaal te installeren.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-125">`Install-Module` attempts to only install the module once.</span></span>

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

<span data-ttu-id="6e7b6-126">`Find-DscResource` maakt gebruik van de para meter **name** om de resource met de naam **xWebsite** te zoeken.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-126">`Find-DscResource` uses the **Name** parameter to find the resource named **xWebsite**.</span></span> <span data-ttu-id="6e7b6-127">Het object wordt vanuit de pijp lijn naar de `Install-Module` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-127">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="6e7b6-128">`Install-Module` Hiermee installeert u de **xWebAdministration** -module voor de resource.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-128">`Install-Module` installs the **xWebAdministration** module for the resource.</span></span>

### <span data-ttu-id="6e7b6-129">Voor beeld 4: alle DSC-resources in een module zoeken</span><span class="sxs-lookup"><span data-stu-id="6e7b6-129">Example 4: Find all DSC resources in a module</span></span>

<span data-ttu-id="6e7b6-130">`Find-DscResource` Hiermee worden alle DSC-resources in een opgegeven module gevonden.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-130">`Find-DscResource` finds all the DSC resources contained in a specified module.</span></span> <span data-ttu-id="6e7b6-131">Standaard wordt de huidige versie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-131">By default, the current version is displayed.</span></span> <span data-ttu-id="6e7b6-132">Als u andere versies wilt weer geven, gebruikt u de para meters **AllVersions** of **RequiredVersions** .</span><span class="sxs-lookup"><span data-stu-id="6e7b6-132">To display other versions, use the **AllVersions** or **RequiredVersions** parameters.</span></span>

```powershell
Find-DscResource -ModuleName xWebAdministration
```

```Output
Name                                Version    ModuleName              Repository
----                                -------    ----------              ----------
WebApplicationHandler               2.6.0.0    xWebAdministration      PSGallery
xIisFeatureDelegation               2.6.0.0    xWebAdministration      PSGallery
xIisHandler                         2.6.0.0    xWebAdministration      PSGallery
xIisLogging                         2.6.0.0    xWebAdministration      PSGallery
```

<span data-ttu-id="6e7b6-133">`Find-DscResource` maakt gebruik van de para meter **module** om de **xWebAdministration** op te geven en de DSC-resources in de module te vinden.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-133">`Find-DscResource` uses the **ModuleName** parameter to specify the **xWebAdministration** and find the DSC resources contained in the module.</span></span> <span data-ttu-id="6e7b6-134">De huidige versie van elke resource wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-134">The current version of each resource is displayed.</span></span>

### <span data-ttu-id="6e7b6-135">Voor beeld 5: een DSC-resource zoeken op label en vereiste versie</span><span class="sxs-lookup"><span data-stu-id="6e7b6-135">Example 5: Find a DSC resource by tag and required version</span></span>

<span data-ttu-id="6e7b6-136">DSC-resources kunnen worden gevonden met behulp van de para meters **tag** en **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-136">DSC resources can be located using the parameters **Tag** and **RequiredVersion**.</span></span> <span data-ttu-id="6e7b6-137">**Tag** geeft de huidige versie weer van elke resource die het opgegeven label bevat in de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-137">**Tag** displays the current version of every resource that contains the specified tag in the repository.</span></span>
<span data-ttu-id="6e7b6-138">**RequiredVersion** moet de  para meter voor de module **naam** hebben en de para meter name is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-138">**RequiredVersion** needs the **ModuleName** parameter and the **Name** parameter is optional.</span></span> <span data-ttu-id="6e7b6-139">De para meters **name en naam** **module** beperken de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-139">The **Name** and **ModuleName** parameters limit the output.</span></span> <span data-ttu-id="6e7b6-140">Gebruik de para meter **AllVersions** om de beschik bare versies van een DSC-resource weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-140">Use the **AllVersions** parameter to display a DSC resource's available versions.</span></span>

```powershell
Find-DscResource -ModuleName xWebAdministration -Tag DSC -RequiredVersion 1.20
```

```output
Name                    Version    ModuleName             Repository
----                    -------    ----------             ----------
xIisFeatureDelegation   1.20.0.0   xWebAdministration     PSGallery
xIisHandler             1.20.0.0   xWebAdministration     PSGallery
xIisLogging             1.20.0.0   xWebAdministration     PSGallery
xIisMimeTypeMapping     1.20.0.0   xWebAdministration     PSGallery
```

### <span data-ttu-id="6e7b6-141">Voor beeld 6: een resource zoeken met behulp van een filter</span><span class="sxs-lookup"><span data-stu-id="6e7b6-141">Example 6: Find a resource by using a filter</span></span>

<span data-ttu-id="6e7b6-142">`Find-DscResource` Hiermee worden alle resources gevonden en de **filter** parameter gebruikt om de resultaten op basis van het **domein** op te geven.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-142">`Find-DscResource` finds all resources and uses the **Filter** parameter to specify the results by **Domain**.</span></span> <span data-ttu-id="6e7b6-143">De **filter** parameter zoekt de filter waarde in de beschrijving of module naam van het object.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-143">The **Filter** parameter finds the filter value in the object's description or module name.</span></span> <span data-ttu-id="6e7b6-144">Gebruik de `Select-Object` cmdlet om de eigenschappen van een object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-144">Use the `Select-Object` cmdlet to view an object's properties.</span></span>

```powershell
Find-DscResource -Filter Domain
```

```output
Name                    Version    ModuleName                 Repository
----                    -------    ----------                 ---------
xComputer               4.1.0.0    xComputerManagement        PSGallery
Computer                6.4.0.0    ComputerManagementDsc      PSGallery
xDSCDomainjoin          1.1        xDSCDomainjoin             PSGallery
xDisk                   1.0        xDisk                      PSGallery
xDSCFirewall            1.6.21     xDSCFirewall               PSGallery
dmAwsTagInstance        1.0.1      domainAwsDSCResources      PSGallery
```

## <span data-ttu-id="6e7b6-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6e7b6-145">PARAMETERS</span></span>

### <span data-ttu-id="6e7b6-146">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="6e7b6-146">-AllowPrerelease</span></span>

<span data-ttu-id="6e7b6-147">Bevat resources die zijn gemarkeerd als een prerelease in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-147">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="6e7b6-148">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="6e7b6-148">-AllVersions</span></span>

<span data-ttu-id="6e7b6-149">Met de para meter **AllVersions** worden alle beschik bare versies van een DSC-resource weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-149">The **AllVersions** parameter displays each of a DSC resource's available versions.</span></span> <span data-ttu-id="6e7b6-150">U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion**, **MaximumVersion** of **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="6e7b6-150">You can't use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="6e7b6-151">-Filter</span><span class="sxs-lookup"><span data-stu-id="6e7b6-151">-Filter</span></span>

<span data-ttu-id="6e7b6-152">Zoekt bronnen op basis van de zoek syntaxis van de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-152">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="6e7b6-153">Geef bijvoorbeeld woorden op waarnaar u wilt zoeken in de  eigenschappen van module **naam en beschrijving** .</span><span class="sxs-lookup"><span data-stu-id="6e7b6-153">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="6e7b6-154">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="6e7b6-154">-MaximumVersion</span></span>

<span data-ttu-id="6e7b6-155">Hiermee geeft u de maximum versie van de resource op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-155">Specifies the maximum version of the resource to include in results.</span></span> <span data-ttu-id="6e7b6-156">De **MaximumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-156">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="6e7b6-157">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="6e7b6-157">-MinimumVersion</span></span>

<span data-ttu-id="6e7b6-158">Hiermee geeft u de minimale versie van de resource op die moet worden meegenomen in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-158">Specifies the minimum version of the resource to include in results.</span></span> <span data-ttu-id="6e7b6-159">De **MinimumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-159">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="6e7b6-160">-Module naam</span><span class="sxs-lookup"><span data-stu-id="6e7b6-160">-ModuleName</span></span>

<span data-ttu-id="6e7b6-161">Hiermee geeft u een module die de DSC-resource bevat.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-161">Specifies a module that contains the DSC resource.</span></span>

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

### <span data-ttu-id="6e7b6-162">-Name</span><span class="sxs-lookup"><span data-stu-id="6e7b6-162">-Name</span></span>

<span data-ttu-id="6e7b6-163">Hiermee geeft u de naam van een resource.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-163">Specifies the name of a resource.</span></span> <span data-ttu-id="6e7b6-164">De standaard waarde is alle resources.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-164">The default is all resources.</span></span> <span data-ttu-id="6e7b6-165">Gebruik komma's om een matrix met resource namen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-165">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="6e7b6-166">-Proxy</span><span class="sxs-lookup"><span data-stu-id="6e7b6-166">-Proxy</span></span>

<span data-ttu-id="6e7b6-167">Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-167">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="6e7b6-168">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="6e7b6-168">-ProxyCredential</span></span>

<span data-ttu-id="6e7b6-169">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven in de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-169">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="6e7b6-170">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="6e7b6-170">-Repository</span></span>

<span data-ttu-id="6e7b6-171">Hiermee geeft u een opslag plaats voor het zoeken naar resources op.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-171">Specifies a repository to search for resources.</span></span> <span data-ttu-id="6e7b6-172">Gebruik komma's om een matrix van de namen van opslag plaatsen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-172">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="6e7b6-173">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6e7b6-173">-RequiredVersion</span></span>

<span data-ttu-id="6e7b6-174">Hiermee geeft u het exacte versie nummer van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-174">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="6e7b6-175">De **RequiredVersion** -en **MinimumVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-175">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="6e7b6-176">-Tag</span><span class="sxs-lookup"><span data-stu-id="6e7b6-176">-Tag</span></span>

<span data-ttu-id="6e7b6-177">Hiermee geeft u labels op waarmee modules in een opslag plaats worden gecategoriseerd.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-177">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="6e7b6-178">Gebruik komma's om een matrix met tags te scheiden.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-178">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="6e7b6-179">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6e7b6-179">CommonParameters</span></span>

<span data-ttu-id="6e7b6-180">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-180">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6e7b6-181">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-181">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6e7b6-182">INVOER</span><span class="sxs-lookup"><span data-stu-id="6e7b6-182">INPUTS</span></span>

## <span data-ttu-id="6e7b6-183">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6e7b6-183">OUTPUTS</span></span>

### <span data-ttu-id="6e7b6-184">PSGetDscResourceInfo</span><span class="sxs-lookup"><span data-stu-id="6e7b6-184">PSGetDscResourceInfo</span></span>

<span data-ttu-id="6e7b6-185">`Find-DscResource` retourneert een **PSGetDscResourceInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-185">`Find-DscResource` returns a **PSGetDscResourceInfo** object.</span></span>

## <span data-ttu-id="6e7b6-186">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6e7b6-186">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6e7b6-187">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-187">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="6e7b6-188">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-188">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="6e7b6-189">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="6e7b6-189">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="6e7b6-190">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6e7b6-190">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="6e7b6-191">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6e7b6-191">RELATED LINKS</span></span>

[<span data-ttu-id="6e7b6-192">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="6e7b6-192">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="6e7b6-193">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="6e7b6-193">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="6e7b6-194">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="6e7b6-194">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="6e7b6-195">Select-Object</span><span class="sxs-lookup"><span data-stu-id="6e7b6-195">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="6e7b6-196">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="6e7b6-196">Uninstall-Module</span></span>](Uninstall-Module.md)
