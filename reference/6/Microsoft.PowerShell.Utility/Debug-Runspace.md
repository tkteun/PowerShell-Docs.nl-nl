---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: 96282d28249f28744cf7dff436fa2e6c601c10ca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251129"
---
# Debug-Runspace

## SAMENVATTING
Hiermee wordt een interactieve foutopsporingssessie gestart met een runs Pace.

## SYNTAXIS

### RunspaceParameterSet (standaard)

```
Debug-Runspace [-Runspace] <Runspace> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Debug-Runspace [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### IdParameterSet

```
Debug-Runspace [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Debug-Runspace [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Debug-Runspace` cmdlet start een interactieve foutopsporingssessie met een lokale of externe actief runs Pace. U kunt een runs Pace vinden waarvoor u fouten wilt opsporen door eerst uit `Get-Process` te voeren naar processen die zijn gekoppeld aan Power shell, vervolgens `Enter-PSHostProcess` met de proces-id die is opgegeven in de **id-** para meter om aan het proces te koppelen en vervolgens `Get-Runspace` runspaces binnen het Power shell-hostproces weer te geven.

Nadat u een runs Pace hebt geselecteerd voor het opsporen van fouten, als de runs Pace momenteel een opdracht of script uitvoert, of als het script op een onderbrekings punt is gestopt, opent Power shell een sessie voor externe fout opsporing voor de runs Pace. U kunt fouten opsporen in het runs Pace-script op dezelfde manier als met externe-sessie scripts worden opgespoord.

U kunt alleen koppelen aan een Power shell-hostproces als u een beheerder bent op de computer waarop het proces wordt uitgevoerd, of als u het script uitvoert dat u wilt fouten opsporen. U kunt ook het hostproces met de huidige Power shell-sessie niet invoeren. U kunt alleen een hostproces invoeren waarop een andere Power shell-sessie wordt uitgevoerd.

## VOORBEELDEN

### Voor beeld 1: fouten opsporen in een externe runs Pace

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

In dit voor beeld kunt u fouten opsporen in een runs Pace die is geopend op een externe computer, WS10TestServer. Op de eerste regel van de opdracht voert u uit `Get-Process` op de externe computer en filtert u op Windows Power shell-host-processen. In dit voor beeld wilt u de proces-ID 1152, het Windows PowerShell ISE-hostproces, fout opsporing uitvoeren.

In de tweede opdracht voert u uit `Enter-PSSession` om een externe sessie op WS10TestServer te openen. In de derde opdracht koppelt u aan het Windows PowerShell ISE-hostproces dat wordt uitgevoerd op de externe server door uit te voeren `Enter-PSHostProcess` en geeft u de id op van het hostproces dat u hebt verkregen in de eerste opdracht, 1152.

In de vierde opdracht vermeldt u beschik bare runspaces voor proces-ID 1152 door uit te voeren `Get-Runspace` .
U noteert het ID-nummer van de bezet runs Pace; Er wordt een script uitgevoerd waarvoor u fouten wilt opsporen.

In de laatste opdracht start u de fout opsporing van een geopende runs Pace met een script, TestWFVar1.ps1, door uit `Debug-Runspace` te voeren en de runs Pace te identificeren met de id, 2, door de **id-** para meter toe te voegen. Omdat het script een onderbrekings punt bevat, wordt het fout opsporingsprogramma geopend.

## PARAMETERS

### -Id

Hiermee wordt het ID-nummer van een runs Pace opgegeven. U kunt uitvoeren `Get-Runspace` om runs Pace-id's weer te geven.

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u een runs Pace op met de instantie-ID, een GUID die u kunt weer geven door uit te voeren `Get-Runspace` .

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een runs Pace op met de naam. U kunt uitvoeren `Get-Runspace` om de namen van runspaces weer te geven.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Runs Pace

Hiermee geeft u een runs Pace-object op. De eenvoudigste manier om een waarde voor deze para meter op te geven, is door een variabele op te geven die de resultaten van een gefilterde `Get-Runspace` opdracht bevat.

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
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
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. Runspaces. runs Pace

U kunt de resultaten van een opdracht door sluizen `Get-Runspace` naar **debug-runs Pace.**

## UITVOER

## OPMERKINGEN

`Debug-Runspace` werkt op runspaces met de status Opened. Als de status van een runs Pace wordt gewijzigd van geopend in een andere status, wordt die runs Pace automatisch verwijderd uit de lijst met actieve. Een runs Pace wordt alleen toegevoegd aan de actieve lijst als deze voldoet aan de volgende criteria.

- Als deze afkomstig is van invoke-opdracht; dat wil zeggen dat het een `Invoke-Command` GUID-id heeft.
- Als dat het geval is `Debug-Runspace` , heeft het een `Debug-Runspace` GUID-id.
- Als het afkomstig is van een Power shell-werk stroom en de werk stroom taak-ID hetzelfde is als de huidige actieve debugger werk stroom taak-ID.

## GERELATEERDE KOPPELINGEN

[about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[Fout opsporing-taak](../Microsoft.PowerShell.Core/Debug-Job.md)

[Get-runs Pace](Get-Runspace.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)

[Enter-PSHostProcess](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[Enter-PSSession](../Microsoft.PowerShell.Core/Enter-PSSession.md)
