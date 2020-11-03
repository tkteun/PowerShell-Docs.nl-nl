---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: f5b8d82b2f2a30c176ab01be42201434842a0454
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/24/2020
ms.locfileid: "93251670"
---
# Enter-PSSession

## SAMENVATTING
Start een interactieve sessie met een externe computer.

## SYNTAXIS

### Computer naam (standaard)

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### SSHHost

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [<CommonParameters>]
```

### Sessie

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### URI

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

### Naam

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

## BESCHRIJVING

`Enter-PSSession`Met de cmdlet wordt een interactieve sessie met één externe computer gestart.
Tijdens de sessie worden de opdrachten die u typt op de externe computer uitgevoerd, net alsof u rechtstreeks op de externe computer typt. U kunt slechts één interactieve sessie tegelijk hebben.

Normaal gesp roken gebruikt u de para meter **ComputerName** om de naam van de externe computer op te geven.
U kunt echter ook een sessie gebruiken die u maakt met behulp van de `New-PSSession` cmdlet voor de interactieve sessie. U kunt echter de-, `Disconnect-PSSession` `Connect-PSSession` -of-cmdlets niet gebruiken om de verbinding met `Receive-PSSession` een interactieve sessie te verbreken of opnieuw te verbinden.

Vanaf Power shell 6,0 kunt u Secure Shell (SSH) gebruiken om een verbinding met een externe computer tot stand te brengen, als SSH beschikbaar is op de lokale computer en de externe computer is geconfigureerd met een Power shell-SSH-eind punt. Het voor deel van een op SSH gebaseerde Power shell-externe sessie is dat deze werkt op meerdere platformen (Windows, Linux, macOS). Voor op SSH gebaseerde externe communicatie gebruikt u de para meter **hostname** om de externe computer en de relevante verbindings gegevens op te geven. Zie voor meer informatie over het instellen van externe toegang tot Power shell [via SSH Power shell](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

Als u de interactieve sessie wilt beëindigen en de verbinding wilt verbreken met de externe computer, gebruikt u de `Exit-PSSession` cmdlet of het type `exit` .

## VOORBEELDEN

### Voor beeld 1: een interactieve sessie starten

```
PS> Enter-PSSession
[localhost]: PS>
```

Met deze opdracht wordt een interactieve sessie gestart op de lokale computer. De opdracht prompt wordt gewijzigd om aan te geven dat u nu opdrachten uitvoert in een andere sessie.

De opdrachten die u invoert, worden uitgevoerd in de nieuwe sessie en de resultaten worden geretourneerd naar de standaard sessie als tekst.

### Voor beeld 2: werken met een interactieve sessie

Met de eerste opdracht wordt de `Enter-PSSession` cmdlet gebruikt voor het starten van een interactieve sessie met Server01, een externe computer. Wanneer de sessie wordt gestart, wordt de computer naam in de opdracht prompt gewijzigd.

Met de tweede opdracht wordt het Power Shell-proces opgehaald en wordt de uitvoer omgeleid naar het Process.txt-bestand. De opdracht wordt verzonden naar de externe computer en het bestand wordt opgeslagen op de externe computer.

De derde opdracht maakt gebruik van het sleutel woord **Exit** om de interactieve sessie te beëindigen en sluit de verbinding.
Met de vierde opdracht wordt bevestigd dat het Process.txt-bestand zich op de externe computer bevindt. Een `Get-ChildItem` ("dir") opdracht op de lokale computer kan het bestand niet vinden.

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

Met deze opdracht wordt aangegeven hoe u kunt werken in een interactieve sessie met een externe computer.

### Voor beeld 3: de sessie parameter gebruiken

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

Met deze opdrachten wordt de **sessie** parameter van gebruikt `Enter-PSSession` voor het uitvoeren van de interactieve sessie in een bestaande Power shell-sessie ( **PSSession** ).

### Voor beeld 4: een interactieve sessie starten en de poort en de referentie parameters opgeven

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

Met deze opdracht wordt een interactieve sessie gestart met de Server01-computer. De para meter **poort** wordt gebruikt om de poort en de **referentie** parameter op te geven om het account op te geven van een gebruiker die gemachtigd is om verbinding te maken met de externe computer.

### Voor beeld 5: een interactieve sessie stoppen

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

In dit voor beeld ziet u hoe u een interactieve sessie start en stopt. Met de eerste opdracht wordt de `Enter-PSSession` cmdlet gebruikt om een interactieve sessie met de Server01-computer te starten.

De tweede opdracht gebruikt de `Exit-PSSession` cmdlet om de sessie te beëindigen. U kunt ook het sleutel woord **Exit** gebruiken om de interactieve sessie te beëindigen. `Exit-PSSession` en **Afsluiten** hebben hetzelfde effect.

### Voor beeld 6: een interactieve sessie starten met SSH

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

In dit voor beeld ziet u hoe u een interactieve sessie start met behulp van Secure Shell (SSH). Als SSH op de externe computer is geconfigureerd om te vragen om wacht woorden, wordt u gevraagd om een wacht woord op te geven.
Anders moet u gebruikmaken van SSH-sleutel op basis van gebruikers verificatie.

### Voor beeld 7: een interactieve sessie starten met SSH en de poort en gebruikers verificatie sleutel opgeven

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

In dit voor beeld ziet u hoe u een interactieve sessie start met SSH. De para meter **poort** wordt gebruikt om de te gebruiken poort op te geven **en de para** meter voor het sleutelpad om een RSA-sleutel op te geven die wordt gebruikt om de gebruiker te verifiëren op de externe computer.

## PARAMETERS

### -AllowRedirection

Hiermee kan de verbinding worden omgeleid naar een alternatieve URI (Uniform Resource Identifier). Omleiding is standaard niet toegestaan.

Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI. Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding te omleiden.

U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen. Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de `$PSSessionOption` Voorkeurs variabele in. De standaard waarde is 5.

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

Hiermee geeft u het segment van de toepassings naam van de verbindings-URI op. Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de para meter **ConnectionURI** niet gebruikt in de opdracht.

De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer. Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN. Deze waarde is geschikt voor de meeste toepassingen. Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.

De **WinRM** -service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden. De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap **URLPrefix** van een listener op de externe computer.

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
- CredSSP
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

De standaard waarde is standaard.

CredSSP-verificatie is alleen beschikbaar in Windows Vista, Windows Server 2008 en latere versies van het Windows-besturings systeem.

Zie [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.

Let op: de verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

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

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren. Voer de vinger afdruk van het certificaat in.

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.

Als u een certificaat wilt ophalen, gebruikt u de `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.

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

