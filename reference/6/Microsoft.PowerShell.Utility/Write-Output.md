---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: 75b046ea6b11be3e4d87ed9db3e011a1f00d6ef5
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93252984"
---
# Write-Output

## SAMENVATTING
Hiermee worden de opgegeven objecten verzonden naar de volgende opdracht in de pijp lijn. Als de opdracht de laatste opdracht in de pijp lijn is, worden de objecten weer gegeven in de-console.

## SYNTAXIS

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## BESCHRIJVING

De `Write-Output` cmdlet verzendt het opgegeven object in de pijp lijn naar de volgende opdracht.
Als de opdracht de laatste opdracht in de pijp lijn is, wordt het object in de-console weer gegeven.

`Write-Output` Hiermee worden objecten verzonden naar de primaire pijp lijn, ook wel bekend als de "uitvoer stroom" of de "pijp lijn slagen". Als u fout objecten wilt verzenden naar de fout pijplijn, gebruikt u schrijf fout.

Deze cmdlet wordt doorgaans gebruikt in scripts om teken reeksen en andere objecten in de-console weer te geven. Een van de ingebouwde aliassen voor `Write-Output` is `echo` en vergelijkbaar met andere shells die gebruikmaken van `echo` , het standaard gedrag is om de uitvoer aan het einde van een pijp lijn weer te geven. In Power shell is het over het algemeen niet nodig om de cmdlet te gebruiken in gevallen waarin de uitvoer standaard wordt weer gegeven. `Get-Process | Write-Output` is bijvoorbeeld gelijk aan `Get-Process`. Of `echo "Home directory: $HOME"` kan worden geschreven, `"Home directory: $HOME"` .

Standaard `Write-Output` inventariseert de verzamelingen die aan de cmdlet worden door gegeven. Kan echter `Write-Output` ook worden gebruikt voor het door geven van verzamelingen in de pijp lijn als één object met de para meter ' **enumerate** '.

## VOORBEELDEN

### Voor beeld 1: objecten ophalen en naar de console schrijven

```powershell
$P = Get-Process
Write-Output $P
```

De eerste opdracht haalt processen op die worden uitgevoerd op de computer en slaat deze op in de `$P` variabele.

Met de tweede en derde opdracht worden de proces objecten in de-console weer gegeven `$P` .

### Voor beeld 2: uitvoer door geven naar een andere cmdlet

```powershell
Write-Output "test output" | Get-Member
```

Met deze opdracht pipet u de test uitvoer teken reeks naar de `Get-Member` cmdlet, waarmee de leden van de klasse **System. String** worden weer gegeven, waarbij wordt aangetoond dat de teken reeks is door gegeven aan de pijp lijn.

### Voor beeld 3: inventarisatie in uitvoer onderdrukken

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

Met deze opdracht wordt de para meter ' niet **opsommen** ' toegevoegd om een verzameling of matrix als één object te behandelen via de pijp lijn.

## PARAMETERS

### -Input object

Hiermee geeft u de objecten op die de pijp lijn moeten verzenden. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Opsomming

Standaard wordt de uitvoer van de `Write-Output` cmdlet altijd opgesomd. De para meter ' niet **opsommen** ' onderdrukt het standaard gedrag en voor komt het `Write-Output` opsommen van uitvoer. De para meter voor de **opsomming** heeft geen effect als de opdracht tussen haakjes wordt ingepakt, omdat de opsomming afdwingt. `(Write-Output 1,2,3)`De matrix wordt bijvoorbeeld nog steeds opgesomd.

> [!NOTE]
> Deze switch werkt alleen goed met Power shell Core 6,2 en hoger. In oudere versies van Power shell core wordt de verzameling nog steeds geïnventariseerd, zelfs met het gebruik van deze switch.

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

### System. Management. Automation. PSObject

U kunt objecten door sluizen naar `Write-Output` .

## UITVOER

### System. Management. Automation. PSObject

`Write-Output` retourneert de objecten die als invoer worden verzonden.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[T-object](Tee-Object.md)

[Schrijf fouten opsporen](Write-Debug.md)

[Schrijf fout](Write-Error.md)

[Write-host](Write-Host.md)

[Write-Information](Write-Information.md)

[Schrijf voortgang](Write-Progress.md)

[Write-verbose](Write-Verbose.md)

[Waarschuwing voor schrijven](Write-Warning.md)
