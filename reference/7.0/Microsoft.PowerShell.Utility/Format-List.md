---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/19/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-list?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-List
ms.openlocfilehash: df013bd6efd127a022d6bd41c5ea5fcca90dbc4a
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251767"
---
# Format-List

## SAMENVATTING
Hiermee wordt de uitvoer opgemaakt als een lijst met eigenschappen waarin elke eigenschap op een nieuwe regel wordt weer gegeven.

## SYNTAXIS

```
Format-List [[-Property] <Object[]>] [-GroupBy <Object>] [-View <string>] [-ShowError]
[-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>] [<CommonParameters>]
```

## BESCHRIJVING

De `Format-List` cmdlet formatteert de uitvoer van een opdracht als een lijst met eigenschappen waarin elke eigenschap op een afzonderlijke regel wordt weer gegeven. U kunt gebruiken `Format-List` om alle of geselecteerde eigenschappen van een object op te maken en weer te geven als een lijst (opmaak lijst *).

Omdat er meer ruimte beschikbaar is voor elk item in een lijst dan in een tabel, worden in Power Shell meer eigenschappen van het object in de lijst weer gegeven en worden de eigenschapwaarden minder waarschijnlijk afgekapt.

## VOORBEELDEN

### Voor beeld 1: computer services Format teren

```powershell
Get-Service | Format-List
```

Met deze opdracht wordt informatie over services op de computer als een lijst opgemaakt. Standaard worden de services opgemaakt als een tabel. De `Get-Service` cmdlet haalt objecten op die de services op de computer vertegenwoordigen. De pijplijn operator (|) geeft de resultaten door de pijp lijn door aan `Format-List` .
De `Format-List` opdracht formatteert vervolgens de service gegevens in een lijst en verzendt deze naar de standaard uitvoer-cmdlet om weer te geven.

### Voor beeld 2: PS1XML-bestanden Format teren

Met deze opdrachten wordt informatie weer gegeven over de PS1XML-bestanden in de Power shell-map als een lijst.

```powershell
$A = Get-ChildItem $pshome\*.ps1xml
Format-List -InputObject $A
```

Met de eerste opdracht worden de objecten opgehaald die de bestanden vertegenwoordigen en opgeslagen in de `$A` variabele.

De tweede opdracht wordt gebruikt `Format-List` voor het opmaken van informatie over objecten die zijn opgeslagen in `$A` . Met deze opdracht wordt de para meter **input object** gebruikt om de variabele door te geven aan `Format-List` , waarna de opgemaakte uitvoer wordt verzonden naar de standaard uitvoer-cmdlet voor weer gave.

### Voor beeld 3: proces eigenschappen opmaken op naam

Met deze opdracht worden de naam, de basis prioriteit en de prioriteits klasse van elk proces op de computer weer gegeven.

```powershell
Get-Process | Format-List -Property name, basepriority, priorityclass
```

De cmdlet wordt gebruikt `Get-Process` om een object op te halen dat elk proces vertegenwoordigt. De pijplijn operator (|) geeft de proces objecten door aan de pijp lijn `Format-List` . `Format-List` Hiermee worden de processen opgemaakt als een lijst met de opgegeven eigenschappen. De naam van de *eigenschaps* parameter is optioneel. u kunt deze weglaten.

### Voor beeld 4: alle eigenschappen voor een proces opmaken

Met deze opdracht worden alle eigenschappen van het Winlogon-proces weer gegeven.

```powershell
Get-Process winlogon | Format-List -Property *
```

De Get-Process cmdlet wordt gebruikt om een object op te halen dat het Winlogon-proces vertegenwoordigt. De pijplijn operator (|) geeft het Winlogon-proces object door de pijp lijn door `Format-List` . De opdracht gebruikt de para meter *Property* om de eigenschappen op te geven en de \* om alle eigenschappen aan te geven.
Omdat de naam van de *eigenschaps* parameter optioneel is, kunt u deze weglaten en de opdracht typen als `Format-List *` . `Format-List` de resultaten worden automatisch naar de standaard uitvoer-cmdlet verzonden voor weer gave.

### Voor beeld 5: problemen met indelings fouten oplossen

In de volgende voor beelden ziet u de resultaten van het toevoegen van de para meters **Display error** of **show error** met een expressie.

