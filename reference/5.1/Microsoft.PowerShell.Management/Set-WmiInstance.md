---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-wmiinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WmiInstance
ms.openlocfilehash: 03288a2ffbef416937b2c92a7d08a5aed49ffb43
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250546"
---
# Set-WmiInstance

## SAMENVATTING
Hiermee wordt een exemplaar van een bestaande Windows Management Instrumentation (WMI)-klasse gemaakt of bijgewerkt.

## SYNTAXIS

### klasse (standaard)

```
Set-WmiInstance [-Class] <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### object

```
Set-WmiInstance -InputObject <ManagementObject> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### leertraject

```
Set-WmiInstance -Path <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### query

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### list

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
`Set-WmiInstance`Met de cmdlet wordt een exemplaar van een bestaande Windows Management Instrumentation (WMI)-klasse gemaakt of bijgewerkt.
Het gemaakte of bijgewerkte exemplaar wordt naar de WMI-opslag plaats geschreven.

Nieuwe CIM-cmdlets, geïntroduceerd in Windows Power Shell 3,0, voert dezelfde taken uit als de WMI-cmdlets.
De CIM-cmdlets voldoen aan de WS-Management (WSMan)-standaarden en met de Common Information Model (CIM) standaard.
op deze manier kunnen cmdlets dezelfde technieken gebruiken voor het beheren van Windows-computers en die met andere besturings systemen.
In plaats van met kunt `Set-WmiInstance` u overwegen de cmdlets [set-CimInstance](/powershell/module/cimcmdlets/set-ciminstance) of [New-CimInstance](/powershell/module/cimcmdlets/new-ciminstance) te gebruiken.

## VOORBEELDEN

### Voor beeld 1: WMI-logboek registratie niveau instellen

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2}
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
```

Met deze opdracht wordt het WMI-logboek registratie niveau ingesteld op 2.
De opdracht geeft de eigenschap die moet worden ingesteld en de waarde, samen als een waardepaar, in de para meter argument.
De para meter gebruikt een hash-tabel die is gedefinieerd door de constructie @ {Property = Value}.
De geretourneerde klasse-informatie weerspiegelt de nieuwe waarde.

### Voor beeld 2: een omgevings variabele en de waarde ervan maken

```
PS C:\> Set-WmiInstance -Class win32_environment -Argument @{Name="testvar";VariableValue="testvalue";UserName="<SYSTEM>"}
__GENUS          : 2
__CLASS          : Win32_Environment
__SUPERCLASS     : CIM_SystemResource
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Environment.Name="testvar",UserName="<SYSTEM>"
__PROPERTY_COUNT : 8
__DERIVATION     : {CIM_SystemResource, CIM_LogicalElement, CIM_ManagedSystemElement}
__SERVER         : SYSTEM01
__NAMESPACE      : root\cimv2
__PATH           : \\SYSTEM01\root\cimv2:Win32_Environment.Name="testvar",UserName="<SYSTEM>"
Caption          : <SYSTEM>\testvar
Description      : <SYSTEM>\testvar
InstallDate      :
Name             : testvar
Status           : OK
SystemVariable   : True
UserName         : <SYSTEM>
VariableValue    : testvalue
```

Met deze opdracht maakt u de omgevings variabele TestVar met de waarde testvalue.
Dit doet u door een nieuw exemplaar van de WMI-klasse **Win32_Environment** te maken.
Deze bewerking vereist de juiste referenties en u moet Windows Power shell mogelijk opnieuw opstarten om de nieuwe omgevings variabele te zien.

