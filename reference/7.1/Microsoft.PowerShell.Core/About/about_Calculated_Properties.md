---
description: Power shell biedt de mogelijkheid om op dynamische wijze nieuwe eigenschappen toe te voegen en de opmaak van objecten uitvoer naar de pijp lijn te wijzigen.
Locale: en-US
ms.date: 08/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 1ecc621d05cb340f6792481df483249095ed63a2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252965"
---
# <a name="about-calculated-properties"></a>Berekende eigenschappen

## <a name="short-description"></a>Korte beschrijving

Power shell biedt de mogelijkheid om op dynamische wijze nieuwe eigenschappen toe te voegen en de opmaak van objecten uitvoer naar de pijp lijn te wijzigen.

## <a name="long-description"></a>Lange beschrijving

Een aantal Power shell-cmdlets transformatie, aggregatie of proces invoer objecten in uitvoer objecten met behulp van para meters die het toevoegen van nieuwe eigenschappen aan die uitvoer objecten toestaan. Deze para meters kunnen worden gebruikt om nieuwe, berekende eigenschappen voor uitvoer objecten te genereren op basis van de waarden van invoer objecten.
De berekende eigenschap wordt gedefinieerd door een [hashtabel](about_hash_tables.md) met sleutel-waardeparen waarmee de naam van de nieuwe eigenschap wordt opgegeven, een expressie voor het berekenen van de waarde en optionele indelings informatie.

## <a name="supported-cmdlets"></a>Ondersteunde cmdlets

De volgende cmdlets ondersteunen berekende eigenschaps waarden voor de **eigenschaps** parameter. De `Format-*` cmdlets ondersteunen ook berekende waarden voor de para meter **GroupBy** .

De volgende lijst specificatie de cmdlets die berekende eigenschappen ondersteunen en de sleutel-waardeparen die door elke cmdlet worden ondersteund.

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - `name`/`label` -optioneel (toegevoegd in Power shell 6. x)
  - `expression`
  - `width` -optioneel
  - `alignment` -optioneel

- `Format-Custom`
  - `expression`
  - `depth` -optioneel

- `Format-List`
  - `name`/`label` -optioneel
  - `expression`
  - `formatstring` -optioneel

  Deze zelfde set sleutel-waardeparen geldt ook voor berekende eigenschaps waarden die worden door gegeven aan de para meter **GroupBy** voor alle `Format-*` cmdlets.

- `Format-Table`
  - `name`/`label` -optioneel
  - `expression`
  - `formatstring` -optioneel
  - `width` -optioneel
  - `alignment` -optioneel

- `Format-Wide`
  - `expression`
  - `formatstring` -optioneel

- `Group-Object`
  - `expression`

- `Measure-Object`
  - Biedt alleen ondersteuning voor een script blok voor de expressie, niet voor een hashtabel.
  - Niet ondersteund in Power shell 5,1 en ouder.

- `Select-Object`
  - `name`/`label` -optioneel
  - `expression`

- `Sort-Object`
  - `expression`
  - `ascending`/`descending` -optioneel

