---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: 667a503d67ac9a9a0f41187cbac079d946247618
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705490"
---
# Where-Object

## SAMENVATTING
Selecteert objecten uit een verzameling op basis van de bijbehorende eigenschaps waarden.

## SYNTAXIS

### Gelijkset (standaard)

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ]
 [<CommonParameters>]
```

### ScriptBlockSet

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### Overeenkomstset

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Match
 [<CommonParameters>]
```

### CaseSensitiveEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CEQ
 [<CommonParameters>]
```

### NotEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NE
 [<CommonParameters>]
```

### CaseSensitiveNotEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNE
 [<CommonParameters>]
```

### GreaterThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GT
 [<CommonParameters>]
```

### CaseSensitiveGreaterThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGT
 [<CommonParameters>]
```

### LessThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LT
 [<CommonParameters>]
```

### CaseSensitiveLessThanSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLT
 [<CommonParameters>]
```

### GreaterOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GE
 [<CommonParameters>]
```

### CaseSensitiveGreaterOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGE
 [<CommonParameters>]
```

### LessOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LE
 [<CommonParameters>]
```

### CaseSensitiveLessOrEqualSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLE
 [<CommonParameters>]
```

### Like-set

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Like
 [<CommonParameters>]
```

### CaseSensitiveLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLike
 [<CommonParameters>]
```

### NotLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotLike
 [<CommonParameters>]
```

### CaseSensitiveNotLikeSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotLike
 [<CommonParameters>]
```

### CaseSensitiveMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CMatch
 [<CommonParameters>]
```

### NotMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotMatch
 [<CommonParameters>]
```

### CaseSensitiveNotMatchSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotMatch
 [<CommonParameters>]
```

### Contains bevat

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Contains
 [<CommonParameters>]
```

### CaseSensitiveContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CContains
 [<CommonParameters>]
```

### NotContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotContains
 [<CommonParameters>]
```

### CaseSensitiveNotContainsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotContains
 [<CommonParameters>]
```

### Pentekenen

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -In
 [<CommonParameters>]
```

### CaseSensitiveInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CIn
 [<CommonParameters>]
```

### NotInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotIn
 [<CommonParameters>]
```

### CaseSensitiveNotInSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotIn
 [<CommonParameters>]
```

### IsSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Is
 [<CommonParameters>]
```

### IsNotSet

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -IsNot
 [<CommonParameters>]
```

### Not

```
Where-Object [-InputObject <PSObject>] [-Property] <String> -Not [<CommonParameters>]
```

## BESCHRIJVING

De `Where-Object` cmdlet selecteert objecten met bepaalde eigenschaps waarden uit de verzameling van objecten die worden door gegeven. U kunt bijvoorbeeld de `Where-Object` -cmdlet gebruiken om bestanden te selecteren die zijn gemaakt na een bepaalde datum, gebeurtenissen met een bepaalde id of computers die gebruikmaken van een bepaalde versie van Windows.

Vanaf Windows Power Shell 3,0 zijn er twee verschillende manieren om een opdracht te maken `Where-Object` .

- **Script blok**. U kunt een script blok gebruiken om de naam van de eigenschap, een vergelijkings operator en een eigenschaps waarde op te geven. `Where-Object` retourneert alle objecten waarvoor de instructie script blok is ingesteld op True.

  Met de volgende opdracht worden bijvoorbeeld processen in de klasse met normale prioriteit opgehaald, dat wil zeggen, processen waarbij de waarde van de eigenschap **PriorityClass** gelijk is aan normaal.

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  Alle Power shell-vergelijkings operatoren zijn geldig in de script blok indeling. Zie [about_Comparison_Operators](./About/about_Comparison_Operators.md)voor meer informatie over vergelijkings operatoren.

