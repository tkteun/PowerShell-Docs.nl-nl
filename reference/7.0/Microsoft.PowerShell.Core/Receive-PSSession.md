---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-PSSession
ms.openlocfilehash: 5c7783cb6f865aead9aae7ae0df77d9ee2db7b16
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391354"
---
# Receive-PSSession

## SAMENVATTING

Hiermee worden de resultaten van opdrachten in verbroken sessies opgehaald

## SYNTAXIS

### Sessie (standaard)

```
Receive-PSSession [-Session] <PSSession> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### Id

```
Receive-PSSession [-Id] <Int32> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### ComputerSessionName

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerInstanceId

```
Receive-PSSession [-ComputerName] <String> [-ApplicationName <String>] [-ConfigurationName <String>]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [-Port <Int32>]
 [-UseSSL] [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriSessionName

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ConnectionUriInstanceId

```
Receive-PSSession [-ConfigurationName <String>] [-ConnectionUri] <Uri> [-AllowRedirection]
 -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [-SessionOption <PSSessionOption>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Receive-PSSession -InstanceId <Guid> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Sessie naam

```
Receive-PSSession -Name <String> [-OutTarget <OutTarget>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Receive-PSSession` cmdlet haalt de resultaten op van de opdrachten die worden uitgevoerd in Power shell-sessies ( **PSSession** ) die zijn losgekoppeld. Als de sessie momenteel is verbonden, worden `Receive-PSSession` de resultaten opgehaald van opdrachten die werden uitgevoerd toen de verbinding met de sessie werd verbroken. Als de sessie nog steeds is verbroken, `Receive-PSSession` maakt verbinding met de sessie, worden alle opdrachten die zijn onderbroken, hervat en worden de resultaten opgehaald van de opdrachten die in de sessie worden uitgevoerd.

Deze cmdlet is geïntroduceerd in Power Shell 3,0.

U kunt een gebruiken `Receive-PSSession` naast of in plaats van een `Connect-PSSession` opdracht.
`Receive-PSSession` kan verbinding maken met elke verbroken of opnieuw verbonden sessie die is gestart in andere sessies of op andere computers.

`Receive-PSSession` werkt op **PSSessions** die opzettelijk zijn losgekoppeld met de `Disconnect-PSSession` cmdlet of de `Invoke-Command` para meter **InDisconnectedSession** . Of de verbinding met een netwerk onderbreking per ongeluk verbroken.

Als u de `Receive-PSSession` cmdlet gebruikt om verbinding te maken met een sessie waarin geen opdrachten worden uitgevoerd of onderbroken, `Receive-PSSession` maakt verbinding met de sessie, maar worden geen uitvoer of fouten geretourneerd.

Zie [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)voor meer informatie over de functie voor verbroken sessies.

Enkele voor beelden gebruiken splatting om de lengte van de lijn te verkleinen en de Lees baarheid te verbeteren. Zie [about_Splatting](./About/about_Splatting.md)voor meer informatie.

## VOORBEELDEN

### Voor beeld 1: verbinding maken met een PSSession

In dit voor beeld wordt verbinding gemaakt met een sessie op een externe computer en worden de resultaten opgehaald van opdrachten die in een sessie worden uitgevoerd.

```powershell
Receive-PSSession -ComputerName Server01 -Name ITTask
```

De `Receive-PSSession` specificeert de externe computer met de para meter **ComputerName** . De para meter **name** identificeert de ITTask-sessie op de Server01-computer. In het voor beeld worden de resultaten opgehaald van opdrachten die werden uitgevoerd in de ITTask-sessie.

Omdat de opdracht geen gebruik maakt van de para meter **outtarget** , worden de resultaten weer gegeven op de opdracht regel.

### Voor beeld 2: resultaten van alle opdrachten in sessies zonder verbinding ophalen

In dit voor beeld worden de resultaten opgehaald van alle opdrachten die worden uitgevoerd in alle verbroken sessies op twee externe computers.

Als een sessie niet is verbroken of als er geen opdrachten worden uitgevoerd, `Receive-PSSession` wordt er geen verbinding met de sessie gemaakt en worden er geen uitvoer of fouten geretourneerd.

```powershell
Get-PSSession -ComputerName Server01, Server02 | Receive-PSSession
```

`Get-PSSession` maakt gebruik van de para meter **ComputerName** om de externe computers op te geven. De objecten worden naar beneden verzonden in de pijp lijn `Receive-PSSession` .

### Voor beeld 3: de resultaten ophalen van een script dat wordt uitgevoerd in een sessie

In dit voor beeld wordt de `Receive-PSSession` cmdlet gebruikt om de resultaten op te halen van een script dat werd uitgevoerd in de sessie van een externe computer.

```powershell
$parms = @{
  ComputerName = "Server01"
  Name = "ITTask"
  OutTarget = "Job"
  JobName = "ITTaskJob01"
  Credential = "Domain01\Admin01"
}
Receive-PSSession @parms
```

```Output
Id     Name            State         HasMoreData     Location
--     ----            -----         -----------     --------
16     ITTaskJob01     Running       True            Server01
```

De opdracht maakt gebruik van de para meters **ComputerName** en **name** om de verbroken sessie te identificeren.
De para meter **outtarget** wordt gebruikt met de waarde taak om `Receive-PSSession` de resultaten te retour neren als een taak. De **JobName** para meter geeft een naam voor de taak in de opnieuw verbonden sessie.
De para meter **Credential** voert de `Receive-PSSession` opdracht uit met de machtigingen van een domein beheerder.

In de uitvoer ziet u dat `Receive-PSSession` de resultaten als een taak in de huidige sessie zijn geretourneerd. Als u de resultaten van de taak wilt weer geven, gebruikt u een `Receive-Job` opdracht

### Voor beeld 4: resultaten ophalen na een storing in het netwerk

In dit voor beeld wordt de `Receive-PSSession` cmdlet gebruikt om de resultaten van een taak op te halen nadat een netwerk onderbreking een sessie verbinding verstoort. Power shell probeert automatisch opnieuw verbinding te maken met de sessie per seconde voor de komende vier minuten. de taak wordt alleen uitgevoerd als alle pogingen van het interval van vier minuten mislukken.

```
PS> $s = New-PSSession -ComputerName Server01 -Name AD -ConfigurationName ADEndpoint
PS> $s

Id  Name   ComputerName    State        ConfigurationName     Availability
--  ----   ------------    -----        -----------------     ------------
8   AD      Server01       Opened       ADEndpoint               Available


PS> Invoke-Command -Session $s -FilePath \\Server12\Scripts\SharedScripts\New-ADResolve.ps1

Running "New-ADResolve.ps1"

# Network outage
# Restart local computer
# Network access is not re-established within 4 minutes


PS> Get-PSSession -ComputerName Server01

Id  Name   ComputerName    State          ConfigurationName      Availability
--  ----   ------------    -----          -----------------      ------------
1  Backup  Server01        Disconnected   Microsoft.PowerShell           None
8  AD      Server01        Disconnected   ADEndpoint                     None


PS> Receive-PSSession -ComputerName Server01 -Name AD -OutTarget Job -JobName AD

Job Id   Name      State         HasMoreData     Location
--       ----      -----         -----------     --------
16       ADJob     Running       True            Server01


PS> Get-PSSession -ComputerName Server01

Id  Name    ComputerName    State         ConfigurationName     Availability
--  ----    ------------    -----         -----------------     ------------
1  Backup   Server01        Disconnected  Microsoft.PowerShell          Busy
8  AD       Server01        Opened        ADEndpoint               Available
```

Met de `New-PSSession` cmdlet wordt een sessie gemaakt op de Server01-computer en wordt de sessie opgeslagen in de `$s` variabele. De `$s` variabele geeft aan dat de **status** is geopend en de **Beschik baarheid** beschikbaar is. Deze waarden geven aan dat u verbonden bent met de sessie en dat er opdrachten kunnen worden uitgevoerd in de sessie.

Met de `Invoke-Command` cmdlet wordt een script uitgevoerd in de sessie in de `$s` variabele. Het script begint met het uitvoeren en retour neren van gegevens, maar er treedt een netwerk storing op waardoor de sessie wordt onderbroken. De gebruiker moet de sessie afsluiten en de lokale computer opnieuw opstarten.

Wanneer de computer opnieuw wordt opgestart, start Power shell en voert de gebruiker een `Get-PSSession` opdracht uit om sessies op de Server01-computer op te halen. In de uitvoer ziet u dat de **ad** -sessie nog bestaat op de Server01-computer. De **status** geeft aan dat de **ad** -sessie is beëindigd. De **beschikbaarheids** waarde geen, geeft aan dat de sessie niet is verbonden met een client sessie.

`Receive-PSSession`Met de cmdlet wordt opnieuw verbinding gemaakt met de **ad** -sessie en worden de resultaten opgehaald van het script dat is uitgevoerd in de sessie. De opdracht gebruikt de para meter **outtarget** om de resultaten aan te vragen in een taak met de naam **ADJob**. De opdracht retourneert een taak object en de uitvoer geeft aan dat het script nog steeds wordt uitgevoerd.

De `Get-PSSession` cmdlet wordt gebruikt om de taak status te controleren. De uitvoer bevestigt dat de `Receive-PSSession` cmdlet opnieuw is verbonden met de **ad** -sessie, die nu is geopend en beschikbaar is voor-opdrachten. En de uitvoering van het script wordt hervat en de resultaten van het script worden opgehaald.

### Voor beeld 5: opnieuw verbinding maken met verbroken sessies

In dit voor beeld wordt de `Receive-PSSession` cmdlet gebruikt om opnieuw verbinding te maken met sessies die opzettelijk zijn losgekoppeld en de resultaten te krijgen van taken die in de sessies werden uitgevoerd.

```
PS> $parms = @{
      InDisconnectedSession = $True
      ComputerName = "Server01", "Server02", "Server30"
      FilePath = "\\Server12\Scripts\SharedScripts\Get-BugStatus.ps1"
      Name = "BugStatus"
      SessionOption = @{IdleTimeout = 86400000}
      ConfigurationName = "ITTasks"
    }
PS> Invoke-Command @parms
PS> Exit


PS> $s = Get-PSSession -ComputerName Server01, Server02, Server30 -Name BugStatus
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Disconnected  ITTasks                       None
8  ITTask  Server02        Disconnected  ITTasks                       None
2  ITTask  Server30        Disconnected  ITTasks                       None


PS> $Results = Receive-PSSession -Session $s
PS> $s

Id  Name   ComputerName    State         ConfigurationName     Availability
--  ----   ------------    -----         -----------------     ------------
1  ITTask  Server01        Opened        ITTasks                  Available
8  ITTask  Server02        Opened        ITTasks                  Available
2  ITTask  Server30        Opened        ITTasks                  Available


PS> $Results

Bug Report - Domain 01
----------------------
ComputerName          BugCount          LastUpdated
--------------        ---------         ------------
Server01              121               Friday, December 30, 2011 5:03:34 PM
```

`Invoke-Command`Met de cmdlet wordt een script uitgevoerd op drie externe computers. Omdat in het script gegevens uit meerdere data bases worden verzameld en samenvatten, neemt het script vaak een lange tijd in beslag om te worden voltooid. De opdracht maakt gebruik van de para meter **InDisconnectedSession** waarmee de scripts worden gestart. vervolgens wordt de verbinding met de sessies onmiddellijk verbroken. De para meter **SessionOption** breidt de waarde **IdleTimeout** van de niet-verbonden sessie uit. Sessies waarbij de verbinding is verbroken, worden niet meer gebruikt vanaf het moment dat de verbinding wordt verbroken. Het is belang rijk om de time-out voor inactiviteit lang genoeg in te stellen, zodat de opdrachten kunnen worden voltooid en u opnieuw verbinding kunt maken met de sessie. U kunt de **IdleTimeout** alleen instellen wanneer u de **PSSession** maakt en deze alleen wijzigen wanneer u de verbinding verbreekt. U kunt de waarde voor **IdleTimeout** niet wijzigen wanneer u verbinding maakt met een **PSSession** of de resultaten ontvangt. Na het uitvoeren van de opdracht, sluit de gebruiker Power shell af en sluit de computer.

De volgende dag, de gebruiker hervat Windows, start Power shell en gebruikt `Get-PSSession` om de sessies te verkrijgen waarin de scripts worden uitgevoerd. De opdracht identificeert de sessies op basis van de computer naam, sessie naam en de naam van de sessie configuratie en slaat de sessies op in de `$s` variabele. De waarde van de `$s` variabele wordt weer gegeven en er wordt aangegeven dat de sessies zijn losgekoppeld, maar niet actief.

De `Receive-PSSession` cmdlet maakt verbinding met de sessies in de `$s` variabele en haalt de resultaten op.
Met de opdracht worden de resultaten opgeslagen in de `$Results` variabele. De `$s` variabele wordt weer gegeven en er wordt aangegeven dat de sessies zijn verbonden en beschikbaar zijn voor opdrachten.

De resultaten van het script in de `$Results` variabele worden weer gegeven in de Power shell-console. Als een van de resultaten onverwacht is, kan de gebruiker opdrachten uitvoeren in de sessies om de hoofd oorzaak te onderzoeken.

### Voor beeld 6: een taak uitvoeren in een sessie zonder verbinding

In dit voor beeld ziet u wat er gebeurt met een taak die wordt uitgevoerd in een sessie waarbij de verbinding is verbroken.

```
PS> $s = New-PSSession -ComputerName Server01 -Name Test
PS> $j = Invoke-Command -Session $s { 1..1500 | Foreach-Object {"Return $_"; sleep 30}} -AsJob
PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Running       True            Server01


PS> $s | Disconnect-PSSession

Id Name   ComputerName    State         ConfigurationName     Availability
-- ----   ------------    -----         -----------------     ------------
1  Test   Server01        Disconnected  Microsoft.PowerShell          None


PS> $j

Id     Name           State         HasMoreData     Location
--     ----           -----         -----------     --------
16     Job1           Disconnected  True            Server01


PS> Receive-Job $j -Keep

Return 1
Return 2


PS> $s2 = Connect-PSSession -ComputerName Server01 -Name Test
PS> $j2 = Receive-PSSession -ComputerName Server01 -Name Test
PS> Receive-Job $j

Return 3
Return 4
```

De `New-PSSession` cmdlet maakt de test sessie op de Server01-computer. Met de opdracht wordt de sessie opgeslagen in de `$s` variabele.

Met de `Invoke-Command` cmdlet wordt een opdracht uitgevoerd in de sessie in de `$s` variabele. De opdracht gebruikt de para meter **AsJob** om de opdracht uit te voeren als een taak en het taak object in de huidige sessie te maken.
De opdracht retourneert een taak object dat is opgeslagen in de `$j` variabele. Met de `$j` variabele wordt het taak object weer gegeven.

Het sessie object in de `$s` variabele wordt verzonden naar de pijp lijn `Disconnect-PSSession` en de sessie wordt verbroken.

De `$j` variabele wordt weer gegeven en toont het effect van het verbreken van de verbinding tussen het taak object in de `$j` variabele. De taak status is nu verbroken.

De `Receive-Job` wordt uitgevoerd op de taak in de `$j` variabele. In de uitvoer ziet u dat de taak is gestart met het retour neren van de uitvoer voordat de sessie en de taak zijn losgekoppeld.

De `Connect-PSSession` cmdlet wordt uitgevoerd in dezelfde client sessie. Met de opdracht wordt opnieuw verbinding gemaakt met de test sessie op de Server01-computer en wordt de sessie opgeslagen in de `$s2` variabele.

De `Receive-PSSession` cmdlet haalt de resultaten op van de taak die werd uitgevoerd in de sessie. Omdat de opdracht wordt uitgevoerd in dezelfde sessie, `Receive-PSSession` retourneert de resultaten standaard als een taak en gebruikt hetzelfde taak object opnieuw. Met de opdracht wordt de taak opgeslagen in de `$j2` variabele. De `Receive-Job` cmdlet haalt de resultaten van de taak op in de `$j` variabele.

## PARAMETERS

### -AllowRedirection

Geeft aan dat deze cmdlet omleiding van deze verbinding met een alternatieve URI (Uniform Resource Identifier) mogelijk maakt.

Wanneer u de para meter **ConnectionURI** gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI. Standaard worden verbindingen niet door Power shell omgeleid, maar u kunt deze para meter gebruiken om de verbinding in te scha kelen.

U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de waarde van de **MaximumConnectionRedirectionCount** -sessie optie te wijzigen. Gebruik de para meter **MaximumRedirection** van de `New-PSSessionOption` cmdlet of stel de eigenschap **MaximumConnectionRedirectionCount** van de `$PSSessionOption` Voorkeurs variabele in. De standaard waarde is 5.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ApplicationName

Hiermee geeft u een toepassing op. Deze cmdlet maakt alleen verbinding met sessies die gebruikmaken van de opgegeven toepassing.

Voer het segment van de toepassings naam van de verbindings-URI in. In de volgende verbindings-URI is WSMan bijvoorbeeld de naam van de toepassing: `http://localhost:5985/WSMAN` .

De toepassings naam van een sessie wordt opgeslagen in de eigenschap **runs Pace. Connection info. appName** van de sessie.

De waarde van de para meter wordt gebruikt voor het selecteren en filteren van sessies. De toepassing die door de sessie wordt gebruikt, wordt niet gewijzigd.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Verificatie

Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties in de opdracht om opnieuw verbinding te maken met een verbroken sessie. De aanvaardbare waarden voor deze parameter zijn:

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
> CredSSP-verificatie (Credential Security Support Provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om verbinding te maken met de verbroken sessie. Voer de vinger afdruk van het certificaat in.

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Certificaten kunnen alleen worden toegewezen aan lokale gebruikers accounts en werken niet met domein accounts.

Als u een vinger afdruk van een certificaat wilt ontvangen, gebruikt u een- `Get-Item` of- `Get-ChildItem` opdracht in het Power shell- `Cert:` station.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de computer waarop de verbroken sessie wordt opgeslagen. Sessies worden opgeslagen op de computer die zich aan de server zijde bevindt of die het einde van een verbinding ontvangt. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name (FQDN) van een computer.
Joker tekens zijn niet toegestaan. Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt ( `.` ), `$env:COMPUTERNAME` of localhost.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Configuratiepad

Hiermee geeft u de naam van een sessie configuratie. Deze cmdlet maakt alleen verbinding met sessies die gebruikmaken van de opgegeven sessie configuratie.

Voer een configuratie naam of de volledig gekwalificeerde resource-URI in voor een sessie configuratie. Als u alleen de configuratie naam opgeeft, wordt de volgende schema-URI voor het voor voegsel geplaatst:

`http://schemas.microsoft.com/powershell`.

De configuratie naam van een sessie wordt opgeslagen in de eigenschap **configuratiepad** van de sessie.

De waarde van de para meter wordt gebruikt voor het selecteren en filteren van sessies. De sessie configuratie die door de sessie wordt gebruikt, wordt niet gewijzigd.

Zie [about_Session_Configurations](./About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ConnectionUri

Hiermee geeft u een URI op die het verbindings eindpunt definieert dat wordt gebruikt om opnieuw verbinding te maken met de verbroken sessie.

De URI moet volledig gekwalificeerd zijn. De indeling van de teken reeks is als volgt:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

De standaard waarde is als volgt:

`http://localhost:5985/WSMAN`

Als u geen verbindings-URI opgeeft, kunt u de para meters **UseSSL** , **ComputerName** , **Port** en **ApplicationName** gebruiken om de verbindings-URI-waarden op te geven.

Geldige waarden voor het **transport** segment van de URI zijn http en HTTPS. Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS. Als u de standaard poorten voor externe communicatie van Power shell wilt gebruiken, geeft u poort 5985 voor HTTP of 5986 op voor HTTPS.

Als de doel computer de verbinding omleidt naar een andere URI, wordt de omleiding door Power shell voor komen, tenzij u de para meter **AllowRedirection** in de opdracht gebruikt.

```yaml
Type: System.Uri
Parameter Sets: ConnectionUriSessionName, ConnectionUriInstanceId
Aliases: URI, CU

Required: True
Position: 0
Default value: http://localhost:5985/WSMAN
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om verbinding te maken met de verbroken sessie. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee geeft u de ID van een niet-verbonden sessie. De **id-** para meter werkt alleen wanneer de verbroken sessie eerder is verbonden met de huidige sessie.

Deze para meter is geldig, maar niet effectief, wanneer de sessie wordt opgeslagen op de lokale computer, maar niet is verbonden met de huidige sessie.

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u de exemplaar-ID van de niet-verbonden sessie. De exemplaar-ID is een unieke aanduiding voor een **PSSession** op een lokale of externe computer. De exemplaar-ID wordt opgeslagen in de eigenschap **InstanceId** van de **PSSession**.

```yaml
Type: System.Guid
Parameter Sets: ComputerInstanceId, ConnectionUriInstanceId, InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JobName

Hiermee geeft u een beschrijvende naam op voor de taak die `Receive-PSSession` wordt geretourneerd.

`Receive-PSSession` retourneert een taak wanneer de waarde van de para meter **outtarget** een taak is of de taak die wordt uitgevoerd in de verbroken sessie, is gestart in de huidige sessie.

Als de taak die in de verbroken sessie wordt uitgevoerd in de huidige sessie is gestart, gebruikt Power shell het oorspronkelijke taak object in de sessie opnieuw en wordt de waarde van de para meter **JobName** genegeerd.

Als de taak die wordt uitgevoerd in de verbroken sessie is gestart in een andere sessie, maakt Power shell een nieuw taak object. Er wordt een standaard naam gebruikt, maar u kunt deze para meter gebruiken om de naam te wijzigen.

Als de standaard waarde of expliciete waarde van de para meter **outtarget** niet taak is, is de opdracht geslaagd, maar de para meter **JobName** heeft geen effect.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de beschrijvende naam van de sessie zonder verbinding.

```yaml
Type: System.String
Parameter Sets: ComputerSessionName, ConnectionUriSessionName, SessionName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Outdoel

Hiermee wordt bepaald hoe de sessie resultaten worden geretourneerd. De aanvaardbare waarden voor deze parameter zijn:

- **Taak**. Retourneert de resultaten asynchroon in een taak object. U kunt de para meter **JobName** gebruiken om een naam of een nieuwe naam voor de taak op te geven.
- **Host**. Retourneert de resultaten naar de opdracht regel (synchroon). Als de opdracht wordt hervat of de resultaten uit een groot aantal objecten bestaan, kan de reactie vertraging oplopen.

De standaard waarde van de para meter **outtarget** is host. Als de opdracht die wordt ontvangen in een verbroken sessie is gestart in de huidige sessie, is de standaard waarde van de para meter **outtarget** de vorm waarin de opdracht is gestart. Als de opdracht als een taak is gestart, wordt deze als een taak geretourneerd. Als dat niet het geval is, wordt de standaard waarde naar het hostprogramma geretourneerd.

Normaal gesp roken geeft het hostprogramma geretourneerde objecten zonder vertraging weer op de opdracht regel, maar dit kan variëren.

```yaml
Type: Microsoft.PowerShell.Commands.OutTarget
Parameter Sets: (All)
Aliases:
Accepted values: Default, Host, Job

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Hiermee geeft u de netwerk poort van de externe computer op die wordt gebruikt om opnieuw verbinding te maken met de sessie. Als u verbinding wilt maken met een externe computer, moet deze Luis teren op de poort die door de verbinding wordt gebruikt. De standaard poorten zijn 5985, de WinRM-poort voor HTTP en 5986, de WinRM-poort voor HTTPS.

Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren. Als u de listener wilt configureren, typt u de volgende twee opdrachten bij de Power shell-prompt:

`Remove-Item -Path WSMan:\Localhost\listener\listener* -Recurse`

`New-Item -Path WSMan:\Localhost\listener -Transport http -Address * -Port \<port-number\>`

Gebruik de para meter **poort** alleen als dit nodig is. De poort die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers.

```yaml
Type: System.Int32
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessie

Hiermee geeft u de sessie zonder verbinding. Voer een variabele in die de **PSSession** bevat of een opdracht die de **PSSession** , zoals een opdracht, maakt of ontvangt `Get-PSSession` .

```yaml
Type: System.Management.Automation.Runspaces.PSSession
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

Zie voor een beschrijving van de sessie opties die de standaard waarden bevatten `New-PSSessionOption` . Zie [about_Preference_Variables](./About/about_Preference_Variables.md)voor meer informatie over de **$PSSessionOption** voorkeurs variabele. Zie [about_Session_Configurations](./About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerSessionName, ComputerInstanceId, ConnectionUriSessionName, ConnectionUriInstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Geeft aan dat deze cmdlet het Secure Sockets Layer-Protocol (SSL) gebruikt om verbinding te maken met de verbroken sessie. SSL wordt standaard niet gebruikt.

WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden. **UseSSL** is een extra bescherming waarmee de gegevens worden verzonden via een HTTPS-verbinding in plaats van via een http-verbinding.

Als u deze para meter gebruikt en SSL niet beschikbaar is op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerSessionName, ComputerInstanceId
Aliases:

Required: False
Position: Named
Default value: False
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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

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

U kunt sessie objecten door sluizen naar deze cmdlet, zoals objecten die door de `Get-PSSession` cmdlet worden geretourneerd.

### System. Int32

U kunt sessie-Id's door sluizen naar deze cmdlet.

### System. GUID

U kunt de exemplaar-Id's van sessies met deze cmdlet door sluizen.

### System. String

U kunt sessie namen aan deze cmdlet door sluizen.

## UITVOER

### System. Management. Automation. job of PSObject

Met deze cmdlet worden de resultaten geretourneerd van opdrachten die zijn uitgevoerd in de verbroken sessie, indien van toepassing. Als de waarde of de standaard waarde van de para meter **outtarget** een taak is, `Receive-PSSession` wordt een taak object geretourneerd. Anders worden objecten geretourneerd die de opdracht resultaten vertegenwoordigen.

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

`Receive-PSSession` Hiermee worden alleen resultaten opgehaald van sessies die zijn losgekoppeld. Alleen sessies die zijn verbonden met of eindigen op computers waarop Power Shell 3,0 of hoger wordt uitgevoerd, kunnen worden losgekoppeld en opnieuw worden aangesloten.

Als de opdrachten die werden uitgevoerd in de verbroken sessie geen resultaten genereren of als de resultaten al naar een andere sessie zijn geretourneerd, `Receive-PSSession` wordt er geen uitvoer gegenereerd.

De modus uitvoer buffer van een sessie bepaalt hoe opdrachten in de sessie uitvoer beheren wanneer de sessie wordt verbroken. Wanneer de waarde van de **OutputBufferingMode** -optie van de sessie wordt verwijderd en de uitvoer buffer vol is, begint de opdracht uitvoer te verwijderen. `Receive-PSSession` kan deze uitvoer niet herstellen. Zie de Help-artikelen voor de cmdlets [New-PSSessionOption](New-PSSessionOption.md) en [New-PSTransportOption](New-PSTransportOption.md) voor meer informatie over de optie voor de modus uitvoer buffer.

U kunt de time-outwaarde van een **PSSession** niet wijzigen wanneer u verbinding maakt met de **PSSession** of resultaten ontvangt. De para meter **SessionOption** van `Receive-PSSession` maakt een **SessionOption** -object met een **IdleTimeout** -waarde. De waarde **IdleTimeout** van het object **SessionOption** en de waarde **IdleTimeout** van de `$PSSessionOption` variabele wordt echter genegeerd wanneer verbinding wordt gemaakt met een **PSSession** of als er resultaten worden ontvangen.

- U kunt de time-out voor inactiviteit van een **PSSession** instellen en wijzigen wanneer u de **PSSession** maakt met behulp van de- `New-PSSession` of `Invoke-Command` -cmdlets en wanneer u de verbinding met de **PSSession** verbreekt.
- De eigenschap **IdleTimeout** van een **PSSession** is essentieel voor verbroken sessies, omdat deze bepaalt hoe lang een verbroken sessie op de externe computer wordt onderhouden. Verbroken sessies worden beschouwd als niet-actief vanaf het moment dat ze worden losgekoppeld, zelfs als opdrachten worden uitgevoerd in de verbroken sessie.

Als u begint met het starten van een taak in een externe sessie met behulp van de para meter **AsJob** van de `Invoke-Command` cmdlet, wordt het taak object gemaakt in de huidige sessie, zelfs als de taak wordt uitgevoerd in de externe sessie. Als u de externe sessie verbreekt, wordt het taak object in de huidige sessie losgekoppeld van de taak. Het taak object bevat alle resultaten die zijn geretourneerd, maar er worden geen nieuwe resultaten van de taak in de verbroken sessie ontvangen.

Als een andere client verbinding maakt met de sessie die de actieve taak bevat, zijn de resultaten die zijn geleverd aan het oorspronkelijke taak object in de oorspronkelijke sessie niet beschikbaar in de zojuist verbonden sessie. Alleen resultaten die niet aan het oorspronkelijke taak object zijn geleverd, zijn beschikbaar in de opnieuw verbonden sessie.

Als u een script in een sessie start en vervolgens de verbinding met de sessie verbreekt, zijn alle resultaten die het script naar de sessie levert voordat de verbinding wordt verbroken, niet beschikbaar voor een andere client die verbinding maakt met de sessie.

Gebruik de para meter **InDisconnectedSession** van de cmdlet om gegevens verlies te voor komen in sessies die u wilt verbreken `Invoke-Command` . Omdat deze para meter voor komt dat resultaten worden geretourneerd naar de huidige sessie, zijn alle resultaten beschikbaar wanneer de sessie opnieuw wordt verbonden.

U kunt gegevens verlies ook voor komen door met behulp van de `Invoke-Command` cmdlet een `Start-Job` opdracht uit te voeren in de externe sessie. In dit geval wordt het taak object in de externe sessie gemaakt. U kunt de cmdlet niet gebruiken `Receive-PSSession` om de taak resultaten op te halen. Gebruik in plaats daarvan de `Connect-PSSession` cmdlet om verbinding te maken met de sessie en gebruik vervolgens de `Invoke-Command` cmdlet om een `Receive-Job` opdracht uit te voeren in de sessie.

Wanneer een sessie die een actieve taak bevat losgekoppeld en vervolgens opnieuw verbinding maakt, wordt het oorspronkelijke taak object opnieuw gebruikt als de verbinding met de taak is verbroken en opnieuw verbinding met dezelfde sessie wordt gemaakt en de opdracht om opnieuw verbinding te maken geen nieuwe taak naam opgeeft. Als de sessie opnieuw wordt verbonden met een andere client sessie of als er een nieuwe taak naam is opgegeven, maakt Power shell een nieuw taak object voor de nieuwe sessie.

Wanneer u een **PSSession** verbreekt, wordt de sessie status losgekoppeld en is de beschik baarheid geen.

- De waarde van de eigenschap **State** is relatief ten opzichte van de huidige sessie. Als de waarde voor de verbinding is verbroken, betekent dit dat de **PSSession** niet is verbonden met de huidige sessie. Dit betekent echter niet dat de **PSSession** van de verbinding met alle sessies is verbroken. Deze is mogelijk verbonden met een andere sessie.
  Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de sessie of er opnieuw verbinding mee wilt maken.
- Een **beschikbaarheids** waarde van geen geeft aan dat u verbinding kunt maken met de sessie. De waarde bezet geeft aan dat u geen verbinding kunt maken met de **PSSession** , omdat deze is verbonden met een andere sessie.
- Zie [RunspaceState](/dotnet/api/system.management.automation.runspaces.runspacestate)voor meer informatie over de waarden van de eigenschap **State** van sessies.
- Zie [RunspaceAvailability](/dotnet/api/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de eigenschap **Beschik baarheid** van sessies.

## GERELATEERDE KOPPELINGEN

[about_PSSessions](./About/about_PSSessions.md)

[about_Remote](./About/about_Remote.md)

[about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)

[about_Session_Configurations](./About/about_Session_Configurations.md)

[Connect-PSSession](Connect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Afsluiten-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-opdracht](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Remove-PSSession](Remove-PSSession.md)
