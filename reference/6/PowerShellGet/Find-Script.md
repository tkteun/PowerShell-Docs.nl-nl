---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/find-script?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Script
ms.openlocfilehash: 6d38f6f4b2b44063c5bf15295fecb90d8fea3d4c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250942"
---
# <span data-ttu-id="df1bc-103">Find-Script</span><span class="sxs-lookup"><span data-stu-id="df1bc-103">Find-Script</span></span>

## <span data-ttu-id="df1bc-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="df1bc-104">SYNOPSIS</span></span>
<span data-ttu-id="df1bc-105">Zoekt naar een script.</span><span class="sxs-lookup"><span data-stu-id="df1bc-105">Finds a script.</span></span>

## <span data-ttu-id="df1bc-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="df1bc-106">SYNTAX</span></span>

```
Find-Script [[-Name] <String[]>] [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-AllVersions] [-IncludeDependencies] [-Filter <String>] [-Tag <String[]>]
 [-Includes <String[]>] [-Command <String[]>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [-Credential <PSCredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="df1bc-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="df1bc-107">DESCRIPTION</span></span>

<span data-ttu-id="df1bc-108">Met de cmdlet **Find-script** vindt u een opgegeven script in de geregistreerde opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="df1bc-108">The **Find-Script** cmdlet finds a specified script in registered repositories.</span></span>

## <span data-ttu-id="df1bc-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="df1bc-109">EXAMPLES</span></span>

### <span data-ttu-id="df1bc-110">Voor beeld 1: alle beschik bare scripts zoeken</span><span class="sxs-lookup"><span data-stu-id="df1bc-110">Example 1: Find all available scripts</span></span>

```
PS C:\> Find-Script
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
2.5        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
2.5        Fabrikam-ServerScript               Script     LocalRepo1           Description for the Fabrikam-ServerScript script
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        Script-WithDependencies2            Script     LocalRepo1           Description for the Script-WithDependencies2 script
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
2.1        Test-Script1                        Script     LocalRepo1           Test-Script1 Script example
2.0        Test-Script2                        Script     LocalRepo1           Test-Script2 Script example
1.0        TestRunbook                         Script     LocalRepo1           Contoso Script example
```

<span data-ttu-id="df1bc-111">Met deze opdracht vindt u alle beschik bare scripts.</span><span class="sxs-lookup"><span data-stu-id="df1bc-111">This command finds all available scripts.</span></span>

### <span data-ttu-id="df1bc-112">Voor beeld 2: een script op naam zoeken</span><span class="sxs-lookup"><span data-stu-id="df1bc-112">Example 2: Find a script by name</span></span>

```
PS C:\> Find-Script -Name "Start-WFContosoServer"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.0        Start-WFContosoServer               Script     LocalRepo1           Start-WFContosoServer Script example
```

<span data-ttu-id="df1bc-113">Met deze opdracht vindt u het script met de naam start-WFContosoServer.</span><span class="sxs-lookup"><span data-stu-id="df1bc-113">This command find the script named Start-WFContosoServer.</span></span>

### <span data-ttu-id="df1bc-114">Voor beeld 3: een script op naam, vereiste versie en uit een opgegeven opslag plaats zoeken</span><span class="sxs-lookup"><span data-stu-id="df1bc-114">Example 3: Find a script by name, required version, and from a specified repository</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo01"
```

<span data-ttu-id="df1bc-115">Met deze opdracht vindt u een script met de naam en de vereiste versie in de LocalRepo01-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="df1bc-115">This command finds a script by name and required version in the LocalRepo01 repository.</span></span>

