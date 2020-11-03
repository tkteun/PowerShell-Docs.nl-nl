---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: d3e3ee1dcde36ac09f8441aff7ce48797cf48b5f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250667"
---
# <span data-ttu-id="422d3-103">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="422d3-103">Set-PSReadLineOption</span></span>

## <span data-ttu-id="422d3-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="422d3-104">Synopsis</span></span>
<span data-ttu-id="422d3-105">Het gedrag van het bewerken van opdracht regels in **PSReadLine** aanpassen.</span><span class="sxs-lookup"><span data-stu-id="422d3-105">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

## <span data-ttu-id="422d3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="422d3-106">Syntax</span></span>

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-Colors <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="422d3-107">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="422d3-107">Description</span></span>

<span data-ttu-id="422d3-108">`Set-PSReadLineOption`Met de cmdlet wordt het gedrag van de **PSReadLine** -module aangepast wanneer u de opdracht regel bewerkt.</span><span class="sxs-lookup"><span data-stu-id="422d3-108">The `Set-PSReadLineOption` cmdlet customizes the behavior of the **PSReadLine** module when you're editing the command line.</span></span> <span data-ttu-id="422d3-109">Als u de **PSReadLine** -instellingen wilt weer geven, gebruikt u `Get-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="422d3-109">To view the **PSReadLine** settings, use `Get-PSReadLineOption`.</span></span>

## <span data-ttu-id="422d3-110">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="422d3-110">Examples</span></span>

### <span data-ttu-id="422d3-111">Voor beeld 1: voorgrond-en achtergrond kleuren instellen</span><span class="sxs-lookup"><span data-stu-id="422d3-111">Example 1: Set foreground and background colors</span></span>

<span data-ttu-id="422d3-112">In dit voor beeld wordt **PSReadLine** ingesteld om het **opmerkings** token met groene voorgrond tekst op een grijze achtergrond weer te geven.</span><span class="sxs-lookup"><span data-stu-id="422d3-112">This example sets **PSReadLine** to display the **Comment** token with green foreground text on a gray background.</span></span> <span data-ttu-id="422d3-113">In de escape-reeks die in het voor beeld wordt gebruikt, vertegenwoordigt **32** de voorgrond kleur en **47** de achtergrond kleur.</span><span class="sxs-lookup"><span data-stu-id="422d3-113">In the escape sequence used in the example, **32** represents the foreground color and **47** represents the background color.</span></span>

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

<span data-ttu-id="422d3-114">U kunt ervoor kiezen om alleen een voorgrond tekst kleur in te stellen.</span><span class="sxs-lookup"><span data-stu-id="422d3-114">You can choose to set only a foreground text color.</span></span> <span data-ttu-id="422d3-115">Bijvoorbeeld een heldere, groene voorgrond tekst kleur voor het **opmerkings** token: ``"Comment"="`e[92m"`` .</span><span class="sxs-lookup"><span data-stu-id="422d3-115">For example, a bright green foreground text color for the **Comment** token: ``"Comment"="`e[92m"``.</span></span>

### <span data-ttu-id="422d3-116">Voor beeld 2: de stijl van de Bel instellen</span><span class="sxs-lookup"><span data-stu-id="422d3-116">Example 2: Set bell style</span></span>

<span data-ttu-id="422d3-117">In dit voor beeld reageert **PSReadLine** op fouten of voor waarden waarvoor aandacht van de gebruiker is vereist.</span><span class="sxs-lookup"><span data-stu-id="422d3-117">In this example, **PSReadLine** will respond to errors or conditions that require user attention.</span></span>
<span data-ttu-id="422d3-118">De **BellStyle** is ingesteld voor het verzenden van een hoorbaar pieptoon bij 1221 Hz voor 60 MS.</span><span class="sxs-lookup"><span data-stu-id="422d3-118">The **BellStyle** is set to emit an audible beep at 1221 Hz for 60 ms.</span></span>

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> <span data-ttu-id="422d3-119">Deze functie werkt mogelijk niet op alle hosts op platforms.</span><span class="sxs-lookup"><span data-stu-id="422d3-119">This feature may not work in all hosts on platforms.</span></span>

### <span data-ttu-id="422d3-120">Voor beeld 3: meerdere opties instellen</span><span class="sxs-lookup"><span data-stu-id="422d3-120">Example 3: Set multiple options</span></span>

<span data-ttu-id="422d3-121">`Set-PSReadLineOption` kan meerdere opties instellen met een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="422d3-121">`Set-PSReadLineOption` can set multiple options with a hash table.</span></span>

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

<span data-ttu-id="422d3-122">In de `$PSReadLineOptions` tabel hash worden de sleutels en waarden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="422d3-122">The `$PSReadLineOptions` hash table sets the keys and values.</span></span> <span data-ttu-id="422d3-123">`Set-PSReadLineOption` gebruikt de sleutels en waarden met `@PSReadLineOptions` om de **PSReadLine** -opties bij te werken.</span><span class="sxs-lookup"><span data-stu-id="422d3-123">`Set-PSReadLineOption` uses the keys and values with `@PSReadLineOptions` to update the **PSReadLine** options.</span></span>

<span data-ttu-id="422d3-124">U kunt de sleutels en waarden voor het invoeren van de naam van de hash-tabel weer geven `$PSReadLineOptions` op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="422d3-124">You can view the keys and values entering the hash table name, `$PSReadLineOptions` on the PowerShell command line.</span></span>

