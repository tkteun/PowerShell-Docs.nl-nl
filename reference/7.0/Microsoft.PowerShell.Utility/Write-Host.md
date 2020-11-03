---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: d6707a9f5c54b736d0b917d453416ccdb0850baa
ms.sourcegitcommit: 758e6dbb428295698d4852b3e19f5d03deade037
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/15/2020
ms.locfileid: "93251919"
---
# Write-Host

## SAMENVATTING

Hiermee wordt de aangepaste uitvoer naar een host geschreven.

## SYNTAXIS

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## BESCHRIJVING

Het `Write-Host` primaire doel van de cmdlet is het maken van een-op-(host)-alleen-weer gave-uitvoer, zoals het afdrukken van gekleurde tekst wanneer de gebruiker wordt gevraagd om in combi natie met [Read-host](Read-Host.md)te worden ingevoerd.
`Write-Host` maakt gebruik van de methode [toString ()](/dotnet/api/system.object.tostring) om de uitvoer te schrijven. Als u daarentegen gegevens naar de pijp lijn wilt uitvoeren, kunt u gebruikmaken van [Write-output](Write-Output.md) of impliciete uitvoer.

U kunt de kleur van tekst opgeven met behulp van de `ForegroundColor` para meter en u kunt de achtergrond kleur opgeven met behulp van de `BackgroundColor` para meter. Met de scheidings parameter kunt u een teken reeks opgeven die moet worden gebruikt voor het scheiden van weer gegeven objecten. Het specifieke resultaat is afhankelijk van het programma dat Power shell host.

> [!NOTE]
> Met ingang van Windows Power shell 5,0 `Write-Host` is een wrapper waarmee `Write-Information` u `Write-Host` de uitvoer naar de informatie stroom kunt verzenden. Hierdoor kan het **vastleggen** of **onderdrukken** van gegevens die zijn geschreven met behoud van `Write-Host` achterwaartse compatibiliteit.
>
> De `$InformationPreference` Voorkeurs variabele en de `InformationAction` algemene para meter zijn niet van invloed op `Write-Host` berichten. De uitzonde ring op deze regel is `-InformationAction Ignore` , waarmee uitvoer effectief wordt onderdrukt `Write-Host` . (zie "voor beeld 5")

## VOORBEELDEN

### Voor beeld 1: naar de console schrijven zonder een nieuwe regel toe te voegen

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

Met deze opdracht wordt de teken reeks ' geen nieuwe regel test ' weer gegeven met de `NoNewline` para meter.

Er wordt een tweede teken reeks geschreven, maar deze eindigt op dezelfde lijn als de eerste omdat de teken reeksen niet worden gescheiden door een nieuwe regel.

### Voor beeld 2: schrijven naar de-console en een scheidings teken toevoegen

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

Met deze opdracht worden de even nummers van twee tot en met 12 weer gegeven. De **scheidings** parameter wordt gebruikt om de teken reeks `, +2= ` (komma, spatie,, `+` `2` , `=` , spatie) toe te voegen.

### Voor beeld 3: schrijven met andere tekst-en achtergrond kleuren

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

Met deze opdracht worden de even nummers van twee tot en met 12 weer gegeven. De `ForegroundColor` para meter wordt gebruikt voor het uitvoeren van donker groene tekst en de `BackgroundColor` para meter om een witte achtergrond weer te geven.

### Voor beeld 4: schrijven met andere tekst-en achtergrond kleuren

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

Met deze opdracht wordt de teken reeks "rood op witte tekst" weer gegeven. De tekst is rood, zoals gedefinieerd door de `ForegroundColor` para meter. De achtergrond is wit, zoals gedefinieerd door de `BackgroundColor` para meter.

### Voor beeld 5: uitvoer van Write-Host onderdrukken

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

Met deze opdrachten wordt de uitvoer van de cmdlet in feite onderdrukt `Write-Host` . De eerste gebruikt de `InformationAction` para meter met de `Ignore` waarde om de uitvoer naar de informatie stroom te onderdrukken.
In het tweede voor beeld wordt de informatie stroom van de opdracht omgeleid naar de `$null` variabele, waardoor deze wordt onderdrukt.

## PARAMETERS

### -BackgroundColor

Hiermee geeft u de achtergrondkleur. Er is geen standaard waarde. De aanvaardbare waarden voor deze parameter zijn:

- Zwart
- DarkBlue
- DarkGreen
- DarkCyan
- DarkRed
- DarkMagenta
- DarkYellow
- Grijs
- DarkGray
- Blue
- Green
- Hoeveelheid
- Rood
- Magenta
- Geel
- Wit

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ForegroundColor

Geeft de tekst kleur aan. Er is geen standaard waarde. De aanvaardbare waarden voor deze parameter zijn:

- Zwart
- DarkBlue
- DarkGreen
- DarkCyan
- DarkRed
- DarkMagenta
- DarkYellow
- Grijs
- DarkGray
- Blue
- Green
- Hoeveelheid
- Rood
- Magenta
- Geel
- Wit

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Nieuwe regel

De teken reeks representaties van de invoer objecten worden samengevoegd om de uitvoer te vormen. Er worden geen spaties of nieuwe regels tussen de uitvoer teken reeksen ingevoegd. Er wordt geen nieuwe regel toegevoegd na de laatste uitvoer teken reeks.

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

### -Object

Objecten die moeten worden weer gegeven op de host.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Scheidings teken

Hiermee geeft u een scheidings teken reeks moet worden ingevoegd tussen objecten die worden weer gegeven door de host.

```yaml
Type: System.Object
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

### System. object

U kunt objecten pipeen die naar de host moeten worden geschreven.

## UITVOER

### Geen

`Write-Host` Hiermee worden de objecten naar de host verzonden. Er worden geen objecten geretourneerd. De host geeft echter de objecten weer die `Write-Host` ernaar worden verzonden.

## OPMERKINGEN

- Wanneer u een verzameling naar de host schrijft, worden elementen van de verzameling op dezelfde regel afgedrukt, gescheiden door één spatie. Dit kan worden overschreven met de **scheidings** parameter.

- Niet-primitieve gegevens typen zoals objecten met eigenschappen kunnen leiden tot onverwachte resultaten en bieden geen zinvolle uitvoer. Bijvoorbeeld, `Write-Host @{a = 1; b = 2}` wordt afgedrukt `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` op de host.

## GERELATEERDE KOPPELINGEN

[Wissen-host](../Microsoft.PowerShell.Core/Clear-Host.md)

[Out-host](../Microsoft.PowerShell.Core/Out-Host.md)

[Schrijf fouten opsporen](Write-Debug.md)

[Schrijf fout](Write-Error.md)

[Write-output](Write-Output.md)

[Schrijf voortgang](Write-Progress.md)

[Write-verbose](Write-Verbose.md)

[Waarschuwing voor schrijven](Write-Warning.md)
