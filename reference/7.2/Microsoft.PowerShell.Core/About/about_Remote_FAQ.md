---
description: Bevat vragen en antwoorden over het uitvoeren van externe opdrachten in Power shell.
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_FAQ
ms.openlocfilehash: da3516697c58e3273538ed2ed93a7a54fcd9bb49
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705320"
---
# <a name="about-remote-faq"></a>Over externe Veelgestelde vragen

## <a name="short-description"></a>Korte beschrijving
Bevat vragen en antwoorden over het uitvoeren van externe opdrachten in Power shell.

## <a name="long-description"></a>Lange beschrijving

Wanneer u op afstand werkt, typt u opdrachten in Power shell op één computer (ook wel ' lokale computer ' genoemd), maar de opdrachten worden uitgevoerd op een andere computer (ook wel ' externe computer ' genoemd). De ervaring van het werken op afstand moet zo veel mogelijk rechtstreeks op de externe computer werken.

Opmerking: als u externe communicatie met Power shell wilt gebruiken, moet u de Remote computer configureren voor externe toegang. Zie [about_Remote_Requirements](about_Remote_Requirements.md)voor meer informatie.

### <a name="must-both-computers-have-powershell-installed"></a>Moeten op beide computers Power shell zijn geïnstalleerd?

Ja. Om op afstand te kunnen werken, moeten de lokale en externe computers Power shell, het Microsoft .NET Framework en het protocol Web Services for Management (WS-Management) hebben. Alle bestanden en andere bronnen die nodig zijn voor het uitvoeren van een bepaalde opdracht, moeten zich op de externe computer bevinden.

Computers met Windows Power Shell 3,0 en computers met Windows Power Shell 2,0 kunnen extern verbinding maken met elkaar en externe opdrachten uitvoeren.
Sommige functies, zoals de mogelijkheid om de verbinding met een sessie te verbreken en opnieuw verbinding te maken, werken echter alleen als Windows Power Shell 3,0 wordt uitgevoerd op beide computers.

U moet gemachtigd zijn om verbinding te maken met de externe computer, om Power shell uit te voeren en om toegang te krijgen tot gegevens archieven (zoals bestanden en mappen) en het REGI ster op de externe computer.

Zie [about_Remote_Requirements](about_Remote_Requirements.md)voor meer informatie.

### <a name="how-does-remoting-work"></a>Hoe werkt externe communicatie?

Wanneer u een externe opdracht verzendt, wordt de opdracht via het netwerk verzonden naar de Power shell-engine op de externe computer en wordt deze uitgevoerd in de Power shell-client op de externe computer. De resultaten van de opdracht worden teruggestuurd naar de lokale computer en worden weer gegeven in de Power shell-sessie op de lokale computer.

Als u de opdrachten wilt verzenden en de uitvoer wilt ontvangen, gebruikt Power shell het WS-Management protocol. Zie het [WS-Management-Protocol](/windows/win32/winrm/ws-management-protocol) in de Windows-documentatie voor meer informatie over het WS-Management-protocol.

Vanaf Windows Power Shell 3,0 worden externe sessies opgeslagen op de externe computer. Zo kunt u de verbinding met de sessie verbreken en opnieuw verbinding maken met een andere sessie of een andere computer zonder de opdrachten te onderbreken of de status verlies te verliezen.

### <a name="is-powershell-remoting-secure"></a>Is externe communicatie van Power shell veilig?

Wanneer u verbinding maakt met een externe computer, gebruikt het systeem de gebruikers naam en het wacht woord op de lokale computer of de referenties die u opgeeft in de opdracht om u aan te melden bij de externe computer. De referenties en de rest van de overdracht worden versleuteld.

Om extra beveiliging toe te voegen, kunt u de externe computer configureren voor het gebruik van Secure Sockets Layer (SSL) in plaats van HTTP om te Luis teren naar aanvragen van Windows Remote Management (WinRM). Vervolgens kunnen gebruikers de para meter **UseSSL** van de `Invoke-Command` `New-PSSession` cmdlets, en gebruiken `Enter-PSSession` bij het tot stand brengen van een verbinding. Deze optie maakt gebruik van het veiligere HTTPS-kanaal in plaats van HTTP.

### <a name="do-all-remote-commands-require-powershell-remoting"></a>Zijn voor alle externe opdrachten Power shell Remoting vereist?

Nee. Verschillende cmdlets hebben de para meter **ComputerName** waarmee u objecten van de externe computer kunt ophalen.

