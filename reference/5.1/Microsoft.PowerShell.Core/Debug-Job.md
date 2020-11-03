---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/debug-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Job
ms.openlocfilehash: d36d15194ce1d4a48a59ad8bb8621b3c9c1a74ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249979"
---
# Debug-Job

## SAMENVATTING
De uitvoering van een actieve achtergrond, externe of Windows Power shell-werk stroom taak wordt ongebruikt.

## SYNTAXIS

### JobParameterSet (standaard)

```
Debug-Job [-Job] <Job> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobNameParameterSet

```
Debug-Job [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobIdParameterSet

```
Debug-Job [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobInstanceIdParameterSet

```
Debug-Job [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **debug-job** kunt u fouten opsporen in scripts die in taken worden uitgevoerd.
De cmdlet is ontworpen voor het opsporen van fouten in Windows Power shell-werk stroom taken, achtergrond taken en taken die worden uitgevoerd in externe sessies.
**Debug: de taak** accepteert een actief taak object, naam, id of exemplaar-id als invoer, en start een foutopsporingssessie op het script dat wordt uitgevoerd.
De opdracht debugger **Afsluiten** stopt de taak en voert script uit.
Vanaf Windows Power shell 5,0 wordt met de opdracht **Exit** het fout opsporingsprogramma losgekoppeld en kan de taak worden uitgevoerd.

## VOORBEELDEN

### Voor beeld 1: fouten opsporen in een taak op taak-ID

```
PS C:\> Debug-Job -ID 3
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
3      Job3            RemoteJob       Running       True            PowerShellIx         TestWFDemo1.ps1
          Entering debug mode. Use h or ? for help.

          Hit Line breakpoint on 'C:\TestWFDemo1.ps1:8'

          At C:\TestWFDemo1.ps1:8 char:5
          +     Write-Output -InputObject "Now writing output:"
          +     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
          [DBG:PowerShellIx]: PS C:\> > list

              3:
              4:  workflow SampleWorkflowTest
              5:  {
              6:      param ($MyOutput)
              7:
              8:*     Write-Output -InputObject "Now writing output:"
              9:      Write-Output -Input $MyOutput
             10:
             11:      Write-Output -InputObject "Get PowerShell process:"
             12:      Get-Process -Name powershell
             13:
             14:      Write-Output -InputObject "Workflow function complete."
             15:  }
             16:
             17:  # Call workflow function
             18:  SampleWorkflowTest -MyOutput "Hello"
```

Met deze opdracht wordt het einde van een taak met de ID 3 gekraakt.

## PARAMETERS

### -Id
Hiermee geeft u het ID-nummer van een actieve taak op.
Als u het ID-nummer van een taak wilt ophalen, voert u de Get-Job-cmdlet uit.

```yaml
Type: System.Int32
Parameter Sets: JobIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId
Hiermee geeft u de exemplaar-ID-GUID van een actieve taak op.
Als u de *InstanceId* van een taak wilt ophalen, voert u de cmdlet **Get-job** uit, pijpleidingt u de resultaten in een **indeling-*-** cmdlet, zoals weer gegeven in het volgende voor beeld:

`Get-Job | Format-List -Property Id,Name,InstanceId,State`

```yaml
Type: System.Guid
Parameter Sets: JobInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Taak
Hiermee wordt een actief taak object opgegeven.
De eenvoudigste manier om deze para meter te gebruiken is het opslaan van de resultaten van een **Get-job-** opdracht die de actieve taak retourneert die u wilt opsporen in een variabele, en vervolgens de variabele opgeven als de waarde van deze para meter.

```yaml
Type: System.Management.Automation.Job
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Hiermee geeft u een taak op met de beschrijvende naam van de taak.
Wanneer u een taak start, kunt u een taak naam opgeven door de para meter *JobName* toe te voegen in cmdlets, zoals Invoke-Command en start taak.

```yaml
Type: System.String
Parameter Sets: JobNameParameterSet
Aliases:

Required: True
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

## INVOER

### System. Management. Automation. RemotingJob

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-job](Get-Job.md)

[Receive-job](Receive-Job.md)

[Verwijderen-taak](Remove-Job.md)

[Resume-job](Resume-Job.md)

[Begin taak](Start-Job.md)

[Stoppen-taak](Stop-Job.md)

[Onderbreken-taak](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
