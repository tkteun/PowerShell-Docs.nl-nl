---
description: Hierin worden de speciale teken reeksen beschreven die bepalen hoe Power shell de volgende tekens in de reeks interpreteert.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: 7e0ea9298dd85627c08298917464cb005f4f37ff
ms.sourcegitcommit: 364c3fe46b2069b810107d840be59fe519ea7b4a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/10/2021
ms.locfileid: "100100730"
---
# <a name="about-special-characters"></a><span data-ttu-id="c791a-104">Speciale tekens</span><span class="sxs-lookup"><span data-stu-id="c791a-104">About Special Characters</span></span>

## <a name="short-description"></a><span data-ttu-id="c791a-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="c791a-105">Short description</span></span>

<span data-ttu-id="c791a-106">Hierin worden de speciale teken reeksen beschreven die bepalen hoe Power shell de volgende tekens in de reeks interpreteert.</span><span class="sxs-lookup"><span data-stu-id="c791a-106">Describes the special character sequences that control how PowerShell interprets the next characters in the sequence.</span></span>

## <a name="long-description"></a><span data-ttu-id="c791a-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="c791a-107">Long description</span></span>

<span data-ttu-id="c791a-108">Power shell ondersteunt een set speciale teken reeksen die worden gebruikt om tekens weer te geven die geen deel uitmaken van de standaard tekenset.</span><span class="sxs-lookup"><span data-stu-id="c791a-108">PowerShell supports a set of special character sequences that are used to represent characters that aren't part of the standard character set.</span></span> <span data-ttu-id="c791a-109">De reeksen worden meestal _escape-reeksen_ genoemd.</span><span class="sxs-lookup"><span data-stu-id="c791a-109">The sequences are commonly known as _escape sequences_.</span></span>

<span data-ttu-id="c791a-110">Escape reeksen beginnen met het apostroffen-teken, ook wel het accent grave (ASCII 96), en zijn hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="c791a-110">Escape sequences begin with the backtick character, known as the grave accent (ASCII 96), and are case-sensitive.</span></span> <span data-ttu-id="c791a-111">Het apostroffen-teken kan ook worden aangeduid als het _escape-teken_.</span><span class="sxs-lookup"><span data-stu-id="c791a-111">The backtick character can also be referred to as the _escape character_.</span></span>

<span data-ttu-id="c791a-112">Escape-reeksen worden alleen geïnterpreteerd als ze zijn opgenomen in teken reeksen met dubbele aanhalings tekens ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="c791a-112">Escape sequences are only interpreted when contained in double-quoted (`"`) strings.</span></span>

<span data-ttu-id="c791a-113">Power shell herkent deze escape reeksen:</span><span class="sxs-lookup"><span data-stu-id="c791a-113">PowerShell recognizes these escape sequences:</span></span>

|  <span data-ttu-id="c791a-114">Reeks</span><span class="sxs-lookup"><span data-stu-id="c791a-114">Sequence</span></span>   |       <span data-ttu-id="c791a-115">Description</span><span class="sxs-lookup"><span data-stu-id="c791a-115">Description</span></span>       |
| ----------- | ----------------------- |
| `` `0 ``    | <span data-ttu-id="c791a-116">Null</span><span class="sxs-lookup"><span data-stu-id="c791a-116">Null</span></span>                    |
| `` `a ``    | <span data-ttu-id="c791a-117">Waarschuwing</span><span class="sxs-lookup"><span data-stu-id="c791a-117">Alert</span></span>                   |
| `` `b ``    | <span data-ttu-id="c791a-118">Backspace</span><span class="sxs-lookup"><span data-stu-id="c791a-118">Backspace</span></span>               |
| `` `f ``    | <span data-ttu-id="c791a-119">Formulier feed</span><span class="sxs-lookup"><span data-stu-id="c791a-119">Form feed</span></span>               |
| `` `n ``    | <span data-ttu-id="c791a-120">Nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="c791a-120">New line</span></span>                |
| `` `r ``    | <span data-ttu-id="c791a-121">Regel terugloop</span><span class="sxs-lookup"><span data-stu-id="c791a-121">Carriage return</span></span>         |
| `` `t ``    | <span data-ttu-id="c791a-122">Tabblad horizon taal</span><span class="sxs-lookup"><span data-stu-id="c791a-122">Horizontal tab</span></span>          |
| `` `v ``    | <span data-ttu-id="c791a-123">Verticaal tabblad</span><span class="sxs-lookup"><span data-stu-id="c791a-123">Vertical tab</span></span>            |

