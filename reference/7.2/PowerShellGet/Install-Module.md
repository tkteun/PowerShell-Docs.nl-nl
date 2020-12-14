---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: f4fcf349c439baf4813c37af4bf56c26a46c7877
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889263"
---
# <span data-ttu-id="b70c0-102">Install-Module</span><span class="sxs-lookup"><span data-stu-id="b70c0-102">Install-Module</span></span>

## <span data-ttu-id="b70c0-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b70c0-103">SYNOPSIS</span></span>
<span data-ttu-id="b70c0-104">Hiermee downloadt u een of meer modules uit een opslag plaats en installeert u deze op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b70c0-104">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

## <span data-ttu-id="b70c0-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b70c0-105">SYNTAX</span></span>

### <span data-ttu-id="b70c0-106">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="b70c0-106">NameParameterSet (Default)</span></span>

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b70c0-107">Input object</span><span class="sxs-lookup"><span data-stu-id="b70c0-107">InputObject</span></span>

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b70c0-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b70c0-108">DESCRIPTION</span></span>

<span data-ttu-id="b70c0-109">De `Install-Module` cmdlet haalt een of meer modules op die voldoen aan opgegeven criteria vanuit een online opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="b70c0-109">The `Install-Module` cmdlet gets one or more modules that meet specified criteria from an online repository.</span></span> <span data-ttu-id="b70c0-110">De cmdlet controleert of de zoek resultaten geldige modules zijn en kopieert de module mappen naar de installatie locatie.</span><span class="sxs-lookup"><span data-stu-id="b70c0-110">The cmdlet verifies that search results are valid modules and copies the module folders to the installation location.</span></span> <span data-ttu-id="b70c0-111">Geïnstalleerde modules worden na de installatie niet automatisch geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-111">Installed modules are not automatically imported after installation.</span></span>
<span data-ttu-id="b70c0-112">U kunt filteren welke module is geïnstalleerd op basis van de minimum-, maximum-en exacte versie van de opgegeven modules.</span><span class="sxs-lookup"><span data-stu-id="b70c0-112">You can filter which module is installed based on the minimum, maximum, and exact versions of specified modules.</span></span>

<span data-ttu-id="b70c0-113">Als de module die wordt geïnstalleerd dezelfde naam of versie heeft, of opdrachten bevat in een bestaande module, worden waarschuwings berichten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b70c0-113">If the module being installed has the same name or version, or contains commands in an existing module, warning messages are displayed.</span></span> <span data-ttu-id="b70c0-114">Nadat u hebt bevestigd dat u de module wilt installeren en de waarschuwingen wilt negeren, gebruikt u de `-Force` `-AllowClobber` para meters en.</span><span class="sxs-lookup"><span data-stu-id="b70c0-114">After you confirm that you want to install the module and override the warnings, use the `-Force` and `-AllowClobber` parameters.</span></span> <span data-ttu-id="b70c0-115">Afhankelijk van de instellingen van uw opslag plaats moet u mogelijk een vraag beantwoorden om de module-installatie voort te zetten.</span><span class="sxs-lookup"><span data-stu-id="b70c0-115">Dependent upon your repository settings, you might need to answer a prompt for the module installation to continue.</span></span>