Deze cmdlets maken geen gebruik van externe communicatie met Power shell. U kunt ze dus op elke computer met Power shell gebruiken, zelfs als de computer niet is geconfigureerd voor externe communicatie met Power shell of als de computer niet voldoet aan de vereisten voor externe communicatie met Power shell.

Dit zijn onder andere de volgende cmdlets:

- `Get-Process`
- `Get-Service`
- `Get-WinEvent`
- `Get-EventLog`
- `Test-Connection`

Als u alle cmdlets wilt zoeken met de para meter **ComputerName** , typt u:

```powershell
Get-Help * -Parameter ComputerName
# or
Get-Command -ParameterName ComputerName
```

Als u wilt weten of de para meter **ComputerName** van een bepaalde cmdlet Power shell Remoting vereist, raadpleegt u de parameter beschrijving. Als u de parameter beschrijving wilt weer geven, typt u:

```powershell
Get-Help <cmdlet-name> -Parameter ComputerName
```

Bijvoorbeeld:

```powershell
Get-Help Get-Process -Parameter ComputerName
```

Voor alle andere opdrachten, gebruikt u de- `Invoke-Command` cmdlet.

### <a name="how-do-i-run-a-command-on-a-remote-computer"></a>Hoe kan ik een opdracht op een externe computer uit te voeren?

Als u een opdracht wilt uitvoeren op een externe computer, gebruikt u de `Invoke-Command` cmdlet.

Plaats de opdracht in accolades ( `{}` ) om een script blok te maken. Gebruik de para meter **script Block** van `Invoke-Command` om de opdracht op te geven.

U kunt de para meter **ComputerName** van gebruiken `Invoke-Command` om een externe computer op te geven. U kunt ook een permanente verbinding met een externe computer (een sessie) maken en vervolgens de **sessie** parameter van gebruiken `Invoke-Command` om de opdracht uit te voeren in de sessie.

Met de volgende opdrachten wordt `Get-Process` op afstand een opdracht uitgevoerd.

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-Process}

#  - OR -

