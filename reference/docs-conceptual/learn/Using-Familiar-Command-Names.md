---
ms.date: 08/27/2018
keywords: Power shell, cmdlet
title: Bekende opdrachtnamen gebruiken
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030892"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="a6c77-103">Bekende opdrachtnamen gebruiken</span><span class="sxs-lookup"><span data-stu-id="a6c77-103">Using familiar command names</span></span>

<span data-ttu-id="a6c77-104">Power shell ondersteunt aliassen om te verwijzen naar opdrachten op alternatieve namen.</span><span class="sxs-lookup"><span data-stu-id="a6c77-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="a6c77-105">Met aliasing kunnen gebruikers ervaring hebben met andere shells om algemene opdracht namen te gebruiken die ze al kennen voor vergelijk bare bewerkingen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="a6c77-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="a6c77-106">Met aliasing wordt een nieuwe naam gekoppeld aan een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="a6c77-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="a6c77-107">Power Shell heeft bijvoorbeeld een interne functie met de naam `Clear-Host` waarmee het uitvoer venster wordt gewist.</span><span class="sxs-lookup"><span data-stu-id="a6c77-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="a6c77-108">U kunt de `cls` of `clear` alias typen bij een opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="a6c77-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="a6c77-109">Power shell interpreteert deze aliassen en voert de `Clear-Host` functie uit.</span><span class="sxs-lookup"><span data-stu-id="a6c77-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="a6c77-110">Deze functie helpt gebruikers bij het leren van Power shell.</span><span class="sxs-lookup"><span data-stu-id="a6c77-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="a6c77-111">Ten eerste hebben de meeste **cmd. exe** -en UNIX-gebruikers een grote aanbod opdrachten die gebruikers al op naam kennen.</span><span class="sxs-lookup"><span data-stu-id="a6c77-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="a6c77-112">De Power shell-equivalenten kunnen geen identieke resultaten opleveren.</span><span class="sxs-lookup"><span data-stu-id="a6c77-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="a6c77-113">De resultaten zijn echter bijna genoeg dat gebruikers kunnen werken zonder de naam van de Power shell-opdracht te weten.</span><span class="sxs-lookup"><span data-stu-id="a6c77-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="a6c77-114">Finger Memory is een andere belang rijke bron van frustraties bij het leren van een nieuwe opdracht shell.</span><span class="sxs-lookup"><span data-stu-id="a6c77-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="a6c77-115">Als u **cmd. exe** hebt gebruikt voor jaren, kunt u de `cls` opdracht om het scherm te wissen, reflexively typen.</span><span class="sxs-lookup"><span data-stu-id="a6c77-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="a6c77-116">Zonder de alias voor `Clear-Host`ontvangt u een fout bericht en weet u niet wat u kunt doen om de uitvoer te wissen.</span><span class="sxs-lookup"><span data-stu-id="a6c77-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="a6c77-117">De volgende lijst bevat enkele van de algemene **cmd. exe** -en UNIX-opdrachten die u kunt gebruiken in Power shell:</span><span class="sxs-lookup"><span data-stu-id="a6c77-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="a6c77-118">Cat5</span><span class="sxs-lookup"><span data-stu-id="a6c77-118">cat</span></span>|<span data-ttu-id="a6c77-119">dir</span><span class="sxs-lookup"><span data-stu-id="a6c77-119">dir</span></span>|<span data-ttu-id="a6c77-120">zachte</span><span class="sxs-lookup"><span data-stu-id="a6c77-120">mount</span></span>|<span data-ttu-id="a6c77-121">RM</span><span class="sxs-lookup"><span data-stu-id="a6c77-121">rm</span></span>|
|<span data-ttu-id="a6c77-122">cd</span><span class="sxs-lookup"><span data-stu-id="a6c77-122">cd</span></span>|<span data-ttu-id="a6c77-123">echo</span><span class="sxs-lookup"><span data-stu-id="a6c77-123">echo</span></span>|<span data-ttu-id="a6c77-124">verplaatsen</span><span class="sxs-lookup"><span data-stu-id="a6c77-124">move</span></span>|<span data-ttu-id="a6c77-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="a6c77-125">rmdir</span></span>|
|<span data-ttu-id="a6c77-126">ziet</span><span class="sxs-lookup"><span data-stu-id="a6c77-126">chdir</span></span>|<span data-ttu-id="a6c77-127">wissen</span><span class="sxs-lookup"><span data-stu-id="a6c77-127">erase</span></span>|<span data-ttu-id="a6c77-128">popd</span><span class="sxs-lookup"><span data-stu-id="a6c77-128">popd</span></span>|<span data-ttu-id="a6c77-129">dwars</span><span class="sxs-lookup"><span data-stu-id="a6c77-129">sleep</span></span>|
|<span data-ttu-id="a6c77-130">wissen</span><span class="sxs-lookup"><span data-stu-id="a6c77-130">clear</span></span>|<span data-ttu-id="a6c77-131">h</span><span class="sxs-lookup"><span data-stu-id="a6c77-131">h</span></span>|<span data-ttu-id="a6c77-132">ps</span><span class="sxs-lookup"><span data-stu-id="a6c77-132">ps</span></span>|<span data-ttu-id="a6c77-133">sorteren</span><span class="sxs-lookup"><span data-stu-id="a6c77-133">sort</span></span>|
|<span data-ttu-id="a6c77-134">compatibiliteit</span><span class="sxs-lookup"><span data-stu-id="a6c77-134">cls</span></span>|<span data-ttu-id="a6c77-135">Geschiedenis</span><span class="sxs-lookup"><span data-stu-id="a6c77-135">history</span></span>|<span data-ttu-id="a6c77-136">pushd</span><span class="sxs-lookup"><span data-stu-id="a6c77-136">pushd</span></span>|<span data-ttu-id="a6c77-137">Tee</span><span class="sxs-lookup"><span data-stu-id="a6c77-137">tee</span></span>|
|<span data-ttu-id="a6c77-138">Kopieer</span><span class="sxs-lookup"><span data-stu-id="a6c77-138">copy</span></span>|<span data-ttu-id="a6c77-139">verwijderen</span><span class="sxs-lookup"><span data-stu-id="a6c77-139">kill</span></span>|<span data-ttu-id="a6c77-140">pwd</span><span class="sxs-lookup"><span data-stu-id="a6c77-140">pwd</span></span>|<span data-ttu-id="a6c77-141">Type</span><span class="sxs-lookup"><span data-stu-id="a6c77-141">type</span></span>|
|<span data-ttu-id="a6c77-142">drukt</span><span class="sxs-lookup"><span data-stu-id="a6c77-142">del</span></span>|<span data-ttu-id="a6c77-143">snelheid</span><span class="sxs-lookup"><span data-stu-id="a6c77-143">lp</span></span>|<span data-ttu-id="a6c77-144">r</span><span class="sxs-lookup"><span data-stu-id="a6c77-144">r</span></span>|<span data-ttu-id="a6c77-145">schrijven</span><span class="sxs-lookup"><span data-stu-id="a6c77-145">write</span></span>|
|<span data-ttu-id="a6c77-146">verschillende</span><span class="sxs-lookup"><span data-stu-id="a6c77-146">diff</span></span>|<span data-ttu-id="a6c77-147">1</span><span class="sxs-lookup"><span data-stu-id="a6c77-147">ls</span></span>|<span data-ttu-id="a6c77-148">Outlook</span><span class="sxs-lookup"><span data-stu-id="a6c77-148">ren</span></span>||

