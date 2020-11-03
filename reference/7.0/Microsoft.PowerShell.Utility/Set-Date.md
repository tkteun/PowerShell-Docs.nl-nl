---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 5999dfbba27a8eedbc054edee3ca2b1061dd2adc
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249442"
---
# <span data-ttu-id="589dc-103">Set-Date</span><span class="sxs-lookup"><span data-stu-id="589dc-103">Set-Date</span></span>

## <span data-ttu-id="589dc-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="589dc-104">SYNOPSIS</span></span>
<span data-ttu-id="589dc-105">Hiermee wijzigt u de systeem tijd op de computer naar een tijd die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="589dc-105">Changes the system time on the computer to a time that you specify.</span></span>

## <span data-ttu-id="589dc-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="589dc-106">SYNTAX</span></span>

### <span data-ttu-id="589dc-107">Datum (standaard)</span><span class="sxs-lookup"><span data-stu-id="589dc-107">Date (Default)</span></span>

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="589dc-108">Stel</span><span class="sxs-lookup"><span data-stu-id="589dc-108">Adjust</span></span>

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="589dc-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="589dc-109">DESCRIPTION</span></span>

<span data-ttu-id="589dc-110">`Set-Date`Met de cmdlet worden de systeem datum en-tijd op de computer gewijzigd in een datum en tijd die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="589dc-110">The `Set-Date` cmdlet changes the system date and time on the computer to a date and time that you specify.</span></span>
<span data-ttu-id="589dc-111">U kunt een nieuwe datum en/of tijd opgeven door een teken reeks te typen of door een **DateTime** -of **time span** -object door te geven aan `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="589dc-111">You can specify a new date and/or time by typing a string or by passing a **DateTime** or **TimeSpan** object to `Set-Date`.</span></span> <span data-ttu-id="589dc-112">Als u een nieuwe datum of tijd wilt opgeven, gebruikt u de para meter **date** .</span><span class="sxs-lookup"><span data-stu-id="589dc-112">To specify a new date or time, use the **Date** parameter.</span></span>
<span data-ttu-id="589dc-113">Als u een wijzigings interval wilt opgeven, gebruikt u de para meter **aanpassen** .</span><span class="sxs-lookup"><span data-stu-id="589dc-113">To specify a change interval, use the **Adjust** parameter.</span></span>

## <span data-ttu-id="589dc-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="589dc-114">EXAMPLES</span></span>

### <span data-ttu-id="589dc-115">Voor beeld 1: drie dagen aan de systeem datum toevoegen</span><span class="sxs-lookup"><span data-stu-id="589dc-115">Example 1: Add three days to the system date</span></span>

<span data-ttu-id="589dc-116">Met deze opdracht worden drie dagen aan de huidige systeem datum toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="589dc-116">This command adds three days to the current system date.</span></span>
<span data-ttu-id="589dc-117">Dit heeft geen invloed op de tijd.</span><span class="sxs-lookup"><span data-stu-id="589dc-117">It does not affect the time.</span></span>
<span data-ttu-id="589dc-118">De opdracht gebruikt de para meter **date** om de datum op te geven.</span><span class="sxs-lookup"><span data-stu-id="589dc-118">The command uses the **Date** parameter to specify the date.</span></span>

<span data-ttu-id="589dc-119">De `Get-Date` cmdlet retourneert de huidige datum als een **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="589dc-119">The `Get-Date` cmdlet returns the current date as a **DateTime** object.</span></span> <span data-ttu-id="589dc-120">De methode **addDays** van het object **DateTime** voegt een opgegeven aantal dagen (3) toe aan het huidige **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="589dc-120">The **DateTime** object's **AddDays** method adds a specified number of days (3) to the current **DateTime** object.</span></span>

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### <span data-ttu-id="589dc-121">Voor beeld 2: de systeem klok is 10 minuten terug ingesteld</span><span class="sxs-lookup"><span data-stu-id="589dc-121">Example 2: Set the system clock back 10 minutes</span></span>

<span data-ttu-id="589dc-122">In dit voor beeld wordt de huidige systeem tijd 10 minuten teruggezet.</span><span class="sxs-lookup"><span data-stu-id="589dc-122">This example sets the current system time back by 10 minutes.</span></span>

<span data-ttu-id="589dc-123">Met de para meter **aanpassen** kunt u een wijzigings interval (min tien minuten) opgeven in de standaardtijd notatie voor de land instelling.</span><span class="sxs-lookup"><span data-stu-id="589dc-123">The **Adjust** parameter allows you to specify an interval of change (minus ten minutes) in the standard time format for the locale.</span></span>

<span data-ttu-id="589dc-124">De para meter **DisplayHint** vertelt Power shell om alleen de tijd weer te geven, maar dit heeft geen invloed op het **DateTime** -object dat `Set-Date` retourneert.</span><span class="sxs-lookup"><span data-stu-id="589dc-124">The **DisplayHint** parameter tells PowerShell to display only the time, but it does not affect the **DateTime** object that `Set-Date` returns.</span></span>

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### <span data-ttu-id="589dc-125">Voor beeld 3: de datum en tijd instellen op een variabele waarde</span><span class="sxs-lookup"><span data-stu-id="589dc-125">Example 3: Set the date and time to a variable value</span></span>

<span data-ttu-id="589dc-126">Met deze opdrachten worden de systeem datum en-tijd op de lokale computer gewijzigd in de datum en tijd die zijn opgeslagen in de variabele `$T` .</span><span class="sxs-lookup"><span data-stu-id="589dc-126">These commands change the system date and time on local computer to the date and time saved in the variable `$T`.</span></span> <span data-ttu-id="589dc-127">Met de eerste opdracht wordt de datum opgehaald en opgeslagen in `$T` .</span><span class="sxs-lookup"><span data-stu-id="589dc-127">The first command gets the date and stores it in `$T`.</span></span>

<span data-ttu-id="589dc-128">De tweede opdracht gebruikt de para meter **date** om het **DateTime** -object door `$T` te geven aan de `Set-Date` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="589dc-128">The second command uses the **Date** parameter to pass the **DateTime** object in `$T` to the `Set-Date` cmdlet.</span></span>

```powershell
$T = Get-Date
Set-Date -Date $T
```

### <span data-ttu-id="589dc-129">Voor beeld 4:90 minuten toevoegen aan de systeem klok</span><span class="sxs-lookup"><span data-stu-id="589dc-129">Example 4: Add 90 minutes to the system clock</span></span>

<span data-ttu-id="589dc-130">Met deze opdrachten wordt de systeem tijd op de lokale computer met 90 minuten voor bereid.</span><span class="sxs-lookup"><span data-stu-id="589dc-130">These commands advance the system time on the local computer by 90 minutes.</span></span>

<span data-ttu-id="589dc-131">De eerste opdracht gebruikt de `New-TimeSpan` cmdlet om een **time span** -object met een interval van 90 minuten te maken en slaat het op in de `$90mins` variabele.</span><span class="sxs-lookup"><span data-stu-id="589dc-131">The first command uses the `New-TimeSpan` cmdlet to create a **TimeSpan** object with a 90-minute interval, and saves it in the `$90mins` variable.</span></span>

<span data-ttu-id="589dc-132">De tweede opdracht maakt gebruik van de para meter **aanpassen** van `Set-Date` om de datum aan te passen door de waarde van het object **time span** in de `$90mins` variabele.</span><span class="sxs-lookup"><span data-stu-id="589dc-132">The second command uses the **Adjust** parameter of `Set-Date` to adjust the date by the value of the **TimeSpan** object in the `$90mins` variable.</span></span>

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## <span data-ttu-id="589dc-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="589dc-133">PARAMETERS</span></span>

### <span data-ttu-id="589dc-134">-Aanpassen</span><span class="sxs-lookup"><span data-stu-id="589dc-134">-Adjust</span></span>

<span data-ttu-id="589dc-135">Hiermee geeft u de waarde op waarvoor deze cmdlet van de huidige datum en tijd wordt toegevoegd of afgetrokken.</span><span class="sxs-lookup"><span data-stu-id="589dc-135">Specifies the value for which this cmdlet adds or subtracts from the current date and time.</span></span>
<span data-ttu-id="589dc-136">kan een aanpassing in de standaard datum-en tijd notatie voor uw land instelling typen of de para meter **aanpassen** gebruiken om een **time span** -object door te geven van `New-TimeSpan` tot `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="589dc-136">can type an adjustment in standard date and time format for your locale or use the **Adjust** parameter to pass a **TimeSpan** object from `New-TimeSpan` to `Set-Date`.</span></span>

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

