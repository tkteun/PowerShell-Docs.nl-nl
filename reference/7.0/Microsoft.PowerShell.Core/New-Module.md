---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Module
ms.openlocfilehash: a0d0e31e9010c5ee119b4fbe5f6a877ebc4dc1d3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249774"
---
# New-Module

## SAMENVATTING
Hiermee maakt u een nieuwe dynamische module die alleen in het geheugen bestaat.

## SYNTAXIS

### Script Block (standaard)

```
New-Module [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>] [-ReturnResult]
 [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### Naam

```
New-Module [-Name] <String> [-ScriptBlock] <ScriptBlock> [-Function <String[]>] [-Cmdlet <String[]>]
 [-ReturnResult] [-AsCustomObject] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## BESCHRIJVING

`New-Module`Met de cmdlet wordt een dynamische module gemaakt op basis van een script blok. De leden van de dynamische module, zoals functies en variabelen, zijn onmiddellijk beschikbaar in de sessie en blijven beschikbaar totdat u de sessie sluit.

Net als statische modules worden standaard de cmdlets en functies in een dynamische module geëxporteerd en de variabelen en aliassen niet. U kunt echter de Export-ModuleMember-cmdlet en de para meters van gebruiken `New-Module` om de standaard instellingen te overschrijven.

U kunt ook de para meter **AsCustomObject** van gebruiken `New-Module` om de dynamische module als een aangepast object te retour neren. De leden van de modules, zoals functions, worden geïmplementeerd als script methoden van het aangepaste object in plaats van in de sessie te worden geïmporteerd.

Dynamische modules bestaan alleen in het geheugen, niet op schijf. Net als alle modules worden de leden van dynamische modules uitgevoerd in een persoonlijk module bereik dat een onderliggend element is van het globale bereik. Get-Module kan geen dynamische module ophalen, maar Get-Command kan de geëxporteerde leden ophalen.

Als u een dynamische module beschikbaar wilt maken voor `Get-Module` , pipet u een `New-Module` opdracht naar import-module of pipet u het module-object dat `New-Module` retourneert naar `Import-Module` . Met deze actie wordt de dynamische module aan de `Get-Module` lijst toegevoegd, maar wordt de module niet op schijf opgeslagen of kan deze permanent worden gemaakt.

## VOORBEELDEN

### Voor beeld 1: een dynamische module maken

In dit voor beeld wordt een nieuwe dynamische module gemaakt met een functie met de naam `Hello` . De opdracht retourneert een module-object dat de nieuwe dynamische module vertegenwoordigt.

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

### Voor beeld 2: werken met dynamische modules en Get-Module en Get-Command

In dit voor beeld wordt gedemonstreerd dat dynamische modules niet worden geretourneerd door de `Get-Module` cmdlet. De leden die ze exporteren, worden geretourneerd door de `Get-Command` cmdlet.

```powershell
new-module -scriptblock {function Hello {"Hello!"}}
```

```Output
Name              : __DynamicModule_2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Path              : 2ceb1d0a-990f-45e4-9fe4-89f0f6ead0e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Module

Get-Command Hello
```

```Output
CommandType     Name   Definition
-----------     ----   ----------
Function        Hello  "Hello!"
```

### Voor beeld 3: een variabele exporteren naar de huidige sessie

In dit voor beeld wordt de `Export-ModuleMember` cmdlet gebruikt om een variabele te exporteren naar de huidige sessie.
Zonder de `Export-ModuleMember` opdracht wordt alleen de functie geëxporteerd.

```powershell
New-Module -ScriptBlock {$SayHelloHelp="Type 'SayHello', a space, and a name."; function SayHello ($name) { "Hello, $name" }; Export-ModuleMember -function SayHello -Variable SayHelloHelp}
$SayHelloHelp
```

```Output
Type 'SayHello', a space, and a name.
```

```powershell
SayHello Jeffrey
```

```Output
Hello, Jeffrey
```

In de uitvoer ziet u dat zowel de variabele als de functie zijn geëxporteerd naar de sessie.

### Voor beeld 4: een dynamische module beschikbaar maken voor Get-Module

In dit voor beeld wordt gedemonstreerd dat u een dynamische module beschikbaar kunt maken voor `Get-Module` door de dynamische module te pijpleidingen naar `Import-Module` .

`New-Module` Hiermee maakt u een module object dat is gesluisd met de `Import-Module` cmdlet. De para meter **name** van `New-Module` wijst een beschrijvende naam toe aan de module. Omdat `Import-Module` er geen objecten worden geretourneerd, is er geen uitvoer van deze opdracht. `Get-Module` of de **GreetingModule** is geïmporteerd in de huidige sessie.

```powershell
New-Module -ScriptBlock {function Hello {"Hello!"}} -name GreetingModule | Import-Module
Get-Module
```

```Output
Name              : GreetingModule
Path              : d54dfdac-4531-4db2-9dec-0b4b9c57a1e5
Description       :
Guid              : 00000000-0000-0000-0000-000000000000
Version           : 0.0
ModuleBase        :
ModuleType        : Script
PrivateData       :
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Hello, Hello]}
ExportedVariables : {}
NestedModules     : {}
```

```powershell
Get-Command hello
```

