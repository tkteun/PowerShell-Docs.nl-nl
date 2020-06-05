---
title: Script modules
description: Script modules zijn een eenvoudige manier om scripts en functies te verpakken in een herbruikbaar hulp programma.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 661ba725764e1f31df628f6c5f2d58d760656e37
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84436510"
---
# <a name="chapter-10---script-modules"></a><span data-ttu-id="63f73-103">Hoofd stuk 10: script modules</span><span class="sxs-lookup"><span data-stu-id="63f73-103">Chapter 10 - Script modules</span></span>

<span data-ttu-id="63f73-104">Het is nog belang rijker om uw one-Lines en scripts in Power shell in te scha kelen in herbruikbare Program ma's.</span><span class="sxs-lookup"><span data-stu-id="63f73-104">Turning your one-liners and scripts in PowerShell into reusable tools becomes even more important if it's something that you're going to use frequently.</span></span> <span data-ttu-id="63f73-105">Als u uw functies in een script module verdeelt, zien ze er professioneel uit en zijn ze gemakkelijker te delen.</span><span class="sxs-lookup"><span data-stu-id="63f73-105">Packaging your functions in a script module makes them look and feel more professional and makes them easier to share.</span></span>

## <a name="dot-sourcing-functions"></a><span data-ttu-id="63f73-106">Functies van punt en sourcing</span><span class="sxs-lookup"><span data-stu-id="63f73-106">Dot-Sourcing Functions</span></span>

<span data-ttu-id="63f73-107">Iets wat we in het vorige hoofd stuk niet hebben gecommuniceerd, is de functie dot.</span><span class="sxs-lookup"><span data-stu-id="63f73-107">Something that we didn't talk about in the previous chapter is dot-sourcing functions.</span></span> <span data-ttu-id="63f73-108">Wanneer een functie in een script geen deel uitmaakt van een module, is de enige manier om deze in het geheugen te laden, het `.PS1` bestand dat wordt opgeslagen in te delen met een punt.</span><span class="sxs-lookup"><span data-stu-id="63f73-108">When a function in a script isn't part of a module, the only way to load it into memory is to dot-source the `.PS1` file that it's saved in.</span></span>

<span data-ttu-id="63f73-109">De volgende functie is opgeslagen als `Get-MrPSVersion.ps1` .</span><span class="sxs-lookup"><span data-stu-id="63f73-109">The following function has been saved as `Get-MrPSVersion.ps1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}
```

<span data-ttu-id="63f73-110">Wanneer u het script uitvoert, gebeurt er niets.</span><span class="sxs-lookup"><span data-stu-id="63f73-110">When you run the script, nothing happens.</span></span>

```powershell
.\Get-MrPSVersion.ps1
```

<span data-ttu-id="63f73-111">Als u probeert de functie aan te roepen, wordt een fout bericht gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="63f73-111">If you try to call the function, it generates an error message.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Get-MrPSVersion : The term 'Get-MrPSVersion' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [], CommandNotFou
   ndException
    + FullyQualifiedErrorId : CommandNotFoundException

```

<span data-ttu-id="63f73-112">U kunt bepalen of functies in het geheugen worden geladen door te controleren of deze bestaan in de **functie** PSDrive.</span><span class="sxs-lookup"><span data-stu-id="63f73-112">You can determine if functions are loaded into memory by checking to see if they exist on the **Function** PSDrive.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
Get-ChildItem : Cannot find path 'Get-MrPSVersion' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path Function:\Get-MrPSVersion
    + CategoryInfo          : ObjectNotFound: (Get-MrPSVersion:String) [Get-ChildItem],
   ItemNotFoundException
    + FullyQualifiedErrorId : PathNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
```

<span data-ttu-id="63f73-113">Het probleem met het aanroepen van het script dat de functie bevat, is dat de functies worden geladen in het _script_ bereik.</span><span class="sxs-lookup"><span data-stu-id="63f73-113">The problem with calling the script that contains the function is that the functions are loaded in the _Script_ scope.</span></span> <span data-ttu-id="63f73-114">Wanneer het script is voltooid, wordt dat bereik verwijderd en wordt de functie Hiermee verwijderd.</span><span class="sxs-lookup"><span data-stu-id="63f73-114">When the script completes, that scope is removed and the function is removed with it.</span></span>

