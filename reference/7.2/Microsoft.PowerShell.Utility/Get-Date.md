---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: bb3c3686310440d9f75d36ca1c83fb60066f5d6a
ms.sourcegitcommit: 925819a5ad5799650c14944bd3e50fb309a7e6c4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/11/2021
ms.locfileid: "102771493"
---
# <span data-ttu-id="5385d-102">Get-Date</span><span class="sxs-lookup"><span data-stu-id="5385d-102">Get-Date</span></span>

## <span data-ttu-id="5385d-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5385d-103">SYNOPSIS</span></span>
<span data-ttu-id="5385d-104">Hiermee worden de huidige datum en tijd opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5385d-104">Gets the current date and time.</span></span>

## <span data-ttu-id="5385d-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5385d-105">SYNTAX</span></span>

### <span data-ttu-id="5385d-106">Datum (standaard)</span><span class="sxs-lookup"><span data-stu-id="5385d-106">Date (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="5385d-107">DateUFormat</span><span class="sxs-lookup"><span data-stu-id="5385d-107">DateUFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### <span data-ttu-id="5385d-108">UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="5385d-108">UnixTimeSeconds</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="5385d-109">UnixTimeSecondsUFormat</span><span class="sxs-lookup"><span data-stu-id="5385d-109">UnixTimeSecondsUFormat</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## <span data-ttu-id="5385d-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5385d-110">DESCRIPTION</span></span>

<span data-ttu-id="5385d-111">De `Get-Date` cmdlet haalt een **DateTime** -object op dat staat voor de huidige datum of een datum die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="5385d-111">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="5385d-112">`Get-Date` de datum en tijd in verschillende .NET-en UNIX-indelingen kunnen worden ingedeeld.</span><span class="sxs-lookup"><span data-stu-id="5385d-112">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="5385d-113">U kunt gebruiken `Get-Date` voor het genereren van een teken reeks voor datum of tijd en vervolgens de teken reeks verzenden naar andere cmdlets of Program ma's.</span><span class="sxs-lookup"><span data-stu-id="5385d-113">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="5385d-114">`Get-Date` gebruikt de instellingen van de computer cultuur om te bepalen hoe de uitvoer wordt geformatteerd.</span><span class="sxs-lookup"><span data-stu-id="5385d-114">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="5385d-115">Gebruik om de instellingen van uw computer weer te geven `(Get-Culture).DateTimeFormat` .</span><span class="sxs-lookup"><span data-stu-id="5385d-115">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="5385d-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5385d-116">EXAMPLES</span></span>

### <span data-ttu-id="5385d-117">Voor beeld 1: de huidige datum en tijd ophalen</span><span class="sxs-lookup"><span data-stu-id="5385d-117">Example 1: Get the current date and time</span></span>