Hiermee geeft u een computer naam op. Met deze cmdlet wordt een interactieve sessie gestart met de opgegeven externe computer. Voer slechts één computer naam in. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, het IP-adres of de Fully Qualified Domain Name van de computer. U kunt ook een computer naam door geven aan `Enter-PSSession` .

Als u een IP-adres wilt gebruiken in de waarde van de para meter **ComputerName** , moet de opdracht de para meter **Credential** bevatten. De computer moet ook worden geconfigureerd voor HTTPS-Trans Port of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer. Zie "een computer toevoegen aan de lijst met vertrouwde hosts" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md)voor instructies voor het toevoegen van een computer naam aan de lijst TrustedHosts.

Opmerking: in Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell starten met de optie als administrator uitvoeren om de lokale computer op te geven in de waarde van de para meter **ComputerName** .

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

### -Configuratiepad

Hiermee geeft u de sessie configuratie op die wordt gebruikt voor de interactieve sessie.

Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie. Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/powershell` .

Bij gebruik in combi natie met SSH geeft dit het subsysteem op dat op het doel moet worden gebruikt, zoals gedefinieerd in sshd_config. De standaard waarde voor SSH is het `powershell` subsysteem.

De sessie configuratie voor een sessie bevindt zich op de externe computer. Als de opgegeven sessie configuratie niet bestaat op de externe computer, mislukt de opdracht.

De standaard waarde is de waarde van de `$PSSessionConfigurationName` Voorkeurs variabele op de lokale computer. Als deze voorkeurs variabele niet is ingesteld, is de standaard instelling micro soft. Power shell. Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie.

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

### -ConnectionUri

Hiermee geeft u een URI op die het verbindings eindpunt voor de sessie definieert. De URI moet volledig gekwalificeerd zijn. De indeling van deze teken reeks is als volgt:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

De standaard waarde is als volgt:

`http://localhost:5985/WSMAN`

