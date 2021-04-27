---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/26/2021
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: 651c3f24cc18ac83ff64883b292546be8a264773
ms.sourcegitcommit: 1e1535cb22d16de06f80beafe77a37a7c77de6d3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025754"
---
# <span data-ttu-id="a8e0b-102">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a8e0b-102">Install-PackageProvider</span></span>

## <span data-ttu-id="a8e0b-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a8e0b-103">SYNOPSIS</span></span>
<span data-ttu-id="a8e0b-104">Installeert een of meer pakketproviders voor pakketbeheer.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-104">Installs one or more Package Management package providers.</span></span>

## <span data-ttu-id="a8e0b-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a8e0b-105">SYNTAX</span></span>

### <span data-ttu-id="a8e0b-106">PackageBySearch (standaard)</span><span class="sxs-lookup"><span data-stu-id="a8e0b-106">PackageBySearch (Default)</span></span>

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="a8e0b-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="a8e0b-107">PackageByInputObject</span></span>

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="a8e0b-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a8e0b-108">DESCRIPTION</span></span>

<span data-ttu-id="a8e0b-109">De `Install-PackageProvider` cmdlet installeert overeenkomende Package Management-providers die beschikbaar zijn in pakketbronnen die zijn geregistreerd bij **PowerShellGet.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-109">The `Install-PackageProvider` cmdlet installs matching Package Management providers that are available in package sources registered with **PowerShellGet**.</span></span> <span data-ttu-id="a8e0b-110">Dit omvat standaard modules die beschikbaar zijn in de Windows PowerShell Gallery met de **tag PackageManagement.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-110">By default, this includes modules available in the Windows PowerShell Gallery with the **PackageManagement** tag.</span></span> <span data-ttu-id="a8e0b-111">De **PowerShellGet Package** Management-provider wordt gebruikt voor het vinden van providers in deze opslagplaatsen.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-111">The **PowerShellGet** Package Management provider is used for finding providers in these repositories.</span></span>

<span data-ttu-id="a8e0b-112">Met deze cmdlet installeert u ook overeenkomende Package Management-providers die beschikbaar zijn met behulp van de pakketbeheertoepassing bootstrapping.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-112">This cmdlet also installs matching Package Management providers that are available using the Package Management bootstrapping application.</span></span>

<span data-ttu-id="a8e0b-113">Met deze cmdlet worden ook overeenkomende Package Management-providers geïnstalleerd die beschikbaar zijn in de Package Management Azure Blob Store.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-113">This cmdlet also installs matching Package Management providers that are available in the Package Management Azure Blob store.</span></span> <span data-ttu-id="a8e0b-114">Gebruik de bootstrapper-provider om ze te zoeken en te installeren.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-114">Use the bootstrapper provider to find and install them.</span></span>

<span data-ttu-id="a8e0b-115">Om de eerste keer uit te voeren, heeft PackageManagement een internetverbinding nodig om de NuGet-pakketprovider te downloaden.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-115">In order to execute the first time, PackageManagement requires an internet connection to download the NuGet package provider.</span></span> <span data-ttu-id="a8e0b-116">Als uw computer echter geen internetverbinding heeft en u de NuGet- of PowerShellGet-provider moet gebruiken, kunt u deze downloaden op een andere computer en naar uw doelcomputer kopiëren.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-116">However, if your computer does not have an internet connection and you need to use the NuGet or PowerShellGet provider, you can download them on another computer and copy them to your target computer.</span></span> <span data-ttu-id="a8e0b-117">Gebruik de volgende stappen om dit te doen:</span><span class="sxs-lookup"><span data-stu-id="a8e0b-117">Use the following steps to do this:</span></span>

