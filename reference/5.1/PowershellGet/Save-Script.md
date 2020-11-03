---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-script?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Script
ms.openlocfilehash: aefc9103b182ab232cb986a2ebb2b51f7cd09767
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250746"
---
# <span data-ttu-id="b707a-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="b707a-103">Save-Script</span></span>

## <span data-ttu-id="b707a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b707a-104">SYNOPSIS</span></span>
<span data-ttu-id="b707a-105">Slaat een script op.</span><span class="sxs-lookup"><span data-stu-id="b707a-105">Saves a script.</span></span>

## <span data-ttu-id="b707a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b707a-106">SYNTAX</span></span>

### <span data-ttu-id="b707a-107">NameAndPathParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="b707a-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b707a-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="b707a-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b707a-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="b707a-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b707a-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="b707a-110">InputObjectAndPathParameterSet</span></span>

```
Save-Script [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b707a-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b707a-111">DESCRIPTION</span></span>

<span data-ttu-id="b707a-112">Met de `Save-Script` cmdlet wordt het opgegeven script opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b707a-112">The `Save-Script` cmdlet saves the specified script.</span></span>

## <span data-ttu-id="b707a-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b707a-113">EXAMPLES</span></span>

### <span data-ttu-id="b707a-114">Voor beeld 1: een script opslaan en de meta gegevens van het script valideren</span><span class="sxs-lookup"><span data-stu-id="b707a-114">Example 1: Save a script and validate the script's metadata</span></span>

<span data-ttu-id="b707a-115">In dit voor beeld wordt een script uit een opslag plaats opgeslagen op de lokale computer en worden de meta gegevens van het script gevalideerd.</span><span class="sxs-lookup"><span data-stu-id="b707a-115">In this example, a script from a repository is saved to the local computer and the script's metadata is validated.</span></span>

```powershell
Save-Script -Name Install-VSCode -Repository PSGallery -Path C:\Test\Scripts
Test-ScriptFileInfo -Path C:\Test\Scripts\Install-VSCode.ps1
```

```Output
Version   Name              Author      Description
-------   ----              ------      -----------
1.3       Install-VSCode    Microsoft   This script can be used to easily install Visual Studio Code
```

<span data-ttu-id="b707a-116">`Save-Script` maakt gebruik van de para meter **name** om de naam van het script op te geven.</span><span class="sxs-lookup"><span data-stu-id="b707a-116">`Save-Script` uses the **Name** parameter to specify the script's name.</span></span> <span data-ttu-id="b707a-117">De **opslagplaats** parameter geeft aan waar het script moet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="b707a-117">The **Repository** parameter specifies where to find the script.</span></span> <span data-ttu-id="b707a-118">Het script wordt opgeslagen op de locatie die is opgegeven door de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="b707a-118">The script is saved in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="b707a-119">`Test-ScriptFileInfo` Hiermee geeft u het **pad** en valideert u de meta gegevens van het script.</span><span class="sxs-lookup"><span data-stu-id="b707a-119">`Test-ScriptFileInfo` specifies the **Path** and validates the script's metadata.</span></span>

## <span data-ttu-id="b707a-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b707a-120">PARAMETERS</span></span>

### <span data-ttu-id="b707a-121">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="b707a-121">-AcceptLicense</span></span>

<span data-ttu-id="b707a-122">Accepteer de gebruiksrecht overeenkomst automatisch als deze vereist is voor het script.</span><span class="sxs-lookup"><span data-stu-id="b707a-122">Automatically accept the license agreement if the script requires it.</span></span>

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

### <span data-ttu-id="b707a-123">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="b707a-123">-AllowPrerelease</span></span>

<span data-ttu-id="b707a-124">Hiermee kunt u een script opslaan dat is gemarkeerd als Prerelease.</span><span class="sxs-lookup"><span data-stu-id="b707a-124">Allows you to save a script marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b707a-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b707a-125">-Confirm</span></span>

<span data-ttu-id="b707a-126">Vraagt u om bevestiging voordat deze wordt uitgevoerd `Save-Script` .</span><span class="sxs-lookup"><span data-stu-id="b707a-126">Prompts you for confirmation before running `Save-Script`.</span></span>

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

### <span data-ttu-id="b707a-127">-Credential</span><span class="sxs-lookup"><span data-stu-id="b707a-127">-Credential</span></span>

<span data-ttu-id="b707a-128">Hiermee geeft u een gebruikers account op dat gemachtigd is om een script op te slaan.</span><span class="sxs-lookup"><span data-stu-id="b707a-128">Specifies a user account that has permission to save a script.</span></span>

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

### <span data-ttu-id="b707a-129">-Force</span><span class="sxs-lookup"><span data-stu-id="b707a-129">-Force</span></span>

<span data-ttu-id="b707a-130">Er wordt geforceerd `Save-Script` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="b707a-130">Forces `Save-Script` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="b707a-131">-Input object</span><span class="sxs-lookup"><span data-stu-id="b707a-131">-InputObject</span></span>

<span data-ttu-id="b707a-132">Hiermee wordt een **PSRepositoryItemInfo** -object geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="b707a-132">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="b707a-133">Bijvoorbeeld: uitvoer `Find-Script` naar een variabele en de variabele gebruiken als het argument **input object** .</span><span class="sxs-lookup"><span data-stu-id="b707a-133">For example, output `Find-Script` to a variable and use that variable as the **InputObject** argument.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObjectAndLiteralPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b707a-134">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b707a-134">-LiteralPath</span></span>

<span data-ttu-id="b707a-135">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="b707a-135">Specifies a path to one or more locations.</span></span> <span data-ttu-id="b707a-136">De waarde van de para meter **LiteralPath** wordt exact als opgegeven gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b707a-136">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="b707a-137">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="b707a-137">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b707a-138">Als het pad escape tekens bevat, plaatst u het pad tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="b707a-138">If the path includes escape characters, enclose the path within single quotation marks.</span></span> <span data-ttu-id="b707a-139">Power shell interpreteert niet alle tekens tussen enkele aanhalings tekens als escape-reeksen.</span><span class="sxs-lookup"><span data-stu-id="b707a-139">PowerShell doesn't interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndLiteralPathParameterSet, InputObjectAndLiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b707a-140">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b707a-140">-MaximumVersion</span></span>

<span data-ttu-id="b707a-141">Hiermee geeft u het maximum of de nieuwste versie van het script op dat moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b707a-141">Specifies the maximum, or newest version of the script to save.</span></span> <span data-ttu-id="b707a-142">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="b707a-142">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b707a-143">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b707a-143">-MinimumVersion</span></span>

<span data-ttu-id="b707a-144">Hiermee geeft u de minimale versie van een script op dat moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b707a-144">Specifies the minimum version of a script to save.</span></span> <span data-ttu-id="b707a-145">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="b707a-145">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b707a-146">-Name</span><span class="sxs-lookup"><span data-stu-id="b707a-146">-Name</span></span>

<span data-ttu-id="b707a-147">Hiermee geeft u een matrix met script namen op die moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b707a-147">Specifies an array of script names to save.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b707a-148">-Path</span><span class="sxs-lookup"><span data-stu-id="b707a-148">-Path</span></span>

<span data-ttu-id="b707a-149">Hiermee geeft u de locatie op de lokale computer op waarop een opgeslagen module moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b707a-149">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="b707a-150">Accepteert joker tekens.</span><span class="sxs-lookup"><span data-stu-id="b707a-150">Accepts wildcard characters.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, InputObjectAndPathParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="b707a-151">-Proxy</span><span class="sxs-lookup"><span data-stu-id="b707a-151">-Proxy</span></span>

<span data-ttu-id="b707a-152">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met een Internet bron.</span><span class="sxs-lookup"><span data-stu-id="b707a-152">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="b707a-153">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="b707a-153">-ProxyCredential</span></span>

<span data-ttu-id="b707a-154">Hiermee geeft u een gebruikers account op dat gemachtigd is om de proxy server te gebruiken die is opgegeven met de **proxy** para meter.</span><span class="sxs-lookup"><span data-stu-id="b707a-154">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="b707a-155">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="b707a-155">-Repository</span></span>

<span data-ttu-id="b707a-156">Hiermee geeft u de beschrijvende naam op van een opslag plaats die is geregistreerd door te worden uitgevoerd `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="b707a-156">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="b707a-157">Gebruik `Get-PSRepository` om geregistreerde opslag plaatsen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b707a-157">Use `Get-PSRepository` to display registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b707a-158">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b707a-158">-RequiredVersion</span></span>

