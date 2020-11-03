---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-formatdata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-FormatData
ms.openlocfilehash: 3bdda43a3996e8ecfe5c26c146190e63796ad130
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251121"
---
# Export-FormatData

## SAMENVATTING
Hiermee slaat u de opmaak gegevens van de huidige sessie op in een opmaak bestand.

## SYNTAXIS

### ByPath (standaard)

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -Path <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

### ByLiteralPath

```
Export-FormatData -InputObject <ExtendedTypeDefinition[]> -LiteralPath <String> [-Force] [-NoClobber]
 [-IncludeScriptBlock] [<CommonParameters>]
```

## BESCHRIJVING

`Export-FormatData`Met de cmdlet worden Power shell-indelings bestanden (format.ps1XML) gemaakt op basis van de opmaak objecten in de huidige sessie. Hiermee worden de **ExtendedTypeDefinition** -objecten `Get-FormatData` opgehaald die worden geretourneerd en opgeslagen in een bestand met de XML-indeling.

Power shell gebruikt de gegevens in indelings bestanden (format.ps1XML) om de standaard weergave van Microsoft .NET Framework-objecten in de sessie te genereren. U kunt de indelings bestanden weer geven en bewerken en de Update-FormatData cmdlet gebruiken om de opmaak gegevens aan een sessie toe te voegen.

Zie [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)voor meer informatie over het format teren van bestanden in Power shell.

## VOORBEELDEN

### Voor beeld 1: gegevens van sessie formaat exporteren

```powershell
Get-FormatData -TypeName "*" -PowerShellVersion 5.1 | Export-FormatData -Path "allformat.ps1xml" -IncludeScriptBlock
```

Met deze opdracht worden alle indelings gegevens in de sessie geëxporteerd naar het XML-bestand van de AllFormat.ps1.

De opdracht gebruikt de `Get-FormatData` cmdlet om de indelings gegevens in de sessie op te halen. De waarde van `*` (alle) voor de para meter **TypeName** zorgt ervoor dat de cmdlet alle gegevens in de sessie ophaalt.

De opdracht maakt gebruik van een pijplijn operator ( `|` ) om de indelings gegevens van de `Get-FormatData` opdracht te verzenden naar de `Export-FormatData` cmdlet, waarmee de indelings gegevens worden geëxporteerd naar het AllFormat.ps1-bestand.

De `Export-FormatData` opdracht gebruikt de para meter **IncludeScriptBlock** voor het insluiten van script blokken in de indelings gegevens in het bestand.

### Voor beeld 2: indelings gegevens exporteren voor een type

```powershell
$F = Get-FormatData -TypeName "helpinfoshort" -PowerShellVersion 5.1
Export-FormatData -InputObject $F -Path "c:\test\help.format.ps1xml" -IncludeScriptBlock
```

Met deze opdrachten exporteert u de indelings gegevens voor het **HelpInfoShort** -type naar het XML-bestand van de Help.format.ps1.

Met de eerste opdracht wordt de `Get-FormatData` cmdlet gebruikt om de indelings gegevens voor het **HelpInfoShort** -type op te halen. deze worden opgeslagen in de `$F` variabele.

Met de tweede opdracht wordt de para meter **input object** van de `Export-FormatData` cmdlet gebruikt om de indelings gegevens in te voeren die in de variabele zijn opgeslagen `$F` . De para meter **IncludeScriptBlock** wordt ook gebruikt om script blokken in de uitvoer op te neemt.

### Voor beeld 3: indelings gegevens exporteren zonder een script blok

```powershell
Get-FormatData -TypeName "System.Diagnostics.Process" -PowerShellVersion 5.1 | Export-FormatData -Path process.format.ps1xml
Update-FormatData -PrependPath ".\process.format.ps1xml"
Get-Process p*
```

```Output
Handles  NPM(K)  PM(K)  WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------  -----  ----- -----   ------    -- -----------
323                                       5600 powershell
336                                       3900 powershell_ise
138                                       4076 PresentationFontCache
```

