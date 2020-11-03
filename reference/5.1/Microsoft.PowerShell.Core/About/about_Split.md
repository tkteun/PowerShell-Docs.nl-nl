---
description: Hierin wordt uitgelegd hoe u de operator split gebruikt om een of meer teken reeksen te splitsen in subtekenreeksen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/20/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: e93f68265bf560b03ac503ca914a11dde1f6b061
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252554"
---
# <a name="about-split"></a><span data-ttu-id="bc51a-104">Over splitsen</span><span class="sxs-lookup"><span data-stu-id="bc51a-104">About Split</span></span>

## <a name="short-description"></a><span data-ttu-id="bc51a-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bc51a-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="bc51a-106">Hierin wordt uitgelegd hoe u de operator split gebruikt om een of meer teken reeksen te splitsen in subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="bc51a-106">Explains how to use the Split operator to split one or more strings into substrings.</span></span>

## <a name="long-description"></a><span data-ttu-id="bc51a-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bc51a-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="bc51a-108">Met de operator Split worden een of meer teken reeksen gesplitst in subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="bc51a-108">The Split operator splits one or more strings into substrings.</span></span> <span data-ttu-id="bc51a-109">U kunt de volgende elementen van de gesplitste bewerking wijzigen:</span><span class="sxs-lookup"><span data-stu-id="bc51a-109">You can change the following elements of the Split operation:</span></span>

- <span data-ttu-id="bc51a-110">Vorm.</span><span class="sxs-lookup"><span data-stu-id="bc51a-110">Delimiter.</span></span> <span data-ttu-id="bc51a-111">De standaard waarde is witruimte, maar u kunt tekens, teken reeksen, patronen of script blokken opgeven waarmee het scheidings teken wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bc51a-111">The default is whitespace, but you can specify characters, strings, patterns, or script blocks that specify the delimiter.</span></span> <span data-ttu-id="bc51a-112">De Splits operator in Windows Power Shell maakt gebruik van een reguliere expressie in het scheidings teken, in plaats van een eenvoudig personage.</span><span class="sxs-lookup"><span data-stu-id="bc51a-112">The Split operator in Windows PowerShell uses a regular expression in the delimiter, rather than a simple character.</span></span>
- <span data-ttu-id="bc51a-113">Het maximum aantal subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="bc51a-113">Maximum number of substrings.</span></span> <span data-ttu-id="bc51a-114">Standaard worden alle subtekenreeksen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bc51a-114">The default is to return all substrings.</span></span> <span data-ttu-id="bc51a-115">Als u een getal opgeeft dat kleiner is dan het aantal subtekenreeksen, worden de resterende subtekenreeksen samengevoegd in de laatste subtekenreeks.</span><span class="sxs-lookup"><span data-stu-id="bc51a-115">If you specify a number less than the number of substrings, the remaining substrings are concatenated in the last substring.</span></span>
- <span data-ttu-id="bc51a-116">Opties die de voor waarden opgeven waaronder het scheidings teken wordt vergeleken, zoals SimpleMatch en meerregelige.</span><span class="sxs-lookup"><span data-stu-id="bc51a-116">Options that specify the conditions under which the delimiter is matched, such as SimpleMatch and Multiline.</span></span>

## <a name="syntax"></a><span data-ttu-id="bc51a-117">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="bc51a-117">SYNTAX</span></span>

<span data-ttu-id="bc51a-118">In het volgende diagram ziet u de syntaxis voor de operator-Split.</span><span class="sxs-lookup"><span data-stu-id="bc51a-118">The following diagram shows the syntax for the -split operator.</span></span>

<span data-ttu-id="bc51a-119">De parameter namen worden niet weer gegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="bc51a-119">The parameter names do not appear in the command.</span></span> <span data-ttu-id="bc51a-120">Alleen de parameter waarden bevatten.</span><span class="sxs-lookup"><span data-stu-id="bc51a-120">Include only the parameter values.</span></span> <span data-ttu-id="bc51a-121">De waarden moeten worden weer gegeven in de volg orde die is opgegeven in het syntaxis diagram.</span><span class="sxs-lookup"><span data-stu-id="bc51a-121">The values must appear in the order specified in the syntax diagram.</span></span>

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

