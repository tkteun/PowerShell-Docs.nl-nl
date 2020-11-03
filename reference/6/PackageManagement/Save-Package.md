---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: f94f1e3feba96aa49d44c25f2775ac9cffd0c459
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250647"
---
# <span data-ttu-id="89bfb-103">Save-Package</span><span class="sxs-lookup"><span data-stu-id="89bfb-103">Save-Package</span></span>

## <span data-ttu-id="89bfb-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="89bfb-104">SYNOPSIS</span></span>
<span data-ttu-id="89bfb-105">Hiermee worden pakketten op de lokale computer opgeslagen zonder dat ze worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="89bfb-105">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="89bfb-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="89bfb-106">SYNTAX</span></span>

### <span data-ttu-id="89bfb-107">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="89bfb-107">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="89bfb-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="89bfb-108">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="89bfb-109">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="89bfb-109">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="89bfb-110">NuGet</span><span class="sxs-lookup"><span data-stu-id="89bfb-110">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="89bfb-111">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="89bfb-111">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="89bfb-112">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="89bfb-112">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="89bfb-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="89bfb-113">DESCRIPTION</span></span>

<span data-ttu-id="89bfb-114">`Save-Package`Met de cmdlet worden pakketten opgeslagen op de lokale computer, maar worden de pakketten niet geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="89bfb-114">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="89bfb-115">Met deze cmdlet wordt de nieuwste versie van een pakket opgeslagen, tenzij u een **RequiredVerion** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="89bfb-115">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion**.</span></span> <span data-ttu-id="89bfb-116">De para meters **Path** en **LiteralPath** sluiten elkaar wederzijds uit en kunnen niet worden toegevoegd aan dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="89bfb-116">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="89bfb-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="89bfb-117">EXAMPLES</span></span>

### <span data-ttu-id="89bfb-118">Voor beeld 1: een pakket opslaan op de lokale computer</span><span class="sxs-lookup"><span data-stu-id="89bfb-118">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="89bfb-119">In dit voor beeld wordt de nieuwste versie van het pakket opgeslagen in een map op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="89bfb-119">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="89bfb-120">De afhankelijkheden van het pakket worden gedownload met het pakket.</span><span class="sxs-lookup"><span data-stu-id="89bfb-120">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="89bfb-121">`Save-Package` maakt gebruik van de para meter **name** om het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="89bfb-121">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="89bfb-122">Het pakket wordt gedownload uit de opslag plaats die is opgegeven door de para meter **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="89bfb-122">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="89bfb-123">De para meter **Path** bepaalt waar het pakket wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="89bfb-123">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="89bfb-124">Voor beeld 2: een specifieke pakket versie opslaan</span><span class="sxs-lookup"><span data-stu-id="89bfb-124">Example 2: Save a specific package version</span></span>

<span data-ttu-id="89bfb-125">In dit voor beeld wordt de versie van het pakket opgegeven en opgeslagen in een map op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="89bfb-125">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="89bfb-126">`Save-Package` maakt gebruik van de para meter **name** om het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="89bfb-126">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="89bfb-127">**RequiredVersion** geeft een specifieke pakket versie aan.</span><span class="sxs-lookup"><span data-stu-id="89bfb-127">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="89bfb-128">Het pakket wordt gedownload uit de opslag plaats die is opgegeven door de para meter **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="89bfb-128">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="89bfb-129">De para meter **Path** bepaalt waar het pakket wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="89bfb-129">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="89bfb-130">Voor beeld 3: Find-Package gebruiken om een pakket op te slaan</span><span class="sxs-lookup"><span data-stu-id="89bfb-130">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="89bfb-131">Met deze opdracht wordt `Find-Package` de nieuwste versie van het pakket gevonden en wordt het object naar verzonden `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="89bfb-131">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="89bfb-132">`Find-Package` maakt gebruik van de para meter **name** om het pakket op te geven.</span><span class="sxs-lookup"><span data-stu-id="89bfb-132">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="89bfb-133">Het pakket wordt gedownload uit de opslag plaats die is opgegeven door de para meter **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="89bfb-133">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="89bfb-134">Het object wordt naar de pijp lijn verzonden `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="89bfb-134">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="89bfb-135">De para meter **Path** bepaalt waar het pakket wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="89bfb-135">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="89bfb-136">Voor beeld 4: het pakket opslaan en installeren</span><span class="sxs-lookup"><span data-stu-id="89bfb-136">Example 4: Save and install the package</span></span>

