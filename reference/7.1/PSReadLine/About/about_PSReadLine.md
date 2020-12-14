---
description: PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.
keywords: powershell
Locale: en-US
ms.date: 11/16/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Over PSReadLine
ms.openlocfilehash: 6d52bb04118914a9ccca5d3442a9d1915c1c2818
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692272"
---
# <a name="psreadline"></a><span data-ttu-id="59ce6-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="59ce6-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="59ce6-106">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="59ce6-106">Short Description</span></span>

<span data-ttu-id="59ce6-107">PSReadLine biedt een verbeterde opdracht regel bewerkings ervaring in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="59ce6-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="59ce6-108">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="59ce6-108">Long Description</span></span>

<span data-ttu-id="59ce6-109">PSReadLine 2,1 biedt een krachtige opdracht regel voor het bewerken van de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="59ce6-109">PSReadLine 2.1 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="59ce6-110">De oplossing biedt het volgende:</span><span class="sxs-lookup"><span data-stu-id="59ce6-110">It provides:</span></span>

- <span data-ttu-id="59ce6-111">Syntaxis kleur van de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="59ce6-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="59ce6-112">Een visuele indicatie van syntaxis fouten</span><span class="sxs-lookup"><span data-stu-id="59ce6-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="59ce6-113">Een betere ervaring met meerdere regels (zowel bewerkingen als geschiedenis)</span><span class="sxs-lookup"><span data-stu-id="59ce6-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="59ce6-114">Aanpas bare sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="59ce6-114">Customizable key bindings</span></span>
- <span data-ttu-id="59ce6-115">Cmd-en emacs-modi</span><span class="sxs-lookup"><span data-stu-id="59ce6-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="59ce6-116">Veel configuratie opties</span><span class="sxs-lookup"><span data-stu-id="59ce6-116">Many configuration options</span></span>
- <span data-ttu-id="59ce6-117">Bash-stijl voltooiing (optioneel in CMD-modus, standaard in Emacs-modus)</span><span class="sxs-lookup"><span data-stu-id="59ce6-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="59ce6-118">Emacs Yank/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="59ce6-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="59ce6-119">"Woord" verplaatsing en afsluiten op basis van Power shell-tokens</span><span class="sxs-lookup"><span data-stu-id="59ce6-119">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="59ce6-120">Voorspellende IntelliSense</span><span class="sxs-lookup"><span data-stu-id="59ce6-120">Predictive IntelliSense</span></span>

<span data-ttu-id="59ce6-121">PSReadLine vereist Power Shell 3,0, of nieuwer, en de console-host.</span><span class="sxs-lookup"><span data-stu-id="59ce6-121">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="59ce6-122">Het werkt niet in Power shell ISE.</span><span class="sxs-lookup"><span data-stu-id="59ce6-122">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="59ce6-123">Het werkt in de console van Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="59ce6-123">It does work in the console of Visual Studio Code.</span></span>

<span data-ttu-id="59ce6-124">PSReadLine 2.1.0 wordt geleverd met Power shell 7,1 en wordt ondersteund in alle ondersteunde versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="59ce6-124">PSReadLine 2.1.0 ships with PowerShell 7.1 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="59ce6-125">Het is beschikbaar om te installeren via de PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="59ce6-125">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="59ce6-126">Voer de volgende opdracht uit om PSReadLine 2.1.0 in een ondersteunde versie van Power shell te installeren.</span><span class="sxs-lookup"><span data-stu-id="59ce6-126">To install PSReadLine 2.1.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -RequiredVersion 2.1.0
```

> [!NOTE]
> <span data-ttu-id="59ce6-127">Vanaf Power shell 7,0 wordt het automatisch laden van PSReadLine in Windows overs Laan als er een scherm lezer wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-127">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="59ce6-128">Op dit moment werkt PSReadLine niet goed met scherm lezers.</span><span class="sxs-lookup"><span data-stu-id="59ce6-128">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="59ce6-129">De standaard weergave en opmaak van Power shell 7,0 in Windows werkt op de juiste manier.</span><span class="sxs-lookup"><span data-stu-id="59ce6-129">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="59ce6-130">U kunt de module hand matig laden, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="59ce6-130">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="59ce6-131">Voorspellende IntelliSense</span><span class="sxs-lookup"><span data-stu-id="59ce6-131">Predictive IntelliSense</span></span>

<span data-ttu-id="59ce6-132">Voorspellende IntelliSense is een aanvulling op het concept van tabblad voltooiing waarmee de gebruiker wordt geholpen bij het volt ooien van opdrachten.</span><span class="sxs-lookup"><span data-stu-id="59ce6-132">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="59ce6-133">Hiermee kunnen gebruikers volledige opdrachten detecteren, bewerken en uitvoeren op basis van overeenkomende voor spellingen van de geschiedenis van de gebruiker en aanvullende toepassingsspecifieke invoeg toepassingen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-133">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="59ce6-134">Voorspellende IntelliSense inschakelen</span><span class="sxs-lookup"><span data-stu-id="59ce6-134">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="59ce6-135">Voorspellende IntelliSense is standaard uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="59ce6-135">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="59ce6-136">Als u voor spellingen wilt inschakelen, voert u gewoon de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="59ce6-136">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="59ce6-137">De para meter **PredictionSource** kan ook invoeg toepassingen accepteren voor specifieke en aangepaste vereisten voor het domein.</span><span class="sxs-lookup"><span data-stu-id="59ce6-137">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="59ce6-138">Als u voorspellende IntelliSense wilt uitschakelen, voert u de volgende handelingen uit:</span><span class="sxs-lookup"><span data-stu-id="59ce6-138">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="59ce6-139">De volgende functies zijn beschikbaar in de klasse **[micro soft. Power shell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="59ce6-139">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="59ce6-140">Basis bewerkings functies</span><span class="sxs-lookup"><span data-stu-id="59ce6-140">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="59ce6-141">Afbreken</span><span class="sxs-lookup"><span data-stu-id="59ce6-141">Abort</span></span>

<span data-ttu-id="59ce6-142">De huidige actie afbreken, bijvoorbeeld een incrementele geschiedenis zoekopdracht.</span><span class="sxs-lookup"><span data-stu-id="59ce6-142">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="59ce6-143">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-143">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="59ce6-144">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="59ce6-144">AcceptAndGetNext</span></span>

<span data-ttu-id="59ce6-145">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-145">Attempt to execute the current input.</span></span> <span data-ttu-id="59ce6-146">Als deze kan worden uitgevoerd (zoals AcceptLine), kunt u het volgende item uit de geschiedenis intrekken de volgende keer dat ReadLine wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-146">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="59ce6-147">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-147">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="59ce6-148">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-148">AcceptLine</span></span>

<span data-ttu-id="59ce6-149">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-149">Attempt to execute the current input.</span></span> <span data-ttu-id="59ce6-150">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-150">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="59ce6-151">Cmd `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-151">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="59ce6-152">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-152">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="59ce6-153">VI Invoeg modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-153">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="59ce6-154">AddLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-154">AddLine</span></span>

<span data-ttu-id="59ce6-155">De vervolg prompt wordt weer gegeven op de volgende regel en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-155">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="59ce6-156">Dit is handig om invoer in meerdere regels als één opdracht in te voeren, zelfs wanneer één regel volledig wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-156">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="59ce6-157">Cmd `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-157">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="59ce6-158">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-158">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="59ce6-159">VI Invoeg modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-159">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="59ce6-160">VI-opdracht modus: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-160">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="59ce6-161">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-161">BackwardDeleteChar</span></span>

<span data-ttu-id="59ce6-162">Verwijder het teken voor de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-162">Delete the character before the cursor.</span></span>

- <span data-ttu-id="59ce6-163">Cmd: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-163">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="59ce6-164">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-164">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="59ce6-165">VI Invoeg modus: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-165">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="59ce6-166">VI-opdracht modus: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-166">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="59ce6-167">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-167">BackwardDeleteLine</span></span>

<span data-ttu-id="59ce6-168">Net als BackwardKillLine: verwijdert tekst van het punt naar het begin van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="59ce6-168">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="59ce6-169">Cmd `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-169">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="59ce6-170">VI Invoeg modus: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-170">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="59ce6-171">VI-opdracht modus: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-171">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="59ce6-172">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-172">BackwardDeleteWord</span></span>

<span data-ttu-id="59ce6-173">Hiermee verwijdert u het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-173">Deletes the previous word.</span></span>

- <span data-ttu-id="59ce6-174">VI-opdracht modus: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-174">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="59ce6-175">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-175">BackwardKillLine</span></span>

<span data-ttu-id="59ce6-176">De invoer van het begin van de invoer wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-176">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="59ce6-177">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="59ce6-177">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="59ce6-178">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-178">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="59ce6-179">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-179">BackwardKillWord</span></span>

<span data-ttu-id="59ce6-180">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-180">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="59ce6-181">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="59ce6-181">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="59ce6-182">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="59ce6-182">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="59ce6-183">Cmd: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-183">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="59ce6-184">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-184">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="59ce6-185">VI Invoeg modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-185">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="59ce6-186">VI-opdracht modus: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-186">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="59ce6-187">CancelLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-187">CancelLine</span></span>

