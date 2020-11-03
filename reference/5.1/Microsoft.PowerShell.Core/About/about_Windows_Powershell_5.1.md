---
description: Hierin worden nieuwe functies beschreven die zijn opgenomen in Windows Power shell 5,1.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/17/2018
online version: https://docs.microsoft.com/powershell/module/?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_5.1
ms.openlocfilehash: 567af048dd137c0287c6eba4ccc42a77055c0c92
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253156"
---
# <a name="about_windows_powershell_51"></a><span data-ttu-id="4958b-104">about_Windows_PowerShell_5.1</span><span class="sxs-lookup"><span data-stu-id="4958b-104">about_Windows_PowerShell_5.1</span></span>

## <a name="short-description"></a><span data-ttu-id="4958b-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4958b-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="4958b-106">Hierin worden nieuwe functies beschreven die zijn opgenomen in Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="4958b-106">Describes new features that are included in Windows PowerShell 5.1.</span></span>

## <a name="long-description"></a><span data-ttu-id="4958b-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4958b-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="4958b-108">Windows Power shell 5,1 bevat belang rijke nieuwe functies die het gebruik ervan uitbreiden, de bruikbaarheid verbeteren en u in staat stellen om op Windows gebaseerde omgevingen eenvoudiger en uitgebreid te beheren.</span><span class="sxs-lookup"><span data-stu-id="4958b-108">Windows PowerShell 5.1 includes significant new features that extend its use, improve its usability, and allow you to control and manage Windows-based environments more easily and comprehensively.</span></span>

<span data-ttu-id="4958b-109">Windows Power shell 5,1 is achterwaarts compatibel.</span><span class="sxs-lookup"><span data-stu-id="4958b-109">Windows PowerShell 5.1 is backward-compatible.</span></span> <span data-ttu-id="4958b-110">Cmdlets, providers, modules, invoeg toepassingen, scripts, functies en profielen die zijn ontworpen voor Windows Power Shell 4,0, Windows Power Shell 3,0 en Windows Power Shell 2,0, werken doorgaans in Windows Power shell 5,1 zonder wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="4958b-110">Cmdlets, providers, modules, snap-ins, scripts, functions, and profiles that were designed for Windows PowerShell 4.0, Windows PowerShell 3.0, and Windows PowerShell 2.0 generally work in Windows PowerShell 5.1 without changes.</span></span>

- <span data-ttu-id="4958b-111">Nieuwe cmdlets: lokale gebruikers en groepen; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="4958b-111">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="4958b-112">PowerShellGet-verbeteringen, waaronder het afdwingen van ondertekende modules en het installeren van JEA-modules</span><span class="sxs-lookup"><span data-stu-id="4958b-112">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="4958b-113">Ondersteuning in PackageManagement toegevoegd voor Containers, CBS Setup, EXE-installatie en CAB-pakketten</span><span class="sxs-lookup"><span data-stu-id="4958b-113">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="4958b-114">Verbeteringen in foutopsporing voor DSC- en PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="4958b-114">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="4958b-115">Beveiligingsverbeteringen, waaronder de handhaving van door catalogus ondertekende modules die afkomstig zijn van de pull-server, gebruikt in combinatie met PowerShellGet-cmdlets</span><span class="sxs-lookup"><span data-stu-id="4958b-115">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="4958b-116">Antwoorden op een aantal gebruikersaanvragen en -problemen</span><span class="sxs-lookup"><span data-stu-id="4958b-116">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="4958b-117">Windows Power shell 5,1 wordt standaard geïnstalleerd op Windows Server 2016 en Windows 10.</span><span class="sxs-lookup"><span data-stu-id="4958b-117">Windows PowerShell 5.1 is installed by default on Windows Server 2016 and Windows 10.</span></span> <span data-ttu-id="4958b-118">Zie [WMF-5,1 installeren en configureren](/powershell/scripting/wmf/setup/install-configure)als u Windows power shell 5,1 wilt installeren op windows server 2012 R2, Windows 8,1 ENTER prise of Windows 8,1 Pro.</span><span class="sxs-lookup"><span data-stu-id="4958b-118">To install Windows PowerShell 5.1 on Windows Server 2012 R2, Windows 8.1 Enterprise, or Windows 8.1 Pro, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>
<span data-ttu-id="4958b-119">Lees de Download gegevens en zorg ervoor dat aan alle systeem vereisten wordt voldaan voordat u Windows Management Framework 5,1 installeert.</span><span class="sxs-lookup"><span data-stu-id="4958b-119">Be sure to read the download details, and meet all system requirements, before you install Windows Management Framework 5.1.</span></span>

