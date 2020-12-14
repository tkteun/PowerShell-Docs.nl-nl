---
description: Hierin worden de regels voor het gebruik van enkele en dubbele aanhalings tekens in Power shell beschreven.
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: fcb4bff0ca27ad0bc4e3b4c74e58e9fefa8cac7b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705794"
---
# <a name="about-quoting-rules"></a><span data-ttu-id="ee4a4-103">Over quot-regels</span><span class="sxs-lookup"><span data-stu-id="ee4a4-103">About Quoting Rules</span></span>

## <a name="short-description"></a><span data-ttu-id="ee4a4-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ee4a4-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ee4a4-105">Hierin worden de regels voor het gebruik van enkele en dubbele aanhalings tekens in Power shell beschreven.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-105">Describes rules for using single and double quotation marks in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="ee4a4-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ee4a4-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="ee4a4-107">Aanhalings tekens worden gebruikt om een letterlijke teken reeks op te geven.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-107">Quotation marks are used to specify a literal string.</span></span> <span data-ttu-id="ee4a4-108">U kunt een teken reeks tussen enkele aanhalings tekens ( `'` ) of tussen dubbele aanhalings tekens plaatsen ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="ee4a4-108">You can enclose a string in single quotation marks (`'`) or double quotation marks (`"`).</span></span>

<span data-ttu-id="ee4a4-109">Aanhalings tekens worden ook gebruikt voor het maken van een hier-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-109">Quotation marks are also used to create a here-string.</span></span> <span data-ttu-id="ee4a4-110">Een hier-teken reeks is een teken reeks met enkele aanhalings tekens of dubbele aanhalings tekens waarin de aanhaling markeringen letterlijk worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-110">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="ee4a4-111">Een hier-teken reeks kan meerdere regels omvatten.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-111">A here-string can span multiple lines.</span></span> <span data-ttu-id="ee4a4-112">Alle regels in een hier-teken reeks worden geïnterpreteerd als teken reeksen, zelfs als ze niet tussen aanhalings tekens staan.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-112">All the lines in a here-string are interpreted as strings, even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="ee4a4-113">In opdrachten voor externe computers definiëren de aanhalings tekens de onderdelen van de opdracht die worden uitgevoerd op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-113">In commands to remote computers, quotation marks define the parts of the command that are run on the remote computer.</span></span> <span data-ttu-id="ee4a4-114">In een externe sessie bepaalt u met aanhalings tekens ook of de variabelen in een opdracht eerst worden geïnterpreteerd op de lokale computer of op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-114">In a remote session, quotation marks also determine whether the variables in a command are interpreted first on the local computer or on the remote computer.</span></span>

### <a name="single-and-double-quoted-strings"></a><span data-ttu-id="ee4a4-115">TEKEN REEKSEN MET ENKELE EN DUBBELE AANHALINGS TEKENS</span><span class="sxs-lookup"><span data-stu-id="ee4a4-115">SINGLE AND DOUBLE-QUOTED STRINGS</span></span>

<span data-ttu-id="ee4a4-116">Wanneer u een teken reeks tussen dubbele aanhalings tekens (een teken reeks met dubbele aanhalings tekens) plaatst, worden namen van variabelen die worden voorafgegaan door een dollar teken ( `$` ) vervangen door de waarde van de variabele voordat de teken reeks wordt door gegeven aan de opdracht voor verwerking.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-116">When you enclose a string in double quotation marks (a double-quoted string), variable names that are preceded by a dollar sign (`$`) are replaced with the variable's value before the string is passed to the command for processing.</span></span>

<span data-ttu-id="ee4a4-117">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-117">For example:</span></span>

```powershell
$i = 5
"The value of $i is $i."
```

<span data-ttu-id="ee4a4-118">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-118">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="ee4a4-119">In een teken reeks met dubbele aanhalings tekens worden expressies ook geëvalueerd en wordt het resultaat in de teken reeks ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-119">Also, in a double-quoted string, expressions are evaluated, and the result is inserted in the string.</span></span> <span data-ttu-id="ee4a4-120">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-120">For example:</span></span>