<span data-ttu-id="89bfb-137">De nieuwste versie van het pakket en de bijbehorende afhankelijkheden worden gedownload en geïnstalleerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="89bfb-137">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="89bfb-138">`Save-Package` Hiermee downloadt u het pakket bestand en de afhankelijkheden ervan naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="89bfb-138">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="89bfb-139">`Install-Package` Hiermee installeert u het pakket en de afhankelijkheden van de opgegeven map.</span><span class="sxs-lookup"><span data-stu-id="89bfb-139">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="89bfb-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="89bfb-140">PARAMETERS</span></span>

### <span data-ttu-id="89bfb-141">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="89bfb-141">-AcceptLicense</span></span>

<span data-ttu-id="89bfb-142">Accepteer de gebruiksrecht overeenkomst tijdens de installatie automatisch als het pakket deze vereist.</span><span class="sxs-lookup"><span data-stu-id="89bfb-142">Automatically accept the license agreement during installation if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-143">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="89bfb-143">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="89bfb-144">Toestaan dat pakketten die zijn gemarkeerd als Prerelease, worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="89bfb-144">Allows packages marked as Prerelease to be saved.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet, PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-145">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="89bfb-145">-AllVersions</span></span>

<span data-ttu-id="89bfb-146">Geeft aan dat met deze cmdlet alle beschik bare versies van het pakket worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="89bfb-146">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="89bfb-147">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="89bfb-147">-Command</span></span>

<span data-ttu-id="89bfb-148">Hiermee geeft u een of meer opdrachten op die zijn opgenomen in het pakket.</span><span class="sxs-lookup"><span data-stu-id="89bfb-148">Specifies one or more commands included in the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-149">-ConfigFile</span><span class="sxs-lookup"><span data-stu-id="89bfb-149">-ConfigFile</span></span>

<span data-ttu-id="89bfb-150">Hiermee geeft u een configuratie bestand op.</span><span class="sxs-lookup"><span data-stu-id="89bfb-150">Specifies a configuration File.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-151">-Bevat</span><span class="sxs-lookup"><span data-stu-id="89bfb-151">-Contains</span></span>

<span data-ttu-id="89bfb-152">`Save-Package` haalt objecten op als een item in de eigenschaps waarden van het object exact overeenkomt met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="89bfb-152">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-153">-Credential</span><span class="sxs-lookup"><span data-stu-id="89bfb-153">-Credential</span></span>

<span data-ttu-id="89bfb-154">Hiermee geeft u een gebruikers account op dat gemachtigd is om een pakket op te slaan van een opgegeven pakket provider of-bron.</span><span class="sxs-lookup"><span data-stu-id="89bfb-154">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

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

### <span data-ttu-id="89bfb-155">-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="89bfb-155">-DscResource</span></span>

<span data-ttu-id="89bfb-156">Hiermee geeft u een of meer resources voor desired state Configuration (DSC) voor het pakket.</span><span class="sxs-lookup"><span data-stu-id="89bfb-156">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="89bfb-157">-Filter</span></span>

<span data-ttu-id="89bfb-158">Hiermee geeft u een filter op voor het pakket.</span><span class="sxs-lookup"><span data-stu-id="89bfb-158">Specifies a filter for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-159">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="89bfb-159">-FilterOnTag</span></span>

<span data-ttu-id="89bfb-160">Hiermee geeft u de tag op waarmee de resultaten worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="89bfb-160">Specifies the tag that filters the results.</span></span> <span data-ttu-id="89bfb-161">De resultaten die de opgegeven tag niet bevatten, worden uitgesloten.</span><span class="sxs-lookup"><span data-stu-id="89bfb-161">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-162">-Force</span><span class="sxs-lookup"><span data-stu-id="89bfb-162">-Force</span></span>

