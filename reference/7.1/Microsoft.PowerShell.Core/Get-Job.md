---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 8a92e07746e86d4b0b84049f1f479a82c85e5e6f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251361"
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

### CommandParameterSet

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### FilterParameterSet

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **Get-job** haalt objecten op die de achtergrond taken vertegenwoordigen die in de huidige sessie zijn gestart. U kunt **Get-job** gebruiken om taken op te halen die zijn gestart met behulp van de cmdlet Start-Job, of door gebruik te maken van de para meter *AsJob* van een cmdlet.

Zonder para meters haalt een **Get-job-** opdracht alle taken in de huidige sessie op.
U kunt de para meters van **Get-job** gebruiken om bepaalde taken op te halen.

Het taak object dat **Get-job** retourneert, bevat nuttige informatie over de taak, maar bevat geen taak resultaten. Gebruik de cmdlet Receive-Job om de resultaten op te halen.

Een Power shell-achtergrond taak is een opdracht die op de achtergrond wordt uitgevoerd zonder interactie met de huidige sessie. Normaal gesp roken gebruikt u een achtergrond taak om een complexe opdracht uit te voeren die veel tijd in beslag neemt. Zie about_Jobs voor meer informatie over achtergrond taken in Power shell.

Vanaf Windows Power Shell 3,0 worden met de cmdlet **Get-job** ook aangepaste taak typen opgehaald, zoals werk stroom taken en exemplaren van geplande taken. Gebruik de eigenschap **PSJobTypeName** van de taak om het taak type van een taak te vinden.

Als u **Get-job** wilt inschakelen om een aangepast taak type op te halen, importeert u de module die het aangepaste taak type ondersteunt in de sessie voordat u een opdracht **Get-job** uitvoert, met behulp van de Import-Module cmdlet of door een cmdlet in de module te gebruiken of op te halen. Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.

## VOORBEELDEN

### Voor beeld 1: alle achtergrond taken ophalen gestart in de huidige sessie

```powershell
Get-Job
```

Met deze opdracht worden alle achtergrond taken opgehaald die in de huidige sessie zijn gestart.
Het bevat geen taken die zijn gemaakt in andere sessies, zelfs als de taken worden uitgevoerd op de lokale computer.

### Voor beeld 2: een taak stoppen met een exemplaar-ID

Deze opdrachten laten zien hoe u de exemplaar-ID van een taak ophaalt en vervolgens kunt gebruiken om een taak te stoppen.
In tegens telling tot de naam van een taak, die niet uniek is, is de exemplaar-ID uniek.

```powershell
$j = Get-Job -Name Job1
$ID = $j.InstanceID
$ID
```

```Output
Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55
```

```powershell
Stop-Job -InstanceId $ID
```

De eerste opdracht maakt gebruik van de cmdlet **Get-job** om een taak op te halen. De para meter *name* wordt gebruikt om de taak te identificeren. De opdracht slaat het taak object op dat **Get-job** retourneert in de variabele $j. In dit voor beeld is er slechts één taak met de opgegeven naam.

Met de tweede opdracht wordt de eigenschap **InstanceId** van het object in de variabele $j opgehaald en opgeslagen in de $id variabele.

Met de derde opdracht wordt de waarde van de variabele $ID weer gegeven.

De vierde opdracht maakt gebruik van Stop-Job cmdlet om de taak te stoppen. De para meter *InstanceId* wordt gebruikt om de taak en $id variabele te identificeren die de exemplaar-id van de taak vertegenwoordigen.

### Voor beeld 3: taken ophalen die een specifieke opdracht bevatten

```powershell
Get-Job -Command "*get-process*"
```

Met deze opdracht worden de taken op het systeem opgehaald die een Get-Process opdracht bevatten. De opdracht gebruikt de *opdracht* parameter van **Get-job** om de opgehaalde taken te beperken. De opdracht gebruikt joker tekens (*) om taken op te halen die een opdracht **Get-process bevatten,** overal in de opdracht reeks.

