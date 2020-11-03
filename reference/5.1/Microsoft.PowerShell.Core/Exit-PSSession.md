---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/exit-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Exit-PSSession
ms.openlocfilehash: efe0e6c9287b3595988aa3ffc520ce46699cafda
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249968"
---
# Exit-PSSession

## SAMENVATTING
Hiermee beëindigt u een interactieve sessie met een externe computer.

## SYNTAXIS

```
Exit-PSSession [<CommonParameters>]
```

## BESCHRIJVING
De **Exit-PSSession** -cmdlet beëindigt interactieve sessies die u hebt gestart met behulp van de cmdlet Enter-PSSession.

U kunt ook het tref woord **Exit** gebruiken om een interactieve sessie te beëindigen.
Het effect is hetzelfde als het gebruik van **Exit-PSSession**.

## VOORBEELDEN

### Voor beeld 1: een interactieve sessie starten en stoppen

```
PS C:\> Enter-PSSession -computername Server01
Server01\PS> Exit-PSSession
PS C:\>
```

Met deze opdrachten wordt een interactieve sessie met de Server01 externe computer gestart en vervolgens gestopt.

### Voor beeld 2: een interactieve sessie starten en stoppen met behulp van een PSSession-object

```
PS C:\> $s = New-PSSession -ComputerName Server01
PS C:\> Enter-PSSession -Session $s
Server01\PS> Exit-PSSession
PS C:\> $s
Id Name            ComputerName    State    ConfigurationName
-- ----            ------------    -----    -----------------
1  Session1        Server01        Opened   Microsoft.PowerShell
```

Met deze opdrachten wordt een interactieve sessie gestart en gestopt met de Server01-computer die gebruikmaakt van een Windows Power shell-sessie ( **PSSession** ).

Omdat de interactieve sessie is gestart met een Windows Power shell-sessie, is de **PSSession** nog steeds beschikbaar wanneer de interactieve sessie wordt beëindigd.
Als u de para meter *ComputerName* gebruikt, wordt door **Enter-PSSession** een tijdelijke sessie gemaakt die wordt gesloten wanneer de interactieve sessie wordt beëindigd.

De eerste opdracht maakt gebruik van de New-PSSession cmdlet om een **PSSession** te maken op de Server01-computer.
Met de opdracht slaat u de **PSSession** op in de variabele $s.

Met de tweede opdracht wordt **Enter-PSSession** gebruikt om een interactieve sessie te starten met behulp van de **PSSession** in $s.

De derde opdracht maakt gebruik van **Exit-PSSession** om de interactieve sessie te beëindigen.

Met de laatste opdracht wordt de **PSSession** weer gegeven in de variabele $s.
De eigenschap **State** geeft aan dat de **PSSession** nog geopend is en beschikbaar is voor gebruik.

### Voor beeld 3: het sleutel woord exit gebruiken om een sessie te stoppen

```
PS C:\> Enter-PSSession -computername Server01
Server01\PS> exit
PS C:\>
```

In dit voor beeld wordt het sleutel woord **Exit** gebruikt om een interactieve sessie te stoppen die is gestart met **Enter-PSSession**.
Het sleutel woord **Exit** heeft hetzelfde effect als het gebruik van **Exit-PSSession**.

## PARAMETERS

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen
U kunt geen objecten naar deze cmdlet pipeen.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

* Deze cmdlet heeft alleen de algemene para meters.


## GERELATEERDE KOPPELINGEN

[Connect-PSSession](Connect-PSSession.md)

[Verbinding verbreken-PSSession](Disconnect-PSSession.md)

[Enter-PSSession](Enter-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Invoke-opdracht](Invoke-Command.md)

[New-PSSession](New-PSSession.md)

[Receive-PSSession](Receive-PSSession.md)

[Remove-PSSession](Remove-PSSession.md)
