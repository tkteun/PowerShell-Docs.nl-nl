---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 6f98a910e43b87793ac4f2af8ffb069d3e5d47ba
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249533"
---
# Remove-Alias

## SAMENVATTING
Een alias verwijderen uit de huidige sessie.

## SYNTAXIS

### Standaard (standaard instelling)

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## BESCHRIJVING

`Remove-Alias`Met de cmdlet wordt een alias uit de huidige Power shell-sessie verwijderd. Als u een alias waarvan de eigenschap **Option** is ingesteld op **ReadOnly** wilt verwijderen, gebruikt u de para meter **Force** .

De `Remove-Alias` cmdlet is geïntroduceerd in Power shell 6,0.

## VOORBEELDEN

### Voor beeld 1: een alias verwijderen

In dit voor beeld wordt een alias `del` met de naam die de cmdlet vertegenwoordigt, verwijderd `Remove-Item` .

```powershell
Remove-Alias -Name del
```

### Voor beeld 2: alle niet-constante aliassen verwijderen

In dit voor beeld worden alle aliassen verwijderd uit de huidige Power shell-sessie, met uitzonde ring van aliassen waarvan de eigenschap **Options** is ingesteld op **constant**. Nadat de opdracht is uitgevoerd, zijn de aliassen beschikbaar in andere Power shell-sessies of nieuwe Power shell-sessies.

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

`Get-Alias` Hiermee worden alle aliassen in de Power shell-sessie opgehaald en worden de objecten van de pijp lijn omlaag verzonden.
`Where-Object` maakt gebruik van een script blok en de eigenschap Automatic variabele ( `$_` ) en **Options** vertegenwoordigen het huidige pijplijn object. De para meter **ne** (niet gelijk aan), selecteert objecten waarvoor geen **optie** waarde is ingesteld op **constant**. `Remove-Alias` maakt gebruik van de para meter **Force** om aliassen te verwijderen, met inbegrip van alleen-lezen aliassen, vanuit de Power shell-sessie.

## PARAMETERS

### -Force

Geeft aan dat de cmdlet een alias verwijdert, inclusief aliassen waarvan de eigenschap **Option** is ingesteld op **ReadOnly**. Met de para meter **Force** kan een alias waarvan de eigenschap **Option** is ingesteld op **constant** niet worden verwijderd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de naam op van de alias die u wilt verwijderen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Bereik

Alleen van invloed op de aliassen in het opgegeven bereik. Het standaard bereik is **lokaal**. Zie [about_Scopes](../microsoft.powershell.core/about/about_scopes.md)voor meer informatie.

De aanvaardbare waarden voor deze parameter zijn:

- Globaal
- Lokaal
- Script
- Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System.String[]

U kunt een alias object door sluizen om **-alias te verwijderen**.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

De wijzigingen zijn alleen van invloed op de huidige scope. Als u een alias van alle sessies wilt verwijderen, voegt u een **Verwijder-alias** opdracht toe aan uw Power shell-profiel.

Zie [about_Aliases](../microsoft.powershell.core/about/about_aliases.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[Exporteren-alias](Export-Alias.md)

[Get-alias](Get-Alias.md)

[Import-alias](Import-Alias.md)

[Nieuwe alias](New-Alias.md)

[Set-alias](Set-Alias.md)

[Where-object](../Microsoft.PowerShell.Core/Where-Object.md)
