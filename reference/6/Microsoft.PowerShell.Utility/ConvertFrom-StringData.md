---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: 8ffb7a33bb1b4b5409c48445b88a8eb58f9b93b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251143"
---
# <span data-ttu-id="10140-103">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="10140-103">ConvertFrom-StringData</span></span>

## <span data-ttu-id="10140-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="10140-104">SYNOPSIS</span></span>
<span data-ttu-id="10140-105">Hiermee wordt een teken reeks met een of meer sleutel-en waardeparen geconverteerd naar een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="10140-105">Converts a string containing one or more key and value pairs to a hash table.</span></span>

## <span data-ttu-id="10140-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="10140-106">SYNTAX</span></span>

### <span data-ttu-id="10140-107">Alles</span><span class="sxs-lookup"><span data-stu-id="10140-107">All</span></span>

```
ConvertFrom-StringData [-StringData] <String> [<CommonParameters>]
```

## <span data-ttu-id="10140-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="10140-108">DESCRIPTION</span></span>

<span data-ttu-id="10140-109">Met de `ConvertFrom-StringData` cmdlet wordt een teken reeks met een of meer sleutel-en waardeparen geconverteerd naar een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="10140-109">The `ConvertFrom-StringData` cmdlet converts a string that contains one or more key and value pairs into a hash table.</span></span> <span data-ttu-id="10140-110">Omdat elke sleutel/waarde-paar op een afzonderlijke regel moet staan, worden hier vaak de invoer gegevens gebruikt.</span><span class="sxs-lookup"><span data-stu-id="10140-110">Because each key-value pair must be on a separate line, here-strings are often used as the input format.</span></span> <span data-ttu-id="10140-111">Standaard moet de **sleutel** worden gescheiden van de **waarde** met een teken () van het gelijkteken ( `=` ).</span><span class="sxs-lookup"><span data-stu-id="10140-111">By default, the **key** must be separated from the **value** by an equals sign (`=`) character.</span></span>

