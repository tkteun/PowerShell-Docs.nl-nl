---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disconnect-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-PSSession
ms.openlocfilehash: c0eed3d571cfb243c3f0ba4d0a4b7ddfaf4f04fb
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251553"
---
# Disconnect-PSSession

## SAMENVATTING
Verbreekt de verbinding met een sessie.

## SYNTAXIS

### Sessie (standaard)

```
Disconnect-PSSession [-Session] <PSSession[]> [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Naam

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Disconnect-PSSession` cmdlet verbreekt de verbinding met een Power shell-sessie ("PSSession"), zoals een start met behulp `New-PSSession` van de cmdlet, vanuit de huidige sessie. Als gevolg hiervan is de PSSession de status niet verbonden. U kunt verbinding maken met de losgekoppelde PSSession van de huidige sessie of van een andere sessie op de lokale computer of een andere computer.

De `Disconnect-PSSession` cmdlet verbreekt alleen open PSSessions die zijn verbonden met de huidige sessie. `Disconnect-PSSession` kan geen verbinding met een verbroken of gesloten PSSessions of interactieve PSSessions is gestart met de `Enter-PSSession` cmdlet en de verbinding met de PSSessions die is verbonden met andere sessies, kan niet worden verbroken.

Als u opnieuw verbinding wilt maken met een niet-verbonden PSSession, gebruikt u de `Connect-PSSession` `Receive-PSSession` cmdlets of.

Wanneer een PSSession wordt losgekoppeld, worden de opdrachten in de PSSession uitgevoerd totdat ze zijn voltooid, tenzij de PSSession een time-out heeft of de opdrachten in de PSSession worden geblokkeerd door een volledige uitvoer buffer. Als u de time-out voor inactiviteit wilt wijzigen, gebruikt u de para meter **IdleTimeoutSec** . Als u de uitvoer buffer modus wilt wijzigen, gebruikt u de para meter **OutputBufferingMode** u kunt ook de para meter **InDisconnectedSession** van de `Invoke-Command` cmdlet gebruiken om een opdracht uit te voeren in een niet-verbonden sessie.

Zie [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md)voor meer informatie over de functie voor verbroken sessies.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een sessie verbreken op naam

Met deze opdracht wordt de verbinding van de UpdateSession PSSession op de Server01-computer met de huidige sessie verbroken. De opdracht gebruikt de para meter **name** om de PSSession te identificeren.

```
PS> Disconnect-PSSession -Name UpdateSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  UpdateSession   Server01        Disconnected  Microsoft.PowerShell          None
```

De uitvoer laat zien dat de poging om de verbinding te verbreken is geslaagd. De sessie status is ontkoppeld en de beschik baarheid is geen, wat aangeeft dat de sessie niet bezet is en opnieuw verbinding kan maken.

### Voor beeld 2: een sessie van een specifieke computer verbreken

Met deze opdracht wordt de verbinding van de ITTask PSSession op de Server12-computer met de huidige sessie verbroken.
De ITTask-sessie is gemaakt in de huidige sessie en maakt verbinding met de Server12-computer. De opdracht gebruikt de `Get-PSSession` cmdlet om de sessie en de `Disconnect-PSSession` cmdlet te verkrijgen om deze te verbreken.

```
PS> Get-PSSession -ComputerName Server12 -Name ITTask |
  Disconnect-PSSession -OutputBufferingMode Drop -IdleTimeoutSec 86400
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  ITTask          Server12        Disconnected  ITTasks               None
```

De `Disconnect-PSSession` opdracht gebruikt de para meter **OutputBufferingMode** om de uitvoer modus in te stellen op **neerzetten**. Deze instelling zorgt ervoor dat het script dat wordt uitgevoerd in de sessie, zelfs kan blijven worden uitgevoerd als de buffer voor de sessie-uitvoer vol is. Omdat de uitvoer van het script naar een rapport op een bestands share wordt geschreven, kan een andere uitvoer zonder enige consequentie verloren gaan.

De opdracht gebruikt ook de para meter **IdleTimeoutSec** om de time-out voor inactiviteit van de sessie tot 24 uur uit te breiden. Deze instelling zorgt ervoor dat deze beheerder of andere beheerders opnieuw verbinding maken met de sessie om te controleren of het script is uitgevoerd en zo nodig problemen kan oplossen.