In dit voor beeld ziet u het effect van het weglaten van de para meter **IncludeScriptBlock** van een `Export-FormatData` opdracht.

Met de eerste opdracht wordt de `Get-FormatData` cmdlet gebruikt om de indelings gegevens op te halen voor het object **System. Diagnostics. process** dat door de cmdlet Get-Process wordt geretourneerd. De opdracht maakt gebruik van een pijplijn operator ( `|` ) voor het verzenden van de opmaak gegevens naar de `Export-FormatData` cmdlet, die deze exporteert naar het Process.format.ps1XML-bestand in de huidige map.

In dit geval gebruikt de `Export-FormatData` opdracht de para meter **IncludeScriptBlock** niet.

De tweede opdracht gebruikt de `Update-FormatData` cmdlet om het Process.format.ps1XML-bestand toe te voegen aan de huidige sessie. De opdracht gebruikt de para meter **PrependPath** om ervoor te zorgen dat de opmaak gegevens voor proces objecten in het XML-bestand van de Process.format.ps1worden gevonden vóór de standaard indelings gegevens voor proces objecten.

Met de derde opdracht worden de effecten van deze wijziging weer gegeven. De opdracht gebruikt de `Get-Process` cmdlet om processen te verkrijgen die namen hebben die met P beginnen. De uitvoer laat zien dat eigenschaps waarden die worden berekend met behulp van script blokken, ontbreken in de weer gave.

## PARAMETERS

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

### -IncludeScriptBlock

Hiermee wordt aangegeven of script blokken in de indelings gegevens worden geëxporteerd.

Omdat script blokken code bevatten en kunnen worden gebruikt om schadelijke software te gebruiken, worden deze niet standaard geëxporteerd.

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

Hiermee geeft u de gegevens objecten opmaken die moeten worden geëxporteerd. Voer een variabele in die de objecten bevat of een opdracht waarmee de objecten worden opgehaald, zoals een `Get-FormatData` opdracht. U kunt de objecten ook door sluizen van `Get-FormatData` naar `Export-FormatData` .

```yaml
Type: System.Management.Automation.ExtendedTypeDefinition[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u een locatie op voor het uitvoer bestand. In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Geeft aan dat de cmdlet bestaande bestanden niet overschrijft. Standaard worden `Export-FormatData` bestanden overschreven zonder waarschuwing tenzij het bestand het kenmerk alleen-lezen heeft.

Als u `Export-FormatData` alleen-lezen bestanden wilt overschrijven, gebruikt u de para meter **Force** .

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

### -Path

Hiermee geeft u een locatie op voor het uitvoer bestand.
Voer een pad (optioneel) en een bestands naam in met een format.ps1XML-bestandsnaam extensie.
Als u het pad weglaat, `Export-FormatData` maakt het bestand in de huidige map.

Als u een andere bestands extensie dan. ps1xml gebruikt, `Update-FormatData` wordt het bestand niet door de cmdlet herkend.

Als u een bestaand bestand opgeeft, wordt `Export-FormatData` het bestand overschreven zonder waarschuwing, tenzij het bestand het kenmerk alleen-lezen heeft. Als u een alleen-lezen bestand wilt overschrijven, gebruikt u de para meter **Force** . Gebruik de para meter **NoClobber** om te voor komen dat bestanden worden overschreven.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: FilePath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. ExtendedTypeDefinition

U kunt **ExtendedTypeDefinition** -objecten door sluizen van `Get-FormatData` naar `Export-FormatData` .

## UITVOER

### Geen

`Export-FormatData` retourneert geen objecten.
Er wordt een bestand gegenereerd en opgeslagen in het opgegeven pad.

## OPMERKINGEN

- Als u een opmaak bestand wilt gebruiken, met inbegrip van een geëxporteerd opmaak bestand, moet het uitvoerings beleid voor de sessie toestaan dat scripts en configuratie bestanden worden uitgevoerd. Zie [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Get-FormatData](Get-FormatData.md)

[Update-FormatData](Update-FormatData.md)
