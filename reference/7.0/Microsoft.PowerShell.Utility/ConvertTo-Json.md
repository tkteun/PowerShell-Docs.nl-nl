---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: f9c441249c2c096158dd2ffc4dc2bd65d6ecff6f
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729889"
---
# ConvertTo-Json

## SAMENVATTING
Converteert een object naar een tekenreeks in JSON-indeling.

## SYNTAXIS

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## BESCHRIJVING

De `ConvertTo-Json` cmdlet converteert elk .NET-object naar een tekenreeks in JavaScript Object Notation indeling (JSON). De eigenschappen worden geconverteerd naar veldnamen, de veldwaarden worden geconverteerd naar eigenschapswaarden en de methoden worden verwijderd.

Vervolgens kunt u de cmdlet gebruiken om een tekenreeks in JSON-indeling te converteren naar een JSON-object, dat eenvoudig kan `ConvertFrom-Json` worden beheerd in PowerShell.

Veel websites gebruiken JSON in plaats van XML om gegevens te serialiseren voor communicatie tussen servers en web-apps.

Deze cmdlet is geïntroduceerd in Windows PowerShell 3.0.

## VOORBEELDEN

### Voorbeeld 1

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
  "MinSupportedDateTime": "0001-01-01T00:00:00",
  "MaxSupportedDateTime": "9999-12-31T23:59:59.9999999",
  "AlgorithmType": 1,
  "CalendarType": 1,
  "Eras": [
    1
  ],
  "TwoDigitYearMax": 2029,
  "IsReadOnly": true
}
```

Met deze opdracht wordt de `ConvertTo-Json` cmdlet gebruikt om een Object CategorisianCalendar te converteren naar een tekenreeks in JSON-indeling.

### Voorbeeld 2

```powershell
Get-Date | ConvertTo-Json; Get-Date | ConvertTo-Json -AsArray
```

```Output
{
  "value": "2018-10-12T23:07:18.8450248-05:00",
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 11:07:18 PM"
}
[
  {
    "value": "2018-10-12T23:07:18.8480668-05:00",
    "DisplayHint": 2,
    "DateTime": "October 12, 2018 11:07:18 PM"
  }
]
```

In dit voorbeeld ziet u de uitvoer van `ConvertTo-Json` de cmdlet met en zonder de **asArray-switchparameter.** U ziet dat het tweede deel van de uitvoer tussen matrixhaken is verpakt.

### Voorbeeld 3

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

Deze opdracht toont het effect van het gebruik van de parameter **Compress** van `ConvertTo-Json` . De compressie is alleen van invloed op het uiterlijk van de tekenreeks, niet op de geldigheid ervan.

### Voorbeeld 4

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 10:55:32 PM",
  "Date": "2018-10-12T00:00:00-05:00",
  "Day": 12,
  "DayOfWeek": 5,
  "DayOfYear": 285,
  "Hour": 22,
  "Kind": 2,
  "Millisecond": 639,
  "Minute": 55,
  "Month": 10,
  "Second": 32,
  "Ticks": 636749817326397744,
  "TimeOfDay": {
    "Ticks": 825326397744,
    "Days": 0,
    "Hours": 22,
    "Milliseconds": 639,
    "Minutes": 55,
    "Seconds": 32,
    "TotalDays": 0.95523888627777775,
    "TotalHours": 22.925733270666665,
    "TotalMilliseconds": 82532639.774400011,
    "TotalMinutes": 1375.54399624,
    "TotalSeconds": 82532.6397744
  },
  "Year": 2018
}
```

In dit voorbeeld wordt de cmdlet gebruikt om een System.DateTime-object van de cmdlet te converteren naar een `ConvertTo-Json`  `Get-Date` tekenreeks in JSON-indeling. De opdracht gebruikt de `Select-Object` cmdlet om alle ( ) eigenschappen `*` van het **DateTime-object op te** halen. In de uitvoer ziet u de JSON-tekenreeks die is `ConvertTo-Json` geretourneerd.

### Voorbeeld 5

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : October 12, 2018 10:55:52 PM
Date        : 2018-10-12 12:00:00 AM
Day         : 12
DayOfWeek   : 5
DayOfYear   : 285
Hour        : 22
Kind        : 2
Millisecond : 768
Minute      : 55
Month       : 10
Second      : 52
Ticks       : 636749817527683372
TimeOfDay   : @{Ticks=825527683372; Days=0; Hours=22; Milliseconds=768; Minutes=55; Seconds=52;
              TotalDays=0.95547185575463; TotalHours=22.9313245381111; TotalMilliseconds=82552768.3372;
              TotalMinutes=1375.87947228667; TotalSeconds=82552.7683372}
Year        : 2018
```

In dit voorbeeld ziet u hoe u de cmdlets en gebruikt om een object te converteren naar een `ConvertTo-Json` `ConvertFrom-Json` JSON-tekenreeks en een JSON-object.

## PARAMETERS

### -AsArray

Het object wordt uitgevoerd tussen matrixhaken, zelfs als de invoer één object is.

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

### -Comprimeren

Geen witruimte en ingesprongen opmaak in de uitvoertekenreeks.

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

### -Diepte

Hiermee geeft u op hoeveel niveaus van ingesloten objecten zijn opgenomen in de JSON-weergave. De waarde kan een getal van tot `1` `[Int]::MaxValue` zijn. De standaardwaarde is `2`. `ConvertTo-Json` geeft een waarschuwing weer als het aantal niveaus in een invoerobject dit aantal overschrijdt.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnumsAsStrings

Biedt een alternatieve serialisatieoptie die alle enumeraties converteert naar hun tekenreeksweergave.

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

### -EscapeHandling

Hiermee bepaalt u hoe bepaalde tekens worden uitgesloten in de resulterende JSON-uitvoer. Standaard worden alleen besturingselementtekens (zoals nieuwe regel) als escape-teken gebruikt.

Acceptabele waarden zijn:

- Standaard: alleen besturingselementtekens krijgen een escape-teken.
- EscapeNonAscii: alle niet-ASCII- en besturingstekens krijgen een escape-teken.
- EscapeHtml - HTML ( `<` , , , , , ) en `>` `&` `'` `"` besturingselementtekens worden als escape-teken gebruikt.

Deze parameter is geïntroduceerd in PowerShell 6.2.

```yaml
Type: Newtonsoft.Json.StringEscapeHandling
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

Hiermee geeft u de objecten om te converteren naar JSON-indeling. Voer een variabele in die de objecten bevat of typ een opdracht of expressie die de objecten op haalt. U kunt een object ook doorspijpen naar `ConvertTo-Json` .

De **parameter InputObject** is vereist, maar de waarde kan null ( `$null` ) of een lege tekenreeks zijn.
Wanneer het invoerobject `$null` is, `ConvertTo-Json` genereert geen uitvoer. Wanneer het invoerobject een lege tekenreeks is, `ConvertTo-Json` retourneert een lege tekenreeks.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie voor meer informatie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INVOER

### System.Object

U kunt elk object doorspijpen naar `ConvertTo-Json` .

## UITVOER

### System.String

## OPMERKINGEN

De `ConvertTo-Json` cmdlet wordt geïmplementeerd met [Newtonsoft Json.NET](https://www.newtonsoft.com/json).

## GERELATEERDE KOPPELINGEN

[Een inleiding tot JavaScript Object Notation (JSON) in JavaScript en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertFrom-Json](ConvertFrom-Json.md)

[Get-Content](../Microsoft.PowerShell.Management/Get-Content.md)

[Get-UICulture](Get-UICulture.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)

[NewtonSoft.Jsaan. StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
