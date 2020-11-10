---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 63742cf1cc7431668a769bec5d4798b23db8c2ae
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94386890"
---
# <span data-ttu-id="fe80f-103">Set-Date</span><span class="sxs-lookup"><span data-stu-id="fe80f-103">Set-Date</span></span>

## <span data-ttu-id="fe80f-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fe80f-104">SYNOPSIS</span></span>
<span data-ttu-id="fe80f-105">Hiermee wijzigt u de systeem tijd op de computer naar een tijd die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="fe80f-105">Changes the system time on the computer to a time that you specify.</span></span>

## <span data-ttu-id="fe80f-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fe80f-106">SYNTAX</span></span>

### <span data-ttu-id="fe80f-107">Datum (standaard)</span><span class="sxs-lookup"><span data-stu-id="fe80f-107">Date (Default)</span></span>

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fe80f-108">Stel</span><span class="sxs-lookup"><span data-stu-id="fe80f-108">Adjust</span></span>

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fe80f-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fe80f-109">DESCRIPTION</span></span>

<span data-ttu-id="fe80f-110">`Set-Date`Met de cmdlet worden de systeem datum en-tijd op de computer gewijzigd in een datum en tijd die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="fe80f-110">The `Set-Date` cmdlet changes the system date and time on the computer to a date and time that you specify.</span></span>
<span data-ttu-id="fe80f-111">U kunt een nieuwe datum en/of tijd opgeven door een teken reeks te typen of door een **DateTime** -of **time span** -object door te geven aan `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="fe80f-111">You can specify a new date and/or time by typing a string or by passing a **DateTime** or **TimeSpan** object to `Set-Date`.</span></span> <span data-ttu-id="fe80f-112">Als u een nieuwe datum of tijd wilt opgeven, gebruikt u de para meter **date** .</span><span class="sxs-lookup"><span data-stu-id="fe80f-112">To specify a new date or time, use the **Date** parameter.</span></span>
<span data-ttu-id="fe80f-113">Als u een wijzigings interval wilt opgeven, gebruikt u de para meter **aanpassen** .</span><span class="sxs-lookup"><span data-stu-id="fe80f-113">To specify a change interval, use the **Adjust** parameter.</span></span>

## <span data-ttu-id="fe80f-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fe80f-114">EXAMPLES</span></span>

### <span data-ttu-id="fe80f-115">Voor beeld 1: drie dagen aan de systeem datum toevoegen</span><span class="sxs-lookup"><span data-stu-id="fe80f-115">Example 1: Add three days to the system date</span></span>

<span data-ttu-id="fe80f-116">Met deze opdracht worden drie dagen aan de huidige systeem datum toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="fe80f-116">This command adds three days to the current system date.</span></span>
<span data-ttu-id="fe80f-117">Dit heeft geen invloed op de tijd.</span><span class="sxs-lookup"><span data-stu-id="fe80f-117">It does not affect the time.</span></span>
<span data-ttu-id="fe80f-118">De opdracht gebruikt de para meter **date** om de datum op te geven.</span><span class="sxs-lookup"><span data-stu-id="fe80f-118">The command uses the **Date** parameter to specify the date.</span></span>

<span data-ttu-id="fe80f-119">De `Get-Date` cmdlet retourneert de huidige datum als een **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="fe80f-119">The `Get-Date` cmdlet returns the current date as a **DateTime** object.</span></span> <span data-ttu-id="fe80f-120">De methode **addDays** van het object **DateTime** voegt een opgegeven aantal dagen (3) toe aan het huidige **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="fe80f-120">The **DateTime** object's **AddDays** method adds a specified number of days (3) to the current **DateTime** object.</span></span>

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### <span data-ttu-id="fe80f-121">Voor beeld 2: de systeem klok is 10 minuten terug ingesteld</span><span class="sxs-lookup"><span data-stu-id="fe80f-121">Example 2: Set the system clock back 10 minutes</span></span>

<span data-ttu-id="fe80f-122">In dit voor beeld wordt de huidige systeem tijd 10 minuten teruggezet.</span><span class="sxs-lookup"><span data-stu-id="fe80f-122">This example sets the current system time back by 10 minutes.</span></span>

<span data-ttu-id="fe80f-123">Met de para meter **aanpassen** kunt u een wijzigings interval (min tien minuten) opgeven in de standaardtijd notatie voor de land instelling.</span><span class="sxs-lookup"><span data-stu-id="fe80f-123">The **Adjust** parameter allows you to specify an interval of change (minus ten minutes) in the standard time format for the locale.</span></span>

<span data-ttu-id="fe80f-124">De para meter **DisplayHint** vertelt Power shell om alleen de tijd weer te geven, maar dit heeft geen invloed op het **DateTime** -object dat `Set-Date` retourneert.</span><span class="sxs-lookup"><span data-stu-id="fe80f-124">The **DisplayHint** parameter tells PowerShell to display only the time, but it does not affect the **DateTime** object that `Set-Date` returns.</span></span>

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### <span data-ttu-id="fe80f-125">Voor beeld 3: de datum en tijd instellen op een variabele waarde</span><span class="sxs-lookup"><span data-stu-id="fe80f-125">Example 3: Set the date and time to a variable value</span></span>

<span data-ttu-id="fe80f-126">Met deze opdrachten worden de systeem datum en-tijd op de lokale computer gewijzigd in de datum en tijd die zijn opgeslagen in de variabele `$T` .</span><span class="sxs-lookup"><span data-stu-id="fe80f-126">These commands change the system date and time on local computer to the date and time saved in the variable `$T`.</span></span> <span data-ttu-id="fe80f-127">Met de eerste opdracht wordt de datum opgehaald en opgeslagen in `$T` .</span><span class="sxs-lookup"><span data-stu-id="fe80f-127">The first command gets the date and stores it in `$T`.</span></span>

<span data-ttu-id="fe80f-128">De tweede opdracht gebruikt de para meter **date** om het **DateTime** -object door `$T` te geven aan de `Set-Date` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fe80f-128">The second command uses the **Date** parameter to pass the **DateTime** object in `$T` to the `Set-Date` cmdlet.</span></span>

```powershell
$T = Get-Date
Set-Date -Date $T
```

### <span data-ttu-id="fe80f-129">Voor beeld 4:90 minuten toevoegen aan de systeem klok</span><span class="sxs-lookup"><span data-stu-id="fe80f-129">Example 4: Add 90 minutes to the system clock</span></span>

<span data-ttu-id="fe80f-130">Met deze opdrachten wordt de systeem tijd op de lokale computer met 90 minuten voor bereid.</span><span class="sxs-lookup"><span data-stu-id="fe80f-130">These commands advance the system time on the local computer by 90 minutes.</span></span>

<span data-ttu-id="fe80f-131">De eerste opdracht gebruikt de `New-TimeSpan` cmdlet om een **time span** -object met een interval van 90 minuten te maken en slaat het op in de `$90mins` variabele.</span><span class="sxs-lookup"><span data-stu-id="fe80f-131">The first command uses the `New-TimeSpan` cmdlet to create a **TimeSpan** object with a 90-minute interval, and saves it in the `$90mins` variable.</span></span>

<span data-ttu-id="fe80f-132">De tweede opdracht maakt gebruik van de para meter **aanpassen** van `Set-Date` om de datum aan te passen door de waarde van het object **time span** in de `$90mins` variabele.</span><span class="sxs-lookup"><span data-stu-id="fe80f-132">The second command uses the **Adjust** parameter of `Set-Date` to adjust the date by the value of the **TimeSpan** object in the `$90mins` variable.</span></span>

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## <span data-ttu-id="fe80f-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fe80f-133">PARAMETERS</span></span>

### <span data-ttu-id="fe80f-134">-Aanpassen</span><span class="sxs-lookup"><span data-stu-id="fe80f-134">-Adjust</span></span>

<span data-ttu-id="fe80f-135">Hiermee geeft u de waarde op waarvoor deze cmdlet van de huidige datum en tijd wordt toegevoegd of afgetrokken.</span><span class="sxs-lookup"><span data-stu-id="fe80f-135">Specifies the value for which this cmdlet adds or subtracts from the current date and time.</span></span>
<span data-ttu-id="fe80f-136">kan een aanpassing in de standaard datum-en tijd notatie voor uw land instelling typen of de para meter **aanpassen** gebruiken om een **time span** -object door te geven van `New-TimeSpan` tot `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="fe80f-136">can type an adjustment in standard date and time format for your locale or use the **Adjust** parameter to pass a **TimeSpan** object from `New-TimeSpan` to `Set-Date`.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fe80f-137">-Datum</span><span class="sxs-lookup"><span data-stu-id="fe80f-137">-Date</span></span>

