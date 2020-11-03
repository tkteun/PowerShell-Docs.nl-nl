---
description: PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over PSReadLine
ms.openlocfilehash: 1188b8dc0b4099a7c1dcc472e3b02c2d4fa908bc
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252131"
---
# <a name="psreadline"></a><span data-ttu-id="b237e-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b237e-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="b237e-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b237e-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="b237e-106">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b237e-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="b237e-107">PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="b237e-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="b237e-108">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b237e-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="b237e-109">PSReadLine 2,0 biedt een krachtige opdracht regel voor het bewerken van de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="b237e-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="b237e-110">De oplossing biedt het volgende:</span><span class="sxs-lookup"><span data-stu-id="b237e-110">It provides:</span></span>

- <span data-ttu-id="b237e-111">Syntaxis kleur van de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="b237e-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="b237e-112">Een visuele indicatie van syntaxis fouten</span><span class="sxs-lookup"><span data-stu-id="b237e-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="b237e-113">Een betere ervaring met meerdere regels (zowel bewerkingen als geschiedenis)</span><span class="sxs-lookup"><span data-stu-id="b237e-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="b237e-114">Aanpas bare sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="b237e-114">Customizable key bindings</span></span>
- <span data-ttu-id="b237e-115">Cmd-en emacs-modi</span><span class="sxs-lookup"><span data-stu-id="b237e-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="b237e-116">Veel configuratie opties</span><span class="sxs-lookup"><span data-stu-id="b237e-116">Many configuration options</span></span>
- <span data-ttu-id="b237e-117">Bash-stijl voltooiing (optioneel in CMD-modus, standaard in Emacs-modus)</span><span class="sxs-lookup"><span data-stu-id="b237e-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="b237e-118">Emacs Yank/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="b237e-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="b237e-119">"Woord" verplaatsing en afsluiten op basis van Power shell-tokens</span><span class="sxs-lookup"><span data-stu-id="b237e-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="b237e-120">De volgende functies zijn beschikbaar in de klasse **[micro soft. Power shell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="b237e-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

> [!NOTE]
> <span data-ttu-id="b237e-121">Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="b237e-121">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="b237e-122">Op dit moment werkt PSReadLine niet goed met scherm lezers.</span><span class="sxs-lookup"><span data-stu-id="b237e-122">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="b237e-123">De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="b237e-123">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="b237e-124">U kunt de module hand matig laden, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="b237e-124">You can manually load the module if necessary.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="b237e-125">Basis bewerkings functies</span><span class="sxs-lookup"><span data-stu-id="b237e-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="b237e-126">Afbreken</span><span class="sxs-lookup"><span data-stu-id="b237e-126">Abort</span></span>

<span data-ttu-id="b237e-127">De huidige actie afbreken, bijvoorbeeld een incrementele geschiedenis zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="b237e-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="b237e-128">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="b237e-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="b237e-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="b237e-129">AcceptAndGetNext</span></span>

<span data-ttu-id="b237e-130">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="b237e-130">Attempt to execute the current input.</span></span> <span data-ttu-id="b237e-131">Als deze kan worden uitgevoerd (zoals AcceptLine), kunt u het volgende item uit de geschiedenis intrekken de volgende keer dat ReadLine wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b237e-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="b237e-132">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="b237e-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="b237e-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="b237e-133">AcceptLine</span></span>

<span data-ttu-id="b237e-134">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="b237e-134">Attempt to execute the current input.</span></span> <span data-ttu-id="b237e-135">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="b237e-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="b237e-136">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b237e-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="b237e-137">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b237e-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="b237e-138">VI Invoeg modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b237e-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="b237e-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="b237e-139">AddLine</span></span>

<span data-ttu-id="b237e-140">De vervolg prompt wordt weer gegeven op de volgende regel en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="b237e-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="b237e-141">Dit is handig om invoer in meerdere regels als één opdracht in te voeren, zelfs wanneer één regel volledig wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="b237e-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="b237e-142">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b237e-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b237e-143">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b237e-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b237e-144">VI Invoeg modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b237e-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b237e-145">VI-opdracht modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b237e-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="b237e-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="b237e-146">BackwardDeleteChar</span></span>

<span data-ttu-id="b237e-147">Verwijder het teken voor de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="b237e-148">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="b237e-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="b237e-149">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="b237e-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="b237e-150">VI Invoeg modus: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b237e-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="b237e-151">VI-opdracht modus: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="b237e-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="b237e-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="b237e-152">BackwardDeleteLine</span></span>

<span data-ttu-id="b237e-153">Net als BackwardKillLine: verwijdert tekst van het punt naar het begin van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="b237e-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="b237e-154">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b237e-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="b237e-155">VI Invoeg modus: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b237e-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="b237e-156">VI-opdracht modus: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="b237e-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="b237e-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="b237e-157">BackwardDeleteWord</span></span>

<span data-ttu-id="b237e-158">Hiermee verwijdert u het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-158">Deletes the previous word.</span></span>

- <span data-ttu-id="b237e-159">VI-opdracht modus: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="b237e-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="b237e-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="b237e-160">BackwardKillLine</span></span>

<span data-ttu-id="b237e-161">De invoer van het begin van de invoer wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="b237e-162">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="b237e-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b237e-163">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b237e-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="b237e-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="b237e-164">BackwardKillWord</span></span>

<span data-ttu-id="b237e-165">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b237e-166">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="b237e-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b237e-167">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="b237e-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b237e-168">Cmd: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="b237e-168">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="b237e-169">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b237e-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="b237e-170">VI Invoeg modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b237e-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="b237e-171">VI-opdracht modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b237e-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="b237e-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="b237e-172">CancelLine</span></span>

<span data-ttu-id="b237e-173">De huidige invoer annuleren, waardoor de invoer op het scherm wordt weer gegeven, maar terugkeert naar de host, zodat de prompt opnieuw wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="b237e-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="b237e-174">VI Invoeg modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b237e-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="b237e-175">VI-opdracht modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b237e-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="b237e-176">Kopiëren</span><span class="sxs-lookup"><span data-stu-id="b237e-176">Copy</span></span>

<span data-ttu-id="b237e-177">Kopieer de geselecteerde regio naar het klem bord van het systeem.</span><span class="sxs-lookup"><span data-stu-id="b237e-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="b237e-178">Als er geen regio is geselecteerd, kopieert u de hele regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="b237e-179">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="b237e-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="b237e-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="b237e-180">CopyOrCancelLine</span></span>

<span data-ttu-id="b237e-181">Als tekst is geselecteerd, kopieert u deze naar het klem bord. anders annuleert u de regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="b237e-182">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b237e-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="b237e-183">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b237e-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="b237e-184">Knippen</span><span class="sxs-lookup"><span data-stu-id="b237e-184">Cut</span></span>

<span data-ttu-id="b237e-185">Geselecteerde regio verwijderen Verwijderde tekst in het systeem Klembord plaatsen.</span><span class="sxs-lookup"><span data-stu-id="b237e-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="b237e-186">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="b237e-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="b237e-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="b237e-187">DeleteChar</span></span>

<span data-ttu-id="b237e-188">Verwijder het teken onder de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="b237e-189">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b237e-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="b237e-190">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b237e-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="b237e-191">VI Invoeg modus: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b237e-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="b237e-192">VI-opdracht modus: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b237e-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="b237e-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="b237e-193">DeleteCharOrExit</span></span>

<span data-ttu-id="b237e-194">Verwijder het teken onder de cursor of als de regel leeg is, sluit u het proces.</span><span class="sxs-lookup"><span data-stu-id="b237e-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="b237e-195">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b237e-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="b237e-196">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="b237e-196">DeleteEndOfBuffer</span></span>

<span data-ttu-id="b237e-197">Hiermee verwijdert u aan het einde van de buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="b237e-197">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="b237e-198">VI-opdracht modus: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="b237e-198">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="b237e-199">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="b237e-199">DeleteEndOfWord</span></span>

<span data-ttu-id="b237e-200">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-200">Delete to the end of the word.</span></span>

- <span data-ttu-id="b237e-201">VI-opdracht modus: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="b237e-201">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="b237e-202">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="b237e-202">DeleteLine</span></span>

<span data-ttu-id="b237e-203">Hiermee verwijdert u de huidige logische lijn van een buffer voor meerdere regels, waarbij u ongedaan maken inschakelt.</span><span class="sxs-lookup"><span data-stu-id="b237e-203">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="b237e-204">VI-opdracht modus: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="b237e-204">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="b237e-205">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="b237e-205">DeletePreviousLines</span></span>

