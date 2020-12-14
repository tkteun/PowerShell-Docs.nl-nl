---
description: Bevat gedetailleerde informatie over Power shell-sessies en de rol die ze afspelen in externe opdrachten.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssession_details?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSession_Details
ms.openlocfilehash: 79340e5d0ae1fe047f1f37bdfdbb1bebe920d851
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705648"
---
# <a name="about-pssession-details"></a>Informatie over PSSession

## <a name="short-description"></a>Korte beschrijving
Bevat gedetailleerde informatie over Power shell-sessies en de rol die ze afspelen in externe opdrachten.

## <a name="long-description"></a>Lange beschrijving

Een sessie is een omgeving waarin Power shell wordt uitgevoerd. Telkens wanneer u Power shell start, wordt er een sessie gemaakt. U kunt op uw computer of op een andere computer extra sessies maken met de naam ' Power shell-sessies ' of ' PSSessions '.

In tegens telling tot de sessies die Power shell voor u maakt, kunt u de PSSessions die u hebt gemaakt, regelen en beheren.

PSSessions speelt een belang rijke rol bij extern computer gebruik. Wanneer u een PSSession maakt die is verbonden met een externe computer, brengt Power shell een permanente verbinding met de externe computer tot stand om de PSSession te ondersteunen. U kunt de PSSession gebruiken om een reeks opdrachten, functies en scripts uit te voeren die gegevens delen.

Dit onderwerp bevat gedetailleerde informatie over sessies en PSSessions in Power shell. Zie [about_PSSessions](about_PSSessions.md)voor algemene informatie over de taken die u met sessies kunt uitvoeren.

## <a name="about-sessions"></a>Over sessies

Technisch gezien is een sessie een uitvoerings omgeving waarin Power shell wordt uitgevoerd. Elke sessie bevat een exemplaar van System. Management. Automation engine en een hostprogramma waarin Power shell wordt uitgevoerd. De host kan de vertrouwde Power shell-console zijn of een ander programma dat opdrachten uitvoert, zoals Cmd.exe, of een programma dat is gebouwd voor het hosten van Power shell, zoals Windows Power shell Integrated Scripting Environment (ISE). Vanuit een Windows-perspectief is een sessie een Windows-proces op de doel computer.

Elke sessie is onafhankelijk geconfigureerd. Het bevat eigen eigenschappen, een eigen uitvoerings beleid en de eigen profielen. De omgeving die zich voordoet wanneer de sessie wordt gemaakt, blijft in de levens duur, zelfs als u de omgeving op de computer wijzigt. Alle sessies worden gemaakt in een globaal bereik, zelfs in sessies die u in een script maakt.

U kunt in een sessie in één keer slechts één opdracht (of opdracht pijplijn) uitvoeren. Een tweede opdracht die synchroon wordt uitgevoerd (één op een keer), wacht tot vier minuten totdat de eerste opdracht is voltooid. Een tweede opdracht die asynchroon (gelijktijdig) wordt uitgevoerd, mislukt.

## <a name="about-pssessions"></a>Over PSSessions

Telkens wanneer u Power shell start, wordt er een sessie gemaakt. En Power Shell maakt tijdelijke sessies voor het uitvoeren van afzonderlijke opdrachten.
U kunt echter ook sessies maken (' Power shell-sessies ' of ' PSSessions ' genoemd) die u beheert en beheert.

PSSessions zijn essentieel voor externe opdrachten. Als u de para meter **ComputerName** van de `Invoke-Command` `Enter-PSSession` cmdlets gebruikt, maakt Power shell een tijdelijke sessie om de opdracht uit te voeren en wordt de sessie gesloten zodra de opdracht of de interactieve sessie is voltooid.

Als u echter de `New-PSSession` -cmdlet gebruikt om een PSSession te maken, brengt Power shell een permanente sessie tot stand op de externe computer waarin u meerdere opdrachten of interactieve sessies kunt uitvoeren. De PSSessions die u maakt, blijven open en beschikbaar voor gebruik totdat u ze verwijdert of totdat u de sessie sluit waarin deze zijn gemaakt.

Wanneer u een PSSession op een externe computer maakt, maakt het systeem een Power Shell-proces op de externe computer en wordt er een verbinding tot stand gebracht tussen de lokale computer en het proces op de externe computer. Wanneer u een PSSession maakt op de lokale computer, worden zowel het nieuwe proces als de verbindingen gemaakt op de lokale computer.

## <a name="when-do-i-need-a-pssession"></a>Wanneer heb ik een PSSession nodig?

De `Invoke-Command` `Enter-PSSession` cmdlets en hebben zowel **ComputerName** als **Session** -para meters. U kunt ofwel gebruiken om een externe opdracht uit te voeren.

Gebruik de para meter **ComputerName** om één opdracht uit te voeren of een reeks niet-gerelateerde opdrachten op een of meer computers.