<span data-ttu-id="59ce6-188">De huidige invoer annuleren, waardoor de invoer op het scherm wordt weer gegeven, maar terugkeert naar de host, zodat de prompt opnieuw wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-188">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="59ce6-189">VI Invoeg modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-189">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="59ce6-190">VI-opdracht modus: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-190">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="59ce6-191">Kopiëren</span><span class="sxs-lookup"><span data-stu-id="59ce6-191">Copy</span></span>

<span data-ttu-id="59ce6-192">Kopieer de geselecteerde regio naar het klem bord van het systeem.</span><span class="sxs-lookup"><span data-stu-id="59ce6-192">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="59ce6-193">Als er geen regio is geselecteerd, kopieert u de hele regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-193">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="59ce6-194">Cmd `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-194">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="59ce6-195">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-195">CopyOrCancelLine</span></span>

<span data-ttu-id="59ce6-196">Als tekst is geselecteerd, kopieert u deze naar het klem bord. anders annuleert u de regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-196">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="59ce6-197">Cmd `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-197">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="59ce6-198">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-198">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="59ce6-199">Knippen</span><span class="sxs-lookup"><span data-stu-id="59ce6-199">Cut</span></span>

<span data-ttu-id="59ce6-200">Geselecteerde regio verwijderen Verwijderde tekst in het systeem Klembord plaatsen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-200">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="59ce6-201">Cmd `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-201">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="59ce6-202">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-202">DeleteChar</span></span>

<span data-ttu-id="59ce6-203">Verwijder het teken onder de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-203">Delete the character under the cursor.</span></span>

- <span data-ttu-id="59ce6-204">Cmd `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-204">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="59ce6-205">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-205">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="59ce6-206">VI Invoeg modus: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-206">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="59ce6-207">VI-opdracht modus: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-207">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="59ce6-208">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="59ce6-208">DeleteCharOrExit</span></span>

<span data-ttu-id="59ce6-209">Verwijder het teken onder de cursor of als de regel leeg is, sluit u het proces.</span><span class="sxs-lookup"><span data-stu-id="59ce6-209">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="59ce6-210">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-210">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="59ce6-211">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="59ce6-211">DeleteEndOfBuffer</span></span>

<span data-ttu-id="59ce6-212">Hiermee verwijdert u aan het einde van de buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="59ce6-212">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="59ce6-213">VI-opdracht modus: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-213">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="59ce6-214">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-214">DeleteEndOfWord</span></span>

<span data-ttu-id="59ce6-215">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-215">Delete to the end of the word.</span></span>

- <span data-ttu-id="59ce6-216">VI-opdracht modus: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-216">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="59ce6-217">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-217">DeleteLine</span></span>

<span data-ttu-id="59ce6-218">Hiermee verwijdert u de huidige logische lijn van een buffer voor meerdere regels, waarbij u ongedaan maken inschakelt.</span><span class="sxs-lookup"><span data-stu-id="59ce6-218">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="59ce6-219">VI-opdracht modus: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-219">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="59ce6-220">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="59ce6-220">DeletePreviousLines</span></span>

<span data-ttu-id="59ce6-221">Hiermee verwijdert u de vorige aangevraagde logische regels en de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="59ce6-221">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="59ce6-222">VI-opdracht modus: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-222">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="59ce6-223">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="59ce6-223">DeleteRelativeLines</span></span>

<span data-ttu-id="59ce6-224">Verwijdert uit het begin van de buffer naar de huidige logische lijn in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="59ce6-224">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="59ce6-225">De meeste MS-DOS-opdrachten `<d,g,g>` kunnen worden voorafgegaan door een numeriek argument waarmee een absoluut regel nummer wordt opgegeven, samen met het huidige regel nummer, een bereik aan regels maken dat moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-225">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="59ce6-226">Als u niets opgeeft, wordt het numerieke argument standaard ingesteld op 1, dat verwijst naar de eerste logische lijn in een buffer met meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="59ce6-226">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="59ce6-227">Het werkelijke aantal regels dat uit de meerregelige moet worden verwijderd, wordt berekend als het verschil tussen het huidige logische regel nummer en het opgegeven numerieke argument. Dit kan dus negatief zijn.</span><span class="sxs-lookup"><span data-stu-id="59ce6-227">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="59ce6-228">Daarom is het _relatieve_ deel van de methode naam.</span><span class="sxs-lookup"><span data-stu-id="59ce6-228">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="59ce6-229">VI-opdracht modus: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-229">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="59ce6-230">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="59ce6-230">DeleteNextLines</span></span>

<span data-ttu-id="59ce6-231">Hiermee verwijdert u de huidige logische lijn en de volgende aangevraagde logische regels in een buffer voor meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="59ce6-231">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="59ce6-232">VI-opdracht modus: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-232">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="59ce6-233">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-233">DeleteLineToFirstChar</span></span>

<span data-ttu-id="59ce6-234">Hiermee wordt tekst van de cursor verwijderd naar het eerste niet-lege teken van de regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-234">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="59ce6-235">VI-opdracht modus: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-235">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="59ce6-236">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="59ce6-236">DeleteToEnd</span></span>

<span data-ttu-id="59ce6-237">Verwijderen tot aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-237">Delete to the end of the line.</span></span>

- <span data-ttu-id="59ce6-238">VI-opdracht modus: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-238">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="59ce6-239">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-239">DeleteWord</span></span>

<span data-ttu-id="59ce6-240">Verwijder het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-240">Delete the next word.</span></span>

- <span data-ttu-id="59ce6-241">VI-opdracht modus: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-241">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="59ce6-242">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-242">ForwardDeleteLine</span></span>

<span data-ttu-id="59ce6-243">Net als ForwardKillLine: verwijdert tekst van het punt naar het einde van de regel, maar plaatst de verwijderde tekst niet in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="59ce6-243">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="59ce6-244">Cmd `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-244">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="59ce6-245">VI Invoeg modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-245">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="59ce6-246">VI-opdracht modus: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-246">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="59ce6-247">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="59ce6-247">InsertLineAbove</span></span>

<span data-ttu-id="59ce6-248">Er wordt een nieuwe lege regel gemaakt op de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="59ce6-248">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="59ce6-249">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-249">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="59ce6-250">Cmd `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-250">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="59ce6-251">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="59ce6-251">InsertLineBelow</span></span>

<span data-ttu-id="59ce6-252">Er wordt een nieuwe lege regel gemaakt onder de huidige regel, ongeacht waar de cursor zich op de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="59ce6-252">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="59ce6-253">De cursor wordt verplaatst naar het begin van de nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-253">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="59ce6-254">Cmd `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-254">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="59ce6-255">InvertCase</span><span class="sxs-lookup"><span data-stu-id="59ce6-255">InvertCase</span></span>

<span data-ttu-id="59ce6-256">Het hoofdletter gebruik van het huidige teken omkeren en verplaatsen naar het volgende.</span><span class="sxs-lookup"><span data-stu-id="59ce6-256">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="59ce6-257">VI-opdracht modus: `<~>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-257">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="59ce6-258">KillLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-258">KillLine</span></span>

<span data-ttu-id="59ce6-259">De invoer wissen van de cursor tot het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-259">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="59ce6-260">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="59ce6-260">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="59ce6-261">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-261">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="59ce6-262">KillRegion</span><span class="sxs-lookup"><span data-stu-id="59ce6-262">KillRegion</span></span>

<span data-ttu-id="59ce6-263">Beëindig de tekst tussen de cursor en de markering.</span><span class="sxs-lookup"><span data-stu-id="59ce6-263">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="59ce6-264">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-264">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="59ce6-265">KillWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-265">KillWord</span></span>

<span data-ttu-id="59ce6-266">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-266">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="59ce6-267">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-267">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="59ce6-268">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="59ce6-268">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="59ce6-269">Cmd: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-269">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="59ce6-270">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-270">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="59ce6-271">VI Invoeg modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-271">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="59ce6-272">VI-opdracht modus: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-272">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="59ce6-273">Plakken</span><span class="sxs-lookup"><span data-stu-id="59ce6-273">Paste</span></span>

<span data-ttu-id="59ce6-274">Tekst van het klem bord van het systeem plakken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-274">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="59ce6-275">Cmd: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-275">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="59ce6-276">VI Invoeg modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-276">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="59ce6-277">VI-opdracht modus: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-277">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59ce6-278">Wanneer u de functie **Paste** gebruikt, wordt de volledige inhoud van de Klembord buffer geplakt in de invoer buffer van PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="59ce6-278">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="59ce6-279">De invoer buffer wordt vervolgens door gegeven aan de Power shell-parser.</span><span class="sxs-lookup"><span data-stu-id="59ce6-279">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="59ce6-280">Invoer die met de **rechter muisknop op** de plak methode van de console toepassing wordt geplakt, wordt met één teken per keer naar de invoer buffer gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-280">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="59ce6-281">De invoer buffer wordt door gegeven aan de parser wanneer een teken voor een nieuwe regel wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-281">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="59ce6-282">Daarom wordt de invoer één regel tegelijk geparseerd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-282">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="59ce6-283">Het verschil tussen plak methoden resulteert in een ander uitvoerings gedrag.</span><span class="sxs-lookup"><span data-stu-id="59ce6-283">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="59ce6-284">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="59ce6-284">PasteAfter</span></span>

<span data-ttu-id="59ce6-285">Plak het klem bord na de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-285">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="59ce6-286">VI-opdracht modus: `<p>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-286">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="59ce6-287">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="59ce6-287">PasteBefore</span></span>