<span data-ttu-id="63f73-115">De functie moet worden geladen in het _globale_ bereik.</span><span class="sxs-lookup"><span data-stu-id="63f73-115">The function needs to be loaded into the _Global_ scope.</span></span> <span data-ttu-id="63f73-116">Dit kan worden bereikt door punt: het script dat de functie bevat.</span><span class="sxs-lookup"><span data-stu-id="63f73-116">That can be accomplished by dot-sourcing the script that contains the function.</span></span> <span data-ttu-id="63f73-117">Het relatieve pad kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="63f73-117">The relative path can be used.</span></span>

```powershell
. .\Get-MrPSVersion.ps1
```

<span data-ttu-id="63f73-118">Het volledig gekwalificeerde pad kan ook worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="63f73-118">The fully qualified path can also be used.</span></span>

```powershell
. C:\Demo\Get-MrPSVersion.ps1
```

<span data-ttu-id="63f73-119">Als een deel van het pad wordt opgeslagen in een variabele, kan dit worden gecombineerd met de rest van het pad.</span><span class="sxs-lookup"><span data-stu-id="63f73-119">If a portion of the path is stored in a variable, it can be combined with the remainder of the path.</span></span>
<span data-ttu-id="63f73-120">Er is geen reden om teken reeks koppeling te gebruiken om de variabele samen te voegen met de rest van het pad.</span><span class="sxs-lookup"><span data-stu-id="63f73-120">There's no reason to use string concatenation to combine the variable together with the remainder of the path.</span></span>

```powershell
$Path = 'C:\'
. $Path\Get-MrPSVersion.ps1
```

<span data-ttu-id="63f73-121">Wanneer ik de **functie** PSDrive Controleer, is de `Get-MrPSVersion` functie nu aanwezig.</span><span class="sxs-lookup"><span data-stu-id="63f73-121">Now when I check the **Function** PSDrive, the `Get-MrPSVersion` function exists.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-MrPSVersion
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-MrPSVersion
```

## <a name="script-modules"></a><span data-ttu-id="63f73-122">Script modules</span><span class="sxs-lookup"><span data-stu-id="63f73-122">Script Modules</span></span>

<span data-ttu-id="63f73-123">Een script module in Power shell is een bestand met een of meer functies die als een bestand worden opgeslagen `.PSM1` in plaats van een `.PS1` bestand.</span><span class="sxs-lookup"><span data-stu-id="63f73-123">A script module in PowerShell is simply a file containing one or more functions that's saved as a `.PSM1` file instead of a `.PS1` file.</span></span>

<span data-ttu-id="63f73-124">Hoe maak ik een script module?</span><span class="sxs-lookup"><span data-stu-id="63f73-124">How do you create a script module?</span></span> <span data-ttu-id="63f73-125">Waarschijnlijk raden we u aan een opdracht met de naam iets zoals `New-Module` .</span><span class="sxs-lookup"><span data-stu-id="63f73-125">You're probably guessing with a command named something like `New-Module`.</span></span> <span data-ttu-id="63f73-126">De veronderstelling is onjuist.</span><span class="sxs-lookup"><span data-stu-id="63f73-126">Your assumption would be wrong.</span></span> <span data-ttu-id="63f73-127">Terwijl er een opdracht in Power shell wordt genoemd `New-Module` , wordt met deze opdracht een dynamische module gemaakt en niet een script module.</span><span class="sxs-lookup"><span data-stu-id="63f73-127">While there is a command in PowerShell named `New-Module`, that command creates a dynamic module, not a script module.</span></span> <span data-ttu-id="63f73-128">Lees altijd de Help-informatie voor een opdracht, zelfs als u denkt dat u de gewenste opdracht hebt gevonden.</span><span class="sxs-lookup"><span data-stu-id="63f73-128">Always be sure to read the help for a command even when you think you've found the command you need.</span></span>

```powershell
help New-Module
```

```Output
NAME
    New-Module

SYNOPSIS
    Creates a new dynamic module that exists only in memory.

