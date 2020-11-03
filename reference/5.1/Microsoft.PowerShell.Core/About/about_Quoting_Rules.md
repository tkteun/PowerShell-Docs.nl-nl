---
description: Hierin worden de regels voor het gebruik van enkele en dubbele aanhalings tekens in Power shell beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: 3a858039a9128235d1b920223ca0fcc3d0b0f6c0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252584"
---
# <a name="about-quoting-rules"></a><span data-ttu-id="a491c-104">Over quot-regels</span><span class="sxs-lookup"><span data-stu-id="a491c-104">About Quoting Rules</span></span>

## <a name="short-description"></a><span data-ttu-id="a491c-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a491c-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a491c-106">Hierin worden de regels voor het gebruik van enkele en dubbele aanhalings tekens in Power shell beschreven.</span><span class="sxs-lookup"><span data-stu-id="a491c-106">Describes rules for using single and double quotation marks in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="a491c-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a491c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a491c-108">Aanhalings tekens worden gebruikt om een letterlijke teken reeks op te geven.</span><span class="sxs-lookup"><span data-stu-id="a491c-108">Quotation marks are used to specify a literal string.</span></span> <span data-ttu-id="a491c-109">U kunt een teken reeks tussen enkele aanhalings tekens ( `'` ) of tussen dubbele aanhalings tekens plaatsen ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="a491c-109">You can enclose a string in single quotation marks (`'`) or double quotation marks (`"`).</span></span>

<span data-ttu-id="a491c-110">Aanhalings tekens worden ook gebruikt voor het maken van een hier-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="a491c-110">Quotation marks are also used to create a here-string.</span></span> <span data-ttu-id="a491c-111">Een hier-teken reeks is een teken reeks met enkele aanhalings tekens of dubbele aanhalings tekens waarin de aanhaling markeringen letterlijk worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="a491c-111">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="a491c-112">Een hier-teken reeks kan meerdere regels omvatten.</span><span class="sxs-lookup"><span data-stu-id="a491c-112">A here-string can span multiple lines.</span></span> <span data-ttu-id="a491c-113">Alle regels in een hier-teken reeks worden geïnterpreteerd als teken reeksen, zelfs als ze niet tussen aanhalings tekens staan.</span><span class="sxs-lookup"><span data-stu-id="a491c-113">All the lines in a here-string are interpreted as strings, even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="a491c-114">In opdrachten voor externe computers definiëren de aanhalings tekens de onderdelen van de opdracht die worden uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="a491c-114">In commands to remote computers, quotation marks define the parts of the command that are run on the remote computer.</span></span> <span data-ttu-id="a491c-115">In een externe sessie bepaalt u met aanhalings tekens ook of de variabelen in een opdracht eerst worden geïnterpreteerd op de lokale computer of op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="a491c-115">In a remote session, quotation marks also determine whether the variables in a command are interpreted first on the local computer or on the remote computer.</span></span>

### <a name="single-and-double-quoted-strings"></a><span data-ttu-id="a491c-116">TEKEN REEKSEN MET ENKELE EN DUBBELE AANHALINGS TEKENS</span><span class="sxs-lookup"><span data-stu-id="a491c-116">SINGLE AND DOUBLE-QUOTED STRINGS</span></span>

<span data-ttu-id="a491c-117">Wanneer u een teken reeks tussen dubbele aanhalings tekens (een teken reeks met dubbele aanhalings tekens) plaatst, worden namen van variabelen die worden voorafgegaan door een dollar teken ( `$` ) vervangen door de waarde van de variabele voordat de teken reeks wordt door gegeven aan de opdracht voor verwerking.</span><span class="sxs-lookup"><span data-stu-id="a491c-117">When you enclose a string in double quotation marks (a double-quoted string), variable names that are preceded by a dollar sign (`$`) are replaced with the variable's value before the string is passed to the command for processing.</span></span>

<span data-ttu-id="a491c-118">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-118">For example:</span></span>

```powershell
$i = 5
"The value of $i is $i."
```

<span data-ttu-id="a491c-119">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-119">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="a491c-120">In een teken reeks met dubbele aanhalings tekens worden expressies ook geëvalueerd en wordt het resultaat in de teken reeks ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="a491c-120">Also, in a double-quoted string, expressions are evaluated, and the result is inserted in the string.</span></span> <span data-ttu-id="a491c-121">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-121">For example:</span></span>

