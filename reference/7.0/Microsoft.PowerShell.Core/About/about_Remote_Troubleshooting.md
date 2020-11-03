---
description: Hierin wordt beschreven hoe u problemen met externe bewerkingen oplost in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_troubleshooting?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Troubleshooting
ms.openlocfilehash: acf4f86d8c20f5a8059be48623255696afabbefb
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/29/2020
ms.locfileid: "93253251"
---
# <a name="about-remote-troubleshooting"></a>Over externe probleem oplossing

## <a name="short-description"></a>Korte beschrijving
Hierin wordt beschreven hoe u problemen met externe bewerkingen oplost in Power shell.

## <a name="long-description"></a>Lange beschrijving

In deze sectie worden enkele van de problemen beschreven die kunnen optreden bij het gebruik van de externe functies van Power shell die zijn gebaseerd op WS-Management technologie en worden oplossingen voor deze problemen voorgesteld.

Zie [about_Remote](about_remote.md) en [about_Remote_Requirements](about_Remote_Requirements.md) voor meer informatie over de configuratie en het basis gebruik voordat u externe communicatie van Power shell kunt gebruiken. Daarnaast bevat de Help-onderwerpen voor elk van de externe cmdlets, met name de parameter beschrijvingen, nuttige informatie die is ontworpen om u te helpen bij het voor komen van problemen.

> [!NOTE]
> Als u de instellingen voor de lokale computer in het WSMan:-station wilt bekijken of wijzigen, inclusief wijzigingen in de sessie configuraties, vertrouwde hosts, poorten of listeners, start u Power shell met de optie **als administrator uitvoeren** .

## <a name="troubleshooting-permission-and-authentication-issues"></a>Problemen met machtigingen en verificatie oplossen

In deze sectie worden externe problemen besproken die betrekking hebben op gebruikers-en computer machtigingen en externe vereisten.

### <a name="how-to-run-as-administrator"></a>Als administrator uitvoeren

```
ERROR: Access is denied. You need to run this cmdlet from an elevated
process.
```

Windows Power shell starten met de optie **als administrator uitvoeren** om een externe sessie op de lokale computer te starten of instellingen te bekijken of te wijzigen voor de lokale computer in het WSMan:-station, inclusief wijzigingen in de sessie configuraties, vertrouwde hosts, poorten of listeners.

Windows Power shell starten met de optie **als administrator uitvoeren** :

- Klik met de rechter muisknop op een Windows Power shell-pictogram (of Windows PowerShell ISE) en klik vervolgens op **als administrator uitvoeren**.

  Windows Power shell starten met de optie **als administrator uitvoeren** in Windows 7 en windows server 2008 R2.

- Klik in de Windows-taak balk met de rechter muisknop op het Windows Power shell-pictogram en klik vervolgens op **als administrator uitvoeren**.

  In Windows Server 2008 R2 wordt het Windows Power shell-pictogram standaard vastgemaakt aan de taak balk.

### <a name="how-to-enable-remoting"></a>Externe toegang inschakelen

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to
listen for requests on the correct port and HTTP URL.
```

Er is geen configuratie vereist om een computer in staat te stellen externe opdrachten te verzenden.
Als u externe opdrachten wilt ontvangen, moet externe communicatie van Power shell op de computer zijn ingeschakeld. U kunt onder andere het starten van de WinRM-service, het opstart type voor de WinRM-service instellen op automatisch, listeners maken voor HTTP-en HTTPS-verbindingen en standaard sessie configuraties maken.

Windows Power shell Remoting is standaard ingeschakeld op Windows Server 2012 en nieuwere versies van Windows Server. Op alle andere systemen voert u de `Enable-PSRemoting` cmdlet uit om externe toegang in te scha kelen. U kunt ook de `Enable-PSRemoting` cmdlet uitvoeren om externe toegang tot Windows server 2012 en nieuwere releases van Windows Server opnieuw in te scha kelen als externe toegang is uitgeschakeld.

Als u een computer wilt configureren voor het ontvangen van externe opdrachten, gebruikt u de `Enable-PSRemoting` cmdlet. Met de volgende opdracht worden alle vereiste externe instellingen ingeschakeld, worden de sessie configuraties ingeschakeld en wordt de WinRM-service opnieuw gestart om de wijzigingen van kracht te laten worden.

`Enable-PSRemoting`

Als u alle gebruikers prompts wilt onderdrukken, typt u:

`Enable-PSRemoting -Force`

Zie [Enable-PSRemoting](xref:Microsoft.PowerShell.Core.Enable-PSRemoting)voor meer informatie.

### <a name="how-to-enable-remoting-in-an-enterprise"></a>Externe toegang inschakelen in een onderneming

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

Gebruik de cmdlet om één computer in staat te stellen externe Power shell-opdrachten te ontvangen en verbindingen te accepteren `Enable-PSRemoting` .

Als u externe toegang wilt inschakelen voor meerdere computers in een onderneming, kunt u de volgende schaal bare opties gebruiken.

- Als u listeners voor externe toegang wilt configureren, schakelt u het groeps beleid **automatische configuratie van listeners toestaan** in.

- Als u het opstart type van Windows Remote Management (WinRM) wilt instellen op automatisch op meerdere computers, gebruikt u de `Set-Service` cmdlet.

- Als u een firewall uitzondering wilt inschakelen, gebruikt u de Windows Firewall: groeps beleid voor **lokale poort uitzonderingen toestaan** .

### <a name="how-to-enable-listeners-by-using-a-group-policy"></a>Listeners inschakelen met behulp van een groeps beleid

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

Als u de listeners voor alle computers in een domein wilt configureren, schakelt u het beleid **automatische configuratie van listeners toestaan** in het volgende groepsbeleid pad:

```
Computer Configuration\Administrative Templates\Windows Components
    \Windows Remote Management (WinRM)\WinRM service
