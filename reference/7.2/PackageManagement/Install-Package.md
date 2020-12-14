---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 1518be0d34733e36217b46cbbf496e580ec7b649
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889432"
---
# <span data-ttu-id="1a207-102">Install-Package</span><span class="sxs-lookup"><span data-stu-id="1a207-102">Install-Package</span></span>

## <span data-ttu-id="1a207-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="1a207-103">SYNOPSIS</span></span>
<span data-ttu-id="1a207-104">Hiermee worden een of meer software pakketten geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-104">Installs one or more software packages.</span></span>

## <span data-ttu-id="1a207-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1a207-105">SYNTAX</span></span>

### <span data-ttu-id="1a207-106">PackageBySearch (standaard)</span><span class="sxs-lookup"><span data-stu-id="1a207-106">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1a207-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1a207-107">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="1a207-108">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="1a207-108">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="1a207-109">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1a207-109">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="1a207-110">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="1a207-110">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="1a207-111">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1a207-111">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="1a207-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1a207-112">DESCRIPTION</span></span>

<span data-ttu-id="1a207-113">`Install-Package`Met de cmdlet worden een of meer software pakketten op de lokale computer geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-113">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="1a207-114">Als u meerdere software bronnen hebt, gebruikt `Get-PackageProvider` en `Get-PackageSource` om details over uw providers weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1a207-114">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="1a207-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1a207-115">EXAMPLES</span></span>

### <span data-ttu-id="1a207-116">Voor beeld 1: een pakket installeren op pakket naam</span><span class="sxs-lookup"><span data-stu-id="1a207-116">Example 1: Install a package by package name</span></span>

<span data-ttu-id="1a207-117">`Install-Package`Met de cmdlet worden een software pakket en de bijbehorende afhankelijkheden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-117">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="1a207-118">`Install-Package` maakt gebruik van para meters om de **naam** en **bron** van het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="1a207-118">`Install-Package` uses parameters to specify the packages **Name** and **Source**.</span></span> <span data-ttu-id="1a207-119">De para meter **Credential** maakt gebruik van een domein gebruikers account met machtigingen voor het installeren van pakketten.</span><span class="sxs-lookup"><span data-stu-id="1a207-119">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="1a207-120">De opdracht vraagt u om het wacht woord voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="1a207-120">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="1a207-121">Voor beeld 2: Find-Package gebruiken om een pakket te installeren</span><span class="sxs-lookup"><span data-stu-id="1a207-121">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="1a207-122">In dit voor beeld wordt het object dat `Find-Package` wordt geretourneerd door, verzonden door de pijp lijn en geïnstalleerd door `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="1a207-122">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="1a207-123">`Find-Package` maakt gebruik van de **name** -en **Source** -para meters voor het zoeken van een pakket.</span><span class="sxs-lookup"><span data-stu-id="1a207-123">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="1a207-124">Het object wordt via de pijp lijn verzonden en `Install-Package` het pakket wordt op de lokale computer geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-124">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="1a207-125">Voor beeld 3: pakketten installeren door een reeks versies op te geven</span><span class="sxs-lookup"><span data-stu-id="1a207-125">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="1a207-126">`Install-Package` maakt gebruik van de para meters **MinimumVersion** en **MaximumVersion** om een reeks software versies op te geven.</span><span class="sxs-lookup"><span data-stu-id="1a207-126">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="1a207-127">`Install-Package` maakt gebruik van de **naam** en de **bron** parameters om een pakket te vinden.</span><span class="sxs-lookup"><span data-stu-id="1a207-127">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="1a207-128">De para meters **MinimumVersion** en **MaximumVersion** geven een reeks software versies op.</span><span class="sxs-lookup"><span data-stu-id="1a207-128">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="1a207-129">De hoogste versie in het bereik is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-129">The highest version in the range is installed.</span></span>

## <span data-ttu-id="1a207-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1a207-130">PARAMETERS</span></span>

### <span data-ttu-id="1a207-131">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="1a207-131">-AcceptLicense</span></span>

 <span data-ttu-id="1a207-132">**AcceptLicense** accepteert de licentie overeenkomst automatisch tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="1a207-132">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

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

### <span data-ttu-id="1a207-133">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="1a207-133">-AllowClobber</span></span>

