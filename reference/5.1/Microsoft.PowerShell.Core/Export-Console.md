---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-console?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Console
ms.openlocfilehash: 7b643b5f9b6868a5da988b19b65dead24f986f67
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249966"
---
# Export-Console

## SAMENVATTING
Exporteert de namen van modules in de huidige sessie naar een console bestand.

## SYNTAXIS

```
Export-Console [[-Path] <String>] [-Force] [-NoClobber] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **export-console** exporteert u de namen van de Windows Power shell-modules in de huidige sessie naar een Windows Power shell-console bestand (. psc1).
U kunt deze cmdlet gebruiken om de modules op te slaan voor gebruik in toekomstige sessies.

Als u de modules in het. psc1-console bestand wilt toevoegen aan een sessie, start u Windows Power shell (Powershell.exe) op de opdracht regel met behulp van Cmd.exe of een andere Windows Power shell-sessie en gebruikt u vervolgens de para meter *PSConsoleFile* van Powershell.exe om het console bestand op te geven.

Zie about_PSSnapins voor meer informatie over Windows Power shell-modules.

## VOORBEELDEN

### Voor beeld 1: de namen van modules in de huidige sessie exporteren

```
PS C:\> Export-Console -Path $pshome\Consoles\ConsoleS1.psc1
```

Met deze opdracht worden de namen van de Windows Power shell-modules in de huidige sessie geëxporteerd naar het bestand ConsoleS1. psc1 in de map consoles van de installatiemap van Windows Power shell, $pshome.

### Voor beeld 2: de namen van modules exporteren naar het meest recente console bestand

```
PS C:\> Export-Console
```

Met deze opdracht exporteert u de namen van Windows Power shell-modules vanuit de huidige sessie naar het Windows Power shell-console bestand dat het meest recent is gebruikt in de huidige sessie.
De vorige bestands inhoud wordt overschreven.

Als u tijdens de huidige sessie geen console bestand hebt geëxporteerd, wordt u gevraagd om toestemming te krijgen om door te gaan en vervolgens om een bestands naam te worden gevraagd.

### Voor beeld 3: een module toevoegen en de namen van modules exporteren

```
PS C:\> Add-PSSnapin NewPSSnapin
PS C:\> Export-Console -path NewPSSnapinConsole.psc1
PS C:\> powershell.exe -PsConsoleFile NewPsSnapinConsole.psc1
```

Met deze opdrachten wordt de NewPSSnapin Windows Power shell-module aan de huidige sessie toegevoegd, worden de namen van Windows Power shell-modules in de huidige sessie naar een console bestand geëxporteerd en wordt vervolgens een Windows Power shell-sessie gestart met het console bestand.

De eerste opdracht maakt gebruik van de cmdlet **add-PSSnapin** om de NewPSSnapin-module toe te voegen aan de huidige sessie.
U kunt alleen Windows Power shell-modules toevoegen die zijn geregistreerd op uw systeem.

Met de tweede opdracht worden de namen van de Windows Power shell-modules geëxporteerd naar het bestand NewPSSnapinConsole. psc1.

Met de derde opdracht start u Windows Power shell met het NewPSSnapinConsole. psc1-bestand.
Omdat het console bestand de naam van de Windows Power shell-module bevat, zijn de cmdlets en providers in de module beschikbaar in de huidige sessie.

### Voor beeld 4: namen van modules exporteren naar een opgegeven locatie

```
PS C:\> export-console -path Console01
PS C:\> notepad console01.psc1
<?xml version="1.0" encoding="utf-8"?>
<PSConsoleFile ConsoleSchemaVersion="1.0">
  <PSVersion>2.0</PSVersion>
  <PSSnapIns>
     <PSSnapIn Name="NewPSSnapin" />
  </PSSnapIns>
