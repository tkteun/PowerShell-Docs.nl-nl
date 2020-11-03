---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: a64b11206a0755cedabad2894ecc330fac95a8d5
ms.sourcegitcommit: c8d1ffeab215e74e87ea1b0af8cd606c1a6a80ab
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/29/2020
ms.locfileid: "93251963"
---
# <span data-ttu-id="c9e60-103">Out-String</span><span class="sxs-lookup"><span data-stu-id="c9e60-103">Out-String</span></span>

## <span data-ttu-id="c9e60-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c9e60-104">SYNOPSIS</span></span>
<span data-ttu-id="c9e60-105">Voert invoer objecten uit als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="c9e60-105">Outputs input objects as a strings.</span></span>

## <span data-ttu-id="c9e60-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c9e60-106">SYNTAX</span></span>

### <span data-ttu-id="c9e60-107">NoNewLineFormatting (standaard)</span><span class="sxs-lookup"><span data-stu-id="c9e60-107">NoNewLineFormatting (Default)</span></span>

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### <span data-ttu-id="c9e60-108">StreamFormatting</span><span class="sxs-lookup"><span data-stu-id="c9e60-108">StreamFormatting</span></span>

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="c9e60-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c9e60-109">DESCRIPTION</span></span>

<span data-ttu-id="c9e60-110">Met de `Out-String` cmdlet worden invoer objecten geconverteerd naar teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="c9e60-110">The `Out-String` cmdlet converts input objects into strings.</span></span> <span data-ttu-id="c9e60-111">`Out-String`De teken reeksen worden standaard gecumuleerd en geretourneerd als een enkele teken reeks, maar u kunt de **Stream** -para meter gebruiken om direct `Out-String` één regel tegelijk te retour neren of om een matrix van teken reeksen te maken.</span><span class="sxs-lookup"><span data-stu-id="c9e60-111">By default, `Out-String` accumulates the strings and returns them as a single string, but you can use the **Stream** parameter to direct `Out-String` to return one line at a time or create and array of strings.</span></span> <span data-ttu-id="c9e60-112">Met deze cmdlet kunt u de teken reeks uitvoer zoeken en manipuleren, net zoals bij traditionele schalen, wanneer het bewerken van objecten minder handig is.</span><span class="sxs-lookup"><span data-stu-id="c9e60-112">This cmdlet lets you search and manipulate string output as you would in traditional shells when object manipulation is less convenient.</span></span>

## <span data-ttu-id="c9e60-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c9e60-113">EXAMPLES</span></span>

### <span data-ttu-id="c9e60-114">Voor beeld 1: de huidige cultuur ophalen en de gegevens converteren naar teken reeksen</span><span class="sxs-lookup"><span data-stu-id="c9e60-114">Example 1: Get the current culture and convert the data to strings</span></span>

<span data-ttu-id="c9e60-115">In dit voor beeld worden de regionale instellingen voor de huidige gebruiker opgehaald en worden de object gegevens geconverteerd naar teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="c9e60-115">This example gets the regional settings for the current user and converts the object data to strings.</span></span>

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

<span data-ttu-id="c9e60-116">De `$C` variabele bevat een **Selected.System. Globalisatie. Culture info** -object.</span><span class="sxs-lookup"><span data-stu-id="c9e60-116">The `$C` variable stores a **Selected.System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="c9e60-117">Het object is het resultaat van het `Get-Culture` verzenden van de uitvoer van de pijp lijn naar `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="c9e60-117">The object is the result of `Get-Culture` sending output down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="c9e60-118">De **eigenschaps** parameter maakt gebruik van een asterisk ( `*` )-Joker teken om alle eigenschappen op te geven die in het object zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="c9e60-118">The **Property** parameter uses an asterisk (`*`) wildcard to specify all properties are contained in the object.</span></span>

<span data-ttu-id="c9e60-119">`Out-String` maakt gebruik van de para meter **input object** om het **Culture info** -object op te geven dat is opgeslagen in de `$C` variabele.</span><span class="sxs-lookup"><span data-stu-id="c9e60-119">`Out-String` uses the **InputObject** parameter to specify the **CultureInfo** object stored in the `$C` variable.</span></span> <span data-ttu-id="c9e60-120">De objecten in `$C` worden geconverteerd naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c9e60-120">The objects in `$C` are converted to a string.</span></span>

> [!NOTE]
> <span data-ttu-id="c9e60-121">Als u de matrix wilt weer geven `Out-String` , slaat u de uitvoer op in een variabele en gebruikt u een matrix index om de elementen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="c9e60-121">To view the `Out-String` array, store the output to a variable and use an array index to view the elements.</span></span> <span data-ttu-id="c9e60-122">Zie [about_Arrays](../microsoft.powershell.core/about/about_arrays.md)voor meer informatie over de matrix index.</span><span class="sxs-lookup"><span data-stu-id="c9e60-122">For more information about the array index, see [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).</span></span>
>
> `$str = Out-String -InputObject $C -Width 100`

### <span data-ttu-id="c9e60-123">Voor beeld 2: werken met objecten</span><span class="sxs-lookup"><span data-stu-id="c9e60-123">Example 2: Working with objects</span></span>

<span data-ttu-id="c9e60-124">In dit voor beeld wordt het verschil gedemonstreerd tussen het werken met objecten en het werken met teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="c9e60-124">This example demonstrates the difference between working with objects and working with strings.</span></span> <span data-ttu-id="c9e60-125">Met de opdracht wordt een alias weer gegeven met de tekst **GCM** , de alias voor `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="c9e60-125">The command displays an alias that includes the text **gcm** , the alias for `Get-Command`.</span></span>

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

