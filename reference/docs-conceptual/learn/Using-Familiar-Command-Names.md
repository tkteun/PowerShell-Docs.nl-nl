---
ms.date: 08/27/2018
keywords: PowerShell-cmdlet
title: Bekende opdrachtnamen gebruiken
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c5665f64fd832eb9c807f413a8e879f63db7f8c6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404623"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="20b20-103">Bekende opdrachtnamen gebruiken</span><span class="sxs-lookup"><span data-stu-id="20b20-103">Using familiar command names</span></span>

<span data-ttu-id="20b20-104">PowerShell ondersteunt om te verwijzen naar opdrachten met alternatieve namen-aliassen.</span><span class="sxs-lookup"><span data-stu-id="20b20-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="20b20-105">Aliasing kan gebruikers met ervaring in andere schalen met namen van algemene opdrachten die ze al kennen voor vergelijkbare bewerkingen in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20b20-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="20b20-106">Een nieuwe naam koppelt aliasing aan een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="20b20-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="20b20-107">PowerShell heeft bijvoorbeeld een interne functie met de naam `Clear-Host` die het uitvoervenster worden gewist.</span><span class="sxs-lookup"><span data-stu-id="20b20-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="20b20-108">U kunt beide typen de `cls` of `clear` alias achter de opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="20b20-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="20b20-109">PowerShell wordt deze aliassen wordt geïnterpreteerd en wordt uitgevoerd de `Clear-Host` functie.</span><span class="sxs-lookup"><span data-stu-id="20b20-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="20b20-110">Deze functie helpt gebruikers voor meer informatie over PowerShell.</span><span class="sxs-lookup"><span data-stu-id="20b20-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="20b20-111">Eerste, meest **cmd.exe** en Unix-gebruikers hebben een grote statusprovider van opdrachten die gebruikers al bekend met de naam.</span><span class="sxs-lookup"><span data-stu-id="20b20-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="20b20-112">De PowerShell-equivalenten kunnen niet dezelfde resultaten opleveren.</span><span class="sxs-lookup"><span data-stu-id="20b20-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="20b20-113">De resultaten zijn echter sluiten voldoende die gebruikers kunnen werken zonder te weten de naam van de PowerShell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="20b20-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="20b20-114">'Finger geheugen' is een andere belangrijke bron van frustraties wanneer een nieuwe opdrachtshell learning.</span><span class="sxs-lookup"><span data-stu-id="20b20-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="20b20-115">Als u hebt gebruikt **cmd.exe** jaar reflexively Typ bijvoorbeeld de `cls` opdracht voor het wissen van het scherm.</span><span class="sxs-lookup"><span data-stu-id="20b20-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="20b20-116">Zonder de alias voor `Clear-Host`, u een foutbericht ontvangt en weet niet wat u moet doen om te wissen van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="20b20-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="20b20-117">De volgende lijst bevat enkele van de algemene **cmd.exe** en Unix-opdrachten die u in PowerShell gebruiken kunt:</span><span class="sxs-lookup"><span data-stu-id="20b20-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="20b20-118">CAT</span><span class="sxs-lookup"><span data-stu-id="20b20-118">cat</span></span>|<span data-ttu-id="20b20-119">dir</span><span class="sxs-lookup"><span data-stu-id="20b20-119">dir</span></span>|<span data-ttu-id="20b20-120">koppelen</span><span class="sxs-lookup"><span data-stu-id="20b20-120">mount</span></span>|<span data-ttu-id="20b20-121">RM</span><span class="sxs-lookup"><span data-stu-id="20b20-121">rm</span></span>|
|<span data-ttu-id="20b20-122">cd</span><span class="sxs-lookup"><span data-stu-id="20b20-122">cd</span></span>|<span data-ttu-id="20b20-123">echo</span><span class="sxs-lookup"><span data-stu-id="20b20-123">echo</span></span>|<span data-ttu-id="20b20-124">verplaatsen</span><span class="sxs-lookup"><span data-stu-id="20b20-124">move</span></span>|<span data-ttu-id="20b20-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="20b20-125">rmdir</span></span>|
|<span data-ttu-id="20b20-126">chdir</span><span class="sxs-lookup"><span data-stu-id="20b20-126">chdir</span></span>|<span data-ttu-id="20b20-127">Wissen</span><span class="sxs-lookup"><span data-stu-id="20b20-127">erase</span></span>|<span data-ttu-id="20b20-128">popd</span><span class="sxs-lookup"><span data-stu-id="20b20-128">popd</span></span>|<span data-ttu-id="20b20-129">slaapstand</span><span class="sxs-lookup"><span data-stu-id="20b20-129">sleep</span></span>|
|<span data-ttu-id="20b20-130">wissen</span><span class="sxs-lookup"><span data-stu-id="20b20-130">clear</span></span>|<span data-ttu-id="20b20-131">H</span><span class="sxs-lookup"><span data-stu-id="20b20-131">h</span></span>|<span data-ttu-id="20b20-132">PS</span><span class="sxs-lookup"><span data-stu-id="20b20-132">ps</span></span>|<span data-ttu-id="20b20-133">Sorteren</span><span class="sxs-lookup"><span data-stu-id="20b20-133">sort</span></span>|
|<span data-ttu-id="20b20-134">CLS</span><span class="sxs-lookup"><span data-stu-id="20b20-134">cls</span></span>|<span data-ttu-id="20b20-135">Geschiedenis</span><span class="sxs-lookup"><span data-stu-id="20b20-135">history</span></span>|<span data-ttu-id="20b20-136">pushd</span><span class="sxs-lookup"><span data-stu-id="20b20-136">pushd</span></span>|<span data-ttu-id="20b20-137">t</span><span class="sxs-lookup"><span data-stu-id="20b20-137">tee</span></span>|
|<span data-ttu-id="20b20-138">Kopiëren</span><span class="sxs-lookup"><span data-stu-id="20b20-138">copy</span></span>|<span data-ttu-id="20b20-139">KILL-instructie</span><span class="sxs-lookup"><span data-stu-id="20b20-139">kill</span></span>|<span data-ttu-id="20b20-140">pwd</span><span class="sxs-lookup"><span data-stu-id="20b20-140">pwd</span></span>|<span data-ttu-id="20b20-141">Type</span><span class="sxs-lookup"><span data-stu-id="20b20-141">type</span></span>|
|<span data-ttu-id="20b20-142">DEL</span><span class="sxs-lookup"><span data-stu-id="20b20-142">del</span></span>|<span data-ttu-id="20b20-143">LP</span><span class="sxs-lookup"><span data-stu-id="20b20-143">lp</span></span>|<span data-ttu-id="20b20-144">r</span><span class="sxs-lookup"><span data-stu-id="20b20-144">r</span></span>|<span data-ttu-id="20b20-145">schrijven</span><span class="sxs-lookup"><span data-stu-id="20b20-145">write</span></span>|
|<span data-ttu-id="20b20-146">diff</span><span class="sxs-lookup"><span data-stu-id="20b20-146">diff</span></span>|<span data-ttu-id="20b20-147">Ls</span><span class="sxs-lookup"><span data-stu-id="20b20-147">ls</span></span>|<span data-ttu-id="20b20-148">ren</span><span class="sxs-lookup"><span data-stu-id="20b20-148">ren</span></span>||

