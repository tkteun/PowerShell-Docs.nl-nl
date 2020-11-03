---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 95601a4f5f42700c4de7d6ad721ee898b22bab84
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/25/2020
ms.locfileid: "93251843"
---
# <span data-ttu-id="692fb-103">Select-String</span><span class="sxs-lookup"><span data-stu-id="692fb-103">Select-String</span></span>

## <span data-ttu-id="692fb-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="692fb-104">SYNOPSIS</span></span>
<span data-ttu-id="692fb-105">Zoeken naar tekst in teken reeksen en bestanden.</span><span class="sxs-lookup"><span data-stu-id="692fb-105">Finds text in strings and files.</span></span>

## <span data-ttu-id="692fb-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="692fb-106">SYNTAX</span></span>

### <span data-ttu-id="692fb-107">Bestand (standaard)</span><span class="sxs-lookup"><span data-stu-id="692fb-107">File (Default)</span></span>

```
Select-String [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="692fb-108">Object</span><span class="sxs-lookup"><span data-stu-id="692fb-108">Object</span></span>

```
Select-String -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="692fb-109">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="692fb-109">LiteralFile</span></span>

```
Select-String [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="692fb-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="692fb-110">DESCRIPTION</span></span>

<span data-ttu-id="692fb-111">De `Select-String` cmdlet zoekt naar tekst-en tekst patronen in invoer teken reeksen en bestanden.</span><span class="sxs-lookup"><span data-stu-id="692fb-111">The `Select-String` cmdlet searches for text and text patterns in input strings and files.</span></span> <span data-ttu-id="692fb-112">U kunt `Select-String` vergelijkbaar met **grep** gebruiken in UNIX of **findstr.exe** in Windows.</span><span class="sxs-lookup"><span data-stu-id="692fb-112">You can use `Select-String` similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="692fb-113">`Select-String` is gebaseerd op regels tekst.</span><span class="sxs-lookup"><span data-stu-id="692fb-113">`Select-String` is based on lines of text.</span></span> <span data-ttu-id="692fb-114">Standaard `Select-String` zoekt de eerste overeenkomst op elke regel en, voor elke overeenkomst, worden de bestands naam, het regel nummer en alle tekst in de regel met de overeenkomst weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="692fb-114">By default, `Select-String` finds the first match in each line and, for each match, it displays the file name, line number, and all text in the line containing the match.</span></span> <span data-ttu-id="692fb-115">U kunt direct `Select-String` zoeken naar meerdere overeenkomsten per regel, tekst weer geven voor en na de overeenkomst of een Booleaanse waarde (waar of onwaar) weer geven die aangeeft of er een overeenkomst is gevonden.</span><span class="sxs-lookup"><span data-stu-id="692fb-115">You can direct `Select-String` to find multiple matches per line, display text before and after the match, or display a Boolean value (True or False) that indicates whether a match is found.</span></span>

<span data-ttu-id="692fb-116">`Select-String` maakt gebruik van reguliere expressie matching, maar kan ook een overeenkomst uitvoeren die de invoer doorzoekt voor de tekst die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="692fb-116">`Select-String` uses regular expression matching, but it can also perform a match that searches the input for the text that you specify.</span></span>

<span data-ttu-id="692fb-117">`Select-String` kan alle tekst overeenkomsten weer geven of stoppen na de eerste overeenkomst in elk invoer bestand.</span><span class="sxs-lookup"><span data-stu-id="692fb-117">`Select-String` can display all the text matches or stop after the first match in each input file.</span></span>
<span data-ttu-id="692fb-118">`Select-String` kan worden gebruikt om alle tekst weer te geven die niet overeenkomt met het opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="692fb-118">`Select-String` can be used to display all text that doesn't match the specified pattern.</span></span>

<span data-ttu-id="692fb-119">U kunt ook opgeven dat `Select-String` een bepaalde teken codering moet worden verwacht, bijvoorbeeld wanneer u bestanden van Unicode-tekst zoekt.</span><span class="sxs-lookup"><span data-stu-id="692fb-119">You can also specify that `Select-String` should expect a particular character encoding, such as when you're searching files of Unicode text.</span></span> <span data-ttu-id="692fb-120">`Select-String` maakt gebruik van de byte-order-Mark (BOM) om de coderings indeling van het bestand te detecteren.</span><span class="sxs-lookup"><span data-stu-id="692fb-120">`Select-String` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="692fb-121">Als het bestand geen stuk lijst heeft, wordt ervan uitgegaan dat de code ring UTF8 is.</span><span class="sxs-lookup"><span data-stu-id="692fb-121">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="692fb-122">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="692fb-122">EXAMPLES</span></span>

### <span data-ttu-id="692fb-123">Voor beeld 1: een hoofdletter gevoelige overeenkomst zoeken</span><span class="sxs-lookup"><span data-stu-id="692fb-123">Example 1: Find a case-sensitive match</span></span>

<span data-ttu-id="692fb-124">In dit voor beeld is een hoofdletter gevoelige overeenkomst van de tekst die de pijp lijn naar de cmdlet heeft verzonden `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="692fb-124">This example does a case-sensitive match of the text that was sent down the pipeline to the `Select-String` cmdlet.</span></span>

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

<span data-ttu-id="692fb-125">De tekst teken reeksen **Hello** en **Hello** worden in de pijp lijn naar de `Select-String` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="692fb-125">The text strings **Hello** and **HELLO** are sent down the pipeline to the `Select-String` cmdlet.</span></span>
<span data-ttu-id="692fb-126">`Select-String` maakt gebruik van de para meter **pattern** om **Hello** op te geven.</span><span class="sxs-lookup"><span data-stu-id="692fb-126">`Select-String` uses the **Pattern** parameter to specify **HELLO**.</span></span> <span data-ttu-id="692fb-127">De para meter **CaseSensitive** geeft aan dat de case alleen moet overeenkomen met het hoofd-hoofdletter patroon.</span><span class="sxs-lookup"><span data-stu-id="692fb-127">The **CaseSensitive** parameter specifies that the case must match only the upper-case pattern.</span></span> <span data-ttu-id="692fb-128">**SimpleMatch** is een optionele para meter en geeft aan dat de teken reeks in het patroon niet wordt geïnterpreteerd als een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="692fb-128">**SimpleMatch** is an optional parameter and specifies that the string in the pattern isn't interpreted as a regular expression.</span></span>
<span data-ttu-id="692fb-129">`Select-String` Hiermee wordt **Hello** weer gegeven in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="692fb-129">`Select-String` displays **HELLO** in the PowerShell console.</span></span>

### <span data-ttu-id="692fb-130">Voor beeld 2: overeenkomsten zoeken in tekst bestanden</span><span class="sxs-lookup"><span data-stu-id="692fb-130">Example 2: Find matches in text files</span></span>

