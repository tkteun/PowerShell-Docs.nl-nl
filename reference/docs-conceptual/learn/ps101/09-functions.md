---
title: Functions
description: Met Power shell-functies kunt u hulpprogram ma's maken die opnieuw kunnen worden gebruikt in scripts.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 9554c0b4d3932b7371201f7b08c8b9d26a567f5e
ms.sourcegitcommit: e85e56d6614cbd30e01965a5cf03fb3f5ca78103
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "94589124"
---
# <a name="chapter-9---functions"></a><span data-ttu-id="3c1d6-103">Hoofd stuk 9-functies</span><span class="sxs-lookup"><span data-stu-id="3c1d6-103">Chapter 9 - Functions</span></span>

<span data-ttu-id="3c1d6-104">Als u de Power shell-One-lines of-scripts schrijft en u deze vaak moet wijzigen voor verschillende scenario's, is het een goed idee om een goede kandidaat in te scha kelen die opnieuw kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-104">If you're writing PowerShell one-liners or scripts and find yourself often having to modify them for different scenarios, there's a good chance that it's a good candidate to be turned into a function that can be reused.</span></span>

<span data-ttu-id="3c1d6-105">Als dat mogelijk is, is het handig om functies te schrijven, omdat deze meer hulp middelen zijn.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-105">Whenever possible, I prefer to write functions because they are more tool oriented.</span></span> <span data-ttu-id="3c1d6-106">Ik kan de functies in een script module plaatsen, die module in de toevoegen `$env:PSModulePath` en de functies aanroepen zonder dat ze fysiek moeten zoeken waar ze worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-106">I can put the functions in a script module, put that module in the `$env:PSModulePath`, and call the functions without needing to physically locate where they're saved.</span></span> <span data-ttu-id="3c1d6-107">Met behulp van de PowerShellGet-module kunt u deze modules eenvoudig delen in een NuGet-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-107">Using the PowerShellGet module, it's easy to share those modules in a NuGet repository.</span></span> <span data-ttu-id="3c1d6-108">PowerShellGet wordt geleverd met Power shell versie 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-108">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="3c1d6-109">Het is beschikbaar als afzonderlijke down load voor Power shell versie 3,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-109">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="3c1d6-110">U hoeft zich niet meer te bemoeilijken.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-110">Don't over complicate things.</span></span> <span data-ttu-id="3c1d6-111">Bewaar het eenvoudig en gebruik de meest directe voorwaartse manier om een taak uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-111">Keep it simple and use the most straight forward way to accomplish a task.</span></span> <span data-ttu-id="3c1d6-112">Vermijd aliassen en positionele para meters in code die u opnieuw gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-112">Avoid aliases and positional parameters in any code that you reuse.</span></span> <span data-ttu-id="3c1d6-113">Maak uw code op voor de Lees baarheid.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-113">Format your code for readability.</span></span> <span data-ttu-id="3c1d6-114">Geen voorlopig hardcoderen we-waarden; gebruik para meters en variabelen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-114">Don't hardcode values; use parameters and variables.</span></span> <span data-ttu-id="3c1d6-115">Schrijf geen overbodige code, zelfs niet als dat niet zo is.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-115">Don't write unnecessary code even if it doesn't hurt anything.</span></span> <span data-ttu-id="3c1d6-116">Het voegt overbodige complexiteit toe.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-116">It adds unnecessary complexity.</span></span> <span data-ttu-id="3c1d6-117">Het is belang rijk om de details van een Power shell-code te schrijven.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-117">Attention to detail goes a long way when writing any PowerShell code.</span></span>

## <a name="naming"></a><span data-ttu-id="3c1d6-118">Naamgeving</span><span class="sxs-lookup"><span data-stu-id="3c1d6-118">Naming</span></span>

<span data-ttu-id="3c1d6-119">Gebruik bij het benoemen van uw functies in Power shell een [Pascal-Case][] naam met een goedgekeurd werk woord en een enkelvoudige zelfstandignaam.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-119">When naming your functions in PowerShell, use a [Pascal case][] name with an approved verb and a singular noun.</span></span> <span data-ttu-id="3c1d6-120">U kunt ook het voor voegsel van het zelfstandig naam woord aanraden.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-120">I also recommend prefixing the noun.</span></span> <span data-ttu-id="3c1d6-121">Bijvoorbeeld: `<ApprovedVerb>-<Prefix><SingularNoun>`.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-121">For example: `<ApprovedVerb>-<Prefix><SingularNoun>`.</span></span>

<span data-ttu-id="3c1d6-122">In Power shell is er een specifieke lijst met goedgekeurde woorden die kunnen worden verkregen door uit te voeren `Get-Verb` .</span><span class="sxs-lookup"><span data-stu-id="3c1d6-122">In PowerShell, there's a specific list of approved verbs that can be obtained by running `Get-Verb`.</span></span>

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