<span data-ttu-id="a6c77-149">De cmdlet `Get-Alias` toont u de werkelijke naam van de systeem eigen Power shell-opdracht die aan een alias is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="a6c77-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="a6c77-150">Standaard aliassen interpreteren</span><span class="sxs-lookup"><span data-stu-id="a6c77-150">Interpreting standard aliases</span></span>

<span data-ttu-id="a6c77-151">De aliassen die eerder zijn beschreven, zijn ontworpen voor naam compatibiliteit met andere opdracht shells.</span><span class="sxs-lookup"><span data-stu-id="a6c77-151">The aliases we described previously were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="a6c77-152">De meeste aliassen die in Power shell zijn ingebouwd, zijn ontworpen voor de boog.</span><span class="sxs-lookup"><span data-stu-id="a6c77-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="a6c77-153">Kortere namen zijn gemakkelijker te typen, maar zijn moeilijk te lezen als u niet weet waar ze naar verwijzen.</span><span class="sxs-lookup"><span data-stu-id="a6c77-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="a6c77-154">Power shell-aliassen proberen te knoeien tussen duidelijkheid en beknoptheid.</span><span class="sxs-lookup"><span data-stu-id="a6c77-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="a6c77-155">Power shell gebruikt een standaardset aliassen voor veelvoorkomende naam woorden en termen.</span><span class="sxs-lookup"><span data-stu-id="a6c77-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="a6c77-156">Voor beelden van afkortingen:</span><span class="sxs-lookup"><span data-stu-id="a6c77-156">Example abbreviations:</span></span>