### <span data-ttu-id="589dc-137">-Datum</span><span class="sxs-lookup"><span data-stu-id="589dc-137">-Date</span></span>

<span data-ttu-id="589dc-138">Wijzigt de datum en tijd in de opgegeven waarden.</span><span class="sxs-lookup"><span data-stu-id="589dc-138">Changes the date and time to the specified values.</span></span>
<span data-ttu-id="589dc-139">U kunt een nieuwe datum typen in de korte datum notatie en een tijd in de standaardtijd notatie voor uw land instelling.</span><span class="sxs-lookup"><span data-stu-id="589dc-139">You can type a new date in the short date format and a time in the standard time format for your locale.</span></span> <span data-ttu-id="589dc-140">U kunt ook een **DateTime** -object door geven van `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="589dc-140">Or, you can pass a **DateTime** object from `Get-Date`.</span></span>

<span data-ttu-id="589dc-141">Als u een datum opgeeft, maar niet een tijd, `Set-Date` wijzigt de tijd in middernacht op de opgegeven datum.</span><span class="sxs-lookup"><span data-stu-id="589dc-141">If you specify a date, but not a time, `Set-Date` changes the time to midnight on the specified date.</span></span> <span data-ttu-id="589dc-142">Als u alleen een tijd opgeeft, wordt de datum niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="589dc-142">If you specify only a time, it does not change the date.</span></span>

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

### <span data-ttu-id="589dc-143">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="589dc-143">-DisplayHint</span></span>

<span data-ttu-id="589dc-144">Hiermee geeft u op welke elementen van de datum en tijd worden weer gegeven. De acceptabele waarden voor deze para meter zijn:</span><span class="sxs-lookup"><span data-stu-id="589dc-144">Specifies which elements of the date and time are displayed.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="589dc-145">Vallen.</span><span class="sxs-lookup"><span data-stu-id="589dc-145">Date.</span></span>
  <span data-ttu-id="589dc-146">geeft alleen de datum weer.</span><span class="sxs-lookup"><span data-stu-id="589dc-146">displays only the date.</span></span>
- <span data-ttu-id="589dc-147">Tijd.</span><span class="sxs-lookup"><span data-stu-id="589dc-147">Time.</span></span>
  <span data-ttu-id="589dc-148">geeft alleen de tijd weer.</span><span class="sxs-lookup"><span data-stu-id="589dc-148">displays only the time.</span></span>
- <span data-ttu-id="589dc-149">DateTime.</span><span class="sxs-lookup"><span data-stu-id="589dc-149">DateTime.</span></span>
  <span data-ttu-id="589dc-150">Hier worden de datum en tijd weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="589dc-150">displays the date and time.</span></span>

<span data-ttu-id="589dc-151">Deze para meter is alleen van invloed op de weer gave.</span><span class="sxs-lookup"><span data-stu-id="589dc-151">This parameter affects only the display.</span></span>
<span data-ttu-id="589dc-152">Dit heeft geen invloed op het **DateTime** -object dat wordt `Get-Date` opgehaald.</span><span class="sxs-lookup"><span data-stu-id="589dc-152">It does not affect the **DateTime** object that `Get-Date` retrieves.</span></span>

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

### <span data-ttu-id="589dc-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="589dc-153">-Confirm</span></span>

<span data-ttu-id="589dc-154">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="589dc-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="589dc-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="589dc-155">-WhatIf</span></span>

<span data-ttu-id="589dc-156">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="589dc-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="589dc-157">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="589dc-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="589dc-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="589dc-158">CommonParameters</span></span>

<span data-ttu-id="589dc-159">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="589dc-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="589dc-160">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="589dc-160">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="589dc-161">INVOER</span><span class="sxs-lookup"><span data-stu-id="589dc-161">INPUTS</span></span>

### <span data-ttu-id="589dc-162">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="589dc-162">System.DateTime</span></span>

<span data-ttu-id="589dc-163">U kunt een datum door sluizen naar `Set-Date` .</span><span class="sxs-lookup"><span data-stu-id="589dc-163">You can pipe a date to `Set-Date`.</span></span>

## <span data-ttu-id="589dc-164">UITVOER</span><span class="sxs-lookup"><span data-stu-id="589dc-164">OUTPUTS</span></span>

### <span data-ttu-id="589dc-165">System. DateTime</span><span class="sxs-lookup"><span data-stu-id="589dc-165">System.DateTime</span></span>

<span data-ttu-id="589dc-166">`Set-Date` retourneert een object dat staat voor de datum die is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="589dc-166">`Set-Date` returns an object that represents the date that it set.</span></span>

## <span data-ttu-id="589dc-167">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="589dc-167">NOTES</span></span>

- <span data-ttu-id="589dc-168">Gebruik deze cmdlet voorzichtig bij het wijzigen van de datum en tijd op de computer.</span><span class="sxs-lookup"><span data-stu-id="589dc-168">Use this cmdlet cautiously when changing the date and time on the computer.</span></span> <span data-ttu-id="589dc-169">De wijziging kan ertoe leiden dat de computer geen systeem gebeurtenissen en updates ontvangt die worden geactiveerd door een datum of tijd.</span><span class="sxs-lookup"><span data-stu-id="589dc-169">The change might prevent the computer from receiving system-wide events and updates that are triggered by a date or time.</span></span> <span data-ttu-id="589dc-170">Gebruik de **WhatIf** en **Bevestig** de para meters om fouten te voor komen.</span><span class="sxs-lookup"><span data-stu-id="589dc-170">Use the **WhatIf** and **Confirm** parameters to avoid errors.</span></span>
- <span data-ttu-id="589dc-171">U kunt standaard .NET-methoden gebruiken met de **DateTime** -en **time span** -objecten die worden gebruikt met `Set-Date` , zoals **addDays** , **AddMonths** en **FromFileTime**.</span><span class="sxs-lookup"><span data-stu-id="589dc-171">You can use standard .NET methods with the **DateTime** and **TimeSpan** objects used with `Set-Date`, such as **AddDays** , **AddMonths** , and **FromFileTime**.</span></span> <span data-ttu-id="589dc-172">Zie [DateTime-methoden](/dotnet/api/system.datetime) en voor meer informatie</span><span class="sxs-lookup"><span data-stu-id="589dc-172">For more information, see [DateTime Methods](/dotnet/api/system.datetime) and</span></span>

  <span data-ttu-id="589dc-173">[Time span-methoden](/dotnet/api/system.timespan) in de MSDN-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="589dc-173">[TimeSpan Methods](/dotnet/api/system.timespan) in the MSDN library.</span></span>

## <span data-ttu-id="589dc-174">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="589dc-174">RELATED LINKS</span></span>

[<span data-ttu-id="589dc-175">Ophalen datum</span><span class="sxs-lookup"><span data-stu-id="589dc-175">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="589dc-176">Nieuw-time span</span><span class="sxs-lookup"><span data-stu-id="589dc-176">New-TimeSpan</span></span>](New-TimeSpan.md)
