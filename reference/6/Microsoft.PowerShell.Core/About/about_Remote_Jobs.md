---
description: Hierin wordt beschreven hoe u achtergrond taken uitvoert op externe computers.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: ad0400c4b4c25c9b0c7133bd916af5056dab1430
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252246"
---
# <a name="about-remote-jobs"></a>Over externe taken

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt beschreven hoe u achtergrond taken uitvoert op externe computers.

## <a name="detailed-description"></a>GEDETAILLEERDE BESCHRIJVING

Een achtergrond taak is een opdracht die asynchroon wordt uitgevoerd zonder interactie met de huidige sessie. De opdracht prompt wordt onmiddellijk geretourneerd en u kunt de sessie blijven gebruiken terwijl de taak wordt uitgevoerd.

Achtergrond taken worden standaard uitgevoerd op de lokale computer. U kunt echter verschillende procedures gebruiken om achtergrond taken uit te voeren op externe computers.

In dit onderwerp wordt uitgelegd hoe u een achtergrond taak kunt uitvoeren op een externe computer. Zie [about_Jobs](about_Jobs.md)voor meer informatie over het uitvoeren van achtergrond taken op een lokale computer. Zie [about_Job_Details](about_Job_Details.md)voor meer informatie over achtergrond taken.

## <a name="remote-background-jobs"></a>EXTERNE ACHTERGROND TAKEN

U kunt achtergrond taken uitvoeren op externe computers door drie verschillende methoden te gebruiken.

- Start een interactieve sessie met een externe computer en start een taak in de interactieve sessie. De procedures zijn hetzelfde als het uitvoeren van een lokale taak, hoewel alle acties worden uitgevoerd op de externe computer.

- Een achtergrond taak uitvoeren op een externe computer die de resultaten retourneert naar de lokale computer. Gebruik deze methode als u de resultaten van achtergrond taken wilt verzamelen en deze wilt onderhouden op een centrale locatie op de lokale computer.

- Een achtergrond taak uitvoeren op een externe computer die de resultaten onderhoudt op de externe computer. Gebruik deze methode wanneer de taak gegevens veiliger worden onderhouden op de oorspronkelijke computer.

### <a name="start-a-background-job-in-an-interactive-session"></a>EEN ACHTERGROND TAAK STARTEN IN EEN INTERACTIEVE SESSIE

U kunt een interactieve sessie starten met een externe computer en vervolgens een achtergrond taak starten tijdens de interactieve sessie. Zie about_Remote voor meer informatie over interactieve sessies en zie Enter-PSSession.

De procedure voor het starten van een achtergrond taak in een interactieve sessie is bijna identiek aan de procedure voor het starten van een achtergrond taak op de lokale computer. Alle bewerkingen vinden echter plaats op de externe computer, niet op de lokale computer.

#### <a name="step-1-enter-pssession"></a>STAP 1: ENTER-PSSESSION

Gebruik de cmdlet Enter-PSSession om een interactieve sessie met een externe computer te starten. U kunt de para meter ComputerName van Enter-PSSession gebruiken om een tijdelijke verbinding voor de interactieve sessie tot stand te brengen. U kunt ook de sessie parameter gebruiken om de interactieve sessie uit te voeren in een Power shell-sessie (PSSession).

Met de volgende opdracht wordt een interactieve sessie op de Server01-computer gestart.

```powershell
C:\PS> Enter-PSSession -computername Server01
```

De opdracht prompt wordt weer gegeven om aan te geven dat u nu verbinding hebt met de Server01-computer.

```
Server01\C:>
```

#### <a name="step-2-start-job"></a>STAP 2: START-JOB

Als u een achtergrond taak in de sessie wilt starten, gebruikt u de cmdlet Start-Job.

Met de volgende opdracht wordt een achtergrond taak uitgevoerd waarmee de gebeurtenissen in het Windows Power shell-gebeurtenis logboek op de Server01-computer worden opgehaald. De cmdlet Start-Job retourneert een object dat de taak vertegenwoordigt.

Met deze opdracht wordt het taak object in de \$ taak variabele opgeslagen.

```powershell
Server01\C:> $job = start-job -scriptblock {
  get-eventlog "Windows PowerShell"
}
```

