---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-custom?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Custom
ms.openlocfilehash: 89c7e8f1b70552e735fccd7b2fd45f951b81f928
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251762"
---
# Format-Custom

## SAMENVATTING
Maakt gebruik van een aangepaste weer gave om de uitvoer op te maken.

## SYNTAXIS

```
Format-Custom [[-Property] <Object[]>] [-Depth <Int32>] [-GroupBy <Object>] [-View <String>]
 [-ShowError] [-DisplayError] [-Force] [-Expand <String>] [-InputObject <PSObject>]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Format-Custom` cmdlet formatteert de uitvoer van een opdracht zoals gedefinieerd in een alternatieve weer gave.
`Format-Custom` is ontworpen om weer gaven weer te geven die niet alleen uit tabellen bestaan of alleen lijsten. U kunt de weer gaven gebruiken die zijn gedefinieerd in de `*format.PS1XML` bestanden in de Power shell-map, maar u kunt ook uw eigen weer gaven maken in nieuwe PS1XML-bestanden en de `Update-FormatData` cmdlet gebruiken om ze toe te voegen aan Power shell.

## VOORBEELDEN

### Voor beeld 1: uitvoer opmaken met een aangepaste weer gave

```powershell
Get-Command Start-Transcript | Format-Custom -View MyView
```

Met deze opdracht wordt informatie over de `Start-Transcript` cmdlet opgemaakt in de indeling die is gedefinieerd door de weer gave MyView, een aangepaste weer gave die door de gebruiker is gemaakt. Als u deze opdracht wilt uitvoeren, moet u eerst een nieuw PS1XML-bestand maken, de weer gave **MyView** definiëren en vervolgens de `Update-FormatData` opdracht gebruiken om het PS1XML-bestand toe te voegen aan Power shell.

### Voor beeld 2: uitvoer opmaken met de standaard weergave

```powershell
Get-Process Winlogon | Format-Custom
```

Met deze opdracht wordt informatie over het **Winlogon** -proces in een alternatieve aangepaste weer gave opgemaakt.
Omdat de opdracht de **weer gave** -para meter niet gebruikt, `Format-Custom` gebruikt een standaard aangepaste weer gave om de gegevens op te maken.

### Voor beeld 3: problemen met indelings fouten oplossen

In de volgende voor beelden ziet u de resultaten van het toevoegen van de para meters **Display error** of **show error** met een expressie.

```powershell
PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -DisplayError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  = #ERR
}


PC /> Get-Date | Format-Custom DayOfWeek,{ $_ / $null } -ShowError

class DateTime
{
  DayOfWeek = Friday
   $_ / $null  =
}

Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:01:04 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -Diepte

Hiermee wordt het aantal kolommen in de weer gave opgegeven.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Display error

Hiermee worden fouten weer gegeven op de opdracht regel. Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-Custom` opdracht en de expressies worden niet weer gegeven.

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

Hiermee wordt het verzamelings object opgemaakt, evenals de objecten in de verzameling. Deze para meter is ontworpen om objecten op te maken die ondersteuning bieden voor de interface **System. Collections. ICollection** . De standaard waarde is **EnumOnly**.

Geldige waarden zijn:

- EnumOnly: Hiermee worden de eigenschappen van de objecten in de verzameling weer gegeven.
- CoreOnly: Hiermee worden de eigenschappen van het verzamelings object weer gegeven.
- Beide: Hiermee worden de eigenschappen van het verzamelings object en de objecten in de verzameling weer gegeven.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: EnumOnly
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hiermee wordt de cmdlet doorgestuurd om alle fout gegevens weer te geven. Gebruik met de para meters **Display error** of **show error** . Wanneer een fout object naar de fout wordt geschreven of stromen weer geven, wordt standaard slechts een deel van de fout informatie weer gegeven.

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

Hiermee wordt de uitvoer in groepen opgemaakt op basis van een gedeelde eigenschap of waarde. Voer een expressie of een eigenschap van de uitvoer in.

De waarde van de para meter **GroupBy** kan een nieuwe berekende eigenschap zijn. De berekende eigenschap kan een script blok of een hash-tabel zijn. Geldige sleutel-waardeparen zijn:

- Naam (of label) `<string>`
- Expressie `<string>` of `<script block>`
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

Als u deze para meter weglaat, zijn de eigenschappen die worden weer gegeven in de weer gave afhankelijk van het object dat wordt weer gegeven. De parameter naam **eigenschap** is optioneel. U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.

De waarde van de **eigenschaps** parameter kan een nieuwe berekende eigenschap zijn. De berekende eigenschap kan een script blok of een hash-tabel zijn. Geldige sleutel-waardeparen zijn:

- Expressie- `<string>` of `<script block>`
- Diepga `<int32>`

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

Hiermee worden fouten verzonden via de pijp lijn. Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-Custom` opdracht en de expressies worden niet weer gegeven.

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

Hiermee geeft u de naam van een alternatieve notatie of weer gave. Als u deze para meter weglaat, `Format-Custom` wordt een standaard aangepaste weer gave gebruikt. U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.

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

U kunt elk object door sluizen naar `Format-Custom` .

## UITVOER

### Micro soft. Power shell. commands. internal. Format

`Format-Custom` retourneert de indelings objecten die de weer gave vertegenwoordigen.

## OPMERKINGEN

`Format-Custom` is ontworpen om weer gaven weer te geven die niet alleen uit tabellen bestaan of alleen lijsten. Als u een alternatieve tabel weergave wilt weer geven, gebruikt u `Format-Table` . Als u een alternatieve lijst weergave wilt weer geven, gebruikt u `Format-List` .

U kunt ook verwijzen naar `Format-Custom` de ingebouwde alias `fc` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.

De para meter **GroupBy** gaat ervan uit dat de objecten zijn gesorteerd. Voordat u `Format-Custom` de objecten groepeert, kunt u `Sort-Object` deze gebruiken om ze te sorteren.

## GERELATEERDE KOPPELINGEN

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)

[Format-Wide](Format-Wide.md)

[Get-Process](../Microsoft.PowerShell.Management/Get-Process.md)
