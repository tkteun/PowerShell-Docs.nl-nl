---
description: Hierin wordt uitgelegd hoe u para meters toevoegt aan geavanceerde functies.
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: da21f6fb7d19fa2ffcd9cd6c5eea217792937ae4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705382"
---
# <a name="about-functions-advanced-parameters"></a>Over functies geavanceerde para meters

## <a name="short-description"></a>Korte beschrijving

Hierin wordt uitgelegd hoe u para meters toevoegt aan geavanceerde functies.

## <a name="long-description"></a>Lange beschrijving

U kunt para meters toevoegen aan de geavanceerde functies die u schrijft en parameter kenmerken en argumenten gebruiken om de parameter waarden te beperken die door gebruikers worden verzonden met de para meter.

De para meters die u aan de functie toevoegt, zijn beschikbaar voor gebruikers naast de algemene para meters die Power shell automatisch toevoegt aan alle cmdlets en geavanceerde functies. Zie [about_CommonParameters](about_CommonParameters.md)voor meer informatie over de algemene Power shell-para meters.

Vanaf Power Shell 3,0 kunt u splatting gebruiken `@Args` om de para meters in een opdracht weer te geven. Splatting is geldig voor eenvoudige en geavanceerde functies. Zie [about_Functions](about_Functions.md) en [about_Splatting](about_Splatting.md)voor meer informatie.

## <a name="type-conversion-of-parameter-values"></a>Type conversie van parameter waarden

Wanneer u teken reeksen opgeeft als argumenten voor para meters die een ander type verwachten, converteert Power shell de teken reeksen impliciet naar het doel type van de para meter.
Geavanceerde functies voeren Culture-invariant-parsering van parameter waarden uit.

Daarentegen wordt een cultuur-gevoelige conversie uitgevoerd tijdens de parameter binding van gecompileerde cmdlets.

In dit voor beeld maken we een cmdlet en een script functie die een `[datetime]` para meter gebruiken. De huidige cultuur wordt gewijzigd voor het gebruik van Duitse instellingen.
Een datum in de Duitse notatie wordt door gegeven aan de para meter.

```powershell
# Create a cmdlet that accepts a [datetime] argument.
Add-Type @'
  using System;
  using System.Management.Automation;
  [Cmdlet("Get", "Date_Cmdlet")]
  public class GetFooCmdlet : Cmdlet {

    [Parameter(Position=0)]
    public DateTime Date { get; set; }

    protected override void ProcessRecord() {
      WriteObject(Date);
    }
  }
'@ -PassThru | % Assembly | Import-Module

[cultureinfo]::CurrentCulture = 'de-DE'
$dateStr = '19-06-2018'

Get-Date_Cmdlet $dateStr
```

```Output
Dienstag, 19. Juni 2018 00:00:00
```

Zoals hierboven wordt weer gegeven, gebruiken cmdlets cultuur gevoelige parseren om de teken reeks te converteren.

```powershell
# Define an equivalent function.
function Get-Date_Func {
  param(
    [DateTime] $Date
  )
  process {
    $Date
  }
}

[cultureinfo]::CurrentCulture = 'de-DE'

# This German-format date string doesn't work with the invariant culture.
# E.g., [datetime] '19-06-2018' breaks.
$dateStr = '19-06-2018'

Get-Date_Func $dateStr
```

Geavanceerde functies gebruiken Culture-invariant-parsering, wat resulteert in de volgende fout.

```Output
Get-Date_Func: Cannot process argument transformation on parameter 'Date'.
Cannot convert value "19-06-2018" to type "System.DateTime". Error: "String
'19-06-2018' was not recognized as a valid DateTime."
```

## <a name="static-parameters"></a>Statische para meters

Statische para meters zijn para meters die altijd beschikbaar zijn in de functie.
De meeste para meters in Power shell-cmdlets en-scripts zijn statische para meters.

In het volgende voor beeld ziet u de declaratie van een **ComputerName** -para meter met de volgende kenmerken:

- Het is verplicht (vereist).
- Het neemt de invoer van de pijp lijn.
- Er wordt een matrix met teken reeksen als invoer gebruikt.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a>Kenmerken van para meters

In deze sectie worden de kenmerken beschreven die u kunt toevoegen aan functie parameters.

Alle kenmerken zijn optioneel. Als u echter het kenmerk **CmdletBinding** weglaat en vervolgens als een geavanceerde functie wordt herkend, moet de functie het **parameter** kenmerk bevatten.

