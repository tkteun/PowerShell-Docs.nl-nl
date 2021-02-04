---
title: Het Help-systeem
description: Het model leren van het Help-systeem is de sleutel om met Power shell te kunnen slagen.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: cfb12f57b7bb6c514f4e19a93dfe9c77245bd977
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216135"
---
# <a name="chapter-2---the-help-system"></a><span data-ttu-id="4c67d-103">Hoofd stuk 2: het Help-systeem</span><span class="sxs-lookup"><span data-stu-id="4c67d-103">Chapter 2 - The Help System</span></span>

<span data-ttu-id="4c67d-104">Er zijn twee groepen IT-professionals die een geschreven test hebben ontvangen zonder toegang tot een computer om het niveau van hun vaardig heden te bepalen met Power shell.</span><span class="sxs-lookup"><span data-stu-id="4c67d-104">Two groups of IT pros were given a written test without access to a computer to determine their skill level with PowerShell.</span></span> <span data-ttu-id="4c67d-105">Beginners van Power shell zijn in één groep en experts in een ander opgenomen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-105">PowerShell beginners were placed in one group and experts in another.</span></span>
<span data-ttu-id="4c67d-106">Op basis van de resultaten van de test lijkt het niet veel verschil in het vaardigheids niveau tussen de twee groepen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-106">Based on the results of the test, there didn't seem to be much difference in the skill level between the two groups.</span></span> <span data-ttu-id="4c67d-107">Beide groepen hebben een tweede test gegeven die vergelijkbaar is met die van de eerste.</span><span class="sxs-lookup"><span data-stu-id="4c67d-107">Both groups were given a second test similar to the first one.</span></span> <span data-ttu-id="4c67d-108">Deze keer werd toegang verleend tot een computer met Power shell die geen toegang tot internet heeft.</span><span class="sxs-lookup"><span data-stu-id="4c67d-108">This time they were given access to a computer with PowerShell that didn't have access to the internet.</span></span> <span data-ttu-id="4c67d-109">De resultaten van de tweede test hebben een enorme verschillen in het vaardigheids niveau tussen de twee groepen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-109">The results of the second test showed a huge difference in the skill level between the two groups.</span></span> <span data-ttu-id="4c67d-110">Experts kennen niet altijd de antwoorden, maar ze weten hoe ze de antwoorden kunnen achterhalen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-110">Experts don't always know the answers, but they know how to figure out the answers.</span></span>

<span data-ttu-id="4c67d-111">Wat is het verschil in de resultaten van de eerste en tweede test tussen deze twee groepen?</span><span class="sxs-lookup"><span data-stu-id="4c67d-111">What was the difference in the results of the first and second test between these two groups?</span></span>

<span data-ttu-id="4c67d-112">De verschillen die in deze twee tests worden waargenomen, waren omdat experts niet weten hoe duizenden opdrachten in Power shell moeten worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4c67d-112">The differences observed in these two tests were because experts don't memorize how to use thousands of commands in PowerShell.</span></span> <span data-ttu-id="4c67d-113">Ze leren hoe het Help-systeem in Power shell extreem goed kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4c67d-113">They learn how to use the help system within PowerShell extremely well.</span></span>
<span data-ttu-id="4c67d-114">Op die manier kunnen ze de benodigde opdrachten vinden wanneer dat nodig is en hoe deze opdrachten kunnen worden gebruikt wanneer ze ze hebben gevonden.</span><span class="sxs-lookup"><span data-stu-id="4c67d-114">This allows them to find the necessary commands when needed and how to use those commands once they've found them.</span></span>

<span data-ttu-id="4c67d-115">Ik heb Jeffrey Snover, de voor Raad van Power shell, een aantal keren een vergelijkbaar verhaal.</span><span class="sxs-lookup"><span data-stu-id="4c67d-115">I've heard Jeffrey Snover, the inventor of PowerShell, tell a similar story a number of times.</span></span>

<span data-ttu-id="4c67d-116">Het model leren van het Help-systeem is de sleutel om met Power shell te kunnen slagen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-116">Mastering the help system is the key to being successful with PowerShell.</span></span>

## <a name="discoverability"></a><span data-ttu-id="4c67d-117">Detectie</span><span class="sxs-lookup"><span data-stu-id="4c67d-117">Discoverability</span></span>

<span data-ttu-id="4c67d-118">Gecompileerde opdrachten in Power shell worden cmdlets genoemd.</span><span class="sxs-lookup"><span data-stu-id="4c67d-118">Compiled commands in PowerShell are called cmdlets.</span></span> <span data-ttu-id="4c67d-119">De cmdlet is uitgesp roken met opdracht-Let (niet CMD-Let).</span><span class="sxs-lookup"><span data-stu-id="4c67d-119">Cmdlet is pronounced "command-let" (not CMD-let).</span></span> <span data-ttu-id="4c67d-120">Namen van cmdlets hebben de vorm van enkelvoudige ' verb-'-opdrachten om ze gemakkelijk te kunnen detecteren.</span><span class="sxs-lookup"><span data-stu-id="4c67d-120">Cmdlets names have the form of singular "Verb-Noun" commands to make them easily discoverable.</span></span> <span data-ttu-id="4c67d-121">De cmdlet voor het bepalen van de uitvoering van de processen is bijvoorbeeld `Get-Process` en de cmdlet voor het ophalen van een lijst met Services en hun status `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="4c67d-121">For example, the cmdlet for determining what processes are running is `Get-Process` and the cmdlet for retrieving a list of services and their statuses is `Get-Service`.</span></span> <span data-ttu-id="4c67d-122">Er zijn andere soorten opdrachten in Power shell, zoals aliassen en functies die verderop in dit boek worden behandeld.</span><span class="sxs-lookup"><span data-stu-id="4c67d-122">There are other types of commands in PowerShell such as aliases and functions that will be covered later in this book.</span></span> <span data-ttu-id="4c67d-123">De term Power shell-opdracht is een algemene term die vaak wordt gebruikt om te verwijzen naar een wille keurig type opdracht in Power shell, ongeacht of het een cmdlet, functie of alias is.</span><span class="sxs-lookup"><span data-stu-id="4c67d-123">The term PowerShell command is a generic term that's often used to refer to any type of command in PowerShell, regardless of whether or not it's a cmdlet, function, or alias.</span></span>

## <a name="the-three-core-cmdlets-in-powershell"></a><span data-ttu-id="4c67d-124">De drie kern-cmdlets in Power shell</span><span class="sxs-lookup"><span data-stu-id="4c67d-124">The Three Core Cmdlets in PowerShell</span></span>

- `Get-Command`
- `Get-Help`
- <span data-ttu-id="4c67d-125">`Get-Member` (bedoeld in hoofd stuk 3)</span><span class="sxs-lookup"><span data-stu-id="4c67d-125">`Get-Member` (covered in chapter 3)</span></span>

<span data-ttu-id="4c67d-126">Hoe weet ik vaak hoe snel u weet wat de opdrachten zijn in Power shell?</span><span class="sxs-lookup"><span data-stu-id="4c67d-126">One question I'm often asked is how do you figure out what the commands are in PowerShell?</span></span> <span data-ttu-id="4c67d-127">Beide `Get-Command` en `Get-Help` kunnen worden gebruikt om de opdrachten te bepalen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-127">Both `Get-Command` and `Get-Help` can be used to determine the commands.</span></span>

## <a name="get-help"></a><span data-ttu-id="4c67d-128">Get-Help</span><span class="sxs-lookup"><span data-stu-id="4c67d-128">Get-Help</span></span>

<span data-ttu-id="4c67d-129">`Get-Help` is een opdracht voor meerdere doel einden.</span><span class="sxs-lookup"><span data-stu-id="4c67d-129">`Get-Help` is a multipurpose command.</span></span> <span data-ttu-id="4c67d-130">`Get-Help` helpt u bij het gebruik van opdrachten nadat u ze hebt gevonden.</span><span class="sxs-lookup"><span data-stu-id="4c67d-130">`Get-Help` helps you learn how to use commands once you find them.</span></span> <span data-ttu-id="4c67d-131">`Get-Help` kan ook worden gebruikt om opdrachten te vinden, maar op een andere en meer indirecte wijze in vergelijking tot `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="4c67d-131">`Get-Help` can also be used to help locate commands, but in a different and more indirect way when compared to `Get-Command`.</span></span>