<span data-ttu-id="c9e60-126">`Get-Alias` Hiermee worden de objecten **System. Management. Automation. AliasInfo** , een voor elke alias, opgehaald en worden de objecten van de pijp lijn omlaag verzonden.</span><span class="sxs-lookup"><span data-stu-id="c9e60-126">`Get-Alias` gets the **System.Management.Automation.AliasInfo** objects, one for each alias, and sends the objects down the pipeline.</span></span> <span data-ttu-id="c9e60-127">`Out-String` gebruikt de **Stream** -para meter om elk object te converteren naar een teken reeks, in plaats van alle objecten te koppelen aan één teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c9e60-127">`Out-String` uses the **Stream** parameter to convert each object to a string rather concatenating all the objects into a single string.</span></span> <span data-ttu-id="c9e60-128">De **System. String** -objecten worden via de pijp lijn verzonden en er `Select-String` wordt gebruikgemaakt van de **patroon** parameter om overeenkomsten te vinden voor de tekst **GCM**.</span><span class="sxs-lookup"><span data-stu-id="c9e60-128">The **System.String** objects are sent down the pipeline and `Select-String` uses the **Pattern** parameter to find matches for the text **gcm**.</span></span>

> [!NOTE]
> <span data-ttu-id="c9e60-129">Als u de **Stream** -para meter weglaat, wordt met de opdracht alle aliassen weer gegeven, omdat `Select-String` de tekst **GCM** wordt gevonden in de teken reeks die `Out-String` als resultaat wordt gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9e60-129">If you omit the **Stream** parameter, the command displays all the aliases because `Select-String` finds the text **gcm** in the single string that `Out-String` returns.</span></span>

### <span data-ttu-id="c9e60-130">Voor beeld 3: gebruik de para meter breedte om afkap ping te voor komen.</span><span class="sxs-lookup"><span data-stu-id="c9e60-130">Example 3: Use the Width parameter to prevent truncation.</span></span>

<span data-ttu-id="c9e60-131">Hoewel de meeste uitvoer van `Out-String` wordt ingepakt naar de volgende regel, zijn er scenario's waarin de uitvoer wordt afgekapt door het format teren systeem voordat deze wordt door gegeven aan `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="c9e60-131">While most output from `Out-String` is wrapped to the next line, there are scenarios where the output is truncated by the formatting system before being passed to `Out-String`.</span></span> <span data-ttu-id="c9e60-132">U kunt afkap ping vermijden met de para meter **width** .</span><span class="sxs-lookup"><span data-stu-id="c9e60-132">You can avoid truncation using the **Width** parameter.</span></span>

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

## <span data-ttu-id="c9e60-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c9e60-133">PARAMETERS</span></span>

### <span data-ttu-id="c9e60-134">-Input object</span><span class="sxs-lookup"><span data-stu-id="c9e60-134">-InputObject</span></span>

<span data-ttu-id="c9e60-135">Geeft aan welke objecten moeten worden geschreven naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c9e60-135">Specifies the objects to be written to a string.</span></span> <span data-ttu-id="c9e60-136">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c9e60-136">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="c9e60-137">-Nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="c9e60-137">-NoNewline</span></span>

<span data-ttu-id="c9e60-138">Hiermee verwijdert u alle nieuwe voors van de uitvoer die wordt gegenereerd door de Power shell-indelings functie.</span><span class="sxs-lookup"><span data-stu-id="c9e60-138">Removes all newlines from output generated by the PowerShell formatter.</span></span> <span data-ttu-id="c9e60-139">Nieuwe regels die deel uitmaken van de teken reeks objecten blijven behouden.</span><span class="sxs-lookup"><span data-stu-id="c9e60-139">Newlines that are part of the string objects are preserved.</span></span>

<span data-ttu-id="c9e60-140">Deze para meter is geïntroduceerd in Power shell 6,0.</span><span class="sxs-lookup"><span data-stu-id="c9e60-140">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="c9e60-141">-Stream</span><span class="sxs-lookup"><span data-stu-id="c9e60-141">-Stream</span></span>

