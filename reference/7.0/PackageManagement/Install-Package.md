---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 506775bf4ef58244a04cb13c1cab926d112111bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251257"
---
# <span data-ttu-id="70277-103">Install-Package</span><span class="sxs-lookup"><span data-stu-id="70277-103">Install-Package</span></span>

## <span data-ttu-id="70277-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="70277-104">SYNOPSIS</span></span>
<span data-ttu-id="70277-105">Hiermee worden een of meer software pakketten geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="70277-105">Installs one or more software packages.</span></span>

## <span data-ttu-id="70277-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="70277-106">SYNTAX</span></span>

### <span data-ttu-id="70277-107">PackageBySearch (standaard)</span><span class="sxs-lookup"><span data-stu-id="70277-107">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="70277-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="70277-108">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="70277-109">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="70277-109">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="70277-110">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="70277-110">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="70277-111">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="70277-111">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="70277-112">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="70277-112">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="70277-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="70277-113">DESCRIPTION</span></span>

<span data-ttu-id="70277-114">`Install-Package`Met de cmdlet worden een of meer software pakketten op de lokale computer geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="70277-114">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="70277-115">Als u meerdere software bronnen hebt, gebruikt `Get-PackageProvider` en `Get-PackageSource` om details over uw providers weer te geven.</span><span class="sxs-lookup"><span data-stu-id="70277-115">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="70277-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="70277-116">EXAMPLES</span></span>

### <span data-ttu-id="70277-117">Voor beeld 1: een pakket installeren op pakket naam</span><span class="sxs-lookup"><span data-stu-id="70277-117">Example 1: Install a package by package name</span></span>

