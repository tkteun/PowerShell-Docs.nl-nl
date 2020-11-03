---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: 6cadebfbcdc8cc7a333d62c3c7b9ff5fb6635168
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2020
ms.locfileid: "93253276"
---
# <span data-ttu-id="5f4d8-103">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="5f4d8-103">Get-Culture</span></span>

## <span data-ttu-id="5f4d8-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="5f4d8-104">SYNOPSIS</span></span>
<span data-ttu-id="5f4d8-105">Hiermee wordt de huidige cultuur ingesteld in het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-105">Gets the current culture set in the operating system.</span></span>

## <span data-ttu-id="5f4d8-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="5f4d8-106">SYNTAX</span></span>

### <span data-ttu-id="5f4d8-107">CurrentCulture (standaard)</span><span class="sxs-lookup"><span data-stu-id="5f4d8-107">CurrentCulture (Default)</span></span>

```
Get-Culture [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="5f4d8-108">Naam</span><span class="sxs-lookup"><span data-stu-id="5f4d8-108">Name</span></span>

```
Get-Culture [-Name <String[]>] [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="5f4d8-109">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="5f4d8-109">ListAvailable</span></span>

```
Get-Culture [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="5f4d8-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="5f4d8-110">DESCRIPTION</span></span>

<span data-ttu-id="5f4d8-111">De `Get-Culture` cmdlet haalt informatie op over de huidige cultuur instellingen.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-111">The `Get-Culture` cmdlet gets information about the current culture settings.</span></span> <span data-ttu-id="5f4d8-112">Dit omvat informatie over de huidige taal instellingen op het systeem, zoals de toetsenbord indeling en de weer gave-indeling van items zoals getallen, valuta en datums.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-112">This includes information about the current language settings on the system, such as the keyboard layout, and the display format of items such as numbers, currency, and dates.</span></span>

<span data-ttu-id="5f4d8-113">U kunt ook de `Get-UICulture` -cmdlet gebruiken, waarmee de huidige gebruikersinterface cultuur op het systeem wordt opgehaald en de cmdlet [set-Culture](/powershell/module/international/set-culture) in de module International.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-113">You can also use the `Get-UICulture` cmdlet, which gets the current user interface culture on the system, and the [Set-Culture](/powershell/module/international/set-culture) cmdlet in the International module.</span></span> <span data-ttu-id="5f4d8-114">De cultuur gebruikers interface (UI) bepaalt welke teken reeksen worden gebruikt voor elementen van de gebruikers interface, zoals menu's en berichten.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-114">The user-interface (UI) culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

## <span data-ttu-id="5f4d8-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="5f4d8-115">EXAMPLES</span></span>

### <span data-ttu-id="5f4d8-116">Voor beeld 1: Cultuur instellingen ophalen</span><span class="sxs-lookup"><span data-stu-id="5f4d8-116">Example 1: Get culture settings</span></span>

```powershell
Get-Culture
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="5f4d8-117">Met deze opdracht wordt informatie weer gegeven over de land instellingen op de computer.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-117">This command displays information about the regional settings on the computer.</span></span>

### <span data-ttu-id="5f4d8-118">Voor beeld 2: de eigenschappen van een cultuur object opmaken</span><span class="sxs-lookup"><span data-stu-id="5f4d8-118">Example 2: Format the properties of a culture object</span></span>

```powershell
PS C:\> $C = Get-Culture
PS C:\> $C | Format-List -Property *
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
CompareInfo                    : CompareInfo - 1033
TextInfo                       : TextInfo - 1033
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar, System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False

PS C:\> $C.Calendar
MinSupportedDateTime : 1/1/0001 12:00:00 AM
MaxSupportedDateTime : 12/31/9999 11:59:59 PM
AlgorithmType        : SolarCalendar
CalendarType         : Localized
Eras                 : {1}
TwoDigitYearMax      : 2029
IsReadOnly           : False

PS C:\> $C.DateTimeFormat
AMDesignator                     : AM
Calendar                         : System.Globalization.GregorianCalendar
DateSeparator                    : /
FirstDayOfWeek                   : Sunday
CalendarWeekRule                 : FirstDay
FullDateTimePattern              : dddd, MMMM dd, yyyy h:mm:ss tt
LongDatePattern                  : dddd, MMMM dd, yyyy
LongTimePattern                  : h:mm:ss tt
MonthDayPattern                  : MMMM dd
PMDesignator                     : PM
RFC1123Pattern                   : ddd, dd MMM yyyy HH':'mm':'ss 'GMT'
ShortDatePattern                 : M/d/yyyy
ShortTimePattern                 : h:mm tt
SortableDateTimePattern          : yyyy'-'MM'-'dd'T'HH':'mm':'ss
TimeSeparator                    : :
UniversalSortableDateTimePattern : yyyy'-'MM'-'dd HH':'mm':'ss'Z'
YearMonthPattern                 : MMMM, yyyy
AbbreviatedDayNames              : {Sun, Mon, Tue, Wed...}
ShortestDayNames                 : {Su, Mo, Tu, We...}
DayNames                         : {Sunday, Monday, Tuesday, Wednesday...}
AbbreviatedMonthNames            : {Jan, Feb, Mar, Apr...}
MonthNames                       : {January, February, March, April...}
IsReadOnly                       : False
NativeCalendarName               : Gregorian Calendar
AbbreviatedMonthGenitiveNames    : {Jan, Feb, Mar, Apr...}
MonthGenitiveNames               : {January, February, March, April...}

PS C:\> $C.DateTimeFormat.FirstDayOfWeek
Sunday
```

<span data-ttu-id="5f4d8-119">In dit voor beeld wordt de enorme hoeveelheid gegevens in het object Culture gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-119">This example demonstrates the vast amount of data in the culture object.</span></span> <span data-ttu-id="5f4d8-120">Hierin ziet u hoe de eigenschappen en subeigenschappen van het object worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-120">It shows how to display the properties and sub-properties of the object.</span></span>

<span data-ttu-id="5f4d8-121">Met de eerste opdracht wordt de `Get-Culture` cmdlet gebruikt om de huidige cultuur instellingen op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-121">The first command uses the `Get-Culture` cmdlet to get the current culture settings on the computer.</span></span>
<span data-ttu-id="5f4d8-122">Het resulterende cultuur object wordt opgeslagen in de `$C` variabele.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-122">It stores the resulting culture object in the `$C` variable.</span></span>

<span data-ttu-id="5f4d8-123">Met de tweede opdracht worden alle eigenschappen van het object Culture weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-123">The second command displays all of the properties of the culture object.</span></span> <span data-ttu-id="5f4d8-124">Er wordt een pijplijn operator ( `|` ) gebruikt om het Culture-object naar `$C` de cmdlet te verzenden `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="5f4d8-124">It uses a pipeline operator (`|`) to send the culture object in `$C` to the `Format-List` cmdlet.</span></span> <span data-ttu-id="5f4d8-125">De para meter **Property** wordt gebruikt om alle ( `*` ) eigenschappen van het object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-125">It uses the **Property** parameter to display all (`*`) properties of the object.</span></span> <span data-ttu-id="5f4d8-126">Deze opdracht kan worden afgekort tot `$c | fl *` .</span><span class="sxs-lookup"><span data-stu-id="5f4d8-126">This command can be abbreviated as `$c | fl *`.</span></span>

<span data-ttu-id="5f4d8-127">De overige opdrachten verkennen de eigenschappen van het object Culture door punt notatie te gebruiken om de waarden van de object eigenschappen weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-127">The remaining commands explore the properties of the culture object by using dot notation to display the values of the object properties.</span></span> <span data-ttu-id="5f4d8-128">U kunt deze notatie gebruiken om de waarde van een eigenschap van het object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-128">You can use this notation to display the value of any property of the object.</span></span>

<span data-ttu-id="5f4d8-129">De derde opdracht maakt gebruik van punt notatie om de waarde van de eigenschap **Calendar** van het object Culture weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-129">The third command uses dot notation to display the value of the **Calendar** property of the culture object.</span></span>

<span data-ttu-id="5f4d8-130">De vierde opdracht maakt gebruik van de punt notatie om de waarde van de eigenschap **DataTimeFormat** van het object Culture weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-130">The fourth command uses dot notation to display the value of the **DataTimeFormat** property of the culture object.</span></span>

<span data-ttu-id="5f4d8-131">Veel object eigenschappen hebben eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-131">Many object properties have properties.</span></span> <span data-ttu-id="5f4d8-132">De vijfde opdracht maakt gebruik van de punt notatie om de waarde van de eigenschap **FirstDayOfWeek** van de eigenschap **date time format** weer te geven.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-132">The fifth command uses dot notation to display the value of the **FirstDayOfWeek** property of the **DateTimeFormat** property.</span></span>

### <span data-ttu-id="5f4d8-133">Voor beeld 3: een specifieke cultuur ophalen</span><span class="sxs-lookup"><span data-stu-id="5f4d8-133">Example 3: Get a specific culture</span></span>

<span data-ttu-id="5f4d8-134">Het object Culture info voor Frans in Frank rijk ophalen.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-134">Get the CultureInfo object for French in France.</span></span>

```powershell
Get-Culture -Name fr-FR
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1036             fr-FR            French (France)
```

## <span data-ttu-id="5f4d8-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5f4d8-135">PARAMETERS</span></span>

### <span data-ttu-id="5f4d8-136">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="5f4d8-136">-ListAvailable</span></span>

<span data-ttu-id="5f4d8-137">Haalt alle cult uren op die worden ondersteund door het huidige besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-137">Retrieves all cultures supported by the current operating system.</span></span>

<span data-ttu-id="5f4d8-138">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-138">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f4d8-139">-Name</span><span class="sxs-lookup"><span data-stu-id="5f4d8-139">-Name</span></span>

<span data-ttu-id="5f4d8-140">Haal een specifieke cultuur op op basis van de naam.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-140">Retrieve a specific culture based on the name.</span></span>

<span data-ttu-id="5f4d8-141">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-141">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5f4d8-142">-NoUserOverrides</span><span class="sxs-lookup"><span data-stu-id="5f4d8-142">-NoUserOverrides</span></span>

<span data-ttu-id="5f4d8-143">Gebruikers wijzigingen voor huidige cultuur negeren.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-143">Ignore user changes for current culture.</span></span>

<span data-ttu-id="5f4d8-144">Deze para meter is geïntroduceerd in Power shell 6,2.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-144">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CurrentCulture, Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f4d8-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f4d8-145">CommonParameters</span></span>

<span data-ttu-id="5f4d8-146">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f4d8-147">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f4d8-148">INVOER</span><span class="sxs-lookup"><span data-stu-id="5f4d8-148">INPUTS</span></span>

### <span data-ttu-id="5f4d8-149">Geen</span><span class="sxs-lookup"><span data-stu-id="5f4d8-149">None</span></span>

<span data-ttu-id="5f4d8-150">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-150">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="5f4d8-151">UITVOER</span><span class="sxs-lookup"><span data-stu-id="5f4d8-151">OUTPUTS</span></span>

### <span data-ttu-id="5f4d8-152">System. Globalization. Culture info</span><span class="sxs-lookup"><span data-stu-id="5f4d8-152">System.Globalization.CultureInfo</span></span>

<span data-ttu-id="5f4d8-153">`Get-Culture` retourneert een object dat de huidige cultuur vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-153">`Get-Culture` returns an object that represents the current culture.</span></span>

## <span data-ttu-id="5f4d8-154">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="5f4d8-154">NOTES</span></span>

<span data-ttu-id="5f4d8-155">U kunt ook de `$PsCulture` variabelen en gebruiken `$PsUICulture` .</span><span class="sxs-lookup"><span data-stu-id="5f4d8-155">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="5f4d8-156">De `$PsCulture` variabele bevat de naam van de huidige cultuur en de `$PsUICulture` variabele bevat de naam van de huidige gebruikersinterface cultuur.</span><span class="sxs-lookup"><span data-stu-id="5f4d8-156">The `$PsCulture` variable stores the name of the current culture and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="5f4d8-157">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="5f4d8-157">RELATED LINKS</span></span>

[<span data-ttu-id="5f4d8-158">Set-Culture</span><span class="sxs-lookup"><span data-stu-id="5f4d8-158">Set-Culture</span></span>](/powershell/module/international/set-culture)

[<span data-ttu-id="5f4d8-159">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="5f4d8-159">Get-UICulture</span></span>](Get-UICulture.md)
