---
description: PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.
keywords: powershell
Locale: en-US
ms.date: 11/16/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over PSReadLine
ms.openlocfilehash: 25fc3a9a814728057b1ebc7e721d3fba84ae72c2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692306"
---
# <a name="psreadline"></a><span data-ttu-id="a3b0f-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="a3b0f-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="a3b0f-106">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="a3b0f-106">Short Description</span></span>

<span data-ttu-id="a3b0f-107">PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="a3b0f-108">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="a3b0f-108">Long Description</span></span>

<span data-ttu-id="a3b0f-109">PSReadLine 2,0 biedt een krachtige opdracht regel voor het bewerken van de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="a3b0f-110">De oplossing biedt het volgende:</span><span class="sxs-lookup"><span data-stu-id="a3b0f-110">It provides:</span></span>

- <span data-ttu-id="a3b0f-111">Syntaxis kleur van de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="a3b0f-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="a3b0f-112">Een visuele indicatie van syntaxis fouten</span><span class="sxs-lookup"><span data-stu-id="a3b0f-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="a3b0f-113">Een betere ervaring met meerdere regels (zowel bewerkingen als geschiedenis)</span><span class="sxs-lookup"><span data-stu-id="a3b0f-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="a3b0f-114">Aanpas bare sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="a3b0f-114">Customizable key bindings</span></span>
- <span data-ttu-id="a3b0f-115">Cmd-en emacs-modi</span><span class="sxs-lookup"><span data-stu-id="a3b0f-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="a3b0f-116">Veel configuratie opties</span><span class="sxs-lookup"><span data-stu-id="a3b0f-116">Many configuration options</span></span>
- <span data-ttu-id="a3b0f-117">Bash-stijl voltooiing (optioneel in CMD-modus, standaard in Emacs-modus)</span><span class="sxs-lookup"><span data-stu-id="a3b0f-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="a3b0f-118">Emacs Yank/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="a3b0f-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="a3b0f-119">"Woord" verplaatsing en afsluiten op basis van Power shell-tokens</span><span class="sxs-lookup"><span data-stu-id="a3b0f-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="a3b0f-120">PSReadLine vereist Power Shell 3,0, of nieuwer, en de console-host.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-120">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="a3b0f-121">Het werkt niet in Power shell ISE.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-121">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="a3b0f-122">Het werkt in de console van Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-122">It does work in the console of Visual Studio Code.</span></span>