<span data-ttu-id="59ce6-288">Plak het klem bord vóór de cursor door de cursor naar het einde van de geplakte tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-288">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="59ce6-289">VI-opdracht modus: `<P>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-289">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="59ce6-290">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="59ce6-290">PrependAndAccept</span></span>

<span data-ttu-id="59ce6-291">Laten voorafgaan door een ' # ' en accepteer de regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-291">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="59ce6-292">VI-opdracht modus: `<#>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-292">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="59ce6-293">Opnieuw uitvoeren</span><span class="sxs-lookup"><span data-stu-id="59ce6-293">Redo</span></span>

<span data-ttu-id="59ce6-294">Undo ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-294">Undo an undo.</span></span>

- <span data-ttu-id="59ce6-295">Cmd `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-295">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="59ce6-296">VI Invoeg modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-296">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="59ce6-297">VI-opdracht modus: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-297">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="59ce6-298">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="59ce6-298">RepeatLastCommand</span></span>

<span data-ttu-id="59ce6-299">Herhaal de laatste tekst wijziging.</span><span class="sxs-lookup"><span data-stu-id="59ce6-299">Repeat the last text modification.</span></span>

- <span data-ttu-id="59ce6-300">VI-opdracht modus: `<.>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-300">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="59ce6-301">RevertLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-301">RevertLine</span></span>

<span data-ttu-id="59ce6-302">Hiermee wordt alle invoer teruggezet naar de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-302">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="59ce6-303">Cmd `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-303">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="59ce6-304">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-304">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="59ce6-305">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-305">ShellBackwardKillWord</span></span>

<span data-ttu-id="59ce6-306">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-306">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="59ce6-307">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="59ce6-307">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="59ce6-308">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="59ce6-308">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="59ce6-309">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-309">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="59ce6-310">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-310">ShellKillWord</span></span>

<span data-ttu-id="59ce6-311">De invoer wissen van de cursor tot het einde van het huidige woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-311">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="59ce6-312">Als de cursor zich tussen woorden bevindt, wordt de invoer uit de cursor verwijderd naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-312">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="59ce6-313">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="59ce6-313">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="59ce6-314">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-314">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="59ce6-315">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="59ce6-315">SwapCharacters</span></span>

<span data-ttu-id="59ce6-316">Het huidige teken en de eerste vervangen door wisselen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-316">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="59ce6-317">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-317">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="59ce6-318">VI Invoeg modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-318">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="59ce6-319">VI-opdracht modus: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-319">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="59ce6-320">Ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="59ce6-320">Undo</span></span>

<span data-ttu-id="59ce6-321">Een vorige bewerking ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-321">Undo a previous edit.</span></span>

- <span data-ttu-id="59ce6-322">Cmd `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-322">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="59ce6-323">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-323">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="59ce6-324">VI Invoeg modus: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-324">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="59ce6-325">VI-opdracht modus: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-325">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="59ce6-326">UndoAll</span><span class="sxs-lookup"><span data-stu-id="59ce6-326">UndoAll</span></span>

<span data-ttu-id="59ce6-327">Alle vorige bewerkingen voor de regel ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-327">Undo all previous edits for line.</span></span>

- <span data-ttu-id="59ce6-328">VI-opdracht modus: `<U>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-328">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="59ce6-329">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="59ce6-329">UnixWordRubout</span></span>

<span data-ttu-id="59ce6-330">De invoer van het begin van het huidige woord wissen tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-330">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="59ce6-331">Als de cursor zich tussen woorden bevindt, wordt de invoer uit het begin van het vorige woord naar de cursor gewist.</span><span class="sxs-lookup"><span data-stu-id="59ce6-331">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="59ce6-332">De gewiste tekst wordt in de Kill-ring geplaatst.</span><span class="sxs-lookup"><span data-stu-id="59ce6-332">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="59ce6-333">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-333">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="59ce6-334">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-334">ValidateAndAcceptLine</span></span>

<span data-ttu-id="59ce6-335">Poging tot het uitvoeren van de huidige invoer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-335">Attempt to execute the current input.</span></span> <span data-ttu-id="59ce6-336">Als de huidige invoer onvolledig is (bijvoorbeeld omdat er een ontbrekend haakje sluiten, een accolade of een aanhalings teken ontbreekt), wordt de voortzettings prompt op de volgende regel weer gegeven en PSReadLine wacht op sleutels om de huidige invoer te bewerken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-336">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="59ce6-337">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-337">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="59ce6-338">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-338">ViAcceptLine</span></span>

<span data-ttu-id="59ce6-339">Accepteer de regel en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-339">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="59ce6-340">VI-opdracht modus: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-340">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="59ce6-341">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="59ce6-341">ViAcceptLineOrExit</span></span>

<span data-ttu-id="59ce6-342">Als DeleteCharOrExit in de Emacs-modus, maar wel in plaats van een teken te verwijderen, accepteert u de regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-342">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="59ce6-343">VI Invoeg modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-343">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="59ce6-344">VI-opdracht modus: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-344">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="59ce6-345">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-345">ViAppendLine</span></span>

<span data-ttu-id="59ce6-346">Er wordt een nieuwe regel ingevoegd onder de huidige regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-346">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="59ce6-347">VI-opdracht modus: `<o>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-347">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="59ce6-348">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="59ce6-348">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="59ce6-349">Hiermee verwijdert u het vorige woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-349">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="59ce6-350">VI-opdracht modus: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-350">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="59ce6-351">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="59ce6-351">ViBackwardGlob</span></span>

<span data-ttu-id="59ce6-352">Verplaatst de cursor terug naar het begin van het vorige woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="59ce6-352">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="59ce6-353">VI-opdracht modus: `<B>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-353">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="59ce6-354">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="59ce6-354">ViDeleteBrace</span></span>

<span data-ttu-id="59ce6-355">Zoek de accolade, het haakje sluiten of de vier Kante haken en verwijder alle inhoud binnen, inclusief de accolade.</span><span class="sxs-lookup"><span data-stu-id="59ce6-355">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="59ce6-356">VI-opdracht modus: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-356">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="59ce6-357">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="59ce6-357">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="59ce6-358">Verwijder aan het einde van het woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-358">Delete to the end of the word.</span></span>

- <span data-ttu-id="59ce6-359">VI-opdracht modus: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-359">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="59ce6-360">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="59ce6-360">ViDeleteGlob</span></span>

<span data-ttu-id="59ce6-361">De volgende Globs verwijderen (door witruimte gescheiden woord).</span><span class="sxs-lookup"><span data-stu-id="59ce6-361">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="59ce6-362">VI-opdracht modus: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-362">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="59ce6-363">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-363">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="59ce6-364">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-364">Deletes until given character.</span></span>

- <span data-ttu-id="59ce6-365">VI-opdracht modus: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-365">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="59ce6-366">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="59ce6-366">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="59ce6-367">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-367">Deletes until given character.</span></span>

- <span data-ttu-id="59ce6-368">VI-opdracht modus: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-368">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="59ce6-369">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-369">ViDeleteToChar</span></span>

<span data-ttu-id="59ce6-370">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-370">Deletes until given character.</span></span>

- <span data-ttu-id="59ce6-371">VI-opdracht modus: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-371">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="59ce6-372">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="59ce6-372">ViDeleteToCharBackward</span></span>

<span data-ttu-id="59ce6-373">Hiermee verwijdert u achterwaartse tekens tot aan het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-373">Deletes backwards until given character.</span></span>

- <span data-ttu-id="59ce6-374">VI-opdracht modus: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-374">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="59ce6-375">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="59ce6-375">ViInsertAtBegining</span></span>

<span data-ttu-id="59ce6-376">Schakel over naar de Invoeg modus en plaats de cursor aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-376">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="59ce6-377">VI-opdracht modus: `<I>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-377">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="59ce6-378">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="59ce6-378">ViInsertAtEnd</span></span>

<span data-ttu-id="59ce6-379">Schakel over naar de Invoeg modus en plaats de cursor aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-379">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="59ce6-380">VI-opdracht modus: `<A>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-380">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="59ce6-381">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-381">ViInsertLine</span></span>

<span data-ttu-id="59ce6-382">Boven de huidige regel wordt een nieuwe regel ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-382">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="59ce6-383">VI-opdracht modus: `<O>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-383">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="59ce6-384">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="59ce6-384">ViInsertWithAppend</span></span>

<span data-ttu-id="59ce6-385">Toevoegen vanaf de huidige regel positie.</span><span class="sxs-lookup"><span data-stu-id="59ce6-385">Append from the current line position.</span></span>

- <span data-ttu-id="59ce6-386">VI-opdracht modus: `<a>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-386">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="59ce6-387">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="59ce6-387">ViInsertWithDelete</span></span>

<span data-ttu-id="59ce6-388">Verwijder het huidige teken en schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-388">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="59ce6-389">VI-opdracht modus: `<s>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-389">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="59ce6-390">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="59ce6-390">ViJoinLines</span></span>

<span data-ttu-id="59ce6-391">De huidige regel en de volgende regel worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-391">Joins the current line and the next line.</span></span>