<span data-ttu-id="b237e-206">Hiermee verwijdert u de vorige aangevraagde logische regels en de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="b237e-206">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="b237e-207">VI-opdracht modus: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="b237e-207">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="b237e-208">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="b237e-208">DeleteRelativeLines</span></span>

<span data-ttu-id="b237e-209">Verwijdert uit het begin van de buffer naar de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="b237e-209">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="b237e-210">De meeste MS-DOS-opdrachten `<d,g,g>` kunnen worden voorafgegaan door een numeriek argument waarmee een absoluut regel nummer wordt opgegeven, samen met het huidige regel nummer, een bereik aan regels maken dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b237e-210">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="b237e-211">Als u niets opgeeft, wordt het numerieke argument standaard ingesteld op 1, dat verwijst naar de eerste logische lijn in een buffer met meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="b237e-211">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="b237e-212">Het werkelijke aantal regels dat uit de meerregelige moet worden verwijderd, wordt berekend als het verschil tussen het huidige logische regel nummer en het opgegeven numerieke argument. Dit kan dus negatief zijn.</span><span class="sxs-lookup"><span data-stu-id="b237e-212">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="b237e-213">Daarom is het _relatieve_ deel van de methode naam.</span><span class="sxs-lookup"><span data-stu-id="b237e-213">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="b237e-214">VI-opdracht modus: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="b237e-214">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="b237e-215">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="b237e-215">DeleteNextLines</span></span>

<span data-ttu-id="b237e-216">Hiermee verwijdert u de huidige logische lijn en de volgende aangevraagde logische regels in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="b237e-216">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="b237e-217">VI-opdracht modus: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="b237e-217">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="b237e-218">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="b237e-218">DeleteLineToFirstChar</span></span>

<span data-ttu-id="b237e-219">Hiermee wordt tekst van de cursor verwijderd naar het eerste niet-lege teken van de regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-219">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="b237e-220">VI-opdracht modus: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="b237e-220">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="b237e-221">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="b237e-221">DeleteToEnd</span></span>

<span data-ttu-id="b237e-222">Verwijderen tot aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-222">Delete to the end of the line.</span></span>

- <span data-ttu-id="b237e-223">VI-opdracht modus: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="b237e-223">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="b237e-224">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="b237e-224">DeleteWord</span></span>

<span data-ttu-id="b237e-225">Verwijder het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-225">Delete the next word.</span></span>

- <span data-ttu-id="b237e-226">VI-opdracht modus: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="b237e-226">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="b237e-227">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="b237e-227">ForwardDeleteLine</span></span>

<span data-ttu-id="b237e-228">Net als ForwardKillLine: verwijdert tekst van het punt naar het einde van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="b237e-228">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="b237e-229">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b237e-229">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="b237e-230">VI Invoeg modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b237e-230">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="b237e-231">VI-opdracht modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b237e-231">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="b237e-232">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="b237e-232">InsertLineAbove</span></span>

<span data-ttu-id="b237e-233">Er wordt een nieuwe lege regel gemaakt op de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="b237e-233">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="b237e-234">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-234">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="b237e-235">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b237e-235">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="b237e-236">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="b237e-236">InsertLineBelow</span></span>

<span data-ttu-id="b237e-237">Er wordt een nieuwe lege regel gemaakt onder de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="b237e-237">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="b237e-238">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-238">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="b237e-239">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b237e-239">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="b237e-240">InvertCase</span><span class="sxs-lookup"><span data-stu-id="b237e-240">InvertCase</span></span>

<span data-ttu-id="b237e-241">Het hoofdletter gebruik van het huidige teken omkeren en verplaatsen naar het volgende.</span><span class="sxs-lookup"><span data-stu-id="b237e-241">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="b237e-242">VI-opdracht modus: `<~>`</span><span class="sxs-lookup"><span data-stu-id="b237e-242">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="b237e-243">KillLine</span><span class="sxs-lookup"><span data-stu-id="b237e-243">KillLine</span></span>

<span data-ttu-id="b237e-244">De invoer wissen van de cursor tot het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="b237e-244">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="b237e-245">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="b237e-245">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b237e-246">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="b237e-246">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="b237e-247">KillRegion</span><span class="sxs-lookup"><span data-stu-id="b237e-247">KillRegion</span></span>

<span data-ttu-id="b237e-248">Beëindig de tekst tussen de cursor en de markering.</span><span class="sxs-lookup"><span data-stu-id="b237e-248">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="b237e-249">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-249">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="b237e-250">KillWord</span><span class="sxs-lookup"><span data-stu-id="b237e-250">KillWord</span></span>

<span data-ttu-id="b237e-251">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-251">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="b237e-252">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-252">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="b237e-253">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="b237e-253">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b237e-254">Cmd: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b237e-254">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="b237e-255">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="b237e-255">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="b237e-256">VI Invoeg modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b237e-256">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="b237e-257">VI-opdracht modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b237e-257">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="b237e-258">Plakken</span><span class="sxs-lookup"><span data-stu-id="b237e-258">Paste</span></span>

<span data-ttu-id="b237e-259">Tekst van het klem bord van het systeem plakken.</span><span class="sxs-lookup"><span data-stu-id="b237e-259">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="b237e-260">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="b237e-260">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="b237e-261">VI Invoeg modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="b237e-261">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="b237e-262">VI-opdracht modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="b237e-262">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b237e-263">Wanneer u de functie **Paste** gebruikt, wordt de volledige inhoud van de Klembord buffer geplakt in de invoer buffer van PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b237e-263">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="b237e-264">De invoer buffer wordt vervolgens door gegeven aan de Power shell-parser.</span><span class="sxs-lookup"><span data-stu-id="b237e-264">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="b237e-265">Invoer die met de **rechter muisknop op** de plak methode van de console toepassing wordt geplakt, wordt met één teken per keer naar de invoer buffer gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="b237e-265">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="b237e-266">De invoer buffer wordt door gegeven aan de parser wanneer een teken voor een nieuwe regel wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="b237e-266">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="b237e-267">Daarom wordt de invoer één regel tegelijk geparseerd.</span><span class="sxs-lookup"><span data-stu-id="b237e-267">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="b237e-268">Het verschil tussen plak methoden resulteert in een ander uitvoerings gedrag.</span><span class="sxs-lookup"><span data-stu-id="b237e-268">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="b237e-269">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="b237e-269">PasteAfter</span></span>

<span data-ttu-id="b237e-270">Plak het klem bord na de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="b237e-270">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="b237e-271">VI-opdracht modus: `<p>`</span><span class="sxs-lookup"><span data-stu-id="b237e-271">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="b237e-272">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="b237e-272">PasteBefore</span></span>

<span data-ttu-id="b237e-273">Plak het klem bord vóór de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="b237e-273">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="b237e-274">VI-opdracht modus: `<P>`</span><span class="sxs-lookup"><span data-stu-id="b237e-274">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="b237e-275">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="b237e-275">PrependAndAccept</span></span>

<span data-ttu-id="b237e-276">Laten voorafgaan door een ' # ' en accepteer de regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-276">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="b237e-277">VI-opdracht modus: `<#>`</span><span class="sxs-lookup"><span data-stu-id="b237e-277">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="b237e-278">Opnieuw uitvoeren</span><span class="sxs-lookup"><span data-stu-id="b237e-278">Redo</span></span>

<span data-ttu-id="b237e-279">Undo ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="b237e-279">Undo an undo.</span></span>

- <span data-ttu-id="b237e-280">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b237e-280">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="b237e-281">VI Invoeg modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b237e-281">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="b237e-282">VI-opdracht modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b237e-282">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="b237e-283">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="b237e-283">RepeatLastCommand</span></span>

<span data-ttu-id="b237e-284">Herhaal de laatste tekst wijziging.</span><span class="sxs-lookup"><span data-stu-id="b237e-284">Repeat the last text modification.</span></span>

- <span data-ttu-id="b237e-285">VI-opdracht modus: `<.>`</span><span class="sxs-lookup"><span data-stu-id="b237e-285">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="b237e-286">RevertLine</span><span class="sxs-lookup"><span data-stu-id="b237e-286">RevertLine</span></span>

<span data-ttu-id="b237e-287">Hiermee wordt alle invoer teruggezet naar de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="b237e-287">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="b237e-288">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="b237e-288">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="b237e-289">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="b237e-289">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="b237e-290">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="b237e-290">ShellBackwardKillWord</span></span>

