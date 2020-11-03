---
description: Hierin worden de speciale teken reeksen beschreven die bepalen hoe Power shell de volgende tekens in de reeks interpreteert.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: 6856d903276f5cbe4db222ac4c5d64ce6939413e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252689"
---
# <a name="about-special-characters"></a><span data-ttu-id="aaa9e-104">Speciale tekens</span><span class="sxs-lookup"><span data-stu-id="aaa9e-104">About Special Characters</span></span>

## <a name="short-description"></a><span data-ttu-id="aaa9e-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="aaa9e-105">Short description</span></span>

<span data-ttu-id="aaa9e-106">Hierin worden de speciale teken reeksen beschreven die bepalen hoe Power shell de volgende tekens in de reeks interpreteert.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-106">Describes the special character sequences that control how PowerShell interprets the next characters in the sequence.</span></span>

## <a name="long-description"></a><span data-ttu-id="aaa9e-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="aaa9e-107">Long description</span></span>

<span data-ttu-id="aaa9e-108">Power shell ondersteunt een set speciale teken reeksen die worden gebruikt om tekens weer te geven die geen deel uitmaken van de standaard tekenset.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-108">PowerShell supports a set of special character sequences that are used to represent characters that aren't part of the standard character set.</span></span> <span data-ttu-id="aaa9e-109">De reeksen worden meestal _escape-reeksen_ genoemd.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-109">The sequences are commonly known as _escape sequences_.</span></span>

<span data-ttu-id="aaa9e-110">Escape reeksen beginnen met het apostroffen-teken, ook wel het accent grave (ASCII 96), en zijn hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-110">Escape sequences begin with the backtick character, known as the grave accent (ASCII 96), and are case-sensitive.</span></span> <span data-ttu-id="aaa9e-111">Het apostroffen-teken kan ook worden aangeduid als het _escape-teken_.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-111">The backtick character can also be referred to as the _escape character_.</span></span>

<span data-ttu-id="aaa9e-112">Escape-reeksen worden alleen geïnterpreteerd als ze zijn opgenomen in teken reeksen met dubbele aanhalings tekens ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="aaa9e-112">Escape sequences are only interpreted when contained in double-quoted (`"`) strings.</span></span>

<span data-ttu-id="aaa9e-113">Power shell herkent deze escape reeksen:</span><span class="sxs-lookup"><span data-stu-id="aaa9e-113">PowerShell recognizes these escape sequences:</span></span>

|  <span data-ttu-id="aaa9e-114">Reeks</span><span class="sxs-lookup"><span data-stu-id="aaa9e-114">Sequence</span></span>   |       <span data-ttu-id="aaa9e-115">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="aaa9e-115">Description</span></span>       |
| ----------- | ----------------------- |
| `` `0 ``    | <span data-ttu-id="aaa9e-116">Null</span><span class="sxs-lookup"><span data-stu-id="aaa9e-116">Null</span></span>                    |
| `` `a ``    | <span data-ttu-id="aaa9e-117">Waarschuwing</span><span class="sxs-lookup"><span data-stu-id="aaa9e-117">Alert</span></span>                   |
| `` `b ``    | <span data-ttu-id="aaa9e-118">Backspace</span><span class="sxs-lookup"><span data-stu-id="aaa9e-118">Backspace</span></span>               |
| `` `e ``    | <span data-ttu-id="aaa9e-119">Escape</span><span class="sxs-lookup"><span data-stu-id="aaa9e-119">Escape</span></span>                  |
| `` `f ``    | <span data-ttu-id="aaa9e-120">Formulier feed</span><span class="sxs-lookup"><span data-stu-id="aaa9e-120">Form feed</span></span>               |
| `` `n ``    | <span data-ttu-id="aaa9e-121">Nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="aaa9e-121">New line</span></span>                |
| `` `r ``    | <span data-ttu-id="aaa9e-122">Regel terugloop</span><span class="sxs-lookup"><span data-stu-id="aaa9e-122">Carriage return</span></span>         |
| `` `t ``    | <span data-ttu-id="aaa9e-123">Tabblad horizon taal</span><span class="sxs-lookup"><span data-stu-id="aaa9e-123">Horizontal tab</span></span>          |
| `` `u{x} `` | <span data-ttu-id="aaa9e-124">Unicode-escape reeks</span><span class="sxs-lookup"><span data-stu-id="aaa9e-124">Unicode escape sequence</span></span> |
| `` `v ``    | <span data-ttu-id="aaa9e-125">Verticaal tabblad</span><span class="sxs-lookup"><span data-stu-id="aaa9e-125">Vertical tab</span></span>            |