<span data-ttu-id="1a207-134">Onderdrukt waarschuwings berichten over conflicten met bestaande opdrachten.</span><span class="sxs-lookup"><span data-stu-id="1a207-134">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="1a207-135">Overschrijft bestaande opdrachten die dezelfde naam hebben als de opdrachten die worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-135">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="1a207-136">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="1a207-136">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="1a207-137">Hiermee kan de installatie van pakketten die zijn gemarkeerd als Prerelease.</span><span class="sxs-lookup"><span data-stu-id="1a207-137">Allows the installation of packages marked as prerelease.</span></span>

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

### <span data-ttu-id="1a207-138">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="1a207-138">-AllVersions</span></span>

<span data-ttu-id="1a207-139">`Install-Package` Hiermee worden alle beschik bare versies van het pakket geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-139">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="1a207-140">Standaard wordt alleen de nieuwste versie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-140">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="1a207-141">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="1a207-141">-Command</span></span>

<span data-ttu-id="1a207-142">Hiermee geeft u een of meer opdrachten op die worden `Install-Package` doorzocht.</span><span class="sxs-lookup"><span data-stu-id="1a207-142">Specifies one or more commands that `Install-Package` searches.</span></span>

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

### <span data-ttu-id="1a207-143">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="1a207-143">-ConfigFile</span></span>

<span data-ttu-id="1a207-144">Hiermee geeft u een pad op dat een configuratie bestand bevat.</span><span class="sxs-lookup"><span data-stu-id="1a207-144">Specifies a path that contains a configuration file.</span></span>

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

### <span data-ttu-id="1a207-145">-Bevat</span><span class="sxs-lookup"><span data-stu-id="1a207-145">-Contains</span></span>

<span data-ttu-id="1a207-146">`Install-Package` haalt objecten op als de para meter **contains** een waarde bevat die overeenkomt met de eigenschaps waarden van het object.</span><span class="sxs-lookup"><span data-stu-id="1a207-146">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

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

### <span data-ttu-id="1a207-147">-Credential</span><span class="sxs-lookup"><span data-stu-id="1a207-147">-Credential</span></span>

<span data-ttu-id="1a207-148">Hiermee geeft u een gebruikers account op dat is gemachtigd om toegang te krijgen tot de computer en om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="1a207-148">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="1a207-149">Typ een gebruikers naam, zoals **gebruiker01**, **Domain01\User01**, of voer een **PSCredential** -object in dat door de `Get-Credential` cmdlet wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-149">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1a207-150">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="1a207-150">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="1a207-151">Wanneer de para meter **Credential** niet is opgegeven, `Install-Package` gebruikt de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="1a207-151">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="1a207-152">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="1a207-152">-Destination</span></span>

<span data-ttu-id="1a207-153">Hiermee geeft u een pad naar een invoer object op.</span><span class="sxs-lookup"><span data-stu-id="1a207-153">Specifies a path to an input object.</span></span>

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

### <span data-ttu-id="1a207-154">-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="1a207-154">-DscResource</span></span>

