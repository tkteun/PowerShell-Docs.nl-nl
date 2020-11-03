---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: 8f4dc173ff95476c4e2cb91e24d30afdd8a31697
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250185"
---
# Join-String

## SAMENVATTING
Hiermee worden objecten van de pijp lijn gecombineerd tot één teken reeks.

## SYNTAXIS

### Standaard (standaard instelling)

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### SingleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### DoubleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### Indeling

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## BESCHRIJVING

De `Join-String` cmdlet voegt tekst van pijplijn objecten samen tot één teken reeks.

Als er geen para meters zijn opgegeven, worden de pijplijn objecten geconverteerd naar een teken reeks en samengevoegd met het standaard scheidings teken `$OFS` .

Als u een eigenschaps naam opgeeft, wordt de waarde van de eigenschap geconverteerd naar een teken reeks en samengevoegd in een teken reeks.

In plaats van een eigenschaps naam kan een script blok worden gebruikt. Het resultaat van het script blok wordt geconverteerd naar een teken reeks voordat deze is gekoppeld aan het formulier resultaat. De tekst van de eigenschap van een object kan worden gecombineerd of het resultaat van het object dat is geconverteerd naar een teken reeks.

Deze cmdlet is geïntroduceerd in Power shell 6,2.

## VOORBEELDEN

### Voor beeld 1: mapnamen toevoegen

<!-- markdownlint-disable MD038 -->
In dit voor beeld worden mapnamen toegevoegd, wordt de uitvoer tussen dubbele aanhalings tekens geplaatst en worden de mapnamen gescheiden door een komma en een spatie ( `, ` ). De uitvoer is een teken reeks object.

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

`Get-ChildItem` gebruikt de **Directory** -para meter om alle mapnamen voor het station op te halen `C:\` .
De objecten worden naar beneden verzonden in de pijp lijn `Join-String` . De **eigenschap** para meter geeft de mapnamen aan. De **doublequote** para meter plaatst de mapnamen met dubbele aanhalings tekens.
De **scheidings** parameter geeft aan dat er een komma en spatie ( `, ` ) worden gebruikt om de mapnamen van elkaar te scheiden.

De `Get-ChildItem` objecten zijn **System. io. DirectoryInfo** en `Join-String` converteren de objecten naar **System. String**.

### Voor beeld 2: een eigenschaps subtekenreeks gebruiken om lid te worden van mapnamen

In dit voor beeld wordt een subtekenreeks methode gebruikt om de eerste vier letters van mapnamen op te halen, wordt de uitvoer in enkele aanhalings tekens geplaatst en worden de mapnamen gescheiden met een punt komma ( `;` ).

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

`Get-ChildItem` gebruikt de **Directory** -para meter om alle mapnamen voor het station op te halen `C:\` .
De objecten worden naar beneden verzonden in de pijp lijn `Join-String` .

De **eigenschap** para meter script Block gebruikt automatische variabele ( `$_` ) om de eigenschap **name** van elk object te specificeren. De subtekenreeks haalt de eerste vier letters van elke mapnaam op. De subtekenreeks geeft de begin-en eind positie van het teken aan. Met de para meter **SingleQuote** worden de mapnamen met enkele aanhalings tekens gepakt. De **scheidings** parameter geeft aan dat er een punt komma ( `;` ) moet worden gebruikt om de mapnamen van elkaar te scheiden.

Zie [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) en [subtekenreeks voor](/dotnet/api/system.string.substring)meer informatie over automatische variabelen en subtekenreeksen.

### Voor beeld 3: samenvoegings uitvoer op een afzonderlijke regel weer geven

In dit voor beeld worden service namen gekoppeld aan elke service op een afzonderlijke regel en Inge sprongen door een tabblad.

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

`Get-Service` maakt gebruik van de para meter **name** om services op te geven die beginnen met `se*` . Het sterretje ( `*` ) is een Joker teken voor elk wille keurig teken.

De objecten worden naar beneden verzonden met `Join-String` behulp van de para meter **Property** om de service namen op te geven. De **scheidings** parameter geeft drie speciale tekens op die een regel terugloop ( `` `r `` ), nieuwe regel ( `` `n `` ) en tab ( `` `t `` ) vertegenwoordigen. De **OutputPrefix** voegt een label **Services in:** met een nieuwe regel en een tabblad voor de eerste uitvoer regel.

Zie [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)voor meer informatie over speciale tekens.

### Voor beeld 4: een klassedefinitie maken op basis van een object

In dit voor beeld wordt een Power shell-klassen definitie gegenereerd met behulp van een bestaand object als sjabloon.

Dit code voorbeeld maakt gebruik van splatting om de lengte van de regel te verkleinen en de Lees baarheid te verbeteren. Zie [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)voor meer informatie.

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## PARAMETERS

### -DoubleQuote

Plaatst de teken reeks waarde van elk pijplijn object in dubbele aanhalings tekens.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Formats Tring

Een indelings teken reeks die opgeeft hoe elk item moet worden opgemaakt.

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object

Hiermee geeft u de tekst op die moet worden gekoppeld. Voer een variabele in die de tekst bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald die moeten worden toegevoegd aan teken reeksen.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OutputPrefix

Tekst die wordt ingevoegd vóór de uitvoer teken reeks. De teken reeks kan speciale tekens bevatten, zoals Carriage Return ( `` `r `` ), nieuwe regel ( `` `n `` ) en tab ( `` `t `` ).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputSuffix

Tekst die wordt toegevoegd aan de uitvoer teken reeks. De teken reeks kan speciale tekens bevatten, zoals Carriage Return ( `` `r `` ), nieuwe regel ( `` `n `` ) en tab ( `` `t `` ).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Eigenschap

De naam van een eigenschap, of een eigenschaps expressie, waarmee het pijplijn object naar tekst wordt geprojecteerd.

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scheidings teken

Tekst of tekens, zoals een komma of punt komma, die tussen de tekst voor elk pijplijn object wordt ingevoegd.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SingleQuote

Plaatst de teken reeks waarde van elk pijplijn object tussen enkele aanhalings tekens.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

Maakt gebruik van het lijst scheidings teken voor de huidige cultuur als item scheidings teken. Als u het lijst scheidings teken voor een cultuur wilt zoeken, gebruikt u de volgende opdracht: `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. PSObject

## UITVOER

### System. String

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)

[Subtekenreeks](/dotnet/api/system.string.substring)

