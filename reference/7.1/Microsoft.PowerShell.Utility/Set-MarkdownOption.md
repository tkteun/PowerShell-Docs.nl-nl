---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7.x.0&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: e7e70637afcf53f84c719b489575f5267f9048b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249907"
---
# Set-MarkdownOption

## SAMENVATTING
Hiermee stelt u de kleuren en stijlen in die worden gebruikt voor het weer geven van de inhoud van de korting

## SYNTAXIS

### IndividualSetting (standaard)

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### Thema

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### Input object

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## BESCHRIJVING

Hiermee stelt u de kleuren en stijlen in die worden gebruikt voor het weer geven van de inhoud van de korting Deze stijlen worden gedefinieerd met behulp van ANSI-escape codes die de kleur en stijl van de gerenderde tekst van de prijs opgave wijzigen.

Zie de [CommonMark](https://commonmark.org/) -website voor meer informatie over de prijs verlaging.

> [!NOTE]
> De teken reeks waarden die in de instellingen worden gebruikt, zijn de tekens die volgen op het **Escape** teken ( `[char]0x1B` ) voor de ANSI-escape reeks. Neem het **Escape** -teken niet op in de teken reeks. Zie [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)voor meer informatie over ANSI escape-codes.

## VOORBEELDEN

### Voor beeld 1: overschakelen naar het licht thema

In dit voor beeld wordt het **licht** thema geselecteerd en wordt de nieuwe configuratie weer gegeven met behulp van de para meter **PassThru** .

```powershell
Set-MarkdownOption -Theme Light -PassThru
```

```Output
Header1         : [7m
Header2         : [4;33m
Header3         : [4;34m
Header4         : [4;35m
Header5         : [4;36m
Header6         : [4;30m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

### Voor beeld 2: de kleur-en stijl instellingen aanpassen

In dit voor beeld wordt de escape-code voor de kopteksten van de korting gewijzigd. De standaard configuratie voor kopteksten wordt weer gegeven als onderstreepte tekst van verschillende kleuren. Met deze wijziging wordt de onderstrepings stijl verwijderd.

```powershell
$mdOptions = Get-MarkdownOption
$mdOptions.Header2 = '[93m'
$mdOptions.Header3 = '[94m'
$mdOptions.Header4 = '[95m'
$mdOptions.Header5 = '[96m'
$mdOptions.Header6 = '[97m'
Set-MarkdownOption -InputObject $mdOptions -PassThru
```

```Output
Header1         : [7m
Header2         : [93m
Header3         : [94m
Header4         : [95m
Header5         : [96m
Header6         : [97m
Code            : [48;2;155;155;155;38;2;30;30;31m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

## PARAMETERS

### -BoldForegroundColor

Hiermee stelt u de voorgrond kleur voor het weer geven van tekst met een zwarte prijs verlaging.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Code

Hiermee stelt u de kleur in voor het renderen van code blokken en-reeksen in de tekst voor de korting.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header1Color

Hiermee stelt u de kleur voor het renderen van Header1-blokken in de tekst voor de korting.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header2Color

Hiermee stelt u de kleur voor het renderen van Header2-blokken in de tekst voor de korting.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header3Color

Hiermee stelt u de kleur voor het renderen van Header3-blokken in de tekst voor de korting.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header4Color

Hiermee stelt u de kleur voor het renderen van Header4-blokken in de tekst voor de korting.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header5Color

Hiermee stelt u de kleur voor het renderen van Header5-blokken in de tekst voor de korting.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header6Color

Hiermee stelt u de kleur voor het renderen van Header6-blokken in de tekst voor de korting.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ImageAltTextForegroundColor

Hiermee stelt u de voorgrond kleur voor het renderen van de alternatieve tekst van een afbeeldings element in de tekst voor de korting.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Een **PSMarkdownOptionInfo** -object met de configuratie die moet worden ingesteld.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ItalicsForegroundColor

Hiermee stelt u de voorgrond kleur voor het renderen van de cursief in de tekst voor de korting.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LinkForegroundColor

Hiermee stelt u de voorgrond kleur voor het weer geven van Hyper links in de tekst voor de korting.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Zorgt ervoor dat de cmdlet een **PSMarkdownOptionInfo** -object met de nieuwe configuratie uitvoer.

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

### -Thema

Hiermee selecteert u een thema met vooraf gedefinieerde kleur instellingen. De mogelijke waarden zijn **donker** en **licht**.

```yaml
Type: System.String
Parameter Sets: Theme
Aliases:
Accepted values: Dark, Light

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

## UITVOER

### Micro soft. Power shell. MarkdownRender. PSMarkdownOptionInfo

## OPMERKINGEN

De teken reeks waarden die worden gebruikt voor het definiëren van de kleur en stijl moeten overeenkomen met de reguliere expressie `^\[*[0-9;]*?m{1}` .

## GERELATEERDE KOPPELINGEN

[Get-MarkdownOption](Get-MarkdownOption.md)

[ConvertFrom-prijs verlaging](ConvertFrom-Markdown.md)

[Weer geven-prijs verlaging](Show-Markdown.md)

[ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)

[CommonMark](https://commonmark.org/)

