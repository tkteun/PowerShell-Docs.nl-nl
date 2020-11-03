---
description: Hierin worden de systeem vereisten en configuratie vereisten beschreven voor het uitvoeren van externe opdrachten in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Requirements
ms.openlocfilehash: bcaed40082c694aa7271177e6c8040a06d02772b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252648"
---
# <a name="about-remote-requirements"></a>Over externe vereisten

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin worden de systeem vereisten en configuratie vereisten beschreven voor het uitvoeren van externe opdrachten in Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

In dit onderwerp worden de systeem vereisten, de gebruikers vereisten en de resource vereisten beschreven voor het tot stand brengen van externe verbindingen en het uitvoeren van externe opdrachten in Power shell. Het bevat ook instructies voor het configureren van externe bewerkingen.

Opmerking: veel cmdlets (inclusief de cmdlets Get-service, Get-process, Get-WMIObject, Get-EventLog en Get-WinEvent) krijgen objecten van externe computers met behulp van Microsoft .NET Framework-methoden om de objecten op te halen. Ze maken geen gebruik van de infra structuur voor externe communicatie van Power shell. De vereisten in dit document zijn niet van toepassing op deze cmdlets.

Lees de beschrijving van de para meter ComputerName van de cmdlets om de cmdlets te vinden die de para meter ComputerName hebben maar geen externe communicatie van Power shell gebruiken.

## <a name="system-requirements"></a>SYSTEEM VEREISTEN

Als u externe sessies wilt uitvoeren op Windows Power Shell 3,0, moeten de lokale en externe computers het volgende hebben:

- Windows Power Shell 3,0 of hoger
- Het Microsoft .NET Framework 4 of hoger
- Windows Remote Management 3,0

Als u externe sessies wilt uitvoeren op Windows Power Shell 2,0, moeten de lokale en externe computers het volgende hebben:

- Windows Power Shell 2,0 of hoger
- Het Microsoft .NET Framework 2,0 of hoger
- Windows Remote Management 2,0

U kunt externe sessies maken tussen computers met Windows Power Shell 2,0 en Windows Power Shell 3,0. Functies die alleen worden uitgevoerd op Windows Power Shell 3,0, zoals de mogelijkheid om de verbinding met sessies te verbreken en opnieuw te verbinden, zijn alleen beschikbaar als op beide computers Windows Power Shell 3,0 wordt uitgevoerd.

Als u het versie nummer van een geïnstalleerde versie van Power shell wilt weten, gebruikt u de $PSVersionTable automatische variabele.

Windows Remote Management (WinRM) 3,0 en Microsoft .NET Framework 4 zijn opgenomen in Windows 8, Windows Server 2012 en nieuwere versies van het Windows-besturings systeem. WinRM 3,0 is opgenomen in Windows Management Framework 3,0 voor oudere besturings systemen. Als de computer niet beschikt over de vereiste versie van WinRM of het Microsoft .NET Framework, mislukt de installatie.

## <a name="user-permissions"></a>GEBRUIKERSMACHTIGINGEN

Om externe sessies te maken en externe opdrachten uit te voeren, moet de huidige gebruiker lid zijn van de groep Administrators op de externe computer of moeten de referenties van een beheerder worden verstrekt. Anders mislukt de opdracht.

De vereiste machtigingen voor het maken van sessies en het uitvoeren van opdrachten op een externe computer (of in een externe sessie op de lokale computer) worden vastgesteld door de sessie configuratie (ook wel ' eind punt ' genoemd) op de externe computer waarmee de sessie verbinding maakt. Met name de security descriptor in de sessie configuratie bepaalt wie toegang heeft tot de sessie configuratie en wie deze kan gebruiken om verbinding te maken.

De security descriptors voor de standaard sessie configuraties, micro soft. Power shell, micro soft. PowerShell32 en micro soft. Power shell. workflow, geven alleen toegang tot leden van de groep Administrators.

Als de huidige gebruiker geen machtiging heeft voor het gebruik van de sessie configuratie, de opdracht voor het uitvoeren van een opdracht (die gebruikmaakt van een tijdelijke sessie) of het maken van een permanente sessie op de externe computer mislukt. De gebruiker kan de para meter configuratiepad van cmdlets gebruiken waarmee sessies worden gemaakt voor het selecteren van een andere sessie configuratie, als er een beschikbaar is.

Leden van de groep Administrators op een computer kunnen bepalen wie toestemming heeft om op afstand verbinding te maken met de computer door de security descriptors te wijzigen op de standaard sessie configuraties en door nieuwe sessie configuraties te maken met verschillende security descriptors.

