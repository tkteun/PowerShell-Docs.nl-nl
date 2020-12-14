---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 3a11bdb27f3fe16b7b66e82821a3ffe8fa5f6cfa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706059"
---
# Receive-Job

## SAMENVATTING
Hiermee worden de resultaten van de Power shell-achtergrond taken in de huidige sessie opgehaald.

## SYNTAXIS

### Locatie (standaard)

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### ComputerName

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### Sessie

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### NameParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### SessionIdParameterSet

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## BESCHRIJVING

Met de `Receive-Job` cmdlet worden de resultaten van Power shell-achtergrond taken opgehaald, zoals die zijn gestart met behulp `Start-Job` van de cmdlet of de **AsJob** -para meter van een cmdlet.
U kunt de resultaten van alle taken ophalen of taken identificeren met hun naam, ID, exemplaar-ID, computer naam, locatie of sessie of door een taak object in te dienen.

Wanneer u een Power shell-achtergrond taak start, wordt de taak gestart, maar worden de resultaten niet onmiddellijk weer gegeven. In plaats daarvan wordt met de opdracht een object geretourneerd dat de achtergrond taak vertegenwoordigt.
Het taak object bevat nuttige informatie over de taak, maar bevat niet de resultaten.
Met deze methode kunt u in de sessie blijven werken terwijl de taak wordt uitgevoerd.
Zie [about_Jobs](./About/about_Jobs.md)voor meer informatie over achtergrond taken in Power shell.

De `Receive-Job` cmdlet haalt de resultaten op die zijn gegenereerd op het moment dat de `Receive-Job` opdracht wordt verzonden.
Als de resultaten nog niet zijn voltooid, kunt u aanvullende `Receive-Job` opdrachten uitvoeren om de resterende resultaten te verkrijgen.

Standaard worden taak resultaten uit het systeem verwijderd wanneer u ze ontvangt, maar u kunt de para meter **bewaren** gebruiken om de resultaten op te slaan, zodat u ze opnieuw kunt ontvangen.
Als u de taak resultaten wilt verwijderen, voert u de `Receive-Job` opdracht opnieuw uit zonder de para meter **Keep** , sluit u de sessie of gebruikt `Remove-Job` u de cmdlet om de taak uit de sessie te verwijderen.

Met ingang van Windows Power Shell 3,0 worden `Receive-Job` ook de resultaten van aangepaste taak typen opgehaald, zoals werk stroom taken en exemplaren van geplande taken.
Als u `Receive-Job` wilt inschakelen om de resultaten van een aangepast taak type op te halen, importeert u de module die het aangepaste taak type in de sessie ondersteunt voordat een opdracht wordt uitgevoerd `Receive-Job` , met behulp van de `Import-Module` cmdlet of door een cmdlet in de module te gebruiken of op te halen.
Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.

## VOORBEELDEN

### Voor beeld 1: resultaten voor een bepaalde taak ophalen

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

Deze opdrachten gebruiken de **taak** parameter van `Receive-Job` om de resultaten van een bepaalde taak op te halen.

Met de eerste opdracht wordt een taak gestart `Start-Job` en wordt het taak object in de `$job` variabele opgeslagen.

Met de tweede opdracht wordt de `Receive-Job` cmdlet gebruikt om de resultaten van de taak op te halen.
De **taak** parameter wordt gebruikt om de taak op te geven.

### Voor beeld 2: de para meter Keep gebruiken

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

In dit voor beeld wordt een taak opgeslagen in de `$job` variabele en wordt de taak door sluizen naar de `Receive-Job` cmdlet. De `-Keep` para meter wordt ook gebruikt om toe te staan dat alle geaggregeerde stroom gegevens opnieuw worden opgehaald na de eerste weer gave.

### Voor beeld 3: resultaten van verschillende achtergrond taken ophalen

Wanneer u de para meter **AsJob** van gebruikt `Invoke-Command` om een taak te starten, wordt het taak object gemaakt op de lokale computer, zelfs als de taak wordt uitgevoerd op de externe computers.
Als gevolg hiervan kunt u lokale opdrachten gebruiken om de taak te beheren.

Wanneer u **AsJob** gebruikt, retourneert Power shell een taak object dat een onderliggende taak bevat voor elke taak die is gestart. In dit geval bevat het taak object drie onderliggende taken, één voor elke taak op elke externe computer.

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### Voor beeld 4: resultaten van achtergrond taken op meerdere externe computers ophalen

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

In dit voor beeld ziet u hoe de resultaten van achtergrond taken worden uitgevoerd op drie externe computers.
In tegens telling tot het vorige voor beeld, gebruikt `Invoke-Command` om de opdracht uit te voeren, `Start-Job` drie onafhankelijke taken op elk van de drie computers. Als gevolg hiervan heeft de opdracht drie taak objecten geretourneerd die drie taken vertegenwoordigen die lokaal worden uitgevoerd op drie verschillende computers.

> [!NOTE]
> In de laatste opdracht, omdat `$j` een lokale variabele is, gebruikt het script blok de aanpassings functie voor het **gebruik van** de scope om de variabele te identificeren `$j` . Zie [about_Remote_Variables](./About/about_Remote_Variables.md)voor meer informatie **over de aanpassing van het** bereik.

### Voor beeld 5: toegang tot onderliggende taken

