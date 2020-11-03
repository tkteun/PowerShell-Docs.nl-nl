---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/07/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-verb?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: a1459c276d8d6b2d031bc4b4f7ab521f7582a4cb
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/11/2020
ms.locfileid: "93251809"
---
# Get-Verb

## SAMENVATTING
Hiermee worden goedgekeurde Power shell-woorden opgehaald.

## SYNTAXIS

```
Get-Verb [[-Verb] <String[]>] [[-Group] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Verb` functie haalt werk woorden op die zijn goedgekeurd voor gebruik in Power shell-opdrachten.

U wordt aangeraden de Power shell-cmdlet en functie namen de `Verb-Noun` indeling te bieden en een goedgekeurde term te bevatten. Met deze procedure worden opdracht namen consistent, voorspelbaar en gemakkelijker te gebruiken.

Opdrachten die gebruikmaken van niet-goedgekeurde woorden, worden nog steeds uitgevoerd in Power shell. Wanneer u echter een module importeert die een opdracht met een niet-goedgekeurde term in de naam bevat, `Import-Module` wordt er een waarschuwings bericht weer gegeven.

> [!NOTE]
> De woorden lijst die `Get-Verb` wordt geretourneerd, is mogelijk niet volledig. Zie [goedgekeurde werk woorden](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in de Microsoft docs voor een bijgewerkte lijst met goedgekeurde Power shell-termen met beschrijvingen.

## Voorbeelden

### Voor beeld 1: een lijst met alle woorden ophalen

```powershell
Get-Verb
```

### Voor beeld 2: een lijst met goedgekeurde woorden ophalen die beginnen met ' ongedaan maken '

```powershell
Get-Verb un*
```

```Output
Verb       AliasPrefix Group     Description
----       ----------- -----     -----------
Undo       un          Common    Sets a resource to its previous state
Unlock     uk          Common    Releases a resource that was locked
Unpublish  ub          Data      Makes a resource unavailable to others
Uninstall  us          Lifecycle Removes a resource from an indicated location
Unregister ur          Lifecycle Removes the entry for a resource from a repository
Unblock    ul          Security  Removes restrictions to a resource
Unprotect  up          Security  Removes safeguards from a resource that were added to prevent it from attack or loss
```

### Voor beeld 3: alle goedgekeurde werk woorden ophalen in de beveiligings groep

```powershell
Get-Verb -Group Security
```

```Output
Verb      AliasPrefix Group    Description
----      ----------- -----    -----------
Block     bl          Security Restricts access to a resource
Grant     gr          Security Allows access to a resource
Protect   pt          Security Safeguards a resource from attack or loss
Revoke    rk          Security Specifies an action that does not allow access to a resource
Unblock   ul          Security Removes restrictions to a resource
Unprotect up          Security Removes safeguards from a resource that were added to prevent it from attack or loss
```

### Voor beeld 4: Hiermee vindt u alle opdrachten in een module die een niet-goedgekeurde term hebben

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## PARAMETERS

### -Verb

Hiermee worden alleen de opgegeven termen opgehaald. Voer de naam van een werk woord of een naam patroon in. Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Common, Communications, Data, Diagnostic, Lifecycle, Other, Security

Required: False
Position: 1
Default value: All groups
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Group

Hiermee worden alleen de opgegeven groepen opgehaald. Voer de naam van een groep in. Joker tekens zijn niet toegestaan.

Deze para meter is geïntroduceerd in Power shell 6,0.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All verbs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

## UITVOER

### System. Management. Automation. VerbInfo

## OPMERKINGEN

Power shell-werk woorden worden toegewezen aan een groep op basis van het meest voorkomende gebruik. De groepen zijn ontworpen om de werk woorden gemakkelijk te vinden en te vergelijken, en om het gebruik ervan te beperken. U kunt elk goedgekeurd werk woord voor elk type opdracht gebruiken.

Elke Power shell-term wordt toegewezen aan een van de volgende groepen.

- Algemeen: Definieer algemene acties die van toepassing kunnen zijn op bijna elke cmdlet, zoals toevoegen.
- Communicatie: acties definiëren die van toepassing zijn op de communicatie, zoals verbinding maken.
- Gegevens: acties definiëren die van toepassing zijn op de verwerking van gegevens, zoals back-up.
- Diagnose: acties definiëren die van toepassing zijn op diagnostische gegevens, zoals fout opsporing.
- Levenscyclus: Definieer acties die van toepassing zijn op de levens cyclus van een cmdlet, zoals voltooid.
- Beveiliging: Definieer acties die van toepassing zijn op de beveiliging, zoals intrekken.
- Overige: andere typen acties definiëren.

Sommige cmdlets die zijn geïnstalleerd met Power shell, zoals `Tee-Object` en `Where-Object` , gebruiken niet-goedgekeurde werk woorden. Deze cmdlets zijn historische uitzonde ringen en hun werk woorden worden als **gereserveerd** geclassificeerd.

## GERELATEERDE KOPPELINGEN

[Import-module](../microsoft.powershell.core/import-module.md)
