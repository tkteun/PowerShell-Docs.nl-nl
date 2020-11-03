---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: 128bdd997e006723a69997e1419efd2f012e97f6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249818"
---
# Get-Variable

## SAMENVATTING
Hiermee worden de variabelen in de huidige console opgehaald.

## SYNTAXIS

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## BESCHRIJVING

`Get-Variable`Met de cmdlet worden de Power shell-variabelen in de huidige console opgehaald.
U kunt alleen de waarden van de variabelen ophalen door de para meter **ValueOnly** op te geven en u kunt de variabelen filteren die worden geretourneerd door de naam.

## VOORBEELDEN

### Voor beeld 1: variabelen ophalen per letter

Met deze opdracht worden variabelen opgehaald met namen die beginnen met de letter m.
Met deze opdracht wordt ook de waarde van de variabelen opgehaald.

```powershell
Get-Variable m*
```

### Voor beeld 2: variabele waarden ophalen per letter

Met deze opdracht worden alleen de waarden opgehaald van de variabelen met een naam die begint met m.

```powershell
Get-Variable m* -ValueOnly
```

### Voor beeld 3: variabelen ophalen met twee letters

Met deze opdracht haalt u informatie op over de variabelen die beginnen met de letter M of de letter P.

```powershell
Get-Variable -Include M*,P*
```

### Voor beeld 4: variabelen ophalen op basis van het bereik

De eerste opdracht haalt alleen de variabelen op die in het lokale bereik zijn gedefinieerd.
Het is gelijk aan `Get-Variable -Scope Local` en kan worden afgekort tot `gv -s 0` .

Met de tweede opdracht wordt de `Compare-Object` cmdlet gebruikt om de variabelen te vinden die in het bovenliggende bereik zijn gedefinieerd (Scope 1), maar die alleen zichtbaar zijn in de lokale scope (scope 0).

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## PARAMETERS

### -Uitsluiten

Hiermee geeft u een matrix van items op die met deze cmdlet worden uitgesloten van de bewerking.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Hiermee wordt een matrix opgegeven met items waarop de cmdlet wordt toegepast, met uitzonde ring van alle andere.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

Hiermee geeft u de naam van de variabele.
Joker tekens zijn toegestaan.
U kunt ook de naam van een variabele naar `Get-Variable` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Bereik

Hiermee geeft u de variabelen in het bereik. De acceptabele waarden voor deze para meter zijn:

- **Globaal**
- **Lokaal**
- **Script**
- Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)

**Local** is de standaard instelling.
Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.

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

### -ValueOnly

Geeft aan dat met deze cmdlet alleen de waarde van de variabele wordt opgehaald.

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

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met de naam van de variabele door sluizen naar `Get-Variable` .

## UITVOER

### System. Management. Automation. PSVariable

Met deze cmdlet wordt een **System. Management. AutomationPSVariable** -object geretourneerd voor elke variabele die wordt opgehaald. Het object type is afhankelijk van de variabele.

### System. object []

Als u de para meter **ValueOnly** opgeeft en de waarde van de opgegeven variabele een verzameling is, `Get-Variable` retourneert een `[System.Object[]]` . Dit gedrag voor komt dat normale bewerking door de pijp lijn de waarden van de variabele een voor een kan verwerken. Een tijdelijke oplossing voor het afdwingen van verzamelings inventarisatie is het insluiten `Get-Variable` van de opdracht tussen haakjes.

## OPMERKINGEN

- Met deze cmdlet worden geen omgevings variabelen beheerd. Als u omgevings variabelen wilt beheren, kunt u de omgevings variabele provider gebruiken.

## GERELATEERDE KOPPELINGEN

[Clear-variabele](Clear-Variable.md)

[Nieuwe variabele](New-Variable.md)

[Remove-variabele](Remove-Variable.md)

[Set-variabele](Set-Variable.md)
