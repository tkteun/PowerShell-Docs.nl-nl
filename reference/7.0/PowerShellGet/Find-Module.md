---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: 33b7861f4e776b992d3483b9b0776c32a88599fc
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249491"
---
# <span data-ttu-id="e384f-103">Find-Module</span><span class="sxs-lookup"><span data-stu-id="e384f-103">Find-Module</span></span>

## <span data-ttu-id="e384f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="e384f-104">SYNOPSIS</span></span>
<span data-ttu-id="e384f-105">Hiermee worden modules in een opslag plaats gevonden die overeenkomen met opgegeven criteria.</span><span class="sxs-lookup"><span data-stu-id="e384f-105">Finds modules in a repository that match specified criteria.</span></span>

## <span data-ttu-id="e384f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="e384f-106">SYNTAX</span></span>

### <span data-ttu-id="e384f-107">Alles</span><span class="sxs-lookup"><span data-stu-id="e384f-107">All</span></span>

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="e384f-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="e384f-108">DESCRIPTION</span></span>

<span data-ttu-id="e384f-109">De `Find-Module` cmdlet vindt modules in een opslag plaats die overeenkomen met de opgegeven criteria.</span><span class="sxs-lookup"><span data-stu-id="e384f-109">The `Find-Module` cmdlet finds modules in a repository that match the specified criteria.</span></span>
<span data-ttu-id="e384f-110">`Find-Module` retourneert een **PSRepositoryItemInfo** -object voor elke module die wordt gevonden.</span><span class="sxs-lookup"><span data-stu-id="e384f-110">`Find-Module` returns a **PSRepositoryItemInfo** object for each module it finds.</span></span> <span data-ttu-id="e384f-111">De objecten kunnen naar de-cmdlets in de pijp lijn worden verzonden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="e384f-111">The objects can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

<span data-ttu-id="e384f-112">De eerste keer dat `Find-Module` u een opslag plaats probeert te gebruiken, wordt u mogelijk gevraagd om updates te installeren.</span><span class="sxs-lookup"><span data-stu-id="e384f-112">The first time `Find-Module` attempts to use a repository, you might be prompted to install updates.</span></span>
<span data-ttu-id="e384f-113">Als de opslagplaats bron niet is geregistreerd bij de `Register-PSRepository` cmdlet, wordt een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e384f-113">If the repository source is not registered with `Register-PSRepository` cmdlet, an error is returned.</span></span>

<span data-ttu-id="e384f-114">`Find-Module` retourneert de nieuwste versie van een module als er geen para meters worden gebruikt die de versie beperken.</span><span class="sxs-lookup"><span data-stu-id="e384f-114">`Find-Module` returns the newest version of a module if no parameters are used that limit the version.</span></span> <span data-ttu-id="e384f-115">Als u de lijst met de versies van een module wilt ophalen, gebruikt u de para meter **AllVersions**.</span><span class="sxs-lookup"><span data-stu-id="e384f-115">To get a repository's list of a module's versions, use the parameter **AllVersions**.</span></span>

<span data-ttu-id="e384f-116">Als de para meter **MinimumVersion** is opgegeven, `Find-Module` retourneert de versie van de module die gelijk is aan of groter is dan de minimum waarde.</span><span class="sxs-lookup"><span data-stu-id="e384f-116">If the **MinimumVersion** parameter is specified, `Find-Module` returns the module's version that is equal to or greater than the minimum.</span></span> <span data-ttu-id="e384f-117">Als er een nieuwere versie beschikbaar is in de opslag plaats, wordt de nieuwere versie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e384f-117">If there is a newer version available in the repository, the newer version is returned.</span></span>

<span data-ttu-id="e384f-118">Als de para meter **MaximumVersion** is opgegeven, `Find-Module` retourneert de nieuwste versie van de module die de opgegeven versie niet overschrijdt.</span><span class="sxs-lookup"><span data-stu-id="e384f-118">If the **MaximumVersion** parameter is specified, `Find-Module` returns the newest version of the module that does not exceed the version specified.</span></span>

