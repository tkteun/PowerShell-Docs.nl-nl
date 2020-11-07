---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pshostprocess?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSHostProcess
ms.openlocfilehash: 1734758d34e89020f579fffa217cef58eb222736
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344045"
---
# Exit-PSHostProcess

## SAMENVATTING
Hiermee sluit u een interactieve sessie met een lokaal proces.

## SYNTAXIS

```
Exit-PSHostProcess [<CommonParameters>]
```

## BESCHRIJVING

De `Exit-PSHostProcess` cmdlet sluit een interactieve sessie met een lokaal proces dat u hebt geopend door de cmdlet uit te voeren `Enter-PSHostProcess` . U voert de `Exit-PSHostProcess` cmdlet uit vanuit het proces, wanneer u klaar bent met het opsporen van fouten of het oplossen van problemen met een script dat in een proces wordt uitgevoerd. Vanaf Power shell 6,2 wordt deze cmdlet ondersteund op niet-Windows-platforms.

## VOORBEELDEN

### Voor beeld 1: een proces afsluiten

```
[Process:1520]: PS>  Exit-PSHostProcess
PS>
```

In dit voor beeld hebt u in een actief proces gewerkt om fouten op te sporen in een script dat wordt uitgevoerd in een runs Pace in het proces, zoals beschreven in `Enter-PSHostProcess` . Nadat u de `exit` opdracht voor het fout opsporingsprogramma hebt getypt, voert u de `Exit-PSHostProcess` cmdlet uit om uw interactieve sessie met het proces te sluiten.
De cmdlet sluit uw sessie in het proces en keert u terug naar de `PS C:\>` prompt.

## PARAMETERS

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Enter-PSHostProcess](Enter-PSHostProcess.md)