<span data-ttu-id="692fb-131">Met deze opdracht worden alle bestanden `.txt` in de huidige map doorzocht met de bestandsnaam extensie.</span><span class="sxs-lookup"><span data-stu-id="692fb-131">This command searches all files with the `.txt` file name extension in the current directory.</span></span> <span data-ttu-id="692fb-132">In de uitvoer worden de regels in die bestanden weer gegeven die de opgegeven teken reeks bevatten.</span><span class="sxs-lookup"><span data-stu-id="692fb-132">The output displays the lines in those files that include the specified string.</span></span>

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

<span data-ttu-id="692fb-133">In dit voor beeld `Get-Alias` wordt `Get-Command` met de `Out-File` cmdlet twee tekst bestanden gemaakt in de huidige map **Alias.txt** en **Command.txt**.</span><span class="sxs-lookup"><span data-stu-id="692fb-133">In this example, `Get-Alias` and `Get-Command` are used with the `Out-File` cmdlet to create two text files in the current directory, **Alias.txt** and **Command.txt**.</span></span>

<span data-ttu-id="692fb-134">`Select-String` gebruikt de para meter **Path** met het `*` Joker teken sterretje () om alle bestanden in de huidige map te doorzoeken met de bestandsnaam extensie `.txt` .</span><span class="sxs-lookup"><span data-stu-id="692fb-134">`Select-String` uses the **Path** parameter with the asterisk (`*`) wildcard to search all files in the current directory with the file name extension `.txt`.</span></span> <span data-ttu-id="692fb-135">De **pattern** -para meter geeft de tekst op die moet overeenkomen met **Get-**.</span><span class="sxs-lookup"><span data-stu-id="692fb-135">The **Pattern** parameter specifies the text to match **Get-**.</span></span> <span data-ttu-id="692fb-136">`Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="692fb-136">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="692fb-137">De bestands naam en het regel nummer vóór elke regel met inhoud die overeenkomt met de **patroon** parameter.</span><span class="sxs-lookup"><span data-stu-id="692fb-137">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="692fb-138">Voor beeld 3: zoeken naar een patroon overeenkomst</span><span class="sxs-lookup"><span data-stu-id="692fb-138">Example 3: Find a pattern match</span></span>

<span data-ttu-id="692fb-139">In dit voor beeld worden meerdere bestanden doorzocht om overeenkomsten te vinden voor het opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="692fb-139">In this example, multiple files are searched to find matches for the specified pattern.</span></span> <span data-ttu-id="692fb-140">Het patroon gebruikt een reguliere expressie-kwantor.</span><span class="sxs-lookup"><span data-stu-id="692fb-140">The pattern uses a regular expression quantifier.</span></span> <span data-ttu-id="692fb-141">Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="692fb-141">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span></span>

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

<span data-ttu-id="692fb-142">De `Select-String` cmdlet gebruikt twee para meters, **pad** en **patroon**.</span><span class="sxs-lookup"><span data-stu-id="692fb-142">The `Select-String` cmdlet uses two parameters, **Path** and **Pattern**.</span></span> <span data-ttu-id="692fb-143">De para meter **Path** maakt gebruik van de variabele `$PSHOME` die de Power shell-map opgeeft.</span><span class="sxs-lookup"><span data-stu-id="692fb-143">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="692fb-144">De rest van het pad bevat de submap en **-US** en geeft elk `*.txt` bestand in de map op.</span><span class="sxs-lookup"><span data-stu-id="692fb-144">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="692fb-145">De **patroon** parameter geeft aan dat deze overeenkomt met een vraag teken ( `?` ) in elk bestand.</span><span class="sxs-lookup"><span data-stu-id="692fb-145">The **Pattern** parameter specifies to match a question mark (`?`) in each file.</span></span> <span data-ttu-id="692fb-146">Een back slash ( `\` ) wordt gebruikt als escape-teken en is nodig omdat het vraag teken ( `?` ) een reguliere expressie-kwantor is.</span><span class="sxs-lookup"><span data-stu-id="692fb-146">A backslash (`\`) is used as an escape character and is necessary because the question mark (`?`) is a regular expression quantifier.</span></span> <span data-ttu-id="692fb-147">`Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="692fb-147">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="692fb-148">De bestands naam en het regel nummer vóór elke regel met inhoud die overeenkomt met de **patroon** parameter.</span><span class="sxs-lookup"><span data-stu-id="692fb-148">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="692fb-149">Voor beeld 4: Select-String gebruiken in een functie</span><span class="sxs-lookup"><span data-stu-id="692fb-149">Example 4: Use Select-String in a function</span></span>