<span data-ttu-id="4c67d-132">Wanneer `Get-Help` wordt gebruikt om opdrachten te vinden, zoekt het eerst naar Joker tekens die overeenkomen met de opdracht namen op basis van de opgegeven invoer.</span><span class="sxs-lookup"><span data-stu-id="4c67d-132">When `Get-Help` is used to locate commands, it first searches for wildcard matches of command names based on the provided input.</span></span> <span data-ttu-id="4c67d-133">Als er geen overeenkomst wordt gevonden, wordt gezocht in de Help-onderwerpen zelf. als er geen overeenkomst wordt gevonden, wordt er een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4c67d-133">If it doesn't find a match, it searches through the help topics themselves, and if no match is found an error is returned.</span></span> <span data-ttu-id="4c67d-134">In tegens telling tot populaire geloofs `Get-Help` kan worden gebruikt om opdrachten te vinden die geen Help-onderwerpen bevatten.</span><span class="sxs-lookup"><span data-stu-id="4c67d-134">Contrary to popular belief, `Get-Help` can be used to find commands that don't have help topics.</span></span>

<span data-ttu-id="4c67d-135">Het eerste wat u moet weten over het Help-systeem in Power shell is het gebruik van de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c67d-135">The first thing you need to know about the help system in PowerShell is how to use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="4c67d-136">De volgende opdracht wordt gebruikt om het Help-onderwerp voor weer te geven `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="4c67d-136">The following command is used to display the help topic for `Get-Help`.</span></span>

```powershell
Get-Help -Name Get-Help
```

```Output
Do you want to run Update-Help?
The Update-Help cmdlet downloads the most current Help files for Windows PowerShell
modules, and installs them on your computer. For more information about the Update-Help
cmdlet, see http://go.microsoft.com/fwlink/?LinkId=210614.
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="4c67d-137">Vanaf Power shell versie 3 wordt de Power shell-Help niet geleverd bij het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="4c67d-137">Beginning with PowerShell version 3, PowerShell help doesn't ship with the operating system.</span></span> <span data-ttu-id="4c67d-138">De eerste keer dat `Get-Help` voor een opdracht wordt uitgevoerd, wordt het vorige bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c67d-138">The first time `Get-Help` is run for a command, the previous message is displayed.</span></span> <span data-ttu-id="4c67d-139">Als de `help` functie of `man` alias wordt gebruikt in plaats van de `Get-Help` cmdlet, wordt dit bericht niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c67d-139">If the `help` function or `man` alias is used instead of the `Get-Help` cmdlet, you don't receive this prompt.</span></span>

<span data-ttu-id="4c67d-140">Als u Ja antwoordt door op <kbd>Y</kbd> wordt de `Update-Help` cmdlet uit te voeren. hiervoor is standaard Internet toegang vereist.</span><span class="sxs-lookup"><span data-stu-id="4c67d-140">Answering yes by pressing <kbd>Y</kbd> runs the `Update-Help` cmdlet, which requires internet access by default.</span></span> <span data-ttu-id="4c67d-141">`Y` kan worden opgegeven in een hoofd-of kleine letter.</span><span class="sxs-lookup"><span data-stu-id="4c67d-141">`Y` can be specified in either upper or lower case.</span></span>

<span data-ttu-id="4c67d-142">Zodra de Help is gedownload en de update is voltooid, wordt het Help-onderwerp geretourneerd voor de opgegeven opdracht:</span><span class="sxs-lookup"><span data-stu-id="4c67d-142">Once the help is downloaded and the update is complete, the help topic is returned for the specified command:</span></span>

```powershell
Get-Help -Name Get-Help
```

<span data-ttu-id="4c67d-143">Neem even de tijd om dit voor beeld uit te voeren op uw computer, Bekijk de uitvoer en Let op hoe de gegevens worden gegroepeerd:</span><span class="sxs-lookup"><span data-stu-id="4c67d-143">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="4c67d-144">NAAM</span><span class="sxs-lookup"><span data-stu-id="4c67d-144">NAME</span></span>
- <span data-ttu-id="4c67d-145">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4c67d-145">SYNOPSIS</span></span>
- <span data-ttu-id="4c67d-146">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4c67d-146">SYNTAX</span></span>
- <span data-ttu-id="4c67d-147">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4c67d-147">DESCRIPTION</span></span>
- <span data-ttu-id="4c67d-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4c67d-148">RELATED LINKS</span></span>
- <span data-ttu-id="4c67d-149">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4c67d-149">REMARKS</span></span>

<span data-ttu-id="4c67d-150">Zoals u kunt zien, kunnen Help-onderwerpen een enorme hoeveelheid informatie bevatten, maar dit is niet het volledige Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="4c67d-150">As you can see, help topics can contain an enormous amount of information and this isn't even the entire help topic.</span></span>

<span data-ttu-id="4c67d-151">Hoewel het niet specifiek is voor Power shell, is een para meter een manier om invoer te leveren aan een opdracht.</span><span class="sxs-lookup"><span data-stu-id="4c67d-151">While not specific to PowerShell, a parameter is a way to provide input to a command.</span></span> <span data-ttu-id="4c67d-152">`Get-Help` heeft veel para meters die kunnen worden opgegeven om het volledige Help-onderwerp of een subset ervan te retour neren.</span><span class="sxs-lookup"><span data-stu-id="4c67d-152">`Get-Help` has many parameters that can be specified in order to return the entire help topic or a subset of it.</span></span>

<span data-ttu-id="4c67d-153">De sectie syntaxis van het Help-onderwerp dat wordt weer gegeven in de vorige set met resultaten bevat een lijst met alle para meters voor `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="4c67d-153">The syntax section of the help topic shown in the previous set of results lists all of the parameters for `Get-Help`.</span></span> <span data-ttu-id="4c67d-154">Op het eerste gezicht ziet u dezelfde para meters die zes verschillende tijdstippen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c67d-154">At first glance, it appears the same parameters are listed six different times.</span></span> <span data-ttu-id="4c67d-155">Elk van deze verschillende blokken in de syntaxis sectie is een parameterset.</span><span class="sxs-lookup"><span data-stu-id="4c67d-155">Each of those different blocks in the syntax section is a parameter set.</span></span> <span data-ttu-id="4c67d-156">Dit betekent dat de `Get-Help` cmdlet zes verschillende parameter sets heeft.</span><span class="sxs-lookup"><span data-stu-id="4c67d-156">This means the `Get-Help` cmdlet has six different parameter sets.</span></span> <span data-ttu-id="4c67d-157">Als u een kijkje neemt, ziet u dat ten minste één para meter in elk van de parameter sets anders is.</span><span class="sxs-lookup"><span data-stu-id="4c67d-157">If you take a closer look, you'll notice that at least one parameter is different in each of the parameter sets.</span></span>

<span data-ttu-id="4c67d-158">Parameter sets sluiten elkaar wederzijds uit.</span><span class="sxs-lookup"><span data-stu-id="4c67d-158">Parameter sets are mutually exclusive.</span></span> <span data-ttu-id="4c67d-159">Wanneer een unieke para meter die alleen in een van de parameter sets voor komt, wordt gebruikt, kunnen alleen para meters in die set para meters worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4c67d-159">Once a unique parameter that only exists in one of the parameter sets is used, only parameters contained within that parameter set can be used.</span></span> <span data-ttu-id="4c67d-160">Zo kunnen zowel de **volledige** als de **gedetailleerde** para meters op hetzelfde moment niet worden opgegeven omdat ze zich in verschillende parameter sets bevinden.</span><span class="sxs-lookup"><span data-stu-id="4c67d-160">For example, both the **Full** and **Detailed** parameters couldn't be specified at the same time because they are in different parameter sets.</span></span>

<span data-ttu-id="4c67d-161">Elk van de volgende para meters bevinden zich in verschillende parameter sets:</span><span class="sxs-lookup"><span data-stu-id="4c67d-161">Each of the following parameters are in different parameter sets:</span></span>