SYNTAX
    New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-ArgumentList <Object[]>]
    [-AsCustomObject] [-Cmdlet <String[]>] [-Function <String[]>] [-ReturnResult]
    [<CommonParameters>]

DESCRIPTION
    The New-Module cmdlet creates a dynamic module from a script block. The members of
    the dynamic module, such as functions and variables, are immediately available in
    the session and remain available until you close the session.

    Like static modules, by default, the cmdlets and functions in a dynamic module are
    exported and the variables and aliases are not. However, you can use the
    Export-ModuleMember cmdlet and the parameters of New-Module to override the defaults.

    You can also use the AsCustomObject parameter of New-Module to return the dynamic
    module as a custom object. The members of the modules, such as functions, are
    implemented as script methods of the custom object instead of being imported into
    the session.

    Dynamic modules exist only in memory, not on disk. Like all modules, the members of
    dynamic modules run in a private module scope that is a child of the global scope.
    Get-Module cannot get a dynamic module, but Get-Command can get the exported members.

    To make a dynamic module available to Get-Module , pipe a New-Module command to
    Import-Module, or pipe the module object that New-Module returns to Import-Module .
    This action adds the dynamic module to the Get-Module list, but it does not save the
    module to disk or make it persistent.

RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821495
    Export-ModuleMember
    Get-Module
    Import-Module
    Remove-Module

REMARKS
    To see the examples, type: "get-help New-Module -examples".
    For more information, type: "get-help New-Module -detailed".
    For technical information, type: "get-help New-Module -full".
    For online help, type: "get-help New-Module -online"
```

<span data-ttu-id="63f73-129">In het vorige hoofd stuk werd vermeld dat de functies goedgekeurde werk woorden moeten gebruiken, anders wordt er een waarschuwings bericht gegenereerd wanneer de module wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="63f73-129">In the previous chapter, I mentioned that functions should use approved verbs otherwise they'll generate a warning message when the module is imported.</span></span> <span data-ttu-id="63f73-130">De volgende code gebruikt de `New-Module` cmdlet om een dynamische module in het geheugen te maken.</span><span class="sxs-lookup"><span data-stu-id="63f73-130">The following code uses the `New-Module` cmdlet to create a dynamic module in memory.</span></span> <span data-ttu-id="63f73-131">In deze module wordt de waarschuwing over een niet-goedgekeurde term gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="63f73-131">This module demonstrates the unapproved verb warning.</span></span>

```powershell
New-Module -Name MyModule -ScriptBlock {

    function Return-MrOsVersion {
        Get-CimInstance -ClassName Win32_OperatingSystem |
        Select-Object -Property @{label='OperatingSystem';expression={$_.Caption}}
    }

    Export-ModuleMember -Function Return-MrOsVersion

} | Import-Module
```

```Output
WARNING: The names of some imported commands from the module 'MyModule' include
unapproved verbs that might make them less discoverable. To find the commands with
unapproved verbs, run the Import-Module command again with the Verbose parameter. For a
list of approved verbs, type Get-Verb.
```

<span data-ttu-id="63f73-132">Net als `New-Module` in het vorige voor beeld, is dat niet de opdracht voor het maken van script modules in Power shell.</span><span class="sxs-lookup"><span data-stu-id="63f73-132">Just to reiterate, although the `New-Module` cmdlet was used in the previous example, that's not the command for creating script modules in PowerShell.</span></span>

<span data-ttu-id="63f73-133">Sla de volgende twee functies op in een bestand met de naam `MyScriptModule.psm1` .</span><span class="sxs-lookup"><span data-stu-id="63f73-133">Save the following two functions in a file named `MyScriptModule.psm1`.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}
```

<span data-ttu-id="63f73-134">Probeer een van de functies aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="63f73-134">Try to call one of the functions.</span></span>

```powershell
Get-MrComputerName
```

