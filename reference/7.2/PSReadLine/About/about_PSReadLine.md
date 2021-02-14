---
description: PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over PSReadLine
ms.openlocfilehash: b0c5950b2af6a866d0ffcfdd6ce7ad92a1763778
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500209"
---
# <a name="psreadline"></a><span data-ttu-id="ad392-103">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ad392-103">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="ad392-104">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ad392-104">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="ad392-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="ad392-105">Short Description</span></span>

<span data-ttu-id="ad392-106">PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="ad392-106">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="ad392-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="ad392-107">Long Description</span></span>

<span data-ttu-id="ad392-108">PSReadLine 2,2 biedt een krachtige opdracht regel voor het bewerken van de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="ad392-108">PSReadLine 2.2 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="ad392-109">De oplossing biedt het volgende:</span><span class="sxs-lookup"><span data-stu-id="ad392-109">It provides:</span></span>

- <span data-ttu-id="ad392-110">Syntaxis kleur van de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="ad392-110">Syntax coloring of the command line</span></span>
- <span data-ttu-id="ad392-111">Een visuele indicatie van syntaxis fouten</span><span class="sxs-lookup"><span data-stu-id="ad392-111">A visual indication of syntax errors</span></span>
- <span data-ttu-id="ad392-112">Een betere ervaring met meerdere regels (zowel bewerkingen als geschiedenis)</span><span class="sxs-lookup"><span data-stu-id="ad392-112">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="ad392-113">Aanpas bare sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="ad392-113">Customizable key bindings</span></span>
- <span data-ttu-id="ad392-114">Cmd-en emacs-modi</span><span class="sxs-lookup"><span data-stu-id="ad392-114">Cmd and Emacs modes</span></span>
- <span data-ttu-id="ad392-115">Veel configuratie opties</span><span class="sxs-lookup"><span data-stu-id="ad392-115">Many configuration options</span></span>
- <span data-ttu-id="ad392-116">Bash-stijl voltooiing (optioneel in CMD-modus, standaard in Emacs-modus)</span><span class="sxs-lookup"><span data-stu-id="ad392-116">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="ad392-117">Emacs Yank/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="ad392-117">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="ad392-118">"Woord" verplaatsing en afsluiten op basis van Power shell-tokens</span><span class="sxs-lookup"><span data-stu-id="ad392-118">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="ad392-119">Voorspellende IntelliSense</span><span class="sxs-lookup"><span data-stu-id="ad392-119">Predictive IntelliSense</span></span>

<span data-ttu-id="ad392-120">PSReadLine 2.2.0 heeft twee nieuwe voorspellende IntelliSense-functies toegevoegd:</span><span class="sxs-lookup"><span data-stu-id="ad392-120">PSReadLine 2.2.0 added two new predictive IntelliSense features:</span></span>

- <span data-ttu-id="ad392-121">De para meter **PredictionViewStyle** is toegevoegd zodat de nieuwe kan worden geselecteerd `ListView` .</span><span class="sxs-lookup"><span data-stu-id="ad392-121">Added the **PredictionViewStyle** parameter to allow for the selection of the new `ListView`.</span></span>
- <span data-ttu-id="ad392-122">Verbonden PSReadLine met de `CommandPrediction` api's die in PS 7,1 zijn geïntroduceerd om een gebruiker toe te staan een Voorspellings module te importeren waarmee de suggesties van een aangepaste bron kunnen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ad392-122">Connected PSReadLine to the `CommandPrediction` APIs introduced in PS 7.1 to allow a user can import a predictor module that can render the suggestions from a custom source.</span></span>

<span data-ttu-id="ad392-123">PSReadLine vereist Power Shell 3,0 of nieuwer.</span><span class="sxs-lookup"><span data-stu-id="ad392-123">PSReadLine requires PowerShell 3.0, or newer.</span></span> <span data-ttu-id="ad392-124">PSReadLine werkt met de standaard console-host, Visual Studio code en Windows-Terminal.</span><span class="sxs-lookup"><span data-stu-id="ad392-124">PSReadLine works with default console host, Visual Studio Code, and Window Terminal.</span></span> <span data-ttu-id="ad392-125">Het werkt niet in Power shell ISE.</span><span class="sxs-lookup"><span data-stu-id="ad392-125">It does not work in PowerShell ISE.</span></span>

<span data-ttu-id="ad392-126">PSReadLine 2.2.0 wordt geleverd met Power shell 7,2 en wordt ondersteund in alle ondersteunde versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="ad392-126">PSReadLine 2.2.0 ships with PowerShell 7.2 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="ad392-127">Het is beschikbaar om te installeren via de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="ad392-127">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="ad392-128">Voer de volgende opdracht uit om PSReadLine 2.2.0 in een ondersteunde versie van Power shell te installeren.</span><span class="sxs-lookup"><span data-stu-id="ad392-128">To install PSReadLine 2.2.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> <span data-ttu-id="ad392-129">Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="ad392-129">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="ad392-130">Op dit moment werkt PSReadLine niet goed met scherm lezers.</span><span class="sxs-lookup"><span data-stu-id="ad392-130">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="ad392-131">De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="ad392-131">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="ad392-132">U kunt de module hand matig laden, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="ad392-132">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="ad392-133">Voorspellende IntelliSense</span><span class="sxs-lookup"><span data-stu-id="ad392-133">Predictive IntelliSense</span></span>