> [!NOTE]
> De waarde van het `expression` kan een script blok in plaats van een hashtabel zijn. Zie de sectie [opmerkingen](#notes) voor meer informatie.

## <a name="hashtable-key-definitions"></a>Hashes sleutel definities

- `name`/`label` -Hiermee geeft u de naam op van de eigenschap die wordt gemaakt. U kunt `name` de alias, `label` , verwisselbaar, gebruiken.
- `expression` -Een script blok dat wordt gebruikt om de waarde van de nieuwe eigenschap te berekenen.
- `alignment` -Wordt gebruikt door cmdlets die in tabel vorm worden uitgevoerd om te definiëren hoe de waarden in een kolom worden weer gegeven. De waarde moet `'left'` , `'center'` of zijn `'right'` .
- `formatstring` -Geeft een indelings teken reeks die definieert hoe de waarde wordt opgemaakt voor uitvoer. Zie [opmaak typen in .net](/dotnet/standard/base-types/formatting-types)voor meer informatie over opmaak teken reeksen.
- `width` -Geeft de kolom maximum breedte in een tabel op wanneer de waarde wordt weer gegeven. De waarde moet groter zijn dan `0` .
- `depth` -De **Depth** -para meter van `Format-Custom` bepaalt de diepte van uitbrei ding voor alle eigenschappen. `depth`Met de sleutel kunt u de diepte van de uitbrei ding per eigenschap opgeven.
- `ascending` / `descending` -Hiermee kunt u de sorteer volgorde voor een of meer eigenschappen opgeven. Dit zijn Booleaanse waarden.

De hash-code sleutels hoeven niet te worden gespeld zolang het opgegeven naam voorvoegsel niet eenduidig is. `n`Kan bijvoorbeeld worden gebruikt in plaats van `Name` en `e` kan worden gebruikt in plaats van `Expression` .

## <a name="examples"></a>Voorbeelden

### <a name="compare-object"></a>Compare-Object

Met berekende eigenschappen kunt u bepalen hoe de eigenschappen van de invoer objecten worden vergeleken. In dit voor beeld worden de waarden in plaats van de waarden rechtstreeks te vergelijken met het resultaat van de reken kundige bewerking (modulus van 2).

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a>ConvertTo-Html

`ConvertTo-Html` een verzameling objecten kan worden geconverteerd naar een HTML-tabel.
Met berekende eigenschappen kunt u bepalen hoe de tabel wordt weer gegeven.

```powershell
Get-Alias |
  ConvertTo-Html Name,
                 Definition,
                 @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                    align='center'
                 } |
    Out-File .\aliases.htm -Force
```

In dit voor beeld wordt een HTML-tabel gemaakt met een lijst met Power shell-aliassen en de numerieke para meters voor elke opdracht met een alias. De waarden van de kolom **ParameterCount** worden gecentreerd.

### <a name="format-custom"></a>Format-Custom

`Format-Custom` biedt een aangepaste weer gave van een object in een indeling die vergelijkbaar is met de definitie van een klasse. Complexere objecten kunnen leden bevatten die diep zijn genest met complexe typen. Met de **Depth** para meter `Format-Custom` bepaalt u de diepte van uitbrei ding voor alle eigenschappen. `depth`Met de sleutel kunt u de diepte van de uitbrei ding per eigenschap opgeven.

In dit voor beeld `depth` vereenvoudigt de sleutel de aangepaste uitvoer voor de `Get-Date` cmdlet. `Get-Date` retourneert een **DateTime** -object. De eigenschap **date** van dit object is ook een **DateTime** -object, zodat het object is genest.

```powershell
Get-Date | Format-Custom @{expr={$_.Date};depth=1},TimeOfDay
```

```Output
class DateTime
{
  $_.Date =
    class DateTime
    {
      Date = 8/7/2020 12:00:00 AM
      Day = 7
      DayOfWeek = Friday
      DayOfYear = 220
      Hour = 0
      Kind = Local
      Millisecond = 0
      Minute = 0
      Month = 8
      Second = 0
      Ticks = 637323552000000000
      TimeOfDay = 00:00:00
      Year = 2020
      DateTime = Friday, August 07, 2020 12:00:00 AM
    }
  TimeOfDay =
    class TimeSpan
    {
      Ticks = 435031592302
      Days = 0
      Hours = 12
      Milliseconds = 159
      Minutes = 5
      Seconds = 3
      TotalDays = 0.503508787386574
      TotalHours = 12.0842108972778
      TotalMilliseconds = 43503159.2302
      TotalMinutes = 725.052653836667
      TotalSeconds = 43503.1592302
    }
}
```

### <a name="format-list"></a>Format-List

In dit voor beeld gebruiken we berekende eigenschappen voor het wijzigen van de naam en de indeling van de uitvoer van `Get-ChildItem` .

```powershell
Get-ChildItem *.json -File |
  Format-List Fullname,
              @{
                 name='Modified'
                 expression={$_.LastWriteTime}
                 formatstring='O'
              },
              @{
                 name='Size'
                 expression={$_.Length/1KB}
                 formatstring='N2'
              }
```

```Output
FullName : C:\Git\PS-Docs\PowerShell-Docs\.markdownlint.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.40

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.publish.config.json
Modified : 2020-07-23T10:26:28.4092457-07:00
Size     : 2.25

FullName : C:\Git\PS-Docs\PowerShell-Docs\.openpublishing.redirection.json
Modified : 2020-07-27T13:05:24.3887629-07:00
Size     : 324.60
```

### <a name="format-table"></a>Format-Table

In dit voor beeld voegt de berekende eigenschap een eigenschap **type** toe die wordt gebruikt om de bestanden te classificeren op basis van het inhouds type.

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Format-Table Name, Length -GroupBy @{
      name='Type'
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
   Type: Metacontent

Name              Length
----              ------
ThirdPartyNotices   1229
LICENSE-CODE        1106
LICENSE            19047

   Type: Configuration

Name                                Length
----                                ------
.editorconfig                          183
.gitattributes                         419
.gitignore                             228
.markdownlint.json                    2456
.openpublishing.publish.config.json   2306
.openpublishing.redirection.json    332394
.localization-config                   232

   Type: Content

Name            Length
----            ------
README.md         3355
CONTRIBUTING.md    247

   Type: Automation

Name                      Length
----                      ------
.openpublishing.build.ps1    796
build.ps1                   7495
ci.yml                       645
ci-steps.yml                2035
daily.yml                   1271
```

### <a name="format-wide"></a>Format-Wide

`Format-Wide`Met de cmdlet kunt u de waarde van één eigenschap voor objecten in een verzameling weer geven als een lijst met meerdere kolommen.

Voor dit voor beeld willen we de bestands naam en de grootte (in kilo bytes) als een brede lijst zien. Omdat `Format-Wide` er niet meer dan één eigenschap wordt weer gegeven, gebruiken we een berekende eigenschap om de waarde van twee eigenschappen te combi neren in één waarde.

```powershell
Get-ChildItem -File |
  Format-Wide -Property @{e={'{0} ({1:N2}kb)' -f $_.name,($_.length/1kb)}}
```

```Output
.editorconfig (0.18kb)                          .gitattributes (0.41kb)
.gitignore (0.22kb)                             .localization-config (0.23kb)
.markdownlint.json (2.40kb)                     .openpublishing.build.ps1 (0.78kb)
.openpublishing.publish.config.json (2.25kb)    .openpublishing.redirection.json (324.60kb)
build.ps1 (7.32kb)                              ci.yml (0.63kb)
ci-steps.yml (1.99kb)                           CONTRIBUTING.md (0.24kb)
daily.yml (1.24kb)                              LICENSE (18.60kb)
LICENSE-CODE (1.08kb)                           README.md (3.28kb)
ThirdPartyNotices (1.20kb)
```

### <a name="group-object"></a>Group-Object

De `Group-Object` cmdlet geeft objecten weer in groepen op basis van de waarde van een opgegeven eigenschap. In dit voor beeld telt de berekende eigenschap het aantal bestanden van elk inhouds type.

```powershell
Get-ChildItem -File |
  Sort-Object extension |
    Group-Object -NoElement -Property @{
      expression={
        switch ($_.extension) {
          '.md'   {'Content'}
          ''      {'Metacontent'}
          '.ps1'  {'Automation'}
          '.yml'  {'Automation'}
          default {'Configuration'}
        }
      }
    }
```

```Output
Count Name
----- ----
    5 Automation
    7 Configuration
    2 Content
    3 Metacontent
```

### <a name="measure-object"></a>Measure-Object

De `Measure-Object` cmdlet berekent de numerieke eigenschappen van de objecten. In dit voor beeld gebruiken we een berekende eigenschap om het aantal ( **som** ) van de getallen te verkrijgen, tussen 1 en 10, die deelbaar zijn door 3.

```powershell
1..10 | Measure-Object -Property {($_ % 3) -eq 0} -Sum
```

```Output
Count             : 10
Average           :
Sum               : 3
Maximum           :
Minimum           :
StandardDeviation :
Property          : ($_ % 3) -eq 0
```

> [!NOTE]
> In tegens telling tot de andere cmdlets `Measure-Object` accepteert geen hashtabel voor berekende eigenschappen. U moet een script blok gebruiken.

### <a name="select-object"></a>Select-Object

U kunt berekende eigenschappen gebruiken om extra leden toe te voegen aan de objecten uitvoer met de `Select-Object` cmdlet. In dit voor beeld geven we de Power shell-aliassen weer die met de letter beginnen `C` . Met `Select-Object` worden de alias, de cmdlet waaraan deze is toegewezen, en een telling voor het aantal gedefinieerde para meters voor de cmdlet uitgevoerd. U kunt de eigenschap **ParameterCount** maken met behulp van een berekende eigenschap.

```powershell
$aliases = Get-Alias c* |
  Select-Object Name,
                Definition,
                @{
                    name='ParameterCount'
                    expr={$_.Parameters.Keys.Count}
                }
$aliases | Get-Member
$aliases
```

```Output
   TypeName: Selected.System.Management.Automation.AliasInfo

Name           MemberType   Definition
----           ----------   ----------
Equals         Method       bool Equals(System.Object obj)
GetHashCode    Method       int GetHashCode()
GetType        Method       type GetType()
ToString       Method       string ToString()
Definition     NoteProperty string Definition=Get-Content
Name           NoteProperty string Name=cat
ParameterCount NoteProperty System.Int32 ParameterCount=21

Name    Definition         ParameterCount
----    ----------         --------------
cat     Get-Content                    21
cd      Set-Location                   15
cdd     Push-MyLocation                 1
chdir   Set-Location                   15
clc     Clear-Content                  20
clear   Clear-Host                      0
clhy    Clear-History                  17
cli     Clear-Item                     20
clp     Clear-ItemProperty             22
cls     Clear-Host                      0
clv     Clear-Variable                 19
cnsn    Connect-PSSession              29
compare Compare-Object                 20
copy    Copy-Item                      24
cp      Copy-Item                      24
cpi     Copy-Item                      24
cpp     Copy-ItemProperty              23
cvpa    Convert-Path                   13
```

### <a name="sort-object"></a>Sort-Object

Met behulp van de berekende eigenschappen kunt u gegevens in verschillende orders per eigenschap sorteren. In dit voor beeld worden gegevens uit een CSV-bestand in oplopende volg orde gesorteerd op **datum**. Maar binnen elke datum worden de rijen in aflopende volg orde gesorteerd op **VerkochteEenheden**.

```powershell
Import-Csv C:\temp\sales-data.csv |
  Sort-Object Date, @{expr={$_.UnitsSold}; desc=$true}, Salesperson  |
    Select-Object Date, Salesperson, UnitsSold
```

```Output
Date       Salesperson UnitsSold
----       ----------- ---------
2020-08-01 Sally       3
2020-08-01 Anne        2
2020-08-01 Fred        1
2020-08-02 Anne        6
2020-08-02 Fred        2
2020-08-02 Sally       0
2020-08-03 Anne        5
2020-08-03 Sally       3
2020-08-03 Fred        1
2020-08-04 Anne        2
2020-08-04 Fred        2
2020-08-04 Sally       2
```

## <a name="notes"></a>Opmerkingen

- U kunt het Expression-script blok _rechtstreeks_ als een argument opgeven, in plaats van deze op te geven als de `Expression` vermelding in een hashtabel. Bijvoorbeeld:

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  Dit voor beeld is handig voor cmdlets die geen ondersteuning vereisen voor een eigenschap via de `Name` sleutel, zoals `Sort-Object` , `Group-Object` , en `Measure-Object` .

  Voor cmdlets die de naam van de eigenschap ondersteunen, wordt het script blok geconverteerd naar een teken reeks en gebruikt als de naam van de eigenschap in de uitvoer.

- `Expression` script blokken worden uitgevoerd in _onderliggende_ bereiken, wat betekent dat de variabelen van de beller niet rechtstreeks kunnen worden gewijzigd.

- Pijplijn logica wordt toegepast op de uitvoer van `Expression` script blokken. Dit betekent dat het uitvoeren van een single-element matrix ertoe leidt dat de matrix onverpakt wordt.

- Voor de meeste cmdlets worden fouten in Expression-script blokken op de achtergrond genegeerd.
  Voor `Sort-Object` is de instructie-Terminate en script-Terminate-fouten _uitvoer_ , maar de instructie wordt niet beëindigd.

## <a name="see-also"></a>Zie ook

[about_Hash_Tables](about_hash_tables.md)

[Compare-object](xref:Microsoft.PowerShell.Utility.Compare-Object)

[ConvertTo-Html](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[Format-Custom](xref:Microsoft.PowerShell.Utility.Format-Custom)

[Format-List](xref:Microsoft.PowerShell.Utility.Format-List)

[Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)

[Format-Wide](xref:Microsoft.PowerShell.Utility.Format-Wide)

[Groep-object](xref:Microsoft.PowerShell.Utility.Group-Object)

[Meting object](xref:Microsoft.PowerShell.Utility.Measure-Object)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

[Sorteer object](xref:Microsoft.PowerShell.Utility.Sort-Object)

[Indelings typen in .NET](/dotnet/standard/base-types/formatting-types)