```Output
CommandType     Name                                                               Definition
-----------     ----                                                               ----------
Function        Hello                                                              "Hello!"
```

De `Get-Command` cmdlet toont de `Hello` functie die de dynamische module exporteert.

### Voor beeld 5: een aangepast object met geëxporteerde functies genereren

In dit voor beeld ziet u hoe u de para meter **AsCustomObject** van gebruikt `New-Module` om een aangepast object te genereren dat script methoden heeft die de geëxporteerde functies vertegenwoordigen.

De `New-Module` cmdlet maakt een dynamische module met twee functies, `Hello` en `Goodbye` . Met de para meter **AsCustomObject** maakt u een aangepast object in plaats van het **PSModuleInfo** -object dat `New-Module` Standaard wordt gegenereerd. Dit aangepaste object wordt opgeslagen in de `$m` variabele.
De `$m` variabele lijkt geen waarde toegewezen te hebben.

```powershell
$m = New-Module -ScriptBlock {
  function Hello ($name) {"Hello, $name"}
  function Goodbye ($name) {"Goodbye, $name"}
} -AsCustomObject
$m
$m | Get-Member
```

```Output
TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
Goodbye     ScriptMethod System.Object Goodbye();
Hello       ScriptMethod System.Object Hello();
```

```powershell
$m.goodbye("Jane")
```

```Output
Goodbye, Jane
```

```powershell
$m.hello("Manoj")
```

```Output
Hello, Manoj
```

De `$m` `Get-Member` Eigenschappen en methoden van het aangepaste object worden weer gegeven in sluizen naar de cmdlet. In de uitvoer ziet u dat het object script methoden heeft die `Hello` de `Goodbye` functies en vertegenwoordigen.
Ten slotte noemen we deze script methoden en worden de resultaten weer gegeven.

### Voor beeld 6: de resultaten van het script blok ophalen

In dit voor beeld wordt de para meter **ReturnResult** gebruikt om de resultaten van het uitvoeren van het script blok op te vragen in plaats van een module object aan te vragen. Het script blok in de nieuwe module definieert de `SayHello` functie en roept vervolgens de functie aan.

```powershell
New-Module -ScriptBlock {function SayHello {"Hello, World!"}; SayHello} -ReturnResult
```

```Output
Hello, World!
```

## PARAMETERS

### -Argument List

Hiermee wordt een matrix met argumenten opgegeven die parameter waarden zijn die worden door gegeven aan het script blok. Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsCustomObject

Geeft aan dat deze cmdlet een aangepast object retourneert dat de dynamische module vertegenwoordigt. De module leden worden geïmplementeerd als script methoden van het aangepaste object, maar ze worden niet in de sessie geïmporteerd. U kunt het aangepaste object opslaan in een variabele en de punt notatie gebruiken om de leden aan te roepen.

Als de module meerdere leden met dezelfde naam heeft, zoals een functie en een variabele die beide de naam A hebben, kan slechts één lid met elke naam worden geopend vanuit het aangepaste object.

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

### -Cmdlet

Hiermee geeft u een matrix met cmdlets op die met deze cmdlet wordt geëxporteerd van de module naar de huidige sessie.
Voer een door komma's gescheiden lijst met cmdlets in. Joker tekens zijn toegestaan. Standaard worden alle cmdlets in de module geëxporteerd.

U kunt geen cmdlets definiëren in een script blok, maar een dynamische module kan cmdlets bevatten als de cmdlets uit een binaire module worden geïmporteerd.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Functie

Hiermee geeft u een matrix op met functies die met deze cmdlet worden geëxporteerd van de module naar de huidige sessie.
Voer een door komma's gescheiden lijst met functies in. Joker tekens zijn toegestaan. Standaard worden alle functies die in een module zijn gedefinieerd, geëxporteerd.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Name

Hiermee geeft u een naam op voor de nieuwe module. U kunt ook een module naam naar een nieuwe module pipeen.

De standaard waarde is een automatisch gegenereerde naam die begint met `__DynamicModule_` en wordt gevolgd door een GUID die het pad van de dynamische module opgeeft.

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ReturnResult

Geeft aan dat met deze cmdlet het script blok wordt uitgevoerd en de resultaten van het script blok worden geretourneerd in plaats van een module object te retour neren.

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

### -Script Block

Hiermee geeft u de inhoud van de dynamische module op. Plaats de inhoud tussen accolades ( `{}` ) om een script blok te maken. Deze parameter is vereist.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een module naam door sluizen naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSModuleInfo, System. Management. Automation. PSCustomObject of geen

Met deze cmdlet wordt standaard een **PSModuleInfo** -object gegenereerd. Als u de para meter **AsCustomObject** gebruikt, wordt er een **PSCustomObject** -object gegenereerd. Als u de para meter **ReturnResult** gebruikt, wordt het resultaat van het evalueren van het script blok in de dynamische module geretourneerd.

## OPMERKINGEN

U kunt ook verwijzen naar `New-Module` de alias `nmo` . Zie [about_Aliases](About/about_Aliases.md)voor meer informatie.

## GERELATEERDE KOPPELINGEN

[Exporteren-ModuleMember](Export-ModuleMember.md)

[Get-module](Get-Module.md)

[Import-module](Import-Module.md)

[Remove-module](Remove-Module.md)
