---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: bfeb838ca8f67bac7c257ef3485eff9b55753933
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250548"
---
# Set-TimeZone

## SAMENVATTING
Hiermee stelt u de systeem tijd zone in op een opgegeven tijd zone.

## SYNTAXIS

### Naam (standaard)

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Input object

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Set-TimeZone`Met de cmdlet wordt de systeem tijd zone ingesteld op een opgegeven tijd zone.

## VOORBEELDEN

### Voor beeld 1: de tijd zone instellen op id

In dit voor beeld wordt de tijd zone op de lokale computer ingesteld op Russische standaard tijd.

```powershell
Set-TimeZone -Id "Russian Standard Time" -PassThru
```

```Output
Id                         : Russian Standard Time
DisplayName                : (UTC+03:00) Moscow, St. Petersburg
StandardName               : Russia TZ 2 Standard Time
DaylightName               : Russia TZ 2 Daylight Time
BaseUtcOffset              : 03:00:00
SupportsDaylightSavingTime : True
```

### Voor beeld 2: de tijd zone instellen op naam

In dit voor beeld wordt de tijd zone op de lokale computer ingesteld op Russische standaard tijd.

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

Zoals we in het vorige voor beeld hebben gezien, komen de **id** en de **naam** van de tijd zone niet altijd overeen.
De para meter **name** moet overeenkomen met de **standaard** eigenschappen of de eigenschap **zomernaam** van het object **time zone info** .

## PARAMETERS

### -Id

Hiermee geeft u de ID op van de tijd zone die met deze cmdlet wordt ingesteld. U kunt een volledige lijst met tijd zone-Id's verkrijgen door de volgende opdracht uit te voeren: `Get-TimeZone -ListAvailable` .

```yaml
Type: System.String
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u een **time zone info** -object moet worden gebruikt als invoer.

```yaml
Type: System.TimeZoneInfo
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de naam van de tijd zone op die met deze cmdlet wordt ingesteld. U kunt een volledige lijst met tijd zone namen verkrijgen door de volgende opdracht uit te voeren: `Get-TimeZone -ListAvailable` .

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt. Deze cmdlet genereert standaard geen uitvoer.

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

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String, System. time zone info, System. String

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-time zone](Get-TimeZone.md)
