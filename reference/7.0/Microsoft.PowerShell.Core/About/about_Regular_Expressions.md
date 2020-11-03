---
description: Hierin worden reguliere expressies in Power shell beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: d4a01d183290f31202471a221b24859d556e7e3d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252171"
---
# <a name="about-regular-expressions"></a><span data-ttu-id="86a45-104">Over reguliere expressies</span><span class="sxs-lookup"><span data-stu-id="86a45-104">About Regular Expressions</span></span>

## <a name="short-description"></a><span data-ttu-id="86a45-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="86a45-105">Short description</span></span>
<span data-ttu-id="86a45-106">Hierin worden reguliere expressies in Power shell beschreven.</span><span class="sxs-lookup"><span data-stu-id="86a45-106">Describes regular expressions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="86a45-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="86a45-107">Long description</span></span>

> [!NOTE]
> <span data-ttu-id="86a45-108">In dit artikel ziet u de syntaxis en methoden voor het gebruik van reguliere expressies in Power shell. niet alle syntaxis wordt besproken.</span><span class="sxs-lookup"><span data-stu-id="86a45-108">This article will show you the syntax and methods for using regular expressions in PowerShell, not all syntax is discussed.</span></span> <span data-ttu-id="86a45-109">Zie voor een uitgebreidere referentie de [reguliere expressie taal-Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span><span class="sxs-lookup"><span data-stu-id="86a45-109">For a more complete reference, see the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

<span data-ttu-id="86a45-110">Een reguliere expressie is een patroon dat wordt gebruikt voor het afstemmen van tekst.</span><span class="sxs-lookup"><span data-stu-id="86a45-110">A regular expression is a pattern used to match text.</span></span> <span data-ttu-id="86a45-111">Het kan bestaan uit letterlijke tekens, Opera tors en andere constructies.</span><span class="sxs-lookup"><span data-stu-id="86a45-111">It can be made up of literal characters, operators, and other constructs.</span></span>

<span data-ttu-id="86a45-112">In dit artikel ziet u de syntaxis van een reguliere expressie in Power shell.</span><span class="sxs-lookup"><span data-stu-id="86a45-112">This article demonstrates regular expression syntax in PowerShell.</span></span> <span data-ttu-id="86a45-113">Power Shell heeft verschillende Opera tors en cmdlets die gebruikmaken van reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="86a45-113">PowerShell has several operators and cmdlets that use regular expressions.</span></span> <span data-ttu-id="86a45-114">U vindt meer informatie over de syntaxis en het gebruik van de onderstaande koppelingen.</span><span class="sxs-lookup"><span data-stu-id="86a45-114">You can read more about their syntax and usage at the links below.</span></span>

- [<span data-ttu-id="86a45-115">Selecteer teken reeks</span><span class="sxs-lookup"><span data-stu-id="86a45-115">Select-String</span></span>](xref:Microsoft.PowerShell.Utility.Select-String)
- [<span data-ttu-id="86a45-116">-overeenkomsten en vervangen Opera tors</span><span class="sxs-lookup"><span data-stu-id="86a45-116">-match and -replace operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="86a45-117">-splitsen</span><span class="sxs-lookup"><span data-stu-id="86a45-117">-split</span></span>](about_Split.md)
- [<span data-ttu-id="86a45-118">switch-instructie met de optie-regex</span><span class="sxs-lookup"><span data-stu-id="86a45-118">switch statement with -regex option</span></span>](about_Switch.md)

<span data-ttu-id="86a45-119">Reguliere Power shell-expressies zijn standaard niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="86a45-119">PowerShell regular expressions are case-insensitive by default.</span></span> <span data-ttu-id="86a45-120">Elke hierboven weer gegeven methode heeft een andere manier om hoofdletter gevoeligheid af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="86a45-120">Each method shown above has a different way to force case sensitivity.</span></span>

|       <span data-ttu-id="86a45-121">Methode</span><span class="sxs-lookup"><span data-stu-id="86a45-121">Method</span></span>       |                      <span data-ttu-id="86a45-122">Hoofdletter gevoeligheid</span><span class="sxs-lookup"><span data-stu-id="86a45-122">Case Sensitivity</span></span>                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | <span data-ttu-id="86a45-123">`-CaseSensitive`switch gebruiken</span><span class="sxs-lookup"><span data-stu-id="86a45-123">use `-CaseSensitive` switch</span></span>                                |
| <span data-ttu-id="86a45-124">`switch` rekeningen</span><span class="sxs-lookup"><span data-stu-id="86a45-124">`switch` statement</span></span> | <span data-ttu-id="86a45-125">Gebruik de `-casesensitive` optie</span><span class="sxs-lookup"><span data-stu-id="86a45-125">use the `-casesensitive` option</span></span>                            |
| <span data-ttu-id="86a45-126">operatoren</span><span class="sxs-lookup"><span data-stu-id="86a45-126">operators</span></span>          | <span data-ttu-id="86a45-127">voor voegsel met **' c '** ( `-cmatch` , `-csplit` of `-creplace` )</span><span class="sxs-lookup"><span data-stu-id="86a45-127">prefix with **'c'** (`-cmatch`, `-csplit`, or `-creplace`)</span></span> |

### <a name="character-literals"></a><span data-ttu-id="86a45-128">Letterlijke tekens</span><span class="sxs-lookup"><span data-stu-id="86a45-128">Character literals</span></span>

<span data-ttu-id="86a45-129">Een reguliere expressie kan een letterlijke teken of een teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="86a45-129">A regular expression can be a literal character or a string.</span></span> <span data-ttu-id="86a45-130">De expressie zorgt ervoor dat de engine overeenkomt met de tekst die precies is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="86a45-130">The expression causes the engine to match the text specified exactly.</span></span>

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a><span data-ttu-id="86a45-131">Teken klassen</span><span class="sxs-lookup"><span data-stu-id="86a45-131">Character classes</span></span>

<span data-ttu-id="86a45-132">Hoewel letterlijke tekens werken als u het exacte patroon kent, kunt u met teken klassen minder specifiek zijn.</span><span class="sxs-lookup"><span data-stu-id="86a45-132">While character literals work if you know the exact pattern, character classes allow you to be less specific.</span></span>

#### <a name="character-groups"></a><span data-ttu-id="86a45-133">Teken groepen</span><span class="sxs-lookup"><span data-stu-id="86a45-133">Character groups</span></span>

<span data-ttu-id="86a45-134">`[character group]` Hiermee kunt u een wille keurig aantal tekens één keer vergelijken, terwijl `[^character group]` alleen de tekens in de groep overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="86a45-134">`[character group]` allows you to match any number of characters one time, while `[^character group]` only matches characters NOT in the group.</span></span>

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

<span data-ttu-id="86a45-135">Als uw lijst met tekens die moeten worden vergeleken, het afbreek streepje ( `-` ) bevat, moet deze aan het begin of einde van de lijst staan om deze te onderscheiden van een teken bereik expressie.</span><span class="sxs-lookup"><span data-stu-id="86a45-135">If your list of characters to match includes the hyphen character (`-`), it must be at the beginning or end of the list to distinguish it from a character range expression.</span></span>

#### <a name="character-ranges"></a><span data-ttu-id="86a45-136">Teken reeksen</span><span class="sxs-lookup"><span data-stu-id="86a45-136">Character ranges</span></span>

<span data-ttu-id="86a45-137">Een patroon kan ook een teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="86a45-137">A pattern can also be a range of characters.</span></span> <span data-ttu-id="86a45-138">De tekens kunnen alfabetisch `[A-Z]` , numeriek `[0-9]` of zelfs op ASCII gebaseerd zijn `[ -~]` (alle afdruk bare tekens).</span><span class="sxs-lookup"><span data-stu-id="86a45-138">The characters can be alphabetic `[A-Z]`, numeric `[0-9]`, or even ASCII-based `[ -~]` (all printable characters).</span></span>

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a><span data-ttu-id="86a45-139">Getallen</span><span class="sxs-lookup"><span data-stu-id="86a45-139">Numbers</span></span>

<span data-ttu-id="86a45-140">De `\d` teken klasse komt overeen met een decimaal getal.</span><span class="sxs-lookup"><span data-stu-id="86a45-140">The `\d` character class will match any decimal digit.</span></span> <span data-ttu-id="86a45-141">Wordt omgekeerd, komt `\D` overeen met een niet-decimaal getal.</span><span class="sxs-lookup"><span data-stu-id="86a45-141">Conversely, `\D` will match any non-decimal digit.</span></span>

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a><span data-ttu-id="86a45-142">Woord tekens</span><span class="sxs-lookup"><span data-stu-id="86a45-142">Word characters</span></span>

<span data-ttu-id="86a45-143">De `\w` teken klasse komt overeen met een wille keurig woord `[a-zA-Z_0-9]` .</span><span class="sxs-lookup"><span data-stu-id="86a45-143">The `\w` character class will match any word character `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="86a45-144">Als u wilt zoeken naar een wille keurig teken dat geen woord is, gebruikt u `\W` .</span><span class="sxs-lookup"><span data-stu-id="86a45-144">To match any non-word character, use `\W`.</span></span>

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a><span data-ttu-id="86a45-145">Jokertekens</span><span class="sxs-lookup"><span data-stu-id="86a45-145">Wildcards</span></span>

<span data-ttu-id="86a45-146">De punt ( `.` ) is een Joker teken in reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="86a45-146">The period (`.`) is a wildcard character in regular expressions.</span></span> <span data-ttu-id="86a45-147">Dit komt overeen met een wille keurig teken behalve een nieuwe regel ( `\n` ).</span><span class="sxs-lookup"><span data-stu-id="86a45-147">It will match any character except a newline (`\n`).</span></span>

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a><span data-ttu-id="86a45-148">Witruimte</span><span class="sxs-lookup"><span data-stu-id="86a45-148">Whitespace</span></span>

<span data-ttu-id="86a45-149">Spatie komt overeen met de `\s` teken klasse.</span><span class="sxs-lookup"><span data-stu-id="86a45-149">Whitespace is matched using the `\s` character class.</span></span> <span data-ttu-id="86a45-150">Een teken dat niet uit witruimte bestaat, wordt met behulp van gebruikt `\S` .</span><span class="sxs-lookup"><span data-stu-id="86a45-150">Any non-whitespace character is matched using `\S`.</span></span> <span data-ttu-id="86a45-151">Er kunnen ook letterlijke spatie tekens `' '` worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="86a45-151">Literal space characters `' '` can also be used.</span></span>

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a><span data-ttu-id="86a45-152">Kwantiteits meters</span><span class="sxs-lookup"><span data-stu-id="86a45-152">Quantifiers</span></span>

<span data-ttu-id="86a45-153">Kwant oren bepalen hoeveel exemplaren van elk element aanwezig moeten zijn in de invoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="86a45-153">Quantifiers control how many instances of each element should be present in the input string.</span></span>

<span data-ttu-id="86a45-154">Hier volgen enkele van de Kwant oren die beschikbaar zijn in Power shell:</span><span class="sxs-lookup"><span data-stu-id="86a45-154">The following are a few of the quantifiers available in PowerShell:</span></span>

| <span data-ttu-id="86a45-155">Kwantiteits meter</span><span class="sxs-lookup"><span data-stu-id="86a45-155">Quantifier</span></span> |                <span data-ttu-id="86a45-156">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="86a45-156">Description</span></span>                |
| ---------- | ----------------------------------------- |
| `*`        | <span data-ttu-id="86a45-157">Nul of meer keer.</span><span class="sxs-lookup"><span data-stu-id="86a45-157">Zero or more times.</span></span>                       |
| `+`        | <span data-ttu-id="86a45-158">Een of meer keren.</span><span class="sxs-lookup"><span data-stu-id="86a45-158">One or more times.</span></span>                        |
| `?`        | <span data-ttu-id="86a45-159">Nul of één keer.</span><span class="sxs-lookup"><span data-stu-id="86a45-159">Zero or one time.</span></span>                         |
| `{n,m}`    | <span data-ttu-id="86a45-160">Minstens `n` , maar niet meer dan een `m` keer.</span><span class="sxs-lookup"><span data-stu-id="86a45-160">At least `n`, but no more than `m` times.</span></span> |

<span data-ttu-id="86a45-161">Het sterretje ( `*` ) komt niet overeen met het vorige element of is meer dan nul.</span><span class="sxs-lookup"><span data-stu-id="86a45-161">The asterisk (`*`) matches the previous element zero or more times.</span></span> <span data-ttu-id="86a45-162">Het resultaat is dat zelfs een invoer teken reeks zonder het element een overeenkomst zou zijn.</span><span class="sxs-lookup"><span data-stu-id="86a45-162">The result is that even an input string without the element would be a match.</span></span>

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

<span data-ttu-id="86a45-163">Het plus teken ( `+` ) komt een of meer keer overeen met het vorige element.</span><span class="sxs-lookup"><span data-stu-id="86a45-163">The plus sign (`+`) matches the previous element one or more times.</span></span>

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

<span data-ttu-id="86a45-164">Het vraag teken `?` komt overeen met het vorige element nul of één keer.</span><span class="sxs-lookup"><span data-stu-id="86a45-164">The question mark `?` matches the previous element zero or one time.</span></span> <span data-ttu-id="86a45-165">Net als bij een sterretje komt `*` het overeen met teken reeksen waar het element niet aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="86a45-165">Like asterisk `*`, it will even match strings where the element is absent.</span></span>

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

<span data-ttu-id="86a45-166">De `{n, m}` kwantor kan verschillende manieren gebruiken om nauw keurige controle over de kwantor toe te staan.</span><span class="sxs-lookup"><span data-stu-id="86a45-166">The `{n, m}` quantifier can be used several different ways to allow granular control over the quantifier.</span></span> <span data-ttu-id="86a45-167">Het tweede element `m` en de komma `,` zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="86a45-167">The second element `m` and the comma `,` are optional.</span></span>

| <span data-ttu-id="86a45-168">Kwantiteits meter</span><span class="sxs-lookup"><span data-stu-id="86a45-168">Quantifier</span></span> |                <span data-ttu-id="86a45-169">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="86a45-169">Description</span></span>                 |
| ---------- | ------------------------------------------ |
| `{n}`      | <span data-ttu-id="86a45-170">EXACT overeenkomen met het `n` aantal keren.</span><span class="sxs-lookup"><span data-stu-id="86a45-170">Match EXACTLY `n` number of times.</span></span>         |
| `{n,}`     | <span data-ttu-id="86a45-171">Ten minste één `n` keer overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="86a45-171">Match at LEAST `n` number of times.</span></span>        |
| `{n,m}`    | <span data-ttu-id="86a45-172">Komt overeen met `n` en `m` aantal keren.</span><span class="sxs-lookup"><span data-stu-id="86a45-172">Match between `n` and `m` number of times.</span></span> |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a><span data-ttu-id="86a45-173">Ankers</span><span class="sxs-lookup"><span data-stu-id="86a45-173">Anchors</span></span>

<span data-ttu-id="86a45-174">Met ankers kunt u ervoor zorgen dat een overeenkomst slaagt of mislukt op basis van de overeenkomst positie binnen de invoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="86a45-174">Anchors allow you to cause a match to succeed or fail based on the matches position within the input string.</span></span>

<span data-ttu-id="86a45-175">De twee veelgebruikte ankers zijn `^` en `$` .</span><span class="sxs-lookup"><span data-stu-id="86a45-175">The two commonly used anchors are `^` and `$`.</span></span> <span data-ttu-id="86a45-176">Het caret `^` komt overeen met het begin van een teken reeks en `$` , die overeenkomt met het einde van een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="86a45-176">The caret `^` matches the start of a string, and `$`, which matches the end of a string.</span></span> <span data-ttu-id="86a45-177">Met de ankers kunt u uw tekst op een specifieke positie afstemmen en ook ongewenste tekens verwijderen.</span><span class="sxs-lookup"><span data-stu-id="86a45-177">The anchors allow you to match your text at a specific position while also discarding unwanted characters.</span></span>

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> <span data-ttu-id="86a45-178">Wanneer u een regex met een `$` anker definieert, moet u de regex insluiten met enkele aanhalings tekens ( `'` ) in plaats van dubbele aanhalings tekens ( `"` ) of de expressie wordt in Power shell uitgebreid als een variabele.</span><span class="sxs-lookup"><span data-stu-id="86a45-178">When defining a regex containing an `$` anchor, be sure to enclose the regex using single quotes (`'`) instead of double quotes (`"`) or PowerShell will expand the expression as a variable.</span></span>

<span data-ttu-id="86a45-179">Wanneer u ankers in Power shell gebruikt, moet u weten wat het verschil is tussen de opties van de **modus singleline** en de reguliere expressie van **meerdere regels** .</span><span class="sxs-lookup"><span data-stu-id="86a45-179">When using anchors in PowerShell, you should understand the difference between **Singleline** and **Multiline** regular expression options.</span></span>

- <span data-ttu-id="86a45-180">**Meerdere** regels: de modus `^` voor meerdere regels en `$` het begin einde van elke regel wordt vergeleken in plaats van het begin en het einde van de invoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="86a45-180">**Multiline** : Multiline mode forces `^` and `$` to match the beginning end of every LINE instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="86a45-181">**Modus singleline** : de modus singleline-modus behandelt de invoer teken reeks als een **modus singleline**.</span><span class="sxs-lookup"><span data-stu-id="86a45-181">**Singleline** : Singleline mode treats the input string as a **SingleLine**.</span></span>
  <span data-ttu-id="86a45-182">Hiermee wordt het `.` teken afgedwongen dat overeenkomt met elk teken (inclusief nieuwe regels), in plaats van elk teken te vergelijken met de nieuwe regel `\n` .</span><span class="sxs-lookup"><span data-stu-id="86a45-182">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>

<span data-ttu-id="86a45-183">Voor meer informatie over deze opties en hoe u deze kunt gebruiken, gaat u naar de [reguliere expressie taal-Naslag informatie](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span><span class="sxs-lookup"><span data-stu-id="86a45-183">To read more about these options and how to use them, visit the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

### <a name="escaping-characters"></a><span data-ttu-id="86a45-184">Escape tekens</span><span class="sxs-lookup"><span data-stu-id="86a45-184">Escaping characters</span></span>

<span data-ttu-id="86a45-185">De back slash ( `\` ) wordt gebruikt om tekens te escapen zodat ze niet worden geparseerd door de reguliere expressie-engine.</span><span class="sxs-lookup"><span data-stu-id="86a45-185">The backslash (`\`) is used to escape characters so they aren't parsed by the regular expression engine.</span></span>

<span data-ttu-id="86a45-186">De volgende tekens zijn gereserveerd: `[]().\^$|?*+{}` .</span><span class="sxs-lookup"><span data-stu-id="86a45-186">The following characters are reserved: `[]().\^$|?*+{}`.</span></span>

<span data-ttu-id="86a45-187">U moet deze tekens in uw patronen opescapeen zodat deze overeenkomen met uw invoer teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="86a45-187">You'll need to escape these characters in your patterns to match them in your input strings.</span></span>

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

<span data-ttu-id="86a45-188">Er is een statische methode van de regex-klasse die tekst voor u kan escapef.</span><span class="sxs-lookup"><span data-stu-id="86a45-188">There\`s a static method of the regex class that can escape text for you.</span></span>

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> <span data-ttu-id="86a45-189">Hiermee worden alle gereserveerde reguliere expressie tekens geescapet, inclusief de bestaande backslashes die in teken klassen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="86a45-189">This escapes all reserved regular expression characters, including existing backslashes used in character classes.</span></span> <span data-ttu-id="86a45-190">Zorg ervoor dat u deze alleen gebruikt in het gedeelte van het patroon dat u wilt escapepen.</span><span class="sxs-lookup"><span data-stu-id="86a45-190">Be sure to only use it on the portion of your pattern that you need to escape.</span></span>

#### <a name="other-character-escapes"></a><span data-ttu-id="86a45-191">Andere teken-Escapes</span><span class="sxs-lookup"><span data-stu-id="86a45-191">Other character escapes</span></span>

<span data-ttu-id="86a45-192">Er zijn ook gereserveerde teken-Escapes die u kunt gebruiken om speciale teken typen te koppelen.</span><span class="sxs-lookup"><span data-stu-id="86a45-192">There are also reserved character escapes that you can use to match special character types.</span></span>

<span data-ttu-id="86a45-193">Hier volgen enkele veelgebruikte escape-tekens:</span><span class="sxs-lookup"><span data-stu-id="86a45-193">The following are a few commonly used character escapes:</span></span>

|<span data-ttu-id="86a45-194">Escape teken</span><span class="sxs-lookup"><span data-stu-id="86a45-194">Character Escape</span></span>  |<span data-ttu-id="86a45-195">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="86a45-195">Description</span></span>  |
|---------|---------|
|`\t`|<span data-ttu-id="86a45-196">Komt overeen met een tabblad</span><span class="sxs-lookup"><span data-stu-id="86a45-196">Matches a tab</span></span>|
|`\n`|<span data-ttu-id="86a45-197">Komt overeen met een nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="86a45-197">Matches a newline</span></span>|
|`\r`|<span data-ttu-id="86a45-198">Komt overeen met een Enter-retour</span><span class="sxs-lookup"><span data-stu-id="86a45-198">Matches a carriage return</span></span>|

### <a name="groups-captures-and-substitutions"></a><span data-ttu-id="86a45-199">Groepen, vastleg ging en vervangingen</span><span class="sxs-lookup"><span data-stu-id="86a45-199">Groups, Captures, and Substitutions</span></span>

<span data-ttu-id="86a45-200">Met groeperings constructies wordt een invoer teken reeks gescheiden in subtekenreeksen die kunnen worden vastgelegd of genegeerd.</span><span class="sxs-lookup"><span data-stu-id="86a45-200">Grouping constructs separate an input string into substrings that can be captured or ignored.</span></span> <span data-ttu-id="86a45-201">Gegroepeerde subtekenreeksen worden subexpressies genoemd.</span><span class="sxs-lookup"><span data-stu-id="86a45-201">Grouped substrings are called subexpressions.</span></span> <span data-ttu-id="86a45-202">Standaard worden subexpressies vastgelegd in genummerde groepen, maar u kunt ook namen toewijzen.</span><span class="sxs-lookup"><span data-stu-id="86a45-202">By default subexpressions are captured in numbered groups, though you can assign names to them as well.</span></span>

<span data-ttu-id="86a45-203">Een groeperings constructie is een reguliere expressie tussen haakjes.</span><span class="sxs-lookup"><span data-stu-id="86a45-203">A grouping construct is a regular expression surrounded by parentheses.</span></span> <span data-ttu-id="86a45-204">Alle tekst die overeenkomt met de Inge sloten reguliere expressie wordt vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="86a45-204">Any text matched by the enclosed regular expression is captured.</span></span> <span data-ttu-id="86a45-205">In het volgende voor beeld wordt de invoer tekst in twee opname groepen onderverdeeld.</span><span class="sxs-lookup"><span data-stu-id="86a45-205">The following example will break the input text into two capturing groups.</span></span>

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

<span data-ttu-id="86a45-206">Gebruik de `$Matches` automatische **hashtabel** -variabele om vastgelegde tekst op te halen.</span><span class="sxs-lookup"><span data-stu-id="86a45-206">Use the `$Matches` **Hashtable** automatic variable to retrieve captured text.</span></span>
<span data-ttu-id="86a45-207">De tekst die de volledige overeenkomst vertegenwoordigt, wordt opgeslagen op de sleutel `0` .</span><span class="sxs-lookup"><span data-stu-id="86a45-207">The text representing the entire match is stored at key `0`.</span></span>

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

<span data-ttu-id="86a45-208">Vastleg ging worden opgeslagen in numerieke sleutels met **gehele getallen** die van links naar rechts worden verhoogd.</span><span class="sxs-lookup"><span data-stu-id="86a45-208">Captures are stored in numeric **Integer** keys that increase from left to right.</span></span> <span data-ttu-id="86a45-209">Capture `1` bevat alle tekst totdat de gebruikers naam, Capture `2` bevat alleen de gebruikers naam.</span><span class="sxs-lookup"><span data-stu-id="86a45-209">Capture `1` contains all the text until the username, capture `2` contains just the username.</span></span>

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
2                              CONTOSO\jsmith
1                              The last logged on user was
0                              The last logged on user was CONTOSO\jsmith
```

> [!IMPORTANT]
> <span data-ttu-id="86a45-210">De `0` sleutel is een **geheel getal**.</span><span class="sxs-lookup"><span data-stu-id="86a45-210">The `0` key is an **Integer**.</span></span> <span data-ttu-id="86a45-211">U kunt elke **hash** -methode gebruiken om toegang te krijgen tot de opgeslagen waarde.</span><span class="sxs-lookup"><span data-stu-id="86a45-211">You can use any **Hashtable** method to access the value stored.</span></span>
>
> ```
> PS> 'Good Dog' -match 'Dog'
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

#### <a name="named-captures"></a><span data-ttu-id="86a45-212">Benoemde opnamen</span><span class="sxs-lookup"><span data-stu-id="86a45-212">Named Captures</span></span>

<span data-ttu-id="86a45-213">Standaard worden opnamen opgeslagen in oplopende numerieke volg orde, van links naar rechts.</span><span class="sxs-lookup"><span data-stu-id="86a45-213">By default, captures are stored in ascending numeric order, from left to right.</span></span>
<span data-ttu-id="86a45-214">U kunt ook een **naam** toewijzen aan een opname groep.</span><span class="sxs-lookup"><span data-stu-id="86a45-214">You can also assign a **name** to a capturing group.</span></span> <span data-ttu-id="86a45-215">Deze **naam** wordt een sleutel voor de `$Matches` Automatische variabele **hashtabel** .</span><span class="sxs-lookup"><span data-stu-id="86a45-215">This **name** becomes a key on the `$Matches` **Hashtable** automatic variable.</span></span>

<span data-ttu-id="86a45-216">In een opname groep gebruikt `?<keyname>` u om opgenomen gegevens onder een benoemde sleutel op te slaan.</span><span class="sxs-lookup"><span data-stu-id="86a45-216">Inside a capturing group, use `?<keyname>` to store captured data under a named key.</span></span>

```
PS> $string = 'The last logged on user was CONTOSO\jsmith'
PS> $string -match 'was (?<domain>.+)\\(?<user>.+)'
True

PS> $Matches

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

PS> $Matches.domain
CONTOSO

PS> $Matches.user
jsmith
```

<span data-ttu-id="86a45-217">In het volgende voor beeld wordt de meest recente logboek vermelding opgeslagen in het Windows-beveiligings logboek.</span><span class="sxs-lookup"><span data-stu-id="86a45-217">The following example stores the newest log entry in the Windows Security Log.</span></span>
<span data-ttu-id="86a45-218">Met de gevoorziete reguliere expressie worden de gebruikers naam en het domein uit het bericht geëxtraheerd en opgeslagen onder de sleutels: **N** voor naam en **D** voor domein.</span><span class="sxs-lookup"><span data-stu-id="86a45-218">The provided regular expression extracts the username and domain from the message and stores them under the keys: **N** for name and **D** for domain.</span></span>

```powershell
$log = (Get-WinEvent -LogName Security -MaxEvents 1).message
$r = '(?s).*Account Name:\s*(?<N>.*).*Account Domain:\s*(?<D>[A-Z,0-9]*)'
$log -match $r
```

```Output
True
```

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
D                              CONTOSO
N                              jsmith
0                              A process has exited....
```

<span data-ttu-id="86a45-219">Zie [Construct groups in reguliere expressies](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="86a45-219">For more information, see [Grouping Constructs in Regular Expressions](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).</span></span>

#### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="86a45-220">Vervangingen in reguliere expressies</span><span class="sxs-lookup"><span data-stu-id="86a45-220">Substitutions in Regular Expressions</span></span>

<span data-ttu-id="86a45-221">Met de reguliere expressies met de `-replace` operator kunt u tekst dynamisch vervangen met behulp van vastgelegde tekst.</span><span class="sxs-lookup"><span data-stu-id="86a45-221">Using the regular expressions with the `-replace` operator allows you to dynamically replace text using captured text.</span></span>

`<input> -replace <original>, <substitute>`

- <span data-ttu-id="86a45-222">`<input>`: De teken reeks die moet worden doorzocht</span><span class="sxs-lookup"><span data-stu-id="86a45-222">`<input>`: The string to be searched</span></span>
- <span data-ttu-id="86a45-223">`<original>`: Een reguliere expressie die wordt gebruikt om de invoer teken reeks te doorzoeken</span><span class="sxs-lookup"><span data-stu-id="86a45-223">`<original>`: A regular expression used to search the input string</span></span>
- <span data-ttu-id="86a45-224">`<substitute>`: Een expressie voor vervanging van een reguliere expressie om overeenkomsten te vervangen die in de invoer teken reeks zijn gevonden.</span><span class="sxs-lookup"><span data-stu-id="86a45-224">`<substitute>`: A regular expression substitution expression to replace matches found in the input string.</span></span>

> [!NOTE]
> <span data-ttu-id="86a45-225">De `<original>` `<substitute>` operanden en zijn onderworpen aan regels van de reguliere-expressie-engine, zoals teken-Escapes.</span><span class="sxs-lookup"><span data-stu-id="86a45-225">The `<original>` and `<substitute>` operands are subject to rules of the regular expression engine such as character escaping.</span></span>

<span data-ttu-id="86a45-226">In de teken reeks kan naar de opname groepen worden verwezen `<substitute>` .</span><span class="sxs-lookup"><span data-stu-id="86a45-226">Capturing groups can be referenced in the `<substitute>` string.</span></span> <span data-ttu-id="86a45-227">De vervanging wordt uitgevoerd met behulp van het `$` teken voor de groeps-id.</span><span class="sxs-lookup"><span data-stu-id="86a45-227">The substitution is done by using the `$` character before the group identifier.</span></span>

<span data-ttu-id="86a45-228">U kunt op twee manieren verwijzen naar het vastleggen van groepen op **nummer** en **naam**.</span><span class="sxs-lookup"><span data-stu-id="86a45-228">Two ways to reference capturing groups are by **Number** and by **Name**.</span></span>

- <span data-ttu-id="86a45-229">Op **nummer** : het vastleggen van groepen wordt van links naar rechts genummerd.</span><span class="sxs-lookup"><span data-stu-id="86a45-229">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="86a45-230">Op **naam** : voor het vastleggen van groepen kan ook naar een naam worden verwezen.</span><span class="sxs-lookup"><span data-stu-id="86a45-230">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

<span data-ttu-id="86a45-231">De `$&` expressie vertegenwoordigt alle overeenkomende tekst.</span><span class="sxs-lookup"><span data-stu-id="86a45-231">The `$&` expression represents all the text matched.</span></span>

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> <span data-ttu-id="86a45-232">Omdat het `$` teken wordt gebruikt in teken reeks uitbreiding, moet u letterlijke teken reeksen gebruiken met vervanging of het teken escapen `$` Wanneer u dubbele aanhalings tekens gebruikt.</span><span class="sxs-lookup"><span data-stu-id="86a45-232">Since the `$` character is used in string expansion, you'll need to use literal strings with substitution, or escape the `$` character when using double quotes.</span></span>
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', '$1 Universe'
> "Hello World" -replace "(\w+) \w+", "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> Hello Universe
> ```
>
> <span data-ttu-id="86a45-233">Als u het `$` als letterlijk teken wilt gebruiken, gebruikt u dit `$$` in plaats van de normale escape-tekens.</span><span class="sxs-lookup"><span data-stu-id="86a45-233">Additionally, if you want to have the `$` as a literal character, use `$$` instead of the normal escape characters.</span></span> <span data-ttu-id="86a45-234">Wanneer u dubbele aanhalings tekens gebruikt, moet u nog steeds alle exemplaren van `$` vervangen om een onjuiste vervanging te voor komen.</span><span class="sxs-lookup"><span data-stu-id="86a45-234">When using double quotes, still escape all instances of `$` to avoid incorrect substitution.</span></span>
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> "5.72" -replace "(.+)", "`$`$`$1"
> ```
>
> ```Output
> $5.72
> $5.72
> ```

<span data-ttu-id="86a45-235">Zie [vervangingen in reguliere expressies](/dotnet/standard/base-types/substitutions-in-regular-expressions)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="86a45-235">For more information, see [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions).</span></span>

## <a name="see-also"></a><span data-ttu-id="86a45-236">Zie ook</span><span class="sxs-lookup"><span data-stu-id="86a45-236">See also</span></span>

[<span data-ttu-id="86a45-237">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="86a45-237">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="86a45-238">about_Operators</span><span class="sxs-lookup"><span data-stu-id="86a45-238">about_Operators</span></span>](about_Operators.md)
