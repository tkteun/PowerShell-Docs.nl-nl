---
description: Bevat informatie over achtergrond taken op lokale en externe computers.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: 0d85cd242c8e79281fa8be153b0e140660f16c1a
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/17/2020
ms.locfileid: "93253088"
---
# <a name="about-job-details"></a>Over taak Details

## <a name="short-description"></a>Korte beschrijving
Bevat informatie over achtergrond taken op lokale en externe computers.

## <a name="detailed-description"></a>Gedetailleerde beschrijving

In dit onderwerp wordt het concept van een achtergrond taak uitgelegd en vindt u technische informatie over de werking van achtergrond taken in Power shell.

Dit onderwerp is een aanvulling op de onderwerpen [about_Jobs](about_Jobs.md), [about_Thread_Jobs](about_Thread_Jobs.md)en [about_Remote_Jobs](about_Remote_Jobs.md) .

### <a name="about-background-jobs"></a>Over achtergrond taken

Met een achtergrond taak wordt een opdracht of expressie asynchroon uitgevoerd. Er kan een cmdlet, een functie, een script of een andere op opdrachten gebaseerde taak worden uitgevoerd. Het is ontworpen om opdrachten uit te voeren die lange tijd duren, maar u kunt deze gebruiken om elke opdracht op de achtergrond uit te voeren.

Wanneer een synchrone opdracht wordt uitgevoerd, wordt de Power shell-opdracht prompt onderdrukt totdat de opdracht is voltooid. De Power shell-prompt wordt niet onderdrukt door een achtergrond taak. Een opdracht voor het starten van een achtergrond taak retourneert een taak object.
De prompt wordt onmiddellijk geretourneerd, zodat u met andere taken kunt werken terwijl de achtergrond taak wordt uitgevoerd.

Wanneer u echter een achtergrond taak start, worden de resultaten niet meteen opgehaald, zelfs niet als de taak zeer snel wordt uitgevoerd. Het taak object dat wordt geretourneerd, bevat nuttige informatie over de taak, maar bevat geen taak resultaten. U moet een afzonderlijke opdracht uitvoeren om de taak resultaten te krijgen. U kunt ook opdrachten uitvoeren om de taak te stoppen, te wachten tot de taak is voltooid en de taak te verwijderen.

Om de timing van een achtergrond taak onafhankelijk van andere opdrachten te maken, wordt elke achtergrond taak uitgevoerd in een eigen Power shell-sessie. Dit kan echter een tijdelijke verbinding zijn die alleen wordt gemaakt om de taak uit te voeren en vervolgens wordt vernietigd, of het kan een permanente **PSSession** zijn die u kunt gebruiken om verschillende gerelateerde taken of opdrachten uit te voeren.

### <a name="using-the-job-cmdlets"></a>De taak-cmdlets gebruiken

Gebruik een `Start-Job` opdracht voor het starten van een achtergrond taak op een lokale computer.
`Start-Job` retourneert een taak object. U kunt ook objecten ophalen die de taken vertegenwoordigen die zijn gestart op de lokale computer met behulp van de- `Get-Job` cmdlet.

Gebruik een opdracht om de taak resultaten te verkrijgen `Receive-Job` . Als de taak niet is voltooid, `Receive-Job` retourneert gedeeltelijke resultaten. U kunt de cmdlet ook gebruiken `Wait-Job` om de opdracht prompt te onderdrukken totdat een of alle taken die in de sessie zijn gestart, zijn voltooid.

Als u een achtergrond taak wilt stoppen, gebruikt u de `Stop-Job` cmdlet. Als u een taak wilt verwijderen, gebruikt u de `Remove-Job` cmdlet.

Zie voor meer informatie over de werking van de cmdlets het Help-onderwerp voor elke cmdlet en Zie [about_Jobs](about_Jobs.md).

### <a name="starting-background-jobs-on-remote-computers"></a>Achtergrond taken op externe computers starten

U kunt achtergrond taken maken en beheren op een lokale of externe computer. Als u een achtergrond taak extern wilt uitvoeren, gebruikt u de para meter **AsJob** van een cmdlet zoals `Invoke-Command` of gebruikt `Invoke-Command` u de cmdlet om een `Start-Job` opdracht op afstand uit te voeren. U kunt ook een achtergrond taak in een interactieve sessie starten.

Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie over externe achtergrond taken.

