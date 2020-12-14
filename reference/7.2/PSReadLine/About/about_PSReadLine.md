---
description: PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over PSReadLine
ms.openlocfilehash: 4836abfec465ba7cdfb6800c1e60104fba19ce08
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913305"
---
# <a name="psreadline"></a><span data-ttu-id="d563a-103">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="d563a-103">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="d563a-104">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="d563a-104">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="d563a-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="d563a-105">Short Description</span></span>

<span data-ttu-id="d563a-106">PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="d563a-106">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="d563a-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="d563a-107">Long Description</span></span>

<span data-ttu-id="d563a-108">PSReadLine 2,2 biedt een krachtige opdracht regel voor het bewerken van de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="d563a-108">PSReadLine 2.2 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="d563a-109">De oplossing biedt het volgende:</span><span class="sxs-lookup"><span data-stu-id="d563a-109">It provides:</span></span>

- <span data-ttu-id="d563a-110">Syntaxis kleur van de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="d563a-110">Syntax coloring of the command line</span></span>
- <span data-ttu-id="d563a-111">Een visuele indicatie van syntaxis fouten</span><span class="sxs-lookup"><span data-stu-id="d563a-111">A visual indication of syntax errors</span></span>
- <span data-ttu-id="d563a-112">Een betere ervaring met meerdere regels (zowel bewerkingen als geschiedenis)</span><span class="sxs-lookup"><span data-stu-id="d563a-112">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="d563a-113">Aanpas bare sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="d563a-113">Customizable key bindings</span></span>
- <span data-ttu-id="d563a-114">Cmd-en emacs-modi</span><span class="sxs-lookup"><span data-stu-id="d563a-114">Cmd and Emacs modes</span></span>
- <span data-ttu-id="d563a-115">Veel configuratie opties</span><span class="sxs-lookup"><span data-stu-id="d563a-115">Many configuration options</span></span>
- <span data-ttu-id="d563a-116">Bash-stijl voltooiing (optioneel in CMD-modus, standaard in Emacs-modus)</span><span class="sxs-lookup"><span data-stu-id="d563a-116">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="d563a-117">Emacs Yank/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="d563a-117">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="d563a-118">"Woord" verplaatsing en afsluiten op basis van Power shell-tokens</span><span class="sxs-lookup"><span data-stu-id="d563a-118">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="d563a-119">Voorspellende IntelliSense</span><span class="sxs-lookup"><span data-stu-id="d563a-119">Predictive IntelliSense</span></span>

<span data-ttu-id="d563a-120">PSReadLine 2.2.0 heeft twee nieuwe voorspellende IntelliSense-functies toegevoegd:</span><span class="sxs-lookup"><span data-stu-id="d563a-120">PSReadLine 2.2.0 added two new predictive IntelliSense features:</span></span>

- <span data-ttu-id="d563a-121">De para meter **PredictionViewStyle** is toegevoegd zodat de nieuwe kan worden geselecteerd `ListView` .</span><span class="sxs-lookup"><span data-stu-id="d563a-121">Added the **PredictionViewStyle** parameter to allow for the selection of the new `ListView`.</span></span>
- <span data-ttu-id="d563a-122">Verbonden PSReadLine met de `CommandPrediction` api's die in PS 7,1 zijn geïntroduceerd om een gebruiker toe te staan een Voorspellings module te importeren waarmee de suggesties van een aangepaste bron kunnen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d563a-122">Connected PSReadLine to the `CommandPrediction` APIs introduced in PS 7.1 to allow a user can import a predictor module that can render the suggestions from a custom source.</span></span>

<span data-ttu-id="d563a-123">PSReadLine vereist Power Shell 3,0 of nieuwer.</span><span class="sxs-lookup"><span data-stu-id="d563a-123">PSReadLine requires PowerShell 3.0, or newer.</span></span> <span data-ttu-id="d563a-124">PSReadLine werkt met de standaard console-host, Visual Studio code en Windows-Terminal.</span><span class="sxs-lookup"><span data-stu-id="d563a-124">PSReadLine works with default console host, Visual Studio Code, and Window Terminal.</span></span> <span data-ttu-id="d563a-125">Het werkt niet in Power shell ISE.</span><span class="sxs-lookup"><span data-stu-id="d563a-125">It does not work in PowerShell ISE.</span></span>

<span data-ttu-id="d563a-126">PSReadLine 2.2.0 wordt geleverd met Power shell 7,2 en wordt ondersteund in alle ondersteunde versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="d563a-126">PSReadLine 2.2.0 ships with PowerShell 7.2 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="d563a-127">Het is beschikbaar om te installeren via de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="d563a-127">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="d563a-128">Voer de volgende opdracht uit om PSReadLine 2.2.0 in een ondersteunde versie van Power shell te installeren.</span><span class="sxs-lookup"><span data-stu-id="d563a-128">To install PSReadLine 2.2.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> <span data-ttu-id="d563a-129">Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="d563a-129">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="d563a-130">Op dit moment werkt PSReadLine niet goed met scherm lezers.</span><span class="sxs-lookup"><span data-stu-id="d563a-130">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="d563a-131">De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="d563a-131">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="d563a-132">U kunt de module hand matig laden, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="d563a-132">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="d563a-133">Voorspellende IntelliSense</span><span class="sxs-lookup"><span data-stu-id="d563a-133">Predictive IntelliSense</span></span>

