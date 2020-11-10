---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/connect-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-PSSession
ms.openlocfilehash: 3352055e9c77dd944ffd66fa5db9863166ad7e95
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388804"
---
# Connect-PSSession

## SAMENVATTING
Opnieuw verbinding maken met verbroken sessies.

## SYNTAXIS

### Naam (standaard)

```
Connect-PSSession -Name <String[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Sessie

```
Connect-PSSession [-Session] <PSSession[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerName

```
Connect-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameGuid

```
Connect-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-SessionOption <PSSessionOption>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUri

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriGuid

```
Connect-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri[]> [-AllowRedirection]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-SessionOption <PSSessionOption>] [-ThrottleLimit <Int32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Connect-PSSession -InstanceId <Guid[]> [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Connect-PSSession [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Connect-PSSession` cmdlet maakt opnieuw verbinding met door gebruikers beheerde Power shell-sessies ( **PSSessions** ) die zijn losgekoppeld. Het werkt op sessies die opzettelijk worden losgekoppeld, zoals met de `Disconnect-PSSession` cmdlet of de **InDisconnectedSession** -para meter van de `Invoke-Command` cmdlet, en die onbedoeld zijn losgekoppeld, bijvoorbeeld door een tijdelijke netwerk storing.

`Connect-PSSession` kan verbinding maken met elke verbroken sessie die is gestart door dezelfde gebruiker. Dit zijn onder andere de verbindingen die zijn gestart door of losgekoppeld van andere sessies op andere computers.

Er `Connect-PSSession` kan echter geen verbinding worden gemaakt met verbroken of gesloten sessies, of interactieve sessies die zijn gestart met behulp van de `Enter-PSSession` cmdlet. Het is ook niet mogelijk om sessies te verbinden met sessies die zijn gestart door andere gebruikers, tenzij u de referenties kunt opgeven van de gebruiker die de sessie heeft gemaakt.

Zie [about_Remote_Disconnected_Sessions](about/about_Remote_Disconnected_Sessions.md)voor meer informatie over de functie voor verbroken sessies.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: opnieuw verbinding maken met een sessie

```
PS C:\> Connect-PSSession -ComputerName Server01 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Opened        ITTasks                  Available
```

Met deze opdracht wordt opnieuw verbinding gemaakt met de ITTask-sessie op de Server01-computer.

In de uitvoer ziet u dat de opdracht is geslaagd. De **status** van de sessie wordt geopend en de **Beschik baarheid** is beschikbaar. Dit geeft aan dat u opdrachten in de sessie kunt uitvoeren.

### Voor beeld 2: gevolgen van het verbreken van de verbinding en opnieuw verbinden

```
PS C:\> Get-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available


PS C:\> Get-PSSession | Disconnect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Disconnected  Microsoft.PowerShell          None


PS C:\> Get-PSSession | Connect-PSSession

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 Backups         Localhost       Opened        Microsoft.PowerShell     Available
```

In dit voor beeld ziet u het effect van het verbreken van de verbinding en vervolgens de verbinding met een sessie.

De eerste opdracht maakt gebruik van de `Get-PSSession` cmdlet. Zonder de para meter **ComputerName** worden met de opdracht alleen sessies opgehaald die in de huidige sessie zijn gemaakt.

In de uitvoer ziet u dat met de opdracht de back-upsessie wordt opgehaald op de lokale computer. De **status** van de sessie wordt geopend en de **Beschik baarheid** is beschikbaar.

Met de tweede opdracht wordt de `Get-PSSession` cmdlet gebruikt om de **PSSession** -objecten op te halen die zijn gemaakt in de huidige sessie en de `Disconnect-PSSession` cmdlet om de sessie te verbreken. In de uitvoer ziet u dat de verbinding met de back-upsessie is verbroken. De **status** van de sessie wordt verbroken en de **Beschik baarheid** is geen.

De derde opdracht gebruikt de `Get-PSSession` cmdlet om de **PSSession** -objecten op te halen die zijn gemaakt in de huidige sessie en de `Connect-PSSession` cmdlet om de sessies opnieuw te verbinden. In de uitvoer ziet u dat er opnieuw verbinding is gemaakt met de back-up van de sessie. De **status** van de sessie wordt geopend en de **Beschik baarheid** is beschikbaar.

Als u de `Connect-PSSession` cmdlet gebruikt voor een sessie die niet wordt losgekoppeld, is de opdracht niet van invloed op de sessie en worden er geen fouten gegenereerd.

### Voor beeld 3: reeks opdrachten in een bedrijfs scenario

In deze reeks opdrachten ziet u hoe de `Connect-PSSession` cmdlet kan worden gebruikt in een bedrijfs scenario. In dit geval start een systeem beheerder een langlopende taak in een sessie op een externe computer. Nadat de taak is gestart, wordt de verbinding met de sessie verbroken en gaat de beheerder naar thuis.
Later die avond meldt de beheerder zich aan bij haar computer thuis en wordt gecontroleerd of de taak is uitgevoerd totdat deze is voltooid.

De beheerder begint met het maken van een sessie op een externe computer en het uitvoeren van een script in de sessie. De eerste opdracht gebruikt de `New-PSSession` cmdlet om de ITTask-sessie te maken op de externe computer met Server01. De opdracht maakt gebruik van de para meter **configuratiepad** om de ITTasks-sessie configuratie op te geven. Met de opdracht worden de sessies in de `$s` variabele opgeslagen.

De tweede opdracht- `Invoke-Command` cmdlet voor het starten van een achtergrond taak in de sessie in de `$s` variabele. Hierbij wordt de **filepath** -para meter gebruikt voor het uitvoeren van het script in de achtergrond taak.

De derde opdracht gebruikt de `Disconnect-PSSession` cmdlet om de verbinding met de sessie in de variabele te verbreken `$s` . De opdracht gebruikt de para meter **OutputBufferingMode** met de waarde drop om te voor komen dat het script wordt geblokkeerd door uitvoer naar de sessie te leveren. De para meter **IdleTimeoutSec** wordt gebruikt om de sessietime-out uit te breiden tot 15 uur. Wanneer de opdracht is voltooid, wordt de computer door de beheerder vergrendeld en blijft de eind avond thuis.

Later die avond start de beheerder haar thuis computer, meldt zich aan bij het bedrijfs netwerk en start Power shell. De vierde opdracht gebruikt de `Get-PSSession` cmdlet om de sessies op de Server01-computer op te halen. De opdracht vindt de ITTask-sessie. De vijfde opdracht maakt gebruik van de `Connect-PSSession` cmdlet om verbinding te maken met de ITTask-sessie. Met de opdracht wordt de sessie opgeslagen in de `$s` variabele.

De zesde opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `Get-Job` in de sessie in de `$s` variabele. In de uitvoer ziet u dat de taak is voltooid. De zevende opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `Receive-Job` in de sessie in de `$s` variabele in de sessie. Met de opdracht worden de resultaten opgeslagen in de `$BackupSpecs` variabele. De achtste opdracht gebruikt de `Invoke-Command` cmdlet om een ander script uit te voeren in de sessie. De opdracht gebruikt de waarde van de `$BackupSpecs` variabele in de sessie als invoer voor het script.

```
PS C:\> $s = New-PSSession -ComputerName Server01 -Name ITTask -ConfigurationName ITTasks
PS C:\> Invoke-Command -Session $s {Start-Job -FilePath \\Server30\Scripts\Backup-SQLDatabase.ps1}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Running       True            Server01             \\Server30\Scripts\Backup...

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None

PS C:\> Get-PSSession -ComputerName Server01 -Name ITTask

Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None


PS C:\> $s = Connect-PSSession -ComputerName Server01 -Name ITTask


Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Opened        ITTasks               Available

PS C:\> Invoke-Command -Session $s {Get-Job}

Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
2      Job2            Completed     True            Server01             \\Server30\Scripts\Backup...

PS C:\> Invoke-Command -Session $s {$BackupSpecs = Receive-Job -JobName Job2}

PS C:\> Invoke-Command -Session $s {\\Server30\Scripts\New-SQLDatabase.ps1 -InitData $BackupSpecs.Initialization}

PS C:\> Disconnect-PSSession -Session $s -OutputBufferingMode Drop -IdleTimeoutSec 60*60*15
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Server01        Disconnected  ITTasks               None
```

De negende opdracht verbreekt de verbinding met de sessie in de `$s` variabele. De beheerder sluit Power shell en sluit de computer. Ze kan de volgende dag opnieuw verbinding maken met de sessie en de script status van haar werk computer controleren.

## PARAMETERS

### -AllowRedirection

Geeft aan dat deze cmdlet omleiding van deze verbinding met een alternatieve URI toestaat.

Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI. Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding te omleiden.

U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen. Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de voorkeurs variabele **$PSSessionOption** in. De standaard waarde is 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Hiermee geeft u de naam van een toepassing op. Deze cmdlet maakt alleen verbinding met sessies die gebruikmaken van de opgegeven toepassing.

Voer het segment van de toepassings naam van de verbindings-URI in. In de volgende verbindings-URI is de naam van de toepassing bijvoorbeeld WSMan: `http://localhost:5985/WSMAN` . De toepassings naam van een sessie wordt opgeslagen in de eigenschap **runs Pace. Connection info. appName** van de sessie.

De waarde van deze para meter wordt gebruikt voor het selecteren en filteren van sessies. De toepassing die door de sessie wordt gebruikt, wordt niet gewijzigd.

```yaml
Type: System.String
Parameter Sets: ComputerName, ComputerNameGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Verificatie

Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van gebruikers referenties in de opdracht om opnieuw verbinding te maken met de verbroken sessie. De aanvaardbare waarden voor deze parameter zijn:

- Standaard
- Basic
- CredSSP
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

De standaard waarde is standaard.

Zie [AuthenticationMechanism Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.

> [!CAUTION]
> De verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om verbinding te maken met de verbroken sessie. Voer de vinger afdruk van het certificaat in.

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. Ze werken niet met domein accounts.

Als u een certificaat vingerafdruk wilt ophalen, gebruikt u een `Get-Item` of- `Get-ChildItem` opdracht in het Power shell-certificaat: station.

```yaml
Type: System.String
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de computers op waarop de niet-verbonden sessies worden opgeslagen. Sessies worden opgeslagen op de computer die zich aan de server zijde bevindt of het einde van een verbinding ontvangt. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een computer. Joker tekens zijn niet toegestaan. Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven.

```yaml
Type: System.String[]
Parameter Sets: ComputerName, ComputerNameGuid
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Configuratiepad

Maakt alleen verbinding met sessies die gebruikmaken van de opgegeven sessie configuratie.

Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie. Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/powershell` . De configuratie naam van een sessie wordt opgeslagen in de eigenschap **configuratiepad** van de sessie.

De waarde van deze para meter wordt gebruikt voor het selecteren en filteren van sessies. De sessie configuratie die door de sessie wordt gebruikt, wordt niet gewijzigd.

Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

```yaml
Type: System.String
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Hiermee geeft u de Uri's van de verbindings eindpunten voor de niet-verbonden sessies.

De URI moet volledig gekwalificeerd zijn. De indeling van deze teken reeks is als volgt:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

De standaard waarde is als volgt:

`http://localhost:5985/WSMAN`

Als u geen verbindings-URI opgeeft, kunt u de para meters **UseSSL** en **Port** gebruiken om de verbindings-URI-waarden op te geven.

Geldige waarden voor het **transport** segment van de URI zijn http en HTTPS. Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS. Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.

Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUri, ConnectionUriGuid
Aliases: URI, CU

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de verbroken sessie. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals `User01` of `Domain01\User01` , of voer een `PSCredential` object in dat door de `Get-Credential` cmdlet wordt gegenereerd. Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee geeft u de Id's van de niet-verbonden sessies. De **id-** para meter werkt alleen wanneer de verbroken sessie eerder is verbonden met de huidige sessie.

Deze para meter is geldig, maar niet effectief, wanneer de sessie wordt opgeslagen op de lokale computer, maar niet is verbonden met de huidige sessie.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u de exemplaar-Id's van de niet-verbonden sessies.

De exemplaar-ID is een unieke aanduiding voor een **PSSession** op een lokale of externe computer.

De exemplaar-ID wordt opgeslagen in de eigenschap **InstanceId** van de **PSSession**.

```yaml
Type: System.Guid[]
Parameter Sets: ComputerNameGuid, ConnectionUriGuid, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de beschrijvende namen van de niet-verbonden sessies.

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri
Aliases:

Required: True (Name), False (ComputerName, ConnectionUri)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Hiermee geeft u de netwerk poort op de externe computer op die wordt gebruikt om opnieuw verbinding te maken met de sessie. Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt. De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.

Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren. Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de Power shell-prompt:

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

Gebruik de para meter **poort** alleen als dat nodig is. De poort die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.

```yaml
Type: System.Int32
Parameter Sets: ComputerName, ComputerNameGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessie

Hiermee geeft u de verbroken sessies. Voer een variabele in die de **PSSession** -objecten bevat of een opdracht waarmee de **PSSession** -objecten, zoals een opdracht, worden gemaakt of opgehaald `Get-PSSession` .

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Hiermee geeft u geavanceerde opties voor de sessie op. Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de `New-PSSessionOption` cmdlet of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden voor de waarden van de sessie.

De standaard waarden voor de opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld. Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.

De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de `$PSSessionOption` Voorkeurs variabele en in de sessie configuratie. Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.

Zie voor een beschrijving van de sessie opties die de standaard waarden bevatten `New-PSSessionOption` . Zie [about_Preference_Variables](About/about_Preference_Variables.md)voor meer informatie over de **$PSSessionOption** voorkeurs variabele. Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, ComputerNameGuid, ConnectionUri, ConnectionUriGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.
Als u deze para meter weglaat of een waarde van 0 invoert, wordt de standaard waarde 32 gebruikt.

De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de verbroken sessie. Standaard wordt SSL niet gebruikt.

WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden. De para meter **UseSSL** is een extra beveiliging waarmee de gegevens worden verzonden via een HTTPS-verbinding in plaats van via een http-verbinding.

Als u deze para meter gebruikt, maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, ComputerNameGuid
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. Runspaces. PSSession

U kunt een sessie ( **PSSession** ) door sluizen naar deze cmdlet.

## UITVOER

### System. Management. Automation. Runspaces. PSSession

Met deze cmdlet wordt een object geretourneerd dat de sessie vertegenwoordigt waarmee de verbinding is gemaakt.

## OPMERKINGEN

- Deze cmdlet is alleen beschikbaar op Windows-platforms.

- `Connect-PSSession` opnieuw verbinding maken met sessies die niet zijn verbonden, dat wil zeggen, sessies waarvan de waarde voor de eigenschap **State** is verbroken. Alleen sessies die zijn verbonden met of eindigen op computers waarop Windows Power Shell 3,0 of hoger wordt uitgevoerd, kunnen worden losgekoppeld en opnieuw worden aangesloten.

- Als u gebruikt `Connect-PSSession` voor een sessie die niet wordt losgekoppeld, is de opdracht niet van invloed op de sessie en worden er geen fouten gegenereerd.

- Verbroken loop Back-sessies met interactieve tokens, die worden gemaakt met behulp van de para meter **EnableNetworkAccess** , kunnen alleen opnieuw worden verbonden vanaf de computer waarop de sessie is gemaakt. Met deze beperking wordt de computer beschermd tegen kwaadwillende toegang.

- De waarde van de eigenschap **State** van een **PSSession** is relatief ten opzichte van de huidige sessie.
  Als de waarde voor de **verbinding is verbroken** , betekent dit daarom dat de **PSSession** niet is verbonden met de huidige sessie. Het betekent echter niet dat de **PSSession** -verbinding met alle sessies is verbroken. Deze is mogelijk verbonden met een andere sessie. Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de sessie of er opnieuw verbinding mee wilt maken.

  Een **beschikbaarheids** waarde van geen geeft aan dat u verbinding kunt maken met de sessie. De waarde bezet geeft aan dat u geen verbinding kunt maken met de **PSSession** omdat deze is verbonden met een andere sessie.

  Zie [RunspaceState Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.runspacestate)voor meer informatie over de waarden van de eigenschap **State** van sessies.

  Zie [RunspaceAvailability Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de eigenschap **Beschik baarheid** van sessies.

- U kunt de time-outwaarde voor inactiviteit van een **PSSession** niet wijzigen wanneer u verbinding maakt met de **PSSession**. De para meter **SessionOption** van `Connect-PSSession` maakt een **SessionOption** -object met een **IdleTimeout** -waarde. De waarde **IdleTimeout** van het object **SessionOption** en de waarde **IdleTimeout** van de `$PSSessionOption` variabele wordt echter genegeerd wanneer er verbinding wordt gemaakt met een **PSSession**.

  U kunt de time-out voor inactiviteit van een **PSSession** instellen en wijzigen wanneer u de **PSSession** maakt met behulp van de- `New-PSSession` of `Invoke-Command` -cmdlets en wanneer u de verbinding met de **PSSession** verbreekt.

  De eigenschap **IdleTimeout** van een **PSSession** is essentieel voor verbroken sessies, omdat deze bepaalt hoe lang een verbroken sessie op de externe computer wordt onderhouden. Verbroken sessies worden beschouwd als niet-actief vanaf het moment dat ze worden losgekoppeld, zelfs als opdrachten worden uitgevoerd in de verbroken sessie.

## GERELATEERDE KOPPELINGEN

[Verbinding verbreken-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Afsluiten-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Receive-PSSession](Receive-PSSession.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Remove-PSSession](Remove-PSSession.md)