<span data-ttu-id="b237e-291">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-291">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b237e-292">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="b237e-292">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b237e-293">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="b237e-293">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="b237e-294">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-294">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="b237e-295">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="b237e-295">ShellKillWord</span></span>

<span data-ttu-id="b237e-296">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-296">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="b237e-297">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-297">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="b237e-298">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="b237e-298">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="b237e-299">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-299">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="b237e-300">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="b237e-300">SwapCharacters</span></span>

<span data-ttu-id="b237e-301">Het huidige teken en de eerste vervangen door wisselen.</span><span class="sxs-lookup"><span data-stu-id="b237e-301">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="b237e-302">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b237e-302">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="b237e-303">VI Invoeg modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b237e-303">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="b237e-304">VI-opdracht modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b237e-304">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="b237e-305">Ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="b237e-305">Undo</span></span>

<span data-ttu-id="b237e-306">Een vorige bewerking ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="b237e-306">Undo a previous edit.</span></span>

- <span data-ttu-id="b237e-307">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="b237e-307">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="b237e-308">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="b237e-308">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="b237e-309">VI Invoeg modus: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="b237e-309">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="b237e-310">VI-opdracht modus: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="b237e-310">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="b237e-311">UndoAll</span><span class="sxs-lookup"><span data-stu-id="b237e-311">UndoAll</span></span>

<span data-ttu-id="b237e-312">Alle vorige bewerkingen voor de regel ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="b237e-312">Undo all previous edits for line.</span></span>

- <span data-ttu-id="b237e-313">VI-opdracht modus: `<U>`</span><span class="sxs-lookup"><span data-stu-id="b237e-313">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="b237e-314">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="b237e-314">UnixWordRubout</span></span>

<span data-ttu-id="b237e-315">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-315">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b237e-316">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="b237e-316">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b237e-317">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="b237e-317">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b237e-318">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="b237e-318">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="b237e-319">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="b237e-319">ValidateAndAcceptLine</span></span>

<span data-ttu-id="b237e-320">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="b237e-320">Attempt to execute the current input.</span></span> <span data-ttu-id="b237e-321">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="b237e-321">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="b237e-322">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="b237e-322">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="b237e-323">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="b237e-323">ViAcceptLine</span></span>

<span data-ttu-id="b237e-324">Accepteer de regel en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="b237e-324">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="b237e-325">VI-opdracht modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b237e-325">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="b237e-326">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="b237e-326">ViAcceptLineOrExit</span></span>

<span data-ttu-id="b237e-327">Als DeleteCharOrExit in de Emacs-modus, maar wel in plaats van een teken te verwijderen, accepteert u de regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-327">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="b237e-328">VI Invoeg modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b237e-328">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="b237e-329">VI-opdracht modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b237e-329">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="b237e-330">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="b237e-330">ViAppendLine</span></span>

<span data-ttu-id="b237e-331">Er wordt een nieuwe regel ingevoegd onder de huidige regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-331">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="b237e-332">VI-opdracht modus: `<o>`</span><span class="sxs-lookup"><span data-stu-id="b237e-332">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="b237e-333">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="b237e-333">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="b237e-334">Hiermee verwijdert u het vorige woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-334">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="b237e-335">VI-opdracht modus: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="b237e-335">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="b237e-336">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="b237e-336">ViBackwardGlob</span></span>

<span data-ttu-id="b237e-337">Verplaatst de cursor terug naar het begin van het vorige woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b237e-337">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="b237e-338">VI-opdracht modus: `<B>`</span><span class="sxs-lookup"><span data-stu-id="b237e-338">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="b237e-339">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="b237e-339">ViDeleteBrace</span></span>

<span data-ttu-id="b237e-340">Zoek de accolade, het haakje sluiten of de vier Kante haken en verwijder alle inhoud binnen, inclusief de accolade.</span><span class="sxs-lookup"><span data-stu-id="b237e-340">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="b237e-341">VI-opdracht modus: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="b237e-341">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="b237e-342">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b237e-342">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="b237e-343">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-343">Delete to the end of the word.</span></span>

- <span data-ttu-id="b237e-344">VI-opdracht modus: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="b237e-344">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="b237e-345">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="b237e-345">ViDeleteGlob</span></span>

<span data-ttu-id="b237e-346">De volgende Globs verwijderen (door witruimte gescheiden woord).</span><span class="sxs-lookup"><span data-stu-id="b237e-346">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="b237e-347">VI-opdracht modus: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="b237e-347">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="b237e-348">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="b237e-348">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="b237e-349">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-349">Deletes until given character.</span></span>

- <span data-ttu-id="b237e-350">VI-opdracht modus: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="b237e-350">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="b237e-351">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="b237e-351">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="b237e-352">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-352">Deletes until given character.</span></span>

- <span data-ttu-id="b237e-353">VI-opdracht modus: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="b237e-353">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="b237e-354">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="b237e-354">ViDeleteToChar</span></span>

<span data-ttu-id="b237e-355">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-355">Deletes until given character.</span></span>

- <span data-ttu-id="b237e-356">VI-opdracht modus: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="b237e-356">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="b237e-357">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="b237e-357">ViDeleteToCharBackward</span></span>

<span data-ttu-id="b237e-358">Hiermee verwijdert u achterwaartse tekens tot aan het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-358">Deletes backwards until given character.</span></span>

- <span data-ttu-id="b237e-359">VI-opdracht modus: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="b237e-359">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="b237e-360">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="b237e-360">ViInsertAtBegining</span></span>

<span data-ttu-id="b237e-361">Schakel over naar de Invoeg modus en plaats de cursor aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-361">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="b237e-362">VI-opdracht modus: `<I>`</span><span class="sxs-lookup"><span data-stu-id="b237e-362">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="b237e-363">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="b237e-363">ViInsertAtEnd</span></span>

<span data-ttu-id="b237e-364">Schakel over naar de Invoeg modus en plaats de cursor aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-364">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="b237e-365">VI-opdracht modus: `<A>`</span><span class="sxs-lookup"><span data-stu-id="b237e-365">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="b237e-366">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="b237e-366">ViInsertLine</span></span>

<span data-ttu-id="b237e-367">Boven de huidige regel wordt een nieuwe regel ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="b237e-367">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="b237e-368">VI-opdracht modus: `<O>`</span><span class="sxs-lookup"><span data-stu-id="b237e-368">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="b237e-369">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="b237e-369">ViInsertWithAppend</span></span>

<span data-ttu-id="b237e-370">Toevoegen vanaf de huidige regel positie.</span><span class="sxs-lookup"><span data-stu-id="b237e-370">Append from the current line position.</span></span>

- <span data-ttu-id="b237e-371">VI-opdracht modus: `<a>`</span><span class="sxs-lookup"><span data-stu-id="b237e-371">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="b237e-372">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="b237e-372">ViInsertWithDelete</span></span>

<span data-ttu-id="b237e-373">Verwijder het huidige teken en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="b237e-373">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="b237e-374">VI-opdracht modus: `<s>`</span><span class="sxs-lookup"><span data-stu-id="b237e-374">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="b237e-375">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="b237e-375">ViJoinLines</span></span>

<span data-ttu-id="b237e-376">De huidige regel en de volgende regel worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="b237e-376">Joins the current line and the next line.</span></span>

- <span data-ttu-id="b237e-377">VI-opdracht modus: `<J>`</span><span class="sxs-lookup"><span data-stu-id="b237e-377">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="b237e-378">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="b237e-378">ViReplaceLine</span></span>

<span data-ttu-id="b237e-379">De volledige opdracht regel wissen.</span><span class="sxs-lookup"><span data-stu-id="b237e-379">Erase the entire command line.</span></span>

- <span data-ttu-id="b237e-380">VI-opdracht modus: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="b237e-380">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="b237e-381">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="b237e-381">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="b237e-382">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-382">Replaces until given character.</span></span>

- <span data-ttu-id="b237e-383">VI-opdracht modus: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="b237e-383">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="b237e-384">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="b237e-384">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="b237e-385">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-385">Replaces until given character.</span></span>

- <span data-ttu-id="b237e-386">VI-opdracht modus: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="b237e-386">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="b237e-387">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="b237e-387">ViReplaceToChar</span></span>

<span data-ttu-id="b237e-388">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-388">Deletes until given character.</span></span>

- <span data-ttu-id="b237e-389">VI-opdracht modus: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="b237e-389">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="b237e-390">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="b237e-390">ViReplaceToCharBackward</span></span>