<span data-ttu-id="5385d-118">In dit voor beeld `Get-Date` worden de huidige systeem datum en-tijd weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5385d-118">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="5385d-119">De uitvoer bevindt zich in de notatie voor lange en lange tijd.</span><span class="sxs-lookup"><span data-stu-id="5385d-119">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="5385d-120">Voor beeld 2: elementen van de huidige datum en tijd ophalen</span><span class="sxs-lookup"><span data-stu-id="5385d-120">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="5385d-121">In dit voor beeld ziet u hoe u kunt gebruiken `Get-Date` om het datum-of tijd-element op te halen.</span><span class="sxs-lookup"><span data-stu-id="5385d-121">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="5385d-122">De para meter gebruikt de argumenten **datum**, **tijd** of **datum/** tijd.</span><span class="sxs-lookup"><span data-stu-id="5385d-122">The parameter uses the arguments **Date**, **Time**, or **DateTime**.</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="5385d-123">`Get-Date` gebruikt de para meter **DisplayHint** met het **datum** argument om alleen de datum op te halen.</span><span class="sxs-lookup"><span data-stu-id="5385d-123">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="5385d-124">Voor beeld 3: de datum en tijd ophalen met een specificatie van .NET-indeling</span><span class="sxs-lookup"><span data-stu-id="5385d-124">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="5385d-125">In dit voor beeld wordt een .NET-indelings specificatie gebruikt om de indeling van de uitvoer aan te passen.</span><span class="sxs-lookup"><span data-stu-id="5385d-125">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="5385d-126">De uitvoer is een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="5385d-126">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="5385d-127">`Get-Date` gebruikt de **indelings** parameter om verschillende indelings aanduidingen op te geven.</span><span class="sxs-lookup"><span data-stu-id="5385d-127">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="5385d-128">De .NET-indelings specificaties die in dit voor beeld worden gebruikt, zijn als volgt gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="5385d-128">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="5385d-129">Aanduiding</span><span class="sxs-lookup"><span data-stu-id="5385d-129">Specifier</span></span> |                      <span data-ttu-id="5385d-130">Definitie</span><span class="sxs-lookup"><span data-stu-id="5385d-130">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | <span data-ttu-id="5385d-131">Dag van de week-volledige naam</span><span class="sxs-lookup"><span data-stu-id="5385d-131">Day of the week - full name</span></span>                           |
| `MM`      | <span data-ttu-id="5385d-132">Maandnummer</span><span class="sxs-lookup"><span data-stu-id="5385d-132">Month number</span></span>                                          |
| `dd`      | <span data-ttu-id="5385d-133">Dag van de maand: 2 cijfers</span><span class="sxs-lookup"><span data-stu-id="5385d-133">Day of the month - 2 digits</span></span>                           |
| `yyyy`    | <span data-ttu-id="5385d-134">Jaar met viercijferige notatie</span><span class="sxs-lookup"><span data-stu-id="5385d-134">Year in 4-digit format</span></span>                                |
| `HH:mm`   | <span data-ttu-id="5385d-135">Tijd in 24-uurs notatie-geen seconden</span><span class="sxs-lookup"><span data-stu-id="5385d-135">Time in 24-hour format - no seconds</span></span>                    |
| `K`       | <span data-ttu-id="5385d-136">Tijd zone-offset van Universal Time Coordinate (UTC)</span><span class="sxs-lookup"><span data-stu-id="5385d-136">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="5385d-137">Zie [aangepaste datum-en tijd notatie reeksen](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)voor meer informatie over .net-indelings specificaties.</span><span class="sxs-lookup"><span data-stu-id="5385d-137">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="5385d-138">Voor beeld 4: de datum en tijd ophalen met een UFormat-aanduiding</span><span class="sxs-lookup"><span data-stu-id="5385d-138">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="5385d-139">In dit voor beeld worden verschillende **UFormat** -indelings specificaties gebruikt voor het aanpassen van de indeling van de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="5385d-139">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="5385d-140">De uitvoer is een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="5385d-140">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="5385d-141">`Get-Date` maakt gebruik van de para meter **UFormat** om verschillende indelings specificaties op te geven.</span><span class="sxs-lookup"><span data-stu-id="5385d-141">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="5385d-142">De **UFormat** -indelings specificaties die in dit voor beeld worden gebruikt, zijn als volgt gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="5385d-142">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="5385d-143">Aanduiding</span><span class="sxs-lookup"><span data-stu-id="5385d-143">Specifier</span></span> |                      <span data-ttu-id="5385d-144">Definitie</span><span class="sxs-lookup"><span data-stu-id="5385d-144">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `%A`      | <span data-ttu-id="5385d-145">Dag van de week-volledige naam</span><span class="sxs-lookup"><span data-stu-id="5385d-145">Day of the week - full name</span></span>                           |
| `%m`      | <span data-ttu-id="5385d-146">Maandnummer</span><span class="sxs-lookup"><span data-stu-id="5385d-146">Month number</span></span>                                          |
| `%d`      | <span data-ttu-id="5385d-147">Dag van de maand: 2 cijfers</span><span class="sxs-lookup"><span data-stu-id="5385d-147">Day of the month - 2 digits</span></span>                           |
| `%Y`      | <span data-ttu-id="5385d-148">Jaar met viercijferige notatie</span><span class="sxs-lookup"><span data-stu-id="5385d-148">Year in 4-digit format</span></span>                                |
| `%R`      | <span data-ttu-id="5385d-149">Tijd in 24-uurs notatie-geen seconden</span><span class="sxs-lookup"><span data-stu-id="5385d-149">Time in 24-hour format - no seconds</span></span>                    |
| `%Z`      | <span data-ttu-id="5385d-150">Tijd zone-offset van Universal Time Coordinate (UTC)</span><span class="sxs-lookup"><span data-stu-id="5385d-150">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="5385d-151">Zie de sectie [opmerkingen](#notes) voor een lijst met geldige indelings specificaties voor **UFormat** .</span><span class="sxs-lookup"><span data-stu-id="5385d-151">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="5385d-152">Voor beeld 5: de dag van een datum van het jaar ophalen</span><span class="sxs-lookup"><span data-stu-id="5385d-152">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="5385d-153">In dit voor beeld wordt een eigenschap gebruikt om de numerieke dag van het jaar op te halen.</span><span class="sxs-lookup"><span data-stu-id="5385d-153">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="5385d-154">De Gregoriaanse kalender heeft 365 dagen, met uitzonde ring van schrikkel jaren die 366 dagen lang zijn.</span><span class="sxs-lookup"><span data-stu-id="5385d-154">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="5385d-155">Zo is 31 december 2020 dag 366.</span><span class="sxs-lookup"><span data-stu-id="5385d-155">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="5385d-156">`Get-Date` gebruikt drie para meters om de datum op te geven: **jaar**, **maand** en **dag**.</span><span class="sxs-lookup"><span data-stu-id="5385d-156">`Get-Date` uses three parameters to specify the date: **Year**, **Month**, and **Day**.</span></span> <span data-ttu-id="5385d-157">De opdracht wordt verpakt met haakjes zodat het resultaat door de eigenschap **DAYOFYEAR** wordt geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="5385d-157">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="5385d-158">Voor beeld 6: controleren of een datum is aangepast aan zomer tijd</span><span class="sxs-lookup"><span data-stu-id="5385d-158">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="5385d-159">In dit voor beeld wordt een Booleaanse methode gebruikt om te controleren of een datum wordt gecorrigeerd met zomer tijd.</span><span class="sxs-lookup"><span data-stu-id="5385d-159">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="5385d-160">Een variabele, `$DST` slaat het resultaat van op `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="5385d-160">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="5385d-161">`$DST` maakt gebruik van de methode **IsDaylightSavingTime** om te testen of de datum wordt aangepast aan zomer tijd.</span><span class="sxs-lookup"><span data-stu-id="5385d-161">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="5385d-162">Voor beeld 7: de huidige tijd converteren naar UTC-tijd</span><span class="sxs-lookup"><span data-stu-id="5385d-162">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="5385d-163">In dit voor beeld wordt de huidige tijd geconverteerd naar UTC-tijd.</span><span class="sxs-lookup"><span data-stu-id="5385d-163">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="5385d-164">De UTC-offset voor de land instelling van het systeem wordt gebruikt om de tijd om te zetten.</span><span class="sxs-lookup"><span data-stu-id="5385d-164">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="5385d-165">Een tabel in de sectie [notities](#notes) bevat een lijst met geldige indelings specificaties voor **UFormat** .</span><span class="sxs-lookup"><span data-stu-id="5385d-165">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="5385d-166">`Get-Date` maakt gebruik van de para meter **UFormat** met indelings specificaties om de huidige systeem datum en-tijd weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5385d-166">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="5385d-167">De indelings aanduiding **% Z** vertegenwoordigt de UTC-afwijking van **-07**.</span><span class="sxs-lookup"><span data-stu-id="5385d-167">The format specifier **%Z** represents the UTC offset of **-07**.</span></span>

<span data-ttu-id="5385d-168">De `$Time` variabele bevat de huidige systeem datum en-tijd.</span><span class="sxs-lookup"><span data-stu-id="5385d-168">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="5385d-169">`$Time` maakt gebruik van de methode **ToUniversalTime ()** om de tijd om te zetten op basis van de UTC-afwijking van de computer.</span><span class="sxs-lookup"><span data-stu-id="5385d-169">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="5385d-170">Voor beeld 8: een tijds tempel maken</span><span class="sxs-lookup"><span data-stu-id="5385d-170">Example 8: Create a timestamp</span></span>

<span data-ttu-id="5385d-171">In dit voor beeld maakt een indelings aanduiding een **teken reeks** object voor een tijds tempel voor een directory naam.</span><span class="sxs-lookup"><span data-stu-id="5385d-171">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="5385d-172">De tijds tempel bevat de datum, tijd en UTC-offset.</span><span class="sxs-lookup"><span data-stu-id="5385d-172">The timestamp includes the date, time, and UTC offset.</span></span>

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

<span data-ttu-id="5385d-173">De `$timestamp` variabele bevat de resultaten van een `Get-Date` opdracht.</span><span class="sxs-lookup"><span data-stu-id="5385d-173">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="5385d-174">`Get-Date` gebruikt de **indelings** parameter met de indelings specificatie van kleine letters `o` om een **teken reeks** object voor een tijds tempel te maken.</span><span class="sxs-lookup"><span data-stu-id="5385d-174">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="5385d-175">Het object wordt naar de pijp lijn verzonden `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="5385d-175">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="5385d-176">Een **script Block** bevat de `$_` variabele die het huidige pijplijn object vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="5385d-176">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="5385d-177">De tijds tempel teken reeks wordt gescheiden door dubbele punten die worden vervangen door punten.</span><span class="sxs-lookup"><span data-stu-id="5385d-177">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="5385d-178">`New-Item` gebruikt de para meter **Path** om de locatie voor een nieuwe map op te geven.</span><span class="sxs-lookup"><span data-stu-id="5385d-178">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="5385d-179">Het pad bevat de `$timestamp` variabele als de mapnaam.</span><span class="sxs-lookup"><span data-stu-id="5385d-179">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="5385d-180">De **type** parameter geeft aan dat er een map is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="5385d-180">The **Type** parameter specifies that a directory is created.</span></span>

### <span data-ttu-id="5385d-181">Voor beeld 9: een Unix-Time Stamp converteren</span><span class="sxs-lookup"><span data-stu-id="5385d-181">Example 9: Convert a Unix timestamp</span></span>

<span data-ttu-id="5385d-182">In dit voor beeld wordt een Unix-tijd (vertegenwoordigd door het aantal seconden sinds 1970-01-01 0:00:00) geconverteerd naar DateTime.</span><span class="sxs-lookup"><span data-stu-id="5385d-182">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### <span data-ttu-id="5385d-183">Voor beeld 10: een datum waarde Retour neren die als UTC wordt geïnterpreteerd</span><span class="sxs-lookup"><span data-stu-id="5385d-183">Example 10: Return a date value interpreted as UTC</span></span>

<span data-ttu-id="5385d-184">In dit voor beeld ziet u hoe u een datum waarde als UTC-equivalent kunt interpreteren.</span><span class="sxs-lookup"><span data-stu-id="5385d-184">This example shows how to interpret a date value as its UTC equivalent.</span></span> <span data-ttu-id="5385d-185">Voor dit voor beeld is deze computer ingesteld op **Pacific Standard Time**.</span><span class="sxs-lookup"><span data-stu-id="5385d-185">For the example, this machine is set to **Pacific Standard Time**.</span></span> <span data-ttu-id="5385d-186">Standaard worden `Get-Date` waarden voor die tijd zone geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5385d-186">By default, `Get-Date` returns values for that timezone.</span></span> <span data-ttu-id="5385d-187">Gebruik de para meter **AsUTC** om de waarde te converteren naar de EQUIVALENTe UTC-tijd.</span><span class="sxs-lookup"><span data-stu-id="5385d-187">Use the **AsUTC** parameter to convert the value to the UTC equivalent time.</span></span>

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

## <span data-ttu-id="5385d-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5385d-188">PARAMETERS</span></span>

### <span data-ttu-id="5385d-189">-AsUTC</span><span class="sxs-lookup"><span data-stu-id="5385d-189">-AsUTC</span></span>

<span data-ttu-id="5385d-190">Hiermee wordt de datum waarde geconverteerd naar de equivalente tijd in UTC.</span><span class="sxs-lookup"><span data-stu-id="5385d-190">Converts the date value to the equivalent time in UTC.</span></span>

<span data-ttu-id="5385d-191">Deze para meter is geïntroduceerd in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="5385d-191">This parameter was introduced in PowerShell 7.1.</span></span>

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

### <span data-ttu-id="5385d-192">-Datum</span><span class="sxs-lookup"><span data-stu-id="5385d-192">-Date</span></span>

<span data-ttu-id="5385d-193">Hiermee geeft u een datum en tijd op.</span><span class="sxs-lookup"><span data-stu-id="5385d-193">Specifies a date and time.</span></span> <span data-ttu-id="5385d-194">Tijd is optioneel en als deze niet is opgegeven, wordt 00:00:00 geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5385d-194">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="5385d-195">Voer de datum en tijd in met een standaard indeling voor de systeem land instelling.</span><span class="sxs-lookup"><span data-stu-id="5385d-195">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="5385d-196">Bijvoorbeeld in Amerikaans Engels:</span><span class="sxs-lookup"><span data-stu-id="5385d-196">For example, in US English:</span></span>

<span data-ttu-id="5385d-197">`Get-Date -Date "6/25/2019 12:30:22"` retourneert dinsdag, 25 juni 2019 12:30:22</span><span class="sxs-lookup"><span data-stu-id="5385d-197">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

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

### <span data-ttu-id="5385d-198">-Dag</span><span class="sxs-lookup"><span data-stu-id="5385d-198">-Day</span></span>

<span data-ttu-id="5385d-199">Hiermee geeft u de dag van de maand op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5385d-199">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="5385d-200">Voer een waarde in van 1 tot 31.</span><span class="sxs-lookup"><span data-stu-id="5385d-200">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="5385d-201">Als de opgegeven waarde groter is dan het aantal dagen in een maand, voegt Power shell het aantal dagen toe aan de maand.</span><span class="sxs-lookup"><span data-stu-id="5385d-201">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="5385d-202">Zo wordt bijvoorbeeld `Get-Date -Month 2 -Day 31` **3 maart**, niet **31 februari**, weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5385d-202">For example, `Get-Date -Month 2 -Day 31` displays **March 3**, not **February 31**.</span></span>

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

### <span data-ttu-id="5385d-203">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="5385d-203">-DisplayHint</span></span>

<span data-ttu-id="5385d-204">Hiermee wordt bepaald welke elementen van de datum en tijd worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5385d-204">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="5385d-205">De geaccepteerde waarden zijn als volgt:</span><span class="sxs-lookup"><span data-stu-id="5385d-205">The accepted values are as follows:</span></span>

- <span data-ttu-id="5385d-206">**Datum**: alleen de datum wordt weer gegeven</span><span class="sxs-lookup"><span data-stu-id="5385d-206">**Date**: displays only the date</span></span>
- <span data-ttu-id="5385d-207">**Tijd**: alleen de tijd weer geven</span><span class="sxs-lookup"><span data-stu-id="5385d-207">**Time**: displays only the time</span></span>
- <span data-ttu-id="5385d-208">Datum **tijd**: hier worden de datums en tijden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="5385d-208">**DateTime**: displays the date and time</span></span>

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

### <span data-ttu-id="5385d-209">-Indeling</span><span class="sxs-lookup"><span data-stu-id="5385d-209">-Format</span></span>

<span data-ttu-id="5385d-210">Hier worden de datum en tijd weer gegeven in de Microsoft .NET Framework-indeling, zoals aangegeven in de indelings specificatie.</span><span class="sxs-lookup"><span data-stu-id="5385d-210">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="5385d-211">De **notatie** parameter voert een **teken reeks** object uit.</span><span class="sxs-lookup"><span data-stu-id="5385d-211">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="5385d-212">Zie [aangepaste datum-en tijd notatie reeksen](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)voor een lijst met beschik bare .net-indelings aanduidingen.</span><span class="sxs-lookup"><span data-stu-id="5385d-212">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="5385d-213">Wanneer de **notatie** para meter wordt gebruikt, worden `Get-Date` alleen de eigenschappen van het **DateTime** -object opgehaald die nodig zijn om de datum weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5385d-213">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="5385d-214">Als gevolg hiervan zijn sommige eigenschappen en methoden van **DateTime** -objecten mogelijk niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="5385d-214">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="5385d-215">Vanaf Power shell 5,0 kunt u de volgende extra notaties gebruiken als waarden voor de **notatie** parameter.</span><span class="sxs-lookup"><span data-stu-id="5385d-215">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="5385d-216">**FileDate**.</span><span class="sxs-lookup"><span data-stu-id="5385d-216">**FileDate**.</span></span> <span data-ttu-id="5385d-217">Een bestands-of pad-gebruiks vriendelijke representatie van de huidige datum in de lokale tijd.</span><span class="sxs-lookup"><span data-stu-id="5385d-217">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="5385d-218">De notatie is `yyyyMMdd` (hoofdletter gevoelig, met een jaar van vier cijfers, een maand van 2 cijfers en een dag van 2 cijfers).</span><span class="sxs-lookup"><span data-stu-id="5385d-218">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="5385d-219">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="5385d-219">For example:</span></span>
  20190627.

- <span data-ttu-id="5385d-220">**FileDateUniversal**.</span><span class="sxs-lookup"><span data-stu-id="5385d-220">**FileDateUniversal**.</span></span> <span data-ttu-id="5385d-221">Een bestands-of pad-beschrijvende weer gave van de huidige datum in Universal Time (UTC).</span><span class="sxs-lookup"><span data-stu-id="5385d-221">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="5385d-222">De notatie is `yyyyMMddZ` (hoofdletter gevoelig, met een jaar van vier cijfers, een maand van 2 cijfers, een dag van 2 cijfers en de letter `Z` als de UTC-indicator).</span><span class="sxs-lookup"><span data-stu-id="5385d-222">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="5385d-223">Bijvoorbeeld: 20190627Z.</span><span class="sxs-lookup"><span data-stu-id="5385d-223">For example: 20190627Z.</span></span>

- <span data-ttu-id="5385d-224">**FileDateTime**.</span><span class="sxs-lookup"><span data-stu-id="5385d-224">**FileDateTime**.</span></span> <span data-ttu-id="5385d-225">Een bestands-of pad-gebruiks vriendelijke weer gave van de huidige datum en tijd in de lokale tijd, in 24-uurs notatie.</span><span class="sxs-lookup"><span data-stu-id="5385d-225">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="5385d-226">De notatie is `yyyyMMddTHHmmssffff` (hoofdletter gevoelig, met behulp van een jaar van vier cijfers, een maand van 2 cijfers, een dag van 2 cijfers, de letter als een tijd scheidings teken, een uur van twee cijfers, een minuut van twee cijfers en een `T` milliseconden van 4 cijfers).</span><span class="sxs-lookup"><span data-stu-id="5385d-226">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="5385d-227">Bijvoorbeeld: 20190627T0840107271.</span><span class="sxs-lookup"><span data-stu-id="5385d-227">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="5385d-228">**FileDateTimeUniversal**.</span><span class="sxs-lookup"><span data-stu-id="5385d-228">**FileDateTimeUniversal**.</span></span> <span data-ttu-id="5385d-229">Een bestands-of pad-gebruiks vriendelijke weer gave van de huidige datum en tijd in UTC (Universal Time), in 24-uurs notatie.</span><span class="sxs-lookup"><span data-stu-id="5385d-229">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="5385d-230">De notatie is `yyyyMMddTHHmmssffffZ` (hoofdletter gevoelig, met behulp van een jaar van vier cijfers, een maand van twee cijfers, de letter `T` als een tijd scheidings teken, een uur van twee cijfers, een minuut van twee cijfers, een tweede milliseconde en de letter `Z` als de UTC-indicator).</span><span class="sxs-lookup"><span data-stu-id="5385d-230">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="5385d-231">Bijvoorbeeld: 20190627T1540500718Z.</span><span class="sxs-lookup"><span data-stu-id="5385d-231">For example: 20190627T1540500718Z.</span></span>

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

### <span data-ttu-id="5385d-232">-Uur</span><span class="sxs-lookup"><span data-stu-id="5385d-232">-Hour</span></span>

<span data-ttu-id="5385d-233">Hiermee geeft u het uur op dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5385d-233">Specifies the hour that is displayed.</span></span> <span data-ttu-id="5385d-234">Voer een waarde tussen 0 en 23 in.</span><span class="sxs-lookup"><span data-stu-id="5385d-234">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="5385d-235">-Milliseconde</span><span class="sxs-lookup"><span data-stu-id="5385d-235">-Millisecond</span></span>

<span data-ttu-id="5385d-236">Geeft de milliseconden in de datum aan.</span><span class="sxs-lookup"><span data-stu-id="5385d-236">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="5385d-237">Voer een waarde in tussen 0 en 999.</span><span class="sxs-lookup"><span data-stu-id="5385d-237">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="5385d-238">Deze para meter is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5385d-238">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5385d-239">-Minuut</span><span class="sxs-lookup"><span data-stu-id="5385d-239">-Minute</span></span>

<span data-ttu-id="5385d-240">Hiermee geeft u de minuut op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5385d-240">Specifies the minute that is displayed.</span></span> <span data-ttu-id="5385d-241">Voer een waarde in tussen 0 en 59.</span><span class="sxs-lookup"><span data-stu-id="5385d-241">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="5385d-242">-Maand</span><span class="sxs-lookup"><span data-stu-id="5385d-242">-Month</span></span>

<span data-ttu-id="5385d-243">Hiermee geeft u de maand op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5385d-243">Specifies the month that is displayed.</span></span> <span data-ttu-id="5385d-244">Voer een waarde tussen 1 en 12 in.</span><span class="sxs-lookup"><span data-stu-id="5385d-244">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="5385d-245">-Seconde</span><span class="sxs-lookup"><span data-stu-id="5385d-245">-Second</span></span>

<span data-ttu-id="5385d-246">Hiermee geeft u de seconde op die wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5385d-246">Specifies the second that is displayed.</span></span> <span data-ttu-id="5385d-247">Voer een waarde in tussen 0 en 59.</span><span class="sxs-lookup"><span data-stu-id="5385d-247">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="5385d-248">-UFormat</span><span class="sxs-lookup"><span data-stu-id="5385d-248">-UFormat</span></span>

<span data-ttu-id="5385d-249">Hiermee worden de datum en tijd in de UNIX-indeling weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5385d-249">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="5385d-250">De para meter **UFormat** voert een teken reeks object uit.</span><span class="sxs-lookup"><span data-stu-id="5385d-250">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="5385d-251">**UFormat** -aanduidingen worden voorafgegaan door een procent teken ( `%` ), bijvoorbeeld, `%m` , `%d` en `%Y` .</span><span class="sxs-lookup"><span data-stu-id="5385d-251">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="5385d-252">De sectie [notities](#notes) bevat een tabel met geldige **UFormat-aanduidingen**.</span><span class="sxs-lookup"><span data-stu-id="5385d-252">The [Notes](#notes) section contains a table of valid **UFormat specifiers**.</span></span>

<span data-ttu-id="5385d-253">Wanneer de para meter **UFormat** wordt gebruikt, worden `Get-Date` alleen de eigenschappen van het object **DateTime** opgehaald die nodig zijn om de datum weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5385d-253">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="5385d-254">Als gevolg hiervan zijn sommige eigenschappen en methoden van **DateTime** -objecten mogelijk niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="5385d-254">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

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

### <span data-ttu-id="5385d-255">-UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="5385d-255">-UnixTimeSeconds</span></span>

<span data-ttu-id="5385d-256">De datum en tijd weer gegeven in seconden sinds 1 januari 1970, 0:00:00.</span><span class="sxs-lookup"><span data-stu-id="5385d-256">Date and time represented in seconds since January 1, 1970, 0:00:00.</span></span>

<span data-ttu-id="5385d-257">Deze para meter is geïntroduceerd in Power shell 7,1.</span><span class="sxs-lookup"><span data-stu-id="5385d-257">This parameter was introduced in PowerShell 7.1.</span></span>

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

### <span data-ttu-id="5385d-258">-Jaar</span><span class="sxs-lookup"><span data-stu-id="5385d-258">-Year</span></span>

<span data-ttu-id="5385d-259">Hiermee geeft u het jaar op dat wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5385d-259">Specifies the year that is displayed.</span></span> <span data-ttu-id="5385d-260">Voer een waarde in van 1 tot en met 9999.</span><span class="sxs-lookup"><span data-stu-id="5385d-260">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="5385d-261">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5385d-261">CommonParameters</span></span>

<span data-ttu-id="5385d-262">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5385d-262">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5385d-263">Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5385d-263">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5385d-264">INVOER</span><span class="sxs-lookup"><span data-stu-id="5385d-264">INPUTS</span></span>

### <span data-ttu-id="5385d-265">Pijplijn invoer</span><span class="sxs-lookup"><span data-stu-id="5385d-265">Pipeline input</span></span>

<span data-ttu-id="5385d-266">`Get-Date` accepteert invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="5385d-266">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="5385d-267">Bijvoorbeeld `Get-ChildItem | Get-Date`.</span><span class="sxs-lookup"><span data-stu-id="5385d-267">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="5385d-268">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5385d-268">OUTPUTS</span></span>

### <span data-ttu-id="5385d-269">System. DateTime of System. String</span><span class="sxs-lookup"><span data-stu-id="5385d-269">System.DateTime or System.String</span></span>

<span data-ttu-id="5385d-270">`Get-Date` retourneert een **DateTime** -object, behalve wanneer de **notatie** -en **UFormat** -para meters worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5385d-270">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="5385d-271">De **notatie** of para meters van de **UFormat** retour neren **teken reeks** objecten.</span><span class="sxs-lookup"><span data-stu-id="5385d-271">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="5385d-272">Wanneer een **DateTime** -object vanuit de pijp lijn naar een cmdlet wordt verzonden `Add-Content` , zoals de teken reeks invoer verwacht, converteert Power shell het object naar een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="5385d-272">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="5385d-273">Met de-methode wordt `(Get-Date).ToString()` een **DateTime** -object omgezet in een **teken reeks** object.</span><span class="sxs-lookup"><span data-stu-id="5385d-273">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="5385d-274">Als u de eigenschappen en methoden van een object wilt weer geven, verzendt u het object omlaag in de pijp lijn `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="5385d-274">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="5385d-275">Bijvoorbeeld `Get-Date | Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="5385d-275">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="5385d-276">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5385d-276">NOTES</span></span>

<span data-ttu-id="5385d-277">**DateTime** -objecten hebben een lange datum en lange tijd notatie voor de systeem land instelling.</span><span class="sxs-lookup"><span data-stu-id="5385d-277">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="5385d-278">De geldige **UFormat-specificaties** worden weer gegeven in de volgende tabel:</span><span class="sxs-lookup"><span data-stu-id="5385d-278">The valid **UFormat specifiers** are displayed in the following table:</span></span>

| <span data-ttu-id="5385d-279">Indelings aanduiding</span><span class="sxs-lookup"><span data-stu-id="5385d-279">Format specifier</span></span> |                                 <span data-ttu-id="5385d-280">Betekenis</span><span class="sxs-lookup"><span data-stu-id="5385d-280">Meaning</span></span>                     |         <span data-ttu-id="5385d-281">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="5385d-281">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="5385d-282">Dag van de week-volledige naam</span><span class="sxs-lookup"><span data-stu-id="5385d-282">Day of the week - full name</span></span>                                             | <span data-ttu-id="5385d-283">Maandag</span><span class="sxs-lookup"><span data-stu-id="5385d-283">Monday</span></span>                   |
| `%a` | <span data-ttu-id="5385d-284">Dag van de week, korte naam</span><span class="sxs-lookup"><span data-stu-id="5385d-284">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="5385d-285">Ma</span><span class="sxs-lookup"><span data-stu-id="5385d-285">Mon</span></span>                      |
| `%B` | <span data-ttu-id="5385d-286">Maand naam-volledig</span><span class="sxs-lookup"><span data-stu-id="5385d-286">Month name - full</span></span>                                                       | <span data-ttu-id="5385d-287">Januari</span><span class="sxs-lookup"><span data-stu-id="5385d-287">January</span></span>                  |
| `%b` | <span data-ttu-id="5385d-288">Maand naam-afgekort</span><span class="sxs-lookup"><span data-stu-id="5385d-288">Month name - abbreviated</span></span>                                                | <span data-ttu-id="5385d-289">Jan</span><span class="sxs-lookup"><span data-stu-id="5385d-289">Jan</span></span>                      |
| `%C` | <span data-ttu-id="5385d-290">Jaar</span><span class="sxs-lookup"><span data-stu-id="5385d-290">Century</span></span>                                                                 | <span data-ttu-id="5385d-291">20 voor 2019</span><span class="sxs-lookup"><span data-stu-id="5385d-291">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="5385d-292">Datum en tijd-afgekort</span><span class="sxs-lookup"><span data-stu-id="5385d-292">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="5385d-293">Do jun 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="5385d-293">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="5385d-294">Datum in de notatie mm/dd/jj</span><span class="sxs-lookup"><span data-stu-id="5385d-294">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="5385d-295">06/27/19</span><span class="sxs-lookup"><span data-stu-id="5385d-295">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="5385d-296">Dag van de maand: 2 cijfers</span><span class="sxs-lookup"><span data-stu-id="5385d-296">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="5385d-297">05</span><span class="sxs-lookup"><span data-stu-id="5385d-297">05</span></span>                       |
| `%e` | <span data-ttu-id="5385d-298">Dag van de maand, voorafgegaan door een spatie als er slechts één cijfer</span><span class="sxs-lookup"><span data-stu-id="5385d-298">Day of the month - preceded by a space if only a single digit</span></span>           | <span data-ttu-id="5385d-299">\<space\>5,0</span><span class="sxs-lookup"><span data-stu-id="5385d-299">\<space\>5</span></span>               |
| `%F` | <span data-ttu-id="5385d-300">Datum in de notatie JJJJ-MM-DD, gelijk aan% Y-% m-% d (ISO 8601-datum notatie)</span><span class="sxs-lookup"><span data-stu-id="5385d-300">Date in YYYY-mm-dd format, equal to %Y-%m-%d (the ISO 8601 date format)</span></span> | <span data-ttu-id="5385d-301">2019-06-27</span><span class="sxs-lookup"><span data-stu-id="5385d-301">2019-06-27</span></span>               |
| `%G` | <span data-ttu-id="5385d-302">Datum jaar ISO-week (jaar met donderdag van de week)</span><span class="sxs-lookup"><span data-stu-id="5385d-302">ISO week date year (year containing Thursday of the week)</span></span>               |                          |
| `%g` | <span data-ttu-id="5385d-303">Hetzelfde als G-2 cijfers</span><span class="sxs-lookup"><span data-stu-id="5385d-303">Same as 'G' - 2 digits</span></span>                                                  |                          |
| `%H` | <span data-ttu-id="5385d-304">Uur in 24-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="5385d-304">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="5385d-305">17</span><span class="sxs-lookup"><span data-stu-id="5385d-305">17</span></span>                       |
| `%h` | <span data-ttu-id="5385d-306">Hetzelfde als ' b '</span><span class="sxs-lookup"><span data-stu-id="5385d-306">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="5385d-307">Uur in 12-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="5385d-307">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="5385d-308">05</span><span class="sxs-lookup"><span data-stu-id="5385d-308">05</span></span>                       |
| `%j` | <span data-ttu-id="5385d-309">Dag van het jaar</span><span class="sxs-lookup"><span data-stu-id="5385d-309">Day of the year</span></span>                                                         | <span data-ttu-id="5385d-310">1-366</span><span class="sxs-lookup"><span data-stu-id="5385d-310">1-366</span></span>                    |
| `%k` | <span data-ttu-id="5385d-311">Hetzelfde als ' H '</span><span class="sxs-lookup"><span data-stu-id="5385d-311">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="5385d-312">Hetzelfde als ' I ' (hoofd letters I)</span><span class="sxs-lookup"><span data-stu-id="5385d-312">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="5385d-313">05</span><span class="sxs-lookup"><span data-stu-id="5385d-313">05</span></span>                       |
| `%M` | <span data-ttu-id="5385d-314">Minuten</span><span class="sxs-lookup"><span data-stu-id="5385d-314">Minutes</span></span>                                                                 | <span data-ttu-id="5385d-315">35</span><span class="sxs-lookup"><span data-stu-id="5385d-315">35</span></span>                       |
| `%m` | <span data-ttu-id="5385d-316">Maandnummer</span><span class="sxs-lookup"><span data-stu-id="5385d-316">Month number</span></span>                                                            | <span data-ttu-id="5385d-317">06</span><span class="sxs-lookup"><span data-stu-id="5385d-317">06</span></span>                       |
| `%n` | <span data-ttu-id="5385d-318">teken voor nieuwe regel</span><span class="sxs-lookup"><span data-stu-id="5385d-318">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="5385d-319">AM of PM</span><span class="sxs-lookup"><span data-stu-id="5385d-319">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="5385d-320">Tijd in 24-uurs notatie-geen seconden</span><span class="sxs-lookup"><span data-stu-id="5385d-320">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="5385d-321">17:45</span><span class="sxs-lookup"><span data-stu-id="5385d-321">17:45</span></span>                    |
| `%r` | <span data-ttu-id="5385d-322">Tijd in 12-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="5385d-322">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="5385d-323">09:15:36 UUR</span><span class="sxs-lookup"><span data-stu-id="5385d-323">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="5385d-324">Seconden</span><span class="sxs-lookup"><span data-stu-id="5385d-324">Seconds</span></span>                                                                 | <span data-ttu-id="5385d-325">05</span><span class="sxs-lookup"><span data-stu-id="5385d-325">05</span></span>                       |
| `%s` | <span data-ttu-id="5385d-326">Seconden verstreken sinds 1 januari 1970 00:00:00</span><span class="sxs-lookup"><span data-stu-id="5385d-326">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="5385d-327">1150451174</span><span class="sxs-lookup"><span data-stu-id="5385d-327">1150451174</span></span>               |
| `%t` | <span data-ttu-id="5385d-328">Teken voor horizontale tab</span><span class="sxs-lookup"><span data-stu-id="5385d-328">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="5385d-329">Tijd in 24-uurs notatie</span><span class="sxs-lookup"><span data-stu-id="5385d-329">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="5385d-330">17:45:52</span><span class="sxs-lookup"><span data-stu-id="5385d-330">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="5385d-331">Hetzelfde als ' W '</span><span class="sxs-lookup"><span data-stu-id="5385d-331">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="5385d-332">Numerieke dag van de week (1-7)</span><span class="sxs-lookup"><span data-stu-id="5385d-332">Numeric day of the week (1-7)</span></span>                                           | <span data-ttu-id="5385d-333">Maandag = 1, zondag = 7</span><span class="sxs-lookup"><span data-stu-id="5385d-333">Monday = 1, Sunday = 7</span></span>   |
| `%V` | <span data-ttu-id="5385d-334">Week van het jaar</span><span class="sxs-lookup"><span data-stu-id="5385d-334">Week of the year</span></span>                                                        | <span data-ttu-id="5385d-335">01-53</span><span class="sxs-lookup"><span data-stu-id="5385d-335">01-53</span></span>                    |
| `%w` | <span data-ttu-id="5385d-336">Numerieke dag van de week (0-6)</span><span class="sxs-lookup"><span data-stu-id="5385d-336">Numeric day of the week (0-6)</span></span>                                           | <span data-ttu-id="5385d-337">Zondag = 0, zaterdag = 6</span><span class="sxs-lookup"><span data-stu-id="5385d-337">Sunday = 0, Saturday = 6</span></span> |
| `%W` | <span data-ttu-id="5385d-338">Week van het jaar</span><span class="sxs-lookup"><span data-stu-id="5385d-338">Week of the year</span></span>                                                        | <span data-ttu-id="5385d-339">00-52</span><span class="sxs-lookup"><span data-stu-id="5385d-339">00-52</span></span>                    |
| `%X` | <span data-ttu-id="5385d-340">Hetzelfde als 'T '</span><span class="sxs-lookup"><span data-stu-id="5385d-340">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="5385d-341">Datum in de standaard notatie voor de land instelling</span><span class="sxs-lookup"><span data-stu-id="5385d-341">Date in standard format for locale</span></span>                                      | <span data-ttu-id="5385d-342">06/27/19 voor Engels-US</span><span class="sxs-lookup"><span data-stu-id="5385d-342">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="5385d-343">Jaar met viercijferige notatie</span><span class="sxs-lookup"><span data-stu-id="5385d-343">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="5385d-344">2019</span><span class="sxs-lookup"><span data-stu-id="5385d-344">2019</span></span>                     |
| `%y` | <span data-ttu-id="5385d-345">Jaar met een notatie van twee cijfers</span><span class="sxs-lookup"><span data-stu-id="5385d-345">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="5385d-346">19</span><span class="sxs-lookup"><span data-stu-id="5385d-346">19</span></span>                       |
| `%Z` | <span data-ttu-id="5385d-347">Tijd zone-offset van Universal Time Coordinate (UTC)</span><span class="sxs-lookup"><span data-stu-id="5385d-347">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="5385d-348">-07</span><span class="sxs-lookup"><span data-stu-id="5385d-348">-07</span></span>                      |

## <span data-ttu-id="5385d-349">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5385d-349">RELATED LINKS</span></span>

[<span data-ttu-id="5385d-350">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="5385d-350">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="5385d-351">Get-cultuur</span><span class="sxs-lookup"><span data-stu-id="5385d-351">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="5385d-352">Get-member</span><span class="sxs-lookup"><span data-stu-id="5385d-352">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="5385d-353">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="5385d-353">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="5385d-354">Nieuw-time span</span><span class="sxs-lookup"><span data-stu-id="5385d-354">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="5385d-355">Set-date</span><span class="sxs-lookup"><span data-stu-id="5385d-355">Set-Date</span></span>](Set-Date.md)
