---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convert-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-String
ms.openlocfilehash: 29ec9e21277bae02ab94ce5e862787c86a87b439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250480"
---
# <span data-ttu-id="f615b-103">Convert-String</span><span class="sxs-lookup"><span data-stu-id="f615b-103">Convert-String</span></span>

## <span data-ttu-id="f615b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f615b-104">SYNOPSIS</span></span>
<span data-ttu-id="f615b-105">Hiermee wordt een teken reeks opgemaakt die overeenkomt met voor beelden.</span><span class="sxs-lookup"><span data-stu-id="f615b-105">Formats a string to match examples.</span></span>

## <span data-ttu-id="f615b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f615b-106">SYNTAX</span></span>

```
Convert-String [-Example <System.Collections.Generic.List`1[System.Management.Automation.PSObject]>]
 -InputObject <String> [<CommonParameters>]
```

## <span data-ttu-id="f615b-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f615b-107">DESCRIPTION</span></span>

<span data-ttu-id="f615b-108">Met de cmdlet **Convert-string** wordt een teken reeks opgemaakt die overeenkomt met de indeling van voor beelden.</span><span class="sxs-lookup"><span data-stu-id="f615b-108">The **Convert-String** cmdlet formats a string to match the format of examples.</span></span>

## <span data-ttu-id="f615b-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f615b-109">EXAMPLES</span></span>

### <span data-ttu-id="f615b-110">Voor beeld 1: indeling van een teken reeks converteren</span><span class="sxs-lookup"><span data-stu-id="f615b-110">Example 1: Convert format of a string</span></span>

```powershell
"Mu Han", "Jim Hance", "David Ahs", "Kim Akers" | Convert-String -Example "Ed Wilson=Wilson, E."
```

```output
Han, M.
Hance, J.
Ahs, D.
Akers, K.
```

<span data-ttu-id="f615b-111">Met de eerste opdracht maakt u een matrix die de voor-en achternaam bevat.</span><span class="sxs-lookup"><span data-stu-id="f615b-111">The first command creates an array that contains first and last names.</span></span>

<span data-ttu-id="f615b-112">Met de tweede opdracht worden de namen op basis van het voor beeld opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="f615b-112">The second command formats the names according to the example.</span></span>
<span data-ttu-id="f615b-113">De achternaam wordt eerst in de uitvoer geplaatst, gevolgd door een eerste.</span><span class="sxs-lookup"><span data-stu-id="f615b-113">It puts the surname first in the output, followed by an initial.</span></span>

### <span data-ttu-id="f615b-114">Voor beeld 2: de indeling van een teken reeks vereenvoudigen</span><span class="sxs-lookup"><span data-stu-id="f615b-114">Example 2: Simplify format of a string</span></span>

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=last, first"
```

```output
Bach, Johann
Mozart, Wolfgang
Chopin, Frederic
Brahms, Johannes
```

<span data-ttu-id="f615b-115">Met de eerste opdracht maakt u een matrix die de eerste, middelste en achternaam bevat.</span><span class="sxs-lookup"><span data-stu-id="f615b-115">The first command creates an array that contains first, middle and last names.</span></span>
<span data-ttu-id="f615b-116">Houd er rekening mee dat de laatste vermelding geen middelste naam heeft.</span><span class="sxs-lookup"><span data-stu-id="f615b-116">Note that the last entry has no middle name.</span></span>

<span data-ttu-id="f615b-117">Met de tweede opdracht worden de namen op basis van het voor beeld opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="f615b-117">The second command formats the names according to the example.</span></span>
<span data-ttu-id="f615b-118">De laatste naam wordt eerst in de uitvoer geplaatst, gevolgd door de voor naam.</span><span class="sxs-lookup"><span data-stu-id="f615b-118">It puts the last name first in the output, followed by the first name.</span></span>
<span data-ttu-id="f615b-119">Alle middelste namen worden verwijderd. invoer zonder middelste naam wordt correct afgehandeld.</span><span class="sxs-lookup"><span data-stu-id="f615b-119">All middle names removed; entry without middle name is handled correctly.</span></span>