<span data-ttu-id="b237e-391">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-391">Replaces until given character.</span></span>

- <span data-ttu-id="b237e-392">VI-opdracht modus: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="b237e-392">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="b237e-393">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="b237e-393">ViYankBeginningOfLine</span></span>

<span data-ttu-id="b237e-394">Yank vanaf het begin van de buffer naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-394">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="b237e-395">VI-opdracht modus: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="b237e-395">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="b237e-396">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b237e-396">ViYankEndOfGlob</span></span>

<span data-ttu-id="b237e-397">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="b237e-397">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="b237e-398">VI-opdracht modus: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="b237e-398">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="b237e-399">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="b237e-399">ViYankEndOfWord</span></span>

<span data-ttu-id="b237e-400">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="b237e-400">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="b237e-401">VI-opdracht modus: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="b237e-401">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="b237e-402">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="b237e-402">ViYankLeft</span></span>

<span data-ttu-id="b237e-403">Yank teken (s) links van de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-403">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="b237e-404">VI-opdracht modus: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="b237e-404">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="b237e-405">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="b237e-405">ViYankLine</span></span>

<span data-ttu-id="b237e-406">Yank de volledige buffer.</span><span class="sxs-lookup"><span data-stu-id="b237e-406">Yank the entire buffer.</span></span>

- <span data-ttu-id="b237e-407">VI-opdracht modus: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="b237e-407">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="b237e-408">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="b237e-408">ViYankNextGlob</span></span>

<span data-ttu-id="b237e-409">Yank van de cursor naar het begin van de volgende woord (en).</span><span class="sxs-lookup"><span data-stu-id="b237e-409">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="b237e-410">VI-opdracht modus: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="b237e-410">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="b237e-411">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="b237e-411">ViYankNextWord</span></span>

<span data-ttu-id="b237e-412">Yank het woord (en) na de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-412">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="b237e-413">VI-opdracht modus: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="b237e-413">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="b237e-414">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="b237e-414">ViYankPercent</span></span>

<span data-ttu-id="b237e-415">Yank naar/van overeenkomende accolade.</span><span class="sxs-lookup"><span data-stu-id="b237e-415">Yank to/from matching brace.</span></span>

- <span data-ttu-id="b237e-416">VI-opdracht modus: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="b237e-416">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="b237e-417">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="b237e-417">ViYankPreviousGlob</span></span>

<span data-ttu-id="b237e-418">Yank vanaf het begin van het (de) woord (en) tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-418">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="b237e-419">VI-opdracht modus: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="b237e-419">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="b237e-420">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="b237e-420">ViYankPreviousWord</span></span>

<span data-ttu-id="b237e-421">Yank de woorden vóór de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-421">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="b237e-422">VI-opdracht modus: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="b237e-422">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="b237e-423">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="b237e-423">ViYankRight</span></span>

<span data-ttu-id="b237e-424">Yank teken (s) onder en rechts van de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-424">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="b237e-425">VI-opdracht modus: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b237e-425">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="b237e-426">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="b237e-426">ViYankToEndOfLine</span></span>

<span data-ttu-id="b237e-427">Yank van de cursor tot het einde van de buffer.</span><span class="sxs-lookup"><span data-stu-id="b237e-427">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="b237e-428">VI-opdracht modus: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="b237e-428">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="b237e-429">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="b237e-429">ViYankToFirstChar</span></span>

<span data-ttu-id="b237e-430">Yank van het eerste niet-spatie teken tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-430">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="b237e-431">VI-opdracht modus: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="b237e-431">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="b237e-432">Yank</span><span class="sxs-lookup"><span data-stu-id="b237e-432">Yank</span></span>

<span data-ttu-id="b237e-433">Voeg de meest recent afgebroken tekst toe aan de invoer.</span><span class="sxs-lookup"><span data-stu-id="b237e-433">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="b237e-434">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b237e-434">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="b237e-435">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="b237e-435">YankLastArg</span></span>

<span data-ttu-id="b237e-436">Yank het laatste argument van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-436">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="b237e-437">Met een argument, de eerste keer dat deze wordt aangeroepen, gedraagt zich op dezelfde manier als YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="b237e-437">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="b237e-438">Als meerdere keren worden aangeroepen, wordt door de geschiedenis en ARG de richting ingesteld (negatief de richting omkeren.)</span><span class="sxs-lookup"><span data-stu-id="b237e-438">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="b237e-439">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="b237e-439">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="b237e-440">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="b237e-440">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="b237e-441">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="b237e-441">YankNthArg</span></span>

<span data-ttu-id="b237e-442">Yank het eerste argument (na de opdracht) van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-442">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="b237e-443">Met een argument, Yank het ne argument (vanaf 0), als het argument negatief is, begint vanaf het laatste argument.</span><span class="sxs-lookup"><span data-stu-id="b237e-443">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="b237e-444">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b237e-444">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="b237e-445">YankPop</span><span class="sxs-lookup"><span data-stu-id="b237e-445">YankPop</span></span>

<span data-ttu-id="b237e-446">Als de vorige bewerking Yank of YankPop is, vervangt u de eerder yanked tekst door de volgende afgebroken tekst van de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="b237e-446">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="b237e-447">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="b237e-447">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="b237e-448">Functies voor cursor verplaatsing</span><span class="sxs-lookup"><span data-stu-id="b237e-448">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="b237e-449">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="b237e-449">BackwardChar</span></span>

<span data-ttu-id="b237e-450">De cursor één teken naar links verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="b237e-450">Move the cursor one character to the left.</span></span> <span data-ttu-id="b237e-451">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="b237e-451">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="b237e-452">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-452">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="b237e-453">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="b237e-453">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="b237e-454">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="b237e-454">BackwardWord</span></span>

<span data-ttu-id="b237e-455">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-455">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b237e-456">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="b237e-456">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b237e-457">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-457">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b237e-458">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="b237e-458">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="b237e-459">VI Invoeg modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-459">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b237e-460">VI-opdracht modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-460">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="b237e-461">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="b237e-461">BeginningOfLine</span></span>

<span data-ttu-id="b237e-462">Als de invoer meerdere regels heeft, gaat u naar het begin van de huidige regel of gaat u naar het begin van de invoer als deze al aan het begin van de regel staat.</span><span class="sxs-lookup"><span data-stu-id="b237e-462">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="b237e-463">Als de invoer één regel heeft, gaat u naar het begin van de invoer.</span><span class="sxs-lookup"><span data-stu-id="b237e-463">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="b237e-464">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b237e-464">Cmd: `<Home>`</span></span>
- <span data-ttu-id="b237e-465">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="b237e-465">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="b237e-466">VI Invoeg modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b237e-466">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="b237e-467">VI-opdracht modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b237e-467">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="b237e-468">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="b237e-468">EndOfLine</span></span>

<span data-ttu-id="b237e-469">Als de invoer meerdere regels heeft, gaat u naar het einde van de huidige regel of gaat u naar het einde van de invoer als u aan het einde van de regel bent.</span><span class="sxs-lookup"><span data-stu-id="b237e-469">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="b237e-470">Als de invoer één regel heeft, gaat u naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="b237e-470">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="b237e-471">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="b237e-471">Cmd: `<End>`</span></span>
- <span data-ttu-id="b237e-472">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="b237e-472">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="b237e-473">VI Invoeg modus: `<End>`</span><span class="sxs-lookup"><span data-stu-id="b237e-473">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="b237e-474">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="b237e-474">ForwardChar</span></span>

<span data-ttu-id="b237e-475">De cursor één teken naar rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="b237e-475">Move the cursor one character to the right.</span></span> <span data-ttu-id="b237e-476">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="b237e-476">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="b237e-477">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-477">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="b237e-478">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="b237e-478">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="b237e-479">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="b237e-479">ForwardWord</span></span>

<span data-ttu-id="b237e-480">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-480">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b237e-481">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="b237e-481">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b237e-482">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="b237e-482">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="b237e-483">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="b237e-483">GotoBrace</span></span>

<span data-ttu-id="b237e-484">Ga naar de accolade, haakjes of vier Kante haakjes.</span><span class="sxs-lookup"><span data-stu-id="b237e-484">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="b237e-485">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b237e-485">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b237e-486">VI Invoeg modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b237e-486">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b237e-487">VI-opdracht modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b237e-487">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="b237e-488">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="b237e-488">GotoColumn</span></span>