<span data-ttu-id="b707a-159">Hiermee geeft u het exacte versie nummer van het script op dat moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b707a-159">Specifies the exact version number of the script to save.</span></span>

```yaml
Type: System.String
Parameter Sets: NameAndPathParameterSet, NameAndLiteralPathParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b707a-160">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b707a-160">-WhatIf</span></span>

<span data-ttu-id="b707a-161">Hier wordt weer gegeven wat er gebeurt als er `Save-Script` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b707a-161">Shows what would happen if `Save-Script` runs.</span></span> <span data-ttu-id="b707a-162">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b707a-162">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="b707a-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b707a-163">CommonParameters</span></span>

<span data-ttu-id="b707a-164">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b707a-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b707a-165">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b707a-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b707a-166">INVOER</span><span class="sxs-lookup"><span data-stu-id="b707a-166">INPUTS</span></span>

## <span data-ttu-id="b707a-167">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b707a-167">OUTPUTS</span></span>

## <span data-ttu-id="b707a-168">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b707a-168">NOTES</span></span>

## <span data-ttu-id="b707a-169">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b707a-169">RELATED LINKS</span></span>

[<span data-ttu-id="b707a-170">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="b707a-170">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="b707a-171">Install-script</span><span class="sxs-lookup"><span data-stu-id="b707a-171">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="b707a-172">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="b707a-172">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="b707a-173">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="b707a-173">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)

[<span data-ttu-id="b707a-174">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="b707a-174">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="b707a-175">Update-script</span><span class="sxs-lookup"><span data-stu-id="b707a-175">Update-Script</span></span>](Update-Script.md)
