---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Aangepaste typen maken met PowerShell-klassen
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470933"
---
# <a name="creating-custom-types-using-powershell-classes"></a>Aangepaste typen maken met PowerShell-klassen

PowerShell 5.0 de mogelijkheid voor het definiëren van klassen en andere door de gebruiker gedefinieerde typen met behulp van formele syntaxis en semantiek net als andere programmeertalen objectgeoriënteerde toegevoegd. Het doel is om in te schakelen van ontwikkelaars en IT-professionals Profiteer van PowerShell voor een breder scala aan toepassingen, Vereenvoudig de ontwikkeling van PowerShell-artefacten (zoals DSC-resources) en de dekking van management oppervlakken versnellen.

## <a name="supported-scenarios-in-this-release"></a>Ondersteunde scenario's in deze release

- DSC-resources en hun bijbehorende typen definiëren met behulp van de PowerShell-taal
- Aangepaste typen definiëren in PowerShell met behulp van bekende objectgeoriënteerde programming-constructs, zoals klassen, eigenschappen, methoden, enzovoort.
- Ondersteuning voor overname van met de klasse in PowerShell en de klasse base DSC-resource
- Fouten opsporen in typen met behulp van de PowerShell-taal
- Genereren en uitzonderingen verwerken met behulp van formele mechanismen en op het juiste niveau

## <a name="declare-base-class"></a>Basisklasse declareren

Als een basistype op voor een andere PowerShell-klasse kunt u een PowerShell-klasse declareren.

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

U kunt ook bestaande .NET Framework-typen gebruiken als basisklassen:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a>Klasseconstructor oproepbasis

Als u wilt een oproepbasis aanroepen vanuit een subklasse, gebruikt u het sleutelwoord **basis**:

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

Als een basisklasse heeft een standaardconstructor (Er is geen parameter), kunt u een expliciete constructoraanroep weglaten:

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a>Klassemethode oproepbasis

U kunt bestaande methoden in subklassen overschrijven. U doet dit door methoden met behulp van dezelfde naam en handtekening te declareren:

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

Voor het aanroepen van methoden van de basisklasse van overschreven-implementaties, geconverteerd naar de basisklasse (`[baseClass]$this`) op voor aanroepen:

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

Alle methoden voor PowerShell zijn virtueel. U kunt niet-virtuele .NET-methoden in een subklasse verbergen met behulp van dezelfde syntaxis als voor een onderdrukking, door op te geven van methoden met dezelfde naam en handtekening.

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="declare-implemented-interface"></a>Geïmplementeerde interface declareren

U kunt geïmplementeerde interfaces aangeven na basistypen of onmiddellijk nadat een dubbele punt (:), als er geen basistype dat is opgegeven. Alle namen worden gescheiden door komma's. Het is vergelijkbaar met C# syntaxis.

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="new-language-features-in-powershell-50"></a>Nieuwe taalfuncties in PowerShell 5.0

PowerShell 5.0 introduceert de volgende nieuwe taalelementen in PowerShell:

### <a name="class-keyword"></a>Klasse trefwoord

De `class` sleutelwoord definieert een nieuwe klasse. Dit is een echte .NET Framework-type. Klasseleden zijn openbaar, maar alleen openbaar binnen het modulebereik. U mag niet verwijzen naar de naam van het als een tekenreeks (bijvoorbeeld `New-Object` niet werkt), en in deze release kunt u een letterlijke type niet gebruiken (bijvoorbeeld `[MyClass]`) buiten het script of een module-bestand waarin de klasse is gedefinieerd.

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Enum sleutelwoord en opsommingen

