---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 6085585a50f8d3ac8adb34d4d9e3e376a1bc17cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251270"
---
# New-DscChecksum

## SAMENVATTING
Hiermee maakt u controlesom bestanden voor DSC-documenten en DSC-resources.

## SYNTAXIS

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **New-DSCCheckSum** genereert controlesom bestanden voor de Power shell-documenten voor desired state Configuration (DSC) en gecomprimeerde DSC-resources.
Met deze cmdlet wordt een controlesom bestand gegenereerd voor elke configuratie en resource die in de pull-modus moeten worden gebruikt.
De DSC-service gebruikt de controle sommen om ervoor te zorgen dat de juiste configuratie en resources bestaan op het doel knooppunt.
Plaats de controle sommen samen met de bijbehorende DSC-documenten en gecomprimeerde DSC-resources in de DSC-service opslag.

## VOORBEELDEN

### Voor beeld 1: controlesom bestanden maken voor alle configuraties in een specifiek pad

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

Met deze opdracht worden controlesom bestanden gemaakt voor alle configuraties in het pad C:\DSC\Configurations.
Eventuele controlesom bestanden die al bestaan, worden overgeslagen.

### Voor beeld 2: controlesom bestanden maken voor alle configuraties in een specifiek pad en de bestaande controlesom bestanden overschrijven

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

Met deze opdracht worden nieuwe controlesom bestanden gemaakt voor alle configuraties in het pad C:\DSC\Configurations.
Het opgeven van de para meter *Force* zorgt ervoor dat de opdracht eventuele controlesom bestanden overschrijft die al bestaan.

## PARAMETERS

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

### -Force

Geeft aan dat de cmdlet het opgegeven uitvoer bestand overschrijft als dit al bestaat.

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

### -Outpath

Hiermee geeft u het pad en de bestands naam van het bestand met de uitvoer controlesom op.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad van het invoer bestand.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ConfigurationPath

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

### Geen

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Overzicht van desired state Configuration voor Windows Power shell](/powershell/scripting/dsc/overview/dscforengineers)