### <span data-ttu-id="422d3-125">Voor beeld 4: meerdere kleur opties instellen</span><span class="sxs-lookup"><span data-stu-id="422d3-125">Example 4: Set multiple color options</span></span>

<span data-ttu-id="422d3-126">In dit voor beeld ziet u hoe u in één opdracht meer dan één kleur waarde kunt instellen.</span><span class="sxs-lookup"><span data-stu-id="422d3-126">This example shows how to set more than one color value in a single command.</span></span>

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### <span data-ttu-id="422d3-127">Voor beeld 5: kleur waarden instellen voor meerdere typen</span><span class="sxs-lookup"><span data-stu-id="422d3-127">Example 5: Set color values for multiple types</span></span>

<span data-ttu-id="422d3-128">Dit voor beeld toont drie verschillende methoden voor het instellen van de kleur van tokens die worden weer gegeven in **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="422d3-128">This example shows three different methods for how to set the color of tokens displayed in **PSReadLine**.</span></span>

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### <span data-ttu-id="422d3-129">Voor beeld 6: ViModeChangeHandler gebruiken om wijzigingen in de modus in de VI weer te geven</span><span class="sxs-lookup"><span data-stu-id="422d3-129">Example 6: Use ViModeChangeHandler to display Vi mode changes</span></span>