### <span data-ttu-id="df1bc-116">Voor beeld 4: een script zoeken en de uitvoer als een lijst opmaken</span><span class="sxs-lookup"><span data-stu-id="df1bc-116">Example 4: Find a script and format the output as a list</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -RequiredVersion 2.0 -Repository "LocalRepo1" | Format-List * -Force
Name                       : Required-Script2
Version                    : 2.0
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/14/2015 2:37:01 PM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {, Tag1, Tag2, Tag-Required-Script2-2.0...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : C:\MyLocalRepo
Repository                 : LocalRepo01
PackageManagementProvider  : NuGet
```

<span data-ttu-id="df1bc-117">Met deze opdracht vindt u Required-Script2 in de LocalRepo1-opslag plaats en geeft u het resulterende **PSRepositoryItemInfo** -object door aan de Format-List-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="df1bc-117">This command finds Required-Script2 in the LocalRepo1 repository, and then passes the resulting **PSRepositoryItemInfo** object to the Format-List cmdlet.</span></span>

### <span data-ttu-id="df1bc-118">Voor beeld 5: een script in het opgegeven versie bereik zoeken</span><span class="sxs-lookup"><span data-stu-id="df1bc-118">Example 5: Find a script in the specified version range</span></span>

```
PS C:\> Find-Script -Name "Required-Script2" -MinimumVersion 2.1 -MaximumVersion 2.5 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="df1bc-119">Met deze opdracht vindt u alle versies van RequiredScript2 tussen versies 2,1 en 2,5 in de LocalRepo1-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="df1bc-119">This command finds all versions of RequiredScript2 between versions 2.1 and 2.5 in the LocalRepo1 respository.</span></span>

### <span data-ttu-id="df1bc-120">Voor beeld 6: alle versies van een script zoeken</span><span class="sxs-lookup"><span data-stu-id="df1bc-120">Example 6: Find all versions of a script</span></span>

```
PS C:\> Find-Script -Name "Required-Script02" -AllVersions
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
1.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.0        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="df1bc-121">Met deze opdracht vindt u alle versies van het vereiste-Script02.</span><span class="sxs-lookup"><span data-stu-id="df1bc-121">This command finds all versions of Required-Script02.</span></span>

### <span data-ttu-id="df1bc-122">Voor beeld 7: een script en de bijbehorende afhankelijkheden zoeken</span><span class="sxs-lookup"><span data-stu-id="df1bc-122">Example 7: Find a script and its dependencies</span></span>

```
PS C:\> Find-Script -Name "Script-WithDependencies1" -IncludeDependencies -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Script-WithDependencies1            Script     LocalRepo1           Description for the Script-WithDependencies1 script
2.0        RequiredModule3                     Script     LocalRepo1           RequiredModule3 module
2.5        Required-Script1                    Script     LocalRepo1           Description for the Required-Script1 script
2.5        Required-Script2                    Script     LocalRepo1           Description for the Required-Script2 script
```

<span data-ttu-id="df1bc-123">Met deze opdracht vindt u een script en de bijbehorende afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="df1bc-123">This command finds a script and its dependencies.</span></span>

### <span data-ttu-id="df1bc-124">Voor beeld 8: scripts met de opgegeven tag zoeken</span><span class="sxs-lookup"><span data-stu-id="df1bc-124">Example 8: Find scripts with the specified tag</span></span>

```
PS C:\> Find-Script -Tag "Tag1" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.0        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
```

<span data-ttu-id="df1bc-125">Met deze opdracht vindt u scripts met de tag Tag1 in de LocalRepo1-opslag plaats</span><span class="sxs-lookup"><span data-stu-id="df1bc-125">This command finds scripts that have the tag Tag1 in the LocalRepo1 repository</span></span>

### <span data-ttu-id="df1bc-126">Voor beeld 9: scripts zoeken met de opgegeven opdracht naam</span><span class="sxs-lookup"><span data-stu-id="df1bc-126">Example 9: Find scripts with specified command name</span></span>

```
PS C:\> Find-Script -Command Test-FunctionFromScript_Required-Script3 -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script3                    Script     LocalRepo1           Description for the Required-Script3 script
```

<span data-ttu-id="df1bc-127">Met deze opdracht vindt u een script met de opgegeven opdracht naam.</span><span class="sxs-lookup"><span data-stu-id="df1bc-127">This command finds a script that contains the specified command name.</span></span>

### <span data-ttu-id="df1bc-128">Voor beeld 10: scripts zoeken met werk stromen</span><span class="sxs-lookup"><span data-stu-id="df1bc-128">Example 10: Find scripts with workflows</span></span>

```
PS C:\> Find-Script -Includes "Workflow" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Fabrikam-ClientScript               Script     LocalRepo1           Description for the Fabrikam-ClientScript script
1.0        Fabrikam-Script                     Script     LocalRepo1           Description for the Fabrikam-Script script
```

<span data-ttu-id="df1bc-129">Met deze opdracht vindt u de werk stroom scripts in de LocalRepo1-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="df1bc-129">This command finds workflow scripts in the LocalRepo1 repository.</span></span>

### <span data-ttu-id="df1bc-130">Voor beeld 11: scripts zoeken met Joker tekens</span><span class="sxs-lookup"><span data-stu-id="df1bc-130">Example 11: Find scripts using wildcards</span></span>

```
PS C:\> Find-Script -Name "Required-Script*" -Repository "LocalRepo1"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="df1bc-131">Met deze opdracht wordt het Joker teken (\*) gebruikt voor het zoeken van scripts die met het vereiste script beginnen.</span><span class="sxs-lookup"><span data-stu-id="df1bc-131">This command uses the wildcard character (\*) to find scripts that begin with Required-Script.</span></span>

## <span data-ttu-id="df1bc-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="df1bc-132">PARAMETERS</span></span>

### <span data-ttu-id="df1bc-133">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="df1bc-133">-AllowPrerelease</span></span>

<span data-ttu-id="df1bc-134">Bevat de resultaten scripts die als Prerelease zijn gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="df1bc-134">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="df1bc-135">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="df1bc-135">-AllVersions</span></span>

<span data-ttu-id="df1bc-136">Geeft aan dat met deze bewerking alle script versies worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="df1bc-136">Indicates that this operation finds all script versions.</span></span>

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

### <span data-ttu-id="df1bc-137">-Opdracht</span><span class="sxs-lookup"><span data-stu-id="df1bc-137">-Command</span></span>

<span data-ttu-id="df1bc-138">Hiermee geeft u een matrix met opdrachten op die moeten worden gevonden in scripts.</span><span class="sxs-lookup"><span data-stu-id="df1bc-138">Specifies an array of commands to find in scripts.</span></span>
<span data-ttu-id="df1bc-139">Een opdracht kan een functie of werk stroom zijn.</span><span class="sxs-lookup"><span data-stu-id="df1bc-139">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="df1bc-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="df1bc-140">-Credential</span></span>

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

### <span data-ttu-id="df1bc-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="df1bc-141">-Filter</span></span>

<span data-ttu-id="df1bc-142">Zoekt scripts op basis van de Package Management-specifieke zoek syntaxis.</span><span class="sxs-lookup"><span data-stu-id="df1bc-142">Finds scripts based on the PackageManagement provider-specific search syntax.</span></span>

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

### <span data-ttu-id="df1bc-143">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="df1bc-143">-IncludeDependencies</span></span>

<span data-ttu-id="df1bc-144">Geeft aan dat met deze bewerking alle scripts worden opgehaald die afhankelijk zijn van het script dat is opgegeven in de para meter *name* .</span><span class="sxs-lookup"><span data-stu-id="df1bc-144">Indicates that this operation gets all scripts that are dependent upon the script specified in the *Name* parameter.</span></span>

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

### <span data-ttu-id="df1bc-145">-Bevat</span><span class="sxs-lookup"><span data-stu-id="df1bc-145">-Includes</span></span>

<span data-ttu-id="df1bc-146">Hiermee wordt het type script opgegeven dat moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="df1bc-146">Specifies type of script to get.</span></span>
<span data-ttu-id="df1bc-147">De acceptabele waarden voor deze para meter zijn: functie, werk stroom.</span><span class="sxs-lookup"><span data-stu-id="df1bc-147">The acceptable values for this parameter are: Function, Workflow.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Function, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="df1bc-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="df1bc-148">-MaximumVersion</span></span>

<span data-ttu-id="df1bc-149">Hiermee geeft u het maximum of nieuwste versie van het script op dat moet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="df1bc-149">Specifies the maximum, or newest, version of the script to find.</span></span>
<span data-ttu-id="df1bc-150">De para meters *MaximumVersion* en *RequiredVersion* sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="df1bc-150">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="df1bc-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="df1bc-151">-MinimumVersion</span></span>

<span data-ttu-id="df1bc-152">Hiermee geeft u de minimale versie van het script op dat moet worden gezocht.</span><span class="sxs-lookup"><span data-stu-id="df1bc-152">Specifies the minimum version of the script to find.</span></span>
<span data-ttu-id="df1bc-153">De para meters *MinimumVersion* en *RequiredVersion* sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="df1bc-153">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="df1bc-154">-Name</span><span class="sxs-lookup"><span data-stu-id="df1bc-154">-Name</span></span>

<span data-ttu-id="df1bc-155">Hiermee geeft u een matrix met namen van scripts op die u wilt zoeken.</span><span class="sxs-lookup"><span data-stu-id="df1bc-155">Specifies an array of names of scripts to find.</span></span>

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

### <span data-ttu-id="df1bc-156">-Proxy</span><span class="sxs-lookup"><span data-stu-id="df1bc-156">-Proxy</span></span>

<span data-ttu-id="df1bc-157">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="df1bc-157">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="df1bc-158">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="df1bc-158">-ProxyCredential</span></span>

<span data-ttu-id="df1bc-159">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="df1bc-159">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="df1bc-160">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="df1bc-160">-Repository</span></span>

<span data-ttu-id="df1bc-161">Hiermee geeft u de beschrijvende naam op van een opslag plaats die is geregistreerd door REGI ster-PSRepository uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="df1bc-161">Specifies the friendly name of a repository that has been registered by running Register-PSRepository.</span></span>

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

### <span data-ttu-id="df1bc-162">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="df1bc-162">-RequiredVersion</span></span>

<span data-ttu-id="df1bc-163">Hiermee geeft u het exacte versie nummer van het script op dat moet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="df1bc-163">Specifies the exact version number of the script to find.</span></span>

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

### <span data-ttu-id="df1bc-164">-Tag</span><span class="sxs-lookup"><span data-stu-id="df1bc-164">-Tag</span></span>

<span data-ttu-id="df1bc-165">Hiermee geeft u een matrix met tags op.</span><span class="sxs-lookup"><span data-stu-id="df1bc-165">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="df1bc-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="df1bc-166">CommonParameters</span></span>

<span data-ttu-id="df1bc-167">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="df1bc-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="df1bc-168">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="df1bc-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="df1bc-169">INVOER</span><span class="sxs-lookup"><span data-stu-id="df1bc-169">INPUTS</span></span>

### <span data-ttu-id="df1bc-170">System.String[]</span><span class="sxs-lookup"><span data-stu-id="df1bc-170">System.String[]</span></span>

### <span data-ttu-id="df1bc-171">System. String</span><span class="sxs-lookup"><span data-stu-id="df1bc-171">System.String</span></span>

### <span data-ttu-id="df1bc-172">System. URI</span><span class="sxs-lookup"><span data-stu-id="df1bc-172">System.Uri</span></span>

### <span data-ttu-id="df1bc-173">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="df1bc-173">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="df1bc-174">UITVOER</span><span class="sxs-lookup"><span data-stu-id="df1bc-174">OUTPUTS</span></span>

### <span data-ttu-id="df1bc-175">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="df1bc-175">PSRepositoryItemInfo</span></span>

## <span data-ttu-id="df1bc-176">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="df1bc-176">NOTES</span></span>

## <span data-ttu-id="df1bc-177">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="df1bc-177">RELATED LINKS</span></span>

[<span data-ttu-id="df1bc-178">Install-script</span><span class="sxs-lookup"><span data-stu-id="df1bc-178">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="df1bc-179">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="df1bc-179">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="df1bc-180">Save-Script</span><span class="sxs-lookup"><span data-stu-id="df1bc-180">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="df1bc-181">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="df1bc-181">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="df1bc-182">Update-script</span><span class="sxs-lookup"><span data-stu-id="df1bc-182">Update-Script</span></span>](Update-Script.md)
