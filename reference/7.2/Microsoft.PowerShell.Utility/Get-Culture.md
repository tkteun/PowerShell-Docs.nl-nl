---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: dc49f153adc22b7c2c943a4cc529ac155561228a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705825"
---
# Get-Culture

## SAMENVATTING
Hiermee wordt de huidige cultuur ingesteld in het besturings systeem.

## SYNTAXIS

### CurrentCulture (standaard)

```
Get-Culture [-NoUserOverrides] [<CommonParameters>]
```

### Name

```
Get-Culture [-Name <String[]>] [-NoUserOverrides] [<CommonParameters>]
```

### ListAvailable

```
Get-Culture [-ListAvailable] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Culture` cmdlet haalt informatie op over de huidige cultuur instellingen. Dit omvat informatie over de huidige taal instellingen op het systeem, zoals de toetsenbord indeling en de weer gave-indeling van items zoals getallen, valuta en datums.

U kunt ook de `Get-UICulture` -cmdlet gebruiken, waarmee de huidige gebruikersinterface cultuur op het systeem wordt opgehaald en de cmdlet [set-Culture](/powershell/module/international/set-culture) in de module International. De cultuur gebruikers interface (UI) bepaalt welke teken reeksen worden gebruikt voor elementen van de gebruikers interface, zoals menu's en berichten.

## VOORBEELDEN

### Voor beeld 1: Cultuur instellingen ophalen

```powershell
Get-Culture
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

Met deze opdracht wordt informatie weer gegeven over de land instellingen op de computer.

### Voor beeld 2: de eigenschappen van een cultuur object opmaken

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

In dit voor beeld wordt de enorme hoeveelheid gegevens in het object Culture gedemonstreerd. Hierin ziet u hoe de eigenschappen en subeigenschappen van het object worden weer gegeven.

Met de eerste opdracht wordt de `Get-Culture` cmdlet gebruikt om de huidige cultuur instellingen op de computer op te halen.
Het resulterende cultuur object wordt opgeslagen in de `$C` variabele.

Met de tweede opdracht worden alle eigenschappen van het object Culture weer gegeven. Er wordt een pijplijn operator ( `|` ) gebruikt om het Culture-object naar `$C` de cmdlet te verzenden `Format-List` . De para meter **Property** wordt gebruikt om alle ( `*` ) eigenschappen van het object weer te geven. Deze opdracht kan worden afgekort tot `$c | fl *` .

De overige opdrachten verkennen de eigenschappen van het object Culture door punt notatie te gebruiken om de waarden van de object eigenschappen weer te geven. U kunt deze notatie gebruiken om de waarde van een eigenschap van het object weer te geven.

De derde opdracht maakt gebruik van punt notatie om de waarde van de eigenschap **Calendar** van het object Culture weer te geven.

De vierde opdracht maakt gebruik van de punt notatie om de waarde van de eigenschap **DataTimeFormat** van het object Culture weer te geven.

Veel object eigenschappen hebben eigenschappen. De vijfde opdracht maakt gebruik van de punt notatie om de waarde van de eigenschap **FirstDayOfWeek** van de eigenschap **date time format** weer te geven.

### Voor beeld 3: een specifieke cultuur ophalen

Het object Culture info voor Frans in Frank rijk ophalen.

```powershell
Get-Culture -Name fr-FR
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1036             fr-FR            French (France)
```

## PARAMETERS

### -ListAvailable

Haalt alle cult uren op die worden ondersteund door het huidige besturings systeem.

Deze para meter is ge??ntroduceerd in Power shell 6,2.

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

### -Name

Haal een specifieke cultuur op op basis van de naam.

Deze para meter is ge??ntroduceerd in Power shell 6,2.

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

### -NoUserOverrides

Gebruikers wijzigingen voor huidige cultuur negeren.

Deze para meter is ge??ntroduceerd in Power shell 6,2.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Globalization. Culture info

`Get-Culture` retourneert een object dat de huidige cultuur vertegenwoordigt.

## OPMERKINGEN

U kunt ook de `$PsCulture` variabelen en gebruiken `$PsUICulture` . De `$PsCulture` variabele bevat de naam van de huidige cultuur en de `$PsUICulture` variabele bevat de naam van de huidige gebruikersinterface cultuur.

## GERELATEERDE KOPPELINGEN

[Set-Culture](/powershell/module/international/set-culture)

[Get-UICulture](Get-UICulture.md)