U hebt een permanente verbinding met de externe computer nodig om opdrachten uit te voeren die gegevens delen. In dat geval maakt u een PSSession en gebruikt u vervolgens de **sessie** parameter om opdrachten uit te voeren in de PSSession.

Veel andere cmdlets die gegevens ophalen van externe computers, zoals `Get-Process` ,, `Get-Service` `Get-EventLog` en `Get-WmiObject` alleen een **ComputerName** -para meter hebben. Ze gebruiken andere technologieën dan externe communicatie van Power shell om gegevens op afstand te verzamelen. Deze cmdlets hebben geen **sessie** parameter, maar u kunt de `Invoke-Command` cmdlet gebruiken om deze opdrachten uit te voeren in een PSSession.

## <a name="how-do-i-create-a-pssession"></a>Hoe maak ik een PSSession?

Gebruik de cmdlet om een PSSession te maken `New-PSSession` . U kunt gebruiken `New-PSSession` om een PSSession te maken op een lokale of externe computer.

## <a name="can-i-create-a-pssession-on-any-computer"></a>Kan ik een PSSession op elke computer maken?

Als u een PSSession wilt maken die is verbonden met een externe computer, moet de computer zijn geconfigureerd voor externe toegang in Power shell. De huidige gebruiker moet lid zijn van de groep Administrators op de externe computer, of de huidige gebruiker moet de referenties kunnen opgeven van een lid van de groep Administrators. Zie [about_Remote_Requirements](about_Remote_Requirements.md)voor meer informatie.

## <a name="can-i-see-my-pssessions-in-other-sessions"></a>Kan ik mijn PSSessions in andere sessies zien?

Vanaf Windows Power Shell 3,0 krijgt de para meter **ComputerName** van de `Get-PSSession` cmdlet PSSessions die u hebt gemaakt op de opgegeven externe computers.

Actieve PSSessions worden onderhouden op de externe computer (de ' server-side ' van een verbinding) en u kunt deze vanuit elke sessie op elke computer ophalen.

Als u bijvoorbeeld een PSSession maakt van de Server01-computer naar de Server02-computer en vervolgens overschakelt naar de Server03-computer, kunt u een opdracht als de volgende gebruiken om de sessie op te halen.

```powershell
Get-PSSession -ComputerName Server02
```

Zelfs als u de verbinding met de sessie verbreekt, wordt de sessie op de externe computer gehandhaafd totdat u deze verwijdert of er een time-out optreedt.

In Windows Power Shell 2,0 kunt u alleen de PSSessions ophalen die u in de huidige sessie hebt gemaakt. U kunt geen PSSessions ophalen die u in andere sessies hebt gemaakt.

Zie [Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)voor meer informatie.

## <a name="can-i-see-the-pssessions-that-others-have-created-on-my-computer"></a>Kan ik de PSSessions zien die anderen op mijn computer hebben gemaakt?

U kunt alleen de PSSessions ophalen en beheren die anderen alleen hebben gemaakt als u de referenties kunt opgeven van de gebruiker die de PSSession heeft gemaakt of de sessie configuratie die de PSSession gebruikt, inclusief runas-referenties. Als dat niet het geval is, kunt u alleen de PSSessions die u hebt gemaakt, ophalen, verbinding maken met en beheren.

## <a name="can-i-connect-to-a-pssession-from-a-different-computer"></a>Kan ik verbinding maken met een PSSession vanaf een andere computer?

Vanaf Windows Power Shell 3,0 zijn PSSessions onafhankelijk van de sessies waarin ze zijn gemaakt. Actieve PSSessions worden onderhouden op de computer op het externe of aan de server zijde van een verbinding.

U kunt de `Disconnect-PSSession` cmdlet gebruiken om de verbinding met een PSSession te verbreken. De PSSession is losgekoppeld van de lokale sessie, maar blijft actief op de externe computer.
Opdrachten blijven actief in de niet-verbonden PSSession. U kunt Power shell sluiten en de oorspronkelijke computer afsluiten zonder de PSSession te onderbreken.

Vervolgens kunt u, zelfs later, de cmdlet gebruiken `Get-PSSession` om de PSSession en de `Connect-PSSession` cmdlet te verkrijgen om verbinding te maken met de PSSession vanuit een nieuwe sessie op een andere computer.

Zie [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)voor meer informatie.

## <a name="what-happens-to-my-pssession-if-my-computer-stops"></a>Wat gebeurt er met mijn PSSession als mijn computer stopt?

Niet-verbonden PSSessions zijn onafhankelijk van de sessies waarin ze zijn gemaakt. Als u een PSSession verbreekt en vervolgens de oorspronkelijke computer sluit, wordt de PSSession op de externe computer onderhouden.

Daarnaast probeert Power shell actieve PSSessions te herstellen die onbedoeld zijn losgekoppeld, zoals het opnieuw opstarten van een computer, een tijdelijke stroom storing of een onderbreking van het netwerk. Power shell probeert de PSSession bij te houden of te herstellen, als de oorspronkelijke sessie nog steeds beschikbaar is, of de status niet verbonden als dat niet het geval is.

