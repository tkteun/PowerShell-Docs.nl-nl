---
description: PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over PSReadLine
ms.openlocfilehash: 5b59ffcdfb35c2aa10f8e0caf3a3b365c5bcf93e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252852"
---
# <a name="psreadline"></a><span data-ttu-id="aefb1-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="aefb1-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="aefb1-106">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aefb1-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="aefb1-107">PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="aefb1-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="aefb1-108">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aefb1-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="aefb1-109">PSReadLine 2,0 biedt een krachtige opdracht regel voor het bewerken van de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="aefb1-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="aefb1-110">De oplossing biedt het volgende:</span><span class="sxs-lookup"><span data-stu-id="aefb1-110">It provides:</span></span>

- <span data-ttu-id="aefb1-111">Syntaxis kleur van de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="aefb1-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="aefb1-112">Een visuele indicatie van syntaxis fouten</span><span class="sxs-lookup"><span data-stu-id="aefb1-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="aefb1-113">Een betere ervaring met meerdere regels (zowel bewerkingen als geschiedenis)</span><span class="sxs-lookup"><span data-stu-id="aefb1-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="aefb1-114">Aanpas bare sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="aefb1-114">Customizable key bindings</span></span>
- <span data-ttu-id="aefb1-115">Cmd-en emacs-modi</span><span class="sxs-lookup"><span data-stu-id="aefb1-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="aefb1-116">Veel configuratie opties</span><span class="sxs-lookup"><span data-stu-id="aefb1-116">Many configuration options</span></span>
- <span data-ttu-id="aefb1-117">Bash-stijl voltooiing (optioneel in CMD-modus, standaard in Emacs-modus)</span><span class="sxs-lookup"><span data-stu-id="aefb1-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="aefb1-118">Emacs Yank/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="aefb1-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="aefb1-119">"Woord" verplaatsing en afsluiten op basis van Power shell-tokens</span><span class="sxs-lookup"><span data-stu-id="aefb1-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="aefb1-120">De volgende functies zijn beschikbaar in de klasse **[micro soft. Power shell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="aefb1-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

> [!NOTE]
> <span data-ttu-id="aefb1-121">Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-121">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="aefb1-122">Op dit moment werkt PSReadLine niet goed met scherm lezers.</span><span class="sxs-lookup"><span data-stu-id="aefb1-122">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="aefb1-123">De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="aefb1-123">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="aefb1-124">U kunt de module hand matig laden, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="aefb1-124">You can manually load the module if necessary.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="aefb1-125">Basis bewerkings functies</span><span class="sxs-lookup"><span data-stu-id="aefb1-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="aefb1-126">Afbreken</span><span class="sxs-lookup"><span data-stu-id="aefb1-126">Abort</span></span>

<span data-ttu-id="aefb1-127">De huidige actie afbreken, bijvoorbeeld een incrementele geschiedenis zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="aefb1-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="aefb1-128">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="aefb1-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="aefb1-129">AcceptAndGetNext</span></span>

<span data-ttu-id="aefb1-130">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-130">Attempt to execute the current input.</span></span> <span data-ttu-id="aefb1-131">Als deze kan worden uitgevoerd (zoals AcceptLine), kunt u het volgende item uit de geschiedenis intrekken de volgende keer dat ReadLine wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="aefb1-132">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="aefb1-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-133">AcceptLine</span></span>

<span data-ttu-id="aefb1-134">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-134">Attempt to execute the current input.</span></span> <span data-ttu-id="aefb1-135">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="aefb1-136">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="aefb1-137">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="aefb1-138">VI Invoeg modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="aefb1-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-139">AddLine</span></span>

<span data-ttu-id="aefb1-140">De vervolg prompt wordt weer gegeven op de volgende regel en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="aefb1-141">Dit is handig om invoer in meerdere regels als één opdracht in te voeren, zelfs wanneer één regel volledig wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="aefb1-142">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="aefb1-143">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="aefb1-144">VI Invoeg modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="aefb1-145">VI-opdracht modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="aefb1-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-146">BackwardDeleteChar</span></span>

<span data-ttu-id="aefb1-147">Verwijder het teken voor de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="aefb1-148">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="aefb1-149">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="aefb1-150">VI Invoeg modus: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="aefb1-151">VI-opdracht modus: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="aefb1-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-152">BackwardDeleteLine</span></span>

<span data-ttu-id="aefb1-153">Net als BackwardKillLine: verwijdert tekst van het punt naar het begin van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="aefb1-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="aefb1-154">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="aefb1-155">VI Invoeg modus: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="aefb1-156">VI-opdracht modus: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="aefb1-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-157">BackwardDeleteWord</span></span>

<span data-ttu-id="aefb1-158">Hiermee verwijdert u het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-158">Deletes the previous word.</span></span>

- <span data-ttu-id="aefb1-159">VI-opdracht modus: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="aefb1-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-160">BackwardKillLine</span></span>

<span data-ttu-id="aefb1-161">De invoer van het begin van de invoer wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="aefb1-162">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="aefb1-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="aefb1-163">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="aefb1-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-164">BackwardKillWord</span></span>

<span data-ttu-id="aefb1-165">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="aefb1-166">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="aefb1-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="aefb1-167">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="aefb1-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="aefb1-168">Cmd `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-168">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="aefb1-169">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="aefb1-170">VI Invoeg modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="aefb1-171">VI-opdracht modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="aefb1-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-172">CancelLine</span></span>

<span data-ttu-id="aefb1-173">De huidige invoer annuleren, waardoor de invoer op het scherm wordt weer gegeven, maar terugkeert naar de host, zodat de prompt opnieuw wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="aefb1-174">VI Invoeg modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="aefb1-175">VI-opdracht modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="aefb1-176">Kopiëren</span><span class="sxs-lookup"><span data-stu-id="aefb1-176">Copy</span></span>

<span data-ttu-id="aefb1-177">Kopieer de geselecteerde regio naar het klem bord van het systeem.</span><span class="sxs-lookup"><span data-stu-id="aefb1-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="aefb1-178">Als er geen regio is geselecteerd, kopieert u de hele regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="aefb1-179">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="aefb1-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-180">CopyOrCancelLine</span></span>

<span data-ttu-id="aefb1-181">Als tekst is geselecteerd, kopieert u deze naar het klem bord. anders annuleert u de regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="aefb1-182">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="aefb1-183">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="aefb1-184">Knippen</span><span class="sxs-lookup"><span data-stu-id="aefb1-184">Cut</span></span>

<span data-ttu-id="aefb1-185">Geselecteerde regio verwijderen Verwijderde tekst in het systeem Klembord plaatsen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="aefb1-186">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="aefb1-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-187">DeleteChar</span></span>

<span data-ttu-id="aefb1-188">Verwijder het teken onder de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="aefb1-189">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="aefb1-190">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="aefb1-191">VI Invoeg modus: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="aefb1-192">VI-opdracht modus: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="aefb1-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="aefb1-193">DeleteCharOrExit</span></span>

<span data-ttu-id="aefb1-194">Verwijder het teken onder de cursor of als de regel leeg is, sluit u het proces.</span><span class="sxs-lookup"><span data-stu-id="aefb1-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="aefb1-195">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="aefb1-196">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-196">DeleteEndOfWord</span></span>

<span data-ttu-id="aefb1-197">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-197">Delete to the end of the word.</span></span>

- <span data-ttu-id="aefb1-198">VI-opdracht modus: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-198">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="aefb1-199">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-199">DeleteLine</span></span>

<span data-ttu-id="aefb1-200">Hiermee verwijdert u de huidige regel, waarbij u ongedaan maken inschakelt.</span><span class="sxs-lookup"><span data-stu-id="aefb1-200">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="aefb1-201">VI-opdracht modus: `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-201">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="aefb1-202">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-202">DeleteLineToFirstChar</span></span>