### <a name="child-jobs"></a>Onderliggende taken

Elke achtergrond taak bestaat uit een bovenliggende taak en een of meer onderliggende taken. In taken die zijn gestart met `Start-Job` of de **AsJob** -para meter van `Invoke-Command` is de bovenliggende taak een Executive. Er worden geen opdrachten uitgevoerd en er worden geen resultaten geretourneerd. De opdrachten worden feitelijk uitgevoerd door de onderliggende taken. Taken die zijn gestart met andere cmdlets werken mogelijk anders.

De onderliggende taken worden opgeslagen in de eigenschap **ChildJobs** van het bovenliggende taak object. De eigenschap **ChildJobs** kan een of meer onderliggende taak objecten bevatten.
De onderliggende taak objecten hebben een **naam** , **id** en **InstanceId** die verschillen van de bovenliggende taak, zodat u de bovenliggende en onderliggende taken afzonderlijk of als een eenheid kunt beheren.

Als u de bovenliggende en onderliggende taken van een taak wilt ophalen, gebruikt u de para meter **IncludeChildJobs** van de `Get-Job` cmdlet. De para meter **IncludeChildJob** is geïntroduceerd in Windows power Shell 3,0.

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

Als u de bovenliggende taak en alleen de onderliggende taken met een bepaalde **status** waarde wilt ophalen, gebruikt u de para meter **ChildJobState** van de `Get-Job` cmdlet. De para meter **ChildJobState** is geïntroduceerd in Windows power Shell 3,0.

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

Als u de onderliggende taken van een taak op alle versies van Power shell wilt ophalen, gebruikt u de eigenschap **ChildJob** van de bovenliggende taak.

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

U kunt ook een `Get-Job` opdracht gebruiken in de onderliggende taak, zoals wordt weer gegeven in de volgende opdracht:

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

De configuratie van de onderliggende taak is afhankelijk van de opdracht die u gebruikt om de taak te starten.

- Wanneer u gebruikt `Start-Job` om een taak te starten op een lokale computer, bestaat de taak uit een Executive bovenliggende taak en een onderliggende taak die de opdracht uitvoert.

- Wanneer u de para meter **AsJob** van gebruikt `Invoke-Command` om een taak op een of meer computers te starten, bestaat de taak uit een Executive bovenliggende taak en een onderliggende taak voor elke taak die op elke computer wordt uitgevoerd.

- Wanneer u gebruikt `Invoke-Command` om een opdracht uit te voeren `Start-Job` op een of meer externe computers, is het resultaat hetzelfde als een lokale opdracht die op elke externe computer wordt uitgevoerd. De opdracht retourneert een taak object voor elke computer. Het taak object bestaat uit een Executive bovenliggende taak en één onderliggende taak die de opdracht uitvoert.

De bovenliggende taak vertegenwoordigt alle onderliggende taken. Wanneer u een bovenliggende taak beheert, beheert u ook de bijbehorende onderliggende taken. Als u bijvoorbeeld een bovenliggende taak stopt, worden alle onderliggende taken gestopt. Als u de resultaten van een bovenliggende taak ontvangt, krijgt u de resultaten van alle onderliggende taken.

U kunt echter ook onderliggende taken afzonderlijk beheren. Dit is vooral handig wanneer u een probleem met een taak wilt onderzoeken of als u de resultaten wilt ophalen van slechts één van een aantal onderliggende taken dat is gestart met de para meter **AsJob** van `Invoke-Command` .

De volgende opdracht maakt gebruik van de para meter **AsJob** van `Invoke-Command` om achtergrond taken op de lokale computer en twee externe computers te starten. Met de opdracht wordt de taak opgeslagen in de `$j` variabele.

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

Wanneer u de eigenschappen name en **ChildJob** van de taak in weergeeft `$j` , ziet u dat de opdracht een taak object heeft geretourneerd met drie onderliggende taken, één voor elke computer.

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

Wanneer u de bovenliggende taak weergeeft, ziet u dat de taak is mislukt.

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

Maar wanneer u een `Get-Job` opdracht uitvoert waarmee de onderliggende taken worden opgehaald, laat de uitvoer zien dat er slechts één onderliggende taak is mislukt.

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

Als u de resultaten van alle onderliggende taken wilt ophalen, gebruikt u de `Receive-Job` cmdlet om de resultaten van de bovenliggende taak op te halen. U kunt echter ook de resultaten van een bepaalde onderliggende taak ophalen, zoals wordt weer gegeven in de volgende opdracht.

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

