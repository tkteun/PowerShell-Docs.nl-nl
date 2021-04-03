---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: ec442dd1e24774b21cf9e00f2e46226d0b714432
ms.sourcegitcommit: c91f79576bc54e162bcc7adf78026417b2776687
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2021
ms.locfileid: "106274218"
---
# New-Alias

## Samen vatting
Hiermee maakt u een nieuwe alias.

## Syntax

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## Beschrijving

De `New-Alias` cmdlet maakt een nieuwe alias in de huidige Windows Power shell-sessie. Aliassen die zijn gemaakt met behulp van `New-Alias` worden niet opgeslagen nadat u de sessie afsluit of Windows Power shell hebt gesloten.
U kunt de- `Export-Alias` cmdlet gebruiken om uw alias gegevens op te slaan in een bestand. U kunt later gebruiken `Import-Alias` om die opgeslagen alias gegevens op te halen.

## Voorbeelden

### Voor beeld 1: een alias maken voor een cmdlet

```
New-Alias -Name "List" Get-ChildItem
```

Met deze opdracht maakt u een alias met de naam lijst die de Get-ChildItem-cmdlet vertegenwoordigt.

### Voor beeld 2: een alleen-lezen-alias maken voor een cmdlet

```
New-Alias -Name "C" -Value Get-ChildItem -Description "quick gci alias" -Option ReadOnly
Get-Alias -Name "C" | Format-List *
```

Met deze opdracht maakt u een alias `C` met de naam die de `Get-ChildItem` cmdlet vertegenwoordigt. Er wordt een beschrijving, een snelle WMI-alias voor de alias gemaakt en deze wordt alleen-lezen. De laatste regel van de opdracht wordt gebruikt `Get-Alias` om de nieuwe alias op te halen en deze te Format-List om alle informatie hierover weer te geven.

## Parameters

### -Beschrijving

Hiermee geeft u een beschrijving van de alias. U kunt een wille keurige teken reeks typen. Als de beschrijving spaties bevat, plaatst u deze tussen aanhalings tekens.

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

### -Force

Geeft aan dat de cmdlet fungeert `Set-Alias` als de alias die al bestaat.

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

### -Name

Hiermee geeft u de nieuwe alias. U kunt alle alfanumerieke tekens in een alias gebruiken, maar het eerste teken mag geen getal zijn.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Optie

Hiermee geeft u de waarde van de eigenschap **Options** van de alias.
Geldige waarden zijn:

- `None`: De alias heeft geen beperkingen (standaard waarde)
- `ReadOnly`: De alias kan worden verwijderd, maar kan niet worden gewijzigd met behulp van de para meter **Force**
- `Constant`: De alias kan niet worden verwijderd of gewijzigd
- `Private`: De alias is alleen beschikbaar in het huidige bereik
- `AllScope`: De alias wordt gekopieerd naar een nieuwe scope die wordt gemaakt
- `Unspecified`: De optie is niet opgegeven

Deze waarden worden gedefinieerd als inventarisatie op basis van een vlag. U kunt meerdere waarden combi neren om meerdere vlaggen in te stellen met behulp van deze para meter. De waarden kunnen worden door gegeven aan de para meter **Option** als een matrix met waarden of als een door komma's gescheiden teken reeks van die waarden. Met de cmdlet worden de waarden gecombineerd met behulp van een binaire waarde of bewerking. Het door geven van waarden als een matrix is de eenvoudigste optie. Daarnaast kunt u met behulp van de waarden van het tabblad volt ooien.

Als u de eigenschap **Options** van alle aliassen in de sessie wilt weer geven, typt u `Get-Alias | Format-Table -Property Name, Options -AutoSize` .

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt. Deze cmdlet genereert standaard geen uitvoer.

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

### -Bereik

Hiermee wordt het bereik van de nieuwe alias opgegeven. De aanvaardbare waarden voor deze parameter zijn:

- `Global`
- `Local`
- `Script`
- Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij `0` het huidige bereik is en de `1` bovenliggende scope).

`Local` is de standaardwaarde. Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.

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

### -Waarde

Hiermee geeft u de naam op van de cmdlet of het opdracht element waarvoor een alias wordt toegepast.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## Invoerwaarden

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## Uitvoerwaarden

### Geen of System. Management. Automation. AliasInfo

Wanneer u de para meter **PassThru** gebruikt, `New-Alias` genereert een **System. Management. Automation. AliasInfo** -object dat de nieuwe alias vertegenwoordigt. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## Notities

- Als u een nieuwe alias wilt maken, gebruikt u `Set-Alias` of `New-Alias` . Als u een alias wilt wijzigen, gebruikt u `Set-Alias` . Als u een alias wilt verwijderen, gebruikt u `Remove-Item` .

## Verwante koppelingen

[Exporteren-alias](Export-Alias.md)

[Get-alias](Get-Alias.md)

[Import-alias](Import-Alias.md)

[Set-alias](Set-Alias.md)