Met de `-Keep` para meter wordt de status van de geaggregeerde streams van een taak behouden, zodat deze weer kan worden weer gegeven. Zonder deze para meter worden alle samengevoegde stroom gegevens gewist wanneer de taak wordt ontvangen. Zie [about_Job_Details](About/about_Job_Details.md#child-jobs) voor meer informatie.

> [!NOTE]
> De geaggregeerde streams bevatten de streams van alle onderliggende taken. U kunt nog steeds de afzonderlijke gegevens stromen bereiken via het taak object en onderliggende taak objecten.

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## PARAMETERS

### -AutoRemoveJob

Geeft aan dat deze cmdlet de taak verwijdert nadat de taak resultaten zijn geretourneerd.
Als de taak meer resultaten heeft, wordt de taak nog steeds verwijderd, maar `Receive-Job` wordt een bericht weer gegeven.

Deze para meter werkt alleen voor aangepaste taak typen.
Het is bedoeld voor exemplaren van taak typen die de taak of het type buiten de sessie opslaan, zoals exemplaren van geplande taken.

Deze para meter kan niet worden gebruikt zonder de para meter **wait** .

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u een matrix met namen van computers op.

Met deze para meter selecteert u onder de taak resultaten die zijn opgeslagen op de lokale computer.
Er worden geen gegevens opgehaald voor taken die worden uitgevoerd op externe computers.
Als u taak resultaten wilt ophalen die zijn opgeslagen op externe computers, gebruikt u de `Invoke-Command` cmdlet om een `Receive-Job` opdracht op afstand uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Force

Geeft aan dat deze cmdlet blijft wachten als taken de status **onderbroken** of **losgekoppeld** hebben. De **wait** -para meter van `Receive-Job` retourneert of beëindigt de wacht tijd wanneer taken een van de volgende statussen hebben:

- Voltooid
- Mislukt
- Gestopt
- Onderbroken
- Verbroken.

De para meter **Force** is alleen geldig als de **wait** -para meter ook in de opdracht wordt gebruikt.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee geeft u een matrix met Id's op.
Met deze cmdlet worden de resultaten van taken met de opgegeven Id's opgehaald.

De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.
Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie. U kunt een of meer Id's typen, gescheiden door komma's.
Als u de ID van een taak wilt zoeken, gebruikt u `Get-Job` .

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

Hiermee geeft u een matrix met exemplaar-Id's op.
Met deze cmdlet worden de resultaten van taken met de opgegeven exemplaar-Id's opgehaald.

Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.
Gebruik de cmdlet om de exemplaar-ID van een taak te vinden `Get-Job` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Taak

Hiermee geeft u de taak op waarvoor de resultaten worden opgehaald.

Voer een variabele in die de taak of een opdracht bevat die de taak ontvangt.
U kunt ook een taak object door sluizen naar `Receive-Job` .

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Keep

Geeft aan dat deze cmdlet de geaggregeerde stream-gegevens in het systeem opslaat, zelfs nadat u ze hebt ontvangen. Samengevoegde stroom gegevens worden standaard gewist na weer gave met `Receive-Job` .

Als u de sessie sluit of als u de taak met de cmdlet verwijdert, `Remove-Job` worden ook geaggregeerde stroom gegevens verwijderd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Locatie

Hiermee geeft u een matrix met locaties op.
Met deze cmdlet worden alleen de resultaten van taken op de opgegeven locaties opgehaald.

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een matrix met beschrijvende namen op.
Met deze cmdlet worden de resultaten opgehaald van taken met de opgegeven namen.
Joker tekens worden ondersteund.

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

### -Niet-terugkerend

Geeft aan dat deze cmdlet alleen resultaten ophaalt van de opgegeven taak.
`Receive-Job`De resultaten van alle onderliggende taken van de opgegeven taak worden standaard ook opgehaald.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessie

Hiermee geeft u een matrix met sessies op.
Met deze cmdlet worden de resultaten opgehaald van taken die zijn uitgevoerd in de opgegeven Power shell-sessie (**PSSession**).
Voer een variabele in die de **PSSession** bevat of een opdracht die de **PSSession**, zoals een opdracht, ophalen `Get-PSSession` .

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Wachten

Geeft aan dat deze cmdlet de opdracht prompt onderdrukt totdat alle taak resultaten zijn ontvangen.
Standaard `Receive-Job` retourneert onmiddellijk de beschik bare resultaten.

Standaard wacht de **wait** -para meter totdat de taak een van de volgende statussen heeft:

- Voltooid
- Mislukt
- Gestopt
- Onderbroken
- Verbroken.

Als u de **wait** -para meter wilt blijven wachten als de taak status onderbroken of losgekoppeld is, gebruikt u de para meter **Force** in combi natie met de para meter **wait** .

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

### -WriteEvents

Geeft aan dat deze cmdlet wijzigingen in de taak status rapporteert terwijl de taak kan worden voltooid.

Deze para meter is alleen geldig als de **wait** -para meter wordt gebruikt in de opdracht en de **Keep** -para meter wordt wegge laten.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WriteJobInResults

Geeft aan dat deze cmdlet het taak object retourneert, gevolgd door de resultaten.

Deze para meter is alleen geldig als de **wait** -para meter wordt gebruikt in de opdracht en de **Keep** -para meter wordt wegge laten.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](./About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. Management. Automation. job

U kunt taak objecten door sluizen naar deze cmdlet.

## UITVOER

### PSObject

Met deze cmdlet worden de resultaten van de opdrachten in de taak geretourneerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-job](Get-Job.md)

[Invoke-opdracht](Invoke-Command.md)

[Verwijderen-taak](Remove-Job.md)

[Begin taak](Start-Job.md)

[Stoppen-taak](Stop-Job.md)

[Wait-Job](Wait-Job.md)

