---
description: PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over PSReadLine
ms.openlocfilehash: ad6e85a30f866cb332c89a4c36f42231f511f5ae
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253159"
---
# <a name="psreadline"></a><span data-ttu-id="99168-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="99168-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="99168-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="99168-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="99168-106">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="99168-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="99168-107">PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="99168-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="99168-108">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="99168-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="99168-109">PSReadLine 2,0 biedt een krachtige opdracht regel voor het bewerken van de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="99168-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="99168-110">De oplossing biedt het volgende:</span><span class="sxs-lookup"><span data-stu-id="99168-110">It provides:</span></span>

- <span data-ttu-id="99168-111">Syntaxis kleur van de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="99168-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="99168-112">Een visuele indicatie van syntaxis fouten</span><span class="sxs-lookup"><span data-stu-id="99168-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="99168-113">Een betere ervaring met meerdere regels (zowel bewerkingen als geschiedenis)</span><span class="sxs-lookup"><span data-stu-id="99168-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="99168-114">Aanpas bare sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="99168-114">Customizable key bindings</span></span>
- <span data-ttu-id="99168-115">Cmd-en emacs-modi</span><span class="sxs-lookup"><span data-stu-id="99168-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="99168-116">Veel configuratie opties</span><span class="sxs-lookup"><span data-stu-id="99168-116">Many configuration options</span></span>
- <span data-ttu-id="99168-117">Bash-stijl voltooiing (optioneel in CMD-modus, standaard in Emacs-modus)</span><span class="sxs-lookup"><span data-stu-id="99168-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="99168-118">Emacs Yank/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="99168-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="99168-119">"Woord" verplaatsing en afsluiten op basis van Power shell-tokens</span><span class="sxs-lookup"><span data-stu-id="99168-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="99168-120">De volgende functies zijn beschikbaar in de klasse **[micro soft. Power shell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="99168-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="99168-121">Basis bewerkings functies</span><span class="sxs-lookup"><span data-stu-id="99168-121">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="99168-122">Afbreken</span><span class="sxs-lookup"><span data-stu-id="99168-122">Abort</span></span>

<span data-ttu-id="99168-123">De huidige actie afbreken, bijvoorbeeld een incrementele geschiedenis zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="99168-123">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="99168-124">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="99168-124">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="99168-125">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="99168-125">AcceptAndGetNext</span></span>

<span data-ttu-id="99168-126">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="99168-126">Attempt to execute the current input.</span></span> <span data-ttu-id="99168-127">Als deze kan worden uitgevoerd (zoals AcceptLine), kunt u het volgende item uit de geschiedenis intrekken de volgende keer dat ReadLine wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="99168-127">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="99168-128">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="99168-128">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="99168-129">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="99168-129">AcceptLine</span></span>

<span data-ttu-id="99168-130">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="99168-130">Attempt to execute the current input.</span></span> <span data-ttu-id="99168-131">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="99168-131">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="99168-132">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="99168-132">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="99168-133">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="99168-133">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="99168-134">VI Invoeg modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="99168-134">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="99168-135">AddLine</span><span class="sxs-lookup"><span data-stu-id="99168-135">AddLine</span></span>

<span data-ttu-id="99168-136">De vervolg prompt wordt weer gegeven op de volgende regel en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="99168-136">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="99168-137">Dit is handig om invoer in meerdere regels als één opdracht in te voeren, zelfs wanneer één regel volledig wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="99168-137">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="99168-138">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="99168-138">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="99168-139">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="99168-139">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="99168-140">VI Invoeg modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="99168-140">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="99168-141">VI-opdracht modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="99168-141">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="99168-142">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="99168-142">BackwardDeleteChar</span></span>

<span data-ttu-id="99168-143">Verwijder het teken voor de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-143">Delete the character before the cursor.</span></span>

- <span data-ttu-id="99168-144">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="99168-144">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="99168-145">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="99168-145">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="99168-146">VI Invoeg modus: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="99168-146">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="99168-147">VI-opdracht modus: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="99168-147">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="99168-148">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="99168-148">BackwardDeleteLine</span></span>

<span data-ttu-id="99168-149">Net als BackwardKillLine: verwijdert tekst van het punt naar het begin van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="99168-149">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="99168-150">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="99168-150">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="99168-151">VI Invoeg modus: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="99168-151">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="99168-152">VI-opdracht modus: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="99168-152">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="99168-153">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="99168-153">BackwardDeleteWord</span></span>

<span data-ttu-id="99168-154">Hiermee verwijdert u het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="99168-154">Deletes the previous word.</span></span>

- <span data-ttu-id="99168-155">VI-opdracht modus: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="99168-155">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="99168-156">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="99168-156">BackwardKillLine</span></span>

<span data-ttu-id="99168-157">De invoer van het begin van de invoer wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-157">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="99168-158">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="99168-158">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="99168-159">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="99168-159">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="99168-160">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="99168-160">BackwardKillWord</span></span>

<span data-ttu-id="99168-161">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-161">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="99168-162">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="99168-162">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="99168-163">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="99168-163">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="99168-164">Cmd `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="99168-164">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="99168-165">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="99168-165">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="99168-166">VI Invoeg modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="99168-166">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="99168-167">VI-opdracht modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="99168-167">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="99168-168">CancelLine</span><span class="sxs-lookup"><span data-stu-id="99168-168">CancelLine</span></span>

<span data-ttu-id="99168-169">De huidige invoer annuleren, waardoor de invoer op het scherm wordt weer gegeven, maar terugkeert naar de host, zodat de prompt opnieuw wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="99168-169">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="99168-170">VI Invoeg modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="99168-170">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="99168-171">VI-opdracht modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="99168-171">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="99168-172">Kopiëren</span><span class="sxs-lookup"><span data-stu-id="99168-172">Copy</span></span>

<span data-ttu-id="99168-173">Kopieer de geselecteerde regio naar het klem bord van het systeem.</span><span class="sxs-lookup"><span data-stu-id="99168-173">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="99168-174">Als er geen regio is geselecteerd, kopieert u de hele regel.</span><span class="sxs-lookup"><span data-stu-id="99168-174">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="99168-175">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="99168-175">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="99168-176">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="99168-176">CopyOrCancelLine</span></span>

<span data-ttu-id="99168-177">Als tekst is geselecteerd, kopieert u deze naar het klem bord. anders annuleert u de regel.</span><span class="sxs-lookup"><span data-stu-id="99168-177">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="99168-178">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="99168-178">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="99168-179">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="99168-179">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="99168-180">Knippen</span><span class="sxs-lookup"><span data-stu-id="99168-180">Cut</span></span>

<span data-ttu-id="99168-181">Geselecteerde regio verwijderen Verwijderde tekst in het systeem Klembord plaatsen.</span><span class="sxs-lookup"><span data-stu-id="99168-181">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="99168-182">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="99168-182">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="99168-183">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="99168-183">DeleteChar</span></span>

<span data-ttu-id="99168-184">Verwijder het teken onder de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-184">Delete the character under the cursor.</span></span>

- <span data-ttu-id="99168-185">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="99168-185">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="99168-186">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="99168-186">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="99168-187">VI Invoeg modus: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="99168-187">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="99168-188">VI-opdracht modus: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="99168-188">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="99168-189">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="99168-189">DeleteCharOrExit</span></span>

<span data-ttu-id="99168-190">Verwijder het teken onder de cursor of als de regel leeg is, sluit u het proces.</span><span class="sxs-lookup"><span data-stu-id="99168-190">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="99168-191">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="99168-191">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="99168-192">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="99168-192">DeleteEndOfWord</span></span>

<span data-ttu-id="99168-193">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="99168-193">Delete to the end of the word.</span></span>

- <span data-ttu-id="99168-194">VI-opdracht modus: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="99168-194">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="99168-195">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="99168-195">DeleteLine</span></span>