### Voor beeld 3: meerdere PSSessions gebruiken op meerdere computers

In deze reeks opdrachten ziet u hoe de `Disconnect-PSSession` cmdlet kan worden gebruikt in een bedrijfs scenario. In dit geval start een nieuwe technicus een script in een sessie op een externe computer en wordt er een probleem opgetreden. De technicus verbreekt de verbinding met de sessie, zodat een ervaren manager verbinding kan maken met de sessie en het probleem kan oplossen.

```
PS> $s = New-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
PS> Invoke-Command $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Get-PSSession -Name ITTask -ComputerName Srv1 | Disconnect-PSSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1 ITTask           Srv1            Disconnected  Microsoft.PowerShell          None

PS> Get-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None
 2 ITTask          Srv2            Opened        Microsoft.PowerShell     Available
 3 ITTask          Srv30           Opened        Microsoft.PowerShell     Available

PS> Get-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None

PS> $s = Connect-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
PS> Invoke-Command -Session $s {dir $home\Scripts\PatchStatusOutput.ps1}
PS> Invoke-Command -Session $s {mkdir $home\Scripts\PatchStatusOutput}
PS> Invoke-Command -Session $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Disconnect-PSSession -Session $s
```

De technicus begint met het maken van sessies op verschillende externe computers en het uitvoeren van een script in elke sessie. De eerste opdracht gebruikt de `New-PSSession` cmdlet om de ITTask-sessie op drie externe computers te maken. De-opdracht slaat de sessies op in de variabele $s. De tweede opdracht gebruikt de **filepath** -para meter van de `Invoke-Command` cmdlet om een script uit te voeren in de sessies in de $s variabele.

Het script dat wordt uitgevoerd op de Srv1-computer genereert onverwachte fouten. De technicus neemt contact op met zijn manager en vraagt om hulp. De Manager geeft de technicus de opdracht om de verbinding met de sessie te verbreken zodat hij deze kan onderzoeken. De tweede opdracht gebruikt de `Get-PSSession` cmdlet om de ITTask-sessie op de Srv1-computer op te halen en de `Disconnect-PSSession` cmdlet om deze te verbreken. Deze opdracht heeft geen invloed op de ITTask-sessies op de andere computers.

De derde opdracht gebruikt de `Get-PSSession` cmdlet om de ITTask-sessies op te halen. De uitvoer laat zien dat de ITTask-sessies op de Srv2-en Srv30-computers niet worden beïnvloed door de opdracht om de verbinding te verbreken.

De Manager meldt zich aan bij zijn thuis computer, maakt verbinding met zijn bedrijfs netwerk, start Power shell en gebruikt de `Get-PSSession` cmdlet om de ITTask-sessie op de Srv1-computer op te halen. Hij gebruikt de referenties van de technicus om toegang te krijgen tot de sessie.

Vervolgens gebruikt de Manager de `Connect-PSSession` cmdlet om verbinding te maken met de ITTask-sessie op de Srv1-computer. Met de opdracht wordt de sessie opgeslagen in de variabele $s.

De Manager gebruikt de `Invoke-Command` cmdlet om enkele diagnostische opdrachten uit te voeren in de sessie in de `$s` variabele. Hij erkent dat het script is mislukt omdat het geen vereiste map heeft gevonden.
De Manager gebruikt de `MkDir` functie om de map te maken en vervolgens wordt het script opnieuw gestart `Get-PatchStatus.ps1` en wordt de verbinding met de sessie verbroken. De manager rapporteert zijn bevindingen aan de technicus, stelt voor dat hij opnieuw verbinding maakt met de sessie voor het volt ooien van de taken en vraagt hem een opdracht toe te voegen aan het `Get-PatchStatus.ps1` script waarmee de vereiste map wordt gemaakt als deze niet bestaat.

### Voor beeld 4: de time-outwaarde voor een PSSession wijzigen

In dit voor beeld ziet u hoe u de waarde van de eigenschap **IdleTimeout** van een sessie kunt corrigeren zodat deze kan worden losgekoppeld.

