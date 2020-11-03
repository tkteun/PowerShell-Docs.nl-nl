---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/remove-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-JobTrigger
ms.openlocfilehash: adcd74361b1a045a57c7db2f15996f4ea53d6d5b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250300"
---
# Remove-JobTrigger

## SAMENVATTING
Taak triggers uit geplande taken verwijderen.

## SYNTAXIS

### Taak definitie (standaard)

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-InputObject] <ScheduledJobDefinition[]> [<CommonParameters>]
```

### JobDefinitionId

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Id] <Int32[]> [<CommonParameters>]
```

### JobDefinitionName

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Name] <String[]> [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Remove-JobTrigger** verwijdert taak triggers van geplande taken.

Een taak trigger definieert een terugkerende planning of voor waarden voor het starten van een geplande taak.
Als u taak triggers wilt beheren, gebruikt u de cmdlets New-JobTrigger en add-JobTrigger, set-JobTrigger en Set-ScheduledJob.

Gebruik de para meters *name* , *id* of *input object* van **Remove-JobTrigger** om de geplande taken te identificeren van waaruit de triggers worden verwijderd.
Gebruik de para meter *TriggerID* om de taak triggers te identificeren die u wilt verwijderen.
Standaard verwijdert **Remove-JobTrigger** alle taak triggers van een geplande taak.

**Remove-JobTrigger** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: alle taak triggers verwijderen

```
PS C:\> Remove-JobTrigger -Name "Test*"
```

Met deze opdracht worden alle taak triggers verwijderd uit een geplande taak met namen die beginnen met de test.

### Voor beeld 2: geselecteerde taak triggers verwijderen

```
PS C:\> Remove-JobTrigger -Name "BackupArchive" -TriggerID 3
```

Met deze opdracht wordt alleen de derde trigger (ID = 3) verwijderd uit de geplande taak BackupArchive.

### Voor beeld 3: AtStartup-taak triggers uit alle geplande taken verwijderen

```
PS C:\> function Delete-AtStartup
{
    Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.Frequency -eq "AtStartup"} | ForEach-Object { Remove-JobTrigger -InputObject $_.JobDefinition -TriggerID $_.ID}
}
```

Deze functie verwijdert alle AtStartup-taak triggers van alle taken op de lokale computer.
Als u de functie wilt gebruiken, voert u de functie in uw sessie uit en typt u `Delete-AtStartup` .

De functie Delete-AtStartup bevat één opdracht.
De opdracht gebruikt de cmdlet Get-ScheduledJob om de geplande taken op de lokale computer op te halen.
Een pijplijn operator (|) verzendt de geplande taken naar de cmdlet Get-JobTrigger, waarmee alle taak triggers van elk van de geplande taken worden opgehaald.
Een pijplijn operator verzendt de taak triggers naar de cmdlet Where-Object, waarmee taak triggers worden geselecteerd waarbij de waarde van de eigenschap Frequency van de taak trigger gelijk is aan AtStartup.

**JobTrigger** -objecten hebben een eigenschap **taak definitie** die de geplande taak bevat die ze activeren.
De rest van de opdracht gebruikt die waardevolle functie.

Een pijplijn operator verzendt de AtStartup-taak triggers naar de cmdlet ForEach-Object, waarmee de opdracht **Remove-JobTrigger** wordt uitgevoerd op elke AtStartup-trigger.
De waarde van de para meter *input object* van **Remove-JobTrigger** is de geplande taak in de eigenschap taak definitie van de taak trigger.
De waarde van de para meter *TriggerID* is de id in de eigenschap ID van de taak trigger.

### Voor beeld 4: een taak trigger verwijderen uit een externe geplande taak

```
PS C:\> Invoke-Command -ComputerName "Server01" { Remove-JobTrigger -ID 38 -TriggerID 1 }
```

Met deze opdracht wordt de eerste taak trigger uit de inventaris taak op de Server01-computer verwijderd.

De opdracht gebruikt de cmdlet **invoke-opdracht** om de cmdlet **Remove-JobTrigger** uit te voeren op de Server01-computer.
De **Remove-JobTrigger** -cmdlet gebruikt de *id-* para meter voor het identificeren van de geplande inventarisatie taak en de para meter *TriggerID* om de eerste trigger op te geven.
De *id-* para meter is met name handig wanneer meerdere geplande taken dezelfde of vergelijk bare naam hebben.

## PARAMETERS

### -Id
Hiermee geeft u de id-nummers van de geplande taken op.
**Remove-JobTrigger** verwijdert taak triggers uit de opgegeven geplande taken.

Als u het id-nummer van geplande taken op de lokale computer of een externe computer wilt ophalen, gebruikt u de Get-ScheduledJob-cmdlet.

```yaml
Type: System.Int32[]
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object
Hiermee geeft u de geplande taken op.
Voer een variabele in die **ScheduledJob** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJob** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.
U kunt ook **ScheduledJob** -objecten pipeen om **-JobTrigger te verwijderen**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Hiermee geeft u de namen van de geplande taken.
**Remove-JobTrigger** verwijdert de taak triggers uit de opgegeven geplande taken.
Joker tekens worden ondersteund.

Gebruik de cmdlet Get-ScheduledJob om de namen van geplande taken op de lokale computer of een externe computer op te halen.

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TriggerId
Hiermee verwijdert u alleen de opgegeven taak triggers.
Standaard verwijdert **Remove-JobTrigger** alle triggers uit de geplande taken.
Gebruik deze para meter wanneer de geplande taken meerdere taak triggers hebben.

Voer de trigger-Id's in van een of meer taak triggers van een geplande taak.
Als u meerdere geplande taken opgeeft, verwijdert **Remove-JobTrigger** de taak trigger met de opgegeven id uit alle geplande taken.

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition
U kunt geplande taken door sluizen naar de cmdlet **Remove-JobTrigger** .

## UITVOER

### Geen
De cmdlet genereert geen uitvoer.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Enable-JobTrigger](Enable-JobTrigger.md)

[Enable-ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[REGI ster-ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Registratie ongedaan maken-ScheduledJob](Unregister-ScheduledJob.md)