Als u geen **ConnectionURI** opgeeft, kunt u de para meters **UseSSL** , **ComputerName** , **Port** en **ApplicationName** gebruiken om de **ConnectionURI** -waarden op te geven.

Geldige waarden voor het transport segment van de URI zijn HTTP en HTTPS. Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met behulp van standaard poorten: 80 voor HTTP en 443 voor HTTPS. Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.

Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.

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

Hiermee geeft u de ID van een container op.

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

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

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

Geeft aan dat met deze cmdlet een interactief beveiligings token wordt toegevoegd aan loop Back-sessies. Met het interactieve token kunt u opdrachten uitvoeren in de loop back-sessie die gegevens van andere computers ophalen. U kunt bijvoorbeeld een opdracht uitvoeren in de sessie waarmee XML-bestanden van een externe computer naar de lokale computer worden gekopieerd.

Een loop back-sessie is een **PSSession** die afkomstig is van en eindigt op dezelfde computer. Als u een loop back-sessie wilt maken, laat u de para meter **ComputerName** weg of stelt u de waarde in op. (punt), localhost of de naam van de lokale computer.

Loop Back-sessies worden standaard gemaakt met behulp van een netwerk token, wat mogelijk niet voldoende machtigingen biedt om te verifiëren bij externe computers.

De para meter **EnableNetworkAccess** is alleen effectief in loop Back-sessies. Als u **EnableNetworkAccess** gebruikt wanneer u een sessie op een externe computer maakt, mislukt de opdracht, maar wordt de para meter genegeerd.

U kunt externe toegang ook toestaan in een loop back-sessie met behulp van de **CredSSP** -waarde van de **verificatie** parameter, die de sessie referenties delegeert naar andere computers.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

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

### -Hostnaam

Hiermee geeft u een computer naam voor een verbinding op basis van SSH (Secure Shell). Dit is vergelijkbaar met de para meter **ComputerName** , behalve dat de verbinding met de externe computer wordt gemaakt met behulp van SSH in plaats van Windows WinRM. Met deze para meter kunt u de gebruikers naam en/of poort opgeven als onderdeel van de waarde van de para meter voor de naam van de hostnaam met behulp van het formulier `user@hostname:port` . De gebruikers naam en/of poort die is opgegeven als onderdeel van de hostnaam, hebben voor rang op de `-UserName` `-Port` para meters en, indien opgegeven. Hierdoor kunnen meerdere computer namen worden door gegeven aan deze para meter, waarbij sommige specifieke gebruikers namen en/of poorten worden gebruikt, terwijl anderen de gebruikers naam en/of poort van de `-UserName` `-Port` para meters en gebruiken.

Deze para meter is geïntroduceerd in Power shell 6,0.

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

Hiermee geeft u de ID op van een bestaande sessie. `Enter-PSSession` maakt gebruik van de opgegeven sessie voor de interactieve sessie.

Gebruik de cmdlet om de ID van een sessie te vinden `Get-PSSession` .

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

Hiermee geeft u de exemplaar-ID van een bestaande sessie. `Enter-PSSession` maakt gebruik van de opgegeven sessie voor de interactieve sessie.

De exemplaar-ID is een GUID. Gebruik de cmdlet om de exemplaar-ID van een sessie te vinden `Get-PSSession` . U kunt ook de para meters voor de **sessie** , **naam** of **id** gebruiken om een bestaande sessie op te geven. U kunt ook de para meter **ComputerName** gebruiken om een tijdelijke sessie te starten.

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

### -Bestandspad

Hiermee geeft u een pad naar een sleutel bestand dat door een Secure Shell (SSH) wordt gebruikt om een gebruiker op een externe computer te verifiëren.

Met SSH kan gebruikers verificatie worden uitgevoerd via persoonlijke/open bare sleutels als alternatief voor de basis wachtwoord verificatie. Als de externe computer is geconfigureerd voor sleutel verificatie, kan deze para meter worden gebruikt om de sleutel op te geven waarmee de gebruiker wordt geïdentificeerd.

Deze para meter is geïntroduceerd in Power shell 6,0.

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

Hiermee geeft u de beschrijvende naam van een bestaande sessie. `Enter-PSSession` maakt gebruik van de opgegeven sessie voor de interactieve sessie.