<span data-ttu-id="1a207-155">Hiermee geeft u een of meer desired state Configuration (DSC)-resources op waarnaar wordt gezocht `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="1a207-155">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="1a207-156">Gebruik de `Find-DscResource` cmdlet om DSC-resources te zoeken.</span><span class="sxs-lookup"><span data-stu-id="1a207-156">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

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

### <span data-ttu-id="1a207-157">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="1a207-157">-ExcludeVersion</span></span>

<span data-ttu-id="1a207-158">Schakel over om het versie nummer in het mappad uit te sluiten.</span><span class="sxs-lookup"><span data-stu-id="1a207-158">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="1a207-159">-Filter</span><span class="sxs-lookup"><span data-stu-id="1a207-159">-Filter</span></span>

<span data-ttu-id="1a207-160">Hiermee geeft u de voor waarden voor het zoeken in de eigenschappen **name** en **Description** .</span><span class="sxs-lookup"><span data-stu-id="1a207-160">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

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

### <span data-ttu-id="1a207-161">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="1a207-161">-FilterOnTag</span></span>

<span data-ttu-id="1a207-162">Hiermee geeft u een label op waarmee resultaten worden gefilterd en worden geen resultaten opgenomen die het opgegeven label niet bevatten.</span><span class="sxs-lookup"><span data-stu-id="1a207-162">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

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

### <span data-ttu-id="1a207-163">-Force</span><span class="sxs-lookup"><span data-stu-id="1a207-163">-Force</span></span>

<span data-ttu-id="1a207-164">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="1a207-164">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="1a207-165">Onderdrukkingen van beperkingen die voor komen dat `Install-Package` de slagen worden voltooid, met uitzonde ring van beveiliging.</span><span class="sxs-lookup"><span data-stu-id="1a207-165">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="1a207-166">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="1a207-166">-ForceBootstrap</span></span>

<span data-ttu-id="1a207-167">Forceert **Package Management** de pakket provider automatisch te installeren voor het opgegeven pakket.</span><span class="sxs-lookup"><span data-stu-id="1a207-167">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="1a207-168">-Headers</span><span class="sxs-lookup"><span data-stu-id="1a207-168">-Headers</span></span>

<span data-ttu-id="1a207-169">Hiermee geeft u de pakket headers op.</span><span class="sxs-lookup"><span data-stu-id="1a207-169">Specifies the package headers.</span></span>

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

### <span data-ttu-id="1a207-170">-Bevat</span><span class="sxs-lookup"><span data-stu-id="1a207-170">-Includes</span></span>

<span data-ttu-id="1a207-171">Hiermee wordt aangegeven of `Install-Package` alle pakket typen moeten worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="1a207-171">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="1a207-172">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="1a207-172">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1a207-173">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1a207-173">Cmdlet</span></span>
- <span data-ttu-id="1a207-174">Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="1a207-174">DscResource</span></span>
- <span data-ttu-id="1a207-175">Functie</span><span class="sxs-lookup"><span data-stu-id="1a207-175">Function</span></span>
- <span data-ttu-id="1a207-176">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="1a207-176">RoleCapability</span></span>
- <span data-ttu-id="1a207-177">Werkstroom</span><span class="sxs-lookup"><span data-stu-id="1a207-177">Workflow</span></span>

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

### <span data-ttu-id="1a207-178">-Input object</span><span class="sxs-lookup"><span data-stu-id="1a207-178">-InputObject</span></span>

<span data-ttu-id="1a207-179">Accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="1a207-179">Accepts pipeline input.</span></span> <span data-ttu-id="1a207-180">Hiermee geeft u een pakket op met behulp van het **SoftwareIdentity** -type van het pakket.</span><span class="sxs-lookup"><span data-stu-id="1a207-180">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="1a207-181">`Find-Package` Hiermee wordt een **SoftwareIdentity** -object uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-181">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

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

### <span data-ttu-id="1a207-182">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="1a207-182">-InstallUpdate</span></span>

<span data-ttu-id="1a207-183">Hiermee wordt aangegeven dat `Install-Package` updates worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-183">Indicates that `Install-Package` installs updates.</span></span>

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

### <span data-ttu-id="1a207-184">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="1a207-184">-MaximumVersion</span></span>

<span data-ttu-id="1a207-185">Hiermee geeft u de Maxi maal toegestane pakket versie op die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="1a207-185">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="1a207-186">Als u deze para meter niet opgeeft, `Install-Package` installeert de nieuwste versie van het pakket.</span><span class="sxs-lookup"><span data-stu-id="1a207-186">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="1a207-187">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="1a207-187">-MinimumVersion</span></span>

<span data-ttu-id="1a207-188">Hiermee geeft u de mini maal toegestane pakket versie op die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="1a207-188">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="1a207-189">Als u deze para meter niet toevoegt, `Install-Package` installeert de nieuwste versie van het pakket die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="1a207-189">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="1a207-190">-Name</span><span class="sxs-lookup"><span data-stu-id="1a207-190">-Name</span></span>

<span data-ttu-id="1a207-191">Hiermee geeft u een of meer pakket namen op.</span><span class="sxs-lookup"><span data-stu-id="1a207-191">Specifies one or more package names.</span></span> <span data-ttu-id="1a207-192">Meerdere pakket namen moeten worden gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="1a207-192">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="1a207-193">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="1a207-193">-NoPathUpdate</span></span>

<span data-ttu-id="1a207-194">**NoPathUpdate** is alleen van toepassing op de `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a207-194">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="1a207-195">**NoPathUpdate** is een dynamische para meter die door de provider wordt toegevoegd en niet wordt ondersteund door `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="1a207-195">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

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

