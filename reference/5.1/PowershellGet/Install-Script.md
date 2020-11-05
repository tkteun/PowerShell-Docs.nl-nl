---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/install-script?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Script
ms.openlocfilehash: ae3d0e3c9f70381884f3e12b19111e4c4eb47307
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250752"
---
# <span data-ttu-id="f4334-103">Install-Script</span><span class="sxs-lookup"><span data-stu-id="f4334-103">Install-Script</span></span>

## <span data-ttu-id="f4334-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f4334-104">SYNOPSIS</span></span>
<span data-ttu-id="f4334-105">Hiermee wordt een script geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f4334-105">Installs a script.</span></span>

## <span data-ttu-id="f4334-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f4334-106">SYNTAX</span></span>

### <span data-ttu-id="f4334-107">NameParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="f4334-107">NameParameterSet (Default)</span></span>

```
Install-Script [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]

```

### <span data-ttu-id="f4334-108">Input object</span><span class="sxs-lookup"><span data-stu-id="f4334-108">InputObject</span></span>

```
Install-Script [-InputObject] <PSObject[]> [-Scope <String>] [-NoPathUpdate] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f4334-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f4334-109">DESCRIPTION</span></span>

<span data-ttu-id="f4334-110">Met de `Install-Script` cmdlet wordt een script lading opgehaald uit een opslag plaats, wordt gecontroleerd of de payload een geldig Power shell-script is en wordt het script bestand gekopieerd naar een opgegeven installatie locatie.</span><span class="sxs-lookup"><span data-stu-id="f4334-110">The `Install-Script` cmdlet acquires a script payload from a repository, verifies that the payload is a valid PowerShell script, and copies the script file to a specified installation location.</span></span>

<span data-ttu-id="f4334-111">De standaard opslagplaatsen `Install-Script` kunnen worden geconfigureerd met behulp van `Register-PSRepository` de `Set-PSRepository` `Unregister-PSRepository` cmdlets,, en `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="f4334-111">The default repositories `Install-Script` operates against are configurable through the `Register-PSRepository`, `Set-PSRepository`, `Unregister-PSRepository`, and `Get-PSRepository` cmdlets.</span></span> <span data-ttu-id="f4334-112">Bij het werken met meerdere opslag plaatsen `Install-Script` installeert het eerste script dat overeenkomt met de opgegeven zoek criteria ( **name** , **MinimumVersion** of **MaximumVersion** ) van de eerste opslag plaats zonder enige fout.</span><span class="sxs-lookup"><span data-stu-id="f4334-112">When operating against multiple repositories, `Install-Script` installs the first script that matches the specified search criteria ( **Name** , **MinimumVersion** , or **MaximumVersion** ) from the first repository without any error.</span></span>

## <span data-ttu-id="f4334-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f4334-113">EXAMPLES</span></span>

### <span data-ttu-id="f4334-114">Voor beeld 1: een script zoeken en installeren</span><span class="sxs-lookup"><span data-stu-id="f4334-114">Example 1: Find a script and install it</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2"
Version    Name                           Type       Repository           Description
-------    ----                           ----       ----------           -----------
2.5        Required-Script2               Script     local1               Description for the Required-Script2 script

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
PS C:\> Get-Command -Name "Required-Script2"
CommandType     Name                      Version    Source
-----------     ----                      -------    ------
ExternalScript  Required-Script2.ps1      2.0       C:\Users\pattif\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1

PS C:\> Get-InstalledScript -Name "Required-Script2"
Version    Name                  Type     Repository           Description
-------    ----                  ----     ----------           -----------
2.5        Required-Script2      Script   local1               Description for the Required-Script2 script

