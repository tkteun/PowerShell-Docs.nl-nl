---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Nieuwe scenario's en onderdelen in WMF 5.1
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686997"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="c1dce-103">Nieuwe scenario's en onderdelen in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="c1dce-103">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="c1dce-104">Opmerking: Deze informatie is voorlopig en kan worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c1dce-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="c1dce-105">PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="c1dce-105">PowerShell Editions</span></span>

<span data-ttu-id="c1dce-106">Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="c1dce-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="c1dce-107">**Desktop-editie:** Gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Server Core- en Windows Desktop volledige footprint.</span><span class="sxs-lookup"><span data-stu-id="c1dce-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="c1dce-108">**Core-editie:** Gebaseerd op .NET Core en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Nano Server en Windows IoT verminderde footprint.</span><span class="sxs-lookup"><span data-stu-id="c1dce-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="c1dce-109">**Meer informatie over het gebruik van PowerShell-edities**</span><span class="sxs-lookup"><span data-stu-id="c1dce-109">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="c1dce-110">Actieve editie van PowerShell met behulp van $PSVersionTable bepalen</span><span class="sxs-lookup"><span data-stu-id="c1dce-110">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="c1dce-111">Resultaten van de Get-Module door met de parameter PSEdition CompatiblePSEditions te filteren</span><span class="sxs-lookup"><span data-stu-id="c1dce-111">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="c1dce-112">Scriptuitvoering wordt voorkomen tenzij uitvoert op een compatibele versie van PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1dce-112">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="c1dce-113">Declareer de compatibiliteit van een module met specifieke versies van PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1dce-113">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a><span data-ttu-id="c1dce-114">Catalogus-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c1dce-114">Catalog Cmdlets</span></span>

<span data-ttu-id="c1dce-115">Twee nieuwe-cmdlets zijn toegevoegd de [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) module; deze genereren en bestanden van Windows-catalogus te valideren.</span><span class="sxs-lookup"><span data-stu-id="c1dce-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) module; these generate and validate Windows catalog files.</span></span>

### <a name="new-filecatalog"></a><span data-ttu-id="c1dce-116">Nieuwe FileCatalog</span><span class="sxs-lookup"><span data-stu-id="c1dce-116">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="c1dce-117">Nieuwe FileCatalog Hiermee maakt u een Windows-catalogusbestand voor set van bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="c1dce-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="c1dce-118">Dit catalogusbestand bevat-hashes voor alle bestanden in de opgegeven paden.</span><span class="sxs-lookup"><span data-stu-id="c1dce-118">This catalog file contains hashes for all files in specified paths.</span></span>
<span data-ttu-id="c1dce-119">Gebruikers kunnen de set van mappen, samen met de bijbehorende catalogusbestand voor deze mappen distribueren.</span><span class="sxs-lookup"><span data-stu-id="c1dce-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span>
<span data-ttu-id="c1dce-120">Deze informatie is nuttig om te valideren of eventuele wijzigingen worden aangebracht aan de mappen sinds de aanmaaktijd van de catalogus.</span><span class="sxs-lookup"><span data-stu-id="c1dce-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="c1dce-121">Versies 1 en 2 van de catalogus worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c1dce-121">Catalog versions 1 and 2 are supported.</span></span>
<span data-ttu-id="c1dce-122">Versie 1 gebruikt de SHA1-hash-algoritme voor het maken van bestands-hashes; SHA256 maakt gebruik van versie 2.</span><span class="sxs-lookup"><span data-stu-id="c1dce-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span>
<span data-ttu-id="c1dce-123">Catalogusversie 2 wordt niet ondersteund op *Windows Server 2008 R2* of *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="c1dce-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span>
<span data-ttu-id="c1dce-124">Moet u catalogusversie 2 van de op *Windows 8*, *Windows Server 2012*, en latere besturingssystemen.</span><span class="sxs-lookup"><span data-stu-id="c1dce-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="c1dce-125">Hiermee maakt u het catalogusbestand.</span><span class="sxs-lookup"><span data-stu-id="c1dce-125">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="c1dce-126">Om te controleren of de integriteit van catalogusbestand (Pester.cat in bovenstaande voorbeeld), meld u aan met behulp van [Set AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1dce-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.</span></span>

