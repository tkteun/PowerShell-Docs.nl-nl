---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: f9cba90ffa69d04df196f4062c8f190d545b9bc3
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892532"
---
# <span data-ttu-id="d889b-102">Find-Module</span><span class="sxs-lookup"><span data-stu-id="d889b-102">Find-Module</span></span>

## <span data-ttu-id="d889b-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d889b-103">SYNOPSIS</span></span>
<span data-ttu-id="d889b-104">Hiermee worden modules in een opslag plaats gevonden die overeenkomen met opgegeven criteria.</span><span class="sxs-lookup"><span data-stu-id="d889b-104">Finds modules in a repository that match specified criteria.</span></span>

## <span data-ttu-id="d889b-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d889b-105">SYNTAX</span></span>

### <span data-ttu-id="d889b-106">Alles</span><span class="sxs-lookup"><span data-stu-id="d889b-106">All</span></span>

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="d889b-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d889b-107">DESCRIPTION</span></span>

<span data-ttu-id="d889b-108">De `Find-Module` cmdlet vindt modules in een opslag plaats die overeenkomen met de opgegeven criteria.</span><span class="sxs-lookup"><span data-stu-id="d889b-108">The `Find-Module` cmdlet finds modules in a repository that match the specified criteria.</span></span>
<span data-ttu-id="d889b-109">`Find-Module` retourneert een **PSRepositoryItemInfo** -object voor elke module die wordt gevonden.</span><span class="sxs-lookup"><span data-stu-id="d889b-109">`Find-Module` returns a **PSRepositoryItemInfo** object for each module it finds.</span></span> <span data-ttu-id="d889b-110">De objecten kunnen naar de-cmdlets in de pijp lijn worden verzonden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="d889b-110">The objects can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

<span data-ttu-id="d889b-111">De eerste keer dat `Find-Module` u een opslag plaats probeert te gebruiken, wordt u mogelijk gevraagd om updates te installeren.</span><span class="sxs-lookup"><span data-stu-id="d889b-111">The first time `Find-Module` attempts to use a repository, you might be prompted to install updates.</span></span>
<span data-ttu-id="d889b-112">Als de opslagplaats bron niet is geregistreerd bij de `Register-PSRepository` cmdlet, wordt een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d889b-112">If the repository source is not registered with `Register-PSRepository` cmdlet, an error is returned.</span></span>

<span data-ttu-id="d889b-113">`Find-Module` retourneert de nieuwste versie van een module als er geen para meters worden gebruikt die de versie beperken.</span><span class="sxs-lookup"><span data-stu-id="d889b-113">`Find-Module` returns the newest version of a module if no parameters are used that limit the version.</span></span> <span data-ttu-id="d889b-114">Als u de lijst met de versies van een module wilt ophalen, gebruikt u de para meter **AllVersions**.</span><span class="sxs-lookup"><span data-stu-id="d889b-114">To get a repository's list of a module's versions, use the parameter **AllVersions**.</span></span>

<span data-ttu-id="d889b-115">Als de para meter **MinimumVersion** is opgegeven, `Find-Module` retourneert de versie van de module die gelijk is aan of groter is dan de minimum waarde.</span><span class="sxs-lookup"><span data-stu-id="d889b-115">If the **MinimumVersion** parameter is specified, `Find-Module` returns the module's version that is equal to or greater than the minimum.</span></span> <span data-ttu-id="d889b-116">Als er een nieuwere versie beschikbaar is in de opslag plaats, wordt de nieuwere versie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d889b-116">If there is a newer version available in the repository, the newer version is returned.</span></span>

<span data-ttu-id="d889b-117">Als de para meter **MaximumVersion** is opgegeven, `Find-Module` retourneert de nieuwste versie van de module die de opgegeven versie niet overschrijdt.</span><span class="sxs-lookup"><span data-stu-id="d889b-117">If the **MaximumVersion** parameter is specified, `Find-Module` returns the newest version of the module that does not exceed the version specified.</span></span>