```Output
Get-MrComputerName : The term 'Get-MrComputerName' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-MrComputerName
    + CategoryInfo          : ObjectNotFound: (Get-MrComputerName:String) [], CommandNot
   FoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="63f73-135">Er wordt een fout bericht gegenereerd met de melding dat de functie niet kan worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="63f73-135">An error message is generated saying the function can't be found.</span></span> <span data-ttu-id="63f73-136">U kunt ook de **functie** PSDrive controleren, net zoals eerder, en u zult zien dat deze niet aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="63f73-136">You could also check the **Function** PSDrive just like before and you'll find that it doesn't exist there either.</span></span>

<span data-ttu-id="63f73-137">U kunt het bestand hand matig met de `Import-Module` cmdlet importeren.</span><span class="sxs-lookup"><span data-stu-id="63f73-137">You could manually import the file with the `Import-Module` cmdlet.</span></span>

```powershell
Import-Module C:\MyScriptModule.psm1
```

<span data-ttu-id="63f73-138">De functie voor het autoladen van module is geïntroduceerd in Power shell versie 3.</span><span class="sxs-lookup"><span data-stu-id="63f73-138">The module autoloading feature was introduced in PowerShell version 3.</span></span> <span data-ttu-id="63f73-139">Een script module moet worden opgeslagen in een map met dezelfde basis naam als het `.PSM1` bestand en op een locatie die is opgegeven in om te profiteren van het autoloaden van module `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="63f73-139">To take advantage of module autoloading, a script module needs to be saved in a folder with the same base name as the `.PSM1` file and in a location specified in `$env:PSModulePath`.</span></span>