<span data-ttu-id="70277-118">`Install-Package`Met de cmdlet worden een software pakket en de bijbehorende afhankelijkheden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="70277-118">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="70277-119">`Install-Package` maakt gebruik van para meters om de **naam** en **bron** van het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="70277-119">`Install-Package` uses parameters to specify the packages **Name** and **Source**.</span></span> <span data-ttu-id="70277-120">De para meter **Credential** maakt gebruik van een domein gebruikers account met machtigingen voor het installeren van pakketten.</span><span class="sxs-lookup"><span data-stu-id="70277-120">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="70277-121">De opdracht vraagt u om het wacht woord voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="70277-121">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="70277-122">Voor beeld 2: Find-Package gebruiken om een pakket te installeren</span><span class="sxs-lookup"><span data-stu-id="70277-122">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="70277-123">In dit voor beeld wordt het object dat `Find-Package` wordt geretourneerd door, verzonden door de pijp lijn en geïnstalleerd door `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="70277-123">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="70277-124">`Find-Package` maakt gebruik van de **name** -en **Source** -para meters voor het zoeken van een pakket.</span><span class="sxs-lookup"><span data-stu-id="70277-124">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="70277-125">Het object wordt via de pijp lijn verzonden en `Install-Package` het pakket wordt op de lokale computer geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="70277-125">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="70277-126">Voor beeld 3: pakketten installeren door een reeks versies op te geven</span><span class="sxs-lookup"><span data-stu-id="70277-126">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="70277-127">`Install-Package` maakt gebruik van de para meters **MinimumVersion** en **MaximumVersion** om een reeks software versies op te geven.</span><span class="sxs-lookup"><span data-stu-id="70277-127">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="70277-128">`Install-Package` maakt gebruik van de **naam** en de **bron** parameters om een pakket te vinden.</span><span class="sxs-lookup"><span data-stu-id="70277-128">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="70277-129">De para meters **MinimumVersion** en **MaximumVersion** geven een reeks software versies op.</span><span class="sxs-lookup"><span data-stu-id="70277-129">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="70277-130">De hoogste versie in het bereik is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="70277-130">The highest version in the range is installed.</span></span>

## <span data-ttu-id="70277-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="70277-131">PARAMETERS</span></span>

### <span data-ttu-id="70277-132">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="70277-132">-AcceptLicense</span></span>

 <span data-ttu-id="70277-133">**AcceptLicense** accepteert de licentie overeenkomst automatisch tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="70277-133">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-134">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="70277-134">-AllowClobber</span></span>

<span data-ttu-id="70277-135">Onderdrukt waarschuwings berichten over conflicten met bestaande opdrachten.</span><span class="sxs-lookup"><span data-stu-id="70277-135">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="70277-136">Overschrijft bestaande opdrachten die dezelfde naam hebben als de opdrachten die worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="70277-136">Overwrites existing commands that have the same name as commands being installed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-137">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="70277-137">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="70277-138">Hiermee kan de installatie van pakketten die zijn gemarkeerd als Prerelease.</span><span class="sxs-lookup"><span data-stu-id="70277-138">Allows the installation of packages marked as prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-139">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="70277-139">-AllVersions</span></span>

<span data-ttu-id="70277-140">`Install-Package` Hiermee worden alle beschik bare versies van het pakket geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="70277-140">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="70277-141">Standaard wordt alleen de nieuwste versie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="70277-141">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="70277-142">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="70277-142">-Command</span></span>

<span data-ttu-id="70277-143">Hiermee geeft u een of meer opdrachten op die worden `Install-Package` doorzocht.</span><span class="sxs-lookup"><span data-stu-id="70277-143">Specifies one or more commands that `Install-Package` searches.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-144">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="70277-144">-ConfigFile</span></span>

<span data-ttu-id="70277-145">Hiermee geeft u een pad op dat een configuratie bestand bevat.</span><span class="sxs-lookup"><span data-stu-id="70277-145">Specifies a path that contains a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-146">-Bevat</span><span class="sxs-lookup"><span data-stu-id="70277-146">-Contains</span></span>

<span data-ttu-id="70277-147">`Install-Package` haalt objecten op als de para meter **contains** een waarde bevat die overeenkomt met de eigenschaps waarden van het object.</span><span class="sxs-lookup"><span data-stu-id="70277-147">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-148">-Credential</span><span class="sxs-lookup"><span data-stu-id="70277-148">-Credential</span></span>

<span data-ttu-id="70277-149">Hiermee geeft u een gebruikers account op dat is gemachtigd om toegang te krijgen tot de computer en om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="70277-149">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="70277-150">Typ een gebruikers naam, zoals **gebruiker01** , **Domain01\User01** , of voer een **PSCredential** -object in dat door de `Get-Credential` cmdlet wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="70277-150">Type a user name, such as **User01** , **Domain01\User01** , or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="70277-151">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="70277-151">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="70277-152">Wanneer de para meter **Credential** niet is opgegeven, `Install-Package` gebruikt de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="70277-152">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="70277-153">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="70277-153">-Destination</span></span>

<span data-ttu-id="70277-154">Hiermee geeft u een pad naar een invoer object op.</span><span class="sxs-lookup"><span data-stu-id="70277-154">Specifies a path to an input object.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-155">-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="70277-155">-DscResource</span></span>

<span data-ttu-id="70277-156">Hiermee geeft u een of meer desired state Configuration (DSC)-resources op waarnaar wordt gezocht `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="70277-156">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="70277-157">Gebruik de `Find-DscResource` cmdlet om DSC-resources te zoeken.</span><span class="sxs-lookup"><span data-stu-id="70277-157">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-158">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="70277-158">-ExcludeVersion</span></span>

<span data-ttu-id="70277-159">Schakel over om het versie nummer in het mappad uit te sluiten.</span><span class="sxs-lookup"><span data-stu-id="70277-159">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-160">-Filter</span><span class="sxs-lookup"><span data-stu-id="70277-160">-Filter</span></span>