Als de naam die u opgeeft, overeenkomt met meer dan één sessie, mislukt de opdracht. U kunt ook de para meters **Session** , **InstanceId** of **id** gebruiken om een bestaande sessie op te geven. U kunt ook de para meter **ComputerName** gebruiken om een tijdelijke sessie te starten.

Als u een beschrijvende naam voor een sessie wilt instellen, gebruikt u de para meter **name** van de `New-PSSession` cmdlet.

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

Hiermee geeft u de netwerk poort op de externe computer die wordt gebruikt voor deze opdracht.

In Power shell 6,0 is deze para meter Inlcuded in de para meter **hostname** die ondersteuning biedt voor ssh-verbindingen (Secure Shell).

**WinRM (ComputerName para meter set)**

Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt. De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.

Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren. Gebruik de volgende opdrachten om de listener te configureren:

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

Gebruik de para meter **poort** alleen als dat nodig is. De poort instelling in de opdracht is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.

**SSH (HostName para meter set)**

Als u verbinding wilt maken met een externe computer, moet de externe computer zijn geconfigureerd met de SSH-service (SSHD) en moet u Luis teren op de poort die door de verbinding wordt gebruikt. De standaard poort voor SSH is 22.

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

Geeft aan dat de **PSSession** wordt uitgevoerd als beheerder.

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

Hiermee geeft u een Power shell-sessie ( **PSSession** ) op die moet worden gebruikt voor de interactieve sessie. Deze para meter gebruikt een sessie object. U kunt ook de para meters **name** , **InstanceId** of **id** gebruiken om een **PSSession** op te geven.

Voer een variabele in die een sessie object bevat of een opdracht waarmee een sessie object wordt gemaakt of opgehaald, zoals een `New-PSSession` of- `Get-PSSession` opdracht. U kunt ook een sessie object door sluizen naar `Enter-PSSession` . U kunt slechts één **PSSession** verzenden met behulp van deze para meter. Als u een variabele opgeeft die meer dan één **PSSession** bevat, mislukt de opdracht.

Wanneer u `Exit-PSSession` of het sleutel woord **Exit** gebruikt, wordt de interactieve sessie beëindigd, maar de **PSSession** die u hebt gemaakt, blijft open en beschikbaar voor gebruik.

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

Hiermee stelt u geavanceerde opties in voor de sessie. Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden voor de waarden van de sessie.

De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld. Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.

De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie. Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.

Zie voor een beschrijving van de sessie opties, met inbegrip van de standaard waarden `New-PSSessionOption` .
Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](About/about_Preference_Variables.md)variabele. Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

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

Power Shell maakt standaard gebruik van Windows WinRM om verbinding te maken met een externe computer. Met deze switch wordt Power shell gedwongen de para meter HostName te gebruiken die is ingesteld voor het maken van een externe SSH-verbinding.

Deze para meter is geïntroduceerd in Power shell 6,0.

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

Hiermee geeft u het subsysteem op dat moet worden gebruikt op het doel zoals gedefinieerd in sshd_config. Het subsysteem start een specifieke versie van Power shell met vooraf gedefinieerde para meters. Als het opgegeven subsysteem niet bestaat op de externe computer, mislukt de opdracht.

Als deze para meter niet wordt gebruikt, is de standaard het subsysteem Power shell.

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

Hiermee geeft u de gebruikers naam op voor het account dat wordt gebruikt om een sessie te maken op de externe computer. De verificatie methode voor de gebruiker is afhankelijk van hoe Secure Shell (SSH) is geconfigureerd op de externe computer.

Als SSH is geconfigureerd voor basis wachtwoord verificatie, wordt u gevraagd om het wacht woord van de gebruiker.

Als SSH is geconfigureerd voor sleutel op basis van gebruikers verificatie, kan een pad naar een sleutel bestand worden opgegeven **via de para** meter voor het sleutelpad en er wordt geen wachtwoord prompt weer gegeven. Houd er rekening mee dat als het sleutel bestand van de client gebruiker zich bevindt op een bekende SSH-locatie, de para meter voor het **bestandspad** niet nodig is voor op sleutels gebaseerde verificatie en de gebruikers verificatie automatisch wordt uitgevoerd op basis van de gebruikers naam. Raadpleeg SSH-documentatie over op sleutels gebaseerde gebruikers verificatie voor meer informatie.

