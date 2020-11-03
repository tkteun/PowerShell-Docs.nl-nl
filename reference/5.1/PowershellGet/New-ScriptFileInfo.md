---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/01/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/new-scriptfileinfo?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScriptFileInfo
ms.openlocfilehash: 551fe34d266cb9330e4f30e823972458255c7f49
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250751"
---
# <span data-ttu-id="0479f-103">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="0479f-103">New-ScriptFileInfo</span></span>

## <span data-ttu-id="0479f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="0479f-104">SYNOPSIS</span></span>
<span data-ttu-id="0479f-105">Hiermee maakt u een script bestand met meta gegevens.</span><span class="sxs-lookup"><span data-stu-id="0479f-105">Creates a script file with metadata.</span></span>

## <span data-ttu-id="0479f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="0479f-106">SYNTAX</span></span>

### <span data-ttu-id="0479f-107">Alles</span><span class="sxs-lookup"><span data-stu-id="0479f-107">All</span></span>

```
New-ScriptFileInfo [[-Path] <String>] [-Version <String>] [-Author <String>] -Description <String>
 [-Guid <Guid>] [-CompanyName <String>] [-Copyright <String>] [-RequiredModules <Object[]>]
 [-ExternalModuleDependencies <String[]>] [-RequiredScripts <String[]>]
 [-ExternalScriptDependencies <String[]>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>]
 [-IconUri <Uri>] [-ReleaseNotes <String[]>] [-PrivateData <String>] [-PassThru] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0479f-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0479f-108">DESCRIPTION</span></span>

<span data-ttu-id="0479f-109">De `New-ScriptFileInfo` cmdlet maakt een Power shell-script bestand, inclusief meta gegevens over het script.</span><span class="sxs-lookup"><span data-stu-id="0479f-109">The `New-ScriptFileInfo` cmdlet creates a PowerShell script file, including metadata about the script.</span></span>

<span data-ttu-id="0479f-110">De voor beelden gebruiken splatting om para meters door te geven aan de `New-ScriptFileInfo` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0479f-110">The examples use splatting to pass parameters to the `New-ScriptFileInfo` cmdlet.</span></span> <span data-ttu-id="0479f-111">Zie [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0479f-111">For more information, see [about_Splatting](../Microsoft.Powershell.Core/About/about_splatting.md).</span></span>

## <span data-ttu-id="0479f-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="0479f-112">EXAMPLES</span></span>

### <span data-ttu-id="0479f-113">Voor beeld 1: een script bestand maken en de versie, auteur en beschrijving opgeven</span><span class="sxs-lookup"><span data-stu-id="0479f-113">Example 1: Create a script file and specify its version, author, and description</span></span>

<span data-ttu-id="0479f-114">In dit voor beeld wordt een script bestand gemaakt en de inhoud ervan wordt weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="0479f-114">In this example, a script file is created and its contents are displayed in the PowerShell console.</span></span>

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

<span data-ttu-id="0479f-115">De `New-ScriptFileInfo` cmdlet gebruikt splatting om verschillende para meters voor het script te configureren.</span><span class="sxs-lookup"><span data-stu-id="0479f-115">The `New-ScriptFileInfo` cmdlet uses splatting to configure several parameters for the script.</span></span>
<span data-ttu-id="0479f-116">**Path** stelt de locatie en de naam van het script in.</span><span class="sxs-lookup"><span data-stu-id="0479f-116">**Path** sets the location and name of the script.</span></span> <span data-ttu-id="0479f-117">**Versie** Hiermee geeft u het versie nummer van het script op.</span><span class="sxs-lookup"><span data-stu-id="0479f-117">**Version** specifies the script's version number.</span></span> <span data-ttu-id="0479f-118">**Auteur** is het e-mail adres van de persoon die het script heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="0479f-118">**Author** is the email address of the person who created the script.</span></span> <span data-ttu-id="0479f-119">**Beschrijving** geeft uitleg over het doel van het script.</span><span class="sxs-lookup"><span data-stu-id="0479f-119">**Description** explains the script's purpose.</span></span>

<span data-ttu-id="0479f-120">Nadat het script is gemaakt, `Get-Content` gebruikt de para meter **Path** om het script te vinden.</span><span class="sxs-lookup"><span data-stu-id="0479f-120">After the script is created, `Get-Content` uses the **Path** parameter to locate the script.</span></span> <span data-ttu-id="0479f-121">De inhoud van het script wordt weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="0479f-121">The script's contents are displayed in the PowerShell console.</span></span>

### <span data-ttu-id="0479f-122">Voor beeld 2: een script bestand testen</span><span class="sxs-lookup"><span data-stu-id="0479f-122">Example 2: Test a script file</span></span>

<span data-ttu-id="0479f-123">In dit voor beeld wordt de meta gegevens voor het script dat is gemaakt in **voor beeld 1** getest.</span><span class="sxs-lookup"><span data-stu-id="0479f-123">In this example, the metadata for the script created in **Example 1** is tested.</span></span>

```powershell
Test-ScriptFileInfo -Path C:\Test\Temp-Scriptfile.ps1
```

```Output
Version   Name                  Author               Description
-------   ----                  ------               -----------
1.0       Temp-Scriptfile       pattif@contoso.com   My test script file description goes here
```

<span data-ttu-id="0479f-124">De `Test-ScriptFileInfo` cmdlet gebruikt de para meter **Path** om de locatie van het script bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="0479f-124">The `Test-ScriptFileInfo` cmdlet uses the **Path** parameter to specify the script file's location.</span></span>

### <span data-ttu-id="0479f-125">Voor beeld 3: een script bestand maken met alle eigenschappen van meta gegevens</span><span class="sxs-lookup"><span data-stu-id="0479f-125">Example 3: Create a script file with all the metadata properties</span></span>

<span data-ttu-id="0479f-126">In dit voor beeld wordt splatting gebruikt voor het maken van een script bestand `New-ScriptFile.ps1` met de naam die alle eigenschappen van meta gegevens bevat.</span><span class="sxs-lookup"><span data-stu-id="0479f-126">This example uses splatting to create a script file named `New-ScriptFile.ps1` that includes all its metadata properties.</span></span> <span data-ttu-id="0479f-127">De para meter **uitgebreid** geeft aan dat er uitgebreide uitvoer wordt weer gegeven wanneer het script wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="0479f-127">The **Verbose** parameter specifies that verbose output is displayed as the script is created.</span></span>

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

## <span data-ttu-id="0479f-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0479f-128">PARAMETERS</span></span>

### <span data-ttu-id="0479f-129">-Author</span><span class="sxs-lookup"><span data-stu-id="0479f-129">-Author</span></span>

<span data-ttu-id="0479f-130">Hiermee geeft u de auteur van het script.</span><span class="sxs-lookup"><span data-stu-id="0479f-130">Specifies the script author.</span></span>

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

### <span data-ttu-id="0479f-131">-CompanyName</span><span class="sxs-lookup"><span data-stu-id="0479f-131">-CompanyName</span></span>

<span data-ttu-id="0479f-132">Hiermee geeft u het bedrijf of de leverancier op die het script heeft gemaakt.</span><span class="sxs-lookup"><span data-stu-id="0479f-132">Specifies the company or vendor who created the script.</span></span>

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

### <span data-ttu-id="0479f-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0479f-133">-Confirm</span></span>

<span data-ttu-id="0479f-134">Vraagt u om bevestiging voordat de wordt uitgevoerd `New-ScriptFileInfo` .</span><span class="sxs-lookup"><span data-stu-id="0479f-134">Prompts you for confirmation before running the `New-ScriptFileInfo`.</span></span>

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

### <span data-ttu-id="0479f-135">-Copyright</span><span class="sxs-lookup"><span data-stu-id="0479f-135">-Copyright</span></span>

<span data-ttu-id="0479f-136">Hiermee geeft u een copyright verklaring voor het script op.</span><span class="sxs-lookup"><span data-stu-id="0479f-136">Specifies a copyright statement for the script.</span></span>

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

### <span data-ttu-id="0479f-137">-Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0479f-137">-Description</span></span>

<span data-ttu-id="0479f-138">Hiermee geeft u een beschrijving op voor het script.</span><span class="sxs-lookup"><span data-stu-id="0479f-138">Specifies a description for the script.</span></span>

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

### <span data-ttu-id="0479f-139">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="0479f-139">-ExternalModuleDependencies</span></span>

<span data-ttu-id="0479f-140">Hiermee geeft u een matrix met externe module-afhankelijkheden op.</span><span class="sxs-lookup"><span data-stu-id="0479f-140">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="0479f-141">-ExternalScriptDependencies</span><span class="sxs-lookup"><span data-stu-id="0479f-141">-ExternalScriptDependencies</span></span>

<span data-ttu-id="0479f-142">Hiermee geeft u een matrix met externe script afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="0479f-142">Specifies an array of external script dependencies.</span></span>

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

### <span data-ttu-id="0479f-143">-Force</span><span class="sxs-lookup"><span data-stu-id="0479f-143">-Force</span></span>

<span data-ttu-id="0479f-144">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="0479f-144">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0479f-145">-GUID</span><span class="sxs-lookup"><span data-stu-id="0479f-145">-Guid</span></span>

<span data-ttu-id="0479f-146">Hiermee geeft u een unieke ID op voor het script.</span><span class="sxs-lookup"><span data-stu-id="0479f-146">Specifies a unique ID for the script.</span></span>

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

### <span data-ttu-id="0479f-147">-IconUri</span><span class="sxs-lookup"><span data-stu-id="0479f-147">-IconUri</span></span>

<span data-ttu-id="0479f-148">Hiermee geeft u de URL van een pictogram voor het script.</span><span class="sxs-lookup"><span data-stu-id="0479f-148">Specifies the URL of an icon for the script.</span></span> <span data-ttu-id="0479f-149">Het opgegeven pictogram wordt weer gegeven op de galerie webpagina voor het script.</span><span class="sxs-lookup"><span data-stu-id="0479f-149">The specified icon is displayed on the gallery web page for the script.</span></span>

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

### <span data-ttu-id="0479f-150">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="0479f-150">-LicenseUri</span></span>

<span data-ttu-id="0479f-151">Hiermee geeft u de URL van de licentie voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="0479f-151">Specifies the URL of licensing terms.</span></span>

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

### <span data-ttu-id="0479f-152">-PassThru</span><span class="sxs-lookup"><span data-stu-id="0479f-152">-PassThru</span></span>

<span data-ttu-id="0479f-153">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="0479f-153">Returns an object that represents the item with which you're working.</span></span> <span data-ttu-id="0479f-154">Standaard genereert geen `New-ScriptFileInfo` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="0479f-154">By default, `New-ScriptFileInfo` doesn't generate any output.</span></span>

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

### <span data-ttu-id="0479f-155">-Path</span><span class="sxs-lookup"><span data-stu-id="0479f-155">-Path</span></span>

<span data-ttu-id="0479f-156">Hiermee geeft u de locatie op waar het script bestand wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="0479f-156">Specifies the location where the script file is saved.</span></span>

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

### <span data-ttu-id="0479f-157">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="0479f-157">-PrivateData</span></span>

<span data-ttu-id="0479f-158">Hiermee geeft u privé gegevens voor het script op.</span><span class="sxs-lookup"><span data-stu-id="0479f-158">Specifies private data for the script.</span></span>

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

### <span data-ttu-id="0479f-159">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="0479f-159">-ProjectUri</span></span>

<span data-ttu-id="0479f-160">Hiermee geeft u de URL van een webpagina over dit project op.</span><span class="sxs-lookup"><span data-stu-id="0479f-160">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="0479f-161">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="0479f-161">-ReleaseNotes</span></span>

<span data-ttu-id="0479f-162">Hiermee geeft u een teken reeks matrix met release opmerkingen of opmerkingen die u beschikbaar wilt stellen aan gebruikers van deze versie van het script.</span><span class="sxs-lookup"><span data-stu-id="0479f-162">Specifies a string array that contains release notes or comments that you want available to users of this version of the script.</span></span>

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

### <span data-ttu-id="0479f-163">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="0479f-163">-RequiredModules</span></span>

<span data-ttu-id="0479f-164">Hiermee worden modules opgegeven die de algemene sessie status moeten hebben.</span><span class="sxs-lookup"><span data-stu-id="0479f-164">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="0479f-165">Als de vereiste modules zich niet in de globale sessie status bevinden, worden ze door Power shell geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="0479f-165">If the required modules aren't in the global session state, PowerShell imports them.</span></span>

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

### <span data-ttu-id="0479f-166">-RequiredScripts</span><span class="sxs-lookup"><span data-stu-id="0479f-166">-RequiredScripts</span></span>

<span data-ttu-id="0479f-167">Hiermee geeft u een matrix met vereiste scripts op.</span><span class="sxs-lookup"><span data-stu-id="0479f-167">Specifies an array of required scripts.</span></span>

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

### <span data-ttu-id="0479f-168">-Tags</span><span class="sxs-lookup"><span data-stu-id="0479f-168">-Tags</span></span>

<span data-ttu-id="0479f-169">Hiermee geeft u een matrix met tags op.</span><span class="sxs-lookup"><span data-stu-id="0479f-169">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="0479f-170">-Versie</span><span class="sxs-lookup"><span data-stu-id="0479f-170">-Version</span></span>

<span data-ttu-id="0479f-171">Hiermee geeft u de versie van het script.</span><span class="sxs-lookup"><span data-stu-id="0479f-171">Specifies the version of the script.</span></span>

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

### <span data-ttu-id="0479f-172">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0479f-172">-WhatIf</span></span>

<span data-ttu-id="0479f-173">Hier wordt weer gegeven wat er gebeurt als er `New-ScriptFileInfo` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0479f-173">Shows what would happen if `New-ScriptFileInfo` runs.</span></span> <span data-ttu-id="0479f-174">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0479f-174">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="0479f-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0479f-175">CommonParameters</span></span>

<span data-ttu-id="0479f-176">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0479f-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0479f-177">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0479f-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0479f-178">INVOER</span><span class="sxs-lookup"><span data-stu-id="0479f-178">INPUTS</span></span>

## <span data-ttu-id="0479f-179">UITVOER</span><span class="sxs-lookup"><span data-stu-id="0479f-179">OUTPUTS</span></span>

## <span data-ttu-id="0479f-180">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="0479f-180">NOTES</span></span>

## <span data-ttu-id="0479f-181">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="0479f-181">RELATED LINKS</span></span>

[<span data-ttu-id="0479f-182">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="0479f-182">about_Splatting</span></span>](../Microsoft.Powershell.Core/About/about_splatting.md)

[<span data-ttu-id="0479f-183">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="0479f-183">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="0479f-184">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="0479f-184">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
