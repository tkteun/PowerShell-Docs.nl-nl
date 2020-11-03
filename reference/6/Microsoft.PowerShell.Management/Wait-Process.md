---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: 97b29f13fd1106a04204f97f02d82e9760fa41ae
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250002"
---
# Wait-Process

## SAMENVATTING
Er wordt gewacht tot de processen zijn gestopt voordat meer invoer wordt geaccepteerd.

## SYNTAXIS

### Naam (standaard)

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### Id

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### Input object

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## BESCHRIJVING

De **wacht-process-** cmdlet wacht totdat een of meer actieve processen worden gestopt voordat de invoer wordt geaccepteerd.
In de Power shell-console onderdrukt deze cmdlet de opdracht prompt totdat de processen zijn gestopt.
U kunt een proces naam of proces-ID (PID) opgeven, of een proces object pipeen dat moet worden **gewacht**.

Een **ogen blik geduld,** werkt alleen voor processen die worden uitgevoerd op de lokale computer.

## VOORBEELDEN

### Voor beeld 1: een proces stoppen en wachten

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

In dit voor beeld wordt het klad blok-proces gestopt en wordt gewacht tot het proces wordt gestopt voordat de volgende opdracht wordt voortgezet.

De eerste opdracht maakt gebruik van de cmdlet **Get-process** om de id van het klad blok-proces op te halen.
De ID wordt opgeslagen in de variabele $nid.

De tweede opdracht gebruikt de cmdlet Stop-Process om het proces te stoppen met de ID die is opgeslagen in $nid.

De derde opdracht gebruikt **wacht proces** om te wachten tot het klad blok-proces is gestopt.
De para meter *id* van **wacht proces** wordt gebruikt om het proces te identificeren.

### Voor beeld 2: een proces opgeven

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

Met deze opdrachten worden drie verschillende methoden weer gegeven voor het opgeven van een proces dat moet worden **gewacht**.
Met de eerste opdracht wordt het klad blok-proces opgehaald en opgeslagen in de variabele $p.

De tweede opdracht gebruikt de *id-* para meter, de derde opdracht gebruikt de para meter *name* en de vierde opdracht maakt gebruik van de para meter *input object* .

Deze opdrachten hebben dezelfde resultaten en kunnen door elkaar worden gebruikt.

### Voor beeld 3: wachten op processen gedurende een opgegeven periode

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

Met deze opdracht wordt 30 seconden gewacht totdat de processen van Outlook en Winword worden gestopt.
Als beide processen niet worden gestopt, wordt in de cmdlet een niet-afsluit fout weer gegeven en de opdracht prompt.

## PARAMETERS

### -Id

Hiermee geeft u de proces-Id's van de processen.
Als u meerdere Id's wilt opgeven, gebruikt u komma's om de Id's van elkaar te scheiden.
Als u de PID van een proces wilt vinden, typt u `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de processen aan door proces objecten te verzenden.
Voer een variabele in die de proces objecten bevat, of typ een opdracht of expressie waarmee de proces objecten worden opgehaald, zoals de cmdlet Get-Process.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de proces namen van de processen.
Als u meerdere namen wilt opgeven, gebruikt u komma's om de namen van elkaar te scheiden.
Joker tekens worden niet ondersteund.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Time-out

Hiermee geeft u de maximum tijd, in seconden, op dat met deze cmdlet wordt gewacht tot de opgegeven processen worden gestopt.
Als dit interval is verlopen, wordt de opdracht weer gegeven met een niet-afsluit fout die de processen vermeld die nog worden uitgevoerd, en eindigt de wacht tijd.
Standaard is er geen time-out.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Diagnostics. process

U kunt een proces object door sluizen naar deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* Deze cmdlet maakt gebruik van de methode **WaitForExit** van de klasse System. Diagnostics. process. Zie de Microsoft .NET Framework SDK voor meer informatie over deze methode.

*

## GERELATEERDE KOPPELINGEN

[Debug-proces](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-process](Start-Process.md)

[Stoppen-proces](Stop-Process.md)

[Wacht proces](Wait-Process.md)