Ondersteuning voor de `enum` sleutelwoord is toegevoegd, waarbij nieuwe regel wordt gebruikt als het scheidingsteken. U kunt geen op dit moment een enumerator voor wat betreft zelf definiëren. U kunt echter een enum-waarde in termen van een andere enum initialiseren, zoals wordt weergegeven in het volgende voorbeeld. Bovendien kan het basistype kan niet worden opgegeven; het is altijd `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

De enumeratorwaarde van een moet een constante parseren. U kunt deze niet instellen op het resultaat van een aangeroepen opdracht.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Enum-waarden ondersteunt rekenkundige bewerkingen, zoals wordt weergegeven in het volgende voorbeeld.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Sleutelwoorden import-dscresource bieden

`Import-DscResource` is nu een waar dynamische trefwoord. PowerShell parseert basismodule van de opgegeven module, zoeken naar klassen die bevatten de **sleutelwoorden dscresource bieden** kenmerk.

### <a name="implementingassembly"></a>ImplementingAssembly

Een nieuw veld **ImplementingAssembly**, is toegevoegd aan **ModuleInfo**. Deze waarde is ingesteld op de dynamische verzameling voor een scriptmodule gemaakt als het script klassen definieert, of de geladen assembly voor binaire modules. Het is niet ingesteld als **ModuleType** is **Manifest**.

Na te denken over de **ImplementingAssembly** veld resources in een module heeft gedetecteerd. Dit betekent dat u kunt de resources die zijn geschreven in PowerShell of andere beheerde talen detecteren.

Velden met initializers:

```powershell
[int] $i = 5
```

`Static` wordt ondersteund. Het werkt als een kenmerk, zoals de typebeperkingen dat wel doet. Deze kan in willekeurige volgorde worden opgegeven.

```powershell
static [int] $count = 0
```

Een type is optioneel.

```powershell
$s = "hello"
```

Alle leden van de zijn openbaar.

### <a name="constructors-and-instantiation"></a>Constructors en instantiëring

PowerShell-klassen kunnen constructors hebben. Ze hebben dezelfde naam als de klasse. Constructors kunnen worden overbelast. Statische constructors worden ondersteund. Eigenschappen met expressies voor objectinitialisatie geïnitialiseerd voordat u code uitvoert in een constructor. Statische eigenschappen worden geïnitialiseerd voordat de hoofdtekst van een statische constructor en instantie-eigenschappen zijn geïnitialiseerd voordat de hoofdtekst van de niet-statische-constructor. Er is momenteel geen syntaxis voor het aanroepen van een constructor vanuit een andere constructor (zoals de C\# syntaxis ': this()"). De tijdelijke oplossing is voor het definiëren van een algemene `Init()` methode.

#### <a name="creating-instances"></a>Het maken van instanties

> [!NOTE]
> In PowerShell 5.0 `New-Object` werkt niet met klassen die zijn gedefinieerd in PowerShell. De naam van het is ook alleen zichtbaar lexicaal, wat betekent dat deze zijn niet zichtbaar is buiten de module of het script dat de klasse definieert. Functies kunnen exemplaren van een klasse is gedefinieerd in PowerShell retourneren. Deze instanties werken buiten de module of het script.

1. Instantiëren met behulp van de standaardconstructor.

   ```powershell
   $a = [MyClass]::new()
   ```

1. Aanroepen van een constructor met een parameter

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. Een matrix doorgegeven aan een constructor met meerdere parameters.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

De pseudo statische methode `new()` werkt met .NET-typen, zoals wordt weergegeven in het volgende voorbeeld.

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a>Detectie van constructors

U ziet nu de constructor overloads met `Get-Member`, of zoals in dit voorbeeld:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static` Geeft een lijst van constructors, zodat u overloads, zoals een andere methode kunt bekijken. De prestaties van deze syntaxis werkt ook aanzienlijk sneller dan `New-Object`.

### <a name="methods"></a>Methoden

Een PowerShell-methode de klasse wordt geïmplementeerd als een **ScriptBlock** waarvoor alleen een end-blok. Alle methoden zijn openbaar. De volgende toont een voorbeeld van het definiëren van een methode met de naam **DoeIets**.

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

Aanroepen van de methode:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Overbelaste methoden worden ook ondersteund.

### <a name="properties"></a>Eigenschappen

Alle eigenschappen zijn openbaar. Eigenschappen van vereist een nieuwe regel of door puntkomma's. Als er geen objecttype is opgegeven, is het type object.

Eigenschappen die validatie of argument transformatie-kenmerken worden gebruikt (zoals `[ValidateSet("aaa")]`) werkt zoals verwacht.

### <a name="hidden"></a>Verborgen

Een nieuw sleutelwoord, `Hidden`, is toegevoegd. `Hidden` kan worden toegepast op eigenschappen en methoden (met inbegrip van constructors).

Verborgen leden openbaar zijn, maar worden niet weergegeven in de uitvoer van `Get-Member` , tenzij de `-Force` parameter is toegevoegd. Verborgen leden zijn niet opgenomen wanneer tabblad voltooien of met behulp van Intellisense, tenzij de voltooiing vindt plaats in de klasse voor het definiëren van het verborgen lid.

Een nieuw kenmerk **System.Management.Automation.HiddenAttribute** is toegevoegd, die C\# code kan hebben dezelfde semantiek in PowerShell.

### <a name="return-types"></a>Typen retourneren

Retourtype is een contract. De geretourneerde waarde wordt geconverteerd naar het verwachte type. Als er geen retourtype is opgegeven, wordt het retourtype is **void**. Er is geen streaming-objecten. Objecten kunnen niet worden geschreven naar de pijplijn opzettelijk of per ongeluk.

### <a name="attributes"></a>Kenmerken

Twee nieuwe kenmerken, **sleutelwoorden dscresource bieden** en **DscProperty** zijn toegevoegd.

### <a name="lexical-scoping-of-variables"></a>Lexicale bereik van variabelen

Hieronder ziet u een voorbeeld van hoe lexicale scoping werken in deze release.

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a>Voorbeeld van de end-to-End

Het volgende voorbeeld wordt een aangepaste klassen voor het implementeren van een HTML-dynamische taal van het opmaakmodel (DSL). Het voorbeeld wordt vervolgens ondersteunende functies voor het maken van specifieke elementtypen als onderdeel van de elementklasse, zoals opmaakprofielen en tabellen, omdat de typen kunnen niet worden gebruikt buiten het bereik van een module.

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```
