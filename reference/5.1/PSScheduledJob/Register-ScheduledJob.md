---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/register-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ScheduledJob
ms.openlocfilehash: 89887474142490a71d372577576fb0059b4ff12e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250301"
---
# Register-ScheduledJob

## SAMENVATTING
Hiermee maakt u een geplande taak.

## SYNTAXIS

### Script Block (standaard)

```
Register-ScheduledJob [-ScriptBlock] <ScriptBlock> [-Name] <String>
 [-Trigger <ScheduledJobTrigger[]>] [-InitializationScript <ScriptBlock>] [-RunAs32]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-ScheduledJobOption <ScheduledJobOptions>] [-ArgumentList <Object[]>] [-MaxResultCount <Int32>]
 [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Bestandspad

```
Register-ScheduledJob [-FilePath] <String> [-Name] <String> [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-ArgumentList <Object[]>] [-MaxResultCount <Int32>] [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Register-ScheduledJob` cmdlet maakt geplande taken op de lokale computer.

Een geplande taak is een Windows Power shell-achtergrond taak die automatisch kan worden gestart in een eenmalige of terugkerende planning. Geplande taken worden op schijf opgeslagen en geregistreerd in taak planner.
De taken kunnen worden beheerd in taak planner of met behulp van de geplande taak cmdlets in Windows Power shell.

Wanneer een geplande taak wordt gestart, wordt een exemplaar van de geplande taak gemaakt. Geplande taak exemplaren zijn identiek aan Windows Power shell-achtergrond taken, behalve dat de resultaten worden opgeslagen op schijf. Gebruik de taak-cmdlets, zoals `Start-Job` , `Get-Job` en `Receive-Job` om de resultaten van de taak exemplaren te bekijken, weer te geven en op te halen.

Gebruiken `Register-ScheduledJob` om een nieuwe geplande taak te maken. Als u de opdrachten wilt opgeven die door de geplande taak worden uitgevoerd, gebruikt u de para meter **script Block** . Als u een script wilt opgeven dat door de taak wordt uitgevoerd, gebruikt u de **filepath** -para meter.

Windows Power shell: geplande taken gebruiken dezelfde taak triggers en taak opties die taak planner gebruikt voor geplande taken.

Met de **trigger** parameter van worden `Register-ScheduledJob` een of meer taak triggers toegevoegd waarmee de taak wordt gestart. De **trigger** parameter is optioneel. u kunt triggers toevoegen wanneer u de geplande taak maakt, taak triggers later toevoegen, de para meter **RunNow** toevoegen om de taak onmiddellijk te starten. Gebruik de `Start-Job` cmdlet om de taak onmiddellijk te starten, of sla de niet-geactiveerde geplande taak op als een sjabloon voor andere taken.

Met de para meter **Options** kunt u de instellingen van de opties voor de geplande taak aanpassen. De para meter **Options** is optioneel, zodat u taak opties kunt instellen wanneer u de geplande taak maakt of op elk gewenst moment wijzigt. Omdat de instellingen van de taak kunnen voor komen dat de geplande taak wordt uitgevoerd, controleert u de taak opties en stelt u deze zorgvuldig in.

`Register-ScheduledJob` is een van een verzameling cmdlets voor taak planning in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.

Zie de artikelen in de **PSScheduledJob** -module voor meer informatie over geplande taken.
Importeer de **PSScheduledJob** -module en typ vervolgens: `Get-Help about_Scheduled*` of Zie [about_Scheduled_Jobs](./about/about_scheduled_jobs.md).

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een geplande taak maken

In dit voor beeld wordt een geplande taak gemaakt op de lokale computer.

```powershell
Register-ScheduledJob -Name "Archive-Scripts" -ScriptBlock {
  Get-ChildItem $home\*.ps1 -Recurse |
    Copy-Item -Destination "\\Server\Share\PSScriptArchive"
}
```

`Register-ScheduledJob` maakt gebruik van de para meter **name** voor het maken van de taak **Archive-scripts** gepland.
De para meter **script Block** wordt uitgevoerd `Get-ChildItem` die de `$home` map recursief doorzoekt naar `.ps1` bestanden. Met de `Copy-Item` cmdlet worden de bestanden gekopieerd naar een map die is opgegeven door de para meter **Destination** .

Omdat de geplande taak geen trigger bevat, wordt deze niet automatisch gestart. U kunt taak triggers toevoegen met `Add-JobTrigger` , de `Start-Job` cmdlet gebruiken om de taak op aanvraag te starten of de geplande taak gebruiken als een sjabloon voor andere geplande taken.

### Voor beeld 2: een geplande taak maken met triggers en aangepaste opties

In dit voor beeld ziet u hoe u een geplande taak maakt met een taak trigger en aangepaste taak opties.

```powershell
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
$path = "\\Srv01\Scripts\UpdateVersion.ps1"
Register-ScheduledJob -Name "UpdateVersion" -FilePath $path -ScheduledJobOption $O -Trigger $T
```

De `$O` variabele slaat het taak optie object op dat de `New-ScheduledJobOption` cmdlet heeft gemaakt. Met de opties wordt de geplande taak gestart, zelfs als de computer niet inactief is, wordt de computer geactiveerd om de taak uit te voeren, indien nodig, en kunnen meerdere exemplaren van de taak in een reeks worden uitgevoerd.

De `$T` variabele slaat het resultaat van de `New-JobTrigger` cmdlet op om een taak trigger te maken waarmee een taak elke andere maandag om 9:00 uur wordt gestart.

De `$path` variabele slaat het pad naar het `UpdateVersion.ps1` script bestand op.

`Register-ScheduledJob` maakt gebruik van de **naam** parameter om de geplande taak **UpdateVersion** te maken.
De **filepath** para meter wordt gebruikt `$path` om het script op te geven dat door de taak wordt uitgevoerd. De para meter **ScheduledJobOption** maakt gebruik van de taak opties die zijn opgeslagen in `$O` . De **trigger** parameter maakt gebruik van de taak triggers die zijn opgeslagen in `$T` .

### Voor beeld 3: hash-tabellen gebruiken om een trigger en geplande taak opties op te geven

Dit voor beeld heeft hetzelfde effect als de opdracht in voor beeld 2. Er wordt een geplande taak gemaakt met behulp van hash-tabellen om de waarden van de **trigger** -en **ScheduledJobOption** -para meters op te geven. De `$O` variabelen en die `$T` in voor beeld 2 zijn gedefinieerd, worden vervangen door hash-tabellen.

```powershell
$T = @{
  Frequency="Weekly"
  At="9:00PM"
  DaysOfWeek="Monday"
  Interval=2
}
$O = @{
  WakeToRun=$true
  StartIfNotIdle=$false
  MultipleInstancePolicy="Queue"
}
Register-ScheduledJob -Trigger $T -ScheduledJobOption $O -Name UpdateVersion -FilePath "\\Srv01\Scripts\Update-Version.ps1"
```

### Voor beeld 4: geplande taken maken op externe computers

In dit voor beeld wordt de geplande taak **EnergyData** op meerdere externe computers gemaakt. Met de geplande taak wordt een script uitgevoerd waarmee onbewerkte gegevens worden verzameld en opgeslagen in een actief logboek op de externe computer.

```powershell
$Cred = Get-Credential
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Invoke-Command -ComputerName (Get-Content Servers.txt) -Credential $Cred -ScriptBlock {
  $params = @{
      Name = "Get-EnergyData"
      FilePath = "\\Srv01\Scripts\Get-EnergyData.ps1"
      ScheduledJobOption = $using:O
      Trigger = $using:T
  }
  Register-ScheduledJob @params
}
```

De `$Cred` variabele slaat referenties op in een **PSCredential** -object voor een gebruiker met machtigingen voor het maken van geplande taken. De `$O` variabele bevat de taak opties die zijn gemaakt met `New-ScheduledJobOption` . De `$T` variabele bevat de taak triggers die zijn gemaakt met `New-JobTrigger` .

De `Invoke-Command` cmdlet gebruikt de para meter **ComputerName** om een lijst met server namen uit het bestand op te halen `Servers.txt` . De **referentie** parameter haalt het referentie object op dat is opgeslagen in `$Cred` .
De para meter **script Block** voert een `Register-ScheduledJob` opdracht op de computers in het `Servers.txt` bestand uit.

De para meters voor `Register-ScheduledJob` worden gedefinieerd door `$params` . De **naam** parameters geeft aan dat de taak de naam **Get-EnergyData** heeft op elke externe computer. Het **bestandspad** bevat de locatie van het `EnergyData.ps1` script. Het script bevindt zich op een bestands server die beschikbaar is voor alle deelnemende computers. De taak wordt uitgevoerd volgens het schema dat is opgegeven door de taak triggers in `$T` en de taak opties in `$O` .

`Register-ScheduledJob @params`Met de opdracht wordt de geplande taak gemaakt met de para meters uit het script blok.

### Voor beeld 5: een geplande taak maken waarmee een script wordt uitgevoerd op externe computers

In dit voor beeld wordt de geplande **CollectEnergyData** -taak op de lokale computer gemaakt. De taak wordt op meerdere externe computers uitgevoerd.

```powershell
$Admin = Get-Credential
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Register-ScheduledJob -Name "CollectEnergyData" -Trigger $T -MaxResultCount 99 -ScriptBlock {
  $params = @{
    AsJob = $true
    ComputerName = (Get-Content Servers.txt)
    FilePath = '\\Srv01\Scripts\Get-EnergyData.ps1'
    Credential = $using:Admin
    Authentication = 'CredSSP'
  }
  Invoke-Command @params
}
```

De `$Admin` variabele bevat referenties voor een gebruiker met machtigingen voor het uitvoeren van de opdrachten in een **PSCredential** -object. De `$T` variabele bevat de taak triggers die zijn gemaakt met `New-JobTrigger` .

De `Register-ScheduledJob` cmdlet gebruikt de para meter **name** om de geplande taak **CollectEnergyData** te maken op de lokale computer. De **trigger** parameter specificeert de taak triggers in `$T` en de para meter **MaxResultCount** verhoogt het aantal opgeslagen resultaten tot 99.

Met de para meter **script Block** worden de `Invoke-Command` para meters gedefinieerd met `$params` . De para meter **AsJob** maakt het object voor de achtergrond taak op de lokale computer, zelfs als het `Energydata.ps1` script wordt uitgevoerd op de externe computers. De para meter **ComputerName** haalt een lijst met server namen uit het `Servers.txt` bestand op. De **referentie** parameter geeft u een gebruikers account op dat gemachtigd is om scripts uit te voeren op de externe computers. En de **verificatie** parameter geeft de waarde **CredSSP** op om gedelegeerde referenties toe te staan.

De `Invoke-Command @params` opdracht wordt uitgevoerd met de para meters uit het script blok.

## PARAMETERS

### -Argument List

Hiermee geeft u waarden op voor de para meters van het script dat is opgegeven met de para meter **filepath** of voor de opdracht die is opgegeven door de para meter **script Block** .

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verificatie

Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren. De standaard waarde is standaard.

De aanvaardbare waarden voor deze parameter zijn:

- Standaard
- Basic
- CredSSP
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.

> [!CAUTION]
> CredSSP-verificatie (Credential Security service provider), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

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

### -Credential

Hiermee geeft u een gebruikers account op dat gemachtigd is om de geplande taak uit te voeren. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in, bijvoorbeeld een van de `Get-Credential` cmdlets. Als u alleen een gebruikers naam opgeeft, wordt u gevraagd een wacht woord op te geven.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

Hiermee geeft u een script op dat door de geplande taak wordt uitgevoerd. Geef het pad op naar een `.ps1` bestand op de lokale computer. Als u standaard waarden voor de script parameters wilt opgeven, gebruikt u de para meter **argument List** .
Elke `Register-ScheduledJob` opdracht moet de para meters **script Block** of **filepath** gebruiken.

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript

Hiermee geeft u het volledige pad naar een Windows Power shell-script ( `.ps1` ) op. Het initialisatie script wordt uitgevoerd in de sessie die is gemaakt voor de achtergrond taak vóór de opdrachten die zijn opgegeven door de para meter **script Block** of het script dat is opgegeven door de para meter **filepath** . U kunt het initialisatie script gebruiken om de sessie te configureren, zoals het toevoegen van bestanden, functies of aliassen, het maken van mappen of het controleren op vereisten.

Als u een script wilt opgeven dat de opdrachten van de primaire opdracht uitvoert, gebruikt u de **filepath** -para meter.

Als het initialisatie script een fout genereert, zelfs een niet-afsluit fout, wordt het huidige exemplaar van de geplande taak niet uitgevoerd en is de status **mislukt**.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxResultCount

Hiermee geeft u op hoeveel items van de taak resultaat voor de geplande taak worden bewaard. De standaard waarde is 32.

Windows Power shell slaat de uitvoerings geschiedenis en resultaten van elk geactiveerd exemplaar van de geplande taak op schijf op. De waarde van deze para meter bepaalt het aantal taak exemplaar resultaten dat voor deze geplande taak wordt opgeslagen. Wanneer het aantal taak exemplaren deze waarde overschrijdt, worden de resultaten van het oudste taak exemplaar door Windows Power shell verwijderd om ruimte te maken voor de resultaten van het nieuwste taak exemplaar.

De geschiedenis van de taak uitvoering en taak resultaten worden opgeslagen in de `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`
directory's op de computer waarop de taak is gemaakt. Als u de uitvoerings geschiedenis wilt zien, gebruikt u de `Get-Job` cmdlet. Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .

Met de para meter **MaxResultCount** wordt de waarde van de eigenschap ExecutionHistoryLength van de geplande taak ingesteld.

Als u de huidige uitvoerings geschiedenis en taak resultaten wilt verwijderen, gebruikt u de para meter **ClearExecutionHistory** van de `Set-ScheduledJob` cmdlet.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een naam op voor de geplande taak. De naam wordt ook gebruikt voor alle gestarte exemplaren van de geplande taak. De naam moet uniek zijn op de computer. Deze parameter is vereist.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAs32

De geplande taak wordt uitgevoerd in een 32-bits proces.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunEvery

Wordt gebruikt om op te geven hoe vaak de taak moet worden uitgevoerd. Gebruik deze optie bijvoorbeeld om elke 15 minuten een taak uit te voeren.

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunNow

Start een taak onmiddellijk, zodra de `Register-ScheduledJob` cmdlet wordt uitgevoerd. Met deze para meter is het niet nodig om taak planner te activeren om een Windows Power shell-script uit te voeren direct na de registratie en hoeven gebruikers geen trigger te maken die een begin datum en-tijd opgeeft.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScheduledJobOption

Opties instellen voor de geplande taak. Voer een **ScheduledJobOptions** -object in, zoals een, dat u maakt met behulp van de `New-ScheduledJobOption` cmdlet of een hash-tabel waarde.

U kunt opties voor een geplande taak instellen wanneer u de plannings taak registreert of de- `Set-ScheduledJobOption` `Set-ScheduledJob` cmdlets gebruikt om de opties te wijzigen.

Veel van de opties en hun standaard waarden bepalen of en wanneer een geplande taak wordt uitgevoerd. Controleer deze opties voordat u een taak plant. Zie voor een beschrijving van de opties voor geplande taken, met inbegrip van de standaard waarden `New-ScheduledJobOption` .

Als u een hash-tabel wilt verzenden, gebruikt u de volgende sleutels. In de volgende hash-tabel worden de sleutels weer gegeven met de standaard waarden.

`@{StartIfOnBattery=$False; StopIfGoingOnBattery=$True; WakeToRun=$False; StartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False; ShowInTaskScheduler=$True; RunElevated=$False; RunWithoutNetwork=$False; DoNotAllowDemandStart=$False; MultipleInstancePolicy="IgnoreNew"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script Block

Hiermee geeft u de opdrachten op die door de geplande taak worden uitgevoerd. Plaats de opdrachten tussen accolades ( `{}` ) om een script blok te maken. Als u standaard waarden voor opdracht parameters wilt opgeven, gebruikt u de para meter **argument List** .

Elke `Register-ScheduledJob` opdracht moet de para meters **script Block** of **filepath** gebruiken.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Trigger

Hiermee geeft u de triggers voor de geplande taak op. Voer een of meer **ScheduledJobTrigger** -objecten in, zoals de objecten die de `New-JobTrigger` cmdlet retourneert of een hash-tabel met sleutels en waarden van de taak trigger.

Met een taak trigger wordt de taak plannen gestart. Met de trigger kan een eenmalige of terugkerende geplande taak of een gebeurtenis worden opgegeven, bijvoorbeeld wanneer een gebruiker zich aanmeldt of als Windows wordt gestart.

De **trigger** parameter is optioneel. U kunt een trigger toevoegen wanneer u de geplande taak maakt, de `Add-JobTrigger` `Set-JobTrigger` cmdlets, of gebruiken `Set-ScheduledJob` om taak triggers later toe te voegen of te wijzigen, of gebruik de `Start-Job` cmdlet om de geplande taak onmiddellijk te starten. U kunt ook een geplande taak maken en onderhouden zonder een trigger die als sjabloon wordt gebruikt.

Als u een hash-tabel wilt verzenden, gebruikt u de volgende sleutels:

- **Frequentie** : dagelijks, wekelijks, AtStartup, AtLogon
- **Op** : een geldige tijd reeks
- **DaysOfWeek** -een combi natie van namen van dagen
- **Interval** -een wille keurig geldig frequentie-interval
- **RandomDelay** : een geldige time span-teken reeks
- **Gebruiker** : een geldige gebruiker. Wordt alleen gebruikt met de AtLogon-frequentie waarde

Bijvoorbeeld:

`@{Frequency="Once"; At="3am"; DaysOfWeek="Monday", "Wednesday"; Interval=2; RandomDelay="30minutes"; User="Domain1\User01"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt de pijp lijn geen invoer naar deze cmdlet sturen.

## UITVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition

## OPMERKINGEN

Elke geplande taak wordt opgeslagen in een submap van de `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` map op de lokale computer.
De submap heeft de naam voor de geplande taak en bevat een XML-bestand voor de geplande taak en records van de uitvoerings geschiedenis. Zie [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md)voor meer informatie over geplande taken op schijf.

Geplande taken die u in Windows Power Shell maakt, worden weer gegeven in taak planner in de `Library\Microsoft\Windows\PowerShell\ScheduledJobs` map taak planner. U kunt taak planner gebruiken om de geplande taak weer te geven en te bewerken.

U kunt taak planner, het **schtasks.exe** opdracht regel programma en de cmdlets van de taak planner gebruiken om geplande taken te beheren die u met de geplande taak-cmdlets maakt. U kunt de geplande taak-cmdlets echter niet gebruiken voor het beheren van taken die u maakt in taak planner.

Als een geplande taak mislukt, wordt een fout bericht geretourneerd door Windows Power shell. Als de taak echter mislukt wanneer taak planner probeert deze uit te voeren, is de fout niet beschikbaar in Windows Power shell.

Als een geplande taak niet wordt uitgevoerd, gebruikt u de volgende methoden om de reden te achterhalen:

- Controleer of de taak trigger juist is ingesteld.
  - Controleer of aan de voor waarden die zijn ingesteld in de taak opties is voldaan.
- Controleer of het gebruikers account waarmee de taak wordt uitgevoerd, gemachtigd is om de opdrachten of scripts in de taak uit te voeren.
- Controleer de geschiedenis van de taak planner op fouten.
- Controleer het gebeurtenis logboek van de taak planner op fouten.

Zie [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md)voor meer informatie.

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