<span data-ttu-id="fe80f-138">Wijzigt de datum en tijd in de opgegeven waarden.</span><span class="sxs-lookup"><span data-stu-id="fe80f-138">Changes the date and time to the specified values.</span></span>
<span data-ttu-id="fe80f-139">U kunt een nieuwe datum typen in de korte datum notatie en een tijd in de standaardtijd notatie voor uw land instelling.</span><span class="sxs-lookup"><span data-stu-id="fe80f-139">You can type a new date in the short date format and a time in the standard time format for your locale.</span></span> <span data-ttu-id="fe80f-140">U kunt ook een **DateTime** -object door geven van `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="fe80f-140">Or, you can pass a **DateTime** object from `Get-Date`.</span></span>

<span data-ttu-id="fe80f-141">Als u een datum opgeeft, maar niet een tijd, `Set-Date` wijzigt de tijd in middernacht op de opgegeven datum.</span><span class="sxs-lookup"><span data-stu-id="fe80f-141">If you specify a date, but not a time, `Set-Date` changes the time to midnight on the specified date.</span></span> <span data-ttu-id="fe80f-142">Als u alleen een tijd opgeeft, wordt de datum niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="fe80f-142">If you specify only a time, it does not change the date.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fe80f-143">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="fe80f-143">-DisplayHint</span></span>

<span data-ttu-id="fe80f-144">Hiermee geeft u op welke elementen van de datum en tijd worden weer gegeven. De acceptabele waarden voor deze para meter zijn:</span><span class="sxs-lookup"><span data-stu-id="fe80f-144">Specifies which elements of the date and time are displayed.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fe80f-145">**Datum** : alleen de datum weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fe80f-145">**Date** - displays only the date.</span></span>
- <span data-ttu-id="fe80f-146">**Tijd** : alleen de tijd weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fe80f-146">**Time** - displays only the time.</span></span>
- <span data-ttu-id="fe80f-147">**DateTime** : geeft de datum en tijd weer.</span><span class="sxs-lookup"><span data-stu-id="fe80f-147">**DateTime** - displays the date and time.</span></span>

<span data-ttu-id="fe80f-148">Deze para meter is alleen van invloed op de weer gave.</span><span class="sxs-lookup"><span data-stu-id="fe80f-148">This parameter affects only the display.</span></span>
<span data-ttu-id="fe80f-149">Dit heeft geen invloed op het **DateTime** -object dat wordt `Get-Date` opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fe80f-149">It does not affect the **DateTime** object that `Get-Date` retrieves.</span></span>

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

### <span data-ttu-id="fe80f-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fe80f-150">-Confirm</span></span>

<span data-ttu-id="fe80f-151">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fe80f-151">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe80f-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fe80f-152">-WhatIf</span></span>

<span data-ttu-id="fe80f-153">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="fe80f-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="fe80f-154">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fe80f-154">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fe80f-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fe80f-155">CommonParameters</span></span>

<span data-ttu-id="fe80f-156">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fe80f-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fe80f-157">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fe80f-157">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="fe80f-158">INVOER</span><span class="sxs-lookup"><span data-stu-id="fe80f-158">INPUTS</span></span>

### <span data-ttu-id="fe80f-159">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="fe80f-159">System.DateTime</span></span>

<span data-ttu-id="fe80f-160">U kunt een datum door sluizen naar `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="fe80f-160">You can pipe a date to `Set-Date`.</span></span>

