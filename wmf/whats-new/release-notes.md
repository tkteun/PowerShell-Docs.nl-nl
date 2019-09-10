---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Opmerkingen bij de WMF 5.x-release
ms.openlocfilehash: 8924240a4bbedcd34bc68b7cacdd23189a3716d6
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848154"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="3eacc-103">Opmerkingen bij de release van Windows Management Framework (WMF) 5. x</span><span class="sxs-lookup"><span data-stu-id="3eacc-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="3eacc-104">WMF 5,0-wijzigingen</span><span class="sxs-lookup"><span data-stu-id="3eacc-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="3eacc-105">Power shell 5,0 voegt een nieuwe gestructureerde **informatie** stroom toe</span><span class="sxs-lookup"><span data-stu-id="3eacc-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="3eacc-106">Verbeteringen in DSC, met inbegrip van vier nieuwe DSC-resources:</span><span class="sxs-lookup"><span data-stu-id="3eacc-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="3eacc-107">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="3eacc-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="3eacc-108">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="3eacc-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="3eacc-109">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="3eacc-109">ServiceSet</span></span>
  - <span data-ttu-id="3eacc-110">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="3eacc-110">ProcessSet</span></span>
- <span data-ttu-id="3eacc-111">Er is net genoeg beheer toegevoegd om op rollen gebaseerd beheer via externe communicatie van Power shell in te scha kelen</span><span class="sxs-lookup"><span data-stu-id="3eacc-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="3eacc-112">Power shell 5,0 breidt de taal uit voor het toevoegen van door de gebruiker gedefinieerde klassen en inventarisaties</span><span class="sxs-lookup"><span data-stu-id="3eacc-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="3eacc-113">Verbeterde functies voor fout opsporing in Power shell ISE en het toevoegen van externe fout opsporing</span><span class="sxs-lookup"><span data-stu-id="3eacc-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="3eacc-114">De modules PowerShellGet en Package Management zijn toegevoegd</span><span class="sxs-lookup"><span data-stu-id="3eacc-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="3eacc-115">Verbeterde logboek registratie en transcripten van Power shell-scripts</span><span class="sxs-lookup"><span data-stu-id="3eacc-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="3eacc-116">Syntaxis-cmdlets voor cryptografische berichten toevoegen</span><span class="sxs-lookup"><span data-stu-id="3eacc-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="3eacc-117">WMF 5,0 bevat de NetworkSwitchManager-module voor Windows</span><span class="sxs-lookup"><span data-stu-id="3eacc-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="3eacc-118">De module micro soft. Power shell. ODataUtils is toegevoegd</span><span class="sxs-lookup"><span data-stu-id="3eacc-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="3eacc-119">Er is ondersteuning toegevoegd voor logboek registratie van software-inventaris (SIL)</span><span class="sxs-lookup"><span data-stu-id="3eacc-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="3eacc-120">Nieuwe of update-cmdlets in reactie op gebruikers aanvragen en problemen</span><span class="sxs-lookup"><span data-stu-id="3eacc-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="3eacc-121">WMF 5,1-wijzigingen</span><span class="sxs-lookup"><span data-stu-id="3eacc-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="3eacc-122">WMF 5,1 bevat de onderdelen van Power shell, WMI, WinRM en Software Inventory logging (SIL) die zijn uitgebracht met Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="3eacc-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="3eacc-123">WMF 5,1 kan worden geïnstalleerd op Windows 7, Windows 8,1, Windows Server 2008 R2, 2012 en 2012 R2, en biedt verschillende verbeteringen ten opzichte van WMF-5,0, waaronder:</span><span class="sxs-lookup"><span data-stu-id="3eacc-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="3eacc-124">Nieuwe cmdlets</span><span class="sxs-lookup"><span data-stu-id="3eacc-124">New cmdlets</span></span>
- <span data-ttu-id="3eacc-125">PowerShellGet-verbeteringen, waaronder het afdwingen van ondertekende modules en het installeren van JEA-modules</span><span class="sxs-lookup"><span data-stu-id="3eacc-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="3eacc-126">Ondersteuning in PackageManagement toegevoegd voor Containers, CBS Setup, EXE-installatie en CAB-pakketten</span><span class="sxs-lookup"><span data-stu-id="3eacc-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="3eacc-127">Verbeteringen in foutopsporing voor DSC- en PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="3eacc-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="3eacc-128">Beveiligingsverbeteringen, waaronder de handhaving van door catalogus ondertekende modules die afkomstig zijn van de pull-server, gebruikt in combinatie met PowerShellGet-cmdlets</span><span class="sxs-lookup"><span data-stu-id="3eacc-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="3eacc-129">Antwoorden op een aantal gebruikersaanvragen en -problemen</span><span class="sxs-lookup"><span data-stu-id="3eacc-129">Responses to a number of user requests and issues</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3eacc-130">Voordat u WMF 5,1 installeert op Windows Server 2008 of Windows 7, controleert u of WMF 3,0 niet is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="3eacc-130">Before you install WMF 5.1 on Windows Server 2008 or Windows 7, confirm that WMF 3.0 isn't installed.</span></span> <span data-ttu-id="3eacc-131">Zie voor meer informatie [WMF 5,1-vereisten voor Windows Server 2008 R2 SP1 en Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).</span><span class="sxs-lookup"><span data-stu-id="3eacc-131">For more information, see [WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="3eacc-132">PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="3eacc-132">PowerShell Editions</span></span>

