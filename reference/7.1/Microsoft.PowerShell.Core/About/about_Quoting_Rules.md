---
description: Hierin worden de regels voor het gebruik van enkele en dubbele aanhalings tekens in Power shell beschreven.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: d8cc6bb875f6d0ec29ae79eb6350edabe493c8f5
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490540"
---
# <a name="about-quoting-rules"></a><span data-ttu-id="d2d30-103">Over quot-regels</span><span class="sxs-lookup"><span data-stu-id="d2d30-103">About Quoting Rules</span></span>

## <a name="short-description"></a><span data-ttu-id="d2d30-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="d2d30-104">Short description</span></span>
<span data-ttu-id="d2d30-105">Hierin worden de regels voor het gebruik van enkele en dubbele aanhalings tekens in Power shell beschreven.</span><span class="sxs-lookup"><span data-stu-id="d2d30-105">Describes rules for using single and double quotation marks in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="d2d30-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="d2d30-106">Long description</span></span>

<span data-ttu-id="d2d30-107">Aanhalings tekens worden gebruikt om een letterlijke teken reeks op te geven.</span><span class="sxs-lookup"><span data-stu-id="d2d30-107">Quotation marks are used to specify a literal string.</span></span> <span data-ttu-id="d2d30-108">U kunt een teken reeks tussen enkele aanhalings tekens ( `'` ) of tussen dubbele aanhalings tekens plaatsen ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="d2d30-108">You can enclose a string in single quotation marks (`'`) or double quotation marks (`"`).</span></span>

<span data-ttu-id="d2d30-109">Aanhalings tekens worden ook gebruikt voor het maken van een _hier-teken reeks_.</span><span class="sxs-lookup"><span data-stu-id="d2d30-109">Quotation marks are also used to create a _here-string_.</span></span> <span data-ttu-id="d2d30-110">Een hier-teken reeks is een teken reeks met enkele aanhalings tekens of dubbele aanhalings tekens waarin de aanhaling markeringen letterlijk worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="d2d30-110">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="d2d30-111">Een hier-teken reeks kan meerdere regels omvatten.</span><span class="sxs-lookup"><span data-stu-id="d2d30-111">A here-string can span multiple lines.</span></span> <span data-ttu-id="d2d30-112">Alle regels in een hier-teken reeks worden geïnterpreteerd als teken reeksen, zelfs als ze niet tussen aanhalings tekens staan.</span><span class="sxs-lookup"><span data-stu-id="d2d30-112">All the lines in a here-string are interpreted as strings, even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="d2d30-113">In opdrachten voor externe computers definiëren de aanhalings tekens de onderdelen van de opdracht die worden uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="d2d30-113">In commands to remote computers, quotation marks define the parts of the command that are run on the remote computer.</span></span> <span data-ttu-id="d2d30-114">In een externe sessie bepaalt u met aanhalings tekens ook of de variabelen in een opdracht eerst worden geïnterpreteerd op de lokale computer of op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="d2d30-114">In a remote session, quotation marks also determine whether the variables in a command are interpreted first on the local computer or on the remote computer.</span></span>

## <a name="single-and-double-quoted-strings"></a><span data-ttu-id="d2d30-115">Teken reeksen met enkele en dubbele aanhalings tekens</span><span class="sxs-lookup"><span data-stu-id="d2d30-115">Single and double-quoted strings</span></span>

<span data-ttu-id="d2d30-116">Een teken reeks tussen dubbele aanhalings tekens is een _uitbreid bare_ teken reeks.</span><span class="sxs-lookup"><span data-stu-id="d2d30-116">A string enclosed in double quotation marks is an _expandable_ string.</span></span> <span data-ttu-id="d2d30-117">Namen van variabelen die worden voorafgegaan door een dollar teken ( `$` ) worden vervangen door de waarde van de variabele voordat de teken reeks wordt door gegeven aan de opdracht voor verwerking.</span><span class="sxs-lookup"><span data-stu-id="d2d30-117">Variable names preceded by a dollar sign (`$`) are replaced with the variable's value before the string is passed to the command for processing.</span></span>

<span data-ttu-id="d2d30-118">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-118">For example:</span></span>

```powershell
$i = 5
"The value of $i is $i."
```

<span data-ttu-id="d2d30-119">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-119">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="d2d30-120">In een teken reeks met dubbele aanhalings tekens worden expressies ook geëvalueerd en wordt het resultaat in de teken reeks ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="d2d30-120">Also, in a double-quoted string, expressions are evaluated, and the result is inserted in the string.</span></span> <span data-ttu-id="d2d30-121">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-121">For example:</span></span>

