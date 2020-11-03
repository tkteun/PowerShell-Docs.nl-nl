---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 553b61c9669afab325e9feec101d701c2b9a7c83
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251499"
---
# Restart-Computer

## SAMENVATTING
Hiermee wordt het besturings systeem opnieuw opgestart op lokale en externe computers.

## SYNTAXIS

### Standaardset (standaard)

```
Restart-Computer [-DcomAuthentication <AuthenticationLevel>] [-Impersonation <ImpersonationLevel>]
 [-WsmanAuthentication <String>] [-Protocol <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AsJobSet

```
Restart-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>]
 [-Impersonation <ImpersonationLevel>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Force] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Restart-Computer`Met de cmdlet wordt het besturings systeem opnieuw gestart op de lokale en externe computers.

U kunt de para meters van gebruiken `Restart-Computer` om de bewerkingen voor opnieuw opstarten uit te voeren als achtergrond taak, om de verificatie niveaus en alternatieve referenties op te geven, om de bewerkingen die tegelijkertijd worden uitgevoerd, te beperken en onmiddellijk opnieuw op te starten.

Vanaf Windows Power Shell 3,0 kunt u wachten tot de herstart is voltooid voordat u de volgende opdracht uitvoert. Geef een time-out op voor de wacht tijd en het query-interval, en wacht totdat bepaalde services beschikbaar zijn op de computer die opnieuw is opgestart. Deze functie maakt het handig om te gebruiken `Restart-Computer` in scripts en functies.

U kunt het WS-Management (WSMan)-protocol gebruiken om de computer opnieuw op te starten, in gevallen waarin gedistribueerde Component Object Model (DCOM)-aanroepen worden geblokkeerd, zoals een bedrijfs firewall. Zie [WS-Management Protocol](/windows/desktop/WinRM/ws-management-protocol)(Engelstalig) voor meer informatie.

Voor deze cmdlet is alleen externe toegang tot Windows Power shell vereist wanneer u de para meter **AsJob** in een opdracht gebruikt.

## VOORBEELDEN

### Voor beeld 1: de lokale computer opnieuw opstarten

`Restart-Computer` Hiermee wordt de lokale computer opnieuw opgestart.

```powershell
Restart-Computer
```

### Voor beeld 2: meerdere computers opnieuw opstarten

`Restart-Computer` externe en lokale computers kunnen opnieuw worden gestart. De para meter **ComputerName** accepteert een matrix met computer namen.

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### Voor beeld 3: computers opnieuw opstarten als achtergrond taak

Met deze opdrachten `Restart-Computer` wordt een opdracht uitgevoerd als achtergrond taak op twee externe computers, waarna de resultaten worden opgehaald.

Omdat **AsJob** de taak op de lokale computer maakt en automatisch de resultaten naar de lokale computer retourneert, kunt u uitvoeren `Receive-Job` als een lokale opdracht.

```powershell
$Job = Restart-Computer -ComputerName "Server01", "Server02" -AsJob
$Job | Receive-Job
```

`Restart-Computer` maakt gebruik van de para meter **ComputerName** om **Server01** en **Server02** op te geven. De **AsJob** para meter voert de opdracht uit als achtergrond taak. Het taak object wordt opgeslagen in de `$Job` variabele. `$Job` wordt via de pijp lijn naar de `Receive-Job` cmdlet verzonden die de resultaten ophaalt.

### Voor beeld 4: een externe computer opnieuw opstarten

`Restart-Computer` Hiermee wordt een externe computer opnieuw opgestart met aangepaste imitatie-en verificatie-instellingen.

```powershell
Restart-Computer -ComputerName Server01 -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

`Restart-Computer` maakt gebruik van de para meter **ComputerName** om **Server01** op te geven. De **imitatie** parameter geeft anoniem op om de identiteit van de aanvrager te verbergen. De **DcomAuthentication** para meter geeft u PacketIntegrity op als verificatie niveau van de verbinding.

