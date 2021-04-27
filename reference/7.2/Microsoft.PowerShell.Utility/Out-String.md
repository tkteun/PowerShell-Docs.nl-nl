---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: 21e21647a4fb25fee7bcb9dc58c4e5a2ba3f3fdb
ms.sourcegitcommit: 1e1535cb22d16de06f80beafe77a37a7c77de6d3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025669"
---
# <span data-ttu-id="d8fba-102">Out-String</span><span class="sxs-lookup"><span data-stu-id="d8fba-102">Out-String</span></span>

## <span data-ttu-id="d8fba-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="d8fba-103">Synopsis</span></span>
<span data-ttu-id="d8fba-104">Invoerobjecten worden uitgevoerd als een tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="d8fba-104">Outputs input objects as a string.</span></span>

## <span data-ttu-id="d8fba-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8fba-105">Syntax</span></span>

### <span data-ttu-id="d8fba-106">NoNewLineFormatting (standaard)</span><span class="sxs-lookup"><span data-stu-id="d8fba-106">NoNewLineFormatting (Default)</span></span>

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### <span data-ttu-id="d8fba-107">StreamFormatting</span><span class="sxs-lookup"><span data-stu-id="d8fba-107">StreamFormatting</span></span>

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="d8fba-108">Description</span><span class="sxs-lookup"><span data-stu-id="d8fba-108">Description</span></span>

<span data-ttu-id="d8fba-109">De `Out-String` cmdlet converteert invoerobjecten naar tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d8fba-109">The `Out-String` cmdlet converts input objects into strings.</span></span> <span data-ttu-id="d8fba-110">Standaard worden de tekenreeksen verzameld en als één tekenreeks retourneert, maar u kunt de Stream-parameter gebruiken om één regel tegelijk te retourneren of een matrix met tekenreeksen `Out-String` te  `Out-String` maken.</span><span class="sxs-lookup"><span data-stu-id="d8fba-110">By default, `Out-String` accumulates the strings and returns them as a single string, but you can use the **Stream** parameter to direct `Out-String` to return one line at a time or create an array of strings.</span></span> <span data-ttu-id="d8fba-111">Met deze cmdlet kunt u tekenreeksuitvoer zoeken en bewerken zoals in traditionele shells wanneer het bewerken van objecten minder handig is.</span><span class="sxs-lookup"><span data-stu-id="d8fba-111">This cmdlet lets you search and manipulate string output as you would in traditional shells when object manipulation is less convenient.</span></span>

## <span data-ttu-id="d8fba-112">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="d8fba-112">Examples</span></span>

### <span data-ttu-id="d8fba-113">Voorbeeld 1: De huidige cultuur op halen en de gegevens converteren naar tekenreeksen</span><span class="sxs-lookup"><span data-stu-id="d8fba-113">Example 1: Get the current culture and convert the data to strings</span></span>

<span data-ttu-id="d8fba-114">In dit voorbeeld worden de regionale instellingen voor de huidige gebruiker en worden de objectgegevens ge converteert naar tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d8fba-114">This example gets the regional settings for the current user and converts the object data to strings.</span></span>

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

<span data-ttu-id="d8fba-115">De `$C` variabele slaat eenSelected.Sys **op. Globalization.CultureInfo-object.**</span><span class="sxs-lookup"><span data-stu-id="d8fba-115">The `$C` variable stores a **Selected.System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="d8fba-116">Het -object is het resultaat van `Get-Culture` het verzenden van uitvoer in de pijplijn naar `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="d8fba-116">The object is the result of `Get-Culture` sending output down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="d8fba-117">De **eigenschap** parameter maakt gebruik van een sterretje ( ) jokerteken om op te geven `*` alle eigenschappen zijn opgenomen in het object.</span><span class="sxs-lookup"><span data-stu-id="d8fba-117">The **Property** parameter uses an asterisk (`*`) wildcard to specify all properties are contained in the object.</span></span>

<span data-ttu-id="d8fba-118">`Out-String` gebruikt de **parameter InputObject** om het object **CultureInfo op** te geven dat is opgeslagen in de `$C` variabele .</span><span class="sxs-lookup"><span data-stu-id="d8fba-118">`Out-String` uses the **InputObject** parameter to specify the **CultureInfo** object stored in the `$C` variable.</span></span> <span data-ttu-id="d8fba-119">De objecten in `$C` worden geconverteerd naar een tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="d8fba-119">The objects in `$C` are converted to a string.</span></span>

> [!NOTE]
> <span data-ttu-id="d8fba-120">Als u de `Out-String` matrix wilt weergeven, moet u de uitvoer opslaan in een variabele en een matrixindex gebruiken om de elementen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="d8fba-120">To view the `Out-String` array, store the output to a variable and use an array index to view the elements.</span></span> <span data-ttu-id="d8fba-121">Zie voor meer informatie over de matrixindex [about_Arrays.](../microsoft.powershell.core/about/about_arrays.md)</span><span class="sxs-lookup"><span data-stu-id="d8fba-121">For more information about the array index, see [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).</span></span>
>
> `$str = Out-String -InputObject $C -Width 100`

### <span data-ttu-id="d8fba-122">Voorbeeld 2: Werken met objecten</span><span class="sxs-lookup"><span data-stu-id="d8fba-122">Example 2: Working with objects</span></span>

<span data-ttu-id="d8fba-123">In dit voorbeeld wordt het verschil gedemonstreerd tussen het werken met objecten en het werken met tekenreeksen.</span><span class="sxs-lookup"><span data-stu-id="d8fba-123">This example demonstrates the difference between working with objects and working with strings.</span></span> <span data-ttu-id="d8fba-124">Met de opdracht wordt een alias weergegeven met de tekst **gcm**, de alias voor `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="d8fba-124">The command displays an alias that includes the text **gcm**, the alias for `Get-Command`.</span></span>

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