```powershell
"The value of $(2+3) is 5."
```

<span data-ttu-id="d2d30-122">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-122">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="d2d30-123">Een teken reeks tussen enkele aanhalings tekens is een _Verbatim_ teken reeks.</span><span class="sxs-lookup"><span data-stu-id="d2d30-123">A string enclosed in single-quotation marks is a _verbatim_ string.</span></span> <span data-ttu-id="d2d30-124">De teken reeks wordt door gegeven aan de opdracht exact zoals u deze typt.</span><span class="sxs-lookup"><span data-stu-id="d2d30-124">The string is passed to the command exactly as you type it.</span></span> <span data-ttu-id="d2d30-125">Er wordt geen vervanging uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d2d30-125">No substitution is performed.</span></span>
<span data-ttu-id="d2d30-126">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-126">For example:</span></span>

```powershell
$i = 5
'The value of $i is $i.'
```

<span data-ttu-id="d2d30-127">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-127">The output of this command is:</span></span>

```Output
The value $i is $i.
```

<span data-ttu-id="d2d30-128">Op dezelfde manier worden expressies in teken reeksen met enkele aanhalings tekens niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="d2d30-128">Similarly, expressions in single-quoted strings are not evaluated.</span></span> <span data-ttu-id="d2d30-129">Ze worden geïnterpreteerd als letterlijke waarden.</span><span class="sxs-lookup"><span data-stu-id="d2d30-129">They are interpreted as literals.</span></span> <span data-ttu-id="d2d30-130">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-130">For example:</span></span>

```powershell
'The value of $(2+3) is 5.'
```

<span data-ttu-id="d2d30-131">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-131">The output of this command is:</span></span>

```Output
The value of $(2+3) is 5.
```

<span data-ttu-id="d2d30-132">Als u wilt voor komen dat een variabele waarde in een teken reeks met dubbele aanhalings tekens wordt vervangen, gebruikt u het teken () apostroffen ( `` ` `` ) (ASCII 96). Dit is het Power shell-escape-teken.</span><span class="sxs-lookup"><span data-stu-id="d2d30-132">To prevent the substitution of a variable value in a double-quoted string, use the backtick character (`` ` ``)(ASCII 96), which is the PowerShell escape character.</span></span>

<span data-ttu-id="d2d30-133">In het volgende voor beeld wordt het apostroffen-teken dat voorafgaat `$i` aan de eerste variabele, voor komt dat Power shell de naam van de variabele vervangt door de waarde ervan.</span><span class="sxs-lookup"><span data-stu-id="d2d30-133">In the following example, the backtick character that precedes the first `$i` variable prevents PowerShell from replacing the variable name with its value.</span></span>
<span data-ttu-id="d2d30-134">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-134">For example:</span></span>

