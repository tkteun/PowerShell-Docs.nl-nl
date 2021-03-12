---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: 800cd9ea24bad09f532db26c5091735cd987eef0
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195048"
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
