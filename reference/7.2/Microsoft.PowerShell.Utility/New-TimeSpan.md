---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 5808685a5560d1cbf91c6705b90643c35702b28a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705926"
---
# <span data-ttu-id="4092e-102">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="4092e-102">New-TimeSpan</span></span>

## <span data-ttu-id="4092e-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4092e-103">SYNOPSIS</span></span>
<span data-ttu-id="4092e-104">Hiermee maakt u een time span-object.</span><span class="sxs-lookup"><span data-stu-id="4092e-104">Creates a TimeSpan object.</span></span>

## <span data-ttu-id="4092e-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4092e-105">SYNTAX</span></span>

### <span data-ttu-id="4092e-106">Datum (standaard)</span><span class="sxs-lookup"><span data-stu-id="4092e-106">Date (Default)</span></span>

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="4092e-107">Tijd</span><span class="sxs-lookup"><span data-stu-id="4092e-107">Time</span></span>

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="4092e-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4092e-108">DESCRIPTION</span></span>

<span data-ttu-id="4092e-109">De `New-TimeSpan` cmdlet maakt een **span** -object dat een tijds interval vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="4092e-109">The `New-TimeSpan` cmdlet creates a **TimeSpan** object that represents a time interval.</span></span>
<span data-ttu-id="4092e-110">U kunt een **time span** -object gebruiken om tijd toe te voegen of af te trekken van **DateTime** -objecten.</span><span class="sxs-lookup"><span data-stu-id="4092e-110">You can use a **TimeSpan** object to add or subtract time from **DateTime** objects.</span></span>

<span data-ttu-id="4092e-111">Zonder para meters `New-TimeSpan` retourneert een opdracht een **span** -object dat een tijds interval van nul vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="4092e-111">Without parameters, a `New-TimeSpan` command returns a **TimeSpan** object that represents a time interval of zero.</span></span>

## <span data-ttu-id="4092e-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4092e-112">EXAMPLES</span></span>

### <span data-ttu-id="4092e-113">Voor beeld 1: een time span-object maken voor een opgegeven duur</span><span class="sxs-lookup"><span data-stu-id="4092e-113">Example 1: Create a TimeSpan object for a specified duration</span></span>

