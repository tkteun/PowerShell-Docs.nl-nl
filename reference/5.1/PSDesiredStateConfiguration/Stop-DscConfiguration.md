---
external help file: Stop-DscConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/19/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/stop-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-DscConfiguration
ms.openlocfilehash: 93c8585ae948dfa360a2ae8e2563670de8fd6e93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250347"
---
# Stop-DscConfiguration

## SAMENVATTING
Hiermee stopt u een configuratie taak die wordt uitgevoerd.

## SYNTAXIS

### Alles

```
Stop-DscConfiguration [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Stop-DscConfiguration` cmdlet stopt een configuratie taak die wordt uitgevoerd. Geef op op welke computers deze cmdlet van toepassing is met behulp van Common Information Model (CIM)-sessies. Als er geen configuratie taak wordt uitgevoerd, wordt met deze cmdlet een waarschuwings bericht weer gegeven.

`Stop-DscConfiguration` is alleen beschikbaar als onderdeel van het [Update pakket van November 2014 voor Windows RT 8,1, windows 8,1 en Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) van de Microsoft ondersteuning-bibliotheek. Voordat u deze cmdlet gebruikt, raadpleegt u de informatie in [What's New in Windows Power shell 5,0](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)

## VOORBEELDEN

### Voor beeld 1: een configuratie taak stoppen

In dit voor beeld wordt een CIM-sessie gemaakt met behulp van de `New-CimSession` cmdlet. Het **CimSession** -object wordt gebruikt om een actieve configuratie taak te stoppen.

```powershell
$Session = New-CimSession -ComputerName Server01 -Credential ACCOUNTS\User01
Stop-DscConfiguration -CimSession $Session
```

`New-CimSession` maakt gebruik van de para meter **ComputerName** om de Server01-computer op te geven. De **referentie** parameter geeft u het gebruikers account op. Het **CimSession** -object wordt opgeslagen in de `$Session` variabele. Wanneer de opdracht wordt uitgevoerd, wordt u gevraagd het wacht woord van het gebruikers account op te vragen.

`Stop-DscConfiguration` maakt gebruik van de para meter **CimSession** en het object dat is opgeslagen in `$Session` om de configuratie taak te stoppen.

## PARAMETERS

### -AsJob

Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak. Zie [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)voor meer informatie over Power shell-achtergrond taken.

Als u de para meter **AsJob** wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang. In Windows Vista en latere versies van het Windows-besturings systeem moet u Power shell openen met de optie **als administrator uitvoeren** . Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)voor meer informatie.

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

### -CimSession

Voert de cmdlet uit in een externe sessie of op een externe computer. Voer een computer naam of een sessie object in, zoals de uitvoer van `New-CimSession` of `Get-CimSession` .

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

### -Confirm

`Stop-DscConfiguration` biedt geen ondersteuning voor de **confirm** -para meter. Als de para meter **confirm** wordt gebruikt, wordt er een fout bericht weer gegeven.

Voor Power shell-cmdlets die ondersteuning bieden voor het **bevestigen** , wordt u door de para meter gevraagd om verificatie voordat een opdracht wordt uitgevoerd.

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

### -Force

Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

### -ThrottleLimit

Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet.

Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, berekent Power shell een optimale bandbreedte limiet op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd. De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.

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

### Geen

## UITVOER

### Geen

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-CimSession](../CimCmdlets/Get-CimSession.md)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[New-CimSession](../CimCmdlets/New-CimSession.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)

[Update-DscConfiguration](Update-DscConfiguration.md)

[Overzicht van desired state Configuration voor Windows Power shell](/powershell/scripting/dsc/overview/overview)
