---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WmiObject
ms.openlocfilehash: 287eb02e7de2f4182e0ecfd7f6b6a7cafb66969e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250579"
---
# Remove-WmiObject

## SAMENVATTING
Hiermee verwijdert u een exemplaar van een bestaande Windows Management Instrumentation-klasse (WMI).

## SYNTAXIS

### klasse (standaard)

```
Remove-WmiObject [-Class] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### object

```
Remove-WmiObject -InputObject <ManagementObject> [-AsJob] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### leertraject

```
Remove-WmiObject -Path <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### query

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### list

```
Remove-WmiObject [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Remove-WmiObject** verwijdert een exemplaar van een bestaande Windows Management INSTRUMENTATION (WMI)-klasse.

## VOORBEELDEN

### Voor beeld 1: alle exemplaren van een Win32-proces sluiten

```
PS C:\> notepad
PS C:\> $np = Get-WmiObject -Query "select * from win32_process where name='notepad.exe'"
PS C:\> $np | Remove-WmiObject
```

In dit voor beeld worden alle exemplaren van Notepad.exe gesloten.

Met de eerste opdracht wordt een exemplaar van Klad blok gestart.

Met de tweede opdracht wordt de cmdlet Get-WmiObject gebruikt voor het ophalen van de exemplaren van de Win32_Process die overeenkomen met Notepad.exe en vervolgens opgeslagen in de variabele $np.

Met de derde opdracht wordt het object in de variabele $np door gegeven aan **Remove-WmiObject** , waarmee alle instanties van Notepad.exe worden verwijderd.

### Voor beeld 2: een map verwijderen

```
PS C:\> $a = Get-WMIObject -Query "Select * From Win32_Directory Where Name ='C:\\Test'"
PS C:\> $a | Remove-WMIObject
```

Met deze opdracht wordt de map C:\Test verwijderd.

De eerste opdracht gebruikt **Get-WMIObject** om te zoeken naar de map C:\Test en slaat het object vervolgens op in de variabele $a.

Met de tweede opdracht pipet u de $a variabele voor **Remove-WMIObject** , waarmee de map wordt verwijderd.

## PARAMETERS

### -AsJob
Geeft aan dat deze cmdlet als achtergrond taak wordt uitgevoerd.
Gebruik deze para meter om opdrachten uit te voeren die lange tijd duren om te volt ooien.

Nieuwe CIM-cmdlets, geïntroduceerd in Windows Power Shell 3,0, voert dezelfde taken uit als de WMI-cmdlets.
De CIM-cmdlets voldoen aan de WS-Management (WSMan)-standaarden en met de Common Information Model (CIM) standaard, waardoor de-cmdlets dezelfde technieken kunnen gebruiken voor het beheren van computers waarop het Windows-besturings systeem wordt uitgevoerd en die met andere besturings systemen.
In plaats van **Remove-WmiObject** te gebruiken, kunt u overwegen de cmdlet Remove-CimInstance te gebruiken https://go.microsoft.com/fwlink/?LinkId=227964 .

Wanneer u de para meter *AsJob* gebruikt, retourneert de opdracht een object dat de achtergrond taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven.
U kunt in de sessie blijven werken terwijl de taak is voltooid.
Als **Remove-WmiObject** wordt gebruikt voor een externe computer, wordt de taak gemaakt op de lokale computer en worden de resultaten van externe computers automatisch teruggestuurd naar de lokale computer.
Als u de taak wilt beheren, gebruikt u de cmdlets die het zelfstandige **taak** onderdeel (de **taak** -cmdlets) bevatten.
Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.

Als u deze para meter voor externe computers wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang.
Start Windows Power shell met de optie als administrator uitvoeren.
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
Hiermee geeft u het verificatie niveau op dat moet worden gebruikt voor de WMI-verbinding.
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
Hiermee geeft u de naam van een WMI-klasse op die met deze cmdlet wordt verwijderd.

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
Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.

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
Als deze para meter wordt gebruikt, worden alle andere para meters genegeerd.

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
De para meter *locale* wordt opgegeven als een matrix in de MS_ \<LCID\> indeling in de gewenste volg orde.

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
Hiermee wordt het WMI-objectpad van een WMI-klasse opgegeven, of het WMI-objectpad van een exemplaar van een WMI-klasse dat moet worden verwijderd.

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

### System. Management. ManagementObject
U kunt een beheer object door sluizen naar deze cmdlet.

## UITVOER

### Geen, System. Management. Automation. RemotingJob
Met deze cmdlet wordt een taak object geretourneerd als u de para meter *AsJob* opgeeft.
Anders wordt er geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-WmiObject](Get-WmiObject.md)

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Set-WmiInstance](Set-WmiInstance.md)