<span data-ttu-id="4958b-120">U kunt ook lezen over wijzigingen in Windows Power shell 5,1 in [Wat is er nieuw in Windows Power shell](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50).</span><span class="sxs-lookup"><span data-stu-id="4958b-120">You can also read about changes to Windows PowerShell 5.1 in [What's New in Windows PowerShell](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50).</span></span>

## <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="4958b-121">Nieuwe Scenario's en functies in WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="4958b-121">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="4958b-122">Opmerking: deze informatie is voorlopig en kan worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="4958b-122">Note: This information is preliminary and subject to change.</span></span>

### <a name="powershell-editions"></a><span data-ttu-id="4958b-123">PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="4958b-123">PowerShell Editions</span></span>
<span data-ttu-id="4958b-124">Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="4958b-124">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="4958b-125">**Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="4958b-125">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="4958b-126">**Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="4958b-126">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="4958b-127">**Meer informatie over het gebruik van Power shell-edities**</span><span class="sxs-lookup"><span data-stu-id="4958b-127">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="4958b-128">De actieve editie van Power shell bepalen met behulp van $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="4958b-128">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="4958b-129">Get-Module resultaten filteren op CompatiblePSEditions met behulp van de PSEdition-para meter</span><span class="sxs-lookup"><span data-stu-id="4958b-129">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="4958b-130">Uitvoering van scripts voor komen tenzij uitgevoerd op een compatibele editie van Power shell</span><span class="sxs-lookup"><span data-stu-id="4958b-130">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/scripting/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="4958b-131">De compatibiliteit van een module met specifieke Power shell-versies declareren</span><span class="sxs-lookup"><span data-stu-id="4958b-131">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

### <a name="catalog-cmdlets"></a><span data-ttu-id="4958b-132">Catalogus-cmdlets</span><span class="sxs-lookup"><span data-stu-id="4958b-132">Catalog Cmdlets</span></span>

<span data-ttu-id="4958b-133">Er zijn twee nieuwe cmdlets toegevoegd in de module [micro soft. Power shell. Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) . Deze genereren en valideren Windows-catalogus bestanden.</span><span class="sxs-lookup"><span data-stu-id="4958b-133">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) module; these generate and validate Windows catalog files.</span></span>

#### <a name="new-filecatalog"></a><span data-ttu-id="4958b-134">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="4958b-134">New-FileCatalog</span></span>

<span data-ttu-id="4958b-135">New-FileCatalog maakt een Windows-catalogus bestand voor een set mappen en bestanden.</span><span class="sxs-lookup"><span data-stu-id="4958b-135">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="4958b-136">Dit catalogus bestand bevat hashes voor alle bestanden in opgegeven paden.</span><span class="sxs-lookup"><span data-stu-id="4958b-136">This catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="4958b-137">Gebruikers kunnen de set mappen distribueren samen met het bijbehorende catalogus bestand dat deze mappen vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="4958b-137">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span> <span data-ttu-id="4958b-138">Deze informatie is nuttig om te controleren of er wijzigingen zijn aangebracht in de mappen sinds de aanmaak tijd van de catalogus.</span><span class="sxs-lookup"><span data-stu-id="4958b-138">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>]
 [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="4958b-139">Catalogus versies 1 en 2 worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="4958b-139">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="4958b-140">Versie 1 maakt gebruik van het SHA1-hash-algoritme om bestands-hashes te maken. versie 2 maakt gebruik van SHA256.</span><span class="sxs-lookup"><span data-stu-id="4958b-140">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span> <span data-ttu-id="4958b-141">Catalogus versie 2 wordt niet ondersteund in *Windows Server 2008 R2* of *Windows 7*.</span><span class="sxs-lookup"><span data-stu-id="4958b-141">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span> <span data-ttu-id="4958b-142">U moet Catalog versie 2 gebruiken voor *Windows 8* , *Windows Server 2012* en latere besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="4958b-142">You should use catalog version 2 on *Windows 8* , *Windows Server 2012* , and later operating systems.</span></span>

<span data-ttu-id="4958b-143">Als u de integriteit van het catalogus bestand (Pester.cat in het bovenstaande voor beeld) wilt controleren, moet u dit ondertekenen met de cmdlet [set-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature) .</span><span class="sxs-lookup"><span data-stu-id="4958b-143">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature) cmdlet.</span></span>