U kunt een of meer kenmerken in elke parameter declaratie toevoegen. Er is geen limiet voor het aantal kenmerken dat u aan een parameter declaratie kunt toevoegen.

### <a name="parameter-attribute"></a>Parameter kenmerk

Het **parameter** kenmerk wordt gebruikt voor het declareren van de kenmerken van functie parameters.

Het **parameter** kenmerk is optioneel en u kunt het weglaten als geen van de para meters van uw functies kenmerken nodig heeft. Maar om te worden herkend als een geavanceerde functie in plaats van een eenvoudige functie, moet een functie het kenmerk **CmdletBinding** of het kenmerk **para meter** of beide hebben.

Het **parameter** kenmerk heeft argumenten waarmee de kenmerken van de para meter worden gedefinieerd, bijvoorbeeld of de para meter verplicht of optioneel is.

Gebruik de volgende syntaxis om het **parameter** kenmerk, een argument en een argument waarde te declareren. De haakjes tussen het argument en de bijbehorende waarde moeten de **para meter** zonder tussenliggende ruimte volgen.

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

Gebruik komma's om de argumenten tussen de haakjes te scheiden. Gebruik de volgende syntaxis om twee argumenten van het **parameter** kenmerk te declareren.

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

De Boole-argument typen van het **parameter** kenmerk zijn standaard ingesteld op **Onwaar** als u het **parameter** kenmerk weglaat. Stel de waarde van het argument in op `$true` of alleen een lijst met de naam van het argument. De volgende **parameter** kenmerken zijn bijvoorbeeld gelijkwaardig.

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

Als u het **parameter** kenmerk zonder argumenten gebruikt als alternatief voor het gebruik van het kenmerk **CmdletBinding** , moeten de haakjes die de kenmerk naam volgen, nog steeds vereist zijn.

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a>Verplicht argument

Het `Mandatory` argument geeft aan dat de para meter is vereist. Als dit argument niet wordt opgegeven, is de para meter optioneel.

In het volgende voor beeld wordt de para meter **ComputerName** gedeclareerd. Het argument wordt gebruikt `Mandatory` om de para meter verplicht te maken.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a>Argument positie

Het `Position` argument bepaalt of de parameter naam vereist is wanneer de para meter in een opdracht wordt gebruikt. Wanneer een parameter declaratie het `Position` argument bevat, kan de parameter naam worden wegge laten en Power shell de niet-gegroepeerde parameter waarde identificeren met behulp van de positie of volg orde in de lijst met niet-genaamde parameter waarden in de opdracht.

Als het `Position` argument niet is opgegeven, de parameter naam of een alias naam of afkorting van de para meter moet vóór de parameter waarde worden voorafgegaan wanneer de para meter wordt gebruikt in een opdracht.

Standaard zijn alle functie parameters positioneel. Power shell wijst positie nummers toe aan para meters in de volg orde waarin de para meters in de functie zijn gedeclareerd. Als u deze functie wilt uitschakelen, stelt u de waarde van het `PositionalBinding` argument van het kenmerk **CmdletBinding** in op `$False` . Het `Position` argument heeft voor rang op de waarde van het `PositionalBinding` argument van het kenmerk **CmdletBinding** . Zie `PositionalBinding` in [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)voor meer informatie.

De waarde van het `Position` argument wordt opgegeven als een geheel getal. Een positie waarde van **0** vertegenwoordigt de eerste positie in de opdracht, een positie waarde van **1** vertegenwoordigt de tweede positie in de opdracht, enzovoort.

Als een functie geen positionele para meters heeft, wijst Power shell posities toe aan elke para meter op basis van de volg orde waarin de para meters worden gedeclareerd.
Als best practice, vertrouwt u echter niet op deze toewijzing. Gebruik het argument als u wilt dat de para meters positioneel zijn `Position` .

In het volgende voor beeld wordt de para meter **ComputerName** gedeclareerd. Het argument wordt gebruikt `Position` met de waarde **0**. Als dit het geval `-ComputerName` is, moet de waarde van de opdracht worden wegge laten door de eerste of enige niet-genaamde parameter waarde in de opdracht.

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a>ParameterSetName-argument

Het `ParameterSetName` argument geeft de parameterset op waarvan een para meter deel uitmaakt. Als er geen parameterset is opgegeven, hoort de para meter bij alle parameter sets die zijn gedefinieerd door de functie. Daarom moet elke parameterset ten minste één para meter hebben die geen lid is van een andere parameterset.