```

Schakel het beleid in en geef de IPv4-en IPv6-filters op. Joker tekens ( `*` ) zijn toegestaan.

### <a name="how-to-enable-remoting-on-public-networks"></a>Externe toegang inschakelen op open bare netwerken

```
ERROR:  Unable to check the status of the firewall
```

De `Enable-PSRemoting` cmdlet retourneert deze fout wanneer het lokale netwerk openbaar is en de para meter **SkipNetworkProfileCheck** niet in de opdracht wordt gebruikt.

Op Server versies van Windows is `Enable-PSRemoting` geslaagd op alle typen netwerk locaties. Er worden firewall regels gemaakt waarmee externe toegang tot privé-en domein netwerken (Home-en work) mogelijk wordt. Voor open bare netwerken maakt firewall regels die externe toegang vanaf hetzelfde lokale subnet toestaan.

Op client versies van Windows `Enable-PSRemoting` slaagt op particuliere en domein netwerken. Standaard mislukt het op open bare netwerken, maar als u de para meter **SkipNetworkProfileCheck** gebruikt, `Enable-PSRemoting` slaagt en maakt een firewall regel die verkeer van hetzelfde lokale subnet toestaat.

Voer de volgende opdracht uit om de beperking van het lokale subnet op open bare netwerken te verwijderen en externe toegang vanaf elke locatie toe te staan:

```powershell
Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any
```

De `Set-NetFirewallRule` cmdlet wordt geëxporteerd door de module netsecurity.

> [!NOTE]
> In Windows Power Shell 2,0 worden op computers met server versies van Windows `Enable-PSRemoting` firewall regels gemaakt waarmee externe toegang wordt toegestaan op particuliere, domein en open bare netwerken. Op computers met client versies van Windows `Enable-PSRemoting` maakt firewall regels die alleen externe toegang toestaan op particuliere en domein netwerken.

### <a name="how-to-enable-a-firewall-exception-by-using-a-group-policy"></a>Een firewall uitzondering inschakelen met behulp van een groeps beleid

```
ERROR:  ACCESS IS DENIED

or

ERROR: The connection to the remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

Als u een firewall-uitzonde ring voor alle computers in een domein wilt inschakelen, schakelt u het **Windows Firewall: beleid voor lokale poort uitzonderingen toestaan** in het volgende groepsbeleid pad:

```
Computer Configuration\Administrative Templates\Network
    \Network Connections\Windows Firewall\Domain Profile
```

Met dit beleid kunnen leden van de groep Administrators op de computer **Windows Firewall** in **configuratie scherm** gebruiken om een firewall uitzondering te maken voor de Windows Remote Management-service.

Als de configuratie van het beleid onjuist is, wordt mogelijk de volgende fout weer gegeven:

```
The client cannot connect to the destination specified in the request. Verify
that the service on the destination is running and is accepting requests.
```

Een configuratie fout in het beleid resulteert in een lege waarde voor de eigenschap **ListeningOn** . Gebruik de volgende opdracht om de waarde te controleren.

```powershell
PS> Get-WSManInstance winrm/config/listener -Enumerate

cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
Source                : GPO
lang                  : en-US
Address               : *
Transport             : HTTP
Port                  : 5985
Hostname              :
Enabled               : true
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {}
```