- **Vergelijkings instructie**. U kunt ook een vergelijkings instructie schrijven die veel meer lijkt op natuurlijke taal. Vergelijkings instructies zijn geïntroduceerd in Windows Power Shell 3,0.

  Met de volgende opdrachten worden ook processen opgehaald die de prioriteits klasse normaal hebben. Deze opdrachten zijn gelijkwaardig en kunnen door elkaar worden gebruikt.

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  Vanuit Windows Power Shell 3,0 worden `Where-Object` vergelijkings operatoren als para meters toegevoegd aan een `Where-Object` opdracht. Tenzij opgegeven, zijn alle Opera tors niet hoofdletter gevoelig. Vóór Windows Power Shell 3,0 kan de vergelijkings operators in de Power shell-taal alleen worden gebruikt in script blokken.

Wanneer u één **eigenschap** opgeeft `Where-Object` , wordt de waarde van de eigenschap behandeld als een booleaanse expressie. Als de waarde van **Length** niet gelijk is aan nul, wordt de expressie geëvalueerd als **waar**. Bijvoorbeeld: `('hi', '', 'there') | Where-Object Length`

Het vorige voor beeld is functioneel equivalent aan:

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## VOORBEELDEN

### Voor beeld 1: gestopt services ophalen

Met deze opdrachten wordt een lijst weer geven met alle services die momenteel zijn gestopt. De `$_` Automatische variabele vertegenwoordigt elk object dat wordt door gegeven aan de `Where-Object` cmdlet.

De eerste opdracht maakt gebruik van de script blok indeling. de tweede opdracht maakt gebruik van de indeling van de vergelijkings instructie. De opdrachten zijn gelijkwaardig en kunnen door elkaar worden gebruikt.

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### Voor beeld 2: processen ophalen op basis van werkset

Met deze opdrachten worden processen weer geven die een werkset hebben die groter is dan 250 mega bytes (KB). De syntaxis van de script Block en-instructie zijn gelijk en kunnen door elkaar worden gebruikt.

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### Voor beeld 3: processen ophalen op basis van proces naam

Met deze opdrachten worden de processen opgehaald die de waarde van de eigenschap **proces** naam hebben die begint met de letter `p` . Met de operator **match** kunt u reguliere expressie overeenkomsten gebruiken.

De syntaxis van de script Block en-instructie zijn gelijk en kunnen door elkaar worden gebruikt.

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### Voor beeld 4: de indeling van de vergelijkings instructie gebruiken

In dit voor beeld ziet u hoe u de nieuwe indeling van de vergelijkings instructie van de `Where-Object` cmdlet gebruikt.

De eerste opdracht maakt gebruik van de indeling van de vergelijkings instructie.
In deze opdracht worden geen aliassen gebruikt en alle para meters bevatten de parameter naam.

De tweede opdracht is het natuurlijke gebruik van de opdracht notatie voor vergelijking. De `where` alias wordt vervangen door de naam van de `Where-Object` cmdlet en alle optionele parameter namen worden wegge laten.

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### Voor beeld 5: opdrachten ophalen op basis van eigenschappen

In dit voor beeld ziet u hoe u opdrachten schrijft die items retour neren die waar of onwaar zijn of een wille keurige waarde hebben voor een opgegeven eigenschap. Elk voor beeld toont zowel het script blok als de indeling van de vergelijkings instructie voor de opdracht.

```powershell
# Use Where-Object to get commands that have any value for the OutputType property of the command.
# This omits commands that do not have an OutputType property and those that have an OutputType property, but no property value.
Get-Command | where OutputType
Get-Command | where {$_.OutputType}
```

```powershell
# Use Where-Object to get objects that are containers.
# This gets objects that have the **PSIsContainer** property with a value of $True and excludes all others.
Get-ChildItem | where PSIsContainer
Get-ChildItem | where {$_.PSIsContainer}
```

```powershell
# Finally, use the Not operator (!) to get objects that are not containers.
# This gets objects that do have the **PSIsContainer** property and those that have a value of $False for the **PSIsContainer** property.
Get-ChildItem | where {!$_.PSIsContainer}
# You cannot use the Not operator (!) in the comparison statement format of the command.
Get-ChildItem | where PSIsContainer -eq $False
```