### <span data-ttu-id="1a207-196">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="1a207-196">-PackageManagementProvider</span></span>

<span data-ttu-id="1a207-197">Hiermee geeft u de naam van de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="1a207-197">Specifies the name of the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="1a207-198">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="1a207-198">-ProviderName</span></span>

<span data-ttu-id="1a207-199">Hiermee geeft u een of meer pakket provider namen op voor het bereik van uw pakket zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="1a207-199">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="1a207-200">U kunt pakket provider namen ophalen door de cmdlet uit te voeren `Get-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="1a207-200">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="1a207-201">-Proxy</span><span class="sxs-lookup"><span data-stu-id="1a207-201">-Proxy</span></span>

<span data-ttu-id="1a207-202">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met een Internet bron.</span><span class="sxs-lookup"><span data-stu-id="1a207-202">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="1a207-203">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="1a207-203">-ProxyCredential</span></span>

<span data-ttu-id="1a207-204">Hiermee geeft u een gebruikers account op dat gemachtigd is om de proxy server te gebruiken die is opgegeven met de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="1a207-204">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="1a207-205">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="1a207-205">-PublishLocation</span></span>

<span data-ttu-id="1a207-206">Hiermee geeft u het pad op naar de gepubliceerde locatie van een pakket.</span><span class="sxs-lookup"><span data-stu-id="1a207-206">Specifies the path to a package's published location.</span></span>

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

### <span data-ttu-id="1a207-207">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="1a207-207">-RequiredVersion</span></span>

<span data-ttu-id="1a207-208">Hiermee geeft u de exacte toegestane versie van het pakket op dat u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="1a207-208">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="1a207-209">Als u deze para meter niet toevoegt, `Install-Package` installeert de nieuwste versie van het pakket die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="1a207-209">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="1a207-210">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="1a207-210">-RoleCapability</span></span>

<span data-ttu-id="1a207-211">Hiermee wordt een matrix met functie mogelijkheden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1a207-211">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="1a207-212">-Bereik</span><span class="sxs-lookup"><span data-stu-id="1a207-212">-Scope</span></span>

<span data-ttu-id="1a207-213">Hiermee geeft u het bereik op waarvoor het pakket moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-213">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="1a207-214">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="1a207-214">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1a207-215">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="1a207-215">CurrentUser</span></span>
- <span data-ttu-id="1a207-216">AllUsers</span><span class="sxs-lookup"><span data-stu-id="1a207-216">AllUsers</span></span>

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

### <span data-ttu-id="1a207-217">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="1a207-217">-ScriptPublishLocation</span></span>

<span data-ttu-id="1a207-218">Hiermee geeft u het pad op naar de gepubliceerde locatie van een script.</span><span class="sxs-lookup"><span data-stu-id="1a207-218">Specifies the path to a script's published location.</span></span>

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

### <span data-ttu-id="1a207-219">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="1a207-219">-ScriptSourceLocation</span></span>

<span data-ttu-id="1a207-220">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="1a207-220">Specifies the script source location.</span></span>

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

### <span data-ttu-id="1a207-221">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="1a207-221">-SkipDependencies</span></span>

<span data-ttu-id="1a207-222">Slaat de installatie van software-afhankelijkheden over.</span><span class="sxs-lookup"><span data-stu-id="1a207-222">Skips the installation of software dependencies.</span></span>

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

### <span data-ttu-id="1a207-223">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="1a207-223">-SkipPublisherCheck</span></span>

<span data-ttu-id="1a207-224">Hiermee kunt u een pakket versie ophalen die nieuwer is dan de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="1a207-224">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="1a207-225">Bijvoorbeeld een geïnstalleerd pakket dat digitaal is ondertekend door een vertrouwde uitgever, maar een nieuwe versie niet digitaal is ondertekend.</span><span class="sxs-lookup"><span data-stu-id="1a207-225">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="1a207-226">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="1a207-226">-SkipValidate</span></span>

<span data-ttu-id="1a207-227">Switch waarmee de validatie van de referenties van een pakket wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1a207-227">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="1a207-228">-Source</span><span class="sxs-lookup"><span data-stu-id="1a207-228">-Source</span></span>

<span data-ttu-id="1a207-229">Hiermee geeft u een of meer pakket bronnen op.</span><span class="sxs-lookup"><span data-stu-id="1a207-229">Specifies one or more package sources.</span></span> <span data-ttu-id="1a207-230">Meerdere pakket bron namen moeten worden gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="1a207-230">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="1a207-231">U kunt pakket bron namen ophalen door de cmdlet uit te voeren `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="1a207-231">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="1a207-232">-Tag</span><span class="sxs-lookup"><span data-stu-id="1a207-232">-Tag</span></span>