<span data-ttu-id="b237e-489">Ga naar de kolom die wordt aangegeven door arg.</span><span class="sxs-lookup"><span data-stu-id="b237e-489">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="b237e-490">VI-opdracht modus: `<|>`</span><span class="sxs-lookup"><span data-stu-id="b237e-490">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="b237e-491">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="b237e-491">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="b237e-492">De cursor verplaatsen naar het eerste niet-lege teken in de regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-492">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="b237e-493">VI-opdracht modus: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="b237e-493">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="b237e-494">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="b237e-494">MoveToEndOfLine</span></span>

<span data-ttu-id="b237e-495">De cursor verplaatsen naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="b237e-495">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="b237e-496">VI-opdracht modus: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="b237e-496">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="b237e-497">NextLine</span><span class="sxs-lookup"><span data-stu-id="b237e-497">NextLine</span></span>

<span data-ttu-id="b237e-498">De cursor verplaatsen naar de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-498">Move the cursor to the next line.</span></span>

- <span data-ttu-id="b237e-499">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-499">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="b237e-500">NextWord</span><span class="sxs-lookup"><span data-stu-id="b237e-500">NextWord</span></span>

<span data-ttu-id="b237e-501">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-501">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b237e-502">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="b237e-502">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b237e-503">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-503">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="b237e-504">VI Invoeg modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-504">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="b237e-505">VI-opdracht modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-505">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="b237e-506">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="b237e-506">NextWordEnd</span></span>

<span data-ttu-id="b237e-507">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-507">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b237e-508">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="b237e-508">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b237e-509">VI-opdracht modus: `<e>`</span><span class="sxs-lookup"><span data-stu-id="b237e-509">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="b237e-510">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="b237e-510">PreviousLine</span></span>

<span data-ttu-id="b237e-511">Verplaats de cursor naar de vorige regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-511">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="b237e-512">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-512">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="b237e-513">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b237e-513">ShellBackwardWord</span></span>

<span data-ttu-id="b237e-514">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b237e-515">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="b237e-515">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b237e-516">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-516">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="b237e-517">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="b237e-517">ShellForwardWord</span></span>

<span data-ttu-id="b237e-518">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-518">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b237e-519">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="b237e-519">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b237e-520">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-520">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="b237e-521">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="b237e-521">ShellNextWord</span></span>

<span data-ttu-id="b237e-522">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-522">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b237e-523">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="b237e-523">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b237e-524">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-524">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="b237e-525">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="b237e-525">ViBackwardChar</span></span>

<span data-ttu-id="b237e-526">De cursor één teken naar links verplaatsen in de bewerkings modus VI.</span><span class="sxs-lookup"><span data-stu-id="b237e-526">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="b237e-527">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="b237e-527">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="b237e-528">VI Invoeg modus: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-528">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="b237e-529">VI-opdracht modus: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="b237e-529">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="b237e-530">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b237e-530">ViBackwardWord</span></span>

<span data-ttu-id="b237e-531">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-531">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b237e-532">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="b237e-532">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b237e-533">VI-opdracht modus: `<b>`</span><span class="sxs-lookup"><span data-stu-id="b237e-533">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="b237e-534">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="b237e-534">ViForwardChar</span></span>

<span data-ttu-id="b237e-535">De cursor één teken naar rechts verplaatsen in de bewerkings modus VI.</span><span class="sxs-lookup"><span data-stu-id="b237e-535">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="b237e-536">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="b237e-536">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="b237e-537">VI Invoeg modus: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-537">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="b237e-538">VI-opdracht modus: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="b237e-538">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="b237e-539">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b237e-539">ViEndOfGlob</span></span>

<span data-ttu-id="b237e-540">Verplaatst de cursor naar het einde van het woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b237e-540">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="b237e-541">VI-opdracht modus: `<E>`</span><span class="sxs-lookup"><span data-stu-id="b237e-541">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="b237e-542">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="b237e-542">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="b237e-543">Wordt verplaatst naar het einde van het vorige woord, waarbij alleen witruimte wordt gebruikt als woord als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-543">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="b237e-544">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-544">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="b237e-545">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="b237e-545">ViGotoBrace</span></span>

<span data-ttu-id="b237e-546">Vergelijkbaar met GotoBrace, maar is in plaats van op tokens gebaseerd.</span><span class="sxs-lookup"><span data-stu-id="b237e-546">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="b237e-547">VI-opdracht modus: `<%>`</span><span class="sxs-lookup"><span data-stu-id="b237e-547">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="b237e-548">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="b237e-548">ViNextGlob</span></span>

<span data-ttu-id="b237e-549">Verplaatst naar het volgende woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-549">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="b237e-550">VI-opdracht modus: `<W>`</span><span class="sxs-lookup"><span data-stu-id="b237e-550">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="b237e-551">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="b237e-551">ViNextWord</span></span>

<span data-ttu-id="b237e-552">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="b237e-552">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b237e-553">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="b237e-553">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b237e-554">VI-opdracht modus: `<w>`</span><span class="sxs-lookup"><span data-stu-id="b237e-554">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="b237e-555">Geschiedenis functies</span><span class="sxs-lookup"><span data-stu-id="b237e-555">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="b237e-556">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="b237e-556">BeginningOfHistory</span></span>

<span data-ttu-id="b237e-557">Hiermee gaat u naar het eerste item in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="b237e-557">Move to the first item in the history.</span></span>

