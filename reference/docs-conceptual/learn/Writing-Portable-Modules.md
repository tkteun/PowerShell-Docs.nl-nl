---
ms.date: 12/14/2018
keywords: PowerShell-cmdlet
title: Draagbare Modules schrijven
ms.openlocfilehash: 38a93b5b030d58784b91292e2cd060b3a2c19a00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086405"
---
# <a name="portable-modules"></a><span data-ttu-id="523e2-103">Draagbare Modules</span><span class="sxs-lookup"><span data-stu-id="523e2-103">Portable Modules</span></span>

<span data-ttu-id="523e2-104">Windows PowerShell is geschreven voor [.NET Framework][] terwijl PowerShell Core is geschreven voor [.NET Core][].</span><span class="sxs-lookup"><span data-stu-id="523e2-104">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="523e2-105">Draagbare modules worden modules die in Windows PowerShell en PowerShell Core werken.</span><span class="sxs-lookup"><span data-stu-id="523e2-105">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="523e2-106">.NET Framework en .NET Core zijn zeer compatibel is, zijn er verschillen in de beschikbare API's tussen de twee.</span><span class="sxs-lookup"><span data-stu-id="523e2-106">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="523e2-107">Er zijn ook verschillen in de API's beschikbaar in Windows PowerShell en PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="523e2-107">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="523e2-108">Modules die zijn bedoeld om te worden gebruikt in beide omgevingen moeten rekening houden met deze verschillen.</span><span class="sxs-lookup"><span data-stu-id="523e2-108">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="523e2-109">Overzetten van een bestaande Module</span><span class="sxs-lookup"><span data-stu-id="523e2-109">Porting an Existing Module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="523e2-110">Een PSSnapIn overzetten</span><span class="sxs-lookup"><span data-stu-id="523e2-110">Porting a PSSnapIn</span></span>