<span data-ttu-id="d8fba-125">`Get-Alias` haalt de **System.Management.Automation.AliasInfo-objecten** op, één voor elke alias, en verzendt de objecten in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="d8fba-125">`Get-Alias` gets the **System.Management.Automation.AliasInfo** objects, one for each alias, and sends the objects down the pipeline.</span></span> <span data-ttu-id="d8fba-126">`Out-String` gebruikt de **Stream-parameter** om elk object te converteren naar een tekenreeks in plaats van alle objecten samen tevoegen in één tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="d8fba-126">`Out-String` uses the **Stream** parameter to convert each object to a string rather than concatenating all the objects into a single string.</span></span>
<span data-ttu-id="d8fba-127">De **System.String-objecten** worden naar de pijplijn verzonden en gebruiken de parameter Pattern om overeenkomsten voor de tekst `Select-String`  **gcm te vinden.**</span><span class="sxs-lookup"><span data-stu-id="d8fba-127">The **System.String** objects are sent down the pipeline and `Select-String` uses the **Pattern** parameter to find matches for the text **gcm**.</span></span>

> [!NOTE]
> <span data-ttu-id="d8fba-128">Als u de **Stream-parameter weglaten,** de opdracht geeft alle aliassen omdat vindt de tekst gcm in de enkele tekenreeks `Select-String` die  `Out-String` retourneert.</span><span class="sxs-lookup"><span data-stu-id="d8fba-128">If you omit the **Stream** parameter, the command displays all the aliases because `Select-String` finds the text **gcm** in the single string that `Out-String` returns.</span></span>

### <span data-ttu-id="d8fba-129">Voorbeeld 3: gebruik de parameter Width om afroepen te voorkomen.</span><span class="sxs-lookup"><span data-stu-id="d8fba-129">Example 3: Use the Width parameter to prevent truncation.</span></span>

<span data-ttu-id="d8fba-130">Hoewel de meeste uitvoer van wordt verpakt naar de volgende regel, zijn er scenario's waarin de uitvoer wordt afgekapt door het opmaaksysteem voordat deze `Out-String` wordt doorgegeven aan `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="d8fba-130">While most output from `Out-String` is wrapped to the next line, there are scenarios where the output is truncated by the formatting system before being passed to `Out-String`.</span></span> <span data-ttu-id="d8fba-131">U kunt afroepen voorkomen met behulp van de parameter **Width.**</span><span class="sxs-lookup"><span data-stu-id="d8fba-131">You can avoid truncation using the **Width** parameter.</span></span>

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## <span data-ttu-id="d8fba-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8fba-132">PARAMETERS</span></span>

### <span data-ttu-id="d8fba-133">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d8fba-133">-InputObject</span></span>

<span data-ttu-id="d8fba-134">Hiermee geeft u de objecten moet worden geschreven naar een tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="d8fba-134">Specifies the objects to be written to a string.</span></span> <span data-ttu-id="d8fba-135">Voer een variabele in die de objecten bevat of typ een opdracht of expressie die de objecten op haalt.</span><span class="sxs-lookup"><span data-stu-id="d8fba-135">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d8fba-136">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="d8fba-136">-NoNewline</span></span>

<span data-ttu-id="d8fba-137">Hiermee verwijdert u alle nieuwelijnen uit de uitvoer die is gegenereerd door de PowerShell-indeling.</span><span class="sxs-lookup"><span data-stu-id="d8fba-137">Removes all newlines from output generated by the PowerShell formatter.</span></span> <span data-ttu-id="d8fba-138">Nieuwelijnen die deel uitmaken van de tekenreeksobjecten blijven behouden.</span><span class="sxs-lookup"><span data-stu-id="d8fba-138">Newlines that are part of the string objects are preserved.</span></span>

<span data-ttu-id="d8fba-139">Deze parameter is geïntroduceerd in PowerShell 6.0.</span><span class="sxs-lookup"><span data-stu-id="d8fba-139">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8fba-140">-Stream</span><span class="sxs-lookup"><span data-stu-id="d8fba-140">-Stream</span></span>