<span data-ttu-id="b70c0-116">In deze voor beelden wordt de [PowerShell Gallery](https://www.powershellgallery.com/) als de enige geregistreerde opslag plaats gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b70c0-116">These examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="b70c0-117">`Get-PSRepository` Hiermee worden de geregistreerde opslag plaatsen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b70c0-117">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="b70c0-118">Als u meerdere geregistreerde opslag plaatsen hebt, gebruikt u de `-Repository` para meter om de naam van de opslag plaats op te geven.</span><span class="sxs-lookup"><span data-stu-id="b70c0-118">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="b70c0-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b70c0-119">EXAMPLES</span></span>

### <span data-ttu-id="b70c0-120">Voor beeld 1: een module zoeken en installeren</span><span class="sxs-lookup"><span data-stu-id="b70c0-120">Example 1: Find and install a module</span></span>

<span data-ttu-id="b70c0-121">In dit voor beeld wordt een module in de opslag plaats gevonden en wordt de module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-121">This example finds a module in the repository and installs the module.</span></span>

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

<span data-ttu-id="b70c0-122">De `Find-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="b70c0-122">The `Find-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="b70c0-123">Standaard wordt de nieuwste versie van de module gedownload uit de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="b70c0-123">By default, the newest version of the module is downloaded from the repository.</span></span> <span data-ttu-id="b70c0-124">Het object wordt vanuit de pijp lijn naar de `Install-Module` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="b70c0-124">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="b70c0-125">`Install-Module` installeert de module voor alle gebruikers in `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="b70c0-125">`Install-Module` installs the module for all users in `$env:ProgramFiles\PowerShell\Modules`.</span></span>

### <span data-ttu-id="b70c0-126">Voor beeld 2: een module installeren op naam</span><span class="sxs-lookup"><span data-stu-id="b70c0-126">Example 2: Install a module by name</span></span>

<span data-ttu-id="b70c0-127">In dit voor beeld is de nieuwste versie van de **PowerShellGet** -module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-127">In this example, the newest version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet
```

<span data-ttu-id="b70c0-128">De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="b70c0-128">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="b70c0-129">Standaard wordt de nieuwste versie van de module gedownload uit de opslag plaats en geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-129">By default, the newest version of the module is downloaded from the repository and installed.</span></span>

### <span data-ttu-id="b70c0-130">Voor beeld 3: een module installeren met de minimale versie</span><span class="sxs-lookup"><span data-stu-id="b70c0-130">Example 3: Install a module using its minimum version</span></span>

<span data-ttu-id="b70c0-131">In dit voor beeld is de minimale versie van de **PowerShellGet** -module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-131">In this example, the minimum version of the **PowerShellGet** module is installed.</span></span> <span data-ttu-id="b70c0-132">De **MinimumVersion** para meter geeft u de laagste versie van de module op die moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-132">The **MinimumVersion** parameter specifies the lowest version of the module that should be installed.</span></span> <span data-ttu-id="b70c0-133">Als er een nieuwere versie van de module beschikbaar is, wordt die versie gedownload en geïnstalleerd voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="b70c0-133">If a newer version of the module is available, that version is downloaded and installed for all users.</span></span>

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

<span data-ttu-id="b70c0-134">De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="b70c0-134">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="b70c0-135">De para meter **MinimumVersion** geeft aan dat versie **2.0.1** is gedownload uit de opslag plaats en moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-135">The **MinimumVersion** parameter specifies that version **2.0.1** is downloaded from the repository and installed.</span></span> <span data-ttu-id="b70c0-136">Omdat versie **2.0.4** beschikbaar is, wordt die versie gedownload en geïnstalleerd voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="b70c0-136">Because version **2.0.4** is available, that version is downloaded and installed for all users.</span></span>

### <span data-ttu-id="b70c0-137">Voor beeld 4: een specifieke versie van een module installeren</span><span class="sxs-lookup"><span data-stu-id="b70c0-137">Example 4: Install a specific version of a module</span></span>

<span data-ttu-id="b70c0-138">In dit voor beeld wordt een specifieke versie van de **PowerShellGet** -module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-138">In this example, a specific version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

<span data-ttu-id="b70c0-139">De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="b70c0-139">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="b70c0-140">De para meter **RequiredVersion** geeft aan dat versie **2.0.0** wordt gedownload en geïnstalleerd voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="b70c0-140">The **RequiredVersion** parameter specifies that version **2.0.0** is downloaded and installed for all users.</span></span>

### <span data-ttu-id="b70c0-141">Voor beeld 5: een module alleen voor de huidige gebruiker installeren</span><span class="sxs-lookup"><span data-stu-id="b70c0-141">Example 5: Install a module only for the current user</span></span>

<span data-ttu-id="b70c0-142">In dit voor beeld wordt de nieuwste versie van een module gedownload en geïnstalleerd, alleen voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b70c0-142">This example downloads and installs the newest version of a module, only for the current user.</span></span>

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

<span data-ttu-id="b70c0-143">De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="b70c0-143">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>
<span data-ttu-id="b70c0-144">`Install-Module` downloadt en installeert de nieuwste versie van **PowerShellGet** in de map van de huidige gebruiker `$home\Documents\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="b70c0-144">`Install-Module` downloads and installs the newest version of **PowerShellGet** into the current user's directory, `$home\Documents\PowerShell\Modules`.</span></span>

## <span data-ttu-id="b70c0-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b70c0-145">PARAMETERS</span></span>

### <span data-ttu-id="b70c0-146">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="b70c0-146">-AcceptLicense</span></span>

<span data-ttu-id="b70c0-147">Voor modules waarvoor een licentie is vereist, accepteert **AcceptLicense** automatisch de licentie overeenkomst tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="b70c0-147">For modules that require a license, **AcceptLicense** automatically accepts the license agreement during installation.</span></span> <span data-ttu-id="b70c0-148">Zie voor meer informatie [modules waarvoor acceptatie van licenties is vereist](/powershell/scripting/gallery/concepts/module-license-acceptance).</span><span class="sxs-lookup"><span data-stu-id="b70c0-148">For more information, see [Modules Requiring License Acceptance](/powershell/scripting/gallery/concepts/module-license-acceptance).</span></span>

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

### <span data-ttu-id="b70c0-149">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="b70c0-149">-AllowClobber</span></span>

<span data-ttu-id="b70c0-150">Onderdrukt waarschuwings berichten over de installatie conflicten met bestaande opdrachten op een computer.</span><span class="sxs-lookup"><span data-stu-id="b70c0-150">Overrides warning messages about installation conflicts about existing commands on a computer.</span></span>
<span data-ttu-id="b70c0-151">Overschrijft bestaande opdrachten die dezelfde naam hebben als opdrachten die door een module worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-151">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>
<span data-ttu-id="b70c0-152">**AllowClobber** en **Force** kunnen samen worden gebruikt in een `Install-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="b70c0-152">**AllowClobber** and **Force** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="b70c0-153">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="b70c0-153">-AllowPrerelease</span></span>

<span data-ttu-id="b70c0-154">Hiermee kunt u een module installeren die als voorlopige versie is gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-154">Allows you to install a module marked as a pre-release.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b70c0-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b70c0-155">-Confirm</span></span>

<span data-ttu-id="b70c0-156">Vraagt u om bevestiging voordat de cmdlet wordt uitgevoerd `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="b70c0-156">Prompts you for confirmation before running the `Install-Module` cmdlet.</span></span>

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

### <span data-ttu-id="b70c0-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="b70c0-157">-Credential</span></span>

<span data-ttu-id="b70c0-158">Hiermee geeft u een gebruikers account op dat beschikt over rechten voor het installeren van een module voor een opgegeven pakket provider of bron.</span><span class="sxs-lookup"><span data-stu-id="b70c0-158">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="b70c0-159">-Force</span><span class="sxs-lookup"><span data-stu-id="b70c0-159">-Force</span></span>

<span data-ttu-id="b70c0-160">Hiermee wordt een module geïnstalleerd en worden waarschuwings berichten over de installatie conflicten van de module genegeerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-160">Installs a module and overrides warning messages about module installation conflicts.</span></span> <span data-ttu-id="b70c0-161">Als er al een module met dezelfde naam op de computer aanwezig is **, kunnen** er meerdere versies worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-161">If a module with the same name already exists on the computer, **Force** allows for multiple versions to be installed.</span></span> <span data-ttu-id="b70c0-162">Als er een bestaande module met dezelfde naam en versie is, wordt door **geforceerd** de versie overschreven.</span><span class="sxs-lookup"><span data-stu-id="b70c0-162">If there is an existing module with the same name and version, **Force** overwrites that version.</span></span> <span data-ttu-id="b70c0-163">**Force** en **AllowClobber** kunnen samen worden gebruikt in een `Install-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="b70c0-163">**Force** and **AllowClobber** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="b70c0-164">-Input object</span><span class="sxs-lookup"><span data-stu-id="b70c0-164">-InputObject</span></span>

<span data-ttu-id="b70c0-165">Wordt gebruikt voor de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b70c0-165">Used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b70c0-166">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b70c0-166">-MaximumVersion</span></span>

<span data-ttu-id="b70c0-167">Hiermee geeft u de maximum versie van één module op die moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-167">Specifies the maximum version of a single module to install.</span></span> <span data-ttu-id="b70c0-168">De geïnstalleerde versie moet kleiner zijn dan of gelijk zijn aan **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="b70c0-168">The version installed must be less than or equal to **MaximumVersion**.</span></span> <span data-ttu-id="b70c0-169">Als u meerdere modules wilt installeren, kunt u **MaximumVersion** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b70c0-169">If you want to install multiple modules, you cannot use **MaximumVersion**.</span></span> <span data-ttu-id="b70c0-170">**MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde `Install-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="b70c0-170">**MaximumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b70c0-171">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b70c0-171">-MinimumVersion</span></span>

<span data-ttu-id="b70c0-172">Hiermee geeft u de minimum versie op van één module die moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-172">Specifies the minimum version of a single module to install.</span></span> <span data-ttu-id="b70c0-173">De geïnstalleerde versie moet groter dan of gelijk zijn aan **MinimumVersion**.</span><span class="sxs-lookup"><span data-stu-id="b70c0-173">The version installed must be greater than or equal to **MinimumVersion**.</span></span> <span data-ttu-id="b70c0-174">Als er een nieuwere versie van de module beschikbaar is, wordt de nieuwere versie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-174">If there is a newer version of the module available, the newer version is installed.</span></span> <span data-ttu-id="b70c0-175">Als u meerdere modules wilt installeren, kunt u **MinimumVersion** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b70c0-175">If you want to install multiple modules, you cannot use **MinimumVersion**.</span></span>
<span data-ttu-id="b70c0-176">**MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde `Install-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="b70c0-176">**MinimumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b70c0-177">-Name</span><span class="sxs-lookup"><span data-stu-id="b70c0-177">-Name</span></span>

<span data-ttu-id="b70c0-178">Hiermee geeft u de exacte namen van modules op die u wilt installeren vanuit de online galerie.</span><span class="sxs-lookup"><span data-stu-id="b70c0-178">Specifies the exact names of modules to install from the online gallery.</span></span> <span data-ttu-id="b70c0-179">Een door komma's gescheiden lijst met module namen wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-179">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="b70c0-180">De module naam moet overeenkomen met de module naam in de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="b70c0-180">The module name must match the module name in the repository.</span></span> <span data-ttu-id="b70c0-181">Gebruiken `Find-Module` om een lijst met module namen op te halen.</span><span class="sxs-lookup"><span data-stu-id="b70c0-181">Use `Find-Module` to get a list of module names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b70c0-182">-PassThru</span><span class="sxs-lookup"><span data-stu-id="b70c0-182">-PassThru</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b70c0-183">-Proxy</span><span class="sxs-lookup"><span data-stu-id="b70c0-183">-Proxy</span></span>

<span data-ttu-id="b70c0-184">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="b70c0-184">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="b70c0-185">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="b70c0-185">-ProxyCredential</span></span>

<span data-ttu-id="b70c0-186">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="b70c0-186">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="b70c0-187">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="b70c0-187">-Repository</span></span>

<span data-ttu-id="b70c0-188">Gebruik de para meter **opslagplaats** om op te geven welke opslag plaats wordt gebruikt voor het downloaden en installeren van een module.</span><span class="sxs-lookup"><span data-stu-id="b70c0-188">Use the **Repository** parameter to specify which repository is used to download and install a module.</span></span> <span data-ttu-id="b70c0-189">Wordt gebruikt wanneer meerdere opslag plaatsen zijn geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-189">Used when multiple repositories are registered.</span></span> <span data-ttu-id="b70c0-190">Hiermee geeft u de naam van een geregistreerde opslag plaats in de `Install-Module` opdracht op.</span><span class="sxs-lookup"><span data-stu-id="b70c0-190">Specifies the name of a registered repository in the `Install-Module` command.</span></span> <span data-ttu-id="b70c0-191">Als u een opslag plaats wilt registreren, gebruikt u `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="b70c0-191">To register a repository, use `Register-PSRepository`.</span></span>
<span data-ttu-id="b70c0-192">Gebruik om geregistreerde opslag plaatsen weer te geven `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="b70c0-192">To display registered repositories, use `Get-PSRepository`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b70c0-193">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b70c0-193">-RequiredVersion</span></span>

<span data-ttu-id="b70c0-194">Hiermee geeft u de exacte versie van één module op die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="b70c0-194">Specifies the exact version of a single module to install.</span></span> <span data-ttu-id="b70c0-195">Als er geen overeenkomst in de opslag plaats voor de opgegeven versie is, wordt er een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b70c0-195">If there is no match in the repository for the specified version, an error is displayed.</span></span> <span data-ttu-id="b70c0-196">Als u meerdere modules wilt installeren, kunt u **RequiredVersion** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b70c0-196">If you want to install multiple modules, you cannot use **RequiredVersion**.</span></span> <span data-ttu-id="b70c0-197">**RequiredVersion** kan niet worden gebruikt in dezelfde `Install-Module` opdracht als **MinimumVersion** of **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="b70c0-197">**RequiredVersion** cannot be used in the same `Install-Module` command as **MinimumVersion** or **MaximumVersion**.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b70c0-198">-Bereik</span><span class="sxs-lookup"><span data-stu-id="b70c0-198">-Scope</span></span>

<span data-ttu-id="b70c0-199">Hiermee geeft u het installatie bereik van de module op.</span><span class="sxs-lookup"><span data-stu-id="b70c0-199">Specifies the installation scope of the module.</span></span> <span data-ttu-id="b70c0-200">De acceptabele waarden voor deze para meter zijn **ALLUSERS** en **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="b70c0-200">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span>

<span data-ttu-id="b70c0-201">Met het **ALLUSERS** -bereik worden modules geïnstalleerd op een locatie die toegankelijk is voor alle gebruikers van de computer:</span><span class="sxs-lookup"><span data-stu-id="b70c0-201">The **AllUsers** scope installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="b70c0-202">De map **CurrentUser** installeert modules op een locatie die alleen toegankelijk is voor de huidige gebruiker van de computer.</span><span class="sxs-lookup"><span data-stu-id="b70c0-202">The **CurrentUser** installs modules in a location that is accessible only to the current user of the computer.</span></span> <span data-ttu-id="b70c0-203">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b70c0-203">For example:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="b70c0-204">Als er geen **bereik** is gedefinieerd, wordt de standaard waarde ingesteld op basis van de PowerShellGet-versie.</span><span class="sxs-lookup"><span data-stu-id="b70c0-204">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="b70c0-205">In PowerShellGet-versies 2.0.0 en hoger is de standaard versie **CurrentUser**, waarvoor geen uitbrei ding van bevoegdheden voor installatie vereist is.</span><span class="sxs-lookup"><span data-stu-id="b70c0-205">In PowerShellGet versions 2.0.0 and above, the default is **CurrentUser**, which does not require elevation for install.</span></span>
- <span data-ttu-id="b70c0-206">In PowerShellGet 1. x versies is de standaard waarde **ALLUSERS**, waarvoor uitbrei ding van bevoegdheden vereist is voor installatie.</span><span class="sxs-lookup"><span data-stu-id="b70c0-206">In PowerShellGet 1.x versions, the default is **AllUsers**, which requires elevation for install.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b70c0-207">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="b70c0-207">-SkipPublisherCheck</span></span>

<span data-ttu-id="b70c0-208">Hiermee kunt u een nieuwere versie installeren van een module die al op uw computer aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="b70c0-208">Allows you to install a newer version of a module that already exists on your computer.</span></span> <span data-ttu-id="b70c0-209">Bijvoorbeeld wanneer een bestaande module digitaal is ondertekend door een vertrouwde uitgever, maar de nieuwe versie niet digitaal is ondertekend door een vertrouwde uitgever.</span><span class="sxs-lookup"><span data-stu-id="b70c0-209">For example, when an existing module is digitally signed by a trusted publisher but the new version is not digitally signed by a trusted publisher.</span></span>

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

### <span data-ttu-id="b70c0-210">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b70c0-210">-WhatIf</span></span>

<span data-ttu-id="b70c0-211">Laat zien wat er zou gebeuren als een `Install-Module` opdracht werd uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-211">Shows what would happen if an `Install-Module` command was run.</span></span> <span data-ttu-id="b70c0-212">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-212">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b70c0-213">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b70c0-213">CommonParameters</span></span>

<span data-ttu-id="b70c0-214">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b70c0-214">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b70c0-215">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b70c0-215">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b70c0-216">INVOER</span><span class="sxs-lookup"><span data-stu-id="b70c0-216">INPUTS</span></span>

### <span data-ttu-id="b70c0-217">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="b70c0-217">PSRepositoryItemInfo</span></span>

<span data-ttu-id="b70c0-218">`Find-Module` Hiermee maakt u **PSRepositoryItemInfo** -objecten waarnaar de pijp lijn kan worden verzonden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="b70c0-218">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span>

### <span data-ttu-id="b70c0-219">System.String[]</span><span class="sxs-lookup"><span data-stu-id="b70c0-219">System.String[]</span></span>

### <span data-ttu-id="b70c0-220">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="b70c0-220">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="b70c0-221">System. String</span><span class="sxs-lookup"><span data-stu-id="b70c0-221">System.String</span></span>

### <span data-ttu-id="b70c0-222">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="b70c0-222">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="b70c0-223">System. URI</span><span class="sxs-lookup"><span data-stu-id="b70c0-223">System.Uri</span></span>

## <span data-ttu-id="b70c0-224">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b70c0-224">OUTPUTS</span></span>

### <span data-ttu-id="b70c0-225">Micro soft. Power shell. commands. PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="b70c0-225">Microsoft.PowerShell.Commands.PSRepositoryItemInfo</span></span>

<span data-ttu-id="b70c0-226">Wanneer u de para meter **PassThru** gebruikt, wordt `Install-Module` een **PSRepositoryItemInfo** -object uitgevoerd voor de module.</span><span class="sxs-lookup"><span data-stu-id="b70c0-226">When using the **PassThru** parameter, `Install-Module` outputs a **PSRepositoryItemInfo** object for the module.</span></span> <span data-ttu-id="b70c0-227">Dit is dezelfde informatie die u van de cmdlet krijgt `Find-Module` .</span><span class="sxs-lookup"><span data-stu-id="b70c0-227">This is the same information that you get from the `Find-Module` cmdlet.</span></span>

## <span data-ttu-id="b70c0-228">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b70c0-228">NOTES</span></span>

<span data-ttu-id="b70c0-229">`Install-Module` wordt uitgevoerd op Power shell 5,0 of hoger, op Windows 7 of Windows 2008 R2 en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="b70c0-229">`Install-Module` runs on PowerShell 5.0 or later releases, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b70c0-230">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="b70c0-230">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="b70c0-231">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="b70c0-231">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="b70c0-232">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="b70c0-232">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="b70c0-233">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b70c0-233">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="b70c0-234">Als beveiligings best practice kunt u de code van een module evalueren voordat u cmdlets of functions voor de eerste keer uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b70c0-234">As a security best practice, evaluate a module's code before running any cmdlets or functions for the first time.</span></span> <span data-ttu-id="b70c0-235">Om te voor komen dat modules worden uitgevoerd die schadelijke code bevatten, worden geïnstalleerde modules na de installatie niet automatisch geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-235">To prevent running modules that contain malicious code, installed modules are not automatically imported after installation.</span></span>

<span data-ttu-id="b70c0-236">Als de module naam die is opgegeven door de para meter **name** niet voor komt in de opslag plaats, `Install-Module` wordt een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-236">If the module name specified by the **Name** parameter does not exist in the repository, `Install-Module` returns an error.</span></span>

<span data-ttu-id="b70c0-237">Als u meerdere modules wilt installeren, gebruikt u de para meter **name** en geeft u een door komma's gescheiden matrix van module namen op.</span><span class="sxs-lookup"><span data-stu-id="b70c0-237">To install multiple modules, use the **Name** parameter and specify a comma-separated array of module names.</span></span> <span data-ttu-id="b70c0-238">Als u meerdere module namen opgeeft, kunt u **MinimumVersion**, **MaximumVersion** of **RequiredVersion** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b70c0-238">If you specify multiple module names, you cannot use **MinimumVersion**, **MaximumVersion**, or **RequiredVersion**.</span></span> <span data-ttu-id="b70c0-239">`Find-Module` Hiermee maakt u **PSRepositoryItemInfo** -objecten waarnaar de pijp lijn kan worden verzonden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="b70c0-239">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span> <span data-ttu-id="b70c0-240">De pijp lijn is een andere manier om meerdere modules op te geven die u wilt installeren in één opdracht.</span><span class="sxs-lookup"><span data-stu-id="b70c0-240">The pipeline is another way to specify multiple modules to install in a single command.</span></span>

<span data-ttu-id="b70c0-241">Standaard worden modules voor het bereik van **ALLUSERS** geïnstalleerd in `$env:ProgramFiles\PowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="b70c0-241">By default, modules for the scope of **AllUsers** are installed in `$env:ProgramFiles\PowerShell\Modules`.</span></span> <span data-ttu-id="b70c0-242">De standaard instelling voor komt Verwar ring bij de installatie van Power shell desired state Configuration (DSC)-resources.</span><span class="sxs-lookup"><span data-stu-id="b70c0-242">The default prevents confusion when you install PowerShell Desired State Configuration (DSC) resources.</span></span>

<span data-ttu-id="b70c0-243">Een module-installatie mislukt en kan niet worden geïmporteerd als deze geen `.psm1` , `.psd1` of `.dll` dezelfde naam in de map heeft.</span><span class="sxs-lookup"><span data-stu-id="b70c0-243">A module installation fails and cannot be imported if it does not have a `.psm1`, `.psd1`, or `.dll` of the same name within the folder.</span></span> <span data-ttu-id="b70c0-244">Gebruik de para meter **Force** om de module te installeren.</span><span class="sxs-lookup"><span data-stu-id="b70c0-244">Use the **Force** parameter to install the module.</span></span>

<span data-ttu-id="b70c0-245">Als de versie van een bestaande module overeenkomt met de naam die is opgegeven door de para meter **name** en de para meter **MinimumVersion** of **RequiredVersion** niet wordt gebruikt, wordt `Install-Module` de module op de achtergrond uitgevoerd, maar wordt deze niet geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-245">If an existing module's version matches the name specified by the **Name** parameter, and the **MinimumVersion** or **RequiredVersion** parameter are not used, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="b70c0-246">Als de versie van een bestaande module groter is dan de waarde van de para meter **MinimumVersion** , of gelijk is aan de waarde van de para meter **RequiredVersion** , wordt `Install-Module` de module op de achtergrond voortgezet, maar wordt niet de modules geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b70c0-246">If an existing module's version is greater than the value of the **MinimumVersion** parameter, or equal to the value of the **RequiredVersion** parameter, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="b70c0-247">Als de bestaande module niet overeenkomt met de waarden die zijn opgegeven door de para meters **MinimumVersion** of **RequiredVersion** , treedt er een fout op in de `Install-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="b70c0-247">If the existing module does not match the values specified by the **MinimumVersion** or **RequiredVersion** parameters, an error occurs in the `Install-Module` command.</span></span> <span data-ttu-id="b70c0-248">Als de versie van de bestaande geïnstalleerde module bijvoorbeeld lager is dan de **MinimumVersion** -waarde of niet gelijk is aan de **RequiredVersion** -waarde.</span><span class="sxs-lookup"><span data-stu-id="b70c0-248">For example, if the version of the existing installed module is lower than the **MinimumVersion** value or not equal to the **RequiredVersion** value.</span></span>

<span data-ttu-id="b70c0-249">Bij een module-installatie worden ook alle afhankelijke modules geïnstalleerd die vereist zijn voor de module Uitgever.</span><span class="sxs-lookup"><span data-stu-id="b70c0-249">A module installation will also install any dependent modules specified as required by the module publisher.</span></span>
<span data-ttu-id="b70c0-250">De uitgever geeft de vereiste modules en hun versies op in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="b70c0-250">The publisher will specify the required modules and their versions in the module manifest.</span></span>

## <span data-ttu-id="b70c0-251">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b70c0-251">RELATED LINKS</span></span>

[<span data-ttu-id="b70c0-252">Find-Module</span><span class="sxs-lookup"><span data-stu-id="b70c0-252">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="b70c0-253">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b70c0-253">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="b70c0-254">Import-module</span><span class="sxs-lookup"><span data-stu-id="b70c0-254">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="b70c0-255">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="b70c0-255">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="b70c0-256">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b70c0-256">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="b70c0-257">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="b70c0-257">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="b70c0-258">Update-Module</span><span class="sxs-lookup"><span data-stu-id="b70c0-258">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="b70c0-259">about_Module</span><span class="sxs-lookup"><span data-stu-id="b70c0-259">about_Module</span></span>](../Microsoft.PowerShell.Core/About/about_Modules.md)
