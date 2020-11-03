---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pstransportoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSTransportOption
ms.openlocfilehash: 9257c0a1829cc9cc85029f7c6fdc8e61b0ed7e56
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251475"
---
# New-PSTransportOption

## SAMENVATTING

Hiermee maakt u een object dat geavanceerde opties bevat voor een sessie configuratie.

## SYNTAXIS

```
New-PSTransportOption [-MaxIdleTimeoutSec <Int32>] [-ProcessIdleTimeoutSec <Int32>] [-MaxSessions <Int32>]
 [-MaxConcurrentCommandsPerSession <Int32>] [-MaxSessionsPerUser <Int32>] [-MaxMemoryPerSessionMB <Int32>]
 [-MaxProcessesPerSession <Int32>] [-MaxConcurrentUsers <Int32>] [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **New-PSTransportOption** maakt u een object dat transport opties bevat voor sessie configuraties.
U kunt het object gebruiken als de waarde van de *TransportOption* -para meter van cmdlets waarmee een sessie configuratie wordt gemaakt of gewijzigd, zoals de Register-PSSessionConfiguration en Set-PSSessionConfiguration-cmdlets.

U kunt ook de instellingen voor transport opties wijzigen door de waarden van de eigenschappen van de sessie configuratie te bewerken in het WSMan:-station.
Zie WSMan-provider voor meer informatie.

De opties voor sessie configuratie vertegenwoordigen de sessie waarden die zijn ingesteld aan de server zijde of het ontvangende einde van een externe verbinding.
Aan de client zijde of het verzenden van het einde van de verbinding, kan de sessie optie waarden instellen wanneer de sessie wordt gemaakt, of wanneer de client de verbinding met de sessie verbreekt of de verbinding opnieuw tot stand brengt.
Tenzij anders vermeld, worden de waarden van de client voor rang gegeven wanneer de instellings waarden conflicteren.
De waarden aan de client zijde kunnen echter niet in strijd zijn met de maximum waarden en quota's die in de sessie configuratie zijn ingesteld.

Zonder para meters, **New-PSTransportOption** genereert een transport optie object dat Null-waarden heeft voor alle opties.
Als u een para meter weglaat, heeft het object een null-waarde voor de eigenschap die door de para meter wordt vertegenwoordigd.
Een null-waarde heeft geen invloed op de sessie configuratie.

Zie New-PSSessionOption voor meer informatie over sessie opties.
Zie [about_Session_Configurations](About/about_Session_Configurations.md) (Engelstalig) voor meer informatie over sessieconfiguraties.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een standaard transport optie genereren

```
PS C:\> New-PSTransportOption
ProcessIdleTimeoutSec           :
MaxIdleTimeoutSec               :
MaxSessions                     :
MaxConcurrentCommandsPerSession :
MaxSessionsPerUser              :
MaxMemoryPerSessionMB           :
MaxProcessesPerSession          :
MaxConcurrentUsers              :
IdleTimeoutSec                  :
OutputBufferingMode             :
```

Met deze opdracht wordt de **New-PSTransportOption** zonder para meters uitgevoerd.
De uitvoer laat zien dat de cmdlet een transport optie object genereert dat Null-waarden voor alle eigenschappen heeft.

### Voor beeld 2: opties voor sessie configuratie ophalen

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport options object, which it saves in the $t variable. The command uses the *MaxSessions* parameter to increase the maximum number of sessions to 40.
PS C:\> $t = New-PSTransportOption -MaxSessions 40

The second command uses the **Register-PSSessionConfiguration** cmdlet create the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Register-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the Get-PSSessionConfiguration cmdlet to get the ITTasks session configurations and the Format-List cmdlet to display all of the properties of the session configuration object in a list. The output shows that the value of the **MaxShells** property of the session configuration is 40.
PS C:\> Get-PSSessionConfiguration -Name ITTasks | Format-List -Property *
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/ITTasks
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
MaxShells                     : 40
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 2
Name                          : ITTasks
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
Enabled                       : True
MaxShellsPerUser              : 25
Permission                    :
```