<span data-ttu-id="3c1d6-123">In het vorige voor beeld heb ik de resultaten gesorteerd op de kolom **term** .</span><span class="sxs-lookup"><span data-stu-id="3c1d6-123">In the previous example, I've sorted the results by the **Verb** column.</span></span> <span data-ttu-id="3c1d6-124">In de kolom **groep** vindt u een idee van de manier waarop deze woorden worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-124">The **Group** column gives you an idea of how these verbs are used.</span></span> <span data-ttu-id="3c1d6-125">Het is belang rijk dat u een goedgekeurde werk woord in Power shell kiest wanneer er functies aan een module worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-125">It's important to choose an approved verb in PowerShell when functions are added to a module.</span></span> <span data-ttu-id="3c1d6-126">De module genereert een waarschuwings bericht bij de laad tijd als u een niet-goedgekeurde term kiest.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-126">The module generates a warning message at load time if you choose an unapproved verb.</span></span> <span data-ttu-id="3c1d6-127">Dit waarschuwings bericht zorgt ervoor dat uw functies worden weer gegeven als unprofessional.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-127">That warning message makes your functions look unprofessional.</span></span> <span data-ttu-id="3c1d6-128">Niet-goedgekeurde werk woorden beperken ook de vind baarheid van uw functies.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-128">Unapproved verbs also limit the discoverability of your functions.</span></span>

## <a name="a-simple-function"></a><span data-ttu-id="3c1d6-129">Een eenvoudige functie</span><span class="sxs-lookup"><span data-stu-id="3c1d6-129">A simple function</span></span>

<span data-ttu-id="3c1d6-130">Een functie in Power shell is gedeclareerd met het gereserveerde woord function gevolgd door de functie naam en vervolgens een accolade openen en sluiten.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-130">A function in PowerShell is declared with the function keyword followed by the function name and then an open and closing curly brace.</span></span> <span data-ttu-id="3c1d6-131">De code die de functie uitvoert, bevindt zich in deze accolades.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-131">The code that the function will execute is contained within those curly braces.</span></span>

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="3c1d6-132">De functie die wordt weer gegeven, is een eenvoudig voor beeld van het retour neren van de versie van Power shell.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-132">The function shown is a simple example that returns the version of PowerShell.</span></span>

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="3c1d6-133">Er is een goede kans op een naam conflict met functies met de naam iets zoals `Get-Version` en standaard opdrachten in Power shell of opdrachten die anderen kunnen schrijven.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-133">There's a good chance of name conflict with functions named something like `Get-Version` and default commands in PowerShell or commands that others may write.</span></span> <span data-ttu-id="3c1d6-134">Daarom raden we u aan om het onderdeel van de zelfstandig naam woord van uw functies voor te stellen om conflicten met namen te voor komen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-134">This is why I recommend prefixing the noun portion of your functions to help prevent naming conflicts.</span></span> <span data-ttu-id="3c1d6-135">In het volgende voor beeld gebruiken we het voor voegsel "PS".</span><span class="sxs-lookup"><span data-stu-id="3c1d6-135">In the following example, I'll use the prefix "PS".</span></span>

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="3c1d6-136">Met uitzonde ring van de naam is deze functie gelijk aan die van de voor gaande.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-136">Other than the name, this function is identical to the previous one.</span></span>

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="3c1d6-137">Zelfs bij het voor voegsel van het zelfstandige naam woord, zoals PS, is er nog steeds een goede kans op conflicten.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-137">Even when prefixing the noun with something like PS, there's still a good chance of having a name conflict.</span></span> <span data-ttu-id="3c1d6-138">Ik maak normaal gesp roken voor voegsel mijn eigen naam woorden met mijn initialen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-138">I typically prefix my function nouns with my initials.</span></span> <span data-ttu-id="3c1d6-139">Ontwikkel een Standard-en-stick.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-139">Develop a standard and stick to it.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="3c1d6-140">Deze functie wijkt af van de vorige twee andere dan het gebruik van een meer herkenbaar naam om conflicten met andere Power shell-opdrachten te voor komen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-140">This function is no different than the previous two other than using a more sensible name to try to prevent naming conflicts with other PowerShell commands.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="3c1d6-141">Wanneer u in het geheugen hebt geladen, kunt u functies zien op de **functie** PSDrive.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-141">Once loaded into memory, you can see functions on the **Function** PSDrive.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

<span data-ttu-id="3c1d6-142">Als u deze functies uit uw huidige sessie wilt verwijderen, moet u deze verwijderen uit de **functie** PSDrive of de Power shell sluiten en opnieuw openen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-142">If you want to remove these functions from your current session, you'll have to remove them from the **Function** PSDrive or close and reopen PowerShell.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

<span data-ttu-id="3c1d6-143">Controleer of de functies inderdaad zijn verwijderd.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-143">Verify that the functions were indeed removed.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

