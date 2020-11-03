---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: a299b04c8e041819ef2870abe263fae381b1d5dc
ms.sourcegitcommit: ea9270bacee7dd1b9df2519384de277576357ce2
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/25/2020
ms.locfileid: "93251865"
---
# <span data-ttu-id="43d34-103">Get-Date</span><span class="sxs-lookup"><span data-stu-id="43d34-103">Get-Date</span></span>

## <span data-ttu-id="43d34-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="43d34-104">SYNOPSIS</span></span>
<span data-ttu-id="43d34-105">Hiermee worden de huidige datum en tijd opgehaald.</span><span class="sxs-lookup"><span data-stu-id="43d34-105">Gets the current date and time.</span></span>

## <span data-ttu-id="43d34-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="43d34-106">SYNTAX</span></span>

### <span data-ttu-id="43d34-107">Datum (standaard)</span><span class="sxs-lookup"><span data-stu-id="43d34-107">Date (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="43d34-108">DateUFormat</span><span class="sxs-lookup"><span data-stu-id="43d34-108">DateUFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### <span data-ttu-id="43d34-109">UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="43d34-109">UnixTimeSeconds</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="43d34-110">UnixTimeSecondsUFormat</span><span class="sxs-lookup"><span data-stu-id="43d34-110">UnixTimeSecondsUFormat</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## <span data-ttu-id="43d34-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="43d34-111">DESCRIPTION</span></span>

<span data-ttu-id="43d34-112">De `Get-Date` cmdlet haalt een **DateTime** -object op dat staat voor de huidige datum of een datum die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="43d34-112">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="43d34-113">`Get-Date` de datum en tijd in verschillende .NET-en UNIX-indelingen kunnen worden ingedeeld.</span><span class="sxs-lookup"><span data-stu-id="43d34-113">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="43d34-114">U kunt gebruiken `Get-Date` voor het genereren van een teken reeks voor datum of tijd en vervolgens de teken reeks verzenden naar andere cmdlets of Program ma's.</span><span class="sxs-lookup"><span data-stu-id="43d34-114">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="43d34-115">`Get-Date` gebruikt de instellingen van de computer cultuur om te bepalen hoe de uitvoer wordt geformatteerd.</span><span class="sxs-lookup"><span data-stu-id="43d34-115">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="43d34-116">Gebruik om de instellingen van uw computer weer te geven `(Get-Culture).DateTimeFormat` .</span><span class="sxs-lookup"><span data-stu-id="43d34-116">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="43d34-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="43d34-117">EXAMPLES</span></span>

### <span data-ttu-id="43d34-118">Voor beeld 1: de huidige datum en tijd ophalen</span><span class="sxs-lookup"><span data-stu-id="43d34-118">Example 1: Get the current date and time</span></span>

