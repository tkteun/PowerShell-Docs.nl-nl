---
description: Package Management is een aggregator voor software pakket beheerders.
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 22f47d01063778fca4f51a534b15d485b3beee28
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705353"
---
# <a name="about-packagemanagement"></a><span data-ttu-id="81aa7-103">Over Package Management</span><span class="sxs-lookup"><span data-stu-id="81aa7-103">About PackageManagement</span></span>

## <a name="short-description"></a><span data-ttu-id="81aa7-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="81aa7-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="81aa7-105">Package Management is een aggregator voor software pakket beheerders.</span><span class="sxs-lookup"><span data-stu-id="81aa7-105">PackageManagement is an aggregator for software package managers.</span></span>

## <a name="long-description"></a><span data-ttu-id="81aa7-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="81aa7-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="81aa7-107">De functionaliteit van Package Management is geïntroduceerd in Windows Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="81aa7-107">PackageManagement functionality was introduced in Windows PowerShell 5.0.</span></span>

<span data-ttu-id="81aa7-108">Package Management is een geïntegreerde interface voor beheer systemen voor software pakketten; u kunt Package Management-cmdlets uitvoeren om software ontdekking-, installatie-en inventarisatie taken (SDII) uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="81aa7-108">PackageManagement is a unified interface for software package management systems; you can run PackageManagement cmdlets to perform software discovery, installation, and inventory (SDII) tasks.</span></span> <span data-ttu-id="81aa7-109">Ongeacht de onderliggende installatie technologie kunt u de algemene cmdlets uitvoeren in de package management-module om pakketten te zoeken, te installeren of te verwijderen; pakket opslagplaatsen toevoegen, verwijderen en opvragen; en query's uitvoeren op een computer om te bepalen welke software pakketten zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="81aa7-109">Regardless of the underlying installation technology, you can run the common cmdlets in the PackageManagement module to search for, install, or uninstall packages; add, remove, and query package repositories; and run queries on a computer to determine which software packages are installed.</span></span>

<span data-ttu-id="81aa7-110">Package Management ondersteunt een flexibel invoeg toepassings model dat ondersteuning biedt voor andere software pakket beheer systemen.</span><span class="sxs-lookup"><span data-stu-id="81aa7-110">PackageManagement supports a flexible plug-in model that enables support for other software package management systems.</span></span>

<span data-ttu-id="81aa7-111">De package management-module is opgenomen in Windows Power shell 5,0 en latere releases van Power shell en werkt op drie niveaus van de pakket beheer structuur: pakket providers, pakket bronnen en de pakketten zelf.</span><span class="sxs-lookup"><span data-stu-id="81aa7-111">The PackageManagement module is included with Windows PowerShell 5.0 and later releases of PowerShell, and works on three levels of package management structure: package providers, package sources, and the packages themselves.</span></span> <span data-ttu-id="81aa7-112">Laat ons enkele voor waarden definiëren:</span><span class="sxs-lookup"><span data-stu-id="81aa7-112">Let us define some terms:</span></span>

- <span data-ttu-id="81aa7-113">Pakket beheer: software pakketbeheersysteem.</span><span class="sxs-lookup"><span data-stu-id="81aa7-113">Package manager: Software package management system.</span></span> <span data-ttu-id="81aa7-114">In Package Management-voor waarden is dit een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="81aa7-114">In PackageManagement terms, this is a package provider.</span></span>
- <span data-ttu-id="81aa7-115">Pakket provider: Package Management term voor een pakket Manager.</span><span class="sxs-lookup"><span data-stu-id="81aa7-115">Package provider: PackageManagement term for a package manager.</span></span> <span data-ttu-id="81aa7-116">Voor beelden hiervan zijn Windows Installer, Choco lade en anderen.</span><span class="sxs-lookup"><span data-stu-id="81aa7-116">Examples can include Windows Installer, Chocolatey, and others.</span></span>
- <span data-ttu-id="81aa7-117">Pakket Bron: een URL, een lokale map of een gedeelde netwerkmap die u voor het configureren van pakket providers kunt gebruiken als opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="81aa7-117">Package source: A URL, local folder, or network shared folder that you configure package providers to use as a repository.</span></span>
- <span data-ttu-id="81aa7-118">Pakket: een stukje software dat een pakket provider beheert en dat is opgeslagen in een specifieke pakket bron.</span><span class="sxs-lookup"><span data-stu-id="81aa7-118">Package: A piece of software that a package provider manages, and that is stored in a specific package source.</span></span>

<span data-ttu-id="81aa7-119">De package management-module bevat de volgende cmdlets.</span><span class="sxs-lookup"><span data-stu-id="81aa7-119">The PackageManagement module includes the following cmdlets.</span></span> <span data-ttu-id="81aa7-120">Zie de [Package Management](/powershell/module/packagemanagement) -Help voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="81aa7-120">For more information, see the [PackageManagement](/powershell/module/packagemanagement) help.</span></span>