Invoke-Command -Session $s -ScriptBlock {Get-Process}
```

Als u een externe opdracht wilt onderbreken, typt u <kbd>CTRL</kbd> + <kbd>C</kbd>. De aanvraag voor de onderbreking wordt door gegeven aan de externe computer, waar de externe opdracht wordt beëindigd.

Zie about_Remote en de Help-onderwerpen voor de cmdlets die ondersteuning bieden voor externe toegang voor meer informatie over externe opdrachten.

### <a name="can-i-just-telnet-into-a-remote-computer"></a>Kan ik gewoon Telnet op een externe computer?

U kunt de `Enter-PSSession` cmdlet gebruiken om een interactieve sessie met een externe computer te starten.

Typ het volgende bij de Power shell-prompt:

```powershell
Enter-PSSession <ComputerName>
```

De opdracht prompt wordt weer gegeven om aan te geven dat u verbinding hebt met de externe computer.

```
<ComputerName>\C:>
```

Nu worden de opdrachten die u typt op de externe computer uitgevoerd, net zoals u ze rechtstreeks op de externe computer hebt getypt.

Als u de interactieve sessie wilt beëindigen, typt u:

```powershell
Exit-PSSession
```

Een interactieve sessie is een permanente sessie die gebruikmaakt van het WS-Management-protocol. Het is niet hetzelfde als het gebruik van Telnet, maar het biedt een vergelijk bare ervaring.

Voor meer informatie raadpleegt u `Enter-PSSession`.

### <a name="can-i-create-a-persistent-connection"></a>Kan ik een permanente verbinding maken?

Ja. U kunt externe opdrachten uitvoeren door de naam van de externe computer, de NetBIOS-naam of het IP-adres op te geven. U kunt ook externe opdrachten uitvoeren door een Power shell-sessie (PSSession) op te geven die is verbonden met de externe computer.

Wanneer u de para meter **ComputerName** van `Invoke-Command` of gebruikt `Enter-PSSession` , brengt Power shell een tijdelijke verbinding tot stand. Power shell gebruikt de verbinding om alleen de huidige opdracht uit te voeren, waarna de verbinding wordt gesloten. Dit is een zeer efficiënte methode voor het uitvoeren van één opdracht of meerdere niet-gerelateerde opdrachten, zelfs op veel externe computers.

Wanneer u de `New-PSSession` -cmdlet gebruikt om een PSSession te maken, brengt Power shell een permanente verbinding tot stand voor de PSSession. Vervolgens kunt u meerdere opdrachten uitvoeren in de PSSession, waaronder opdrachten voor het delen van gegevens.

Normaal gesp roken maakt u een PSSession om een reeks gerelateerde opdrachten uit te voeren die gegevens delen. Anders is de tijdelijke verbinding die is gemaakt door de para meter **ComputerName** voldoende voor de meeste opdrachten.

Zie about_PSSessions voor meer informatie over sessies.

### <a name="can-i-run-commands-on-more-than-one-computer-at-a-time"></a>Kan ik opdrachten op meer dan één computer tegelijk uitvoeren?

Ja. De para meter **ComputerName** van de `Invoke-Command` cmdlet accepteert meerdere computer namen en de **sessie** parameter accepteert meerdere PSSessions.

Wanneer u een `Invoke-Command` opdracht uitvoert, voert Power shell de opdrachten uit op alle opgegeven computers of in alle opgegeven PSSessions.

In Power shell kunnen honderden gelijktijdige externe verbindingen worden beheerd. Het aantal externe opdrachten dat u kunt verzenden, kan echter worden beperkt door de bronnen van uw computer en de capaciteit om meerdere netwerk verbindingen tot stand te brengen en te onderhouden.

Zie het voor beeld in het Help-onderwerp voor meer informatie `Invoke-Command` .

### <a name="where-are-my-profiles"></a>Waar bevinden zich mijn profielen?

Power shell-profielen worden niet automatisch uitgevoerd in externe sessies, zodat de opdrachten die het profiel toevoegt, niet aanwezig zijn in de sessie. Daarnaast `$profile` wordt de automatische variabele niet ingevuld in externe sessies.

Als u een profiel in een sessie wilt uitvoeren, gebruikt u de `Invoke-Command` cmdlet.

Met de volgende opdracht wordt bijvoorbeeld het CurrentUserCurrentHost-profiel uitgevoerd van de lokale computer in de sessie in `$s` .

```
Invoke-Command -Session $s -FilePath $profile
```

Met de volgende opdracht wordt het CurrentUserCurrentHost-profiel uitgevoerd vanaf de externe computer in de sessie in `$s` . Omdat de `$profile` variabele niet is ingevuld, gebruikt de opdracht het expliciete pad naar het profiel.

```powershell
Invoke-Command -Session $s {
  . "$home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

Nadat u deze opdracht hebt uitgevoerd, zijn de opdrachten die door het profiel aan de sessie worden toegevoegd, beschikbaar in `$s` .

U kunt ook een opstart script in een sessie configuratie gebruiken om een profiel uit te voeren in elke externe sessie die gebruikmaakt van de sessie configuratie.

Zie about_Profiles voor meer informatie over Power shell-profielen.
Zie voor meer informatie over sessie configuraties `Register-PSSessionConfiguration` .

### <a name="how-does-throttling-work-on-remote-commands"></a>Hoe werkt het beperken op externe opdrachten?

Om u te helpen bij het beheren van de resources op uw lokale computer, bevat Power shell een functie beperking per opdracht waarmee u het aantal gelijktijdige externe verbindingen kunt beperken dat voor elke opdracht tot stand wordt gebracht.

De standaard instelling is 32 gelijktijdige verbindingen, maar u kunt de para meter **ThrottleLimit** van de cmdlets gebruiken om een aangepaste beperkings limiet voor bepaalde opdrachten in te stellen.

Wanneer u de beperkings functie gebruikt, moet u er rekening mee houden dat deze wordt toegepast op elke opdracht, niet op de hele sessie of op de computer. Als u opdrachten gelijktijdig uitvoert in verschillende sessies of PSSessions, is het aantal gelijktijdige verbindingen de som van de gelijktijdige verbindingen in alle sessies.

Als u cmdlets wilt zoeken met een **ThrottleLimit** -para meter, typt u:

```
Get-Help * -Parameter ThrottleLimit
-or-
Get-Command -ParameterName ThrottleLimit
```

### <a name="is-the-output-of-remote-commands-different-from-local-output"></a>Is de uitvoer van externe opdrachten afwijkend van de lokale uitvoer?

Wanneer u Power shell lokaal gebruikt, verzendt en ontvangt u ' live ' .NET Framework objecten; ' live ' objecten zijn objecten die zijn gekoppeld aan de werkelijke Program ma's of systeem onderdelen. Wanneer u de methoden aanroept of de eigenschappen van live objecten wijzigt, zijn de wijzigingen van invloed op het werkelijke programma of onderdeel. En wanneer de eigenschappen van een programma of onderdeel worden gewijzigd, worden de eigenschappen van het object die ze vertegenwoordigen ook gewijzigd.

Omdat de meeste live objecten echter niet via het netwerk kunnen worden verzonden, worden de meeste objecten die worden verzonden in externe opdrachten, dat wil zeggen, geconverteerd naar een reeks XML-gegevens elementen (beperkings taal in XML [CLiXML]) voor verzen ding.

Wanneer Power shell een geserialiseerd object ontvangt, wordt de XML geconverteerd naar een gedeserialiseerd object type. Het gedeserialiseerd object is een nauw keurige record van de eigenschappen van het programma of onderdeel op een eerder tijdstip, maar het is niet langer ' live ', dat wil zeggen dat het niet langer rechtstreeks aan het onderdeel is gekoppeld. De methoden worden verwijderd, omdat ze niet langer effectief zijn.

Normaal gesp roken kunt u ongeserialiseerde objecten gebruiken, net zoals u live objecten zou gebruiken, maar u moet op de hoogte zijn van de beperkingen. Daarnaast hebben de objecten die worden geretourneerd door de `Invoke-Command` cmdlet extra eigenschappen die u helpen de oorsprong van de opdracht te bepalen.

Sommige object typen, zoals DirectoryInfo-objecten en GUID'S, worden weer omgezet in live-objecten wanneer ze worden ontvangen. Voor deze objecten is geen speciale verwerking of opmaak vereist.

Zie [about_Remote_Output](about_Remote_Output.md)voor meer informatie over het interpreteren en Format teren van externe uitvoer.

### <a name="can-i-run-background-jobs-remotely"></a>Kan ik achtergrond taken op afstand uitvoeren?

Ja. Een Power shell-achtergrond taak is een Power shell-opdracht die asynchroon wordt uitgevoerd zonder interactie met de sessie. Wanneer u een achtergrond taak start, wordt de opdracht regel onmiddellijk geretourneerd en kunt u in de sessie blijven werken terwijl de taak wordt uitgevoerd, zelfs als deze gedurende een lange periode wordt uitgevoerd.

U kunt ook een achtergrond taak starten terwijl andere opdrachten worden uitgevoerd, omdat de achtergrond taken in een tijdelijke sessie altijd asynchroon worden uitgevoerd.

U kunt achtergrond taken uitvoeren op een lokale of externe computer. Standaard wordt een achtergrond taak uitgevoerd op de lokale computer. U kunt echter de para meter **AsJob** van de `Invoke-Command` cmdlet gebruiken om een externe opdracht als achtergrond taak uit te voeren. En u kunt gebruiken `Invoke-Command` om een `Start-Job` opdracht op afstand uit te voeren.

Zie [about_Jobs (about_Jobs. MD)] en [about_Remote_Jobs (about_Remote_Jobs. MD)] voor meer informatie over achtergrond taken in Power shell.

### <a name="can-i-run-windows-programs-on-a-remote-computer"></a>Kan ik Windows-Program ma's uitvoeren op een externe computer?

U kunt externe Power shell-opdrachten gebruiken voor het uitvoeren van Windows-Program ma's op externe computers. U kunt bijvoorbeeld uitvoeren `Shutdown.exe` of `Ipconfig.exe` op een externe computer.

U kunt echter geen Power shell-opdrachten gebruiken om de gebruikers interface voor elk programma op een externe computer te openen.

Wanneer u een Windows-programma op een externe computer start, wordt de opdracht niet voltooid en de Power shell-opdracht prompt wordt niet geretourneerd totdat het programma is voltooid of totdat u op <kbd>CTRL</kbd> + <kbd>C</kbd> drukt om de opdracht te onderbreken. Als u bijvoorbeeld het `Ipconfig.exe` programma op een externe computer uitvoert, wordt de opdracht prompt pas geretourneerd nadat het `Ipconfig.exe` is voltooid.

Als u externe opdrachten gebruikt om een programma met een gebruikers interface te starten, wordt het programma gestart, maar de gebruikers interface wordt niet weer gegeven. De Power shell-opdracht is niet voltooid en de opdracht prompt wordt pas weer gegeven nadat u het programma proces hebt gestopt of totdat u op <kbd>CTRL</kbd> + <kbd>C</kbd>drukt, waardoor de opdracht wordt onderbroken en het proces wordt gestopt.

Als u bijvoorbeeld een Power shell-opdracht gebruikt om uit te voeren `Notepad` op een externe computer, wordt het klad blok-proces op de externe computer gestart, maar de gebruikers interface van Klad blok wordt niet weer gegeven. Als u de opdracht wilt onderbreken en de opdracht prompt wilt herstellen, drukt u op <kbd>CTRL</kbd> + <kbd>C</kbd>.

### <a name="can-i-limit-the-commands-that-users-can-run-remotely-on-my-computer"></a>Kan ik de opdrachten beperken die gebruikers op afstand kunnen uitvoeren op mijn computer?

Ja. Elke externe sessie moet een van de sessie configuraties op de externe computer gebruiken. U kunt de sessie configuraties op uw computer (en de machtigingen voor die sessie configuraties) beheren om te bepalen wie opdrachten op afstand kan uitvoeren op uw computer en welke opdrachten ze kunnen uitvoeren.

Met een sessie configuratie configureert u de omgeving voor de sessie. U kunt de configuratie definiëren met behulp van een assembly die een nieuwe configuratie klasse implementeert of met behulp van een script dat in de sessie wordt uitgevoerd. De configuratie kan bepalen welke opdrachten beschikbaar zijn in de sessie.
En de configuratie kan instellingen bevatten voor het beveiligen van de computer, zoals instellingen die de hoeveelheid gegevens beperken die de sessie op afstand kan ontvangen in één object of opdracht. U kunt ook een security descriptor opgeven die de benodigde machtigingen voor het gebruik van de configuratie bepaalt.

De `Enable-PSRemoting` cmdlet maakt de standaard sessie configuraties op uw computer: micro soft. Power shell, micro soft. Power shell. workflow en micro soft. PowerShell32 (alleen 64-bits besturings systemen). `Enable-PSRemoting` Hiermee stelt u de security descriptor in voor de configuratie zodat alleen leden van de groep Administrators op uw computer deze kunnen gebruiken.

U kunt de-cmdlets voor sessie configuratie gebruiken om de standaard sessie configuraties te bewerken, nieuwe sessie configuraties te maken en de security descriptors van alle sessie configuraties te wijzigen.

Met ingang van Windows Power Shell 3,0 `New-PSSessionConfigurationFile` kunt u met de cmdlet aangepaste sessie configuraties maken met behulp van een tekst bestand. Het bestand bevat opties voor het instellen van de taal modus en voor het opgeven van de cmdlets en modules die beschikbaar zijn in sessies die gebruikmaken van de sessie configuratie.

Wanneer gebruikers de `Invoke-Command` -, `New-PSSession` -of- `Enter-PSSession` cmdlets gebruiken, kunnen ze de para meter **configuratiepad** gebruiken om de sessie configuratie aan te geven die wordt gebruikt voor de sessie. En ze kunnen de standaard configuratie wijzigen die hun sessies gebruiken door de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele in de sessie te wijzigen.

Zie de Help bij de cmdlets voor sessie configuratie voor meer informatie over sessie configuraties. Als u de cmdlets voor de sessie configuratie wilt vinden, typt u:

```powershell
Get-Command *PSSessionConfiguration
```

### <a name="what-are-fan-in-and-fan-out-configurations"></a>Wat zijn ventilatoren in en uitwaaieren van configuraties?

Het meest voorkomende scenario voor externe communicatie van Power shell met meerdere computers is de een-op-veel-configuratie, waarbij een lokale computer (de computer van de beheerder) Power shell-opdrachten op talloze externe computers uitvoert. Dit wordt het scenario ' uitwaaieren ' genoemd.

In sommige ondernemingen is de configuratie echter veel-op-één, waarbij veel client computers verbinding maken met één externe computer met Power shell, zoals een bestands server of een kiosk. Dit wordt ook wel de ' ventilator in ' configuratie genoemd.

Externe communicatie van Power shell ondersteunt zowel uitwaaier-als ventilator configuraties.

Voor de uitwaaiers configuratie gebruikt Power shell het protocol Web Services for Management (WS-Management) en de WinRM-service die ondersteuning biedt voor de micro soft-implementatie van WS-Management. Wanneer een lokale computer verbinding maakt met een externe computer, WS-Management een verbinding tot stand brengt en een invoeg toepassing voor Power shell gebruikt om het Power shell-hostproces (Wsmprovhost.exe) op de externe computer te starten. De gebruiker kan een alternatieve poort opgeven, een alternatieve sessie configuratie en andere functies om de externe verbinding aan te passen.

Power shell gebruikt IIS (Internet Information Services) voor het hosten van WS-Management om de Power shell-invoeg toepassing te laden en Power shell te starten om de configuratie van ' ventilator in ' te ondersteunen. In dit scenario, in plaats van elke Power shell-sessie in een afzonderlijk proces te starten, worden alle Power shell-sessies uitgevoerd in hetzelfde hostproces.

IIS-hosting en-ventilator in extern beheer wordt niet ondersteund in Windows XP of in Windows Server 2003.

In een configuratie van een ventilator kan de gebruiker een verbindings-URI en een HTTP-eind punt opgeven, met inbegrip van het Trans Port, de computer naam, de poort en de toepassings naam.
Alle aanvragen met een opgegeven toepassings naam worden door IIS doorgestuurd naar de toepassing. De standaard waarde is WS-Management, die Power shell kan hosten.

U kunt ook een verificatie mechanisme opgeven en omleiding van HTTP-en HTTPS-eind punten verbieden of toestaan.

### <a name="can-i-test-remoting-on-a-single-computer-not-in-a-domain"></a>Kan ik externe toegang testen op één computer die zich niet in een domein bevindt?

Ja. Externe communicatie met Power shell is ook beschikbaar wanneer de lokale computer zich niet in een domein bevindt. U kunt de externe functies gebruiken om verbinding te maken met sessies en om sessies op dezelfde computer. De functies werken hetzelfde als wanneer u verbinding maakt met een externe computer.

Als u externe opdrachten op een computer in een werk groep wilt uitvoeren, wijzigt u de volgende Windows-instellingen op de computer.

Let op: deze instellingen zijn van invloed op alle gebruikers op het systeem en ze kunnen het systeem kwetsbaarder maken voor een kwaadwillende aanval. Wees voorzichtig wanneer u deze wijzigingen aanbrengt.

- Windows Vista, Windows 7, Windows 8:

  Maak de volgende register vermelding en stel de waarde in op 1: LocalAccountTokenFilterPolicy in ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`

  U kunt de volgende Power shell-opdracht gebruiken om deze vermelding toe te voegen:

    ```powershell
    $parameters = @{
      Path='HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System'
      Name='LocalAccountTokenFilterPolicy'
      propertyType='DWord'
      Value=1
    }
    New-ItemProperty @parameters
    ```

- Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2:

  Er zijn geen wijzigingen nodig omdat de standaard instelling van het beleid ' netwerk toegang: delen en beveiligings model voor lokale accounts ' ' klassiek ' is. Controleer de instelling als deze is gewijzigd.

### <a name="can-i-run-remote-commands-on-a-computer-in-another-domain"></a>Kan ik externe opdrachten uitvoeren op een computer in een ander domein?

Ja. Normaal gesp roken worden de opdrachten zonder fouten uitgevoerd, maar u moet mogelijk de para meter **Credential** van `Invoke-Command` de `New-PSSession` cmdlets, of gebruiken `Enter-PSSession` om de referenties op te geven van een lid van de groep Administrators op de externe computer. Dit is soms ook vereist, zelfs wanneer de huidige gebruiker lid is van de groep Administrators op de lokale en externe computers.

Als de externe computer echter zich niet in een domein bevindt dat de lokale computer vertrouwt, kan de externe computer de referenties van de gebruiker mogelijk niet verifiëren.

Als u verificatie wilt inschakelen, gebruikt u de volgende opdracht om de externe computer toe te voegen aan de lijst met vertrouwde hosts voor de lokale computer in WinRM. Typ de opdracht achter de Power shell-prompt.

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value <Remote-computer-name>
```

Als u bijvoorbeeld de Server01-computer wilt toevoegen aan de lijst met vertrouwde hosts op de lokale computer, typt u de volgende opdracht achter de Power shell-prompt:

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value Server01
```

### <a name="does-powershell-support-remoting-over-ssh"></a>Ondersteunt Power shell externe toegang via SSH?

Ja. Zie voor meer informatie [Power shell Remoting via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## <a name="see-also"></a>Zie ook

[about_Remote](about_Remote.md)

[about_Profiles](about_Profiles.md)

[about_PSSessions](about_PSSessions.md)

[about_Remote_Jobs](about_Remote_Jobs.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
