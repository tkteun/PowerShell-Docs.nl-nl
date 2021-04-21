---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSession
ms.openlocfilehash: 1af271c164b4478bf57132046affb4276e541108
ms.sourcegitcommit: b10731301412afd4111743b85da95e8c25583533
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/20/2021
ms.locfileid: "107756304"
---
# New-PSSession

## Synopsis
Hiermee maakt u een permanente verbinding met een lokale of externe computer.

## Syntax

### ComputerName (standaard)

```
New-PSSession [[-ComputerName] <String[]>] [-Credential <PSCredential>] [-Name <String[]>]
 [-EnableNetworkAccess] [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-ThrottleLimit <Int32>] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### Uri

```
New-PSSession [-Credential <PSCredential>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ConfigurationName <String>] [-ThrottleLimit <Int32>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### VMId

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 [-VMId] <Guid[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### VMName

```
New-PSSession -Credential <PSCredential> [-Name <String[]>] [-ConfigurationName <String>]
 -VMName <String[]> [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### Sessie

```
New-PSSession [[-Session] <PSSession[]>] [-Name <String[]>] [-EnableNetworkAccess]
 [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### ContainerId

```
New-PSSession [-Name <String[]>] [-ConfigurationName <String>] -ContainerId <String[]>
 [-RunAsAdministrator] [-ThrottleLimit <Int32>] [<CommonParameters>]
```

### UseWindowsPowerShellParameterSet

```
New-PSSession [-Name <String[]>] [-UseWindowsPowerShell] [<CommonParameters>]
```

### SSHHost

```
New-PSSession [-Name <String[]>] [-Port <Int32>] [-HostName] <String[]> [-UserName <String>] [-KeyFilePath <String>]
[-SSHTransport] [-Subsystem <String>] [-ConnectingTimeout <int>] [<CommonParameters>]
```

### SSHHostHashParam

```
New-PSSession [-Name <String[]>] -SSHConnection <Hashtable[]> [<CommonParameters>]
```

## Description

De `New-PSSession` cmdlet maakt een PowerShell-sessie **(PSSession)** op een lokale of externe computer. Wanneer u een **PSSession maakt,** maakt PowerShell een permanente verbinding met de externe computer.

Gebruik een **PSSession om** meerdere opdrachten uit te voeren die gegevens delen, zoals een functie of de waarde van een variabele. Gebruik de cmdlet om opdrachten uit te voeren in een **PSSession.** `Invoke-Command` Als u **pssession wilt gebruiken om** rechtstreeks met een externe computer te communiceren, gebruikt u de `Enter-PSSession` cmdlet . Zie voor meer informatie [about_PSSessions](about/about_PSSessions.md).

U kunt opdrachten uitvoeren op een externe computer zonder een **PSSession te maken** met behulp van de **ComputerName-parameters** van of `Enter-PSSession` `Invoke-Command` . Wanneer u de **parameter ComputerName** gebruikt, maakt PowerShell een tijdelijke verbinding die wordt gebruikt voor de opdracht en vervolgens wordt gesloten.

Vanaf PowerShell 6.0 kunt u Secure Shell (SSH) gebruiken om een verbinding tot stand te brengen en een sessie te maken op een externe computer, als SSH beschikbaar is op de lokale computer en de externe computer is geconfigureerd met een PowerShell SSH-eindpunt. Het voordeel van een externe PowerShell-sessie op basis van SSH is dat deze kan werken op meerdere platforms (Windows, Linux, macOS). Voor SSH-sessies gebruikt u de parameter **HostName** of **SSHConnection** om de externe computer en relevante verbindingsgegevens op te geven. Zie Voor meer informatie over het instellen van SSH-remoting voor [PowerShell Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)

> [!NOTE]
> Wanneer u WSMan gebruikt voor remoting vanaf een Linux- of macOS-client met een HTTPS-eindpunt waarop het servercertificaat niet wordt vertrouwd (bijvoorbeeld een zelf-ondertekend certificaat). U moet een met `PSSessionOption` en verstrekken om de verbinding tot stand te `-SkipCACheck` `-SkipCNCheck` brengen. Dit doet u alleen als u zich in een omgeving waar u zeker van het servercertificaat en de netwerkverbinding met het doelsysteem kunt zijn.

## Voorbeelden

### Voorbeeld 1: Een sessie maken op de lokale computer

```powershell
$s = New-PSSession
```

Met deze opdracht maakt u een **nieuwe PSSession** op de lokale computer en slaat u **de PSSession** op in de `$s` variabele .

U kunt deze **PSSession nu gebruiken om** opdrachten uit te voeren op de lokale computer.

### Voorbeeld 2: Een sessie maken op een externe computer

```powershell
$Server01 = New-PSSession -ComputerName Server01
```

Met deze opdracht maakt u een **nieuwe PSSession** op de computer Server01 en slaat u deze op in de `$Server01` variabele .

Wanneer u meerdere **PSSession-objecten maakt,** wijst u deze toe aan variabelen met nuttige namen. Dit helpt u bij het beheren van **de PSSession-objecten** in volgende opdrachten.

### Voorbeeld 3: Sessies maken op meerdere computers

```powershell
$s1, $s2, $s3 = New-PSSession -ComputerName Server01,Server02,Server03
```

Met deze opdracht maakt u **drie PSSession-objecten,** één op elk van de computers die zijn opgegeven door de **ComputerName** parameter.

De opdracht gebruikt de toewijzingsoperator (=) om de nieuwe **PSSession-objecten** toe te wijzen aan variabelen: `$s1` , , `$s2` `$s3` . De Server01 **PSSession** wordt toegewezen aan `$s1` , de Server02 **PSSession** aan `$s2` en de Server03 **PSSession** aan `$s3` .

Wanneer u meerdere objecten toewijst aan een reeks variabelen, wijst PowerShell elk object toe aan een variabele in de reeks. Als er meer objecten dan variabelen zijn, worden alle resterende objecten toegewezen aan de laatste variabele. Als er meer variabelen dan objecten zijn, zijn de resterende variabelen leeg (null).

### Voorbeeld 4: Een sessie maken met een opgegeven poort

```powershell
New-PSSession -ComputerName Server01 -Port 8081 -UseSSL -ConfigurationName E12
```

Met deze opdracht maakt u een nieuwe **PSSession** op de computer Server01 die verbinding maakt met serverpoort 8081 en het SSL-protocol gebruikt. De nieuwe **PSSession maakt gebruik** van een alternatieve sessieconfiguratie met de naam E12.

Voordat u de poort instelt, moet u de WinRM-listener op de externe computer configureren om te luisteren op poort 8081. Zie de beschrijving van de parameter **Port voor meer** informatie.

### Voorbeeld 5: een sessie maken op basis van een bestaande sessie

```powershell
New-PSSession -Session $s -Credential Domain01\User01
```

Met deze opdracht maakt **u een PSSession** met dezelfde eigenschappen als een bestaande **PSSession**. U kunt deze opdrachtindeling gebruiken wanneer de resources van een bestaande **PSSession** zijn uitgeput en een nieuwe **PSSession** nodig is om een deel van de vraag te offloaden.

De opdracht gebruikt de **sessieparameter** van `New-PSSession` om de **PSSession op te geven die** is opgeslagen in de variabele `$s` . Deze gebruikt de referenties van de gebruiker Domain1\Admin01 om de opdracht uit te voeren.

### Voorbeeld 6: Een sessie maken met een globaal bereik in een ander domein

```powershell
$global:s = New-PSSession -ComputerName Server1.Domain44.Corpnet.Fabrikam.com -Credential Domain01\Admin01
```

In dit voorbeeld ziet u hoe u een **PSSession** maakt met een globaal bereik op een computer in een ander domein.

**PSSession-objecten die zijn** gemaakt op de opdrachtregel, worden standaard gemaakt met een lokaal bereik en **PSSession-objecten** die in een script zijn gemaakt, hebben een scriptbereik.

Als u een **PSSession wilt** maken met een globaal bereik, maakt u een nieuwe **PSSession** en sla u de **PSSession** op in een variabele die wordt gecast naar een globaal bereik. In dit geval wordt de `$s` variabele gecast naar een globaal bereik.

De opdracht gebruikt de **ComputerName** parameter opgeven voor de externe computer. Omdat de computer zich in een ander domein dan het gebruikersaccount, wordt de volledige naam van de computer samen met de referenties van de gebruiker opgegeven.

### Voorbeeld 7: Sessies maken voor veel computers

```powershell
$rs = Get-Content C:\Test\Servers.txt | New-PSSession -ThrottleLimit 50
```

Met deze opdracht maakt u **een PSSession** op elk van de 200 computers die worden vermeld in het Servers.txt-bestand en wordt de resulterende **PSSession** opgeslagen in de `$rs` variabele . De **PSSession-objecten** hebben een limiet van 50.

U kunt deze opdrachtindeling gebruiken wanneer de namen van computers worden opgeslagen in een database, spreadsheet, tekstbestand of andere tekstindeling.

### Voorbeeld 8: Een sessie maken met behulp van een URI

```powershell
$s = New-PSSession -URI http://Server01:91/NewSession -Credential Domain01\User01
```

Met deze opdracht maakt **u een PSSession** op de computer Server01 en slaat u deze op in de `$s` variabele . Hierbij de **URI parameter** opgeven voor het transportprotocol, de externe computer, de poort en een alternatieve sessieconfiguratie. Ook wordt de **referentie** parameter opgeven voor een gebruikersaccount dat is machtiging voor het maken van een sessie op de externe computer.

### Voorbeeld 9: Een achtergrond job uitvoeren in een reeks sessies

```powershell
$s = New-PSSession -ComputerName (Get-Content Servers.txt) -Credential Domain01\Admin01 -ThrottleLimit 16
Invoke-Command -Session $s -ScriptBlock {Get-Process PowerShell} -AsJob
```

Met deze opdrachten maakt u een set **PSSession-objecten** en voert u vervolgens een achtergrond-taak uit in elk van de **PSSession-objecten.**

Met de eerste opdracht maakt u een **nieuwe PSSession** op elk van de computers die worden vermeld in het Servers.txt bestand. De `New-PSSession` cmdlet wordt gebruikt om de **PSSession te maken.** De waarde van de **ComputerName** parameter is een opdracht die gebruikmaakt van de cmdlet om op te halen van de lijst met `Get-Content` computernamen Servers.txt bestand.

De opdracht gebruikt de **referentie** parameter voor het maken van de **PSSession-objecten** die de machtiging van een domeinbeheerder en gebruikt de **ThrottleLimit** parameter voor het beperken van de opdracht tot 16 gelijktijdige verbindingen. De opdracht slaat de **PSSession-objecten** op in de `$s` variabele .

De tweede opdracht maakt gebruik van de **parameter AsJob** van de cmdlet om een achtergrondopdracht te starten die een opdracht in elk van de `Invoke-Command` `Get-Process PowerShell` **PSSession-objecten** in wordt `$s` uitgevoerd.

Zie PowerShell-achtergrondtaken voor meer [informatie about_Jobs](About/about_Jobs.md) en [about_Remote_Jobs.](About/about_Remote_Jobs.md)

### Voorbeeld 10: Een sessie voor een computer maken met behulp van de URI

```powershell
New-PSSession -ConnectionURI https://management.exchangelabs.com/Management
```

Met deze opdracht maakt u **een PSSession-objecten** die verbinding maken met een computer die is opgegeven door een URI in plaats van een computernaam.

### Voorbeeld 11: Een sessieoptie maken

```powershell
$so = New-PSSessionOption -SkipCACheck
New-PSSession -ConnectionUri https://management.exchangelabs.com/Management -SessionOption $so -Credential Server01\Admin01
```

In dit voorbeeld ziet u hoe u een sessieoptieobject maakt en de parameter **SessionOption** gebruikt.

De eerste opdracht maakt gebruik van `New-PSSessionOption` de cmdlet om een sessieoptie te maken. Hiermee slaat u het **resulterende SessionOption-object** op in de `$so` variabele .

De tweede opdracht maakt gebruik van de optie in een nieuwe sessie. De opdracht maakt gebruik van `New-PSSession` de cmdlet om een nieuwe sessie te maken. De waarde van de parameter SessionOption is het **object SessionOption** in de `$so` variabele .

### Voorbeeld 12: Een sessie maken met SSH

```powershell
New-PSSession -HostName UserA@LinuxServer01
```

In dit voorbeeld ziet u hoe u een nieuwe **PSSession maakt** met behulp van Secure Shell (SSH). Als SSH is geconfigureerd op de externe computer om te vragen om wachtwoorden, krijgt u een wachtwoordprompt. Anders moet u gebruikersverificatie op basis van een SSH-sleutel gebruiken.

### Voorbeeld 13: een sessie maken met SSH en de poort- en gebruikersverificatiesleutel opgeven

```powershell
New-PSSession -HostName UserA@LinuxServer01:22 -KeyFilePath c:\<path>\userAKey_rsa
```

In dit voorbeeld ziet u hoe u een **PSSession maakt** met behulp van Secure Shell (SSH). De parameter **Port** wordt gebruikt om de poort op te geven die moet worden gebruikt en de parameter **KeyFilePath** om een RSA-sleutel op te geven die wordt gebruikt om de gebruiker op de externe computer te identificeren en te verifiëren.

### Voorbeeld 14: Meerdere sessies maken met SSH

```powershell
$sshConnections = @{ HostName="WinServer1"; UserName="domain\userA"; KeyFilePath="c:\users\UserA\id_rsa" }, @{ HostName="UserB@LinuxServer5"; KeyFilePath="c:\UserB\<path>\id_rsa" }
New-PSSession -SSHConnection $sshConnections
```

In dit voorbeeld ziet u hoe u meerdere sessies maakt met behulp van Secure Shell (SSH) en de **parameterset SSHConnection.** De **parameter SSHConnection** maakt gebruik van een matrix met hashtabellen die verbindingsgegevens voor elke sessie bevatten. Houd er rekening mee dat voor dit voorbeeld SSH is geconfigureerd voor de doel-externe computers ter ondersteuning van gebruikersverificatie op basis van sleutels.

## Parameters

### -AllowRedirection

Geeft aan dat deze cmdlet omleiding van deze verbinding naar een alternatieve Uniform Resource Identifier (URI) toestaat.

Wanneer u de **parameter ConnectionURI** gebruikt, kan de externe bestemming een instructie retourneren om om te leiden naar een andere URI. PowerShell leidt verbindingen standaard niet om, maar u kunt deze parameter gebruiken om de verbinding om te leiden.

U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de **optiewaarde maximumConnectionRedirectionCount-sessie** te wijzigen. Gebruik de **parameter MaximumRedirection** van de cmdlet of stel de eigenschap `New-PSSessionOption` **MaximumConnectionRedirectionCount** van de **$PSSessionOption** voorkeursvariabele in. De standaardwaarde is 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Hiermee geeft u het toepassingsnaamsegment van de verbindings-URI op. Gebruik deze parameter om de naam van de toepassing op te geven wanneer u de **parameter ConnectionURI** niet gebruikt in de opdracht .

De standaardwaarde is de waarde van de `$PSSessionApplicationName` voorkeursvariabele op de lokale computer. Als deze voorkeursvariabele niet is gedefinieerd, is de standaardwaarde WSMAN. Deze waarde is geschikt voor de meeste toepassingen. Zie voor meer informatie [about_Preference_Variables](About/about_Preference_Variables.md).

De WinRM-service gebruikt de toepassingsnaam om een listener te selecteren om de verbindingsaanvraag te verwerken.
De waarde van deze parameter moet overeenkomen met de waarde van de **eigenschap URLPrefix** van een listener op de externe computer.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Verificatie

Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.
De aanvaardbare waarden voor deze parameter zijn:

- Standaard
- Basic
- Credssp
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

De standaardwaarde is Standaard.

Zie [AuthenticationMechanism Enumeration](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze parameter.

> [!CAUTION]
> CredSSP-verificatie (Credential Security Support Provider), waarbij de gebruikersreferenties worden doorgegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie op meer dan één resource is vereist, zoals toegang tot een externe netwerk share. Dit mechanisme verhoogt het beveiligingsrisico van de externe bewerking. Als de externe computer is gecompromitteerd, kunnen de referenties die worden doorgegeven aan de computer worden gebruikt voor het beheer van de netwerksessie.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Hiermee geeft u het digitale openbare-sleutelcertificaat (X509) op van een gebruikersaccount dat is machtigingen heeft om deze actie uit te voeren. Voer de vingerafdruk van het certificaat in.

Certificaten worden gebruikt in verificatie op basis van clientcertificaten. Ze kunnen alleen worden toe te staan aan lokale gebruikersaccounts; ze werken niet met domeinaccounts.

Als u een certificaat wilt verkrijgen, gebruikt u `Get-Item` de opdracht of in het `Get-ChildItem` PowerShell-station Certificaat: .

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u een matrix met namen van computers. Met deze cmdlet maakt u een permanente verbinding **(PSSession)** met de opgegeven computer. Als u meerdere computernamen op te geven, `New-PSSession` maakt meerdere **PSSession-objecten,** één voor elke computer. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een volledig gekwalificeerde domeinnaam van een of meer externe computers. Als u de lokale computer wilt opgeven, typt u de computernaam, localhost of een punt (.). Wanneer de computer zich in een ander domein dan de gebruiker, de volledig gekwalificeerde domeinnaam is vereist. U kunt een computernaam ook tussen aanhalingstekens doorseen naar `New-PSSession` .

Als u een IP-adres wilt gebruiken in de waarde van de parameter **ComputerName,** moet de opdracht de parameter **Credential** bevatten. De computer moet ook worden geconfigureerd voor HTTPS-transport of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer. Zie voor instructies voor het toevoegen van een computernaam aan de lijst TrustedHosts "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](about/about_Remote_Troubleshooting.md).

Als u de lokale computer wilt opnemen in de waarde van de parameter **ComputerName,** start Windows PowerShell met de optie Als administrator uitvoeren.

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ConfigurationName

Hiermee geeft u de sessieconfiguratie op die wordt gebruikt voor de nieuwe **PSSession**.

Voer een configuratienaam of de volledig gekwalificeerde resource-URI in voor een sessieconfiguratie. Als u alleen de configuratienaam opgeeft, wordt de volgende schema-URI toegevoegd: `http://schemas.microsoft.com/PowerShell` .

De sessieconfiguratie voor een sessie bevindt zich op de externe computer. Als de opgegeven sessieconfiguratie niet bestaat op de externe computer, mislukt de opdracht.

De standaardwaarde is de waarde van de `$PSSessionConfigurationName` voorkeursvariabele op de lokale computer. Als deze voorkeursvariabele niet is ingesteld, is de standaardwaarde Microsoft.PowerShell. Zie voor meer informatie [about_Preference_Variables](About/about_Preference_Variables.md).

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectingTimeout

Hiermee geeft u de hoeveelheid tijd in milliseconden op die is toegestaan voor het voltooien van de eerste SSH-verbinding. Als de verbinding niet binnen de opgegeven tijd is voltooid, wordt er een fout geretourneerd.

Deze parameter is geïntroduceerd in PowerShell 7.2

```yaml
Type: System.Int32
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: unlimited
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionUri

Hiermee geeft u een URI op die het verbindings-eindpunt voor de sessie definieert. De URI moet volledig gekwalificeerd zijn. De indeling van deze tekenreeks is als volgt:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

De standaardwaarde is als volgt:

`http://localhost:5985/WSMAN`

Als u geen **ConnectionURI** opgeeft, kunt u de parameters **UseSSL,** **ComputerName,** **Port** en **ApplicationName** gebruiken om de **ConnectionURI-waarden op te** geven.

Geldige waarden voor het segment Transport van de URI zijn HTTP en HTTPS. Als u een verbindings-URI opgeeft met een Transport-segment, maar geen poort opgeeft, wordt de sessie gemaakt met standaardenpoorten: 80 voor HTTP en 443 voor HTTPS. Geef poort 5985 voor HTTP of 5986 voor HTTPS op als u de standaardpoorten wilt gebruiken voor het op andere locatie gebruiken van PowerShell.

Als de doelcomputer de verbinding omleiden naar een andere URI, PowerShell voorkomt de omleiding, tenzij u de **parameter AllowRedirection** in de opdracht.

```yaml
Type: System.Uri[]
Parameter Sets: Uri
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

Hiermee geeft u een matrix met ID's van containers op. Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven containers. Gebruik de `docker ps` opdracht om een lijst met container-ID's op te halen. Zie de Help voor de opdracht [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikersaccount op dat is machtigingen heeft om deze actie uit te voeren. Standaard is dit de huidige gebruiker.

Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een **PSCredential-object** in dat door de `Get-Credential` cmdlet is gegenereerd. Als u een gebruikersnaam typt, wordt u gevraagd het wachtwoord in te voeren.

Referenties worden opgeslagen in een [PSCredential-object](/dotnet/api/system.management.automation.pscredential) en het wachtwoord wordt opgeslagen als een [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie How secure is **SecureString?** (Hoe veilig is SecureString?) voor meer informatie over [SecureString-gegevensbeveiliging.](/dotnet/api/system.security.securestring#how-secure-is-securestring)

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Geeft aan dat deze cmdlet een interactief beveiliging token toevoegt aan loopback-sessies. Met het interactieve token kunt u opdrachten uitvoeren in de loopback-sessie die gegevens van andere computers op halen. U kunt bijvoorbeeld een opdracht uitvoeren in de sessie die XML-bestanden kopieert van een externe computer naar de lokale computer.

Een loopback-sessie is **een PSSession** die afkomstig is van en eindigt op dezelfde computer. Als u een loopbacksessie wilt maken, laat u de parameter **ComputerName** weg of stelt u de waarde ervan in op punt (.), localhost of de naam van de lokale computer.

Standaard maakt deze cmdlet loopback-sessies met behulp van een netwerk-token, die mogelijk onvoldoende machtigingen biedt voor verificatie bij externe computers.

De **parameter EnableNetworkAccess** is alleen van kracht in loopback-sessies. Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, slaagt de opdracht, maar de parameter wordt genegeerd.

U kunt ook externe toegang inschakelen in een loopback-sessie  met behulp van de CredSSP-waarde van de verificatieparameter, die de sessiereferenties delegeert naar andere computers.

Om de computer te beschermen tegen schadelijke toegang, kunnen losgekoppelde loopback-sessies met interactieve tokens, die zijn gemaakt met de parameter **EnableNetworkAccess,** alleen opnieuw worden verbonden vanaf de computer waarop de sessie is gemaakt. Niet-verbonden sessies die gebruikmaken van CredSSP-verificatie kunnen opnieuw worden verbonden vanaf andere computers. Voor meer informatie raadpleegt u `Disconnect-PSSession`.

Deze parameter is geïntroduceerd in PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri, Session
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

Hiermee geeft u een matrix met computernamen op voor een SSH-verbinding (Secure Shell). Dit is vergelijkbaar met de ComputerName parameter behalve dat de verbinding met de externe computer wordt gemaakt met behulp van SSH in plaats van Windows WinRM.

Deze parameter is geïntroduceerd in PowerShell 6.0.

```yaml
Type: System.String[]
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -KeyFilePath

Hiermee geeft u een sleutelbestandspad op dat wordt gebruikt door Secure Shell (SSH) om een gebruiker op een externe computer te verifiëren.

Met SSH kan gebruikersverificatie worden uitgevoerd via persoonlijke/openbare sleutels als alternatief voor basisverificatie van wachtwoorden. Als de externe computer is geconfigureerd voor sleutelverificatie, kan deze parameter worden gebruikt om de sleutel op te geven waarmee de gebruiker wordt geïdentificeerd.

Deze parameter is geïntroduceerd in PowerShell 6.0.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een gebruiksvriendelijke naam op voor **de PSSession**.

U kunt de naam gebruiken om naar de **PSSession te** verwijzen wanneer u andere cmdlets gebruikt, zoals `Get-PSSession` en `Enter-PSSession` . De naam is niet vereist om uniek te zijn voor de computer of de huidige sessie.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Hiermee geeft u de netwerkpoort op de externe computer die wordt gebruikt voor deze verbinding. Als u verbinding wilt maken met een externe computer, moet de externe computer luisteren op de poort die de verbinding gebruikt. De standaardpoorten zijn 5985, de WinRM-poort voor HTTP, en 5986, de WinRM-poort voor HTTPS.

Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om naar die poort te luisteren. Gebruik de volgende opdrachten om de listener te configureren:

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

Gebruik de parameter **Poort alleen als** dat nodig is. De poortinstelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poortinstelling kan verhinderen dat de opdracht op alle computers wordt uitgevoerd.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunAsAdministrator

Geeft aan dat **pssession wordt uitgevoerd** als beheerder.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessie

Hiermee geeft u een matrix **van PSSession-objecten** op die deze cmdlet gebruikt als model voor de nieuwe **PSSession**. Met deze parameter maakt u **nieuwe PSSession-objecten** met dezelfde eigenschappen als de opgegeven **PSSession-objecten.**

Voer een variabele in die de **PSSession-objecten** bevat of een opdracht die de **PSSession-objecten** maakt of op haalt, zoals een `New-PSSession` - of `Get-PSSession` -opdracht.

De resulterende **PSSession-objecten** hebben dezelfde computernaam, toepassingsnaam, verbindings-URI, poort, configuratienaam, beperkingslimiet en SSL-waarde (Secure Sockets Layer), maar ze hebben een andere weergavenaam, id en exemplaar-id (GUID).

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Hiermee geeft u geavanceerde opties voor de sessie. Voer een **SessionOption-object** in, zoals een object dat u maakt met behulp van de cmdlet of een hash-tabel waarin de sleutels sessieoptienamen zijn en de waarden `New-PSSessionOption` sessieoptiewaarden zijn.

De standaardwaarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` voorkeursvariabele als deze is ingesteld. Anders worden de standaardwaarden ingesteld door opties die zijn ingesteld in de sessieconfiguratie.

De waarden van de sessieoptie hebben voorrang op de standaardwaarden voor sessies die zijn ingesteld in de `$PSSessionOption` voorkeursvariabele en in de sessieconfiguratie. Ze hebben echter geen voorrang op maximumwaarden, quota of limieten die zijn ingesteld in de sessieconfiguratie.

Zie voor een beschrijving van de sessieopties die de standaardwaarden `New-PSSessionOption` bevatten. Zie voor meer informatie `$PSSessionOption` over de voorkeursvariabele [about_Preference_Variables.](About/about_Preference_Variables.md) Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHConnection

Deze parameter maakt gebruik van een matrix met hashtabels waarbij elke hashtabel een of meer verbindingsparameters bevat die nodig zijn om een SSH-verbinding (Secure Shell) tot stand te brengen (HostName, Port, UserName, KeyFilePath).

De hashtabelverbindingsparameters zijn hetzelfde als die zijn gedefinieerd voor de **parameterset HostName.**

De **parameter SSHConnection** is handig voor het maken van meerdere sessies waarbij elke sessie andere verbindingsgegevens vereist.

Deze parameter is geïntroduceerd in PowerShell 6.0.

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: SSHHostHashParam
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SSHTransport

Geeft aan dat de externe verbinding tot stand is gebracht met behulp van Secure Shell (SSH).

PowerShell maakt standaard gebruik van Windows WinRM om verbinding te maken met een externe computer. Deze schakelknop dwingt PowerShell om de parameterset HostName te gebruiken voor het tot stand brengen van een externe SSH-verbinding.

Deze parameter is geïntroduceerd in PowerShell 6.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Hiermee geeft u het maximum aantal gelijktijdige verbindingen die kunnen worden ingesteld voor het uitvoeren van deze opdracht.
Als u deze parameter weglaten of een waarde van 0 (nul), de standaardwaarde, 32, wordt gebruikt.

De beperkingslimiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, Uri, VMId, VMName, Session, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GebruikersNaam

Hiermee geeft u de gebruikersnaam voor het account dat wordt gebruikt voor het maken van een sessie op de externe computer. De verificatiemethode voor gebruikers is afhankelijk van hoe Secure Shell (SSH) is geconfigureerd op de externe computer.

Als SSH is geconfigureerd voor basisverificatie van wachtwoorden, wordt u gevraagd om het gebruikerswachtwoord.

Als SSH is geconfigureerd voor gebruikersverificatie op basis van sleutels, kan er een pad naar een sleutelbestand worden opgegeven via de parameter KeyFilePath en wordt er geen wachtwoordprompt uitgevoerd. Houd er rekening mee dat als het clientgebruikerssleutelbestand zich op een bekende SSH-locatie bevindt, de parameter KeyFilePath niet nodig is voor verificatie op basis van sleutels en dat gebruikersverificatie automatisch wordt uitgevoerd op basis van de gebruikersnaam. Zie SSH-documentatie over op sleutels gebaseerde gebruikersverificatie voor meer informatie.

Dit is geen vereiste parameter. Als er geen userName parameter is opgegeven, wordt de huidige gebruikersnaam voor het aanmelden gebruikt voor de verbinding.

Deze parameter is geïntroduceerd in PowerShell 6.0.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Geeft aan dat deze cmdlet het SSL-protocol gebruikt om een verbinding met de externe computer tot stand te brengen.
Standaard wordt SSL niet gebruikt.

WS-Management versleutelt alle PowerShell-inhoud die via het netwerk wordt verzonden. De **parameter UseSSL** biedt een extra beveiliging die de gegevens via een HTTPS-verbinding verzendt in plaats van een HTTP-verbinding.

Als u deze parameter gebruikt, maar SSL niet beschikbaar is op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

Hiermee geeft u een matrix van id van virtuele machines. Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines. Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de volgende opdracht:

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

Hiermee geeft u een matrix met namen van virtuele machines. Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines. Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u `Get-VM` de cmdlet .

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Subsysteem

Hiermee geeft u het SSH-subsysteem op dat wordt gebruikt voor de nieuwe **PSSession**.

Hiermee geeft u het subsysteem op dat op het doel moet worden gebruikt, zoals gedefinieerd in sshd_config.
Het subsysteem start een specifieke versie van PowerShell met vooraf gedefinieerde parameters.
Als het opgegeven subsysteem niet bestaat op de externe computer, mislukt de opdracht.

Als deze parameter niet wordt gebruikt, is de standaardwaarde het subsysteem 'powershell'.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseWindowsPowerShell

{{ Fill UseWindowsPowerShell Description }}

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseWindowsPowerShellParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie voor meer informatie about_CommonParameters ( https://go.microsoft.com/fwlink/?LinkID=113216) .

## Invoerwaarden

### System.String, System.URI, System.Management.Automation.Runspaces.PSSession

U kunt een tekenreeks, URI of sessieobject doorsleesen naar deze cmdlet.

## Uitvoerwaarden

### System.Management.Automation.Runspaces.PSSession

## Notities

- Deze cmdlet maakt gebruik van de infrastructuur voor remoting van PowerShell. Als u deze cmdlet wilt gebruiken, moeten de lokale computer en alle externe computers worden geconfigureerd voor externe toegang van PowerShell. Zie voor meer informatie [about_Remote_Requirements](About/about_Remote_Requirements.md).
- Als u een **PSSession wilt maken** op de lokale computer, start u PowerShell met de optie Als administrator uitvoeren.
- Wanneer u klaar bent met de **PSSession,** gebruikt u de `Remove-PSSession` cmdlet om de **PSSession** te verwijderen en de resources vrij te geven.
- De **parametersets HostName** en **SSHConnection** zijn opgenomen vanaf PowerShell 6.0.
  Ze zijn toegevoegd om Toegang tot PowerShell te bieden op basis van Secure Shell (SSH). Zowel SSH als PowerShell worden ondersteund op meerdere platforms (Windows, Linux, macOS) en voor het voor mobiele gebruik van PowerShell worden deze platformen gebruikt waarop PowerShell en SSH zijn geïnstalleerd en geconfigureerd. Dit staat los van de vorige windows-remoting die is gebaseerd op WinRM en veel specifieke WinRM-functies en -beperkingen zijn niet van toepassing. Bijvoorbeeld quota op basis van WinRM, sessieopties, aangepaste eindpuntconfiguratie en functies voor verbreken/opnieuw verbinden worden momenteel niet ondersteund. Zie Voor meer informatie over het instellen van SSH-remoting voor [PowerShell Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)

## Verwante koppelingen

[Connect-PSSession](Connect-PSSession.md)

[Verbinding verbreken met PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-opdracht](Invoke-Command.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)
