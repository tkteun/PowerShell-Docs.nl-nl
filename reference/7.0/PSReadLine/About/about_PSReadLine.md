---
description: PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over PSReadLine
ms.openlocfilehash: f5ae99a7c8bdae82372423a3e4d8261d95ab83d5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692204"
---
# <a name="psreadline"></a><span data-ttu-id="77dac-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="77dac-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="77dac-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="77dac-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="77dac-106">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="77dac-106">Short Description</span></span>

<span data-ttu-id="77dac-107">PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="77dac-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="77dac-108">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="77dac-108">Long Description</span></span>

<span data-ttu-id="77dac-109">PSReadLine 2,0 biedt een krachtige opdracht regel voor het bewerken van de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="77dac-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="77dac-110">De oplossing biedt het volgende:</span><span class="sxs-lookup"><span data-stu-id="77dac-110">It provides:</span></span>

- <span data-ttu-id="77dac-111">Syntaxis kleur van de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="77dac-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="77dac-112">Een visuele indicatie van syntaxis fouten</span><span class="sxs-lookup"><span data-stu-id="77dac-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="77dac-113">Een betere ervaring met meerdere regels (zowel bewerkingen als geschiedenis)</span><span class="sxs-lookup"><span data-stu-id="77dac-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="77dac-114">Aanpas bare sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="77dac-114">Customizable key bindings</span></span>
- <span data-ttu-id="77dac-115">Cmd-en emacs-modi</span><span class="sxs-lookup"><span data-stu-id="77dac-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="77dac-116">Veel configuratie opties</span><span class="sxs-lookup"><span data-stu-id="77dac-116">Many configuration options</span></span>
- <span data-ttu-id="77dac-117">Bash-stijl voltooiing (optioneel in CMD-modus, standaard in Emacs-modus)</span><span class="sxs-lookup"><span data-stu-id="77dac-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="77dac-118">Emacs Yank/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="77dac-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="77dac-119">"Woord" verplaatsing en afsluiten op basis van Power shell-tokens</span><span class="sxs-lookup"><span data-stu-id="77dac-119">PowerShell token based "word" movement and kill</span></span>

> [!NOTE]
> <span data-ttu-id="77dac-120">Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="77dac-120">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="77dac-121">Op dit moment werkt PSReadLine niet goed met scherm lezers.</span><span class="sxs-lookup"><span data-stu-id="77dac-121">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="77dac-122">De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="77dac-122">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="77dac-123">U kunt de module hand matig laden, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="77dac-123">You can manually load the module if necessary.</span></span>