1. <span data-ttu-id="a8e0b-118">Voer `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` uit om de provider te installeren vanaf een computer met een internetverbinding.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-118">Run `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` to install the provider from a computer with an internet connection.</span></span>
1. <span data-ttu-id="a8e0b-119">Na de installatie kunt u de provider vinden die is geïnstalleerd in `$env:ProgramFiles\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` of `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` .</span><span class="sxs-lookup"><span data-stu-id="a8e0b-119">After the install, you can find the provider installed in `$env:ProgramFiles\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>`.</span></span>
1. <span data-ttu-id="a8e0b-120">Plaats de `<ProviderName>` map, in dit geval de nuGet-map, op de overeenkomstige locatie op uw doelcomputer.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-120">Place the `<ProviderName>` folder, which in this case is the NuGet folder, in the corresponding location on your target computer.</span></span> <span data-ttu-id="a8e0b-121">Als uw doelcomputer een Nano-server is, moet u uitvoeren vanaf Nano Server om `Install-PackageProvider` de juiste binaire NuGet-bestanden te downloaden.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-121">If your target computer is a Nano server, you need to run `Install-PackageProvider` from Nano Server to download the correct NuGet binaries.</span></span>
1. <span data-ttu-id="a8e0b-122">Start PowerShell opnieuw op om de pakketprovider automatisch te laden.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-122">Restart PowerShell to auto-load the package provider.</span></span> <span data-ttu-id="a8e0b-123">U kunt ook uitvoeren om `Get-PackageProvider -ListAvailable` een lijst weer te geven van alle pakketproviders die beschikbaar zijn op de computer.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-123">Alternatively, run `Get-PackageProvider -ListAvailable` to list all the package providers available on the computer.</span></span>
   <span data-ttu-id="a8e0b-124">Gebruik vervolgens `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` om de provider te importeren in de huidige Windows PowerShell sessie.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-124">Then use `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` to import the provider to the current Windows PowerShell session.</span></span>

## <span data-ttu-id="a8e0b-125">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a8e0b-125">EXAMPLES</span></span>

### <span data-ttu-id="a8e0b-126">Voorbeeld 1: een pakketprovider installeren vanuit de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="a8e0b-126">Example 1: Install a package provider from the PowerShell Gallery</span></span>

<span data-ttu-id="a8e0b-127">Met deze opdracht installeert u de provider van het PakketProvider-PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-127">This command installs the GistProvider package provider from the PowerShell Gallery.</span></span>

```powershell
Install-PackageProvider -Name "GistProvider" -Verbose
```

### <span data-ttu-id="a8e0b-128">Voorbeeld 2: een opgegeven versie van een pakketprovider installeren</span><span class="sxs-lookup"><span data-stu-id="a8e0b-128">Example 2: Install a specified version of a package provider</span></span>

<span data-ttu-id="a8e0b-129">In dit voorbeeld wordt een opgegeven versie van de NuGet-pakketprovider geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-129">This example installs a specified version of the NuGet package provider.</span></span>

<span data-ttu-id="a8e0b-130">Met de eerste opdracht worden alle versies van de pakketprovider met de naam NuGet gevonden.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-130">The first command finds all versions of the package provider named NuGet.</span></span>
<span data-ttu-id="a8e0b-131">Met de tweede opdracht wordt een opgegeven versie van de NuGet-pakketprovider geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-131">The second command installs a specified version of the NuGet package provider.</span></span>

```powershell
Find-PackageProvider -Name "NuGet" -AllVersions
Install-PackageProvider -Name "NuGet" -RequiredVersion "2.8.5.216" -Force
```

### <span data-ttu-id="a8e0b-132">Voorbeeld 3: Een provider zoeken en installeren</span><span class="sxs-lookup"><span data-stu-id="a8e0b-132">Example 3: Find a provider and install it</span></span>

<span data-ttu-id="a8e0b-133">In dit voorbeeld wordt `Find-PackageProvider` gebruikgemaakt van en de pijplijn om te zoeken naar de Leverancier-provider en deze te installeren.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-133">This example uses `Find-PackageProvider` and the pipeline to search for the Gist provider and install it.</span></span>

```powershell
Find-PackageProvider -Name "GistProvider" | Install-PackageProvider -Verbose
```

### <span data-ttu-id="a8e0b-134">Voorbeeld 4: Een provider installeren in de modulemap van de huidige gebruiker</span><span class="sxs-lookup"><span data-stu-id="a8e0b-134">Example 4: Install a provider to the current user's module folder</span></span>

<span data-ttu-id="a8e0b-135">Met deze opdracht installeert u een pakketprovider `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` in zodat alleen de huidige gebruiker deze kan gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-135">This command installs a package provider to `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` so that only the current user can use it.</span></span>

```powershell
Install-PackageProvider -Name GistProvider -Verbose -Scope CurrentUser
```

## <span data-ttu-id="a8e0b-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a8e0b-136">PARAMETERS</span></span>

### <span data-ttu-id="a8e0b-137">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="a8e0b-137">-AllVersions</span></span>

