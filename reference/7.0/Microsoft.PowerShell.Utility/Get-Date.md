---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 4ae3734d0ce41ef2faa7bcf3e07f136b9e9916a2
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514956"
---
# <span data-ttu-id="ddc83-103">Get-Date</span><span class="sxs-lookup"><span data-stu-id="ddc83-103">Get-Date</span></span>

## <span data-ttu-id="ddc83-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="ddc83-104">SYNOPSIS</span></span>
<span data-ttu-id="ddc83-105">Hiermee worden de huidige datum en tijd opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ddc83-105">Gets the current date and time.</span></span>

## <span data-ttu-id="ddc83-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ddc83-106">SYNTAX</span></span>

### <span data-ttu-id="ddc83-107">net (standaard)</span><span class="sxs-lookup"><span data-stu-id="ddc83-107">net (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [<CommonParameters>]
```

### <span data-ttu-id="ddc83-108">UFormat</span><span class="sxs-lookup"><span data-stu-id="ddc83-108">UFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-UFormat <String>] [<CommonParameters>]
```

## <span data-ttu-id="ddc83-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ddc83-109">DESCRIPTION</span></span>

<span data-ttu-id="ddc83-110">De `Get-Date` cmdlet haalt een **DateTime** -object op dat staat voor de huidige datum of een datum die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="ddc83-110">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="ddc83-111">`Get-Date` de datum en tijd in verschillende .NET-en UNIX-indelingen kunnen worden ingedeeld.</span><span class="sxs-lookup"><span data-stu-id="ddc83-111">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="ddc83-112">U kunt gebruiken `Get-Date` voor het genereren van een teken reeks voor datum of tijd en vervolgens de teken reeks verzenden naar andere cmdlets of Program ma's.</span><span class="sxs-lookup"><span data-stu-id="ddc83-112">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="ddc83-113">`Get-Date` gebruikt de instellingen van de computer cultuur om te bepalen hoe de uitvoer wordt geformatteerd.</span><span class="sxs-lookup"><span data-stu-id="ddc83-113">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="ddc83-114">Gebruik om de instellingen van uw computer weer te geven `(Get-Culture).DateTimeFormat` .</span><span class="sxs-lookup"><span data-stu-id="ddc83-114">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="ddc83-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ddc83-115">EXAMPLES</span></span>

### <span data-ttu-id="ddc83-116">Voor beeld 1: de huidige datum en tijd ophalen</span><span class="sxs-lookup"><span data-stu-id="ddc83-116">Example 1: Get the current date and time</span></span>

