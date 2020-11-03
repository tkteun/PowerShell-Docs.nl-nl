---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 0b9c76ca1e26adaa244473366c2eabdaaa28452c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249959"
---
# Get-Job

## SAMENVATTING
Hiermee worden Power shell-achtergrond taken opgehaald die in de huidige sessie worden uitgevoerd.

## SYNTAXIS

### SessionIdParameterSet (standaard)

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### CommandParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### NameParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### StateParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### FilterParameterSet

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **Get-job** haalt objecten op die de achtergrond taken vertegenwoordigen die in de huidige sessie zijn gestart.
U kunt **Get-job** gebruiken om taken op te halen die zijn gestart met behulp van de cmdlet Start-Job, of door gebruik te maken van de para meter *AsJob* van een cmdlet.

Zonder para meters haalt een **Get-job-** opdracht alle taken in de huidige sessie op.
U kunt de para meters van **Get-job** gebruiken om bepaalde taken op te halen.

Het taak object dat **Get-job** retourneert, bevat nuttige informatie over de taak, maar bevat geen taak resultaten.
Gebruik de cmdlet Receive-Job om de resultaten op te halen.

Een Windows Power shell-achtergrond taak is een opdracht die op de achtergrond wordt uitgevoerd zonder interactie met de huidige sessie.
Normaal gesp roken gebruikt u een achtergrond taak om een complexe opdracht uit te voeren die veel tijd in beslag neemt.
Zie about_Jobs voor meer informatie over achtergrond taken in Windows Power shell.

Vanaf Windows Power Shell 3,0 worden met de cmdlet **Get-job** ook aangepaste taak typen opgehaald, zoals werk stroom taken en exemplaren van geplande taken.
Gebruik de eigenschap **PSJobTypeName** van de taak om het taak type van een taak te vinden.

Als u **Get-job** wilt inschakelen om een aangepast taak type op te halen, importeert u de module die het aangepaste taak type ondersteunt in de sessie voordat u een opdracht **Get-job** uitvoert, met behulp van de Import-Module cmdlet of door een cmdlet in de module te gebruiken of op te halen.
Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.

## VOORBEELDEN

### Voor beeld 1: alle achtergrond taken ophalen gestart in de huidige sessie

```
PS C:\> Get-Job
```

Met deze opdracht worden alle achtergrond taken opgehaald die in de huidige sessie zijn gestart.
Het bevat geen taken die zijn gemaakt in andere sessies, zelfs als de taken worden uitgevoerd op de lokale computer.

### Voor beeld 2: een taak stoppen met een exemplaar-ID

```
The first command uses the **Get-Job** cmdlet to get a job. It uses the *Name* parameter to identify the job. The command stores the job object that **Get-Job** returns in the $j variable. In this example, there is only one job with the specified name.
PS C:\> $j = Get-Job -Name Job1

The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.
PS C:\> $ID = $j.InstanceID

The third command displays the value of the $ID variable.
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

The fourth command uses Stop-Job cmdlet to stop the job. It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.
PS C:\> Stop-Job -InstanceId $ID
```

Deze opdrachten laten zien hoe u de exemplaar-ID van een taak ophaalt en vervolgens kunt gebruiken om een taak te stoppen.
In tegens telling tot de naam van een taak, die niet uniek is, is de exemplaar-ID uniek.

### Voor beeld 3: taken ophalen die een specifieke opdracht bevatten

```
PS C:\> Get-Job -Command "*get-process*"
```

Met deze opdracht worden de taken op het systeem opgehaald die een Get-Process opdracht bevatten.
De opdracht gebruikt de *opdracht* parameter van **Get-job** om de opgehaalde taken te beperken.
De opdracht gebruikt joker tekens (*) om taken op te halen die een opdracht **Get-process bevatten,** overal in de opdracht reeks.

### Voor beeld 4: taken met een bepaalde opdracht ophalen met behulp van de pijp lijn

```
PS C:\> "*get-process*" | Get-Job
```

Net als de opdracht in het vorige voor beeld, haalt deze opdracht de taken op het systeem op die een opdracht **Get-process** bevatten.
De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van een teken reeks tussen aanhalings tekens en de cmdlet **Get-job** .
Dit is het equivalent van de vorige opdracht.

### Voor beeld 5: taken ophalen die niet zijn gestart

```
PS C:\> Get-Job -State NotStarted
```

Met deze opdracht worden alleen de taken opgehaald die zijn gemaakt, maar die nog niet zijn gestart.
Dit omvat taken die in de toekomst zijn gepland en die nog niet zijn gepland.

### Voor beeld 6: taken ophalen waaraan geen naam is toegewezen

```
PS C:\> Get-Job -Name Job*
```

Met deze opdracht worden alle taken opgehaald die met taak namen beginnen.
Omdat taak \<number\> de standaard naam voor een taak is, worden met deze opdracht alle taken opgehaald die geen expliciet toegewezen naam hebben.

### Voor beeld 7: een taak object gebruiken om de taak in een opdracht weer te geven