De eigenschap time-out voor inactiviteit van een sessie is essentieel voor verbroken sessies, omdat deze bepaalt hoe lang een verbroken sessie wordt behouden voordat deze wordt verwijderd. U kunt de optie time-out voor inactiviteit instellen wanneer u een sessie maakt en wanneer u de verbinding verbreekt. De standaard waarden voor de time-out voor inactiviteit van een sessie worden ingesteld in de `$PSSessionOption` Voorkeurs variabele op de lokale computer en in de sessie configuratie op de externe computer. De waarden die voor de sessie zijn ingesteld, hebben voor rang op de waarden die zijn ingesteld in de sessie configuratie, maar sessie waarden mogen niet groter zijn dan de quota die zijn ingesteld in de sessie configuratie, zoals de **MaxIdleTimeoutMs** -waarde.

```
PS> $Timeout = New-PSSessionOption -IdleTimeout 172800000
PS> $s = New-PSSession -Computer Server01 -Name ITTask -SessionOption $Timeout
PS> Disconnect-PSSession -Session $s
Disconnect-PSSession : The session ITTask cannot be disconnected because the specified
idle timeout value 172800(seconds) is either greater than the server maximum allowed
43200 (seconds) or less that the minimum allowed60(seconds).  Choose an idle time out
value that is within the allowed range and try again.

PS> Invoke-Command -ComputerName Server01 {Get-PSSessionConfiguration Microsoft.PowerShell} |
 Format-List -Property *

Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/microsoft.powershell
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
SecurityDescriptorSddl        : O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 2147483647
Uri                           : http://schemas.microsoft.com/powershell/microsoft.powershell
SDKVersion                    : 2
Name                          : microsoft.powershell
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
ParentResourceUri             : http://schemas.microsoft.com/powershell/microsoft.powershell
Enabled                       : true
MaxShells                     : 25
MaxShellsPerUser              : 25
Permission                    : BUILTIN\Administrators AccessAllowed
PSComputerName                : localhost
RunspaceId                    : aea84310-6dbf-4c21-90ac-13980039925a
PSShowComputerName            : True


PS> $s.Runspace.ConnectionInfo
ConnectionUri                     : http://Server01/wsman
ComputerName                      : Server01
Scheme                            : http
Port                              : 80
AppName                           : /wsman
Credential                        :
ShellUri                          : http://schemas.microsoft.com/powershell/Microsoft.PowerShell
AuthenticationMechanism           : Default
CertificateThumbprint             :
MaximumConnectionRedirectionCount : 5
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
UseCompression                    : True
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
NoEncryption                      : False
UseUTF16                          : False
OutputBufferingMode               : Drop
IncludePortInSPN                  : False
Culture                           : en-US
UICulture                         : en-US
OpenTimeout                       : 180000
CancelTimeout                     : 60000
OperationTimeout                  : 180000
IdleTimeout                       : 172800000

PS> Disconnect-PSSession $s -IdleTimeoutSec 43200
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Disconnected  Microsoft.PowerShell          None

PS> $s.Runspace.ConnectionInfo.IdleTimeout
43200000
```

De eerste opdracht maakt gebruik van de `New-PSSessionOption` cmdlet om een sessie optie object te maken. De para meter **IdleTimeout** wordt gebruikt om een time-out van 48 uur (172800000 milliseconden) in te stellen. Met de opdracht slaat u het sessie optie object op in de variabele $Timeout.

De tweede opdracht gebruikt de `New-PSSession` cmdlet om de ITTask-sessie te maken op de Server01-computer. Met de opdracht wordt de sessie in de $s variabele opgeslagen. De waarde van de para meter **SessionOption** is de time-out van 48 uur in de variabele $timeout.

Met de derde opdracht wordt de ITTask-sessie in de variabele $s verbroken. De opdracht mislukt omdat de waarde van de time-out voor inactiviteit van de sessie groter is dan de **MaxIdleTimeoutMs** quota in de sessie configuratie. Omdat de time-out voor inactiviteit niet wordt gebruikt totdat de verbinding met de sessie wordt verbroken, kan deze schending niet worden gedetecteerd wanneer de sessie in gebruik is.

De vierde opdracht gebruikt de `Invoke-Command` cmdlet om een opdracht uit te voeren `Get-PSSessionConfiguration` voor de micro soft. Power shell-sessie configuratie op de Server01-computer. De opdracht gebruikt de `Format-List` cmdlet om alle eigenschappen van de sessie configuratie in een lijst weer te geven. In de uitvoer ziet u dat de eigenschap **MaxIdleTimeoutMS** , waarmee de Maxi maal toegestane **IdleTimeout** -waarde wordt ingesteld voor sessies die gebruikmaken van de sessie configuratie, 43200000 milliseconden (12 uur) is.

