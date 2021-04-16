---
description: Legt uit hoe u parameters toevoegt aan geavanceerde functies.
Locale: en-US
ms.date: 04/14/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: 00fcf9d07ab77ce2df6c0b8ff6c73fb87393f9b2
ms.sourcegitcommit: 366304d096c1caf52f0e17962f6ed23d20f86e7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2021
ms.locfileid: "107543812"
---
# <a name="about-functions-advanced-parameters"></a>Over geavanceerde functiesparameters

## <a name="short-description"></a>Korte beschrijving

Legt uit hoe u parameters toevoegt aan geavanceerde functies.

## <a name="long-description"></a>Lange beschrijving

U kunt parameters toevoegen aan de geavanceerde functies die u schrijft en parameterkenmerken en argumenten gebruiken om de parameterwaarden te beperken die functiegebruikers verzenden met de parameter .

De parameters die u aan uw functie toevoegt, zijn beschikbaar voor gebruikers, naast de algemene parameters die PowerShell automatisch toevoegt aan alle cmdlets en geavanceerde functies. Zie voor meer informatie over de algemene PowerShell-parameters [about_CommonParameters.](about_CommonParameters.md)

Vanaf PowerShell 3.0 kunt u splatting gebruiken met om de parameters in een `@Args` opdracht weer te geven. Splatting is geldig voor eenvoudige en geavanceerde functies. Zie voor meer informatie [about_Functions](about_Functions.md) en [about_Splatting.](about_Splatting.md)

## <a name="type-conversion-of-parameter-values"></a>Typeconversie van parameterwaarden

Wanneer u tekenreeksen als argumenten opgeeft voor parameters die een ander type verwachten, converteert PowerShell impliciet de tekenreeksen naar het doeltype van de parameter.
Geavanceerde functies voeren cultuur-invariante parsering van parameterwaarden uit.

Daarentegen wordt een cultuurgevoelige conversie uitgevoerd tijdens parameterbinding voor gecompileerde cmdlets.

In dit voorbeeld maken we een cmdlet en een scriptfunctie die een `[datetime]` parameter gebruiken. De huidige cultuur wordt gewijzigd om Duitse instellingen te gebruiken.
Een datum in Duits-indeling wordt doorgegeven aan de parameter .

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

Zoals hierboven wordt weergegeven, gebruiken cmdlets cultuurgevoelige parsering om de tekenreeks te converteren.

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

Bij geavanceerde functies wordt gebruik gemaakt van parseren van cultuur invariant, wat resulteert in de volgende fout.

```Output
Get-Date_Func: Cannot process argument transformation on parameter 'Date'.
Cannot convert value "19-06-2018" to type "System.DateTime". Error: "String
'19-06-2018' was not recognized as a valid DateTime."
```

## <a name="static-parameters"></a>Statische parameters

Statische parameters zijn parameters die altijd beschikbaar zijn in de functie .
De meeste parameters in PowerShell-cmdlets en -scripts zijn statische parameters.

In het volgende voorbeeld ziet u de declaratie van een **parameter ComputerName** met de volgende kenmerken:

- Dit is verplicht (vereist).
- Er wordt invoer uit de pijplijn gebruikt.
- Er wordt een matrix met tekenreeksen als invoer gebruikt.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a>Kenmerken van parameters

In deze sectie worden de kenmerken beschreven die u kunt toevoegen aan functieparameters.

Alle kenmerken zijn optioneel. Als u echter het **kenmerk CmdletBinding** weglaat, moet de functie het **kenmerk Parameter** bevatten om te worden herkend als een geavanceerde functie.

U kunt een of meer kenmerken toevoegen aan elke parameterdeclaratie. Er is geen limiet voor het aantal kenmerken dat u aan een parameterdeclaratie kunt toevoegen.

### <a name="parameter-attribute"></a>Parameterkenmerk

Het **kenmerk Parameter** wordt gebruikt om de kenmerken van functieparameters te declaren.

Het **kenmerk Parameter** is optioneel en u kunt dit weglaten als geen van de parameters van uw functies kenmerken nodig heeft. Maar om te worden herkend als een geavanceerde functie, in plaats van een eenvoudige functie, moet een functie ofwel het **kenmerk CmdletBinding,** het **kenmerk Parameter** of beide hebben.

Het **kenmerk Parameter** bevat argumenten die de kenmerken van de parameter definiëren, zoals of de parameter verplicht of optioneel is.

