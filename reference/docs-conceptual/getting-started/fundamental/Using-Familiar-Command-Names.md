---
ms.date: 08/27/2018
keywords: PowerShell-cmdlet
title: Bekende opdrachtnamen gebruiken
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: 08402aa5b959711c150fff89aa6747b6b43f8aa8
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134080"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="f61b1-103">Bekende opdrachtnamen gebruiken</span><span class="sxs-lookup"><span data-stu-id="f61b1-103">Using familiar command names</span></span>

<span data-ttu-id="f61b1-104">PowerShell ondersteunt om te verwijzen naar opdrachten met alternatieve namen-aliassen.</span><span class="sxs-lookup"><span data-stu-id="f61b1-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="f61b1-105">Aliasing kan gebruikers met ervaring in andere schalen met namen van algemene opdrachten die ze al kennen voor vergelijkbare bewerkingen in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f61b1-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="f61b1-106">Een nieuwe naam koppelt aliasing aan een andere opdracht.</span><span class="sxs-lookup"><span data-stu-id="f61b1-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="f61b1-107">PowerShell heeft bijvoorbeeld een interne functie met de naam `Clear-Host` die het uitvoervenster worden gewist.</span><span class="sxs-lookup"><span data-stu-id="f61b1-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="f61b1-108">U kunt beide typen de `cls` of `clear` alias achter de opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="f61b1-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="f61b1-109">PowerShell wordt deze aliassen wordt geïnterpreteerd en wordt uitgevoerd de `Clear-Host` functie.</span><span class="sxs-lookup"><span data-stu-id="f61b1-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="f61b1-110">Deze functie helpt gebruikers voor meer informatie over PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f61b1-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="f61b1-111">Eerste, de meeste Cmd.exe- en Unix-gebruikers hebben een grote statusprovider van opdrachten die gebruikers al bekend met de naam.</span><span class="sxs-lookup"><span data-stu-id="f61b1-111">First, most Cmd.exe and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="f61b1-112">De PowerShell-equivalenten kunnen niet dezelfde resultaten opleveren.</span><span class="sxs-lookup"><span data-stu-id="f61b1-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="f61b1-113">De resultaten zijn echter sluiten voldoende die gebruikers kunnen werken zonder te weten de naam van de PowerShell-opdracht.</span><span class="sxs-lookup"><span data-stu-id="f61b1-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="f61b1-114">'Finger geheugen' is een andere belangrijke bron van frustraties wanneer een nieuwe opdrachtshell learning.</span><span class="sxs-lookup"><span data-stu-id="f61b1-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="f61b1-115">Als u Cmd.exe voor jaar hebt gebruikt, mogelijk reflexively typt u de `cls` opdracht voor het wissen van het scherm.</span><span class="sxs-lookup"><span data-stu-id="f61b1-115">If you have used Cmd.exe for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="f61b1-116">Zonder de alias voor `Clear-Host`, u een foutbericht ontvangt en weet niet wat u moet doen om te wissen van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f61b1-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="f61b1-117">De volgende lijst bevat enkele van de algemene Cmd.exe- en Unix-opdrachten die u kunt gebruiken in PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f61b1-117">The following list shows a few of the common Cmd.exe and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="f61b1-118">CAT</span><span class="sxs-lookup"><span data-stu-id="f61b1-118">cat</span></span>|<span data-ttu-id="f61b1-119">dir</span><span class="sxs-lookup"><span data-stu-id="f61b1-119">dir</span></span>|<span data-ttu-id="f61b1-120">koppelen</span><span class="sxs-lookup"><span data-stu-id="f61b1-120">mount</span></span>|<span data-ttu-id="f61b1-121">RM</span><span class="sxs-lookup"><span data-stu-id="f61b1-121">rm</span></span>|
|<span data-ttu-id="f61b1-122">cd</span><span class="sxs-lookup"><span data-stu-id="f61b1-122">cd</span></span>|<span data-ttu-id="f61b1-123">echo</span><span class="sxs-lookup"><span data-stu-id="f61b1-123">echo</span></span>|<span data-ttu-id="f61b1-124">verplaatsen</span><span class="sxs-lookup"><span data-stu-id="f61b1-124">move</span></span>|<span data-ttu-id="f61b1-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="f61b1-125">rmdir</span></span>|
|<span data-ttu-id="f61b1-126">chdir</span><span class="sxs-lookup"><span data-stu-id="f61b1-126">chdir</span></span>|<span data-ttu-id="f61b1-127">Wissen</span><span class="sxs-lookup"><span data-stu-id="f61b1-127">erase</span></span>|<span data-ttu-id="f61b1-128">popd</span><span class="sxs-lookup"><span data-stu-id="f61b1-128">popd</span></span>|<span data-ttu-id="f61b1-129">slaapstand</span><span class="sxs-lookup"><span data-stu-id="f61b1-129">sleep</span></span>|
|<span data-ttu-id="f61b1-130">wissen</span><span class="sxs-lookup"><span data-stu-id="f61b1-130">clear</span></span>|<span data-ttu-id="f61b1-131">H</span><span class="sxs-lookup"><span data-stu-id="f61b1-131">h</span></span>|<span data-ttu-id="f61b1-132">PS</span><span class="sxs-lookup"><span data-stu-id="f61b1-132">ps</span></span>|<span data-ttu-id="f61b1-133">Sorteren</span><span class="sxs-lookup"><span data-stu-id="f61b1-133">sort</span></span>|
|<span data-ttu-id="f61b1-134">CLS</span><span class="sxs-lookup"><span data-stu-id="f61b1-134">cls</span></span>|<span data-ttu-id="f61b1-135">Geschiedenis</span><span class="sxs-lookup"><span data-stu-id="f61b1-135">history</span></span>|<span data-ttu-id="f61b1-136">pushd</span><span class="sxs-lookup"><span data-stu-id="f61b1-136">pushd</span></span>|<span data-ttu-id="f61b1-137">t</span><span class="sxs-lookup"><span data-stu-id="f61b1-137">tee</span></span>|
|<span data-ttu-id="f61b1-138">Kopiëren</span><span class="sxs-lookup"><span data-stu-id="f61b1-138">copy</span></span>|<span data-ttu-id="f61b1-139">KILL-instructie</span><span class="sxs-lookup"><span data-stu-id="f61b1-139">kill</span></span>|<span data-ttu-id="f61b1-140">pwd</span><span class="sxs-lookup"><span data-stu-id="f61b1-140">pwd</span></span>|<span data-ttu-id="f61b1-141">Type</span><span class="sxs-lookup"><span data-stu-id="f61b1-141">type</span></span>|
|<span data-ttu-id="f61b1-142">DEL</span><span class="sxs-lookup"><span data-stu-id="f61b1-142">del</span></span>|<span data-ttu-id="f61b1-143">LP</span><span class="sxs-lookup"><span data-stu-id="f61b1-143">lp</span></span>|<span data-ttu-id="f61b1-144">r</span><span class="sxs-lookup"><span data-stu-id="f61b1-144">r</span></span>|<span data-ttu-id="f61b1-145">schrijven</span><span class="sxs-lookup"><span data-stu-id="f61b1-145">write</span></span>|
|<span data-ttu-id="f61b1-146">diff</span><span class="sxs-lookup"><span data-stu-id="f61b1-146">diff</span></span>|<span data-ttu-id="f61b1-147">Ls</span><span class="sxs-lookup"><span data-stu-id="f61b1-147">ls</span></span>|<span data-ttu-id="f61b1-148">ren</span><span class="sxs-lookup"><span data-stu-id="f61b1-148">ren</span></span>||