<span data-ttu-id="aaa9e-126">Power Shell heeft ook een speciaal token om te markeren waar u wilt parseren om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-126">PowerShell also has a special token to mark where you want parsing to stop.</span></span> <span data-ttu-id="aaa9e-127">Alle tekens die deze token volgen, worden gebruikt als letterlijke waarden die niet worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-127">All characters that follow this token are used as literal values that aren't interpreted.</span></span>

<span data-ttu-id="aaa9e-128">Speciaal parserings token:</span><span class="sxs-lookup"><span data-stu-id="aaa9e-128">Special parsing token:</span></span>

| <span data-ttu-id="aaa9e-129">Reeks</span><span class="sxs-lookup"><span data-stu-id="aaa9e-129">Sequence</span></span> |            <span data-ttu-id="aaa9e-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="aaa9e-130">Description</span></span>             |
| -------- | ---------------------------------- |
| `--%`    | <span data-ttu-id="aaa9e-131">Stoppen met het parseren van alles dat volgt</span><span class="sxs-lookup"><span data-stu-id="aaa9e-131">Stop parsing anything that follows</span></span> |

## <a name="null-0"></a><span data-ttu-id="aaa9e-132">Null (' 0)</span><span class="sxs-lookup"><span data-stu-id="aaa9e-132">Null (\`0)</span></span>

<span data-ttu-id="aaa9e-133">Het null- `` `0 `` teken () wordt weer gegeven als een lege ruimte in Power shell-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-133">The null (`` `0 ``) character appears as an empty space in PowerShell output.</span></span>
<span data-ttu-id="aaa9e-134">Met deze functie kunt u Power shell gebruiken om tekst bestanden te lezen en verwerken die null-tekens gebruiken, zoals teken reeks beëindiging of Indica tors voor het beëindigen van een record.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-134">This functionality allows you to use PowerShell to read and process text files that use null characters, such as string termination or record termination indicators.</span></span> <span data-ttu-id="aaa9e-135">Het speciale teken voor een null-waarde is niet gelijk aan de `$null` variabele, die een **Null** -waarden opslaat.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-135">The null special character isn't equivalent to the `$null` variable, which stores a **null** value.</span></span>

## <a name="alert-a"></a><span data-ttu-id="aaa9e-136">Waarschuwing (' a ')</span><span class="sxs-lookup"><span data-stu-id="aaa9e-136">Alert (\`a)</span></span>