Met de functie voor onderliggende taken van Power shell-achtergrond taken hebt u meer controle over de taken die u uitvoert.

### <a name="job-types"></a>Jobtypen

Power shell ondersteunt verschillende typen taken voor verschillende taken. Met ingang van Windows Power Shell 3,0 kunnen ontwikkel aars ' taak bron adapters ' schrijven waarmee nieuwe taak typen worden toegevoegd aan Power shell en de taak bron adapters in modules worden meegenomen.
Wanneer u de module importeert, kunt u het nieuwe taak type gebruiken in uw sessie.

De PSScheduledJob-module voegt bijvoorbeeld geplande taken toe en de PSWorkflow-module voegt werk stroom taken toe.

Aangepaste taken typen kunnen aanzienlijk verschillen van standaard-Power shell-achtergrond taken. Geplande taken worden bijvoorbeeld op schijf opgeslagen. ze bestaan niet alleen in een bepaalde sessie. Werk stroom taken kunnen worden onderbroken en hervat.

De cmdlets die u gebruikt om aangepaste taken te beheren, zijn afhankelijk van het taak type. Voor sommige gebruikt u de standaard taak cmdlets, zoals `Get-Job` en `Start-Job` . Andere worden geleverd met gespecialiseerde cmdlets die alleen een bepaald type taak beheren. Zie de Help-onderwerpen over het taak type voor gedetailleerde informatie over aangepaste taak typen.

Gebruik de cmdlet om het taak type van een taak te vinden `Get-Job` . `Get-Job` retourneert verschillende taak objecten voor verschillende typen taken. De waarde van de eigenschap **PSJobTypeName** van de `Get-Job` geretourneerde taak objecten geeft het taak type aan.

De volgende tabel bevat de taak typen die bij Power shell worden geleverd.

|    Taak type    |                       Beschrijving                        |
| -------------- | -------------------------------------------------------- |
| BackgroundJob  | Het gebruik van de cmdlet is gestart `Start-Job` .                    |
| RemoteJob      | Gestart met het gebruik van de para meter **AsJob** van de             |
|                | `Invoke-Command` cmdlet.                                 |
| PSWorkflowJob  | Gestart met het gebruik van de para meter **AsJob** van een werk stroom.     |
| PSScheduledJob | Een exemplaar van een geplande taak die is gestart door een taak trigger. |
| CIMJob         | Gestart met het gebruik van de para meter **AsJob** van een cmdlet van een |
|                | CDXML-module.                                            |
| WMIJob         | Gestart met het gebruik van de para meter **AsJob** van een cmdlet van een |
|                | WMI-module.                                              |
| PSEventJob     | Gemaakt met `Register-ObjectEvent` en opgeven van een    |
|                | actie met de **actie** parameter.                    |

Opmerking: voordat u de `Get-Job` cmdlet gebruikt om taken van een bepaald type op te halen, moet u controleren of de module waarmee het taak type wordt toegevoegd, is geïmporteerd in de huidige sessie.
Als dat niet het geval is, `Get-Job` worden er geen taken van dat type opgehaald.

## <a name="examples"></a>Voorbeelden

Met de volgende opdrachten maakt u een lokale achtergrond taak, een externe achtergrond taak, een werk stroom taak en een geplande taak. Vervolgens wordt de cmdlet gebruikt `Get-Job` om de taken op te halen. `Get-Job` Hiermee wordt de geplande taak niet opgehaald, maar worden alle gestarte exemplaren van de geplande taak opgehaald.

Start een achtergrond taak op de lokale computer.

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

Een achtergrond taak starten die wordt uitgevoerd op een externe computer.

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

Een geplande taak maken

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

Een werk stroom maken.

```powershell
PS> workflow Test-Workflow {Get-Process}
```

Voer de werk stroom uit als een taak.

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

De taken ophalen. De `Get-Job` opdracht ontvangt geen geplande taken, maar er worden exemplaren van de geplande taak opgehaald die worden gestart.

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

Als u geplande taken wilt ophalen, gebruikt u de `Get-ScheduledJob` cmdlet.

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a>Zie ook

- [about_Jobs](about_Jobs.md)
- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Remote](about_Remote.md)
- [Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Begin taak](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stoppen-taak](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Verwijderen-taak](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Afsluiten-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
