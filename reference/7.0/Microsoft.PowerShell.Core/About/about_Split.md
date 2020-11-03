---
description: Hierin wordt uitgelegd hoe u de operator split gebruikt om een of meer teken reeksen te splitsen in subtekenreeksen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: ed57cec30577fbd02f7aa317460bf1a73b006685
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252064"
---
# <a name="about-split"></a><span data-ttu-id="d2177-104">Over splitsen</span><span class="sxs-lookup"><span data-stu-id="d2177-104">About Split</span></span>

## <a name="short-description"></a><span data-ttu-id="d2177-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d2177-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="d2177-106">Hierin wordt uitgelegd hoe u de operator split gebruikt om een of meer teken reeksen te splitsen in subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d2177-106">Explains how to use the Split operator to split one or more strings into substrings.</span></span>

## <a name="long-description"></a><span data-ttu-id="d2177-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d2177-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="d2177-108">Met de operator Split worden een of meer teken reeksen gesplitst in subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d2177-108">The Split operator splits one or more strings into substrings.</span></span> <span data-ttu-id="d2177-109">U kunt de volgende elementen van de gesplitste bewerking wijzigen:</span><span class="sxs-lookup"><span data-stu-id="d2177-109">You can change the following elements of the Split operation:</span></span>

- <span data-ttu-id="d2177-110">Vorm.</span><span class="sxs-lookup"><span data-stu-id="d2177-110">Delimiter.</span></span> <span data-ttu-id="d2177-111">De standaard waarde is witruimte, maar u kunt tekens, teken reeksen, patronen of script blokken opgeven waarmee het scheidings teken wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d2177-111">The default is whitespace, but you can specify characters, strings, patterns, or script blocks that specify the delimiter.</span></span> <span data-ttu-id="d2177-112">De Splits operator in Power Shell maakt gebruik van een reguliere expressie in het scheidings teken, in plaats van een eenvoudig personage.</span><span class="sxs-lookup"><span data-stu-id="d2177-112">The Split operator in PowerShell uses a regular expression in the delimiter, rather than a simple character.</span></span>
- <span data-ttu-id="d2177-113">Het maximum aantal subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d2177-113">Maximum number of substrings.</span></span> <span data-ttu-id="d2177-114">Standaard worden alle subtekenreeksen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d2177-114">The default is to return all substrings.</span></span> <span data-ttu-id="d2177-115">Als u een getal opgeeft dat kleiner is dan het aantal subtekenreeksen, worden de resterende subtekenreeksen samengevoegd in de laatste subtekenreeks.</span><span class="sxs-lookup"><span data-stu-id="d2177-115">If you specify a number less than the number of substrings, the remaining substrings are concatenated in the last substring.</span></span>
- <span data-ttu-id="d2177-116">Opties die de voor waarden opgeven waaronder het scheidings teken wordt vergeleken, zoals SimpleMatch en meerregelige.</span><span class="sxs-lookup"><span data-stu-id="d2177-116">Options that specify the conditions under which the delimiter is matched, such as SimpleMatch and Multiline.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2177-117">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d2177-117">SYNTAX</span></span>

<span data-ttu-id="d2177-118">In het volgende diagram ziet u de syntaxis voor de operator-Split.</span><span class="sxs-lookup"><span data-stu-id="d2177-118">The following diagram shows the syntax for the -split operator.</span></span>

<span data-ttu-id="d2177-119">De parameter namen worden niet weer gegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="d2177-119">The parameter names do not appear in the command.</span></span> <span data-ttu-id="d2177-120">Alleen de parameter waarden bevatten.</span><span class="sxs-lookup"><span data-stu-id="d2177-120">Include only the parameter values.</span></span> <span data-ttu-id="d2177-121">De waarden moeten worden weer gegeven in de volg orde die is opgegeven in het syntaxis diagram.</span><span class="sxs-lookup"><span data-stu-id="d2177-121">The values must appear in the order specified in the syntax diagram.</span></span>

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