<span data-ttu-id="99168-196">Hiermee verwijdert u de huidige regel, waarbij u ongedaan maken inschakelt.</span><span class="sxs-lookup"><span data-stu-id="99168-196">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="99168-197">VI-opdracht modus: `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="99168-197">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="99168-198">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="99168-198">DeleteLineToFirstChar</span></span>

<span data-ttu-id="99168-199">Hiermee wordt tekst van de cursor verwijderd naar het eerste niet-lege teken van de regel.</span><span class="sxs-lookup"><span data-stu-id="99168-199">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="99168-200">VI-opdracht modus: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="99168-200">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="99168-201">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="99168-201">DeleteToEnd</span></span>

<span data-ttu-id="99168-202">Verwijderen tot aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="99168-202">Delete to the end of the line.</span></span>

- <span data-ttu-id="99168-203">VI-opdracht modus: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="99168-203">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="99168-204">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="99168-204">DeleteWord</span></span>

<span data-ttu-id="99168-205">Verwijder het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="99168-205">Delete the next word.</span></span>

- <span data-ttu-id="99168-206">VI-opdracht modus: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="99168-206">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="99168-207">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="99168-207">ForwardDeleteLine</span></span>

<span data-ttu-id="99168-208">Net als ForwardKillLine: verwijdert tekst van het punt naar het einde van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="99168-208">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="99168-209">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="99168-209">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="99168-210">VI Invoeg modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="99168-210">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="99168-211">VI-opdracht modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="99168-211">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="99168-212">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="99168-212">InsertLineAbove</span></span>

<span data-ttu-id="99168-213">Er wordt een nieuwe lege regel gemaakt op de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="99168-213">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="99168-214">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="99168-214">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="99168-215">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="99168-215">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="99168-216">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="99168-216">InsertLineBelow</span></span>

<span data-ttu-id="99168-217">Er wordt een nieuwe lege regel gemaakt onder de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="99168-217">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="99168-218">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="99168-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="99168-219">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="99168-219">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="99168-220">InvertCase</span><span class="sxs-lookup"><span data-stu-id="99168-220">InvertCase</span></span>

<span data-ttu-id="99168-221">Het hoofdletter gebruik van het huidige teken omkeren en verplaatsen naar het volgende.</span><span class="sxs-lookup"><span data-stu-id="99168-221">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="99168-222">VI-opdracht modus: `<~>`</span><span class="sxs-lookup"><span data-stu-id="99168-222">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="99168-223">KillLine</span><span class="sxs-lookup"><span data-stu-id="99168-223">KillLine</span></span>

<span data-ttu-id="99168-224">De invoer wissen van de cursor tot het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="99168-224">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="99168-225">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="99168-225">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="99168-226">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="99168-226">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="99168-227">KillRegion</span><span class="sxs-lookup"><span data-stu-id="99168-227">KillRegion</span></span>

<span data-ttu-id="99168-228">Beëindig de tekst tussen de cursor en de markering.</span><span class="sxs-lookup"><span data-stu-id="99168-228">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="99168-229">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-229">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="99168-230">KillWord</span><span class="sxs-lookup"><span data-stu-id="99168-230">KillWord</span></span>

<span data-ttu-id="99168-231">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="99168-231">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="99168-232">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="99168-232">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="99168-233">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="99168-233">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="99168-234">Cmd `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="99168-234">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="99168-235">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="99168-235">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="99168-236">VI Invoeg modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="99168-236">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="99168-237">VI-opdracht modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="99168-237">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="99168-238">Plakken</span><span class="sxs-lookup"><span data-stu-id="99168-238">Paste</span></span>

<span data-ttu-id="99168-239">Tekst van het klem bord van het systeem plakken.</span><span class="sxs-lookup"><span data-stu-id="99168-239">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="99168-240">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="99168-240">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="99168-241">VI Invoeg modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="99168-241">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="99168-242">VI-opdracht modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="99168-242">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99168-243">Wanneer u de functie **Paste** gebruikt, wordt de volledige inhoud van de Klembord buffer geplakt in de invoer buffer van PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="99168-243">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="99168-244">De invoer buffer wordt vervolgens door gegeven aan de Power shell-parser.</span><span class="sxs-lookup"><span data-stu-id="99168-244">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="99168-245">Invoer die met de **rechter muisknop op** de plak methode van de console toepassing wordt geplakt, wordt met één teken per keer naar de invoer buffer gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="99168-245">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="99168-246">De invoer buffer wordt door gegeven aan de parser wanneer een teken voor een nieuwe regel wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="99168-246">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="99168-247">Daarom wordt de invoer één regel tegelijk geparseerd.</span><span class="sxs-lookup"><span data-stu-id="99168-247">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="99168-248">Het verschil tussen plak methoden resulteert in een ander uitvoerings gedrag.</span><span class="sxs-lookup"><span data-stu-id="99168-248">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="99168-249">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="99168-249">PasteAfter</span></span>

<span data-ttu-id="99168-250">Plak het klem bord na de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="99168-250">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="99168-251">VI-opdracht modus: `<p>`</span><span class="sxs-lookup"><span data-stu-id="99168-251">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="99168-252">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="99168-252">PasteBefore</span></span>

<span data-ttu-id="99168-253">Plak het klem bord vóór de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="99168-253">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="99168-254">VI-opdracht modus: `<P>`</span><span class="sxs-lookup"><span data-stu-id="99168-254">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="99168-255">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="99168-255">PrependAndAccept</span></span>

<span data-ttu-id="99168-256">Laten voorafgaan door een ' # ' en accepteer de regel.</span><span class="sxs-lookup"><span data-stu-id="99168-256">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="99168-257">VI-opdracht modus: `<#>`</span><span class="sxs-lookup"><span data-stu-id="99168-257">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="99168-258">Opnieuw uitvoeren</span><span class="sxs-lookup"><span data-stu-id="99168-258">Redo</span></span>

<span data-ttu-id="99168-259">Undo ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="99168-259">Undo an undo.</span></span>

- <span data-ttu-id="99168-260">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="99168-260">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="99168-261">VI Invoeg modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="99168-261">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="99168-262">VI-opdracht modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="99168-262">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="99168-263">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="99168-263">RepeatLastCommand</span></span>

<span data-ttu-id="99168-264">Herhaal de laatste tekst wijziging.</span><span class="sxs-lookup"><span data-stu-id="99168-264">Repeat the last text modification.</span></span>

- <span data-ttu-id="99168-265">VI-opdracht modus: `<.>`</span><span class="sxs-lookup"><span data-stu-id="99168-265">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="99168-266">RevertLine</span><span class="sxs-lookup"><span data-stu-id="99168-266">RevertLine</span></span>

<span data-ttu-id="99168-267">Hiermee wordt alle invoer teruggezet naar de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="99168-267">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="99168-268">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="99168-268">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="99168-269">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="99168-269">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="99168-270">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="99168-270">ShellBackwardKillWord</span></span>

<span data-ttu-id="99168-271">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-271">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="99168-272">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="99168-272">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="99168-273">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="99168-273">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="99168-274">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-274">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="99168-275">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="99168-275">ShellKillWord</span></span>

<span data-ttu-id="99168-276">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="99168-276">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="99168-277">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="99168-277">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="99168-278">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="99168-278">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="99168-279">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-279">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="99168-280">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="99168-280">SwapCharacters</span></span>

<span data-ttu-id="99168-281">Het huidige teken en de eerste vervangen door wisselen.</span><span class="sxs-lookup"><span data-stu-id="99168-281">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="99168-282">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="99168-282">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="99168-283">VI Invoeg modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="99168-283">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="99168-284">VI-opdracht modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="99168-284">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="99168-285">Ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="99168-285">Undo</span></span>

<span data-ttu-id="99168-286">Een vorige bewerking ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="99168-286">Undo a previous edit.</span></span>