- <span data-ttu-id="59ce6-392">VI-opdracht modus: `<J>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-392">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="59ce6-393">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-393">ViReplaceLine</span></span>

<span data-ttu-id="59ce6-394">De volledige opdracht regel wissen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-394">Erase the entire command line.</span></span>

- <span data-ttu-id="59ce6-395">VI-opdracht modus: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-395">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="59ce6-396">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-396">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="59ce6-397">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-397">Replaces until given character.</span></span>

- <span data-ttu-id="59ce6-398">VI-opdracht modus: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-398">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="59ce6-399">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="59ce6-399">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="59ce6-400">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-400">Replaces until given character.</span></span>

- <span data-ttu-id="59ce6-401">VI-opdracht modus: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-401">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="59ce6-402">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-402">ViReplaceToChar</span></span>

<span data-ttu-id="59ce6-403">Hiermee verwijdert u tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-403">Deletes until given character.</span></span>

- <span data-ttu-id="59ce6-404">VI-opdracht modus: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-404">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="59ce6-405">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="59ce6-405">ViReplaceToCharBackward</span></span>

<span data-ttu-id="59ce6-406">Vervangt tot het opgegeven teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-406">Replaces until given character.</span></span>

- <span data-ttu-id="59ce6-407">VI-opdracht modus: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-407">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="59ce6-408">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-408">ViYankBeginningOfLine</span></span>

<span data-ttu-id="59ce6-409">Yank vanaf het begin van de buffer naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-409">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="59ce6-410">VI-opdracht modus: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-410">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="59ce6-411">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="59ce6-411">ViYankEndOfGlob</span></span>

<span data-ttu-id="59ce6-412">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="59ce6-412">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="59ce6-413">VI-opdracht modus: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-413">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="59ce6-414">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-414">ViYankEndOfWord</span></span>

<span data-ttu-id="59ce6-415">Yank van de cursor tot het einde van het (de) woord (en).</span><span class="sxs-lookup"><span data-stu-id="59ce6-415">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="59ce6-416">VI-opdracht modus: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-416">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="59ce6-417">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="59ce6-417">ViYankLeft</span></span>

<span data-ttu-id="59ce6-418">Yank teken (s) links van de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-418">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="59ce6-419">VI-opdracht modus: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-419">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="59ce6-420">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-420">ViYankLine</span></span>

<span data-ttu-id="59ce6-421">Yank de volledige buffer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-421">Yank the entire buffer.</span></span>

- <span data-ttu-id="59ce6-422">VI-opdracht modus: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-422">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="59ce6-423">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="59ce6-423">ViYankNextGlob</span></span>

<span data-ttu-id="59ce6-424">Yank van de cursor naar het begin van de volgende woord (en).</span><span class="sxs-lookup"><span data-stu-id="59ce6-424">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="59ce6-425">VI-opdracht modus: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-425">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="59ce6-426">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-426">ViYankNextWord</span></span>

<span data-ttu-id="59ce6-427">Yank het woord (en) na de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-427">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="59ce6-428">VI-opdracht modus: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-428">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="59ce6-429">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="59ce6-429">ViYankPercent</span></span>

<span data-ttu-id="59ce6-430">Yank naar/van overeenkomende accolade.</span><span class="sxs-lookup"><span data-stu-id="59ce6-430">Yank to/from matching brace.</span></span>

- <span data-ttu-id="59ce6-431">VI-opdracht modus: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-431">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="59ce6-432">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="59ce6-432">ViYankPreviousGlob</span></span>

<span data-ttu-id="59ce6-433">Yank vanaf het begin van het (de) woord (en) tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-433">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="59ce6-434">VI-opdracht modus: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-434">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="59ce6-435">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-435">ViYankPreviousWord</span></span>

<span data-ttu-id="59ce6-436">Yank de woorden vóór de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-436">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="59ce6-437">VI-opdracht modus: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-437">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="59ce6-438">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="59ce6-438">ViYankRight</span></span>

<span data-ttu-id="59ce6-439">Yank teken (s) onder en rechts van de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-439">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="59ce6-440">VI-opdracht modus: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-440">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="59ce6-441">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-441">ViYankToEndOfLine</span></span>

<span data-ttu-id="59ce6-442">Yank van de cursor tot het einde van de buffer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-442">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="59ce6-443">VI-opdracht modus: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-443">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="59ce6-444">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-444">ViYankToFirstChar</span></span>

<span data-ttu-id="59ce6-445">Yank van het eerste niet-spatie teken tot de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-445">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="59ce6-446">VI-opdracht modus: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-446">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="59ce6-447">Yank</span><span class="sxs-lookup"><span data-stu-id="59ce6-447">Yank</span></span>

<span data-ttu-id="59ce6-448">Voeg de meest recent afgebroken tekst toe aan de invoer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-448">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="59ce6-449">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-449">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="59ce6-450">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="59ce6-450">YankLastArg</span></span>

<span data-ttu-id="59ce6-451">Yank het laatste argument van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-451">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="59ce6-452">Met een argument, de eerste keer dat deze wordt aangeroepen, gedraagt zich op dezelfde manier als YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="59ce6-452">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="59ce6-453">Als meerdere keren worden aangeroepen, wordt door de geschiedenis en ARG de richting ingesteld (negatief de richting omkeren.)</span><span class="sxs-lookup"><span data-stu-id="59ce6-453">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="59ce6-454">Cmd `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-454">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="59ce6-455">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-455">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="59ce6-456">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="59ce6-456">YankNthArg</span></span>

<span data-ttu-id="59ce6-457">Yank het eerste argument (na de opdracht) van de vorige geschiedenis regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-457">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="59ce6-458">Met een argument, Yank het ne argument (vanaf 0), als het argument negatief is, begint vanaf het laatste argument.</span><span class="sxs-lookup"><span data-stu-id="59ce6-458">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="59ce6-459">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-459">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="59ce6-460">YankPop</span><span class="sxs-lookup"><span data-stu-id="59ce6-460">YankPop</span></span>

<span data-ttu-id="59ce6-461">Als de vorige bewerking Yank of YankPop is, vervangt u de eerder yanked tekst door de volgende afgebroken tekst van de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="59ce6-461">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="59ce6-462">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-462">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="59ce6-463">Functies voor cursor verplaatsing</span><span class="sxs-lookup"><span data-stu-id="59ce6-463">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="59ce6-464">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-464">BackwardChar</span></span>

<span data-ttu-id="59ce6-465">De cursor één teken naar links verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-465">Move the cursor one character to the left.</span></span> <span data-ttu-id="59ce6-466">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="59ce6-466">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="59ce6-467">Cmd `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-467">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="59ce6-468">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-468">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="59ce6-469">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-469">BackwardWord</span></span>

<span data-ttu-id="59ce6-470">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-470">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="59ce6-471">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="59ce6-471">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="59ce6-472">Cmd `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-472">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="59ce6-473">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-473">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="59ce6-474">VI Invoeg modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-474">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="59ce6-475">VI-opdracht modus: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-475">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="59ce6-476">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-476">BeginningOfLine</span></span>

<span data-ttu-id="59ce6-477">Als de invoer meerdere regels heeft, gaat u naar het begin van de huidige regel of gaat u naar het begin van de invoer als deze al aan het begin van de regel staat.</span><span class="sxs-lookup"><span data-stu-id="59ce6-477">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="59ce6-478">Als de invoer één regel heeft, gaat u naar het begin van de invoer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-478">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="59ce6-479">Cmd `<Home>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-479">Cmd: `<Home>`</span></span>
- <span data-ttu-id="59ce6-480">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-480">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="59ce6-481">VI Invoeg modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-481">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="59ce6-482">VI-opdracht modus: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-482">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="59ce6-483">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-483">EndOfLine</span></span>

<span data-ttu-id="59ce6-484">Als de invoer meerdere regels heeft, gaat u naar het einde van de huidige regel of gaat u naar het einde van de invoer als u aan het einde van de regel bent.</span><span class="sxs-lookup"><span data-stu-id="59ce6-484">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="59ce6-485">Als de invoer één regel heeft, gaat u naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-485">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="59ce6-486">Cmd `<End>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-486">Cmd: `<End>`</span></span>
- <span data-ttu-id="59ce6-487">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-487">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="59ce6-488">VI Invoeg modus: `<End>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-488">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="59ce6-489">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-489">ForwardChar</span></span>

<span data-ttu-id="59ce6-490">De cursor één teken naar rechts verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-490">Move the cursor one character to the right.</span></span> <span data-ttu-id="59ce6-491">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="59ce6-491">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="59ce6-492">Cmd `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-492">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="59ce6-493">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-493">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="59ce6-494">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-494">ForwardWord</span></span>

<span data-ttu-id="59ce6-495">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="59ce6-496">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="59ce6-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="59ce6-497">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-497">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="59ce6-498">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="59ce6-498">GotoBrace</span></span>