### <a name="how-to-set-the-startup-type-of-the-winrm-service"></a>Het opstart type van de WinRM-service instellen

```
ERROR:  ACCESS IS DENIED
```

Externe communicatie van Power shell is afhankelijk van de WinRM-service (Windows Remote Management).
De service moet worden uitgevoerd om externe opdrachten te ondersteunen.

In Server versies van Windows wordt het opstart type van de WinRM-service (Windows Remote Management) automatisch.

Op client versies van Windows is de WinRM-service echter standaard uitgeschakeld.

Als u het opstart type van een service op een externe computer wilt instellen, gebruikt u de `Set-Service` cmdlet.

Als u de opdracht op meerdere computers wilt uitvoeren, kunt u een tekst bestand of CSV-bestand van de computer namen maken.

Met de volgende opdrachten wordt bijvoorbeeld een lijst met computer namen uit het `Servers.txt` bestand opgehaald en wordt vervolgens het opstart type van de WinRM-service op alle computers ingesteld op **automatisch**.

```powershell
$servers = Get-Content servers.txt
Set-Service WinRM -ComputerName $servers -startuptype Automatic
```

Als u de resultaten wilt weer geven, gebruikt u de `Get-WMIObject` cmdlet met het **Win32_Service** -object. Zie [set-service](xref:Microsoft.PowerShell.Management.Set-Service)voor meer informatie.

### <a name="how-to-recreate-the-default-session-configurations"></a>De standaard sessie configuraties opnieuw maken

```
ERROR:  ACCESS IS DENIED
```

Om verbinding te maken met de lokale computer en opdrachten op afstand uit te voeren, moet de lokale computer sessie configuraties voor externe opdrachten bevatten.

Wanneer u gebruikt `Enable-PSRemoting` , worden standaard sessie configuraties gemaakt op de lokale computer. Externe gebruikers gebruiken deze sessie configuraties wanneer een externe opdracht de para meter **configuratiepad** niet bevat.

Als de standaard configuraties op een computer niet zijn geregistreerd of verwijderd, gebruikt `Enable-PSRemoting` u de cmdlet om ze opnieuw te maken. U kunt deze cmdlet herhaaldelijk gebruiken. Er worden geen fouten gegenereerd als een functie al is geconfigureerd.

Als u de standaard sessie configuraties wijzigt en de oorspronkelijke standaard sessie configuraties wilt herstellen, gebruikt u de `Unregister-PSSessionConfiguration` cmdlet om de gewijzigde sessie configuraties te verwijderen en gebruikt u vervolgens de `Enable-PSRemoting` cmdlet om ze te herstellen.
`Enable-PSRemoting` de bestaande sessie configuraties worden niet gewijzigd.

> [!NOTE]
> Wanneer `Enable-PSRemoting` de standaard sessie configuratie herstelt, worden er geen expliciete Security descriptors gemaakt voor de configuraties. In plaats daarvan nemen de configuraties de security descriptor van de RootSDDL over, die standaard veilig is.

Als u de RootSDDL-security descriptor wilt zien, typt u:

```powershell
Get-Item wsman:\localhost\Service\RootSDDL
```

Als u de RootSDDL wilt wijzigen, gebruikt u de `Set-Item` cmdlet in het station WSMan:. Als u de security descriptor van een sessie configuratie wilt wijzigen, gebruikt u de `Set-PSSessionConfiguration` cmdlet met de para meters **SecurityDescriptorSDDL** of **ShowSecurityDescriptorUI** .

Zie het Help-onderwerp voor de WSMan-provider (' Get-Help WSMan ') voor meer informatie over WSMan: drive.

### <a name="how-to-provide-administrator-credentials"></a>Beheerders referenties opgeven

```
ERROR:  ACCESS IS DENIED
```

Als u een PSSession wilt maken of opdrachten wilt uitvoeren op een externe computer, moet de huidige gebruiker standaard lid zijn van de groep Administrators op de externe computer. Referenties zijn soms vereist, zelfs wanneer de huidige gebruiker is aangemeld met een account dat lid is van de groep Administrators.

Als de huidige gebruiker lid is van de groep Administrators op de externe computer of u de referenties van een lid van de groep Administrators kunt opgeven, gebruikt u de para meter **Credential** van de `New-PSSession` - `Enter-PSSession` of- `Invoke-Command` cmdlets om extern verbinding te maken.

De volgende opdracht geeft bijvoorbeeld de referenties van een beheerder.

