---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: 9953a7912d29517249fa215b154c1dfae46585d1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250871"
---
# <span data-ttu-id="cddca-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="cddca-103">Find-DscResource</span></span>

## <span data-ttu-id="cddca-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cddca-104">SYNOPSIS</span></span>
<span data-ttu-id="cddca-105">Zoekt naar desired state Configuration (DSC)-resources.</span><span class="sxs-lookup"><span data-stu-id="cddca-105">Finds Desired State Configuration (DSC) resources.</span></span>

## <span data-ttu-id="cddca-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cddca-106">SYNTAX</span></span>

### <span data-ttu-id="cddca-107">Alles</span><span class="sxs-lookup"><span data-stu-id="cddca-107">All</span></span>

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="cddca-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cddca-108">DESCRIPTION</span></span>

<span data-ttu-id="cddca-109">De `Find-DscResource` cmdlet zoekt geregistreerde opslag plaatsen om DSC-resources in modules te vinden.</span><span class="sxs-lookup"><span data-stu-id="cddca-109">The `Find-DscResource` cmdlet searches registered repositories to find DSC resources contained in modules.</span></span> <span data-ttu-id="cddca-110">Standaard `Find-DscResource` doorzoekt alle geregistreerde opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="cddca-110">By default `Find-DscResource` searches all registered repositories.</span></span>

