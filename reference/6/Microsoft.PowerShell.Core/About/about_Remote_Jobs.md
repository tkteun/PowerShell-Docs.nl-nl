---
description: Hierin wordt beschreven hoe u taken uitvoert op externe computers.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 734bcdaea41a8c0cd589f0f31719a2069264adf3
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524384"
---
# <a name="about-remote-jobs"></a>Over externe taken

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u taken uitvoert op externe computers.

## <a name="detailed-description"></a>Gedetailleerde beschrijving

Met Power shell worden opdrachten en scripts gelijktijdig uitgevoerd via taken. Er zijn drie typen taken die door Power shell worden geboden ter ondersteuning van gelijktijdigheid.

- `RemoteJob` -Opdrachten en scripts worden uitgevoerd in een externe sessie.
- `BackgroundJob` -Opdrachten en scripts worden in een afzonderlijk proces op de lokale computer uitgevoerd. Zie [About Jobs](about_Jobs.md) (Taken) voor meer informatie.
- `PSTaskJob` of `ThreadJob` -opdrachten en scripts worden uitgevoerd in een afzonderlijke thread binnen hetzelfde proces op de lokale computer. Zie [about_Thread_Jobs](about_Thread_Jobs.md)voor meer informatie.

Scripts op afstand uitvoeren op een afzonderlijke machine of in een afzonderlijk proces, bieden een uitstekende isolatie. Fouten die optreden in de externe taak hebben geen invloed op andere actieve taken of de bovenliggende sessie die de taak heeft gestart. De externe laag voegt echter overhead toe, inclusief object serialisatie. Alle objecten worden geserialiseerd en gedeserialiseerd wanneer ze worden door gegeven tussen de bovenliggende sessie en de externe (taak) sessie. Serialisatie van grote complexe gegevens objecten kan grote hoeveel heden reken-en geheugen bronnen verbruiken en grote hoeveel heden gegevens via het netwerk overzetten.

> [!IMPORTANT]
> Met de bovenliggende sessie die de taak heeft gemaakt, wordt ook de taak status bewaakt en worden de pijplijn gegevens verzameld. Het onderliggende proces van de taak wordt beëindigd door de bovenliggende bewerking zodra de taak de status voltooid heeft bereikt. Als de bovenliggende sessie wordt beëindigd, worden alle actieve onderliggende taken beëindigd samen met de onderliggende processen.

Er zijn twee manieren om deze situatie te omzeilen:

1. Gebruiken `Invoke-Command` om taken te maken die worden uitgevoerd in sessies zonder verbinding. Zie de sectie [ontkoppelde processen](#how-to-run-as-a-detached-process) van dit artikel.
1. Gebruiken `Start-Process` om een nieuw proces te maken in plaats van een taak. Zie [start-process](xref:Microsoft.PowerShell.Management.Start-Process)(Engelstalig) voor meer informatie.

## <a name="remote-jobs"></a>Externe taken

U kunt taken uitvoeren op externe computers door drie verschillende methoden te gebruiken.

- Een interactieve sessie starten op een externe computer. Start vervolgens een taak in de interactieve sessie. De procedures zijn hetzelfde als het uitvoeren van een lokale taak, hoewel alle acties worden uitgevoerd op de externe computer.

- Een taak uitvoeren op een externe computer die de resultaten retourneert naar de lokale computer. Gebruik deze methode als u de resultaten van taken wilt verzamelen en deze wilt onderhouden op een centrale locatie op de lokale computer.

- Een taak uitvoeren op een externe computer die de resultaten onderhoudt op de externe computer. Gebruik deze methode wanneer de taak gegevens veiliger worden onderhouden op de oorspronkelijke computer.

### <a name="start-a-job-in-an-interactive-session"></a>Een taak starten in een interactieve sessie

U kunt een interactieve sessie starten met een externe computer en vervolgens een taak starten tijdens de interactieve sessie. Zie about_Remote voor meer informatie over interactieve sessies en Zie `Enter-PSSession` .

De procedure voor het starten van een taak in een interactieve sessie is bijna identiek aan de procedure voor het starten van een achtergrond taak op de lokale computer. Alle bewerkingen vinden echter plaats op de externe computer, niet op de lokale computer.

1. Gebruik de `Enter-PSSession` cmdlet om een interactieve sessie met een externe computer te starten. U kunt de para meter ComputerName van gebruiken `Enter-PSSession` om een tijdelijke verbinding voor de interactieve sessie tot stand te brengen. U kunt ook de sessie parameter gebruiken om de interactieve sessie uit te voeren in een Power shell-sessie (PSSession).

   Met de volgende opdracht wordt een interactieve sessie op de Server01-computer gestart.

   ```powershell
   C:\PS> Enter-PSSession -computername Server01
   ```

   De opdracht prompt wordt weer gegeven om aan te geven dat u nu verbinding hebt met de Server01-computer.

   ```
   Server01\C:>
   ```

1. Als u een externe taak in de sessie wilt starten, gebruikt u de `Start-Job` cmdlet. Met de volgende opdracht wordt een externe taak uitgevoerd waarmee de gebeurtenissen in het Windows Power shell-gebeurtenis logboek op de Server01-computer worden opgehaald. De `Start-Job` cmdlet retourneert een object dat de taak vertegenwoordigt.

   Met deze opdracht wordt het taak object in de `$job` variabele opgeslagen.

   ```powershell
   Server01\C:> $job = Start-Job -scriptblock {
     Get-Eventlog "Windows PowerShell"
   }
   ```

   Terwijl de taak wordt uitgevoerd, kunt u de interactieve sessie gebruiken om andere opdrachten uit te voeren, waaronder andere taken. U moet de interactieve sessie echter laten openen totdat de taak is voltooid. Als u de sessie beëindigt, wordt de taak onderbroken en gaan de resultaten verloren.

1. Als u wilt weten of de taak is voltooid, geeft u de waarde van de `$job` variabele weer of gebruikt `Get-Job` u de cmdlet om de taak op te halen. De volgende opdracht gebruikt de `Get-Job` cmdlet om de taak weer te geven.

   ```powershell
   Server01\C:> Get-Job $job

   SessionId  Name  State      HasMoreData  Location   Command
   ---------  ----  -----      -----------  --------   -------
   1          Job1  Complete   True         localhost  Get-Eventlog "Windows...
   ```

   `Get-Job`In de uitvoer ziet u dat de taak wordt uitgevoerd op de ' localhost ' computer omdat de taak is gestart op en wordt uitgevoerd op dezelfde computer (in dit geval Server01).

1. Gebruik de cmdlet om de resultaten van de taak te verkrijgen `Receive-Job` . U kunt de resultaten weer geven in de interactieve sessie of opslaan in een bestand op de externe computer. Met de volgende opdracht worden de resultaten van de taak in de variabele $job opgehaald. De opdracht maakt gebruik van de omleidings operator ( `>` ) om de resultaten van de taak op te slaan in het PsLog.txt bestand op de Server01-computer.

   ```powershell
   Server01\C:> Receive-Job $job > c:\logs\PsLog.txt
   ```

1. Gebruik de cmdlet om de interactieve sessie te beëindigen `Exit-PSSession` . De opdracht prompt wordt weer gegeven om aan te geven dat u terug bent in de oorspronkelijke sessie op de lokale computer.

   ```powershell
   Server01\C:> Exit-PSSession
   C:\PS>
   ```

1. Als u de inhoud van het `PsLog.txt` bestand op de Server01-computer op elk gewenst moment wilt weer geven, start u een andere interactieve sessie of voert u een externe opdracht uit. Dit type opdracht wordt het beste uitgevoerd in een PSSession (een permanente verbinding) voor het geval u meerdere opdrachten wilt gebruiken om de gegevens in het bestand te onderzoeken en te beheren `PsLog.txt` . Zie [about_PSSessions](about_PSSessions.md)voor meer informatie over PSSessions.

   De volgende opdrachten gebruiken de `New-PSSession` cmdlet om een **PSSession** te maken die is verbonden met de Server01-computer, en ze gebruiken de `Invoke-Command` cmdlet om een `Get-Content` opdracht uit te voeren in de PSSession om de inhoud van het bestand weer te geven.

   ```powershell
   $s = New-PSSession -computername Server01
   Invoke-Command -session $s -scriptblock {
     Get-Content c:\logs\pslog.txt}
   ```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a>Een externe taak starten die de resultaten retourneert naar de lokale computer (AsJob)

Als u een taak wilt starten op een externe computer die de opdracht resultaten retourneert naar de lokale computer, gebruikt u de para meter **AsJob** van een cmdlet zoals de `Invoke-Command` cmdlet.

Wanneer u de para meter **AsJob** gebruikt, wordt het taak object daad werkelijk gemaakt op de lokale computer, zelfs als de taak wordt uitgevoerd op de externe computer. Wanneer de taak is voltooid, worden de resultaten geretourneerd naar de lokale computer.

U kunt de cmdlets gebruiken die het zelfstandige taak onderdeel (de taak-cmdlets) bevatten om elke taak te beheren die door elke cmdlet wordt gemaakt. Veel van de cmdlets met **AsJob** -para meters gebruiken geen externe communicatie van Power shell, zodat u ze zelfs kunt gebruiken op computers die niet zijn geconfigureerd voor externe communicatie en die niet voldoen aan de vereisten voor externe communicatie.

1. De volgende opdracht maakt gebruik van de para meter **AsJob** van `Invoke-Command` om een taak op de Server01-computer te starten. De taak voert een `Get-Eventlog` opdracht uit waarmee de gebeurtenissen in het systeem logboek worden opgehaald. U kunt de para meter JobName gebruiken om een weergave naam toe te wijzen aan de taak.

   ```powershell
   Invoke-Command -computername Server01 -scriptblock {
     Get-Eventlog system} -AsJob
   ```

   De resultaten van de opdracht lijken op de volgende voorbeeld uitvoer.

   ```Output
   SessionId   Name   State    HasMoreData   Location   Command
   ---------   ----   -----    -----------   --------   -------
   1           Job1   Running  True          Server01   Get-Eventlog system
   ```

   Wanneer de para meter **AsJob** wordt gebruikt, `Invoke-Command` retourneert hetzelfde type taak object dat `Start-Job` retourneert. U kunt het taak object opslaan in een variabele, maar u kunt ook een `Get-Job` opdracht gebruiken om de taak op te halen.

   Houd er rekening mee dat de waarde van de eigenschap locatie laat zien dat de taak is uitgevoerd op de Server01-computer.

1. Voor het beheren van een taak die is gestart met behulp van de para meter **AsJob** van de `Invoke-Command` cmdlet, gebruikt u de taak-cmdlets. Omdat het taak object dat de externe taak vertegenwoordigt, zich op de lokale computer bevindt, hoeft u geen externe opdrachten uit te voeren om de taak te beheren.

   Gebruik een opdracht om te bepalen of de taak is voltooid `Get-Job` . Met de volgende opdracht worden alle taken opgehaald die in de huidige sessie zijn gestart.

   ```powershell
   Get-Job
   ```

   Omdat de externe taak is gestart in de huidige sessie, haalt een lokale `Get-Job` opdracht de taak op. De eigenschap State van het taak object geeft aan dat de opdracht is voltooid.

   ```Output
   SessionId   Name   State      HasMoreData   Location   Command
   ---------   ----   -----      -----------   --------   -------
   1           Job1   Completed  True          Server01   Get-Eventlog system
   ```

1. Gebruik de cmdlet om de resultaten van de taak te verkrijgen `Receive-Job` . Omdat de resultaten van de taak automatisch worden teruggestuurd naar de computer waarop het taak object zich bevindt, kunt u de resultaten ophalen met een lokale `Receive-Job` opdracht.

   De volgende opdracht gebruikt de `Receive-Job` cmdlet om de resultaten van de taak op te halen. De sessie-ID wordt gebruikt om de taak te identificeren. Met deze opdracht worden de taak resultaten opgeslagen in de variabele $results. U kunt de resultaten ook omleiden naar een bestand.

   ```powershell
   $results = Receive-Job -id 1
   ```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a>Een externe taak starten die de resultaten op de externe computer bewaart

Als u een taak wilt starten op een externe computer die de opdracht resultaten op de externe computer houdt, gebruikt u de `Invoke-Command` cmdlet om een `Start-Job` opdracht op een externe computer uit te voeren. U kunt deze methode gebruiken om taken uit te voeren op meerdere computers.

Wanneer u een `Start-Job` opdracht op afstand uitvoert, wordt het taak object op de externe computer gemaakt en worden de taak resultaten op de externe computer bewaard.
Vanuit het perspectief van de taak zijn alle bewerkingen lokaal. U hoeft alleen opdrachten op afstand uit te voeren om een lokale taak op de externe computer te beheren.

1. Gebruik de `Invoke-Command` cmdlet om een opdracht uit te voeren `Start-Job` op een externe computer.

   Voor deze opdracht is een PSSession (een permanente verbinding) vereist. Als u de para meter ComputerName van gebruikt `Invoke-Command` om een tijdelijke verbinding tot stand te brengen, `Invoke-Command` wordt de opdracht als voltooid beschouwd wanneer het taak object wordt geretourneerd. Als gevolg hiervan wordt de tijdelijke verbinding gesloten en wordt de taak geannuleerd.

   De volgende opdracht maakt gebruik van de `New-PSSession` cmdlet om een PSSession te maken die is verbonden met de Server01-computer. Met de opdracht slaat u de PSSession op in de `$s` variabele.

   ```powershell
   $s = New-PSSession -computername Server01
   ```

   De volgende opdracht maakt gebruik `Invoke-Command` van de cmdlet om een opdracht uit te voeren `Start-Job` in de PSSession. De `Start-Job` opdracht en de `Get-Eventlog` opdracht staan tussen accolades.

   ```powershell
   Invoke-Command -session $s -scriptblock {
     Start-Job -scriptblock {Get-Eventlog system}}
   ```

   De resultaten zijn vergelijkbaar met de volgende voorbeeld uitvoer.

   ```Output
   Id       Name    State      HasMoreData     Location   Command
   --       ----    -----      -----------     --------   -------
   2        Job2    Running    True            Localhost  Get-Eventlog system
   ```

   Wanneer u een `Start-Job` opdracht extern uitvoert, `Invoke-Command` retourneert hetzelfde type taak object dat `Start-Job` retourneert. U kunt het taak object opslaan in een variabele, maar u kunt ook een `Get-Job` opdracht gebruiken om de taak op te halen.

   Houd er rekening mee dat de waarde van de eigenschap **locatie** aangeeft dat de taak is uitgevoerd op de lokale computer, ook wel ' localhost ' genoemd, hoewel de taak is uitgevoerd op de Server01-computer. Omdat het taak object op de Server01-computer wordt gemaakt en de taak wordt uitgevoerd op dezelfde computer, wordt deze als een lokale achtergrond taak beschouwd.

1. Als u een externe taak wilt beheren, gebruikt u de **taak** -cmdlets. Omdat het taak object zich op de externe computer bevindt, moet u externe opdrachten uitvoeren om de taak resultaten op te halen, te stoppen, te wachten of op te halen.

   Als u wilt zien of de taak is voltooid, gebruikt u een `Invoke-Command` opdracht voor `Get-Job` het uitvoeren van een opdracht in de PSSession die is verbonden met de Server01-computer.

   ```powershell
   Invoke-Command -session $s -scriptblock {Get-Job}
   ```

   De opdracht retourneert een taak object. De eigenschap **State** van het taak object geeft aan dat de opdracht is voltooid.

   ```Output
   SessionId   Name  State      HasMoreData   Location   Command
   ---------   ----  -----      -----------   --------   -------
   2           Job2  Completed  True          LocalHost   Get-Eventlog system
   ```

1. Als u de resultaten van de taak wilt ophalen, gebruikt u de `Invoke-Command` cmdlet om een `Receive-Job` opdracht uit te voeren in de PSSession die is verbonden met de Server01-computer.

   De volgende opdracht gebruikt de `Receive-Job` cmdlet om de resultaten van de taak op te halen. De sessie-ID wordt gebruikt om de taak te identificeren. Met deze opdracht worden de taak resultaten in de `$results` variabele opgeslagen. Hierbij wordt de para meter ' Keep ' gebruikt `Receive-Job` om het resultaat in de taak cache op de externe computer te blijven.

   ```powershell
   $results = Invoke-Command -session $s -scriptblock {
     Receive-Job -SessionId 2 -Keep
   }
   ```

   U kunt de resultaten ook omleiden naar een bestand op de lokale of externe computer.
   De volgende opdracht maakt gebruik van een omleidings operator om de resultaten op te slaan in een bestand op de Server01-computer.

   ```powershell
   Invoke-Command -session $s -command {
     Receive-Job -SessionId 2 > c:\logs\pslog.txt
   }
   ```

## <a name="how-to-run-as-a-detached-process"></a>Uitvoeren als een ontkoppeld proces

Zoals eerder vermeld, worden alle actieve onderliggende taken beëindigd samen met de onderliggende processen, wanneer de bovenliggende sessie wordt beëindigd. U kunt externe toegang op de lokale computer gebruiken om taken uit te voeren die niet zijn gekoppeld aan de huidige Power shell-sessie.

Maak een nieuwe Power shell-sessie op de lokale computer. Het gebruik `Invoke-Command` om een taak in deze sessie te starten. `Invoke-Command` Hiermee kunt u de verbinding van een externe sessie verbreken en de bovenliggende sessie beëindigen. U kunt later een nieuwe Power shell-sessie starten en verbinding maken met de eerder verbroken sessie om de bewaking van de taak te hervatten. Alle gegevens die naar de oorspronkelijke Power shell-sessie zijn geretourneerd, gaan echter verloren wanneer de sessie wordt beëindigd. Alleen nieuwe gegevens objecten die zijn gegenereerd nadat de verbinding is verbroken, worden geretourneerd wanneer de verbinding is hersteld.

```powershell
# Create remote session on local machine
PS> $session = New-PSSession -cn localhost

# Start remote job
PS> $job = Invoke-Command -Session $session -ScriptBlock { 1..60 | % { sleep 1; "Output $_" } } -AsJob
PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Running       True            localhost     1..60 | % { sleep 1; ...

# Disconnect the job session
PS> Disconnect-PSSession $session

Id Name         Transport ComputerName    ComputerType    State         ConfigurationName     Availability
-- ----         --------- ------------    ------------    -----         -----------------     ------------
1 Runspace1     WSMan     localhost       RemoteMachine   Disconnected  Microsoft.PowerShell          None

PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Disconnected  True            localhost     1..60 | % { sleep 1;

# Reconnect the session to a new job object
PS> $jobNew = Receive-PSSession -Session $session -OutTarget Job
PS> $job | Wait-Job | Receive-Job
Output 9
Output 10
Output 11
...
```

Voor dit voor beeld zijn de taken nog steeds gekoppeld aan een bovenliggende Power shell-sessie.
De bovenliggende sessie is echter niet de oorspronkelijke Power shell-sessie waar `Invoke-Command` werd uitgevoerd.

## <a name="see-also"></a>Zie tevens

- [about_Jobs](about_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_Remote_Variables](about_Remote_Variables.md)
- [Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Begin taak](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stoppen-taak](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Verwijderen-taak](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Afsluiten-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
