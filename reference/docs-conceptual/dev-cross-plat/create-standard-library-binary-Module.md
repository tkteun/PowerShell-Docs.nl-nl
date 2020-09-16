---
title: Een binaire module van een standaard bibliotheek maken
description: Met de standaard bibliotheek van Power shell kunnen wij platformoverschrijdende modules maken die zowel in Power shell Core als met Windows Power shell 5,1 worden uitgevoerd.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ff6a49f70a3fb77f5a30cc909d53bb77b3cd7d43
ms.sourcegitcommit: 8c01e56f0c10ff2637955dc892ea78432d563a7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/21/2020
ms.locfileid: "88702742"
---
# <a name="how-to-create-a-standard-library-binary-module"></a><span data-ttu-id="e72c9-103">Een binaire module van een standaardbibliotheek maken</span><span class="sxs-lookup"><span data-stu-id="e72c9-103">How to create a Standard Library binary module</span></span>

<span data-ttu-id="e72c9-104">Ik heb onlangs een idee voor de module die ik wilde implementeren als binaire module.</span><span class="sxs-lookup"><span data-stu-id="e72c9-104">I recently had an idea for module that I wanted to implement as a binary module.</span></span> <span data-ttu-id="e72c9-105">Ik heb een wacht tijd gemaakt met behulp van de [standaard bibliotheek van Power shell][] , zodat deze zo goed mogelijk is.</span><span class="sxs-lookup"><span data-stu-id="e72c9-105">I have yet to create one using the [PowerShell Standard Library][] so this felt like a good opportunity.</span></span> <span data-ttu-id="e72c9-106">Ik heb de hand leiding [een multi-platform binaire module maken][] gebruikt om deze module zonder obstakels te maken.</span><span class="sxs-lookup"><span data-stu-id="e72c9-106">I used the [Creating a cross-platform binary module][] guide to create this module without any roadblocks.</span></span>
<span data-ttu-id="e72c9-107">We gaan hetzelfde proces door lopen en ik voeg graag een beetje extra commentaar toe.</span><span class="sxs-lookup"><span data-stu-id="e72c9-107">We're going to walk that same process and I'll add a little extra commentary along the way.</span></span>

