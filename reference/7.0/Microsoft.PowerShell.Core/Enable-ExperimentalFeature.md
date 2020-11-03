---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-experimentalfeature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ExperimentalFeature
ms.openlocfilehash: 79884c73bc6e010eb218f1b722d26e0aaa05ef53
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249705"
---
# Enable-ExperimentalFeature

## SAMENVATTING
Een experimentele functie inschakelen bij het opstarten van een nieuw exemplaar van Power shell.

## SYNTAXIS

```
Enable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Enable-ExperimentalFeature` cmdlet maakt experimentele functies mogelijk door de genoemde experimentele functies toe te voegen aan het `powershell.config.json` instellingen bestand dat in Power shell wordt gestart.

Deze cmdlet is geïntroduceerd in Power shell 6,2.

> [!NOTE]
> Wijzigingen in de status van experimentele functies worden alleen van kracht bij het opnieuw opstarten van Power shell

## VOORBEELDEN

### Voor beeld 1: een experimentele functie inschakelen

Als deze experimentele functie eerder is uitgeschakeld, wordt het bestand in dit voor beeld `powershell.config.json` bijgewerkt zodat de gebruiker die functie inschakelt nadat Power shell opnieuw is opgestart.
Wanneer het succes is, wordt er niets naar de pijp lijn uitgevoerd en wordt er alleen een waarschuwings bericht weer gegeven.

```powershell
Enable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## PARAMETERS

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

De naam of namen van de experimentele functies die moeten worden ingeschakeld.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Bereik

Hiermee wordt bepaald welke `powershell.config.json` moet worden bijgewerkt of dit van invloed is op alle gebruikers of alleen de huidige gebruiker.

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### ExperimentalFeature

Pipe-exemplaren van ExperimentalFeature van de `Get-ExperimentalFeature` cmdlet die u wilt inschakelen.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

Wijzigingen in de status van een experimentele functie worden alleen van kracht bij het opnieuw opstarten van Power shell.

## GERELATEERDE KOPPELINGEN

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Get-ExperimentalFeature](Get-ExperimentalFeature.md)
