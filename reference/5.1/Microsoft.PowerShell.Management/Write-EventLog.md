---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/write-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-EventLog
ms.openlocfilehash: 4044453cb46b407344619f1edd3227213bf67250
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388243"
---
# Write-EventLog

## SAMENVATTING
Hiermee wordt een gebeurtenis naar een gebeurtenis logboek geschreven.

## SYNTAXIS

```
Write-EventLog [-LogName] <String> [-Source] <String> [[-EntryType] <EventLogEntryType>] [-Category <Int16>]
 [-EventId] <Int32> [-Message] <String> [-RawData <Byte[]>] [-ComputerName <String>] [<CommonParameters>]
```

## BESCHRIJVING
De `Write-EventLog` cmdlet schrijft een gebeurtenis naar een gebeurtenis logboek.

Als u een gebeurtenis naar een gebeurtenis logboek wilt schrijven, moet het gebeurtenis logboek op de computer bestaan en moet de bron zijn geregistreerd voor het gebeurtenis logboek.

De cmdlets die het zelfstandig naam woord van het **gebeurtenissen logboek** bevatten (de **Eventlog** -cmdlets) werken alleen in klassieke gebeurtenis Logboeken. Als u gebeurtenissen wilt ophalen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van het Windows-besturings systeem, gebruikt u de `Get-WinEvent` cmdlet.

## VOORBEELDEN

### Voor beeld 1: een gebeurtenis naar het gebeurtenis logboek van de toepassing schrijven

```
PS C:\> Write-EventLog -LogName "Application" -Source "MyApp" -EventID 3001 -EntryType Information -Message "MyApp added a user-requested feature to the display." -Category 1 -RawData 10,20
```

Met deze opdracht wordt een gebeurtenis van de Mijntoep-bron naar het toepassings gebeurtenis logboek geschreven.

### Voor beeld 2: een gebeurtenis schrijven naar het toepassings gebeurtenis logboek van een externe computer

```
PS C:\> Write-EventLog -ComputerName "Server01" -LogName Application -Source "MyApp" -EventID 3001 -Message "MyApp added a user-requested feature to the display."
```

Met deze opdracht schrijft u een gebeurtenis van de Mijntoep-bron naar het toepassings gebeurtenis logboek op de externe computer Server01.

## PARAMETERS

### -Categorie

Hiermee geeft u een taak categorie op voor de gebeurtenis. Voer een geheel getal in dat is gekoppeld aan de teken reeksen in het categorie bericht bestand voor het gebeurtenis logboek.

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u een externe computer. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer.

Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell. U kunt de para meter **ComputerName** van de `Get-EventLog` cmdlet ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Entry type is

Hiermee geeft u het vermeldings type van de gebeurtenis. De acceptabele waarden voor deze para meter zijn: fout, waarschuwing, informatie, SuccessAudit en FailureAudit. De standaard waarde is informatie.

Zie [EventLogEntryType Enumeration (Engelstalig)](/dotnet/api/system.diagnostics.eventlogentrytype)voor een beschrijving van de waarden.

```yaml
Type: System.Diagnostics.EventLogEntryType
Parameter Sets: (All)
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Gebeurtenis-eigen

Hiermee geeft u de gebeurtenis-id op. Deze parameter is vereist. De maximum waarde voor de **gebeurtenis** -para meter 65535.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ID, EID

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

Hiermee geeft u de naam op van het logboek waarnaar de gebeurtenis wordt geschreven. Voer de naam van het logboek in. De logboek naam is de waarde van de eigenschap **logboek** , niet de **LogDisplayName**. Joker tekens zijn niet toegestaan.
Deze parameter is vereist.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bericht

Hiermee geeft u het gebeurtenis bericht. Deze parameter is vereist.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MSG

Required: True
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RawData

Hiermee geeft u de binaire gegevens in bytes op die zijn gekoppeld aan de gebeurtenis.

```yaml
Type: System.Byte[]
Parameter Sets: (All)
Aliases: RD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Hiermee geeft u de bron van de gebeurtenis, meestal de naam van de toepassing die de gebeurtenis naar het logboek schrijft.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 1
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

### System. Diagnostics. EventLogEntry
Deze cmdlet retourneert objecten die de gebeurtenissen in de logboeken vertegenwoordigen.

## OPMERKINGEN

Als u wilt gebruiken `Write-EventLog` , start u Windows Power shell met de optie als administrator uitvoeren.

## GERELATEERDE KOPPELINGEN

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[Nieuw-gebeurtenis logboek](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Weer geven-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