```powershell
Invoke-Command -ComputerName Server01 -Credential Domain01\Admin01
```

Zie [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession) of [invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)voor meer informatie over de para meter **Credential** .

### <a name="how-to-enable-remoting-for-non-administrative-users"></a>Externe toegang inschakelen voor gebruikers die geen beheerder zijn

```
ERROR:  ACCESS IS DENIED
```

Om een PSSession te maken of een opdracht uit te voeren op een externe computer, moet de gebruiker gemachtigd zijn om de sessie configuraties te gebruiken op de externe computer.

Standaard zijn alleen leden van de groep Administrators op een computer gemachtigd om de standaard sessie configuraties te gebruiken. Daarom kunnen alleen leden van de groep Administrators op afstand verbinding maken met de computer.

Om andere gebruikers toe te staan verbinding te maken met de lokale computer, geeft u de gebruiker de bevoegdheid om de standaard sessie configuraties op de lokale computer uit te voeren.

Met de volgende opdracht wordt een eigenschappen venster geopend waarmee u de security descriptor van de standaard configuratie van de micro soft. Power shell-sessie op de lokale computer kunt wijzigen.

```powershell
Set-PSSessionConfiguration Microsoft.PowerShell -ShowSecurityDescriptorUI
```

Zie [about_Session_Configurations](about_Session_Configurations.md)voor meer informatie.

### <a name="how-to-enable-remoting-for-administrators-in-other-domains"></a>Externe toegang inschakelen voor beheerders in andere domeinen

```
ERROR:  ACCESS IS DENIED
```

Wanneer een gebruiker in een ander domein lid is van de groep Administrators op de lokale computer, kan de gebruiker niet extern verbinding maken met de lokale computer met Administrator bevoegdheden. Externe verbindingen van andere domeinen worden standaard alleen uitgevoerd met standaard gebruikers privilege-tokens.

U kunt echter de register vermelding **LocalAccountTokenFilterPolicy** gebruiken om het standaard gedrag te wijzigen en externe gebruikers die lid zijn van de groep Administrators toe te staan om met beheerders bevoegdheden uit te voeren.

> [!CAUTION]
> Met de **LocalAccountTokenFilterPolicy** -vermelding worden externe beperkingen van Gebruikersaccountbeheer (UAC) uitgeschakeld voor alle gebruikers van alle betrokken computers. Houd rekening met de implicaties van deze instelling zorgvuldig voordat u het beleid wijzigt.

Als u het beleid wilt wijzigen, gebruikt u de volgende opdracht om de waarde van de register vermelding **LocalAccountTokenFilterPolicy** in te stellen op 1.

```powershell
New-ItemProperty -Name LocalAccountTokenFilterPolicy `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System `
  -PropertyType DWord -Value 1
```

### <a name="how-to-use-an-ip-address-in-a-remote-command"></a>Een IP-adres gebruiken in een externe opdracht

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

De para meter **ComputerName** van de `New-PSSession` - `Enter-PSSession` en `Invoke-Command` -cmdlets accepteert een IP-adres als een geldige waarde. Omdat Kerberos-verificatie echter geen ondersteuning biedt voor IP-adressen, wordt NTLM-verificatie standaard gebruikt wanneer u een IP-adres opgeeft.

Als NTLM-verificatie wordt gebruikt, is de volgende procedure vereist voor externe toegang.

1. Configureer de computer voor HTTPS-Trans Port of Voeg de IP-adressen van de externe computers toe aan de lijst TrustedHosts op de lokale computer.

1. Gebruik de para meter **Credential** in alle externe opdrachten.

   Dit is ook vereist wanneer u de referenties van de huidige gebruiker verzendt.

### <a name="how-to-connect-remotely-from-a-workgroup-based-computer"></a>Extern verbinding maken vanaf een computer op basis van een werk groep

```
ERROR: The WinRM client cannot process the request. If the authentication
scheme is different from Kerberos, or if the client computer is not joined to a
domain, then HTTPS transport must be used or the destination machine must be
added to the TrustedHosts configuration setting.
```

Als de lokale computer zich niet in een domein bevindt, is de volgende procedure vereist voor externe toegang.

1. Configureer de computer voor HTTPS-Trans Port of Voeg de namen van de externe computers toe aan de lijst TrustedHosts op de lokale computer.

1. Controleer of er een wacht woord is ingesteld op de computer die is gebaseerd op werk groep. Als er geen wacht woord is ingesteld of als de wachtwoord waarde leeg is, kunt u geen externe opdrachten uitvoeren.

   Als u wacht woord voor uw gebruikers account wilt instellen, gebruikt u gebruikers accounts in het configuratie scherm.

