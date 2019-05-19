---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Opmerkingen bij de Release van de WMF 5.x
ms.openlocfilehash: 8bdc423234cf0b104b72b1bee1de35e50783d8a4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856397"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="040cd-103">Windows Management Framework (WMF) 5.x Release Notes</span><span class="sxs-lookup"><span data-stu-id="040cd-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="040cd-104">WMF 5.0 wordt gewijzigd</span><span class="sxs-lookup"><span data-stu-id="040cd-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="040cd-105">PowerShell 5.0 voegt een nieuwe gestructureerde **informatie** stream</span><span class="sxs-lookup"><span data-stu-id="040cd-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="040cd-106">Verbeteringen aan DSC, met inbegrip van vier nieuwe DSC-resources:</span><span class="sxs-lookup"><span data-stu-id="040cd-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="040cd-107">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="040cd-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="040cd-108">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="040cd-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="040cd-109">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="040cd-109">ServiceSet</span></span>
  - <span data-ttu-id="040cd-110">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="040cd-110">ProcessSet</span></span>
- <span data-ttu-id="040cd-111">Toegevoegde Just Enough Administration om in te schakelen op rollen gebaseerd beheer via externe communicatie van PowerShell</span><span class="sxs-lookup"><span data-stu-id="040cd-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="040cd-112">PowerShell 5.0 breidt de taal om op te nemen van de gebruiker gedefinieerde klassen en opsommingen</span><span class="sxs-lookup"><span data-stu-id="040cd-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="040cd-113">Verbeterde functies in PowerShell ISE en extra foutopsporing op afstand foutopsporing</span><span class="sxs-lookup"><span data-stu-id="040cd-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="040cd-114">De PowerShellGet en PackageManagement-modules toegevoegd</span><span class="sxs-lookup"><span data-stu-id="040cd-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="040cd-115">Uitgebreide logboekregistratie voor PowerShell-script en transcripties</span><span class="sxs-lookup"><span data-stu-id="040cd-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="040cd-116">Cmdlets voor Cryptographic Message-syntaxis toevoegen</span><span class="sxs-lookup"><span data-stu-id="040cd-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="040cd-117">WMF 5.0 bevat de NetworkSwitchManager-module voor Windows</span><span class="sxs-lookup"><span data-stu-id="040cd-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="040cd-118">De module Microsoft.PowerShell.ODataUtils toegevoegd</span><span class="sxs-lookup"><span data-stu-id="040cd-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="040cd-119">Er is ondersteuning toegevoegd voor Software Inventory Logging (SIL)</span><span class="sxs-lookup"><span data-stu-id="040cd-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="040cd-120">Nieuwe server of -cmdlets in reactie op aanvragen van gebruikers en problemen bijwerken</span><span class="sxs-lookup"><span data-stu-id="040cd-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="040cd-121">WMF 5.1 wordt gewijzigd</span><span class="sxs-lookup"><span data-stu-id="040cd-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="040cd-122">WMF 5.1 omvat de PowerShell-, WMI-, WinRM- en Software Inventory Logging (SIL)-onderdelen die zijn uitgebracht met Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="040cd-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="040cd-123">WMF 5.1 kan worden geïnstalleerd op Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 en 2012 R2, en biedt verschillende verbeteringen ten opzichte van WMF 5.0 met inbegrip van:</span><span class="sxs-lookup"><span data-stu-id="040cd-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="040cd-124">Er zijn nieuwe cmdlets</span><span class="sxs-lookup"><span data-stu-id="040cd-124">New cmdlets</span></span>
- <span data-ttu-id="040cd-125">PowerShellGet-verbeteringen, waaronder het afdwingen van ondertekende modules en het installeren van JEA-modules</span><span class="sxs-lookup"><span data-stu-id="040cd-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="040cd-126">Ondersteuning in PackageManagement toegevoegd voor Containers, CBS Setup, EXE-installatie en CAB-pakketten</span><span class="sxs-lookup"><span data-stu-id="040cd-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="040cd-127">Verbeteringen in foutopsporing voor DSC- en PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="040cd-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="040cd-128">Beveiligingsverbeteringen, waaronder de handhaving van door catalogus ondertekende modules die afkomstig zijn van de pull-server, gebruikt in combinatie met PowerShellGet-cmdlets</span><span class="sxs-lookup"><span data-stu-id="040cd-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="040cd-129">Antwoorden op een aantal gebruikersaanvragen en -problemen</span><span class="sxs-lookup"><span data-stu-id="040cd-129">Responses to a number of user requests and issues</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="040cd-130">PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="040cd-130">PowerShell Editions</span></span>