### <span data-ttu-id="f615b-120">Voor beeld 3: uitvoer beheer als teken reeksen niet overeenkomen met voor beeld</span><span class="sxs-lookup"><span data-stu-id="f615b-120">Example 3: Output management when strings don't match example</span></span>

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=middle, first"
```

```output
Sebastian, Johann
Amadeus, Wolfgang
Francois, Frederic
```

<span data-ttu-id="f615b-121">Met de eerste opdracht maakt u een matrix die de eerste, middelste en achternaam bevat.</span><span class="sxs-lookup"><span data-stu-id="f615b-121">The first command creates an array that contains first, middle and last names.</span></span>
<span data-ttu-id="f615b-122">Houd er rekening mee dat de laatste vermelding geen middelste naam heeft.</span><span class="sxs-lookup"><span data-stu-id="f615b-122">Note that the last entry has no middle name.</span></span>

<span data-ttu-id="f615b-123">Met de tweede opdracht worden de namen op basis van het voor beeld opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="f615b-123">The second command formats the names according to the example.</span></span>
<span data-ttu-id="f615b-124">De **tweede naam** wordt eerst in de uitvoer geplaatst, gevolgd door de voor naam.</span><span class="sxs-lookup"><span data-stu-id="f615b-124">It puts the **middle name** first in the output, followed by the first name.</span></span>
<span data-ttu-id="f615b-125">De laatste vermelding in **$Composers** wordt overgeslagen, omdat deze niet overeenkomt met het voorbeeld patroon: er is geen middelste naam.</span><span class="sxs-lookup"><span data-stu-id="f615b-125">The last entry in **$Composers** is skipped, because it doesn't match the sample pattern: it has no middle name.</span></span>

### <span data-ttu-id="f615b-126">Voor beeld 4: waarschuwing met mooie Spaces</span><span class="sxs-lookup"><span data-stu-id="f615b-126">Example 4: Caution with beauty spaces</span></span>

```powershell
$composers = @("Antonio Vivaldi", "Richard Wagner ", "Franz Schubert", "Johannes Brahms ")
$composers | Convert-String -Example "Patti Fuller = Fuller, P."
```

```output
 Wagner, R.
 Brahms, J.
