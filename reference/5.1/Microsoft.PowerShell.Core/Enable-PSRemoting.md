---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 0c8c386ab376afde3d15fcd29b3f653b3f738f63
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2020
ms.locfileid: "93251443"
---
# Enable-PSRemoting

## SAMENVATTING
Hiermee configureert u de computer voor het ontvangen van externe opdrachten.

## SYNTAXIS

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Enable-PSRemoting`Met de cmdlet wordt de computer geconfigureerd om externe Power shell-opdrachten te ontvangen die worden verzonden met behulp van de WS-Management technologie.

Externe communicatie van Power shell is standaard ingeschakeld op Windows Server 2012. U kunt gebruiken `Enable-PSRemoting` om externe communicatie van Power shell in te scha kelen op andere ondersteunde versies van Windows en externe toegang opnieuw in te scha kelen op Windows Server 2012 als deze functie wordt uitgeschakeld.

U hoeft deze opdracht slechts één keer uit te voeren op elke computer waarop opdrachten worden ontvangen. U hoeft deze niet uit te voeren op computers die alleen opdrachten verzenden. Omdat de configuratie listeners start, is het voorzichtig om deze alleen uit te voeren als dat nodig is.

Vanaf Power Shell 3,0 kan de `Enable-PSRemoting` cmdlet Power shell-externe toegang inschakelen op client versies van Windows wanneer de computer zich in een openbaar netwerk bevindt. Zie de beschrijving van de para meter **SkipNetworkProfileCheck** voor meer informatie.

De `Enable-PSRemoting` cmdlet voert de volgende bewerkingen uit:

- Voert de cmdlet [set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) uit, waarmee de volgende taken worden uitgevoerd:
  - De WinRM-service wordt gestart.
  - Hiermee stelt u het opstart type van de WinRM-service in op automatisch.
  - Hiermee maakt u een listener voor het accepteren van aanvragen op een IP-adres.
  - Hiermee schakelt u een firewall-uitzonde ring voor WS-Management-communicatie.
  - Registreert de **micro soft. Power shell** en **micro soft. Power shell. werk stroom** sessie configuraties, als deze nog niet zijn geregistreerd.
  - Registreert de **micro soft. PowerShell32** -sessie configuratie op 64-bits computers, als deze nog niet is geregistreerd.
  - Hiermee schakelt u alle sessie configuraties in.
  - Hiermee wijzigt u de security descriptor van alle sessie configuraties om externe toegang toe te staan.
- De WinRM-service wordt opnieuw gestart om de voor gaande wijzigingen van kracht te laten worden.

Als u deze cmdlet wilt uitvoeren op het Windows-platform, start u Power shell met de optie als administrator uitvoeren. Dit geldt niet voor Linux-of MacOS-versies van Power shell.

> [!CAUTION]
> Gebruik Power Shell 2,0 niet voor het uitvoeren van de cmdlets op systemen met Power Shell 3,0 en Power Shell 2,0 `Enable-PSRemoting` `Disable-PSRemoting` . De opdrachten kunnen lijken te slagen, maar externe communicatie is niet juist geconfigureerd. Externe opdrachten en latere pogingen om externe toegang in te scha kelen en uit te scha kelen, mislukken waarschijnlijk.

## VOORBEELDEN

### Voor beeld 1: een computer configureren voor het ontvangen van externe opdrachten

Met deze opdracht wordt de computer zo geconfigureerd dat externe opdrachten worden ontvangen.

```powershell
Enable-PSRemoting
```

### Voor beeld 2: een computer configureren voor het ontvangen van externe opdrachten zonder een bevestigings prompt

Met deze opdracht wordt de computer zo geconfigureerd dat externe opdrachten worden ontvangen.
De para meter **Force** onderdrukt de gebruikers prompts.

```powershell
Enable-PSRemoting -Force
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

In Power Shell 3,0 `Enable-PSRemoting` maakt u de volgende firewall-uitzonde ringen voor WS-Management-communicatie.

Op Server versies van het Windows-besturings systeem `Enable-PSRemoting` maakt u firewall regels voor privé-en domein netwerken die externe toegang toestaan en maakt u een firewall regel voor open bare netwerken die alleen externe toegang vanaf computers in hetzelfde lokale subnet mogelijk maken.

Op client versies van het Windows-besturings systeem `Enable-PSRemoting` maakt Power shell 3,0 firewall regels voor particuliere en domein netwerken die onbeperkte externe toegang toestaan. Als u een firewall regel wilt maken voor open bare netwerken die externe toegang tot hetzelfde lokale subnet toestaan, gebruikt u de para meter **SkipNetworkProfileCheck** .

Op client-of server versies van het Windows-besturings systeem, om een firewall regel te maken voor open bare netwerken die de lokale subnet-beperking verwijderen en externe toegang toestaan, gebruikt u de `Set-NetFirewallRule` cmdlet in de module netsecurity om de volgende opdracht uit te voeren: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`

In Power Shell 2,0 `Enable-PSRemoting` maakt u de volgende firewall-uitzonde ringen voor WS-Management-communicatie.

Op Server versies van het Windows-besturings systeem maakt de firewall regels voor alle netwerken die externe toegang toestaan.

Op client versies van het Windows-besturings systeem `Enable-PSRemoting` maakt Power shell 2,0 een firewall uitzondering alleen voor locaties van domein en particulier netwerk. Voor het minimaliseren van beveiligings Risico's `Enable-PSRemoting` maakt geen firewall regel voor open bare netwerken op client versies van Windows. Wanneer de huidige netwerk locatie openbaar is, `Enable-PSRemoting` wordt het volgende bericht weer gegeven: kan de status van de firewall niet controleren.

Vanaf Power Shell 3,0 worden `Enable-PSRemoting` alle sessie configuraties ingeschakeld door de waarde van de eigenschap **enabled** van alle sessie configuraties in te stellen op `$True` .

In Power Shell 2,0 `Enable-PSRemoting` wordt de instelling **Deny_All** verwijderd uit de security descriptor van de sessie configuraties. In Power Shell 3,0 `Enable-PSRemoting` verwijdert u de instellingen **Deny_All** en **Network_Deny_All** . Dit biedt externe toegang tot sessie configuraties die zijn gereserveerd voor lokaal gebruik.

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
