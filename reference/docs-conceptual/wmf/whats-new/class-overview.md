---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Aangepaste typen maken met PowerShell-klassen
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71145199"
---
# <a name="creating-custom-types-using-powershell-classes"></a>Aangepaste typen maken met PowerShell-klassen

Power shell 5,0 heeft de mogelijkheid om klassen en andere door de gebruiker gedefinieerde typen te definiëren met behulp van formele syntaxis en semantiek, zoals andere objectgeoriënteerd programmeer talen. Het doel is om ontwikkel aars en IT-professionals in staat te stellen Power shell te gebruiken voor een breder scala aan gebruiks voorbeelden, het ontwikkelen van Power shell-artefacten (zoals DSC-resources) te vereenvoudigen en de dekking van management-Opper vlakken te versnellen.

## <a name="supported-scenarios-in-this-release"></a>Ondersteunde scenario's in deze release

- DSC-resources en de bijbehorende typen definiëren met behulp van de Power shell-taal
- Aangepaste typen in Power shell definiëren met behulp van vertrouwde object georiënteerde Programmeer constructies, zoals klassen, eigenschappen, methoden, enzovoort.
- Overname ondersteuning voor de klasse in Power shell en Class base DSC resource
- Typen fout opsporing met behulp van de Power shell-taal
- Uitzonde ringen genereren en verwerken met behulp van formele mechanismen en op het juiste niveau

## <a name="declare-base-class"></a>Basisklasse declareren

U kunt een Power shell-klasse declareren als basis type voor een andere Power shell-klasse.

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

U kunt ook bestaande .NET Framework typen als basis klassen gebruiken:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a>Klasseconstructor oproepbasis

Als u een basis klasse-constructor vanuit een subklasse wilt aanroepen, gebruikt u de **basis**sleutel woord:

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

Als een basis klasse een standaard-constructor (geen para meter) heeft, kunt u een expliciete aanroep van een constructor weglaten:

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a>Klassemethode oproepbasis

U kunt bestaande methoden in subklassen overschrijven. Om dit te doen, declareert u methoden met dezelfde naam en hand tekening:

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

Voor het aanroepen van basis klassen methoden van overschreven implementaties, Casting naar`[baseClass]$this`de basis klasse () op aanroepen:

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

Alle Power shell-methoden zijn virtueel. U kunt niet-virtuele .NET-methoden in een subklasse verbergen door dezelfde syntaxis te gebruiken als voor een onderdrukking, door methoden te declareren met dezelfde naam en hand tekening.

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

U kunt geïmplementeerde interfaces na basis typen of direct na een dubbele punt (:) declareren als er geen basis type is opgegeven. Scheid alle type namen met behulp van komma's. Het is vergelijkbaar met de syntaxis van C#.

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

## <a name="new-language-features-in-powershell-50"></a>Nieuwe taal functies in Power shell 5,0

Power shell 5,0 introduceert de volgende nieuwe taal elementen in Power shell:

### <a name="class-keyword"></a>Tref woord klasse

Het `class` sleutel woord definieert een nieuwe klasse. Dit is een True .NET Framework type. Klasse-leden zijn openbaar, maar alleen openbaar binnen het module bereik. U kunt niet naar de type naam verwijzen als een teken reeks (bijvoorbeeld `New-Object` niet werkt), en in deze release kunt u geen letterlijke type waarde (bijvoorbeeld `[MyClass]`) gebruiken buiten het script of module bestand waarin de klasse is gedefinieerd.

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Tref woord en opsommingen inventariseren