```
The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer. The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob

The second command uses Get-Job to get the job. It uses the *Name* parameter of **Get-Job** to identify the job. The command saves the resulting job object in the $j variable.
PS C:\> $j = Get-Job -Name MyJob

The third command displays the value of the job object in the $j variable. The value of the **State** property shows that the job is completed. The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

The fourth command uses the **Receive-Job** cmdlet to get the results of the job. It uses the job object in the $j variable to represent the job. You can also use a pipeline operator to send a job object to **Receive-Job**.
PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

In dit voor beeld ziet u hoe u **Get-job** kunt gebruiken om een taak object op te halen. vervolgens ziet u hoe u het taak object kunt gebruiken om de taak in een opdracht weer te geven.

### Voor beeld 8: alle taken ophalen, inclusief taken die met een andere methode zijn gestart

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer.
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}

The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer. Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob

The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer. By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}

The fourth command uses **Get-Job** to get the jobs stored on the local computer. The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command. On the S2 computer, the job appears to be a local job. The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see about_Remote_Jobs.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

In dit voor beeld wordt gedemonstreerd dat de cmdlet **Get-job** alle taken kan ophalen die in de huidige sessie zijn gestart, zelfs als deze zijn gestart door verschillende methoden te gebruiken.

### Voor beeld 9: een mislukte taak onderzoeken

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer. The job object that **Start-Job** returns shows that the job failed. The value of the **State** property is Failed.
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

The second command uses the **Get-Job** cmdlet to get the job. The command uses the dot method to get the value of the **JobStateInfo** property of the object. It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.
PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

The third command investigates more. It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.
PS C:\> Get-Job | Format-List -Property *
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :

The fourth command uses **Get-Job** to get the job object that represents the Job2 child job. This is the job in which the command actually ran. It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error. In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see about_Remote_Requirements. For troubleshooting tips, see about_Remote_Troubleshooting.
PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.
```

Met deze opdracht wordt uitgelegd hoe u het taak object gebruikt dat **Get-job** retourneert om te onderzoeken waarom een taak is mislukt.
Ook wordt uitgelegd hoe u de onderliggende taken van elke taak kunt ophalen.

### Voor beeld 10: gefilterde resultaten ophalen

```
The first command uses the **Workflow** keyword to create the WFProcess workflow.
PS C:\> Workflow WFProcess {Get-Process}

The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job. It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}

The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

In dit voor beeld ziet u hoe u de *filter* parameter gebruikt om een werk stroom taak op te halen.
De *filter* parameter, die is geïntroduceerd in Windows power Shell 3,0, is alleen geldig voor aangepaste taak typen, zoals werk stroom taken en geplande taken.

### Voor beeld 11: informatie over onderliggende taken ophalen

```
The first command gets the jobs in the current session. The output includes a background job, a remote job and several instances of a scheduled job. The remote job, Job4, appears to have failed.
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The second command uses the *IncludeChildJob* parameter of **Get-Job**. The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.
PS C:\> Get-Job -IncludeChildJob
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.
PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.
PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

In dit voor beeld ziet u het effect van het gebruik van de para meters *IncludeChildJob* en *ChildJobState* van de cmdlet **Get-job** .

## PARAMETERS

### -Na

Hiermee worden voltooide taken opgehaald die zijn beëindigd na de opgegeven datum en tijd.
Voer een **DateTime** -object in, bijvoorbeeld een waarde die wordt geretourneerd door de Get-Date cmdlet of een teken reeks die kan worden geconverteerd naar een **DateTime** -object, zoals `Dec 1, 2012 2:00 AM` of `11/06` .

Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken, die een eigenschap **EndTime** hebben.
Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .
Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Vóór

Hiermee worden voltooide taken opgehaald die voor de opgegeven datum en tijd zijn beëindigd.
Voer een **DateTime** -object in.

Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken, die een eigenschap **EndTime** hebben.
Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .
Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ChildJobState

Hiermee worden alleen de onderliggende taken met de opgegeven status opgehaald.
De aanvaardbare waarden voor deze parameter zijn:

- NotStarted
- Wordt uitgevoerd
- Voltooid
- Mislukt
- Gestopt
- Geblokkeerd
- Onderbroken
- Ontkoppeld
- Onderbreken
- Stoppen

**Get-job** krijgt standaard geen onderliggende taken.
Met behulp van de *IncludeChildJob* para meter **Get-job** worden alle onderliggende taken opgehaald.
Als u de para meter *ChildJobState* gebruikt, heeft de para meter *IncludeChildJob* geen effect.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Opdracht

Geeft een matrix van opdrachten aan als teken reeksen.
Met deze cmdlet worden de taken opgehaald die de opgegeven opdrachten bevatten.
De standaard waarde is alle taken.
U kunt joker tekens gebruiken om een opdracht patroon op te geven.

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Filter

Hiermee geeft u een hash-tabel met voor waarden op.
Met deze cmdlet worden taken opgehaald die voldoen aan alle voor waarden.
Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.

Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken.
Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .
Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

### -HasMoreData

