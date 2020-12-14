---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Module
ms.openlocfilehash: ec9862e9003bd73e952422a8d15d373193a80c12
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889773"
---
# <span data-ttu-id="34817-103">Install-Module</span><span class="sxs-lookup"><span data-stu-id="34817-103">Install-Module</span></span>

## <span data-ttu-id="34817-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="34817-104">SYNOPSIS</span></span>
<span data-ttu-id="34817-105">Hiermee downloadt u een of meer modules uit een opslag plaats en installeert u deze op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="34817-105">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

## <span data-ttu-id="34817-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="34817-106">SYNTAX</span></span>

### <span data-ttu-id="34817-107">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="34817-107">NameParameterSet (Default)</span></span>

```
Install-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="34817-108">Input object</span><span class="sxs-lookup"><span data-stu-id="34817-108">InputObject</span></span>

```
Install-Module [-InputObject] <PSObject[]> [-Credential <PSCredential>] [-Scope <String>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllowClobber] [-SkipPublisherCheck] [-Force]
 [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="34817-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="34817-109">DESCRIPTION</span></span>

<span data-ttu-id="34817-110">De `Install-Module` cmdlet haalt een of meer modules op die voldoen aan opgegeven criteria vanuit een online opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="34817-110">The `Install-Module` cmdlet gets one or more modules that meet specified criteria from an online repository.</span></span> <span data-ttu-id="34817-111">De cmdlet controleert of de zoek resultaten geldige modules zijn en kopieert de module mappen naar de installatie locatie.</span><span class="sxs-lookup"><span data-stu-id="34817-111">The cmdlet verifies that search results are valid modules and copies the module folders to the installation location.</span></span> <span data-ttu-id="34817-112">Geïnstalleerde modules worden na de installatie niet automatisch geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="34817-112">Installed modules are not automatically imported after installation.</span></span>
<span data-ttu-id="34817-113">U kunt filteren welke module is geïnstalleerd op basis van de minimum-, maximum-en exacte versie van de opgegeven modules.</span><span class="sxs-lookup"><span data-stu-id="34817-113">You can filter which module is installed based on the minimum, maximum, and exact versions of specified modules.</span></span>

<span data-ttu-id="34817-114">Als de module die wordt geïnstalleerd dezelfde naam of versie heeft, of opdrachten bevat in een bestaande module, worden waarschuwings berichten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="34817-114">If the module being installed has the same name or version, or contains commands in an existing module, warning messages are displayed.</span></span> <span data-ttu-id="34817-115">Nadat u hebt bevestigd dat u de module wilt installeren en de waarschuwingen wilt negeren, gebruikt u de `-Force` `-AllowClobber` para meters en.</span><span class="sxs-lookup"><span data-stu-id="34817-115">After you confirm that you want to install the module and override the warnings, use the `-Force` and `-AllowClobber` parameters.</span></span> <span data-ttu-id="34817-116">Afhankelijk van de instellingen van uw opslag plaats moet u mogelijk een vraag beantwoorden om de module-installatie voort te zetten.</span><span class="sxs-lookup"><span data-stu-id="34817-116">Dependent upon your repository settings, you might need to answer a prompt for the module installation to continue.</span></span>

<span data-ttu-id="34817-117">In deze voor beelden wordt de [PowerShell Gallery](https://www.powershellgallery.com/) als de enige geregistreerde opslag plaats gebruikt.</span><span class="sxs-lookup"><span data-stu-id="34817-117">These examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="34817-118">`Get-PSRepository` Hiermee worden de geregistreerde opslag plaatsen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="34817-118">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="34817-119">Als u meerdere geregistreerde opslag plaatsen hebt, gebruikt u de `-Repository` para meter om de naam van de opslag plaats op te geven.</span><span class="sxs-lookup"><span data-stu-id="34817-119">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="34817-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="34817-120">EXAMPLES</span></span>

### <span data-ttu-id="34817-121">Voor beeld 1: een module zoeken en installeren</span><span class="sxs-lookup"><span data-stu-id="34817-121">Example 1: Find and install a module</span></span>

<span data-ttu-id="34817-122">In dit voor beeld wordt een module in de opslag plaats gevonden en wordt de module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-122">This example finds a module in the repository and installs the module.</span></span>

```powershell
Find-Module -Name PowerShellGet | Install-Module
```

<span data-ttu-id="34817-123">De `Find-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="34817-123">The `Find-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="34817-124">Standaard wordt de nieuwste versie van de module gedownload uit de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="34817-124">By default, the newest version of the module is downloaded from the repository.</span></span> <span data-ttu-id="34817-125">Het object wordt vanuit de pijp lijn naar de `Install-Module` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="34817-125">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="34817-126">`Install-Module` installeert de module voor alle gebruikers in `$env:ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="34817-126">`Install-Module` installs the module for all users in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>

### <span data-ttu-id="34817-127">Voor beeld 2: een module installeren op naam</span><span class="sxs-lookup"><span data-stu-id="34817-127">Example 2: Install a module by name</span></span>

<span data-ttu-id="34817-128">In dit voor beeld is de nieuwste versie van de **PowerShellGet** -module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-128">In this example, the newest version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet
```

<span data-ttu-id="34817-129">De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="34817-129">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="34817-130">Standaard wordt de nieuwste versie van de module gedownload uit de opslag plaats en geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-130">By default, the newest version of the module is downloaded from the repository and installed.</span></span>

### <span data-ttu-id="34817-131">Voor beeld 3: een module installeren met de minimale versie</span><span class="sxs-lookup"><span data-stu-id="34817-131">Example 3: Install a module using its minimum version</span></span>

<span data-ttu-id="34817-132">In dit voor beeld is de minimale versie van de **PowerShellGet** -module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-132">In this example, the minimum version of the **PowerShellGet** module is installed.</span></span> <span data-ttu-id="34817-133">De **MinimumVersion** para meter geeft u de laagste versie van de module op die moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-133">The **MinimumVersion** parameter specifies the lowest version of the module that should be installed.</span></span> <span data-ttu-id="34817-134">Als er een nieuwere versie van de module beschikbaar is, wordt die versie gedownload en geïnstalleerd voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="34817-134">If a newer version of the module is available, that version is downloaded and installed for all users.</span></span>

```powershell
Install-Module -Name PowerShellGet -MinimumVersion 2.0.1
```

<span data-ttu-id="34817-135">De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="34817-135">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="34817-136">De para meter **MinimumVersion** geeft aan dat versie **2.0.1** is gedownload uit de opslag plaats en moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-136">The **MinimumVersion** parameter specifies that version **2.0.1** is downloaded from the repository and installed.</span></span> <span data-ttu-id="34817-137">Omdat versie **2.0.4** beschikbaar is, wordt die versie gedownload en geïnstalleerd voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="34817-137">Because version **2.0.4** is available, that version is downloaded and installed for all users.</span></span>

### <span data-ttu-id="34817-138">Voor beeld 4: een specifieke versie van een module installeren</span><span class="sxs-lookup"><span data-stu-id="34817-138">Example 4: Install a specific version of a module</span></span>

<span data-ttu-id="34817-139">In dit voor beeld wordt een specifieke versie van de **PowerShellGet** -module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-139">In this example, a specific version of the **PowerShellGet** module is installed.</span></span>

```powershell
Install-Module -Name PowerShellGet -RequiredVersion 2.0.0
```

<span data-ttu-id="34817-140">De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="34817-140">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="34817-141">De para meter **RequiredVersion** geeft aan dat versie **2.0.0** wordt gedownload en geïnstalleerd voor alle gebruikers.</span><span class="sxs-lookup"><span data-stu-id="34817-141">The **RequiredVersion** parameter specifies that version **2.0.0** is downloaded and installed for all users.</span></span>

### <span data-ttu-id="34817-142">Voor beeld 5: een module alleen voor de huidige gebruiker installeren</span><span class="sxs-lookup"><span data-stu-id="34817-142">Example 5: Install a module only for the current user</span></span>

<span data-ttu-id="34817-143">In dit voor beeld wordt de nieuwste versie van een module gedownload en geïnstalleerd, alleen voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="34817-143">This example downloads and installs the newest version of a module, only for the current user.</span></span>

```powershell
Install-Module -Name PowerShellGet -Scope CurrentUser
```

<span data-ttu-id="34817-144">De `Install-Module` gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.</span><span class="sxs-lookup"><span data-stu-id="34817-144">The `Install-Module` uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>
<span data-ttu-id="34817-145">`Install-Module` downloadt en installeert de nieuwste versie van **PowerShellGet** in de map van de huidige gebruiker `$home\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="34817-145">`Install-Module` downloads and installs the newest version of **PowerShellGet** into the current user's directory, `$home\Documents\WindowsPowerShell\Modules`.</span></span>

## <span data-ttu-id="34817-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="34817-146">PARAMETERS</span></span>

### <span data-ttu-id="34817-147">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="34817-147">-AcceptLicense</span></span>

<span data-ttu-id="34817-148">Voor modules waarvoor een licentie is vereist, accepteert **AcceptLicense** automatisch de licentie overeenkomst tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="34817-148">For modules that require a license, **AcceptLicense** automatically accepts the license agreement during installation.</span></span> <span data-ttu-id="34817-149">Zie voor meer informatie [modules waarvoor acceptatie van licenties is vereist](/powershell/scripting/gallery/concepts/module-license-acceptance).</span><span class="sxs-lookup"><span data-stu-id="34817-149">For more information, see [Modules Requiring License Acceptance](/powershell/scripting/gallery/concepts/module-license-acceptance).</span></span>

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

### <span data-ttu-id="34817-150">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="34817-150">-AllowClobber</span></span>

<span data-ttu-id="34817-151">Onderdrukt waarschuwings berichten over de installatie conflicten met bestaande opdrachten op een computer.</span><span class="sxs-lookup"><span data-stu-id="34817-151">Overrides warning messages about installation conflicts about existing commands on a computer.</span></span>
<span data-ttu-id="34817-152">Overschrijft bestaande opdrachten die dezelfde naam hebben als opdrachten die door een module worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-152">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>
<span data-ttu-id="34817-153">**AllowClobber** en **Force** kunnen samen worden gebruikt in een `Install-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="34817-153">**AllowClobber** and **Force** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="34817-154">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="34817-154">-AllowPrerelease</span></span>

<span data-ttu-id="34817-155">Hiermee kunt u een module installeren die als voorlopige versie is gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="34817-155">Allows you to install a module marked as a pre-release.</span></span>

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

### <span data-ttu-id="34817-156">-Confirm</span><span class="sxs-lookup"><span data-stu-id="34817-156">-Confirm</span></span>

<span data-ttu-id="34817-157">Vraagt u om bevestiging voordat de cmdlet wordt uitgevoerd `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="34817-157">Prompts you for confirmation before running the `Install-Module` cmdlet.</span></span>

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

### <span data-ttu-id="34817-158">-Credential</span><span class="sxs-lookup"><span data-stu-id="34817-158">-Credential</span></span>

<span data-ttu-id="34817-159">Hiermee geeft u een gebruikers account op dat beschikt over rechten voor het installeren van een module voor een opgegeven pakket provider of bron.</span><span class="sxs-lookup"><span data-stu-id="34817-159">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="34817-160">-Force</span><span class="sxs-lookup"><span data-stu-id="34817-160">-Force</span></span>

<span data-ttu-id="34817-161">Hiermee wordt een module geïnstalleerd en worden waarschuwings berichten over de installatie conflicten van de module genegeerd.</span><span class="sxs-lookup"><span data-stu-id="34817-161">Installs a module and overrides warning messages about module installation conflicts.</span></span> <span data-ttu-id="34817-162">Als er al een module met dezelfde naam op de computer aanwezig is **, kunnen** er meerdere versies worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-162">If a module with the same name already exists on the computer, **Force** allows for multiple versions to be installed.</span></span> <span data-ttu-id="34817-163">Als er een bestaande module met dezelfde naam en versie is, wordt door **geforceerd** de versie overschreven.</span><span class="sxs-lookup"><span data-stu-id="34817-163">If there is an existing module with the same name and version, **Force** overwrites that version.</span></span> <span data-ttu-id="34817-164">**Force** en **AllowClobber** kunnen samen worden gebruikt in een `Install-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="34817-164">**Force** and **AllowClobber** can be used together in an `Install-Module` command.</span></span>

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

### <span data-ttu-id="34817-165">-Input object</span><span class="sxs-lookup"><span data-stu-id="34817-165">-InputObject</span></span>

<span data-ttu-id="34817-166">Wordt gebruikt voor de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="34817-166">Used for pipeline input.</span></span>

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

### <span data-ttu-id="34817-167">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="34817-167">-MaximumVersion</span></span>

<span data-ttu-id="34817-168">Hiermee geeft u de maximum versie van één module op die moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-168">Specifies the maximum version of a single module to install.</span></span> <span data-ttu-id="34817-169">De geïnstalleerde versie moet kleiner zijn dan of gelijk zijn aan **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="34817-169">The version installed must be less than or equal to **MaximumVersion**.</span></span> <span data-ttu-id="34817-170">Als u meerdere modules wilt installeren, kunt u **MaximumVersion** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="34817-170">If you want to install multiple modules, you cannot use **MaximumVersion**.</span></span> <span data-ttu-id="34817-171">**MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde `Install-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="34817-171">**MaximumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

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

### <span data-ttu-id="34817-172">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="34817-172">-MinimumVersion</span></span>

<span data-ttu-id="34817-173">Hiermee geeft u de minimum versie op van één module die moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-173">Specifies the minimum version of a single module to install.</span></span> <span data-ttu-id="34817-174">De geïnstalleerde versie moet groter dan of gelijk zijn aan **MinimumVersion**.</span><span class="sxs-lookup"><span data-stu-id="34817-174">The version installed must be greater than or equal to **MinimumVersion**.</span></span> <span data-ttu-id="34817-175">Als er een nieuwere versie van de module beschikbaar is, wordt de nieuwere versie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-175">If there is a newer version of the module available, the newer version is installed.</span></span> <span data-ttu-id="34817-176">Als u meerdere modules wilt installeren, kunt u **MinimumVersion** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="34817-176">If you want to install multiple modules, you cannot use **MinimumVersion**.</span></span>
<span data-ttu-id="34817-177">**MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde `Install-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="34817-177">**MinimumVersion** and **RequiredVersion** cannot be used in the same `Install-Module` command.</span></span>

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

### <span data-ttu-id="34817-178">-Name</span><span class="sxs-lookup"><span data-stu-id="34817-178">-Name</span></span>

<span data-ttu-id="34817-179">Hiermee geeft u de exacte namen van modules op die u wilt installeren vanuit de online galerie.</span><span class="sxs-lookup"><span data-stu-id="34817-179">Specifies the exact names of modules to install from the online gallery.</span></span> <span data-ttu-id="34817-180">Een door komma's gescheiden lijst met module namen wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="34817-180">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="34817-181">De module naam moet overeenkomen met de module naam in de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="34817-181">The module name must match the module name in the repository.</span></span> <span data-ttu-id="34817-182">Gebruiken `Find-Module` om een lijst met module namen op te halen.</span><span class="sxs-lookup"><span data-stu-id="34817-182">Use `Find-Module` to get a list of module names.</span></span>

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

### <span data-ttu-id="34817-183">-PassThru</span><span class="sxs-lookup"><span data-stu-id="34817-183">-PassThru</span></span>

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

### <span data-ttu-id="34817-184">-Proxy</span><span class="sxs-lookup"><span data-stu-id="34817-184">-Proxy</span></span>

<span data-ttu-id="34817-185">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="34817-185">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="34817-186">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="34817-186">-ProxyCredential</span></span>

<span data-ttu-id="34817-187">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="34817-187">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="34817-188">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="34817-188">-Repository</span></span>

<span data-ttu-id="34817-189">Gebruik de para meter **opslagplaats** om op te geven welke opslag plaats wordt gebruikt voor het downloaden en installeren van een module.</span><span class="sxs-lookup"><span data-stu-id="34817-189">Use the **Repository** parameter to specify which repository is used to download and install a module.</span></span> <span data-ttu-id="34817-190">Wordt gebruikt wanneer meerdere opslag plaatsen zijn geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="34817-190">Used when multiple repositories are registered.</span></span> <span data-ttu-id="34817-191">Hiermee geeft u de naam van een geregistreerde opslag plaats in de `Install-Module` opdracht op.</span><span class="sxs-lookup"><span data-stu-id="34817-191">Specifies the name of a registered repository in the `Install-Module` command.</span></span> <span data-ttu-id="34817-192">Als u een opslag plaats wilt registreren, gebruikt u `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="34817-192">To register a repository, use `Register-PSRepository`.</span></span>
<span data-ttu-id="34817-193">Gebruik om geregistreerde opslag plaatsen weer te geven `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="34817-193">To display registered repositories, use `Get-PSRepository`.</span></span>

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

### <span data-ttu-id="34817-194">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="34817-194">-RequiredVersion</span></span>

<span data-ttu-id="34817-195">Hiermee geeft u de exacte versie van één module op die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="34817-195">Specifies the exact version of a single module to install.</span></span> <span data-ttu-id="34817-196">Als er geen overeenkomst in de opslag plaats voor de opgegeven versie is, wordt er een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="34817-196">If there is no match in the repository for the specified version, an error is displayed.</span></span> <span data-ttu-id="34817-197">Als u meerdere modules wilt installeren, kunt u **RequiredVersion** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="34817-197">If you want to install multiple modules, you cannot use **RequiredVersion**.</span></span> <span data-ttu-id="34817-198">**RequiredVersion** kan niet worden gebruikt in dezelfde `Install-Module` opdracht als **MinimumVersion** of **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="34817-198">**RequiredVersion** cannot be used in the same `Install-Module` command as **MinimumVersion** or **MaximumVersion**.</span></span>

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

### <span data-ttu-id="34817-199">-Bereik</span><span class="sxs-lookup"><span data-stu-id="34817-199">-Scope</span></span>

<span data-ttu-id="34817-200">Hiermee geeft u het installatie bereik van de module op.</span><span class="sxs-lookup"><span data-stu-id="34817-200">Specifies the installation scope of the module.</span></span> <span data-ttu-id="34817-201">De acceptabele waarden voor deze para meter zijn **ALLUSERS** en **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="34817-201">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span>

<span data-ttu-id="34817-202">Met het **ALLUSERS** -bereik worden modules geïnstalleerd op een locatie die toegankelijk is voor alle gebruikers van de computer:</span><span class="sxs-lookup"><span data-stu-id="34817-202">The **AllUsers** scope installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\WindowsPowerShell\Modules`

<span data-ttu-id="34817-203">De map **CurrentUser** installeert modules op een locatie die alleen toegankelijk is voor de huidige gebruiker van de computer.</span><span class="sxs-lookup"><span data-stu-id="34817-203">The **CurrentUser** installs modules in a location that is accessible only to the current user of the computer.</span></span> <span data-ttu-id="34817-204">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="34817-204">For example:</span></span>

`$home\Documents\WindowsPowerShell\Modules`

<span data-ttu-id="34817-205">Als er geen **bereik** is gedefinieerd, wordt de standaard waarde ingesteld op basis van de PowerShellGet-versie.</span><span class="sxs-lookup"><span data-stu-id="34817-205">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="34817-206">In PowerShellGet-versies 2.0.0 en hoger is de standaard versie **CurrentUser**, waarvoor geen uitbrei ding van bevoegdheden voor installatie vereist is.</span><span class="sxs-lookup"><span data-stu-id="34817-206">In PowerShellGet versions 2.0.0 and above, the default is **CurrentUser**, which does not require elevation for install.</span></span>
- <span data-ttu-id="34817-207">In PowerShellGet 1. x versies is de standaard waarde **ALLUSERS**, waarvoor uitbrei ding van bevoegdheden vereist is voor installatie.</span><span class="sxs-lookup"><span data-stu-id="34817-207">In PowerShellGet 1.x versions, the default is **AllUsers**, which requires elevation for install.</span></span>

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

### <span data-ttu-id="34817-208">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="34817-208">-SkipPublisherCheck</span></span>

<span data-ttu-id="34817-209">Hiermee kunt u een nieuwere versie installeren van een module die al op uw computer aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="34817-209">Allows you to install a newer version of a module that already exists on your computer.</span></span> <span data-ttu-id="34817-210">Bijvoorbeeld wanneer een bestaande module digitaal is ondertekend door een vertrouwde uitgever, maar de nieuwe versie niet digitaal is ondertekend door een vertrouwde uitgever.</span><span class="sxs-lookup"><span data-stu-id="34817-210">For example, when an existing module is digitally signed by a trusted publisher but the new version is not digitally signed by a trusted publisher.</span></span>

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

### <span data-ttu-id="34817-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="34817-211">-WhatIf</span></span>

<span data-ttu-id="34817-212">Laat zien wat er zou gebeuren als een `Install-Module` opdracht werd uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="34817-212">Shows what would happen if an `Install-Module` command was run.</span></span> <span data-ttu-id="34817-213">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="34817-213">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="34817-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="34817-214">CommonParameters</span></span>

<span data-ttu-id="34817-215">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="34817-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="34817-216">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="34817-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="34817-217">INVOER</span><span class="sxs-lookup"><span data-stu-id="34817-217">INPUTS</span></span>

### <span data-ttu-id="34817-218">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="34817-218">PSRepositoryItemInfo</span></span>

<span data-ttu-id="34817-219">`Find-Module` Hiermee maakt u **PSRepositoryItemInfo** -objecten waarnaar de pijp lijn kan worden verzonden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="34817-219">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span>

### <span data-ttu-id="34817-220">System.String[]</span><span class="sxs-lookup"><span data-stu-id="34817-220">System.String[]</span></span>

### <span data-ttu-id="34817-221">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="34817-221">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="34817-222">System. String</span><span class="sxs-lookup"><span data-stu-id="34817-222">System.String</span></span>

### <span data-ttu-id="34817-223">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="34817-223">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="34817-224">System. URI</span><span class="sxs-lookup"><span data-stu-id="34817-224">System.Uri</span></span>

## <span data-ttu-id="34817-225">UITVOER</span><span class="sxs-lookup"><span data-stu-id="34817-225">OUTPUTS</span></span>

### <span data-ttu-id="34817-226">Micro soft. Power shell. commands. PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="34817-226">Microsoft.PowerShell.Commands.PSRepositoryItemInfo</span></span>

<span data-ttu-id="34817-227">Wanneer u de para meter **PassThru** gebruikt, wordt `Install-Module` een **PSRepositoryItemInfo** -object uitgevoerd voor de module.</span><span class="sxs-lookup"><span data-stu-id="34817-227">When using the **PassThru** parameter, `Install-Module` outputs a **PSRepositoryItemInfo** object for the module.</span></span> <span data-ttu-id="34817-228">Dit is dezelfde informatie die u van de cmdlet krijgt `Find-Module` .</span><span class="sxs-lookup"><span data-stu-id="34817-228">This is the same information that you get from the `Find-Module` cmdlet.</span></span>

## <span data-ttu-id="34817-229">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="34817-229">NOTES</span></span>

<span data-ttu-id="34817-230">`Install-Module` wordt uitgevoerd op Power shell 5,0 of hoger, op Windows 7 of Windows 2008 R2 en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="34817-230">`Install-Module` runs on PowerShell 5.0 or later releases, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34817-231">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="34817-231">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="34817-232">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="34817-232">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="34817-233">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="34817-233">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="34817-234">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="34817-234">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="34817-235">Als beveiligings best practice kunt u de code van een module evalueren voordat u cmdlets of functions voor de eerste keer uitvoert.</span><span class="sxs-lookup"><span data-stu-id="34817-235">As a security best practice, evaluate a module's code before running any cmdlets or functions for the first time.</span></span> <span data-ttu-id="34817-236">Om te voor komen dat modules worden uitgevoerd die schadelijke code bevatten, worden geïnstalleerde modules na de installatie niet automatisch geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="34817-236">To prevent running modules that contain malicious code, installed modules are not automatically imported after installation.</span></span>

<span data-ttu-id="34817-237">Als de module naam die is opgegeven door de para meter **name** niet voor komt in de opslag plaats, `Install-Module` wordt een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="34817-237">If the module name specified by the **Name** parameter does not exist in the repository, `Install-Module` returns an error.</span></span>

<span data-ttu-id="34817-238">Als u meerdere modules wilt installeren, gebruikt u de para meter **name** en geeft u een door komma's gescheiden matrix van module namen op.</span><span class="sxs-lookup"><span data-stu-id="34817-238">To install multiple modules, use the **Name** parameter and specify a comma-separated array of module names.</span></span> <span data-ttu-id="34817-239">Als u meerdere module namen opgeeft, kunt u **MinimumVersion**, **MaximumVersion** of **RequiredVersion** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="34817-239">If you specify multiple module names, you cannot use **MinimumVersion**, **MaximumVersion**, or **RequiredVersion**.</span></span> <span data-ttu-id="34817-240">`Find-Module` Hiermee maakt u **PSRepositoryItemInfo** -objecten waarnaar de pijp lijn kan worden verzonden `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="34817-240">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to `Install-Module`.</span></span> <span data-ttu-id="34817-241">De pijp lijn is een andere manier om meerdere modules op te geven die u wilt installeren in één opdracht.</span><span class="sxs-lookup"><span data-stu-id="34817-241">The pipeline is another way to specify multiple modules to install in a single command.</span></span>

<span data-ttu-id="34817-242">Standaard worden modules voor het bereik van **ALLUSERS** geïnstalleerd in `$env:ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="34817-242">By default, modules for the scope of **AllUsers** are installed in `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span> <span data-ttu-id="34817-243">De standaard instelling voor komt Verwar ring bij de installatie van Power shell desired state Configuration (DSC)-resources.</span><span class="sxs-lookup"><span data-stu-id="34817-243">The default prevents confusion when you install PowerShell Desired State Configuration (DSC) resources.</span></span>

<span data-ttu-id="34817-244">Een module-installatie mislukt en kan niet worden geïmporteerd als deze geen `.psm1` , `.psd1` of `.dll` dezelfde naam in de map heeft.</span><span class="sxs-lookup"><span data-stu-id="34817-244">A module installation fails and cannot be imported if it does not have a `.psm1`, `.psd1`, or `.dll` of the same name within the folder.</span></span> <span data-ttu-id="34817-245">Gebruik de para meter **Force** om de module te installeren.</span><span class="sxs-lookup"><span data-stu-id="34817-245">Use the **Force** parameter to install the module.</span></span>

<span data-ttu-id="34817-246">Als de versie van een bestaande module overeenkomt met de naam die is opgegeven door de para meter **name** en de para meter **MinimumVersion** of **RequiredVersion** niet wordt gebruikt, wordt `Install-Module` de module op de achtergrond uitgevoerd, maar wordt deze niet geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-246">If an existing module's version matches the name specified by the **Name** parameter, and the **MinimumVersion** or **RequiredVersion** parameter are not used, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="34817-247">Als de versie van een bestaande module groter is dan de waarde van de para meter **MinimumVersion** , of gelijk is aan de waarde van de para meter **RequiredVersion** , wordt `Install-Module` de module op de achtergrond voortgezet, maar wordt niet de modules geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="34817-247">If an existing module's version is greater than the value of the **MinimumVersion** parameter, or equal to the value of the **RequiredVersion** parameter, `Install-Module` silently continues but does not install the module.</span></span>

<span data-ttu-id="34817-248">Als de bestaande module niet overeenkomt met de waarden die zijn opgegeven door de para meters **MinimumVersion** of **RequiredVersion** , treedt er een fout op in de `Install-Module` opdracht.</span><span class="sxs-lookup"><span data-stu-id="34817-248">If the existing module does not match the values specified by the **MinimumVersion** or **RequiredVersion** parameters, an error occurs in the `Install-Module` command.</span></span> <span data-ttu-id="34817-249">Als de versie van de bestaande geïnstalleerde module bijvoorbeeld lager is dan de **MinimumVersion** -waarde of niet gelijk is aan de **RequiredVersion** -waarde.</span><span class="sxs-lookup"><span data-stu-id="34817-249">For example, if the version of the existing installed module is lower than the **MinimumVersion** value or not equal to the **RequiredVersion** value.</span></span>

<span data-ttu-id="34817-250">Bij een module-installatie worden ook alle afhankelijke modules geïnstalleerd die vereist zijn voor de module Uitgever.</span><span class="sxs-lookup"><span data-stu-id="34817-250">A module installation will also install any dependent modules specified as required by the module publisher.</span></span>
<span data-ttu-id="34817-251">De uitgever geeft de vereiste modules en hun versies op in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="34817-251">The publisher will specify the required modules and their versions in the module manifest.</span></span>

## <span data-ttu-id="34817-252">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="34817-252">RELATED LINKS</span></span>

[<span data-ttu-id="34817-253">Find-Module</span><span class="sxs-lookup"><span data-stu-id="34817-253">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="34817-254">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="34817-254">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="34817-255">Import-module</span><span class="sxs-lookup"><span data-stu-id="34817-255">Import-Module</span></span>](../Microsoft.PowerShell.Core/Import-Module.md)

[<span data-ttu-id="34817-256">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="34817-256">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="34817-257">REGI ster-PSRepository</span><span class="sxs-lookup"><span data-stu-id="34817-257">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="34817-258">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="34817-258">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="34817-259">Update-Module</span><span class="sxs-lookup"><span data-stu-id="34817-259">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="34817-260">about_Module</span><span class="sxs-lookup"><span data-stu-id="34817-260">about_Module</span></span>](../Microsoft.PowerShell.Core/About/about_Modules.md)
