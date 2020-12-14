---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/16/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Module
ms.openlocfilehash: ee94ba7808cb364306826325cfbc3df2cf9834a5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892583"
---
# <span data-ttu-id="67dd1-103">Update-Module</span><span class="sxs-lookup"><span data-stu-id="67dd1-103">Update-Module</span></span>

## <span data-ttu-id="67dd1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="67dd1-104">SYNOPSIS</span></span>
<span data-ttu-id="67dd1-105">Downloadt en installeert de nieuwste versie van de opgegeven modules van een online galerie naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="67dd1-105">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <span data-ttu-id="67dd1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="67dd1-106">SYNTAX</span></span>

### <span data-ttu-id="67dd1-107">Alles</span><span class="sxs-lookup"><span data-stu-id="67dd1-107">All</span></span>

```
Update-Module [[-Name] <String[]>] [-RequiredVersion <String>] [-MaximumVersion <String>]
 [-Credential <PSCredential>] [-Scope <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Force] [-AllowPrerelease] [-AcceptLicense] [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="67dd1-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="67dd1-108">DESCRIPTION</span></span>

<span data-ttu-id="67dd1-109">Met de cmdlet wordt de `Update-Module` nieuwste versie van een module in een online galerie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="67dd1-109">The `Update-Module` cmdlet installs a module's newest version from an online gallery.</span></span> <span data-ttu-id="67dd1-110">U wordt gevraagd om de update te bevestigen voordat deze wordt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="67dd1-110">You're prompted to confirm the update before it's installed.</span></span> <span data-ttu-id="67dd1-111">Updates worden alleen geïnstalleerd voor modules die zijn geïnstalleerd op de lokale computer met `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="67dd1-111">Updates are installed only for modules that were installed on the local computer with `Install-Module`.</span></span> <span data-ttu-id="67dd1-112">`Update-Module` Hiermee zoekt u naar `$env:PSModulePath` geïnstalleerde modules.</span><span class="sxs-lookup"><span data-stu-id="67dd1-112">`Update-Module` searches `$env:PSModulePath` for installed modules.</span></span>

<span data-ttu-id="67dd1-113">`Update-Module` Als er geen para meters zijn opgegeven, worden alle geïnstalleerde modules bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="67dd1-113">`Update-Module` with no parameters specified updates all installed modules.</span></span> <span data-ttu-id="67dd1-114">Gebruik de para meter **name** om een module op te geven die moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="67dd1-114">To specify a module to update, use the **Name** parameter.</span></span> <span data-ttu-id="67dd1-115">U kunt bijwerken naar de specifieke versie van een module met behulp van de para meter **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="67dd1-115">You can update to a module's specific version by using the **RequiredVersion** parameter.</span></span>

<span data-ttu-id="67dd1-116">Als een geïnstalleerde module al de nieuwste versie is, wordt de module niet bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="67dd1-116">If an installed module is already the newest version, the module isn't updated.</span></span> <span data-ttu-id="67dd1-117">Als de module niet wordt gevonden in `$env:PSModulePath` , wordt een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="67dd1-117">If the module isn't found in `$env:PSModulePath`, an error is displayed.</span></span>

<span data-ttu-id="67dd1-118">Als u de geïnstalleerde modules wilt weer geven, gebruikt u `Get-InstalledModule` .</span><span class="sxs-lookup"><span data-stu-id="67dd1-118">To display the installed modules, use `Get-InstalledModule`.</span></span>

## <span data-ttu-id="67dd1-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="67dd1-119">EXAMPLES</span></span>

### <span data-ttu-id="67dd1-120">Voor beeld 1: alle modules bijwerken</span><span class="sxs-lookup"><span data-stu-id="67dd1-120">Example 1: Update all modules</span></span>

<span data-ttu-id="67dd1-121">In dit voor beeld worden alle geïnstalleerde modules bijgewerkt naar de nieuwste versie in een online galerie.</span><span class="sxs-lookup"><span data-stu-id="67dd1-121">This example updates all installed modules to the newest version in an online gallery.</span></span>

```powershell
Update-Module
```

### <span data-ttu-id="67dd1-122">Voor beeld 2: een module bijwerken op naam</span><span class="sxs-lookup"><span data-stu-id="67dd1-122">Example 2: Update a module by name</span></span>

<span data-ttu-id="67dd1-123">In dit voor beeld wordt een specifieke module in een online galerie bijgewerkt naar de nieuwste versie.</span><span class="sxs-lookup"><span data-stu-id="67dd1-123">This example updates a specific module to the newest version in an online gallery.</span></span>

