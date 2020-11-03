---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-wmimethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WmiMethod
ms.openlocfilehash: e9743488e86429e5cc3252162e51268a7978b79d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2020
ms.locfileid: "93251431"
---
# Invoke-WmiMethod

## SAMENVATTING
WMI-methoden aanroept.

## SYNTAXIS

### klasse (standaard)

```
Invoke-WmiMethod [-Class] <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### object

```
Invoke-WmiMethod -InputObject <ManagementObject> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### leertraject

```
Invoke-WmiMethod -Path <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### query

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### list

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Invoke-WmiMethod` cmdlet roept de methoden van de Windows Management Instrumentation-objecten (WMI) aan.

Nieuwe Common Information Model (CIM)-cmdlets, geïntroduceerd in Windows Power Shell 3,0, voeren dezelfde taken uit als de WMI-cmdlets. De CIM-cmdlets voldoen aan de WS-Management (WSMan)-standaarden en met de CIM-standaard, waardoor de-cmdlets dezelfde technieken kunnen gebruiken voor het beheren van Windows-computers en die met andere besturings systemen. In plaats van met kunt `Invoke-WmiMethod` u ook [invoke-CimMethod](../cimcmdlets/invoke-cimmethod.md)gebruiken.

## VOORBEELDEN

### Voor beeld 1: de vereiste volg orde van WMI-objecten weer geven

```powershell
([wmiclass]'Win32_Volume').GetMethodParameters('Format')
```

```Output
__GENUS           : 2
__CLASS           : __PARAMETERS
__SUPERCLASS      :
__DYNASTY         : __PARAMETERS
__RELPATH         :
__PROPERTY_COUNT  : 6
__DERIVATION      : {}
__SERVER          :
__NAMESPACE       :
__PATH            :
ClusterSize       : 0
EnableCompression : False
FileSystem        : NTFS
Label             :
QuickFormat       : False
Version           : 0
PSComputerName    :
```

Met deze opdracht wordt een lijst weer gegeven met de vereiste volg orde van de objecten. Voor het aanroepen van WMI in Power Shell 3,0 wijkt af van alternatieve methoden en vereist dat object waarden in een specifieke volg orde worden ingevoerd.

### Voor beeld 2: een exemplaar van een toepassing starten

```powershell
([Wmiclass]'Win32_Process').GetMethodParameters('Create')
```

```Output
__GENUS                   : 2
__CLASS                   : __PARAMETERS
__SUPERCLASS              :
__DYNASTY                 : __PARAMETERS
__RELPATH                 :
__PROPERTY_COUNT          : 3
__DERIVATION              : {}
__SERVER                  :
__NAMESPACE               :
__PATH                    :
CommandLine               :
CurrentDirectory          :
ProcessStartupInformation :
PSComputerName            :
```

```powershell
Invoke-WmiMethod -Path win32_process -Name create -ArgumentList notepad.exe
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 2
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ProcessId        : 11312
ReturnValue      : 0
PSComputerName   :
```

Met deze opdracht start u een exemplaar van Klad blok door de `Create` methode van de **Win32_Process** -klasse aan te roepen.

De eigenschap **returnValue** wordt gevuld met een 0 en de eigenschap **ProcessID** wordt gevuld met een geheel getal (het nummer van de volgende proces-id) als de opdracht is voltooid.

### Voor beeld 3: de naam van een bestand wijzigen

```powershell
Invoke-WmiMethod -Path "CIM_DataFile.Name='C:\scripts\test.txt'" -Name Rename -ArgumentList "C:\scripts\test_bu.txt"
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ReturnValue      : 0
```

Met deze opdracht wordt de naam van een bestand gewijzigd. De para meter **Path** wordt gebruikt om te verwijzen naar een exemplaar van de klasse **CIM_DataFile** . Vervolgens wordt de methode Rename toegepast op dat specifieke exemplaar.

De eigenschap **returnValue** wordt gevuld met een 0 als de opdracht is voltooid.

### Voor beeld 4: een matrix met waarden door geven met `-ArgumentList`

Een voor beeld van het gebruik van een matrix met objecten `$binSD` gevolgd door een `$null` waarde.

```powershell
$acl = get-acl test.txt
$binSD = $acl.GetSecurityDescriptorBinaryForm()
Invoke-WmiMethod -class Win32_SecurityDescriptorHelper -Name BinarySDToSDDL -ArgumentList $binSD, $null
```

## PARAMETERS

### -Argument List

Hiermee geeft u de para meters op die worden door gegeven aan de aangeroepen methode. De waarde van deze para meter moet een matrix met objecten zijn en moet worden weer gegeven in de volg orde die wordt vereist door de aangeroepen methode. `Invoke-CimCommand`Deze beperkingen gelden niet voor de cmdlet.

Als u de volg orde wilt bepalen waarin deze objecten worden weer gegeven, voert u de `GetMethodParameters()` methode uit op de WMI-klasse, zoals in voor beeld 1, aan het einde van dit onderwerp.

> [!IMPORTANT]
> Als de eerste waarde een matrix is die meer dan één element bevat, is een tweede waarde van $null vereist. Anders wordt er een fout gegenereerd, zoals ' kan een object van het type System. byte niet converteren naar het type ' System. array '. '. Zie voor beeld 4 hierboven.