> [!NOTE]
> Voor een cmdlet of functie geldt een limiet van 32 parameter sets.

In het volgende voor beeld wordt de para meter **ComputerName** gedeclareerd in de `Computer` parameterset, een **gebruikers naam** parameter in de `User` parameterset en een **samenvattings** parameter in beide parameter sets.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false)]
    [Switch]
    $Summary
)
```

U kunt slechts één `ParameterSetName` waarde opgeven in elk argument en slechts één `ParameterSetName` argument in elk **parameter** kenmerk. Voeg extra **parameter** kenmerken toe om aan te geven dat een para meter in meer dan één parameterset wordt weer gegeven.

In het volgende voor beeld wordt de **samenvattings** parameter expliciet aan de `Computer` `User` para meters en ingesteld. De **samenvattings** parameter is optioneel in de `Computer` parameterset en verplicht in de `User` parameterset.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false, ParameterSetName="Computer")]
    [Parameter(Mandatory=$true, ParameterSetName="User")]
    [Switch]
    $Summary
)
```

Zie [about para meters](about_parameter_sets.md)voor meer informatie over parameter sets.

#### <a name="valuefrompipeline-argument"></a>ValueFromPipeline-argument

Het `ValueFromPipeline` argument geeft aan dat de para meter invoer accepteert van een pijplijn object. Geef dit argument op als de functie het volledige object accepteert, niet alleen een eigenschap van het object.

In het volgende voor beeld wordt een para meter **ComputerName** gedeclareerd die verplicht is en wordt een object geaccepteerd dat wordt door gegeven aan de functie vanuit de pijp lijn.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a>ValueFromPipelineByPropertyName-argument

Het `ValueFromPipelineByPropertyName` argument geeft aan dat de para meter invoer accepteert van een eigenschap van een pijplijn object. De object eigenschap moet dezelfde naam of alias hebben als de para meter.

Als de functie bijvoorbeeld de para meter **ComputerName** heeft en het object piped een eigenschap **ComputerName** heeft, wordt de waarde van de eigenschap **ComputerName** toegewezen aan de para meter **ComputerName** van de functie.

In het volgende voor beeld wordt een para meter **ComputerName** gedeclareerd die verplicht is en accepteert de invoer van de eigenschap **ComputerName** van het object die wordt door gegeven aan de functie via de pijp lijn.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> Een getypeerde para meter die pijplijn invoer ( `by Value` ) of () accepteert, `by PropertyName` maakt het gebruik van script blokken met _vertragings bindingen_ mogelijk voor de para meter.
>
> Het script blok voor de _vertragings binding_ wordt automatisch uitgevoerd tijdens **ParameterBinding**. Het resultaat is gebonden aan de para meter. De vertraagde binding werkt niet voor para meters die zijn gedefinieerd als type `ScriptBlock` of `System.Object` . Het script blok is door gegeven _zonder te_ worden aangeroepen.
>
> U kunt hier meer lezen over de script blokken _met vertragings bindingen_ [about_Script_Blocks. MD](about_Script_Blocks.md).

#### <a name="valuefromremainingarguments-argument"></a>ValueFromRemainingArguments-argument

Het `ValueFromRemainingArguments` argument geeft aan dat de para meter alle waarden van de para meter in de opdracht accepteert die niet zijn toegewezen aan andere para meters van de functie.

In het volgende voor beeld wordt een **waarde** -para meter gedeclareerd die verplicht is en een **resterende** para meter die alle resterende parameter waarden accepteert die worden verzonden naar de functie.

```powershell
function Test-Remainder
{
     param(
         [string]
         [Parameter(Mandatory = $true, Position=0)]
         $Value,
         [string[]]
         [Parameter(Position=1, ValueFromRemainingArguments)]
         $Remaining)
     "Found $($Remaining.Count) elements"
     for ($i = 0; $i -lt $Remaining.Count; $i++)
     {
        "${i}: $($Remaining[$i])"
     }
}
Test-Remainder first one,two
```

```Output
Found 2 elements
0: one
1: two
```

> [!NOTE]
> Vóór Power shell 6,2 werd de **ValueFromRemainingArguments** -verzameling toegevoegd als één entiteit onder index **0**.

#### <a name="helpmessage-argument"></a>HelpMessage-argument