Terwijl de taak wordt uitgevoerd, kunt u de interactieve sessie gebruiken om andere opdrachten uit te voeren, waaronder andere achtergrond taken. U moet de interactieve sessie echter laten openen totdat de taak is voltooid. Als u de sessie beëindigt, wordt de taak onderbroken en gaan de resultaten verloren.

#### <a name="step-3-get-job"></a>STAP 3: GET-JOB

Als u wilt weten of de taak is voltooid, geeft u de waarde van de \$ taak variabele weer of gebruikt u de cmdlet Get-Job om de taak op te halen. De volgende opdracht maakt gebruik van de cmdlet Get-Job om de taak weer te geven.

```powershell
Server01\C:> get-job $job

SessionId  Name  State      HasMoreData  Location   Command
---------  ----  -----      -----------  --------   -------
1          Job1  Complete   True         localhost  get-eventlog "Windows...
```

In de Get-Job uitvoer ziet u dat de taak wordt uitgevoerd op de computer ' localhost ' omdat de taak is gestart op en wordt uitgevoerd op dezelfde computer (in dit geval Server01).

#### <a name="step-4-receive-job"></a>STAP 4: RECEIVE-JOB

Gebruik de cmdlet Receive-Job om de resultaten van de taak op te halen. U kunt de resultaten weer geven in de interactieve sessie of opslaan in een bestand op de externe computer. Met de volgende opdracht worden de resultaten van de taak in de variabele $job opgehaald. De opdracht maakt gebruik van de omleidings operator (>) om de resultaten van de taak op te slaan in het PsLog.txt bestand op de Server01-computer.

```powershell
Server01\C:> receive-job $job > c:\logs\PsLog.txt
```

#### <a name="step-5-exit-pssession"></a>STAP 5: AFSLUITEN-PSSESSION

Gebruik de cmdlet Exit-PSSession om de interactieve sessie te beëindigen. De opdracht prompt wordt weer gegeven om aan te geven dat u terug bent in de oorspronkelijke sessie op de lokale computer.

```powershell
Server01\C:> Exit-PSSession
C:\PS>
```

#### <a name="step-6-invoke-command-get-content"></a>STAP 6: INVOKE-OPDRACHT: GET-CONTENT

Als u de inhoud van het PsLog.txt-bestand op de Server01-computer op elk gewenst moment wilt weer geven, start u een andere interactieve sessie of voert u een externe opdracht uit. Dit type opdracht wordt het beste uitgevoerd in een PSSession (een permanente verbinding) voor het geval u meerdere opdrachten wilt gebruiken om de gegevens in het PsLog.txt-bestand te onderzoeken en te beheren. Zie about_PSSessions voor meer informatie over PSSessions.

De volgende opdrachten gebruiken de New-PSSession cmdlet om een PSSession te maken die is verbonden met de Server01-computer, en ze gebruiken de Invoke-Command cmdlet om een Get-Content opdracht uit te voeren in de PSSession om de inhoud van het bestand weer te geven.

```powershell
$s = new-pssession -computername Server01
invoke-command -session $s -scriptblock {
  get-content c:\logs\pslog.txt}
```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a>Een externe taak starten die de resultaten retourneert naar de lokale COMPUTER \( ASJOB\)

Als u een achtergrond taak wilt starten op een externe computer die de opdracht resultaten retourneert naar de lokale computer, gebruikt u de para meter AsJob van een cmdlet zoals de cmdlet Invoke-Command.

Wanneer u de para meter AsJob gebruikt, wordt het taak object daad werkelijk gemaakt op de lokale computer, zelfs als de taak wordt uitgevoerd op de externe computer. Wanneer de taak is voltooid, worden de resultaten geretourneerd naar de lokale computer.

U kunt de cmdlets gebruiken die het zelfstandige taak onderdeel (de taak-cmdlets) bevatten om elke taak te beheren die door elke cmdlet wordt gemaakt. Veel van de cmdlets met AsJob-para meters gebruiken geen externe communicatie van Power shell, zodat u ze zelfs kunt gebruiken op computers die niet zijn geconfigureerd voor externe communicatie en die niet voldoen aan de vereisten voor externe communicatie.

#### <a name="step-1-invoke-command--asjob"></a>STAP 1: INVOKE-COMMAND-ASJOB