```yaml
Type: System.Object[]
Parameter Sets: class, object, path
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsJob

Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak. Gebruik deze para meter om opdrachten uit te voeren die lange tijd duren om te volt ooien.

Wanneer u de para meter **AsJob** gebruikt, retourneert de opdracht een object dat de achtergrond taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven. U kunt in de sessie blijven werken terwijl de taak is voltooid. Als `Invoke-WmiMethod` wordt gebruikt voor een externe computer, wordt de taak gemaakt op de lokale computer en worden de resultaten van externe computers automatisch teruggestuurd naar de lokale computer. Als u de taak wilt beheren, gebruikt u de cmdlets die het zelfstandige taak onderdeel (de taak-cmdlets) bevatten. Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.

Als u deze para meter met externe computers wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang. Daarnaast moet u Windows Power shell starten met de optie als administrator uitvoeren in Windows Vista en latere versies van Windows. Zie about_Remote_Requirements voor meer informatie.

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

Hiermee geeft u het verificatie niveau op dat moet worden gebruikt met de WMI-verbinding. De aanvaardbare waarden voor deze parameter zijn:

- -1: ongewijzigd
- 0: standaard
- 1: geen (er is geen verificatie uitgevoerd.)
- 2: verbinding maken (verificatie wordt alleen uitgevoerd wanneer de client een relatie tot stand brengt met de toepassing.)
- 3: aanroep (verificatie wordt alleen uitgevoerd aan het begin van elke aanroep wanneer de toepassing de aanvraag ontvangt.)
- 4: pakket (verificatie wordt uitgevoerd op alle gegevens die van de client worden ontvangen.)
- 5: PacketIntegrity (alle gegevens die worden overgebracht tussen de client en de toepassing worden geverifieerd en geverifieerd.)
- 6: PacketPrivacy (de eigenschappen van de andere authenticatie niveaus worden gebruikt en alle gegevens worden versleuteld.)

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

Hiermee geeft u de instantie op die moet worden gebruikt om de WMI-verbinding te verifiëren. U kunt standaard Windows NT LAN Manager (NTLM) of Kerberos-verificatie opgeven. Als u NTLM wilt gebruiken, stelt u de instelling van de instantie in op ntlmdomain: \<DomainName\> , waarbij \<DomainName\> een geldige NTLM-domein naam wordt geïdentificeerd. Als u Kerberos wilt gebruiken, geeft u Kerberos op: \<DomainName\ServerName\> . U kunt de instelling van de instantie niet toevoegen wanneer u verbinding maakt met de lokale computer.

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

Hiermee geeft u de WMI-klasse op die een statische methode bevat die moet worden aangeroepen.

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

Geeft als een teken reeks matrix de computers waarop deze cmdlet de opdracht uitvoert. Standaard is dit de lokale computer.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer computers. Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.

Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell. U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

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

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Standaard is dit de huidige gebruiker. Typ een gebruikers naam, zoals `User01` , `Domain01\User01` of `User@Contoso.com` . U kunt ook een **PSCredential** -object invoeren, zoals een object dat wordt geretourneerd door de cmdlet Get-Credential. Wanneer u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.

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

Hiermee wordt aangegeven dat met deze cmdlet alle bevoegdheden van de huidige gebruiker worden ingeschakeld voordat de opdracht de WMI-aanroep uitvoert.

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

Hiermee geeft u het imitatie niveau op dat moet worden gebruikt. De aanvaardbare waarden voor deze parameter zijn:

- 0: standaard (leest het lokale REGI ster voor het standaard imitatie niveau, dat meestal is ingesteld op ' 3: impersonate '.)
- 1: anoniem (Hiermee worden de referenties van de aanroep functie verborgen.)
- 2: identificeren (Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.)
- 3: imiteren (toestaan dat objecten de referenties van de aanroeper gebruiken.)
- 4: delegeren (toestaan dat objecten andere objecten de referenties van de aanroep functie gebruiken.)

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

Hiermee geeft u een **ManagementObject** -object moet worden gebruikt als invoer. Als deze para meter wordt gebruikt, worden alle andere para meters, met uitzonde ring **van de para** meters en **argumenten** , genegeerd.

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

Hiermee geeft u de voorkeurs land instelling voor WMI-objecten. Geef de waarde van de para meter **locale** op als een matrix in de `MS_<LCID>` notatie in de gewenste volg orde.

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

### -Name

Hiermee geeft u de naam op van de methode die moet worden aangeroepen. Deze para meter is verplicht en mag niet null of leeg zijn.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Naam ruimte

In combi natie met de para meter **Class** geeft deze para meter de naam ruimte van de WMI-opslag plaats waar de WMI-klasse of het object waarnaar wordt verwezen, zich bevindt.

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

Hiermee wordt het WMI-objectpad van een WMI-klasse opgegeven of het WMI-objectpad van een exemplaar van een WMI-klasse. De klasse of het exemplaar dat u opgeeft, moet de-methode bevatten die is opgegeven in de para meter **name** .

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

### -ThrottleLimit

Hiermee geeft u een vertragings waarde voor het aantal WMI-bewerkingen dat tegelijkertijd kan worden uitgevoerd.
Deze para meter wordt gebruikt in combi natie met de para meter **AsJob** . De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.

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

### Geen

Deze cmdlet accepteert geen invoer.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-WSManInstance](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[Invoke-WSManAction](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[New-WSManInstance](../Microsoft.WsMan.Management/New-WSManInstance.md)

[Remove-WSManInstance](../Microsoft.WsMan.Management/Remove-WSManInstance.md)

[Get-WmiObject](Get-WmiObject.md)

[Remove-WmiObject](Remove-WmiObject.md)

[Set-WmiInstance](Set-WmiInstance.md)