Het `HelpMessage` argument geeft een teken reeks die een korte beschrijving van de para meter of de waarde ervan bevat. In Power shell wordt dit bericht weer gegeven in de prompt die wordt weer gegeven wanneer een verplichte parameter waarde ontbreekt in een opdracht. Dit argument heeft geen effect op optionele para meters.

In het volgende voor beeld declareert u een verplichte para meter **ComputerName** en een Help-bericht waarin de verwachte parameter waarde wordt uitgelegd.

Als er geen andere [Help-syntaxis op basis van opmerkingen](./about_comment_based_help.md) is voor de functie (bijvoorbeeld `.SYNOPSIS` ), wordt dit bericht ook weer gegeven in `Get-Help` uitvoer.

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a>Alias kenmerk

Met het **alias** kenmerk wordt een alternatieve naam voor de para meter gemaakt.
Er is geen limiet voor het aantal aliassen dat u aan een para meter kunt toewijzen.

In het volgende voor beeld ziet u een parameter declaratie waarmee de **CN** -en **MachineName** -aliassen worden toegevoegd aan de verplichte para meter **ComputerName** .

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a>SupportsWildcards-kenmerk

Het kenmerk **SupportsWildcards** wordt gebruikt om aan te geven dat de para meter Joker teken waarden accepteert. In het volgende voor beeld ziet u een parameter declaratie voor een verplichte para meter **Path** die waarden voor joker tekens ondersteunt.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

Als u dit kenmerk gebruikt, wordt ondersteuning voor joker tekens niet automatisch ingeschakeld. De cmdlet-ontwikkelaar moet de code implementeren voor het afhandelen van de invoer van het Joker teken. De ondersteunde joker tekens kunnen variëren, afhankelijk van de onderliggende API of Power shell-provider. Zie [about_Wildcards](about_Wildcards.md)voor meer informatie.

### <a name="parameter-and-variable-validation-attributes"></a>Validatie kenmerken voor para meters en variabelen

Validatie kenmerken direct Power shell voor het testen van de parameter waarden die gebruikers verzenden wanneer ze de functie Advanced aanroepen. Als de parameter waarden de test niet uitvoeren, wordt er een fout gegenereerd en wordt de functie niet aangeroepen. Parameter validatie wordt alleen toegepast op de opgegeven invoer en andere waarden, zoals standaard waarden, worden niet gevalideerd.

U kunt ook de validatie kenmerken gebruiken om de waarden te beperken die gebruikers voor variabelen kunnen opgeven. Wanneer u een type-Converter gebruikt in combi natie met een validatie kenmerk, moet het type Converter worden gedefinieerd vóór het kenmerk.

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a>Validatie kenmerk AllowNull

Met het kenmerk **AllowNull** kan de waarde van een verplichte para meter zijn `$null` . In het volgende voor beeld wordt een hashtabel **ComputerInfo** -para meter gedeclareerd die een **Null** -waarde kan hebben.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> Het kenmerk **AllowNull** werkt niet als het type Converter is ingesteld op teken reeks, omdat het teken reeks type geen null-waarde accepteert. U kunt het kenmerk **AllowEmptyString** gebruiken voor dit scenario.

### <a name="allowemptystring-validation-attribute"></a>Validatie kenmerk AllowEmptyString

Met het kenmerk **AllowEmptyString** kan de waarde van een verplichte para meter een lege teken reeks ( `""` ) zijn. In het volgende voor beeld wordt een **ComputerName** -para meter gedeclareerd die een lege teken reeks waarde kan hebben.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a>Validatie kenmerk AllowEmptyCollection

Met het kenmerk **AllowEmptyCollection** kan de waarde van een verplichte para meter een lege verzameling zijn `@()` . In het volgende voor beeld wordt een **ComputerName** -para meter gedeclareerd die een lege verzamelings waarde kan hebben.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a>Validatie kenmerk ValidateCount

Het kenmerk **ValidateCount** geeft het minimale en maximale aantal parameter waarden op dat door een para meter wordt geaccepteerd. In Power shell wordt een fout gegenereerd als het aantal parameter waarden in de opdracht die de functie aanroept buiten dat bereik valt.

Met de volgende parameter declaratie wordt een **ComputerName** -para meter gemaakt die één tot vijf parameter waarden nodig heeft.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a>Validatie kenmerk ValidateLength