### Voor beeld 3: het WMI-logboek registratie niveau instellen voor verschillende externe computers

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2} -Computername "system01", "system02", "system03"
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
...
```

Met deze opdracht wordt het WMI-logboek registratie niveau ingesteld op 2.
De opdracht geeft de eigenschap die moet worden ingesteld en de waarde, samen als een waardepaar, in de para meter argument.
De para meter gebruikt een hash-tabel die is gedefinieerd door de constructie @ {Property = Value}.
De geretourneerde klassegegevens weerspiegelt de nieuwe waarde.

## PARAMETERS

### -Argumenten
Hiermee geeft u de naam op van de eigenschap die moet worden gewijzigd en de nieuwe waarde voor die eigenschap.
De naam en de waarde moeten een naam/waarde-paar zijn.
De naam/waarde-paar wordt door gegeven op de opdracht regel als een hash-tabel.
Bijvoorbeeld:

`@{Setting1=1; Setting2=5; Setting3="test"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: class, object, path
Aliases: Args, Property

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob
Geeft aan dat deze cmdket wordt uitgevoerd als een achtergrond taak.
Gebruik deze para meter om opdrachten uit te voeren die lange tijd duren om te volt ooien.

Wanneer u de para meter *AsJob* opgeeft, retourneert de opdracht een object dat de achtergrond taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven.
U kunt in de sessie blijven werken terwijl de taak is voltooid.
Als **set-WmiInstance** wordt gebruikt voor een externe computer, wordt de taak gemaakt op de lokale computer en worden de resultaten van externe computers automatisch teruggestuurd naar de lokale computer.
Als u de taak wilt beheren, gebruikt u de cmdlets die het zelfstandige **taak** onderdeel (de **taak** -cmdlets) bevatten.
Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.

Als u deze para meter samen met externe computers wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang.
Daarnaast moet u Windows Power shell starten met de optie als administrator uitvoeren in Windows Vista en latere versies van het Windows-besturings systeem.
Zie about_Remote_Requirements voor meer informatie.

Zie about_Jobs en about_Remote_Jobs voor meer informatie over Windows Power shell-achtergrond taken.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verificatie
Hiermee geeft u het verificatie niveau op dat moet worden gebruikt met de WMI-verbinding.
De aanvaardbare waarden voor deze parameter zijn:

- -1: ongewijzigd.
- 0: standaard.
- 1: geen.
Er is geen verificatie uitgevoerd.
- 2: verbinding maken.
Verificatie wordt alleen uitgevoerd wanneer de client een relatie met de toepassing tot stand brengt.
- 3: bellen.
Verificatie wordt alleen aan het begin van elke aanroep uitgevoerd wanneer de toepassing de aanvraag ontvangt.
- 4: pakket.
Verificatie wordt uitgevoerd op alle gegevens die van de client worden ontvangen.
- 5: PacketIntegrity.
Alle gegevens die worden overgebracht tussen de client en de toepassing, worden geverifieerd en geverifieerd.
- 6: PacketPrivacy.
De eigenschappen van de andere authenticatie niveaus worden gebruikt en alle gegevens worden versleuteld.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authority
Hiermee geeft u de instantie op die moet worden gebruikt om de WMI-verbinding te verifiëren.
U kunt standaard NTLM-of Kerberos-verificatie opgeven.
Als u NTLM wilt gebruiken, stelt u de instelling van de instantie in op ntlmdomain: \<DomainName\> , waarbij \<DomainName\> een geldige NTLM-domein naam wordt geïdentificeerd.
Als u Kerberos wilt gebruiken, geeft u Kerberos op: \<DomainName\> \\ \<ServerName\> .
U kunt de instelling van de instantie niet toevoegen wanneer u verbinding maakt met de lokale computer.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Klasse
Hiermee geeft u de naam van een WMI-klasse op.

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName
Hiermee geeft u de naam op van de computer waarop deze cmdlet wordt uitgevoerd.
Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer computers.
Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.

Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.
U kunt de para meter *ComputerName* ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.
Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de cmdlet Get-Credential.
Als u een gebruikers naam typt, wordt met deze cmdlet om een wacht woord gevraagd.

Deze para meter wordt niet ondersteund door providers die met een para meter zijn geïnstalleerd, worden niet ondersteund door providers die zijn geïnstalleerd met Windows Power shell.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges
Hiermee wordt aangegeven dat met deze cmdlet alle machtigingen van de huidige gebruiker worden ingeschakeld voordat de opdracht de WMI-aanroep uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Imitatie
Hiermee geeft u het imitatie niveau op dat moet worden gebruikt.
De aanvaardbare waarden voor deze parameter zijn:

- 0: standaard.
Leest het lokale REGI ster voor het standaard imitatie niveau, dat meestal is ingesteld op 3: imiteren.
- 1: anoniem.
Hiermee worden de referenties van de aanroep functie verborgen.
- 2: identificeren.
Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.
- 3: imiteren.
Toestaan dat objecten de referenties van de aanroep functie gebruiken.
- 4: delegeren.
Hiermee kunnen objecten andere objecten toestaan de referenties van de aanroeper te gebruiken.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object
Hiermee geeft u een **ManagementObject** -object moet worden gebruikt als invoer.
Als deze para meter wordt gebruikt, worden alle andere para meters, met uitzonde ring van de *argumenten* para meter, genegeerd.

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Land instellingen
Hiermee geeft u de voorkeurs land instelling voor WMI-objecten.
De para meter *locale* is opgegeven in een matrix in de MS_ \<LCID\> indeling in de gewenste volg orde.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Naam ruimte
Hiermee geeft u de naam ruimte van de WMI-opslag plaats waar de WMI-klasse waarnaar wordt verwezen zich bevindt als deze wordt gebruikt met de para meter *Class* .

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Hiermee geeft u een WMI-objectpad van het exemplaar dat u wilt maken of bijwerken.

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PutType
Hiermee wordt aangegeven of het WMI-exemplaar moet worden gemaakt of bijgewerkt.
De aanvaardbare waarden voor deze parameter zijn:

- UpdateOnly.
Hiermee wordt een bestaand WMI-exemplaar bijgewerkt.
- CreateOnly.
Hiermee maakt u een nieuw WMI-exemplaar.
- UpdateOrCreate.
Hiermee wordt het WMI-exemplaar bijgewerkt als het bestaat of een nieuw exemplaar maakt als er geen exemplaar bestaat.

```yaml
Type: System.Management.PutType
Parameter Sets: (All)
Aliases:
Accepted values: None, UpdateOnly, CreateOnly, UpdateOrCreate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.
Deze para meter wordt gebruikt in combi natie met de para meter *AsJob* .
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

### Geen
Deze cmdlet accepteert geen invoer.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-WmiObject](Get-WmiObject.md)

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Remove-WmiObject](Remove-WmiObject.md)