```powershell
Update-Module -Name SpeculationControl
```

<span data-ttu-id="67dd1-124">`Update-Module` maakt gebruik van de para meter **name** voor het bijwerken van een specifieke module, **SpeculationControl**.</span><span class="sxs-lookup"><span data-stu-id="67dd1-124">`Update-Module` uses the **Name** parameter to update a specific module, **SpeculationControl**.</span></span>

### <span data-ttu-id="67dd1-125">Voor beeld 3: wat-als-Update-Module worden uitgevoerd weer geven</span><span class="sxs-lookup"><span data-stu-id="67dd1-125">Example 3: View what-if Update-Module runs</span></span>

<span data-ttu-id="67dd1-126">In dit voor beeld wordt een wat-als-scenario weer gegeven wat er gebeurt als `Update-Module` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="67dd1-126">This example does a what-if scenario to show what happens if `Update-Module` is run.</span></span> <span data-ttu-id="67dd1-127">De opdracht wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="67dd1-127">The command isn't run.</span></span>

```powershell
Update-Module -WhatIf
```

```Output
What if: Performing the operation "Update-Module" on target "Version '2.8.0' of module
  'Carbon', updating to version '2.8.1'".
What if: Performing the operation "Update-Module" on target "Version '1.0.10' of module
  'SpeculationControl', updating to version '1.0.14'".
```

<span data-ttu-id="67dd1-128">`Update-Module` Hiermee wordt de **WhatIf** -para meter weer gegeven wat er zou gebeuren als ze `Update-Module` werden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="67dd1-128">`Update-Module` uses the **WhatIf** parameter display what would happen if `Update-Module` were run.</span></span>

### <span data-ttu-id="67dd1-129">Voor beeld 4: een module bijwerken naar een opgegeven versie</span><span class="sxs-lookup"><span data-stu-id="67dd1-129">Example 4: Update a module to a specified version</span></span>

<span data-ttu-id="67dd1-130">In dit voor beeld wordt een module bijgewerkt naar een specifieke versie.</span><span class="sxs-lookup"><span data-stu-id="67dd1-130">In this example, a module is updated to a specific version.</span></span> <span data-ttu-id="67dd1-131">De versie moet in de online galerie bestaan, anders wordt er een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="67dd1-131">The version must exist in the online gallery or an error is displayed.</span></span>

```powershell
Update-Module -Name SpeculationControl -RequiredVersion 1.0.14
```

<span data-ttu-id="67dd1-132">`Update-Module` maakt gebruik van de para meter **name** om de module **SpeculationControl** op te geven.</span><span class="sxs-lookup"><span data-stu-id="67dd1-132">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="67dd1-133">De **RequiredVersion** para meter geeft u de versie, **1.0.14**.</span><span class="sxs-lookup"><span data-stu-id="67dd1-133">The **RequiredVersion** parameter specifies the version, **1.0.14**.</span></span>

### <span data-ttu-id="67dd1-134">Voor beeld 5: een module bijwerken zonder bevestiging</span><span class="sxs-lookup"><span data-stu-id="67dd1-134">Example 5: Update a module without confirmation</span></span>

<span data-ttu-id="67dd1-135">In dit voor beeld wordt geen bevestiging gevraagd om de module bij te werken naar de nieuwste versie vanuit een online galerie.</span><span class="sxs-lookup"><span data-stu-id="67dd1-135">This example doesn't request confirmation to update the module to the newest version from an online gallery.</span></span> <span data-ttu-id="67dd1-136">Als de module al is geïnstalleerd, wordt de module met de para meter **Force** opnieuw geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="67dd1-136">If the module is already installed, the **Force** parameter reinstalls the module.</span></span>

```powershell
Update-Module -Name SpeculationControl -Force
```

<span data-ttu-id="67dd1-137">`Update-Module` maakt gebruik van de para meter **name** om de module **SpeculationControl** op te geven.</span><span class="sxs-lookup"><span data-stu-id="67dd1-137">`Update-Module` uses the **Name** parameter to specify the module, **SpeculationControl**.</span></span> <span data-ttu-id="67dd1-138">Met de para meter **Force** wordt de module bijgewerkt zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="67dd1-138">The **Force** parameter updates the module without requesting user confirmation.</span></span>

## <span data-ttu-id="67dd1-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="67dd1-139">PARAMETERS</span></span>

### <span data-ttu-id="67dd1-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="67dd1-140">-AcceptLicense</span></span>