<span data-ttu-id="c9e60-142">Geeft aan dat de cmdlet een afzonderlijke teken reeks voor elke regel van een invoer object verzendt.</span><span class="sxs-lookup"><span data-stu-id="c9e60-142">Indicates that the cmdlet sends a separate string for each line of an input object.</span></span> <span data-ttu-id="c9e60-143">Standaard worden de teken reeksen voor elk object verzameld en als één teken reeks verzonden.</span><span class="sxs-lookup"><span data-stu-id="c9e60-143">By default, the strings for each object are accumulated and sent as a single string.</span></span>

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

### <span data-ttu-id="c9e60-144">-Breedte</span><span class="sxs-lookup"><span data-stu-id="c9e60-144">-Width</span></span>

<span data-ttu-id="c9e60-145">Hiermee geeft u het aantal tekens in elke regel van uitvoer op.</span><span class="sxs-lookup"><span data-stu-id="c9e60-145">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="c9e60-146">Eventuele extra tekens worden ingepakt naar de volgende regel of worden afgekapt, afhankelijk van de gebruikte formatter-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c9e60-146">Any additional characters are wrapped to the next line or truncated depending on the formatter cmdlet used.</span></span> <span data-ttu-id="c9e60-147">De para meter **width** is alleen van toepassing op objecten die worden opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="c9e60-147">The **Width** parameter applies only to objects that are being formatted.</span></span> <span data-ttu-id="c9e60-148">Als u deze para meter weglaat, wordt de breedte bepaald door de kenmerken van het hostprogramma.</span><span class="sxs-lookup"><span data-stu-id="c9e60-148">If you omit this parameter, the width is determined by the characteristics of the host program.</span></span> <span data-ttu-id="c9e60-149">In Terminal (console) Windows wordt de breedte van het huidige venster als de standaard waarde gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c9e60-149">In terminal (console) windows, the current window width is used as the default value.</span></span> <span data-ttu-id="c9e60-150">Power shell-console Windows standaard ingesteld op een breedte van 80 tekens tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="c9e60-150">PowerShell console windows default to a width of 80 characters on installation.</span></span>

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

### <span data-ttu-id="c9e60-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c9e60-151">CommonParameters</span></span>

<span data-ttu-id="c9e60-152">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c9e60-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c9e60-153">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c9e60-153">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c9e60-154">INVOER</span><span class="sxs-lookup"><span data-stu-id="c9e60-154">INPUTS</span></span>

### <span data-ttu-id="c9e60-155">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="c9e60-155">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c9e60-156">U kunt objecten naar beneden verplaatsen in de pijp lijn `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="c9e60-156">You can send objects down the pipeline to `Out-String`.</span></span>

## <span data-ttu-id="c9e60-157">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c9e60-157">OUTPUTS</span></span>

### <span data-ttu-id="c9e60-158">System. String</span><span class="sxs-lookup"><span data-stu-id="c9e60-158">System.String</span></span>

<span data-ttu-id="c9e60-159">`Out-String` retourneert de teken reeks die wordt gemaakt op basis van het invoer object.</span><span class="sxs-lookup"><span data-stu-id="c9e60-159">`Out-String` returns the string that it creates from the input object.</span></span>

## <span data-ttu-id="c9e60-160">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c9e60-160">NOTES</span></span>

<span data-ttu-id="c9e60-161">De cmdlets die de term bevatten, hebben `Out` geen objecten.</span><span class="sxs-lookup"><span data-stu-id="c9e60-161">The cmdlets that contain the `Out` verb don't format objects.</span></span> <span data-ttu-id="c9e60-162">`Out`Met de cmdlets worden objecten verzonden naar de formatter voor het opgegeven weergave doel.</span><span class="sxs-lookup"><span data-stu-id="c9e60-162">The `Out` cmdlets send objects to the formatter for the specified display destination.</span></span>

## <span data-ttu-id="c9e60-163">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c9e60-163">RELATED LINKS</span></span>

[<span data-ttu-id="c9e60-164">about_Formatting</span><span class="sxs-lookup"><span data-stu-id="c9e60-164">about_Formatting</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="c9e60-165">Out-standaard</span><span class="sxs-lookup"><span data-stu-id="c9e60-165">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="c9e60-166">Out-file</span><span class="sxs-lookup"><span data-stu-id="c9e60-166">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="c9e60-167">Out-host</span><span class="sxs-lookup"><span data-stu-id="c9e60-167">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="c9e60-168">Out-Null</span><span class="sxs-lookup"><span data-stu-id="c9e60-168">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="c9e60-169">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="c9e60-169">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="c9e60-170">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="c9e60-170">Out-Printer</span></span>](Out-Printer.md)
