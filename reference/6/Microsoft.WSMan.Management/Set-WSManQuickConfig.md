---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: e8bc5bc248eafe479f366397aa947845e94e190c
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/01/2020
ms.locfileid: "93251891"
---
# Set-WSManQuickConfig

## SAMENVATTING
Hiermee configureert u de lokale computer voor extern beheer.

## SYNTAXIS

### Alles

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## BESCHRIJVING

`Set-WSManQuickConfig`Met de cmdlet wordt de computer geconfigureerd om externe Power shell-opdrachten te ontvangen die worden verzonden met behulp van de technologie van webservices voor beheer (WS-Management).

`Set-WSManQuickConfig` voert de volgende acties uit:

- Controleert of de WinRM-service wordt uitgevoerd. Als de WinRM-service niet wordt uitgevoerd, wordt de service gestart.
- Hiermee stelt u het opstart type voor de WinRM-service in op automatisch.
- Hiermee maakt u een listener voor het accepteren van aanvragen op een IP-adres. Het standaard transport is **http**.
- Hiermee schakelt u een firewall-uitzonde ring voor WinRM-verkeer.

`Set-WSManQuickConfig`Start Power shell met de optie **als administrator uitvoeren** om het programma uit te voeren.

## VOORBEELDEN

### Voor beeld 1: extern beheer van de lokale computer via HTTP inschakelen

In dit voor beeld wordt de vereiste configuratie ingesteld om extern beheer van de lokale computer in te scha kelen. Met deze opdracht maakt u standaard een WS-Management listener op **http**.

```powershell
Set-WSManQuickConfig
```

### Voor beeld 2: extern beheer van de lokale computer via HTTPS inschakelen

In dit voor beeld wordt de vereiste configuratie ingesteld om extern beheer van de lokale computer in te scha kelen. De para meter **UseSSL** geeft aan dat **https** wordt gebruikt om te communiceren met de computer.

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> **Https** vereist hand matige configuratie. Zie de beschrijving van de para meter **UseSSL** voor meer informatie.

## PARAMETERS

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

### -SkipNetworkProfileCheck

Hiermee configureert u Windows-client versies voor externe toegang wanneer de computer zich op een openbaar netwerk bevindt. Met deze para meter wordt een firewall regel ingeschakeld voor open bare netwerken die alleen externe toegang toestaan vanaf computers in hetzelfde lokale subnet.

Deze para meter heeft geen invloed op Server versies van Windows, die standaard een lokale subnet-firewall regel voor open bare netwerken hebben. Als de firewall regel van het lokale subnet is uitgeschakeld op de server versie van Windows, `Enable-PSRemoting` schakelt u deze opnieuw in, ongeacht de waarde van deze para meter.

Als u de beperkingen voor lokale subnetten wilt verwijderen en externe toegang vanaf alle locaties op open bare netwerken wilt inschakelen, gebruikt u de `Set-NetFirewallRule` cmdlet in de module **netsecurity** .

Deze para meter is geïntroduceerd in Power Shell 3,0.

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

### -UseSSL

Hiermee geeft u op dat het SSL-protocol (Secure Sockets Layer) wordt gebruikt om verbinding te maken met de externe computer. SSL wordt standaard niet gebruikt.

WS-Management versleutelt alle Power shell-inhoud die via het netwerk wordt verzonden. Met de para meter **UseSSL** kunt u de extra beveiliging van https in plaats van http opgeven. Als u deze para meter gebruikt en SSL niet beschikbaar is op de poort die wordt gebruikt voor de verbinding, mislukt de opdracht.

**Https** vereist hand matige configuratie van WinRM-en firewall regels. Zie [How to: Configure WINRM for HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)(Engelstalig) voor meer informatie.

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

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Verbinding verbreken-WSMan](Disconnect-WSMan.md)

[Enable-PSRemoting](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Procedure: WINRM configureren voor HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Testen-WSMan](Test-WSMan.md)