- <span data-ttu-id="99168-287">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="99168-287">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="99168-288">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="99168-288">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="99168-289">VI Invoeg modus: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="99168-289">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="99168-290">VI-opdracht modus: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="99168-290">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="99168-291">UndoAll</span><span class="sxs-lookup"><span data-stu-id="99168-291">UndoAll</span></span>

<span data-ttu-id="99168-292">Alle vorige bewerkingen voor de regel ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="99168-292">Undo all previous edits for line.</span></span>

- <span data-ttu-id="99168-293">VI-opdracht modus: `<U>`</span><span class="sxs-lookup"><span data-stu-id="99168-293">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="99168-294">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="99168-294">UnixWordRubout</span></span>

<span data-ttu-id="99168-295">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-295">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="99168-296">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="99168-296">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="99168-297">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="99168-297">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="99168-298">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="99168-298">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="99168-299">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="99168-299">ValidateAndAcceptLine</span></span>

<span data-ttu-id="99168-300">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="99168-300">Attempt to execute the current input.</span></span> <span data-ttu-id="99168-301">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="99168-301">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="99168-302">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="99168-302">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="99168-303">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="99168-303">ViAcceptLine</span></span>

<span data-ttu-id="99168-304">Accepteer de regel en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="99168-304">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="99168-305">VI-opdracht modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="99168-305">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="99168-306">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="99168-306">ViAcceptLineOrExit</span></span>

<span data-ttu-id="99168-307">Als DeleteCharOrExit in de Emacs-modus, maar wel in plaats van een teken te verwijderen, accepteert u de regel.</span><span class="sxs-lookup"><span data-stu-id="99168-307">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="99168-308">VI Invoeg modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="99168-308">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="99168-309">VI-opdracht modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="99168-309">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="99168-310">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="99168-310">ViAppendLine</span></span>

<span data-ttu-id="99168-311">Er wordt een nieuwe regel ingevoegd onder de huidige regel.</span><span class="sxs-lookup"><span data-stu-id="99168-311">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="99168-312">VI-opdracht modus: `<o>`</span><span class="sxs-lookup"><span data-stu-id="99168-312">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="99168-313">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="99168-313">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="99168-314">Hiermee verwijdert u het vorige woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="99168-314">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="99168-315">VI-opdracht modus: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="99168-315">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="99168-316">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="99168-316">ViBackwardGlob</span></span>

<span data-ttu-id="99168-317">Verplaatst de cursor terug naar het begin van het vorige woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="99168-317">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="99168-318">VI-opdracht modus: `<B>`</span><span class="sxs-lookup"><span data-stu-id="99168-318">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="99168-319">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="99168-319">ViDeleteBrace</span></span>

<span data-ttu-id="99168-320">Zoek de accolade, het haakje sluiten of de vier Kante haken en verwijder alle inhoud binnen, inclusief de accolade.</span><span class="sxs-lookup"><span data-stu-id="99168-320">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="99168-321">VI-opdracht modus: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="99168-321">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="99168-322">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="99168-322">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="99168-323">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="99168-323">Delete to the end of the word.</span></span>

- <span data-ttu-id="99168-324">VI-opdracht modus: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="99168-324">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="99168-325">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="99168-325">ViDeleteGlob</span></span>

<span data-ttu-id="99168-326">De volgende Globs verwijderen (door witruimte gescheiden woord).</span><span class="sxs-lookup"><span data-stu-id="99168-326">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="99168-327">VI-opdracht modus: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="99168-327">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="99168-328">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="99168-328">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="99168-329">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="99168-329">Deletes until given character.</span></span>

- <span data-ttu-id="99168-330">VI-opdracht modus: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="99168-330">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="99168-331">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="99168-331">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="99168-332">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="99168-332">Deletes until given character.</span></span>

- <span data-ttu-id="99168-333">VI-opdracht modus: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="99168-333">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="99168-334">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="99168-334">ViDeleteToChar</span></span>

<span data-ttu-id="99168-335">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="99168-335">Deletes until given character.</span></span>

- <span data-ttu-id="99168-336">VI-opdracht modus: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="99168-336">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="99168-337">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="99168-337">ViDeleteToCharBackward</span></span>

<span data-ttu-id="99168-338">Hiermee verwijdert u achterwaartse tekens tot aan het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="99168-338">Deletes backwards until given character.</span></span>

- <span data-ttu-id="99168-339">VI-opdracht modus: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="99168-339">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="99168-340">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="99168-340">ViInsertAtBegining</span></span>

<span data-ttu-id="99168-341">Schakel over naar de Invoeg modus en plaats de cursor aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="99168-341">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="99168-342">VI-opdracht modus: `<I>`</span><span class="sxs-lookup"><span data-stu-id="99168-342">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="99168-343">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="99168-343">ViInsertAtEnd</span></span>

<span data-ttu-id="99168-344">Schakel over naar de Invoeg modus en plaats de cursor aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="99168-344">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="99168-345">VI-opdracht modus: `<A>`</span><span class="sxs-lookup"><span data-stu-id="99168-345">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="99168-346">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="99168-346">ViInsertLine</span></span>

<span data-ttu-id="99168-347">Boven de huidige regel wordt een nieuwe regel ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="99168-347">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="99168-348">VI-opdracht modus: `<O>`</span><span class="sxs-lookup"><span data-stu-id="99168-348">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="99168-349">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="99168-349">ViInsertWithAppend</span></span>

<span data-ttu-id="99168-350">Toevoegen vanaf de huidige regel positie.</span><span class="sxs-lookup"><span data-stu-id="99168-350">Append from the current line position.</span></span>

- <span data-ttu-id="99168-351">VI-opdracht modus: `<a>`</span><span class="sxs-lookup"><span data-stu-id="99168-351">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="99168-352">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="99168-352">ViInsertWithDelete</span></span>

<span data-ttu-id="99168-353">Verwijder het huidige teken en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="99168-353">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="99168-354">VI-opdracht modus: `<s>`</span><span class="sxs-lookup"><span data-stu-id="99168-354">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="99168-355">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="99168-355">ViJoinLines</span></span>

<span data-ttu-id="99168-356">De huidige regel en de volgende regel worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="99168-356">Joins the current line and the next line.</span></span>

- <span data-ttu-id="99168-357">VI-opdracht modus: `<J>`</span><span class="sxs-lookup"><span data-stu-id="99168-357">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="99168-358">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="99168-358">ViReplaceLine</span></span>

<span data-ttu-id="99168-359">De volledige opdracht regel wissen.</span><span class="sxs-lookup"><span data-stu-id="99168-359">Erase the entire command line.</span></span>

- <span data-ttu-id="99168-360">VI-opdracht modus: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="99168-360">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="99168-361">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="99168-361">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="99168-362">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="99168-362">Replaces until given character.</span></span>

- <span data-ttu-id="99168-363">VI-opdracht modus: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="99168-363">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="99168-364">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="99168-364">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="99168-365">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="99168-365">Replaces until given character.</span></span>

- <span data-ttu-id="99168-366">VI-opdracht modus: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="99168-366">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="99168-367">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="99168-367">ViReplaceToChar</span></span>

<span data-ttu-id="99168-368">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="99168-368">Deletes until given character.</span></span>

- <span data-ttu-id="99168-369">VI-opdracht modus: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="99168-369">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="99168-370">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="99168-370">ViReplaceToCharBackward</span></span>

<span data-ttu-id="99168-371">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="99168-371">Replaces until given character.</span></span>

- <span data-ttu-id="99168-372">VI-opdracht modus: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="99168-372">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="99168-373">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="99168-373">ViYankBeginningOfLine</span></span>

<span data-ttu-id="99168-374">Yank vanaf het begin van de buffer naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-374">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="99168-375">VI-opdracht modus: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="99168-375">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="99168-376">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="99168-376">ViYankEndOfGlob</span></span>