```powershell
"The value of $(2+3) is 5."
```

<span data-ttu-id="a491c-122">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-122">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="a491c-123">Wanneer u een teken reeks tussen enkele aanhalings tekens plaatst (een teken reeks met één aanhalings tekens), wordt de teken reeks door gegeven aan de opdracht exact zoals u deze typt.</span><span class="sxs-lookup"><span data-stu-id="a491c-123">When you enclose a string in single-quotation marks (a single-quoted string), the string is passed to the command exactly as you type it.</span></span> <span data-ttu-id="a491c-124">Er wordt geen vervanging uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a491c-124">No substitution is performed.</span></span> <span data-ttu-id="a491c-125">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-125">For example:</span></span>

```powershell
$i = 5
'The value of $i is $i.'
```

<span data-ttu-id="a491c-126">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-126">The output of this command is:</span></span>

```Output
The value $i is $i.
```

<span data-ttu-id="a491c-127">Op dezelfde manier worden expressies in teken reeksen met enkele aanhalings tekens niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="a491c-127">Similarly, expressions in single-quoted strings are not evaluated.</span></span> <span data-ttu-id="a491c-128">Ze worden geïnterpreteerd als letterlijke waarden.</span><span class="sxs-lookup"><span data-stu-id="a491c-128">They are interpreted as literals.</span></span> <span data-ttu-id="a491c-129">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-129">For example:</span></span>

```powershell
'The value of $(2+3) is 5.'
```

<span data-ttu-id="a491c-130">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-130">The output of this command is:</span></span>

```Output
The value of $(2+3) is 5.
```

<span data-ttu-id="a491c-131">Als u wilt voor komen dat een variabele waarde in een teken reeks met dubbele aanhalings tekens wordt vervangen, gebruikt u het teken () apostroffen ( `` ` `` ) (ASCII 96). Dit is het Power shell-escape-teken.</span><span class="sxs-lookup"><span data-stu-id="a491c-131">To prevent the substitution of a variable value in a double-quoted string, use the backtick character (`` ` ``)(ASCII 96), which is the PowerShell escape character.</span></span>

<span data-ttu-id="a491c-132">In het volgende voor beeld wordt het apostroffen-teken dat voorafgaat aan de eerste $i variabele, voor komt dat Power shell de naam van de variabele vervangt door de waarde ervan.</span><span class="sxs-lookup"><span data-stu-id="a491c-132">In the following example, the backtick character that precedes the first $i variable prevents PowerShell from replacing the variable name with its value.</span></span>
<span data-ttu-id="a491c-133">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-133">For example:</span></span>