</PSConsoleFile>
```

Met deze opdracht worden de namen van de Windows Power shell-modules in de huidige sessie geëxporteerd naar het Console01. psc1-bestand in de huidige map.

Met de tweede opdracht wordt de inhoud van het bestand Console01. psc1 in Klad blok weer gegeven.

### Voor beeld 5: bepalen welk console bestand moet worden bijgewerkt

```
PS C:\> powershell.exe -PSConsoleFile Console01.psc1
PS C:\> Add-PSSnapin MySnapin
PS C:\> Export-Console NewConsole.psc1
PS C:\> $ConsoleFileName
PS C:\> Add-PSSnapin SnapIn03
PS C:\> Export-Console
```

In dit voor beeld ziet u hoe u de $ConsoleFileName Automatic-variabele gebruikt om het console bestand te bepalen dat wordt bijgewerkt als u **exporteren-console** gebruikt zonder een para meter voor het *pad* .

De eerste opdracht maakt gebruik van de *PSConsoleFile* -para meter van PowerShell.exe om Windows Power shell te openen met het bestand Console01. psc1.

De tweede opdracht maakt gebruik van de cmdlet **add-PSSnapin** om de MySnapin Windows Power shell-module toe te voegen aan de huidige sessie.

De derde opdracht maakt gebruik van de cmdlet **export-console** om de namen van alle Windows Power shell-modules in de sessie te exporteren naar het bestand NewConsole. psc1.

Met de vierde opdracht wordt de $ConsoleFileName variabele weer gegeven.
Het bevat het meest recent gebruikte console bestand.
In de voorbeeld uitvoer ziet u dat NewConsole.ps1 het meest recent gebruikte bestand is.

De vijfde opdracht voegt SnapIn03 toe aan de huidige console.

De zesde opdracht maakt gebruik van de cmdlet **export-console** zonder een *Path* -para meter.
Met deze opdracht worden de namen van alle Windows Power shell-modules in de huidige sessie geëxporteerd naar het laatst gebruikte bestand, NewConsole. psc1.

## PARAMETERS

### -Force
Geeft aan dat met deze cmdlet de gegevens in een console bestand worden overschreven zonder dat er een waarschuwing wordt gegeven, zelfs als het bestand het kenmerk alleen-lezen heeft.
Het kenmerk alleen-lezen wordt gewijzigd en wordt niet opnieuw ingesteld wanneer de opdracht is voltooid.

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

### -NoClobber
Geeft aan dat deze cmdlet een bestaand console bestand niet overschrijft.
Als er een bestand in het opgegeven pad voor komt, wordt het bestand standaard zonder waarschuwing overschreven door de **console exporteren** .

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
Hiermee geeft u een pad en een bestands naam voor het console bestand (*. psc1).
Voer een optioneel pad en een naam in.
Joker tekens zijn niet toegestaan.

Als u alleen een bestands naam opgeeft, maakt **exporteren-console** een bestand met die naam en de bestandsnaam extensie. psc1 in de huidige map.

Deze para meter is vereist tenzij u Windows Power shell hebt geopend met de para meter *PSConsoleFile* of een console bestand hebt geëxporteerd tijdens de huidige sessie.
Het is ook vereist wanneer u de para meter *NoClobber* gebruikt om te voor komen dat het huidige console bestand wordt overschreven.

Als u deze para meter weglaat, wordt het console bestand dat het meest recent is gebruikt in deze sessie overschreven door de **console** .
Het pad van het meest recent gebruikte console bestand wordt opgeslagen in de waarde van de $ConsoleFileName automatische variabele.
Zie about_Automatic_Variables voor meer informatie.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
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

### System. String
U kunt een padtekenreeks door sluizen naar deze cmdlet.

## UITVOER

### System. IO. file info
Met deze cmdlet wordt een bestand gemaakt dat de geëxporteerde aliassen bevat.

## OPMERKINGEN

* Wanneer een console bestand (. psc1) wordt gebruikt om de sessie te starten, wordt de naam van het console bestand automatisch opgeslagen in de automatische variabele $ConsoleFileName. De waarde van $ConsoleFileName wordt bijgewerkt wanneer u de para meter *Path* van **export-console** gebruikt om een nieuw console bestand op te geven. Als er geen console bestand wordt gebruikt, heeft $ConsoleFileName geen waarde ($Null).

  Als u een Windows Power shell-console bestand wilt gebruiken in een nieuwe sessie, gebruikt u de volgende syntaxis om Windows Power shell te starten:

  `powershell.exe -PsConsoleFile \<ConsoleFile\>.psc1`

  U kunt ook Windows Power shell-modules voor toekomstige sessies opslaan door een Add-PSSnapin-opdracht toe te voegen aan uw Windows Power shell-profiel.
Zie about_Profiles voor meer informatie.


## GERELATEERDE KOPPELINGEN

[Add-PSSnapin](Add-PSSnapin.md)

[Get-PSSnapin](Get-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