<span data-ttu-id="aaa9e-137">Met het teken alert ( `` `a `` ) wordt een piep Toon signaal verzonden naar de spreker van de computer.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-137">The alert (`` `a ``) character sends a beep signal to the computer's speaker.</span></span>
<span data-ttu-id="aaa9e-138">U kunt dit teken gebruiken om een gebruiker te waarschuwen over een bedreigende actie.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-138">You can use this character to warn a user about an impending action.</span></span> <span data-ttu-id="aaa9e-139">In het volgende voor beeld worden twee piep signalen verzonden naar de spreker van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-139">The following example sends two beep signals to the local computer's speaker.</span></span>

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a><span data-ttu-id="aaa9e-140">Backspace (' b ')</span><span class="sxs-lookup"><span data-stu-id="aaa9e-140">Backspace (\`b)</span></span>

<span data-ttu-id="aaa9e-141">Het Backspace `` `b `` teken () verplaatst de cursor één teken naar achter, maar verwijdert geen tekens.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-141">The backspace (`` `b ``) character moves the cursor back one character, but it doesn't delete any characters.</span></span>

<span data-ttu-id="aaa9e-142">In het voor beeld wordt de **back-up** van Word geschreven en vervolgens de cursor twee keer verplaatst.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-142">The example writes the word **backup** and then moves the cursor back twice.</span></span>
<span data-ttu-id="aaa9e-143">Op de nieuwe positie schrijft vervolgens een spatie, gevolgd door het woord **uit**.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-143">Then, at the new position, writes a space followed by the word **out**.</span></span>

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="escape-e"></a><span data-ttu-id="aaa9e-144">Escape (' e)</span><span class="sxs-lookup"><span data-stu-id="aaa9e-144">Escape (\`e)</span></span>

<span data-ttu-id="aaa9e-145">Het escape- `` `e `` teken () wordt meestal gebruikt voor het opgeven van een virtuele terminal reeks (ANSI Escape Sequence) waarmee de kleur van tekst en andere tekst kenmerken, zoals vet en onderstrepen, worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-145">The escape (`` `e ``) character is most commonly used to specify a virtual terminal sequence (ANSI escape sequence) that modifies the color of text and other text attributes such as bolding and underlining.</span></span> <span data-ttu-id="aaa9e-146">Deze reeksen kunnen ook worden gebruikt voor het positioneren en schuiven van de cursor.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-146">These sequences can also be used for cursor positioning and scrolling.</span></span> <span data-ttu-id="aaa9e-147">De Power shell-host moet virtuele terminal reeksen ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-147">The PowerShell host must support virtual terminal sequences.</span></span> <span data-ttu-id="aaa9e-148">U kunt de Booleaanse waarde van controleren `$Host.UI.SupportsVirtualTerminal` om te bepalen of deze ANSI-reeksen worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-148">You can check the boolean value of `$Host.UI.SupportsVirtualTerminal` to determine if these ANSI sequences are supported.</span></span>

<span data-ttu-id="aaa9e-149">Zie [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)voor meer informatie over ANSI escape-reeksen.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-149">For more information about ANSI escape sequences, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

<span data-ttu-id="aaa9e-150">In het volgende voor beeld wordt tekst met een groene voorgrond kleur uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-150">The following example outputs text with a green foreground color.</span></span>

```powershell
$fgColor = 32 # green
"`e[${fgColor}mGreen text`e[0m"
```

```Output
Green text
```

## <a name="form-feed-f"></a><span data-ttu-id="aaa9e-151">Formulier feed (f)</span><span class="sxs-lookup"><span data-stu-id="aaa9e-151">Form feed (\`f)</span></span>

<span data-ttu-id="aaa9e-152">Het teken voor formulier invoer ( `` `f `` ) is een afdruk instructie waarmee de huidige pagina wordt uitgeworpen en wordt verder afgedrukt op de volgende pagina.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-152">The form feed (`` `f ``) character is a print instruction that ejects the current page and continues printing on the next page.</span></span> <span data-ttu-id="aaa9e-153">Het teken voor de formulier invoer is alleen van invloed op afgedrukte documenten.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-153">The form feed character only affects printed documents.</span></span> <span data-ttu-id="aaa9e-154">Dit heeft geen invloed op de scherm uitvoer.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-154">It doesn't affect screen output.</span></span>

## <a name="new-line-n"></a><span data-ttu-id="aaa9e-155">Nieuwe regel (' n ')</span><span class="sxs-lookup"><span data-stu-id="aaa9e-155">New line (\`n)</span></span>

<span data-ttu-id="aaa9e-156">Met het nieuwe regel `` `n `` teken () wordt direct na het teken een regel afbreek punt ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-156">The new line (`` `n ``) character inserts a line break immediately after the character.</span></span>

<span data-ttu-id="aaa9e-157">In dit voor beeld ziet u hoe u het nieuwe regel teken kunt gebruiken om regel einden in een opdracht te maken `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="aaa9e-157">This example shows how to use the new line character to create line breaks in a `Write-Host` command.</span></span>

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a><span data-ttu-id="aaa9e-158">Regel terugloop (r)</span><span class="sxs-lookup"><span data-stu-id="aaa9e-158">Carriage return (\`r)</span></span>

<span data-ttu-id="aaa9e-159">Met het teken Enter Return ( `` `r `` ) verplaatst u de uitvoer cursor naar het begin van de huidige regel en gaat u verder met schrijven.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-159">The carriage return (`` `r ``) character moves the output cursor to the beginning of the current line and continues writing.</span></span> <span data-ttu-id="aaa9e-160">Alle tekens op de huidige regel worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-160">Any characters on the current line are overwritten.</span></span>

