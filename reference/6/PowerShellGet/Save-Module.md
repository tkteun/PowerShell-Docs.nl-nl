---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: 1cd9c146017869ce8c6c4f848c6e559aefaf1348
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250922"
---
# <span data-ttu-id="17c49-103">Save-Module</span><span class="sxs-lookup"><span data-stu-id="17c49-103">Save-Module</span></span>

## <span data-ttu-id="17c49-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="17c49-104">SYNOPSIS</span></span>
<span data-ttu-id="17c49-105">Slaat een module en de bijbehorende afhankelijkheden op de lokale computer op, maar installeert de module niet.</span><span class="sxs-lookup"><span data-stu-id="17c49-105">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

## <span data-ttu-id="17c49-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="17c49-106">SYNTAX</span></span>

### <span data-ttu-id="17c49-107">NameAndPathParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="17c49-107">NameAndPathParameterSet (Default)</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="17c49-108">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="17c49-108">NameAndLiteralPathParameterSet</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="17c49-109">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="17c49-109">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="17c49-110">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="17c49-110">InputObjectAndPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="17c49-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="17c49-111">DESCRIPTION</span></span>

<span data-ttu-id="17c49-112">De `Save-Module` cmdlet downloadt een module en eventuele afhankelijkheden van een geregistreerde opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="17c49-112">The `Save-Module` cmdlet downloads a module and any dependencies from a registered repository.</span></span>
<span data-ttu-id="17c49-113">`Save-Module` Hiermee wordt de meest recente versie van een module gedownload en opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-113">`Save-Module` downloads and saves the most current version of a module.</span></span> <span data-ttu-id="17c49-114">De bestanden worden opgeslagen in een opgegeven pad op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="17c49-114">The files are saved to a specified path on the local computer.</span></span> <span data-ttu-id="17c49-115">De module is niet geïnstalleerd, maar de inhoud is beschikbaar voor inspectie door een beheerder.</span><span class="sxs-lookup"><span data-stu-id="17c49-115">The module isn't installed, but the contents are available for inspection by an administrator.</span></span> <span data-ttu-id="17c49-116">De opgeslagen module kan vervolgens worden gekopieerd naar de juiste `$env:PSModulePath` locatie van de offline machine.</span><span class="sxs-lookup"><span data-stu-id="17c49-116">The saved module can then be copied into the appropriate `$env:PSModulePath` location of the offline machine.</span></span>

<span data-ttu-id="17c49-117">`Get-PSRepository` Hiermee worden de geregistreerde opslag plaatsen van de lokale computer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="17c49-117">`Get-PSRepository` displays the local computer's registered repositories.</span></span> <span data-ttu-id="17c49-118">U kunt de `Find-Module` cmdlet gebruiken om te zoeken in geregistreerde opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="17c49-118">You can use the `Find-Module` cmdlet to search registered repositories.</span></span>

## <span data-ttu-id="17c49-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="17c49-119">EXAMPLES</span></span>

### <span data-ttu-id="17c49-120">Voor beeld 1: een module opslaan</span><span class="sxs-lookup"><span data-stu-id="17c49-120">Example 1: Save a module</span></span>

<span data-ttu-id="17c49-121">In dit voor beeld worden een module en de bijbehorende afhankelijkheden opgeslagen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="17c49-121">In this example, a module and its dependencies are saved to the local computer.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery
Get-ChildItem -Path C:\Test\Modules
```

```Output
    Directory: C:\Test\Modules

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:31                PackageManagement
d-----         7/1/2019     13:31                PowerShellGet
```

<span data-ttu-id="17c49-122">`Save-Module` maakt gebruik van de para meter **name** om de module **PowerShellGet** op te geven.</span><span class="sxs-lookup"><span data-stu-id="17c49-122">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="17c49-123">De para meter **Path** geeft aan waar de gedownloade module moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-123">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="17c49-124">De **opslagplaats** parameter geeft een geregistreerde opslag plaats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="17c49-124">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="17c49-125">Wanneer het downloaden is voltooid, `Get-ChildItem` wordt de inhoud weer gegeven van het **pad** waar de bestanden zijn opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-125">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="17c49-126">Voor beeld 2: een specifieke versie van een module opslaan</span><span class="sxs-lookup"><span data-stu-id="17c49-126">Example 2: Save a specific version of a module</span></span>

<span data-ttu-id="17c49-127">In dit voor beeld ziet u hoe u een para meter zoals **MaximumVersion** of **RequiredVersion** gebruikt om een module versie op te geven.</span><span class="sxs-lookup"><span data-stu-id="17c49-127">This example shows how to use a parameter such as **MaximumVersion** , or **RequiredVersion** to specify a module version.</span></span>

```powershell
Save-Module -Name PowerShellGet -Path C:\Test\Modules -Repository PSGallery -MaximumVersion 2.1.0
Get-ChildItem -Path C:\Test\Modules\PowerShellGet\
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     13:40                2.1.0
```

<span data-ttu-id="17c49-128">`Save-Module` maakt gebruik van de para meter **name** om de module **PowerShellGet** op te geven.</span><span class="sxs-lookup"><span data-stu-id="17c49-128">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="17c49-129">De para meter **Path** geeft aan waar de gedownloade module moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-129">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="17c49-130">De **opslagplaats** parameter geeft een geregistreerde opslag plaats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="17c49-130">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="17c49-131">**MaximumVersion** geeft aan dat versie **2.1.0** wordt gedownload en opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-131">**MaximumVersion** specifies that version **2.1.0** is downloaded and saved.</span></span> <span data-ttu-id="17c49-132">Wanneer het downloaden is voltooid, `Get-ChildItem` wordt de inhoud weer gegeven van het **pad** waar de bestanden zijn opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-132">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="17c49-133">Voor beeld 3: een specifieke versie van een module zoeken en opslaan</span><span class="sxs-lookup"><span data-stu-id="17c49-133">Example 3: Find and save a specific version of a module</span></span>

<span data-ttu-id="17c49-134">In dit voor beeld wordt een vereiste module versie gevonden in de opslag plaats en opgeslagen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="17c49-134">In this example, a required module version is found in the repository and saved to the local computer.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery -RequiredVersion 1.6.5 |
  Save-Module -Path C:\Test\Modules
Get-ChildItem -Path C:\Test\Modules\PowerShellGet
```

