---
ms.date: 10/21/2020
keywords: powershell,cmdlet
title: Draag bare modules schrijven
description: In dit artikel wordt uitgelegd hoe u nieuwe modules maakt of bestaande modules bijwerkt, zodat ze werken in de platforms die worden ondersteund door Power shell.
ms.openlocfilehash: 6d5c36263c3c6d1219f963cea2e94ae92b07e863
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500790"
---
# <a name="portable-modules"></a><span data-ttu-id="647c8-104">Draag bare modules</span><span class="sxs-lookup"><span data-stu-id="647c8-104">Portable Modules</span></span>

<span data-ttu-id="647c8-105">Windows Power shell is geschreven voor [.NET Framework][] terwijl Power shell Core is geschreven voor [.net core][].</span><span class="sxs-lookup"><span data-stu-id="647c8-105">Windows PowerShell is written for [.NET Framework][] while PowerShell Core is written for [.NET Core][].</span></span> <span data-ttu-id="647c8-106">Draag bare modules zijn modules die in Windows Power shell en Power shell core werken.</span><span class="sxs-lookup"><span data-stu-id="647c8-106">Portable modules are modules that work in both Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="647c8-107">Hoewel .NET Framework en .NET core zeer compatibel zijn, zijn er verschillen in de beschik bare Api's tussen de twee.</span><span class="sxs-lookup"><span data-stu-id="647c8-107">While .NET Framework and .NET Core are highly compatible, there are differences in the available APIs between the two.</span></span> <span data-ttu-id="647c8-108">Er zijn ook verschillen in de Api's die beschikbaar zijn in Windows Power shell en Power shell core.</span><span class="sxs-lookup"><span data-stu-id="647c8-108">There are also differences in the APIs available in Windows PowerShell and PowerShell Core.</span></span> <span data-ttu-id="647c8-109">Modules die in beide omgevingen moeten worden gebruikt, moeten op de hoogte zijn van deze verschillen.</span><span class="sxs-lookup"><span data-stu-id="647c8-109">Modules intended to be used in both environments need to be aware of these differences.</span></span>

## <a name="porting-an-existing-module"></a><span data-ttu-id="647c8-110">Een bestaande module overbrengen</span><span class="sxs-lookup"><span data-stu-id="647c8-110">Porting an existing module</span></span>

### <a name="porting-a-pssnapin"></a><span data-ttu-id="647c8-111">Een PSSnapIn overbrengen</span><span class="sxs-lookup"><span data-stu-id="647c8-111">Porting a PSSnapIn</span></span>

<span data-ttu-id="647c8-112">Power shell- [modules](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) worden niet ondersteund in Power shell core.</span><span class="sxs-lookup"><span data-stu-id="647c8-112">PowerShell [SnapIns](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) aren't supported in PowerShell Core.</span></span> <span data-ttu-id="647c8-113">Het is echter een lastigere PSSnapIn te converteren naar een Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="647c8-113">However, it's trivial to convert a PSSnapIn to a PowerShell module.</span></span> <span data-ttu-id="647c8-114">De registratie code van de PSSnapIn bevindt zich doorgaans in één bron bestand van een klasse die is afgeleid van [PSSnapIn][].</span><span class="sxs-lookup"><span data-stu-id="647c8-114">Typically, the PSSnapIn registration code is in a single source file of a class that derives from [PSSnapIn][].</span></span> <span data-ttu-id="647c8-115">Dit bron bestand verwijderen uit de build; het is niet meer nodig.</span><span class="sxs-lookup"><span data-stu-id="647c8-115">Remove this source file from the build; it's no longer needed.</span></span>

<span data-ttu-id="647c8-116">Gebruik [New-ModuleManifest][] om een nieuw module manifest te maken waarmee de PSSnapIn-registratie code moet worden vervangen.</span><span class="sxs-lookup"><span data-stu-id="647c8-116">Use [New-ModuleManifest][] to create a new module manifest that replaces the need for the PSSnapIn registration code.</span></span> <span data-ttu-id="647c8-117">Sommige waarden van de **PSSnapIn** (zoals **Description**) kunnen opnieuw worden gebruikt binnen het module manifest.</span><span class="sxs-lookup"><span data-stu-id="647c8-117">Some of the values from the **PSSnapIn** (such as **Description**) can be reused within the module manifest.</span></span>