<span data-ttu-id="67dd1-141">Accepteer de gebruiksrecht overeenkomst tijdens de installatie automatisch als het pakket deze vereist.</span><span class="sxs-lookup"><span data-stu-id="67dd1-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="67dd1-142">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="67dd1-142">-AllowPrerelease</span></span>

<span data-ttu-id="67dd1-143">Hiermee kunt u een module bijwerken met de nieuwere module die is gemarkeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="67dd1-143">Allows you to update a module with the newer module marked as a prerelease.</span></span>

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

### <span data-ttu-id="67dd1-144">-Confirm</span><span class="sxs-lookup"><span data-stu-id="67dd1-144">-Confirm</span></span>

<span data-ttu-id="67dd1-145">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Update-Module` .</span><span class="sxs-lookup"><span data-stu-id="67dd1-145">Prompts you for confirmation before running `Update-Module`.</span></span>

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

### <span data-ttu-id="67dd1-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="67dd1-146">-Credential</span></span>

<span data-ttu-id="67dd1-147">Hiermee geeft u een gebruikers account op dat gemachtigd is om een module bij te werken.</span><span class="sxs-lookup"><span data-stu-id="67dd1-147">Specifies a user account that has permission to update a module.</span></span>

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

### <span data-ttu-id="67dd1-148">-Force</span><span class="sxs-lookup"><span data-stu-id="67dd1-148">-Force</span></span>

<span data-ttu-id="67dd1-149">Hiermee wordt een update van elke opgegeven module geforceerd zonder dat u wordt gevraagd om een bevestiging te vragen.</span><span class="sxs-lookup"><span data-stu-id="67dd1-149">Forces an update of each specified module without a prompt to request confirmation.</span></span> <span data-ttu-id="67dd1-150">Als de module al is geïnstalleerd, wordt de module **geforceerd** opnieuw geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="67dd1-150">If the module is already installed, **Force** reinstalls the module.</span></span>

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

### <span data-ttu-id="67dd1-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="67dd1-151">-MaximumVersion</span></span>

<span data-ttu-id="67dd1-152">Hiermee geeft u de maximum versie van één module op die moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="67dd1-152">Specifies the maximum version of a single module to update.</span></span> <span data-ttu-id="67dd1-153">U kunt deze para meter niet toevoegen als u probeert meerdere modules bij te werken.</span><span class="sxs-lookup"><span data-stu-id="67dd1-153">You can't add this parameter if you're attempting to update multiple modules.</span></span> <span data-ttu-id="67dd1-154">De **MaximumVersion** -en **RequiredVersion** -para meters kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="67dd1-154">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="67dd1-155">-Name</span><span class="sxs-lookup"><span data-stu-id="67dd1-155">-Name</span></span>

<span data-ttu-id="67dd1-156">Hiermee geeft u de namen op van een of meer modules die moeten worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="67dd1-156">Specifies the names of one or more modules to update.</span></span> <span data-ttu-id="67dd1-157">`Update-Module` Hiermee wordt gezocht naar `$env:PSModulePath` de modules die moeten worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="67dd1-157">`Update-Module` searches `$env:PSModulePath` for the modules to update.</span></span> <span data-ttu-id="67dd1-158">Als er geen overeenkomsten worden gevonden in `$env:PSModulePath` voor de opgegeven module naam, treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="67dd1-158">If no matches are found in `$env:PSModulePath` for the specified module name, an error occurs.</span></span>

<span data-ttu-id="67dd1-159">Joker tekens worden geaccepteerd in module namen.</span><span class="sxs-lookup"><span data-stu-id="67dd1-159">Wildcards are accepted in module names.</span></span> <span data-ttu-id="67dd1-160">Als u Joker tekens toevoegt aan de opgegeven naam en er geen overeenkomsten worden gevonden, treedt er geen fout op.</span><span class="sxs-lookup"><span data-stu-id="67dd1-160">If you add wildcard characters to the specified name and no matches are found, no error occurs.</span></span>

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

### <span data-ttu-id="67dd1-161">-PassThru</span><span class="sxs-lookup"><span data-stu-id="67dd1-161">-PassThru</span></span>

<span data-ttu-id="67dd1-162">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="67dd1-162">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="67dd1-163">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="67dd1-163">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="67dd1-164">De ondersteuning voor de **PassThru** -para meter is toegevoegd in **PowerShellGet** 2.0.0</span><span class="sxs-lookup"><span data-stu-id="67dd1-164">The **PassThru** parameter support was added in **PowerShellGet** 2.0.0</span></span>

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

### <span data-ttu-id="67dd1-165">-Proxy</span><span class="sxs-lookup"><span data-stu-id="67dd1-165">-Proxy</span></span>

<span data-ttu-id="67dd1-166">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met een Internet bron.</span><span class="sxs-lookup"><span data-stu-id="67dd1-166">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="67dd1-167">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="67dd1-167">-ProxyCredential</span></span>

<span data-ttu-id="67dd1-168">Hiermee geeft u een gebruikers account op dat gemachtigd is om de proxy server te gebruiken die is opgegeven met de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="67dd1-168">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="67dd1-169">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="67dd1-169">-RequiredVersion</span></span>

<span data-ttu-id="67dd1-170">Hiermee geeft u de exacte versie op waarop de bestaande geïnstalleerde module wordt bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="67dd1-170">Specifies the exact version to which the existing installed module will be updated.</span></span> <span data-ttu-id="67dd1-171">De versie die is opgegeven door **RequiredVersion** moet aanwezig zijn in de online galerie, anders wordt er een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="67dd1-171">The version specified by **RequiredVersion** must exist in the online gallery or an error is displayed.</span></span> <span data-ttu-id="67dd1-172">Als er meer dan één module in één opdracht is bijgewerkt, kunt u **RequiredVersion** niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="67dd1-172">If more than one module is updated in a single command, you can't use **RequiredVersion**.</span></span>

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

### <span data-ttu-id="67dd1-173">-Bereik</span><span class="sxs-lookup"><span data-stu-id="67dd1-173">-Scope</span></span>

<span data-ttu-id="67dd1-174">Hiermee geeft u het installatie bereik van de module op.</span><span class="sxs-lookup"><span data-stu-id="67dd1-174">Specifies the installation scope of the module.</span></span> <span data-ttu-id="67dd1-175">De acceptabele waarden voor deze para meter zijn **ALLUSERS** en **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="67dd1-175">The acceptable values for this parameter are **AllUsers** and **CurrentUser**.</span></span> <span data-ttu-id="67dd1-176">Als **Scope** niet is opgegeven, wordt de update geïnstalleerd in het bereik van **CurrentUser** .</span><span class="sxs-lookup"><span data-stu-id="67dd1-176">If **Scope** isn't specified, the update is installed in the **CurrentUser** scope.</span></span>

<span data-ttu-id="67dd1-177">Het bereik **ALLUSERS** vereist verhoogde machtigingen en installeert modules op een locatie die toegankelijk is voor alle gebruikers van de computer:</span><span class="sxs-lookup"><span data-stu-id="67dd1-177">The **AllUsers** scope requires elevated permissions and installs modules in a location that is accessible to all users of the computer:</span></span>

`$env:ProgramFiles\PowerShell\Modules`

<span data-ttu-id="67dd1-178">Voor de **CurrentUser** zijn geen verhoogde machtigingen vereist en modules geïnstalleerd op een locatie die alleen toegankelijk is voor de huidige gebruiker van de computer:</span><span class="sxs-lookup"><span data-stu-id="67dd1-178">The **CurrentUser** doesn't require elevated permissions and installs modules in a location that is accessible only to the current user of the computer:</span></span>

`$home\Documents\PowerShell\Modules`

<span data-ttu-id="67dd1-179">Als er geen **bereik** is gedefinieerd, wordt de standaard waarde ingesteld op basis van de PowerShellGet-versie.</span><span class="sxs-lookup"><span data-stu-id="67dd1-179">When no **Scope** is defined, the default is set based on the PowerShellGet version.</span></span>

- <span data-ttu-id="67dd1-180">In PowerShellGet-versies 2.0.0 en hoger is de standaard waarde **ALLUSERS** wanneer een verhoogde sessie en een andere versie van **CurrentUser** wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="67dd1-180">In PowerShellGet versions 2.0.0 and above, the default is **AllUsers** when running an elevated session and **CurrentUser** for all others.</span></span>
- <span data-ttu-id="67dd1-181">In PowerShellGet 1. x versies is de standaard waarde **ALLUSERS**, waarvoor uitbrei ding van bevoegdheden vereist is voor installatie.</span><span class="sxs-lookup"><span data-stu-id="67dd1-181">In PowerShellGet 1.x versions, the default is **AllUsers**, which requires elevation for install.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="67dd1-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="67dd1-182">-WhatIf</span></span>

<span data-ttu-id="67dd1-183">Hier wordt weer gegeven wat er gebeurt als er `Update-Module` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="67dd1-183">Shows what would happen if `Update-Module` runs.</span></span> <span data-ttu-id="67dd1-184">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="67dd1-184">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="67dd1-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="67dd1-185">CommonParameters</span></span>

<span data-ttu-id="67dd1-186">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="67dd1-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="67dd1-187">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="67dd1-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="67dd1-188">INVOER</span><span class="sxs-lookup"><span data-stu-id="67dd1-188">INPUTS</span></span>

### <span data-ttu-id="67dd1-189">System.String[]</span><span class="sxs-lookup"><span data-stu-id="67dd1-189">System.String[]</span></span>

### <span data-ttu-id="67dd1-190">System. String</span><span class="sxs-lookup"><span data-stu-id="67dd1-190">System.String</span></span>

### <span data-ttu-id="67dd1-191">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="67dd1-191">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="67dd1-192">System. URI</span><span class="sxs-lookup"><span data-stu-id="67dd1-192">System.Uri</span></span>

## <span data-ttu-id="67dd1-193">UITVOER</span><span class="sxs-lookup"><span data-stu-id="67dd1-193">OUTPUTS</span></span>

### <span data-ttu-id="67dd1-194">System. object</span><span class="sxs-lookup"><span data-stu-id="67dd1-194">System.Object</span></span>

## <span data-ttu-id="67dd1-195">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="67dd1-195">NOTES</span></span>

<span data-ttu-id="67dd1-196">Voor Power shell 5,1 of lager is het standaard bereik in een sessie met verhoogde bevoegdheid **ALLUSERS** en in een niet-verhoogde sessie, **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="67dd1-196">For PowerShell 5.1 or below, the default scope in an elevated session is **AllUsers**, and in a non-elevated session, **CurrentUser**.</span></span> <span data-ttu-id="67dd1-197">Module-updates voor **ALLUSERS**, `$env:ProgramFiles\PowerShell\Modules` , vereist verhoogde machtigingen.</span><span class="sxs-lookup"><span data-stu-id="67dd1-197">Module updates for **AllUsers**, `$env:ProgramFiles\PowerShell\Modules`, need elevated permissions.</span></span> <span data-ttu-id="67dd1-198">Module-updates voor **CurrentUser**, `$home\Documents\PowerShell\Modules` , hebben geen verhoogde machtigingen nodig.</span><span class="sxs-lookup"><span data-stu-id="67dd1-198">Module updates for **CurrentUser**, `$home\Documents\PowerShell\Modules`, don't need elevated permissions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="67dd1-199">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="67dd1-199">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="67dd1-200">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="67dd1-200">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="67dd1-201">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="67dd1-201">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="67dd1-202">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="67dd1-202">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="67dd1-203">`Update-Module` wordt uitgevoerd op Power Shell 3,0 of latere versies van Power shell, op Windows 7 of Windows 2008 R2 en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="67dd1-203">`Update-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="67dd1-204">Als de module die u opgeeft met de para meter **name** niet is geïnstalleerd met behulp van `Install-Module` , treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="67dd1-204">If the module that you specify with the **Name** parameter wasn't installed by using `Install-Module`, an error occurs.</span></span>

