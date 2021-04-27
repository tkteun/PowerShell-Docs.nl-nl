---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: 90f4a775b4a99ad9539645791521836a93351f22
ms.sourcegitcommit: 1e1535cb22d16de06f80beafe77a37a7c77de6d3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025703"
---
# Out-String

## Synopsis
Invoerobjecten worden uitgevoerd als een tekenreeks.

## Syntax

### NoNewLineFormatting (standaard)

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### StreamFormatting

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## Description

De `Out-String` cmdlet converteert invoerobjecten naar tekenreeksen. Standaard worden de tekenreeksen verzameld en als één tekenreeks retourneert, maar u kunt de Stream-parameter gebruiken om één regel per keer te retourneren of een matrix met tekenreeksen te `Out-String`  `Out-String` maken. Met deze cmdlet kunt u tekenreeksuitvoer zoeken en bewerken zoals in traditionele shells wanneer objectmanipulatie minder handig is.

## Voorbeelden

### Voorbeeld 1: De huidige cultuur op halen en de gegevens converteren naar tekenreeksen

In dit voorbeeld worden de regionale instellingen voor de huidige gebruiker opgetrokken en worden de objectgegevens ge converteert naar tekenreeksen.

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
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
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

De `$C` variabele slaat eenSelected.Sys **op. Globalization.CultureInfo-object.** Het -object is het resultaat van het `Get-Culture` verzenden van uitvoer in de pijplijn naar `Select-Object` . De **eigenschap** parameter maakt gebruik van een sterretje ( ) jokerteken om op te geven `*` alle eigenschappen zijn opgenomen in het object.

`Out-String` gebruikt de **parameter InputObject** om het object **CultureInfo op te** geven dat is opgeslagen in de variabele `$C` . De objecten in `$C` worden geconverteerd naar een tekenreeks.

> [!NOTE]
> Als u de `Out-String` matrix wilt weergeven, moet u de uitvoer opslaan in een variabele en een matrixindex gebruiken om de elementen weer te geven. Zie voor meer informatie over de matrixindex [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).
>
> `$str = Out-String -InputObject $C -Width 100`

### Voorbeeld 2: Werken met objecten

In dit voorbeeld wordt het verschil gedemonstreerd tussen het werken met objecten en het werken met tekenreeksen. De opdracht geeft een alias weer die de tekst **gcm** bevat, de alias voor `Get-Command` .

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

`Get-Alias` haalt de **System.Management.Automation.AliasInfo-objecten** op, één voor elke alias, en verzendt de objecten in de pijplijn. `Out-String` gebruikt de **Stream-parameter** om elk object te converteren naar een tekenreeks in plaats van alle objecten samen tevoegen in één tekenreeks.
De **System.String-objecten** worden naar de pijplijn verzonden en gebruiken de parameter Pattern om overeenkomsten voor de `Select-String` tekst **gcm te vinden.** 

> [!NOTE]
> Als u de **Stream-parameter** weglaten, de opdracht geeft alle aliassen omdat de tekst gcm in de enkele tekenreeks `Select-String` die  `Out-String` retourneert zoekt.

### Voorbeeld 3: gebruik de parameter Width om afzetting te voorkomen.

Hoewel de meeste uitvoer van naar de volgende regel wordt verpakt, zijn er scenario's waarin de uitvoer door het opmaaksysteem wordt afgekapt voordat deze wordt `Out-String` doorgegeven aan `Out-String` . U kunt afzetting voorkomen met behulp van de parameter **Width.**

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## PARAMETERS

### -InputObject

Hiermee geeft u de objecten moet worden geschreven naar een tekenreeks. Voer een variabele in die de objecten bevat of typ een opdracht of expressie die de objecten op haalt.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -NoNewline

Hiermee verwijdert u alle nieuwelijnen uit de uitvoer die is gegenereerd door de PowerShell-indeling. Nieuwelijnen die deel uitmaken van de tekenreeksobjecten blijven behouden.

Deze parameter is geïntroduceerd in PowerShell 6.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Stream

Standaard wordt één tekenreeks uitgevoerd die is opgemaakt zoals u deze zou zien in de console, inclusief lege kopteksten of `Out-String` nieuwe eindlijnen. Met **de parameter Stream** kan elke regel één voor één worden `Out-String` uitgevoerd. De enige uitzondering hierop zijn tekenreeksen met meerdere regel. In dat geval wordt `Out-String` de tekenreeks nog steeds uitgevoerd als één tekenreeks met meerderelines.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Breedte

Hiermee geeft u het aantal tekens in elke regel uitvoer. Eventuele extra tekens worden verpakt op de volgende regel of afgekapt, afhankelijk van de gebruikte cmdlet formatter. De **parameter Width** is alleen van toepassing op objecten die worden geformatteerd. Als u deze parameter weglaten, wordt de breedte bepaald door de kenmerken van het hostprogramma. In terminalvensters (console) wordt de huidige vensterbreedte gebruikt als de standaardwaarde. Windows in de PowerShell-console hebben standaard een breedte van 80 tekens bij de installatie.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INVOER

### System.Management.Automation.PSObject

U kunt objecten in de pijplijn verzenden naar `Out-String` .

## UITVOER

### System.String

`Out-String` retourneert de tekenreeks die wordt gemaakt op basis van het invoerobject.

## OPMERKINGEN

De cmdlets die het werkwoord `Out` bevatten, maken geen objecten op. De `Out` cmdlets verzenden objecten naar de formatter voor de opgegeven weergavebestemming.

## GERELATEERDE KOPPELINGEN

[about_Formatting](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[Standaardinstelling](../Microsoft.PowerShell.Core/Out-Default.md)

[Out-File](Out-File.md)

[Out-Host](../Microsoft.PowerShell.Core/Out-Host.md)

[Out-Null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-GridView](Out-GridView.md)

[Out-Printer](Out-Printer.md)