<span data-ttu-id="59ce6-499">Ga naar de accolade, haakjes of vier Kante haakjes.</span><span class="sxs-lookup"><span data-stu-id="59ce6-499">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="59ce6-500">Cmd `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-500">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="59ce6-501">VI Invoeg modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-501">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="59ce6-502">VI-opdracht modus: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-502">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="59ce6-503">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="59ce6-503">GotoColumn</span></span>

<span data-ttu-id="59ce6-504">Ga naar de kolom die wordt aangegeven door arg.</span><span class="sxs-lookup"><span data-stu-id="59ce6-504">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="59ce6-505">VI-opdracht modus: `<|>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-505">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="59ce6-506">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-506">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="59ce6-507">De cursor verplaatsen naar het eerste niet-lege teken in de regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-507">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="59ce6-508">VI-opdracht modus: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-508">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="59ce6-509">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-509">MoveToEndOfLine</span></span>

<span data-ttu-id="59ce6-510">De cursor verplaatsen naar het einde van de invoer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-510">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="59ce6-511">VI-opdracht modus: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-511">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="59ce6-512">NextLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-512">NextLine</span></span>

<span data-ttu-id="59ce6-513">De cursor verplaatsen naar de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-513">Move the cursor to the next line.</span></span>

- <span data-ttu-id="59ce6-514">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-514">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="59ce6-515">NextWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-515">NextWord</span></span>

<span data-ttu-id="59ce6-516">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-516">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="59ce6-517">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="59ce6-517">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="59ce6-518">Cmd `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-518">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="59ce6-519">VI Invoeg modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-519">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="59ce6-520">VI-opdracht modus: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-520">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="59ce6-521">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="59ce6-521">NextWordEnd</span></span>

<span data-ttu-id="59ce6-522">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-522">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="59ce6-523">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="59ce6-523">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="59ce6-524">VI-opdracht modus: `<e>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-524">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="59ce6-525">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-525">PreviousLine</span></span>

<span data-ttu-id="59ce6-526">Verplaats de cursor naar de vorige regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-526">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="59ce6-527">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-527">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="59ce6-528">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-528">ShellBackwardWord</span></span>

<span data-ttu-id="59ce6-529">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-529">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="59ce6-530">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="59ce6-530">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="59ce6-531">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-531">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="59ce6-532">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-532">ShellForwardWord</span></span>

<span data-ttu-id="59ce6-533">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-533">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="59ce6-534">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="59ce6-534">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="59ce6-535">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-535">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="59ce6-536">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-536">ShellNextWord</span></span>

<span data-ttu-id="59ce6-537">De cursor naar het einde van het huidige woord verplaatsen, of tussen woorden, naar het einde van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-537">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="59ce6-538">Grenzen van woorden worden gedefinieerd door Power shell-tokens.</span><span class="sxs-lookup"><span data-stu-id="59ce6-538">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="59ce6-539">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-539">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="59ce6-540">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-540">ViBackwardChar</span></span>

<span data-ttu-id="59ce6-541">De cursor één teken naar links verplaatsen in de bewerkings modus VI.</span><span class="sxs-lookup"><span data-stu-id="59ce6-541">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="59ce6-542">Hierdoor kan de cursor worden verplaatst naar de vorige regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="59ce6-542">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="59ce6-543">VI Invoeg modus: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-543">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="59ce6-544">VI-opdracht modus: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-544">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="59ce6-545">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-545">ViBackwardWord</span></span>

<span data-ttu-id="59ce6-546">De cursor weer naar het begin van het huidige woord verplaatsen of tussen woorden, het begin van het vorige woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-546">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="59ce6-547">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="59ce6-547">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="59ce6-548">VI-opdracht modus: `<b>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-548">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="59ce6-549">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-549">ViForwardChar</span></span>

<span data-ttu-id="59ce6-550">De cursor één teken naar rechts verplaatsen in de bewerkings modus VI.</span><span class="sxs-lookup"><span data-stu-id="59ce6-550">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="59ce6-551">Hierdoor kan de cursor worden verplaatst naar de volgende regel van de invoer op meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="59ce6-551">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="59ce6-552">VI Invoeg modus: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-552">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="59ce6-553">VI-opdracht modus: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-553">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="59ce6-554">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="59ce6-554">ViEndOfGlob</span></span>

<span data-ttu-id="59ce6-555">Verplaatst de cursor naar het einde van het woord, waarbij alleen spaties als scheidings teken worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="59ce6-555">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="59ce6-556">VI-opdracht modus: `<E>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-556">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="59ce6-557">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="59ce6-557">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="59ce6-558">Wordt verplaatst naar het einde van het vorige woord, waarbij alleen witruimte wordt gebruikt als woord als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-558">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="59ce6-559">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-559">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="59ce6-560">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="59ce6-560">ViGotoBrace</span></span>

<span data-ttu-id="59ce6-561">Vergelijkbaar met GotoBrace, maar is in plaats van op tokens gebaseerd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-561">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="59ce6-562">VI-opdracht modus: `<%>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-562">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="59ce6-563">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="59ce6-563">ViNextGlob</span></span>

<span data-ttu-id="59ce6-564">Verplaatst naar het volgende woord, waarbij alleen witruimte wordt gebruikt als woord scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-564">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="59ce6-565">VI-opdracht modus: `<W>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-565">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="59ce6-566">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-566">ViNextWord</span></span>

<span data-ttu-id="59ce6-567">De cursor voorwaarts verplaatsen naar het begin van het volgende woord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-567">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="59ce6-568">Grenzen van woorden worden gedefinieerd door een Configureer bare set tekens.</span><span class="sxs-lookup"><span data-stu-id="59ce6-568">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="59ce6-569">VI-opdracht modus: `<w>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-569">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="59ce6-570">Geschiedenis functies</span><span class="sxs-lookup"><span data-stu-id="59ce6-570">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="59ce6-571">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="59ce6-571">BeginningOfHistory</span></span>

<span data-ttu-id="59ce6-572">Hiermee gaat u naar het eerste item in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="59ce6-572">Move to the first item in the history.</span></span>

- <span data-ttu-id="59ce6-573">Emacs: `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-573">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="59ce6-574">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="59ce6-574">ClearHistory</span></span>

<span data-ttu-id="59ce6-575">Hiermee wist u de geschiedenis in PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="59ce6-575">Clears history in PSReadLine.</span></span> <span data-ttu-id="59ce6-576">Dit heeft geen invloed op de Power shell-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="59ce6-576">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="59ce6-577">Cmd `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-577">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="59ce6-578">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="59ce6-578">EndOfHistory</span></span>

<span data-ttu-id="59ce6-579">Hiermee gaat u naar het laatste item (de huidige invoer) in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="59ce6-579">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="59ce6-580">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-580">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="59ce6-581">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="59ce6-581">ForwardSearchHistory</span></span>

<span data-ttu-id="59ce6-582">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="59ce6-582">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="59ce6-583">Cmd `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-583">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="59ce6-584">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-584">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="59ce6-585">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="59ce6-585">HistorySearchBackward</span></span>

<span data-ttu-id="59ce6-586">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-586">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="59ce6-587">Cmd `<F8>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-587">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="59ce6-588">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="59ce6-588">HistorySearchForward</span></span>

<span data-ttu-id="59ce6-589">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis dat overeenkomt met de tekens tussen de start en de invoer en de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-589">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="59ce6-590">Cmd `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-590">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="59ce6-591">NextHistory</span><span class="sxs-lookup"><span data-stu-id="59ce6-591">NextHistory</span></span>

<span data-ttu-id="59ce6-592">Vervang de huidige invoer door het ' volgende ' item uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="59ce6-592">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="59ce6-593">Cmd `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-593">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="59ce6-594">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-594">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="59ce6-595">VI Invoeg modus: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-595">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="59ce6-596">VI-opdracht modus: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-596">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="59ce6-597">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="59ce6-597">PreviousHistory</span></span>

<span data-ttu-id="59ce6-598">Vervang de huidige invoer door het item ' Previous ' uit de PSReadLine-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="59ce6-598">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="59ce6-599">Cmd `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-599">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="59ce6-600">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-600">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="59ce6-601">VI Invoeg modus: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-601">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="59ce6-602">VI-opdracht modus: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="59ce6-602">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="59ce6-603">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="59ce6-603">ReverseSearchHistory</span></span>

<span data-ttu-id="59ce6-604">Voer een incrementele zoek opdracht uit met de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="59ce6-604">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="59ce6-605">Cmd `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-605">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="59ce6-606">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-606">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="59ce6-607">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="59ce6-607">ViSearchHistoryBackward</span></span>

<span data-ttu-id="59ce6-608">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="59ce6-608">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="59ce6-609">VI Invoeg modus: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-609">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="59ce6-610">VI-opdracht modus: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-610">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="59ce6-611">Voltooiings functies</span><span class="sxs-lookup"><span data-stu-id="59ce6-611">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="59ce6-612">Voltooid</span><span class="sxs-lookup"><span data-stu-id="59ce6-612">Complete</span></span>

<span data-ttu-id="59ce6-613">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-613">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="59ce6-614">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="59ce6-614">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="59ce6-615">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="59ce6-615">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="59ce6-616">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-616">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="59ce6-617">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="59ce6-617">MenuComplete</span></span>

<span data-ttu-id="59ce6-618">Poging tot het volt ooien van de tekst rondom de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-618">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="59ce6-619">Als er meerdere mogelijke afrondingen zijn, wordt het langste ondubbelzinnige voor voegsel gebruikt voor het volt ooien.</span><span class="sxs-lookup"><span data-stu-id="59ce6-619">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="59ce6-620">Als u probeert de langste ondubbelzinnige voltooiing te volt ooien, wordt een lijst met mogelijke voltooiingen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="59ce6-620">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="59ce6-621">Cmd: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-621">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="59ce6-622">Emacs: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-622">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="59ce6-623">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="59ce6-623">PossibleCompletions</span></span>

<span data-ttu-id="59ce6-624">De lijst met mogelijke aanvullingen weer geven.</span><span class="sxs-lookup"><span data-stu-id="59ce6-624">Display the list of possible completions.</span></span>

- <span data-ttu-id="59ce6-625">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-625">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="59ce6-626">VI Invoeg modus: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-626">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="59ce6-627">VI-opdracht modus: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-627">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="59ce6-628">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="59ce6-628">TabCompleteNext</span></span>

<span data-ttu-id="59ce6-629">Poging om de tekst rond de cursor te volt ooien met de volgende beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="59ce6-629">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="59ce6-630">Cmd `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-630">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="59ce6-631">VI-opdracht modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-631">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="59ce6-632">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="59ce6-632">TabCompletePrevious</span></span>

