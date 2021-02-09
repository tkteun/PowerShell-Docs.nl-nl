---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/08/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: b1827929c53560cb261cd7b3ba1e5bd407c25700
ms.sourcegitcommit: 3a1d80e27438976101f216b8c3d623c61b868db8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/09/2021
ms.locfileid: "99975087"
---
# Exit-PSSession

## Samen vatting
Hiermee beëindigt u een interactieve sessie met een externe computer.

## SYNTAXIS

```
Exit-PSSession [<CommonParameters>]
```

## Description

De `Exit-PSSession` cmdlet beëindigt interactieve sessies die u hebt gestart met behulp van de `Enter-PSSession` cmdlet.

U kunt ook het `exit` tref woord gebruiken om een interactieve sessie te beëindigen. Het effect is hetzelfde als het gebruiken `Exit-PSSession` .

## Voorbeelden

### Voor beeld 1: een interactieve sessie starten en stoppen

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> Exit-PSSession
PS>
```

Met deze opdrachten wordt een interactieve sessie met de Server01 externe computer gestart en vervolgens gestopt.

### Voor beeld 2: een interactieve sessie starten en stoppen met behulp van een PSSession-object

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

Met deze opdrachten wordt een interactieve sessie gestart en gestopt met de Server01-computer die gebruikmaakt van een Power shell-sessie (**PSSession**).

Omdat de interactieve sessie is gestart met een Power shell-sessie, is de **PSSession** nog steeds beschikbaar wanneer de interactieve sessie wordt beëindigd. Als u de para meter _ComputerName_ gebruikt, `Enter-PSSession` wordt er een tijdelijke sessie gemaakt die wordt gesloten wanneer de interactieve sessie wordt beëindigd.

De eerste opdracht gebruikt de `New-PSSession` cmdlet om een **PSSession** te maken op de Server01-computer. Met de opdracht slaat u de **PSSession** op in de `$s` variabele.

De tweede opdracht wordt gebruikt `Enter-PSSession` om een interactieve sessie te starten met behulp van de **PSSession** in `$s` .

De derde opdracht wordt gebruikt `Exit-PSSession` om de interactieve sessie te stoppen.

Met de laatste opdracht wordt de **PSSession** in de variabele weer gegeven `$s` . De eigenschap **State** geeft aan dat de **PSSession** nog geopend is en beschikbaar is voor gebruik.

### Voor beeld 3: het sleutel woord exit gebruiken om een sessie te stoppen

```powershell
PS> Enter-PSSession -ComputerName Server01
Server01\PS> exit
PS>
```

In dit voor beeld wordt het `exit` sleutel woord gebruikt voor het stoppen van een interactieve sessie die is gestart met `Enter-PSSession` . Het `exit` sleutel woord heeft hetzelfde effect als het gebruik van `Exit-PSSession` .

## Parameters

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## Invoerwaarden

### Geen

U kunt geen objecten naar deze cmdlet pipeen.

## Uitvoerwaarden

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## Notities

Deze cmdlet heeft alleen de algemene para meters.

## GERELATEERDE KOPPELINGEN

[Connect-PSSession](Connect-PSSession.md)

[Verbinding verbreken-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-opdracht](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)