<span data-ttu-id="a8e0b-138">Geeft aan dat deze cmdlet alle beschikbare versies van de pakketprovider installeert.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-138">Indicates that this cmdlet installs all available versions of the package provider.</span></span> <span data-ttu-id="a8e0b-139">Standaard `Install-PackageProvider` retourneert alleen de hoogste beschikbare versie.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-139">By default, `Install-PackageProvider` only returns the highest available version.</span></span>

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

### <span data-ttu-id="a8e0b-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="a8e0b-140">-Credential</span></span>

<span data-ttu-id="a8e0b-141">Hiermee geeft u een gebruikersaccount met machtigingen voor het installeren van pakketproviders.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-141">Specifies a user account that has permission to install package providers.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8e0b-142">-Force</span><span class="sxs-lookup"><span data-stu-id="a8e0b-142">-Force</span></span>

<span data-ttu-id="a8e0b-143">Geeft aan dat deze cmdlet alle acties forceerd met deze cmdlet die kunnen worden geforceerd.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-143">Indicates that this cmdlet forces all actions with this cmdlet that can be forced.</span></span> <span data-ttu-id="a8e0b-144">Op dit moment betekent dit dat de parameter **Force** hetzelfde werkt als de **parameter ForceBootstrap.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-144">Currently, this means the **Force** parameter acts the same as the **ForceBootstrap** parameter.</span></span>

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

### <span data-ttu-id="a8e0b-145">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="a8e0b-145">-ForceBootstrap</span></span>

<span data-ttu-id="a8e0b-146">Geeft aan dat deze cmdlet automatisch de pakketprovider installeert.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-146">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="a8e0b-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a8e0b-147">-InputObject</span></span>

<span data-ttu-id="a8e0b-148">Hiermee geeft u een **SoftwareIdentity-object.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-148">Specifies a **SoftwareIdentity** object.</span></span> <span data-ttu-id="a8e0b-149">Gebruik de `Find-PackageProvider` cmdlet om een **SoftwareIdentity-object te** verkrijgen om door te se pijpen naar `Install-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="a8e0b-149">Use the `Find-PackageProvider` cmdlet to obtain a **SoftwareIdentity** object to pipe into `Install-PackageProvider`.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a8e0b-150">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a8e0b-150">-MaximumVersion</span></span>

<span data-ttu-id="a8e0b-151">Hiermee geeft u de maximaal toegestane versie van de pakketprovider die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-151">Specifies the maximum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="a8e0b-152">Als u deze parameter niet toevoegt, `Install-PackageProvider` installeert de hoogste beschikbare versie van de provider.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-152">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8e0b-153">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a8e0b-153">-MinimumVersion</span></span>

<span data-ttu-id="a8e0b-154">Hiermee geeft u de minimaal toegestane versie van de pakketprovider op die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-154">Specifies the minimum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="a8e0b-155">Als u deze parameter niet toevoegt, installeert de hoogste beschikbare versie van het pakket dat ook voldoet aan een vereiste die is opgegeven door de `Install-PackageProvider` *parameter MaximumVersion.*</span><span class="sxs-lookup"><span data-stu-id="a8e0b-155">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the package that also satisfies any requirement specified by the *MaximumVersion* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8e0b-156">-Name</span><span class="sxs-lookup"><span data-stu-id="a8e0b-156">-Name</span></span>

<span data-ttu-id="a8e0b-157">Hiermee geeft u een of meer pakket provider modulenamen.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-157">Specifies one or more package provider module names.</span></span> <span data-ttu-id="a8e0b-158">Scheid meerdere pakketnamen met komma's.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-158">Separate multiple package names with commas.</span></span>
<span data-ttu-id="a8e0b-159">Jokertekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-159">Wildcard characters are not supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8e0b-160">-Proxy</span><span class="sxs-lookup"><span data-stu-id="a8e0b-160">-Proxy</span></span>

<span data-ttu-id="a8e0b-161">Hiermee geeft u een proxyserver voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de internetresource.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-161">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="a8e0b-162">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a8e0b-162">-ProxyCredential</span></span>

<span data-ttu-id="a8e0b-163">Hiermee geeft u een gebruikersaccount dat is gemachtigd voor het gebruik van de proxyserver die is opgegeven door de **proxyparameter.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-163">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8e0b-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a8e0b-164">-RequiredVersion</span></span>