PS C:\> Get-InstalledScript -Name "Required-Script2" | Format-List *
Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\pattif\Documents\WindowsPowerShell\Scripts
```

<span data-ttu-id="f4334-115">Met de eerste opdracht vindt u het script met de naam `Required-Script2` uit de Local1-opslag plaats en worden de resultaten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4334-115">The first command finds the script named `Required-Script2` from the Local1 repository and displays the results.</span></span>

<span data-ttu-id="f4334-116">Met de tweede opdracht wordt het `Required-Script2` script gevonden en vervolgens de pijplijn operator gebruikt om het door te geven aan de `Install-Script` cmdlet om het te installeren.</span><span class="sxs-lookup"><span data-stu-id="f4334-116">The second command finds the `Required-Script2` script, and then uses the pipeline operator to pass it to the `Install-Script` cmdlet to install it.</span></span>

<span data-ttu-id="f4334-117">De derde opdracht gebruikt de `Get-Command` cmdlet om op te halen `Required-Script2` . vervolgens worden de resultaten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4334-117">The third command uses the `Get-Command` cmdlet to get `Required-Script2`, and then displays the results.</span></span>

<span data-ttu-id="f4334-118">De vierde opdracht gebruikt de `Get-InstalledScript` cmdlet om de resultaten op te halen `Required-Script2` en weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f4334-118">The fourth command uses the `Get-InstalledScript` cmdlet to get `Required-Script2` and display the results.</span></span>

<span data-ttu-id="f4334-119">Met de vijfde opdracht wordt `Required-Script2` de pijplijn operator opgehaald en gebruikt om deze door te geven aan de `Format-List` cmdlet om de uitvoer op te maken.</span><span class="sxs-lookup"><span data-stu-id="f4334-119">The fifth command gets `Required-Script2` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="f4334-120">Voor beeld 2: een script met AllUsers-bereik installeren</span><span class="sxs-lookup"><span data-stu-id="f4334-120">Example 2: Install a script with AllUsers scope</span></span>

```
PS C:\> Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
PS C:\> Get-InstalledScript -Name "Required-Script3"
Version    Name                  Type       Repository    Description
-------    ----                  ----       ----------    -----------
2.5        Required-Script3      Script     local1        Description for the Required-Script3 script

PS C:\> Get-InstalledScript -Name "Required-Script3" | Format-List *
Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : pattif
CompanyName                :
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://pattif-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts
```

<span data-ttu-id="f4334-121">Met de eerste opdracht wordt het script geïnstalleerd met de naam `Required-Script3` en wordt het ALLUSERS-bereik toegewezen.</span><span class="sxs-lookup"><span data-stu-id="f4334-121">The first command installs the script named `Required-Script3` and assigns it AllUsers scope.</span></span>

<span data-ttu-id="f4334-122">Met de tweede opdracht wordt het geïnstalleerde script opgehaald `Required-Script3` en informatie hierover weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4334-122">The second command gets the installed script `Required-Script3` and displays information about it.</span></span>

<span data-ttu-id="f4334-123">Met de derde opdracht wordt `Required-Script3` de pijplijn operator opgehaald en gebruikt om deze door te geven aan de `Format-List` cmdlet om de uitvoer op te maken.</span><span class="sxs-lookup"><span data-stu-id="f4334-123">The third command gets `Required-Script3` and uses the pipeline operator to pass it to the `Format-List` cmdlet to format the output.</span></span>

### <span data-ttu-id="f4334-124">Voor beeld 3: een script en de bijbehorende afhankelijkheden installeren</span><span class="sxs-lookup"><span data-stu-id="f4334-124">Example 3: Install a script and its dependencies</span></span>

```
PS C:\> Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
2.0        Script-WithDependencies2    Script     local1        Description for the Script-WithDependencies2 script

PS C:\> Get-InstalledModule
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        RequiredModule1             Module     local1        RequiredModule1 module
2.5        RequiredModule2             Module     local1        RequiredModule2 module
2.5        RequiredModule3             Module     local1        RequiredModule3 module

PS C:\> Find-Script -Repository "Local1" -Name "Required-Script*"
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script

