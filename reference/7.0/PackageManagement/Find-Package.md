---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Package
ms.openlocfilehash: 9bbcda92b98410835a2380296a06fd053c01b52c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249688"
---
# <span data-ttu-id="3216c-103">Find-Package</span><span class="sxs-lookup"><span data-stu-id="3216c-103">Find-Package</span></span>

## <span data-ttu-id="3216c-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3216c-104">SYNOPSIS</span></span>
<span data-ttu-id="3216c-105">Zoekt naar software pakketten in beschik bare pakket bronnen.</span><span class="sxs-lookup"><span data-stu-id="3216c-105">Finds software packages in available package sources.</span></span>

## <span data-ttu-id="3216c-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3216c-106">SYNTAX</span></span>

### <span data-ttu-id="3216c-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="3216c-107">NuGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>]
 [-FilterOnTag <String[]>] [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="3216c-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="3216c-108">PowerShellGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-AllowPrereleaseVersions] [-PackageManagementProvider <String>]
 [-PublishLocation <String>] [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>]
 [-Type <String>] [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>]
 [-DscResource <String[]>] [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense]
 [<CommonParameters>]
```

## <span data-ttu-id="3216c-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3216c-109">DESCRIPTION</span></span>

<span data-ttu-id="3216c-110">`Find-Package` zoekt naar software pakketten die beschikbaar zijn in pakket bronnen.</span><span class="sxs-lookup"><span data-stu-id="3216c-110">`Find-Package` finds software packages that are available in package sources.</span></span> <span data-ttu-id="3216c-111">`Get-PackageProvider` en `Get-PackageSource` Details over uw providers weer geven.</span><span class="sxs-lookup"><span data-stu-id="3216c-111">`Get-PackageProvider` and `Get-PackageSource` display details about your providers.</span></span>

## <span data-ttu-id="3216c-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3216c-112">EXAMPLES</span></span>

### <span data-ttu-id="3216c-113">Voor beeld 1: alle beschik bare pakketten van een pakket provider zoeken</span><span class="sxs-lookup"><span data-stu-id="3216c-113">Example 1: Find all available packages from a package provider</span></span>

<span data-ttu-id="3216c-114">Met deze opdracht vindt u alle beschik bare Power shell-module pakketten in een geregistreerde galerie.</span><span class="sxs-lookup"><span data-stu-id="3216c-114">This command finds all available PowerShell module packages in a registered gallery.</span></span> <span data-ttu-id="3216c-115">Gebruik `Get-PackageProvider` om de naam van de provider op te halen.</span><span class="sxs-lookup"><span data-stu-id="3216c-115">Use `Get-PackageProvider` to get the provider name.</span></span>

```
Find-Package -ProviderName NuGet
```

```Output
Name               Version   Source     Summary
----               -------   ------     -------
NUnit              3.11.0    MyNuGet    NUnit is a unit-testing framework for all .NET langua...
Newtonsoft.Json    12.0.1    MyNuGet    Json.NET is a popular high-performance JSON framework...
EntityFramework    6.2.0     MyNuGet    Entity Framework is Microsoft's recommended data acce...
MySql.Data         8.0.15    MyNuGet    MySql.Data.MySqlClient .Net Core Class Library
bootstrap          4.3.1     MyNuGet    Bootstrap framework in CSS. Includes fonts and JavaSc...
NuGet.Core         2.14.0    MyNuGet    NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="3216c-116">`Find-Package` gebruikt de **provider** parameter om de provider- **NuGet** op te geven.</span><span class="sxs-lookup"><span data-stu-id="3216c-116">`Find-Package` uses the **Provider** parameter to specify the provider **NuGet**.</span></span>

### <span data-ttu-id="3216c-117">Voor beeld 2: een pakket uit een pakket bron zoeken</span><span class="sxs-lookup"><span data-stu-id="3216c-117">Example 2: Find a package from a package source</span></span>

<span data-ttu-id="3216c-118">Met deze opdracht vindt u de nieuwste versie van een pakket van een opgegeven pakket bron.</span><span class="sxs-lookup"><span data-stu-id="3216c-118">This command finds the newest version of a package from a specified package source.</span></span> <span data-ttu-id="3216c-119">Als er geen pakket bron wordt gegeven, `Find-Package` doorzoekt elke geïnstalleerde pakket provider en de bijbehorende pakket bronnen.</span><span class="sxs-lookup"><span data-stu-id="3216c-119">If a package source isn't provided, `Find-Package` searches each installed package provider and its package sources.</span></span> <span data-ttu-id="3216c-120">Gebruiken `Get-PackageSource` om de bron naam op te halen.</span><span class="sxs-lookup"><span data-stu-id="3216c-120">Use `Get-PackageSource` to get the source name.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet
```

```Output
Name         Version   Source    Summary
----         -------   ------    -------
NuGet.Core   2.14.0    MyNuGet   NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="3216c-121">`Find-Package` maakt gebruik van de para meter **name** om de pakket naam **NuGet. core** op te geven.</span><span class="sxs-lookup"><span data-stu-id="3216c-121">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="3216c-122">De para meter **Source** geeft aan dat het pakket moet worden gezocht in **MyNuGet**.</span><span class="sxs-lookup"><span data-stu-id="3216c-122">The **Source** parameter specifies to search for the package in **MyNuGet**.</span></span>

### <span data-ttu-id="3216c-123">Voor beeld 3: alle versies van een pakket zoeken</span><span class="sxs-lookup"><span data-stu-id="3216c-123">Example 3: Find all versions of a package</span></span>

<span data-ttu-id="3216c-124">Met deze opdracht vindt u alle beschik bare pakket versies van een opgegeven provider.</span><span class="sxs-lookup"><span data-stu-id="3216c-124">This command finds all available package versions from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.14.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.14.0-rtm-832   MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.13.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
...
NuGet.Core    1.1.229.159      MyNuGet      NuGet.Core is the core framework assembly for NuGet...
Nuget.Core    1.0.1120.104     MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="3216c-125">`Find-Package` maakt gebruik van de para meter **name** om het pakket **NuGet. core** op te geven.</span><span class="sxs-lookup"><span data-stu-id="3216c-125">`Find-Package` uses the **Name** parameter to specify the package **NuGet.Core**.</span></span> <span data-ttu-id="3216c-126">De para meter **ProviderName** geeft aan dat het pakket moet worden gezocht in **MyNuGet**.</span><span class="sxs-lookup"><span data-stu-id="3216c-126">The **ProviderName** parameter specifies to search for the package in **MyNuGet**.</span></span> <span data-ttu-id="3216c-127">**AllVersions** geeft aan dat alle beschik bare versies worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3216c-127">**AllVersions** specifies that all available versions are returned.</span></span>

### <span data-ttu-id="3216c-128">Voor beeld 4: een pakket met een specifieke naam en versie zoeken</span><span class="sxs-lookup"><span data-stu-id="3216c-128">Example 4: Find a package with a specific name and version</span></span>

<span data-ttu-id="3216c-129">Met deze opdracht vindt u een specifieke pakket versie van een opgegeven provider.</span><span class="sxs-lookup"><span data-stu-id="3216c-129">This command finds a specific package version from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -RequiredVersion 2.9.0
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="3216c-130">`Find-Package` maakt gebruik van de para meter **name** om de pakket naam **NuGet. core** op te geven.</span><span class="sxs-lookup"><span data-stu-id="3216c-130">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="3216c-131">De para meter **ProviderName** geeft aan dat het pakket moet worden gezocht in **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3216c-131">The **ProviderName** parameter specifies to search for the package in **NuGet**.</span></span> <span data-ttu-id="3216c-132">**RequiredVersion** geeft aan dat alleen versie **2.9.0** wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3216c-132">**RequiredVersion** specifies that only version **2.9.0** is returned.</span></span>

### <span data-ttu-id="3216c-133">Voor beeld 5: pakketten zoeken binnen een reeks versies</span><span class="sxs-lookup"><span data-stu-id="3216c-133">Example 5: Find packages within a range of versions</span></span>

<span data-ttu-id="3216c-134">Met deze opdracht vindt u een reeks versies voor een opgegeven pakket.</span><span class="sxs-lookup"><span data-stu-id="3216c-134">This command finds a range of versions for a specified package.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -MinimumVersion 2.7.0 -MaximumVersion 2.9.0 -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.6            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.7.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="3216c-135">`Find-Package` maakt gebruik van de para meter **name** om de pakket naam **NuGet. core** op te geven.</span><span class="sxs-lookup"><span data-stu-id="3216c-135">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="3216c-136">De para meter **ProviderName** geeft aan dat het pakket moet worden gezocht in **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3216c-136">The **ProviderName** parameter specifies to search for the package in **NuGet**.</span></span> <span data-ttu-id="3216c-137">**MinimumVersion** Hiermee geeft u de laagste versie **2.7.0** op.</span><span class="sxs-lookup"><span data-stu-id="3216c-137">**MinimumVersion** specifies the lowest version **2.7.0**.</span></span> <span data-ttu-id="3216c-138">**MaximumVersion** Hiermee geeft u de hoogste versie **2.9.0**.</span><span class="sxs-lookup"><span data-stu-id="3216c-138">**MaximumVersion** specifies the highest version **2.9.0**.</span></span>
<span data-ttu-id="3216c-139">**AllVersions** bepaalt het bereik dat wordt geretourneerd door de minimum-en maximum waarde.</span><span class="sxs-lookup"><span data-stu-id="3216c-139">**AllVersions** determines the range is returned as specified by the minimum and maximum.</span></span>

### <span data-ttu-id="3216c-140">Voor beeld 6: een pakket uit een bestands systeem zoeken</span><span class="sxs-lookup"><span data-stu-id="3216c-140">Example 6: Find a package from a file system</span></span>

<span data-ttu-id="3216c-141">Met deze opdracht vindt u pakketten met de bestands extensie `.nupkg` die is opgeslagen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="3216c-141">This command finds packages with the file extension `.nupkg` that are stored on the local computer.</span></span>
<span data-ttu-id="3216c-142">De bestanden zijn pakketten die zijn gedownload uit een galerie, zoals de **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3216c-142">The files are packages downloaded from a gallery such as the **NuGet**.</span></span>

```
PS> Find-Package -Source C:\LocalPkg
```

```Output
Name                 Version    Source           Summary
----                 -------    ------           -------
Microsoft.Web.Xdt    3.0.0      C:\LocalPkg\     Microsoft Xml Document Transformation (XDT)...
NuGet.Core           2.14.0     C:\LocalPkg\     NuGet.Core is the core framework assembly...
```

## <span data-ttu-id="3216c-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3216c-143">PARAMETERS</span></span>

### <span data-ttu-id="3216c-144">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="3216c-144">-AcceptLicense</span></span>

<span data-ttu-id="3216c-145">Accepteert automatisch een gebruiksrecht overeenkomst als het pakket deze vereist.</span><span class="sxs-lookup"><span data-stu-id="3216c-145">Automatically accepts a license agreement if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-146">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="3216c-146">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="3216c-147">Bevat pakketten die zijn gemarkeerd als een prerelease in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="3216c-147">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="3216c-148">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="3216c-148">-AllVersions</span></span>

<span data-ttu-id="3216c-149">Hiermee wordt aangegeven dat `Find-Package` alle beschik bare versies van het pakket worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3216c-149">Indicates that `Find-Package` returns all available versions of the package.</span></span> <span data-ttu-id="3216c-150">`Find-Package`Retourneert standaard alleen de nieuwste beschik bare versie.</span><span class="sxs-lookup"><span data-stu-id="3216c-150">By default, `Find-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="3216c-151">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="3216c-151">-Command</span></span>

<span data-ttu-id="3216c-152">Hiermee wordt een matrix opgegeven met opdrachten die worden doorzocht `Find-Package` .</span><span class="sxs-lookup"><span data-stu-id="3216c-152">Specifies an array of commands searched by `Find-Package`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-153">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="3216c-153">-ConfigFile</span></span>

<span data-ttu-id="3216c-154">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="3216c-154">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-155">-Bevat</span><span class="sxs-lookup"><span data-stu-id="3216c-155">-Contains</span></span>

<span data-ttu-id="3216c-156">`Find-Package` haalt objecten op als een item in de eigenschaps waarden van het object exact overeenkomt met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="3216c-156">`Find-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="3216c-157">-Credential</span></span>

<span data-ttu-id="3216c-158">Hiermee geeft u een gebruikers account op dat gemachtigd is om te zoeken naar pakketten.</span><span class="sxs-lookup"><span data-stu-id="3216c-158">Specifies a user account that has permission to search for packages.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-159">-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="3216c-159">-DscResource</span></span>

<span data-ttu-id="3216c-160">Hiermee geeft u een matrix met DSC-resources (desired state Configuration) op die met deze cmdlet wordt doorzocht.</span><span class="sxs-lookup"><span data-stu-id="3216c-160">Specifies an array of Desired State Configuration (DSC) resources that this cmdlet searches.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-161">-Filter</span><span class="sxs-lookup"><span data-stu-id="3216c-161">-Filter</span></span>

<span data-ttu-id="3216c-162">Hiermee geeft u de voor waarden voor het zoeken in de eigenschappen **name** en **Description** .</span><span class="sxs-lookup"><span data-stu-id="3216c-162">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-163">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="3216c-163">-FilterOnTag</span></span>

<span data-ttu-id="3216c-164">Hiermee geeft u de tag op waarmee de resultaten worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="3216c-164">Specifies the tag that filters the results.</span></span> <span data-ttu-id="3216c-165">De resultaten die de opgegeven tag niet bevatten, worden uitgesloten.</span><span class="sxs-lookup"><span data-stu-id="3216c-165">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-166">-Force</span><span class="sxs-lookup"><span data-stu-id="3216c-166">-Force</span></span>

<span data-ttu-id="3216c-167">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="3216c-167">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="3216c-168">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="3216c-168">-ForceBootstrap</span></span>

<span data-ttu-id="3216c-169">Geeft aan `Find-Package` dat **Package Management** automatisch de pakket provider installeert.</span><span class="sxs-lookup"><span data-stu-id="3216c-169">Indicates that `Find-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="3216c-170">-Headers</span><span class="sxs-lookup"><span data-stu-id="3216c-170">-Headers</span></span>

<span data-ttu-id="3216c-171">Hiermee geeft u de headers voor het pakket op.</span><span class="sxs-lookup"><span data-stu-id="3216c-171">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-172">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="3216c-172">-IncludeDependencies</span></span>

<span data-ttu-id="3216c-173">Geeft aan dat deze cmdlet pakket afhankelijkheden in de resultaten bevat.</span><span class="sxs-lookup"><span data-stu-id="3216c-173">Indicates that this cmdlet includes package dependencies in the results.</span></span>

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

### <span data-ttu-id="3216c-174">-Bevat</span><span class="sxs-lookup"><span data-stu-id="3216c-174">-Includes</span></span>

<span data-ttu-id="3216c-175">Hiermee wordt aangegeven of `Find-Package` alle pakketten binnen een categorie moeten worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="3216c-175">Specifies whether `Find-Package` should find all packages within a category.</span></span>

<span data-ttu-id="3216c-176">De geaccepteerde waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="3216c-176">The accepted values are as follows:</span></span>

- <span data-ttu-id="3216c-177">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3216c-177">Cmdlet</span></span>
- <span data-ttu-id="3216c-178">Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="3216c-178">DscResource</span></span>
- <span data-ttu-id="3216c-179">Functie</span><span class="sxs-lookup"><span data-stu-id="3216c-179">Function</span></span>
- <span data-ttu-id="3216c-180">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="3216c-180">RoleCapability</span></span>
- <span data-ttu-id="3216c-181">Werkstroom</span><span class="sxs-lookup"><span data-stu-id="3216c-181">Workflow</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-182">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="3216c-182">-MaximumVersion</span></span>

<span data-ttu-id="3216c-183">Hiermee geeft u de maximale pakket versie op die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="3216c-183">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="3216c-184">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="3216c-184">-MinimumVersion</span></span>

<span data-ttu-id="3216c-185">Hiermee geeft u de minimale pakket versie op die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="3216c-185">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="3216c-186">Als er een hogere versie beschikbaar is, wordt die versie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3216c-186">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="3216c-187">-Name</span><span class="sxs-lookup"><span data-stu-id="3216c-187">-Name</span></span>

<span data-ttu-id="3216c-188">Hiermee geeft u een of meer pakket namen of pakket namen met Joker tekens op.</span><span class="sxs-lookup"><span data-stu-id="3216c-188">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="3216c-189">Scheid meerdere pakket namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="3216c-189">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3216c-190">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="3216c-190">-PackageManagementProvider</span></span>

<span data-ttu-id="3216c-191">Hiermee geeft u de naam van een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="3216c-191">Specifies the name of a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-192">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="3216c-192">-ProviderName</span></span>

<span data-ttu-id="3216c-193">Hiermee geeft u een of meer pakket provider namen op.</span><span class="sxs-lookup"><span data-stu-id="3216c-193">Specifies one or more package provider names.</span></span> <span data-ttu-id="3216c-194">Scheid meerdere pakket provider namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="3216c-194">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="3216c-195">Gebruiken `Get-PackageProvider` om een lijst met beschik bare pakket providers op te halen.</span><span class="sxs-lookup"><span data-stu-id="3216c-195">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-196">-Proxy</span><span class="sxs-lookup"><span data-stu-id="3216c-196">-Proxy</span></span>

<span data-ttu-id="3216c-197">Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="3216c-197">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-198">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="3216c-198">-ProxyCredential</span></span>

<span data-ttu-id="3216c-199">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="3216c-199">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-200">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="3216c-200">-PublishLocation</span></span>

<span data-ttu-id="3216c-201">Hiermee geeft u een locatie op voor het publiceren van het pakket.</span><span class="sxs-lookup"><span data-stu-id="3216c-201">Specifies a location for publishing the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-202">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3216c-202">-RequiredVersion</span></span>

<span data-ttu-id="3216c-203">Hiermee geeft u een exacte pakket versie op die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="3216c-203">Specifies an exact package version that you want to find.</span></span>

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

### <span data-ttu-id="3216c-204">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="3216c-204">-RoleCapability</span></span>

<span data-ttu-id="3216c-205">Hiermee wordt een matrix met functie mogelijkheden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3216c-205">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-206">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="3216c-206">-ScriptPublishLocation</span></span>

<span data-ttu-id="3216c-207">Hiermee geeft u een locatie voor het publiceren van een script op voor het pakket.</span><span class="sxs-lookup"><span data-stu-id="3216c-207">Specifies a script publishing location for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-208">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="3216c-208">-ScriptSourceLocation</span></span>

<span data-ttu-id="3216c-209">Hiermee geeft u een bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="3216c-209">Specifies a script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-210">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="3216c-210">-SkipValidate</span></span>

<span data-ttu-id="3216c-211">Switch waarmee validatie van pakket referenties wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="3216c-211">Switch that skips package credential validation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-212">-Source</span><span class="sxs-lookup"><span data-stu-id="3216c-212">-Source</span></span>

<span data-ttu-id="3216c-213">Hiermee geeft u een of meer pakket bronnen op.</span><span class="sxs-lookup"><span data-stu-id="3216c-213">Specifies one or more package sources.</span></span> <span data-ttu-id="3216c-214">Gebruiken `Get-PackageSource` om een lijst met beschik bare pakket bronnen op te halen.</span><span class="sxs-lookup"><span data-stu-id="3216c-214">Use `Get-PackageSource` to get a list of available package sources.</span></span> <span data-ttu-id="3216c-215">Een File System-map kan worden gebruikt als bron voor het downloaden van pakketten.</span><span class="sxs-lookup"><span data-stu-id="3216c-215">A file system directory can be used as a source for download packages.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-216">-Tag</span><span class="sxs-lookup"><span data-stu-id="3216c-216">-Tag</span></span>

<span data-ttu-id="3216c-217">Hiermee geeft u een of meer teken reeksen op waarnaar moet worden gezocht in de meta gegevens van het pakket.</span><span class="sxs-lookup"><span data-stu-id="3216c-217">Specifies one or more strings to search for in the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-218">-Type</span><span class="sxs-lookup"><span data-stu-id="3216c-218">-Type</span></span>

<span data-ttu-id="3216c-219">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of een van beide.</span><span class="sxs-lookup"><span data-stu-id="3216c-219">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3216c-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3216c-220">CommonParameters</span></span>

<span data-ttu-id="3216c-221">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3216c-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3216c-222">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3216c-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3216c-223">INVOER</span><span class="sxs-lookup"><span data-stu-id="3216c-223">INPUTS</span></span>

### <span data-ttu-id="3216c-224">Geen</span><span class="sxs-lookup"><span data-stu-id="3216c-224">None</span></span>

<span data-ttu-id="3216c-225">`Find-Package` invoer van de pijp lijn wordt niet geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="3216c-225">`Find-Package` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="3216c-226">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3216c-226">OUTPUTS</span></span>

### <span data-ttu-id="3216c-227">SoftwareIdentify[]</span><span class="sxs-lookup"><span data-stu-id="3216c-227">SoftwareIdentify[]</span></span>

<span data-ttu-id="3216c-228">`Find-Package` Hiermee wordt een **SoftwareIdentity** -object uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="3216c-228">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

## <span data-ttu-id="3216c-229">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3216c-229">NOTES</span></span>

## <span data-ttu-id="3216c-230">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3216c-230">RELATED LINKS</span></span>

[<span data-ttu-id="3216c-231">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="3216c-231">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="3216c-232">Get-Package</span><span class="sxs-lookup"><span data-stu-id="3216c-232">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="3216c-233">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="3216c-233">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="3216c-234">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="3216c-234">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="3216c-235">Install-Package</span><span class="sxs-lookup"><span data-stu-id="3216c-235">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="3216c-236">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="3216c-236">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="3216c-237">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="3216c-237">Uninstall-Package</span></span>](Uninstall-Package.md)
