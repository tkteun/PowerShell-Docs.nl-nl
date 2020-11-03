---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 1cfc2cdf4aaf15d54485fb04741f2bbca65fd3be
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251012"
---
# <span data-ttu-id="16b53-103">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="16b53-103">New-TimeSpan</span></span>

## <span data-ttu-id="16b53-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="16b53-104">SYNOPSIS</span></span>
<span data-ttu-id="16b53-105">Hiermee maakt u een time span-object.</span><span class="sxs-lookup"><span data-stu-id="16b53-105">Creates a TimeSpan object.</span></span>

## <span data-ttu-id="16b53-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="16b53-106">SYNTAX</span></span>

### <span data-ttu-id="16b53-107">Datum (standaard)</span><span class="sxs-lookup"><span data-stu-id="16b53-107">Date (Default)</span></span>

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="16b53-108">Tijd</span><span class="sxs-lookup"><span data-stu-id="16b53-108">Time</span></span>

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="16b53-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="16b53-109">DESCRIPTION</span></span>

<span data-ttu-id="16b53-110">De `New-TimeSpan` cmdlet maakt een **span** -object dat een tijds interval vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="16b53-110">The `New-TimeSpan` cmdlet creates a **TimeSpan** object that represents a time interval.</span></span>
<span data-ttu-id="16b53-111">U kunt een **time span** -object gebruiken om tijd toe te voegen of af te trekken van **DateTime** -objecten.</span><span class="sxs-lookup"><span data-stu-id="16b53-111">You can use a **TimeSpan** object to add or subtract time from **DateTime** objects.</span></span>

<span data-ttu-id="16b53-112">Zonder para meters `New-TimeSpan` retourneert een opdracht een **span** -object dat een tijds interval van nul vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="16b53-112">Without parameters, a `New-TimeSpan` command returns a **TimeSpan** object that represents a time interval of zero.</span></span>

## <span data-ttu-id="16b53-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="16b53-113">EXAMPLES</span></span>

### <span data-ttu-id="16b53-114">Voor beeld 1: een time span-object maken voor een opgegeven duur</span><span class="sxs-lookup"><span data-stu-id="16b53-114">Example 1: Create a TimeSpan object for a specified duration</span></span>