- <span data-ttu-id="4c67d-162">Volledig</span><span class="sxs-lookup"><span data-stu-id="4c67d-162">Full</span></span>
- <span data-ttu-id="4c67d-163">Gedetailleerd</span><span class="sxs-lookup"><span data-stu-id="4c67d-163">Detailed</span></span>
- <span data-ttu-id="4c67d-164">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="4c67d-164">Examples</span></span>
- <span data-ttu-id="4c67d-165">Online</span><span class="sxs-lookup"><span data-stu-id="4c67d-165">Online</span></span>
- <span data-ttu-id="4c67d-166">Parameter</span><span class="sxs-lookup"><span data-stu-id="4c67d-166">Parameter</span></span>
- <span data-ttu-id="4c67d-167">ShowWindow</span><span class="sxs-lookup"><span data-stu-id="4c67d-167">ShowWindow</span></span>

<span data-ttu-id="4c67d-168">Alle cryptische syntaxis, zoals vier Kante en punt haken in de syntaxis sectie, betekent iets, maar wordt wel behandeld in bijlage A van dit boek.</span><span class="sxs-lookup"><span data-stu-id="4c67d-168">All of the cryptic syntax such as square and angle brackets in the syntax section means something but will be covered in Appendix A of this book.</span></span> <span data-ttu-id="4c67d-169">Het is belang rijk dat u weet dat de cryptische syntaxis vaak moeilijk te bewaren is voor iemand die geen ervaring heeft met Power shell en deze mogelijk niet dagelijks gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4c67d-169">While important, learning the cryptic syntax is often difficult to retain for someone who is new to PowerShell and may not use it everyday.</span></span>

<span data-ttu-id="4c67d-170">Zie [bijlage A][]voor meer informatie over het beter begrijpen van de cryptische syntaxis.</span><span class="sxs-lookup"><span data-stu-id="4c67d-170">For more information to better understand the cryptic syntax, see [Appendix A][].</span></span>

<span data-ttu-id="4c67d-171">Voor beginners is er een eenvoudige manier om dezelfde informatie te achterhalen, behalve in de taal normaal.</span><span class="sxs-lookup"><span data-stu-id="4c67d-171">For beginners, there's an easier way to figure out the same information except in plain language.</span></span>

<span data-ttu-id="4c67d-172">Wanneer de **volledige** para meter van `Get-Help` is opgegeven, wordt het volledige Help-onderwerp geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4c67d-172">When the **Full** parameter of `Get-Help` is specified, the entire help topic is returned.</span></span>

```powershell
Get-Help -Name Get-Help -Full
```

<span data-ttu-id="4c67d-173">Neem even de tijd om dit voor beeld uit te voeren op uw computer, Bekijk de uitvoer en Let op hoe de gegevens worden gegroepeerd:</span><span class="sxs-lookup"><span data-stu-id="4c67d-173">Take a moment to run that example on your computer, review the output, and take note of how the information is grouped:</span></span>

- <span data-ttu-id="4c67d-174">NAAM</span><span class="sxs-lookup"><span data-stu-id="4c67d-174">NAME</span></span>
- <span data-ttu-id="4c67d-175">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4c67d-175">SYNOPSIS</span></span>
- <span data-ttu-id="4c67d-176">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4c67d-176">SYNTAX</span></span>
- <span data-ttu-id="4c67d-177">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4c67d-177">DESCRIPTION</span></span>
- <span data-ttu-id="4c67d-178">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4c67d-178">PARAMETERS</span></span>
- <span data-ttu-id="4c67d-179">INVOER</span><span class="sxs-lookup"><span data-stu-id="4c67d-179">INPUTS</span></span>
- <span data-ttu-id="4c67d-180">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4c67d-180">OUTPUTS</span></span>
- <span data-ttu-id="4c67d-181">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4c67d-181">NOTES</span></span>
- <span data-ttu-id="4c67d-182">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4c67d-182">EXAMPLES</span></span>
- <span data-ttu-id="4c67d-183">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4c67d-183">RELATED LINKS</span></span>

<span data-ttu-id="4c67d-184">U ziet dat met behulp van de **volledige** para meter verschillende extra secties zijn geretourneerd, een van de para meters die meer informatie bevat dan de sectie cryptische syntaxis.</span><span class="sxs-lookup"><span data-stu-id="4c67d-184">Notice that using the **Full** parameter returned several additional sections, one of which is the PARAMETERS section that provides more information than the cryptic SYNTAX section.</span></span>

<span data-ttu-id="4c67d-185">De **volledige** para meter is een switch parameter.</span><span class="sxs-lookup"><span data-stu-id="4c67d-185">The **Full** parameter is a switch parameter.</span></span> <span data-ttu-id="4c67d-186">Een para meter waarvoor geen waarde is vereist, wordt een switch parameter genoemd.</span><span class="sxs-lookup"><span data-stu-id="4c67d-186">A parameter that doesn't require a value is called a switch parameter.</span></span> <span data-ttu-id="4c67d-187">Wanneer een switch parameter wordt opgegeven, is de waarde ervan True en wanneer dat niet het geval is, is de waarde false.</span><span class="sxs-lookup"><span data-stu-id="4c67d-187">When a switch parameter is specified, its value is true and when it's not, its value is false.</span></span>

<span data-ttu-id="4c67d-188">Als u dit hoofd stuk in de Power shell-console hebt door lopen, hebt u opgemerkt dat de vorige opdracht om het volledige Help-onderwerp voor vloog weer te geven `Get-Help` op het scherm, zonder dat u de kans krijgt om het te lezen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-188">If you've been working through this chapter in the PowerShell console, you noticed that the previous command to display the full help topic for `Get-Help` flew by on the screen without giving you a chance to read it.</span></span> <span data-ttu-id="4c67d-189">Er is een betere manier.</span><span class="sxs-lookup"><span data-stu-id="4c67d-189">There's a better way.</span></span>