<span data-ttu-id="3c1d6-144">Als de functies zijn geladen als onderdeel van een module, kan de module worden verwijderd om ze te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-144">If the functions were loaded as part of a module, the module can be unloaded to remove them.</span></span>

```powershell
Remove-Module -Name <ModuleName>
```

<span data-ttu-id="3c1d6-145">Met de `Remove-Module` cmdlet worden modules uit het geheugen verwijderd uit de huidige Power shell-sessie, worden deze niet verwijderd van uw systeem of van schijf.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-145">The `Remove-Module` cmdlet removes modules from memory in your current PowerShell session, it doesn't remove them from your system or from disk.</span></span>

## <a name="parameters"></a><span data-ttu-id="3c1d6-146">Parameters</span><span class="sxs-lookup"><span data-stu-id="3c1d6-146">Parameters</span></span>

<span data-ttu-id="3c1d6-147">Geen statische waarden toewijzen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-147">Don't statically assign values!</span></span> <span data-ttu-id="3c1d6-148">Gebruik para meters en variabelen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-148">Use parameters and variables.</span></span> <span data-ttu-id="3c1d6-149">Wanneer het gaat om de naam van uw para meters, moet u, indien mogelijk, dezelfde naam gebruiken als de standaard-cmdlets voor uw parameter namen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-149">When it comes to naming your parameters, use the same name as the default cmdlets for your parameter names whenever possible.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3c1d6-150">Waarom heb ik **ComputerName** en niet **computer** , **servername** of **host** gebruikt voor mijn parameter naam?</span><span class="sxs-lookup"><span data-stu-id="3c1d6-150">Why did I use **ComputerName** and not **Computer** , **ServerName** , or **Host** for my parameter name?</span></span> <span data-ttu-id="3c1d6-151">De reden hiervoor is dat ik mijn functie wil gebruiken zoals de standaard-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-151">It's because I wanted my function standardized like the default cmdlets.</span></span>

<span data-ttu-id="3c1d6-152">Ik maak een functie om alle opdrachten op een systeem te doorzoeken en het aantal te retour neren met specifieke parameter namen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-152">I'll create a function to query all of the commands on a system and return the number of them that have specific parameter names.</span></span>

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

<span data-ttu-id="3c1d6-153">Zoals u kunt zien in de onderstaande resultaten, 39 opdrachten met de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="3c1d6-153">As you can see in the results shown below, 39 commands that have a **ComputerName** parameter.</span></span> <span data-ttu-id="3c1d6-154">Er zijn geen cmdlets met para meters zoals **computer** , **servername** , **host** of **machine**.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-154">There aren't any cmdlets that have parameters such as **Computer** , **ServerName** , **Host** , or **Machine**.</span></span>

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

<span data-ttu-id="3c1d6-155">Het is ook raadzaam om hetzelfde hoofdletter gebruik te gebruiken voor uw parameter namen als de standaard-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-155">I also recommend using the same case for your parameter names as the default cmdlets.</span></span> <span data-ttu-id="3c1d6-156">Gebruiken `ComputerName` , niet `computername` .</span><span class="sxs-lookup"><span data-stu-id="3c1d6-156">Use `ComputerName`, not `computername`.</span></span> <span data-ttu-id="3c1d6-157">Dit zorgt ervoor dat uw functies eruitzien zoals de standaard-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-157">This makes your functions look and feel like the default cmdlets.</span></span> <span data-ttu-id="3c1d6-158">Mensen die al bekend zijn met Power shell, kunnen thuis.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-158">People who are already familiar with PowerShell will feel right at home.</span></span>

## <a name="advanced-functions"></a><span data-ttu-id="3c1d6-159">Geavanceerde functies</span><span class="sxs-lookup"><span data-stu-id="3c1d6-159">Advanced Functions</span></span>

<span data-ttu-id="3c1d6-160">Het is heel eenvoudig om een functie in Power shell in te scha kelen in een geavanceerde functie.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-160">Turning a function in PowerShell into an advanced function is really simple.</span></span> <span data-ttu-id="3c1d6-161">Een van de verschillen tussen een functie en een geavanceerde functie is dat geavanceerde functies beschikken over een aantal algemene para meters die automatisch aan de functie worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-161">One of the differences between a function and an advanced function is that advanced functions have a number of common parameters that are added to the function automatically.</span></span> <span data-ttu-id="3c1d6-162">Deze algemene para meters zijn para meters zoals **uitgebreid** en **fout opsporing**.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-162">These common parameters include parameters such as **Verbose** and **Debug**.</span></span>

