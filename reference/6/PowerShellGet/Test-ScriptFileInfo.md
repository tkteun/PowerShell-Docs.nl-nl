---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/test-scriptfileinfo?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ScriptFileInfo
ms.openlocfilehash: c773b247d5f0da4071517134b7187ba674bfbfbd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251077"
---
# Test-ScriptFileInfo

## SAMENVATTING
Hiermee wordt een opmerkingen blok voor een script gevalideerd.

## SYNTAXIS

### PathParameterSet (standaard)

```
Test-ScriptFileInfo [-Path] <String> [<CommonParameters>]
```

### LiteralPathParameterSet

```
Test-ScriptFileInfo -LiteralPath <String> [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **test-ScriptFileInfo** valideert het opmerkingen blok aan het begin van een script dat wordt gepubliceerd met de cmdlet Publish-Script.
Als er een fout is opgetreden in het blok met opmerkingen, retourneert deze cmdlet informatie over waar de fout zich bevindt of hoe deze moet worden gecorrigeerd.

## VOORBEELDEN

### Voor beeld 1: een script bestand testen

```
PS C:\> Test-ScriptFileInfo -Path "C:\temp\temp_scripts\New-ScriptFile.ps1"
Version    Name                      Author               Description
-------    ----                      ------               -----------
1.0        New-ScriptFile            pattif               my new script file test
```

Met deze opdracht wordt het New-ScriptFile.ps1-script bestand getest en worden de resultaten weer gegeven.
Het script bestand bevat geldige meta gegevens.

### Voor beeld 2: een script bestand met waarden voor alle eigenschappen van meta gegevens testen

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Test-Runbook.ps1" | Format-List *
Name                       : Test-Runbook
Path                       : D:\code\Test-Runbook.ps1
ScriptBase                 : D:\code
ReleaseNotes               : {contoso script now supports following features, Feature 1, Feature 2, Feature 3...}
Version                    : 1.0
Guid                       : eb246b19-17da-4392-8c89-7c280f69ad0e
Author                     : pattif
CompanyName                : Microsoft Corporation
Copyright                  : 2015 Microsoft Corporation. All rights reserved.
Tags                       : {Tag1, Tag2, Tag3}
LicenseUri                 : https://contoso.com/License
ProjectUri                 : https://contoso.com/
IconUri                    : https://contoso.com/MyScriptIcon
ExternalModuleDependencies : ExternalModule1
RequiredScripts            : {Start-WFContosoServer, Stop-ContosoServerScript}
ExternalScriptDependencies : Stop-ContosoServerScript
Description                : Contoso Script example
RequiredModules            : {RequiredModule1, @{ ModuleName = 'RequiredModule2'; ModuleVersion = '1.0' }, @{ ModuleName = 'RequiredModule3'; RequiredVersion = '2.0' }, ExternalModule1}
ExportedCommands           : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-Workflow...}
ExportedFunctions          : {Test-WebUri, ValidateAndAdd-PSScriptInfoEntry, Get-PSScriptInfo, My-AdvPSCmdlet}
ExportedWorkflows          : My-Workflow
```

Met deze opdracht wordt het script bestand getest Test-Runbook.ps1 en wordt de pijplijn operator gebruikt om de resultaten door te geven aan de Format-List cmdlet om de resultaten op te maken.

### Voor beeld 3: een script bestand testen dat geen meta gegevens bevat

```
PS C:\> Test-ScriptFileInfo -Path "D:\code\Hello-World.ps1"
Test-ScriptFileInfo : Script 'D:\code\Hello-World.ps1' is missing required metadata properties. Verify that the script file has Version, Description
and Author properties. You can use the Update-ScriptFileInfo or New-ScriptFileInfo cmdlet to add or update the PSScriptInfo to the script file.
At line:1 char:1
+ Test-ScriptFileInfo D:\code\Hello-World.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidArgument: (D:\code\Hello-World.ps1:String) [Test-ScriptFileInfo], ArgumentException

+ FullyQualifiedErrorId : MissingRequiredPSScriptInfoProperties,Test-ScriptFile
```

Met deze opdracht wordt het script bestand getest Hello-World.ps1, waaraan geen meta gegevens zijn gekoppeld.

## PARAMETERS

### -LiteralPath

Hiermee geeft u een pad naar een of meer locaties.
In tegens telling tot de para meter *Path* wordt de waarde van de para meter *LiteralPath* exact gebruikt wanneer deze wordt ingevoerd.
Geen tekens worden geïnterpreteerd als joker tekens.
Als het pad escape tekens bevat, plaatst u deze tussen enkele aanhalings tekens.
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

```yaml
Type: System.String
Parameter Sets: LiteralPathParameterSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Hiermee geeft u een pad naar een of meer locaties.
Joker tekens zijn toegestaan.
De standaard locatie is de huidige map (.).

```yaml
Type: System.String
Parameter Sets: PathParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

## UITVOER

### System. object

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[New-ScriptFileInfo](New-ScriptFileInfo.md)

[Publish-Script](Publish-Script.md)

[Update-ScriptFileInfo](Update-ScriptFileInfo.md)
