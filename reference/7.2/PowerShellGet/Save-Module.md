---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 11/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/save-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Module
ms.openlocfilehash: df5056b4402664602409388825c8b2b8acd4e02f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891889"
---
# <span data-ttu-id="ee1f6-102">Save-Module</span><span class="sxs-lookup"><span data-stu-id="ee1f6-102">Save-Module</span></span>

## <span data-ttu-id="ee1f6-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ee1f6-103">SYNOPSIS</span></span>
<span data-ttu-id="ee1f6-104">Slaat een module en de bijbehorende afhankelijkheden op de lokale computer op, maar installeert de module niet.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-104">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

## <span data-ttu-id="ee1f6-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ee1f6-105">SYNTAX</span></span>

### <span data-ttu-id="ee1f6-106">NameAndPathParameterSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="ee1f6-106">NameAndPathParameterSet (Default)</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ee1f6-107">NameAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="ee1f6-107">NameAndLiteralPathParameterSet</span></span>

```
Save-Module [-Name] <String[]> [-MinimumVersion <String>] [-MaximumVersion <String>]
 [-RequiredVersion <String>] [-Repository <String[]>] -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AllowPrerelease]
 [-AcceptLicense] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ee1f6-108">InputObjectAndLiteralPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="ee1f6-108">InputObjectAndLiteralPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> -LiteralPath <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ee1f6-109">InputObjectAndPathParameterSet</span><span class="sxs-lookup"><span data-stu-id="ee1f6-109">InputObjectAndPathParameterSet</span></span>

```
Save-Module [-InputObject] <PSObject[]> [-Path] <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-Credential <PSCredential>] [-Force] [-AcceptLicense] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ee1f6-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ee1f6-110">DESCRIPTION</span></span>

<span data-ttu-id="ee1f6-111">De `Save-Module` cmdlet downloadt een module en eventuele afhankelijkheden van een geregistreerde opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-111">The `Save-Module` cmdlet downloads a module and any dependencies from a registered repository.</span></span>
<span data-ttu-id="ee1f6-112">`Save-Module` Hiermee wordt de meest recente versie van een module gedownload en opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-112">`Save-Module` downloads and saves the most current version of a module.</span></span> <span data-ttu-id="ee1f6-113">De bestanden worden opgeslagen in een opgegeven pad op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-113">The files are saved to a specified path on the local computer.</span></span> <span data-ttu-id="ee1f6-114">De module is niet geïnstalleerd, maar de inhoud is beschikbaar voor inspectie door een beheerder.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-114">The module isn't installed, but the contents are available for inspection by an administrator.</span></span> <span data-ttu-id="ee1f6-115">De opgeslagen module kan vervolgens worden gekopieerd naar de juiste `$env:PSModulePath` locatie van de offline machine.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-115">The saved module can then be copied into the appropriate `$env:PSModulePath` location of the offline machine.</span></span>

<span data-ttu-id="ee1f6-116">`Get-PSRepository` Hiermee worden de geregistreerde opslag plaatsen van de lokale computer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-116">`Get-PSRepository` displays the local computer's registered repositories.</span></span> <span data-ttu-id="ee1f6-117">U kunt de `Find-Module` cmdlet gebruiken om te zoeken in geregistreerde opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-117">You can use the `Find-Module` cmdlet to search registered repositories.</span></span>

## <span data-ttu-id="ee1f6-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ee1f6-118">EXAMPLES</span></span>

### <span data-ttu-id="ee1f6-119">Voor beeld 1: een module opslaan</span><span class="sxs-lookup"><span data-stu-id="ee1f6-119">Example 1: Save a module</span></span>

<span data-ttu-id="ee1f6-120">In dit voor beeld worden een module en de bijbehorende afhankelijkheden opgeslagen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-120">In this example, a module and its dependencies are saved to the local computer.</span></span>

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

<span data-ttu-id="ee1f6-121">`Save-Module` maakt gebruik van de para meter **name** om de module **PowerShellGet** op te geven.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-121">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="ee1f6-122">De para meter **Path** geeft aan waar de gedownloade module moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-122">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="ee1f6-123">De **opslagplaats** parameter geeft een geregistreerde opslag plaats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-123">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="ee1f6-124">Wanneer het downloaden is voltooid, `Get-ChildItem` wordt de inhoud weer gegeven van het **pad** waar de bestanden zijn opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-124">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="ee1f6-125">Voor beeld 2: een specifieke versie van een module opslaan</span><span class="sxs-lookup"><span data-stu-id="ee1f6-125">Example 2: Save a specific version of a module</span></span>

<span data-ttu-id="ee1f6-126">In dit voor beeld ziet u hoe u een para meter zoals **MaximumVersion** of **RequiredVersion** gebruikt om een module versie op te geven.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-126">This example shows how to use a parameter such as **MaximumVersion**, or **RequiredVersion** to specify a module version.</span></span>

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