### Voor beeld 4: taken met een bepaalde opdracht ophalen met behulp van de pijp lijn

```powershell
"*get-process*" | Get-Job
```

Net als de opdracht in het vorige voor beeld, haalt deze opdracht de taken op het systeem op die een opdracht **Get-process** bevatten. De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van een teken reeks tussen aanhalings tekens en de cmdlet **Get-job** . Dit is het equivalent van de vorige opdracht.

### Voor beeld 5: taken ophalen die niet zijn gestart

```powershell
Get-Job -State NotStarted
```

Met deze opdracht worden alleen de taken opgehaald die zijn gemaakt, maar die nog niet zijn gestart.
Dit omvat taken die in de toekomst zijn gepland en die nog niet zijn gepland.

### Voor beeld 6: taken ophalen waaraan geen naam is toegewezen

```powershell
Get-Job -Name Job*
```

Met deze opdracht worden alle taken opgehaald die met taak namen beginnen.
Omdat taak \<number\> de standaard naam voor een taak is, worden met deze opdracht alle taken opgehaald die geen expliciet toegewezen naam hebben.

### Voor beeld 7: een taak object gebruiken om de taak in een opdracht weer te geven

In dit voor beeld ziet u hoe u **Get-job** kunt gebruiken om een taak object op te halen. vervolgens ziet u hoe u het taak object kunt gebruiken om de taak in een opdracht weer te geven.

```powershell
Start-Job -ScriptBlock {Get-Process} -Name MyJob
$j = Get-Job -Name MyJob
$j
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process
```

```powershell
Receive-Job -Job $j
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

De eerste opdracht maakt gebruik van de cmdlet **Start-job** om een achtergrond taak te starten die een **Get-process-** opdracht uitvoert op de lokale computer. De opdracht gebruikt de para meter *name* van **Start-job** om een beschrijvende naam toe te wijzen aan de taak.

De tweede opdracht maakt gebruik van Get-Job om de taak op te halen. De para meter *name* van **Get-job** wordt gebruikt om de taak te identificeren. De opdracht slaat het resulterende taak object op in de variabele $j.

Met de derde opdracht wordt de waarde van het taak object weer gegeven in de variabele $j. De waarde van de **status** eigenschap geeft aan dat de taak is voltooid. De waarde van de eigenschap **HasMoreData** geeft aan dat er resultaten beschikbaar zijn van de taak die nog niet zijn opgehaald.

De vierde opdracht maakt gebruik van de cmdlet **Receive-job** om de resultaten van de taak op te halen. Het taak object in de variabele $j wordt gebruikt om de taak te vertegenwoordigen. U kunt ook een pijplijn operator gebruiken om een taak object te verzenden naar **Receive-job**.

### Voor beeld 8: alle taken ophalen, inclusief taken die met een andere methode zijn gestart

In dit voor beeld wordt gedemonstreerd dat de cmdlet **Get-job** alle taken kan ophalen die in de huidige sessie zijn gestart, zelfs als deze zijn gestart door verschillende methoden te gebruiken.

```powershell
Start-Job -ScriptBlock {Get-EventLog System}
Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Get-Job
```

```Output
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System
```

```powershell
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
```

```Output
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

De eerste opdracht maakt gebruik van de cmdlet **Start-job** om een taak op de lokale computer te starten.

De tweede opdracht maakt gebruik van de para meter *AsJob* van de cmdlet **invoke-opdracht** om een taak op de computer S1 te starten. Hoewel de opdrachten in de taak worden uitgevoerd op de externe computer, wordt het taak object gemaakt op de lokale computer, dus u kunt lokale opdrachten gebruiken om de taak te beheren.

De derde opdracht maakt gebruik van de cmdlet **invoke-opdracht** om een **Start-taak** opdracht uit te voeren op de S2-computer. Met deze methode wordt het taak object op de externe computer gemaakt, zodat u externe opdrachten gebruikt om de taak te beheren.

