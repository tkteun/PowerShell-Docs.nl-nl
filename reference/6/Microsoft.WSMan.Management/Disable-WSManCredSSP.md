---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 6b6cf6b4056dd5907f6a43cd9cf6d491bc7512b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250086"
---
# Disable-WSManCredSSP

## SAMENVATTING
Hiermee schakelt u CredSSP-verificatie op een computer uit.

## SYNTAXIS

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Disable-WSManCredSSP** wordt CredSSP-verificatie (Credential Security Support Provider) uitgeschakeld op een client of op een Server computer.
Wanneer CredSSP-verificatie wordt gebruikt, worden de gebruikers referenties door gegeven aan een externe computer die moet worden geverifieerd.

Gebruik deze cmdlet om CredSSP op de client uit te scha kelen door de client op te geven in de para meter *Role* .
Met deze cmdlet worden de volgende acties uitgevoerd:

- Hiermee schakelt u CredSSP op de client uit. Met deze cmdlet wordt de WS-Management instelling **\<localhost|computername\> \Client\Auth\CredSSP** ingesteld op ONWAAR.
- Hiermee verwijdert u elke WSMan/*-instelling uit de **AllowFreshCredentials** van het Windows-CredSSP-beleid op de client.

Gebruik deze cmdlet om CredSSP op de server uit te scha kelen door de server *functie* op te geven.
Met deze cmdlet wordt de volgende actie uitgevoerd:

- Hiermee schakelt u CredSSP op de server uit. Met deze cmdlet wordt de WS-Management instelling **\<localhost|computername\> \Service\Auth\CredSSP** ingesteld op ONWAAR.

Let op: CredSSP-verificatie delegeert de gebruikers referenties van de lokale computer naar een externe computer.
Deze procedure verhoogt het beveiligings risico van de externe bewerking.
Als er is geknoeid met de externe computer, kunnen de referenties worden gebruikt om de netwerk sessie te beheren wanneer er referenties worden door gegeven.

## VOORBEELDEN

### Voor beeld 1: CredSSP uitschakelen op een client

```
PS C:\> Disable-WSManCredSSP -Role Client
```

Met deze opdracht wordt CredSSP op de client uitgeschakeld, waardoor overdracht naar servers wordt voor komen.

### Voor beeld 2: CredSSP uitschakelen op een server

```
PS C:\> Disable-WSManCredSSP -Role Server
```

Met deze opdracht wordt CredSSP op de server uitgeschakeld, waardoor delegering van clients wordt voor komen.

## PARAMETERS

### -Rol
Hiermee wordt aangegeven of CredSSP moet worden uitgeschakeld als een client of als server.
De acceptabele waarden voor deze para meter zijn: client en server.

Als u de client opgeeft, voert deze cmdlet de volgende acties uit:

- Hiermee schakelt u CredSSP op de client uit. Met deze cmdlet wordt WS-Management instelling **\<localhost|computername\> \Client\Auth\CredSSP** ingesteld op ONWAAR.
- Hiermee verwijdert u elke WSMan/*-instelling uit de **AllowFreshCredentials** van het Windows-CredSSP-beleid op de client.

Als u server opgeeft, voert deze cmdlet de volgende actie uit:

- Hiermee schakelt u CredSSP op de server uit. Met deze cmdlet wordt de WS-Management instelling **\<localhost|computername\> \Service\Auth\CredSSP** ingesteld op ONWAAR.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
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

* Gebruik de cmdlet Enable-WSManCredSSP om CredSSP-verificatie in te scha kelen.

*

## GERELATEERDE KOPPELINGEN

[Connect-WSMan](Connect-WSMan.md)

[Verbinding verbreken-WSMan](Disconnect-WSMan.md)

[Enable-WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Testen-WSMan](Test-WSMan.md)
