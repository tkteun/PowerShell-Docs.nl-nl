---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/11/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Computer
ms.openlocfilehash: 8062210aa94cb46d5e5557ede1bac672cae39622
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251497"
---
# Stop-Computer

## SAMENVATTING
Stopt (wordt afgesloten) van lokale en externe computers.

## SYNTAXIS

### Alles

```
Stop-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Stop-Computer` cmdlet sluit de lokale computer en externe computers.

U kunt de para meters van gebruiken `Stop-Computer` om de afsluit bewerkingen uit te voeren als achtergrond taak, om de verificatie niveaus en alternatieve referenties op te geven, om de gelijktijdige verbindingen te beperken die worden gemaakt om de opdracht uit te voeren en om een onmiddellijke afsluit bewerking af te dwingen.

Voor deze cmdlet is geen externe Power shell-communicatie vereist tenzij u de para meter **AsJob** gebruikt.

## VOORBEELDEN

### Voor beeld 1: de lokale computer uitschakelen

In dit voor beeld wordt de lokale computer afgesloten.

```powershell
Stop-Computer -ComputerName localhost
```

### Voor beeld 2: twee externe computers en de lokale computer uitschakelen

In dit voor beeld worden twee externe computers en de lokale computer gestopt.

```powershell
Stop-Computer -ComputerName "Server01", "Server02", "localhost"
```

`Stop-Computer` maakt gebruik van de para meter **ComputerName** om twee externe computers en de lokale computer op te geven. Elke computer wordt afgesloten.

### Voor beeld 3: externe computers afsluiten als achtergrond taak

In dit voor beeld `Stop-Computer` wordt uitgevoerd als een achtergrond taak op twee externe computers.

```powershell
$j = Stop-Computer -ComputerName "Server01", "Server02" -AsJob
$results = $j | Receive-Job
$results
```

`Stop-Computer` maakt gebruik van de para meter **ComputerName** om twee externe computers op te geven. De **AsJob** para meter voert de opdracht uit als achtergrond taak. De taak objecten worden opgeslagen in de `$j` variabele.

De taak objecten in de `$j` variabele worden verzonden naar de pijp lijn naar `Receive-Job` , waardoor de taak resultaten worden opgehaald. De objecten worden opgeslagen in de `$results` variabele. `$results`Met de variabele wordt de taak informatie in de Power shell-console weer gegeven.

Omdat **AsJob** de taak op de lokale computer maakt en automatisch de resultaten naar de lokale computer retourneert, kunt u uitvoeren `Receive-Job` als een lokale opdracht.

### Voor beeld 4: een externe computer afsluiten

In dit voor beeld wordt een externe computer met opgegeven verificatie afgesloten.

