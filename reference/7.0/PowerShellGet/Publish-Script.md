---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-script?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Script
ms.openlocfilehash: a67610fdbee8a138eb0f4e37016cdf142248e3c3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249731"
---
# <span data-ttu-id="cff36-103">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="cff36-103">Publish-Script</span></span>

## <span data-ttu-id="cff36-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="cff36-104">SYNOPSIS</span></span>
<span data-ttu-id="cff36-105">Publiceert een script.</span><span class="sxs-lookup"><span data-stu-id="cff36-105">Publishes a script.</span></span>

## <span data-ttu-id="cff36-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="cff36-106">SYNTAX</span></span>

### <span data-ttu-id="cff36-107">PathParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="cff36-107">PathParameterSet (Default)</span></span>

```
Publish-Script -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="cff36-108">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="cff36-108">LiteralPathParameterSet</span></span>

```
Publish-Script -LiteralPath <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="cff36-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="cff36-109">DESCRIPTION</span></span>

<span data-ttu-id="cff36-110">De `Publish-Script` cmdlet publiceert het opgegeven script naar de online galerie.</span><span class="sxs-lookup"><span data-stu-id="cff36-110">The `Publish-Script` cmdlet publishes the specified script to the online gallery.</span></span>

## <span data-ttu-id="cff36-111">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="cff36-111">EXAMPLES</span></span>

### <span data-ttu-id="cff36-112">Voor beeld 1: een script bestand maken, inhoud toevoegen en publiceren</span><span class="sxs-lookup"><span data-stu-id="cff36-112">Example 1: Create a script file, add content to it, and publish it</span></span>

<span data-ttu-id="cff36-113">Met de `New-ScriptFileInfo` cmdlet maakt u een script bestand met de naam `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="cff36-113">The `New-ScriptFileInfo` cmdlet creates a script file named `Demo-Script.ps1`.</span></span> <span data-ttu-id="cff36-114">`Get-Content` Hiermee wordt de inhoud van weer gegeven `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="cff36-114">`Get-Content` displays the content of `Demo-Script.ps1`.</span></span> <span data-ttu-id="cff36-115">De `Add-Content` cmdlet voegt een functie en een werk stroom toe aan `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="cff36-115">The `Add-Content` cmdlet adds a function and a workflow to `Demo-Script.ps1`.</span></span>

```powershell
$newScriptInfo = @{
  Path = 'D:\ScriptSharingDemo\Demo-Script.ps1'
  Version = '1.0'
  Author = 'author@contoso.com'
  Description = "my test script file description goes here"
}
New-ScriptFileInfo @newScriptInfo
Get-Content -Path $newScriptInfo.Path
```

```Output
<#PSScriptInfo

.VERSION 1.0

.AUTHOR pattif@microsoft.com

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
#>

<#
.DESCRIPTION
 my test script file description goes here
#>
Param()
```

```powershell
Add-Content -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Value @"

Function Demo-ScriptFunction { 'Demo-ScriptFunction' }

Workflow Demo-ScriptWorkflow { 'Demo-ScriptWorkflow' }

Demo-ScriptFunction
Demo-ScriptWorkflow
"@
Test-ScriptFileInfo -Path D:\ScriptSharingDemo\Demo-Script.ps1
```

```Output
Version    Name                 Author                   Description
-------    ----                 ------                   -----------
1.0        Demo-Script          author@contoso.com       my test script file description goes here
```

```powershell
Publish-Script -Path D:\ScriptSharingDemo\Demo-Script.ps1 -Repository LocalRepo1
Find-Script -Repository LocalRepo1 -Name "Demo-Script"
```

```Output
Version    Name                 Type       Repository    Description
-------    ----                 ----       ----------    -----------
1.0        Demo-Script          Script     LocalRepo1    my test script file description goes here
```

<span data-ttu-id="cff36-116">De `Test-ScriptFileInfo` cmdlet wordt gevalideerd `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="cff36-116">The `Test-ScriptFileInfo` cmdlet validates `Demo-Script.ps1`.</span></span> <span data-ttu-id="cff36-117">De `Publish-Script` cmdlet publiceert het script naar de **LocalRepo1** -opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="cff36-117">The `Publish-Script` cmdlet publishes the script to the **LocalRepo1** repository.</span></span> <span data-ttu-id="cff36-118">Als laatste verwijst</span><span class="sxs-lookup"><span data-stu-id="cff36-118">Finally.</span></span> <span data-ttu-id="cff36-119">`Find-Script` wordt gebruikt om te zoeken `Demo-Script.ps1` in de **LocalRepo1** -opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="cff36-119">`Find-Script` is used to search for `Demo-Script.ps1` in the **LocalRepo1** repository.</span></span>