De vijfde opdracht haalt de sessie optie waarden van de sessie op in de variabele $s. De waarden van veel sessie opties zijn eigenschappen van de eigenschap **Connection info** van de eigenschap **runs Pace** van de sessie. De uitvoer laat zien dat de waarde van de eigenschap **IdleTimeout** van de sessie 172800000 milliseconden (48 uur) is, wat in strijd is met het **MaxIdleTimeoutMs** -quotum van 12 uur in de sessie configuratie. Als u dit conflict wilt oplossen, kunt u de para meter **configuratiepad** gebruiken om een andere sessie configuratie te selecteren of de para meter **IdleTimeout** gebruiken om de time-out voor de sessie niet actief te maken.

Met de zesde opdracht wordt de sessie verbroken. De para meter **IdleTimeoutSec** wordt gebruikt om de time-out voor inactiviteit in te stellen op het maximum van 12 uur.

Met de zevende opdracht wordt de waarde van de eigenschap **IdleTimeout** van de niet-verbonden sessie opgehaald, die wordt gemeten in milliseconden. De uitvoer bevestigt dat de opdracht is geslaagd.

## PARAMETERS

### -Id

Verbreekt de verbinding met sessies met de opgegeven sessie-ID. Typ een of meer Id's (gescheiden door komma's) of gebruik de operator Range (..) om een bereik van Id's op te geven.

Als u de ID van een sessie wilt ophalen, gebruikt u de `Get-PSSession` cmdlet. De exemplaar-ID wordt opgeslagen in de eigenschap **id** van de sessie.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IdleTimeoutSec

Hiermee wijzigt u de time-outwaarde voor niet-verbonden PSSession. Voer een waarde in seconden in. De minimum waarde is 60 (1 minuut).

De time-out voor inactiviteit bepaalt hoe lang de losgekoppelde PSSession op de externe computer wordt onderhouden. Wanneer de time-out is verlopen, wordt het PSSession verwijderd.

Ontkoppelde PSSessions worden beschouwd als niet-actief vanaf het moment dat ze worden losgekoppeld, zelfs als opdrachten worden uitgevoerd in de verbroken sessie.

De standaard waarde voor de time-out voor inactiviteit van een sessie wordt ingesteld op basis van de waarde van de eigenschap **IdleTimeoutMs** van de sessie configuratie. De standaard waarde is 7200000 milliseconden (2 uur).

De waarde van deze para meter heeft voor rang op de waarde van de eigenschap **IdleTimeout** van de variabele $PSSessionOption voor keur en de standaard waarde voor de time-out voor inactiviteit in de sessie configuratie. Deze waarde mag echter niet groter zijn dan de waarde van de eigenschap **MaxIdleTimeoutMs** van de sessie configuratie. De standaard waarde van **MaxIdleTimeoutMs** is 12 uur (43200000 milliseconden).

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Verbreekt de verbinding met sessies met de opgegeven exemplaar-Id's.

De exemplaar-ID is een GUID waarmee een sessie op een lokale of externe computer uniek wordt geïdentificeerd. De exemplaar-ID is uniek, zelfs op meerdere sessies op meerdere computers.

Als u de exemplaar-ID van een sessie wilt ophalen, gebruikt u de `Get-PSSession` cmdlet. De exemplaar-ID wordt opgeslagen in de eigenschap **InstanceId** van de sessie.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Verbreekt de verbinding met sessies met de opgegeven beschrijvende namen. Joker tekens zijn toegestaan.

Gebruik de cmdlet om de beschrijvende naam van een sessie te verkrijgen `Get-PSSession` . De beschrijvende naam wordt opgeslagen in de eigenschap **naam** van de sessie.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Sessie

De verbinding met de opgegeven PSSessions wordt verbroken. Voer PSSession-objecten in, zoals die worden `New-PSSession` geretourneerd door de cmdlet. U kunt ook een PSSession-object pipeen naar `Disconnect-PSSession` .

De `Get-PSSession` cmdlet kan alle PSSessions ophalen die eindigen op een externe computer, waaronder PSSessions die niet zijn verbonden en PSSessions die zijn verbonden met andere sessies op andere computers. `Disconnect-PSSession` koppelt alleen PSSession die zijn verbonden met de huidige sessie. Als u andere PSSessions naar wilt `Disconnect-PSSession` door sluizen, `Disconnect-PSSession` mislukt de opdracht.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ThrottleLimit

