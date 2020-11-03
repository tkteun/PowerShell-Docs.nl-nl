---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: 5968c51f04199d59d3514cdc85ba3f15d02475a4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250372"
---
# Set-PSBreakpoint

## SAMENVATTING
Hiermee stelt u een onderbrekings punt in voor een regel, opdracht of variabele.

## SYNTAXIS

### Regel (standaard)

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### Opdracht

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### Variabele

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Set-PSBreakpoint` cmdlet wordt een onderbrekings punt ingesteld in een script of in een opdracht die wordt uitgevoerd in de huidige sessie. U kunt gebruiken `Set-PSBreakpoint` om een onderbrekings punt in te stellen voordat u een script uitvoert of een opdracht uitvoert, of tijdens fout opsporing, wanneer deze op een ander onderbrekings punt wordt gestopt.

`Set-PSBreakpoint` kan geen onderbrekings punt instellen op een externe computer. Als u fouten wilt opsporen in een script op een externe computer, kopieert u het script naar de lokale computer en voert u de fout opsporing lokaal uit.

`Set-PSBreakpoint`Met elke opdracht maakt u een van de volgende drie typen onderbrekings punten:

- Regel onderbrekings punt: stelt onderbrekings punten in voor bepaalde lijn-en kolom coördinaten.
- Opdracht onderbrekings punt: Hiermee stelt u onderbrekings punten in voor opdrachten en functies.
- Variabele onderbrekings punt: Hiermee stelt u onderbrekings punten in voor variabelen.

U kunt een onderbrekings punt op meerdere regels, opdrachten of variabelen instellen in één `Set-PSBreakpoint` opdracht, maar met elke `Set-PSBreakpoint` opdracht wordt slechts één type onderbrekings punt ingesteld.

Bij een onderbrekings punt wordt het uitvoeren van Power shell tijdelijk gestopt en krijgt de fout opsporing controle. De opdracht prompt wordt gewijzigd in `DBG\>` en er worden een aantal opdrachten voor fout opsporing beschikbaar voor gebruik. U kunt echter de **actie** parameter gebruiken om een ander antwoord op te geven, zoals de voor waarden voor het onderbrekings punt of de instructies voor het uitvoeren van aanvullende taken, zoals logboek registratie of diagnose.

De `Set-PSBreakpoint` cmdlet is een van de verschillende cmdlets die zijn ontworpen voor het opsporen van fouten in Power shell-scripts.
Zie [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)voor meer informatie over de Power Shell-fout opsporing.

## VOORBEELDEN

### Voor beeld 1: een onderbrekings punt op een regel instellen

In dit voor beeld wordt een onderbrekings punt ingesteld op regel 5 in het Sample.ps1 script. Wanneer het script wordt uitgevoerd, stopt de uitvoering onmiddellijk voordat regel 5 wordt uitgevoerd.

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

Wanneer u een nieuw onderbrekings punt op regel nummer instelt, `Set-PSBreakpoint` genereert de cmdlet een regel onderbrekings object ( **System. Management. Automation. LineBreakpoint** ) met daarin de ONDERBREKINGS punt-id en het aantal treffers.

### Voor beeld 2: een onderbrekings punt instellen voor een functie

In dit voor beeld wordt een onderbrekings punt voor opdrachten gemaakt voor de `Increment` functie in de cmdlet Sample.ps1. Het script stopt direct voor elke aanroep van de opgegeven functie.

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

Het resultaat is een opdracht onderbrekings object. Voordat het script wordt uitgevoerd, is de waarde van de eigenschap **HitCount** 0.

### Voor beeld 3: een onderbrekings punt instellen voor een variabele

In dit voor beeld wordt een onderbrekings punt ingesteld voor de **Server** variabele in het Sample.ps1 script. De **modus** para meter met de waarde **readwrite** wordt gebruikt om de uitvoering te stoppen wanneer de waarde van de variabele wordt gelezen en net voordat de waarde wordt gewijzigd.

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### Voor beeld 4: een onderbrekings punt instellen voor elke opdracht die begint met opgegeven tekst

In dit voor beeld wordt een onderbrekings punt ingesteld voor elke opdracht in het Sample.ps1 script dat begint met schrijven, zoals `Write-Host` .

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### Voor beeld 5: een onderbrekings punt instellen, afhankelijk van de waarde van een variabele

In dit voor beeld wordt de uitvoering van de `DiskTest` functie in het Test.ps1 script alleen gestopt als de waarde van de `$Disk` variabele groter is dan 2.

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

De waarde van de **actie** is een script blok waarmee de waarde van de `$Disk` variabele in de functie wordt getest.

De actie gebruikt het `break` tref woord om de uitvoering te stoppen als aan de voor waarde is voldaan. Het alternatief (en de standaard instelling) wordt **voortgezet**.

### Voor beeld 6: een onderbrekings punt instellen voor een functie

In dit voor beeld wordt een onderbrekings punt voor de `CheckLog` functie ingesteld. Omdat met de opdracht geen script wordt opgegeven, wordt het onderbrekings punt ingesteld op alles dat wordt uitgevoerd in de huidige sessie. Het fout opsporingsprogramma breekt wanneer de functie wordt aangeroepen, niet wanneer deze wordt gedeclareerd.

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### Voor beeld 7: onderbrekings punten op meerdere regels instellen

In dit voor beeld worden drie regel onderbrekingen in het Sample.ps1 script ingesteld. Er wordt één onderbrekings punt op kolom 2 ingesteld op elk van de regels die zijn opgegeven in het script. De actie die is opgegeven in de **actie** parameter is van toepassing op alle onderbrekings punten.

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## PARAMETERS

### -Actie

Geeft opdrachten die worden uitgevoerd op elke onderbrekings punt in plaats van te breken. Voer een script blok in dat de opdrachten bevat. U kunt deze para meter gebruiken om voorwaardelijke onderbrekings punten in te stellen of om andere taken uit te voeren, zoals testen of logboek registratie.

Als deze para meter wordt wegge laten of er geen actie is opgegeven, wordt de uitvoering gestopt bij het onderbrekings punt en wordt het fout opsporingsprogramma gestart.

Wanneer de **actie** parameter wordt gebruikt, wordt het actie script blok uitgevoerd op elke onderbrekings punt. De uitvoering stopt alleen als het sleutel woord Outstore is opgenomen in het script blok. Als u het sleutel woord door gaan in het script blok gebruikt, wordt de uitvoering hervat tot het volgende onderbrekings punt.

Zie [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)en [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md)voor meer informatie.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Kolom

Hiermee geeft u het kolom nummer van de kolom in het script bestand op waarop de uitvoering wordt gestopt. Voer slechts één kolom nummer in. De standaard waarde is kolom 1.

De waarde van de kolom wordt gebruikt in combi natie met de waarde van de **regel** parameter om het onderbrekings punt op te geven. Als met de **regel** parameter meerdere regels worden opgegeven, stelt de **kolom** parameter een onderbrekings punt in op de opgegeven kolom op elk van de opgegeven regels. Power shell stopt met het uitvoeren van de instructie of expressie die het teken op de opgegeven regel en kolom positie bevat.

Kolommen worden geteld vanaf de bovenste linkermarge, beginnend met kolom nummer 1 (niet 0). Als u een kolom opgeeft die niet voor komt in het script, wordt een fout niet gedeclareerd, maar wordt het onderbrekings punt nooit uitgevoerd.

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### -Opdracht

Hiermee stelt u een opdracht onderbrekings punt in. Voer de namen van de cmdlets, zoals `Get-Process` , of functie namen in. Joker tekens zijn toegestaan.

De uitvoering stopt net voordat elk exemplaar van elke opdracht wordt uitgevoerd. Als de opdracht een functie is, stopt de uitvoering telkens wanneer de functie wordt aangeroepen en aan elk van de BEGIN-, proces-en END-secties.

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Regel

Hiermee stelt u een onderbrekings punt in een script. Voer een of meer regel nummers in, gescheiden door komma's. Power shell stopt onmiddellijk voor het uitvoeren van de instructie die begint op elk van de opgegeven regels.

De regels worden geteld vanaf de linkermarge van het script bestand, beginnend met regel nummer 1 (niet 0).
Als u een lege regel opgeeft, wordt de uitvoering gestopt voor de volgende niet-lege regel. Als de regel zich buiten het bereik bevindt, wordt het onderbrekings punt nooit bereikt.

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Modus

Hiermee geeft u de toegangs modus voor het activeren van variabele onderbrekings punten. De standaard waarde is **schrijven**.

Deze para meter is alleen geldig wanneer de **variabele** para meter in de opdracht wordt gebruikt. De modus is van toepassing op alle onderbrekings punten die in de opdracht zijn ingesteld. De aanvaardbare waarden voor deze parameter zijn:

- De uitvoering van **Write** -stop stopt direct voordat een nieuwe waarde naar de variabele wordt geschreven.
- **Lezen** -stopt de uitvoering wanneer de variabele wordt gelezen, dat wil zeggen, wanneer de waarde ervan wordt geopend, wordt toegewezen, weer gegeven of gebruikt. In Lees modus stopt de uitvoering niet wanneer de waarde van de variabele wordt gewijzigd.
- **Readwrite** -stopt de uitvoering wanneer de variabele wordt gelezen of geschreven.

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script

Hiermee wordt een reeks script bestanden opgegeven die met deze cmdlet een onderbrekings punt in worden ingesteld. Voer de paden en bestands namen in van een of meer script bestanden. Als de bestanden zich in de huidige map bevinden, kunt u het pad weglaten.
Joker tekens zijn toegestaan.

Standaard worden onderbrekings punten en opdracht onderbrekings punten ingesteld voor elke opdracht die in de huidige sessie wordt uitgevoerd. Deze para meter is alleen vereist bij het instellen van een onderbrekings punt van een regel.

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variabele

Hiermee geeft u een matrix van variabelen op waarvoor met deze cmdlet onderbrekings punten worden ingesteld. Voer een door komma's gescheiden lijst met variabelen in zonder dollar tekens ( `$` ).

Gebruik de **modus** para meter om de toegangs modus te bepalen die de onderbrekings punten activeert. De standaard modus, schrijven en stopt de uitvoering, net voordat een nieuwe waarde naar de variabele wordt geschreven.

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen
U kunt geen pipe invoer naar `Set-PSBreakpoint` .

## UITVOER

### Break Point object (System. Management. Automation. LineBreakpoint, System. Management. Automation. VariableBreakpoint, System. Management. Automation. CommandBreakpoint)

`Set-PSBreakpoint` retourneert een object dat staat voor elk onderbrekings punt dat wordt ingesteld.

## OPMERKINGEN

- `Set-PSBreakpoint` kan geen onderbrekings punt instellen op een externe computer. Als u fouten wilt opsporen in een script op een externe computer, kopieert u het script naar de lokale computer en voert u de fout opsporing lokaal uit.
- Wanneer u een onderbrekings punt instelt op meer dan één regel, opdracht of variabele, `Set-PSBreakpoint` genereert een onderbrekings punt object voor elk item.
- Bij het instellen van een onderbrekings punt voor een functie of variabele bij de opdracht prompt, kunt u het onderbrekings punt instellen vóór of na het maken van de functie of variabele.

## GERELATEERDE KOPPELINGEN

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Enable-PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)
