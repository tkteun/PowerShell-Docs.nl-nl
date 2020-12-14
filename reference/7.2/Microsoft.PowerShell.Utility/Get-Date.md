---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 8c0a1b7a14f5dfa071a85808f5d7dfba4d06048e
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514970"
---
# Get-Date

## SAMENVATTING
Hiermee worden de huidige datum en tijd opgehaald.

## SYNTAXIS

### Datum (standaard)

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### DateUFormat

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### UnixTimeSeconds

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### UnixTimeSecondsUFormat

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Date` cmdlet haalt een **DateTime** -object op dat staat voor de huidige datum of een datum die u opgeeft. `Get-Date` de datum en tijd in verschillende .NET-en UNIX-indelingen kunnen worden ingedeeld. U kunt gebruiken `Get-Date` voor het genereren van een teken reeks voor datum of tijd en vervolgens de teken reeks verzenden naar andere cmdlets of Program ma's.

`Get-Date` gebruikt de instellingen van de computer cultuur om te bepalen hoe de uitvoer wordt geformatteerd. Gebruik om de instellingen van uw computer weer te geven `(Get-Culture).DateTimeFormat` .

## VOORBEELDEN

### Voor beeld 1: de huidige datum en tijd ophalen

In dit voor beeld `Get-Date` worden de huidige systeem datum en-tijd weer gegeven. De uitvoer bevindt zich in de notatie voor lange en lange tijd.

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### Voor beeld 2: elementen van de huidige datum en tijd ophalen

In dit voor beeld ziet u hoe u kunt gebruiken `Get-Date` om het datum-of tijd-element op te halen. De para meter gebruikt de argumenten **datum**, **tijd** of **datum/** tijd.

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

`Get-Date` gebruikt de para meter **DisplayHint** met het **datum** argument om alleen de datum op te halen.

### Voor beeld 3: de datum en tijd ophalen met een specificatie van .NET-indeling

In dit voor beeld wordt een .NET-indelings specificatie gebruikt om de indeling van de uitvoer aan te passen. De uitvoer is een **teken reeks** object.

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

`Get-Date` gebruikt de **indelings** parameter om verschillende indelings aanduidingen op te geven.

De .NET-indelings specificaties die in dit voor beeld worden gebruikt, zijn als volgt gedefinieerd:

| Aanduiding |                      Definitie                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | Dag van de week-volledige naam                           |
| `MM`      | Maandnummer                                          |
| `dd`      | Dag van de maand: 2 cijfers                           |
| `yyyy`    | Jaar met viercijferige notatie                                |
| `HH:mm`   | Tijd in 24-uurs notatie-geen seconden                    |
| `K`       | Tijd zone-offset van Universal Time Coordinate (UTC) |

Zie [aangepaste datum-en tijd notatie reeksen](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)voor meer informatie over .net-indelings specificaties.

### Voor beeld 4: de datum en tijd ophalen met een UFormat-aanduiding

In dit voor beeld worden verschillende **UFormat** -indelings specificaties gebruikt voor het aanpassen van de indeling van de uitvoer.
De uitvoer is een **teken reeks** object.

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

`Get-Date` maakt gebruik van de para meter **UFormat** om verschillende indelings specificaties op te geven.

De **UFormat** -indelings specificaties die in dit voor beeld worden gebruikt, zijn als volgt gedefinieerd:

| Aanduiding |                      Definitie                       |
| --------- | ----------------------------------------------------- |
| `%A`      | Dag van de week-volledige naam                           |
| `%m`      | Maandnummer                                          |
| `%d`      | Dag van de maand: 2 cijfers                           |
| `%Y`      | Jaar met viercijferige notatie                                |
| `%R`      | Tijd in 24-uurs notatie-geen seconden                    |
| `%Z`      | Tijd zone-offset van Universal Time Coordinate (UTC) |

Zie de sectie [opmerkingen](#notes) voor een lijst met geldige indelings specificaties voor **UFormat** .

### Voor beeld 5: de dag van een datum van het jaar ophalen

In dit voor beeld wordt een eigenschap gebruikt om de numerieke dag van het jaar op te halen.

De Gregoriaanse kalender heeft 365 dagen, met uitzonde ring van schrikkel jaren die 366 dagen lang zijn. Zo is 31 december 2020 dag 366.

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

`Get-Date` gebruikt drie para meters om de datum op te geven: **jaar**, **maand** en **dag**. De opdracht wordt verpakt met haakjes zodat het resultaat door de eigenschap **DAYOFYEAR** wordt geëvalueerd.

### Voor beeld 6: controleren of een datum is aangepast aan zomer tijd

In dit voor beeld wordt een Booleaanse methode gebruikt om te controleren of een datum wordt gecorrigeerd met zomer tijd.

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

Een variabele, `$DST` slaat het resultaat van op `Get-Date` . `$DST` maakt gebruik van de methode **IsDaylightSavingTime** om te testen of de datum wordt aangepast aan zomer tijd.

### Voor beeld 7: de huidige tijd converteren naar UTC-tijd

In dit voor beeld wordt de huidige tijd geconverteerd naar UTC-tijd. De UTC-offset voor de land instelling van het systeem wordt gebruikt om de tijd om te zetten. Een tabel in de sectie [notities](#notes) bevat een lijst met geldige indelings specificaties voor **UFormat** .

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

`Get-Date` maakt gebruik van de para meter **UFormat** met indelings specificaties om de huidige systeem datum en-tijd weer te geven. De indelings aanduiding **% Z** vertegenwoordigt de UTC-afwijking van **-07**.

De `$Time` variabele bevat de huidige systeem datum en-tijd. `$Time` maakt gebruik van de methode **ToUniversalTime ()** om de tijd om te zetten op basis van de UTC-afwijking van de computer.

### Voor beeld 8: een tijds tempel maken

In dit voor beeld maakt een indelings aanduiding een **teken reeks** object voor een tijds tempel voor een directory naam. De tijds tempel bevat de datum, tijd en UTC-offset.

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

De `$timestamp` variabele bevat de resultaten van een `Get-Date` opdracht. `Get-Date` gebruikt de **indelings** parameter met de indelings specificatie van kleine letters `o` om een **teken reeks** object voor een tijds tempel te maken. Het object wordt naar de pijp lijn verzonden `ForEach-Object` . Een **script Block** bevat de `$_` variabele die het huidige pijplijn object vertegenwoordigt. De tijds tempel teken reeks wordt gescheiden door dubbele punten die worden vervangen door punten.

`New-Item` gebruikt de para meter **Path** om de locatie voor een nieuwe map op te geven. Het pad bevat de `$timestamp` variabele als de mapnaam. De **type** parameter geeft aan dat er een map is gemaakt.

### Voor beeld 9: een Unix-Time Stamp converteren

In dit voor beeld wordt een Unix-tijd (vertegenwoordigd door het aantal seconden sinds 1970-01-01 0:00:00) geconverteerd naar DateTime.

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### Voor beeld 10: een datum waarde Retour neren die als UTC wordt geïnterpreteerd

In dit voor beeld ziet u hoe u een datum waarde als UTC-equivalent kunt interpreteren. Voor dit voor beeld is deze computer ingesteld op **Pacific Standard Time**. Standaard worden `Get-Date` waarden voor die tijd zone geretourneerd. Gebruik de para meter **AsUTC** om de waarde te converteren naar de EQUIVALENTe UTC-tijd.

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

## PARAMETERS

### -AsUTC

Hiermee wordt de datum waarde geconverteerd naar de equivalente tijd in UTC.

Deze para meter is geïntroduceerd in Power shell 7,1.

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

### -Datum

Hiermee geeft u een datum en tijd op. Tijd is optioneel en als deze niet is opgegeven, wordt 00:00:00 geretourneerd.

Voer de datum en tijd in met een standaard indeling voor de systeem land instelling.

Bijvoorbeeld in Amerikaans Engels:

`Get-Date -Date "6/25/2019 12:30:22"` retourneert dinsdag, 25 juni 2019 12:30:22

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

### -Dag

Hiermee geeft u de dag van de maand op die wordt weer gegeven. Voer een waarde in van 1 tot 31.

Als de opgegeven waarde groter is dan het aantal dagen in een maand, voegt Power shell het aantal dagen toe aan de maand. Zo wordt bijvoorbeeld `Get-Date -Month 2 -Day 31` **3 maart**, niet **31 februari**, weer gegeven.

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

### -DisplayHint

Hiermee wordt bepaald welke elementen van de datum en tijd worden weer gegeven.

De geaccepteerde waarden zijn als volgt:

- **Datum**: alleen de datum wordt weer gegeven
- **Tijd**: alleen de tijd weer geven
- Datum **tijd**: hier worden de datums en tijden weer gegeven

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

### -Indeling

Hier worden de datum en tijd weer gegeven in de Microsoft .NET Framework-indeling, zoals aangegeven in de indelings specificatie.
De **notatie** parameter voert een **teken reeks** object uit.

Zie [aangepaste datum-en tijd notatie reeksen](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8)voor een lijst met beschik bare .net-indelings aanduidingen.

Wanneer de **notatie** para meter wordt gebruikt, worden `Get-Date` alleen de eigenschappen van het **DateTime** -object opgehaald die nodig zijn om de datum weer te geven. Als gevolg hiervan zijn sommige eigenschappen en methoden van **DateTime** -objecten mogelijk niet beschikbaar.

Vanaf Power shell 5,0 kunt u de volgende extra notaties gebruiken als waarden voor de **notatie** parameter.

- **FileDate**. Een bestands-of pad-gebruiks vriendelijke representatie van de huidige datum in de lokale tijd. De notatie is `yyyyMMdd` (hoofdletter gevoelig, met een jaar van vier cijfers, een maand van 2 cijfers en een dag van 2 cijfers). Bijvoorbeeld:
  20190627.

- **FileDateUniversal**. Een bestands-of pad-beschrijvende weer gave van de huidige datum in Universal Time (UTC). De notatie is `yyyyMMddZ` (hoofdletter gevoelig, met een jaar van vier cijfers, een maand van 2 cijfers, een dag van 2 cijfers en de letter `Z` als de UTC-indicator). Bijvoorbeeld: 20190627Z.

- **FileDateTime**. Een bestands-of pad-gebruiks vriendelijke weer gave van de huidige datum en tijd in de lokale tijd, in 24-uurs notatie. De notatie is `yyyyMMddTHHmmssffff` (hoofdletter gevoelig, met behulp van een jaar van vier cijfers, een maand van 2 cijfers, een dag van 2 cijfers, de letter als een tijd scheidings teken, een uur van twee cijfers, een minuut van twee cijfers en een `T` milliseconden van 4 cijfers). Bijvoorbeeld: 20190627T0840107271.

- **FileDateTimeUniversal**. Een bestands-of pad-gebruiks vriendelijke weer gave van de huidige datum en tijd in UTC (Universal Time), in 24-uurs notatie. De notatie is `yyyyMMddTHHmmssffffZ` (hoofdletter gevoelig, met behulp van een jaar van vier cijfers, een maand van twee cijfers, de letter `T` als een tijd scheidings teken, een uur van twee cijfers, een minuut van twee cijfers, een tweede milliseconde en de letter `Z` als de UTC-indicator). Bijvoorbeeld: 20190627T1540500718Z.

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

### -Uur

Hiermee geeft u het uur op dat wordt weer gegeven. Voer een waarde tussen 0 en 23 in.

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

### -Milliseconde

Geeft de milliseconden in de datum aan. Voer een waarde in tussen 0 en 999.

Deze para meter is geïntroduceerd in Power Shell 3,0.

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

### -Minuut

Hiermee geeft u de minuut op die wordt weer gegeven. Voer een waarde in tussen 0 en 59.

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

### -Maand

Hiermee geeft u de maand op die wordt weer gegeven. Voer een waarde tussen 1 en 12 in.

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

### -Seconde

Hiermee geeft u de seconde op die wordt weer gegeven. Voer een waarde in tussen 0 en 59.

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

### -UFormat

Hiermee worden de datum en tijd in de UNIX-indeling weer gegeven. De para meter **UFormat** voert een teken reeks object uit.

**UFormat** -aanduidingen worden voorafgegaan door een procent teken ( `%` ), bijvoorbeeld, `%m` , `%d` en `%Y` . De sectie [notities](#notes) bevat een tabel met geldige **UFormat-aanduidingen**.

Wanneer de para meter **UFormat** wordt gebruikt, worden `Get-Date` alleen de eigenschappen van het object **DateTime** opgehaald die nodig zijn om de datum weer te geven. Als gevolg hiervan zijn sommige eigenschappen en methoden van **DateTime** -objecten mogelijk niet beschikbaar.

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

### -UnixTimeSeconds

De datum en tijd weer gegeven in seconden sinds 1 januari 1970, 0:00:00.

Deze para meter is geïntroduceerd in Power shell 7,1.

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

### -Jaar

Hiermee geeft u het jaar op dat wordt weer gegeven. Voer een waarde in van 1 tot en met 9999.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Pijplijn invoer

`Get-Date` accepteert invoer van de pijp lijn. Bijvoorbeeld `Get-ChildItem | Get-Date`.

## UITVOER

### System. DateTime of System. String

`Get-Date` retourneert een **DateTime** -object, behalve wanneer de **notatie** -en **UFormat** -para meters worden gebruikt. De **notatie** of para meters van de **UFormat** retour neren **teken reeks** objecten.

Wanneer een **DateTime** -object vanuit de pijp lijn naar een cmdlet wordt verzonden `Add-Content` , zoals de teken reeks invoer verwacht, converteert Power shell het object naar een **teken reeks** object.

Met de-methode wordt `(Get-Date).ToString()` een **DateTime** -object omgezet in een **teken reeks** object.

Als u de eigenschappen en methoden van een object wilt weer geven, verzendt u het object omlaag in de pijp lijn `Get-Member` .
Bijvoorbeeld `Get-Date | Get-Member`.

## OPMERKINGEN

**DateTime** -objecten hebben een lange datum en lange tijd notatie voor de systeem land instelling.

De geldige **UFormat-specificaties** worden weer gegeven in de volgende tabel:

| Indelings aanduiding |                                 Betekenis                     |         Voorbeeld          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | Dag van de week-volledige naam                                             | Maandag                   |
| `%a` | Dag van de week, korte naam                                      | Ma                      |
| `%B` | Maand naam-volledig                                                       | Januari                  |
| `%b` | Maand naam-afgekort                                                | Jan                      |
| `%C` | Jaar                                                                 | 20 voor 2019              |
| `%c` | Datum en tijd-afgekort                                             | Do jun 27 08:44:18 2019 |
| `%D` | Datum in de notatie mm/dd/jj                                                 | 06/27/19                 |
| `%d` | Dag van de maand: 2 cijfers                                             | 05                       |
| `%e` | Dag van de maand, voorafgegaan door een spatie als er slechts één cijfer           | \<space\>5,0               |
| `%F` | Datum in de notatie JJJJ-MM-DD, gelijk aan% Y-% m-% d (ISO 8601-datum notatie) | 2019-06-27               |
| `%G` | Hetzelfde als ' Y '                                                             |                          |
| `%g` | Hetzelfde als ' y '                                                             |                          |
| `%H` | Uur in 24-uurs notatie                                                  | 17                       |
| `%h` | Hetzelfde als ' b '                                                             |                          |
| `%I` | Uur in 12-uurs notatie                                                  | 05                       |
| `%j` | Dag van het jaar                                                         | 1-366                    |
| `%k` | Hetzelfde als ' H '                                                             |                          |
| `%l` | Hetzelfde als ' I ' (hoofd letters I)                                              | 05                       |
| `%M` | Minuten                                                                 | 35                       |
| `%m` | Maandnummer                                                            | 06                       |
| `%n` | teken voor nieuwe regel                                                       |                          |
| `%p` | AM of PM                                                                |                          |
| `%R` | Tijd in 24-uurs notatie-geen seconden                                      | 17:45                    |
| `%r` | Tijd in 12-uurs notatie                                                  | 09:15:36 UUR              |
| `%S` | Seconden                                                                 | 05                       |
| `%s` | Seconden verstreken sinds 1 januari 1970 00:00:00                          | 1150451174               |
| `%t` | Teken voor horizontale tab                                                |                          |
| `%T` | Tijd in 24-uurs notatie                                                  | 17:45:52                 |
| `%U` | Hetzelfde als ' W '                                                             |                          |
| `%u` | Dag van het week nummer                                                | Zondag = 0               |
| `%V` | Week van het jaar                                                        | 01-53                    |
| `%w` | Hetzelfde als ' u '                                                             |                          |
| `%W` | Week van het jaar                                                        | 00-52                    |
| `%X` | Hetzelfde als 'T '                                                             |                          |
| `%x` | Datum in de standaard notatie voor de land instelling                                      | 06/27/19 voor Engels-US  |
| `%Y` | Jaar met viercijferige notatie                                                  | 2019                     |
| `%y` | Jaar met een notatie van twee cijfers                                                  | 19                       |
| `%Z` | Tijd zone-offset van Universal Time Coordinate (UTC)                   | -07                      |

## GERELATEERDE KOPPELINGEN

[ForEach-object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-cultuur](Get-Culture.md)

[Get-member](Get-Member.md)

[Nieuw-item](../Microsoft.PowerShell.Management/New-Item.md)

[Nieuw-time span](New-TimeSpan.md)

[Set-date](Set-Date.md)
