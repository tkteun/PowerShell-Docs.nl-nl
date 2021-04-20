---
title: Alles wat u wilde weten over ShouldProcess
description: ShouldProcess is een belangrijke functie die vaak over het hoofd wordt gezien. Met de parameters WhatIf en Confirm kunt u eenvoudig toevoegen aan uw functies.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 8d0d7dfe15f1ced2343212cddea7ae84a11eed62
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729969"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a><span data-ttu-id="15a02-104">Alles wat u wilde weten over ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="15a02-104">Everything you wanted to know about ShouldProcess</span></span>

<span data-ttu-id="15a02-105">PowerShell-functies hebben verschillende functies die de manier waarop gebruikers erop reageren sterk verbeteren.</span><span class="sxs-lookup"><span data-stu-id="15a02-105">PowerShell functions have several features that greatly improve the way users interact with them.</span></span>
<span data-ttu-id="15a02-106">Een belangrijke functie die vaak over het hoofd wordt gezien, is ondersteuning en het is eenvoudig `-WhatIf` om aan uw functies toe te `-Confirm` voegen.</span><span class="sxs-lookup"><span data-stu-id="15a02-106">One important feature that is often overlooked is `-WhatIf` and `-Confirm` support and it's easy to add to your functions.</span></span> <span data-ttu-id="15a02-107">In dit artikel gaan we dieper in op het implementeren van deze functie.</span><span class="sxs-lookup"><span data-stu-id="15a02-107">In this article, we dive deep into how to implement this feature.</span></span>

