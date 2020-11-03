---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-EventLog
ms.openlocfilehash: 4cf29146727c9a54715459a2d56e47a27c5bacc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250582"
---
# Remove-EventLog

## SAMENVATTING
Hiermee verwijdert u een gebeurtenis logboek of maakt u de registratie van een gebeurtenis bron ongedaan.

## SYNTAXIS

### Standaard (standaard instelling)

```
Remove-EventLog [[-ComputerName] <String[]>] [-LogName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Bron

```
Remove-EventLog [[-ComputerName] <String[]>] [-Source <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Remove-Eventlog** verwijdert een gebeurtenis logboek bestand van een lokale of externe computer en maakt de registratie van alle gebeurtenis bronnen voor het logboek ongedaan.
U kunt deze cmdlet ook gebruiken voor het opheffen van de registratie van gebeurtenis bronnen zonder gebeurtenis logboeken te verwijderen.

De cmdlets die de zelfstandig naam van het **gebeurtenis logboek** bevatten, de **Eventlog** -cmdlets, werken alleen in klassieke gebeurtenis Logboeken.
Gebruik Get-Wine vent om gebeurtenissen op te halen uit logboeken die gebruikmaken van de Windows-gebeurtenis logboek technologie in Windows Vista en latere versies van het Windows-besturings systeem.

Let op: met deze cmdlet kunnen gebeurtenis logboeken van het besturings systeem worden verwijderd. Dit kan leiden tot toepassings fouten en onverwacht gedrag van het systeem.

## VOORBEELDEN

### Voor beeld 1: een gebeurtenis logboek van de lokale computer verwijderen

```
PS C:\> Remove-EventLog -LogName "MyLog"
```

Met deze opdracht wordt het MyLog-gebeurtenis logboek van de lokale computer verwijderd en worden de registratie van de gebeurtenis bronnen ongedaan gemaakt.

### Voor beeld 2: een gebeurtenis logboek van verschillende computers verwijderen

```
PS C:\> Remove-EventLog -LogName "MyLog", "TestLog" -ComputerName "Server01", "Server02", "localhost"
```

Met deze opdracht worden de gebeurtenis logboeken MyLog en TestLog van de lokale computer en de externe computers Server01 en Server02 verwijderd.
Met deze opdracht wordt ook de registratie van de gebeurtenis bronnen voor deze logboeken ongedaan gemaakt.

### Voor beeld 3: een gebeurtenis bron verwijderen

```
PS C:\> Remove-EventLog -Source "MyApp"
```

Met deze opdracht wordt de gebeurtenis bron MyApp verwijderd uit de logboeken op de lokale computer.
Wanneer de opdracht is voltooid, kan het programma Mijntoep niet schrijven naar gebeurtenis Logboeken.

### Voor beeld 4: een gebeurtenis logboek verwijderen en de actie bevestigen

```
The first command lists the event logs on the local computer.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
15,168      7 OverwriteAsNeeded          12 ZapLog

The second command deletes the ZapLog event log.
PS C:\> Remove-EventLog -LogName "ZapLog"

The third command lists the event logs again. The ZapLog event log no longer appears in the list.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
```

Deze opdrachten laten zien hoe u de gebeurtenis logboeken op een computer kunt weer geven en kunt controleren of de opdracht **Remove-Eventlog** is geslaagd.

### Voor beeld 5: een gebeurtenis bron verwijderen en de actie bevestigen

```
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'" | foreach {$_.sources}
MyApp
TestApp
PS C:\> Remove-Eventlog -Source "MyApp"
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'"} | foreach {$_.sources}
TestApp
```

Deze opdrachten gebruiken de cmdlet Get-WmiObject om de gebeurtenis bronnen op de lokale computer weer te geven.
U kunt deze opdrachten om het succes van een opdracht te controleren of om een gebeurtenis bron te verwijderen.

Met de eerste opdracht worden de gebeurtenis bronnen van het TestLog-gebeurtenis logboek op de lokale computer opgehaald.
MyApp is een van de bronnen.

De tweede opdracht maakt gebruik van de para meter *Source* van **Remove-Eventlog** om de gebeurtenis bron MyApp te verwijderen.

De derde opdracht is identiek aan de eerste.
U ziet dat de gebeurtenis bron MyApp is verwijderd.

## PARAMETERS

### -ComputerName
Hiermee geeft u een externe computer.
Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer.
Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.

Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.
U kunt de para meter *ComputerName* van **Remove-Eventlog gebruiken,** zelfs als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
Hiermee geeft u de gebeurtenis Logboeken.
Voer de logboek naam in van een of meer gebeurtenis logboeken, gescheiden door komma's.
De logboek naam is de waarde van de eigenschap **logboek** , niet de *LogDisplayName*. joker tekens zijn niet toegestaan.
Deze parameter is vereist.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source
Hiermee geeft u de gebeurtenis bronnen op die met deze cmdlet worden geregistreerd.
Voer de bron namen in, niet de naam van het uitvoer bare bestand, gescheiden door komma's.

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: SRC

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
Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

* Als u **Remove-Eventlog** wilt gebruiken in Windows Vista en latere versies van het Windows-besturings systeem, start u Windows Power shell met de optie als administrator uitvoeren.

  Als u een gebeurtenis logboek verwijdert en vervolgens het logboek opnieuw maakt, kunt u niet dezelfde gebeurtenis bronnen registreren.
Toepassingen die de gebeurtenis bronnen hebben gebruikt om vermeldingen naar het oorspronkelijke logboek te schrijven, kunnen niet naar het nieuwe logboek schrijven.

* Wanneer u de registratie van een gebeurtenis bron voor een bepaald logboek ongedaan maakt, kan de gebeurtenis bron mogelijk geen vermeldingen in andere gebeurtenis logboeken schrijven.

## GERELATEERDE KOPPELINGEN

[Clear-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Limit-EventLog](Limit-EventLog.md)

[Nieuw-gebeurtenis logboek](New-EventLog.md)

[Remove-EventLog](Remove-EventLog.md)

[Weer geven-EventLog](Show-EventLog.md)

[Write-EventLog](Write-EventLog.md)