<span data-ttu-id="aaa9e-161">In dit voor beeld wordt de tekst vóór de regel terugloop overschreven.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-161">In this example, the text before the carriage return is overwritten.</span></span>

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

<span data-ttu-id="aaa9e-162">U ziet dat de tekst voordat het `` `r `` teken wordt verwijderd, wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-162">Notice that the text before the `` `r `` character is not deleted, it is overwritten.</span></span>

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a><span data-ttu-id="aaa9e-163">Horizon taal tabblad (niet)</span><span class="sxs-lookup"><span data-stu-id="aaa9e-163">Horizontal tab (\`t)</span></span>

<span data-ttu-id="aaa9e-164">Het horizontale tabblad ( `` `t `` ) teken gaat naar de volgende tabpositie en blijft op dat punt schrijven.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-164">The horizontal tab (`` `t ``) character advances to the next tab stop and continues writing at that point.</span></span> <span data-ttu-id="aaa9e-165">De Power shell-console heeft standaard een tabpositie op elke achtste spatie.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-165">By default, the PowerShell console has a tab stop at every eighth space.</span></span>

<span data-ttu-id="aaa9e-166">In dit voor beeld worden twee tabbladen tussen elke kolom ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-166">This example inserts two tabs between each column.</span></span>

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="unicode-character-ux"></a><span data-ttu-id="aaa9e-167">Unicode-teken (' u {x})</span><span class="sxs-lookup"><span data-stu-id="aaa9e-167">Unicode character (\`u{x})</span></span>

<span data-ttu-id="aaa9e-168">Met de Unicode-escape reeks ( `` `u{x} `` ) kunt u een Unicode-teken opgeven door de hexadecimale weer gave van het code punt.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-168">The Unicode escape sequence (`` `u{x} ``) allows you to specify any Unicode character by the hexadecimal representation of its code point.</span></span> <span data-ttu-id="aaa9e-169">Dit geldt ook voor Unicode-tekens boven het basis vlak (meertalig) (> `0xFFFF` ), dat Emoji-tekens bevat, zoals het teken **duim omhoog** ( `` `u{1F44D} `` ).</span><span class="sxs-lookup"><span data-stu-id="aaa9e-169">This includes Unicode characters above the Basic Multilingual Plane (> `0xFFFF`) which includes emoji characters such as the **thumbs up** (`` `u{1F44D} ``) character.</span></span> <span data-ttu-id="aaa9e-170">De Unicode-escape reeks vereist ten minste één hexadecimaal cijfer en ondersteunt Maxi maal zes hexadecimale cijfers.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-170">The Unicode escape sequence requires at least one hexadecimal digit and supports up to six hexadecimal digits.</span></span> <span data-ttu-id="aaa9e-171">De maximale hexadecimale waarde voor de reeks is `10FFFF` .</span><span class="sxs-lookup"><span data-stu-id="aaa9e-171">The maximum hexadecimal value for the sequence is `10FFFF`.</span></span>

<span data-ttu-id="aaa9e-172">In dit voor beeld wordt het symbool **pijl-omhoog** (&#x2195;) uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-172">This example outputs the **up down arrow** (&#x2195;) symbol.</span></span>

```powershell
"`u{2195}"
```

## <a name="vertical-tab-v"></a><span data-ttu-id="aaa9e-173">Verticaal tabblad (' v)</span><span class="sxs-lookup"><span data-stu-id="aaa9e-173">Vertical tab (\`v)</span></span>

<span data-ttu-id="aaa9e-174">Het horizontale tabblad ( `` `v `` ) teken gaat naar het volgende verticale tabblad en schrijft de resterende uitvoer op dat punt.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-174">The horizontal tab (`` `v ``) character advances to the next vertical tab stop and writes the remaining output at that point.</span></span> <span data-ttu-id="aaa9e-175">Dit heeft geen invloed op de standaard Windows-console.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-175">This has no effect in the default Windows console.</span></span>

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

<span data-ttu-id="aaa9e-176">In het volgende voor beeld ziet u de uitvoer die u op een printer of op een andere console host zou krijgen.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-176">The following example shows the output you would get on a printer or in a different console host.</span></span>

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a><span data-ttu-id="aaa9e-177">Token voor stoppen en parseren (--%)</span><span class="sxs-lookup"><span data-stu-id="aaa9e-177">Stop-parsing token (--%)</span></span>

<span data-ttu-id="aaa9e-178">Het token voor het stoppen van parseren ( `--%` ) voor komt dat Power shell teken reeksen interpreteert als Power shell-opdrachten en-expressies.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-178">The stop-parsing (`--%`) token prevents PowerShell from interpreting strings as PowerShell commands and expressions.</span></span> <span data-ttu-id="aaa9e-179">Hierdoor kunnen die teken reeksen worden door gegeven aan andere Program ma's voor interpretatie.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-179">This allows those strings to be passed to other programs for interpretation.</span></span>

<span data-ttu-id="aaa9e-180">Plaats het token voor het stoppen van het parseren na de programma naam en vóór programma argumenten die fouten kunnen veroorzaken.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-180">Place the stop-parsing token after the program name and before program arguments that might cause errors.</span></span>

<span data-ttu-id="aaa9e-181">In dit voor beeld `Icacls` maakt de opdracht gebruik van het token voor stoppen-parseren.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-181">In this example, the `Icacls` command uses the stop-parsing token.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="aaa9e-182">Power shell verzendt de volgende teken reeks naar `Icacls` .</span><span class="sxs-lookup"><span data-stu-id="aaa9e-182">PowerShell sends the following string to `Icacls`.</span></span>

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="aaa9e-183">Hier volgt nog een voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-183">Here is another example.</span></span> <span data-ttu-id="aaa9e-184">De functie **showArgs** voert de waarden uit die zijn door gegeven.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-184">The **showArgs** function outputs the values passed to it.</span></span> <span data-ttu-id="aaa9e-185">In dit voor beeld geven we de variabele `$HOME` met de naam naar de functie twee keer door.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-185">In this example, we pass the variable named `$HOME` to the function twice.</span></span>

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

U kunt in de uitvoer zien dat de variabele voor de eerste para meter `$HOME` wordt geïnterpreteerd door Power shell, zodat de waarde van de variabele wordt door gegeven aan de functie. <span data-ttu-id="aaa9e-187">Het tweede gebruik van `$HOME` is na het token voor het stoppen van parseren, zodat de teken reeks "$Home" wordt door gegeven aan de functie zonder interpretatie.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-187">The second use of `$HOME` comes after the stop-parsing token, so the string "$HOME" is passed to the function without interpretation.</span></span>

```Output
$args = C:\Users\username|--%|$HOME
```

<span data-ttu-id="aaa9e-188">Zie [about_Parsing](about_Parsing.md)voor meer informatie over het stop-parseren token.</span><span class="sxs-lookup"><span data-stu-id="aaa9e-188">For more information about the stop-parsing token, see [about_Parsing](about_Parsing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aaa9e-189">Zie ook</span><span class="sxs-lookup"><span data-stu-id="aaa9e-189">See also</span></span>

[<span data-ttu-id="aaa9e-190">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="aaa9e-190">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