> [!NOTE]
> <span data-ttu-id="15a02-108">De [oorspronkelijke versie][] van dit artikel is te vinden in de blog geschreven door [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="15a02-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="15a02-109">Het PowerShell-team bedankt Voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="15a02-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="15a02-110">Bekijk zijn blog op [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="15a02-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

<span data-ttu-id="15a02-111">Dit is een eenvoudige functie die u in uw functies kunt inschakelen om een veiligheidsnet te bieden voor de gebruikers die deze nodig hebben.</span><span class="sxs-lookup"><span data-stu-id="15a02-111">This is a simple feature you can enable in your functions to provide a safety net for the users that need it.</span></span> <span data-ttu-id="15a02-112">Er is niets ergs dan het uitvoeren van een opdracht die voor de eerste keer gevaarlijk kan zijn.</span><span class="sxs-lookup"><span data-stu-id="15a02-112">There's nothing scarier than running a command that you know can be dangerous for the first time.</span></span> <span data-ttu-id="15a02-113">De optie om het uit te voeren `-WhatIf` met kan een groot verschil maken.</span><span class="sxs-lookup"><span data-stu-id="15a02-113">The option to run it with `-WhatIf` can make a big difference.</span></span>

## <a name="commonparameters"></a><span data-ttu-id="15a02-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="15a02-114">CommonParameters</span></span>

<span data-ttu-id="15a02-115">Voordat we kijken naar het implementeren van deze [algemene parameters,][]wil ik even kijken hoe ze worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="15a02-115">Before we look at implementing these [common parameters][], I want to take a quick look at how they're used.</span></span>

## <a name="using--whatif"></a><span data-ttu-id="15a02-116">-WhatIf gebruiken</span><span class="sxs-lookup"><span data-stu-id="15a02-116">Using -WhatIf</span></span>

<span data-ttu-id="15a02-117">Wanneer een opdracht de parameter ondersteunt, kunt u zien wat de opdracht zou hebben gedaan in plaats `-WhatIf` van wijzigingen aan te brengen.</span><span class="sxs-lookup"><span data-stu-id="15a02-117">When a command supports the `-WhatIf` parameter, it allows you to see what the command would have done instead of making changes.</span></span> <span data-ttu-id="15a02-118">Het is een goede manier om de impact van een opdracht te testen, vooral voordat u iets destructiefs doet.</span><span class="sxs-lookup"><span data-stu-id="15a02-118">it's a good way to test out the impact of a command, especially before you do something destructive.</span></span>

```powershell
PS C:\temp> Get-ChildItem
    Directory: C:\temp
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         4/19/2021   8:59 AM              0 importantfile.txt
-a----         4/19/2021   8:58 AM              0 myfile1.txt
-a----         4/19/2021   8:59 AM              0 myfile2.txt

PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="15a02-119">Als de opdracht correct wordt geïmplementeerd, ziet u alle wijzigingen die `ShouldProcess` deze zou hebben aangebracht.</span><span class="sxs-lookup"><span data-stu-id="15a02-119">If the command correctly implements `ShouldProcess`, it should show you all the changes that it would have made.</span></span> <span data-ttu-id="15a02-120">Hier is een voorbeeld van het gebruik van een jokerteken om meerdere bestanden te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="15a02-120">Here is an example using a wildcard to delete multiple files.</span></span>

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a><span data-ttu-id="15a02-121">-Confirm gebruiken</span><span class="sxs-lookup"><span data-stu-id="15a02-121">Using -Confirm</span></span>

<span data-ttu-id="15a02-122">Opdrachten die ondersteuning bieden `-WhatIf` voor ondersteunen ook `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="15a02-122">Commands that support `-WhatIf` also support `-Confirm`.</span></span> <span data-ttu-id="15a02-123">Dit geeft u een kans om een actie te bevestigen voordat u deze gaat uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="15a02-123">This gives you a chance confirm an action before performing it.</span></span>

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="15a02-124">In dit geval hebt u meerdere opties waarmee u kunt doorgaan, een wijziging kunt overslaan of het script kunt stoppen.</span><span class="sxs-lookup"><span data-stu-id="15a02-124">In this case, you have multiple options that allow you to continue, skip a change, or stop the script.</span></span> <span data-ttu-id="15a02-125">In de Help-prompt worden al deze opties als deze beschreven.</span><span class="sxs-lookup"><span data-stu-id="15a02-125">The help prompt describes each of those options like this.</span></span>

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a><span data-ttu-id="15a02-126">Lokalisatie</span><span class="sxs-lookup"><span data-stu-id="15a02-126">Localization</span></span>

<span data-ttu-id="15a02-127">Deze prompt is gelokaliseerd in PowerShell, zodat de taal wordt gewijzigd op basis van de taal van uw besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="15a02-127">This prompt is localized in PowerShell so the language changes based on the language of your operating system.</span></span> <span data-ttu-id="15a02-128">Dit is nog één ding dat PowerShell voor u beheert.</span><span class="sxs-lookup"><span data-stu-id="15a02-128">This is one more thing that PowerShell manages for you.</span></span>

### <a name="switch-parameters"></a><span data-ttu-id="15a02-129">Schakelen tussen parameters</span><span class="sxs-lookup"><span data-stu-id="15a02-129">Switch parameters</span></span>

<span data-ttu-id="15a02-130">Laten we even kijken naar manieren om een waarde door te geven aan een switchparameter.</span><span class="sxs-lookup"><span data-stu-id="15a02-130">Let's take quick moment to look at ways to pass a value to a switch parameter.</span></span> <span data-ttu-id="15a02-131">De belangrijkste reden waarom ik dit aanroep, is dat u vaak parameterwaarden wilt doorgeven aan functies die u aanroept.</span><span class="sxs-lookup"><span data-stu-id="15a02-131">The main reason I call this out is that you often want to pass parameter values to functions you call.</span></span>

<span data-ttu-id="15a02-132">De eerste benadering is een specifieke parametersyntaxis die kan worden gebruikt voor alle parameters, maar u ziet dat deze meestal wordt gebruikt voor switchparameters.</span><span class="sxs-lookup"><span data-stu-id="15a02-132">The first approach is a specific parameter syntax that can be used for all parameters but you mostly see it used for switch parameters.</span></span> <span data-ttu-id="15a02-133">U geeft een dubbele punt op om een waarde aan de parameter te koppelen.</span><span class="sxs-lookup"><span data-stu-id="15a02-133">You specify a colon to attach a value to the parameter.</span></span>

```powershell
Remove-Item -Path:* -WhatIf:$true
```

<span data-ttu-id="15a02-134">U kunt hetzelfde doen met een variabele.</span><span class="sxs-lookup"><span data-stu-id="15a02-134">You can do the same with a variable.</span></span>

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

<span data-ttu-id="15a02-135">De tweede benadering is het gebruik van een hashtabel om de waarde te splatten.</span><span class="sxs-lookup"><span data-stu-id="15a02-135">The second approach is to use a hashtable to splat the value.</span></span>

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

<span data-ttu-id="15a02-136">Als u geen bekend bent met hashtabels of splatting, heb ik nog een artikel over alles wat u wilde [weten over hashtables.][]</span><span class="sxs-lookup"><span data-stu-id="15a02-136">If you're new to hashtables or splatting, I have another article on that covers [everything you wanted to know about hashtables][].</span></span>

## <a name="supportsshouldprocess"></a><span data-ttu-id="15a02-137">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="15a02-137">SupportsShouldProcess</span></span>

<span data-ttu-id="15a02-138">De eerste stap voor het `-WhatIf` inschakelen `-Confirm` en ondersteunen van is het opgeven in de van uw `SupportsShouldProcess` `CmdletBinding` functie.</span><span class="sxs-lookup"><span data-stu-id="15a02-138">The first step to enable `-WhatIf` and `-Confirm` support is to specify `SupportsShouldProcess` in the `CmdletBinding` of your function.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

<span data-ttu-id="15a02-139">Door op deze manier op te geven, kunnen we nu `SupportsShouldProcess` onze functie aanroepen met `-WhatIf` (of `-Confirm` ).</span><span class="sxs-lookup"><span data-stu-id="15a02-139">By specifying `SupportsShouldProcess` in this way, we can now call our function with `-WhatIf` (or `-Confirm`).</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="15a02-140">U ziet dat ik geen parameter met de naam heb `-WhatIf` gemaakt.</span><span class="sxs-lookup"><span data-stu-id="15a02-140">Notice that I did not create a parameter called `-WhatIf`.</span></span> <span data-ttu-id="15a02-141">Als u `SupportsShouldProcess` opgeeft, wordt deze automatisch voor ons gemaakt.</span><span class="sxs-lookup"><span data-stu-id="15a02-141">Specifying `SupportsShouldProcess` automatically creates it for us.</span></span> <span data-ttu-id="15a02-142">Wanneer we de `-WhatIf` parameter voor `Test-ShouldProcess` opgeven, voeren sommige dingen die we aanroepen ook verwerking `-WhatIf` uit.</span><span class="sxs-lookup"><span data-stu-id="15a02-142">When we specify the `-WhatIf` parameter on `Test-ShouldProcess`, some things we call also perform `-WhatIf` processing.</span></span>

### <a name="trust-but-verify"></a><span data-ttu-id="15a02-143">Vertrouwen, maar verifiëren</span><span class="sxs-lookup"><span data-stu-id="15a02-143">Trust but verify</span></span>

<span data-ttu-id="15a02-144">Er bestaat hier een risico wanneer u vertrouwt dat alles wat u aanroept waarden `-WhatIf` overgenomen.</span><span class="sxs-lookup"><span data-stu-id="15a02-144">There's some danger here trusting that everything you call inherits `-WhatIf` values.</span></span> <span data-ttu-id="15a02-145">Voor de rest van de voorbeelden ga ik ervan uit dat het niet werkt en zeer expliciet is bij het aanroepen van andere opdrachten.</span><span class="sxs-lookup"><span data-stu-id="15a02-145">For the rest of the examples, I'm going to assume that it doesn't work and be very explicit when making calls to other commands.</span></span> <span data-ttu-id="15a02-146">U wordt aangeraden hetzelfde te doen.</span><span class="sxs-lookup"><span data-stu-id="15a02-146">I recommend that you do the same.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIfPreference
}
```

<span data-ttu-id="15a02-147">Ik ga veel later terug naar de nuances als u een beter beeld hebt van alle onderdelen.</span><span class="sxs-lookup"><span data-stu-id="15a02-147">I will revisit the nuances much later once you have a better understanding of all the pieces in play.</span></span>

## <a name="pscmdletshouldprocess"></a><span data-ttu-id="15a02-148">$PSCmdlet.ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="15a02-148">$PSCmdlet.ShouldProcess</span></span>

<span data-ttu-id="15a02-149">De methode waarmee u kunt implementeren `SupportsShouldProcess` is `$PSCmdlet.ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="15a02-149">The method that allows you to implement `SupportsShouldProcess` is `$PSCmdlet.ShouldProcess`.</span></span> <span data-ttu-id="15a02-150">U roept `$PSCmdlet.ShouldProcess(...)` aan om te zien of u logica moet verwerken en PowerShell zorgt voor de rest.</span><span class="sxs-lookup"><span data-stu-id="15a02-150">You call `$PSCmdlet.ShouldProcess(...)` to see if you should process some logic and PowerShell takes care of the rest.</span></span> <span data-ttu-id="15a02-151">Laten we beginnen met een voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15a02-151">Let's start with an example:</span></span>

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

<span data-ttu-id="15a02-152">De aanroep `$PSCmdlet.ShouldProcess($file.name)` van controleert op `-WhatIf` de parameter (en ) en verwerkt deze `-Confirm` vervolgens dienovereenkomstig.</span><span class="sxs-lookup"><span data-stu-id="15a02-152">The call to `$PSCmdlet.ShouldProcess($file.name)` checks for the `-WhatIf` (and `-Confirm` parameter) then handles it accordingly.</span></span> <span data-ttu-id="15a02-153">De `-WhatIf` oorzaken zijn de uitvoer van een beschrijving van de wijziging en `ShouldProcess` retourneren `$false` :</span><span class="sxs-lookup"><span data-stu-id="15a02-153">The `-WhatIf` causes `ShouldProcess` to output a description of the change and return `$false`:</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

<span data-ttu-id="15a02-154">Een aanroep `-Confirm` met pauzeert het script en vraagt de gebruiker met de optie om door te gaan.</span><span class="sxs-lookup"><span data-stu-id="15a02-154">A call using `-Confirm` pauses the script and prompts the user with the option to continue.</span></span> <span data-ttu-id="15a02-155">Deze retourneert `$true` als de gebruiker heeft `Y` geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="15a02-155">It returns `$true` if the user selected `Y`.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="15a02-156">Een geweldige functie van `$PSCmdlet.ShouldProcess` is dat deze wordt verdubbeld als uitgebreide uitvoer.</span><span class="sxs-lookup"><span data-stu-id="15a02-156">An awesome feature of `$PSCmdlet.ShouldProcess` is that it doubles as verbose output.</span></span> <span data-ttu-id="15a02-157">Ik ben hier vaak van afhankelijk bij het implementeren `ShouldProcess` van .</span><span class="sxs-lookup"><span data-stu-id="15a02-157">I depend on this often when implementing `ShouldProcess`.</span></span>

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a><span data-ttu-id="15a02-158">Overloads</span><span class="sxs-lookup"><span data-stu-id="15a02-158">Overloads</span></span>

<span data-ttu-id="15a02-159">Er zijn enkele verschillende overloads voor `$PSCmdlet.ShouldProcess` met verschillende parameters voor het aanpassen van de berichten.</span><span class="sxs-lookup"><span data-stu-id="15a02-159">There are a few different overloads for `$PSCmdlet.ShouldProcess` with different parameters for customizing the messaging.</span></span> <span data-ttu-id="15a02-160">In het bovenstaande voorbeeld hebben we het eerste al gezien.</span><span class="sxs-lookup"><span data-stu-id="15a02-160">We already saw the first one in the example above.</span></span> <span data-ttu-id="15a02-161">Laten we dit eens nader bekijken.</span><span class="sxs-lookup"><span data-stu-id="15a02-161">Let's take a closer look at it.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

<span data-ttu-id="15a02-162">Dit produceert uitvoer die zowel de functienaam als het doel (waarde van de parameter) bevat.</span><span class="sxs-lookup"><span data-stu-id="15a02-162">This produces output that includes both the function name and the target (value of the parameter).</span></span>

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

<span data-ttu-id="15a02-163">Als u een tweede parameter opgeeft als de bewerking, wordt de bewerkingswaarde gebruikt in plaats van de functienaam in het bericht.</span><span class="sxs-lookup"><span data-stu-id="15a02-163">Specifying a second parameter as the operation uses the operation value instead of the function name in the message.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

<span data-ttu-id="15a02-164">De volgende optie is om drie parameters op te geven om het bericht volledig aan te passen.</span><span class="sxs-lookup"><span data-stu-id="15a02-164">The next option is to specify three parameters to fully customize the message.</span></span> <span data-ttu-id="15a02-165">Wanneer er drie parameters worden gebruikt, is de eerste het hele bericht.</span><span class="sxs-lookup"><span data-stu-id="15a02-165">When three parameters are used, the first one is the entire message.</span></span> <span data-ttu-id="15a02-166">De tweede twee parameters worden nog steeds gebruikt in de `-Confirm` berichtuitvoer.</span><span class="sxs-lookup"><span data-stu-id="15a02-166">The second two parameters are still used in the `-Confirm` message output.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a><span data-ttu-id="15a02-167">Snel naslagmateriaal voor parameters</span><span class="sxs-lookup"><span data-stu-id="15a02-167">Quick parameter reference</span></span>

<span data-ttu-id="15a02-168">Voor het geval u hier alleen bent om erachter te komen welke parameters u moet gebruiken, vindt u hier een snelle referentie die laat zien hoe de parameters het bericht in de verschillende scenario's `-WhatIf` wijzigen.</span><span class="sxs-lookup"><span data-stu-id="15a02-168">Just in case you came here only to figure out what parameters you should use, here is a quick reference showing how the parameters change the message in the different `-WhatIf` scenarios.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

<span data-ttu-id="15a02-169">Ik gebruik meestal de ene met twee parameters.</span><span class="sxs-lookup"><span data-stu-id="15a02-169">I tend to use the one with two parameters.</span></span>

### <a name="shouldprocessreason"></a><span data-ttu-id="15a02-170">ShouldProcessReason</span><span class="sxs-lookup"><span data-stu-id="15a02-170">ShouldProcessReason</span></span>

<span data-ttu-id="15a02-171">We hebben een vierde overbelasting die geavanceerder is dan de andere.</span><span class="sxs-lookup"><span data-stu-id="15a02-171">We have a fourth overload that's more advanced than the others.</span></span> <span data-ttu-id="15a02-172">Hiermee kunt u de reden van de `ShouldProcess` uitvoering zien.</span><span class="sxs-lookup"><span data-stu-id="15a02-172">It allows you to get the reason `ShouldProcess` was executed.</span></span> <span data-ttu-id="15a02-173">Ik voeg dit hier alleen toe voor de volledigheid, omdat we in plaats daarvan gewoon kunnen controleren of `$WhatIfPreference` dat `$true` zo is.</span><span class="sxs-lookup"><span data-stu-id="15a02-173">I'm only adding this here for completeness because we can just check if `$WhatIfPreference` is `$true` instead.</span></span>

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

<span data-ttu-id="15a02-174">We moeten de variabele doorgeven `$reason` aan de vierde parameter als referentievariabele met `[ref]` .</span><span class="sxs-lookup"><span data-stu-id="15a02-174">We have to pass the `$reason` variable into the fourth parameter as a reference variable with `[ref]`.</span></span> <span data-ttu-id="15a02-175">`ShouldProcess` wordt gevuld `$reason` met de waarde of `None` `WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="15a02-175">`ShouldProcess` populates `$reason` with the value `None` or `WhatIf`.</span></span> <span data-ttu-id="15a02-176">Ik heb niet gezegd dat dit nuttig is en ik heb geen reden gehad om het ooit te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="15a02-176">I didn't say this was useful and I have had no reason to ever use it.</span></span>

### <a name="where-to-place-it"></a><span data-ttu-id="15a02-177">Waar u het kunt plaatsen</span><span class="sxs-lookup"><span data-stu-id="15a02-177">Where to place it</span></span>

<span data-ttu-id="15a02-178">U gebruikt om `ShouldProcess` uw scripts veiliger te maken.</span><span class="sxs-lookup"><span data-stu-id="15a02-178">You use `ShouldProcess` to make your scripts safer.</span></span> <span data-ttu-id="15a02-179">U gebruikt deze dus wanneer uw scripts wijzigingen aanbrengen.</span><span class="sxs-lookup"><span data-stu-id="15a02-179">So you use it when your scripts are making changes.</span></span> <span data-ttu-id="15a02-180">Ik wil de `$PSCmdlet.ShouldProcess` aanroep zo dicht mogelijk bij de wijziging plaatsen.</span><span class="sxs-lookup"><span data-stu-id="15a02-180">I like to place the `$PSCmdlet.ShouldProcess` call as close to the change as possible.</span></span>

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

<span data-ttu-id="15a02-181">Als ik een verzameling items verwerkt, noem ik deze voor elk item.</span><span class="sxs-lookup"><span data-stu-id="15a02-181">If I'm processing a collection of items, I call it for each item.</span></span> <span data-ttu-id="15a02-182">De aanroep wordt dus in de foreach-lus geplaatst.</span><span class="sxs-lookup"><span data-stu-id="15a02-182">So the call gets placed inside the foreach loop.</span></span>

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

<span data-ttu-id="15a02-183">De reden waarom ik de wijziging nauw om de wijziging heen plaats, is dat ik zoveel mogelijk code wil uitvoeren `ShouldProcess` wanneer `-WhatIf` wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="15a02-183">The reason why I place `ShouldProcess` tightly around the change, is that I want as much code to execute as possible when `-WhatIf` is specified.</span></span> <span data-ttu-id="15a02-184">Ik wil dat de installatie en validatie zo mogelijk worden uitgevoerd, zodat de gebruiker deze fouten kan zien.</span><span class="sxs-lookup"><span data-stu-id="15a02-184">I want the setup and validation to run if possible so the user gets to see those errors.</span></span>

<span data-ttu-id="15a02-185">Ik wil dit ook gebruiken in mijn Tests voor het valideren van mijn projecten.</span><span class="sxs-lookup"><span data-stu-id="15a02-185">I also like to use this in my Pester tests that validate my projects.</span></span> <span data-ttu-id="15a02-186">Als ik een stukje logica heb dat moeilijk te na te denken is in een hoer, kan ik deze vaak inpakken en aanroepen `ShouldProcess` `-WhatIf` met in mijn tests.</span><span class="sxs-lookup"><span data-stu-id="15a02-186">If I have a piece of logic that is hard to mock in pester, I can often wrap it in `ShouldProcess` and call it with `-WhatIf` in my tests.</span></span> <span data-ttu-id="15a02-187">Het is beter om een deel van uw code te testen dan geen code.</span><span class="sxs-lookup"><span data-stu-id="15a02-187">It's better to test some of your code than none of it.</span></span>

### <a name="whatifpreference"></a><span data-ttu-id="15a02-188">$WhatIfPreference</span><span class="sxs-lookup"><span data-stu-id="15a02-188">$WhatIfPreference</span></span>

<span data-ttu-id="15a02-189">De eerste voorkeursvariabele die we hebben, is `$WhatIfPreference` .</span><span class="sxs-lookup"><span data-stu-id="15a02-189">The first preference variable we have is `$WhatIfPreference`.</span></span> <span data-ttu-id="15a02-190">Dit is `$false` standaard.</span><span class="sxs-lookup"><span data-stu-id="15a02-190">This is `$false` by default.</span></span> <span data-ttu-id="15a02-191">Als u deze in stelt `$true` op , wordt uw functie uitgevoerd alsof u hebt `-WhatIf` opgegeven.</span><span class="sxs-lookup"><span data-stu-id="15a02-191">If you set it to `$true` then your function executes as if you specified `-WhatIf`.</span></span> <span data-ttu-id="15a02-192">Als u dit in uw sessie in stelt, worden alle opdrachten `-WhatIf` uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="15a02-192">If you set this in your session, all commands perform `-WhatIf` execution.</span></span>

<span data-ttu-id="15a02-193">Wanneer u een functie aanroept met , wordt de waarde `-WhatIf` van ingesteld op binnen het bereik van uw `$WhatIfPreference` `$true` functie.</span><span class="sxs-lookup"><span data-stu-id="15a02-193">When you call a function with `-WhatIf`, the value of `$WhatIfPreference` gets set to `$true` inside the scope of your function.</span></span>

## <a name="confirmimpact"></a><span data-ttu-id="15a02-194">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="15a02-194">ConfirmImpact</span></span>

<span data-ttu-id="15a02-195">De meeste van mijn voorbeelden zijn `-WhatIf` voor, maar alles tot nu toe werkt ook met `-Confirm` om de gebruiker te vragen.</span><span class="sxs-lookup"><span data-stu-id="15a02-195">Most of my examples are for `-WhatIf` but everything so far also works with `-Confirm` to prompt the user.</span></span> <span data-ttu-id="15a02-196">U kunt de van de functie instellen op Hoog en de gebruiker wordt gevraagd of `ConfirmImpact` deze is aangeroepen met `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="15a02-196">You can set the `ConfirmImpact` of the function to high and it prompts the user as if it was called with `-Confirm`.</span></span>

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

<span data-ttu-id="15a02-197">Deze aanroep `Test-ShouldProcess` van voert de actie uit vanwege de `-Confirm` `High` impact.</span><span class="sxs-lookup"><span data-stu-id="15a02-197">This call to `Test-ShouldProcess` is performing the `-Confirm` action because of the `High` impact.</span></span>

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

<span data-ttu-id="15a02-198">Het voor de hand liggende probleem is dat het nu moeilijker is om in andere scripts te gebruiken zonder de gebruiker te vragen.</span><span class="sxs-lookup"><span data-stu-id="15a02-198">The obvious issue is that now it's harder to use in other scripts without prompting the user.</span></span> <span data-ttu-id="15a02-199">In dit geval kunnen we een doorgeven aan `$false` om de prompt te `-Confirm` onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="15a02-199">In this case, we can pass a `$false` to `-Confirm` to suppress the prompt.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

<span data-ttu-id="15a02-200">In een latere sectie wordt be lezen hoe `-Force` u ondersteuning toevoegt.</span><span class="sxs-lookup"><span data-stu-id="15a02-200">I'll cover how to add `-Force` support in a later section.</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="15a02-201">$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="15a02-201">$ConfirmPreference</span></span>

<span data-ttu-id="15a02-202">`$ConfirmPreference` is een automatische variabele die bepaalt wanneer `ConfirmImpact` u wordt gevraagd om de uitvoering te bevestigen.</span><span class="sxs-lookup"><span data-stu-id="15a02-202">`$ConfirmPreference` is an automatic variable that controls when `ConfirmImpact` asks you to confirm execution.</span></span> <span data-ttu-id="15a02-203">Hier zijn de mogelijke waarden voor zowel `$ConfirmPreference` als `ConfirmImpact` .</span><span class="sxs-lookup"><span data-stu-id="15a02-203">Here are the possible values for both `$ConfirmPreference` and `ConfirmImpact`.</span></span>

- `High`
- `Medium`
- `Low`
- `None`

<span data-ttu-id="15a02-204">Met deze waarden kunt u verschillende niveaus van impact voor elke functie opgeven.</span><span class="sxs-lookup"><span data-stu-id="15a02-204">With these values, you can specify different levels of impact for each function.</span></span> <span data-ttu-id="15a02-205">Als u hebt ingesteld op een waarde die hoger is dan , wordt u niet gevraagd `$ConfirmPreference` om de uitvoering te `ConfirmImpact` bevestigen.</span><span class="sxs-lookup"><span data-stu-id="15a02-205">If you have `$ConfirmPreference` set to a value higher than `ConfirmImpact`, then you aren't prompted to confirm execution.</span></span>

<span data-ttu-id="15a02-206">Is standaard `$ConfirmPreference` ingesteld op en is `High` `ConfirmImpact` `Medium` .</span><span class="sxs-lookup"><span data-stu-id="15a02-206">By default, `$ConfirmPreference` is set to `High` and `ConfirmImpact` is `Medium`.</span></span> <span data-ttu-id="15a02-207">Als u wilt dat de functie de gebruiker automatisch vraagt, stelt u uw `ConfirmImpact` in op `High` .</span><span class="sxs-lookup"><span data-stu-id="15a02-207">If you want your function to automatically prompt the user, set your `ConfirmImpact` to `High`.</span></span> <span data-ttu-id="15a02-208">Anders instellen op als `Medium` de destructieve en gebruiken `Low` als de opdracht altijd veilig in productie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="15a02-208">Otherwise set it to `Medium` if its destructive and use `Low` if the command is always safe run in production.</span></span> <span data-ttu-id="15a02-209">Als u deze in stelt op , wordt er niet om gevraagd, zelfs niet als is opgegeven (maar u wordt `none` `-Confirm` wel `-WhatIf` ondersteund).</span><span class="sxs-lookup"><span data-stu-id="15a02-209">If you set it to `none`, it doesn't prompt even if `-Confirm` was specified (but it still gives you `-WhatIf` support).</span></span>

<span data-ttu-id="15a02-210">Wanneer u een functie aanroept met , wordt de waarde `-Confirm` van ingesteld op binnen het bereik van uw `$ConfirmPreference` `Low` functie.</span><span class="sxs-lookup"><span data-stu-id="15a02-210">When calling a function with `-Confirm`, the value of `$ConfirmPreference` gets set to `Low` inside the scope of your function.</span></span>

### <a name="suppressing-nested-confirm-prompts"></a><span data-ttu-id="15a02-211">Geneste bevestigingsprompts onderdrukken</span><span class="sxs-lookup"><span data-stu-id="15a02-211">Suppressing nested confirm prompts</span></span>

<span data-ttu-id="15a02-212">De `$ConfirmPreference` kan worden opgehaald door functies die u aanroept.</span><span class="sxs-lookup"><span data-stu-id="15a02-212">The `$ConfirmPreference` can get picked up by functions that you call.</span></span> <span data-ttu-id="15a02-213">Dit kan scenario's maken waarbij u een bevestigingsprompt toevoegt en de functie die u aanroept ook de gebruiker vraagt.</span><span class="sxs-lookup"><span data-stu-id="15a02-213">This can create scenarios where you add a confirm prompt and the function you call also prompts the user.</span></span>

<span data-ttu-id="15a02-214">Wat ik meestal doe, is opgeven in de opdrachten die ik aanroep wanneer ik de prompt `-Confirm:$false` al heb afgehandeld.</span><span class="sxs-lookup"><span data-stu-id="15a02-214">What I tend to do is specify `-Confirm:$false` on the commands that I call when I have already handled the prompting.</span></span>

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

<span data-ttu-id="15a02-215">Dit brengt ons terug naar een eerdere waarschuwing: Er zijn nuances voor wanneer niet wordt doorgegeven aan een functie en wanneer wordt doorgegeven `-WhatIf` `-Confirm` aan een functie.</span><span class="sxs-lookup"><span data-stu-id="15a02-215">This brings us back to an earlier warning: There are nuances as to when `-WhatIf` is not passed to a function and when `-Confirm` passes to a function.</span></span> <span data-ttu-id="15a02-216">Ik ga dit later nog eens doen.</span><span class="sxs-lookup"><span data-stu-id="15a02-216">I promise I'll get back to this later.</span></span>

## <a name="pscmdletshouldcontinue"></a><span data-ttu-id="15a02-217">$PSCmdlet.ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="15a02-217">$PSCmdlet.ShouldContinue</span></span>

<span data-ttu-id="15a02-218">Als u meer controle nodig hebt dan `ShouldProcess` u hebt, kunt u de prompt rechtstreeks activeren met `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="15a02-218">If you need more control than `ShouldProcess` provides, you can trigger the prompt directly with `ShouldContinue`.</span></span> <span data-ttu-id="15a02-219">`ShouldContinue` negeert `$ConfirmPreference` `ConfirmImpact` , , , , en omdat `-Confirm` deze telkens wordt gevraagd als deze wordt `$WhatIfPreference` `-WhatIf` uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="15a02-219">`ShouldContinue` ignores `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference`, and `-WhatIf` because it prompts every time it's executed.</span></span>

<span data-ttu-id="15a02-220">In een oogopslag is het eenvoudig om en te `ShouldProcess` `ShouldContinue` verwarrend.</span><span class="sxs-lookup"><span data-stu-id="15a02-220">At a quick glance, it's easy to confuse `ShouldProcess` and `ShouldContinue`.</span></span> <span data-ttu-id="15a02-221">Ik vergeet niet om te `ShouldProcess` gebruiken, omdat de parameter wordt `SupportsShouldProcess` aangeroepen in de `CmdletBinding` .</span><span class="sxs-lookup"><span data-stu-id="15a02-221">I tend to remember to use `ShouldProcess` because the parameter is called `SupportsShouldProcess` in the `CmdletBinding`.</span></span>
<span data-ttu-id="15a02-222">U moet in `ShouldProcess` bijna elk scenario gebruiken.</span><span class="sxs-lookup"><span data-stu-id="15a02-222">You should use `ShouldProcess` in almost every scenario.</span></span> <span data-ttu-id="15a02-223">Daarom heb ik die methode eerst behandeld.</span><span class="sxs-lookup"><span data-stu-id="15a02-223">That is why I covered that method first.</span></span>

<span data-ttu-id="15a02-224">Laten we eens kijken `ShouldContinue` naar in actie.</span><span class="sxs-lookup"><span data-stu-id="15a02-224">Let's take a look at `ShouldContinue` in action.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="15a02-225">Dit biedt ons een eenvoudigere prompt met minder opties.</span><span class="sxs-lookup"><span data-stu-id="15a02-225">This provides us a simpler prompt with fewer options.</span></span>

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="15a02-226">Het grootste probleem met is dat de gebruiker deze interactief moet uitvoeren, omdat de gebruiker hier altijd `ShouldContinue` om wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="15a02-226">The biggest issue with `ShouldContinue` is that it requires the user to run it interactively because it always prompts the user.</span></span> <span data-ttu-id="15a02-227">U moet altijd hulpprogramma's bouwen die door andere scripts kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="15a02-227">You should always be building tools that can be used by other scripts.</span></span> <span data-ttu-id="15a02-228">De manier waarop u dit doet, is door te `-Force` implementeren.</span><span class="sxs-lookup"><span data-stu-id="15a02-228">The way you do this is by implementing `-Force`.</span></span> <span data-ttu-id="15a02-229">Ik kom later terug op dit idee.</span><span class="sxs-lookup"><span data-stu-id="15a02-229">I'll revisit this idea later.</span></span>

### <a name="yes-to-all"></a><span data-ttu-id="15a02-230">Ja op alles</span><span class="sxs-lookup"><span data-stu-id="15a02-230">Yes to all</span></span>

<span data-ttu-id="15a02-231">Dit wordt automatisch afgehandeld met , maar we moeten iets meer `ShouldProcess` doen voor `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="15a02-231">This is automatically handled with `ShouldProcess` but we have to do a little more work for `ShouldContinue`.</span></span> <span data-ttu-id="15a02-232">Er is een tweede methode-overload waarbij we een paar waarden moeten doorgeven om de logica te kunnen bepalen.</span><span class="sxs-lookup"><span data-stu-id="15a02-232">There's a second method overload where we have to pass in a few values by reference to control the logic.</span></span>

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

<span data-ttu-id="15a02-233">Ik heb een `foreach` lus en een verzameling toegevoegd om deze in actie te zien.</span><span class="sxs-lookup"><span data-stu-id="15a02-233">I added a `foreach` loop and a collection to show it in action.</span></span> <span data-ttu-id="15a02-234">Ik heb de `ShouldContinue` aanroep uit de `if` -instructie gehaald om het gemakkelijker te lezen.</span><span class="sxs-lookup"><span data-stu-id="15a02-234">I pulled the `ShouldContinue` call out of the `if` statement to make it easier to read.</span></span> <span data-ttu-id="15a02-235">Het aanroepen van een methode met vier parameters begint een beetje vervelend te worden, maar ik heb geprobeerd om deze er zo schoon mogelijk uit te laten zien.</span><span class="sxs-lookup"><span data-stu-id="15a02-235">Calling a method with four parameters starts to get a little ugly, but I tried to make it look as clean as I could.</span></span>

## <a name="implementing--force"></a><span data-ttu-id="15a02-236">-Force implementeren</span><span class="sxs-lookup"><span data-stu-id="15a02-236">Implementing -Force</span></span>

<span data-ttu-id="15a02-237">`ShouldProcess` en `ShouldContinue` moeten op verschillende manieren worden `-Force` geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="15a02-237">`ShouldProcess` and `ShouldContinue` need to implement `-Force` in different ways.</span></span> <span data-ttu-id="15a02-238">De trick voor deze implementaties is dat `ShouldProcess` altijd moet worden uitgevoerd, maar niet moet `ShouldContinue` worden uitgevoerd als is `-Force` opgegeven.</span><span class="sxs-lookup"><span data-stu-id="15a02-238">The trick to these implementations is that `ShouldProcess` should always get executed, but `ShouldContinue` should not get executed if `-Force` is specified.</span></span>

### <a name="shouldprocess--force"></a><span data-ttu-id="15a02-239">ShouldProcess - Force</span><span class="sxs-lookup"><span data-stu-id="15a02-239">ShouldProcess -Force</span></span>

<span data-ttu-id="15a02-240">Als u uw in stelt op , is het eerste wat uw gebruikers proberen te onderdrukken `ConfirmImpact` `high` met `-Force` .</span><span class="sxs-lookup"><span data-stu-id="15a02-240">If you set your `ConfirmImpact` to `high`, the first thing your users are going to try is to suppress it with `-Force`.</span></span> <span data-ttu-id="15a02-241">Dat is het eerste wat ik toch doe.</span><span class="sxs-lookup"><span data-stu-id="15a02-241">That's the first thing I do anyway.</span></span>

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

<span data-ttu-id="15a02-242">Zoals u zich nog herinnert `ConfirmImpact` uit de sectie, moeten ze deze als de volgende aanroepen:</span><span class="sxs-lookup"><span data-stu-id="15a02-242">If you recall from the `ConfirmImpact` section, they actually need to call it like this:</span></span>

```powershell
Test-ShouldProcess -Confirm:$false
```

<span data-ttu-id="15a02-243">Niet iedereen realiseert zich dat ze dat moeten doen `-Force` en onderdrukt `ShouldContinue` niet.</span><span class="sxs-lookup"><span data-stu-id="15a02-243">Not everyone realizes they need to do that and `-Force` doesn't suppress `ShouldContinue`.</span></span>
<span data-ttu-id="15a02-244">Daarom moeten we implementeren `-Force` voor de gezondheid van onze gebruikers.</span><span class="sxs-lookup"><span data-stu-id="15a02-244">So we should implement `-Force` for the sanity of our users.</span></span> <span data-ttu-id="15a02-245">Bekijk dit volledige voorbeeld hier:</span><span class="sxs-lookup"><span data-stu-id="15a02-245">Take a look at this full example here:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="15a02-246">We voegen onze eigen `-Force` switch toe als parameter.</span><span class="sxs-lookup"><span data-stu-id="15a02-246">We add our own `-Force` switch as a parameter.</span></span> <span data-ttu-id="15a02-247">De `-Confirm` parameter wordt automatisch toegevoegd wanneer wordt gebruikt in de `SupportsShouldProcess` `CmdletBinding` .</span><span class="sxs-lookup"><span data-stu-id="15a02-247">The `-Confirm` parameter is automatically added when using `SupportsShouldProcess` in the `CmdletBinding`.</span></span>

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

<span data-ttu-id="15a02-248">Richt u hier op `-Force` de logica:</span><span class="sxs-lookup"><span data-stu-id="15a02-248">Focusing in on the `-Force` logic here:</span></span>

```powershell
if ($Force){
    $ConfirmPreference = 'None'
}
```

<span data-ttu-id="15a02-249">Als de gebruiker `-Force` opgeeft, willen we de bevestigingsprompt onderdrukken, tenzij ze ook `-Confirm` opgeven.</span><span class="sxs-lookup"><span data-stu-id="15a02-249">If the user specifies `-Force`, we want to suppress the confirm prompt unless they also specify `-Confirm`.</span></span> <span data-ttu-id="15a02-250">Hierdoor kan een gebruiker een wijziging forcen, maar toch de wijziging bevestigen.</span><span class="sxs-lookup"><span data-stu-id="15a02-250">This allows a user to force a change but still confirm the change.</span></span> <span data-ttu-id="15a02-251">Vervolgens stellen we `$ConfirmPreference` in het lokale bereik in.</span><span class="sxs-lookup"><span data-stu-id="15a02-251">Then we set `$ConfirmPreference` in the local scope.</span></span> <span data-ttu-id="15a02-252">Nu stelt u met de parameter tijdelijk de in op geen, en wordt `-Force` de prompt om bevestiging uit te `$ConfirmPreference` stellen.</span><span class="sxs-lookup"><span data-stu-id="15a02-252">Now, using the `-Force` parameter temporarily sets the `$ConfirmPreference` to none, disabling prompt for confirmation.</span></span>

```powershell
if ($Force -or $PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

<span data-ttu-id="15a02-253">Als iemand zowel als `-Force` opfeit, `-WhatIf` moet deze prioriteit `-WhatIf` krijgen.</span><span class="sxs-lookup"><span data-stu-id="15a02-253">If someone specifies both `-Force` and `-WhatIf`, then `-WhatIf` needs to take priority.</span></span> <span data-ttu-id="15a02-254">Deze aanpak behoudt `-WhatIf` de verwerking omdat altijd wordt `ShouldProcess` uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="15a02-254">This approach preserves `-WhatIf` processing because `ShouldProcess` always gets executed.</span></span>

<span data-ttu-id="15a02-255">Voeg geen controle toe voor de waarde `$Force` in de instructie met de `if` `ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="15a02-255">Do not add a check for the `$Force` value inside the `if` statement with the `ShouldProcess`.</span></span> <span data-ttu-id="15a02-256">Dat is een antipatroon voor dit specifieke scenario, ook al laat ik u dat zien in de volgende sectie voor `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="15a02-256">That is an anti-pattern for this specific scenario even though that's what I show you in the next section for `ShouldContinue`.</span></span>

### <a name="shouldcontinue--force"></a><span data-ttu-id="15a02-257">ShouldContinue -Force</span><span class="sxs-lookup"><span data-stu-id="15a02-257">ShouldContinue -Force</span></span>

<span data-ttu-id="15a02-258">Dit is de juiste manier om te `-Force` implementeren met `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="15a02-258">This is the correct way to implement `-Force` with `ShouldContinue`.</span></span>

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

<span data-ttu-id="15a02-259">Door de `$Force` links van de operator te `-or` plaatsen, wordt deze eerst geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="15a02-259">By placing the `$Force` to the left of the `-or` operator, it gets evaluated first.</span></span> <span data-ttu-id="15a02-260">Als u deze op deze manier schrijft, wordt de uitvoering van de `if` -instructie verkort.</span><span class="sxs-lookup"><span data-stu-id="15a02-260">Writing it this way short circuits the execution of the `if` statement.</span></span> <span data-ttu-id="15a02-261">Als `$force` `$true` is, wordt `ShouldContinue` de niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="15a02-261">If `$force` is `$true`, then the `ShouldContinue` is not executed.</span></span>

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

<span data-ttu-id="15a02-262">We hoeven ons geen zorgen te maken over `-Confirm` of in dit scenario omdat ze niet worden ondersteund door `-WhatIf` `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="15a02-262">We don't have to worry about `-Confirm` or `-WhatIf` in this scenario because they're not supported by `ShouldContinue`.</span></span> <span data-ttu-id="15a02-263">Daarom moet dit anders worden verwerkt dan `ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="15a02-263">This is why it needs to be handled differently than `ShouldProcess`.</span></span>

## <a name="scope-issues"></a><span data-ttu-id="15a02-264">Bereikproblemen</span><span class="sxs-lookup"><span data-stu-id="15a02-264">Scope issues</span></span>

<span data-ttu-id="15a02-265">Het `-WhatIf` gebruik van en moet van toepassing zijn op alles in uw functies en alles wat ze `-Confirm` aanroepen.</span><span class="sxs-lookup"><span data-stu-id="15a02-265">Using `-WhatIf` and `-Confirm` are supposed to apply to everything inside your functions and everything they call.</span></span> <span data-ttu-id="15a02-266">Ze doen dit door in te `$WhatIfPreference` stellen op of in te stellen op in het lokale bereik van de `$true` `$ConfirmPreference` `Low` functie.</span><span class="sxs-lookup"><span data-stu-id="15a02-266">They do this by setting `$WhatIfPreference` to `$true` or setting `$ConfirmPreference` to `Low` in the local scope of the function.</span></span> <span data-ttu-id="15a02-267">Wanneer u een andere functie aanroept, roept u aan `ShouldProcess` om deze waarden te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="15a02-267">When you call another function, calls to `ShouldProcess` use those values.</span></span>

<span data-ttu-id="15a02-268">Dit werkt in de meeste tijd correct.</span><span class="sxs-lookup"><span data-stu-id="15a02-268">This actually works correctly most of the time.</span></span> <span data-ttu-id="15a02-269">Steeds wanneer u de ingebouwde cmdlet of een functie in hetzelfde bereik aanroept, werkt deze.</span><span class="sxs-lookup"><span data-stu-id="15a02-269">Anytime you call built-in cmdlet or a function in your same scope, it works.</span></span> <span data-ttu-id="15a02-270">Het werkt ook wanneer u een script of een functie in een scriptmodule aanroept vanuit de -console.</span><span class="sxs-lookup"><span data-stu-id="15a02-270">It also works when you call a script or a function in a script module from the console.</span></span>

<span data-ttu-id="15a02-271">De ene specifieke plaats waar het niet werkt, is wanneer een script of scriptmodule een functie aanroept in een andere scriptmodule.</span><span class="sxs-lookup"><span data-stu-id="15a02-271">The one specific place where it doesn't work is when a script or a script module calls a function in another script module.</span></span> <span data-ttu-id="15a02-272">Dit klinkt misschien niet als een groot probleem, maar de meeste modules die u maakt of pullt uit PSGallery zijn scriptmodules.</span><span class="sxs-lookup"><span data-stu-id="15a02-272">This may not sound like a big problem, but most of the modules you create or pull from the PSGallery are script modules.</span></span>

<span data-ttu-id="15a02-273">Het belangrijkste probleem is dat scriptmodules de waarden voor of (en verschillende andere) niet overnemen wanneer ze worden aangeroepen vanuit `$WhatIfPreference` `$ConfirmPreference` functies in andere scriptmodules.</span><span class="sxs-lookup"><span data-stu-id="15a02-273">The core issue is that script modules do not inherit the values for `$WhatIfPreference` or `$ConfirmPreference` (and several others) when called from functions in other script modules.</span></span>

<span data-ttu-id="15a02-274">De beste manier om dit samen te vatten als een algemene regel is dat dit correct werkt voor binaire modules en nooit vertrouwt dat het werkt voor scriptmodules.</span><span class="sxs-lookup"><span data-stu-id="15a02-274">The best way to summarize this as a general rule is that this works correctly for binary modules and never trust it to work for script modules.</span></span> <span data-ttu-id="15a02-275">Als u het niet zeker weet, test u deze of gaat u ervan uit dat het niet correct werkt.</span><span class="sxs-lookup"><span data-stu-id="15a02-275">If you aren't sure, either test it or just assume it doesn't work correctly.</span></span>

<span data-ttu-id="15a02-276">Persoonlijk vind ik dit erg gevaarlijk omdat er scenario's worden gemaakt waarin u ondersteuning toevoegt aan meerdere modules die op de juiste manier werken, maar niet goed werken wanneer ze elkaar `-WhatIf` aanroepen.</span><span class="sxs-lookup"><span data-stu-id="15a02-276">I personally feel this is very dangerous because it creates scenarios where you add `-WhatIf` support to multiple modules that work correctly in isolation, but fail to work correctly when they call each other.</span></span>

<span data-ttu-id="15a02-277">We hebben een GitHub RFC die werkt om dit probleem op te lossen.</span><span class="sxs-lookup"><span data-stu-id="15a02-277">We do have a GitHub RFC working to get this issue fixed.</span></span> <span data-ttu-id="15a02-278">Zie [Uitvoeringsvoorkeuren doorgeven buiten het bereik van scriptmodule][RFC] voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="15a02-278">See [Propagate execution preferences beyond script module scope][RFC] for more details.</span></span>

## <a name="in-closing"></a><span data-ttu-id="15a02-279">Afsluitend</span><span class="sxs-lookup"><span data-stu-id="15a02-279">In closing</span></span>

<span data-ttu-id="15a02-280">Ik moet elke keer dat ik het nodig heb, op zoek naar hoe `ShouldProcess` ik het moet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="15a02-280">I have to look up how to use `ShouldProcess` every time I need to use it.</span></span> <span data-ttu-id="15a02-281">Het duurde lang om te onderscheiden van `ShouldProcess` `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="15a02-281">It took me a long time to distinguish `ShouldProcess` from `ShouldContinue`.</span></span> <span data-ttu-id="15a02-282">Ik moet bijna altijd op zoek naar de parameters die ik moet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="15a02-282">I almost always need to look up what parameters to use.</span></span> <span data-ttu-id="15a02-283">U hoeft zich dus geen zorgen te maken als u van tijd tot tijd nog steeds in de war raakt.</span><span class="sxs-lookup"><span data-stu-id="15a02-283">So don't worry if you still get confused from time to time.</span></span> <span data-ttu-id="15a02-284">Dit artikel vindt u hier wanneer u het nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="15a02-284">This article will be here when you need it.</span></span> <span data-ttu-id="15a02-285">Ik weet zeker dat ik er zelf vaak naar verwijs.</span><span class="sxs-lookup"><span data-stu-id="15a02-285">I'm sure I will reference it often myself.</span></span>

<span data-ttu-id="15a02-286">Als u tevreden bent over dit bericht, kunt u uw mening met mij delen op Twitter via de onderstaande koppeling.</span><span class="sxs-lookup"><span data-stu-id="15a02-286">If you liked this post, please share your thoughts with me on Twitter using the link below.</span></span> <span data-ttu-id="15a02-287">Ik vind het altijd leuk om te horen van mensen die waarde krijgen uit mijn inhoud.</span><span class="sxs-lookup"><span data-stu-id="15a02-287">I always like hearing from people that get value from my content.</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[original version]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[algemene parameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[common parameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[alles wat u wilde weten over hashtables]: everything-about-hashtable.md
[everything you wanted to know about hashtables]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