<span data-ttu-id="4c67d-190">`Help` is een functie die pipet `Get-Help` naar een functie met `more` de naam, een wrapper voor het `more.com` uitvoer bare bestand in Windows.</span><span class="sxs-lookup"><span data-stu-id="4c67d-190">`Help` is a function that pipes `Get-Help` to a function named `more`, which is a wrapper for the `more.com` executable file in Windows.</span></span> <span data-ttu-id="4c67d-191">In de Power shell-console `help` biedt één pagina met Help per keer.</span><span class="sxs-lookup"><span data-stu-id="4c67d-191">In the PowerShell console, `help` provides one page of help at a time.</span></span> <span data-ttu-id="4c67d-192">In de ISE werkt het op dezelfde manier als `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="4c67d-192">In the ISE, it works the same way as `Get-Help`.</span></span> <span data-ttu-id="4c67d-193">Mijn aanbeveling is de functie te gebruiken `help` in plaats van de `Get-Help` cmdlet, omdat het een betere ervaring biedt en het minder is om te typen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-193">My recommendation is to use the `help` function instead of the `Get-Help` cmdlet since it provides a better experience and it's less to type.</span></span>

<span data-ttu-id="4c67d-194">Minder typen zijn echter niet altijd goed.</span><span class="sxs-lookup"><span data-stu-id="4c67d-194">Less typing isn't always a good thing, however.</span></span> <span data-ttu-id="4c67d-195">Als u uw opdrachten wilt opslaan als een script of ze wilt delen met iemand anders, moet u volledige cmdlet-en parameter namen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4c67d-195">If you're going to save your commands as a script or share them with someone else, be sure to use full cmdlet and parameter names.</span></span> <span data-ttu-id="4c67d-196">De volledige namen zijn zelf gedocumenteerd, waardoor ze gemakkelijker te begrijpen zijn.</span><span class="sxs-lookup"><span data-stu-id="4c67d-196">The full names are self-documenting, which makes them easier to understand.</span></span> <span data-ttu-id="4c67d-197">Denk aan de volgende persoon die uw opdrachten moet lezen en begrijpen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-197">Think about the next person that has to read and understand your commands.</span></span> <span data-ttu-id="4c67d-198">U kunt dit ook doen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-198">It could be you.</span></span> <span data-ttu-id="4c67d-199">Uw collega's en de toekomst zullen u bedanken.</span><span class="sxs-lookup"><span data-stu-id="4c67d-199">Your coworkers and future self will thank you.</span></span>

<span data-ttu-id="4c67d-200">Voer de volgende opdrachten uit in de Power shell-console op de computer met de Windows 10-test omgeving.</span><span class="sxs-lookup"><span data-stu-id="4c67d-200">Try running the following commands in the PowerShell console on your Windows 10 lab environment computer.</span></span>

```powershell
Get-Help -Name Get-Help -Full
help -Name Get-Help -Full
help Get-Help -Full
```

<span data-ttu-id="4c67d-201">Hebt u de verschillen in de uitvoer van de eerder vermelde opdrachten genoteerd toen u ze op de computer met Windows 10 lab-omgeving werd uitgevoerd?</span><span class="sxs-lookup"><span data-stu-id="4c67d-201">Did you notice any differences in the output from the previously listed commands when you ran them on your Windows 10 lab environment computer?</span></span>

<span data-ttu-id="4c67d-202">Er zijn geen verschillen tussen de laatste twee opties en retour neren de resultaten één pagina per keer.</span><span class="sxs-lookup"><span data-stu-id="4c67d-202">There aren't any differences other than the last two options return the results one page at a time.</span></span>
<span data-ttu-id="4c67d-203">De <kbd>spatie balk</kbd> wordt gebruikt om de volgende pagina met inhoud weer te geven wanneer u de `Help` functie gebruikt en <kbd>CTRL</kbd> + <kbd>C</kbd> opdrachten die in de Power shell-console worden uitgevoerd, worden geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="4c67d-203">The <kbd>spacebar</kbd> is used to display the next page of content when using the `Help` function and <kbd>Ctrl</kbd>+<kbd>C</kbd> cancels commands that are running in the PowerShell console.</span></span>

<span data-ttu-id="4c67d-204">In het eerste voor beeld wordt de `Get-Help` cmdlet gebruikt, de tweede gebruikt de `Help` functie en de derde para meter voor de **naam** weglaat wanneer u de `Help` functie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4c67d-204">The first example uses the `Get-Help` cmdlet, the second uses the `Help` function, and the third omits the **Name** parameter when using the `Help` function.</span></span> <span data-ttu-id="4c67d-205">**Name** is een positionele para meter en wordt positioneel in dit voor beeld gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4c67d-205">**Name** is a positional parameter and it's being used positionally in that example.</span></span> <span data-ttu-id="4c67d-206">Dit betekent dat de waarde kan worden opgegeven zonder de parameter naam op te geven, zolang de waarde zelf is opgegeven op de juiste positie.</span><span class="sxs-lookup"><span data-stu-id="4c67d-206">This means the value can be specified without specifying the parameter name, as long as the value itself is specified in the correct position.</span></span> <span data-ttu-id="4c67d-207">Hoe weet ik op welke positie de waarde moet worden opgegeven?</span><span class="sxs-lookup"><span data-stu-id="4c67d-207">How did I know what position to specify the value in?</span></span> <span data-ttu-id="4c67d-208">Lees de Help, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="4c67d-208">By reading the help as shown in the following example.</span></span>

```powershell
help Get-Help -Parameter Name
```

```Output
-Name <String>
    Gets help about the specified command or concept. Enter the name of a cmdlet, function,
    provider, script, or workflow, such as Get-Member, a conceptual article name, such as
    about_Objects, or an alias, such as ls. Wildcard characters are permitted in cmdlet and
    provider names, but you can't use wildcard characters to find the names of function help and
    script help articles.

    To get help for a script that isn't located in a path that's listed in the $env:Path
    environment variable, type the script's path and file name.

    If you enter the exact name of a help article, Get-Help displays the article contents.

    If you enter a word or word pattern that appears in several help article titles, Get-Help
    displays a list of the matching titles.

    If you enter a word that doesn't match any help article titles, Get-Help displays a list of
    articles that include that word in their contents.

    The names of conceptual articles, such as about_Objects, must be entered in English, even in
    non-English versions of PowerShell.

    Required?                    false
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  true
```

<span data-ttu-id="4c67d-209">In het vorige voor beeld is de **parameter** parameter met de Help-functie gebruikt om alleen informatie uit het Help-onderwerp voor de para meter **name** te retour neren.</span><span class="sxs-lookup"><span data-stu-id="4c67d-209">Notice that in the previous example, the **Parameter** parameter was used with the Help function to only return information from the help topic for the **Name** parameter.</span></span> <span data-ttu-id="4c67d-210">Dit is veel beknopter dan het hand matig gebruiken van een honderd pagina Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="4c67d-210">This is much more concise than trying to manually sift through what sometimes seems like a hundred page help topic.</span></span>

<span data-ttu-id="4c67d-211">Op basis van deze resultaten kunt u zien dat de para meter **name** positioneel is en moet u deze opgeven in positie nul (de eerste positie) wanneer u positioneel gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4c67d-211">Based on those results, you can see that the **Name** parameter is positional and must be specified in position zero (the first position) when used positionally.</span></span> <span data-ttu-id="4c67d-212">De volg orde waarin para meters worden opgegeven, is niet van belang als de parameter naam is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="4c67d-212">The order that parameters are specified in doesn't matter if the parameter name is specified.</span></span>

<span data-ttu-id="4c67d-213">Een andere belang rijke informatie is dat de para meter **name** verwacht dat het gegevens type voor de waarde een enkele teken reeks is, die wordt aangeduid door `<String>` .</span><span class="sxs-lookup"><span data-stu-id="4c67d-213">One other important piece of information is that the **Name** parameter expects the datatype for its value to be a single string, which is denoted by `<String>`.</span></span> <span data-ttu-id="4c67d-214">Als er meerdere teken reeksen zijn geaccepteerd, wordt het gegevens type weer gegeven als `<String[]>` .</span><span class="sxs-lookup"><span data-stu-id="4c67d-214">If it accepted multiple strings, the datatype would be listed as `<String[]>`.</span></span>

<span data-ttu-id="4c67d-215">Soms wilt u alleen het volledige Help-onderwerp voor een opdracht weer geven.</span><span class="sxs-lookup"><span data-stu-id="4c67d-215">Sometimes you simply don't want to display the entire help topic for a command.</span></span> <span data-ttu-id="4c67d-216">Er zijn een aantal andere para meters behalve de **volledige** waarde die kan worden opgegeven met `Get-Help` of `Help` .</span><span class="sxs-lookup"><span data-stu-id="4c67d-216">There are a number of other parameters besides **Full** that can be specified with `Get-Help` or `Help`.</span></span> <span data-ttu-id="4c67d-217">Voer de volgende opdrachten uit op de computer met de Windows 10-test omgeving:</span><span class="sxs-lookup"><span data-stu-id="4c67d-217">Try running the following commands on your Windows 10 lab environment computer:</span></span>

```powershell
Get-Help -Name Get-Command -Full
Get-Help -Name Get-Command -Detailed
Get-Help -Name Get-Command -Examples
Get-Help -Name Get-Command -Online
Get-Help -Name Get-Command -Parameter Noun
Get-Help -Name Get-Command -ShowWindow
```

<span data-ttu-id="4c67d-218">Ik gebruik normaal gesp roken `help <command name>` met de **volledige** of **online** -para meter.</span><span class="sxs-lookup"><span data-stu-id="4c67d-218">I typically use `help <command name>` with the **Full** or **Online** parameter.</span></span> <span data-ttu-id="4c67d-219">Als ik alleen geïnteresseerd in de voor beelden, gebruik ik de **voor beelden** van de para meter en als ik alleen in een specifieke para meter geïnteresseerd ben, gebruik **ik de para meter parameter.**</span><span class="sxs-lookup"><span data-stu-id="4c67d-219">If I'm only interested in the examples, I'll use the **Examples** parameter and if I'm only interested in a specific parameter, I'll use the **Parameter** parameter.</span></span> <span data-ttu-id="4c67d-220">De **ShowWindow** -para meter opent u het Help-onderwerp in een afzonderlijk Zoek venster dat kan worden geplaatst op een andere monitor als u meerdere monitors hebt.</span><span class="sxs-lookup"><span data-stu-id="4c67d-220">The **ShowWindow** parameter opens the help topic in a separate searchable window that can be placed on a different monitor if you have multiple monitors.</span></span> <span data-ttu-id="4c67d-221">Ik heb de **ShowWindow** -para meter vermeden, omdat er een bekende fout is waarbij het volledige Help-onderwerp niet wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c67d-221">I've avoided the **ShowWindow** parameter because there's a known bug where it doesn't display the entire help topic.</span></span>

<span data-ttu-id="4c67d-222">Als u hulp nodig hebt in een afzonderlijk venster, is het raadzaam om de para meter **online** te gebruiken of de **volledige** para meter te gebruiken en de resultaten door te sluizen naar `Out-GridView` , zoals in het volgende voor beeld wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c67d-222">If you want help in a separate window, my recommendation is to either use the **Online** parameter or use the **Full** parameter and pipe the results to `Out-GridView`, as shown in the following example.</span></span>

```powershell
help Get-Command -Full | Out-GridView
```

<span data-ttu-id="4c67d-223">Zowel de `Out-GridView` cmdlet als de **ShowWindow** -para meter van de `Get-Help` cmdlet vereisen een besturings systeem met een GUI (grafische gebruikers interface).</span><span class="sxs-lookup"><span data-stu-id="4c67d-223">Both the `Out-GridView` cmdlet and the **ShowWindow** parameter of the `Get-Help` cmdlet require an operating system with a GUI (Graphical User Interface).</span></span> <span data-ttu-id="4c67d-224">Er wordt een fout bericht gegenereerd als u probeert een van beide te gebruiken op een Windows-Server die is geïnstalleerd met behulp van de Server Core-installatie optie (no-GUI).</span><span class="sxs-lookup"><span data-stu-id="4c67d-224">They will generate an error message if you attempt to use either of them on Windows Server that's been installed using the server core (no-GUI) installation option.</span></span>

<span data-ttu-id="4c67d-225">Als u `Get-Help` wilt gebruiken om opdrachten te vinden, gebruikt u het `*` Joker teken asterisk () met de **naam** parameter.</span><span class="sxs-lookup"><span data-stu-id="4c67d-225">To use `Get-Help` to find commands, use the asterisk (`*`) wildcard character with the **Name** parameter.</span></span> <span data-ttu-id="4c67d-226">Geef een term op die u zoekt naar opdrachten als de waarde voor de para meter **name** , zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="4c67d-226">Specify a term that you're searching for commands on as the value for the **Name** parameter as shown in the following example.</span></span>

```powershell
help *process*
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
Exit-PSHostProcess                Cmdlet    Microsoft.PowerShell.Core Closes an intera...
Get-PSHostProcessInfo             Cmdlet    Microsoft.PowerShell.Core
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-AppvVirtualProcess            Function  AppvClient                ...
Start-AppvVirtualProcess          Function  AppvClient                ...
```

<span data-ttu-id="4c67d-227">In het vorige voor beeld `*` zijn de joker tekens niet vereist en wordt het weglaten van hetzelfde resultaat.</span><span class="sxs-lookup"><span data-stu-id="4c67d-227">In the previous example, the `*` wildcard characters are not required and omitting them produces the same result.</span></span> <span data-ttu-id="4c67d-228">`Get-Help` voegt automatisch de joker tekens achter de schermen toe.</span><span class="sxs-lookup"><span data-stu-id="4c67d-228">`Get-Help` automatically adds the wildcard characters behind the scenes.</span></span>

```powershell
help process
```

<span data-ttu-id="4c67d-229">Met de vorige opdracht worden dezelfde resultaten gegenereerd als het `*` Joker teken opgeven aan elk einde van het proces.</span><span class="sxs-lookup"><span data-stu-id="4c67d-229">The previous command produces the same results as specifying the `*` wildcard character on each end of process.</span></span>

<span data-ttu-id="4c67d-230">Ik wil ze liever toevoegen omdat dit de optie is die altijd consistent werkt.</span><span class="sxs-lookup"><span data-stu-id="4c67d-230">I prefer to add them since that's the option that always works consistently.</span></span> <span data-ttu-id="4c67d-231">Anders zijn ze vereist in bepaalde scenario's en niet op andere.</span><span class="sxs-lookup"><span data-stu-id="4c67d-231">Otherwise, they are required in certain scenarios and not others.</span></span> <span data-ttu-id="4c67d-232">Zodra u een Joker teken aan het midden van de waarde toevoegt, worden deze niet meer automatisch achter de schermen toegevoegd aan de waarde die u hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="4c67d-232">As soon as you add a wildcard character in the middle of the value, they're no longer automatically added behind the scenes to the value you specified.</span></span>

```powershell
help pr*cess
```

<span data-ttu-id="4c67d-233">Met deze opdracht worden geen resultaten geretourneerd, tenzij het `*` Joker teken wordt toegevoegd aan het begin, het einde of aan het begin en het einde van `pr*cess` .</span><span class="sxs-lookup"><span data-stu-id="4c67d-233">No results are returned by that command unless the `*` wildcard character is added to the beginning, end, or both the beginning and end of `pr*cess`.</span></span>

<span data-ttu-id="4c67d-234">Als de waarde die u hebt opgegeven begint met een streepje, wordt er een fout gegenereerd omdat Power shell deze als parameter naam interpreteert en er geen parameter naam bestaat voor de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c67d-234">If the value you specified begins with a dash, then an error is generated because PowerShell interprets it as a parameter name and no such parameter name exists for the `Get-Help` cmdlet.</span></span>

```powershell
help -process
```

<span data-ttu-id="4c67d-235">Als u wilt zoeken naar opdrachten die eindigen op `-process` , hoeft u alleen het `*` Joker teken aan het begin van de waarde toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-235">If what you're attempting to look for are commands that end with `-process`, you only need to add the `*` wildcard character to the beginning of the value.</span></span>

```powershell
help *-process
```

<span data-ttu-id="4c67d-236">Wanneer u Power shell-opdrachten zoekt met `Get-Help` , wilt u nog iets meer vague in plaats van te specifiek voor wat u zoekt.</span><span class="sxs-lookup"><span data-stu-id="4c67d-236">When searching for PowerShell commands with `Get-Help`, you want to be a little more vague instead of being too specific with what you're searching for.</span></span>

<span data-ttu-id="4c67d-237">Zoeken naar `process` eerder gevonden alleen opdrachten die zijn opgenomen `process` in de naam van de opdracht en alleen die resultaten retour neren.</span><span class="sxs-lookup"><span data-stu-id="4c67d-237">Searching for `process` earlier found only commands that contained `process` in the name of the command and returned only those results.</span></span> <span data-ttu-id="4c67d-238">Wanneer `Get-Help` wordt gebruikt om te zoeken, worden er geen `processes` overeenkomsten voor opdracht namen gevonden, zodat er een zoek opdracht wordt uitgevoerd in elk Help-onderwerp in Power shell op uw systeem en er gevonden overeenkomsten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4c67d-238">When `Get-Help` is used to search for `processes`, it doesn't find any matches for command names, so it performs a search of every help topic in PowerShell on your system and returns any matches it finds.</span></span> <span data-ttu-id="4c67d-239">Dit leidt ertoe dat er een enorm aantal resultaten wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4c67d-239">This causes it to return an enormous number of results.</span></span>

```powershell
Get-Help processes
```

```Output
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disconnect-PSSession              Cmdlet    Microsoft.PowerShell.Core Disconnects from...
Enter-PSHostProcess               Cmdlet    Microsoft.PowerShell.Core Connects to and ...
ForEach-Object                    Cmdlet    Microsoft.PowerShell.Core Performs an oper...
Get-PSSessionConfiguration        Cmdlet    Microsoft.PowerShell.Core Gets the registe...
New-PSTransportOption             Cmdlet    Microsoft.PowerShell.Core Creates an objec...
Out-Host                          Cmdlet    Microsoft.PowerShell.Core Sends output to ...
Where-Object                      Cmdlet    Microsoft.PowerShell.Core Selects objects ...
Clear-Variable                    Cmdlet    Microsoft.PowerShell.U... Deletes the valu...
Compare-Object                    Cmdlet    Microsoft.PowerShell.U... Compares two set...
Convert-String                    Cmdlet    Microsoft.PowerShell.U... Formats a string...
ConvertFrom-Csv                   Cmdlet    Microsoft.PowerShell.U... Converts object ...
ConvertTo-Html                    Cmdlet    Microsoft.PowerShell.U... Converts Microso...
ConvertTo-Xml                     Cmdlet    Microsoft.PowerShell.U... Creates an XML-b...
Debug-Runspace                    Cmdlet    Microsoft.PowerShell.U... Starts an intera...
Export-Csv                        Cmdlet    Microsoft.PowerShell.U... Converts objects...
Export-FormatData                 Cmdlet    Microsoft.PowerShell.U... Saves formatting...
Format-List                       Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Format-Table                      Cmdlet    Microsoft.PowerShell.U... Formats the outp...
Get-Random                        Cmdlet    Microsoft.PowerShell.U... Gets a random nu...
Get-Unique                        Cmdlet    Microsoft.PowerShell.U... Returns unique i...
Group-Object                      Cmdlet    Microsoft.PowerShell.U... Groups objects t...
Import-Clixml                     Cmdlet    Microsoft.PowerShell.U... Imports a CLIXML...
Import-Csv                        Cmdlet    Microsoft.PowerShell.U... Creates table-li...
Measure-Object                    Cmdlet    Microsoft.PowerShell.U... Calculates the n...
Out-File                          Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Out-GridView                      Cmdlet    Microsoft.PowerShell.U... Sends output to ...
Select-Object                     Cmdlet    Microsoft.PowerShell.U... Selects objects ...
Set-Variable                      Cmdlet    Microsoft.PowerShell.U... Sets the value o...
Sort-Object                       Cmdlet    Microsoft.PowerShell.U... Sorts objects by...
Tee-Object                        Cmdlet    Microsoft.PowerShell.U... Saves command ou...
Trace-Command                     Cmdlet    Microsoft.PowerShell.U... Configures and s...
Write-Output                      Cmdlet    Microsoft.PowerShell.U... Sends the specif...
Debug-Process                     Cmdlet    Microsoft.PowerShell.M... Debugs one or mo...
Get-Process                       Cmdlet    Microsoft.PowerShell.M... Gets the process...
Get-WmiObject                     Cmdlet    Microsoft.PowerShell.M... Gets instances o...
Start-Process                     Cmdlet    Microsoft.PowerShell.M... Starts one or mo...
Stop-Process                      Cmdlet    Microsoft.PowerShell.M... Stops one or mor...
Wait-Process                      Cmdlet    Microsoft.PowerShell.M... Waits for the pr...
Get-Counter                       Cmdlet    Microsoft.PowerShell.D... Gets performance...
Invoke-WSManAction                Cmdlet    Microsoft.WSMan.Manage... Invokes an actio...
Remove-WSManInstance              Cmdlet    Microsoft.WSMan.Manage... Deletes a manage...
Get-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Displays managem...
New-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Creates a new in...
Set-WSManInstance                 Cmdlet    Microsoft.WSMan.Manage... Modifies the man...
about_Arithmetic_Operators        HelpFile                            Describes the op...
about_Arrays                      HelpFile                            Describes arrays...
about_Debuggers                   HelpFile                            Describes the Wi...
about_Execution_Policies          HelpFile                            Describes the Wi...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Foreach                     HelpFile                            Describes a lang...
about_Functions                   HelpFile                            Describes how to...
about_Language_Keywords           HelpFile                            Describes the ke...
about_Methods                     HelpFile                            Describes how to...
about_Objects                     HelpFile                            Provides essenti...
about_Parallel                    HelpFile                            Describes the Pa...
about_Pipelines                   HelpFile                            Combining comman...
about_Preference_Variables        HelpFile                            Variables that c...
about_Remote                      HelpFile                            Describes how to...
about_Remote_Output               HelpFile                            Describes how to...
about_Sequence                    HelpFile                            Describes the Se...
about_Session_Configuration_Files HelpFile                            Describes sessio...
about_Variables                   HelpFile                            Describes how va...
about_Windows_PowerShell_5.0      HelpFile                            Describes new fe...
about_WQL                         HelpFile                            Describes WMI Qu...
about_WS-Management_Cmdlets       HelpFile                            Provides an over...
about_ForEach-Parallel            HelpFile                            Describes the Fo...
about_Parallel                    HelpFile                            Describes the Pa...
about_Sequence                    HelpFile                            Describes the Se...
```

<span data-ttu-id="4c67d-240">Gebruiken `Help` om te zoeken naar `process` geretourneerde 10 resultaten en om te zoeken naar `processes` geretourneerde 68-resultaten.</span><span class="sxs-lookup"><span data-stu-id="4c67d-240">Using `Help` to search for `process` returned 10 results and using it to search for `processes` returned 68 results.</span></span> <span data-ttu-id="4c67d-241">Als er slechts één resultaat wordt gevonden, wordt het Help-onderwerp zelf weer gegeven in plaats van een lijst met opdrachten.</span><span class="sxs-lookup"><span data-stu-id="4c67d-241">If only one result is found, the help topic itself will be displayed instead of a list of commands.</span></span>

```powershell
get-help *hotfix*
```

```Output
NAME
    Get-HotFix

