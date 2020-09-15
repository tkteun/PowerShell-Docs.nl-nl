---
title: Alles wat u wilt weten over ShouldProcess
description: ShouldProcess is een belang rijke functie die vaak wordt weer geven. Met de para meters WhatIf en confirm kunt u eenvoudig toevoegen aan uw functies.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 6bd4dbd5255203f2daf804163aa2a84d992d6697
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469732"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a><span data-ttu-id="ec35e-104">Alles wat u wilt weten over ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="ec35e-104">Everything you wanted to know about ShouldProcess</span></span>

<span data-ttu-id="ec35e-105">Power shell-functies hebben verschillende functies waarmee de manier waarop gebruikers ermee kunnen communiceren, aanzienlijk wordt verbeterd.</span><span class="sxs-lookup"><span data-stu-id="ec35e-105">PowerShell functions have several features that greatly improve the way users interact with them.</span></span>
<span data-ttu-id="ec35e-106">Een belang rijke functie die vaak wordt overzien, is `-WhatIf` en wordt `-Confirm` ondersteund en is gemakkelijk aan uw functies toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-106">One important feature that is often overlooked is `-WhatIf` and `-Confirm` support and it's easy to add to your functions.</span></span> <span data-ttu-id="ec35e-107">In dit artikel wordt uitgelegd hoe u deze functie implementeert.</span><span class="sxs-lookup"><span data-stu-id="ec35e-107">In this article, we dive deep into how to implement this feature.</span></span>

