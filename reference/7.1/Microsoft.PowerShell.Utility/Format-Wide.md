---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-wide?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Wide
ms.openlocfilehash: eed3ba1982792cc5675b7343525e1182f9e6a420
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/10/2020
ms.locfileid: "93251797"
---
# Format-Wide

## SAMENVATTING
Maakt objecten op als een brede tabel waarin slechts één eigenschap van elk object wordt weer gegeven.

## SYNTAXIS

```
Format-Wide [[-Property] <Object>] [-AutoSize] [-Column <int>] [-GroupBy <Object>] [-View <string>]
  [-ShowError] [-DisplayError] [-Force] [-Expand <string>] [-InputObject <psobject>]
  [<CommonParameters>]
```

## BESCHRIJVING

`Format-Wide`Met de cmdlet worden objecten opgemaakt als een brede tabel waarin slechts één eigenschap van elk object wordt weer gegeven. U kunt de **eigenschap** para meter gebruiken om te bepalen welke eigenschap wordt weer gegeven.

## VOORBEELDEN

### Voor beeld 1: de namen van bestanden in de huidige map Format teren

Met deze opdracht worden de namen van de bestanden in de huidige map in drie kolommen op het scherm weer gegeven.

```powershell
Get-ChildItem | Format-Wide -Column 3
```

Met de cmdlet Get-ChildItem worden objecten opgehaald die elk bestand in de map vertegenwoordigen. De pijplijn operator (|) geeft de bestands objecten door aan de pijp lijn naar `Format-Wide` , waardoor ze worden opgemaakt voor uitvoer. De para meter **Column** geeft het aantal kolommen aan.

### Voor beeld 2: de namen van register sleutels opmaken

Met deze opdracht worden de namen van register sleutels in de sleutel HKEY_CURRENT_USER\Software\Microsoft weer gegeven.

```powershell
Get-ChildItem HKCU:\software\microsoft | Format-Wide -Property pschildname -AutoSize
```

De Get-ChildItem cmdlet haalt objecten op die de sleutels vertegenwoordigen. Het pad wordt opgegeven als HKCU:, een van de stations die worden weer gegeven door de Power shell-register provider, gevolgd door het sleutelpad. Met de pijplijn operator (|) worden de register sleutel objecten door gegeven via de pijp lijn naar `Format-Wide` , waarmee ze worden geformatteerd voor uitvoer. De **eigenschap** para meter geeft de naam van de eigenschap op en de **AutoSize** -para meter past de kolommen voor de Lees baarheid aan.

### Voor beeld 3: problemen met indelings fouten oplossen

In de volgende voor beelden ziet u de resultaten van het toevoegen van de para meters **Display error** of **show error** met een expressie.

```powershell
PS /> Get-Date | Format-Wide { $_ / $null } -DisplayError


#ERR

PS /> Get-Date | Format-Wide { $_ / $null } -ShowError


Failed to evaluate expression " $_ / $null ".
+ CategoryInfo          : InvalidArgument: (12/21/2018 8:18:01 AM:PSObject) [], RuntimeException
+ FullyQualifiedErrorId : PSPropertyExpressionError
```

## PARAMETERS

### -AutoSize

Past de kolom grootte en het aantal kolommen aan op basis van de breedte van de gegevens. De grootte en het aantal van de kolom worden standaard bepaald door de weer gave. U kunt de para meters **AutoSize** en **Column** niet in dezelfde opdracht gebruiken.

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

### -Kolom

Hiermee wordt het aantal kolommen in de weer gave opgegeven. U kunt de para meters **AutoSize** en **Column** niet in dezelfde opdracht gebruiken.

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

Hiermee worden fouten weer gegeven op de opdracht regel. Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-Wide` opdracht en de expressies worden niet weer gegeven.

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

Hiermee wordt het verzamelings object opgemaakt, evenals de objecten in de verzameling. Deze para meter is ontworpen om objecten op te maken die ondersteuning bieden voor de ICollection-interface (System. Collections). De standaard waarde is **EnumOnly**.

Geldige waarden zijn:

- EnumOnly: Hiermee worden de eigenschappen van de objecten in de verzameling weer gegeven.
- CoreOnly: Hiermee worden de eigenschappen van het verzamelings object weer gegeven.
- Beide: Hiermee worden de eigenschappen van het verzamelings object en de eigenschappen van objecten in de verzameling weer gegeven.

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

Hiermee wordt aangegeven dat met deze cmdlet de beperkingen worden overschreven waarmee wordt voor komen dat de opdracht kan worden uitgevoerd, zodat de wijzigingen geen inbreuk maken op de beveiliging. **Forceert** bijvoorbeeld het kenmerk alleen-lezen of maakt mappen om een bestandspad te volt ooien, maar er wordt geen poging gedaan om bestands machtigingen te wijzigen.

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

Hiermee geeft u de objecten op die moeten worden opgemaakt. Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.

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

- Expressie- `<string>` of `<script block>`
- Tring `<string>`

Zie [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)voor meer informatie.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Show error

Hiermee worden fouten verzonden via de pijp lijn. Deze para meter wordt zelden gebruikt, maar kan worden gebruikt als hulp bij het opsporen van een fout in een `Format-Wide` opdracht en de expressies worden niet weer gegeven.

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

Geeft de naam van een alternatieve tabel indeling of weer gave aan. U kunt de **Eigenschappen** en **weer gave** -para meters niet gebruiken in dezelfde opdracht.

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

U kunt elk object door sluizen naar `Format-Wide` .

## UITVOER

### Micro soft. Power shell. commands. internal. Format

`Format-Wide` retourneert de indelings objecten die de tabel vertegenwoordigen.

## OPMERKINGEN

U kunt ook verwijzen naar `Format-Wide` de ingebouwde alias `fw` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.

De para meter **GroupBy** gaat ervan uit dat de objecten zijn gesorteerd. Gebruik `Sort-Object` voordat `Format-Custom` u de objecten groepeert.

Met de para meter **weer geven** kunt u een alternatieve notatie voor de tabel opgeven. U kunt de weer gaven gebruiken die zijn gedefinieerd in de `*.format.PS1XML` bestanden in de Power shell-map, maar u kunt ook uw eigen weer gaven maken in nieuwe PS1XML-bestanden en de `Update-FormatData` cmdlet gebruiken om deze op te geven in Power shell.

De alternatieve weer gave voor de **weergave** parameter moet tabel indeling gebruiken. Als dat niet het geval is, mislukt de opdracht. Als de weer gave alternatieve een lijst is, gebruikt u `Format-List` . Als de alternatieve weer gave geen lijst of tabel is, gebruikt u indeling-aangepast.

## GERELATEERDE KOPPELINGEN

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[Format-Custom](Format-Custom.md)

[Format-Hex](Format-Hex.md)

[Format-List](Format-List.md)

[Format-Table](Format-Table.md)
