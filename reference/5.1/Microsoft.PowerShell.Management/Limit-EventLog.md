---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/limit-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Limit-EventLog
ms.openlocfilehash: 3ec3214103dc6151e148f7482b0be8b821871e3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250609"
---
# Limit-EventLog

## SAMENVATTING
Hiermee stelt u de eigenschappen van het gebeurtenis logboek in die de grootte van het gebeurtenis logboek en de leeftijd van de vermeldingen beperken.

## SYNTAXIS

```
Limit-EventLog [-LogName] <String[]> [-ComputerName <String[]>] [-RetentionDays <Int32>]
 [-OverflowAction <OverflowAction>] [-MaximumSize <Int64>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Limit-Eventlog** wordt de maximale grootte van een klassiek gebeurtenis logboek ingesteld, hoe lang elke gebeurtenis moet worden bewaard en wat er gebeurt als het logboek de maximum grootte bereikt.
U kunt deze gebruiken om de gebeurtenis logboeken op lokale of externe computers te beperken.

De cmdlets die het zelfstandig naam woord van het gebeurtenissen logboek bevatten (de EventLog-cmdlets) werken alleen in klassieke gebeurtenis Logboeken.
Gebruik Get-Wine vent om gebeurtenissen op te halen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van Windows.

## VOORBEELDEN

### Voor beeld 1: de grootte van een gebeurtenis logboek verg Roten

```
PS C:\> Limit-EventLog -LogName "Windows PowerShell" -MaximumSize 20KB
```

Met deze opdracht wordt de maximale grootte van het Windows Power shell-gebeurtenis logboek op de lokale computer verhoogd tot 20480 bytes (20 KB).

### Voor beeld 2: een gebeurtenis logboek voor een opgegeven duur bewaren

```
PS C:\> Limit-EventLog -LogName Security -ComputerName "Server01", "Server02" -RetentionDays 7
```

Met deze opdracht zorgt u ervoor dat gebeurtenissen in het beveiligings logboek op de Server01-en Server02-computers ten minste 7 dagen worden bewaard.

### Voor beeld 3: de overloop actie van alle gebeurtenis logboeken wijzigen

```
PS C:\> $Logs = Get-EventLog -List | ForEach {$_.log}
PS C:\> Limit-EventLog -OverflowAction OverwriteOlder -LogName $Logs
PS C:\> Get-EventLog -List

Max(K) Retain OverflowAction     Entries  Log
------ ------ --------------     -------  ---
15,168      0 OverwriteOlder       3,412  Application
512         0 OverwriteOlder           0  DFS Replication
512         0 OverwriteOlder          17  DxStudio
10,240      7 OverwriteOlder           0  HardwareEvents
512         0 OverwriteOlder           0  Internet Explorer
512         0 OverwriteOlder           0  Key Management Service
16,384      0 OverwriteOlder           4  ODiag
16,384      0 OverwriteOlder         389  OSession Security
15,168      0 OverwriteOlder      19,360  System
15,360      0 OverwriteOlder      15,828  Windows PowerShell
```

In dit voor beeld wordt de overloop actie van alle gebeurtenis logboeken op de lokale computer gewijzigd in OverwriteOlder.

Met de eerste opdracht worden de logboek namen van alle logboeken op de lokale computer opgehaald.
Met de tweede opdracht wordt de overloop actie ingesteld.
Met de derde opdracht worden de resultaten weer gegeven.

## PARAMETERS

### -ComputerName
Hiermee geeft u externe computers op.
Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een Internet Protocol (IP-adres) of een Fully Qualified Domain Name (FQDN) van een externe computer.
Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.

Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.
U kunt de para meter *ComputerName* van **Limit-Eventlog gebruiken,** zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
Hiermee geeft u de gebeurtenis Logboeken.
Voer de naam van het logboek in (de waarde van de eigenschap log, niet de LogDisplayName) van een of meer gebeurtenis logboeken, gescheiden door komma's.
Joker tekens zijn niet toegestaan.
Deze parameter is vereist.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumSize
Hiermee geeft u de maximale grootte van de gebeurtenis Logboeken in bytes.
Voer een waarde in tussen 64 kB (KB) en 4 gigabyte (GB).
De waarde moet deelbaar zijn door 64 KB (65536).

Met deze para meter wordt de waarde van de eigenschap **MaximumKilobytes** van het object **System. Diagnostics. Eventlog** opgegeven dat een klassiek gebeurtenis logboek vertegenwoordigt.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OverflowAction
Hiermee geeft u op wat er gebeurt als het gebeurtenis logboek de maximum grootte heeft bereikt.

De aanvaardbare waarden voor deze parameter zijn:

- DoNotOverwrite: bestaande vermeldingen worden bewaard en nieuwe vermeldingen worden verwijderd.
- OverwriteAsNeeded: elke nieuwe vermelding overschrijft de oudste vermelding.
- OverwriteOlder: nieuwe gebeurtenissen overschrijven gebeurtenissen die ouder zijn dan de waarde die is opgegeven door de eigenschap **MinimumRetentionDays** . Als er geen gebeurtenissen ouder zijn dan opgegeven door de waarde van de eigenschap **MinimumRetentionDays** , worden nieuwe gebeurtenissen genegeerd.

Met deze para meter wordt de waarde van de eigenschap **OverflowAction** van het object **System. Diagnostics. Eventlog** opgegeven dat een klassiek gebeurtenis logboek vertegenwoordigt.

```yaml
Type: System.Diagnostics.OverflowAction
Parameter Sets: (All)
Aliases: OFA
Accepted values: OverwriteOlder, OverwriteAsNeeded, DoNotOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RetentionDays
Hiermee geeft u het minimum aantal dagen op dat een gebeurtenis in het gebeurtenis logboek moet blijven.

Met deze para meter wordt de waarde van de eigenschap **MinimumRetentionDays** van het object **System. Diagnostics. Eventlog** opgegeven dat een klassiek gebeurtenis logboek vertegenwoordigt.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: MRD

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

### Geen
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* Als u deze cmdlet wilt gebruiken in Windows Vista en latere versies van Windows, opent u Windows Power shell met de optie als administrator uitvoeren.

  Met deze cmdlet worden de eigenschappen van het object **System. Diagnostics. Eventlog** gewijzigd dat een klassiek gebeurtenis logboek vertegenwoordigt.
Als u de huidige instellingen van de eigenschappen van het gebeurtenis logboek wilt zien, typt u `Get-EventLog -List` .

*

## GERELATEERDE KOPPELINGEN

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[Nieuw-gebeurtenis logboek](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Weer geven-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