<span data-ttu-id="3c1d6-163">Ik begin met de `Test-MrParameter` functie die is gebruikt in de vorige sectie.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-163">I'll start out with the `Test-MrParameter` function that was used in the previous section.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3c1d6-164">Wat ik wil dat de `Test-MrParameter` functie geen algemene para meters bevat.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-164">What I want you to notice is that the `Test-MrParameter` function doesn't have any common parameters.</span></span> <span data-ttu-id="3c1d6-165">Er zijn verschillende manieren om de algemene para meters weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-165">There are a couple of different ways to see the common parameters.</span></span> <span data-ttu-id="3c1d6-166">Een voor beeld is de syntaxis met behulp van `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="3c1d6-166">One is by viewing the syntax using `Get-Command`.</span></span>

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

<span data-ttu-id="3c1d6-167">Een andere is om in te zoomen op de para meters met `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="3c1d6-167">Another is to drill down into the parameters with `Get-Command`.</span></span>

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

<span data-ttu-id="3c1d6-168">Toevoegen `CmdletBinding` om de functie in te scha kelen in een geavanceerde functie.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-168">Add `CmdletBinding` to turn the function into an advanced function.</span></span>

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3c1d6-169">`CmdletBinding`De algemene para meters worden automatisch toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-169">Adding `CmdletBinding` adds the common parameters automatically.</span></span> <span data-ttu-id="3c1d6-170">`CmdletBinding` vereist een `param` blok, maar het `param` blok kan leeg zijn.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-170">`CmdletBinding` requires a `param` block, but the `param` block can be empty.</span></span>

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

<span data-ttu-id="3c1d6-171">Inzoomen op de para meters met `Get-Command` toont de werkelijke parameter namen met inbegrip van de gemeen schappelijke para meters.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-171">Drilling down into the parameters with `Get-Command` shows the actual parameter names including the common ones.</span></span>

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a><span data-ttu-id="3c1d6-172">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="3c1d6-172">SupportsShouldProcess</span></span>

<span data-ttu-id="3c1d6-173">`SupportsShouldProcess` Hiermee worden **WhatIf** -en **confirm** -para meters toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-173">`SupportsShouldProcess` adds **WhatIf** and **Confirm** parameters.</span></span> <span data-ttu-id="3c1d6-174">Deze zijn alleen nodig voor opdrachten die wijzigingen aanbrengen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-174">These are only needed for commands that make changes.</span></span>

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3c1d6-175">U ziet dat er nu **WhatIf** en-para meters worden **bevestigd** .</span><span class="sxs-lookup"><span data-stu-id="3c1d6-175">Notice that there are now **WhatIf** and **Confirm** parameters.</span></span>

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="3c1d6-176">Opnieuw kunt u ook gebruiken `Get-Command` om een lijst met de werkelijke parameter namen te retour neren, met inbegrip van de gemeen schappelijke para meters, samen met WhatIf en bevestigen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-176">Once again, you can also use `Get-Command` to return a list of the actual parameter names including the common ones along with WhatIf and Confirm.</span></span>

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a><span data-ttu-id="3c1d6-177">Validatie van de para meter</span><span class="sxs-lookup"><span data-stu-id="3c1d6-177">Parameter Validation</span></span>

<span data-ttu-id="3c1d6-178">Valideer invoer vroegtijdig op.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-178">Validate input early on.</span></span> <span data-ttu-id="3c1d6-179">Waarom staat uw code toe om door te gaan op een pad wanneer het niet mogelijk is om zonder geldige invoer uit te voeren?</span><span class="sxs-lookup"><span data-stu-id="3c1d6-179">Why allow your code to continue on a path when it's not possible to run without valid input?</span></span>

<span data-ttu-id="3c1d6-180">Typ altijd de variabelen die voor de para meters worden gebruikt (Geef een gegevens type op).</span><span class="sxs-lookup"><span data-stu-id="3c1d6-180">Always type the variables that are being used for your parameters (specify a datatype).</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3c1d6-181">In het vorige voor beeld is de **teken reeks** opgegeven als het gegevens type voor de para meter **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="3c1d6-181">In the previous example, I've specified **String** as the datatype for the **ComputerName** parameter.</span></span> <span data-ttu-id="3c1d6-182">Hierdoor kan er slechts één computer naam worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-182">This causes it to allow only a single computer name to be specified.</span></span> <span data-ttu-id="3c1d6-183">Als meer dan een computer naam is opgegeven via een lijst met door komma's gescheiden waarden, wordt er een fout gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-183">If more than one computer name is specified via a comma-separated list, an error is generated.</span></span>

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