### Voor beeld 6: meerdere voor waarden gebruiken

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

In dit voor beeld ziet u hoe u een `Where-Object` opdracht met meerdere voor waarden maakt.

Met deze opdracht worden niet-kern modules opgehaald die ondersteuning bieden voor de Help-functie die kan worden bijgewerkt. De opdracht gebruikt de para meter **ListAvailable** van de `Get-Module` cmdlet om alle modules op de computer op te halen. Een pijplijn operator ( `|` ) verzendt de modules naar de `Where-Object` cmdlet, die modules ophaalt waarvan de namen niet beginnen met micro soft of PS, en een waarde hebben voor de eigenschap **HelpInfoURI** , die Power shell vertelt waar bijgewerkte Help-bestanden voor de module moeten worden gevonden. De vergelijkings instructies zijn verbonden door de operator **and** .

In het voor beeld wordt de script blok opdracht indeling gebruikt. Logische Opera Tors, zoals **en** en **of**, zijn alleen geldig in script blokken. U kunt ze niet gebruiken in de indeling van de vergelijkings instructie van een `Where-Object` opdracht.

- Zie [about_Logical_Operators](./About/about_logical_operators.md)voor meer informatie over logische Power shell-Opera tors.
- Zie [about_Updatable_Help](./About/about_Updatable_Help.md)voor meer informatie over de Help-functie die kan worden bijgewerkt.

## PARAMETERS

### -CContains

Geeft aan dat deze cmdlet objecten van een collectie ophaalt als de eigenschaps waarde van het object een exacte overeenkomst voor de opgegeven waarde is. Deze bewerking is hoofdletter gevoelig.

Bijvoorbeeld: `Get-Process | where ProcessName -CContains "svchost"`

**CContains** verwijst naar een verzameling waarden en is waar als de verzameling een item bevat dat exact overeenkomt met de opgegeven waarde. Als de invoer één object is, wordt dit door Power shell geconverteerd naar een verzameling van één object.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CEQ

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap gelijk is aan de opgegeven waarde.
Deze bewerking is hoofdletter gevoelig.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CGE

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan of gelijk is aan de opgegeven waarde. Deze bewerking is hoofdletter gevoelig.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CGT

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan de opgegeven waarde.
Deze bewerking is hoofdletter gevoelig.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CIn

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap de opgegeven waarde bevat. Deze bewerking is hoofdletter gevoelig.

Bijvoorbeeld: `Get-Process | where -Value "svchost" -CIn ProcessName`

**Cin** lijkt op **CContains**, behalve dat de positie van de eigenschap en de waarde worden omgekeerd. De volgende instructies zijn bijvoorbeeld beide waar.

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLE

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan of gelijk is aan de opgegeven waarde. Deze bewerking is hoofdletter gevoelig.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLike

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap overeenkomt met een waarde die joker tekens bevat. Deze bewerking is hoofdletter gevoelig.

Bijvoorbeeld: `Get-Process | where ProcessName -CLike "*host"`

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CLT

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan de opgegeven waarde. Deze bewerking is hoofdletter gevoelig.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CMatch

Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde overeenkomt met de opgegeven reguliere expressie. Deze bewerking is hoofdletter gevoelig. Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.

Bijvoorbeeld: `Get-Process | where ProcessName -CMatch "Shell"`

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNE

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap anders is dan de opgegeven waarde.
Deze bewerking is hoofdletter gevoelig.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotContains

Hiermee wordt aangegeven dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde van het object niet exact overeenkomt met de opgegeven waarde. Deze bewerking is hoofdletter gevoelig.

Bijvoorbeeld: `Get-Process | where ProcessName -CNotContains "svchost"`

