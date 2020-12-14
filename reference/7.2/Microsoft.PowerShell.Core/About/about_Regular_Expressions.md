---
description: Hierin worden reguliere expressies in Power shell beschreven.
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: 4dc6ac670a31cbea4c35ee6540ce3368ad9b02ca
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705324"
---
# <a name="about-regular-expressions"></a><span data-ttu-id="41a59-103">Over reguliere expressies</span><span class="sxs-lookup"><span data-stu-id="41a59-103">About Regular Expressions</span></span>

## <a name="short-description"></a><span data-ttu-id="41a59-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="41a59-104">Short description</span></span>
<span data-ttu-id="41a59-105">Hierin worden reguliere expressies in Power shell beschreven.</span><span class="sxs-lookup"><span data-stu-id="41a59-105">Describes regular expressions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="41a59-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="41a59-106">Long description</span></span>

> [!NOTE]
> <span data-ttu-id="41a59-107">In dit artikel ziet u de syntaxis en methoden voor het gebruik van reguliere expressies in Power shell. niet alle syntaxis wordt besproken.</span><span class="sxs-lookup"><span data-stu-id="41a59-107">This article will show you the syntax and methods for using regular expressions in PowerShell, not all syntax is discussed.</span></span> <span data-ttu-id="41a59-108">Zie voor een uitgebreidere referentie de [reguliere expressie taal-Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span><span class="sxs-lookup"><span data-stu-id="41a59-108">For a more complete reference, see the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

<span data-ttu-id="41a59-109">Een reguliere expressie is een patroon dat wordt gebruikt voor het afstemmen van tekst.</span><span class="sxs-lookup"><span data-stu-id="41a59-109">A regular expression is a pattern used to match text.</span></span> <span data-ttu-id="41a59-110">Het kan bestaan uit letterlijke tekens, Opera tors en andere constructies.</span><span class="sxs-lookup"><span data-stu-id="41a59-110">It can be made up of literal characters, operators, and other constructs.</span></span>

<span data-ttu-id="41a59-111">In dit artikel ziet u de syntaxis van een reguliere expressie in Power shell.</span><span class="sxs-lookup"><span data-stu-id="41a59-111">This article demonstrates regular expression syntax in PowerShell.</span></span> <span data-ttu-id="41a59-112">Power Shell heeft verschillende Opera tors en cmdlets die gebruikmaken van reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="41a59-112">PowerShell has several operators and cmdlets that use regular expressions.</span></span> <span data-ttu-id="41a59-113">U vindt meer informatie over de syntaxis en het gebruik van de onderstaande koppelingen.</span><span class="sxs-lookup"><span data-stu-id="41a59-113">You can read more about their syntax and usage at the links below.</span></span>

- [<span data-ttu-id="41a59-114">Selecteer teken reeks</span><span class="sxs-lookup"><span data-stu-id="41a59-114">Select-String</span></span>](xref:Microsoft.PowerShell.Utility.Select-String)
- [<span data-ttu-id="41a59-115">-overeenkomsten en vervangen Opera tors</span><span class="sxs-lookup"><span data-stu-id="41a59-115">-match and -replace operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="41a59-116">-splitsen</span><span class="sxs-lookup"><span data-stu-id="41a59-116">-split</span></span>](about_Split.md)
- [<span data-ttu-id="41a59-117">switch-instructie met de optie-regex</span><span class="sxs-lookup"><span data-stu-id="41a59-117">switch statement with -regex option</span></span>](about_Switch.md)

<span data-ttu-id="41a59-118">Reguliere Power shell-expressies zijn standaard niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="41a59-118">PowerShell regular expressions are case-insensitive by default.</span></span> <span data-ttu-id="41a59-119">Elke hierboven weer gegeven methode heeft een andere manier om hoofdletter gevoeligheid af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="41a59-119">Each method shown above has a different way to force case sensitivity.</span></span>

|       <span data-ttu-id="41a59-120">Methode</span><span class="sxs-lookup"><span data-stu-id="41a59-120">Method</span></span>       |                      <span data-ttu-id="41a59-121">Hoofdletter gevoeligheid</span><span class="sxs-lookup"><span data-stu-id="41a59-121">Case Sensitivity</span></span>                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | <span data-ttu-id="41a59-122">`-CaseSensitive`switch gebruiken</span><span class="sxs-lookup"><span data-stu-id="41a59-122">use `-CaseSensitive` switch</span></span>                                |
| <span data-ttu-id="41a59-123">`switch` rekeningen</span><span class="sxs-lookup"><span data-stu-id="41a59-123">`switch` statement</span></span> | <span data-ttu-id="41a59-124">Gebruik de `-casesensitive` optie</span><span class="sxs-lookup"><span data-stu-id="41a59-124">use the `-casesensitive` option</span></span>                            |
| <span data-ttu-id="41a59-125">operatoren</span><span class="sxs-lookup"><span data-stu-id="41a59-125">operators</span></span>          | <span data-ttu-id="41a59-126">voor voegsel met **' c '** ( `-cmatch` , `-csplit` of `-creplace` )</span><span class="sxs-lookup"><span data-stu-id="41a59-126">prefix with **'c'** (`-cmatch`, `-csplit`, or `-creplace`)</span></span> |

### <a name="character-literals"></a><span data-ttu-id="41a59-127">Letterlijke tekens</span><span class="sxs-lookup"><span data-stu-id="41a59-127">Character literals</span></span>

<span data-ttu-id="41a59-128">Een reguliere expressie kan een letterlijke teken of een teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="41a59-128">A regular expression can be a literal character or a string.</span></span> <span data-ttu-id="41a59-129">De expressie zorgt ervoor dat de engine overeenkomt met de tekst die precies is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="41a59-129">The expression causes the engine to match the text specified exactly.</span></span>

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a><span data-ttu-id="41a59-130">Teken klassen</span><span class="sxs-lookup"><span data-stu-id="41a59-130">Character classes</span></span>

<span data-ttu-id="41a59-131">Hoewel letterlijke tekens werken als u het exacte patroon kent, kunt u met teken klassen minder specifiek zijn.</span><span class="sxs-lookup"><span data-stu-id="41a59-131">While character literals work if you know the exact pattern, character classes allow you to be less specific.</span></span>

#### <a name="character-groups"></a><span data-ttu-id="41a59-132">Teken groepen</span><span class="sxs-lookup"><span data-stu-id="41a59-132">Character groups</span></span>

<span data-ttu-id="41a59-133">`[character group]` Hiermee kunt u een wille keurig aantal tekens één keer vergelijken, terwijl `[^character group]` alleen de tekens in de groep overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="41a59-133">`[character group]` allows you to match any number of characters one time, while `[^character group]` only matches characters NOT in the group.</span></span>

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

<span data-ttu-id="41a59-134">Als uw lijst met tekens die moeten worden vergeleken, het afbreek streepje ( `-` ) bevat, moet deze aan het begin of einde van de lijst staan om deze te onderscheiden van een teken bereik expressie.</span><span class="sxs-lookup"><span data-stu-id="41a59-134">If your list of characters to match includes the hyphen character (`-`), it must be at the beginning or end of the list to distinguish it from a character range expression.</span></span>

#### <a name="character-ranges"></a><span data-ttu-id="41a59-135">Teken reeksen</span><span class="sxs-lookup"><span data-stu-id="41a59-135">Character ranges</span></span>

<span data-ttu-id="41a59-136">Een patroon kan ook een teken reeks zijn.</span><span class="sxs-lookup"><span data-stu-id="41a59-136">A pattern can also be a range of characters.</span></span> <span data-ttu-id="41a59-137">De tekens kunnen alfabetisch `[A-Z]` , numeriek `[0-9]` of zelfs op ASCII gebaseerd zijn `[ -~]` (alle afdruk bare tekens).</span><span class="sxs-lookup"><span data-stu-id="41a59-137">The characters can be alphabetic `[A-Z]`, numeric `[0-9]`, or even ASCII-based `[ -~]` (all printable characters).</span></span>

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a><span data-ttu-id="41a59-138">Getallen</span><span class="sxs-lookup"><span data-stu-id="41a59-138">Numbers</span></span>

<span data-ttu-id="41a59-139">De `\d` teken klasse komt overeen met een decimaal getal.</span><span class="sxs-lookup"><span data-stu-id="41a59-139">The `\d` character class will match any decimal digit.</span></span> <span data-ttu-id="41a59-140">Wordt omgekeerd, komt `\D` overeen met een niet-decimaal getal.</span><span class="sxs-lookup"><span data-stu-id="41a59-140">Conversely, `\D` will match any non-decimal digit.</span></span>

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a><span data-ttu-id="41a59-141">Woord tekens</span><span class="sxs-lookup"><span data-stu-id="41a59-141">Word characters</span></span>

<span data-ttu-id="41a59-142">De `\w` teken klasse komt overeen met een wille keurig woord `[a-zA-Z_0-9]` .</span><span class="sxs-lookup"><span data-stu-id="41a59-142">The `\w` character class will match any word character `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="41a59-143">Als u wilt zoeken naar een wille keurig teken dat geen woord is, gebruikt u `\W` .</span><span class="sxs-lookup"><span data-stu-id="41a59-143">To match any non-word character, use `\W`.</span></span>

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a><span data-ttu-id="41a59-144">Jokertekens</span><span class="sxs-lookup"><span data-stu-id="41a59-144">Wildcards</span></span>

<span data-ttu-id="41a59-145">De punt ( `.` ) is een Joker teken in reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="41a59-145">The period (`.`) is a wildcard character in regular expressions.</span></span> <span data-ttu-id="41a59-146">Dit komt overeen met een wille keurig teken behalve een nieuwe regel ( `\n` ).</span><span class="sxs-lookup"><span data-stu-id="41a59-146">It will match any character except a newline (`\n`).</span></span>

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a><span data-ttu-id="41a59-147">Witruimte</span><span class="sxs-lookup"><span data-stu-id="41a59-147">Whitespace</span></span>

<span data-ttu-id="41a59-148">Spatie komt overeen met de `\s` teken klasse.</span><span class="sxs-lookup"><span data-stu-id="41a59-148">Whitespace is matched using the `\s` character class.</span></span> <span data-ttu-id="41a59-149">Een teken dat niet uit witruimte bestaat, wordt met behulp van gebruikt `\S` .</span><span class="sxs-lookup"><span data-stu-id="41a59-149">Any non-whitespace character is matched using `\S`.</span></span> <span data-ttu-id="41a59-150">Er kunnen ook letterlijke spatie tekens `' '` worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="41a59-150">Literal space characters `' '` can also be used.</span></span>

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a><span data-ttu-id="41a59-151">Kwantiteits meters</span><span class="sxs-lookup"><span data-stu-id="41a59-151">Quantifiers</span></span>

<span data-ttu-id="41a59-152">Kwant oren bepalen hoeveel exemplaren van elk element aanwezig moeten zijn in de invoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="41a59-152">Quantifiers control how many instances of each element should be present in the input string.</span></span>

<span data-ttu-id="41a59-153">Hier volgen enkele van de Kwant oren die beschikbaar zijn in Power shell:</span><span class="sxs-lookup"><span data-stu-id="41a59-153">The following are a few of the quantifiers available in PowerShell:</span></span>

| <span data-ttu-id="41a59-154">Kwantiteits meter</span><span class="sxs-lookup"><span data-stu-id="41a59-154">Quantifier</span></span> |                <span data-ttu-id="41a59-155">Description</span><span class="sxs-lookup"><span data-stu-id="41a59-155">Description</span></span>                |
| ---------- | ----------------------------------------- |
| `*`        | <span data-ttu-id="41a59-156">Nul of meer keer.</span><span class="sxs-lookup"><span data-stu-id="41a59-156">Zero or more times.</span></span>                       |
| `+`        | <span data-ttu-id="41a59-157">Een of meer keren.</span><span class="sxs-lookup"><span data-stu-id="41a59-157">One or more times.</span></span>                        |
| `?`        | <span data-ttu-id="41a59-158">Nul of één keer.</span><span class="sxs-lookup"><span data-stu-id="41a59-158">Zero or one time.</span></span>                         |
| `{n,m}`    | <span data-ttu-id="41a59-159">Minstens `n` , maar niet meer dan een `m` keer.</span><span class="sxs-lookup"><span data-stu-id="41a59-159">At least `n`, but no more than `m` times.</span></span> |

<span data-ttu-id="41a59-160">Het sterretje ( `*` ) komt niet overeen met het vorige element of is meer dan nul.</span><span class="sxs-lookup"><span data-stu-id="41a59-160">The asterisk (`*`) matches the previous element zero or more times.</span></span> <span data-ttu-id="41a59-161">Het resultaat is dat zelfs een invoer teken reeks zonder het element een overeenkomst zou zijn.</span><span class="sxs-lookup"><span data-stu-id="41a59-161">The result is that even an input string without the element would be a match.</span></span>

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

<span data-ttu-id="41a59-162">Het plus teken ( `+` ) komt een of meer keer overeen met het vorige element.</span><span class="sxs-lookup"><span data-stu-id="41a59-162">The plus sign (`+`) matches the previous element one or more times.</span></span>

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

<span data-ttu-id="41a59-163">Het vraag teken `?` komt overeen met het vorige element nul of één keer.</span><span class="sxs-lookup"><span data-stu-id="41a59-163">The question mark `?` matches the previous element zero or one time.</span></span> <span data-ttu-id="41a59-164">Net als bij een sterretje komt `*` het overeen met teken reeksen waar het element niet aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="41a59-164">Like asterisk `*`, it will even match strings where the element is absent.</span></span>

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

<span data-ttu-id="41a59-165">De `{n, m}` kwantor kan verschillende manieren gebruiken om nauw keurige controle over de kwantor toe te staan.</span><span class="sxs-lookup"><span data-stu-id="41a59-165">The `{n, m}` quantifier can be used several different ways to allow granular control over the quantifier.</span></span> <span data-ttu-id="41a59-166">Het tweede element `m` en de komma `,` zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="41a59-166">The second element `m` and the comma `,` are optional.</span></span>

| <span data-ttu-id="41a59-167">Kwantiteits meter</span><span class="sxs-lookup"><span data-stu-id="41a59-167">Quantifier</span></span> |                <span data-ttu-id="41a59-168">Description</span><span class="sxs-lookup"><span data-stu-id="41a59-168">Description</span></span>                 |
| ---------- | ------------------------------------------ |
| `{n}`      | <span data-ttu-id="41a59-169">EXACT overeenkomen met het `n` aantal keren.</span><span class="sxs-lookup"><span data-stu-id="41a59-169">Match EXACTLY `n` number of times.</span></span>         |
| `{n,}`     | <span data-ttu-id="41a59-170">Ten minste één `n` keer overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="41a59-170">Match at LEAST `n` number of times.</span></span>        |
| `{n,m}`    | <span data-ttu-id="41a59-171">Komt overeen met `n` en `m` aantal keren.</span><span class="sxs-lookup"><span data-stu-id="41a59-171">Match between `n` and `m` number of times.</span></span> |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a><span data-ttu-id="41a59-172">Ankers</span><span class="sxs-lookup"><span data-stu-id="41a59-172">Anchors</span></span>

<span data-ttu-id="41a59-173">Met ankers kunt u ervoor zorgen dat een overeenkomst slaagt of mislukt op basis van de overeenkomst positie binnen de invoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="41a59-173">Anchors allow you to cause a match to succeed or fail based on the matches position within the input string.</span></span>

<span data-ttu-id="41a59-174">De twee veelgebruikte ankers zijn `^` en `$` .</span><span class="sxs-lookup"><span data-stu-id="41a59-174">The two commonly used anchors are `^` and `$`.</span></span> <span data-ttu-id="41a59-175">Het caret `^` komt overeen met het begin van een teken reeks en `$` , die overeenkomt met het einde van een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="41a59-175">The caret `^` matches the start of a string, and `$`, which matches the end of a string.</span></span> <span data-ttu-id="41a59-176">Met de ankers kunt u uw tekst op een specifieke positie afstemmen en ook ongewenste tekens verwijderen.</span><span class="sxs-lookup"><span data-stu-id="41a59-176">The anchors allow you to match your text at a specific position while also discarding unwanted characters.</span></span>

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> <span data-ttu-id="41a59-177">Wanneer u een regex met een `$` anker definieert, moet u de regex insluiten met enkele aanhalings tekens ( `'` ) in plaats van dubbele aanhalings tekens ( `"` ) of de expressie wordt in Power shell uitgebreid als een variabele.</span><span class="sxs-lookup"><span data-stu-id="41a59-177">When defining a regex containing an `$` anchor, be sure to enclose the regex using single quotes (`'`) instead of double quotes (`"`) or PowerShell will expand the expression as a variable.</span></span>

<span data-ttu-id="41a59-178">Wanneer u ankers in Power shell gebruikt, moet u weten wat het verschil is tussen de opties van de **modus singleline** en de reguliere expressie van **meerdere regels** .</span><span class="sxs-lookup"><span data-stu-id="41a59-178">When using anchors in PowerShell, you should understand the difference between **Singleline** and **Multiline** regular expression options.</span></span>

- <span data-ttu-id="41a59-179">**Meerdere** regels: de modus `^` voor meerdere regels en `$` het begin einde van elke regel wordt vergeleken in plaats van het begin en het einde van de invoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="41a59-179">**Multiline**: Multiline mode forces `^` and `$` to match the beginning end of every LINE instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="41a59-180">**Modus singleline**: de modus singleline-modus behandelt de invoer teken reeks als een **modus singleline**.</span><span class="sxs-lookup"><span data-stu-id="41a59-180">**Singleline**: Singleline mode treats the input string as a **SingleLine**.</span></span>
  <span data-ttu-id="41a59-181">Hiermee wordt het `.` teken afgedwongen dat overeenkomt met elk teken (inclusief nieuwe regels), in plaats van elk teken te vergelijken met de nieuwe regel `\n` .</span><span class="sxs-lookup"><span data-stu-id="41a59-181">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>

<span data-ttu-id="41a59-182">Voor meer informatie over deze opties en hoe u deze kunt gebruiken, gaat u naar de [reguliere expressie taal-Naslag informatie](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span><span class="sxs-lookup"><span data-stu-id="41a59-182">To read more about these options and how to use them, visit the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

### <a name="escaping-characters"></a><span data-ttu-id="41a59-183">Escape tekens</span><span class="sxs-lookup"><span data-stu-id="41a59-183">Escaping characters</span></span>

<span data-ttu-id="41a59-184">De back slash ( `\` ) wordt gebruikt om tekens te escapen zodat ze niet worden geparseerd door de reguliere expressie-engine.</span><span class="sxs-lookup"><span data-stu-id="41a59-184">The backslash (`\`) is used to escape characters so they aren't parsed by the regular expression engine.</span></span>

<span data-ttu-id="41a59-185">De volgende tekens zijn gereserveerd: `[]().\^$|?*+{}` .</span><span class="sxs-lookup"><span data-stu-id="41a59-185">The following characters are reserved: `[]().\^$|?*+{}`.</span></span>

<span data-ttu-id="41a59-186">U moet deze tekens in uw patronen opescapeen zodat deze overeenkomen met uw invoer teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="41a59-186">You'll need to escape these characters in your patterns to match them in your input strings.</span></span>

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

<span data-ttu-id="41a59-187">Er is een statische methode van de regex-klasse die tekst voor u kan escapef.</span><span class="sxs-lookup"><span data-stu-id="41a59-187">There\`s a static method of the regex class that can escape text for you.</span></span>

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> <span data-ttu-id="41a59-188">Hiermee worden alle gereserveerde reguliere expressie tekens geescapet, inclusief de bestaande backslashes die in teken klassen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="41a59-188">This escapes all reserved regular expression characters, including existing backslashes used in character classes.</span></span> <span data-ttu-id="41a59-189">Zorg ervoor dat u deze alleen gebruikt in het gedeelte van het patroon dat u wilt escapepen.</span><span class="sxs-lookup"><span data-stu-id="41a59-189">Be sure to only use it on the portion of your pattern that you need to escape.</span></span>

#### <a name="other-character-escapes"></a><span data-ttu-id="41a59-190">Andere teken-Escapes</span><span class="sxs-lookup"><span data-stu-id="41a59-190">Other character escapes</span></span>

<span data-ttu-id="41a59-191">Er zijn ook gereserveerde teken-Escapes die u kunt gebruiken om speciale teken typen te koppelen.</span><span class="sxs-lookup"><span data-stu-id="41a59-191">There are also reserved character escapes that you can use to match special character types.</span></span>

<span data-ttu-id="41a59-192">Hier volgen enkele veelgebruikte escape-tekens:</span><span class="sxs-lookup"><span data-stu-id="41a59-192">The following are a few commonly used character escapes:</span></span>

|<span data-ttu-id="41a59-193">Escape teken</span><span class="sxs-lookup"><span data-stu-id="41a59-193">Character Escape</span></span>  |<span data-ttu-id="41a59-194">Description</span><span class="sxs-lookup"><span data-stu-id="41a59-194">Description</span></span>  |
|---------|---------|
|`\t`|<span data-ttu-id="41a59-195">Komt overeen met een tabblad</span><span class="sxs-lookup"><span data-stu-id="41a59-195">Matches a tab</span></span>|
|`\n`|<span data-ttu-id="41a59-196">Komt overeen met een nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="41a59-196">Matches a newline</span></span>|
|`\r`|<span data-ttu-id="41a59-197">Komt overeen met een Enter-retour</span><span class="sxs-lookup"><span data-stu-id="41a59-197">Matches a carriage return</span></span>|

### <a name="groups-captures-and-substitutions"></a><span data-ttu-id="41a59-198">Groepen, vastleg ging en vervangingen</span><span class="sxs-lookup"><span data-stu-id="41a59-198">Groups, Captures, and Substitutions</span></span>

<span data-ttu-id="41a59-199">Met groeperings constructies wordt een invoer teken reeks gescheiden in subtekenreeksen die kunnen worden vastgelegd of genegeerd.</span><span class="sxs-lookup"><span data-stu-id="41a59-199">Grouping constructs separate an input string into substrings that can be captured or ignored.</span></span> <span data-ttu-id="41a59-200">Gegroepeerde subtekenreeksen worden subexpressies genoemd.</span><span class="sxs-lookup"><span data-stu-id="41a59-200">Grouped substrings are called subexpressions.</span></span> <span data-ttu-id="41a59-201">Standaard worden subexpressies vastgelegd in genummerde groepen, maar u kunt ook namen toewijzen.</span><span class="sxs-lookup"><span data-stu-id="41a59-201">By default subexpressions are captured in numbered groups, though you can assign names to them as well.</span></span>

<span data-ttu-id="41a59-202">Een groeperings constructie is een reguliere expressie tussen haakjes.</span><span class="sxs-lookup"><span data-stu-id="41a59-202">A grouping construct is a regular expression surrounded by parentheses.</span></span> <span data-ttu-id="41a59-203">Alle tekst die overeenkomt met de Inge sloten reguliere expressie wordt vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="41a59-203">Any text matched by the enclosed regular expression is captured.</span></span> <span data-ttu-id="41a59-204">In het volgende voor beeld wordt de invoer tekst in twee opname groepen onderverdeeld.</span><span class="sxs-lookup"><span data-stu-id="41a59-204">The following example will break the input text into two capturing groups.</span></span>

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

<span data-ttu-id="41a59-205">Gebruik de `$Matches` automatische **hashtabel** -variabele om vastgelegde tekst op te halen.</span><span class="sxs-lookup"><span data-stu-id="41a59-205">Use the `$Matches` **Hashtable** automatic variable to retrieve captured text.</span></span>
<span data-ttu-id="41a59-206">De tekst die de volledige overeenkomst vertegenwoordigt, wordt opgeslagen op de sleutel `0` .</span><span class="sxs-lookup"><span data-stu-id="41a59-206">The text representing the entire match is stored at key `0`.</span></span>

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

<span data-ttu-id="41a59-207">Vastleg ging worden opgeslagen in numerieke sleutels met **gehele getallen** die van links naar rechts worden verhoogd.</span><span class="sxs-lookup"><span data-stu-id="41a59-207">Captures are stored in numeric **Integer** keys that increase from left to right.</span></span> <span data-ttu-id="41a59-208">Capture `1` bevat alle tekst totdat de gebruikers naam, Capture `2` bevat alleen de gebruikers naam.</span><span class="sxs-lookup"><span data-stu-id="41a59-208">Capture `1` contains all the text until the username, capture `2` contains just the username.</span></span>

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
> <span data-ttu-id="41a59-209">De `0` sleutel is een **geheel getal**.</span><span class="sxs-lookup"><span data-stu-id="41a59-209">The `0` key is an **Integer**.</span></span> <span data-ttu-id="41a59-210">U kunt elke **hash** -methode gebruiken om toegang te krijgen tot de opgeslagen waarde.</span><span class="sxs-lookup"><span data-stu-id="41a59-210">You can use any **Hashtable** method to access the value stored.</span></span>
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

#### <a name="named-captures"></a><span data-ttu-id="41a59-211">Benoemde opnamen</span><span class="sxs-lookup"><span data-stu-id="41a59-211">Named Captures</span></span>

<span data-ttu-id="41a59-212">Standaard worden opnamen opgeslagen in oplopende numerieke volg orde, van links naar rechts.</span><span class="sxs-lookup"><span data-stu-id="41a59-212">By default, captures are stored in ascending numeric order, from left to right.</span></span>
<span data-ttu-id="41a59-213">U kunt ook een **naam** toewijzen aan een opname groep.</span><span class="sxs-lookup"><span data-stu-id="41a59-213">You can also assign a **name** to a capturing group.</span></span> <span data-ttu-id="41a59-214">Deze **naam** wordt een sleutel voor de `$Matches` Automatische variabele **hashtabel** .</span><span class="sxs-lookup"><span data-stu-id="41a59-214">This **name** becomes a key on the `$Matches` **Hashtable** automatic variable.</span></span>

<span data-ttu-id="41a59-215">In een opname groep gebruikt `?<keyname>` u om opgenomen gegevens onder een benoemde sleutel op te slaan.</span><span class="sxs-lookup"><span data-stu-id="41a59-215">Inside a capturing group, use `?<keyname>` to store captured data under a named key.</span></span>

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

<span data-ttu-id="41a59-216">In het volgende voor beeld wordt de meest recente logboek vermelding opgeslagen in het Windows-beveiligings logboek.</span><span class="sxs-lookup"><span data-stu-id="41a59-216">The following example stores the newest log entry in the Windows Security Log.</span></span>
<span data-ttu-id="41a59-217">Met de gevoorziete reguliere expressie worden de gebruikers naam en het domein uit het bericht geëxtraheerd en opgeslagen onder de sleutels:**N** voor naam en **D** voor domein.</span><span class="sxs-lookup"><span data-stu-id="41a59-217">The provided regular expression extracts the username and domain from the message and stores them under the keys:**N** for name and **D** for domain.</span></span>

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

<span data-ttu-id="41a59-218">Zie [Construct groups in reguliere expressies](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="41a59-218">For more information, see [Grouping Constructs in Regular Expressions](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).</span></span>

#### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="41a59-219">Vervangingen in reguliere expressies</span><span class="sxs-lookup"><span data-stu-id="41a59-219">Substitutions in Regular Expressions</span></span>

<span data-ttu-id="41a59-220">Met de reguliere expressies met de `-replace` operator kunt u tekst dynamisch vervangen met behulp van vastgelegde tekst.</span><span class="sxs-lookup"><span data-stu-id="41a59-220">Using the regular expressions with the `-replace` operator allows you to dynamically replace text using captured text.</span></span>

`<input> -replace <original>, <substitute>`

- <span data-ttu-id="41a59-221">`<input>`: De teken reeks die moet worden doorzocht</span><span class="sxs-lookup"><span data-stu-id="41a59-221">`<input>`: The string to be searched</span></span>
- <span data-ttu-id="41a59-222">`<original>`: Een reguliere expressie die wordt gebruikt om de invoer teken reeks te doorzoeken</span><span class="sxs-lookup"><span data-stu-id="41a59-222">`<original>`: A regular expression used to search the input string</span></span>
- <span data-ttu-id="41a59-223">`<substitute>`: Een expressie voor vervanging van een reguliere expressie om overeenkomsten te vervangen die in de invoer teken reeks zijn gevonden.</span><span class="sxs-lookup"><span data-stu-id="41a59-223">`<substitute>`: A regular expression substitution expression to replace matches found in the input string.</span></span>

> [!NOTE]
> <span data-ttu-id="41a59-224">De `<original>` `<substitute>` operanden en zijn onderworpen aan regels van de reguliere-expressie-engine, zoals teken-Escapes.</span><span class="sxs-lookup"><span data-stu-id="41a59-224">The `<original>` and `<substitute>` operands are subject to rules of the regular expression engine such as character escaping.</span></span>

<span data-ttu-id="41a59-225">In de teken reeks kan naar de opname groepen worden verwezen `<substitute>` .</span><span class="sxs-lookup"><span data-stu-id="41a59-225">Capturing groups can be referenced in the `<substitute>` string.</span></span> <span data-ttu-id="41a59-226">De vervanging wordt uitgevoerd met behulp van het `$` teken voor de groeps-id.</span><span class="sxs-lookup"><span data-stu-id="41a59-226">The substitution is done by using the `$` character before the group identifier.</span></span>

<span data-ttu-id="41a59-227">U kunt op twee manieren verwijzen naar het vastleggen van groepen op **nummer** en **naam**.</span><span class="sxs-lookup"><span data-stu-id="41a59-227">Two ways to reference capturing groups are by **Number** and by **Name**.</span></span>

- <span data-ttu-id="41a59-228">Op **nummer** : het vastleggen van groepen wordt van links naar rechts genummerd.</span><span class="sxs-lookup"><span data-stu-id="41a59-228">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="41a59-229">Op **naam** : voor het vastleggen van groepen kan ook naar een naam worden verwezen.</span><span class="sxs-lookup"><span data-stu-id="41a59-229">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

<span data-ttu-id="41a59-230">De `$&` expressie vertegenwoordigt alle overeenkomende tekst.</span><span class="sxs-lookup"><span data-stu-id="41a59-230">The `$&` expression represents all the text matched.</span></span>

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> <span data-ttu-id="41a59-231">Omdat het `$` teken wordt gebruikt in teken reeks uitbreiding, moet u letterlijke teken reeksen gebruiken met vervanging of het teken escapen `$` Wanneer u dubbele aanhalings tekens gebruikt.</span><span class="sxs-lookup"><span data-stu-id="41a59-231">Since the `$` character is used in string expansion, you'll need to use literal strings with substitution, or escape the `$` character when using double quotes.</span></span>
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
> <span data-ttu-id="41a59-232">Als u het `$` als letterlijk teken wilt gebruiken, gebruikt u dit `$$` in plaats van de normale escape-tekens.</span><span class="sxs-lookup"><span data-stu-id="41a59-232">Additionally, if you want to have the `$` as a literal character, use `$$` instead of the normal escape characters.</span></span> <span data-ttu-id="41a59-233">Wanneer u dubbele aanhalings tekens gebruikt, moet u nog steeds alle exemplaren van `$` vervangen om een onjuiste vervanging te voor komen.</span><span class="sxs-lookup"><span data-stu-id="41a59-233">When using double quotes, still escape all instances of `$` to avoid incorrect substitution.</span></span>
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

<span data-ttu-id="41a59-234">Zie [vervangingen in reguliere expressies](/dotnet/standard/base-types/substitutions-in-regular-expressions)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="41a59-234">For more information, see [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions).</span></span>

## <a name="see-also"></a><span data-ttu-id="41a59-235">Zie ook</span><span class="sxs-lookup"><span data-stu-id="41a59-235">See also</span></span>

[<span data-ttu-id="41a59-236">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="41a59-236">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="41a59-237">about_Operators</span><span class="sxs-lookup"><span data-stu-id="41a59-237">about_Operators</span></span>](about_Operators.md)