<span data-ttu-id="a8e0b-165">Hiermee geeft u de exacte toegestane versie van de pakketprovider die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-165">Specifies the exact allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="a8e0b-166">Als u deze parameter niet toevoegt, installeert de hoogste beschikbare versie van de provider die ook voldoet aan een maximumversie die is opgegeven door de `Install-PackageProvider` **parameter MaximumVersion.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-166">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a8e0b-167">-Bereik</span><span class="sxs-lookup"><span data-stu-id="a8e0b-167">-Scope</span></span>

<span data-ttu-id="a8e0b-168">Hiermee geeft u het installatiebereik van de provider.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-168">Specifies the installation scope of the provider.</span></span> <span data-ttu-id="a8e0b-169">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="a8e0b-169">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a8e0b-170">**AllUsers:** installeert providers op een locatie die toegankelijk is voor alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-170">**AllUsers** - installs providers in a location that is accessible to all users of the computer.</span></span>
  <span data-ttu-id="a8e0b-171">Standaard is dit **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-171">By default, this is **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**</span></span>

- <span data-ttu-id="a8e0b-172">**CurrentUser:** installeert providers op een locatie waar ze alleen toegankelijk zijn voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-172">**CurrentUser** - installs providers in a location where they are only accessible to the current user.</span></span> <span data-ttu-id="a8e0b-173">Standaard is dit **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span><span class="sxs-lookup"><span data-stu-id="a8e0b-173">By default, this is **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span></span>

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

### <span data-ttu-id="a8e0b-174">-Source</span><span class="sxs-lookup"><span data-stu-id="a8e0b-174">-Source</span></span>

<span data-ttu-id="a8e0b-175">Hiermee geeft u een of meer pakketbronnen.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-175">Specifies one or more package sources.</span></span> <span data-ttu-id="a8e0b-176">Gebruik de `Get-PackageSource` cmdlet om een lijst met beschikbare pakketbronnen op te halen.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-176">Use the `Get-PackageSource` cmdlet to get a list of available package sources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a8e0b-177">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a8e0b-177">-Confirm</span></span>

<span data-ttu-id="a8e0b-178">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-178">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a8e0b-179">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a8e0b-179">-WhatIf</span></span>

<span data-ttu-id="a8e0b-180">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-180">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a8e0b-181">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-181">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a8e0b-182">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a8e0b-182">CommonParameters</span></span>

<span data-ttu-id="a8e0b-183">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-183">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a8e0b-184">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a8e0b-184">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a8e0b-185">INVOER</span><span class="sxs-lookup"><span data-stu-id="a8e0b-185">INPUTS</span></span>

### <span data-ttu-id="a8e0b-186">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span><span class="sxs-lookup"><span data-stu-id="a8e0b-186">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="a8e0b-187">U kunt een **SoftwareIdentity-object doorseen** naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-187">You can pipe a **SoftwareIdentity** object to this cmdlet.</span></span> <span data-ttu-id="a8e0b-188">Gebruik `Find-PackageProvider` om een **SoftwareIdentity-object** op te halen dat kan worden doorspijpt naar `Install-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="a8e0b-188">Use `Find-PackageProvider` to get a **SoftwareIdentity** object that can be piped into `Install-PackageProvider`.</span></span>

## <span data-ttu-id="a8e0b-189">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a8e0b-189">OUTPUTS</span></span>

## <span data-ttu-id="a8e0b-190">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a8e0b-190">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8e0b-191">Vanaf april 2020 ondersteunt de PowerShell Gallery versies 1.0 en 1.1 Transport Layer Security (TLS) niet meer.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-191">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="a8e0b-192">Als u TLS 1.2 of hoger niet gebruikt, wordt er een foutbericht weergegeven wanneer u toegang probeert te krijgen tot PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-192">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="a8e0b-193">Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1.2 gebruikt:</span><span class="sxs-lookup"><span data-stu-id="a8e0b-193">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="a8e0b-194">Zie de aankondiging in [de](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) PowerShell-blog voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a8e0b-194">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="a8e0b-195">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a8e0b-195">RELATED LINKS</span></span>

[<span data-ttu-id="a8e0b-196">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a8e0b-196">Find-PackageProvider</span></span>](Find-PackageProvider.md)

[<span data-ttu-id="a8e0b-197">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a8e0b-197">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="a8e0b-198">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a8e0b-198">Import-PackageProvider</span></span>](Import-PackageProvider.md)