Een ' actieve ' PSSession is een met-opdrachten. Als een PSSession is verbonden (niet verbroken) en de opdrachten worden uitgevoerd in de PSSession wanneer de verbonden sessie wordt gesloten, probeert Power shell de PSSession op de externe computer te onderhouden. Als er echter geen opdrachten worden uitgevoerd in de PSSession, wordt de PSSession door Power shell gesloten wanneer de verbonden sessie wordt gesloten.

Zie [about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)voor meer informatie.

## <a name="can-i-run-a-background-job-in-a-pssession"></a>Kan ik een achtergrond taak uitvoeren in een PSSession?

Ja. Een achtergrond taak is een opdracht die asynchroon op de achtergrond wordt uitgevoerd zonder interactie met de huidige sessie. Wanneer u een opdracht verzendt om een taak te starten, retourneert de opdracht een taak object, maar de taak wordt uitgevoerd op de achtergrond totdat deze is voltooid.

Als u een achtergrond taak wilt starten op een lokale computer, gebruikt u de `Start-Job` opdracht.
U kunt de achtergrond taak uitvoeren in een tijdelijke verbinding (door de para meter **ComputerName** te gebruiken) of in een PSSession (met behulp van de para meter **Session** ).

Als u een achtergrond taak wilt starten op een externe computer, gebruikt u de `Invoke-Command` cmdlet met de para meter **AsJob** of gebruikt `Invoke-Command` u de cmdlet om een opdracht uit te voeren `Start-Job` op een externe computer. Wanneer u de para meter **AsJob** gebruikt, kunt u de **computer naam** of de **sessie** parameters gebruiken.

Wanneer `Invoke-Command` u gebruikt om een opdracht uit te voeren `Start-Job` , moet u de opdracht uitvoeren in een PSSession. Als u de para meter **ComputerName** gebruikt, wordt de verbinding door Power Shell beëindigd wanneer het taak object retourneert, en wordt de taak onderbroken.

Zie [About Jobs](about_Jobs.md) (Taken) voor meer informatie.

## <a name="can-i-run-an-interactive-session"></a>Kan ik een interactieve sessie uitvoeren?

Ja. Als u een interactieve sessie met een externe computer wilt starten, gebruikt u de `Enter-PSSession` cmdlet. In een interactieve sessie worden de opdrachten die u typt op de externe computer uitgevoerd, net alsof u ze rechtstreeks op de externe computer hebt getypt.

U kunt een interactieve sessie uitvoeren in een tijdelijke sessie (met behulp van de para meter **ComputerName** ) of in een PSSession (met behulp van de para meter **Session** ).
Als u een PSSession gebruikt, worden de gegevens van de vorige opdrachten door de PSSession bewaard en worden alle gegevens die zijn gegenereerd tijdens de interactieve sessie, bewaard voor gebruik in latere opdrachten.

Wanneer u de interactieve sessie beëindigt, blijft de PSSession open en beschikbaar voor gebruik.

Zie [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) en [Exit-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)voor meer informatie.

## <a name="must-i-delete-the-pssessions"></a>Moet ik de PSSessions verwijderen?

Ja. Een PSSession is een proces. Dit is een op zichzelf staande omgeving waarin geheugen en andere bronnen worden gebruikt, zelfs wanneer u deze niet gebruikt. Wanneer u klaar bent met een PSSession, verwijdert u deze. Als u meerdere PSSessions maakt, sluit u de bestanden die u niet gebruikt en behoudt u alleen de items die momenteel in gebruik zijn.

Als u PSSessions wilt verwijderen, gebruikt u de `Remove-PSSession` cmdlet. De PSSessions wordt verwijderd en alle resources die ze gebruiken, worden vrijgegeven.

U kunt ook de para meter **IdleTimeOut** van gebruiken `New-PSSessionOption` om een inactieve PSSession te sluiten na een interval dat u opgeeft. Zie [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor meer informatie.

Als u een PSSession-object opslaat in een variabele en vervolgens de PSSession verwijdert of een time-out krijgt, bevat de variabele nog steeds het object PSSession, maar de PSSession is niet actief en kan niet worden gebruikt of gerepareerd.

## <a name="are-all-sessions-and-pssessions-alike"></a>Zijn alle sessies en PSSessions hetzelfde?

Nee. Ontwikkel aars kunnen aangepaste sessies maken die alleen geselecteerde providers en cmdlets bevatten. Als een opdracht in één sessie werkt, maar niet in een andere, wordt de sessie mogelijk beperkt.

## <a name="see-also"></a>Zie ook

[about_Jobs](about_Jobs.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Afsluiten-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[Get-PSSession](xref:Microsoft.PowerShell.Core.Get-PSSession)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Remove-PSSession](xref:Microsoft.PowerShell.Core.Remove-PSSession)

