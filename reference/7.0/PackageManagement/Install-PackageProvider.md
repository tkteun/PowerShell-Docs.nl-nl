---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: bd149e554528101e20cdc51ca728e679ed2cf28d
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524617"
---
# <span data-ttu-id="01b4d-103">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="01b4d-103">Install-PackageProvider</span></span>

## <span data-ttu-id="01b4d-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="01b4d-104">SYNOPSIS</span></span>
<span data-ttu-id="01b4d-105">Hiermee worden een of meer pakket beheer pakket providers geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="01b4d-105">Installs one or more Package Management package providers.</span></span>

## <span data-ttu-id="01b4d-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="01b4d-106">SYNTAX</span></span>

### <span data-ttu-id="01b4d-107">PackageBySearch (standaard)</span><span class="sxs-lookup"><span data-stu-id="01b4d-107">PackageBySearch (Default)</span></span>

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="01b4d-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="01b4d-108">PackageByInputObject</span></span>

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="01b4d-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="01b4d-109">DESCRIPTION</span></span>

<span data-ttu-id="01b4d-110">`Install-PackageProvider`Met de cmdlet worden overeenkomende pakket beheer providers geïnstalleerd die beschikbaar zijn in pakket bronnen die zijn geregistreerd bij **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="01b4d-110">The `Install-PackageProvider` cmdlet installs matching Package Management providers that are available in package sources registered with **PowerShellGet**.</span></span> <span data-ttu-id="01b4d-111">Dit omvat standaard beschik bare modules in het Windows-PowerShell Gallery met het label **Package Management** .</span><span class="sxs-lookup"><span data-stu-id="01b4d-111">By default, this includes modules available in the Windows PowerShell Gallery with the **PackageManagement** tag.</span></span> <span data-ttu-id="01b4d-112">De **PowerShellGet** -pakket beheer provider wordt gebruikt voor het zoeken naar providers in deze opslag plaatsen.</span><span class="sxs-lookup"><span data-stu-id="01b4d-112">The **PowerShellGet** Package Management provider is used for finding providers in these repositories.</span></span>

<span data-ttu-id="01b4d-113">Met deze cmdlet worden ook overeenkomende pakket beheer providers geïnstalleerd die beschikbaar zijn via de toepassing voor het Boots trappen van het pakket beheer.</span><span class="sxs-lookup"><span data-stu-id="01b4d-113">This cmdlet also installs matching Package Management providers that are available using the Package Management bootstrapping application.</span></span>

<span data-ttu-id="01b4d-114">Met deze cmdlet worden ook overeenkomende pakket beheer providers geïnstalleerd die beschikbaar zijn in de Azure Blob Store van het pakket beheer.</span><span class="sxs-lookup"><span data-stu-id="01b4d-114">This cmdlet also installs matching Package Management providers that are available in the Package Management Azure Blob store.</span></span> <span data-ttu-id="01b4d-115">Gebruik de Boots Trapper-provider om ze te zoeken en te installeren.</span><span class="sxs-lookup"><span data-stu-id="01b4d-115">Use the bootstrapper provider to find and install them.</span></span>

<span data-ttu-id="01b4d-116">Voor de eerste keer moet Package Management een Internet verbinding hebben om de NuGet-pakket provider te downloaden.</span><span class="sxs-lookup"><span data-stu-id="01b4d-116">In order to execute the first time, PackageManagement requires an internet connection to download the NuGet package provider.</span></span> <span data-ttu-id="01b4d-117">Als uw computer echter geen Internet verbinding heeft en u de provider NuGet of PowerShellGet moet gebruiken, kunt u deze downloaden op een andere computer en deze naar uw doel computer kopiëren.</span><span class="sxs-lookup"><span data-stu-id="01b4d-117">However, if your computer does not have an internet connection and you need to use the NuGet or PowerShellGet provider, you can download them on another computer and copy them to your target computer.</span></span> <span data-ttu-id="01b4d-118">Gebruik de volgende stappen om dit te doen:</span><span class="sxs-lookup"><span data-stu-id="01b4d-118">Use the following steps to do this:</span></span>