```powershell
"The value of $(2+3) is 5."
```

<span data-ttu-id="ee4a4-121">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-121">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="ee4a4-122">Wanneer u een teken reeks tussen enkele aanhalings tekens plaatst (een teken reeks met één aanhalings tekens), wordt de teken reeks door gegeven aan de opdracht exact zoals u deze typt.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-122">When you enclose a string in single-quotation marks (a single-quoted string), the string is passed to the command exactly as you type it.</span></span> <span data-ttu-id="ee4a4-123">Er wordt geen vervanging uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-123">No substitution is performed.</span></span> <span data-ttu-id="ee4a4-124">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-124">For example:</span></span>

```powershell
$i = 5
'The value of $i is $i.'
```

<span data-ttu-id="ee4a4-125">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-125">The output of this command is:</span></span>

```Output
The value $i is $i.
```

<span data-ttu-id="ee4a4-126">Op dezelfde manier worden expressies in teken reeksen met enkele aanhalings tekens niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-126">Similarly, expressions in single-quoted strings are not evaluated.</span></span> <span data-ttu-id="ee4a4-127">Ze worden geïnterpreteerd als letterlijke waarden.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-127">They are interpreted as literals.</span></span> <span data-ttu-id="ee4a4-128">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-128">For example:</span></span>

```powershell
'The value of $(2+3) is 5.'
```

<span data-ttu-id="ee4a4-129">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-129">The output of this command is:</span></span>

```Output
The value of $(2+3) is 5.
```

<span data-ttu-id="ee4a4-130">Als u wilt voor komen dat een variabele waarde in een teken reeks met dubbele aanhalings tekens wordt vervangen, gebruikt u het teken () apostroffen ( `` ` `` ) (ASCII 96). Dit is het Power shell-escape-teken.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-130">To prevent the substitution of a variable value in a double-quoted string, use the backtick character (`` ` ``)(ASCII 96), which is the PowerShell escape character.</span></span>

<span data-ttu-id="ee4a4-131">In het volgende voor beeld wordt het apostroffen-teken dat voorafgaat aan de eerste $i variabele, voor komt dat Power shell de naam van de variabele vervangt door de waarde ervan.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-131">In the following example, the backtick character that precedes the first $i variable prevents PowerShell from replacing the variable name with its value.</span></span>
<span data-ttu-id="ee4a4-132">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-132">For example:</span></span>