<span data-ttu-id="43d34-119">In dit voor beeld `Get-Date` worden de huidige systeem datum en-tijd weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43d34-119">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="43d34-120">De uitvoer bevindt zich in de notatie voor lange en lange tijd.</span><span class="sxs-lookup"><span data-stu-id="43d34-120">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="43d34-121">Voor beeld 2: elementen van de huidige datum en tijd ophalen</span><span class="sxs-lookup"><span data-stu-id="43d34-121">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="43d34-122">In dit voor beeld ziet u hoe u kunt gebruiken `Get-Date` om het datum-of tijd-element op te halen.</span><span class="sxs-lookup"><span data-stu-id="43d34-122">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="43d34-123">De para meter gebruikt de argumenten **datum** , **tijd** of **datum/** tijd.</span><span class="sxs-lookup"><span data-stu-id="43d34-123">The parameter uses the arguments **Date** , **Time** , or **DateTime**.</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="43d34-124">`Get-Date` gebruikt de para meter **DisplayHint** met het **datum** argument om alleen de datum op te halen.</span><span class="sxs-lookup"><span data-stu-id="43d34-124">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="43d34-125">Voor beeld 3: de datum en tijd ophalen met een specificatie van .NET-indeling</span><span class="sxs-lookup"><span data-stu-id="43d34-125">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="43d34-126">In dit voor beeld wordt een .NET-indelings specificatie gebruikt om de indeling van de uitvoer aan te passen.</span><span class="sxs-lookup"><span data-stu-id="43d34-126">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="43d34-127">De uitvoer is een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="43d34-127">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="43d34-128">`Get-Date` gebruikt de **indelings** parameter om verschillende indelings aanduidingen op te geven.</span><span class="sxs-lookup"><span data-stu-id="43d34-128">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="43d34-129">De .NET-indelings specificaties die in dit voor beeld worden gebruikt, zijn als volgt gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="43d34-129">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="43d34-130">Aanduiding</span><span class="sxs-lookup"><span data-stu-id="43d34-130">Specifier</span></span> |                      <span data-ttu-id="43d34-131">Definitie</span><span class="sxs-lookup"><span data-stu-id="43d34-131">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | <span data-ttu-id="43d34-132">Dag van de week-volledige naam</span><span class="sxs-lookup"><span data-stu-id="43d34-132">Day of the week - full name</span></span>                           |
| `MM`      | <span data-ttu-id="43d34-133">Maandnummer</span><span class="sxs-lookup"><span data-stu-id="43d34-133">Month number</span></span>                                          |
| `dd`      | <span data-ttu-id="43d34-134">Dag van de maand: 2 cijfers</span><span class="sxs-lookup"><span data-stu-id="43d34-134">Day of the month - 2 digits</span></span>                           |
| `yyyy`    | <span data-ttu-id="43d34-135">Jaar met viercijferige notatie</span><span class="sxs-lookup"><span data-stu-id="43d34-135">Year in 4-digit format</span></span>                                |
| `HH:mm`   | <span data-ttu-id="43d34-136">Tijd in 24-uurs notatie-geen seconden</span><span class="sxs-lookup"><span data-stu-id="43d34-136">Time in 24-hour format - no seconds</span></span>                    |
| `K`       | <span data-ttu-id="43d34-137">Tijd zone-offset van Universal Time Coordinate (UTC)</span><span class="sxs-lookup"><span data-stu-id="43d34-137">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="43d34-138">Zie [aangepaste datum-en tijd notatie reeksen](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)voor meer informatie over .net-indelings specificaties.</span><span class="sxs-lookup"><span data-stu-id="43d34-138">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="43d34-139">Voor beeld 4: de datum en tijd ophalen met een UFormat-aanduiding</span><span class="sxs-lookup"><span data-stu-id="43d34-139">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="43d34-140">In dit voor beeld worden verschillende **UFormat** -indelings specificaties gebruikt voor het aanpassen van de indeling van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="43d34-140">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="43d34-141">De uitvoer is een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="43d34-141">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="43d34-142">`Get-Date` maakt gebruik van de para meter **UFormat** om verschillende indelings specificaties op te geven.</span><span class="sxs-lookup"><span data-stu-id="43d34-142">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="43d34-143">De **UFormat** -indelings specificaties die in dit voor beeld worden gebruikt, zijn als volgt gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="43d34-143">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="43d34-144">Aanduiding</span><span class="sxs-lookup"><span data-stu-id="43d34-144">Specifier</span></span> |                      <span data-ttu-id="43d34-145">Definitie</span><span class="sxs-lookup"><span data-stu-id="43d34-145">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `%A`      | <span data-ttu-id="43d34-146">Dag van de week-volledige naam</span><span class="sxs-lookup"><span data-stu-id="43d34-146">Day of the week - full name</span></span>                           |
| `%m`      | <span data-ttu-id="43d34-147">Maandnummer</span><span class="sxs-lookup"><span data-stu-id="43d34-147">Month number</span></span>                                          |
| `%d`      | <span data-ttu-id="43d34-148">Dag van de maand: 2 cijfers</span><span class="sxs-lookup"><span data-stu-id="43d34-148">Day of the month - 2 digits</span></span>                           |
| `%Y`      | <span data-ttu-id="43d34-149">Jaar met viercijferige notatie</span><span class="sxs-lookup"><span data-stu-id="43d34-149">Year in 4-digit format</span></span>                                |
| `%R`      | <span data-ttu-id="43d34-150">Tijd in 24-uurs notatie-geen seconden</span><span class="sxs-lookup"><span data-stu-id="43d34-150">Time in 24-hour format - no seconds</span></span>                    |
| `%Z`      | <span data-ttu-id="43d34-151">Tijd zone-offset van Universal Time Coordinate (UTC)</span><span class="sxs-lookup"><span data-stu-id="43d34-151">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="43d34-152">Zie de sectie [opmerkingen](#notes) voor een lijst met geldige indelings specificaties voor **UFormat** .</span><span class="sxs-lookup"><span data-stu-id="43d34-152">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="43d34-153">Voor beeld 5: de dag van een datum van het jaar ophalen</span><span class="sxs-lookup"><span data-stu-id="43d34-153">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="43d34-154">In dit voor beeld wordt een eigenschap gebruikt om de numerieke dag van het jaar op te halen.</span><span class="sxs-lookup"><span data-stu-id="43d34-154">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="43d34-155">De Gregoriaanse kalender heeft 365 dagen, met uitzonde ring van schrikkel jaren die 366 dagen lang zijn.</span><span class="sxs-lookup"><span data-stu-id="43d34-155">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="43d34-156">Zo is 31 december 2020 dag 366.</span><span class="sxs-lookup"><span data-stu-id="43d34-156">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="43d34-157">`Get-Date` gebruikt drie para meters om de datum op te geven: **jaar** , **maand** en **dag**.</span><span class="sxs-lookup"><span data-stu-id="43d34-157">`Get-Date` uses three parameters to specify the date: **Year** , **Month** , and **Day**.</span></span> <span data-ttu-id="43d34-158">De opdracht wordt verpakt met haakjes zodat het resultaat door de eigenschap **DAYOFYEAR** wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="43d34-158">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="43d34-159">Voor beeld 6: controleren of een datum is aangepast aan zomer tijd</span><span class="sxs-lookup"><span data-stu-id="43d34-159">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="43d34-160">In dit voor beeld wordt een Booleaanse methode gebruikt om te controleren of een datum wordt gecorrigeerd met zomer tijd.</span><span class="sxs-lookup"><span data-stu-id="43d34-160">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="43d34-161">Een variabele, `$DST` slaat het resultaat van op `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="43d34-161">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="43d34-162">`$DST` maakt gebruik van de methode **IsDaylightSavingTime** om te testen of de datum wordt aangepast aan zomer tijd.</span><span class="sxs-lookup"><span data-stu-id="43d34-162">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="43d34-163">Voor beeld 7: de huidige tijd converteren naar UTC-tijd</span><span class="sxs-lookup"><span data-stu-id="43d34-163">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="43d34-164">In dit voor beeld wordt de huidige tijd geconverteerd naar UTC-tijd.</span><span class="sxs-lookup"><span data-stu-id="43d34-164">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="43d34-165">De UTC-offset voor de land instelling van het systeem wordt gebruikt om de tijd om te zetten.</span><span class="sxs-lookup"><span data-stu-id="43d34-165">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="43d34-166">Een tabel in de sectie [notities](#notes) bevat een lijst met geldige indelings specificaties voor **UFormat** .</span><span class="sxs-lookup"><span data-stu-id="43d34-166">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="43d34-167">`Get-Date` maakt gebruik van de para meter **UFormat** met indelings specificaties om de huidige systeem datum en-tijd weer te geven.</span><span class="sxs-lookup"><span data-stu-id="43d34-167">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="43d34-168">De indelings aanduiding **% Z** vertegenwoordigt de UTC-afwijking van **-07**.</span><span class="sxs-lookup"><span data-stu-id="43d34-168">The format specifier **%Z** represents the UTC offset of **-07**.</span></span>

<span data-ttu-id="43d34-169">De `$Time` variabele bevat de huidige systeem datum en-tijd.</span><span class="sxs-lookup"><span data-stu-id="43d34-169">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="43d34-170">`$Time` maakt gebruik van de methode **ToUniversalTime ()** om de tijd om te zetten op basis van de UTC-afwijking van de computer.</span><span class="sxs-lookup"><span data-stu-id="43d34-170">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="43d34-171">Voor beeld 8: een tijds tempel maken</span><span class="sxs-lookup"><span data-stu-id="43d34-171">Example 8: Create a timestamp</span></span>

<span data-ttu-id="43d34-172">In dit voor beeld maakt een indelings aanduiding een **teken reeks** object voor een tijds tempel voor een directory naam.</span><span class="sxs-lookup"><span data-stu-id="43d34-172">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="43d34-173">De tijds tempel bevat de datum, tijd en UTC-offset.</span><span class="sxs-lookup"><span data-stu-id="43d34-173">The timestamp includes the date, time, and UTC offset.</span></span>

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

<span data-ttu-id="43d34-174">De `$timestamp` variabele bevat de resultaten van een `Get-Date` opdracht.</span><span class="sxs-lookup"><span data-stu-id="43d34-174">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="43d34-175">`Get-Date` gebruikt de **indelings** parameter met de indelings specificatie van kleine letters `o` om een **teken reeks** object voor een tijds tempel te maken.</span><span class="sxs-lookup"><span data-stu-id="43d34-175">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="43d34-176">Het object wordt naar de pijp lijn verzonden `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="43d34-176">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="43d34-177">Een **script Block** bevat de `$_` variabele die het huidige pijplijn object vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="43d34-177">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="43d34-178">De tijds tempel teken reeks wordt gescheiden door dubbele punten die worden vervangen door punten.</span><span class="sxs-lookup"><span data-stu-id="43d34-178">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="43d34-179">`New-Item` gebruikt de para meter **Path** om de locatie voor een nieuwe map op te geven.</span><span class="sxs-lookup"><span data-stu-id="43d34-179">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="43d34-180">Het pad bevat de `$timestamp` variabele als de mapnaam.</span><span class="sxs-lookup"><span data-stu-id="43d34-180">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="43d34-181">De **type** parameter geeft aan dat er een map is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="43d34-181">The **Type** parameter specifies that a directory is created.</span></span>

### <span data-ttu-id="43d34-182">Voor beeld 9: een Unix-Time Stamp converteren</span><span class="sxs-lookup"><span data-stu-id="43d34-182">Example 9: Convert a Unix timestamp</span></span>

<span data-ttu-id="43d34-183">In dit voor beeld wordt een Unix-tijd (vertegenwoordigd door het aantal seconden sinds 1970-01-01 0:00:00) geconverteerd naar DateTime.</span><span class="sxs-lookup"><span data-stu-id="43d34-183">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### <span data-ttu-id="43d34-184">Voor beeld 10: een datum waarde Retour neren die als UTC wordt geïnterpreteerd</span><span class="sxs-lookup"><span data-stu-id="43d34-184">Example 10: Return a date value interpreted as UTC</span></span>

<span data-ttu-id="43d34-185">In dit voor beeld ziet u hoe u een datum waarde als UTC-equivalent kunt interpreteren.</span><span class="sxs-lookup"><span data-stu-id="43d34-185">This example shows how to interpret a date value as its UTC equivalent.</span></span> <span data-ttu-id="43d34-186">Voor dit voor beeld is deze computer ingesteld op **Pacific Standard Time**.</span><span class="sxs-lookup"><span data-stu-id="43d34-186">For the example, this machine is set to **Pacific Standard Time**.</span></span> <span data-ttu-id="43d34-187">Standaard worden `Get-Date` waarden voor die tijd zone geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="43d34-187">By default, `Get-Date` returns values for that timezone.</span></span> <span data-ttu-id="43d34-188">Gebruik de para meter **AsUTC** om de waarde te converteren naar de EQUIVALENTe UTC-tijd.</span><span class="sxs-lookup"><span data-stu-id="43d34-188">Use the **AsUTC** parameter to convert the value to the UTC equivalent time.</span></span>

```powershell
PS> Get-TimeZone

Id                         : Pacific Standard Time
DisplayName                : (UTC-08:00) Pacific Time (US & Canada)
StandardName               : Pacific Standard Time
DaylightName               : Pacific Daylight Time
BaseUtcOffset              : -08:00:00
SupportsDaylightSavingTime : True

PS> (Get-Date -Date "2020-01-01T00:00:00").Kind
Unspecified

PS> Get-Date -Date "2020-01-01T00:00:00"

Wednesday, January 1, 2020 12:00:00 AM

PS> (Get-Date -Date "2020-01-01T00:00:00" -AsUTC).Kind
Utc

PS> Get-Date -Date "2020-01-01T00:00:00" -AsUTC

Wednesday, January 1, 2020 8:00:00 AM
```

## <span data-ttu-id="43d34-189">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43d34-189">PARAMETERS</span></span>

### <span data-ttu-id="43d34-190">-AsUTC</span><span class="sxs-lookup"><span data-stu-id="43d34-190">-AsUTC</span></span>

<span data-ttu-id="43d34-191">Hiermee wordt de datum waarde geconverteerd naar de equivalente tijd in UTC.</span><span class="sxs-lookup"><span data-stu-id="43d34-191">Converts the date value to the equivalent time in UTC.</span></span>

<span data-ttu-id="43d34-192">Deze para meter is geïntroduceerd in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="43d34-192">This parameter was introduced in PowerShell 7.1.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43d34-193">-Datum</span><span class="sxs-lookup"><span data-stu-id="43d34-193">-Date</span></span>

<span data-ttu-id="43d34-194">Hiermee geeft u een datum en tijd op.</span><span class="sxs-lookup"><span data-stu-id="43d34-194">Specifies a date and time.</span></span> <span data-ttu-id="43d34-195">Tijd is optioneel en als deze niet is opgegeven, wordt 00:00:00 geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="43d34-195">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="43d34-196">Voer de datum en tijd in met een standaard indeling voor de systeem land instelling.</span><span class="sxs-lookup"><span data-stu-id="43d34-196">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="43d34-197">Bijvoorbeeld in Amerikaans Engels:</span><span class="sxs-lookup"><span data-stu-id="43d34-197">For example, in US English:</span></span>

<span data-ttu-id="43d34-198">`Get-Date -Date "6/25/2019 12:30:22"` retourneert dinsdag, 25 juni 2019 12:30:22</span><span class="sxs-lookup"><span data-stu-id="43d34-198">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

```yaml
Type: System.DateTime
Parameter Sets: DateAndFormat, DateAndUFormat
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="43d34-199">-Dag</span><span class="sxs-lookup"><span data-stu-id="43d34-199">-Day</span></span>

<span data-ttu-id="43d34-200">Hiermee geeft u de dag van de maand op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43d34-200">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="43d34-201">Voer een waarde in van 1 tot 31.</span><span class="sxs-lookup"><span data-stu-id="43d34-201">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="43d34-202">Als de opgegeven waarde groter is dan het aantal dagen in een maand, voegt Power shell het aantal dagen toe aan de maand.</span><span class="sxs-lookup"><span data-stu-id="43d34-202">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="43d34-203">Zo wordt bijvoorbeeld `Get-Date -Month 2 -Day 31` **3 maart** , niet **31 februari** , weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43d34-203">For example, `Get-Date -Month 2 -Day 31` displays **March 3** , not **February 31**.</span></span>

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

### <span data-ttu-id="43d34-204">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="43d34-204">-DisplayHint</span></span>

<span data-ttu-id="43d34-205">Hiermee wordt bepaald welke elementen van de datum en tijd worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43d34-205">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="43d34-206">De geaccepteerde waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="43d34-206">The accepted values are as follows:</span></span>

- <span data-ttu-id="43d34-207">**Datum** : alleen de datum wordt weer gegeven</span><span class="sxs-lookup"><span data-stu-id="43d34-207">**Date** : displays only the date</span></span>
- <span data-ttu-id="43d34-208">**Tijd** : alleen de tijd weer geven</span><span class="sxs-lookup"><span data-stu-id="43d34-208">**Time** : displays only the time</span></span>
- <span data-ttu-id="43d34-209">Datum **tijd** : hier worden de datums en tijden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="43d34-209">**DateTime** : displays the date and time</span></span>

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

### <span data-ttu-id="43d34-210">-Indeling</span><span class="sxs-lookup"><span data-stu-id="43d34-210">-Format</span></span>

<span data-ttu-id="43d34-211">Hier worden de datum en tijd weer gegeven in de Microsoft .NET Framework-indeling, zoals aangegeven in de indelings specificatie.</span><span class="sxs-lookup"><span data-stu-id="43d34-211">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="43d34-212">De **notatie** parameter voert een **teken reeks** object uit.</span><span class="sxs-lookup"><span data-stu-id="43d34-212">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="43d34-213">Zie [aangepaste datum-en tijd notatie reeksen](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)voor een lijst met beschik bare .net-indelings aanduidingen.</span><span class="sxs-lookup"><span data-stu-id="43d34-213">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="43d34-214">Wanneer de **notatie** para meter wordt gebruikt, worden `Get-Date` alleen de eigenschappen van het **DateTime** -object opgehaald die nodig zijn om de datum weer te geven.</span><span class="sxs-lookup"><span data-stu-id="43d34-214">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="43d34-215">Als gevolg hiervan zijn sommige eigenschappen en methoden van **DateTime** -objecten mogelijk niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="43d34-215">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="43d34-216">Vanaf Power shell 5,0 kunt u de volgende extra notaties gebruiken als waarden voor de **notatie** parameter.</span><span class="sxs-lookup"><span data-stu-id="43d34-216">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="43d34-217">**FileDate**.</span><span class="sxs-lookup"><span data-stu-id="43d34-217">**FileDate**.</span></span> <span data-ttu-id="43d34-218">Een bestands-of pad-gebruiks vriendelijke representatie van de huidige datum in de lokale tijd.</span><span class="sxs-lookup"><span data-stu-id="43d34-218">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="43d34-219">De notatie is `yyyyMMdd` (hoofdletter gevoelig, met een jaar van vier cijfers, een maand van 2 cijfers en een dag van 2 cijfers).</span><span class="sxs-lookup"><span data-stu-id="43d34-219">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="43d34-220">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="43d34-220">For example:</span></span>
  20190627.

- <span data-ttu-id="43d34-221">**FileDateUniversal**.</span><span class="sxs-lookup"><span data-stu-id="43d34-221">**FileDateUniversal**.</span></span> <span data-ttu-id="43d34-222">Een bestands-of pad-beschrijvende weer gave van de huidige datum in Universal Time (UTC).</span><span class="sxs-lookup"><span data-stu-id="43d34-222">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="43d34-223">De notatie is `yyyyMMddZ` (hoofdletter gevoelig, met een jaar van vier cijfers, een maand van 2 cijfers, een dag van 2 cijfers en de letter `Z` als de UTC-indicator).</span><span class="sxs-lookup"><span data-stu-id="43d34-223">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="43d34-224">Bijvoorbeeld: 20190627Z.</span><span class="sxs-lookup"><span data-stu-id="43d34-224">For example: 20190627Z.</span></span>

- <span data-ttu-id="43d34-225">**FileDateTime**.</span><span class="sxs-lookup"><span data-stu-id="43d34-225">**FileDateTime**.</span></span> <span data-ttu-id="43d34-226">Een bestands-of pad-gebruiks vriendelijke weer gave van de huidige datum en tijd in de lokale tijd, in 24-uurs notatie.</span><span class="sxs-lookup"><span data-stu-id="43d34-226">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="43d34-227">De notatie is `yyyyMMddTHHmmssffff` (hoofdletter gevoelig, met behulp van een jaar van vier cijfers, een maand van 2 cijfers, een dag van 2 cijfers, de letter als een tijd scheidings teken, een uur van twee cijfers, een minuut van twee cijfers en een `T` milliseconden van 4 cijfers).</span><span class="sxs-lookup"><span data-stu-id="43d34-227">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="43d34-228">Bijvoorbeeld: 20190627T0840107271.</span><span class="sxs-lookup"><span data-stu-id="43d34-228">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="43d34-229">**FileDateTimeUniversal**.</span><span class="sxs-lookup"><span data-stu-id="43d34-229">**FileDateTimeUniversal**.</span></span> <span data-ttu-id="43d34-230">Een bestands-of pad-gebruiks vriendelijke weer gave van de huidige datum en tijd in UTC (Universal Time), in 24-uurs notatie.</span><span class="sxs-lookup"><span data-stu-id="43d34-230">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="43d34-231">De notatie is `yyyyMMddTHHmmssffffZ` (hoofdletter gevoelig, met behulp van een jaar van vier cijfers, een maand van twee cijfers, de letter `T` als een tijd scheidings teken, een uur van twee cijfers, een minuut van twee cijfers, een tweede milliseconde en de letter `Z` als de UTC-indicator).</span><span class="sxs-lookup"><span data-stu-id="43d34-231">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="43d34-232">Bijvoorbeeld: 20190627T1540500718Z.</span><span class="sxs-lookup"><span data-stu-id="43d34-232">For example: 20190627T1540500718Z.</span></span>

```yaml
Type: System.String
Parameter Sets: DateAndFormat, UnixTimeSecondsAndFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43d34-233">-Uur</span><span class="sxs-lookup"><span data-stu-id="43d34-233">-Hour</span></span>

<span data-ttu-id="43d34-234">Hiermee geeft u het uur op dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43d34-234">Specifies the hour that is displayed.</span></span> <span data-ttu-id="43d34-235">Voer een waarde tussen 0 en 23 in.</span><span class="sxs-lookup"><span data-stu-id="43d34-235">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="43d34-236">-Milliseconde</span><span class="sxs-lookup"><span data-stu-id="43d34-236">-Millisecond</span></span>

<span data-ttu-id="43d34-237">Geeft de milliseconden in de datum aan.</span><span class="sxs-lookup"><span data-stu-id="43d34-237">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="43d34-238">Voer een waarde in tussen 0 en 999.</span><span class="sxs-lookup"><span data-stu-id="43d34-238">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="43d34-239">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="43d34-239">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="43d34-240">-Minuut</span><span class="sxs-lookup"><span data-stu-id="43d34-240">-Minute</span></span>

<span data-ttu-id="43d34-241">Hiermee geeft u de minuut op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43d34-241">Specifies the minute that is displayed.</span></span> <span data-ttu-id="43d34-242">Voer een waarde in tussen 0 en 59.</span><span class="sxs-lookup"><span data-stu-id="43d34-242">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="43d34-243">-Maand</span><span class="sxs-lookup"><span data-stu-id="43d34-243">-Month</span></span>

<span data-ttu-id="43d34-244">Hiermee geeft u de maand op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43d34-244">Specifies the month that is displayed.</span></span> <span data-ttu-id="43d34-245">Voer een waarde tussen 1 en 12 in.</span><span class="sxs-lookup"><span data-stu-id="43d34-245">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="43d34-246">-Seconde</span><span class="sxs-lookup"><span data-stu-id="43d34-246">-Second</span></span>

<span data-ttu-id="43d34-247">Hiermee geeft u de seconde op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43d34-247">Specifies the second that is displayed.</span></span> <span data-ttu-id="43d34-248">Voer een waarde in tussen 0 en 59.</span><span class="sxs-lookup"><span data-stu-id="43d34-248">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="43d34-249">-UFormat</span><span class="sxs-lookup"><span data-stu-id="43d34-249">-UFormat</span></span>

<span data-ttu-id="43d34-250">Hiermee worden de datum en tijd in de UNIX-indeling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43d34-250">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="43d34-251">De para meter **UFormat** voert een teken reeks object uit.</span><span class="sxs-lookup"><span data-stu-id="43d34-251">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="43d34-252">**UFormat** -aanduidingen worden voorafgegaan door een procent teken ( `%` ), bijvoorbeeld, `%m` , `%d` en `%Y` .</span><span class="sxs-lookup"><span data-stu-id="43d34-252">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="43d34-253">De sectie [notities](#notes) bevat een tabel met geldige **UFormat-aanduidingen**.</span><span class="sxs-lookup"><span data-stu-id="43d34-253">The [Notes](#notes) section contains a table of valid **UFormat specifiers**.</span></span>

<span data-ttu-id="43d34-254">Wanneer de para meter **UFormat** wordt gebruikt, worden `Get-Date` alleen de eigenschappen van het object **DateTime** opgehaald die nodig zijn om de datum weer te geven.</span><span class="sxs-lookup"><span data-stu-id="43d34-254">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="43d34-255">Als gevolg hiervan zijn sommige eigenschappen en methoden van **DateTime** -objecten mogelijk niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="43d34-255">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

```yaml
Type: System.String
Parameter Sets: DateAndUFormat, UnixTimeSecondsAndUFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43d34-256">-UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="43d34-256">-UnixTimeSeconds</span></span>

<span data-ttu-id="43d34-257">De datum en tijd weer gegeven in seconden sinds 1 januari 1970, 0:00:00.</span><span class="sxs-lookup"><span data-stu-id="43d34-257">Date and time represented in seconds since January 1, 1970, 0:00:00.</span></span>

<span data-ttu-id="43d34-258">Deze para meter is geïntroduceerd in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="43d34-258">This parameter was introduced in PowerShell 7.1.</span></span>

```yaml
Type: System.Int64
Parameter Sets: UnixTimeSecondsAndFormat, UnixTimeSecondsAndUFormat
Aliases: UnixTime

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43d34-259">-Jaar</span><span class="sxs-lookup"><span data-stu-id="43d34-259">-Year</span></span>

<span data-ttu-id="43d34-260">Hiermee geeft u het jaar op dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="43d34-260">Specifies the year that is displayed.</span></span> <span data-ttu-id="43d34-261">Voer een waarde in van 1 tot en met 9999.</span><span class="sxs-lookup"><span data-stu-id="43d34-261">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="43d34-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43d34-262">CommonParameters</span></span>

<span data-ttu-id="43d34-263">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="43d34-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43d34-264">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="43d34-264">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="43d34-265">INVOER</span><span class="sxs-lookup"><span data-stu-id="43d34-265">INPUTS</span></span>

### <span data-ttu-id="43d34-266">Pijplijn invoer</span><span class="sxs-lookup"><span data-stu-id="43d34-266">Pipeline input</span></span>

<span data-ttu-id="43d34-267">`Get-Date` accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="43d34-267">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="43d34-268">Bijvoorbeeld `Get-ChildItem | Get-Date`.</span><span class="sxs-lookup"><span data-stu-id="43d34-268">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="43d34-269">UITVOER</span><span class="sxs-lookup"><span data-stu-id="43d34-269">OUTPUTS</span></span>

### <span data-ttu-id="43d34-270">System. DateTime of System. String</span><span class="sxs-lookup"><span data-stu-id="43d34-270">System.DateTime or System.String</span></span>

<span data-ttu-id="43d34-271">`Get-Date` retourneert een **DateTime** -object, behalve wanneer de **notatie** -en **UFormat** -para meters worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="43d34-271">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="43d34-272">De **notatie** of para meters van de **UFormat** retour neren **teken reeks** objecten.</span><span class="sxs-lookup"><span data-stu-id="43d34-272">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="43d34-273">Wanneer een **DateTime** -object vanuit de pijp lijn naar een cmdlet wordt verzonden `Add-Content` , zoals de teken reeks invoer verwacht, converteert Power shell het object naar een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="43d34-273">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="43d34-274">Met de-methode wordt `(Get-Date).ToString()` een **DateTime** -object omgezet in een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="43d34-274">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="43d34-275">Als u de eigenschappen en methoden van een object wilt weer geven, verzendt u het object omlaag in de pijp lijn `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="43d34-275">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="43d34-276">Bijvoorbeeld `Get-Date | Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="43d34-276">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="43d34-277">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="43d34-277">NOTES</span></span>

<span data-ttu-id="43d34-278">**DateTime** -objecten hebben een lange datum en lange tijd notatie voor de systeem land instelling.</span><span class="sxs-lookup"><span data-stu-id="43d34-278">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="43d34-279">De geldige **UFormat-specificaties** worden weer gegeven in de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="43d34-279">The valid **UFormat specifiers** are displayed in the following table:</span></span>

| <span data-ttu-id="43d34-280">Indelings aanduiding</span><span class="sxs-lookup"><span data-stu-id="43d34-280">Format specifier</span></span> |                                 <span data-ttu-id="43d34-281">Betekenis</span><span class="sxs-lookup"><span data-stu-id="43d34-281">Meaning</span></span>                     |         <span data-ttu-id="43d34-282">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="43d34-282">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="43d34-283">Dag van de week-volledige naam</span><span class="sxs-lookup"><span data-stu-id="43d34-283">Day of the week - full name</span></span>                                             | <span data-ttu-id="43d34-284">Maandag</span><span class="sxs-lookup"><span data-stu-id="43d34-284">Monday</span></span>                   |
| `%a` | <span data-ttu-id="43d34-285">Dag van de week, korte naam</span><span class="sxs-lookup"><span data-stu-id="43d34-285">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="43d34-286">Ma</span><span class="sxs-lookup"><span data-stu-id="43d34-286">Mon</span></span>                      |
| `%B` | <span data-ttu-id="43d34-287">Maand naam-volledig</span><span class="sxs-lookup"><span data-stu-id="43d34-287">Month name - full</span></span>                                                       | <span data-ttu-id="43d34-288">Januari</span><span class="sxs-lookup"><span data-stu-id="43d34-288">January</span></span>                  |
| `%b` | <span data-ttu-id="43d34-289">Maand naam-afgekort</span><span class="sxs-lookup"><span data-stu-id="43d34-289">Month name - abbreviated</span></span>                                                | <span data-ttu-id="43d34-290">Jan</span><span class="sxs-lookup"><span data-stu-id="43d34-290">Jan</span></span>                      |
| `%C` | <span data-ttu-id="43d34-291">Jaar</span><span class="sxs-lookup"><span data-stu-id="43d34-291">Century</span></span>                                                                 | <span data-ttu-id="43d34-292">20 voor 2019</span><span class="sxs-lookup"><span data-stu-id="43d34-292">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="43d34-293">Datum en tijd-afgekort</span><span class="sxs-lookup"><span data-stu-id="43d34-293">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="43d34-294">Do jun 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="43d34-294">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="43d34-295">Datum in de notatie mm/dd/jj</span><span class="sxs-lookup"><span data-stu-id="43d34-295">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="43d34-296">06/27/19</span><span class="sxs-lookup"><span data-stu-id="43d34-296">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="43d34-297">Dag van de maand: 2 cijfers</span><span class="sxs-lookup"><span data-stu-id="43d34-297">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="43d34-298">05</span><span class="sxs-lookup"><span data-stu-id="43d34-298">05</span></span>                       |
| `%e` | <span data-ttu-id="43d34-299">Dag van de maand cijfer voorafgegaan door een spatie</span><span class="sxs-lookup"><span data-stu-id="43d34-299">Day of the month - digit preceded by a space</span></span>                            | <span data-ttu-id="43d34-300">\<space\>5,0</span><span class="sxs-lookup"><span data-stu-id="43d34-300">\<space\>5</span></span>               |
| `%F` | <span data-ttu-id="43d34-301">Datum in de notatie JJJJ-MM-DD, gelijk aan% Y-% m-% d (ISO 8601-datum notatie)</span><span class="sxs-lookup"><span data-stu-id="43d34-301">Date in YYYY-mm-dd format, equal to %Y-%m-%d (the ISO 8601 date format)</span></span> | <span data-ttu-id="43d34-302">2019-06-27</span><span class="sxs-lookup"><span data-stu-id="43d34-302">2019-06-27</span></span>               |
| `%G` | <span data-ttu-id="43d34-303">Hetzelfde als ' Y '</span><span class="sxs-lookup"><span data-stu-id="43d34-303">Same as 'Y'</span></span>                                                             |                          |
| `%g` | <span data-ttu-id="43d34-304">Hetzelfde als ' y '</span><span class="sxs-lookup"><span data-stu-id="43d34-304">Same as 'y'</span></span>                                                             |                          |
| `%H` | <span data-ttu-id="43d34-305">Uur in 24-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="43d34-305">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="43d34-306">17</span><span class="sxs-lookup"><span data-stu-id="43d34-306">17</span></span>                       |
| `%h` | <span data-ttu-id="43d34-307">Hetzelfde als ' b '</span><span class="sxs-lookup"><span data-stu-id="43d34-307">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="43d34-308">Uur in 12-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="43d34-308">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="43d34-309">05</span><span class="sxs-lookup"><span data-stu-id="43d34-309">05</span></span>                       |
| `%j` | <span data-ttu-id="43d34-310">Dag van het jaar</span><span class="sxs-lookup"><span data-stu-id="43d34-310">Day of the year</span></span>                                                         | <span data-ttu-id="43d34-311">1-366</span><span class="sxs-lookup"><span data-stu-id="43d34-311">1-366</span></span>                    |
| `%k` | <span data-ttu-id="43d34-312">Hetzelfde als ' H '</span><span class="sxs-lookup"><span data-stu-id="43d34-312">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="43d34-313">Hetzelfde als ' I ' (hoofd letters I)</span><span class="sxs-lookup"><span data-stu-id="43d34-313">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="43d34-314">05</span><span class="sxs-lookup"><span data-stu-id="43d34-314">05</span></span>                       |
| `%M` | <span data-ttu-id="43d34-315">Minuten</span><span class="sxs-lookup"><span data-stu-id="43d34-315">Minutes</span></span>                                                                 | <span data-ttu-id="43d34-316">35</span><span class="sxs-lookup"><span data-stu-id="43d34-316">35</span></span>                       |
| `%m` | <span data-ttu-id="43d34-317">Maandnummer</span><span class="sxs-lookup"><span data-stu-id="43d34-317">Month number</span></span>                                                            | <span data-ttu-id="43d34-318">06</span><span class="sxs-lookup"><span data-stu-id="43d34-318">06</span></span>                       |
| `%n` | <span data-ttu-id="43d34-319">teken voor nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="43d34-319">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="43d34-320">AM of PM</span><span class="sxs-lookup"><span data-stu-id="43d34-320">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="43d34-321">Tijd in 24-uurs notatie-geen seconden</span><span class="sxs-lookup"><span data-stu-id="43d34-321">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="43d34-322">17:45</span><span class="sxs-lookup"><span data-stu-id="43d34-322">17:45</span></span>                    |
| `%r` | <span data-ttu-id="43d34-323">Tijd in 12-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="43d34-323">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="43d34-324">09:15:36 UUR</span><span class="sxs-lookup"><span data-stu-id="43d34-324">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="43d34-325">Seconden</span><span class="sxs-lookup"><span data-stu-id="43d34-325">Seconds</span></span>                                                                 | <span data-ttu-id="43d34-326">05</span><span class="sxs-lookup"><span data-stu-id="43d34-326">05</span></span>                       |
| `%s` | <span data-ttu-id="43d34-327">Seconden verstreken sinds 1 januari 1970 00:00:00</span><span class="sxs-lookup"><span data-stu-id="43d34-327">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="43d34-328">1150451174</span><span class="sxs-lookup"><span data-stu-id="43d34-328">1150451174</span></span>               |
| `%t` | <span data-ttu-id="43d34-329">Teken voor horizontale tab</span><span class="sxs-lookup"><span data-stu-id="43d34-329">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="43d34-330">Tijd in 24-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="43d34-330">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="43d34-331">17:45:52</span><span class="sxs-lookup"><span data-stu-id="43d34-331">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="43d34-332">Hetzelfde als ' W '</span><span class="sxs-lookup"><span data-stu-id="43d34-332">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="43d34-333">Dag van het week nummer</span><span class="sxs-lookup"><span data-stu-id="43d34-333">Day of the week - number</span></span>                                                | <span data-ttu-id="43d34-334">Zondag = 0</span><span class="sxs-lookup"><span data-stu-id="43d34-334">Sunday = 0</span></span>               |
| `%V` | <span data-ttu-id="43d34-335">Week van het jaar</span><span class="sxs-lookup"><span data-stu-id="43d34-335">Week of the year</span></span>                                                        | <span data-ttu-id="43d34-336">01-53</span><span class="sxs-lookup"><span data-stu-id="43d34-336">01-53</span></span>                    |
| `%w` | <span data-ttu-id="43d34-337">Hetzelfde als ' u '</span><span class="sxs-lookup"><span data-stu-id="43d34-337">Same as 'u'</span></span>                                                             |                          |
| `%W` | <span data-ttu-id="43d34-338">Week van het jaar</span><span class="sxs-lookup"><span data-stu-id="43d34-338">Week of the year</span></span>                                                        | <span data-ttu-id="43d34-339">00-52</span><span class="sxs-lookup"><span data-stu-id="43d34-339">00-52</span></span>                    |
| `%X` | <span data-ttu-id="43d34-340">Hetzelfde als 'T '</span><span class="sxs-lookup"><span data-stu-id="43d34-340">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="43d34-341">Datum in de standaard notatie voor de land instelling</span><span class="sxs-lookup"><span data-stu-id="43d34-341">Date in standard format for locale</span></span>                                      | <span data-ttu-id="43d34-342">06/27/19 voor Engels-US</span><span class="sxs-lookup"><span data-stu-id="43d34-342">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="43d34-343">Jaar met viercijferige notatie</span><span class="sxs-lookup"><span data-stu-id="43d34-343">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="43d34-344">2019</span><span class="sxs-lookup"><span data-stu-id="43d34-344">2019</span></span>                     |
| `%y` | <span data-ttu-id="43d34-345">Jaar met een notatie van twee cijfers</span><span class="sxs-lookup"><span data-stu-id="43d34-345">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="43d34-346">19</span><span class="sxs-lookup"><span data-stu-id="43d34-346">19</span></span>                       |
| `%Z` | <span data-ttu-id="43d34-347">Tijd zone-offset van Universal Time Coordinate (UTC)</span><span class="sxs-lookup"><span data-stu-id="43d34-347">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="43d34-348">-07</span><span class="sxs-lookup"><span data-stu-id="43d34-348">-07</span></span>                      |

## <span data-ttu-id="43d34-349">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="43d34-349">RELATED LINKS</span></span>

[<span data-ttu-id="43d34-350">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="43d34-350">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="43d34-351">Get-cultuur</span><span class="sxs-lookup"><span data-stu-id="43d34-351">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="43d34-352">Get-member</span><span class="sxs-lookup"><span data-stu-id="43d34-352">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="43d34-353">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="43d34-353">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="43d34-354">Nieuw-time span</span><span class="sxs-lookup"><span data-stu-id="43d34-354">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="43d34-355">Set-date</span><span class="sxs-lookup"><span data-stu-id="43d34-355">Set-Date</span></span>](Set-Date.md)
