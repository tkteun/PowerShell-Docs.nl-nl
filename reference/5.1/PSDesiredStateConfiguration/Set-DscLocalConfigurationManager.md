---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 04/29/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/set-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-DscLocalConfigurationManager
ms.openlocfilehash: 0d35aa56a52f0e6c17abd0e7b2707869e780324c
ms.sourcegitcommit: 0d4d3e47f6979876550591f62061096e7a568f7e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/11/2020
ms.locfileid: "93251437"
---
# Set-DscLocalConfigurationManager

## SAMENVATTING

Hiermee worden lokale Configuration Manager (LCM)-instellingen toegepast op knoop punten.

## SYNTAXIS

### ComputerNameSet (standaard)

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [[-ComputerName] <String[]>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionSet

```
Set-DscLocalConfigurationManager [-Path] <String> [-Force] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

`Set-DscLocalConfigurationManager`Met de cmdlet worden de instellingen van de LCM of meta configuratie toegepast op knoop punten. Geef computers op door computer namen op te geven of door Common Information Model (CIM)-sessies te gebruiken. Als u geen doel computer opgeeft, past de cmdlet instellingen toe op de lokale computer.

## VOORBEELDEN

### Voor beeld 1: instellingen voor de LCM Toep assen

```
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\"
```

Met deze opdracht worden de instellingen van de ICM van `C:\DSC\Configurations\` op de doel knooppunten toegepast. Nadat de instellingen zijn ontvangen, worden ze door de LCM verwerkt.

> [!WARNING]
> Als er meerdere META mof's zijn voor dezelfde computer die is opgeslagen in de opgegeven map, wordt alleen de eerste meta MOF toegepast.

### Voor beeld 2: instellingen voor de LCM Toep assen met behulp van een CIM-sessie

```
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Set-DscLocalConfigurationManager -Path "C:\DSC\Configurations\" -CimSession $Session
```

In dit voor beeld worden de instellingen van de LCM toegepast op een computer en worden de instellingen toegepast. In het voor beeld wordt een CIM-sessie voor een computer met de naam Server01 gemaakt voor gebruik met de cmdlet. U kunt ook een matrix met CIM-sessies maken om de cmdlet op meerdere opgegeven computers toe te passen.

Met de eerste opdracht maakt u een CIM-sessie met behulp van de `New-CimSession` cmdlet en slaat u vervolgens het **CimSession** -object op in de `$Session` variabele. De opdracht vraagt u om een wacht woord. Typ `Get-Help New-CimSession` voor meer informatie.

Met de tweede opdracht worden de instellingen voor de LCM van het doel knooppunt toegepast `C:\DSC\Configurations\` op de computer die wordt geïdentificeerd door de **CimSession** -objecten die zijn opgeslagen in de `$Session` variabele. In dit voor beeld `$Session` bevat de variabele alleen een CIM-sessie voor de computer met de naam Server01. Met de opdracht worden de instellingen toegepast. Nadat de instellingen zijn ontvangen, worden ze door de LCM verwerkt.

## PARAMETERS

### -CimSession

Voert de cmdlet uit in een externe sessie of op een externe computer. Voer een computer naam of een sessie object in, zoals de uitvoer van de cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) of [Get-CimSession](/powershell/module/CimCmdlets/Get-CimSession) .
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

Hiermee geeft u een matrix van computer namen op. Deze para meter beperkt de computers die meta-configuratie documenten hebben in de para meter **Path** tot die in de matrix zijn opgegeven.

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

Hiermee geeft u een gebruikers naam en wacht woord op als een **PSCredential** -object voor de doel computer. Als u een **PSCredential** -object wilt ophalen, gebruikt u de cmdlet Get-Credential. Typ `Get-Help Get-Credential` voor meer informatie.

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

### -Force

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

### -Path

Hiermee geeft u een bestandspad van een map met bestanden met configuratie-instellingen. De cmdlet publiceert en past deze instellingen van de ICM toe op computers met instellingen bestanden in het opgegeven pad. Elk doel knooppunt moet een instellingen bestand hebben met de volgende indeling: `NetBIOS Name.meta.mof` .

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

### -ThrottleLimit

Hiermee geeft u het maximum aantal gelijktijdige bewerkingen op dat kan worden ingesteld voor het uitvoeren van de cmdlet. Als deze para meter wordt wegge laten of een waarde van `0` wordt ingevoerd, wordt in Windows Power shell een optimale bandbreedte limiet voor de cmdlet berekend op basis van het aantal CIM-cmdlets dat op de computer wordt uitgevoerd. De beperkings limiet geldt alleen voor de huidige cmdlet, niet voor de sessie of voor de computer.

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

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Overzicht van desired state Configuration voor Windows Power shell](/powershell/scripting/dsc/overview/overview)

[Get-DscLocalConfigurationManager](Get-DscLocalConfigurationManager.md)