<span data-ttu-id="aefb1-203">Hiermee wordt tekst van de cursor verwijderd naar het eerste niet-lege teken van de regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-203">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="aefb1-204">VI-opdracht modus: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-204">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="aefb1-205">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="aefb1-205">DeleteToEnd</span></span>

<span data-ttu-id="aefb1-206">Verwijderen tot aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-206">Delete to the end of the line.</span></span>

- <span data-ttu-id="aefb1-207">VI-opdracht modus: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-207">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="aefb1-208">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-208">DeleteWord</span></span>

<span data-ttu-id="aefb1-209">Verwijder het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-209">Delete the next word.</span></span>

- <span data-ttu-id="aefb1-210">VI-opdracht modus: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-210">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="aefb1-211">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-211">ForwardDeleteLine</span></span>

<span data-ttu-id="aefb1-212">Net als ForwardKillLine: verwijdert tekst van het punt naar het einde van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="aefb1-212">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="aefb1-213">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-213">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="aefb1-214">VI Invoeg modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-214">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="aefb1-215">VI-opdracht modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-215">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="aefb1-216">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="aefb1-216">InsertLineAbove</span></span>

<span data-ttu-id="aefb1-217">Er wordt een nieuwe lege regel gemaakt op de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="aefb1-217">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="aefb1-218">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="aefb1-219">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-219">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="aefb1-220">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="aefb1-220">InsertLineBelow</span></span>

<span data-ttu-id="aefb1-221">Er wordt een nieuwe lege regel gemaakt onder de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="aefb1-221">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="aefb1-222">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-222">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="aefb1-223">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-223">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="aefb1-224">InvertCase</span><span class="sxs-lookup"><span data-stu-id="aefb1-224">InvertCase</span></span>

<span data-ttu-id="aefb1-225">Het hoofdletter gebruik van het huidige teken omkeren en verplaatsen naar het volgende.</span><span class="sxs-lookup"><span data-stu-id="aefb1-225">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="aefb1-226">VI-opdracht modus: `<~>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-226">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="aefb1-227">KillLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-227">KillLine</span></span>

<span data-ttu-id="aefb1-228">De invoer wissen van de cursor tot het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-228">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="aefb1-229">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="aefb1-229">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="aefb1-230">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-230">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="aefb1-231">KillRegion</span><span class="sxs-lookup"><span data-stu-id="aefb1-231">KillRegion</span></span>

<span data-ttu-id="aefb1-232">Beëindig de tekst tussen de cursor en de markering.</span><span class="sxs-lookup"><span data-stu-id="aefb1-232">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="aefb1-233">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-233">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="aefb1-234">KillWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-234">KillWord</span></span>

<span data-ttu-id="aefb1-235">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-235">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="aefb1-236">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-236">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="aefb1-237">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="aefb1-237">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="aefb1-238">Cmd `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-238">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="aefb1-239">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-239">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="aefb1-240">VI Invoeg modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-240">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="aefb1-241">VI-opdracht modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-241">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="aefb1-242">Plakken</span><span class="sxs-lookup"><span data-stu-id="aefb1-242">Paste</span></span>

<span data-ttu-id="aefb1-243">Tekst van het klem bord van het systeem plakken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-243">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="aefb1-244">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-244">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="aefb1-245">VI Invoeg modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-245">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="aefb1-246">VI-opdracht modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-246">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aefb1-247">Wanneer u de functie **Paste** gebruikt, wordt de volledige inhoud van de Klembord buffer geplakt in de invoer buffer van PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="aefb1-247">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="aefb1-248">De invoer buffer wordt vervolgens door gegeven aan de Power shell-parser.</span><span class="sxs-lookup"><span data-stu-id="aefb1-248">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="aefb1-249">Invoer die met de **rechter muisknop op** de plak methode van de console toepassing wordt geplakt, wordt met één teken per keer naar de invoer buffer gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-249">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="aefb1-250">De invoer buffer wordt door gegeven aan de parser wanneer een teken voor een nieuwe regel wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-250">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="aefb1-251">Daarom wordt de invoer één regel tegelijk geparseerd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-251">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="aefb1-252">Het verschil tussen plak methoden resulteert in een ander uitvoerings gedrag.</span><span class="sxs-lookup"><span data-stu-id="aefb1-252">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="aefb1-253">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="aefb1-253">PasteAfter</span></span>

<span data-ttu-id="aefb1-254">Plak het klem bord na de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-254">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="aefb1-255">VI-opdracht modus: `<p>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-255">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="aefb1-256">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="aefb1-256">PasteBefore</span></span>

<span data-ttu-id="aefb1-257">Plak het klem bord vóór de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-257">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="aefb1-258">VI-opdracht modus: `<P>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-258">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="aefb1-259">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="aefb1-259">PrependAndAccept</span></span>

<span data-ttu-id="aefb1-260">Laten voorafgaan door een ' # ' en accepteer de regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-260">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="aefb1-261">VI-opdracht modus: `<#>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-261">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="aefb1-262">Opnieuw uitvoeren</span><span class="sxs-lookup"><span data-stu-id="aefb1-262">Redo</span></span>

<span data-ttu-id="aefb1-263">Undo ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-263">Undo an undo.</span></span>

- <span data-ttu-id="aefb1-264">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-264">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="aefb1-265">VI Invoeg modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-265">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="aefb1-266">VI-opdracht modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-266">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="aefb1-267">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="aefb1-267">RepeatLastCommand</span></span>

<span data-ttu-id="aefb1-268">Herhaal de laatste tekst wijziging.</span><span class="sxs-lookup"><span data-stu-id="aefb1-268">Repeat the last text modification.</span></span>

- <span data-ttu-id="aefb1-269">VI-opdracht modus: `<.>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-269">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="aefb1-270">RevertLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-270">RevertLine</span></span>

<span data-ttu-id="aefb1-271">Hiermee wordt alle invoer teruggezet naar de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-271">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="aefb1-272">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-272">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="aefb1-273">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-273">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="aefb1-274">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-274">ShellBackwardKillWord</span></span>

<span data-ttu-id="aefb1-275">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-275">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="aefb1-276">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="aefb1-276">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="aefb1-277">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="aefb1-277">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="aefb1-278">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-278">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="aefb1-279">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-279">ShellKillWord</span></span>

<span data-ttu-id="aefb1-280">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-280">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="aefb1-281">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-281">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="aefb1-282">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="aefb1-282">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="aefb1-283">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-283">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="aefb1-284">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="aefb1-284">SwapCharacters</span></span>

<span data-ttu-id="aefb1-285">Het huidige teken en de eerste vervangen door wisselen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-285">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="aefb1-286">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-286">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="aefb1-287">VI Invoeg modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-287">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="aefb1-288">VI-opdracht modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-288">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="aefb1-289">Ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="aefb1-289">Undo</span></span>

<span data-ttu-id="aefb1-290">Een vorige bewerking ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-290">Undo a previous edit.</span></span>

- <span data-ttu-id="aefb1-291">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-291">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="aefb1-292">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-292">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="aefb1-293">VI Invoeg modus: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-293">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="aefb1-294">VI-opdracht modus: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-294">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="aefb1-295">UndoAll</span><span class="sxs-lookup"><span data-stu-id="aefb1-295">UndoAll</span></span>

<span data-ttu-id="aefb1-296">Alle vorige bewerkingen voor de regel ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-296">Undo all previous edits for line.</span></span>

- <span data-ttu-id="aefb1-297">VI-opdracht modus: `<U>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-297">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="aefb1-298">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="aefb1-298">UnixWordRubout</span></span>