<span data-ttu-id="422d3-130">In dit voor beeld wordt een cursor wijziging een VT-Escape verzonden in reactie op een wijziging in de **VI** -modus.</span><span class="sxs-lookup"><span data-stu-id="422d3-130">This example emits a cursor change VT escape in response to a **Vi** mode change.</span></span>

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "`e[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "`e[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

<span data-ttu-id="422d3-131">De functie **OnViModeChange** stelt de cursor opties in voor de **VI** -modi: insert en Command.</span><span class="sxs-lookup"><span data-stu-id="422d3-131">The **OnViModeChange** function sets the cursor options for the **Vi** modes: insert and command.</span></span>
<span data-ttu-id="422d3-132">**ViModeChangeHandler** maakt gebruik van de `Function:` provider om te verwijzen naar **OnViModeChange** als een script blok-object.</span><span class="sxs-lookup"><span data-stu-id="422d3-132">**ViModeChangeHandler** uses the `Function:` provider to reference **OnViModeChange** as a script block object.</span></span>

<span data-ttu-id="422d3-133">Zie [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="422d3-133">For more information, see [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span></span>

## <span data-ttu-id="422d3-134">Parameters</span><span class="sxs-lookup"><span data-stu-id="422d3-134">Parameters</span></span>

### <span data-ttu-id="422d3-135">-AddToHistoryHandler</span><span class="sxs-lookup"><span data-stu-id="422d3-135">-AddToHistoryHandler</span></span>

<span data-ttu-id="422d3-136">Hiermee geeft u een **script Block** op die bepaalt welke opdrachten aan de **PSReadLine** -geschiedenis worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="422d3-136">Specifies a **ScriptBlock** that controls which commands get added to **PSReadLine** history.</span></span>

<span data-ttu-id="422d3-137">De **script Block** ontvangt de opdracht regel als invoer.</span><span class="sxs-lookup"><span data-stu-id="422d3-137">The **ScriptBlock** receives the command line as input.</span></span> <span data-ttu-id="422d3-138">Als de **script Block** wordt geretourneerd `$True` , wordt de opdracht regel aan de geschiedenis toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="422d3-138">If the **ScriptBlock** returns `$True`, the command line is added to the history.</span></span>

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-139">-AnsiEscapeTimeout</span><span class="sxs-lookup"><span data-stu-id="422d3-139">-AnsiEscapeTimeout</span></span>

<span data-ttu-id="422d3-140">Deze optie is specifiek voor Windows wanneer invoer wordt omgeleid, bijvoorbeeld wanneer deze wordt uitgevoerd onder `tmux` of `screen` .</span><span class="sxs-lookup"><span data-stu-id="422d3-140">This option is specific to Windows when input is redirected, for example, when running under `tmux` or `screen`.</span></span>

<span data-ttu-id="422d3-141">Met omgeleide invoer in Windows worden veel sleutels verzonden als een reeks tekens die beginnen met het escape-teken.</span><span class="sxs-lookup"><span data-stu-id="422d3-141">With redirected input on Windows, many keys are sent as a sequence of characters starting with the escape character.</span></span> <span data-ttu-id="422d3-142">Het is niet mogelijk om onderscheid te maken tussen één escape teken, gevolgd door meer tekens en een geldige escape reeks.</span><span class="sxs-lookup"><span data-stu-id="422d3-142">It's impossible to distinguish between a single escape character followed by more characters and a valid escape sequence.</span></span>

<span data-ttu-id="422d3-143">De veronderstelling is dat de Terminal de tekens sneller kan verzenden dan een gebruiker typt.</span><span class="sxs-lookup"><span data-stu-id="422d3-143">The assumption is that the terminal can send the characters faster than a user types.</span></span> <span data-ttu-id="422d3-144">**PSReadLine** wacht op deze time-out voordat wordt geconcludeerd dat er een volledige escape reeks is ontvangen.</span><span class="sxs-lookup"><span data-stu-id="422d3-144">**PSReadLine** waits for this timeout before concluding that it has received a complete escape sequence.</span></span>

<span data-ttu-id="422d3-145">Als u wille keurige of onverwachte tekens ziet wanneer u typt, kunt u deze time-out aanpassen.</span><span class="sxs-lookup"><span data-stu-id="422d3-145">If you see random or unexpected characters when you type, you can adjust this timeout.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-146">-BellStyle</span><span class="sxs-lookup"><span data-stu-id="422d3-146">-BellStyle</span></span>

<span data-ttu-id="422d3-147">Hiermee geeft u op hoe **PSReadLine** reageert op verschillende fout-en ambigue voor waarden.</span><span class="sxs-lookup"><span data-stu-id="422d3-147">Specifies how **PSReadLine** responds to various error and ambiguous conditions.</span></span>

<span data-ttu-id="422d3-148">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="422d3-148">The valid values are as follows:</span></span>

- <span data-ttu-id="422d3-149">**Hoorbaar** : een korte piep Toon.</span><span class="sxs-lookup"><span data-stu-id="422d3-149">**Audible** : A short beep.</span></span>
- <span data-ttu-id="422d3-150">**Visueel** : tekst knippert even.</span><span class="sxs-lookup"><span data-stu-id="422d3-150">**Visual** : Text flashes briefly.</span></span>
- <span data-ttu-id="422d3-151">**Geen: geen** feedback.</span><span class="sxs-lookup"><span data-stu-id="422d3-151">**None** : No feedback.</span></span>

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-152">-Kleuren</span><span class="sxs-lookup"><span data-stu-id="422d3-152">-Colors</span></span>

<span data-ttu-id="422d3-153">De para meter **kleuren** bevat verschillende kleuren die worden gebruikt door **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="422d3-153">The **Colors** parameter specifies various colors used by **PSReadLine**.</span></span>

<span data-ttu-id="422d3-154">Het argument is een hash-tabel waarin de sleutels opgeven welk element en welke waarden de kleur opgeven.</span><span class="sxs-lookup"><span data-stu-id="422d3-154">The argument is a hash table where the keys specify which element and the values specify the color.</span></span>
<span data-ttu-id="422d3-155">Zie [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="422d3-155">For more information, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="422d3-156">Kleuren kunnen bestaan uit een waarde van **ConsoleColor** , bijvoorbeeld `[ConsoleColor]::Red` of een geldige ANSI-escape reeks.</span><span class="sxs-lookup"><span data-stu-id="422d3-156">Colors can be either a value from **ConsoleColor** , for example `[ConsoleColor]::Red`, or a valid ANSI escape sequence.</span></span> <span data-ttu-id="422d3-157">Geldige escape reeksen zijn afhankelijk van uw Terminal.</span><span class="sxs-lookup"><span data-stu-id="422d3-157">Valid escape sequences depend on your terminal.</span></span> <span data-ttu-id="422d3-158">In Power shell 5,0 is een voor beeld van een escape reeks voor rode tekst `$([char]0x1b)[91m` .</span><span class="sxs-lookup"><span data-stu-id="422d3-158">In PowerShell 5.0, an example escape sequence for red text is `$([char]0x1b)[91m`.</span></span> <span data-ttu-id="422d3-159">In Power shell 6 en hoger is dezelfde escape reeks `` `e[91m`` .</span><span class="sxs-lookup"><span data-stu-id="422d3-159">In PowerShell 6 and above, the same escape sequence is `` `e[91m``.</span></span> <span data-ttu-id="422d3-160">U kunt andere escape reeksen opgeven, met inbegrip van de volgende typen:</span><span class="sxs-lookup"><span data-stu-id="422d3-160">You can specify other escape sequences including the following types:</span></span>

- <span data-ttu-id="422d3-161">256-kleur</span><span class="sxs-lookup"><span data-stu-id="422d3-161">256 color</span></span>
- <span data-ttu-id="422d3-162">24-bits kleur</span><span class="sxs-lookup"><span data-stu-id="422d3-162">24-bit color</span></span>
- <span data-ttu-id="422d3-163">Voor grond, achtergrond of beide</span><span class="sxs-lookup"><span data-stu-id="422d3-163">Foreground, background, or both</span></span>
- <span data-ttu-id="422d3-164">Inverse, vet</span><span class="sxs-lookup"><span data-stu-id="422d3-164">Inverse, bold</span></span>

<span data-ttu-id="422d3-165">Zie [ANSI escape-code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia voor meer informatie over ANSI-kleur codes.</span><span class="sxs-lookup"><span data-stu-id="422d3-165">For more information about ANSI color codes, see [ANSI escape code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia.</span></span>

<span data-ttu-id="422d3-166">De geldige sleutels zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="422d3-166">The valid keys include:</span></span>

- <span data-ttu-id="422d3-167">**ContinuationPrompt** : de kleur van de voortzettings prompt.</span><span class="sxs-lookup"><span data-stu-id="422d3-167">**ContinuationPrompt** : The color of the continuation prompt.</span></span>
- <span data-ttu-id="422d3-168">**Nadruk** : de kleur van de nadruk.</span><span class="sxs-lookup"><span data-stu-id="422d3-168">**Emphasis** : The emphasis color.</span></span> <span data-ttu-id="422d3-169">Bijvoorbeeld, de overeenkomende tekst bij het zoeken van de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="422d3-169">For example, the matching text when searching history.</span></span>
- <span data-ttu-id="422d3-170">**Fout** : de fout kleur.</span><span class="sxs-lookup"><span data-stu-id="422d3-170">**Error** : The error color.</span></span> <span data-ttu-id="422d3-171">Bijvoorbeeld in de prompt.</span><span class="sxs-lookup"><span data-stu-id="422d3-171">For example, in the prompt.</span></span>
- <span data-ttu-id="422d3-172">**Selectie** : de kleur voor het markeren van de menu selectie of de geselecteerde tekst.</span><span class="sxs-lookup"><span data-stu-id="422d3-172">**Selection** : The color to highlight the menu selection or selected text.</span></span>
- <span data-ttu-id="422d3-173">**Standaard** : de kleur van het standaard token.</span><span class="sxs-lookup"><span data-stu-id="422d3-173">**Default** : The default token color.</span></span>
- <span data-ttu-id="422d3-174">**Opmerking** : de kleur van het opmerkings token.</span><span class="sxs-lookup"><span data-stu-id="422d3-174">**Comment** : The comment token color.</span></span>
- <span data-ttu-id="422d3-175">**Sleutel woord** : de kleur van het trefwoord token.</span><span class="sxs-lookup"><span data-stu-id="422d3-175">**Keyword** : The keyword token color.</span></span>
- <span data-ttu-id="422d3-176">**Teken reeks** : de kleur van het teken reeks token.</span><span class="sxs-lookup"><span data-stu-id="422d3-176">**String** : The string token color.</span></span>
- <span data-ttu-id="422d3-177">**Operator** : de kleur van de operator token.</span><span class="sxs-lookup"><span data-stu-id="422d3-177">**Operator** : The operator token color.</span></span>
- <span data-ttu-id="422d3-178">**Variabele** : de kleur van het variabele token.</span><span class="sxs-lookup"><span data-stu-id="422d3-178">**Variable** : The variable token color.</span></span>
- <span data-ttu-id="422d3-179">**Opdracht** : de kleur van het opdracht token.</span><span class="sxs-lookup"><span data-stu-id="422d3-179">**Command** : The command token color.</span></span>
- <span data-ttu-id="422d3-180">**Para meter** : de kleur van het parameter token.</span><span class="sxs-lookup"><span data-stu-id="422d3-180">**Parameter** : The parameter token color.</span></span>
- <span data-ttu-id="422d3-181">**Type** : het type token kleur.</span><span class="sxs-lookup"><span data-stu-id="422d3-181">**Type** : The type token color.</span></span>
- <span data-ttu-id="422d3-182">**Getal** : de kleur van het cijfer token.</span><span class="sxs-lookup"><span data-stu-id="422d3-182">**Number** : The number token color.</span></span>
- <span data-ttu-id="422d3-183">**Lid** : de kleur van het token van de leden naam.</span><span class="sxs-lookup"><span data-stu-id="422d3-183">**Member** : The member name token color.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-184">-CommandValidationHandler</span><span class="sxs-lookup"><span data-stu-id="422d3-184">-CommandValidationHandler</span></span>

<span data-ttu-id="422d3-185">Hiermee geeft u een **script Block** die wordt aangeroepen vanuit **ValidateAndAcceptLine**.</span><span class="sxs-lookup"><span data-stu-id="422d3-185">Specifies a **ScriptBlock** that is called from **ValidateAndAcceptLine**.</span></span> <span data-ttu-id="422d3-186">Als er een uitzonde ring wordt gegenereerd, mislukt de validatie en wordt de fout gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="422d3-186">If an exception is thrown, validation fails and the error is reported.</span></span>

<span data-ttu-id="422d3-187">Voordat u een uitzonde ring uitvoerde, kan de validatie-handler de cursor op het punt van de fout plaatsen, zodat deze eenvoudiger te verhelpen is.</span><span class="sxs-lookup"><span data-stu-id="422d3-187">Before throwing an exception, the validation handler can place the cursor at the point of the error to make it easier to fix.</span></span> <span data-ttu-id="422d3-188">Een validatie-handler kan ook de opdracht regel wijzigen, zoals om veelvoorkomende typografische fouten te corrigeren.</span><span class="sxs-lookup"><span data-stu-id="422d3-188">A validation handler can also change the command line, such as to correct common typographical errors.</span></span>

<span data-ttu-id="422d3-189">**ValidateAndAcceptLine** wordt gebruikt om te voor komen dat uw geschiedenis wordt opgeruimd met opdrachten die niet werken.</span><span class="sxs-lookup"><span data-stu-id="422d3-189">**ValidateAndAcceptLine** is used to avoid cluttering your history with commands that can't work.</span></span>

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-190">-CompletionQueryItems</span><span class="sxs-lookup"><span data-stu-id="422d3-190">-CompletionQueryItems</span></span>

<span data-ttu-id="422d3-191">Hiermee geeft u het maximum aantal voltooiings items op dat wordt weer gegeven zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="422d3-191">Specifies the maximum number of completion items that are shown without prompting.</span></span>

<span data-ttu-id="422d3-192">Als het aantal items dat moet worden weer gegeven groter is dan deze waarde, vraagt **PSReadLine** **Ja/Nee** voordat de voltooiings items worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="422d3-192">If the number of items to show is greater than this value, **PSReadLine** prompts **yes/no** before displaying the completion items.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-193">-ContinuationPrompt</span><span class="sxs-lookup"><span data-stu-id="422d3-193">-ContinuationPrompt</span></span>

<span data-ttu-id="422d3-194">Geeft de teken reeks aan die wordt weer gegeven aan het begin van de volgende regels wanneer de invoer van meerdere regels wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="422d3-194">Specifies the string displayed at the beginning of the subsequent lines when multi-line input is entered.</span></span> <span data-ttu-id="422d3-195">De standaard waarde is Double groter dan tekens ( `>>` ).</span><span class="sxs-lookup"><span data-stu-id="422d3-195">The default is double greater-than signs (`>>`).</span></span> <span data-ttu-id="422d3-196">Een lege teken reeks is geldig.</span><span class="sxs-lookup"><span data-stu-id="422d3-196">An empty string is valid.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-197">-DingDuration</span><span class="sxs-lookup"><span data-stu-id="422d3-197">-DingDuration</span></span>

<span data-ttu-id="422d3-198">Hiermee geeft u de duur van de piep Toon op wanneer **BellStyle** is ingesteld op **hoorbaar**.</span><span class="sxs-lookup"><span data-stu-id="422d3-198">Specifies the duration of the beep when **BellStyle** is set to **Audible**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-199">-DingTone</span><span class="sxs-lookup"><span data-stu-id="422d3-199">-DingTone</span></span>

<span data-ttu-id="422d3-200">Geeft de Toon in Hertz (Hz) van de piep Toon wanneer **BellStyle** is ingesteld op **hoorbaar**.</span><span class="sxs-lookup"><span data-stu-id="422d3-200">Specifies the tone in Hertz (Hz) of the beep when **BellStyle** is set to **Audible**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-201">-EditMode</span><span class="sxs-lookup"><span data-stu-id="422d3-201">-EditMode</span></span>

<span data-ttu-id="422d3-202">Hiermee geeft u de bewerkings modus van de opdracht regel op.</span><span class="sxs-lookup"><span data-stu-id="422d3-202">Specifies the command line editing mode.</span></span> <span data-ttu-id="422d3-203">Als u deze para meter gebruikt, worden de sleutel bindingen die zijn ingesteld door hersteld `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="422d3-203">Using this parameter resets any key bindings set by `Set-PSReadLineKeyHandler`.</span></span>

<span data-ttu-id="422d3-204">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="422d3-204">The valid values are as follows:</span></span>

- <span data-ttu-id="422d3-205">**Windows** : sleutel bindingen emuleren Power shell, cmd en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="422d3-205">**Windows** : Key bindings emulate PowerShell, cmd, and Visual Studio.</span></span>
- <span data-ttu-id="422d3-206">**Emacs** : sleutel bindingen bash of emacs emuleren.</span><span class="sxs-lookup"><span data-stu-id="422d3-206">**Emacs** : Key bindings emulate Bash or Emacs.</span></span>
- <span data-ttu-id="422d3-207">**VI** : sleutel bindingen emuleren VI.</span><span class="sxs-lookup"><span data-stu-id="422d3-207">**Vi** : Key bindings emulate Vi.</span></span>

<span data-ttu-id="422d3-208">Gebruik `Get-PSReadLineKeyHandler` om de sleutel bindingen voor de momenteel geconfigureerde **EditMode** weer te geven.</span><span class="sxs-lookup"><span data-stu-id="422d3-208">Use `Get-PSReadLineKeyHandler` to see the key bindings for the currently configured **EditMode**.</span></span>

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-209">-ExtraPromptLineCount</span><span class="sxs-lookup"><span data-stu-id="422d3-209">-ExtraPromptLineCount</span></span>

<span data-ttu-id="422d3-210">Hiermee geeft u het aantal extra regels op.</span><span class="sxs-lookup"><span data-stu-id="422d3-210">Specifies the number of extra lines.</span></span>

<span data-ttu-id="422d3-211">Als uw prompt meer dan één regel omvat, geeft u een waarde op voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="422d3-211">If your prompt spans more than one line, specify a value for this parameter.</span></span> <span data-ttu-id="422d3-212">Gebruik deze optie als u wilt dat extra lijnen beschikbaar zijn wanneer **PSReadLine** de vraag geeft nadat een bepaalde uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="422d3-212">Use this option when you want extra lines to be available when **PSReadLine** displays the prompt after showing some output.</span></span> <span data-ttu-id="422d3-213">**PSReadLine** retourneert bijvoorbeeld een lijst met voltooiingen.</span><span class="sxs-lookup"><span data-stu-id="422d3-213">For example, **PSReadLine** returns a list of completions.</span></span>

<span data-ttu-id="422d3-214">Deze optie is minder nodig dan in eerdere versies van **PSReadLine** , maar is handig wanneer de `InvokePrompt` functie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="422d3-214">This option is needed less than in previous versions of **PSReadLine** , but is useful when the `InvokePrompt` function is used.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-215">-HistoryNoDuplicates</span><span class="sxs-lookup"><span data-stu-id="422d3-215">-HistoryNoDuplicates</span></span>

<span data-ttu-id="422d3-216">Met deze optie bepaalt u het intrekkings gedrag.</span><span class="sxs-lookup"><span data-stu-id="422d3-216">This option controls the recall behavior.</span></span> <span data-ttu-id="422d3-217">Er worden nog dubbele opdrachten toegevoegd aan het geschiedenis bestand.</span><span class="sxs-lookup"><span data-stu-id="422d3-217">Duplicate commands are still added to the history file.</span></span>
<span data-ttu-id="422d3-218">Als deze optie is ingesteld, wordt alleen de meest recente aanroep weer gegeven wanneer opdrachten worden ingetrokken.</span><span class="sxs-lookup"><span data-stu-id="422d3-218">When this option is set, only the most recent invocation appears when recalling commands.</span></span> <span data-ttu-id="422d3-219">Herhaalde opdrachten worden toegevoegd aan de geschiedenis om de volg orde te behouden tijdens het intrekken.</span><span class="sxs-lookup"><span data-stu-id="422d3-219">Repeated commands are added to history to preserve ordering during recall.</span></span> <span data-ttu-id="422d3-220">Normaal gesp roken wilt u de opdracht echter niet meerdere keren zien wanneer u de geschiedenis aanroept of doorzoekt.</span><span class="sxs-lookup"><span data-stu-id="422d3-220">However, you typically don't want to see the command multiple times when recalling or searching the history.</span></span>

<span data-ttu-id="422d3-221">De eigenschap **HistoryNoDuplicates** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `True` .</span><span class="sxs-lookup"><span data-stu-id="422d3-221">By default, the **HistoryNoDuplicates** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="422d3-222">Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` .</span><span class="sxs-lookup"><span data-stu-id="422d3-222">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="422d3-223">Als u de waarde van de eigenschap wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-HistoryNoDuplicates:$False` .</span><span class="sxs-lookup"><span data-stu-id="422d3-223">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-HistoryNoDuplicates:$False`.</span></span>

<span data-ttu-id="422d3-224">Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:</span><span class="sxs-lookup"><span data-stu-id="422d3-224">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-225">-HistorySavePath</span><span class="sxs-lookup"><span data-stu-id="422d3-225">-HistorySavePath</span></span>

<span data-ttu-id="422d3-226">Hiermee geeft u het pad op naar het bestand waarin de geschiedenis wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="422d3-226">Specifies the path to the file where history is saved.</span></span> <span data-ttu-id="422d3-227">Op computers met Windows-of niet-Windows-platforms wordt het bestand op verschillende locaties opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="422d3-227">Computers running Windows or non-Windows platforms store the file in different locations.</span></span> <span data-ttu-id="422d3-228">De bestands naam wordt bijvoorbeeld opgeslagen in een variabele `$($host.Name)_history.txt` `ConsoleHost_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="422d3-228">The filename is stored in a variable `$($host.Name)_history.txt`, for example `ConsoleHost_history.txt`.</span></span>

<span data-ttu-id="422d3-229">Als u deze para meter niet gebruikt, is het standaardpad als volgt:</span><span class="sxs-lookup"><span data-stu-id="422d3-229">If you don't use this parameter, the default path is as follows:</span></span>

<span data-ttu-id="422d3-230">**Windows**</span><span class="sxs-lookup"><span data-stu-id="422d3-230">**Windows**</span></span>

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

<span data-ttu-id="422d3-231">**niet-Windows**</span><span class="sxs-lookup"><span data-stu-id="422d3-231">**non-Windows**</span></span>

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-232">-HistorySaveStyle</span><span class="sxs-lookup"><span data-stu-id="422d3-232">-HistorySaveStyle</span></span>

<span data-ttu-id="422d3-233">Hiermee geeft u op hoe **PSReadLine** de geschiedenis opslaat.</span><span class="sxs-lookup"><span data-stu-id="422d3-233">Specifies how **PSReadLine** saves history.</span></span>

<span data-ttu-id="422d3-234">Geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="422d3-234">Valid values are as follows:</span></span>

- <span data-ttu-id="422d3-235">**SaveIncrementally** : Sla de geschiedenis op nadat elke opdracht is uitgevoerd en delen over meerdere instanties van Power shell.</span><span class="sxs-lookup"><span data-stu-id="422d3-235">**SaveIncrementally** : Save history after each command is executed and share across multiple instances of PowerShell.</span></span>
- <span data-ttu-id="422d3-236">**SaveAtExit** : het geschiedenis bestand toevoegen wanneer Power shell wordt afgesloten.</span><span class="sxs-lookup"><span data-stu-id="422d3-236">**SaveAtExit** : Append history file when PowerShell exits.</span></span>
- <span data-ttu-id="422d3-237">**SaveNothing** : gebruik geen geschiedenis bestand.</span><span class="sxs-lookup"><span data-stu-id="422d3-237">**SaveNothing** : Don't use a history file.</span></span>

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-238">-HistorySearchCaseSensitive</span><span class="sxs-lookup"><span data-stu-id="422d3-238">-HistorySearchCaseSensitive</span></span>

<span data-ttu-id="422d3-239">Hiermee geeft u op dat zoeken in de geschiedenis hoofdletter gevoelig is in functions zoals **ReverseSearchHistory** of **HistorySearchBackward**.</span><span class="sxs-lookup"><span data-stu-id="422d3-239">Specifies that history searching is case-sensitive in functions like **ReverseSearchHistory** or **HistorySearchBackward**.</span></span>

<span data-ttu-id="422d3-240">De eigenschap **HistorySearchCaseSensitive** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `False` .</span><span class="sxs-lookup"><span data-stu-id="422d3-240">By default, the **HistorySearchCaseSensitive** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="422d3-241">Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` .</span><span class="sxs-lookup"><span data-stu-id="422d3-241">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="422d3-242">Als u de waarde van de eigenschap terug wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-HistorySearchCaseSensitive:$False` .</span><span class="sxs-lookup"><span data-stu-id="422d3-242">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCaseSensitive:$False`.</span></span>

<span data-ttu-id="422d3-243">Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:</span><span class="sxs-lookup"><span data-stu-id="422d3-243">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-244">-HistorySearchCursorMovesToEnd</span><span class="sxs-lookup"><span data-stu-id="422d3-244">-HistorySearchCursorMovesToEnd</span></span>

<span data-ttu-id="422d3-245">Hiermee wordt aangegeven dat de cursor wordt verplaatst naar het einde van opdrachten die u uit de geschiedenis laadt met behulp van een zoek opdracht.</span><span class="sxs-lookup"><span data-stu-id="422d3-245">Indicates that the cursor moves to the end of commands that you load from history by using a search.</span></span>
<span data-ttu-id="422d3-246">Als deze para meter is ingesteld op `$False` , blijft de cursor op de positie waar deze zich bevond toen u op de pijl omhoog of omlaag was geklikt.</span><span class="sxs-lookup"><span data-stu-id="422d3-246">When this parameter is set to `$False`, the cursor remains at the position it was when you pressed the up or down arrows.</span></span>

<span data-ttu-id="422d3-247">De eigenschap **HistorySearchCursorMovesToEnd** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `False` .</span><span class="sxs-lookup"><span data-stu-id="422d3-247">By default, the **HistorySearchCursorMovesToEnd** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="422d3-248">Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` .</span><span class="sxs-lookup"><span data-stu-id="422d3-248">Using this **SwitchParameter** set the property value to `True`.</span></span> <span data-ttu-id="422d3-249">Als u de waarde van de eigenschap terug wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-HistorySearchCursorMovesToEnd:$False` .</span><span class="sxs-lookup"><span data-stu-id="422d3-249">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCursorMovesToEnd:$False`.</span></span>

<span data-ttu-id="422d3-250">Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:</span><span class="sxs-lookup"><span data-stu-id="422d3-250">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-251">-MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="422d3-251">-MaximumHistoryCount</span></span>

<span data-ttu-id="422d3-252">Hiermee geeft u het maximum aantal opdrachten op dat moet worden opgeslagen in de **PSReadLine** geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="422d3-252">Specifies the maximum number of commands to save in **PSReadLine** history.</span></span>

<span data-ttu-id="422d3-253">De geschiedenis van de **PSReadLine** is gescheiden van de Power shell-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="422d3-253">**PSReadLine** history is separate from PowerShell history.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-254">-MaximumKillRingCount</span><span class="sxs-lookup"><span data-stu-id="422d3-254">-MaximumKillRingCount</span></span>

<span data-ttu-id="422d3-255">Hiermee geeft u het maximum aantal items op dat is opgeslagen in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="422d3-255">Specifies the maximum number of items stored in the kill ring.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-256">-PromptText</span><span class="sxs-lookup"><span data-stu-id="422d3-256">-PromptText</span></span>

<span data-ttu-id="422d3-257">Wanneer er een parseringsfout optreedt, wordt in **PSReadLine** een deel van de prompt rood gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="422d3-257">When there's a parse error, **PSReadLine** changes a part of the prompt red.</span></span> <span data-ttu-id="422d3-258">**PSReadLine** analyseert uw prompt functie om te bepalen hoe u alleen de kleur van een deel van uw prompt kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="422d3-258">**PSReadLine** analyzes your prompt function to determine how to change only the color of part of your prompt.</span></span> <span data-ttu-id="422d3-259">Deze analyse is niet 100% betrouwbaar.</span><span class="sxs-lookup"><span data-stu-id="422d3-259">This analysis isn't 100% reliable.</span></span>

<span data-ttu-id="422d3-260">Gebruik deze optie als **PSReadLine** uw prompt op onverwachte manieren wijzigt.</span><span class="sxs-lookup"><span data-stu-id="422d3-260">Use this option if **PSReadLine** is changing your prompt in unexpected ways.</span></span> <span data-ttu-id="422d3-261">Geef een wille keurige spatie op.</span><span class="sxs-lookup"><span data-stu-id="422d3-261">Include any trailing whitespace.</span></span>

<span data-ttu-id="422d3-262">Bijvoorbeeld, als uw prompt functie lijkt op het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="422d3-262">For example, if your prompt function looked like the following example:</span></span>

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

<span data-ttu-id="422d3-263">Vervolgens ingesteld:</span><span class="sxs-lookup"><span data-stu-id="422d3-263">Then set:</span></span>

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-264">-ShowToolTips</span><span class="sxs-lookup"><span data-stu-id="422d3-264">-ShowToolTips</span></span>

<span data-ttu-id="422d3-265">Wanneer mogelijke voltooiingen worden weer gegeven, worden knop Info weer gegeven in de lijst met voltooiingen.</span><span class="sxs-lookup"><span data-stu-id="422d3-265">When displaying possible completions, tooltips are shown in the list of completions.</span></span>

<span data-ttu-id="422d3-266">Deze optie is standaard ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="422d3-266">This option is enabled by default.</span></span> <span data-ttu-id="422d3-267">Deze optie is niet standaard ingeschakeld in eerdere versies van **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="422d3-267">This option wasn't enabled by default in prior versions of **PSReadLine**.</span></span> <span data-ttu-id="422d3-268">Als u wilt uitschakelen, stelt u deze optie in op `$False` .</span><span class="sxs-lookup"><span data-stu-id="422d3-268">To disable, set this option to `$False`.</span></span>

<span data-ttu-id="422d3-269">De eigenschap **ShowToolTips** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `True` .</span><span class="sxs-lookup"><span data-stu-id="422d3-269">By default, the **ShowToolTips** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="422d3-270">Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` .</span><span class="sxs-lookup"><span data-stu-id="422d3-270">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="422d3-271">Als u de waarde van de eigenschap wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-ShowToolTips:$False` .</span><span class="sxs-lookup"><span data-stu-id="422d3-271">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-ShowToolTips:$False`.</span></span>

<span data-ttu-id="422d3-272">Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:</span><span class="sxs-lookup"><span data-stu-id="422d3-272">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).ShowToolTips = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-273">-ViModeChangeHandler</span><span class="sxs-lookup"><span data-stu-id="422d3-273">-ViModeChangeHandler</span></span>

<span data-ttu-id="422d3-274">Wanneer de **ViModeIndicator** is ingesteld op `Script` , wordt het opgegeven script blok elke keer dat de modus verandert, aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="422d3-274">When the **ViModeIndicator** is set to `Script`, the script block provided will be invoked every time the mode changes.</span></span> <span data-ttu-id="422d3-275">Het script blok biedt één argument van het type `ViMode` .</span><span class="sxs-lookup"><span data-stu-id="422d3-275">The script block is provided one argument of type `ViMode`.</span></span>

<span data-ttu-id="422d3-276">Deze para meter is geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="422d3-276">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-277">-ViModeIndicator</span><span class="sxs-lookup"><span data-stu-id="422d3-277">-ViModeIndicator</span></span>

<span data-ttu-id="422d3-278">Met deze optie stelt u de visuele indicatie in voor de huidige **VI** -modus.</span><span class="sxs-lookup"><span data-stu-id="422d3-278">This option sets the visual indication for the current **Vi** mode.</span></span> <span data-ttu-id="422d3-279">De Invoeg modus of de opdracht modus.</span><span class="sxs-lookup"><span data-stu-id="422d3-279">Either insert mode or command mode.</span></span>

<span data-ttu-id="422d3-280">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="422d3-280">The valid values are as follows:</span></span>

- <span data-ttu-id="422d3-281">**Geen** : er is geen indicatie.</span><span class="sxs-lookup"><span data-stu-id="422d3-281">**None** : There's no indication.</span></span>
- <span data-ttu-id="422d3-282">**Prompt** : de prompt verandert in kleur.</span><span class="sxs-lookup"><span data-stu-id="422d3-282">**Prompt** : The prompt changes color.</span></span>
- <span data-ttu-id="422d3-283">**Cursor** : de grootte van de cursor verandert.</span><span class="sxs-lookup"><span data-stu-id="422d3-283">**Cursor** : The cursor changes size.</span></span>
- <span data-ttu-id="422d3-284">**Script** : door de gebruiker opgegeven tekst wordt afgedrukt.</span><span class="sxs-lookup"><span data-stu-id="422d3-284">**Script** : User-specified text is printed.</span></span>

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-285">-WordDelimiters</span><span class="sxs-lookup"><span data-stu-id="422d3-285">-WordDelimiters</span></span>

<span data-ttu-id="422d3-286">Hiermee geeft u de tekens op waarmee woorden worden beperkt voor functies zoals **ForwardWord** of **KillWord**.</span><span class="sxs-lookup"><span data-stu-id="422d3-286">Specifies the characters that delimit words for functions like **ForwardWord** or **KillWord**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"–—―
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="422d3-287">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="422d3-287">CommonParameters</span></span>

<span data-ttu-id="422d3-288">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="422d3-288">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="422d3-289">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="422d3-289">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="422d3-290">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="422d3-290">Inputs</span></span>

### <span data-ttu-id="422d3-291">Geen</span><span class="sxs-lookup"><span data-stu-id="422d3-291">None</span></span>

<span data-ttu-id="422d3-292">U kunt objecten niet naar `Set-PSReadLineOption.`</span><span class="sxs-lookup"><span data-stu-id="422d3-292">You cannot pipe objects to `Set-PSReadLineOption.`</span></span>

## <span data-ttu-id="422d3-293">Uitvoer</span><span class="sxs-lookup"><span data-stu-id="422d3-293">Outputs</span></span>

### <span data-ttu-id="422d3-294">Geen</span><span class="sxs-lookup"><span data-stu-id="422d3-294">None</span></span>

<span data-ttu-id="422d3-295">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="422d3-295">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="422d3-296">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="422d3-296">Notes</span></span>

## <span data-ttu-id="422d3-297">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="422d3-297">Related links</span></span>

[<span data-ttu-id="422d3-298">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="422d3-298">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

[<span data-ttu-id="422d3-299">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="422d3-299">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="422d3-300">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="422d3-300">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="422d3-301">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="422d3-301">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="422d3-302">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="422d3-302">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