De volgende opdracht maakt gebruik van de AsJob-para meter van Invoke-Command om een achtergrond taak op de Server01-computer te starten. De taak voert een Get-Eventlog opdracht uit waarmee de gebeurtenissen in het systeem logboek worden opgehaald. U kunt de para meter JobName gebruiken om een weergave naam toe te wijzen aan de taak.

```powershell
invoke-command -computername Server01 -scriptblock {
  get-eventlog system} -asjob
```

De resultaten van de opdracht lijken op de volgende voorbeeld uitvoer.

```Output
SessionId   Name   State    HasMoreData   Location   Command
---------   ----   -----    -----------   --------   -------
1           Job1   Running  True          Server01   get-eventlog system
```

Wanneer de para meter AsJob wordt gebruikt, retourneert Invoke-Command hetzelfde type taak object dat Start-Job retourneert. U kunt het taak object opslaan in een variabele, maar u kunt ook een Get-Job opdracht gebruiken om de taak op te halen.

Houd er rekening mee dat de waarde van de eigenschap locatie laat zien dat de taak is uitgevoerd op de Server01-computer.

#### <a name="step-2-get-job"></a>STAP 2: GET-JOB

Voor het beheren van een taak die is gestart met behulp van de para meter AsJob van de cmdlet Invoke-Command, gebruikt u de taak-cmdlets. Omdat het taak object dat de externe taak vertegenwoordigt, zich op de lokale computer bevindt, hoeft u geen externe opdrachten uit te voeren om de taak te beheren.

Gebruik een Get-Job opdracht om te bepalen of de taak is voltooid. Met de volgende opdracht worden alle taken opgehaald die in de huidige sessie zijn gestart.

```powershell
get-job
```

Omdat de externe taak is gestart in de huidige sessie, haalt een lokale Get-Job opdracht de taak op. De eigenschap State van het taak object geeft aan dat de opdracht is voltooid.

```Output
SessionId   Name   State      HasMoreData   Location   Command
---------   ----   -----      -----------   --------   -------
1           Job1   Completed  True          Server01   get-eventlog system
```

#### <a name="step-3-receive-job"></a>STAP 3: RECEIVE-JOB

Gebruik de cmdlet Receive-Job om de resultaten van de taak op te halen. Omdat de resultaten van de taak automatisch worden teruggestuurd naar de computer waarop het taak object zich bevindt, kunt u de resultaten ophalen met een lokale Receive-Job opdracht.

De volgende opdracht maakt gebruik van de cmdlet Receive-Job om de resultaten van de taak op te halen. De sessie-ID wordt gebruikt om de taak te identificeren. Met deze opdracht worden de taak resultaten opgeslagen in de variabele $results. U kunt de resultaten ook omleiden naar een bestand.

```powershell
$results = receive-job -id 1
```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a>EEN EXTERNE TAAK STARTEN DIE DE RESULTATEN OP DE EXTERNE COMPUTER BEWAART

Als u een achtergrond taak wilt starten op een externe computer die de opdracht resultaten op de externe computer houdt, gebruikt u de cmdlet Invoke-Command om een Start-Job opdracht uit te voeren op een externe computer. U kunt deze methode gebruiken om achtergrond taken uit te voeren op meerdere computers.

Wanneer u een Start-Job opdracht op afstand uitvoert, wordt het taak object op de externe computer gemaakt en worden de taak resultaten op de externe computer bewaard.
Vanuit het perspectief van de taak zijn alle bewerkingen lokaal. U hoeft alleen opdrachten op afstand uit te voeren om een lokale taak op de externe computer te beheren.

#### <a name="step-1-invoke-command-start-job"></a>STAP 1: INVOKE-OPDRACHT STARTEN-TAAK

Gebruik de cmdlet Invoke-Command om een Start-Job opdracht uit te voeren op een externe computer.

Voor deze opdracht is een PSSession (een permanente verbinding) vereist. Als u de para meter ComputerName van Invoke-Command gebruikt om een tijdelijke verbinding tot stand te brengen, wordt de Invoke-Command-opdracht als voltooid beschouwd wanneer het taak object wordt geretourneerd. Als gevolg hiervan wordt de tijdelijke verbinding gesloten en wordt de taak geannuleerd.

