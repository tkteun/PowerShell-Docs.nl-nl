---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 4d00b875aab2e175465b262a320e7b16893c255c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347377"
---
# Enable-PSRemoting

## SAMENVATTING
Hiermee configureert u de computer voor het ontvangen van externe opdrachten.

## SYNTAXIS

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Enable-PSRemoting`Met de cmdlet wordt de computer geconfigureerd om externe Power shell-opdrachten te ontvangen die worden verzonden met behulp van de WS-Management technologie. Externe communicatie van Power shell op basis van WS-Management wordt momenteel alleen ondersteund op het Windows-platform.

Externe communicatie van Power shell is standaard ingeschakeld op Windows Server-platforms. U kunt gebruiken `Enable-PSRemoting` om externe communicatie van Power shell in te scha kelen op andere ondersteunde versies van Windows en externe toegang opnieuw in te scha kelen als deze wordt uitgeschakeld.

U hoeft deze opdracht slechts één keer uit te voeren op elke computer waarop opdrachten worden ontvangen. U hoeft deze niet uit te voeren op computers die alleen opdrachten verzenden. Omdat de configuratie listeners worden gestart om externe verbindingen te accepteren, is het verstandig om deze alleen uit te voeren als dat nodig is.

Externe communicatie van Power shell inschakelen op client versies van Windows als de computer zich op een openbaar netwerk bevindt, wordt normaal gesp roken niet toegestaan, maar u kunt deze beperking overs laan met behulp van de para meter **SkipNetworkProfileCheck** . Zie de beschrijving van de para meter **SkipNetworkProfileCheck** voor meer informatie.

Meerdere Power shell-installaties kunnen naast elkaar bestaan op één computer. Als `Enable-PSRemoting` u uitvoert, wordt een extern eind punt geconfigureerd voor de specifieke installatie versie waarop u de cmdlet uitvoert. Dus als u uitvoert `Enable-PSRemoting` tijdens het uitvoeren van Power shell 6,2, wordt een extern eind punt geconfigureerd dat Power shell 6,2 uitvoert. Als u uitvoert `Enable-PSRemoting` tijdens het uitvoeren van Power shell 7-Preview, wordt een extern eind punt geconfigureerd dat Power shell 7-Preview uitvoert.

`Enable-PSRemoting` maakt twee externe eindpunt configuraties waar nodig. Als de eindpunt configuraties al bestaan, kunnen ze gewoon worden ingeschakeld. De gemaakte configuraties zijn identiek, maar hebben verschillende namen. Een voor waarde is een eenvoudige naam die overeenkomt met de Power shell-versie die als host fungeert voor de sessie. De andere configuratie naam bevat gedetailleerde informatie over de Power shell-versie die als host fungeert voor de sessie. Bij uitvoering `Enable-PSRemoting` in Power shell 6,2 krijgt u bijvoorbeeld twee geconfigureerde eind punten met de naam **Power shell. 6** , **Power shell. 6.2.2**.
Hierdoor kunt u een verbinding met de nieuwste versie van Power shell 6-host maken met behulp van de eenvoudige naam **Power shell. 6**. U kunt ook verbinding maken met een specifieke versie van de Power shell-host met behulp van de meer naam **Power shell. 6.2.2**.

Als u de nieuw ingeschakelde externe eind punten wilt gebruiken, moet u deze opgeven met de naam met de para meter **configuratiepad** bij het maken van een externe verbinding met behulp van de `Invoke-Command` `New-PSSession` `Enter-PSSession` cmdlets. Zie voor beeld 4 voor meer informatie.

De `Enable-PSRemoting` cmdlet voert de volgende bewerkingen uit:

- Voert de cmdlet [set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) uit, waarmee de volgende taken worden uitgevoerd:
  - De WinRM-service wordt gestart.
  - Hiermee stelt u het opstart type van de WinRM-service in op automatisch.
  - Hiermee maakt u een listener voor het accepteren van aanvragen op een IP-adres.
  - Hiermee schakelt u een firewall-uitzonde ring voor WS-Management-communicatie.
  - Maakt zo nodig de eenvoudige en lange naam van de sessie-eindpunt configuraties.
  - Hiermee schakelt u alle sessie configuraties in.
  - Hiermee wijzigt u de security descriptor van alle sessie configuraties om externe toegang toe te staan.
- De WinRM-service wordt opnieuw gestart om de voor gaande wijzigingen van kracht te laten worden.

Als u deze cmdlet wilt uitvoeren op het Windows-platform, start u Power shell met de optie als administrator uitvoeren. Deze cmdlet is niet beschikbaar in Linux-of MacOS-versies van Power shell.

> [!CAUTION]
> Deze cmdlet heeft geen invloed op externe eindpunt configuraties die zijn gemaakt door Windows Power shell.
> Dit geldt alleen voor eind punten die zijn gemaakt met Power shell versie 6 en hoger. Als u externe Power shell-eind punten die worden gehost door Windows Power shell wilt in-en uitschakelen, voert u de `Enable-PSRemoting` cmdlet uit vanuit een Windows Power shell-sessie.

## VOORBEELDEN

### Voor beeld 1: een computer configureren voor het ontvangen van externe opdrachten

Met deze opdracht wordt de computer zo geconfigureerd dat externe opdrachten worden ontvangen.

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### Voor beeld 2: een computer configureren voor het ontvangen van externe opdrachten zonder een bevestigings prompt

Met deze opdracht wordt de computer zo geconfigureerd dat externe opdrachten worden ontvangen.
De para meter **Force** onderdrukt de gebruikers prompts.

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### Voor beeld 3: externe toegang op clients toestaan

In dit voor beeld ziet u hoe u externe toegang toestaat vanuit open bare netwerken op client versies van het Windows-besturings systeem. De naam van de firewall regel kan verschillend zijn voor verschillende versies van Windows.
Gebruiken `Get-NetFirewallRule` om een lijst met regels weer te geven. Voordat u de firewall regel inschakelt, bekijkt u de beveiligings instellingen in de regel om te controleren of de configuratie geschikt is voor uw omgeving.

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

`Enable-PSRemoting`Maakt standaard netwerk regels die externe toegang vanaf particuliere en domein netwerken toestaan. De opdracht gebruikt de para meter **SkipNetworkProfileCheck** om externe toegang vanaf open bare netwerken in hetzelfde lokale subnet toe te staan. De opdracht geeft de para meter **Force** om bevestigings berichten te onderdrukken.

De para meter **SkipNetworkProfileCheck** heeft geen invloed op Server versies van het Windows-besturings systeem, waardoor externe toegang vanaf open bare netwerken in hetzelfde lokale subnet standaard is toegestaan.

De `Set-NetFirewallRule` cmdlet in de module **netsecurity** voegt een firewall regel toe die externe toegang vanaf open bare netwerken vanaf elke externe locatie toestaat. Dit omvat locaties in verschillende subnetten.

### Voor beeld 4: een externe sessie maken naar de nieuwe ingeschakelde eindpunt configuratie

In dit voor beeld ziet u hoe u externe communicatie van Power shell op een computer inschakelt, de geconfigureerde eindpunt namen zoekt en een externe sessie maakt naar een van de eind punten.

Met de eerste opdracht wordt externe communicatie met Power shell op de computer ingeschakeld.

Met de tweede opdracht worden de eindpunt configuraties weer gegeven.

Met de derde opdracht maakt u een externe Power shell-sessie op dezelfde computer, waarbij u de **Power shell. 6** -eind punt op naam opgeeft. De externe sessie wordt gehost met de nieuwste versie van Power shell 6 (6.2.2).

Met de laatste opdracht wordt de `$PSVersionTable` variabele in de externe sessie geopend om de Power shell-versie weer te geven die als host fungeert voor de sessie.

```powershell
Enable-PSRemoting -Force

