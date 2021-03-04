---
description: PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over PSReadLine
ms.openlocfilehash: ddc88dda3514e4279b6d91b023e26da88f645af7
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685215"
---
# <a name="psreadline"></a><span data-ttu-id="5b3ed-103">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-103">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="5b3ed-104">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-104">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="5b3ed-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="5b3ed-105">Short Description</span></span>

<span data-ttu-id="5b3ed-106">PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-106">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="5b3ed-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="5b3ed-107">Long Description</span></span>

<span data-ttu-id="5b3ed-108">PSReadLine 2,2 biedt een krachtige opdracht regel voor het bewerken van de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-108">PSReadLine 2.2 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="5b3ed-109">De oplossing biedt het volgende:</span><span class="sxs-lookup"><span data-stu-id="5b3ed-109">It provides:</span></span>

- <span data-ttu-id="5b3ed-110">Syntaxis kleur van de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="5b3ed-110">Syntax coloring of the command line</span></span>
- <span data-ttu-id="5b3ed-111">Een visuele indicatie van syntaxis fouten</span><span class="sxs-lookup"><span data-stu-id="5b3ed-111">A visual indication of syntax errors</span></span>
- <span data-ttu-id="5b3ed-112">Een betere ervaring met meerdere regels (zowel bewerkingen als geschiedenis)</span><span class="sxs-lookup"><span data-stu-id="5b3ed-112">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="5b3ed-113">Aanpas bare sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="5b3ed-113">Customizable key bindings</span></span>
- <span data-ttu-id="5b3ed-114">Cmd-en emacs-modi</span><span class="sxs-lookup"><span data-stu-id="5b3ed-114">Cmd and Emacs modes</span></span>
- <span data-ttu-id="5b3ed-115">Veel configuratie opties</span><span class="sxs-lookup"><span data-stu-id="5b3ed-115">Many configuration options</span></span>
- <span data-ttu-id="5b3ed-116">Bash-stijl voltooiing (optioneel in CMD-modus, standaard in Emacs-modus)</span><span class="sxs-lookup"><span data-stu-id="5b3ed-116">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="5b3ed-117">Emacs Yank/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="5b3ed-117">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="5b3ed-118">"Woord" verplaatsing en afsluiten op basis van Power shell-tokens</span><span class="sxs-lookup"><span data-stu-id="5b3ed-118">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="5b3ed-119">Voorspellende IntelliSense</span><span class="sxs-lookup"><span data-stu-id="5b3ed-119">Predictive IntelliSense</span></span>

<span data-ttu-id="5b3ed-120">PSReadLine 2.2.0 heeft twee nieuwe voorspellende IntelliSense-functies toegevoegd:</span><span class="sxs-lookup"><span data-stu-id="5b3ed-120">PSReadLine 2.2.0 added two new predictive IntelliSense features:</span></span>

- <span data-ttu-id="5b3ed-121">De para meter **PredictionViewStyle** is toegevoegd zodat de nieuwe kan worden geselecteerd `ListView` .</span><span class="sxs-lookup"><span data-stu-id="5b3ed-121">Added the **PredictionViewStyle** parameter to allow for the selection of the new `ListView`.</span></span>
- <span data-ttu-id="5b3ed-122">Verbonden PSReadLine met de `CommandPrediction` api's die in PS 7,1 zijn geïntroduceerd om een gebruiker toe te staan een Voorspellings module te importeren waarmee de suggesties van een aangepaste bron kunnen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-122">Connected PSReadLine to the `CommandPrediction` APIs introduced in PS 7.1 to allow a user can import a predictor module that can render the suggestions from a custom source.</span></span>

<span data-ttu-id="5b3ed-123">PSReadLine vereist Power Shell 3,0 of nieuwer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-123">PSReadLine requires PowerShell 3.0, or newer.</span></span> <span data-ttu-id="5b3ed-124">PSReadLine werkt met de standaard console-host, Visual Studio code en Windows-Terminal.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-124">PSReadLine works with default console host, Visual Studio Code, and Window Terminal.</span></span> <span data-ttu-id="5b3ed-125">Het werkt niet in Power shell ISE.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-125">It does not work in PowerShell ISE.</span></span>

<span data-ttu-id="5b3ed-126">PSReadLine 2.2.0 wordt geleverd met Power shell 7,2 en wordt ondersteund in alle ondersteunde versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-126">PSReadLine 2.2.0 ships with PowerShell 7.2 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="5b3ed-127">Het is beschikbaar om te installeren via de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-127">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="5b3ed-128">Voer de volgende opdracht uit om PSReadLine 2.2.0 in een ondersteunde versie van Power shell te installeren.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-128">To install PSReadLine 2.2.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> <span data-ttu-id="5b3ed-129">Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-129">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="5b3ed-130">Op dit moment werkt PSReadLine niet goed met scherm lezers.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-130">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="5b3ed-131">De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-131">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="5b3ed-132">U kunt de module hand matig laden, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-132">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="5b3ed-133">Voorspellende IntelliSense</span><span class="sxs-lookup"><span data-stu-id="5b3ed-133">Predictive IntelliSense</span></span>