Ondersteuning voor het `enum` tref woord is toegevoegd. Dit maakt gebruik van een nieuwe regel als scheidings teken. Op dit moment kunt u geen enumerator definiëren in termen van zichzelf. U kunt echter een Enum initialiseren in termen van een andere Enum, zoals wordt weer gegeven in het volgende voor beeld. Het basis type kan ook niet worden opgegeven. het is altijd `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Een enumerator-waarde moet een geparseerd tijd constante zijn. U kunt deze niet instellen op het resultaat van een aangeroepen opdracht.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Opsommingen bieden ondersteuning voor reken kundige bewerkingen, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Import-Dscresource bieden

`Import-DscResource`is nu een echt dynamisch sleutel woord. Power shell parseert de hoofd module van de opgegeven module. er wordt gezocht naar klassen die het kenmerk **dscresource bieden** bevatten.

### <a name="implementingassembly"></a>ImplementingAssembly

Er is een nieuw veld, **ImplementingAssembly**, toegevoegd aan **ModuleInfo**. Deze wordt ingesteld op de dynamische assembly die is gemaakt voor een script module als het script klassen definieert, of de geladen assembly voor binaire modules. Het is niet ingesteld wanneer **module type** is **manifest**.

Reflectie in het veld **ImplementingAssembly** detecteert bronnen in een module. Dit betekent dat u resources kunt detecteren die in Power shell of andere beheerde talen zijn geschreven.

Velden met initialisatie functies:

```powershell
[int] $i = 5
```

`Static`wordt ondersteund. Het werkt als een kenmerk, zoals de type beperkingen. Dit kan in een wille keurige volg orde worden opgegeven.

```powershell
static [int] $count = 0
```

Een type is optioneel.

```powershell
$s = "hello"
```

Alle leden zijn openbaar.

### <a name="constructors-and-instantiation"></a>Constructors en instantiëring

Power shell-klassen kunnen constructors hebben. Ze hebben dezelfde naam als hun klasse. Constructors kunnen overbelast zijn. Statische Constructors worden ondersteund. Eigenschappen met initialisatie-expressies worden geïnitialiseerd voordat code in een constructor wordt uitgevoerd. Statische eigenschappen worden geïnitialiseerd voordat de hoofd tekst van een statische constructor, en instantie-eigenschappen worden geïnitialiseerd vóór de hoofd tekst van de niet-statische constructor. Op dit moment is er geen syntaxis voor het aanroepen van een constructor vanuit een andere constructor (\# zoals de C-syntaxis ": This ()"). De tijdelijke oplossing is het definiëren van `Init()` een algemene methode.

#### <a name="creating-instances"></a>Instanties maken

> [!NOTE]
> In Power shell 5,0 `New-Object` werkt niet met klassen die in Power shell zijn gedefinieerd. De type naam is ook op een lexicale zicht bare locatie, wat betekent dat deze niet zichtbaar is buiten de module of het script waarmee de klasse wordt gedefinieerd. Functies kunnen exemplaren retour neren van een klasse die is gedefinieerd in Power shell. Deze instanties werken buiten de module of het script.

1. Instantiëren met behulp van de standaardconstructor.

   ```powershell
   $a = [MyClass]::new()
   ```

1. Een constructor met een para meter aanroepen

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. Een matrix wordt door gegeven aan een constructor met meerdere para meters.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

De pseudo-statische methode `new()` werkt met .net-typen, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a>Constructors detecteren

U kunt nu overbelasting van constructor zien met `Get-Member`, of zoals in dit voor beeld wordt weer gegeven:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static`Hierin worden constructors weer gegeven, zodat u Overloads kunt bekijken, zoals een andere methode. De prestaties van deze syntaxis zijn ook aanzienlijk sneller dan `New-Object`.

### <a name="methods"></a>Methoden

Een Power shell-klassen methode wordt geïmplementeerd als een **script Block** die alleen een eind blok heeft. Alle methoden zijn openbaar. Hieronder ziet u een voor beeld van het definiëren van een methode met de naam **DoSomething**.

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

Aanroep methode:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Overbelaste methoden worden ook ondersteund.

### <a name="properties"></a>Eigenschappen

Alle eigenschappen zijn openbaar. Eigenschappen vereisen een nieuwe regel of een punt komma. Als er geen object type is opgegeven, is het eigenschaps type object.

Eigenschappen die gebruikmaken van validatie-of argument transformatie kenmerken `[ValidateSet("aaa")]`(zoals) werken zoals verwacht.

### <a name="hidden"></a>Verborgen

Er is een nieuw `Hidden`tref woord,, toegevoegd. `Hidden`kan worden toegepast op Eigenschappen en methoden (inclusief constructors).

Verborgen leden zijn openbaar, maar worden niet weer gegeven in de uitvoer `Get-Member` van tenzij `-Force` de para meter is toegevoegd. Verborgen leden worden niet opgenomen wanneer het tabblad wordt voltooid of gebruikmaakt van IntelliSense, tenzij de voltooiing plaatsvindt in de klasse die het verborgen lid definieert.

Er is een nieuw kenmerk, **System. Management. Automation. HiddenAttribute** toegevoegd, zodat\# de C-code dezelfde semantiek kan hebben in Power shell.

### <a name="return-types"></a>Retour typen

Retour type is een contract. De geretourneerde waarde wordt geconverteerd naar het verwachte type. Als er geen retour type is opgegeven, is het retour type **void**. Er zijn geen streaming van-objecten. Objecten kunnen niet opzettelijk of per ongeluk naar de pijp lijn worden geschreven.

### <a name="attributes"></a>Kenmerken

Er zijn twee nieuwe kenmerken, **dscresource bieden** en **DscProperty** toegevoegd.

### <a name="lexical-scoping-of-variables"></a>Lexicale bereik van variabelen

Hieronder ziet u een voor beeld van hoe lexicale scoping werkt in deze release.

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

## <a name="end-to-end-example"></a>End-to-end-voor beeld

In het volgende voor beeld worden een aantal aangepaste klassen gemaakt voor het implementeren van een HTML Dynamic style sheet-taal (DSL). Vervolgens voegt het voor beeld hulp functies toe om specifieke element typen te maken als onderdeel van de klasse element, zoals kopstijlen en tabellen, omdat typen niet buiten het bereik van een module kunnen worden gebruikt.

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