<span data-ttu-id="3eacc-133">Vanaf versie 5,1 is Power shell beschikbaar in verschillende edities waarin verschillende functie sets en platform compatibiliteit worden aangegeven.</span><span class="sxs-lookup"><span data-stu-id="3eacc-133">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="3eacc-134">**Desktop Edition:** Gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van Power shell die worden uitgevoerd op edities van Windows met een volledige footprint, zoals Server Core en Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="3eacc-134">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="3eacc-135">**Core-editie:** Gebaseerd op .NET core en biedt compatibiliteit met scripts en modules die zijn gericht op versies van Power shell die worden uitgevoerd op edities van Windows met een verminderde footprint, zoals nano server en Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="3eacc-135">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="3eacc-136">Meer informatie over het gebruik van Power shell-edities</span><span class="sxs-lookup"><span data-stu-id="3eacc-136">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="3eacc-137">De actieve editie van Power shell bepalen met behulp van $PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="3eacc-137">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="3eacc-138">Get-module resultaten filteren op CompatiblePSEditions met behulp van de PSEdition-para meter</span><span class="sxs-lookup"><span data-stu-id="3eacc-138">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="3eacc-139">Uitvoering van scripts voor komen tenzij uitgevoerd op een compatibele editie van Power shell</span><span class="sxs-lookup"><span data-stu-id="3eacc-139">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="3eacc-140">De compatibiliteit van een module met specifieke Power shell-versies declareren</span><span class="sxs-lookup"><span data-stu-id="3eacc-140">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="3eacc-141">Module analyse cache</span><span class="sxs-lookup"><span data-stu-id="3eacc-141">Module Analysis Cache</span></span>