- <span data-ttu-id="b237e-558">Emacs: `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="b237e-558">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="b237e-559">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="b237e-559">ClearHistory</span></span>

<span data-ttu-id="b237e-560">Hiermee wist u de geschiedenis in PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b237e-560">Clears history in PSReadLine.</span></span> <span data-ttu-id="b237e-561">Dit heeft geen invloed op de Power shell-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="b237e-561">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="b237e-562">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="b237e-562">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="b237e-563">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="b237e-563">EndOfHistory</span></span>

<span data-ttu-id="b237e-564">Hiermee gaat u naar het laatste item (de huidige invoer) in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="b237e-564">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="b237e-565">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="b237e-565">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="b237e-566">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="b237e-566">ForwardSearchHistory</span></span>

<span data-ttu-id="b237e-567">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="b237e-567">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="b237e-568">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b237e-568">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="b237e-569">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b237e-569">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="b237e-570">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="b237e-570">HistorySearchBackward</span></span>

<span data-ttu-id="b237e-571">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-571">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="b237e-572">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="b237e-572">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="b237e-573">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="b237e-573">HistorySearchForward</span></span>

<span data-ttu-id="b237e-574">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-574">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="b237e-575">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="b237e-575">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="b237e-576">NextHistory</span><span class="sxs-lookup"><span data-stu-id="b237e-576">NextHistory</span></span>

<span data-ttu-id="b237e-577">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="b237e-577">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="b237e-578">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-578">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="b237e-579">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="b237e-579">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="b237e-580">VI Invoeg modus: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-580">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="b237e-581">VI-opdracht modus: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="b237e-581">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="b237e-582">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="b237e-582">PreviousHistory</span></span>

<span data-ttu-id="b237e-583">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="b237e-583">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="b237e-584">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-584">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="b237e-585">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="b237e-585">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="b237e-586">VI Invoeg modus: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-586">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="b237e-587">VI-opdracht modus: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="b237e-587">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="b237e-588">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="b237e-588">ReverseSearchHistory</span></span>

<span data-ttu-id="b237e-589">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="b237e-589">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="b237e-590">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b237e-590">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="b237e-591">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b237e-591">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="b237e-592">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="b237e-592">ViSearchHistoryBackward</span></span>

<span data-ttu-id="b237e-593">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="b237e-593">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="b237e-594">VI Invoeg modus: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b237e-594">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="b237e-595">VI-opdracht modus: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b237e-595">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="b237e-596">Voltooiings functies</span><span class="sxs-lookup"><span data-stu-id="b237e-596">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="b237e-597">Voltooid</span><span class="sxs-lookup"><span data-stu-id="b237e-597">Complete</span></span>

<span data-ttu-id="b237e-598">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-598">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="b237e-599">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="b237e-599">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="b237e-600">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b237e-600">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="b237e-601">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b237e-601">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="b237e-602">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="b237e-602">MenuComplete</span></span>

<span data-ttu-id="b237e-603">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-603">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="b237e-604">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="b237e-604">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="b237e-605">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b237e-605">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="b237e-606">Cmd: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b237e-606">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="b237e-607">Emacs: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b237e-607">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="b237e-608">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="b237e-608">PossibleCompletions</span></span>

<span data-ttu-id="b237e-609">De lijst met mogelijke aanvullingen weer geven.</span><span class="sxs-lookup"><span data-stu-id="b237e-609">Display the list of possible completions.</span></span>

- <span data-ttu-id="b237e-610">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="b237e-610">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="b237e-611">VI Invoeg modus: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b237e-611">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="b237e-612">VI-opdracht modus: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b237e-612">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="b237e-613">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="b237e-613">TabCompleteNext</span></span>

<span data-ttu-id="b237e-614">Poging om de tekst rond de cursor te volt ooien met de volgende beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="b237e-614">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="b237e-615">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b237e-615">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="b237e-616">VI-opdracht modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b237e-616">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="b237e-617">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="b237e-617">TabCompletePrevious</span></span>

<span data-ttu-id="b237e-618">Poging om de tekst rond de cursor te volt ooien met de vorige beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="b237e-618">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="b237e-619">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b237e-619">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="b237e-620">VI-opdracht modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b237e-620">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="b237e-621">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="b237e-621">ViTabCompleteNext</span></span>

<span data-ttu-id="b237e-622">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompleteNext aan.</span><span class="sxs-lookup"><span data-stu-id="b237e-622">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="b237e-623">VI Invoeg modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b237e-623">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="b237e-624">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="b237e-624">ViTabCompletePrevious</span></span>

<span data-ttu-id="b237e-625">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompletePrevious aan.</span><span class="sxs-lookup"><span data-stu-id="b237e-625">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="b237e-626">VI Invoeg modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b237e-626">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="b237e-627">Diverse functies</span><span class="sxs-lookup"><span data-stu-id="b237e-627">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="b237e-628">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="b237e-628">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="b237e-629">Het volgende woord van de inline of geselecteerde suggestie accepteren.</span><span class="sxs-lookup"><span data-stu-id="b237e-629">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="b237e-630">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-630">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="b237e-631">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="b237e-631">AcceptSuggestion</span></span>

<span data-ttu-id="b237e-632">De huidige inline of geselecteerde suggestie accepteren.</span><span class="sxs-lookup"><span data-stu-id="b237e-632">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="b237e-633">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-633">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="b237e-634">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="b237e-634">CaptureScreen</span></span>

<span data-ttu-id="b237e-635">Interactieve scherm opname starten-pijl-omhoog/omlaag Selecteer regels en voer de geselecteerde tekst als tekst en HTML naar het klem bord kopiëren.</span><span class="sxs-lookup"><span data-stu-id="b237e-635">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="b237e-636">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-636">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="b237e-637">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="b237e-637">ClearScreen</span></span>

<span data-ttu-id="b237e-638">Schakel het scherm uit en teken de huidige regel boven aan het scherm.</span><span class="sxs-lookup"><span data-stu-id="b237e-638">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="b237e-639">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b237e-639">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b237e-640">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b237e-640">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b237e-641">VI Invoeg modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b237e-641">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b237e-642">VI-opdracht modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b237e-642">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="b237e-643">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="b237e-643">DigitArgument</span></span>

<span data-ttu-id="b237e-644">Start een nieuw cijfer argument om door te geven aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="b237e-644">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="b237e-645">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="b237e-645">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="b237e-646">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="b237e-646">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="b237e-647">VI-opdracht modus: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="b237e-647">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="b237e-648">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="b237e-648">InvokePrompt</span></span>

<span data-ttu-id="b237e-649">Hiermee wordt de huidige prompt gewist en wordt de functie Prompt aangeroepen om de prompt opnieuw weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b237e-649">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="b237e-650">Dit is handig voor aangepaste sleutel afhandelingen die de status wijzigen, bijvoorbeeld de huidige map wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b237e-650">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="b237e-651">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-651">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="b237e-652">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="b237e-652">ScrollDisplayDown</span></span>

<span data-ttu-id="b237e-653">De weer gave één scherm omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="b237e-653">Scroll the display down one screen.</span></span>

- <span data-ttu-id="b237e-654">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b237e-654">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="b237e-655">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b237e-655">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="b237e-656">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="b237e-656">ScrollDisplayDownLine</span></span>

<span data-ttu-id="b237e-657">De weer gave één regel omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="b237e-657">Scroll the display down one line.</span></span>

- <span data-ttu-id="b237e-658">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b237e-658">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="b237e-659">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b237e-659">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="b237e-660">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="b237e-660">ScrollDisplayToCursor</span></span>

<span data-ttu-id="b237e-661">Schuif de weer gave naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-661">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="b237e-662">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b237e-662">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="b237e-663">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="b237e-663">ScrollDisplayTop</span></span>

<span data-ttu-id="b237e-664">Schuif de weer gave naar boven.</span><span class="sxs-lookup"><span data-stu-id="b237e-664">Scroll the display to the top.</span></span>

- <span data-ttu-id="b237e-665">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b237e-665">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="b237e-666">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="b237e-666">ScrollDisplayUp</span></span>

<span data-ttu-id="b237e-667">Schuif de weer gave één scherm omhoog.</span><span class="sxs-lookup"><span data-stu-id="b237e-667">Scroll the display up one screen.</span></span>

- <span data-ttu-id="b237e-668">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b237e-668">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="b237e-669">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b237e-669">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="b237e-670">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="b237e-670">ScrollDisplayUpLine</span></span>

<span data-ttu-id="b237e-671">De weer gave één regel omhoog schuiven.</span><span class="sxs-lookup"><span data-stu-id="b237e-671">Scroll the display up one line.</span></span>

- <span data-ttu-id="b237e-672">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b237e-672">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="b237e-673">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b237e-673">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="b237e-674">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="b237e-674">SelfInsert</span></span>

<span data-ttu-id="b237e-675">Voeg de sleutel in.</span><span class="sxs-lookup"><span data-stu-id="b237e-675">Insert the key.</span></span>

- <span data-ttu-id="b237e-676">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-676">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="b237e-677">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="b237e-677">ShowKeyBindings</span></span>

<span data-ttu-id="b237e-678">Alle gebonden sleutels weer geven.</span><span class="sxs-lookup"><span data-stu-id="b237e-678">Show all bound keys.</span></span>

- <span data-ttu-id="b237e-679">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b237e-679">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="b237e-680">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b237e-680">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="b237e-681">VI Invoeg modus: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b237e-681">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="b237e-682">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="b237e-682">ViCommandMode</span></span>

<span data-ttu-id="b237e-683">Schakel de huidige bedrijfs modus uit van Vi-Insert naar de VI-opdracht.</span><span class="sxs-lookup"><span data-stu-id="b237e-683">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="b237e-684">VI Invoeg modus: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="b237e-684">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="b237e-685">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="b237e-685">ViDigitArgumentInChord</span></span>

<span data-ttu-id="b237e-686">Start een nieuw cijfer argument om door te geven aan andere functies in een van de koorden van VI.</span><span class="sxs-lookup"><span data-stu-id="b237e-686">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="b237e-687">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-687">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="b237e-688">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="b237e-688">ViEditVisually</span></span>

<span data-ttu-id="b237e-689">Bewerk de opdracht regel in een tekst editor die is opgegeven door $env: EDITOR of $env: VISUAL.</span><span class="sxs-lookup"><span data-stu-id="b237e-689">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="b237e-690">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="b237e-690">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="b237e-691">VI-opdracht modus: `<v>`</span><span class="sxs-lookup"><span data-stu-id="b237e-691">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="b237e-692">ViExit</span><span class="sxs-lookup"><span data-stu-id="b237e-692">ViExit</span></span>

<span data-ttu-id="b237e-693">Hiermee wordt de shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="b237e-693">Exits the shell.</span></span>

- <span data-ttu-id="b237e-694">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-694">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="b237e-695">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="b237e-695">ViInsertMode</span></span>

<span data-ttu-id="b237e-696">Schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="b237e-696">Switch to Insert mode.</span></span>

- <span data-ttu-id="b237e-697">VI-opdracht modus: `<i>`</span><span class="sxs-lookup"><span data-stu-id="b237e-697">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="b237e-698">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="b237e-698">WhatIsKey</span></span>

<span data-ttu-id="b237e-699">Lees een sleutel en vertel me wat de sleutel is gebonden.</span><span class="sxs-lookup"><span data-stu-id="b237e-699">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="b237e-700">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b237e-700">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="b237e-701">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b237e-701">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="b237e-702">Selectie functies</span><span class="sxs-lookup"><span data-stu-id="b237e-702">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="b237e-703">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="b237e-703">ExchangePointAndMark</span></span>

<span data-ttu-id="b237e-704">De cursor wordt op de locatie van het merk geplaatst en het vinkje wordt verplaatst naar de locatie van de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-704">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="b237e-705">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="b237e-705">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="b237e-706">SelectAll aanroepen</span><span class="sxs-lookup"><span data-stu-id="b237e-706">SelectAll</span></span>

<span data-ttu-id="b237e-707">Selecteer de volledige regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-707">Select the entire line.</span></span>

- <span data-ttu-id="b237e-708">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="b237e-708">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="b237e-709">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="b237e-709">SelectBackwardChar</span></span>

<span data-ttu-id="b237e-710">Pas de huidige selectie aan om het vorige teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="b237e-710">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="b237e-711">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-711">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="b237e-712">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-712">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="b237e-713">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="b237e-713">SelectBackwardsLine</span></span>

<span data-ttu-id="b237e-714">Pas de huidige selectie aan de cursor toe aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-714">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="b237e-715">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="b237e-715">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="b237e-716">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="b237e-716">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="b237e-717">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b237e-717">SelectBackwardWord</span></span>

<span data-ttu-id="b237e-718">Pas de huidige selectie aan om het vorige woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="b237e-718">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="b237e-719">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-719">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b237e-720">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="b237e-720">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="b237e-721">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="b237e-721">SelectForwardChar</span></span>

<span data-ttu-id="b237e-722">Pas de huidige selectie aan om het volgende teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="b237e-722">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="b237e-723">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-723">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="b237e-724">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-724">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="b237e-725">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="b237e-725">SelectForwardWord</span></span>

<span data-ttu-id="b237e-726">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="b237e-726">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="b237e-727">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="b237e-727">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="b237e-728">SelectLine</span><span class="sxs-lookup"><span data-stu-id="b237e-728">SelectLine</span></span>

<span data-ttu-id="b237e-729">Pas de huidige selectie aan de cursor toe aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-729">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="b237e-730">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="b237e-730">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="b237e-731">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="b237e-731">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="b237e-732">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="b237e-732">SelectNextWord</span></span>

<span data-ttu-id="b237e-733">Pas de huidige selectie aan om het volgende woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="b237e-733">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="b237e-734">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b237e-734">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="b237e-735">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b237e-735">SelectShellBackwardWord</span></span>

<span data-ttu-id="b237e-736">Pas de huidige selectie aan om het vorige woord op te maken met behulp van ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="b237e-736">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="b237e-737">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-737">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="b237e-738">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="b237e-738">SelectShellForwardWord</span></span>

<span data-ttu-id="b237e-739">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="b237e-739">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="b237e-740">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-740">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="b237e-741">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="b237e-741">SelectShellNextWord</span></span>

<span data-ttu-id="b237e-742">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="b237e-742">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="b237e-743">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="b237e-743">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="b237e-744">SetMark</span><span class="sxs-lookup"><span data-stu-id="b237e-744">SetMark</span></span>

<span data-ttu-id="b237e-745">De huidige locatie van de cursor markeren voor gebruik in een volgende bewerkings opdracht.</span><span class="sxs-lookup"><span data-stu-id="b237e-745">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="b237e-746">Emacs: `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="b237e-746">Emacs: `<Ctrl+@>`</span></span>