<span data-ttu-id="e384f-119">Als de para meter **RequiredVersion** is opgegeven, `Find-Module` retourneert alleen de module versie die exact overeenkomt met de opgegeven versie.</span><span class="sxs-lookup"><span data-stu-id="e384f-119">If the **RequiredVersion** parameter is specified, `Find-Module` only returns the module version that is an exact match to the specified version.</span></span> <span data-ttu-id="e384f-120">`Find-Module` doorzoekt alle beschik bare modules, omdat er naam conflicten tussen bronnen kunnen optreden.</span><span class="sxs-lookup"><span data-stu-id="e384f-120">`Find-Module` searches through all available modules, because name conflicts between sources can occur.</span></span>

<span data-ttu-id="e384f-121">De volgende voor beelden gebruiken de [PowerShell Gallery](https://www.powershellgallery.com/) als de enige geregistreerde opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e384f-121">The following examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="e384f-122">`Get-PSRepository` Hiermee worden de geregistreerde opslag plaatsen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e384f-122">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="e384f-123">Als u meerdere geregistreerde opslag plaatsen hebt, gebruikt u de `-Repository` para meter om de naam van de opslag plaats op te geven.</span><span class="sxs-lookup"><span data-stu-id="e384f-123">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="e384f-124">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="e384f-124">EXAMPLES</span></span>

### <span data-ttu-id="e384f-125">Voor beeld 1: een module op naam zoeken</span><span class="sxs-lookup"><span data-stu-id="e384f-125">Example 1: Find a module by name</span></span>

<span data-ttu-id="e384f-126">In dit voor beeld wordt een module in de standaard opslagplaats gevonden.</span><span class="sxs-lookup"><span data-stu-id="e384f-126">This example finds a module in the default repository.</span></span>

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

<span data-ttu-id="e384f-127">De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="e384f-127">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>

### <span data-ttu-id="e384f-128">Voor beeld 2: modules met vergelijk bare namen zoeken</span><span class="sxs-lookup"><span data-stu-id="e384f-128">Example 2: Find modules with similar names</span></span>

<span data-ttu-id="e384f-129">In dit voor beeld wordt het `*` Joker teken sterretje () gebruikt om modules met vergelijk bare namen te vinden.</span><span class="sxs-lookup"><span data-stu-id="e384f-129">This example uses the asterisk (`*`) wildcard to find modules with similar names.</span></span>

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

<span data-ttu-id="e384f-130">De `Find-Module` cmdlet gebruikt de para meter **name** met het `*` Joker teken sterretje () om alle modules te zoeken die **Power shell** bevatten.</span><span class="sxs-lookup"><span data-stu-id="e384f-130">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to find all modules that contain **PowerShell**.</span></span>

### <span data-ttu-id="e384f-131">Voor beeld 3: een module op minimale versie zoeken</span><span class="sxs-lookup"><span data-stu-id="e384f-131">Example 3: Find a module by minimum version</span></span>

<span data-ttu-id="e384f-132">In dit voor beeld wordt gezocht naar de minimale versie van een module.</span><span class="sxs-lookup"><span data-stu-id="e384f-132">This example searches for a module's minimum version.</span></span> <span data-ttu-id="e384f-133">Als de opslag plaats een nieuwere versie van de module bevat, wordt de nieuwere versie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e384f-133">If the repository contains a newer version of the module, the newer version is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="e384f-134">De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="e384f-134">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="e384f-135">De **MinimumVersion** geeft versie **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="e384f-135">The **MinimumVersion** specifies version **1.6.5**.</span></span> <span data-ttu-id="e384f-136">`Find-Module` retourneert PowerShellGet-versie **2.1.0** omdat deze de minimale versie overschrijdt en de meest recente versie is.</span><span class="sxs-lookup"><span data-stu-id="e384f-136">`Find-Module` returns PowerShellGet version **2.1.0** because it exceeds the minimum version and is the most current version.</span></span>

### <span data-ttu-id="e384f-137">Voor beeld 4: een module zoeken op specifieke versie</span><span class="sxs-lookup"><span data-stu-id="e384f-137">Example 4: Find a module by specific version</span></span>

<span data-ttu-id="e384f-138">In dit voor beeld wordt een object geretourneerd dat de specifieke versie van een module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="e384f-138">This example returns an object that represents a module's specific version.</span></span> <span data-ttu-id="e384f-139">Als de opgegeven versie niet wordt gevonden, wordt er een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e384f-139">If the specified version is not found, an error is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="e384f-140">De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="e384f-140">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="e384f-141">De para meter **RequiredVersion** geeft versie **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="e384f-141">The **RequiredVersion** parameter specifies version **1.6.5**.</span></span>

### <span data-ttu-id="e384f-142">Voor beeld 5: een module in een specifieke opslag plaats zoeken</span><span class="sxs-lookup"><span data-stu-id="e384f-142">Example 5: Find a module in a specific repository</span></span>

<span data-ttu-id="e384f-143">In dit voor beeld wordt de para meter **repository** gebruikt om een module in een specifieke opslag plaats te vinden.</span><span class="sxs-lookup"><span data-stu-id="e384f-143">This example uses the **Repository** parameter to find a module in a specific repository.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="e384f-144">De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="e384f-144">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="e384f-145">De **opslagplaats** parameter geeft aan dat de **PSGallery** -opslag plaats moet worden doorzocht.</span><span class="sxs-lookup"><span data-stu-id="e384f-145">The **Repository** parameter specifies to search the **PSGallery** repository.</span></span>

### <span data-ttu-id="e384f-146">Voor beeld 6: een module in meerdere opslag plaatsen zoeken</span><span class="sxs-lookup"><span data-stu-id="e384f-146">Example 6: Find a module in multiple repositories</span></span>

<span data-ttu-id="e384f-147">In dit voor beeld wordt de gebruikt `Register-PSRepository` om een opslag plaats op te geven.</span><span class="sxs-lookup"><span data-stu-id="e384f-147">This example uses the `Register-PSRepository` to specify a repository.</span></span> <span data-ttu-id="e384f-148">`Find-Module` maakt gebruik van de opslag plaats om een module te zoeken.</span><span class="sxs-lookup"><span data-stu-id="e384f-148">`Find-Module` uses the repository to search for a module.</span></span>

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

<span data-ttu-id="e384f-149">De `Register-PSRepository` cmdlet registreert een nieuwe opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e384f-149">The `Register-PSRepository` cmdlet registers a new repository.</span></span> <span data-ttu-id="e384f-150">De para meter **name** wijst de naam **MySource** toe.</span><span class="sxs-lookup"><span data-stu-id="e384f-150">The **Name** parameter assigns the name **MySource**.</span></span> <span data-ttu-id="e384f-151">De **SourceLocation** para meter geeft u het adres van de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e384f-151">The **SourceLocation** parameter specifies the repository's address.</span></span>

<span data-ttu-id="e384f-152">De `Find-Module` cmdlet gebruikt de para meter **name** met het `*` Joker teken sterretje () om de **Contoso** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="e384f-152">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to specify the **Contoso** module.</span></span> <span data-ttu-id="e384f-153">De **opslagplaats** parameter geeft aan dat twee opslag plaatsen, **PSGallery** en **MySource** , moeten worden doorzocht.</span><span class="sxs-lookup"><span data-stu-id="e384f-153">The **Repository** parameter specifies to search two repositories, **PSGallery** and **MySource**.</span></span>

### <span data-ttu-id="e384f-154">Voor beeld 7: een module zoeken die een DSC-resource bevat</span><span class="sxs-lookup"><span data-stu-id="e384f-154">Example 7: Find a module that contains a DSC resource</span></span>

<span data-ttu-id="e384f-155">Met deze opdracht worden modules geretourneerd die DSC-resources bevatten.</span><span class="sxs-lookup"><span data-stu-id="e384f-155">This command returns modules that contain DSC resources.</span></span> <span data-ttu-id="e384f-156">De para meter **includes** heeft vier vooraf gedefinieerde functionaliteiten die worden gebruikt voor het doorzoeken van de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e384f-156">The **Includes** parameter has four predefined functionalities that are used to search the repository.</span></span> <span data-ttu-id="e384f-157">Gebruik tab-volt ooien om de vier functies weer te geven die worden ondersteund door de para meter **includes** .</span><span class="sxs-lookup"><span data-stu-id="e384f-157">Use tab-complete to display the four functionalities supported by the **Includes** parameter.</span></span>

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

<span data-ttu-id="e384f-158">De `Find-Module` cmdlet gebruikt de para meter **opslagplaats** om de opslag plaats, **PSGallery** te doorzoeken.</span><span class="sxs-lookup"><span data-stu-id="e384f-158">The `Find-Module` cmdlet uses the **Repository** parameter to search the repository, **PSGallery**.</span></span>
<span data-ttu-id="e384f-159">Met de para meter **includes** wordt **dscresource bieden** opgegeven. Dit is een functionaliteit die in de opslag plaats kan worden gezocht in de-para meter.</span><span class="sxs-lookup"><span data-stu-id="e384f-159">The **Includes** parameter specifies **DscResource** , which is a functionality that the parameter can search for in the repository.</span></span>

### <span data-ttu-id="e384f-160">Voor beeld 8: een module met een filter zoeken</span><span class="sxs-lookup"><span data-stu-id="e384f-160">Example 8: Find a module with a filter</span></span>

<span data-ttu-id="e384f-161">In dit voor beeld wordt voor het zoeken naar modules een filter gebruikt om de opslag plaats te doorzoeken.</span><span class="sxs-lookup"><span data-stu-id="e384f-161">In this example, to find modules, a filter is used to search the repository.</span></span>

<span data-ttu-id="e384f-162">Voor een NuGet-opslag plaats zoekt de **filter** parameter de naam, de beschrijving en de labels voor het argument.</span><span class="sxs-lookup"><span data-stu-id="e384f-162">For a NuGet-based repository, the **Filter** parameter searches through the name, description, and tags for the argument.</span></span>

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

<span data-ttu-id="e384f-163">De `Find-Module` cmdlet gebruikt de **filter** parameter om de opslag plaats voor **AppDomain** te doorzoeken.</span><span class="sxs-lookup"><span data-stu-id="e384f-163">The `Find-Module` cmdlet uses the **Filter** parameter to search the repository for **AppDomain**.</span></span>

## <span data-ttu-id="e384f-164">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e384f-164">PARAMETERS</span></span>

### <span data-ttu-id="e384f-165">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="e384f-165">-AllowPrerelease</span></span>

<span data-ttu-id="e384f-166">Bevat de resultaten modules die als voorlopige versie zijn gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="e384f-166">Includes in the results modules marked as a pre-release.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e384f-167">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="e384f-167">-AllVersions</span></span>

<span data-ttu-id="e384f-168">Hiermee geeft u alle versies van een module in de resultaten opneemt.</span><span class="sxs-lookup"><span data-stu-id="e384f-168">Specifies to include all versions of a module in the results.</span></span> <span data-ttu-id="e384f-169">U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion** , **MaximumVersion** of **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="e384f-169">You cannot use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="e384f-170">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="e384f-170">-Command</span></span>

<span data-ttu-id="e384f-171">Hiermee geeft u een matrix met opdrachten op die in modules moet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="e384f-171">Specifies an array of commands to find in modules.</span></span> <span data-ttu-id="e384f-172">Een opdracht kan een functie of werk stroom zijn.</span><span class="sxs-lookup"><span data-stu-id="e384f-172">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="e384f-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="e384f-173">-Credential</span></span>

<span data-ttu-id="e384f-174">Hiermee geeft u een gebruikers account op dat beschikt over rechten voor het installeren van een module voor een opgegeven pakket provider of bron.</span><span class="sxs-lookup"><span data-stu-id="e384f-174">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="e384f-175">-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="e384f-175">-DscResource</span></span>

<span data-ttu-id="e384f-176">Hiermee geeft u de naam of een deel van de naam van modules die DSC-resources bevatten.</span><span class="sxs-lookup"><span data-stu-id="e384f-176">Specifies the name, or part of the name, of modules that contain DSC resources.</span></span> <span data-ttu-id="e384f-177">U kunt per Power shell-conventies een **of** -zoek opdracht uitvoeren wanneer u meerdere argumenten opgeeft.</span><span class="sxs-lookup"><span data-stu-id="e384f-177">Per PowerShell conventions, performs an **OR** search when you provide multiple arguments.</span></span>

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

### <span data-ttu-id="e384f-178">-Filter</span><span class="sxs-lookup"><span data-stu-id="e384f-178">-Filter</span></span>

<span data-ttu-id="e384f-179">Hiermee geeft u een filter op op basis van de **Package Management** -specifieke zoek syntaxis.</span><span class="sxs-lookup"><span data-stu-id="e384f-179">Specifies a filter based on the **PackageManagement** provider-specific search syntax.</span></span> <span data-ttu-id="e384f-180">Voor NuGet-modules is deze para meter het equivalent van zoeken met behulp van de zoek balk op de [PowerShell Gallery](https://www.powershellgallery.com/) -website.</span><span class="sxs-lookup"><span data-stu-id="e384f-180">For NuGet modules, this parameter is the equivalent of searching by using the Search bar on the [PowerShell Gallery](https://www.powershellgallery.com/) website.</span></span>

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

### <span data-ttu-id="e384f-181">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="e384f-181">-IncludeDependencies</span></span>

<span data-ttu-id="e384f-182">Geeft aan dat deze bewerking alle modules bevat die afhankelijk zijn van de module die is opgegeven in de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="e384f-182">Indicates that this operation includes all modules that are dependent upon the module specified in the **Name** parameter.</span></span>

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

### <span data-ttu-id="e384f-183">-Bevat</span><span class="sxs-lookup"><span data-stu-id="e384f-183">-Includes</span></span>

<span data-ttu-id="e384f-184">Retourneert alleen de modules die specifieke soorten Power shell-functionaliteit bevatten.</span><span class="sxs-lookup"><span data-stu-id="e384f-184">Returns only those modules that include specific kinds of PowerShell functionality.</span></span> <span data-ttu-id="e384f-185">U kunt bijvoorbeeld alleen modules zoeken die **dscresource bieden** bevatten.</span><span class="sxs-lookup"><span data-stu-id="e384f-185">For example, you might only want to find modules that include **DSCResource**.</span></span> <span data-ttu-id="e384f-186">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="e384f-186">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e384f-187">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e384f-187">Cmdlet</span></span>
- <span data-ttu-id="e384f-188">Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="e384f-188">DscResource</span></span>
- <span data-ttu-id="e384f-189">Functie</span><span class="sxs-lookup"><span data-stu-id="e384f-189">Function</span></span>
- <span data-ttu-id="e384f-190">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="e384f-190">RoleCapability</span></span>

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

### <span data-ttu-id="e384f-191">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e384f-191">-MaximumVersion</span></span>

<span data-ttu-id="e384f-192">Hiermee geeft u het maximum, of de meest recente versie van de module op die in de zoek resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="e384f-192">Specifies the maximum, or latest, version of the module to include in the search results.</span></span>
<span data-ttu-id="e384f-193">**MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="e384f-193">**MaximumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

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

### <span data-ttu-id="e384f-194">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e384f-194">-MinimumVersion</span></span>

<span data-ttu-id="e384f-195">Hiermee geeft u de minimale versie van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="e384f-195">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="e384f-196">**MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="e384f-196">**MinimumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

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

### <span data-ttu-id="e384f-197">-Name</span><span class="sxs-lookup"><span data-stu-id="e384f-197">-Name</span></span>

<span data-ttu-id="e384f-198">Hiermee geeft u de namen van modules op waarnaar moet worden gezocht in de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e384f-198">Specifies the names of modules to search for in the repository.</span></span> <span data-ttu-id="e384f-199">Een door komma's gescheiden lijst met module namen wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="e384f-199">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="e384f-200">Joker tekens worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="e384f-200">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e384f-201">-Proxy</span><span class="sxs-lookup"><span data-stu-id="e384f-201">-Proxy</span></span>

<span data-ttu-id="e384f-202">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="e384f-202">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="e384f-203">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="e384f-203">-ProxyCredential</span></span>

<span data-ttu-id="e384f-204">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="e384f-204">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="e384f-205">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="e384f-205">-Repository</span></span>

<span data-ttu-id="e384f-206">Gebruik de para meter **opslagplaats** om op te geven welke opslag plaats moet worden doorzocht op een module.</span><span class="sxs-lookup"><span data-stu-id="e384f-206">Use the **Repository** parameter to specify which repository to search for a module.</span></span> <span data-ttu-id="e384f-207">Wordt gebruikt wanneer meerdere opslag plaatsen zijn geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="e384f-207">Used when multiple repositories are registered.</span></span> <span data-ttu-id="e384f-208">Accepteert een door komma's gescheiden lijst met opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="e384f-208">Accepts a comma-separated list of repositories.</span></span> <span data-ttu-id="e384f-209">Als u een opslag plaats wilt registreren, gebruikt u `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="e384f-209">To register a repository, use `Register-PSRepository`.</span></span> <span data-ttu-id="e384f-210">Gebruik om geregistreerde opslag plaatsen weer te geven `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="e384f-210">To display registered repositories, use `Get-PSRepository`.</span></span>

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

### <span data-ttu-id="e384f-211">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e384f-211">-RequiredVersion</span></span>

<span data-ttu-id="e384f-212">Hiermee geeft u het exacte versie nummer van de module op die in de resultaten moet worden meegenomen.</span><span class="sxs-lookup"><span data-stu-id="e384f-212">Specifies the exact version number of the module to include in the results.</span></span> <span data-ttu-id="e384f-213">**RequiredVersion** kan niet worden gebruikt in dezelfde opdracht als **MinimumVersion** of **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="e384f-213">**RequiredVersion** cannot be used in the same command as **MinimumVersion** or **MaximumVersion**.</span></span>

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

### <span data-ttu-id="e384f-214">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="e384f-214">-RoleCapability</span></span>

<span data-ttu-id="e384f-215">Hiermee wordt een matrix met functie mogelijkheden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e384f-215">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="e384f-216">-Tag</span><span class="sxs-lookup"><span data-stu-id="e384f-216">-Tag</span></span>

<span data-ttu-id="e384f-217">Hiermee geeft u een matrix met tags op.</span><span class="sxs-lookup"><span data-stu-id="e384f-217">Specifies an array of tags.</span></span> <span data-ttu-id="e384f-218">Voor beelden van tags zijn **DesiredStateConfiguration** , **DSC** , **DSCResourceKit** of **PSModule**.</span><span class="sxs-lookup"><span data-stu-id="e384f-218">Example tags include **DesiredStateConfiguration** , **DSC** , **DSCResourceKit** , or **PSModule**.</span></span>

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

### <span data-ttu-id="e384f-219">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e384f-219">CommonParameters</span></span>

<span data-ttu-id="e384f-220">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e384f-220">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e384f-221">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e384f-221">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e384f-222">INVOER</span><span class="sxs-lookup"><span data-stu-id="e384f-222">INPUTS</span></span>

### <span data-ttu-id="e384f-223">System.String[]</span><span class="sxs-lookup"><span data-stu-id="e384f-223">System.String[]</span></span>

### <span data-ttu-id="e384f-224">System. String</span><span class="sxs-lookup"><span data-stu-id="e384f-224">System.String</span></span>

### <span data-ttu-id="e384f-225">System. URI</span><span class="sxs-lookup"><span data-stu-id="e384f-225">System.Uri</span></span>

### <span data-ttu-id="e384f-226">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="e384f-226">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="e384f-227">UITVOER</span><span class="sxs-lookup"><span data-stu-id="e384f-227">OUTPUTS</span></span>

### <span data-ttu-id="e384f-228">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="e384f-228">PSRepositoryItemInfo</span></span>

<span data-ttu-id="e384f-229">`Find-Module` Hiermee maakt u **PSRepositoryItemInfo** -objecten die de pijp lijn kunnen verzenden naar cmdlets zoals `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="e384f-229">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

## <span data-ttu-id="e384f-230">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="e384f-230">NOTES</span></span>

<span data-ttu-id="e384f-231">Deze cmdlet wordt uitgevoerd op Power shell 5,0 of latere versies van Power shell, Windows 7 of Windows 2008 R2 en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="e384f-231">This cmdlet runs on PowerShell 5.0 or later releases of PowerShell, on Windows 7, or Windows 2008 R2 and later releases of Windows.</span></span>

## <span data-ttu-id="e384f-232">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="e384f-232">RELATED LINKS</span></span>

[<span data-ttu-id="e384f-233">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="e384f-233">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="e384f-234">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="e384f-234">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="e384f-235">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="e384f-235">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="e384f-236">Save-Module</span><span class="sxs-lookup"><span data-stu-id="e384f-236">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="e384f-237">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="e384f-237">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="e384f-238">Update-Module</span><span class="sxs-lookup"><span data-stu-id="e384f-238">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="e384f-239">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="e384f-239">Register-PSRepository</span></span>](Register-PSRepository.md)
