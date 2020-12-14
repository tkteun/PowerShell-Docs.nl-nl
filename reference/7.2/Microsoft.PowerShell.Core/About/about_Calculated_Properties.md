---
description: Power shell biedt de mogelijkheid om op dynamische wijze nieuwe eigenschappen toe te voegen en de opmaak van objecten uitvoer naar de pijp lijn te wijzigen.
Locale: en-US
ms.date: 08/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_calculated_properties?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Calculated_Properties
ms.openlocfilehash: 1f7470a47a24b7c2b8265d180aac49cfec9031f6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706124"
---
# <a name="about-calculated-properties"></a><span data-ttu-id="a7dbd-103">Berekende eigenschappen</span><span class="sxs-lookup"><span data-stu-id="a7dbd-103">About calculated properties</span></span>

## <a name="short-description"></a><span data-ttu-id="a7dbd-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="a7dbd-104">Short Description</span></span>

<span data-ttu-id="a7dbd-105">Power shell biedt de mogelijkheid om op dynamische wijze nieuwe eigenschappen toe te voegen en de opmaak van objecten uitvoer naar de pijp lijn te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-105">PowerShell provides the ability to dynamically add new properties and alter the formatting of objects output to the pipeline.</span></span>

## <a name="long-description"></a><span data-ttu-id="a7dbd-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="a7dbd-106">Long Description</span></span>

<span data-ttu-id="a7dbd-107">Een aantal Power shell-cmdlets transformatie, aggregatie of proces invoer objecten in uitvoer objecten met behulp van para meters die het toevoegen van nieuwe eigenschappen aan die uitvoer objecten toestaan.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-107">A number of PowerShell cmdlets transform, aggregate, or process input objects into output objects using parameters that allow the addition of new properties to those output objects.</span></span> <span data-ttu-id="a7dbd-108">Deze para meters kunnen worden gebruikt om nieuwe, berekende eigenschappen voor uitvoer objecten te genereren op basis van de waarden van invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-108">These parameters can be used to generate new, calculated properties on output objects based on the values of input objects.</span></span>
<span data-ttu-id="a7dbd-109">De berekende eigenschap wordt gedefinieerd door een [hashtabel](about_hash_tables.md) met sleutel-waardeparen waarmee de naam van de nieuwe eigenschap wordt opgegeven, een expressie voor het berekenen van de waarde en optionele indelings informatie.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-109">The calculated property is defined by a [hashtable](about_hash_tables.md) containing key-value pairs that specify the name of the new property, an expression to calculate the value, and optional formatting information.</span></span>

## <a name="supported-cmdlets"></a><span data-ttu-id="a7dbd-110">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="a7dbd-110">Supported cmdlets</span></span>

<span data-ttu-id="a7dbd-111">De volgende cmdlets ondersteunen berekende eigenschaps waarden voor de **eigenschaps** parameter.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-111">The following cmdlets support calculated property values for the **Property** parameter.</span></span> <span data-ttu-id="a7dbd-112">De `Format-*` cmdlets ondersteunen ook berekende waarden voor de para meter **GroupBy** .</span><span class="sxs-lookup"><span data-stu-id="a7dbd-112">The `Format-*` cmdlets also support calculated values for the **GroupBy** parameter.</span></span>

<span data-ttu-id="a7dbd-113">De volgende lijst specificatie de cmdlets die berekende eigenschappen ondersteunen en de sleutel-waardeparen die door elke cmdlet worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-113">The following list itemizes the cmdlets that support calculated properties and the key-value pairs that are supported by each cmdlet.</span></span>

- `Compare-Object`
  - `expression`

- `ConvertTo-Html`
  - <span data-ttu-id="a7dbd-114">`name`/`label` -optioneel (toegevoegd in Power shell 6. x)</span><span class="sxs-lookup"><span data-stu-id="a7dbd-114">`name`/`label` - optional (added in PowerShell 6.x)</span></span>
  - `expression`
  - <span data-ttu-id="a7dbd-115">`width` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-115">`width` - optional</span></span>
  - <span data-ttu-id="a7dbd-116">`alignment` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-116">`alignment` - optional</span></span>

- `Format-Custom`
  - `expression`
  - <span data-ttu-id="a7dbd-117">`depth` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-117">`depth` - optional</span></span>