<span data-ttu-id="4092e-114">Met deze opdracht maakt u een **time span** -object met een duur van 1 uur en 25 minuten en slaat u deze op in een variabele met de naam `$TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="4092e-114">This command creates a **TimeSpan** object with a duration of 1 hour and 25 minutes and stores it in a variable named `$TimeSpan`.</span></span> <span data-ttu-id="4092e-115">Er wordt een weer gave van het object **time span** weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4092e-115">It displays a representation of the **TimeSpan** object.</span></span>

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

### <span data-ttu-id="4092e-116">Voor beeld 2: een time span-object maken voor een tijds interval</span><span class="sxs-lookup"><span data-stu-id="4092e-116">Example 2: Create a TimeSpan object for a time interval</span></span>

<span data-ttu-id="4092e-117">In dit voor beeld wordt een nieuw **time span** -object gemaakt dat het interval aangeeft tussen het tijdstip waarop de opdracht wordt uitgevoerd en 1 januari 2010.</span><span class="sxs-lookup"><span data-stu-id="4092e-117">This example creates a new **TimeSpan** object that represents the interval between the time that the command is run and January 1, 2010.</span></span>

<span data-ttu-id="4092e-118">Voor deze opdracht is de **Start** parameter niet vereist, omdat de standaard waarde van de para meter **Start** de huidige datum en tijd is.</span><span class="sxs-lookup"><span data-stu-id="4092e-118">This command does not require the **Start** parameter, because the default value of the **Start** parameter is the current date and time.</span></span>

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### <span data-ttu-id="4092e-119">Voor beeld 3: de datum 90 dagen vanaf de huidige datum ophalen</span><span class="sxs-lookup"><span data-stu-id="4092e-119">Example 3: Get the date 90 days from the current date</span></span>

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

<span data-ttu-id="4092e-120">Met deze opdrachten wordt de datum geretourneerd die 90 dagen na de huidige datum valt.</span><span class="sxs-lookup"><span data-stu-id="4092e-120">These commands return the date that is 90 days after the current date.</span></span>

### <span data-ttu-id="4092e-121">Voor beeld 4: de time span ontdekken sinds een bestand is bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="4092e-121">Example 4: Discover the TimeSpan since a file was updated</span></span>

<span data-ttu-id="4092e-122">Met deze opdracht wordt aangegeven hoe lang het is sinds het [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) Help-bestand voor het laatst is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="4092e-122">This command tells you how long it has been since the [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) help file was last updated.</span></span>
<span data-ttu-id="4092e-123">U kunt deze opdracht indeling gebruiken voor elk bestand of elk ander object met een eigenschap **LastWriteTime** .</span><span class="sxs-lookup"><span data-stu-id="4092e-123">You can use this command format on any file, or any other object that has a **LastWriteTime** property.</span></span>

<span data-ttu-id="4092e-124">Deze opdracht werkt omdat de **Start** parameter van `New-TimeSpan` een alias van **LastWriteTime** heeft.</span><span class="sxs-lookup"><span data-stu-id="4092e-124">This command works because the **Start** parameter of `New-TimeSpan` has an alias of **LastWriteTime**.</span></span> <span data-ttu-id="4092e-125">Wanneer u een object met een **LastWriteTime** -eigenschap naar een pipet `New-TimeSpan` , gebruikt Power shell de waarde van de eigenschap **LastWriteTime** als de waarde van de para meter **Start** .</span><span class="sxs-lookup"><span data-stu-id="4092e-125">When you pipe an object that has a **LastWriteTime** property to `New-TimeSpan`, PowerShell uses the value of the **LastWriteTime** property as the value of the **Start** parameter.</span></span>

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

## <span data-ttu-id="4092e-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4092e-126">PARAMETERS</span></span>

### <span data-ttu-id="4092e-127">-Dagen</span><span class="sxs-lookup"><span data-stu-id="4092e-127">-Days</span></span>

<span data-ttu-id="4092e-128">Hiermee geeft u de dagen in de tijds Panne op.</span><span class="sxs-lookup"><span data-stu-id="4092e-128">Specifies the days in the time span.</span></span>
<span data-ttu-id="4092e-129">De standaardwaarde is 0.</span><span class="sxs-lookup"><span data-stu-id="4092e-129">The default value is 0.</span></span>

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

### <span data-ttu-id="4092e-130">-End</span><span class="sxs-lookup"><span data-stu-id="4092e-130">-End</span></span>

<span data-ttu-id="4092e-131">Hiermee geeft u het einde van een tijds Panne op.</span><span class="sxs-lookup"><span data-stu-id="4092e-131">Specifies the end of a time span.</span></span>
<span data-ttu-id="4092e-132">De standaard waarde is de huidige datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="4092e-132">The default value is the current date and time.</span></span>

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

### <span data-ttu-id="4092e-133">-Uren</span><span class="sxs-lookup"><span data-stu-id="4092e-133">-Hours</span></span>

<span data-ttu-id="4092e-134">Hiermee geeft u de uren in de tijds Panne op.</span><span class="sxs-lookup"><span data-stu-id="4092e-134">Specifies the hours in the time span.</span></span>
<span data-ttu-id="4092e-135">De standaard waarde is nul.</span><span class="sxs-lookup"><span data-stu-id="4092e-135">The default value is zero.</span></span>

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

### <span data-ttu-id="4092e-136">-Minuten</span><span class="sxs-lookup"><span data-stu-id="4092e-136">-Minutes</span></span>

<span data-ttu-id="4092e-137">Geeft de minuten in de tijds Panne aan.</span><span class="sxs-lookup"><span data-stu-id="4092e-137">Specifies the minutes in the time span.</span></span>
<span data-ttu-id="4092e-138">De standaardwaarde is 0.</span><span class="sxs-lookup"><span data-stu-id="4092e-138">The default value is 0.</span></span>

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

### <span data-ttu-id="4092e-139">-Seconden</span><span class="sxs-lookup"><span data-stu-id="4092e-139">-Seconds</span></span>

<span data-ttu-id="4092e-140">Hiermee geeft u de lengte van de tijds duur in seconden op.</span><span class="sxs-lookup"><span data-stu-id="4092e-140">Specifies the length of the time span in seconds.</span></span>
<span data-ttu-id="4092e-141">De standaardwaarde is 0.</span><span class="sxs-lookup"><span data-stu-id="4092e-141">The default value is 0.</span></span>

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

### <span data-ttu-id="4092e-142">-Start</span><span class="sxs-lookup"><span data-stu-id="4092e-142">-Start</span></span>

<span data-ttu-id="4092e-143">Hiermee geeft u het begin van een tijds Panne op.</span><span class="sxs-lookup"><span data-stu-id="4092e-143">Specifies the start of a time span.</span></span>
<span data-ttu-id="4092e-144">Voer een teken reeks in die de datum en tijd vertegenwoordigt, zoals "3/15/09" of een **DateTime** -object, zoals een van een `Get-Date` opdracht.</span><span class="sxs-lookup"><span data-stu-id="4092e-144">Enter a string that represents the date and time, such as "3/15/09" or a **DateTime** object, such as one from a `Get-Date` command.</span></span> <span data-ttu-id="4092e-145">De standaard waarde is de huidige datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="4092e-145">The default value is the current date and time.</span></span>

<span data-ttu-id="4092e-146">U kunt **Start** of de alias gebruiken, **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="4092e-146">You can use **Start** or its alias, **LastWriteTime**.</span></span>
<span data-ttu-id="4092e-147">Met de **LastWriteTime** -alias kunt u objecten die een **LastWriteTime** -eigenschap hebben, zoals bestanden in het bestands systeem `[System.Io.FileIO]` , met de para meter **Start** van opgeven `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="4092e-147">The **LastWriteTime** alias lets you pipe objects that have a **LastWriteTime** property, such as files in the file system `[System.Io.FileIO]`, to the **Start** parameter of `New-TimeSpan`.</span></span>

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