1. Gebruik de para meter **Credential** in alle externe opdrachten.

   Dit is ook vereist wanneer u de referenties van de huidige gebruiker verzendt.

### <a name="how-to-add-a-computer-to-the-trusted-hosts-list"></a>Een computer toevoegen aan de lijst met vertrouwde hosts

Het TrustedHosts-item kan een door komma's gescheiden lijst met computer namen, IP-adressen en volledig gekwalificeerde domein namen bevatten. Joker tekens zijn toegestaan.

Als u de lijst met vertrouwde hosts wilt weer geven of wijzigen, gebruikt u het station WSMan:. Het TrustedHost-item bevindt zich in het `WSMan:\localhost\Client` knoop punt.

Alleen leden van de groep Administrators op de computer zijn gemachtigd om de lijst met vertrouwde hosts op de computer te wijzigen.

Let op: de waarde die u voor het TrustedHosts-item instelt, is van invloed op alle gebruikers van de computer.

Als u de lijst met vertrouwde hosts wilt weer geven, gebruikt u de volgende opdracht:

```powershell
Get-Item wsman:\localhost\Client\TrustedHosts
```

U kunt ook de `Set-Location` cmdlet (alias = cd) gebruiken om te navigeren naar de locatie WSMan: station. Bijvoorbeeld:

```powershell
cd WSMan:\localhost\Client; dir
```

Als u alle computers aan de lijst met vertrouwde hosts wilt toevoegen, gebruikt u de volgende opdracht, waarmee de waarde * (alle) wordt geplaatst in de computer naam

```powershell
Set-Item wsman:localhost\client\trustedhosts -Value *
```

U kunt ook een Joker teken ( `*` ) gebruiken om alle computers in een bepaald domein toe te voegen aan de lijst met vertrouwde hosts. Met de volgende opdracht worden alle computers in het fabrikam-domein bijvoorbeeld toegevoegd aan de lijst met vertrouwde hosts.

```powershell
Set-Item wsman:localhost\client\trustedhosts *.fabrikam.com
```

Gebruik de volgende opdracht indeling om de namen van bepaalde computers toe te voegen aan de lijst met vertrouwde hosts:

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <ComputerName>
```

waarbij elke waarde `<ComputerName>` de volgende notatie moet hebben:

```
<Computer>.<Domain>.<Company>.<top-level-domain>
```

Bijvoorbeeld:

```powershell
$server = 'Server01.Domain01.Fabrikam.com'
Set-Item wsman:\localhost\Client\TrustedHosts -Value $server
```

Als u een computer naam wilt toevoegen aan een bestaande lijst met vertrouwde hosts, slaat u eerst de huidige waarde op in een variabele en stelt u de waarde in op een door komma's gescheiden lijst met de huidige en nieuwe waarden.

Als u bijvoorbeeld de Server01-computer aan een bestaande lijst met vertrouwde hosts wilt toevoegen, gebruikt u de volgende opdracht:

```powershell
$curValue = (Get-Item wsman:\localhost\Client\TrustedHosts).value

Set-Item wsman:\localhost\Client\TrustedHosts -Value `
  "$curValue, Server01.Domain01.Fabrikam.com"
```

