---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 381d7d9cb32ed4682729ad304e82bb994a21190d
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/02/2020
ms.locfileid: "93249296"
---
# Exit-PSHostProcess

## SAMENVATTING
Hiermee sluit u een interactieve sessie met een lokaal proces.

## SYNTAXIS

```
Exit-PSHostProcess [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **Exit-PSHostProcess** wordt een interactieve sessie gesloten met een lokaal proces dat u hebt geopend door de Enter-PSHostProcess-cmdlet uit te voeren. U voert de cmdlet **Exit-PSHostProcess** uit vanuit het proces, wanneer u klaar bent met het opsporen van fouten of het oplossen van problemen met een script dat in een proces wordt uitgevoerd.

## VOORBEELDEN

### Voor beeld 1: een proces afsluiten

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

In dit voor beeld hebt u in een actief proces gewerkt om fouten op te sporen in een script dat wordt uitgevoerd in een runs Pace in het proces, zoals beschreven in Enter-PSHostProcess. Nadat u de opdracht **Exit** hebt getypt om de fout opsporing af te sluiten, voert u de cmdlet **Exit-PSHostProcess** uit om uw interactieve sessie met het proces te sluiten.
De cmdlet sluit uw sessie in het proces en keert u terug naar de PS C:- \\ \> prompt.

## PARAMETERS

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Enter-PSHostProcess](Enter-PSHostProcess.md)