1. <span data-ttu-id="01b4d-119">Voer `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` uit om de provider te installeren vanaf een computer met een Internet verbinding.</span><span class="sxs-lookup"><span data-stu-id="01b4d-119">Run `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` to install the provider from a computer with an internet connection.</span></span>
1. <span data-ttu-id="01b4d-120">Na de installatie kunt u de provider vinden die is geïnstalleerd in `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` of `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` .</span><span class="sxs-lookup"><span data-stu-id="01b4d-120">After the install, you can find the provider installed in `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>`.</span></span>
1. <span data-ttu-id="01b4d-121">Plaats de `<ProviderName>` map, in dit geval de map NuGet, in de bijbehorende locatie op de doel computer.</span><span class="sxs-lookup"><span data-stu-id="01b4d-121">Place the `<ProviderName>` folder, which in this case is the NuGet folder, in the corresponding location on your target computer.</span></span> <span data-ttu-id="01b4d-122">Als uw doel computer een nano server is, moet u uitvoeren `Install-PackageProvider` vanaf nano server om de juiste binaire NuGet-bestanden te downloaden.</span><span class="sxs-lookup"><span data-stu-id="01b4d-122">If your target computer is a Nano server, you need to run `Install-PackageProvider` from Nano Server to download the correct NuGet binaries.</span></span>
1. <span data-ttu-id="01b4d-123">Start Power shell opnieuw om de pakket provider automatisch te laden.</span><span class="sxs-lookup"><span data-stu-id="01b4d-123">Restart PowerShell to auto-load the package provider.</span></span> <span data-ttu-id="01b4d-124">U kunt ook uitvoeren `Get-PackageProvider -ListAvailable` om alle pakket providers weer te geven die beschikbaar zijn op de computer.</span><span class="sxs-lookup"><span data-stu-id="01b4d-124">Alternatively, run `Get-PackageProvider -ListAvailable` to list all the package providers available on the computer.</span></span>
   <span data-ttu-id="01b4d-125">Vervolgens gebruiken `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` om de provider te importeren in de huidige Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="01b4d-125">Then use `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` to import the provider to the current Windows PowerShell session.</span></span>

## <span data-ttu-id="01b4d-126">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="01b4d-126">EXAMPLES</span></span>

### <span data-ttu-id="01b4d-127">Voor beeld 1: een pakket provider installeren vanuit de PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="01b4d-127">Example 1: Install a package provider from the PowerShell Gallery</span></span>

<span data-ttu-id="01b4d-128">Met deze opdracht wordt de GistProvider-pakket provider van de PowerShell Gallery geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="01b4d-128">This command installs the GistProvider package provider from the PowerShell Gallery.</span></span>

```powershell
Install-PackageProvider -Name "GistProvider" -Verbose
```

### <span data-ttu-id="01b4d-129">Voor beeld 2: een opgegeven versie van een pakket provider installeren</span><span class="sxs-lookup"><span data-stu-id="01b4d-129">Example 2: Install a specified version of a package provider</span></span>

<span data-ttu-id="01b4d-130">In dit voor beeld wordt een opgegeven versie van de NuGet-pakket provider geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="01b4d-130">This example installs a specified version of the NuGet package provider.</span></span>

<span data-ttu-id="01b4d-131">Met de eerste opdracht vindt u alle versies van de pakket provider met de naam NuGet.</span><span class="sxs-lookup"><span data-stu-id="01b4d-131">The first command finds all versions of the package provider named NuGet.</span></span>
<span data-ttu-id="01b4d-132">Met de tweede opdracht wordt een opgegeven versie van de NuGet-pakket provider geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="01b4d-132">The second command installs a specified version of the NuGet package provider.</span></span>

```powershell
Find-PackageProvider -Name "NuGet" -AllVersions
Install-PackageProvider -Name "NuGet" -RequiredVersion "2.8.5.216" -Force
```

### <span data-ttu-id="01b4d-133">Voor beeld 3: een provider zoeken en installeren</span><span class="sxs-lookup"><span data-stu-id="01b4d-133">Example 3: Find a provider and install it</span></span>

<span data-ttu-id="01b4d-134">In dit voor beeld wordt `Find-PackageProvider` de pijp lijn gebruikt om te zoeken naar de bron van de service provider en deze te installeren.</span><span class="sxs-lookup"><span data-stu-id="01b4d-134">This example uses `Find-PackageProvider` and the pipeline to search for the Gist provider and install it.</span></span>

```powershell
Find-PackageProvider -Name "GistProvider" | Install-PackageProvider -Verbose
```

### <span data-ttu-id="01b4d-135">Voor beeld 4: een provider installeren op de module map van de huidige gebruiker</span><span class="sxs-lookup"><span data-stu-id="01b4d-135">Example 4: Install a provider to the current user's module folder</span></span>

<span data-ttu-id="01b4d-136">Met deze opdracht wordt een pakket provider zodanig geïnstalleerd `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` dat alleen de huidige gebruiker deze kan gebruiken.</span><span class="sxs-lookup"><span data-stu-id="01b4d-136">This command installs a package provider to `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` so that only the current user can use it.</span></span>

```powershell
Install-PackageProvider -Name GistProvider -Verbose -Scope CurrentUser
```

## <span data-ttu-id="01b4d-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="01b4d-137">PARAMETERS</span></span>

### <span data-ttu-id="01b4d-138">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="01b4d-138">-AllVersions</span></span>