```Output
    Directory: C:\Test\Modules\PowerShellGet

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         7/1/2019     14:04                1.6.5
```

<span data-ttu-id="17c49-135">`Find-Module` maakt gebruik van de para meter **name** om de module **PowerShellGet** op te geven.</span><span class="sxs-lookup"><span data-stu-id="17c49-135">`Find-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="17c49-136">De **opslagplaats** parameter geeft een geregistreerde opslag plaats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="17c49-136">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="17c49-137">**RequiredVersion** geeft versie **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="17c49-137">**RequiredVersion** specifies version **1.6.5**.</span></span>

<span data-ttu-id="17c49-138">Het object wordt naar de pijp lijn verzonden `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="17c49-138">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="17c49-139">De para meter **Path** geeft aan waar de gedownloade module moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-139">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="17c49-140">Wanneer het downloaden is voltooid, `Get-ChildItem` wordt de inhoud weer gegeven van het **pad** waar de bestanden zijn opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-140">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

## <span data-ttu-id="17c49-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="17c49-141">PARAMETERS</span></span>

### <span data-ttu-id="17c49-142">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="17c49-142">-AcceptLicense</span></span>

<span data-ttu-id="17c49-143">Accepteer de gebruiksrecht overeenkomst automatisch als het pakket deze vereist.</span><span class="sxs-lookup"><span data-stu-id="17c49-143">Automatically accept the license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="17c49-144">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="17c49-144">-AllowPrerelease</span></span>

<span data-ttu-id="17c49-145">Hiermee kunt u een module opslaan die is gemarkeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="17c49-145">Allows you to save a module marked as a prerelease.</span></span>

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

### <span data-ttu-id="17c49-146">-Confirm</span><span class="sxs-lookup"><span data-stu-id="17c49-146">-Confirm</span></span>

<span data-ttu-id="17c49-147">Vraagt u om bevestiging voordat de wordt uitgevoerd `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="17c49-147">Prompts you for confirmation before running the `Save-Module`.</span></span>

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

### <span data-ttu-id="17c49-148">-Credential</span><span class="sxs-lookup"><span data-stu-id="17c49-148">-Credential</span></span>

<span data-ttu-id="17c49-149">Hiermee geeft u een gebruikers account op dat rechten heeft om een module op te slaan.</span><span class="sxs-lookup"><span data-stu-id="17c49-149">Specifies a user account that has rights to save a module.</span></span>

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

### <span data-ttu-id="17c49-150">-Force</span><span class="sxs-lookup"><span data-stu-id="17c49-150">-Force</span></span>

<span data-ttu-id="17c49-151">Er wordt geforceerd `Save-Module` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="17c49-151">Forces `Save-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="17c49-152">-Input object</span><span class="sxs-lookup"><span data-stu-id="17c49-152">-InputObject</span></span>

<span data-ttu-id="17c49-153">Hiermee wordt een **PSRepositoryItemInfo** -object geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="17c49-153">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="17c49-154">Bijvoorbeeld: uitvoer `Find-Module` naar een variabele en de variabele gebruiken als het argument **input object** .</span><span class="sxs-lookup"><span data-stu-id="17c49-154">For example, output `Find-Module` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="17c49-155">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="17c49-155">-LiteralPath</span></span>

