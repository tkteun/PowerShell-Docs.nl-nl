---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/new-scriptfileinfo?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScriptFileInfo
ms.openlocfilehash: d3e3c0ec257bd9c405accaf3051abd1ae4501f0f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705985"
---
# <span data-ttu-id="99714-102">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="99714-102">New-ScriptFileInfo</span></span>

## <span data-ttu-id="99714-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="99714-103">SYNOPSIS</span></span>
<span data-ttu-id="99714-104">Hiermee maakt u een script bestand met meta gegevens.</span><span class="sxs-lookup"><span data-stu-id="99714-104">Creates a script file with metadata.</span></span>

## <span data-ttu-id="99714-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="99714-105">SYNTAX</span></span>

### <span data-ttu-id="99714-106">Alles</span><span class="sxs-lookup"><span data-stu-id="99714-106">All</span></span>

```
New-ScriptFileInfo [[-Path] <String>] [-Version <String>] [-Author <String>] -Description <String>
 [-Guid <Guid>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="99714-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="99714-107">DESCRIPTION</span></span>

<span data-ttu-id="99714-108">De `New-ScriptFileInfo` cmdlet maakt een Power shell-script bestand, inclusief meta gegevens over het script.</span><span class="sxs-lookup"><span data-stu-id="99714-108">The `New-ScriptFileInfo` cmdlet creates a PowerShell script file, including metadata about the script.</span></span>

<span data-ttu-id="99714-109">De voor beelden gebruiken splatting om para meters door te geven aan de `New-ScriptFileInfo` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="99714-109">The examples use splatting to pass parameters to the `New-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="99714-110">Zie [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="99714-110">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

## <span data-ttu-id="99714-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="99714-111">EXAMPLES</span></span>

### <span data-ttu-id="99714-112">Voor beeld 1: een script bestand maken en de versie, auteur en beschrijving opgeven</span><span class="sxs-lookup"><span data-stu-id="99714-112">Example 1: Create a script file and specify its version, author, and description</span></span>

<span data-ttu-id="99714-113">In dit voor beeld wordt een script bestand gemaakt en de inhoud ervan wordt weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="99714-113">In this example, a script file is created and its contents are displayed in the PowerShell console.</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\Temp-Scriptfile.ps1"
  Version = "1.0"
  Author = "pattif@contoso.com"
  Description = "My test script file description goes here"
  }
New-ScriptFileInfo @Parms
Get-Content -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
<#PSScriptInfo

.VERSION 1.0

.GUID 3bb10ee7-38c1-41b9-88ea-16899164fc19

.AUTHOR pattif@contoso.com

.COMPANYNAME

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
 My test script file description goes here