```powershell
PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -DisplayError

DayOfWeek    : Friday
 $_ / $null  : #ERR

PC /> Get-Date | Format-List DayOfWeek,{ $_ / $null } -ShowError

DayOfWeek    : Friday
 $_ / $null  :

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 7:59:23 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -Display error

Geeft aan dat met deze cmdlet fouten worden weer gegeven op de opdracht regel. Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-List` opdracht en de expressies worden niet weer gegeven.

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

### -Uitbreiden

Hiermee geeft u het opgemaakte verzamelings object op, evenals de objecten in de verzameling. Deze para meter is ontworpen om objecten op te maken die ondersteuning bieden voor de ICollection-interface (System. Collections). De standaard waarde is EnumOnly. De aanvaardbare waarden voor deze parameter zijn:

- EnumOnly. Hiermee worden de eigenschappen van de objecten in de verzameling weer gegeven.
- CoreOnly. Hiermee worden de eigenschappen van het verzamelings object weer gegeven.
- Zowel. Hiermee worden de eigenschappen van het verzamelings object en de eigenschappen van objecten in de verzameling weer gegeven.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Geeft aan dat met deze cmdlet alle fout gegevens worden weer gegeven. Gebruik met de para meter **Display error** of **show error** . Wanneer een fout object naar de fout wordt geschreven of stromen weer geven, wordt standaard slechts een deel van de fout informatie weer gegeven.

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

### -GroupBy

Hiermee geeft u de uitvoer op in groepen op basis van een gedeelde eigenschap of waarde. Voer een expressie of een eigenschap van de uitvoer in.

De waarde van de para meter **GroupBy** kan een nieuwe berekende eigenschap zijn. De berekende eigenschap kan een script blok of een hash-tabel zijn. Geldige sleutel-waardeparen zijn:

- Naam (of label)- `<string>`
- Expressie- `<string>` of `<script block>`
- Tring `<string>`

Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Geeft aan welke objecten moeten worden opgemaakt. Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.

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

### -Eigenschap

Hiermee geeft u de object eigenschappen op die in de weer gave worden weer gegeven en de volg orde waarin ze worden weer gegeven.
Joker tekens zijn toegestaan.

Als u deze para meter weglaat, zijn de eigenschappen die worden weer gegeven in de weer gave afhankelijk van het object dat wordt weer gegeven. De parameter naam ' Property ' is optioneel. U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.

De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn. De berekende eigenschap kan een script blok of een hash-tabel zijn. Geldige sleutel-waardeparen zijn:

- Naam (of label)- `<string>`
- Expressie- `<string>` of `<script block>`
- Tring `<string>`

Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Show error

Geeft aan dat de cmdlet fouten verzendt via de pijp lijn. Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-List` opdracht en de expressies worden niet weer gegeven.

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

### -Weer geven

Geeft de naam van een alternatieve lijst indeling of weer gave aan. U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.

```yaml
Type: System.String
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

U kunt elk object door sluizen naar `Format-List` .

## UITVOER

### Micro soft. Power shell. commands. internal. Format

`Format-List` retourneert de indelings objecten die de lijst vertegenwoordigen.

## OPMERKINGEN

U kunt ook verwijzen naar Format-List door de ingebouwde alias, FL. Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.

De indelings-cmdlets, zoals `Format-List` , ordenen van de gegevens die worden weer gegeven, maar niet weer geven.
De gegevens worden weer gegeven in de uitvoer functies van Power shell en door de cmdlets die de out-verb (de out-cmdlets) bevatten, zoals `Out-Host` of `Out-File` .

Als u geen indelings-cmdlet gebruikt, past Power shell deze standaard indeling toe voor elk object dat wordt weer gegeven.

De para meter **GroupBy** gaat ervan uit dat de objecten zijn gesorteerd. Gebruik Sort-Object voordat `Format-List` u de objecten groepeert.

Met de para meter **weer geven** kunt u een alternatieve notatie voor de tabel opgeven. U kunt de weer gaven gebruiken die zijn gedefinieerd in de `*.format.PS1XML` bestanden in de Power shell-map, maar u kunt ook uw eigen weer gaven maken in nieuwe PS1XML-bestanden en de cmdlet Update-FormatData gebruiken om deze op te geven in Power shell.

De alternatieve weer gave voor de **weer gave** -para meter moet de lijst indeling gebruiken, anders mislukt de opdracht. Als de weer gave alternatieve een tabel is, gebruikt u `Format-Table` . Als de alternatieve weer gave geen lijst of tabel is, gebruikt u `Format-Custom` .

## GERELATEERDE KOPPELINGEN

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)
