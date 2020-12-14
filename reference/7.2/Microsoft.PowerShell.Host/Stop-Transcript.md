---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: 16b41711e98276fee37d56f77f57e7372daa4cf3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705750"
---
# Stop-Transcript

## SAMENVATTING
Hiermee wordt een transcript gestopt.

## SYNTAXIS

```
Stop-Transcript [<CommonParameters>]
```

## BESCHRIJVING

De `Stop-Transcript` cmdlet stopt een transcript dat is gestart door de `Start-Transcript` cmdlet.
U kunt ook een sessie beëindigen om een transcript te stoppen.

## VOORBEELDEN

### Voor beeld 1: alle transcripten stoppen

```powershell
Stop-Transcript
```

Met deze opdracht worden alle transcripten gestopt.

## PARAMETERS

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### System. String

Deze cmdlet retourneert een teken reeks die een status bericht en het pad naar het uitvoer bestand bevat.

## OPMERKINGEN

* Als er geen transcript is gestart, mislukt de opdracht.

*

## GERELATEERDE KOPPELINGEN

[Start-transcript](Start-Transcript.md)