- <span data-ttu-id="81aa7-121">`Get-PackageProvider`: Retourneert een lijst met pakket providers die zijn verbonden met Package Management.</span><span class="sxs-lookup"><span data-stu-id="81aa7-121">`Get-PackageProvider`: Returns a list of package providers that are  connected to PackageManagement.</span></span>
- <span data-ttu-id="81aa7-122">`Get-PackageSource`: Hiermee wordt een lijst met pakket bronnen opgehaald die zijn geregistreerd voor een pakket provider.</span><span class="sxs-lookup"><span data-stu-id="81aa7-122">`Get-PackageSource`: Gets a list of package sources that are registered for a package provider.</span></span>
- <span data-ttu-id="81aa7-123">`Register-PackageSource`: Hiermee voegt u een pakket bron voor een opgegeven pakket provider toe.</span><span class="sxs-lookup"><span data-stu-id="81aa7-123">`Register-PackageSource`: Adds a package source for a specified package provider.</span></span>
- <span data-ttu-id="81aa7-124">`Set-PackageSource`: Hiermee stelt u eigenschappen in voor een bestaande pakket bron.</span><span class="sxs-lookup"><span data-stu-id="81aa7-124">`Set-PackageSource`: Sets properties on an existing package source.</span></span>
- <span data-ttu-id="81aa7-125">`Unregister-PackageSource`: Hiermee verwijdert u een geregistreerde pakket bron.</span><span class="sxs-lookup"><span data-stu-id="81aa7-125">`Unregister-PackageSource`: Removes a registered package source.</span></span>
- <span data-ttu-id="81aa7-126">`Get-Package`: Retourneert een lijst met geïnstalleerde software pakketten.</span><span class="sxs-lookup"><span data-stu-id="81aa7-126">`Get-Package`: Returns a list of installed software packages.</span></span>
- <span data-ttu-id="81aa7-127">`Find-Package`: Zoeken naar software pakketten in beschik bare pakket bronnen.</span><span class="sxs-lookup"><span data-stu-id="81aa7-127">`Find-Package`: Finds software packages in available package sources.</span></span>
- <span data-ttu-id="81aa7-128">`Install-Package`: Hiermee worden een of meer software pakketten geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="81aa7-128">`Install-Package`: Installs one or more software packages.</span></span>
- <span data-ttu-id="81aa7-129">`Save-Package`: Hiermee worden pakketten op de lokale computer opgeslagen zonder dat ze worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="81aa7-129">`Save-Package`: Saves packages to the local computer without installing them.</span></span>
- <span data-ttu-id="81aa7-130">`Uninstall-Package`: Hiermee verwijdert u een of meer software pakketten.</span><span class="sxs-lookup"><span data-stu-id="81aa7-130">`Uninstall-Package`: Uninstalls one or more software packages.</span></span>

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a><span data-ttu-id="81aa7-131">Boots trap-en dynamische cmdlet-para meters van pakket provider</span><span class="sxs-lookup"><span data-stu-id="81aa7-131">Package Provider Bootstrapping and Dynamic Cmdlet Parameters</span></span>

<span data-ttu-id="81aa7-132">Package Management wordt standaard geleverd met een kern Boots trap-provider.</span><span class="sxs-lookup"><span data-stu-id="81aa7-132">By default, PackageManagement ships with a core bootstrap provider.</span></span> <span data-ttu-id="81aa7-133">U kunt aanvullende pakket providers installeren wanneer u deze nodig hebt door de providers te Boots trappen; dat wil zeggen dat er wordt gereageerd op een prompt om de provider automatisch te installeren vanuit een webservice.</span><span class="sxs-lookup"><span data-stu-id="81aa7-133">You can install additional package providers as you need them by bootstrapping the providers; that is, responding to a prompt to install the provider automatically, from a web service.</span></span> <span data-ttu-id="81aa7-134">U kunt een pakket provider met een wille keurige Package Management-cmdlet opgeven. Als de opgegeven provider niet beschikbaar is, wordt u door Package Management gevraagd om de provider te Boots trapen (of automatisch te installeren).</span><span class="sxs-lookup"><span data-stu-id="81aa7-134">You can specify a package provider with any PackageManagement cmdlet; if the specified provider is not available, PackageManagement prompts you to bootstrap (or automatically install) the provider.</span></span> <span data-ttu-id="81aa7-135">Als de chocolade-provider nog niet is geïnstalleerd in de volgende voor beelden, installeert Package Management Boots trap ping de provider.</span><span class="sxs-lookup"><span data-stu-id="81aa7-135">In the following examples, if the Chocolatey provider is not already installed, PackageManagement bootstrapping installs the provider.</span></span>

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

