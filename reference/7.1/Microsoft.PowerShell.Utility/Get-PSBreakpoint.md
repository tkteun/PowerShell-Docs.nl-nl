---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 6afabaf46907d317ec864519a658c500466d4c38
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250209"
---
# Get-PSBreakpoint

## SAMENVATTING
Hiermee worden de onderbrekings punten opgehaald die in de huidige sessie zijn ingesteld.

## SYNTAXIS

### Script (standaard)

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### Variabele

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### Opdracht

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### Type

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### Id

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **Get-PSBreakPoint** haalt de onderbrekings punten op die in de huidige sessie zijn ingesteld.
U kunt de cmdlet-para meters gebruiken voor het ophalen van bepaalde onderbrekings punten.

Een onderbrekings punt is een Point in een opdracht of script waar uitvoering tijdelijk wordt gestopt zodat u de instructies kunt onderzoeken.
**Get-PSBreakpoint** is een van de verschillende cmdlets die zijn ontworpen voor het opsporen van fouten in Power shell-scripts en-opdrachten. Zie about_Debuggers voor meer informatie over de Power Shell-fout opsporing.

## VOORBEELDEN

### Voor beeld 1: alle onderbrekings punten ophalen voor alle scripts en functies

```
PS C:\> Get-PSBreakpoint
```

Met deze opdracht worden alle onderbrekings punten opgehaald die zijn ingesteld voor alle scripts en functies in de huidige sessie.

### Voor beeld 2: onderbrekings punten ophalen op ID

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

Met deze opdracht wordt het onderbrekings punt met onderbrekings punt-ID 2 opgehaald.

### Voor beeld 3: een ID Get-PSBreakpoint

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

Deze opdrachten laten zien hoe een onderbrekings punt kan worden verkregen door een onderbrekings punt-ID op te **halen-PSBreakpoint**.

De eerste opdracht gebruikt de cmdlet Set-PSBreakpoint om een onderbrekings punt te maken voor de functie increment in het Sample.ps1 script. Het object onderbrekings punt wordt opgeslagen in de variabele $B.

De tweede opdracht maakt gebruik van de punt operator (.) om de eigenschap ID van het object onderbrekings punt in de variabele $B te verkrijgen. Er wordt een pijplijn operator (|) gebruikt om de ID te verzenden naar de cmdlet **Get-PSBreakpoint** .

Als gevolg hiervan **krijgt Get-PSBreakpoint** het onderbrekings punt met de opgegeven id.

### Voor beeld 4: onderbrekings punten in opgegeven script bestanden ophalen

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

Met deze opdracht worden alle onderbrekings punten in de Sample.ps1-en SupportScript.ps1-bestanden opgehaald.

Met deze opdracht worden geen andere onderbrekings punten opgehaald die kunnen worden ingesteld in andere scripts of op functies in de sessie.

### Voor beeld 5: onderbrekings punten in opgegeven cmdlets ophalen

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

Met deze opdracht worden alle opdracht onderbrekings punten opgehaald die zijn ingesteld op Read-Host of Write-Host opdrachten in het Sample.ps1-bestand.

### Voor beeld 6: opdracht onderbrekings punten ophalen in een opgegeven bestand

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

Met deze opdracht worden alle opdracht onderbrekings punten in het Sample.ps1-bestand opgehaald.

### Voor beeld 7: onderbrekings punten ophalen per variabele

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

Met deze opdracht worden onderbrekings punten opgehaald die zijn ingesteld voor de $Index en $Swap variabelen in de huidige sessie.

### Voor beeld 8: alle regel-en variabele onderbrekings punten in een bestand ophalen

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

Met deze opdracht worden alle regel-en variabele onderbrekings punten in het Sample.ps1 script opgehaald.

## PARAMETERS

### -Opdracht

Hiermee geeft u een matrix met opdracht onderbrekings punten op die zijn ingesteld voor de opgegeven opdracht namen.
Voer de opdracht namen in, zoals de naam van een cmdlet of functie.

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee geeft u de onderbrekings punt-Id's op die met deze cmdlet worden opgehaald.
Geef de Id's op in een lijst met door komma's gescheiden waarden.
U kunt ook punt-Id's van de pijp **lijn naar Get-PSBreakpoint**.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Script

Hiermee geeft u een matrix met scripts die de onderbrekings punten bevatten.
Voer het pad (optioneel) en de namen van een of meer script bestanden in.
Als u het pad weglaat, is de standaard locatie de huidige map.

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Type

Hiermee geeft u een matrix van typen onderbrekings punten op die met deze cmdlet worden opgehaald.
Voer een of meer typen in.
De aanvaardbare waarden voor deze parameter zijn:

- Lijn
- Opdracht
- Variabele

U kunt ook de PSBreakPoint van het type pijp **lijn ophalen**.

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Variabele

Hiermee geeft u een matrix met variabele onderbrekings punten op die zijn ingesteld voor de opgegeven namen van variabelen.
Voer de namen van de variabelen in zonder dollar tekens.

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie about_CommonParameters (voor meer informatie https://go.microsoft.com/fwlink/?LinkID=113216) .

## INVOER

### System. Int32, micro soft. Power shell. commands. BreakpointType

U kunt de onderbrekings punt-Id's en typen onderbrekings punten voor **Get-PSBreakPoint**.

## UITVOER

### System. Management. Automation. Break Point

**Get-PSBreakPoint** retourneert objecten die de onderbrekings punten in de sessie vertegenwoordigen.

## OPMERKINGEN

* U kunt **Get-PSBreakpoint** of diens alias gebruiken, "GBP".

## GERELATEERDE KOPPELINGEN

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