<span data-ttu-id="89bfb-163">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="89bfb-163">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="89bfb-164">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="89bfb-164">-ForceBootstrap</span></span>

<span data-ttu-id="89bfb-165">Geeft aan `Save-Package` dat **Package Management** automatisch de pakket provider voor het opgegeven pakket installeert.</span><span class="sxs-lookup"><span data-stu-id="89bfb-165">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="89bfb-166">-Headers</span><span class="sxs-lookup"><span data-stu-id="89bfb-166">-Headers</span></span>

<span data-ttu-id="89bfb-167">Hiermee geeft u de headers voor het pakket op.</span><span class="sxs-lookup"><span data-stu-id="89bfb-167">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-168">-Bevat</span><span class="sxs-lookup"><span data-stu-id="89bfb-168">-Includes</span></span>

<span data-ttu-id="89bfb-169">Hiermee worden de resources aangegeven die in het pakket zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="89bfb-169">Indicates the resources that the package includes.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: DscResource, Cmdlet, Function, Workflow, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-170">-Input object</span><span class="sxs-lookup"><span data-stu-id="89bfb-170">-InputObject</span></span>

<span data-ttu-id="89bfb-171">Een software-ID-object dat het pakket vertegenwoordigt dat u wilt opslaan.</span><span class="sxs-lookup"><span data-stu-id="89bfb-171">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="89bfb-172">Software-Id's maken deel uit van de resultaten van de `Find-Package` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="89bfb-172">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="89bfb-173">-LiteralPath</span></span>

<span data-ttu-id="89bfb-174">Hiermee geeft u het letterlijke pad op waarin u het pakket wilt opslaan.</span><span class="sxs-lookup"><span data-stu-id="89bfb-174">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="89bfb-175">U kunt deze para meter en de para meter **Path** niet aan dezelfde opdracht toevoegen.</span><span class="sxs-lookup"><span data-stu-id="89bfb-175">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="89bfb-176">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="89bfb-176">-MaximumVersion</span></span>

<span data-ttu-id="89bfb-177">Hiermee geeft u de maximum versie van het pakket op dat u wilt opslaan.</span><span class="sxs-lookup"><span data-stu-id="89bfb-177">Specifies the maximum version of the package that you want to save.</span></span>

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

### <span data-ttu-id="89bfb-178">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="89bfb-178">-MinimumVersion</span></span>

<span data-ttu-id="89bfb-179">Hiermee geeft u de minimum versie van het pakket dat u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="89bfb-179">Specifies the minimum version of the package that you want to find.</span></span>

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

### <span data-ttu-id="89bfb-180">-Name</span><span class="sxs-lookup"><span data-stu-id="89bfb-180">-Name</span></span>

<span data-ttu-id="89bfb-181">Hiermee geeft u een of meer pakket namen op.</span><span class="sxs-lookup"><span data-stu-id="89bfb-181">Specifies one or more package names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-182">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="89bfb-182">-PackageManagementProvider</span></span>

<span data-ttu-id="89bfb-183">Hiermee geeft u een pakket beheer provider.</span><span class="sxs-lookup"><span data-stu-id="89bfb-183">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-184">-Path</span><span class="sxs-lookup"><span data-stu-id="89bfb-184">-Path</span></span>

<span data-ttu-id="89bfb-185">Hiermee geeft u de locatie op de lokale computer op waarop het pakket moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="89bfb-185">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="89bfb-186">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="89bfb-186">-ProviderName</span></span>

<span data-ttu-id="89bfb-187">Hiermee geeft u een of meer provider namen op.</span><span class="sxs-lookup"><span data-stu-id="89bfb-187">Specifies one or more provider names.</span></span>

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

### <span data-ttu-id="89bfb-188">-Proxy</span><span class="sxs-lookup"><span data-stu-id="89bfb-188">-Proxy</span></span>

<span data-ttu-id="89bfb-189">Hiermee geeft u een proxy server voor de aanvraag op, in plaats van een rechtstreekse verbinding met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="89bfb-189">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="89bfb-190">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="89bfb-190">-ProxyCredential</span></span>

