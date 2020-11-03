---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: 08c9d61f210761e2ed7a3a5014812b2bd362201b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250331"
---
# Enable-WSManTrace

## SAMENVATTING
Start een logboek registratie sessie met de WSMan-providers ingeschakeld.

## SYNTAXIS

```
Enable-WSManTrace [<CommonParameters>]
```

## BESCHRIJVING
Met deze cmdlet wordt een logboek registratie sessie gestart met de WSMan-providers ingeschakeld. De volgende gebeurtenis providers zijn ingeschakeld:

- Gebeurtenis door sturen
- IpmiDrv
- IPMIPrv
- WinRM
- WinrsCmd
- WinrsExe
- WinrsMgr
- WSManProvHost

De sessie heeft de naam ' wsmlog '.

Deze cmdlet maakt gebruik van de `Start-Trace` cmdlet.

U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.

## VOORBEELDEN

### Voor beeld 1: een WSMan-logboek registratie sessie starten.

```powershell
Enable-WSManTrace
```

## PARAMETERS

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Gebeurtenis tracering](/windows/desktop/ETW/event-tracing-portal)

[Start-traceren](start-trace.md)

[Disable-WSManTrace](Disable-WSManTrace.md)