SYNOPSIS
    Gets the hotfixes that have been applied to the local and remote computers.


SYNTAX
    Get-HotFix [-ComputerName <String[]>] [-Credential <PSCredential>] [-Description
    <String[]>] [<CommonParameters>]

    Get-HotFix [[-Id] <String[]>] [-ComputerName <String[]>] [-Credential
    <PSCredential>] [<CommonParameters>]


DESCRIPTION
    The Get-Hotfix cmdlet gets hotfixes (also called updates) that have been installed
    on either the local computer (or on specified remote computers) by Windows Update,
    Microsoft Update, or Windows Server Update Services; the cmdlet also gets hotfixes
    or updates that have been installed manually by users.


RELATED LINKS
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821586
    Win32_QuickFixEngineering http://go.microsoft.com/fwlink/?LinkID=145071
    Get-ComputerRestorePoint
    Add-Content

REMARKS
    To see the examples, type: "get-help Get-HotFix -examples".
    For more information, type: "get-help Get-HotFix -detailed".
    For technical information, type: "get-help Get-HotFix -full".
    For online help, type: "get-help Get-HotFix -online"
```

<span data-ttu-id="4c67d-242">Nu debunk u de mythe die `Help` in Power shell alleen opdrachten kan vinden die Help-onderwerpen bevatten.</span><span class="sxs-lookup"><span data-stu-id="4c67d-242">Now to debunk the myth that `Help` in PowerShell can only find commands that have help topics.</span></span>

```powershell
help *more*
```

```Output
NAME
    more

