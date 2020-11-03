---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 89f277f658645f18d0ae5f2f3ad0e81a8fbdb4a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250394"
---
# New-TimeSpan

## SAMENVATTING
Hiermee maakt u een time span-object.

## SYNTAXIS

### Datum (standaard)

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### Tijd

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## BESCHRIJVING

De `New-TimeSpan` cmdlet maakt een **span** -object dat een tijds interval vertegenwoordigt.
U kunt een **time span** -object gebruiken om tijd toe te voegen of af te trekken van **DateTime** -objecten.

Zonder para meters `New-TimeSpan` retourneert een opdracht een **span** -object dat een tijds interval van nul vertegenwoordigt.

## VOORBEELDEN

### Voor beeld 1: een time span-object maken voor een opgegeven duur

Met deze opdracht maakt u een **time span** -object met een duur van 1 uur en 25 minuten en slaat u deze op in een variabele met de naam `$TimeSpan` . Er wordt een weer gave van het object **time span** weer gegeven.

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### Voor beeld 2: een time span-object maken voor een tijds interval

In dit voor beeld wordt een nieuw **time span** -object gemaakt dat het interval aangeeft tussen het tijdstip waarop de opdracht wordt uitgevoerd en 1 januari 2010.

Voor deze opdracht is de **Start** parameter niet vereist, omdat de standaard waarde van de para meter **Start** de huidige datum en tijd is.

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### Voor beeld 3: de datum 90 dagen vanaf de huidige datum ophalen

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

Met deze opdrachten wordt de datum geretourneerd die 90 dagen na de huidige datum valt.

### Voor beeld 4: de time span ontdekken sinds een bestand is bijgewerkt

Met deze opdracht wordt aangegeven hoe lang het is sinds het [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) Help-bestand voor het laatst is bijgewerkt.
U kunt deze opdracht indeling gebruiken voor elk bestand of elk ander object met een eigenschap **LastWriteTime** .

Deze opdracht werkt omdat de **Start** parameter van `New-TimeSpan` een alias van **LastWriteTime** heeft. Wanneer u een object met een **LastWriteTime** -eigenschap naar een pipet `New-TimeSpan` , gebruikt Power shell de waarde van de eigenschap **LastWriteTime** als de waarde van de para meter **Start** .

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## PARAMETERS

### -Dagen

Hiermee geeft u de dagen in de tijds Panne op.
De standaardwaarde is 0.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -End

Hiermee geeft u het einde van een tijds Panne op.
De standaard waarde is de huidige datum en tijd.

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Uren

Hiermee geeft u de uren in de tijds Panne op.
De standaard waarde is nul.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Minuten

Geeft de minuten in de tijds Panne aan.
De standaardwaarde is 0.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Seconden

Hiermee geeft u de lengte van de tijds duur in seconden op.
De standaardwaarde is 0.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Start

Hiermee geeft u het begin van een tijds Panne op.
Voer een teken reeks in die de datum en tijd vertegenwoordigt, zoals "3/15/09" of een **DateTime** -object, zoals een van een `Get-Date` opdracht. De standaard waarde is de huidige datum en tijd.

U kunt **Start** of de alias gebruiken, **LastWriteTime**.
Met de **LastWriteTime** -alias kunt u objecten die een **LastWriteTime** -eigenschap hebben, zoals bestanden in het bestands systeem `[System.Io.FileIO]` , met de para meter **Start** van opgeven `New-TimeSpan` .

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. DateTime

U kunt een **DateTime** -object dat de begin tijd vertegenwoordigt, door sluizen naar `New-TimeSpan` .

## UITVOER

### System. time span

`New-TimeSpan` retourneert een object dat de tijds Panne vertegenwoordigt.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Ophalen datum](Get-Date.md)

[Set-date](Set-Date.md)
