---
description: Verschillende versies van Power shell die worden uitgevoerd op verschillende onderliggende Runtimes.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_editions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Editions
ms.openlocfilehash: 3b1b938874b36919a1a0627f3b492cbc961e4a2f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706085"
---
# <a name="about-powershell-editions"></a><span data-ttu-id="6e420-103">Over Power shell-edities</span><span class="sxs-lookup"><span data-stu-id="6e420-103">About PowerShell Editions</span></span>

## <a name="short-description"></a><span data-ttu-id="6e420-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="6e420-104">Short Description</span></span>
<span data-ttu-id="6e420-105">Verschillende versies van Power shell die worden uitgevoerd op verschillende onderliggende Runtimes.</span><span class="sxs-lookup"><span data-stu-id="6e420-105">Different editions of PowerShell run on different underlying runtimes.</span></span>

## <a name="long-description"></a><span data-ttu-id="6e420-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="6e420-106">Long Description</span></span>

<span data-ttu-id="6e420-107">Vanuit Power shell 5,1 zijn er meerdere *versies* van Power shell die elk worden uitgevoerd op een andere .NET-runtime.</span><span class="sxs-lookup"><span data-stu-id="6e420-107">From PowerShell 5.1, there are multiple *editions* of PowerShell that each run on a different .NET runtime.</span></span> <span data-ttu-id="6e420-108">Vanaf Power shell 6,2 zijn er twee versies van Power shell:</span><span class="sxs-lookup"><span data-stu-id="6e420-108">As of PowerShell 6.2 there are two editions of PowerShell:</span></span>

- <span data-ttu-id="6e420-109">**Bureau blad**, dat wordt uitgevoerd op .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e420-109">**Desktop**, which runs on .NET Framework.</span></span> <span data-ttu-id="6e420-110">Power Shell 4 en lager, en Power shell 5,1 op volledig uitgeruste Windows-edities zoals Windows Desktop, Windows Server, Windows Server Core en de meeste andere Windows-besturings systemen zijn Desktop Edition.</span><span class="sxs-lookup"><span data-stu-id="6e420-110">PowerShell 4 and below, as well as PowerShell 5.1 on full-featured Windows editions like Windows Desktop, Windows Server, Windows Server Core and most other Windows operating systems are Desktop edition.</span></span>
  <span data-ttu-id="6e420-111">Dit is de oorspronkelijke Power shell-editie.</span><span class="sxs-lookup"><span data-stu-id="6e420-111">This is the original PowerShell edition.</span></span>
- <span data-ttu-id="6e420-112">**Core**, die wordt uitgevoerd op .net core.</span><span class="sxs-lookup"><span data-stu-id="6e420-112">**Core**, which runs on .NET Core.</span></span> <span data-ttu-id="6e420-113">Power shell 6,0 en hoger, evenals Power shell 5,1 op sommige Windows-edities met een verminderde footprint, zoals Windows nano server en Windows IoT, waarbij .NET Framework niet beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="6e420-113">PowerShell 6.0 and above, as well as PowerShell 5.1 on some reduced-footprint Windows editions such as Windows Nano Server and Windows IoT where .NET Framework is unavailable.</span></span>

<span data-ttu-id="6e420-114">Omdat de editie van Power shell overeenkomt met de .NET runtime, is het de primaire indicator van de compatibiliteit van .NET API en Power shell-modules. Sommige .NET-Api's,-typen of-methoden zijn niet beschikbaar in .NET-Runtimes en zijn van invloed op Power shell-scripts en-modules die hiervan afhankelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="6e420-114">Because the edition of PowerShell corresponds to its .NET runtime, it is the primary indicator of .NET API and PowerShell module compatibility; some .NET APIs, types or methods are not available in both .NET runtimes and this affects PowerShell scripts and modules that depend on them.</span></span>

## <a name="the-psedition-automatic-variable"></a><span data-ttu-id="6e420-115">De `$PSEdition` Automatische variabele</span><span class="sxs-lookup"><span data-stu-id="6e420-115">The `$PSEdition` automatic variable</span></span>