## <a name="search-functions"></a><span data-ttu-id="b237e-747">Zoek functies</span><span class="sxs-lookup"><span data-stu-id="b237e-747">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="b237e-748">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="b237e-748">CharacterSearch</span></span>

<span data-ttu-id="b237e-749">Lees een teken en zoek voorwaarts naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-749">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="b237e-750">Als er een argument is opgegeven, zoekt u voorwaarts (of achterwaarts als negatieve) voor het ne voorval.</span><span class="sxs-lookup"><span data-stu-id="b237e-750">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="b237e-751">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b237e-751">Cmd: `<F3>`</span></span>
- <span data-ttu-id="b237e-752">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b237e-752">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b237e-753">VI Invoeg modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b237e-753">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="b237e-754">VI-opdracht modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b237e-754">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="b237e-755">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="b237e-755">CharacterSearchBackward</span></span>

<span data-ttu-id="b237e-756">Lees een teken en zoek terug naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-756">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="b237e-757">Als er een argument is opgegeven, zoekt u terug (of als dit negatief is) voor het ne exemplaar.</span><span class="sxs-lookup"><span data-stu-id="b237e-757">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="b237e-758">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b237e-758">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="b237e-759">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="b237e-759">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="b237e-760">VI Invoeg modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b237e-760">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="b237e-761">VI-opdracht modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b237e-761">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="b237e-762">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="b237e-762">RepeatLastCharSearch</span></span>

<span data-ttu-id="b237e-763">De laatst opgenomen zoek opdracht herhalen.</span><span class="sxs-lookup"><span data-stu-id="b237e-763">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="b237e-764">VI-opdracht modus: `<;>`</span><span class="sxs-lookup"><span data-stu-id="b237e-764">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="b237e-765">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="b237e-765">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="b237e-766">De laatst opgenomen zoek opdracht herhalen, maar in tegenovergestelde richting.</span><span class="sxs-lookup"><span data-stu-id="b237e-766">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="b237e-767">VI-opdracht modus: `<,>`</span><span class="sxs-lookup"><span data-stu-id="b237e-767">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="b237e-768">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="b237e-768">RepeatSearch</span></span>

<span data-ttu-id="b237e-769">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="b237e-769">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="b237e-770">VI-opdracht modus: `<n>`</span><span class="sxs-lookup"><span data-stu-id="b237e-770">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="b237e-771">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="b237e-771">RepeatSearchBackward</span></span>

<span data-ttu-id="b237e-772">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="b237e-772">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="b237e-773">VI-opdracht modus: `<N>`</span><span class="sxs-lookup"><span data-stu-id="b237e-773">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="b237e-774">SearchChar</span><span class="sxs-lookup"><span data-stu-id="b237e-774">SearchChar</span></span>

<span data-ttu-id="b237e-775">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-775">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="b237e-776">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="b237e-776">This is for 't' functionality.</span></span>

- <span data-ttu-id="b237e-777">VI-opdracht modus: `<f>`</span><span class="sxs-lookup"><span data-stu-id="b237e-777">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="b237e-778">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="b237e-778">SearchCharBackward</span></span>

<span data-ttu-id="b237e-779">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-779">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="b237e-780">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="b237e-780">This is for 'T' functionality.</span></span>

- <span data-ttu-id="b237e-781">VI-opdracht modus: `<F>`</span><span class="sxs-lookup"><span data-stu-id="b237e-781">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="b237e-782">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="b237e-782">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="b237e-783">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-783">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="b237e-784">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="b237e-784">This is for 'T' functionality.</span></span>

- <span data-ttu-id="b237e-785">VI-opdracht modus: `<T>`</span><span class="sxs-lookup"><span data-stu-id="b237e-785">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="b237e-786">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="b237e-786">SearchCharWithBackoff</span></span>

<span data-ttu-id="b237e-787">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="b237e-787">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="b237e-788">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="b237e-788">This is for 't' functionality.</span></span>

- <span data-ttu-id="b237e-789">VI-opdracht modus: `<t>`</span><span class="sxs-lookup"><span data-stu-id="b237e-789">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="b237e-790">SearchForward</span><span class="sxs-lookup"><span data-stu-id="b237e-790">SearchForward</span></span>

<span data-ttu-id="b237e-791">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="b237e-791">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="b237e-792">VI Invoeg modus: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b237e-792">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="b237e-793">VI-opdracht modus: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b237e-793">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="b237e-794">Aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="b237e-794">Custom Key Bindings</span></span>