Get-PSSessionConfiguration

$session = New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6

Invoke-Command -Session $session -ScriptBlock { $PSVersionTable }
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name                           Value
----                           -----
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
PSEdition                      Core
PSRemotingProtocolVersion      2.3
Platform                       Win32NT
SerializationVersion           1.1.0.1
GitCommitId                    6.2.2
WSManStackVersion              3.0
PSVersion                      6.2.2
OS                             Microsoft Windows 10.0.18363
```

> [!NOTE]
> De naam van de firewall regel kan verschillen, afhankelijk van de versie van Windows. Gebruik de `Get-NetFirewallRule` cmdlet om de namen van de regels op uw systeem weer te geven.

## PARAMETERS

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

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

### -SkipNetworkProfileCheck

Geeft aan dat met deze cmdlet externe toegang wordt ingeschakeld op client versies van het Windows-besturings systeem wanneer de computer zich op een openbaar netwerk bevindt. Met deze para meter wordt een firewall regel ingeschakeld voor open bare netwerken die alleen externe toegang toestaan vanaf computers in hetzelfde lokale subnet.

Deze para meter heeft geen invloed op Server versies van het Windows-besturings systeem, die standaard een lokale subnet-firewall regel voor open bare netwerken hebben. Als de firewall regel van het lokale subnet is uitgeschakeld op een server versie, `Enable-PSRemoting` schakelt u deze opnieuw in, ongeacht de waarde van deze para meter.

Als u de beperkingen voor lokale subnetten wilt verwijderen en externe toegang vanaf alle locaties op open bare netwerken wilt inschakelen, gebruikt u de `Set-NetFirewallRule` cmdlet in de module **netsecurity** .

Deze para meter is geïntroduceerd in Power Shell 3,0.

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

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. String

Deze cmdlet retourneert teken reeksen die de resultaten beschrijven.

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

Op Server versies van het Windows-besturings systeem `Enable-PSRemoting` maakt u firewall regels voor privé-en domein netwerken die externe toegang toestaan en maakt u een firewall regel voor open bare netwerken die alleen externe toegang vanaf computers in hetzelfde lokale subnet mogelijk maken.

Op client versies van het Windows-besturings systeem `Enable-PSRemoting` maakt firewall regels voor particuliere en domein netwerken die onbeperkte externe toegang toestaan. Als u een firewall regel wilt maken voor open bare netwerken die externe toegang tot hetzelfde lokale subnet toestaan, gebruikt u de para meter **SkipNetworkProfileCheck** .

Op client-of server versies van het Windows-besturings systeem, om een firewall regel te maken voor open bare netwerken die de lokale subnet-beperking verwijderen en externe toegang toestaan, gebruikt u de `Set-NetFirewallRule` cmdlet in de module netsecurity om de volgende opdracht uit te voeren: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`

`Enable-PSRemoting` Hiermee schakelt u alle sessie configuraties in door de waarde van de eigenschap **ingeschakeld** van alle sessie configuraties in te stellen op `$True` .

`Enable-PSRemoting` Hiermee verwijdert u de instellingen voor **Deny_All** en **Network_Deny_All** . Dit biedt externe toegang tot sessie configuraties die zijn gereserveerd voor lokaal gebruik.

## GERELATEERDE KOPPELINGEN

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Enable-PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Register-PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Disable-PSRemoting](Disable-PSRemoting.md)

[WSMan Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Remote](About/about_Remote.md)

[about_Session_Configurations](About/about_Session_Configurations.md)