Gebruik de volgende syntaxis om het **kenmerk Parameter,** een argument en een argumentwaarde te declaren. De haakjes die het argument en de waarde ervan tussensluiten, moeten **Parameter** volgen zonder tussenliggende ruimte.

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

Gebruik komma's om argumenten tussen haakjes te scheiden. Gebruik de volgende syntaxis om twee argumenten van het kenmerk **Parameter te** declareeren.

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

De Booleaanse argumenttypen van het **kenmerk Parameter** worden standaard ingesteld op **False** wanneer ze worden weggelaten uit het **kenmerk Parameter.** Stel de argumentwaarde in op `$true` of vermeld het argument op naam. De volgende parameterkenmerken **zijn** bijvoorbeeld gelijkwaardig.

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

Als u het **kenmerk Parameter** zonder argumenten gebruikt, als alternatief voor het gebruik van het **kenmerk CmdletBinding,** zijn de haakjes die de kenmerknaam volgen nog steeds vereist.

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a>Verplicht argument

Het `Mandatory` argument geeft aan dat de parameter vereist is. Als dit argument niet is opgegeven, is de parameter optioneel.

In het volgende voorbeeld wordt de **parameter ComputerName gedeclareert.** Het argument wordt `Mandatory` gebruikt om de parameter verplicht te maken.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a>Argument Position

Het `Position` argument bepaalt of de parameternaam vereist is wanneer de parameter wordt gebruikt in een opdracht. Wanneer een parameterdeclaratie het argument bevat, kan de parameternaam worden weggelaten en identificeert PowerShell de naamloze parameterwaarde op basis van de positie of volgorde in de lijst met niet-naamloze parameterwaarden in de `Position` opdracht.

Als het argument niet is opgegeven, moet de parameternaam of een alias of afkorting van de parameternaam voorafgaan aan de parameterwaarde wanneer de parameter wordt gebruikt `Position` in een opdracht.

Standaard zijn alle functieparameters positioneel. PowerShell wijst positienummers toe aan parameters in de volgorde waarin de parameters in de functie worden gedeclareerd. Als u deze functie wilt uitschakelen, stelt u de waarde van het `PositionalBinding` argument van het kenmerk **CmdletBinding** in op `$False` . Het `Position` argument heeft voorrang op de waarde van het argument van het kenmerk `PositionalBinding` **CmdletBinding.** Zie in about_Functions_CmdletBindingAttribute `PositionalBinding` voor [meer informatie.](about_Functions_CmdletBindingAttribute.md)

De waarde van het `Position` argument wordt opgegeven als een geheel getal. Een positiewaarde **van 0** vertegenwoordigt de eerste positie in de opdracht, een positiewaarde **van 1** vertegenwoordigt de tweede positie in de opdracht, en meer.

Als een functie geen positionele parameters heeft, wijst PowerShell posities toe aan elke parameter op basis van de volgorde waarin de parameters worden gedeclareerd.
Als een best practice, vertrouwt u echter niet op deze toewijzing. Als u wilt dat parameters positioneel zijn, gebruikt u het `Position` argument .

In het volgende voorbeeld wordt de **parameter ComputerName gedeclareert.** Hierbij wordt het `Position` argument met de waarde **0 gebruikt.** Als gevolg hiervan, wanneer wordt weggelaten uit de opdracht, moet de waarde ervan de eerste of alleen `-ComputerName` naamloze parameterwaarde in de opdracht.

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a>Argument ParameterSetName

Het `ParameterSetName` argument geeft de parameterset aan waar een parameter bij hoort. Als er geen parameterset is opgegeven, behoort de parameter tot alle parametersets die door de functie zijn gedefinieerd. Om uniek te zijn, moet elke parameterset ten minste één parameter hebben die geen lid is van een andere parameterset.

> [!NOTE]
> Voor een cmdlet of functie geldt een limiet van 32 parametersets.

In het volgende voorbeeld wordt een **computernaam** parameter in de parameterset, een Gebruikersnaam parameter in de parameterset en een samenvatting `Computer` parameter in beide  `User` parametersets gedeclareert. 

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

U kunt slechts één waarde `ParameterSetName` opgeven in elk argument en slechts één argument in elk `ParameterSetName` **parameterkenmerk.** Als u wilt aangeven dat een parameter wordt weergegeven in meer dan één parameterset, voegt u aanvullende **parameterkenmerken** toe.

