---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WmiObject
ms.openlocfilehash: ed759ff3d0dd35cd55f9dac5a2d76e36eac4dc6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250789"
---
# Get-WmiObject

## SAMENVATTING
Hiermee worden instanties van Windows Management Instrumentation (WMI)-klassen of informatie over de beschik bare klassen opgehaald.

## SYNTAXIS

### query (standaard)

```
Get-WmiObject [-Class] <String> [[-Property] <String[]>] [-Filter <String>] [-Amended] [-DirectRead]
 [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### list

```
Get-WmiObject [[-Class] <String>] [-Recurse] [-Amended] [-List] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### WQLQuery

```
Get-WmiObject [-Amended] [-DirectRead] -Query <String> [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### klasse

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### leertraject

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

## BESCHRIJVING

Vanaf Power Shell 3,0 is deze cmdlet vervangen door `Get-CimInstance` .

De `Get-WmiObject` cmdlet krijgt instanties van WMI-klassen of informatie over de beschik bare WMI-klassen. Als u een externe computer wilt opgeven, gebruikt u de para meter **ComputerName** . Als de **List** -para meter is opgegeven, krijgt de cmdlet informatie over de WMI-klassen die beschikbaar zijn in een opgegeven naam ruimte. Als de **query** parameter is opgegeven, wordt door de CMDLET een WQL-instructie (WMI Query Language) uitgevoerd.

De `Get-WmiObject` cmdlet maakt geen gebruik van externe Windows Power shell om bewerkingen uit te voeren.
U kunt de para meter **ComputerName** van de `Get-WmiObject` cmdlet ook gebruiken als uw computer niet voldoet aan de vereisten voor Windows Power shell Remoting of niet is geconfigureerd voor externe toegang in Windows Power shell.

Vanaf Windows Power Shell 3,0 is de eigenschap **__Server** van het object dat `Get-WmiObject` retourneert een **PSComputerName** -alias. Zo kunt u gemakkelijker de naam van de bron computer in uitvoer en rapporten toevoegen.

## VOORBEELDEN

### Voor beeld 1: processen op de lokale computer ophalen

In dit voor beeld worden de processen op de lokale computer opgehaald.

```powershell
Get-WmiObject -Class Win32_Process
```

### Voor beeld 2: Hiermee worden services op een externe computer opgehaald

In dit voor beeld worden de services op een externe computer opgehaald. Met de para meter **ComputerName** wordt het IP-adres van een externe computer opgegeven. Standaard moet het huidige gebruikers account lid zijn van de groep **Administrators** op de externe computer.

```powershell
Get-WmiObject -Class Win32_Service -ComputerName 10.1.4.62
```

### Voor beeld 3: WMI-klassen ophalen in de hoofdmap of standaard naam ruimte van de lokale computer

In dit voor beeld worden de WMI-klassen in de hoofdmap of standaard naam ruimte van de lokale computer opgehaald.

```powershell
Get-WmiObject -Namespace "root/default" -List
```

### Voor beeld 4: een benoemde service op meerdere computers ophalen

In dit voor beeld wordt de WinRM-service op de computers opgehaald die zijn opgegeven met de waarde van de para meter **ComputerName** .

```powershell
Get-WmiObject -Query "select * from win32_service where name='WinRM'" -ComputerName Server01, Server02 |
  Format-List -Property PSComputerName, Name, ExitCode, Name, ProcessID, StartMode, State, Status
```

```Output
PSComputerName : SERVER01
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 844
StartMode      : Auto
State          : Running
Status         : OK

