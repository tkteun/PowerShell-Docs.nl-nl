---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: 5553f61038c10d0c7c251609f729d157c53b03b9
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93252982"
---
# Write-Warning

## SAMENVATTING
Hiermee schrijft u een waarschuwings bericht.

## SYNTAXIS

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## BESCHRIJVING

De `Write-Warning` cmdlet schrijft een waarschuwings bericht naar de Power shell-host. De reactie op de waarschuwing is afhankelijk van de waarde van de gebruikers `$WarningPreference` variabele en het gebruik van de gemeen schappelijke para meter **WarningAction** .

## VOORBEELDEN

### Voor beeld 1: een waarschuwings bericht schrijven

Met deze opdracht wordt het bericht ' waarschuwing: dit is alleen een test waarschuwing ' weer gegeven.

```powershell
Write-Warning "This is only a test warning."
```

### Voor beeld 2: een teken reeks door geven Write-Warning

Met deze opdracht wordt aangegeven dat u een pijplijn operator () kunt gebruiken `|` om een teken reeks naar te verzenden `Write-Warning` .
U kunt de teken reeks in een variabele opslaan, zoals in deze opdracht wordt weer gegeven, of de teken reeks rechtstreeks naar `Write-Warning` .

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### Voor beeld 3: de $WarningPreference variabele instellen en een waarschuwing schrijven

In dit voor beeld wordt het effect van de waarde van de `$WarningPreference` variabele op een opdracht weer gegeven `Write-Warning` .

```powershell
PS> $WarningPreference
Continue
PS> Write-Warning "This is only a test warning."
This is only a test warning.
PS> $WarningPreference = "SilentlyContinue"
PS> Write-Warning "This is only a test warning."
PS> $WarningPreference = "Stop"
PS> Write-Warning "This is only a test warning."
WARNING: This is only a test message.
Write-Warning : Command execution stopped because the shell variable "WarningPreference" is set to Stop.
At line:1 char:14
     + Write-Warning <<<<  "This is only a test message."
```

Met de eerste opdracht wordt de standaard waarde van de `$WarningPreference` variabele weer gegeven `Continue` . Als u een waarschuwing schrijft, wordt het waarschuwings bericht weer gegeven en wordt de uitvoering voortgezet.

Wanneer u de waarde van de `$WarningPreference` variabele wijzigt, wordt het effect van de `Write-Warning` opdracht opnieuw gewijzigd. Een waarde van `SilentlyContinue` onderdrukt de waarschuwing. Met de waarde `Stop` wordt de waarschuwing weer gegeven en wordt de uitvoering van de opdracht gestopt.

Zie about_Preference_Variables voor meer informatie over de `$WarningPreference` variabele [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).

### Voor beeld 4: de para meter WarningAction instellen en een waarschuwing schrijven

In dit voor beeld ziet u het effect van de algemene para meter **WarningAction** voor een `Write-Warning` opdracht. U kunt de algemene para meter **WarningAction** gebruiken met elke cmdlet om te bepalen hoe Power shell reageert op waarschuwingen die voortkomen uit die opdracht. De algemene para meter **WarningAction** overschrijft de waarde van de `$WarningPreference` enige voor die specifieke opdracht.

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

Met deze opdracht wordt de `Write-Warning` cmdlet gebruikt om een waarschuwing weer te geven. De gemeen schappelijke para meter **WarningAction** met de waarde query stuurt het systeem om de gebruiker te vragen wanneer de opdracht een waarschuwing weergeeft.

Zie [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md)voor meer informatie over de algemene para meter **WarningAction** .

## PARAMETERS

### -Bericht
Hiermee geeft u het waarschuwings bericht.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks die de waarschuwing bevat, door sluizen naar `Write-Warning` .

## UITVOER

### Geen

`Write-Warning` schrijft alleen naar de waarschuwings stroom. Er wordt geen andere uitvoer gegenereerd.

## OPMERKINGEN

De standaard waarde voor de `$WarningPreference` variabele is `Continue` , waarbij de waarschuwing wordt weer gegeven en de opdracht vervolgens blijft uitvoeren. Als u geldige waarden voor een voorkeurs variabele wilt bepalen, zoals `$WarningPreference` , stelt u deze in op een teken reeks van wille keurige tekens, zoals "ABC". Het gegenereerde fout bericht bevat een lijst met de geldige waarden.

## GERELATEERDE KOPPELINGEN

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Schrijf fouten opsporen](Write-Debug.md)

[Schrijf fout](Write-Error.md)

[Write-host](Write-Host.md)

[Write-Information](Write-Information.md)

[Write-output](Write-Output.md)

[Schrijf voortgang](Write-Progress.md)

[Write-verbose](Write-Verbose.md)