In het volgende voorbeeld wordt de parameter **Summary** expliciet toegevoegd aan de `Computer` `User` parametersets en . De **samenvatting** parameter is optioneel in de `Computer` parameterset en verplicht in de `User` parameterset.

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

Zie Over parametersets voor meer informatie [over parametersets.](about_parameter_sets.md)

#### <a name="valuefrompipeline-argument"></a>Argument ValueFromPipeline

Het `ValueFromPipeline` argument geeft aan dat de parameter invoer van een pijplijnobject accepteert. Geef dit argument op als de functie het hele object accepteert, niet alleen een eigenschap van het -object.

In het volgende voorbeeld wordt de parameter **ComputerName** gedeclareert die verplicht is en een object accepteert dat vanuit de pijplijn aan de functie wordt doorgegeven.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a>Argument ValueFromPipelineByPropertyName

Het `ValueFromPipelineByPropertyName` argument geeft aan dat de parameter invoer accepteert van een eigenschap van een pijplijnobject. De eigenschap object moet dezelfde naam of alias hebben als de parameter .

Als de functie bijvoorbeeld een parameter **ComputerName** heeft en het object piped een **eigenschap ComputerName** heeft, wordt de waarde van de eigenschap **ComputerName** toegewezen aan de parameter **ComputerName** van de functie.

In het volgende voorbeeld wordt een **parameter ComputerName** gedeclareert die verplicht is en invoer accepteert van de **eigenschap ComputerName** van het object die via de pijplijn wordt doorgegeven aan de functie.

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> Een getypte parameter die pijplijninvoer ( ) of ( ) accepteert, maakt het gebruik van `by Value` `by PropertyName` _delay-bind-scriptblokken_ voor de parameter mogelijk.
>
> Het _scriptblok delay-bind_ wordt automatisch uitgevoerd tijdens **ParameterBinding.** Het resultaat is gebonden aan de parameter . Vertragingsbinding werkt niet voor parameters die zijn gedefinieerd als type `ScriptBlock` of `System.Object` . Het scriptblok wordt doorgegeven zonder _te_ worden aangeroepen.
>
> U kunt hier meer lezen _over scriptblokken voor_ vertragingsbinding [about_Script_Blocks.md.](about_Script_Blocks.md)

#### <a name="valuefromremainingarguments-argument"></a>Argument ValueFromRemainingArguments

Het argument geeft aan dat de parameter alle waarden van de parameter in de opdracht accepteert die niet zijn toegewezen aan andere `ValueFromRemainingArguments` parameters van de functie.

In het volgende  voorbeeld wordt een waardeparameter gedeclareert die verplicht is en een **resterende** parameter die alle resterende parameterwaarden accepteert die naar de functie worden verzonden.

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
> Vóór PowerShell 6.2 werd de verzameling **ValueFromRemainingArguments** toegevoegd als één entiteit onder index **0**.

#### <a name="helpmessage-argument"></a>Argument HelpMessage

Het `HelpMessage` argument geeft een tekenreeks op die een korte beschrijving van de parameter of de waarde ervan bevat. PowerShell geeft dit bericht weer in de prompt die wordt weergegeven wanneer een verplichte parameterwaarde ontbreekt in een opdracht. Dit argument heeft geen invloed op optionele parameters.

In het volgende voorbeeld wordt een verplichte **ComputerName-parameter** en een Help-bericht gedeclareert waarin de verwachte parameterwaarde wordt uitgelegd.

Als er geen andere [helpsyntaxis](./about_comment_based_help.md) op basis van opmerkingen is voor de functie (bijvoorbeeld ) wordt dit bericht `.SYNOPSIS` ook weergegeven in de `Get-Help` uitvoer.

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a>Aliaskenmerk

Met **het kenmerk Alias** wordt een alternatieve naam voor de parameter gemaakt.
Er is geen limiet voor het aantal aliassen dat u aan een parameter kunt toewijzen.

In het volgende voorbeeld ziet u een parameterdeclaratie die de **CN-** en **MachineName-aliassen** toevoegt aan de verplichte parameter **ComputerName.**

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a>Ondersteunt het kenmerk SupportsWildcards

Het **kenmerk SupportsWildcards** wordt gebruikt om aan te geven dat de parameter jokertekenwaarden accepteert. In het volgende voorbeeld ziet u een parameterdeclaratie voor een verplichte **padparameter** die jokertekenwaarden ondersteunt.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

