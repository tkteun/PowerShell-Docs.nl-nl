---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSession
ms.openlocfilehash: 08ca0ec9a45542e86ea197fc24df65430f2d0649
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251629"
---
# Get-PSSession

## SAMENVATTING
Hiermee haalt u de Power shell-sessies op lokale en externe computers op.

## SYNTAXIS

### Naam (standaard)

```
Get-PSSession [-Name <String[]>] [<CommonParameters>]
```

### ComputerName

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 [-Name <String[]>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ComputerInstanceId

```
Get-PSSession [-ComputerName] <String[]> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid[]> [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [-Port <Int32>] [-UseSSL] [-ThrottleLimit <Int32>]
 [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUri

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] [-Name <String[]>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Get-PSSession [-ConnectionUri] <Uri[]> [-ConfigurationName <String>] [-AllowRedirection] -InstanceId <Guid[]>
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-ThrottleLimit <Int32>] [-State <SessionFilterState>] [-SessionOption <PSSessionOption>] [<CommonParameters>]
```

### VMNameInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -VMName <String[]> [<CommonParameters>]
```

### ContainerId

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### ContainerIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>]
 -ContainerId <String[]> [<CommonParameters>]
```

### VMId

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### VMIdInstanceId

```
Get-PSSession [-ConfigurationName <String>] -InstanceId <Guid[]> [-State <SessionFilterState>] -VMId <Guid[]>
 [<CommonParameters>]
```

### VMName

```
Get-PSSession [-ConfigurationName <String>] [-Name <String[]>] [-State <SessionFilterState>] -VMName <String[]>
 [<CommonParameters>]
```

### InstanceId

```
Get-PSSession [-InstanceId <Guid[]>] [<CommonParameters>]
```

### Id

```
Get-PSSession [-Id] <Int32[]> [<CommonParameters>]
```

## BESCHRIJVING

De `Get-PSSession` cmdlet haalt de door de gebruiker beheerde Power shell-sessies ( **PSSessions** ) op lokale en externe computers op.

Vanaf Windows Power Shell 3,0 worden sessies opgeslagen op de computers aan het externe uiteinde van elke verbinding. U kunt de para meters **ComputerName** of **ConnectionUri** van gebruiken `Get-PSSession` voor het ophalen van de sessies die verbinding maken met de lokale computer of externe computers, zelfs als ze niet in de huidige sessie zijn gemaakt.

Zonder para meters worden `Get-PSSession` alle sessies opgehaald die in de huidige sessie zijn gemaakt.

Gebruik de filter parameters, zoals **naam** , **id** , **InstanceId** , **status** , **ApplicationName** en **configuratiepad** om te selecteren uit de sessies die worden `Get-PSSession` geretourneerd.

Gebruik de resterende para meters voor het configureren van de tijdelijke verbinding waarbij de `Get-PSSession` opdracht wordt uitgevoerd wanneer u de para meter **ComputerName** of **ConnectionUri** gebruikt.

Opmerking: in Windows Power Shell 2,0, zonder para meters, worden `Get-PSSession` alle sessies opgehaald die in de huidige sessie zijn gemaakt. De para meter **ComputerName** haalt sessies op die in de huidige sessie zijn gemaakt en maakt verbinding met de opgegeven computer.

Zie [about_PSSessions](about/about_PSSessions.md)voor meer informatie over Power shell-sessies.

## VOORBEELDEN

### Voor beeld 1: sessies die zijn gemaakt in de huidige sessie ophalen

```powershell
Get-PSSession
```

Met deze opdracht worden alle **PSSessions** opgehaald die in de huidige sessie zijn gemaakt. Er worden geen **PSSessions** opgehaald die zijn gemaakt in andere sessies of op andere computers, zelfs als ze verbinding maken met deze computer.

### Voor beeld 2: sessies ophalen die zijn verbonden met de lokale computer

```powershell
Get-PSSession -ComputerName "localhost"
```

Met deze opdracht worden de **PSSessions** die zijn verbonden met de lokale computer. Typ de computer naam, localhost of een punt (.) om de lokale computer aan te duiden.

De opdracht retourneert alle sessies op de lokale computer, zelfs als ze zijn gemaakt in verschillende sessies of op verschillende computers.

### Voor beeld 3: sessies ophalen die zijn verbonden met een computer

```powershell
Get-PSSession -ComputerName "Server02"
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  2 Session3        Server02       Disconnected  ITTasks                       Busy
  1 ScheduledJobs   Server02       Opened        Microsoft.PowerShell     Available
  3 Test            Server02       Disconnected  Microsoft.PowerShell          Busy
```

Met deze opdracht worden de **PSSessions** opgehaald die zijn verbonden met de Server02-computer.

Met de opdracht worden alle sessies in Server02 geretourneerd, zelfs als ze zijn gemaakt in verschillende sessies of op verschillende computers.

In de uitvoer ziet u dat twee van de sessies een niet-verbonden status hebben en een beschikbaarheids info. Ze zijn in verschillende sessies gemaakt en zijn momenteel in gebruik. De ScheduledJobs-sessie, die wordt geopend en beschikbaar, is in de huidige sessie gemaakt.

### Voor beeld 4: resultaten van deze opdracht opslaan

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
$s1, $s2, $s3 = Get-PSSession
```

In dit voor beeld ziet u hoe u de resultaten van een `Get-PSSession` opdracht in meerdere variabelen opslaat.

De eerste opdracht gebruikt de `New-PSSession` cmdlet om **PSSessions** te maken op drie externe computers.

De tweede opdracht maakt gebruik van een `Get-PSSession` cmdlet om de drie **PSSessions** op te halen. Vervolgens worden alle **PSSessions** in een afzonderlijke variabele opgeslagen.

Wanneer Power shell een matrix met objecten toewijst aan een matrix met variabelen, wordt het eerste object toegewezen aan de eerste variabele, het tweede object op de tweede variabele, enzovoort. Als er meer objecten zijn dan variabelen, worden alle resterende objecten toegewezen aan de laatste variabele in de matrix. Als er meer variabelen zijn dan objecten, worden de extra variabelen niet gebruikt.

### Voor beeld 5: een sessie verwijderen met een exemplaar-ID

```powershell
Get-PSSession | Format-Table -Property ComputerName, InstanceID
$s = Get-PSSession -InstanceID a786be29-a6bb-40da-80fb-782c67f7db0f
Remove-PSSession -Session $s
```

In dit voor beeld ziet u hoe u een **PSSession** ophaalt met behulp van de instantie-id en vervolgens verwijdert u de **PSSession**.

Met de eerste opdracht worden alle **PSSessions** opgehaald die in de huidige sessie zijn gemaakt. De **PSSessions** wordt verzonden naar de cmdlet Format-Table, waarin de eigenschappen **ComputerName** en **InstanceId** van elke **PSSession** worden weer gegeven.

Met de tweede opdracht wordt de `Get-PSSession` cmdlet gebruikt voor het ophalen van een bepaalde **PSSession** en om deze op te slaan in de `$s` variabele. De opdracht gebruikt de **InstanceId** para meter om de **PSSession** te identificeren.

De derde opdracht maakt gebruik van de Remove-PSSession cmdlet om de **PSSession** in de variabele te verwijderen `$s` .

### Voor beeld 6: een sessie met een bepaalde naam ophalen

Met de opdrachten in dit voor beeld wordt een sessie met een bepaalde naam indeling gevonden en wordt een bepaalde sessie configuratie gebruikt en wordt vervolgens verbinding gemaakt met de sessie. U kunt een opdracht als deze gebruiken om een sessie te vinden waarin een collega een taak begon en verbinding maken om de taak te volt ooien.

```powershell
Get-PSSession -ComputerName Server02, Server12 -Name BackupJob* -ConfigurationName ITTasks -SessionOption @{OperationTimeout=240000}
```

```Output
 Id Name            ComputerName    State         ConfigurationName     Availability
 -- ----            ------------    -----         -----------------     ------------
  3 BackupJob04     Server02        Disconnected        ITTasks                  None
```

```powershell
$s = Get-PSSession -ComputerName Server02 -Name BackupJob04 -ConfigurationName ITTasks | Connect-PSSession
$s
```

```Output
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 5 BackupJob04     Server02        Opened        ITTasks                  Available
```

De eerste opdracht haalt sessies op de Server02 en Server12 externe computers met namen die beginnen met BackupJob en gebruik de ITTasks-sessie configuratie. De opdracht gebruikt de para meter **name** om het naam patroon en de para meter **configuratiepad** op te geven om de sessie configuratie op te geven. De waarde van de para meter **SessionOption** is een hash-tabel waarmee de waarde van de **OperationTimeout** wordt ingesteld op 240000 milliseconden (4 minuten). Deze instelling zorgt ervoor dat de opdracht meer tijd in beslag is. De para meters **configuratiepad** en **SessionOption** worden gebruikt voor het configureren van de tijdelijke sessies waarin de `Get-PSSession` cmdlet op elke computer wordt uitgevoerd. In de uitvoer ziet u dat de opdracht de BackupJob04-sessie retourneert. De sessie wordt beëindigd en de **Beschik baarheid** is geen, wat aangeeft dat deze niet in gebruik is.

Met de tweede opdracht wordt de `Get-PSSession` cmdlet gebruikt voor het ophalen van de BackupJob04-sessie en de cmdlet Connect-PSSession om verbinding te maken met de sessie. Met de opdracht wordt de sessie opgeslagen in de variabele $s.

Met de derde opdracht wordt de sessie in de variabele $s opgehaald. In de uitvoer ziet u dat de `Connect-PSSession` opdracht is geslaagd. De sessie bevindt zich in de status **Open** en is beschikbaar voor gebruik.

### Voor beeld 7: een sessie ophalen met behulp van de ID

```powershell
Get-PSSession -Id 2
```

Met deze opdracht wordt de **PSSession** met id 2 opgehaald. Omdat de waarde van de eigenschap **id** alleen uniek is in de huidige sessie, is de **id-** para meter alleen geldig voor lokale opdrachten.

## PARAMETERS

### -AllowRedirection

Geeft aan dat deze cmdlet omleiding van deze verbinding met een alternatieve URI (Uniform Resource Identifier) mogelijk maakt. Standaard worden verbindingen door Power shell niet omgeleid.

Met deze para meter configureert u de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ConnectionUri** .

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Hiermee geeft u de naam van een toepassing op. Deze cmdlet maakt alleen verbinding met sessies die gebruikmaken van de opgegeven toepassing.

Voer het segment van de toepassings naam van de verbindings-URI in. In de volgende verbindings-URI is de naam van de toepassing bijvoorbeeld WSMan: `http://localhost:5985/WSMAN` . De toepassings naam van een sessie wordt opgeslagen in de eigenschap **runs Pace. Connection info. appName** van de sessie.

De waarde van deze para meter wordt gebruikt voor het selecteren en filteren van sessies. De toepassing die door de sessie wordt gebruikt, wordt niet gewijzigd.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Verificatie

Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van referenties voor de sessie waarin de `Get-PSSession` opdracht wordt uitgevoerd.

Met deze para meter configureert u de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ComputerName** of **ConnectionUri** .

De aanvaardbare waarden voor deze parameter zijn:

- Standaard
- Basic
- CredSSP
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential.

De standaard waarde is standaard.

Zie [AuthenticationMechanism Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.runspaces.authenticationmechanism) in de MSDN-bibliotheek voor meer informatie over de waarden van deze para meter.

Let op: de verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat gemachtigd is om de sessie te maken waarin de `Get-PSSession` opdracht wordt uitgevoerd. Voer de vinger afdruk van het certificaat in.

Met deze para meter configureert u de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ComputerName** of **ConnectionUri** .

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.

Als u een certificaat vingerafdruk wilt krijgen, gebruikt u een Get-Item-of Get-ChildItem opdracht in het Power shell-certificaat: station.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u een matrix met namen van computers op. Hiermee worden de sessies opgehaald die verbinding maken met de opgegeven computers.
Joker tekens zijn niet toegestaan. Er is geen standaard waarde.

Vanaf Windows Power Shell 3,0 worden **PSSession** -objecten opgeslagen op de computers aan het externe uiteinde van elke verbinding. Om de sessies op de opgegeven computers op te halen, maakt Power shell een tijdelijke verbinding met elke computer en voert een `Get-PSSession` opdracht uit.

Typ de NetBIOS-naam, een IP-adres of een FQDN-naam (Fully Qualified Domain Name) van een of meer computers. Typ de computer naam, localhost of een punt (.) om de lokale computer op te geven.

Opmerking: met deze para meter worden alleen sessies opgehaald van computers waarop Windows Power Shell 3,0 of hoger van Power shell wordt uitgevoerd. In eerdere versies worden geen sessies opgeslagen.

```yaml
Type: System.String[]
Parameter Sets: ComputerInstanceId, ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Configuratiepad

Hiermee geeft u de naam van een configuratie. Deze cmdlet wordt alleen gebruikt voor sessies die gebruikmaken van de opgegeven sessie configuratie.

Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie. Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor voegsel: `http://schemas.microsoft.com/powershell` . De configuratie naam van een sessie wordt opgeslagen in de eigenschap **configuratiepad** van de sessie.

De waarde van deze para meter wordt gebruikt voor het selecteren en filteren van sessies. De sessie configuratie die door de sessie wordt gebruikt, wordt niet gewijzigd.

Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

```yaml
Type: System.String
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Hiermee geeft u een URI op die het verbindings eindpunt definieert voor de tijdelijke sessie waarin de `Get-PSSession` opdracht wordt uitgevoerd. De URI moet volledig gekwalificeerd zijn.

Met deze para meter configureert u de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ConnectionUri** .

De notatie van deze teken reeks is:

`<Transport>://<ComputerName>:<Port\>/<ApplicationName>`

De standaard waarde is: `http://localhost:5985/WSMAN` .

Als u geen **ConnectionUri** opgeeft, kunt u de para meters **UseSSL** , **ComputerName** , **Port** en **ApplicationName** gebruiken om de **ConnectionUri** -waarden op te geven. Geldige waarden voor het transport segment van de URI zijn HTTP en HTTPS. Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS. Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.

Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

Met deze para meter worden alleen sessies opgehaald van computers waarop Windows Power Shell 3,0 of een latere versie van Windows Power shell wordt uitgevoerd. In eerdere versies worden geen sessies opgeslagen.

```yaml
Type: System.Uri[]
Parameter Sets: ConnectionUriInstanceId, ConnectionUri
Aliases: URI, CU

Required: True
Position: 0
Default value: Http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ContainerId

Hiermee geeft u een matrix met Id's van containers op. Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven containers. Gebruik de `docker ps` opdracht om een lijst met container-id's op te halen. Zie de Help voor de opdracht [docker PS](https://docs.docker.com/engine/reference/commandline/ps/) voor meer informatie.

```yaml
Type: System.String[]
Parameter Sets: ContainerId, ContainerIdInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers referentie op. Met deze cmdlet wordt de opdracht uitgevoerd met de machtigingen van de opgegeven gebruiker. Geef een gebruikers account op dat is gemachtigd om verbinding te maken met de externe computer en een opdracht uit te voeren `Get-PSSession` . Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

Deze para meter wordt geconfigureerd voor de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ComputerName** of **ConnectionUri** .

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee geeft u een matrix met sessie-Id's op. Met deze cmdlet worden alleen de sessies met de opgegeven Id's opgehaald. Typ een of meer Id's, gescheiden door komma's, of gebruik de operator Range (..) om een bereik van Id's op te geven. U kunt de ID-para meter niet gebruiken in combi natie met de para meter **ComputerName** .

Een ID is een geheel getal dat de door de gebruiker beheerde sessies op unieke wijze identificeert in de huidige sessie. Het is gemakkelijker te onthouden en te typen dan de **InstanceId** , maar is alleen uniek binnen de huidige sessie. De ID van een sessie wordt opgeslagen in de eigenschap ID van de sessie.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u een matrix met exemplaar-Id's van sessies. Met deze cmdlet worden alleen de sessies met de opgegeven exemplaar-Id's opgehaald.

De exemplaar-ID is een GUID waarmee een sessie op een lokale of externe computer uniek wordt geïdentificeerd. De **InstanceId** is uniek, zelfs wanneer er meerdere sessies in Power shell worden uitgevoerd.

De exemplaar-ID van een sessie wordt opgeslagen in de eigenschap **InstanceId** van de sessie.

```yaml
Type: System.Guid[]
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId, InstanceId
Aliases:

Required: True (ComputerInstanceId, ConnectionUriInstanceId, ContainerIdInstanceId, VMIdInstanceId, VMNameInstanceId), False (InstanceId)
Position: Named
Default value: All sessions
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u een matrix met sessie namen op. Met deze cmdlet worden alleen de sessies met de opgegeven beschrijvende namen opgehaald. Joker tekens zijn toegestaan.

De beschrijvende naam van een sessie wordt opgeslagen in de eigenschap **name** van de sessie.

```yaml
Type: System.String[]
Parameter Sets: Name, ComputerName, ConnectionUri, ContainerId, VMId, VMName
Aliases:

Required: False
Position: Named
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Port

Hiermee geeft u de opgegeven netwerk poort die wordt gebruikt voor de tijdelijke verbinding waarin de `Get-PSSession` opdracht wordt uitgevoerd. Als u verbinding wilt maken met een externe computer, moet op de externe computer worden geluisterd op de poort die door de verbinding wordt gebruikt. De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.

Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren. Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de Power shell-prompt:

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

Deze para meter wordt geconfigureerd voor de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ComputerName** of **ConnectionUri** .

Gebruik de para meter **poort** alleen als dat nodig is. De **poort** die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: 5985, 5986
Accept pipeline input: False
Accept wildcard characters: False
```

### -SessionOption

Hiermee geeft u geavanceerde opties voor de sessie op. Voer een **SessionOption** -object in, zoals het, dat u maakt met behulp van de cmdlet New-PSSessionOption, of een hash-tabel waarin de sleutels de naam van de sessie optie zijn en de waarden zijn de waarden van de sessie.

De standaard waarden voor de opties worden bepaald door de waarde van de $PSSessionOption voorkeurs variabele, als deze is ingesteld. Anders worden de standaard waarden bepaald door opties die zijn ingesteld in de sessie configuratie.

De waarden van de sessie optie hebben voor rang op de standaard waarden voor sessies die zijn ingesteld in de $PSSessionOption voorkeurs variabele en in de sessie configuratie. Ze hebben echter geen voor rang op de maximum waarden, quota's of limieten die zijn ingesteld in de sessie configuratie.

Zie voor een beschrijving van de sessie opties, met inbegrip van de standaard waarden `New-PSSessionOption` .
Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](About/about_Preference_Variables.md)variabele. Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status

Hiermee geeft u een sessie status op. Met deze cmdlet worden alleen sessies in de opgegeven status opgehaald. De acceptabele waarden voor deze para meter zijn: alle, geopend, losgekoppeld, gesloten en verbroken. De standaardwaarde is Alle.

De sessie status waarde is relatief ten opzichte van de huidige sessies. Sessies die niet in de huidige sessies zijn gemaakt en niet zijn verbonden met de huidige sessie, hebben de status losgekoppeld, zelfs wanneer ze zijn verbonden met een andere sessie.

De status van een sessie wordt opgeslagen in de eigenschap **State** van de sessie.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: Microsoft.PowerShell.Commands.SessionFilterState
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri, ContainerId, ContainerIdInstanceId, VMId, VMIdInstanceId, VMName, VMNameInstanceId
Aliases:
Accepted values: All, Opened, Disconnected, Closed, Broken

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om de opdracht uit te voeren `Get-PSSession` . Als u deze para meter weglaat of een waarde van 0 (nul) opgeeft, wordt de standaard waarde 32 gebruikt. De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Int32
Parameter Sets: ComputerInstanceId, ComputerName, ConnectionUriInstanceId, ConnectionUri
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om de verbinding tot stand te brengen waarin de `Get-PSSession` opdracht wordt uitgevoerd. Standaard wordt SSL niet gebruikt. Als u deze para meter gebruikt maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.

Met deze para meter configureert u de tijdelijke verbinding die wordt gemaakt om een opdracht uit te voeren `Get-PSSession` met de para meter **ComputerName** .

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerInstanceId, ComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -VMId

Hiermee geeft u een ID-matrix van virtuele machines op. Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines. Als u de virtuele machines wilt zien die voor u beschikbaar zijn, gebruikt u de volgende opdracht:

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId, VMIdInstanceId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -VMName

Hiermee geeft u een matrix met namen van virtuele machines op. Met deze cmdlet wordt een interactieve sessie gestart met elk van de opgegeven virtuele machines. Gebruik de cmdlet om de virtuele machines weer te geven die voor u beschikbaar zijn `Get-VM` .

```yaml
Type: System.String[]
Parameter Sets: VMName, VMNameInstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. Management. Automation. Runspaces. PSSession

## OPMERKINGEN

- Met deze cmdlet worden door gebruikers beheerde sessies **PSSession** objecten, zoals de-cmdlets New-PSSession, `Enter-PSSession` en Invoke-Command. Er wordt geen door het systeem beheerde sessie opgehaald die wordt gemaakt wanneer u Power shell start.
- Vanaf Windows Power Shell 3,0 worden **PSSession** -objecten opgeslagen op de computer die zich aan de server zijde bevindt of het einde van een verbinding ontvangt. Voor het ophalen van de sessies die zijn opgeslagen op de lokale computer of een externe computer, brengt Power shell een tijdelijke sessie tot stand met de opgegeven computer en worden query opdrachten uitgevoerd in de sessie.
- Als u sessies wilt ontvangen die verbinding maken met een externe computer, gebruikt u de para meters **ComputerName** of **ConnectionUri** om de externe computer op te geven. Als u de sessies wilt filteren die `Get-PSSession` worden opgehaald, gebruikt u de para meters **naam** , **id** , **InstanceId** en **status** . Gebruik de resterende para meters voor het configureren van de tijdelijke sessie die `Get-PSSession` gebruikt.
- Wanneer u de para meter **ComputerName** of **ConnectionUri** gebruikt, worden `Get-PSSession` alleen sessies opgehaald van computers met Windows Power Shell 3,0 en latere versies van Power shell.
- De waarde van de eigenschap **State** van een **PSSession** is relatief ten opzichte van de huidige sessie.
  Als de waarde voor de **verbinding is verbroken** , betekent dit daarom dat de **PSSession** niet is verbonden met de huidige sessie. Het betekent echter niet dat de **PSSession** -verbinding met alle sessies is verbroken. Deze is mogelijk verbonden met een andere sessie. Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de **PSSession** via de huidige sessie en hoe u er opnieuw verbinding mee maakt.

Een **beschikbaarheids** waarde van **geen** geeft aan dat u verbinding kunt maken met de sessie. De waarde **bezet** geeft aan dat u geen verbinding kunt maken met de **PSSession** omdat deze is verbonden met een andere sessie.

Zie [RunspaceState Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspacestate)voor meer informatie over de waarden van de eigenschap **State** van sessies.

Zie [RunspaceAvailability Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de eigenschap **Beschik baarheid** van sessies.

## GERELATEERDE KOPPELINGEN

[Connect-PSSession](Connect-PSSession.md)

[Verbinding verbreken-PSSession](Disconnect-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Afsluiten-PSSession](Exit-PSSession.md)

[Invoke-opdracht](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