<span data-ttu-id="6e420-116">In Power shell 5,1 en hoger kunt u zien welke editie u uitvoert met de `$PSEdition` Automatische variabele:</span><span class="sxs-lookup"><span data-stu-id="6e420-116">In PowerShell 5.1 and above, you can find out what edition you are running with the `$PSEdition` automatic variable:</span></span>

```powershell
$PSEdition
```

```Output
Core
```

<span data-ttu-id="6e420-117">Deze variabele bestaat niet in Power Shell 4 en lager.</span><span class="sxs-lookup"><span data-stu-id="6e420-117">In PowerShell 4 and below, this variable does not exist.</span></span> <span data-ttu-id="6e420-118">`$PSEdition` Null moet worden behandeld als gelijk aan de waarde `Desktop` .</span><span class="sxs-lookup"><span data-stu-id="6e420-118">`$PSEdition` being null should be treated as the same as having the value `Desktop`.</span></span>

### <a name="edition-in-psversiontable"></a><span data-ttu-id="6e420-119">Edition in `$PSVersionTable`</span><span class="sxs-lookup"><span data-stu-id="6e420-119">Edition in `$PSVersionTable`</span></span>

<span data-ttu-id="6e420-120">De `$PSVersionTable` Automatische variabele bevat ook editie-informatie in Power shell 5,1 en hoger:</span><span class="sxs-lookup"><span data-stu-id="6e420-120">The `$PSVersionTable` automatic variable also has edition information in PowerShell 5.1 and above:</span></span>

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      6.2.0-rc.1
PSEdition                      Core           # <-- Edition information
GitCommitId                    6.2.0-rc.1
OS                             Microsoft Windows 10.0.18865
Platform                       Win32NT
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
WSManStackVersion              3.0
```

<span data-ttu-id="6e420-121">Het `PSEdition` veld heeft dezelfde waarde als de `$PSEdition` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="6e420-121">The `PSEdition` field will have the same value as the `$PSEdition` automatic variable.</span></span>

## <a name="the-compatiblepseditions-module-manifest-field"></a><span data-ttu-id="6e420-122">Het `CompatiblePSEditions` veld module manifest</span><span class="sxs-lookup"><span data-stu-id="6e420-122">The `CompatiblePSEditions` module manifest field</span></span>

<span data-ttu-id="6e420-123">Power shell-modules kunnen declareren in welke versies van Power shell ze compatibel zijn met behulp `CompatiblePSEditions` van het veld van het module manifest.</span><span class="sxs-lookup"><span data-stu-id="6e420-123">PowerShell modules can declare what editions of PowerShell they are compatible with using the `CompatiblePSEditions` field of the module manifest.</span></span>

<span data-ttu-id="6e420-124">Een module manifest dat bijvoorbeeld compatibiliteit met zowel-als- `Desktop` `Core` edities van Power shell declareert:</span><span class="sxs-lookup"><span data-stu-id="6e420-124">For example, a module manifest declaring compatibility with both `Desktop` and `Core` editions of PowerShell:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

<span data-ttu-id="6e420-125">Een voor beeld van een module manifest met alleen `Desktop` Compatibiliteit:</span><span class="sxs-lookup"><span data-stu-id="6e420-125">An example of a module manifest with only `Desktop` compatibility:</span></span>

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

<span data-ttu-id="6e420-126">Het weglaten `CompatiblePSEditions` van het veld uit een module manifest heeft hetzelfde effect als het instellen op `Desktop` , omdat modules die zijn gemaakt voordat dit veld werd geïntroduceerd, impliciet werden geschreven voor deze editie.</span><span class="sxs-lookup"><span data-stu-id="6e420-126">Omitting the `CompatiblePSEditions` field from a module manifest will have the same effect as setting it to `Desktop`, since modules created before this field was introduced were implicitly written for this edition.</span></span>

<span data-ttu-id="6e420-127">Voor modules die niet worden geleverd als onderdeel van Windows (modules die u schrijft of installeert vanuit de galerie), is dit veld alleen ter informatie. Power shell verandert geen gedrag op basis van het `CompatiblePSEditions` veld, maar maakt het op het `PSModuleInfo` object zichtbaar (geretourneerd door `Get-Module` ) voor uw eigen logica:</span><span class="sxs-lookup"><span data-stu-id="6e420-127">For modules not shipped as part of Windows (i.e. modules you write or install from the gallery), this field is informational only; PowerShell does not change behavior based on the `CompatiblePSEditions` field, but does expose it on the `PSModuleInfo` object (returned by `Get-Module`) for your own logic:</span></span>

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion '5.1'
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

> [!NOTE]
> <span data-ttu-id="6e420-128">Het `CompatiblePSEditions` module veld is alleen compatibel met Power shell 5,1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="6e420-128">The `CompatiblePSEditions` module field is only compatible with PowerShell 5.1 and above.</span></span>
> <span data-ttu-id="6e420-129">Met inbegrip van dit veld wordt een module niet compatibel met Power Shell 4 en lager.</span><span class="sxs-lookup"><span data-stu-id="6e420-129">Including this field will cause a module to be incompatible with PowerShell 4 and below.</span></span>
> <span data-ttu-id="6e420-130">Omdat het veld louter informatief is, kan het veilig worden wegge laten in latere Power shell-versies.</span><span class="sxs-lookup"><span data-stu-id="6e420-130">Since the field is purely informational, it can be safely omitted in later PowerShell versions.</span></span>

<span data-ttu-id="6e420-131">In Power shell 6,1 `Get-Module -ListAvailable` heeft de indelings functie bijgewerkt om de editie-compatibiliteit van elke module weer te geven:</span><span class="sxs-lookup"><span data-stu-id="6e420-131">In PowerShell 6.1, `Get-Module -ListAvailable` has had its formatter updated to display the edition-compatibility of each module:</span></span>

```PowerShell
Get-Module -ListAvailable
```

```Output

    Directory: C:\Users\me\Documents\PowerShell\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Script     1.4.0      Az                                  Core,Desk