<span data-ttu-id="647c8-118">De eigenschap **RootModule** in het manifest van de module moet worden ingesteld op de naam van de assembly (dll) die de cmdlets implementeert.</span><span class="sxs-lookup"><span data-stu-id="647c8-118">The **RootModule** property in the module manifest should be set to the name of the assembly (dll) implementing the cmdlets.</span></span>

### <a name="the-net-portability-analyzer-aka-apiport"></a><span data-ttu-id="647c8-119">De .NET-portabiliteit Analyzer (ook wel APIPort)</span><span class="sxs-lookup"><span data-stu-id="647c8-119">The .NET Portability Analyzer (aka APIPort)</span></span>

<span data-ttu-id="647c8-120">Als u poort modules hebt geschreven voor Windows Power shell voor gebruik met Power shell core, start u met de [.net-portabiliteit Analyzer][].</span><span class="sxs-lookup"><span data-stu-id="647c8-120">To port modules written for Windows PowerShell to work with PowerShell Core, start with the [.NET Portability Analyzer][].</span></span> <span data-ttu-id="647c8-121">Voer dit hulp programma uit met de gecompileerde assembly om te bepalen of de .NET-Api's die in de module worden gebruikt, compatibel zijn met .NET Framework, .NET core en andere .NET-Runtimes.</span><span class="sxs-lookup"><span data-stu-id="647c8-121">Run this tool against your compiled assembly to determine if the .NET APIs used in the module are compatible with .NET Framework, .NET Core, and other .NET runtimes.</span></span> <span data-ttu-id="647c8-122">Het hulp programma stelt alternatieve Api's voor als deze bestaan.</span><span class="sxs-lookup"><span data-stu-id="647c8-122">The tool suggests alternate APIs if they exist.</span></span> <span data-ttu-id="647c8-123">Als dat niet het geval is, moet u mogelijk [runtime controles][] toevoegen en de mogelijkheden beperken die niet beschikbaar zijn in specifieke Runtimes.</span><span class="sxs-lookup"><span data-stu-id="647c8-123">Otherwise, you may need to add [runtime checks][] and restrict capabilities not available in specific runtimes.</span></span>

## <a name="creating-a-new-module"></a><span data-ttu-id="647c8-124">Een nieuwe module maken</span><span class="sxs-lookup"><span data-stu-id="647c8-124">Creating a new module</span></span>

<span data-ttu-id="647c8-125">Als u een nieuwe module maakt, is de aanbeveling de [.net cli][]te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="647c8-125">If creating a new module, the recommendation is to use the [.NET CLI][].</span></span>

### <a name="installing-the-powershell-standard-module-template"></a><span data-ttu-id="647c8-126">De sjabloon voor de Power Shell-standaard module installeren</span><span class="sxs-lookup"><span data-stu-id="647c8-126">Installing the PowerShell Standard module template</span></span>

<span data-ttu-id="647c8-127">Zodra .NET CLI is geïnstalleerd, installeert u een sjabloon bibliotheek voor het genereren van een eenvoudige Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="647c8-127">Once the .NET CLI is installed, install a template library to generate a simple PowerShell module.</span></span>
<span data-ttu-id="647c8-128">De module is compatibel met Windows Power shell, Power shell core, Windows, Linux en macOS.</span><span class="sxs-lookup"><span data-stu-id="647c8-128">The module will be compatible with Windows PowerShell, PowerShell Core, Windows, Linux, and macOS.</span></span>

<span data-ttu-id="647c8-129">In het volgende voor beeld ziet u hoe u de sjabloon installeert:</span><span class="sxs-lookup"><span data-stu-id="647c8-129">The following example shows how to install the template:</span></span>

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