De volgende opdracht maakt gebruik van de New-PSSession cmdlet om een PSSession te maken die is verbonden met de Server01-computer. Met de opdracht slaat u de PSSession op in de \$ variabele s.

```powershell
$s = new-pssession -computername Server01
```

De volgende opdracht maakt gebruik van de cmdlet Invoke-Command om een Start-Job opdracht uit te voeren in de PSSession. De Start-Job opdracht en de Get-Eventlog opdracht staan tussen accolades.

```powershell
invoke-command -session $s -scriptblock {
  start-job -scriptblock {get-eventlog system}}
```

De resultaten zijn vergelijkbaar met de volgende voorbeeld uitvoer.

```Output
Id       Name    State      HasMoreData     Location   Command
--       ----    -----      -----------     --------   -------
2        Job2    Running    True            Localhost  get-eventlog system
```

Wanneer u een Start-Job opdracht op afstand uitvoert, Invoke-Command retourneert hetzelfde type taak object dat Start-Job retourneert. U kunt het taak object opslaan in een variabele, maar u kunt ook een Get-Job opdracht gebruiken om de taak op te halen.

Houd er rekening mee dat de waarde van de eigenschap locatie aangeeft dat de taak is uitgevoerd op de lokale computer, ook wel ' LocalHost ' genoemd, hoewel de taak is uitgevoerd op de Server01-computer. Omdat het taak object op de Server01-computer wordt gemaakt en de taak wordt uitgevoerd op dezelfde computer, wordt deze als een lokale achtergrond taak beschouwd.

#### <a name="step-2-invoke-command-get-job"></a>STAP 2: INVOKE-OPDRACHT GET-JOB

Als u een externe achtergrond taak wilt beheren, gebruikt u de taak-cmdlets. Omdat het taak object zich op de externe computer bevindt, moet u externe opdrachten uitvoeren om de taak resultaten op te halen, te stoppen, te wachten of op te halen.

Als u wilt zien of de taak is voltooid, gebruikt u een Invoke-Command opdracht om een Get-Job opdracht uit te voeren in de PSSession die is verbonden met de Server01-computer.

```powershell
invoke-command -session $s -scriptblock {get-job}
```

De opdracht retourneert een taak object. De eigenschap State van het taak object geeft aan dat de opdracht is voltooid.

```Output
SessionId   Name  State      HasMoreData   Location   Command
---------   ----  -----      -----------   --------   -------
2           Job2  Completed  True          LocalHost   get-eventlog system
```

#### <a name="step-3-invoke-command-receive-job"></a>STAP 3: INVOKE-OPDRACHT RECEIVE-JOB

Als u de resultaten van de taak wilt weer geven, gebruikt u de cmdlet Invoke-Command om een Receive-Job opdracht uit te voeren in de PSSession die is verbonden met de Server01-computer.

De volgende opdracht maakt gebruik van de cmdlet Receive-Job om de resultaten van de taak op te halen. De sessie-ID wordt gebruikt om de taak te identificeren. Met deze opdracht worden de taak resultaten opgeslagen in de \$ resultaten variabele. De para meter ' Keep ' van Receive-Job wordt gebruikt om het resultaat in de taak cache op de externe computer te blijven gebruiken.

```powershell
$results = invoke-command -session $s -scriptblock {
  receive-job -sessionid 2 -keep}
```

U kunt de resultaten ook omleiden naar een bestand op de lokale of externe computer.
De volgende opdracht maakt gebruik van een omleidings operator om de resultaten op te slaan in een bestand op de Server01-computer.

```powershell
invoke-command -session $s -command {
  receive-job -sessionid 2 > c:\logs\pslog.txt}
```

## <a name="see-also"></a>ZIE OOK

[about_Jobs](about_Jobs.md)

[about_Job_Details](about_Job_Details.md)

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Begin taak](xref:Microsoft.PowerShell.Core.Start-Job)

[Get-job](xref:Microsoft.PowerShell.Core.Get-Job)

[Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)

[Stoppen-taak](xref:Microsoft.PowerShell.Core.Stop-Job)

[Verwijderen-taak](xref:Microsoft.PowerShell.Core.Remove-Job)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Afsluiten-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
