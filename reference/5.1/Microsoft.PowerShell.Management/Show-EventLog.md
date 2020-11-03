---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-EventLog
ms.openlocfilehash: e8dbcf1aa4280c0481714a8a9fb24f2e5ef79ffe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250545"
---
# Show-EventLog

## SAMENVATTING
Hiermee worden de gebeurtenis logboeken van de lokale of externe computer in Logboeken weer gegeven.

## SYNTAXIS

```
Show-EventLog [[-ComputerName] <String>] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Show-Eventlog** wordt geopend logboeken op de lokale computer en wordt weer gegeven in alle klassieke gebeurtenis logboeken op de lokale computer of een externe computer.

Als u Logboeken wilt openen op Windows Vista en latere versies van het Windows-besturings systeem, moet de huidige gebruiker lid zijn van de groep Administrators op de lokale computer.

De cmdlets die het zelfstandig naam woord van het **gebeurtenissen logboek** bevatten (de **Eventlog** -cmdlets) werken alleen in klassieke gebeurtenis Logboeken.
Als u gebeurtenissen wilt ophalen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van het Windows-besturings systeem, gebruikt u de cmdlet Get-WinEvent.

## VOORBEELDEN

### Voor beeld 1: gebeurtenis logboeken voor de lokale computer weer geven

```
PS C:\> Show-EventLog
```

Met deze opdracht wordt Logboeken geopend en weer gegeven in de klassieke gebeurtenis logboeken op de lokale computer.

### Voor beeld 2: gebeurtenis logboeken weer geven voor een externe computer

```
PS C:\> Show-EventLog -ComputerName "Server01"
```

Met deze opdracht wordt Logboeken geopend en weer gegeven in de klassieke gebeurtenis logboeken op de Server01-computer.

## PARAMETERS

### -ComputerName
Hiermee geeft u een externe computer.
**Show-Eventlog** worden de gebeurtenis logboeken van de opgegeven computer in Logboeken op de lokale computer weer gegeven.
Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer.

Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.
U kunt de para meter *ComputerName* ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 0
Default value: None
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

* De Windows Power shell-opdracht prompt wordt weer gegeven zodra Logboeken wordt geopend. U kunt in de huidige sessie werken terwijl Logboeken is geopend.

  Omdat deze cmdlet een gebruikers interface vereist, werkt deze niet op Server Core-installaties van Windows Server.

*

## GERELATEERDE KOPPELINGEN

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[Nieuw-gebeurtenis logboek](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Write-EventLog](Write-EventLog.md)
