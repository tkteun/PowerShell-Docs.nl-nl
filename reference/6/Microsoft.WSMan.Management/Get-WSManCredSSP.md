---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: 814be4153687268123114b4036b640eeb0f0da71
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249254"
---
# Get-WSManCredSSP

## SAMENVATTING
Hiermee wordt de configuratie van de provider met referentie beveiligings ondersteuning voor de client opgehaald.

## SYNTAXIS

```
Get-WSManCredSSP [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Get-WSManCredSSP** wordt de configuratie van de client en de server met referentie beveiligings ondersteuning opgehaald.
De uitvoer geeft aan of de CredSSP-verificatie (Credential Security Support Provider) is ingeschakeld of uitgeschakeld.
Met deze cmdlet worden ook configuratie-informatie weer gegeven voor het **AllowFreshCredentials** -beleid van CredSSP.

Wanneer u CredSSP-verificatie gebruikt, worden de gebruikers referenties door gegeven aan een externe computer die moet worden geverifieerd.
Dit type verificatie is ontworpen voor opdrachten die een externe sessie vanuit een andere externe sessie maken.
Als u bijvoorbeeld een achtergrond taak wilt uitvoeren op een externe computer, gebruikt u dit type verificatie.

De cmdlet voert de volgende acties uit:

- Hiermee wordt de WS-Management CredSSP-instelling op de client ( **\<localhost|computername\> \Client\Auth\CredSSP** ) opgehaald.
- Hiermee wordt de Windows CredSSP-beleids instelling **AllowFreshCredentials** opgehaald.
- Hiermee wordt de WS-Management CredSSP-instelling op de server opgehaald ( **\<localhost|computername\> \Service\Auth\CredSSP** ).

Let op: CredSSP-verificatie delegeert de gebruikers referenties van de lokale computer naar een externe computer.
Deze procedure verhoogt het beveiligings risico van de externe bewerking.
Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.

## VOORBEELDEN

### Voor beeld 1: CredSSP-configuratie weer geven

```
PS C:\> Get-WSManCredSSP
```

Met deze opdracht worden CredSSP-configuratie gegevens weer gegeven voor zowel de client als de server.

De uitvoer geeft aan dat deze computer of niet is geconfigureerd voor CredSSP.

Als de computer is geconfigureerd voor CredSSP, is dit de uitvoer:

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

Als de computer niet is geconfigureerd voor CredSSP, is dit de uitvoer:

`The machine is not configured to allow delegating fresh credentials.`

## PARAMETERS

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen
Deze cmdlet accepteert geen invoer.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* Als u CredSSP-verificatie wilt uitschakelen, gebruikt u de Disable-WSManCredSSP-cmdlet. Gebruik de cmdlet Enable-WSManCredSSP om CredSSP-verificatie in te scha kelen.

## GERELATEERDE KOPPELINGEN

[Connect-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Verbinding verbreken-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Testen-WSMan](Test-WSMan.md)