Als u dit kenmerk gebruikt, wordt ondersteuning voor jokertekens niet automatisch ingeschakeld. De cmdlet-ontwikkelaar moet de code implementeren om de invoer met jokertekens te verwerken. De ondersteunde jokertekens kunnen variëren afhankelijk van de onderliggende API of PowerShell-provider. Zie voor meer informatie [about_Wildcards](about_Wildcards.md).

### <a name="parameter-and-variable-validation-attributes"></a>Validatiekenmerken voor parameters en variabelen

Validatiekenmerken zorgen ervoor dat PowerShell de parameterwaarden test die gebruikers verzenden wanneer ze de geavanceerde functie aanroepen. Als de parameterwaarden niet slagen voor de test, wordt er een fout gegenereerd en wordt de functie niet aangeroepen. Parametervalidatie wordt alleen toegepast op de opgegeven invoer en andere waarden, zoals standaardwaarden, worden niet gevalideerd.

U kunt ook de validatiekenmerken gebruiken om de waarden te beperken die gebruikers voor variabelen kunnen opgeven. Wanneer u een typeconverter samen met een validatiekenmerk gebruikt, moet de typeconverter worden gedefinieerd vóór het kenmerk .

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a>AllowNull-validatiekenmerk

Met **het kenmerk AllowNull** kan de waarde van een verplichte parameter `$null` zijn. In het volgende voorbeeld wordt een **hashtabelcomputerinfo-parameter** gedeclareert die een **null-waarde kan** hebben.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> Het **kenmerk AllowNull** werkt niet als de typeconverter is ingesteld op tekenreeks omdat het tekenreekstype geen null-waarde accepteert. U kunt het **kenmerk AllowEmptyString** gebruiken voor dit scenario.

### <a name="allowemptystring-validation-attribute"></a>Validatiekenmerk AllowEmptyString

Met **het kenmerk AllowEmptyString** kan de waarde van een verplichte parameter een lege tekenreeks () `""` zijn. In het volgende voorbeeld wordt een **parameter ComputerName gedeclareert** die een lege tekenreekswaarde kan hebben.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a>Validatiekenmerk AllowEmptyCollection

Met **het kenmerk AllowEmptyCollection** kan de waarde van een verplichte parameter een lege verzameling `@()` zijn. In het volgende voorbeeld wordt een **parameter ComputerName gedeclareert** die een lege verzamelingswaarde kan hebben.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a>Validatiekenmerk ValidateCount

Het **kenmerk ValidateCount** geeft het minimum- en maximum aantal parameterwaarden aan dat een parameter accepteert. PowerShell genereert een fout als het aantal parameterwaarden in de opdracht die de functie aanroept, buiten dat bereik valt.

Met de volgende parameterdeclaratie maakt u **een ComputerName-parameter** die één tot vijf parameterwaarden nodig heeft.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a>Validatiekenmerk ValidateLength

Het **kenmerk ValidateLength** geeft het minimum- en maximum aantal tekens in een parameter of variabele waarde aan. PowerShell genereert een fout als de lengte van een waarde die is opgegeven voor een parameter of een variabele buiten het bereik valt.

In het volgende voorbeeld moet elke computernaam één tot tien tekens bevatten.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

In het volgende voorbeeld moet de waarde van de variabele minimaal één teken lang en maximaal tien `$number` tekens zijn.

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> In dit voorbeeld wordt de waarde van `01` tussen enkele aanhalingstekens verpakt. Het **kenmerk ValidateLength** accepteert geen getal zonder tussen aanhalingstekens te worden verpakt.

### <a name="validatepattern-validation-attribute"></a>Validatiekenmerk ValidatePattern

Het **kenmerk ValidatePattern** geeft een reguliere expressie op die wordt vergeleken met de parameter of variabele waarde. PowerShell genereert een fout als de waarde niet overeen komt met het patroon van de reguliere expressie.

In het volgende voorbeeld moet de parameterwaarde een viercijferig getal bevatten en moet elk cijfer een getal van nul tot negen zijn.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

In het volgende voorbeeld moet de waarde van de variabele exact een getal van vier cijfers zijn en moet elk cijfer een getal nul tot `$number` negen zijn.

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a>Validatiekenmerk ValidateRange