<span data-ttu-id="c791a-124">Power Shell heeft ook een speciaal token om te markeren waar u wilt parseren om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="c791a-124">PowerShell also has a special token to mark where you want parsing to stop.</span></span> <span data-ttu-id="c791a-125">Alle tekens die deze token volgen, worden gebruikt als letterlijke waarden die niet worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="c791a-125">All characters that follow this token are used as literal values that aren't interpreted.</span></span>

<span data-ttu-id="c791a-126">Speciaal parserings token:</span><span class="sxs-lookup"><span data-stu-id="c791a-126">Special parsing token:</span></span>

| <span data-ttu-id="c791a-127">Reeks</span><span class="sxs-lookup"><span data-stu-id="c791a-127">Sequence</span></span> |            <span data-ttu-id="c791a-128">Description</span><span class="sxs-lookup"><span data-stu-id="c791a-128">Description</span></span>             |
| -------- | ---------------------------------- |
| `--%`    | <span data-ttu-id="c791a-129">Stoppen met het parseren van alles dat volgt</span><span class="sxs-lookup"><span data-stu-id="c791a-129">Stop parsing anything that follows</span></span> |

## <a name="null-0"></a><span data-ttu-id="c791a-130">Null (' 0)</span><span class="sxs-lookup"><span data-stu-id="c791a-130">Null (\`0)</span></span>

<span data-ttu-id="c791a-131">Het null- `` `0 `` teken () wordt weer gegeven als een lege ruimte in Power shell-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c791a-131">The null (`` `0 ``) character appears as an empty space in PowerShell output.</span></span>
<span data-ttu-id="c791a-132">Met deze functie kunt u Power shell gebruiken om tekst bestanden te lezen en verwerken die null-tekens gebruiken, zoals teken reeks beëindiging of Indica tors voor het beëindigen van een record.</span><span class="sxs-lookup"><span data-stu-id="c791a-132">This functionality allows you to use PowerShell to read and process text files that use null characters, such as string termination or record termination indicators.</span></span> <span data-ttu-id="c791a-133">Het speciale teken voor een null-waarde is niet gelijk aan de `$null` variabele, die een **Null** -waarden opslaat.</span><span class="sxs-lookup"><span data-stu-id="c791a-133">The null special character isn't equivalent to the `$null` variable, which stores a **null** value.</span></span>

## <a name="alert-a"></a><span data-ttu-id="c791a-134">Waarschuwing (' a ')</span><span class="sxs-lookup"><span data-stu-id="c791a-134">Alert (\`a)</span></span>