### <span data-ttu-id="4092e-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4092e-148">CommonParameters</span></span>

<span data-ttu-id="4092e-149">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4092e-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4092e-150">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4092e-150">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4092e-151">INVOER</span><span class="sxs-lookup"><span data-stu-id="4092e-151">INPUTS</span></span>

### <span data-ttu-id="4092e-152">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="4092e-152">System.DateTime</span></span>

<span data-ttu-id="4092e-153">U kunt een **DateTime** -object dat de begin tijd vertegenwoordigt, door sluizen naar `New-TimeSpan` .</span><span class="sxs-lookup"><span data-stu-id="4092e-153">You can pipe a **DateTime** object that represents that start time to `New-TimeSpan`.</span></span>

## <span data-ttu-id="4092e-154">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4092e-154">OUTPUTS</span></span>

### <span data-ttu-id="4092e-155">System. time span</span><span class="sxs-lookup"><span data-stu-id="4092e-155">System.TimeSpan</span></span>

<span data-ttu-id="4092e-156">`New-TimeSpan` retourneert een object dat de tijds Panne vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="4092e-156">`New-TimeSpan` returns an object that represents the time span.</span></span>

## <span data-ttu-id="4092e-157">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4092e-157">NOTES</span></span>

## <span data-ttu-id="4092e-158">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4092e-158">RELATED LINKS</span></span>

[<span data-ttu-id="4092e-159">Ophalen datum</span><span class="sxs-lookup"><span data-stu-id="4092e-159">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="4092e-160">Set-date</span><span class="sxs-lookup"><span data-stu-id="4092e-160">Set-Date</span></span>](Set-Date.md)