<span data-ttu-id="aefb1-299">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-299">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="aefb1-300">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="aefb1-300">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="aefb1-301">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="aefb1-301">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="aefb1-302">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-302">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="aefb1-303">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-303">ValidateAndAcceptLine</span></span>

<span data-ttu-id="aefb1-304">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-304">Attempt to execute the current input.</span></span> <span data-ttu-id="aefb1-305">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-305">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="aefb1-306">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-306">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="aefb1-307">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-307">ViAcceptLine</span></span>

<span data-ttu-id="aefb1-308">Accepteer de regel en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-308">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="aefb1-309">VI-opdracht modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-309">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="aefb1-310">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="aefb1-310">ViAcceptLineOrExit</span></span>

<span data-ttu-id="aefb1-311">Als DeleteCharOrExit in de Emacs-modus, maar wel in plaats van een teken te verwijderen, accepteert u de regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-311">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="aefb1-312">VI Invoeg modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-312">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="aefb1-313">VI-opdracht modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-313">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="aefb1-314">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-314">ViAppendLine</span></span>

<span data-ttu-id="aefb1-315">Er wordt een nieuwe regel ingevoegd onder de huidige regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-315">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="aefb1-316">VI-opdracht modus: `<o>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-316">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="aefb1-317">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="aefb1-317">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="aefb1-318">Hiermee verwijdert u het vorige woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-318">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="aefb1-319">VI-opdracht modus: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-319">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="aefb1-320">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="aefb1-320">ViBackwardGlob</span></span>

<span data-ttu-id="aefb1-321">Verplaatst de cursor terug naar het begin van het vorige woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aefb1-321">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="aefb1-322">VI-opdracht modus: `<B>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-322">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="aefb1-323">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="aefb1-323">ViDeleteBrace</span></span>

<span data-ttu-id="aefb1-324">Zoek de accolade, het haakje sluiten of de vier Kante haken en verwijder alle inhoud binnen, inclusief de accolade.</span><span class="sxs-lookup"><span data-stu-id="aefb1-324">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="aefb1-325">VI-opdracht modus: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-325">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="aefb1-326">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="aefb1-326">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="aefb1-327">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-327">Delete to the end of the word.</span></span>

- <span data-ttu-id="aefb1-328">VI-opdracht modus: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-328">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="aefb1-329">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="aefb1-329">ViDeleteGlob</span></span>

<span data-ttu-id="aefb1-330">De volgende Globs verwijderen (door witruimte gescheiden woord).</span><span class="sxs-lookup"><span data-stu-id="aefb1-330">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="aefb1-331">VI-opdracht modus: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-331">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="aefb1-332">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-332">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="aefb1-333">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-333">Deletes until given character.</span></span>

- <span data-ttu-id="aefb1-334">VI-opdracht modus: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-334">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="aefb1-335">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="aefb1-335">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="aefb1-336">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-336">Deletes until given character.</span></span>

- <span data-ttu-id="aefb1-337">VI-opdracht modus: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-337">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="aefb1-338">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-338">ViDeleteToChar</span></span>

<span data-ttu-id="aefb1-339">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-339">Deletes until given character.</span></span>

- <span data-ttu-id="aefb1-340">VI-opdracht modus: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-340">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="aefb1-341">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="aefb1-341">ViDeleteToCharBackward</span></span>

<span data-ttu-id="aefb1-342">Hiermee verwijdert u achterwaartse tekens tot aan het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-342">Deletes backwards until given character.</span></span>

- <span data-ttu-id="aefb1-343">VI-opdracht modus: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-343">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="aefb1-344">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="aefb1-344">ViInsertAtBegining</span></span>

<span data-ttu-id="aefb1-345">Schakel over naar de Invoeg modus en plaats de cursor aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-345">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="aefb1-346">VI-opdracht modus: `<I>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-346">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="aefb1-347">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="aefb1-347">ViInsertAtEnd</span></span>

<span data-ttu-id="aefb1-348">Schakel over naar de Invoeg modus en plaats de cursor aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-348">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="aefb1-349">VI-opdracht modus: `<A>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-349">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="aefb1-350">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-350">ViInsertLine</span></span>

<span data-ttu-id="aefb1-351">Boven de huidige regel wordt een nieuwe regel ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-351">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="aefb1-352">VI-opdracht modus: `<O>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-352">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="aefb1-353">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="aefb1-353">ViInsertWithAppend</span></span>

<span data-ttu-id="aefb1-354">Toevoegen vanaf de huidige regel positie.</span><span class="sxs-lookup"><span data-stu-id="aefb1-354">Append from the current line position.</span></span>

- <span data-ttu-id="aefb1-355">VI-opdracht modus: `<a>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-355">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="aefb1-356">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="aefb1-356">ViInsertWithDelete</span></span>

<span data-ttu-id="aefb1-357">Verwijder het huidige teken en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-357">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="aefb1-358">VI-opdracht modus: `<s>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-358">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="aefb1-359">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="aefb1-359">ViJoinLines</span></span>

<span data-ttu-id="aefb1-360">De huidige regel en de volgende regel worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-360">Joins the current line and the next line.</span></span>

- <span data-ttu-id="aefb1-361">VI-opdracht modus: `<J>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-361">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="aefb1-362">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-362">ViReplaceLine</span></span>

<span data-ttu-id="aefb1-363">De volledige opdracht regel wissen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-363">Erase the entire command line.</span></span>

- <span data-ttu-id="aefb1-364">VI-opdracht modus: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-364">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="aefb1-365">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-365">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="aefb1-366">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-366">Replaces until given character.</span></span>

- <span data-ttu-id="aefb1-367">VI-opdracht modus: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-367">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="aefb1-368">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="aefb1-368">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="aefb1-369">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-369">Replaces until given character.</span></span>

- <span data-ttu-id="aefb1-370">VI-opdracht modus: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-370">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="aefb1-371">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-371">ViReplaceToChar</span></span>

<span data-ttu-id="aefb1-372">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-372">Deletes until given character.</span></span>

- <span data-ttu-id="aefb1-373">VI-opdracht modus: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-373">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="aefb1-374">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="aefb1-374">ViReplaceToCharBackward</span></span>

<span data-ttu-id="aefb1-375">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-375">Replaces until given character.</span></span>

- <span data-ttu-id="aefb1-376">VI-opdracht modus: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-376">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="aefb1-377">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-377">ViYankBeginningOfLine</span></span>

<span data-ttu-id="aefb1-378">Yank vanaf het begin van de buffer naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-378">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="aefb1-379">VI-opdracht modus: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-379">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="aefb1-380">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="aefb1-380">ViYankEndOfGlob</span></span>

<span data-ttu-id="aefb1-381">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="aefb1-381">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="aefb1-382">VI-opdracht modus: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-382">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="aefb1-383">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-383">ViYankEndOfWord</span></span>

<span data-ttu-id="aefb1-384">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="aefb1-384">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="aefb1-385">VI-opdracht modus: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-385">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="aefb1-386">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="aefb1-386">ViYankLeft</span></span>

<span data-ttu-id="aefb1-387">Yank teken (s) links van de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-387">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="aefb1-388">VI-opdracht modus: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-388">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="aefb1-389">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-389">ViYankLine</span></span>

<span data-ttu-id="aefb1-390">Yank de volledige buffer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-390">Yank the entire buffer.</span></span>

- <span data-ttu-id="aefb1-391">VI-opdracht modus: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-391">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="aefb1-392">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="aefb1-392">ViYankNextGlob</span></span>

<span data-ttu-id="aefb1-393">Yank van de cursor naar het begin van de volgende woord (en).</span><span class="sxs-lookup"><span data-stu-id="aefb1-393">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="aefb1-394">VI-opdracht modus: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-394">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="aefb1-395">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-395">ViYankNextWord</span></span>

<span data-ttu-id="aefb1-396">Yank het woord (en) na de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-396">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="aefb1-397">VI-opdracht modus: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-397">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="aefb1-398">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="aefb1-398">ViYankPercent</span></span>

<span data-ttu-id="aefb1-399">Yank naar/van overeenkomende accolade.</span><span class="sxs-lookup"><span data-stu-id="aefb1-399">Yank to/from matching brace.</span></span>

- <span data-ttu-id="aefb1-400">VI-opdracht modus: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-400">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="aefb1-401">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="aefb1-401">ViYankPreviousGlob</span></span>

<span data-ttu-id="aefb1-402">Yank vanaf het begin van het (de) woord (en) tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-402">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="aefb1-403">VI-opdracht modus: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-403">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="aefb1-404">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-404">ViYankPreviousWord</span></span>

<span data-ttu-id="aefb1-405">Yank de woorden vóór de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-405">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="aefb1-406">VI-opdracht modus: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-406">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="aefb1-407">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="aefb1-407">ViYankRight</span></span>

<span data-ttu-id="aefb1-408">Yank teken (s) onder en rechts van de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-408">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="aefb1-409">VI-opdracht modus: `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-409">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="aefb1-410">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-410">ViYankToEndOfLine</span></span>