```powershell
$env:PSModulePath
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules;C:\Program Files\WindowsPowerShell\
Modules;C:\Windows\system32\WindowsPowerShell\v1.0\Modules;C:\Program Files (x86)\Microsof
t SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="63f73-140">De resultaten zijn moeilijk te lezen.</span><span class="sxs-lookup"><span data-stu-id="63f73-140">The results are difficult to read.</span></span> <span data-ttu-id="63f73-141">Aangezien de paden worden gescheiden door een punt komma, kunt u de resultaten splitsen om elk pad op een afzonderlijke regel te retour neren.</span><span class="sxs-lookup"><span data-stu-id="63f73-141">Since the paths are separated by a semicolon, you can split the results to return each path on a separate line.</span></span> <span data-ttu-id="63f73-142">Dit maakt het gemakkelijker om ze te lezen.</span><span class="sxs-lookup"><span data-stu-id="63f73-142">This makes them easier to read.</span></span>

```powershell
$env:PSModulePath -split ';'
```

```Output
C:\Users\mike-ladm\Documents\WindowsPowerShell\Modules
C:\Program Files\WindowsPowerShell\Modules
C:\Windows\system32\WindowsPowerShell\v1.0\Modules
C:\Program Files (x86)\Microsoft SQL Server\130\Tools\PowerShell\Modules\
```

<span data-ttu-id="63f73-143">De eerste drie paden in de lijst zijn de standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="63f73-143">The first three paths in the list are the default.</span></span> <span data-ttu-id="63f73-144">Als SQL Server Management Studio is geïnstalleerd, is het laatste pad toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="63f73-144">When SQL Server Management Studio was installed, it added the last path.</span></span> <span data-ttu-id="63f73-145">Als u de module autoloading wilt gebruiken, `MyScriptModule.psm1` moet het bestand zich bevinden in een map met de naam `MyScriptModule` direct in een van deze paden.</span><span class="sxs-lookup"><span data-stu-id="63f73-145">For module autoloading to work, the `MyScriptModule.psm1` file needs to be located in a folder named `MyScriptModule` directly inside one of those paths.</span></span>

<span data-ttu-id="63f73-146">Niet zo snel.</span><span class="sxs-lookup"><span data-stu-id="63f73-146">Not so fast.</span></span> <span data-ttu-id="63f73-147">Voor mij is mijn huidige gebruikers pad niet de eerste in de lijst.</span><span class="sxs-lookup"><span data-stu-id="63f73-147">For me, my current user path isn't the first one in the list.</span></span> <span data-ttu-id="63f73-148">Ik gebruik dit pad bijna nooit omdat ik me bij Windows aanmeld met een andere gebruiker dan het account dat ik gebruik om Power shell uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="63f73-148">I almost never use that path since I log into Windows with a different user than the one I use to run PowerShell.</span></span> <span data-ttu-id="63f73-149">Dit betekent dat het zich niet in de map normale documenten bevindt.</span><span class="sxs-lookup"><span data-stu-id="63f73-149">That means it's not located in my normal Documents folder.</span></span>

<span data-ttu-id="63f73-150">Het tweede pad is het **ALLUSERS** -pad.</span><span class="sxs-lookup"><span data-stu-id="63f73-150">The second path is the **AllUsers** path.</span></span> <span data-ttu-id="63f73-151">Dit is de locatie waar ik al mijn modules Bewaar.</span><span class="sxs-lookup"><span data-stu-id="63f73-151">This is the location where I store all of my modules.</span></span>

<span data-ttu-id="63f73-152">Het derde pad staat eronder `C:\Windows\System32` .</span><span class="sxs-lookup"><span data-stu-id="63f73-152">The third path is underneath `C:\Windows\System32`.</span></span> <span data-ttu-id="63f73-153">Alleen micro soft moet modules op die locatie opslaan, omdat deze zich in de map besturings systeem bevindt.</span><span class="sxs-lookup"><span data-stu-id="63f73-153">Only Microsoft should be storing modules in that location since it resides within the operating systems folder.</span></span>

<span data-ttu-id="63f73-154">Zodra het `.PSM1` bestand zich in het juiste pad bevindt, wordt de module automatisch geladen wanneer een van de opdrachten wordt genoemd.</span><span class="sxs-lookup"><span data-stu-id="63f73-154">Once the `.PSM1` file is located in the correct path, the module will load automatically when one of its commands is called.</span></span>

## <a name="module-manifests"></a><span data-ttu-id="63f73-155">Module manifesten</span><span class="sxs-lookup"><span data-stu-id="63f73-155">Module Manifests</span></span>

<span data-ttu-id="63f73-156">Alle modules moeten een module manifest hebben.</span><span class="sxs-lookup"><span data-stu-id="63f73-156">All modules should have a module manifest.</span></span> <span data-ttu-id="63f73-157">Een module manifest bevat meta gegevens over uw module.</span><span class="sxs-lookup"><span data-stu-id="63f73-157">A module manifest contains metadata about your module.</span></span>
<span data-ttu-id="63f73-158">De bestands extensie voor een manifest bestand van de module is `.PSD1` .</span><span class="sxs-lookup"><span data-stu-id="63f73-158">The file extension for a module manifest file is `.PSD1`.</span></span> <span data-ttu-id="63f73-159">Niet alle bestanden met een `.PSD1` extensie zijn module manifesten.</span><span class="sxs-lookup"><span data-stu-id="63f73-159">Not all files with a `.PSD1` extension are module manifests.</span></span> <span data-ttu-id="63f73-160">Ze kunnen ook worden gebruikt voor zaken zoals het opslaan van het onderdeel van een DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="63f73-160">They can also be used for things such as storing the environmental portion of a DSC configuration.</span></span> <span data-ttu-id="63f73-161">`New-ModuleManifest`wordt gebruikt om een module manifest te maken.</span><span class="sxs-lookup"><span data-stu-id="63f73-161">`New-ModuleManifest` is used to create a module manifest.</span></span> <span data-ttu-id="63f73-162">Het **pad** is de enige vereiste waarde.</span><span class="sxs-lookup"><span data-stu-id="63f73-162">**Path** is the only value that's required.</span></span> <span data-ttu-id="63f73-163">De module werkt echter niet als **RootModule** niet is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="63f73-163">However, the module won't work if **RootModule** isn't specified.</span></span> <span data-ttu-id="63f73-164">Het is een goed idee om de **Auteur** en **Beschrijving** op te geven voor het geval u besluit uw module te uploaden naar een NuGet-opslag plaats met PowerShellGet, omdat deze waarden in dat scenario zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="63f73-164">It's a good idea to specify **Author** and **Description** in case you decide to upload your module to a NuGet repository with PowerShellGet since those values are required in that scenario.</span></span>

<span data-ttu-id="63f73-165">De versie van een module zonder manifest is 0,0.</span><span class="sxs-lookup"><span data-stu-id="63f73-165">The version of a module without a manifest is 0.0.</span></span> <span data-ttu-id="63f73-166">Dit is een Dead-Giveaway dat de module geen manifest heeft.</span><span class="sxs-lookup"><span data-stu-id="63f73-166">This is a dead giveaway that the module doesn't have a manifest.</span></span>

```powershell
Get-Module -Name MyScriptModule
```

```Output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Script     0.0        myscriptmodule                      {Get-MrComputerName, Get-MrP...
```

<span data-ttu-id="63f73-167">Het module manifest kan worden gemaakt met alle aanbevolen informatie.</span><span class="sxs-lookup"><span data-stu-id="63f73-167">The module manifest can be created with all of the recommended information.</span></span>

```powershell
New-ModuleManifest -Path $env:ProgramFiles\WindowsPowerShell\Modules\MyScriptModule\MyScriptModule.psd1 -RootModule MyScriptModule -Author 'Mike F Robbins' -Description 'MyScriptModule' -CompanyName 'mikefrobbins.com'
```

<span data-ttu-id="63f73-168">Als een van deze gegevens wordt gemist tijdens het maken van de eerste keer dat het module manifest wordt gemaakt, kan het worden toegevoegd of later worden bijgewerkt met `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="63f73-168">If any of this information is missed during the initial creation of the module manifest, it can be added or updated later using `Update-ModuleManifest`.</span></span> <span data-ttu-id="63f73-169">Maak het manifest niet opnieuw met behulp `New-ModuleManifest` van zodra het al is gemaakt, omdat de GUID verandert.</span><span class="sxs-lookup"><span data-stu-id="63f73-169">Don't recreate the manifest using `New-ModuleManifest` once it's already created because the GUID will change.</span></span>

## <a name="defining-public-and-private-functions"></a><span data-ttu-id="63f73-170">Open bare en persoonlijke functies definiëren</span><span class="sxs-lookup"><span data-stu-id="63f73-170">Defining Public and Private Functions</span></span>

<span data-ttu-id="63f73-171">Mogelijk hebt u hulp functies die u mogelijk persoonlijk wilt maken en alleen toegankelijk zijn voor andere functies in de module.</span><span class="sxs-lookup"><span data-stu-id="63f73-171">You may have helper functions that you may want to be private and only accessible by other functions within the module.</span></span> <span data-ttu-id="63f73-172">Ze zijn niet bedoeld om toegankelijk te zijn voor gebruikers van uw module.</span><span class="sxs-lookup"><span data-stu-id="63f73-172">They are not intended to be accessible to users of your module.</span></span> <span data-ttu-id="63f73-173">Er zijn een aantal verschillende manieren om dit te bereiken.</span><span class="sxs-lookup"><span data-stu-id="63f73-173">There are a couple of different ways to accomplish this.</span></span>

<span data-ttu-id="63f73-174">Als u niet de aanbevolen procedures volgt en alleen een bestand hebt `.PSM1` , kunt u de cmdlet alleen gebruiken `Export-ModuleMember` .</span><span class="sxs-lookup"><span data-stu-id="63f73-174">If you're not following the best practices and only have a `.PSM1` file, then your only option is to use the `Export-ModuleMember` cmdlet.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable
}