#>
Param()
```

<span data-ttu-id="99714-114">De `New-ScriptFileInfo` cmdlet gebruikt splatting om verschillende para meters voor het script te configureren.</span><span class="sxs-lookup"><span data-stu-id="99714-114">The `New-ScriptFileInfo` cmdlet uses splatting to configure several parameters for the script.</span></span>
<span data-ttu-id="99714-115">**Path** stelt de locatie en de naam van het script in.</span><span class="sxs-lookup"><span data-stu-id="99714-115">**Path** sets the location and name of the script.</span></span> <span data-ttu-id="99714-116">**Versie** Hiermee geeft u het versie nummer van het script op.</span><span class="sxs-lookup"><span data-stu-id="99714-116">**Version** specifies the script's version number.</span></span> <span data-ttu-id="99714-117">**Auteur** is het e-mail adres van de persoon die het script heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="99714-117">**Author** is the email address of the person who created the script.</span></span> <span data-ttu-id="99714-118">**Beschrijving** geeft uitleg over het doel van het script.</span><span class="sxs-lookup"><span data-stu-id="99714-118">**Description** explains the script's purpose.</span></span>

<span data-ttu-id="99714-119">Nadat het script is gemaakt, `Get-Content` gebruikt de para meter **Path** om het script te vinden.</span><span class="sxs-lookup"><span data-stu-id="99714-119">After the script is created, `Get-Content` uses the **Path** parameter to locate the script.</span></span> <span data-ttu-id="99714-120">De inhoud van het script wordt weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="99714-120">The script's contents are displayed in the PowerShell console.</span></span>

### <span data-ttu-id="99714-121">Voor beeld 2: een script bestand testen</span><span class="sxs-lookup"><span data-stu-id="99714-121">Example 2: Test a script file</span></span>

<span data-ttu-id="99714-122">In dit voor beeld wordt de meta gegevens voor het script dat is gemaakt in **voor beeld 1** getest.</span><span class="sxs-lookup"><span data-stu-id="99714-122">In this example, the metadata for the script created in **Example 1** is tested.</span></span>

```powershell
Test-ScriptFileInfo -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
Version   Name                  Author               Description
-------   ----                  ------               -----------
1.0       Temp-Scriptfile       pattif@contoso.com   My test script file description goes here
```

<span data-ttu-id="99714-123">De `Test-ScriptFileInfo` cmdlet gebruikt de para meter **Path** om de locatie van het script bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="99714-123">The `Test-ScriptFileInfo` cmdlet uses the **Path** parameter to specify the script file's location.</span></span>

### <span data-ttu-id="99714-124">Voor beeld 3: een script bestand maken met alle eigenschappen van meta gegevens</span><span class="sxs-lookup"><span data-stu-id="99714-124">Example 3: Create a script file with all the metadata properties</span></span>

<span data-ttu-id="99714-125">In dit voor beeld wordt splatting gebruikt voor het maken van een script bestand `New-ScriptFile.ps1` met de naam die alle eigenschappen van meta gegevens bevat.</span><span class="sxs-lookup"><span data-stu-id="99714-125">This example uses splatting to create a script file named `New-ScriptFile.ps1` that includes all its metadata properties.</span></span> <span data-ttu-id="99714-126">De para meter **uitgebreid** geeft aan dat er uitgebreide uitvoer wordt weer gegeven wanneer het script wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="99714-126">The **Verbose** parameter specifies that verbose output is displayed as the script is created.</span></span>

```powershell
$Parms = @{
 Path = "C:\Test\New-ScriptFile.ps1"
 Verbose = $True
 Version = "1.0"
 Author = "pattif@contoso.com"
 Description = "My new script file test"
 CompanyName = "Contoso Corporation"
 Copyright = "2019 Contoso Corporation. All rights reserved."
 ExternalModuleDependencies = "ff","bb"
 RequiredScripts = "Start-WFContosoServer", "Stop-ContosoServerScript"
 ExternalScriptDependencies = "Stop-ContosoServerScript"
 Tags = @("Tag1", "Tag2", "Tag3")
 ProjectUri = "https://contoso.com"
 LicenseUri = "https://contoso.com/License"
 IconUri = "https://contoso.com/Icon"
 PassThru = $True
 ReleaseNotes = @("Contoso script now supports the following features:",
   "Feature 1",
   "Feature 2",
   "Feature 3",
   "Feature 4",
   "Feature 5")
 RequiredModules =
   "1",
   "2",
   "RequiredModule1",
   @{ModuleName="RequiredModule2";ModuleVersion="1.0"},
   @{ModuleName="RequiredModule3";RequiredVersion="2.0"},
   "ExternalModule1"
 }
New-ScriptFileInfo @Parms
```

```Output
VERBOSE: Performing the operation "Creating the 'C:\Test\New-ScriptFile.ps1'
  PowerShell Script file" on target "C:\Test\New-ScriptFile.ps1".

<#PSScriptInfo

.VERSION 1.0

.GUID 4fabe8c7-7862-45b1-a72e-1352a433b77d

.AUTHOR pattif@contoso.com

.COMPANYNAME Contoso Corporation

.COPYRIGHT 2019 Contoso Corporation. All rights reserved.

.TAGS Tag1 Tag2 Tag3

.LICENSEURI https://contoso.com/License

