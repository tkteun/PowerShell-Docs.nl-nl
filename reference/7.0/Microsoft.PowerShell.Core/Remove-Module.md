---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: b8577db1d44f0e7bd4571a080133fecaa282770b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249559"
---
# Remove-Module

## SAMENVATTING
Verwijdert modules uit de huidige sessie.

## SYNTAXIS

### name

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FullyQualifiedName

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModuleInfo

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **Remove-module** worden de leden van een module, zoals cmdlets en functions, verwijderd uit de huidige sessie.

Als de module een assembly (. dll) bevat, worden alle leden die door de assembly zijn geïmplementeerd, verwijderd, maar wordt de assembly niet uit het geheugen geladen.

Met deze cmdlet wordt de module niet verwijderd of verwijderd van de computer.
Dit is alleen van invloed op de huidige Power shell-sessie.

## VOORBEELDEN

### Voor beeld 1: een module verwijderen

```powershell
Remove-Module -Name "BitsTransfer"
```

Met deze opdracht wordt de BitsTransfer-module verwijderd uit de huidige sessie.

### Voor beeld 2: alle modules verwijderen

```powershell
Get-Module | Remove-Module
```

Met deze opdracht worden alle modules uit de huidige sessie verwijderd.

### Voor beeld 3: modules verwijderen met behulp van de pijp lijn

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

Met deze opdracht verwijdert u de BitsTransfer-en PSDiagnostics-modules uit de huidige sessie.

De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van de module namen naar **Remove-module**.
De *uitgebreide* algemene para meter wordt gebruikt om gedetailleerde informatie over de verwijderde leden op te halen.

De *uitgebreide* berichten tonen de items die worden verwijderd.
De berichten verschillen omdat de BitsTransfer-module een assembly bevat waarmee de cmdlets en een geneste module met een eigen assembly worden geïmplementeerd.
De PSDiagnostics-module bevat een module script bestand (. psm1) dat functies exporteert.

### Voor beeld 4: een module verwijderen met behulp van ModuleInfo

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

Met deze opdracht wordt de *ModuleInfo* -para meter gebruikt om de BitsTransfer-module te verwijderen.

## PARAMETERS

### -Force

Geeft aan dat met deze cmdlet alleen-lezen modules worden verwijderd.
Standaard verwijdert **Remove-module** alleen de modules lezen/schrijven.

De **ReadOnly** -en **readwrite** -waarden worden opgeslagen in de eigenschap **AccessMode** van een module.

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

### -FullyQualifiedName

Hiermee geeft u de volledig gekwalificeerde namen van modules op die moeten worden verwijderd.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ModuleInfo

Hiermee geeft u de module objecten die moeten worden verwijderd.
Voer een variabele in die een module object ( **PSModuleInfo** ) bevat of een opdracht waarmee een module object wordt opgehaald, zoals een Get-Module opdracht.
U kunt module-objecten ook pipeen om te **verwijderen-module**.

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de namen van de modules die u wilt verwijderen.
Joker tekens zijn toegestaan.
U kunt ook de naam van de teken reeksen van de **invoeg module verplaatsen**.

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
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

### System. String, System. Management. Automation. PSModuleInfo

U kunt module namen en module-objecten in een pipe **neerzetten** om de module te verwijderen.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

Wanneer u een module verwijdert, is er een gebeurtenis in de module die wordt uitgevoerd.
Met deze gebeurtenis kan een module reageren op het verwijderen en enige opschoning uitvoeren, zoals het vrijmaken van resources. Voorbeeld:

$OnRemoveScript = {

  \# opschonen uitvoeren

  $cachedSessions | Remove-PSSession

}

$ExecutionContext. SessionState. module. OnRemove + = $OnRemoveScript

Voor volledige consistentie is het wellicht ook handig om te reageren op het sluiten van het Power Shell-proces:

Register-EngineEvent-SourceIdentifier ([System. Management. Automation. PsEngineEvent]:: Exit)-actie $OnRemoveScript

## GERELATEERDE KOPPELINGEN

[Get-module](Get-Module.md)

[Import-module](Import-Module.md)
