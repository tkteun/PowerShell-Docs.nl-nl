---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: c9e6f844b25abe5f2a94aa929eeeb457efab3d44
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249753"
---
# New-Alias

## SAMENVATTING
Hiermee maakt u een nieuwe alias.

## SYNTAXIS

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **New-alias** maakt u een nieuwe alias in de huidige Power shell-sessie.
Aliassen die zijn gemaakt met behulp van **New-alias** worden niet opgeslagen nadat u de sessie afsluit of Power shell sluiten.
U kunt de Export-Alias cmdlet gebruiken om uw alias gegevens op te slaan in een bestand.
U kunt later **import-alias** gebruiken om die opgeslagen alias gegevens op te halen.

## VOORBEELDEN

### Voor beeld 1: een alias maken voor een cmdlet

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

Met deze opdracht maakt u een alias met de naam lijst die de Get-ChildItem-cmdlet vertegenwoordigt.

### Voor beeld 2: een alleen-lezen-alias maken voor een cmdlet

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

Met deze opdracht maakt u een alias met de naam W om de cmdlet Get-WmiObject te vertegenwoordigen.
Er wordt een beschrijving, een snelle WMI-alias voor de alias gemaakt en deze wordt alleen-lezen.
De laatste regel van de opdracht maakt gebruik van Get-Alias om de nieuwe alias te verkrijgen en deze te Format-List om alle informatie hierover weer te geven.

## PARAMETERS

### -Beschrijving

Hiermee geeft u een beschrijving van de alias.
U kunt een wille keurige teken reeks typen.
Als de beschrijving spaties bevat, plaatst u deze tussen aanhalings tekens.

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

Geeft aan dat de cmdlet als Set-Alias fungeert als de alias met de naam al bestaat.

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

Hiermee geeft u de nieuwe alias.
U kunt alle alfanumerieke tekens in een alias gebruiken, maar het eerste teken mag geen getal zijn.

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

- Geen: de alias heeft geen beperkingen (standaard waarde)
- ReadOnly: de alias kan worden verwijderd, maar kan niet worden gewijzigd met behulp van de para meter **Force**
- Constante: de alias kan niet worden verwijderd of gewijzigd
- Persoonlijk: de alias is alleen beschikbaar in het huidige bereik
- AllScope: de alias wordt gekopieerd naar een nieuwe scope die wordt gemaakt
- Niet opgegeven: de optie is niet opgegeven

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

Retourneert een object dat het item vertegenwoordigt waarmee u werkt.
Deze cmdlet genereert standaard geen uitvoer.

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

Hiermee wordt het bereik van de nieuwe alias opgegeven.
De aanvaardbare waarden voor deze parameter zijn:

- Globaal
- Lokaal
- Script
- Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope).

Local is de standaard instelling.
Zie about_Scopes voor meer informatie.

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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Geen of System. Management. Automation. AliasInfo

Wanneer u de para meter *PassThru* gebruikt, genereert **New-alias** een **System. Management. Automation. AliasInfo** -object dat de nieuwe alias vertegenwoordigt.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* Als u een nieuwe alias wilt maken, gebruikt u `Set-Alias` of `New-Alias` . Als u een alias wilt wijzigen, gebruikt u `Set-Alias` . Als u een alias wilt verwijderen, gebruikt u `Remove-Item` .

## GERELATEERDE KOPPELINGEN

[Exporteren-alias](Export-Alias.md)

[Get-alias](Get-Alias.md)

[Import-alias](Import-Alias.md)

[Set-alias](Set-Alias.md)