<span data-ttu-id="01b4d-139">Geeft aan dat met deze cmdlet alle beschik bare versies van de pakket provider worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="01b4d-139">Indicates that this cmdlet installs all available versions of the package provider.</span></span> <span data-ttu-id="01b4d-140">`Install-PackageProvider`Retourneert standaard alleen de hoogste beschik bare versie.</span><span class="sxs-lookup"><span data-stu-id="01b4d-140">By default, `Install-PackageProvider` only returns the highest available version.</span></span>

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

### <span data-ttu-id="01b4d-141">-Credential</span><span class="sxs-lookup"><span data-stu-id="01b4d-141">-Credential</span></span>

<span data-ttu-id="01b4d-142">Hiermee geeft u een gebruikers account op dat is gemachtigd om pakket providers te installeren.</span><span class="sxs-lookup"><span data-stu-id="01b4d-142">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="01b4d-143">-Force</span><span class="sxs-lookup"><span data-stu-id="01b4d-143">-Force</span></span>

<span data-ttu-id="01b4d-144">Geeft aan dat deze cmdlet alle acties met deze cmdlet afdwingt die kunnen worden geforceerd.</span><span class="sxs-lookup"><span data-stu-id="01b4d-144">Indicates that this cmdlet forces all actions with this cmdlet that can be forced.</span></span> <span data-ttu-id="01b4d-145">Dit betekent dat de para meter **Forces** hetzelfde is als de para meter **ForceBootstrap** .</span><span class="sxs-lookup"><span data-stu-id="01b4d-145">Currently, this means the **Force** parameter acts the same as the **ForceBootstrap** parameter.</span></span>

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

### <span data-ttu-id="01b4d-146">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="01b4d-146">-ForceBootstrap</span></span>

<span data-ttu-id="01b4d-147">Geeft aan dat met deze cmdlet automatisch de pakket provider wordt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="01b4d-147">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="01b4d-148">-Input object</span><span class="sxs-lookup"><span data-stu-id="01b4d-148">-InputObject</span></span>