Het kenmerk **ValidateLength** geeft het minimale en maximale aantal tekens in een para meter of variabele waarde aan. Power shell genereert een fout als de lengte van een opgegeven waarde voor een para meter of variabele buiten het bereik valt.

In het volgende voor beeld moet elke computer naam een tot tien tekens bevatten.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

In het volgende voor beeld moet de waarde van de variabele `$number` Mini maal één teken lang zijn en Maxi maal tien tekens bevatten.

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> In dit voor beeld is de waarde van `01` wordt ingepakt in enkele aanhalings tekens. Het kenmerk **ValidateLength** accepteert geen getal zonder aanhalings tekens.

### <a name="validatepattern-validation-attribute"></a>Validatie kenmerk ValidatePattern

Het kenmerk **ValidatePattern** geeft een reguliere expressie aan die wordt vergeleken met de waarde van de para meter of variabele. Power shell genereert een fout als de waarde niet overeenkomt met het reguliere-expressie patroon.

In het volgende voor beeld moet de parameter waarde een getal van vier cijfers bevatten en elk cijfer moet een getal van nul tot negen zijn.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

In het volgende voor beeld moet de waarde van de variabele `$number` exact een getal van vier cijfers zijn en moet elk cijfer een getal van nul tot negen zijn.

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a>Validatie kenmerk ValidateRange

Het kenmerk **ValidateRange** geeft een numeriek bereik of een **ValidateRangeKind** -Enum-waarde voor elke para meter of variabele waarde aan.
Power shell genereert een fout als een wille keurige waarde buiten dat bereik valt.

De **ValidateRangeKind** -opsomming kan de volgende waarden hebben:

- Een **positief** getal dat groter is dan nul.
- **Negatief** -een getal kleiner dan nul.
- Niet- **positief** -een getal kleiner dan of gelijk aan nul.
- Niet- **negatief** : een getal dat groter is dan of gelijk is aan nul.

In het volgende voor beeld moet de waarde van de para meter **pogingen** tussen nul en tien zijn.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

In het volgende voor beeld moet de waarde van de variabele `$number` tussen 0 en tien zijn.

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

In het volgende voor beeld moet de waarde van de variabele `$number` groter zijn dan nul.

```powershell
[Int32][ValidateRange("Positive")]$number = 1
```

### <a name="validatescript-validation-attribute"></a>Validatie kenmerk ValidateScript

Het kenmerk **ValidateScript** geeft een script op dat wordt gebruikt om een para meter of variabele waarde te valideren. Power shell Pipet de waarde naar het script en genereert een fout als het script wordt geretourneerd `$false` of als het script een uitzonde ring genereert.

Wanneer u het kenmerk **ValidateScript** gebruikt, wordt de te valideren waarde toegewezen aan de `$_` variabele. U kunt de `$_` variabele gebruiken om te verwijzen naar de waarde in het script.

In het volgende voor beeld moet de waarde van de para meter **EventDate** groter zijn dan of gelijk zijn aan de huidige datum.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

In het volgende voor beeld moet de waarde van de variabele `$date` groter zijn dan of gelijk zijn aan de huidige datum en tijd.

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> Als u **ValidateScript** gebruikt, kunt u geen waarde door geven `$null` aan de para meter. Wanneer u een null-waarde doorgeeft **ValidateScript** kan het argument niet valideren.

### <a name="validateset-attribute"></a>Het kenmerk validate

Het kenmerk **Validate** bevat een set geldige waarden voor een para meter of variabele en schakelt het volt ooien van het tabblad in. Power shell genereert een fout als een para meter of variabele waarde niet overeenkomt met een waarde in de set. In het volgende voor beeld kan de waarde van de para meter **detail** alleen laag, gemiddeld of hoog zijn.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

In het volgende voor beeld moet de waarde van de variabele `$flavor` Choco lade, aard beien of vanille zijn.

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

De validatie wordt uitgevoerd wanneer deze variabele wordt toegewezen, zelfs binnen het script. Het volgende resulteert bijvoorbeeld in een fout tijdens runtime:

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

#### <a name="dynamic-validateset-values"></a>Dynamische validate-waarden

U kunt een **klasse** gebruiken voor het dynamisch genereren van de waarden voor **Validate** tijdens runtime. In het volgende voor beeld worden de geldige waarden voor de variabele `$Sound` gegenereerd via een **klasse** met de naam **SoundNames** die drie bestandssysteem paden controleert op beschik bare geluids bestanden:

```powershell
Class SoundNames : System.Management.Automation.IValidateSetValuesGenerator {
    [String[]] GetValidValues() {
        $SoundPaths = '/System/Library/Sounds/',
            '/Library/Sounds','~/Library/Sounds'
        $SoundNames = ForEach ($SoundPath in $SoundPaths) {
            If (Test-Path $SoundPath) {
                (Get-ChildItem $SoundPath).BaseName
            }
        }
        return [String[]] $SoundNames
    }
}
```

De `[SoundNames]` klasse wordt vervolgens als volgt geïmplementeerd als een dynamische **Validate** -waarde:

```powershell
Param(
    [ValidateSet([SoundNames])]
    [String]$Sound
)
```

### <a name="validatenotnull-validation-attribute"></a>Validatie kenmerk ValidateNotNull

Het kenmerk **ValidateNotNull** geeft aan dat de parameter waarde niet kan zijn `$null` . Power shell genereert een fout als de waarde van de para meter `$null` .

Het kenmerk **ValidateNotNull** is ontworpen om te worden gebruikt wanneer de para meter optioneel is en het type is niet gedefinieerd of een type Converter heeft dat een null-waarde zoals een **object** niet impliciet kan converteren. Als u een type opgeeft dat impliciet een null-waarde, zoals een **teken reeks**, converteert, wordt de null-waarde omgezet in een lege teken reeks, zelfs wanneer het kenmerk **ValidateNotNull** wordt gebruikt. Voor dit scenario gebruikt u de **ValidateNotNullOrEmpty**

In het volgende voor beeld kan de waarde van de para meter **id** niet zijn `$null` .

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a>Validatie kenmerk ValidateNotNullOrEmpty

Het kenmerk **ValidateNotNullOrEmpty** geeft aan dat de parameter waarde niet kan zijn `$null` en mag geen lege teken reeks ( `""` ) zijn. Power shell genereert een fout als de para meter wordt gebruikt in een functie aanroep, maar de waarde hiervan is `$null` , een lege teken reeks ( `""` ) of een lege matrix `@()` .

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a>Validatie kenmerk ValidateDrive

Het kenmerk **ValidateDrive** geeft aan dat de parameter waarde het pad moet vertegenwoordigen, dat alleen verwijst naar de toegestane stations. Power shell genereert een fout als de waarde van de para meter verwijst naar andere stations dan toegestaan. Het bestaan van het pad, met uitzonde ring van het station zelf, wordt niet gecontroleerd.

Als u een relatief pad gebruikt, moet het huidige station zich in de lijst met toegestane stations bevinden.

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a>Validatie kenmerk ValidateUserDrive

Het kenmerk **ValidateUserDrive** geeft aan dat de parameter waarde het pad moet vertegenwoordigen dat verwijst naar een `User` station. Power shell genereert een fout melding als het pad naar een ander station verwijst. Het validatie kenmerk test alleen op het bestaan van het station gedeelte van het pad.

Als u een relatief pad gebruikt, moet het huidige station zijn `User` .