### Voor beeld 5: de computers die worden vermeld in een tekst bestand geforceerd opnieuw opstarten

In dit voor beeld wordt een onmiddellijke herstart van de computers die in het bestand worden vermeld, geforceerd `Domain01.txt` . De computer namen uit het tekst bestand worden opgeslagen in een variabele. De **Force** -para meter forceert onmiddellijk opnieuw opstarten en de para meter **ThrottleLimit** beperkt het aantal gelijktijdige verbindingen.

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force -ThrottleLimit 10
```

`Get-Content` gebruikt de para meter **Path** voor het ophalen van een lijst met computer namen uit een tekst bestand **Domain01.txt**. De computer namen worden opgeslagen in de variabele `$Names` . `Get-Credential` vraagt u om een gebruikers naam en wacht woord en slaat de waarden op in de variabele `$Creds` . `Restart-Computer` maakt gebruik van de **computer naam** en de **referentie** parameters met hun variabelen. De para meter **Force** zorgt ervoor dat elke computer direct opnieuw wordt opgestart. De para meter **ThrottleLimit** beperkt de opdracht tot tien gelijktijdige verbindingen.

### Voor beeld 6: een externe computer opnieuw opstarten en wachten op Power shell

`Restart-Computer` Start de externe computer opnieuw op en wacht vijf minuten (300 seconden), waarna Power shell beschikbaar wordt op de computer die opnieuw is opgestart voordat deze doorgaat.

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

`Restart-Computer` maakt gebruik van de para meter **ComputerName** om **Server01** op te geven. De **wait** -para meter wacht totdat de herstart is voltooid. Met de **for** geeft u op dat Power shell opdrachten kan uitvoeren op de externe computer. De **time-** outpara meter geeft een wacht tijd van vijf minuten. De **vertragings** parameter voert elke twee seconden een query uit op de externe computer om vast te stellen of deze opnieuw wordt opgestart.

### Voor beeld 7: een computer opnieuw opstarten met behulp van het WSMan-Protocol

`Restart-Computer` Hiermee wordt de externe computer opnieuw opgestart met behulp van het WSMan-protocol in plaats van de standaard DCOM. Met Kerberos-verificatie wordt bepaald of de huidige gebruiker gemachtigd is om de externe computer opnieuw op te starten.

Deze instellingen zijn ontworpen voor ondernemingen waarbij op DCOM gebaseerde herstarts mislukken omdat DCOM is geblokkeerd. Bijvoorbeeld door een firewall.

```powershell
Restart-Computer -ComputerName Server01 -Protocol WSMan -WsmanAuthentication Kerberos
```

`Restart-Computer` maakt gebruik van de para meter **ComputerName** om de externe computer op te geven, **Server01**.
De **protocol** parameter geeft aan dat het WSMan-protocol moet worden gebruikt. De **WsmanAuthentication** para meter geeft u de verificatie methode op als **Kerberos**.

## PARAMETERS

### -AsJob

Geeft aan dat `Restart-Computer` wordt uitgevoerd als achtergrond taak.

Als u deze para meter wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang. In Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell openen met de optie **als administrator uitvoeren** . Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)voor meer informatie.

Wanneer u de para meter **AsJob** opgeeft, retourneert de opdracht direct een object dat de achtergrond taak vertegenwoordigt. U kunt in de sessie blijven werken terwijl de taak is voltooid. De taak wordt gemaakt op de lokale computer en de resultaten van externe computers worden automatisch geretourneerd naar de lokale computer. Gebruik de **taak** -cmdlets om de taak te beheren. Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .

Zie [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)voor meer informatie over Windows Power shell-achtergrond taken.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u een computer naam of een door komma's gescheiden matrix van computer namen op. `Restart-Computer` Hiermee worden **computer naam** objecten van de pijp lijn of variabelen geaccepteerd.

Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een externe computer. Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt `.` of localhost.

Deze para meter is niet afhankelijk van externe communicatie met Power shell. U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

Als de para meter **ComputerName** niet is opgegeven, wordt `Restart-Computer` de lokale computer opnieuw opgestart.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat gemachtigd is om deze actie uit te voeren. Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals **gebruiker01** of **Domain01\User01** , of voer een **PSCredential** -object in dat door de cmdlet wordt gegenereerd `Get-Credential` . Als u een gebruikers naam typt, wordt u gevraagd het wacht woord in te voeren.

Referenties worden opgeslagen in een [PSCredential](/dotnet/api/system.management.automation.pscredential) -object en het wacht woord wordt opgeslagen als [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Zie [Hoe veilig is securestring?](/dotnet/api/system.security.securestring#how-secure-is-securestring)voor meer informatie over **securestring** Data Protection.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DcomAuthentication

Hiermee geeft u het verificatie niveau op dat wordt gebruikt voor de WMI-verbinding. `Restart-Computer` maakt gebruik van WMI.

Geldige waarden zijn:

- **Aanroep** : com-verificatie op aanroepen niveau
- **Verbinding maken** : com-verificatie op verbindings niveau
- **Standaard** : Windows-verificatie
- **Geen** : geen com-verificatie
- **Pakket** : com-verificatie op pakket niveau.
- **PacketIntegrity** : com-verificatie op pakket integriteit-niveau
- **PacketPrivacy** : com-verificatie op privacyniveau op pakket niveau.
- **Ongewijzigd** : het verificatie niveau is hetzelfde als de vorige opdracht.

Zie [authenticationLevel Enumeration (Engelstalig)](/dotnet/api/system.management.authenticationlevel)voor meer informatie.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Vertraging

Hiermee geeft u de frequentie van query's in seconden. Power shell vraagt de service op die is opgegeven door de para meter **for** om te bepalen of de service beschikbaar is nadat de computer opnieuw is opgestart.

Deze para meter is alleen geldig in combi natie met de **wacht** **-en-** para meters.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

Als de para meter **Delay** niet is opgegeven, `Restart-Computer` wordt een vertraging van vijf seconden gebruikt.

```yaml
Type: System.Int16
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Voor

