---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-host?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Host
ms.openlocfilehash: 15305de9512a45a92242c283f60f6fd36b80fbe3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93247169"
---
# Get-Host

## SAMENVATTING
Hiermee wordt een object opgehaald dat het huidige host-programma vertegenwoordigt.

## SYNTAXIS

```
Get-Host [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Host` cmdlet haalt een object op dat staat voor het programma dat als host fungeert voor Windows Power shell.

De standaard weergave bevat het versie nummer van Windows Power shell en de huidige regio-en taal instellingen die de host gebruikt, maar het object host bevat een schat aan informatie, inclusief gedetailleerde informatie over de versie van Windows Power shell die momenteel wordt uitgevoerd en de huidige cultuur-en GEBRUIKERSINTERFACE cultuur van Windows Power shell. U kunt deze cmdlet ook gebruiken voor het aanpassen van de functies van de gebruikers interface van het gast programma, zoals de tekst-en achtergrond kleuren.

## VOORBEELDEN

### Voor beeld 1: informatie over de host van de Power shell-console ophalen

```
PS C:\> Get-Host
Name             : ConsoleHost
Version          : 2.0
InstanceId       : e4e0ab54-cc5e-4261-9117-4081f20ce7a2
UI               : System.Management.Automation.Internal.Host.InternalHostUserInterface
CurrentCulture   : en-US
CurrentUICulture : en-US
PrivateData      : Microsoft.PowerShell.ConsoleHost+ConsoleColorProxy
IsRunspacePushed : False
Runspace         : System.Management.Automation.Runspaces.LocalRunspace
```

Met deze opdracht wordt informatie weer gegeven over de Windows Power shell-console, het huidige hostprogramma voor Windows Power shell in dit voor beeld. Het bevat de naam van de host, de versie van Windows Power shell die wordt uitgevoerd op de host en de huidige cultuur-en GEBRUIKERSINTERFACE cultuur.

De eigenschappen version, UI, CurrentCulture, CurrentUICulture, PrivateData en runs Pace bevatten elk een object met zeer nuttige eigenschappen. In latere voor beelden worden deze eigenschappen onderzocht.

### Voor beeld 2: het formaat van het Power shell-venster wijzigen

```powershell
PS C:\> $H = Get-Host
PS C:\> $Win = $H.UI.RawUI.WindowSize
PS C:\> $Win.Height = 10
PS C:\> $Win.Width  = 10
PS C:\> $H.UI.RawUI.Set_WindowSize($Win)
```

Met deze opdracht wordt het formaat van het Windows Power shell-venster gewijzigd in 10 pixels van 10 pixels.

### Voor beeld 3: de Power shell-versie voor de host ophalen