Script     1.3.1      Az.Accounts                         Core,Desk {Disable-AzDataCollection, Disable-AzContextAutosave, E...
Script     1.0.1      Az.Aks                              Core,Desk {Get-AzAks, New-AzAks, Remove-AzAks, Import-AzAksCreden...

...

Script     4.4.0      Pester                              Desk      {Describe, Context, It, Should...}
Script     1.18.0     PSScriptAnalyzer                    Desk      {Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer, Invoke-...
Script     1.0.0      WindowsCompatibility                Core      {Initialize-WinSession, Add-WinFunction, Invoke-WinComm...

```

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a><span data-ttu-id="6e420-132">Editie-compatibiliteit voor modules die worden geleverd als onderdeel van Windows</span><span class="sxs-lookup"><span data-stu-id="6e420-132">Edition-compatibility for modules that ship as part of Windows</span></span>

<span data-ttu-id="6e420-133">Voor modules die deel uitmaken van Windows (of die zijn geïnstalleerd als onderdeel van een functie of onderdeel), wordt het veld anders behandeld in Power shell 6,1 en hoger `CompatiblePSEditions` .</span><span class="sxs-lookup"><span data-stu-id="6e420-133">For modules that come as part of Windows (or are installed as part of a role or feature), PowerShell 6.1 and above treat the `CompatiblePSEditions` field differently.</span></span> <span data-ttu-id="6e420-134">Dergelijke modules vindt u in de Directory systeem modules van Windows Power shell ( `%windir%\System\WindowsPowerShell\v1.0\Modules` ).</span><span class="sxs-lookup"><span data-stu-id="6e420-134">Such modules are found in the Windows PowerShell system modules directory (`%windir%\System\WindowsPowerShell\v1.0\Modules`).</span></span>

<span data-ttu-id="6e420-135">Voor modules die zijn geladen vanuit of gevonden in deze map, gebruikt Power shell 6,1 en hoger het `CompatiblePSEditions` veld om te bepalen of de module compatibel is met de huidige sessie en zich dienovereenkomstig gedraagt.</span><span class="sxs-lookup"><span data-stu-id="6e420-135">For modules loaded from or found in this directory, PowerShell 6.1 and above uses the `CompatiblePSEditions` field to determine whether the module will be compatible with the current session and behaves accordingly.</span></span>

<span data-ttu-id="6e420-136">Wanneer `Import-Module` wordt gebruikt, wordt een module zonder `Core` in `CompatiblePSEditions` niet geïmporteerd en wordt er een fout melding weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="6e420-136">When `Import-Module` is used, a module without `Core` in `CompatiblePSEditions` will not be imported and an error will be displayed:</span></span>

```powershell
Import-Module BitsTransfer
```

```Output
Import-Module : Module 'C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1' does not support current PowerShell edition 'Core'. Its supported editions are 'Desktop'. Use 'Import-Module -SkipEditionCheck' to ignore the compatibility of this module.
At line:1 char:1
+ Import-Module BitsTransfer
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : ResourceUnavailable: (C:\WINDOWS\system32\u2026r\BitsTransfer.psd1:String) [Import-Module], InvalidOperationException
+ FullyQualifiedErrorId : Modules_PSEditionNotSupported,Microsoft.PowerShell.Commands.ImportModuleCommand
```

<span data-ttu-id="6e420-137">Als `Get-Module -ListAvailable` wordt gebruikt, worden modules zonder `Core` in `CompatiblePSEditions` niet weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="6e420-137">When `Get-Module -ListAvailable` is used, modules without `Core` in `CompatiblePSEditions` will not be displayed:</span></span>

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

<span data-ttu-id="6e420-138">In beide gevallen kan de `-SkipEditionCheck` para meter switch worden gebruikt om dit gedrag te negeren:</span><span class="sxs-lookup"><span data-stu-id="6e420-138">In both cases, the `-SkipEditionCheck` switch parameter can be used to override this behavior:</span></span>

```powershell
Get-Module -ListAvailable -SkipEditionCheck BitsTransfer
```

```Output

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.0.0    BitsTransfer                        Desk      {Add-BitsFile, Complete-BitsTransfer, Get-BitsTransfer,...

```

> [!WARNING]
> <span data-ttu-id="6e420-139">`Import-Module -SkipEditionCheck` lijkt voor een module te slagen, maar het gebruik van die module voert het risico op een later tijdstip van compatibiliteit tegen problemen uit. terwijl het laden van de module in eerste instantie slaagt, kan een opdracht later een incompatibele API aanroepen en spon Taan mislukken.</span><span class="sxs-lookup"><span data-stu-id="6e420-139">`Import-Module -SkipEditionCheck` may appear to succeed for a module, but using that module runs the risk of encountering an incompatibility later on; while loading the module initially succeeds, a command may later call an incompatible API and fail spontaneously.</span></span>

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a><span data-ttu-id="6e420-140">Power shell-modules ontwerpen voor compatibiliteit tussen versies</span><span class="sxs-lookup"><span data-stu-id="6e420-140">Authoring PowerShell modules for edition cross-compatibility</span></span>

<span data-ttu-id="6e420-141">Wanneer u een Power shell-module schrijft om te richten op zowel `Desktop` `Core` -als-edities van Power shell, zijn er dingen die u kunt doen om compatibiliteit met meerdere edities te garanderen.</span><span class="sxs-lookup"><span data-stu-id="6e420-141">When writing a PowerShell module to target both `Desktop` and `Core` editions of PowerShell, there are things you can do to ensure cross-edition compatibility.</span></span>

<span data-ttu-id="6e420-142">De enige manier om compatibiliteit te bevestigen en voortdurend te valideren is het schrijven van tests voor uw script of module, en het uitvoeren ervan op alle versies en edities van Power shell waarvoor u compatibiliteit nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="6e420-142">The only true way to confirm and continually validate compatibility however is to write tests for your script or module and run them on all versions and editions of PowerShell you need compatibility with.</span></span> <span data-ttu-id="6e420-143">Een aanbevolen test raamwerk voor dit is een [ziekte][].</span><span class="sxs-lookup"><span data-stu-id="6e420-143">A recommended testing framework for this is [Pester][].</span></span>

### <a name="powershell-script"></a><span data-ttu-id="6e420-144">PowerShell-script</span><span class="sxs-lookup"><span data-stu-id="6e420-144">PowerShell script</span></span>

<span data-ttu-id="6e420-145">Power shell werkt als een taal hetzelfde tussen de edities. Dit zijn de cmdlets, modules en .NET-Api's die u gebruikt die worden beïnvloed door editie compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="6e420-145">As a language, PowerShell works the same between editions; it is the cmdlets, modules and .NET APIs you use that are affected by edition compatibility.</span></span>

<span data-ttu-id="6e420-146">Scripts die in Power shell 6,1 en hoger werken, werken meestal met Windows Power shell 5,1, maar er zijn enkele uitzonde ringen.</span><span class="sxs-lookup"><span data-stu-id="6e420-146">Generally, scripts that work in PowerShell 6.1 and above will work with Windows PowerShell 5.1, but there are some exceptions.</span></span>

<span data-ttu-id="6e420-147">De module versie 1.18.0 [PSScriptAnalyzer][] bevat regels zoals [`PSUseCompatibleCommands`][] en [`PSUseCompatibleTypes`][] die mogelijk incompatibel gebruik van opdrachten en .net-api's in Power shell-scripts kunnen detecteren.</span><span class="sxs-lookup"><span data-stu-id="6e420-147">Version 1.18.0 [PSScriptAnalyzer][] module has rules like [`PSUseCompatibleCommands`][] and [`PSUseCompatibleTypes`][] that are able to detect possibly incompatible usage of commands and .NET APIs in PowerShell scripts.</span></span>

### <a name="net-assemblies"></a><span data-ttu-id="6e420-148">.NET-assembly's</span><span class="sxs-lookup"><span data-stu-id="6e420-148">.NET assemblies</span></span>

<span data-ttu-id="6e420-149">Als u een binaire module schrijft of een module die .NET-assembly's (Dll's) bevat die zijn gegenereerd op basis van de bron code, moet u zich compileren op basis van [.NET Standard][] en [Power shell Standard][] voor het valideren van de compatibiliteit van .net-en Power shell-API-compatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="6e420-149">If you are writing a binary module or a module that incorporates .NET assemblies (DLLs) generated from source code, you should compile against [.NET Standard][] and [PowerShell Standard][] for compile-time compatibility validation of .NET and PowerShell API compatibility.</span></span>

<span data-ttu-id="6e420-150">Hoewel deze bibliotheken tijdens de compilatie enige compatibiliteit kunnen controleren, kunnen ze geen mogelijke gedrags verschillen tussen de edities ondervangen.</span><span class="sxs-lookup"><span data-stu-id="6e420-150">Although these libraries are able to check some compatibility at compile time, they won't be able to catch possible behavioral differences between editions.</span></span> <span data-ttu-id="6e420-151">Voor dit moet u nog steeds tests schrijven.</span><span class="sxs-lookup"><span data-stu-id="6e420-151">For this you must still write tests.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e420-152">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6e420-152">See also</span></span>

- [<span data-ttu-id="6e420-153">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="6e420-153">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="6e420-154">Import-module</span><span class="sxs-lookup"><span data-stu-id="6e420-154">Import-Module</span></span>](xref:Microsoft.PowerShell.Core.Import-Module)
- [<span data-ttu-id="6e420-155">Get-module</span><span class="sxs-lookup"><span data-stu-id="6e420-155">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)
- [<span data-ttu-id="6e420-156">Modules met compatibele Power shell-edities</span><span class="sxs-lookup"><span data-stu-id="6e420-156">Modules with compatible PowerShell Editions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
['PSUseCompatibleCommands']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
[`PSUseCompatibleCommands`]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
['PSUseCompatibleTypes']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[`PSUseCompatibleTypes`]: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[Power Shell-standaard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
[PowerShell Standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