<span data-ttu-id="692fb-150">In dit voor beeld wordt een functie gemaakt om te zoeken naar een patroon in de Help-bestanden van Power shell.</span><span class="sxs-lookup"><span data-stu-id="692fb-150">This example creates a function to search for a pattern in the PowerShell help files.</span></span> <span data-ttu-id="692fb-151">Voor dit voor beeld is de functie alleen aanwezig in de Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="692fb-151">For this example, the function only exists in the PowerShell session.</span></span> <span data-ttu-id="692fb-152">Wanneer de Power shell-sessie is gesloten, wordt de functie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="692fb-152">When the PowerShell session is closed, the function is deleted.</span></span> <span data-ttu-id="692fb-153">Zie [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="692fb-153">For more information, see [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span></span>

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:2:   about_ActivityCommonParameters
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:31:  see about_WorkflowCommonParameters.
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:33:  about_CommonParameters.
```

<span data-ttu-id="692fb-154">De functie wordt gemaakt op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="692fb-154">The function is created on the PowerShell command line.</span></span> <span data-ttu-id="692fb-155">De `Function` opdracht maakt gebruik van de naam **zoeken-Help**.</span><span class="sxs-lookup"><span data-stu-id="692fb-155">The `Function` command uses the name **Search-Help**.</span></span> <span data-ttu-id="692fb-156">Druk op **Enter** om instructies toe te voegen aan de functie.</span><span class="sxs-lookup"><span data-stu-id="692fb-156">Press **Enter** to begin adding statements to the function.</span></span> <span data-ttu-id="692fb-157">Voeg bij de `>>` prompt elke instructie toe en druk op **Enter** , zoals wordt weer gegeven in het voor beeld.</span><span class="sxs-lookup"><span data-stu-id="692fb-157">From the `>>` prompt, add each statement and press **Enter** as shown in the example.</span></span> <span data-ttu-id="692fb-158">Nadat het haakje is toegevoegd, keert u terug naar een Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="692fb-158">After the closing bracket is added, you're returned to a PowerShell prompt.</span></span>

<span data-ttu-id="692fb-159">De functie bevat twee opdrachten.</span><span class="sxs-lookup"><span data-stu-id="692fb-159">The function contains two commands.</span></span> <span data-ttu-id="692fb-160">De `$PSHelp` variabele slaat het pad op naar de Help-bestanden van Power shell.</span><span class="sxs-lookup"><span data-stu-id="692fb-160">The `$PSHelp` variable stores the path to the PowerShell help files.</span></span> <span data-ttu-id="692fb-161">`$PSHOME` is de Power shell-installatiemap met de submap **en-US** waarmee elk `*.txt` bestand in de Directory wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="692fb-161">`$PSHOME` is the PowerShell installation directory with the subdirectory **en-US** that specifies each `*.txt` file in the directory.</span></span>

<span data-ttu-id="692fb-162">De `Select-String` opdracht in de functie maakt gebruik van het **pad** en de **patroon** parameters.</span><span class="sxs-lookup"><span data-stu-id="692fb-162">The `Select-String` command in the function uses the **Path** and **Pattern** parameters.</span></span> <span data-ttu-id="692fb-163">De para meter **Path** gebruikt de `$PSHelp` variabele om het pad op te halen.</span><span class="sxs-lookup"><span data-stu-id="692fb-163">The **Path** parameter uses the `$PSHelp` variable to get the path.</span></span> <span data-ttu-id="692fb-164">De **patroon** parameter maakt gebruik van de teken reeks **About_** als Zoek criterium.</span><span class="sxs-lookup"><span data-stu-id="692fb-164">The **Pattern** parameter uses the string **About_** as the search criteria.</span></span>

<span data-ttu-id="692fb-165">Als u de functie wilt uitvoeren, typt u `Search-Help` .</span><span class="sxs-lookup"><span data-stu-id="692fb-165">To run the function, type `Search-Help`.</span></span> <span data-ttu-id="692fb-166">De opdracht van de functie `Select-String` geeft de uitvoer in de Power shell-console.</span><span class="sxs-lookup"><span data-stu-id="692fb-166">The function's `Select-String` command displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="692fb-167">Voor beeld 5: zoeken naar een teken reeks in een Windows-gebeurtenis logboek</span><span class="sxs-lookup"><span data-stu-id="692fb-167">Example 5: Search for a string in a Windows event log</span></span>

<span data-ttu-id="692fb-168">In dit voor beeld wordt gezocht naar een teken reeks in een Windows-gebeurtenis logboek.</span><span class="sxs-lookup"><span data-stu-id="692fb-168">This example searches for a string in a Windows event log.</span></span> <span data-ttu-id="692fb-169">De variabele `$_` vertegenwoordigt het huidige object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="692fb-169">The variable `$_` represents the current object in the pipeline.</span></span> <span data-ttu-id="692fb-170">Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="692fb-170">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

<span data-ttu-id="692fb-171">De `Get-WinEvent` cmdlet gebruikt de para meter **LogName** om het toepassings logboek op te geven.</span><span class="sxs-lookup"><span data-stu-id="692fb-171">The `Get-WinEvent` cmdlet uses the **LogName** parameter to specify the Application log.</span></span> <span data-ttu-id="692fb-172">De para meter **MaxEvents** haalt de 50 meest recente gebeurtenissen uit het logboek op.</span><span class="sxs-lookup"><span data-stu-id="692fb-172">The **MaxEvents** parameter gets the 50 most recent events from the log.</span></span> <span data-ttu-id="692fb-173">De logboek inhoud wordt opgeslagen in de variabele met de naam `$Events` .</span><span class="sxs-lookup"><span data-stu-id="692fb-173">The log content is stored in the variable named `$Events`.</span></span>

<span data-ttu-id="692fb-174">De `$Events` variabele wordt via de pijp lijn naar de `Select-String` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="692fb-174">The `$Events` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="692fb-175">`Select-String` maakt gebruik van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="692fb-175">`Select-String` uses the **InputObject** parameter.</span></span> <span data-ttu-id="692fb-176">De `$_` variabele vertegenwoordigt het huidige object en `message` is een eigenschap van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="692fb-176">The `$_` variable represents the current object and `message` is a property of the event.</span></span> <span data-ttu-id="692fb-177">De **patroon** parameter vissoort de teken reeks **is mislukt** en zoekt naar overeenkomsten in `$_.message` .</span><span class="sxs-lookup"><span data-stu-id="692fb-177">The **Pattern** parameter species the string **Failed** and searches for matches in `$_.message`.</span></span> <span data-ttu-id="692fb-178">`Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="692fb-178">`Select-String` displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="692fb-179">Voor beeld 6: een teken reeks zoeken in submappen</span><span class="sxs-lookup"><span data-stu-id="692fb-179">Example 6: Find a string in subdirectories</span></span>

<span data-ttu-id="692fb-180">In dit voor beeld wordt gezocht naar een map en alle submappen voor een specifieke teken reeks.</span><span class="sxs-lookup"><span data-stu-id="692fb-180">This example searches a directory and all of its subdirectories for a specific text string.</span></span>

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

<span data-ttu-id="692fb-181">`Get-ChildItem` maakt gebruik van de para meter **Path** om **C:\Windows\System32 \* . txt** op te geven.</span><span class="sxs-lookup"><span data-stu-id="692fb-181">`Get-ChildItem` uses the **Path** parameter to specify **C:\Windows\System32\*.txt**.</span></span> <span data-ttu-id="692fb-182">De **recursie** -para meter bevat de submappen.</span><span class="sxs-lookup"><span data-stu-id="692fb-182">The **Recurse** parameter includes the subdirectories.</span></span> <span data-ttu-id="692fb-183">De objecten worden naar beneden verzonden in de pijp lijn `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="692fb-183">The objects are sent down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="692fb-184">`Select-String` maakt gebruik van de **patroon** parameter en specificeert de teken reeks **micro soft**.</span><span class="sxs-lookup"><span data-stu-id="692fb-184">`Select-String` uses the **Pattern** parameter and specifies the string **Microsoft**.</span></span> <span data-ttu-id="692fb-185">De para meter **CaseSensitive** wordt gebruikt om de exacte case van de teken reeks overeen te laten komen.</span><span class="sxs-lookup"><span data-stu-id="692fb-185">The **CaseSensitive** parameter is used to match the exact case of the string.</span></span> <span data-ttu-id="692fb-186">`Select-String` Hiermee wordt de uitvoer in de Power shell-console weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="692fb-186">`Select-String` displays the output in the PowerShell console.</span></span>

> [!NOTE]
> <span data-ttu-id="692fb-187">Afhankelijk van uw machtigingen ziet u mogelijk de **toegang geweigerde** berichten in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="692fb-187">Dependent upon your permissions, you might see **Access denied** messages in the output.</span></span>

### <span data-ttu-id="692fb-188">Voor beeld 7: teken reeksen zoeken die niet overeenkomen met een patroon</span><span class="sxs-lookup"><span data-stu-id="692fb-188">Example 7: Find strings that do not match a pattern</span></span>

<span data-ttu-id="692fb-189">In dit voor beeld ziet u hoe u gegevens regels uitsluit die niet overeenkomen met een patroon.</span><span class="sxs-lookup"><span data-stu-id="692fb-189">This example shows how to exclude lines of data that don't match a pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

<span data-ttu-id="692fb-190">De `Get-Command` cmdlet verzendt objecten van de pijp lijn naar de `Out-File` om het **Command.txt** -bestand in de huidige map te maken.</span><span class="sxs-lookup"><span data-stu-id="692fb-190">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="692fb-191">`Select-String` maakt gebruik van de para meter **Path** om het **Command.txt** -bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="692fb-191">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="692fb-192">De para meter **pattern** geeft **Get** en **set** op als zoek patroon.</span><span class="sxs-lookup"><span data-stu-id="692fb-192">The **Pattern** parameter specifies **Get** and **Set** as the search pattern.</span></span> <span data-ttu-id="692fb-193">De para meter **NotMatch** uitgesloten **Get** en **set** van de resultaten.</span><span class="sxs-lookup"><span data-stu-id="692fb-193">The **NotMatch** parameter excludes **Get** and **Set** from the results.</span></span>
<span data-ttu-id="692fb-194">`Select-String` Hiermee wordt de uitvoer weer gegeven in de Power shell-console die geen **Get** of **set** bevat.</span><span class="sxs-lookup"><span data-stu-id="692fb-194">`Select-String` displays the output in the PowerShell console that doesn't include **Get** or **Set**.</span></span>

### <span data-ttu-id="692fb-195">Voor beeld 8: regels voor en na een overeenkomst zoeken</span><span class="sxs-lookup"><span data-stu-id="692fb-195">Example 8: Find lines before and after a match</span></span>

<span data-ttu-id="692fb-196">In dit voor beeld ziet u hoe u de lijnen voor en na het overeenkomende patroon kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="692fb-196">This example shows how to get the lines before and after the matched pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:1186:Cmdlet          Get-CmsMessage            3.0.0.0    Microsoft.PowerShell.Security
  Command.txt:1187:Cmdlet          Get-Command               3.0.0.0    Microsoft.PowerShell.Core
> Command.txt:1188:Cmdlet          Get-ComputerInfo          3.1.0.0    Microsoft.PowerShell.Management
> Command.txt:1189:Cmdlet          Get-ComputerRestorePoint  3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1190:Cmdlet          Get-Content               3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1191:Cmdlet          Get-ControlPanelItem      3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1192:Cmdlet          Get-Counter               3.0.0.0    Microsoft.PowerShell.Diagnostics
```

<span data-ttu-id="692fb-197">De `Get-Command` cmdlet verzendt objecten van de pijp lijn naar de `Out-File` om het **Command.txt** -bestand in de huidige map te maken.</span><span class="sxs-lookup"><span data-stu-id="692fb-197">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="692fb-198">`Select-String` maakt gebruik van de para meter **Path** om het **Command.txt** -bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="692fb-198">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="692fb-199">De para meter **pattern** geeft **Get-computer** op als zoek patroon.</span><span class="sxs-lookup"><span data-stu-id="692fb-199">The **Pattern** parameter specifies **Get-Computer** as the search pattern.</span></span> <span data-ttu-id="692fb-200">De para meter **context** gebruikt twee waarden, vóór en na, en markeert patroon overeenkomsten in de uitvoer met een punt haak ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="692fb-200">The **Context** parameter uses two values, before and after, and marks pattern matches in the output with an angle bracket (`>`).</span></span> <span data-ttu-id="692fb-201">Met de **context** parameter worden de twee regels vóór het eerste patroon uitgevoerd en worden er drie regels na het laatste patroon overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="692fb-201">The **Context** parameter outputs the two lines before the first pattern match and three lines after the last pattern match.</span></span>

### <span data-ttu-id="692fb-202">Voor beeld 9: alle patroon overeenkomsten zoeken</span><span class="sxs-lookup"><span data-stu-id="692fb-202">Example 9: Find all pattern matches</span></span>

<span data-ttu-id="692fb-203">In dit voor beeld ziet u hoe de para meter **AllMatches** elke overeenkomende patroon in een tekst regel vindt.</span><span class="sxs-lookup"><span data-stu-id="692fb-203">This example shows how the **AllMatches** parameter finds each pattern match in a line of text.</span></span> <span data-ttu-id="692fb-204">Standaard `Select-String` zoekt alleen het eerste exemplaar van een patroon in een tekst regel.</span><span class="sxs-lookup"><span data-stu-id="692fb-204">By default, `Select-String` only finds the first occurrence of a pattern in a line of text.</span></span> <span data-ttu-id="692fb-205">In dit voor beeld worden object eigenschappen gebruikt die met de cmdlet worden gevonden `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="692fb-205">This example uses object properties that are found with the `Get-Member` cmdlet.</span></span>

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:5:    Describes the parameters that Windows PowerShell
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:9:    Windows PowerShell Workflow adds the activity common

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

2073

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

2200
```

<span data-ttu-id="692fb-206">De `Get-ChildItem` cmdlet gebruikt de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="692fb-206">The `Get-ChildItem` cmdlet uses the **Path** parameter.</span></span> <span data-ttu-id="692fb-207">De para meter **Path** maakt gebruik van de variabele `$PSHOME` die de Power shell-map opgeeft.</span><span class="sxs-lookup"><span data-stu-id="692fb-207">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="692fb-208">De rest van het pad bevat de submap en **-US** en geeft elk `*.txt` bestand in de map op.</span><span class="sxs-lookup"><span data-stu-id="692fb-208">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="692fb-209">De `Get-ChildItem` objecten worden opgeslagen in de `$A` variabele.</span><span class="sxs-lookup"><span data-stu-id="692fb-209">The `Get-ChildItem` objects are stored in the `$A` variable.</span></span> <span data-ttu-id="692fb-210">De `$A` variabele wordt via de pijp lijn naar de `Select-String` cmdlet verzonden.</span><span class="sxs-lookup"><span data-stu-id="692fb-210">The `$A` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="692fb-211">`Select-String` maakt gebruik van de **patroon** parameter om te zoeken in elk bestand naar de teken reeks- **Power shell**.</span><span class="sxs-lookup"><span data-stu-id="692fb-211">`Select-String` uses the **Pattern** parameter to search each file for the string **PowerShell**.</span></span>

<span data-ttu-id="692fb-212">Van de Power shell-opdracht regel wordt de `$A` variabele-inhoud weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="692fb-212">From the PowerShell command line, the `$A` variable contents are displayed.</span></span> <span data-ttu-id="692fb-213">Er is een regel die twee exemplaren van de teken reeks **Power shell** bevat.</span><span class="sxs-lookup"><span data-stu-id="692fb-213">There's a line that contains two occurrences of the string **PowerShell**.</span></span>

<span data-ttu-id="692fb-214">De `$A.Matches` eigenschap geeft het eerste exemplaar van het patroon **Power shell** op elke regel.</span><span class="sxs-lookup"><span data-stu-id="692fb-214">The `$A.Matches` property lists the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="692fb-215">De `$A.Matches.Length` eigenschap telt het eerste exemplaar van het patroon **Power shell** op elke regel.</span><span class="sxs-lookup"><span data-stu-id="692fb-215">The `$A.Matches.Length` property counts the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="692fb-216">De `$B` variabele maakt gebruik van dezelfde `Get-ChildItem` en `Select-String` cmdlets, maar voegt de para meter **AllMatches** toe.</span><span class="sxs-lookup"><span data-stu-id="692fb-216">The `$B` variable uses the same `Get-ChildItem` and `Select-String` cmdlets, but adds the **AllMatches** parameter.</span></span> <span data-ttu-id="692fb-217">**AllMatches** vindt elk exemplaar van het patroon **Power shell** op elke regel.</span><span class="sxs-lookup"><span data-stu-id="692fb-217">**AllMatches** finds each occurrence of the pattern **PowerShell** on each line.</span></span> <span data-ttu-id="692fb-218">De objecten die zijn opgeslagen in de `$A` `$B` variabelen en zijn identiek.</span><span class="sxs-lookup"><span data-stu-id="692fb-218">The objects stored in the `$A` and `$B` variables are identical.</span></span>

<span data-ttu-id="692fb-219">De `$B.Matches.Length` eigenschap neemt toe vanwege elke regel, waarbij elk exemplaar van het patroon **Power shell** wordt geteld.</span><span class="sxs-lookup"><span data-stu-id="692fb-219">The `$B.Matches.Length` property increases because for each line, every occurrence of the pattern **PowerShell** is counted.</span></span>

## <span data-ttu-id="692fb-220">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="692fb-220">PARAMETERS</span></span>

### <span data-ttu-id="692fb-221">-AllMatches</span><span class="sxs-lookup"><span data-stu-id="692fb-221">-AllMatches</span></span>

<span data-ttu-id="692fb-222">Geeft aan dat de cmdlet zoekt naar meer dan één overeenkomst in elke regel tekst.</span><span class="sxs-lookup"><span data-stu-id="692fb-222">Indicates that the cmdlet searches for more than one match in each line of text.</span></span> <span data-ttu-id="692fb-223">Zonder deze para meter wordt `Select-String` alleen gezocht naar de eerste overeenkomst in elke regel tekst.</span><span class="sxs-lookup"><span data-stu-id="692fb-223">Without this parameter, `Select-String` finds only the first match in each line of text.</span></span>

<span data-ttu-id="692fb-224">Wanneer er `Select-String` meer dan één overeenkomst in een tekst regel wordt gevonden, wordt er nog steeds slechts één **MatchInfo** -object voor de regel geleverd, maar de eigenschap **matchs** van het object bevat alle overeenkomsten.</span><span class="sxs-lookup"><span data-stu-id="692fb-224">When `Select-String` finds more than one match in a line of text, it still emits only one **MatchInfo** object for the line, but the **Matches** property of the object contains all the matches.</span></span>

> [!NOTE]
> <span data-ttu-id="692fb-225">Deze para meter wordt genegeerd als deze wordt gebruikt in combi natie met de para meter **SimpleMatch** .</span><span class="sxs-lookup"><span data-stu-id="692fb-225">This parameter is ignored when used in combination with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="692fb-226">Als u alle overeenkomsten wilt retour neren en het patroon waarnaar u zoekt reguliere expressie tekens bevat, moet u deze tekens weglaten in plaats van **SimpleMatch** te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="692fb-226">If you wish to return all matches and the pattern that you are searching for contains regular expression characters, you must escape those characters rather than using **SimpleMatch**.</span></span> <span data-ttu-id="692fb-227">Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) voor meer informatie over reguliere expressies voor Escapes.</span><span class="sxs-lookup"><span data-stu-id="692fb-227">See [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) for more information about escaping regular expressions.</span></span>

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

### <span data-ttu-id="692fb-228">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="692fb-228">-CaseSensitive</span></span>

<span data-ttu-id="692fb-229">Geeft aan dat de cmdlets overeenkomen met hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="692fb-229">Indicates that the cmdlet matches are case-sensitive.</span></span> <span data-ttu-id="692fb-230">Standaard zijn niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="692fb-230">By default, matches aren't case-sensitive.</span></span>

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

### <span data-ttu-id="692fb-231">-Context</span><span class="sxs-lookup"><span data-stu-id="692fb-231">-Context</span></span>

<span data-ttu-id="692fb-232">Hiermee wordt het opgegeven aantal regels vóór en na de lijn die overeenkomt met het patroon vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="692fb-232">Captures the specified number of lines before and after the line that matches the pattern.</span></span>

<span data-ttu-id="692fb-233">Als u één getal als waarde voor deze para meter opgeeft, wordt het aantal regels bepaald dat voor en na de overeenkomst is vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="692fb-233">If you enter one number as the value of this parameter, that number determines the number of lines captured before and after the match.</span></span> <span data-ttu-id="692fb-234">Als u twee getallen opgeeft als waarde, bepaalt het eerste getal het aantal regels vóór de overeenkomst en het tweede getal bepaalt het aantal regels na de overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="692fb-234">If you enter two numbers as the value, the first number determines the number of lines before the match and the second number determines the number of lines after the match.</span></span> <span data-ttu-id="692fb-235">Bijvoorbeeld `-Context 2,3`.</span><span class="sxs-lookup"><span data-stu-id="692fb-235">For example, `-Context 2,3`.</span></span>

<span data-ttu-id="692fb-236">In de standaard weergave worden regels met een overeenkomst aangeduid met een rechter punt haak ( `>` ) (ASCII 62) in de eerste kolom van de weer gave.</span><span class="sxs-lookup"><span data-stu-id="692fb-236">In the default display, lines with a match are indicated by a right angle bracket (`>`) (ASCII 62) in the first column of the display.</span></span> <span data-ttu-id="692fb-237">Niet-gemarkeerde regels zijn de context.</span><span class="sxs-lookup"><span data-stu-id="692fb-237">Unmarked lines are the context.</span></span>

<span data-ttu-id="692fb-238">De para meter **context** wijzigt niet het aantal objecten dat door is gegenereerd `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="692fb-238">The **Context** parameter doesn't change the number of objects generated by `Select-String`.</span></span>
<span data-ttu-id="692fb-239">`Select-String` genereert één [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) -object voor elke overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="692fb-239">`Select-String` generates one [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) object for each match.</span></span> <span data-ttu-id="692fb-240">De context wordt opgeslagen als een matrix met teken reeksen in de **context** eigenschap van het object.</span><span class="sxs-lookup"><span data-stu-id="692fb-240">The context is stored as an array of strings in the **Context** property of the object.</span></span>

<span data-ttu-id="692fb-241">Wanneer de uitvoer van een `Select-String` opdracht door de pijp lijn naar een andere opdracht wordt verzonden `Select-String` , doorzoekt de ontvangende opdracht alleen de tekst in de overeenkomende lijn.</span><span class="sxs-lookup"><span data-stu-id="692fb-241">When the output of a `Select-String` command is sent down the pipeline to another `Select-String` command, the receiving command searches only the text in the matched line.</span></span> <span data-ttu-id="692fb-242">De overeenkomende lijn is de waarde van de **regel** eigenschap van het object **MatchInfo** , niet de tekst in de context regels.</span><span class="sxs-lookup"><span data-stu-id="692fb-242">The matched line is the value of the **Line** property of the **MatchInfo** object, not the text in the context lines.</span></span> <span data-ttu-id="692fb-243">Als gevolg hiervan is de **context** parameter niet geldig voor de ontvangende `Select-String` opdracht.</span><span class="sxs-lookup"><span data-stu-id="692fb-243">As a result, the **Context** parameter isn't valid on the receiving `Select-String` command.</span></span>

<span data-ttu-id="692fb-244">Wanneer de context een overeenkomst bevat, bevat het **MatchInfo** -object voor elke overeenkomst alle context regels, maar worden de overlappende lijnen slechts eenmaal in de weer gave weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="692fb-244">When the context includes a match, the **MatchInfo** object for each match includes all the context lines, but the overlapping lines appear only once in the display.</span></span>

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

### <span data-ttu-id="692fb-245">-Encoding</span><span class="sxs-lookup"><span data-stu-id="692fb-245">-Encoding</span></span>

<span data-ttu-id="692fb-246">Hiermee geeft u het type code ring voor het doel bestand op.</span><span class="sxs-lookup"><span data-stu-id="692fb-246">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="692fb-247">De standaardwaarde is `default`.</span><span class="sxs-lookup"><span data-stu-id="692fb-247">The default value is `default`.</span></span>

<span data-ttu-id="692fb-248">De acceptabele waarden voor deze para meter zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="692fb-248">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="692fb-249">`ascii` Maakt gebruik van ASCII-tekenset (7-bits).</span><span class="sxs-lookup"><span data-stu-id="692fb-249">`ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="692fb-250">`bigendianunicode` Maakt gebruik van UTF-16 met de byte volgorde big endian.</span><span class="sxs-lookup"><span data-stu-id="692fb-250">`bigendianunicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="692fb-251">`default` Gebruikt de code ring die overeenkomt met de actieve code tabel van het systeem (meestal ANSI).</span><span class="sxs-lookup"><span data-stu-id="692fb-251">`default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="692fb-252">`oem` Gebruikt de code ring die overeenkomt met de huidige OEM-code tabel van het systeem.</span><span class="sxs-lookup"><span data-stu-id="692fb-252">`oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="692fb-253">`unicode` Maakt gebruik van UTF-16 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="692fb-253">`unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="692fb-254">`utf7` Maakt gebruik van UTF-7.</span><span class="sxs-lookup"><span data-stu-id="692fb-254">`utf7` Uses UTF-7.</span></span>
- <span data-ttu-id="692fb-255">`utf8` Maakt gebruik van UTF-8.</span><span class="sxs-lookup"><span data-stu-id="692fb-255">`utf8` Uses UTF-8.</span></span>
- <span data-ttu-id="692fb-256">`utf32` Maakt gebruik van UTF-32 met de byte volgorde little endian.</span><span class="sxs-lookup"><span data-stu-id="692fb-256">`utf32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="692fb-257">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="692fb-257">-Exclude</span></span>

<span data-ttu-id="692fb-258">Sluit de opgegeven items uit.</span><span class="sxs-lookup"><span data-stu-id="692fb-258">Exclude the specified items.</span></span> <span data-ttu-id="692fb-259">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="692fb-259">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="692fb-260">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="692fb-260">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="692fb-261">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="692fb-261">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="692fb-262">-Include</span><span class="sxs-lookup"><span data-stu-id="692fb-262">-Include</span></span>

<span data-ttu-id="692fb-263">Bevat de opgegeven items.</span><span class="sxs-lookup"><span data-stu-id="692fb-263">Includes the specified items.</span></span> <span data-ttu-id="692fb-264">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="692fb-264">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="692fb-265">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="692fb-265">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="692fb-266">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="692fb-266">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="692fb-267">-Input object</span><span class="sxs-lookup"><span data-stu-id="692fb-267">-InputObject</span></span>

<span data-ttu-id="692fb-268">Geeft de tekst aan waarnaar moet worden gezocht.</span><span class="sxs-lookup"><span data-stu-id="692fb-268">Specifies the text to be searched.</span></span> <span data-ttu-id="692fb-269">Voer een variabele in die de tekst bevat of typ een opdracht of expressie waarmee de tekst wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="692fb-269">Enter a variable that contains the text, or type a command or expression that gets the text.</span></span>

<span data-ttu-id="692fb-270">Het gebruik van de para meter **input object** is niet hetzelfde als het verzenden van teken reeksen naar de pijp lijn `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="692fb-270">Using the **InputObject** parameter isn't the same as sending strings down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="692fb-271">Wanneer u meer dan een teken reeks naar de `Select-String` cmdlet Pipet, zoekt het naar de opgegeven tekst in elke teken reeks en retourneert elke teken reeks die de Zoek tekst bevat.</span><span class="sxs-lookup"><span data-stu-id="692fb-271">When you pipe more than one string to the `Select-String` cmdlet, it searches for the specified text in each string and returns each string that contains the search text.</span></span>

<span data-ttu-id="692fb-272">Wanneer u de para meter **input object** gebruikt voor het verzenden van een verzameling teken reeksen, `Select-String` behandelt de verzameling als één gecombineerde teken reeks.</span><span class="sxs-lookup"><span data-stu-id="692fb-272">When you use the **InputObject** parameter to submit a collection of strings, `Select-String` treats the collection as a single combined string.</span></span> <span data-ttu-id="692fb-273">`Select-String` retourneert de teken reeksen als eenheid als de Zoek tekst in een wille keurige teken reeks wordt gevonden.</span><span class="sxs-lookup"><span data-stu-id="692fb-273">`Select-String` returns the strings as a unit if it finds the search text in any string.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="692fb-274">-Lijst</span><span class="sxs-lookup"><span data-stu-id="692fb-274">-List</span></span>

<span data-ttu-id="692fb-275">Alleen het eerste exemplaar van de overeenkomende tekst wordt geretourneerd vanuit elk invoer bestand.</span><span class="sxs-lookup"><span data-stu-id="692fb-275">Only the first instance of matching text is returned from each input file.</span></span> <span data-ttu-id="692fb-276">Dit is de meest efficiënte manier om een lijst met bestanden op te halen met inhoud die overeenkomt met de reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="692fb-276">This is the most efficient way to retrieve a list of files that have contents matching the regular expression.</span></span>

<span data-ttu-id="692fb-277">`Select-String`Retourneert standaard een **MatchInfo** -object voor elke gevonden overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="692fb-277">By default, `Select-String` returns a **MatchInfo** object for each match it finds.</span></span>

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

### <span data-ttu-id="692fb-278">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="692fb-278">-LiteralPath</span></span>

<span data-ttu-id="692fb-279">Hiermee geeft u het pad op naar de bestanden die moeten worden doorzocht.</span><span class="sxs-lookup"><span data-stu-id="692fb-279">Specifies the path to the files to be searched.</span></span> <span data-ttu-id="692fb-280">De waarde van de para meter **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="692fb-280">The value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="692fb-281">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="692fb-281">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="692fb-282">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="692fb-282">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="692fb-283">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="692fb-283">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="692fb-284">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="692fb-284">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralFile
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="692fb-285">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="692fb-285">-NotMatch</span></span>

<span data-ttu-id="692fb-286">De para meter **NotMatch** vindt tekst die niet overeenkomt met het opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="692fb-286">The **NotMatch** parameter finds text that doesn't match the specified pattern.</span></span>

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

### <span data-ttu-id="692fb-287">-Path</span><span class="sxs-lookup"><span data-stu-id="692fb-287">-Path</span></span>

<span data-ttu-id="692fb-288">Hiermee geeft u het pad op naar de bestanden waarnaar moet worden gezocht.</span><span class="sxs-lookup"><span data-stu-id="692fb-288">Specifies the path to the files to search.</span></span> <span data-ttu-id="692fb-289">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="692fb-289">Wildcards are permitted.</span></span> <span data-ttu-id="692fb-290">De standaard locatie is de lokale map.</span><span class="sxs-lookup"><span data-stu-id="692fb-290">The default location is the local directory.</span></span>

<span data-ttu-id="692fb-291">Bestanden opgeven in de Directory, zoals `log1.txt` , `*.doc` of `*.*` .</span><span class="sxs-lookup"><span data-stu-id="692fb-291">Specify files in the directory, such as `log1.txt`, `*.doc`, or `*.*`.</span></span> <span data-ttu-id="692fb-292">Als u alleen een map opgeeft, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="692fb-292">If you specify only a directory, the command fails.</span></span>

```yaml
Type: System.String[]
Parameter Sets: File
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="692fb-293">-Patroon</span><span class="sxs-lookup"><span data-stu-id="692fb-293">-Pattern</span></span>

<span data-ttu-id="692fb-294">Hiermee geeft u de tekst op elke regel moet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="692fb-294">Specifies the text to find on each line.</span></span> <span data-ttu-id="692fb-295">De patroon waarde wordt beschouwd als een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="692fb-295">The pattern value is treated as a regular expression.</span></span>

<span data-ttu-id="692fb-296">Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)voor meer informatie over reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="692fb-296">To learn about regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

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

### <span data-ttu-id="692fb-297">-Quiet</span><span class="sxs-lookup"><span data-stu-id="692fb-297">-Quiet</span></span>

<span data-ttu-id="692fb-298">Geeft aan dat de cmdlet een Booleaanse waarde retourneert (True of false) in plaats van een **MatchInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="692fb-298">Indicates that the cmdlet returns a Boolean value (True or False), instead of a **MatchInfo** object.</span></span> <span data-ttu-id="692fb-299">De waarde is True als het patroon is gevonden; anders is de waarde false.</span><span class="sxs-lookup"><span data-stu-id="692fb-299">The value is True if the pattern is found; otherwise the value is False.</span></span>

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

### <span data-ttu-id="692fb-300">-SimpleMatch</span><span class="sxs-lookup"><span data-stu-id="692fb-300">-SimpleMatch</span></span>

<span data-ttu-id="692fb-301">Geeft aan dat de cmdlet een eenvoudige overeenkomst gebruikt in plaats van een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="692fb-301">Indicates that the cmdlet uses a simple match rather than a regular expression match.</span></span> <span data-ttu-id="692fb-302">In een eenvoudige overeenkomst `Select-String` zoekt de invoer voor de tekst in de para meter **pattern** .</span><span class="sxs-lookup"><span data-stu-id="692fb-302">In a simple match, `Select-String` searches the input for the text in the **Pattern** parameter.</span></span> <span data-ttu-id="692fb-303">De waarde van de **patroon** parameter wordt niet geïnterpreteerd als een reguliere expressie-instructie.</span><span class="sxs-lookup"><span data-stu-id="692fb-303">It doesn't interpret the value of the **Pattern** parameter as a regular expression statement.</span></span>

<span data-ttu-id="692fb-304">Wanneer **SimpleMatch** wordt gebruikt, is de eigenschap **matchers** van het geretourneerde **MatchInfo** -object ook leeg.</span><span class="sxs-lookup"><span data-stu-id="692fb-304">Also, when **SimpleMatch** is used, the **Matches** property of the **MatchInfo** object returned is empty.</span></span>

> [!NOTE]
> <span data-ttu-id="692fb-305">Als deze para meter wordt gebruikt met de para meter **AllMatches** , wordt de **AllMatches** genegeerd.</span><span class="sxs-lookup"><span data-stu-id="692fb-305">When this parameter is used with the **AllMatches** parameter, the **AllMatches** is ignored.</span></span>

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

### <span data-ttu-id="692fb-306">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="692fb-306">CommonParameters</span></span>

<span data-ttu-id="692fb-307">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="692fb-307">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="692fb-308">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="692fb-308">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="692fb-309">INVOER</span><span class="sxs-lookup"><span data-stu-id="692fb-309">INPUTS</span></span>

### <span data-ttu-id="692fb-310">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="692fb-310">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="692fb-311">U kunt elk object dat een **toString** -methode heeft, aan het sluis teken toe `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="692fb-311">You can pipe any object that has a **ToString** method to `Select-String`.</span></span>

## <span data-ttu-id="692fb-312">UITVOER</span><span class="sxs-lookup"><span data-stu-id="692fb-312">OUTPUTS</span></span>

### <span data-ttu-id="692fb-313">Micro soft. Power shell. commands. MatchInfo of System. Boolean</span><span class="sxs-lookup"><span data-stu-id="692fb-313">Microsoft.PowerShell.Commands.MatchInfo or System.Boolean</span></span>

<span data-ttu-id="692fb-314">Standaard is de uitvoer een set **MatchInfo** -objecten met één voor elke gevonden overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="692fb-314">By default, the output is a set of **MatchInfo** objects with one for each match found.</span></span> <span data-ttu-id="692fb-315">Als u de **stille** para meter gebruikt, is de uitvoer een Booleaanse waarde die aangeeft of het patroon is gevonden.</span><span class="sxs-lookup"><span data-stu-id="692fb-315">If you use the **Quiet** parameter, the output is a Boolean value indicating whether the pattern was found.</span></span>

## <span data-ttu-id="692fb-316">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="692fb-316">NOTES</span></span>

<span data-ttu-id="692fb-317">`Select-String` is vergelijkbaar met **grep** in UNIX of **findstr.exe** in Windows.</span><span class="sxs-lookup"><span data-stu-id="692fb-317">`Select-String` is similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="692fb-318">De **SLS** -alias voor de `Select-String` cmdlet is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="692fb-318">The **sls** alias for the `Select-String` cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="692fb-319">Volgens de [goedgekeurde werk woorden voor Power shell-opdrachten](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)is het officiële alias voorvoegsel voor `Select-*` cmdlets `sc` `sl` .</span><span class="sxs-lookup"><span data-stu-id="692fb-319">According to [Approved Verbs for PowerShell Commands](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), the official alias prefix for `Select-*` cmdlets is `sc`, not `sl`.</span></span> <span data-ttu-id="692fb-320">Daarom moet de juiste alias voor `Select-String` zijn `scs` , niet `sls` .</span><span class="sxs-lookup"><span data-stu-id="692fb-320">Therefore, the proper alias for `Select-String` should be `scs`, not `sls`.</span></span> <span data-ttu-id="692fb-321">Dit is een uitzonde ring op deze regel.</span><span class="sxs-lookup"><span data-stu-id="692fb-321">This is an exception to this rule.</span></span>

<span data-ttu-id="692fb-322">Als u wilt gebruiken `Select-String` , typt u de tekst die u wilt zoeken als waarde voor de **patroon** parameter.</span><span class="sxs-lookup"><span data-stu-id="692fb-322">To use `Select-String`, type the text that you want to find as the value of the **Pattern** parameter.</span></span> <span data-ttu-id="692fb-323">Gebruik de volgende criteria om de tekst op te geven die moet worden doorzocht:</span><span class="sxs-lookup"><span data-stu-id="692fb-323">To specify the text to be searched, use the following criteria:</span></span>

- <span data-ttu-id="692fb-324">Typ de tekst in een teken reeks tussen aanhalings tekens en sleep deze naar `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="692fb-324">Type the text in a quoted string, and then pipe it to `Select-String`.</span></span>
- <span data-ttu-id="692fb-325">Sla een teken reeks op in een variabele en geef de variabele op als de waarde van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="692fb-325">Store a text string in a variable, and then specify the variable as the value of the **InputObject** parameter.</span></span>
- <span data-ttu-id="692fb-326">Als de tekst wordt opgeslagen in bestanden, gebruikt u de para meter **Path** om het pad naar de bestanden op te geven.</span><span class="sxs-lookup"><span data-stu-id="692fb-326">If the text is stored in files, use the **Path** parameter to specify the path to the files.</span></span>

<span data-ttu-id="692fb-327">`Select-String`De waarde van de **pattern** -para meter wordt standaard geïnterpreteerd als een reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="692fb-327">By default, `Select-String` interprets the value of the **Pattern** parameter as a regular expression.</span></span> <span data-ttu-id="692fb-328">Zie [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="692fb-328">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span> <span data-ttu-id="692fb-329">U kunt de para meter **SimpleMatch** gebruiken om de reguliere expressie overeenkomst te overschrijven.</span><span class="sxs-lookup"><span data-stu-id="692fb-329">You can use the **SimpleMatch** parameter to override the regular expression matching.</span></span> <span data-ttu-id="692fb-330">De para meter **SimpleMatch** vindt instanties van de waarde van de para meter **pattern** in de invoer.</span><span class="sxs-lookup"><span data-stu-id="692fb-330">The **SimpleMatch** parameter finds instances of the value of the **Pattern** parameter in the input.</span></span>

<span data-ttu-id="692fb-331">De standaard uitvoer van `Select-String` is een **MatchInfo** -object, dat gedetailleerde informatie over de overeenkomsten bevat.</span><span class="sxs-lookup"><span data-stu-id="692fb-331">The default output of `Select-String` is a **MatchInfo** object, which includes detailed information about the matches.</span></span> <span data-ttu-id="692fb-332">De informatie in het object is handig wanneer u zoekt naar tekst in bestanden, omdat **MatchInfo** -objecten eigenschappen hebben zoals **filename** en **Line**.</span><span class="sxs-lookup"><span data-stu-id="692fb-332">The information in the object is useful when you're searching for text in files, because **MatchInfo** objects have properties such as **Filename** and **Line**.</span></span> <span data-ttu-id="692fb-333">Wanneer de invoer niet van het bestand is, is de waarde van deze para meters **InputStream**.</span><span class="sxs-lookup"><span data-stu-id="692fb-333">When the input isn't from the file, the value of these parameters is **InputStream**.</span></span>

<span data-ttu-id="692fb-334">Als u de gegevens in het **MatchInfo** -object niet nodig hebt, gebruikt u de **stille** para meter.</span><span class="sxs-lookup"><span data-stu-id="692fb-334">If you don't need the information in the **MatchInfo** object, use the **Quiet** parameter.</span></span> <span data-ttu-id="692fb-335">De **stille** para meter retourneert een Booleaanse waarde (waar of onwaar) om aan te geven of deze een overeenkomst heeft gevonden in plaats van een **MatchInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="692fb-335">The **Quiet** parameter returns a Boolean value (True or False) to indicate whether it found a match, instead of a **MatchInfo** object.</span></span>

<span data-ttu-id="692fb-336">Bij overeenkomende woord groepen `Select-String` gebruikt de huidige cultuur die is ingesteld voor het systeem.</span><span class="sxs-lookup"><span data-stu-id="692fb-336">When matching phrases, `Select-String` uses the current culture that is set for the system.</span></span> <span data-ttu-id="692fb-337">Als u de huidige cultuur wilt zoeken, gebruikt u de `Get-Culture` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="692fb-337">To find the current culture, use the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="692fb-338">Als u de eigenschappen van een **MatchInfo** -object wilt zoeken, typt u de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="692fb-338">To find the properties of a **MatchInfo** object, type the following command:</span></span>

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## <span data-ttu-id="692fb-339">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="692fb-339">RELATED LINKS</span></span>

[<span data-ttu-id="692fb-340">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="692fb-340">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="692fb-341">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="692fb-341">about_Comparison_Operators</span></span>](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[<span data-ttu-id="692fb-342">about_Functions</span><span class="sxs-lookup"><span data-stu-id="692fb-342">about_Functions</span></span>](../Microsoft.PowerShell.Core/About/about_Functions.md)

[<span data-ttu-id="692fb-343">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="692fb-343">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="692fb-344">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="692fb-344">about_Regular_Expressions</span></span>](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[<span data-ttu-id="692fb-345">Get-alias</span><span class="sxs-lookup"><span data-stu-id="692fb-345">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="692fb-346">Get-Child item</span><span class="sxs-lookup"><span data-stu-id="692fb-346">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="692fb-347">Get-Command</span><span class="sxs-lookup"><span data-stu-id="692fb-347">Get-Command</span></span>](../Microsoft.PowerShell.Core/Get-Command.md)

[<span data-ttu-id="692fb-348">Get-member</span><span class="sxs-lookup"><span data-stu-id="692fb-348">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="692fb-349">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="692fb-349">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="692fb-350">Out-file</span><span class="sxs-lookup"><span data-stu-id="692fb-350">Out-File</span></span>](Out-File.md)