<span data-ttu-id="c791a-135">Met het teken alert ( `` `a `` ) wordt een piep Toon signaal verzonden naar de spreker van de computer.</span><span class="sxs-lookup"><span data-stu-id="c791a-135">The alert (`` `a ``) character sends a beep signal to the computer's speaker.</span></span>
<span data-ttu-id="c791a-136">U kunt dit teken gebruiken om een gebruiker te waarschuwen over een bedreigende actie.</span><span class="sxs-lookup"><span data-stu-id="c791a-136">You can use this character to warn a user about an impending action.</span></span> <span data-ttu-id="c791a-137">In het volgende voor beeld worden twee piep signalen verzonden naar de spreker van de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c791a-137">The following example sends two beep signals to the local computer's speaker.</span></span>

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a><span data-ttu-id="c791a-138">Backspace (' b ')</span><span class="sxs-lookup"><span data-stu-id="c791a-138">Backspace (\`b)</span></span>

<span data-ttu-id="c791a-139">Het Backspace `` `b `` teken () verplaatst de cursor één teken naar achter, maar verwijdert geen tekens.</span><span class="sxs-lookup"><span data-stu-id="c791a-139">The backspace (`` `b ``) character moves the cursor back one character, but it doesn't delete any characters.</span></span>

<span data-ttu-id="c791a-140">In het voor beeld wordt de **back-up** van Word geschreven en vervolgens de cursor twee keer verplaatst.</span><span class="sxs-lookup"><span data-stu-id="c791a-140">The example writes the word **backup** and then moves the cursor back twice.</span></span>
<span data-ttu-id="c791a-141">Op de nieuwe positie schrijft vervolgens een spatie, gevolgd door het woord **uit**.</span><span class="sxs-lookup"><span data-stu-id="c791a-141">Then, at the new position, writes a space followed by the word **out**.</span></span>

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="form-feed-f"></a><span data-ttu-id="c791a-142">Formulier feed (f)</span><span class="sxs-lookup"><span data-stu-id="c791a-142">Form feed (\`f)</span></span>

<span data-ttu-id="c791a-143">Het teken voor formulier invoer ( `` `f `` ) is een afdruk instructie waarmee de huidige pagina wordt uitgeworpen en wordt verder afgedrukt op de volgende pagina.</span><span class="sxs-lookup"><span data-stu-id="c791a-143">The form feed (`` `f ``) character is a print instruction that ejects the current page and continues printing on the next page.</span></span> <span data-ttu-id="c791a-144">Het teken voor de formulier invoer is alleen van invloed op afgedrukte documenten.</span><span class="sxs-lookup"><span data-stu-id="c791a-144">The form feed character only affects printed documents.</span></span> <span data-ttu-id="c791a-145">Dit heeft geen invloed op de scherm uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c791a-145">It doesn't affect screen output.</span></span>

## <a name="new-line-n"></a><span data-ttu-id="c791a-146">Nieuwe regel (' n ')</span><span class="sxs-lookup"><span data-stu-id="c791a-146">New line (\`n)</span></span>

<span data-ttu-id="c791a-147">Met het nieuwe regel `` `n `` teken () wordt direct na het teken een regel afbreek punt ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="c791a-147">The new line (`` `n ``) character inserts a line break immediately after the character.</span></span>

<span data-ttu-id="c791a-148">In dit voor beeld ziet u hoe u het nieuwe regel teken kunt gebruiken om regel einden in een opdracht te maken `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="c791a-148">This example shows how to use the new line character to create line breaks in a `Write-Host` command.</span></span>

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a><span data-ttu-id="c791a-149">Regel terugloop (r)</span><span class="sxs-lookup"><span data-stu-id="c791a-149">Carriage return (\`r)</span></span>

<span data-ttu-id="c791a-150">Met het teken Enter Return ( `` `r `` ) verplaatst u de uitvoer cursor naar het begin van de huidige regel en gaat u verder met schrijven.</span><span class="sxs-lookup"><span data-stu-id="c791a-150">The carriage return (`` `r ``) character moves the output cursor to the beginning of the current line and continues writing.</span></span> <span data-ttu-id="c791a-151">Alle tekens op de huidige regel worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="c791a-151">Any characters on the current line are overwritten.</span></span>

<span data-ttu-id="c791a-152">In dit voor beeld wordt de tekst vóór de regel terugloop overschreven.</span><span class="sxs-lookup"><span data-stu-id="c791a-152">In this example, the text before the carriage return is overwritten.</span></span>

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

<span data-ttu-id="c791a-153">U ziet dat de tekst voordat het `` `r `` teken wordt verwijderd, wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="c791a-153">Notice that the text before the `` `r `` character is not deleted, it is overwritten.</span></span>

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a><span data-ttu-id="c791a-154">Horizon taal tabblad (niet)</span><span class="sxs-lookup"><span data-stu-id="c791a-154">Horizontal tab (\`t)</span></span>

<span data-ttu-id="c791a-155">Het horizontale tabblad ( `` `t `` ) teken gaat naar de volgende tabpositie en blijft op dat punt schrijven.</span><span class="sxs-lookup"><span data-stu-id="c791a-155">The horizontal tab (`` `t ``) character advances to the next tab stop and continues writing at that point.</span></span> <span data-ttu-id="c791a-156">De Power shell-console heeft standaard een tabpositie op elke achtste spatie.</span><span class="sxs-lookup"><span data-stu-id="c791a-156">By default, the PowerShell console has a tab stop at every eighth space.</span></span>

<span data-ttu-id="c791a-157">In dit voor beeld worden twee tabbladen tussen elke kolom ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="c791a-157">This example inserts two tabs between each column.</span></span>

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="vertical-tab-v"></a><span data-ttu-id="c791a-158">Verticaal tabblad (' v)</span><span class="sxs-lookup"><span data-stu-id="c791a-158">Vertical tab (\`v)</span></span>

<span data-ttu-id="c791a-159">Het verticale tabblad ( `` `v `` ) teken gaat naar het volgende verticale tabblad en schrijft de resterende uitvoer op dat punt.</span><span class="sxs-lookup"><span data-stu-id="c791a-159">The vertical tab (`` `v ``) character advances to the next vertical tab stop and writes the remaining output at that point.</span></span> <span data-ttu-id="c791a-160">De weer gave van het verticale tabblad is afhankelijk van het apparaat en de Terminal.</span><span class="sxs-lookup"><span data-stu-id="c791a-160">The rendering of the the vertical tab is device and terminal dependent.</span></span>

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

<span data-ttu-id="c791a-161">In de volgende voor beelden ziet u de gerenderde uitvoer van het verticale tabblad in enkele algemene omgevingen.</span><span class="sxs-lookup"><span data-stu-id="c791a-161">The following examples show the rendered output of the vertical tab in some common environments.</span></span>

<span data-ttu-id="c791a-162">De Windows-console Host-toepassing interpreteert ( `` `v `` ) als een speciaal teken zonder extra ruimte toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="c791a-162">The Windows Console host application interprets (`` `v ``) as a special character with no extra spacing added.</span></span>

```Output
There is a vertical tab♂between the words.
```

<span data-ttu-id="c791a-163">In de [Windows-Terminal](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701) wordt het verticale tabteken weer gegeven als een regel terugloop en een regelinvoerteken.</span><span class="sxs-lookup"><span data-stu-id="c791a-163">The [Windows Terminal](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701) renders the vertical tab character as a carriage return and line feed.</span></span> <span data-ttu-id="c791a-164">De rest van de uitvoer wordt afgedrukt aan het begin van de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="c791a-164">The rest of the output is printed at the beginning of the next line.</span></span>

```Output
There is a vertical tab
between the words.
```

<span data-ttu-id="c791a-165">Op printers of in een UNIX-console kunt u met het verticale tabteken naar de volgende regel gaan en de resterende uitvoer op dat punt schrijven.</span><span class="sxs-lookup"><span data-stu-id="c791a-165">On printers or in a unix-based consoles, the vertical tab character advances to the next line and writes the remaining output at that point.</span></span>

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a><span data-ttu-id="c791a-166">Token voor stoppen en parseren (--%)</span><span class="sxs-lookup"><span data-stu-id="c791a-166">Stop-parsing token (--%)</span></span>

<span data-ttu-id="c791a-167">Het token voor het stoppen van parseren ( `--%` ) voor komt dat Power shell teken reeksen interpreteert als Power shell-opdrachten en-expressies.</span><span class="sxs-lookup"><span data-stu-id="c791a-167">The stop-parsing (`--%`) token prevents PowerShell from interpreting strings as PowerShell commands and expressions.</span></span> <span data-ttu-id="c791a-168">Hierdoor kunnen die teken reeksen worden door gegeven aan andere Program ma's voor interpretatie.</span><span class="sxs-lookup"><span data-stu-id="c791a-168">This allows those strings to be passed to other programs for interpretation.</span></span>

<span data-ttu-id="c791a-169">Plaats het token voor het stoppen van het parseren na de programma naam en vóór programma argumenten die fouten kunnen veroorzaken.</span><span class="sxs-lookup"><span data-stu-id="c791a-169">Place the stop-parsing token after the program name and before program arguments that might cause errors.</span></span>

<span data-ttu-id="c791a-170">In dit voor beeld `Icacls` maakt de opdracht gebruik van het token voor stoppen-parseren.</span><span class="sxs-lookup"><span data-stu-id="c791a-170">In this example, the `Icacls` command uses the stop-parsing token.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="c791a-171">Power shell verzendt de volgende teken reeks naar `Icacls` .</span><span class="sxs-lookup"><span data-stu-id="c791a-171">PowerShell sends the following string to `Icacls`.</span></span>

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="c791a-172">Hier volgt nog een voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="c791a-172">Here is another example.</span></span> <span data-ttu-id="c791a-173">De functie **showArgs** voert de waarden uit die zijn door gegeven.</span><span class="sxs-lookup"><span data-stu-id="c791a-173">The **showArgs** function outputs the values passed to it.</span></span> <span data-ttu-id="c791a-174">In dit voor beeld geven we de variabele `$HOME` met de naam naar de functie twee keer door.</span><span class="sxs-lookup"><span data-stu-id="c791a-174">In this example, we pass the variable named `$HOME` to the function twice.</span></span>

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

U kunt in de uitvoer zien dat de variabele voor de eerste para meter `$HOME` wordt geïnterpreteerd door Power shell, zodat de waarde van de variabele wordt door gegeven aan de functie. <span data-ttu-id="c791a-176">Het tweede gebruik van `$HOME` is na het token voor het stoppen van parseren, zodat de teken reeks "$Home" wordt door gegeven aan de functie zonder interpretatie.</span><span class="sxs-lookup"><span data-stu-id="c791a-176">The second use of `$HOME` comes after the stop-parsing token, so the string "$HOME" is passed to the function without interpretation.</span></span>

```Output
$args = C:\Users\username|--%|$HOME
```

<span data-ttu-id="c791a-177">Zie [about_Parsing](about_Parsing.md)voor meer informatie over het stop-parseren token.</span><span class="sxs-lookup"><span data-stu-id="c791a-177">For more information about the stop-parsing token, see [about_Parsing](about_Parsing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c791a-178">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c791a-178">See also</span></span>

[<span data-ttu-id="c791a-179">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="c791a-179">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
