---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 0fac823666277621c3bed0f961ae2ce22d8d8408
ms.sourcegitcommit: b10731301412afd4111743b85da95e8c25583533
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/20/2021
ms.locfileid: "107756236"
---
# Enter-PSSession

## Synopsis
Start een interactieve sessie met een externe computer.

## Syntax

### ComputerName (standaard)

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### SSHHost

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [-ConnectingTimeout <int>] [<CommonParameters>]
```

### Sessie

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### Uri

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### InstanceId

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### Id

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### Name

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### VMId

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### VMName

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### ContainerId

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## Description

De `Enter-PSSession` cmdlet start een interactieve sessie met één externe computer.
Tijdens de sessie worden de opdrachten die u typt, uitgevoerd op de externe computer, net alsof u rechtstreeks op de externe computer typt. U kunt slechts één interactieve sessie tegelijk hebben.

Normaal gesproken gebruikt u de **ComputerName** parameter opgeven voor de naam van de externe computer.
U kunt echter ook een sessie gebruiken die u maakt met behulp van de `New-PSSession` cmdlet voor de interactieve sessie. U kunt de cmdlets , of echter niet gebruiken om de verbinding met een interactieve sessie te verbreken of opnieuw verbinding `Disconnect-PSSession` `Connect-PSSession` te `Receive-PSSession` maken.

Vanaf PowerShell 6.0 kunt u Secure Shell (SSH) gebruiken om verbinding te maken met een externe computer, als SSH beschikbaar is op de lokale computer en de externe computer is geconfigureerd met een PowerShell SSH-eindpunt. Het voordeel van een externe PowerShell-sessie op basis van SSH is dat deze op meerdere platforms (Windows, Linux, macOS) werkt. Voor externe toegang op basis van SSH gebruikt u de **parameterset HostName** om de externe computer en relevante verbindingsgegevens op te geven. Zie Voor meer informatie over het instellen van SSH-remoting voor [PowerShell Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)

Als u de interactieve sessie wilt beëindigen en de verbinding met de externe computer wilt verbreken, gebruikt u `Exit-PSSession` de cmdlet of typt u `exit` .

## Voorbeelden

### Voorbeeld 1: Een interactieve sessie starten

```
PS> Enter-PSSession
[localhost]: PS>
```

Met deze opdracht start u een interactieve sessie op de lokale computer. De opdrachtprompt wordt gewijzigd om aan te geven dat u nu opdrachten in een andere sessie uitvoeren.

De opdrachten die u op te geven, worden uitgevoerd in de nieuwe sessie en de resultaten worden als tekst geretourneerd naar de standaardsessie.

### Voorbeeld 2: Werken met een interactieve sessie

De eerste opdracht gebruikt de `Enter-PSSession` cmdlet voor het starten van een interactieve sessie met Server01, een externe computer. Wanneer de sessie wordt gestart, wordt de opdrachtprompt gewijzigd om de computernaam op te nemen.

Met de tweede opdracht wordt het PowerShell-proces opgeslagen en wordt de uitvoer omgeleid naar Process.txt bestand. De opdracht wordt verzonden naar de externe computer en het bestand wordt opgeslagen op de externe computer.

De derde opdracht maakt gebruik van **het trefwoord Afsluiten** om de interactieve sessie te beëindigen en de verbinding te sluiten.
De vierde opdracht bevestigt dat het Process.txt bestand zich op de externe computer. Een `Get-ChildItem` opdracht ("dir") op de lokale computer kan het bestand niet vinden.

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

Deze opdracht laat zien hoe u in een interactieve sessie met een externe computer werkt.

### Voorbeeld 3: De sessieparameter gebruiken

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

Deze opdrachten gebruiken de **sessieparameter** van om de interactieve sessie `Enter-PSSession` uit te voeren in een bestaande PowerShell-sessie **(PSSession).**

### Voorbeeld 4: Een interactieve sessie starten en de parameters Port en Credential opgeven

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

Met deze opdracht start u een interactieve sessie met de computer Server01. Hierbij de **poort** parameter opgeven voor de poort en de **referentie** parameter opgeven voor het account van een gebruiker die is machtigingen om verbinding te maken met de externe computer.

### Voorbeeld 5: Een interactieve sessie stoppen

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

In dit voorbeeld ziet u hoe u een interactieve sessie start en stopt. De eerste opdracht gebruikt de `Enter-PSSession` cmdlet om een interactieve sessie met de computer Server01 te starten.

De tweede opdracht gebruikt de `Exit-PSSession` cmdlet om de sessie te beëindigen. U kunt ook het **trefwoord Afsluiten** gebruiken om de interactieve sessie te beëindigen. `Exit-PSSession` en **Afsluiten** hebben hetzelfde effect.

### Voorbeeld 6: Een interactieve sessie starten met SSH

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

In dit voorbeeld ziet u hoe u een interactieve sessie start met behulp van Secure Shell (SSH). Als SSH is geconfigureerd op de externe computer om te vragen om wachtwoorden, krijgt u een wachtwoordprompt.
Anders moet u gebruikersverificatie op basis van een SSH-sleutel gebruiken.

### Voorbeeld 7: Een interactieve sessie starten met SSH en de sleutel voor poort- en gebruikersverificatie opgeven

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

In dit voorbeeld ziet u hoe u een interactieve sessie start met behulp van SSH. De parameter **Port wordt** gebruikt om de poort op te geven die moet worden gebruikt en de parameter **KeyFilePath** om een RSA-sleutel op te geven die wordt gebruikt om de gebruiker op de externe computer te verifiëren.

## Parameters

### -AllowRedirection

Staat omleiding van deze verbinding naar een alternatieve Uniform Resource Identifier (URI) toe. Omleiding is standaard niet toegestaan.

Wanneer u de **parameter ConnectionURI** gebruikt, kan de externe bestemming een instructie retourneren om om te leiden naar een andere URI. PowerShell leidt verbindingen standaard niet om, maar u kunt deze parameter gebruiken om de verbinding om te leiden.

U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de **optiewaarde maximumConnectionRedirectionCount-sessie** te wijzigen. Gebruik de **parameter MaximumRedirection** van de cmdlet of stel de eigenschap `New-PSSessionOption` **MaximumConnectionRedirectionCount** van de `$PSSessionOption` voorkeursvariabele in. De standaardwaarde is 5.

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

De standaardwaarde is de waarde van de `$PSSessionApplicationName` voorkeursvariabele op de lokale computer. Als deze voorkeursvariabele niet is gedefinieerd, is de standaardwaarde WSMAN. Deze waarde is geschikt voor de meeste toepassingen. Zie voor meer informatie [about_Preference_Variables.](About/about_Preference_Variables.md)

De **WinRM-service** gebruikt de toepassingsnaam om een listener te selecteren om de verbindingsaanvraag te verwerken. De waarde van deze parameter moet overeenkomen met de waarde van de **eigenschap URLPrefix** van een listener op de externe computer.

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

Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren. De aanvaardbare waarden voor deze parameter zijn:

- Standaard
- Basic
- Credssp
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

De standaardwaarde is Standaard.

CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturingssysteem.

Zie [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze parameter.

Let op: CredSSP-verificatie (Credential Security Support Provider), waarbij de referenties van de gebruiker worden doorgegeven aan een externe computer om te worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie op meer dan één resource is vereist, zoals toegang tot een externe netwerk share. Dit mechanisme verhoogt het beveiligingsrisico van de externe bewerking. Als de externe computer is gecompromitteerd, kunnen de referenties die worden doorgegeven aan de computer worden gebruikt voor het beheer van de netwerksessie.

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

Certificaten worden gebruikt bij verificatie op basis van clientcertificaten. Ze kunnen alleen worden toe te wijs aan lokale gebruikersaccounts; ze werken niet met domeinaccounts.

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

Hiermee geeft u een computernaam. Deze cmdlet start een interactieve sessie met de opgegeven externe computer. Voer slechts één computernaam in. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, het IP-adres of de fully qualified domain name van de computer. U kunt ook een computernaam doorspijpen naar `Enter-PSSession` .

Als u een IP-adres wilt gebruiken in de waarde van de parameter **ComputerName,** moet de opdracht de parameter **Credential** bevatten. De computer moet ook worden geconfigureerd voor HTTPS-transport of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer. Zie 'How to Add a Computer to the Trusted Host List' in about_Remote_Troubleshooting voor instructies voor het toevoegen van een computernaam [aan de](About/about_Remote_Troubleshooting.md)lijst met TrustedHosts.

Opmerking: in Windows Vista en latere versies van het Windows-besturingssysteem moet u PowerShell starten met de optie Als administrator uitvoeren om de lokale computer op te nemen in de waarde van de parameter **ComputerName.**

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ConfigurationName

Hiermee geeft u de sessieconfiguratie die wordt gebruikt voor de interactieve sessie.

Voer een configuratienaam of de volledig gekwalificeerde resource-URI in voor een sessieconfiguratie. Als u alleen de configuratienaam opgeeft, wordt de volgende schema-URI toegevoegd: `http://schemas.microsoft.com/powershell` .