<span data-ttu-id="3c1d6-184">Het probleem met de huidige definitie is dat de waarde van de para meter **ComputerName** weglaat, maar een waarde is vereist voor het volt ooien van de functie.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-184">The problem with the current definition is that it's valid to omit the value of the **ComputerName** parameter, but a value is required for the function to complete successfully.</span></span> <span data-ttu-id="3c1d6-185">Hier `Mandatory` komt het parameter kenmerk op de handige manier.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-185">This is where the `Mandatory` parameter attribute comes in handy.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3c1d6-186">De syntaxis die in het vorige voor beeld wordt gebruikt, is Power shell versie 3,0 en hoger compatibel.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-186">The syntax used in the previous example is PowerShell version 3.0 and higher compatible.</span></span>
<span data-ttu-id="3c1d6-187">`[Parameter(Mandatory=$true)]` kan in plaats daarvan worden opgegeven om de functie compatibel te maken met Power shell versie 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-187">`[Parameter(Mandatory=$true)]` could be specified instead to make the function compatible with PowerShell version 2.0 and higher.</span></span> <span data-ttu-id="3c1d6-188">Nu de **computer naam** is vereist, als deze nog niet is opgegeven, wordt er een prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-188">Now that the **ComputerName** is required, if one isn't specified, the function will prompt for one.</span></span>

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

<span data-ttu-id="3c1d6-189">Als u meer dan één waarde wilt toestaan voor de para meter **ComputerName** , gebruikt u het **teken reeks** gegevens type, maar voegt u open en gesloten vier Kante haken toe aan het gegevens type om een matrix van teken reeksen toe te staan.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-189">If you want to allow for more than one value for the **ComputerName** parameter, use the **String** datatype but add open and closed square brackets to the datatype to allow for an array of strings.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3c1d6-190">Misschien wilt u een standaard waarde opgeven voor de para meter **ComputerName** als er geen is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-190">Maybe you want to specify a default value for the **ComputerName** parameter if one isn't specified.</span></span>
<span data-ttu-id="3c1d6-191">Het probleem is dat de standaard waarden niet met verplichte para meters kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-191">The problem is that default values can't be used with mandatory parameters.</span></span> <span data-ttu-id="3c1d6-192">In plaats daarvan moet u het `ValidateNotNullOrEmpty` parameter validatie kenmerk gebruiken met een standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-192">Instead, you'll need to use the `ValidateNotNullOrEmpty` parameter validation attribute with a default value.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="3c1d6-193">Zelfs wanneer u een standaard waarde instelt, kunt u geen statische waarden gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-193">Even when setting a default value, try not to use static values.</span></span> <span data-ttu-id="3c1d6-194">In het vorige voor beeld `$env:COMPUTERNAME` wordt gebruikt als de standaard waarde, die automatisch wordt omgezet in de naam van de lokale computer als er geen waarde wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-194">In the previous example, `$env:COMPUTERNAME` is used as the default value, which is automatically translated into the local computer name if a value is not provided.</span></span>

## <a name="verbose-output"></a><span data-ttu-id="3c1d6-195">Uitgebreide uitvoer</span><span class="sxs-lookup"><span data-stu-id="3c1d6-195">Verbose Output</span></span>

<span data-ttu-id="3c1d6-196">Inline opmerkingen zijn handig, met name als u complexe code schrijft, ze worden nooit door gebruikers gezien, tenzij ze in de code zelf kijken.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-196">While inline comments are useful, especially if you're writing some complex code, they never get seen by users unless they look into the code itself.</span></span>

<span data-ttu-id="3c1d6-197">In het volgende voor beeld wordt in de lus een in line opmerking weer gegeven `foreach` .</span><span class="sxs-lookup"><span data-stu-id="3c1d6-197">The function shown in the following example has an inline comment in the `foreach` loop.</span></span> <span data-ttu-id="3c1d6-198">Hoewel deze specifieke opmerking mogelijk niet moeilijk te vinden is, stel dan dat de functie honderden regels code bevat.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-198">While this particular comment may not be that difficult to locate, imagine if the function included hundreds of lines of code.</span></span>

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

<span data-ttu-id="3c1d6-199">Een betere optie is om `Write-Verbose` in plaats van inline opmerkingen te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-199">A better option is to use `Write-Verbose` instead of inline comments.</span></span>

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

<span data-ttu-id="3c1d6-200">Wanneer de functie wordt aangeroepen zonder de para meter **uitgebreid** , wordt de uitgebreide uitvoer niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-200">When the function is called without the **Verbose** parameter, the verbose output won't be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

<span data-ttu-id="3c1d6-201">Als deze wordt aangeroepen met de para meter **uitgebreid** , wordt de uitgebreide uitvoer weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-201">When it's called with the **Verbose** parameter, the verbose output will be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a><span data-ttu-id="3c1d6-202">Pijplijn invoer</span><span class="sxs-lookup"><span data-stu-id="3c1d6-202">Pipeline Input</span></span>