Het **kenmerk ValidateRange** geeft een numeriek bereik of een **validateRangeKind-enumwaarde** op voor elke parameter of variabele waarde.
PowerShell genereert een fout als een waarde buiten dat bereik valt.

De **enum ValidateRangeKind** staat de volgende waarden toe:

- **Positief:** een getal dat groter is dan nul.
- **Negatief:** een getal dat kleiner is dan nul.
- **Niet-gevoelig:** een getal dat kleiner is dan of gelijk is aan nul.
- **Niet-nul:** een getal dat groter is dan of gelijk is aan nul.

In het volgende voorbeeld moet de waarde van de parameter **Attempts** tussen nul en tien zijn.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

In het volgende voorbeeld moet de waarde van de variabele `$number` tussen nul en tien zijn.

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

In het volgende voorbeeld moet de waarde van de `$number` variabele groter zijn dan nul.

```powershell
[Int32][ValidateRange("Positive")]$number = 1
```

### <a name="validatescript-validation-attribute"></a>Validatiekenmerk ValidateScript

Het **kenmerk ValidateScript** bevat een script dat wordt gebruikt om een parameter of variabele waarde te valideren. PowerShell geeft de waarde door aan het script en genereert een fout als het script retourneert of als het `$false` script een uitzondering genereert.

Wanneer u het **kenmerk ValidateScript** gebruikt, wordt de waarde die wordt gevalideerd, aan de variabele `$_` toegesneden. U kunt de variabele `$_` gebruiken om te verwijzen naar de waarde in het script.

In het volgende voorbeeld moet de waarde van de parameter **EventDate** groter zijn dan of gelijk zijn aan de huidige datum.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

In het volgende voorbeeld moet de waarde van de variabele groter zijn dan of `$date` gelijk zijn aan de huidige datum en tijd.

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> Als u **ValidateScript gebruikt,** kunt u geen waarde `$null` doorgeven aan de parameter . Wanneer u een null-waarde door **te geven,** kan ValidateScript het argument niet valideren.

### <a name="validateset-attribute"></a>ValidateSet-kenmerk

Het **kenmerk ValidateSet** specificeert een set geldige waarden voor een parameter of variabele en maakt tab-voltooiing mogelijk. PowerShell genereert een fout als een parameter of variabele waarde niet overeen komt met een waarde in de set. In het volgende voorbeeld kan de waarde van de parameter **Detail** alleen Laag, Gemiddeld of Hoog zijn.

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

In het volgende voorbeeld moet de waarde van de variabele `$flavor` Chocolade, Aardbeien of Vanille zijn.

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

De validatie vindt plaats wanneer die variabele wordt toegewezen, zelfs binnen het script. Het volgende resulteert bijvoorbeeld in een fout tijdens runtime:

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

#### <a name="dynamic-validateset-values"></a>Dynamische validateSet-waarden

U kunt een klasse **gebruiken om** de waarden voor **ValidateSet** dynamisch te genereren tijdens runtime. In het volgende voorbeeld worden de geldige waarden voor de variabele gegenereerd via een klasse met de naam SoundNames die drie bestandssysteempaden controleert `$Sound` op beschikbare  geluidsbestanden: 

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

De klasse wordt vervolgens als volgt geïmplementeerd als een dynamische `[SoundNames]` **ValidateSet-waarde:**

```powershell
Param(
    [ValidateSet([SoundNames])]
    [String]$Sound
)
```

> [!NOTE]
> De `IValidateSetValuesGenerator` klasse is geïntroduceerd in PowerShell 6.0

### <a name="validatenotnull-validation-attribute"></a>Validatiekenmerk ValidateNotNull

Het **kenmerk ValidateNotNull** geeft aan dat de parameterwaarde niet mag `$null` zijn. PowerShell genereert een fout als de parameterwaarde `$null` is.

Het **kenmerk ValidateNotNull** is ontworpen om te worden gebruikt wanneer de parameter optioneel is en het type niet is gedefinieerd of een typeconverter heeft die niet impliciet een null-waarde kan converteren, zoals **object**. Als u een type opgeeft dat impliciet een null-waarde converteert, zoals een tekenreeks, wordt de null-waarde geconverteerd naar een lege tekenreeks, zelfs wanneer het **kenmerk ValidateNotNull wordt** gebruikt. Gebruik voor dit scenario **de ValidateNotNullOrEmpty**