Hiermee wordt aangegeven of met deze cmdlet alleen taken worden opgehaald die de opgegeven waarde voor de eigenschap **HasMoreData** hebben.
De eigenschap **HasMoreData** geeft aan of alle taak resultaten zijn ontvangen in de huidige sessie.
Als u taken met meer resultaten wilt ophalen, geeft u de waarde $True op.
Als u taken wilt ophalen die niet meer resultaten hebben, geeft u de waarde $False op.

Gebruik de cmdlet Receive-Job om de resultaten van een taak op te halen.

Wanneer u de cmdlet **Receive-job** gebruikt, wordt deze verwijderd uit de in-Memory, sessie-specifieke opslag de geretourneerde resultaten.
Wanneer het alle resultaten van de taak in de huidige sessie heeft geretourneerd, wordt de waarde van de eigenschap **HasMoreData** van de taak ingesteld op $false) om aan te geven dat deze geen resultaten meer heeft voor de taak in de huidige sessie.
Gebruik de *para* meter van **Receive-job** om te voor komen dat de **functie receive** results verwijdert en de waarde van de eigenschap **HasMoreData** wijzigt.
Typ `Get-Help Receive-Job` voor meer informatie.

De eigenschap **HasMoreData** is specifiek voor de huidige sessie.
Als de resultaten voor een aangepast taak type buiten de sessie worden opgeslagen, zoals het type geplande taak, waarmee taak resultaten op schijf worden opgeslagen, kunt u de cmdlet **Receive-job** in een andere sessie gebruiken om de taak resultaten opnieuw op te halen, zelfs als de waarde van **HasMoreData** is $False.
Zie de Help-onderwerpen voor het aangepaste taak type voor meer informatie.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee wordt een matrix met Id's opgegeven van taken die met deze cmdlet worden opgehaald.

De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.
Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.
U kunt een of meer Id's typen, gescheiden door komma's.
Als u de ID van een taak wilt zoeken, typt u `Get-Job` zonder para meters.

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IncludeChildJob

Geeft aan dat deze cmdlet onderliggende taken retourneert, naast de bovenliggende taken.

Deze para meter is vooral nuttig voor het onderzoeken van werk stroom taken, waarvoor **Get-job** een bovenliggende container taak en taak fouten retourneert, omdat de reden voor de fout wordt opgeslagen in een eigenschap van de onderliggende taak.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u een matrix met exemplaar-Id's van taken op die met deze cmdlet worden opgehaald.
De standaard waarde is alle taken.

Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.
Gebruik **Get-job** om de exemplaar-id van een taak te vinden.

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

### -Name

Hiermee geeft u een matrix met beschrijvende namen van taken op die met deze cmdlet worden opgehaald.
Voer een taak naam in of gebruik joker tekens om een job name-patroon in te voeren.
**Get-job** haalt standaard alle taken in de huidige sessie op.

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

### -Nieuwste

Hiermee geeft u een aantal taken op dat moet worden opgehaald.
Met deze cmdlet worden de taken opgehaald die het meest recent zijn beëindigd.

De *nieuwste* para meter sorteert of retourneert de nieuwste taken niet in de volg orde van de eind tijd.
Als u de uitvoer wilt sorteren, gebruikt u de cmdlet Sort-Object.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status

Hiermee geeft u een taak status op.
Met deze cmdlet worden alleen taken in de opgegeven status opgehaald.
De aanvaardbare waarden voor deze parameter zijn:

- NotStarted
- Wordt uitgevoerd
- Voltooid
- Mislukt
- Gestopt
- Geblokkeerd
- Onderbroken
- Ontkoppeld
- Onderbreken
- Stoppen

**Get-job** haalt standaard alle taken in de huidige sessie op.

Zie [JobState Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.jobstate) in de MSDN-bibliotheek voor meer informatie over de status van de taak.

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. RemotingJob

Deze cmdlet retourneert objecten die de taken in de sessie vertegenwoordigen.

## OPMERKINGEN

* De eigenschap **PSJobTypeName** van taken geeft het taak type van de taak aan. De waarde van de eigenschap wordt bepaald door de auteur van het taak type. De volgende lijst bevat algemene taak typen.

  - **BackgroundJob**.
De lokale taak is gestart met **het starten** van de taak.

  - **RemoteJob**.
De taak is gestart in een **PSSession** met de para meter *AsJob* van de cmdlet Invoke-Command.

  - **PSWorkflowJob**.
De taak is gestart met de gemeen schappelijke para meter *AsJob* van werk stromen.

## GERELATEERDE KOPPELINGEN

[Invoke-opdracht](Invoke-Command.md)

[Receive-job](Receive-Job.md)

[Verwijderen-taak](Remove-Job.md)

[Resume-job](Resume-Job.md)

[Begin taak](Start-Job.md)

[Stoppen-taak](Stop-Job.md)

[Onderbreken-taak](Suspend-Job.md)

[Wait-Job](Wait-Job.md)

[about_Jobs](About/about_Jobs.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)

[about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md)