<span data-ttu-id="aefb1-411">Yank van de cursor tot het einde van de buffer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-411">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="aefb1-412">VI-opdracht modus: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-412">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="aefb1-413">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-413">ViYankToFirstChar</span></span>

<span data-ttu-id="aefb1-414">Yank van het eerste niet-spatie teken tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-414">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="aefb1-415">VI-opdracht modus: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-415">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="aefb1-416">Yank</span><span class="sxs-lookup"><span data-stu-id="aefb1-416">Yank</span></span>

<span data-ttu-id="aefb1-417">Voeg de meest recent afgebroken tekst toe aan de invoer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-417">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="aefb1-418">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-418">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="aefb1-419">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="aefb1-419">YankLastArg</span></span>

<span data-ttu-id="aefb1-420">Yank het laatste argument van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-420">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="aefb1-421">Met een argument, de eerste keer dat deze wordt aangeroepen, gedraagt zich op dezelfde manier als YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="aefb1-421">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="aefb1-422">Als meerdere keren worden aangeroepen, wordt door de geschiedenis en ARG de richting ingesteld (negatief de richting omkeren.)</span><span class="sxs-lookup"><span data-stu-id="aefb1-422">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="aefb1-423">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-423">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="aefb1-424">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-424">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="aefb1-425">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="aefb1-425">YankNthArg</span></span>

<span data-ttu-id="aefb1-426">Yank het eerste argument (na de opdracht) van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-426">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="aefb1-427">Met een argument, Yank het ne argument (vanaf 0), als het argument negatief is, begint vanaf het laatste argument.</span><span class="sxs-lookup"><span data-stu-id="aefb1-427">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="aefb1-428">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-428">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="aefb1-429">YankPop</span><span class="sxs-lookup"><span data-stu-id="aefb1-429">YankPop</span></span>

<span data-ttu-id="aefb1-430">Als de vorige bewerking Yank of YankPop is, vervangt u de eerder yanked tekst door de volgende afgebroken tekst van de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="aefb1-430">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="aefb1-431">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-431">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="aefb1-432">Functies voor cursor verplaatsing</span><span class="sxs-lookup"><span data-stu-id="aefb1-432">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="aefb1-433">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-433">BackwardChar</span></span>

<span data-ttu-id="aefb1-434">De cursor één teken naar links verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-434">Move the cursor one character to the left.</span></span> <span data-ttu-id="aefb1-435">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="aefb1-435">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="aefb1-436">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-436">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="aefb1-437">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-437">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="aefb1-438">VI Invoeg modus: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-438">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="aefb1-439">VI-opdracht modus: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-439">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="aefb1-440">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-440">BackwardWord</span></span>

<span data-ttu-id="aefb1-441">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-441">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="aefb1-442">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="aefb1-442">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="aefb1-443">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-443">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="aefb1-444">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-444">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="aefb1-445">VI Invoeg modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-445">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="aefb1-446">VI-opdracht modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-446">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="aefb1-447">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-447">BeginningOfLine</span></span>

<span data-ttu-id="aefb1-448">Als de invoer meerdere regels heeft, gaat u naar het begin van de huidige regel of gaat u naar het begin van de invoer als deze al aan het begin van de regel staat.</span><span class="sxs-lookup"><span data-stu-id="aefb1-448">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="aefb1-449">Als de invoer één regel heeft, gaat u naar het begin van de invoer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-449">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="aefb1-450">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-450">Cmd: `<Home>`</span></span>
- <span data-ttu-id="aefb1-451">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-451">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="aefb1-452">VI Invoeg modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-452">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="aefb1-453">VI-opdracht modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-453">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="aefb1-454">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-454">EndOfLine</span></span>

<span data-ttu-id="aefb1-455">Als de invoer meerdere regels heeft, gaat u naar het einde van de huidige regel of gaat u naar het einde van de invoer als u aan het einde van de regel bent.</span><span class="sxs-lookup"><span data-stu-id="aefb1-455">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="aefb1-456">Als de invoer één regel heeft, gaat u naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-456">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="aefb1-457">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-457">Cmd: `<End>`</span></span>
- <span data-ttu-id="aefb1-458">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-458">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="aefb1-459">VI Invoeg modus: `<End>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-459">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="aefb1-460">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-460">ForwardChar</span></span>

<span data-ttu-id="aefb1-461">De cursor één teken naar rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-461">Move the cursor one character to the right.</span></span> <span data-ttu-id="aefb1-462">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="aefb1-462">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="aefb1-463">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-463">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="aefb1-464">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-464">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="aefb1-465">VI Invoeg modus: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-465">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="aefb1-466">VI-opdracht modus: `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-466">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="aefb1-467">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-467">ForwardWord</span></span>

<span data-ttu-id="aefb1-468">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-468">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="aefb1-469">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="aefb1-469">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="aefb1-470">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-470">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="aefb1-471">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="aefb1-471">GotoBrace</span></span>

<span data-ttu-id="aefb1-472">Ga naar de accolade, haakjes of vier Kante haakjes.</span><span class="sxs-lookup"><span data-stu-id="aefb1-472">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="aefb1-473">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-473">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="aefb1-474">VI Invoeg modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-474">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="aefb1-475">VI-opdracht modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-475">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="aefb1-476">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="aefb1-476">GotoColumn</span></span>

<span data-ttu-id="aefb1-477">Ga naar de kolom die wordt aangegeven door arg.</span><span class="sxs-lookup"><span data-stu-id="aefb1-477">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="aefb1-478">VI-opdracht modus: `<|>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-478">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="aefb1-479">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-479">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="aefb1-480">De cursor verplaatsen naar het eerste niet-lege teken in de regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-480">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="aefb1-481">VI-opdracht modus: `<^>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-481">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="aefb1-482">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-482">MoveToEndOfLine</span></span>

<span data-ttu-id="aefb1-483">De cursor verplaatsen naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-483">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="aefb1-484">VI-opdracht modus: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-484">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="aefb1-485">NextLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-485">NextLine</span></span>

<span data-ttu-id="aefb1-486">De cursor verplaatsen naar de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-486">Move the cursor to the next line.</span></span>