```powershell
PS C:\> (Get-Host).Version | Format-List -Property *
Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

Met deze opdracht wordt gedetailleerde informatie opgehaald over de versie van Windows Power shell die wordt uitgevoerd op de host.
U kunt deze waarden weer geven, maar niet wijzigen.

De versie-eigenschap van `Get-Host` bevat een **System. version** -object. Met deze opdracht wordt een pijplijn operator (|) gebruikt om het versie object naar de `Format-List` cmdlet te verzenden. De `Format-List` opdracht gebruikt de *eigenschap* para meter met de waarde all (*) om alle eigenschappen en eigenschaps waarden van het versie object weer te geven.

### Voor beeld 4: de huidige cultuur voor de host ophalen

```powershell
PS C:\> (Get-Host).CurrentCulture | Format-List -Property *
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
```

Met deze opdracht wordt gedetailleerde informatie over de huidige cultuur ingesteld voor Windows Power shell die wordt uitgevoerd op de host. Dit is dezelfde informatie die wordt geretourneerd door de `Get-Culture` cmdlet.

Op dezelfde manier retourneert de eigenschap **CurrentUICulture** hetzelfde object `Get-UICulture` als dat retourneert.

De eigenschap **CurrentCulture** van het object host bevat een object **System. Globalization. Culture info** . Met deze opdracht wordt een pijplijn operator (|) gebruikt om het **Culture info** -object naar de cmdlet te verzenden `Format-List` . De `Format-List` opdracht maakt gebruik van de *eigenschap* para meter met de waarde all (*) om alle eigenschappen en eigenschapwaarden van het **Culture info** -object weer te geven.

### Voor beeld 5: de date time format voor de huidige cultuur ophalen

```powershell
PS C:\> (Get-Host).CurrentCulture.DateTimeFormat | Format-List -Property *
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
```

Met deze opdracht wordt gedetailleerde informatie geretourneerd over de date time format van de huidige cultuur die wordt gebruikt voor Windows Power shell.

De eigenschap **CurrentCulture** van het object host bevat een **Culture info** -object dat op zijn beurt een groot aantal nuttige eigenschappen heeft. De eigenschap **date time format** bevat onder andere een **DateTimeFormatInfo** -object met veel nuttige eigenschappen.

Gebruik de cmdlet om het type van een object te vinden dat is opgeslagen in een object eigenschap `Get-Member` . Gebruik de cmdlet om de eigenschaps waarden van het object weer te geven `Format-List` .

### Voor beeld 6: de eigenschap RawUI voor de host ophalen

```
PS C:\> (Get-Host).UI.RawUI | Format-List -Property *
ForegroundColor       : DarkYellow
BackgroundColor       : DarkBlue
CursorPosition        : 0,390
WindowPosition        : 0,341
CursorSize            : 25
BufferSize            : 120,3000
WindowSize            : 120,50
MaxWindowSize         : 120,81
MaxPhysicalWindowSize : 182,81
KeyAvailable          : False
WindowTitle           : Windows PowerShell 2.0 (04/11/2008 00:08:14)
```

Met deze opdracht worden de eigenschappen van de eigenschap **RawUI** van het object host weer gegeven. Door deze waarden te wijzigen, kunt u de weer gave van het host-programma wijzigen.

### Voor beeld 7: de achtergrond kleur voor de Power shell-console instellen

```powershell
PS C:\> (Get-Host).UI.RawUI.BackgroundColor = "Black"
PS C:\> cls
```

Met deze opdrachten wordt de achtergrond kleur van de Windows Power shell-console gewijzigd in zwart. De **CLS** -opdracht is een alias voor de `Clear-Host` functie, waardoor het scherm wordt gewist en het hele scherm wordt gewijzigd in de nieuwe kleur.

Deze wijziging is alleen effectief in de huidige sessie. Als u de achtergrond kleur van de console voor alle sessies wilt wijzigen, voegt u de opdracht toe aan uw Windows Power shell-profiel.

### Voor beeld 8: de achtergrond kleur voor fout berichten instellen

```
PS C:\> $Host.PrivateData.ErrorBackgroundColor = "white"
```

Met deze opdracht wordt de achtergrond kleur van fout berichten gewijzigd in wit.

Met deze opdracht wordt de `$Host` Automatische variabele gebruikt, die het object host bevat voor het huidige host-programma. `Get-Host` retourneert hetzelfde object dat `$Host` bevat, zodat u ze kunt gebruiken.

Deze opdracht maakt gebruik van de eigenschap **PrivateData** van `$Host` als de eigenschap ErrorBackgroundColor. Om alle eigenschappen van het object in de te bekijken `$Host` . Eigenschap PrivateData, type `$host.privatedata | format-list *` .

## PARAMETERS

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. internal. host. InternalHost

`Get-Host` retourneert het object **System. Management. Automation. internal. host. InternalHost** .

## OPMERKINGEN

De `$Host` Automatische variabele bevat hetzelfde object dat `Get-Host` retourneert, en u kunt het op dezelfde manier gebruiken. Op dezelfde manier `$PSCulture` bevatten de en `$PSUICulture` automatische variabelen dezelfde objecten die de eigenschappen CurrentCulture en CurrentUICulture van het object host bevatten. U kunt deze functies door elkaar gebruiken.

Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Wissen-host](../Microsoft.PowerShell.Core/Clear-Host.md)

[Read-host](Read-Host.md)

[Write-host](Write-Host.md)