Hiermee wordt het gedrag van Power shell opgegeven wanneer wordt gewacht tot de opgegeven service of functie beschikbaar is nadat de computer opnieuw is opgestart. Deze para meter is alleen geldig met de para meter **wait** .

De aanvaardbare waarden voor deze parameter zijn:

- **Standaard** : er wordt gewacht tot Power shell opnieuw is opgestart.
- **Power shell** : opdrachten kunnen uitvoeren in een externe Power shell-sessie op de computer.
- **WMI** : ontvangt een antwoord op een Win32_ComputerSystem-query voor de computer.
- **WinRM** : kan een externe sessie met de computer tot stand brengen met behulp van WS-Management.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: DefaultSet
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt de computer direct opnieuw opgestart.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Imitatie

Hiermee geeft u het imitatie niveau op dat met deze cmdlet wordt gebruikt om WMI aan te roepen. `Restart-Computer` maakt gebruik van WMI.
De aanvaardbare waarden voor deze parameter zijn:

- **Standaard** : standaard imitatie. Ondanks de naam is dit niet de standaard waarde.
- **Anoniem** : Hiermee verbergt u de identiteit van de aanroeper.
- **Identify** : Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.
- **Nabooten** : Hiermee staat u toe dat objecten gebruikmaken van de referenties van de aanroeper.

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

### -Protocol

Hiermee geeft u het protocol op dat moet worden gebruikt om de computers opnieuw op te starten. De geldige waarden zijn **WSMan** en **DCOM**.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Hiermee geeft u het maximum aantal gelijktijdige verbindingen op dat tot stand kan worden gebracht om deze opdracht uit te voeren.
De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.