<span data-ttu-id="17c49-156">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="17c49-156">Specifies a path to one or more locations.</span></span> <span data-ttu-id="17c49-157">De waarde van de para meter **LiteralPath** wordt exact als opgegeven gebruikt.</span><span class="sxs-lookup"><span data-stu-id="17c49-157">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="17c49-158">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="17c49-158">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="17c49-159">Als het pad escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="17c49-159">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="17c49-160">Power shell interpreteert geen tekens tussen enkele aanhalings teken als escape-reeksen.</span><span class="sxs-lookup"><span data-stu-id="17c49-160">PowerShell does not interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

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

### <span data-ttu-id="17c49-161">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="17c49-161">-MaximumVersion</span></span>

<span data-ttu-id="17c49-162">Hiermee geeft u het maximum of nieuwste versie van de module op die moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-162">Specifies the maximum, or newest, version of the module to save.</span></span> <span data-ttu-id="17c49-163">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="17c49-163">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="17c49-164">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="17c49-164">-MinimumVersion</span></span>

<span data-ttu-id="17c49-165">Hiermee geeft u de minimum versie van één module op die moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-165">Specifies the minimum version of a single module to save.</span></span> <span data-ttu-id="17c49-166">U kunt deze para meter niet toevoegen als u probeert meerdere modules te installeren.</span><span class="sxs-lookup"><span data-stu-id="17c49-166">You cannot add this parameter if you are attempting to install multiple modules.</span></span> <span data-ttu-id="17c49-167">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="17c49-167">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="17c49-168">-Name</span><span class="sxs-lookup"><span data-stu-id="17c49-168">-Name</span></span>

<span data-ttu-id="17c49-169">Hiermee geeft u een matrix met namen van modules op die moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-169">Specifies an array of names of modules to save.</span></span>

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

### <span data-ttu-id="17c49-170">-Path</span><span class="sxs-lookup"><span data-stu-id="17c49-170">-Path</span></span>

<span data-ttu-id="17c49-171">Hiermee geeft u de locatie op de lokale computer op waarop een opgeslagen module moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-171">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="17c49-172">Accepteert joker tekens.</span><span class="sxs-lookup"><span data-stu-id="17c49-172">Accepts wildcard characters.</span></span>

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

### <span data-ttu-id="17c49-173">-Proxy</span><span class="sxs-lookup"><span data-stu-id="17c49-173">-Proxy</span></span>

<span data-ttu-id="17c49-174">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="17c49-174">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>

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

### <span data-ttu-id="17c49-175">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="17c49-175">-ProxyCredential</span></span>

<span data-ttu-id="17c49-176">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="17c49-176">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="17c49-177">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="17c49-177">-Repository</span></span>

<span data-ttu-id="17c49-178">Hiermee geeft u de beschrijvende naam op van een opslag plaats die is geregistreerd door te worden uitgevoerd `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="17c49-178">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="17c49-179">Gebruik `Get-PSRepository` om geregistreerde opslag plaatsen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="17c49-179">Use `Get-PSRepository` to display registered repositories.</span></span>

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

### <span data-ttu-id="17c49-180">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="17c49-180">-RequiredVersion</span></span>

<span data-ttu-id="17c49-181">Hiermee geeft u het exacte versie nummer van de module op die moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="17c49-181">Specifies the exact version number of the module to save.</span></span>

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

### <span data-ttu-id="17c49-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="17c49-182">-WhatIf</span></span>

<span data-ttu-id="17c49-183">Laat zien wat er zou gebeuren als de `Save-Module` uitvoeringen wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="17c49-183">Shows what would happen if the `Save-Module` runs.</span></span> <span data-ttu-id="17c49-184">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="17c49-184">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="17c49-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="17c49-185">CommonParameters</span></span>

<span data-ttu-id="17c49-186">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="17c49-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="17c49-187">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="17c49-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="17c49-188">INVOER</span><span class="sxs-lookup"><span data-stu-id="17c49-188">INPUTS</span></span>

### <span data-ttu-id="17c49-189">System.String[]</span><span class="sxs-lookup"><span data-stu-id="17c49-189">System.String[]</span></span>

### <span data-ttu-id="17c49-190">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="17c49-190">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="17c49-191">System. String</span><span class="sxs-lookup"><span data-stu-id="17c49-191">System.String</span></span>

### <span data-ttu-id="17c49-192">System. URI</span><span class="sxs-lookup"><span data-stu-id="17c49-192">System.Uri</span></span>

### <span data-ttu-id="17c49-193">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="17c49-193">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="17c49-194">UITVOER</span><span class="sxs-lookup"><span data-stu-id="17c49-194">OUTPUTS</span></span>

### <span data-ttu-id="17c49-195">System. object</span><span class="sxs-lookup"><span data-stu-id="17c49-195">System.Object</span></span>

## <span data-ttu-id="17c49-196">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="17c49-196">NOTES</span></span>

## <span data-ttu-id="17c49-197">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="17c49-197">RELATED LINKS</span></span>