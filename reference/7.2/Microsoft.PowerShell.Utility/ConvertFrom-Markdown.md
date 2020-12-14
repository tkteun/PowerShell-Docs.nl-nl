---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: c694e73e69c1e51ecf88f445684923ef5f19113f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705848"
---
# ConvertFrom-Markdown

## SAMENVATTING
De inhoud van een teken reeks of een bestand converteren naar een **MarkdownInfo** -object.

## SYNTAXIS

### PathParamSet (standaard)

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### LiteralParamSet

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### InputObjParamSet

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## BESCHRIJVING

Met deze cmdlet wordt de opgegeven inhoud geconverteerd naar een **MarkdownInfo**. Wanneer een bestandspad is opgegeven voor de para meter **Path** , wordt de inhoud van het bestand geconverteerd. Het uitvoer object heeft drie eigenschappen:

- De eigenschap **token** heeft de abstracte syntaxis structuur (AST) van het geconverteerde object
- De eigenschap **HTML** heeft de HTML-conversie van de opgegeven invoer
- De eigenschap **VT100EncodedString** heeft de geconverteerde teken reeks met ANSI (VT100) escape-reeksen als de para meter **AsVT100EncodedString** is opgegeven

Deze cmdlet is geïntroduceerd in Power shell 6,1.

## VOORBEELDEN

### Voor beeld 1: een bestand met de inhoud van de prijs verlaging converteren naar HTML

```powershell
ConvertFrom-Markdown -Path .\README.md
```

Het **MarkdownInfo** -object wordt geretourneerd. De eigenschap **tokens** heeft de AST van de geconverteerde inhoud van het `README.md` bestand. De **HTML-** eigenschap bevat de HTML-inhoud van het `README.md` bestand.

### Voor beeld 2: een bestand met de inhoud van de prijs opwaarde converteren naar een VT100-gecodeerde teken reeks

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

Het **MarkdownInfo** -object wordt geretourneerd. De eigenschap **tokens** heeft de AST van de geconverteerde inhoud van het `README.md` bestand. De eigenschap **VT100EncodedString** heeft de door VT100 versleutelde teken reeks die inhoud van het bestand heeft geconverteerd `README.md` .

### Voor beeld 3: een invoer object met de inhoud van de prijs opwaarde converteren naar een VT100-gecodeerde teken reeks

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

Het **MarkdownInfo** -object wordt geretourneerd. Het **file info** -object van `Get-Item` wordt geconverteerd naar een met VT100 versleutelde teken reeks. De eigenschap **tokens** heeft de AST van de geconverteerde inhoud van het `README.md` bestand. De eigenschap **VT100EncodedString** heeft de door VT100 versleutelde teken reeks die inhoud van het bestand heeft geconverteerd `README.md` .

### Voor beeld 4: een teken reeks met de inhoud van de prijs opwaarderen naar een VT100-gecodeerde teken reeks

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

Het **MarkdownInfo** -object wordt geretourneerd. De opgegeven teken reeks `**Bold text**` wordt geconverteerd naar een in VT100 versleutelde teken reeks en is beschikbaar in de eigenschap **VT100EncodedString** .

## PARAMETERS

### -AsVT100EncodedString

Geeft aan of de uitvoer moet worden gecodeerd als een teken reeks met VT100-escape codes.

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

### -Input object

Geeft het object aan dat moet worden geconverteerd. Wanneer een object van het type **System. String** wordt opgegeven, wordt de teken reeks geconverteerd. Wanneer een object van het type **System. io. file info** is opgegeven, wordt de inhoud van het bestand dat is opgegeven door het object geconverteerd. Objecten van elk ander type resulteren in een fout.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObjParamSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u een pad op naar het bestand dat moet worden geconverteerd.

```yaml
Type: System.String[]
Parameter Sets: LiteralParamSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u een pad op naar het bestand dat moet worden geconverteerd.

```yaml
Type: System.String[]
Parameter Sets: PathParamSet
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

### System. Management. Automation. PSObject

## UITVOER

### Micro soft. Power shell. MarkdownRender. MarkdownInfo

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Parser prijs verlaging](https://github.com/lunet-io/markdig)

[ANSI escape-code](https://wikipedia.org/wiki/ANSI_escape_code)