<span data-ttu-id="3c1d6-203">Wanneer u de invoer van de pijp lijn wilt accepteren, is een extra code ring nodig.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-203">When you want your function to accept pipeline input, some additional coding is necessary.</span></span> <span data-ttu-id="3c1d6-204">Zoals eerder in dit boek wordt vermeld, kunnen opdrachten de invoer van de pijp lijn **op basis van waarde** (per type) of **eigenschaps naam** accepteren.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-204">As mentioned earlier in this book, commands can accept pipeline input **by value** (by type) or **by property name**.</span></span> <span data-ttu-id="3c1d6-205">U kunt uw functies schrijven op dezelfde manier als de systeem eigen opdrachten, zodat ze een of beide typen invoer accepteren.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-205">You can write your functions just like the native commands so that they accept either one or both of these types of input.</span></span>

<span data-ttu-id="3c1d6-206">Als u de pijp lijn invoer **per waarde** wilt accepteren, moet u het `ValueFromPipeline` parameter kenmerk voor die specifieke para meter opgeven.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-206">To accept pipeline input **by value** , specified the `ValueFromPipeline` parameter attribute for that particular parameter.</span></span> <span data-ttu-id="3c1d6-207">Denk eraan dat u alleen pijplijn invoer kunt accepteren **op waarde** uit een van beide gegevens typen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-207">Keep in mind that you can only accept pipeline input **by value** from one of each datatype.</span></span> <span data-ttu-id="3c1d6-208">Als u bijvoorbeeld twee para meters hebt die teken reeks invoer accepteren, kan slechts één van deze de pijplijn invoer **door de waarde** accepteren. Als u deze voor beide teken reeks parameters hebt opgegeven, zou de pijplijn invoer niet weten welk item moet worden gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-208">For example, if you have two parameters that accept string input, only one of those can accept pipeline input **by value** because if you specified it for both of the string parameters, the pipeline input wouldn't know which one to bind to.</span></span> <span data-ttu-id="3c1d6-209">Dit is een andere reden dat ik dit type pijplijn invoer aanroept _per type_ in plaats van **met een waarde**.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-209">This is another reason I call this type of pipeline input _by type_ instead of **by value**.</span></span>

<span data-ttu-id="3c1d6-210">De invoer van de pijp lijn bevindt zich in één item op hetzelfde tijdstip als de manier waarop items in een lus worden verwerkt `foreach` .</span><span class="sxs-lookup"><span data-stu-id="3c1d6-210">Pipeline input comes in one item at a time similar to the way items are handled in a `foreach` loop.</span></span>
<span data-ttu-id="3c1d6-211">Een blok is mini maal `process` vereist voor het verwerken van elk van deze items als u een matrix als invoer accepteert.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-211">At a minimum, a `process` block is required to process each of these items if you're accepting an array as input.</span></span> <span data-ttu-id="3c1d6-212">Als u slechts één waarde als invoer accepteert, `process` is een blok is niet nodig, maar het wordt nog wel aanbevolen om het op consistentie te geven.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-212">If you're only accepting a single value as input, a `process` block isn't necessary, but I still recommend specifying it for consistency.</span></span>

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

<span data-ttu-id="3c1d6-213">De invoer van de pijp lijn wordt geaccepteerd **door de naam** van de eigenschap, behalve dat deze is opgegeven met het `ValueFromPipelineByPropertyName` parameter kenmerk en kan worden opgegeven voor een wille keurig aantal para meters ongeacht het gegevens type.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-213">Accepting pipeline input **by property name** is similar except it's specified with the `ValueFromPipelineByPropertyName` parameter attribute and it can be specified for any number of parameters regardless of datatype.</span></span> <span data-ttu-id="3c1d6-214">De sleutel is de uitvoer van de opdracht die wordt gesluizen in, moet een eigenschaps naam hebben die overeenkomt met de naam van de para meter of een parameter alias van uw functie.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-214">The key is that the output of the command that's being piped in has to have a property name that matches the name of the parameter or a parameter alias of your function.</span></span>

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

<span data-ttu-id="3c1d6-215">`BEGIN` en `END` blokken zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-215">`BEGIN` and `END` blocks are optional.</span></span> <span data-ttu-id="3c1d6-216">`BEGIN` moet vóór het blok worden opgegeven `PROCESS` en wordt gebruikt voor het uitvoeren van de eerste werkzaamheden vóór de items die vanuit de pijp lijn worden ontvangen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-216">`BEGIN` would be specified before the `PROCESS` block and is used to perform any initial work prior to the items being received from the pipeline.</span></span> <span data-ttu-id="3c1d6-217">Dit is belang rijk om te begrijpen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-217">This is important to understand.</span></span> <span data-ttu-id="3c1d6-218">Waarden die worden bepiped in, zijn niet toegankelijk in het `BEGIN` blok.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-218">Values that are piped in are not accessible in the `BEGIN` block.</span></span> <span data-ttu-id="3c1d6-219">Het `END` blok wordt na het blok opgegeven `PROCESS` en wordt gebruikt voor het opschonen van alle items die in de pipes zijn verwerkt.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-219">The `END` block would be specified after the `PROCESS` block and is used for cleanup once all of the items that are piped in have been processed.</span></span>

