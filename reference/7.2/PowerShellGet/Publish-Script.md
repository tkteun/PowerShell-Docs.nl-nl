---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Script
ms.openlocfilehash: 344a789c9daced51b549d562b7fd74677fe403dc
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889200"
---
# <span data-ttu-id="edd47-102">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="edd47-102">Publish-Script</span></span>

## <span data-ttu-id="edd47-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="edd47-103">SYNOPSIS</span></span>
<span data-ttu-id="edd47-104">Publiceert een script.</span><span class="sxs-lookup"><span data-stu-id="edd47-104">Publishes a script.</span></span>

## <span data-ttu-id="edd47-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="edd47-105">SYNTAX</span></span>

### <span data-ttu-id="edd47-106">PathParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="edd47-106">PathParameterSet (Default)</span></span>

```
Publish-Script -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="edd47-107">LiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="edd47-107">LiteralPathParameterSet</span></span>

```
Publish-Script -LiteralPath <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="edd47-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="edd47-108">DESCRIPTION</span></span>

<span data-ttu-id="edd47-109">De `Publish-Script` cmdlet publiceert het opgegeven script naar de online galerie.</span><span class="sxs-lookup"><span data-stu-id="edd47-109">The `Publish-Script` cmdlet publishes the specified script to the online gallery.</span></span>

## <span data-ttu-id="edd47-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="edd47-110">EXAMPLES</span></span>

### <span data-ttu-id="edd47-111">Voor beeld 1: een script bestand maken, inhoud toevoegen en publiceren</span><span class="sxs-lookup"><span data-stu-id="edd47-111">Example 1: Create a script file, add content to it, and publish it</span></span>

<span data-ttu-id="edd47-112">Met de `New-ScriptFileInfo` cmdlet maakt u een script bestand met de naam `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="edd47-112">The `New-ScriptFileInfo` cmdlet creates a script file named `Demo-Script.ps1`.</span></span> <span data-ttu-id="edd47-113">`Get-Content` Hiermee wordt de inhoud van weer gegeven `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="edd47-113">`Get-Content` displays the content of `Demo-Script.ps1`.</span></span> <span data-ttu-id="edd47-114">De `Add-Content` cmdlet voegt een functie en een werk stroom toe aan `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="edd47-114">The `Add-Content` cmdlet adds a function and a workflow to `Demo-Script.ps1`.</span></span>

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

<span data-ttu-id="edd47-115">De `Test-ScriptFileInfo` cmdlet wordt gevalideerd `Demo-Script.ps1` .</span><span class="sxs-lookup"><span data-stu-id="edd47-115">The `Test-ScriptFileInfo` cmdlet validates `Demo-Script.ps1`.</span></span> <span data-ttu-id="edd47-116">De `Publish-Script` cmdlet publiceert het script naar de **LocalRepo1** -opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="edd47-116">The `Publish-Script` cmdlet publishes the script to the **LocalRepo1** repository.</span></span> <span data-ttu-id="edd47-117">Als laatste verwijst</span><span class="sxs-lookup"><span data-stu-id="edd47-117">Finally.</span></span> <span data-ttu-id="edd47-118">`Find-Script` wordt gebruikt om te zoeken `Demo-Script.ps1` in de **LocalRepo1** -opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="edd47-118">`Find-Script` is used to search for `Demo-Script.ps1` in the **LocalRepo1** repository.</span></span>

## <span data-ttu-id="edd47-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="edd47-119">PARAMETERS</span></span>

### <span data-ttu-id="edd47-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="edd47-120">-Confirm</span></span>

<span data-ttu-id="edd47-121">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="edd47-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="edd47-122">-Credential</span><span class="sxs-lookup"><span data-stu-id="edd47-122">-Credential</span></span>

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

### <span data-ttu-id="edd47-123">-Force</span><span class="sxs-lookup"><span data-stu-id="edd47-123">-Force</span></span>

<span data-ttu-id="edd47-124">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="edd47-124">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="edd47-125">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="edd47-125">-LiteralPath</span></span>

<span data-ttu-id="edd47-126">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="edd47-126">Specifies a path to one or more locations.</span></span> <span data-ttu-id="edd47-127">In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact als ingevoerd gebruikt.</span><span class="sxs-lookup"><span data-stu-id="edd47-127">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="edd47-128">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="edd47-128">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="edd47-129">Als het pad escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="edd47-129">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="edd47-130">Enkele aanhalings tekens geven aan dat Windows Power shell geen tekens interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="edd47-130">Single quotation marks tell Windows PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="edd47-131">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="edd47-131">-NuGetApiKey</span></span>

<span data-ttu-id="edd47-132">Hiermee geeft u de API-sleutel op die u wilt gebruiken voor het publiceren van een script in de online galerie.</span><span class="sxs-lookup"><span data-stu-id="edd47-132">Specifies the API key that you want to use to publish a script to the online gallery.</span></span> <span data-ttu-id="edd47-133">De API-sleutel maakt deel uit van uw profiel in de online galerie.</span><span class="sxs-lookup"><span data-stu-id="edd47-133">The API key is part of your profile in the online gallery.</span></span> <span data-ttu-id="edd47-134">Zie [Managing API Keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="edd47-134">For more information see [Managing API keys](/powershell/scripting/gallery/how-to/managing-profile/creating-apikeys).</span></span>

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

### <span data-ttu-id="edd47-135">-Path</span><span class="sxs-lookup"><span data-stu-id="edd47-135">-Path</span></span>

<span data-ttu-id="edd47-136">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="edd47-136">Specifies a path to one or more locations.</span></span> <span data-ttu-id="edd47-137">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="edd47-137">Wildcards are permitted.</span></span> <span data-ttu-id="edd47-138">De standaard locatie is de huidige map.</span><span class="sxs-lookup"><span data-stu-id="edd47-138">The default location is the current directory.</span></span>

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

### <span data-ttu-id="edd47-139">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="edd47-139">-Repository</span></span>

<span data-ttu-id="edd47-140">Hiermee geeft u de beschrijvende naam op van een opslag plaats die is geregistreerd door te worden uitgevoerd `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="edd47-140">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span>

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

