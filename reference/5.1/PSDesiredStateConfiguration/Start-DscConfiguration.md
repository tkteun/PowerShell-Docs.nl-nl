---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/start-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-DscConfiguration
ms.openlocfilehash: c34754aeb7fce99030cf4ddb235e3e7e8161f3eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250763"
---
# Start-DscConfiguration

## SAMENVATTING
Hiermee wordt configuratie op knoop punten toegepast.

## SYNTAXIS

### ComputerNameAndPathSet (standaard)

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-JobName <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimSessionAndPathSet

```
Start-DscConfiguration [-Wait] [-Force] [[-Path] <String>] -CimSession <CimSession[]> [-ThrottleLimit <Int32>]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ComputerNameAndUseExistingSet

```
Start-DscConfiguration [-Wait] [-Force] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-UseExisting] [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionAndUseExistingSet

```
Start-DscConfiguration [-Wait] [-Force] -CimSession <CimSession[]> [-ThrottleLimit <Int32>] [-UseExisting]
 [-JobName <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Start-DscConfiguration** past configuratie toe op knoop punten.
Bij gebruik met de para meter *UseExisting* wordt de bestaande configuratie op de doel computer toegepast.
Geef op op welke computers u de configuratie wilt Toep assen door computer namen op te geven of door Common Information Model (CIM)-sessies te gebruiken.

Deze cmdlet maakt standaard een taak en retourneert een **taak** object.
Typ voor meer informatie over achtergrond taken `Get-Help about_Jobs` .
Als u deze cmdlet interactief wilt gebruiken, geeft u de *wait* -para meter op.

Geef de para meter *uitgebreid* op om details weer te geven van wat de cmdlet doet wanneer configuratie-instellingen worden toegepast.

## VOORBEELDEN

### Voor beeld 1: configuratie-instellingen Toep assen

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\"
```

Met deze opdracht worden de configuratie-instellingen van C:\DSC\Configurations\ toegepast op elke computer met instellingen in die map.
Met de opdracht worden **taak** objecten geretourneerd voor elk doel knooppunt dat is geïmplementeerd op.

### Voor beeld 2: configuratie-instellingen Toep assen en wachten tot de configuratie is voltooid

```
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -Wait -Verbose
```

Met deze opdracht wordt de configuratie van C:\DSC\Configurations\ toegepast op de lokale computer.
De opdracht retourneert **taak** objecten voor elk doel knooppunt dat is geïmplementeerd op, in dit geval alleen de lokale computer.
In dit voor beeld wordt de *uitgebreide* para meter opgegeven.
Daarom verzendt de opdracht berichten naar de console als deze wordt uitgevoerd.
De opdracht bevat de *wait* -para meter.
Daarom kunt u de-console pas gebruiken als de opdracht alle configuratie taken heeft voltooid.

### Voor beeld 3: configuratie-instellingen Toep assen met behulp van een CIM-sessie

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Start-DscConfiguration -Path "C:\DSC\Configurations\" -CimSession $Session
```

In dit voor beeld worden configuratie-instellingen toegepast op een opgegeven computer.
In het voor beeld wordt een CIM-sessie voor een computer met de naam Server01 gemaakt voor gebruik met de cmdlet.
U kunt ook een matrix met CIM-sessies maken om de cmdlet op meerdere opgegeven computers toe te passen.

Met de eerste opdracht maakt u een CIM-sessie met behulp van de cmdlet **New-CimSession** en slaat u het **CimSession** -object op in de variabele $Session.
De opdracht vraagt u om een wacht woord.
Typ `Get-Help NewCimSession` voor meer informatie.

Met de tweede opdracht worden de configuratie-instellingen van C:\DSC\Configurations\ toegepast op de computers die worden geïdentificeerd door de **CimSession** -objecten die zijn opgeslagen in de variabele $Session.
In dit voor beeld bevat de variabele $Session alleen een CIM-sessie voor de computer met de naam Server01.
De opdracht past de configuratie toe.
De opdracht maakt **taak** objecten voor elke geconfigureerde computer.

## PARAMETERS

### -CimSession
Voert de cmdlet uit in een externe sessie of op een externe computer.
Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) of [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) .
De standaard waarde is de huidige sessie op de lokale computer.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionAndPathSet, CimSessionAndUseExistingSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
Hiermee geeft u een matrix van computer namen op.
Deze para meter beperkt de computers die configuratie documenten hebben in de para meter *Path* naar die zijn opgegeven in de matrix.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
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
Parameter Sets: ComputerNameAndPathSet, ComputerNameAndUseExistingSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Hiermee wordt de configuratie bewerking gestopt die momenteel wordt uitgevoerd op de doel computer en wordt de nieuwe Start-Configuration bewerking gestart.
Als de eigenschap **RefreshMode** van de lokale Configuration Manager is ingesteld op **pull** , en als u deze para meter opgeeft, wordt deze gewijzigd in **Push**.

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

### -Path
Hiermee geeft u een bestandspad van een map met bestanden met configuratie-instellingen.
Met deze cmdlet worden deze configuratie-instellingen gepubliceerd en toegepast op computers met instellingen bestanden in het opgegeven pad.
Elk doel knooppunt moet een instellingen bestand hebben met de volgende indeling: NetBIOS name. mof.

```yaml
Type: System.String
Parameter Sets: ComputerNameAndPathSet, CimSessionAndPathSet
Aliases:

Required: False
Position: 0
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

### -UseExisting
Geeft aan dat met deze cmdlet de bestaande configuratie wordt toegepast.
De configuratie kan bestaan op de doel computer met behulp van de cmdlet **Start-DscConfiguration** of op basis van de Publish-DscConfiguration

Lees de informatie in [What's New in Windows Power shell 5,0](/powershell/scripting/whats-new/what-s-new-in-windows-powershell-50) voordat u deze para meter voor deze cmdlet opgeeft.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerNameAndUseExistingSet, CimSessionAndUseExistingSet
Aliases:

Required: True
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

[Overzicht van desired state Configuration voor Windows Power shell](/powershell/scripting/dsc/overview/overview)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Stop-DscConfiguration](Stop-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)

[Update-DscConfiguration](Update-DscConfiguration.md)