<span data-ttu-id="cddca-111">Voor elke module die door wordt gevonden `Find-DscResource` , wordt een **PSGetDscResourceInfo** -object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cddca-111">For each module found by `Find-DscResource`, a **PSGetDscResourceInfo** object is returned.</span></span>
<span data-ttu-id="cddca-112">**PSGetDscResourceInfo** -objecten kunnen naar de-cmdlet worden verzonden door de pijp lijn `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="cddca-112">**PSGetDscResourceInfo** objects can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="cddca-113">`Install-Module` installeert de module.</span><span class="sxs-lookup"><span data-stu-id="cddca-113">`Install-Module` installs the module.</span></span>

## <span data-ttu-id="cddca-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cddca-114">EXAMPLES</span></span>

### <span data-ttu-id="cddca-115">Voor beeld 1: alle DSC-resources zoeken</span><span class="sxs-lookup"><span data-stu-id="cddca-115">Example 1: Find all DSC resources</span></span>

<span data-ttu-id="cddca-116">`Find-DscResource` Hiermee worden DSC-resources uit de geregistreerde opslag plaatsen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cddca-116">`Find-DscResource` returns DSC resources from registered repositories.</span></span> <span data-ttu-id="cddca-117">Als u een specifieke opslag plaats wilt doorzoeken, gebruikt u de para meter **opslagplaats** .</span><span class="sxs-lookup"><span data-stu-id="cddca-117">To search a specific repository, use the **Repository** parameter.</span></span>

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

### <span data-ttu-id="cddca-118">Voor beeld 2: een DSC-resource op naam zoeken</span><span class="sxs-lookup"><span data-stu-id="cddca-118">Example 2: Find a DSC resource by name</span></span>

<span data-ttu-id="cddca-119">`Find-DscResource` DSC-resources zoeken op naam.</span><span class="sxs-lookup"><span data-stu-id="cddca-119">`Find-DscResource` locates DSC resources by name.</span></span> <span data-ttu-id="cddca-120">Gebruik komma's om een matrix met resource namen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="cddca-120">Use commas to separate an array of resource names.</span></span>

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

<span data-ttu-id="cddca-121">`Find-DscResource` maakt gebruik van de para meter **name** om de opgegeven matrix van DSC-resources te zoeken.</span><span class="sxs-lookup"><span data-stu-id="cddca-121">`Find-DscResource` uses the **Name** parameter to find the specified array of DSC resources.</span></span>

### <span data-ttu-id="cddca-122">Voor beeld 3: een DSC-resource zoeken en installeren</span><span class="sxs-lookup"><span data-stu-id="cddca-122">Example 3: Find a DSC resource and install it</span></span>

<span data-ttu-id="cddca-123">`Find-DscResource` zoekt een DSC-resource en stuurt het object omlaag in de pijp lijn die moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="cddca-123">`Find-DscResource` locates a DSC resource and sends the object down the pipeline to be installed.</span></span>
<span data-ttu-id="cddca-124">Na de installatie gebruikt `Get-InstalledModule` u om de resultaten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cddca-124">After the installation, use `Get-InstalledModule` to view the results.</span></span>

<span data-ttu-id="cddca-125">Er kunnen meerdere resources van dezelfde module naar de pijp lijn worden verzonden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="cddca-125">Multiple resources from the same module can be sent down the pipeline to the `Install-Module`.</span></span>
<span data-ttu-id="cddca-126">`Install-Module` probeert de module alleen eenmaal te installeren.</span><span class="sxs-lookup"><span data-stu-id="cddca-126">`Install-Module` attempts to only install the module once.</span></span>

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

<span data-ttu-id="cddca-127">`Find-DscResource` maakt gebruik van de para meter **name** om de resource met de naam **xWebsite** te zoeken.</span><span class="sxs-lookup"><span data-stu-id="cddca-127">`Find-DscResource` uses the **Name** parameter to find the resource named **xWebsite**.</span></span> <span data-ttu-id="cddca-128">Het object wordt vanuit de pijp lijn naar de `Install-Module` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="cddca-128">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="cddca-129">`Install-Module` Hiermee installeert u de **xWebAdministration** -module voor de resource.</span><span class="sxs-lookup"><span data-stu-id="cddca-129">`Install-Module` installs the **xWebAdministration** module for the resource.</span></span>

### <span data-ttu-id="cddca-130">Voor beeld 4: alle DSC-resources in een module zoeken</span><span class="sxs-lookup"><span data-stu-id="cddca-130">Example 4: Find all DSC resources in a module</span></span>

<span data-ttu-id="cddca-131">`Find-DscResource` Hiermee worden alle DSC-resources in een opgegeven module gevonden.</span><span class="sxs-lookup"><span data-stu-id="cddca-131">`Find-DscResource` finds all the DSC resources contained in a specified module.</span></span> <span data-ttu-id="cddca-132">Standaard wordt de huidige versie weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cddca-132">By default, the current version is displayed.</span></span> <span data-ttu-id="cddca-133">Als u andere versies wilt weer geven, gebruikt u de para meters **AllVersions** of **RequiredVersions** .</span><span class="sxs-lookup"><span data-stu-id="cddca-133">To display other versions, use the **AllVersions** or **RequiredVersions** parameters.</span></span>

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

<span data-ttu-id="cddca-134">`Find-DscResource` maakt gebruik van de para meter **module** om de **xWebAdministration** op te geven en de DSC-resources in de module te vinden.</span><span class="sxs-lookup"><span data-stu-id="cddca-134">`Find-DscResource` uses the **ModuleName** parameter to specify the **xWebAdministration** and find the DSC resources contained in the module.</span></span> <span data-ttu-id="cddca-135">De huidige versie van elke resource wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cddca-135">The current version of each resource is displayed.</span></span>

### <span data-ttu-id="cddca-136">Voor beeld 5: een DSC-resource zoeken op label en vereiste versie</span><span class="sxs-lookup"><span data-stu-id="cddca-136">Example 5: Find a DSC resource by tag and required version</span></span>

<span data-ttu-id="cddca-137">DSC-resources kunnen worden gevonden met behulp van de para meters **tag** en **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="cddca-137">DSC resources can be located using the parameters **Tag** and **RequiredVersion**.</span></span> <span data-ttu-id="cddca-138">**Tag** geeft de huidige versie weer van elke resource die het opgegeven label bevat in de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="cddca-138">**Tag** displays the current version of every resource that contains the specified tag in the repository.</span></span>
<span data-ttu-id="cddca-139">**RequiredVersion** moet de **ModuleName** para meter voor de module **naam** hebben en de para meter name is optioneel.</span><span class="sxs-lookup"><span data-stu-id="cddca-139">**RequiredVersion** needs the **ModuleName** parameter and the **Name** parameter is optional.</span></span> <span data-ttu-id="cddca-140">De para meters **name en naam** **module** beperken de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="cddca-140">The **Name** and **ModuleName** parameters limit the output.</span></span> <span data-ttu-id="cddca-141">Gebruik de para meter **AllVersions** om de beschik bare versies van een DSC-resource weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cddca-141">Use the **AllVersions** parameter to display a DSC resource's available versions.</span></span>

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

### <span data-ttu-id="cddca-142">Voor beeld 6: een resource zoeken met behulp van een filter</span><span class="sxs-lookup"><span data-stu-id="cddca-142">Example 6: Find a resource by using a filter</span></span>

<span data-ttu-id="cddca-143">`Find-DscResource` Hiermee worden alle resources gevonden en de **filter** parameter gebruikt om de resultaten op basis van het **domein** op te geven.</span><span class="sxs-lookup"><span data-stu-id="cddca-143">`Find-DscResource` finds all resources and uses the **Filter** parameter to specify the results by **Domain**.</span></span> <span data-ttu-id="cddca-144">De **filter** parameter zoekt de filter waarde in de beschrijving of module naam van het object.</span><span class="sxs-lookup"><span data-stu-id="cddca-144">The **Filter** parameter finds the filter value in the object's description or module name.</span></span> <span data-ttu-id="cddca-145">Gebruik de `Select-Object` cmdlet om de eigenschappen van een object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cddca-145">Use the `Select-Object` cmdlet to view an object's properties.</span></span>

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

## <span data-ttu-id="cddca-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cddca-146">PARAMETERS</span></span>

### <span data-ttu-id="cddca-147">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="cddca-147">-AllowPrerelease</span></span>

<span data-ttu-id="cddca-148">Bevat resources die zijn gemarkeerd als een prerelease in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="cddca-148">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="cddca-149">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="cddca-149">-AllVersions</span></span>

<span data-ttu-id="cddca-150">Met de para meter **AllVersions** worden alle beschik bare versies van een DSC-resource weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="cddca-150">The **AllVersions** parameter displays each of a DSC resource's available versions.</span></span> <span data-ttu-id="cddca-151">U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion** , **MaximumVersion** of **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="cddca-151">You can't use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="cddca-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="cddca-152">-Filter</span></span>

<span data-ttu-id="cddca-153">Zoekt bronnen op basis van de zoek syntaxis van de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="cddca-153">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="cddca-154">Geef bijvoorbeeld woorden op waarnaar u wilt zoeken in de **ModuleName** eigenschappen van module **naam en beschrijving** .</span><span class="sxs-lookup"><span data-stu-id="cddca-154">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="cddca-155">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="cddca-155">-MaximumVersion</span></span>

<span data-ttu-id="cddca-156">Hiermee geeft u de maximum versie van de resource op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="cddca-156">Specifies the maximum version of the resource to include in results.</span></span> <span data-ttu-id="cddca-157">De **MaximumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="cddca-157">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="cddca-158">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="cddca-158">-MinimumVersion</span></span>

<span data-ttu-id="cddca-159">Hiermee geeft u de minimale versie van de resource op die moet worden meegenomen in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="cddca-159">Specifies the minimum version of the resource to include in results.</span></span> <span data-ttu-id="cddca-160">De **MinimumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="cddca-160">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="cddca-161">-Module naam</span><span class="sxs-lookup"><span data-stu-id="cddca-161">-ModuleName</span></span>

<span data-ttu-id="cddca-162">Hiermee geeft u een module die de DSC-resource bevat.</span><span class="sxs-lookup"><span data-stu-id="cddca-162">Specifies a module that contains the DSC resource.</span></span>

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

### <span data-ttu-id="cddca-163">-Name</span><span class="sxs-lookup"><span data-stu-id="cddca-163">-Name</span></span>

<span data-ttu-id="cddca-164">Hiermee geeft u de naam van een resource.</span><span class="sxs-lookup"><span data-stu-id="cddca-164">Specifies the name of a resource.</span></span> <span data-ttu-id="cddca-165">De standaard waarde is alle resources.</span><span class="sxs-lookup"><span data-stu-id="cddca-165">The default is all resources.</span></span> <span data-ttu-id="cddca-166">Gebruik komma's om een matrix met resource namen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="cddca-166">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="cddca-167">-Proxy</span><span class="sxs-lookup"><span data-stu-id="cddca-167">-Proxy</span></span>

<span data-ttu-id="cddca-168">Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="cddca-168">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="cddca-169">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="cddca-169">-ProxyCredential</span></span>

<span data-ttu-id="cddca-170">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven in de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="cddca-170">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="cddca-171">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="cddca-171">-Repository</span></span>

<span data-ttu-id="cddca-172">Hiermee geeft u een opslag plaats voor het zoeken naar resources op.</span><span class="sxs-lookup"><span data-stu-id="cddca-172">Specifies a repository to search for resources.</span></span> <span data-ttu-id="cddca-173">Gebruik komma's om een matrix van de namen van opslag plaatsen te scheiden.</span><span class="sxs-lookup"><span data-stu-id="cddca-173">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="cddca-174">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="cddca-174">-RequiredVersion</span></span>

<span data-ttu-id="cddca-175">Hiermee geeft u het exacte versie nummer van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="cddca-175">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="cddca-176">De **RequiredVersion** -en **MinimumVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="cddca-176">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="cddca-177">-Tag</span><span class="sxs-lookup"><span data-stu-id="cddca-177">-Tag</span></span>

<span data-ttu-id="cddca-178">Hiermee geeft u labels op waarmee modules in een opslag plaats worden gecategoriseerd.</span><span class="sxs-lookup"><span data-stu-id="cddca-178">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="cddca-179">Gebruik komma's om een matrix met tags te scheiden.</span><span class="sxs-lookup"><span data-stu-id="cddca-179">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="cddca-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cddca-180">CommonParameters</span></span>

<span data-ttu-id="cddca-181">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cddca-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cddca-182">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cddca-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cddca-183">INVOER</span><span class="sxs-lookup"><span data-stu-id="cddca-183">INPUTS</span></span>

## <span data-ttu-id="cddca-184">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cddca-184">OUTPUTS</span></span>

### <span data-ttu-id="cddca-185">PSGetDscResourceInfo</span><span class="sxs-lookup"><span data-stu-id="cddca-185">PSGetDscResourceInfo</span></span>

<span data-ttu-id="cddca-186">`Find-DscResource` retourneert een **PSGetDscResourceInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="cddca-186">`Find-DscResource` returns a **PSGetDscResourceInfo** object.</span></span>

## <span data-ttu-id="cddca-187">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cddca-187">NOTES</span></span>

## <span data-ttu-id="cddca-188">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cddca-188">RELATED LINKS</span></span>

[<span data-ttu-id="cddca-189">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="cddca-189">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="cddca-190">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="cddca-190">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="cddca-191">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="cddca-191">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="cddca-192">Select-Object</span><span class="sxs-lookup"><span data-stu-id="cddca-192">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="cddca-193">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="cddca-193">Uninstall-Module</span></span>](Uninstall-Module.md)