- `Format-List`
  - <span data-ttu-id="a7dbd-118">`name`/`label` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-118">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="a7dbd-119">`formatstring` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-119">`formatstring` - optional</span></span>

  <span data-ttu-id="a7dbd-120">Deze zelfde set sleutel-waardeparen geldt ook voor berekende eigenschaps waarden die worden door gegeven aan de para meter **GroupBy** voor alle `Format-*` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-120">This same set of key-value pairs also apply to calculated property values passed to the **GroupBy** parameter for all `Format-*` cmdlets.</span></span>

- `Format-Table`
  - <span data-ttu-id="a7dbd-121">`name`/`label` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-121">`name`/`label` - optional</span></span>
  - `expression`
  - <span data-ttu-id="a7dbd-122">`formatstring` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-122">`formatstring` - optional</span></span>
  - <span data-ttu-id="a7dbd-123">`width` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-123">`width` - optional</span></span>
  - <span data-ttu-id="a7dbd-124">`alignment` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-124">`alignment` - optional</span></span>

- `Format-Wide`
  - `expression`
  - <span data-ttu-id="a7dbd-125">`formatstring` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-125">`formatstring` - optional</span></span>

- `Group-Object`
  - `expression`

- `Measure-Object`
  - <span data-ttu-id="a7dbd-126">Biedt alleen ondersteuning voor een script blok voor de expressie, niet voor een hashtabel.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-126">Only supports a script block for the expression, not a hashtable.</span></span>
  - <span data-ttu-id="a7dbd-127">Niet ondersteund in Power shell 5,1 en ouder.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-127">Not supported in PowerShell 5.1 and older.</span></span>

- `Select-Object`
  - <span data-ttu-id="a7dbd-128">`name`/`label` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-128">`name`/`label` - optional</span></span>
  - `expression`

- `Sort-Object`
  - `expression`
  - <span data-ttu-id="a7dbd-129">`ascending`/`descending` -optioneel</span><span class="sxs-lookup"><span data-stu-id="a7dbd-129">`ascending`/`descending` - optional</span></span>