<span data-ttu-id="59ce6-633">Poging om de tekst rond de cursor te volt ooien met de vorige beschik bare voltooiing.</span><span class="sxs-lookup"><span data-stu-id="59ce6-633">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="59ce6-634">Cmd `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-634">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="59ce6-635">VI-opdracht modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-635">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="59ce6-636">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="59ce6-636">ViTabCompleteNext</span></span>

<span data-ttu-id="59ce6-637">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompleteNext aan.</span><span class="sxs-lookup"><span data-stu-id="59ce6-637">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="59ce6-638">VI Invoeg modus: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-638">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="59ce6-639">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="59ce6-639">ViTabCompletePrevious</span></span>

<span data-ttu-id="59ce6-640">Beëindigt de huidige bewerkings groep, indien nodig, en roept TabCompletePrevious aan.</span><span class="sxs-lookup"><span data-stu-id="59ce6-640">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="59ce6-641">VI Invoeg modus: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-641">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="59ce6-642">Diverse functies</span><span class="sxs-lookup"><span data-stu-id="59ce6-642">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="59ce6-643">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-643">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="59ce6-644">Het volgende woord van de inline of geselecteerde suggestie accepteren.</span><span class="sxs-lookup"><span data-stu-id="59ce6-644">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="59ce6-645">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-645">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="59ce6-646">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="59ce6-646">AcceptSuggestion</span></span>

<span data-ttu-id="59ce6-647">De huidige inline of geselecteerde suggestie accepteren.</span><span class="sxs-lookup"><span data-stu-id="59ce6-647">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="59ce6-648">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-648">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="59ce6-649">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="59ce6-649">CaptureScreen</span></span>

<span data-ttu-id="59ce6-650">Interactieve scherm opname starten-pijl-omhoog/omlaag Selecteer regels en voer de geselecteerde tekst als tekst en HTML naar het klem bord kopiëren.</span><span class="sxs-lookup"><span data-stu-id="59ce6-650">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="59ce6-651">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-651">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="59ce6-652">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="59ce6-652">ClearScreen</span></span>

<span data-ttu-id="59ce6-653">Schakel het scherm uit en teken de huidige regel boven aan het scherm.</span><span class="sxs-lookup"><span data-stu-id="59ce6-653">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="59ce6-654">Cmd `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-654">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="59ce6-655">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-655">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="59ce6-656">VI Invoeg modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-656">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="59ce6-657">VI-opdracht modus: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-657">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="59ce6-658">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="59ce6-658">DigitArgument</span></span>

<span data-ttu-id="59ce6-659">Start een nieuw cijfer argument om door te geven aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="59ce6-659">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="59ce6-660">Cmd: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="59ce6-660">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="59ce6-661">Emacs: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` , `<Alt+5>` , `<Alt+6>` , `<Alt+7>` , `<Alt+8>` , `<Alt+9>` , `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="59ce6-661">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="59ce6-662">VI-opdracht modus: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` , `<5>` , `<6>` , `<7>` , `<8>` , `<9>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-662">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="59ce6-663">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="59ce6-663">InvokePrompt</span></span>

<span data-ttu-id="59ce6-664">Hiermee wordt de huidige prompt gewist en wordt de functie Prompt aangeroepen om de prompt opnieuw weer te geven.</span><span class="sxs-lookup"><span data-stu-id="59ce6-664">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="59ce6-665">Dit is handig voor aangepaste sleutel afhandelingen die de status wijzigen, bijvoorbeeld de huidige map wijzigen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-665">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="59ce6-666">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-666">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="59ce6-667">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="59ce6-667">ScrollDisplayDown</span></span>

<span data-ttu-id="59ce6-668">De weer gave één scherm omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="59ce6-668">Scroll the display down one screen.</span></span>

- <span data-ttu-id="59ce6-669">Cmd `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-669">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="59ce6-670">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-670">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="59ce6-671">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-671">ScrollDisplayDownLine</span></span>

<span data-ttu-id="59ce6-672">De weer gave één regel omlaag schuiven.</span><span class="sxs-lookup"><span data-stu-id="59ce6-672">Scroll the display down one line.</span></span>

- <span data-ttu-id="59ce6-673">Cmd `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-673">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="59ce6-674">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-674">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="59ce6-675">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="59ce6-675">ScrollDisplayToCursor</span></span>

<span data-ttu-id="59ce6-676">Schuif de weer gave naar de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-676">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="59ce6-677">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-677">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="59ce6-678">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="59ce6-678">ScrollDisplayTop</span></span>

<span data-ttu-id="59ce6-679">Schuif de weer gave naar boven.</span><span class="sxs-lookup"><span data-stu-id="59ce6-679">Scroll the display to the top.</span></span>

- <span data-ttu-id="59ce6-680">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-680">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="59ce6-681">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="59ce6-681">ScrollDisplayUp</span></span>

<span data-ttu-id="59ce6-682">Schuif de weer gave één scherm omhoog.</span><span class="sxs-lookup"><span data-stu-id="59ce6-682">Scroll the display up one screen.</span></span>

- <span data-ttu-id="59ce6-683">Cmd `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-683">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="59ce6-684">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-684">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="59ce6-685">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-685">ScrollDisplayUpLine</span></span>

<span data-ttu-id="59ce6-686">De weer gave één regel omhoog schuiven.</span><span class="sxs-lookup"><span data-stu-id="59ce6-686">Scroll the display up one line.</span></span>

- <span data-ttu-id="59ce6-687">Cmd `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-687">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="59ce6-688">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-688">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="59ce6-689">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="59ce6-689">SelfInsert</span></span>

<span data-ttu-id="59ce6-690">Voeg de sleutel in.</span><span class="sxs-lookup"><span data-stu-id="59ce6-690">Insert the key.</span></span>

- <span data-ttu-id="59ce6-691">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-691">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="59ce6-692">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="59ce6-692">ShowKeyBindings</span></span>

<span data-ttu-id="59ce6-693">Alle gebonden sleutels weer geven.</span><span class="sxs-lookup"><span data-stu-id="59ce6-693">Show all bound keys.</span></span>

- <span data-ttu-id="59ce6-694">Cmd `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-694">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="59ce6-695">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-695">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="59ce6-696">VI Invoeg modus: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-696">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="59ce6-697">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="59ce6-697">ViCommandMode</span></span>

<span data-ttu-id="59ce6-698">Schakel de huidige bedrijfs modus uit van Vi-Insert naar de VI-opdracht.</span><span class="sxs-lookup"><span data-stu-id="59ce6-698">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="59ce6-699">VI Invoeg modus: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-699">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="59ce6-700">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="59ce6-700">ViDigitArgumentInChord</span></span>

<span data-ttu-id="59ce6-701">Start een nieuw cijfer argument om door te geven aan andere functies in een van de koorden van VI.</span><span class="sxs-lookup"><span data-stu-id="59ce6-701">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="59ce6-702">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-702">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="59ce6-703">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="59ce6-703">ViEditVisually</span></span>

<span data-ttu-id="59ce6-704">Bewerk de opdracht regel in een tekst editor die is opgegeven door $env: EDITOR of $env: VISUAL.</span><span class="sxs-lookup"><span data-stu-id="59ce6-704">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="59ce6-705">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-705">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="59ce6-706">VI-opdracht modus: `<v>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-706">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="59ce6-707">ViExit</span><span class="sxs-lookup"><span data-stu-id="59ce6-707">ViExit</span></span>

<span data-ttu-id="59ce6-708">Hiermee wordt de shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="59ce6-708">Exits the shell.</span></span>

- <span data-ttu-id="59ce6-709">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-709">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="59ce6-710">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="59ce6-710">ViInsertMode</span></span>

<span data-ttu-id="59ce6-711">Schakel over naar de modus invoegen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-711">Switch to Insert mode.</span></span>

- <span data-ttu-id="59ce6-712">VI-opdracht modus: `<i>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-712">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="59ce6-713">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="59ce6-713">WhatIsKey</span></span>

<span data-ttu-id="59ce6-714">Lees een sleutel en vertel me wat de sleutel is gebonden.</span><span class="sxs-lookup"><span data-stu-id="59ce6-714">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="59ce6-715">Cmd `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-715">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="59ce6-716">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-716">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="59ce6-717">Selectie functies</span><span class="sxs-lookup"><span data-stu-id="59ce6-717">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="59ce6-718">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="59ce6-718">ExchangePointAndMark</span></span>