<span data-ttu-id="67dd1-205">U kunt alleen uitvoeren `Update-Module` op modules die u hebt geïnstalleerd vanuit de online galerie door uit te voeren `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="67dd1-205">You can only run `Update-Module` on modules that you installed from the online gallery by running `Install-Module`.</span></span>

<span data-ttu-id="67dd1-206">Als er `Update-Module` wordt geprobeerd binaire bestanden bij te werken, `Update-Module` retourneert een fout die de probleem processen identificeert.</span><span class="sxs-lookup"><span data-stu-id="67dd1-206">If `Update-Module` attempts to update binaries that are in use, `Update-Module` returns an error that identifies the problem processes.</span></span> <span data-ttu-id="67dd1-207">De gebruiker wordt op de hoogte gesteld `Update-Module` wanneer de processen zijn gestopt.</span><span class="sxs-lookup"><span data-stu-id="67dd1-207">The user is informed to retry `Update-Module` after the processes are stopped.</span></span>

## <span data-ttu-id="67dd1-208">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="67dd1-208">RELATED LINKS</span></span>

[<span data-ttu-id="67dd1-209">Find-Module</span><span class="sxs-lookup"><span data-stu-id="67dd1-209">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="67dd1-210">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="67dd1-210">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="67dd1-211">Installatie-module</span><span class="sxs-lookup"><span data-stu-id="67dd1-211">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="67dd1-212">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="67dd1-212">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="67dd1-213">Uninstall-module</span><span class="sxs-lookup"><span data-stu-id="67dd1-213">Uninstall-Module</span></span>](Uninstall-Module.md)
