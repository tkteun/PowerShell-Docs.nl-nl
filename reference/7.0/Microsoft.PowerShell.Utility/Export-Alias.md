---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 4ddc9af276f1d24cc687652d96ffba77897305f0
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249512"
---
# Export-Alias

## SAMENVATTING
Exporteert informatie over momenteel gedefinieerde aliassen naar een bestand.

## SYNTAXIS

### ByPath (standaard)

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Export-Alias`Met de cmdlet worden de aliassen in de huidige sessie geëxporteerd naar een bestand.
Als het uitvoer bestand niet bestaat, wordt het door de cmdlet gemaakt.

`Export-Alias` kan de aliassen in een bepaald bereik of alle bereiken exporteren, het kan de gegevens in CSV-indeling genereren of als een reeks Set-Alias opdrachten die u aan een sessie of een Power shell-profiel kunt toevoegen.

## VOORBEELDEN

### Voor beeld 1: een alias exporteren

```powershell
Export-Alias -Path "alias.csv"
```

Met deze opdracht worden de huidige alias gegevens geëxporteerd naar een bestand met de naam Alias.csv in de huidige map.

### Voor beeld 2: een alias exporteren tenzij het export bestand al bestaat

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

Met deze opdracht worden de aliassen in de huidige sessie geëxporteerd naar een Alias.csv-bestand.

Omdat de para meter **NoClobber** is opgegeven, mislukt de opdracht als er al een Alias.csv-bestand in de huidige map bestaat.

### Voor beeld 3: aliassen toevoegen aan een bestand

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

Met deze opdracht worden de aliassen in de huidige sessie toegevoegd aan het Alias.csv-bestand.

De opdracht gebruikt de para meter **Description** om een beschrijving toe te voegen aan de opmerkingen boven aan het bestand.

De opdracht gebruikt ook de **Force** -para meter om bestaande Alias.csv-bestanden te overschrijven, zelfs als ze het kenmerk alleen-lezen hebben.

### Voor beeld 4: aliassen als een script exporteren

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

In dit voor beeld ziet u hoe u de bestands indeling van het script gebruikt die wordt `Export-Alias` gegenereerd.

Met de eerste opdracht worden de aliassen in de sessie geëxporteerd naar het Alias.ps1-bestand.
Het gebruikt de **as** -para meter met de waarde script om een bestand te genereren dat een Set-Alias-opdracht voor elke alias bevat.

Met de tweede opdracht worden de aliassen in het Alias.ps1-bestand toegevoegd aan het CurrentUser-CurrentHost-profiel.
Het pad naar het profiel wordt opgeslagen in de `$Profile` variabele.
De opdracht gebruikt de- `Get-Content` cmdlet om de aliassen uit het Alias.ps1 bestand en de `Add-Content` cmdlet te verkrijgen om ze aan het profiel toe te voegen.
Zie about_Profiles voor meer informatie.

De derde en vierde opdracht voegen de aliassen in het Alias.ps1 bestand toe aan een externe sessie op de Server01-computer.
De derde opdracht gebruikt de `New-PSSession` cmdlet om de sessie te maken.
De vierde opdracht gebruikt de **filepath** -para meter van de `Invoke-Command` cmdlet om het Alias.ps1-bestand in de nieuwe sessie uit te voeren.

## PARAMETERS

### -Toevoegen

Geeft aan dat met deze cmdlet de uitvoer wordt toegevoegd aan het opgegeven bestand, in plaats van de bestaande inhoud van dat bestand te overschrijven.

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

### -As

Hiermee geeft u de indeling van de uitvoer.
CSV is de standaard waarde.
De aanvaardbare waarden voor deze parameter zijn:

- Bestand.
Indeling met door komma's gescheiden waarden (CSV).
- Schriften.
Hiermee maakt u een `Set-Alias` opdracht voor elke geëxporteerde alias.
Als u het uitvoer bestand een naam met de extensie. ps1 hebt, kunt u het uitvoeren als een script om de aliassen toe te voegen aan een sessie.

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Beschrijving

Hiermee geeft u de beschrijving van het geëxporteerde bestand.
De beschrijving wordt weer gegeven als een opmerking boven aan het bestand, volgens de koptekst informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

Hiermee wordt het uitvoer bestand overschreven, zelfs als het kenmerk alleen-lezen is ingesteld voor het bestand.

Standaard worden `Export-Alias` bestanden zonder waarschuwing overschreven, tenzij het kenmerk alleen-lezen of verborgen is ingesteld, of als de para meter **NoClobber** in de opdracht wordt gebruikt.
De para meter **NoClobber** krijgt voor rang op de para meter **Force** wanneer beide worden gebruikt in een opdracht.

De **Force** -para meter kan niet forceren `Export-Alias` om bestanden te overschrijven met het kenmerk Hidden.

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

Hiermee geeft u het pad naar het uitvoer bestand.
In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.
Geen tekens worden geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de namen als een matrix van de aliassen die u wilt exporteren.
Joker tekens zijn toegestaan.

`Export-Alias`Exporteert standaard alle aliassen in de sessie of het bereik.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoClobber

Geeft aan dat deze cmdlet voor komt dat `Export-Alias` bestanden worden overschreven, zelfs niet als de para meter **Force** in de opdracht wordt gebruikt.

Als de para meter **NoClobber** wordt wegge laten, `Export-Alias` wordt een bestaand bestand zonder waarschuwing overschreven, tenzij het kenmerk alleen-lezen is ingesteld voor het bestand.
*NoClobber* heeft voor rang op de para meter **Force** , waarmee `Export-Alias` een bestand kan worden overschreven door het kenmerk alleen-lezen.

*NoClobber* verhindert niet dat de **toevoeg** parameter inhoud toevoegt aan een bestaand bestand.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt.
Deze cmdlet genereert standaard geen uitvoer.

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

Hiermee geeft u het pad naar het uitvoer bestand.
Joker tekens zijn toegestaan, maar de resulterende padwaarde moet worden omgezet in een enkele bestands naam.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Bereik

Hiermee geeft u het bereik op waaruit de aliassen moeten worden geëxporteerd.
De aanvaardbare waarden voor deze parameter zijn:

- Globaal
- Lokaal
- Script
- Een getal dat relatief is ten opzichte van het huidige bereik (0 tot het aantal bereiken waarbij 0 het huidige bereik is en 1 de bovenliggende scope)

De standaard waarde is lokaal.
Zie about_Scopes voor meer informatie.

```yaml
Type: System.String
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

### Geen.

U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### Geen of System. Management. Automation. AliasInfo

Wanneer u de para meter **PassThru** gebruikt, `Export-Alias` retourneert een **System. Management. Automation. AliasInfo** -object dat de alias vertegenwoordigt.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* U kunt alleen Export-Aliases naar een bestand.

## GERELATEERDE KOPPELINGEN

[Get-alias](Get-Alias.md)

[Import-alias](Import-Alias.md)

[Nieuwe alias](New-Alias.md)

[Set-alias](Set-Alias.md)
