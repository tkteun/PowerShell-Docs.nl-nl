---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: cac2c2bb8ce1f3a28c0d91c7503b3ac4d038ccad
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514946"
---
# <span data-ttu-id="2a225-102">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="2a225-102">Set-PSReadLineOption</span></span>

## <span data-ttu-id="2a225-103">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="2a225-103">Synopsis</span></span>
<span data-ttu-id="2a225-104">Het gedrag van het bewerken van opdracht regels in **PSReadLine** aanpassen.</span><span class="sxs-lookup"><span data-stu-id="2a225-104">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

## <span data-ttu-id="2a225-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a225-105">Syntax</span></span>

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func`2[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action`1[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-PredictionSource <PredictionSource>]
 [-PredictionViewStyle <PredictionViewStyle>] [-Colors <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="2a225-106">Description</span><span class="sxs-lookup"><span data-stu-id="2a225-106">Description</span></span>

<span data-ttu-id="2a225-107">`Set-PSReadLineOption`Met de cmdlet wordt het gedrag van de **PSReadLine** -module aangepast wanneer u de opdracht regel bewerkt.</span><span class="sxs-lookup"><span data-stu-id="2a225-107">The `Set-PSReadLineOption` cmdlet customizes the behavior of the **PSReadLine** module when you're editing the command line.</span></span> <span data-ttu-id="2a225-108">Als u de **PSReadLine** -instellingen wilt weer geven, gebruikt u `Get-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="2a225-108">To view the **PSReadLine** settings, use `Get-PSReadLineOption`.</span></span>

## <span data-ttu-id="2a225-109">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="2a225-109">Examples</span></span>

### <span data-ttu-id="2a225-110">Voor beeld 1: voorgrond-en achtergrond kleuren instellen</span><span class="sxs-lookup"><span data-stu-id="2a225-110">Example 1: Set foreground and background colors</span></span>

<span data-ttu-id="2a225-111">In dit voor beeld wordt **PSReadLine** ingesteld om het **opmerkings** token met groene voorgrond tekst op een grijze achtergrond weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2a225-111">This example sets **PSReadLine** to display the **Comment** token with green foreground text on a gray background.</span></span> <span data-ttu-id="2a225-112">In de escape-reeks die in het voor beeld wordt gebruikt, vertegenwoordigt **32** de voorgrond kleur en **47** de achtergrond kleur.</span><span class="sxs-lookup"><span data-stu-id="2a225-112">In the escape sequence used in the example, **32** represents the foreground color and **47** represents the background color.</span></span>

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

<span data-ttu-id="2a225-113">U kunt ervoor kiezen om alleen een voorgrond tekst kleur in te stellen.</span><span class="sxs-lookup"><span data-stu-id="2a225-113">You can choose to set only a foreground text color.</span></span> <span data-ttu-id="2a225-114">Bijvoorbeeld een heldere, groene voorgrond tekst kleur voor het **opmerkings** token: ``"Comment"="`e[92m"`` .</span><span class="sxs-lookup"><span data-stu-id="2a225-114">For example, a bright green foreground text color for the **Comment** token: ``"Comment"="`e[92m"``.</span></span>

### <span data-ttu-id="2a225-115">Voor beeld 2: de stijl van de Bel instellen</span><span class="sxs-lookup"><span data-stu-id="2a225-115">Example 2: Set bell style</span></span>

<span data-ttu-id="2a225-116">In dit voor beeld reageert **PSReadLine** op fouten of voor waarden waarvoor aandacht van de gebruiker is vereist.</span><span class="sxs-lookup"><span data-stu-id="2a225-116">In this example, **PSReadLine** will respond to errors or conditions that require user attention.</span></span>
<span data-ttu-id="2a225-117">De **BellStyle** is ingesteld voor het verzenden van een hoorbaar pieptoon bij 1221 Hz voor 60 MS.</span><span class="sxs-lookup"><span data-stu-id="2a225-117">The **BellStyle** is set to emit an audible beep at 1221 Hz for 60 ms.</span></span>

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> <span data-ttu-id="2a225-118">Deze functie werkt mogelijk niet op alle hosts op platforms.</span><span class="sxs-lookup"><span data-stu-id="2a225-118">This feature may not work in all hosts on platforms.</span></span>

### <span data-ttu-id="2a225-119">Voor beeld 3: meerdere opties instellen</span><span class="sxs-lookup"><span data-stu-id="2a225-119">Example 3: Set multiple options</span></span>

<span data-ttu-id="2a225-120">`Set-PSReadLineOption` kan meerdere opties instellen met een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="2a225-120">`Set-PSReadLineOption` can set multiple options with a hash table.</span></span>

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

<span data-ttu-id="2a225-121">In de `$PSReadLineOptions` tabel hash worden de sleutels en waarden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="2a225-121">The `$PSReadLineOptions` hash table sets the keys and values.</span></span> <span data-ttu-id="2a225-122">`Set-PSReadLineOption` gebruikt de sleutels en waarden met `@PSReadLineOptions` om de **PSReadLine** -opties bij te werken.</span><span class="sxs-lookup"><span data-stu-id="2a225-122">`Set-PSReadLineOption` uses the keys and values with `@PSReadLineOptions` to update the **PSReadLine** options.</span></span>

<span data-ttu-id="2a225-123">U kunt de sleutels en waarden voor het invoeren van de naam van de hash-tabel weer geven `$PSReadLineOptions` op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="2a225-123">You can view the keys and values entering the hash table name, `$PSReadLineOptions` on the PowerShell command line.</span></span>

### <span data-ttu-id="2a225-124">Voor beeld 4: meerdere kleur opties instellen</span><span class="sxs-lookup"><span data-stu-id="2a225-124">Example 4: Set multiple color options</span></span>

<span data-ttu-id="2a225-125">In dit voor beeld ziet u hoe u in één opdracht meer dan één kleur waarde kunt instellen.</span><span class="sxs-lookup"><span data-stu-id="2a225-125">This example shows how to set more than one color value in a single command.</span></span>

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

### <span data-ttu-id="2a225-126">Voor beeld 5: kleur waarden instellen voor meerdere typen</span><span class="sxs-lookup"><span data-stu-id="2a225-126">Example 5: Set color values for multiple types</span></span>

<span data-ttu-id="2a225-127">Dit voor beeld toont drie verschillende methoden voor het instellen van de kleur van tokens die worden weer gegeven in **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="2a225-127">This example shows three different methods for how to set the color of tokens displayed in **PSReadLine**.</span></span>

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

### <span data-ttu-id="2a225-128">Voor beeld 6: ViModeChangeHandler gebruiken om wijzigingen in de modus in de VI weer te geven</span><span class="sxs-lookup"><span data-stu-id="2a225-128">Example 6: Use ViModeChangeHandler to display Vi mode changes</span></span>

<span data-ttu-id="2a225-129">In dit voor beeld wordt een cursor wijziging een VT-Escape verzonden in reactie op een wijziging in de **VI** -modus.</span><span class="sxs-lookup"><span data-stu-id="2a225-129">This example emits a cursor change VT escape in response to a **Vi** mode change.</span></span>

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

<span data-ttu-id="2a225-130">De functie **OnViModeChange** stelt de cursor opties in voor de **VI** -modi: insert en Command.</span><span class="sxs-lookup"><span data-stu-id="2a225-130">The **OnViModeChange** function sets the cursor options for the **Vi** modes: insert and command.</span></span>
<span data-ttu-id="2a225-131">**ViModeChangeHandler** maakt gebruik van de `Function:` provider om te verwijzen naar **OnViModeChange** als een script blok-object.</span><span class="sxs-lookup"><span data-stu-id="2a225-131">**ViModeChangeHandler** uses the `Function:` provider to reference **OnViModeChange** as a script block object.</span></span>

<span data-ttu-id="2a225-132">Zie [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2a225-132">For more information, see [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span></span>

## <span data-ttu-id="2a225-133">Parameters</span><span class="sxs-lookup"><span data-stu-id="2a225-133">Parameters</span></span>

### <span data-ttu-id="2a225-134">-AddToHistoryHandler</span><span class="sxs-lookup"><span data-stu-id="2a225-134">-AddToHistoryHandler</span></span>

<span data-ttu-id="2a225-135">Hiermee geeft u een **script Block** op die bepaalt welke opdrachten aan de **PSReadLine** -geschiedenis worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="2a225-135">Specifies a **ScriptBlock** that controls which commands get added to **PSReadLine** history.</span></span>

<span data-ttu-id="2a225-136">De **script Block** ontvangt de opdracht regel als invoer.</span><span class="sxs-lookup"><span data-stu-id="2a225-136">The **ScriptBlock** receives the command line as input.</span></span> <span data-ttu-id="2a225-137">Als de **script Block** wordt geretourneerd `$True` , wordt de opdracht regel aan de geschiedenis toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="2a225-137">If the **ScriptBlock** returns `$True`, the command line is added to the history.</span></span>

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

### <span data-ttu-id="2a225-138">-AnsiEscapeTimeout</span><span class="sxs-lookup"><span data-stu-id="2a225-138">-AnsiEscapeTimeout</span></span>

<span data-ttu-id="2a225-139">Deze optie is specifiek voor Windows wanneer invoer wordt omgeleid, bijvoorbeeld wanneer deze wordt uitgevoerd onder `tmux` of `screen` .</span><span class="sxs-lookup"><span data-stu-id="2a225-139">This option is specific to Windows when input is redirected, for example, when running under `tmux` or `screen`.</span></span>

<span data-ttu-id="2a225-140">Met omgeleide invoer in Windows worden veel sleutels verzonden als een reeks tekens die beginnen met het escape-teken.</span><span class="sxs-lookup"><span data-stu-id="2a225-140">With redirected input on Windows, many keys are sent as a sequence of characters starting with the escape character.</span></span> <span data-ttu-id="2a225-141">Het is niet mogelijk om onderscheid te maken tussen één escape teken, gevolgd door meer tekens en een geldige escape reeks.</span><span class="sxs-lookup"><span data-stu-id="2a225-141">It's impossible to distinguish between a single escape character followed by more characters and a valid escape sequence.</span></span>

<span data-ttu-id="2a225-142">De veronderstelling is dat de Terminal de tekens sneller kan verzenden dan een gebruiker typt.</span><span class="sxs-lookup"><span data-stu-id="2a225-142">The assumption is that the terminal can send the characters faster than a user types.</span></span> <span data-ttu-id="2a225-143">**PSReadLine** wacht op deze time-out voordat wordt geconcludeerd dat er een volledige escape reeks is ontvangen.</span><span class="sxs-lookup"><span data-stu-id="2a225-143">**PSReadLine** waits for this timeout before concluding that it has received a complete escape sequence.</span></span>

<span data-ttu-id="2a225-144">Als u wille keurige of onverwachte tekens ziet wanneer u typt, kunt u deze time-out aanpassen.</span><span class="sxs-lookup"><span data-stu-id="2a225-144">If you see random or unexpected characters when you type, you can adjust this timeout.</span></span>

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

### <span data-ttu-id="2a225-145">-BellStyle</span><span class="sxs-lookup"><span data-stu-id="2a225-145">-BellStyle</span></span>

<span data-ttu-id="2a225-146">Hiermee geeft u op hoe **PSReadLine** reageert op verschillende fout-en ambigue voor waarden.</span><span class="sxs-lookup"><span data-stu-id="2a225-146">Specifies how **PSReadLine** responds to various error and ambiguous conditions.</span></span>

<span data-ttu-id="2a225-147">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="2a225-147">The valid values are as follows:</span></span>

- <span data-ttu-id="2a225-148">**Hoorbaar**: een korte piep Toon.</span><span class="sxs-lookup"><span data-stu-id="2a225-148">**Audible**: A short beep.</span></span>
- <span data-ttu-id="2a225-149">**Visueel**: tekst knippert even.</span><span class="sxs-lookup"><span data-stu-id="2a225-149">**Visual**: Text flashes briefly.</span></span>
- <span data-ttu-id="2a225-150">**Geen: geen** feedback.</span><span class="sxs-lookup"><span data-stu-id="2a225-150">**None**: No feedback.</span></span>

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

### <span data-ttu-id="2a225-151">-Kleuren</span><span class="sxs-lookup"><span data-stu-id="2a225-151">-Colors</span></span>

<span data-ttu-id="2a225-152">De para meter **kleuren** bevat verschillende kleuren die worden gebruikt door **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="2a225-152">The **Colors** parameter specifies various colors used by **PSReadLine**.</span></span>

<span data-ttu-id="2a225-153">Het argument is een hash-tabel waarin de sleutels opgeven welk element en welke waarden de kleur opgeven.</span><span class="sxs-lookup"><span data-stu-id="2a225-153">The argument is a hash table where the keys specify which element and the values specify the color.</span></span>
<span data-ttu-id="2a225-154">Zie [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2a225-154">For more information, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="2a225-155">Kleuren kunnen bestaan uit een waarde van **ConsoleColor**, bijvoorbeeld `[ConsoleColor]::Red` of een geldige ANSI-escape reeks.</span><span class="sxs-lookup"><span data-stu-id="2a225-155">Colors can be either a value from **ConsoleColor**, for example `[ConsoleColor]::Red`, or a valid ANSI escape sequence.</span></span> <span data-ttu-id="2a225-156">Geldige escape reeksen zijn afhankelijk van uw Terminal.</span><span class="sxs-lookup"><span data-stu-id="2a225-156">Valid escape sequences depend on your terminal.</span></span> <span data-ttu-id="2a225-157">In Power shell 5,0 is een voor beeld van een escape reeks voor rode tekst `$([char]0x1b)[91m` .</span><span class="sxs-lookup"><span data-stu-id="2a225-157">In PowerShell 5.0, an example escape sequence for red text is `$([char]0x1b)[91m`.</span></span> <span data-ttu-id="2a225-158">In Power shell 6 en hoger is dezelfde escape reeks `` `e[91m`` .</span><span class="sxs-lookup"><span data-stu-id="2a225-158">In PowerShell 6 and above, the same escape sequence is `` `e[91m``.</span></span> <span data-ttu-id="2a225-159">U kunt andere escape reeksen opgeven, met inbegrip van de volgende typen:</span><span class="sxs-lookup"><span data-stu-id="2a225-159">You can specify other escape sequences including the following types:</span></span>

<span data-ttu-id="2a225-160">Er zijn twee kleur instellingen toegevoegd ter ondersteuning van aanpassing van de `ListView` in PSReadLine 2.2.0:</span><span class="sxs-lookup"><span data-stu-id="2a225-160">Two color settings were added to support customization of the `ListView` in PSReadLine 2.2.0:</span></span>

- <span data-ttu-id="2a225-161">**ListPredictionColor** : Stel de kleur voor het voorloop `>` teken en de Volg naam van de bron in, bijvoorbeeld `[History]` .</span><span class="sxs-lookup"><span data-stu-id="2a225-161">**ListPredictionColor** - set color for the leading `>` character and the trailing source name, e.g. `[History]`.</span></span> <span data-ttu-id="2a225-162">De standaard instelling wordt gebruikt `DarkYellow` als de voorgrond kleur.</span><span class="sxs-lookup"><span data-stu-id="2a225-162">By default, it uses `DarkYellow` as the foreground color.</span></span>
- <span data-ttu-id="2a225-163">**ListPredictionSelectedColor** : Stel de kleur in om aan te geven dat een lijst item is geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="2a225-163">**ListPredictionSelectedColor** - set color for indicating a list item is selected.</span></span> <span data-ttu-id="2a225-164">De standaard instelling wordt gebruikt `DarkBlack` als de achtergrond kleur.</span><span class="sxs-lookup"><span data-stu-id="2a225-164">By default, it uses `DarkBlack` as the background color.</span></span>

- <span data-ttu-id="2a225-165">256-kleur</span><span class="sxs-lookup"><span data-stu-id="2a225-165">256 color</span></span>
- <span data-ttu-id="2a225-166">24-bits kleur</span><span class="sxs-lookup"><span data-stu-id="2a225-166">24-bit color</span></span>
- <span data-ttu-id="2a225-167">Voor grond, achtergrond of beide</span><span class="sxs-lookup"><span data-stu-id="2a225-167">Foreground, background, or both</span></span>
- <span data-ttu-id="2a225-168">Inverse, vet</span><span class="sxs-lookup"><span data-stu-id="2a225-168">Inverse, bold</span></span>

<span data-ttu-id="2a225-169">Zie [ANSI escape-code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia voor meer informatie over ANSI-kleur codes.</span><span class="sxs-lookup"><span data-stu-id="2a225-169">For more information about ANSI color codes, see [ANSI escape code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia.</span></span>

<span data-ttu-id="2a225-170">De geldige sleutels zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="2a225-170">The valid keys include:</span></span>

- <span data-ttu-id="2a225-171">**ContinuationPrompt**: de kleur van de voortzettings prompt.</span><span class="sxs-lookup"><span data-stu-id="2a225-171">**ContinuationPrompt**: The color of the continuation prompt.</span></span>
- <span data-ttu-id="2a225-172">**Nadruk**: de kleur van de nadruk.</span><span class="sxs-lookup"><span data-stu-id="2a225-172">**Emphasis**: The emphasis color.</span></span> <span data-ttu-id="2a225-173">Bijvoorbeeld, de overeenkomende tekst bij het zoeken van de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="2a225-173">For example, the matching text when searching history.</span></span>
- <span data-ttu-id="2a225-174">**Fout**: de fout kleur.</span><span class="sxs-lookup"><span data-stu-id="2a225-174">**Error**: The error color.</span></span> <span data-ttu-id="2a225-175">Bijvoorbeeld in de prompt.</span><span class="sxs-lookup"><span data-stu-id="2a225-175">For example, in the prompt.</span></span>
- <span data-ttu-id="2a225-176">**Selectie**: de kleur voor het markeren van de menu selectie of de geselecteerde tekst.</span><span class="sxs-lookup"><span data-stu-id="2a225-176">**Selection**: The color to highlight the menu selection or selected text.</span></span>
- <span data-ttu-id="2a225-177">**Standaard**: de kleur van het standaard token.</span><span class="sxs-lookup"><span data-stu-id="2a225-177">**Default**: The default token color.</span></span>
- <span data-ttu-id="2a225-178">**Opmerking**: de kleur van het opmerkings token.</span><span class="sxs-lookup"><span data-stu-id="2a225-178">**Comment**: The comment token color.</span></span>
- <span data-ttu-id="2a225-179">**Sleutel woord**: de kleur van het trefwoord token.</span><span class="sxs-lookup"><span data-stu-id="2a225-179">**Keyword**: The keyword token color.</span></span>
- <span data-ttu-id="2a225-180">**Teken reeks**: de kleur van het teken reeks token.</span><span class="sxs-lookup"><span data-stu-id="2a225-180">**String**: The string token color.</span></span>
- <span data-ttu-id="2a225-181">**Operator**: de kleur van de operator token.</span><span class="sxs-lookup"><span data-stu-id="2a225-181">**Operator**: The operator token color.</span></span>
- <span data-ttu-id="2a225-182">**Variabele**: de kleur van het variabele token.</span><span class="sxs-lookup"><span data-stu-id="2a225-182">**Variable**: The variable token color.</span></span>
- <span data-ttu-id="2a225-183">**Opdracht**: de kleur van het opdracht token.</span><span class="sxs-lookup"><span data-stu-id="2a225-183">**Command**: The command token color.</span></span>
- <span data-ttu-id="2a225-184">**Para meter**: de kleur van het parameter token.</span><span class="sxs-lookup"><span data-stu-id="2a225-184">**Parameter**: The parameter token color.</span></span>
- <span data-ttu-id="2a225-185">**Type**: het type token kleur.</span><span class="sxs-lookup"><span data-stu-id="2a225-185">**Type**: The type token color.</span></span>
- <span data-ttu-id="2a225-186">**Getal**: de kleur van het cijfer token.</span><span class="sxs-lookup"><span data-stu-id="2a225-186">**Number**: The number token color.</span></span>
- <span data-ttu-id="2a225-187">**Lid**: de kleur van het token van de leden naam.</span><span class="sxs-lookup"><span data-stu-id="2a225-187">**Member**: The member name token color.</span></span>
- <span data-ttu-id="2a225-188">**InlinePrediction**: de kleur voor de inline weer gave van de voorspellende suggestie.</span><span class="sxs-lookup"><span data-stu-id="2a225-188">**InlinePrediction**: The color for the inline view of the predictive suggestion.</span></span>

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

### <span data-ttu-id="2a225-189">-CommandValidationHandler</span><span class="sxs-lookup"><span data-stu-id="2a225-189">-CommandValidationHandler</span></span>

<span data-ttu-id="2a225-190">Hiermee geeft u een **script Block** die wordt aangeroepen vanuit **ValidateAndAcceptLine**.</span><span class="sxs-lookup"><span data-stu-id="2a225-190">Specifies a **ScriptBlock** that is called from **ValidateAndAcceptLine**.</span></span> <span data-ttu-id="2a225-191">Als er een uitzonde ring wordt gegenereerd, mislukt de validatie en wordt de fout gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="2a225-191">If an exception is thrown, validation fails and the error is reported.</span></span>

<span data-ttu-id="2a225-192">Voordat u een uitzonde ring uitvoerde, kan de validatie-handler de cursor op het punt van de fout plaatsen, zodat deze eenvoudiger te verhelpen is.</span><span class="sxs-lookup"><span data-stu-id="2a225-192">Before throwing an exception, the validation handler can place the cursor at the point of the error to make it easier to fix.</span></span> <span data-ttu-id="2a225-193">Een validatie-handler kan ook de opdracht regel wijzigen, zoals om veelvoorkomende typografische fouten te corrigeren.</span><span class="sxs-lookup"><span data-stu-id="2a225-193">A validation handler can also change the command line, such as to correct common typographical errors.</span></span>

<span data-ttu-id="2a225-194">**ValidateAndAcceptLine** wordt gebruikt om te voor komen dat uw geschiedenis wordt opgeruimd met opdrachten die niet werken.</span><span class="sxs-lookup"><span data-stu-id="2a225-194">**ValidateAndAcceptLine** is used to avoid cluttering your history with commands that can't work.</span></span>

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

### <span data-ttu-id="2a225-195">-CompletionQueryItems</span><span class="sxs-lookup"><span data-stu-id="2a225-195">-CompletionQueryItems</span></span>

<span data-ttu-id="2a225-196">Hiermee geeft u het maximum aantal voltooiings items op dat wordt weer gegeven zonder te vragen.</span><span class="sxs-lookup"><span data-stu-id="2a225-196">Specifies the maximum number of completion items that are shown without prompting.</span></span>

<span data-ttu-id="2a225-197">Als het aantal items dat moet worden weer gegeven groter is dan deze waarde, vraagt **PSReadLine** **Ja/Nee** voordat de voltooiings items worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2a225-197">If the number of items to show is greater than this value, **PSReadLine** prompts **yes/no** before displaying the completion items.</span></span>

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

### <span data-ttu-id="2a225-198">-ContinuationPrompt</span><span class="sxs-lookup"><span data-stu-id="2a225-198">-ContinuationPrompt</span></span>

<span data-ttu-id="2a225-199">Geeft de teken reeks aan die wordt weer gegeven aan het begin van de volgende regels wanneer de invoer van meerdere regels wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="2a225-199">Specifies the string displayed at the beginning of the subsequent lines when multi-line input is entered.</span></span> <span data-ttu-id="2a225-200">De standaard waarde is Double groter dan tekens ( `>>` ).</span><span class="sxs-lookup"><span data-stu-id="2a225-200">The default is double greater-than signs (`>>`).</span></span> <span data-ttu-id="2a225-201">Een lege teken reeks is geldig.</span><span class="sxs-lookup"><span data-stu-id="2a225-201">An empty string is valid.</span></span>

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

### <span data-ttu-id="2a225-202">-DingDuration</span><span class="sxs-lookup"><span data-stu-id="2a225-202">-DingDuration</span></span>

<span data-ttu-id="2a225-203">Hiermee geeft u de duur van de piep Toon op wanneer **BellStyle** is ingesteld op **hoorbaar**.</span><span class="sxs-lookup"><span data-stu-id="2a225-203">Specifies the duration of the beep when **BellStyle** is set to **Audible**.</span></span>

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

### <span data-ttu-id="2a225-204">-DingTone</span><span class="sxs-lookup"><span data-stu-id="2a225-204">-DingTone</span></span>

<span data-ttu-id="2a225-205">Geeft de Toon in Hertz (Hz) van de piep Toon wanneer **BellStyle** is ingesteld op **hoorbaar**.</span><span class="sxs-lookup"><span data-stu-id="2a225-205">Specifies the tone in Hertz (Hz) of the beep when **BellStyle** is set to **Audible**.</span></span>

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

### <span data-ttu-id="2a225-206">-EditMode</span><span class="sxs-lookup"><span data-stu-id="2a225-206">-EditMode</span></span>

<span data-ttu-id="2a225-207">Hiermee geeft u de bewerkings modus van de opdracht regel op.</span><span class="sxs-lookup"><span data-stu-id="2a225-207">Specifies the command line editing mode.</span></span> <span data-ttu-id="2a225-208">Als u deze para meter gebruikt, worden de sleutel bindingen die zijn ingesteld door hersteld `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="2a225-208">Using this parameter resets any key bindings set by `Set-PSReadLineKeyHandler`.</span></span>

<span data-ttu-id="2a225-209">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="2a225-209">The valid values are as follows:</span></span>

- <span data-ttu-id="2a225-210">**Windows**: sleutel bindingen emuleren Power shell, cmd en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a225-210">**Windows**: Key bindings emulate PowerShell, cmd, and Visual Studio.</span></span>
- <span data-ttu-id="2a225-211">**Emacs**: sleutel bindingen bash of emacs emuleren.</span><span class="sxs-lookup"><span data-stu-id="2a225-211">**Emacs**: Key bindings emulate Bash or Emacs.</span></span>
- <span data-ttu-id="2a225-212">**VI**: sleutel bindingen emuleren VI.</span><span class="sxs-lookup"><span data-stu-id="2a225-212">**Vi**: Key bindings emulate Vi.</span></span>

<span data-ttu-id="2a225-213">Gebruik `Get-PSReadLineKeyHandler` om de sleutel bindingen voor de momenteel geconfigureerde **EditMode** weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2a225-213">Use `Get-PSReadLineKeyHandler` to see the key bindings for the currently configured **EditMode**.</span></span>

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

### <span data-ttu-id="2a225-214">-ExtraPromptLineCount</span><span class="sxs-lookup"><span data-stu-id="2a225-214">-ExtraPromptLineCount</span></span>

<span data-ttu-id="2a225-215">Hiermee geeft u het aantal extra regels op.</span><span class="sxs-lookup"><span data-stu-id="2a225-215">Specifies the number of extra lines.</span></span>

<span data-ttu-id="2a225-216">Als uw prompt meer dan één regel omvat, geeft u een waarde op voor deze para meter.</span><span class="sxs-lookup"><span data-stu-id="2a225-216">If your prompt spans more than one line, specify a value for this parameter.</span></span> <span data-ttu-id="2a225-217">Gebruik deze optie als u wilt dat extra lijnen beschikbaar zijn wanneer **PSReadLine** de vraag geeft nadat een bepaalde uitvoer wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2a225-217">Use this option when you want extra lines to be available when **PSReadLine** displays the prompt after showing some output.</span></span> <span data-ttu-id="2a225-218">**PSReadLine** retourneert bijvoorbeeld een lijst met voltooiingen.</span><span class="sxs-lookup"><span data-stu-id="2a225-218">For example, **PSReadLine** returns a list of completions.</span></span>

<span data-ttu-id="2a225-219">Deze optie is minder nodig dan in eerdere versies van **PSReadLine**, maar is handig wanneer de `InvokePrompt` functie wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2a225-219">This option is needed less than in previous versions of **PSReadLine**, but is useful when the `InvokePrompt` function is used.</span></span>

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

### <span data-ttu-id="2a225-220">-HistoryNoDuplicates</span><span class="sxs-lookup"><span data-stu-id="2a225-220">-HistoryNoDuplicates</span></span>

<span data-ttu-id="2a225-221">Met deze optie bepaalt u het intrekkings gedrag.</span><span class="sxs-lookup"><span data-stu-id="2a225-221">This option controls the recall behavior.</span></span> <span data-ttu-id="2a225-222">Er worden nog dubbele opdrachten toegevoegd aan het geschiedenis bestand.</span><span class="sxs-lookup"><span data-stu-id="2a225-222">Duplicate commands are still added to the history file.</span></span>
<span data-ttu-id="2a225-223">Als deze optie is ingesteld, wordt alleen de meest recente aanroep weer gegeven wanneer opdrachten worden ingetrokken.</span><span class="sxs-lookup"><span data-stu-id="2a225-223">When this option is set, only the most recent invocation appears when recalling commands.</span></span> <span data-ttu-id="2a225-224">Herhaalde opdrachten worden toegevoegd aan de geschiedenis om de volg orde te behouden tijdens het intrekken.</span><span class="sxs-lookup"><span data-stu-id="2a225-224">Repeated commands are added to history to preserve ordering during recall.</span></span> <span data-ttu-id="2a225-225">Normaal gesp roken wilt u de opdracht echter niet meerdere keren zien wanneer u de geschiedenis aanroept of doorzoekt.</span><span class="sxs-lookup"><span data-stu-id="2a225-225">However, you typically don't want to see the command multiple times when recalling or searching the history.</span></span>

<span data-ttu-id="2a225-226">De eigenschap **HistoryNoDuplicates** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `True` .</span><span class="sxs-lookup"><span data-stu-id="2a225-226">By default, the **HistoryNoDuplicates** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="2a225-227">Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` .</span><span class="sxs-lookup"><span data-stu-id="2a225-227">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="2a225-228">Als u de waarde van de eigenschap wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-HistoryNoDuplicates:$False` .</span><span class="sxs-lookup"><span data-stu-id="2a225-228">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-HistoryNoDuplicates:$False`.</span></span>

<span data-ttu-id="2a225-229">Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:</span><span class="sxs-lookup"><span data-stu-id="2a225-229">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="2a225-230">-HistorySavePath</span><span class="sxs-lookup"><span data-stu-id="2a225-230">-HistorySavePath</span></span>

<span data-ttu-id="2a225-231">Hiermee geeft u het pad op naar het bestand waarin de geschiedenis wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="2a225-231">Specifies the path to the file where history is saved.</span></span> <span data-ttu-id="2a225-232">Op computers met Windows-of niet-Windows-platforms wordt het bestand op verschillende locaties opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="2a225-232">Computers running Windows or non-Windows platforms store the file in different locations.</span></span> <span data-ttu-id="2a225-233">De bestands naam wordt bijvoorbeeld opgeslagen in een variabele `$($host.Name)_history.txt` `ConsoleHost_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="2a225-233">The filename is stored in a variable `$($host.Name)_history.txt`, for example `ConsoleHost_history.txt`.</span></span>

<span data-ttu-id="2a225-234">Als u deze para meter niet gebruikt, is het standaardpad als volgt:</span><span class="sxs-lookup"><span data-stu-id="2a225-234">If you don't use this parameter, the default path is as follows:</span></span>

<span data-ttu-id="2a225-235">**Windows**</span><span class="sxs-lookup"><span data-stu-id="2a225-235">**Windows**</span></span>

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

<span data-ttu-id="2a225-236">**niet-Windows**</span><span class="sxs-lookup"><span data-stu-id="2a225-236">**non-Windows**</span></span>

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

### <span data-ttu-id="2a225-237">-HistorySaveStyle</span><span class="sxs-lookup"><span data-stu-id="2a225-237">-HistorySaveStyle</span></span>

<span data-ttu-id="2a225-238">Hiermee geeft u op hoe **PSReadLine** de geschiedenis opslaat.</span><span class="sxs-lookup"><span data-stu-id="2a225-238">Specifies how **PSReadLine** saves history.</span></span>

<span data-ttu-id="2a225-239">Geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="2a225-239">Valid values are as follows:</span></span>

- <span data-ttu-id="2a225-240">**SaveIncrementally**: Sla de geschiedenis op nadat elke opdracht is uitgevoerd en delen over meerdere instanties van Power shell.</span><span class="sxs-lookup"><span data-stu-id="2a225-240">**SaveIncrementally**: Save history after each command is executed and share across multiple instances of PowerShell.</span></span>
- <span data-ttu-id="2a225-241">**SaveAtExit**: het geschiedenis bestand toevoegen wanneer Power shell wordt afgesloten.</span><span class="sxs-lookup"><span data-stu-id="2a225-241">**SaveAtExit**: Append history file when PowerShell exits.</span></span>
- <span data-ttu-id="2a225-242">**SaveNothing**: gebruik geen geschiedenis bestand.</span><span class="sxs-lookup"><span data-stu-id="2a225-242">**SaveNothing**: Don't use a history file.</span></span>

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

### <span data-ttu-id="2a225-243">-HistorySearchCaseSensitive</span><span class="sxs-lookup"><span data-stu-id="2a225-243">-HistorySearchCaseSensitive</span></span>

<span data-ttu-id="2a225-244">Hiermee geeft u op dat zoeken in de geschiedenis hoofdletter gevoelig is in functions zoals **ReverseSearchHistory** of **HistorySearchBackward**.</span><span class="sxs-lookup"><span data-stu-id="2a225-244">Specifies that history searching is case-sensitive in functions like **ReverseSearchHistory** or **HistorySearchBackward**.</span></span>

<span data-ttu-id="2a225-245">De eigenschap **HistorySearchCaseSensitive** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `False` .</span><span class="sxs-lookup"><span data-stu-id="2a225-245">By default, the **HistorySearchCaseSensitive** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="2a225-246">Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` .</span><span class="sxs-lookup"><span data-stu-id="2a225-246">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="2a225-247">Als u de waarde van de eigenschap terug wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-HistorySearchCaseSensitive:$False` .</span><span class="sxs-lookup"><span data-stu-id="2a225-247">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCaseSensitive:$False`.</span></span>

<span data-ttu-id="2a225-248">Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:</span><span class="sxs-lookup"><span data-stu-id="2a225-248">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="2a225-249">-HistorySearchCursorMovesToEnd</span><span class="sxs-lookup"><span data-stu-id="2a225-249">-HistorySearchCursorMovesToEnd</span></span>

<span data-ttu-id="2a225-250">Hiermee wordt aangegeven dat de cursor wordt verplaatst naar het einde van opdrachten die u uit de geschiedenis laadt met behulp van een zoek opdracht.</span><span class="sxs-lookup"><span data-stu-id="2a225-250">Indicates that the cursor moves to the end of commands that you load from history by using a search.</span></span>
<span data-ttu-id="2a225-251">Als deze para meter is ingesteld op `$False` , blijft de cursor op de positie waar deze zich bevond toen u op de pijl omhoog of omlaag was geklikt.</span><span class="sxs-lookup"><span data-stu-id="2a225-251">When this parameter is set to `$False`, the cursor remains at the position it was when you pressed the up or down arrows.</span></span>

<span data-ttu-id="2a225-252">De eigenschap **HistorySearchCursorMovesToEnd** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `False` .</span><span class="sxs-lookup"><span data-stu-id="2a225-252">By default, the **HistorySearchCursorMovesToEnd** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="2a225-253">Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` .</span><span class="sxs-lookup"><span data-stu-id="2a225-253">Using this **SwitchParameter** set the property value to `True`.</span></span> <span data-ttu-id="2a225-254">Als u de waarde van de eigenschap terug wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-HistorySearchCursorMovesToEnd:$False` .</span><span class="sxs-lookup"><span data-stu-id="2a225-254">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCursorMovesToEnd:$False`.</span></span>

<span data-ttu-id="2a225-255">Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:</span><span class="sxs-lookup"><span data-stu-id="2a225-255">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="2a225-256">-MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="2a225-256">-MaximumHistoryCount</span></span>

<span data-ttu-id="2a225-257">Hiermee geeft u het maximum aantal opdrachten op dat moet worden opgeslagen in de **PSReadLine** geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="2a225-257">Specifies the maximum number of commands to save in **PSReadLine** history.</span></span>

<span data-ttu-id="2a225-258">De geschiedenis van de **PSReadLine** is gescheiden van de Power shell-geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="2a225-258">**PSReadLine** history is separate from PowerShell history.</span></span>

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

### <span data-ttu-id="2a225-259">-MaximumKillRingCount</span><span class="sxs-lookup"><span data-stu-id="2a225-259">-MaximumKillRingCount</span></span>

<span data-ttu-id="2a225-260">Hiermee geeft u het maximum aantal items op dat is opgeslagen in de Kill-ring.</span><span class="sxs-lookup"><span data-stu-id="2a225-260">Specifies the maximum number of items stored in the kill ring.</span></span>

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

### <span data-ttu-id="2a225-261">-PromptText</span><span class="sxs-lookup"><span data-stu-id="2a225-261">-PromptText</span></span>

<span data-ttu-id="2a225-262">Wanneer er een parseringsfout optreedt, wordt in **PSReadLine** een deel van de prompt rood gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="2a225-262">When there's a parse error, **PSReadLine** changes a part of the prompt red.</span></span> <span data-ttu-id="2a225-263">**PSReadLine** analyseert uw prompt functie om te bepalen hoe u alleen de kleur van een deel van uw prompt kunt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="2a225-263">**PSReadLine** analyzes your prompt function to determine how to change only the color of part of your prompt.</span></span> <span data-ttu-id="2a225-264">Deze analyse is niet 100% betrouwbaar.</span><span class="sxs-lookup"><span data-stu-id="2a225-264">This analysis isn't 100% reliable.</span></span>

<span data-ttu-id="2a225-265">Gebruik deze optie als **PSReadLine** uw prompt op onverwachte manieren wijzigt.</span><span class="sxs-lookup"><span data-stu-id="2a225-265">Use this option if **PSReadLine** is changing your prompt in unexpected ways.</span></span> <span data-ttu-id="2a225-266">Geef een wille keurige spatie op.</span><span class="sxs-lookup"><span data-stu-id="2a225-266">Include any trailing whitespace.</span></span>

<span data-ttu-id="2a225-267">Bijvoorbeeld, als uw prompt functie lijkt op het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="2a225-267">For example, if your prompt function looked like the following example:</span></span>

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

<span data-ttu-id="2a225-268">Vervolgens ingesteld:</span><span class="sxs-lookup"><span data-stu-id="2a225-268">Then set:</span></span>

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

### <span data-ttu-id="2a225-269">-ShowToolTips</span><span class="sxs-lookup"><span data-stu-id="2a225-269">-ShowToolTips</span></span>

<span data-ttu-id="2a225-270">Wanneer mogelijke voltooiingen worden weer gegeven, worden knop Info weer gegeven in de lijst met voltooiingen.</span><span class="sxs-lookup"><span data-stu-id="2a225-270">When displaying possible completions, tooltips are shown in the list of completions.</span></span>

<span data-ttu-id="2a225-271">Deze optie is standaard ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="2a225-271">This option is enabled by default.</span></span> <span data-ttu-id="2a225-272">Deze optie is niet standaard ingeschakeld in eerdere versies van **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="2a225-272">This option wasn't enabled by default in prior versions of **PSReadLine**.</span></span> <span data-ttu-id="2a225-273">Als u wilt uitschakelen, stelt u deze optie in op `$False` .</span><span class="sxs-lookup"><span data-stu-id="2a225-273">To disable, set this option to `$False`.</span></span>

<span data-ttu-id="2a225-274">De eigenschap **ShowToolTips** van het object Global **PSConsoleReadLineOptions** is standaard ingesteld op `True` .</span><span class="sxs-lookup"><span data-stu-id="2a225-274">By default, the **ShowToolTips** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="2a225-275">Met deze **SwitchParameter** stelt u de waarde van de eigenschap in op `True` .</span><span class="sxs-lookup"><span data-stu-id="2a225-275">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="2a225-276">Als u de waarde van de eigenschap wilt wijzigen, moet u de waarde van de **SwitchParameter** als volgt opgeven: `-ShowToolTips:$False` .</span><span class="sxs-lookup"><span data-stu-id="2a225-276">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-ShowToolTips:$False`.</span></span>

<span data-ttu-id="2a225-277">Met de volgende opdracht kunt u de waarde van de eigenschap rechtstreeks instellen:</span><span class="sxs-lookup"><span data-stu-id="2a225-277">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="2a225-278">-ViModeChangeHandler</span><span class="sxs-lookup"><span data-stu-id="2a225-278">-ViModeChangeHandler</span></span>

<span data-ttu-id="2a225-279">Wanneer de **ViModeIndicator** is ingesteld op `Script` , wordt het opgegeven script blok elke keer dat de modus verandert, aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="2a225-279">When the **ViModeIndicator** is set to `Script`, the script block provided will be invoked every time the mode changes.</span></span> <span data-ttu-id="2a225-280">Het script blok biedt één argument van het type `ViMode` .</span><span class="sxs-lookup"><span data-stu-id="2a225-280">The script block is provided one argument of type `ViMode`.</span></span>

<span data-ttu-id="2a225-281">Deze para meter is geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="2a225-281">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="2a225-282">-ViModeIndicator</span><span class="sxs-lookup"><span data-stu-id="2a225-282">-ViModeIndicator</span></span>

<span data-ttu-id="2a225-283">Met deze optie stelt u de visuele indicatie in voor de huidige **VI** -modus.</span><span class="sxs-lookup"><span data-stu-id="2a225-283">This option sets the visual indication for the current **Vi** mode.</span></span> <span data-ttu-id="2a225-284">De Invoeg modus of de opdracht modus.</span><span class="sxs-lookup"><span data-stu-id="2a225-284">Either insert mode or command mode.</span></span>

<span data-ttu-id="2a225-285">De geldige waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="2a225-285">The valid values are as follows:</span></span>

- <span data-ttu-id="2a225-286">**Geen**: er is geen indicatie.</span><span class="sxs-lookup"><span data-stu-id="2a225-286">**None**: There's no indication.</span></span>
- <span data-ttu-id="2a225-287">**Prompt**: de prompt verandert in kleur.</span><span class="sxs-lookup"><span data-stu-id="2a225-287">**Prompt**: The prompt changes color.</span></span>
- <span data-ttu-id="2a225-288">**Cursor**: de grootte van de cursor verandert.</span><span class="sxs-lookup"><span data-stu-id="2a225-288">**Cursor**: The cursor changes size.</span></span>
- <span data-ttu-id="2a225-289">**Script**: door de gebruiker opgegeven tekst wordt afgedrukt.</span><span class="sxs-lookup"><span data-stu-id="2a225-289">**Script**: User-specified text is printed.</span></span>

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

### <span data-ttu-id="2a225-290">-WordDelimiters</span><span class="sxs-lookup"><span data-stu-id="2a225-290">-WordDelimiters</span></span>

<span data-ttu-id="2a225-291">Hiermee geeft u de tekens op waarmee woorden worden beperkt voor functies zoals **ForwardWord** of **KillWord**.</span><span class="sxs-lookup"><span data-stu-id="2a225-291">Specifies the characters that delimit words for functions like **ForwardWord** or **KillWord**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"---
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2a225-292">-PredictionSource</span><span class="sxs-lookup"><span data-stu-id="2a225-292">-PredictionSource</span></span>

<span data-ttu-id="2a225-293">Hiermee geeft u de bron voor PSReadLine op om voorspellende suggesties te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="2a225-293">Specifies the source for PSReadLine to get predictive suggestions.</span></span>

<span data-ttu-id="2a225-294">Geldige waarden zijn:</span><span class="sxs-lookup"><span data-stu-id="2a225-294">Valid values are:</span></span>

- <span data-ttu-id="2a225-295">**Geen** : de functie voor voorspellende IntelliSense uitschakelen (standaard).</span><span class="sxs-lookup"><span data-stu-id="2a225-295">**None** - disable the predictive IntelliSense feature (default).</span></span>
<span data-ttu-id="2a225-296">-\`**Geschiedenis** : Schakel de functie voor voorspellende IntelliSense in en gebruik de PSReadLine-geschiedenis als enige bron.</span><span class="sxs-lookup"><span data-stu-id="2a225-296">-\`**History** - enable the predictive IntelliSense feature and use the PSReadLine history as the only source.</span></span>
- <span data-ttu-id="2a225-297">**Invoeg toepassing** : Schakel de functie voor voorspellende IntelliSense in en gebruik de invoeg toepassingen ( `CommandPrediction` ) als enige bron.</span><span class="sxs-lookup"><span data-stu-id="2a225-297">**Plugin** - enable the predictive IntelliSense feature and use the plugins (`CommandPrediction`) as the only source.</span></span> <span data-ttu-id="2a225-298">Deze waarde is toegevoegd in PSReadLine 2.2.0</span><span class="sxs-lookup"><span data-stu-id="2a225-298">This value was added in PSReadLine 2.2.0</span></span>
- <span data-ttu-id="2a225-299">**HistoryAndPlugin** : Schakel de functie voor voorspellende IntelliSense in en gebruik zowel de geschiedenis als de-invoeg toepassing als bronnen.</span><span class="sxs-lookup"><span data-stu-id="2a225-299">**HistoryAndPlugin** - enable the predictive IntelliSense feature and use both history and plugin as the sources.</span></span> <span data-ttu-id="2a225-300">Deze waarde is toegevoegd in PSReadLine 2.2.0</span><span class="sxs-lookup"><span data-stu-id="2a225-300">This value was added in PSReadLine 2.2.0</span></span>

```yaml
Type: Microsoft.PowerShell.PredictionSource
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2a225-301">-PredictionViewStyle</span><span class="sxs-lookup"><span data-stu-id="2a225-301">-PredictionViewStyle</span></span>

<span data-ttu-id="2a225-302">Hiermee stelt u de stijl in voor de weer gave van de voorspelde tekst.</span><span class="sxs-lookup"><span data-stu-id="2a225-302">Sets the style for the display of the predictive text.</span></span> <span data-ttu-id="2a225-303">De standaard waarde is **InlineView**.</span><span class="sxs-lookup"><span data-stu-id="2a225-303">The default is **InlineView**.</span></span>

- <span data-ttu-id="2a225-304">**InlineView** : de stijl die vandaag is, vergelijkbaar met die van vis en zsh.</span><span class="sxs-lookup"><span data-stu-id="2a225-304">**InlineView** - the style as existing today, similar as in fish shell and zsh.</span></span> <span data-ttu-id="2a225-305">(standaard)</span><span class="sxs-lookup"><span data-stu-id="2a225-305">(default)</span></span>
- <span data-ttu-id="2a225-306">**List View** : suggesties worden weer gegeven in een vervolg keuzelijst en gebruikers kunnen selecteren met behulp van <kbd>pijl-omhoog</kbd> en <kbd>DownArrow</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2a225-306">**ListView** - suggestions are rendered in a drop down list, and users can select using <kbd>UpArrow</kbd> and <kbd>DownArrow</kbd>.</span></span>

<span data-ttu-id="2a225-307">Deze para meter is toegevoegd in PSReadLine 2.2.0</span><span class="sxs-lookup"><span data-stu-id="2a225-307">This parameter was added in PSReadLine 2.2.0</span></span>

```yaml
Type: Microsoft.PowerShell.PredictionViewStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineView
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2a225-308">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2a225-308">CommonParameters</span></span>

<span data-ttu-id="2a225-309">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2a225-309">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2a225-310">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2a225-310">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2a225-311">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="2a225-311">Inputs</span></span>

### <span data-ttu-id="2a225-312">Geen</span><span class="sxs-lookup"><span data-stu-id="2a225-312">None</span></span>

<span data-ttu-id="2a225-313">U kunt objecten niet naar `Set-PSReadLineOption.`</span><span class="sxs-lookup"><span data-stu-id="2a225-313">You cannot pipe objects to `Set-PSReadLineOption.`</span></span>

## <span data-ttu-id="2a225-314">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="2a225-314">Outputs</span></span>

### <span data-ttu-id="2a225-315">Geen</span><span class="sxs-lookup"><span data-stu-id="2a225-315">None</span></span>

<span data-ttu-id="2a225-316">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="2a225-316">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2a225-317">Notities</span><span class="sxs-lookup"><span data-stu-id="2a225-317">Notes</span></span>

## <span data-ttu-id="2a225-318">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="2a225-318">Related links</span></span>

[<span data-ttu-id="2a225-319">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="2a225-319">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

[<span data-ttu-id="2a225-320">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2a225-320">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="2a225-321">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="2a225-321">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="2a225-322">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2a225-322">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="2a225-323">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="2a225-323">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
