---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: 695a13d4fbbf60caadeed994c1aa9c36432be917
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250832"
---
# Clear-EventLog

## SAMENVATTING
Hiermee worden alle vermeldingen uit de opgegeven gebeurtenis logboeken op de lokale of externe computers gewist.

## SYNTAXIS

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Clear-EventLog` cmdlet worden alle vermeldingen uit de opgegeven gebeurtenis logboeken op de lokale computer of op externe computers verwijderd.
Als u wilt gebruiken `Clear-EventLog` , moet u lid zijn van de groep Administrators op de desbetreffende computer.

De cmdlets die het zelfstandig naam woord van het **gebeurtenissen logboek** bevatten (de Eventlog-cmdlets) werken alleen in klassieke gebeurtenis Logboeken.
Als u gebeurtenissen wilt ophalen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van Windows, gebruikt u de cmdlet Get-WinEvent.

## VOORBEELDEN

### Voor beeld 1: specifieke gebeurtenis logboek typen wissen van de lokale computer

```powershell
Clear-EventLog "Windows PowerShell"
```

Met deze opdracht worden de vermeldingen uit het gebeurtenis logboek van Windows Power shell op de lokale computer gewist.

### Voor beeld 2: specifieke meerdere logboek typen wissen van de lokale en externe computers

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

Met deze opdracht worden alle vermeldingen in de logboeken Microsoft Office Diagnostics (ODiag) en Microsoft Office Sessions (OSession) op de lokale computer en de Server02 externe computer gewist.

### Voor beeld 3: alle logboeken op de opgegeven computers wissen vervolgens de lijst met gebeurtenis logboeken weer geven

```powershell
Clear-EventLog -LogName application, system -confirm
```

Met deze opdracht wordt u om bevestiging gevraagd voordat de vermeldingen in de opgegeven gebeurtenis logboeken worden verwijderd.

### Voor beeld 4: alle logboeken op de opgegeven computers wissen vervolgens de lijst met gebeurtenis logboeken weer geven

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

Met deze functie worden alle gebeurtenis logboeken op de opgegeven computers gewist en wordt vervolgens de resulterende lijst met gebeurtenis logboeken weer gegeven.

U ziet dat er een paar vermeldingen zijn toegevoegd aan de systeem-en beveiligings Logboeken nadat de logboeken zijn gewist, maar voordat ze werden weer gegeven.

## PARAMETERS

### -ComputerName

Hiermee geeft u een externe computer.
Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een Internet Protocol (IP)-adres of een Fully Qualified Domain Name van een externe computer.
Typ de computer naam, een punt (.) of ' localhost ' om de lokale computer op te geven.

Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.
U kunt de para meter **ComputerName** gebruiken `Get-EventLog` , zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
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
Accept pipeline input: True (ByPropertyName)
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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### Geen

U kunt geen objecten pipeen naar `Clear-EventLog` .

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

- Als u wilt gebruiken `Clear-EventLog` voor Windows Vista en latere versies van Windows, start u Windows Power shell met de optie als administrator uitvoeren.

## GERELATEERDE KOPPELINGEN

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[Nieuw-gebeurtenis logboek](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Weer geven-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