Als de para meter **ThrottleLimit** niet is opgegeven of als de waarde 0 wordt gebruikt, `Restart-Computer` wordt een maximum van 32 gelijktijdige verbindingen gebruikt.

```yaml
Type: System.Int32
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Time-out

Hiermee geeft u de duur van de wacht tijd in seconden. Wanneer de time-out is verstreken, `Restart-Computer` keert u terug naar de opdracht prompt, zelfs als de computers niet opnieuw worden opgestart.

De **time-** outparameter is alleen geldig met de **wait** -para meter. **Time-out** overschrijft de onbepaalde wacht tijd van de **wait** -para meter.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Int32
Parameter Sets: DefaultSet
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wachten

`Restart-Computer` onderdrukt de Power shell-prompt en blokkeert de pijp lijn totdat de computers opnieuw zijn opgestart. U kunt deze para meter in een script gebruiken om computers opnieuw op te starten en vervolgens door gaan met het proces wanneer het opnieuw opstarten is voltooid.

De **wacht** parameter voor onbepaalde tijd wacht op het opnieuw opstarten van de computers. U kunt **time-out** gebruiken om de timing en de para meters **voor** en **uitstel** in te stellen om te wachten tot bepaalde services beschikbaar zijn op de computers die opnieuw worden opgestart.

De **wait** -para meter is niet geldig wanneer u de lokale computer opnieuw opstart. Als de waarde van de para meter **ComputerName** de namen van externe computers en de lokale computer bevat, wordt `Restart-Computer` er een niet-afsluit fout gegenereerd voor **wachten** op de lokale computer, maar wordt gewacht tot de externe computers opnieuw worden opgestart.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WsmanAuthentication

Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties. Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

De acceptabele waarden voor deze para meter zijn: **Basic** , **CredSSP** , **default** , **Digest** , **Kerberos** en **Negotiate**.

Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie.

> [!WARNING]
> CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Vraagt u om bevestiging voordat deze wordt uitgevoerd `Restart-Computer` .

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

Laat zien wat er zou gebeuren als de `Restart-Computer` uitvoeringen wordt uitgevoerd. De `Restart-Computer` cmdlet wordt niet uitgevoerd.

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

### System. String

`Restart-Computer` Hiermee worden computer namen van de pijp lijn of variabelen geaccepteerd.

In Windows Power Shell 2,0 krijgt de para meter **ComputerName** alleen invoer van de pijp lijn op basis van de naam van de eigenschap. In Windows Power Shell 3,0 en hoger neemt de para meter **ComputerName** de invoer van de pijp lijn op waarde.

## UITVOER

### Geen, System. Management. Automation. RemotingJob

Als u de para meter **AsJob** opgeeft, `Restart-Computer` wordt een taak object geretourneerd. Anders wordt er geen uitvoer gegenereerd.

## OPMERKINGEN

- `Restart-Computer` werk alleen op computers met Windows en vereist WinRM en WMI om een systeem te afsluiten, inclusief het lokale systeem.
- `Restart-Computer` maakt gebruik van de [methode Win32Shutdown](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) van de klasse Windows Management INSTRUMENTATION (WMI) [Win32_OperatingSystem](/windows/desktop/CIMWin32Prov/win32-operatingsystem) .  Voor deze methode moet de bevoegdheid **SeShutdownPrivilege** zijn ingeschakeld voor het gebruikers account dat wordt gebruikt om de computer opnieuw op te starten.

In Windows Power Shell 2,0 werkt de para meter **AsJob** niet betrouwbaar wanneer u externe computers opnieuw opstart of stopt. In Windows Power Shell 3,0 is de implementatie gewijzigd om dit probleem op te lossen.

## GERELATEERDE KOPPELINGEN

[Over Windows Remote Management](/windows/desktop/WinRM/about-windows-remote-management)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[WS-Management-protocol](/windows/desktop/WinRM/ws-management-protocol)