<span data-ttu-id="523e2-111">PowerShell SnapIns (PSSnapIn) worden niet ondersteund in PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="523e2-111">PowerShell SnapIns (PSSnapIn) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="523e2-112">Het is echter pretje om een PSSnapIn converteren naar een PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="523e2-112">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="523e2-113">De registratiecode PSSnapIn is meestal in een bestand met één bron van een klasse die is afgeleid van [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="523e2-113">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="523e2-114">Dit bestand verwijderen van de build; het niet meer nodig.</span><span class="sxs-lookup"><span data-stu-id="523e2-114">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="523e2-115">Gebruik [Nieuwe ModuleManifest][] te maken van een nieuwe modulemanifest dat de registratiecode PSSnapIn meer nodig.</span><span class="sxs-lookup"><span data-stu-id="523e2-115">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="523e2-116">Sommige van de waarden uit de PSSnapIn (zoals beschrijving) opnieuw kan worden gebruikt in de module-manifest.</span><span class="sxs-lookup"><span data-stu-id="523e2-116">Some of the values from the PSSnapIn (such as Description) can be reused within the module manifest.</span></span>

<span data-ttu-id="523e2-117">De `RootModule` eigenschap in de module-manifest moet worden ingesteld op de naam van de implementatie van de cmdlets assembly (dll).</span><span class="sxs-lookup"><span data-stu-id="523e2-117">The `RootModule` property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="523e2-118">De .NET draagbaarheid Analyzer (ook wel APIPort)</span><span class="sxs-lookup"><span data-stu-id="523e2-118">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="523e2-119">Poort-modules die zijn geschreven voor Windows PowerShell om te werken met PowerShell Core, te beginnen met de [.NET Portability Analyzer][].</span><span class="sxs-lookup"><span data-stu-id="523e2-119">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="523e2-120">Dit hulpprogramma uitvoeren op basis van uw gecompileerde assembly om te bepalen of de .NET-API's gebruikt in de module compatibel met .NET Framework, .NET Core en andere runtimes .NET zijn.</span><span class="sxs-lookup"><span data-stu-id="523e2-120">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="523e2-121">Het hulpprogramma zijn overeenkomstig alternatieve API's als deze bestaan.</span><span class="sxs-lookup"><span data-stu-id="523e2-121">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="523e2-122">U moet anders toevoegen [Runtime-controles][] en beperken de mogelijkheden die niet beschikbaar in bepaalde runtimes.</span><span class="sxs-lookup"><span data-stu-id="523e2-122">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="523e2-123">Het maken van een nieuwe Module</span><span class="sxs-lookup"><span data-stu-id="523e2-123">Creating a New Module</span></span>

<span data-ttu-id="523e2-124">Als u een nieuwe module maakt, wordt de aanbeveling is het gebruik van de [.NET CLI][].</span><span class="sxs-lookup"><span data-stu-id="523e2-124">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="523e2-125">De sjabloon standaard PowerShell-Module installeren</span><span class="sxs-lookup"><span data-stu-id="523e2-125">Installing the PowerShell Standard Module Template</span></span>

<span data-ttu-id="523e2-126">Nadat de .NET-CLI is geïnstalleerd, installeert u een bibliotheek voor sjablonen voor het genereren van een eenvoudige PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="523e2-126">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="523e2-127">De module is compatibel met Windows PowerShell, PowerShell Core, Windows, Linux en macOS.</span><span class="sxs-lookup"><span data-stu-id="523e2-127">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="523e2-128">Het volgende voorbeeld laat zien hoe de sjabloon wilt installeren:</span><span class="sxs-lookup"><span data-stu-id="523e2-128">The following example shows how to install the template:</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="523e2-129">Het maken van een nieuw Project in de Module</span><span class="sxs-lookup"><span data-stu-id="523e2-129">Creating a New Module Project</span></span>

<span data-ttu-id="523e2-130">Nadat de sjabloon is geïnstalleerd, kunt u een nieuw PowerShell-module-project met deze sjabloon kunt maken.</span><span class="sxs-lookup"><span data-stu-id="523e2-130">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="523e2-131">In dit voorbeeld wordt de voorbeeldmodule 'myModule' genoemd.</span><span class="sxs-lookup"><span data-stu-id="523e2-131">In this example, the sample module is called 'myModule'.</span></span>

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a><span data-ttu-id="523e2-132">Het bouwen van de Module</span><span class="sxs-lookup"><span data-stu-id="523e2-132">Building the Module</span></span>

<span data-ttu-id="523e2-133">Standaard .NET-CLI-opdrachten gebruiken om het project te bouwen.</span><span class="sxs-lookup"><span data-stu-id="523e2-133">Use standard .NET CLI commands to build the project.</span></span>

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a><span data-ttu-id="523e2-134">De Module testen</span><span class="sxs-lookup"><span data-stu-id="523e2-134">Testing the Module</span></span>

<span data-ttu-id="523e2-135">U kunt na het maken van de module importeren en uitvoeren van de voorbeeld-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="523e2-135">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

<span data-ttu-id="523e2-136">De volgende secties wordt beschreven in detail van de technologieën die worden gebruikt door deze sjabloon.</span><span class="sxs-lookup"><span data-stu-id="523e2-136">The following sections describe in detail some of the technologies used by this template.</span></span>

## <a name="net-standard-library"></a><span data-ttu-id="523e2-137">Standaard .NET-bibliotheek</span><span class="sxs-lookup"><span data-stu-id="523e2-137">.NET Standard Library</span></span>

<span data-ttu-id="523e2-138">[.NET standard][] is een formele specificatie van .NET-API's die beschikbaar in alle .NET-implementaties zijn.</span><span class="sxs-lookup"><span data-stu-id="523e2-138">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="523e2-139">Beheerde code die gericht is op .NET Standard werkt met de .NET Framework en .NET Core-versies die compatibel met die versie van .NET Standard zijn.</span><span class="sxs-lookup"><span data-stu-id="523e2-139">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="523e2-140">Hoewel een API in .NET Standard bestaat mogelijk, de implementatie van de API in .NET Core kan veroorzaken een `PlatformNotSupportedException` tijdens runtime, dus als u wilt controleren van compatibiliteit met Windows PowerShell en PowerShell Core, de aanbevolen procedure is om uit te voeren tests voor de module in beide omgevingen.</span><span class="sxs-lookup"><span data-stu-id="523e2-140">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="523e2-141">Ook tests uitvoeren op Linux en Mac OS, als uw module is bedoeld voor meerdere platforms.</span><span class="sxs-lookup"><span data-stu-id="523e2-141">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="523e2-142">Die gericht is op .NET Standard, zorgt ervoor dat, als de module zich verder ontwikkelt, niet-compatibele API's niet per ongeluk in de module introduceren.</span><span class="sxs-lookup"><span data-stu-id="523e2-142">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="523e2-143">Compatibiliteitsproblemen zijn gedetecteerd bij het compileren in plaats van de runtime.</span><span class="sxs-lookup"><span data-stu-id="523e2-143">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="523e2-144">Het is echter niet vereist voor het doel .NET Standard voor een module om te werken met Windows PowerShell en PowerShell Core, zolang u compatibele API's gebruiken.</span><span class="sxs-lookup"><span data-stu-id="523e2-144">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="523e2-145">De tussenliggende taal (IL) is tussen de twee runtimes compatibel.</span><span class="sxs-lookup"><span data-stu-id="523e2-145">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="523e2-146">U kunt .NET Framework 4.6.1 installeert, doelgroep die compatibel is met .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="523e2-146">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="523e2-147">Als u API's buiten .NET Standard 2.0 niet gebruikt, klikt u vervolgens werkt de module met PowerShell Core 6 zonder hercompilatie.</span><span class="sxs-lookup"><span data-stu-id="523e2-147">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

## <a name="powershell-standard-library"></a><span data-ttu-id="523e2-148">PowerShell-Standard-bibliotheek</span><span class="sxs-lookup"><span data-stu-id="523e2-148">PowerShell Standard Library</span></span>

<span data-ttu-id="523e2-149">De [PowerShell-standaard][] bibliotheek is een formele specificatie van de PowerShell-APIs beschikbaar in alle versies van PowerShell groter is dan of gelijk zijn aan de versie van die standaard.</span><span class="sxs-lookup"><span data-stu-id="523e2-149">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="523e2-150">Bijvoorbeeld, [PowerShell Standard 5.1][] is compatibel met Windows PowerShell 5.1 en PowerShell Core 6.0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="523e2-150">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="523e2-151">Het is raadzaam om eerst te compileren van de module met behulp van PowerShell Standard-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="523e2-151">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="523e2-152">De bibliotheek zorgt ervoor dat de API's zijn beschikbaar en worden geïmplementeerd in Windows PowerShell en PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="523e2-152">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="523e2-153">PowerShell-standaard is bedoeld om altijd worden doorgestuurd-compatibel.</span><span class="sxs-lookup"><span data-stu-id="523e2-153">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="523e2-154">Een module die is gebouwd met behulp van PowerShell Standard-bibliotheek 5.1 wordt altijd compatibel zijn met toekomstige versies van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="523e2-154">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

## <a name="module-manifest"></a><span data-ttu-id="523e2-155">Module-Manifest</span><span class="sxs-lookup"><span data-stu-id="523e2-155">Module Manifest</span></span>

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="523e2-156">Compatibiliteit met Windows PowerShell en PowerShell Core die aangeeft</span><span class="sxs-lookup"><span data-stu-id="523e2-156">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="523e2-157">Nadat is gevalideerd dat de module met Windows PowerShell en PowerShell Core werkt, de module-manifest moet expliciet aangeven compatibiliteit met behulp van de [CompatiblePSEditions][] eigenschap.</span><span class="sxs-lookup"><span data-stu-id="523e2-157">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="523e2-158">Een waarde van `Desktop` betekent dat de module compatibel met Windows PowerShell, terwijl een waarde van is `Core` betekent dat de module compatibel met PowerShell Core is.</span><span class="sxs-lookup"><span data-stu-id="523e2-158">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="523e2-159">Zowel `Desktop` en `Core` betekent dat de module compatibel met Windows PowerShell en PowerShell Core is.</span><span class="sxs-lookup"><span data-stu-id="523e2-159">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="523e2-160">`Core` automatisch betekent niet dat de module compatibel met Windows, Linux en macOS is.</span><span class="sxs-lookup"><span data-stu-id="523e2-160">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="523e2-161">De **CompatiblePSEditions** eigenschap werd geïntroduceerd in PowerShell versie 5.</span><span class="sxs-lookup"><span data-stu-id="523e2-161">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="523e2-162">Module manifesten die gebruikmaken van de **CompatiblePSEditions** eigenschap niet worden geladen in versies voorafgaand aan PowerShell-versie 5.</span><span class="sxs-lookup"><span data-stu-id="523e2-162">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="523e2-163">Compatibiliteit met besturingssystemen die aangeeft</span><span class="sxs-lookup"><span data-stu-id="523e2-163">Indicating OS Compatibility</span></span>

<span data-ttu-id="523e2-164">Valideer eerst of uw module in Linux en macOS werkt.</span><span class="sxs-lookup"><span data-stu-id="523e2-164">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="523e2-165">Vervolgens geven compatibiliteit met deze besturingssystemen in de module-manifest.</span><span class="sxs-lookup"><span data-stu-id="523e2-165">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="523e2-166">Dit maakt het gemakkelijker voor gebruikers van uw module vinden voor hun besturingssysteem wanneer gepubliceerd naar de [PowerShell Gallery][].</span><span class="sxs-lookup"><span data-stu-id="523e2-166">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="523e2-167">In de module-manifest, het `PrivateData` eigenschap heeft een `PSData` onderliggende eigenschap.</span><span class="sxs-lookup"><span data-stu-id="523e2-167">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="523e2-168">De optionele `Tags` eigenschap van `PSData` wordt een matrix met waarden die worden weergegeven in de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="523e2-168">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="523e2-169">De PowerShell Gallery ondersteunt de volgende waarden voor de compatibiliteit van:</span><span class="sxs-lookup"><span data-stu-id="523e2-169">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="523e2-170">Code</span><span class="sxs-lookup"><span data-stu-id="523e2-170">Tag</span></span>               | <span data-ttu-id="523e2-171">Description</span><span class="sxs-lookup"><span data-stu-id="523e2-171">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="523e2-172">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="523e2-172">PSEdition_Core</span></span>    | <span data-ttu-id="523e2-173">Compatibel met PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="523e2-173">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="523e2-174">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="523e2-174">PSEdition_Desktop</span></span> | <span data-ttu-id="523e2-175">Compatibel met Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="523e2-175">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="523e2-176">Windows</span><span class="sxs-lookup"><span data-stu-id="523e2-176">Windows</span></span>           | <span data-ttu-id="523e2-177">Compatibel met Windows</span><span class="sxs-lookup"><span data-stu-id="523e2-177">Compatible with Windows</span></span>                    |
| <span data-ttu-id="523e2-178">Linux</span><span class="sxs-lookup"><span data-stu-id="523e2-178">Linux</span></span>             | <span data-ttu-id="523e2-179">Compatibel met Linux (Er zijn geen specifieke distributie)</span><span class="sxs-lookup"><span data-stu-id="523e2-179">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="523e2-180">macOS</span><span class="sxs-lookup"><span data-stu-id="523e2-180">macOS</span></span>             | <span data-ttu-id="523e2-181">Compatibel met macOS</span><span class="sxs-lookup"><span data-stu-id="523e2-181">Compatible with macOS</span></span>                      |

<span data-ttu-id="523e2-182">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="523e2-182">Example:</span></span>

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[Nieuwe ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Runtime-controles]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell-standaard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