<span data-ttu-id="f61b1-149">De `Get-Alias` cmdlet ziet u de echte naam van de systeemeigen PowerShell-opdracht die is gekoppeld aan een alias.</span><span class="sxs-lookup"><span data-stu-id="f61b1-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="f61b1-150">Standard aliassen interpreteren</span><span class="sxs-lookup"><span data-stu-id="f61b1-150">Interpreting standard aliases</span></span>

<span data-ttu-id="f61b1-151">De aliassen we vorige beschreven zijn ontworpen voor de naam van compatibiliteit met andere opdrachtshells.</span><span class="sxs-lookup"><span data-stu-id="f61b1-151">The aliases we described previous were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="f61b1-152">De meeste aliassen die zijn ingebouwd in PowerShell zijn ontworpen voor kort te houden.</span><span class="sxs-lookup"><span data-stu-id="f61b1-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="f61b1-153">Kortere namen zijn gemakkelijker te type, maar zijn moeilijk te lezen als u niet wat ze verwijzen weet naar.</span><span class="sxs-lookup"><span data-stu-id="f61b1-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="f61b1-154">PowerShell-aliassen proberen te manipuleren tussen duidelijkheid en beknopt te houden.</span><span class="sxs-lookup"><span data-stu-id="f61b1-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="f61b1-155">PowerShell maakt gebruik van een standaardset aliassen voor veelvoorkomende woorden en bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="f61b1-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="f61b1-156">Voorbeeld van de afkortingen:</span><span class="sxs-lookup"><span data-stu-id="f61b1-156">Example abbreviations:</span></span>

