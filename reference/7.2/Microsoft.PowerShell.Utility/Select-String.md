---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 339afab9c817b54a79e2f1b33b7021ecb4fe6a6e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94704739"
---
# <span data-ttu-id="43469-102">Select-String</span><span class="sxs-lookup"><span data-stu-id="43469-102">Select-String</span></span>

## <span data-ttu-id="43469-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="43469-103">SYNOPSIS</span></span>
<span data-ttu-id="43469-104">Zoeken naar tekst in teken reeksen en bestanden.</span><span class="sxs-lookup"><span data-stu-id="43469-104">Finds text in strings and files.</span></span>

## <span data-ttu-id="43469-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="43469-105">SYNTAX</span></span>

### <span data-ttu-id="43469-106">Bestand (standaard)</span><span class="sxs-lookup"><span data-stu-id="43469-106">File (Default)</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="43469-107">ObjectRaw</span><span class="sxs-lookup"><span data-stu-id="43469-107">ObjectRaw</span></span>

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="43469-108">Object</span><span class="sxs-lookup"><span data-stu-id="43469-108">Object</span></span>

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="43469-109">FileRaw</span><span class="sxs-lookup"><span data-stu-id="43469-109">FileRaw</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="43469-110">LiteralFileRaw</span><span class="sxs-lookup"><span data-stu-id="43469-110">LiteralFileRaw</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="43469-111">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="43469-111">LiteralFile</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="43469-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="43469-112">DESCRIPTION</span></span>

<span data-ttu-id="43469-113">De `Select-String` cmdlet zoekt naar tekst-en tekst patronen in invoer teken reeksen en bestanden.</span><span class="sxs-lookup"><span data-stu-id="43469-113">The `Select-String` cmdlet searches for text and text patterns in input strings and files.</span></span> <span data-ttu-id="43469-114">U kunt `Select-String` vergelijkbaar met **grep** gebruiken in UNIX of **findstr.exe** in Windows.</span><span class="sxs-lookup"><span data-stu-id="43469-114">You can use `Select-String` similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="43469-115">`Select-String` is gebaseerd op regels tekst.</span><span class="sxs-lookup"><span data-stu-id="43469-115">`Select-String` is based on lines of text.</span></span> <span data-ttu-id="43469-116">Standaard `Select-String` zoekt de eerste overeenkomst op elke regel en, voor elke overeenkomst, worden de bestands naam, het regel nummer en alle tekst in de regel met de overeenkomst weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43469-116">By default, `Select-String` finds the first match in each line and, for each match, it displays the file name, line number, and all text in the line containing the match.</span></span> <span data-ttu-id="43469-117">U kunt direct `Select-String` zoeken naar meerdere overeenkomsten per regel, tekst weer geven voor en na de overeenkomst of een Booleaanse waarde (waar of onwaar) weer geven die aangeeft of er een overeenkomst is gevonden.</span><span class="sxs-lookup"><span data-stu-id="43469-117">You can direct `Select-String` to find multiple matches per line, display text before and after the match, or display a Boolean value (True or False) that indicates whether a match is found.</span></span>

<span data-ttu-id="43469-118">`Select-String` maakt gebruik van reguliere expressie matching, maar kan ook een overeenkomst uitvoeren die de invoer doorzoekt voor de tekst die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="43469-118">`Select-String` uses regular expression matching, but it can also perform a match that searches the input for the text that you specify.</span></span>

<span data-ttu-id="43469-119">`Select-String` kan alle tekst overeenkomsten weer geven of stoppen na de eerste overeenkomst in elk invoer bestand.</span><span class="sxs-lookup"><span data-stu-id="43469-119">`Select-String` can display all the text matches or stop after the first match in each input file.</span></span>
<span data-ttu-id="43469-120">`Select-String` kan worden gebruikt om alle tekst weer te geven die niet overeenkomt met het opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="43469-120">`Select-String` can be used to display all text that doesn't match the specified pattern.</span></span>

<span data-ttu-id="43469-121">U kunt ook opgeven dat `Select-String` een bepaalde teken codering moet worden verwacht, bijvoorbeeld wanneer u bestanden van Unicode-tekst zoekt.</span><span class="sxs-lookup"><span data-stu-id="43469-121">You can also specify that `Select-String` should expect a particular character encoding, such as when you're searching files of Unicode text.</span></span> <span data-ttu-id="43469-122">`Select-String` maakt gebruik van de byte-order-Mark (BOM) om de coderings indeling van het bestand te detecteren.</span><span class="sxs-lookup"><span data-stu-id="43469-122">`Select-String` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="43469-123">Als het bestand geen stuk lijst heeft, wordt ervan uitgegaan dat de code ring UTF8 is.</span><span class="sxs-lookup"><span data-stu-id="43469-123">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="43469-124">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="43469-124">EXAMPLES</span></span>

### <span data-ttu-id="43469-125">Voor beeld 1: een hoofdletter gevoelige overeenkomst zoeken</span><span class="sxs-lookup"><span data-stu-id="43469-125">Example 1: Find a case-sensitive match</span></span>

<span data-ttu-id="43469-126">In dit voor beeld is een hoofdletter gevoelige overeenkomst van de tekst die de pijp lijn naar de cmdlet heeft verzonden `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="43469-126">This example does a case-sensitive match of the text that was sent down the pipeline to the `Select-String` cmdlet.</span></span>

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

<span data-ttu-id="43469-127">De tekst teken reeksen **Hello** en **Hello** worden in de pijp lijn naar de `Select-String` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="43469-127">The text strings **Hello** and **HELLO** are sent down the pipeline to the `Select-String` cmdlet.</span></span>
<span data-ttu-id="43469-128">`Select-String` maakt gebruik van de para meter **pattern** om **Hello** op te geven.</span><span class="sxs-lookup"><span data-stu-id="43469-128">`Select-String` uses the **Pattern** parameter to specify **HELLO**.</span></span> <span data-ttu-id="43469-129">De para meter **CaseSensitive** geeft aan dat de case alleen moet overeenkomen met het hoofd-hoofdletter patroon.</span><span class="sxs-lookup"><span data-stu-id="43469-129">The **CaseSensitive** parameter specifies that the case must match only the upper-case pattern.</span></span> <span data-ttu-id="43469-130">**SimpleMatch** is een optionele para meter en geeft aan dat de teken reeks in het patroon niet wordt geïnterpreteerd als een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="43469-130">**SimpleMatch** is an optional parameter and specifies that the string in the pattern isn't interpreted as a regular expression.</span></span>
<span data-ttu-id="43469-131">`Select-String` Hiermee wordt **Hello** weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="43469-131">`Select-String` displays **HELLO** in the PowerShell console.</span></span>

### <span data-ttu-id="43469-132">Voor beeld 2: overeenkomsten zoeken in tekst bestanden</span><span class="sxs-lookup"><span data-stu-id="43469-132">Example 2: Find matches in text files</span></span>

<span data-ttu-id="43469-133">Met deze opdracht worden alle bestanden `.txt` in de huidige map doorzocht met de bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="43469-133">This command searches all files with the `.txt` file name extension in the current directory.</span></span> <span data-ttu-id="43469-134">In de uitvoer worden de regels in die bestanden weer gegeven die de opgegeven teken reeks bevatten.</span><span class="sxs-lookup"><span data-stu-id="43469-134">The output displays the lines in those files that include the specified string.</span></span>

```powershell
Get-Alias | Out-File -FilePath .\Alias.txt
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\*.txt -Pattern 'Get-'
```

```Output
Alias.txt:8:Alias            cat -> Get-Content
Alias.txt:28:Alias           dir -> Get-ChildItem
Alias.txt:43:Alias           gal -> Get-Alias
Command.txt:966:Cmdlet       Get-Acl
Command.txt:967:Cmdlet       Get-Alias
```

<span data-ttu-id="43469-135">In dit voor beeld `Get-Alias` wordt `Get-Command` met de `Out-File` cmdlet twee tekst bestanden gemaakt in de huidige map **Alias.txt** en **Command.txt**.</span><span class="sxs-lookup"><span data-stu-id="43469-135">In this example, `Get-Alias` and `Get-Command` are used with the `Out-File` cmdlet to create two text files in the current directory, **Alias.txt** and **Command.txt**.</span></span>

<span data-ttu-id="43469-136">`Select-String` gebruikt de para meter **Path** met het `*` Joker teken sterretje () om alle bestanden in de huidige map te doorzoeken met de bestandsnaam extensie `.txt` .</span><span class="sxs-lookup"><span data-stu-id="43469-136">`Select-String` uses the **Path** parameter with the asterisk (`*`) wildcard to search all files in the current directory with the file name extension `.txt`.</span></span> <span data-ttu-id="43469-137">De **pattern** -para meter geeft de tekst op die moet overeenkomen met **Get-**.</span><span class="sxs-lookup"><span data-stu-id="43469-137">The **Pattern** parameter specifies the text to match **Get-**.</span></span> <span data-ttu-id="43469-138">`Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43469-138">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="43469-139">De bestands naam en het regel nummer vóór elke regel met inhoud die overeenkomt met de **patroon** parameter.</span><span class="sxs-lookup"><span data-stu-id="43469-139">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="43469-140">Voor beeld 3: zoeken naar een patroon overeenkomst</span><span class="sxs-lookup"><span data-stu-id="43469-140">Example 3: Find a pattern match</span></span>