**NotContains** en **CNotContains** verwijzen naar een verzameling waarden en zijn waar wanneer de verzameling geen items bevat die exact overeenkomen voor de opgegeven waarde. Als de invoer één object is, wordt dit door Power shell geconverteerd naar een verzameling van één object.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotIn

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap niet exact overeenkomt met de opgegeven waarde. Deze bewerking is hoofdletter gevoelig.

Bijvoorbeeld: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`

**NotIn** -en **CNotIn** -Opera tors lijken op **NotContains** en **CNotContains**, behalve dat de positie van de eigenschap en de waarde worden omgekeerd. De volgende instructies zijn bijvoorbeeld waar.

`"abc", "def" -CNotContains "Abc"`

`"abc" -CNotIn "Abc", "def"`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotLike

Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde niet overeenkomt met een waarde die joker tekens bevat. Deze bewerking is hoofdletter gevoelig.

Bijvoorbeeld: `Get-Process | where ProcessName -CNotLike "*host"`

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CNotMatch

Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde niet overeenkomt met de opgegeven reguliere expressie. Deze bewerking is hoofdletter gevoelig. Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.

Bijvoorbeeld: `Get-Process | where ProcessName -CNotMatch "Shell"`

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bevat

Geeft aan dat met deze cmdlet objecten worden opgehaald als een item in de waarde van de eigenschap van het object een exacte overeenkomst voor de opgegeven waarde is.

Bijvoorbeeld: `Get-Process | where ProcessName -Contains "Svchost"`

Als de waarde van de eigenschap één object bevat, wordt deze door Power shell geconverteerd naar een verzameling van één object.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainsSet
Aliases: IContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EQ

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap gelijk is aan de opgegeven waarde.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: EqualSet
Aliases: IEQ

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterScript

Hiermee geeft u het script blok op dat wordt gebruikt voor het filteren van de objecten. Plaats het script blok tussen accolades ( `{}` ).

De parameter naam **FilterScript** is optioneel.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GE

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan of gelijk is aan de opgegeven waarde.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterOrEqualSet
Aliases: IGE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GT

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan de opgegeven waarde.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterThanSet
Aliases: IGT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -In

Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde overeenkomt met een van de opgegeven waarden.
Bijvoorbeeld:

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

Als de waarde van de para meter **Value** één object is, converteert Power shell deze naar een verzameling van één object.

Als de eigenschaps waarde van een object een matrix is, gebruikt Power shell referentie gelijkheid om een overeenkomst te bepalen. `Where-Object` retourneert het object alleen als de waarde van de **eigenschaps** parameter en een waarde van **waarde** hetzelfde exemplaar van een object zijn.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InSet
Aliases: IIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Geeft aan welke objecten moeten worden gefilterd. U kunt de objecten ook door sluizen naar `Where-Object` .

Wanneer u de para meter **input object** gebruikt in `Where-Object` plaats van de resultaten van de pijpleiding opdracht, `Where-Object` wordt de waarde van **input object** behandeld als een enkel object. Dit geldt ook als de waarde een verzameling is die het resultaat is van een opdracht, zoals `-InputObject (Get-Process)` . Omdat **input object** geen afzonderlijke eigenschappen van een matrix of verzameling van objecten kan retour neren, raden we u aan dat, als u gebruikt `Where-Object` om een verzameling objecten te filteren voor objecten die specifieke waarden in gedefinieerde eigenschappen hebben, u `Where-Object` in de pijp lijn gebruikt, zoals wordt weer gegeven in de voor beelden in dit onderwerp.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Is

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap een exemplaar van het opgegeven .NET-type is. Plaats de type naam tussen vier Kante haken.

Bijvoorbeeld: `Get-Process | where StartTime -Is [DateTime]`

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IsNot

Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde geen exemplaar van het opgegeven .NET-type is.

Bijvoorbeeld: `Get-Process | where StartTime -IsNot [DateTime]`

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsNotSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LE

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan of gelijk is aan de opgegeven waarde.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessOrEqualSet
Aliases: ILE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Like

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap overeenkomt met een waarde die joker tekens bevat.

Bijvoorbeeld: `Get-Process | where ProcessName -Like "*host"`

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LikeSet
Aliases: ILike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LT

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan de opgegeven waarde.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessThanSet
Aliases: ILT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Overeenkomst

Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde overeenkomt met de opgegeven reguliere expressie. Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.

Bijvoorbeeld: `Get-Process | where ProcessName -Match "shell"`

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MatchSet
Aliases: IMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NE

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap anders is dan de opgegeven waarde.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotEqualSet
Aliases: INE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Niet

Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschap niet bestaat of de waarde null of False heeft.

Bijvoorbeeld: `Get-Service | where -Not "DependentServices"`

Deze para meter is geïntroduceerd in Windows Power shell 6,1.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Not
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotContains

Hiermee wordt aangegeven dat met deze cmdlet objecten worden opgehaald als geen van de items in de waarde van de eigenschap een exacte overeenkomst voor de opgegeven waarde is.

Bijvoorbeeld: `Get-Process | where ProcessName -NotContains "Svchost"`

**NotContains** verwijst naar een verzameling waarden en is waar als de verzameling geen items bevat die exact overeenkomen voor de opgegeven waarde. Als de invoer één object is, wordt dit door Power shell geconverteerd naar een verzameling van één object.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotContainsSet
Aliases: INotContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotIn

Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap niet exact overeenkomt met een van de opgegeven waarden.

Bijvoorbeeld: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`