## <a name="error-handling"></a><span data-ttu-id="3c1d6-220">Foutafhandeling</span><span class="sxs-lookup"><span data-stu-id="3c1d6-220">Error Handling</span></span>

<span data-ttu-id="3c1d6-221">De functie die in het volgende voor beeld wordt weer gegeven, genereert een onverwerkte uitzonde ring wanneer er geen verbinding kan worden gemaakt met een computer.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-221">The function shown in the following example generates an unhandled exception when a computer can't be contacted.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

<span data-ttu-id="3c1d6-222">Er zijn verschillende manieren om fouten in Power shell af te handelen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-222">There are a couple of different ways to handle errors in PowerShell.</span></span> <span data-ttu-id="3c1d6-223">`Try/Catch` is de meer moderne manier om fouten af te handelen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-223">`Try/Catch` is the more modern way to handle errors.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

<span data-ttu-id="3c1d6-224">Hoewel de functie die in het vorige voor beeld wordt weer gegeven, gebruikmaakt van fout afhandeling, wordt er ook een onverwerkte uitzonde ring gegenereerd omdat de opdracht geen afsluit fout genereert.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-224">Although the function shown in the previous example uses error handling, it also generates an unhandled exception because the command doesn't generate a terminating error.</span></span> <span data-ttu-id="3c1d6-225">Dit is ook belang rijk om te begrijpen.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-225">This is also important to understand.</span></span> <span data-ttu-id="3c1d6-226">Alleen afsluit fouten worden geblokkeerd.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-226">Only terminating errors are caught.</span></span> <span data-ttu-id="3c1d6-227">Geef de para meter **Error Action** op met **stoppen** als de waarde om een niet-afsluit fout te maken naar een beëindiging.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-227">Specify the **ErrorAction** parameter with **Stop** as the value to turn a non-terminating error into a terminating one.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

<span data-ttu-id="3c1d6-228">Wijzig de globale `$ErrorActionPreference` variabele alleen als dat absoluut nood zakelijk is.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-228">Don't modify the global `$ErrorActionPreference` variable unless absolutely necessary.</span></span> <span data-ttu-id="3c1d6-229">Als u iets zoals .NET rechtstreeks vanuit uw Power shell-functie gebruikt, kunt u de **Error Action** niet opgeven in de opdracht zelf.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-229">If you're using something like .NET directly from within your PowerShell function, you can't specify the **ErrorAction** on the command itself.</span></span> <span data-ttu-id="3c1d6-230">In dat geval moet u mogelijk de globale `$ErrorActionPreference` variabele wijzigen, maar als u deze wijzigt, wijzigt u deze direct na het uitvoeren van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-230">In that scenario, you might need to change the global `$ErrorActionPreference` variable, but if you do change it, change it back immediately after trying the command.</span></span>

## <a name="comment-based-help"></a><span data-ttu-id="3c1d6-231">Help bij Comment-Based</span><span class="sxs-lookup"><span data-stu-id="3c1d6-231">Comment-Based Help</span></span>

<span data-ttu-id="3c1d6-232">Het wordt beschouwd als een best practice om Help op basis van opmerkingen toe te voegen aan uw functies, zodat de personen met wie u ze deelt, weten hoe ze kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-232">It's considered to be a best practice to add comment based help to your functions so the people you're sharing them with will know how to use them.</span></span>

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

<span data-ttu-id="3c1d6-233">Wanneer u op opmerkingen gebaseerde hulp toevoegt aan uw functies, kan Help worden opgehaald, net als de standaard ingebouwde opdrachten.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-233">When you add comment based help to your functions, help can be retrieved for them just like the default built-in commands.</span></span>

<span data-ttu-id="3c1d6-234">Alle syntaxis voor het schrijven van een functie in Power shell lijkt bijzonder goed te zijn voor iemand die net aan de slag gaat.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-234">All of the syntax for writing a function in PowerShell can seem overwhelming especially for someone who is just getting started.</span></span> <span data-ttu-id="3c1d6-235">Vaak als ik de syntaxis voor iets niet weet, open ik een tweede kopie van de ISE op een afzonderlijke monitor en bekijk ik het ' cmdlet (geavanceerde functie)-volledig ' tijdens het typen van de code voor mijn functie.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-235">Often times if I can't remember the syntax for something, I'll open a second copy of the ISE on a separate monitor and view the "Cmdlet (advanced function) - Complete" snippet while typing in the code for my function.</span></span> <span data-ttu-id="3c1d6-236">Fragmenten kunnen worden geopend in de Power shell-ISE met behulp van de toetscombinatie <kbd>CTRL</kbd> + <kbd>J</kbd> .</span><span class="sxs-lookup"><span data-stu-id="3c1d6-236">Snippets can be accessed in the PowerShell ISE using the <kbd>Ctrl</kbd>+<kbd>J</kbd> key combination.</span></span>