<span data-ttu-id="3eacc-142">Vanaf WMF 5,1 biedt Power shell controle over het bestand dat wordt gebruikt voor het opslaan van gegevens over een module, zoals de opdrachten die worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="3eacc-142">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="3eacc-143">Deze cache wordt standaard opgeslagen in het bestand `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="3eacc-143">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="3eacc-144">De cache wordt doorgaans tijdens het opstarten gelezen tijdens het zoeken naar een opdracht en wordt ergens op een achtergrond thread geschreven nadat een module is geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="3eacc-144">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="3eacc-145">Als u de standaard locatie van de cache wilt wijzigen, `$env:PSModuleAnalysisCachePath` stelt u de omgevings variabele in voordat u Power shell start.</span><span class="sxs-lookup"><span data-stu-id="3eacc-145">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="3eacc-146">Wijzigingen aan deze omgevings variabele worden alleen toegepast op onderliggende processen.</span><span class="sxs-lookup"><span data-stu-id="3eacc-146">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="3eacc-147">De waarde moet een volledig pad (inclusief bestands naam) zijn dat Power shell toestemming heeft om bestanden te maken en te schrijven.</span><span class="sxs-lookup"><span data-stu-id="3eacc-147">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="3eacc-148">Als u de bestands cache wilt uitschakelen, stelt u deze waarde in op een ongeldige locatie, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="3eacc-148">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="3eacc-149">Hiermee stelt u het pad naar een ongeldig apparaat in.</span><span class="sxs-lookup"><span data-stu-id="3eacc-149">This sets the path to an invalid device.</span></span> <span data-ttu-id="3eacc-150">Als Power shell het pad niet kan schrijven, wordt er geen fout geretourneerd, maar u kunt fout rapportage zien met behulp van een tracering:</span><span class="sxs-lookup"><span data-stu-id="3eacc-150">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="3eacc-151">Wanneer u de cache afschrijft, controleert Power shell op modules die niet meer bestaan om een onnodig grote cache te voor komen.</span><span class="sxs-lookup"><span data-stu-id="3eacc-151">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="3eacc-152">Soms zijn deze controles niet gewenst, in welk geval u ze kunt uitschakelen door het volgende in te stellen:</span><span class="sxs-lookup"><span data-stu-id="3eacc-152">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="3eacc-153">Het instellen van deze omgevings variabele wordt direct van kracht in het huidige proces.</span><span class="sxs-lookup"><span data-stu-id="3eacc-153">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="3eacc-154">Module versie opgeven</span><span class="sxs-lookup"><span data-stu-id="3eacc-154">Specifying module version</span></span>

<span data-ttu-id="3eacc-155">In WMF 5,1 `using module` gedraagt zich op dezelfde manier als andere module constructies in Power shell.</span><span class="sxs-lookup"><span data-stu-id="3eacc-155">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="3eacc-156">U had eerder geen manier om een bepaalde module versie op te geven. Als er meerdere versies aanwezig zijn, resulteert dit in een fout.</span><span class="sxs-lookup"><span data-stu-id="3eacc-156">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="3eacc-157">In WMF 5,1:</span><span class="sxs-lookup"><span data-stu-id="3eacc-157">In WMF 5.1:</span></span>

- <span data-ttu-id="3eacc-158">U kunt de [ModuleSpecification-constructor (hashtabel)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3eacc-158">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

  <span data-ttu-id="3eacc-159">Deze hash-tabel heeft dezelfde indeling als `Get-Module -FullyQualifiedName`.</span><span class="sxs-lookup"><span data-stu-id="3eacc-159">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="3eacc-160">**Voor beeld:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="3eacc-160">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="3eacc-161">Als er meerdere versies van de module zijn, maakt Power shell gebruik van **dezelfde oplossings logica** als `Import-Module` en wordt er geen fout geretourneerd-- `Import-Module` hetzelfde `Import-DscResource`gedrag als en.</span><span class="sxs-lookup"><span data-stu-id="3eacc-161">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="3eacc-162">Verbeteringen aan de ziekte</span><span class="sxs-lookup"><span data-stu-id="3eacc-162">Improvements to Pester</span></span>

<span data-ttu-id="3eacc-163">In WMF 5,1 is de versie van de ziekte die wordt geleverd met Power shell, bijgewerkt van 3.3.5 naar 3.4.0.</span><span class="sxs-lookup"><span data-stu-id="3eacc-163">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="3eacc-164">Deze update zorgt voor een betere werking van een ziekte op nano server.</span><span class="sxs-lookup"><span data-stu-id="3eacc-164">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="3eacc-165">U kunt de wijzigingen in parasiet controleren door de [wijzigingen logboek](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in de GitHub-opslag plaats te controleren.</span><span class="sxs-lookup"><span data-stu-id="3eacc-165">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>