<span data-ttu-id="99168-377">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="99168-377">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="99168-378">VI-opdracht modus: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="99168-378">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="99168-379">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="99168-379">ViYankEndOfWord</span></span>

<span data-ttu-id="99168-380">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="99168-380">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="99168-381">VI-opdracht modus: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="99168-381">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="99168-382">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="99168-382">ViYankLeft</span></span>

<span data-ttu-id="99168-383">Yank teken (s) links van de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-383">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="99168-384">VI-opdracht modus: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="99168-384">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="99168-385">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="99168-385">ViYankLine</span></span>

<span data-ttu-id="99168-386">Yank de volledige buffer.</span><span class="sxs-lookup"><span data-stu-id="99168-386">Yank the entire buffer.</span></span>

- <span data-ttu-id="99168-387">VI-opdracht modus: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="99168-387">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="99168-388">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="99168-388">ViYankNextGlob</span></span>

<span data-ttu-id="99168-389">Yank van de cursor naar het begin van de volgende woord (en).</span><span class="sxs-lookup"><span data-stu-id="99168-389">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="99168-390">VI-opdracht modus: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="99168-390">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="99168-391">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="99168-391">ViYankNextWord</span></span>

<span data-ttu-id="99168-392">Yank het woord (en) na de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-392">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="99168-393">VI-opdracht modus: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="99168-393">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="99168-394">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="99168-394">ViYankPercent</span></span>

<span data-ttu-id="99168-395">Yank naar/van overeenkomende accolade.</span><span class="sxs-lookup"><span data-stu-id="99168-395">Yank to/from matching brace.</span></span>

- <span data-ttu-id="99168-396">VI-opdracht modus: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="99168-396">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="99168-397">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="99168-397">ViYankPreviousGlob</span></span>

<span data-ttu-id="99168-398">Yank vanaf het begin van het (de) woord (en) tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-398">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="99168-399">VI-opdracht modus: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="99168-399">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="99168-400">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="99168-400">ViYankPreviousWord</span></span>

<span data-ttu-id="99168-401">Yank de woorden vóór de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-401">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="99168-402">VI-opdracht modus: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="99168-402">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="99168-403">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="99168-403">ViYankRight</span></span>

<span data-ttu-id="99168-404">Yank teken (s) onder en rechts van de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-404">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="99168-405">VI-opdracht modus: `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="99168-405">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="99168-406">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="99168-406">ViYankToEndOfLine</span></span>

<span data-ttu-id="99168-407">Yank van de cursor tot het einde van de buffer.</span><span class="sxs-lookup"><span data-stu-id="99168-407">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="99168-408">VI-opdracht modus: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="99168-408">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="99168-409">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="99168-409">ViYankToFirstChar</span></span>

<span data-ttu-id="99168-410">Yank van het eerste niet-spatie teken tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-410">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="99168-411">VI-opdracht modus: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="99168-411">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="99168-412">Yank</span><span class="sxs-lookup"><span data-stu-id="99168-412">Yank</span></span>

<span data-ttu-id="99168-413">Voeg de meest recent afgebroken tekst toe aan de invoer.</span><span class="sxs-lookup"><span data-stu-id="99168-413">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="99168-414">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="99168-414">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="99168-415">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="99168-415">YankLastArg</span></span>

<span data-ttu-id="99168-416">Yank het laatste argument van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="99168-416">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="99168-417">Met een argument, de eerste keer dat deze wordt aangeroepen, gedraagt zich op dezelfde manier als YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="99168-417">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="99168-418">Als meerdere keren worden aangeroepen, wordt door de geschiedenis en ARG de richting ingesteld (negatief de richting omkeren.)</span><span class="sxs-lookup"><span data-stu-id="99168-418">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="99168-419">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="99168-419">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="99168-420">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="99168-420">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="99168-421">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="99168-421">YankNthArg</span></span>

<span data-ttu-id="99168-422">Yank het eerste argument (na de opdracht) van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="99168-422">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="99168-423">Met een argument, Yank het ne argument (vanaf 0), als het argument negatief is, begint vanaf het laatste argument.</span><span class="sxs-lookup"><span data-stu-id="99168-423">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="99168-424">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="99168-424">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="99168-425">YankPop</span><span class="sxs-lookup"><span data-stu-id="99168-425">YankPop</span></span>

<span data-ttu-id="99168-426">Als de vorige bewerking Yank of YankPop is, vervangt u de eerder yanked tekst door de volgende afgebroken tekst van de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="99168-426">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="99168-427">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="99168-427">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="99168-428">Functies voor cursor verplaatsing</span><span class="sxs-lookup"><span data-stu-id="99168-428">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="99168-429">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="99168-429">BackwardChar</span></span>

<span data-ttu-id="99168-430">De cursor één teken naar links verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="99168-430">Move the cursor one character to the left.</span></span> <span data-ttu-id="99168-431">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="99168-431">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="99168-432">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-432">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="99168-433">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="99168-433">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="99168-434">VI Invoeg modus: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-434">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="99168-435">VI-opdracht modus: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="99168-435">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="99168-436">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="99168-436">BackwardWord</span></span>

<span data-ttu-id="99168-437">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="99168-437">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="99168-438">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="99168-438">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="99168-439">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-439">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="99168-440">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="99168-440">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="99168-441">VI Invoeg modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-441">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="99168-442">VI-opdracht modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-442">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="99168-443">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="99168-443">BeginningOfLine</span></span>

<span data-ttu-id="99168-444">Als de invoer meerdere regels heeft, gaat u naar het begin van de huidige regel of gaat u naar het begin van de invoer als deze al aan het begin van de regel staat.</span><span class="sxs-lookup"><span data-stu-id="99168-444">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="99168-445">Als de invoer één regel heeft, gaat u naar het begin van de invoer.</span><span class="sxs-lookup"><span data-stu-id="99168-445">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="99168-446">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="99168-446">Cmd: `<Home>`</span></span>
- <span data-ttu-id="99168-447">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="99168-447">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="99168-448">VI Invoeg modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="99168-448">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="99168-449">VI-opdracht modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="99168-449">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="99168-450">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="99168-450">EndOfLine</span></span>

<span data-ttu-id="99168-451">Als de invoer meerdere regels heeft, gaat u naar het einde van de huidige regel of gaat u naar het einde van de invoer als u aan het einde van de regel bent.</span><span class="sxs-lookup"><span data-stu-id="99168-451">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="99168-452">Als de invoer één regel heeft, gaat u naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="99168-452">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="99168-453">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="99168-453">Cmd: `<End>`</span></span>
- <span data-ttu-id="99168-454">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="99168-454">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="99168-455">VI Invoeg modus: `<End>`</span><span class="sxs-lookup"><span data-stu-id="99168-455">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="99168-456">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="99168-456">ForwardChar</span></span>