function Get-MrComputerName {
    $env:COMPUTERNAME
}

Export-ModuleMember -Function Get-MrPSVersion
```

<span data-ttu-id="63f73-175">In het vorige voor beeld is alleen de `Get-MrPSVersion` functie beschikbaar voor de gebruikers van uw module, maar de `Get-MrComputerName` functie is beschikbaar voor andere functies in de module zelf.</span><span class="sxs-lookup"><span data-stu-id="63f73-175">In the previous example, only the `Get-MrPSVersion` function is available to the users of your module, but the `Get-MrComputerName` function is available to other functions within the module itself.</span></span>

```powershell
Get-Command -Module MyScriptModule

CommandType     Name                        Version    Source
-----------     ----                        -------    ------
Function        Get-MrPSVersion             1.0        MyScript...
```

<span data-ttu-id="63f73-176">Als u een module manifest hebt toegevoegd aan uw module (en dit moet u wel doen), raden we u aan om de afzonderlijke functies op te geven die u wilt exporteren in de sectie **FunctionsToExport** van het module manifest.</span><span class="sxs-lookup"><span data-stu-id="63f73-176">If you've added a module manifest to your module (and you should), then I recommend specifying the individual functions you want to export in the **FunctionsToExport** section of the module manifest.</span></span>

```powershell
FunctionsToExport = 'Get-MrPSVersion'
```

<span data-ttu-id="63f73-177">Het is niet nodig om zowel `Export-ModuleMember` in het `.PSM1` bestand als in het gedeelte **FunctionsToExport** van het module manifest te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="63f73-177">It's not necessary to use both `Export-ModuleMember` in the `.PSM1` file and the **FunctionsToExport** section of the module manifest.</span></span> <span data-ttu-id="63f73-178">De ene of de andere is voldoende.</span><span class="sxs-lookup"><span data-stu-id="63f73-178">One or the other is sufficient.</span></span>

## <a name="summary"></a><span data-ttu-id="63f73-179">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="63f73-179">Summary</span></span>

<span data-ttu-id="63f73-180">In dit hoofd stuk hebt u geleerd hoe u uw functies kunt omzetten in een script module in Power shell.</span><span class="sxs-lookup"><span data-stu-id="63f73-180">In this chapter you've learned how to turn your functions into a script module in PowerShell.</span></span> <span data-ttu-id="63f73-181">Daarnaast hebt u een aantal aanbevolen procedures voor het maken van script modules, zoals het maken van een module manifest voor uw script module, gelean.</span><span class="sxs-lookup"><span data-stu-id="63f73-181">You've also leaned some of the best practices for creating script modules such as creating a module manifest for your script module.</span></span>

## <a name="review"></a><span data-ttu-id="63f73-182">Beoordelen</span><span class="sxs-lookup"><span data-stu-id="63f73-182">Review</span></span>

1. <span data-ttu-id="63f73-183">Hoe maak ik een script module in Power shell?</span><span class="sxs-lookup"><span data-stu-id="63f73-183">How do you create a script module in PowerShell?</span></span>
1. <span data-ttu-id="63f73-184">Waarom is het belang rijk dat uw functies een goedgekeurde term gebruiken?</span><span class="sxs-lookup"><span data-stu-id="63f73-184">Why is it important for your functions to use an approved verb?</span></span>
1. <span data-ttu-id="63f73-185">Hoe maak ik een module manifest in Power shell?</span><span class="sxs-lookup"><span data-stu-id="63f73-185">How do you create a module manifest in PowerShell?</span></span>
1. <span data-ttu-id="63f73-186">Wat zijn de twee opties voor het exporteren van alleen bepaalde functies uit uw module?</span><span class="sxs-lookup"><span data-stu-id="63f73-186">What are the two options for exporting only certain functions from your module?</span></span>
1. <span data-ttu-id="63f73-187">Wat is er nodig om uw modules automatisch te laden wanneer een opdracht wordt aangeroepen?</span><span class="sxs-lookup"><span data-stu-id="63f73-187">What is required for your modules to load automatically when a command is called?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="63f73-188">Aanbevolen Lees bewerkingen</span><span class="sxs-lookup"><span data-stu-id="63f73-188">Recommended Reading</span></span>

- <span data-ttu-id="63f73-189">[Power shell-script modules en module manifesten maken][]</span><span class="sxs-lookup"><span data-stu-id="63f73-189">[How to Create PowerShell Script Modules and Module Manifests][]</span></span>
- <span data-ttu-id="63f73-190">[about_Modules][]</span><span class="sxs-lookup"><span data-stu-id="63f73-190">[about_Modules][]</span></span>
- <span data-ttu-id="63f73-191">[New-ModuleManifest][]</span><span class="sxs-lookup"><span data-stu-id="63f73-191">[New-ModuleManifest][]</span></span>
- <span data-ttu-id="63f73-192">[Exporteren-ModuleMember][]</span><span class="sxs-lookup"><span data-stu-id="63f73-192">[Export-ModuleMember][]</span></span>

<!-- link references -->
[Power shell-script modules en module manifesten maken]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[How to Create PowerShell Script Modules and Module Manifests]: https://mikefrobbins.com/2013/07/04/how-to-create-powershell-script-modules-and-module-manifests/
[about_Modules]: /powershell/module/microsoft.powershell.core/about/about_modules
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Exporteren-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
[Export-ModuleMember]: /powershell/module/microsoft.powershell.core/export-modulemember