## <a name="summary"></a><span data-ttu-id="3c1d6-237">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="3c1d6-237">Summary</span></span>

<span data-ttu-id="3c1d6-238">In dit hoofd stuk hebt u de basis beginselen geleerd van het schrijven van functies in Power shell om te laten zien hoe u een functie kunt omzetten in een geavanceerde functie en een aantal van de belangrijkste elementen waarmee u rekening moet houden wanneer u Power shell-functies schrijft, zoals validatie van de para meters, uitgebreide uitvoer, invoer van de pijp lijn, fout afhandeling en op opmerkingen gebaseerde Help.</span><span class="sxs-lookup"><span data-stu-id="3c1d6-238">In this chapter you've learned the basics of writing functions in PowerShell to include how to turn a function into an advanced function and some of the more important elements that you should consider when writing PowerShell functions such as parameter validation, verbose output, pipeline input, error handling, and comment based help.</span></span>

## <a name="review"></a><span data-ttu-id="3c1d6-239">Beoordelen</span><span class="sxs-lookup"><span data-stu-id="3c1d6-239">Review</span></span>

1. <span data-ttu-id="3c1d6-240">Hoe krijg ik een lijst met goedgekeurde werk woorden in Power shell?</span><span class="sxs-lookup"><span data-stu-id="3c1d6-240">How do you obtain a list of approved verbs in PowerShell?</span></span>
1. <span data-ttu-id="3c1d6-241">Hoe zet u een Power shell-functie om in een geavanceerde functie?</span><span class="sxs-lookup"><span data-stu-id="3c1d6-241">How do you turn a PowerShell function into an advanced function?</span></span>
1. <span data-ttu-id="3c1d6-242">Wanneer moet **WhatIf** en **Bevestig** de para meters worden toegevoegd aan uw Power shell-functies?</span><span class="sxs-lookup"><span data-stu-id="3c1d6-242">When should **WhatIf** and **Confirm** parameters be added to your PowerShell functions?</span></span>
1. <span data-ttu-id="3c1d6-243">Hoe kan ik een niet-afsluit fout omzetten in een afsluitende?</span><span class="sxs-lookup"><span data-stu-id="3c1d6-243">How do you turn a non-terminating error into a terminating one?</span></span>
1. <span data-ttu-id="3c1d6-244">Waarom moet u op opmerkingen gebaseerde hulp toevoegen aan uw functies?</span><span class="sxs-lookup"><span data-stu-id="3c1d6-244">Why should you add comment based help to your functions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="3c1d6-245">Aanbevolen Lees bewerkingen</span><span class="sxs-lookup"><span data-stu-id="3c1d6-245">Recommended Reading</span></span>

- <span data-ttu-id="3c1d6-246">[about_Functions][]</span><span class="sxs-lookup"><span data-stu-id="3c1d6-246">[about_Functions][]</span></span>
- <span data-ttu-id="3c1d6-247">[about_Functions_Advanced_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="3c1d6-247">[about_Functions_Advanced_Parameters][]</span></span>
- <span data-ttu-id="3c1d6-248">[about_CommonParameters][]</span><span class="sxs-lookup"><span data-stu-id="3c1d6-248">[about_CommonParameters][]</span></span>
- <span data-ttu-id="3c1d6-249">[about_Functions_CmdletBindingAttribute][]</span><span class="sxs-lookup"><span data-stu-id="3c1d6-249">[about_Functions_CmdletBindingAttribute][]</span></span>
- <span data-ttu-id="3c1d6-250">[about_Functions_Advanced][]</span><span class="sxs-lookup"><span data-stu-id="3c1d6-250">[about_Functions_Advanced][]</span></span>
- <span data-ttu-id="3c1d6-251">[about_Try_Catch_Finally][]</span><span class="sxs-lookup"><span data-stu-id="3c1d6-251">[about_Try_Catch_Finally][]</span></span>
- <span data-ttu-id="3c1d6-252">[about_Comment_Based_Help][]</span><span class="sxs-lookup"><span data-stu-id="3c1d6-252">[about_Comment_Based_Help][]</span></span>
- <span data-ttu-id="3c1d6-253">[Video: Power shell-Toolmaking met geavanceerde functies en script modules][]</span><span class="sxs-lookup"><span data-stu-id="3c1d6-253">[Video: PowerShell Toolmaking with Advanced Functions and Script Modules][]</span></span>

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[Video: Power shell-Toolmaking met geavanceerde functies en script modules]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[Video: PowerShell Toolmaking with Advanced Functions and Script Modules]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/
[Pascal-Case]: /dotnet/standard/design-guidelines/capitalization-conventions
[Pascal case]: /dotnet/standard/design-guidelines/capitalization-conventions
