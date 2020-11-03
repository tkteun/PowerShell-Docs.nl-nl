---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/07/2018
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/get-verb?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 4474bb50c2bf3be10e72d2554190208e956f9040
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/11/2020
ms.locfileid: "93251807"
---
# Get-Verb

## SAMENVATTING
Hiermee worden goedgekeurde Power shell-woorden opgehaald.

## SYNTAXIS

```
Get-Verb [[-verb] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Verb` functie haalt werk woorden op die zijn goedgekeurd voor gebruik in Power shell-opdrachten.

Power shell raadt cmdlet-en functie namen aan de Verb-Noun-indeling en een goedgekeurde term toe. Met deze procedure worden opdracht namen consistent, voorspelbaar en gemakkelijker te gebruiken.

Opdrachten die gebruikmaken van niet-goedgekeurde woorden worden uitgevoerd in Power shell. Wanneer u echter een module importeert die een opdracht met een niet-goedgekeurde term in de naam bevat, `Import-Module` wordt er een waarschuwings bericht weer gegeven.

> [!NOTE]
> De woorden lijst die `Get-Verb` wordt geretourneerd, is mogelijk niet volledig. Zie [goedgekeurde werk woorden](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in de Microsoft docs voor een bijgewerkte lijst met goedgekeurde Power shell-termen met beschrijvingen.

## VOORBEELDEN

### Voor beeld 1: een lijst met alle woorden ophalen

```powershell
Get-Verb
```

### Voor beeld 2: een lijst met goedgekeurde woorden ophalen die beginnen met ' ongedaan maken '

```powershell
Get-Verb un*
```

```Output
Verb                 Group
----                 -----
Undo                 Common
Unlock               Common
Unpublish            Data
Uninstall            Lifecycle
Unregister           Lifecycle
Unblock              Security
Unprotect            Security
```

### Voor beeld 3: alle goedgekeurde werk woorden ophalen in de beveiligings groep

```powershell
Get-Verb | Where-Object Group -EQ Security
```

```Output
Verb      Group
----      -----
Block     Security
Grant     Security
Protect   Security
Revoke    Security
Unblock   Security
Unprotect Security
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

### -verb

Hiermee worden alleen de opgegeven termen opgehaald.
Voer de naam van een werk woord of een naam patroon in.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: All verbs
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

## INVOER

### Geen

## UITVOER

### Geselecteerd. Microsoft. Power shell. commands. MemberDefinition

## OPMERKINGEN

`Get-Verb` retourneert een gewijzigde versie van een micro soft. Power shell. commands. MemberDefinition-object.
Het object heeft niet de standaard eigenschappen van een MemberDefinition-object. In plaats daarvan heeft het verb-en Group-eigenschappen. De eigenschap verb bevat een teken reeks met de naam van de bewerking. De eigenschap Group bevat een teken reeks met de groep verb.

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

[Import-module](import-module.md)