SYNTAX
    more [[-paths] <string[]>]


ALIASES
    None


REMARKS
    None
```

<span data-ttu-id="4c67d-243">U ziet in het vorige voor beeld dat `more` geen Help-onderwerp is, maar het `Help` systeem in Power shell kon het niet vinden.</span><span class="sxs-lookup"><span data-stu-id="4c67d-243">Notice in the previous example that `more` doesn't have a help topic, yet the `Help` system in PowerShell was able to find it.</span></span> <span data-ttu-id="4c67d-244">Er is slechts één overeenkomst gevonden die overeenkomt met de basis informatie over de syntaxis die wordt weer gegeven wanneer een opdracht geen Help-onderwerp heeft.</span><span class="sxs-lookup"><span data-stu-id="4c67d-244">It only found one match and returned the basic syntax information that you'll see when a command doesn't have a help topic.</span></span>

<span data-ttu-id="4c67d-245">Power shell bevat talloze conceptuele Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-245">PowerShell contains numerous conceptual (About) help topics.</span></span> <span data-ttu-id="4c67d-246">De volgende opdracht kan worden gebruikt om een lijst met alle Help-onderwerpen op uw **systeem te retour** neren.</span><span class="sxs-lookup"><span data-stu-id="4c67d-246">The following command can be used to return a list of all **About** help topics on your system.</span></span>

```powershell
help About_*
```

<span data-ttu-id="4c67d-247">Als u de resultaten beperkt tot één Help-onderwerp, wordt het werkelijke Help-onderwerp weer gegeven in plaats van een lijst te retour neren.</span><span class="sxs-lookup"><span data-stu-id="4c67d-247">Limiting the results to one single About help topic displays the actual help topic instead of returning a list.</span></span>

```powershell
help about_Updatable_Help
```

<span data-ttu-id="4c67d-248">Het Help-systeem in Power shell moet worden bijgewerkt zodat **de Help-** onderwerpen aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="4c67d-248">The help system in PowerShell has to be updated in order for the **About** help topics to be present.</span></span> <span data-ttu-id="4c67d-249">Als de eerste update van het Help-systeem op uw computer is mislukt, zijn de bestanden niet beschikbaar totdat de cmdlet is `Update-Help` uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4c67d-249">If for some reason the initial update of the help system failed on your computer, the files will not be available until the `Update-Help` cmdlet has been run successfully.</span></span>

## <a name="get-command"></a><span data-ttu-id="4c67d-250">Get-Command</span><span class="sxs-lookup"><span data-stu-id="4c67d-250">Get-Command</span></span>

<span data-ttu-id="4c67d-251">`Get-Command` is ontworpen om u te helpen bij het vinden van opdrachten.</span><span class="sxs-lookup"><span data-stu-id="4c67d-251">`Get-Command` is designed to help you locate commands.</span></span> <span data-ttu-id="4c67d-252">`Get-Command`Als u zonder para meters uitvoert, wordt een lijst met alle opdrachten op het systeem geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4c67d-252">Running `Get-Command` without any parameters returns a list of all the commands on your system.</span></span> <span data-ttu-id="4c67d-253">In het volgende voor beeld ziet u hoe u de `Get-Command` cmdlet gebruikt om te bepalen welke opdrachten bestaan voor het werken met processen:</span><span class="sxs-lookup"><span data-stu-id="4c67d-253">The following example demonstrates using the `Get-Command` cmdlet to determine what commands exist for working with processes:</span></span>

```powershell
Get-Command -Noun Process
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsof...
Cmdlet          Get-Process                                        3.1.0.0    Microsof...
Cmdlet          Start-Process                                      3.1.0.0    Microsof...
Cmdlet          Stop-Process                                       3.1.0.0    Microsof...
Cmdlet          Wait-Process                                       3.1.0.0    Microsof...
```

<span data-ttu-id="4c67d-254">In het vorige voor beeld waar `Get-Command` is uitgevoerd, wordt de para meter **zelfstandig** gebruikt en `Process` wordt deze opgegeven als de waarde voor de para meter **zelfstandig** .</span><span class="sxs-lookup"><span data-stu-id="4c67d-254">Notice in the previous example where `Get-Command` was run, the **Noun** parameter is used and `Process` is specified as the value for the **Noun** parameter.</span></span> <span data-ttu-id="4c67d-255">Wat als u niet weet hoe u de cmdlet moet gebruiken `Get-Command` ?</span><span class="sxs-lookup"><span data-stu-id="4c67d-255">What if you didn't know how to use the `Get-Command` cmdlet?</span></span> <span data-ttu-id="4c67d-256">U kunt gebruiken `Get-Help` om het Help-onderwerp voor weer te geven `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="4c67d-256">You could use `Get-Help` to display the help topic for `Get-Command`.</span></span>

