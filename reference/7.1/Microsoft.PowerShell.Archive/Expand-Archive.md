---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: 6b89512ebc786a47ae47dd2cd8f51cb532382e02
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "93251451"
---
# Expand-Archive

## SAMENVATTING
Hiermee worden bestanden uitgepakt uit een opgegeven archief bestand (zip).

## SYNTAXIS

### Pad (standaard)

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Expand-Archive`Met de cmdlet worden bestanden uit een opgegeven gezipt archief bestand uitgepakt naar een opgegeven doelmap. Met een archief bestand kunnen meerdere bestanden worden verpakt en optioneel gecomprimeerd in één ZIP-bestand, voor een eenvoudigere distributie en opslag.

## VOORBEELDEN

### Voor beeld 1: de inhoud van een archief extra heren

In dit voor beeld wordt de inhoud van een bestaand archief bestand geëxtraheerd naar de map die is opgegeven door de para meter **doelpad** .

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

In dit voor beeld wordt de para meter **LiteralPath** gebruikt omdat de bestands naam tekens bevat die als Joker teken kunnen worden geïnterpreteerd.

### Voor beeld 2: de inhoud van een archief in de huidige map extra heren

In dit voor beeld wordt de inhoud van een bestaand archief bestand in de huidige map geëxtraheerd naar de map die is opgegeven door de para meter **doelpad** .

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## PARAMETERS

### -Doelpad

`Expand-Archive`Maakt standaard een map op de huidige locatie die dezelfde naam als het zip-bestand heeft. Met de para meter kunt u het pad naar een andere map opgeven. De doelmap wordt gemaakt als deze niet bestaat.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: A folder in the current location
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

### -LiteralPath

Hiermee geeft u het pad naar een archief bestand. In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt. Joker tekens worden niet ondersteund. Als het pad escape tekens bevat, moet u elk escape teken tussen enkele aanhalings tekens plaatsen om Power shell te instrueren dat tekens niet worden geïnterpreteerd als escape reeksen.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Zorgt ervoor dat de cmdlet een lijst uitvoer van de bestanden die uit het archief zijn uitgevouwen.

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

### -Path

Hiermee geeft u het pad naar het archief bestand.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### System. String

U kunt een teken reeks met een pad naar een bestaand archief bestand door sluizen.

## UITVOER

### System. IO. FileSystemInfo

Wanneer de `-PassThru` para meter wordt gebruikt, voert de cmdlet een lijst met bestanden uit die zijn uitgevouwen uit het archief.

## OPMERKINGEN

De [specificatie zip-bestand](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) geeft geen standaard wijze op voor het coderen van bestands namen die niet-ASCII-tekens bevatten. De `Compress-Archive` cmdlet maakt gebruik van UTF-8-code ring. Andere ZIP-archief hulpprogramma's kunnen gebruikmaken van een ander coderings schema. Bij het uitpakken van bestanden met bestands namen die niet met UTF-8-code ring zijn opgeslagen, `Expand-Archive` wordt de onbewerkte waarde gebruikt die in het archief is gevonden. Dit kan resulteren in een bestands naam die verschilt van de bron bestandsnaam die is opgeslagen in het archief.

## GERELATEERDE KOPPELINGEN

[Comprimeren-archief](compress-archive.md)