<span data-ttu-id="99168-457">De cursor één teken naar rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="99168-457">Move the cursor one character to the right.</span></span> <span data-ttu-id="99168-458">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="99168-458">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="99168-459">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-459">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="99168-460">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="99168-460">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="99168-461">VI Invoeg modus: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-461">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="99168-462">VI-opdracht modus: `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="99168-462">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="99168-463">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="99168-463">ForwardWord</span></span>

<span data-ttu-id="99168-464">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="99168-464">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="99168-465">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="99168-465">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="99168-466">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="99168-466">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="99168-467">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="99168-467">GotoBrace</span></span>

<span data-ttu-id="99168-468">Ga naar de accolade, haakjes of vier Kante haakjes.</span><span class="sxs-lookup"><span data-stu-id="99168-468">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="99168-469">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="99168-469">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="99168-470">VI Invoeg modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="99168-470">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="99168-471">VI-opdracht modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="99168-471">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="99168-472">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="99168-472">GotoColumn</span></span>

<span data-ttu-id="99168-473">Ga naar de kolom die wordt aangegeven door arg.</span><span class="sxs-lookup"><span data-stu-id="99168-473">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="99168-474">VI-opdracht modus: `<|>`</span><span class="sxs-lookup"><span data-stu-id="99168-474">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="99168-475">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="99168-475">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="99168-476">De cursor verplaatsen naar het eerste niet-lege teken in de regel.</span><span class="sxs-lookup"><span data-stu-id="99168-476">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="99168-477">VI-opdracht modus: `<^>`</span><span class="sxs-lookup"><span data-stu-id="99168-477">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="99168-478">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="99168-478">MoveToEndOfLine</span></span>

<span data-ttu-id="99168-479">De cursor verplaatsen naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="99168-479">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="99168-480">VI-opdracht modus: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="99168-480">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="99168-481">NextLine</span><span class="sxs-lookup"><span data-stu-id="99168-481">NextLine</span></span>

<span data-ttu-id="99168-482">De cursor verplaatsen naar de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="99168-482">Move the cursor to the next line.</span></span>

- <span data-ttu-id="99168-483">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-483">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="99168-484">NextWord</span><span class="sxs-lookup"><span data-stu-id="99168-484">NextWord</span></span>

<span data-ttu-id="99168-485">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="99168-485">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="99168-486">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="99168-486">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="99168-487">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-487">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="99168-488">VI Invoeg modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-488">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="99168-489">VI-opdracht modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-489">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="99168-490">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="99168-490">NextWordEnd</span></span>

<span data-ttu-id="99168-491">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="99168-491">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="99168-492">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="99168-492">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="99168-493">VI-opdracht modus: `<e>`</span><span class="sxs-lookup"><span data-stu-id="99168-493">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="99168-494">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="99168-494">PreviousLine</span></span>

<span data-ttu-id="99168-495">Verplaats de cursor naar de vorige regel.</span><span class="sxs-lookup"><span data-stu-id="99168-495">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="99168-496">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-496">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="99168-497">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="99168-497">ShellBackwardWord</span></span>

<span data-ttu-id="99168-498">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="99168-498">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="99168-499">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="99168-499">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="99168-500">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-500">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="99168-501">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="99168-501">ShellForwardWord</span></span>

<span data-ttu-id="99168-502">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="99168-502">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="99168-503">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="99168-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="99168-504">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-504">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="99168-505">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="99168-505">ShellNextWord</span></span>

<span data-ttu-id="99168-506">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="99168-506">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="99168-507">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="99168-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="99168-508">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-508">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="99168-509">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="99168-509">ViBackwardWord</span></span>

<span data-ttu-id="99168-510">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="99168-510">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="99168-511">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="99168-511">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="99168-512">VI-opdracht modus: `<b>`</span><span class="sxs-lookup"><span data-stu-id="99168-512">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="99168-513">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="99168-513">ViEndOfGlob</span></span>

<span data-ttu-id="99168-514">Verplaatst de cursor naar het einde van het woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="99168-514">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="99168-515">VI-opdracht modus: `<E>`</span><span class="sxs-lookup"><span data-stu-id="99168-515">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="99168-516">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="99168-516">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="99168-517">Wordt verplaatst naar het einde van het vorige woord, waarbij alleen witruimte wordt gebruikt als woord als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="99168-517">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="99168-518">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-518">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="99168-519">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="99168-519">ViGotoBrace</span></span>

<span data-ttu-id="99168-520">Vergelijkbaar met GotoBrace, maar is in plaats van op tokens gebaseerd.</span><span class="sxs-lookup"><span data-stu-id="99168-520">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="99168-521">VI-opdracht modus: `<%>`</span><span class="sxs-lookup"><span data-stu-id="99168-521">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="99168-522">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="99168-522">ViNextGlob</span></span>

<span data-ttu-id="99168-523">Verplaatst naar het volgende woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="99168-523">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="99168-524">VI-opdracht modus: `<W>`</span><span class="sxs-lookup"><span data-stu-id="99168-524">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="99168-525">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="99168-525">ViNextWord</span></span>

<span data-ttu-id="99168-526">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="99168-526">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="99168-527">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="99168-527">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="99168-528">VI-opdracht modus: `<w>`</span><span class="sxs-lookup"><span data-stu-id="99168-528">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="99168-529">Geschiedenis functies</span><span class="sxs-lookup"><span data-stu-id="99168-529">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="99168-530">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="99168-530">BeginningOfHistory</span></span>

<span data-ttu-id="99168-531">Hiermee gaat u naar het eerste item in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="99168-531">Move to the first item in the history.</span></span>

- <span data-ttu-id="99168-532">Emacs: `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="99168-532">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="99168-533">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="99168-533">ClearHistory</span></span>

<span data-ttu-id="99168-534">Hiermee wist u de geschiedenis in PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="99168-534">Clears history in PSReadLine.</span></span> <span data-ttu-id="99168-535">Dit heeft geen invloed op de Power shell-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="99168-535">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="99168-536">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="99168-536">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="99168-537">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="99168-537">EndOfHistory</span></span>

<span data-ttu-id="99168-538">Hiermee gaat u naar het laatste item (de huidige invoer) in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="99168-538">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="99168-539">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="99168-539">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="99168-540">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="99168-540">ForwardSearchHistory</span></span>

<span data-ttu-id="99168-541">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="99168-541">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="99168-542">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="99168-542">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="99168-543">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="99168-543">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="99168-544">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="99168-544">HistorySearchBackward</span></span>

<span data-ttu-id="99168-545">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-545">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="99168-546">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="99168-546">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="99168-547">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="99168-547">HistorySearchForward</span></span>

<span data-ttu-id="99168-548">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-548">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="99168-549">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="99168-549">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="99168-550">NextHistory</span><span class="sxs-lookup"><span data-stu-id="99168-550">NextHistory</span></span>

<span data-ttu-id="99168-551">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="99168-551">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="99168-552">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-552">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="99168-553">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="99168-553">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="99168-554">VI Invoeg modus: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-554">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="99168-555">VI-opdracht modus: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="99168-555">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="99168-556">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="99168-556">PreviousHistory</span></span>

<span data-ttu-id="99168-557">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="99168-557">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="99168-558">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-558">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="99168-559">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="99168-559">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="99168-560">VI Invoeg modus: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-560">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="99168-561">VI-opdracht modus: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="99168-561">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="99168-562">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="99168-562">ReverseSearchHistory</span></span>

<span data-ttu-id="99168-563">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="99168-563">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="99168-564">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="99168-564">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="99168-565">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="99168-565">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="99168-566">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="99168-566">ViSearchHistoryBackward</span></span>

<span data-ttu-id="99168-567">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="99168-567">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="99168-568">VI Invoeg modus: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="99168-568">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="99168-569">VI-opdracht modus: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="99168-569">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="99168-570">Voltooiings functies</span><span class="sxs-lookup"><span data-stu-id="99168-570">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="99168-571">Voltooid</span><span class="sxs-lookup"><span data-stu-id="99168-571">Complete</span></span>

<span data-ttu-id="99168-572">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-572">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="99168-573">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="99168-573">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="99168-574">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="99168-574">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="99168-575">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="99168-575">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="99168-576">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="99168-576">MenuComplete</span></span>

<span data-ttu-id="99168-577">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-577">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="99168-578">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="99168-578">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="99168-579">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="99168-579">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="99168-580">Cmd `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="99168-580">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="99168-581">Emacs: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="99168-581">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="99168-582">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="99168-582">PossibleCompletions</span></span>

<span data-ttu-id="99168-583">De lijst met mogelijke aanvullingen weer geven.</span><span class="sxs-lookup"><span data-stu-id="99168-583">Display the list of possible completions.</span></span>