<span data-ttu-id="ad392-134">Voorspellende IntelliSense is een aanvulling op het concept van tabblad voltooiing waarmee de gebruiker wordt geholpen bij het volt ooien van opdrachten.</span><span class="sxs-lookup"><span data-stu-id="ad392-134">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="ad392-135">Hiermee kunnen gebruikers volledige opdrachten detecteren, bewerken en uitvoeren op basis van overeenkomende voor spellingen van de geschiedenis van de gebruiker en aanvullende toepassingsspecifieke invoeg toepassingen.</span><span class="sxs-lookup"><span data-stu-id="ad392-135">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="ad392-136">Voorspellende IntelliSense inschakelen</span><span class="sxs-lookup"><span data-stu-id="ad392-136">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="ad392-137">Voorspellende IntelliSense is standaard uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="ad392-137">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="ad392-138">Als u voor spellingen wilt inschakelen, voert u gewoon de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="ad392-138">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="ad392-139">De para meter **PredictionSource** kan ook invoeg toepassingen accepteren voor specifieke en aangepaste vereisten voor het domein.</span><span class="sxs-lookup"><span data-stu-id="ad392-139">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="ad392-140">Als u voorspellende IntelliSense wilt uitschakelen, voert u de volgende handelingen uit:</span><span class="sxs-lookup"><span data-stu-id="ad392-140">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="ad392-141">De volgende functies zijn beschikbaar in de klasse **[micro soft. Power shell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="ad392-141">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="ad392-142">Basis bewerkings functies</span><span class="sxs-lookup"><span data-stu-id="ad392-142">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="ad392-143">Afbreken</span><span class="sxs-lookup"><span data-stu-id="ad392-143">Abort</span></span>

<span data-ttu-id="ad392-144">De huidige actie afbreken, bijvoorbeeld een incrementele geschiedenis zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="ad392-144">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="ad392-145">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="ad392-145">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="ad392-146">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="ad392-146">AcceptAndGetNext</span></span>

<span data-ttu-id="ad392-147">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="ad392-147">Attempt to execute the current input.</span></span> <span data-ttu-id="ad392-148">Als deze kan worden uitgevoerd (zoals AcceptLine), kunt u het volgende item uit de geschiedenis intrekken de volgende keer dat ReadLine wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="ad392-148">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="ad392-149">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="ad392-149">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="ad392-150">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="ad392-150">AcceptLine</span></span>

<span data-ttu-id="ad392-151">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="ad392-151">Attempt to execute the current input.</span></span> <span data-ttu-id="ad392-152">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="ad392-152">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="ad392-153">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ad392-153">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="ad392-154">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ad392-154">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="ad392-155">VI Invoeg modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ad392-155">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="ad392-156">AddLine</span><span class="sxs-lookup"><span data-stu-id="ad392-156">AddLine</span></span>

<span data-ttu-id="ad392-157">De vervolg prompt wordt weer gegeven op de volgende regel en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="ad392-157">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="ad392-158">Dit is handig om invoer in meerdere regels als één opdracht in te voeren, zelfs wanneer één regel volledig wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="ad392-158">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="ad392-159">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ad392-159">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="ad392-160">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ad392-160">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="ad392-161">VI Invoeg modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ad392-161">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="ad392-162">VI-opdracht modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ad392-162">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="ad392-163">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="ad392-163">BackwardDeleteChar</span></span>

<span data-ttu-id="ad392-164">Verwijder het teken voor de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-164">Delete the character before the cursor.</span></span>

- <span data-ttu-id="ad392-165">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="ad392-165">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="ad392-166">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="ad392-166">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="ad392-167">VI Invoeg modus: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ad392-167">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="ad392-168">VI-opdracht modus: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="ad392-168">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="ad392-169">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="ad392-169">BackwardDeleteLine</span></span>

<span data-ttu-id="ad392-170">Net als BackwardKillLine: verwijdert tekst van het punt naar het begin van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="ad392-170">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="ad392-171">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="ad392-171">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="ad392-172">VI Invoeg modus: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="ad392-172">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="ad392-173">VI-opdracht modus: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="ad392-173">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="ad392-174">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="ad392-174">BackwardDeleteWord</span></span>

<span data-ttu-id="ad392-175">Hiermee verwijdert u het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-175">Deletes the previous word.</span></span>

- <span data-ttu-id="ad392-176">VI-opdracht modus: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="ad392-176">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="ad392-177">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="ad392-177">BackwardKillLine</span></span>

<span data-ttu-id="ad392-178">De invoer van het begin van de invoer wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-178">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="ad392-179">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="ad392-179">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ad392-180">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ad392-180">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="ad392-181">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="ad392-181">BackwardKillWord</span></span>

<span data-ttu-id="ad392-182">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-182">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="ad392-183">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="ad392-183">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="ad392-184">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="ad392-184">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ad392-185">Cmd: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="ad392-185">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="ad392-186">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ad392-186">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="ad392-187">VI Invoeg modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ad392-187">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="ad392-188">VI-opdracht modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ad392-188">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="ad392-189">CancelLine</span><span class="sxs-lookup"><span data-stu-id="ad392-189">CancelLine</span></span>

<span data-ttu-id="ad392-190">De huidige invoer annuleren, waardoor de invoer op het scherm wordt weer gegeven, maar terugkeert naar de host, zodat de prompt opnieuw wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="ad392-190">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="ad392-191">VI Invoeg modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ad392-191">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="ad392-192">VI-opdracht modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ad392-192">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="ad392-193">Kopiëren</span><span class="sxs-lookup"><span data-stu-id="ad392-193">Copy</span></span>

<span data-ttu-id="ad392-194">Kopieer de geselecteerde regio naar het klem bord van het systeem.</span><span class="sxs-lookup"><span data-stu-id="ad392-194">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="ad392-195">Als er geen regio is geselecteerd, kopieert u de hele regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-195">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="ad392-196">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="ad392-196">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="ad392-197">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="ad392-197">CopyOrCancelLine</span></span>

<span data-ttu-id="ad392-198">Als tekst is geselecteerd, kopieert u deze naar het klem bord. anders annuleert u de regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-198">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="ad392-199">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ad392-199">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="ad392-200">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ad392-200">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="ad392-201">Knippen</span><span class="sxs-lookup"><span data-stu-id="ad392-201">Cut</span></span>

<span data-ttu-id="ad392-202">Geselecteerde regio verwijderen Verwijderde tekst in het systeem Klembord plaatsen.</span><span class="sxs-lookup"><span data-stu-id="ad392-202">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="ad392-203">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="ad392-203">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="ad392-204">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="ad392-204">DeleteChar</span></span>

<span data-ttu-id="ad392-205">Verwijder het teken onder de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-205">Delete the character under the cursor.</span></span>

- <span data-ttu-id="ad392-206">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="ad392-206">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="ad392-207">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="ad392-207">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="ad392-208">VI Invoeg modus: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="ad392-208">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="ad392-209">VI-opdracht modus: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="ad392-209">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="ad392-210">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="ad392-210">DeleteCharOrExit</span></span>

<span data-ttu-id="ad392-211">Verwijder het teken onder de cursor of als de regel leeg is, sluit u het proces.</span><span class="sxs-lookup"><span data-stu-id="ad392-211">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="ad392-212">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="ad392-212">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="ad392-213">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="ad392-213">DeleteEndOfBuffer</span></span>

<span data-ttu-id="ad392-214">Hiermee verwijdert u aan het einde van de buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="ad392-214">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="ad392-215">VI-opdracht modus: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="ad392-215">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="ad392-216">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="ad392-216">DeleteEndOfWord</span></span>

<span data-ttu-id="ad392-217">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-217">Delete to the end of the word.</span></span>

- <span data-ttu-id="ad392-218">VI-opdracht modus: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="ad392-218">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="ad392-219">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="ad392-219">DeleteLine</span></span>

<span data-ttu-id="ad392-220">Hiermee verwijdert u de huidige logische lijn van een buffer voor meerdere regels, waarbij u ongedaan maken inschakelt.</span><span class="sxs-lookup"><span data-stu-id="ad392-220">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="ad392-221">VI-opdracht modus: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="ad392-221">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="ad392-222">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="ad392-222">DeletePreviousLines</span></span>

<span data-ttu-id="ad392-223">Hiermee verwijdert u de vorige aangevraagde logische regels en de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="ad392-223">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="ad392-224">VI-opdracht modus: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="ad392-224">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="ad392-225">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="ad392-225">DeleteRelativeLines</span></span>

<span data-ttu-id="ad392-226">Verwijdert uit het begin van de buffer naar de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="ad392-226">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="ad392-227">De meeste MS-DOS-opdrachten `<d,g,g>` kunnen worden voorafgegaan door een numeriek argument waarmee een absoluut regel nummer wordt opgegeven, samen met het huidige regel nummer, een bereik aan regels maken dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ad392-227">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="ad392-228">Als u niets opgeeft, wordt het numerieke argument standaard ingesteld op 1, dat verwijst naar de eerste logische lijn in een buffer met meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="ad392-228">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="ad392-229">Het werkelijke aantal regels dat uit de meerregelige moet worden verwijderd, wordt berekend als het verschil tussen het huidige logische regel nummer en het opgegeven numerieke argument. Dit kan dus negatief zijn.</span><span class="sxs-lookup"><span data-stu-id="ad392-229">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="ad392-230">Daarom is het _relatieve_ deel van de methode naam.</span><span class="sxs-lookup"><span data-stu-id="ad392-230">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="ad392-231">VI-opdracht modus: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="ad392-231">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="ad392-232">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="ad392-232">DeleteNextLines</span></span>

<span data-ttu-id="ad392-233">Hiermee verwijdert u de huidige logische lijn en de volgende aangevraagde logische regels in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="ad392-233">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="ad392-234">VI-opdracht modus: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="ad392-234">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="ad392-235">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="ad392-235">DeleteLineToFirstChar</span></span>

<span data-ttu-id="ad392-236">Verwijdert uit het eerste niet-lege teken van de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="ad392-236">Deletes from the first non-blank character of the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="ad392-237">VI-opdracht modus: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="ad392-237">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="ad392-238">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="ad392-238">DeleteToEnd</span></span>

<span data-ttu-id="ad392-239">Verwijderen tot aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-239">Delete to the end of the line.</span></span>

- <span data-ttu-id="ad392-240">VI-opdracht modus: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="ad392-240">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="ad392-241">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="ad392-241">DeleteWord</span></span>

<span data-ttu-id="ad392-242">Verwijder het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-242">Delete the next word.</span></span>

- <span data-ttu-id="ad392-243">VI-opdracht modus: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="ad392-243">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="ad392-244">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="ad392-244">ForwardDeleteLine</span></span>

<span data-ttu-id="ad392-245">Net als ForwardKillLine: verwijdert tekst van het punt naar het einde van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="ad392-245">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="ad392-246">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ad392-246">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="ad392-247">VI Invoeg modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ad392-247">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="ad392-248">VI-opdracht modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ad392-248">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="ad392-249">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="ad392-249">InsertLineAbove</span></span>

<span data-ttu-id="ad392-250">Er wordt een nieuwe lege regel gemaakt op de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="ad392-250">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="ad392-251">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-251">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="ad392-252">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ad392-252">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="ad392-253">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="ad392-253">InsertLineBelow</span></span>

<span data-ttu-id="ad392-254">Er wordt een nieuwe lege regel gemaakt onder de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="ad392-254">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="ad392-255">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-255">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="ad392-256">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ad392-256">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="ad392-257">InvertCase</span><span class="sxs-lookup"><span data-stu-id="ad392-257">InvertCase</span></span>

<span data-ttu-id="ad392-258">Het hoofdletter gebruik van het huidige teken omkeren en verplaatsen naar het volgende.</span><span class="sxs-lookup"><span data-stu-id="ad392-258">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="ad392-259">VI-opdracht modus: `<~>`</span><span class="sxs-lookup"><span data-stu-id="ad392-259">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="ad392-260">KillLine</span><span class="sxs-lookup"><span data-stu-id="ad392-260">KillLine</span></span>

<span data-ttu-id="ad392-261">De invoer wissen van de cursor tot het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="ad392-261">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="ad392-262">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="ad392-262">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ad392-263">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="ad392-263">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="ad392-264">KillRegion</span><span class="sxs-lookup"><span data-stu-id="ad392-264">KillRegion</span></span>

<span data-ttu-id="ad392-265">Beëindig de tekst tussen de cursor en de markering.</span><span class="sxs-lookup"><span data-stu-id="ad392-265">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="ad392-266">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-266">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="ad392-267">KillWord</span><span class="sxs-lookup"><span data-stu-id="ad392-267">KillWord</span></span>

<span data-ttu-id="ad392-268">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-268">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="ad392-269">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-269">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="ad392-270">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="ad392-270">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ad392-271">Cmd: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="ad392-271">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="ad392-272">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="ad392-272">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="ad392-273">VI Invoeg modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="ad392-273">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="ad392-274">VI-opdracht modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="ad392-274">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="ad392-275">Plakken</span><span class="sxs-lookup"><span data-stu-id="ad392-275">Paste</span></span>

<span data-ttu-id="ad392-276">Tekst van het klem bord van het systeem plakken.</span><span class="sxs-lookup"><span data-stu-id="ad392-276">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="ad392-277">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="ad392-277">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="ad392-278">VI Invoeg modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="ad392-278">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="ad392-279">VI-opdracht modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="ad392-279">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad392-280">Wanneer u de functie **Paste** gebruikt, wordt de volledige inhoud van de Klembord buffer geplakt in de invoer buffer van PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ad392-280">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="ad392-281">De invoer buffer wordt vervolgens door gegeven aan de Power shell-parser.</span><span class="sxs-lookup"><span data-stu-id="ad392-281">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="ad392-282">Invoer die met de **rechter muisknop op** de plak methode van de console toepassing wordt geplakt, wordt met één teken per keer naar de invoer buffer gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="ad392-282">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="ad392-283">De invoer buffer wordt door gegeven aan de parser wanneer een teken voor een nieuwe regel wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="ad392-283">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="ad392-284">Daarom wordt de invoer één regel tegelijk geparseerd.</span><span class="sxs-lookup"><span data-stu-id="ad392-284">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="ad392-285">Het verschil tussen plak methoden resulteert in een ander uitvoerings gedrag.</span><span class="sxs-lookup"><span data-stu-id="ad392-285">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="ad392-286">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="ad392-286">PasteAfter</span></span>

<span data-ttu-id="ad392-287">Plak het klem bord na de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="ad392-287">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="ad392-288">VI-opdracht modus: `<p>`</span><span class="sxs-lookup"><span data-stu-id="ad392-288">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="ad392-289">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="ad392-289">PasteBefore</span></span>

<span data-ttu-id="ad392-290">Plak het klem bord vóór de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="ad392-290">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="ad392-291">VI-opdracht modus: `<P>`</span><span class="sxs-lookup"><span data-stu-id="ad392-291">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="ad392-292">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="ad392-292">PrependAndAccept</span></span>

<span data-ttu-id="ad392-293">Laten voorafgaan door een ' # ' en accepteer de regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-293">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="ad392-294">VI-opdracht modus: `<#>`</span><span class="sxs-lookup"><span data-stu-id="ad392-294">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="ad392-295">Opnieuw uitvoeren</span><span class="sxs-lookup"><span data-stu-id="ad392-295">Redo</span></span>

<span data-ttu-id="ad392-296">Undo ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="ad392-296">Undo an undo.</span></span>

- <span data-ttu-id="ad392-297">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ad392-297">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="ad392-298">VI Invoeg modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ad392-298">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="ad392-299">VI-opdracht modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ad392-299">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="ad392-300">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="ad392-300">RepeatLastCommand</span></span>

<span data-ttu-id="ad392-301">Herhaal de laatste tekst wijziging.</span><span class="sxs-lookup"><span data-stu-id="ad392-301">Repeat the last text modification.</span></span>

- <span data-ttu-id="ad392-302">VI-opdracht modus: `<.>`</span><span class="sxs-lookup"><span data-stu-id="ad392-302">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="ad392-303">RevertLine</span><span class="sxs-lookup"><span data-stu-id="ad392-303">RevertLine</span></span>

<span data-ttu-id="ad392-304">Hiermee wordt alle invoer teruggezet naar de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="ad392-304">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="ad392-305">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="ad392-305">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="ad392-306">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="ad392-306">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="ad392-307">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="ad392-307">ShellBackwardKillWord</span></span>

<span data-ttu-id="ad392-308">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-308">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="ad392-309">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="ad392-309">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="ad392-310">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="ad392-310">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="ad392-311">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-311">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="ad392-312">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="ad392-312">ShellKillWord</span></span>

<span data-ttu-id="ad392-313">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-313">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="ad392-314">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-314">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="ad392-315">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="ad392-315">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="ad392-316">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-316">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="ad392-317">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="ad392-317">SwapCharacters</span></span>

<span data-ttu-id="ad392-318">Het huidige teken en de eerste vervangen door wisselen.</span><span class="sxs-lookup"><span data-stu-id="ad392-318">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="ad392-319">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="ad392-319">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="ad392-320">VI Invoeg modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="ad392-320">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="ad392-321">VI-opdracht modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="ad392-321">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="ad392-322">Ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="ad392-322">Undo</span></span>

<span data-ttu-id="ad392-323">Een vorige bewerking ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="ad392-323">Undo a previous edit.</span></span>

- <span data-ttu-id="ad392-324">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="ad392-324">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="ad392-325">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="ad392-325">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="ad392-326">VI Invoeg modus: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="ad392-326">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="ad392-327">VI-opdracht modus: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="ad392-327">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="ad392-328">UndoAll</span><span class="sxs-lookup"><span data-stu-id="ad392-328">UndoAll</span></span>

<span data-ttu-id="ad392-329">Alle vorige bewerkingen voor de regel ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="ad392-329">Undo all previous edits for line.</span></span>

- <span data-ttu-id="ad392-330">VI-opdracht modus: `<U>`</span><span class="sxs-lookup"><span data-stu-id="ad392-330">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="ad392-331">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="ad392-331">UnixWordRubout</span></span>

<span data-ttu-id="ad392-332">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-332">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="ad392-333">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="ad392-333">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="ad392-334">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="ad392-334">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ad392-335">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="ad392-335">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="ad392-336">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="ad392-336">ValidateAndAcceptLine</span></span>

<span data-ttu-id="ad392-337">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="ad392-337">Attempt to execute the current input.</span></span> <span data-ttu-id="ad392-338">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="ad392-338">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="ad392-339">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="ad392-339">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="ad392-340">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="ad392-340">ViAcceptLine</span></span>

<span data-ttu-id="ad392-341">Accepteer de regel en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="ad392-341">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="ad392-342">VI-opdracht modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ad392-342">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="ad392-343">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="ad392-343">ViAcceptLineOrExit</span></span>

<span data-ttu-id="ad392-344">Als DeleteCharOrExit in de Emacs-modus, maar wel in plaats van een teken te verwijderen, accepteert u de regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-344">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="ad392-345">VI Invoeg modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="ad392-345">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="ad392-346">VI-opdracht modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="ad392-346">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="ad392-347">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="ad392-347">ViAppendLine</span></span>

<span data-ttu-id="ad392-348">Er wordt een nieuwe regel ingevoegd onder de huidige regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-348">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="ad392-349">VI-opdracht modus: `<o>`</span><span class="sxs-lookup"><span data-stu-id="ad392-349">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="ad392-350">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="ad392-350">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="ad392-351">Hiermee verwijdert u het vorige woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-351">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="ad392-352">VI-opdracht modus: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="ad392-352">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="ad392-353">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="ad392-353">ViBackwardGlob</span></span>

<span data-ttu-id="ad392-354">Verplaatst de cursor terug naar het begin van het vorige woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ad392-354">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="ad392-355">VI-opdracht modus: `<B>`</span><span class="sxs-lookup"><span data-stu-id="ad392-355">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="ad392-356">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="ad392-356">ViDeleteBrace</span></span>

<span data-ttu-id="ad392-357">Zoek de accolade, het haakje sluiten of de vier Kante haken en verwijder alle inhoud binnen, inclusief de accolade.</span><span class="sxs-lookup"><span data-stu-id="ad392-357">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="ad392-358">VI-opdracht modus: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="ad392-358">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="ad392-359">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="ad392-359">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="ad392-360">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-360">Delete to the end of the word.</span></span>

- <span data-ttu-id="ad392-361">VI-opdracht modus: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="ad392-361">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="ad392-362">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="ad392-362">ViDeleteGlob</span></span>

<span data-ttu-id="ad392-363">De volgende Globs verwijderen (door witruimte gescheiden woord).</span><span class="sxs-lookup"><span data-stu-id="ad392-363">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="ad392-364">VI-opdracht modus: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="ad392-364">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="ad392-365">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="ad392-365">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="ad392-366">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-366">Deletes until given character.</span></span>

- <span data-ttu-id="ad392-367">VI-opdracht modus: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="ad392-367">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="ad392-368">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="ad392-368">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="ad392-369">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-369">Deletes until given character.</span></span>

- <span data-ttu-id="ad392-370">VI-opdracht modus: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="ad392-370">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="ad392-371">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="ad392-371">ViDeleteToChar</span></span>

<span data-ttu-id="ad392-372">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-372">Deletes until given character.</span></span>

- <span data-ttu-id="ad392-373">VI-opdracht modus: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="ad392-373">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="ad392-374">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="ad392-374">ViDeleteToCharBackward</span></span>

<span data-ttu-id="ad392-375">Hiermee verwijdert u achterwaartse tekens tot aan het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-375">Deletes backwards until given character.</span></span>

- <span data-ttu-id="ad392-376">VI-opdracht modus: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="ad392-376">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="ad392-377">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="ad392-377">ViInsertAtBegining</span></span>

<span data-ttu-id="ad392-378">Schakel over naar de Invoeg modus en plaats de cursor aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-378">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="ad392-379">VI-opdracht modus: `<I>`</span><span class="sxs-lookup"><span data-stu-id="ad392-379">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="ad392-380">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="ad392-380">ViInsertAtEnd</span></span>

<span data-ttu-id="ad392-381">Schakel over naar de Invoeg modus en plaats de cursor aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-381">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="ad392-382">VI-opdracht modus: `<A>`</span><span class="sxs-lookup"><span data-stu-id="ad392-382">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="ad392-383">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="ad392-383">ViInsertLine</span></span>

<span data-ttu-id="ad392-384">Boven de huidige regel wordt een nieuwe regel ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="ad392-384">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="ad392-385">VI-opdracht modus: `<O>`</span><span class="sxs-lookup"><span data-stu-id="ad392-385">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="ad392-386">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="ad392-386">ViInsertWithAppend</span></span>

<span data-ttu-id="ad392-387">Toevoegen vanaf de huidige regel positie.</span><span class="sxs-lookup"><span data-stu-id="ad392-387">Append from the current line position.</span></span>

- <span data-ttu-id="ad392-388">VI-opdracht modus: `<a>`</span><span class="sxs-lookup"><span data-stu-id="ad392-388">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="ad392-389">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="ad392-389">ViInsertWithDelete</span></span>

<span data-ttu-id="ad392-390">Verwijder het huidige teken en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="ad392-390">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="ad392-391">VI-opdracht modus: `<s>`</span><span class="sxs-lookup"><span data-stu-id="ad392-391">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="ad392-392">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="ad392-392">ViJoinLines</span></span>

<span data-ttu-id="ad392-393">De huidige regel en de volgende regel worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="ad392-393">Joins the current line and the next line.</span></span>

- <span data-ttu-id="ad392-394">VI-opdracht modus: `<J>`</span><span class="sxs-lookup"><span data-stu-id="ad392-394">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="ad392-395">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="ad392-395">ViReplaceLine</span></span>

<span data-ttu-id="ad392-396">De volledige opdracht regel wissen.</span><span class="sxs-lookup"><span data-stu-id="ad392-396">Erase the entire command line.</span></span>

- <span data-ttu-id="ad392-397">VI-opdracht modus: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="ad392-397">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="ad392-398">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="ad392-398">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="ad392-399">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-399">Replaces until given character.</span></span>

- <span data-ttu-id="ad392-400">VI-opdracht modus: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="ad392-400">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="ad392-401">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="ad392-401">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="ad392-402">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-402">Replaces until given character.</span></span>

- <span data-ttu-id="ad392-403">VI-opdracht modus: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="ad392-403">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="ad392-404">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="ad392-404">ViReplaceToChar</span></span>

<span data-ttu-id="ad392-405">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-405">Deletes until given character.</span></span>

- <span data-ttu-id="ad392-406">VI-opdracht modus: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="ad392-406">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="ad392-407">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="ad392-407">ViReplaceToCharBackward</span></span>

<span data-ttu-id="ad392-408">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-408">Replaces until given character.</span></span>

- <span data-ttu-id="ad392-409">VI-opdracht modus: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="ad392-409">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="ad392-410">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="ad392-410">ViYankBeginningOfLine</span></span>

<span data-ttu-id="ad392-411">Yank vanaf het begin van de buffer naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-411">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="ad392-412">VI-opdracht modus: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="ad392-412">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="ad392-413">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="ad392-413">ViYankEndOfGlob</span></span>

<span data-ttu-id="ad392-414">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="ad392-414">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="ad392-415">VI-opdracht modus: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="ad392-415">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="ad392-416">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="ad392-416">ViYankEndOfWord</span></span>

<span data-ttu-id="ad392-417">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="ad392-417">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="ad392-418">VI-opdracht modus: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="ad392-418">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="ad392-419">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="ad392-419">ViYankLeft</span></span>

<span data-ttu-id="ad392-420">Yank teken (s) links van de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-420">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="ad392-421">VI-opdracht modus: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="ad392-421">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="ad392-422">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="ad392-422">ViYankLine</span></span>

<span data-ttu-id="ad392-423">Yank de volledige buffer.</span><span class="sxs-lookup"><span data-stu-id="ad392-423">Yank the entire buffer.</span></span>

- <span data-ttu-id="ad392-424">VI-opdracht modus: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="ad392-424">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="ad392-425">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="ad392-425">ViYankNextGlob</span></span>

<span data-ttu-id="ad392-426">Yank van de cursor naar het begin van de volgende woord (en).</span><span class="sxs-lookup"><span data-stu-id="ad392-426">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="ad392-427">VI-opdracht modus: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="ad392-427">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="ad392-428">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="ad392-428">ViYankNextWord</span></span>

<span data-ttu-id="ad392-429">Yank het woord (en) na de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-429">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="ad392-430">VI-opdracht modus: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="ad392-430">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="ad392-431">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="ad392-431">ViYankPercent</span></span>

<span data-ttu-id="ad392-432">Yank naar/van overeenkomende accolade.</span><span class="sxs-lookup"><span data-stu-id="ad392-432">Yank to/from matching brace.</span></span>

- <span data-ttu-id="ad392-433">VI-opdracht modus: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="ad392-433">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="ad392-434">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="ad392-434">ViYankPreviousGlob</span></span>

<span data-ttu-id="ad392-435">Yank vanaf het begin van het (de) woord (en) tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-435">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="ad392-436">VI-opdracht modus: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="ad392-436">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="ad392-437">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="ad392-437">ViYankPreviousWord</span></span>

<span data-ttu-id="ad392-438">Yank de woorden vóór de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-438">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="ad392-439">VI-opdracht modus: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="ad392-439">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="ad392-440">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="ad392-440">ViYankRight</span></span>

<span data-ttu-id="ad392-441">Yank teken (s) onder en rechts van de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-441">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="ad392-442">VI-opdracht modus: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="ad392-442">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="ad392-443">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="ad392-443">ViYankToEndOfLine</span></span>

<span data-ttu-id="ad392-444">Yank van de cursor tot het einde van de buffer.</span><span class="sxs-lookup"><span data-stu-id="ad392-444">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="ad392-445">VI-opdracht modus: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="ad392-445">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="ad392-446">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="ad392-446">ViYankToFirstChar</span></span>

<span data-ttu-id="ad392-447">Yank van het eerste niet-spatie teken tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-447">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="ad392-448">VI-opdracht modus: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="ad392-448">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="ad392-449">Yank</span><span class="sxs-lookup"><span data-stu-id="ad392-449">Yank</span></span>

<span data-ttu-id="ad392-450">Voeg de meest recent afgebroken tekst toe aan de invoer.</span><span class="sxs-lookup"><span data-stu-id="ad392-450">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="ad392-451">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ad392-451">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="ad392-452">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="ad392-452">YankLastArg</span></span>

<span data-ttu-id="ad392-453">Yank het laatste argument van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-453">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="ad392-454">Met een argument, de eerste keer dat deze wordt aangeroepen, gedraagt zich op dezelfde manier als YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="ad392-454">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="ad392-455">Als meerdere keren worden aangeroepen, wordt door de geschiedenis en ARG de richting ingesteld (negatief de richting omkeren.)</span><span class="sxs-lookup"><span data-stu-id="ad392-455">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="ad392-456">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="ad392-456">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="ad392-457">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="ad392-457">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="ad392-458">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="ad392-458">YankNthArg</span></span>

<span data-ttu-id="ad392-459">Yank het eerste argument (na de opdracht) van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-459">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="ad392-460">Met een argument, Yank het ne argument (vanaf 0), als het argument negatief is, begint vanaf het laatste argument.</span><span class="sxs-lookup"><span data-stu-id="ad392-460">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="ad392-461">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ad392-461">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="ad392-462">YankPop</span><span class="sxs-lookup"><span data-stu-id="ad392-462">YankPop</span></span>

<span data-ttu-id="ad392-463">Als de vorige bewerking Yank of YankPop is, vervangt u de eerder yanked tekst door de volgende afgebroken tekst van de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="ad392-463">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="ad392-464">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="ad392-464">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="ad392-465">Functies voor cursor verplaatsing</span><span class="sxs-lookup"><span data-stu-id="ad392-465">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="ad392-466">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="ad392-466">BackwardChar</span></span>

<span data-ttu-id="ad392-467">De cursor één teken naar links verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="ad392-467">Move the cursor one character to the left.</span></span> <span data-ttu-id="ad392-468">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="ad392-468">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="ad392-469">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-469">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="ad392-470">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="ad392-470">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="ad392-471">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="ad392-471">BackwardWord</span></span>

<span data-ttu-id="ad392-472">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-472">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="ad392-473">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="ad392-473">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ad392-474">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-474">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="ad392-475">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="ad392-475">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="ad392-476">VI Invoeg modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-476">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="ad392-477">VI-opdracht modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-477">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="ad392-478">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="ad392-478">BeginningOfLine</span></span>

<span data-ttu-id="ad392-479">Als de invoer meerdere regels heeft, gaat u naar het begin van de huidige regel of gaat u naar het begin van de invoer als deze al aan het begin van de regel staat.</span><span class="sxs-lookup"><span data-stu-id="ad392-479">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="ad392-480">Als de invoer één regel heeft, gaat u naar het begin van de invoer.</span><span class="sxs-lookup"><span data-stu-id="ad392-480">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="ad392-481">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="ad392-481">Cmd: `<Home>`</span></span>
- <span data-ttu-id="ad392-482">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="ad392-482">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="ad392-483">VI Invoeg modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="ad392-483">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="ad392-484">VI-opdracht modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="ad392-484">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="ad392-485">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="ad392-485">EndOfLine</span></span>

<span data-ttu-id="ad392-486">Als de invoer meerdere regels heeft, gaat u naar het einde van de huidige regel of gaat u naar het einde van de invoer als u aan het einde van de regel bent.</span><span class="sxs-lookup"><span data-stu-id="ad392-486">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="ad392-487">Als de invoer één regel heeft, gaat u naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="ad392-487">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="ad392-488">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="ad392-488">Cmd: `<End>`</span></span>
- <span data-ttu-id="ad392-489">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="ad392-489">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="ad392-490">VI Invoeg modus: `<End>`</span><span class="sxs-lookup"><span data-stu-id="ad392-490">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="ad392-491">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="ad392-491">ForwardChar</span></span>

<span data-ttu-id="ad392-492">De cursor één teken naar rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="ad392-492">Move the cursor one character to the right.</span></span> <span data-ttu-id="ad392-493">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="ad392-493">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="ad392-494">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-494">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="ad392-495">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="ad392-495">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="ad392-496">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="ad392-496">ForwardWord</span></span>

<span data-ttu-id="ad392-497">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-497">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="ad392-498">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="ad392-498">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ad392-499">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="ad392-499">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="ad392-500">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="ad392-500">GotoBrace</span></span>

<span data-ttu-id="ad392-501">Ga naar de accolade, haakjes of vier Kante haakjes.</span><span class="sxs-lookup"><span data-stu-id="ad392-501">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="ad392-502">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ad392-502">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="ad392-503">VI Invoeg modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ad392-503">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="ad392-504">VI-opdracht modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ad392-504">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="ad392-505">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="ad392-505">GotoColumn</span></span>

<span data-ttu-id="ad392-506">Ga naar de kolom die wordt aangegeven door arg.</span><span class="sxs-lookup"><span data-stu-id="ad392-506">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="ad392-507">VI-opdracht modus: `<|>`</span><span class="sxs-lookup"><span data-stu-id="ad392-507">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="ad392-508">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="ad392-508">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="ad392-509">De cursor verplaatsen naar het eerste niet-lege teken in de regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-509">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="ad392-510">VI-opdracht modus: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="ad392-510">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="ad392-511">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="ad392-511">MoveToEndOfLine</span></span>

<span data-ttu-id="ad392-512">De cursor verplaatsen naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="ad392-512">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="ad392-513">VI-opdracht modus: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="ad392-513">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="ad392-514">NextLine</span><span class="sxs-lookup"><span data-stu-id="ad392-514">NextLine</span></span>

<span data-ttu-id="ad392-515">De cursor verplaatsen naar de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-515">Move the cursor to the next line.</span></span>

- <span data-ttu-id="ad392-516">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-516">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="ad392-517">NextWord</span><span class="sxs-lookup"><span data-stu-id="ad392-517">NextWord</span></span>

<span data-ttu-id="ad392-518">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-518">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="ad392-519">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="ad392-519">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ad392-520">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-520">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="ad392-521">VI Invoeg modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-521">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="ad392-522">VI-opdracht modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-522">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="ad392-523">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="ad392-523">NextWordEnd</span></span>

<span data-ttu-id="ad392-524">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-524">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="ad392-525">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="ad392-525">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ad392-526">VI-opdracht modus: `<e>`</span><span class="sxs-lookup"><span data-stu-id="ad392-526">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="ad392-527">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="ad392-527">PreviousLine</span></span>

<span data-ttu-id="ad392-528">Verplaats de cursor naar de vorige regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-528">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="ad392-529">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-529">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="ad392-530">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ad392-530">ShellBackwardWord</span></span>

<span data-ttu-id="ad392-531">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-531">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="ad392-532">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="ad392-532">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="ad392-533">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-533">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="ad392-534">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="ad392-534">ShellForwardWord</span></span>

<span data-ttu-id="ad392-535">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-535">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="ad392-536">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="ad392-536">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="ad392-537">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-537">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="ad392-538">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="ad392-538">ShellNextWord</span></span>

<span data-ttu-id="ad392-539">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-539">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="ad392-540">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="ad392-540">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="ad392-541">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-541">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="ad392-542">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="ad392-542">ViBackwardChar</span></span>

<span data-ttu-id="ad392-543">De cursor één teken naar links verplaatsen in de bewerkings modus VI.</span><span class="sxs-lookup"><span data-stu-id="ad392-543">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="ad392-544">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="ad392-544">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="ad392-545">VI Invoeg modus: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-545">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="ad392-546">VI-opdracht modus: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="ad392-546">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="ad392-547">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ad392-547">ViBackwardWord</span></span>

<span data-ttu-id="ad392-548">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-548">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="ad392-549">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="ad392-549">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ad392-550">VI-opdracht modus: `<b>`</span><span class="sxs-lookup"><span data-stu-id="ad392-550">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="ad392-551">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="ad392-551">ViForwardChar</span></span>

<span data-ttu-id="ad392-552">De cursor één teken naar rechts verplaatsen in de bewerkings modus VI.</span><span class="sxs-lookup"><span data-stu-id="ad392-552">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="ad392-553">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="ad392-553">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="ad392-554">VI Invoeg modus: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-554">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="ad392-555">VI-opdracht modus: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="ad392-555">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="ad392-556">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="ad392-556">ViEndOfGlob</span></span>

<span data-ttu-id="ad392-557">Verplaatst de cursor naar het einde van het woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ad392-557">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="ad392-558">VI-opdracht modus: `<E>`</span><span class="sxs-lookup"><span data-stu-id="ad392-558">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="ad392-559">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="ad392-559">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="ad392-560">Wordt verplaatst naar het einde van het vorige woord, waarbij alleen witruimte wordt gebruikt als woord als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-560">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="ad392-561">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-561">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="ad392-562">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="ad392-562">ViGotoBrace</span></span>

<span data-ttu-id="ad392-563">Vergelijkbaar met GotoBrace, maar is in plaats van op tokens gebaseerd.</span><span class="sxs-lookup"><span data-stu-id="ad392-563">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="ad392-564">VI-opdracht modus: `<%>`</span><span class="sxs-lookup"><span data-stu-id="ad392-564">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="ad392-565">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="ad392-565">ViNextGlob</span></span>

<span data-ttu-id="ad392-566">Verplaatst naar het volgende woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-566">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="ad392-567">VI-opdracht modus: `<W>`</span><span class="sxs-lookup"><span data-stu-id="ad392-567">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="ad392-568">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="ad392-568">ViNextWord</span></span>

<span data-ttu-id="ad392-569">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="ad392-569">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="ad392-570">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="ad392-570">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ad392-571">VI-opdracht modus: `<w>`</span><span class="sxs-lookup"><span data-stu-id="ad392-571">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="ad392-572">Geschiedenis functies</span><span class="sxs-lookup"><span data-stu-id="ad392-572">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="ad392-573">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="ad392-573">BeginningOfHistory</span></span>

<span data-ttu-id="ad392-574">Hiermee gaat u naar het eerste item in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="ad392-574">Move to the first item in the history.</span></span>

- <span data-ttu-id="ad392-575">Emacs: `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="ad392-575">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="ad392-576">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="ad392-576">ClearHistory</span></span>

<span data-ttu-id="ad392-577">Hiermee wist u de geschiedenis in PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ad392-577">Clears history in PSReadLine.</span></span> <span data-ttu-id="ad392-578">Dit heeft geen invloed op de Power shell-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="ad392-578">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="ad392-579">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="ad392-579">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="ad392-580">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="ad392-580">EndOfHistory</span></span>

<span data-ttu-id="ad392-581">Hiermee gaat u naar het laatste item (de huidige invoer) in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="ad392-581">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="ad392-582">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="ad392-582">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="ad392-583">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="ad392-583">ForwardSearchHistory</span></span>

<span data-ttu-id="ad392-584">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="ad392-584">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="ad392-585">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ad392-585">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="ad392-586">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ad392-586">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="ad392-587">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="ad392-587">HistorySearchBackward</span></span>

<span data-ttu-id="ad392-588">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-588">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="ad392-589">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="ad392-589">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="ad392-590">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="ad392-590">HistorySearchForward</span></span>

<span data-ttu-id="ad392-591">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-591">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="ad392-592">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="ad392-592">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="ad392-593">NextHistory</span><span class="sxs-lookup"><span data-stu-id="ad392-593">NextHistory</span></span>

<span data-ttu-id="ad392-594">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="ad392-594">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="ad392-595">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-595">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="ad392-596">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="ad392-596">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="ad392-597">VI Invoeg modus: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-597">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="ad392-598">VI-opdracht modus: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="ad392-598">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="ad392-599">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="ad392-599">PreviousHistory</span></span>

<span data-ttu-id="ad392-600">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="ad392-600">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="ad392-601">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-601">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="ad392-602">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="ad392-602">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="ad392-603">VI Invoeg modus: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-603">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="ad392-604">VI-opdracht modus: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="ad392-604">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="ad392-605">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="ad392-605">ReverseSearchHistory</span></span>

<span data-ttu-id="ad392-606">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="ad392-606">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="ad392-607">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ad392-607">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="ad392-608">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ad392-608">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="ad392-609">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="ad392-609">ViSearchHistoryBackward</span></span>

<span data-ttu-id="ad392-610">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="ad392-610">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="ad392-611">VI Invoeg modus: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ad392-611">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="ad392-612">VI-opdracht modus: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ad392-612">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="ad392-613">Voltooiings functies</span><span class="sxs-lookup"><span data-stu-id="ad392-613">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="ad392-614">Voltooid</span><span class="sxs-lookup"><span data-stu-id="ad392-614">Complete</span></span>

<span data-ttu-id="ad392-615">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-615">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="ad392-616">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="ad392-616">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="ad392-617">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ad392-617">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="ad392-618">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ad392-618">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="ad392-619">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="ad392-619">MenuComplete</span></span>

<span data-ttu-id="ad392-620">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-620">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="ad392-621">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="ad392-621">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="ad392-622">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ad392-622">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="ad392-623">Cmd: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="ad392-623">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="ad392-624">Emacs: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="ad392-624">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="ad392-625">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="ad392-625">PossibleCompletions</span></span>

<span data-ttu-id="ad392-626">De lijst met mogelijke aanvullingen weer geven.</span><span class="sxs-lookup"><span data-stu-id="ad392-626">Display the list of possible completions.</span></span>

- <span data-ttu-id="ad392-627">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="ad392-627">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="ad392-628">VI Invoeg modus: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="ad392-628">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="ad392-629">VI-opdracht modus: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="ad392-629">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="ad392-630">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="ad392-630">TabCompleteNext</span></span>

<span data-ttu-id="ad392-631">Poging om de tekst rond de cursor te volt ooien met de volgende beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="ad392-631">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="ad392-632">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ad392-632">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="ad392-633">VI-opdracht modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ad392-633">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="ad392-634">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="ad392-634">TabCompletePrevious</span></span>

<span data-ttu-id="ad392-635">Poging om de tekst rond de cursor te volt ooien met de vorige beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="ad392-635">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="ad392-636">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="ad392-636">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="ad392-637">VI-opdracht modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="ad392-637">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="ad392-638">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="ad392-638">ViTabCompleteNext</span></span>

<span data-ttu-id="ad392-639">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompleteNext aan.</span><span class="sxs-lookup"><span data-stu-id="ad392-639">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="ad392-640">VI Invoeg modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ad392-640">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="ad392-641">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="ad392-641">ViTabCompletePrevious</span></span>

<span data-ttu-id="ad392-642">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompletePrevious aan.</span><span class="sxs-lookup"><span data-stu-id="ad392-642">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="ad392-643">VI Invoeg modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="ad392-643">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="prediction-functions"></a><span data-ttu-id="ad392-644">Voorspellings functies</span><span class="sxs-lookup"><span data-stu-id="ad392-644">Prediction functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="ad392-645">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="ad392-645">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="ad392-646">Wanneer u `InlineView` als weergave stijl voor voor spellingen gebruikt, moet u het volgende woord van de inline suggestie accepteren.</span><span class="sxs-lookup"><span data-stu-id="ad392-646">When using `InlineView` as the view style for prediction, accept the next word of the inline suggestion.</span></span>

- <span data-ttu-id="ad392-647">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-647">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="ad392-648">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="ad392-648">AcceptSuggestion</span></span>

<span data-ttu-id="ad392-649">Wanneer u `InlineView` als weergave stijl voor voor spellingen gebruikt, moet u de huidige inline suggestie accepteren.</span><span class="sxs-lookup"><span data-stu-id="ad392-649">When using `InlineView` as the view style for prediction, accept the current inline suggestion.</span></span>

- <span data-ttu-id="ad392-650">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-650">Function is unbound.</span></span>

### <a name="nextsuggestion"></a><span data-ttu-id="ad392-651">NextSuggestion</span><span class="sxs-lookup"><span data-stu-id="ad392-651">NextSuggestion</span></span>

<span data-ttu-id="ad392-652">Wanneer u `ListView` als weergave stijl voor voor spellingen gebruikt, gaat u naar de volgende suggestie in de lijst.</span><span class="sxs-lookup"><span data-stu-id="ad392-652">When using `ListView` as the view style for prediction, navigate to the next suggestion in the list.</span></span>

- <span data-ttu-id="ad392-653">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-653">Function is unbound.</span></span>

### <a name="previoussuggestion"></a><span data-ttu-id="ad392-654">PreviousSuggestion</span><span class="sxs-lookup"><span data-stu-id="ad392-654">PreviousSuggestion</span></span>

<span data-ttu-id="ad392-655">Wanneer u `ListView` als weergave stijl voor voor spellingen gebruikt, gaat u naar de vorige suggestie in de lijst.</span><span class="sxs-lookup"><span data-stu-id="ad392-655">When using `ListView` as the view style for prediction, navigate to the previous suggestion in the list.</span></span>

- <span data-ttu-id="ad392-656">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-656">Function is unbound.</span></span>

### <a name="switchpredictionview"></a><span data-ttu-id="ad392-657">SwitchPredictionView</span><span class="sxs-lookup"><span data-stu-id="ad392-657">SwitchPredictionView</span></span>

<span data-ttu-id="ad392-658">Scha kelen tussen de weergave stijl voor de voor spelling tussen `InlineView` en `ListView` .</span><span class="sxs-lookup"><span data-stu-id="ad392-658">Switch the view style for prediction between `InlineView` and `ListView`.</span></span>

- <span data-ttu-id="ad392-659">Cmd `<F2>`</span><span class="sxs-lookup"><span data-stu-id="ad392-659">Cmd: `<F2>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="ad392-660">Diverse functies</span><span class="sxs-lookup"><span data-stu-id="ad392-660">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="ad392-661">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="ad392-661">CaptureScreen</span></span>

<span data-ttu-id="ad392-662">Interactieve scherm opname starten-pijl-omhoog/omlaag Selecteer regels en voer de geselecteerde tekst als tekst en HTML naar het klem bord kopiëren.</span><span class="sxs-lookup"><span data-stu-id="ad392-662">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="ad392-663">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-663">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="ad392-664">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="ad392-664">ClearScreen</span></span>

<span data-ttu-id="ad392-665">Schakel het scherm uit en teken de huidige regel boven aan het scherm.</span><span class="sxs-lookup"><span data-stu-id="ad392-665">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="ad392-666">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ad392-666">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="ad392-667">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ad392-667">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="ad392-668">VI Invoeg modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ad392-668">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="ad392-669">VI-opdracht modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ad392-669">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="ad392-670">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="ad392-670">DigitArgument</span></span>

<span data-ttu-id="ad392-671">Start een nieuw cijfer argument om door te geven aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="ad392-671">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="ad392-672">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="ad392-672">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="ad392-673">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="ad392-673">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="ad392-674">VI-opdracht modus: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="ad392-674">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="ad392-675">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="ad392-675">InvokePrompt</span></span>

<span data-ttu-id="ad392-676">Hiermee wordt de huidige prompt gewist en wordt de functie Prompt aangeroepen om de prompt opnieuw weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ad392-676">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="ad392-677">Dit is handig voor aangepaste sleutel afhandelingen die de status wijzigen, bijvoorbeeld de huidige map wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ad392-677">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="ad392-678">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-678">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="ad392-679">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="ad392-679">ScrollDisplayDown</span></span>

<span data-ttu-id="ad392-680">De weer gave één scherm omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="ad392-680">Scroll the display down one screen.</span></span>

- <span data-ttu-id="ad392-681">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ad392-681">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="ad392-682">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ad392-682">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="ad392-683">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="ad392-683">ScrollDisplayDownLine</span></span>

<span data-ttu-id="ad392-684">De weer gave één regel omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="ad392-684">Scroll the display down one line.</span></span>

- <span data-ttu-id="ad392-685">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ad392-685">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="ad392-686">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ad392-686">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="ad392-687">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="ad392-687">ScrollDisplayToCursor</span></span>

<span data-ttu-id="ad392-688">Schuif de weer gave naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-688">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="ad392-689">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ad392-689">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="ad392-690">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="ad392-690">ScrollDisplayTop</span></span>

<span data-ttu-id="ad392-691">Schuif de weer gave naar boven.</span><span class="sxs-lookup"><span data-stu-id="ad392-691">Scroll the display to the top.</span></span>

- <span data-ttu-id="ad392-692">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="ad392-692">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="ad392-693">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="ad392-693">ScrollDisplayUp</span></span>

<span data-ttu-id="ad392-694">Schuif de weer gave één scherm omhoog.</span><span class="sxs-lookup"><span data-stu-id="ad392-694">Scroll the display up one screen.</span></span>

- <span data-ttu-id="ad392-695">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ad392-695">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="ad392-696">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ad392-696">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="ad392-697">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="ad392-697">ScrollDisplayUpLine</span></span>

<span data-ttu-id="ad392-698">De weer gave één regel omhoog schuiven.</span><span class="sxs-lookup"><span data-stu-id="ad392-698">Scroll the display up one line.</span></span>

- <span data-ttu-id="ad392-699">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ad392-699">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="ad392-700">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ad392-700">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="ad392-701">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="ad392-701">SelfInsert</span></span>

<span data-ttu-id="ad392-702">Voeg de sleutel in.</span><span class="sxs-lookup"><span data-stu-id="ad392-702">Insert the key.</span></span>

- <span data-ttu-id="ad392-703">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-703">Function is unbound.</span></span>

### <a name="showcommandhelp"></a><span data-ttu-id="ad392-704">ShowCommandHelp</span><span class="sxs-lookup"><span data-stu-id="ad392-704">ShowCommandHelp</span></span>

<span data-ttu-id="ad392-705">Biedt een weer gave van de volledige Help-informatie over een andere scherm buffer met behulp van een paginerings functie van **micro soft. Power shell. pager**.</span><span class="sxs-lookup"><span data-stu-id="ad392-705">Provides a view of full cmdlet help on alternate screen buffer using a Pager from **Microsoft.PowerShell.Pager**.</span></span>

- <span data-ttu-id="ad392-706">Cmd `<F1>`</span><span class="sxs-lookup"><span data-stu-id="ad392-706">Cmd: `<F1>`</span></span>
- <span data-ttu-id="ad392-707">Emacs: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="ad392-707">Emacs: `<F1>`</span></span>
- <span data-ttu-id="ad392-708">VI Invoeg modus: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="ad392-708">Vi insert mode: `<F1>`</span></span>
- <span data-ttu-id="ad392-709">VI-opdracht modus: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="ad392-709">Vi command mode: `<F1>`</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="ad392-710">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="ad392-710">ShowKeyBindings</span></span>

<span data-ttu-id="ad392-711">Alle gebonden sleutels weer geven.</span><span class="sxs-lookup"><span data-stu-id="ad392-711">Show all bound keys.</span></span>

- <span data-ttu-id="ad392-712">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ad392-712">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="ad392-713">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ad392-713">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="ad392-714">VI Invoeg modus: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ad392-714">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="showparameterhelp"></a><span data-ttu-id="ad392-715">ShowParameterHelp</span><span class="sxs-lookup"><span data-stu-id="ad392-715">ShowParameterHelp</span></span>

<span data-ttu-id="ad392-716">Biedt dynamische Help voor para meters door deze onder de huidige opdracht regel te laten zien `MenuComplete` .</span><span class="sxs-lookup"><span data-stu-id="ad392-716">Provides dynamic help for parameters by showing it below the current command line like `MenuComplete`.</span></span>

- <span data-ttu-id="ad392-717">Cmd `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="ad392-717">Cmd: `<Alt+h>`</span></span>
- <span data-ttu-id="ad392-718">Emacs: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="ad392-718">Emacs: `<Alt+h>`</span></span>
- <span data-ttu-id="ad392-719">VI Invoeg modus: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="ad392-719">Vi insert mode: `<Alt+h>`</span></span>
- <span data-ttu-id="ad392-720">VI-opdracht modus: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="ad392-720">Vi command mode: `<Alt+h>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="ad392-721">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="ad392-721">ViCommandMode</span></span>

<span data-ttu-id="ad392-722">Schakel de huidige bedrijfs modus uit van Vi-Insert naar de VI-opdracht.</span><span class="sxs-lookup"><span data-stu-id="ad392-722">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="ad392-723">VI Invoeg modus: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="ad392-723">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="ad392-724">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="ad392-724">ViDigitArgumentInChord</span></span>

<span data-ttu-id="ad392-725">Start een nieuw cijfer argument om door te geven aan andere functies in een van de koorden van VI.</span><span class="sxs-lookup"><span data-stu-id="ad392-725">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="ad392-726">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-726">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="ad392-727">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="ad392-727">ViEditVisually</span></span>

<span data-ttu-id="ad392-728">Bewerk de opdracht regel in een tekst editor die is opgegeven door $env: EDITOR of $env: VISUAL.</span><span class="sxs-lookup"><span data-stu-id="ad392-728">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="ad392-729">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="ad392-729">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="ad392-730">VI-opdracht modus: `<v>`</span><span class="sxs-lookup"><span data-stu-id="ad392-730">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="ad392-731">ViExit</span><span class="sxs-lookup"><span data-stu-id="ad392-731">ViExit</span></span>

<span data-ttu-id="ad392-732">Hiermee wordt de shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="ad392-732">Exits the shell.</span></span>

- <span data-ttu-id="ad392-733">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-733">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="ad392-734">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="ad392-734">ViInsertMode</span></span>

<span data-ttu-id="ad392-735">Schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="ad392-735">Switch to Insert mode.</span></span>

- <span data-ttu-id="ad392-736">VI-opdracht modus: `<i>`</span><span class="sxs-lookup"><span data-stu-id="ad392-736">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="ad392-737">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="ad392-737">WhatIsKey</span></span>

<span data-ttu-id="ad392-738">Lees een sleutel en vertel me wat de sleutel is gebonden.</span><span class="sxs-lookup"><span data-stu-id="ad392-738">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="ad392-739">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ad392-739">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="ad392-740">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ad392-740">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="ad392-741">Selectie functies</span><span class="sxs-lookup"><span data-stu-id="ad392-741">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="ad392-742">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="ad392-742">ExchangePointAndMark</span></span>

<span data-ttu-id="ad392-743">De cursor wordt op de locatie van het merk geplaatst en het vinkje wordt verplaatst naar de locatie van de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-743">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="ad392-744">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="ad392-744">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="ad392-745">SelectAll aanroepen</span><span class="sxs-lookup"><span data-stu-id="ad392-745">SelectAll</span></span>

<span data-ttu-id="ad392-746">Selecteer de volledige regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-746">Select the entire line.</span></span>

- <span data-ttu-id="ad392-747">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="ad392-747">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="ad392-748">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="ad392-748">SelectBackwardChar</span></span>

<span data-ttu-id="ad392-749">Pas de huidige selectie aan om het vorige teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="ad392-749">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="ad392-750">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-750">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="ad392-751">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-751">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="ad392-752">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="ad392-752">SelectBackwardsLine</span></span>

<span data-ttu-id="ad392-753">Pas de huidige selectie aan de cursor toe aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-753">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="ad392-754">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="ad392-754">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="ad392-755">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="ad392-755">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="ad392-756">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ad392-756">SelectBackwardWord</span></span>

<span data-ttu-id="ad392-757">Pas de huidige selectie aan om het vorige woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="ad392-757">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="ad392-758">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-758">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="ad392-759">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="ad392-759">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="ad392-760">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="ad392-760">SelectForwardChar</span></span>

<span data-ttu-id="ad392-761">Pas de huidige selectie aan om het volgende teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="ad392-761">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="ad392-762">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-762">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="ad392-763">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-763">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="ad392-764">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="ad392-764">SelectForwardWord</span></span>

<span data-ttu-id="ad392-765">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="ad392-765">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="ad392-766">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="ad392-766">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="ad392-767">SelectLine</span><span class="sxs-lookup"><span data-stu-id="ad392-767">SelectLine</span></span>

<span data-ttu-id="ad392-768">Pas de huidige selectie aan de cursor toe aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-768">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="ad392-769">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="ad392-769">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="ad392-770">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="ad392-770">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="ad392-771">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="ad392-771">SelectNextWord</span></span>

<span data-ttu-id="ad392-772">Pas de huidige selectie aan om het volgende woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="ad392-772">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="ad392-773">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ad392-773">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="ad392-774">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ad392-774">SelectShellBackwardWord</span></span>

<span data-ttu-id="ad392-775">Pas de huidige selectie aan om het vorige woord op te maken met behulp van ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="ad392-775">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="ad392-776">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-776">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="ad392-777">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="ad392-777">SelectShellForwardWord</span></span>

<span data-ttu-id="ad392-778">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="ad392-778">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="ad392-779">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-779">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="ad392-780">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="ad392-780">SelectShellNextWord</span></span>

<span data-ttu-id="ad392-781">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="ad392-781">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="ad392-782">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="ad392-782">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="ad392-783">SetMark</span><span class="sxs-lookup"><span data-stu-id="ad392-783">SetMark</span></span>

<span data-ttu-id="ad392-784">De huidige locatie van de cursor markeren voor gebruik in een volgende bewerkings opdracht.</span><span class="sxs-lookup"><span data-stu-id="ad392-784">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="ad392-785">Emacs: `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="ad392-785">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="ad392-786">Voorspellende IntelliSense-functies</span><span class="sxs-lookup"><span data-stu-id="ad392-786">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="ad392-787">Voorspellende IntelliSense moet zijn ingeschakeld om deze functies te kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ad392-787">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="ad392-788">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="ad392-788">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="ad392-789">Hiermee wordt het volgende woord van de inline suggestie geaccepteerd van voorspellende IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ad392-789">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="ad392-790">Deze functie kan worden gebonden met <kbd>CTRL</kbd> + <kbd>F</kbd> door de volgende opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ad392-790">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="ad392-791">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="ad392-791">AcceptSuggestion</span></span>

<span data-ttu-id="ad392-792">Hiermee wordt de huidige inline suggestie van voorspellende IntelliSense geaccepteerd door op <kbd>RightArrow</kbd> te drukken wanneer de cursor zich aan het einde van de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="ad392-792">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="ad392-793">Zoek functies</span><span class="sxs-lookup"><span data-stu-id="ad392-793">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="ad392-794">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="ad392-794">CharacterSearch</span></span>

<span data-ttu-id="ad392-795">Lees een teken en zoek voorwaarts naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-795">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="ad392-796">Als er een argument is opgegeven, zoekt u voorwaarts (of achterwaarts als negatieve) voor het ne voorval.</span><span class="sxs-lookup"><span data-stu-id="ad392-796">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="ad392-797">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="ad392-797">Cmd: `<F3>`</span></span>
- <span data-ttu-id="ad392-798">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ad392-798">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="ad392-799">VI Invoeg modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="ad392-799">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="ad392-800">VI-opdracht modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="ad392-800">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="ad392-801">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="ad392-801">CharacterSearchBackward</span></span>

<span data-ttu-id="ad392-802">Lees een teken en zoek terug naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-802">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="ad392-803">Als er een argument is opgegeven, zoekt u terug (of als dit negatief is) voor het ne exemplaar.</span><span class="sxs-lookup"><span data-stu-id="ad392-803">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="ad392-804">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="ad392-804">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="ad392-805">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="ad392-805">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="ad392-806">VI Invoeg modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="ad392-806">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="ad392-807">VI-opdracht modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="ad392-807">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="ad392-808">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="ad392-808">RepeatLastCharSearch</span></span>

<span data-ttu-id="ad392-809">De laatst opgenomen zoek opdracht herhalen.</span><span class="sxs-lookup"><span data-stu-id="ad392-809">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="ad392-810">VI-opdracht modus: `<;>`</span><span class="sxs-lookup"><span data-stu-id="ad392-810">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="ad392-811">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="ad392-811">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="ad392-812">De laatst opgenomen zoek opdracht herhalen, maar in tegenovergestelde richting.</span><span class="sxs-lookup"><span data-stu-id="ad392-812">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="ad392-813">VI-opdracht modus: `<,>`</span><span class="sxs-lookup"><span data-stu-id="ad392-813">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="ad392-814">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="ad392-814">RepeatSearch</span></span>

<span data-ttu-id="ad392-815">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="ad392-815">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="ad392-816">VI-opdracht modus: `<n>`</span><span class="sxs-lookup"><span data-stu-id="ad392-816">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="ad392-817">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="ad392-817">RepeatSearchBackward</span></span>

<span data-ttu-id="ad392-818">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="ad392-818">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="ad392-819">VI-opdracht modus: `<N>`</span><span class="sxs-lookup"><span data-stu-id="ad392-819">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="ad392-820">SearchChar</span><span class="sxs-lookup"><span data-stu-id="ad392-820">SearchChar</span></span>

<span data-ttu-id="ad392-821">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-821">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="ad392-822">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="ad392-822">This is for 't' functionality.</span></span>

- <span data-ttu-id="ad392-823">VI-opdracht modus: `<f>`</span><span class="sxs-lookup"><span data-stu-id="ad392-823">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="ad392-824">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="ad392-824">SearchCharBackward</span></span>

<span data-ttu-id="ad392-825">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-825">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="ad392-826">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="ad392-826">This is for 'T' functionality.</span></span>

- <span data-ttu-id="ad392-827">VI-opdracht modus: `<F>`</span><span class="sxs-lookup"><span data-stu-id="ad392-827">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="ad392-828">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="ad392-828">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="ad392-829">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-829">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="ad392-830">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="ad392-830">This is for 'T' functionality.</span></span>

- <span data-ttu-id="ad392-831">VI-opdracht modus: `<T>`</span><span class="sxs-lookup"><span data-stu-id="ad392-831">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="ad392-832">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="ad392-832">SearchCharWithBackoff</span></span>

<span data-ttu-id="ad392-833">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="ad392-833">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="ad392-834">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="ad392-834">This is for 't' functionality.</span></span>

- <span data-ttu-id="ad392-835">VI-opdracht modus: `<t>`</span><span class="sxs-lookup"><span data-stu-id="ad392-835">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="ad392-836">SearchForward</span><span class="sxs-lookup"><span data-stu-id="ad392-836">SearchForward</span></span>

<span data-ttu-id="ad392-837">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="ad392-837">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="ad392-838">VI Invoeg modus: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ad392-838">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="ad392-839">VI-opdracht modus: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ad392-839">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="ad392-840">Aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="ad392-840">Custom Key Bindings</span></span>

<span data-ttu-id="ad392-841">PSReadLine ondersteunt aangepaste sleutel bindingen met behulp van de-cmdlet `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="ad392-841">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="ad392-842">De meeste aangepaste sleutel bindingen roepen een van de bovenstaande functies aan, bijvoorbeeld</span><span class="sxs-lookup"><span data-stu-id="ad392-842">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="ad392-843">U kunt een script Block binden aan een sleutel.</span><span class="sxs-lookup"><span data-stu-id="ad392-843">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="ad392-844">Het script Block kan veel wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="ad392-844">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="ad392-845">Enkele handige voor beelden zijn</span><span class="sxs-lookup"><span data-stu-id="ad392-845">Some useful examples include</span></span>

- <span data-ttu-id="ad392-846">de opdracht regel bewerken</span><span class="sxs-lookup"><span data-stu-id="ad392-846">edit the command line</span></span>
- <span data-ttu-id="ad392-847">een nieuw venster openen (bijvoorbeeld Help)</span><span class="sxs-lookup"><span data-stu-id="ad392-847">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="ad392-848">mappen wijzigen zonder de opdracht regel te wijzigen</span><span class="sxs-lookup"><span data-stu-id="ad392-848">change directories without changing the command line</span></span>

<span data-ttu-id="ad392-849">De script Block ontvangt twee argumenten:</span><span class="sxs-lookup"><span data-stu-id="ad392-849">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="ad392-850">`$key` -Een **[ConsoleKeyInfo]** -object dat de sleutel is die de aangepaste binding heeft geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="ad392-850">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="ad392-851">Als u dezelfde script Block aan meerdere sleutels koppelt en verschillende acties moet uitvoeren, afhankelijk van de sleutel, kunt u $key controleren.</span><span class="sxs-lookup"><span data-stu-id="ad392-851">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="ad392-852">Veel aangepaste bindingen negeren dit argument.</span><span class="sxs-lookup"><span data-stu-id="ad392-852">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="ad392-853">`$arg` -Een wille keurig argument.</span><span class="sxs-lookup"><span data-stu-id="ad392-853">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="ad392-854">Meestal is dit een geheel getal dat de gebruiker door gegeven van de sleutel bindingen DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="ad392-854">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="ad392-855">Als uw binding geen argumenten accepteert, is het redelijk om dit argument te negeren.</span><span class="sxs-lookup"><span data-stu-id="ad392-855">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="ad392-856">Laten we een voor beeld bekijken waarmee een opdracht regel wordt toegevoegd aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ad392-856">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="ad392-857">Dit is handig wanneer u ervoor hebt gekozen om iets te doen, maar niet opnieuw moet invoeren van de opdracht regel die u al hebt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="ad392-857">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="ad392-858">U kunt veel meer voor beelden bekijken in het bestand `SamplePSReadLineProfile.ps1` dat is geïnstalleerd in de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="ad392-858">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="ad392-859">De meeste sleutel bindingen gebruiken enkele hulp functies voor het bewerken van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-859">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="ad392-860">Deze Api's worden beschreven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="ad392-860">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="ad392-861">Api's voor de ondersteuning van aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="ad392-861">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="ad392-862">De volgende functies zijn openbaar in micro soft. Power shell. PSConsoleReadLine, maar kunnen niet rechtstreeks aan een sleutel worden gebonden.</span><span class="sxs-lookup"><span data-stu-id="ad392-862">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="ad392-863">De meeste zijn handig in aangepaste sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="ad392-863">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="ad392-864">Een opdracht regel toevoegen aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ad392-864">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="ad392-865">Wis de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="ad392-865">Clear the kill-ring.</span></span>  <span data-ttu-id="ad392-866">Dit wordt meestal gebruikt voor het testen.</span><span class="sxs-lookup"><span data-stu-id="ad392-866">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="ad392-867">Verwijder de lengte tekens uit het begin.</span><span class="sxs-lookup"><span data-stu-id="ad392-867">Delete length characters from start.</span></span>  <span data-ttu-id="ad392-868">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ad392-868">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="ad392-869">Voer de actie opname uit op basis van de voor keuren van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="ad392-869">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="ad392-870">Deze twee functies halen nuttige informatie op over de huidige status van de invoer buffer.</span><span class="sxs-lookup"><span data-stu-id="ad392-870">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="ad392-871">De eerste wordt vaak gebruikt voor eenvoudige gevallen.</span><span class="sxs-lookup"><span data-stu-id="ad392-871">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="ad392-872">De tweede wordt gebruikt als uw binding iets geavanceerder gaat met de AST.</span><span class="sxs-lookup"><span data-stu-id="ad392-872">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="ad392-873">Deze twee functies worden gebruikt door `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="ad392-873">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="ad392-874">De eerste wordt gebruikt om alle sleutel bindingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="ad392-874">The first is used to get all key bindings.</span></span> <span data-ttu-id="ad392-875">De tweede wordt gebruikt voor het ophalen van specifieke sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="ad392-875">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="ad392-876">Deze functie wordt gebruikt door Get-PSReadLineOption en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="ad392-876">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="ad392-877">Als er niets is geselecteerd op de opdracht regel, wordt-1 geretourneerd in zowel start als length.</span><span class="sxs-lookup"><span data-stu-id="ad392-877">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="ad392-878">Als er een selectie is op de opdracht regel, worden het begin en de lengte van de selectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ad392-878">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="ad392-879">Voeg een teken of teken reeks toe aan de cursor.</span><span class="sxs-lookup"><span data-stu-id="ad392-879">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="ad392-880">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ad392-880">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="ad392-881">Dit is het belangrijkste ingangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ad392-881">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="ad392-882">Er wordt geen recursie ondersteund, dus is niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="ad392-882">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="ad392-883">Deze functie wordt gebruikt door Remove-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="ad392-883">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="ad392-884">Vervang een deel van de invoer.</span><span class="sxs-lookup"><span data-stu-id="ad392-884">Replace some of the input.</span></span> <span data-ttu-id="ad392-885">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ad392-885">This operation supports undo/redo.</span></span> <span data-ttu-id="ad392-886">U kunt het beste verwijderen gevolgd door INSERT, omdat het wordt beschouwd als één actie voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="ad392-886">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="ad392-887">De cursor verplaatsen naar de opgegeven verschuiving.</span><span class="sxs-lookup"><span data-stu-id="ad392-887">Move the cursor to the given offset.</span></span> <span data-ttu-id="ad392-888">Cursor verplaatsing wordt niet bijgehouden voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="ad392-888">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="ad392-889">Deze functie is een helper-methode die wordt gebruikt door de cmdlet Set-PSReadLineOption, maar kan handig zijn voor een aangepaste sleutel binding die tijdelijk een instelling wil wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ad392-889">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="ad392-890">Deze Help methode wordt gebruikt voor aangepaste bindingen die voldoen aan DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="ad392-890">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="ad392-891">Een typische aanroep ziet eruit als</span><span class="sxs-lookup"><span data-stu-id="ad392-891">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a><span data-ttu-id="ad392-892">Notities</span><span class="sxs-lookup"><span data-stu-id="ad392-892">Notes</span></span>

### <a name="command-history"></a><span data-ttu-id="ad392-893">Opdracht geschiedenis</span><span class="sxs-lookup"><span data-stu-id="ad392-893">Command History</span></span>

<span data-ttu-id="ad392-894">PSReadLine onderhoudt een geschiedenis bestand met alle opdrachten en gegevens die u hebt ingevoerd op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="ad392-894">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="ad392-895">Dit kan gevoelige gegevens bevatten, inclusief wacht woorden.</span><span class="sxs-lookup"><span data-stu-id="ad392-895">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="ad392-896">Als u bijvoorbeeld de cmdlet gebruikt, `ConvertTo-SecureString` wordt het wacht woord in het geschiedenis bestand vastgelegd als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="ad392-896">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="ad392-897">De geschiedenis bestanden zijn een bestand met de naam `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="ad392-897">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="ad392-898">Op Windows-systemen wordt het geschiedenis bestand opgeslagen op `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="ad392-898">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="ad392-899">Op niet-Windows-systemen worden de geschiedenis bestanden opgeslagen in `$env:XDG_DATA_HOME/powershell/PSReadLine` of `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="ad392-899">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="ad392-900">Feedback & bijdragen aan PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ad392-900">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="ad392-901">PSReadLine op GitHub</span><span class="sxs-lookup"><span data-stu-id="ad392-901">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="ad392-902">U kunt een pull-aanvraag verzenden of feedback verzenden op de pagina GitHub.</span><span class="sxs-lookup"><span data-stu-id="ad392-902">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad392-903">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ad392-903">See Also</span></span>

<span data-ttu-id="ad392-904">PSReadLine wordt sterk beïnvloed door de GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="ad392-904">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