```powershell
Stop-Computer -ComputerName "Server01" -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

`Stop-Computer` maakt gebruik van de para meter **ComputerName** om de externe computer op te geven. De **imitatie** parameter geeft een aangepaste imitatie op en de para meter **DcomAuthentication** geeft instellingen voor verificatie niveau.

### Voor beeld 5: computers afsluiten in een domein

In dit voor beeld forceren de opdrachten een onmiddellijke afsluiting van alle computers in een opgegeven domein.

```powershell
$s = Get-Content -Path ./Domain01.txt
$c = Get-Credential -Credential Domain01\Admin01
Stop-Computer -ComputerName $s -Force -ThrottleLimit 10 -Credential $c
```

`Get-Content` gebruikt de para meter **Path** om een bestand in de huidige map op te halen met de lijst van domein computers. De objecten worden opgeslagen in de `$s` variabele.

`Get-Credential` maakt gebruik van de para meter **Credential** om de referenties van een domein beheerder op te geven. De referenties worden opgeslagen in de `$c` variabele.

`Stop-Computer` de computers die zijn opgegeven met de **computer naam** parameter lijst van computers in de variabele worden afgesloten `$s` . Met de **Force** -para meter wordt direct afsluiten afgedwongen. De para meter **ThrottleLimit** beperkt de opdracht tot tien gelijktijdige verbindingen. De **referentie** parameter verzendt de referenties die zijn opgeslagen in de `$c` variabele.

## PARAMETERS

### -AsJob

Geeft aan dat deze cmdlet wordt uitgevoerd als een achtergrond taak.

Als u deze para meter wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang en, onder Windows Vista en latere versies van het Windows-besturings systeem, moet u Power shell openen met de optie **als administrator uitvoeren** . Zie [about_Remote_Requirements](..//microsoft.powershell.core/about/about_remote_requirements.md)voor meer informatie.

Wanneer u de para meter **AsJob** opgeeft, retourneert de opdracht direct een object dat de achtergrond taak vertegenwoordigt. U kunt in de sessie blijven werken terwijl de taak is voltooid. De taak wordt gemaakt op de lokale computer en de resultaten van externe computers worden automatisch geretourneerd naar de lokale computer. Gebruik de cmdlet om de taak resultaten te verkrijgen `Receive-Job` .

Zie [about_Jobs](..//microsoft.powershell.core/about/about_jobs.md) en [about_Remote_Jobs](../microsoft.powershell.core/about/about_remote_jobs.md)voor meer informatie over Power shell-achtergrond taken.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Hiermee geeft u de computers op die moeten worden gestopt. Standaard is dit de lokale computer.

Typ de NETBIOS-naam, het IP-adres of de Fully Qualified Domain Name van een of meer computers in een lijst met door komma's gescheiden waarden. Als u de lokale computer wilt opgeven, typt u de naam van de computer of localhost.

Deze para meter is niet afhankelijk van externe communicatie met Power shell. U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Hiermee geeft u het verificatie niveau op dat met deze cmdlet wordt gebruikt met WMI. `Stop-Computer` maakt gebruik van WMI. De standaard waarde is **pakket**.

De aanvaardbare waarden voor deze parameter zijn:

- **Standaard** : Windows-verificatie.
- **Geen** : geen com-verificatie.
- **Verbinding maken** : com-verificatie op verbinding niveau.
- **Aanroep** : com-verificatie op aanroepen niveau.
- **Pakket** : com-verificatie op pakket niveau.
- **PacketIntegrity** : com-verificatie op pakket integriteit-niveau.
- **PacketPrivacy** : com-verificatie op privacyniveau op pakket niveau.
- **Ongewijzigd** : hetzelfde als de vorige opdracht.

Zie [authenticationLevel](/dotnet/api/system.management.authenticationlevel)voor meer informatie over de waarden van deze para meter.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt de computer onmiddellijk afgesloten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Imitatie

Hiermee geeft u het imitatie niveau op dat moet worden gebruikt wanneer deze cmdlet WMI aanroept. De standaard waarde is **imiteren**.

`Stop-Computer` maakt gebruik van WMI. De aanvaardbare waarden voor deze parameter zijn:

- **Standaard** : standaard imitatie.
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
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

Hiermee geeft u het protocol op dat moet worden gebruikt om de computers opnieuw op te starten. De acceptabele waarden voor deze para meter zijn: **WSMan** en **DCOM**. De standaard waarde is **DCOM**.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: DCOM
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

### -WsmanAuthentication

Hiermee geeft u het mechanisme op dat wordt gebruikt voor het verifiëren van de gebruikers referenties wanneer deze cmdlet gebruikmaakt van het WSMan-protocol. De standaard waarde is **standaard**.

De aanvaardbare waarden voor deze parameter zijn:

- Basic
- CredSSP
- Standaard
- Samenvatting
- Kerberos
- Afspraken.

Zie [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)voor meer informatie over de waarden van deze para meter.

> [!CAUTION]
> CredSSP-verificatie (Credential Security service provider), waarbij de gebruikers referenties worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

Deze para meter is geïntroduceerd in Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
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

U kunt invoer niet naar deze cmdlet pipeen.

## UITVOER

### Geen of System. Management. Automation. RemotingJob

De cmdlet retourneert een **System. Management. Automation. RemotingJob** -object, als u de para meter **AsJob** opgeeft. Anders wordt er geen uitvoer gegenereerd.

## OPMERKINGEN

Deze cmdlet maakt gebruik van de methode **Win32Shutdown** van de WMI-klasse **Win32_OperatingSystem** . Voor deze methode moet de bevoegdheid **SeShutdownPrivilege** zijn ingeschakeld voor het gebruikers account dat wordt gebruikt om de computer opnieuw op te starten.

## GERELATEERDE KOPPELINGEN

[Add-computer](Add-Computer.md)

[Checkpoint-Computer](Checkpoint-Computer.md)

[Verwijderen-computer](Remove-Computer.md)

[Naam wijzigen-computer](Rename-Computer.md)

[Restart-Computer](Restart-Computer.md)

[Herstellen-computer](Restore-Computer.md)

[Test-Connection](Test-Connection.md)