- <span data-ttu-id="99168-584">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="99168-584">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="99168-585">VI Invoeg modus: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="99168-585">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="99168-586">VI-opdracht modus: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="99168-586">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="99168-587">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="99168-587">TabCompleteNext</span></span>

<span data-ttu-id="99168-588">Poging om de tekst rond de cursor te volt ooien met de volgende beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="99168-588">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="99168-589">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="99168-589">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="99168-590">VI-opdracht modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="99168-590">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="99168-591">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="99168-591">TabCompletePrevious</span></span>

<span data-ttu-id="99168-592">Poging om de tekst rond de cursor te volt ooien met de vorige beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="99168-592">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="99168-593">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="99168-593">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="99168-594">VI-opdracht modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="99168-594">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="99168-595">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="99168-595">ViTabCompleteNext</span></span>

<span data-ttu-id="99168-596">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompleteNext aan.</span><span class="sxs-lookup"><span data-stu-id="99168-596">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="99168-597">VI Invoeg modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="99168-597">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="99168-598">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="99168-598">ViTabCompletePrevious</span></span>

<span data-ttu-id="99168-599">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompletePrevious aan.</span><span class="sxs-lookup"><span data-stu-id="99168-599">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="99168-600">VI Invoeg modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="99168-600">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="99168-601">Diverse functies</span><span class="sxs-lookup"><span data-stu-id="99168-601">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="99168-602">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="99168-602">CaptureScreen</span></span>

<span data-ttu-id="99168-603">Interactieve scherm opname starten-pijl-omhoog/omlaag Selecteer regels en voer de geselecteerde tekst als tekst en HTML naar het klem bord kopiëren.</span><span class="sxs-lookup"><span data-stu-id="99168-603">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="99168-604">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-604">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="99168-605">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="99168-605">ClearScreen</span></span>

<span data-ttu-id="99168-606">Schakel het scherm uit en teken de huidige regel boven aan het scherm.</span><span class="sxs-lookup"><span data-stu-id="99168-606">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="99168-607">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="99168-607">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="99168-608">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="99168-608">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="99168-609">VI Invoeg modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="99168-609">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="99168-610">VI-opdracht modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="99168-610">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="99168-611">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="99168-611">DigitArgument</span></span>

<span data-ttu-id="99168-612">Start een nieuw cijfer argument om door te geven aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="99168-612">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="99168-613">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="99168-613">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="99168-614">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="99168-614">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="99168-615">VI-opdracht modus: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="99168-615">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="99168-616">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="99168-616">InvokePrompt</span></span>

<span data-ttu-id="99168-617">Hiermee wordt de huidige prompt gewist en wordt de functie Prompt aangeroepen om de prompt opnieuw weer te geven.</span><span class="sxs-lookup"><span data-stu-id="99168-617">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="99168-618">Dit is handig voor aangepaste sleutel afhandelingen die de status wijzigen, bijvoorbeeld de huidige map wijzigen.</span><span class="sxs-lookup"><span data-stu-id="99168-618">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="99168-619">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-619">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="99168-620">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="99168-620">ScrollDisplayDown</span></span>

<span data-ttu-id="99168-621">De weer gave één scherm omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="99168-621">Scroll the display down one screen.</span></span>

- <span data-ttu-id="99168-622">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="99168-622">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="99168-623">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="99168-623">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="99168-624">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="99168-624">ScrollDisplayDownLine</span></span>

<span data-ttu-id="99168-625">De weer gave één regel omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="99168-625">Scroll the display down one line.</span></span>

- <span data-ttu-id="99168-626">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="99168-626">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="99168-627">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="99168-627">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="99168-628">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="99168-628">ScrollDisplayToCursor</span></span>

<span data-ttu-id="99168-629">Schuif de weer gave naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-629">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="99168-630">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="99168-630">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="99168-631">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="99168-631">ScrollDisplayTop</span></span>

<span data-ttu-id="99168-632">Schuif de weer gave naar boven.</span><span class="sxs-lookup"><span data-stu-id="99168-632">Scroll the display to the top.</span></span>

- <span data-ttu-id="99168-633">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="99168-633">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="99168-634">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="99168-634">ScrollDisplayUp</span></span>

<span data-ttu-id="99168-635">Schuif de weer gave één scherm omhoog.</span><span class="sxs-lookup"><span data-stu-id="99168-635">Scroll the display up one screen.</span></span>

- <span data-ttu-id="99168-636">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="99168-636">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="99168-637">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="99168-637">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="99168-638">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="99168-638">ScrollDisplayUpLine</span></span>

<span data-ttu-id="99168-639">De weer gave één regel omhoog schuiven.</span><span class="sxs-lookup"><span data-stu-id="99168-639">Scroll the display up one line.</span></span>

- <span data-ttu-id="99168-640">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="99168-640">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="99168-641">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="99168-641">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="99168-642">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="99168-642">SelfInsert</span></span>

<span data-ttu-id="99168-643">Voeg de sleutel in.</span><span class="sxs-lookup"><span data-stu-id="99168-643">Insert the key.</span></span>

- <span data-ttu-id="99168-644">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-644">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="99168-645">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="99168-645">ShowKeyBindings</span></span>

<span data-ttu-id="99168-646">Alle gebonden sleutels weer geven.</span><span class="sxs-lookup"><span data-stu-id="99168-646">Show all bound keys.</span></span>

- <span data-ttu-id="99168-647">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="99168-647">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="99168-648">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="99168-648">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="99168-649">VI Invoeg modus: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="99168-649">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="99168-650">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="99168-650">ViCommandMode</span></span>

<span data-ttu-id="99168-651">Schakel de huidige bedrijfs modus uit van Vi-Insert naar de VI-opdracht.</span><span class="sxs-lookup"><span data-stu-id="99168-651">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="99168-652">VI Invoeg modus: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="99168-652">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="99168-653">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="99168-653">ViDigitArgumentInChord</span></span>

<span data-ttu-id="99168-654">Start een nieuw cijfer argument om door te geven aan andere functies in een van de koorden van VI.</span><span class="sxs-lookup"><span data-stu-id="99168-654">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="99168-655">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-655">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="99168-656">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="99168-656">ViEditVisually</span></span>

<span data-ttu-id="99168-657">Bewerk de opdracht regel in een tekst editor die is opgegeven door $env: EDITOR of $env: VISUAL.</span><span class="sxs-lookup"><span data-stu-id="99168-657">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="99168-658">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="99168-658">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="99168-659">VI-opdracht modus: `<v>`</span><span class="sxs-lookup"><span data-stu-id="99168-659">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="99168-660">ViExit</span><span class="sxs-lookup"><span data-stu-id="99168-660">ViExit</span></span>

<span data-ttu-id="99168-661">Hiermee wordt de shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="99168-661">Exits the shell.</span></span>

- <span data-ttu-id="99168-662">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-662">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="99168-663">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="99168-663">ViInsertMode</span></span>

<span data-ttu-id="99168-664">Schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="99168-664">Switch to Insert mode.</span></span>

- <span data-ttu-id="99168-665">VI-opdracht modus: `<i>`</span><span class="sxs-lookup"><span data-stu-id="99168-665">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="99168-666">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="99168-666">WhatIsKey</span></span>

<span data-ttu-id="99168-667">Lees een sleutel en vertel me wat de sleutel is gebonden.</span><span class="sxs-lookup"><span data-stu-id="99168-667">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="99168-668">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="99168-668">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="99168-669">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="99168-669">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="99168-670">Selectie functies</span><span class="sxs-lookup"><span data-stu-id="99168-670">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="99168-671">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="99168-671">ExchangePointAndMark</span></span>

<span data-ttu-id="99168-672">De cursor wordt op de locatie van het merk geplaatst en het vinkje wordt verplaatst naar de locatie van de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-672">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="99168-673">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="99168-673">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="99168-674">SelectAll aanroepen</span><span class="sxs-lookup"><span data-stu-id="99168-674">SelectAll</span></span>