<span data-ttu-id="4c67d-257">De para meters **name**, zelfstandig naam **woord** en **Verb** accepteren joker tekens.</span><span class="sxs-lookup"><span data-stu-id="4c67d-257">The **Name**, **Noun**, and **Verb** parameters accept wildcards.</span></span> <span data-ttu-id="4c67d-258">In het volgende voor beeld ziet u Joker tekens die worden gebruikt met de para meter **name** :</span><span class="sxs-lookup"><span data-stu-id="4c67d-258">The following example shows wildcards being used with the **Name** parameter:</span></span>

```Output
Get-Command -Name *service*
```

```powershell
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Function        Set-NetFirewallServiceFilter                       2.0.0.0    NetSecurity
Cmdlet          Get-Service                                        3.1.0.0    Microsof...
Cmdlet          New-Service                                        3.1.0.0    Microsof...
Cmdlet          New-WebServiceProxy                                3.1.0.0    Microsof...
Cmdlet          Restart-Service                                    3.1.0.0    Microsof...
Cmdlet          Resume-Service                                     3.1.0.0    Microsof...
Cmdlet          Set-Service                                        3.1.0.0    Microsof...
Cmdlet          Start-Service                                      3.1.0.0    Microsof...
Cmdlet          Stop-Service                                       3.1.0.0    Microsof...
Cmdlet          Suspend-Service                                    3.1.0.0    Microsof...
Application     AgentService.exe                                   10.0.14... C:\Windo...
Application     SensorDataService.exe                              10.0.14... C:\Windo...
Application     services.exe                                       10.0.14... C:\Windo...
Application     services.msc                                       0.0.0.0    C:\Windo...
Application     TieringEngineService.exe                           10.0.14... C:\Windo...
```

<span data-ttu-id="4c67d-259">Ik ben geen ventilator van het gebruik van joker tekens met de para meter **name** van `Get-Command` , omdat deze ook uitvoer bare bestanden retourneert die geen systeem eigen Power shell-opdrachten zijn.</span><span class="sxs-lookup"><span data-stu-id="4c67d-259">I'm not a fan of using wildcards with the **Name** parameter of `Get-Command` since it also returns executable files that are not native PowerShell commands.</span></span>

<span data-ttu-id="4c67d-260">Als u Joker tekens wilt gebruiken met de para meter **name** , raden we u aan de resultaten te beperken met de para meter **CommandType** .</span><span class="sxs-lookup"><span data-stu-id="4c67d-260">If you are going to use wildcard characters with the **Name** parameter, I recommend limiting the results with the **CommandType** parameter.</span></span>

```powershell
Get-Command -Name *service* -CommandType Cmdlet, Function, Alias
```

<span data-ttu-id="4c67d-261">Een betere optie is het gebruik van ofwel het **woord** of de **zelfstandig** para meter, omdat alleen Power shell-opdrachten beide werk woorden en zelfstandige naam woorden hebben.</span><span class="sxs-lookup"><span data-stu-id="4c67d-261">A better option is to use either the **Verb** or **Noun** parameter or both of them since only PowerShell commands have both verbs and nouns.</span></span>

<span data-ttu-id="4c67d-262">Is er iets mis met een Help-onderwerp?</span><span class="sxs-lookup"><span data-stu-id="4c67d-262">Found something wrong with a help topic?</span></span> <span data-ttu-id="4c67d-263">Het goede nieuws is de Help-onderwerpen voor Power shell zijn geopend en beschikbaar in de [Power shell-docs-][] opslag plaats op github.</span><span class="sxs-lookup"><span data-stu-id="4c67d-263">The good news is the help topics for PowerShell have been open-sourced and available in the [PowerShell-Docs][] repository on GitHub.</span></span> <span data-ttu-id="4c67d-264">Betaal het voorwaarts door niet alleen de onjuiste informatie voor uzelf te corrigeren, maar ook voor alle andere gebruikers.</span><span class="sxs-lookup"><span data-stu-id="4c67d-264">Pay it forward by not only fixing the incorrect information for yourself, but everyone else as well.</span></span> <span data-ttu-id="4c67d-265">U hoeft alleen de Power shell-documentatie opslagplaats op GitHub te splitsen, het Help-onderwerp bij te werken en een pull-aanvraag in te dienen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-265">Simply fork the PowerShell documentation repository on GitHub, update the help topic, and submit a pull request.</span></span>
<span data-ttu-id="4c67d-266">Zodra de pull-aanvraag is geaccepteerd, is de gecorrigeerde documentatie voor iedereen beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="4c67d-266">Once the pull request is accepted, the corrected documentation is available for everyone.</span></span>

## <a name="updating-help"></a><span data-ttu-id="4c67d-267">Help bijwerken</span><span class="sxs-lookup"><span data-stu-id="4c67d-267">Updating Help</span></span>

<span data-ttu-id="4c67d-268">De lokale versie van de Help-onderwerpen voor Power shell is eerder bijgewerkt met de eerste keer dat er een opdracht is aangevraagd.</span><span class="sxs-lookup"><span data-stu-id="4c67d-268">The local copy of the PowerShell help topics was previously updated the first-time help on a command was requested.</span></span> <span data-ttu-id="4c67d-269">Het is raadzaam om het Help-systeem regel matig bij te werken omdat er van tijd tot tijd updates kunnen zijn voor de Help-inhoud.</span><span class="sxs-lookup"><span data-stu-id="4c67d-269">It's recommended to periodically update the help system because there can be updates to the help content from time to time.</span></span> <span data-ttu-id="4c67d-270">De `Update-Help` cmdlet wordt gebruikt om de Help-onderwerpen bij te werken.</span><span class="sxs-lookup"><span data-stu-id="4c67d-270">The `Update-Help` cmdlet is used to update the help topics.</span></span>
<span data-ttu-id="4c67d-271">Hiervoor is Internet toegang vereist en u moet Power shell met verhoogde bevoegdheden uitvoeren als Administrator.</span><span class="sxs-lookup"><span data-stu-id="4c67d-271">It requires internet access by default and for you to be running PowerShell elevated as an administrator.</span></span>

