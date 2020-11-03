---
external help file: Get-DSCLocalConfigurationManager.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dsclocalconfigurationmanager?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscLocalConfigurationManager
ms.openlocfilehash: 162770d8eb3a8953dcfaeb31f30742a46353b33b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250770"
---
# Get-DscLocalConfigurationManager

## SAMENVATTING

Hiermee worden de instellingen van lokale Configuration Manager (LCM) en statussen voor het knoop punt opgehaald.

## SYNTAXIS

```
Get-DscLocalConfigurationManager [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Get-DscLocalConfigurationManager` cmdlet krijgt instellingen voor de ICM, meta configuratie en de status van LCM voor het knoop punt. Geef computers op met behulp van Common Information Model (CIM)-sessies. Als u geen doel computer opgeeft, worden de configuratie-instellingen van de lokale computer opgehaald met de cmdlet.

## VOORBEELDEN

### Voor beeld 1: de ICM-instellingen voor de lokale computer ophalen

```powershell
Get-DscLocalConfigurationManager
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 47edd8c9-2798-4827-839a-b35cc87e69fb
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName
```

Met deze opdracht worden de ICM-instellingen voor de lokale computer opgehaald.

Zie de documentatie over [het configureren van de lokale Configuration Manager](../../docs-conceptual/dsc/managing-nodes/metaconfig.md#basic-settings) voor meer informatie over de afzonderlijke kenmerken van de uitvoer.

### Voor beeld 2: instellingen voor de ICM ophalen voor een opgegeven computer

```powershell
$Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
Get-DscLocalConfigurationManager -CimSession $Session
```

```Output
ActionAfterReboot              : ContinueConfiguration
AgentId                        : 169dfa57-a7f9-43be-a7a5-9dd06587e052
AllowModuleOverWrite           : False
CertificateID                  :
ConfigurationDownloadManagers  : {}
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 15
Credential                     :
DebugMode                      : {NONE}
DownloadManagerCustomData      :
DownloadManagerName            :
LCMCompatibleVersions          : {1.0, 2.0}
LCMState                       : Idle
LCMStateDetail                 :
LCMVersion                     : 2.0
StatusRetentionTimeInDays      : 10
SignatureValidationPolicy      : NONE
SignatureValidations           : {}
MaximumDownloadSizeMB          : 500
PartialConfigurations          :
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 30
RefreshMode                    : PUSH
ReportManagers                 : {}
ResourceModuleManagers         : {}
PSComputerName                 : Server01
PSComputerName                 : Server01
```

In dit voor beeld worden de ICM-instellingen opgehaald voor een computer die is opgegeven door een CIM-sessie.
In het voor beeld wordt een CIM-sessie voor een computer met de naam Server01 gemaakt voor gebruik met de cmdlet.
U kunt ook een matrix met CIM-sessies maken om de cmdlet op meerdere opgegeven computers toe te passen.

Met de eerste opdracht maakt u een CIM-sessie met behulp van de `New-CimSession` cmdlet. vervolgens slaat u het **CimSession** -object op in de variabele $Session. De opdracht vraagt u om een wacht woord. Typ `Get-Help New-CimSession` voor meer informatie.

Met de tweede opdracht worden lokale Configuration Manager-instellingen opgehaald voor de computers die worden geïdentificeerd door de **CimSession** -objecten die zijn opgeslagen in de $Session-variabele. In dit geval de computer met de naam Server01.

## PARAMETERS

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

Voert de cmdlet uit in een externe sessie of op een externe computer. Voer een computer naam of een sessie object in, zoals de uitvoer van een- `New-CimSession` of- `Get-CimSession` cmdlet.

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

[Set-DscLocalConfigurationManager](Set-DscLocalConfigurationManager.md)