<span data-ttu-id="59ce6-719">De cursor wordt op de locatie van het merk geplaatst en het vinkje wordt verplaatst naar de locatie van de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-719">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="59ce6-720">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-720">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="59ce6-721">SelectAll aanroepen</span><span class="sxs-lookup"><span data-stu-id="59ce6-721">SelectAll</span></span>

<span data-ttu-id="59ce6-722">Selecteer de volledige regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-722">Select the entire line.</span></span>

- <span data-ttu-id="59ce6-723">Cmd `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-723">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="59ce6-724">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-724">SelectBackwardChar</span></span>

<span data-ttu-id="59ce6-725">Pas de huidige selectie aan om het vorige teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="59ce6-725">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="59ce6-726">Cmd `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-726">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="59ce6-727">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-727">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="59ce6-728">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-728">SelectBackwardsLine</span></span>

<span data-ttu-id="59ce6-729">Pas de huidige selectie aan de cursor toe aan het begin van de regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-729">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="59ce6-730">Cmd `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-730">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="59ce6-731">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-731">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="59ce6-732">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-732">SelectBackwardWord</span></span>

<span data-ttu-id="59ce6-733">Pas de huidige selectie aan om het vorige woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="59ce6-733">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="59ce6-734">Cmd `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-734">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="59ce6-735">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-735">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="59ce6-736">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-736">SelectForwardChar</span></span>

<span data-ttu-id="59ce6-737">Pas de huidige selectie aan om het volgende teken op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="59ce6-737">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="59ce6-738">Cmd `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-738">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="59ce6-739">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-739">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="59ce6-740">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-740">SelectForwardWord</span></span>

<span data-ttu-id="59ce6-741">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-741">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="59ce6-742">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-742">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="59ce6-743">SelectLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-743">SelectLine</span></span>

<span data-ttu-id="59ce6-744">Pas de huidige selectie aan de cursor toe aan het einde van de regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-744">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="59ce6-745">Cmd `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-745">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="59ce6-746">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-746">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="59ce6-747">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-747">SelectNextWord</span></span>

<span data-ttu-id="59ce6-748">Pas de huidige selectie aan om het volgende woord op te laten staan.</span><span class="sxs-lookup"><span data-stu-id="59ce6-748">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="59ce6-749">Cmd `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-749">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="59ce6-750">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-750">SelectShellBackwardWord</span></span>

<span data-ttu-id="59ce6-751">Pas de huidige selectie aan om het vorige woord op te maken met behulp van ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-751">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="59ce6-752">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-752">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="59ce6-753">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-753">SelectShellForwardWord</span></span>

<span data-ttu-id="59ce6-754">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-754">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="59ce6-755">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-755">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="59ce6-756">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="59ce6-756">SelectShellNextWord</span></span>

<span data-ttu-id="59ce6-757">Pas de huidige selectie aan om het volgende woord in te voegen met behulp van ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="59ce6-757">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="59ce6-758">De functie is niet-afhankelijk.</span><span class="sxs-lookup"><span data-stu-id="59ce6-758">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="59ce6-759">SetMark</span><span class="sxs-lookup"><span data-stu-id="59ce6-759">SetMark</span></span>

<span data-ttu-id="59ce6-760">De huidige locatie van de cursor markeren voor gebruik in een volgende bewerkings opdracht.</span><span class="sxs-lookup"><span data-stu-id="59ce6-760">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="59ce6-761">Emacs: `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-761">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="59ce6-762">Voorspellende IntelliSense-functies</span><span class="sxs-lookup"><span data-stu-id="59ce6-762">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="59ce6-763">Voorspellende IntelliSense moet zijn ingeschakeld om deze functies te kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-763">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="59ce6-764">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="59ce6-764">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="59ce6-765">Hiermee wordt het volgende woord van de inline suggestie geaccepteerd van voorspellende IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="59ce6-765">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="59ce6-766">Deze functie kan worden gebonden met <kbd>CTRL</kbd> + <kbd>F</kbd> door de volgende opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="59ce6-766">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="59ce6-767">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="59ce6-767">AcceptSuggestion</span></span>

<span data-ttu-id="59ce6-768">Hiermee wordt de huidige inline suggestie van voorspellende IntelliSense geaccepteerd door op <kbd>RightArrow</kbd> te drukken wanneer de cursor zich aan het einde van de huidige regel bevindt.</span><span class="sxs-lookup"><span data-stu-id="59ce6-768">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="59ce6-769">Zoek functies</span><span class="sxs-lookup"><span data-stu-id="59ce6-769">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="59ce6-770">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="59ce6-770">CharacterSearch</span></span>

<span data-ttu-id="59ce6-771">Lees een teken en zoek voorwaarts naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-771">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="59ce6-772">Als er een argument is opgegeven, zoekt u voorwaarts (of achterwaarts als negatieve) voor het ne voorval.</span><span class="sxs-lookup"><span data-stu-id="59ce6-772">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="59ce6-773">Cmd `<F3>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-773">Cmd: `<F3>`</span></span>
- <span data-ttu-id="59ce6-774">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-774">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="59ce6-775">VI Invoeg modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-775">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="59ce6-776">VI-opdracht modus: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-776">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="59ce6-777">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="59ce6-777">CharacterSearchBackward</span></span>

<span data-ttu-id="59ce6-778">Lees een teken en zoek terug naar het volgende exemplaar van het teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-778">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="59ce6-779">Als er een argument is opgegeven, zoekt u terug (of als dit negatief is) voor het ne exemplaar.</span><span class="sxs-lookup"><span data-stu-id="59ce6-779">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="59ce6-780">Cmd `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-780">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="59ce6-781">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-781">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="59ce6-782">VI Invoeg modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-782">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="59ce6-783">VI-opdracht modus: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-783">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="59ce6-784">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="59ce6-784">RepeatLastCharSearch</span></span>

<span data-ttu-id="59ce6-785">De laatst opgenomen zoek opdracht herhalen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-785">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="59ce6-786">VI-opdracht modus: `<;>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-786">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="59ce6-787">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="59ce6-787">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="59ce6-788">De laatst opgenomen zoek opdracht herhalen, maar in tegenovergestelde richting.</span><span class="sxs-lookup"><span data-stu-id="59ce6-788">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="59ce6-789">VI-opdracht modus: `<,>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-789">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="59ce6-790">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="59ce6-790">RepeatSearch</span></span>

<span data-ttu-id="59ce6-791">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-791">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="59ce6-792">VI-opdracht modus: `<n>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-792">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="59ce6-793">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="59ce6-793">RepeatSearchBackward</span></span>

<span data-ttu-id="59ce6-794">Herhaal de laatste zoek opdracht in dezelfde richting als voorheen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-794">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="59ce6-795">VI-opdracht modus: `<N>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-795">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="59ce6-796">SearchChar</span><span class="sxs-lookup"><span data-stu-id="59ce6-796">SearchChar</span></span>

<span data-ttu-id="59ce6-797">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-797">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="59ce6-798">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="59ce6-798">This is for 't' functionality.</span></span>

- <span data-ttu-id="59ce6-799">VI-opdracht modus: `<f>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-799">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="59ce6-800">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="59ce6-800">SearchCharBackward</span></span>

<span data-ttu-id="59ce6-801">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-801">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="59ce6-802">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="59ce6-802">This is for 'T' functionality.</span></span>

- <span data-ttu-id="59ce6-803">VI-opdracht modus: `<F>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-803">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="59ce6-804">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="59ce6-804">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="59ce6-805">Lees het volgende teken en zoek het vervolgens naar achteren, en ga vervolgens terug naar een teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-805">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="59ce6-806">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="59ce6-806">This is for 'T' functionality.</span></span>

- <span data-ttu-id="59ce6-807">VI-opdracht modus: `<T>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-807">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="59ce6-808">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="59ce6-808">SearchCharWithBackoff</span></span>

<span data-ttu-id="59ce6-809">Lees het volgende teken, zoek het naar een later moment en maak een back-up van het teken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-809">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="59ce6-810">Dit is voor de ' on'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="59ce6-810">This is for 't' functionality.</span></span>

- <span data-ttu-id="59ce6-811">VI-opdracht modus: `<t>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-811">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="59ce6-812">SearchForward</span><span class="sxs-lookup"><span data-stu-id="59ce6-812">SearchForward</span></span>

<span data-ttu-id="59ce6-813">Vraagt om een zoek reeks en start de zoek opdracht op AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="59ce6-813">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="59ce6-814">VI Invoeg modus: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-814">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="59ce6-815">VI-opdracht modus: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="59ce6-815">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="59ce6-816">Aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="59ce6-816">Custom Key Bindings</span></span>