<span data-ttu-id="1a207-233">Hiermee geeft u een of meer teken reeksen op waarnaar moet worden gezocht in de meta gegevens van het pakket.</span><span class="sxs-lookup"><span data-stu-id="1a207-233">Specifies one or more strings to search for in the package metadata.</span></span>

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

### <span data-ttu-id="1a207-234">-Type</span><span class="sxs-lookup"><span data-stu-id="1a207-234">-Type</span></span>

<span data-ttu-id="1a207-235">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of beide.</span><span class="sxs-lookup"><span data-stu-id="1a207-235">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="1a207-236">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="1a207-236">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1a207-237">Module</span><span class="sxs-lookup"><span data-stu-id="1a207-237">Module</span></span>
- <span data-ttu-id="1a207-238">Script</span><span class="sxs-lookup"><span data-stu-id="1a207-238">Script</span></span>
- <span data-ttu-id="1a207-239">Alles</span><span class="sxs-lookup"><span data-stu-id="1a207-239">All</span></span>

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

### <span data-ttu-id="1a207-240">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1a207-240">-Confirm</span></span>

<span data-ttu-id="1a207-241">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1a207-241">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1a207-242">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1a207-242">-WhatIf</span></span>

<span data-ttu-id="1a207-243">Laat zien wat er zou gebeuren als de `Install-Package` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-243">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="1a207-244">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1a207-244">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1a207-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a207-245">CommonParameters</span></span>

<span data-ttu-id="1a207-246">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1a207-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1a207-247">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1a207-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1a207-248">INVOER</span><span class="sxs-lookup"><span data-stu-id="1a207-248">INPUTS</span></span>

### <span data-ttu-id="1a207-249">`Install-Package` accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="1a207-249">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="1a207-250">UITVOER</span><span class="sxs-lookup"><span data-stu-id="1a207-250">OUTPUTS</span></span>

### <span data-ttu-id="1a207-251">SoftwareIdentity []</span><span class="sxs-lookup"><span data-stu-id="1a207-251">SoftwareIdentity[]</span></span>

## <span data-ttu-id="1a207-252">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="1a207-252">NOTES</span></span>

<span data-ttu-id="1a207-253">Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a207-253">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="1a207-254">Dynamische para meters zijn specifiek voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="1a207-254">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="1a207-255">De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.</span><span class="sxs-lookup"><span data-stu-id="1a207-255">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="1a207-256">`Install-Package`Heeft bijvoorbeeld de para meter **PowerShellGet** met de waarde `-NoPathUpdate` , `AllowClobber` en `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="1a207-256">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1a207-257">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="1a207-257">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="1a207-258">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="1a207-258">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="1a207-259">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="1a207-259">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="1a207-260">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1a207-260">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="1a207-261">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="1a207-261">RELATED LINKS</span></span>

[<span data-ttu-id="1a207-262">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="1a207-262">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="1a207-263">Zoeken-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="1a207-263">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="1a207-264">Get-Help</span><span class="sxs-lookup"><span data-stu-id="1a207-264">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="1a207-265">Get-Package</span><span class="sxs-lookup"><span data-stu-id="1a207-265">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="1a207-266">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="1a207-266">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="1a207-267">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="1a207-267">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="1a207-268">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="1a207-268">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="1a207-269">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="1a207-269">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="1a207-270">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="1a207-270">Uninstall-Package</span></span>](Uninstall-Package.md)