```powershell
$i = 5
"The value of `$i is $i."
```

<span data-ttu-id="ee4a4-133">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-133">The output of this command is:</span></span>

```Output
The value $i is 5.
```

<span data-ttu-id="ee4a4-134">Als u dubbele aanhalings tekens in een teken reeks wilt weer geven, plaatst u de hele teken reeks tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-134">To make double-quotation marks appear in a string, enclose the entire string in single quotation marks.</span></span> <span data-ttu-id="ee4a4-135">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-135">For example:</span></span>

```powershell
'As they say, "live and learn."'
```

<span data-ttu-id="ee4a4-136">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-136">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="ee4a4-137">U kunt ook een teken reeks met enkele aanhalings tekens insluiten in een teken reeks met dubbele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-137">You can also enclose a single-quoted string in a double-quoted string.</span></span> <span data-ttu-id="ee4a4-138">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-138">For example:</span></span>

```powershell
"As they say, 'live and learn.'"
```

<span data-ttu-id="ee4a4-139">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-139">The output of this command is:</span></span>

```Output
As they say, 'live and learn.'
```

<span data-ttu-id="ee4a4-140">U kunt ook dubbele aanhalings tekens plaatsen rond een tekst met dubbele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-140">Or, double the quotation marks around a double-quoted phrase.</span></span> <span data-ttu-id="ee4a4-141">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-141">For example:</span></span>

```powershell
"As they say, ""live and learn."""
```

<span data-ttu-id="ee4a4-142">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-142">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="ee4a4-143">Als u één aanhalings teken wilt gebruiken in een teken reeks met één waarde, gebruikt u een tweede opeenvolgende enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-143">To include a single quotation mark in a single-quoted string, use a second consecutive single quote.</span></span> <span data-ttu-id="ee4a4-144">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-144">For example:</span></span>

```powershell
'don''t'
```

<span data-ttu-id="ee4a4-145">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-145">The output of this command is:</span></span>

```Output
don't
```

<span data-ttu-id="ee4a4-146">Als u wilt forceren dat Power shell een dubbele aanhalings tekens letterlijk interpreteert, gebruikt u een apostroffen-teken.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-146">To force PowerShell to interpret a double quotation mark literally, use a backtick character.</span></span> <span data-ttu-id="ee4a4-147">Dit voor komt dat Power shell het aanhalings teken interpreteert als teken reeks scheiding.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-147">This prevents PowerShell from interpreting the quotation mark as a string delimiter.</span></span> <span data-ttu-id="ee4a4-148">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-148">For example:</span></span>

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

<span data-ttu-id="ee4a4-149">Omdat de inhoud van teken reeksen met enkele aanhalings tekens letterlijk wordt geïnterpreteerd, wordt het apostroffen-teken beschouwd als een letterlijke teken en weer gegeven in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-149">Because the contents of single-quoted strings are interpreted literally, you the backtick character is treated as a literal character and displayed in the output.</span></span>

### <a name="here-strings"></a><span data-ttu-id="ee4a4-150">HIER-TEKEN REEKSEN</span><span class="sxs-lookup"><span data-stu-id="ee4a4-150">HERE-STRINGS</span></span>

<span data-ttu-id="ee4a4-151">De offerte regels voor hier-teken reeksen zijn iets anders.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-151">The quotation rules for here-strings are slightly different.</span></span>

<span data-ttu-id="ee4a4-152">Een hier-teken reeks is een teken reeks met enkele aanhalings tekens of dubbele aanhalings tekens waarin de aanhaling markeringen letterlijk worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-152">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="ee4a4-153">Een hier-teken reeks kan meerdere regels omvatten.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-153">A here-string can span multiple lines.</span></span> <span data-ttu-id="ee4a4-154">Alle regels in een hier-teken reeks worden geïnterpreteerd als teken reeksen, zelfs als ze niet tussen aanhalings tekens staan.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-154">All the lines in a here-string are interpreted as strings even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="ee4a4-155">Net als bij reguliere teken reeksen worden variabelen vervangen door hun waarden in dubbele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-155">Like regular strings, variables are replaced by their values in double-quoted here-strings.</span></span> <span data-ttu-id="ee4a4-156">In een enkel aanhalings teken, worden variabelen niet vervangen door hun waarden.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-156">In single-quoted here-strings, variables are not replaced by their values.</span></span>

<span data-ttu-id="ee4a4-157">U kunt hier teken reeksen voor elke tekst gebruiken, maar deze zijn vooral handig voor de volgende soorten tekst:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-157">You can use here-strings for any text, but they are particularly useful for the following kinds of text:</span></span>

- <span data-ttu-id="ee4a4-158">Tekst die letterlijke aanhalings tekens bevat</span><span class="sxs-lookup"><span data-stu-id="ee4a4-158">Text that contains literal quotation marks</span></span>
- <span data-ttu-id="ee4a4-159">Meerdere tekst regels, zoals de tekst in een HTML-of XML-bestand</span><span class="sxs-lookup"><span data-stu-id="ee4a4-159">Multiple lines of text, such as the text in an HTML or XML</span></span>
- <span data-ttu-id="ee4a4-160">De Help-tekst voor een script of functie document</span><span class="sxs-lookup"><span data-stu-id="ee4a4-160">The Help text for a script or function document</span></span>

<span data-ttu-id="ee4a4-161">Een hier-teken reeks kan een van de volgende indelingen hebben, waarbij `<Enter>` de nieuwe regel of het verborgen teken van de voor waarde die wordt toegevoegd, wordt weer gegeven wanneer u op de <kbd>Enter</kbd> -toets drukt.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-161">A here-string can have either of the following formats, where `<Enter>` represents the linefeed or newline hidden character that is added when you press the <kbd>ENTER</kbd> key.</span></span>

<span data-ttu-id="ee4a4-162">Dubbele aanhalings tekens:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-162">Double-quotes:</span></span>

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

<span data-ttu-id="ee4a4-163">Enkele aanhalings tekens:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-163">Single-quotes:</span></span>

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

<span data-ttu-id="ee4a4-164">In beide indelingen moet het aanhalings teken sluiten het eerste teken in de regel zijn.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-164">In either format, the closing quotation mark must be the first character in the line.</span></span>

<span data-ttu-id="ee4a4-165">Een hier-teken reeks bevat alle tekst tussen de twee verborgen tekens.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-165">A here-string contains all the text between the two hidden characters.</span></span> <span data-ttu-id="ee4a4-166">In de teken reeks hier worden alle aanhalings tekens letterlijk geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-166">In the here-string, all quotation marks are interpreted literally.</span></span> <span data-ttu-id="ee4a4-167">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-167">For example:</span></span>

```powershell
@"
For help, type "get-help"
"@
```

<span data-ttu-id="ee4a4-168">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-168">The output of this command is:</span></span>

```Output
For help, type "get-help"
```

<span data-ttu-id="ee4a4-169">Het gebruik van een hier-teken reeks kan vereenvoudigen met een teken reeks in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-169">Using a here-string can simplify using a string in a command.</span></span> <span data-ttu-id="ee4a4-170">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-170">For example:</span></span>

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

<span data-ttu-id="ee4a4-171">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-171">The output of this command is:</span></span>

```Output
Use a quotation mark (') to begin a string.
```

<span data-ttu-id="ee4a4-172">In hier worden enkele aanhalings tekens, variabelen worden letterlijk geïnterpreteerd en precies gereproduceerd.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-172">In single-quoted here-strings, variables are interpreted literally and reproduced exactly.</span></span> <span data-ttu-id="ee4a4-173">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-173">For example:</span></span>

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

<span data-ttu-id="ee4a4-174">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-174">The output of this command is:</span></span>

```Output
The $profile variable contains the path
of your PowerShell profile.
```

<span data-ttu-id="ee4a4-175">In dubbele aanhalings tekens, variabelen worden vervangen door hun waarden.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-175">In double-quoted here-strings, variables are replaced by their values.</span></span> <span data-ttu-id="ee4a4-176">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-176">For example:</span></span>

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

<span data-ttu-id="ee4a4-177">De uitvoer van deze opdracht is:</span><span class="sxs-lookup"><span data-stu-id="ee4a4-177">The output of this command is:</span></span>

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

<span data-ttu-id="ee4a4-178">Hier-teken reeksen worden meestal gebruikt om meerdere regels aan een variabele toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-178">Here-strings are typically used to assign multiple lines to a variable.</span></span> <span data-ttu-id="ee4a4-179">Met de volgende teken reeks wordt bijvoorbeeld een pagina met XML toegewezen aan de variabele $page.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-179">For example, the following here-string assigns a page of XML to the $page variable.</span></span>

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

<span data-ttu-id="ee4a4-180">Hier zijn teken reeksen ook een handige indeling voor de invoer van de `ConvertFrom-StringData` cmdlet, die hier teken reeksen converteert naar hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-180">Here-strings are also a convenient format for input to the `ConvertFrom-StringData` cmdlet, which converts here-strings to hash tables.</span></span>
<span data-ttu-id="ee4a4-181">Voor meer informatie raadpleegt u `ConvertFrom-StringData`.</span><span class="sxs-lookup"><span data-stu-id="ee4a4-181">For more information, see `ConvertFrom-StringData`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee4a4-182">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="ee4a4-182">SEE ALSO</span></span>

[<span data-ttu-id="ee4a4-183">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="ee4a4-183">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="ee4a4-184">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="ee4a4-184">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
