---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/09/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-scriptfileinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ScriptFileInfo
ms.openlocfilehash: de138a27ed9425057406dc6120a8354b72a3b8a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706142"
---
# <span data-ttu-id="12b8d-102">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="12b8d-102">Update-ScriptFileInfo</span></span>

## <span data-ttu-id="12b8d-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="12b8d-103">SYNOPSIS</span></span>
<span data-ttu-id="12b8d-104">Hiermee wordt informatie over een script bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="12b8d-104">Updates information for a script.</span></span>

## <span data-ttu-id="12b8d-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="12b8d-105">SYNTAX</span></span>

### <span data-ttu-id="12b8d-106">PathParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="12b8d-106">PathParameterSet (Default)</span></span>

```
Update-ScriptFileInfo [-Path] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="12b8d-107">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="12b8d-107">LiteralPathParameterSet</span></span>

```
Update-ScriptFileInfo [-LiteralPath] <String> [-Version <String>] [-Author <String>] [-Guid <Guid>]
 [-Description <String>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="12b8d-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="12b8d-108">DESCRIPTION</span></span>

<span data-ttu-id="12b8d-109">Met de cmdlet worden de `Update-ScriptFileInfo` eigenschaps waarden van een script bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="12b8d-109">The `Update-ScriptFileInfo` cmdlet updates a script's property values.</span></span> <span data-ttu-id="12b8d-110">Bijvoorbeeld: de waarden voor versie, auteur of beschrijving.</span><span class="sxs-lookup"><span data-stu-id="12b8d-110">For example, the values for version, author, or description.</span></span>

## <span data-ttu-id="12b8d-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="12b8d-111">EXAMPLES</span></span>

### <span data-ttu-id="12b8d-112">Voor beeld 1: de versie van een script bestand bijwerken</span><span class="sxs-lookup"><span data-stu-id="12b8d-112">Example 1: Update the version of a script file</span></span>

<span data-ttu-id="12b8d-113">In dit voor beeld wordt een bestaand script bestand bijgewerkt met nieuwe eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="12b8d-113">In this example, an existing script file is updated with new property values.</span></span>

<span data-ttu-id="12b8d-114">Splatting wordt gebruikt om para meters door te geven aan de `Update-ScriptFileInfo` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="12b8d-114">Splatting is used to pass parameters to the `Update-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="12b8d-115">Zie [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12b8d-115">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

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

<span data-ttu-id="12b8d-116">`$Parms` Hiermee slaat u de parameter waarden voor **pad**, **versie**, **Auteur**, **Bedrijfs naam** en **Beschrijving** op.</span><span class="sxs-lookup"><span data-stu-id="12b8d-116">`$Parms` stores the parameter values for **Path**, **Version**, **Author**, **CompanyName**, and **Description**.</span></span> <span data-ttu-id="12b8d-117">`Update-ScriptFileInfo` Hiermee worden de parameter waarden opgehaald uit `@Parms` en wordt het script bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="12b8d-117">`Update-ScriptFileInfo` gets the parameter values from `@Parms` and updates the script.</span></span> <span data-ttu-id="12b8d-118">Met de para meter **PassThru** wordt de inhoud van het script weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="12b8d-118">The **PassThru** parameter displays the script's contents in the PowerShell console.</span></span>

## <span data-ttu-id="12b8d-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12b8d-119">PARAMETERS</span></span>

### <span data-ttu-id="12b8d-120">-Author</span><span class="sxs-lookup"><span data-stu-id="12b8d-120">-Author</span></span>

<span data-ttu-id="12b8d-121">Hiermee geeft u de auteur van het script.</span><span class="sxs-lookup"><span data-stu-id="12b8d-121">Specifies the script author.</span></span>

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

### <span data-ttu-id="12b8d-122">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="12b8d-122">-CompanyName</span></span>

<span data-ttu-id="12b8d-123">Hiermee geeft u het bedrijf of de leverancier op die het script heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="12b8d-123">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="12b8d-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="12b8d-124">-Confirm</span></span>

<span data-ttu-id="12b8d-125">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Update-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="12b8d-125">Prompts you for confirmation before running `Update-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="12b8d-126">-Copyright</span><span class="sxs-lookup"><span data-stu-id="12b8d-126">-Copyright</span></span>

<span data-ttu-id="12b8d-127">Hiermee geeft u een copyright verklaring voor het script op.</span><span class="sxs-lookup"><span data-stu-id="12b8d-127">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="12b8d-128">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="12b8d-128">-Description</span></span>

<span data-ttu-id="12b8d-129">Hiermee geeft u een beschrijving op voor het script.</span><span class="sxs-lookup"><span data-stu-id="12b8d-129">Specifies a description for the script.</span></span>

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

### <span data-ttu-id="12b8d-130">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="12b8d-130">-ExternalModuleDependencies</span></span>

<span data-ttu-id="12b8d-131">Hiermee geeft u een matrix met externe module-afhankelijkheden op.</span><span class="sxs-lookup"><span data-stu-id="12b8d-131">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="12b8d-132">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="12b8d-132">-ExternalScriptDependencies</span></span>

<span data-ttu-id="12b8d-133">Hiermee geeft u een matrix met externe script afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="12b8d-133">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="12b8d-134">-Force</span><span class="sxs-lookup"><span data-stu-id="12b8d-134">-Force</span></span>

<span data-ttu-id="12b8d-135">Er wordt geforceerd `Update-ScriptFileInfo` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="12b8d-135">Forces `Update-ScriptFileInfo` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="12b8d-136">-GUID</span><span class="sxs-lookup"><span data-stu-id="12b8d-136">-Guid</span></span>

<span data-ttu-id="12b8d-137">Hiermee geeft u een unieke ID voor een script op.</span><span class="sxs-lookup"><span data-stu-id="12b8d-137">Specifies a unique ID for a script.</span></span>

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

### <span data-ttu-id="12b8d-138">-IconUri</span><span class="sxs-lookup"><span data-stu-id="12b8d-138">-IconUri</span></span>

<span data-ttu-id="12b8d-139">Hiermee geeft u de URL van een pictogram voor het script.</span><span class="sxs-lookup"><span data-stu-id="12b8d-139">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="12b8d-140">Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor het script.</span><span class="sxs-lookup"><span data-stu-id="12b8d-140">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="12b8d-141">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="12b8d-141">-LicenseUri</span></span>

<span data-ttu-id="12b8d-142">Hiermee geeft u de URL van de licentie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="12b8d-142">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="12b8d-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="12b8d-143">-LiteralPath</span></span>

<span data-ttu-id="12b8d-144">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="12b8d-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="12b8d-145">De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="12b8d-145">The **LiteralPath** parameter's value is used exactly as it's entered.</span></span> <span data-ttu-id="12b8d-146">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="12b8d-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="12b8d-147">Als het pad escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="12b8d-147">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="12b8d-148">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="12b8d-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="12b8d-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="12b8d-149">-PassThru</span></span>

<span data-ttu-id="12b8d-150">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="12b8d-150">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="12b8d-151">Standaard genereert geen `Update-ScriptFileInfo` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="12b8d-151">By default, `Update-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="12b8d-152">-Path</span><span class="sxs-lookup"><span data-stu-id="12b8d-152">-Path</span></span>

<span data-ttu-id="12b8d-153">Hiermee geeft u de locatie van het script bestand.</span><span class="sxs-lookup"><span data-stu-id="12b8d-153">Specifies the script file's location.</span></span> <span data-ttu-id="12b8d-154">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="12b8d-154">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="12b8d-155">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="12b8d-155">-PrivateData</span></span>

<span data-ttu-id="12b8d-156">Hiermee geeft u de persoonlijke gegevens voor het script.</span><span class="sxs-lookup"><span data-stu-id="12b8d-156">Specifies the private data for the script.</span></span>

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

### <span data-ttu-id="12b8d-157">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="12b8d-157">-ProjectUri</span></span>

<span data-ttu-id="12b8d-158">Hiermee geeft u de URL van een webpagina over dit project op.</span><span class="sxs-lookup"><span data-stu-id="12b8d-158">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="12b8d-159">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="12b8d-159">-ReleaseNotes</span></span>

<span data-ttu-id="12b8d-160">Hiermee geeft u een teken reeks matrix met release opmerkingen of opmerkingen die u beschikbaar wilt stellen voor deze versie van het script.</span><span class="sxs-lookup"><span data-stu-id="12b8d-160">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="12b8d-161">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="12b8d-161">-RequiredModules</span></span>

<span data-ttu-id="12b8d-162">Hiermee worden modules opgegeven die de algemene sessie status moeten hebben.</span><span class="sxs-lookup"><span data-stu-id="12b8d-162">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="12b8d-163">Als de vereiste modules zich niet in de globale sessie status bevinden, worden ze door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="12b8d-163">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="12b8d-164">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="12b8d-164">-RequiredScripts</span></span>

<span data-ttu-id="12b8d-165">Hiermee geeft u een matrix met vereiste scripts op.</span><span class="sxs-lookup"><span data-stu-id="12b8d-165">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="12b8d-166">-Tags</span><span class="sxs-lookup"><span data-stu-id="12b8d-166">-Tags</span></span>

<span data-ttu-id="12b8d-167">Hiermee geeft u een matrix met tags op.</span><span class="sxs-lookup"><span data-stu-id="12b8d-167">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="12b8d-168">-Versie</span><span class="sxs-lookup"><span data-stu-id="12b8d-168">-Version</span></span>

<span data-ttu-id="12b8d-169">Hiermee geeft u de versie van het script op.</span><span class="sxs-lookup"><span data-stu-id="12b8d-169">Specifies the script's version.</span></span>

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

### <span data-ttu-id="12b8d-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="12b8d-170">-WhatIf</span></span>

<span data-ttu-id="12b8d-171">Hier wordt weer gegeven wat er gebeurt als er `Update-ScriptFileInfo` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="12b8d-171">Shows what would happen if `Update-ScriptFileInfo` runs.</span></span> <span data-ttu-id="12b8d-172">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="12b8d-172">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="12b8d-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12b8d-173">CommonParameters</span></span>

<span data-ttu-id="12b8d-174">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="12b8d-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12b8d-175">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12b8d-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12b8d-176">INVOER</span><span class="sxs-lookup"><span data-stu-id="12b8d-176">INPUTS</span></span>

### <span data-ttu-id="12b8d-177">System. String</span><span class="sxs-lookup"><span data-stu-id="12b8d-177">System.String</span></span>

## <span data-ttu-id="12b8d-178">UITVOER</span><span class="sxs-lookup"><span data-stu-id="12b8d-178">OUTPUTS</span></span>

### <span data-ttu-id="12b8d-179">System. object</span><span class="sxs-lookup"><span data-stu-id="12b8d-179">System.Object</span></span>

## <span data-ttu-id="12b8d-180">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="12b8d-180">NOTES</span></span>

<span data-ttu-id="12b8d-181">Gebruik de `Test-ScriptFileInfo` cmdlet om de meta gegevens van een script te valideren.</span><span class="sxs-lookup"><span data-stu-id="12b8d-181">Use the `Test-ScriptFileInfo` cmdlet to validate a script's metadata.</span></span> <span data-ttu-id="12b8d-182">Scripts moeten waarden bevatten voor versie, GUID, beschrijving en auteur.</span><span class="sxs-lookup"><span data-stu-id="12b8d-182">Scripts must include values for version, GUID, description, and author.</span></span>

## <span data-ttu-id="12b8d-183">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="12b8d-183">RELATED LINKS</span></span>

[<span data-ttu-id="12b8d-184">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="12b8d-184">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="12b8d-185">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="12b8d-185">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

