---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: f3230c247296d5fd907d580e719cbbbc560183a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250560"
---
# Set-Clipboard

## SAMENVATTING
Hiermee stelt u de huidige vermelding van het Windows-klem bord.

## SYNTAXIS

### Teken reeks (standaard)

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Waarde

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Pad

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Set-Clipboard` cmdlet wordt het huidige Windows klem bord-item ingesteld.

## VOORBEELDEN

### Voor beeld 1: tekst naar het klem bord kopiëren

```powershell
Set-Clipboard -Value "This is a test string"
```

### Voor beeld 2: de inhoud van een map naar het klem bord kopiëren

Met deze opdracht wordt de inhoud van de opgegeven map naar het klem bord gekopieerd.

```powershell
Set-Clipboard -Path "C:\Staging\"
```

## PARAMETERS

### -Toevoegen

Geeft aan dat het klem bord niet wordt gewist door de cmdlet en er inhoud aan wordt toegevoegd.

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

### -AsHtml

Geeft aan dat de cmdlet de inhoud weergeeft als HTML-bestand naar het klem bord.

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

Hiermee geeft u het pad op naar het item dat naar het klem bord wordt gekopieerd. In tegens telling tot **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Windows Power shell geen tekens interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad op naar het item dat naar het klem bord wordt gekopieerd. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Waarde

Geeft als een teken reeks matrix de inhoud aan die naar het klem bord moet worden gekopieerd.

```yaml
Type: System.String[]
Parameter Sets: Value
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

### System.String[]

## UITVOER

## OPMERKINGEN

In zeldzame gevallen wanneer `Set-Clipboard` u met een groot aantal waarden snel achter elkaar gebruikt, bijvoorbeeld in een lus, kunt u sporadisch een lege waarde uit het klem bord halen. Dit kan worden opgelost door `Start-Sleep -Milliseconds 1` in de lus te gebruiken.

## GERELATEERDE KOPPELINGEN

[Get-klem bord](Get-Clipboard.md)