<span data-ttu-id="20b20-149">De `Get-Alias` cmdlet ziet u de echte naam van de systeemeigen PowerShell-opdracht die is gekoppeld aan een alias.</span><span class="sxs-lookup"><span data-stu-id="20b20-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="20b20-150">Standard aliassen interpreteren</span><span class="sxs-lookup"><span data-stu-id="20b20-150">Interpreting standard aliases</span></span>

<span data-ttu-id="20b20-151">De aliassen we vorige beschreven zijn ontworpen voor de naam van compatibiliteit met andere opdrachtshells.</span><span class="sxs-lookup"><span data-stu-id="20b20-151">The aliases we described previous were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="20b20-152">De meeste aliassen die zijn ingebouwd in PowerShell zijn ontworpen voor kort te houden.</span><span class="sxs-lookup"><span data-stu-id="20b20-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="20b20-153">Kortere namen zijn gemakkelijker te type, maar zijn moeilijk te lezen als u niet wat ze verwijzen weet naar.</span><span class="sxs-lookup"><span data-stu-id="20b20-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="20b20-154">PowerShell-aliassen proberen te manipuleren tussen duidelijkheid en beknopt te houden.</span><span class="sxs-lookup"><span data-stu-id="20b20-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="20b20-155">PowerShell maakt gebruik van een standaardset aliassen voor veelvoorkomende woorden en bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="20b20-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="20b20-156">Voorbeeld van de afkortingen:</span><span class="sxs-lookup"><span data-stu-id="20b20-156">Example abbreviations:</span></span>

