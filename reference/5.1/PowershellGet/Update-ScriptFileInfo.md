---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-scriptfileinfo?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ScriptFileInfo
ms.openlocfilehash: bb36d5a1acc8331762513219e823bf91304b6b45
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250732"
---
# <span data-ttu-id="67995-103">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="67995-103">Update-ScriptFileInfo</span></span>

## <span data-ttu-id="67995-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="67995-104">SYNOPSIS</span></span>
<span data-ttu-id="67995-105">Hiermee wordt informatie over een script bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="67995-105">Updates information for a script.</span></span>

## <span data-ttu-id="67995-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="67995-106">SYNTAX</span></span>

### <span data-ttu-id="67995-107">PathParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="67995-107">PathParameterSet (Default)</span></span>

```
Update-ScriptFileInfo [-Path] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="67995-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="67995-108">LiteralPathParameterSet</span></span>

```
Update-ScriptFileInfo [-LiteralPath] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="67995-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="67995-109">DESCRIPTION</span></span>

<span data-ttu-id="67995-110">Met de cmdlet worden de `Update-ScriptFileInfo` eigenschaps waarden van een script bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="67995-110">The `Update-ScriptFileInfo` cmdlet updates a script's property values.</span></span> <span data-ttu-id="67995-111">Bijvoorbeeld: de waarden voor versie, auteur of beschrijving.</span><span class="sxs-lookup"><span data-stu-id="67995-111">For example, the values for version, author, or description.</span></span>

## <span data-ttu-id="67995-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="67995-112">EXAMPLES</span></span>

### <span data-ttu-id="67995-113">Voor beeld 1: de versie van een script bestand bijwerken</span><span class="sxs-lookup"><span data-stu-id="67995-113">Example 1: Update the version of a script file</span></span>

<span data-ttu-id="67995-114">In dit voor beeld wordt een bestaand script bestand bijgewerkt met nieuwe eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="67995-114">In this example, an existing script file is updated with new property values.</span></span>

<span data-ttu-id="67995-115">Splatting wordt gebruikt om para meters door te geven aan de `Update-ScriptFileInfo` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="67995-115">Splatting is used to pass parameters to the `Update-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="67995-116">Zie [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="67995-116">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "2.0"
  Author = "bob@contoso.com"
  CompanyName = "Contoso"
  Description = "This is the updated description"
  }
Update-ScriptFileInfo @Parms -PassThru
```

```Output
<#PSScriptInfo

.VERSION 2.0

.GUID 4609f00c-e850-4d3f-9c69-3741e56e4133

.AUTHOR bob@contoso.com

.COMPANYNAME Contoso

.COPYRIGHT

.TAGS

.LICENSEURI

.PROJECTURI

.ICONURI

.EXTERNALMODULEDEPENDENCIES

.REQUIREDSCRIPTS

.EXTERNALSCRIPTDEPENDENCIES

.RELEASENOTES

.PRIVATEDATA

#>

<#

.DESCRIPTION
This is the updated description

#>
Param()
```

<span data-ttu-id="67995-117">`$Parms` Hiermee slaat u de parameter waarden voor **pad** , **versie** , **Auteur** , **Bedrijfs naam** en **Beschrijving** op.</span><span class="sxs-lookup"><span data-stu-id="67995-117">`$Parms` stores the parameter values for **Path** , **Version** , **Author** , **CompanyName** , and **Description**.</span></span> <span data-ttu-id="67995-118">`Update-ScriptFileInfo` Hiermee worden de parameter waarden opgehaald uit `@Parms` en wordt het script bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="67995-118">`Update-ScriptFileInfo` gets the parameter values from `@Parms` and updates the script.</span></span> <span data-ttu-id="67995-119">Met de para meter **PassThru** wordt de inhoud van het script weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="67995-119">The **PassThru** parameter displays the script's contents in the PowerShell console.</span></span>

## <span data-ttu-id="67995-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="67995-120">PARAMETERS</span></span>

### <span data-ttu-id="67995-121">-Author</span><span class="sxs-lookup"><span data-stu-id="67995-121">-Author</span></span>

<span data-ttu-id="67995-122">Hiermee geeft u de auteur van het script.</span><span class="sxs-lookup"><span data-stu-id="67995-122">Specifies the script author.</span></span>

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

### <span data-ttu-id="67995-123">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="67995-123">-CompanyName</span></span>

<span data-ttu-id="67995-124">Hiermee geeft u het bedrijf of de leverancier op die het script heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="67995-124">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="67995-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="67995-125">-Confirm</span></span>

