---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: 8d99f861a9cbdc72d30975275c49c6cd5bde2bed
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249789"
---
# Export-ModuleMember

## SAMENVATTING
Hiermee geeft u de module leden op die worden geëxporteerd.

## SYNTAXIS

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## BESCHRIJVING

De cmdlet **export-ModuleMember** geeft de module leden op die worden geëxporteerd uit een script module bestand (. psm1) of van een dynamische module die is gemaakt met behulp van de cmdlet New-Module.
Module leden bevatten cmdlets, functies, variabelen en aliassen.
Deze cmdlet kan alleen worden gebruikt in een script module bestand of een dynamische module.

Als een script module geen opdracht **export-ModuleMember** bevat, worden de functies en aliassen in de script module geëxporteerd, maar de variabelen niet.
Wanneer een script module **export-ModuleMember** opdrachten bevat, worden alleen de leden geëxporteerd die zijn opgegeven in de **export-ModuleMember-** opdrachten.
U kunt ook **exporteren-ModuleMember** gebruiken om leden te onderdrukken of te exporteren die de script module uit andere modules importeert.

Een **export-ModuleMember-** opdracht is optioneel, maar het is een Best Practice.
Zelfs als met de opdracht de standaard waarden worden bevestigd, wordt de bedoeling van de module Auteur gedemonstreerd.

## VOORBEELDEN

### Voor beeld 1: functies en aliassen exporteren in een script module

```powershell
Export-ModuleMember -Function * -Alias *
```

Met deze opdracht worden alle functies en aliassen die in de script module zijn gedefinieerd, geëxporteerd.

### Voor beeld 2: specifieke aliassen en functies exporteren

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

Met deze opdracht worden drie aliassen en drie functies die in de script module zijn gedefinieerd, geëxporteerd.

U kunt deze opdracht indeling gebruiken om de namen van module leden op te geven.

### Voor beeld 3: geen leden exporteren

```powershell
Export-ModuleMember
```

Met deze opdracht geeft u op dat er geen leden die zijn gedefinieerd in de script module, worden geëxporteerd.

Met deze opdracht voor komt u dat de module leden worden geëxporteerd, maar niet de leden verbergen.
Gebruikers kunnen module leden lezen en kopiëren of de aanroep operator (&) gebruiken om module leden aan te roepen die niet worden geëxporteerd.

### Voor beeld 4: een specifieke variabele exporteren

```powershell
Export-ModuleMember -Variable increment
```

Met deze opdracht wordt alleen de variabele $increment van de script module geëxporteerd.
Er zijn geen andere leden geëxporteerd.

Als u een variabele wilt exporteren, naast het exporteren van de functies in een module, moet de opdracht **export-ModuleMember** de namen bevatten van alle functies en de naam van de variabele.

### Voor beeld 5: meerdere opdrachten voor exporteren

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

Deze opdrachten laten zien hoe meerdere opdrachten voor **exporteren ModuleMember** worden geïnterpreteerd in een script module bestand (. psm1).

Met deze opdrachten worden drie functies en één alias gemaakt en vervolgens worden twee van de functies en de alias geëxporteerd.

Zonder de **export-ModuleMember-** opdrachten, worden alle drie de functies en de alias geëxporteerd.
Met de opdracht **export-ModuleMember** worden alleen de functies **New-test** en **Start-test** en de STT-alias geëxporteerd.

### Voor beeld 6: leden exporteren in een dynamische module

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

Met deze opdracht wordt uitgelegd hoe u Export-ModuleMember gebruikt in een dynamische module die is gemaakt met behulp van de cmdlet **New-module** .

In dit voor beeld wordt **export-ModuleMember** gebruikt om zowel de Hi-alias als de functie **SayHello** in de dynamische module te exporteren.

### Voor beeld 7: een functie declareren en exporteren in één opdracht

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

Dit voor beeld bevat een functie met de naam **export** die een functie declareert of een variabele maakt, en schrijft vervolgens een `Export-ModuleMember` opdracht voor de functie of variabele.
Hiermee kunt u een functie of variabele declareren en exporteren in één opdracht.

Als u de functie **exporteren** wilt gebruiken, neemt u deze op in de script module.
Als u een functie wilt exporteren, typt u `Export` voor het gereserveerde woord **Function** .

Als u een variabele wilt exporteren, gebruikt u de volgende indeling om de variabele te declareren en de waarde ervan in te stellen:

`Export variable <variable-name> <value>`

Met de opdrachten in het voor beeld wordt de juiste indeling weer gegeven.
In dit voor beeld worden alleen de functie **New-test** en de variabele $interval geëxporteerd.

## PARAMETERS

### -Alias

Hiermee geeft u de aliassen op die uit het script module bestand worden geëxporteerd.
Voer de alias namen in.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Cmdlet

Hiermee geeft u de cmdlets op die uit het script module bestand worden geëxporteerd.
Voer de namen van de cmdlets in.
Joker tekens zijn toegestaan.

U kunt geen cmdlets maken in een script module-bestand, maar met cmdlets van een binaire module naar een script module, en deze opnieuw exporteren vanuit de script module.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Functie

Hiermee geeft u de functies op die uit het script module bestand worden geëxporteerd.
Voer de namen van de functies in.
Joker tekens zijn toegestaan.
U kunt ook de functie naam teken reeksen van de sluis naar **export-ModuleMember**.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Variabele

Hiermee geeft u de variabelen op die uit het script module bestand worden geëxporteerd.
Voer de namen van de variabelen in, zonder een dollar teken.
Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt de functie naam reeksen naar deze cmdlet pipeen.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* Als u een lid wilt uitsluiten van de lijst met geëxporteerde leden, voegt u een opdracht **export-ModuleMember** toe met een lijst met alle andere leden, maar laat u het lid dat u wilt uitsluiten.

## GERELATEERDE KOPPELINGEN

[Get-module](Get-Module.md)

[Import-module](Import-Module.md)

[Remove-module](Remove-Module.md)