> [!NOTE]
> <span data-ttu-id="ec35e-108">De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="ec35e-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="ec35e-109">Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="ec35e-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="ec35e-110">Raadpleeg zijn blog op [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="ec35e-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

<span data-ttu-id="ec35e-111">Dit is een eenvoudige functie die u in uw functies kunt inschakelen om een veiligheids netwerk te bieden voor de gebruikers die er behoefte aan hebben.</span><span class="sxs-lookup"><span data-stu-id="ec35e-111">This is a simple feature you can enable in your functions to provide a safety net for the users that need it.</span></span> <span data-ttu-id="ec35e-112">Er is niets scarier dan het uitvoeren van een opdracht waarvan u weet dat deze voor de eerste keer gevaarlijk kan zijn.</span><span class="sxs-lookup"><span data-stu-id="ec35e-112">There's nothing scarier than running a command that you know can be dangerous for the first time.</span></span> <span data-ttu-id="ec35e-113">De optie om het uit te voeren met `-WhatIf` kan een groot verschil maken.</span><span class="sxs-lookup"><span data-stu-id="ec35e-113">The option to run it with `-WhatIf` can make a big difference.</span></span>

## <a name="commonparameters"></a><span data-ttu-id="ec35e-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ec35e-114">CommonParameters</span></span>

<span data-ttu-id="ec35e-115">Voordat we kijken hoe u deze [algemene para meters][]implementeert, wil ik snel kijken hoe ze worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ec35e-115">Before we look at implementing these [common parameters][], I want to take a quick look at how they're used.</span></span>

## <a name="using--whatif"></a><span data-ttu-id="ec35e-116">Using-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ec35e-116">Using -WhatIf</span></span>

<span data-ttu-id="ec35e-117">Wanneer een opdracht de `-WhatIf` para meter ondersteunt, kunt u zien wat de opdracht zou hebben gedaan in plaats van wijzigingen aan te brengen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-117">When a command supports the `-WhatIf` parameter, it allows you to see what the command would have done instead of making changes.</span></span> <span data-ttu-id="ec35e-118">het is een goede manier om de impact van een opdracht te testen, met name voordat u een destructieve handeling doet.</span><span class="sxs-lookup"><span data-stu-id="ec35e-118">it's a good way to test out the impact of a command, especially before you do something destructive.</span></span>

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="ec35e-119">Als de opdracht op de juiste wijze `ShouldProcess` wordt geïmplementeerd, worden alle wijzigingen weer gegeven die zijn aangebracht.</span><span class="sxs-lookup"><span data-stu-id="ec35e-119">If the command correctly implements `ShouldProcess`, it should show you all the changes that it would have made.</span></span> <span data-ttu-id="ec35e-120">Hier volgt een voor beeld van het gebruik van een Joker teken om meerdere bestanden te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-120">Here is an example using a wildcard to delete multiple files.</span></span>

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a><span data-ttu-id="ec35e-121">Gebruiken-bevestigen</span><span class="sxs-lookup"><span data-stu-id="ec35e-121">Using -Confirm</span></span>

<span data-ttu-id="ec35e-122">Opdrachten die ondersteunen `-WhatIf` ook ondersteuning `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-122">Commands that support `-WhatIf` also support `-Confirm`.</span></span> <span data-ttu-id="ec35e-123">Dit geeft u de mogelijkheid om een actie te bevestigen voordat u deze uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ec35e-123">This gives you a chance confirm an action before performing it.</span></span>

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="ec35e-124">In dit geval hebt u meerdere opties waarmee u kunt door gaan, een wijziging overs Laan of het script stoppen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-124">In this case, you have multiple options that allow you to continue, skip a change, or stop the script.</span></span> <span data-ttu-id="ec35e-125">De Help-prompt bevat een beschrijving van elk van deze opties.</span><span class="sxs-lookup"><span data-stu-id="ec35e-125">The help prompt describes each of those options like this.</span></span>

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a><span data-ttu-id="ec35e-126">Lokalisatie</span><span class="sxs-lookup"><span data-stu-id="ec35e-126">Localization</span></span>

<span data-ttu-id="ec35e-127">Deze prompt is gelokaliseerd in Power shell, zodat de taal wordt gewijzigd op basis van de taal van uw besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="ec35e-127">This prompt is localized in PowerShell so the language changes based on the language of your operating system.</span></span> <span data-ttu-id="ec35e-128">Dit is nog een ding die Power shell voor u beheert.</span><span class="sxs-lookup"><span data-stu-id="ec35e-128">This is one more thing that PowerShell manages for you.</span></span>

### <a name="switch-parameters"></a><span data-ttu-id="ec35e-129">Switch parameters</span><span class="sxs-lookup"><span data-stu-id="ec35e-129">Switch parameters</span></span>

<span data-ttu-id="ec35e-130">U kunt snel even kijken hoe u een waarde kunt door geven aan een switch parameter.</span><span class="sxs-lookup"><span data-stu-id="ec35e-130">Let's take quick moment to look at ways to pass a value to a switch parameter.</span></span> <span data-ttu-id="ec35e-131">De belangrijkste reden hiervoor is dat u de parameter waarden vaak wilt door geven aan de functies die u aanroept.</span><span class="sxs-lookup"><span data-stu-id="ec35e-131">The main reason I call this out is that you often want to pass parameter values to functions you call.</span></span>

<span data-ttu-id="ec35e-132">De eerste benadering is een specifieke parameter syntaxis die kan worden gebruikt voor alle para meters, maar u kunt deze ook gebruiken voor switch-para meters.</span><span class="sxs-lookup"><span data-stu-id="ec35e-132">The first approach is a specific parameter syntax that can be used for all parameters but you mostly see it used for switch parameters.</span></span> <span data-ttu-id="ec35e-133">U geeft een dubbele punt op om een waarde aan de para meter toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-133">You specify a colon to attach a value to the parameter.</span></span>

```powershell
Remove-Item -Path:* -WhatIf:$true
```

<span data-ttu-id="ec35e-134">U kunt hetzelfde doen met een variabele.</span><span class="sxs-lookup"><span data-stu-id="ec35e-134">You can do the same with a variable.</span></span>

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

<span data-ttu-id="ec35e-135">De tweede aanpak is het gebruik van een hashtabel om de waarde te splat.</span><span class="sxs-lookup"><span data-stu-id="ec35e-135">The second approach is to use a hashtable to splat the value.</span></span>

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

<span data-ttu-id="ec35e-136">Als u nog niet bekend bent met hashtabellen of splatting, hebt u nog een artikel op dat betrekking heeft op [Alles wat u wilde weten over hashtabellen][].</span><span class="sxs-lookup"><span data-stu-id="ec35e-136">If you're new to hashtables or splatting, I have another article on that covers [everything you wanted to know about hashtables][].</span></span>

## <a name="supportsshouldprocess"></a><span data-ttu-id="ec35e-137">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="ec35e-137">SupportsShouldProcess</span></span>

<span data-ttu-id="ec35e-138">De eerste stap om in te scha kelen `-WhatIf` en `-Confirm` te ondersteunen is het opgeven `SupportsShouldProcess` `CmdletBinding` van uw functie.</span><span class="sxs-lookup"><span data-stu-id="ec35e-138">The first step to enable `-WhatIf` and `-Confirm` support is to specify `SupportsShouldProcess` in the `CmdletBinding` of your function.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

<span data-ttu-id="ec35e-139">Als u `SupportsShouldProcess` op deze manier opgeeft, kunnen we onze functie nu aanroepen met `-WhatIf` (of `-Confirm` ).</span><span class="sxs-lookup"><span data-stu-id="ec35e-139">By specifying `SupportsShouldProcess` in this way, we can now call our function with `-WhatIf` (or `-Confirm`).</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="ec35e-140">U ziet dat ik geen para meter met de naam heb gemaakt `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-140">Notice that I did not create a parameter called `-WhatIf`.</span></span> <span data-ttu-id="ec35e-141">Als `SupportsShouldProcess` u deze opgeeft, worden deze automatisch gemaakt voor ons.</span><span class="sxs-lookup"><span data-stu-id="ec35e-141">Specifying `SupportsShouldProcess` automatically creates it for us.</span></span> <span data-ttu-id="ec35e-142">Wanneer we de `-WhatIf` para meter op hebben opgegeven `Test-ShouldProcess` , kunnen we de verwerking ook uitvoeren `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-142">When we specify the `-WhatIf` parameter on `Test-ShouldProcess`, some things we call also perform `-WhatIf` processing.</span></span>

### <a name="trust-but-verify"></a><span data-ttu-id="ec35e-143">Vertrouwen, maar controleren</span><span class="sxs-lookup"><span data-stu-id="ec35e-143">Trust but verify</span></span>

<span data-ttu-id="ec35e-144">Er is een risico dat hier wordt vertrouwd dat alles dat u aanroept waarden overneemt `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-144">There's some danger here trusting that everything you call inherits `-WhatIf` values.</span></span> <span data-ttu-id="ec35e-145">In de rest van de voor beelden gaan we ervan uit dat deze niet werkt en zeer expliciet zijn bij het aanroepen van andere opdrachten.</span><span class="sxs-lookup"><span data-stu-id="ec35e-145">For the rest of the examples, I'm going to assume that it doesn't work and be very explicit when making calls to other commands.</span></span> <span data-ttu-id="ec35e-146">U wordt aangeraden hetzelfde te doen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-146">I recommend that you do the same.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIf
}
```

<span data-ttu-id="ec35e-147">Ik ga de nuances veel later opnieuw bezoeken wanneer u een beter inzicht hebt in alle onderdelen die worden afgespeeld.</span><span class="sxs-lookup"><span data-stu-id="ec35e-147">I will revisit the nuances much later once you have a better understanding of all the pieces in play.</span></span>

## <a name="pscmdletshouldprocess"></a><span data-ttu-id="ec35e-148">$PSCmdlet. ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="ec35e-148">$PSCmdlet.ShouldProcess</span></span>

<span data-ttu-id="ec35e-149">De methode waarmee u kunt implementeren `SupportsShouldProcess` is `$PSCmdlet.ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-149">The method that allows you to implement `SupportsShouldProcess` is `$PSCmdlet.ShouldProcess`.</span></span> <span data-ttu-id="ec35e-150">U wordt gebeld `$PSCmdlet.ShouldProcess(...)` om te zien of u een deel van de logica moet verwerken en Power shell zorgt voor de rest.</span><span class="sxs-lookup"><span data-stu-id="ec35e-150">You call `$PSCmdlet.ShouldProcess(...)` to see if you should process some logic and PowerShell takes care of the rest.</span></span> <span data-ttu-id="ec35e-151">Laten we beginnen met een voor beeld:</span><span class="sxs-lookup"><span data-stu-id="ec35e-151">Let's start with an example:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

<span data-ttu-id="ec35e-152">De aanroep `$PSCmdlet.ShouldProcess($file.name)` van controles voor de `-WhatIf` `-Confirm` para meter (en) wordt vervolgens dienovereenkomstig afgehandeld.</span><span class="sxs-lookup"><span data-stu-id="ec35e-152">The call to `$PSCmdlet.ShouldProcess($file.name)` checks for the `-WhatIf` (and `-Confirm` parameter) then handles it accordingly.</span></span> <span data-ttu-id="ec35e-153">De `-WhatIf` oorzaken `ShouldProcess` van het uitvoeren van een beschrijving van de wijziging en het resultaat `$false` :</span><span class="sxs-lookup"><span data-stu-id="ec35e-153">The `-WhatIf` causes `ShouldProcess` to output a description of the change and return `$false`:</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

<span data-ttu-id="ec35e-154">Als u een aanroep gebruikt `-Confirm` , wordt het script onderbroken en wordt de gebruiker gevraagd om door te gaan.</span><span class="sxs-lookup"><span data-stu-id="ec35e-154">A call using `-Confirm` pauses the script and prompts the user with the option to continue.</span></span> <span data-ttu-id="ec35e-155">Als de gebruiker is geselecteerd, wordt deze geretourneerd `$true` `Y` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-155">It returns `$true` if the user selected `Y`.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="ec35e-156">Een meester functie van `$PSCmdlet.ShouldProcess` is dat deze wordt verdubbeld als uitgebreide uitvoer.</span><span class="sxs-lookup"><span data-stu-id="ec35e-156">An awesome feature of `$PSCmdlet.ShouldProcess` is that it doubles as verbose output.</span></span> <span data-ttu-id="ec35e-157">Dit is vaak afhankelijk van het implementeren van `ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-157">I depend on this often when implementing `ShouldProcess`.</span></span>

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a><span data-ttu-id="ec35e-158">Overloads</span><span class="sxs-lookup"><span data-stu-id="ec35e-158">Overloads</span></span>

<span data-ttu-id="ec35e-159">Er zijn een aantal verschillende overbelastingen voor `$PSCmdlet.ShouldProcess` met verschillende para meters voor het aanpassen van de berichten.</span><span class="sxs-lookup"><span data-stu-id="ec35e-159">There are a few different overloads for `$PSCmdlet.ShouldProcess` with different parameters for customizing the messaging.</span></span> <span data-ttu-id="ec35e-160">In het bovenstaande voor beeld is de eerste versie al gezien.</span><span class="sxs-lookup"><span data-stu-id="ec35e-160">We already saw the first one in the example above.</span></span> <span data-ttu-id="ec35e-161">Laten we dit eens nader bekijken.</span><span class="sxs-lookup"><span data-stu-id="ec35e-161">Let's take a closer look at it.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

<span data-ttu-id="ec35e-162">Dit produceert uitvoer die zowel de naam van de functie als het doel (waarde van de para meter) bevat.</span><span class="sxs-lookup"><span data-stu-id="ec35e-162">This produces output that includes both the function name and the target (value of the parameter).</span></span>

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

<span data-ttu-id="ec35e-163">Het opgeven van een tweede para meter als de bewerking de bewerkings waarde gebruikt in plaats van de functie naam in het bericht.</span><span class="sxs-lookup"><span data-stu-id="ec35e-163">Specifying a second parameter as the operation uses the operation value instead of the function name in the message.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

<span data-ttu-id="ec35e-164">De volgende optie is om drie para meters op te geven voor het volledig aanpassen van het bericht.</span><span class="sxs-lookup"><span data-stu-id="ec35e-164">The next option is to specify three parameters to fully customize the message.</span></span> <span data-ttu-id="ec35e-165">Als er drie para meters worden gebruikt, is de eerste een het hele bericht.</span><span class="sxs-lookup"><span data-stu-id="ec35e-165">When three parameters are used, the first one is the entire message.</span></span> <span data-ttu-id="ec35e-166">De tweede twee para meters worden nog steeds gebruikt in de `-Confirm` bericht uitvoer.</span><span class="sxs-lookup"><span data-stu-id="ec35e-166">The second two parameters are still used in the `-Confirm` message output.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a><span data-ttu-id="ec35e-167">Naslag informatie voor snelle para meters</span><span class="sxs-lookup"><span data-stu-id="ec35e-167">Quick parameter reference</span></span>

<span data-ttu-id="ec35e-168">U hoeft alleen maar te weten welke para meters u moet gebruiken. Hier volgt een kort overzicht van hoe de para meters het bericht in de verschillende `-WhatIf` scenario's wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-168">Just in case you came here only to figure out what parameters you should use, here is a quick reference showing how the parameters change the message in the different `-WhatIf` scenarios.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

<span data-ttu-id="ec35e-169">Ik gebruik een van de twee para meters.</span><span class="sxs-lookup"><span data-stu-id="ec35e-169">I tend to use the one with two parameters.</span></span>

### <a name="shouldprocessreason"></a><span data-ttu-id="ec35e-170">ShouldProcessReason</span><span class="sxs-lookup"><span data-stu-id="ec35e-170">ShouldProcessReason</span></span>

<span data-ttu-id="ec35e-171">We hebben een vierde overbelasting die geavanceerder is dan de andere.</span><span class="sxs-lookup"><span data-stu-id="ec35e-171">We have a fourth overload that's more advanced than the others.</span></span> <span data-ttu-id="ec35e-172">U kunt de reden hiervoor `ShouldProcess` uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="ec35e-172">It allows you to get the reason `ShouldProcess` was executed.</span></span> <span data-ttu-id="ec35e-173">Ik voeg dit hier alleen toe voor de volledige taak omdat we `$WhatIf` `$true` in plaats daarvan alleen kunnen controleren.</span><span class="sxs-lookup"><span data-stu-id="ec35e-173">I'm only adding this here for completeness because we can just check if `$WhatIf` is `$true` instead.</span></span>

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

<span data-ttu-id="ec35e-174">De variabele moet worden door gegeven aan `$reason` de vierde para meter als referentie variabele met `[ref]` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-174">We have to pass the `$reason` variable into the fourth parameter as a reference variable with `[ref]`.</span></span> <span data-ttu-id="ec35e-175">`ShouldProcess` vult `$reason` met de waarde `None` of `WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-175">`ShouldProcess` populates `$reason` with the value `None` or `WhatIf`.</span></span> <span data-ttu-id="ec35e-176">Ik heb dit niet gedaan, maar ik heb geen reden gehad om deze ooit te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ec35e-176">I didn't say this was useful and I have had no reason to ever use it.</span></span>

### <a name="where-to-place-it"></a><span data-ttu-id="ec35e-177">Locatie van de locatie</span><span class="sxs-lookup"><span data-stu-id="ec35e-177">Where to place it</span></span>

<span data-ttu-id="ec35e-178">U gebruikt `ShouldProcess` om uw scripts veiliger te maken.</span><span class="sxs-lookup"><span data-stu-id="ec35e-178">You use `ShouldProcess` to make your scripts safer.</span></span> <span data-ttu-id="ec35e-179">Daarom gebruikt u dit wanneer uw scripts wijzigingen aanbrengen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-179">So you use it when your scripts are making changes.</span></span> <span data-ttu-id="ec35e-180">Ik wil de oproep zo `$PSCmdlet.ShouldProcess` dicht mogelijk bij de wijziging plaatsen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-180">I like to place the `$PSCmdlet.ShouldProcess` call as close to the change as possible.</span></span>

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

<span data-ttu-id="ec35e-181">Als ik een verzameling items Verwerk, roep ik deze voor elk item aan.</span><span class="sxs-lookup"><span data-stu-id="ec35e-181">If I'm processing a collection of items, I call it for each item.</span></span> <span data-ttu-id="ec35e-182">De aanroep wordt dus in de foreach-lus geplaatst.</span><span class="sxs-lookup"><span data-stu-id="ec35e-182">So the call gets placed inside the foreach loop.</span></span>

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

<span data-ttu-id="ec35e-183">De reden waarom ik `ShouldProcess` nauw keurig rond de wijziging bevindt, is dat ik zo veel mogelijk code wil uitvoeren wanneer deze `-WhatIf` is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ec35e-183">The reason why I place `ShouldProcess` tightly around the change, is that I want as much code to execute as possible when `-WhatIf` is specified.</span></span> <span data-ttu-id="ec35e-184">Ik wil dat de installatie en validatie zo mogelijk worden uitgevoerd, zodat de gebruiker deze fouten kan zien.</span><span class="sxs-lookup"><span data-stu-id="ec35e-184">I want the setup and validation to run if possible so the user gets to see those errors.</span></span>

<span data-ttu-id="ec35e-185">Ik wil dit ook gebruiken in mijn ziekte tests die mijn projecten valideren.</span><span class="sxs-lookup"><span data-stu-id="ec35e-185">I also like to use this in my Pester tests that validate my projects.</span></span> <span data-ttu-id="ec35e-186">Als er sprake is van een stukje logica dat moeilijk in de ziekte kan worden gesimuleerd, kunt u deze regel matig inpakken `ShouldProcess` en aanroepen `-WhatIf` in mijn tests.</span><span class="sxs-lookup"><span data-stu-id="ec35e-186">If I have a piece of logic that is hard to mock in pester, I can often wrap it in `ShouldProcess` and call it with `-WhatIf` in my tests.</span></span> <span data-ttu-id="ec35e-187">Het is beter om een deel van uw code te testen dan geen van deze.</span><span class="sxs-lookup"><span data-stu-id="ec35e-187">It's better to test some of your code than none of it.</span></span>

### <a name="whatifpreference"></a><span data-ttu-id="ec35e-188">$WhatIfPreference</span><span class="sxs-lookup"><span data-stu-id="ec35e-188">$WhatIfPreference</span></span>

<span data-ttu-id="ec35e-189">De eerste voorkeurs variabele is `$WhatIfPreference` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-189">The first preference variable we have is `$WhatIfPreference`.</span></span> <span data-ttu-id="ec35e-190">Dit is `$false` standaard.</span><span class="sxs-lookup"><span data-stu-id="ec35e-190">This is `$false` by default.</span></span> <span data-ttu-id="ec35e-191">Als u deze instelt op `$true` , wordt de functie uitgevoerd alsof u deze hebt opgegeven `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-191">If you set it to `$true` then your function executes as if you specified `-WhatIf`.</span></span> <span data-ttu-id="ec35e-192">Als u dit instelt in uw sessie, worden alle opdrachten `-WhatIf` uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ec35e-192">If you set this in your session, all commands perform `-WhatIf` execution.</span></span>

<span data-ttu-id="ec35e-193">Wanneer u een functie aanroept met `-WhatIf` , wordt de waarde van `$WhatIfPreference` ingesteld op `$true` binnen het bereik van uw functie.</span><span class="sxs-lookup"><span data-stu-id="ec35e-193">When you call a function with `-WhatIf`, the value of `$WhatIfPreference` gets set to `$true` inside the scope of your function.</span></span>

## <a name="confirmimpact"></a><span data-ttu-id="ec35e-194">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="ec35e-194">ConfirmImpact</span></span>

<span data-ttu-id="ec35e-195">De meeste van de voor beelden zijn voor `-WhatIf` , maar alles werkt ook met `-Confirm` om de gebruiker te vragen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-195">Most of my examples are for `-WhatIf` but everything so far also works with `-Confirm` to prompt the user.</span></span> <span data-ttu-id="ec35e-196">U kunt de `ConfirmImpact` functie instellen op hoog en de gebruiker wordt gevraagd alsof deze is aangeroepen met `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-196">You can set the `ConfirmImpact` of the function to high and it prompts the user as if it was called with `-Confirm`.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="ec35e-197">Met deze aanroep `Test-ShouldProcess` wordt de `-Confirm` actie uitgevoerd wegens de `High` impact.</span><span class="sxs-lookup"><span data-stu-id="ec35e-197">This call to `Test-ShouldProcess` is performing the `-Confirm` action because of the `High` impact.</span></span>

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

<span data-ttu-id="ec35e-198">Het probleem is nu moeilijker te gebruiken in andere scripts zonder dat de gebruiker om toestemming wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="ec35e-198">The obvious issue is that now it's harder to use in other scripts without prompting the user.</span></span> <span data-ttu-id="ec35e-199">In dit geval kunnen we een ' aan ' door geven `$false` `-Confirm` om de prompt te onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="ec35e-199">In this case, we can pass a `$false` to `-Confirm` to suppress the prompt.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

<span data-ttu-id="ec35e-200">Ik wil `-Force` de ondersteuning voor een latere sectie toevoegen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-200">I'll cover how to add `-Force` support in a later section.</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="ec35e-201">$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="ec35e-201">$ConfirmPreference</span></span>

<span data-ttu-id="ec35e-202">`$ConfirmPreference` is een automatische variabele die bepaalt wanneer `ConfirmImpact` u wordt gevraagd om de uitvoering te bevestigen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-202">`$ConfirmPreference` is an automatic variable that controls when `ConfirmImpact` asks you to confirm execution.</span></span> <span data-ttu-id="ec35e-203">Dit zijn de mogelijke waarden voor zowel `$ConfirmPreference` als `ConfirmImpact` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-203">Here are the possible values for both `$ConfirmPreference` and `ConfirmImpact`.</span></span>

- `High`
- `Medium`
- `Low`
- `None`

<span data-ttu-id="ec35e-204">Met deze waarden kunt u verschillende niveaus van invloed op elke functie opgeven.</span><span class="sxs-lookup"><span data-stu-id="ec35e-204">With these values, you can specify different levels of impact for each function.</span></span> <span data-ttu-id="ec35e-205">Als u `$ConfirmPreference` een waarde hebt ingesteld die hoger `ConfirmImpact` is dan, wordt u niet gevraagd om de uitvoering te bevestigen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-205">If you have `$ConfirmPreference` set to a value higher than `ConfirmImpact`, then you aren't prompted to confirm execution.</span></span>

<span data-ttu-id="ec35e-206">`$ConfirmPreference`Is standaard ingesteld op `High` en `ConfirmImpact` `Medium` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-206">By default, `$ConfirmPreference` is set to `High` and `ConfirmImpact` is `Medium`.</span></span> <span data-ttu-id="ec35e-207">Als u wilt dat uw functie de gebruiker automatisch vraagt, stelt u uw `ConfirmImpact` in op `High` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-207">If you want your function to automatically prompt the user, set your `ConfirmImpact` to `High`.</span></span> <span data-ttu-id="ec35e-208">Stel deze optie in op `Medium` als het destructieve en gebruik `Low` als de opdracht altijd veilig moet worden uitgevoerd in de productie omgeving.</span><span class="sxs-lookup"><span data-stu-id="ec35e-208">Otherwise set it to `Medium` if its destructive and use `Low` if the command is always safe run in production.</span></span> <span data-ttu-id="ec35e-209">Als u deze instelt op `none` , wordt u niet gevraagd, zelfs als deze `-Confirm` is opgegeven (maar nog wel ondersteuning biedt voor u `-WhatIf` ).</span><span class="sxs-lookup"><span data-stu-id="ec35e-209">If you set it to `none`, it doesn't prompt even if `-Confirm` was specified (but it still gives you `-WhatIf` support).</span></span>

<span data-ttu-id="ec35e-210">Bij het aanroepen van een functie met `-Confirm` wordt de waarde van `$ConfirmPreference` ingesteld op `Low` binnen het bereik van uw functie.</span><span class="sxs-lookup"><span data-stu-id="ec35e-210">When calling a function with `-Confirm`, the value of `$ConfirmPreference` gets set to `Low` inside the scope of your function.</span></span>

### <a name="suppressing-nested-confirm-prompts"></a><span data-ttu-id="ec35e-211">Geneste bevestigings prompts onderdrukken</span><span class="sxs-lookup"><span data-stu-id="ec35e-211">Suppressing nested confirm prompts</span></span>

<span data-ttu-id="ec35e-212">De `$ConfirmPreference` kan worden opgehaald op basis van functies die u aanroept.</span><span class="sxs-lookup"><span data-stu-id="ec35e-212">The `$ConfirmPreference` can get picked up by functions that you call.</span></span> <span data-ttu-id="ec35e-213">Dit kan scenario's maken waarbij u een bevestigings prompt toevoegt en de functie die u aanroept ook vraagt de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="ec35e-213">This can create scenarios where you add a confirm prompt and the function you call also prompts the user.</span></span>

<span data-ttu-id="ec35e-214">Wat ik vaak wil doen, is `-Confirm:$false` het opgeven van de opdrachten die ik roep wanneer ik de vragen al heb afgehandeld.</span><span class="sxs-lookup"><span data-stu-id="ec35e-214">What I tend to do is specify `-Confirm:$false` on the commands that I call when I have already handled the prompting.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

<span data-ttu-id="ec35e-215">Hiermee gaat u terug naar een eerdere waarschuwing: er zijn nuances die niet worden `-WhatIf` door gegeven aan een functie en wanneer `-Confirm` een functie wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="ec35e-215">This brings us back to an earlier warning: There are nuances as to when `-WhatIf` is not passed to a function and when `-Confirm` passes to a function.</span></span> <span data-ttu-id="ec35e-216">Ik ga nu later terug.</span><span class="sxs-lookup"><span data-stu-id="ec35e-216">I promise I'll get back to this later.</span></span>

## <a name="pscmdletshouldcontinue"></a><span data-ttu-id="ec35e-217">$PSCmdlet. ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="ec35e-217">$PSCmdlet.ShouldContinue</span></span>

<span data-ttu-id="ec35e-218">Als u meer controle nodig hebt dan `ShouldProcess` biedt, kunt u de prompt direct activeren met `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-218">If you need more control than `ShouldProcess` provides, you can trigger the prompt directly with `ShouldContinue`.</span></span> <span data-ttu-id="ec35e-219">`ShouldContinue` negeert `$ConfirmPreference` ,,, `ConfirmImpact` `-Confirm` `$WhatIfPreference` en `-WhatIf` wordt gevraagd elke keer dat deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ec35e-219">`ShouldContinue` ignores `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference`, and `-WhatIf` because it prompts every time it's executed.</span></span>

<span data-ttu-id="ec35e-220">In een kort overzicht kunt u gemakkelijk verwarren `ShouldProcess` en `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-220">At a quick glance, it's easy to confuse `ShouldProcess` and `ShouldContinue`.</span></span> <span data-ttu-id="ec35e-221">Ik wil het vaak niet gebruiken `ShouldProcess` omdat de para meter wordt aangeroepen `SupportsShouldProcess` in de `CmdletBinding` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-221">I tend to remember to use `ShouldProcess` because the parameter is called `SupportsShouldProcess` in the `CmdletBinding`.</span></span>
<span data-ttu-id="ec35e-222">U moet `ShouldProcess` in vrijwel elk scenario gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ec35e-222">You should use `ShouldProcess` in almost every scenario.</span></span> <span data-ttu-id="ec35e-223">Daarom heb ik die methode eerst gedekt.</span><span class="sxs-lookup"><span data-stu-id="ec35e-223">That is why I covered that method first.</span></span>

<span data-ttu-id="ec35e-224">Laten we eens kijken `ShouldContinue` in actie.</span><span class="sxs-lookup"><span data-stu-id="ec35e-224">Let's take a look at `ShouldContinue` in action.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="ec35e-225">Dit biedt ons een eenvoudigere prompt met minder opties.</span><span class="sxs-lookup"><span data-stu-id="ec35e-225">This provides us a simpler prompt with fewer options.</span></span>

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="ec35e-226">Het grootste probleem met `ShouldContinue` is dat de gebruiker het interactief moet uitvoeren omdat de gebruiker altijd om toestemming wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="ec35e-226">The biggest issue with `ShouldContinue` is that it requires the user to run it interactively because it always prompts the user.</span></span> <span data-ttu-id="ec35e-227">U moet altijd hulp middelen bouwen die door andere scripts kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ec35e-227">You should always be building tools that can be used by other scripts.</span></span> <span data-ttu-id="ec35e-228">Hoe u dit doet, is door de implementatie uit te voeren `-Force` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-228">The way you do this is by implementing `-Force`.</span></span> <span data-ttu-id="ec35e-229">Ik ga dit idee later opnieuw.</span><span class="sxs-lookup"><span data-stu-id="ec35e-229">I'll revisit this idea later.</span></span>

### <a name="yes-to-all"></a><span data-ttu-id="ec35e-230">Ja op alles</span><span class="sxs-lookup"><span data-stu-id="ec35e-230">Yes to all</span></span>

<span data-ttu-id="ec35e-231">Dit wordt automatisch afgehandeld, `ShouldProcess` maar we moeten nog wat werk voor doen `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-231">This is automatically handled with `ShouldProcess` but we have to do a little more work for `ShouldContinue`.</span></span> <span data-ttu-id="ec35e-232">Er is een tweede methode overbelasting waar we een paar waarden moeten door lopen door te verwijzen naar de logica te beheren.</span><span class="sxs-lookup"><span data-stu-id="ec35e-232">There's a second method overload where we have to pass in a few values by reference to control the logic.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

<span data-ttu-id="ec35e-233">Ik heb een `foreach` lus en een verzameling toegevoegd om deze in actie weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ec35e-233">I added a `foreach` loop and a collection to show it in action.</span></span> <span data-ttu-id="ec35e-234">Ik heb de `ShouldContinue` aanroep uit de `if` verklaring gehaald, zodat deze eenvoudiger te lezen is.</span><span class="sxs-lookup"><span data-stu-id="ec35e-234">I pulled the `ShouldContinue` call out of the `if` statement to make it easier to read.</span></span> <span data-ttu-id="ec35e-235">Het aanroepen van een methode met vier para meters begint met het verkrijgen van een beetje rommelige, maar ik heb geprobeerd het uiterlijk zo schoon te maken.</span><span class="sxs-lookup"><span data-stu-id="ec35e-235">Calling a method with four parameters starts to get a little ugly, but I tried to make it look as clean as I could.</span></span>

## <a name="implementing--force"></a><span data-ttu-id="ec35e-236">Implementatie-forceren</span><span class="sxs-lookup"><span data-stu-id="ec35e-236">Implementing -Force</span></span>

<span data-ttu-id="ec35e-237">`ShouldProcess` en `ShouldContinue` moet `-Force` op verschillende manieren worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="ec35e-237">`ShouldProcess` and `ShouldContinue` need to implement `-Force` in different ways.</span></span> <span data-ttu-id="ec35e-238">De truc van deze implementaties is dat `ShouldProcess` altijd moet worden uitgevoerd, maar `ShouldContinue` niet moet worden uitgevoerd als `-Force` is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ec35e-238">The trick to these implementations is that `ShouldProcess` should always get executed, but `ShouldContinue` should not get executed if `-Force` is specified.</span></span>

### <a name="shouldprocess--force"></a><span data-ttu-id="ec35e-239">ShouldProcess-forceren</span><span class="sxs-lookup"><span data-stu-id="ec35e-239">ShouldProcess -Force</span></span>

<span data-ttu-id="ec35e-240">Als u uw instelt `ConfirmImpact` op `high` , is het eerste wat uw gebruikers gaan proberen te onderdrukken `-Force` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-240">If you set your `ConfirmImpact` to `high`, the first thing your users are going to try is to suppress it with `-Force`.</span></span> <span data-ttu-id="ec35e-241">Dat is de eerste ding die ik toch kan doen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-241">That's the first thing I do anyway.</span></span>

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

<span data-ttu-id="ec35e-242">Als u de sectie intrekt, moeten deze als volgt `ConfirmImpact` worden opgeroepen:</span><span class="sxs-lookup"><span data-stu-id="ec35e-242">If you recall from the `ConfirmImpact` section, they actually need to call it like this:</span></span>

```powershell
Test-ShouldProcess -Confirm:$false
```

<span data-ttu-id="ec35e-243">Niet iedereen realiseert dat ze dit moeten doen en `-Confirm:$false` niet worden onderdrukt `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-243">Not everyone realizes they need to do that and `-Confirm:$false` doesn't suppress `ShouldContinue`.</span></span>
<span data-ttu-id="ec35e-244">Daarom moeten we `-Force` de Sanity van onze gebruikers implementeren.</span><span class="sxs-lookup"><span data-stu-id="ec35e-244">So we should implement `-Force` for the sanity of our users.</span></span> <span data-ttu-id="ec35e-245">Bekijk hier dit volledige voor beeld:</span><span class="sxs-lookup"><span data-stu-id="ec35e-245">Take a look at this full example here:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force -and -not $Confirm){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="ec35e-246">We voegen onze eigen `-Force` switch toe als een para meter en gebruiken de `$Confirm` automatische para meter die beschikbaar is bij `SupportsShouldProcess` het toevoegen in `CmdletBinding` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-246">We add our own `-Force` switch as a parameter and use the `$Confirm` automatic parameter that is available when adding `SupportsShouldProcess` in the `CmdletBinding`.</span></span>

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

<span data-ttu-id="ec35e-247">Hier kunt u zich richten op de `-Force` logica:</span><span class="sxs-lookup"><span data-stu-id="ec35e-247">Focusing in on the `-Force` logic here:</span></span>

```powershell
if ($Force -and -not $Confirm){
    $ConfirmPreference = 'None'
}
```

<span data-ttu-id="ec35e-248">Als de gebruiker opgeeft `-Force` , willen we de bevestigings prompt onderdrukken, tenzij ze ook opgeven `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-248">If the user specifies `-Force`, we want to suppress the confirm prompt unless they also specify `-Confirm`.</span></span> <span data-ttu-id="ec35e-249">Hiermee kan een gebruiker een wijziging afdwingen, maar wordt de wijziging toch bevestigd.</span><span class="sxs-lookup"><span data-stu-id="ec35e-249">This allows a user to force a change but still confirm the change.</span></span> <span data-ttu-id="ec35e-250">Vervolgens stellen we `$ConfirmPreference` in het lokale bereik op de aanroep naar `ShouldProcess` detecties.</span><span class="sxs-lookup"><span data-stu-id="ec35e-250">Then we set `$ConfirmPreference` in the local scope where our call to `ShouldProcess` discoverers it.</span></span>

```powershell
if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

<span data-ttu-id="ec35e-251">Als iemand beide opgeeft `-Force` en `-WhatIf` , moet de prioriteit worden ingesteld `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-251">If someone specifies both `-Force` and `-WhatIf`, then `-WhatIf` needs to take priority.</span></span> <span data-ttu-id="ec35e-252">Deze aanpak behoudt de `-WhatIf` verwerking omdat deze `ShouldProcess` altijd wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ec35e-252">This approach preserves `-WhatIf` processing because `ShouldProcess` always gets executed.</span></span>

<span data-ttu-id="ec35e-253">Voeg geen controle toe voor de `$Force` waarde in de `if` instructie met de `ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-253">Do not add a check for the `$Force` value inside the `if` statement with the `ShouldProcess`.</span></span> <span data-ttu-id="ec35e-254">Dit is een anti patroon voor dit specifieke scenario, zelfs als dat zo is, in de volgende sectie voor `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-254">That is an anti-pattern for this specific scenario even though that's what I show you in the next section for `ShouldContinue`.</span></span>

### <a name="shouldcontinue--force"></a><span data-ttu-id="ec35e-255">ShouldContinue-forceren</span><span class="sxs-lookup"><span data-stu-id="ec35e-255">ShouldContinue -Force</span></span>

<span data-ttu-id="ec35e-256">Dit is de juiste manier om met te implementeren `-Force` `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-256">This is the correct way to implement `-Force` with `ShouldContinue`.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="ec35e-257">Door de `$Force` aan de linkerkant van de operator te plaatsen, wordt het `-or` eerst geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="ec35e-257">By placing the `$Force` to the left of the `-or` operator, it gets evaluated first.</span></span> <span data-ttu-id="ec35e-258">Op deze manier schrijft u de uitvoering van de-instructie korte circuits `if` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-258">Writing it this way short circuits the execution of the `if` statement.</span></span> <span data-ttu-id="ec35e-259">Als `$force` dat `$true` het geval is, `ShouldContinue` wordt de niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ec35e-259">If `$force` is `$true`, then the `ShouldContinue` is not executed.</span></span>

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

<span data-ttu-id="ec35e-260">U hoeft zich geen zorgen te maken over `-Confirm` of `-WhatIf` in dit scenario omdat deze niet worden ondersteund door `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-260">We don't have to worry about `-Confirm` or `-WhatIf` in this scenario because they're not supported by `ShouldContinue`.</span></span> <span data-ttu-id="ec35e-261">Dit is de reden dat het anders moet worden afgehandeld dan `ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-261">This is why it needs to be handled differently than `ShouldProcess`.</span></span>

## <a name="scope-issues"></a><span data-ttu-id="ec35e-262">Scope problemen</span><span class="sxs-lookup"><span data-stu-id="ec35e-262">Scope issues</span></span>

<span data-ttu-id="ec35e-263">Het gebruik van `-WhatIf` en `-Confirm` moet worden toegepast op alles binnen uw functies en alles wat ze aanroepen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-263">Using `-WhatIf` and `-Confirm` are supposed to apply to everything inside your functions and everything they call.</span></span> <span data-ttu-id="ec35e-264">Dit doet u door `$WhatIfPreference` in te stellen op `$true` of `$ConfirmPreference` `Low` in het lokale bereik van de functie.</span><span class="sxs-lookup"><span data-stu-id="ec35e-264">They do this by setting `$WhatIfPreference` to `$true` or setting `$ConfirmPreference` to `Low` in the local scope of the function.</span></span> <span data-ttu-id="ec35e-265">Wanneer u een andere functie aanroept, aanroepen om `ShouldProcess` deze waarden te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ec35e-265">When you call another function, calls to `ShouldProcess` use those values.</span></span>

<span data-ttu-id="ec35e-266">Dit werkt eigenlijk de meeste tijd goed.</span><span class="sxs-lookup"><span data-stu-id="ec35e-266">This actually works correctly most of the time.</span></span> <span data-ttu-id="ec35e-267">Telkens wanneer u ingebouwde cmdlet of een functie binnen hetzelfde bereik aanroept, werkt deze.</span><span class="sxs-lookup"><span data-stu-id="ec35e-267">Anytime you call built-in cmdlet or a function in your same scope, it works.</span></span> <span data-ttu-id="ec35e-268">Het werkt ook wanneer u een script of een functie in een script module aanroept vanuit de-console.</span><span class="sxs-lookup"><span data-stu-id="ec35e-268">It also works when you call a script or a function in a script module from the console.</span></span>

<span data-ttu-id="ec35e-269">De ene specifieke locatie waar deze niet werkt, is wanneer een script of een script module een functie in een andere script module aanroept.</span><span class="sxs-lookup"><span data-stu-id="ec35e-269">The one specific place where it doesn't work is when a script or a script module calls a function in another script module.</span></span> <span data-ttu-id="ec35e-270">Dit klinkt mogelijk niet zo goed als een groot probleem, maar de meeste modules die u maakt of ophaalt vanuit de PSGallery zijn script modules.</span><span class="sxs-lookup"><span data-stu-id="ec35e-270">This may not sound like a big problem, but most of the modules you create or pull from the PSGallery are script modules.</span></span>

<span data-ttu-id="ec35e-271">Het belangrijkste probleem is dat script modules de waarden voor `$WhatIfPreference` of `$ConfirmPreference` (en verschillende andere) niet overnemen bij het aanroepen van functies in andere script modules.</span><span class="sxs-lookup"><span data-stu-id="ec35e-271">The core issue is that script modules do not inherit the values for `$WhatIfPreference` or `$ConfirmPreference` (and several others) when called from functions in other script modules.</span></span>

<span data-ttu-id="ec35e-272">De beste manier om dit samen te vatten als een algemene regel is dat dit correct werkt voor binaire modules en de IT-afdeling nooit vertrouwt om te werken voor script modules.</span><span class="sxs-lookup"><span data-stu-id="ec35e-272">The best way to summarize this as a general rule is that this works correctly for binary modules and never trust it to work for script modules.</span></span> <span data-ttu-id="ec35e-273">Als u dat niet zeker weet, kunt u het testen of alleen naar behoren werken.</span><span class="sxs-lookup"><span data-stu-id="ec35e-273">If you aren't sure, either test it or just assume it doesn't work correctly.</span></span>

<span data-ttu-id="ec35e-274">Ik vind het persoonlijk dat dit zeer gevaarlijk is omdat er scenario's worden gemaakt waarin u `-WhatIf` ondersteuning toevoegt aan meerdere modules die correct werken, maar niet goed werken wanneer ze elkaar aanroepen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-274">I personally feel this is very dangerous because it creates scenarios where you add `-WhatIf` support to multiple modules that work correctly in isolation, but fail to work correctly when they call each other.</span></span>

<span data-ttu-id="ec35e-275">Er is een GitHub-RFC actief om dit probleem te verhelpen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-275">We do have a GitHub RFC working to get this issue fixed.</span></span> <span data-ttu-id="ec35e-276">Zie [uitvoerings voorkeuren buiten het bereik van de script module door geven][RFC] voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ec35e-276">See [Propagate execution preferences beyond script module scope][RFC] for more details.</span></span>

## <a name="in-closing"></a><span data-ttu-id="ec35e-277">In sluiten</span><span class="sxs-lookup"><span data-stu-id="ec35e-277">In closing</span></span>

<span data-ttu-id="ec35e-278">Ik moet kijken hoe `ShouldProcess` ze elke keer moeten worden gebruikt om het te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ec35e-278">I have to look up how to use `ShouldProcess` every time I need to use it.</span></span> <span data-ttu-id="ec35e-279">Het kan erg lang duren om onderscheid te `ShouldProcess` maken `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="ec35e-279">It took me a long time to distinguish `ShouldProcess` from `ShouldContinue`.</span></span> <span data-ttu-id="ec35e-280">Ik moet bijna altijd zoeken welke para meters u moet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ec35e-280">I almost always need to look up what parameters to use.</span></span> <span data-ttu-id="ec35e-281">Dit is geen probleem als u nog steeds van tijd tot tijd wordt geverwarrend.</span><span class="sxs-lookup"><span data-stu-id="ec35e-281">So don't worry if you still get confused from time to time.</span></span> <span data-ttu-id="ec35e-282">Dit artikel wordt weer gegeven wanneer u het nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="ec35e-282">This article will be here when you need it.</span></span> <span data-ttu-id="ec35e-283">Ik weet dat ik het vaak zelf kan raadplegen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-283">I'm sure I will reference it often myself.</span></span>

<span data-ttu-id="ec35e-284">Als u dit bericht leuk vindt, kunt u met behulp van de onderstaande koppeling uw gedachten delen met mij op Twitter.</span><span class="sxs-lookup"><span data-stu-id="ec35e-284">If you liked this post, please share your thoughts with me on Twitter using the link below.</span></span> <span data-ttu-id="ec35e-285">Ik vind het altijd leuk om te horen van mensen die de waarde van mijn inhoud ophalen.</span><span class="sxs-lookup"><span data-stu-id="ec35e-285">I always like hearing from people that get value from my content.</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[original version]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[algemene para meters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[common parameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[alles wat u wilt weten over hashtabellen]: everything-about-hashtable.md
[everything you wanted to know about hashtables]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