## <span data-ttu-id="cff36-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cff36-120">PARAMETERS</span></span>

### <span data-ttu-id="cff36-121">-Confirm</span><span class="sxs-lookup"><span data-stu-id="cff36-121">-Confirm</span></span>

<span data-ttu-id="cff36-122">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cff36-122">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="cff36-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="cff36-123">-Credential</span></span>

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

### <span data-ttu-id="cff36-124">-Force</span><span class="sxs-lookup"><span data-stu-id="cff36-124">-Force</span></span>

<span data-ttu-id="cff36-125">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="cff36-125">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="cff36-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="cff36-126">-LiteralPath</span></span>

<span data-ttu-id="cff36-127">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="cff36-127">Specifies a path to one or more locations.</span></span> <span data-ttu-id="cff36-128">In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact als ingevoerd gebruikt.</span><span class="sxs-lookup"><span data-stu-id="cff36-128">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="cff36-129">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="cff36-129">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="cff36-130">Als het pad escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="cff36-130">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="cff36-131">Enkele aanhalings tekens geven aan dat Windows Power shell geen tekens interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="cff36-131">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="cff36-132">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="cff36-132">-NuGetApiKey</span></span>

<span data-ttu-id="cff36-133">Hiermee geeft u de API-sleutel op die u wilt gebruiken voor het publiceren van een script in de online galerie.</span><span class="sxs-lookup"><span data-stu-id="cff36-133">Specifies the API key that you want to use to publish a script to the online gallery.</span></span> <span data-ttu-id="cff36-134">De API-sleutel maakt deel uit van uw profiel in de online galerie.</span><span class="sxs-lookup"><span data-stu-id="cff36-134">The API key is part of your profile in the online gallery.</span></span> <span data-ttu-id="cff36-135">Zie [Managing API Keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cff36-135">For more information see [Managing API keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span></span>

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

### <span data-ttu-id="cff36-136">-Path</span><span class="sxs-lookup"><span data-stu-id="cff36-136">-Path</span></span>

<span data-ttu-id="cff36-137">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="cff36-137">Specifies a path to one or more locations.</span></span> <span data-ttu-id="cff36-138">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="cff36-138">Wildcards are permitted.</span></span> <span data-ttu-id="cff36-139">De standaard locatie is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="cff36-139">The default location is the current directory.</span></span>

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: Named
Default value: <Current location>
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="cff36-140">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="cff36-140">-Repository</span></span>

<span data-ttu-id="cff36-141">Hiermee geeft u de beschrijvende naam op van een opslag plaats die is geregistreerd door te worden uitgevoerd `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="cff36-141">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span>

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

### <span data-ttu-id="cff36-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="cff36-142">-WhatIf</span></span>

<span data-ttu-id="cff36-143">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="cff36-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="cff36-144">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cff36-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="cff36-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cff36-145">CommonParameters</span></span>

<span data-ttu-id="cff36-146">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cff36-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cff36-147">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="cff36-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cff36-148">INVOER</span><span class="sxs-lookup"><span data-stu-id="cff36-148">INPUTS</span></span>

### <span data-ttu-id="cff36-149">System. String</span><span class="sxs-lookup"><span data-stu-id="cff36-149">System.String</span></span>

### <span data-ttu-id="cff36-150">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="cff36-150">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="cff36-151">UITVOER</span><span class="sxs-lookup"><span data-stu-id="cff36-151">OUTPUTS</span></span>

### <span data-ttu-id="cff36-152">System. object</span><span class="sxs-lookup"><span data-stu-id="cff36-152">System.Object</span></span>

## <span data-ttu-id="cff36-153">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="cff36-153">NOTES</span></span>

## <span data-ttu-id="cff36-154">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="cff36-154">RELATED LINKS</span></span>

[<span data-ttu-id="cff36-155">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="cff36-155">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="cff36-156">Install-script</span><span class="sxs-lookup"><span data-stu-id="cff36-156">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="cff36-157">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="cff36-157">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="cff36-158">Save-Script</span><span class="sxs-lookup"><span data-stu-id="cff36-158">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="cff36-159">Update-script</span><span class="sxs-lookup"><span data-stu-id="cff36-159">Update-Script</span></span>](Update-Script.md)
