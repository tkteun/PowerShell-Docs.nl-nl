---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 058ed7f90e63bd7ca7a29cf6c89864a30255662a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250270"
---
# <span data-ttu-id="c0543-103">Install-Package</span><span class="sxs-lookup"><span data-stu-id="c0543-103">Install-Package</span></span>

## <span data-ttu-id="c0543-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c0543-104">SYNOPSIS</span></span>
<span data-ttu-id="c0543-105">Hiermee worden een of meer software pakketten geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-105">Installs one or more software packages.</span></span>

## <span data-ttu-id="c0543-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c0543-106">SYNTAX</span></span>

### <span data-ttu-id="c0543-107">PackageBySearch (standaard)</span><span class="sxs-lookup"><span data-stu-id="c0543-107">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="c0543-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="c0543-108">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="c0543-109">Program ma's: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="c0543-109">Programs:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-IncludeWindowsInstaller]
 [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="c0543-110">Program ma's: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="c0543-110">Programs:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-IncludeWindowsInstaller]
 [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="c0543-111">MSI: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="c0543-111">msi:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AdditionalArguments <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="c0543-112">MSI: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="c0543-112">msi:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AdditionalArguments <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="c0543-113">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="c0543-113">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="c0543-114">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="c0543-114">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="c0543-115">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="c0543-115">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="c0543-116">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="c0543-116">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="c0543-117">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c0543-117">DESCRIPTION</span></span>

<span data-ttu-id="c0543-118">`Install-Package`Met de cmdlet worden een of meer software pakketten op de lokale computer geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-118">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="c0543-119">Als u meerdere software bronnen hebt, gebruikt `Get-PackageProvider` en `Get-PackageSource` om details over uw providers weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c0543-119">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="c0543-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c0543-120">EXAMPLES</span></span>

### <span data-ttu-id="c0543-121">Voor beeld 1: een pakket installeren op pakket naam</span><span class="sxs-lookup"><span data-stu-id="c0543-121">Example 1: Install a package by package name</span></span>

<span data-ttu-id="c0543-122">`Install-Package`Met de cmdlet worden een software pakket en de bijbehorende afhankelijkheden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-122">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="c0543-123">`Install-Package` maakt gebruik van para meters om de **naam** en **bron** van het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="c0543-123">`Install-Package` uses parameters to specify the packages **Name** and **Source**.</span></span> <span data-ttu-id="c0543-124">De para meter **Credential** maakt gebruik van een domein gebruikers account met machtigingen voor het installeren van pakketten.</span><span class="sxs-lookup"><span data-stu-id="c0543-124">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="c0543-125">De opdracht vraagt u om het wacht woord voor het gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="c0543-125">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="c0543-126">Voor beeld 2: Find-Package gebruiken om een pakket te installeren</span><span class="sxs-lookup"><span data-stu-id="c0543-126">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="c0543-127">In dit voor beeld wordt het object dat `Find-Package` wordt geretourneerd door, verzonden door de pijp lijn en geïnstalleerd door `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="c0543-127">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="c0543-128">`Find-Package` maakt gebruik van de **name** -en **Source** -para meters voor het zoeken van een pakket.</span><span class="sxs-lookup"><span data-stu-id="c0543-128">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="c0543-129">Het object wordt via de pijp lijn verzonden en `Install-Package` het pakket wordt op de lokale computer geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-129">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="c0543-130">Voor beeld 3: pakketten installeren door een reeks versies op te geven</span><span class="sxs-lookup"><span data-stu-id="c0543-130">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="c0543-131">`Install-Package` maakt gebruik van de para meters **MinimumVersion** en **MaximumVersion** om een reeks software versies op te geven.</span><span class="sxs-lookup"><span data-stu-id="c0543-131">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="c0543-132">`Install-Package` maakt gebruik van de **naam** en de **bron** parameters om een pakket te vinden.</span><span class="sxs-lookup"><span data-stu-id="c0543-132">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="c0543-133">De para meters **MinimumVersion** en **MaximumVersion** geven een reeks software versies op.</span><span class="sxs-lookup"><span data-stu-id="c0543-133">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="c0543-134">De hoogste versie in het bereik is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-134">The highest version in the range is installed.</span></span>

## <span data-ttu-id="c0543-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c0543-135">PARAMETERS</span></span>

### <span data-ttu-id="c0543-136">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="c0543-136">-AcceptLicense</span></span>

 <span data-ttu-id="c0543-137">**AcceptLicense** accepteert de licentie overeenkomst automatisch tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="c0543-137">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

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

### <span data-ttu-id="c0543-138">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="c0543-138">-AllowClobber</span></span>

<span data-ttu-id="c0543-139">Onderdrukt waarschuwings berichten over conflicten met bestaande opdrachten.</span><span class="sxs-lookup"><span data-stu-id="c0543-139">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="c0543-140">Overschrijft bestaande opdrachten die dezelfde naam hebben als de opdrachten die worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-140">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="c0543-141">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="c0543-141">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="c0543-142">Hiermee kan de installatie van pakketten die zijn gemarkeerd als Prerelease.</span><span class="sxs-lookup"><span data-stu-id="c0543-142">Allows the installation of packages marked as prerelease.</span></span>

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

### <span data-ttu-id="c0543-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="c0543-143">-AllVersions</span></span>

<span data-ttu-id="c0543-144">`Install-Package` Hiermee worden alle beschik bare versies van het pakket geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-144">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="c0543-145">Standaard wordt alleen de nieuwste versie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-145">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="c0543-146">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="c0543-146">-Command</span></span>

<span data-ttu-id="c0543-147">Hiermee geeft u een of meer opdrachten op die worden `Install-Package` doorzocht.</span><span class="sxs-lookup"><span data-stu-id="c0543-147">Specifies one or more commands that `Install-Package` searches.</span></span>

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

### <span data-ttu-id="c0543-148">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="c0543-148">-ConfigFile</span></span>

<span data-ttu-id="c0543-149">Hiermee geeft u een pad op dat een configuratie bestand bevat.</span><span class="sxs-lookup"><span data-stu-id="c0543-149">Specifies a path that contains a configuration file.</span></span>

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

### <span data-ttu-id="c0543-150">-Bevat</span><span class="sxs-lookup"><span data-stu-id="c0543-150">-Contains</span></span>

<span data-ttu-id="c0543-151">`Install-Package` haalt objecten op als de para meter **contains** een waarde bevat die overeenkomt met de eigenschaps waarden van het object.</span><span class="sxs-lookup"><span data-stu-id="c0543-151">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

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

### <span data-ttu-id="c0543-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="c0543-152">-Credential</span></span>

<span data-ttu-id="c0543-153">Hiermee geeft u een gebruikers account op dat is gemachtigd om toegang te krijgen tot de computer en om opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c0543-153">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="c0543-154">Typ een gebruikers naam, zoals **gebruiker01** , **Domain01\User01** , of voer een **PSCredential** -object in dat door de `Get-Credential` cmdlet wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-154">Type a user name, such as **User01** , **Domain01\User01** , or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="c0543-155">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="c0543-155">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="c0543-156">Wanneer de para meter **Credential** niet is opgegeven, `Install-Package` gebruikt de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="c0543-156">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="c0543-157">-Bestemming</span><span class="sxs-lookup"><span data-stu-id="c0543-157">-Destination</span></span>

<span data-ttu-id="c0543-158">Hiermee geeft u een pad naar een invoer object op.</span><span class="sxs-lookup"><span data-stu-id="c0543-158">Specifies a path to an input object.</span></span>

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

### <span data-ttu-id="c0543-159">-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="c0543-159">-DscResource</span></span>

<span data-ttu-id="c0543-160">Hiermee geeft u een of meer desired state Configuration (DSC)-resources op waarnaar wordt gezocht `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="c0543-160">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="c0543-161">Gebruik de `Find-DscResource` cmdlet om DSC-resources te zoeken.</span><span class="sxs-lookup"><span data-stu-id="c0543-161">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

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

### <span data-ttu-id="c0543-162">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="c0543-162">-ExcludeVersion</span></span>

<span data-ttu-id="c0543-163">Schakel over om het versie nummer in het mappad uit te sluiten.</span><span class="sxs-lookup"><span data-stu-id="c0543-163">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="c0543-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="c0543-164">-Filter</span></span>

<span data-ttu-id="c0543-165">Hiermee geeft u de voor waarden voor het zoeken in de eigenschappen **name** en **Description** .</span><span class="sxs-lookup"><span data-stu-id="c0543-165">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

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

### <span data-ttu-id="c0543-166">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="c0543-166">-FilterOnTag</span></span>

<span data-ttu-id="c0543-167">Hiermee geeft u een label op waarmee resultaten worden gefilterd en worden geen resultaten opgenomen die het opgegeven label niet bevatten.</span><span class="sxs-lookup"><span data-stu-id="c0543-167">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

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

### <span data-ttu-id="c0543-168">-Force</span><span class="sxs-lookup"><span data-stu-id="c0543-168">-Force</span></span>

<span data-ttu-id="c0543-169">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="c0543-169">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="c0543-170">Onderdrukkingen van beperkingen die voor komen dat `Install-Package` de slagen worden voltooid, met uitzonde ring van beveiliging.</span><span class="sxs-lookup"><span data-stu-id="c0543-170">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="c0543-171">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="c0543-171">-ForceBootstrap</span></span>

<span data-ttu-id="c0543-172">Forceert **Package Management** de pakket provider automatisch te installeren voor het opgegeven pakket.</span><span class="sxs-lookup"><span data-stu-id="c0543-172">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="c0543-173">-Headers</span><span class="sxs-lookup"><span data-stu-id="c0543-173">-Headers</span></span>

<span data-ttu-id="c0543-174">Hiermee geeft u de pakket headers op.</span><span class="sxs-lookup"><span data-stu-id="c0543-174">Specifies the package headers.</span></span>

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

### <span data-ttu-id="c0543-175">-Bevat</span><span class="sxs-lookup"><span data-stu-id="c0543-175">-Includes</span></span>

<span data-ttu-id="c0543-176">Hiermee wordt aangegeven of `Install-Package` alle pakket typen moeten worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="c0543-176">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="c0543-177">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="c0543-177">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c0543-178">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0543-178">Cmdlet</span></span>
- <span data-ttu-id="c0543-179">Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="c0543-179">DscResource</span></span>
- <span data-ttu-id="c0543-180">Functie</span><span class="sxs-lookup"><span data-stu-id="c0543-180">Function</span></span>
- <span data-ttu-id="c0543-181">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="c0543-181">RoleCapability</span></span>
- <span data-ttu-id="c0543-182">Werkstroom</span><span class="sxs-lookup"><span data-stu-id="c0543-182">Workflow</span></span>

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

### <span data-ttu-id="c0543-183">-Input object</span><span class="sxs-lookup"><span data-stu-id="c0543-183">-InputObject</span></span>

<span data-ttu-id="c0543-184">Accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c0543-184">Accepts pipeline input.</span></span> <span data-ttu-id="c0543-185">Hiermee geeft u een pakket op met behulp van het **SoftwareIdentity** -type van het pakket.</span><span class="sxs-lookup"><span data-stu-id="c0543-185">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="c0543-186">`Find-Package` Hiermee wordt een **SoftwareIdentity** -object uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-186">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

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

### <span data-ttu-id="c0543-187">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="c0543-187">-InstallUpdate</span></span>

<span data-ttu-id="c0543-188">Hiermee wordt aangegeven dat `Install-Package` updates worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-188">Indicates that `Install-Package` installs updates.</span></span>

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

### <span data-ttu-id="c0543-189">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="c0543-189">-MaximumVersion</span></span>

<span data-ttu-id="c0543-190">Hiermee geeft u de Maxi maal toegestane pakket versie op die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="c0543-190">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="c0543-191">Als u deze para meter niet opgeeft, `Install-Package` installeert de nieuwste versie van het pakket.</span><span class="sxs-lookup"><span data-stu-id="c0543-191">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="c0543-192">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="c0543-192">-MinimumVersion</span></span>

<span data-ttu-id="c0543-193">Hiermee geeft u de mini maal toegestane pakket versie op die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="c0543-193">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="c0543-194">Als u deze para meter niet toevoegt, `Install-Package` installeert de nieuwste versie van het pakket die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="c0543-194">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="c0543-195">-Name</span><span class="sxs-lookup"><span data-stu-id="c0543-195">-Name</span></span>

<span data-ttu-id="c0543-196">Hiermee geeft u een of meer pakket namen op.</span><span class="sxs-lookup"><span data-stu-id="c0543-196">Specifies one or more package names.</span></span> <span data-ttu-id="c0543-197">Meerdere pakket namen moeten worden gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="c0543-197">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="c0543-198">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="c0543-198">-NoPathUpdate</span></span>

<span data-ttu-id="c0543-199">**NoPathUpdate** is alleen van toepassing op de `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0543-199">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="c0543-200">**NoPathUpdate** is een dynamische para meter die door de provider wordt toegevoegd en niet wordt ondersteund door `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="c0543-200">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

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

### <span data-ttu-id="c0543-201">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="c0543-201">-PackageManagementProvider</span></span>

<span data-ttu-id="c0543-202">Hiermee geeft u de naam van de **Package Management** -provider.</span><span class="sxs-lookup"><span data-stu-id="c0543-202">Specifies the name of the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="c0543-203">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="c0543-203">-ProviderName</span></span>

<span data-ttu-id="c0543-204">Hiermee geeft u een of meer pakket provider namen op voor het bereik van uw pakket zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="c0543-204">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="c0543-205">U kunt pakket provider namen ophalen door de cmdlet uit te voeren `Get-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="c0543-205">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="c0543-206">-Proxy</span><span class="sxs-lookup"><span data-stu-id="c0543-206">-Proxy</span></span>

<span data-ttu-id="c0543-207">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met een Internet bron.</span><span class="sxs-lookup"><span data-stu-id="c0543-207">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="c0543-208">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="c0543-208">-ProxyCredential</span></span>

<span data-ttu-id="c0543-209">Hiermee geeft u een gebruikers account op dat gemachtigd is om de proxy server te gebruiken die is opgegeven met de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="c0543-209">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="c0543-210">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="c0543-210">-PublishLocation</span></span>

<span data-ttu-id="c0543-211">Hiermee geeft u het pad op naar de gepubliceerde locatie van een pakket.</span><span class="sxs-lookup"><span data-stu-id="c0543-211">Specifies the path to a package's published location.</span></span>

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

### <span data-ttu-id="c0543-212">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c0543-212">-RequiredVersion</span></span>

<span data-ttu-id="c0543-213">Hiermee geeft u de exacte toegestane versie van het pakket op dat u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="c0543-213">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="c0543-214">Als u deze para meter niet toevoegt, `Install-Package` installeert de nieuwste versie van het pakket die voldoet aan de versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="c0543-214">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="c0543-215">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="c0543-215">-RoleCapability</span></span>

<span data-ttu-id="c0543-216">Hiermee wordt een matrix met functie mogelijkheden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c0543-216">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="c0543-217">-Bereik</span><span class="sxs-lookup"><span data-stu-id="c0543-217">-Scope</span></span>

<span data-ttu-id="c0543-218">Hiermee geeft u het bereik op waarvoor het pakket moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-218">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="c0543-219">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="c0543-219">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c0543-220">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="c0543-220">CurrentUser</span></span>
- <span data-ttu-id="c0543-221">AllUsers</span><span class="sxs-lookup"><span data-stu-id="c0543-221">AllUsers</span></span>

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

### <span data-ttu-id="c0543-222">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="c0543-222">-ScriptPublishLocation</span></span>

<span data-ttu-id="c0543-223">Hiermee geeft u het pad op naar de gepubliceerde locatie van een script.</span><span class="sxs-lookup"><span data-stu-id="c0543-223">Specifies the path to a script's published location.</span></span>

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

### <span data-ttu-id="c0543-224">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="c0543-224">-ScriptSourceLocation</span></span>

<span data-ttu-id="c0543-225">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="c0543-225">Specifies the script source location.</span></span>

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

### <span data-ttu-id="c0543-226">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="c0543-226">-SkipDependencies</span></span>

<span data-ttu-id="c0543-227">Slaat de installatie van software-afhankelijkheden over.</span><span class="sxs-lookup"><span data-stu-id="c0543-227">Skips the installation of software dependencies.</span></span>

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

### <span data-ttu-id="c0543-228">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="c0543-228">-SkipPublisherCheck</span></span>

<span data-ttu-id="c0543-229">Hiermee kunt u een pakket versie ophalen die nieuwer is dan de geïnstalleerde versie.</span><span class="sxs-lookup"><span data-stu-id="c0543-229">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="c0543-230">Bijvoorbeeld een geïnstalleerd pakket dat digitaal is ondertekend door een vertrouwde uitgever, maar een nieuwe versie niet digitaal is ondertekend.</span><span class="sxs-lookup"><span data-stu-id="c0543-230">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="c0543-231">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="c0543-231">-SkipValidate</span></span>

<span data-ttu-id="c0543-232">Switch waarmee de validatie van de referenties van een pakket wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="c0543-232">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="c0543-233">-Source</span><span class="sxs-lookup"><span data-stu-id="c0543-233">-Source</span></span>

<span data-ttu-id="c0543-234">Hiermee geeft u een of meer pakket bronnen op.</span><span class="sxs-lookup"><span data-stu-id="c0543-234">Specifies one or more package sources.</span></span> <span data-ttu-id="c0543-235">Meerdere pakket bron namen moeten worden gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="c0543-235">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="c0543-236">U kunt pakket bron namen ophalen door de cmdlet uit te voeren `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="c0543-236">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="c0543-237">-Tag</span><span class="sxs-lookup"><span data-stu-id="c0543-237">-Tag</span></span>

<span data-ttu-id="c0543-238">Hiermee geeft u een of meer teken reeksen op waarnaar moet worden gezocht in de meta gegevens van het pakket.</span><span class="sxs-lookup"><span data-stu-id="c0543-238">Specifies one or more strings to search for in the package metadata.</span></span>

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

### <span data-ttu-id="c0543-239">-Type</span><span class="sxs-lookup"><span data-stu-id="c0543-239">-Type</span></span>

<span data-ttu-id="c0543-240">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of beide.</span><span class="sxs-lookup"><span data-stu-id="c0543-240">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="c0543-241">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="c0543-241">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c0543-242">Module</span><span class="sxs-lookup"><span data-stu-id="c0543-242">Module</span></span>
- <span data-ttu-id="c0543-243">Script</span><span class="sxs-lookup"><span data-stu-id="c0543-243">Script</span></span>
- <span data-ttu-id="c0543-244">Alles</span><span class="sxs-lookup"><span data-stu-id="c0543-244">All</span></span>

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

### <span data-ttu-id="c0543-245">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c0543-245">-Confirm</span></span>

<span data-ttu-id="c0543-246">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c0543-246">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c0543-247">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c0543-247">-WhatIf</span></span>

<span data-ttu-id="c0543-248">Laat zien wat er zou gebeuren als de `Install-Package` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-248">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="c0543-249">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c0543-249">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c0543-250">-AdditionalArguments</span><span class="sxs-lookup"><span data-stu-id="c0543-250">-AdditionalArguments</span></span>

<span data-ttu-id="c0543-251">Hiermee geeft u een of meer aanvullende argumenten voor installatie op.</span><span class="sxs-lookup"><span data-stu-id="c0543-251">Specifies one or more additional arguments for installation.</span></span>

```yaml
Type: System.String[]
Parameter Sets: msi:PackageBySearch, msi:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0543-252">-IncludeSystemComponent</span><span class="sxs-lookup"><span data-stu-id="c0543-252">-IncludeSystemComponent</span></span>

<span data-ttu-id="c0543-253">Geeft aan dat deze cmdlet systeem onderdelen bevat in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="c0543-253">Indicates that this cmdlet includes system components in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageBySearch, Programs:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0543-254">-IncludeWindowsInstaller</span><span class="sxs-lookup"><span data-stu-id="c0543-254">-IncludeWindowsInstaller</span></span>

<span data-ttu-id="c0543-255">Geeft aan dat deze cmdlet de Windows Installer bevat in de resultaten.</span><span class="sxs-lookup"><span data-stu-id="c0543-255">Indicates that this cmdlet includes the Windows installer in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageBySearch, Programs:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0543-256">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0543-256">CommonParameters</span></span>

<span data-ttu-id="c0543-257">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c0543-257">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c0543-258">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c0543-258">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c0543-259">INVOER</span><span class="sxs-lookup"><span data-stu-id="c0543-259">INPUTS</span></span>

### <span data-ttu-id="c0543-260">`Install-Package` accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="c0543-260">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="c0543-261">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c0543-261">OUTPUTS</span></span>

### <span data-ttu-id="c0543-262">SoftwareIdentity []</span><span class="sxs-lookup"><span data-stu-id="c0543-262">SoftwareIdentity[]</span></span>

## <span data-ttu-id="c0543-263">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c0543-263">NOTES</span></span>

<span data-ttu-id="c0543-264">Het opnemen van een pakket provider in een opdracht kan dynamische para meters beschikbaar maken voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0543-264">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="c0543-265">Dynamische para meters zijn specifiek voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="c0543-265">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="c0543-266">De `Get-Help` cmdlet geeft een lijst van de parameter sets van de cmdlet en bevat de parameterset van de provider.</span><span class="sxs-lookup"><span data-stu-id="c0543-266">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="c0543-267">`Install-Package`Heeft bijvoorbeeld de para meter **PowerShellGet** met de waarde `-NoPathUpdate` , `AllowClobber` en `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="c0543-267">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="c0543-268">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c0543-268">RELATED LINKS</span></span>

[<span data-ttu-id="c0543-269">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="c0543-269">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="c0543-270">Zoeken-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="c0543-270">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="c0543-271">Get-Help</span><span class="sxs-lookup"><span data-stu-id="c0543-271">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="c0543-272">Get-Package</span><span class="sxs-lookup"><span data-stu-id="c0543-272">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="c0543-273">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="c0543-273">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="c0543-274">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="c0543-274">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="c0543-275">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="c0543-275">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="c0543-276">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="c0543-276">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="c0543-277">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="c0543-277">Uninstall-Package</span></span>](Uninstall-Package.md)
