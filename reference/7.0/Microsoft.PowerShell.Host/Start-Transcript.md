---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: d4b777202474ead8f944cd2f751b116d9273e728
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860725"
---
# Start-Transcript

## Samen vatting
Hiermee maakt u een record van een Power shell-sessie of een deel ervan aan een tekst bestand.

## Syntax

### ByPath (standaard)

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByLiteralPath

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByOutputDirectory

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## Description

`Start-Transcript`Met de cmdlet maakt u een record van een Power shell-sessie of een deel ervan aan een tekst bestand. De transcript bevat alle opdrachten die de gebruiker typt en alle uitvoer die wordt weer gegeven op de-console.

Vanaf Windows Power shell 5,0 `Start-Transcript` bevat de hostnaam in de gegenereerde bestands naam van alle transcripten. Dit is vooral handig wanneer de logboek registratie van uw onderneming is gecentraliseerd.
Bestanden die door de cmdlet worden gemaakt, `Start-Transcript` bevatten wille keurige tekens in namen om te voor komen dat er sprake is van mogelijke overschrijvingen of duplicatie wanneer twee of meer transcripten tegelijk worden gestart.
Dit voor komt ook niet-geautoriseerde detectie van transcripten die zijn opgeslagen in een gecentraliseerde bestands share.

Als u de para meter **Append** gebruikt en het doel bestand heeft geen byte order Mark (bom) `Start-Transcript` standaard ingesteld op `ASCII` coderen in het doel bestand. Dit gedrag kan leiden tot onjuiste code ring van mulitbyte-tekens in de transcriptie.

## Voorbeelden

### Voor beeld 1: een transcript bestand met de standaard instellingen starten

```powershell
Start-Transcript
```

Met deze opdracht start u een transcriptie op de standaard locatie van het bestand.

### Voor beeld 2: een transcript bestand op een specifieke locatie starten

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

Met deze opdracht wordt een transcript in het `Transcript0.txt` bestand in geopend `C:\transcripts` . Omdat de para meter **NoClobber** wordt gebruikt, wordt voor komen dat bestaande bestanden worden overschreven. Als het `Transcript0.txt` bestand al bestaat, mislukt de opdracht.

## Parameters

### -Toevoegen

Geeft aan dat met deze cmdlet het nieuwe transcript wordt toegevoegd aan het einde van een bestaand bestand. Gebruik de para meter **Path** om het bestand op te geven.

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

### -Force

Hiermee kan de-cmdlet de transcriptie toevoegen aan een bestaand alleen-lezen bestand. Bij gebruik in een bestand met het kenmerk alleen-lezen, wijzigt de cmdlet de bestands machtiging voor lezen/schrijven. De cmdlet kan geen beveiligings beperkingen overschrijven als deze para meter wordt gebruikt.

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

### -IncludeInvocationHeader

Geeft aan dat met deze cmdlet het tijds tempel wordt geregistreerd wanneer opdrachten worden uitgevoerd.

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

### -UseMinimalHeader

Laten voorafgaan door een korte kop voor de transcriptie, in plaats van de gedetailleerde header die standaard is opgenomen. Deze para meter is toegevoegd in Power shell 6,2.

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

Hiermee geeft u een locatie naar het transcript bestand op. In tegens telling tot de para meter **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt terwijl deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens melden Power shell geen tekens te interpreteren als escape reeksen.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Hiermee wordt aangegeven dat deze cmdlet geen bestaand bestand overschrijft. Als er een transcript bestand bestaat in het opgegeven pad, wordt `Start-Transcript` het bestand standaard zonder waarschuwing overschreven.

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

### -Output directory

Hiermee geeft u een specifiek pad en een map op waarin een transcript moet worden opgeslagen. Power shell wijst automatisch de transcript naam toe.

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Hiermee geeft u een locatie naar het transcript bestand op. Voer een pad naar een `.txt` bestand in. Joker tekens zijn niet toegestaan.

Als u geen pad opgeeft, `Start-Transcript` wordt het pad gebruikt in de waarde van de `$Transcript` globale variabele. Als u deze variabele niet hebt gemaakt, `Start-Transcript` slaat de transcripten op in de `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` bestanden.

Als een van de mappen in het pad niet bestaat, mislukt de opdracht.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
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

## Invoerwaarden

### Geen

U kunt geen objecten naar deze cmdlet pipeen.

## Uitvoerwaarden

### System. String

Deze cmdlet retourneert een teken reeks die een bevestigings bericht en het pad naar het uitvoer bestand bevat.

## Notities

Als u een transcript wilt stoppen, gebruikt u de `Stop-Transcript` cmdlet.

Als u een volledige sessie wilt vastleggen, voegt `Start-Transcript` u de opdracht toe aan uw profiel. Zie [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)voor meer informatie.

## Verwante koppelingen

[Stoppen-transcriptie](Stop-Transcript.md)