<span data-ttu-id="d2177-122">U kunt vervangen `-iSplit` of `-cSplit` voor `-split` een binaire Splits instructie (een split-instructie met een scheidings teken of script blok).</span><span class="sxs-lookup"><span data-stu-id="d2177-122">You can substitute `-iSplit` or `-cSplit` for `-split` in any binary Split statement (a Split statement that includes a delimiter or script block).</span></span> <span data-ttu-id="d2177-123">De `-iSplit` `-split` Opera tors en zijn niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="d2177-123">The `-iSplit` and `-split` operators are case-insensitive.</span></span> <span data-ttu-id="d2177-124">De `-cSplit` operator is hoofdletter gevoelig, wat betekent dat er sprake is van het Toep assen van de scheidings regels.</span><span class="sxs-lookup"><span data-stu-id="d2177-124">The `-cSplit` operator is case-sensitive, meaning that case is considered when the delimiter rules are applied.</span></span>

## <a name="parameters"></a><span data-ttu-id="d2177-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d2177-125">PARAMETERS</span></span>

### <a name="string-or-string"></a><span data-ttu-id="d2177-126">\<String\> of \<String[]\></span><span class="sxs-lookup"><span data-stu-id="d2177-126">\<String\> or \<String[]\></span></span>

<span data-ttu-id="d2177-127">Hiermee geeft u een of meer teken reeksen moet worden gesplitst.</span><span class="sxs-lookup"><span data-stu-id="d2177-127">Specifies one or more strings to be split.</span></span> <span data-ttu-id="d2177-128">Als u meerdere teken reeksen verzendt, worden alle teken reeksen gesplitst met dezelfde scheidings regels.</span><span class="sxs-lookup"><span data-stu-id="d2177-128">If you submit multiple strings, all the strings are split using the same delimiter rules.</span></span>

<span data-ttu-id="d2177-129">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2177-129">Example:</span></span>

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