<span data-ttu-id="5b3ed-134">Voorspellende IntelliSense is een aanvulling op het concept van tabblad voltooiing waarmee de gebruiker wordt geholpen bij het volt ooien van opdrachten.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-134">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="5b3ed-135">Hiermee kunnen gebruikers volledige opdrachten detecteren, bewerken en uitvoeren op basis van overeenkomende voor spellingen van de geschiedenis van de gebruiker en aanvullende toepassingsspecifieke invoeg toepassingen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-135">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="5b3ed-136">Voorspellende IntelliSense inschakelen</span><span class="sxs-lookup"><span data-stu-id="5b3ed-136">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="5b3ed-137">Voorspellende IntelliSense is standaard uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-137">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="5b3ed-138">Als u voor spellingen wilt inschakelen, voert u gewoon de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="5b3ed-138">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="5b3ed-139">De para meter **PredictionSource** kan ook invoeg toepassingen accepteren voor specifieke en aangepaste vereisten voor het domein.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-139">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="5b3ed-140">Als u voorspellende IntelliSense wilt uitschakelen, voert u de volgende handelingen uit:</span><span class="sxs-lookup"><span data-stu-id="5b3ed-140">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="5b3ed-141">De volgende functies zijn beschikbaar in de klasse **[micro soft. Power shell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-141">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="5b3ed-142">Basis bewerkings functies</span><span class="sxs-lookup"><span data-stu-id="5b3ed-142">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="5b3ed-143">Afbreken</span><span class="sxs-lookup"><span data-stu-id="5b3ed-143">Abort</span></span>

<span data-ttu-id="5b3ed-144">De huidige actie afbreken, bijvoorbeeld een incrementele geschiedenis zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-144">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="5b3ed-145">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-145">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="5b3ed-146">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="5b3ed-146">AcceptAndGetNext</span></span>

<span data-ttu-id="5b3ed-147">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-147">Attempt to execute the current input.</span></span> <span data-ttu-id="5b3ed-148">Als deze kan worden uitgevoerd (zoals AcceptLine), kunt u het volgende item uit de geschiedenis intrekken de volgende keer dat ReadLine wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-148">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="5b3ed-149">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-149">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="5b3ed-150">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-150">AcceptLine</span></span>

<span data-ttu-id="5b3ed-151">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-151">Attempt to execute the current input.</span></span> <span data-ttu-id="5b3ed-152">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-152">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="5b3ed-153">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-153">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="5b3ed-154">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-154">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="5b3ed-155">VI Invoeg modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-155">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="5b3ed-156">AddLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-156">AddLine</span></span>

<span data-ttu-id="5b3ed-157">De vervolg prompt wordt weer gegeven op de volgende regel en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-157">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="5b3ed-158">Dit is handig om invoer in meerdere regels als één opdracht in te voeren, zelfs wanneer één regel volledig wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-158">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="5b3ed-159">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-159">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="5b3ed-160">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-160">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="5b3ed-161">VI Invoeg modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-161">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="5b3ed-162">VI-opdracht modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-162">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="5b3ed-163">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-163">BackwardDeleteChar</span></span>

<span data-ttu-id="5b3ed-164">Verwijder het teken voor de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-164">Delete the character before the cursor.</span></span>

- <span data-ttu-id="5b3ed-165">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-165">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="5b3ed-166">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-166">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="5b3ed-167">VI Invoeg modus: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-167">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="5b3ed-168">VI-opdracht modus: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-168">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteinput"></a><span data-ttu-id="5b3ed-169">BackwardDeleteInput</span><span class="sxs-lookup"><span data-stu-id="5b3ed-169">BackwardDeleteInput</span></span>

<span data-ttu-id="5b3ed-170">Net als BackwardKillInput: verwijdert tekst van het punt naar het begin van de invoer, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-170">Like BackwardKillInput - deletes text from the point to the start of the input, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="5b3ed-171">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-171">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="5b3ed-172">VI Invoeg modus: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-172">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="5b3ed-173">VI-opdracht modus: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-173">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="5b3ed-174">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-174">BackwardDeleteLine</span></span>

<span data-ttu-id="5b3ed-175">Net als BackwardKillLine: verwijdert tekst van het punt naar het begin van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-175">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="5b3ed-176">VI-opdracht modus: `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-176">Vi command mode: `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="5b3ed-177">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-177">BackwardDeleteWord</span></span>

<span data-ttu-id="5b3ed-178">Hiermee verwijdert u het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-178">Deletes the previous word.</span></span>

- <span data-ttu-id="5b3ed-179">VI-opdracht modus: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-179">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillinput"></a><span data-ttu-id="5b3ed-180">BackwardKillInput</span><span class="sxs-lookup"><span data-stu-id="5b3ed-180">BackwardKillInput</span></span>

<span data-ttu-id="5b3ed-181">Hiermee wordt de tekst van het begin van de invoer naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-181">Clear the text from the start of the input to the cursor.</span></span> <span data-ttu-id="5b3ed-182">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-182">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="5b3ed-183">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-183">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="5b3ed-184">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-184">BackwardKillLine</span></span>

<span data-ttu-id="5b3ed-185">Hiermee wordt de tekst van het begin van de huidige logische lijn naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-185">Clear the text from the start of the current logical line to the cursor.</span></span> <span data-ttu-id="5b3ed-186">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-186">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="5b3ed-187">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-187">Function is unbound.</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="5b3ed-188">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-188">BackwardKillWord</span></span>

<span data-ttu-id="5b3ed-189">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-189">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="5b3ed-190">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-190">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="5b3ed-191">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-191">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="5b3ed-192">Cmd: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-192">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="5b3ed-193">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-193">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="5b3ed-194">VI Invoeg modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-194">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="5b3ed-195">VI-opdracht modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-195">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="5b3ed-196">CancelLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-196">CancelLine</span></span>

<span data-ttu-id="5b3ed-197">De huidige invoer annuleren, waardoor de invoer op het scherm wordt weer gegeven, maar terugkeert naar de host, zodat de prompt opnieuw wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-197">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="5b3ed-198">VI Invoeg modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-198">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="5b3ed-199">VI-opdracht modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-199">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="5b3ed-200">Kopiëren</span><span class="sxs-lookup"><span data-stu-id="5b3ed-200">Copy</span></span>

<span data-ttu-id="5b3ed-201">Kopieer de geselecteerde regio naar het klem bord van het systeem.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-201">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="5b3ed-202">Als er geen regio is geselecteerd, kopieert u de hele regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-202">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="5b3ed-203">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-203">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="5b3ed-204">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-204">CopyOrCancelLine</span></span>

<span data-ttu-id="5b3ed-205">Als tekst is geselecteerd, kopieert u deze naar het klem bord. anders annuleert u de regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-205">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="5b3ed-206">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-206">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="5b3ed-207">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-207">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="5b3ed-208">Knippen</span><span class="sxs-lookup"><span data-stu-id="5b3ed-208">Cut</span></span>

<span data-ttu-id="5b3ed-209">Geselecteerde regio verwijderen Verwijderde tekst in het systeem Klembord plaatsen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-209">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="5b3ed-210">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-210">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="5b3ed-211">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-211">DeleteChar</span></span>

<span data-ttu-id="5b3ed-212">Verwijder het teken onder de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-212">Delete the character under the cursor.</span></span>

- <span data-ttu-id="5b3ed-213">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-213">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="5b3ed-214">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-214">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="5b3ed-215">VI Invoeg modus: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-215">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="5b3ed-216">VI-opdracht modus: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-216">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="5b3ed-217">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="5b3ed-217">DeleteCharOrExit</span></span>

<span data-ttu-id="5b3ed-218">Verwijder het teken onder de cursor of als de regel leeg is, sluit u het proces.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-218">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="5b3ed-219">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-219">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="5b3ed-220">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="5b3ed-220">DeleteEndOfBuffer</span></span>

<span data-ttu-id="5b3ed-221">Hiermee verwijdert u aan het einde van de buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-221">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="5b3ed-222">VI-opdracht modus: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-222">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="5b3ed-223">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-223">DeleteEndOfWord</span></span>

<span data-ttu-id="5b3ed-224">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-224">Delete to the end of the word.</span></span>

- <span data-ttu-id="5b3ed-225">VI-opdracht modus: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-225">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="5b3ed-226">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-226">DeleteLine</span></span>

<span data-ttu-id="5b3ed-227">Hiermee verwijdert u de huidige logische lijn van een buffer voor meerdere regels, waarbij u ongedaan maken inschakelt.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-227">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="5b3ed-228">VI-opdracht modus: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-228">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="5b3ed-229">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="5b3ed-229">DeletePreviousLines</span></span>

<span data-ttu-id="5b3ed-230">Hiermee verwijdert u de vorige aangevraagde logische regels en de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-230">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="5b3ed-231">VI-opdracht modus: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-231">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="5b3ed-232">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="5b3ed-232">DeleteRelativeLines</span></span>

<span data-ttu-id="5b3ed-233">Verwijdert uit het begin van de buffer naar de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-233">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="5b3ed-234">De meeste MS-DOS-opdrachten `<d,g,g>` kunnen worden voorafgegaan door een numeriek argument waarmee een absoluut regel nummer wordt opgegeven, samen met het huidige regel nummer, een bereik aan regels maken dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-234">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="5b3ed-235">Als u niets opgeeft, wordt het numerieke argument standaard ingesteld op 1, dat verwijst naar de eerste logische lijn in een buffer met meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-235">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="5b3ed-236">Het werkelijke aantal regels dat uit de meerregelige moet worden verwijderd, wordt berekend als het verschil tussen het huidige logische regel nummer en het opgegeven numerieke argument. Dit kan dus negatief zijn.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-236">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="5b3ed-237">Daarom is het _relatieve_ deel van de methode naam.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-237">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="5b3ed-238">VI-opdracht modus: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-238">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="5b3ed-239">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="5b3ed-239">DeleteNextLines</span></span>

<span data-ttu-id="5b3ed-240">Hiermee verwijdert u de huidige logische lijn en de volgende aangevraagde logische regels in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-240">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="5b3ed-241">VI-opdracht modus: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-241">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="5b3ed-242">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-242">DeleteLineToFirstChar</span></span>

<span data-ttu-id="5b3ed-243">Verwijdert uit het eerste niet-lege teken van de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-243">Deletes from the first non-blank character of the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="5b3ed-244">VI-opdracht modus: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-244">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="5b3ed-245">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="5b3ed-245">DeleteToEnd</span></span>

<span data-ttu-id="5b3ed-246">Verwijderen tot aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-246">Delete to the end of the line.</span></span>

- <span data-ttu-id="5b3ed-247">VI-opdracht modus: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-247">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="5b3ed-248">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-248">DeleteWord</span></span>

<span data-ttu-id="5b3ed-249">Verwijder het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-249">Delete the next word.</span></span>

- <span data-ttu-id="5b3ed-250">VI-opdracht modus: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-250">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteinput"></a><span data-ttu-id="5b3ed-251">ForwardDeleteInput</span><span class="sxs-lookup"><span data-stu-id="5b3ed-251">ForwardDeleteInput</span></span>

<span data-ttu-id="5b3ed-252">Net als KillLine: verwijdert tekst van het punt naar het einde van de invoer, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-252">Like KillLine - deletes text from the point to the end of the input, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="5b3ed-253">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-253">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="5b3ed-254">VI Invoeg modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-254">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="5b3ed-255">VI-opdracht modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-255">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="5b3ed-256">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-256">ForwardDeleteLine</span></span>

<span data-ttu-id="5b3ed-257">Hiermee wordt tekst van het punt naar het einde van de huidige logische lijn verwijderd, maar wordt de verwijderde tekst niet in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-257">Deletes text from the point to the end of the current logical line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="5b3ed-258">Functie is niet-afhankelijk</span><span class="sxs-lookup"><span data-stu-id="5b3ed-258">Function is unbound</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="5b3ed-259">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="5b3ed-259">InsertLineAbove</span></span>

<span data-ttu-id="5b3ed-260">Er wordt een nieuwe lege regel gemaakt op de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-260">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="5b3ed-261">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-261">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="5b3ed-262">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-262">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="5b3ed-263">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="5b3ed-263">InsertLineBelow</span></span>

<span data-ttu-id="5b3ed-264">Er wordt een nieuwe lege regel gemaakt onder de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-264">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="5b3ed-265">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-265">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="5b3ed-266">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-266">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="5b3ed-267">InvertCase</span><span class="sxs-lookup"><span data-stu-id="5b3ed-267">InvertCase</span></span>

<span data-ttu-id="5b3ed-268">Het hoofdletter gebruik van het huidige teken omkeren en verplaatsen naar het volgende.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-268">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="5b3ed-269">VI-opdracht modus: `<~>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-269">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="5b3ed-270">KillLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-270">KillLine</span></span>

<span data-ttu-id="5b3ed-271">De invoer wissen van de cursor tot het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-271">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="5b3ed-272">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-272">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="5b3ed-273">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-273">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="5b3ed-274">KillRegion</span><span class="sxs-lookup"><span data-stu-id="5b3ed-274">KillRegion</span></span>

<span data-ttu-id="5b3ed-275">Beëindig de tekst tussen de cursor en de markering.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-275">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="5b3ed-276">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-276">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="5b3ed-277">KillWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-277">KillWord</span></span>

<span data-ttu-id="5b3ed-278">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-278">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="5b3ed-279">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-279">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="5b3ed-280">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-280">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="5b3ed-281">Cmd: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-281">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="5b3ed-282">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-282">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="5b3ed-283">VI Invoeg modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-283">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="5b3ed-284">VI-opdracht modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-284">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="5b3ed-285">Plakken</span><span class="sxs-lookup"><span data-stu-id="5b3ed-285">Paste</span></span>

<span data-ttu-id="5b3ed-286">Tekst van het klem bord van het systeem plakken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-286">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="5b3ed-287">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-287">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="5b3ed-288">VI Invoeg modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-288">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="5b3ed-289">VI-opdracht modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-289">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b3ed-290">Wanneer u de functie **Paste** gebruikt, wordt de volledige inhoud van de Klembord buffer geplakt in de invoer buffer van PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-290">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="5b3ed-291">De invoer buffer wordt vervolgens door gegeven aan de Power shell-parser.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-291">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="5b3ed-292">Invoer die met de **rechter muisknop op** de plak methode van de console toepassing wordt geplakt, wordt met één teken per keer naar de invoer buffer gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-292">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="5b3ed-293">De invoer buffer wordt door gegeven aan de parser wanneer een teken voor een nieuwe regel wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-293">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="5b3ed-294">Daarom wordt de invoer één regel tegelijk geparseerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-294">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="5b3ed-295">Het verschil tussen plak methoden resulteert in een ander uitvoerings gedrag.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-295">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="5b3ed-296">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="5b3ed-296">PasteAfter</span></span>

<span data-ttu-id="5b3ed-297">Plak het klem bord na de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-297">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="5b3ed-298">VI-opdracht modus: `<p>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-298">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="5b3ed-299">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="5b3ed-299">PasteBefore</span></span>

<span data-ttu-id="5b3ed-300">Plak het klem bord vóór de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-300">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="5b3ed-301">VI-opdracht modus: `<P>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-301">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="5b3ed-302">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="5b3ed-302">PrependAndAccept</span></span>

<span data-ttu-id="5b3ed-303">Laten voorafgaan door een ' # ' en accepteer de regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-303">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="5b3ed-304">VI-opdracht modus: `<#>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-304">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="5b3ed-305">Opnieuw uitvoeren</span><span class="sxs-lookup"><span data-stu-id="5b3ed-305">Redo</span></span>

<span data-ttu-id="5b3ed-306">Undo ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-306">Undo an undo.</span></span>

- <span data-ttu-id="5b3ed-307">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-307">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="5b3ed-308">VI Invoeg modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-308">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="5b3ed-309">VI-opdracht modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-309">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="5b3ed-310">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="5b3ed-310">RepeatLastCommand</span></span>

<span data-ttu-id="5b3ed-311">Herhaal de laatste tekst wijziging.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-311">Repeat the last text modification.</span></span>

- <span data-ttu-id="5b3ed-312">VI-opdracht modus: `<.>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-312">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="5b3ed-313">RevertLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-313">RevertLine</span></span>

<span data-ttu-id="5b3ed-314">Hiermee wordt alle invoer teruggezet naar de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-314">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="5b3ed-315">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-315">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="5b3ed-316">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-316">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="5b3ed-317">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-317">ShellBackwardKillWord</span></span>

<span data-ttu-id="5b3ed-318">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-318">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="5b3ed-319">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-319">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="5b3ed-320">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-320">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="5b3ed-321">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-321">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="5b3ed-322">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-322">ShellKillWord</span></span>

<span data-ttu-id="5b3ed-323">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-323">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="5b3ed-324">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-324">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="5b3ed-325">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-325">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="5b3ed-326">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-326">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="5b3ed-327">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="5b3ed-327">SwapCharacters</span></span>

<span data-ttu-id="5b3ed-328">Het huidige teken en de eerste vervangen door wisselen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-328">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="5b3ed-329">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-329">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="5b3ed-330">VI Invoeg modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-330">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="5b3ed-331">VI-opdracht modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-331">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="5b3ed-332">Ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="5b3ed-332">Undo</span></span>

<span data-ttu-id="5b3ed-333">Een vorige bewerking ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-333">Undo a previous edit.</span></span>

- <span data-ttu-id="5b3ed-334">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-334">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="5b3ed-335">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-335">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="5b3ed-336">VI Invoeg modus: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-336">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="5b3ed-337">VI-opdracht modus: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-337">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="5b3ed-338">UndoAll</span><span class="sxs-lookup"><span data-stu-id="5b3ed-338">UndoAll</span></span>

<span data-ttu-id="5b3ed-339">Alle vorige bewerkingen voor de regel ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-339">Undo all previous edits for line.</span></span>

- <span data-ttu-id="5b3ed-340">VI-opdracht modus: `<U>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-340">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="5b3ed-341">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="5b3ed-341">UnixWordRubout</span></span>

<span data-ttu-id="5b3ed-342">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-342">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="5b3ed-343">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-343">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="5b3ed-344">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-344">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="5b3ed-345">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-345">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="5b3ed-346">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-346">ValidateAndAcceptLine</span></span>

<span data-ttu-id="5b3ed-347">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-347">Attempt to execute the current input.</span></span> <span data-ttu-id="5b3ed-348">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-348">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="5b3ed-349">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-349">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="5b3ed-350">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-350">ViAcceptLine</span></span>

<span data-ttu-id="5b3ed-351">Accepteer de regel en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-351">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="5b3ed-352">VI-opdracht modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-352">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="5b3ed-353">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="5b3ed-353">ViAcceptLineOrExit</span></span>

<span data-ttu-id="5b3ed-354">Als DeleteCharOrExit in de Emacs-modus, maar wel in plaats van een teken te verwijderen, accepteert u de regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-354">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="5b3ed-355">VI Invoeg modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-355">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="5b3ed-356">VI-opdracht modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-356">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="5b3ed-357">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-357">ViAppendLine</span></span>

<span data-ttu-id="5b3ed-358">Er wordt een nieuwe regel ingevoegd onder de huidige regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-358">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="5b3ed-359">VI-opdracht modus: `<o>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-359">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="5b3ed-360">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="5b3ed-360">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="5b3ed-361">Hiermee verwijdert u het vorige woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-361">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="5b3ed-362">VI-opdracht modus: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-362">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="5b3ed-363">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="5b3ed-363">ViBackwardGlob</span></span>

<span data-ttu-id="5b3ed-364">Verplaatst de cursor terug naar het begin van het vorige woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-364">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="5b3ed-365">VI-opdracht modus: `<B>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-365">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="5b3ed-366">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="5b3ed-366">ViDeleteBrace</span></span>

<span data-ttu-id="5b3ed-367">Zoek de accolade, het haakje sluiten of de vier Kante haken en verwijder alle inhoud binnen, inclusief de accolade.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-367">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="5b3ed-368">VI-opdracht modus: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-368">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="5b3ed-369">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="5b3ed-369">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="5b3ed-370">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-370">Delete to the end of the word.</span></span>

- <span data-ttu-id="5b3ed-371">VI-opdracht modus: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-371">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="5b3ed-372">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="5b3ed-372">ViDeleteGlob</span></span>

<span data-ttu-id="5b3ed-373">De volgende Globs verwijderen (door witruimte gescheiden woord).</span><span class="sxs-lookup"><span data-stu-id="5b3ed-373">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="5b3ed-374">VI-opdracht modus: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-374">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="5b3ed-375">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-375">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="5b3ed-376">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-376">Deletes until given character.</span></span>

- <span data-ttu-id="5b3ed-377">VI-opdracht modus: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-377">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="5b3ed-378">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="5b3ed-378">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="5b3ed-379">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-379">Deletes until given character.</span></span>

- <span data-ttu-id="5b3ed-380">VI-opdracht modus: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-380">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="5b3ed-381">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-381">ViDeleteToChar</span></span>

<span data-ttu-id="5b3ed-382">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-382">Deletes until given character.</span></span>

- <span data-ttu-id="5b3ed-383">VI-opdracht modus: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-383">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="5b3ed-384">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="5b3ed-384">ViDeleteToCharBackward</span></span>

<span data-ttu-id="5b3ed-385">Hiermee verwijdert u achterwaartse tekens tot aan het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-385">Deletes backwards until given character.</span></span>

- <span data-ttu-id="5b3ed-386">VI-opdracht modus: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-386">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="5b3ed-387">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="5b3ed-387">ViInsertAtBegining</span></span>

<span data-ttu-id="5b3ed-388">Schakel over naar de Invoeg modus en plaats de cursor aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-388">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="5b3ed-389">VI-opdracht modus: `<I>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-389">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="5b3ed-390">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="5b3ed-390">ViInsertAtEnd</span></span>

<span data-ttu-id="5b3ed-391">Schakel over naar de Invoeg modus en plaats de cursor aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-391">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="5b3ed-392">VI-opdracht modus: `<A>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-392">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="5b3ed-393">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-393">ViInsertLine</span></span>

<span data-ttu-id="5b3ed-394">Boven de huidige regel wordt een nieuwe regel ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-394">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="5b3ed-395">VI-opdracht modus: `<O>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-395">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="5b3ed-396">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="5b3ed-396">ViInsertWithAppend</span></span>

<span data-ttu-id="5b3ed-397">Toevoegen vanaf de huidige regel positie.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-397">Append from the current line position.</span></span>

- <span data-ttu-id="5b3ed-398">VI-opdracht modus: `<a>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-398">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="5b3ed-399">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="5b3ed-399">ViInsertWithDelete</span></span>

<span data-ttu-id="5b3ed-400">Verwijder het huidige teken en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-400">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="5b3ed-401">VI-opdracht modus: `<s>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-401">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="5b3ed-402">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="5b3ed-402">ViJoinLines</span></span>

<span data-ttu-id="5b3ed-403">De huidige regel en de volgende regel worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-403">Joins the current line and the next line.</span></span>

- <span data-ttu-id="5b3ed-404">VI-opdracht modus: `<J>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-404">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="5b3ed-405">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-405">ViReplaceLine</span></span>

<span data-ttu-id="5b3ed-406">De volledige opdracht regel wissen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-406">Erase the entire command line.</span></span>

- <span data-ttu-id="5b3ed-407">VI-opdracht modus: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-407">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="5b3ed-408">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-408">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="5b3ed-409">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-409">Replaces until given character.</span></span>

- <span data-ttu-id="5b3ed-410">VI-opdracht modus: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-410">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="5b3ed-411">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="5b3ed-411">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="5b3ed-412">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-412">Replaces until given character.</span></span>

- <span data-ttu-id="5b3ed-413">VI-opdracht modus: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-413">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="5b3ed-414">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-414">ViReplaceToChar</span></span>

<span data-ttu-id="5b3ed-415">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-415">Deletes until given character.</span></span>

- <span data-ttu-id="5b3ed-416">VI-opdracht modus: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-416">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="5b3ed-417">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="5b3ed-417">ViReplaceToCharBackward</span></span>

<span data-ttu-id="5b3ed-418">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-418">Replaces until given character.</span></span>

- <span data-ttu-id="5b3ed-419">VI-opdracht modus: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-419">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="5b3ed-420">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-420">ViYankBeginningOfLine</span></span>

<span data-ttu-id="5b3ed-421">Yank vanaf het begin van de buffer naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-421">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="5b3ed-422">VI-opdracht modus: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-422">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="5b3ed-423">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="5b3ed-423">ViYankEndOfGlob</span></span>

<span data-ttu-id="5b3ed-424">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="5b3ed-424">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="5b3ed-425">VI-opdracht modus: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-425">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="5b3ed-426">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-426">ViYankEndOfWord</span></span>

<span data-ttu-id="5b3ed-427">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="5b3ed-427">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="5b3ed-428">VI-opdracht modus: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-428">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="5b3ed-429">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="5b3ed-429">ViYankLeft</span></span>

<span data-ttu-id="5b3ed-430">Yank teken (s) links van de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-430">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="5b3ed-431">VI-opdracht modus: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-431">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="5b3ed-432">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-432">ViYankLine</span></span>

<span data-ttu-id="5b3ed-433">Yank de volledige buffer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-433">Yank the entire buffer.</span></span>

- <span data-ttu-id="5b3ed-434">VI-opdracht modus: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-434">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="5b3ed-435">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="5b3ed-435">ViYankNextGlob</span></span>

<span data-ttu-id="5b3ed-436">Yank van de cursor naar het begin van de volgende woord (en).</span><span class="sxs-lookup"><span data-stu-id="5b3ed-436">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="5b3ed-437">VI-opdracht modus: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-437">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="5b3ed-438">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-438">ViYankNextWord</span></span>

<span data-ttu-id="5b3ed-439">Yank het woord (en) na de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-439">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="5b3ed-440">VI-opdracht modus: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-440">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="5b3ed-441">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="5b3ed-441">ViYankPercent</span></span>

<span data-ttu-id="5b3ed-442">Yank naar/van overeenkomende accolade.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-442">Yank to/from matching brace.</span></span>

- <span data-ttu-id="5b3ed-443">VI-opdracht modus: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-443">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="5b3ed-444">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="5b3ed-444">ViYankPreviousGlob</span></span>

<span data-ttu-id="5b3ed-445">Yank vanaf het begin van het (de) woord (en) tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-445">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="5b3ed-446">VI-opdracht modus: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-446">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="5b3ed-447">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-447">ViYankPreviousWord</span></span>

<span data-ttu-id="5b3ed-448">Yank de woorden vóór de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-448">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="5b3ed-449">VI-opdracht modus: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-449">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="5b3ed-450">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="5b3ed-450">ViYankRight</span></span>

<span data-ttu-id="5b3ed-451">Yank teken (s) onder en rechts van de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-451">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="5b3ed-452">VI-opdracht modus: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-452">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="5b3ed-453">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-453">ViYankToEndOfLine</span></span>

<span data-ttu-id="5b3ed-454">Yank van de cursor tot het einde van de buffer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-454">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="5b3ed-455">VI-opdracht modus: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-455">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="5b3ed-456">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-456">ViYankToFirstChar</span></span>

<span data-ttu-id="5b3ed-457">Yank van het eerste niet-spatie teken tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-457">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="5b3ed-458">VI-opdracht modus: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-458">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="5b3ed-459">Yank</span><span class="sxs-lookup"><span data-stu-id="5b3ed-459">Yank</span></span>

<span data-ttu-id="5b3ed-460">Voeg de meest recent afgebroken tekst toe aan de invoer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-460">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="5b3ed-461">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-461">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="5b3ed-462">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="5b3ed-462">YankLastArg</span></span>

<span data-ttu-id="5b3ed-463">Yank het laatste argument van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-463">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="5b3ed-464">Met een argument, de eerste keer dat deze wordt aangeroepen, gedraagt zich op dezelfde manier als YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-464">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="5b3ed-465">Als meerdere keren worden aangeroepen, wordt door de geschiedenis en ARG de richting ingesteld (negatief de richting omkeren.)</span><span class="sxs-lookup"><span data-stu-id="5b3ed-465">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="5b3ed-466">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-466">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="5b3ed-467">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-467">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="5b3ed-468">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="5b3ed-468">YankNthArg</span></span>

<span data-ttu-id="5b3ed-469">Yank het eerste argument (na de opdracht) van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-469">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="5b3ed-470">Met een argument, Yank het ne argument (vanaf 0), als het argument negatief is, begint vanaf het laatste argument.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-470">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="5b3ed-471">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-471">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="5b3ed-472">YankPop</span><span class="sxs-lookup"><span data-stu-id="5b3ed-472">YankPop</span></span>

<span data-ttu-id="5b3ed-473">Als de vorige bewerking Yank of YankPop is, vervangt u de eerder yanked tekst door de volgende afgebroken tekst van de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-473">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="5b3ed-474">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-474">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="5b3ed-475">Functies voor cursor verplaatsing</span><span class="sxs-lookup"><span data-stu-id="5b3ed-475">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="5b3ed-476">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-476">BackwardChar</span></span>

<span data-ttu-id="5b3ed-477">De cursor één teken naar links verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-477">Move the cursor one character to the left.</span></span> <span data-ttu-id="5b3ed-478">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-478">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="5b3ed-479">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-479">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="5b3ed-480">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-480">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="5b3ed-481">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-481">BackwardWord</span></span>

<span data-ttu-id="5b3ed-482">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-482">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="5b3ed-483">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-483">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="5b3ed-484">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-484">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="5b3ed-485">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-485">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="5b3ed-486">VI Invoeg modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-486">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="5b3ed-487">VI-opdracht modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-487">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="5b3ed-488">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-488">BeginningOfLine</span></span>

<span data-ttu-id="5b3ed-489">Als de invoer meerdere regels heeft, gaat u naar het begin van de huidige regel of gaat u naar het begin van de invoer als deze al aan het begin van de regel staat.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-489">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="5b3ed-490">Als de invoer één regel heeft, gaat u naar het begin van de invoer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-490">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="5b3ed-491">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-491">Cmd: `<Home>`</span></span>
- <span data-ttu-id="5b3ed-492">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-492">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="5b3ed-493">VI Invoeg modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-493">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="5b3ed-494">VI-opdracht modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-494">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="5b3ed-495">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-495">EndOfLine</span></span>

<span data-ttu-id="5b3ed-496">Als de invoer meerdere regels heeft, gaat u naar het einde van de huidige regel of gaat u naar het einde van de invoer als u aan het einde van de regel bent.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-496">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="5b3ed-497">Als de invoer één regel heeft, gaat u naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-497">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="5b3ed-498">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-498">Cmd: `<End>`</span></span>
- <span data-ttu-id="5b3ed-499">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-499">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="5b3ed-500">VI Invoeg modus: `<End>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-500">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="5b3ed-501">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-501">ForwardChar</span></span>

<span data-ttu-id="5b3ed-502">De cursor één teken naar rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-502">Move the cursor one character to the right.</span></span> <span data-ttu-id="5b3ed-503">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-503">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="5b3ed-504">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-504">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="5b3ed-505">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-505">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="5b3ed-506">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-506">ForwardWord</span></span>

<span data-ttu-id="5b3ed-507">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-507">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="5b3ed-508">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-508">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="5b3ed-509">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-509">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="5b3ed-510">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="5b3ed-510">GotoBrace</span></span>

<span data-ttu-id="5b3ed-511">Ga naar de accolade, haakjes of vier Kante haakjes.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-511">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="5b3ed-512">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-512">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="5b3ed-513">VI Invoeg modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-513">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="5b3ed-514">VI-opdracht modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-514">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="5b3ed-515">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="5b3ed-515">GotoColumn</span></span>

<span data-ttu-id="5b3ed-516">Ga naar de kolom die wordt aangegeven door arg.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-516">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="5b3ed-517">VI-opdracht modus: `<|>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-517">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="5b3ed-518">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-518">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="5b3ed-519">De cursor verplaatsen naar het eerste niet-lege teken in de regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-519">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="5b3ed-520">VI-opdracht modus: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-520">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="5b3ed-521">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-521">MoveToEndOfLine</span></span>

<span data-ttu-id="5b3ed-522">De cursor verplaatsen naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-522">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="5b3ed-523">VI-opdracht modus: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-523">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="5b3ed-524">NextLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-524">NextLine</span></span>

<span data-ttu-id="5b3ed-525">De cursor verplaatsen naar de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-525">Move the cursor to the next line.</span></span>

- <span data-ttu-id="5b3ed-526">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-526">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="5b3ed-527">NextWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-527">NextWord</span></span>

<span data-ttu-id="5b3ed-528">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-528">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="5b3ed-529">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-529">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="5b3ed-530">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-530">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="5b3ed-531">VI Invoeg modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-531">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="5b3ed-532">VI-opdracht modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-532">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="5b3ed-533">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="5b3ed-533">NextWordEnd</span></span>

<span data-ttu-id="5b3ed-534">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-534">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="5b3ed-535">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-535">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="5b3ed-536">VI-opdracht modus: `<e>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-536">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="5b3ed-537">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-537">PreviousLine</span></span>

<span data-ttu-id="5b3ed-538">Verplaats de cursor naar de vorige regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-538">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="5b3ed-539">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-539">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="5b3ed-540">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-540">ShellBackwardWord</span></span>

<span data-ttu-id="5b3ed-541">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-541">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="5b3ed-542">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-542">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="5b3ed-543">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-543">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="5b3ed-544">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-544">ShellForwardWord</span></span>

<span data-ttu-id="5b3ed-545">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-545">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="5b3ed-546">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-546">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="5b3ed-547">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-547">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="5b3ed-548">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-548">ShellNextWord</span></span>

<span data-ttu-id="5b3ed-549">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-549">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="5b3ed-550">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-550">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="5b3ed-551">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-551">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="5b3ed-552">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-552">ViBackwardChar</span></span>

<span data-ttu-id="5b3ed-553">De cursor één teken naar links verplaatsen in de bewerkings modus VI.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-553">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="5b3ed-554">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-554">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="5b3ed-555">VI Invoeg modus: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-555">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="5b3ed-556">VI-opdracht modus: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-556">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="5b3ed-557">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-557">ViBackwardWord</span></span>

<span data-ttu-id="5b3ed-558">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-558">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="5b3ed-559">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-559">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="5b3ed-560">VI-opdracht modus: `<b>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-560">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="5b3ed-561">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-561">ViForwardChar</span></span>

<span data-ttu-id="5b3ed-562">De cursor één teken naar rechts verplaatsen in de bewerkings modus VI.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-562">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="5b3ed-563">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-563">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="5b3ed-564">VI Invoeg modus: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-564">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="5b3ed-565">VI-opdracht modus: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-565">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="5b3ed-566">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="5b3ed-566">ViEndOfGlob</span></span>

<span data-ttu-id="5b3ed-567">Verplaatst de cursor naar het einde van het woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-567">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="5b3ed-568">VI-opdracht modus: `<E>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-568">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="5b3ed-569">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="5b3ed-569">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="5b3ed-570">Wordt verplaatst naar het einde van het vorige woord, waarbij alleen witruimte wordt gebruikt als woord als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-570">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="5b3ed-571">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-571">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="5b3ed-572">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="5b3ed-572">ViGotoBrace</span></span>

<span data-ttu-id="5b3ed-573">Vergelijkbaar met GotoBrace, maar is in plaats van op tokens gebaseerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-573">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="5b3ed-574">VI-opdracht modus: `<%>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-574">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="5b3ed-575">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="5b3ed-575">ViNextGlob</span></span>

<span data-ttu-id="5b3ed-576">Verplaatst naar het volgende woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-576">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="5b3ed-577">VI-opdracht modus: `<W>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-577">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="5b3ed-578">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-578">ViNextWord</span></span>

<span data-ttu-id="5b3ed-579">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-579">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="5b3ed-580">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-580">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="5b3ed-581">VI-opdracht modus: `<w>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-581">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="5b3ed-582">Geschiedenis functies</span><span class="sxs-lookup"><span data-stu-id="5b3ed-582">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="5b3ed-583">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="5b3ed-583">BeginningOfHistory</span></span>

<span data-ttu-id="5b3ed-584">Hiermee gaat u naar het eerste item in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-584">Move to the first item in the history.</span></span>

- <span data-ttu-id="5b3ed-585">Emacs: `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-585">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="5b3ed-586">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="5b3ed-586">ClearHistory</span></span>

<span data-ttu-id="5b3ed-587">Hiermee wist u de geschiedenis in PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-587">Clears history in PSReadLine.</span></span> <span data-ttu-id="5b3ed-588">Dit heeft geen invloed op de Power shell-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-588">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="5b3ed-589">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-589">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="5b3ed-590">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="5b3ed-590">EndOfHistory</span></span>

<span data-ttu-id="5b3ed-591">Hiermee gaat u naar het laatste item (de huidige invoer) in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-591">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="5b3ed-592">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-592">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="5b3ed-593">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="5b3ed-593">ForwardSearchHistory</span></span>

<span data-ttu-id="5b3ed-594">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-594">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="5b3ed-595">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-595">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="5b3ed-596">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-596">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="5b3ed-597">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="5b3ed-597">HistorySearchBackward</span></span>

<span data-ttu-id="5b3ed-598">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-598">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="5b3ed-599">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-599">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="5b3ed-600">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="5b3ed-600">HistorySearchForward</span></span>

<span data-ttu-id="5b3ed-601">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-601">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="5b3ed-602">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-602">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="5b3ed-603">NextHistory</span><span class="sxs-lookup"><span data-stu-id="5b3ed-603">NextHistory</span></span>

<span data-ttu-id="5b3ed-604">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-604">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="5b3ed-605">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-605">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="5b3ed-606">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-606">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="5b3ed-607">VI Invoeg modus: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-607">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="5b3ed-608">VI-opdracht modus: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-608">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="5b3ed-609">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="5b3ed-609">PreviousHistory</span></span>

<span data-ttu-id="5b3ed-610">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-610">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="5b3ed-611">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-611">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="5b3ed-612">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-612">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="5b3ed-613">VI Invoeg modus: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-613">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="5b3ed-614">VI-opdracht modus: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-614">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="5b3ed-615">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="5b3ed-615">ReverseSearchHistory</span></span>

<span data-ttu-id="5b3ed-616">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-616">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="5b3ed-617">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-617">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="5b3ed-618">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-618">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="5b3ed-619">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="5b3ed-619">ViSearchHistoryBackward</span></span>

<span data-ttu-id="5b3ed-620">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-620">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="5b3ed-621">VI Invoeg modus: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-621">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="5b3ed-622">VI-opdracht modus: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-622">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="5b3ed-623">Voltooiings functies</span><span class="sxs-lookup"><span data-stu-id="5b3ed-623">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="5b3ed-624">Voltooid</span><span class="sxs-lookup"><span data-stu-id="5b3ed-624">Complete</span></span>

<span data-ttu-id="5b3ed-625">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-625">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="5b3ed-626">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-626">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="5b3ed-627">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-627">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="5b3ed-628">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-628">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="5b3ed-629">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="5b3ed-629">MenuComplete</span></span>

<span data-ttu-id="5b3ed-630">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-630">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="5b3ed-631">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-631">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="5b3ed-632">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-632">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="5b3ed-633">Cmd: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-633">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="5b3ed-634">Emacs: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-634">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="5b3ed-635">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="5b3ed-635">PossibleCompletions</span></span>

<span data-ttu-id="5b3ed-636">De lijst met mogelijke aanvullingen weer geven.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-636">Display the list of possible completions.</span></span>

- <span data-ttu-id="5b3ed-637">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-637">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="5b3ed-638">VI Invoeg modus: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-638">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="5b3ed-639">VI-opdracht modus: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-639">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="5b3ed-640">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="5b3ed-640">TabCompleteNext</span></span>

<span data-ttu-id="5b3ed-641">Poging om de tekst rond de cursor te volt ooien met de volgende beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-641">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="5b3ed-642">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-642">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="5b3ed-643">VI-opdracht modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-643">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="5b3ed-644">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="5b3ed-644">TabCompletePrevious</span></span>

<span data-ttu-id="5b3ed-645">Poging om de tekst rond de cursor te volt ooien met de vorige beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-645">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="5b3ed-646">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-646">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="5b3ed-647">VI-opdracht modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-647">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="5b3ed-648">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="5b3ed-648">ViTabCompleteNext</span></span>

<span data-ttu-id="5b3ed-649">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompleteNext aan.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-649">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="5b3ed-650">VI Invoeg modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-650">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="5b3ed-651">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="5b3ed-651">ViTabCompletePrevious</span></span>

<span data-ttu-id="5b3ed-652">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompletePrevious aan.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-652">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="5b3ed-653">VI Invoeg modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-653">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="prediction-functions"></a><span data-ttu-id="5b3ed-654">Voorspellings functies</span><span class="sxs-lookup"><span data-stu-id="5b3ed-654">Prediction functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="5b3ed-655">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-655">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="5b3ed-656">Wanneer u `InlineView` als weergave stijl voor voor spellingen gebruikt, moet u het volgende woord van de inline suggestie accepteren.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-656">When using `InlineView` as the view style for prediction, accept the next word of the inline suggestion.</span></span>

- <span data-ttu-id="5b3ed-657">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-657">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="5b3ed-658">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="5b3ed-658">AcceptSuggestion</span></span>

<span data-ttu-id="5b3ed-659">Wanneer u `InlineView` als weergave stijl voor voor spellingen gebruikt, moet u de huidige inline suggestie accepteren.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-659">When using `InlineView` as the view style for prediction, accept the current inline suggestion.</span></span>

- <span data-ttu-id="5b3ed-660">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-660">Function is unbound.</span></span>

### <a name="nextsuggestion"></a><span data-ttu-id="5b3ed-661">NextSuggestion</span><span class="sxs-lookup"><span data-stu-id="5b3ed-661">NextSuggestion</span></span>

<span data-ttu-id="5b3ed-662">Wanneer u `ListView` als weergave stijl voor voor spellingen gebruikt, gaat u naar de volgende suggestie in de lijst.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-662">When using `ListView` as the view style for prediction, navigate to the next suggestion in the list.</span></span>

- <span data-ttu-id="5b3ed-663">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-663">Function is unbound.</span></span>

### <a name="previoussuggestion"></a><span data-ttu-id="5b3ed-664">PreviousSuggestion</span><span class="sxs-lookup"><span data-stu-id="5b3ed-664">PreviousSuggestion</span></span>

<span data-ttu-id="5b3ed-665">Wanneer u `ListView` als weergave stijl voor voor spellingen gebruikt, gaat u naar de vorige suggestie in de lijst.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-665">When using `ListView` as the view style for prediction, navigate to the previous suggestion in the list.</span></span>

- <span data-ttu-id="5b3ed-666">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-666">Function is unbound.</span></span>

### <a name="switchpredictionview"></a><span data-ttu-id="5b3ed-667">SwitchPredictionView</span><span class="sxs-lookup"><span data-stu-id="5b3ed-667">SwitchPredictionView</span></span>

<span data-ttu-id="5b3ed-668">Scha kelen tussen de weergave stijl voor de voor spelling tussen `InlineView` en `ListView` .</span><span class="sxs-lookup"><span data-stu-id="5b3ed-668">Switch the view style for prediction between `InlineView` and `ListView`.</span></span>

- <span data-ttu-id="5b3ed-669">Cmd `<F2>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-669">Cmd: `<F2>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="5b3ed-670">Diverse functies</span><span class="sxs-lookup"><span data-stu-id="5b3ed-670">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="5b3ed-671">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="5b3ed-671">CaptureScreen</span></span>

<span data-ttu-id="5b3ed-672">Interactieve scherm opname starten-pijl-omhoog/omlaag Selecteer regels en voer de geselecteerde tekst als tekst en HTML naar het klem bord kopiëren.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-672">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="5b3ed-673">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-673">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="5b3ed-674">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="5b3ed-674">ClearScreen</span></span>

<span data-ttu-id="5b3ed-675">Schakel het scherm uit en teken de huidige regel boven aan het scherm.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-675">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="5b3ed-676">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-676">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="5b3ed-677">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-677">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="5b3ed-678">VI Invoeg modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-678">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="5b3ed-679">VI-opdracht modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-679">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="5b3ed-680">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="5b3ed-680">DigitArgument</span></span>

<span data-ttu-id="5b3ed-681">Start een nieuw cijfer argument om door te geven aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-681">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="5b3ed-682">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-682">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="5b3ed-683">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-683">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="5b3ed-684">VI-opdracht modus: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-684">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="5b3ed-685">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="5b3ed-685">InvokePrompt</span></span>

<span data-ttu-id="5b3ed-686">Hiermee wordt de huidige prompt gewist en wordt de functie Prompt aangeroepen om de prompt opnieuw weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-686">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="5b3ed-687">Dit is handig voor aangepaste sleutel afhandelingen die de status wijzigen, bijvoorbeeld de huidige map wijzigen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-687">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="5b3ed-688">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-688">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="5b3ed-689">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="5b3ed-689">ScrollDisplayDown</span></span>

<span data-ttu-id="5b3ed-690">De weer gave één scherm omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-690">Scroll the display down one screen.</span></span>

- <span data-ttu-id="5b3ed-691">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-691">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="5b3ed-692">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-692">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="5b3ed-693">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-693">ScrollDisplayDownLine</span></span>

<span data-ttu-id="5b3ed-694">De weer gave één regel omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-694">Scroll the display down one line.</span></span>

- <span data-ttu-id="5b3ed-695">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-695">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="5b3ed-696">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-696">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="5b3ed-697">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="5b3ed-697">ScrollDisplayToCursor</span></span>

<span data-ttu-id="5b3ed-698">Schuif de weer gave naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-698">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="5b3ed-699">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-699">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="5b3ed-700">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="5b3ed-700">ScrollDisplayTop</span></span>

<span data-ttu-id="5b3ed-701">Schuif de weer gave naar boven.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-701">Scroll the display to the top.</span></span>

- <span data-ttu-id="5b3ed-702">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-702">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="5b3ed-703">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="5b3ed-703">ScrollDisplayUp</span></span>

<span data-ttu-id="5b3ed-704">Schuif de weer gave één scherm omhoog.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-704">Scroll the display up one screen.</span></span>

- <span data-ttu-id="5b3ed-705">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-705">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="5b3ed-706">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-706">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="5b3ed-707">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-707">ScrollDisplayUpLine</span></span>

<span data-ttu-id="5b3ed-708">De weer gave één regel omhoog schuiven.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-708">Scroll the display up one line.</span></span>

- <span data-ttu-id="5b3ed-709">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-709">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="5b3ed-710">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-710">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="5b3ed-711">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="5b3ed-711">SelfInsert</span></span>

<span data-ttu-id="5b3ed-712">Voeg de sleutel in.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-712">Insert the key.</span></span>

- <span data-ttu-id="5b3ed-713">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-713">Function is unbound.</span></span>

### <a name="showcommandhelp"></a><span data-ttu-id="5b3ed-714">ShowCommandHelp</span><span class="sxs-lookup"><span data-stu-id="5b3ed-714">ShowCommandHelp</span></span>

<span data-ttu-id="5b3ed-715">Biedt een weer gave van de volledige Help-informatie over cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-715">Provides a view of full cmdlet help.</span></span> <span data-ttu-id="5b3ed-716">Wanneer de cursor zich aan het einde van een volledig uitgebreide para meter bevindt, wordt de `<F1>` weer gave van de Help op de locatie van de para meter gepositioneerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-716">When the cursor is at the end of a fully-expanded parameter, hitting the `<F1>` key positions the display of help at the location of that parameter.</span></span>

<span data-ttu-id="5b3ed-717">De Help wordt weer gegeven op een andere scherm buffer met behulp van een paginerings functie van **micro soft. Power shell. pager**.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-717">The help is displayed on an alternate screen buffer using a Pager from **Microsoft.PowerShell.Pager**.</span></span> <span data-ttu-id="5b3ed-718">Wanneer u de paginerings functie verlaat, keert u terug naar de oorspronkelijke cursor positie op het oorspronkelijke scherm.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-718">When you exit the pager you are returned to the original cursor position on the original screen.</span></span> <span data-ttu-id="5b3ed-719">Deze paginering werkt alleen in moderne terminal toepassingen zoals [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701).</span><span class="sxs-lookup"><span data-stu-id="5b3ed-719">This pager only works in modern terminal applications such as [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701).</span></span>

- <span data-ttu-id="5b3ed-720">Cmd `<F1>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-720">Cmd: `<F1>`</span></span>
- <span data-ttu-id="5b3ed-721">Emacs: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-721">Emacs: `<F1>`</span></span>
- <span data-ttu-id="5b3ed-722">VI Invoeg modus: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-722">Vi insert mode: `<F1>`</span></span>
- <span data-ttu-id="5b3ed-723">VI-opdracht modus: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-723">Vi command mode: `<F1>`</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="5b3ed-724">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="5b3ed-724">ShowKeyBindings</span></span>

<span data-ttu-id="5b3ed-725">Alle gebonden sleutels weer geven.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-725">Show all bound keys.</span></span>

- <span data-ttu-id="5b3ed-726">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-726">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="5b3ed-727">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-727">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="5b3ed-728">VI Invoeg modus: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-728">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="showparameterhelp"></a><span data-ttu-id="5b3ed-729">ShowParameterHelp</span><span class="sxs-lookup"><span data-stu-id="5b3ed-729">ShowParameterHelp</span></span>

<span data-ttu-id="5b3ed-730">Biedt dynamische Help voor para meters door deze onder de huidige opdracht regel te laten zien `MenuComplete` .</span><span class="sxs-lookup"><span data-stu-id="5b3ed-730">Provides dynamic help for parameters by showing it below the current command line like `MenuComplete`.</span></span> <span data-ttu-id="5b3ed-731">Wanneer u op de toets drukt, moet de cursor zich aan het einde van de naam van de volledig uitgebreide para meter bevinden `<Alt+h>` .</span><span class="sxs-lookup"><span data-stu-id="5b3ed-731">The cursor must be at the end of the fully-expanded parameter name when you press the `<Alt+h>` key.</span></span>

- <span data-ttu-id="5b3ed-732">Cmd `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-732">Cmd: `<Alt+h>`</span></span>
- <span data-ttu-id="5b3ed-733">Emacs: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-733">Emacs: `<Alt+h>`</span></span>
- <span data-ttu-id="5b3ed-734">VI Invoeg modus: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-734">Vi insert mode: `<Alt+h>`</span></span>
- <span data-ttu-id="5b3ed-735">VI-opdracht modus: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-735">Vi command mode: `<Alt+h>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="5b3ed-736">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="5b3ed-736">ViCommandMode</span></span>

<span data-ttu-id="5b3ed-737">Schakel de huidige bedrijfs modus uit van Vi-Insert naar de VI-opdracht.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-737">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="5b3ed-738">VI Invoeg modus: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-738">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="5b3ed-739">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-739">ViDigitArgumentInChord</span></span>

<span data-ttu-id="5b3ed-740">Start een nieuw cijfer argument om door te geven aan andere functies in een van de koorden van VI.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-740">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="5b3ed-741">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-741">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="5b3ed-742">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="5b3ed-742">ViEditVisually</span></span>

<span data-ttu-id="5b3ed-743">Bewerk de opdracht regel in een tekst editor die is opgegeven door $env: EDITOR of $env: VISUAL.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-743">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="5b3ed-744">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-744">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="5b3ed-745">VI-opdracht modus: `<v>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-745">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="5b3ed-746">ViExit</span><span class="sxs-lookup"><span data-stu-id="5b3ed-746">ViExit</span></span>

<span data-ttu-id="5b3ed-747">Hiermee wordt de shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-747">Exits the shell.</span></span>

- <span data-ttu-id="5b3ed-748">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-748">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="5b3ed-749">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="5b3ed-749">ViInsertMode</span></span>

<span data-ttu-id="5b3ed-750">Schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-750">Switch to Insert mode.</span></span>

- <span data-ttu-id="5b3ed-751">VI-opdracht modus: `<i>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-751">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="5b3ed-752">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="5b3ed-752">WhatIsKey</span></span>

<span data-ttu-id="5b3ed-753">Lees een sleutel en vertel me wat de sleutel is gebonden.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-753">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="5b3ed-754">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-754">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="5b3ed-755">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-755">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="5b3ed-756">Selectie functies</span><span class="sxs-lookup"><span data-stu-id="5b3ed-756">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="5b3ed-757">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="5b3ed-757">ExchangePointAndMark</span></span>

<span data-ttu-id="5b3ed-758">De cursor wordt op de locatie van het merk geplaatst en het vinkje wordt verplaatst naar de locatie van de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-758">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="5b3ed-759">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-759">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="5b3ed-760">SelectAll aanroepen</span><span class="sxs-lookup"><span data-stu-id="5b3ed-760">SelectAll</span></span>

<span data-ttu-id="5b3ed-761">Selecteer de volledige regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-761">Select the entire line.</span></span>

- <span data-ttu-id="5b3ed-762">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-762">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="5b3ed-763">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-763">SelectBackwardChar</span></span>

<span data-ttu-id="5b3ed-764">Pas de huidige selectie aan om het vorige teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-764">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="5b3ed-765">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-765">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="5b3ed-766">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-766">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="5b3ed-767">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-767">SelectBackwardsLine</span></span>

<span data-ttu-id="5b3ed-768">Pas de huidige selectie aan de cursor toe aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-768">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="5b3ed-769">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-769">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="5b3ed-770">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-770">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="5b3ed-771">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-771">SelectBackwardWord</span></span>

<span data-ttu-id="5b3ed-772">Pas de huidige selectie aan om het vorige woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-772">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="5b3ed-773">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-773">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="5b3ed-774">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-774">Emacs: `<Alt+B>`</span></span>

### <a name="selectcommandargument"></a><span data-ttu-id="5b3ed-775">SelectCommandArgument</span><span class="sxs-lookup"><span data-stu-id="5b3ed-775">SelectCommandArgument</span></span>

<span data-ttu-id="5b3ed-776">Maak een visuele selectie van de opdracht argumenten.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-776">Make visual selection of the command arguments.</span></span> <span data-ttu-id="5b3ed-777">De selectie van argumenten ligt binnen het bereik van een script blok.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-777">Selection of arguments is scoped within a script block.</span></span> <span data-ttu-id="5b3ed-778">Op basis van de positie van de cursor zoekt het naar het binnenste script blok naar het hoogste script blok en stopt wanneer er argumenten worden gevonden in een script blok bereik.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-778">Based on the cursor position, it searches from the innermost script block to the outmost script block, and stops when it finds any arguments in a script block scope.</span></span>

<span data-ttu-id="5b3ed-779">Deze functie voldoet aan DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-779">This function honors DigitArgument.</span></span> <span data-ttu-id="5b3ed-780">De waarden voor het positieve of negatieve argument worden beschouwd als de begin-of achterwaartse verschuivingen van het momenteel geselecteerde argument of vanaf de huidige cursor positie wanneer er geen argument is geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-780">It treats the positive or negative argument values as the forward or backward offsets from the currently selected argument, or from the current cursor position when no argument is selected.</span></span>

- <span data-ttu-id="5b3ed-781">Cmd `<Alt+a>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-781">Cmd: `<Alt+a>`</span></span>
- <span data-ttu-id="5b3ed-782">Emacs: `<Alt+a>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-782">Emacs: `<Alt+a>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="5b3ed-783">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-783">SelectForwardChar</span></span>

<span data-ttu-id="5b3ed-784">Pas de huidige selectie aan om het volgende teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-784">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="5b3ed-785">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-785">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="5b3ed-786">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-786">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="5b3ed-787">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-787">SelectForwardWord</span></span>

<span data-ttu-id="5b3ed-788">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-788">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="5b3ed-789">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-789">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="5b3ed-790">SelectLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-790">SelectLine</span></span>

<span data-ttu-id="5b3ed-791">Pas de huidige selectie aan de cursor toe aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-791">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="5b3ed-792">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-792">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="5b3ed-793">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-793">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="5b3ed-794">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-794">SelectNextWord</span></span>

<span data-ttu-id="5b3ed-795">Pas de huidige selectie aan om het volgende woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-795">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="5b3ed-796">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-796">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="5b3ed-797">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-797">SelectShellBackwardWord</span></span>

<span data-ttu-id="5b3ed-798">Pas de huidige selectie aan om het vorige woord op te maken met behulp van ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-798">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="5b3ed-799">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-799">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="5b3ed-800">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-800">SelectShellForwardWord</span></span>

<span data-ttu-id="5b3ed-801">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-801">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="5b3ed-802">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-802">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="5b3ed-803">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="5b3ed-803">SelectShellNextWord</span></span>

<span data-ttu-id="5b3ed-804">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-804">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="5b3ed-805">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-805">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="5b3ed-806">SetMark</span><span class="sxs-lookup"><span data-stu-id="5b3ed-806">SetMark</span></span>

<span data-ttu-id="5b3ed-807">De huidige locatie van de cursor markeren voor gebruik in een volgende bewerkings opdracht.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-807">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="5b3ed-808">Emacs: `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-808">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="5b3ed-809">Voorspellende IntelliSense-functies</span><span class="sxs-lookup"><span data-stu-id="5b3ed-809">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="5b3ed-810">Voorspellende IntelliSense moet zijn ingeschakeld om deze functies te kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-810">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="5b3ed-811">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="5b3ed-811">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="5b3ed-812">Hiermee wordt het volgende woord van de inline suggestie geaccepteerd van voorspellende IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-812">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="5b3ed-813">Deze functie kan worden gebonden met <kbd>CTRL</kbd> + <kbd>F</kbd> door de volgende opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-813">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="5b3ed-814">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="5b3ed-814">AcceptSuggestion</span></span>

<span data-ttu-id="5b3ed-815">Hiermee wordt de huidige inline suggestie van voorspellende IntelliSense geaccepteerd door op <kbd>RightArrow</kbd> te drukken wanneer de cursor zich aan het einde van de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-815">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="5b3ed-816">Zoek functies</span><span class="sxs-lookup"><span data-stu-id="5b3ed-816">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="5b3ed-817">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="5b3ed-817">CharacterSearch</span></span>

<span data-ttu-id="5b3ed-818">Lees een teken en zoek voorwaarts naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-818">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="5b3ed-819">Als er een argument is opgegeven, zoekt u voorwaarts (of achterwaarts als negatieve) voor het ne voorval.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-819">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="5b3ed-820">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-820">Cmd: `<F3>`</span></span>
- <span data-ttu-id="5b3ed-821">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-821">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="5b3ed-822">VI Invoeg modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-822">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="5b3ed-823">VI-opdracht modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-823">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="5b3ed-824">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="5b3ed-824">CharacterSearchBackward</span></span>

<span data-ttu-id="5b3ed-825">Lees een teken en zoek terug naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-825">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="5b3ed-826">Als er een argument is opgegeven, zoekt u terug (of als dit negatief is) voor het ne exemplaar.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-826">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="5b3ed-827">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-827">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="5b3ed-828">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-828">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="5b3ed-829">VI Invoeg modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-829">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="5b3ed-830">VI-opdracht modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-830">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="5b3ed-831">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="5b3ed-831">RepeatLastCharSearch</span></span>

<span data-ttu-id="5b3ed-832">De laatst opgenomen zoek opdracht herhalen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-832">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="5b3ed-833">VI-opdracht modus: `<;>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-833">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="5b3ed-834">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="5b3ed-834">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="5b3ed-835">De laatst opgenomen zoek opdracht herhalen, maar in tegenovergestelde richting.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-835">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="5b3ed-836">VI-opdracht modus: `<,>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-836">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="5b3ed-837">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="5b3ed-837">RepeatSearch</span></span>

<span data-ttu-id="5b3ed-838">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-838">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="5b3ed-839">VI-opdracht modus: `<n>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-839">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="5b3ed-840">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="5b3ed-840">RepeatSearchBackward</span></span>

<span data-ttu-id="5b3ed-841">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-841">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="5b3ed-842">VI-opdracht modus: `<N>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-842">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="5b3ed-843">SearchChar</span><span class="sxs-lookup"><span data-stu-id="5b3ed-843">SearchChar</span></span>

<span data-ttu-id="5b3ed-844">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-844">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="5b3ed-845">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-845">This is for 't' functionality.</span></span>

- <span data-ttu-id="5b3ed-846">VI-opdracht modus: `<f>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-846">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="5b3ed-847">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="5b3ed-847">SearchCharBackward</span></span>

<span data-ttu-id="5b3ed-848">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-848">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="5b3ed-849">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-849">This is for 'T' functionality.</span></span>

- <span data-ttu-id="5b3ed-850">VI-opdracht modus: `<F>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-850">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="5b3ed-851">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="5b3ed-851">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="5b3ed-852">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-852">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="5b3ed-853">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-853">This is for 'T' functionality.</span></span>

- <span data-ttu-id="5b3ed-854">VI-opdracht modus: `<T>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-854">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="5b3ed-855">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="5b3ed-855">SearchCharWithBackoff</span></span>

<span data-ttu-id="5b3ed-856">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-856">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="5b3ed-857">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-857">This is for 't' functionality.</span></span>

- <span data-ttu-id="5b3ed-858">VI-opdracht modus: `<t>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-858">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="5b3ed-859">SearchForward</span><span class="sxs-lookup"><span data-stu-id="5b3ed-859">SearchForward</span></span>

<span data-ttu-id="5b3ed-860">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-860">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="5b3ed-861">VI Invoeg modus: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-861">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="5b3ed-862">VI-opdracht modus: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="5b3ed-862">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="5b3ed-863">Aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="5b3ed-863">Custom Key Bindings</span></span>

<span data-ttu-id="5b3ed-864">PSReadLine ondersteunt aangepaste sleutel bindingen met behulp van de-cmdlet `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="5b3ed-864">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="5b3ed-865">De meeste aangepaste sleutel bindingen roepen een van de bovenstaande functies aan, bijvoorbeeld</span><span class="sxs-lookup"><span data-stu-id="5b3ed-865">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="5b3ed-866">U kunt een script Block binden aan een sleutel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-866">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="5b3ed-867">Het script Block kan veel wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-867">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="5b3ed-868">Enkele handige voor beelden zijn</span><span class="sxs-lookup"><span data-stu-id="5b3ed-868">Some useful examples include</span></span>

- <span data-ttu-id="5b3ed-869">de opdracht regel bewerken</span><span class="sxs-lookup"><span data-stu-id="5b3ed-869">edit the command line</span></span>
- <span data-ttu-id="5b3ed-870">een nieuw venster openen (bijvoorbeeld Help)</span><span class="sxs-lookup"><span data-stu-id="5b3ed-870">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="5b3ed-871">mappen wijzigen zonder de opdracht regel te wijzigen</span><span class="sxs-lookup"><span data-stu-id="5b3ed-871">change directories without changing the command line</span></span>

<span data-ttu-id="5b3ed-872">De script Block ontvangt twee argumenten:</span><span class="sxs-lookup"><span data-stu-id="5b3ed-872">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="5b3ed-873">`$key` -Een **[ConsoleKeyInfo]** -object dat de sleutel is die de aangepaste binding heeft geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-873">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="5b3ed-874">Als u dezelfde script Block aan meerdere sleutels koppelt en verschillende acties moet uitvoeren, afhankelijk van de sleutel, kunt u $key controleren.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-874">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="5b3ed-875">Veel aangepaste bindingen negeren dit argument.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-875">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="5b3ed-876">`$arg` -Een wille keurig argument.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-876">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="5b3ed-877">Meestal is dit een geheel getal dat de gebruiker door gegeven van de sleutel bindingen DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-877">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="5b3ed-878">Als uw binding geen argumenten accepteert, is het redelijk om dit argument te negeren.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-878">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="5b3ed-879">Laten we een voor beeld bekijken waarmee een opdracht regel wordt toegevoegd aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-879">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="5b3ed-880">Dit is handig wanneer u ervoor hebt gekozen om iets te doen, maar niet opnieuw moet invoeren van de opdracht regel die u al hebt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-880">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

<span data-ttu-id="5b3ed-881">U kunt veel meer voor beelden bekijken in het bestand `SamplePSReadLineProfile.ps1` dat is geïnstalleerd in de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-881">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="5b3ed-882">De meeste sleutel bindingen gebruiken enkele hulp functies voor het bewerken van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-882">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="5b3ed-883">Deze Api's worden beschreven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-883">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="5b3ed-884">Api's voor de ondersteuning van aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="5b3ed-884">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="5b3ed-885">De volgende functies zijn openbaar in micro soft. Power shell. PSConsoleReadLine, maar kunnen niet rechtstreeks aan een sleutel worden gebonden.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-885">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="5b3ed-886">De meeste zijn handig in aangepaste sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-886">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="5b3ed-887">Een opdracht regel toevoegen aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-887">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="5b3ed-888">Wis de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-888">Clear the kill-ring.</span></span>  <span data-ttu-id="5b3ed-889">Dit wordt meestal gebruikt voor het testen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-889">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="5b3ed-890">Verwijder de lengte tekens uit het begin.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-890">Delete length characters from start.</span></span>  <span data-ttu-id="5b3ed-891">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-891">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="5b3ed-892">Voer de actie opname uit op basis van de voor keuren van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-892">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="5b3ed-893">Deze twee functies halen nuttige informatie op over de huidige status van de invoer buffer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-893">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="5b3ed-894">De eerste wordt vaak gebruikt voor eenvoudige gevallen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-894">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="5b3ed-895">De tweede wordt gebruikt als uw binding iets geavanceerder gaat met de AST.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-895">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="5b3ed-896">Deze twee functies worden gebruikt door `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="5b3ed-896">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="5b3ed-897">De eerste wordt gebruikt om alle sleutel bindingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-897">The first is used to get all key bindings.</span></span> <span data-ttu-id="5b3ed-898">De tweede wordt gebruikt voor het ophalen van specifieke sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-898">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="5b3ed-899">Deze functie wordt gebruikt door Get-PSReadLineOption en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-899">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="5b3ed-900">Als er niets is geselecteerd op de opdracht regel, wordt-1 geretourneerd in zowel start als length.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-900">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="5b3ed-901">Als er een selectie is op de opdracht regel, worden het begin en de lengte van de selectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-901">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="5b3ed-902">Voeg een teken of teken reeks toe aan de cursor.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-902">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="5b3ed-903">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-903">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="5b3ed-904">Dit is het belangrijkste ingangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-904">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="5b3ed-905">Er wordt geen recursie ondersteund, dus is niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-905">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="5b3ed-906">Deze functie wordt gebruikt door Remove-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-906">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="5b3ed-907">Vervang een deel van de invoer.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-907">Replace some of the input.</span></span> <span data-ttu-id="5b3ed-908">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-908">This operation supports undo/redo.</span></span> <span data-ttu-id="5b3ed-909">U kunt het beste verwijderen gevolgd door INSERT, omdat het wordt beschouwd als één actie voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-909">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="5b3ed-910">De cursor verplaatsen naar de opgegeven verschuiving.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-910">Move the cursor to the given offset.</span></span> <span data-ttu-id="5b3ed-911">Cursor verplaatsing wordt niet bijgehouden voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-911">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="5b3ed-912">Deze functie is een helper-methode die wordt gebruikt door de cmdlet Set-PSReadLineOption, maar kan handig zijn voor een aangepaste sleutel binding die tijdelijk een instelling wil wijzigen.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-912">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="5b3ed-913">Deze Help methode wordt gebruikt voor aangepaste bindingen die voldoen aan DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-913">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="5b3ed-914">Een typische aanroep ziet eruit als</span><span class="sxs-lookup"><span data-stu-id="5b3ed-914">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a><span data-ttu-id="5b3ed-915">Notities</span><span class="sxs-lookup"><span data-stu-id="5b3ed-915">Notes</span></span>

### <a name="command-history"></a><span data-ttu-id="5b3ed-916">Opdracht geschiedenis</span><span class="sxs-lookup"><span data-stu-id="5b3ed-916">Command History</span></span>

<span data-ttu-id="5b3ed-917">PSReadLine onderhoudt een geschiedenis bestand met alle opdrachten en gegevens die u hebt ingevoerd op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-917">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="5b3ed-918">Dit kan gevoelige gegevens bevatten, inclusief wacht woorden.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-918">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="5b3ed-919">Als u bijvoorbeeld de cmdlet gebruikt, `ConvertTo-SecureString` wordt het wacht woord in het geschiedenis bestand vastgelegd als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-919">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="5b3ed-920">De geschiedenis bestanden zijn een bestand met de naam `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="5b3ed-920">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="5b3ed-921">Op Windows-systemen wordt het geschiedenis bestand opgeslagen op `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="5b3ed-921">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="5b3ed-922">Op niet-Windows-systemen worden de geschiedenis bestanden opgeslagen in `$env:XDG_DATA_HOME/powershell/PSReadLine` of `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="5b3ed-922">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="5b3ed-923">Feedback & bijdragen aan PSReadLine</span><span class="sxs-lookup"><span data-stu-id="5b3ed-923">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="5b3ed-924">PSReadLine op GitHub</span><span class="sxs-lookup"><span data-stu-id="5b3ed-924">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="5b3ed-925">U kunt een pull-aanvraag verzenden of feedback verzenden op de pagina GitHub.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-925">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b3ed-926">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5b3ed-926">See Also</span></span>

<span data-ttu-id="5b3ed-927">PSReadLine wordt sterk beïnvloed door de GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="5b3ed-927">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