> [!NOTE]
> <span data-ttu-id="a7dbd-130">De waarde van het `expression` kan een script blok in plaats van een hashtabel zijn.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-130">The value of the `expression` can be a script block instead of a hashtable.</span></span> <span data-ttu-id="a7dbd-131">Zie de sectie [opmerkingen](#notes) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-131">For more information, see the [Notes](#notes) section.</span></span>

## <a name="hashtable-key-definitions"></a><span data-ttu-id="a7dbd-132">Hashes sleutel definities</span><span class="sxs-lookup"><span data-stu-id="a7dbd-132">Hashtable key definitions</span></span>

- <span data-ttu-id="a7dbd-133">`name`/`label` -Hiermee geeft u de naam op van de eigenschap die wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-133">`name`/`label` - Specifies the name of the property being created.</span></span> <span data-ttu-id="a7dbd-134">U kunt `name` de alias, `label` , verwisselbaar, gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-134">You can use `name` or its alias, `label`, interchangeably.</span></span>
- <span data-ttu-id="a7dbd-135">`expression` -Een script blok dat wordt gebruikt om de waarde van de nieuwe eigenschap te berekenen.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-135">`expression` - A script block used to calculate the value of the new property.</span></span>
- <span data-ttu-id="a7dbd-136">`alignment` -Wordt gebruikt door cmdlets die in tabel vorm worden uitgevoerd om te definiëren hoe de waarden in een kolom worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-136">`alignment` - Used by cmdlets that produce tabular output to define how the values are displayed in a column.</span></span> <span data-ttu-id="a7dbd-137">De waarde moet `'left'` , `'center'` of zijn `'right'` .</span><span class="sxs-lookup"><span data-stu-id="a7dbd-137">The value must be `'left'`, `'center'`, or `'right'`.</span></span>
- <span data-ttu-id="a7dbd-138">`formatstring` -Geeft een indelings teken reeks die definieert hoe de waarde wordt opgemaakt voor uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-138">`formatstring` - Specifies a format string that defines how the value is formatted for output.</span></span> <span data-ttu-id="a7dbd-139">Zie [opmaak typen in .net](/dotnet/standard/base-types/formatting-types)voor meer informatie over opmaak teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-139">For more information about format strings, see [Format types in .NET](/dotnet/standard/base-types/formatting-types).</span></span>
- <span data-ttu-id="a7dbd-140">`width` -Geeft de kolom maximum breedte in een tabel op wanneer de waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-140">`width` - Specifies the maximum width column in a table when the value is displayed.</span></span> <span data-ttu-id="a7dbd-141">De waarde moet groter zijn dan `0` .</span><span class="sxs-lookup"><span data-stu-id="a7dbd-141">The value must be greater than `0`.</span></span>
- <span data-ttu-id="a7dbd-142">`depth` -De **Depth** -para meter van `Format-Custom` bepaalt de diepte van uitbrei ding voor alle eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-142">`depth` - The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="a7dbd-143">`depth`Met de sleutel kunt u de diepte van de uitbrei ding per eigenschap opgeven.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-143">The `depth` key allows you to specify the depth of expansion per property.</span></span>
- <span data-ttu-id="a7dbd-144">`ascending` / `descending` -Hiermee kunt u de sorteer volgorde voor een of meer eigenschappen opgeven.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-144">`ascending` / `descending` - Allows you to specify the order of sorting for one or more properties.</span></span> <span data-ttu-id="a7dbd-145">Dit zijn Booleaanse waarden.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-145">These are boolean values.</span></span>

<span data-ttu-id="a7dbd-146">De hash-code sleutels hoeven niet te worden gespeld zolang het opgegeven naam voorvoegsel niet eenduidig is.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-146">The hashtable keys need not be spelled out as long as the specified name prefix is unambiguous.</span></span> <span data-ttu-id="a7dbd-147">`n`Kan bijvoorbeeld worden gebruikt in plaats van `Name` en `e` kan worden gebruikt in plaats van `Expression` .</span><span class="sxs-lookup"><span data-stu-id="a7dbd-147">For example, `n` can be used in lieu of `Name` and `e` can be used in lieu of `Expression`.</span></span>

## <a name="examples"></a><span data-ttu-id="a7dbd-148">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="a7dbd-148">Examples</span></span>

### <a name="compare-object"></a><span data-ttu-id="a7dbd-149">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="a7dbd-149">Compare-Object</span></span>

<span data-ttu-id="a7dbd-150">Met berekende eigenschappen kunt u bepalen hoe de eigenschappen van de invoer objecten worden vergeleken.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-150">With calculated properties, you can control how the properties of the input objects are compared.</span></span> <span data-ttu-id="a7dbd-151">In dit voor beeld worden de waarden in plaats van de waarden rechtstreeks te vergelijken met het resultaat van de reken kundige bewerking (modulus van 2).</span><span class="sxs-lookup"><span data-stu-id="a7dbd-151">In this example, rather than comparing the values directly, the values are compared to the result of the arithmetic operation (modulus of 2).</span></span>

```powershell
Compare-Object @{p=1} @{p=2} -property @{ Expression = { $_.p % 2 } }
```

```Output
 $_.p % 2  SideIndicator
---------- -------------
         0 =>
         1 <=
```

### <a name="convertto-html"></a><span data-ttu-id="a7dbd-152">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="a7dbd-152">ConvertTo-Html</span></span>

<span data-ttu-id="a7dbd-153">`ConvertTo-Html` een verzameling objecten kan worden geconverteerd naar een HTML-tabel.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-153">`ConvertTo-Html` can convert a collection of objects to an HTML table.</span></span>
<span data-ttu-id="a7dbd-154">Met berekende eigenschappen kunt u bepalen hoe de tabel wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-154">Calculated properties allow you to control how the table is presented.</span></span>

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

<span data-ttu-id="a7dbd-155">In dit voor beeld wordt een HTML-tabel gemaakt met een lijst met Power shell-aliassen en de numerieke para meters voor elke opdracht met een alias.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-155">This example creates an HTML table containing a list of PowerShell aliases and the number parameters for each aliased command.</span></span> <span data-ttu-id="a7dbd-156">De waarden van de kolom **ParameterCount** worden gecentreerd.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-156">The values of **ParameterCount** column are centered.</span></span>

### <a name="format-custom"></a><span data-ttu-id="a7dbd-157">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="a7dbd-157">Format-Custom</span></span>

<span data-ttu-id="a7dbd-158">`Format-Custom` biedt een aangepaste weer gave van een object in een indeling die vergelijkbaar is met de definitie van een klasse.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-158">`Format-Custom` provides a custom view of an object in a format similar to a class definition.</span></span> <span data-ttu-id="a7dbd-159">Complexere objecten kunnen leden bevatten die diep zijn genest met complexe typen.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-159">More complex objects can contain members that are deeply nested with complex types.</span></span> <span data-ttu-id="a7dbd-160">Met de **Depth** para meter `Format-Custom` bepaalt u de diepte van uitbrei ding voor alle eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-160">The **Depth** parameter of `Format-Custom` specifies the depth of expansion for all properties.</span></span> <span data-ttu-id="a7dbd-161">`depth`Met de sleutel kunt u de diepte van de uitbrei ding per eigenschap opgeven.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-161">The `depth` key allows you to specify the depth of expansion per property.</span></span>

<span data-ttu-id="a7dbd-162">In dit voor beeld `depth` vereenvoudigt de sleutel de aangepaste uitvoer voor de `Get-Date` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-162">In this example, the `depth` key simplifies the custom output for the `Get-Date` cmdlet.</span></span> <span data-ttu-id="a7dbd-163">`Get-Date` retourneert een **DateTime** -object.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-163">`Get-Date` returns a **DateTime** object.</span></span> <span data-ttu-id="a7dbd-164">De eigenschap **date** van dit object is ook een **DateTime** -object, zodat het object is genest.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-164">The **Date** property of this object is also a **DateTime** object, so the object is nested.</span></span>

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

### <a name="format-list"></a><span data-ttu-id="a7dbd-165">Format-List</span><span class="sxs-lookup"><span data-stu-id="a7dbd-165">Format-List</span></span>

<span data-ttu-id="a7dbd-166">In dit voor beeld gebruiken we berekende eigenschappen voor het wijzigen van de naam en de indeling van de uitvoer van `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="a7dbd-166">In this example, we use calculated properties to change the name and format of the output from `Get-ChildItem`.</span></span>

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

### <a name="format-table"></a><span data-ttu-id="a7dbd-167">Format-Table</span><span class="sxs-lookup"><span data-stu-id="a7dbd-167">Format-Table</span></span>

<span data-ttu-id="a7dbd-168">In dit voor beeld voegt de berekende eigenschap een eigenschap **type** toe die wordt gebruikt om de bestanden te classificeren op basis van het inhouds type.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-168">In this example, the calculated property adds a **Type** property used to classify the files by the content type.</span></span>

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

### <a name="format-wide"></a><span data-ttu-id="a7dbd-169">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="a7dbd-169">Format-Wide</span></span>

<span data-ttu-id="a7dbd-170">`Format-Wide`Met de cmdlet kunt u de waarde van één eigenschap voor objecten in een verzameling weer geven als een lijst met meerdere kolommen.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-170">The `Format-Wide` cmdlet allows you to display the value of one property for objects in a collection as a multi-column list.</span></span>

<span data-ttu-id="a7dbd-171">Voor dit voor beeld willen we de bestands naam en de grootte (in kilo bytes) als een brede lijst zien.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-171">For this example, we want to see the filename and the size (in kilobytes) as a wide listing.</span></span> <span data-ttu-id="a7dbd-172">Omdat `Format-Wide` er niet meer dan één eigenschap wordt weer gegeven, gebruiken we een berekende eigenschap om de waarde van twee eigenschappen te combi neren in één waarde.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-172">Since `Format-Wide` does not display more than one property, we use a calculated property to combine the value of two properties into a single value.</span></span>

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

### <a name="group-object"></a><span data-ttu-id="a7dbd-173">Group-Object</span><span class="sxs-lookup"><span data-stu-id="a7dbd-173">Group-Object</span></span>

<span data-ttu-id="a7dbd-174">De `Group-Object` cmdlet geeft objecten weer in groepen op basis van de waarde van een opgegeven eigenschap.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-174">The `Group-Object` cmdlet displays objects in groups based on the value of a specified property.</span></span> <span data-ttu-id="a7dbd-175">In dit voor beeld telt de berekende eigenschap het aantal bestanden van elk inhouds type.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-175">In this example, the calculated property counts the number of files of each content type.</span></span>

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

### <a name="measure-object"></a><span data-ttu-id="a7dbd-176">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="a7dbd-176">Measure-Object</span></span>

<span data-ttu-id="a7dbd-177">De `Measure-Object` cmdlet berekent de numerieke eigenschappen van de objecten.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-177">The `Measure-Object` cmdlet calculates the numeric properties of objects.</span></span> <span data-ttu-id="a7dbd-178">In dit voor beeld gebruiken we een berekende eigenschap om het aantal (**som**) van de getallen te verkrijgen, tussen 1 en 10, die deelbaar zijn door 3.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-178">In this example, we use a calculated property to get the count (**Sum**) of the numbers, between 1 and 10, that are evenly divisible by 3.</span></span>

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
> <span data-ttu-id="a7dbd-179">In tegens telling tot de andere cmdlets `Measure-Object` accepteert geen hashtabel voor berekende eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-179">Unlike the other cmdlets, `Measure-Object` does not accept a hashtable for calculated properties.</span></span> <span data-ttu-id="a7dbd-180">U moet een script blok gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-180">You must use a script block.</span></span>

### <a name="select-object"></a><span data-ttu-id="a7dbd-181">Select-Object</span><span class="sxs-lookup"><span data-stu-id="a7dbd-181">Select-Object</span></span>

<span data-ttu-id="a7dbd-182">U kunt berekende eigenschappen gebruiken om extra leden toe te voegen aan de objecten uitvoer met de `Select-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-182">You can use calculated properties to add additional members to the objects output with the `Select-Object` cmdlet.</span></span> <span data-ttu-id="a7dbd-183">In dit voor beeld geven we de Power shell-aliassen weer die met de letter beginnen `C` .</span><span class="sxs-lookup"><span data-stu-id="a7dbd-183">In this example, we are listing the PowerShell aliases that begin with the letter `C`.</span></span> <span data-ttu-id="a7dbd-184">Met `Select-Object` worden de alias, de cmdlet waaraan deze is toegewezen, en een telling voor het aantal gedefinieerde para meters voor de cmdlet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-184">Using `Select-Object`, we output the alias, the cmdlet it's mapped to, and a count for the number of parameters defined for the cmdlet.</span></span> <span data-ttu-id="a7dbd-185">U kunt de eigenschap **ParameterCount** maken met behulp van een berekende eigenschap.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-185">Using a calculated property, we can create the **ParameterCount** property.</span></span>

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

### <a name="sort-object"></a><span data-ttu-id="a7dbd-186">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="a7dbd-186">Sort-Object</span></span>

<span data-ttu-id="a7dbd-187">Met behulp van de berekende eigenschappen kunt u gegevens in verschillende orders per eigenschap sorteren.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-187">Using the calculated properties, you can sort data in different orders per property.</span></span> <span data-ttu-id="a7dbd-188">In dit voor beeld worden gegevens uit een CSV-bestand in oplopende volg orde gesorteerd op **datum**.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-188">This example sorts data from a CSV file in ascending order by **Date**.</span></span> <span data-ttu-id="a7dbd-189">Maar binnen elke datum worden de rijen in aflopende volg orde gesorteerd op **VerkochteEenheden**.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-189">But within each date, it sorts the rows in descending order by **UnitsSold**.</span></span>

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

## <a name="notes"></a><span data-ttu-id="a7dbd-190">Notities</span><span class="sxs-lookup"><span data-stu-id="a7dbd-190">Notes</span></span>

- <span data-ttu-id="a7dbd-191">U kunt het Expression-script blok _rechtstreeks_ als een argument opgeven, in plaats van deze op te geven als de `Expression` vermelding in een hashtabel.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-191">You may specify the expression script block _directly_, as an argument, rather than specifying it as the `Expression` entry in a hashtable.</span></span> <span data-ttu-id="a7dbd-192">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a7dbd-192">For example:</span></span>

  ```powershell
  '1', '10', '2' | Sort-Object { [int] $_ }
  ```

  <span data-ttu-id="a7dbd-193">Dit voor beeld is handig voor cmdlets die geen ondersteuning vereisen voor een eigenschap via de `Name` sleutel, zoals `Sort-Object` , `Group-Object` , en `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="a7dbd-193">This example is convenient for cmdlets that do not require (or support) naming a property via the `Name` key, such as `Sort-Object`, `Group-Object`, and `Measure-Object`.</span></span>

  <span data-ttu-id="a7dbd-194">Voor cmdlets die de naam van de eigenschap ondersteunen, wordt het script blok geconverteerd naar een teken reeks en gebruikt als de naam van de eigenschap in de uitvoer.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-194">For cmdlets that support naming the property, the script block is converted to a string and used as the name of the property in the output.</span></span>

- <span data-ttu-id="a7dbd-195">`Expression` script blokken worden uitgevoerd in _onderliggende_ bereiken, wat betekent dat de variabelen van de beller niet rechtstreeks kunnen worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-195">`Expression` script blocks run in _child_ scopes, meaning that the caller's variables cannot be directly modified.</span></span>

- <span data-ttu-id="a7dbd-196">Pijplijn logica wordt toegepast op de uitvoer van `Expression` script blokken.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-196">Pipeline logic is applied to the output from `Expression` script blocks.</span></span> <span data-ttu-id="a7dbd-197">Dit betekent dat het uitvoeren van een single-element matrix ertoe leidt dat de matrix onverpakt wordt.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-197">This means that outputting a single-element array causes that array to be unwrapped.</span></span>

- <span data-ttu-id="a7dbd-198">Voor de meeste cmdlets worden fouten in Expression-script blokken op de achtergrond genegeerd.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-198">For most cmdlets, errors inside expression script blocks are quietly ignored.</span></span>
  <span data-ttu-id="a7dbd-199">Voor `Sort-Object` is de instructie-Terminate en script-Terminate-fouten _uitvoer_ , maar de instructie wordt niet beëindigd.</span><span class="sxs-lookup"><span data-stu-id="a7dbd-199">For `Sort-Object`, statement-terminating and script-terminating errors are _output_ but they do not terminate the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7dbd-200">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a7dbd-200">See Also</span></span>

[<span data-ttu-id="a7dbd-201">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="a7dbd-201">about_Hash_Tables</span></span>](about_hash_tables.md)

[<span data-ttu-id="a7dbd-202">Compare-object</span><span class="sxs-lookup"><span data-stu-id="a7dbd-202">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="a7dbd-203">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="a7dbd-203">ConvertTo-Html</span></span>](xref:Microsoft.PowerShell.Utility.ConvertTo-Html)

[<span data-ttu-id="a7dbd-204">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="a7dbd-204">Format-Custom</span></span>](xref:Microsoft.PowerShell.Utility.Format-Custom)

[<span data-ttu-id="a7dbd-205">Format-List</span><span class="sxs-lookup"><span data-stu-id="a7dbd-205">Format-List</span></span>](xref:Microsoft.PowerShell.Utility.Format-List)

[<span data-ttu-id="a7dbd-206">Format-Table</span><span class="sxs-lookup"><span data-stu-id="a7dbd-206">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="a7dbd-207">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="a7dbd-207">Format-Wide</span></span>](xref:Microsoft.PowerShell.Utility.Format-Wide)

[<span data-ttu-id="a7dbd-208">Groep-object</span><span class="sxs-lookup"><span data-stu-id="a7dbd-208">Group-Object</span></span>](xref:Microsoft.PowerShell.Utility.Group-Object)

[<span data-ttu-id="a7dbd-209">Meting object</span><span class="sxs-lookup"><span data-stu-id="a7dbd-209">Measure-Object</span></span>](xref:Microsoft.PowerShell.Utility.Measure-Object)

[<span data-ttu-id="a7dbd-210">Select-Object</span><span class="sxs-lookup"><span data-stu-id="a7dbd-210">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

[<span data-ttu-id="a7dbd-211">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="a7dbd-211">Sort-Object</span></span>](xref:Microsoft.PowerShell.Utility.Sort-Object)

[<span data-ttu-id="a7dbd-212">Indelings typen in .NET</span><span class="sxs-lookup"><span data-stu-id="a7dbd-212">Format types in .NET</span></span>](/dotnet/standard/base-types/formatting-types)
