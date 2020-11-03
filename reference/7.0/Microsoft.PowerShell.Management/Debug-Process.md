---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/debug-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Process
ms.openlocfilehash: 9d2b9ce8d9aa0a1e75c0af0f2ed57aca41ec7791
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249386"
---
# Debug-Process

## SAMENVATTING
De uitvoering van een of meer processen die worden uitgevoerd op de lokale computer.

## SYNTAXIS

### Naam (standaard)

```
Debug-Process [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Debug-Process [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Input object

```
Debug-Process -InputObject <Process[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **debug-process** voegt een fout opsporingsprogramma toe aan een of meer actieve processen op een lokale computer.
U kunt de processen opgeven op basis van hun proces naam of proces-ID (PID), of u kunt proces objecten door sluizen naar deze cmdlet.

Met deze cmdlet wordt het fout opsporingsprogramma dat momenteel is geregistreerd voor het proces, gekoppeld.
Voordat u deze cmdlet kunt gebruiken, moet u controleren of een fout opsporingsprogramma is gedownload en correct is geconfigureerd.

## VOORBEELDEN

### Voor beeld 1: een fout opsporingsprogramma koppelen aan een proces op de computer

```
PS C:\> Debug-Process -Name "Windows Powershell"
```

Met deze opdracht koppelt u een fout opsporingsprogramma aan het Power Shell-proces op de computer.

### Voor beeld 2: een fout opsporingsprogramma koppelen aan alle processen die met de opgegeven teken reeks beginnen

```
PS C:\> Debug-Process -Name "SQL*"
```

Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan alle processen met namen die met SQL beginnen.

### Voor beeld 3: een fout opsporingsprogramma aan meerdere processen koppelen

```
PS C:\> Debug-Process "Winlogon", "Explorer", "Outlook"
```

Met deze opdracht koppelt u een fout opsporingsprogramma aan de Winlogon-, Explorer-en Outlook-processen.

### Voor beeld 4: een fout opsporingsprogramma koppelen aan meerdere proces-Id's

```
PS C:\> Debug-Process -Id 1132, 2028
```

Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de processen met proces-id 1132 en 2028.

### Voor beeld 5: Get-Process gebruiken om een proces te verkrijgen en vervolgens een fout opsporingsprogramma aan toe te voegen

```
PS C:\> Get-Process "Windows PowerShell" | Debug-Process
```

Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de Power shell-processen op de computer.
De cmdlet **Get-process** wordt gebruikt om de Power shell-processen op de computer op te halen en maakt gebruik van een pijplijn operator (|) om de processen te verzenden naar de cmdlet **debug-process** .

Als u een bepaald Power Shell-proces wilt opgeven, gebruikt u de para meter ID van **Get-process**.

### Voor beeld 6: een fout opsporingsprogramma koppelen aan een huidig proces op de lokale computer

```
PS C:\> $PID | Debug-Process
```

Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de huidige Power shell-processen op de computer.

De opdracht maakt gebruik van de $PID automatische variabele, die de proces-ID van het huidige Power Shell-proces bevat.
Vervolgens wordt een pijplijn operator (|) gebruikt om de proces-ID te verzenden naar de cmdlet **debug-process** .

Zie about_Automatic_Variables voor meer informatie over de automatische variabele $PID.

### Voor beeld 7: een fout opsporingsprogramma koppelen aan een proces dat gebruikmaakt van de para meter input object

```
PS C:\> $P = Get-Process "Windows PowerShell"
PS C:\> Debug-Process -InputObject $P
```

Met deze opdracht wordt een fout opsporingsprogramma gekoppeld aan de Power shell-processen op de lokale computer.

De eerste opdracht maakt gebruik van de cmdlet **Get-process** om de Power shell-processen op de computer op te halen.
Het resulterende proces object wordt opgeslagen in de variabele met de naam $P.

De tweede opdracht maakt gebruik van de para meter *input object* van de cmdlet **debug-process** om het proces object in de variabele $P te verzenden.

## PARAMETERS

### -Id

Hiermee geeft u de proces-Id's op van de processen waarvoor u fouten wilt opsporen.
De *id-* parameter naam is optioneel.

Als u de proces-ID van een proces wilt zoeken, typt u `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de proces objecten op die processen vertegenwoordigen waarvoor fouten worden opgespoord.
Voer een variabele in die de proces objecten bevat of een opdracht waarmee de proces objecten worden opgehaald, zoals de cmdlet Get-Process.
U kunt ook proces objecten naar deze cmdlet pipeen.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de namen van de processen waarvoor u fouten wilt opsporen.
Als er meer dan één proces met dezelfde naam is, voegt deze cmdlet een fout opsporingsprogramma toe aan alle processen met die naam.
De para meter *name* is optioneel.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Int32, System. Diagnostics. proces, System. String

U kunt een proces-ID (INT32), een proces object (System. Diagnostics. process) of een proces naam (teken reeks) door sluizen naar deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* Deze cmdlet maakt gebruik van de methode AttachDebugger van de klasse Windows Management Instrumentation (WMI) Win32_Process. Zie [AttachDebugger-methode](https://go.microsoft.com/fwlink/?LinkId=143640) in de MSDN-bibliotheek voor meer informatie over deze methode.

## GERELATEERDE KOPPELINGEN

[Debug-proces](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-process](Start-Process.md)

[Stoppen-proces](Stop-Process.md)

[Wacht proces](Wait-Process.md)