.PROJECTURI https://contoso.com/

.ICONURI https://contoso.com/Icon

.EXTERNALMODULEDEPENDENCIES ff,bb

.REQUIREDSCRIPTS Start-WFContosoServer,Stop-ContosoServerScript

.EXTERNALSCRIPTDEPENDENCIES Stop-ContosoServerScript

.RELEASENOTES
Contoso script now supports the following features:
Feature 1
Feature 2
Feature 3
Feature 4
Feature 5

.PRIVATEDATA

#>

#Requires -Module 1
#Requires -Module 2
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '1.0'}
#Requires -Module @{RequiredVersion = '2.0'; ModuleName = 'RequiredModule3'}
#Requires -Module ExternalModule1

<#

.DESCRIPTION
 My new script file test

#>
Param()
```

## <span data-ttu-id="99714-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="99714-127">PARAMETERS</span></span>

### <span data-ttu-id="99714-128">-Author</span><span class="sxs-lookup"><span data-stu-id="99714-128">-Author</span></span>

<span data-ttu-id="99714-129">Hiermee geeft u de auteur van het script.</span><span class="sxs-lookup"><span data-stu-id="99714-129">Specifies the script author.</span></span>

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

### <span data-ttu-id="99714-130">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="99714-130">-CompanyName</span></span>

<span data-ttu-id="99714-131">Hiermee geeft u het bedrijf of de leverancier op die het script heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="99714-131">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="99714-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="99714-132">-Confirm</span></span>

<span data-ttu-id="99714-133">Vraagt u om bevestiging voordat de wordt uitgevoerd `New-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="99714-133">Prompts you for confirmation before running the `New-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="99714-134">-Copyright</span><span class="sxs-lookup"><span data-stu-id="99714-134">-Copyright</span></span>

<span data-ttu-id="99714-135">Hiermee geeft u een copyright verklaring voor het script op.</span><span class="sxs-lookup"><span data-stu-id="99714-135">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="99714-136">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="99714-136">-Description</span></span>

<span data-ttu-id="99714-137">Hiermee geeft u een beschrijving op voor het script.</span><span class="sxs-lookup"><span data-stu-id="99714-137">Specifies a description for the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="99714-138">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="99714-138">-ExternalModuleDependencies</span></span>

<span data-ttu-id="99714-139">Hiermee geeft u een matrix met externe module-afhankelijkheden op.</span><span class="sxs-lookup"><span data-stu-id="99714-139">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="99714-140">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="99714-140">-ExternalScriptDependencies</span></span>

<span data-ttu-id="99714-141">Hiermee geeft u een matrix met externe script afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="99714-141">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="99714-142">-Force</span><span class="sxs-lookup"><span data-stu-id="99714-142">-Force</span></span>

<span data-ttu-id="99714-143">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="99714-143">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="99714-144">-GUID</span><span class="sxs-lookup"><span data-stu-id="99714-144">-Guid</span></span>

<span data-ttu-id="99714-145">Hiermee geeft u een unieke ID op voor het script.</span><span class="sxs-lookup"><span data-stu-id="99714-145">Specifies a unique ID for the script.</span></span>

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

### <span data-ttu-id="99714-146">-IconUri</span><span class="sxs-lookup"><span data-stu-id="99714-146">-IconUri</span></span>

<span data-ttu-id="99714-147">Hiermee geeft u de URL van een pictogram voor het script.</span><span class="sxs-lookup"><span data-stu-id="99714-147">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="99714-148">Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor het script.</span><span class="sxs-lookup"><span data-stu-id="99714-148">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="99714-149">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="99714-149">-LicenseUri</span></span>

<span data-ttu-id="99714-150">Hiermee geeft u de URL van de licentie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="99714-150">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="99714-151">-PassThru</span><span class="sxs-lookup"><span data-stu-id="99714-151">-PassThru</span></span>

<span data-ttu-id="99714-152">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="99714-152">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="99714-153">Standaard genereert geen `New-ScriptFileInfo` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="99714-153">By default, `New-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="99714-154">-Path</span><span class="sxs-lookup"><span data-stu-id="99714-154">-Path</span></span>