Templates                        Short Name         Language          Tags
-----------------------------------------------------------------------------------------------
Console Application              console            [C#], F#, VB      Common/Console
Class library                    classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module       psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a><span data-ttu-id="647c8-130">Een nieuw module project maken</span><span class="sxs-lookup"><span data-stu-id="647c8-130">Creating a new module project</span></span>

<span data-ttu-id="647c8-131">Nadat de sjabloon is geïnstalleerd, kunt u een nieuw Power shell-module project maken op basis van deze sjabloon.</span><span class="sxs-lookup"><span data-stu-id="647c8-131">After the template is installed, you can create a new PowerShell module project using that template.</span></span> <span data-ttu-id="647c8-132">In dit voor beeld wordt de voorbeeld module ' myModule ' genoemd.</span><span class="sxs-lookup"><span data-stu-id="647c8-132">In this example, the sample module is called 'myModule'.</span></span>

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

### <a name="building-the-module"></a><span data-ttu-id="647c8-133">De module bouwen</span><span class="sxs-lookup"><span data-stu-id="647c8-133">Building the module</span></span>

<span data-ttu-id="647c8-134">Gebruik de standaard .NET CLI-opdrachten om het project te bouwen.</span><span class="sxs-lookup"><span data-stu-id="647c8-134">Use standard .NET CLI commands to build the project.</span></span>

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

### <a name="testing-the-module"></a><span data-ttu-id="647c8-135">De module testen</span><span class="sxs-lookup"><span data-stu-id="647c8-135">Testing the module</span></span>

<span data-ttu-id="647c8-136">Nadat u de module hebt gemaakt, kunt u deze importeren en de voor beeld-cmdlet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="647c8-136">After building the module, you can import it and execute the sample cmdlet.</span></span>

```powershell
Import-Module .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

### <a name="debugging-the-module"></a><span data-ttu-id="647c8-137">Fout opsporing in de module</span><span class="sxs-lookup"><span data-stu-id="647c8-137">Debugging the module</span></span>

<span data-ttu-id="647c8-138">Zie [Visual Studio code gebruiken voor het opsporen van fouten in gecompileerde cmdlets][]voor een hand leiding voor het instellen van Visual Studio code voor het opsporen van fouten in de module.</span><span class="sxs-lookup"><span data-stu-id="647c8-138">For a guide on setting up Visual Studio Code to debug the module, see [Using Visual Studio Code for debugging compiled cmdlets][].</span></span>

## <a name="supporting-technologies"></a><span data-ttu-id="647c8-139">Ondersteunende technologieën</span><span class="sxs-lookup"><span data-stu-id="647c8-139">Supporting technologies</span></span>

<span data-ttu-id="647c8-140">In de volgende secties worden een aantal technologieën beschreven die worden gebruikt door deze sjabloon.</span><span class="sxs-lookup"><span data-stu-id="647c8-140">The following sections describe in detail some of the technologies used by this template.</span></span>

### <a name="net-standard-library"></a><span data-ttu-id="647c8-141">.NET Standard-bibliotheek</span><span class="sxs-lookup"><span data-stu-id="647c8-141">.NET Standard Library</span></span>

<span data-ttu-id="647c8-142">[.NET Standard][] is een formele specificatie van .net-api's die beschikbaar zijn in alle .net-implementaties.</span><span class="sxs-lookup"><span data-stu-id="647c8-142">[.NET Standard][] is a formal specification of .NET APIs that are available in all .NET implementations.</span></span> <span data-ttu-id="647c8-143">Beheerde code doelen .NET Standard werkt met de .NET Framework-en .NET Core-versies die compatibel zijn met die versie van de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="647c8-143">Managed code targeting .NET Standard works with the .NET Framework and .NET Core versions that are compatible with that version of the .NET Standard.</span></span>

> [!NOTE]
> <span data-ttu-id="647c8-144">Hoewel er in .NET Standard een API kan bestaan, kan de API-implementatie in .NET core een `PlatformNotSupportedException` tijdens runtime genereren, zodat u de compatibiliteit met Windows Power shell en Power shell Core kunt controleren. de best practice is om in beide omgevingen tests uit te voeren voor uw module.</span><span class="sxs-lookup"><span data-stu-id="647c8-144">Although an API may exist in .NET Standard, the API implementation in .NET Core may throw a `PlatformNotSupportedException` at runtime, so to verify compatibility with Windows PowerShell and PowerShell Core, the best practice is to run tests for your module within both environments.</span></span>
> <span data-ttu-id="647c8-145">Voer ook tests uit op Linux en macOS als uw module geschikt is voor meerdere platforms.</span><span class="sxs-lookup"><span data-stu-id="647c8-145">Also run tests on Linux and macOS if your module is intended to be cross-platform.</span></span>

<span data-ttu-id="647c8-146">Met behulp van .NET Standard kunt u ervoor zorgen dat bij het ontwikkelen van de module niet-compatibele Api's per ongeluk worden geïntroduceerd in de module.</span><span class="sxs-lookup"><span data-stu-id="647c8-146">Targeting .NET Standard helps ensure that, as the module evolves, incompatible APIs don't accidentally get introduced into the module.</span></span> <span data-ttu-id="647c8-147">Incompatibiliteiten worden tijdens het compileren gedetecteerd in plaats van runtime.</span><span class="sxs-lookup"><span data-stu-id="647c8-147">Incompatibilities are discovered at compile time instead of runtime.</span></span>

<span data-ttu-id="647c8-148">Het is echter niet nodig om .NET Standard te richten op een module om te kunnen werken met Windows Power shell en Power shell core, zolang u compatibele Api's gebruikt.</span><span class="sxs-lookup"><span data-stu-id="647c8-148">However, it isn't required to target .NET Standard for a module to work with both Windows PowerShell and PowerShell Core, as long as you use compatible APIs.</span></span> <span data-ttu-id="647c8-149">De tussen taal (IL) is compatibel tussen de twee Runtimes.</span><span class="sxs-lookup"><span data-stu-id="647c8-149">The Intermediate Language (IL) is compatible between the two runtimes.</span></span> <span data-ttu-id="647c8-150">U kunt .NET Framework 4.6.1 instellen, die compatibel is met .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="647c8-150">You can target .NET Framework 4.6.1, which is compatible with .NET Standard 2.0.</span></span> <span data-ttu-id="647c8-151">Als u geen Api's buiten .NET Standard 2,0 gebruikt, werkt uw module met Power shell Core 6 zonder opnieuw te compileren.</span><span class="sxs-lookup"><span data-stu-id="647c8-151">If you don't use APIs outside of .NET Standard 2.0, then your module works with PowerShell Core 6 without recompilation.</span></span>

### <a name="powershell-standard-library"></a><span data-ttu-id="647c8-152">Standaard bibliotheek van Power shell</span><span class="sxs-lookup"><span data-stu-id="647c8-152">PowerShell Standard Library</span></span>

<span data-ttu-id="647c8-153">De [standaard bibliotheek van Power shell][] is een formele specificatie van Power shell-api's die beschikbaar zijn in alle Power shell-versies die groter zijn dan of gelijk zijn aan de versie van die Standard.</span><span class="sxs-lookup"><span data-stu-id="647c8-153">The [PowerShell Standard][] library is a formal specification of PowerShell APIs available in all PowerShell versions greater than or equal to the version of that standard.</span></span>

<span data-ttu-id="647c8-154">[Power shell Standard 5,1][] is bijvoorbeeld compatibel met Windows power shell 5,1 en Power shell Core 6,0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="647c8-154">For example, [PowerShell Standard 5.1][] is compatible with both Windows PowerShell 5.1 and PowerShell Core 6.0 or newer.</span></span>

<span data-ttu-id="647c8-155">U wordt aangeraden uw module te compileren met behulp van de standaard bibliotheek van Power shell.</span><span class="sxs-lookup"><span data-stu-id="647c8-155">We recommend you compile your module using PowerShell Standard Library.</span></span> <span data-ttu-id="647c8-156">De tape wisselaar zorgt ervoor dat de Api's beschikbaar zijn en in Windows Power shell en Power shell Core 6 worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="647c8-156">The library ensures the APIs are available and implemented in both Windows PowerShell and PowerShell Core 6.</span></span>
<span data-ttu-id="647c8-157">Power shell Standard is bedoeld om altijd compatibel te zijn.</span><span class="sxs-lookup"><span data-stu-id="647c8-157">PowerShell Standard is intended to always be forwards-compatible.</span></span> <span data-ttu-id="647c8-158">Een module die is gemaakt met behulp van de standaard bibliotheek 5,1 van Power shell is altijd compatibel met toekomstige versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="647c8-158">A module built using PowerShell Standard Library 5.1 will always be compatible with future versions of PowerShell.</span></span>

### <a name="module-manifest"></a><span data-ttu-id="647c8-159">Module manifest</span><span class="sxs-lookup"><span data-stu-id="647c8-159">Module Manifest</span></span>

#### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a><span data-ttu-id="647c8-160">Duidt op compatibiliteit met Windows Power shell en Power shell core</span><span class="sxs-lookup"><span data-stu-id="647c8-160">Indicating Compatibility With Windows PowerShell and PowerShell Core</span></span>

<span data-ttu-id="647c8-161">Nadat u hebt gecontroleerd of de module werkt met Windows Power shell en Power shell core, moet het module manifest expliciet duiden op compatibiliteit met behulp van de eigenschap [CompatiblePSEditions][] .</span><span class="sxs-lookup"><span data-stu-id="647c8-161">After validating that your module works with both Windows PowerShell and PowerShell Core, the module manifest should explicitly indicate compatibility by using the [CompatiblePSEditions][] property.</span></span> <span data-ttu-id="647c8-162">Een waarde `Desktop` betekent dat de module compatibel is met Windows Power shell, terwijl een waarde `Core` betekent dat de module compatibel is met Power shell core.</span><span class="sxs-lookup"><span data-stu-id="647c8-162">A value of `Desktop` means that the module is compatible with Windows PowerShell, while a value of `Core` means that the module is compatible with PowerShell Core.</span></span> <span data-ttu-id="647c8-163">Inclusief beide `Desktop` en `Core` betekent dat de module compatibel is met Windows Power shell en Power shell core.</span><span class="sxs-lookup"><span data-stu-id="647c8-163">Including both `Desktop` and `Core` means that the module is compatible with both Windows PowerShell and PowerShell Core.</span></span>

> [!NOTE]
> <span data-ttu-id="647c8-164">`Core` betekent niet automatisch dat de module compatibel is met Windows, Linux en macOS.</span><span class="sxs-lookup"><span data-stu-id="647c8-164">`Core` does not automatically mean that the module is compatible with Windows, Linux, and macOS.</span></span>
> <span data-ttu-id="647c8-165">De eigenschap **CompatiblePSEditions** is geïntroduceerd in Power Shell v5.</span><span class="sxs-lookup"><span data-stu-id="647c8-165">The **CompatiblePSEditions** property was introduced in PowerShell v5.</span></span> <span data-ttu-id="647c8-166">Module manifesten die gebruikmaken van de eigenschap **CompatiblePSEditions** , kunnen niet worden geladen in versies voorafgaand aan Power Shell v5.</span><span class="sxs-lookup"><span data-stu-id="647c8-166">Module manifests that use the **CompatiblePSEditions** property fail to load in versions prior to PowerShell v5.</span></span>

### <a name="indicating-os-compatibility"></a><span data-ttu-id="647c8-167">De compatibiliteit van besturings systemen aangeven</span><span class="sxs-lookup"><span data-stu-id="647c8-167">Indicating OS Compatibility</span></span>

<span data-ttu-id="647c8-168">Controleer eerst of uw module werkt op Linux en macOS.</span><span class="sxs-lookup"><span data-stu-id="647c8-168">First, validate that your module works on Linux and macOS.</span></span> <span data-ttu-id="647c8-169">Geef vervolgens compatibiliteit met deze besturings systemen op in het module manifest.</span><span class="sxs-lookup"><span data-stu-id="647c8-169">Next, indicate compatibility with those operating systems in the module manifest.</span></span> <span data-ttu-id="647c8-170">Dit maakt het gemakkelijker voor gebruikers om uw module te vinden voor hun besturings systeem wanneer deze naar de [PowerShell Gallery][]worden gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="647c8-170">This makes it easier for users to find your module for their operating system when published to the [PowerShell Gallery][].</span></span>

<span data-ttu-id="647c8-171">Binnen het module manifest heeft de `PrivateData` eigenschap een `PSData` subeigenschap.</span><span class="sxs-lookup"><span data-stu-id="647c8-171">Within the module manifest, the `PrivateData` property has a `PSData` sub-property.</span></span> <span data-ttu-id="647c8-172">De optionele `Tags` eigenschap van `PSData` heeft een matrix van waarden die worden weer gegeven in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="647c8-172">The optional `Tags` property of `PSData` takes an array of values that show up in PowerShell Gallery.</span></span> <span data-ttu-id="647c8-173">De PowerShell Gallery ondersteunt de volgende compatibiliteits waarden:</span><span class="sxs-lookup"><span data-stu-id="647c8-173">The PowerShell Gallery supports the following compatibility values:</span></span>

| <span data-ttu-id="647c8-174">Tag</span><span class="sxs-lookup"><span data-stu-id="647c8-174">Tag</span></span>               | <span data-ttu-id="647c8-175">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="647c8-175">Description</span></span>                                |
|-------------------|--------------------------------------------|
| <span data-ttu-id="647c8-176">PSEdition_Core</span><span class="sxs-lookup"><span data-stu-id="647c8-176">PSEdition_Core</span></span>    | <span data-ttu-id="647c8-177">Compatibel met Power shell Core 6</span><span class="sxs-lookup"><span data-stu-id="647c8-177">Compatible with PowerShell Core 6</span></span>          |
| <span data-ttu-id="647c8-178">PSEdition_Desktop</span><span class="sxs-lookup"><span data-stu-id="647c8-178">PSEdition_Desktop</span></span> | <span data-ttu-id="647c8-179">Compatibel met Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="647c8-179">Compatible with Windows PowerShell</span></span>         |
| <span data-ttu-id="647c8-180">Windows</span><span class="sxs-lookup"><span data-stu-id="647c8-180">Windows</span></span>           | <span data-ttu-id="647c8-181">Compatibel met Windows</span><span class="sxs-lookup"><span data-stu-id="647c8-181">Compatible with Windows</span></span>                    |
| <span data-ttu-id="647c8-182">Linux</span><span class="sxs-lookup"><span data-stu-id="647c8-182">Linux</span></span>             | <span data-ttu-id="647c8-183">Compatibel met Linux (geen specifieke distributie)</span><span class="sxs-lookup"><span data-stu-id="647c8-183">Compatible with Linux (no specific distro)</span></span> |
| <span data-ttu-id="647c8-184">macOS</span><span class="sxs-lookup"><span data-stu-id="647c8-184">macOS</span></span>             | <span data-ttu-id="647c8-185">Compatibel met macOS</span><span class="sxs-lookup"><span data-stu-id="647c8-185">Compatible with macOS</span></span>                      |

<span data-ttu-id="647c8-186">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="647c8-186">Example:</span></span>

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

### <a name="dependency-on-native-libraries"></a><span data-ttu-id="647c8-187">Afhankelijkheid van systeem eigen bibliotheken</span><span class="sxs-lookup"><span data-stu-id="647c8-187">Dependency on Native Libraries</span></span>

<span data-ttu-id="647c8-188">Modules die bedoeld zijn voor gebruik in verschillende besturings systemen of processor architecturen kunnen afhankelijk zijn van een beheerde bibliotheek die zelf afhankelijk is van sommige systeem eigen bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="647c8-188">Modules intended for use across different operating systems or processor architectures may depend on a managed library that itself depends on some native libraries.</span></span>

<span data-ttu-id="647c8-189">Voorafgaand aan Power shell 7 zou een aangepaste code moeten hebben om de juiste systeem eigen dll te laden, zodat de beheerde bibliotheek deze correct kan vinden.</span><span class="sxs-lookup"><span data-stu-id="647c8-189">Prior to PowerShell 7, one would have to have custom code to load the appropriate native dll so that the managed library can find it correctly.</span></span>

<span data-ttu-id="647c8-190">Met Power shell 7 worden systeem eigen binaire bestanden die worden geladen in submappen in de locatie van de beheerde bibliotheek doorzocht na een subset van de [.net Rid-catalogus][] notatie.</span><span class="sxs-lookup"><span data-stu-id="647c8-190">With PowerShell 7, native binaries to load are searched in sub-folders within the managed library's location following a subset of the [.NET RID Catalog][] notation.</span></span>

```
managed.dll folder
    |
    |--- 'win-x64' folder
    |       |--- native.dll
    |
    |--- 'win-x86' folder
    |       |--- native.dll
    |
    |--- 'win-arm' folder
    |       |--- native.dll
    |
    |--- 'win-arm64' folder
    |       |--- native.dll
    |
    |--- 'linux-x64' folder
    |       |--- native.so
    |
    |--- 'linux-x86' folder
    |       |--- native.so
    |
    |--- 'linux-arm' folder
    |       |--- native.so
    |
    |--- 'linux-arm64' folder
    |       |--- native.so
    |
    |--- 'osx-x64' folder
    |       |--- native.dylib
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[runtime controles]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[runtime checks]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[Visual Studio code gebruiken voor het opsporen van fouten in gecompileerde cmdlets]: vscode/using-vscode-for-debugging-compiled-cmdlets.md
[Using Visual Studio Code for debugging compiled cmdlets]: vscode/using-vscode-for-debugging-compiled-cmdlets.md
[.NET Standard]: /dotnet/standard/net-standard
[Power Shell-standaard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[Power Shell-standaard 5,1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell Gallery]: https://www.powershellgallery.com
[.NET-portabiliteit Analyzer]: https://github.com/Microsoft/dotnet-apiport
[.NET Portability Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
[.NET RID-catalogus]: /dotnet/core/rid-catalog
[.NET RID Catalog]: /dotnet/core/rid-catalog