Dit is geen vereiste para meter. Als er geen **username** -para meter is opgegeven, wordt de naam van de huidige aanmeldings gebruiker gebruikt voor de verbinding.

Deze para meter is geïntroduceerd in Power shell 6,0.

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

Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de externe computer. Standaard wordt SSL niet gebruikt.

WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden. De para meter **UseSSL** is een extra beveiliging waarmee de gegevens worden verzonden via een HTTPS-verbinding in plaats van via een http-verbinding.

Als u deze para meter gebruikt, maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.

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

Hiermee geeft u de ID van een virtuele machine op.

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

Hiermee geeft u de naam van een virtuele machine op.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String, System. Management. Automation. Runspaces. PSSession

U kunt een computer naam, als een teken reeks of een sessie object door geven aan deze cmdlet.

## UITVOER

### Geen

De cmdlet retourneert geen uitvoer.

## OPMERKINGEN

Als u verbinding wilt maken met een externe computer, moet u lid zijn van de groep Administrators op de externe computer. Als u een interactieve sessie op de lokale computer wilt starten, moet u Power shell starten met de optie **als administrator uitvoeren** .

Wanneer u gebruikt `Enter-PSSession` , wordt uw gebruikers profiel op de externe computer gebruikt voor de interactieve sessie. De opdrachten in het profiel voor externe gebruikers, met inbegrip van opdrachten voor het toevoegen van Power shell-modules en het wijzigen van de opdracht prompt, uitvoeren voordat de prompt op afstand wordt weer gegeven.

`Enter-PSSession` maakt gebruik van de GEBRUIKERSINTERFACE cultuur-instelling op de lokale computer voor de interactieve sessie. Gebruik de automatische variabele om de lokale GEBRUIKERSINTERFACE cultuur te vinden `$UICulture` .

`Enter-PSSession` vereist de `Get-Command` `Out-Default` `Exit-PSSession` cmdlets, en. Als deze cmdlets niet zijn opgenomen in de sessie configuratie op de externe computer, `Enter-PSSession` mislukt de opdrachten.

In tegens telling tot `Invoke-Command` , waarbij de opdrachten worden geparseerd en geïnterpreteerd voordat deze naar de externe computer worden verzonden, `Enter-PSSession` verzendt de opdrachten rechtstreeks naar de externe computer zonder interpretatie.

Als de sessie die u wilt invoeren, bezig is met het verwerken van een opdracht, kan er een vertraging optreden voordat Power shell reageert op de `Enter-PSSession` opdracht. U bent verbonden zodra de sessie beschikbaar is. U annuleert de `Enter-PSSession` opdracht door op <kbd>CTRL</kbd> + <kbd>C</kbd>te drukken.

De para meter **hostname** is opgenomen vanaf power shell 6,0. Het is toegevoegd om externe communicatie van Power shell op te geven op basis van de Secure Shell (SSH). SSH en Power shell worden ondersteund op meerdere platformen (Windows, Linux, macOS) en externe communicatie met Power shell werkt op deze platforms waarin Power shell en SSH zijn geïnstalleerd en geconfigureerd. Dit is gescheiden van de vorige Windows-functie voor externe toegang die is gebaseerd op WinRM en veel van de specifieke WinRM-functies en-beperkingen zijn niet van toepassing. Zo worden op WinRM gebaseerde quota's, sessie opties, aangepaste eindpunt configuratie en functies voor ontkoppelen en opnieuw verbinden op dit moment niet ondersteund. Zie voor meer informatie over het instellen van externe toegang tot Power shell [via SSH Power shell](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

Voorafgaand aan Power shell 7,1 heeft externe toegang via SSH geen ondersteuning voor externe sessies van de tweede hop. Deze mogelijkheid is beperkt tot sessies met WinRM. Met Power shell 7,1 kunt `Enter-PSSession` `Enter-PSHostProcess` u binnen elke interactieve externe sessie werken.

## GERELATEERDE KOPPELINGEN

[Afsluiten-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-opdracht](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[Connect-PSSession](Connect-PSSession.md)

[Verbinding verbreken-PSSession](Disconnect-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)