```powershell
Update-Help
```

```Output
Update-Help : Failed to update Help for the module(s) 'BitsTransfer' with UI culture(s)
{en-US} : Unable to retrieve the HelpInfo XML file for UI culture en-US. Make sure the HelpInfoUri
property in the module manifest is valid or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : InvalidHelpInfoUri,Microsoft.PowerShell.Commands.UpdateHel
   pCommand

Update-Help : Failed to update Help for the module(s) 'NetworkControllerDiagnostics,
StorageReplica' with UI culture(s) {en-US} : Unable to retrieve the HelpInfo XML file
for UI culture en-US. Make sure the HelpInfoUri property in the module manifest is valid
or check your network connection and then try the command again.
At line:1 char:1
+ Update-Help
+
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.
   UpdateHelpCommand
```

<span data-ttu-id="4c67d-272">Enkele van de modules hebben fouten geretourneerd die niet ongebruikelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="4c67d-272">A couple of the modules returned errors, which is not uncommon.</span></span> <span data-ttu-id="4c67d-273">Als de computer geen toegang heeft tot internet, kunt u de `Save-Help` cmdlet gebruiken op een andere computer die toegang heeft tot internet om eerst de bijgewerkte Help-informatie op te slaan in een bestands share op uw netwerk en vervolgens de para meter **SourcePath** van gebruiken `Update-Help` om deze netwerk locatie op te geven voor de Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-273">If the machine didn't have internet access, you could use the `Save-Help` cmdlet on another machine that does have internet access to first save the updated help information to a file share on your network and then use the **SourcePath** parameter of `Update-Help` to specify this network location for the help topics.</span></span>

<span data-ttu-id="4c67d-274">Overweeg een geplande taak in te stellen of een logica toe te voegen aan uw profiel script in Power shell om regel matig de Help-inhoud op uw computer bij te werken.</span><span class="sxs-lookup"><span data-stu-id="4c67d-274">Consider setting up a scheduled task or adding some logic to your profile script in PowerShell to periodically update the help content on your computer.</span></span> <span data-ttu-id="4c67d-275">Profiel scripts worden besproken in een gepland hoofd stuk.</span><span class="sxs-lookup"><span data-stu-id="4c67d-275">Profile scripts will be discussed in an upcoming chapter.</span></span>

## <a name="summary"></a><span data-ttu-id="4c67d-276">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="4c67d-276">Summary</span></span>

<span data-ttu-id="4c67d-277">In dit hoofd stuk hebt u geleerd hoe u opdrachten kunt vinden met zowel `Get-Help` als `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="4c67d-277">In this chapter you've learned how to find commands with both `Get-Help` and `Get-Command`.</span></span> <span data-ttu-id="4c67d-278">U hebt geleerd hoe u het Help-systeem kunt gebruiken om de opdrachten te gebruiken wanneer u ze hebt gevonden.</span><span class="sxs-lookup"><span data-stu-id="4c67d-278">You've learned how to use the help system to figure out how to use commands once you find them.</span></span> <span data-ttu-id="4c67d-279">U hebt ook geleerd hoe u de inhoud van de Help-onderwerpen bijwerkt wanneer er updates beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="4c67d-279">You've also learned how to update the content of the help topics when updates are available.</span></span>

<span data-ttu-id="4c67d-280">Mijn uitdaging voor u is om een Power shell-opdracht per dag te leren.</span><span class="sxs-lookup"><span data-stu-id="4c67d-280">My challenge to you is to learn a PowerShell command a day.</span></span>

```powershell
Get-Command | Get-Random | Get-Help -Full
```

## <a name="review"></a><span data-ttu-id="4c67d-281">Beoordelen</span><span class="sxs-lookup"><span data-stu-id="4c67d-281">Review</span></span>

1. <span data-ttu-id="4c67d-282">Is de para meter **DisplayName** van `Get-Service` positioneel?</span><span class="sxs-lookup"><span data-stu-id="4c67d-282">Is the **DisplayName** parameter of `Get-Service` positional?</span></span>
1. <span data-ttu-id="4c67d-283">Hoeveel parameter sets heeft de `Get-Process` cmdlet?</span><span class="sxs-lookup"><span data-stu-id="4c67d-283">How many parameter sets does the `Get-Process` cmdlet have?</span></span>
1. <span data-ttu-id="4c67d-284">Welke Power shell-opdrachten bestaan er voor het werken met gebeurtenis logboeken?</span><span class="sxs-lookup"><span data-stu-id="4c67d-284">What PowerShell commands exist for working with event logs?</span></span>
1. <span data-ttu-id="4c67d-285">Wat is de Power shell-opdracht voor het retour neren van een lijst met Power shell-processen die worden uitgevoerd op uw computer?</span><span class="sxs-lookup"><span data-stu-id="4c67d-285">What is the PowerShell command for returning a list of PowerShell processes running on your computer?</span></span>
1. <span data-ttu-id="4c67d-286">Hoe werkt u de Help-inhoud van Power shell bij die op uw computer is opgeslagen?</span><span class="sxs-lookup"><span data-stu-id="4c67d-286">How do you update the PowerShell help content that's stored on your computer?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="4c67d-287">Aanbevolen documentatie</span><span class="sxs-lookup"><span data-stu-id="4c67d-287">Recommended Reading</span></span>

<span data-ttu-id="4c67d-288">Als u meer informatie wilt over de onderwerpen die in dit hoofd stuk worden behandeld, raden we u aan de volgende Help-onderwerpen voor Power shell te lezen.</span><span class="sxs-lookup"><span data-stu-id="4c67d-288">If you want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="4c67d-289">[Get-Help][]</span><span class="sxs-lookup"><span data-stu-id="4c67d-289">[Get-Help][]</span></span>
- <span data-ttu-id="4c67d-290">[Get-Command][]</span><span class="sxs-lookup"><span data-stu-id="4c67d-290">[Get-Command][]</span></span>
- <span data-ttu-id="4c67d-291">[Update-Help][]</span><span class="sxs-lookup"><span data-stu-id="4c67d-291">[Update-Help][]</span></span>
- <span data-ttu-id="4c67d-292">[Opslaan-Help][]</span><span class="sxs-lookup"><span data-stu-id="4c67d-292">[Save-Help][]</span></span>
- <span data-ttu-id="4c67d-293">[about_Updatable_Help][]</span><span class="sxs-lookup"><span data-stu-id="4c67d-293">[about_Updatable_Help][]</span></span>
- <span data-ttu-id="4c67d-294">[about_Command_Syntax][]</span><span class="sxs-lookup"><span data-stu-id="4c67d-294">[about_Command_Syntax][]</span></span>

<span data-ttu-id="4c67d-295">In het volgende hoofd stuk vindt u informatie over de `Get-Member` cmdlet en objecten, eigenschappen en methoden.</span><span class="sxs-lookup"><span data-stu-id="4c67d-295">In the next chapter, you'll learn about the `Get-Member` cmdlet as well as objects, properties, and methods.</span></span>

<!-- link references -->
[Get-Help]: /powershell/module/microsoft.powershell.core/get-help
[Get-Command]: /powershell/module/microsoft.powershell.core/get-command
[Update-Help]: /powershell/module/microsoft.powershell.core/update-help
[Opslaan-Help]: /powershell/module/microsoft.powershell.core/save-help
[Save-Help]: /powershell/module/microsoft.powershell.core/save-help
[about_Updatable_Help]: /powershell/module/microsoft.powershell.core/about/about_updatable_help
[about_Command_Syntax]: /powershell/module/microsoft.powershell.core/about/about_command_syntax
[PowerShell-Docs]: https://github.com/powershell/powershell
[Bijlage A]: appendix-a.md
[Appendix A]: appendix-a.md