<span data-ttu-id="70277-161">Hiermee geeft u de voor waarden voor het zoeken in de eigenschappen **name** en **Description** .</span><span class="sxs-lookup"><span data-stu-id="70277-161">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-162">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="70277-162">-FilterOnTag</span></span>

<span data-ttu-id="70277-163">Hiermee geeft u een label op waarmee resultaten worden gefilterd en worden geen resultaten opgenomen die het opgegeven label niet bevatten.</span><span class="sxs-lookup"><span data-stu-id="70277-163">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-164">-Force</span><span class="sxs-lookup"><span data-stu-id="70277-164">-Force</span></span>

<span data-ttu-id="70277-165">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="70277-165">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="70277-166">Onderdrukkingen van beperkingen die voor komen dat `Install-Package` de slagen worden voltooid, met uitzonde ring van beveiliging.</span><span class="sxs-lookup"><span data-stu-id="70277-166">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="70277-167">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="70277-167">-ForceBootstrap</span></span>

<span data-ttu-id="70277-168">Forceert **Package Management** de pakket provider automatisch te installeren voor het opgegeven pakket.</span><span class="sxs-lookup"><span data-stu-id="70277-168">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="70277-169">-Headers</span><span class="sxs-lookup"><span data-stu-id="70277-169">-Headers</span></span>

<span data-ttu-id="70277-170">Hiermee geeft u de pakket headers op.</span><span class="sxs-lookup"><span data-stu-id="70277-170">Specifies the package headers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-171">-Bevat</span><span class="sxs-lookup"><span data-stu-id="70277-171">-Includes</span></span>

<span data-ttu-id="70277-172">Hiermee wordt aangegeven of `Install-Package` alle pakket typen moeten worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="70277-172">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="70277-173">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="70277-173">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="70277-174">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70277-174">Cmdlet</span></span>
- <span data-ttu-id="70277-175">Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="70277-175">DscResource</span></span>
- <span data-ttu-id="70277-176">Functie</span><span class="sxs-lookup"><span data-stu-id="70277-176">Function</span></span>
- <span data-ttu-id="70277-177">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="70277-177">RoleCapability</span></span>
- <span data-ttu-id="70277-178">Werkstroom</span><span class="sxs-lookup"><span data-stu-id="70277-178">Workflow</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-179">-Input object</span><span class="sxs-lookup"><span data-stu-id="70277-179">-InputObject</span></span>

<span data-ttu-id="70277-180">Accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="70277-180">Accepts pipeline input.</span></span> <span data-ttu-id="70277-181">Hiermee geeft u een pakket op met behulp van het **SoftwareIdentity** -type van het pakket.</span><span class="sxs-lookup"><span data-stu-id="70277-181">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="70277-182">`Find-Package` Hiermee wordt een **SoftwareIdentity** -object uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="70277-182">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="70277-183">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="70277-183">-InstallUpdate</span></span>

<span data-ttu-id="70277-184">Hiermee wordt aangegeven dat `Install-Package` updates worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="70277-184">Indicates that `Install-Package` installs updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-185">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="70277-185">-MaximumVersion</span></span>

<span data-ttu-id="70277-186">Hiermee geeft u de Maxi maal toegestane pakket versie op die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="70277-186">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="70277-187">Als u deze para meter niet opgeeft, `Install-Package` installeert de nieuwste versie van het pakket.</span><span class="sxs-lookup"><span data-stu-id="70277-187">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-188">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="70277-188">-MinimumVersion</span></span>

<span data-ttu-id="70277-189">Hiermee geeft u de mini maal toegestane pakket versie op die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="70277-189">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="70277-190">Als u deze para meter niet toevoegt, `Install-Package` installeert de nieuwste versie van het pakket die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="70277-190">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-191">-Name</span><span class="sxs-lookup"><span data-stu-id="70277-191">-Name</span></span>