> [!NOTE]
> <span data-ttu-id="e72c9-108">De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="e72c9-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="e72c9-109">Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="e72c9-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="e72c9-110">Raadpleeg zijn blog op [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="e72c9-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-the-powershell-standard-library"></a><span data-ttu-id="e72c9-111">Wat is de standaard-Power shell-bibliotheek?</span><span class="sxs-lookup"><span data-stu-id="e72c9-111">What is the PowerShell Standard Library?</span></span>

<span data-ttu-id="e72c9-112">Met de standaard bibliotheek van Power shell kunnen wij cross platform modules maken die zowel in Power shell Core als in Windows Power shell 5,1 (of 3,0) werken.</span><span class="sxs-lookup"><span data-stu-id="e72c9-112">The PowerShell Standard Library allows us to create cross platform modules that work in both PowerShell Core and with Windows PowerShell 5.1 (or 3.0).</span></span>

## <a name="planning-our-module"></a><span data-ttu-id="e72c9-113">Onze module plannen</span><span class="sxs-lookup"><span data-stu-id="e72c9-113">Planning our module</span></span>

<span data-ttu-id="e72c9-114">Het plan voor deze module is het maken `src` van een map voor de C#-code en de structuur van de rest, zoals voor een script module.</span><span class="sxs-lookup"><span data-stu-id="e72c9-114">The plan for this module is to create a `src` folder for the C# code and structure the rest like I would for a script module.</span></span> <span data-ttu-id="e72c9-115">Dit omvat het gebruik van een build-script voor het compileren van alles in een `output` map.</span><span class="sxs-lookup"><span data-stu-id="e72c9-115">This includes using a build script to compile everything into an `output` folder.</span></span> <span data-ttu-id="e72c9-116">De mapstructuur ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="e72c9-116">The folder structure looks like this:</span></span>

```
MyModule
├───src
├───Output
│   └───MyModule
├───MyModule
│   ├───Data
│   ├───Private
│   └───Public
└───Tests
```

## <a name="getting-started"></a><span data-ttu-id="e72c9-117">Aan de slag</span><span class="sxs-lookup"><span data-stu-id="e72c9-117">Getting Started</span></span>

<span data-ttu-id="e72c9-118">Ik gebruik normaal gesp roken een gips sjabloon, maar mijn huidige sjabloon heeft nog geen ondersteuning voor binaire modules.</span><span class="sxs-lookup"><span data-stu-id="e72c9-118">I normally use a Plaster template but my current template doesn't have any binary module support yet.</span></span> <span data-ttu-id="e72c9-119">Niet veel.</span><span class="sxs-lookup"><span data-stu-id="e72c9-119">Not a big deal.</span></span> <span data-ttu-id="e72c9-120">Ik maak dit nu hand matig.</span><span class="sxs-lookup"><span data-stu-id="e72c9-120">I'll create this one by hand this time.</span></span>

<span data-ttu-id="e72c9-121">Eerst moet u de map maken en de Git-opslag plaats maken.</span><span class="sxs-lookup"><span data-stu-id="e72c9-121">First I need to create the folder and create the git repo.</span></span> <span data-ttu-id="e72c9-122">Ik gebruik `$module` als tijdelijke aanduiding voor de naam van de module.</span><span class="sxs-lookup"><span data-stu-id="e72c9-122">I'm using `$module` as a placeholder for the module name.</span></span> <span data-ttu-id="e72c9-123">Zo nodig kunt u deze voor beelden gemakkelijker opnieuw gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e72c9-123">This should make it easier for you to reuse these examples if needed.</span></span>

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

<span data-ttu-id="e72c9-124">Maak vervolgens de mappen op het hoofd niveau.</span><span class="sxs-lookup"><span data-stu-id="e72c9-124">Then create the root level folders.</span></span>

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a><span data-ttu-id="e72c9-125">Setup van binaire module</span><span class="sxs-lookup"><span data-stu-id="e72c9-125">Binary module setup</span></span>

<span data-ttu-id="e72c9-126">Dit artikel is gericht op de binaire module, zodat we beginnen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-126">This article os focused on the binary module so that is where we'll start.</span></span> <span data-ttu-id="e72c9-127">In deze sectie vindt u voor beelden van de hand leiding [een multi-platform binaire module maken][] .</span><span class="sxs-lookup"><span data-stu-id="e72c9-127">This section pulls examples from the [Creating a cross-platform binary module][] guide.</span></span> <span data-ttu-id="e72c9-128">Lees deze hand leiding als u meer informatie nodig hebt of problemen ondervindt.</span><span class="sxs-lookup"><span data-stu-id="e72c9-128">Review that guide if you need more details or have any issues.</span></span>

<span data-ttu-id="e72c9-129">Het eerste wat we willen doen, is de versie controleren van de [DotNet core SDK][] die we hebben geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e72c9-129">First thing we want to do is check the version of the [dotnet core SDK][] that we installed.</span></span> <span data-ttu-id="e72c9-130">Ik gebruik 2.1.4, maar u moet 2.0.0 of nieuwer hebben voordat u kunt door gaan.</span><span class="sxs-lookup"><span data-stu-id="e72c9-130">I'm using 2.1.4, but you should have 2.0.0 or newer before continuing.</span></span>

```powershell
PS> dotnet --version
2.1.4
```

<span data-ttu-id="e72c9-131">Ik werk samen met de `src` map voor deze sectie.</span><span class="sxs-lookup"><span data-stu-id="e72c9-131">I'm working out of the `src` folder for this section.</span></span>

```powershell
Set-Location 'src'
```

<span data-ttu-id="e72c9-132">Maak met behulp van de opdracht DotNet een nieuwe klassen bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="e72c9-132">Using the dotnet command, create a new class library.</span></span>

```powershell
dotnet new classlib --name $module
```

<span data-ttu-id="e72c9-133">Het bibliotheek project is gemaakt in een submap, maar ik wil niet dat het extra geneste niveau.</span><span class="sxs-lookup"><span data-stu-id="e72c9-133">This created the library project in a subfolder but I don't want that extra level of nesting.</span></span> <span data-ttu-id="e72c9-134">Ik ga deze bestanden naar een niveau omhoog verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-134">I'm going to move those files up a level.</span></span>

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

<span data-ttu-id="e72c9-135">Stel de .NET core SDK-versie voor het project in.</span><span class="sxs-lookup"><span data-stu-id="e72c9-135">Set the .NET core SDK version for the project.</span></span> <span data-ttu-id="e72c9-136">Ik heb de 2,1-SDK zodat ik 2.1.0 kan opgeven.</span><span class="sxs-lookup"><span data-stu-id="e72c9-136">I have the 2.1 SDK so I'm going to specify 2.1.0.</span></span>
<span data-ttu-id="e72c9-137">Gebruik 2.0.0 als u de 2,0-SDK gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e72c9-137">Use 2.0.0 if you're using the 2.0 SDK.</span></span>

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

<span data-ttu-id="e72c9-138">Voeg het [NuGet-pakket][] van de Power Shell-standaard bibliotheek toe aan het project.</span><span class="sxs-lookup"><span data-stu-id="e72c9-138">Add the PowerShell Standard Library [NuGet package][] to the project.</span></span> <span data-ttu-id="e72c9-139">Zorg ervoor dat u de meest recente versie gebruikt die beschikbaar is voor het compatibiliteits niveau dat u nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="e72c9-139">Make sure you use the most recent version available for the level of compatibility that you need.</span></span> <span data-ttu-id="e72c9-140">Ik zou standaard de nieuwste versie kunnen gebruiken, maar ik denk eraan dat deze module geen functies gebruikt die nieuwer zijn dan Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e72c9-140">I would default to the latest version but I don't think this module leverages any features newer than PowerShell 3.0.</span></span>

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

<span data-ttu-id="e72c9-141">De map src moet er als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="e72c9-141">We should have a src folder that looks like this:</span></span>

```powershell
PS> Get-ChildItem
    Directory: \MyModule\src

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        7/14/2018   9:51 PM                obj
-a----        7/14/2018   9:51 PM             86 Class1.cs
-a----        7/14/2018  10:03 PM            259 MyModule.csproj
-a----        7/14/2018  10:05 PM             45 global.json
```

<span data-ttu-id="e72c9-142">U kunt nu onze eigen code aan het project toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-142">Now we're ready to add our own code to the project.</span></span>

### <a name="building-a-binary-cmdlet"></a><span data-ttu-id="e72c9-143">Een binaire cmdlet bouwen</span><span class="sxs-lookup"><span data-stu-id="e72c9-143">Building a binary cmdlet</span></span>

<span data-ttu-id="e72c9-144">De `src\Class1.cs` moet worden bijgewerkt om deze start-cmdlet te bevatten:</span><span class="sxs-lookup"><span data-stu-id="e72c9-144">We need to update the `src\Class1.cs` to contain this starter cmdlet:</span></span>

```csharp
using System;
using System.Management.Automation;

namespace MyModule
{
    [Cmdlet( VerbsDiagnostic.Resolve , "MyCmdlet")]
    public class ResolveMyCmdletCommand : PSCmdlet
    {
        [Parameter(Position=0)]
        public Object InputObject { get; set; }

        protected override void EndProcessing()
        {
            this.WriteObject(this.InputObject);
            base.EndProcessing();
        }
    }
}
```

<span data-ttu-id="e72c9-145">Wijzig de naam van het bestand zodat dit overeenkomt met de naam van de klasse.</span><span class="sxs-lookup"><span data-stu-id="e72c9-145">Rename the file to match the class name.</span></span>

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

<span data-ttu-id="e72c9-146">Vervolgens kunnen we onze module bouwen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-146">Then we can build our module.</span></span>

```powershell
PS> dotnet build

Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

Restore completed in 18.19 ms for C:\workspace\MyModule\src\MyModule.csproj.
MyModule -> C:\workspace\MyModule\src\bin\Debug\netstandard2.0\MyModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.19
```

<span data-ttu-id="e72c9-147">We kunnen `Import-Module` op de nieuwe dll bellen om onze nieuwe CMDlet te laden.</span><span class="sxs-lookup"><span data-stu-id="e72c9-147">We can call `Import-Module` on the new dll to load our new CMDlet.</span></span>

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

<span data-ttu-id="e72c9-148">Als het importeren mislukt op uw systeem, probeert u .NET bij te werken naar 4.7.1 of nieuwer.</span><span class="sxs-lookup"><span data-stu-id="e72c9-148">If the import fails on your system, try updating .NET to 4.7.1 or newer.</span></span> <span data-ttu-id="e72c9-149">De hand leiding voor het [maken van een multi platform binaire module][] biedt meer informatie over .net-ondersteuning en-compatibiliteit voor oudere versies van .net.</span><span class="sxs-lookup"><span data-stu-id="e72c9-149">The [Creating a cross-platform binary module][] guide goes into more details on .NET support and compatibility for older versions of .NET.</span></span>

### <a name="module-manifest"></a><span data-ttu-id="e72c9-150">Module manifest</span><span class="sxs-lookup"><span data-stu-id="e72c9-150">Module manifest</span></span>

<span data-ttu-id="e72c9-151">Het is geweldig dat de dll kan worden geïmporteerd en dat er een werkende module is.</span><span class="sxs-lookup"><span data-stu-id="e72c9-151">It's cool that we can import the dll and have a working module.</span></span> <span data-ttu-id="e72c9-152">Ik ga graag aan de slag en maak een module manifest.</span><span class="sxs-lookup"><span data-stu-id="e72c9-152">I like to keep going with it and create a module manifest.</span></span> <span data-ttu-id="e72c9-153">U hebt het manifest nodig als u later naar de PSGallery wilt publiceren.</span><span class="sxs-lookup"><span data-stu-id="e72c9-153">We need the manifest if we want to publish to the PSGallery later.</span></span>

<span data-ttu-id="e72c9-154">In de hoofdmap van ons project kunnen we deze opdracht uitvoeren om het module manifest te maken dat we nodig hebben.</span><span class="sxs-lookup"><span data-stu-id="e72c9-154">From the root of our project, we can run this command to create the module manifest that we need.</span></span>

```powershell
$manifestSplat = @{
    Path              = ".\$module\$module.psd1"
    Author            = 'Kevin Marquette'
    NestedModules     = @('bin\MyModule.dll')
    RootModule        = "$module.psm1"
    FunctionsToExport = @('Resolve-MyCmdlet')
}
New-ModuleManifest @manifestSplat
```

<span data-ttu-id="e72c9-155">U gaat ook een lege basis module maken voor toekomstige Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="e72c9-155">I'm also going to create an empty root module for future PowerShell functions.</span></span>

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

<span data-ttu-id="e72c9-156">Zo kunt u zowel normale Power shell-functies als binaire cmdlets in hetzelfde project combi neren.</span><span class="sxs-lookup"><span data-stu-id="e72c9-156">This allows me to mix both normal PowerShell functions and binary Cmdlets in the same project.</span></span>

### <a name="building-the-full-module"></a><span data-ttu-id="e72c9-157">De volledige module bouwen</span><span class="sxs-lookup"><span data-stu-id="e72c9-157">Building the full module</span></span>

<span data-ttu-id="e72c9-158">Ik compileer alles samen in een uitvoermap.</span><span class="sxs-lookup"><span data-stu-id="e72c9-158">I compile everything together into an output folder.</span></span> <span data-ttu-id="e72c9-159">We moeten een bouw script maken om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-159">We need to create a build script to do that.</span></span> <span data-ttu-id="e72c9-160">Ik voeg dit normaal gesp roken toe aan een `Invoke-Build` script, maar we kunnen het eenvoudig voor dit voor beeld blijven gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e72c9-160">I would normally add this to an `Invoke-Build` script, but we can keep it simple for this example.</span></span> <span data-ttu-id="e72c9-161">Voeg dit toe aan een `build.ps1` aan de basis van het project.</span><span class="sxs-lookup"><span data-stu-id="e72c9-161">Add this to a `build.ps1` at the root of the project.</span></span>

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

<span data-ttu-id="e72c9-162">Met deze opdrachten bouwt u onze DLL en plaatst u deze in onze `output\$module\bin` map.</span><span class="sxs-lookup"><span data-stu-id="e72c9-162">These commands build our DLL and place it into our `output\$module\bin` folder.</span></span> <span data-ttu-id="e72c9-163">Vervolgens worden de andere module bestanden gekopieerd naar de locatie.</span><span class="sxs-lookup"><span data-stu-id="e72c9-163">It then copies the other module files into place.</span></span>

```
Output
└───MyModule
    │   MyModule.psd1
    │   MyModule.psm1
    │
    └───bin
            MyModule.deps.json
            MyModule.dll
            MyModule.pdb
```

<span data-ttu-id="e72c9-164">Op dit moment kunnen we onze module met het psd1-bestand importeren.</span><span class="sxs-lookup"><span data-stu-id="e72c9-164">At this point, we can import our module with the psd1 file.</span></span>

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

<span data-ttu-id="e72c9-165">Hier kunt u de map neerzetten `.\Output\$module` in onze `$env:PSModulePath` Directory en de opdracht wordt op elk gewenst moment geladen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-165">From here, we can drop the `.\Output\$module` folder into our `$env:PSModulePath` directory and it autoloads our command whenever we need it.</span></span>

### <a name="update-dotnet-new-psmodule"></a><span data-ttu-id="e72c9-166">Update: dotnet New PSModule</span><span class="sxs-lookup"><span data-stu-id="e72c9-166">Update: dotnet new PSModule</span></span>

<span data-ttu-id="e72c9-167">Ik heb geleerd dat het `dotnet` hulp programma een `PSModule` sjabloon heeft.</span><span class="sxs-lookup"><span data-stu-id="e72c9-167">I learned that the `dotnet` tool has a `PSModule` template.</span></span>

<span data-ttu-id="e72c9-168">Alle stappen die hieronder worden beschreven, zijn nog steeds geldig, maar deze sjabloon knipt veel hiervan uit. Er is nog steeds een redelijk nieuwe sjabloon aanwezig, waardoor er nog steeds een gepolijste manier wordt opgenomen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-168">All the steps that I outlined above are still valid, but this template cuts many of them out. It's still a fairly new template that is still getting some polish placed on it.</span></span> <span data-ttu-id="e72c9-169">Verwacht wordt dat u deze beter kunt blijven gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e72c9-169">Expect it to keep getting better from here.</span></span>

<span data-ttu-id="e72c9-170">Dit is de manier waarop u de PSModule-sjabloon installeert en gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e72c9-170">This is how you use install and use the PSModule template.</span></span>

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

<span data-ttu-id="e72c9-171">Deze sjabloon met minimale beschik bare sjablonen zorgt ervoor dat u de .NET SDK, de standaard bibliotheek van Power shell toevoegt en een voorbeeld klasse maakt in het project.</span><span class="sxs-lookup"><span data-stu-id="e72c9-171">This minimally-viable template takes care of adding the .NET SDK, PowerShell Standard Library, and creates an example class in the project.</span></span> <span data-ttu-id="e72c9-172">U kunt het bouwen en direct uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="e72c9-172">You can build it and run it right away.</span></span>

## <a name="important-details"></a><span data-ttu-id="e72c9-173">Belang rijke Details</span><span class="sxs-lookup"><span data-stu-id="e72c9-173">Important details</span></span>

<span data-ttu-id="e72c9-174">Voordat we dit artikel beëindigen, zijn hier enkele andere details te vermelden.</span><span class="sxs-lookup"><span data-stu-id="e72c9-174">Before we end this article, here are a few other details worth mentioning.</span></span>

### <a name="unloading-dlls"></a><span data-ttu-id="e72c9-175">Dll-bestanden verwijderen</span><span class="sxs-lookup"><span data-stu-id="e72c9-175">Unloading DLLs</span></span>

<span data-ttu-id="e72c9-176">Zodra een binaire module is geladen, kunt u deze niet verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-176">Once a binary module is loaded, you can't really unload it.</span></span> <span data-ttu-id="e72c9-177">Het DLL-bestand wordt vergrendeld totdat u het verwijdert.</span><span class="sxs-lookup"><span data-stu-id="e72c9-177">The DLL file is locked until you unload it.</span></span> <span data-ttu-id="e72c9-178">Dit kan vervelend zijn wanneer u een wijziging aanbrengt en u deze wilt bouwen, maar het bestand is vaak vergrendeld.</span><span class="sxs-lookup"><span data-stu-id="e72c9-178">This can be annoying when developing because every time you make a change and want to build it, the file is often locked.</span></span> <span data-ttu-id="e72c9-179">De enige betrouw bare manier om dit probleem op te lossen is het sluiten van de Power shell-sessie die de DLL heeft geladen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-179">The only reliable way to resolve this is to close the PowerShell session that loaded the DLL.</span></span>

### <a name="vs-code-reload-window-action"></a><span data-ttu-id="e72c9-180">De actie VS-code opnieuw laden</span><span class="sxs-lookup"><span data-stu-id="e72c9-180">VS Code reload window action</span></span>

<span data-ttu-id="e72c9-181">Ik voer de meeste van mijn Power shell-ontwikkel werkzaamheden uit in [VS code][].</span><span class="sxs-lookup"><span data-stu-id="e72c9-181">I do most of my PowerShell dev work in [VS Code][].</span></span> <span data-ttu-id="e72c9-182">Wanneer ik aan een binaire module (of een module met klassen) aan het werk ben, heb ik dan elke keer dat ik bouw, de code opnieuw geladen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-182">When I'm working on a binary module (or a module with classes), I've gotten into the habit of reloading VS Code every time I build.</span></span>
<span data-ttu-id="e72c9-183"><kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>P</kbd> het opdracht venster wordt weer gegeven en `Reload Window` is altijd aan de bovenkant van de lijst.</span><span class="sxs-lookup"><span data-stu-id="e72c9-183"><kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> pops the command window and `Reload Window` is always at the top of my list.</span></span>

### <a name="nested-powershell-sessions"></a><span data-ttu-id="e72c9-184">Geneste Power shell-sessies</span><span class="sxs-lookup"><span data-stu-id="e72c9-184">Nested PowerShell sessions</span></span>

<span data-ttu-id="e72c9-185">Een andere mogelijkheid is een goede dekkings test voor de ziekte te hebben.</span><span class="sxs-lookup"><span data-stu-id="e72c9-185">One other option is to have good Pester test coverage.</span></span> <span data-ttu-id="e72c9-186">Vervolgens kunt u het build.ps1 script aanpassen om een nieuwe Power shell-sessie te starten, de build uit te voeren, de tests uit te voeren en de sessie te sluiten.</span><span class="sxs-lookup"><span data-stu-id="e72c9-186">Then you can adjust the build.ps1 script to start a new PowerShell session, perform the build, run the tests, and close the session.</span></span>

### <a name="updating-installed-modules"></a><span data-ttu-id="e72c9-187">Geïnstalleerde modules bijwerken</span><span class="sxs-lookup"><span data-stu-id="e72c9-187">Updating installed modules</span></span>

<span data-ttu-id="e72c9-188">Deze vergren deling kan vervelend zijn wanneer u uw lokaal geïnstalleerde module wilt bijwerken.</span><span class="sxs-lookup"><span data-stu-id="e72c9-188">This locking can be annoying when trying to update your locally installed module.</span></span> <span data-ttu-id="e72c9-189">Als een sessie is geladen, moet u deze opsporen en sluiten.</span><span class="sxs-lookup"><span data-stu-id="e72c9-189">If any session has it loaded, you have to go hunt it down and close it.</span></span> <span data-ttu-id="e72c9-190">Dit is minder van een probleem bij de installatie vanaf een PSGallery, omdat de module versie beheer het nieuwe item in een andere map plaatst.</span><span class="sxs-lookup"><span data-stu-id="e72c9-190">This is less of an issue when installing from a PSGallery because module versioning places the new one in a different folder.</span></span>

<span data-ttu-id="e72c9-191">U kunt een lokale PSGallery instellen en deze publiceren als onderdeel van uw build.</span><span class="sxs-lookup"><span data-stu-id="e72c9-191">You can set up a local PSGallery and publish to that as part of your build.</span></span> <span data-ttu-id="e72c9-192">Voer vervolgens uw lokale installatie uit vanaf die PSGallery.</span><span class="sxs-lookup"><span data-stu-id="e72c9-192">Then do your local install from that PSGallery.</span></span> <span data-ttu-id="e72c9-193">Dit klinkt als veel werk, maar dit kan net zo eenvoudig zijn als het starten van een docker-container.</span><span class="sxs-lookup"><span data-stu-id="e72c9-193">This sounds like a lot of work, but this can be as simple as starting a docker container.</span></span> <span data-ttu-id="e72c9-194">Ik bevindt een manier om dit te doen in mijn post op het [gebruik van een NuGet-server voor een PSRepository][].</span><span class="sxs-lookup"><span data-stu-id="e72c9-194">I cover a way to do that in my post on [Using a NuGet server for a PSRepository][].</span></span>

## <a name="why-binary-modules"></a><span data-ttu-id="e72c9-195">Waarom binaire modules?</span><span class="sxs-lookup"><span data-stu-id="e72c9-195">Why binary modules?</span></span>

<span data-ttu-id="e72c9-196">Ik heb het recht om een binaire module te maken en heeft niet aangegeven waarom u er een wilt maken.</span><span class="sxs-lookup"><span data-stu-id="e72c9-196">I jumped right into how to make a binary module and didn't mention why you want to make one.</span></span> <span data-ttu-id="e72c9-197">In werkelijkheid schrijft u C# en kunt u eenvoudig toegang krijgen tot Power shell-cmdlets en-functies.</span><span class="sxs-lookup"><span data-stu-id="e72c9-197">In reality, you are writing C# and give up easy access to PowerShell Cmdlets and functions.</span></span> <span data-ttu-id="e72c9-198">Dit is de belangrijkste reden waarom ik eerder geen binaire modules heb verplaatst.</span><span class="sxs-lookup"><span data-stu-id="e72c9-198">That is the main reason why I have not shifted to binary modules sooner.</span></span>

<span data-ttu-id="e72c9-199">Maar als u een module maakt die niet afhankelijk is van een groot aantal Power shell-opdrachten, kan het prestatie voordeel aanzienlijk zijn.</span><span class="sxs-lookup"><span data-stu-id="e72c9-199">But if you are creating a module that doesn't depend on a lot of other PowerShell commands, the performance benefit can be significant.</span></span> <span data-ttu-id="e72c9-200">Door in C# te verwijderen, kunt u de overhead die is toegevoegd door Power shell uitbrengen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-200">By dropping into C#, you get to shed the overhead added by PowerShell.</span></span> <span data-ttu-id="e72c9-201">Power shell is geoptimaliseerd voor de beheerder en niet op de computer, waardoor er weinig overhead wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="e72c9-201">PowerShell was optimized for the administrator, not the computer, and that adds a little overhead.</span></span>

<span data-ttu-id="e72c9-202">Op het werk hebben we een kritiek proces dat veel werk met JSON en hashtabellen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-202">At work, we have a critical process that does a lot of work with JSON and Hashtables.</span></span> <span data-ttu-id="e72c9-203">We hebben de Power shell zoveel mogelijk geoptimaliseerd, maar dit proces werd 12 minuten nog steeds uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e72c9-203">We optimized the PowerShell as much as we could but this process was still running for 12 minutes.</span></span> <span data-ttu-id="e72c9-204">De module bevat al een heleboel C# style Power shell.</span><span class="sxs-lookup"><span data-stu-id="e72c9-204">The module already contained a lot of C# style PowerShell.</span></span> <span data-ttu-id="e72c9-205">Hierdoor is de conversie naar een binaire module schoon en eenvoudig.</span><span class="sxs-lookup"><span data-stu-id="e72c9-205">This made the conversion to a binary module clean and easy to do.</span></span> <span data-ttu-id="e72c9-206">Onze conversie knipt dat proces van meer dan 12 minuten tot minder dan vier minuten.</span><span class="sxs-lookup"><span data-stu-id="e72c9-206">Our conversion cut that process down from over 12 minutes to under four minutes.</span></span>

### <a name="hybrid-modules"></a><span data-ttu-id="e72c9-207">Hybride modules</span><span class="sxs-lookup"><span data-stu-id="e72c9-207">Hybrid modules</span></span>

<span data-ttu-id="e72c9-208">U kunt binaire cmdlets combi neren met geavanceerde Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="e72c9-208">You can mix binary Cmdlets with PowerShell advanced functions.</span></span> <span data-ttu-id="e72c9-209">Dat is precies wat ik in deze hand leiding doe.</span><span class="sxs-lookup"><span data-stu-id="e72c9-209">That is exactly what I'm doing in this guide.</span></span> <span data-ttu-id="e72c9-210">U kunt alles wat u weet over script modules en dit allemaal op dezelfde manier Toep assen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-210">You can take everything you know about script modules and it all applies the same way.</span></span>
<span data-ttu-id="e72c9-211">Het lege `psm1` bestand dat ik nu heb gemaakt, is op dit moment alleen mogelijk in andere Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="e72c9-211">The empty `psm1` file that I created today is there just so you can drop in other PowerShell functions later.</span></span>

<span data-ttu-id="e72c9-212">Bijna alle gecompileerde cmdlets die we hebben gemaakt, zijn de eerste keer gestart als een Power shell-functie.</span><span class="sxs-lookup"><span data-stu-id="e72c9-212">Almost all of the compiled cmdlets that we created started out as a PowerShell function first.</span></span> <span data-ttu-id="e72c9-213">Al onze binaire modules zijn eigenlijk hybride modules.</span><span class="sxs-lookup"><span data-stu-id="e72c9-213">All of our binary modules are really hybrid modules.</span></span>

### <a name="build-scripts"></a><span data-ttu-id="e72c9-214">Scripts maken</span><span class="sxs-lookup"><span data-stu-id="e72c9-214">Build scripts</span></span>

<span data-ttu-id="e72c9-215">Ik heb het opbouw script hier eenvoudig gehouden.</span><span class="sxs-lookup"><span data-stu-id="e72c9-215">I kept the build script simple here.</span></span> <span data-ttu-id="e72c9-216">Ik gebruik in het algemeen een groot `Invoke-Build` script als onderdeel van mijn CI/cd-pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e72c9-216">I generally use a large `Invoke-Build` script as part of my CI/CD pipeline.</span></span> <span data-ttu-id="e72c9-217">Het is meer Magic, zoals het uitvoeren van ziekte tests, het uitvoeren van PSScriptAnalyzer, het beheren van versie beheer en het publiceren naar de PSGallery.</span><span class="sxs-lookup"><span data-stu-id="e72c9-217">It does more magic like running Pester tests, running PSScriptAnalyzer, managing versioning, and publishing to the PSGallery.</span></span> <span data-ttu-id="e72c9-218">Nadat ik een build-script voor mijn modules heb gestart, heb ik veel dingen kunnen vinden om hieraan toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="e72c9-218">Once I started using a build script for my modules, I was able to find lots of things to add to it.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="e72c9-219">Laatste ideeën</span><span class="sxs-lookup"><span data-stu-id="e72c9-219">Final thoughts</span></span>

<span data-ttu-id="e72c9-220">Binaire modules zijn eenvoudig te maken.</span><span class="sxs-lookup"><span data-stu-id="e72c9-220">Binary modules are easy to create.</span></span> <span data-ttu-id="e72c9-221">Ik heb niet gereageerd op de C#-syntaxis voor het maken van een cmdlet, maar er is in de [Windows Power shell-SDK][]nog meer documentatie over.</span><span class="sxs-lookup"><span data-stu-id="e72c9-221">I didn't touch on the C# syntax for creating a Cmdlet, but there is plenty of documentation on it in the [Windows PowerShell SDK][].</span></span> <span data-ttu-id="e72c9-222">Het is een goed idee om te experimenteren met als steper-steen in meer ernstige C#.</span><span class="sxs-lookup"><span data-stu-id="e72c9-222">It is definitely something worth experimenting with as a stepping stone into more serious C#.</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[original version]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Standaard bibliotheek van Power shell]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard Library]: https://github.com/PowerShell/PowerShellStandard
[Een binaire module voor meerdere platforms maken]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[Creating a cross-platform binary module]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[DotNet core SDK]: https://www.microsoft.com/net/download/core
[dotnet core SDK]: https://www.microsoft.com/net/download/core
[Een NuGet-server gebruiken voor een PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Using a NuGet server for a PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[VS-code]: https://code.visualstudio.com
[VS Code]: https://code.visualstudio.com
[nuget-pakket]: https://www.nuget.org/packages/PowerShellStandard.Library/
[nuget package]: https://www.nuget.org/packages/PowerShellStandard.Library/
