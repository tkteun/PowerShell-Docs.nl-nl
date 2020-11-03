---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 90cb571f93243e6fbc59970e5602911e17e25ec7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250334"
---
# Disable-WSManTrace

## SAMENVATTING
Stop de WSMan-logboek registratie sessie die is gestart door Enable-WSManTrace.

## SYNTAXIS

```
Disable-WSManTrace [<CommonParameters>]
```

## BESCHRIJVING
Met deze cmdlet stopt u de WSMan-logboek registratie sessie die is gestart door Enable-WSManTrace.

Deze cmdlet maakt gebruik van de `Stop-Trace` cmdlet.

U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.

## VOORBEELDEN

### Voor beeld 1: WSMan-tracering stoppen

```powershell
Disable-WSManTrace
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

[Stoppen-traceren](stop-trace.md)

[Enable-WSManTrace](Enable-WSManTrace.md)
