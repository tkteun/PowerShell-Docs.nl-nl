---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/export-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-BinaryMiLog
ms.openlocfilehash: cf03ad884121c6cf8cf65cdb791cbdc4e587c3b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250065"
---
# Export-BinaryMiLog

## SAMENVATTING
Hiermee maakt u een binaire, gecodeerde weer gave van een object of objecten en slaat u deze op in een bestand.

## SYNTAXIS

```
Export-BinaryMiLog [-InputObject <CimInstance>] [-Path] <String> [<CommonParameters>]
```

## BESCHRIJVING

`Export-BinaryMILog`Met de cmdlet wordt een op binaire wijze weer gave van een object of objecten gemaakt en opgeslagen in een bestand. U kunt de cmdlet vervolgens gebruiken `Import-BinaryMiLog` om het opgeslagen object opnieuw te maken op basis van de inhoud van het bestand.

Deze cmdlet is vergelijkbaar met `Import-Clixml` , behalve dat `Export-BinaryMILog` het resulterende object wordt opgeslagen in een bestand met binaire code ring.

## VOORBEELDEN

### Voor beeld 1: een binaire weer gave van CimInstances maken

```powershell
Get-CimInstance Win32_Process | Export-BinaryMiLog -Path "Processes.bmil"
```

Met deze opdracht wordt **CimInstances** geëxporteerd naar een binair mi-logboek bestand dat is opgegeven door de para meter Path. Zie het voor beeld voor Import-BinaryMiLog om te zien hoe u de **CimInstances** opnieuw kunt maken door dit bestand te importeren.

## PARAMETERS

### -Input object

Hiermee geeft u de invoer voor deze cmdlet op. U kunt deze para meter gebruiken, of u kunt de invoer door sluizen naar deze cmdlet.

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

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

### Micro soft. Management. Infrastructure. CimInstance

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-CimInstance](get-ciminstance.md)

[Import-BinaryMiLog](import-binarymilog.md)

[Import-Clixml](../microsoft.powershell.utility/import-clixml.md)