<span data-ttu-id="040cd-131">Vanaf versie 5.1 is is PowerShell beschikbaar in de verschillende edities, op basis van verschillende functies en platformcompatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="040cd-131">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="040cd-132">**Desktop-editie:** Gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Server Core- en Windows Desktop volledige footprint.</span><span class="sxs-lookup"><span data-stu-id="040cd-132">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="040cd-133">**Core-editie:** Gebaseerd op .NET Core en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows, zoals Nano Server en Windows IoT verminderde footprint.</span><span class="sxs-lookup"><span data-stu-id="040cd-133">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="040cd-134">Meer informatie over het gebruik van PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="040cd-134">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="040cd-135">Actieve editie van PowerShell met behulp van $PSVersionTable bepalen</span><span class="sxs-lookup"><span data-stu-id="040cd-135">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="040cd-136">Resultaten van de Get-Module door met de parameter PSEdition CompatiblePSEditions te filteren</span><span class="sxs-lookup"><span data-stu-id="040cd-136">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="040cd-137">Scriptuitvoering wordt voorkomen tenzij uitvoert op een compatibele versie van PowerShell</span><span class="sxs-lookup"><span data-stu-id="040cd-137">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="040cd-138">Declareer de compatibiliteit van een module met specifieke versies van PowerShell</span><span class="sxs-lookup"><span data-stu-id="040cd-138">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="040cd-139">Module Analysis Cache</span><span class="sxs-lookup"><span data-stu-id="040cd-139">Module Analysis Cache</span></span>

<span data-ttu-id="040cd-140">Beginnen met WMF 5.1, biedt PowerShell controle over het bestand dat wordt gebruikt om cachegegevens over een module, zoals de opdrachten die zijn geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="040cd-140">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="040cd-141">Standaard worden deze cache wordt opgeslagen in het bestand `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="040cd-141">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="040cd-142">De cache doorgaans bij het opstarten tijdens het zoeken naar een opdracht wordt gelezen en geschreven op een achtergrond-thread enige tijd opnieuw uit nadat een module is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="040cd-142">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="040cd-143">Als u wilt de standaardlocatie van de cache wijzigen, stelt de `$env:PSModuleAnalysisCachePath` omgevingsvariabele voordat u begint met PowerShell.</span><span class="sxs-lookup"><span data-stu-id="040cd-143">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="040cd-144">Wijzigingen in deze omgevingsvariabele wordt alleen van invloed op de onderliggende processen.</span><span class="sxs-lookup"><span data-stu-id="040cd-144">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="040cd-145">De waarde moet een naam een volledig pad (inclusief bestandsnaam) zijn dat PowerShell gemachtigd is om het maken en bestanden te schrijven.</span><span class="sxs-lookup"><span data-stu-id="040cd-145">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="040cd-146">Als u wilt uitschakelen bestandscache, deze waarde instelt op een ongeldige locatie, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="040cd-146">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="040cd-147">Hiermee stelt het pad naar een ongeldige apparaatnaam.</span><span class="sxs-lookup"><span data-stu-id="040cd-147">This sets the path to an invalid device.</span></span> <span data-ttu-id="040cd-148">Als PowerShell kan niet naar het pad schrijven, er wordt geen fout wordt geretourneerd, maar u kunt zien die fouten rapporteren met behulp van een traceringstoken:</span><span class="sxs-lookup"><span data-stu-id="040cd-148">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="040cd-149">Bij het schrijven van de cache wordt PowerShell-modules die niet meer aanwezig zijn om te voorkomen dat een onnodig groot cache controleren.</span><span class="sxs-lookup"><span data-stu-id="040cd-149">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="040cd-150">Soms zijn deze controles niet wenselijk in dat geval kunt u deze uitschakelen door in te stellen:</span><span class="sxs-lookup"><span data-stu-id="040cd-150">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="040cd-151">Instellen van deze omgevingsvariabele wordt onmiddellijk van kracht in het huidige proces.</span><span class="sxs-lookup"><span data-stu-id="040cd-151">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="040cd-152">Moduleversie opgeven</span><span class="sxs-lookup"><span data-stu-id="040cd-152">Specifying module version</span></span>

<span data-ttu-id="040cd-153">In WMF 5.1, `using module` gedrag net als andere constructies met betrekking tot module in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="040cd-153">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="040cd-154">Voorheen moest u geen enkele manier om op te geven van een bepaalde moduleversie; Als er meerdere versies aanwezig waren, dit heeft een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="040cd-154">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="040cd-155">In WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="040cd-155">In WMF 5.1:</span></span>

- <span data-ttu-id="040cd-156">U kunt [ModuleSpecification Constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="040cd-156">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
  <span data-ttu-id="040cd-157">Deze hashtabel heeft dezelfde indeling als `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="040cd-157">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="040cd-158">**Voorbeeld:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="040cd-158">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="040cd-159">Als er meerdere versies van de module, PowerShell wordt gebruikt de **dezelfde resolutie logica** als `Import-Module` en niet een plaatsingsfout--hetzelfde gedrag als `Import-Module` en `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="040cd-159">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="040cd-160">Verbeteringen voor lastige</span><span class="sxs-lookup"><span data-stu-id="040cd-160">Improvements to Pester</span></span>

<span data-ttu-id="040cd-161">In WMF 5.1, is de versie van Pester die wordt geleverd met PowerShell uit 3.3.5 bijgewerkt naar 3.4.0.</span><span class="sxs-lookup"><span data-stu-id="040cd-161">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="040cd-162">Deze update kunt beter gedrag voor Pester op Nano Server.</span><span class="sxs-lookup"><span data-stu-id="040cd-162">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="040cd-163">U kunt de wijzigingen in het kader van bestrijding bekijken door te inspecteren de [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in de GitHub-opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="040cd-163">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>
