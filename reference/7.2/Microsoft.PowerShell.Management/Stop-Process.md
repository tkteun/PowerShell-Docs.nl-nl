---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: 8c9e520f1f19444fd538fabee99a48ec08c69992
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705951"
---
# Stop-Process

## SAMENVATTING
Hiermee stopt u een of meer actieve processen.

## SYNTAXIS

### Id (standaard)

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Name

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Input object

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **Stop-process** stopt een of meer actieve processen.
U kunt een proces opgeven op basis van de proces naam of proces-ID (PID) of een proces object door geven om het proces te **stoppen**.
**Stop: het proces** werkt alleen voor processen die worden uitgevoerd op de lokale computer.

In Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell starten met de optie als administrator uitvoeren om een proces te stoppen dat geen eigendom is van de huidige gebruiker.
U wordt ook niet gevraagd om bevestiging tenzij u de para meter *confirm* opgeeft.

## VOORBEELDEN

### Voor beeld 1: alle exemplaren van een proces stoppen

```
PS C:\> Stop-Process -Name "notepad"
```

Met deze opdracht worden alle exemplaren van het klad blok-proces op de computer gestopt.
Elk exemplaar van Klad blok wordt uitgevoerd in een eigen proces.
Hierbij wordt de para meter *name* gebruikt voor het opgeven van de processen, die allemaal dezelfde naam hebben.
Als u de *id-* para meter zou gebruiken om dezelfde processen te stoppen, moet u de proces-id's van elk exemplaar van Klad blok vermelden.

### Voor beeld 2: een specifiek exemplaar van een proces stoppen

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

Met deze opdracht wordt een bepaald exemplaar van het klad blok-proces gestopt.
De proces-ID, 3952, wordt gebruikt om het proces te identificeren.
De para meter *confirm* stuurt Power shell door om u te vragen voordat het proces wordt gestopt.
Omdat de prompt de proces namein toevoegen aan de ID, is dit best practice.
Met de para meter *PassThru* wordt het proces object door gegeven aan de formatter voor weer gave.
Zonder deze para meter wordt er geen weer gegeven na de opdracht **Stop-process** .

### Voor beeld 3: een proces stoppen en detecteren dat het is gestopt

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

Met deze reeks opdrachten wordt het proces voor het berekenen gestart en gestopt, waarna processen worden gedetecteerd die zijn gestopt.

Met de eerste opdracht wordt een exemplaar van de reken machine gestart.

Met de tweede opdracht wordt **Get-process** gebruikt om een object op te halen dat het verwerkings proces vertegenwoordigt, en vervolgens opgeslagen in de variabele $p.

Met de derde opdracht wordt het berekenen van het proces gestopt.
De para meter *input object* wordt gebruikt om het object door te geven om het **proces te stoppen**.

De laatste opdracht haalt alle processen op de computer op die actief waren, maar die nu zijn gestopt.
Het gebruikt **Get-process** om alle processen op de computer op te halen.
De pijplijn operator (|) geeft de resultaten door aan de cmdlet Where-Object, die de waarden selecteert waar de eigenschap **HasExited** is $True.
**HasExited** is slechts één eigenschap van proces objecten.
Als u alle eigenschappen wilt zoeken, typt u `Get-Process | Get-Member` .

### Voor beeld 4: een proces stoppen dat niet het eigendom is van de huidige gebruiker

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

Deze opdrachten tonen het effect van het gebruik van *Force* om een proces te stoppen dat geen eigendom is van de gebruiker.

De eerste opdracht gebruikt **Get-process** om het Lsass-proces op te halen.
Een pijplijn operator verzendt het proces om te **stoppen,** om het te stoppen.
Zoals in de voorbeeld uitvoer wordt weer gegeven, mislukt de eerste opdracht met een bericht dat de toegang is geweigerd, omdat dit proces alleen kan worden gestopt door een lid van de groep Administrators op de computer.

Wanneer Power shell wordt geopend met de optie als administrator uitvoeren en de opdracht wordt herhaald, vraagt Power shell u om bevestiging.

Met de tweede opdracht wordt *geforceerd* dat de prompt wordt onderdrukt.
Als gevolg hiervan wordt het proces zonder bevestiging gestopt.

## PARAMETERS

### -Force

Hiermee worden de opgegeven processen gestopt zonder dat om bevestiging wordt gevraagd.
Standaard vraagt **het Stop proces** om bevestiging voordat een proces wordt gestopt dat geen eigendom is van de huidige gebruiker.

Als u de eigenaar van een proces wilt vinden, gebruikt u de `Get-CimInstance` cmdlet om een **Win32_Process** -object op te halen dat het proces vertegenwoordigt, en gebruikt u vervolgens de methode **GetOwner** van het object.

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

### -Id

Hiermee geeft u de proces-Id's op van de processen die moeten worden gestopt.
Als u meerdere Id's wilt opgeven, gebruikt u komma's om de Id's van elkaar te scheiden.
Als u de PID van een proces wilt vinden, typt u `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de proces objecten op die moeten worden gestopt.
Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de proces namen op van de processen die moeten worden gestopt.
U kunt meerdere proces namen typen, gescheiden door komma's of joker tekens gebruiken.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

Retourneert een object dat het proces vertegenwoordigt.
Deze cmdlet genereert standaard geen uitvoer.

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

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Diagnostics. process

U kunt een proces object door sluizen naar deze cmdlet.

## UITVOER

### Geen, System. Diagnostics. process

Deze cmdlet retourneert een **System. Diagnostics. process** -object dat het gestopte proces vertegenwoordigt, als u de para meter *PassThru* opgeeft.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* U kunt ook verwijzen naar **Stop-process** door de ingebouwde aliassen, **Kill** en **spps**. Zie about_Aliases voor meer informatie.

  U kunt ook de eigenschappen en methoden van het **Win32_Process** -object Windows Management Instrumentation (WMI) in Windows Power shell gebruiken.
Zie `Get-CimInstance` en de WMI-SDK voor meer informatie.

* Bij het stoppen van processen kan het stoppen van het proces en de services die afhankelijk zijn van het proces, worden gestopt.
In een extreem geval kan Windows stoppen met het stoppen van een proces.

## GERELATEERDE KOPPELINGEN

[Debug-proces](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-process](Start-Process.md)

[Stoppen-proces](Stop-Process.md)

[Wacht proces](Wait-Process.md)