<span data-ttu-id="16b53-115">Met deze opdracht maakt u een **time span** -object met een duur van 1 uur en 25 minuten en slaat u deze op in een variabele met de naam `$TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="16b53-115">This command creates a **TimeSpan** object with a duration of 1 hour and 25 minutes and stores it in a variable named `$TimeSpan`.</span></span> <span data-ttu-id="16b53-116">Er wordt een weer gave van het object **time span** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="16b53-116">It displays a representation of the **TimeSpan** object.</span></span>

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### <span data-ttu-id="16b53-117">Voor beeld 2: een time span-object maken voor een tijds interval</span><span class="sxs-lookup"><span data-stu-id="16b53-117">Example 2: Create a TimeSpan object for a time interval</span></span>

<span data-ttu-id="16b53-118">In dit voor beeld wordt een nieuw **time span** -object gemaakt dat het interval aangeeft tussen het tijdstip waarop de opdracht wordt uitgevoerd en 1 januari 2010.</span><span class="sxs-lookup"><span data-stu-id="16b53-118">This example creates a new **TimeSpan** object that represents the interval between the time that the command is run and January 1, 2010.</span></span>

<span data-ttu-id="16b53-119">Voor deze opdracht is de **Start** parameter niet vereist, omdat de standaard waarde van de para meter **Start** de huidige datum en tijd is.</span><span class="sxs-lookup"><span data-stu-id="16b53-119">This command does not require the **Start** parameter, because the default value of the **Start** parameter is the current date and time.</span></span>

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### <span data-ttu-id="16b53-120">Voor beeld 3: de datum 90 dagen vanaf de huidige datum ophalen</span><span class="sxs-lookup"><span data-stu-id="16b53-120">Example 3: Get the date 90 days from the current date</span></span>

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

<span data-ttu-id="16b53-121">Met deze opdrachten wordt de datum geretourneerd die 90 dagen na de huidige datum valt.</span><span class="sxs-lookup"><span data-stu-id="16b53-121">These commands return the date that is 90 days after the current date.</span></span>

### <span data-ttu-id="16b53-122">Voor beeld 4: de time span ontdekken sinds een bestand is bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="16b53-122">Example 4: Discover the TimeSpan since a file was updated</span></span>

<span data-ttu-id="16b53-123">Met deze opdracht wordt aangegeven hoe lang het is sinds het [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) Help-bestand voor het laatst is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="16b53-123">This command tells you how long it has been since the [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) help file was last updated.</span></span>
<span data-ttu-id="16b53-124">U kunt deze opdracht indeling gebruiken voor elk bestand of elk ander object met een eigenschap **LastWriteTime** .</span><span class="sxs-lookup"><span data-stu-id="16b53-124">You can use this command format on any file, or any other object that has a **LastWriteTime** property.</span></span>

<span data-ttu-id="16b53-125">Deze opdracht werkt omdat de **Start** parameter van `New-TimeSpan` een alias van **LastWriteTime** heeft.</span><span class="sxs-lookup"><span data-stu-id="16b53-125">This command works because the **Start** parameter of `New-TimeSpan` has an alias of **LastWriteTime**.</span></span> <span data-ttu-id="16b53-126">Wanneer u een object met een **LastWriteTime** -eigenschap naar een pipet `New-TimeSpan` , gebruikt Power shell de waarde van de eigenschap **LastWriteTime** als de waarde van de para meter **Start** .</span><span class="sxs-lookup"><span data-stu-id="16b53-126">When you pipe an object that has a **LastWriteTime** property to `New-TimeSpan`, PowerShell uses the value of the **LastWriteTime** property as the value of the **Start** parameter.</span></span>

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## <span data-ttu-id="16b53-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="16b53-127">PARAMETERS</span></span>

### <span data-ttu-id="16b53-128">-Dagen</span><span class="sxs-lookup"><span data-stu-id="16b53-128">-Days</span></span>

<span data-ttu-id="16b53-129">Hiermee geeft u de dagen in de tijds Panne op.</span><span class="sxs-lookup"><span data-stu-id="16b53-129">Specifies the days in the time span.</span></span>
<span data-ttu-id="16b53-130">De standaardwaarde is 0.</span><span class="sxs-lookup"><span data-stu-id="16b53-130">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16b53-131">-End</span><span class="sxs-lookup"><span data-stu-id="16b53-131">-End</span></span>

<span data-ttu-id="16b53-132">Hiermee geeft u het einde van een tijds Panne op.</span><span class="sxs-lookup"><span data-stu-id="16b53-132">Specifies the end of a time span.</span></span>
<span data-ttu-id="16b53-133">De standaard waarde is de huidige datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="16b53-133">The default value is the current date and time.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="16b53-134">-Uren</span><span class="sxs-lookup"><span data-stu-id="16b53-134">-Hours</span></span>

<span data-ttu-id="16b53-135">Hiermee geeft u de uren in de tijds Panne op.</span><span class="sxs-lookup"><span data-stu-id="16b53-135">Specifies the hours in the time span.</span></span>
<span data-ttu-id="16b53-136">De standaard waarde is nul.</span><span class="sxs-lookup"><span data-stu-id="16b53-136">The default value is zero.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16b53-137">-Minuten</span><span class="sxs-lookup"><span data-stu-id="16b53-137">-Minutes</span></span>

<span data-ttu-id="16b53-138">Geeft de minuten in de tijds Panne aan.</span><span class="sxs-lookup"><span data-stu-id="16b53-138">Specifies the minutes in the time span.</span></span>
<span data-ttu-id="16b53-139">De standaardwaarde is 0.</span><span class="sxs-lookup"><span data-stu-id="16b53-139">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16b53-140">-Seconden</span><span class="sxs-lookup"><span data-stu-id="16b53-140">-Seconds</span></span>

<span data-ttu-id="16b53-141">Hiermee geeft u de lengte van de tijds duur in seconden op.</span><span class="sxs-lookup"><span data-stu-id="16b53-141">Specifies the length of the time span in seconds.</span></span>
<span data-ttu-id="16b53-142">De standaardwaarde is 0.</span><span class="sxs-lookup"><span data-stu-id="16b53-142">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="16b53-143">-Start</span><span class="sxs-lookup"><span data-stu-id="16b53-143">-Start</span></span>

<span data-ttu-id="16b53-144">Hiermee geeft u het begin van een tijds Panne op.</span><span class="sxs-lookup"><span data-stu-id="16b53-144">Specifies the start of a time span.</span></span>
<span data-ttu-id="16b53-145">Voer een teken reeks in die de datum en tijd vertegenwoordigt, zoals "3/15/09" of een **DateTime** -object, zoals een van een `Get-Date` opdracht.</span><span class="sxs-lookup"><span data-stu-id="16b53-145">Enter a string that represents the date and time, such as "3/15/09" or a **DateTime** object, such as one from a `Get-Date` command.</span></span> <span data-ttu-id="16b53-146">De standaard waarde is de huidige datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="16b53-146">The default value is the current date and time.</span></span>

<span data-ttu-id="16b53-147">U kunt **Start** of de alias gebruiken, **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="16b53-147">You can use **Start** or its alias, **LastWriteTime**.</span></span>
<span data-ttu-id="16b53-148">Met de **LastWriteTime** -alias kunt u objecten die een **LastWriteTime** -eigenschap hebben, zoals bestanden in het bestands systeem `[System.Io.FileIO]` , met de para meter **Start** van opgeven `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="16b53-148">The **LastWriteTime** alias lets you pipe objects that have a **LastWriteTime** property, such as files in the file system `[System.Io.FileIO]`, to the **Start** parameter of `New-TimeSpan`.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="16b53-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="16b53-149">CommonParameters</span></span>

<span data-ttu-id="16b53-150">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="16b53-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="16b53-151">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="16b53-151">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="16b53-152">INVOER</span><span class="sxs-lookup"><span data-stu-id="16b53-152">INPUTS</span></span>

### <span data-ttu-id="16b53-153">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="16b53-153">System.DateTime</span></span>

<span data-ttu-id="16b53-154">U kunt een **DateTime** -object dat de begin tijd vertegenwoordigt, door sluizen naar `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="16b53-154">You can pipe a **DateTime** object that represents that start time to `New-TimeSpan`.</span></span>

## <span data-ttu-id="16b53-155">UITVOER</span><span class="sxs-lookup"><span data-stu-id="16b53-155">OUTPUTS</span></span>

### <span data-ttu-id="16b53-156">System. time span</span><span class="sxs-lookup"><span data-stu-id="16b53-156">System.TimeSpan</span></span>

<span data-ttu-id="16b53-157">`New-TimeSpan` retourneert een object dat de tijds Panne vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="16b53-157">`New-TimeSpan` returns an object that represents the time span.</span></span>

## <span data-ttu-id="16b53-158">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="16b53-158">NOTES</span></span>

## <span data-ttu-id="16b53-159">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="16b53-159">RELATED LINKS</span></span>

[<span data-ttu-id="16b53-160">Ophalen datum</span><span class="sxs-lookup"><span data-stu-id="16b53-160">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="16b53-161">Set-date</span><span class="sxs-lookup"><span data-stu-id="16b53-161">Set-Date</span></span>](Set-Date.md)