<span data-ttu-id="99168-675">Selecteer de volledige regel.</span><span class="sxs-lookup"><span data-stu-id="99168-675">Select the entire line.</span></span>

- <span data-ttu-id="99168-676">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="99168-676">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="99168-677">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="99168-677">SelectBackwardChar</span></span>

<span data-ttu-id="99168-678">Pas de huidige selectie aan om het vorige teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="99168-678">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="99168-679">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-679">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="99168-680">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-680">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="99168-681">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="99168-681">SelectBackwardsLine</span></span>

<span data-ttu-id="99168-682">Pas de huidige selectie aan de cursor toe aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="99168-682">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="99168-683">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="99168-683">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="99168-684">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="99168-684">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="99168-685">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="99168-685">SelectBackwardWord</span></span>

<span data-ttu-id="99168-686">Pas de huidige selectie aan om het vorige woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="99168-686">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="99168-687">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-687">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="99168-688">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="99168-688">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="99168-689">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="99168-689">SelectForwardChar</span></span>

<span data-ttu-id="99168-690">Pas de huidige selectie aan om het volgende teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="99168-690">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="99168-691">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-691">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="99168-692">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-692">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="99168-693">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="99168-693">SelectForwardWord</span></span>

<span data-ttu-id="99168-694">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="99168-694">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="99168-695">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="99168-695">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="99168-696">SelectLine</span><span class="sxs-lookup"><span data-stu-id="99168-696">SelectLine</span></span>

<span data-ttu-id="99168-697">Pas de huidige selectie aan de cursor toe aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="99168-697">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="99168-698">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="99168-698">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="99168-699">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="99168-699">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="99168-700">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="99168-700">SelectNextWord</span></span>

<span data-ttu-id="99168-701">Pas de huidige selectie aan om het volgende woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="99168-701">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="99168-702">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="99168-702">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="99168-703">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="99168-703">SelectShellBackwardWord</span></span>

<span data-ttu-id="99168-704">Pas de huidige selectie aan om het vorige woord op te maken met behulp van ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="99168-704">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="99168-705">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-705">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="99168-706">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="99168-706">SelectShellForwardWord</span></span>

<span data-ttu-id="99168-707">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="99168-707">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="99168-708">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-708">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="99168-709">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="99168-709">SelectShellNextWord</span></span>

<span data-ttu-id="99168-710">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="99168-710">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="99168-711">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="99168-711">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="99168-712">SetMark</span><span class="sxs-lookup"><span data-stu-id="99168-712">SetMark</span></span>

<span data-ttu-id="99168-713">De huidige locatie van de cursor markeren voor gebruik in een volgende bewerkings opdracht.</span><span class="sxs-lookup"><span data-stu-id="99168-713">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="99168-714">Emacs: `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="99168-714">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="99168-715">Zoek functies</span><span class="sxs-lookup"><span data-stu-id="99168-715">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="99168-716">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="99168-716">CharacterSearch</span></span>

<span data-ttu-id="99168-717">Lees een teken en zoek voorwaarts naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="99168-717">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="99168-718">Als er een argument is opgegeven, zoekt u voorwaarts (of achterwaarts als negatieve) voor het ne voorval.</span><span class="sxs-lookup"><span data-stu-id="99168-718">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="99168-719">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="99168-719">Cmd: `<F3>`</span></span>
- <span data-ttu-id="99168-720">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="99168-720">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="99168-721">VI Invoeg modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="99168-721">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="99168-722">VI-opdracht modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="99168-722">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="99168-723">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="99168-723">CharacterSearchBackward</span></span>

<span data-ttu-id="99168-724">Lees een teken en zoek terug naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="99168-724">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="99168-725">Als er een argument is opgegeven, zoekt u terug (of als dit negatief is) voor het ne exemplaar.</span><span class="sxs-lookup"><span data-stu-id="99168-725">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="99168-726">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="99168-726">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="99168-727">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="99168-727">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="99168-728">VI Invoeg modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="99168-728">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="99168-729">VI-opdracht modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="99168-729">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="99168-730">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="99168-730">RepeatLastCharSearch</span></span>

<span data-ttu-id="99168-731">De laatst opgenomen zoek opdracht herhalen.</span><span class="sxs-lookup"><span data-stu-id="99168-731">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="99168-732">VI-opdracht modus: `<;>`</span><span class="sxs-lookup"><span data-stu-id="99168-732">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="99168-733">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="99168-733">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="99168-734">De laatst opgenomen zoek opdracht herhalen, maar in tegenovergestelde richting.</span><span class="sxs-lookup"><span data-stu-id="99168-734">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="99168-735">VI-opdracht modus: `<,>`</span><span class="sxs-lookup"><span data-stu-id="99168-735">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="99168-736">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="99168-736">RepeatSearch</span></span>

<span data-ttu-id="99168-737">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="99168-737">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="99168-738">VI-opdracht modus: `<n>`</span><span class="sxs-lookup"><span data-stu-id="99168-738">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="99168-739">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="99168-739">RepeatSearchBackward</span></span>

<span data-ttu-id="99168-740">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="99168-740">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="99168-741">VI-opdracht modus: `<N>`</span><span class="sxs-lookup"><span data-stu-id="99168-741">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="99168-742">SearchChar</span><span class="sxs-lookup"><span data-stu-id="99168-742">SearchChar</span></span>

<span data-ttu-id="99168-743">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="99168-743">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="99168-744">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="99168-744">This is for 't' functionality.</span></span>

- <span data-ttu-id="99168-745">VI-opdracht modus: `<f>`</span><span class="sxs-lookup"><span data-stu-id="99168-745">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="99168-746">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="99168-746">SearchCharBackward</span></span>

<span data-ttu-id="99168-747">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="99168-747">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="99168-748">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="99168-748">This is for 'T' functionality.</span></span>

- <span data-ttu-id="99168-749">VI-opdracht modus: `<F>`</span><span class="sxs-lookup"><span data-stu-id="99168-749">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="99168-750">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="99168-750">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="99168-751">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="99168-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="99168-752">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="99168-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="99168-753">VI-opdracht modus: `<T>`</span><span class="sxs-lookup"><span data-stu-id="99168-753">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="99168-754">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="99168-754">SearchCharWithBackoff</span></span>

<span data-ttu-id="99168-755">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="99168-755">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="99168-756">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="99168-756">This is for 't' functionality.</span></span>

- <span data-ttu-id="99168-757">VI-opdracht modus: `<t>`</span><span class="sxs-lookup"><span data-stu-id="99168-757">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="99168-758">SearchForward</span><span class="sxs-lookup"><span data-stu-id="99168-758">SearchForward</span></span>

<span data-ttu-id="99168-759">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="99168-759">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="99168-760">VI Invoeg modus: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="99168-760">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="99168-761">VI-opdracht modus: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="99168-761">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="99168-762">Aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="99168-762">Custom Key Bindings</span></span>

<span data-ttu-id="99168-763">PSReadLine ondersteunt aangepaste sleutel bindingen met behulp van de-cmdlet `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="99168-763">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="99168-764">De meeste aangepaste sleutel bindingen roepen een van de bovenstaande functies aan, bijvoorbeeld</span><span class="sxs-lookup"><span data-stu-id="99168-764">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="99168-765">U kunt een script Block binden aan een sleutel.</span><span class="sxs-lookup"><span data-stu-id="99168-765">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="99168-766">Het script Block kan veel wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="99168-766">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="99168-767">Enkele handige voor beelden zijn</span><span class="sxs-lookup"><span data-stu-id="99168-767">Some useful examples include</span></span>