- <span data-ttu-id="aefb1-487">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-487">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="aefb1-488">NextWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-488">NextWord</span></span>

<span data-ttu-id="aefb1-489">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-489">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="aefb1-490">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="aefb1-490">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="aefb1-491">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-491">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="aefb1-492">VI Invoeg modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-492">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="aefb1-493">VI-opdracht modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-493">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="aefb1-494">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="aefb1-494">NextWordEnd</span></span>

<span data-ttu-id="aefb1-495">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="aefb1-496">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="aefb1-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="aefb1-497">VI-opdracht modus: `<e>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-497">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="aefb1-498">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-498">PreviousLine</span></span>

<span data-ttu-id="aefb1-499">Verplaats de cursor naar de vorige regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-499">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="aefb1-500">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-500">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="aefb1-501">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-501">ShellBackwardWord</span></span>

<span data-ttu-id="aefb1-502">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-502">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="aefb1-503">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="aefb1-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="aefb1-504">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-504">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="aefb1-505">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-505">ShellForwardWord</span></span>

<span data-ttu-id="aefb1-506">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-506">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="aefb1-507">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="aefb1-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="aefb1-508">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-508">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="aefb1-509">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-509">ShellNextWord</span></span>

<span data-ttu-id="aefb1-510">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-510">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="aefb1-511">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="aefb1-511">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="aefb1-512">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-512">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="aefb1-513">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-513">ViBackwardWord</span></span>

<span data-ttu-id="aefb1-514">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="aefb1-515">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="aefb1-515">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="aefb1-516">VI-opdracht modus: `<b>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-516">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="aefb1-517">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="aefb1-517">ViEndOfGlob</span></span>

<span data-ttu-id="aefb1-518">Verplaatst de cursor naar het einde van het woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aefb1-518">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="aefb1-519">VI-opdracht modus: `<E>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-519">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="aefb1-520">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="aefb1-520">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="aefb1-521">Wordt verplaatst naar het einde van het vorige woord, waarbij alleen witruimte wordt gebruikt als woord als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-521">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="aefb1-522">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-522">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="aefb1-523">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="aefb1-523">ViGotoBrace</span></span>

<span data-ttu-id="aefb1-524">Vergelijkbaar met GotoBrace, maar is in plaats van op tokens gebaseerd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-524">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="aefb1-525">VI-opdracht modus: `<%>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-525">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="aefb1-526">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="aefb1-526">ViNextGlob</span></span>

<span data-ttu-id="aefb1-527">Verplaatst naar het volgende woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-527">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="aefb1-528">VI-opdracht modus: `<W>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-528">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="aefb1-529">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-529">ViNextWord</span></span>

<span data-ttu-id="aefb1-530">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-530">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="aefb1-531">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="aefb1-531">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="aefb1-532">VI-opdracht modus: `<w>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-532">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="aefb1-533">Geschiedenis functies</span><span class="sxs-lookup"><span data-stu-id="aefb1-533">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="aefb1-534">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="aefb1-534">BeginningOfHistory</span></span>

<span data-ttu-id="aefb1-535">Hiermee gaat u naar het eerste item in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="aefb1-535">Move to the first item in the history.</span></span>

- <span data-ttu-id="aefb1-536">Emacs: `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="aefb1-536">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="aefb1-537">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="aefb1-537">ClearHistory</span></span>

<span data-ttu-id="aefb1-538">Hiermee wist u de geschiedenis in PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="aefb1-538">Clears history in PSReadLine.</span></span> <span data-ttu-id="aefb1-539">Dit heeft geen invloed op de Power shell-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="aefb1-539">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="aefb1-540">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-540">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="aefb1-541">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="aefb1-541">EndOfHistory</span></span>

<span data-ttu-id="aefb1-542">Hiermee gaat u naar het laatste item (de huidige invoer) in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="aefb1-542">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="aefb1-543">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-543">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="aefb1-544">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="aefb1-544">ForwardSearchHistory</span></span>

<span data-ttu-id="aefb1-545">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="aefb1-545">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="aefb1-546">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-546">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="aefb1-547">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-547">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="aefb1-548">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="aefb1-548">HistorySearchBackward</span></span>

<span data-ttu-id="aefb1-549">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-549">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="aefb1-550">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-550">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="aefb1-551">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="aefb1-551">HistorySearchForward</span></span>

<span data-ttu-id="aefb1-552">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-552">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="aefb1-553">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-553">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="aefb1-554">NextHistory</span><span class="sxs-lookup"><span data-stu-id="aefb1-554">NextHistory</span></span>

<span data-ttu-id="aefb1-555">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="aefb1-555">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="aefb1-556">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-556">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="aefb1-557">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-557">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="aefb1-558">VI Invoeg modus: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-558">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="aefb1-559">VI-opdracht modus: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-559">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="aefb1-560">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="aefb1-560">PreviousHistory</span></span>

<span data-ttu-id="aefb1-561">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="aefb1-561">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="aefb1-562">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-562">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="aefb1-563">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-563">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="aefb1-564">VI Invoeg modus: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-564">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="aefb1-565">VI-opdracht modus: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="aefb1-565">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="aefb1-566">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="aefb1-566">ReverseSearchHistory</span></span>

<span data-ttu-id="aefb1-567">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="aefb1-567">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="aefb1-568">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-568">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="aefb1-569">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-569">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="aefb1-570">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="aefb1-570">ViSearchHistoryBackward</span></span>

<span data-ttu-id="aefb1-571">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="aefb1-571">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="aefb1-572">VI Invoeg modus: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-572">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="aefb1-573">VI-opdracht modus: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-573">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="aefb1-574">Voltooiings functies</span><span class="sxs-lookup"><span data-stu-id="aefb1-574">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="aefb1-575">Voltooid</span><span class="sxs-lookup"><span data-stu-id="aefb1-575">Complete</span></span>

<span data-ttu-id="aefb1-576">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-576">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="aefb1-577">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="aefb1-577">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="aefb1-578">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aefb1-578">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="aefb1-579">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-579">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="aefb1-580">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="aefb1-580">MenuComplete</span></span>

<span data-ttu-id="aefb1-581">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-581">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="aefb1-582">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="aefb1-582">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="aefb1-583">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aefb1-583">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="aefb1-584">Cmd `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-584">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="aefb1-585">Emacs: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-585">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="aefb1-586">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="aefb1-586">PossibleCompletions</span></span>

<span data-ttu-id="aefb1-587">De lijst met mogelijke aanvullingen weer geven.</span><span class="sxs-lookup"><span data-stu-id="aefb1-587">Display the list of possible completions.</span></span>

- <span data-ttu-id="aefb1-588">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-588">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="aefb1-589">VI Invoeg modus: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-589">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="aefb1-590">VI-opdracht modus: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-590">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="aefb1-591">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="aefb1-591">TabCompleteNext</span></span>

<span data-ttu-id="aefb1-592">Poging om de tekst rond de cursor te volt ooien met de volgende beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="aefb1-592">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="aefb1-593">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-593">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="aefb1-594">VI-opdracht modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-594">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="aefb1-595">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="aefb1-595">TabCompletePrevious</span></span>

<span data-ttu-id="aefb1-596">Poging om de tekst rond de cursor te volt ooien met de vorige beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="aefb1-596">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="aefb1-597">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-597">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="aefb1-598">VI-opdracht modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-598">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="aefb1-599">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="aefb1-599">ViTabCompleteNext</span></span>

<span data-ttu-id="aefb1-600">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompleteNext aan.</span><span class="sxs-lookup"><span data-stu-id="aefb1-600">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="aefb1-601">VI Invoeg modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-601">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="aefb1-602">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="aefb1-602">ViTabCompletePrevious</span></span>