<span data-ttu-id="d889b-118">Als de para meter **RequiredVersion** is opgegeven, `Find-Module` retourneert alleen de module versie die exact overeenkomt met de opgegeven versie.</span><span class="sxs-lookup"><span data-stu-id="d889b-118">If the **RequiredVersion** parameter is specified, `Find-Module` only returns the module version that is an exact match to the specified version.</span></span> <span data-ttu-id="d889b-119">`Find-Module` doorzoekt alle beschik bare modules, omdat er naam conflicten tussen bronnen kunnen optreden.</span><span class="sxs-lookup"><span data-stu-id="d889b-119">`Find-Module` searches through all available modules, because name conflicts between sources can occur.</span></span>

<span data-ttu-id="d889b-120">De volgende voor beelden gebruiken de [PowerShell Gallery](https://www.powershellgallery.com/) als de enige geregistreerde opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="d889b-120">The following examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="d889b-121">`Get-PSRepository` Hiermee worden de geregistreerde opslag plaatsen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d889b-121">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="d889b-122">Als u meerdere geregistreerde opslag plaatsen hebt, gebruikt u de `-Repository` para meter om de naam van de opslag plaats op te geven.</span><span class="sxs-lookup"><span data-stu-id="d889b-122">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="d889b-123">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d889b-123">EXAMPLES</span></span>

### <span data-ttu-id="d889b-124">Voor beeld 1: een module op naam zoeken</span><span class="sxs-lookup"><span data-stu-id="d889b-124">Example 1: Find a module by name</span></span>

<span data-ttu-id="d889b-125">In dit voor beeld wordt een module in de standaard opslagplaats gevonden.</span><span class="sxs-lookup"><span data-stu-id="d889b-125">This example finds a module in the default repository.</span></span>

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

<span data-ttu-id="d889b-126">De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="d889b-126">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>

### <span data-ttu-id="d889b-127">Voor beeld 2: modules met vergelijk bare namen zoeken</span><span class="sxs-lookup"><span data-stu-id="d889b-127">Example 2: Find modules with similar names</span></span>

<span data-ttu-id="d889b-128">In dit voor beeld wordt het `*` Joker teken sterretje () gebruikt om modules met vergelijk bare namen te vinden.</span><span class="sxs-lookup"><span data-stu-id="d889b-128">This example uses the asterisk (`*`) wildcard to find modules with similar names.</span></span>

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

<span data-ttu-id="d889b-129">De `Find-Module` cmdlet gebruikt de para meter **name** met het `*` Joker teken sterretje () om alle modules te zoeken die **Power shell** bevatten.</span><span class="sxs-lookup"><span data-stu-id="d889b-129">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to find all modules that contain **PowerShell**.</span></span>

### <span data-ttu-id="d889b-130">Voor beeld 3: een module op minimale versie zoeken</span><span class="sxs-lookup"><span data-stu-id="d889b-130">Example 3: Find a module by minimum version</span></span>

<span data-ttu-id="d889b-131">In dit voor beeld wordt gezocht naar de minimale versie van een module.</span><span class="sxs-lookup"><span data-stu-id="d889b-131">This example searches for a module's minimum version.</span></span> <span data-ttu-id="d889b-132">Als de opslag plaats een nieuwere versie van de module bevat, wordt de nieuwere versie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d889b-132">If the repository contains a newer version of the module, the newer version is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="d889b-133">De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="d889b-133">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="d889b-134">De **MinimumVersion** geeft versie **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="d889b-134">The **MinimumVersion** specifies version **1.6.5**.</span></span> <span data-ttu-id="d889b-135">`Find-Module` retourneert PowerShellGet-versie **2.1.0** omdat deze de minimale versie overschrijdt en de meest recente versie is.</span><span class="sxs-lookup"><span data-stu-id="d889b-135">`Find-Module` returns PowerShellGet version **2.1.0** because it exceeds the minimum version and is the most current version.</span></span>

### <span data-ttu-id="d889b-136">Voor beeld 4: een module zoeken op specifieke versie</span><span class="sxs-lookup"><span data-stu-id="d889b-136">Example 4: Find a module by specific version</span></span>

<span data-ttu-id="d889b-137">In dit voor beeld wordt een object geretourneerd dat de specifieke versie van een module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="d889b-137">This example returns an object that represents a module's specific version.</span></span> <span data-ttu-id="d889b-138">Als de opgegeven versie niet wordt gevonden, wordt er een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d889b-138">If the specified version is not found, an error is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="d889b-139">De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="d889b-139">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="d889b-140">De para meter **RequiredVersion** geeft versie **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="d889b-140">The **RequiredVersion** parameter specifies version **1.6.5**.</span></span>

### <span data-ttu-id="d889b-141">Voor beeld 5: een module in een specifieke opslag plaats zoeken</span><span class="sxs-lookup"><span data-stu-id="d889b-141">Example 5: Find a module in a specific repository</span></span>

<span data-ttu-id="d889b-142">In dit voor beeld wordt de para meter **repository** gebruikt om een module in een specifieke opslag plaats te vinden.</span><span class="sxs-lookup"><span data-stu-id="d889b-142">This example uses the **Repository** parameter to find a module in a specific repository.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="d889b-143">De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="d889b-143">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="d889b-144">De **opslagplaats** parameter geeft aan dat de **PSGallery** -opslag plaats moet worden doorzocht.</span><span class="sxs-lookup"><span data-stu-id="d889b-144">The **Repository** parameter specifies to search the **PSGallery** repository.</span></span>

### <span data-ttu-id="d889b-145">Voor beeld 6: een module in meerdere opslag plaatsen zoeken</span><span class="sxs-lookup"><span data-stu-id="d889b-145">Example 6: Find a module in multiple repositories</span></span>

<span data-ttu-id="d889b-146">In dit voor beeld wordt de gebruikt `Register-PSRepository` om een opslag plaats op te geven.</span><span class="sxs-lookup"><span data-stu-id="d889b-146">This example uses the `Register-PSRepository` to specify a repository.</span></span> <span data-ttu-id="d889b-147">`Find-Module` maakt gebruik van de opslag plaats om een module te zoeken.</span><span class="sxs-lookup"><span data-stu-id="d889b-147">`Find-Module` uses the repository to search for a module.</span></span>

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

<span data-ttu-id="d889b-148">De `Register-PSRepository` cmdlet registreert een nieuwe opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="d889b-148">The `Register-PSRepository` cmdlet registers a new repository.</span></span> <span data-ttu-id="d889b-149">De para meter **name** wijst de naam **MySource** toe.</span><span class="sxs-lookup"><span data-stu-id="d889b-149">The **Name** parameter assigns the name **MySource**.</span></span> <span data-ttu-id="d889b-150">De **SourceLocation** para meter geeft u het adres van de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="d889b-150">The **SourceLocation** parameter specifies the repository's address.</span></span>

<span data-ttu-id="d889b-151">De `Find-Module` cmdlet gebruikt de para meter **name** met het `*` Joker teken sterretje () om de **Contoso** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="d889b-151">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to specify the **Contoso** module.</span></span> <span data-ttu-id="d889b-152">De **opslagplaats** parameter geeft aan dat twee opslag plaatsen, **PSGallery** en **MySource**, moeten worden doorzocht.</span><span class="sxs-lookup"><span data-stu-id="d889b-152">The **Repository** parameter specifies to search two repositories, **PSGallery** and **MySource**.</span></span>

### <span data-ttu-id="d889b-153">Voor beeld 7: een module zoeken die een DSC-resource bevat</span><span class="sxs-lookup"><span data-stu-id="d889b-153">Example 7: Find a module that contains a DSC resource</span></span>

<span data-ttu-id="d889b-154">Met deze opdracht worden modules geretourneerd die DSC-resources bevatten.</span><span class="sxs-lookup"><span data-stu-id="d889b-154">This command returns modules that contain DSC resources.</span></span> <span data-ttu-id="d889b-155">De para meter **includes** heeft vier vooraf gedefinieerde functionaliteiten die worden gebruikt voor het doorzoeken van de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="d889b-155">The **Includes** parameter has four predefined functionalities that are used to search the repository.</span></span> <span data-ttu-id="d889b-156">Gebruik tab-volt ooien om de vier functies weer te geven die worden ondersteund door de para meter **includes** .</span><span class="sxs-lookup"><span data-stu-id="d889b-156">Use tab-complete to display the four functionalities supported by the **Includes** parameter.</span></span>

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

<span data-ttu-id="d889b-157">De `Find-Module` cmdlet gebruikt de para meter **opslagplaats** om de opslag plaats, **PSGallery** te doorzoeken.</span><span class="sxs-lookup"><span data-stu-id="d889b-157">The `Find-Module` cmdlet uses the **Repository** parameter to search the repository, **PSGallery**.</span></span>
<span data-ttu-id="d889b-158">Met de para meter **includes** wordt **dscresource bieden** opgegeven. Dit is een functionaliteit die in de opslag plaats kan worden gezocht in de-para meter.</span><span class="sxs-lookup"><span data-stu-id="d889b-158">The **Includes** parameter specifies **DscResource**, which is a functionality that the parameter can search for in the repository.</span></span>

### <span data-ttu-id="d889b-159">Voor beeld 8: een module met een filter zoeken</span><span class="sxs-lookup"><span data-stu-id="d889b-159">Example 8: Find a module with a filter</span></span>

<span data-ttu-id="d889b-160">In dit voor beeld wordt voor het zoeken naar modules een filter gebruikt om de opslag plaats te doorzoeken.</span><span class="sxs-lookup"><span data-stu-id="d889b-160">In this example, to find modules, a filter is used to search the repository.</span></span>

<span data-ttu-id="d889b-161">Voor een NuGet-opslag plaats zoekt de **filter** parameter de naam, de beschrijving en de labels voor het argument.</span><span class="sxs-lookup"><span data-stu-id="d889b-161">For a NuGet-based repository, the **Filter** parameter searches through the name, description, and tags for the argument.</span></span>

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

<span data-ttu-id="d889b-162">De `Find-Module` cmdlet gebruikt de **filter** parameter om de opslag plaats voor **AppDomain** te doorzoeken.</span><span class="sxs-lookup"><span data-stu-id="d889b-162">The `Find-Module` cmdlet uses the **Filter** parameter to search the repository for **AppDomain**.</span></span>

## <span data-ttu-id="d889b-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d889b-163">PARAMETERS</span></span>

### <span data-ttu-id="d889b-164">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="d889b-164">-AllowPrerelease</span></span>

<span data-ttu-id="d889b-165">Bevat de resultaten modules die als voorlopige versie zijn gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="d889b-165">Includes in the results modules marked as a pre-release.</span></span>

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

### <span data-ttu-id="d889b-166">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="d889b-166">-AllVersions</span></span>

<span data-ttu-id="d889b-167">Hiermee geeft u alle versies van een module in de resultaten opneemt.</span><span class="sxs-lookup"><span data-stu-id="d889b-167">Specifies to include all versions of a module in the results.</span></span> <span data-ttu-id="d889b-168">U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion**, **MaximumVersion** of **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="d889b-168">You cannot use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="d889b-169">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="d889b-169">-Command</span></span>

<span data-ttu-id="d889b-170">Hiermee geeft u een matrix met opdrachten op die in modules moet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="d889b-170">Specifies an array of commands to find in modules.</span></span> <span data-ttu-id="d889b-171">Een opdracht kan een functie of werk stroom zijn.</span><span class="sxs-lookup"><span data-stu-id="d889b-171">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="d889b-172">-Credential</span><span class="sxs-lookup"><span data-stu-id="d889b-172">-Credential</span></span>

<span data-ttu-id="d889b-173">Hiermee geeft u een gebruikers account op dat beschikt over rechten voor het installeren van een module voor een opgegeven pakket provider of bron.</span><span class="sxs-lookup"><span data-stu-id="d889b-173">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="d889b-174">-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="d889b-174">-DscResource</span></span>

<span data-ttu-id="d889b-175">Hiermee geeft u de naam of een deel van de naam van modules die DSC-resources bevatten.</span><span class="sxs-lookup"><span data-stu-id="d889b-175">Specifies the name, or part of the name, of modules that contain DSC resources.</span></span> <span data-ttu-id="d889b-176">U kunt per Power shell-conventies een **of** -zoek opdracht uitvoeren wanneer u meerdere argumenten opgeeft.</span><span class="sxs-lookup"><span data-stu-id="d889b-176">Per PowerShell conventions, performs an **OR** search when you provide multiple arguments.</span></span>

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

### <span data-ttu-id="d889b-177">-Filter</span><span class="sxs-lookup"><span data-stu-id="d889b-177">-Filter</span></span>

<span data-ttu-id="d889b-178">Hiermee geeft u een filter op op basis van de **Package Management** -specifieke zoek syntaxis.</span><span class="sxs-lookup"><span data-stu-id="d889b-178">Specifies a filter based on the **PackageManagement** provider-specific search syntax.</span></span> <span data-ttu-id="d889b-179">Voor NuGet-modules is deze para meter het equivalent van zoeken met behulp van de zoek balk op de [PowerShell Gallery](https://www.powershellgallery.com/) -website.</span><span class="sxs-lookup"><span data-stu-id="d889b-179">For NuGet modules, this parameter is the equivalent of searching by using the Search bar on the [PowerShell Gallery](https://www.powershellgallery.com/) website.</span></span>

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

### <span data-ttu-id="d889b-180">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="d889b-180">-IncludeDependencies</span></span>

<span data-ttu-id="d889b-181">Geeft aan dat deze bewerking alle modules bevat die afhankelijk zijn van de module die is opgegeven in de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="d889b-181">Indicates that this operation includes all modules that are dependent upon the module specified in the **Name** parameter.</span></span>

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

### <span data-ttu-id="d889b-182">-Bevat</span><span class="sxs-lookup"><span data-stu-id="d889b-182">-Includes</span></span>

<span data-ttu-id="d889b-183">Retourneert alleen de modules die specifieke soorten Power shell-functionaliteit bevatten.</span><span class="sxs-lookup"><span data-stu-id="d889b-183">Returns only those modules that include specific kinds of PowerShell functionality.</span></span> <span data-ttu-id="d889b-184">U kunt bijvoorbeeld alleen modules zoeken die **dscresource bieden** bevatten.</span><span class="sxs-lookup"><span data-stu-id="d889b-184">For example, you might only want to find modules that include **DSCResource**.</span></span> <span data-ttu-id="d889b-185">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="d889b-185">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="d889b-186">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d889b-186">Cmdlet</span></span>
- <span data-ttu-id="d889b-187">Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="d889b-187">DscResource</span></span>
- <span data-ttu-id="d889b-188">Functie</span><span class="sxs-lookup"><span data-stu-id="d889b-188">Function</span></span>
- <span data-ttu-id="d889b-189">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="d889b-189">RoleCapability</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d889b-190">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="d889b-190">-MaximumVersion</span></span>

<span data-ttu-id="d889b-191">Hiermee geeft u het maximum, of de meest recente versie van de module op die in de zoek resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="d889b-191">Specifies the maximum, or latest, version of the module to include in the search results.</span></span>
<span data-ttu-id="d889b-192">**MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="d889b-192">**MaximumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d889b-193">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="d889b-193">-MinimumVersion</span></span>

<span data-ttu-id="d889b-194">Hiermee geeft u de minimale versie van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="d889b-194">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="d889b-195">**MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="d889b-195">**MinimumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d889b-196">-Name</span><span class="sxs-lookup"><span data-stu-id="d889b-196">-Name</span></span>

<span data-ttu-id="d889b-197">Hiermee geeft u de namen van modules op waarnaar moet worden gezocht in de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="d889b-197">Specifies the names of modules to search for in the repository.</span></span> <span data-ttu-id="d889b-198">Een door komma's gescheiden lijst met module namen wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="d889b-198">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="d889b-199">Joker tekens worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="d889b-199">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d889b-200">-Proxy</span><span class="sxs-lookup"><span data-stu-id="d889b-200">-Proxy</span></span>

<span data-ttu-id="d889b-201">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="d889b-201">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="d889b-202">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="d889b-202">-ProxyCredential</span></span>

<span data-ttu-id="d889b-203">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="d889b-203">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="d889b-204">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="d889b-204">-Repository</span></span>

<span data-ttu-id="d889b-205">Gebruik de para meter **opslagplaats** om op te geven welke opslag plaats moet worden doorzocht op een module.</span><span class="sxs-lookup"><span data-stu-id="d889b-205">Use the **Repository** parameter to specify which repository to search for a module.</span></span> <span data-ttu-id="d889b-206">Wordt gebruikt wanneer meerdere opslag plaatsen zijn geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="d889b-206">Used when multiple repositories are registered.</span></span> <span data-ttu-id="d889b-207">Accepteert een door komma's gescheiden lijst met opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="d889b-207">Accepts a comma-separated list of repositories.</span></span> <span data-ttu-id="d889b-208">Als u een opslag plaats wilt registreren, gebruikt u `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="d889b-208">To register a repository, use `Register-PSRepository`.</span></span> <span data-ttu-id="d889b-209">Gebruik om geregistreerde opslag plaatsen weer te geven `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="d889b-209">To display registered repositories, use `Get-PSRepository`.</span></span>

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

### <span data-ttu-id="d889b-210">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="d889b-210">-RequiredVersion</span></span>

<span data-ttu-id="d889b-211">Hiermee geeft u het exacte versie nummer van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="d889b-211">Specifies the exact version number of the module to include in the results.</span></span> <span data-ttu-id="d889b-212">**RequiredVersion** kan niet worden gebruikt in dezelfde opdracht als **MinimumVersion** of **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="d889b-212">**RequiredVersion** cannot be used in the same command as **MinimumVersion** or **MaximumVersion**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d889b-213">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="d889b-213">-RoleCapability</span></span>

<span data-ttu-id="d889b-214">Hiermee wordt een matrix met functie mogelijkheden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d889b-214">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="d889b-215">-Tag</span><span class="sxs-lookup"><span data-stu-id="d889b-215">-Tag</span></span>

<span data-ttu-id="d889b-216">Hiermee geeft u een matrix met tags op.</span><span class="sxs-lookup"><span data-stu-id="d889b-216">Specifies an array of tags.</span></span> <span data-ttu-id="d889b-217">Voor beelden van tags zijn **DesiredStateConfiguration**, **DSC**, **DSCResourceKit** of **PSModule**.</span><span class="sxs-lookup"><span data-stu-id="d889b-217">Example tags include **DesiredStateConfiguration**, **DSC**, **DSCResourceKit**, or **PSModule**.</span></span>

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

### <span data-ttu-id="d889b-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d889b-218">CommonParameters</span></span>

<span data-ttu-id="d889b-219">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d889b-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d889b-220">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d889b-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d889b-221">INVOER</span><span class="sxs-lookup"><span data-stu-id="d889b-221">INPUTS</span></span>

### <span data-ttu-id="d889b-222">System.String[]</span><span class="sxs-lookup"><span data-stu-id="d889b-222">System.String[]</span></span>

### <span data-ttu-id="d889b-223">System. String</span><span class="sxs-lookup"><span data-stu-id="d889b-223">System.String</span></span>

### <span data-ttu-id="d889b-224">System. URI</span><span class="sxs-lookup"><span data-stu-id="d889b-224">System.Uri</span></span>

### <span data-ttu-id="d889b-225">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="d889b-225">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="d889b-226">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d889b-226">OUTPUTS</span></span>

### <span data-ttu-id="d889b-227">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="d889b-227">PSRepositoryItemInfo</span></span>

<span data-ttu-id="d889b-228">`Find-Module` Hiermee maakt u **PSRepositoryItemInfo** -objecten die de pijp lijn kunnen verzenden naar cmdlets zoals `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="d889b-228">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

## <span data-ttu-id="d889b-229">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d889b-229">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d889b-230">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="d889b-230">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d889b-231">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d889b-231">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d889b-232">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="d889b-232">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d889b-233">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d889b-233">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d889b-234">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d889b-234">RELATED LINKS</span></span>

[<span data-ttu-id="d889b-235">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d889b-235">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="d889b-236">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="d889b-236">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="d889b-237">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="d889b-237">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="d889b-238">Save-Module</span><span class="sxs-lookup"><span data-stu-id="d889b-238">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="d889b-239">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="d889b-239">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="d889b-240">Update-Module</span><span class="sxs-lookup"><span data-stu-id="d889b-240">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="d889b-241">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d889b-241">Register-PSRepository</span></span>](Register-PSRepository.md)
