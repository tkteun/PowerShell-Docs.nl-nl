---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: d73d8d6a30e6b7c08b5a0b7988ea2327be34002a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250769"
---
# Invoke-DscResource

## SAMENVATTING
Hiermee wordt een methode van een opgegeven DSC-resource uitgevoerd.

## SYNTAXIS

```
Invoke-DscResource [-Name] <String> [-Method] <String> -ModuleName <ModuleSpecification> -Property <Hashtable>
 [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **invoke-dscresource bieden** wordt een methode uitgevoerd van een opgegeven Windows Power shell-resource voor desired state Configuration (DSC).
Voordat u deze cmdlet uitvoert, stelt u de vernieuwings modus van de lokale Configuration Manager (LCM) in op uitgeschakeld.

Met deze cmdlet wordt een DSC-resource rechtstreeks aangeroepen zonder dat er een configuratie document wordt gemaakt.
Met deze cmdlet kunnen Configuration Management-producten Windows beheren met behulp van DSC-resources.
Met deze cmdlet wordt ook fout opsporing van resources mogelijk wanneer de DSC-Engine of de LCM wordt uitgevoerd met de fout opsporing is ingeschakeld.

## VOORBEELDEN

### Voor beeld 1: de set-methode van een bron aanroepen door de verplichte eigenschappen op te geven

```
PS C:\> Invoke-DscResource -Name Log -Method Set -Property @{Message = 'Hello World'} -ModuleName PSDesiredStateConfiguration
```

Met deze opdracht wordt de **set** -methode aangeroepen van een resource met de naam log en wordt er een **bericht** eigenschap voor opgegeven.

### Voor beeld 2: de test methode van een resource aanroepen voor een opgegeven module

```
PS C:\> Invoke-DscResource -Name WindowsProcess -Method Test -Property @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''} -ModuleName PSDesiredStateConfiguration
```

Met deze opdracht wordt de **test** methode aangeroepen van een resource met de naam WindowsProcess, die zich in de module met de naam PSDesiredStateConfiguration bevindt.

## PARAMETERS

### -Methode
Hiermee geeft u de methode van de resource op die door deze cmdlet wordt aangeroepen. De acceptabele waarden voor deze para meter zijn: Get, set en test.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Module naam
Hiermee geeft u de naam van de module op waaruit deze cmdlet de opgegeven resource aanroept.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name
Hiermee geeft u de naam op van de DSC-resource die moet worden gestart.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Eigenschap
Hiermee geeft u de naam van de resource eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde. Gebruik de cmdlet **Get-dscresource bieden** om de bron eigenschappen en hun typen te detecteren.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

### Micro soft. Management. Infrastructure. CimInstance, System. Boolean

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Overzicht van desired state Configuration voor Windows Power shell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Get-Dscresource bieden](Get-DscResource.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Set-DscLocalConfigurationManager](Set-DscLocalConfigurationManager.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