| <span data-ttu-id="a6c77-157">Zelfstandig naam woord of werk woord</span><span class="sxs-lookup"><span data-stu-id="a6c77-157">Noun or Verb</span></span> | <span data-ttu-id="a6c77-158">Afkorting</span><span class="sxs-lookup"><span data-stu-id="a6c77-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="a6c77-159">Ophalen</span><span class="sxs-lookup"><span data-stu-id="a6c77-159">Get</span></span>          | <span data-ttu-id="a6c77-160">g</span><span class="sxs-lookup"><span data-stu-id="a6c77-160">g</span></span>            |
| <span data-ttu-id="a6c77-161">Instellen</span><span class="sxs-lookup"><span data-stu-id="a6c77-161">Set</span></span>          | <span data-ttu-id="a6c77-162">s</span><span class="sxs-lookup"><span data-stu-id="a6c77-162">s</span></span>            |
| <span data-ttu-id="a6c77-163">Item</span><span class="sxs-lookup"><span data-stu-id="a6c77-163">Item</span></span>         | <span data-ttu-id="a6c77-164">Ik</span><span class="sxs-lookup"><span data-stu-id="a6c77-164">i</span></span>            |
| <span data-ttu-id="a6c77-165">Locatie</span><span class="sxs-lookup"><span data-stu-id="a6c77-165">Location</span></span>     | <span data-ttu-id="a6c77-166">l</span><span class="sxs-lookup"><span data-stu-id="a6c77-166">l</span></span>            |
| <span data-ttu-id="a6c77-167">Opdracht</span><span class="sxs-lookup"><span data-stu-id="a6c77-167">Command</span></span>      | <span data-ttu-id="a6c77-168">bedraagt</span><span class="sxs-lookup"><span data-stu-id="a6c77-168">cm</span></span>           |
| <span data-ttu-id="a6c77-169">Alias</span><span class="sxs-lookup"><span data-stu-id="a6c77-169">Alias</span></span>        | <span data-ttu-id="a6c77-170">al</span><span class="sxs-lookup"><span data-stu-id="a6c77-170">al</span></span>           |

<span data-ttu-id="a6c77-171">Deze aliassen zijn begrijpelijk wanneer u de korte namen kent.</span><span class="sxs-lookup"><span data-stu-id="a6c77-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="a6c77-172">Naam van cmdlet</span><span class="sxs-lookup"><span data-stu-id="a6c77-172">Cmdlet name</span></span>    | <span data-ttu-id="a6c77-173">Alias</span><span class="sxs-lookup"><span data-stu-id="a6c77-173">Alias</span></span> |
|----------------|-------|
| `Get-Item`     | <span data-ttu-id="a6c77-174">GI</span><span class="sxs-lookup"><span data-stu-id="a6c77-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="a6c77-175">si</span><span class="sxs-lookup"><span data-stu-id="a6c77-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="a6c77-176">boekhoud</span><span class="sxs-lookup"><span data-stu-id="a6c77-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="a6c77-177">lineaire</span><span class="sxs-lookup"><span data-stu-id="a6c77-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="a6c77-178">GCM</span><span class="sxs-lookup"><span data-stu-id="a6c77-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="a6c77-179">Gal</span><span class="sxs-lookup"><span data-stu-id="a6c77-179">gal</span></span>   |

<span data-ttu-id="a6c77-180">Wanneer u bekend bent met het uitvoeren van Power shell-aliasing, kunt u gemakkelijk achterhalen dat de alias **Sal** naar `Set-Alias`verwijst.</span><span class="sxs-lookup"><span data-stu-id="a6c77-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="a6c77-181">Nieuwe aliassen maken</span><span class="sxs-lookup"><span data-stu-id="a6c77-181">Creating new aliases</span></span>

<span data-ttu-id="a6c77-182">U kunt uw eigen aliassen maken met behulp van de cmdlet `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="a6c77-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="a6c77-183">Met de volgende instructies worden bijvoorbeeld de standaard-cmdlet-aliassen gemaakt die eerder zijn besproken:</span><span class="sxs-lookup"><span data-stu-id="a6c77-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="a6c77-184">Intern gebruikt Power shell vergelijk bare opdrachten tijdens het opstarten, maar deze aliassen kunnen niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a6c77-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="a6c77-185">Als u probeert een van deze opdrachten uit te voeren, krijgt u een fout melding waarin wordt uitgelegd dat de alias niet kan worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a6c77-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="a6c77-186">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a6c77-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