De vierde opdracht gebruikt **Get-job** om de taken op de lokale computer op te halen. De eigenschap **PSJobTypeName** van taken, geïntroduceerd in Windows power Shell 3,0, laat zien dat de lokale taak is gestart met de cmdlet **Start-job** een achtergrond taak is en de taak is gestart in een externe sessie met behulp van de cmdlet **invoke-opdracht** is een externe taak.

De vijfde opdracht gebruikt u **invoke-opdracht** om een opdracht **Get-job** uit te voeren op de S2-computer. De voorbeeld uitvoer toont de resultaten van de Get-Job opdracht. Op de computer S2 lijkt de taak een lokale taak te zijn. De computer naam is localhost en het taak type is een achtergrond taak.

Zie about_Remote_Jobs voor meer informatie over het uitvoeren van achtergrond taken op externe computers.

### Voor beeld 9: een mislukte taak onderzoeken

```powershell
Start-Job -ScriptBlock {Get-Process}
```

```Output
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process
```

```powershell
(Get-Job).JobStateInfo | Format-List -Property *
```

```Output
State  : Failed
Reason :
```

```powershell
Get-Job | Format-List -Property *
```

```Output
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
```

```powershell
(Get-Job -Name job2).JobStateInfo.Reason
```

```Output
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.

For information about requirements for remoting in PowerShell, see about_Remote_Requirements. For
troubleshooting tips, see about_Remote_Troubleshooting.
```

Met deze opdracht wordt uitgelegd hoe u het taak object gebruikt dat **Get-job** retourneert om te onderzoeken waarom een taak is mislukt.
Ook wordt uitgelegd hoe u de onderliggende taken van elke taak kunt ophalen.

De eerste opdracht maakt gebruik van de cmdlet **Start-job** om een taak op de lokale computer te starten. Het taak object dat **Start taak retourneert,** geeft aan dat de taak is mislukt. De waarde van de **status** eigenschap is mislukt.

De tweede opdracht maakt gebruik van de cmdlet **Get-job** om de taak op te halen. De opdracht gebruikt de punt methode om de waarde van de eigenschap **JobStateInfo** van het object op te halen. Er wordt een pijplijn operator gebruikt voor het verzenden van het object in de eigenschap **JobStateInfo** naar de cmdlet Format-List, waarmee alle eigenschappen van het object (*) in een lijst worden opgemaakt. Het resultaat van de **indeling-lijst** opdracht laat zien dat de waarde van de eigenschap **reason** van de taak leeg is.

De derde opdracht onderzoekt meer. Er wordt een opdracht **Get-job** gebruikt om de taak op te halen en vervolgens een pijplijn operator gebruikt om het hele taak object te verzenden naar de **indelings lijst-** cmdlet, waarin alle eigenschappen van de taak in een lijst worden weer gegeven. De weer gave van alle eigenschappen in het taak object toont aan dat de taak een onderliggende taak bevat met de naam Job2.

De vierde opdracht gebruikt **Get-job** om het taak object op te halen dat de onderliggende taak Job2 vertegenwoordigt. Dit is de taak waarin de opdracht daad werkelijk wordt uitgevoerd. De punt methode wordt gebruikt om de eigenschap **reason** van de eigenschap **JobStateInfo** op te halen. Het resultaat toont aan dat de taak is mislukt vanwege een fout bij de toegang geweigerd. In dit geval is de gebruiker verg eten de optie als administrator uitvoeren te gebruiken bij het starten van Power shell. omdat achtergrond taken gebruikmaken van de externe functies van Power shell, moet de computer zijn geconfigureerd voor externe toegang om een taak uit te voeren, zelfs wanneer de taak wordt uitgevoerd op de lokale computer.

### Voor beeld 10: gefilterde resultaten ophalen

In dit voor beeld ziet u hoe u de *filter* parameter gebruikt om een werk stroom taak op te halen.
De *filter* parameter, die is geïntroduceerd in Windows power Shell 3,0, is alleen geldig voor aangepaste taak typen, zoals werk stroom taken en geplande taken.