<span data-ttu-id="aefb1-603">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompletePrevious aan.</span><span class="sxs-lookup"><span data-stu-id="aefb1-603">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="aefb1-604">VI Invoeg modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-604">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="aefb1-605">Diverse functies</span><span class="sxs-lookup"><span data-stu-id="aefb1-605">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="aefb1-606">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="aefb1-606">CaptureScreen</span></span>

<span data-ttu-id="aefb1-607">Interactieve scherm opname starten-pijl-omhoog/omlaag Selecteer regels en voer de geselecteerde tekst als tekst en HTML naar het klem bord kopiëren.</span><span class="sxs-lookup"><span data-stu-id="aefb1-607">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="aefb1-608">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-608">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="aefb1-609">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="aefb1-609">ClearScreen</span></span>

<span data-ttu-id="aefb1-610">Schakel het scherm uit en teken de huidige regel boven aan het scherm.</span><span class="sxs-lookup"><span data-stu-id="aefb1-610">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="aefb1-611">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-611">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="aefb1-612">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-612">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="aefb1-613">VI Invoeg modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-613">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="aefb1-614">VI-opdracht modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-614">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="aefb1-615">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="aefb1-615">DigitArgument</span></span>

<span data-ttu-id="aefb1-616">Start een nieuw cijfer argument om door te geven aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="aefb1-616">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="aefb1-617">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="aefb1-617">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="aefb1-618">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="aefb1-618">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="aefb1-619">VI-opdracht modus: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-619">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="aefb1-620">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="aefb1-620">InvokePrompt</span></span>

<span data-ttu-id="aefb1-621">Hiermee wordt de huidige prompt gewist en wordt de functie Prompt aangeroepen om de prompt opnieuw weer te geven.</span><span class="sxs-lookup"><span data-stu-id="aefb1-621">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="aefb1-622">Dit is handig voor aangepaste sleutel afhandelingen die de status wijzigen, bijvoorbeeld de huidige map wijzigen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-622">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="aefb1-623">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-623">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="aefb1-624">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="aefb1-624">ScrollDisplayDown</span></span>

<span data-ttu-id="aefb1-625">De weer gave één scherm omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="aefb1-625">Scroll the display down one screen.</span></span>

- <span data-ttu-id="aefb1-626">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-626">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="aefb1-627">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-627">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="aefb1-628">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-628">ScrollDisplayDownLine</span></span>

<span data-ttu-id="aefb1-629">De weer gave één regel omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="aefb1-629">Scroll the display down one line.</span></span>

- <span data-ttu-id="aefb1-630">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-630">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="aefb1-631">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-631">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="aefb1-632">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="aefb1-632">ScrollDisplayToCursor</span></span>

<span data-ttu-id="aefb1-633">Schuif de weer gave naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-633">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="aefb1-634">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-634">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="aefb1-635">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="aefb1-635">ScrollDisplayTop</span></span>

<span data-ttu-id="aefb1-636">Schuif de weer gave naar boven.</span><span class="sxs-lookup"><span data-stu-id="aefb1-636">Scroll the display to the top.</span></span>

- <span data-ttu-id="aefb1-637">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-637">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="aefb1-638">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="aefb1-638">ScrollDisplayUp</span></span>

<span data-ttu-id="aefb1-639">Schuif de weer gave één scherm omhoog.</span><span class="sxs-lookup"><span data-stu-id="aefb1-639">Scroll the display up one screen.</span></span>

- <span data-ttu-id="aefb1-640">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-640">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="aefb1-641">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-641">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="aefb1-642">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-642">ScrollDisplayUpLine</span></span>

<span data-ttu-id="aefb1-643">De weer gave één regel omhoog schuiven.</span><span class="sxs-lookup"><span data-stu-id="aefb1-643">Scroll the display up one line.</span></span>

- <span data-ttu-id="aefb1-644">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-644">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="aefb1-645">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-645">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="aefb1-646">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="aefb1-646">SelfInsert</span></span>

<span data-ttu-id="aefb1-647">Voeg de sleutel in.</span><span class="sxs-lookup"><span data-stu-id="aefb1-647">Insert the key.</span></span>

- <span data-ttu-id="aefb1-648">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-648">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="aefb1-649">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="aefb1-649">ShowKeyBindings</span></span>

<span data-ttu-id="aefb1-650">Alle gebonden sleutels weer geven.</span><span class="sxs-lookup"><span data-stu-id="aefb1-650">Show all bound keys.</span></span>

- <span data-ttu-id="aefb1-651">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-651">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="aefb1-652">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-652">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="aefb1-653">VI Invoeg modus: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-653">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="aefb1-654">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="aefb1-654">ViCommandMode</span></span>

<span data-ttu-id="aefb1-655">Schakel de huidige bedrijfs modus uit van Vi-Insert naar de VI-opdracht.</span><span class="sxs-lookup"><span data-stu-id="aefb1-655">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="aefb1-656">VI Invoeg modus: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-656">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="aefb1-657">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="aefb1-657">ViDigitArgumentInChord</span></span>

<span data-ttu-id="aefb1-658">Start een nieuw cijfer argument om door te geven aan andere functies in een van de koorden van VI.</span><span class="sxs-lookup"><span data-stu-id="aefb1-658">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="aefb1-659">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-659">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="aefb1-660">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="aefb1-660">ViEditVisually</span></span>

<span data-ttu-id="aefb1-661">Bewerk de opdracht regel in een tekst editor die is opgegeven door $env: EDITOR of $env: VISUAL.</span><span class="sxs-lookup"><span data-stu-id="aefb1-661">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="aefb1-662">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-662">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="aefb1-663">VI-opdracht modus: `<v>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-663">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="aefb1-664">ViExit</span><span class="sxs-lookup"><span data-stu-id="aefb1-664">ViExit</span></span>

<span data-ttu-id="aefb1-665">Hiermee wordt de shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="aefb1-665">Exits the shell.</span></span>

- <span data-ttu-id="aefb1-666">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-666">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="aefb1-667">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="aefb1-667">ViInsertMode</span></span>

<span data-ttu-id="aefb1-668">Schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-668">Switch to Insert mode.</span></span>