<span data-ttu-id="a3b0f-123">De volgende functies zijn beschikbaar in de klasse **[micro soft. Power shell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-123">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="a3b0f-124">Basis bewerkings functies</span><span class="sxs-lookup"><span data-stu-id="a3b0f-124">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="a3b0f-125">Afbreken</span><span class="sxs-lookup"><span data-stu-id="a3b0f-125">Abort</span></span>

<span data-ttu-id="a3b0f-126">De huidige actie afbreken, bijvoorbeeld een incrementele geschiedenis zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-126">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="a3b0f-127">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-127">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="a3b0f-128">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="a3b0f-128">AcceptAndGetNext</span></span>

<span data-ttu-id="a3b0f-129">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-129">Attempt to execute the current input.</span></span> <span data-ttu-id="a3b0f-130">Als deze kan worden uitgevoerd (zoals AcceptLine), kunt u het volgende item uit de geschiedenis intrekken de volgende keer dat ReadLine wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-130">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="a3b0f-131">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-131">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="a3b0f-132">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-132">AcceptLine</span></span>

<span data-ttu-id="a3b0f-133">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-133">Attempt to execute the current input.</span></span> <span data-ttu-id="a3b0f-134">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-134">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="a3b0f-135">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-135">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="a3b0f-136">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-136">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="a3b0f-137">VI Invoeg modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-137">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="a3b0f-138">AddLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-138">AddLine</span></span>

<span data-ttu-id="a3b0f-139">De vervolg prompt wordt weer gegeven op de volgende regel en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-139">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="a3b0f-140">Dit is handig om invoer in meerdere regels als één opdracht in te voeren, zelfs wanneer één regel volledig wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-140">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="a3b0f-141">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-141">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="a3b0f-142">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-142">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="a3b0f-143">VI Invoeg modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-143">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="a3b0f-144">VI-opdracht modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-144">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="a3b0f-145">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-145">BackwardDeleteChar</span></span>

<span data-ttu-id="a3b0f-146">Verwijder het teken voor de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-146">Delete the character before the cursor.</span></span>

- <span data-ttu-id="a3b0f-147">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-147">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="a3b0f-148">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-148">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="a3b0f-149">VI Invoeg modus: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-149">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="a3b0f-150">VI-opdracht modus: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-150">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="a3b0f-151">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-151">BackwardDeleteLine</span></span>

<span data-ttu-id="a3b0f-152">Net als BackwardKillLine: verwijdert tekst van het punt naar het begin van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-152">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="a3b0f-153">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-153">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="a3b0f-154">VI Invoeg modus: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-154">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="a3b0f-155">VI-opdracht modus: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-155">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="a3b0f-156">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-156">BackwardDeleteWord</span></span>

<span data-ttu-id="a3b0f-157">Hiermee verwijdert u het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-157">Deletes the previous word.</span></span>

- <span data-ttu-id="a3b0f-158">VI-opdracht modus: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-158">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="a3b0f-159">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-159">BackwardKillLine</span></span>

<span data-ttu-id="a3b0f-160">De invoer van het begin van de invoer wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-160">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="a3b0f-161">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-161">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="a3b0f-162">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-162">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="a3b0f-163">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-163">BackwardKillWord</span></span>

<span data-ttu-id="a3b0f-164">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-164">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="a3b0f-165">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-165">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="a3b0f-166">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-166">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="a3b0f-167">Cmd `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-167">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="a3b0f-168">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-168">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="a3b0f-169">VI Invoeg modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-169">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="a3b0f-170">VI-opdracht modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-170">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="a3b0f-171">CancelLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-171">CancelLine</span></span>

<span data-ttu-id="a3b0f-172">De huidige invoer annuleren, waardoor de invoer op het scherm wordt weer gegeven, maar terugkeert naar de host, zodat de prompt opnieuw wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-172">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="a3b0f-173">VI Invoeg modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-173">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="a3b0f-174">VI-opdracht modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-174">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="a3b0f-175">Kopiëren</span><span class="sxs-lookup"><span data-stu-id="a3b0f-175">Copy</span></span>

<span data-ttu-id="a3b0f-176">Kopieer de geselecteerde regio naar het klem bord van het systeem.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-176">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="a3b0f-177">Als er geen regio is geselecteerd, kopieert u de hele regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-177">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="a3b0f-178">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-178">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="a3b0f-179">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-179">CopyOrCancelLine</span></span>

<span data-ttu-id="a3b0f-180">Als tekst is geselecteerd, kopieert u deze naar het klem bord. anders annuleert u de regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-180">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="a3b0f-181">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-181">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="a3b0f-182">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-182">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="a3b0f-183">Knippen</span><span class="sxs-lookup"><span data-stu-id="a3b0f-183">Cut</span></span>

<span data-ttu-id="a3b0f-184">Geselecteerde regio verwijderen Verwijderde tekst in het systeem Klembord plaatsen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-184">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="a3b0f-185">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-185">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="a3b0f-186">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-186">DeleteChar</span></span>

<span data-ttu-id="a3b0f-187">Verwijder het teken onder de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-187">Delete the character under the cursor.</span></span>

- <span data-ttu-id="a3b0f-188">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-188">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="a3b0f-189">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-189">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="a3b0f-190">VI Invoeg modus: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-190">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="a3b0f-191">VI-opdracht modus: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-191">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="a3b0f-192">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="a3b0f-192">DeleteCharOrExit</span></span>

<span data-ttu-id="a3b0f-193">Verwijder het teken onder de cursor of als de regel leeg is, sluit u het proces.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-193">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="a3b0f-194">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-194">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="a3b0f-195">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-195">DeleteEndOfWord</span></span>

<span data-ttu-id="a3b0f-196">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-196">Delete to the end of the word.</span></span>

- <span data-ttu-id="a3b0f-197">VI-opdracht modus: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-197">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="a3b0f-198">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-198">DeleteLine</span></span>

<span data-ttu-id="a3b0f-199">Hiermee verwijdert u de huidige regel, waarbij u ongedaan maken inschakelt.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-199">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="a3b0f-200">VI-opdracht modus: `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-200">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="a3b0f-201">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-201">DeleteLineToFirstChar</span></span>

<span data-ttu-id="a3b0f-202">Hiermee wordt tekst van de cursor verwijderd naar het eerste niet-lege teken van de regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-202">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="a3b0f-203">VI-opdracht modus: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-203">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="a3b0f-204">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="a3b0f-204">DeleteToEnd</span></span>

<span data-ttu-id="a3b0f-205">Verwijderen tot aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-205">Delete to the end of the line.</span></span>

- <span data-ttu-id="a3b0f-206">VI-opdracht modus: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-206">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="a3b0f-207">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-207">DeleteWord</span></span>

<span data-ttu-id="a3b0f-208">Verwijder het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-208">Delete the next word.</span></span>

- <span data-ttu-id="a3b0f-209">VI-opdracht modus: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-209">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="a3b0f-210">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-210">ForwardDeleteLine</span></span>

<span data-ttu-id="a3b0f-211">Net als ForwardKillLine: verwijdert tekst van het punt naar het einde van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-211">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="a3b0f-212">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-212">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="a3b0f-213">VI Invoeg modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-213">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="a3b0f-214">VI-opdracht modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-214">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="a3b0f-215">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="a3b0f-215">InsertLineAbove</span></span>

<span data-ttu-id="a3b0f-216">Er wordt een nieuwe lege regel gemaakt op de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-216">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="a3b0f-217">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-217">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="a3b0f-218">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-218">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="a3b0f-219">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="a3b0f-219">InsertLineBelow</span></span>

<span data-ttu-id="a3b0f-220">Er wordt een nieuwe lege regel gemaakt onder de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-220">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="a3b0f-221">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-221">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="a3b0f-222">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-222">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="a3b0f-223">InvertCase</span><span class="sxs-lookup"><span data-stu-id="a3b0f-223">InvertCase</span></span>

<span data-ttu-id="a3b0f-224">Het hoofdletter gebruik van het huidige teken omkeren en verplaatsen naar het volgende.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-224">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="a3b0f-225">VI-opdracht modus: `<~>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-225">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="a3b0f-226">KillLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-226">KillLine</span></span>

<span data-ttu-id="a3b0f-227">De invoer wissen van de cursor tot het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-227">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="a3b0f-228">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-228">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="a3b0f-229">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-229">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="a3b0f-230">KillRegion</span><span class="sxs-lookup"><span data-stu-id="a3b0f-230">KillRegion</span></span>

<span data-ttu-id="a3b0f-231">Beëindig de tekst tussen de cursor en de markering.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-231">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="a3b0f-232">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-232">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="a3b0f-233">KillWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-233">KillWord</span></span>

<span data-ttu-id="a3b0f-234">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-234">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="a3b0f-235">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-235">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="a3b0f-236">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-236">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="a3b0f-237">Cmd `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-237">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="a3b0f-238">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-238">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="a3b0f-239">VI Invoeg modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-239">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="a3b0f-240">VI-opdracht modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-240">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="a3b0f-241">Plakken</span><span class="sxs-lookup"><span data-stu-id="a3b0f-241">Paste</span></span>

<span data-ttu-id="a3b0f-242">Tekst van het klem bord van het systeem plakken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-242">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="a3b0f-243">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-243">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="a3b0f-244">VI Invoeg modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-244">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="a3b0f-245">VI-opdracht modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-245">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3b0f-246">Wanneer u de functie **Paste** gebruikt, wordt de volledige inhoud van de Klembord buffer geplakt in de invoer buffer van PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-246">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="a3b0f-247">De invoer buffer wordt vervolgens door gegeven aan de Power shell-parser.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-247">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="a3b0f-248">Invoer die met de **rechter muisknop op** de plak methode van de console toepassing wordt geplakt, wordt met één teken per keer naar de invoer buffer gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-248">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="a3b0f-249">De invoer buffer wordt door gegeven aan de parser wanneer een teken voor een nieuwe regel wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-249">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="a3b0f-250">Daarom wordt de invoer één regel tegelijk geparseerd.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-250">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="a3b0f-251">Het verschil tussen plak methoden resulteert in een ander uitvoerings gedrag.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-251">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="a3b0f-252">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="a3b0f-252">PasteAfter</span></span>

<span data-ttu-id="a3b0f-253">Plak het klem bord na de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-253">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="a3b0f-254">VI-opdracht modus: `<p>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-254">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="a3b0f-255">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="a3b0f-255">PasteBefore</span></span>

<span data-ttu-id="a3b0f-256">Plak het klem bord vóór de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-256">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="a3b0f-257">VI-opdracht modus: `<P>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-257">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="a3b0f-258">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="a3b0f-258">PrependAndAccept</span></span>

<span data-ttu-id="a3b0f-259">Laten voorafgaan door een ' # ' en accepteer de regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-259">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="a3b0f-260">VI-opdracht modus: `<#>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-260">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="a3b0f-261">Opnieuw uitvoeren</span><span class="sxs-lookup"><span data-stu-id="a3b0f-261">Redo</span></span>

<span data-ttu-id="a3b0f-262">Undo ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-262">Undo an undo.</span></span>

- <span data-ttu-id="a3b0f-263">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-263">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="a3b0f-264">VI Invoeg modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-264">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="a3b0f-265">VI-opdracht modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-265">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="a3b0f-266">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="a3b0f-266">RepeatLastCommand</span></span>

<span data-ttu-id="a3b0f-267">Herhaal de laatste tekst wijziging.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-267">Repeat the last text modification.</span></span>

- <span data-ttu-id="a3b0f-268">VI-opdracht modus: `<.>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-268">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="a3b0f-269">RevertLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-269">RevertLine</span></span>

<span data-ttu-id="a3b0f-270">Hiermee wordt alle invoer teruggezet naar de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-270">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="a3b0f-271">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-271">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="a3b0f-272">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-272">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="a3b0f-273">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-273">ShellBackwardKillWord</span></span>

<span data-ttu-id="a3b0f-274">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-274">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="a3b0f-275">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-275">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="a3b0f-276">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-276">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="a3b0f-277">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-277">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="a3b0f-278">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-278">ShellKillWord</span></span>

<span data-ttu-id="a3b0f-279">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-279">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="a3b0f-280">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-280">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="a3b0f-281">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-281">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="a3b0f-282">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-282">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="a3b0f-283">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="a3b0f-283">SwapCharacters</span></span>

<span data-ttu-id="a3b0f-284">Het huidige teken en de eerste vervangen door wisselen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-284">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="a3b0f-285">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-285">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="a3b0f-286">VI Invoeg modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-286">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="a3b0f-287">VI-opdracht modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-287">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="a3b0f-288">Ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="a3b0f-288">Undo</span></span>

<span data-ttu-id="a3b0f-289">Een vorige bewerking ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-289">Undo a previous edit.</span></span>

- <span data-ttu-id="a3b0f-290">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-290">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="a3b0f-291">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-291">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="a3b0f-292">VI Invoeg modus: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-292">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="a3b0f-293">VI-opdracht modus: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-293">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="a3b0f-294">UndoAll</span><span class="sxs-lookup"><span data-stu-id="a3b0f-294">UndoAll</span></span>

<span data-ttu-id="a3b0f-295">Alle vorige bewerkingen voor de regel ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-295">Undo all previous edits for line.</span></span>

- <span data-ttu-id="a3b0f-296">VI-opdracht modus: `<U>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-296">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="a3b0f-297">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="a3b0f-297">UnixWordRubout</span></span>

<span data-ttu-id="a3b0f-298">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-298">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="a3b0f-299">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-299">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="a3b0f-300">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-300">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="a3b0f-301">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-301">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="a3b0f-302">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-302">ValidateAndAcceptLine</span></span>

<span data-ttu-id="a3b0f-303">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-303">Attempt to execute the current input.</span></span> <span data-ttu-id="a3b0f-304">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-304">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="a3b0f-305">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-305">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="a3b0f-306">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-306">ViAcceptLine</span></span>

<span data-ttu-id="a3b0f-307">Accepteer de regel en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-307">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="a3b0f-308">VI-opdracht modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-308">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="a3b0f-309">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="a3b0f-309">ViAcceptLineOrExit</span></span>

<span data-ttu-id="a3b0f-310">Als DeleteCharOrExit in de Emacs-modus, maar wel in plaats van een teken te verwijderen, accepteert u de regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-310">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="a3b0f-311">VI Invoeg modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-311">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="a3b0f-312">VI-opdracht modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-312">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="a3b0f-313">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-313">ViAppendLine</span></span>

<span data-ttu-id="a3b0f-314">Er wordt een nieuwe regel ingevoegd onder de huidige regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-314">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="a3b0f-315">VI-opdracht modus: `<o>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-315">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="a3b0f-316">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="a3b0f-316">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="a3b0f-317">Hiermee verwijdert u het vorige woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-317">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="a3b0f-318">VI-opdracht modus: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-318">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="a3b0f-319">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="a3b0f-319">ViBackwardGlob</span></span>

<span data-ttu-id="a3b0f-320">Verplaatst de cursor terug naar het begin van het vorige woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-320">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="a3b0f-321">VI-opdracht modus: `<B>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-321">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="a3b0f-322">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="a3b0f-322">ViDeleteBrace</span></span>

<span data-ttu-id="a3b0f-323">Zoek de accolade, het haakje sluiten of de vier Kante haken en verwijder alle inhoud binnen, inclusief de accolade.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-323">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="a3b0f-324">VI-opdracht modus: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-324">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="a3b0f-325">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="a3b0f-325">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="a3b0f-326">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-326">Delete to the end of the word.</span></span>

- <span data-ttu-id="a3b0f-327">VI-opdracht modus: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-327">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="a3b0f-328">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="a3b0f-328">ViDeleteGlob</span></span>

<span data-ttu-id="a3b0f-329">De volgende Globs verwijderen (door witruimte gescheiden woord).</span><span class="sxs-lookup"><span data-stu-id="a3b0f-329">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="a3b0f-330">VI-opdracht modus: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-330">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="a3b0f-331">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-331">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="a3b0f-332">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-332">Deletes until given character.</span></span>

- <span data-ttu-id="a3b0f-333">VI-opdracht modus: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-333">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="a3b0f-334">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="a3b0f-334">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="a3b0f-335">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-335">Deletes until given character.</span></span>

- <span data-ttu-id="a3b0f-336">VI-opdracht modus: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-336">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="a3b0f-337">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-337">ViDeleteToChar</span></span>

<span data-ttu-id="a3b0f-338">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-338">Deletes until given character.</span></span>

- <span data-ttu-id="a3b0f-339">VI-opdracht modus: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-339">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="a3b0f-340">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="a3b0f-340">ViDeleteToCharBackward</span></span>

<span data-ttu-id="a3b0f-341">Hiermee verwijdert u achterwaartse tekens tot aan het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-341">Deletes backwards until given character.</span></span>

- <span data-ttu-id="a3b0f-342">VI-opdracht modus: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-342">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="a3b0f-343">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="a3b0f-343">ViInsertAtBegining</span></span>

<span data-ttu-id="a3b0f-344">Schakel over naar de Invoeg modus en plaats de cursor aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-344">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="a3b0f-345">VI-opdracht modus: `<I>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-345">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="a3b0f-346">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="a3b0f-346">ViInsertAtEnd</span></span>

<span data-ttu-id="a3b0f-347">Schakel over naar de Invoeg modus en plaats de cursor aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-347">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="a3b0f-348">VI-opdracht modus: `<A>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-348">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="a3b0f-349">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-349">ViInsertLine</span></span>

<span data-ttu-id="a3b0f-350">Boven de huidige regel wordt een nieuwe regel ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-350">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="a3b0f-351">VI-opdracht modus: `<O>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-351">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="a3b0f-352">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="a3b0f-352">ViInsertWithAppend</span></span>

<span data-ttu-id="a3b0f-353">Toevoegen vanaf de huidige regel positie.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-353">Append from the current line position.</span></span>

- <span data-ttu-id="a3b0f-354">VI-opdracht modus: `<a>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-354">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="a3b0f-355">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="a3b0f-355">ViInsertWithDelete</span></span>

<span data-ttu-id="a3b0f-356">Verwijder het huidige teken en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-356">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="a3b0f-357">VI-opdracht modus: `<s>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-357">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="a3b0f-358">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="a3b0f-358">ViJoinLines</span></span>

<span data-ttu-id="a3b0f-359">De huidige regel en de volgende regel worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-359">Joins the current line and the next line.</span></span>

- <span data-ttu-id="a3b0f-360">VI-opdracht modus: `<J>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-360">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="a3b0f-361">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-361">ViReplaceLine</span></span>

<span data-ttu-id="a3b0f-362">De volledige opdracht regel wissen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-362">Erase the entire command line.</span></span>

- <span data-ttu-id="a3b0f-363">VI-opdracht modus: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-363">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="a3b0f-364">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-364">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="a3b0f-365">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-365">Replaces until given character.</span></span>

- <span data-ttu-id="a3b0f-366">VI-opdracht modus: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-366">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="a3b0f-367">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="a3b0f-367">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="a3b0f-368">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-368">Replaces until given character.</span></span>

- <span data-ttu-id="a3b0f-369">VI-opdracht modus: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-369">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="a3b0f-370">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-370">ViReplaceToChar</span></span>

<span data-ttu-id="a3b0f-371">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-371">Deletes until given character.</span></span>

- <span data-ttu-id="a3b0f-372">VI-opdracht modus: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-372">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="a3b0f-373">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="a3b0f-373">ViReplaceToCharBackward</span></span>

<span data-ttu-id="a3b0f-374">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-374">Replaces until given character.</span></span>

- <span data-ttu-id="a3b0f-375">VI-opdracht modus: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-375">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="a3b0f-376">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-376">ViYankBeginningOfLine</span></span>

<span data-ttu-id="a3b0f-377">Yank vanaf het begin van de buffer naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-377">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="a3b0f-378">VI-opdracht modus: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-378">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="a3b0f-379">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="a3b0f-379">ViYankEndOfGlob</span></span>

<span data-ttu-id="a3b0f-380">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="a3b0f-380">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="a3b0f-381">VI-opdracht modus: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-381">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="a3b0f-382">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-382">ViYankEndOfWord</span></span>

<span data-ttu-id="a3b0f-383">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="a3b0f-383">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="a3b0f-384">VI-opdracht modus: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-384">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="a3b0f-385">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="a3b0f-385">ViYankLeft</span></span>

<span data-ttu-id="a3b0f-386">Yank teken (s) links van de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-386">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="a3b0f-387">VI-opdracht modus: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-387">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="a3b0f-388">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-388">ViYankLine</span></span>

<span data-ttu-id="a3b0f-389">Yank de volledige buffer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-389">Yank the entire buffer.</span></span>

- <span data-ttu-id="a3b0f-390">VI-opdracht modus: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-390">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="a3b0f-391">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="a3b0f-391">ViYankNextGlob</span></span>

<span data-ttu-id="a3b0f-392">Yank van de cursor naar het begin van de volgende woord (en).</span><span class="sxs-lookup"><span data-stu-id="a3b0f-392">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="a3b0f-393">VI-opdracht modus: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-393">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="a3b0f-394">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-394">ViYankNextWord</span></span>

<span data-ttu-id="a3b0f-395">Yank het woord (en) na de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-395">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="a3b0f-396">VI-opdracht modus: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-396">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="a3b0f-397">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="a3b0f-397">ViYankPercent</span></span>

<span data-ttu-id="a3b0f-398">Yank naar/van overeenkomende accolade.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-398">Yank to/from matching brace.</span></span>

- <span data-ttu-id="a3b0f-399">VI-opdracht modus: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-399">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="a3b0f-400">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="a3b0f-400">ViYankPreviousGlob</span></span>

<span data-ttu-id="a3b0f-401">Yank vanaf het begin van het (de) woord (en) tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-401">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="a3b0f-402">VI-opdracht modus: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-402">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="a3b0f-403">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-403">ViYankPreviousWord</span></span>

<span data-ttu-id="a3b0f-404">Yank de woorden vóór de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-404">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="a3b0f-405">VI-opdracht modus: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-405">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="a3b0f-406">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="a3b0f-406">ViYankRight</span></span>

<span data-ttu-id="a3b0f-407">Yank teken (s) onder en rechts van de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-407">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="a3b0f-408">VI-opdracht modus: `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-408">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="a3b0f-409">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-409">ViYankToEndOfLine</span></span>

<span data-ttu-id="a3b0f-410">Yank van de cursor tot het einde van de buffer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-410">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="a3b0f-411">VI-opdracht modus: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-411">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="a3b0f-412">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-412">ViYankToFirstChar</span></span>

<span data-ttu-id="a3b0f-413">Yank van het eerste niet-spatie teken tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-413">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="a3b0f-414">VI-opdracht modus: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-414">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="a3b0f-415">Yank</span><span class="sxs-lookup"><span data-stu-id="a3b0f-415">Yank</span></span>

<span data-ttu-id="a3b0f-416">Voeg de meest recent afgebroken tekst toe aan de invoer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-416">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="a3b0f-417">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-417">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="a3b0f-418">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="a3b0f-418">YankLastArg</span></span>

<span data-ttu-id="a3b0f-419">Yank het laatste argument van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-419">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="a3b0f-420">Met een argument, de eerste keer dat deze wordt aangeroepen, gedraagt zich op dezelfde manier als YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-420">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="a3b0f-421">Als meerdere keren worden aangeroepen, wordt door de geschiedenis en ARG de richting ingesteld (negatief de richting omkeren.)</span><span class="sxs-lookup"><span data-stu-id="a3b0f-421">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="a3b0f-422">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-422">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="a3b0f-423">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-423">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="a3b0f-424">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="a3b0f-424">YankNthArg</span></span>

<span data-ttu-id="a3b0f-425">Yank het eerste argument (na de opdracht) van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-425">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="a3b0f-426">Met een argument, Yank het ne argument (vanaf 0), als het argument negatief is, begint vanaf het laatste argument.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-426">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="a3b0f-427">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-427">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="a3b0f-428">YankPop</span><span class="sxs-lookup"><span data-stu-id="a3b0f-428">YankPop</span></span>

<span data-ttu-id="a3b0f-429">Als de vorige bewerking Yank of YankPop is, vervangt u de eerder yanked tekst door de volgende afgebroken tekst van de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-429">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="a3b0f-430">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-430">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="a3b0f-431">Functies voor cursor verplaatsing</span><span class="sxs-lookup"><span data-stu-id="a3b0f-431">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="a3b0f-432">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-432">BackwardChar</span></span>

<span data-ttu-id="a3b0f-433">De cursor één teken naar links verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-433">Move the cursor one character to the left.</span></span> <span data-ttu-id="a3b0f-434">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-434">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="a3b0f-435">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-435">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="a3b0f-436">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-436">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="a3b0f-437">VI Invoeg modus: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-437">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="a3b0f-438">VI-opdracht modus: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-438">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="a3b0f-439">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-439">BackwardWord</span></span>

<span data-ttu-id="a3b0f-440">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-440">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="a3b0f-441">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-441">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="a3b0f-442">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-442">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="a3b0f-443">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-443">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="a3b0f-444">VI Invoeg modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-444">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="a3b0f-445">VI-opdracht modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-445">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="a3b0f-446">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-446">BeginningOfLine</span></span>

<span data-ttu-id="a3b0f-447">Als de invoer meerdere regels heeft, gaat u naar het begin van de huidige regel of gaat u naar het begin van de invoer als deze al aan het begin van de regel staat.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-447">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="a3b0f-448">Als de invoer één regel heeft, gaat u naar het begin van de invoer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-448">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="a3b0f-449">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-449">Cmd: `<Home>`</span></span>
- <span data-ttu-id="a3b0f-450">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-450">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="a3b0f-451">VI Invoeg modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-451">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="a3b0f-452">VI-opdracht modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-452">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="a3b0f-453">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-453">EndOfLine</span></span>

<span data-ttu-id="a3b0f-454">Als de invoer meerdere regels heeft, gaat u naar het einde van de huidige regel of gaat u naar het einde van de invoer als u aan het einde van de regel bent.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-454">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="a3b0f-455">Als de invoer één regel heeft, gaat u naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-455">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="a3b0f-456">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-456">Cmd: `<End>`</span></span>
- <span data-ttu-id="a3b0f-457">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-457">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="a3b0f-458">VI Invoeg modus: `<End>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-458">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="a3b0f-459">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-459">ForwardChar</span></span>

<span data-ttu-id="a3b0f-460">De cursor één teken naar rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-460">Move the cursor one character to the right.</span></span> <span data-ttu-id="a3b0f-461">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-461">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="a3b0f-462">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-462">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="a3b0f-463">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-463">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="a3b0f-464">VI Invoeg modus: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-464">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="a3b0f-465">VI-opdracht modus: `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-465">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="a3b0f-466">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-466">ForwardWord</span></span>

<span data-ttu-id="a3b0f-467">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-467">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="a3b0f-468">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-468">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="a3b0f-469">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-469">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="a3b0f-470">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="a3b0f-470">GotoBrace</span></span>

<span data-ttu-id="a3b0f-471">Ga naar de accolade, haakjes of vier Kante haakjes.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-471">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="a3b0f-472">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-472">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="a3b0f-473">VI Invoeg modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-473">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="a3b0f-474">VI-opdracht modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-474">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="a3b0f-475">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="a3b0f-475">GotoColumn</span></span>

<span data-ttu-id="a3b0f-476">Ga naar de kolom die wordt aangegeven door arg.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-476">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="a3b0f-477">VI-opdracht modus: `<|>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-477">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="a3b0f-478">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-478">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="a3b0f-479">De cursor verplaatsen naar het eerste niet-lege teken in de regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-479">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="a3b0f-480">VI-opdracht modus: `<^>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-480">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="a3b0f-481">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-481">MoveToEndOfLine</span></span>

<span data-ttu-id="a3b0f-482">De cursor verplaatsen naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-482">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="a3b0f-483">VI-opdracht modus: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-483">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="a3b0f-484">NextLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-484">NextLine</span></span>

<span data-ttu-id="a3b0f-485">De cursor verplaatsen naar de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-485">Move the cursor to the next line.</span></span>

- <span data-ttu-id="a3b0f-486">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-486">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="a3b0f-487">NextWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-487">NextWord</span></span>

<span data-ttu-id="a3b0f-488">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-488">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="a3b0f-489">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-489">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="a3b0f-490">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-490">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="a3b0f-491">VI Invoeg modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-491">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="a3b0f-492">VI-opdracht modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-492">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="a3b0f-493">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="a3b0f-493">NextWordEnd</span></span>

<span data-ttu-id="a3b0f-494">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-494">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="a3b0f-495">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-495">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="a3b0f-496">VI-opdracht modus: `<e>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-496">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="a3b0f-497">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-497">PreviousLine</span></span>

<span data-ttu-id="a3b0f-498">Verplaats de cursor naar de vorige regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-498">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="a3b0f-499">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-499">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="a3b0f-500">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-500">ShellBackwardWord</span></span>

<span data-ttu-id="a3b0f-501">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-501">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="a3b0f-502">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-502">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="a3b0f-503">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-503">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="a3b0f-504">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-504">ShellForwardWord</span></span>

<span data-ttu-id="a3b0f-505">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-505">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="a3b0f-506">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-506">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="a3b0f-507">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-507">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="a3b0f-508">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-508">ShellNextWord</span></span>

<span data-ttu-id="a3b0f-509">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-509">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="a3b0f-510">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-510">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="a3b0f-511">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-511">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="a3b0f-512">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-512">ViBackwardWord</span></span>

<span data-ttu-id="a3b0f-513">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-513">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="a3b0f-514">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-514">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="a3b0f-515">VI-opdracht modus: `<b>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-515">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="a3b0f-516">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="a3b0f-516">ViEndOfGlob</span></span>

<span data-ttu-id="a3b0f-517">Verplaatst de cursor naar het einde van het woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-517">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="a3b0f-518">VI-opdracht modus: `<E>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-518">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="a3b0f-519">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="a3b0f-519">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="a3b0f-520">Wordt verplaatst naar het einde van het vorige woord, waarbij alleen witruimte wordt gebruikt als woord als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-520">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="a3b0f-521">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-521">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="a3b0f-522">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="a3b0f-522">ViGotoBrace</span></span>

<span data-ttu-id="a3b0f-523">Vergelijkbaar met GotoBrace, maar is in plaats van op tokens gebaseerd.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-523">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="a3b0f-524">VI-opdracht modus: `<%>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-524">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="a3b0f-525">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="a3b0f-525">ViNextGlob</span></span>

<span data-ttu-id="a3b0f-526">Verplaatst naar het volgende woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-526">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="a3b0f-527">VI-opdracht modus: `<W>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-527">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="a3b0f-528">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-528">ViNextWord</span></span>

<span data-ttu-id="a3b0f-529">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-529">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="a3b0f-530">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-530">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="a3b0f-531">VI-opdracht modus: `<w>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-531">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="a3b0f-532">Geschiedenis functies</span><span class="sxs-lookup"><span data-stu-id="a3b0f-532">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="a3b0f-533">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="a3b0f-533">BeginningOfHistory</span></span>

<span data-ttu-id="a3b0f-534">Hiermee gaat u naar het eerste item in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-534">Move to the first item in the history.</span></span>

- <span data-ttu-id="a3b0f-535">Emacs: `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-535">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="a3b0f-536">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="a3b0f-536">ClearHistory</span></span>

<span data-ttu-id="a3b0f-537">Hiermee wist u de geschiedenis in PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-537">Clears history in PSReadLine.</span></span> <span data-ttu-id="a3b0f-538">Dit heeft geen invloed op de Power shell-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-538">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="a3b0f-539">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-539">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="a3b0f-540">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="a3b0f-540">EndOfHistory</span></span>

<span data-ttu-id="a3b0f-541">Hiermee gaat u naar het laatste item (de huidige invoer) in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-541">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="a3b0f-542">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-542">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="a3b0f-543">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="a3b0f-543">ForwardSearchHistory</span></span>

<span data-ttu-id="a3b0f-544">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-544">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="a3b0f-545">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-545">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="a3b0f-546">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-546">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="a3b0f-547">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="a3b0f-547">HistorySearchBackward</span></span>

<span data-ttu-id="a3b0f-548">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-548">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="a3b0f-549">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-549">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="a3b0f-550">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="a3b0f-550">HistorySearchForward</span></span>

<span data-ttu-id="a3b0f-551">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-551">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="a3b0f-552">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-552">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="a3b0f-553">NextHistory</span><span class="sxs-lookup"><span data-stu-id="a3b0f-553">NextHistory</span></span>

<span data-ttu-id="a3b0f-554">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-554">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="a3b0f-555">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-555">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="a3b0f-556">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-556">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="a3b0f-557">VI Invoeg modus: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-557">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="a3b0f-558">VI-opdracht modus: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-558">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="a3b0f-559">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="a3b0f-559">PreviousHistory</span></span>

<span data-ttu-id="a3b0f-560">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-560">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="a3b0f-561">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-561">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="a3b0f-562">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-562">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="a3b0f-563">VI Invoeg modus: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-563">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="a3b0f-564">VI-opdracht modus: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-564">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="a3b0f-565">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="a3b0f-565">ReverseSearchHistory</span></span>

<span data-ttu-id="a3b0f-566">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-566">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="a3b0f-567">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-567">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="a3b0f-568">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-568">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="a3b0f-569">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="a3b0f-569">ViSearchHistoryBackward</span></span>

<span data-ttu-id="a3b0f-570">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-570">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="a3b0f-571">VI Invoeg modus: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-571">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="a3b0f-572">VI-opdracht modus: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-572">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="a3b0f-573">Voltooiings functies</span><span class="sxs-lookup"><span data-stu-id="a3b0f-573">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="a3b0f-574">Voltooid</span><span class="sxs-lookup"><span data-stu-id="a3b0f-574">Complete</span></span>

<span data-ttu-id="a3b0f-575">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-575">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="a3b0f-576">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-576">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="a3b0f-577">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-577">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="a3b0f-578">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-578">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="a3b0f-579">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="a3b0f-579">MenuComplete</span></span>

<span data-ttu-id="a3b0f-580">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-580">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="a3b0f-581">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-581">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="a3b0f-582">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-582">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="a3b0f-583">Cmd `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-583">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="a3b0f-584">Emacs: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-584">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="a3b0f-585">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="a3b0f-585">PossibleCompletions</span></span>

<span data-ttu-id="a3b0f-586">De lijst met mogelijke aanvullingen weer geven.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-586">Display the list of possible completions.</span></span>

- <span data-ttu-id="a3b0f-587">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-587">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="a3b0f-588">VI Invoeg modus: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-588">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="a3b0f-589">VI-opdracht modus: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-589">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="a3b0f-590">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="a3b0f-590">TabCompleteNext</span></span>

<span data-ttu-id="a3b0f-591">Poging om de tekst rond de cursor te volt ooien met de volgende beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-591">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="a3b0f-592">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-592">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="a3b0f-593">VI-opdracht modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-593">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="a3b0f-594">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="a3b0f-594">TabCompletePrevious</span></span>

<span data-ttu-id="a3b0f-595">Poging om de tekst rond de cursor te volt ooien met de vorige beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-595">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="a3b0f-596">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-596">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="a3b0f-597">VI-opdracht modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-597">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="a3b0f-598">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="a3b0f-598">ViTabCompleteNext</span></span>

<span data-ttu-id="a3b0f-599">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompleteNext aan.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-599">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="a3b0f-600">VI Invoeg modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-600">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="a3b0f-601">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="a3b0f-601">ViTabCompletePrevious</span></span>

<span data-ttu-id="a3b0f-602">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompletePrevious aan.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-602">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="a3b0f-603">VI Invoeg modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-603">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="a3b0f-604">Diverse functies</span><span class="sxs-lookup"><span data-stu-id="a3b0f-604">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="a3b0f-605">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="a3b0f-605">CaptureScreen</span></span>

<span data-ttu-id="a3b0f-606">Interactieve scherm opname starten-pijl-omhoog/omlaag Selecteer regels en voer de geselecteerde tekst als tekst en HTML naar het klem bord kopiëren.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-606">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="a3b0f-607">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-607">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="a3b0f-608">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="a3b0f-608">ClearScreen</span></span>

<span data-ttu-id="a3b0f-609">Schakel het scherm uit en teken de huidige regel boven aan het scherm.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-609">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="a3b0f-610">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-610">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="a3b0f-611">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-611">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="a3b0f-612">VI Invoeg modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-612">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="a3b0f-613">VI-opdracht modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-613">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="a3b0f-614">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="a3b0f-614">DigitArgument</span></span>

<span data-ttu-id="a3b0f-615">Start een nieuw cijfer argument om door te geven aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-615">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="a3b0f-616">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-616">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="a3b0f-617">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-617">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="a3b0f-618">VI-opdracht modus: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-618">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="a3b0f-619">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="a3b0f-619">InvokePrompt</span></span>

<span data-ttu-id="a3b0f-620">Hiermee wordt de huidige prompt gewist en wordt de functie Prompt aangeroepen om de prompt opnieuw weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-620">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="a3b0f-621">Dit is handig voor aangepaste sleutel afhandelingen die de status wijzigen, bijvoorbeeld de huidige map wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-621">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="a3b0f-622">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-622">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="a3b0f-623">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="a3b0f-623">ScrollDisplayDown</span></span>

<span data-ttu-id="a3b0f-624">De weer gave één scherm omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-624">Scroll the display down one screen.</span></span>

- <span data-ttu-id="a3b0f-625">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-625">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="a3b0f-626">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-626">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="a3b0f-627">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-627">ScrollDisplayDownLine</span></span>

<span data-ttu-id="a3b0f-628">De weer gave één regel omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-628">Scroll the display down one line.</span></span>

- <span data-ttu-id="a3b0f-629">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-629">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="a3b0f-630">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-630">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="a3b0f-631">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="a3b0f-631">ScrollDisplayToCursor</span></span>

<span data-ttu-id="a3b0f-632">Schuif de weer gave naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-632">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="a3b0f-633">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-633">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="a3b0f-634">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="a3b0f-634">ScrollDisplayTop</span></span>

<span data-ttu-id="a3b0f-635">Schuif de weer gave naar boven.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-635">Scroll the display to the top.</span></span>

- <span data-ttu-id="a3b0f-636">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-636">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="a3b0f-637">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="a3b0f-637">ScrollDisplayUp</span></span>

<span data-ttu-id="a3b0f-638">Schuif de weer gave één scherm omhoog.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-638">Scroll the display up one screen.</span></span>

- <span data-ttu-id="a3b0f-639">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-639">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="a3b0f-640">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-640">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="a3b0f-641">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-641">ScrollDisplayUpLine</span></span>

<span data-ttu-id="a3b0f-642">De weer gave één regel omhoog schuiven.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-642">Scroll the display up one line.</span></span>

- <span data-ttu-id="a3b0f-643">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-643">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="a3b0f-644">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-644">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="a3b0f-645">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="a3b0f-645">SelfInsert</span></span>

<span data-ttu-id="a3b0f-646">Voeg de sleutel in.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-646">Insert the key.</span></span>

- <span data-ttu-id="a3b0f-647">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-647">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="a3b0f-648">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="a3b0f-648">ShowKeyBindings</span></span>

<span data-ttu-id="a3b0f-649">Alle gebonden sleutels weer geven.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-649">Show all bound keys.</span></span>

- <span data-ttu-id="a3b0f-650">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-650">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="a3b0f-651">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-651">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="a3b0f-652">VI Invoeg modus: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-652">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="a3b0f-653">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="a3b0f-653">ViCommandMode</span></span>

<span data-ttu-id="a3b0f-654">Schakel de huidige bedrijfs modus uit van Vi-Insert naar de VI-opdracht.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-654">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="a3b0f-655">VI Invoeg modus: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-655">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="a3b0f-656">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-656">ViDigitArgumentInChord</span></span>

<span data-ttu-id="a3b0f-657">Start een nieuw cijfer argument om door te geven aan andere functies in een van de koorden van VI.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-657">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="a3b0f-658">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-658">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="a3b0f-659">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="a3b0f-659">ViEditVisually</span></span>

<span data-ttu-id="a3b0f-660">Bewerk de opdracht regel in een tekst editor die is opgegeven door $env: EDITOR of $env: VISUAL.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-660">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="a3b0f-661">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-661">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="a3b0f-662">VI-opdracht modus: `<v>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-662">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="a3b0f-663">ViExit</span><span class="sxs-lookup"><span data-stu-id="a3b0f-663">ViExit</span></span>

<span data-ttu-id="a3b0f-664">Hiermee wordt de shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-664">Exits the shell.</span></span>

- <span data-ttu-id="a3b0f-665">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-665">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="a3b0f-666">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="a3b0f-666">ViInsertMode</span></span>

<span data-ttu-id="a3b0f-667">Schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-667">Switch to Insert mode.</span></span>

- <span data-ttu-id="a3b0f-668">VI-opdracht modus: `<i>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-668">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="a3b0f-669">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="a3b0f-669">WhatIsKey</span></span>

<span data-ttu-id="a3b0f-670">Lees een sleutel en vertel me wat de sleutel is gebonden.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-670">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="a3b0f-671">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-671">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="a3b0f-672">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-672">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="a3b0f-673">Selectie functies</span><span class="sxs-lookup"><span data-stu-id="a3b0f-673">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="a3b0f-674">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="a3b0f-674">ExchangePointAndMark</span></span>

<span data-ttu-id="a3b0f-675">De cursor wordt op de locatie van het merk geplaatst en het vinkje wordt verplaatst naar de locatie van de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-675">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="a3b0f-676">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-676">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="a3b0f-677">SelectAll aanroepen</span><span class="sxs-lookup"><span data-stu-id="a3b0f-677">SelectAll</span></span>

<span data-ttu-id="a3b0f-678">Selecteer de volledige regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-678">Select the entire line.</span></span>

- <span data-ttu-id="a3b0f-679">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-679">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="a3b0f-680">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-680">SelectBackwardChar</span></span>

<span data-ttu-id="a3b0f-681">Pas de huidige selectie aan om het vorige teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-681">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="a3b0f-682">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-682">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="a3b0f-683">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-683">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="a3b0f-684">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-684">SelectBackwardsLine</span></span>

<span data-ttu-id="a3b0f-685">Pas de huidige selectie aan de cursor toe aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-685">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="a3b0f-686">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-686">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="a3b0f-687">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-687">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="a3b0f-688">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-688">SelectBackwardWord</span></span>

<span data-ttu-id="a3b0f-689">Pas de huidige selectie aan om het vorige woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-689">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="a3b0f-690">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-690">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="a3b0f-691">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-691">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="a3b0f-692">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-692">SelectForwardChar</span></span>

<span data-ttu-id="a3b0f-693">Pas de huidige selectie aan om het volgende teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-693">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="a3b0f-694">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-694">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="a3b0f-695">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-695">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="a3b0f-696">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-696">SelectForwardWord</span></span>

<span data-ttu-id="a3b0f-697">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-697">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="a3b0f-698">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-698">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="a3b0f-699">SelectLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-699">SelectLine</span></span>

<span data-ttu-id="a3b0f-700">Pas de huidige selectie aan de cursor toe aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-700">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="a3b0f-701">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-701">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="a3b0f-702">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-702">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="a3b0f-703">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-703">SelectNextWord</span></span>

<span data-ttu-id="a3b0f-704">Pas de huidige selectie aan om het volgende woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-704">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="a3b0f-705">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-705">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="a3b0f-706">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-706">SelectShellBackwardWord</span></span>

<span data-ttu-id="a3b0f-707">Pas de huidige selectie aan om het vorige woord op te maken met behulp van ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-707">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="a3b0f-708">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-708">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="a3b0f-709">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-709">SelectShellForwardWord</span></span>

<span data-ttu-id="a3b0f-710">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-710">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="a3b0f-711">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-711">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="a3b0f-712">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="a3b0f-712">SelectShellNextWord</span></span>

<span data-ttu-id="a3b0f-713">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-713">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="a3b0f-714">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-714">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="a3b0f-715">SetMark</span><span class="sxs-lookup"><span data-stu-id="a3b0f-715">SetMark</span></span>

<span data-ttu-id="a3b0f-716">De huidige locatie van de cursor markeren voor gebruik in een volgende bewerkings opdracht.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-716">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="a3b0f-717">Emacs: `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-717">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="a3b0f-718">Zoek functies</span><span class="sxs-lookup"><span data-stu-id="a3b0f-718">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="a3b0f-719">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="a3b0f-719">CharacterSearch</span></span>

<span data-ttu-id="a3b0f-720">Lees een teken en zoek voorwaarts naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-720">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="a3b0f-721">Als er een argument is opgegeven, zoekt u voorwaarts (of achterwaarts als negatieve) voor het ne voorval.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-721">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="a3b0f-722">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-722">Cmd: `<F3>`</span></span>
- <span data-ttu-id="a3b0f-723">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-723">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="a3b0f-724">VI Invoeg modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-724">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="a3b0f-725">VI-opdracht modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-725">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="a3b0f-726">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="a3b0f-726">CharacterSearchBackward</span></span>

<span data-ttu-id="a3b0f-727">Lees een teken en zoek terug naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-727">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="a3b0f-728">Als er een argument is opgegeven, zoekt u terug (of als dit negatief is) voor het ne exemplaar.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-728">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="a3b0f-729">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-729">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="a3b0f-730">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-730">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="a3b0f-731">VI Invoeg modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-731">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="a3b0f-732">VI-opdracht modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-732">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="a3b0f-733">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="a3b0f-733">RepeatLastCharSearch</span></span>

<span data-ttu-id="a3b0f-734">De laatst opgenomen zoek opdracht herhalen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-734">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="a3b0f-735">VI-opdracht modus: `<;>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-735">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="a3b0f-736">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="a3b0f-736">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="a3b0f-737">De laatst opgenomen zoek opdracht herhalen, maar in tegenovergestelde richting.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-737">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="a3b0f-738">VI-opdracht modus: `<,>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-738">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="a3b0f-739">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="a3b0f-739">RepeatSearch</span></span>

<span data-ttu-id="a3b0f-740">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-740">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="a3b0f-741">VI-opdracht modus: `<n>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-741">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="a3b0f-742">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="a3b0f-742">RepeatSearchBackward</span></span>

<span data-ttu-id="a3b0f-743">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-743">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="a3b0f-744">VI-opdracht modus: `<N>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-744">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="a3b0f-745">SearchChar</span><span class="sxs-lookup"><span data-stu-id="a3b0f-745">SearchChar</span></span>

<span data-ttu-id="a3b0f-746">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-746">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="a3b0f-747">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-747">This is for 't' functionality.</span></span>

- <span data-ttu-id="a3b0f-748">VI-opdracht modus: `<f>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-748">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="a3b0f-749">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="a3b0f-749">SearchCharBackward</span></span>

<span data-ttu-id="a3b0f-750">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-750">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="a3b0f-751">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-751">This is for 'T' functionality.</span></span>

- <span data-ttu-id="a3b0f-752">VI-opdracht modus: `<F>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-752">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="a3b0f-753">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="a3b0f-753">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="a3b0f-754">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-754">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="a3b0f-755">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-755">This is for 'T' functionality.</span></span>

- <span data-ttu-id="a3b0f-756">VI-opdracht modus: `<T>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-756">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="a3b0f-757">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="a3b0f-757">SearchCharWithBackoff</span></span>

<span data-ttu-id="a3b0f-758">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-758">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="a3b0f-759">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-759">This is for 't' functionality.</span></span>

- <span data-ttu-id="a3b0f-760">VI-opdracht modus: `<t>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-760">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="a3b0f-761">SearchForward</span><span class="sxs-lookup"><span data-stu-id="a3b0f-761">SearchForward</span></span>

<span data-ttu-id="a3b0f-762">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-762">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="a3b0f-763">VI Invoeg modus: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-763">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="a3b0f-764">VI-opdracht modus: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="a3b0f-764">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="a3b0f-765">Aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="a3b0f-765">Custom Key Bindings</span></span>

<span data-ttu-id="a3b0f-766">PSReadLine ondersteunt aangepaste sleutel bindingen met behulp van de-cmdlet `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="a3b0f-766">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="a3b0f-767">De meeste aangepaste sleutel bindingen roepen een van de bovenstaande functies aan, bijvoorbeeld</span><span class="sxs-lookup"><span data-stu-id="a3b0f-767">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="a3b0f-768">U kunt een script Block binden aan een sleutel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-768">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="a3b0f-769">Het script Block kan veel wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-769">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="a3b0f-770">Enkele handige voor beelden zijn</span><span class="sxs-lookup"><span data-stu-id="a3b0f-770">Some useful examples include</span></span>

- <span data-ttu-id="a3b0f-771">de opdracht regel bewerken</span><span class="sxs-lookup"><span data-stu-id="a3b0f-771">edit the command line</span></span>
- <span data-ttu-id="a3b0f-772">een nieuw venster openen (bijvoorbeeld Help)</span><span class="sxs-lookup"><span data-stu-id="a3b0f-772">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="a3b0f-773">mappen wijzigen zonder de opdracht regel te wijzigen</span><span class="sxs-lookup"><span data-stu-id="a3b0f-773">change directories without changing the command line</span></span>

<span data-ttu-id="a3b0f-774">De script Block ontvangt twee argumenten:</span><span class="sxs-lookup"><span data-stu-id="a3b0f-774">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="a3b0f-775">`$key` -Een **[ConsoleKeyInfo]** -object dat de sleutel is die de aangepaste binding heeft geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-775">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="a3b0f-776">Als u dezelfde script Block aan meerdere sleutels koppelt en verschillende acties moet uitvoeren, afhankelijk van de sleutel, kunt u $key controleren.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-776">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="a3b0f-777">Veel aangepaste bindingen negeren dit argument.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-777">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="a3b0f-778">`$arg` -Een wille keurig argument.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-778">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="a3b0f-779">Meestal is dit een geheel getal dat de gebruiker door gegeven van de sleutel bindingen DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-779">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="a3b0f-780">Als uw binding geen argumenten accepteert, is het redelijk om dit argument te negeren.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-780">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="a3b0f-781">Laten we een voor beeld bekijken waarmee een opdracht regel wordt toegevoegd aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-781">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="a3b0f-782">Dit is handig wanneer u ervoor hebt gekozen om iets te doen, maar niet opnieuw moet invoeren van de opdracht regel die u al hebt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-782">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="a3b0f-783">U kunt veel meer voor beelden bekijken in het bestand `SamplePSReadLineProfile.ps1` dat is geïnstalleerd in de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-783">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="a3b0f-784">De meeste sleutel bindingen gebruiken enkele hulp functies voor het bewerken van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-784">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="a3b0f-785">Deze Api's worden beschreven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-785">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="a3b0f-786">Api's voor de ondersteuning van aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="a3b0f-786">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="a3b0f-787">De volgende functies zijn openbaar in micro soft. Power shell. PSConsoleReadLine, maar kunnen niet rechtstreeks aan een sleutel worden gebonden.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-787">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="a3b0f-788">De meeste zijn handig in aangepaste sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-788">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="a3b0f-789">Een opdracht regel toevoegen aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-789">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="a3b0f-790">Wis de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-790">Clear the kill-ring.</span></span>  <span data-ttu-id="a3b0f-791">Dit wordt meestal gebruikt voor het testen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-791">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="a3b0f-792">Verwijder de lengte tekens uit het begin.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-792">Delete length characters from start.</span></span>  <span data-ttu-id="a3b0f-793">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-793">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="a3b0f-794">Voer de actie opname uit op basis van de voor keuren van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-794">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="a3b0f-795">Deze twee functies halen nuttige informatie op over de huidige status van de invoer buffer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-795">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="a3b0f-796">De eerste wordt vaak gebruikt voor eenvoudige gevallen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-796">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="a3b0f-797">De tweede wordt gebruikt als uw binding iets geavanceerder gaat met de AST.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-797">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="a3b0f-798">Deze functie wordt gebruikt door Get-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-798">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="a3b0f-799">Deze functie wordt gebruikt door Get-PSReadLineOption en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-799">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="a3b0f-800">Als er niets is geselecteerd op de opdracht regel, wordt-1 geretourneerd in zowel start als length.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-800">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="a3b0f-801">Als er een selectie is op de opdracht regel, worden het begin en de lengte van de selectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-801">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="a3b0f-802">Voeg een teken of teken reeks toe aan de cursor.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-802">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="a3b0f-803">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-803">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="a3b0f-804">Dit is het belangrijkste ingangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-804">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="a3b0f-805">Er wordt geen recursie ondersteund, dus is niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-805">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="a3b0f-806">Deze functie wordt gebruikt door Remove-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-806">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="a3b0f-807">Vervang een deel van de invoer.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-807">Replace some of the input.</span></span> <span data-ttu-id="a3b0f-808">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-808">This operation supports undo/redo.</span></span> <span data-ttu-id="a3b0f-809">U kunt het beste verwijderen gevolgd door INSERT, omdat het wordt beschouwd als één actie voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-809">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="a3b0f-810">De cursor verplaatsen naar de opgegeven verschuiving.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-810">Move the cursor to the given offset.</span></span> <span data-ttu-id="a3b0f-811">Cursor verplaatsing wordt niet bijgehouden voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-811">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="a3b0f-812">Deze functie is een helper-methode die wordt gebruikt door de cmdlet Set-PSReadLineOption, maar kan handig zijn voor een aangepaste sleutel binding die tijdelijk een instelling wil wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-812">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="a3b0f-813">Deze Help methode wordt gebruikt voor aangepaste bindingen die voldoen aan DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-813">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="a3b0f-814">Een typische aanroep ziet eruit als</span><span class="sxs-lookup"><span data-stu-id="a3b0f-814">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="a3b0f-815">Notitie</span><span class="sxs-lookup"><span data-stu-id="a3b0f-815">Note</span></span>

### <a name="command-history"></a><span data-ttu-id="a3b0f-816">Opdracht geschiedenis</span><span class="sxs-lookup"><span data-stu-id="a3b0f-816">Command History</span></span>

<span data-ttu-id="a3b0f-817">PSReadLine onderhoudt een geschiedenis bestand met alle opdrachten en gegevens die u hebt ingevoerd op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-817">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="a3b0f-818">Dit kan gevoelige gegevens bevatten, inclusief wacht woorden.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-818">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="a3b0f-819">Als u bijvoorbeeld de cmdlet gebruikt, `ConvertTo-SecureString` wordt het wacht woord in het geschiedenis bestand vastgelegd als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-819">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="a3b0f-820">De geschiedenis bestanden zijn een bestand met de naam `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="a3b0f-820">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="a3b0f-821">Op Windows-systemen wordt het geschiedenis bestand opgeslagen op `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="a3b0f-821">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="a3b0f-822">Feedback & bijdragen aan PSReadLine</span><span class="sxs-lookup"><span data-stu-id="a3b0f-822">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="a3b0f-823">PSReadLine op GitHub</span><span class="sxs-lookup"><span data-stu-id="a3b0f-823">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="a3b0f-824">U kunt een pull-aanvraag verzenden of feedback verzenden op de pagina GitHub.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-824">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="a3b0f-825">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a3b0f-825">See Also</span></span>

<span data-ttu-id="a3b0f-826">PSReadLine wordt sterk beïnvloed door de GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="a3b0f-826">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
