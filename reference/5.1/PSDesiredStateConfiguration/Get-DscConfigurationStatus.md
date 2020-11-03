---
external help file: Get-DscConfigurationStatus.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfigurationStatus
ms.openlocfilehash: 0d59ce58a70eab68441ea1fe6097bbdf7792a54f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250782"
---
# Get-DscConfigurationStatus

## SAMENVATTING
Haalt gegevens op over voltooide configuratie-uitvoeringen.

## SYNTAXIS

```
Get-DscConfigurationStatus [-All] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Get-DscConfigurationStatus** haalt gedetailleerde informatie op over voltooide configuratie-uitvoeringen op het systeem.
Standaard wordt de informatie over de laatste configuratie-uitvoering geretourneerd.
Deze cmdlet is handig voor het vinden van historische informatie over configuratie runs, zoals wanneer de configuraties werden uitgevoerd, de status van de uitvoeringen, het aantal resources in de configuraties en welke resources zijn geslaagd of mislukt.

## VOORBEELDEN

### Voor beeld 1: informatie over de laatste configuratie-uitvoering ophalen

```
PS C:\> Get-DscConfigurationStatus
```

Met deze opdracht wordt informatie over de laatste configuratie-uitvoering opgehaald.

### Voor beeld 2: informatie over alle configuraties ophalen

```
PS C:\> Get-DscConfigurationStatus -All
```

Met deze opdracht wordt informatie opgehaald over alle configuraties die op het systeem zijn uitgevoerd, inclusief de consistentie controle van de desired state Configuration (DSC) van Windows Power shell.

### Voor beeld 3: informatie over de configuratie uitvoeren op een externe computer

```
PS C:\> Get-DscConfigurationStatus -CimSession "Server01"
```

Met deze opdracht worden de details van de configuratie-uitvoering opgehaald van de externe computer met de naam Server01.
Dit maakt gebruik van het WSMan-Trans Port om verbinding te maken met de externe computer en vereist dat de gebruiker die de verbinding maakt, een beheerder is op de externe computer.

## PARAMETERS

### -Alle
Geeft aan dat deze cmdlet informatie ophaalt over alle configuratie runs op de computer, met inbegrip van de configuratie toepassing en de consistentie controle.

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

### -AsJob
Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.

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

### -CimSession
Voert de cmdlet uit in een externe sessie of op een externe computer.
Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .
De standaard waarde is de huidige sessie op de lokale computer.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.
Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd.
De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.

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

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Overzicht van desired state Configuration voor Windows Power shell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscLocalConfigurationManager](Get-DscLocalConfigurationManager.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