- <span data-ttu-id="aefb1-669">VI-opdracht modus: `<i>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-669">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="aefb1-670">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="aefb1-670">WhatIsKey</span></span>

<span data-ttu-id="aefb1-671">Lees een sleutel en vertel me wat de sleutel is gebonden.</span><span class="sxs-lookup"><span data-stu-id="aefb1-671">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="aefb1-672">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-672">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="aefb1-673">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-673">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="aefb1-674">Selectie functies</span><span class="sxs-lookup"><span data-stu-id="aefb1-674">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="aefb1-675">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="aefb1-675">ExchangePointAndMark</span></span>

<span data-ttu-id="aefb1-676">De cursor wordt op de locatie van het merk geplaatst en het vinkje wordt verplaatst naar de locatie van de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-676">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="aefb1-677">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-677">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="aefb1-678">SelectAll aanroepen</span><span class="sxs-lookup"><span data-stu-id="aefb1-678">SelectAll</span></span>

<span data-ttu-id="aefb1-679">Selecteer de volledige regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-679">Select the entire line.</span></span>

- <span data-ttu-id="aefb1-680">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-680">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="aefb1-681">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-681">SelectBackwardChar</span></span>

<span data-ttu-id="aefb1-682">Pas de huidige selectie aan om het vorige teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="aefb1-682">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="aefb1-683">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-683">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="aefb1-684">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-684">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="aefb1-685">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-685">SelectBackwardsLine</span></span>

<span data-ttu-id="aefb1-686">Pas de huidige selectie aan de cursor toe aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-686">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="aefb1-687">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-687">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="aefb1-688">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-688">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="aefb1-689">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-689">SelectBackwardWord</span></span>

<span data-ttu-id="aefb1-690">Pas de huidige selectie aan om het vorige woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="aefb1-690">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="aefb1-691">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-691">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="aefb1-692">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-692">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="aefb1-693">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-693">SelectForwardChar</span></span>

<span data-ttu-id="aefb1-694">Pas de huidige selectie aan om het volgende teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="aefb1-694">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="aefb1-695">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-695">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="aefb1-696">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-696">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="aefb1-697">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-697">SelectForwardWord</span></span>

<span data-ttu-id="aefb1-698">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-698">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="aefb1-699">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-699">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="aefb1-700">SelectLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-700">SelectLine</span></span>

<span data-ttu-id="aefb1-701">Pas de huidige selectie aan de cursor toe aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-701">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="aefb1-702">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-702">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="aefb1-703">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-703">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="aefb1-704">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-704">SelectNextWord</span></span>

<span data-ttu-id="aefb1-705">Pas de huidige selectie aan om het volgende woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="aefb1-705">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="aefb1-706">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-706">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="aefb1-707">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-707">SelectShellBackwardWord</span></span>

<span data-ttu-id="aefb1-708">Pas de huidige selectie aan om het vorige woord op te maken met behulp van ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-708">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="aefb1-709">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-709">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="aefb1-710">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-710">SelectShellForwardWord</span></span>

<span data-ttu-id="aefb1-711">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-711">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="aefb1-712">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-712">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="aefb1-713">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="aefb1-713">SelectShellNextWord</span></span>

<span data-ttu-id="aefb1-714">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="aefb1-714">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="aefb1-715">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="aefb1-715">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="aefb1-716">SetMark</span><span class="sxs-lookup"><span data-stu-id="aefb1-716">SetMark</span></span>

<span data-ttu-id="aefb1-717">De huidige locatie van de cursor markeren voor gebruik in een volgende bewerkings opdracht.</span><span class="sxs-lookup"><span data-stu-id="aefb1-717">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="aefb1-718">Emacs: `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="aefb1-718">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="aefb1-719">Zoek functies</span><span class="sxs-lookup"><span data-stu-id="aefb1-719">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="aefb1-720">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="aefb1-720">CharacterSearch</span></span>

<span data-ttu-id="aefb1-721">Lees een teken en zoek voorwaarts naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-721">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="aefb1-722">Als er een argument is opgegeven, zoekt u voorwaarts (of achterwaarts als negatieve) voor het ne voorval.</span><span class="sxs-lookup"><span data-stu-id="aefb1-722">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="aefb1-723">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-723">Cmd: `<F3>`</span></span>
- <span data-ttu-id="aefb1-724">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-724">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="aefb1-725">VI Invoeg modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-725">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="aefb1-726">VI-opdracht modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-726">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="aefb1-727">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="aefb1-727">CharacterSearchBackward</span></span>

<span data-ttu-id="aefb1-728">Lees een teken en zoek terug naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-728">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="aefb1-729">Als er een argument is opgegeven, zoekt u terug (of als dit negatief is) voor het ne exemplaar.</span><span class="sxs-lookup"><span data-stu-id="aefb1-729">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="aefb1-730">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-730">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="aefb1-731">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-731">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="aefb1-732">VI Invoeg modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-732">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="aefb1-733">VI-opdracht modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-733">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="aefb1-734">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="aefb1-734">RepeatLastCharSearch</span></span>

<span data-ttu-id="aefb1-735">De laatst opgenomen zoek opdracht herhalen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-735">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="aefb1-736">VI-opdracht modus: `<;>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-736">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="aefb1-737">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="aefb1-737">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="aefb1-738">De laatst opgenomen zoek opdracht herhalen, maar in tegenovergestelde richting.</span><span class="sxs-lookup"><span data-stu-id="aefb1-738">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="aefb1-739">VI-opdracht modus: `<,>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-739">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="aefb1-740">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="aefb1-740">RepeatSearch</span></span>

<span data-ttu-id="aefb1-741">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-741">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="aefb1-742">VI-opdracht modus: `<n>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-742">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="aefb1-743">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="aefb1-743">RepeatSearchBackward</span></span>

<span data-ttu-id="aefb1-744">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-744">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="aefb1-745">VI-opdracht modus: `<N>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-745">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="aefb1-746">SearchChar</span><span class="sxs-lookup"><span data-stu-id="aefb1-746">SearchChar</span></span>

<span data-ttu-id="aefb1-747">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-747">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="aefb1-748">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="aefb1-748">This is for 't' functionality.</span></span>

- <span data-ttu-id="aefb1-749">VI-opdracht modus: `<f>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-749">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="aefb1-750">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="aefb1-750">SearchCharBackward</span></span>

<span data-ttu-id="aefb1-751">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="aefb1-752">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="aefb1-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="aefb1-753">VI-opdracht modus: `<F>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-753">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="aefb1-754">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="aefb1-754">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="aefb1-755">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-755">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="aefb1-756">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="aefb1-756">This is for 'T' functionality.</span></span>

- <span data-ttu-id="aefb1-757">VI-opdracht modus: `<T>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-757">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="aefb1-758">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="aefb1-758">SearchCharWithBackoff</span></span>

<span data-ttu-id="aefb1-759">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-759">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="aefb1-760">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="aefb1-760">This is for 't' functionality.</span></span>

- <span data-ttu-id="aefb1-761">VI-opdracht modus: `<t>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-761">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="aefb1-762">SearchForward</span><span class="sxs-lookup"><span data-stu-id="aefb1-762">SearchForward</span></span>

<span data-ttu-id="aefb1-763">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="aefb1-763">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="aefb1-764">VI Invoeg modus: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-764">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="aefb1-765">VI-opdracht modus: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="aefb1-765">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="aefb1-766">Aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="aefb1-766">Custom Key Bindings</span></span>