<span data-ttu-id="ddc83-117">In dit voor beeld `Get-Date` worden de huidige systeem datum en-tijd weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-117">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="ddc83-118">De uitvoer bevindt zich in de notatie voor lange en lange tijd.</span><span class="sxs-lookup"><span data-stu-id="ddc83-118">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="ddc83-119">Voor beeld 2: elementen van de huidige datum en tijd ophalen</span><span class="sxs-lookup"><span data-stu-id="ddc83-119">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="ddc83-120">In dit voor beeld ziet u hoe u kunt gebruiken `Get-Date` om het datum-of tijd-element op te halen.</span><span class="sxs-lookup"><span data-stu-id="ddc83-120">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="ddc83-121">De para meter gebruikt de argumenten **datum**, **tijd** of **datum/** tijd.</span><span class="sxs-lookup"><span data-stu-id="ddc83-121">The parameter uses the arguments **Date**, **Time**, or **DateTime**.</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="ddc83-122">`Get-Date` gebruikt de para meter **DisplayHint** met het **datum** argument om alleen de datum op te halen.</span><span class="sxs-lookup"><span data-stu-id="ddc83-122">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="ddc83-123">Voor beeld 3: de datum en tijd ophalen met een specificatie van .NET-indeling</span><span class="sxs-lookup"><span data-stu-id="ddc83-123">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="ddc83-124">In dit voor beeld wordt een .NET-indelings specificatie gebruikt om de indeling van de uitvoer aan te passen.</span><span class="sxs-lookup"><span data-stu-id="ddc83-124">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="ddc83-125">De uitvoer is een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="ddc83-125">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="ddc83-126">`Get-Date` gebruikt de **indelings** parameter om verschillende indelings aanduidingen op te geven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-126">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="ddc83-127">De .NET-indelings specificaties die in dit voor beeld worden gebruikt, zijn als volgt gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="ddc83-127">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="ddc83-128">Aanduiding</span><span class="sxs-lookup"><span data-stu-id="ddc83-128">Specifier</span></span> | <span data-ttu-id="ddc83-129">Definitie</span><span class="sxs-lookup"><span data-stu-id="ddc83-129">Definition</span></span> |
| --- | --- |
| `dddd` | <span data-ttu-id="ddc83-130">Dag van de week-volledige naam</span><span class="sxs-lookup"><span data-stu-id="ddc83-130">Day of the week - full name</span></span> |
| `MM` | <span data-ttu-id="ddc83-131">Maandnummer</span><span class="sxs-lookup"><span data-stu-id="ddc83-131">Month number</span></span> |
| `dd` | <span data-ttu-id="ddc83-132">Dag van de maand: 2 cijfers</span><span class="sxs-lookup"><span data-stu-id="ddc83-132">Day of the month - 2 digits</span></span> |
| `yyyy` | <span data-ttu-id="ddc83-133">Jaar met viercijferige notatie</span><span class="sxs-lookup"><span data-stu-id="ddc83-133">Year in 4-digit format</span></span> |
| `HH:mm` | <span data-ttu-id="ddc83-134">Tijd in 24-uurs notatie-geen seconden</span><span class="sxs-lookup"><span data-stu-id="ddc83-134">Time in 24-hour format -no seconds</span></span> |
| `K` | <span data-ttu-id="ddc83-135">Tijd zone-offset van Universal Time Coordinate (UTC)</span><span class="sxs-lookup"><span data-stu-id="ddc83-135">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="ddc83-136">Zie [aangepaste datum-en tijd notatie reeksen](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)voor meer informatie over .net-indelings specificaties.</span><span class="sxs-lookup"><span data-stu-id="ddc83-136">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="ddc83-137">Voor beeld 4: de datum en tijd ophalen met een UFormat-aanduiding</span><span class="sxs-lookup"><span data-stu-id="ddc83-137">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="ddc83-138">In dit voor beeld worden verschillende **UFormat** -indelings specificaties gebruikt voor het aanpassen van de indeling van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="ddc83-138">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="ddc83-139">De uitvoer is een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="ddc83-139">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="ddc83-140">`Get-Date` maakt gebruik van de para meter **UFormat** om verschillende indelings specificaties op te geven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-140">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="ddc83-141">De **UFormat** -indelings specificaties die in dit voor beeld worden gebruikt, zijn als volgt gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="ddc83-141">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="ddc83-142">Aanduiding</span><span class="sxs-lookup"><span data-stu-id="ddc83-142">Specifier</span></span> | <span data-ttu-id="ddc83-143">Definitie</span><span class="sxs-lookup"><span data-stu-id="ddc83-143">Definition</span></span> |
| --- | --- |
| `%A` | <span data-ttu-id="ddc83-144">Dag van de week-volledige naam</span><span class="sxs-lookup"><span data-stu-id="ddc83-144">Day of the week - full name</span></span> |
| `%m` | <span data-ttu-id="ddc83-145">Maandnummer</span><span class="sxs-lookup"><span data-stu-id="ddc83-145">Month number</span></span> |
| `%d` | <span data-ttu-id="ddc83-146">Dag van de maand: 2 cijfers</span><span class="sxs-lookup"><span data-stu-id="ddc83-146">Day of the month - 2 digits</span></span> |
| `%Y` | <span data-ttu-id="ddc83-147">Jaar met viercijferige notatie</span><span class="sxs-lookup"><span data-stu-id="ddc83-147">Year in 4-digit format</span></span> |
| `%R` | <span data-ttu-id="ddc83-148">Tijd in 24-uurs notatie-geen seconden</span><span class="sxs-lookup"><span data-stu-id="ddc83-148">Time in 24-hour format -no seconds</span></span> |
| `%Z` | <span data-ttu-id="ddc83-149">Tijd zone-offset van Universal Time Coordinate (UTC)</span><span class="sxs-lookup"><span data-stu-id="ddc83-149">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="ddc83-150">Zie de sectie [opmerkingen](#notes) voor een lijst met geldige indelings specificaties voor **UFormat** .</span><span class="sxs-lookup"><span data-stu-id="ddc83-150">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="ddc83-151">Voor beeld 5: de dag van een datum van het jaar ophalen</span><span class="sxs-lookup"><span data-stu-id="ddc83-151">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="ddc83-152">In dit voor beeld wordt een eigenschap gebruikt om de numerieke dag van het jaar op te halen.</span><span class="sxs-lookup"><span data-stu-id="ddc83-152">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="ddc83-153">De Gregoriaanse kalender heeft 365 dagen, met uitzonde ring van schrikkel jaren die 366 dagen lang zijn.</span><span class="sxs-lookup"><span data-stu-id="ddc83-153">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="ddc83-154">Zo is 31 december 2020 dag 366.</span><span class="sxs-lookup"><span data-stu-id="ddc83-154">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="ddc83-155">`Get-Date` gebruikt drie para meters om de datum op te geven: **jaar**, **maand** en **dag**.</span><span class="sxs-lookup"><span data-stu-id="ddc83-155">`Get-Date` uses three parameters to specify the date: **Year**, **Month**, and **Day**.</span></span> <span data-ttu-id="ddc83-156">De opdracht wordt verpakt met haakjes zodat het resultaat door de eigenschap **DAYOFYEAR** wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="ddc83-156">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="ddc83-157">Voor beeld 6: controleren of een datum is aangepast aan zomer tijd</span><span class="sxs-lookup"><span data-stu-id="ddc83-157">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="ddc83-158">In dit voor beeld wordt een Booleaanse methode gebruikt om te controleren of een datum wordt gecorrigeerd met zomer tijd.</span><span class="sxs-lookup"><span data-stu-id="ddc83-158">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="ddc83-159">Een variabele, `$DST` slaat het resultaat van op `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="ddc83-159">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="ddc83-160">`$DST` maakt gebruik van de methode **IsDaylightSavingTime** om te testen of de datum wordt aangepast aan zomer tijd.</span><span class="sxs-lookup"><span data-stu-id="ddc83-160">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="ddc83-161">Voor beeld 7: de huidige tijd converteren naar UTC-tijd</span><span class="sxs-lookup"><span data-stu-id="ddc83-161">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="ddc83-162">In dit voor beeld wordt de huidige tijd geconverteerd naar UTC-tijd.</span><span class="sxs-lookup"><span data-stu-id="ddc83-162">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="ddc83-163">De UTC-offset voor de land instelling van het systeem wordt gebruikt om de tijd om te zetten.</span><span class="sxs-lookup"><span data-stu-id="ddc83-163">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="ddc83-164">Een tabel in de sectie [notities](#notes) bevat een lijst met geldige indelings specificaties voor **UFormat** .</span><span class="sxs-lookup"><span data-stu-id="ddc83-164">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="ddc83-165">`Get-Date` maakt gebruik van de para meter **UFormat** met indelings specificaties om de huidige systeem datum en-tijd weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-165">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="ddc83-166">De indelings aanduiding **% Z** vertegenwoordigt de UTC-afwijking van **-07**.</span><span class="sxs-lookup"><span data-stu-id="ddc83-166">The format specifier **%Z** represents the UTC offset of **-07**.</span></span>

<span data-ttu-id="ddc83-167">De `$Time` variabele bevat de huidige systeem datum en-tijd.</span><span class="sxs-lookup"><span data-stu-id="ddc83-167">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="ddc83-168">`$Time` maakt gebruik van de methode **ToUniversalTime ()** om de tijd om te zetten op basis van de UTC-afwijking van de computer.</span><span class="sxs-lookup"><span data-stu-id="ddc83-168">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="ddc83-169">Voor beeld 8: een tijds tempel maken</span><span class="sxs-lookup"><span data-stu-id="ddc83-169">Example 8: Create a timestamp</span></span>

<span data-ttu-id="ddc83-170">In dit voor beeld maakt een indelings aanduiding een **teken reeks** object voor een tijds tempel voor een directory naam.</span><span class="sxs-lookup"><span data-stu-id="ddc83-170">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="ddc83-171">De tijds tempel bevat de datum, tijd en UTC-offset.</span><span class="sxs-lookup"><span data-stu-id="ddc83-171">The timestamp includes the date, time, and UTC offset.</span></span>

```powershell
$timestamp = Get-Date -Format o | ForEach-Object { $_ -replace ":", "." }
New-Item -Path C:\Test\$timestamp -Type Directory
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         6/27/2019    07:59                2019-06-27T07.59.24.4603750-07.00
```

<span data-ttu-id="ddc83-172">De `$timestamp` variabele bevat de resultaten van een `Get-Date` opdracht.</span><span class="sxs-lookup"><span data-stu-id="ddc83-172">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="ddc83-173">`Get-Date` gebruikt de **indelings** parameter met de indelings specificatie van kleine letters `o` om een **teken reeks** object voor een tijds tempel te maken.</span><span class="sxs-lookup"><span data-stu-id="ddc83-173">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="ddc83-174">Het object wordt naar de pijp lijn verzonden `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="ddc83-174">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="ddc83-175">Een **script Block** bevat de `$_` variabele die het huidige pijplijn object vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="ddc83-175">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="ddc83-176">De tijds tempel teken reeks wordt gescheiden door dubbele punten die worden vervangen door punten.</span><span class="sxs-lookup"><span data-stu-id="ddc83-176">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="ddc83-177">`New-Item` gebruikt de para meter **Path** om de locatie voor een nieuwe map op te geven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-177">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="ddc83-178">Het pad bevat de `$timestamp` variabele als de mapnaam.</span><span class="sxs-lookup"><span data-stu-id="ddc83-178">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="ddc83-179">De **type** parameter geeft aan dat er een map is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="ddc83-179">The **Type** parameter specifies that a directory is created.</span></span>

## <span data-ttu-id="ddc83-180">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ddc83-180">PARAMETERS</span></span>

### <span data-ttu-id="ddc83-181">-Datum</span><span class="sxs-lookup"><span data-stu-id="ddc83-181">-Date</span></span>

<span data-ttu-id="ddc83-182">Hiermee geeft u een datum en tijd op.</span><span class="sxs-lookup"><span data-stu-id="ddc83-182">Specifies a date and time.</span></span> <span data-ttu-id="ddc83-183">Tijd is optioneel en als deze niet is opgegeven, wordt 00:00:00 geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ddc83-183">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="ddc83-184">Voer de datum en tijd in met een standaard indeling voor de systeem land instelling.</span><span class="sxs-lookup"><span data-stu-id="ddc83-184">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="ddc83-185">Bijvoorbeeld in Amerikaans Engels:</span><span class="sxs-lookup"><span data-stu-id="ddc83-185">For example, in US English:</span></span>

<span data-ttu-id="ddc83-186">`Get-Date -Date "6/25/2019 12:30:22"` retourneert dinsdag, 25 juni 2019 12:30:22</span><span class="sxs-lookup"><span data-stu-id="ddc83-186">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ddc83-187">-Dag</span><span class="sxs-lookup"><span data-stu-id="ddc83-187">-Day</span></span>

<span data-ttu-id="ddc83-188">Hiermee geeft u de dag van de maand op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-188">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="ddc83-189">Voer een waarde in van 1 tot 31.</span><span class="sxs-lookup"><span data-stu-id="ddc83-189">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="ddc83-190">Als de opgegeven waarde groter is dan het aantal dagen in een maand, voegt Power shell het aantal dagen toe aan de maand.</span><span class="sxs-lookup"><span data-stu-id="ddc83-190">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="ddc83-191">Zo wordt bijvoorbeeld `Get-Date -Month 2 -Day 31` **3 maart**, niet **31 februari**, weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-191">For example, `Get-Date -Month 2 -Day 31` displays **March 3**, not **February 31**.</span></span>

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

### <span data-ttu-id="ddc83-192">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="ddc83-192">-DisplayHint</span></span>

<span data-ttu-id="ddc83-193">Hiermee wordt bepaald welke elementen van de datum en tijd worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-193">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="ddc83-194">De geaccepteerde waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="ddc83-194">The accepted values are as follows:</span></span>

- <span data-ttu-id="ddc83-195">**Datum**: alleen de datum wordt weer gegeven</span><span class="sxs-lookup"><span data-stu-id="ddc83-195">**Date**: displays only the date</span></span>
- <span data-ttu-id="ddc83-196">**Tijd**: alleen de tijd weer geven</span><span class="sxs-lookup"><span data-stu-id="ddc83-196">**Time**: displays only the time</span></span>
- <span data-ttu-id="ddc83-197">Datum **tijd**: hier worden de datums en tijden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="ddc83-197">**DateTime**: displays the date and time</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ddc83-198">-Indeling</span><span class="sxs-lookup"><span data-stu-id="ddc83-198">-Format</span></span>

<span data-ttu-id="ddc83-199">Hier worden de datum en tijd weer gegeven in de Microsoft .NET Framework-indeling, zoals aangegeven in de indelings specificatie.</span><span class="sxs-lookup"><span data-stu-id="ddc83-199">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="ddc83-200">De **notatie** parameter voert een **teken reeks** object uit.</span><span class="sxs-lookup"><span data-stu-id="ddc83-200">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="ddc83-201">Zie [aangepaste datum-en tijd notatie reeksen](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)voor een lijst met beschik bare .net-indelings aanduidingen.</span><span class="sxs-lookup"><span data-stu-id="ddc83-201">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="ddc83-202">Wanneer de **notatie** para meter wordt gebruikt, worden `Get-Date` alleen de eigenschappen van het **DateTime** -object opgehaald die nodig zijn om de datum weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-202">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="ddc83-203">Als gevolg hiervan zijn sommige eigenschappen en methoden van **DateTime** -objecten mogelijk niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="ddc83-203">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="ddc83-204">Vanaf Power shell 5,0 kunt u de volgende extra notaties gebruiken als waarden voor de **notatie** parameter.</span><span class="sxs-lookup"><span data-stu-id="ddc83-204">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="ddc83-205">**FileDate**.</span><span class="sxs-lookup"><span data-stu-id="ddc83-205">**FileDate**.</span></span> <span data-ttu-id="ddc83-206">Een bestands-of pad-gebruiks vriendelijke representatie van de huidige datum in de lokale tijd.</span><span class="sxs-lookup"><span data-stu-id="ddc83-206">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="ddc83-207">De notatie is `yyyyMMdd` (hoofdletter gevoelig, met een jaar van vier cijfers, een maand van 2 cijfers en een dag van 2 cijfers).</span><span class="sxs-lookup"><span data-stu-id="ddc83-207">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="ddc83-208">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ddc83-208">For example:</span></span>
  20190627.

- <span data-ttu-id="ddc83-209">**FileDateUniversal**.</span><span class="sxs-lookup"><span data-stu-id="ddc83-209">**FileDateUniversal**.</span></span> <span data-ttu-id="ddc83-210">Een bestands-of pad-beschrijvende weer gave van de huidige datum in Universal Time (UTC).</span><span class="sxs-lookup"><span data-stu-id="ddc83-210">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="ddc83-211">De notatie is `yyyyMMddZ` (hoofdletter gevoelig, met een jaar van vier cijfers, een maand van 2 cijfers, een dag van 2 cijfers en de letter `Z` als de UTC-indicator).</span><span class="sxs-lookup"><span data-stu-id="ddc83-211">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="ddc83-212">Bijvoorbeeld: 20190627Z.</span><span class="sxs-lookup"><span data-stu-id="ddc83-212">For example: 20190627Z.</span></span>

- <span data-ttu-id="ddc83-213">**FileDateTime**.</span><span class="sxs-lookup"><span data-stu-id="ddc83-213">**FileDateTime**.</span></span> <span data-ttu-id="ddc83-214">Een bestands-of pad-gebruiks vriendelijke weer gave van de huidige datum en tijd in de lokale tijd, in 24-uurs notatie.</span><span class="sxs-lookup"><span data-stu-id="ddc83-214">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="ddc83-215">De notatie is `yyyyMMddTHHmmssffff` (hoofdletter gevoelig, met behulp van een jaar van vier cijfers, een maand van 2 cijfers, een dag van 2 cijfers, de letter als een tijd scheidings teken, een uur van twee cijfers, een minuut van twee cijfers en een `T` milliseconden van 4 cijfers).</span><span class="sxs-lookup"><span data-stu-id="ddc83-215">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="ddc83-216">Bijvoorbeeld: 20190627T0840107271.</span><span class="sxs-lookup"><span data-stu-id="ddc83-216">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="ddc83-217">**FileDateTimeUniversal**.</span><span class="sxs-lookup"><span data-stu-id="ddc83-217">**FileDateTimeUniversal**.</span></span> <span data-ttu-id="ddc83-218">Een bestands-of pad-gebruiks vriendelijke weer gave van de huidige datum en tijd in UTC (Universal Time), in 24-uurs notatie.</span><span class="sxs-lookup"><span data-stu-id="ddc83-218">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="ddc83-219">De notatie is `yyyyMMddTHHmmssffffZ` (hoofdletter gevoelig, met behulp van een jaar van vier cijfers, een maand van twee cijfers, de letter `T` als een tijd scheidings teken, een uur van twee cijfers, een minuut van twee cijfers, een tweede milliseconde en de letter `Z` als de UTC-indicator).</span><span class="sxs-lookup"><span data-stu-id="ddc83-219">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="ddc83-220">Bijvoorbeeld: 20190627T1540500718Z.</span><span class="sxs-lookup"><span data-stu-id="ddc83-220">For example: 20190627T1540500718Z.</span></span>

```yaml
Type: System.String
Parameter Sets: net
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ddc83-221">-Uur</span><span class="sxs-lookup"><span data-stu-id="ddc83-221">-Hour</span></span>

<span data-ttu-id="ddc83-222">Hiermee geeft u het uur op dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-222">Specifies the hour that is displayed.</span></span> <span data-ttu-id="ddc83-223">Voer een waarde tussen 0 en 23 in.</span><span class="sxs-lookup"><span data-stu-id="ddc83-223">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="ddc83-224">-Milliseconde</span><span class="sxs-lookup"><span data-stu-id="ddc83-224">-Millisecond</span></span>

<span data-ttu-id="ddc83-225">Geeft de milliseconden in de datum aan.</span><span class="sxs-lookup"><span data-stu-id="ddc83-225">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="ddc83-226">Voer een waarde in tussen 0 en 999.</span><span class="sxs-lookup"><span data-stu-id="ddc83-226">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="ddc83-227">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ddc83-227">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ddc83-228">-Minuut</span><span class="sxs-lookup"><span data-stu-id="ddc83-228">-Minute</span></span>

<span data-ttu-id="ddc83-229">Hiermee geeft u de minuut op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-229">Specifies the minute that is displayed.</span></span> <span data-ttu-id="ddc83-230">Voer een waarde in tussen 0 en 59.</span><span class="sxs-lookup"><span data-stu-id="ddc83-230">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="ddc83-231">-Maand</span><span class="sxs-lookup"><span data-stu-id="ddc83-231">-Month</span></span>

<span data-ttu-id="ddc83-232">Hiermee geeft u de maand op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-232">Specifies the month that is displayed.</span></span> <span data-ttu-id="ddc83-233">Voer een waarde tussen 1 en 12 in.</span><span class="sxs-lookup"><span data-stu-id="ddc83-233">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="ddc83-234">-Seconde</span><span class="sxs-lookup"><span data-stu-id="ddc83-234">-Second</span></span>

<span data-ttu-id="ddc83-235">Hiermee geeft u de seconde op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-235">Specifies the second that is displayed.</span></span> <span data-ttu-id="ddc83-236">Voer een waarde in tussen 0 en 59.</span><span class="sxs-lookup"><span data-stu-id="ddc83-236">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="ddc83-237">-UFormat</span><span class="sxs-lookup"><span data-stu-id="ddc83-237">-UFormat</span></span>

<span data-ttu-id="ddc83-238">Hiermee worden de datum en tijd in de UNIX-indeling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-238">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="ddc83-239">De para meter **UFormat** voert een teken reeks object uit.</span><span class="sxs-lookup"><span data-stu-id="ddc83-239">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="ddc83-240">**UFormat** -aanduidingen worden voorafgegaan door een procent teken ( `%` ), bijvoorbeeld, `%m` , `%d` en `%Y` .</span><span class="sxs-lookup"><span data-stu-id="ddc83-240">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="ddc83-241">De sectie [notities](#notes) bevat een tabel met geldige **UFormat-aanduidingen**.</span><span class="sxs-lookup"><span data-stu-id="ddc83-241">The [Notes](#notes) section contains a table of valid **UFormat specifiers**.</span></span>

<span data-ttu-id="ddc83-242">Wanneer de para meter **UFormat** wordt gebruikt, worden `Get-Date` alleen de eigenschappen van het object **DateTime** opgehaald die nodig zijn om de datum weer te geven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-242">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="ddc83-243">Als gevolg hiervan zijn sommige eigenschappen en methoden van **DateTime** -objecten mogelijk niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="ddc83-243">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

```yaml
Type: System.String
Parameter Sets: UFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ddc83-244">-Jaar</span><span class="sxs-lookup"><span data-stu-id="ddc83-244">-Year</span></span>

<span data-ttu-id="ddc83-245">Hiermee geeft u het jaar op dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ddc83-245">Specifies the year that is displayed.</span></span> <span data-ttu-id="ddc83-246">Voer een waarde in van 1 tot en met 9999.</span><span class="sxs-lookup"><span data-stu-id="ddc83-246">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="ddc83-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ddc83-247">CommonParameters</span></span>

<span data-ttu-id="ddc83-248">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ddc83-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ddc83-249">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ddc83-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ddc83-250">INVOER</span><span class="sxs-lookup"><span data-stu-id="ddc83-250">INPUTS</span></span>

### <span data-ttu-id="ddc83-251">Pijplijn invoer</span><span class="sxs-lookup"><span data-stu-id="ddc83-251">Pipeline input</span></span>

<span data-ttu-id="ddc83-252">`Get-Date` accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="ddc83-252">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="ddc83-253">Bijvoorbeeld `Get-ChildItem | Get-Date`.</span><span class="sxs-lookup"><span data-stu-id="ddc83-253">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="ddc83-254">UITVOER</span><span class="sxs-lookup"><span data-stu-id="ddc83-254">OUTPUTS</span></span>

### <span data-ttu-id="ddc83-255">System. DateTime of System. String</span><span class="sxs-lookup"><span data-stu-id="ddc83-255">System.DateTime or System.String</span></span>

<span data-ttu-id="ddc83-256">`Get-Date` retourneert een **DateTime** -object, behalve wanneer de **notatie** -en **UFormat** -para meters worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ddc83-256">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="ddc83-257">De **notatie** of para meters van de **UFormat** retour neren **teken reeks** objecten.</span><span class="sxs-lookup"><span data-stu-id="ddc83-257">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="ddc83-258">Wanneer een **DateTime** -object vanuit de pijp lijn naar een cmdlet wordt verzonden `Add-Content` , zoals de teken reeks invoer verwacht, converteert Power shell het object naar een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="ddc83-258">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="ddc83-259">Met de-methode wordt `(Get-Date).ToString()` een **DateTime** -object omgezet in een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="ddc83-259">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="ddc83-260">Als u de eigenschappen en methoden van een object wilt weer geven, verzendt u het object omlaag in de pijp lijn `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="ddc83-260">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="ddc83-261">Bijvoorbeeld `Get-Date | Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="ddc83-261">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="ddc83-262">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="ddc83-262">NOTES</span></span>

<span data-ttu-id="ddc83-263">**DateTime** -objecten hebben een lange datum en lange tijd notatie voor de systeem land instelling.</span><span class="sxs-lookup"><span data-stu-id="ddc83-263">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="ddc83-264">De geldige **UFormat-specificaties** worden weer gegeven in de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="ddc83-264">The valid **UFormat specifiers** are displayed in the following table:</span></span>

| <span data-ttu-id="ddc83-265">Indelings aanduiding</span><span class="sxs-lookup"><span data-stu-id="ddc83-265">Format specifier</span></span> |                                 <span data-ttu-id="ddc83-266">Betekenis</span><span class="sxs-lookup"><span data-stu-id="ddc83-266">Meaning</span></span>                     |         <span data-ttu-id="ddc83-267">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ddc83-267">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="ddc83-268">Dag van de week-volledige naam</span><span class="sxs-lookup"><span data-stu-id="ddc83-268">Day of the week - full name</span></span>                                             | <span data-ttu-id="ddc83-269">Maandag</span><span class="sxs-lookup"><span data-stu-id="ddc83-269">Monday</span></span>                   |
| `%a` | <span data-ttu-id="ddc83-270">Dag van de week, korte naam</span><span class="sxs-lookup"><span data-stu-id="ddc83-270">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="ddc83-271">Ma</span><span class="sxs-lookup"><span data-stu-id="ddc83-271">Mon</span></span>                      |
| `%B` | <span data-ttu-id="ddc83-272">Maand naam-volledig</span><span class="sxs-lookup"><span data-stu-id="ddc83-272">Month name - full</span></span>                                                       | <span data-ttu-id="ddc83-273">Januari</span><span class="sxs-lookup"><span data-stu-id="ddc83-273">January</span></span>                  |
| `%b` | <span data-ttu-id="ddc83-274">Maand naam-afgekort</span><span class="sxs-lookup"><span data-stu-id="ddc83-274">Month name - abbreviated</span></span>                                                | <span data-ttu-id="ddc83-275">Jan</span><span class="sxs-lookup"><span data-stu-id="ddc83-275">Jan</span></span>                      |
| `%C` | <span data-ttu-id="ddc83-276">Jaar</span><span class="sxs-lookup"><span data-stu-id="ddc83-276">Century</span></span>                                                                 | <span data-ttu-id="ddc83-277">20 voor 2019</span><span class="sxs-lookup"><span data-stu-id="ddc83-277">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="ddc83-278">Datum en tijd-afgekort</span><span class="sxs-lookup"><span data-stu-id="ddc83-278">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="ddc83-279">Do jun 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="ddc83-279">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="ddc83-280">Datum in de notatie mm/dd/jj</span><span class="sxs-lookup"><span data-stu-id="ddc83-280">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="ddc83-281">06/27/19</span><span class="sxs-lookup"><span data-stu-id="ddc83-281">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="ddc83-282">Dag van de maand: 2 cijfers</span><span class="sxs-lookup"><span data-stu-id="ddc83-282">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="ddc83-283">05</span><span class="sxs-lookup"><span data-stu-id="ddc83-283">05</span></span>                       |
| `%e` | <span data-ttu-id="ddc83-284">Dag van de maand, voorafgegaan door een spatie als er slechts één cijfer</span><span class="sxs-lookup"><span data-stu-id="ddc83-284">Day of the month - preceded by a space if only a single digit</span></span>           | <span data-ttu-id="ddc83-285">\<space\>5,0</span><span class="sxs-lookup"><span data-stu-id="ddc83-285">\<space\>5</span></span>               |
| `%F` | <span data-ttu-id="ddc83-286">Datum in de notatie JJJJ-MM-DD, gelijk aan% Y-% m-% d (ISO 8601-datum notatie)</span><span class="sxs-lookup"><span data-stu-id="ddc83-286">Date in YYYY-mm-dd format, equal to %Y-%m-%d (the ISO 8601 date format)</span></span> | <span data-ttu-id="ddc83-287">2019-06-27</span><span class="sxs-lookup"><span data-stu-id="ddc83-287">2019-06-27</span></span>               |
| `%G` | <span data-ttu-id="ddc83-288">Hetzelfde als ' Y '</span><span class="sxs-lookup"><span data-stu-id="ddc83-288">Same as 'Y'</span></span>                                                             |                          |
| `%g` | <span data-ttu-id="ddc83-289">Hetzelfde als ' y '</span><span class="sxs-lookup"><span data-stu-id="ddc83-289">Same as 'y'</span></span>                                                             |                          |
| `%H` | <span data-ttu-id="ddc83-290">Uur in 24-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="ddc83-290">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="ddc83-291">17</span><span class="sxs-lookup"><span data-stu-id="ddc83-291">17</span></span>                       |
| `%h` | <span data-ttu-id="ddc83-292">Hetzelfde als ' b '</span><span class="sxs-lookup"><span data-stu-id="ddc83-292">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="ddc83-293">Uur in 12-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="ddc83-293">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="ddc83-294">05</span><span class="sxs-lookup"><span data-stu-id="ddc83-294">05</span></span>                       |
| `%j` | <span data-ttu-id="ddc83-295">Dag van het jaar</span><span class="sxs-lookup"><span data-stu-id="ddc83-295">Day of the year</span></span>                                                         | <span data-ttu-id="ddc83-296">1-366</span><span class="sxs-lookup"><span data-stu-id="ddc83-296">1-366</span></span>                    |
| `%k` | <span data-ttu-id="ddc83-297">Hetzelfde als ' H '</span><span class="sxs-lookup"><span data-stu-id="ddc83-297">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="ddc83-298">Hetzelfde als ' I ' (hoofd letters I)</span><span class="sxs-lookup"><span data-stu-id="ddc83-298">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="ddc83-299">05</span><span class="sxs-lookup"><span data-stu-id="ddc83-299">05</span></span>                       |
| `%M` | <span data-ttu-id="ddc83-300">Minuten</span><span class="sxs-lookup"><span data-stu-id="ddc83-300">Minutes</span></span>                                                                 | <span data-ttu-id="ddc83-301">35</span><span class="sxs-lookup"><span data-stu-id="ddc83-301">35</span></span>                       |
| `%m` | <span data-ttu-id="ddc83-302">Maandnummer</span><span class="sxs-lookup"><span data-stu-id="ddc83-302">Month number</span></span>                                                            | <span data-ttu-id="ddc83-303">06</span><span class="sxs-lookup"><span data-stu-id="ddc83-303">06</span></span>                       |
| `%n` | <span data-ttu-id="ddc83-304">teken voor nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="ddc83-304">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="ddc83-305">AM of PM</span><span class="sxs-lookup"><span data-stu-id="ddc83-305">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="ddc83-306">Tijd in 24-uurs notatie-geen seconden</span><span class="sxs-lookup"><span data-stu-id="ddc83-306">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="ddc83-307">17:45</span><span class="sxs-lookup"><span data-stu-id="ddc83-307">17:45</span></span>                    |
| `%r` | <span data-ttu-id="ddc83-308">Tijd in 12-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="ddc83-308">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="ddc83-309">09:15:36 UUR</span><span class="sxs-lookup"><span data-stu-id="ddc83-309">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="ddc83-310">Seconden</span><span class="sxs-lookup"><span data-stu-id="ddc83-310">Seconds</span></span>                                                                 | <span data-ttu-id="ddc83-311">05</span><span class="sxs-lookup"><span data-stu-id="ddc83-311">05</span></span>                       |
| `%s` | <span data-ttu-id="ddc83-312">Seconden verstreken sinds 1 januari 1970 00:00:00</span><span class="sxs-lookup"><span data-stu-id="ddc83-312">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="ddc83-313">1150451174</span><span class="sxs-lookup"><span data-stu-id="ddc83-313">1150451174</span></span>               |
| `%t` | <span data-ttu-id="ddc83-314">Teken voor horizontale tab</span><span class="sxs-lookup"><span data-stu-id="ddc83-314">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="ddc83-315">Tijd in 24-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="ddc83-315">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="ddc83-316">17:45:52</span><span class="sxs-lookup"><span data-stu-id="ddc83-316">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="ddc83-317">Hetzelfde als ' W '</span><span class="sxs-lookup"><span data-stu-id="ddc83-317">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="ddc83-318">Dag van het week nummer</span><span class="sxs-lookup"><span data-stu-id="ddc83-318">Day of the week - number</span></span>                                                | <span data-ttu-id="ddc83-319">Zondag = 0</span><span class="sxs-lookup"><span data-stu-id="ddc83-319">Sunday = 0</span></span>               |
| `%V` | <span data-ttu-id="ddc83-320">Week van het jaar</span><span class="sxs-lookup"><span data-stu-id="ddc83-320">Week of the year</span></span>                                                        | <span data-ttu-id="ddc83-321">01-53</span><span class="sxs-lookup"><span data-stu-id="ddc83-321">01-53</span></span>                    |
| `%w` | <span data-ttu-id="ddc83-322">Hetzelfde als ' u '</span><span class="sxs-lookup"><span data-stu-id="ddc83-322">Same as 'u'</span></span>                                                             |                          |
| `%W` | <span data-ttu-id="ddc83-323">Week van het jaar</span><span class="sxs-lookup"><span data-stu-id="ddc83-323">Week of the year</span></span>                                                        | <span data-ttu-id="ddc83-324">00-52</span><span class="sxs-lookup"><span data-stu-id="ddc83-324">00-52</span></span>                    |
| `%X` | <span data-ttu-id="ddc83-325">Hetzelfde als 'T '</span><span class="sxs-lookup"><span data-stu-id="ddc83-325">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="ddc83-326">Datum in de standaard notatie voor de land instelling</span><span class="sxs-lookup"><span data-stu-id="ddc83-326">Date in standard format for locale</span></span>                                      | <span data-ttu-id="ddc83-327">06/27/19 voor Engels-US</span><span class="sxs-lookup"><span data-stu-id="ddc83-327">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="ddc83-328">Jaar met viercijferige notatie</span><span class="sxs-lookup"><span data-stu-id="ddc83-328">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="ddc83-329">2019</span><span class="sxs-lookup"><span data-stu-id="ddc83-329">2019</span></span>                     |
| `%y` | <span data-ttu-id="ddc83-330">Jaar met een notatie van twee cijfers</span><span class="sxs-lookup"><span data-stu-id="ddc83-330">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="ddc83-331">19</span><span class="sxs-lookup"><span data-stu-id="ddc83-331">19</span></span>                       |
| `%Z` | <span data-ttu-id="ddc83-332">Tijd zone-offset van Universal Time Coordinate (UTC)</span><span class="sxs-lookup"><span data-stu-id="ddc83-332">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="ddc83-333">-07</span><span class="sxs-lookup"><span data-stu-id="ddc83-333">-07</span></span>                      |

## <span data-ttu-id="ddc83-334">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="ddc83-334">RELATED LINKS</span></span>

[<span data-ttu-id="ddc83-335">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="ddc83-335">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="ddc83-336">Get-cultuur</span><span class="sxs-lookup"><span data-stu-id="ddc83-336">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="ddc83-337">Get-member</span><span class="sxs-lookup"><span data-stu-id="ddc83-337">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="ddc83-338">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="ddc83-338">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="ddc83-339">Nieuw-time span</span><span class="sxs-lookup"><span data-stu-id="ddc83-339">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="ddc83-340">Set-date</span><span class="sxs-lookup"><span data-stu-id="ddc83-340">Set-Date</span></span>](Set-Date.md)