<span data-ttu-id="b237e-795">PSReadLine ondersteunt aangepaste sleutel bindingen met behulp van de-cmdlet `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="b237e-795">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="b237e-796">De meeste aangepaste sleutel bindingen roepen een van de bovenstaande functies aan, bijvoorbeeld</span><span class="sxs-lookup"><span data-stu-id="b237e-796">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="b237e-797">U kunt een script Block binden aan een sleutel.</span><span class="sxs-lookup"><span data-stu-id="b237e-797">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="b237e-798">Het script Block kan veel wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="b237e-798">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="b237e-799">Enkele handige voor beelden zijn</span><span class="sxs-lookup"><span data-stu-id="b237e-799">Some useful examples include</span></span>

- <span data-ttu-id="b237e-800">de opdracht regel bewerken</span><span class="sxs-lookup"><span data-stu-id="b237e-800">edit the command line</span></span>
- <span data-ttu-id="b237e-801">een nieuw venster openen (bijvoorbeeld Help)</span><span class="sxs-lookup"><span data-stu-id="b237e-801">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="b237e-802">mappen wijzigen zonder de opdracht regel te wijzigen</span><span class="sxs-lookup"><span data-stu-id="b237e-802">change directories without changing the command line</span></span>

<span data-ttu-id="b237e-803">De script Block ontvangt twee argumenten:</span><span class="sxs-lookup"><span data-stu-id="b237e-803">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="b237e-804">`$key` -Een **[ConsoleKeyInfo]** -object dat de sleutel is die de aangepaste binding heeft geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="b237e-804">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="b237e-805">Als u dezelfde script Block aan meerdere sleutels koppelt en verschillende acties moet uitvoeren, afhankelijk van de sleutel, kunt u $key controleren.</span><span class="sxs-lookup"><span data-stu-id="b237e-805">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="b237e-806">Veel aangepaste bindingen negeren dit argument.</span><span class="sxs-lookup"><span data-stu-id="b237e-806">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="b237e-807">`$arg` -Een wille keurig argument.</span><span class="sxs-lookup"><span data-stu-id="b237e-807">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="b237e-808">Meestal is dit een geheel getal dat de gebruiker door gegeven van de sleutel bindingen DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="b237e-808">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="b237e-809">Als uw binding geen argumenten accepteert, is het redelijk om dit argument te negeren.</span><span class="sxs-lookup"><span data-stu-id="b237e-809">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="b237e-810">Laten we een voor beeld bekijken waarmee een opdracht regel wordt toegevoegd aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b237e-810">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="b237e-811">Dit is handig wanneer u ervoor hebt gekozen om iets te doen, maar niet opnieuw moet invoeren van de opdracht regel die u al hebt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="b237e-811">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="b237e-812">U kunt veel meer voor beelden bekijken in het bestand `SamplePSReadLineProfile.ps1` dat is geïnstalleerd in de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="b237e-812">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="b237e-813">De meeste sleutel bindingen gebruiken enkele hulp functies voor het bewerken van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-813">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="b237e-814">Deze Api's worden beschreven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="b237e-814">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="b237e-815">Api's voor de ondersteuning van aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="b237e-815">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="b237e-816">De volgende functies zijn openbaar in micro soft. Power shell. PSConsoleReadLine, maar kunnen niet rechtstreeks aan een sleutel worden gebonden.</span><span class="sxs-lookup"><span data-stu-id="b237e-816">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="b237e-817">De meeste zijn handig in aangepaste sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="b237e-817">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="b237e-818">Een opdracht regel toevoegen aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b237e-818">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="b237e-819">Wis de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="b237e-819">Clear the kill-ring.</span></span>  <span data-ttu-id="b237e-820">Dit wordt meestal gebruikt voor het testen.</span><span class="sxs-lookup"><span data-stu-id="b237e-820">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="b237e-821">Verwijder de lengte tekens uit het begin.</span><span class="sxs-lookup"><span data-stu-id="b237e-821">Delete length characters from start.</span></span>  <span data-ttu-id="b237e-822">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b237e-822">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="b237e-823">Voer de actie opname uit op basis van de voor keuren van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b237e-823">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="b237e-824">Deze twee functies halen nuttige informatie op over de huidige status van de invoer buffer.</span><span class="sxs-lookup"><span data-stu-id="b237e-824">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="b237e-825">De eerste wordt vaak gebruikt voor eenvoudige gevallen.</span><span class="sxs-lookup"><span data-stu-id="b237e-825">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="b237e-826">De tweede wordt gebruikt als uw binding iets geavanceerder gaat met de AST.</span><span class="sxs-lookup"><span data-stu-id="b237e-826">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="b237e-827">Deze twee functies worden gebruikt door `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="b237e-827">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="b237e-828">De eerste wordt gebruikt om alle sleutel bindingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="b237e-828">The first is used to get all key bindings.</span></span> <span data-ttu-id="b237e-829">De tweede wordt gebruikt voor het ophalen van specifieke sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="b237e-829">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="b237e-830">Deze functie wordt gebruikt door Get-PSReadLineOption en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="b237e-830">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="b237e-831">Als er niets is geselecteerd op de opdracht regel, wordt-1 geretourneerd in zowel start als length.</span><span class="sxs-lookup"><span data-stu-id="b237e-831">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="b237e-832">Als er een selectie is op de opdracht regel, worden het begin en de lengte van de selectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b237e-832">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="b237e-833">Voeg een teken of teken reeks toe aan de cursor.</span><span class="sxs-lookup"><span data-stu-id="b237e-833">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="b237e-834">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b237e-834">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="b237e-835">Dit is het belangrijkste ingangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b237e-835">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="b237e-836">Er wordt geen recursie ondersteund, dus is niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="b237e-836">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="b237e-837">Deze functie wordt gebruikt door Remove-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="b237e-837">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="b237e-838">Vervang een deel van de invoer.</span><span class="sxs-lookup"><span data-stu-id="b237e-838">Replace some of the input.</span></span> <span data-ttu-id="b237e-839">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b237e-839">This operation supports undo/redo.</span></span> <span data-ttu-id="b237e-840">U kunt het beste verwijderen gevolgd door INSERT, omdat het wordt beschouwd als één actie voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="b237e-840">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="b237e-841">De cursor verplaatsen naar de opgegeven verschuiving.</span><span class="sxs-lookup"><span data-stu-id="b237e-841">Move the cursor to the given offset.</span></span> <span data-ttu-id="b237e-842">Cursor verplaatsing wordt niet bijgehouden voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="b237e-842">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="b237e-843">Deze functie is een helper-methode die wordt gebruikt door de cmdlet Set-PSReadLineOption, maar kan handig zijn voor een aangepaste sleutel binding die tijdelijk een instelling wil wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b237e-843">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="b237e-844">Deze Help methode wordt gebruikt voor aangepaste bindingen die voldoen aan DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="b237e-844">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="b237e-845">Een typische aanroep ziet eruit als</span><span class="sxs-lookup"><span data-stu-id="b237e-845">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="b237e-846">OPMERKING</span><span class="sxs-lookup"><span data-stu-id="b237e-846">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="b237e-847">COMPATIBILITEIT MET POWER SHELL</span><span class="sxs-lookup"><span data-stu-id="b237e-847">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="b237e-848">PSReadLine vereist Power Shell 3,0, of nieuwer, en de console-host.</span><span class="sxs-lookup"><span data-stu-id="b237e-848">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="b237e-849">Het werkt niet in Power shell ISE.</span><span class="sxs-lookup"><span data-stu-id="b237e-849">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="b237e-850">Het werkt in de console van Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="b237e-850">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="b237e-851">OPDRACHT GESCHIEDENIS</span><span class="sxs-lookup"><span data-stu-id="b237e-851">COMMAND HISTORY</span></span>

<span data-ttu-id="b237e-852">PSReadLine onderhoudt een geschiedenis bestand met alle opdrachten en gegevens die u hebt ingevoerd op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="b237e-852">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="b237e-853">Dit kan gevoelige gegevens bevatten, inclusief wacht woorden.</span><span class="sxs-lookup"><span data-stu-id="b237e-853">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="b237e-854">Als u bijvoorbeeld de cmdlet gebruikt, `ConvertTo-SecureString` wordt het wacht woord in het geschiedenis bestand vastgelegd als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="b237e-854">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="b237e-855">De geschiedenis bestanden zijn een bestand met de naam `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="b237e-855">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="b237e-856">Op Windows-systemen wordt het geschiedenis bestand opgeslagen op `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="b237e-856">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="b237e-857">Op niet-Windows-systemen worden de geschiedenis bestanden opgeslagen in `$env:XDG_DATA_HOME/powershell/PSReadLine` of `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="b237e-857">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="b237e-858">FEEDBACK & bijdragen aan PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b237e-858">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="b237e-859">PSReadLine op GitHub</span><span class="sxs-lookup"><span data-stu-id="b237e-859">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="b237e-860">U kunt een pull-aanvraag verzenden of feedback verzenden op de pagina GitHub.</span><span class="sxs-lookup"><span data-stu-id="b237e-860">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="b237e-861">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="b237e-861">SEE ALSO</span></span>

<span data-ttu-id="b237e-862">PSReadLine wordt sterk beïnvloed door de GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="b237e-862">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>