<span data-ttu-id="d2177-130">De tekens die het einde van een subtekenreeks identificeren.</span><span class="sxs-lookup"><span data-stu-id="d2177-130">The characters that identify the end of a substring.</span></span> <span data-ttu-id="d2177-131">Het standaard scheidings teken is witruimte, inclusief spaties en niet-afdruk bare tekens, zoals nieuwe regel ( \` n) en tab ( \` t).</span><span class="sxs-lookup"><span data-stu-id="d2177-131">The default delimiter is whitespace, including spaces and non-printable characters, such as newline (\`n) and tab (\`t).</span></span> <span data-ttu-id="d2177-132">Wanneer de teken reeksen zijn gesplitst, wordt het scheidings teken uit alle subtekenreeksen wegge laten.</span><span class="sxs-lookup"><span data-stu-id="d2177-132">When the strings are split, the delimiter is omitted from all the substrings.</span></span> <span data-ttu-id="d2177-133">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2177-133">Example:</span></span>

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

<span data-ttu-id="d2177-134">Standaard wordt het scheidings teken uit de resultaten wegge laten.</span><span class="sxs-lookup"><span data-stu-id="d2177-134">By default, the delimiter is omitted from the results.</span></span> <span data-ttu-id="d2177-135">Als u het scheidings teken geheel of gedeeltelijk wilt behouden, plaatst u tussen haakjes het onderdeel dat u wilt behouden.</span><span class="sxs-lookup"><span data-stu-id="d2177-135">To preserve all or part of the delimiter, enclose in parentheses the part that you want to preserve.</span></span>
<span data-ttu-id="d2177-136">Als de \<Max-substrings\> para meter wordt toegevoegd, heeft dit prioriteit wanneer uw opdracht de verzameling opsplitst.</span><span class="sxs-lookup"><span data-stu-id="d2177-136">If the \<Max-substrings\> parameter is added, this takes precedence when your command splits up the collection.</span></span> <span data-ttu-id="d2177-137">Als u ervoor kiest om een scheidings teken op te nemen als onderdeel van de uitvoer, retourneert de opdracht het scheidings teken als onderdeel van de uitvoer; het splitsen van de teken reeks om het scheidings teken als onderdeel van de uitvoer te retour neren, telt echter niet als een splitsing.</span><span class="sxs-lookup"><span data-stu-id="d2177-137">If you opt to include a delimiter as part of the output, the command returns the delimiter as part of the output; however, splitting the string to return the delimiter as part of output does not count as a split.</span></span>

<span data-ttu-id="d2177-138">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="d2177-138">Examples:</span></span>

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

<span data-ttu-id="d2177-139">In het volgende voor beeld \<Max-substrings\> is ingesteld op 3.</span><span class="sxs-lookup"><span data-stu-id="d2177-139">In the following example, \<Max-substrings\> is set to 3.</span></span> <span data-ttu-id="d2177-140">Dit resulteert in drie delen van de teken reeks waarden, maar in totaal vijf teken reeksen in de resulterende uitvoer; het scheidings teken wordt opgenomen na de splitsing, totdat het maximum van de drie subtekenreeksen is bereikt.</span><span class="sxs-lookup"><span data-stu-id="d2177-140">This results in three splits of the string values, but a total of five strings in the resulting output; the delimiter is included after the splits, until the maximum of three substrings is reached.</span></span> <span data-ttu-id="d2177-141">Extra scheidings tekens in de uiteindelijke subtekenreeks worden deel van de subtekenreeks.</span><span class="sxs-lookup"><span data-stu-id="d2177-141">Additional delimiters in the final substring become part of the substring.</span></span>

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```Output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

<span data-ttu-id="d2177-142">Hiermee geeft u het maximum aantal keren op dat een teken reeks moet worden gesplitst.</span><span class="sxs-lookup"><span data-stu-id="d2177-142">Specifies the maximum number of times that a string is split.</span></span> <span data-ttu-id="d2177-143">De standaard waarde is alle subtekenreeksen die door het scheidings teken worden gesplitst.</span><span class="sxs-lookup"><span data-stu-id="d2177-143">The default is all the substrings split by the delimiter.</span></span> <span data-ttu-id="d2177-144">Als er meer subtekenreeksen zijn, worden deze samengevoegd met de uiteindelijke subtekenreeks.</span><span class="sxs-lookup"><span data-stu-id="d2177-144">If there are more substrings, they are concatenated to the final substring.</span></span> <span data-ttu-id="d2177-145">Als er minder subtekenreeksen zijn, worden alle subtekenreeksen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d2177-145">If there are fewer substrings, all the substrings are returned.</span></span> <span data-ttu-id="d2177-146">De waarde 0 retourneert alle subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d2177-146">A value of 0 returns all the substrings.</span></span> <span data-ttu-id="d2177-147">Negatieve waarden geven de hoeveelheid subtekenreeksen aan die is aangevraagd vanaf het einde van de invoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="d2177-147">Negative values return the amount of substrings requested starting from the end of the input string.</span></span>

> [!NOTE]
> <span data-ttu-id="d2177-148">Er is ondersteuning voor negatieve waarden toegevoegd aan Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="d2177-148">Support for negative values was added in PowerShell 7.</span></span>

<span data-ttu-id="d2177-149">**Max-subtekenreeksen** geeft niet het maximum aantal objecten op dat wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d2177-149">**Max-substrings** does not specify the maximum number of objects that are returned.</span></span> <span data-ttu-id="d2177-150">De waarde is gelijk aan het maximum aantal keren dat een teken reeks wordt gesplitst.</span><span class="sxs-lookup"><span data-stu-id="d2177-150">Its value equals the maximum number of times that a string is split.</span></span>
<span data-ttu-id="d2177-151">Als u meer dan één teken reeks (een matrix met teken reeksen) naar de `-split` operator verzendt, wordt de limiet voor de **maximale subtekenreeksen** voor elke teken reeks afzonderlijk toegepast.</span><span class="sxs-lookup"><span data-stu-id="d2177-151">If you submit more than one string (an array of strings) to the `-split` operator, the **Max-substrings** limit is applied to each string separately.</span></span>

<span data-ttu-id="d2177-152">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2177-152">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```Output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", -5
```

```Output
Mercury,Venus,Earth,Mars
Jupiter
Saturn
Uranus
Neptune
```

### \<ScriptBlock\>

<span data-ttu-id="d2177-153">Een expressie waarmee de regels voor het Toep assen van het scheidings teken worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d2177-153">An expression that specifies rules for applying the delimiter.</span></span> <span data-ttu-id="d2177-154">De expressie moet $true of $false evalueren.</span><span class="sxs-lookup"><span data-stu-id="d2177-154">The expression must evaluate to $true or $false.</span></span> <span data-ttu-id="d2177-155">Plaats het script blok tussen accolades.</span><span class="sxs-lookup"><span data-stu-id="d2177-155">Enclose the script block in braces.</span></span>

<span data-ttu-id="d2177-156">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2177-156">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```Output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

<span data-ttu-id="d2177-157">Plaats de naam van de optie tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="d2177-157">Enclose the option name in quotation marks.</span></span> <span data-ttu-id="d2177-158">Opties zijn alleen geldig wanneer de \<Max-substrings\> para meter wordt gebruikt in de instructie.</span><span class="sxs-lookup"><span data-stu-id="d2177-158">Options are valid only when the \<Max-substrings\> parameter is used in the statement.</span></span>

<span data-ttu-id="d2177-159">De syntaxis voor de para meter Options is:</span><span class="sxs-lookup"><span data-stu-id="d2177-159">The syntax for the Options parameter is:</span></span>

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

<span data-ttu-id="d2177-160">De SimpleMatch-opties zijn:</span><span class="sxs-lookup"><span data-stu-id="d2177-160">The SimpleMatch options are:</span></span>

- <span data-ttu-id="d2177-161">**SimpleMatch** : gebruik eenvoudige teken reeks vergelijking bij het evalueren van het scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="d2177-161">**SimpleMatch** : Use simple string comparison when evaluating the delimiter.</span></span> <span data-ttu-id="d2177-162">Kan niet worden gebruikt met RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="d2177-162">Cannot be used with RegexMatch.</span></span>
- <span data-ttu-id="d2177-163">**IgnoreCase** : dwingt niet-hoofdletter gevoelige overeenkomst af, zelfs als de operator-cSplit is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d2177-163">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>

<span data-ttu-id="d2177-164">De RegexMatch-opties zijn:</span><span class="sxs-lookup"><span data-stu-id="d2177-164">The RegexMatch options are:</span></span>

- <span data-ttu-id="d2177-165">**RegexMatch** : gebruik reguliere expressie matching om het scheidings teken te evalueren.</span><span class="sxs-lookup"><span data-stu-id="d2177-165">**RegexMatch** : Use regular expression matching to evaluate the delimiter.</span></span> <span data-ttu-id="d2177-166">Dit is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="d2177-166">This is the default behavior.</span></span> <span data-ttu-id="d2177-167">Kan niet worden gebruikt met SimpleMatch.</span><span class="sxs-lookup"><span data-stu-id="d2177-167">Cannot be used with SimpleMatch.</span></span>
- <span data-ttu-id="d2177-168">**IgnoreCase** : dwingt niet-hoofdletter gevoelige overeenkomst af, zelfs als de operator-cSplit is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d2177-168">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>
- <span data-ttu-id="d2177-169">**CultureInvariant** : negeert culturele verschillen in taal wanneer het scheidings teken wordt evaluting.</span><span class="sxs-lookup"><span data-stu-id="d2177-169">**CultureInvariant** : Ignores cultural differences in language when evaluting the delimiter.</span></span> <span data-ttu-id="d2177-170">Alleen geldig voor RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="d2177-170">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="d2177-171">**IgnorePatternWhitespace** : negeert witruimte zonder escape-teken en opmerkingen met het hekje (#).</span><span class="sxs-lookup"><span data-stu-id="d2177-171">**IgnorePatternWhitespace** : Ignores unescaped whitespace and comments marked with the number sign (#).</span></span> <span data-ttu-id="d2177-172">Alleen geldig voor RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="d2177-172">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="d2177-173">**Meerdere** regels: de modus `^` voor meerdere regels en `$` het begin einde van elke regel wordt vergeleken in plaats van het begin en het einde van de invoer teken reeks.</span><span class="sxs-lookup"><span data-stu-id="d2177-173">**Multiline** : Multiline mode forces `^` and `$` to match the beginning end of every line instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="d2177-174">**Modus singleline** : de modus singleline-modus behandelt de invoer teken reeks als een *modus singleline*.</span><span class="sxs-lookup"><span data-stu-id="d2177-174">**Singleline** : Singleline mode treats the input string as a *SingleLine*.</span></span>
  <span data-ttu-id="d2177-175">Hiermee wordt het `.` teken afgedwongen dat overeenkomt met elk teken (inclusief nieuwe regels), in plaats van elk teken te vergelijken met de nieuwe regel `\n` .</span><span class="sxs-lookup"><span data-stu-id="d2177-175">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>
- <span data-ttu-id="d2177-176">**ExplicitCapture** : negeert niet-benoemde overeenkomende groepen, zodat alleen expliciete opname groepen worden geretourneerd in de lijst met resultaten.</span><span class="sxs-lookup"><span data-stu-id="d2177-176">**ExplicitCapture** : Ignores non-named match groups so that only explicit capture groups are returned in the result list.</span></span> <span data-ttu-id="d2177-177">Alleen geldig voor RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="d2177-177">Valid only with RegexMatch.</span></span>

## <a name="unary-and-binary-split-operators"></a><span data-ttu-id="d2177-178">Unaire en binaire SPLITs Opera tors</span><span class="sxs-lookup"><span data-stu-id="d2177-178">UNARY and BINARY SPLIT OPERATORS</span></span>

<span data-ttu-id="d2177-179">De unaire Splits operator ( `-split <string>` ) heeft een hogere prioriteit dan een komma.</span><span class="sxs-lookup"><span data-stu-id="d2177-179">The unary split operator (`-split <string>`) has higher precedence than a comma.</span></span> <span data-ttu-id="d2177-180">Als u dus een door komma's gescheiden lijst met teken reeksen verzendt naar de operator unsplit, wordt alleen de eerste teken reeks (vóór de eerste komma) gesplitst.</span><span class="sxs-lookup"><span data-stu-id="d2177-180">As a result, if you submit a comma-separated list of strings to the unary split operator, only the first string (before the first comma) is split.</span></span>

<span data-ttu-id="d2177-181">Gebruik een van de volgende patronen om meer dan één teken reeks te splitsen:</span><span class="sxs-lookup"><span data-stu-id="d2177-181">Use one of the following patterns to split more than one string:</span></span>

- <span data-ttu-id="d2177-182">De binaire Splits operator ( \<string[]\> -Split \<delimiter\> ) gebruiken</span><span class="sxs-lookup"><span data-stu-id="d2177-182">Use the binary split operator (\<string[]\> -split \<delimiter\>)</span></span>
- <span data-ttu-id="d2177-183">Alle teken reeksen tussen haakjes plaatsen</span><span class="sxs-lookup"><span data-stu-id="d2177-183">Enclose all the strings in parentheses</span></span>
- <span data-ttu-id="d2177-184">De teken reeksen in een variabele opslaan en vervolgens de variabele naar de Splits operator verzenden</span><span class="sxs-lookup"><span data-stu-id="d2177-184">Store the strings in a variable then submit the variable to the split operator</span></span>

<span data-ttu-id="d2177-185">Kijk eens naar het volgende voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2177-185">Consider the following example:</span></span>

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

## <a name="examples"></a><span data-ttu-id="d2177-186">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d2177-186">EXAMPLES</span></span>

<span data-ttu-id="d2177-187">De volgende instructie splitst de teken reeks op een spatie.</span><span class="sxs-lookup"><span data-stu-id="d2177-187">The following statement splits the string at whitespace.</span></span>

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```Output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

<span data-ttu-id="d2177-188">De volgende instructie splitst de teken reeks op een wille keurige komma.</span><span class="sxs-lookup"><span data-stu-id="d2177-188">The following statement splits the string at any comma.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```Output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

<span data-ttu-id="d2177-189">Met de volgende instructie wordt de teken reeks in het patroon ' er ' gesplitst.</span><span class="sxs-lookup"><span data-stu-id="d2177-189">The following statement splits the string at the pattern "er".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```Output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

<span data-ttu-id="d2177-190">De volgende instructie voert een hoofdletter gevoelige splitsing uit op de letter "N".</span><span class="sxs-lookup"><span data-stu-id="d2177-190">The following statement performs a case-sensitive split at the letter "N".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```Output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

<span data-ttu-id="d2177-191">Met de volgende instructie wordt de teken reeks op ' e ' en ' t ' gesplitst.</span><span class="sxs-lookup"><span data-stu-id="d2177-191">The following statement splits the string at "e" and "t".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```Output
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

<span data-ttu-id="d2177-192">Met de volgende instructie wordt de teken reeks op ' e ' en ' r ' gesplitst, maar worden de resulterende subtekenreeksen beperkt tot zes subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d2177-192">The following statement splits the string at "e" and "r", but limits the resulting substrings to six substrings.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```Output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

<span data-ttu-id="d2177-193">Met de volgende instructie wordt een teken reeks gesplitst in drie subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d2177-193">The following statement splits a string into three substrings.</span></span>

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```Output
a
b
c,d,e,f,g,h
```

<span data-ttu-id="d2177-194">Met de volgende instructie wordt een teken reeks gesplitst in drie subtekenreeksen vanaf het einde van de teken reeks.</span><span class="sxs-lookup"><span data-stu-id="d2177-194">The following statement splits a string into three substrings starting from the end of the string.</span></span>

```powershell
"a,b,c,d,e,f,g,h" -split ",", -3
```

```Output
a,b,c,d,e,f
g
h
```

<span data-ttu-id="d2177-195">Met de volgende instructie splitst u twee teken reeksen in drie subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d2177-195">The following statement splits two strings into three substrings.</span></span>
<span data-ttu-id="d2177-196">(De limiet wordt afzonderlijk toegepast op elke teken reeks.)</span><span class="sxs-lookup"><span data-stu-id="d2177-196">(The limit is applied to each string independently.)</span></span>

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```Output
a
b
c,d
e
f
g,h
```

<span data-ttu-id="d2177-197">Met de volgende instructie wordt elke regel in de teken reeks in het eerste cijfer gesplitst.</span><span class="sxs-lookup"><span data-stu-id="d2177-197">The following statement splits each line in the here-string at the first digit.</span></span> <span data-ttu-id="d2177-198">De optie voor meerdere regels wordt gebruikt om het begin van elke regel en teken reeks te herkennen.</span><span class="sxs-lookup"><span data-stu-id="d2177-198">It uses the Multiline option to recognize the beginning of each line and string.</span></span>

<span data-ttu-id="d2177-199">De 0 vertegenwoordigt de waarde ' return all ' van de para meter Max-subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d2177-199">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="d2177-200">U kunt opties, zoals meerregelige, alleen gebruiken wanneer de waarde voor de Max-subtekenreeksen is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d2177-200">You can use options, such as Multiline, only when the Max-substrings value is specified.</span></span>

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```Output

The first line.

The second line.

The third of three lines.
```

<span data-ttu-id="d2177-201">In de volgende instructie wordt de back slash gebruikt om het punt scheidings teken (.) te escapen.</span><span class="sxs-lookup"><span data-stu-id="d2177-201">The following statement uses the backslash character to escape the dot (.) delimiter.</span></span>

<span data-ttu-id="d2177-202">Met de standaard waarde RegexMatch, de punt tussen aanhalings tekens (".") wordt geïnterpreteerd zodat deze overeenkomt met een wille keurig teken behalve een nieuwe regel.</span><span class="sxs-lookup"><span data-stu-id="d2177-202">With the default, RegexMatch, the dot enclosed in quotation marks (".") is interpreted to match any character except for a newline character.</span></span> <span data-ttu-id="d2177-203">Als gevolg hiervan retourneert de gesplitste instructie een lege regel voor elk teken behalve een nieuwe voor waarde.</span><span class="sxs-lookup"><span data-stu-id="d2177-203">As a result, the Split statement returns a blank line for every character except newline.</span></span>

```powershell
"This.is.a.test" -split "\."
```

```Output
This
is
a
test
```

<span data-ttu-id="d2177-204">De volgende instructie maakt gebruik van de SimpleMatch-optie om de operator-split te sturen om het punt scheidings teken letterlijk te interpreteren.</span><span class="sxs-lookup"><span data-stu-id="d2177-204">The following statement uses the SimpleMatch option to direct the -split operator to interpret the dot (.) delimiter literally.</span></span>

<span data-ttu-id="d2177-205">De 0 vertegenwoordigt de waarde ' return all ' van de para meter Max-subtekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d2177-205">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="d2177-206">U kunt opties, zoals SimpleMatch, alleen gebruiken wanneer de waarde voor de Max-subtekenreeksen is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d2177-206">You can use options, such as SimpleMatch, only when the Max-substrings value is specified.</span></span>

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```Output
This
is
a
test
```

<span data-ttu-id="d2177-207">Met de volgende instructie wordt de teken reeks in een van de twee scheidings tekens gesplitst, afhankelijk van de waarde van een variabele.</span><span class="sxs-lookup"><span data-stu-id="d2177-207">The following statement splits the string at one of two delimiters, depending on the value of a variable.</span></span>

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```Output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a><span data-ttu-id="d2177-208">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="d2177-208">SEE ALSO</span></span>

[<span data-ttu-id="d2177-209">Split-pad</span><span class="sxs-lookup"><span data-stu-id="d2177-209">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)

[<span data-ttu-id="d2177-210">about_Operators</span><span class="sxs-lookup"><span data-stu-id="d2177-210">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="d2177-211">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="d2177-211">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="d2177-212">about_Join</span><span class="sxs-lookup"><span data-stu-id="d2177-212">about_Join</span></span>](about_Join.md)
