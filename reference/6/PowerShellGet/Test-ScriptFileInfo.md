---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/test-scriptfileinfo?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ScriptFileInfo
ms.openlocfilehash: c773b247d5f0da4071517134b7187ba674bfbfbd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251077"
---
# <span data-ttu-id="c8916-103">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="c8916-103">Test-ScriptFileInfo</span></span>

## <span data-ttu-id="c8916-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c8916-104">SYNOPSIS</span></span>
<span data-ttu-id="c8916-105">Hiermee wordt een opmerkingen blok voor een script gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="c8916-105">Validates a comment block for a script.</span></span>

## <span data-ttu-id="c8916-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c8916-106">SYNTAX</span></span>

### <span data-ttu-id="c8916-107">PathParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="c8916-107">PathParameterSet (Default)</span></span>

```
Test-ScriptFileInfo [-Path] <String> [<CommonParameters>]
```

### <span data-ttu-id="c8916-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="c8916-108">LiteralPathParameterSet</span></span>

```
Test-ScriptFileInfo -LiteralPath <String> [<CommonParameters>]
```

## <span data-ttu-id="c8916-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c8916-109">DESCRIPTION</span></span>

<span data-ttu-id="c8916-110">De cmdlet **test-ScriptFileInfo** valideert het opmerkingen blok aan het begin van een script dat wordt gepubliceerd met de cmdlet Publish-Script.</span><span class="sxs-lookup"><span data-stu-id="c8916-110">The **Test-ScriptFileInfo** cmdlet validates the comment block at the beginning of a script that will be published with the Publish-Script cmdlet.</span></span>
<span data-ttu-id="c8916-111">Als er een fout is opgetreden in het blok met opmerkingen, retourneert deze cmdlet informatie over waar de fout zich bevindt of hoe deze moet worden gecorrigeerd.</span><span class="sxs-lookup"><span data-stu-id="c8916-111">If the comment block has an error, this cmdlet returns information about where the error is located or how to correct it.</span></span>

## <span data-ttu-id="c8916-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c8916-112">EXAMPLES</span></span>

### <span data-ttu-id="c8916-113">Voor beeld 1: een script bestand testen</span><span class="sxs-lookup"><span data-stu-id="c8916-113">Example 1: Test a script file</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "C:\temp\temp_scripts\New-ScriptFile.ps1"
Version    Name                      Author               Description
-------    ----                      ------               -----------
1.0        New-ScriptFile            pattif               my new script file test
```

<span data-ttu-id="c8916-114">Met deze opdracht wordt het New-ScriptFile.ps1-script bestand getest en worden de resultaten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c8916-114">This command tests the New-ScriptFile.ps1 script file and displays the results.</span></span>
<span data-ttu-id="c8916-115">Het script bestand bevat geldige meta gegevens.</span><span class="sxs-lookup"><span data-stu-id="c8916-115">The script file includes valid metadata.</span></span>

### <span data-ttu-id="c8916-116">Voor beeld 2: een script bestand met waarden voor alle eigenschappen van meta gegevens testen</span><span class="sxs-lookup"><span data-stu-id="c8916-116">Example 2: Test a script file that has values for all metadata properties</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Test-Runbook.ps1" | Format-List *
Name                       : Test-Runbook
Path                       : D:\code\Test-Runbook.ps1
ScriptBase                 : D:\code
ReleaseNotes               : {contoso script now supports following features, Feature 1, Feature 2, Feature 3...}
Version                    : 1.0
Guid                       : eb246b19-17da-4392-8c89-7c280f69ad0e
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
Tags                       : {Tag1, Tag2, Tag3}
LicenseUri                 : https://contoso.com/License
ProjectUri                 : https://contoso.com/
IconUri                    : https://contoso.com/MyScriptIcon
ExternalModuleDependencies : ExternalModule1
RequiredScripts            : {Start-WFContosoServer, Stop-ContosoServerScript}
ExternalScriptDependencies : Stop-ContosoServerScript
Description                : Contoso Script example
RequiredModules            : {RequiredModule1, @{ ModuleName = 'RequiredModule2'; ModuleVersion = '1.0' }, @{ ModuleName = 'RequiredModule3'; RequiredVersion = '2.0' }, ExternalModule1}
ExportedCommands           : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-Workflow...}
ExportedFunctions          : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-AdvPSCmdlet}
ExportedWorkflows          : My-Workflow
```