| <span data-ttu-id="20b20-157">Zelfstandig naamwoord of term</span><span class="sxs-lookup"><span data-stu-id="20b20-157">Noun or Verb</span></span> | <span data-ttu-id="20b20-158">Afkorting</span><span class="sxs-lookup"><span data-stu-id="20b20-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="20b20-159">Ophalen</span><span class="sxs-lookup"><span data-stu-id="20b20-159">Get</span></span>          | <span data-ttu-id="20b20-160">G</span><span class="sxs-lookup"><span data-stu-id="20b20-160">g</span></span>            |
| <span data-ttu-id="20b20-161">Instellen</span><span class="sxs-lookup"><span data-stu-id="20b20-161">Set</span></span>          | <span data-ttu-id="20b20-162">s</span><span class="sxs-lookup"><span data-stu-id="20b20-162">s</span></span>            |
| <span data-ttu-id="20b20-163">Item</span><span class="sxs-lookup"><span data-stu-id="20b20-163">Item</span></span>         | <span data-ttu-id="20b20-164">Ik</span><span class="sxs-lookup"><span data-stu-id="20b20-164">i</span></span>            |
| <span data-ttu-id="20b20-165">Locatie</span><span class="sxs-lookup"><span data-stu-id="20b20-165">Location</span></span>     | <span data-ttu-id="20b20-166">l</span><span class="sxs-lookup"><span data-stu-id="20b20-166">l</span></span>            |
| <span data-ttu-id="20b20-167">Opdracht</span><span class="sxs-lookup"><span data-stu-id="20b20-167">Command</span></span>      | <span data-ttu-id="20b20-168">cm</span><span class="sxs-lookup"><span data-stu-id="20b20-168">cm</span></span>           |
| <span data-ttu-id="20b20-169">Alias</span><span class="sxs-lookup"><span data-stu-id="20b20-169">Alias</span></span>        | <span data-ttu-id="20b20-170">al</span><span class="sxs-lookup"><span data-stu-id="20b20-170">al</span></span>           |

<span data-ttu-id="20b20-171">Deze aliassen zijn opgebouwd uit overzichtelijke als u weet dat de stenonaam.</span><span class="sxs-lookup"><span data-stu-id="20b20-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="20b20-172">Naam van cmdlet</span><span class="sxs-lookup"><span data-stu-id="20b20-172">Cmdlet name</span></span>    | <span data-ttu-id="20b20-173">Alias</span><span class="sxs-lookup"><span data-stu-id="20b20-173">Alias</span></span> |
|----------------|-------|
| `Get-Item `    | <span data-ttu-id="20b20-174">GI</span><span class="sxs-lookup"><span data-stu-id="20b20-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="20b20-175">SI</span><span class="sxs-lookup"><span data-stu-id="20b20-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="20b20-176">GB</span><span class="sxs-lookup"><span data-stu-id="20b20-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="20b20-177">SL</span><span class="sxs-lookup"><span data-stu-id="20b20-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="20b20-178">GCM</span><span class="sxs-lookup"><span data-stu-id="20b20-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="20b20-179">GAL</span><span class="sxs-lookup"><span data-stu-id="20b20-179">gal</span></span>   |

<span data-ttu-id="20b20-180">Als u bekend met PowerShell aliasing bent, is het gemakkelijk te raden dat de **sal** alias verwijst naar `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="20b20-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="20b20-181">Het maken van nieuwe aliassen</span><span class="sxs-lookup"><span data-stu-id="20b20-181">Creating new aliases</span></span>

<span data-ttu-id="20b20-182">Kunt u uw eigen aliassen met behulp van de `Set-Alias` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20b20-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="20b20-183">Bijvoorbeeld, maken de volgende instructies uit de standaard-cmdlet-aliassen die eerder werd besproken:</span><span class="sxs-lookup"><span data-stu-id="20b20-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="20b20-184">Intern, PowerShell maakt gebruik van vergelijkbare opdrachten tijdens het opstarten, maar deze aliassen zijn niet mag worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="20b20-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="20b20-185">Als u probeert uit te voeren op een van deze opdrachten, krijgt u een foutbericht waarin wordt uitgelegd dat de alias kan niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="20b20-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="20b20-186">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="20b20-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```