In dit voor beeld ziet u hoe u een object transport opties gebruikt om opties voor sessie configuratie in te stellen.

### Voor beeld 3: een transport optie instellen

```
The first command uses the **New-PSTransportOption** cmdlet to create a transport option object. The command uses the *IdleTimeoutSec* parameter to set the **IdleTimeoutSec** property value of the object to one hour (3600 seconds). The command saves the transport objects object in the $t variable.
PS C:\> $t = New-PSTransportOption -IdleTimeoutSec 3600

The second command uses the Set-PSSessionConfiguration cmdlet to change the transport options of the ITTasks session configuration. The command uses the *TransportOption* parameter to specify the transport options object in the $t variable.
PS C:\> Set-PSSessionConfiguration -Name ITTasks -TransportOption $t

The third command uses the New-PSSession cmdlet to create the MyITTasks session on the local computer. The command uses the **ConfigurationName** property to specify the ITTasks session configuration. The command saves the session in the $s variable.Notice that the command does not use the *SessionOption* parameter of **New-PSSession** to set a custom idle time-out for the session. If it did, the idle time-out value set in the session option would take precedence over the idle time-out set in the session configuration.
PS C:\> $s = New-PSSession -Name MyITTasks -ConfigurationName ITTasks

The fourth command uses the Format-List cmdlet to display all properties of the session in the $s variable in a list. The output shows that the session has an idle time-out of one hour (360,000 milliseconds).
PS C:\> $s | Format-List -Property *
State                  : Opened
IdleTimeout            : 3600000
OutputBufferingMode    : Block
ComputerName           : localhost
ConfigurationName      : ITTasks
InstanceId             : 4110c3f5-68ea-40fa-9bbf-04a433dbb02d
Id                     : 1
Name                   : MyITTasks
Availability           : Available
ApplicationPrivateData : {PSVersionTable}
Runspace               : System.Management.Automation.RemoteRunspace
```

Met deze opdracht wordt het effect weer gegeven van het instellen van een transport optie in een sessie configuratie op de sessies die gebruikmaken van de sessie configuratie.

## PARAMETERS

### -IdleTimeoutSec

Hiermee wordt bepaald hoe lang elke sessie open blijft als de externe computer geen communicatie van de lokale computer ontvangt.
Dit omvat het heartbeat-signaal.
Wanneer het interval is verlopen, wordt de sessie gesloten.

De time-outwaarde voor inactiviteit is van groot belang wanneer de gebruiker de verbinding verbreekt en opnieuw verbinding maakt met een sessie.
De gebruiker kan opnieuw verbinding maken als er geen time-out is opgetreden voor de sessie.

De para meter *IdleTimeoutSec* komt overeen met de eigenschap **IdleTimeoutMs** van een sessie configuratie.

Voer een waarde in seconden in.
De standaard waarde is 7200 (2 uur).
De minimum waarde is 60 (1 minuut).
Het maximum is de waarde van de eigenschap **IdleTimeout** van shell-objecten in de WSMan-configuratie ( `WSMan:\\\<ComputerName\>\Shell\IdleTimeout` ).
De standaard waarde is 7200000 milliseconden (2 uur).

Als er een time-outwaarde voor inactiviteit is ingesteld in de sessie opties en in de sessie configuratie, krijgt de waarde die in de sessie opties is ingesteld prioriteit, maar kan de waarde van de eigenschap **MaxIdleTimeoutMs** van de sessie configuratie niet groter worden.
Als u de waarde van de eigenschap **MaxIdleTimeoutMs** wilt instellen, gebruikt u de para meter *MaxIdleTimeoutSec* .

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxConcurrentCommandsPerSession

Beperkt het aantal opdrachten dat tegelijkertijd in elke sessie kan worden uitgevoerd naar de opgegeven waarde.
De standaardwaarde is 1000.

De para meter *MaxConcurrentCommandsPerSession* komt overeen met de eigenschap **MaxConcurrentCommandsPerShell** van een sessie configuratie.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxConcurrentUsers

Beperkt het aantal gebruikers dat op hetzelfde moment in elke sessie opdrachten kan uitvoeren op de opgegeven waarde.
De standaard waarde is 5.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxIdleTimeoutSec

Hiermee wordt de time-out voor inactiviteit voor elke sessie beperkt tot de opgegeven waarde.
De standaard waarde is \[ int \] :: MaxValue (~ 25 dagen).

De time-outwaarde voor inactiviteit is van groot belang wanneer de gebruiker de verbinding verbreekt en opnieuw verbinding maakt met een sessie.
De gebruiker kan opnieuw verbinding maken als er geen time-out is opgetreden voor de sessie.

De para meter *MaxIdleTimeoutSec* komt overeen met de eigenschap **MaxIdleTimeoutMs** van een sessie configuratie.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxMemoryPerSessionMB

Hiermee wordt het geheugen dat door elke sessie wordt gebruikt, beperkt tot de opgegeven waarde.
Voer een waarde in mega bytes in.
De standaard waarde is 1024 MB (1 GB).

De para meter *MaxMemoryPerSessionMB* komt overeen met de eigenschap **MaxMemoryPerShellMB** van een sessie configuratie.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxProcessesPerSession

Beperkt het aantal processen dat in elke sessie wordt uitgevoerd op de opgegeven waarde.
De standaard waarde is 15.

De para meter *MaxProcessesPerSession* komt overeen met de eigenschap **MaxProcessesPerShell** van een sessie configuratie.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxSessions

Hiermee beperkt u het aantal sessies dat de sessie configuratie gebruikt.
De standaard waarde is 25.

De para meter *maxsessions* komt overeen met de eigenschap **MaxShells** van een sessie configuratie.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MaxSessionsPerUser

Hiermee beperkt u het aantal sessies dat de sessie configuratie gebruikt en voert u uit met de referenties van een bepaalde gebruiker naar de opgegeven waarde.
De standaard waarde is 25.

Wanneer u deze waarde opgeeft, moet u er rekening mee houden dat veel gebruikers mogelijk gebruikmaken van de referenties van een run as-gebruiker.

De para meter *MaxSessionsPerUser* komt overeen met de eigenschap **MaxShellsPerUser** van een sessie configuratie.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OutputBufferingMode

Hiermee wordt bepaald hoe de uitvoer van de opdracht wordt beheerd in verbroken sessies wanneer de uitvoer buffer vol raakt.
De aanvaardbare waarden voor deze parameter zijn:

- Blok keren.
Wanneer de uitvoer buffer vol is, wordt de uitvoering onderbroken totdat de buffer leeg is.
- Directe.
Wanneer de uitvoer buffer vol is, wordt de uitvoering voortgezet.
Wanneer er een nieuwe uitvoer wordt opgeslagen, wordt de oudste uitvoer verwijderd.
- Geen.
Er is geen uitvoer buffer modus opgegeven.

De standaard waarde van de eigenschap **OutputBufferingMode** van sessies is blok keren.

```yaml
Type: System.Nullable`1[System.Management.Automation.Runspaces.OutputBufferingMode]
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProcessIdleTimeoutSec

Hiermee wordt de time-out voor elk hostproces beperkt tot de opgegeven waarde.
De standaard waarde, 0, betekent dat er geen time-outwaarde is voor het proces.

Andere sessie configuraties hebben time-outwaarden per proces.
Bijvoorbeeld: de **micro soft. Power shell. werk stroom** sessie configuratie heeft een time-outwaarde van 28800 seconden (8 uur).

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
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

### Micro soft. Power shell. commands. WSManConfigurationOption

## OPMERKINGEN

- De eigenschappen van een sessie configuratie object zijn afhankelijk van de opties die zijn ingesteld voor de sessie configuratie en de waarden van deze opties. Daarnaast hebben sessie configuraties die gebruikmaken van een sessie configuratie bestand extra eigenschappen.

## GERELATEERDE KOPPELINGEN

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)