<span data-ttu-id="aefb1-767">PSReadLine ondersteunt aangepaste sleutel bindingen met behulp van de-cmdlet `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="aefb1-767">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="aefb1-768">De meeste aangepaste sleutel bindingen roepen een van de bovenstaande functies aan, bijvoorbeeld</span><span class="sxs-lookup"><span data-stu-id="aefb1-768">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="aefb1-769">U kunt een script Block binden aan een sleutel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-769">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="aefb1-770">Het script Block kan veel wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="aefb1-770">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="aefb1-771">Enkele handige voor beelden zijn</span><span class="sxs-lookup"><span data-stu-id="aefb1-771">Some useful examples include</span></span>

- <span data-ttu-id="aefb1-772">de opdracht regel bewerken</span><span class="sxs-lookup"><span data-stu-id="aefb1-772">edit the command line</span></span>
- <span data-ttu-id="aefb1-773">een nieuw venster openen (bijvoorbeeld Help)</span><span class="sxs-lookup"><span data-stu-id="aefb1-773">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="aefb1-774">mappen wijzigen zonder de opdracht regel te wijzigen</span><span class="sxs-lookup"><span data-stu-id="aefb1-774">change directories without changing the command line</span></span>

<span data-ttu-id="aefb1-775">De script Block ontvangt twee argumenten:</span><span class="sxs-lookup"><span data-stu-id="aefb1-775">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="aefb1-776">`$key` -Een **[ConsoleKeyInfo]** -object dat de sleutel is die de aangepaste binding heeft geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-776">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="aefb1-777">Als u dezelfde script Block aan meerdere sleutels koppelt en verschillende acties moet uitvoeren, afhankelijk van de sleutel, kunt u $key controleren.</span><span class="sxs-lookup"><span data-stu-id="aefb1-777">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="aefb1-778">Veel aangepaste bindingen negeren dit argument.</span><span class="sxs-lookup"><span data-stu-id="aefb1-778">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="aefb1-779">`$arg` -Een wille keurig argument.</span><span class="sxs-lookup"><span data-stu-id="aefb1-779">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="aefb1-780">Meestal is dit een geheel getal dat de gebruiker door gegeven van de sleutel bindingen DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="aefb1-780">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="aefb1-781">Als uw binding geen argumenten accepteert, is het redelijk om dit argument te negeren.</span><span class="sxs-lookup"><span data-stu-id="aefb1-781">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="aefb1-782">Laten we een voor beeld bekijken waarmee een opdracht regel wordt toegevoegd aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="aefb1-782">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="aefb1-783">Dit is handig wanneer u ervoor hebt gekozen om iets te doen, maar niet opnieuw moet invoeren van de opdracht regel die u al hebt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-783">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="aefb1-784">U kunt veel meer voor beelden bekijken in het bestand `SamplePSReadLineProfile.ps1` dat is geïnstalleerd in de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="aefb1-784">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="aefb1-785">De meeste sleutel bindingen gebruiken enkele hulp functies voor het bewerken van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-785">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="aefb1-786">Deze Api's worden beschreven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="aefb1-786">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="aefb1-787">Api's voor de ondersteuning van aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="aefb1-787">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="aefb1-788">De volgende functies zijn openbaar in micro soft. Power shell. PSConsoleReadLine, maar kunnen niet rechtstreeks aan een sleutel worden gebonden.</span><span class="sxs-lookup"><span data-stu-id="aefb1-788">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="aefb1-789">De meeste zijn handig in aangepaste sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-789">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="aefb1-790">Een opdracht regel toevoegen aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="aefb1-790">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="aefb1-791">Wis de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="aefb1-791">Clear the kill-ring.</span></span>  <span data-ttu-id="aefb1-792">Dit wordt meestal gebruikt voor het testen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-792">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="aefb1-793">Verwijder de lengte tekens uit het begin.</span><span class="sxs-lookup"><span data-stu-id="aefb1-793">Delete length characters from start.</span></span>  <span data-ttu-id="aefb1-794">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="aefb1-794">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="aefb1-795">Voer de actie opname uit op basis van de voor keuren van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="aefb1-795">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="aefb1-796">Deze twee functies halen nuttige informatie op over de huidige status van de invoer buffer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-796">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="aefb1-797">De eerste wordt vaak gebruikt voor eenvoudige gevallen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-797">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="aefb1-798">De tweede wordt gebruikt als uw binding iets geavanceerder gaat met de AST.</span><span class="sxs-lookup"><span data-stu-id="aefb1-798">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="aefb1-799">Deze functie wordt gebruikt door Get-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="aefb1-799">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="aefb1-800">Deze functie wordt gebruikt door Get-PSReadLineOption en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="aefb1-800">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="aefb1-801">Als er niets is geselecteerd op de opdracht regel, wordt-1 geretourneerd in zowel start als length.</span><span class="sxs-lookup"><span data-stu-id="aefb1-801">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="aefb1-802">Als er een selectie is op de opdracht regel, worden het begin en de lengte van de selectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="aefb1-802">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="aefb1-803">Voeg een teken of teken reeks toe aan de cursor.</span><span class="sxs-lookup"><span data-stu-id="aefb1-803">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="aefb1-804">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="aefb1-804">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="aefb1-805">Dit is het belangrijkste ingangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="aefb1-805">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="aefb1-806">Er wordt geen recursie ondersteund, dus is niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="aefb1-806">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="aefb1-807">Deze functie wordt gebruikt door Remove-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="aefb1-807">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="aefb1-808">Vervang een deel van de invoer.</span><span class="sxs-lookup"><span data-stu-id="aefb1-808">Replace some of the input.</span></span> <span data-ttu-id="aefb1-809">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="aefb1-809">This operation supports undo/redo.</span></span> <span data-ttu-id="aefb1-810">U kunt het beste verwijderen gevolgd door INSERT, omdat het wordt beschouwd als één actie voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-810">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="aefb1-811">De cursor verplaatsen naar de opgegeven verschuiving.</span><span class="sxs-lookup"><span data-stu-id="aefb1-811">Move the cursor to the given offset.</span></span> <span data-ttu-id="aefb1-812">Cursor verplaatsing wordt niet bijgehouden voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="aefb1-812">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="aefb1-813">Deze functie is een helper-methode die wordt gebruikt door de cmdlet Set-PSReadLineOption, maar kan handig zijn voor een aangepaste sleutel binding die tijdelijk een instelling wil wijzigen.</span><span class="sxs-lookup"><span data-stu-id="aefb1-813">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="aefb1-814">Deze Help methode wordt gebruikt voor aangepaste bindingen die voldoen aan DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="aefb1-814">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="aefb1-815">Een typische aanroep ziet eruit als</span><span class="sxs-lookup"><span data-stu-id="aefb1-815">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="aefb1-816">OPMERKING</span><span class="sxs-lookup"><span data-stu-id="aefb1-816">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="aefb1-817">COMPATIBILITEIT MET POWER SHELL</span><span class="sxs-lookup"><span data-stu-id="aefb1-817">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="aefb1-818">PSReadLine vereist Power Shell 3,0, of nieuwer, en de console-host.</span><span class="sxs-lookup"><span data-stu-id="aefb1-818">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="aefb1-819">Het werkt niet in Power shell ISE.</span><span class="sxs-lookup"><span data-stu-id="aefb1-819">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="aefb1-820">Het werkt in de console van Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="aefb1-820">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="aefb1-821">OPDRACHT GESCHIEDENIS</span><span class="sxs-lookup"><span data-stu-id="aefb1-821">COMMAND HISTORY</span></span>

<span data-ttu-id="aefb1-822">PSReadLine onderhoudt een geschiedenis bestand met alle opdrachten en gegevens die u hebt ingevoerd op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="aefb1-822">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="aefb1-823">Dit kan gevoelige gegevens bevatten, inclusief wacht woorden.</span><span class="sxs-lookup"><span data-stu-id="aefb1-823">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="aefb1-824">Als u bijvoorbeeld de cmdlet gebruikt, `ConvertTo-SecureString` wordt het wacht woord in het geschiedenis bestand vastgelegd als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="aefb1-824">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="aefb1-825">De geschiedenis bestanden zijn een bestand met de naam `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="aefb1-825">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="aefb1-826">Op Windows-systemen wordt het geschiedenis bestand opgeslagen op `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="aefb1-826">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="aefb1-827">Op niet-Windows-systemen worden de geschiedenis bestanden opgeslagen in `$env:XDG_DATA_HOME/powershell/PSReadLine` of `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="aefb1-827">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="aefb1-828">FEEDBACK & bijdragen aan PSReadLine</span><span class="sxs-lookup"><span data-stu-id="aefb1-828">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="aefb1-829">PSReadLine op GitHub</span><span class="sxs-lookup"><span data-stu-id="aefb1-829">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="aefb1-830">U kunt een pull-aanvraag verzenden of feedback verzenden op de pagina GitHub.</span><span class="sxs-lookup"><span data-stu-id="aefb1-830">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="aefb1-831">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="aefb1-831">SEE ALSO</span></span>

<span data-ttu-id="aefb1-832">PSReadLine wordt sterk beïnvloed door de GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="aefb1-832">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>