<span data-ttu-id="bc51a-122">U kunt vervangen `-iSplit` of `-cSplit` voor `-split` een binaire Splits instructie (een split-instructie met een scheidings teken of script blok).</span><span class="sxs-lookup"><span data-stu-id="bc51a-122">You can substitute `-iSplit` or `-cSplit` for `-split` in any binary Split statement (a Split statement that includes a delimiter or script block).</span></span> <span data-ttu-id="bc51a-123">De `-iSplit` `-split` Opera tors en zijn niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="bc51a-123">The `-iSplit` and `-split` operators are case-insensitive.</span></span> <span data-ttu-id="bc51a-124">De `-cSplit` operator is hoofdletter gevoelig, wat betekent dat er sprake is van het Toep assen van de scheidings regels.</span><span class="sxs-lookup"><span data-stu-id="bc51a-124">The `-cSplit` operator is case-sensitive, meaning that case is considered when the delimiter rules are applied.</span></span>

## <a name="parameters"></a><span data-ttu-id="bc51a-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bc51a-125">PARAMETERS</span></span>

### <a name="string-or-string"></a><span data-ttu-id="bc51a-126">\<String\> of \<String[]\></span><span class="sxs-lookup"><span data-stu-id="bc51a-126">\<String\> or \<String[]\></span></span>

<span data-ttu-id="bc51a-127">Hiermee geeft u een of meer teken reeksen moet worden gesplitst.</span><span class="sxs-lookup"><span data-stu-id="bc51a-127">Specifies one or more strings to be split.</span></span> <span data-ttu-id="bc51a-128">Als u meerdere teken reeksen verzendt, worden alle teken reeksen gesplitst met dezelfde scheidings regels.</span><span class="sxs-lookup"><span data-stu-id="bc51a-128">If you submit multiple strings, all the strings are split using the same delimiter rules.</span></span>

<span data-ttu-id="bc51a-129">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bc51a-129">Example:</span></span>

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