Zie [about_Session_Configurations](about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

## <a name="windows-network-locations"></a>WINDOWS-NETWERK LOCATIES

Met ingang van Windows Power Shell 3,0 kan de cmdlet Enable-PSRemoting externe communicatie mogelijk maken op client-en server versies van Windows op particuliere, domein-en open bare netwerken.

Op Server versies van Windows met particuliere en domein netwerken maakt de Enable-PSRemoting-cmdlet firewall regels die onbeperkte externe toegang toestaan. Er wordt ook een firewall regel gemaakt voor open bare netwerken die alleen externe toegang vanaf computers in hetzelfde lokale subnet toestaan. Deze regel voor het lokale subnet firewall is standaard ingeschakeld op Server versies van Windows op open bare netwerken, maar Enable-PSRemoting past de regel opnieuw toe als deze is gewijzigd of verwijderd.

Op client versies van Windows met particuliere en domein netwerken maakt de Enable-PSRemoting-cmdlet standaard firewall regels waarmee onbeperkte externe toegang is toegestaan.

Als u externe toegang wilt inschakelen op client versies van Windows met open bare netwerken, gebruikt u de para meter SkipNetworkProfileCheck van de cmdlet Enable-PSRemoting. Er wordt een firewall regel gemaakt die alleen externe toegang toestaat vanaf computers in hetzelfde lokale subnet.

Als u de lokale subnet-beperking voor open bare netwerken wilt verwijderen en externe toegang vanaf alle locaties op client-en server versies van Windows wilt toestaan, gebruikt u de Set-NetFirewallRule cmdlet in de module netsecurity. Voer de volgende opdracht uit:

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

In Windows Power Shell 2,0, op Server versies van Windows, maakt Enable-PSRemoting firewall regels die externe toegang op alle netwerken toestaan.

In Windows Power Shell 2,0, op client versies van Windows, maakt Enable-PSRemoting firewall regels alleen op particuliere en domein netwerken. Als de netwerk locatie openbaar is, mislukt Enable-PSRemoting.

## <a name="run-as-administrator"></a>ALS ADMINISTRATOR UITVOEREN

Beheerders bevoegdheden zijn vereist voor de volgende externe bewerkingen:

- Een externe verbinding met de lokale computer tot stand brengen. Dit wordt meestal een ' loop back-scenario ' genoemd.

- De sessie configuraties op de lokale computer beheren.

- WS-Management instellingen op de lokale computer weer geven en wijzigen. Dit zijn de instellingen in het LocalHost-knoop punt van het WSMAN:-station.

Als u deze taken wilt uitvoeren, moet u Power shell starten met de optie als administrator uitvoeren, zelfs als u lid bent van de groep Administrators op de lokale computer.

In Windows 7 en in Windows Server 2008 R2 start u Windows Power shell met de optie als administrator uitvoeren:

1. Klik op Start, klik op alle Program Ma's, klik op accessoires en klik vervolgens op de map Windows Power shell.
2. Klik met de rechter muisknop op Windows Power shell en klik vervolgens op als administrator uitvoeren.

Windows Power shell starten met de optie als administrator uitvoeren:

1. Klik op Start, klik op alle Program Ma's en klik vervolgens op de map Windows Power shell.
2. Klik met de rechter muisknop op Windows Power shell en klik vervolgens op als administrator uitvoeren.

De optie als administrator uitvoeren is ook beschikbaar in andere Windows Verkenner-vermeldingen voor Windows Power shell, inclusief snelkoppelingen. Klik met de rechter muisknop op het item en klik vervolgens op als administrator uitvoeren.

Wanneer u Windows Power shell start vanuit een ander programma, zoals Cmd.exe, gebruikt u de optie als administrator uitvoeren om het programma te starten.

## <a name="how-to-configure-your-computer-for-remoting"></a>UW COMPUTER CONFIGUREREN VOOR EXTERNE COMMUNICATIE

Computers met alle ondersteunde versies van Windows kunnen externe verbindingen tot stand brengen met en externe opdrachten uitvoeren in Power shell zonder enige configuratie. Als u echter verbindingen wilt ontvangen en gebruikers wilt toestaan lokale en externe door de gebruiker beheerde Power shell-sessies ("PSSessions") te maken en opdrachten op de lokale computer uit te voeren, moet u externe communicatie van Power shell op de computer inschakelen.

Windows Server 2012 en nieuwere versies van Windows Server zijn standaard ingeschakeld voor externe communicatie met Power shell. Als de instellingen zijn gewijzigd, kunt u de standaard instellingen herstellen door de cmdlet Enable-PSRemoting uit te voeren.

In alle andere ondersteunde versies van Windows moet u de Enable-PSRemoting-cmdlet uitvoeren om externe communicatie van Power shell in te scha kelen.

De externe functies van Power shell worden ondersteund door de WinRM-service. Dit is de micro soft-implementatie van het protocol Web Services for Management (WS-Management). Wanneer u externe communicatie van Power shell inschakelt, wijzigt u de standaard configuratie van WS-Management en voegt u systeem configuratie toe waarmee gebruikers verbinding kunnen maken met WS-Management.

Power shell configureren voor het ontvangen van externe opdrachten:

1. Start Power shell met de optie als administrator uitvoeren.
2. Typ bij de opdrachtprompt: `Enable-PSRemoting`

Als u wilt controleren of externe toegang juist is geconfigureerd, voert u een test opdracht uit, zoals de volgende opdracht, waarmee een externe sessie op de lokale computer wordt gemaakt.

```powershell
New-PSSession
```

Als externe toegang op de juiste wijze is geconfigureerd, wordt door de opdracht een sessie op de lokale computer gemaakt en wordt een object geretourneerd dat de sessie vertegenwoordigt. De uitvoer moet er ongeveer uitzien als in de volgende voorbeeld uitvoer:

```output
Id Name        ComputerName    State    ConfigurationName
-- ----        ------------    -----    -----
1  Session1    localhost       Opened   Microsoft.PowerShell
```

Als de opdracht mislukt, raadpleegt u [about_Remote_Troubleshooting](about_Remote_Troubleshooting.md)voor hulp.

## <a name="understand-policies"></a>BELEID BEGRIJPEN

Wanneer u op afstand werkt, gebruikt u twee instanties van Power shell, een op de lokale computer en een op de externe computer. Als gevolg hiervan wordt uw werk beïnvloed door het Windows-beleid en de Power shell-beleids regels op de lokale en externe computers.

In het algemeen is het beleid op de lokale computer van kracht voordat u verbinding maakt en wanneer u de verbinding tot stand brengt. Wanneer u de verbinding gebruikt, zijn de beleids regels op de externe computer van kracht.

## <a name="basic-authentication-limitations-on-linux-and-macos"></a>Elementaire verificatie beperkingen voor Linux en macOS

Wanneer u verbinding maakt vanaf een Linux-of macOS-systeem naar Windows, wordt basis verificatie via HTTP niet ondersteund. Basis verificatie kan worden gebruikt via HTTPS door een certificaat te installeren op de doel server. Het certificaat moet een CN-naam hebben die overeenkomt met de hostnaam, is niet verlopen of ingetrokken. Een zelfondertekend certificaat kan worden gebruikt voor test doeleinden.

Zie [procedure: WINRM voor HTTPS configureren](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https) voor meer informatie.

De volgende opdracht wordt uitgevoerd vanaf een opdracht prompt met verhoogde bevoegdheid en configureert de HTTPS-listener in Windows met het geïnstalleerde certificaat.

```powershell
$hostinfo = '@{Hostname="<DNS_NAME>"; CertificateThumbprint="<THUMBPRINT>"}'
winrm create winrm/config/Listener?Address=*+Transport=HTTPS $hostinfo
```

Selecteer op de Linux-of macOS-zijde Basic voor verificatie en-UseSSl.

> Opmerking: basis verificatie kan niet worden gebruikt met domein accounts. Er is een lokaal account vereist en het account moet zich in de groep Administrators bevindt.

```powershell
# The specified local user must have administrator rights on the target machine.
# Specify the unqualified username.
$cred = Get-Credential username
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Basic -UseSSL
```

Een alternatief voor basis verificatie via HTTPS is onderhandeld. Dit resulteert in NTLM-verificatie tussen de client en de server en de payload wordt versleuteld via HTTP.

Het volgende illustreert het gebruik van onderhandelen met New-PSSession:

```powershell
# The specified user must have administrator rights on the target machine.
$cred = Get-Credential username@hostname
$session = New-PSSession -Computer <hostname> -Credential $cred `
  -Authentication Negotiate
```

> [!NOTE]
> Voor Windows Server is een extra register instelling vereist om beheerders, behalve de ingebouwde Administrator, in te scha kelen om verbinding te maken met behulp van NTLM.
> Raadpleeg de register instelling LocalAccountTokenFilterPolicy onder Negotiate-verificatie in [authenticatie voor externe verbindingen](/windows/win32/winrm/authentication-for-remote-connections)

## <a name="see-also"></a>ZIE OOK

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[about_PSSessions](about_PSSessions.md)

[Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

