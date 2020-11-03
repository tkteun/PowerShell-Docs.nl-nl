---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: cc660b80a29d2e27a0b3928c1073168b2575af8f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249778"
---
# Get-PSSessionCapability

## SAMENVATTING
Hiermee worden de mogelijkheden van een specifieke gebruiker voor een beperkte sessie configuratie opgehaald.

## SYNTAXIS

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **Get-PSSessionCapability** worden de mogelijkheden van een specifieke gebruiker voor een beperkte sessie configuratie opgehaald.
Gebruik deze cmdlet om aangepaste sessie configuraties voor gebruikers te controleren.

Vanuit Windows Power shell 5,0 kunt u de eigenschap **RoleDefinitions** in een sessie configuratie bestand (. pssc) gebruiken.
Met deze eigenschap kunt u gebruikers verschillende mogelijkheden geven op een enkel beperkt eind punt op basis van groepslid maatschap.
De cmdlet **Get-PSSessionCapability** vermindert de complexiteit bij het controleren van deze eind punten door u de exacte mogelijkheden te bepalen die aan een gebruiker worden verleend.

De cmdlet **Get-PSSessionCapability** retourneert standaard een lijst met opdrachten die de opgegeven gebruiker kan uitvoeren in het opgegeven eind punt.
Dit is gelijk aan de gebruiker die **Get-opdracht** uitvoert in het opgegeven eind punt.
Wanneer u uitvoert met de *volledige* para meter, retourneert deze cmdlet een **InitialSessionState** -object.
Dit object bevat details over de Power shell-runs Pace waarmee de opgegeven gebruiker communiceert voor het opgegeven eind punt.
Het bevat informatie zoals de taal modus, het uitvoerings beleid en omgevings variabelen.

## VOORBEELDEN

### Voor beeld 1: opdrachten ophalen die beschikbaar zijn voor een gebruiker

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

In dit voor beeld worden de opdrachten die beschikbaar zijn voor de gebruiker CONTOSO\User wanneer verbinding wordt gemaakt met het Endpoint1 beperkte eind punt op de lokale computer.

### Voor beeld 2: Details over een runs Pace voor een gebruiker ophalen

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

In dit voor beeld worden details geretourneerd over de runs Pace waarmee de gebruiker CONTOSO\User zou communiceren wanneer er verbinding wordt gemaakt met het Endpoint1-beperkt eind punt.

## PARAMETERS

### -Configuratiepad

Hiermee geeft u de beperkte sessie configuratie (eind punt) op die u wilt inspecteren.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Volledig

Geeft aan dat deze cmdlet de volledige initiële sessie status retourneert voor de opgegeven gebruiker op het opgegeven beperkte eind punt.

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

### -Gebruikers naam

Hiermee geeft u de gebruiker waarvan u de mogelijkheden wilt inspecteren.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

### System. Management. Automation. AliasInfo

### System. Management. Automation. FunctionInfo

### System.Management.Automation.Runspaces.InitialSessionState

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[New-PSRoleCapabilityFile](New-PSRoleCapabilityFile.md)