Bij gebruik met SSH geeft u hiermee het subsysteem op dat moet worden gebruikt op het doel, zoals gedefinieerd in sshd_config. De standaardwaarde voor SSH is het `powershell` subsysteem.

De sessieconfiguratie voor een sessie bevindt zich op de externe computer. Als de opgegeven sessieconfiguratie niet bestaat op de externe computer, mislukt de opdracht.

De standaardwaarde is de waarde van de `$PSSessionConfigurationName` voorkeursvariabele op de lokale computer. Als deze voorkeursvariabele niet is ingesteld, is de standaardwaarde Microsoft.PowerShell. Zie voor meer informatie [about_Preference_Variables.](About/about_Preference_Variables.md)

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

Hiermee geeft u de hoeveelheid tijd in milliseconden op die is toegestaan voor het voltooien van de eerste SSH-verbinding. Als de verbinding niet binnen de opgegeven tijd wordt voltooid, wordt er een fout geretourneerd.

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

Geldige waarden voor het segment Transport van de URI zijn HTTP en HTTPS. Als u een verbindings-URI opgeeft met een Transport-segment, maar geen poort opgeeft, wordt de sessie gemaakt met behulp van standaardenpoorten: 80 voor HTTP en 443 voor HTTPS. Als u de standaardpoorten wilt gebruiken voor remoting van PowerShell, geeft u poort 5985 voor HTTP of 5986 voor HTTPS op.