<span data-ttu-id="c8916-117">Met deze opdracht wordt het script bestand getest Test-Runbook.ps1 en wordt de pijplijn operator gebruikt om de resultaten door te geven aan de Format-List cmdlet om de resultaten op te maken.</span><span class="sxs-lookup"><span data-stu-id="c8916-117">This command tests the script file Test-Runbook.ps1 and uses the pipeline operator to pass the results to the Format-List cmdlet to format the results.</span></span>

### <span data-ttu-id="c8916-118">Voor beeld 3: een script bestand testen dat geen meta gegevens bevat</span><span class="sxs-lookup"><span data-stu-id="c8916-118">Example 3: Test a script file that has no metadata</span></span>

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Hello-World.ps1"
Test-ScriptFileInfo : Script 'D:\code\Hello-World.ps1' is missing required metadata properties. Verify that the script file has Version, Description
and Author properties. You can use the Update-ScriptFileInfo or New-ScriptFileInfo cmdlet to add or update the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo D:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidArgument: (D:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException

+ FullyQualifiedErrorId : MissingRequiredPSScriptInfoProperties,Test-ScriptFile
```

<span data-ttu-id="c8916-119">Met deze opdracht wordt het script bestand getest Hello-World.ps1, waaraan geen meta gegevens zijn gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="c8916-119">This command tests the script file Hello-World.ps1, which has no metadata associated with it.</span></span>

## <span data-ttu-id="c8916-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c8916-120">PARAMETERS</span></span>

### <span data-ttu-id="c8916-121">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c8916-121">-LiteralPath</span></span>

<span data-ttu-id="c8916-122">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="c8916-122">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="c8916-123">In tegens telling tot de para meter *Path* wordt de waarde van de para meter *LiteralPath* exact gebruikt wanneer deze wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="c8916-123">Unlike the *Path* parameter, the value of the *LiteralPath* parameter is used exactly as it is entered.</span></span>
<span data-ttu-id="c8916-124">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="c8916-124">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="c8916-125">Als het pad escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="c8916-125">If the path includes escape characters, enclose them in single quotation marks.</span></span>
<span data-ttu-id="c8916-126">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="c8916-126">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c8916-127">-Path</span><span class="sxs-lookup"><span data-stu-id="c8916-127">-Path</span></span>

<span data-ttu-id="c8916-128">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="c8916-128">Specifies a path to one or more locations.</span></span>
<span data-ttu-id="c8916-129">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="c8916-129">Wildcards are permitted.</span></span>
<span data-ttu-id="c8916-130">De standaard locatie is de huidige map (.).</span><span class="sxs-lookup"><span data-stu-id="c8916-130">The default location is the current directory (.).</span></span>

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

### <span data-ttu-id="c8916-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c8916-131">CommonParameters</span></span>

<span data-ttu-id="c8916-132">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c8916-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c8916-133">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c8916-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c8916-134">INVOER</span><span class="sxs-lookup"><span data-stu-id="c8916-134">INPUTS</span></span>

### <span data-ttu-id="c8916-135">System. String</span><span class="sxs-lookup"><span data-stu-id="c8916-135">System.String</span></span>

## <span data-ttu-id="c8916-136">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c8916-136">OUTPUTS</span></span>

### <span data-ttu-id="c8916-137">System. object</span><span class="sxs-lookup"><span data-stu-id="c8916-137">System.Object</span></span>

## <span data-ttu-id="c8916-138">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c8916-138">NOTES</span></span>

## <span data-ttu-id="c8916-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c8916-139">RELATED LINKS</span></span>

[<span data-ttu-id="c8916-140">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="c8916-140">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)

[<span data-ttu-id="c8916-141">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="c8916-141">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="c8916-142">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="c8916-142">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
