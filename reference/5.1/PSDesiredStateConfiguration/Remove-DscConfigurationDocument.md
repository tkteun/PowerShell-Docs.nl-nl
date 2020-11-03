---
external help file: Remove-DscConfigurationDocument.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-DscConfigurationDocument
ms.openlocfilehash: d3e9b15dfeea94921503247adc08b291eed9d7d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250766"
---
# Remove-DscConfigurationDocument

## SAMENVATTING
Hiermee verwijdert u een configuratie document uit de DSC-configuratie opslag.

## SYNTAXIS

```
Remove-DscConfigurationDocument -Stage <Stage> [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>]
 [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De `Remove-DscConfigurationDocument` cmdlet verwijdert een configuratie document (. MOF-bestand) uit het configuratie archief Windows Power shell desired state Configuration (DSC).
Tijdens de configuratie `Start-DscConfiguration` kopieert de cmdlet een. MOF-bestand naar een map op de doel computer.
Met deze cmdlet wordt dat configuratie document verwijderd en wordt er extra opgeruimd.

Deze cmdlet is alleen beschikbaar als onderdeel van het [Update pakket van November 2014 voor Windows RT 8,1, Windows 8,1 en Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) uit de Microsoft ondersteuning-bibliotheek.

## VOORBEELDEN

### Voor beeld 1: het huidige configuratie document verwijderen

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Remove-DscConfigurationDocument -Stage Current -CimSession $Session
```

Met de eerste opdracht maakt u een CIM-sessie met behulp van de cmdlet **New-CimSession** en slaat u het **CimSession** -object op in de variabele $Session.
De opdracht vraagt u om een wacht woord.
Typ `Get-Help New-CimSession` voor meer informatie.

Met de tweede opdracht wordt het huidige configuratie document verwijderd voor de computer die is opgegeven in de **CimSession** die zijn opgeslagen in $Session.

## PARAMETERS

### -AsJob
Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.

Als u de para meter *AsJob* opgeeft, retourneert de opdracht een object dat de taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven.
U kunt in de sessie blijven werken totdat de taak is voltooid.
De taak wordt gemaakt op de lokale computer en de resultaten van externe computers worden automatisch geretourneerd naar de lokale computer.
Gebruik de taak-cmdlets om de taak te beheren.
Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.

Als u deze para meter wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang en op Windows Vista en latere versies van het Windows-besturings systeem, moet u Windows Power shell openen met de optie als administrator uitvoeren.
Zie [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md)voor meer informatie.

Zie [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) en [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md)voor meer informatie over Windows Power shell-achtergrond taken.

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
Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet **New-CimSession** of **Get-CimSession** .

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

### -Force
Geeft aan dat deze cmdlet de actieve configuratie taak stopt voordat het configuratie document wordt verwijderd.
Hiermee wordt de opdracht uitgevoerd zonder dat de gebruiker om bevestiging wordt gevraagd.

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

### -Fase
Hiermee geeft u op welk configuratie document moet worden verwijderd.
U kunt meerdere documenten opgeven.
De aanvaardbare waarden voor deze parameter zijn:

- VLOTT.
Verwijder het configuratie document waarin de huidige status van het systeem wordt beschreven.
- Status.
Verwijder het configuratie document met een beschrijving van de status van het systeem in behandeling.
- Bestaande.
Verwijder het configuratie document waarin de vorige status van het systeem wordt beschreven.

```yaml
Type: Microsoft.PowerShell.Cmdletization.GeneratedTypes.RemoveDscConfigurationDocument.Stage
Parameter Sets: (All)
Aliases:
Accepted values: Current, Pending, Previous

Required: True
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

## UITVOER

### Geen

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Overzicht van desired state Configuration voor Windows Power shell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)