```powershell
function Test-UserDrivePath{
    [OutputType([bool])]
    Param(
      [Parameter(Mandatory=, Position=0)][ValidateUserDrive()][String]$Path
      )
    $True
}

Test-UserDrivePath -Path C:\
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. The path
argument drive C does not belong to the set of approved drives: User.
Supply a path argument with an approved drive.
```

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. Cannot
find drive. A drive with the name 'User' does not exist.
```

U kunt een `User` station definiëren in net voldoende beheer-en JEA-sessie configuraties. Voor dit voor beeld maken we de gebruiker: station.

```powershell
New-PSDrive -Name 'User' -PSProvider FileSystem -Root $env:HOMEPATH
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
User               75.76         24.24 FileSystem    C:\Users\ExampleUser

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
True
```

### <a name="validatetrusteddata-validation-attribute"></a>Validatie kenmerk ValidateTrustedData

Dit kenmerk is toegevoegd aan Power shell 6.1.1.

Op dit moment wordt het kenmerk intern gebruikt door Power shell zelf en is het niet bedoeld voor extern gebruik.

## <a name="dynamic-parameters"></a>Dynamische parameters

Dynamische para meters zijn para meters van een cmdlet, functie of script die alleen beschikbaar zijn onder bepaalde voor waarden.

Meerdere provider-cmdlets hebben bijvoorbeeld para meters die alleen beschikbaar zijn wanneer de cmdlet wordt gebruikt in het provider station of in een bepaald pad van het provider station. De para meter **Encoding** is bijvoorbeeld alleen beschikbaar in de `Add-Content` `Get-Content` `Set-Content` cmdlets, en alleen als deze wordt gebruikt in een bestandssysteem station.

U kunt ook een para meter maken die alleen wordt weer gegeven wanneer een andere para meter wordt gebruikt in de functie opdracht of wanneer een andere para meter een bepaalde waarde heeft.

Dynamische para meters kunnen nuttig zijn, maar alleen gebruiken wanneer dat nodig is, omdat ze moeilijk kunnen worden gedetecteerd door gebruikers. Als u een dynamische para meter wilt zoeken, moet de gebruiker zich in het pad van de provider bevinden, de para meter **argument List** van de `Get-Command` cmdlet gebruiken of de para meter **Path** van gebruiken `Get-Help` .

Als u een dynamische para meter voor een functie of script wilt maken, gebruikt u het `DynamicParam` sleutel woord.

De syntaxis is als volgt:

`DynamicParam {<statement-list>}`

Gebruik in de lijst overzicht een `If` instructie om de voor waarden op te geven waaronder de para meter beschikbaar is in de functie.

Gebruik de `New-Object` cmdlet om een **System. Management. Automation. RuntimeDefinedParameter** -object te maken dat de para meter weergeeft en geef de naam op.

U kunt een `New-Object` opdracht gebruiken om een **System. Management. Automation. ParameterAttribute** -object te maken om kenmerken van de para meter weer te geven, zoals **verplicht**, **positie** of **ValueFromPipeline** of de bijbehorende parameterset.

In het volgende voor beeld ziet u een voorbeeld functie met de standaard parameters **name** en **Path** en een optionele dynamische para meter met de naam **DP1**. De **DP1** -para meter bevindt zich in de `PSet1` parameterset en heeft een type van `Int32` .
De para meter **DP1** is alleen beschikbaar in de `Get-Sample` functie wanneer de waarde van de para meter **Path** begint met `HKLM:` , wat aangeeft dat deze wordt gebruikt in het `HKEY_LOCAL_MACHINE` register station.

```powershell
function Get-Sample {
  [CmdletBinding()]
  Param([String]$Name, [String]$Path)

  DynamicParam
  {
    if ($Path.StartsWith("HKLM:"))
    {
      $attributes = New-Object -Type `
        System.Management.Automation.ParameterAttribute
      $attributes.ParameterSetName = "PSet1"
      $attributes.Mandatory = $false
      $attributeCollection = New-Object `
        -Type System.Collections.ObjectModel.Collection[System.Attribute]
      $attributeCollection.Add($attributes)

      $dynParam1 = New-Object -Type `
        System.Management.Automation.RuntimeDefinedParameter("DP1", [Int32],
          $attributeCollection)

      $paramDictionary = New-Object `
        -Type System.Management.Automation.RuntimeDefinedParameterDictionary
      $paramDictionary.Add("DP1", $dynParam1)
      return $paramDictionary
    }
  }
}
```

Zie [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter)voor meer informatie.

## <a name="switch-parameters"></a>Switch parameters

Switch parameters zijn para meters zonder parameter waarde. Ze zijn alleen effectief als ze worden gebruikt en slechts één effect hebben.

De para meter geen **profiel** van **powershell.exe** is bijvoorbeeld een para meter switch.

Als u een switch parameter in een functie wilt maken, geeft u het `Switch` type op in de parameter definitie.

Bijvoorbeeld:

```powershell
Param([Switch]<ParameterName>)
```

U kunt ook een andere methode gebruiken:

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

Switch parameters zijn gemakkelijk te gebruiken en hebben de voor keur boven Boole-para meters, die een moeilijkerere syntaxis hebben.

Als u bijvoorbeeld een para meter switch wilt gebruiken, typt de gebruiker de para meter in de opdracht.

`-IncludeAll`

Als u een Boole-para meter wilt gebruiken, typt de gebruiker de para meter en een Booleaanse waarde.

`-IncludeAll:$true`

Wanneer u switch parameters maakt, moet u de parameter naam zorgvuldig kiezen. Zorg ervoor dat de parameter naam het effect van de para meter communiceert naar de gebruiker.
Vermijd dubbel zinnige termen, zoals het **filter** of het **maximum** waarmee een waarde kan worden opgelegd.

## <a name="argumentcompleter-attribute"></a>ArgumentCompleter-kenmerk

Met het kenmerk **ArgumentCompleter** kunt u waarden voor het volt ooien van tabs toevoegen aan een specifieke para meter. Er moet een **ArgumentCompleter** -kenmerk worden gedefinieerd voor elke para meter die het tabblad moet volt ooien. Net als bij **DynamicParameters** worden de beschik bare waarden tijdens runtime berekend wanneer de gebruiker op <kbd>Tab</kbd> drukt na de parameter naam.

Om een **ArgumentCompleter** -kenmerk toe te voegen, moet u een script blok definiëren waarmee de waarden worden bepaald. Het script blok moet de volgende para meters in de opgegeven volg orde volgen. De namen van de para meters zijn niet belang rijk, omdat de waarden positioneel worden gegeven.

De syntaxis is als volgt:

```powershell
Param(
    [Parameter(Mandatory)]
    [ArgumentCompleter({
        param ( $commandName,
                $parameterName,
                $wordToComplete,
                $commandAst,
                $fakeBoundParameters )
        # Perform calculation of tab completed values here.
    })]
)
```

### <a name="argumentcompleter-script-block"></a>ArgumentCompleter-script blok

De script Block-para meters worden ingesteld op de volgende waarden:

- `$commandName` (Positie 0): deze para meter is ingesteld op de naam van de opdracht waarvoor het script blok het volt ooien van het tabblad oplevert.
- `$parameterName` (Positie 1)-deze para meter wordt ingesteld op de para meter waarvan de waarde het volt ooien van het tabblad vereist.
- `$wordToComplete` (Positie 2): deze para meter is ingesteld op waarde die de gebruiker heeft opgegeven voordat deze <kbd>Tab</kbd>werd ingedrukt. Het script blok moet deze waarde gebruiken om de waarden voor het volt ooien van tabs te bepalen.
- `$commandAst` (Positie 3): deze para meter is ingesteld op de abstracte syntaxis structuur (AST) voor de huidige invoer regel. Zie [AST class](/dotnet/api/system.management.automation.language.ast)(Engelstalig) voor meer informatie.
- `$fakeBoundParameters` (Positie 4): deze para meter is ingesteld op een hashtabel die de `$PSBoundParameters` voor de cmdlet bevat, voordat het <kbd>tabblad</kbd>van de gebruiker wordt ingedrukt. Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie.

Het **ArgumentCompleter** -script blok moet de waarden van de pijp lijn, zoals `ForEach-Object` , `Where-Object` of een andere geschikte methode, ongedaan maken.
Als u een matrix met waarden retourneert, wordt de gehele matrix als **één** waarde voor het volt ooien van een tab behandeld.

In het volgende voor beeld wordt Tab-aanvulling toegevoegd aan de **waarde** -para meter. Als alleen de **waarde** para meter is opgegeven, worden alle mogelijke waarden, of argumenten, voor **waarde** weer gegeven. Als de para meter **type** is opgegeven, geeft de para meter **Value** alleen de mogelijke waarden voor dat type weer.

De operator zorgt er ook voor `-like` dat als de gebruiker de volgende opdracht typt en het <kbd>tabblad</kbd> aanvulling gebruikt, alleen **Apple** wordt geretourneerd.

`Test-ArgumentCompleter -Type Fruits -Value A`

```powershell
function Test-ArgumentCompleter {
[CmdletBinding()]
 param (
        [Parameter(Mandatory=$true)]
        [ValidateSet('Fruits', 'Vegetables')]
        $Type,
        [Parameter(Mandatory=$true)]
        [ArgumentCompleter( {
            param ( $commandName,
                    $parameterName,
                    $wordToComplete,
                    $commandAst,
                    $fakeBoundParameters )

            $possibleValues = @{
                Fruits = @('Apple', 'Orange', 'Banana')
                Vegetables = @('Tomato', 'Squash', 'Corn')
            }
            if ($fakeBoundParameters.ContainsKey('Type'))
            {
                $possibleValues[$fakeBoundParameters.Type] | Where-Object {
                    $_ -like "$wordToComplete*"
                }
            }
            else
            {
                $possibleValues.Values | ForEach-Object {$_}
            }
        } )]
        $Value
      )
}
```

## <a name="see-also"></a>Zie ook

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