<span data-ttu-id="d8fba-141">Standaard wordt één tekenreeks uitgevoerd die is opgemaakt zoals u deze zou zien in de console, inclusief lege headers of `Out-String` na een nieuwe lijn.</span><span class="sxs-lookup"><span data-stu-id="d8fba-141">By default, `Out-String` outputs a single string formatted as you would see it in the console including any blank headers or trailing newlines.</span></span> <span data-ttu-id="d8fba-142">Met **de parameter Stream** kan elke regel één voor één worden `Out-String` uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d8fba-142">The **Stream** parameter enables `Out-String` to output each line one by one.</span></span> <span data-ttu-id="d8fba-143">De enige uitzondering hierop zijn meerdere regelreeksen.</span><span class="sxs-lookup"><span data-stu-id="d8fba-143">The only exception to this are multiline strings.</span></span> <span data-ttu-id="d8fba-144">In dat geval wordt `Out-String` de tekenreeks nog steeds uitgevoerd als één tekenreeks met meerdere reeksen.</span><span class="sxs-lookup"><span data-stu-id="d8fba-144">In that case, `Out-String` will still output the string as a single, multiline string.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8fba-145">-Breedte</span><span class="sxs-lookup"><span data-stu-id="d8fba-145">-Width</span></span>

<span data-ttu-id="d8fba-146">Hiermee geeft u het aantal tekens in elke regel van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="d8fba-146">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="d8fba-147">Eventuele extra tekens worden verpakt op de volgende regel of afgekapt, afhankelijk van de gebruikte cmdlet voor formatter.</span><span class="sxs-lookup"><span data-stu-id="d8fba-147">Any additional characters are wrapped to the next line or truncated depending on the formatter cmdlet used.</span></span> <span data-ttu-id="d8fba-148">De **parameter Width** is alleen van toepassing op objecten die worden geformatteerd.</span><span class="sxs-lookup"><span data-stu-id="d8fba-148">The **Width** parameter applies only to objects that are being formatted.</span></span> <span data-ttu-id="d8fba-149">Als u deze parameter weglaten, wordt de breedte bepaald door de kenmerken van het hostprogramma.</span><span class="sxs-lookup"><span data-stu-id="d8fba-149">If you omit this parameter, the width is determined by the characteristics of the host program.</span></span> <span data-ttu-id="d8fba-150">In terminalvensters (console) wordt de huidige breedte van het venster gebruikt als de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="d8fba-150">In terminal (console) windows, the current window width is used as the default value.</span></span> <span data-ttu-id="d8fba-151">Windows in de PowerShell-console hebben standaard een breedte van 80 tekens bij de installatie.</span><span class="sxs-lookup"><span data-stu-id="d8fba-151">PowerShell console windows default to a width of 80 characters on installation.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8fba-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8fba-152">CommonParameters</span></span>

<span data-ttu-id="d8fba-153">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d8fba-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8fba-154">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d8fba-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8fba-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="d8fba-155">INPUTS</span></span>

### <span data-ttu-id="d8fba-156">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="d8fba-156">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="d8fba-157">U kunt objecten in de pijplijn verzenden naar `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="d8fba-157">You can send objects down the pipeline to `Out-String`.</span></span>

## <span data-ttu-id="d8fba-158">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d8fba-158">OUTPUTS</span></span>

### <span data-ttu-id="d8fba-159">System.String</span><span class="sxs-lookup"><span data-stu-id="d8fba-159">System.String</span></span>

<span data-ttu-id="d8fba-160">`Out-String` retourneert de tekenreeks die wordt gemaakt op basis van het invoerobject.</span><span class="sxs-lookup"><span data-stu-id="d8fba-160">`Out-String` returns the string that it creates from the input object.</span></span>

## <span data-ttu-id="d8fba-161">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d8fba-161">NOTES</span></span>

<span data-ttu-id="d8fba-162">De cmdlets die het werkwoord `Out` bevatten, maken geen objecten op.</span><span class="sxs-lookup"><span data-stu-id="d8fba-162">The cmdlets that contain the `Out` verb don't format objects.</span></span> <span data-ttu-id="d8fba-163">De `Out` cmdlets verzenden objecten naar de formatter voor de opgegeven weergavebestemming.</span><span class="sxs-lookup"><span data-stu-id="d8fba-163">The `Out` cmdlets send objects to the formatter for the specified display destination.</span></span>

## <span data-ttu-id="d8fba-164">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d8fba-164">RELATED LINKS</span></span>

[<span data-ttu-id="d8fba-165">about_Formatting</span><span class="sxs-lookup"><span data-stu-id="d8fba-165">about_Formatting</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="d8fba-166">Out-Default</span><span class="sxs-lookup"><span data-stu-id="d8fba-166">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="d8fba-167">Out-File</span><span class="sxs-lookup"><span data-stu-id="d8fba-167">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="d8fba-168">Out-Host</span><span class="sxs-lookup"><span data-stu-id="d8fba-168">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="d8fba-169">Out-Null</span><span class="sxs-lookup"><span data-stu-id="d8fba-169">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="d8fba-170">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="d8fba-170">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="d8fba-171">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="d8fba-171">Out-Printer</span></span>](Out-Printer.md)
