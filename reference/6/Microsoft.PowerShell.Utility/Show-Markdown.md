---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: 2d88b24519f472f0c167dc5138450ab542a8b7cf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250996"
---
# Show-Markdown

## SAMENVATTING
Toont een bestand of teken reeks in de-console op een beschrijvende manier met VT100-escape reeksen of in een browser met behulp van HTML.

## SYNTAXIS

### Pad (standaard)

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### Input object

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### LiteralPath

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## BESCHRIJVING

De `Show-Markdown` cmdlet wordt gebruikt om de prijs verlaging te genereren in een lees bare vorm in een Terminal of in een browser.

`Show-Markdown` kan een teken reeks retour neren die de VT100-escape reeksen bevat die door de terminal worden weer gegeven (als deze ondersteuning biedt voor VT100-escape reeksen). Dit wordt voornamelijk gebruikt voor het weer geven van de kortings bestanden in een Terminal. U kunt deze teken reeks ook ophalen via de `ConvertFrom-Markdown` door de para meter **AsVT100EncodedString** op te geven.

`Show-Markdown` biedt ook de mogelijkheid om een browser te openen en een gerenderde versie van de prijs opgave weer te geven. De korting wordt weer gegeven door deze in HTML in te scha kelen en het HTML-bestand te openen in de standaard browser.

U kunt wijzigen hoe `Show-Markdown` de prestaties van een terminal worden geprijsd met behulp van `Set-MarkdownOption` .

Deze cmdlet is geïntroduceerd in Power shell 6,1.

## VOORBEELDEN

### Voor beeld 1: eenvoudig voor beeld van een pad opgeven

```powershell
Show-Markdown -Path ./README.md
```

### Voor beeld 2: een eenvoudig voor beeld van een teken reeks opgeven

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### Voor beeld 2: de prijs verlaging wordt geopend in een browser

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## PARAMETERS

### -Input object

Een kortings teken reeks die wordt weer gegeven in de Terminal. Als u geen ondersteunde indeling doorgeeft, `Show-Markdown` wordt een fout bericht weer gegeven.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad op naar het bestand voor een afkorting. In tegens telling tot de para meter path wordt de waarde van LiteralPath precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u het pad op naar het bestand voor afkorting dat moet worden gerenderd.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -UseBrowser

Compileert de invoer voor de prijs verlaging als HTML en opent deze in de standaard browser.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

### System.String[]

## UITVOER

### System. String

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[ConvertFrom-prijs verlaging](ConvertFrom-Markdown.md)