<span data-ttu-id="99714-155">Hiermee geeft u de locatie op waar het script bestand wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="99714-155">Specifies the location where the script file is saved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="99714-156">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="99714-156">-PrivateData</span></span>

<span data-ttu-id="99714-157">Hiermee geeft u privé gegevens voor het script op.</span><span class="sxs-lookup"><span data-stu-id="99714-157">Specifies private data for the script.</span></span>

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

### <span data-ttu-id="99714-158">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="99714-158">-ProjectUri</span></span>

<span data-ttu-id="99714-159">Hiermee geeft u de URL van een webpagina over dit project op.</span><span class="sxs-lookup"><span data-stu-id="99714-159">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="99714-160">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="99714-160">-ReleaseNotes</span></span>

<span data-ttu-id="99714-161">Hiermee geeft u een teken reeks matrix met release opmerkingen of opmerkingen die u beschikbaar wilt stellen aan gebruikers van deze versie van het script.</span><span class="sxs-lookup"><span data-stu-id="99714-161">Specifies a string array that contains release notes or comments that you want available to users of this version of the script.</span></span>

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

### <span data-ttu-id="99714-162">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="99714-162">-RequiredModules</span></span>

<span data-ttu-id="99714-163">Hiermee worden modules opgegeven die de algemene sessie status moeten hebben.</span><span class="sxs-lookup"><span data-stu-id="99714-163">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="99714-164">Als de vereiste modules zich niet in de globale sessie status bevinden, worden ze door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="99714-164">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="99714-165">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="99714-165">-RequiredScripts</span></span>

<span data-ttu-id="99714-166">Hiermee geeft u een matrix met vereiste scripts op.</span><span class="sxs-lookup"><span data-stu-id="99714-166">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="99714-167">-Tags</span><span class="sxs-lookup"><span data-stu-id="99714-167">-Tags</span></span>

<span data-ttu-id="99714-168">Hiermee geeft u een matrix met tags op.</span><span class="sxs-lookup"><span data-stu-id="99714-168">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="99714-169">-Versie</span><span class="sxs-lookup"><span data-stu-id="99714-169">-Version</span></span>

<span data-ttu-id="99714-170">Hiermee geeft u de versie van het script.</span><span class="sxs-lookup"><span data-stu-id="99714-170">Specifies the version of the script.</span></span>

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

### <span data-ttu-id="99714-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="99714-171">-WhatIf</span></span>

<span data-ttu-id="99714-172">Hier wordt weer gegeven wat er gebeurt als er `New-ScriptFileInfo` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="99714-172">Shows what would happen if `New-ScriptFileInfo` runs.</span></span> <span data-ttu-id="99714-173">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="99714-173">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="99714-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="99714-174">CommonParameters</span></span>

<span data-ttu-id="99714-175">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="99714-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="99714-176">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="99714-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="99714-177">INVOER</span><span class="sxs-lookup"><span data-stu-id="99714-177">INPUTS</span></span>

### <span data-ttu-id="99714-178">System. String</span><span class="sxs-lookup"><span data-stu-id="99714-178">System.String</span></span>

## <span data-ttu-id="99714-179">UITVOER</span><span class="sxs-lookup"><span data-stu-id="99714-179">OUTPUTS</span></span>

### <span data-ttu-id="99714-180">System. object</span><span class="sxs-lookup"><span data-stu-id="99714-180">System.Object</span></span>

## <span data-ttu-id="99714-181">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="99714-181">NOTES</span></span>

## <span data-ttu-id="99714-182">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="99714-182">RELATED LINKS</span></span>

[<span data-ttu-id="99714-183">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="99714-183">about_Splatting</span></span>](../Microsoft.Powershell.Core/About/about_splatting.md)

[<span data-ttu-id="99714-184">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="99714-184">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="99714-185">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="99714-185">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)