### <a name="test-filecatalog"></a><span data-ttu-id="c1dce-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="c1dce-127">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="c1dce-128">Test-FileCatalog valideert de catalogus voor een set van mappen.</span><span class="sxs-lookup"><span data-stu-id="c1dce-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="c1dce-129">Deze cmdlet worden alle bestanden-hashes vergeleken en hun relatieve paden te vinden *catalogus* met resources op *schijf*.</span><span class="sxs-lookup"><span data-stu-id="c1dce-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span>
<span data-ttu-id="c1dce-130">Als er overeenkomende bestands-hashes en paden gedetecteerd wordt de status als *ValidationFailed*.</span><span class="sxs-lookup"><span data-stu-id="c1dce-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span>
<span data-ttu-id="c1dce-131">Gebruikers kunnen al deze gegevens ophalen met behulp van de *-gedetailleerde* parameter.</span><span class="sxs-lookup"><span data-stu-id="c1dce-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span>
<span data-ttu-id="c1dce-132">Er wordt ook weergegeven ondertekenings status van de catalogus in *handtekening* eigenschap die gelijk is aan het aanroepen [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet uit op de catalog-bestand.</span><span class="sxs-lookup"><span data-stu-id="c1dce-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet on the catalog file.</span></span>
<span data-ttu-id="c1dce-133">Gebruikers kunnen ook een bestand tijdens de validatie overslaan met behulp van de *- FilesToSkip* parameter.</span><span class="sxs-lookup"><span data-stu-id="c1dce-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

## <a name="module-analysis-cache"></a><span data-ttu-id="c1dce-134">Module Analysis Cache</span><span class="sxs-lookup"><span data-stu-id="c1dce-134">Module Analysis Cache</span></span>

<span data-ttu-id="c1dce-135">Beginnen met WMF 5.1, biedt PowerShell controle over het bestand dat wordt gebruikt om cachegegevens over een module, zoals de opdrachten die zijn geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="c1dce-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="c1dce-136">Standaard worden deze cache wordt opgeslagen in het bestand `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="c1dce-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="c1dce-137">De cache doorgaans bij het opstarten tijdens het zoeken naar een opdracht wordt gelezen en geschreven op een achtergrond-thread enige tijd opnieuw uit nadat een module is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="c1dce-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="c1dce-138">Als u wilt de standaardlocatie van de cache wijzigen, stelt de `$env:PSModuleAnalysisCachePath` omgevingsvariabele voordat u begint met PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1dce-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span>
<span data-ttu-id="c1dce-139">Wijzigingen in deze omgevingsvariabele wordt alleen van invloed op de onderliggende processen.</span><span class="sxs-lookup"><span data-stu-id="c1dce-139">Changes to this environment variable will only affect children processes.</span></span>
<span data-ttu-id="c1dce-140">De waarde moet een naam een volledig pad (inclusief bestandsnaam) zijn dat PowerShell gemachtigd is om het maken en bestanden te schrijven.</span><span class="sxs-lookup"><span data-stu-id="c1dce-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>
<span data-ttu-id="c1dce-141">Als u wilt uitschakelen bestandscache, deze waarde instelt op een ongeldige locatie, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="c1dce-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="c1dce-142">Hiermee stelt het pad naar een ongeldige apparaatnaam.</span><span class="sxs-lookup"><span data-stu-id="c1dce-142">This sets the path to an invalid device.</span></span>
<span data-ttu-id="c1dce-143">Als PowerShell kan niet naar het pad schrijven, er wordt geen fout wordt geretourneerd, maar u kunt zien die fouten rapporteren met behulp van een traceringstoken:</span><span class="sxs-lookup"><span data-stu-id="c1dce-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="c1dce-144">Bij het schrijven van de cache wordt PowerShell-modules die niet meer aanwezig zijn om te voorkomen dat een onnodig groot cache controleren.</span><span class="sxs-lookup"><span data-stu-id="c1dce-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="c1dce-145">Soms zijn deze controles niet wenselijk in dat geval kunt u deze uitschakelen door in te stellen:</span><span class="sxs-lookup"><span data-stu-id="c1dce-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="c1dce-146">Instellen van deze omgevingsvariabele wordt onmiddellijk van kracht in het huidige proces.</span><span class="sxs-lookup"><span data-stu-id="c1dce-146">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="c1dce-147">Moduleversie opgeven</span><span class="sxs-lookup"><span data-stu-id="c1dce-147">Specifying module version</span></span>

<span data-ttu-id="c1dce-148">In WMF 5.1, `using module` gedrag net als andere constructies met betrekking tot module in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c1dce-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="c1dce-149">Voorheen moest u geen enkele manier om op te geven van een bepaalde moduleversie; Als er meerdere versies aanwezig waren, dit heeft een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="c1dce-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="c1dce-150">In WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="c1dce-150">In WMF 5.1:</span></span>

- <span data-ttu-id="c1dce-151">U kunt [ModuleSpecification Constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="c1dce-151">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="c1dce-152">Deze hashtabel heeft dezelfde indeling als `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="c1dce-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="c1dce-153">**Voorbeeld:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="c1dce-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="c1dce-154">Als er meerdere versies van de module, PowerShell wordt gebruikt de **dezelfde resolutie logica** als `Import-Module` en niet een plaatsingsfout--hetzelfde gedrag als `Import-Module` en `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="c1dce-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="c1dce-155">Verbeteringen voor lastige</span><span class="sxs-lookup"><span data-stu-id="c1dce-155">Improvements to Pester</span></span>

<span data-ttu-id="c1dce-156">In WMF 5.1, de versie van Pester die wordt geleverd met PowerShell is bijgewerkt van 3.3.5 naar 3.4.0, met de toevoeging van het doorvoeren https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, die zorgt voor een betere gedrag voor Pester op Nano Server.</span><span class="sxs-lookup"><span data-stu-id="c1dce-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="c1dce-157">U kunt de wijzigingen in versie 3.3.5-3.4.0 bekijken door te inspecteren van het bestand ChangeLog.md op: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="c1dce-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>