<span data-ttu-id="bc51a-130">De tekens die het einde van een subtekenreeks identificeren.</span><span class="sxs-lookup"><span data-stu-id="bc51a-130">The characters that identify the end of a substring.</span></span> <span data-ttu-id="bc51a-131">Het standaard scheidings teken is witruimte, inclusief spaties en niet-afdruk bare tekens, zoals nieuwe regel ( \` n) en tab ( \` t).</span><span class="sxs-lookup"><span data-stu-id="bc51a-131">The default delimiter is whitespace, including spaces and non-printable characters, such as newline (\`n) and tab (\`t).</span></span> <span data-ttu-id="bc51a-132">Wanneer de teken reeksen zijn gesplitst, wordt het scheidings teken uit alle subtekenreeksen wegge laten.</span><span class="sxs-lookup"><span data-stu-id="bc51a-132">When the strings are split, the delimiter is omitted from all the substrings.</span></span> <span data-ttu-id="bc51a-133">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bc51a-133">Example:</span></span>

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

<span data-ttu-id="bc51a-134">Standaard wordt het scheidings teken uit de resultaten wegge laten.</span><span class="sxs-lookup"><span data-stu-id="bc51a-134">By default, the delimiter is omitted from the results.</span></span> <span data-ttu-id="bc51a-135">Als u het scheidings teken geheel of gedeeltelijk wilt behouden, plaatst u tussen haakjes het onderdeel dat u wilt behouden.</span><span class="sxs-lookup"><span data-stu-id="bc51a-135">To preserve all or part of the delimiter, enclose in parentheses the part that you want to preserve.</span></span>
<span data-ttu-id="bc51a-136">Als de \<Max-substrings\> para meter wordt toegevoegd, heeft dit prioriteit wanneer uw opdracht de verzameling opsplitst.</span><span class="sxs-lookup"><span data-stu-id="bc51a-136">If the \<Max-substrings\> parameter is added, this takes precedence when your command splits up the collection.</span></span> <span data-ttu-id="bc51a-137">Als u ervoor kiest om een scheidings teken op te nemen als onderdeel van de uitvoer, retourneert de opdracht het scheidings teken als onderdeel van de uitvoer; het splitsen van de teken reeks om het scheidings teken als onderdeel van de uitvoer te retour neren, telt echter niet als een splitsing.</span><span class="sxs-lookup"><span data-stu-id="bc51a-137">If you opt to include a delimiter as part of the output, the command returns the delimiter as part of the output; however, splitting the string to return the delimiter as part of output does not count as a split.</span></span>

<span data-ttu-id="bc51a-138">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="bc51a-138">Examples:</span></span>

```
"Lastname:FirstName:Address" -split "(:)"
Lastname
:
FirstName
:
Address

"Lastname/:/FirstName/:/Address" -split "/(:)/"
Lastname
:
FirstName
:
Address
```

<span data-ttu-id="bc51a-139">In het volgende voor beeld \<Max-substrings\> is ingesteld op 3.</span><span class="sxs-lookup"><span data-stu-id="bc51a-139">In the following example, \<Max-substrings\> is set to 3.</span></span> <span data-ttu-id="bc51a-140">Dit resulteert in drie delen van de teken reeks waarden, maar in totaal vijf teken reeksen in de resulterende uitvoer; het scheidings teken wordt opgenomen na de splitsing, totdat het maximum van de drie subtekenreeksen is bereikt.</span><span class="sxs-lookup"><span data-stu-id="bc51a-140">This results in three splits of the string values, but a total of five strings in the resulting output; the delimiter is included after the splits, until the maximum of three substrings is reached.</span></span> <span data-ttu-id="bc51a-141">Extra scheidings tekens in de uiteindelijke subtekenreeks worden deel van de subtekenreeks.</span><span class="sxs-lookup"><span data-stu-id="bc51a-141">Additional delimiters in the final substring become part of the substring.</span></span>

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

<span data-ttu-id="bc51a-142">Hiermee geeft u het maximum aantal keren op dat een teken reeks moet worden gesplitst.</span><span class="sxs-lookup"><span data-stu-id="bc51a-142">Specifies the maximum number of times that a string is split.</span></span> <span data-ttu-id="bc51a-143">De standaard waarde is alle subtekenreeksen die door het scheidings teken worden gesplitst.</span><span class="sxs-lookup"><span data-stu-id="bc51a-143">The default is all the substrings split by the delimiter.</span></span> <span data-ttu-id="bc51a-144">Als er meer subtekenreeksen zijn, worden deze samengevoegd met de uiteindelijke subtekenreeks.</span><span class="sxs-lookup"><span data-stu-id="bc51a-144">If there are more substrings, they are concatenated to the final substring.</span></span> <span data-ttu-id="bc51a-145">Als er minder subtekenreeksen zijn, worden alle subtekenreeksen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bc51a-145">If there are fewer substrings, all the substrings are returned.</span></span> <span data-ttu-id="bc51a-146">De waarde 0 en negatieve waarden geven alle subtekenreeksen als resultaat.</span><span class="sxs-lookup"><span data-stu-id="bc51a-146">A value of 0 and negative values return all the substrings.</span></span>

<span data-ttu-id="bc51a-147">Max-subtekenreeksen geeft niet het maximum aantal objecten op dat wordt geretourneerd. de waarde is gelijk aan het maximum aantal keren dat een teken reeks wordt gesplitst.</span><span class="sxs-lookup"><span data-stu-id="bc51a-147">Max-substrings does not specify the maximum number of objects that are returned; its value equals the maximum number of times that a string is split.</span></span>
<span data-ttu-id="bc51a-148">Als u meer dan één teken reeks (een matrix met teken reeksen) naar de Splits operator verzendt, wordt de limiet voor de maximale subtekenreeksen voor elke teken reeks afzonderlijk toegepast.</span><span class="sxs-lookup"><span data-stu-id="bc51a-148">If you submit more than one string (an array of strings) to the Split operator , the Max-substrings limit is applied to each string separately.</span></span>

<span data-ttu-id="bc51a-149">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bc51a-149">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

### \<ScriptBlock\>

<span data-ttu-id="bc51a-150">Een expressie waarmee de regels voor het Toep assen van het scheidings teken worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bc51a-150">An expression that specifies rules for applying the delimiter.</span></span> <span data-ttu-id="bc51a-151">De expressie moet $true of $false evalueren.</span><span class="sxs-lookup"><span data-stu-id="bc51a-151">The expression must evaluate to $true or $false.</span></span> <span data-ttu-id="bc51a-152">Plaats het script blok tussen accolades.</span><span class="sxs-lookup"><span data-stu-id="bc51a-152">Enclose the script block in braces.</span></span>

<span data-ttu-id="bc51a-153">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bc51a-153">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

<span data-ttu-id="bc51a-154">Plaats de naam van de optie tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="bc51a-154">Enclose the option name in quotation marks.</span></span> <span data-ttu-id="bc51a-155">Opties zijn alleen geldig wanneer de \<Max-substrings\> para meter wordt gebruikt in de instructie.</span><span class="sxs-lookup"><span data-stu-id="bc51a-155">Options are valid only when the \<Max-substrings\> parameter is used in the statement.</span></span>

<span data-ttu-id="bc51a-156">De syntaxis voor de para meter Options is:</span><span class="sxs-lookup"><span data-stu-id="bc51a-156">The syntax for the Options parameter is:</span></span>

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

<span data-ttu-id="bc51a-157">De SimpleMatch-opties zijn:</span><span class="sxs-lookup"><span data-stu-id="bc51a-157">The SimpleMatch options are:</span></span>

- <span data-ttu-id="bc51a-158">**SimpleMatch** : gebruik eenvoudige teken reeks vergelijking bij het evalueren van het scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="bc51a-158">**SimpleMatch** : Use simple string comparison when evaluating the delimiter.</span></span> <span data-ttu-id="bc51a-159">Kan niet worden gebruikt met RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="bc51a-159">Cannot be used with RegexMatch.</span></span>
- <span data-ttu-id="bc51a-160">**IgnoreCase** : dwingt niet-hoofdletter gevoelige overeenkomst af, zelfs als de operator-cSplit is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bc51a-160">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>

<span data-ttu-id="bc51a-161">De RegexMatch-opties zijn:</span><span class="sxs-lookup"><span data-stu-id="bc51a-161">The RegexMatch options are:</span></span>

- <span data-ttu-id="bc51a-162">**RegexMatch** : gebruik reguliere expressie matching om het scheidings teken te evalueren.</span><span class="sxs-lookup"><span data-stu-id="bc51a-162">**RegexMatch** : Use regular expression matching to evaluate the delimiter.</span></span> <span data-ttu-id="bc51a-163">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="bc51a-163">This is the default behavior.</span></span> <span data-ttu-id="bc51a-164">Kan niet worden gebruikt met SimpleMatch.</span><span class="sxs-lookup"><span data-stu-id="bc51a-164">Cannot be used with SimpleMatch.</span></span>
- <span data-ttu-id="bc51a-165">**IgnoreCase** : dwingt niet-hoofdletter gevoelige overeenkomst af, zelfs als de operator-cSplit is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bc51a-165">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>
- <span data-ttu-id="bc51a-166">**CultureInvariant** : negeert culturele verschillen in taal wanneer het scheidings teken wordt evaluting.</span><span class="sxs-lookup"><span data-stu-id="bc51a-166">**CultureInvariant** : Ignores cultural differences in language when evaluting the delimiter.</span></span> <span data-ttu-id="bc51a-167">Alleen geldig voor RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="bc51a-167">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="bc51a-168">**IgnorePatternWhitespace** : negeert witruimte zonder escape-teken en opmerkingen met het hekje (#).</span><span class="sxs-lookup"><span data-stu-id="bc51a-168">**IgnorePatternWhitespace** : Ignores unescaped whitespace and comments marked with the number sign (#).</span></span> <span data-ttu-id="bc51a-169">Alleen geldig voor RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="bc51a-169">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="bc51a-170">**Meerdere** regels: de modus `^` voor meerdere regels en `$` het begin einde van elke regel wordt vergeleken in plaats van het begin en het einde van de invoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="bc51a-170">**Multiline** : Multiline mode forces `^` and `$` to match the beginning end of every line instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="bc51a-171">**Modus singleline** : de modus singleline-modus behandelt de invoer teken reeks als een *modus singleline*.</span><span class="sxs-lookup"><span data-stu-id="bc51a-171">**Singleline** : Singleline mode treats the input string as a *SingleLine*.</span></span>
  <span data-ttu-id="bc51a-172">Hiermee wordt het `.` teken afgedwongen dat overeenkomt met elk teken (inclusief nieuwe regels), in plaats van elk teken te vergelijken met de nieuwe regel `\n` .</span><span class="sxs-lookup"><span data-stu-id="bc51a-172">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>
- <span data-ttu-id="bc51a-173">**ExplicitCapture** : negeert niet-benoemde overeenkomende groepen, zodat alleen expliciete opname groepen worden geretourneerd in de lijst met resultaten.</span><span class="sxs-lookup"><span data-stu-id="bc51a-173">**ExplicitCapture** : Ignores non-named match groups so that only explicit capture groups are returned in the result list.</span></span> <span data-ttu-id="bc51a-174">Alleen geldig voor RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="bc51a-174">Valid only with RegexMatch.</span></span>

> [!NOTE]
> <span data-ttu-id="bc51a-175">Modus singleline is het standaard gedrag.</span><span class="sxs-lookup"><span data-stu-id="bc51a-175">SingleLine is the default behavior.</span></span> <span data-ttu-id="bc51a-176">Modus singleline en meerregelige kunnen niet worden gebruikt in combi natie met de para meter Options.</span><span class="sxs-lookup"><span data-stu-id="bc51a-176">Singleline and Multiline cannot be used together with the options parameter.</span></span> <span data-ttu-id="bc51a-177">Dit probleem is opgelost in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="bc51a-177">This was resolved in PowerShell 6.0.</span></span>
> <span data-ttu-id="bc51a-178">De tijdelijke oplossing is met behulp van de *modus-para meters* in uw reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="bc51a-178">The work around is by using *Mode-Modifiers* in your regular expression.</span></span>
> <span data-ttu-id="bc51a-179">U kunt meer informatie over de opties voor de modus in [reguliere expressies](/dotnet/standard/base-types/regular-expression-options) lezen</span><span class="sxs-lookup"><span data-stu-id="bc51a-179">You can read more about mode modifiers in [Regular Expression Options](/dotnet/standard/base-types/regular-expression-options)</span></span>

## <a name="unary-and-binary-split-operators"></a><span data-ttu-id="bc51a-180">Unaire en binaire SPLITs Opera tors</span><span class="sxs-lookup"><span data-stu-id="bc51a-180">UNARY and BINARY SPLIT OPERATORS</span></span>

<span data-ttu-id="bc51a-181">De unaire Splits operator ( `-split <string>` ) heeft een hogere prioriteit dan een komma.</span><span class="sxs-lookup"><span data-stu-id="bc51a-181">The unary split operator (`-split <string>`) has higher precedence than a comma.</span></span> <span data-ttu-id="bc51a-182">Als u dus een door komma's gescheiden lijst met teken reeksen verzendt naar de operator unsplit, wordt alleen de eerste teken reeks (vóór de eerste komma) gesplitst.</span><span class="sxs-lookup"><span data-stu-id="bc51a-182">As a result, if you submit a comma-separated list of strings to the unary split operator, only the first string (before the first comma) is split.</span></span>

<span data-ttu-id="bc51a-183">Gebruik een van de volgende patronen om meer dan één teken reeks te splitsen:</span><span class="sxs-lookup"><span data-stu-id="bc51a-183">Use one of the following patterns to split more than one string:</span></span>

- <span data-ttu-id="bc51a-184">De binaire Splits operator ( \<string[]\> -Split \<delimiter\> ) gebruiken</span><span class="sxs-lookup"><span data-stu-id="bc51a-184">Use the binary split operator (\<string[]\> -split \<delimiter\>)</span></span>
- <span data-ttu-id="bc51a-185">Alle teken reeksen tussen haakjes plaatsen</span><span class="sxs-lookup"><span data-stu-id="bc51a-185">Enclose all the strings in parentheses</span></span>
- <span data-ttu-id="bc51a-186">De teken reeksen in een variabele opslaan en vervolgens de variabele naar de Splits operator verzenden</span><span class="sxs-lookup"><span data-stu-id="bc51a-186">Store the strings in a variable then submit the variable to the split operator</span></span>

<span data-ttu-id="bc51a-187">Kijk eens naar het volgende voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bc51a-187">Consider the following example:</span></span>

```
PS> -split "1 2", "a b"
1
2
a b
```

```
PS> "1 2", "a b" -split " "
1
2
a
b
```

```
PS> -split ("1 2", "a b")
1
2
a
b
```

```
PS> $a = "1 2", "a b"
PS> -split $a
1
2
a
b
```

## <a name="examples"></a><span data-ttu-id="bc51a-188">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="bc51a-188">EXAMPLES</span></span>

<span data-ttu-id="bc51a-189">De volgende instructie splitst de teken reeks op een spatie.</span><span class="sxs-lookup"><span data-stu-id="bc51a-189">The following statement splits the string at whitespace.</span></span>

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

<span data-ttu-id="bc51a-190">De volgende instructie splitst de teken reeks op een wille keurige komma.</span><span class="sxs-lookup"><span data-stu-id="bc51a-190">The following statement splits the string at any comma.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

<span data-ttu-id="bc51a-191">Met de volgende instructie wordt de teken reeks in het patroon ' er ' gesplitst.</span><span class="sxs-lookup"><span data-stu-id="bc51a-191">The following statement splits the string at the pattern "er".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

<span data-ttu-id="bc51a-192">De volgende instructie voert een hoofdletter gevoelige splitsing uit op de letter "N".</span><span class="sxs-lookup"><span data-stu-id="bc51a-192">The following statement performs a case-sensitive split at the letter "N".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

<span data-ttu-id="bc51a-193">Met de volgende instructie wordt de teken reeks op ' e ' en ' t ' gesplitst.</span><span class="sxs-lookup"><span data-stu-id="bc51a-193">The following statement splits the string at "e" and "t".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```output
M
rcury,V
nus,
ar
h,Mars,Jupi

r,Sa
urn,Uranus,N
p
un
```

<span data-ttu-id="bc51a-194">Met de volgende instructie wordt de teken reeks op ' e ' en ' r ' gesplitst, maar worden de resulterende subtekenreeksen beperkt tot zes subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="bc51a-194">The following statement splits the string at "e" and "r", but limits the resulting substrings to six substrings.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

<span data-ttu-id="bc51a-195">Met de volgende instructie wordt een teken reeks gesplitst in drie subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="bc51a-195">The following statement splits a string into three substrings.</span></span>

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```output
a
b
c,d,e,f,g,h
```

<span data-ttu-id="bc51a-196">Met de volgende instructie splitst u twee teken reeksen in drie subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="bc51a-196">The following statement splits two strings into three substrings.</span></span>
<span data-ttu-id="bc51a-197">(De limiet wordt afzonderlijk toegepast op elke teken reeks.)</span><span class="sxs-lookup"><span data-stu-id="bc51a-197">(The limit is applied to each string independently.)</span></span>

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```output
a
b
c,d
e
f
g,h
```

<span data-ttu-id="bc51a-198">Met de volgende instructie wordt elke regel in de teken reeks in het eerste cijfer gesplitst.</span><span class="sxs-lookup"><span data-stu-id="bc51a-198">The following statement splits each line in the here-string at the first digit.</span></span> <span data-ttu-id="bc51a-199">De optie voor meerdere regels wordt gebruikt om het begin van elke regel en teken reeks te herkennen.</span><span class="sxs-lookup"><span data-stu-id="bc51a-199">It uses the Multiline option to recognize the beginning of each line and string.</span></span>

<span data-ttu-id="bc51a-200">De 0 vertegenwoordigt de waarde ' return all ' van de para meter Max-subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="bc51a-200">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="bc51a-201">U kunt opties, zoals meerregelige, alleen gebruiken wanneer de waarde voor de Max-subtekenreeksen is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bc51a-201">You can use options, such as Multiline, only when the Max-substrings value is specified.</span></span>

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```output

The first line.

The second line.

The third of three lines.
```

<span data-ttu-id="bc51a-202">In de volgende instructie wordt de back slash gebruikt om het punt scheidings teken (.) te escapen.</span><span class="sxs-lookup"><span data-stu-id="bc51a-202">The following statement uses the backslash character to escape the dot (.) delimiter.</span></span>

<span data-ttu-id="bc51a-203">Met de standaard waarde RegexMatch, de punt tussen aanhalings tekens (".") wordt geïnterpreteerd zodat deze overeenkomt met een wille keurig teken behalve een nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="bc51a-203">With the default, RegexMatch, the dot enclosed in quotation marks (".") is interpreted to match any character except for a newline character.</span></span> <span data-ttu-id="bc51a-204">Als gevolg hiervan retourneert de gesplitste instructie een lege regel voor elk teken behalve een nieuwe voor waarde.</span><span class="sxs-lookup"><span data-stu-id="bc51a-204">As a result, the Split statement returns a blank line for every character except newline.</span></span>

```powershell
"This.is.a.test" -split "\."
```

```output
This
is
a
test
```

<span data-ttu-id="bc51a-205">De volgende instructie maakt gebruik van de SimpleMatch-optie om de operator-split te sturen om het punt scheidings teken letterlijk te interpreteren.</span><span class="sxs-lookup"><span data-stu-id="bc51a-205">The following statement uses the SimpleMatch option to direct the -split operator to interpret the dot (.) delimiter literally.</span></span>

<span data-ttu-id="bc51a-206">De 0 vertegenwoordigt de waarde ' return all ' van de para meter Max-subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="bc51a-206">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="bc51a-207">U kunt opties, zoals SimpleMatch, alleen gebruiken wanneer de waarde voor de Max-subtekenreeksen is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="bc51a-207">You can use options, such as SimpleMatch, only when the Max-substrings value is specified.</span></span>

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```output
This
is
a
test
```

<span data-ttu-id="bc51a-208">Met de volgende instructie wordt de teken reeks in een van de twee scheidings tekens gesplitst, afhankelijk van de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="bc51a-208">The following statement splits the string at one of two delimiters, depending on the value of a variable.</span></span>

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a><span data-ttu-id="bc51a-209">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="bc51a-209">SEE ALSO</span></span>

[<span data-ttu-id="bc51a-210">Split-pad</span><span class="sxs-lookup"><span data-stu-id="bc51a-210">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)

[<span data-ttu-id="bc51a-211">about_Operators</span><span class="sxs-lookup"><span data-stu-id="bc51a-211">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="bc51a-212">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="bc51a-212">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="bc51a-213">about_Join</span><span class="sxs-lookup"><span data-stu-id="bc51a-213">about_Join</span></span>](about_Join.md)