<span data-ttu-id="01b4d-149">Hiermee geeft u een **SoftwareIdentity** -object op.</span><span class="sxs-lookup"><span data-stu-id="01b4d-149">Specifies a **SoftwareIdentity** object.</span></span> <span data-ttu-id="01b4d-150">Gebruik de `Find-PackageProvider` cmdlet om een **SoftwareIdentity** -object naar een pipe te verkrijgen `Install-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="01b4d-150">Use the `Find-PackageProvider` cmdlet to obtain a **SoftwareIdentity** object to pipe into `Install-PackageProvider`.</span></span>

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

### <span data-ttu-id="01b4d-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="01b4d-151">-MaximumVersion</span></span>

<span data-ttu-id="01b4d-152">Hiermee geeft u de Maxi maal toegestane versie van de pakket provider op die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="01b4d-152">Specifies the maximum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="01b4d-153">Als u deze para meter niet toevoegt, wordt `Install-PackageProvider` de hoogste beschik bare versie van de provider geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="01b4d-153">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider.</span></span>

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

### <span data-ttu-id="01b4d-154">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="01b4d-154">-MinimumVersion</span></span>

<span data-ttu-id="01b4d-155">Hiermee geeft u de mini maal toegestane versie van de pakket provider die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="01b4d-155">Specifies the minimum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="01b4d-156">Als u deze para meter niet toevoegt, `Install-PackageProvider` installeert de hoogste beschik bare versie van het pakket die ook voldoet aan een vereiste die is opgegeven door de para meter *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="01b4d-156">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the package that also satisfies any requirement specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="01b4d-157">-Name</span><span class="sxs-lookup"><span data-stu-id="01b4d-157">-Name</span></span>

<span data-ttu-id="01b4d-158">Hiermee geeft u een of meer module namen van een pakket provider op.</span><span class="sxs-lookup"><span data-stu-id="01b4d-158">Specifies one or more package provider module names.</span></span> <span data-ttu-id="01b4d-159">Scheid meerdere pakket namen met komma's.</span><span class="sxs-lookup"><span data-stu-id="01b4d-159">Separate multiple package names with commas.</span></span>
<span data-ttu-id="01b4d-160">Joker tekens worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="01b4d-160">Wildcard characters are not supported.</span></span>

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

### <span data-ttu-id="01b4d-161">-Proxy</span><span class="sxs-lookup"><span data-stu-id="01b4d-161">-Proxy</span></span>

<span data-ttu-id="01b4d-162">Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.</span><span class="sxs-lookup"><span data-stu-id="01b4d-162">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="01b4d-163">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="01b4d-163">-ProxyCredential</span></span>

<span data-ttu-id="01b4d-164">Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .</span><span class="sxs-lookup"><span data-stu-id="01b4d-164">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="01b4d-165">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="01b4d-165">-RequiredVersion</span></span>

<span data-ttu-id="01b4d-166">Hiermee geeft u de exacte toegestane versie van de pakket provider op die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="01b4d-166">Specifies the exact allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="01b4d-167">Als u deze para meter niet toevoegt, `Install-PackageProvider` installeert de hoogste beschik bare versie van de provider die ook voldoet aan de maximum versie die is opgegeven door de para meter **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="01b4d-167">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="01b4d-168">-Bereik</span><span class="sxs-lookup"><span data-stu-id="01b4d-168">-Scope</span></span>

<span data-ttu-id="01b4d-169">Hiermee geeft u het installatie bereik van de provider op.</span><span class="sxs-lookup"><span data-stu-id="01b4d-169">Specifies the installation scope of the provider.</span></span> <span data-ttu-id="01b4d-170">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="01b4d-170">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="01b4d-171">**ALLUSERS** : installeert providers op een locatie die toegankelijk is voor alle gebruikers van de computer.</span><span class="sxs-lookup"><span data-stu-id="01b4d-171">**AllUsers** - installs providers in a location that is accessible to all users of the computer.</span></span>
  <span data-ttu-id="01b4d-172">Dit is standaard **$env:P rogramfiles\packagemanagement\providerassemblies.**</span><span class="sxs-lookup"><span data-stu-id="01b4d-172">By default, this is **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**</span></span>

- <span data-ttu-id="01b4d-173">**CurrentUser** : installeert providers op een locatie waar ze alleen toegankelijk zijn voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="01b4d-173">**CurrentUser** - installs providers in a location where they are only accessible to the current user.</span></span> <span data-ttu-id="01b4d-174">Dit is standaard **$env: LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span><span class="sxs-lookup"><span data-stu-id="01b4d-174">By default, this is **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span></span>

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

### <span data-ttu-id="01b4d-175">-Source</span><span class="sxs-lookup"><span data-stu-id="01b4d-175">-Source</span></span>

<span data-ttu-id="01b4d-176">Hiermee geeft u een of meer pakket bronnen op.</span><span class="sxs-lookup"><span data-stu-id="01b4d-176">Specifies one or more package sources.</span></span> <span data-ttu-id="01b4d-177">Gebruik de `Get-PackageSource` cmdlet om een lijst met beschik bare pakket bronnen op te halen.</span><span class="sxs-lookup"><span data-stu-id="01b4d-177">Use the `Get-PackageSource` cmdlet to get a list of available package sources.</span></span>

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

### <span data-ttu-id="01b4d-178">-Confirm</span><span class="sxs-lookup"><span data-stu-id="01b4d-178">-Confirm</span></span>

<span data-ttu-id="01b4d-179">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="01b4d-179">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="01b4d-180">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="01b4d-180">-WhatIf</span></span>

<span data-ttu-id="01b4d-181">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="01b4d-181">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="01b4d-182">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="01b4d-182">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="01b4d-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01b4d-183">CommonParameters</span></span>

<span data-ttu-id="01b4d-184">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="01b4d-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="01b4d-185">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="01b4d-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="01b4d-186">INVOER</span><span class="sxs-lookup"><span data-stu-id="01b4d-186">INPUTS</span></span>

### <span data-ttu-id="01b4d-187">Micro soft. package management. verpakking. SoftwareIdentity</span><span class="sxs-lookup"><span data-stu-id="01b4d-187">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="01b4d-188">U kunt een **SoftwareIdentity** -object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="01b4d-188">You can pipe a **SoftwareIdentity** object to this cmdlet.</span></span> <span data-ttu-id="01b4d-189">`Find-PackageProvider`Wordt gebruikt voor het ophalen van een **SoftwareIdentity** -object waarnaar kan worden gepiped `Install-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="01b4d-189">Use `Find-PackageProvider` to get a **SoftwareIdentity** object that can be piped into `Install-PackageProvider`.</span></span>

## <span data-ttu-id="01b4d-190">UITVOER</span><span class="sxs-lookup"><span data-stu-id="01b4d-190">OUTPUTS</span></span>

## <span data-ttu-id="01b4d-191">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="01b4d-191">NOTES</span></span>

## <span data-ttu-id="01b4d-192">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="01b4d-192">RELATED LINKS</span></span>

[<span data-ttu-id="01b4d-193">Zoeken-package provider</span><span class="sxs-lookup"><span data-stu-id="01b4d-193">Find-PackageProvider</span></span>](Find-PackageProvider.md)

[<span data-ttu-id="01b4d-194">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="01b4d-194">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="01b4d-195">Import-package provider</span><span class="sxs-lookup"><span data-stu-id="01b4d-195">Import-PackageProvider</span></span>](Import-PackageProvider.md)
