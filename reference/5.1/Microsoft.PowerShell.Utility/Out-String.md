---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: 6bcda4d1796f2a2ccd61469523443f90ddde5e29
ms.sourcegitcommit: c8d1ffeab215e74e87ea1b0af8cd606c1a6a80ab
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/29/2020
ms.locfileid: "93251959"
---
# Out-String

## SAMENVATTING
Voert invoer objecten uit als teken reeksen.

## SYNTAXIS

### Alles

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Out-String` cmdlet worden invoer objecten geconverteerd naar teken reeksen. `Out-String`De teken reeksen worden standaard gecumuleerd en geretourneerd als een enkele teken reeks, maar u kunt de **Stream** -para meter gebruiken om direct `Out-String` één regel tegelijk te retour neren of om een matrix van teken reeksen te maken. Met deze cmdlet kunt u de teken reeks uitvoer zoeken en manipuleren, net zoals bij traditionele schalen, wanneer het bewerken van objecten minder handig is.

## VOORBEELDEN

### Voor beeld 1: de huidige cultuur ophalen en de gegevens converteren naar teken reeksen

In dit voor beeld worden de regionale instellingen voor de huidige gebruiker opgehaald en worden de object gegevens geconverteerd naar teken reeksen.

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

De `$C` variabele bevat een **Selected.System. Globalisatie. Culture info** -object. Het object is het resultaat van het `Get-Culture` verzenden van de uitvoer van de pijp lijn naar `Select-Object` . De **eigenschaps** parameter maakt gebruik van een asterisk ( `*` )-Joker teken om alle eigenschappen op te geven die in het object zijn opgenomen.

`Out-String` maakt gebruik van de para meter **input object** om het **Culture info** -object op te geven dat is opgeslagen in de `$C` variabele. De objecten in `$C` worden geconverteerd naar een teken reeks.

> [!NOTE]
> Als u de matrix wilt weer geven `Out-String` , slaat u de uitvoer op in een variabele en gebruikt u een matrix index om de elementen weer te geven. Zie [about_Arrays](../microsoft.powershell.core/about/about_arrays.md)voor meer informatie over de matrix index.
>
> `$str = Out-String -InputObject $C -Width 100`

### Voor beeld 2: werken met objecten

In dit voor beeld wordt het verschil gedemonstreerd tussen het werken met objecten en het werken met teken reeksen. Met de opdracht wordt een alias weer gegeven met de tekst **GCM** , de alias voor `Get-Command` .

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

`Get-Alias` Hiermee worden de objecten **System. Management. Automation. AliasInfo** , een voor elke alias, opgehaald en worden de objecten van de pijp lijn omlaag verzonden. `Out-String` gebruikt de **Stream** -para meter om elk object te converteren naar een teken reeks, in plaats van alle objecten te koppelen aan één teken reeks. De **System. String** -objecten worden via de pijp lijn verzonden en er `Select-String` wordt gebruikgemaakt van de **patroon** parameter om overeenkomsten te vinden voor de tekst **GCM**.

> [!NOTE]
> Als u de **Stream** -para meter weglaat, wordt met de opdracht alle aliassen weer gegeven, omdat `Select-String` de tekst **GCM** wordt gevonden in de teken reeks die `Out-String` als resultaat wordt gegeven.

### Voor beeld 3: gebruik de para meter breedte om afkap ping te voor komen.

Hoewel de meeste uitvoer van `Out-String` wordt ingepakt naar de volgende regel, zijn er scenario's waarin de uitvoer wordt afgekapt door het format teren systeem voordat deze wordt door gegeven aan `Out-String` . U kunt afkap ping vermijden met de para meter **width** .

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

### -Input object

Geeft aan welke objecten moeten worden geschreven naar een teken reeks. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

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

### -Stream

Geeft aan dat de cmdlet een afzonderlijke teken reeks voor elke regel van een invoer object verzendt. Standaard worden de teken reeksen voor elk object verzameld en als één teken reeks verzonden.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Breedte

Hiermee geeft u het aantal tekens in elke regel van uitvoer op. Eventuele extra tekens worden ingepakt naar de volgende regel of worden afgekapt, afhankelijk van de gebruikte formatter-cmdlet. De para meter **width** is alleen van toepassing op objecten die worden opgemaakt. Als u deze para meter weglaat, wordt de breedte bepaald door de kenmerken van het hostprogramma. In Terminal (console) Windows wordt de breedte van het huidige venster als de standaard waarde gebruikt. Power shell-console Windows standaard ingesteld op een breedte van 80 tekens tijdens de installatie.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt objecten naar beneden verplaatsen in de pijp lijn `Out-String` .

## UITVOER

### System. String

`Out-String` retourneert de teken reeks die wordt gemaakt op basis van het invoer object.

## OPMERKINGEN

De cmdlets die de term bevatten, hebben `Out` geen objecten. `Out`Met de cmdlets worden objecten verzonden naar de formatter voor het opgegeven weergave doel.

## GERELATEERDE KOPPELINGEN

[about_Formatting](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[Out-standaard](../Microsoft.PowerShell.Core/Out-Default.md)

[Out-file](Out-File.md)

[Out-host](../Microsoft.PowerShell.Core/Out-Host.md)

[Out-Null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-GridView](Out-GridView.md)

[Out-Printer](Out-Printer.md)