```powershell
Workflow WFProcess {Get-Process}
WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
Get-Job -Filter @{MyCustomId = 92107}
```

```Output
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

Met de eerste opdracht wordt het sleutel woord **workflow** gebruikt om de WFProcess-werk stroom te maken.

De tweede opdracht maakt gebruik van de para meter *AsJob* van de WFProcess-werk stroom om de werk stroom als een achtergrond taak uit te voeren. De para meter *JobName* van de werk stroom wordt gebruikt om een naam voor de taak op te geven en de para meter *PSPrivateMetadata* van de werk stroom om een aangepaste ID op te geven.

De derde opdracht gebruikt de *filter* parameter van **Get-job** om de taak op te halen op basis van een aangepaste id die is opgegeven in de para meter *PSPrivateMetadata* .

### Voor beeld 11: informatie over onderliggende taken ophalen

In dit voor beeld ziet u het effect van het gebruik van de para meters *IncludeChildJob* en *ChildJobState* van de cmdlet **Get-job** .

```powershell
Get-Job
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
Get-Job -IncludeChildJob
```

```Output
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
```

```powershell
Get-Job -Name Job4 -ChildJobState Failed
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
(Get-Job -Name Job5).JobStateInfo.Reason
```

```Output
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

Met de eerste opdracht worden de taken in de huidige sessie opgehaald. De uitvoer bevat een achtergrond taak, een externe taak en verschillende exemplaren van een geplande taak. De externe taak Job4 lijkt te zijn mislukt.

De tweede opdracht maakt gebruik van de para meter *IncludeChildJob* van **Get-job**. Met de uitvoer worden de onderliggende taken van alle taken met onderliggende taken toegevoegd. In dit geval toont de gereviseerde uitvoer alleen dat de onderliggende Job5-taak van Job4 is mislukt.

De derde opdracht gebruikt de para meter *ChildJobState* met de waarde mislukt. de uitvoer bevat alle bovenliggende taken en alleen de onderliggende taken die zijn mislukt.

De vierde opdracht maakt gebruik van de eigenschap **JobStateInfo** van Jobs en de eigenschap **reason** om te ontdekken waarom Job5 is mislukt.

## PARAMETERS

### -Na

Hiermee worden voltooide taken opgehaald die zijn beëindigd na de opgegeven datum en tijd. Voer een **DateTime** -object in, bijvoorbeeld een waarde die wordt geretourneerd door de Get-Date cmdlet of een teken reeks die kan worden geconverteerd naar een **DateTime** -object, zoals `Dec 1, 2012 2:00 AM` of `11/06` .

Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken, die een eigenschap **EndTime** hebben. Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** . Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
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

Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken, die een eigenschap **EndTime** hebben. Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** . Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
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
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
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

Wanneer u de cmdlet **Receive-job** gebruikt, wordt deze verwijderd uit de in-Memory, sessie-specifieke opslag de geretourneerde resultaten. Wanneer het alle resultaten van de taak in de huidige sessie heeft geretourneerd, wordt de waarde van de eigenschap **HasMoreData** van de taak ingesteld op $false) om aan te geven dat deze geen resultaten meer heeft voor de taak in de huidige sessie. Gebruik de *para* meter van **Receive-job** om te voor komen dat de **functie receive** results verwijdert en de waarde van de eigenschap **HasMoreData** wijzigt. Typ `Get-Help Receive-Job` voor meer informatie.

De eigenschap **HasMoreData** is specifiek voor de huidige sessie. Als de resultaten voor een aangepast taak type buiten de sessie worden opgeslagen, zoals het type geplande taak, waarmee taak resultaten op schijf worden opgeslagen, kunt u de cmdlet **Receive-job** in een andere sessie gebruiken om de taak resultaten opnieuw op te halen, zelfs als de waarde van **HasMoreData** is $False. Zie de Help-onderwerpen voor het aangepaste taak type voor meer informatie.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
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
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
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
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
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

[Begin taak](Start-Job.md)

[Stoppen-taak](Stop-Job.md)

[Wait-Job](Wait-Job.md)