```

<span data-ttu-id="f615b-127">Met de eerste opdracht maakt u een matrix met de voor-en achternaam.</span><span class="sxs-lookup"><span data-stu-id="f615b-127">The first command creates an array of first and last names.</span></span>
<span data-ttu-id="f615b-128">Houd er rekening mee dat tweede en vierde items een extra spatie hebben na de achternaam.</span><span class="sxs-lookup"><span data-stu-id="f615b-128">Note that second and fourth items have an extra trailing space, after the last name.</span></span>

<span data-ttu-id="f615b-129">Met de tweede opdracht worden alle teken reeksen die overeenkomen met het voorbeeld patroon geconverteerd: _woord, spatie, woord en laatste Volg spatie_ , alle voor het gelijkteken.</span><span class="sxs-lookup"><span data-stu-id="f615b-129">The second command converts all strings that match the sample pattern: _word, space, word, and final trailing space_ , all of this before the equal sign.</span></span>
<span data-ttu-id="f615b-130">Let ook op de voorloop ruimte in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f615b-130">Also, note the leading space in the output.</span></span>

### <span data-ttu-id="f615b-131">Voor beeld 5: proces gegevens opmaken met meerdere patronen</span><span class="sxs-lookup"><span data-stu-id="f615b-131">Example 5: Format process information with multiple patterns</span></span>

```powershell
$ExamplePatterns = @(
    @{before='"Hello","World"'; after='World: Hello'},
    @{before='"Hello","1"'; after='1: Hello'},
    @{before='"Hello-World","22"'; after='22: Hello-World'},
    @{before='"hello world","333"'; after='333: hello world'}
)
$Processes = Get-Process   | Select-Object -Property ProcessName, Id | ConvertTo-Csv -NoTypeInformation
$Processes | Convert-String -Example $ExamplePatterns
```

```output
Id: ProcessName
4368: AGSService
8896: Amazon Music Helper
4420: AppleMobileDeviceService
...
11140: git-bash
0: Idle
...
56: Secure System
...
13028: WmiPrvSE
2724: WUDFHost
2980: WUDFHost
3348: WUDFHost
```

<span data-ttu-id="f615b-132">**$ExamplePatterns** definieert verschillende verwachte patronen in de gegevens, via voor beelden.</span><span class="sxs-lookup"><span data-stu-id="f615b-132">**$ExamplePatterns** defines different expected patterns in the data, through examples.</span></span>

<span data-ttu-id="f615b-133">Het eerste patroon, `@{before='"Hello","World"'; after='World: Hello'}` , lezen als volgt: er worden _teken reeksen verwacht waarbij een woord tussen dubbele aanhalings tekens, gevolgd door een komma_ 
 _en vervolgens de tweede en laatste woord tussen aanhalings tekens_ is geplaatst. 
 _zonder spaties in de teken reeks. In de uitvoer: plaats het tweede woord eerst,_ 
 _zonder aanhalings tekens, vervolgens één spatie en vervolgens het eerste woord, zonder aanhalings tekens._</span><span class="sxs-lookup"><span data-stu-id="f615b-133">The first pattern, `@{before='"Hello","World"'; after='World: Hello'}`, reads as follows: _expect strings where a word comes enclosed in double quotes, then a comma,_
_and then the second, and last, word enclosed in quotes;_
_with no spaces in the string. On the output: place second word first,_
_without quotes, then a single space, and then the first word, without quotes._</span></span>

<span data-ttu-id="f615b-134">Het tweede patroon, `@{before='"Hello","1"'; after='1: Hello'}` , lezen als volgt: _er worden teken reeksen verwacht waarbij een woord tussen dubbele aanhalings tekens, gevolgd door een komma_ 
 _en een getal tussen aanhalings tekens_ is geplaatst. 
 _zonder spaties in de teken reeks. In de uitvoer: plaats het getal eerst,_ 
 _zonder aanhalings tekens, één spatie en vervolgens het woord, zonder aanhalings tekens._</span><span class="sxs-lookup"><span data-stu-id="f615b-134">The second pattern, `@{before='"Hello","1"'; after='1: Hello'}`, reads as follows: _expect strings where a word comes enclosed in double quotes, then a comma,_
_and then a number enclosed in quotes;_
_with no spaces in the string. On the output: place the number first,_
_without quotes, then a single space, and then the word, without quotes._</span></span>

<span data-ttu-id="f615b-135">Het derde patroon, `@{before='"Hello-World","22"'; after='22: Hello-World'}` , lezen als volgt: _er worden teken reeksen verwacht waarbij twee woorden met een afbreek streepje tussen_ 
 _dubbele aanhalings tekens, gevolgd door een komma en een getal tussen aanhalings tekens staan._ 
 _zonder spaties tussen de komma en de derde dubbele aanhalings tekens._ 
 _In de uitvoer: plaats het getal eerst, zonder aanhalings tekens, vervolgens één spatie,_ 
 _en vervolgens de woord afbreek streepjes, zonder aanhalings tekens._</span><span class="sxs-lookup"><span data-stu-id="f615b-135">The third pattern, `@{before='"Hello-World","22"'; after='22: Hello-World'}`, reads as follows: _expect strings where two words with a hyphen in between come enclosed in_
_double quotes, then a comma, and then a number enclosed in quotes;_
_with no spaces between the comma and the third double quote._
_On the output: place the number first, without quotes, then a single space,_
_and then the hyphenated words, without quotes._</span></span>

<span data-ttu-id="f615b-136">Het vierde en laatste patroon, `@{before='"hello world","333"'; after='333: hello world'}` worden als volgt gelezen: er _worden teken reeksen verwacht waarbij twee woorden met een spatie tussen_ 
 _dubbele aanhalings tekens, gevolgd door een komma en een getal tussen aanhalings tekens staan._ 
 _zonder spaties tussen de komma en de derde dubbele aanhalings tekens._ 
 _In de uitvoer: plaats het getal eerst, zonder aanhalings tekens, vervolgens één spatie,_ 
 _en vervolgens de woorden met de spatie tussen en zonder aanhalings tekens._</span><span class="sxs-lookup"><span data-stu-id="f615b-136">The fourth, and final, pattern, `@{before='"hello world","333"'; after='333: hello world'}`, reads as follows: _expect strings where two words with a space in between come enclosed in_
_double quotes, then a comma, and then a number enclosed in quotes;_
_with no spaces between the comma and the third double quote._
_On the output: place the number first, without quotes, then a single space,_
_and then the words with the space in between, without quotes._</span></span>

<span data-ttu-id="f615b-137">Met de eerste opdracht worden alle processen opgehaald met behulp van de cmdlet Get-Process.</span><span class="sxs-lookup"><span data-stu-id="f615b-137">The first command gets all processes by using the Get-Process cmdlet.</span></span>
<span data-ttu-id="f615b-138">De opdracht geeft deze door aan de cmdlet Select-Object, waarmee de proces naam en proces-ID worden geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="f615b-138">The command passes them to the Select-Object cmdlet, which selects the process name and process ID.</span></span> <span data-ttu-id="f615b-139">Aan het einde van de pijp lijn converteert de opdracht de uitvoer naar door komma's gescheiden waarden, zonder type gegevens, met behulp van de ConvertTo-Csv-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f615b-139">At the end of the pipeline, the command converts the output to comma separated values, without type information, by using the ConvertTo-Csv cmdlet.</span></span>
<span data-ttu-id="f615b-140">Met de opdracht worden de resultaten opgeslagen in de variabele **$processes** .</span><span class="sxs-lookup"><span data-stu-id="f615b-140">The command stores the results in the **$Processes** variable.</span></span>
<span data-ttu-id="f615b-141">**$Processes** bevat nu proces namen en PID.</span><span class="sxs-lookup"><span data-stu-id="f615b-141">**$Processes** now contains process names and PID.</span></span>

<span data-ttu-id="f615b-142">Met de tweede opdracht wordt een voorbeeld variabele opgegeven waarmee de volg orde van de invoer items wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f615b-142">The second command specifies an example variable that changes the order of the input items.</span></span>
<span data-ttu-id="f615b-143">De opdracht keert elke teken reeks om in **$processes**.</span><span class="sxs-lookup"><span data-stu-id="f615b-143">The command coverts each string in **$Processes**.</span></span>

><span data-ttu-id="f615b-144">**Opmerking** Het vierde patroon geeft impliciet aan dat twee of meer woorden die worden gescheiden door spaties, overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="f615b-144">**Note** The fourth pattern implicitly says that two or more words separated by spaces are matched.</span></span>
>
><span data-ttu-id="f615b-145">Zonder het vierde patroon komt alleen het eerste woord van de teken reeks tussen dubbele aanhalings tekens overeen.</span><span class="sxs-lookup"><span data-stu-id="f615b-145">Without the fourth pattern, only the first word of the string enclosed in double quotes is matched.</span></span>

## <span data-ttu-id="f615b-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f615b-146">PARAMETERS</span></span>

### <span data-ttu-id="f615b-147">-Voor beeld</span><span class="sxs-lookup"><span data-stu-id="f615b-147">-Example</span></span>

<span data-ttu-id="f615b-148">Hiermee geeft u een lijst met voor beelden van de doel indeling op.</span><span class="sxs-lookup"><span data-stu-id="f615b-148">Specifies a list of examples of the target format.</span></span>
<span data-ttu-id="f615b-149">Geef paren op, gescheiden door het gelijkteken (=), met het bron patroon aan de linkerkant en het doel patroon aan de rechter kant, zoals in de volgende voor beelden:</span><span class="sxs-lookup"><span data-stu-id="f615b-149">Specify pairs separated by the equal (=) sign, with the source pattern on the left and the target pattern on the right, as in the following examples:</span></span>

* `-Example "Hello World=World, Hello"`
* `-Example "Hello World=World: Hello",'"Hello","1"=1: Hello'`

><span data-ttu-id="f615b-150">**Opmerking** In het tweede voor beeld wordt een lijst met patronen gebruikt</span><span class="sxs-lookup"><span data-stu-id="f615b-150">**Note** The second example uses a list of patterns</span></span>

<span data-ttu-id="f615b-151">U kunt ook een lijst met hash-tabellen opgeven die **vóór** en **na** de eigenschappen bevatten.</span><span class="sxs-lookup"><span data-stu-id="f615b-151">Alternatively, specify a list of hash tables that contain **Before** and **After** properties.</span></span>

* `-Example @{before='"Hello","World"'; after='World: Hello'}, @{before='"Hello","1"'; after='1: Hello'}`

><span data-ttu-id="f615b-152">**Waarschuwing** Vermijd het gebruik van spaties rond het gelijkteken, aangezien deze worden beschouwd als onderdeel van het patroon.</span><span class="sxs-lookup"><span data-stu-id="f615b-152">**Caution** Avoid using spaces around the equal sign, as they are treated as part of the pattern.</span></span>

```yaml
Type: System.Collections.Generic.List`1[System.Management.Automation.PSObject]
Parameter Sets: (All)
Aliases: E

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f615b-153">-Input object</span><span class="sxs-lookup"><span data-stu-id="f615b-153">-InputObject</span></span>

<span data-ttu-id="f615b-154">Geeft een teken reeks op die moet worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="f615b-154">Specifies a string to format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f615b-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f615b-155">CommonParameters</span></span>

<span data-ttu-id="f615b-156">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f615b-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f615b-157">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f615b-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f615b-158">INVOER</span><span class="sxs-lookup"><span data-stu-id="f615b-158">INPUTS</span></span>

### <span data-ttu-id="f615b-159">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="f615b-159">String</span></span>

<span data-ttu-id="f615b-160">U kunt teken reeksen naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="f615b-160">You can pipe strings to this cmdlet.</span></span>

## <span data-ttu-id="f615b-161">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f615b-161">OUTPUTS</span></span>

### <span data-ttu-id="f615b-162">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="f615b-162">String</span></span>

<span data-ttu-id="f615b-163">Met deze cmdlet wordt een teken reeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f615b-163">This cmdlet returns a string.</span></span>

## <span data-ttu-id="f615b-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f615b-164">NOTES</span></span>

## <span data-ttu-id="f615b-165">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f615b-165">RELATED LINKS</span></span>

[<span data-ttu-id="f615b-166">ConvertFrom-teken reeks</span><span class="sxs-lookup"><span data-stu-id="f615b-166">ConvertFrom-String</span></span>](ConvertFrom-String.md)

[<span data-ttu-id="f615b-167">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="f615b-167">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="f615b-168">Get-Process</span><span class="sxs-lookup"><span data-stu-id="f615b-168">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="f615b-169">Out-teken reeks</span><span class="sxs-lookup"><span data-stu-id="f615b-169">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="f615b-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="f615b-170">Select-Object</span></span>](Select-Object.md)