<span data-ttu-id="89bfb-191">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="89bfb-191">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="89bfb-192">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="89bfb-192">-PublishLocation</span></span>

<span data-ttu-id="89bfb-193">Hiermee geeft u de publicatie locatie op.</span><span class="sxs-lookup"><span data-stu-id="89bfb-193">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-194">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="89bfb-194">-RequiredVersion</span></span>

<span data-ttu-id="89bfb-195">Hiermee geeft u de exacte versie van het pakket op dat moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="89bfb-195">Specifies the exact version of the package to save.</span></span>

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

### <span data-ttu-id="89bfb-196">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="89bfb-196">-RoleCapability</span></span>

<span data-ttu-id="89bfb-197">Hiermee wordt een matrix met functie mogelijkheden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="89bfb-197">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-198">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="89bfb-198">-ScriptPublishLocation</span></span>

<span data-ttu-id="89bfb-199">Hiermee geeft u de publicatie locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="89bfb-199">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-200">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="89bfb-200">-ScriptSourceLocation</span></span>

<span data-ttu-id="89bfb-201">Hiermee geeft u de bron locatie van het script op.</span><span class="sxs-lookup"><span data-stu-id="89bfb-201">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-202">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="89bfb-202">-SkipValidate</span></span>

<span data-ttu-id="89bfb-203">Switch waarmee de validatie van de referenties van een pakket wordt overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="89bfb-203">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-204">-Source</span><span class="sxs-lookup"><span data-stu-id="89bfb-204">-Source</span></span>

<span data-ttu-id="89bfb-205">Hiermee geeft u een of meer pakket bronnen op.</span><span class="sxs-lookup"><span data-stu-id="89bfb-205">Specifies one or more package sources.</span></span>

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

### <span data-ttu-id="89bfb-206">-Tag</span><span class="sxs-lookup"><span data-stu-id="89bfb-206">-Tag</span></span>

<span data-ttu-id="89bfb-207">Hiermee geeft u een label op waarnaar moet worden gezocht in de meta gegevens van het pakket.</span><span class="sxs-lookup"><span data-stu-id="89bfb-207">Specifies a tag to search for within the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-208">-Type</span><span class="sxs-lookup"><span data-stu-id="89bfb-208">-Type</span></span>

<span data-ttu-id="89bfb-209">Hiermee geeft u op of u wilt zoeken naar pakketten met een module, een script of een van beide.</span><span class="sxs-lookup"><span data-stu-id="89bfb-209">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="89bfb-210">-Confirm</span><span class="sxs-lookup"><span data-stu-id="89bfb-210">-Confirm</span></span>

<span data-ttu-id="89bfb-211">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="89bfb-211">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="89bfb-212">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="89bfb-212">-WhatIf</span></span>

<span data-ttu-id="89bfb-213">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="89bfb-213">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="89bfb-214">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="89bfb-214">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="89bfb-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="89bfb-215">CommonParameters</span></span>

<span data-ttu-id="89bfb-216">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="89bfb-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="89bfb-217">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="89bfb-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="89bfb-218">INVOER</span><span class="sxs-lookup"><span data-stu-id="89bfb-218">INPUTS</span></span>

### <span data-ttu-id="89bfb-219">`Save-Package` objecten uit de pijp lijn accepteren.</span><span class="sxs-lookup"><span data-stu-id="89bfb-219">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="89bfb-220">UITVOER</span><span class="sxs-lookup"><span data-stu-id="89bfb-220">OUTPUTS</span></span>

### <span data-ttu-id="89bfb-221">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="89bfb-221">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="89bfb-222">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="89bfb-222">NOTES</span></span>

## <span data-ttu-id="89bfb-223">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="89bfb-223">RELATED LINKS</span></span>

[<span data-ttu-id="89bfb-224">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="89bfb-224">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="89bfb-225">Get-Package</span><span class="sxs-lookup"><span data-stu-id="89bfb-225">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="89bfb-226">Install-Package</span><span class="sxs-lookup"><span data-stu-id="89bfb-226">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="89bfb-227">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="89bfb-227">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="89bfb-228">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="89bfb-228">Uninstall-Package</span></span>](Uninstall-Package.md)