Hiermee stelt u de beperkings limiet voor de `Disconnect-PSSession` opdracht in.

De beperkings limiet is het maximum aantal gelijktijdige verbindingen dat tot stand kan worden gebracht om deze opdracht uit te voeren. Als u deze para meter weglaat of een waarde van 0 invoert, wordt de standaard waarde 32 gebruikt.

De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

Hiermee wordt bepaald hoe de uitvoer van de opdracht wordt beheerd in de verbroken sessie wanneer de uitvoer buffer vol is. De standaard waarde is **blok keren**.

Als de opdracht in de verbroken sessie uitvoer retourneert en de uitvoer buffer vol is, bepaalt de waarde van deze para meter effectief of de opdracht wordt uitgevoerd wanneer de sessie wordt verbroken. De waarde **blok** wordt onderbroken totdat de sessie opnieuw is verbonden. Met de waarde **Drop** kan de opdracht worden voltooid, hoewel gegevens verloren kunnen gaan. Wanneer u de waarde voor **neerzetten** gebruikt, moet u de uitvoer van de opdracht omleiden naar een bestand op schijf.

Geldige waarden zijn:

- **Blok keren** : wanneer de uitvoer buffer vol is, wordt de uitvoering onderbroken totdat de buffer leeg is.
- **Drop** : de uitvoering wordt voortgezet wanneer de uitvoer buffer vol is. Wanneer er een nieuwe uitvoer wordt opgeslagen, wordt de oudste uitvoer verwijderd.
- **Geen** : er is geen uitvoer buffer modus opgegeven. De waarde van de eigenschap **OutputBufferingMode** van de sessie configuratie wordt gebruikt voor de niet-verbonden sessie.

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Block
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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](./About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. Management. Automation. Runspaces. PSSession

U kunt een sessie door sluizen naar `Disconnect-PSSession` .

## UITVOER

### System. Management. Automation. Runspaces. PSSession

`Disconnect-PSSession` retourneert een object dat de sessie vertegenwoordigt waarvan de verbinding is verbroken.

## OPMERKINGEN

- De `Disconnect-PSSession` cmdlet werkt alleen als op de lokale en externe computers Power shell 3,0 of hoger wordt uitgevoerd.
- Als u de `Disconnect-PSSession` cmdlet gebruikt voor een niet-verbonden sessie, heeft de opdracht geen effect op de sessie en worden er geen fouten gegenereerd.
- Verbroken loop Back-sessies met interactieve beveiligings tokens (die zijn gemaakt met de para meter **EnableNetworkAccess** ) kunnen alleen opnieuw worden verbonden vanaf de computer waarop de sessie is gemaakt. Met deze beperking wordt de computer beschermd tegen kwaadwillende toegang.
- Wanneer u een PSSession verbreekt, wordt de sessie status **losgekoppeld** en is de beschik baarheid **geen**.

  De waarde van de eigenschap **State** is relatief ten opzichte van de huidige sessie. Als de waarde voor de **verbinding is verbroken** , betekent dit daarom dat de PSSession niet is verbonden met de huidige sessie. Het betekent echter niet dat de PSSession-verbinding met alle sessies is verbroken. Deze is mogelijk verbonden met een andere sessie. Gebruik de eigenschap **Beschik baarheid** om te bepalen of u verbinding kunt maken met de sessie of er opnieuw verbinding mee wilt maken.

  Een **beschikbaarheids** waarde van **geen** geeft aan dat u verbinding kunt maken met de sessie. De waarde **bezet** geeft aan dat u geen verbinding kunt maken met de PSSession omdat deze is verbonden met een andere sessie.

  Zie [RunspaceState Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.runspacestate)voor meer informatie over de waarden van de eigenschap **State** van sessies.

  Zie [RunspaceAvailability Enumeration (Engelstalig)](/dotnet/api/system.management.automation.runspaces.runspaceavailability)voor meer informatie over de waarden van de eigenschap **Beschik baarheid** van sessies.

## GERELATEERDE KOPPELINGEN

[Connect-PSSession](Connect-PSSession.md)

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

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

[about_Remote_Disconnected_Sessions](About/about_Remote_Disconnected_Sessions.md)