<span data-ttu-id="10140-112">De `ConvertFrom-StringData` cmdlet wordt beschouwd als een veilige cmdlet die kan worden gebruikt in de `DATA` sectie van een script of functie.</span><span class="sxs-lookup"><span data-stu-id="10140-112">The `ConvertFrom-StringData` cmdlet is considered to be a safe cmdlet that can be used in the `DATA` section of a script or function.</span></span> <span data-ttu-id="10140-113">Bij gebruik in een `DATA` sectie moet de inhoud van de teken reeks voldoen aan de regels voor een gegevens sectie.</span><span class="sxs-lookup"><span data-stu-id="10140-113">When used in a `DATA` section, the contents of the string must conform to the rules for a DATA section.</span></span> <span data-ttu-id="10140-114">Zie [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="10140-114">For more information, see [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).</span></span>

<span data-ttu-id="10140-115">`ConvertFrom-StringData` ondersteunt escape-teken reeksen die zijn toegestaan door conventionele hulpprogram ma's voor machine vertalingen.</span><span class="sxs-lookup"><span data-stu-id="10140-115">`ConvertFrom-StringData` supports escape character sequences that are allowed by conventional machine translation tools.</span></span> <span data-ttu-id="10140-116">Dat wil zeggen dat de cmdlet backslashes () kan interpreteren `\` als escape tekens in de teken reeks gegevens met behulp van de [methode regex. unesc](/dotnet/api/system.text.regularexpressions.regex.unescape), in plaats van het Power shell apostroffen-teken ( \` ) dat normaal gesp roken het einde van een regel in een script zou Signa leren.</span><span class="sxs-lookup"><span data-stu-id="10140-116">That is, the cmdlet can interpret backslashes (`\`) as escape characters in the string data by using the [Regex.Unescape Method](/dotnet/api/system.text.regularexpressions.regex.unescape), instead of the PowerShell backtick character (\`) that would normally signal the end of a line in a script.</span></span> <span data-ttu-id="10140-117">In de teken reeks die hier is, werkt het apostroffen-teken niet.</span><span class="sxs-lookup"><span data-stu-id="10140-117">Inside the here-string, the backtick character does not work.</span></span> <span data-ttu-id="10140-118">U kunt ook een letterlijke back slash in uw resultaten behouden door deze te escapen met een voor gaande back slash, bijvoorbeeld: `\\` .</span><span class="sxs-lookup"><span data-stu-id="10140-118">You can also preserve a literal backslash in your results by escaping it with a preceding backslash, like this: `\\`.</span></span> <span data-ttu-id="10140-119">Back slash-tekens, zoals die vaak worden gebruikt in bestands paden, kunnen worden weer gegeven als ongeldige escape reeksen in uw resultaten.</span><span class="sxs-lookup"><span data-stu-id="10140-119">Unescaped backslash characters, such as those that are commonly used in file paths, can render as illegal escape sequences in your results.</span></span>

## <span data-ttu-id="10140-120">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="10140-120">EXAMPLES</span></span>

### <span data-ttu-id="10140-121">Voor beeld 1: een enkel aanhalings teken naar een hash-tabel converteren</span><span class="sxs-lookup"><span data-stu-id="10140-121">Example 1: Convert a single-quoted here-string to a hash table</span></span>

<span data-ttu-id="10140-122">In dit voor beeld wordt een teken reeks met enkele aanhalings tekens van gebruikers berichten geconverteerd naar een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="10140-122">This example converts a single-quoted here-string of user messages into a hash table.</span></span> <span data-ttu-id="10140-123">In een teken reeks met enkele aanhalings tekens worden waarden niet vervangen door variabelen en expressies worden niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="10140-123">In a single-quoted string, values are not substituted for variables and expressions are not evaluated.</span></span>
<span data-ttu-id="10140-124">`ConvertFrom-StringData`Met de cmdlet wordt de waarde in de `$Here` variabele geconverteerd naar een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="10140-124">The `ConvertFrom-StringData` cmdlet converts the value in the `$Here` variable to a hash table.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
ConvertFrom-StringData -StringData $Here
```

```Output
Name                           Value
----                           -----
Msg3                           The specified variable does not exist.
Msg2                           Credentials are required for this command.
Msg1                           The string parameter is required.
```

### <span data-ttu-id="10140-125">Voor beeld 2: een hier een teken reeks converteren met een opmerking</span><span class="sxs-lookup"><span data-stu-id="10140-125">Example 2: Convert a here-string containing a comment</span></span>

<span data-ttu-id="10140-126">In dit voor beeld wordt een hier-teken reeks geconverteerd die een opmerking en meerdere sleutel-waardeparen in een hash-tabel bevat.</span><span class="sxs-lookup"><span data-stu-id="10140-126">This example converts a here-string that contains a comment and multiple key-value pairs into a hash table.</span></span>

```powershell
ConvertFrom-StringData -StringData @'
Name = Disks.ps1

# Category is optional.

Category = Storage
Cost = Free
'@
```

```Output
Name                           Value
----                           -----
Cost                           Free
Category                       Storage
Name                           Disks.ps1
```

<span data-ttu-id="10140-127">De waarde van de para meter **StringData** is een hier-teken reeks, in plaats van een variabele die een hier-teken reeks bevat.</span><span class="sxs-lookup"><span data-stu-id="10140-127">The value of the **StringData** parameter is a here-string, instead of a variable that contains a here-string.</span></span> <span data-ttu-id="10140-128">Beide indelingen zijn geldig.</span><span class="sxs-lookup"><span data-stu-id="10140-128">Either format is valid.</span></span> <span data-ttu-id="10140-129">De volgende teken reeks bevat een opmerking over een van de teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="10140-129">The here-string includes a comment about one of the strings.</span></span>
<span data-ttu-id="10140-130">`ConvertFrom-StringData` opmerkingen met één regel worden genegeerd, maar het `#` teken moet het eerste niet-spatie teken op de regel zijn.</span><span class="sxs-lookup"><span data-stu-id="10140-130">`ConvertFrom-StringData` ignores single-line comments, but the `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="10140-131">Alle tekens op de regel na de `#` worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="10140-131">All characters on the line after the `#` are ignored.</span></span>

### <span data-ttu-id="10140-132">Voor beeld 3: een teken reeks converteren naar een hash-tabel</span><span class="sxs-lookup"><span data-stu-id="10140-132">Example 3: Convert a string to a hash table</span></span>

<span data-ttu-id="10140-133">In dit voor beeld wordt een reguliere teken reeks met dubbele aanhalings tekens (geen hier een teken reeks) geconverteerd naar een hash-tabel en opgeslagen in de `$A` variabele.</span><span class="sxs-lookup"><span data-stu-id="10140-133">This example converts a regular double-quoted string (not a here-string) into a hash table and saves it in the `$A` variable.</span></span>

```powershell
$A = ConvertFrom-StringData -StringData "Top = Red `n Bottom = Blue"
$A
```

```Output
Name             Value
----             -----
Bottom           Blue
Top              Red
```

<span data-ttu-id="10140-134">Om te voldoen aan de voor waarde dat elke sleutel waarde-paar op een afzonderlijke regel moet staan, gebruikt de teken reeks het Power shell-teken voor nieuwe regels ( \` n) om de paren van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="10140-134">To satisfy the condition that each key-value pair must be on a separate line, the string uses the PowerShell newline character (\`n) to separate the pairs.</span></span>

### <span data-ttu-id="10140-135">Voor beeld 4: ConvertFrom-StringData gebruiken in de sectie gegevens van een script</span><span class="sxs-lookup"><span data-stu-id="10140-135">Example 4: Use ConvertFrom-StringData in the DATA section of a script</span></span>

<span data-ttu-id="10140-136">In dit voor beeld ziet u een `ConvertFrom-StringData` opdracht die wordt gebruikt in de sectie data van een script.</span><span class="sxs-lookup"><span data-stu-id="10140-136">This example shows a `ConvertFrom-StringData` command used in the DATA section of a script.</span></span>
<span data-ttu-id="10140-137">De instructies onder de sectie gegevens geven de tekst weer voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="10140-137">The statements below the DATA section display the text to the user.</span></span>

```powershell
$TextMsgs = DATA {
ConvertFrom-StringData @'
Text001 = The $Notebook variable contains the name of the user's system notebook.
Text002 = The $MyNotebook variable contains the name of the user's private notebook.
'@
}
$TextMsgs
```

```Output
Name             Value
----             -----
Text001          The $Notebook variable contains the name of the user's system notebook.
Text002          The $MyNotebook variable contains the name of the user's private notebook.
```

<span data-ttu-id="10140-138">Omdat de tekst namen van variabelen bevat, moet deze worden inge sloten in een teken reeks met enkele aanhalings tekens, zodat de variabelen letterlijk worden geïnterpreteerd en niet worden uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="10140-138">Because the text includes variable names, it must be enclosed in a single-quoted string so that the variables are interpreted literally and not expanded.</span></span> <span data-ttu-id="10140-139">Variabelen zijn niet toegestaan in de sectie **gegevens** .</span><span class="sxs-lookup"><span data-stu-id="10140-139">Variables are not permitted in the **DATA** section.</span></span>

### <span data-ttu-id="10140-140">Voor beeld 5: de pijplijn operator gebruiken om een teken reeks door te geven</span><span class="sxs-lookup"><span data-stu-id="10140-140">Example 5: Use the pipeline operator to pass a string</span></span>

<span data-ttu-id="10140-141">Dit voor beeld laat zien dat u een pijplijn operator () kunt gebruiken `|` voor het verzenden van een teken reeks naar `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="10140-141">This example shows that you can use a pipeline operator (`|`) to send a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="10140-142">De waarde van de `$Here` variabele wordt naar het `ConvertFrom-StringData` resultaat in de `$Hash` variabele geleid.</span><span class="sxs-lookup"><span data-stu-id="10140-142">The the value of the `$Here` variable is piped to `ConvertFrom-StringData` and the result in the `$Hash` variable.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
$Hash = $Here | ConvertFrom-StringData
$Hash
```

```Output
Name     Value
----     -----
Msg3     The specified variable does not exist.
Msg2     Credentials are required for this command.
Msg1     The string parameter is required.
```

### <span data-ttu-id="10140-143">Voor beeld 6: Escape tekens gebruiken om nieuwe lijnen en retour tekens toe te voegen</span><span class="sxs-lookup"><span data-stu-id="10140-143">Example 6: Use escape characters to add new lines and return characters</span></span>

<span data-ttu-id="10140-144">In dit voor beeld ziet u het gebruik van escape tekens voor het maken van nieuwe regels en het retour neren van tekens in de bron gegevens.</span><span class="sxs-lookup"><span data-stu-id="10140-144">This example shows the use of escape characters to create new lines and return characters in source data.</span></span> <span data-ttu-id="10140-145">De escape-teken reeks `\n` wordt gebruikt voor het maken van nieuwe regels in een tekst blok dat is gekoppeld aan een naam of item in de resulterende hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="10140-145">The escape sequence `\n` is used to create new lines within a block of text that is associated with a name or item in the resulting hash table.</span></span>

```powershell
ConvertFrom-StringData @"
Vincentio = Heaven doth with us as we with torches do,\nNot light them for themselves; for if our virtues\nDid not go forth of us, 'twere all alike\nAs if we had them not.
Angelo = Let there be some more test made of my metal,\nBefore so noble and so great a figure\nBe stamp'd upon it.
"@ | Format-List
```

```Output
Name  : Angelo
Value : Let there be some more test made of my metal,
        Before so noble and so great a figure
        Be stamp'd upon it.

Name  : Vincentio
Value : Heaven doth with us as we with torches do,
        Not light them for themselves; for if our virtues
        Did not go forth of us, 'twere all alike
        As if we had them not.
```

### <span data-ttu-id="10140-146">Voor beeld 7: back slash-escape teken gebruiken om een bestandspad correct weer te geven</span><span class="sxs-lookup"><span data-stu-id="10140-146">Example 7: Use backslash escape character to correctly render a file path</span></span>

<span data-ttu-id="10140-147">In dit voor beeld ziet u hoe u het escape-teken van back slash in de teken reeks gegevens kunt gebruiken om te zorgen dat een bestandspad correct kan worden weer gegeven in de resulterende `ConvertFrom-StringData` hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="10140-147">This example shows how to use of the backslash escape character in the string data to allow a file path to render correctly in the resulting `ConvertFrom-StringData` hash table.</span></span> <span data-ttu-id="10140-148">De dubbele back slash zorgt ervoor dat de letterlijke back slash-tekens correct worden weer gegeven in de hash-tabel uitvoer.</span><span class="sxs-lookup"><span data-stu-id="10140-148">The double backslash ensures that the literal backslash characters render correctly in the hash table output.</span></span>

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## <span data-ttu-id="10140-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="10140-149">PARAMETERS</span></span>

### <span data-ttu-id="10140-150">-StringData</span><span class="sxs-lookup"><span data-stu-id="10140-150">-StringData</span></span>

<span data-ttu-id="10140-151">Geeft de teken reeks die moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="10140-151">Specifies the string to be converted.</span></span> <span data-ttu-id="10140-152">U kunt deze para meter of pipe een teken reeks gebruiken voor `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="10140-152">You can use this parameter or pipe a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="10140-153">De parameter naam is optioneel.</span><span class="sxs-lookup"><span data-stu-id="10140-153">The parameter name is optional.</span></span>

<span data-ttu-id="10140-154">De waarde van deze para meter moet een teken reeks zijn die een of meer sleutel-waardeparen bevat.</span><span class="sxs-lookup"><span data-stu-id="10140-154">The value of this parameter must be a string that contains one or more key-value pairs.</span></span> <span data-ttu-id="10140-155">Elk sleutel-waardepaar moet zich op een afzonderlijke regel behoren of elk paar moet worden gescheiden door een nieuwe teken reeks ( \` n).</span><span class="sxs-lookup"><span data-stu-id="10140-155">Each key-value pair must be on a separate line, or each pair must be separated by newline characters (\`n).</span></span>

<span data-ttu-id="10140-156">U kunt opmerkingen toevoegen aan de teken reeks, maar de opmerkingen mogen zich niet op dezelfde regel bevindt als een sleutel/waarde-paar.</span><span class="sxs-lookup"><span data-stu-id="10140-156">You can include comments in the string, but the comments cannot be on the same line as a key-value pair.</span></span> <span data-ttu-id="10140-157">`ConvertFrom-StringData` opmerkingen over één regel worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="10140-157">`ConvertFrom-StringData` ignores single-line comments.</span></span> <span data-ttu-id="10140-158">Het `#` teken moet het eerste niet-spatie teken op de regel zijn.</span><span class="sxs-lookup"><span data-stu-id="10140-158">The `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="10140-159">Alle tekens op de regel na de `#` worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="10140-159">All characters on the line after the `#` are ignored.</span></span> <span data-ttu-id="10140-160">De opmerkingen worden niet opgenomen in de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="10140-160">The comments are not included in the hash table.</span></span>

<span data-ttu-id="10140-161">Een hier-teken reeks is een teken reeks die bestaat uit een of meer regels.</span><span class="sxs-lookup"><span data-stu-id="10140-161">A here-string is a string consisting of one or more lines.</span></span> <span data-ttu-id="10140-162">Aanhalings tekens in de teken reeks worden letterlijk geïnterpreteerd als onderdeel van de teken reeks gegevens.</span><span class="sxs-lookup"><span data-stu-id="10140-162">Quotation marks within the here-string are interpreted literally as part of the string data.</span></span> <span data-ttu-id="10140-163">Zie [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="10140-163">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="10140-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="10140-164">CommonParameters</span></span>

<span data-ttu-id="10140-165">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="10140-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="10140-166">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="10140-166">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="10140-167">INVOER</span><span class="sxs-lookup"><span data-stu-id="10140-167">INPUTS</span></span>

### <span data-ttu-id="10140-168">System. String</span><span class="sxs-lookup"><span data-stu-id="10140-168">System.String</span></span>

<span data-ttu-id="10140-169">U kunt een teken reeks met een sleutel/waarde-paar door sluizen naar `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="10140-169">You can pipe a string containing a key-value pair to `ConvertFrom-StringData`.</span></span>

## <span data-ttu-id="10140-170">UITVOER</span><span class="sxs-lookup"><span data-stu-id="10140-170">OUTPUTS</span></span>

### <span data-ttu-id="10140-171">System. Collections. hashtabel</span><span class="sxs-lookup"><span data-stu-id="10140-171">System.Collections.Hashtable</span></span>

<span data-ttu-id="10140-172">Met deze cmdlet wordt een hash-tabel geretourneerd die wordt gemaakt op basis van de sleutel-waardeparen.</span><span class="sxs-lookup"><span data-stu-id="10140-172">This cmdlet returns a hash table that it creates from the key-value pairs.</span></span>

## <span data-ttu-id="10140-173">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="10140-173">NOTES</span></span>

<span data-ttu-id="10140-174">Een hier-teken reeks is een teken reeks die bestaat uit een of meer regels waarin de aanhalings tekens letterlijk worden geïnterpreteerd.</span><span class="sxs-lookup"><span data-stu-id="10140-174">A here-string is a string consisting of one or more lines within which quotation marks are interpreted literally.</span></span>

<span data-ttu-id="10140-175">Deze cmdlet kan nuttig zijn in scripts waarmee gebruikers berichten in meerdere gesp roken talen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="10140-175">This cmdlet can be useful in scripts that display user messages in multiple spoken languages.</span></span> <span data-ttu-id="10140-176">U kunt de hash-tabellen voor het woordenlijst type gebruiken om teken reeksen uit code te isoleren, zoals in bron bestanden, en om de tekst teken reeksen op te maken voor gebruik in Vertaal hulpprogramma's.</span><span class="sxs-lookup"><span data-stu-id="10140-176">You can use the dictionary-style hash tables to isolate text strings from code, such as in resource files, and to format the text strings for use in translation tools.</span></span>

## <span data-ttu-id="10140-177">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="10140-177">RELATED LINKS</span></span>