<span data-ttu-id="77dac-124">De volgende functies zijn beschikbaar in de klasse **[micro soft. Power shell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="77dac-124">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="77dac-125">Basis bewerkings functies</span><span class="sxs-lookup"><span data-stu-id="77dac-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="77dac-126">Afbreken</span><span class="sxs-lookup"><span data-stu-id="77dac-126">Abort</span></span>

<span data-ttu-id="77dac-127">De huidige actie afbreken, bijvoorbeeld een incrementele geschiedenis zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="77dac-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="77dac-128">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="77dac-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="77dac-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="77dac-129">AcceptAndGetNext</span></span>

<span data-ttu-id="77dac-130">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="77dac-130">Attempt to execute the current input.</span></span> <span data-ttu-id="77dac-131">Als deze kan worden uitgevoerd (zoals AcceptLine), kunt u het volgende item uit de geschiedenis intrekken de volgende keer dat ReadLine wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="77dac-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="77dac-132">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="77dac-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="77dac-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="77dac-133">AcceptLine</span></span>

<span data-ttu-id="77dac-134">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="77dac-134">Attempt to execute the current input.</span></span> <span data-ttu-id="77dac-135">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="77dac-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="77dac-136">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="77dac-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="77dac-137">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="77dac-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="77dac-138">VI Invoeg modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="77dac-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="77dac-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="77dac-139">AddLine</span></span>

<span data-ttu-id="77dac-140">De vervolg prompt wordt weer gegeven op de volgende regel en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="77dac-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="77dac-141">Dit is handig om invoer in meerdere regels als één opdracht in te voeren, zelfs wanneer één regel volledig wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="77dac-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="77dac-142">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="77dac-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="77dac-143">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="77dac-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="77dac-144">VI Invoeg modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="77dac-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="77dac-145">VI-opdracht modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="77dac-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="77dac-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="77dac-146">BackwardDeleteChar</span></span>

<span data-ttu-id="77dac-147">Verwijder het teken voor de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="77dac-148">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="77dac-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="77dac-149">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="77dac-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="77dac-150">VI Invoeg modus: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="77dac-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="77dac-151">VI-opdracht modus: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="77dac-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="77dac-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="77dac-152">BackwardDeleteLine</span></span>

<span data-ttu-id="77dac-153">Net als BackwardKillLine: verwijdert tekst van het punt naar het begin van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="77dac-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="77dac-154">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="77dac-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="77dac-155">VI Invoeg modus: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="77dac-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="77dac-156">VI-opdracht modus: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="77dac-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="77dac-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="77dac-157">BackwardDeleteWord</span></span>

<span data-ttu-id="77dac-158">Hiermee verwijdert u het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-158">Deletes the previous word.</span></span>

- <span data-ttu-id="77dac-159">VI-opdracht modus: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="77dac-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="77dac-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="77dac-160">BackwardKillLine</span></span>

<span data-ttu-id="77dac-161">De invoer van het begin van de invoer wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="77dac-162">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="77dac-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="77dac-163">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="77dac-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="77dac-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="77dac-164">BackwardKillWord</span></span>

<span data-ttu-id="77dac-165">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="77dac-166">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="77dac-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="77dac-167">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="77dac-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="77dac-168">Cmd `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="77dac-168">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="77dac-169">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="77dac-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="77dac-170">VI Invoeg modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="77dac-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="77dac-171">VI-opdracht modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="77dac-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="77dac-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="77dac-172">CancelLine</span></span>

<span data-ttu-id="77dac-173">De huidige invoer annuleren, waardoor de invoer op het scherm wordt weer gegeven, maar terugkeert naar de host, zodat de prompt opnieuw wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="77dac-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="77dac-174">VI Invoeg modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="77dac-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="77dac-175">VI-opdracht modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="77dac-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="77dac-176">Kopiëren</span><span class="sxs-lookup"><span data-stu-id="77dac-176">Copy</span></span>

<span data-ttu-id="77dac-177">Kopieer de geselecteerde regio naar het klem bord van het systeem.</span><span class="sxs-lookup"><span data-stu-id="77dac-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="77dac-178">Als er geen regio is geselecteerd, kopieert u de hele regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="77dac-179">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="77dac-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="77dac-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="77dac-180">CopyOrCancelLine</span></span>

<span data-ttu-id="77dac-181">Als tekst is geselecteerd, kopieert u deze naar het klem bord. anders annuleert u de regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="77dac-182">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="77dac-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="77dac-183">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="77dac-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="77dac-184">Knippen</span><span class="sxs-lookup"><span data-stu-id="77dac-184">Cut</span></span>

<span data-ttu-id="77dac-185">Geselecteerde regio verwijderen Verwijderde tekst in het systeem Klembord plaatsen.</span><span class="sxs-lookup"><span data-stu-id="77dac-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="77dac-186">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="77dac-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="77dac-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="77dac-187">DeleteChar</span></span>

<span data-ttu-id="77dac-188">Verwijder het teken onder de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="77dac-189">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="77dac-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="77dac-190">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="77dac-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="77dac-191">VI Invoeg modus: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="77dac-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="77dac-192">VI-opdracht modus: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="77dac-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="77dac-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="77dac-193">DeleteCharOrExit</span></span>

<span data-ttu-id="77dac-194">Verwijder het teken onder de cursor of als de regel leeg is, sluit u het proces.</span><span class="sxs-lookup"><span data-stu-id="77dac-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="77dac-195">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="77dac-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="77dac-196">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="77dac-196">DeleteEndOfWord</span></span>

<span data-ttu-id="77dac-197">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-197">Delete to the end of the word.</span></span>

- <span data-ttu-id="77dac-198">VI-opdracht modus: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="77dac-198">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="77dac-199">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="77dac-199">DeleteLine</span></span>

<span data-ttu-id="77dac-200">Hiermee verwijdert u de huidige regel, waarbij u ongedaan maken inschakelt.</span><span class="sxs-lookup"><span data-stu-id="77dac-200">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="77dac-201">VI-opdracht modus: `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="77dac-201">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="77dac-202">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="77dac-202">DeleteLineToFirstChar</span></span>

<span data-ttu-id="77dac-203">Hiermee wordt tekst van de cursor verwijderd naar het eerste niet-lege teken van de regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-203">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="77dac-204">VI-opdracht modus: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="77dac-204">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="77dac-205">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="77dac-205">DeleteToEnd</span></span>

<span data-ttu-id="77dac-206">Verwijderen tot aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-206">Delete to the end of the line.</span></span>

- <span data-ttu-id="77dac-207">VI-opdracht modus: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="77dac-207">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="77dac-208">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="77dac-208">DeleteWord</span></span>

<span data-ttu-id="77dac-209">Verwijder het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-209">Delete the next word.</span></span>

- <span data-ttu-id="77dac-210">VI-opdracht modus: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="77dac-210">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="77dac-211">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="77dac-211">ForwardDeleteLine</span></span>

<span data-ttu-id="77dac-212">Net als ForwardKillLine: verwijdert tekst van het punt naar het einde van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="77dac-212">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="77dac-213">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="77dac-213">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="77dac-214">VI Invoeg modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="77dac-214">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="77dac-215">VI-opdracht modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="77dac-215">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="77dac-216">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="77dac-216">InsertLineAbove</span></span>

<span data-ttu-id="77dac-217">Er wordt een nieuwe lege regel gemaakt op de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="77dac-217">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="77dac-218">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="77dac-219">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="77dac-219">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="77dac-220">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="77dac-220">InsertLineBelow</span></span>

<span data-ttu-id="77dac-221">Er wordt een nieuwe lege regel gemaakt onder de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="77dac-221">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="77dac-222">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-222">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="77dac-223">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="77dac-223">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="77dac-224">InvertCase</span><span class="sxs-lookup"><span data-stu-id="77dac-224">InvertCase</span></span>

<span data-ttu-id="77dac-225">Het hoofdletter gebruik van het huidige teken omkeren en verplaatsen naar het volgende.</span><span class="sxs-lookup"><span data-stu-id="77dac-225">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="77dac-226">VI-opdracht modus: `<~>`</span><span class="sxs-lookup"><span data-stu-id="77dac-226">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="77dac-227">KillLine</span><span class="sxs-lookup"><span data-stu-id="77dac-227">KillLine</span></span>

<span data-ttu-id="77dac-228">De invoer wissen van de cursor tot het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="77dac-228">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="77dac-229">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="77dac-229">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="77dac-230">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="77dac-230">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="77dac-231">KillRegion</span><span class="sxs-lookup"><span data-stu-id="77dac-231">KillRegion</span></span>

<span data-ttu-id="77dac-232">Beëindig de tekst tussen de cursor en de markering.</span><span class="sxs-lookup"><span data-stu-id="77dac-232">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="77dac-233">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-233">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="77dac-234">KillWord</span><span class="sxs-lookup"><span data-stu-id="77dac-234">KillWord</span></span>

<span data-ttu-id="77dac-235">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-235">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="77dac-236">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-236">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="77dac-237">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="77dac-237">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="77dac-238">Cmd `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="77dac-238">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="77dac-239">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="77dac-239">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="77dac-240">VI Invoeg modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="77dac-240">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="77dac-241">VI-opdracht modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="77dac-241">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="77dac-242">Plakken</span><span class="sxs-lookup"><span data-stu-id="77dac-242">Paste</span></span>

<span data-ttu-id="77dac-243">Tekst van het klem bord van het systeem plakken.</span><span class="sxs-lookup"><span data-stu-id="77dac-243">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="77dac-244">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="77dac-244">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="77dac-245">VI Invoeg modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="77dac-245">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="77dac-246">VI-opdracht modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="77dac-246">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="77dac-247">Wanneer u de functie **Paste** gebruikt, wordt de volledige inhoud van de Klembord buffer geplakt in de invoer buffer van PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="77dac-247">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="77dac-248">De invoer buffer wordt vervolgens door gegeven aan de Power shell-parser.</span><span class="sxs-lookup"><span data-stu-id="77dac-248">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="77dac-249">Invoer die met de **rechter muisknop op** de plak methode van de console toepassing wordt geplakt, wordt met één teken per keer naar de invoer buffer gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="77dac-249">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="77dac-250">De invoer buffer wordt door gegeven aan de parser wanneer een teken voor een nieuwe regel wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="77dac-250">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="77dac-251">Daarom wordt de invoer één regel tegelijk geparseerd.</span><span class="sxs-lookup"><span data-stu-id="77dac-251">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="77dac-252">Het verschil tussen plak methoden resulteert in een ander uitvoerings gedrag.</span><span class="sxs-lookup"><span data-stu-id="77dac-252">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="77dac-253">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="77dac-253">PasteAfter</span></span>

<span data-ttu-id="77dac-254">Plak het klem bord na de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="77dac-254">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="77dac-255">VI-opdracht modus: `<p>`</span><span class="sxs-lookup"><span data-stu-id="77dac-255">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="77dac-256">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="77dac-256">PasteBefore</span></span>

<span data-ttu-id="77dac-257">Plak het klem bord vóór de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="77dac-257">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="77dac-258">VI-opdracht modus: `<P>`</span><span class="sxs-lookup"><span data-stu-id="77dac-258">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="77dac-259">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="77dac-259">PrependAndAccept</span></span>

<span data-ttu-id="77dac-260">Laten voorafgaan door een ' # ' en accepteer de regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-260">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="77dac-261">VI-opdracht modus: `<#>`</span><span class="sxs-lookup"><span data-stu-id="77dac-261">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="77dac-262">Opnieuw uitvoeren</span><span class="sxs-lookup"><span data-stu-id="77dac-262">Redo</span></span>

<span data-ttu-id="77dac-263">Undo ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="77dac-263">Undo an undo.</span></span>

- <span data-ttu-id="77dac-264">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="77dac-264">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="77dac-265">VI Invoeg modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="77dac-265">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="77dac-266">VI-opdracht modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="77dac-266">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="77dac-267">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="77dac-267">RepeatLastCommand</span></span>

<span data-ttu-id="77dac-268">Herhaal de laatste tekst wijziging.</span><span class="sxs-lookup"><span data-stu-id="77dac-268">Repeat the last text modification.</span></span>

- <span data-ttu-id="77dac-269">VI-opdracht modus: `<.>`</span><span class="sxs-lookup"><span data-stu-id="77dac-269">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="77dac-270">RevertLine</span><span class="sxs-lookup"><span data-stu-id="77dac-270">RevertLine</span></span>

<span data-ttu-id="77dac-271">Hiermee wordt alle invoer teruggezet naar de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="77dac-271">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="77dac-272">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="77dac-272">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="77dac-273">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="77dac-273">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="77dac-274">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="77dac-274">ShellBackwardKillWord</span></span>

<span data-ttu-id="77dac-275">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-275">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="77dac-276">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="77dac-276">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="77dac-277">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="77dac-277">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="77dac-278">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-278">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="77dac-279">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="77dac-279">ShellKillWord</span></span>

<span data-ttu-id="77dac-280">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-280">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="77dac-281">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-281">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="77dac-282">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="77dac-282">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="77dac-283">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-283">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="77dac-284">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="77dac-284">SwapCharacters</span></span>

<span data-ttu-id="77dac-285">Het huidige teken en de eerste vervangen door wisselen.</span><span class="sxs-lookup"><span data-stu-id="77dac-285">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="77dac-286">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="77dac-286">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="77dac-287">VI Invoeg modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="77dac-287">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="77dac-288">VI-opdracht modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="77dac-288">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="77dac-289">Ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="77dac-289">Undo</span></span>

<span data-ttu-id="77dac-290">Een vorige bewerking ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="77dac-290">Undo a previous edit.</span></span>

- <span data-ttu-id="77dac-291">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="77dac-291">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="77dac-292">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="77dac-292">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="77dac-293">VI Invoeg modus: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="77dac-293">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="77dac-294">VI-opdracht modus: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="77dac-294">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="77dac-295">UndoAll</span><span class="sxs-lookup"><span data-stu-id="77dac-295">UndoAll</span></span>

<span data-ttu-id="77dac-296">Alle vorige bewerkingen voor de regel ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="77dac-296">Undo all previous edits for line.</span></span>

- <span data-ttu-id="77dac-297">VI-opdracht modus: `<U>`</span><span class="sxs-lookup"><span data-stu-id="77dac-297">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="77dac-298">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="77dac-298">UnixWordRubout</span></span>

<span data-ttu-id="77dac-299">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-299">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="77dac-300">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="77dac-300">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="77dac-301">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="77dac-301">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="77dac-302">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="77dac-302">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="77dac-303">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="77dac-303">ValidateAndAcceptLine</span></span>

<span data-ttu-id="77dac-304">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="77dac-304">Attempt to execute the current input.</span></span> <span data-ttu-id="77dac-305">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="77dac-305">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="77dac-306">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="77dac-306">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="77dac-307">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="77dac-307">ViAcceptLine</span></span>

<span data-ttu-id="77dac-308">Accepteer de regel en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="77dac-308">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="77dac-309">VI-opdracht modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="77dac-309">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="77dac-310">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="77dac-310">ViAcceptLineOrExit</span></span>

<span data-ttu-id="77dac-311">Als DeleteCharOrExit in de Emacs-modus, maar wel in plaats van een teken te verwijderen, accepteert u de regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-311">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="77dac-312">VI Invoeg modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="77dac-312">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="77dac-313">VI-opdracht modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="77dac-313">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="77dac-314">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="77dac-314">ViAppendLine</span></span>

<span data-ttu-id="77dac-315">Er wordt een nieuwe regel ingevoegd onder de huidige regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-315">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="77dac-316">VI-opdracht modus: `<o>`</span><span class="sxs-lookup"><span data-stu-id="77dac-316">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="77dac-317">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="77dac-317">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="77dac-318">Hiermee verwijdert u het vorige woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-318">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="77dac-319">VI-opdracht modus: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="77dac-319">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="77dac-320">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="77dac-320">ViBackwardGlob</span></span>

<span data-ttu-id="77dac-321">Verplaatst de cursor terug naar het begin van het vorige woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="77dac-321">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="77dac-322">VI-opdracht modus: `<B>`</span><span class="sxs-lookup"><span data-stu-id="77dac-322">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="77dac-323">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="77dac-323">ViDeleteBrace</span></span>

<span data-ttu-id="77dac-324">Zoek de accolade, het haakje sluiten of de vier Kante haken en verwijder alle inhoud binnen, inclusief de accolade.</span><span class="sxs-lookup"><span data-stu-id="77dac-324">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="77dac-325">VI-opdracht modus: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="77dac-325">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="77dac-326">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="77dac-326">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="77dac-327">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-327">Delete to the end of the word.</span></span>

- <span data-ttu-id="77dac-328">VI-opdracht modus: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="77dac-328">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="77dac-329">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="77dac-329">ViDeleteGlob</span></span>

<span data-ttu-id="77dac-330">De volgende Globs verwijderen (door witruimte gescheiden woord).</span><span class="sxs-lookup"><span data-stu-id="77dac-330">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="77dac-331">VI-opdracht modus: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="77dac-331">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="77dac-332">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="77dac-332">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="77dac-333">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-333">Deletes until given character.</span></span>

- <span data-ttu-id="77dac-334">VI-opdracht modus: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="77dac-334">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="77dac-335">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="77dac-335">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="77dac-336">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-336">Deletes until given character.</span></span>

- <span data-ttu-id="77dac-337">VI-opdracht modus: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="77dac-337">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="77dac-338">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="77dac-338">ViDeleteToChar</span></span>

<span data-ttu-id="77dac-339">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-339">Deletes until given character.</span></span>

- <span data-ttu-id="77dac-340">VI-opdracht modus: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="77dac-340">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="77dac-341">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="77dac-341">ViDeleteToCharBackward</span></span>

<span data-ttu-id="77dac-342">Hiermee verwijdert u achterwaartse tekens tot aan het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-342">Deletes backwards until given character.</span></span>

- <span data-ttu-id="77dac-343">VI-opdracht modus: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="77dac-343">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="77dac-344">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="77dac-344">ViInsertAtBegining</span></span>

<span data-ttu-id="77dac-345">Schakel over naar de Invoeg modus en plaats de cursor aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-345">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="77dac-346">VI-opdracht modus: `<I>`</span><span class="sxs-lookup"><span data-stu-id="77dac-346">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="77dac-347">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="77dac-347">ViInsertAtEnd</span></span>

<span data-ttu-id="77dac-348">Schakel over naar de Invoeg modus en plaats de cursor aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-348">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="77dac-349">VI-opdracht modus: `<A>`</span><span class="sxs-lookup"><span data-stu-id="77dac-349">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="77dac-350">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="77dac-350">ViInsertLine</span></span>

<span data-ttu-id="77dac-351">Boven de huidige regel wordt een nieuwe regel ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="77dac-351">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="77dac-352">VI-opdracht modus: `<O>`</span><span class="sxs-lookup"><span data-stu-id="77dac-352">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="77dac-353">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="77dac-353">ViInsertWithAppend</span></span>

<span data-ttu-id="77dac-354">Toevoegen vanaf de huidige regel positie.</span><span class="sxs-lookup"><span data-stu-id="77dac-354">Append from the current line position.</span></span>

- <span data-ttu-id="77dac-355">VI-opdracht modus: `<a>`</span><span class="sxs-lookup"><span data-stu-id="77dac-355">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="77dac-356">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="77dac-356">ViInsertWithDelete</span></span>

<span data-ttu-id="77dac-357">Verwijder het huidige teken en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="77dac-357">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="77dac-358">VI-opdracht modus: `<s>`</span><span class="sxs-lookup"><span data-stu-id="77dac-358">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="77dac-359">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="77dac-359">ViJoinLines</span></span>

<span data-ttu-id="77dac-360">De huidige regel en de volgende regel worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="77dac-360">Joins the current line and the next line.</span></span>

- <span data-ttu-id="77dac-361">VI-opdracht modus: `<J>`</span><span class="sxs-lookup"><span data-stu-id="77dac-361">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="77dac-362">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="77dac-362">ViReplaceLine</span></span>

<span data-ttu-id="77dac-363">De volledige opdracht regel wissen.</span><span class="sxs-lookup"><span data-stu-id="77dac-363">Erase the entire command line.</span></span>

- <span data-ttu-id="77dac-364">VI-opdracht modus: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="77dac-364">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="77dac-365">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="77dac-365">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="77dac-366">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-366">Replaces until given character.</span></span>

- <span data-ttu-id="77dac-367">VI-opdracht modus: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="77dac-367">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="77dac-368">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="77dac-368">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="77dac-369">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-369">Replaces until given character.</span></span>

- <span data-ttu-id="77dac-370">VI-opdracht modus: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="77dac-370">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="77dac-371">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="77dac-371">ViReplaceToChar</span></span>

<span data-ttu-id="77dac-372">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-372">Deletes until given character.</span></span>

- <span data-ttu-id="77dac-373">VI-opdracht modus: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="77dac-373">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="77dac-374">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="77dac-374">ViReplaceToCharBackward</span></span>

<span data-ttu-id="77dac-375">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-375">Replaces until given character.</span></span>

- <span data-ttu-id="77dac-376">VI-opdracht modus: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="77dac-376">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="77dac-377">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="77dac-377">ViYankBeginningOfLine</span></span>

<span data-ttu-id="77dac-378">Yank vanaf het begin van de buffer naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-378">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="77dac-379">VI-opdracht modus: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="77dac-379">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="77dac-380">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="77dac-380">ViYankEndOfGlob</span></span>

<span data-ttu-id="77dac-381">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="77dac-381">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="77dac-382">VI-opdracht modus: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="77dac-382">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="77dac-383">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="77dac-383">ViYankEndOfWord</span></span>

<span data-ttu-id="77dac-384">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="77dac-384">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="77dac-385">VI-opdracht modus: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="77dac-385">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="77dac-386">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="77dac-386">ViYankLeft</span></span>

<span data-ttu-id="77dac-387">Yank teken (s) links van de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-387">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="77dac-388">VI-opdracht modus: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="77dac-388">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="77dac-389">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="77dac-389">ViYankLine</span></span>

<span data-ttu-id="77dac-390">Yank de volledige buffer.</span><span class="sxs-lookup"><span data-stu-id="77dac-390">Yank the entire buffer.</span></span>

- <span data-ttu-id="77dac-391">VI-opdracht modus: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="77dac-391">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="77dac-392">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="77dac-392">ViYankNextGlob</span></span>

<span data-ttu-id="77dac-393">Yank van de cursor naar het begin van de volgende woord (en).</span><span class="sxs-lookup"><span data-stu-id="77dac-393">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="77dac-394">VI-opdracht modus: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="77dac-394">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="77dac-395">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="77dac-395">ViYankNextWord</span></span>

<span data-ttu-id="77dac-396">Yank het woord (en) na de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-396">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="77dac-397">VI-opdracht modus: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="77dac-397">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="77dac-398">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="77dac-398">ViYankPercent</span></span>

<span data-ttu-id="77dac-399">Yank naar/van overeenkomende accolade.</span><span class="sxs-lookup"><span data-stu-id="77dac-399">Yank to/from matching brace.</span></span>

- <span data-ttu-id="77dac-400">VI-opdracht modus: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="77dac-400">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="77dac-401">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="77dac-401">ViYankPreviousGlob</span></span>

<span data-ttu-id="77dac-402">Yank vanaf het begin van het (de) woord (en) tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-402">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="77dac-403">VI-opdracht modus: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="77dac-403">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="77dac-404">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="77dac-404">ViYankPreviousWord</span></span>

<span data-ttu-id="77dac-405">Yank de woorden vóór de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-405">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="77dac-406">VI-opdracht modus: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="77dac-406">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="77dac-407">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="77dac-407">ViYankRight</span></span>

<span data-ttu-id="77dac-408">Yank teken (s) onder en rechts van de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-408">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="77dac-409">VI-opdracht modus: `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="77dac-409">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="77dac-410">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="77dac-410">ViYankToEndOfLine</span></span>

<span data-ttu-id="77dac-411">Yank van de cursor tot het einde van de buffer.</span><span class="sxs-lookup"><span data-stu-id="77dac-411">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="77dac-412">VI-opdracht modus: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="77dac-412">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="77dac-413">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="77dac-413">ViYankToFirstChar</span></span>

<span data-ttu-id="77dac-414">Yank van het eerste niet-spatie teken tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-414">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="77dac-415">VI-opdracht modus: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="77dac-415">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="77dac-416">Yank</span><span class="sxs-lookup"><span data-stu-id="77dac-416">Yank</span></span>

<span data-ttu-id="77dac-417">Voeg de meest recent afgebroken tekst toe aan de invoer.</span><span class="sxs-lookup"><span data-stu-id="77dac-417">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="77dac-418">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="77dac-418">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="77dac-419">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="77dac-419">YankLastArg</span></span>

<span data-ttu-id="77dac-420">Yank het laatste argument van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-420">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="77dac-421">Met een argument, de eerste keer dat deze wordt aangeroepen, gedraagt zich op dezelfde manier als YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="77dac-421">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="77dac-422">Als meerdere keren worden aangeroepen, wordt door de geschiedenis en ARG de richting ingesteld (negatief de richting omkeren.)</span><span class="sxs-lookup"><span data-stu-id="77dac-422">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="77dac-423">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="77dac-423">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="77dac-424">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="77dac-424">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="77dac-425">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="77dac-425">YankNthArg</span></span>

<span data-ttu-id="77dac-426">Yank het eerste argument (na de opdracht) van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-426">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="77dac-427">Met een argument, Yank het ne argument (vanaf 0), als het argument negatief is, begint vanaf het laatste argument.</span><span class="sxs-lookup"><span data-stu-id="77dac-427">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="77dac-428">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="77dac-428">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="77dac-429">YankPop</span><span class="sxs-lookup"><span data-stu-id="77dac-429">YankPop</span></span>

<span data-ttu-id="77dac-430">Als de vorige bewerking Yank of YankPop is, vervangt u de eerder yanked tekst door de volgende afgebroken tekst van de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="77dac-430">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="77dac-431">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="77dac-431">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="77dac-432">Functies voor cursor verplaatsing</span><span class="sxs-lookup"><span data-stu-id="77dac-432">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="77dac-433">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="77dac-433">BackwardChar</span></span>

<span data-ttu-id="77dac-434">De cursor één teken naar links verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="77dac-434">Move the cursor one character to the left.</span></span> <span data-ttu-id="77dac-435">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="77dac-435">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="77dac-436">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-436">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="77dac-437">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="77dac-437">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="77dac-438">VI Invoeg modus: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-438">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="77dac-439">VI-opdracht modus: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="77dac-439">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="77dac-440">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="77dac-440">BackwardWord</span></span>

<span data-ttu-id="77dac-441">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-441">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="77dac-442">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="77dac-442">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="77dac-443">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-443">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="77dac-444">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="77dac-444">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="77dac-445">VI Invoeg modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-445">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="77dac-446">VI-opdracht modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-446">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="77dac-447">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="77dac-447">BeginningOfLine</span></span>

<span data-ttu-id="77dac-448">Als de invoer meerdere regels heeft, gaat u naar het begin van de huidige regel of gaat u naar het begin van de invoer als deze al aan het begin van de regel staat.</span><span class="sxs-lookup"><span data-stu-id="77dac-448">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="77dac-449">Als de invoer één regel heeft, gaat u naar het begin van de invoer.</span><span class="sxs-lookup"><span data-stu-id="77dac-449">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="77dac-450">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="77dac-450">Cmd: `<Home>`</span></span>
- <span data-ttu-id="77dac-451">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="77dac-451">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="77dac-452">VI Invoeg modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="77dac-452">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="77dac-453">VI-opdracht modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="77dac-453">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="77dac-454">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="77dac-454">EndOfLine</span></span>

<span data-ttu-id="77dac-455">Als de invoer meerdere regels heeft, gaat u naar het einde van de huidige regel of gaat u naar het einde van de invoer als u aan het einde van de regel bent.</span><span class="sxs-lookup"><span data-stu-id="77dac-455">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="77dac-456">Als de invoer één regel heeft, gaat u naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="77dac-456">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="77dac-457">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="77dac-457">Cmd: `<End>`</span></span>
- <span data-ttu-id="77dac-458">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="77dac-458">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="77dac-459">VI Invoeg modus: `<End>`</span><span class="sxs-lookup"><span data-stu-id="77dac-459">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="77dac-460">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="77dac-460">ForwardChar</span></span>

<span data-ttu-id="77dac-461">De cursor één teken naar rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="77dac-461">Move the cursor one character to the right.</span></span> <span data-ttu-id="77dac-462">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="77dac-462">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="77dac-463">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-463">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="77dac-464">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="77dac-464">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="77dac-465">VI Invoeg modus: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-465">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="77dac-466">VI-opdracht modus: `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="77dac-466">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="77dac-467">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="77dac-467">ForwardWord</span></span>

<span data-ttu-id="77dac-468">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-468">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="77dac-469">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="77dac-469">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="77dac-470">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="77dac-470">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="77dac-471">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="77dac-471">GotoBrace</span></span>

<span data-ttu-id="77dac-472">Ga naar de accolade, haakjes of vier Kante haakjes.</span><span class="sxs-lookup"><span data-stu-id="77dac-472">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="77dac-473">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="77dac-473">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="77dac-474">VI Invoeg modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="77dac-474">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="77dac-475">VI-opdracht modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="77dac-475">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="77dac-476">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="77dac-476">GotoColumn</span></span>

<span data-ttu-id="77dac-477">Ga naar de kolom die wordt aangegeven door arg.</span><span class="sxs-lookup"><span data-stu-id="77dac-477">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="77dac-478">VI-opdracht modus: `<|>`</span><span class="sxs-lookup"><span data-stu-id="77dac-478">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="77dac-479">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="77dac-479">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="77dac-480">De cursor verplaatsen naar het eerste niet-lege teken in de regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-480">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="77dac-481">VI-opdracht modus: `<^>`</span><span class="sxs-lookup"><span data-stu-id="77dac-481">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="77dac-482">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="77dac-482">MoveToEndOfLine</span></span>

<span data-ttu-id="77dac-483">De cursor verplaatsen naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="77dac-483">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="77dac-484">VI-opdracht modus: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="77dac-484">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="77dac-485">NextLine</span><span class="sxs-lookup"><span data-stu-id="77dac-485">NextLine</span></span>

<span data-ttu-id="77dac-486">De cursor verplaatsen naar de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-486">Move the cursor to the next line.</span></span>

- <span data-ttu-id="77dac-487">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-487">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="77dac-488">NextWord</span><span class="sxs-lookup"><span data-stu-id="77dac-488">NextWord</span></span>

<span data-ttu-id="77dac-489">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-489">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="77dac-490">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="77dac-490">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="77dac-491">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-491">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="77dac-492">VI Invoeg modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-492">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="77dac-493">VI-opdracht modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-493">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="77dac-494">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="77dac-494">NextWordEnd</span></span>

<span data-ttu-id="77dac-495">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="77dac-496">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="77dac-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="77dac-497">VI-opdracht modus: `<e>`</span><span class="sxs-lookup"><span data-stu-id="77dac-497">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="77dac-498">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="77dac-498">PreviousLine</span></span>

<span data-ttu-id="77dac-499">Verplaats de cursor naar de vorige regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-499">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="77dac-500">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-500">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="77dac-501">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="77dac-501">ShellBackwardWord</span></span>

<span data-ttu-id="77dac-502">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-502">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="77dac-503">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="77dac-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="77dac-504">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-504">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="77dac-505">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="77dac-505">ShellForwardWord</span></span>

<span data-ttu-id="77dac-506">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-506">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="77dac-507">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="77dac-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="77dac-508">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-508">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="77dac-509">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="77dac-509">ShellNextWord</span></span>

<span data-ttu-id="77dac-510">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-510">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="77dac-511">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="77dac-511">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="77dac-512">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-512">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="77dac-513">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="77dac-513">ViBackwardWord</span></span>

<span data-ttu-id="77dac-514">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="77dac-515">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="77dac-515">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="77dac-516">VI-opdracht modus: `<b>`</span><span class="sxs-lookup"><span data-stu-id="77dac-516">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="77dac-517">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="77dac-517">ViEndOfGlob</span></span>

<span data-ttu-id="77dac-518">Verplaatst de cursor naar het einde van het woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="77dac-518">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="77dac-519">VI-opdracht modus: `<E>`</span><span class="sxs-lookup"><span data-stu-id="77dac-519">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="77dac-520">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="77dac-520">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="77dac-521">Wordt verplaatst naar het einde van het vorige woord, waarbij alleen witruimte wordt gebruikt als woord als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-521">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="77dac-522">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-522">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="77dac-523">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="77dac-523">ViGotoBrace</span></span>

<span data-ttu-id="77dac-524">Vergelijkbaar met GotoBrace, maar is in plaats van op tokens gebaseerd.</span><span class="sxs-lookup"><span data-stu-id="77dac-524">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="77dac-525">VI-opdracht modus: `<%>`</span><span class="sxs-lookup"><span data-stu-id="77dac-525">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="77dac-526">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="77dac-526">ViNextGlob</span></span>

<span data-ttu-id="77dac-527">Verplaatst naar het volgende woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-527">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="77dac-528">VI-opdracht modus: `<W>`</span><span class="sxs-lookup"><span data-stu-id="77dac-528">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="77dac-529">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="77dac-529">ViNextWord</span></span>

<span data-ttu-id="77dac-530">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="77dac-530">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="77dac-531">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="77dac-531">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="77dac-532">VI-opdracht modus: `<w>`</span><span class="sxs-lookup"><span data-stu-id="77dac-532">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="77dac-533">Geschiedenis functies</span><span class="sxs-lookup"><span data-stu-id="77dac-533">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="77dac-534">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="77dac-534">BeginningOfHistory</span></span>

<span data-ttu-id="77dac-535">Hiermee gaat u naar het eerste item in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="77dac-535">Move to the first item in the history.</span></span>

- <span data-ttu-id="77dac-536">Emacs: `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="77dac-536">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="77dac-537">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="77dac-537">ClearHistory</span></span>

<span data-ttu-id="77dac-538">Hiermee wist u de geschiedenis in PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="77dac-538">Clears history in PSReadLine.</span></span> <span data-ttu-id="77dac-539">Dit heeft geen invloed op de Power shell-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="77dac-539">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="77dac-540">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="77dac-540">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="77dac-541">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="77dac-541">EndOfHistory</span></span>

<span data-ttu-id="77dac-542">Hiermee gaat u naar het laatste item (de huidige invoer) in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="77dac-542">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="77dac-543">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="77dac-543">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="77dac-544">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="77dac-544">ForwardSearchHistory</span></span>

<span data-ttu-id="77dac-545">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="77dac-545">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="77dac-546">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="77dac-546">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="77dac-547">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="77dac-547">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="77dac-548">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="77dac-548">HistorySearchBackward</span></span>

<span data-ttu-id="77dac-549">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-549">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="77dac-550">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="77dac-550">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="77dac-551">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="77dac-551">HistorySearchForward</span></span>

<span data-ttu-id="77dac-552">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-552">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="77dac-553">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="77dac-553">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="77dac-554">NextHistory</span><span class="sxs-lookup"><span data-stu-id="77dac-554">NextHistory</span></span>

<span data-ttu-id="77dac-555">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="77dac-555">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="77dac-556">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-556">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="77dac-557">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="77dac-557">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="77dac-558">VI Invoeg modus: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-558">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="77dac-559">VI-opdracht modus: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="77dac-559">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="77dac-560">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="77dac-560">PreviousHistory</span></span>

<span data-ttu-id="77dac-561">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="77dac-561">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="77dac-562">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-562">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="77dac-563">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="77dac-563">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="77dac-564">VI Invoeg modus: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-564">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="77dac-565">VI-opdracht modus: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="77dac-565">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="77dac-566">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="77dac-566">ReverseSearchHistory</span></span>

<span data-ttu-id="77dac-567">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="77dac-567">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="77dac-568">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="77dac-568">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="77dac-569">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="77dac-569">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="77dac-570">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="77dac-570">ViSearchHistoryBackward</span></span>

<span data-ttu-id="77dac-571">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="77dac-571">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="77dac-572">VI Invoeg modus: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="77dac-572">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="77dac-573">VI-opdracht modus: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="77dac-573">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="77dac-574">Voltooiings functies</span><span class="sxs-lookup"><span data-stu-id="77dac-574">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="77dac-575">Voltooid</span><span class="sxs-lookup"><span data-stu-id="77dac-575">Complete</span></span>

<span data-ttu-id="77dac-576">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-576">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="77dac-577">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="77dac-577">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="77dac-578">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="77dac-578">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="77dac-579">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="77dac-579">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="77dac-580">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="77dac-580">MenuComplete</span></span>

<span data-ttu-id="77dac-581">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-581">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="77dac-582">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="77dac-582">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="77dac-583">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="77dac-583">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="77dac-584">Cmd `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="77dac-584">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="77dac-585">Emacs: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="77dac-585">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="77dac-586">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="77dac-586">PossibleCompletions</span></span>

<span data-ttu-id="77dac-587">De lijst met mogelijke aanvullingen weer geven.</span><span class="sxs-lookup"><span data-stu-id="77dac-587">Display the list of possible completions.</span></span>

- <span data-ttu-id="77dac-588">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="77dac-588">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="77dac-589">VI Invoeg modus: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="77dac-589">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="77dac-590">VI-opdracht modus: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="77dac-590">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="77dac-591">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="77dac-591">TabCompleteNext</span></span>

<span data-ttu-id="77dac-592">Poging om de tekst rond de cursor te volt ooien met de volgende beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="77dac-592">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="77dac-593">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="77dac-593">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="77dac-594">VI-opdracht modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="77dac-594">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="77dac-595">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="77dac-595">TabCompletePrevious</span></span>

<span data-ttu-id="77dac-596">Poging om de tekst rond de cursor te volt ooien met de vorige beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="77dac-596">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="77dac-597">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="77dac-597">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="77dac-598">VI-opdracht modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="77dac-598">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="77dac-599">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="77dac-599">ViTabCompleteNext</span></span>

<span data-ttu-id="77dac-600">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompleteNext aan.</span><span class="sxs-lookup"><span data-stu-id="77dac-600">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="77dac-601">VI Invoeg modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="77dac-601">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="77dac-602">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="77dac-602">ViTabCompletePrevious</span></span>

<span data-ttu-id="77dac-603">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompletePrevious aan.</span><span class="sxs-lookup"><span data-stu-id="77dac-603">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="77dac-604">VI Invoeg modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="77dac-604">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="77dac-605">Diverse functies</span><span class="sxs-lookup"><span data-stu-id="77dac-605">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="77dac-606">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="77dac-606">CaptureScreen</span></span>

<span data-ttu-id="77dac-607">Interactieve scherm opname starten-pijl-omhoog/omlaag Selecteer regels en voer de geselecteerde tekst als tekst en HTML naar het klem bord kopiëren.</span><span class="sxs-lookup"><span data-stu-id="77dac-607">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="77dac-608">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-608">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="77dac-609">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="77dac-609">ClearScreen</span></span>

<span data-ttu-id="77dac-610">Schakel het scherm uit en teken de huidige regel boven aan het scherm.</span><span class="sxs-lookup"><span data-stu-id="77dac-610">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="77dac-611">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="77dac-611">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="77dac-612">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="77dac-612">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="77dac-613">VI Invoeg modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="77dac-613">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="77dac-614">VI-opdracht modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="77dac-614">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="77dac-615">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="77dac-615">DigitArgument</span></span>

<span data-ttu-id="77dac-616">Start een nieuw cijfer argument om door te geven aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="77dac-616">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="77dac-617">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="77dac-617">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="77dac-618">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="77dac-618">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="77dac-619">VI-opdracht modus: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="77dac-619">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="77dac-620">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="77dac-620">InvokePrompt</span></span>

<span data-ttu-id="77dac-621">Hiermee wordt de huidige prompt gewist en wordt de functie Prompt aangeroepen om de prompt opnieuw weer te geven.</span><span class="sxs-lookup"><span data-stu-id="77dac-621">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="77dac-622">Dit is handig voor aangepaste sleutel afhandelingen die de status wijzigen, bijvoorbeeld de huidige map wijzigen.</span><span class="sxs-lookup"><span data-stu-id="77dac-622">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="77dac-623">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-623">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="77dac-624">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="77dac-624">ScrollDisplayDown</span></span>

<span data-ttu-id="77dac-625">De weer gave één scherm omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="77dac-625">Scroll the display down one screen.</span></span>

- <span data-ttu-id="77dac-626">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="77dac-626">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="77dac-627">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="77dac-627">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="77dac-628">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="77dac-628">ScrollDisplayDownLine</span></span>

<span data-ttu-id="77dac-629">De weer gave één regel omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="77dac-629">Scroll the display down one line.</span></span>

- <span data-ttu-id="77dac-630">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="77dac-630">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="77dac-631">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="77dac-631">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="77dac-632">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="77dac-632">ScrollDisplayToCursor</span></span>

<span data-ttu-id="77dac-633">Schuif de weer gave naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-633">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="77dac-634">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="77dac-634">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="77dac-635">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="77dac-635">ScrollDisplayTop</span></span>

<span data-ttu-id="77dac-636">Schuif de weer gave naar boven.</span><span class="sxs-lookup"><span data-stu-id="77dac-636">Scroll the display to the top.</span></span>

- <span data-ttu-id="77dac-637">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="77dac-637">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="77dac-638">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="77dac-638">ScrollDisplayUp</span></span>

<span data-ttu-id="77dac-639">Schuif de weer gave één scherm omhoog.</span><span class="sxs-lookup"><span data-stu-id="77dac-639">Scroll the display up one screen.</span></span>

- <span data-ttu-id="77dac-640">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="77dac-640">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="77dac-641">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="77dac-641">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="77dac-642">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="77dac-642">ScrollDisplayUpLine</span></span>

<span data-ttu-id="77dac-643">De weer gave één regel omhoog schuiven.</span><span class="sxs-lookup"><span data-stu-id="77dac-643">Scroll the display up one line.</span></span>

- <span data-ttu-id="77dac-644">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="77dac-644">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="77dac-645">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="77dac-645">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="77dac-646">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="77dac-646">SelfInsert</span></span>

<span data-ttu-id="77dac-647">Voeg de sleutel in.</span><span class="sxs-lookup"><span data-stu-id="77dac-647">Insert the key.</span></span>

- <span data-ttu-id="77dac-648">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-648">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="77dac-649">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="77dac-649">ShowKeyBindings</span></span>

<span data-ttu-id="77dac-650">Alle gebonden sleutels weer geven.</span><span class="sxs-lookup"><span data-stu-id="77dac-650">Show all bound keys.</span></span>

- <span data-ttu-id="77dac-651">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="77dac-651">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="77dac-652">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="77dac-652">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="77dac-653">VI Invoeg modus: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="77dac-653">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="77dac-654">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="77dac-654">ViCommandMode</span></span>

<span data-ttu-id="77dac-655">Schakel de huidige bedrijfs modus uit van Vi-Insert naar de VI-opdracht.</span><span class="sxs-lookup"><span data-stu-id="77dac-655">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="77dac-656">VI Invoeg modus: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="77dac-656">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="77dac-657">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="77dac-657">ViDigitArgumentInChord</span></span>

<span data-ttu-id="77dac-658">Start een nieuw cijfer argument om door te geven aan andere functies in een van de koorden van VI.</span><span class="sxs-lookup"><span data-stu-id="77dac-658">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="77dac-659">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-659">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="77dac-660">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="77dac-660">ViEditVisually</span></span>

<span data-ttu-id="77dac-661">Bewerk de opdracht regel in een tekst editor die is opgegeven door $env: EDITOR of $env: VISUAL.</span><span class="sxs-lookup"><span data-stu-id="77dac-661">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="77dac-662">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="77dac-662">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="77dac-663">VI-opdracht modus: `<v>`</span><span class="sxs-lookup"><span data-stu-id="77dac-663">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="77dac-664">ViExit</span><span class="sxs-lookup"><span data-stu-id="77dac-664">ViExit</span></span>

<span data-ttu-id="77dac-665">Hiermee wordt de shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="77dac-665">Exits the shell.</span></span>

- <span data-ttu-id="77dac-666">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-666">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="77dac-667">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="77dac-667">ViInsertMode</span></span>

<span data-ttu-id="77dac-668">Schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="77dac-668">Switch to Insert mode.</span></span>

- <span data-ttu-id="77dac-669">VI-opdracht modus: `<i>`</span><span class="sxs-lookup"><span data-stu-id="77dac-669">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="77dac-670">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="77dac-670">WhatIsKey</span></span>

<span data-ttu-id="77dac-671">Lees een sleutel en vertel me wat de sleutel is gebonden.</span><span class="sxs-lookup"><span data-stu-id="77dac-671">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="77dac-672">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="77dac-672">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="77dac-673">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="77dac-673">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="77dac-674">Selectie functies</span><span class="sxs-lookup"><span data-stu-id="77dac-674">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="77dac-675">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="77dac-675">ExchangePointAndMark</span></span>

<span data-ttu-id="77dac-676">De cursor wordt op de locatie van het merk geplaatst en het vinkje wordt verplaatst naar de locatie van de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-676">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="77dac-677">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="77dac-677">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="77dac-678">SelectAll aanroepen</span><span class="sxs-lookup"><span data-stu-id="77dac-678">SelectAll</span></span>

<span data-ttu-id="77dac-679">Selecteer de volledige regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-679">Select the entire line.</span></span>

- <span data-ttu-id="77dac-680">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="77dac-680">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="77dac-681">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="77dac-681">SelectBackwardChar</span></span>

<span data-ttu-id="77dac-682">Pas de huidige selectie aan om het vorige teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="77dac-682">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="77dac-683">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-683">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="77dac-684">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-684">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="77dac-685">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="77dac-685">SelectBackwardsLine</span></span>

<span data-ttu-id="77dac-686">Pas de huidige selectie aan de cursor toe aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-686">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="77dac-687">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="77dac-687">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="77dac-688">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="77dac-688">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="77dac-689">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="77dac-689">SelectBackwardWord</span></span>

<span data-ttu-id="77dac-690">Pas de huidige selectie aan om het vorige woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="77dac-690">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="77dac-691">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-691">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="77dac-692">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="77dac-692">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="77dac-693">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="77dac-693">SelectForwardChar</span></span>

<span data-ttu-id="77dac-694">Pas de huidige selectie aan om het volgende teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="77dac-694">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="77dac-695">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-695">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="77dac-696">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-696">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="77dac-697">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="77dac-697">SelectForwardWord</span></span>

<span data-ttu-id="77dac-698">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="77dac-698">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="77dac-699">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="77dac-699">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="77dac-700">SelectLine</span><span class="sxs-lookup"><span data-stu-id="77dac-700">SelectLine</span></span>

<span data-ttu-id="77dac-701">Pas de huidige selectie aan de cursor toe aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-701">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="77dac-702">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="77dac-702">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="77dac-703">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="77dac-703">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="77dac-704">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="77dac-704">SelectNextWord</span></span>

<span data-ttu-id="77dac-705">Pas de huidige selectie aan om het volgende woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="77dac-705">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="77dac-706">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="77dac-706">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="77dac-707">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="77dac-707">SelectShellBackwardWord</span></span>

<span data-ttu-id="77dac-708">Pas de huidige selectie aan om het vorige woord op te maken met behulp van ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="77dac-708">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="77dac-709">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-709">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="77dac-710">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="77dac-710">SelectShellForwardWord</span></span>

<span data-ttu-id="77dac-711">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="77dac-711">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="77dac-712">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-712">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="77dac-713">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="77dac-713">SelectShellNextWord</span></span>

<span data-ttu-id="77dac-714">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="77dac-714">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="77dac-715">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="77dac-715">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="77dac-716">SetMark</span><span class="sxs-lookup"><span data-stu-id="77dac-716">SetMark</span></span>

<span data-ttu-id="77dac-717">De huidige locatie van de cursor markeren voor gebruik in een volgende bewerkings opdracht.</span><span class="sxs-lookup"><span data-stu-id="77dac-717">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="77dac-718">Emacs: `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="77dac-718">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="77dac-719">Zoek functies</span><span class="sxs-lookup"><span data-stu-id="77dac-719">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="77dac-720">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="77dac-720">CharacterSearch</span></span>

<span data-ttu-id="77dac-721">Lees een teken en zoek voorwaarts naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-721">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="77dac-722">Als er een argument is opgegeven, zoekt u voorwaarts (of achterwaarts als negatieve) voor het ne voorval.</span><span class="sxs-lookup"><span data-stu-id="77dac-722">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="77dac-723">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="77dac-723">Cmd: `<F3>`</span></span>
- <span data-ttu-id="77dac-724">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="77dac-724">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="77dac-725">VI Invoeg modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="77dac-725">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="77dac-726">VI-opdracht modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="77dac-726">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="77dac-727">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="77dac-727">CharacterSearchBackward</span></span>

<span data-ttu-id="77dac-728">Lees een teken en zoek terug naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-728">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="77dac-729">Als er een argument is opgegeven, zoekt u terug (of als dit negatief is) voor het ne exemplaar.</span><span class="sxs-lookup"><span data-stu-id="77dac-729">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="77dac-730">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="77dac-730">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="77dac-731">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="77dac-731">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="77dac-732">VI Invoeg modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="77dac-732">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="77dac-733">VI-opdracht modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="77dac-733">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="77dac-734">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="77dac-734">RepeatLastCharSearch</span></span>

<span data-ttu-id="77dac-735">De laatst opgenomen zoek opdracht herhalen.</span><span class="sxs-lookup"><span data-stu-id="77dac-735">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="77dac-736">VI-opdracht modus: `<;>`</span><span class="sxs-lookup"><span data-stu-id="77dac-736">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="77dac-737">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="77dac-737">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="77dac-738">De laatst opgenomen zoek opdracht herhalen, maar in tegenovergestelde richting.</span><span class="sxs-lookup"><span data-stu-id="77dac-738">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="77dac-739">VI-opdracht modus: `<,>`</span><span class="sxs-lookup"><span data-stu-id="77dac-739">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="77dac-740">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="77dac-740">RepeatSearch</span></span>

<span data-ttu-id="77dac-741">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="77dac-741">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="77dac-742">VI-opdracht modus: `<n>`</span><span class="sxs-lookup"><span data-stu-id="77dac-742">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="77dac-743">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="77dac-743">RepeatSearchBackward</span></span>

<span data-ttu-id="77dac-744">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="77dac-744">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="77dac-745">VI-opdracht modus: `<N>`</span><span class="sxs-lookup"><span data-stu-id="77dac-745">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="77dac-746">SearchChar</span><span class="sxs-lookup"><span data-stu-id="77dac-746">SearchChar</span></span>

<span data-ttu-id="77dac-747">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-747">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="77dac-748">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="77dac-748">This is for 't' functionality.</span></span>

- <span data-ttu-id="77dac-749">VI-opdracht modus: `<f>`</span><span class="sxs-lookup"><span data-stu-id="77dac-749">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="77dac-750">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="77dac-750">SearchCharBackward</span></span>

<span data-ttu-id="77dac-751">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="77dac-752">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="77dac-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="77dac-753">VI-opdracht modus: `<F>`</span><span class="sxs-lookup"><span data-stu-id="77dac-753">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="77dac-754">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="77dac-754">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="77dac-755">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-755">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="77dac-756">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="77dac-756">This is for 'T' functionality.</span></span>

- <span data-ttu-id="77dac-757">VI-opdracht modus: `<T>`</span><span class="sxs-lookup"><span data-stu-id="77dac-757">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="77dac-758">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="77dac-758">SearchCharWithBackoff</span></span>

<span data-ttu-id="77dac-759">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="77dac-759">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="77dac-760">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="77dac-760">This is for 't' functionality.</span></span>

- <span data-ttu-id="77dac-761">VI-opdracht modus: `<t>`</span><span class="sxs-lookup"><span data-stu-id="77dac-761">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="77dac-762">SearchForward</span><span class="sxs-lookup"><span data-stu-id="77dac-762">SearchForward</span></span>

<span data-ttu-id="77dac-763">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="77dac-763">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="77dac-764">VI Invoeg modus: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="77dac-764">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="77dac-765">VI-opdracht modus: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="77dac-765">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="77dac-766">Aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="77dac-766">Custom Key Bindings</span></span>

<span data-ttu-id="77dac-767">PSReadLine ondersteunt aangepaste sleutel bindingen met behulp van de-cmdlet `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="77dac-767">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="77dac-768">De meeste aangepaste sleutel bindingen roepen een van de bovenstaande functies aan, bijvoorbeeld</span><span class="sxs-lookup"><span data-stu-id="77dac-768">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="77dac-769">U kunt een script Block binden aan een sleutel.</span><span class="sxs-lookup"><span data-stu-id="77dac-769">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="77dac-770">Het script Block kan veel wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="77dac-770">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="77dac-771">Enkele handige voor beelden zijn</span><span class="sxs-lookup"><span data-stu-id="77dac-771">Some useful examples include</span></span>

- <span data-ttu-id="77dac-772">de opdracht regel bewerken</span><span class="sxs-lookup"><span data-stu-id="77dac-772">edit the command line</span></span>
- <span data-ttu-id="77dac-773">een nieuw venster openen (bijvoorbeeld Help)</span><span class="sxs-lookup"><span data-stu-id="77dac-773">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="77dac-774">mappen wijzigen zonder de opdracht regel te wijzigen</span><span class="sxs-lookup"><span data-stu-id="77dac-774">change directories without changing the command line</span></span>

<span data-ttu-id="77dac-775">De script Block ontvangt twee argumenten:</span><span class="sxs-lookup"><span data-stu-id="77dac-775">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="77dac-776">`$key` -Een **[ConsoleKeyInfo]** -object dat de sleutel is die de aangepaste binding heeft geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="77dac-776">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="77dac-777">Als u dezelfde script Block aan meerdere sleutels koppelt en verschillende acties moet uitvoeren, afhankelijk van de sleutel, kunt u $key controleren.</span><span class="sxs-lookup"><span data-stu-id="77dac-777">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="77dac-778">Veel aangepaste bindingen negeren dit argument.</span><span class="sxs-lookup"><span data-stu-id="77dac-778">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="77dac-779">`$arg` -Een wille keurig argument.</span><span class="sxs-lookup"><span data-stu-id="77dac-779">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="77dac-780">Meestal is dit een geheel getal dat de gebruiker door gegeven van de sleutel bindingen DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="77dac-780">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="77dac-781">Als uw binding geen argumenten accepteert, is het redelijk om dit argument te negeren.</span><span class="sxs-lookup"><span data-stu-id="77dac-781">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="77dac-782">Laten we een voor beeld bekijken waarmee een opdracht regel wordt toegevoegd aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="77dac-782">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="77dac-783">Dit is handig wanneer u ervoor hebt gekozen om iets te doen, maar niet opnieuw moet invoeren van de opdracht regel die u al hebt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="77dac-783">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="77dac-784">U kunt veel meer voor beelden bekijken in het bestand `SamplePSReadLineProfile.ps1` dat is geïnstalleerd in de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="77dac-784">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="77dac-785">De meeste sleutel bindingen gebruiken enkele hulp functies voor het bewerken van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-785">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="77dac-786">Deze Api's worden beschreven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="77dac-786">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="77dac-787">Api's voor de ondersteuning van aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="77dac-787">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="77dac-788">De volgende functies zijn openbaar in micro soft. Power shell. PSConsoleReadLine, maar kunnen niet rechtstreeks aan een sleutel worden gebonden.</span><span class="sxs-lookup"><span data-stu-id="77dac-788">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="77dac-789">De meeste zijn handig in aangepaste sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="77dac-789">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="77dac-790">Een opdracht regel toevoegen aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="77dac-790">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="77dac-791">Wis de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="77dac-791">Clear the kill-ring.</span></span>  <span data-ttu-id="77dac-792">Dit wordt meestal gebruikt voor het testen.</span><span class="sxs-lookup"><span data-stu-id="77dac-792">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="77dac-793">Verwijder de lengte tekens uit het begin.</span><span class="sxs-lookup"><span data-stu-id="77dac-793">Delete length characters from start.</span></span>  <span data-ttu-id="77dac-794">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="77dac-794">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="77dac-795">Voer de actie opname uit op basis van de voor keuren van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="77dac-795">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="77dac-796">Deze twee functies halen nuttige informatie op over de huidige status van de invoer buffer.</span><span class="sxs-lookup"><span data-stu-id="77dac-796">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="77dac-797">De eerste wordt vaak gebruikt voor eenvoudige gevallen.</span><span class="sxs-lookup"><span data-stu-id="77dac-797">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="77dac-798">De tweede wordt gebruikt als uw binding iets geavanceerder gaat met de AST.</span><span class="sxs-lookup"><span data-stu-id="77dac-798">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="77dac-799">Deze functie wordt gebruikt door Get-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="77dac-799">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="77dac-800">Deze functie wordt gebruikt door Get-PSReadLineOption en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="77dac-800">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="77dac-801">Als er niets is geselecteerd op de opdracht regel, wordt-1 geretourneerd in zowel start als length.</span><span class="sxs-lookup"><span data-stu-id="77dac-801">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="77dac-802">Als er een selectie is op de opdracht regel, worden het begin en de lengte van de selectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="77dac-802">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="77dac-803">Voeg een teken of teken reeks toe aan de cursor.</span><span class="sxs-lookup"><span data-stu-id="77dac-803">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="77dac-804">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="77dac-804">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="77dac-805">Dit is het belangrijkste ingangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="77dac-805">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="77dac-806">Er wordt geen recursie ondersteund, dus is niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="77dac-806">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="77dac-807">Deze functie wordt gebruikt door Remove-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="77dac-807">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="77dac-808">Vervang een deel van de invoer.</span><span class="sxs-lookup"><span data-stu-id="77dac-808">Replace some of the input.</span></span> <span data-ttu-id="77dac-809">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="77dac-809">This operation supports undo/redo.</span></span> <span data-ttu-id="77dac-810">U kunt het beste verwijderen gevolgd door INSERT, omdat het wordt beschouwd als één actie voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="77dac-810">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="77dac-811">De cursor verplaatsen naar de opgegeven verschuiving.</span><span class="sxs-lookup"><span data-stu-id="77dac-811">Move the cursor to the given offset.</span></span> <span data-ttu-id="77dac-812">Cursor verplaatsing wordt niet bijgehouden voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="77dac-812">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="77dac-813">Deze functie is een helper-methode die wordt gebruikt door de cmdlet Set-PSReadLineOption, maar kan handig zijn voor een aangepaste sleutel binding die tijdelijk een instelling wil wijzigen.</span><span class="sxs-lookup"><span data-stu-id="77dac-813">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="77dac-814">Deze Help methode wordt gebruikt voor aangepaste bindingen die voldoen aan DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="77dac-814">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="77dac-815">Een typische aanroep ziet eruit als</span><span class="sxs-lookup"><span data-stu-id="77dac-815">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="77dac-816">Notitie</span><span class="sxs-lookup"><span data-stu-id="77dac-816">Note</span></span>

### <a name="command-history"></a><span data-ttu-id="77dac-817">Opdracht geschiedenis</span><span class="sxs-lookup"><span data-stu-id="77dac-817">Command History</span></span>

<span data-ttu-id="77dac-818">PSReadLine onderhoudt een geschiedenis bestand met alle opdrachten en gegevens die u hebt ingevoerd op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="77dac-818">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="77dac-819">Dit kan gevoelige gegevens bevatten, inclusief wacht woorden.</span><span class="sxs-lookup"><span data-stu-id="77dac-819">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="77dac-820">Als u bijvoorbeeld de cmdlet gebruikt, `ConvertTo-SecureString` wordt het wacht woord in het geschiedenis bestand vastgelegd als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="77dac-820">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="77dac-821">De geschiedenis bestanden zijn een bestand met de naam `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="77dac-821">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="77dac-822">Op Windows-systemen wordt het geschiedenis bestand opgeslagen op `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="77dac-822">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="77dac-823">Op niet-Windows-systemen worden de geschiedenis bestanden opgeslagen in `$env:XDG_DATA_HOME/powershell/PSReadLine` of `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="77dac-823">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="77dac-824">Feedback & bijdragen aan PSReadLine</span><span class="sxs-lookup"><span data-stu-id="77dac-824">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="77dac-825">PSReadLine op GitHub</span><span class="sxs-lookup"><span data-stu-id="77dac-825">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="77dac-826">U kunt een pull-aanvraag verzenden of feedback verzenden op de pagina GitHub.</span><span class="sxs-lookup"><span data-stu-id="77dac-826">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="77dac-827">Zie ook</span><span class="sxs-lookup"><span data-stu-id="77dac-827">See Also</span></span>

<span data-ttu-id="77dac-828">PSReadLine wordt sterk beïnvloed door de GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="77dac-828">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
