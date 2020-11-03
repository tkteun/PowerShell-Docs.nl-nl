---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: b91d3b7cbf86c7ea827539903b2e8373cdfdac72
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250467"
---
# ConvertTo-Json

## SAMENVATTING
Converteert een object naar een teken reeks in JSON-indeling.

## SYNTAXIS

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
 [<CommonParameters>]
```

## BESCHRIJVING

`ConvertTo-Json`Met de cmdlet wordt een .net-object geconverteerd naar een teken reeks in de indeling van de JavaScript object Notation (JSON). De eigenschappen worden geconverteerd naar veld namen, de veld waarden worden geconverteerd naar eigenschaps waarden en de methoden worden verwijderd.

U kunt de cmdlet vervolgens gebruiken `ConvertFrom-Json` om een JSON-indelings teken reeks te converteren naar een JSON-object, dat eenvoudig kan worden beheerd in Power shell.

Veel websites gebruiken JSON in plaats van XML om gegevens te serialiseren voor communicatie tussen servers en web-apps.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voorbeeld 1

```powershell
PS C:\> (Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
    "MinSupportedDateTime":  "\/Date(-62135596800000)\/",
    "MaxSupportedDateTime":  "\/Date(253402300799999)\/",
    "AlgorithmType":  1,
    "CalendarType":  1,
    "Eras":  [
                 1
             ],
    "TwoDigitYearMax":  2029,
    "IsReadOnly":  false
}
```

Met deze opdracht wordt de `ConvertTo-Json` cmdlet gebruikt om een GregorianCalendar-object te converteren naar een JSON-indelings teken reeks.

### Voorbeeld 2

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

Met deze opdracht wordt het effect van het gebruik van de para meter **compress** van gebruikt `ConvertTo-Json` . De compressie is alleen van invloed op de weer gave van de teken reeks, niet op de geldigheids duur.

### Voorbeeld 3

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
    "DisplayHint":  2,
    "DateTime":  "Friday, January 13, 2012 8:06:16 PM",
    "Date":  "\/Date(1326441600000)\/",
    "Day":  13,
    "DayOfWeek":  5,
    "DayOfYear":  13,
    "Hour":  20,
    "Kind":  2,
    "Millisecond":  221,
    "Minute":  6,
    "Month":  1,
    "Second":  16,
    "Ticks":  634620819762218083,
    "TimeOfDay":  {
                      "Ticks":  723762218083,
                      "Days":  0,
                      "Hours":  20,
                      "Milliseconds":  221,
                      "Minutes":  6,
                      "Seconds":  16,
                      "TotalDays":  0.83768775241087956,
                      "TotalHours":  20.104506057861109,
                      "TotalMilliseconds":  72376221.8083,
                      "TotalMinutes":  1206.2703634716668,
                      "TotalSeconds":  72376.22180829999
                  },
    "Year":  2012
}
```

In dit voor beeld wordt de `ConvertTo-Json` cmdlet gebruikt voor het converteren van een **System. datetime** -object van de `Get-Date` cmdlet naar een teken reeks in JSON-indeling. De opdracht gebruikt de `Select-Object` cmdlet om alle ( `*` ) van de eigenschappen van het **DateTime** -object op te halen. In de uitvoer ziet u de JSON-teken reeks die is `ConvertTo-Json` geretourneerd.

### Voorbeeld 4

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

In dit voor beeld ziet u hoe u de `ConvertTo-Json` cmdlets en kunt gebruiken `ConvertFrom-Json` om een object te converteren naar een JSON-teken reeks en een JSON-object.

## PARAMETERS

### -Comprimeren

Witruimte en Inge sprongen opmaak in de uitvoer teken reeks weglaten.

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

Hiermee geeft u op hoeveel niveaus van Inge sloten objecten worden opgenomen in de JSON-weer gave. De standaardwaarde is 2.

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

### -Input object

Hiermee geeft u de objecten die moeten worden geconverteerd naar de JSON-indeling. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald. U kunt ook een object pipet naar `ConvertTo-Json` .

De para meter **input object** is vereist, maar de waarde kan Null ( `$null` ) of een lege teken reeks zijn.
Wanneer het invoer object is `$null` , wordt `ConvertTo-Json` er geen uitvoer gegenereerd. Wanneer het invoer object een lege teken reeks is, `ConvertTo-Json` retourneert een lege teken reeks.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. object

U kunt elk object door sluizen naar `ConvertTo-Json` .

## UITVOER

### System. String

## OPMERKINGEN

De `ConvertTo-Json` cmdlet wordt geïmplementeerd met behulp van de [JavaScriptSerializer-klasse](/dotnet/api/system.web.script.serialization.javascriptserializer).

## GERELATEERDE KOPPELINGEN

[Een inleiding tot JavaScript Object Notation (JSON) in Java script en .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertFrom-JSON](ConvertFrom-Json.md)

[Get-Content](../Microsoft.PowerShell.Management/Get-Content.md)

[Get-UICulture](Get-UICulture.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