<span data-ttu-id="67995-126">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Update-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="67995-126">Prompts you for confirmation before running `Update-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="67995-127">-Copyright</span><span class="sxs-lookup"><span data-stu-id="67995-127">-Copyright</span></span>

<span data-ttu-id="67995-128">Hiermee geeft u een copyright verklaring voor het script op.</span><span class="sxs-lookup"><span data-stu-id="67995-128">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="67995-129">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="67995-129">-Description</span></span>

<span data-ttu-id="67995-130">Hiermee geeft u een beschrijving op voor het script.</span><span class="sxs-lookup"><span data-stu-id="67995-130">Specifies a description for the script.</span></span>

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

### <span data-ttu-id="67995-131">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="67995-131">-ExternalModuleDependencies</span></span>

<span data-ttu-id="67995-132">Hiermee geeft u een matrix met externe module-afhankelijkheden op.</span><span class="sxs-lookup"><span data-stu-id="67995-132">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="67995-133">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="67995-133">-ExternalScriptDependencies</span></span>

<span data-ttu-id="67995-134">Hiermee geeft u een matrix met externe script afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="67995-134">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="67995-135">-Force</span><span class="sxs-lookup"><span data-stu-id="67995-135">-Force</span></span>

<span data-ttu-id="67995-136">Er wordt geforceerd `Update-ScriptFileInfo` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="67995-136">Forces `Update-ScriptFileInfo` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="67995-137">-GUID</span><span class="sxs-lookup"><span data-stu-id="67995-137">-Guid</span></span>

<span data-ttu-id="67995-138">Hiermee geeft u een unieke ID voor een script op.</span><span class="sxs-lookup"><span data-stu-id="67995-138">Specifies a unique ID for a script.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="67995-139">-IconUri</span><span class="sxs-lookup"><span data-stu-id="67995-139">-IconUri</span></span>

<span data-ttu-id="67995-140">Hiermee geeft u de URL van een pictogram voor het script.</span><span class="sxs-lookup"><span data-stu-id="67995-140">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="67995-141">Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor het script.</span><span class="sxs-lookup"><span data-stu-id="67995-141">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="67995-142">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="67995-142">-LicenseUri</span></span>

<span data-ttu-id="67995-143">Hiermee geeft u de URL van de licentie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="67995-143">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="67995-144">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="67995-144">-LiteralPath</span></span>

<span data-ttu-id="67995-145">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="67995-145">Specifies a path to one or more locations.</span></span> <span data-ttu-id="67995-146">De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="67995-146">The **LiteralPath** parameter's value is used exactly as it's entered.</span></span> <span data-ttu-id="67995-147">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="67995-147">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="67995-148">Als het pad escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="67995-148">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="67995-149">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="67995-149">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="67995-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="67995-150">-PassThru</span></span>

<span data-ttu-id="67995-151">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="67995-151">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="67995-152">Standaard genereert geen `Update-ScriptFileInfo` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="67995-152">By default, `Update-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="67995-153">-Path</span><span class="sxs-lookup"><span data-stu-id="67995-153">-Path</span></span>

<span data-ttu-id="67995-154">Hiermee geeft u de locatie van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="67995-154">Specifies the script file's location.</span></span> <span data-ttu-id="67995-155">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="67995-155">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="67995-156">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="67995-156">-PrivateData</span></span>

<span data-ttu-id="67995-157">Hiermee geeft u de persoonlijke gegevens voor het script.</span><span class="sxs-lookup"><span data-stu-id="67995-157">Specifies the private data for the script.</span></span>

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

### <span data-ttu-id="67995-158">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="67995-158">-ProjectUri</span></span>

<span data-ttu-id="67995-159">Hiermee geeft u de URL van een webpagina over dit project op.</span><span class="sxs-lookup"><span data-stu-id="67995-159">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="67995-160">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="67995-160">-ReleaseNotes</span></span>

<span data-ttu-id="67995-161">Hiermee geeft u een teken reeks matrix met release opmerkingen of opmerkingen die u beschikbaar wilt stellen voor deze versie van het script.</span><span class="sxs-lookup"><span data-stu-id="67995-161">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="67995-162">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="67995-162">-RequiredModules</span></span>

<span data-ttu-id="67995-163">Hiermee worden modules opgegeven die de algemene sessie status moeten hebben.</span><span class="sxs-lookup"><span data-stu-id="67995-163">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="67995-164">Als de vereiste modules zich niet in de globale sessie status bevinden, worden ze door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="67995-164">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="67995-165">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="67995-165">-RequiredScripts</span></span>

<span data-ttu-id="67995-166">Hiermee geeft u een matrix met vereiste scripts op.</span><span class="sxs-lookup"><span data-stu-id="67995-166">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="67995-167">-Tags</span><span class="sxs-lookup"><span data-stu-id="67995-167">-Tags</span></span>

<span data-ttu-id="67995-168">Hiermee geeft u een matrix met tags op.</span><span class="sxs-lookup"><span data-stu-id="67995-168">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="67995-169">-Versie</span><span class="sxs-lookup"><span data-stu-id="67995-169">-Version</span></span>

<span data-ttu-id="67995-170">Hiermee geeft u de versie van het script op.</span><span class="sxs-lookup"><span data-stu-id="67995-170">Specifies the script's version.</span></span>

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

### <span data-ttu-id="67995-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="67995-171">-WhatIf</span></span>

<span data-ttu-id="67995-172">Hier wordt weer gegeven wat er gebeurt als er `Update-ScriptFileInfo` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="67995-172">Shows what would happen if `Update-ScriptFileInfo` runs.</span></span> <span data-ttu-id="67995-173">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="67995-173">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="67995-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="67995-174">CommonParameters</span></span>

<span data-ttu-id="67995-175">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="67995-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="67995-176">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="67995-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="67995-177">INVOER</span><span class="sxs-lookup"><span data-stu-id="67995-177">INPUTS</span></span>

## <span data-ttu-id="67995-178">UITVOER</span><span class="sxs-lookup"><span data-stu-id="67995-178">OUTPUTS</span></span>

## <span data-ttu-id="67995-179">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="67995-179">NOTES</span></span>

<span data-ttu-id="67995-180">Gebruik de `Test-ScriptFileInfo` cmdlet om de meta gegevens van een script te valideren.</span><span class="sxs-lookup"><span data-stu-id="67995-180">Use the `Test-ScriptFileInfo` cmdlet to validate a script's metadata.</span></span> <span data-ttu-id="67995-181">Scripts moeten waarden bevatten voor versie, GUID, beschrijving en auteur.</span><span class="sxs-lookup"><span data-stu-id="67995-181">Scripts must include values for version, GUID, description, and author.</span></span>

## <span data-ttu-id="67995-182">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="67995-182">RELATED LINKS</span></span>

[<span data-ttu-id="67995-183">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="67995-183">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="67995-184">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="67995-184">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)