| <span data-ttu-id="f61b1-157">Zelfstandig naamwoord of term</span><span class="sxs-lookup"><span data-stu-id="f61b1-157">Noun or Verb</span></span> | <span data-ttu-id="f61b1-158">Afkorting</span><span class="sxs-lookup"><span data-stu-id="f61b1-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="f61b1-159">Ophalen</span><span class="sxs-lookup"><span data-stu-id="f61b1-159">Get</span></span>          | <span data-ttu-id="f61b1-160">G</span><span class="sxs-lookup"><span data-stu-id="f61b1-160">g</span></span>            |
| <span data-ttu-id="f61b1-161">Instellen</span><span class="sxs-lookup"><span data-stu-id="f61b1-161">Set</span></span>          | <span data-ttu-id="f61b1-162">s</span><span class="sxs-lookup"><span data-stu-id="f61b1-162">s</span></span>            |
| <span data-ttu-id="f61b1-163">Item</span><span class="sxs-lookup"><span data-stu-id="f61b1-163">Item</span></span>         | <span data-ttu-id="f61b1-164">Ik</span><span class="sxs-lookup"><span data-stu-id="f61b1-164">i</span></span>            |
| <span data-ttu-id="f61b1-165">Locatie</span><span class="sxs-lookup"><span data-stu-id="f61b1-165">Location</span></span>     | <span data-ttu-id="f61b1-166">l</span><span class="sxs-lookup"><span data-stu-id="f61b1-166">l</span></span>            |
| <span data-ttu-id="f61b1-167">Opdracht</span><span class="sxs-lookup"><span data-stu-id="f61b1-167">Command</span></span>      | <span data-ttu-id="f61b1-168">cm</span><span class="sxs-lookup"><span data-stu-id="f61b1-168">cm</span></span>           |
| <span data-ttu-id="f61b1-169">Alias</span><span class="sxs-lookup"><span data-stu-id="f61b1-169">Alias</span></span>        | <span data-ttu-id="f61b1-170">al</span><span class="sxs-lookup"><span data-stu-id="f61b1-170">al</span></span>           |

<span data-ttu-id="f61b1-171">Deze aliassen zijn opgebouwd uit overzichtelijke als u weet dat de stenonaam.</span><span class="sxs-lookup"><span data-stu-id="f61b1-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="f61b1-172">Naam van cmdlet</span><span class="sxs-lookup"><span data-stu-id="f61b1-172">Cmdlet name</span></span>    | <span data-ttu-id="f61b1-173">Alias</span><span class="sxs-lookup"><span data-stu-id="f61b1-173">Alias</span></span> |
|----------------|-------|
| `Get-Item `    | <span data-ttu-id="f61b1-174">GI</span><span class="sxs-lookup"><span data-stu-id="f61b1-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="f61b1-175">SI</span><span class="sxs-lookup"><span data-stu-id="f61b1-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="f61b1-176">GB</span><span class="sxs-lookup"><span data-stu-id="f61b1-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="f61b1-177">SL</span><span class="sxs-lookup"><span data-stu-id="f61b1-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="f61b1-178">GCM</span><span class="sxs-lookup"><span data-stu-id="f61b1-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="f61b1-179">GAL</span><span class="sxs-lookup"><span data-stu-id="f61b1-179">gal</span></span>   |

<span data-ttu-id="f61b1-180">Als u bekend met PowerShell aliasing bent, is het gemakkelijk te raden dat de **sal** alias verwijst naar `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="f61b1-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="f61b1-181">Het maken van nieuwe aliassen</span><span class="sxs-lookup"><span data-stu-id="f61b1-181">Creating new aliases</span></span>

<span data-ttu-id="f61b1-182">Kunt u uw eigen aliassen met behulp van de `Set-Alias` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f61b1-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="f61b1-183">Bijvoorbeeld, maken de volgende instructies uit de standaard-cmdlet-aliassen die eerder werd besproken:</span><span class="sxs-lookup"><span data-stu-id="f61b1-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="f61b1-184">Intern, PowerShell maakt gebruik van vergelijkbare opdrachten tijdens het opstarten, maar deze aliassen zijn niet mag worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f61b1-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="f61b1-185">Als u probeert uit te voeren op een van deze opdrachten, krijgt u een foutbericht waarin wordt uitgelegd dat de alias kan niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f61b1-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="f61b1-186">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f61b1-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```