## <span data-ttu-id="fe80f-161">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fe80f-161">OUTPUTS</span></span>

### <span data-ttu-id="fe80f-162">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="fe80f-162">System.DateTime</span></span>

<span data-ttu-id="fe80f-163">`Set-Date` retourneert een object dat staat voor de datum die is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="fe80f-163">`Set-Date` returns an object that represents the date that it set.</span></span>

## <span data-ttu-id="fe80f-164">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fe80f-164">NOTES</span></span>

- <span data-ttu-id="fe80f-165">Gebruik deze cmdlet voorzichtig bij het wijzigen van de datum en tijd op de computer.</span><span class="sxs-lookup"><span data-stu-id="fe80f-165">Use this cmdlet cautiously when changing the date and time on the computer.</span></span> <span data-ttu-id="fe80f-166">De wijziging kan ertoe leiden dat de computer geen systeem gebeurtenissen en updates ontvangt die worden geactiveerd door een datum of tijd.</span><span class="sxs-lookup"><span data-stu-id="fe80f-166">The change might prevent the computer from receiving system-wide events and updates that are triggered by a date or time.</span></span> <span data-ttu-id="fe80f-167">Gebruik de **WhatIf** en **Bevestig** de para meters om fouten te voor komen.</span><span class="sxs-lookup"><span data-stu-id="fe80f-167">Use the **WhatIf** and **Confirm** parameters to avoid errors.</span></span>
- <span data-ttu-id="fe80f-168">U kunt standaard .NET-methoden gebruiken met de **DateTime** -en **time span** -objecten die worden gebruikt met `Set-Date` , zoals **addDays** , **AddMonths** en **FromFileTime**.</span><span class="sxs-lookup"><span data-stu-id="fe80f-168">You can use standard .NET methods with the **DateTime** and **TimeSpan** objects used with `Set-Date`, such as **AddDays** , **AddMonths** , and **FromFileTime**.</span></span> <span data-ttu-id="fe80f-169">Zie [DateTime-methoden](/dotnet/api/system.datetime) en voor meer informatie</span><span class="sxs-lookup"><span data-stu-id="fe80f-169">For more information, see [DateTime Methods](/dotnet/api/system.datetime) and</span></span>

  <span data-ttu-id="fe80f-170">[Time span-methoden](/dotnet/api/system.timespan) in de .NET SDK.</span><span class="sxs-lookup"><span data-stu-id="fe80f-170">[TimeSpan Methods](/dotnet/api/system.timespan) in the .NET SDK.</span></span>

## <span data-ttu-id="fe80f-171">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fe80f-171">RELATED LINKS</span></span>

[<span data-ttu-id="fe80f-172">Ophalen datum</span><span class="sxs-lookup"><span data-stu-id="fe80f-172">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="fe80f-173">Nieuw-time span</span><span class="sxs-lookup"><span data-stu-id="fe80f-173">New-TimeSpan</span></span>](New-TimeSpan.md)