In het volgende voorbeeld mag de waarde van de **id-parameter** niet `$null` zijn.

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a>Validatiekenmerk ValidateNotNullOrEmpty

Het **kenmerk ValidateNotNullOrEmpty** geeft aan dat de parameterwaarde niet mag zijn en geen `$null` lege tekenreeks () mag `""` zijn. PowerShell genereert een fout als de parameter wordt gebruikt in een functie-aanroep, maar de waarde ervan is , een lege tekenreeks `$null` ( ) of een lege matrix `""` `@()` .

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a>Validatiekenmerk ValidateDrive

Het **kenmerk ValidateDrive** geeft aan dat de parameterwaarde het pad moet vertegenwoordigen, dat alleen verwijst naar toegestane stations. PowerShell genereert een fout als de parameterwaarde verwijst naar andere stations dan de toegestane. Het bestaan van het pad, met uitzondering van het station zelf, wordt niet geverifieerd.

Als u een relatief pad gebruikt, moet het huidige station in de lijst met toegestane station.

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a>Validatiekenmerk ValidateUserDrive

Het **kenmerk ValidateUserDrive** geeft aan dat de parameterwaarde het pad moet vertegenwoordigen, dat verwijst naar `User` station. PowerShell genereert een fout als het pad naar een ander station verwijst. Het validatiekenmerk test alleen op het bestaan van het stationgedeelte van het pad.

Als u een relatief pad gebruikt, moet het huidige station `User` zijn.

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

U kunt het `User` station definiëren in JEA-sessieconfiguraties (Just Enough Administration). Voor dit voorbeeld maken we het station Gebruiker: .

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

### <a name="validatetrusteddata-validation-attribute"></a>Validatiekenmerk ValidateTrustedData

Dit kenmerk is toegevoegd in PowerShell 6.1.1.

Op dit moment wordt het kenmerk intern gebruikt door PowerShell zelf en is het niet bedoeld voor extern gebruik.

## <a name="dynamic-parameters"></a>Dynamische parameters

Dynamische parameters zijn parameters van een cmdlet, functie of script die alleen onder bepaalde voorwaarden beschikbaar zijn.

Zo hebben verschillende provider-cmdlets parameters die alleen beschikbaar zijn wanneer de cmdlet wordt gebruikt in het providerstation of in een bepaald pad van het providerstation. De parameter **Encoding** is bijvoorbeeld alleen beschikbaar voor de cmdlets , en wanneer deze wordt gebruikt `Add-Content` `Get-Content` in een `Set-Content` bestandssysteemstation.

U kunt ook een parameter maken die alleen wordt weergegeven wanneer een andere parameter wordt gebruikt in de functieopdracht of wanneer een andere parameter een bepaalde waarde heeft.

Dynamische parameters kunnen handig zijn, maar ze alleen gebruiken wanneer dat nodig is, omdat ze moeilijk te vinden zijn voor gebruikers. Als u een dynamische parameter wilt zoeken, moet de gebruiker zich in het pad van de provider, de parameter **ArgumentList** van de `Get-Command` cmdlet gebruiken of de parameter **Path** van `Get-Help` gebruiken.

Gebruik het trefwoord om een dynamische parameter voor een functie of script `DynamicParam` te maken.

De syntaxis is als volgt:

`DynamicParam {<statement-list>}`

Gebruik in de lijst met -instructie een `If` -instructie om de voorwaarden op te geven waaronder de parameter beschikbaar is in de functie.

Gebruik de `New-Object` cmdlet om een **System.Management.Automation.RuntimeDefinedParameter-object** te maken dat de parameter vertegenwoordigt en de naam ervan opgeeft.

U kunt een opdracht gebruiken om een `New-Object` **System.Management.Automation.ParameterAttribute-object** te maken om kenmerken van de parameter weer te geven, zoals **Verplicht**, **Positie** of **ValueFromPipeline** of de parameterset.

In het volgende voorbeeld ziet u een voorbeeldfunctie met standaardparameters met de naam **Naam** en **Pad,** en een optionele dynamische parameter met de **naam DP1.** De **parameter DP1** staat in de `PSet1` parameterset en heeft het type `Int32` .
De **DP1** parameter is alleen beschikbaar in de functie wanneer de waarde van de pad parameter begint met , waarmee wordt aangegeven dat deze wordt gebruikt `Get-Sample` in het  `HKLM:` `HKEY_LOCAL_MACHINE` registerstation.

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