Als de doelcomputer de verbinding omleiden naar een andere URI, PowerShell voorkomt de omleiding, tenzij u de **parameter AllowRedirection** in de opdracht.

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

Hiermee geeft u de id van een container op.

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikersaccount op dat is machtigingen heeft om deze actie uit te voeren. Standaard is dit de huidige gebruiker.

Typ een gebruikersnaam, zoals **User01** of **Domain01\User01,** of voer een **PSCredential-object** in dat is gegenereerd door de `Get-Credential` cmdlet . Als u een gebruikersnaam typt, wordt u gevraagd het wachtwoord in te voeren.

Referenties worden opgeslagen in een [PSCredential-object](/dotnet/api/system.management.automation.pscredential) en het wachtwoord wordt opgeslagen als een [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie How secure is SecureString? (Hoe veilig [is SecureString?) voor meer informatie over SecureString-gegevensbeveiliging.](/dotnet/api/system.security.securestring#how-secure-is-securestring) 

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EnableNetworkAccess

Geeft aan dat deze cmdlet een interactief beveiliging token toevoegt aan loopback-sessies. Met het interactieve token kunt u opdrachten uitvoeren in de loopback-sessie die gegevens van andere computers op halen. U kunt bijvoorbeeld een opdracht uitvoeren in de sessie die XML-bestanden kopieert van een externe computer naar de lokale computer.

Een loopback-sessie is **een PSSession** die afkomstig is van en eindigt op dezelfde computer. Als u een loopback-sessie wilt maken, laat u de parameter **ComputerName** weg of stelt u de waarde ervan in op . (punt), localhost of de naam van de lokale computer.

Loopback-sessies worden standaard gemaakt met behulp van een netwerk-token, dat mogelijk onvoldoende machtigingen biedt voor verificatie bij externe computers.

De **parameter EnableNetworkAccess** is alleen effectief in loopback-sessies. Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, slaagt de opdracht, maar de parameter wordt genegeerd.

U kunt ook externe toegang toestaan in een loopback-sessie  met behulp van de **CredSSP-waarde** van de verificatieparameter, die de sessiereferenties delegeert naar andere computers.

Deze parameter is geïntroduceerd in Windows PowerShell 3.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -HostName

Hiermee geeft u een computernaam op voor een SSH-verbinding (Secure Shell). Dit is vergelijkbaar met de **ComputerName** parameter behalve dat de verbinding met de externe computer wordt gemaakt met behulp van SSH in plaats van Windows WinRM. Deze parameter ondersteunt het opgeven van de gebruikersnaam en/of poort als onderdeel van de parameterwaarde van de hostnaam met behulp van het formulier `user@hostname:port` . De gebruikersnaam en/of poort die zijn opgegeven als onderdeel van de hostnaam heeft voorrang op de `-UserName` `-Port` parameters en, indien opgegeven. Hierdoor kunnen meerdere computernamen worden doorgegeven aan deze parameter, waarbij sommige specifieke gebruikersnamen en/of poorten hebben, terwijl andere de gebruikersnaam en/of poort van de `-UserName` `-Port` parameters en gebruiken.

Deze parameter is geïntroduceerd in PowerShell 6.0.

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Id

Hiermee geeft u de id van een bestaande sessie. `Enter-PSSession` gebruikt de opgegeven sessie voor de interactieve sessie.

Gebruik de cmdlet om de id van een `Get-PSSession` sessie te vinden.

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u de exemplaar-id van een bestaande sessie. `Enter-PSSession` gebruikt de opgegeven sessie voor de interactieve sessie.

De exemplaar-id is een GUID. Gebruik de cmdlet om de exemplaar-id van een `Get-PSSession` sessie te vinden. U kunt ook de parameters **Sessie,** **Naam** of **Id** gebruiken om een bestaande sessie op te geven. U kunt ook de **parameter ComputerName gebruiken** om een tijdelijke sessie te starten.

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -KeyFilePath

Hiermee geeft u een sleutelbestandspad op dat door Secure Shell (SSH) wordt gebruikt om een gebruiker op een externe computer te verifiëren.

Met SSH kan gebruikersverificatie worden uitgevoerd via persoonlijke/openbare sleutels als alternatief voor basiswachtwoordverificatie. Als de externe computer is geconfigureerd voor sleutelverificatie, kan deze parameter worden gebruikt om de sleutel op te geven waarmee de gebruiker wordt geïdentificeerd.

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

Hiermee geeft u de naam van een bestaande sessie. `Enter-PSSession` gebruikt de opgegeven sessie voor de interactieve sessie.

Als de naam die u opgeeft overeenkomt met meer dan één sessie, mislukt de opdracht. U kunt ook de parameters **Session,** **InstanceID** of **ID** gebruiken om een bestaande sessie op te geven. U kunt ook de **parameter ComputerName gebruiken** om een tijdelijke sessie te starten.

Als u een gebruiksvriendelijke naam voor een sessie wilt maken, gebruikt u de parameter **Name** van de `New-PSSession` cmdlet .

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Port

Hiermee geeft u de netwerkpoort op de externe computer die wordt gebruikt voor deze opdracht.

In PowerShell 6.0 is deze parameter in de **parameterset HostName** gebruikt die ondersteuning biedt voor SSH-verbindingen (Secure Shell).

**WinRM (parameterset ComputerName)**

Als u verbinding wilt maken met een externe computer, moet de externe computer luisteren op de poort die de verbinding gebruikt. De standaardpoorten zijn 5985, de WinRM-poort voor HTTP, en 5986, de WinRM-poort voor HTTPS.

Voordat u een alternatieve poort gebruikt, moet u de WinRM-listener op de externe computer configureren om naar die poort te luisteren. Gebruik de volgende opdrachten om de listener te configureren:

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

Gebruik de parameter **Port alleen** als dat nodig is. De poortinstelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poortinstelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.

**SSH (set hostnaamparameters)**

Als u verbinding wilt maken met een externe computer, moet de externe computer zijn geconfigureerd met de SSH-service (SSHD) en moet deze luisteren op de poort die door de verbinding wordt gebruikt. De standaardpoort voor SSH is 22.

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

Hiermee geeft u een PowerShell-sessie **(PSSession**) op die moet worden gebruikt voor de interactieve sessie. Deze parameter gebruikt een sessieobject. U kunt ook de parameters **Name,** **InstanceID** of **ID** gebruiken om een **PSSession op te geven.**

Voer een variabele in die een sessieobject bevat of een opdracht die een sessieobject maakt of op haalt, zoals een `New-PSSession` - of `Get-PSSession` -opdracht. U kunt ook een sessieobject doorspijpen naar `Enter-PSSession` . U kunt slechts één **PSSession verzenden met** behulp van deze parameter. Als u een variabele met meer dan één **PSSession opgeeft,** mislukt de opdracht.

Wanneer u of `Exit-PSSession` het **trefwoord EXIT** gebruikt, wordt de interactieve sessie beëindigd, maar de **PSSession** die u hebt gemaakt, blijft geopend en beschikbaar voor gebruik.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Hiermee stelt u geavanceerde opties voor de sessie. Voer een **SessionOption-object** in, zoals een object dat u maakt met behulp van de cmdlet of een hash-tabel waarin de sleutels sessieoptienamen zijn en de waarden `New-PSSessionOption` sessieoptiewaarden zijn.

De standaardwaarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` voorkeursvariabele als deze is ingesteld. Anders worden de standaardwaarden ingesteld door opties die zijn ingesteld in de sessieconfiguratie.

De waarden van de sessieoptie hebben voorrang op de standaardwaarden voor sessies die zijn ingesteld in de `$PSSessionOption` voorkeursvariabele en in de sessieconfiguratie. Ze hebben echter geen voorrang op maximumwaarden, quota of limieten die zijn ingesteld in de sessieconfiguratie.

Zie voor een beschrijving van de sessieopties, met inbegrip van de `New-PSSessionOption` standaardwaarden.
Zie voor meer informatie `$PSSessionOption` over de voorkeursvariabele [about_Preference_Variables.](About/about_Preference_Variables.md) Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

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

### -Subsysteem

Hiermee geeft u het SSH-subsysteem op dat wordt gebruikt voor de nieuwe **PSSession**.

Hiermee geeft u het subsysteem op dat moet worden gebruikt op het doel, zoals gedefinieerd in sshd_config. Het subsysteem start een specifieke versie van PowerShell met vooraf gedefinieerde parameters. Als het opgegeven subsysteem niet bestaat op de externe computer, mislukt de opdracht.

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

### -GebruikersNaam

Hiermee geeft u de gebruikersnaam voor het account dat wordt gebruikt voor het maken van een sessie op de externe computer. De verificatiemethode voor gebruikers is afhankelijk van hoe Secure Shell (SSH) is geconfigureerd op de externe computer.

Als SSH is geconfigureerd voor basisverificatie van wachtwoorden, wordt u gevraagd om het gebruikerswachtwoord.

Als SSH is geconfigureerd voor gebruikersverificatie op basis van sleutels, kan er een pad naar een sleutelbestand worden opgegeven via de parameter **KeyFilePath** en wordt er geen wachtwoordprompt uitgevoerd. Houd er rekening mee dat als het clientgebruikerssleutelbestand zich op een bekende SSH-locatie bevindt, de parameter **KeyFilePath** niet nodig is voor verificatie op basis van sleutels en dat gebruikersverificatie automatisch wordt uitgevoerd op basis van de gebruikersnaam. Zie SSH-documentatie over op sleutels gebaseerde gebruikersverificatie voor meer informatie.

Dit is geen vereiste parameter. Als er **geen userName** parameter is opgegeven, wordt de huidige gebruikersnaam voor aanmelden gebruikt voor de verbinding.

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

Geeft aan dat deze cmdlet het SSL-protocol (Secure Sockets Layer) gebruikt om een verbinding met de externe computer tot stand te brengen. Standaard wordt SSL niet gebruikt.

WS-Management versleutelt alle PowerShell-inhoud die via het netwerk wordt verzonden. De **parameter UseSSL** is een extra beveiliging die de gegevens via een HTTPS-verbinding verzendt in plaats van een HTTP-verbinding.

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

Hiermee geeft u de id van een virtuele machine.

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -VMName

Hiermee geeft u de naam van een virtuele machine.

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## Invoerwaarden

### System.String, System.Management.Automation.Runspaces.PSSession

U kunt een computernaam, als een tekenreeks of een sessieobject doorseen naar deze cmdlet.

## Uitvoerwaarden

### Geen

De cmdlet retourneerde geen uitvoer.

## Notities

Als u verbinding wilt maken met een externe computer, moet u lid zijn van de groep Administrators op de externe computer. Als u een interactieve sessie op de lokale computer wilt starten, moet u PowerShell starten met de **optie Als administrator** uitvoeren.

Wanneer u `Enter-PSSession` gebruikt, wordt uw gebruikersprofiel op de externe computer gebruikt voor de interactieve sessie. De opdrachten in het profiel van de externe gebruiker, inclusief opdrachten voor het toevoegen van PowerShell-modules en om de opdrachtprompt te wijzigen, voert u uit voordat de externe prompt wordt weergegeven.

`Enter-PSSession` gebruikt de cultuurinstelling ui op de lokale computer voor de interactieve sessie. Gebruik de automatische variabele om de lokale UI-cultuur `$UICulture` te vinden.

`Enter-PSSession` vereist `Get-Command` de `Out-Default` `Exit-PSSession` cmdlets , en . Als deze cmdlets niet zijn opgenomen in de sessieconfiguratie op de externe computer, mislukt `Enter-PSSession` de opdrachten.

In tegenstelling tot , die de opdrachten parseert en interpreteert voordat deze naar de externe computer worden verzendt, verzendt de opdrachten rechtstreeks naar de externe `Invoke-Command` `Enter-PSSession` computer zonder interpretatie.

Als de sessie die u wilt invoeren bezig is met het verwerken van een opdracht, kan er een vertraging zijn voordat PowerShell op de opdracht `Enter-PSSession` reageert. U bent verbonden zodra de sessie beschikbaar is. Druk op `Enter-PSSession` <kbd>CTRL C</kbd>om de opdracht + <kbd>te annuleren.</kbd>

De **parameterset HostName** is opgenomen vanaf PowerShell 6.0. Het is toegevoegd om Toegang tot PowerShell te bieden op basis van Secure Shell (SSH). Zowel SSH als PowerShell worden ondersteund op meerdere platforms (Windows, Linux, macOS) en voor het voor mobiele gebruik van PowerShell worden deze platformen gebruikt waarop PowerShell en SSH zijn geïnstalleerd en geconfigureerd. Dit staat los van de vorige windows-remoting die is gebaseerd op WinRM en veel van de specifieke WinRM-functies en -beperkingen zijn niet van toepassing. Op WinRM gebaseerde quota, sessieopties, aangepaste eindpuntconfiguratie en functies voor verbreken/opnieuw verbinden worden momenteel bijvoorbeeld niet ondersteund. Zie Voor meer informatie over het instellen van SSH-remoting voor [PowerShell Via SSH.](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)

Vóór PowerShell 7.1 biedt externe externe sessies geen ondersteuning voor externe sessies via externe toegang via SSH. Deze mogelijkheid was beperkt tot sessies met WinRM. Met PowerShell 7.1 kunnen `Enter-PSSession` en werken vanuit elke interactieve externe `Enter-PSHostProcess` sessie.

## Verwante koppelingen

[Exit-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-opdracht](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[Connect-PSSession](Connect-PSSession.md)

[Verbinding verbreken met PSSession](Disconnect-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