PS C:\> Install-Script -Repository "Local1" -Name "Required-Script*"
PS C:\> Get-InstalledScript
Version    Name                        Type       Repository    Description
-------    ----                        ----       ----------    -----------
2.5        Required-Script1            Script     local1        Description for the Required-Script1 script
2.5        Required-Script2            Script     local1        Description for the Required-Script2 script
2.5        Required-Script3            Script     local1        Description for the Required-Script3 script
```

<span data-ttu-id="f4334-125">Met de eerste opdracht vindt u het script met de naam `Script-WithDependencies2` en de bijbehorende afhankelijkheden in de Local1-opslag plaats en worden de resultaten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4334-125">The first command finds the script named `Script-WithDependencies2` and its dependencies in the Local1 repository and displays the results.</span></span>

<span data-ttu-id="f4334-126">De tweede opdracht wordt geïnstalleerd `Script-WithDependencies2` .</span><span class="sxs-lookup"><span data-stu-id="f4334-126">The second command installs `Script-WithDependencies2`.</span></span>

<span data-ttu-id="f4334-127">De derde opdracht gebruikt de `Get-InstalledScript` script-cmdlet om geïnstalleerde scripts op te halen en de resultaten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f4334-127">The third command uses the `Get-InstalledScript` script cmdlet to get installed scripts and display the results.</span></span>

<span data-ttu-id="f4334-128">De vierde opdracht gebruikt de `Get-InstalledModule` cmdlet om geïnstalleerde modules op te halen en de resultaten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f4334-128">The fourth command uses the `Get-InstalledModule` cmdlet to get installed modules and display the results.</span></span>

<span data-ttu-id="f4334-129">De vijfde opdracht gebruikt de `Find-Script` cmdlet om scripts te zoeken waarvan de naam begint met `Required-Script` en de resultaten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f4334-129">The fifth command uses the `Find-Script` cmdlet to find scripts where the name begins with `Required-Script` and display the results.</span></span>

<span data-ttu-id="f4334-130">De zesde opdracht installeert de scripts waarvan de naam begint met `Required-Script` in de Local1-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="f4334-130">The sixth command installs the scripts where the name begins with `Required-Script` in the Local1 repository.</span></span>

<span data-ttu-id="f4334-131">Met de laatste opdracht worden de geïnstalleerde scripts opgehaald en worden de resultaten weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f4334-131">The final command gets installed scripts and displays the results.</span></span>

## <span data-ttu-id="f4334-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f4334-132">PARAMETERS</span></span>

### <span data-ttu-id="f4334-133">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="f4334-133">-AcceptLicense</span></span>

<span data-ttu-id="f4334-134">Accepteer de gebruiksrecht overeenkomst automatisch tijdens de installatie als deze vereist is voor de module.</span><span class="sxs-lookup"><span data-stu-id="f4334-134">Automatically accept the license agreement during installation if the module requires it.</span></span>

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

### <span data-ttu-id="f4334-135">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="f4334-135">-AllowPrerelease</span></span>

<span data-ttu-id="f4334-136">Hiermee kunt u een script installeren dat is gemarkeerd als Prerelease.</span><span class="sxs-lookup"><span data-stu-id="f4334-136">Allows you to install a script marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4334-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f4334-137">-Confirm</span></span>

<span data-ttu-id="f4334-138">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f4334-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f4334-139">-Credential</span><span class="sxs-lookup"><span data-stu-id="f4334-139">-Credential</span></span>

<span data-ttu-id="f4334-140">Hiermee geeft u een gebruikers account op dat beschikt over rechten voor het installeren van een script voor een opgegeven pakket provider of bron.</span><span class="sxs-lookup"><span data-stu-id="f4334-140">Specifies a user account that has rights to install a script for a specified package provider or source.</span></span>

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

### <span data-ttu-id="f4334-141">-Force</span><span class="sxs-lookup"><span data-stu-id="f4334-141">-Force</span></span>

<span data-ttu-id="f4334-142">Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="f4334-142">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="f4334-143">-Input object</span><span class="sxs-lookup"><span data-stu-id="f4334-143">-InputObject</span></span>

<span data-ttu-id="f4334-144">Wordt gebruikt voor de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="f4334-144">Used for pipeline input.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f4334-145">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="f4334-145">-MaximumVersion</span></span>

<span data-ttu-id="f4334-146">Hiermee geeft u de maximum versie van één script op dat moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f4334-146">Specifies the maximum version of a single scripts to install.</span></span> <span data-ttu-id="f4334-147">U kunt deze para meter niet toevoegen als u probeert meerdere scripts te installeren.</span><span class="sxs-lookup"><span data-stu-id="f4334-147">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="f4334-148">De **MaximumVersion** en de **RequiredVersion** -para meters sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f4334-148">The **MaximumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f4334-149">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="f4334-149">-MinimumVersion</span></span>

<span data-ttu-id="f4334-150">Hiermee geeft u de minimum versie van één script op dat moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f4334-150">Specifies the minimum version of a single script to install.</span></span> <span data-ttu-id="f4334-151">U kunt deze para meter niet toevoegen als u probeert meerdere scripts te installeren.</span><span class="sxs-lookup"><span data-stu-id="f4334-151">You cannot add this parameter if you are attempting to install multiple scripts.</span></span> <span data-ttu-id="f4334-152">De **MinimumVersion** en de **RequiredVersion** -para meters sluiten elkaar wederzijds uit. u kunt niet beide para meters in dezelfde opdracht gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f4334-152">The **MinimumVersion** and the **RequiredVersion** parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f4334-153">-Name</span><span class="sxs-lookup"><span data-stu-id="f4334-153">-Name</span></span>

<span data-ttu-id="f4334-154">Hiermee geeft u een matrix met namen van te installeren scripts op.</span><span class="sxs-lookup"><span data-stu-id="f4334-154">Specifies an array of names of scripts to install.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f4334-155">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="f4334-155">-NoPathUpdate</span></span>

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

### <span data-ttu-id="f4334-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f4334-156">-PassThru</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4334-157">-Proxy</span><span class="sxs-lookup"><span data-stu-id="f4334-157">-Proxy</span></span>

<span data-ttu-id="f4334-158">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="f4334-158">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="f4334-159">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="f4334-159">-ProxyCredential</span></span>

<span data-ttu-id="f4334-160">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="f4334-160">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="f4334-161">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="f4334-161">-Repository</span></span>

<span data-ttu-id="f4334-162">Hiermee geeft u de beschrijvende naam op van een opslag plaats die is geregistreerd bij de `Register-PSRepository` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4334-162">Specifies the friendly name of a repository that has been registered with the `Register-PSRepository` cmdlet.</span></span> <span data-ttu-id="f4334-163">De standaard instelling is alle geregistreerde opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="f4334-163">The default is all registered repositories.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4334-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="f4334-164">-RequiredVersion</span></span>

<span data-ttu-id="f4334-165">Hiermee geeft u het exacte versie nummer van het script op dat moet worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f4334-165">Specifies the exact version number of the script to install.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f4334-166">-Bereik</span><span class="sxs-lookup"><span data-stu-id="f4334-166">-Scope</span></span>

<span data-ttu-id="f4334-167">Hiermee geeft u het installatie bereik van het script.</span><span class="sxs-lookup"><span data-stu-id="f4334-167">Specifies the installation scope of the script.</span></span>
<span data-ttu-id="f4334-168">Geldige waarden zijn: AllUsers en CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="f4334-168">Valid values are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="f4334-169">Met het AllUsers-bereik kunnen modules worden geïnstalleerd op een locatie die toegankelijk is voor alle gebruikers van de computer, dat wil zeggen `$env:ProgramFiles\WindowsPowerShell\Scripts` .</span><span class="sxs-lookup"><span data-stu-id="f4334-169">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, `$env:ProgramFiles\WindowsPowerShell\Scripts`.</span></span>

<span data-ttu-id="f4334-170">Met het bereik CurrentUser kunnen modules alleen worden geïnstalleerd op `$home\Documents\WindowsPowerShell\Scripts` , zodat de module alleen beschikbaar is voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f4334-170">The CurrentUser scope lets modules be installed only to `$home\Documents\WindowsPowerShell\Scripts`, so that the module is available only to the current user.</span></span>

<span data-ttu-id="f4334-171">Als er geen **bereik** is gedefinieerd, wordt de standaard waarde ingesteld op basis van de huidige sessie:</span><span class="sxs-lookup"><span data-stu-id="f4334-171">When no **Scope** is defined, the default will be set based on the current session:</span></span>

- <span data-ttu-id="f4334-172">Voor een Power shell-sessie met verhoogde bevoegdheid, wordt standaard de **Scope** ALLUSERS.</span><span class="sxs-lookup"><span data-stu-id="f4334-172">For an elevated PowerShell session, **Scope** defaults to AllUsers;</span></span>
- <span data-ttu-id="f4334-173">Voor niet-verhoogde Power shell-sessies in [PowerShellGet-versies 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) en hoger, is de **Scope** CurrentUser;</span><span class="sxs-lookup"><span data-stu-id="f4334-173">For non-elevated PowerShell sessions in [PowerShellGet versions 2.0.0](https://www.powershellgallery.com/packages/PowerShellGet) and above, **Scope** is CurrentUser;</span></span>
- <span data-ttu-id="f4334-174">Voor niet-verhoogde Power shell-sessies in PowerShellGet-versies 1.6.7 en eerder, is het **bereik** niet gedefinieerd en `Install-Module` mislukt.</span><span class="sxs-lookup"><span data-stu-id="f4334-174">For non-elevated PowerShell sessions in PowerShellGet versions 1.6.7 and earlier, **Scope** is undefined, and `Install-Module` fails.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f4334-175">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f4334-175">-WhatIf</span></span>

<span data-ttu-id="f4334-176">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f4334-176">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f4334-177">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f4334-177">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f4334-178">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f4334-178">CommonParameters</span></span>

<span data-ttu-id="f4334-179">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f4334-179">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f4334-180">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f4334-180">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f4334-181">INVOER</span><span class="sxs-lookup"><span data-stu-id="f4334-181">INPUTS</span></span>

### <span data-ttu-id="f4334-182">System.String[]</span><span class="sxs-lookup"><span data-stu-id="f4334-182">System.String[]</span></span>

### <span data-ttu-id="f4334-183">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="f4334-183">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="f4334-184">System. String</span><span class="sxs-lookup"><span data-stu-id="f4334-184">System.String</span></span>

### <span data-ttu-id="f4334-185">System. URI</span><span class="sxs-lookup"><span data-stu-id="f4334-185">System.Uri</span></span>

### <span data-ttu-id="f4334-186">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="f4334-186">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="f4334-187">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f4334-187">OUTPUTS</span></span>

### <span data-ttu-id="f4334-188">System. object</span><span class="sxs-lookup"><span data-stu-id="f4334-188">System.Object</span></span>
## <span data-ttu-id="f4334-189">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f4334-189">NOTES</span></span>

## <span data-ttu-id="f4334-190">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f4334-190">RELATED LINKS</span></span>

[<span data-ttu-id="f4334-191">Zoeken-script</span><span class="sxs-lookup"><span data-stu-id="f4334-191">Find-Script</span></span>](Find-Script.md)

[<span data-ttu-id="f4334-192">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="f4334-192">Publish-Script</span></span>](Publish-Script.md)

[<span data-ttu-id="f4334-193">Save-Script</span><span class="sxs-lookup"><span data-stu-id="f4334-193">Save-Script</span></span>](Save-Script.md)

[<span data-ttu-id="f4334-194">Uninstall-script</span><span class="sxs-lookup"><span data-stu-id="f4334-194">Uninstall-Script</span></span>](Uninstall-Script.md)

[<span data-ttu-id="f4334-195">Update-script</span><span class="sxs-lookup"><span data-stu-id="f4334-195">Update-Script</span></span>](Update-Script.md)