- <span data-ttu-id="99168-768">de opdracht regel bewerken</span><span class="sxs-lookup"><span data-stu-id="99168-768">edit the command line</span></span>
- <span data-ttu-id="99168-769">een nieuw venster openen (bijvoorbeeld Help)</span><span class="sxs-lookup"><span data-stu-id="99168-769">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="99168-770">mappen wijzigen zonder de opdracht regel te wijzigen</span><span class="sxs-lookup"><span data-stu-id="99168-770">change directories without changing the command line</span></span>

<span data-ttu-id="99168-771">De script Block ontvangt twee argumenten:</span><span class="sxs-lookup"><span data-stu-id="99168-771">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="99168-772">`$key` -Een **[ConsoleKeyInfo]** -object dat de sleutel is die de aangepaste binding heeft geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="99168-772">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="99168-773">Als u dezelfde script Block aan meerdere sleutels koppelt en verschillende acties moet uitvoeren, afhankelijk van de sleutel, kunt u $key controleren.</span><span class="sxs-lookup"><span data-stu-id="99168-773">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="99168-774">Veel aangepaste bindingen negeren dit argument.</span><span class="sxs-lookup"><span data-stu-id="99168-774">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="99168-775">`$arg` -Een wille keurig argument.</span><span class="sxs-lookup"><span data-stu-id="99168-775">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="99168-776">Meestal is dit een geheel getal dat de gebruiker door gegeven van de sleutel bindingen DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="99168-776">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="99168-777">Als uw binding geen argumenten accepteert, is het redelijk om dit argument te negeren.</span><span class="sxs-lookup"><span data-stu-id="99168-777">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="99168-778">Laten we een voor beeld bekijken waarmee een opdracht regel wordt toegevoegd aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="99168-778">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="99168-779">Dit is handig wanneer u ervoor hebt gekozen om iets te doen, maar niet opnieuw moet invoeren van de opdracht regel die u al hebt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="99168-779">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="99168-780">U kunt veel meer voor beelden bekijken in het bestand `SamplePSReadLineProfile.ps1` dat is geïnstalleerd in de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="99168-780">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="99168-781">De meeste sleutel bindingen gebruiken enkele hulp functies voor het bewerken van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="99168-781">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="99168-782">Deze Api's worden beschreven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="99168-782">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="99168-783">Api's voor de ondersteuning van aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="99168-783">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="99168-784">De volgende functies zijn openbaar in micro soft. Power shell. PSConsoleReadLine, maar kunnen niet rechtstreeks aan een sleutel worden gebonden.</span><span class="sxs-lookup"><span data-stu-id="99168-784">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="99168-785">De meeste zijn handig in aangepaste sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="99168-785">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="99168-786">Een opdracht regel toevoegen aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="99168-786">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="99168-787">Wis de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="99168-787">Clear the kill-ring.</span></span>  <span data-ttu-id="99168-788">Dit wordt meestal gebruikt voor het testen.</span><span class="sxs-lookup"><span data-stu-id="99168-788">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="99168-789">Verwijder de lengte tekens uit het begin.</span><span class="sxs-lookup"><span data-stu-id="99168-789">Delete length characters from start.</span></span>  <span data-ttu-id="99168-790">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="99168-790">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="99168-791">Voer de actie opname uit op basis van de voor keuren van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="99168-791">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="99168-792">Deze twee functies halen nuttige informatie op over de huidige status van de invoer buffer.</span><span class="sxs-lookup"><span data-stu-id="99168-792">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="99168-793">De eerste wordt vaak gebruikt voor eenvoudige gevallen.</span><span class="sxs-lookup"><span data-stu-id="99168-793">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="99168-794">De tweede wordt gebruikt als uw binding iets geavanceerder gaat met de AST.</span><span class="sxs-lookup"><span data-stu-id="99168-794">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="99168-795">Deze functie wordt gebruikt door Get-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="99168-795">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="99168-796">Deze functie wordt gebruikt door Get-PSReadLineOption en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="99168-796">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="99168-797">Als er niets is geselecteerd op de opdracht regel, wordt-1 geretourneerd in zowel start als length.</span><span class="sxs-lookup"><span data-stu-id="99168-797">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="99168-798">Als er een selectie is op de opdracht regel, worden het begin en de lengte van de selectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="99168-798">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="99168-799">Voeg een teken of teken reeks toe aan de cursor.</span><span class="sxs-lookup"><span data-stu-id="99168-799">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="99168-800">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="99168-800">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="99168-801">Dit is het belangrijkste ingangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="99168-801">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="99168-802">Er wordt geen recursie ondersteund, dus is niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="99168-802">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="99168-803">Deze functie wordt gebruikt door Remove-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="99168-803">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="99168-804">Vervang een deel van de invoer.</span><span class="sxs-lookup"><span data-stu-id="99168-804">Replace some of the input.</span></span> <span data-ttu-id="99168-805">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="99168-805">This operation supports undo/redo.</span></span> <span data-ttu-id="99168-806">U kunt het beste verwijderen gevolgd door INSERT, omdat het wordt beschouwd als één actie voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="99168-806">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="99168-807">De cursor verplaatsen naar de opgegeven verschuiving.</span><span class="sxs-lookup"><span data-stu-id="99168-807">Move the cursor to the given offset.</span></span> <span data-ttu-id="99168-808">Cursor verplaatsing wordt niet bijgehouden voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="99168-808">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="99168-809">Deze functie is een helper-methode die wordt gebruikt door de cmdlet Set-PSReadLineOption, maar kan handig zijn voor een aangepaste sleutel binding die tijdelijk een instelling wil wijzigen.</span><span class="sxs-lookup"><span data-stu-id="99168-809">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="99168-810">Deze Help methode wordt gebruikt voor aangepaste bindingen die voldoen aan DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="99168-810">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="99168-811">Een typische aanroep ziet eruit als</span><span class="sxs-lookup"><span data-stu-id="99168-811">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="99168-812">OPMERKING</span><span class="sxs-lookup"><span data-stu-id="99168-812">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="99168-813">COMPATIBILITEIT MET POWER SHELL</span><span class="sxs-lookup"><span data-stu-id="99168-813">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="99168-814">PSReadLine vereist Power Shell 3,0, of nieuwer, en de console-host.</span><span class="sxs-lookup"><span data-stu-id="99168-814">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="99168-815">Het werkt niet in Power shell ISE.</span><span class="sxs-lookup"><span data-stu-id="99168-815">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="99168-816">Het werkt in de console van Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="99168-816">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="99168-817">OPDRACHT GESCHIEDENIS</span><span class="sxs-lookup"><span data-stu-id="99168-817">COMMAND HISTORY</span></span>

<span data-ttu-id="99168-818">PSReadLine onderhoudt een geschiedenis bestand met alle opdrachten en gegevens die u hebt ingevoerd op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="99168-818">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="99168-819">Dit kan gevoelige gegevens bevatten, inclusief wacht woorden.</span><span class="sxs-lookup"><span data-stu-id="99168-819">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="99168-820">Als u bijvoorbeeld de cmdlet gebruikt, `ConvertTo-SecureString` wordt het wacht woord in het geschiedenis bestand vastgelegd als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="99168-820">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="99168-821">De geschiedenis bestanden zijn een bestand met de naam `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="99168-821">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="99168-822">Op Windows-systemen wordt het geschiedenis bestand opgeslagen op `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="99168-822">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="99168-823">FEEDBACK & bijdragen aan PSReadLine</span><span class="sxs-lookup"><span data-stu-id="99168-823">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="99168-824">PSReadLine op GitHub</span><span class="sxs-lookup"><span data-stu-id="99168-824">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="99168-825">U kunt een pull-aanvraag verzenden of feedback verzenden op de pagina GitHub.</span><span class="sxs-lookup"><span data-stu-id="99168-825">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="99168-826">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="99168-826">SEE ALSO</span></span>

<span data-ttu-id="99168-827">PSReadLine wordt sterk beïnvloed door de GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="99168-827">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
