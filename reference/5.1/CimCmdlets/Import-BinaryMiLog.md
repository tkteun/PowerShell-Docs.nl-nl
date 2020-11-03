---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: ce5dd31170bc47edaa04ca3c31deab62dc4ec354
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250057"
---
# Import-BinaryMiLog

## SAMENVATTING
Wordt gebruikt om de opgeslagen objecten opnieuw te maken op basis van de inhoud van een export bestand.

## SYNTAXIS

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## BESCHRIJVING

Gebruik deze cmdlet om opgeslagen objecten opnieuw te maken op basis van de inhoud van een export bestand dat is gemaakt door `Export-BinaryMILog` . Deze cmdlet is vergelijkbaar met `Import-Clixml` , behalve dat `Export-BinaryMILog` het resulterende object wordt opgeslagen in een bestand met binaire code ring.

## VOORBEELDEN

### Voor beeld 1: objecten herstellen die zijn geëxporteerd naar een bestand

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## PARAMETERS

### -Path

Hiermee geeft u het pad van het bestand waarin de binaire weer gave van het object moet worden opgeslagen. De para meter **Path** ondersteunt joker tekens en relatieve paden. Met deze cmdlet wordt een fout gegenereerd als het pad wordt omgezet in meer dan een bestand.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN
