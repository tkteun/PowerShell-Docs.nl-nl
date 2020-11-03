---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: f6b14ea6cda7d83792f7b51b854471a2cb62bfb5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249384"
---
# Enable-PSWSManCombinedTrace

## SAMENVATTING
Start een logboek registratie sessie met de WSMan-en Power shell-providers ingeschakeld.

## SYNTAXIS

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## BESCHRIJVING

Met deze cmdlet wordt een logboek registratie sessie gestart met de volgende Power shell-providers ingeschakeld:

- Micro soft-Windows-Power shell
- Micro soft-Windows-WinRM

De sessie heeft de naam ' PSTrace '.

Deze cmdlet maakt gebruik van de `Start-Trace` cmdlet.

U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.

## VOORBEELDEN

### Voor beeld 1: een gecombineerde logboek registratie sessie starten

```powershell
Enable-PSWSManCombinedTrace
```

## PARAMETERS

### -DoNotOverwriteExistingTrace

Standaard worden de gebeurtenissen geschreven naar ' $pshome \Traces\PSTrace.etl '. Als deze para meter wordt gebruikt, maakt de cmdlet een unieke bestands naam: "$pshome \Traces\ PSTrace_ {GUID}. etl"

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

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

## UITVOER

### Geen

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Gebeurtenis tracering](/windows/desktop/ETW/event-tracing-portal)

[Start-traceren](start-trace.md)

[Disable-PSWSManCombinedTrace](Disable-PSWSManCombinedTrace.md)
