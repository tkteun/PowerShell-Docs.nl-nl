---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: 52613dae3ba73227818c6c0dec40183ba20ce2a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706048"
---
# Remove-Job

## SAMENVATTING
Hiermee verwijdert u een Power shell-achtergrond taak.

## SYNTAXIS

### SessionIdParameterSet (standaard)

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandParameterSet

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Remove-Job` cmdlet verwijdert Power shell-achtergrond taken die zijn gestart door de `Start-Job` cmdlet of door cmdlets zoals `Invoke-Command` die ondersteuning bieden voor de para meter **AsJob** .

U kunt gebruiken `Remove-Job` om alle taken te verwijderen of geselecteerde taken te verwijderen. De taken worden geïdentificeerd aan de hand van hun **naam**, **ID**, **exemplaar-id**, **opdracht** of **status**. U kunt ook een taak object omlaag naar de pijp lijn verzenden `Remove-Job` . Zonder para meters of parameter waarden `Remove-Job` heeft geen effect.

Sinds Power Shell 3,0 `Remove-Job` kunnen aangepaste taak typen, zoals geplande taken en werk stroom taken, verwijderen. `Remove-Job`Hiermee verwijdert u bijvoorbeeld de geplande taak, alle exemplaren van de geplande taak op schijf en de resultaten van alle geactiveerde taak exemplaren.

Als u probeert een actieve taak te verwijderen, `Remove-Job` mislukt de bewerking. Gebruik de `Stop-Job` cmdlet om een actieve taak te stoppen. Of gebruik `Remove-Job` met de para meter **Force** om een actieve taak te verwijderen.

Taken blijven aanwezig in de cache van de globale taak totdat u de achtergrond taak verwijdert of de Power shell-sessie sluit.

## VOORBEELDEN

### Voor beeld 1: een taak verwijderen door gebruik te maken van de naam

In dit voor beeld worden een variabele en de pijp lijn gebruikt om een taak op naam te verwijderen.

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

`Get-Job` gebruikt de para meter **name** om de taak, **BatchJob**, op te geven. Het taak object wordt opgeslagen in de `$batch` variabele. Het object in `$batch` wordt naar beneden verzonden in de pijp lijn `Remove-Job` .

U kunt ook de **taak** parameter gebruiken, zoals `Remove-Job -Job $batch` .

### Voor beeld 2: alle taken in een sessie verwijderen

In dit voor beeld worden alle taken in de huidige Power shell-sessie verwijderd.

```powershell
Get-job | Remove-Job
```

`Get-Job` Hiermee worden alle taken in de huidige Power shell-sessie opgehaald. De taak objecten worden naar beneden verzonden in de pijp lijn `Remove-Job` .

### Voor beeld 3: NotStarted-taken verwijderen

In dit voor beeld worden alle taken verwijderd uit de huidige Power shell-sessie die nog niet is gestart.

```powershell
Remove-Job -State NotStarted
```

`Remove-Job` gebruikt de para meter **State** om de taak status op te geven.

### Voor beeld 4: taken verwijderen met een beschrijvende naam

In dit voor beeld worden alle taken van de huidige sessie verwijderd met beschrijvende namen die eindigen op * batch * *, inclusief taken die worden uitgevoerd.

```powershell
Remove-Job -Name *batch -Force
```

`Remove-Job` maakt gebruik van de para meter **name** om een taak naam patroon op te geven. Het patroon bevat het sterretje ( `*` ) als Joker teken om alle taak namen te vinden die eindigen op **batch**. Met de para meter **Force** worden taken verwijderd die worden uitgevoerd.

### Voor beeld 5: een taak verwijderen die is gemaakt door Invoke-Command

In dit voor beeld wordt een taak die op een externe computer is gestart, verwijderd met behulp `Invoke-Command` van de para meter **AsJob** .

Omdat in het voor beeld de para meter **AsJob** wordt gebruikt, wordt het taak object op de lokale computer gemaakt.
Maar de taak wordt uitgevoerd op een externe computer. Als gevolg hiervan kunt u lokale opdrachten gebruiken om de taak te beheren.

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

`Invoke-Command` Hiermee wordt een taak uitgevoerd op de **Server01** -computer. De para meter **AsJob** voert de **script Block** als een achtergrond taak. Het taak object wordt opgeslagen in de `$job` variabele. Het `$job` variabele-object wordt naar beneden verzonden in de pijp lijn `Remove-Job` .

### Voor beeld 6: een taak verwijderen die is gemaakt door Invoke-Command en Start-Job

In dit voor beeld ziet u hoe u een taak verwijdert op een externe computer die is gestart met `Invoke-Command` om uit te voeren `Start-Job` . Het taak object wordt gemaakt op de externe computer en de externe opdrachten worden gebruikt om de taak te beheren. Een permanente verbinding is vereist voor het uitvoeren van een externe `Start-Job` opdracht.

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

`New-PSSession` Hiermee maakt u een **PSSession**, een permanente verbinding, naar de **Server01** -computer. De verbinding wordt opgeslagen in de `$S` variabele.

`Invoke-Command` maakt verbinding met de sessie die is opgeslagen in `$S` . De **script Block** gebruikt `Start-Job` om een externe taak te starten. De taak voert een `Get-Process` opdracht uit en gebruikt de para meter **name** om een beschrijvende taak naam op te geven, **MyJob**.

`Invoke-Command` maakt gebruik van de `$S` sessie en wordt uitgevoerd `Remove-Job` . De para meter **name** geeft aan dat de taak met de naam **MyJob** wordt verwijderd.

### Voor beeld 7: een taak verwijderen door gebruik te maken van de InstanceId

In dit voor beeld wordt een taak op basis van de **InstanceId** verwijderd.

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

`Start-Job` Hiermee wordt een achtergrond taak gestart en het taak object wordt opgeslagen in de `$job` variabele.

Het object in `$job` wordt naar beneden verzonden in de pijp lijn `Format-List` . De **eigenschaps** parameter maakt gebruik van een asterisk ( `*` ) om op te geven dat alle eigenschappen van het object in een lijst worden weer gegeven.

`Remove-Job` gebruikt de **InstanceId** para meter om de taak op te geven die moet worden verwijderd.

## PARAMETERS

### -Opdracht

Hiermee verwijdert u taken die de opgegeven woorden bevatten in de opdracht. U kunt een door komma's gescheiden matrix invoeren.

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Vraagt u om bevestiging voordat deze `Remove-Job` wordt uitgevoerd.

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

### -Filter

Hiermee verwijdert u taken die voldoen aan de voor waarden die zijn vastgelegd in de bijbehorende hash-tabel. Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.

Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken. Het werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de `Start-Job` .

Deze para meter wordt geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

Hiermee verwijdert u een taak, zelfs als de status van de taak wordt **uitgevoerd**. Als de para meter **Forces** niet wordt opgegeven, worden `Remove-Job` actieve taken niet verwijderd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, InstanceIdParameterSet, NameParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee verwijdert u achtergrond taken met de opgegeven **id**. U kunt een door komma's gescheiden matrix invoeren. De **id** van de taak is een uniek geheel getal dat een taak binnen de huidige sessie identificeert.

Als u de **id** van een taak wilt zoeken, gebruikt u `Get-Job` zonder para meters.

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Hiermee verwijdert u taken met de opgegeven **InstanceId**. U kunt een door komma's gescheiden matrix invoeren. Een **InstanceId** is een unieke GUID waarmee een taak wordt aangeduid.

Als u wilt zoeken naar de **InstanceId** van een taak, gebruikt u `Get-Job` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Taak

Hiermee geeft u de taken die moeten worden verwijderd. Voer een variabele in die de taken bevat of een opdracht waarmee de taken worden opgehaald. U kunt een door komma's gescheiden matrix invoeren.

U kunt taak objecten naar beneden verplaatsen in de pijp lijn `Remove-Job` .

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee verwijdert u alleen taken met de opgegeven beschrijvende naam. Joker tekens zijn toegestaan. U kunt een door komma's gescheiden matrix invoeren.

Beschrijvende namen voor taken zijn niet gegarandeerd uniek, zelfs binnen een Power shell-sessie. Gebruik de para meters **WhatIf** en **confirm** wanneer u bestanden op naam verwijdert.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Status

Hiermee verwijdert u alleen taken met de opgegeven status. Als u taken wilt verwijderen met de status **wordt uitgevoerd**, gebruikt u de para meter **Force** .

Geaccepteerde waarden:

- AtBreakpoint
- Geblokkeerd
- Voltooid
- Ontkoppeld
- Mislukt
- NotStarted
- Wordt uitgevoerd
- Gestopt
- Stoppen
- Onderbroken
- Onderbreken

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Hier wordt weer gegeven wat er gebeurt als er `Remove-Job` wordt uitgevoerd. De cmdlet wordt niet uitgevoerd.

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

### System. Management. Automation. job

U kunt een taak object omlaag verzenden via de pijp lijn `Remove-Job` .

## UITVOER

### Geen

`Remove-Job` Er wordt geen uitvoer gegenereerd.

## OPMERKINGEN

Een Power shell-taak maakt een nieuw proces. Wanneer de taak is voltooid, wordt het proces afgesloten. Wanneer `Remove-Job` wordt uitgevoerd, wordt de status van de taak verwijderd.

Als een taak stopt voordat deze is voltooid en het proces ervan niet is afgesloten, wordt het proces geforceerd beëindigd.

## GERELATEERDE KOPPELINGEN

[about_Jobs](./About/about_Jobs.md)

[about_Job_Details](./About/about_Job_Details.md)

[about_Remote_Jobs](./About/about_Remote_Jobs.md)

[Get-job](Get-Job.md)

[Invoke-opdracht](Invoke-Command.md)

[Receive-job](Receive-Job.md)

[Begin taak](Start-Job.md)

[Stoppen-taak](Stop-Job.md)

[Wait-Job](Wait-Job.md)