<span data-ttu-id="d563a-134">Voorspellende IntelliSense is een aanvulling op het concept van tabblad voltooiing waarmee de gebruiker wordt geholpen bij het volt ooien van opdrachten.</span><span class="sxs-lookup"><span data-stu-id="d563a-134">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="d563a-135">Hiermee kunnen gebruikers volledige opdrachten detecteren, bewerken en uitvoeren op basis van overeenkomende voor spellingen van de geschiedenis van de gebruiker en aanvullende toepassingsspecifieke invoeg toepassingen.</span><span class="sxs-lookup"><span data-stu-id="d563a-135">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="d563a-136">Voorspellende IntelliSense inschakelen</span><span class="sxs-lookup"><span data-stu-id="d563a-136">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="d563a-137">Voorspellende IntelliSense is standaard uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="d563a-137">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="d563a-138">Als u voor spellingen wilt inschakelen, voert u gewoon de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="d563a-138">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="d563a-139">De para meter **PredictionSource** kan ook invoeg toepassingen accepteren voor specifieke en aangepaste vereisten voor het domein.</span><span class="sxs-lookup"><span data-stu-id="d563a-139">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="d563a-140">Als u voorspellende IntelliSense wilt uitschakelen, voert u de volgende handelingen uit:</span><span class="sxs-lookup"><span data-stu-id="d563a-140">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="d563a-141">De volgende functies zijn beschikbaar in de klasse **[micro soft. Power shell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="d563a-141">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="d563a-142">Basis bewerkings functies</span><span class="sxs-lookup"><span data-stu-id="d563a-142">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="d563a-143">Afbreken</span><span class="sxs-lookup"><span data-stu-id="d563a-143">Abort</span></span>

<span data-ttu-id="d563a-144">De huidige actie afbreken, bijvoorbeeld een incrementele geschiedenis zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="d563a-144">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="d563a-145">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="d563a-145">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="d563a-146">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="d563a-146">AcceptAndGetNext</span></span>

<span data-ttu-id="d563a-147">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="d563a-147">Attempt to execute the current input.</span></span> <span data-ttu-id="d563a-148">Als deze kan worden uitgevoerd (zoals AcceptLine), kunt u het volgende item uit de geschiedenis intrekken de volgende keer dat ReadLine wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="d563a-148">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="d563a-149">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="d563a-149">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="d563a-150">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="d563a-150">AcceptLine</span></span>

<span data-ttu-id="d563a-151">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="d563a-151">Attempt to execute the current input.</span></span> <span data-ttu-id="d563a-152">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="d563a-152">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="d563a-153">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="d563a-153">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="d563a-154">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="d563a-154">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="d563a-155">VI Invoeg modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="d563a-155">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="d563a-156">AddLine</span><span class="sxs-lookup"><span data-stu-id="d563a-156">AddLine</span></span>

<span data-ttu-id="d563a-157">De vervolg prompt wordt weer gegeven op de volgende regel en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="d563a-157">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="d563a-158">Dit is handig om invoer in meerdere regels als één opdracht in te voeren, zelfs wanneer één regel volledig wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="d563a-158">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="d563a-159">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d563a-159">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="d563a-160">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d563a-160">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="d563a-161">VI Invoeg modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d563a-161">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="d563a-162">VI-opdracht modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d563a-162">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="d563a-163">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="d563a-163">BackwardDeleteChar</span></span>

<span data-ttu-id="d563a-164">Verwijder het teken voor de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-164">Delete the character before the cursor.</span></span>

- <span data-ttu-id="d563a-165">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="d563a-165">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="d563a-166">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="d563a-166">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="d563a-167">VI Invoeg modus: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="d563a-167">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="d563a-168">VI-opdracht modus: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="d563a-168">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="d563a-169">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="d563a-169">BackwardDeleteLine</span></span>

<span data-ttu-id="d563a-170">Net als BackwardKillLine: verwijdert tekst van het punt naar het begin van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="d563a-170">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="d563a-171">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="d563a-171">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="d563a-172">VI Invoeg modus: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="d563a-172">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="d563a-173">VI-opdracht modus: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="d563a-173">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="d563a-174">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="d563a-174">BackwardDeleteWord</span></span>

<span data-ttu-id="d563a-175">Hiermee verwijdert u het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-175">Deletes the previous word.</span></span>

- <span data-ttu-id="d563a-176">VI-opdracht modus: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="d563a-176">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="d563a-177">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="d563a-177">BackwardKillLine</span></span>

<span data-ttu-id="d563a-178">De invoer van het begin van de invoer wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-178">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="d563a-179">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="d563a-179">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="d563a-180">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="d563a-180">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="d563a-181">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="d563a-181">BackwardKillWord</span></span>

<span data-ttu-id="d563a-182">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-182">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="d563a-183">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="d563a-183">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="d563a-184">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="d563a-184">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="d563a-185">Cmd: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="d563a-185">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="d563a-186">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="d563a-186">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="d563a-187">VI Invoeg modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="d563a-187">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="d563a-188">VI-opdracht modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="d563a-188">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="d563a-189">CancelLine</span><span class="sxs-lookup"><span data-stu-id="d563a-189">CancelLine</span></span>

<span data-ttu-id="d563a-190">De huidige invoer annuleren, waardoor de invoer op het scherm wordt weer gegeven, maar terugkeert naar de host, zodat de prompt opnieuw wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="d563a-190">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="d563a-191">VI Invoeg modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="d563a-191">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="d563a-192">VI-opdracht modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="d563a-192">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="d563a-193">Kopiëren</span><span class="sxs-lookup"><span data-stu-id="d563a-193">Copy</span></span>

<span data-ttu-id="d563a-194">Kopieer de geselecteerde regio naar het klem bord van het systeem.</span><span class="sxs-lookup"><span data-stu-id="d563a-194">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="d563a-195">Als er geen regio is geselecteerd, kopieert u de hele regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-195">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="d563a-196">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="d563a-196">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="d563a-197">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="d563a-197">CopyOrCancelLine</span></span>

<span data-ttu-id="d563a-198">Als tekst is geselecteerd, kopieert u deze naar het klem bord. anders annuleert u de regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-198">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="d563a-199">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="d563a-199">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="d563a-200">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="d563a-200">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="d563a-201">Knippen</span><span class="sxs-lookup"><span data-stu-id="d563a-201">Cut</span></span>

<span data-ttu-id="d563a-202">Geselecteerde regio verwijderen Verwijderde tekst in het systeem Klembord plaatsen.</span><span class="sxs-lookup"><span data-stu-id="d563a-202">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="d563a-203">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="d563a-203">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="d563a-204">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="d563a-204">DeleteChar</span></span>

<span data-ttu-id="d563a-205">Verwijder het teken onder de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-205">Delete the character under the cursor.</span></span>

- <span data-ttu-id="d563a-206">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="d563a-206">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="d563a-207">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="d563a-207">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="d563a-208">VI Invoeg modus: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="d563a-208">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="d563a-209">VI-opdracht modus: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="d563a-209">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="d563a-210">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="d563a-210">DeleteCharOrExit</span></span>

<span data-ttu-id="d563a-211">Verwijder het teken onder de cursor of als de regel leeg is, sluit u het proces.</span><span class="sxs-lookup"><span data-stu-id="d563a-211">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="d563a-212">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="d563a-212">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="d563a-213">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="d563a-213">DeleteEndOfBuffer</span></span>

<span data-ttu-id="d563a-214">Hiermee verwijdert u aan het einde van de buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="d563a-214">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="d563a-215">VI-opdracht modus: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="d563a-215">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="d563a-216">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="d563a-216">DeleteEndOfWord</span></span>

<span data-ttu-id="d563a-217">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-217">Delete to the end of the word.</span></span>

- <span data-ttu-id="d563a-218">VI-opdracht modus: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="d563a-218">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="d563a-219">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="d563a-219">DeleteLine</span></span>

<span data-ttu-id="d563a-220">Hiermee verwijdert u de huidige logische lijn van een buffer voor meerdere regels, waarbij u ongedaan maken inschakelt.</span><span class="sxs-lookup"><span data-stu-id="d563a-220">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="d563a-221">VI-opdracht modus: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="d563a-221">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="d563a-222">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="d563a-222">DeletePreviousLines</span></span>

<span data-ttu-id="d563a-223">Hiermee verwijdert u de vorige aangevraagde logische regels en de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="d563a-223">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="d563a-224">VI-opdracht modus: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="d563a-224">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="d563a-225">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="d563a-225">DeleteRelativeLines</span></span>

<span data-ttu-id="d563a-226">Verwijdert uit het begin van de buffer naar de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="d563a-226">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="d563a-227">De meeste MS-DOS-opdrachten `<d,g,g>` kunnen worden voorafgegaan door een numeriek argument waarmee een absoluut regel nummer wordt opgegeven, samen met het huidige regel nummer, een bereik aan regels maken dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d563a-227">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="d563a-228">Als u niets opgeeft, wordt het numerieke argument standaard ingesteld op 1, dat verwijst naar de eerste logische lijn in een buffer met meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="d563a-228">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="d563a-229">Het werkelijke aantal regels dat uit de meerregelige moet worden verwijderd, wordt berekend als het verschil tussen het huidige logische regel nummer en het opgegeven numerieke argument. Dit kan dus negatief zijn.</span><span class="sxs-lookup"><span data-stu-id="d563a-229">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="d563a-230">Daarom is het _relatieve_ deel van de methode naam.</span><span class="sxs-lookup"><span data-stu-id="d563a-230">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="d563a-231">VI-opdracht modus: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="d563a-231">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="d563a-232">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="d563a-232">DeleteNextLines</span></span>

<span data-ttu-id="d563a-233">Hiermee verwijdert u de huidige logische lijn en de volgende aangevraagde logische regels in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="d563a-233">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="d563a-234">VI-opdracht modus: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="d563a-234">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="d563a-235">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="d563a-235">DeleteLineToFirstChar</span></span>

<span data-ttu-id="d563a-236">Verwijdert uit het eerste niet-lege teken van de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="d563a-236">Deletes from the first non-blank character of the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="d563a-237">VI-opdracht modus: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="d563a-237">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="d563a-238">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="d563a-238">DeleteToEnd</span></span>

<span data-ttu-id="d563a-239">Verwijderen tot aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-239">Delete to the end of the line.</span></span>

- <span data-ttu-id="d563a-240">VI-opdracht modus: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="d563a-240">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="d563a-241">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="d563a-241">DeleteWord</span></span>

<span data-ttu-id="d563a-242">Verwijder het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-242">Delete the next word.</span></span>

- <span data-ttu-id="d563a-243">VI-opdracht modus: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="d563a-243">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="d563a-244">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="d563a-244">ForwardDeleteLine</span></span>

<span data-ttu-id="d563a-245">Net als ForwardKillLine: verwijdert tekst van het punt naar het einde van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="d563a-245">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="d563a-246">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="d563a-246">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="d563a-247">VI Invoeg modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="d563a-247">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="d563a-248">VI-opdracht modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="d563a-248">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="d563a-249">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="d563a-249">InsertLineAbove</span></span>

<span data-ttu-id="d563a-250">Er wordt een nieuwe lege regel gemaakt op de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="d563a-250">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="d563a-251">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-251">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="d563a-252">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d563a-252">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="d563a-253">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="d563a-253">InsertLineBelow</span></span>

<span data-ttu-id="d563a-254">Er wordt een nieuwe lege regel gemaakt onder de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="d563a-254">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="d563a-255">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-255">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="d563a-256">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d563a-256">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="d563a-257">InvertCase</span><span class="sxs-lookup"><span data-stu-id="d563a-257">InvertCase</span></span>

<span data-ttu-id="d563a-258">Het hoofdletter gebruik van het huidige teken omkeren en verplaatsen naar het volgende.</span><span class="sxs-lookup"><span data-stu-id="d563a-258">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="d563a-259">VI-opdracht modus: `<~>`</span><span class="sxs-lookup"><span data-stu-id="d563a-259">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="d563a-260">KillLine</span><span class="sxs-lookup"><span data-stu-id="d563a-260">KillLine</span></span>

<span data-ttu-id="d563a-261">De invoer wissen van de cursor tot het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="d563a-261">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="d563a-262">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="d563a-262">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="d563a-263">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="d563a-263">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="d563a-264">KillRegion</span><span class="sxs-lookup"><span data-stu-id="d563a-264">KillRegion</span></span>

<span data-ttu-id="d563a-265">Beëindig de tekst tussen de cursor en de markering.</span><span class="sxs-lookup"><span data-stu-id="d563a-265">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="d563a-266">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-266">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="d563a-267">KillWord</span><span class="sxs-lookup"><span data-stu-id="d563a-267">KillWord</span></span>

<span data-ttu-id="d563a-268">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-268">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="d563a-269">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-269">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="d563a-270">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="d563a-270">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="d563a-271">Cmd: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="d563a-271">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="d563a-272">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="d563a-272">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="d563a-273">VI Invoeg modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="d563a-273">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="d563a-274">VI-opdracht modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="d563a-274">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="d563a-275">Plakken</span><span class="sxs-lookup"><span data-stu-id="d563a-275">Paste</span></span>

<span data-ttu-id="d563a-276">Tekst van het klem bord van het systeem plakken.</span><span class="sxs-lookup"><span data-stu-id="d563a-276">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="d563a-277">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="d563a-277">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="d563a-278">VI Invoeg modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="d563a-278">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="d563a-279">VI-opdracht modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="d563a-279">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d563a-280">Wanneer u de functie **Paste** gebruikt, wordt de volledige inhoud van de Klembord buffer geplakt in de invoer buffer van PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="d563a-280">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="d563a-281">De invoer buffer wordt vervolgens door gegeven aan de Power shell-parser.</span><span class="sxs-lookup"><span data-stu-id="d563a-281">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="d563a-282">Invoer die met de **rechter muisknop op** de plak methode van de console toepassing wordt geplakt, wordt met één teken per keer naar de invoer buffer gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="d563a-282">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="d563a-283">De invoer buffer wordt door gegeven aan de parser wanneer een teken voor een nieuwe regel wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="d563a-283">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="d563a-284">Daarom wordt de invoer één regel tegelijk geparseerd.</span><span class="sxs-lookup"><span data-stu-id="d563a-284">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="d563a-285">Het verschil tussen plak methoden resulteert in een ander uitvoerings gedrag.</span><span class="sxs-lookup"><span data-stu-id="d563a-285">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="d563a-286">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="d563a-286">PasteAfter</span></span>

<span data-ttu-id="d563a-287">Plak het klem bord na de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="d563a-287">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="d563a-288">VI-opdracht modus: `<p>`</span><span class="sxs-lookup"><span data-stu-id="d563a-288">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="d563a-289">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="d563a-289">PasteBefore</span></span>

<span data-ttu-id="d563a-290">Plak het klem bord vóór de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="d563a-290">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="d563a-291">VI-opdracht modus: `<P>`</span><span class="sxs-lookup"><span data-stu-id="d563a-291">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="d563a-292">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="d563a-292">PrependAndAccept</span></span>

<span data-ttu-id="d563a-293">Laten voorafgaan door een ' # ' en accepteer de regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-293">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="d563a-294">VI-opdracht modus: `<#>`</span><span class="sxs-lookup"><span data-stu-id="d563a-294">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="d563a-295">Opnieuw uitvoeren</span><span class="sxs-lookup"><span data-stu-id="d563a-295">Redo</span></span>

<span data-ttu-id="d563a-296">Undo ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="d563a-296">Undo an undo.</span></span>

- <span data-ttu-id="d563a-297">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="d563a-297">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="d563a-298">VI Invoeg modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="d563a-298">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="d563a-299">VI-opdracht modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="d563a-299">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="d563a-300">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="d563a-300">RepeatLastCommand</span></span>

<span data-ttu-id="d563a-301">Herhaal de laatste tekst wijziging.</span><span class="sxs-lookup"><span data-stu-id="d563a-301">Repeat the last text modification.</span></span>

- <span data-ttu-id="d563a-302">VI-opdracht modus: `<.>`</span><span class="sxs-lookup"><span data-stu-id="d563a-302">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="d563a-303">RevertLine</span><span class="sxs-lookup"><span data-stu-id="d563a-303">RevertLine</span></span>

<span data-ttu-id="d563a-304">Hiermee wordt alle invoer teruggezet naar de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="d563a-304">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="d563a-305">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="d563a-305">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="d563a-306">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="d563a-306">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="d563a-307">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="d563a-307">ShellBackwardKillWord</span></span>

<span data-ttu-id="d563a-308">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-308">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="d563a-309">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="d563a-309">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="d563a-310">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="d563a-310">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="d563a-311">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-311">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="d563a-312">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="d563a-312">ShellKillWord</span></span>

<span data-ttu-id="d563a-313">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-313">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="d563a-314">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-314">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="d563a-315">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="d563a-315">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="d563a-316">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-316">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="d563a-317">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="d563a-317">SwapCharacters</span></span>

<span data-ttu-id="d563a-318">Het huidige teken en de eerste vervangen door wisselen.</span><span class="sxs-lookup"><span data-stu-id="d563a-318">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="d563a-319">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="d563a-319">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="d563a-320">VI Invoeg modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="d563a-320">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="d563a-321">VI-opdracht modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="d563a-321">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="d563a-322">Ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="d563a-322">Undo</span></span>

<span data-ttu-id="d563a-323">Een vorige bewerking ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="d563a-323">Undo a previous edit.</span></span>

- <span data-ttu-id="d563a-324">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="d563a-324">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="d563a-325">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="d563a-325">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="d563a-326">VI Invoeg modus: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="d563a-326">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="d563a-327">VI-opdracht modus: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="d563a-327">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="d563a-328">UndoAll</span><span class="sxs-lookup"><span data-stu-id="d563a-328">UndoAll</span></span>

<span data-ttu-id="d563a-329">Alle vorige bewerkingen voor de regel ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="d563a-329">Undo all previous edits for line.</span></span>

- <span data-ttu-id="d563a-330">VI-opdracht modus: `<U>`</span><span class="sxs-lookup"><span data-stu-id="d563a-330">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="d563a-331">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="d563a-331">UnixWordRubout</span></span>

<span data-ttu-id="d563a-332">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-332">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="d563a-333">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="d563a-333">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="d563a-334">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="d563a-334">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="d563a-335">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="d563a-335">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="d563a-336">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="d563a-336">ValidateAndAcceptLine</span></span>

<span data-ttu-id="d563a-337">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="d563a-337">Attempt to execute the current input.</span></span> <span data-ttu-id="d563a-338">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="d563a-338">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="d563a-339">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="d563a-339">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="d563a-340">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="d563a-340">ViAcceptLine</span></span>

<span data-ttu-id="d563a-341">Accepteer de regel en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="d563a-341">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="d563a-342">VI-opdracht modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="d563a-342">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="d563a-343">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="d563a-343">ViAcceptLineOrExit</span></span>

<span data-ttu-id="d563a-344">Als DeleteCharOrExit in de Emacs-modus, maar wel in plaats van een teken te verwijderen, accepteert u de regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-344">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="d563a-345">VI Invoeg modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="d563a-345">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="d563a-346">VI-opdracht modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="d563a-346">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="d563a-347">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="d563a-347">ViAppendLine</span></span>

<span data-ttu-id="d563a-348">Er wordt een nieuwe regel ingevoegd onder de huidige regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-348">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="d563a-349">VI-opdracht modus: `<o>`</span><span class="sxs-lookup"><span data-stu-id="d563a-349">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="d563a-350">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="d563a-350">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="d563a-351">Hiermee verwijdert u het vorige woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-351">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="d563a-352">VI-opdracht modus: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="d563a-352">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="d563a-353">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="d563a-353">ViBackwardGlob</span></span>

<span data-ttu-id="d563a-354">Verplaatst de cursor terug naar het begin van het vorige woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d563a-354">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="d563a-355">VI-opdracht modus: `<B>`</span><span class="sxs-lookup"><span data-stu-id="d563a-355">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="d563a-356">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="d563a-356">ViDeleteBrace</span></span>

<span data-ttu-id="d563a-357">Zoek de accolade, het haakje sluiten of de vier Kante haken en verwijder alle inhoud binnen, inclusief de accolade.</span><span class="sxs-lookup"><span data-stu-id="d563a-357">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="d563a-358">VI-opdracht modus: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="d563a-358">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="d563a-359">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="d563a-359">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="d563a-360">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-360">Delete to the end of the word.</span></span>

- <span data-ttu-id="d563a-361">VI-opdracht modus: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="d563a-361">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="d563a-362">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="d563a-362">ViDeleteGlob</span></span>

<span data-ttu-id="d563a-363">De volgende Globs verwijderen (door witruimte gescheiden woord).</span><span class="sxs-lookup"><span data-stu-id="d563a-363">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="d563a-364">VI-opdracht modus: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="d563a-364">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="d563a-365">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="d563a-365">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="d563a-366">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-366">Deletes until given character.</span></span>

- <span data-ttu-id="d563a-367">VI-opdracht modus: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="d563a-367">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="d563a-368">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="d563a-368">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="d563a-369">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-369">Deletes until given character.</span></span>

- <span data-ttu-id="d563a-370">VI-opdracht modus: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="d563a-370">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="d563a-371">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="d563a-371">ViDeleteToChar</span></span>

<span data-ttu-id="d563a-372">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-372">Deletes until given character.</span></span>

- <span data-ttu-id="d563a-373">VI-opdracht modus: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="d563a-373">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="d563a-374">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="d563a-374">ViDeleteToCharBackward</span></span>

<span data-ttu-id="d563a-375">Hiermee verwijdert u achterwaartse tekens tot aan het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-375">Deletes backwards until given character.</span></span>

- <span data-ttu-id="d563a-376">VI-opdracht modus: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="d563a-376">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="d563a-377">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="d563a-377">ViInsertAtBegining</span></span>

<span data-ttu-id="d563a-378">Schakel over naar de Invoeg modus en plaats de cursor aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-378">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="d563a-379">VI-opdracht modus: `<I>`</span><span class="sxs-lookup"><span data-stu-id="d563a-379">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="d563a-380">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="d563a-380">ViInsertAtEnd</span></span>

<span data-ttu-id="d563a-381">Schakel over naar de Invoeg modus en plaats de cursor aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-381">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="d563a-382">VI-opdracht modus: `<A>`</span><span class="sxs-lookup"><span data-stu-id="d563a-382">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="d563a-383">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="d563a-383">ViInsertLine</span></span>

<span data-ttu-id="d563a-384">Boven de huidige regel wordt een nieuwe regel ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="d563a-384">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="d563a-385">VI-opdracht modus: `<O>`</span><span class="sxs-lookup"><span data-stu-id="d563a-385">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="d563a-386">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="d563a-386">ViInsertWithAppend</span></span>

<span data-ttu-id="d563a-387">Toevoegen vanaf de huidige regel positie.</span><span class="sxs-lookup"><span data-stu-id="d563a-387">Append from the current line position.</span></span>

- <span data-ttu-id="d563a-388">VI-opdracht modus: `<a>`</span><span class="sxs-lookup"><span data-stu-id="d563a-388">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="d563a-389">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="d563a-389">ViInsertWithDelete</span></span>

<span data-ttu-id="d563a-390">Verwijder het huidige teken en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="d563a-390">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="d563a-391">VI-opdracht modus: `<s>`</span><span class="sxs-lookup"><span data-stu-id="d563a-391">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="d563a-392">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="d563a-392">ViJoinLines</span></span>

<span data-ttu-id="d563a-393">De huidige regel en de volgende regel worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="d563a-393">Joins the current line and the next line.</span></span>

- <span data-ttu-id="d563a-394">VI-opdracht modus: `<J>`</span><span class="sxs-lookup"><span data-stu-id="d563a-394">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="d563a-395">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="d563a-395">ViReplaceLine</span></span>

<span data-ttu-id="d563a-396">De volledige opdracht regel wissen.</span><span class="sxs-lookup"><span data-stu-id="d563a-396">Erase the entire command line.</span></span>

- <span data-ttu-id="d563a-397">VI-opdracht modus: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="d563a-397">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="d563a-398">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="d563a-398">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="d563a-399">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-399">Replaces until given character.</span></span>

- <span data-ttu-id="d563a-400">VI-opdracht modus: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="d563a-400">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="d563a-401">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="d563a-401">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="d563a-402">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-402">Replaces until given character.</span></span>

- <span data-ttu-id="d563a-403">VI-opdracht modus: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="d563a-403">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="d563a-404">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="d563a-404">ViReplaceToChar</span></span>

<span data-ttu-id="d563a-405">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-405">Deletes until given character.</span></span>

- <span data-ttu-id="d563a-406">VI-opdracht modus: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="d563a-406">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="d563a-407">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="d563a-407">ViReplaceToCharBackward</span></span>

<span data-ttu-id="d563a-408">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-408">Replaces until given character.</span></span>

- <span data-ttu-id="d563a-409">VI-opdracht modus: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="d563a-409">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="d563a-410">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="d563a-410">ViYankBeginningOfLine</span></span>

<span data-ttu-id="d563a-411">Yank vanaf het begin van de buffer naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-411">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="d563a-412">VI-opdracht modus: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="d563a-412">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="d563a-413">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="d563a-413">ViYankEndOfGlob</span></span>

<span data-ttu-id="d563a-414">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="d563a-414">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="d563a-415">VI-opdracht modus: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="d563a-415">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="d563a-416">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="d563a-416">ViYankEndOfWord</span></span>

<span data-ttu-id="d563a-417">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="d563a-417">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="d563a-418">VI-opdracht modus: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="d563a-418">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="d563a-419">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="d563a-419">ViYankLeft</span></span>

<span data-ttu-id="d563a-420">Yank teken (s) links van de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-420">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="d563a-421">VI-opdracht modus: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="d563a-421">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="d563a-422">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="d563a-422">ViYankLine</span></span>

<span data-ttu-id="d563a-423">Yank de volledige buffer.</span><span class="sxs-lookup"><span data-stu-id="d563a-423">Yank the entire buffer.</span></span>

- <span data-ttu-id="d563a-424">VI-opdracht modus: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="d563a-424">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="d563a-425">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="d563a-425">ViYankNextGlob</span></span>

<span data-ttu-id="d563a-426">Yank van de cursor naar het begin van de volgende woord (en).</span><span class="sxs-lookup"><span data-stu-id="d563a-426">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="d563a-427">VI-opdracht modus: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="d563a-427">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="d563a-428">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="d563a-428">ViYankNextWord</span></span>

<span data-ttu-id="d563a-429">Yank het woord (en) na de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-429">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="d563a-430">VI-opdracht modus: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="d563a-430">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="d563a-431">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="d563a-431">ViYankPercent</span></span>

<span data-ttu-id="d563a-432">Yank naar/van overeenkomende accolade.</span><span class="sxs-lookup"><span data-stu-id="d563a-432">Yank to/from matching brace.</span></span>

- <span data-ttu-id="d563a-433">VI-opdracht modus: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="d563a-433">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="d563a-434">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="d563a-434">ViYankPreviousGlob</span></span>

<span data-ttu-id="d563a-435">Yank vanaf het begin van het (de) woord (en) tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-435">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="d563a-436">VI-opdracht modus: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="d563a-436">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="d563a-437">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="d563a-437">ViYankPreviousWord</span></span>

<span data-ttu-id="d563a-438">Yank de woorden vóór de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-438">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="d563a-439">VI-opdracht modus: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="d563a-439">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="d563a-440">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="d563a-440">ViYankRight</span></span>

<span data-ttu-id="d563a-441">Yank teken (s) onder en rechts van de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-441">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="d563a-442">VI-opdracht modus: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="d563a-442">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="d563a-443">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="d563a-443">ViYankToEndOfLine</span></span>

<span data-ttu-id="d563a-444">Yank van de cursor tot het einde van de buffer.</span><span class="sxs-lookup"><span data-stu-id="d563a-444">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="d563a-445">VI-opdracht modus: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="d563a-445">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="d563a-446">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="d563a-446">ViYankToFirstChar</span></span>

<span data-ttu-id="d563a-447">Yank van het eerste niet-spatie teken tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-447">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="d563a-448">VI-opdracht modus: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="d563a-448">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="d563a-449">Yank</span><span class="sxs-lookup"><span data-stu-id="d563a-449">Yank</span></span>

<span data-ttu-id="d563a-450">Voeg de meest recent afgebroken tekst toe aan de invoer.</span><span class="sxs-lookup"><span data-stu-id="d563a-450">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="d563a-451">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="d563a-451">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="d563a-452">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="d563a-452">YankLastArg</span></span>

<span data-ttu-id="d563a-453">Yank het laatste argument van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-453">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="d563a-454">Met een argument, de eerste keer dat deze wordt aangeroepen, gedraagt zich op dezelfde manier als YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="d563a-454">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="d563a-455">Als meerdere keren worden aangeroepen, wordt door de geschiedenis en ARG de richting ingesteld (negatief de richting omkeren.)</span><span class="sxs-lookup"><span data-stu-id="d563a-455">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="d563a-456">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="d563a-456">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="d563a-457">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="d563a-457">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="d563a-458">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="d563a-458">YankNthArg</span></span>

<span data-ttu-id="d563a-459">Yank het eerste argument (na de opdracht) van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-459">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="d563a-460">Met een argument, Yank het ne argument (vanaf 0), als het argument negatief is, begint vanaf het laatste argument.</span><span class="sxs-lookup"><span data-stu-id="d563a-460">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="d563a-461">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="d563a-461">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="d563a-462">YankPop</span><span class="sxs-lookup"><span data-stu-id="d563a-462">YankPop</span></span>

<span data-ttu-id="d563a-463">Als de vorige bewerking Yank of YankPop is, vervangt u de eerder yanked tekst door de volgende afgebroken tekst van de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="d563a-463">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="d563a-464">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="d563a-464">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="d563a-465">Functies voor cursor verplaatsing</span><span class="sxs-lookup"><span data-stu-id="d563a-465">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="d563a-466">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="d563a-466">BackwardChar</span></span>

<span data-ttu-id="d563a-467">De cursor één teken naar links verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="d563a-467">Move the cursor one character to the left.</span></span> <span data-ttu-id="d563a-468">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="d563a-468">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="d563a-469">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-469">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="d563a-470">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="d563a-470">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="d563a-471">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="d563a-471">BackwardWord</span></span>

<span data-ttu-id="d563a-472">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-472">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="d563a-473">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="d563a-473">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d563a-474">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-474">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="d563a-475">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="d563a-475">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="d563a-476">VI Invoeg modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-476">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="d563a-477">VI-opdracht modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-477">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="d563a-478">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="d563a-478">BeginningOfLine</span></span>

<span data-ttu-id="d563a-479">Als de invoer meerdere regels heeft, gaat u naar het begin van de huidige regel of gaat u naar het begin van de invoer als deze al aan het begin van de regel staat.</span><span class="sxs-lookup"><span data-stu-id="d563a-479">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="d563a-480">Als de invoer één regel heeft, gaat u naar het begin van de invoer.</span><span class="sxs-lookup"><span data-stu-id="d563a-480">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="d563a-481">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="d563a-481">Cmd: `<Home>`</span></span>
- <span data-ttu-id="d563a-482">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="d563a-482">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="d563a-483">VI Invoeg modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="d563a-483">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="d563a-484">VI-opdracht modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="d563a-484">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="d563a-485">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="d563a-485">EndOfLine</span></span>

<span data-ttu-id="d563a-486">Als de invoer meerdere regels heeft, gaat u naar het einde van de huidige regel of gaat u naar het einde van de invoer als u aan het einde van de regel bent.</span><span class="sxs-lookup"><span data-stu-id="d563a-486">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="d563a-487">Als de invoer één regel heeft, gaat u naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="d563a-487">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="d563a-488">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="d563a-488">Cmd: `<End>`</span></span>
- <span data-ttu-id="d563a-489">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="d563a-489">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="d563a-490">VI Invoeg modus: `<End>`</span><span class="sxs-lookup"><span data-stu-id="d563a-490">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="d563a-491">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="d563a-491">ForwardChar</span></span>

<span data-ttu-id="d563a-492">De cursor één teken naar rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="d563a-492">Move the cursor one character to the right.</span></span> <span data-ttu-id="d563a-493">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="d563a-493">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="d563a-494">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-494">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="d563a-495">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="d563a-495">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="d563a-496">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="d563a-496">ForwardWord</span></span>

<span data-ttu-id="d563a-497">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-497">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="d563a-498">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="d563a-498">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d563a-499">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="d563a-499">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="d563a-500">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="d563a-500">GotoBrace</span></span>

<span data-ttu-id="d563a-501">Ga naar de accolade, haakjes of vier Kante haakjes.</span><span class="sxs-lookup"><span data-stu-id="d563a-501">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="d563a-502">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="d563a-502">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="d563a-503">VI Invoeg modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="d563a-503">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="d563a-504">VI-opdracht modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="d563a-504">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="d563a-505">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="d563a-505">GotoColumn</span></span>

<span data-ttu-id="d563a-506">Ga naar de kolom die wordt aangegeven door arg.</span><span class="sxs-lookup"><span data-stu-id="d563a-506">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="d563a-507">VI-opdracht modus: `<|>`</span><span class="sxs-lookup"><span data-stu-id="d563a-507">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="d563a-508">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="d563a-508">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="d563a-509">De cursor verplaatsen naar het eerste niet-lege teken in de regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-509">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="d563a-510">VI-opdracht modus: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="d563a-510">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="d563a-511">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="d563a-511">MoveToEndOfLine</span></span>

<span data-ttu-id="d563a-512">De cursor verplaatsen naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="d563a-512">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="d563a-513">VI-opdracht modus: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="d563a-513">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="d563a-514">NextLine</span><span class="sxs-lookup"><span data-stu-id="d563a-514">NextLine</span></span>

<span data-ttu-id="d563a-515">De cursor verplaatsen naar de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-515">Move the cursor to the next line.</span></span>

- <span data-ttu-id="d563a-516">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-516">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="d563a-517">NextWord</span><span class="sxs-lookup"><span data-stu-id="d563a-517">NextWord</span></span>

<span data-ttu-id="d563a-518">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-518">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="d563a-519">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="d563a-519">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d563a-520">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-520">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="d563a-521">VI Invoeg modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-521">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="d563a-522">VI-opdracht modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-522">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="d563a-523">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="d563a-523">NextWordEnd</span></span>

<span data-ttu-id="d563a-524">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-524">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="d563a-525">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="d563a-525">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d563a-526">VI-opdracht modus: `<e>`</span><span class="sxs-lookup"><span data-stu-id="d563a-526">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="d563a-527">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="d563a-527">PreviousLine</span></span>

<span data-ttu-id="d563a-528">Verplaats de cursor naar de vorige regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-528">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="d563a-529">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-529">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="d563a-530">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="d563a-530">ShellBackwardWord</span></span>

<span data-ttu-id="d563a-531">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-531">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="d563a-532">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="d563a-532">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="d563a-533">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-533">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="d563a-534">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="d563a-534">ShellForwardWord</span></span>

<span data-ttu-id="d563a-535">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-535">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="d563a-536">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="d563a-536">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="d563a-537">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-537">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="d563a-538">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="d563a-538">ShellNextWord</span></span>

<span data-ttu-id="d563a-539">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-539">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="d563a-540">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="d563a-540">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="d563a-541">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-541">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="d563a-542">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="d563a-542">ViBackwardChar</span></span>

<span data-ttu-id="d563a-543">De cursor één teken naar links verplaatsen in de bewerkings modus VI.</span><span class="sxs-lookup"><span data-stu-id="d563a-543">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="d563a-544">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="d563a-544">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="d563a-545">VI Invoeg modus: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-545">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="d563a-546">VI-opdracht modus: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="d563a-546">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="d563a-547">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="d563a-547">ViBackwardWord</span></span>

<span data-ttu-id="d563a-548">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-548">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="d563a-549">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="d563a-549">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d563a-550">VI-opdracht modus: `<b>`</span><span class="sxs-lookup"><span data-stu-id="d563a-550">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="d563a-551">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="d563a-551">ViForwardChar</span></span>

<span data-ttu-id="d563a-552">De cursor één teken naar rechts verplaatsen in de bewerkings modus VI.</span><span class="sxs-lookup"><span data-stu-id="d563a-552">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="d563a-553">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="d563a-553">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="d563a-554">VI Invoeg modus: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-554">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="d563a-555">VI-opdracht modus: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="d563a-555">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="d563a-556">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="d563a-556">ViEndOfGlob</span></span>

<span data-ttu-id="d563a-557">Verplaatst de cursor naar het einde van het woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d563a-557">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="d563a-558">VI-opdracht modus: `<E>`</span><span class="sxs-lookup"><span data-stu-id="d563a-558">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="d563a-559">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="d563a-559">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="d563a-560">Wordt verplaatst naar het einde van het vorige woord, waarbij alleen witruimte wordt gebruikt als woord als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-560">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="d563a-561">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-561">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="d563a-562">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="d563a-562">ViGotoBrace</span></span>

<span data-ttu-id="d563a-563">Vergelijkbaar met GotoBrace, maar is in plaats van op tokens gebaseerd.</span><span class="sxs-lookup"><span data-stu-id="d563a-563">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="d563a-564">VI-opdracht modus: `<%>`</span><span class="sxs-lookup"><span data-stu-id="d563a-564">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="d563a-565">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="d563a-565">ViNextGlob</span></span>

<span data-ttu-id="d563a-566">Verplaatst naar het volgende woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-566">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="d563a-567">VI-opdracht modus: `<W>`</span><span class="sxs-lookup"><span data-stu-id="d563a-567">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="d563a-568">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="d563a-568">ViNextWord</span></span>

<span data-ttu-id="d563a-569">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="d563a-569">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="d563a-570">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="d563a-570">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d563a-571">VI-opdracht modus: `<w>`</span><span class="sxs-lookup"><span data-stu-id="d563a-571">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="d563a-572">Geschiedenis functies</span><span class="sxs-lookup"><span data-stu-id="d563a-572">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="d563a-573">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="d563a-573">BeginningOfHistory</span></span>

<span data-ttu-id="d563a-574">Hiermee gaat u naar het eerste item in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="d563a-574">Move to the first item in the history.</span></span>

- <span data-ttu-id="d563a-575">Emacs: `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="d563a-575">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="d563a-576">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="d563a-576">ClearHistory</span></span>

<span data-ttu-id="d563a-577">Hiermee wist u de geschiedenis in PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="d563a-577">Clears history in PSReadLine.</span></span> <span data-ttu-id="d563a-578">Dit heeft geen invloed op de Power shell-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="d563a-578">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="d563a-579">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="d563a-579">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="d563a-580">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="d563a-580">EndOfHistory</span></span>

<span data-ttu-id="d563a-581">Hiermee gaat u naar het laatste item (de huidige invoer) in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="d563a-581">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="d563a-582">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="d563a-582">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="d563a-583">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="d563a-583">ForwardSearchHistory</span></span>

<span data-ttu-id="d563a-584">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="d563a-584">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="d563a-585">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="d563a-585">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="d563a-586">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="d563a-586">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="d563a-587">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="d563a-587">HistorySearchBackward</span></span>

<span data-ttu-id="d563a-588">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-588">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="d563a-589">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="d563a-589">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="d563a-590">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="d563a-590">HistorySearchForward</span></span>

<span data-ttu-id="d563a-591">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-591">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="d563a-592">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="d563a-592">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="d563a-593">NextHistory</span><span class="sxs-lookup"><span data-stu-id="d563a-593">NextHistory</span></span>

<span data-ttu-id="d563a-594">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="d563a-594">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="d563a-595">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-595">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="d563a-596">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="d563a-596">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="d563a-597">VI Invoeg modus: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-597">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="d563a-598">VI-opdracht modus: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="d563a-598">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="d563a-599">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="d563a-599">PreviousHistory</span></span>

<span data-ttu-id="d563a-600">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="d563a-600">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="d563a-601">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-601">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="d563a-602">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="d563a-602">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="d563a-603">VI Invoeg modus: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-603">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="d563a-604">VI-opdracht modus: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="d563a-604">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="d563a-605">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="d563a-605">ReverseSearchHistory</span></span>

<span data-ttu-id="d563a-606">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="d563a-606">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="d563a-607">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="d563a-607">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="d563a-608">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="d563a-608">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="d563a-609">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="d563a-609">ViSearchHistoryBackward</span></span>

<span data-ttu-id="d563a-610">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="d563a-610">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="d563a-611">VI Invoeg modus: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="d563a-611">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="d563a-612">VI-opdracht modus: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="d563a-612">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="d563a-613">Voltooiings functies</span><span class="sxs-lookup"><span data-stu-id="d563a-613">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="d563a-614">Voltooid</span><span class="sxs-lookup"><span data-stu-id="d563a-614">Complete</span></span>

<span data-ttu-id="d563a-615">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-615">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="d563a-616">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="d563a-616">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="d563a-617">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d563a-617">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="d563a-618">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="d563a-618">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="d563a-619">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="d563a-619">MenuComplete</span></span>

<span data-ttu-id="d563a-620">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-620">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="d563a-621">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="d563a-621">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="d563a-622">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d563a-622">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="d563a-623">Cmd: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="d563a-623">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="d563a-624">Emacs: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="d563a-624">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="d563a-625">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="d563a-625">PossibleCompletions</span></span>

<span data-ttu-id="d563a-626">De lijst met mogelijke aanvullingen weer geven.</span><span class="sxs-lookup"><span data-stu-id="d563a-626">Display the list of possible completions.</span></span>

- <span data-ttu-id="d563a-627">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="d563a-627">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="d563a-628">VI Invoeg modus: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="d563a-628">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="d563a-629">VI-opdracht modus: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="d563a-629">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="d563a-630">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="d563a-630">TabCompleteNext</span></span>

<span data-ttu-id="d563a-631">Poging om de tekst rond de cursor te volt ooien met de volgende beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="d563a-631">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="d563a-632">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="d563a-632">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="d563a-633">VI-opdracht modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="d563a-633">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="d563a-634">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="d563a-634">TabCompletePrevious</span></span>

<span data-ttu-id="d563a-635">Poging om de tekst rond de cursor te volt ooien met de vorige beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="d563a-635">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="d563a-636">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="d563a-636">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="d563a-637">VI-opdracht modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="d563a-637">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="d563a-638">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="d563a-638">ViTabCompleteNext</span></span>

<span data-ttu-id="d563a-639">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompleteNext aan.</span><span class="sxs-lookup"><span data-stu-id="d563a-639">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="d563a-640">VI Invoeg modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="d563a-640">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="d563a-641">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="d563a-641">ViTabCompletePrevious</span></span>

<span data-ttu-id="d563a-642">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompletePrevious aan.</span><span class="sxs-lookup"><span data-stu-id="d563a-642">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="d563a-643">VI Invoeg modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="d563a-643">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="d563a-644">Diverse functies</span><span class="sxs-lookup"><span data-stu-id="d563a-644">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="d563a-645">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="d563a-645">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="d563a-646">Het volgende woord van de inline of geselecteerde suggestie accepteren.</span><span class="sxs-lookup"><span data-stu-id="d563a-646">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="d563a-647">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-647">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="d563a-648">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="d563a-648">AcceptSuggestion</span></span>

<span data-ttu-id="d563a-649">De huidige inline of geselecteerde suggestie accepteren.</span><span class="sxs-lookup"><span data-stu-id="d563a-649">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="d563a-650">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-650">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="d563a-651">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="d563a-651">CaptureScreen</span></span>

<span data-ttu-id="d563a-652">Interactieve scherm opname starten-pijl-omhoog/omlaag Selecteer regels en voer de geselecteerde tekst als tekst en HTML naar het klem bord kopiëren.</span><span class="sxs-lookup"><span data-stu-id="d563a-652">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="d563a-653">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-653">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="d563a-654">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="d563a-654">ClearScreen</span></span>

<span data-ttu-id="d563a-655">Schakel het scherm uit en teken de huidige regel boven aan het scherm.</span><span class="sxs-lookup"><span data-stu-id="d563a-655">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="d563a-656">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="d563a-656">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="d563a-657">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="d563a-657">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="d563a-658">VI Invoeg modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="d563a-658">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="d563a-659">VI-opdracht modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="d563a-659">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="d563a-660">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="d563a-660">DigitArgument</span></span>

<span data-ttu-id="d563a-661">Start een nieuw cijfer argument om door te geven aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="d563a-661">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="d563a-662">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="d563a-662">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="d563a-663">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="d563a-663">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="d563a-664">VI-opdracht modus: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="d563a-664">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="d563a-665">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="d563a-665">InvokePrompt</span></span>

<span data-ttu-id="d563a-666">Hiermee wordt de huidige prompt gewist en wordt de functie Prompt aangeroepen om de prompt opnieuw weer te geven.</span><span class="sxs-lookup"><span data-stu-id="d563a-666">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="d563a-667">Dit is handig voor aangepaste sleutel afhandelingen die de status wijzigen, bijvoorbeeld de huidige map wijzigen.</span><span class="sxs-lookup"><span data-stu-id="d563a-667">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="d563a-668">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-668">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="d563a-669">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="d563a-669">ScrollDisplayDown</span></span>

<span data-ttu-id="d563a-670">De weer gave één scherm omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="d563a-670">Scroll the display down one screen.</span></span>

- <span data-ttu-id="d563a-671">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="d563a-671">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="d563a-672">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="d563a-672">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="d563a-673">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="d563a-673">ScrollDisplayDownLine</span></span>

<span data-ttu-id="d563a-674">De weer gave één regel omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="d563a-674">Scroll the display down one line.</span></span>

- <span data-ttu-id="d563a-675">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="d563a-675">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="d563a-676">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="d563a-676">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="d563a-677">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="d563a-677">ScrollDisplayToCursor</span></span>

<span data-ttu-id="d563a-678">Schuif de weer gave naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-678">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="d563a-679">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="d563a-679">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="d563a-680">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="d563a-680">ScrollDisplayTop</span></span>

<span data-ttu-id="d563a-681">Schuif de weer gave naar boven.</span><span class="sxs-lookup"><span data-stu-id="d563a-681">Scroll the display to the top.</span></span>

- <span data-ttu-id="d563a-682">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="d563a-682">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="d563a-683">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="d563a-683">ScrollDisplayUp</span></span>

<span data-ttu-id="d563a-684">Schuif de weer gave één scherm omhoog.</span><span class="sxs-lookup"><span data-stu-id="d563a-684">Scroll the display up one screen.</span></span>

- <span data-ttu-id="d563a-685">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="d563a-685">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="d563a-686">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="d563a-686">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="d563a-687">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="d563a-687">ScrollDisplayUpLine</span></span>

<span data-ttu-id="d563a-688">De weer gave één regel omhoog schuiven.</span><span class="sxs-lookup"><span data-stu-id="d563a-688">Scroll the display up one line.</span></span>

- <span data-ttu-id="d563a-689">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="d563a-689">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="d563a-690">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="d563a-690">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="d563a-691">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="d563a-691">SelfInsert</span></span>

<span data-ttu-id="d563a-692">Voeg de sleutel in.</span><span class="sxs-lookup"><span data-stu-id="d563a-692">Insert the key.</span></span>

- <span data-ttu-id="d563a-693">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-693">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="d563a-694">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="d563a-694">ShowKeyBindings</span></span>

<span data-ttu-id="d563a-695">Alle gebonden sleutels weer geven.</span><span class="sxs-lookup"><span data-stu-id="d563a-695">Show all bound keys.</span></span>

- <span data-ttu-id="d563a-696">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="d563a-696">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="d563a-697">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="d563a-697">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="d563a-698">VI Invoeg modus: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="d563a-698">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="d563a-699">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="d563a-699">ViCommandMode</span></span>

<span data-ttu-id="d563a-700">Schakel de huidige bedrijfs modus uit van Vi-Insert naar de VI-opdracht.</span><span class="sxs-lookup"><span data-stu-id="d563a-700">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="d563a-701">VI Invoeg modus: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="d563a-701">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="d563a-702">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="d563a-702">ViDigitArgumentInChord</span></span>

<span data-ttu-id="d563a-703">Start een nieuw cijfer argument om door te geven aan andere functies in een van de koorden van VI.</span><span class="sxs-lookup"><span data-stu-id="d563a-703">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="d563a-704">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-704">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="d563a-705">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="d563a-705">ViEditVisually</span></span>

<span data-ttu-id="d563a-706">Bewerk de opdracht regel in een tekst editor die is opgegeven door $env: EDITOR of $env: VISUAL.</span><span class="sxs-lookup"><span data-stu-id="d563a-706">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="d563a-707">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="d563a-707">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="d563a-708">VI-opdracht modus: `<v>`</span><span class="sxs-lookup"><span data-stu-id="d563a-708">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="d563a-709">ViExit</span><span class="sxs-lookup"><span data-stu-id="d563a-709">ViExit</span></span>

<span data-ttu-id="d563a-710">Hiermee wordt de shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="d563a-710">Exits the shell.</span></span>

- <span data-ttu-id="d563a-711">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-711">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="d563a-712">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="d563a-712">ViInsertMode</span></span>

<span data-ttu-id="d563a-713">Schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="d563a-713">Switch to Insert mode.</span></span>

- <span data-ttu-id="d563a-714">VI-opdracht modus: `<i>`</span><span class="sxs-lookup"><span data-stu-id="d563a-714">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="d563a-715">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="d563a-715">WhatIsKey</span></span>

<span data-ttu-id="d563a-716">Lees een sleutel en vertel me wat de sleutel is gebonden.</span><span class="sxs-lookup"><span data-stu-id="d563a-716">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="d563a-717">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="d563a-717">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="d563a-718">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="d563a-718">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="d563a-719">Selectie functies</span><span class="sxs-lookup"><span data-stu-id="d563a-719">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="d563a-720">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="d563a-720">ExchangePointAndMark</span></span>

<span data-ttu-id="d563a-721">De cursor wordt op de locatie van het merk geplaatst en het vinkje wordt verplaatst naar de locatie van de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-721">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="d563a-722">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="d563a-722">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="d563a-723">SelectAll aanroepen</span><span class="sxs-lookup"><span data-stu-id="d563a-723">SelectAll</span></span>

<span data-ttu-id="d563a-724">Selecteer de volledige regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-724">Select the entire line.</span></span>

- <span data-ttu-id="d563a-725">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="d563a-725">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="d563a-726">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="d563a-726">SelectBackwardChar</span></span>

<span data-ttu-id="d563a-727">Pas de huidige selectie aan om het vorige teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="d563a-727">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="d563a-728">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-728">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="d563a-729">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-729">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="d563a-730">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="d563a-730">SelectBackwardsLine</span></span>

<span data-ttu-id="d563a-731">Pas de huidige selectie aan de cursor toe aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-731">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="d563a-732">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="d563a-732">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="d563a-733">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="d563a-733">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="d563a-734">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="d563a-734">SelectBackwardWord</span></span>

<span data-ttu-id="d563a-735">Pas de huidige selectie aan om het vorige woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="d563a-735">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="d563a-736">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-736">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="d563a-737">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="d563a-737">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="d563a-738">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="d563a-738">SelectForwardChar</span></span>

<span data-ttu-id="d563a-739">Pas de huidige selectie aan om het volgende teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="d563a-739">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="d563a-740">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-740">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="d563a-741">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-741">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="d563a-742">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="d563a-742">SelectForwardWord</span></span>

<span data-ttu-id="d563a-743">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="d563a-743">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="d563a-744">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="d563a-744">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="d563a-745">SelectLine</span><span class="sxs-lookup"><span data-stu-id="d563a-745">SelectLine</span></span>

<span data-ttu-id="d563a-746">Pas de huidige selectie aan de cursor toe aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-746">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="d563a-747">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="d563a-747">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="d563a-748">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="d563a-748">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="d563a-749">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="d563a-749">SelectNextWord</span></span>

<span data-ttu-id="d563a-750">Pas de huidige selectie aan om het volgende woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="d563a-750">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="d563a-751">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d563a-751">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="d563a-752">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="d563a-752">SelectShellBackwardWord</span></span>

<span data-ttu-id="d563a-753">Pas de huidige selectie aan om het vorige woord op te maken met behulp van ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="d563a-753">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="d563a-754">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-754">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="d563a-755">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="d563a-755">SelectShellForwardWord</span></span>

<span data-ttu-id="d563a-756">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="d563a-756">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="d563a-757">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-757">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="d563a-758">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="d563a-758">SelectShellNextWord</span></span>

<span data-ttu-id="d563a-759">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="d563a-759">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="d563a-760">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="d563a-760">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="d563a-761">SetMark</span><span class="sxs-lookup"><span data-stu-id="d563a-761">SetMark</span></span>

<span data-ttu-id="d563a-762">De huidige locatie van de cursor markeren voor gebruik in een volgende bewerkings opdracht.</span><span class="sxs-lookup"><span data-stu-id="d563a-762">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="d563a-763">Emacs: `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="d563a-763">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="d563a-764">Voorspellende IntelliSense-functies</span><span class="sxs-lookup"><span data-stu-id="d563a-764">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="d563a-765">Voorspellende IntelliSense moet zijn ingeschakeld om deze functies te kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d563a-765">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="d563a-766">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="d563a-766">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="d563a-767">Hiermee wordt het volgende woord van de inline suggestie geaccepteerd van voorspellende IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="d563a-767">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="d563a-768">Deze functie kan worden gebonden met <kbd>CTRL</kbd> + <kbd>F</kbd> door de volgende opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d563a-768">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="d563a-769">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="d563a-769">AcceptSuggestion</span></span>

<span data-ttu-id="d563a-770">Hiermee wordt de huidige inline suggestie van voorspellende IntelliSense geaccepteerd door op <kbd>RightArrow</kbd> te drukken wanneer de cursor zich aan het einde van de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="d563a-770">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="d563a-771">Zoek functies</span><span class="sxs-lookup"><span data-stu-id="d563a-771">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="d563a-772">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="d563a-772">CharacterSearch</span></span>

<span data-ttu-id="d563a-773">Lees een teken en zoek voorwaarts naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-773">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="d563a-774">Als er een argument is opgegeven, zoekt u voorwaarts (of achterwaarts als negatieve) voor het ne voorval.</span><span class="sxs-lookup"><span data-stu-id="d563a-774">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="d563a-775">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="d563a-775">Cmd: `<F3>`</span></span>
- <span data-ttu-id="d563a-776">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="d563a-776">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="d563a-777">VI Invoeg modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="d563a-777">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="d563a-778">VI-opdracht modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="d563a-778">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="d563a-779">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="d563a-779">CharacterSearchBackward</span></span>

<span data-ttu-id="d563a-780">Lees een teken en zoek terug naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-780">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="d563a-781">Als er een argument is opgegeven, zoekt u terug (of als dit negatief is) voor het ne exemplaar.</span><span class="sxs-lookup"><span data-stu-id="d563a-781">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="d563a-782">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="d563a-782">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="d563a-783">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="d563a-783">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="d563a-784">VI Invoeg modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="d563a-784">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="d563a-785">VI-opdracht modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="d563a-785">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="d563a-786">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="d563a-786">RepeatLastCharSearch</span></span>

<span data-ttu-id="d563a-787">De laatst opgenomen zoek opdracht herhalen.</span><span class="sxs-lookup"><span data-stu-id="d563a-787">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="d563a-788">VI-opdracht modus: `<;>`</span><span class="sxs-lookup"><span data-stu-id="d563a-788">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="d563a-789">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="d563a-789">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="d563a-790">De laatst opgenomen zoek opdracht herhalen, maar in tegenovergestelde richting.</span><span class="sxs-lookup"><span data-stu-id="d563a-790">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="d563a-791">VI-opdracht modus: `<,>`</span><span class="sxs-lookup"><span data-stu-id="d563a-791">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="d563a-792">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="d563a-792">RepeatSearch</span></span>

<span data-ttu-id="d563a-793">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="d563a-793">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="d563a-794">VI-opdracht modus: `<n>`</span><span class="sxs-lookup"><span data-stu-id="d563a-794">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="d563a-795">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="d563a-795">RepeatSearchBackward</span></span>

<span data-ttu-id="d563a-796">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="d563a-796">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="d563a-797">VI-opdracht modus: `<N>`</span><span class="sxs-lookup"><span data-stu-id="d563a-797">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="d563a-798">SearchChar</span><span class="sxs-lookup"><span data-stu-id="d563a-798">SearchChar</span></span>

<span data-ttu-id="d563a-799">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-799">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="d563a-800">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="d563a-800">This is for 't' functionality.</span></span>

- <span data-ttu-id="d563a-801">VI-opdracht modus: `<f>`</span><span class="sxs-lookup"><span data-stu-id="d563a-801">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="d563a-802">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="d563a-802">SearchCharBackward</span></span>

<span data-ttu-id="d563a-803">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-803">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="d563a-804">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="d563a-804">This is for 'T' functionality.</span></span>

- <span data-ttu-id="d563a-805">VI-opdracht modus: `<F>`</span><span class="sxs-lookup"><span data-stu-id="d563a-805">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="d563a-806">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="d563a-806">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="d563a-807">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-807">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="d563a-808">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="d563a-808">This is for 'T' functionality.</span></span>

- <span data-ttu-id="d563a-809">VI-opdracht modus: `<T>`</span><span class="sxs-lookup"><span data-stu-id="d563a-809">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="d563a-810">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="d563a-810">SearchCharWithBackoff</span></span>

<span data-ttu-id="d563a-811">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="d563a-811">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="d563a-812">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="d563a-812">This is for 't' functionality.</span></span>

- <span data-ttu-id="d563a-813">VI-opdracht modus: `<t>`</span><span class="sxs-lookup"><span data-stu-id="d563a-813">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="d563a-814">SearchForward</span><span class="sxs-lookup"><span data-stu-id="d563a-814">SearchForward</span></span>

<span data-ttu-id="d563a-815">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="d563a-815">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="d563a-816">VI Invoeg modus: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="d563a-816">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="d563a-817">VI-opdracht modus: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="d563a-817">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="d563a-818">Aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="d563a-818">Custom Key Bindings</span></span>

<span data-ttu-id="d563a-819">PSReadLine ondersteunt aangepaste sleutel bindingen met behulp van de-cmdlet `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="d563a-819">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="d563a-820">De meeste aangepaste sleutel bindingen roepen een van de bovenstaande functies aan, bijvoorbeeld</span><span class="sxs-lookup"><span data-stu-id="d563a-820">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="d563a-821">U kunt een script Block binden aan een sleutel.</span><span class="sxs-lookup"><span data-stu-id="d563a-821">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="d563a-822">Het script Block kan veel wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="d563a-822">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="d563a-823">Enkele handige voor beelden zijn</span><span class="sxs-lookup"><span data-stu-id="d563a-823">Some useful examples include</span></span>

- <span data-ttu-id="d563a-824">de opdracht regel bewerken</span><span class="sxs-lookup"><span data-stu-id="d563a-824">edit the command line</span></span>
- <span data-ttu-id="d563a-825">een nieuw venster openen (bijvoorbeeld Help)</span><span class="sxs-lookup"><span data-stu-id="d563a-825">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="d563a-826">mappen wijzigen zonder de opdracht regel te wijzigen</span><span class="sxs-lookup"><span data-stu-id="d563a-826">change directories without changing the command line</span></span>

<span data-ttu-id="d563a-827">De script Block ontvangt twee argumenten:</span><span class="sxs-lookup"><span data-stu-id="d563a-827">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="d563a-828">`$key` -Een **[ConsoleKeyInfo]** -object dat de sleutel is die de aangepaste binding heeft geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="d563a-828">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="d563a-829">Als u dezelfde script Block aan meerdere sleutels koppelt en verschillende acties moet uitvoeren, afhankelijk van de sleutel, kunt u $key controleren.</span><span class="sxs-lookup"><span data-stu-id="d563a-829">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="d563a-830">Veel aangepaste bindingen negeren dit argument.</span><span class="sxs-lookup"><span data-stu-id="d563a-830">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="d563a-831">`$arg` -Een wille keurig argument.</span><span class="sxs-lookup"><span data-stu-id="d563a-831">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="d563a-832">Meestal is dit een geheel getal dat de gebruiker door gegeven van de sleutel bindingen DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="d563a-832">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="d563a-833">Als uw binding geen argumenten accepteert, is het redelijk om dit argument te negeren.</span><span class="sxs-lookup"><span data-stu-id="d563a-833">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="d563a-834">Laten we een voor beeld bekijken waarmee een opdracht regel wordt toegevoegd aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d563a-834">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="d563a-835">Dit is handig wanneer u ervoor hebt gekozen om iets te doen, maar niet opnieuw moet invoeren van de opdracht regel die u al hebt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="d563a-835">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="d563a-836">U kunt veel meer voor beelden bekijken in het bestand `SamplePSReadLineProfile.ps1` dat is geïnstalleerd in de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="d563a-836">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="d563a-837">De meeste sleutel bindingen gebruiken enkele hulp functies voor het bewerken van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-837">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="d563a-838">Deze Api's worden beschreven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="d563a-838">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="d563a-839">Api's voor de ondersteuning van aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="d563a-839">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="d563a-840">De volgende functies zijn openbaar in micro soft. Power shell. PSConsoleReadLine, maar kunnen niet rechtstreeks aan een sleutel worden gebonden.</span><span class="sxs-lookup"><span data-stu-id="d563a-840">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="d563a-841">De meeste zijn handig in aangepaste sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="d563a-841">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="d563a-842">Een opdracht regel toevoegen aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d563a-842">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="d563a-843">Wis de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="d563a-843">Clear the kill-ring.</span></span>  <span data-ttu-id="d563a-844">Dit wordt meestal gebruikt voor het testen.</span><span class="sxs-lookup"><span data-stu-id="d563a-844">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="d563a-845">Verwijder de lengte tekens uit het begin.</span><span class="sxs-lookup"><span data-stu-id="d563a-845">Delete length characters from start.</span></span>  <span data-ttu-id="d563a-846">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d563a-846">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="d563a-847">Voer de actie opname uit op basis van de voor keuren van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d563a-847">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="d563a-848">Deze twee functies halen nuttige informatie op over de huidige status van de invoer buffer.</span><span class="sxs-lookup"><span data-stu-id="d563a-848">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="d563a-849">De eerste wordt vaak gebruikt voor eenvoudige gevallen.</span><span class="sxs-lookup"><span data-stu-id="d563a-849">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="d563a-850">De tweede wordt gebruikt als uw binding iets geavanceerder gaat met de AST.</span><span class="sxs-lookup"><span data-stu-id="d563a-850">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="d563a-851">Deze twee functies worden gebruikt door `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="d563a-851">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="d563a-852">De eerste wordt gebruikt om alle sleutel bindingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="d563a-852">The first is used to get all key bindings.</span></span> <span data-ttu-id="d563a-853">De tweede wordt gebruikt voor het ophalen van specifieke sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="d563a-853">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="d563a-854">Deze functie wordt gebruikt door Get-PSReadLineOption en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="d563a-854">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="d563a-855">Als er niets is geselecteerd op de opdracht regel, wordt-1 geretourneerd in zowel start als length.</span><span class="sxs-lookup"><span data-stu-id="d563a-855">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="d563a-856">Als er een selectie is op de opdracht regel, worden het begin en de lengte van de selectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d563a-856">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="d563a-857">Voeg een teken of teken reeks toe aan de cursor.</span><span class="sxs-lookup"><span data-stu-id="d563a-857">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="d563a-858">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d563a-858">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="d563a-859">Dit is het belangrijkste ingangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="d563a-859">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="d563a-860">Er wordt geen recursie ondersteund, dus is niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="d563a-860">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="d563a-861">Deze functie wordt gebruikt door Remove-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="d563a-861">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="d563a-862">Vervang een deel van de invoer.</span><span class="sxs-lookup"><span data-stu-id="d563a-862">Replace some of the input.</span></span> <span data-ttu-id="d563a-863">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d563a-863">This operation supports undo/redo.</span></span> <span data-ttu-id="d563a-864">U kunt het beste verwijderen gevolgd door INSERT, omdat het wordt beschouwd als één actie voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="d563a-864">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="d563a-865">De cursor verplaatsen naar de opgegeven verschuiving.</span><span class="sxs-lookup"><span data-stu-id="d563a-865">Move the cursor to the given offset.</span></span> <span data-ttu-id="d563a-866">Cursor verplaatsing wordt niet bijgehouden voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="d563a-866">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="d563a-867">Deze functie is een helper-methode die wordt gebruikt door de cmdlet Set-PSReadLineOption, maar kan handig zijn voor een aangepaste sleutel binding die tijdelijk een instelling wil wijzigen.</span><span class="sxs-lookup"><span data-stu-id="d563a-867">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="d563a-868">Deze Help methode wordt gebruikt voor aangepaste bindingen die voldoen aan DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="d563a-868">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="d563a-869">Een typische aanroep ziet eruit als</span><span class="sxs-lookup"><span data-stu-id="d563a-869">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a><span data-ttu-id="d563a-870">Notities</span><span class="sxs-lookup"><span data-stu-id="d563a-870">Notes</span></span>

### <a name="command-history"></a><span data-ttu-id="d563a-871">Opdracht geschiedenis</span><span class="sxs-lookup"><span data-stu-id="d563a-871">Command History</span></span>

<span data-ttu-id="d563a-872">PSReadLine onderhoudt een geschiedenis bestand met alle opdrachten en gegevens die u hebt ingevoerd op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="d563a-872">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="d563a-873">Dit kan gevoelige gegevens bevatten, inclusief wacht woorden.</span><span class="sxs-lookup"><span data-stu-id="d563a-873">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="d563a-874">Als u bijvoorbeeld de cmdlet gebruikt, `ConvertTo-SecureString` wordt het wacht woord in het geschiedenis bestand vastgelegd als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="d563a-874">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="d563a-875">De geschiedenis bestanden zijn een bestand met de naam `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="d563a-875">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="d563a-876">Op Windows-systemen wordt het geschiedenis bestand opgeslagen op `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="d563a-876">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="d563a-877">Op niet-Windows-systemen worden de geschiedenis bestanden opgeslagen in `$env:XDG_DATA_HOME/powershell/PSReadLine` of `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="d563a-877">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="d563a-878">Feedback & bijdragen aan PSReadLine</span><span class="sxs-lookup"><span data-stu-id="d563a-878">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="d563a-879">PSReadLine op GitHub</span><span class="sxs-lookup"><span data-stu-id="d563a-879">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="d563a-880">U kunt een pull-aanvraag verzenden of feedback verzenden op de pagina GitHub.</span><span class="sxs-lookup"><span data-stu-id="d563a-880">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="d563a-881">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d563a-881">See Also</span></span>

<span data-ttu-id="d563a-882">PSReadLine wordt sterk beïnvloed door de GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="d563a-882">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