PSComputerName : SERVER02
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 932
StartMode      : Auto
State          : Running
Status         : OK
```

Een pijplijn operator (|) verzendt de uitvoer naar de `Format-List` cmdlet, waarmee de eigenschap **PSComputerName** wordt toegevoegd aan de standaard uitvoer. **PSComputerName** is een alias van de eigenschap **__Server** van de objecten die worden `Get-WmiObject` geretourneerd. Deze alias is geïntroduceerd in Power Shell 3,0.

### Voor beeld 5: een service stoppen op een externe computer

In dit voor beeld wordt de WinRM-service op een externe computer gestopt. `Get-WmiObject` Hiermee wordt het exemplaar van het WinRM-service object op Server01 opgehaald. Vervolgens wordt de methode **Stop Service** aangeroepen van de WMI-klasse **Win32_Service** voor dat object.

```powershell
(Get-WmiObject -Class Win32_Service -Filter "name='WinRM'" -ComputerName Server01).StopService()
```

Dit is gelijk aan het gebruik van de `Stop-Service` cmdlet.

### Voor beeld 6: het BIOS op de lokale computer ophalen

In dit voor beeld worden de BIOS-gegevens van de lokale computer opgehaald. De **eigenschaps** parameter van de `Format-List` cmdlet wordt gebruikt om alle eigenschappen van het geretourneerde object in een lijst weer te geven. Standaard worden alleen de subset eigenschappen `Types.ps1xml` weer gegeven die in het configuratie bestand zijn gedefinieerd.

```powershell
Get-WmiObject -Class Win32_Bios | Format-List -Property *
```

```Output
Status                : OK
Name                  : Phoenix ROM BIOS PLUS Version 1.10 A05
Caption               : Phoenix ROM BIOS PLUS Version 1.10 A05
SMBIOSPresent         : True
__GENUS               : 2
__CLASS               : Win32_BIOS
__SUPERCLASS          : CIM_BIOSElement
__DYNASTY             : CIM_ManagedSystemElement
__RELPATH             : Win32_BIOS.Name="Phoenix ROM BIOS PLUS Version 1.10
__PROPERTY_COUNT      : 27
__DERIVATION          : {CIM_BIOSElement, CIM_SoftwareElement, CIM_LogicalElement,
__SERVER              : Server01
__NAMESPACE           : root\cimv2
__PATH                : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
BiosCharacteristics   : {7, 9, 10, 11...}
BIOSVersion           : {DELL   - 15, Phoenix ROM BIOS PLUS Version 1.10 A05}
BuildNumber           :
CodeSet               :
CurrentLanguage       : en|US|iso8859-1
Description           : Phoenix ROM BIOS PLUS Version 1.10 A05
IdentificationCode    :
InstallableLanguages  : 1
InstallDate           :
LanguageEdition       :
ListOfLanguages       : {en|US|iso8859-1}
Manufacturer          : Dell Inc.
OtherTargetOS         :
PrimaryBIOS           : True
ReleaseDate           : 20101103000000.000000+000
SerialNumber          : 8VDM9P1
SMBIOSBIOSVersion     : A05
SMBIOSMajorVersion    : 2
SMBIOSMinorVersion    : 6
SoftwareElementID     : Phoenix ROM BIOS PLUS Version 1.10 A05
SoftwareElementState  : 3
TargetOperatingSystem : 0
Version               : DELL   - 15
Scope                 : System.Management.ManagementScope
Path                  : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
Options               : System.Management.ObjectGetOptions
ClassPath             : \\JUNE-PC\root\cimv2:Win32_BIOS
Properties            : {BiosCharacteristics, BIOSVersion, BuildNumber, Caption...}
SystemProperties      : {__GENUS, __CLASS, __SUPERCLASS, __DYNASTY...}
Qualifiers            : {dynamic, Locale, provider, UUID}
Site                  :
Container             :
```

### Voor beeld 7: de services op een externe computer ophalen

In dit voor beeld wordt de para meter **Credential** van de `Get-WmiObject` cmdlet gebruikt om de services op een externe computer op te halen. De waarde van de **referentie** parameter is de naam van een gebruikers account. De gebruiker wordt gevraagd om een wacht woord.

```powershell
Get-WmiObject Win32_Service -Credential FABRIKAM\administrator -ComputerName Fabrikam
```

> [!NOTE]
> Referenties kunnen niet worden gebruikt bij het richten op de lokale computer.

## PARAMETERS

### -Gewijzigd

Hiermee wordt een waarde opgehaald of ingesteld die aangeeft of de objecten die worden geretourneerd door WMI, gewijzigde informatie bevatten. Normaal gesp roken wordt gewijzigde informatie gelokaliseerde informatie, zoals object-en eigenschaps beschrijvingen, die aan het WMI-object is gekoppeld.

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

### -AsJob

De opdracht wordt uitgevoerd als een achtergrond taak. Gebruik deze para meter om opdrachten uit te voeren die lange tijd duren om te volt ooien.

Wanneer u de para meter **AsJob** gebruikt, retourneert de opdracht een object dat de achtergrond taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven. U kunt in de sessie blijven werken terwijl de taak is voltooid. Als `Get-WmiObject` op een externe computer wordt gebruikt, wordt de taak op de lokale computer gemaakt en worden de resultaten van externe computers automatisch naar de lokale computer geretourneerd. Als u de taak wilt beheren, gebruikt u de cmdlets die de taak-cmdlets bevatten. Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .

> [!NOTE]
> Als u deze para meter met externe computers wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang. Daarnaast moet u Windows Power shell starten met de optie als administrator uitvoeren in Windows Vista en latere versies van Windows. Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)voor meer informatie.

Zie [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md)voor meer informatie over Windows Power shell-achtergrond taken.

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
Geldige waarden zijn:

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
Parameter Sets: (All)
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authority

Hiermee geeft u de instantie op die moet worden gebruikt om de WMI-verbinding te verifiëren. U kunt standaard NTLM-of Kerberos-verificatie opgeven. Als u NTLM wilt gebruiken, stelt u de instelling instantie in op `ntlmdomain:<DomainName>` , waarbij `<DomainName>` een geldige NTLM-domein naam wordt geïdentificeerd. Als u Kerberos wilt gebruiken, geeft u op `kerberos:<DomainName>\<ServerName>` . U kunt de instelling van de instantie niet toevoegen wanneer u verbinding maakt met de lokale computer.

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

### -Klasse

Hiermee geeft u de naam van een WMI-klasse op. Als deze para meter wordt gebruikt, haalt de cmdlet instanties van de WMI-klasse op.

```yaml
Type: System.String
Parameter Sets: query, list
Aliases: ClassName

Required: True (query), False (list)
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de doel computer voor de beheer bewerking op. Voer een Fully Qualified Domain Name (FQDN), een NetBIOS-naam of een IP-adres in. Wanneer de externe computer zich in een ander domein bevindt dan de lokale computer, is de Fully Qualified Domain Name vereist.

Standaard is dit de lokale computer. Gebruik ' localhost ', de naam van de lokale computer of een punt (.) om de lokale computer op te geven, zoals in een lijst met computer namen.

Deze para meter is niet afhankelijk van Windows Power shell remoting en maakt gebruik van WS-Management. U kunt de para meter **ComputerName** gebruiken `Get-WmiObject` , zelfs als uw computer niet is geconfigureerd om WS-Management externe opdrachten uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren. Standaard is dit de huidige gebruiker. Typ een gebruikers naam, zoals "gebruiker01", "Domain01\User01" of User@Contoso.com . U kunt ook een **PSCredential** -object invoeren, zoals een object dat door de cmdlet wordt geretourneerd `Get-Credential` . Wanneer u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen. Referenties kunnen niet worden gebruikt bij het richten op de lokale computer.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DirectRead

Hiermee geeft u op of directe toegang tot de WMI-provider is aangevraagd voor de opgegeven klasse, zonder enige voor de basis klasse of de afgeleide klassen ervan.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: query, WQLQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges

Hiermee worden alle bevoegdheden van de huidige gebruiker ingeschakeld voordat de opdracht de WMI-aanroep uitvoert.

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

### -Filter

Hiermee geeft u een **where** -component moet worden gebruikt als een filter. Gebruikt de syntaxis van de WMI Query Language (WQL).

> [!IMPORTANT]
> Neem het sleutel woord **waar** niet op in de waarde van de para meter. De volgende opdrachten retour neren bijvoorbeeld alleen de logische schijven met een **DeviceID** van c: en services die de naam ' WinRM ' hebben zonder het sleutel woord **where** te gebruiken.

`Get-WmiObject Win32_LogicalDisk -filter "DeviceID = 'c:' "`

`Get-WmiObject win32_service -filter "name='WinRM'"`

```yaml
Type: System.String
Parameter Sets: query
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

- 0: standaard. Hiermee wordt het lokale REGI ster voor het standaard imitatie niveau gelezen. De standaard instelling is doorgaans ingesteld op **imiteren**.
- 1: anoniem. Hiermee worden de referenties van de aanroep functie verborgen.
- 2: identificeren. Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.
- 3: imiteren. Toestaan dat objecten de referenties van de aanroep functie gebruiken.
- 4: delegeren. Hiermee kunnen objecten andere objecten toestaan de referenties van de aanroeper te gebruiken.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Lijst

Hiermee worden de namen opgehaald van de WMI-klassen in de naam ruimte van de WMI-opslag plaats die is opgegeven door de para meter van de **naam ruimte** .

Als u de **lijst** parameter opgeeft, maar niet de para meter van de **naam ruimte** , `Get-WmiObject` wordt standaard de **Root\Cimv2** -naam ruimte gebruikt. Deze cmdlet gebruikt niet de standaard register vermelding voor de **naam ruimte** in de `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` register sleutel om de standaard naam ruimte te bepalen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Land instellingen

Hiermee geeft u de voorkeurs land instelling voor WMI-objecten.
Voer een waarde in MS_ \<LCID\> notatie in.

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

### -Naam ruimte

Bij gebruik in combi natie met de para meter **Class** specificeert de **naam ruimte** parameter de naam ruimte van de WMI-opslag plaats waarin de opgegeven WMI-klasse zich bevindt. In combi natie met de para meter **List** geeft u de naam ruimte op waaruit u informatie over de WMI-klasse wilt verzamelen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Eigenschap

Hiermee geeft u de eigenschappen van de WMI-klasse op waarvan deze cmdlet gegevens ophaalt. Voer de namen van de eigenschappen in.

```yaml
Type: System.String[]
Parameter Sets: query
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Query uitvoeren

Hiermee wordt de opgegeven WMI Query Language-instructie (WQL) uitgevoerd. Deze para meter biedt geen ondersteuning voor gebeurtenis query's.

```yaml
Type: System.String
Parameter Sets: WQLQuery
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Recursief

Zoekt in de huidige naam ruimte en alle andere naam ruimten voor de klassenaam die is opgegeven door de para meter **Class** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Hiermee geeft u het maximum aantal WMI-bewerkingen op dat tegelijkertijd kan worden uitgevoerd. Deze para meter is alleen geldig als de para meter **AsJob** in de opdracht wordt gebruikt.

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen pipe invoer naar `Get-WmiObject` .

## UITVOER

### PSObject of System. Management. Automation. RemotingJob

Wanneer u de para meter **AsJob** gebruikt, retourneert de cmdlet een taak object. Anders is het object dat `Get-WmiObject` retourneert, afhankelijk van de waarde van de **klasse** para meter.

## OPMERKINGEN

Om toegang te krijgen tot WMI-gegevens op een externe computer, moet de cmdlet worden uitgevoerd onder een account dat lid is van de lokale groep Administrators op de externe computer. Of het standaard toegangs beheer voor de WMI-naam ruimte van de externe opslag plaats kan worden gewijzigd om toegangs rechten te geven voor andere accounts.

Standaard worden slechts enkele eigenschappen van elke WMI-klasse weer gegeven. De set eigenschappen die voor elke WMI-klasse wordt weer gegeven, is opgegeven in het XML-configuratie bestand van Types.ps1. Als u alle eigenschappen van een WMI-object wilt ophalen, gebruikt u de `Get-Member` `Format-List` cmdlets of.

## GERELATEERDE KOPPELINGEN

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Remove-WmiObject](Remove-WmiObject.md)

[Set-WmiInstance](Set-WmiInstance.md)

[Get-WSManInstance](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[Invoke-WSManAction](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[New-WSManInstance](../Microsoft.WsMan.Management/New-WSManInstance.md)

[Remove-WSManInstance](../Microsoft.WsMan.Management/Remove-WSManInstance.md)