<span data-ttu-id="ee1f6-127">`Save-Module` maakt gebruik van de para meter **name** om de module **PowerShellGet** op te geven.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-127">`Save-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="ee1f6-128">De para meter **Path** geeft aan waar de gedownloade module moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-128">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="ee1f6-129">De **opslagplaats** parameter geeft een geregistreerde opslag plaats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-129">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="ee1f6-130">**MaximumVersion** geeft aan dat versie **2.1.0** wordt gedownload en opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-130">**MaximumVersion** specifies that version **2.1.0** is downloaded and saved.</span></span> <span data-ttu-id="ee1f6-131">Wanneer het downloaden is voltooid, `Get-ChildItem` wordt de inhoud weer gegeven van het **pad** waar de bestanden zijn opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-131">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

### <span data-ttu-id="ee1f6-132">Voor beeld 3: een specifieke versie van een module zoeken en opslaan</span><span class="sxs-lookup"><span data-stu-id="ee1f6-132">Example 3: Find and save a specific version of a module</span></span>

<span data-ttu-id="ee1f6-133">In dit voor beeld wordt een vereiste module versie gevonden in de opslag plaats en opgeslagen op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-133">In this example, a required module version is found in the repository and saved to the local computer.</span></span>

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

<span data-ttu-id="ee1f6-134">`Find-Module` maakt gebruik van de para meter **name** om de module **PowerShellGet** op te geven.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-134">`Find-Module` uses the **Name** parameter to specify the module, **PowerShellGet**.</span></span> <span data-ttu-id="ee1f6-135">De **opslagplaats** parameter geeft een geregistreerde opslag plaats, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-135">The **Repository** parameter specifies a registered repository, **PSGallery**.</span></span> <span data-ttu-id="ee1f6-136">**RequiredVersion** geeft versie **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-136">**RequiredVersion** specifies version **1.6.5**.</span></span>

<span data-ttu-id="ee1f6-137">Het object wordt naar de pijp lijn verzonden `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="ee1f6-137">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="ee1f6-138">De para meter **Path** geeft aan waar de gedownloade module moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-138">The **Path** parameter specifies where to store the downloaded module.</span></span> <span data-ttu-id="ee1f6-139">Wanneer het downloaden is voltooid, `Get-ChildItem` wordt de inhoud weer gegeven van het **pad** waar de bestanden zijn opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-139">After the download is finished, `Get-ChildItem` displays the contents of **Path** where the files are stored.</span></span>

## <span data-ttu-id="ee1f6-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ee1f6-140">PARAMETERS</span></span>

### <span data-ttu-id="ee1f6-141">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="ee1f6-141">-AcceptLicense</span></span>

<span data-ttu-id="ee1f6-142">Accepteer de gebruiksrecht overeenkomst automatisch als het pakket deze vereist.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-142">Automatically accept the license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="ee1f6-143">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="ee1f6-143">-AllowPrerelease</span></span>

<span data-ttu-id="ee1f6-144">Hiermee kunt u een module opslaan die is gemarkeerd als een voorlopige versie.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-144">Allows you to save a module marked as a prerelease.</span></span>

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

### <span data-ttu-id="ee1f6-145">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ee1f6-145">-Confirm</span></span>

<span data-ttu-id="ee1f6-146">Vraagt u om bevestiging voordat de wordt uitgevoerd `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="ee1f6-146">Prompts you for confirmation before running the `Save-Module`.</span></span>

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

### <span data-ttu-id="ee1f6-147">-Credential</span><span class="sxs-lookup"><span data-stu-id="ee1f6-147">-Credential</span></span>

<span data-ttu-id="ee1f6-148">Hiermee geeft u een gebruikers account op dat rechten heeft om een module op te slaan.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-148">Specifies a user account that has rights to save a module.</span></span>

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

### <span data-ttu-id="ee1f6-149">-Force</span><span class="sxs-lookup"><span data-stu-id="ee1f6-149">-Force</span></span>

<span data-ttu-id="ee1f6-150">Er wordt geforceerd `Save-Module` dat de uitvoering wordt uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-150">Forces `Save-Module` to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="ee1f6-151">-Input object</span><span class="sxs-lookup"><span data-stu-id="ee1f6-151">-InputObject</span></span>

<span data-ttu-id="ee1f6-152">Hiermee wordt een **PSRepositoryItemInfo** -object geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-152">Accepts a **PSRepositoryItemInfo** object.</span></span> <span data-ttu-id="ee1f6-153">Bijvoorbeeld: uitvoer `Find-Module` naar een variabele en de variabele gebruiken als het argument **input object** .</span><span class="sxs-lookup"><span data-stu-id="ee1f6-153">For example, output `Find-Module` to a variable and use that variable as the **InputObject** argument.</span></span>

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

### <span data-ttu-id="ee1f6-154">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ee1f6-154">-LiteralPath</span></span>

<span data-ttu-id="ee1f6-155">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-155">Specifies a path to one or more locations.</span></span> <span data-ttu-id="ee1f6-156">De waarde van de para meter **LiteralPath** wordt exact als opgegeven gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-156">The value of the **LiteralPath** parameter is used exactly as entered.</span></span> <span data-ttu-id="ee1f6-157">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-157">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ee1f6-158">Als het pad escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-158">If the path includes escape characters, enclose them in single quotation marks.</span></span> <span data-ttu-id="ee1f6-159">Power shell interpreteert geen tekens tussen enkele aanhalings teken als escape-reeksen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-159">PowerShell does not interpret any characters enclosed in single quotation marks as escape sequences.</span></span>

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

