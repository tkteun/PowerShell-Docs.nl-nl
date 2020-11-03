---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Expression
ms.openlocfilehash: d8f7df3a4c7197b6cf62eecc0b0b314d9668de90
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249390"
---
# Invoke-Expression

## SAMENVATTING
Voert opdrachten of expressies uit op de lokale computer.

## SYNTAXIS

```
Invoke-Expression [-Command] <String> [<CommonParameters>]
```

## BESCHRIJVING

De `Invoke-Expression` cmdlet evalueert of voert een opgegeven teken reeks als een opdracht en retourneert de resultaten van de expressie of opdracht. Zonder `Invoke-Expression` , wordt een teken reeks die is verzonden op de opdracht regel, ongewijzigd geretourneerd (geechod).

Expressies worden geëvalueerd en uitgevoerd in de huidige scope. Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.

> [!CAUTION]
> Zorg voor redelijke voorzorgsmaatregelen bij het gebruik `Invoke-Expression` van de cmdlet in scripts. Wanneer u gebruikt `Invoke-Expression` om een opdracht uit te voeren die door de gebruiker wordt ingevoerd, controleert u of de opdracht veilig is om uit te voeren voordat deze wordt uitgevoerd. Over het algemeen kunt u het script het beste ontwerpen met vooraf gedefinieerde invoer opties, in plaats van vrije-vorm invoer toe te staan.

## VOORBEELDEN

### Voor beeld 1: een expressie evalueren

```powershell
$Command = "Get-Process"
$Command
```

```Output
Get-Process
```

```powershell
Invoke-Expression $Command
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
296       4       1572       1956    20       0.53     1348   AdtAgent
270       6       1328       800     34       0.06     2396   alg
67        2       620        484     20       0.22     716    ati2evxx
1060      15      12904      11840   74       11.48    892    CcmExec
1400      33      25280      37544   223      38.44    2564   communicator
...
```

In dit voor beeld ziet u hoe `Invoke-Expression` u een expressie kunt evalueren. Zonder `Invoke-Expression` , de expressie wordt afgedrukt, maar niet geëvalueerd.

Met de eerste opdracht wordt een waarde van `Get-Process` (een teken reeks) toegewezen aan de `$Command` variabele.

Met de tweede opdracht wordt het effect van het typen van de naam van de variabele op de opdracht regel weer gegeven. Power shell Echos de teken reeks.

De derde opdracht wordt gebruikt `Invoke-Expression` om de teken reeks te evalueren.

### Voor beeld 2: een script uitvoeren op de lokale computer

```powershell
Invoke-Expression -Command "C:\ps-test\testscript.ps1"
"C:\ps-test\testscript.ps1" | Invoke-Expression
```

Deze opdrachten gebruiken `Invoke-Expression` om een script, TestScript.ps1, uit te voeren op de lokale computer. De twee opdrachten zijn gelijk. De eerste gebruikt de **opdracht** parameter om op te geven welke opdracht moet worden uitgevoerd.
De tweede gebruikt een pijplijn operator ( `|` ) om de opdracht teken reeks naar te verzenden `Invoke-Expression` .

### Voor beeld 3: een opdracht uitvoeren in een variabele

```powershell
$Command = 'Get-Process | where {$_.cpu -gt 1000}'
Invoke-Expression $Command
```

In dit voor beeld wordt een opdracht reeks uitgevoerd die is opgeslagen in de `$Command` variabele.

De opdracht teken reeks staat tussen enkele aanhalings tekens, omdat deze een variabele bevat, `$_` waarmee het huidige object wordt aangeduid. Als deze tussen dubbele aanhalings tekens is geplaatst, wordt de `$_` variabele vervangen door de waarde voordat deze is opgeslagen in de `$Command` variabele.

### Voor beeld 4: een Help-voor beeld van cmdlet ophalen en uitvoeren

```powershell
$Cmdlet_name = "Get-EventLog"
$Example_number = 1
$Example_code = (Get-Help $Cmdlet_name).examples.example[($Example_number-1)].code
Invoke-Expression $Example_code
```

Met deze opdracht wordt het eerste voor beeld in het Help-onderwerp van de cmdlet opgehaald en uitgevoerd `Get-EventLog` .

Als u een voor beeld van een andere cmdlet wilt uitvoeren, wijzigt u de waarde van de `$Cmdlet_name` variabele in de naam van de cmdlet. En wijzig de `$Example_number` variabele in het voorbeeld nummer dat u wilt uitvoeren. De opdracht mislukt als het voorbeeld nummer ongeldig is.

## PARAMETERS

### -Opdracht

Hiermee geeft u de opdracht of expressie op die moet worden uitgevoerd. Typ de opdracht of expressie of voer een variabele in die de opdracht of expressie bevat. De **opdracht** parameter is vereist.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String of PSObject

U kunt een object dat de opdracht vertegenwoordigt door sluizen naar `Invoke-Expression` .
Gebruik de `$Input` Automatische variabele om de invoer objecten in de opdracht weer te geven.

## UITVOER

### PSObject

Retourneert de uitvoer die wordt gegenereerd door de aangeroepen opdracht (de waarde van de **opdracht** parameter).

## OPMERKINGEN

In de meeste gevallen roept u expressies aan met behulp van de aanroep operator van Power shell en haalt u dezelfde resultaten op.
De aanroep operator is een veiliger methode. Zie [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Invoke-opdracht](../Microsoft.PowerShell.Core/Invoke-Command.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)