```powershell
$i = 5
"The value of `$i is $i."
```

<span data-ttu-id="a491c-134">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-134">The output of this command is:</span></span>

```Output
The value $i is 5.
```

<span data-ttu-id="a491c-135">Als u dubbele aanhalings tekens in een teken reeks wilt weer geven, plaatst u de hele teken reeks tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="a491c-135">To make double-quotation marks appear in a string, enclose the entire string in single quotation marks.</span></span> <span data-ttu-id="a491c-136">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-136">For example:</span></span>

```powershell
'As they say, "live and learn."'
```

<span data-ttu-id="a491c-137">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-137">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="a491c-138">U kunt ook een teken reeks met enkele aanhalings tekens insluiten in een teken reeks met dubbele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="a491c-138">You can also enclose a single-quoted string in a double-quoted string.</span></span> <span data-ttu-id="a491c-139">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-139">For example:</span></span>

```powershell
"As they say, 'live and learn.'"
```

<span data-ttu-id="a491c-140">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-140">The output of this command is:</span></span>

```Output
As they say, 'live and learn.'
```

<span data-ttu-id="a491c-141">U kunt ook dubbele aanhalings tekens plaatsen rond een tekst met dubbele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="a491c-141">Or, double the quotation marks around a double-quoted phrase.</span></span> <span data-ttu-id="a491c-142">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-142">For example:</span></span>

```powershell
"As they say, ""live and learn."""
```

<span data-ttu-id="a491c-143">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-143">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="a491c-144">Als u één aanhalings teken wilt gebruiken in een teken reeks met één waarde, gebruikt u een tweede opeenvolgende enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="a491c-144">To include a single quotation mark in a single-quoted string, use a second consecutive single quote.</span></span> <span data-ttu-id="a491c-145">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-145">For example:</span></span>

```powershell
'don''t'
```

<span data-ttu-id="a491c-146">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-146">The output of this command is:</span></span>

```Output
don't
```

<span data-ttu-id="a491c-147">Als u wilt forceren dat Power shell een dubbele aanhalings tekens letterlijk interpreteert, gebruikt u een apostroffen-teken.</span><span class="sxs-lookup"><span data-stu-id="a491c-147">To force PowerShell to interpret a double quotation mark literally, use a backtick character.</span></span> <span data-ttu-id="a491c-148">Dit voor komt dat Power shell het aanhalings teken interpreteert als teken reeks scheiding.</span><span class="sxs-lookup"><span data-stu-id="a491c-148">This prevents PowerShell from interpreting the quotation mark as a string delimiter.</span></span> <span data-ttu-id="a491c-149">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-149">For example:</span></span>

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

<span data-ttu-id="a491c-150">Omdat de inhoud van teken reeksen met enkele aanhalings tekens letterlijk wordt geïnterpreteerd, wordt het apostroffen-teken beschouwd als een letterlijke teken en weer gegeven in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a491c-150">Because the contents of single-quoted strings are interpreted literally, you the backtick character is treated as a literal character and displayed in the output.</span></span>

### <a name="here-strings"></a><span data-ttu-id="a491c-151">HIER-TEKEN REEKSEN</span><span class="sxs-lookup"><span data-stu-id="a491c-151">HERE-STRINGS</span></span>

<span data-ttu-id="a491c-152">De offerte regels voor hier-teken reeksen zijn iets anders.</span><span class="sxs-lookup"><span data-stu-id="a491c-152">The quotation rules for here-strings are slightly different.</span></span>

<span data-ttu-id="a491c-153">Een hier-teken reeks is een teken reeks met enkele aanhalings tekens of dubbele aanhalings tekens waarin de aanhaling markeringen letterlijk worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="a491c-153">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="a491c-154">Een hier-teken reeks kan meerdere regels omvatten.</span><span class="sxs-lookup"><span data-stu-id="a491c-154">A here-string can span multiple lines.</span></span> <span data-ttu-id="a491c-155">Alle regels in een hier-teken reeks worden geïnterpreteerd als teken reeksen, zelfs als ze niet tussen aanhalings tekens staan.</span><span class="sxs-lookup"><span data-stu-id="a491c-155">All the lines in a here-string are interpreted as strings even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="a491c-156">Net als bij reguliere teken reeksen worden variabelen vervangen door hun waarden in dubbele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="a491c-156">Like regular strings, variables are replaced by their values in double-quoted here-strings.</span></span> <span data-ttu-id="a491c-157">In een enkel aanhalings teken, worden variabelen niet vervangen door hun waarden.</span><span class="sxs-lookup"><span data-stu-id="a491c-157">In single-quoted here-strings, variables are not replaced by their values.</span></span>

<span data-ttu-id="a491c-158">U kunt hier teken reeksen voor elke tekst gebruiken, maar deze zijn vooral handig voor de volgende soorten tekst:</span><span class="sxs-lookup"><span data-stu-id="a491c-158">You can use here-strings for any text, but they are particularly useful for the following kinds of text:</span></span>

- <span data-ttu-id="a491c-159">Tekst die letterlijke aanhalings tekens bevat</span><span class="sxs-lookup"><span data-stu-id="a491c-159">Text that contains literal quotation marks</span></span>
- <span data-ttu-id="a491c-160">Meerdere tekst regels, zoals de tekst in een HTML-of XML-bestand</span><span class="sxs-lookup"><span data-stu-id="a491c-160">Multiple lines of text, such as the text in an HTML or XML</span></span>
- <span data-ttu-id="a491c-161">De Help-tekst voor een script of functie document</span><span class="sxs-lookup"><span data-stu-id="a491c-161">The Help text for a script or function document</span></span>

<span data-ttu-id="a491c-162">Een hier-teken reeks kan een van de volgende indelingen hebben, waarbij `<Enter>` de nieuwe regel of het verborgen teken van de voor waarde die wordt toegevoegd, wordt weer gegeven wanneer u op de <kbd>Enter</kbd> -toets drukt.</span><span class="sxs-lookup"><span data-stu-id="a491c-162">A here-string can have either of the following formats, where `<Enter>` represents the linefeed or newline hidden character that is added when you press the <kbd>ENTER</kbd> key.</span></span>

<span data-ttu-id="a491c-163">Dubbele aanhalings tekens:</span><span class="sxs-lookup"><span data-stu-id="a491c-163">Double-quotes:</span></span>

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

<span data-ttu-id="a491c-164">Enkele aanhalings tekens:</span><span class="sxs-lookup"><span data-stu-id="a491c-164">Single-quotes:</span></span>

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

<span data-ttu-id="a491c-165">In beide indelingen moet het aanhalings teken sluiten het eerste teken in de regel zijn.</span><span class="sxs-lookup"><span data-stu-id="a491c-165">In either format, the closing quotation mark must be the first character in the line.</span></span>

<span data-ttu-id="a491c-166">Een hier-teken reeks bevat alle tekst tussen de twee verborgen tekens.</span><span class="sxs-lookup"><span data-stu-id="a491c-166">A here-string contains all the text between the two hidden characters.</span></span> <span data-ttu-id="a491c-167">In de teken reeks hier worden alle aanhalings tekens letterlijk geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="a491c-167">In the here-string, all quotation marks are interpreted literally.</span></span> <span data-ttu-id="a491c-168">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-168">For example:</span></span>

```powershell
@"
For help, type "get-help"
"@
```

<span data-ttu-id="a491c-169">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-169">The output of this command is:</span></span>

```Output
For help, type "get-help"
```

<span data-ttu-id="a491c-170">Het gebruik van een hier-teken reeks kan vereenvoudigen met een teken reeks in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="a491c-170">Using a here-string can simplify using a string in a command.</span></span> <span data-ttu-id="a491c-171">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-171">For example:</span></span>

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

<span data-ttu-id="a491c-172">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-172">The output of this command is:</span></span>

```Output
Use a quotation mark (') to begin a string.
```

<span data-ttu-id="a491c-173">In hier worden enkele aanhalings tekens, variabelen worden letterlijk geïnterpreteerd en precies gereproduceerd.</span><span class="sxs-lookup"><span data-stu-id="a491c-173">In single-quoted here-strings, variables are interpreted literally and reproduced exactly.</span></span> <span data-ttu-id="a491c-174">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-174">For example:</span></span>

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

<span data-ttu-id="a491c-175">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-175">The output of this command is:</span></span>

```Output
The $profile variable contains the path
of your PowerShell profile.
```

<span data-ttu-id="a491c-176">In dubbele aanhalings tekens, variabelen worden vervangen door hun waarden.</span><span class="sxs-lookup"><span data-stu-id="a491c-176">In double-quoted here-strings, variables are replaced by their values.</span></span> <span data-ttu-id="a491c-177">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a491c-177">For example:</span></span>

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

<span data-ttu-id="a491c-178">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="a491c-178">The output of this command is:</span></span>

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

<span data-ttu-id="a491c-179">Hier-teken reeksen worden meestal gebruikt om meerdere regels aan een variabele toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="a491c-179">Here-strings are typically used to assign multiple lines to a variable.</span></span> <span data-ttu-id="a491c-180">Met de volgende teken reeks wordt bijvoorbeeld een pagina met XML toegewezen aan de variabele $page.</span><span class="sxs-lookup"><span data-stu-id="a491c-180">For example, the following here-string assigns a page of XML to the $page variable.</span></span>

```powershell
$page = [XML] @"
<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
<command:details>
        <command:name>
               Format-Table
        </command:name>
        <maml:description>
            <maml:para>Formats the output as a table.</maml:para>
        </maml:description>
        <command:verb>format</command:verb>
        <command:noun>table</command:noun>
        <dev:version></dev:version>
</command:details>
...
</command:command>
"@
```

<span data-ttu-id="a491c-181">Hier zijn teken reeksen ook een handige indeling voor de invoer van de `ConvertFrom-StringData` cmdlet, die hier teken reeksen converteert naar hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="a491c-181">Here-strings are also a convenient format for input to the `ConvertFrom-StringData` cmdlet, which converts here-strings to hash tables.</span></span>
<span data-ttu-id="a491c-182">Voor meer informatie raadpleegt u `ConvertFrom-StringData`.</span><span class="sxs-lookup"><span data-stu-id="a491c-182">For more information, see `ConvertFrom-StringData`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a491c-183">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="a491c-183">SEE ALSO</span></span>

[<span data-ttu-id="a491c-184">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="a491c-184">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="a491c-185">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="a491c-185">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