### <span data-ttu-id="edd47-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="edd47-141">-WhatIf</span></span>

<span data-ttu-id="edd47-142">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="edd47-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="edd47-143">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="edd47-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="edd47-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="edd47-144">CommonParameters</span></span>

<span data-ttu-id="edd47-145">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="edd47-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="edd47-146">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="edd47-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="edd47-147">INVOER</span><span class="sxs-lookup"><span data-stu-id="edd47-147">INPUTS</span></span>

### <span data-ttu-id="edd47-148">System. String</span><span class="sxs-lookup"><span data-stu-id="edd47-148">System.String</span></span>

### <span data-ttu-id="edd47-149">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="edd47-149">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="edd47-150">UITVOER</span><span class="sxs-lookup"><span data-stu-id="edd47-150">OUTPUTS</span></span>

### <span data-ttu-id="edd47-151">System. object</span><span class="sxs-lookup"><span data-stu-id="edd47-151">System.Object</span></span>

## <span data-ttu-id="edd47-152">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="edd47-152">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="edd47-153">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="edd47-153">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="edd47-154">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="edd47-154">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="edd47-155">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="edd47-155">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="edd47-156">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="edd47-156">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="edd47-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="edd47-157">RELATED LINKS</span></span>

[<span data-ttu-id="edd47-158">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="edd47-158">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="edd47-159">Install-script</span><span class="sxs-lookup"><span data-stu-id="edd47-159">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="edd47-160">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="edd47-160">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="edd47-161">Save-Script</span><span class="sxs-lookup"><span data-stu-id="edd47-161">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="edd47-162">Update-script</span><span class="sxs-lookup"><span data-stu-id="edd47-162">Update-Script</span></span>](Update-Script.md)