Als de waarde van de **waarde** één object is, converteert Power shell deze naar een verzameling van één object.

Als de eigenschaps waarde van een object een matrix is, gebruikt Power shell referentie gelijkheid om een overeenkomst te bepalen. `Where-Object` retourneert het object alleen als de waarde van de **eigenschap** en een waarde van de **waarde** niet hetzelfde exemplaar van een object zijn.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotInSet
Aliases: INotIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotLike

Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde niet overeenkomt met een waarde die joker tekens bevat.

Bijvoorbeeld: `Get-Process | where ProcessName -NotLike "*host"`

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotLikeSet
Aliases: INotLike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NotMatch

Geeft aan dat met deze cmdlet objecten worden opgehaald wanneer de eigenschaps waarde niet overeenkomt met de opgegeven reguliere expressie. Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.

Bijvoorbeeld: `Get-Process | where ProcessName -NotMatch "PowerShell"`

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotMatchSet
Aliases: INotMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Eigenschap

Hiermee geeft u de naam van een object eigenschap op. De parameter naam, **eigenschap** is optioneel.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet, Not
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Waarde

Geeft een eigenschaps waarde aan. De parameter naam, **waarde**, is optioneel. Deze para meter accepteert joker tekens wanneer ze worden gebruikt met de volgende vergelijkings parameters:

- **CLike**
- **CNotLike**
- **Zo**
- **NotLike**

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Object
Parameter Sets: EqualSet, LessOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

U kunt de objecten door sluizen naar deze cmdlet.

## UITVOER

### Object

Met deze cmdlet worden geselecteerde items uit de invoer objectset geretourneerd.

## OPMERKINGEN

Starten in Windows Power Shell 4,0 `Where` en `ForEach` methoden zijn toegevoegd voor gebruik met verzamelingen.

U kunt hier meer lezen over deze nieuwe methoden [about_arrays](./About/about_Arrays.md)

## GERELATEERDE KOPPELINGEN

[Compare-object](../Microsoft.PowerShell.Utility/Compare-Object.md)

[ForEach-object](ForEach-Object.md)

[Groep-object](../Microsoft.PowerShell.Utility/Group-Object.md)

[Meting object](../Microsoft.PowerShell.Utility/Measure-Object.md)

[New-Object](../Microsoft.PowerShell.Utility/New-Object.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Sorteer object](../Microsoft.PowerShell.Utility/Sort-Object.md)

[T-object](../Microsoft.PowerShell.Utility/Tee-Object.md)