<span data-ttu-id="59ce6-817">PSReadLine ondersteunt aangepaste sleutel bindingen met behulp van de-cmdlet `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="59ce6-817">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="59ce6-818">De meeste aangepaste sleutel bindingen roepen een van de bovenstaande functies aan, bijvoorbeeld</span><span class="sxs-lookup"><span data-stu-id="59ce6-818">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="59ce6-819">U kunt een script Block binden aan een sleutel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-819">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="59ce6-820">Het script Block kan veel wat u wilt.</span><span class="sxs-lookup"><span data-stu-id="59ce6-820">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="59ce6-821">Enkele handige voor beelden zijn</span><span class="sxs-lookup"><span data-stu-id="59ce6-821">Some useful examples include</span></span>

- <span data-ttu-id="59ce6-822">de opdracht regel bewerken</span><span class="sxs-lookup"><span data-stu-id="59ce6-822">edit the command line</span></span>
- <span data-ttu-id="59ce6-823">een nieuw venster openen (bijvoorbeeld Help)</span><span class="sxs-lookup"><span data-stu-id="59ce6-823">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="59ce6-824">mappen wijzigen zonder de opdracht regel te wijzigen</span><span class="sxs-lookup"><span data-stu-id="59ce6-824">change directories without changing the command line</span></span>

<span data-ttu-id="59ce6-825">De script Block ontvangt twee argumenten:</span><span class="sxs-lookup"><span data-stu-id="59ce6-825">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="59ce6-826">`$key` -Een **[ConsoleKeyInfo]** -object dat de sleutel is die de aangepaste binding heeft geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-826">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="59ce6-827">Als u dezelfde script Block aan meerdere sleutels koppelt en verschillende acties moet uitvoeren, afhankelijk van de sleutel, kunt u $key controleren.</span><span class="sxs-lookup"><span data-stu-id="59ce6-827">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="59ce6-828">Veel aangepaste bindingen negeren dit argument.</span><span class="sxs-lookup"><span data-stu-id="59ce6-828">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="59ce6-829">`$arg` -Een wille keurig argument.</span><span class="sxs-lookup"><span data-stu-id="59ce6-829">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="59ce6-830">Meestal is dit een geheel getal dat de gebruiker door gegeven van de sleutel bindingen DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="59ce6-830">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="59ce6-831">Als uw binding geen argumenten accepteert, is het redelijk om dit argument te negeren.</span><span class="sxs-lookup"><span data-stu-id="59ce6-831">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="59ce6-832">Laten we een voor beeld bekijken waarmee een opdracht regel wordt toegevoegd aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="59ce6-832">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="59ce6-833">Dit is handig wanneer u ervoor hebt gekozen om iets te doen, maar niet opnieuw moet invoeren van de opdracht regel die u al hebt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-833">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="59ce6-834">U kunt veel meer voor beelden bekijken in het bestand `SamplePSReadLineProfile.ps1` dat is geïnstalleerd in de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="59ce6-834">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="59ce6-835">De meeste sleutel bindingen gebruiken enkele hulp functies voor het bewerken van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-835">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="59ce6-836">Deze Api's worden beschreven in de volgende sectie.</span><span class="sxs-lookup"><span data-stu-id="59ce6-836">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="59ce6-837">Api's voor de ondersteuning van aangepaste sleutel bindingen</span><span class="sxs-lookup"><span data-stu-id="59ce6-837">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="59ce6-838">De volgende functies zijn openbaar in micro soft. Power shell. PSConsoleReadLine, maar kunnen niet rechtstreeks aan een sleutel worden gebonden.</span><span class="sxs-lookup"><span data-stu-id="59ce6-838">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="59ce6-839">De meeste zijn handig in aangepaste sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-839">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="59ce6-840">Een opdracht regel toevoegen aan de geschiedenis zonder deze uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="59ce6-840">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="59ce6-841">Wis de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="59ce6-841">Clear the kill-ring.</span></span>  <span data-ttu-id="59ce6-842">Dit wordt meestal gebruikt voor het testen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-842">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="59ce6-843">Verwijder de lengte tekens uit het begin.</span><span class="sxs-lookup"><span data-stu-id="59ce6-843">Delete length characters from start.</span></span>  <span data-ttu-id="59ce6-844">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="59ce6-844">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="59ce6-845">Voer de actie opname uit op basis van de voor keuren van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="59ce6-845">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="59ce6-846">Deze twee functies halen nuttige informatie op over de huidige status van de invoer buffer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-846">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="59ce6-847">De eerste wordt vaak gebruikt voor eenvoudige gevallen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-847">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="59ce6-848">De tweede wordt gebruikt als uw binding iets geavanceerder gaat met de AST.</span><span class="sxs-lookup"><span data-stu-id="59ce6-848">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="59ce6-849">Deze twee functies worden gebruikt door `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="59ce6-849">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="59ce6-850">De eerste wordt gebruikt om alle sleutel bindingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-850">The first is used to get all key bindings.</span></span> <span data-ttu-id="59ce6-851">De tweede wordt gebruikt voor het ophalen van specifieke sleutel bindingen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-851">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="59ce6-852">Deze functie wordt gebruikt door Get-PSReadLineOption en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="59ce6-852">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="59ce6-853">Als er niets is geselecteerd op de opdracht regel, wordt-1 geretourneerd in zowel start als length.</span><span class="sxs-lookup"><span data-stu-id="59ce6-853">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="59ce6-854">Als er een selectie is op de opdracht regel, worden het begin en de lengte van de selectie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="59ce6-854">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="59ce6-855">Voeg een teken of teken reeks toe aan de cursor.</span><span class="sxs-lookup"><span data-stu-id="59ce6-855">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="59ce6-856">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="59ce6-856">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="59ce6-857">Dit is het belangrijkste ingangs punt voor PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="59ce6-857">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="59ce6-858">Er wordt geen recursie ondersteund, dus is niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="59ce6-858">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="59ce6-859">Deze functie wordt gebruikt door Remove-PSReadLineKeyHandler en is waarschijnlijk niet nuttig in een aangepaste sleutel binding.</span><span class="sxs-lookup"><span data-stu-id="59ce6-859">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="59ce6-860">Vervang een deel van de invoer.</span><span class="sxs-lookup"><span data-stu-id="59ce6-860">Replace some of the input.</span></span> <span data-ttu-id="59ce6-861">Met deze bewerking wordt ongedaan maken/opnieuw uitvoeren ondersteund.</span><span class="sxs-lookup"><span data-stu-id="59ce6-861">This operation supports undo/redo.</span></span> <span data-ttu-id="59ce6-862">U kunt het beste verwijderen gevolgd door INSERT, omdat het wordt beschouwd als één actie voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-862">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="59ce6-863">De cursor verplaatsen naar de opgegeven verschuiving.</span><span class="sxs-lookup"><span data-stu-id="59ce6-863">Move the cursor to the given offset.</span></span> <span data-ttu-id="59ce6-864">Cursor verplaatsing wordt niet bijgehouden voor ongedaan maken.</span><span class="sxs-lookup"><span data-stu-id="59ce6-864">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="59ce6-865">Deze functie is een helper-methode die wordt gebruikt door de cmdlet Set-PSReadLineOption, maar kan handig zijn voor een aangepaste sleutel binding die tijdelijk een instelling wil wijzigen.</span><span class="sxs-lookup"><span data-stu-id="59ce6-865">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="59ce6-866">Deze Help methode wordt gebruikt voor aangepaste bindingen die voldoen aan DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="59ce6-866">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="59ce6-867">Een typische aanroep ziet eruit als</span><span class="sxs-lookup"><span data-stu-id="59ce6-867">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="59ce6-868">Notitie</span><span class="sxs-lookup"><span data-stu-id="59ce6-868">Note</span></span>

### <a name="command-history"></a><span data-ttu-id="59ce6-869">Opdracht geschiedenis</span><span class="sxs-lookup"><span data-stu-id="59ce6-869">Command History</span></span>

<span data-ttu-id="59ce6-870">PSReadLine onderhoudt een geschiedenis bestand met alle opdrachten en gegevens die u hebt ingevoerd op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="59ce6-870">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="59ce6-871">Dit kan gevoelige gegevens bevatten, inclusief wacht woorden.</span><span class="sxs-lookup"><span data-stu-id="59ce6-871">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="59ce6-872">Als u bijvoorbeeld de cmdlet gebruikt, `ConvertTo-SecureString` wordt het wacht woord in het geschiedenis bestand vastgelegd als tekst zonder opmaak.</span><span class="sxs-lookup"><span data-stu-id="59ce6-872">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="59ce6-873">De geschiedenis bestanden zijn een bestand met de naam `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="59ce6-873">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="59ce6-874">Op Windows-systemen wordt het geschiedenis bestand opgeslagen op `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="59ce6-874">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="59ce6-875">Op niet-Windows-systemen worden de geschiedenis bestanden opgeslagen in `$env:XDG_DATA_HOME/powershell/PSReadLine` of `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="59ce6-875">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="59ce6-876">Feedback & bijdragen aan PSReadLine</span><span class="sxs-lookup"><span data-stu-id="59ce6-876">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="59ce6-877">PSReadLine op GitHub</span><span class="sxs-lookup"><span data-stu-id="59ce6-877">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="59ce6-878">U kunt een pull-aanvraag verzenden of feedback verzenden op de pagina GitHub.</span><span class="sxs-lookup"><span data-stu-id="59ce6-878">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="59ce6-879">Zie ook</span><span class="sxs-lookup"><span data-stu-id="59ce6-879">See Also</span></span>

<span data-ttu-id="59ce6-880">PSReadLine wordt sterk beïnvloed door de GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="59ce6-880">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