Zie [RuntimeDefinedParameter voor meer informatie.](/dotnet/api/system.management.automation.runtimedefinedparameter)

## <a name="switch-parameters"></a>Schakelen tussen parameters

Switchparameters zijn parameters zonder parameterwaarde. Ze zijn alleen effectief wanneer ze worden gebruikt en hebben slechts één effect.

De parameter **NoProfile van** powershell.exe **is** bijvoorbeeld een switchparameter.

Als u een switchparameter in een functie wilt maken, geeft u `Switch` het type op in de parameterdefinitie.

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

Switchparameters zijn eenvoudig te gebruiken en hebben de voorkeur boven Booleaanse parameters, die een moeilijkere syntaxis hebben.

Als u bijvoorbeeld een switchparameter wilt gebruiken, moet de gebruiker de parameter in de opdracht typen.

`-IncludeAll`

Als u een Booleaanse parameter wilt gebruiken, geeft de gebruiker de parameter en een Booleaanse waarde op.

`-IncludeAll:$true`

Kies bij het maken van switchparameters de parameternaam zorgvuldig. Zorg ervoor dat de parameternaam het effect van de parameter aan de gebruiker doorgeeft.
Vermijd niet-eenduidige termen, zoals **Filter** of **Maximum,** die kunnen impliceren dat een waarde vereist is.

## <a name="argumentcompleter-attribute"></a>ArgumentCompleter-kenmerk

Met **het kenmerk ArgumentCompleter** kunt u tabinvullingswaarden toevoegen aan een specifieke parameter. Er **moet een kenmerk ArgumentCompleter** worden gedefinieerd voor elke parameter die tab-voltooiing nodig heeft. Net als **bij DynamicParameters** worden de beschikbare waarden berekend tijdens runtime wanneer de gebruiker op <kbd>Tab drukt</kbd> na de parameternaam.

Als u een **ArgumentCompleter-kenmerk** wilt toevoegen, moet u een scriptblok definiëren dat de waarden bepaalt. Het scriptblok moet de volgende parameters hebben in de onderstaande volgorde. De namen van de parameter zijn niet van belang omdat de waarden positioneel worden opgegeven.

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

### <a name="argumentcompleter-script-block"></a>ArgumentCompleter-scriptblok

De parameters voor het scriptblok zijn ingesteld op de volgende waarden:

- `$commandName` (Positie 0) - Deze parameter is ingesteld op de naam van de opdracht waarvoor het scriptblok tab-voltooiing biedt.
- `$parameterName` (Positie 1) - Deze parameter is ingesteld op de parameter waarvan de waarde tab-voltooiing vereist.
- `$wordToComplete` (Positie 2) - Deze parameter is ingesteld op de waarde die de gebruiker heeft opgegeven voordat deze op <kbd>Tab heeft gedrukt.</kbd> Uw scriptblok moet deze waarde gebruiken om tab-voltooiingswaarden te bepalen.
- `$commandAst` (Positie 3) - Deze parameter is ingesteld op de Abstract Syntax Tree (AST) voor de huidige invoerregel. Zie [Ast Class voor meer informatie.](/dotnet/api/system.management.automation.language.ast)
- `$fakeBoundParameters` (Positie 4) - Deze parameter is ingesteld op een hashtabel met de voor de `$PSBoundParameters` cmdlet voordat de gebruiker op Tab heeft <kbd>gedrukt.</kbd> Zie voor meer informatie [about_Automatic_Variables](about_Automatic_Variables.md).

Het **scriptblok ArgumentCompleter** moet de waarden uitschrijven met behulp van de pijplijn, zoals `ForEach-Object` , of een andere geschikte `Where-Object` methode.
Het retourneren van een matrix met waarden  zorgt ervoor dat PowerShell de hele matrix als één tab-voltooiingswaarde behandelt.

In het volgende voorbeeld wordt tab-aanvulling toegevoegd aan de parameter **Value.** Als alleen de **parameter Waarde** is opgegeven, worden alle mogelijke waarden of argumenten voor **Waarde** weergegeven. Wanneer de **parameter Type** is opgegeven, geeft de parameter **Waarde** alleen de mogelijke waarden voor dat type weer.

Bovendien zorgt de operator ervoor dat als de gebruiker de volgende opdracht intimpt en `-like` <kbd>Tab-voltooiing</kbd> gebruikt, alleen **Apple** wordt geretourneerd.

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