#### <a name="test-filecatalog"></a><span data-ttu-id="4958b-144">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="4958b-144">Test-FileCatalog</span></span>

<span data-ttu-id="4958b-145">Test-FileCatalog valideert de catalogus die een set mappen vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="4958b-145">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>]
 [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="4958b-146">Met deze cmdlet worden alle bestanden-hashes en hun relatieve paden gevonden die in de *catalogus* met die op *schijf* zijn aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="4958b-146">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span> <span data-ttu-id="4958b-147">Als wordt gedetecteerd dat de bestands-hashes en de paden niet overeenkomen, wordt de status als *ValidationFailed* geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4958b-147">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span> <span data-ttu-id="4958b-148">Gebruikers kunnen al deze gegevens ophalen met behulp van de *-gedetailleerde* para meter.</span><span class="sxs-lookup"><span data-stu-id="4958b-148">Users can retrieve all this information by using the *-Detailed* parameter.</span></span> <span data-ttu-id="4958b-149">Ook wordt de status van de ondertekening weer gegeven in de *handtekening* eigenschap, die gelijk is aan het aanroepen van de cmdlet [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) in het catalogus bestand.</span><span class="sxs-lookup"><span data-stu-id="4958b-149">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) cmdlet on the catalog file.</span></span> <span data-ttu-id="4958b-150">Gebruikers kunnen ook bestanden overs Laan tijdens de validatie met behulp van de para meter *-FilesToSkip* .</span><span class="sxs-lookup"><span data-stu-id="4958b-150">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

### <a name="module-analysis-cache"></a><span data-ttu-id="4958b-151">Module analyse cache</span><span class="sxs-lookup"><span data-stu-id="4958b-151">Module Analysis Cache</span></span>

<span data-ttu-id="4958b-152">Vanaf WMF 5,1 biedt Power shell controle over het bestand dat wordt gebruikt voor het opslaan van gegevens over een module, zoals de opdrachten die worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="4958b-152">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="4958b-153">Deze cache wordt standaard opgeslagen in het bestand `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` .</span><span class="sxs-lookup"><span data-stu-id="4958b-153">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="4958b-154">De cache wordt doorgaans tijdens het opstarten gelezen tijdens het zoeken naar een opdracht en wordt ergens op een achtergrond thread geschreven nadat een module is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="4958b-154">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="4958b-155">Als u de standaard locatie van de cache wilt wijzigen, stelt u de `$env:PSModuleAnalysisCachePath` omgevings variabele in voordat u Power shell start.</span><span class="sxs-lookup"><span data-stu-id="4958b-155">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="4958b-156">Wijzigingen aan deze omgevings variabele worden alleen toegepast op onderliggende processen.</span><span class="sxs-lookup"><span data-stu-id="4958b-156">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="4958b-157">De waarde moet een volledig pad (inclusief bestands naam) zijn dat Power shell toestemming heeft om bestanden te maken en te schrijven.</span><span class="sxs-lookup"><span data-stu-id="4958b-157">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="4958b-158">Als u de bestands cache wilt uitschakelen, stelt u deze waarde in op een ongeldige locatie, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="4958b-158">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="4958b-159">Hiermee stelt u het pad naar een ongeldig apparaat in.</span><span class="sxs-lookup"><span data-stu-id="4958b-159">This sets the path to an invalid device.</span></span> <span data-ttu-id="4958b-160">Als Power shell het pad niet kan schrijven, wordt er geen fout geretourneerd, maar u kunt fout rapportage zien met behulp van een tracering:</span><span class="sxs-lookup"><span data-stu-id="4958b-160">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression {
  Import-Module Microsoft.PowerShell.Management -Force
}
```

<span data-ttu-id="4958b-161">Wanneer u de cache afschrijft, controleert Power shell op modules die niet meer bestaan om een onnodig grote cache te voor komen.</span><span class="sxs-lookup"><span data-stu-id="4958b-161">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="4958b-162">Soms zijn deze controles niet gewenst, in welk geval u ze kunt uitschakelen door het volgende in te stellen:</span><span class="sxs-lookup"><span data-stu-id="4958b-162">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="4958b-163">Het instellen van deze omgevings variabele wordt direct van kracht in het huidige proces.</span><span class="sxs-lookup"><span data-stu-id="4958b-163">Setting this environment variable will take effect immediately in the current process.</span></span>

### <a name="specifying-module-version"></a><span data-ttu-id="4958b-164">Module versie opgeven</span><span class="sxs-lookup"><span data-stu-id="4958b-164">Specifying module version</span></span>

<span data-ttu-id="4958b-165">In WMF 5,1 `using module` gedraagt zich op dezelfde manier als andere module constructies in Power shell.</span><span class="sxs-lookup"><span data-stu-id="4958b-165">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span> <span data-ttu-id="4958b-166">U had eerder geen manier om een bepaalde module versie op te geven. Als er meerdere versies aanwezig zijn, resulteert dit in een fout.</span><span class="sxs-lookup"><span data-stu-id="4958b-166">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="4958b-167">In WMF 5,1:</span><span class="sxs-lookup"><span data-stu-id="4958b-167">In WMF 5.1:</span></span>

* <span data-ttu-id="4958b-168">U kunt de [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor)gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4958b-168">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor).</span></span>
  <span data-ttu-id="4958b-169">Deze hash-tabel heeft dezelfde indeling als `Get-Module -FullyQualifiedName` .</span><span class="sxs-lookup"><span data-stu-id="4958b-169">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="4958b-170">**Voor beeld:**`using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="4958b-170">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

* <span data-ttu-id="4958b-171">Als er meerdere versies van de module zijn, maakt Power shell gebruik van **dezelfde oplossings logica** als `Import-Module` en wordt er geen fout geretourneerd--hetzelfde gedrag als `Import-Module` en `Import-DscResource` .</span><span class="sxs-lookup"><span data-stu-id="4958b-171">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

### <a name="improvements-to-pester"></a><span data-ttu-id="4958b-172">Verbeteringen aan de ziekte</span><span class="sxs-lookup"><span data-stu-id="4958b-172">Improvements to Pester</span></span>

<span data-ttu-id="4958b-173">In WMF 5,1 is de versie van de ziekte die wordt geleverd met Power shell, bijgewerkt van 3.3.5 naar 3.4.0, met toevoeging van GitHub [PR # 484](https://github.com/pester/Pester/pull/484), waardoor het gedrag van de ziekte op nano server beter is.</span><span class="sxs-lookup"><span data-stu-id="4958b-173">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of GitHub [PR# 484](https://github.com/pester/Pester/pull/484), which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="4958b-174">U kunt de wijzigingen in versies 3.3.5 in 3.4.0 controleren door het ChangeLog.md-bestand te controleren op: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span><span class="sxs-lookup"><span data-stu-id="4958b-174">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>

## <a name="keywords"></a><span data-ttu-id="4958b-175">WOORD</span><span class="sxs-lookup"><span data-stu-id="4958b-175">KEYWORDS</span></span>

<span data-ttu-id="4958b-176">Wat is er nieuw in Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="4958b-176">What's New in Windows PowerShell 5.1</span></span>