<span data-ttu-id="70277-192">Hiermee geeft u een of meer pakket namen op.</span><span class="sxs-lookup"><span data-stu-id="70277-192">Specifies one or more package names.</span></span> <span data-ttu-id="70277-193">Meerdere pakket namen moeten worden gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="70277-193">Multiple package names must be separated by commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-194">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="70277-194">-NoPathUpdate</span></span>

<span data-ttu-id="70277-195">**NoPathUpdate** is alleen van toepassing op de `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70277-195">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="70277-196">**NoPathUpdate** is een dynamische para meter die door de provider wordt toegevoegd en niet wordt ondersteund door `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="70277-196">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-197">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="70277-197">-PackageManagementProvider</span></span>

<span data-ttu-id="70277-198">Hiermee geeft u de naam van de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="70277-198">Specifies the name of the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-199">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="70277-199">-ProviderName</span></span>

<span data-ttu-id="70277-200">Hiermee geeft u een of meer pakket provider namen op voor het bereik van uw pakket zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="70277-200">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="70277-201">U kunt pakket provider namen ophalen door de cmdlet uit te voeren `Get-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="70277-201">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="70277-202">-Proxy</span><span class="sxs-lookup"><span data-stu-id="70277-202">-Proxy</span></span>

<span data-ttu-id="70277-203">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met een Internet bron.</span><span class="sxs-lookup"><span data-stu-id="70277-203">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="70277-204">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="70277-204">-ProxyCredential</span></span>

<span data-ttu-id="70277-205">Hiermee geeft u een gebruikers account op dat gemachtigd is om de proxy server te gebruiken die is opgegeven met de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="70277-205">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="70277-206">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="70277-206">-PublishLocation</span></span>

<span data-ttu-id="70277-207">Hiermee geeft u het pad op naar de gepubliceerde locatie van een pakket.</span><span class="sxs-lookup"><span data-stu-id="70277-207">Specifies the path to a package's published location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-208">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="70277-208">-RequiredVersion</span></span>

<span data-ttu-id="70277-209">Hiermee geeft u de exacte toegestane versie van het pakket op dat u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="70277-209">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="70277-210">Als u deze para meter niet toevoegt, `Install-Package` installeert de nieuwste versie van het pakket die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="70277-210">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-211">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="70277-211">-RoleCapability</span></span>

<span data-ttu-id="70277-212">Hiermee wordt een matrix met functie mogelijkheden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="70277-212">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-213">-Bereik</span><span class="sxs-lookup"><span data-stu-id="70277-213">-Scope</span></span>

<span data-ttu-id="70277-214">Hiermee geeft u het bereik op waarvoor het pakket moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="70277-214">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="70277-215">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="70277-215">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="70277-216">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="70277-216">CurrentUser</span></span>
- <span data-ttu-id="70277-217">AllUsers</span><span class="sxs-lookup"><span data-stu-id="70277-217">AllUsers</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-218">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="70277-218">-ScriptPublishLocation</span></span>

<span data-ttu-id="70277-219">Hiermee geeft u het pad op naar de gepubliceerde locatie van een script.</span><span class="sxs-lookup"><span data-stu-id="70277-219">Specifies the path to a script's published location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-220">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="70277-220">-ScriptSourceLocation</span></span>

<span data-ttu-id="70277-221">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="70277-221">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-222">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="70277-222">-SkipDependencies</span></span>

<span data-ttu-id="70277-223">Slaat de installatie van software-afhankelijkheden over.</span><span class="sxs-lookup"><span data-stu-id="70277-223">Skips the installation of software dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-224">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="70277-224">-SkipPublisherCheck</span></span>

<span data-ttu-id="70277-225">Hiermee kunt u een pakket versie ophalen die nieuwer is dan de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="70277-225">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="70277-226">Bijvoorbeeld een geïnstalleerd pakket dat digitaal is ondertekend door een vertrouwde uitgever, maar een nieuwe versie niet digitaal is ondertekend.</span><span class="sxs-lookup"><span data-stu-id="70277-226">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-227">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="70277-227">-SkipValidate</span></span>

<span data-ttu-id="70277-228">Switch waarmee de validatie van de referenties van een pakket wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="70277-228">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-229">-Source</span><span class="sxs-lookup"><span data-stu-id="70277-229">-Source</span></span>

<span data-ttu-id="70277-230">Hiermee geeft u een of meer pakket bronnen op.</span><span class="sxs-lookup"><span data-stu-id="70277-230">Specifies one or more package sources.</span></span> <span data-ttu-id="70277-231">Meerdere pakket bron namen moeten worden gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="70277-231">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="70277-232">U kunt pakket bron namen ophalen door de cmdlet uit te voeren `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="70277-232">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="70277-233">-Tag</span><span class="sxs-lookup"><span data-stu-id="70277-233">-Tag</span></span>