<span data-ttu-id="81aa7-136">Als de chocolade-provider nog niet is geïnstalleerd, wordt u gevraagd deze te installeren wanneer u de voor gaande opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="81aa7-136">If the Chocolatey provider is not already installed, when you run the preceding command, you are prompted to install it.</span></span>

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

<span data-ttu-id="81aa7-137">Als de chocolade-provider nog niet is geïnstalleerd, wordt de provider geïnstalleerd wanneer u de voor gaande opdracht uitvoert. maar omdat de para meter ForceBootstrap is toegevoegd aan de opdracht, wordt u niet gevraagd om deze te installeren. zowel de provider als het pakket worden automatisch geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="81aa7-137">If the Chocolatey provider is not already installed, when you run the preceding command, the provider is installed; but because the ForceBootstrap parameter has been added to the command, you are not prompted to install it; both the provider and the package are installed automatically.</span></span>

<span data-ttu-id="81aa7-138">Wanneer u een pakket probeert te installeren, als u de ondersteunende provider nog niet hebt geïnstalleerd en u de para meter ForceBootstrap niet aan uw opdracht toevoegt, wordt u door Package Management gevraagd de provider te installeren.</span><span class="sxs-lookup"><span data-stu-id="81aa7-138">When you try to install a package, if you do not already have the supporting provider installed, and you do not add the ForceBootstrap parameter to your command, PackageManagement prompts you to install the provider.</span></span>

<span data-ttu-id="81aa7-139">Het opgeven van een pakket provider in de Package Management-opdracht kan dynamische para meters beschikbaar maken die specifiek zijn voor die pakket provider.</span><span class="sxs-lookup"><span data-stu-id="81aa7-139">Specifying a package provider in your PackageManagement command can make dynamic parameters available that are specific to that package provider.</span></span> <span data-ttu-id="81aa7-140">Wanneer u Get-Help uitvoert voor een specifieke Package Management-cmdlet, wordt een lijst met parameter sets geretourneerd, waarbij dynamische para meters voor beschik bare pakket providers in afzonderlijke parameter sets worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="81aa7-140">When you run Get-Help for a specific PackageManagement cmdlet, a list of parameter sets are returned, grouping dynamic parameters for available package providers in separate parameter sets.</span></span>

<span data-ttu-id="81aa7-141">Meer informatie over het package management-project</span><span class="sxs-lookup"><span data-stu-id="81aa7-141">More Information About the PackageManagement Project</span></span>

<span data-ttu-id="81aa7-142">Voor meer informatie over het package management Open Development project, met inbegrip van het maken van een package management-pakket provider, raadpleegt u het package management-project op GitHub op https://oneget.org .</span><span class="sxs-lookup"><span data-stu-id="81aa7-142">For more information about the PackageManagement open development project, including how to create a PackageManagement package provider, see the PackageManagement project on GitHub at https://oneget.org.</span></span>

## <a name="see-also"></a><span data-ttu-id="81aa7-143">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="81aa7-143">SEE ALSO</span></span>

[<span data-ttu-id="81aa7-144">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="81aa7-144">Get-PackageProvider</span></span>](xref:PackageManagement.Get-PackageProvider)

[<span data-ttu-id="81aa7-145">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="81aa7-145">Get-PackageSource</span></span>](xref:PackageManagement.Get-PackageSource)

[<span data-ttu-id="81aa7-146">REGI ster-PackageSource</span><span class="sxs-lookup"><span data-stu-id="81aa7-146">Register-PackageSource</span></span>](xref:PackageManagement.Register-PackageSource)

[<span data-ttu-id="81aa7-147">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="81aa7-147">Set-PackageSource</span></span>](xref:PackageManagement.Set-PackageSource)

[<span data-ttu-id="81aa7-148">Registratie ongedaan maken-PackageSource</span><span class="sxs-lookup"><span data-stu-id="81aa7-148">Unregister-PackageSource</span></span>](xref:PackageManagement.Unregister-PackageSource)

[<span data-ttu-id="81aa7-149">Get-Package</span><span class="sxs-lookup"><span data-stu-id="81aa7-149">Get-Package</span></span>](xref:PackageManagement.Get-Package)

[<span data-ttu-id="81aa7-150">Zoeken-pakket</span><span class="sxs-lookup"><span data-stu-id="81aa7-150">Find-Package</span></span>](xref:PackageManagement.Find-Package)

[<span data-ttu-id="81aa7-151">Install-Package</span><span class="sxs-lookup"><span data-stu-id="81aa7-151">Install-Package</span></span>](xref:PackageManagement.Install-Package)

[<span data-ttu-id="81aa7-152">Opslaan-pakket</span><span class="sxs-lookup"><span data-stu-id="81aa7-152">Save-Package</span></span>](xref:PackageManagement.Save-Package)

[<span data-ttu-id="81aa7-153">Uninstall-pakket</span><span class="sxs-lookup"><span data-stu-id="81aa7-153">Uninstall-Package</span></span>](xref:PackageManagement.Uninstall-Package)

