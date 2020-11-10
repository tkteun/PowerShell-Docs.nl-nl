---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: e44cad2bab6c81de67cdd0902af5172438efa19e
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388498"
---
# Set-StrictMode

## SAMENVATTING
Hiermee worden code regels in expressies, scripts en script blokken vastgelegd en afgedwongen.

## SYNTAXIS

### Versie (standaard)

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### Aan

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## BESCHRIJVING

`Set-StrictMode`Met de cmdlet configureert u de strikte modus voor het huidige bereik en alle onderliggende bereiken, en schakelt u deze in en uit. Als de strikte modus is ingeschakeld, genereert Power shell een afsluit fout wanneer de inhoud van een expressie, script of script blok in strijd is met de basis regels voor Best Practice-code ring.

Gebruik de **versie** parameter om te bepalen welke code regels worden afgedwongen.

`Set-PSDebug -Strict` met cmdlet schakelt u de strikte modus in voor het globale bereik. `Set-StrictMode` alleen van invloed op het huidige bereik en de onderliggende bereiken. Daarom kunt u deze in een script of functie gebruiken om de instelling te overschrijven die is overgenomen van het globale bereik.

Als `Set-StrictMode` is uitgeschakeld, heeft Power shell het volgende gedrag:

- Bij niet-geïnitialiseerde variabelen wordt ervan uitgegaan dat de waarde 0 (nul) of `$Null` , afhankelijk van het type
- Verwijzingen naar niet-bestaande eigenschappen retour neren `$Null`
- De resultaten van een onjuiste functie syntaxis zijn afhankelijk van de fout voorwaarden
- Er wordt geprobeerd een waarde op te halen met een ongeldige index in een matrix `$Null`

## VOORBEELDEN

### Voor beeld 1: de strikte modus inschakelen als versie 1,0

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
The variable $a cannot be retrieved because it has not been set yet.

At line:1 char:3
+ $a <<<<  -gt 5
+ CategoryInfo          : InvalidOperation: (a:Token) [], RuntimeException
+ FullyQualifiedErrorId : VariableIsUndefined
```

Wanneer de strikte modus is ingesteld op versie 1,0, wordt geprobeerd te verwijzen naar variabelen die niet zijn geïnitialiseerd.

### Voor beeld 2: de strikte modus inschakelen als versie 2,0

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
The function or command was called like a method. Parameters should be separated by spaces,
as described in 'Get-Help about_Parameter.'
At line:1 char:4
+ add <<<< (3,4)
+ CategoryInfo          : InvalidOperation: (:) [], RuntimeException
+ FullyQualifiedErrorId : StrictModeFunctionCallWithParens
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$null -eq $string.Month
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$null -eq $string.Month
```

```Output
Property 'Month' cannot be found on this object; make sure it exists.
At line:1 char:9
+ $string. <<<< month
+ CategoryInfo          : InvalidOperation: (.:OperatorToken) [], RuntimeException
+ FullyQualifiedErrorId : PropertyNotFoundStrict
```

Met deze opdracht wordt de strikte modus ingeschakeld en wordt deze ingesteld op versie 2,0. Als gevolg hiervan retourneert Power shell een fout melding als u syntaxis van de methode gebruikt, waarbij gebruik wordt gemaakt van haakjes en komma's, voor een functie aanroep of verwijzing naar niet-geïnitialiseerde variabelen of niet-bestaande eigenschappen.

De voorbeeld uitvoer toont het effect van de strikte modus versie 2,0.

Zonder versie 2,0 Strict-modus wordt de waarde ' (3, 4) ' geïnterpreteerd als één matrix object waaraan niets is toegevoegd. Door de strikte modus versie 2,0 te gebruiken, wordt deze juist geïnterpreteerd als een fout syntaxis voor het verzenden van twee waarden.

Zonder versie 2,0 wordt de verwijzing naar de niet-bestaande eigenschap **Month** van een teken reeks alleen geretourneerd `$Null` . Door versie 2,0 te gebruiken, wordt deze correct geïnterpreteerd als een verwijzings fout.

### Voor beeld 3: de strikte modus inschakelen als versie 3,0

Als de strikte modus is ingesteld op **uit** , is het resultaat van een ongeldige of buiten grenzende indexen Null-waarden.

```powershell
# Strict mode is off by default.
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
Index was outside the bounds of the array.
At line:1 char:1
+ $null -eq $a[2]
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
    + FullyQualifiedErrorId : System.IndexOutOfRangeException

Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
At line:1 char:1
+ $null -eq $a['abc']
+ ~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvalidCastFromStringToInteger
```

Als de strikte modus is ingesteld op versie 3 of hoger, zijn ongeldige of buiten grenzende indexen resulteren in fouten.

## PARAMETERS

### -Uit

Geeft aan dat met deze cmdlet de strikte modus voor het huidige bereik en voor alle onderliggende bereiken wordt uitgeschakeld.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Versie

Hiermee geeft u de voor waarden op die een fout veroorzaken in de strikte modus. Deze para meter accepteert een geldig Power shell-versie nummer. Een getal hoger dan 3 wordt als **laatste** beschouwd.

De ingangs waarden voor deze para meter zijn:

- 1.0
  - Verbiedt verwijzingen naar niet-geïnitialiseerde variabelen, met uitzonde ring van niet-geïnitialiseerde variabelen in teken reeksen.
- 2,0
  - Verbiedt verwijzingen naar niet-geïnitialiseerde variabelen. Dit omvat niet-geïnitialiseerde variabelen in teken reeksen.
  - Verbiedt verwijzingen naar niet-bestaande eigenschappen van een object.
  - Verbiedt functie aanroepen die gebruikmaken van de syntaxis voor het aanroepen van methoden.
- 3,0
  - Verbiedt verwijzingen naar niet-geïnitialiseerde variabelen. Dit omvat niet-geïnitialiseerde variabelen in teken reeksen.
  - Verbiedt verwijzingen naar niet-bestaande eigenschappen van een object.
  - Verbiedt functie aanroepen die gebruikmaken van de syntaxis voor het aanroepen van methoden.
  - Geen grenzen of onherleidbare matrix indexen.
- Laatste
  - Hiermee selecteert u de meest recente versie die beschikbaar is. De meest recente versie is de meest strikte. Gebruik deze waarde om ervoor te zorgen dat scripts de striktst beschik bare versie gebruiken, zelfs wanneer er nieuwe versies worden toegevoegd aan Power shell.

> [!CAUTION]
> Het gebruik van een **nieuwste** **versie** in scripts. De betekenis van de **laatste** wijziging kan worden gewijzigd in nieuwe releases van Power shell. Daarom is voor een script dat is geschreven voor een oudere versie van Power shell die wordt gebruikt, `Set-StrictMode -Version Latest` onderhevig aan meer beperkende regels wanneer ze in een nieuwere versie van Power shell worden uitgevoerd.

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Geen

Met deze cmdlet wordt geen uitvoer geretourneerd.

## OPMERKINGEN

`Set-StrictMode` is alleen effectief in het bereik waarin het is ingesteld en in het onderliggende bereik. Zie [about_Scopes](about/about_Scopes.md)voor meer informatie over bereiken in Power shell.

## GERELATEERDE KOPPELINGEN

[Set-PSDebug](Set-PSDebug.md)
