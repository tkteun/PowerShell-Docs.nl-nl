---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: f4e29d06dc92d1d9aee61df7fd0c2de142fb1c7a
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253055"
---
# Write-Debug

## SAMENVATTING
Schrijft een debug-bericht naar de-console.

## SYNTAXIS

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## BESCHRIJVING

De `Write-Debug` cmdlet schrijft fout opsporingsgegevens van berichten naar de host vanuit een script of opdracht.

Standaard worden fout opsporings berichten niet weer gegeven in de-console, maar u kunt ze weer geven met de para meter **debug** of de `$DebugPreference` variabele.

## VOORBEELDEN

### Voor beeld 1: inzicht $DebugPreference

In dit voor beeld wordt een debug-bericht geschreven.

```powershell
Write-Debug "Cannot open file."
```

De standaard waarde van `$DebugPreference` is **SilentlyContinue**. Het bericht wordt daarom niet in de-console weer gegeven.

### Voor beeld 2: de waarde van $DebugPreference wijzigen

In dit voor beeld ziet u het effect van het wijzigen van de waarde van de `$DebugPreference` variabele. Eerst wordt de huidige waarde van `$DebugPreference` en poging tot het schrijven van een fout bericht weer gegeven. Vervolgens wijzigen we de waarde van `$DebugPreference` om **door te gaan** , waardoor fout opsporingsgegevens kunnen worden weer gegeven.

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

Zie about_Preference_Variables voor meer informatie over `$DebugPreference` . [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables)

### Voor beeld 3: de para meter debug gebruiken om $DebugPreference te negeren

De `Test-Debug` functie schrijft de waarde van de `$DebugPreference` variabele naar de Power shell-host en naar de stroom voor fout opsporing. In dit voor beeld gebruiken we de para meter **debug** om de `$DebugPreference` waarde te overschrijven.

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Continue
$DebugPreference is Continue
PS> $DebugPreference
SilentlyContinue
```

U ziet dat de waarde van `$DebugPreference` wijzigingen wanneer u de para meter **debug** gebruikt. Deze wijziging is alleen van invloed op het bereik van de functie. De waarde wordt niet beïnvloed buiten de functie.

Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie over de para meter common **debug** .

## PARAMETERS

### -Bericht

Hiermee geeft u het debug-bericht op dat naar de-console moet worden verzonden.

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

U kunt een teken reeks die een debug-bericht bevat, door sluizen naar `Write-Debug` .

## UITVOER

### Geen

`Write-Debug` schrijft alleen naar de stroom voor fout opsporing. Er worden geen objecten naar de pijp lijn geschreven.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Schrijf fout](Write-Error.md)

[Write-host](Write-Host.md)

[Write-output](Write-Output.md)

[Schrijf voortgang](Write-Progress.md)

[Write-verbose](Write-Verbose.md)

[Waarschuwing voor schrijven](Write-Warning.md)