<span data-ttu-id="43469-141">In dit voor beeld worden meerdere bestanden doorzocht om overeenkomsten te vinden voor het opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="43469-141">In this example, multiple files are searched to find matches for the specified pattern.</span></span> <span data-ttu-id="43469-142">Het patroon gebruikt een reguliere expressie-kwantor.</span><span class="sxs-lookup"><span data-stu-id="43469-142">The pattern uses a regular expression quantifier.</span></span> <span data-ttu-id="43469-143">Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="43469-143">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span></span>

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

<span data-ttu-id="43469-144">De `Select-String` cmdlet gebruikt twee para meters, **pad** en **patroon**.</span><span class="sxs-lookup"><span data-stu-id="43469-144">The `Select-String` cmdlet uses two parameters, **Path** and **Pattern**.</span></span> <span data-ttu-id="43469-145">De para meter **Path** maakt gebruik van de variabele `$PSHOME` die de Power shell-map opgeeft.</span><span class="sxs-lookup"><span data-stu-id="43469-145">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="43469-146">De rest van het pad bevat de submap en **-US** en geeft elk `*.txt` bestand in de map op.</span><span class="sxs-lookup"><span data-stu-id="43469-146">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="43469-147">De **patroon** parameter geeft aan dat deze overeenkomt met een vraag teken ( `?` ) in elk bestand.</span><span class="sxs-lookup"><span data-stu-id="43469-147">The **Pattern** parameter specifies to match a question mark (`?`) in each file.</span></span> <span data-ttu-id="43469-148">Een back slash ( `\` ) wordt gebruikt als escape-teken en is nodig omdat het vraag teken ( `?` ) een reguliere expressie-kwantor is.</span><span class="sxs-lookup"><span data-stu-id="43469-148">A backslash (`\`) is used as an escape character and is necessary because the question mark (`?`) is a regular expression quantifier.</span></span> <span data-ttu-id="43469-149">`Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43469-149">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="43469-150">De bestands naam en het regel nummer vóór elke regel met inhoud die overeenkomt met de **patroon** parameter.</span><span class="sxs-lookup"><span data-stu-id="43469-150">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="43469-151">Voor beeld 4: Select-String gebruiken in een functie</span><span class="sxs-lookup"><span data-stu-id="43469-151">Example 4: Use Select-String in a function</span></span>

<span data-ttu-id="43469-152">In dit voor beeld wordt een functie gemaakt om te zoeken naar een patroon in de Help-bestanden van Power shell.</span><span class="sxs-lookup"><span data-stu-id="43469-152">This example creates a function to search for a pattern in the PowerShell help files.</span></span> <span data-ttu-id="43469-153">Voor dit voor beeld is de functie alleen aanwezig in de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="43469-153">For this example, the function only exists in the PowerShell session.</span></span> <span data-ttu-id="43469-154">Wanneer de Power shell-sessie is gesloten, wordt de functie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="43469-154">When the PowerShell session is closed, the function is deleted.</span></span> <span data-ttu-id="43469-155">Zie [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="43469-155">For more information, see [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span></span>

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Program Files\PowerShell\6\en-US\default.help.txt:67:    The titles of conceptual topics begin with "About_".
C:\Program Files\PowerShell\6\en-US\default.help.txt:70:    Get-Help About_<topic-name>
C:\Program Files\PowerShell\6\en-US\default.help.txt:93:    Get-Help About_Modules : Displays help about PowerShell modules.
C:\Program Files\PowerShell\6\en-US\default.help.txt:97:    about_Updatable_Help
```

<span data-ttu-id="43469-156">De functie wordt gemaakt op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="43469-156">The function is created on the PowerShell command line.</span></span> <span data-ttu-id="43469-157">De `Function` opdracht maakt gebruik van de naam **zoeken-Help**.</span><span class="sxs-lookup"><span data-stu-id="43469-157">The `Function` command uses the name **Search-Help**.</span></span> <span data-ttu-id="43469-158">Druk op **Enter** om instructies toe te voegen aan de functie.</span><span class="sxs-lookup"><span data-stu-id="43469-158">Press **Enter** to begin adding statements to the function.</span></span> <span data-ttu-id="43469-159">Voeg bij de `>>` prompt elke instructie toe en druk op **Enter** , zoals wordt weer gegeven in het voor beeld.</span><span class="sxs-lookup"><span data-stu-id="43469-159">From the `>>` prompt, add each statement and press **Enter** as shown in the example.</span></span> <span data-ttu-id="43469-160">Nadat het haakje is toegevoegd, keert u terug naar een Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="43469-160">After the closing bracket is added, you're returned to a PowerShell prompt.</span></span>

<span data-ttu-id="43469-161">De functie bevat twee opdrachten.</span><span class="sxs-lookup"><span data-stu-id="43469-161">The function contains two commands.</span></span> <span data-ttu-id="43469-162">De `$PSHelp` variabele slaat het pad op naar de Help-bestanden van Power shell.</span><span class="sxs-lookup"><span data-stu-id="43469-162">The `$PSHelp` variable stores the path to the PowerShell help files.</span></span> <span data-ttu-id="43469-163">`$PSHOME` is de Power shell-installatiemap met de submap **en-US** waarmee elk `*.txt` bestand in de Directory wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="43469-163">`$PSHOME` is the PowerShell installation directory with the subdirectory **en-US** that specifies each `*.txt` file in the directory.</span></span>

<span data-ttu-id="43469-164">De `Select-String` opdracht in de functie maakt gebruik van het **pad** en de **patroon** parameters.</span><span class="sxs-lookup"><span data-stu-id="43469-164">The `Select-String` command in the function uses the **Path** and **Pattern** parameters.</span></span> <span data-ttu-id="43469-165">De para meter **Path** gebruikt de `$PSHelp` variabele om het pad op te halen.</span><span class="sxs-lookup"><span data-stu-id="43469-165">The **Path** parameter uses the `$PSHelp` variable to get the path.</span></span> <span data-ttu-id="43469-166">De **patroon** parameter maakt gebruik van de teken reeks **About_** als Zoek criterium.</span><span class="sxs-lookup"><span data-stu-id="43469-166">The **Pattern** parameter uses the string **About_** as the search criteria.</span></span>

<span data-ttu-id="43469-167">Als u de functie wilt uitvoeren, typt u `Search-Help` .</span><span class="sxs-lookup"><span data-stu-id="43469-167">To run the function, type `Search-Help`.</span></span> <span data-ttu-id="43469-168">De opdracht van de functie `Select-String` geeft de uitvoer in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="43469-168">The function's `Select-String` command displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="43469-169">Voor beeld 5: zoeken naar een teken reeks in een Windows-gebeurtenis logboek</span><span class="sxs-lookup"><span data-stu-id="43469-169">Example 5: Search for a string in a Windows event log</span></span>

<span data-ttu-id="43469-170">In dit voor beeld wordt gezocht naar een teken reeks in een Windows-gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="43469-170">This example searches for a string in a Windows event log.</span></span> <span data-ttu-id="43469-171">De variabele `$_` vertegenwoordigt het huidige object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="43469-171">The variable `$_` represents the current object in the pipeline.</span></span> <span data-ttu-id="43469-172">Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="43469-172">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

<span data-ttu-id="43469-173">De `Get-WinEvent` cmdlet gebruikt de para meter **LogName** om het toepassings logboek op te geven.</span><span class="sxs-lookup"><span data-stu-id="43469-173">The `Get-WinEvent` cmdlet uses the **LogName** parameter to specify the Application log.</span></span> <span data-ttu-id="43469-174">De para meter **MaxEvents** haalt de 50 meest recente gebeurtenissen uit het logboek op.</span><span class="sxs-lookup"><span data-stu-id="43469-174">The **MaxEvents** parameter gets the 50 most recent events from the log.</span></span> <span data-ttu-id="43469-175">De logboek inhoud wordt opgeslagen in de variabele met de naam `$Events` .</span><span class="sxs-lookup"><span data-stu-id="43469-175">The log content is stored in the variable named `$Events`.</span></span>

<span data-ttu-id="43469-176">De `$Events` variabele wordt via de pijp lijn naar de `Select-String` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="43469-176">The `$Events` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="43469-177">`Select-String` maakt gebruik van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="43469-177">`Select-String` uses the **InputObject** parameter.</span></span> <span data-ttu-id="43469-178">De `$_` variabele vertegenwoordigt het huidige object en `message` is een eigenschap van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="43469-178">The `$_` variable represents the current object and `message` is a property of the event.</span></span> <span data-ttu-id="43469-179">De **patroon** parameter vissoort de teken reeks **is mislukt** en zoekt naar overeenkomsten in `$_.message` .</span><span class="sxs-lookup"><span data-stu-id="43469-179">The **Pattern** parameter species the string **Failed** and searches for matches in `$_.message`.</span></span> <span data-ttu-id="43469-180">`Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43469-180">`Select-String` displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="43469-181">Voor beeld 6: een teken reeks zoeken in submappen</span><span class="sxs-lookup"><span data-stu-id="43469-181">Example 6: Find a string in subdirectories</span></span>

<span data-ttu-id="43469-182">In dit voor beeld wordt gezocht naar een map en alle submappen voor een specifieke teken reeks.</span><span class="sxs-lookup"><span data-stu-id="43469-182">This example searches a directory and all of its subdirectories for a specific text string.</span></span>

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

<span data-ttu-id="43469-183">`Get-ChildItem` maakt gebruik van de para meter **Path** om **C:\Windows\System32 \* . txt** op te geven.</span><span class="sxs-lookup"><span data-stu-id="43469-183">`Get-ChildItem` uses the **Path** parameter to specify **C:\Windows\System32\*.txt**.</span></span> <span data-ttu-id="43469-184">De **recursie** -para meter bevat de submappen.</span><span class="sxs-lookup"><span data-stu-id="43469-184">The **Recurse** parameter includes the subdirectories.</span></span> <span data-ttu-id="43469-185">De objecten worden naar beneden verzonden in de pijp lijn `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="43469-185">The objects are sent down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="43469-186">`Select-String` maakt gebruik van de **patroon** parameter en specificeert de teken reeks **micro soft**.</span><span class="sxs-lookup"><span data-stu-id="43469-186">`Select-String` uses the **Pattern** parameter and specifies the string **Microsoft**.</span></span> <span data-ttu-id="43469-187">De para meter **CaseSensitive** wordt gebruikt om de exacte case van de teken reeks overeen te laten komen.</span><span class="sxs-lookup"><span data-stu-id="43469-187">The **CaseSensitive** parameter is used to match the exact case of the string.</span></span> <span data-ttu-id="43469-188">`Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43469-188">`Select-String` displays the output in the PowerShell console.</span></span>

> [!NOTE]
> <span data-ttu-id="43469-189">Afhankelijk van uw machtigingen ziet u mogelijk de **toegang geweigerde** berichten in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="43469-189">Dependent upon your permissions, you might see **Access denied** messages in the output.</span></span>

### <span data-ttu-id="43469-190">Voor beeld 7: teken reeksen zoeken die niet overeenkomen met een patroon</span><span class="sxs-lookup"><span data-stu-id="43469-190">Example 7: Find strings that do not match a pattern</span></span>

<span data-ttu-id="43469-191">In dit voor beeld ziet u hoe u gegevens regels uitsluit die niet overeenkomen met een patroon.</span><span class="sxs-lookup"><span data-stu-id="43469-191">This example shows how to exclude lines of data that don't match a pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

<span data-ttu-id="43469-192">De `Get-Command` cmdlet verzendt objecten van de pijp lijn naar de `Out-File` om het **Command.txt** -bestand in de huidige map te maken.</span><span class="sxs-lookup"><span data-stu-id="43469-192">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="43469-193">`Select-String` maakt gebruik van de para meter **Path** om het **Command.txt** -bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="43469-193">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="43469-194">De para meter **pattern** geeft **Get** en **set** op als zoek patroon.</span><span class="sxs-lookup"><span data-stu-id="43469-194">The **Pattern** parameter specifies **Get** and **Set** as the search pattern.</span></span> <span data-ttu-id="43469-195">De para meter **NotMatch** uitgesloten **Get** en **set** van de resultaten.</span><span class="sxs-lookup"><span data-stu-id="43469-195">The **NotMatch** parameter excludes **Get** and **Set** from the results.</span></span>
<span data-ttu-id="43469-196">`Select-String` Hiermee wordt de uitvoer weer gegeven in de Power shell-console die geen **Get** of **set** bevat.</span><span class="sxs-lookup"><span data-stu-id="43469-196">`Select-String` displays the output in the PowerShell console that doesn't include **Get** or **Set**.</span></span>

### <span data-ttu-id="43469-197">Voor beeld 8: regels voor en na een overeenkomst zoeken</span><span class="sxs-lookup"><span data-stu-id="43469-197">Example 8: Find lines before and after a match</span></span>

<span data-ttu-id="43469-198">In dit voor beeld ziet u hoe u de lijnen voor en na het overeenkomende patroon kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="43469-198">This example shows how to get the lines before and after the matched pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:986:Cmdlet          Get-CmsMessage           6.1.0.0    Microsoft.PowerShell.Security
  Command.txt:987:Cmdlet          Get-Command              6.1.2.0    Microsoft.PowerShell.Core
> Command.txt:988:Cmdlet          Get-ComputerInfo         6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:990:Cmdlet          Get-Content              6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:991:Cmdlet          Get-ControlPanelItem     3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:992:Cmdlet          Get-Credential           6.1.0.0    Microsoft.PowerShell.Security
```

<span data-ttu-id="43469-199">De `Get-Command` cmdlet verzendt objecten van de pijp lijn naar de `Out-File` om het **Command.txt** -bestand in de huidige map te maken.</span><span class="sxs-lookup"><span data-stu-id="43469-199">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="43469-200">`Select-String` maakt gebruik van de para meter **Path** om het **Command.txt** -bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="43469-200">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="43469-201">De para meter **pattern** geeft **Get-computer** op als zoek patroon.</span><span class="sxs-lookup"><span data-stu-id="43469-201">The **Pattern** parameter specifies **Get-Computer** as the search pattern.</span></span> <span data-ttu-id="43469-202">De para meter **context** gebruikt twee waarden, vóór en na, en markeert patroon overeenkomsten in de uitvoer met een punt haak ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="43469-202">The **Context** parameter uses two values, before and after, and marks pattern matches in the output with an angle bracket (`>`).</span></span> <span data-ttu-id="43469-203">Met de **context** parameter worden de twee regels vóór het eerste patroon uitgevoerd en worden er drie regels na het laatste patroon overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="43469-203">The **Context** parameter outputs the two lines before the first pattern match and three lines after the last pattern match.</span></span>

### <span data-ttu-id="43469-204">Voor beeld 9: alle patroon overeenkomsten zoeken</span><span class="sxs-lookup"><span data-stu-id="43469-204">Example 9: Find all pattern matches</span></span>

<span data-ttu-id="43469-205">In dit voor beeld ziet u hoe de para meter **AllMatches** elke overeenkomende patroon in een tekst regel vindt.</span><span class="sxs-lookup"><span data-stu-id="43469-205">This example shows how the **AllMatches** parameter finds each pattern match in a line of text.</span></span> <span data-ttu-id="43469-206">Standaard `Select-String` zoekt alleen het eerste exemplaar van een patroon in een tekst regel.</span><span class="sxs-lookup"><span data-stu-id="43469-206">By default, `Select-String` only finds the first occurrence of a pattern in a line of text.</span></span> <span data-ttu-id="43469-207">In dit voor beeld worden object eigenschappen gebruikt die met de cmdlet worden gevonden `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="43469-207">This example uses object properties that are found with the `Get-Member` cmdlet.</span></span>

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Program Files\PowerShell\6\en-US\default.help.txt:3:    PowerShell Help System
C:\Program Files\PowerShell\6\en-US\default.help.txt:6:    Displays help about PowerShell cmdlets and concepts.
C:\Program Files\PowerShell\6\en-US\default.help.txt:9:    PowerShell Help describes PowerShell cmdlets

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

8

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

9
```

<span data-ttu-id="43469-208">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="43469-208">The `Get-ChildItem` cmdlet uses the **Path** parameter.</span></span> <span data-ttu-id="43469-209">De para meter **Path** maakt gebruik van de variabele `$PSHOME` die de Power shell-map opgeeft.</span><span class="sxs-lookup"><span data-stu-id="43469-209">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="43469-210">De rest van het pad bevat de submap en **-US** en geeft elk `*.txt` bestand in de map op.</span><span class="sxs-lookup"><span data-stu-id="43469-210">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="43469-211">De `Get-ChildItem` objecten worden opgeslagen in de `$A` variabele.</span><span class="sxs-lookup"><span data-stu-id="43469-211">The `Get-ChildItem` objects are stored in the `$A` variable.</span></span> <span data-ttu-id="43469-212">De `$A` variabele wordt via de pijp lijn naar de `Select-String` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="43469-212">The `$A` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="43469-213">`Select-String` maakt gebruik van de **patroon** parameter om te zoeken in elk bestand naar de teken reeks- **Power shell**.</span><span class="sxs-lookup"><span data-stu-id="43469-213">`Select-String` uses the **Pattern** parameter to search each file for the string **PowerShell**.</span></span>

<span data-ttu-id="43469-214">Van de Power shell-opdracht regel wordt de `$A` variabele-inhoud weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43469-214">From the PowerShell command line, the `$A` variable contents are displayed.</span></span> <span data-ttu-id="43469-215">Er is een regel die twee exemplaren van de teken reeks **Power shell** bevat.</span><span class="sxs-lookup"><span data-stu-id="43469-215">There's a line that contains two occurrences of the string **PowerShell**.</span></span>

<span data-ttu-id="43469-216">De `$A.Matches` eigenschap geeft het eerste exemplaar van het patroon **Power shell** op elke regel.</span><span class="sxs-lookup"><span data-stu-id="43469-216">The `$A.Matches` property lists the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="43469-217">De `$A.Matches.Length` eigenschap telt het eerste exemplaar van het patroon **Power shell** op elke regel.</span><span class="sxs-lookup"><span data-stu-id="43469-217">The `$A.Matches.Length` property counts the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="43469-218">De `$B` variabele maakt gebruik van dezelfde `Get-ChildItem` en `Select-String` cmdlets, maar voegt de para meter **AllMatches** toe.</span><span class="sxs-lookup"><span data-stu-id="43469-218">The `$B` variable uses the same `Get-ChildItem` and `Select-String` cmdlets, but adds the **AllMatches** parameter.</span></span> <span data-ttu-id="43469-219">**AllMatches** vindt elk exemplaar van het patroon **Power shell** op elke regel.</span><span class="sxs-lookup"><span data-stu-id="43469-219">**AllMatches** finds each occurrence of the pattern **PowerShell** on each line.</span></span> <span data-ttu-id="43469-220">De objecten die zijn opgeslagen in de `$A` `$B` variabelen en zijn identiek.</span><span class="sxs-lookup"><span data-stu-id="43469-220">The objects stored in the `$A` and `$B` variables are identical.</span></span>

<span data-ttu-id="43469-221">De `$B.Matches.Length` eigenschap neemt toe vanwege elke regel, waarbij elk exemplaar van het patroon **Power shell** wordt geteld.</span><span class="sxs-lookup"><span data-stu-id="43469-221">The `$B.Matches.Length` property increases because for each line, every occurrence of the pattern **PowerShell** is counted.</span></span>

## <span data-ttu-id="43469-222">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43469-222">PARAMETERS</span></span>

### <span data-ttu-id="43469-223">-AllMatches</span><span class="sxs-lookup"><span data-stu-id="43469-223">-AllMatches</span></span>

<span data-ttu-id="43469-224">Geeft aan dat de cmdlet zoekt naar meer dan één overeenkomst in elke regel tekst.</span><span class="sxs-lookup"><span data-stu-id="43469-224">Indicates that the cmdlet searches for more than one match in each line of text.</span></span> <span data-ttu-id="43469-225">Zonder deze para meter wordt `Select-String` alleen gezocht naar de eerste overeenkomst in elke regel tekst.</span><span class="sxs-lookup"><span data-stu-id="43469-225">Without this parameter, `Select-String` finds only the first match in each line of text.</span></span>

<span data-ttu-id="43469-226">Wanneer er `Select-String` meer dan één overeenkomst in een tekst regel wordt gevonden, wordt er nog steeds slechts één **MatchInfo** -object voor de regel geleverd, maar de eigenschap **matchs** van het object bevat alle overeenkomsten.</span><span class="sxs-lookup"><span data-stu-id="43469-226">When `Select-String` finds more than one match in a line of text, it still emits only one **MatchInfo** object for the line, but the **Matches** property of the object contains all the matches.</span></span>

> [!NOTE]
> <span data-ttu-id="43469-227">Deze para meter wordt genegeerd als deze wordt gebruikt in combi natie met de para meter **SimpleMatch** .</span><span class="sxs-lookup"><span data-stu-id="43469-227">This parameter is ignored when used in combination with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="43469-228">Als u alle overeenkomsten wilt retour neren en het patroon waarnaar u zoekt reguliere expressie tekens bevat, moet u deze tekens weglaten in plaats van **SimpleMatch** te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="43469-228">If you wish to return all matches and the pattern that you are searching for contains regular expression characters, you must escape those characters rather than using **SimpleMatch**.</span></span> <span data-ttu-id="43469-229">Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) voor meer informatie over reguliere expressies voor Escapes.</span><span class="sxs-lookup"><span data-stu-id="43469-229">See [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) for more information about escaping regular expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-230">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="43469-230">-CaseSensitive</span></span>

<span data-ttu-id="43469-231">Geeft aan dat de cmdlets overeenkomen met hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="43469-231">Indicates that the cmdlet matches are case-sensitive.</span></span> <span data-ttu-id="43469-232">Standaard zijn niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="43469-232">By default, matches aren't case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-233">-Context</span><span class="sxs-lookup"><span data-stu-id="43469-233">-Context</span></span>

<span data-ttu-id="43469-234">Hiermee wordt het opgegeven aantal regels vóór en na de lijn die overeenkomt met het patroon vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="43469-234">Captures the specified number of lines before and after the line that matches the pattern.</span></span>

<span data-ttu-id="43469-235">Als u één getal als waarde voor deze para meter opgeeft, wordt het aantal regels bepaald dat voor en na de overeenkomst is vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="43469-235">If you enter one number as the value of this parameter, that number determines the number of lines captured before and after the match.</span></span> <span data-ttu-id="43469-236">Als u twee getallen opgeeft als waarde, bepaalt het eerste getal het aantal regels vóór de overeenkomst en het tweede getal bepaalt het aantal regels na de overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="43469-236">If you enter two numbers as the value, the first number determines the number of lines before the match and the second number determines the number of lines after the match.</span></span> <span data-ttu-id="43469-237">Bijvoorbeeld `-Context 2,3`.</span><span class="sxs-lookup"><span data-stu-id="43469-237">For example, `-Context 2,3`.</span></span>

<span data-ttu-id="43469-238">In de standaard weergave worden regels met een overeenkomst aangeduid met een rechter punt haak ( `>` ) (ASCII 62) in de eerste kolom van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="43469-238">In the default display, lines with a match are indicated by a right angle bracket (`>`) (ASCII 62) in the first column of the display.</span></span> <span data-ttu-id="43469-239">Niet-gemarkeerde regels zijn de context.</span><span class="sxs-lookup"><span data-stu-id="43469-239">Unmarked lines are the context.</span></span>

<span data-ttu-id="43469-240">De para meter **context** wijzigt niet het aantal objecten dat door is gegenereerd `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="43469-240">The **Context** parameter doesn't change the number of objects generated by `Select-String`.</span></span>
<span data-ttu-id="43469-241">`Select-String` genereert één [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) -object voor elke overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="43469-241">`Select-String` generates one [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) object for each match.</span></span> <span data-ttu-id="43469-242">De context wordt opgeslagen als een matrix met teken reeksen in de **context** eigenschap van het object.</span><span class="sxs-lookup"><span data-stu-id="43469-242">The context is stored as an array of strings in the **Context** property of the object.</span></span>

<span data-ttu-id="43469-243">Wanneer de uitvoer van een `Select-String` opdracht door de pijp lijn naar een andere opdracht wordt verzonden `Select-String` , doorzoekt de ontvangende opdracht alleen de tekst in de overeenkomende lijn.</span><span class="sxs-lookup"><span data-stu-id="43469-243">When the output of a `Select-String` command is sent down the pipeline to another `Select-String` command, the receiving command searches only the text in the matched line.</span></span> <span data-ttu-id="43469-244">De overeenkomende lijn is de waarde van de **regel** eigenschap van het object **MatchInfo** , niet de tekst in de context regels.</span><span class="sxs-lookup"><span data-stu-id="43469-244">The matched line is the value of the **Line** property of the **MatchInfo** object, not the text in the context lines.</span></span> <span data-ttu-id="43469-245">Als gevolg hiervan is de **context** parameter niet geldig voor de ontvangende `Select-String` opdracht.</span><span class="sxs-lookup"><span data-stu-id="43469-245">As a result, the **Context** parameter isn't valid on the receiving `Select-String` command.</span></span>

<span data-ttu-id="43469-246">Wanneer de context een overeenkomst bevat, bevat het **MatchInfo** -object voor elke overeenkomst alle context regels, maar worden de overlappende lijnen slechts eenmaal in de weer gave weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43469-246">When the context includes a match, the **MatchInfo** object for each match includes all the context lines, but the overlapping lines appear only once in the display.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-247">-Cultuur</span><span class="sxs-lookup"><span data-stu-id="43469-247">-Culture</span></span>

<span data-ttu-id="43469-248">Hiermee geeft u een cultuur naam op die overeenkomt met het opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="43469-248">Specifies a culture name to match the specified pattern.</span></span> <span data-ttu-id="43469-249">De para meter **Culture** moet worden gebruikt in combi natie met de para meter **SimpleMatch** .</span><span class="sxs-lookup"><span data-stu-id="43469-249">The **Culture** parameter must be used with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="43469-250">Bij het standaard gedrag wordt gebruikgemaakt van de cultuur van de huidige Power shell-runs Pace (sessie).</span><span class="sxs-lookup"><span data-stu-id="43469-250">The default behavior uses the culture of the current PowerShell runspace (session).</span></span>

<span data-ttu-id="43469-251">Gebruik de opdracht om een lijst met alle ondersteunde cult uren weer te geven `Get-Culture -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="43469-251">To get a list of all supported cultures, use `Get-Culture -ListAvailable` command.</span></span>

<span data-ttu-id="43469-252">Daarnaast accepteert deze para meter de volgende argumenten:</span><span class="sxs-lookup"><span data-stu-id="43469-252">In addition, this parameter accepts the following arguments:</span></span>

- <span data-ttu-id="43469-253">CurrentCulture, dat is standaard;</span><span class="sxs-lookup"><span data-stu-id="43469-253">CurrentCulture, that is default;</span></span>
- <span data-ttu-id="43469-254">Rang telwoord, dat wil zeggen een binaire vergelijking zonder taal;</span><span class="sxs-lookup"><span data-stu-id="43469-254">Ordinal, that is non-linguistic binary comparison;</span></span>
- <span data-ttu-id="43469-255">Invariantie, een cultuur onafhankelijke vergelijking.</span><span class="sxs-lookup"><span data-stu-id="43469-255">Invariant, that is culture independent comparison.</span></span>

<span data-ttu-id="43469-256">Met de `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` opdracht kunt u een snelste binaire vergelijking.</span><span class="sxs-lookup"><span data-stu-id="43469-256">With `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` command you gets fastest binary comparison.</span></span>

<span data-ttu-id="43469-257">De para meter **Culture** gebruikt Tab-aanvulling om door de lijst met argumenten te bladeren waarmee de beschik bare cult uren worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="43469-257">The **Culture** parameter uses tab completion to scroll through the list of arguments that specify the available cultures.</span></span> <span data-ttu-id="43469-258">Als u alle beschik bare argumenten wilt weer geven, gebruikt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="43469-258">To list all available arguments, use the following command:</span></span>

`(Get-Command Select-String).Parameters.Culture.Attributes.ValidValues`

<span data-ttu-id="43469-259">Zie [CultureInfo.name](/dotnet/api//system.globalization.cultureinfo.name)voor meer informatie over de eigenschap .net CultureInfo.name.</span><span class="sxs-lookup"><span data-stu-id="43469-259">For more information about .NET CultureInfo.Name property, see [CultureInfo.Name](/dotnet/api//system.globalization.cultureinfo.name).</span></span>

<span data-ttu-id="43469-260">De para meter **Culture** is geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="43469-260">The **Culture** parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Culture of the current PowerShell session
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-261">-Encoding</span><span class="sxs-lookup"><span data-stu-id="43469-261">-Encoding</span></span>

<span data-ttu-id="43469-262">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="43469-262">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="43469-263">De standaardwaarde is `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="43469-263">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="43469-264">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="43469-264">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="43469-265">`ascii`: Gebruikt de code ring voor de ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="43469-265">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="43469-266">`bigendianunicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="43469-266">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="43469-267">`bigendianutf32`: Codeert in UTF-32-indeling met behulp van de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="43469-267">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="43469-268">`oem`: Maakt gebruik van de standaard codering voor MS-DOS-en console Programma's.</span><span class="sxs-lookup"><span data-stu-id="43469-268">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="43469-269">`unicode`: Wordt gecodeerd in UTF-16-indeling met behulp van de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="43469-269">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="43469-270">`utf7`: Wordt gecodeerd in de indeling UTF-7.</span><span class="sxs-lookup"><span data-stu-id="43469-270">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="43469-271">`utf8`: Wordt gecodeerd in UTF-8-indeling.</span><span class="sxs-lookup"><span data-stu-id="43469-271">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="43469-272">`utf8BOM`: Code ring in UTF-8-indeling met byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="43469-272">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="43469-273">`utf8NoBOM`: Code ring in UTF-8-indeling zonder byte order Mark (BOM)</span><span class="sxs-lookup"><span data-stu-id="43469-273">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="43469-274">`utf32`: Gecodeerd in UTF-32-indeling.</span><span class="sxs-lookup"><span data-stu-id="43469-274">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="43469-275">Vanaf Power shell 6,2 kunnen met de para meter **Encoding** ook numerieke id's van geregistreerde code pagina's (zoals `-Encoding 1251` ) of teken reeks namen van geregistreerde code pagina's (zoals) worden toegestaan `-Encoding "windows-1251"` .</span><span class="sxs-lookup"><span data-stu-id="43469-275">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="43469-276">Zie de .NET-documentatie voor [code ring. code tabel](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="43469-276">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="43469-277">**UTF-7** _ wordt niet meer aanbevolen om te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="43469-277">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="43469-278">In Power shell 7,1 wordt een waarschuwing geschreven als u `utf7` de para meter _ *Encoding*\* opgeeft.</span><span class="sxs-lookup"><span data-stu-id="43469-278">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-279">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="43469-279">-Exclude</span></span>

<span data-ttu-id="43469-280">Sluit de opgegeven items uit.</span><span class="sxs-lookup"><span data-stu-id="43469-280">Exclude the specified items.</span></span> <span data-ttu-id="43469-281">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="43469-281">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="43469-282">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="43469-282">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="43469-283">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="43469-283">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="43469-284">-Include</span><span class="sxs-lookup"><span data-stu-id="43469-284">-Include</span></span>

<span data-ttu-id="43469-285">Bevat de opgegeven items.</span><span class="sxs-lookup"><span data-stu-id="43469-285">Includes the specified items.</span></span> <span data-ttu-id="43469-286">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="43469-286">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="43469-287">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="43469-287">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="43469-288">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="43469-288">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="43469-289">-Input object</span><span class="sxs-lookup"><span data-stu-id="43469-289">-InputObject</span></span>

<span data-ttu-id="43469-290">Geeft de tekst aan waarnaar moet worden gezocht.</span><span class="sxs-lookup"><span data-stu-id="43469-290">Specifies the text to be searched.</span></span> <span data-ttu-id="43469-291">Voer een variabele in die de tekst bevat of typ een opdracht of expressie waarmee de tekst wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="43469-291">Enter a variable that contains the text, or type a command or expression that gets the text.</span></span>

<span data-ttu-id="43469-292">Het gebruik van de para meter **input object** is niet hetzelfde als het verzenden van teken reeksen naar de pijp lijn `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="43469-292">Using the **InputObject** parameter isn't the same as sending strings down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="43469-293">Wanneer u meer dan een teken reeks naar de `Select-String` cmdlet Pipet, zoekt het naar de opgegeven tekst in elke teken reeks en retourneert elke teken reeks die de Zoek tekst bevat.</span><span class="sxs-lookup"><span data-stu-id="43469-293">When you pipe more than one string to the `Select-String` cmdlet, it searches for the specified text in each string and returns each string that contains the search text.</span></span>

<span data-ttu-id="43469-294">Wanneer u de para meter **input object** gebruikt voor het verzenden van een verzameling teken reeksen, `Select-String` behandelt de verzameling als één gecombineerde teken reeks.</span><span class="sxs-lookup"><span data-stu-id="43469-294">When you use the **InputObject** parameter to submit a collection of strings, `Select-String` treats the collection as a single combined string.</span></span> <span data-ttu-id="43469-295">`Select-String` retourneert de teken reeksen als eenheid als de Zoek tekst in een wille keurige teken reeks wordt gevonden.</span><span class="sxs-lookup"><span data-stu-id="43469-295">`Select-String` returns the strings as a unit if it finds the search text in any string.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object, ObjectRaw
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="43469-296">-Lijst</span><span class="sxs-lookup"><span data-stu-id="43469-296">-List</span></span>

<span data-ttu-id="43469-297">Alleen het eerste exemplaar van de overeenkomende tekst wordt geretourneerd vanuit elk invoer bestand.</span><span class="sxs-lookup"><span data-stu-id="43469-297">Only the first instance of matching text is returned from each input file.</span></span> <span data-ttu-id="43469-298">Dit is de meest efficiënte manier om een lijst met bestanden op te halen met inhoud die overeenkomt met de reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="43469-298">This is the most efficient way to retrieve a list of files that have contents matching the regular expression.</span></span>

<span data-ttu-id="43469-299">`Select-String`Retourneert standaard een **MatchInfo** -object voor elke gevonden overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="43469-299">By default, `Select-String` returns a **MatchInfo** object for each match it finds.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-300">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="43469-300">-LiteralPath</span></span>

<span data-ttu-id="43469-301">Hiermee geeft u het pad op naar de bestanden die moeten worden doorzocht.</span><span class="sxs-lookup"><span data-stu-id="43469-301">Specifies the path to the files to be searched.</span></span> <span data-ttu-id="43469-302">De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="43469-302">The value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="43469-303">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="43469-303">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="43469-304">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="43469-304">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="43469-305">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="43469-305">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="43469-306">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="43469-306">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralFileRaw, LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="43469-307">-De nadruk</span><span class="sxs-lookup"><span data-stu-id="43469-307">-NoEmphasis</span></span>

<span data-ttu-id="43469-308">`Select-String`Markeert standaard de teken reeks die overeenkomt met het patroon dat u hebt gezocht met de **patroon** parameter.</span><span class="sxs-lookup"><span data-stu-id="43469-308">By default, `Select-String` highlights the string that matches the pattern you searched for with the **Pattern** parameter.</span></span> <span data-ttu-id="43469-309">Met de para meter voor de **nadruk** wordt de markering uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="43469-309">The **NoEmphasis** parameter disables the highlighting.</span></span>

<span data-ttu-id="43469-310">De nadruk gebruikt negatieve kleuren op basis van uw Power shell-achtergrond en tekst kleuren.</span><span class="sxs-lookup"><span data-stu-id="43469-310">The emphasis uses negative colors based on your PowerShell background and text colors.</span></span> <span data-ttu-id="43469-311">Als uw Power shell-kleuren bijvoorbeeld een zwarte achtergrond met witte tekst zijn.</span><span class="sxs-lookup"><span data-stu-id="43469-311">For example, if your PowerShell colors are a black background with white text.</span></span> <span data-ttu-id="43469-312">De nadruk is een witte achtergrond met zwarte tekst.</span><span class="sxs-lookup"><span data-stu-id="43469-312">The emphasis is a white background with black text.</span></span>

<span data-ttu-id="43469-313">Deze para meter is geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="43469-313">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-314">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="43469-314">-NotMatch</span></span>

<span data-ttu-id="43469-315">De para meter **NotMatch** vindt tekst die niet overeenkomt met het opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="43469-315">The **NotMatch** parameter finds text that doesn't match the specified pattern.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-316">-Path</span><span class="sxs-lookup"><span data-stu-id="43469-316">-Path</span></span>

<span data-ttu-id="43469-317">Hiermee geeft u het pad op naar de bestanden waarnaar moet worden gezocht.</span><span class="sxs-lookup"><span data-stu-id="43469-317">Specifies the path to the files to search.</span></span> <span data-ttu-id="43469-318">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="43469-318">Wildcards are permitted.</span></span> <span data-ttu-id="43469-319">De standaard locatie is de lokale map.</span><span class="sxs-lookup"><span data-stu-id="43469-319">The default location is the local directory.</span></span>

<span data-ttu-id="43469-320">Bestanden opgeven in de Directory, zoals `log1.txt` , `*.doc` of `*.*` .</span><span class="sxs-lookup"><span data-stu-id="43469-320">Specify files in the directory, such as `log1.txt`, `*.doc`, or `*.*`.</span></span> <span data-ttu-id="43469-321">Als u alleen een map opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="43469-321">If you specify only a directory, the command fails.</span></span>

```yaml
Type: System.String[]
Parameter Sets: File, FileRaw
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="43469-322">-Patroon</span><span class="sxs-lookup"><span data-stu-id="43469-322">-Pattern</span></span>

<span data-ttu-id="43469-323">Hiermee geeft u de tekst op elke regel moet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="43469-323">Specifies the text to find on each line.</span></span> <span data-ttu-id="43469-324">De patroon waarde wordt beschouwd als een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="43469-324">The pattern value is treated as a regular expression.</span></span>

<span data-ttu-id="43469-325">Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)voor meer informatie over reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="43469-325">To learn about regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-326">-Quiet</span><span class="sxs-lookup"><span data-stu-id="43469-326">-Quiet</span></span>

<span data-ttu-id="43469-327">Geeft aan dat de cmdlet een Booleaanse waarde retourneert (True of false) in plaats van een **MatchInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="43469-327">Indicates that the cmdlet returns a Boolean value (True or False), instead of a **MatchInfo** object.</span></span> <span data-ttu-id="43469-328">De waarde is True als het patroon is gevonden; anders is de waarde false.</span><span class="sxs-lookup"><span data-stu-id="43469-328">The value is True if the pattern is found; otherwise the value is False.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File, Object, LiteralFile
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-329">-RAW</span><span class="sxs-lookup"><span data-stu-id="43469-329">-Raw</span></span>

<span data-ttu-id="43469-330">Zorgt ervoor dat de cmdlet alleen de overeenkomende teken reeksen uitvoer in plaats van **MatchInfo** -objecten.</span><span class="sxs-lookup"><span data-stu-id="43469-330">Causes the cmdlet to output only the matching strings, rather than **MatchInfo** objects.</span></span> <span data-ttu-id="43469-331">Dit is de resultaten die het meest overeenkomen met **de UNIX-** of Windows **findstr.exe** -opdrachten.</span><span class="sxs-lookup"><span data-stu-id="43469-331">This is the results in behavior that's the most similar to the Unix **grep** or Windows **findstr.exe** commands.</span></span>

<span data-ttu-id="43469-332">Deze para meter is geïntroduceerd in Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="43469-332">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ObjectRaw, FileRaw, LiteralFileRaw
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-333">-SimpleMatch</span><span class="sxs-lookup"><span data-stu-id="43469-333">-SimpleMatch</span></span>

<span data-ttu-id="43469-334">Geeft aan dat de cmdlet een eenvoudige overeenkomst gebruikt in plaats van een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="43469-334">Indicates that the cmdlet uses a simple match rather than a regular expression match.</span></span> <span data-ttu-id="43469-335">In een eenvoudige overeenkomst `Select-String` zoekt de invoer voor de tekst in de para meter **pattern** .</span><span class="sxs-lookup"><span data-stu-id="43469-335">In a simple match, `Select-String` searches the input for the text in the **Pattern** parameter.</span></span> <span data-ttu-id="43469-336">De waarde van de **patroon** parameter wordt niet geïnterpreteerd als een reguliere expressie-instructie.</span><span class="sxs-lookup"><span data-stu-id="43469-336">It doesn't interpret the value of the **Pattern** parameter as a regular expression statement.</span></span>

<span data-ttu-id="43469-337">Wanneer **SimpleMatch** wordt gebruikt, is de eigenschap **matchers** van het geretourneerde **MatchInfo** -object ook leeg.</span><span class="sxs-lookup"><span data-stu-id="43469-337">Also, when **SimpleMatch** is used, the **Matches** property of the **MatchInfo** object returned is empty.</span></span>

> [!NOTE]
> <span data-ttu-id="43469-338">Als deze para meter wordt gebruikt met de para meter **AllMatches** , wordt de **AllMatches** genegeerd.</span><span class="sxs-lookup"><span data-stu-id="43469-338">When this parameter is used with the **AllMatches** parameter, the **AllMatches** is ignored.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43469-339">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43469-339">CommonParameters</span></span>

<span data-ttu-id="43469-340">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="43469-340">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43469-341">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="43469-341">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="43469-342">INVOER</span><span class="sxs-lookup"><span data-stu-id="43469-342">INPUTS</span></span>

### <span data-ttu-id="43469-343">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="43469-343">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="43469-344">U kunt elk object dat een **toString** -methode heeft, aan het sluis teken toe `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="43469-344">You can pipe any object that has a **ToString** method to `Select-String`.</span></span>

## <span data-ttu-id="43469-345">UITVOER</span><span class="sxs-lookup"><span data-stu-id="43469-345">OUTPUTS</span></span>

### <span data-ttu-id="43469-346">Micro soft. Power shell. commands. MatchInfo, System. Boolean, System. String</span><span class="sxs-lookup"><span data-stu-id="43469-346">Microsoft.PowerShell.Commands.MatchInfo, System.Boolean, System.String</span></span>

<span data-ttu-id="43469-347">Standaard is de uitvoer een set **MatchInfo** -objecten met één voor elke gevonden overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="43469-347">By default, the output is a set of **MatchInfo** objects with one for each match found.</span></span> <span data-ttu-id="43469-348">Als u de **stille** para meter gebruikt, is de uitvoer een **Booleaanse** waarde die aangeeft of het patroon is gevonden.</span><span class="sxs-lookup"><span data-stu-id="43469-348">If you use the **Quiet** parameter, the output is a **Boolean** value indicating whether the pattern was found.</span></span>
<span data-ttu-id="43469-349">Als u de **onbewerkte** para meter gebruikt, is de uitvoer een set **teken reeks** objecten die overeenkomen met het patroon.</span><span class="sxs-lookup"><span data-stu-id="43469-349">If you use the **Raw** parameter, the output is a set of **String** objects that match the pattern.</span></span>

## <span data-ttu-id="43469-350">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="43469-350">NOTES</span></span>

<span data-ttu-id="43469-351">`Select-String` is vergelijkbaar met **grep** in UNIX of **findstr.exe** in Windows.</span><span class="sxs-lookup"><span data-stu-id="43469-351">`Select-String` is similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="43469-352">De **SLS** -alias voor de `Select-String` cmdlet is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="43469-352">The **sls** alias for the `Select-String` cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="43469-353">Volgens de [goedgekeurde werk woorden voor Power shell-opdrachten](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)is het officiële alias voorvoegsel voor `Select-*` cmdlets `sc` `sl` .</span><span class="sxs-lookup"><span data-stu-id="43469-353">According to [Approved Verbs for PowerShell Commands](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), the official alias prefix for `Select-*` cmdlets is `sc`, not `sl`.</span></span> <span data-ttu-id="43469-354">Daarom moet de juiste alias voor `Select-String` zijn `scs` , niet `sls` .</span><span class="sxs-lookup"><span data-stu-id="43469-354">Therefore, the proper alias for `Select-String` should be `scs`, not `sls`.</span></span> <span data-ttu-id="43469-355">Dit is een uitzonde ring op deze regel.</span><span class="sxs-lookup"><span data-stu-id="43469-355">This is an exception to this rule.</span></span>

<span data-ttu-id="43469-356">Als u wilt gebruiken `Select-String` , typt u de tekst die u wilt zoeken als waarde voor de **patroon** parameter.</span><span class="sxs-lookup"><span data-stu-id="43469-356">To use `Select-String`, type the text that you want to find as the value of the **Pattern** parameter.</span></span> <span data-ttu-id="43469-357">Gebruik de volgende criteria om de tekst op te geven die moet worden doorzocht:</span><span class="sxs-lookup"><span data-stu-id="43469-357">To specify the text to be searched, use the following criteria:</span></span>

- <span data-ttu-id="43469-358">Typ de tekst in een teken reeks tussen aanhalings tekens en sleep deze naar `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="43469-358">Type the text in a quoted string, and then pipe it to `Select-String`.</span></span>
- <span data-ttu-id="43469-359">Sla een teken reeks op in een variabele en geef de variabele op als de waarde van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="43469-359">Store a text string in a variable, and then specify the variable as the value of the **InputObject** parameter.</span></span>
- <span data-ttu-id="43469-360">Als de tekst wordt opgeslagen in bestanden, gebruikt u de para meter **Path** om het pad naar de bestanden op te geven.</span><span class="sxs-lookup"><span data-stu-id="43469-360">If the text is stored in files, use the **Path** parameter to specify the path to the files.</span></span>

<span data-ttu-id="43469-361">`Select-String`De waarde van de **pattern** -para meter wordt standaard geïnterpreteerd als een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="43469-361">By default, `Select-String` interprets the value of the **Pattern** parameter as a regular expression.</span></span> <span data-ttu-id="43469-362">Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="43469-362">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span> <span data-ttu-id="43469-363">U kunt de para meter **SimpleMatch** gebruiken om de reguliere expressie overeenkomst te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="43469-363">You can use the **SimpleMatch** parameter to override the regular expression matching.</span></span> <span data-ttu-id="43469-364">De para meter **SimpleMatch** vindt instanties van de waarde van de para meter **pattern** in de invoer.</span><span class="sxs-lookup"><span data-stu-id="43469-364">The **SimpleMatch** parameter finds instances of the value of the **Pattern** parameter in the input.</span></span>

<span data-ttu-id="43469-365">De standaard uitvoer van `Select-String` is een **MatchInfo** -object, dat gedetailleerde informatie over de overeenkomsten bevat.</span><span class="sxs-lookup"><span data-stu-id="43469-365">The default output of `Select-String` is a **MatchInfo** object, which includes detailed information about the matches.</span></span> <span data-ttu-id="43469-366">De informatie in het object is handig wanneer u zoekt naar tekst in bestanden, omdat **MatchInfo** -objecten eigenschappen hebben zoals **filename** en **Line**.</span><span class="sxs-lookup"><span data-stu-id="43469-366">The information in the object is useful when you're searching for text in files, because **MatchInfo** objects have properties such as **Filename** and **Line**.</span></span> <span data-ttu-id="43469-367">Wanneer de invoer niet van het bestand is, is de waarde van deze para meters **InputStream**.</span><span class="sxs-lookup"><span data-stu-id="43469-367">When the input isn't from the file, the value of these parameters is **InputStream**.</span></span>

<span data-ttu-id="43469-368">Als u de gegevens in het **MatchInfo** -object niet nodig hebt, gebruikt u de **stille** para meter.</span><span class="sxs-lookup"><span data-stu-id="43469-368">If you don't need the information in the **MatchInfo** object, use the **Quiet** parameter.</span></span> <span data-ttu-id="43469-369">De **stille** para meter retourneert een Booleaanse waarde (waar of onwaar) om aan te geven of deze een overeenkomst heeft gevonden in plaats van een **MatchInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="43469-369">The **Quiet** parameter returns a Boolean value (True or False) to indicate whether it found a match, instead of a **MatchInfo** object.</span></span>

<span data-ttu-id="43469-370">Bij overeenkomende woord groepen `Select-String` gebruikt de huidige cultuur die is ingesteld voor het systeem.</span><span class="sxs-lookup"><span data-stu-id="43469-370">When matching phrases, `Select-String` uses the current culture that is set for the system.</span></span> <span data-ttu-id="43469-371">Als u de huidige cultuur wilt zoeken, gebruikt u de `Get-Culture` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43469-371">To find the current culture, use the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="43469-372">Als u de eigenschappen van een **MatchInfo** -object wilt zoeken, typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="43469-372">To find the properties of a **MatchInfo** object, type the following command:</span></span>

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## <span data-ttu-id="43469-373">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="43469-373">RELATED LINKS</span></span>

[<span data-ttu-id="43469-374">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="43469-374">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="43469-375">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="43469-375">about_Comparison_Operators</span></span>](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[<span data-ttu-id="43469-376">about_Functions</span><span class="sxs-lookup"><span data-stu-id="43469-376">about_Functions</span></span>](../Microsoft.PowerShell.Core/About/about_Functions.md)

[<span data-ttu-id="43469-377">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="43469-377">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="43469-378">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="43469-378">about_Regular_Expressions</span></span>](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[<span data-ttu-id="43469-379">Get-alias</span><span class="sxs-lookup"><span data-stu-id="43469-379">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="43469-380">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="43469-380">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="43469-381">Get-Command</span><span class="sxs-lookup"><span data-stu-id="43469-381">Get-Command</span></span>](../Microsoft.PowerShell.Core/Get-Command.md)

[<span data-ttu-id="43469-382">Get-member</span><span class="sxs-lookup"><span data-stu-id="43469-382">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="43469-383">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="43469-383">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="43469-384">Out-file</span><span class="sxs-lookup"><span data-stu-id="43469-384">Out-File</span></span>](Out-File.md)