<span data-ttu-id="70277-234">Hiermee geeft u een of meer teken reeksen op waarnaar moet worden gezocht in de meta gegevens van het pakket.</span><span class="sxs-lookup"><span data-stu-id="70277-234">Specifies one or more strings to search for in the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-235">-Type</span><span class="sxs-lookup"><span data-stu-id="70277-235">-Type</span></span>

<span data-ttu-id="70277-236">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of beide.</span><span class="sxs-lookup"><span data-stu-id="70277-236">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="70277-237">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="70277-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="70277-238">Module</span><span class="sxs-lookup"><span data-stu-id="70277-238">Module</span></span>
- <span data-ttu-id="70277-239">Script</span><span class="sxs-lookup"><span data-stu-id="70277-239">Script</span></span>
- <span data-ttu-id="70277-240">Alles</span><span class="sxs-lookup"><span data-stu-id="70277-240">All</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-241">-Confirm</span><span class="sxs-lookup"><span data-stu-id="70277-241">-Confirm</span></span>

<span data-ttu-id="70277-242">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="70277-242">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-243">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="70277-243">-WhatIf</span></span>

<span data-ttu-id="70277-244">Laat zien wat er zou gebeuren als de `Install-Package` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="70277-244">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="70277-245">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="70277-245">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70277-246">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="70277-246">CommonParameters</span></span>

<span data-ttu-id="70277-247">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="70277-247">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="70277-248">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="70277-248">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="70277-249">INVOER</span><span class="sxs-lookup"><span data-stu-id="70277-249">INPUTS</span></span>

### <span data-ttu-id="70277-250">`Install-Package` accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="70277-250">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="70277-251">UITVOER</span><span class="sxs-lookup"><span data-stu-id="70277-251">OUTPUTS</span></span>

### <span data-ttu-id="70277-252">SoftwareIdentity []</span><span class="sxs-lookup"><span data-stu-id="70277-252">SoftwareIdentity[]</span></span>

## <span data-ttu-id="70277-253">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="70277-253">NOTES</span></span>

<span data-ttu-id="70277-254">Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70277-254">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="70277-255">Dynamische para meters zijn specifiek voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="70277-255">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="70277-256">De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.</span><span class="sxs-lookup"><span data-stu-id="70277-256">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="70277-257">`Install-Package`Heeft bijvoorbeeld de para meter **PowerShellGet** met de waarde `-NoPathUpdate` , `AllowClobber` en `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="70277-257">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="70277-258">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="70277-258">RELATED LINKS</span></span>

[<span data-ttu-id="70277-259">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="70277-259">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="70277-260">Zoeken-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="70277-260">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="70277-261">Get-Help</span><span class="sxs-lookup"><span data-stu-id="70277-261">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="70277-262">Get-Package</span><span class="sxs-lookup"><span data-stu-id="70277-262">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="70277-263">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="70277-263">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="70277-264">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="70277-264">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="70277-265">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="70277-265">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="70277-266">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="70277-266">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="70277-267">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="70277-267">Uninstall-Package</span></span>](Uninstall-Package.md)