Als u de IP-adressen van bepaalde computers wilt toevoegen aan de lijst met vertrouwde hosts, gebruikt u de volgende opdracht indeling:

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value <IP Address>
```

Bijvoorbeeld:

```powershell
Set-Item wsman:\localhost\Client\TrustedHosts -Value 172.16.0.0
```

Als u een computer wilt toevoegen aan de lijst TrustedHosts van een externe computer, gebruikt u de `Connect-WSMan` cmdlet om een knoop punt voor de externe computer toe te voegen aan het WSMan:-station op de lokale computer. Gebruik vervolgens een `Set-Item` opdracht om de computer toe te voegen.

`Connect-WSMan`Zie [Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)voor meer informatie over de cmdlet.

## <a name="troubleshooting-computer-configuration-issues"></a>Problemen met computer configuratie oplossen

In deze sectie worden externe problemen besproken die betrekking hebben op bepaalde configuraties van een computer, domein of onderneming.

### <a name="how-to-configure-remoting-on-alternate-ports"></a>Externe toegang configureren op alternatieve poorten

```
ERROR: The connection to the specified remote host was refused. Verify that the
WS-Management service is running on the remote host and configured to listen
for requests on the correct port and HTTP URL.
```

Externe communicatie van Power shell gebruikt poort 80 voor HTTP-Trans Port. De standaard poort wordt gebruikt wanneer de gebruiker niet de para meters **ConnectionURI** of **poort** opgeeft in een externe opdracht.

Als u de standaard poort die Power shell gebruikt, wilt wijzigen, gebruikt u `Set-Item` cmdlet in het station WSMan: om de poort waarde in het knoop punt listener te wijzigen.

Met de volgende opdracht wordt bijvoorbeeld de standaard poort gewijzigd in 8080.

```powershell
Set-Item wsman:\localhost\listener\listener*\port -Value 8080
```

### <a name="how-to-configure-remoting-with-a-proxy-server"></a>Externe toegang configureren met een proxy server

```
ERROR: The client cannot connect to the destination specified in the request.
Verify that the service on the destination is running and is accepting
requests.
```

Omdat externe communicatie van Power shell gebruikmaakt van het HTTP-protocol, is dit van invloed op de HTTP-proxy-instellingen. In ondernemingen met proxy servers hebben gebruikers geen rechtstreekse toegang tot een externe Power shell-computer.

U kunt dit probleem oplossen met behulp van opties voor proxy-instellingen in uw externe opdracht. De volgende instellingen zijn beschikbaar:

- ProxyAccessType
- ProxyAuthentication
- ProxyCredential

Als u deze opties voor een bepaalde opdracht wilt instellen, gebruikt u de volgende procedure:

1. Gebruik de para meters **ProxyAccessType** , **ProxyAuthentication** en **ProxyCredential** van de `New-PSSessionOption` cmdlet om een sessie optie object te maken met de proxy-instellingen voor uw onderneming. Sla het optie object op als variabele.

1. Gebruik de variabele die het optie object bevat als waarde voor de para meter **SessionOption** van een `New-PSSession` , `Enter-PSSession` , of `Invoke-Command` opdracht.

Met de volgende opdracht wordt bijvoorbeeld een sessie optie object gemaakt met proxy sessie opties en wordt het object vervolgens gebruikt om een externe sessie te maken.

```powershell
$SessionOption = New-PSSessionOption -ProxyAccessType IEConfig `
-ProxyAuthentication Negotiate -ProxyCredential Domain01\User01

New-PSSession -ConnectionURI https://www.fabrikam.com
```

