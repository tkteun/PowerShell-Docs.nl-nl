---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: c6347ea9ca2169c6379871131bc98001bcdb5d25
ms.sourcegitcommit: 84fcc90bd018ab76ac4e964d53e7c9c2b5a7b6c6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251654"
---
# Remove-Variable

## SAMENVATTING
Hiermee verwijdert u een variabele en de bijbehorende waarde.

## SYNTAXIS

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Remove-Variable` cmdlet verwijdert een variabele en de waarde ervan uit het bereik waarin deze is gedefinieerd, zoals de huidige sessie. U kunt deze cmdlet niet gebruiken om variabelen te verwijderen die zijn ingesteld als constanten of die eigendom zijn van het systeem.

## VOORBEELDEN

### Voor beeld 1: een variabele verwijderen

```powershell
Remove-Variable Smp
```

Met deze opdracht wordt de `$Smp` variabele verwijderd.

## PARAMETERS

### -Uitsluiten

Hiermee geeft u een matrix van items op die met deze cmdlet worden wegge laten uit de bewerking. De waarde van deze para meter komt in aanmerking voor de para meter **name** . Voer een naam element of patroon in, zoals ' s * '. Joker tekens zijn toegestaan.

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

### -Force

Geeft aan dat de cmdlet een variabele verwijdert, zelfs als deze alleen-lezen is. Zelfs met de para meter **Forces** kan de cmdlet een constante niet verwijderen.

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

### -Include

Hiermee geeft u een matrix van items op die met deze cmdlet worden verwijderd in de bewerking. De waarde van deze para meter komt in aanmerking voor de para meter **name** . Voer een naam element of patroon in, zoals s *. Joker tekens zijn toegestaan.

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

Hiermee geeft u de naam op van de variabele die moet worden verwijderd. De parameter naam ( **naam** ) is optioneel.
Joker tekens zijn toegestaan

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Bereik

Hiermee worden alleen de variabelen in het opgegeven bereik opgehaald. De aanvaardbare waarden voor deze parameter zijn:

- Globaal
- Lokaal
- Script
- Een getal dat relatief is ten opzichte van het huidige bereik (0 tot en met het aantal bereiken, waarbij 0 het huidige bereik is en 1 de bovenliggende scope)

Local is de standaard instelling. Zie [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)voor meer informatie.

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

## INVOER

### System. Management. Automation. PSVariable

U kunt een variabel object door sluizen naar `Remove-Variable` .

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

- Wijzigingen zijn alleen van invloed op het huidige bereik, zoals een sessie. Als u een variabele uit alle sessies wilt verwijderen, voegt `Remove-Variable` u een opdracht toe aan uw Power shell-profiel.

- U kunt ook verwijzen naar `Remove-Variable` de ingebouwde alias `rv` . Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Clear-variabele](Clear-Variable.md)

[Get-variabele](Get-Variable.md)

[Nieuwe variabele](New-Variable.md)

[Set-variabele](Set-Variable.md)
