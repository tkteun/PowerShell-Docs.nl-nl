---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/update-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-DscConfiguration
ms.openlocfilehash: 13365902ab317a3daa41b9a951d5e2fa6e4f1b37
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250340"
---
# Update-DscConfiguration

## SAMENVATTING
Controleert de pull-server op een bijgewerkte configuratie en past deze toe.

## SYNTAXIS

### ComputerNameSet (standaard)

```
Update-DscConfiguration [-Wait] [-JobName <String>] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionSet

```
Update-DscConfiguration [-Wait] [-JobName <String>] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De `Update-DscConfiguration` cmdlet maakt verbinding met een pull-server, downloadt de configuratie als deze afwijkt van wat er op het knoop punt staat en past de configuratie vervolgens toe op de computer.

Deze cmdlet is alleen beschikbaar als onderdeel van het [Update pakket van November 2014 voor Windows RT 8,1, Windows 8,1 en Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) uit de Microsoft ondersteuning-bibliotheek.

## VOORBEELDEN

### Voor beeld 1: een configuratie bijwerken

```
PS C:\> Update-DscConfiguration -Wait -Verbose
```

Nadat u deze opdracht hebt uitgevoerd, maakt de server verbinding met de geregistreerde pull-service, downloadt de meest recente toegewezen configuratie en past deze vervolgens toe.
De para meters-wait en-verbose zijn optioneel.
Wanneer u interactief werkt, kunt u met deze para meters realtime feedback geven over de voortgang en het slagen of mislukken bij het Toep assen van de configuratie.

### Voor beeld 2: een configuratie bijwerken door verbinding te maken via een CIM-sessie

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Update-DscConfiguration -CimSession $Session -Wait
```

Met de eerste opdracht maakt u een CIM-sessie met behulp van de cmdlet **New-CimSession** en slaat u het **CimSession** -object op in de variabele $Session.
De opdracht vraagt u om een wacht woord.
Typ `Get-Help New-CimSession` voor meer informatie.

Met de tweede opdracht wordt de computer die is opgegeven in de **CimSession** die is opgeslagen in $Session, bijgewerkt.
Met de opdracht wordt de *wait* -para meter opgegeven.
De console accepteert geen aanvullende opdrachten totdat de huidige opdracht is voltooid.

## PARAMETERS

### -CimSession
Voert de cmdlet uit in een externe sessie of op een externe computer.
Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .
De standaard waarde is de huidige sessie op de lokale computer.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
Hiermee geeft u een matrix van computer namen op.
Met de cmdlet worden de configuratie-instellingen toegepast op de computers die door deze para meter worden opgegeven.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
Hiermee geeft u een gebruikers naam en wacht woord op als een **PSCredential** -object voor de doel computer.
Als u een **PSCredential** -object wilt ophalen, gebruikt u de cmdlet Get-Credential.
Typ `Get-Help Get-Credential` voor meer informatie.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -JobName
Hiermee geeft u een beschrijvende naam voor een taak op.
Als u deze para meter opgeeft, wordt de cmdlet uitgevoerd als een taak en wordt een **taak** object geretourneerd.

Windows Power shell wijst standaard de naam JobN toe, waarbij N een geheel getal is.

Als u de *wait* -para meter opgeeft, moet u deze para meter niet opgeven.

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

### -Wachten
Geeft aan dat de cmdlet de console blokkeert totdat alle configuratie taken zijn voltooid.

Als u deze para meter opgeeft, moet u de para meter *JobName* niet opgeven.

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

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Overzicht van desired state Configuration voor Windows Power shell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Stop-DscConfiguration](Stop-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