### <span data-ttu-id="ee1f6-160">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="ee1f6-160">-MaximumVersion</span></span>

<span data-ttu-id="ee1f6-161">Hiermee geeft u het maximum of nieuwste versie van de module op die moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-161">Specifies the maximum, or newest, version of the module to save.</span></span> <span data-ttu-id="ee1f6-162">De para meters **MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-162">The **MaximumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="ee1f6-163">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="ee1f6-163">-MinimumVersion</span></span>

<span data-ttu-id="ee1f6-164">Hiermee geeft u de minimum versie van één module op die moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-164">Specifies the minimum version of a single module to save.</span></span> <span data-ttu-id="ee1f6-165">U kunt deze para meter niet toevoegen als u probeert meerdere modules te installeren.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-165">You cannot add this parameter if you are attempting to install multiple modules.</span></span> <span data-ttu-id="ee1f6-166">De para meters **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-166">The **MinimumVersion** and **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="ee1f6-167">-Name</span><span class="sxs-lookup"><span data-stu-id="ee1f6-167">-Name</span></span>

<span data-ttu-id="ee1f6-168">Hiermee geeft u een matrix met namen van modules op die moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-168">Specifies an array of names of modules to save.</span></span>

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

### <span data-ttu-id="ee1f6-169">-Path</span><span class="sxs-lookup"><span data-stu-id="ee1f6-169">-Path</span></span>

<span data-ttu-id="ee1f6-170">Hiermee geeft u de locatie op de lokale computer op waarop een opgeslagen module moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-170">Specifies the location on the local computer to store a saved module.</span></span> <span data-ttu-id="ee1f6-171">Accepteert joker tekens.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-171">Accepts wildcard characters.</span></span>

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

### <span data-ttu-id="ee1f6-172">-Proxy</span><span class="sxs-lookup"><span data-stu-id="ee1f6-172">-Proxy</span></span>

<span data-ttu-id="ee1f6-173">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-173">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>

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

### <span data-ttu-id="ee1f6-174">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="ee1f6-174">-ProxyCredential</span></span>

<span data-ttu-id="ee1f6-175">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="ee1f6-175">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="ee1f6-176">-Opslag plaats</span><span class="sxs-lookup"><span data-stu-id="ee1f6-176">-Repository</span></span>

<span data-ttu-id="ee1f6-177">Hiermee geeft u de beschrijvende naam op van een opslag plaats die is geregistreerd door te worden uitgevoerd `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="ee1f6-177">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="ee1f6-178">Gebruik `Get-PSRepository` om geregistreerde opslag plaatsen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-178">Use `Get-PSRepository` to display registered repositories.</span></span>

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

### <span data-ttu-id="ee1f6-179">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="ee1f6-179">-RequiredVersion</span></span>

<span data-ttu-id="ee1f6-180">Hiermee geeft u het exacte versie nummer van de module op die moet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-180">Specifies the exact version number of the module to save.</span></span>

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

### <span data-ttu-id="ee1f6-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ee1f6-181">-WhatIf</span></span>

<span data-ttu-id="ee1f6-182">Laat zien wat er zou gebeuren als de `Save-Module` uitvoeringen wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-182">Shows what would happen if the `Save-Module` runs.</span></span> <span data-ttu-id="ee1f6-183">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-183">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ee1f6-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee1f6-184">CommonParameters</span></span>

<span data-ttu-id="ee1f6-185">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee1f6-186">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ee1f6-187">INVOER</span><span class="sxs-lookup"><span data-stu-id="ee1f6-187">INPUTS</span></span>

### <span data-ttu-id="ee1f6-188">System.String[]</span><span class="sxs-lookup"><span data-stu-id="ee1f6-188">System.String[]</span></span>

### <span data-ttu-id="ee1f6-189">System. Management. Automation. PSObject []</span><span class="sxs-lookup"><span data-stu-id="ee1f6-189">System.Management.Automation.PSObject[]</span></span>

### <span data-ttu-id="ee1f6-190">System. String</span><span class="sxs-lookup"><span data-stu-id="ee1f6-190">System.String</span></span>

### <span data-ttu-id="ee1f6-191">System. URI</span><span class="sxs-lookup"><span data-stu-id="ee1f6-191">System.Uri</span></span>

### <span data-ttu-id="ee1f6-192">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="ee1f6-192">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="ee1f6-193">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ee1f6-193">OUTPUTS</span></span>

### <span data-ttu-id="ee1f6-194">System. object</span><span class="sxs-lookup"><span data-stu-id="ee1f6-194">System.Object</span></span>

## <span data-ttu-id="ee1f6-195">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ee1f6-195">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ee1f6-196">Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-196">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="ee1f6-197">Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-197">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="ee1f6-198">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="ee1f6-198">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="ee1f6-199">Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ee1f6-199">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="ee1f6-200">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ee1f6-200">RELATED LINKS</span></span>