```powershell
$i = 5
"The value of `$i is $i."
```

<span data-ttu-id="d2d30-135">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-135">The output of this command is:</span></span>

```Output
The value $i is 5.
```

<span data-ttu-id="d2d30-136">Als u dubbele aanhalings tekens in een teken reeks wilt weer geven, plaatst u de hele teken reeks tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="d2d30-136">To make double-quotation marks appear in a string, enclose the entire string in single quotation marks.</span></span> <span data-ttu-id="d2d30-137">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-137">For example:</span></span>

```powershell
'As they say, "live and learn."'
```

<span data-ttu-id="d2d30-138">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-138">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="d2d30-139">U kunt ook een teken reeks met enkele aanhalings tekens insluiten in een teken reeks met dubbele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="d2d30-139">You can also enclose a single-quoted string in a double-quoted string.</span></span> <span data-ttu-id="d2d30-140">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-140">For example:</span></span>

```powershell
"As they say, 'live and learn.'"
```

<span data-ttu-id="d2d30-141">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-141">The output of this command is:</span></span>

```Output
As they say, 'live and learn.'
```

<span data-ttu-id="d2d30-142">U kunt ook dubbele aanhalings tekens plaatsen rond een tekst met dubbele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="d2d30-142">Or, double the quotation marks around a double-quoted phrase.</span></span> <span data-ttu-id="d2d30-143">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-143">For example:</span></span>

```powershell
"As they say, ""live and learn."""
```

<span data-ttu-id="d2d30-144">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-144">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="d2d30-145">Als u één aanhalings teken wilt gebruiken in een teken reeks met één waarde, gebruikt u een tweede opeenvolgende enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="d2d30-145">To include a single quotation mark in a single-quoted string, use a second consecutive single quote.</span></span> <span data-ttu-id="d2d30-146">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-146">For example:</span></span>

```powershell
'don''t'
```

<span data-ttu-id="d2d30-147">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-147">The output of this command is:</span></span>

```Output
don't
```

<span data-ttu-id="d2d30-148">Als u wilt forceren dat Power shell een dubbele aanhalings tekens letterlijk interpreteert, gebruikt u een apostroffen-teken.</span><span class="sxs-lookup"><span data-stu-id="d2d30-148">To force PowerShell to interpret a double quotation mark literally, use a backtick character.</span></span> <span data-ttu-id="d2d30-149">Dit voor komt dat Power shell het aanhalings teken interpreteert als teken reeks scheiding.</span><span class="sxs-lookup"><span data-stu-id="d2d30-149">This prevents PowerShell from interpreting the quotation mark as a string delimiter.</span></span> <span data-ttu-id="d2d30-150">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-150">For example:</span></span>

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

<span data-ttu-id="d2d30-151">Omdat de inhoud van teken reeksen met enkele aanhalings tekens letterlijk wordt geïnterpreteerd, wordt het apostroffen-teken beschouwd als een letterlijke teken en weer gegeven in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="d2d30-151">Because the contents of single-quoted strings are interpreted literally, you the backtick character is treated as a literal character and displayed in the output.</span></span>

## <a name="here-strings"></a><span data-ttu-id="d2d30-152">Hier-teken reeksen</span><span class="sxs-lookup"><span data-stu-id="d2d30-152">Here-strings</span></span>

<span data-ttu-id="d2d30-153">De offerte regels voor hier-teken reeksen zijn iets anders.</span><span class="sxs-lookup"><span data-stu-id="d2d30-153">The quotation rules for here-strings are slightly different.</span></span>

<span data-ttu-id="d2d30-154">Een hier-teken reeks is een teken reeks met enkele aanhalings tekens of dubbele aanhalings tekens waarin de aanhaling markeringen letterlijk worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="d2d30-154">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="d2d30-155">Een hier-teken reeks kan meerdere regels omvatten.</span><span class="sxs-lookup"><span data-stu-id="d2d30-155">A here-string can span multiple lines.</span></span> <span data-ttu-id="d2d30-156">Alle regels in een hier-teken reeks worden geïnterpreteerd als teken reeksen, zelfs als ze niet tussen aanhalings tekens staan.</span><span class="sxs-lookup"><span data-stu-id="d2d30-156">All the lines in a here-string are interpreted as strings even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="d2d30-157">Net als bij reguliere teken reeksen worden variabelen vervangen door hun waarden in dubbele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="d2d30-157">Like regular strings, variables are replaced by their values in double-quoted here-strings.</span></span> <span data-ttu-id="d2d30-158">In een enkel aanhalings teken, worden variabelen niet vervangen door hun waarden.</span><span class="sxs-lookup"><span data-stu-id="d2d30-158">In single-quoted here-strings, variables are not replaced by their values.</span></span>

<span data-ttu-id="d2d30-159">U kunt hier teken reeksen voor elke tekst gebruiken, maar deze zijn vooral handig voor de volgende soorten tekst:</span><span class="sxs-lookup"><span data-stu-id="d2d30-159">You can use here-strings for any text, but they are particularly useful for the following kinds of text:</span></span>

- <span data-ttu-id="d2d30-160">Tekst die letterlijke aanhalings tekens bevat</span><span class="sxs-lookup"><span data-stu-id="d2d30-160">Text that contains literal quotation marks</span></span>
- <span data-ttu-id="d2d30-161">Meerdere tekst regels, zoals de tekst in een HTML-of XML-bestand</span><span class="sxs-lookup"><span data-stu-id="d2d30-161">Multiple lines of text, such as the text in an HTML or XML</span></span>
- <span data-ttu-id="d2d30-162">De Help-tekst voor een script of functie document</span><span class="sxs-lookup"><span data-stu-id="d2d30-162">The Help text for a script or function document</span></span>

<span data-ttu-id="d2d30-163">Een hier-teken reeks kan een van de volgende indelingen hebben, waarbij `<Enter>` de nieuwe regel of het verborgen teken van de voor waarde die wordt toegevoegd, wordt weer gegeven wanneer u op de <kbd>Enter</kbd> -toets drukt.</span><span class="sxs-lookup"><span data-stu-id="d2d30-163">A here-string can have either of the following formats, where `<Enter>` represents the linefeed or newline hidden character that is added when you press the <kbd>ENTER</kbd> key.</span></span>

<span data-ttu-id="d2d30-164">Dubbele aanhalings tekens:</span><span class="sxs-lookup"><span data-stu-id="d2d30-164">Double-quotes:</span></span>

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

<span data-ttu-id="d2d30-165">Enkele aanhalings tekens:</span><span class="sxs-lookup"><span data-stu-id="d2d30-165">Single-quotes:</span></span>

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

<span data-ttu-id="d2d30-166">In beide indelingen moet het aanhalings teken sluiten het eerste teken in de regel zijn.</span><span class="sxs-lookup"><span data-stu-id="d2d30-166">In either format, the closing quotation mark must be the first character in the line.</span></span>

<span data-ttu-id="d2d30-167">Een hier-teken reeks bevat alle tekst tussen de twee verborgen tekens.</span><span class="sxs-lookup"><span data-stu-id="d2d30-167">A here-string contains all the text between the two hidden characters.</span></span> <span data-ttu-id="d2d30-168">In de teken reeks hier worden alle aanhalings tekens letterlijk geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="d2d30-168">In the here-string, all quotation marks are interpreted literally.</span></span> <span data-ttu-id="d2d30-169">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-169">For example:</span></span>

```powershell
@"
For help, type "get-help"
"@
```

<span data-ttu-id="d2d30-170">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-170">The output of this command is:</span></span>

```Output
For help, type "get-help"
```

<span data-ttu-id="d2d30-171">Het gebruik van een hier-teken reeks kan vereenvoudigen met een teken reeks in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="d2d30-171">Using a here-string can simplify using a string in a command.</span></span> <span data-ttu-id="d2d30-172">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-172">For example:</span></span>

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

<span data-ttu-id="d2d30-173">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-173">The output of this command is:</span></span>

```Output
Use a quotation mark (') to begin a string.
```

<span data-ttu-id="d2d30-174">In hier worden enkele aanhalings tekens, variabelen worden letterlijk geïnterpreteerd en precies gereproduceerd.</span><span class="sxs-lookup"><span data-stu-id="d2d30-174">In single-quoted here-strings, variables are interpreted literally and reproduced exactly.</span></span> <span data-ttu-id="d2d30-175">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-175">For example:</span></span>

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

<span data-ttu-id="d2d30-176">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-176">The output of this command is:</span></span>

```Output
The $profile variable contains the path
of your PowerShell profile.
```

<span data-ttu-id="d2d30-177">In dubbele aanhalings tekens, variabelen worden vervangen door hun waarden.</span><span class="sxs-lookup"><span data-stu-id="d2d30-177">In double-quoted here-strings, variables are replaced by their values.</span></span> <span data-ttu-id="d2d30-178">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2d30-178">For example:</span></span>

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

<span data-ttu-id="d2d30-179">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="d2d30-179">The output of this command is:</span></span>

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

<span data-ttu-id="d2d30-180">Hier-teken reeksen worden meestal gebruikt om meerdere regels aan een variabele toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="d2d30-180">Here-strings are typically used to assign multiple lines to a variable.</span></span> <span data-ttu-id="d2d30-181">Met de volgende teken reeks wordt bijvoorbeeld een pagina met XML toegewezen aan de variabele $page.</span><span class="sxs-lookup"><span data-stu-id="d2d30-181">For example, the following here-string assigns a page of XML to the $page variable.</span></span>

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

<span data-ttu-id="d2d30-182">Hier zijn teken reeksen ook een handige indeling voor de invoer van de `ConvertFrom-StringData` cmdlet, die hier teken reeksen converteert naar hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="d2d30-182">Here-strings are also a convenient format for input to the `ConvertFrom-StringData` cmdlet, which converts here-strings to hash tables.</span></span>
<span data-ttu-id="d2d30-183">Voor meer informatie raadpleegt u `ConvertFrom-StringData`.</span><span class="sxs-lookup"><span data-stu-id="d2d30-183">For more information, see `ConvertFrom-StringData`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2d30-184">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d2d30-184">See also</span></span>

[<span data-ttu-id="d2d30-185">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="d2d30-185">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="d2d30-186">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="d2d30-186">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