`New-PSSessionOption`Zie [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor meer informatie over de cmdlet.

Als u deze opties wilt instellen voor alle externe opdrachten in de huidige sessie, gebruikt u het optie object dat `New-PSSessionOption` maakt in de waarde van de `$PSSessionOption` Voorkeurs variabele. Zie [about_Preference_Variables](about_Preference_Variables.md)voor meer informatie.

Als u deze opties wilt instellen voor alle externe opdrachten alle Power shell-sessies op de lokale computer, voegt `$PSSessionOption` u de voorkeurs variabele toe aan uw Power shell-profiel. Zie [about_Profiles](about_Profiles.md)voor meer informatie over Power shell-profielen.

### <a name="how-to-detect-a-32-bit-session-on-a-64-bit-computer"></a>Een 32-bits sessie op een 64-bits computer detecteren

```
ERROR: The term "<tool-Name>" is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

Als op de externe computer een 64-bits versie van Windows wordt uitgevoerd en de externe opdracht een 32-bits sessie configuratie gebruikt, zoals micro soft. PowerShell32, laadt Windows Remote Management (WinRM) een WOW64-proces en worden alle verwijzingen naar de Directory automatisch door Windows omgeleid naar `$env:Windir\System32` de `$env:Windir\SysWOW64` map.

Als u probeert hulpprogram ma's in de map System32 te gebruiken die geen tegen Hangers hebben in de map SysWow64, zoals `Defrag.exe` , kunnen de hulpprogram ma's niet worden gevonden in de map.

Als u de processor architectuur wilt vinden die in de sessie wordt gebruikt, gebruikt u de waarde van de omgevings variabele **PROCESSOR_ARCHITECTURE** . Met de volgende opdracht wordt de processor architectuur van de sessie in de `$s` variabele gevonden.

```powershell
$s = New-PSSession -ComputerName Server01 -ConfigurationName CustomShell
Invoke-Command -Session $s {$env:PROCESSOR_ARCHITECTURE}
```

```Output
x86
```

Zie [about_Session_Configurations](about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

## <a name="troubleshooting-policy-and-preference-issues"></a>Problemen met beleid en voor keuren oplossen

In deze sectie worden externe problemen besproken die betrekking hebben op beleids regels en voor keuren die zijn ingesteld op de lokale en externe computers.

### <a name="how-to-change-the-execution-policy-for-import-pssession-and-import-module"></a>Het uitvoerings beleid voor Import-PSSession en Import-Module wijzigen

```
ERROR: Import-Module: File <filename> cannot be loaded because the
execution of scripts is disabled on this system.
```

De `Import-PSSession` `Export-PSSession` cmdlets en maken modules met niet-ondertekende script bestanden en indelings bestanden.

Als u de modules wilt importeren die zijn gemaakt met deze cmdlets, `Import-PSSession` kunt u `Import-Module` het uitvoerings beleid in de huidige sessie niet beperken of alles ondertekend. Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie over het uitvoeren van Power shell-uitvoerings beleid.

Als u de modules wilt importeren zonder het uitvoerings beleid voor de lokale computer die is ingesteld in het REGI ster te wijzigen, gebruikt u de para meter **bereik** van `Set-ExecutionPolicy` om een minder beperkend uitvoerings beleid in te stellen voor één proces.

Met de volgende opdracht wordt bijvoorbeeld een proces met het `RemoteSigned` uitvoerings beleid gestart. De wijziging van het uitvoerings beleid is alleen van invloed op het huidige proces en wijzigt de Power shell **ExecutionPolicy** -register instelling niet.

```powershell
Set-ExecutionPolicy -Scope process -ExecutionPolicy RemoteSigned
```

U kunt ook de para meter **ExecutionPolicy** van gebruiken `PowerShell.exe` om één sessie met een minder beperkend uitvoerings beleid te starten.

```powershell
PowerShell.exe -ExecutionPolicy RemoteSigned
```

Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie over uitvoerings beleid. Typ `PowerShell.exe -?` voor meer informatie.

### <a name="how-to-set-and-change-quotas"></a>Quota's instellen en wijzigen

```
ERROR: The total data received from the remote client exceeded allowed
maximum.
```

U kunt quota's gebruiken om de lokale computer en de externe computer te beschermen tegen overmatig gebruik van bronnen, zowel per ongeluk als kwaad aardigheid.

De volgende quota's zijn beschikbaar in de basis configuratie.

- De WSMan-provider (WSMan:) biedt verschillende quota-instellingen, zoals de instellingen **MaxEnvelopeSizeKB** en **MaxProviderRequests** in het `WSMan:<ComputerName>` knoop punt en de instellingen **MaxConcurrentOperations** , **MaxConcurrentOperationsPerUser** en **MaxConnections** in het `WSMan:<ComputerName>\Service` knoop punt.

- U kunt de lokale computer beveiligen met behulp van de **MaximumReceivedDataSizePerCommand** -en **MaximumReceivedObjectSize** -para meters van de `New-PSSessionOption` cmdlet en de `$PSSessionOption` Voorkeurs variabele.

- U kunt de externe computer beveiligen door beperkingen toe te voegen aan de sessie configuraties, zoals met behulp van de para meters **MaximumReceivedDataSizePerCommandMB** en **MaximumReceivedObjectSizeMB** van de `Register-PSSessionConfiguration` cmdlet.

Wanneer quota conflicteren met een opdracht, genereert Power shell een fout.

Wijzig de externe opdracht om te voldoen aan het quotum om de fout op te lossen. U kunt ook de bron van het quotum bepalen en vervolgens het quotum verhogen zodat de opdracht kan worden voltooid.

Met de volgende opdracht wordt bijvoorbeeld het quotum voor de object grootte in de micro soft. Power shell-sessie configuratie op de externe computer verhoogd van 10 MB (de standaard waarde) tot 11 MB.

```powershell
Set-PSSessionConfiguration -Name microsoft.PowerShell `
  -MaximumReceivedObjectSizeMB 11 -Force
```

Zie voor meer informatie over de `New-PSSessionOption` cmdlet `New-PSSessionOption` .

Zie [about_WSMan_Provider](../../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)voor meer informatie over de WS-Management quota's.

### <a name="how-to-resolve-timeout-errors"></a>Time-outfouten oplossen

```
ERROR: The WS-Management service cannot complete the operation within
the time specified in OperationTimeout.
```

U kunt time-outs gebruiken om de lokale computer en de externe computer te beschermen tegen overmatig gebruik van bronnen, zowel per ongeluk als kwaad aardig. Wanneer time-outs zijn ingesteld op zowel de lokale als de externe computer, gebruikt Power shell de kortste time-outinstellingen.

De volgende time-outs zijn beschikbaar in de basis configuratie.

- De WSMan-provider (WSMan:) voorziet in verschillende time-outinstellingen aan de client zijde en aan de service zijde, zoals de instelling **MaxTimeoutms** in het `WSMan:<ComputerName>` knoop punt en de **EnumerationTimeoutms** -en **MaxPacketRetrievalTimeSeconds** -instellingen in het `WSMan:<ComputerName>\Service` knoop punt.

- U kunt de lokale computer beveiligen door gebruik te maken van de para meters **CancelTimeout** , **IdleTimeout** , **opentime out** en **OperationTimeout** van de `New-PSSessionOption` cmdlet en de `$PSSessionOption` Voorkeurs variabele.

- U kunt de externe computer ook beveiligen door time-outwaarden programmatisch in te stellen in de sessie configuratie voor de sessie.

Als een time-outwaarde een bewerking niet kan worden voltooid, wordt de bewerking door Power Shell beëindigd en wordt er een fout gegenereerd.

Om de fout op te lossen, wijzigt u de opdracht in volt ooien binnen de time-outinterval of bepaalt u de bron van de time-outlimiet en verhoogt u de time-outinterval zodat de opdracht kan worden voltooid.

De volgende opdrachten gebruiken bijvoorbeeld de `New-PSSessionOption` cmdlet om een sessie optie object te maken met een **OperationTimeout** -waarde van 4 minuten (in MS) en vervolgens het object Session Option gebruiken om een externe sessie te maken.

```powershell
$pso = New-PSSessionoption -OperationTimeout 240000

New-PSSession -ComputerName Server01 -sessionOption $pso
```

Zie het Help-onderwerp voor de WSMan-provider (type) voor meer informatie over de WS-Management-time-outs `Get-Help WSMan` .

`New-PSSessionOption`Zie [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor meer informatie over de cmdlet.

## <a name="troubleshooting-unresponsive-behavior"></a>Oplossen van problemen met niet-reagerende gedrag

In deze sectie worden externe problemen beschreven die voor komen dat een opdracht wordt voltooid en de retour nering van de Power shell-prompt wordt voor komen of vertraagd.

### <a name="how-to-interrupt-a-command"></a>Een opdracht onderbreken

Sommige systeem eigen Windows-Program ma's, zoals Program ma's met een gebruikers interface, console toepassingen die invoer vragen en console toepassingen die gebruikmaken van de Win32-console-API, werken niet goed in de externe Power shell-host.

Wanneer u deze Program ma's gebruikt, ziet u mogelijk onverwacht gedrag, zoals geen uitvoer, gedeeltelijke uitvoer of een externe opdracht die niet is voltooid.

Als u een programma wilt beëindigen dat niet meer reageert, typt u <kbd>CTRL</kbd> + <kbd>C</kbd>. Als u fouten wilt weer geven die mogelijk zijn gerapporteerd, typt u `$error` de lokale host en de externe sessie.

## <a name="how-to-recover-from-an-operation-failure"></a>Herstellen na een mislukte bewerking

```
ERROR: The I/O operation has been aborted because of either a thread exit
or an  application request.
```

Deze fout wordt geretourneerd wanneer een bewerking wordt beëindigd voordat deze is voltooid.
Normaal gesp roken treedt er een fout op wanneer de WinRM-service wordt gestopt of opnieuw wordt gestart terwijl andere WinRM-bewerkingen worden uitgevoerd.

Om dit probleem op te lossen, controleert u of de WinRM-service wordt uitgevoerd en voert u de opdracht opnieuw uit.

1. Start Power shell met de optie **als administrator uitvoeren** .
1. Voer de volgende opdracht uit:

   `Start-Service WinRM`

1. Voer de opdracht die de fout heeft gegenereerd opnieuw uit.

## <a name="linux-and-macos-limitations"></a>Beperkingen voor Linux en macOS

### <a name="authentication"></a>Verificatie

Alleen basis verificatie werkt in macOS en poging tot het gebruik van andere verificatie schema's kan leiden tot een storing in het proces.

Raadpleeg de [Omi-verificatie](https://github.com/PowerShell/psl-omi-provider#connecting-from-linux-to-windows) -instructies.

## <a name="see-also"></a>ZIE OOK

[Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)

[Exporteren-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession)

[Import-module](xref:Microsoft.PowerShell.Core.Import-Module)

[about_Remote](about_Remote.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_Variables](about_Remote_Variables.md)
