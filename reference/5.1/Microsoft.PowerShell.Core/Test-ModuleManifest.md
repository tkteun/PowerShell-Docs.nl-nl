---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-modulemanifest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-ModuleManifest
ms.openlocfilehash: 6e05a9a8e2266422e05040f6781224744e481830
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250131"
---
# Test-ModuleManifest

## SAMENVATTING
Verifieert of een module manifest bestand nauw keurig de inhoud van een module beschrijft.

## SYNTAXIS

```
Test-ModuleManifest [-Path] <String> [<CommonParameters>]
```

## BESCHRIJVING

Met de cmdlet **test-ModuleManifest** wordt gecontroleerd of de bestanden die worden vermeld in het module manifest bestand (. psd1) zich in werkelijkheid in de opgegeven paden bevinden.

Deze cmdlet is ontworpen om module auteurs te helpen hun manifest bestanden te testen.
Module gebruikers kunnen deze cmdlet ook gebruiken in scripts en opdrachten om fouten te detecteren voordat ze scripts uitvoeren die afhankelijk zijn van de module.

**Test-ModuleManifest** retourneert een object dat de module vertegenwoordigt.
Dit is hetzelfde type object dat Get-Module retourneert.
Als bestanden zich niet op de opgegeven locaties in het manifest bevinden, genereert de cmdlet ook een fout voor elk ontbrekend bestand.

## VOORBEELDEN

### Voor beeld 1: een manifest testen

```powershell
test-ModuleManifest -Path "$pshome\Modules\TestModule.psd1"
```

Met deze opdracht wordt het module manifest TestModule.psd1 getest.

### Voor beeld 2: een manifest testen met behulp van de pijp lijn

```powershell
"$pshome\Modules\TestModule.psd1" | test-modulemanifest
```

```Output
Test-ModuleManifest : The specified type data file 'C:\Windows\System32\Wi
ndowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml' could not be processed because the file was not found. Please correct the path and try again.
At line:1 char:34
+ "$pshome\Modules\TestModule.psd1" | test-modulemanifest <<<<
+ CategoryInfo          : ResourceUnavailable: (C:\Windows\System32\WindowsPowerShell\v1.0\Modules\TestModule\TestTypes.ps1xml:String) [Test-ModuleManifest], FileNotFoundException
+ FullyQualifiedErrorId : Modules_TypeDataFileNotFound,Microsoft.PowerShell.Commands.TestModuleManifestCommandName

Name              : TestModule
Path              : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule\TestModule.psd1
Description       :
Guid              : 6f0f1387-cd25-4902-b7b4-22cff6aefa7b
Version           : 1.0
ModuleBase        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\TestModule
ModuleType        : Manifest
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {}
ExportedVariables : {}
NestedModules     : {}
```

Met deze opdracht wordt een pijplijn operator (|) gebruikt voor het verzenden van een padtekenreeks naar **test-ModuleManifest**.

De uitvoer van de opdracht geeft aan dat de test is mislukt, omdat het TestTypes.ps1XML-bestand, dat in het manifest is vermeld, niet is gevonden.

### Voor beeld 3: een functie schrijven om een module manifest te testen

```powershell
function Test-ManifestBool ($path)
```

```Output
{$a = dir $path | Test-ModuleManifest -ErrorAction SilentlyContinue; $?}
```

Deze functie is vergelijkbaar met **test-ModuleManifest** , maar retourneert een Booleaanse waarde.
De functie retourneert $True als het manifest is door gegeven aan de test en $False anderszins.

De functie maakt gebruik van de Get-ChildItem cmdlet, alias = dir, om het module manifest op te halen dat is opgegeven door de $path-variabele.
De opdracht maakt gebruik van een pijplijn operator (|) om het File-object door te geven aan **test-ModuleManifest**.

**Test-ModuleManifest** gebruikt de gemeen schappelijke para meter *Error Action* met de waarde SilentlyContinue om de weer gave te onderdrukken van fouten die door de opdracht worden gegenereerd.
Ook wordt het **PSModuleInfo** -object opgeslagen dat door **test-ModuleManifest** wordt geretourneerd in de variabele $a.
Daarom wordt het object niet weer gegeven.

Vervolgens wordt in een afzonderlijke opdracht de waarde van de $? weer gegeven.
Automatische variabele.
Als er geen fout wordt gegenereerd door de vorige opdracht, wordt de opdracht $True weer gegeven en $False anders.

U kunt deze functie gebruiken in voorwaardelijke instructies, zoals die voor een opdracht van een **import module** of een opdracht die gebruikmaakt van de module.

## PARAMETERS

### -Path

Hiermee geeft u een pad en een bestands naam op voor het manifest bestand.
Voer een optioneel pad en de naam in van het manifest bestand van de module met de bestandsnaam extensie. psd1.
De standaard locatie is de huidige map.
Joker tekens worden ondersteund, maar moeten worden omgezet in een manifest bestand met één module.
Deze parameter is vereist.
U kunt ook een pad naar **test-ModuleManifest** sluizen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt het pad naar een module manifest door sluizen naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSModuleInfo

Met deze cmdlet wordt een **PSModuleInfo** -object geretourneerd dat de module vertegenwoordigt.
Dit object wordt als resultaat gegeven, zelfs als het manifest fouten bevat.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Exporteren-ModuleMember](Export-ModuleMember.md)

[Get-module](Get-Module.md)

[Import-module](Import-Module.md)

[New-module](New-Module.md)

[New-ModuleManifest](New-ModuleManifest.md)

[Remove-module](Remove-Module.md)

[about_Modules](About/about_Modules.md)
