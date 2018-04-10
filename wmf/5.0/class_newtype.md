---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 85e9206ffef76fb4bd7714d847888e6e5bbcc4ec
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="new-language-features-in-powershell-50"></a>Nieuwe taalfuncties in PowerShell 5.0

PowerShell 5.0 introduceert de volgende nieuwe taalelementen in Windows PowerShell:

## <a name="class-keyword"></a>Klasse sleutelwoord

De **klasse** sleutelwoord definieert een nieuwe klasse. Dit is een echte .NET Framework-type.
Klasseleden zijn openbaar, maar alleen openbare binnen het modulebereik.
U mag niet verwijzen naar de typenaam als tekenreeks (bijvoorbeeld `New-Object` niet werkt), en in deze release kunt u een letterlijke waarde van het type niet gebruiken (bijvoorbeeld `[MyClass]`) buiten het scriptmodule /-bestand waarin de klasse is gedefinieerd.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Enum-sleutelwoord en opsommingen

Ondersteuning voor de **enum** sleutelwoord is toegevoegd, waarbij nieuwe regel wordt gebruikt als scheidingsteken.
Huidige beperkingen: u kunt een enumerator in termen van zelf niet definiëren, maar u kunt een enum in termen van een andere enum initialiseren, zoals wordt weergegeven in het volgende voorbeeld.
Het basistype kan niet ook op dat moment worden opgegeven; het is altijd [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Een enumeratorwaarde moet een constante parse; u kunt deze niet instellen op het resultaat van een opdracht aangeroepen.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Enums ondersteuning voor rekenkundige bewerkingen, zoals wordt weergegeven in het volgende voorbeeld.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a>Import-DscResource

**Importeren DscResource** is nu een waar dynamische sleutelwoord.
PowerShell parseert de opgegeven module root-module, zoeken naar klassen die bevatten de **DscResource** kenmerk.

## <a name="implementingassembly"></a>ImplementingAssembly

Een nieuw veld **ImplementingAssembly**, is toegevoegd aan ModuleInfo. Het is ingesteld op de dynamische assembly voor een scriptmodule gemaakt als het script klassen gedefinieerd of de assembly geladen voor binaire modules. Het is niet ingesteld als ModuleType = Manifest.

Na te denken over de **ImplementingAssembly** veld detecteert resources in een module. Dit betekent dat u de resources die zijn geschreven in PowerShell of andere beheerde talen kunt detecteren.

De velden met initalisatiefuncties:

```powershell
[int] $i = 5
```

Statische ondersteund. Dit werkt als een kenmerk, evenals de typebeperkingen, zodat deze kan worden opgegeven in een willekeurige volgorde.

```powershell
static [int] $count = 0
```

Een type is optioneel.

```powershell
$s = "hello"
```

Alle leden zijn openbaar.

## <a name="constructors-and-instantiation"></a>Constructors en instantiëring

Windows PowerShell-klassen kunnen hebben constructors; ze hebben dezelfde naam als de klasse. Constructors kunnen overbelast. Statische constructors worden ondersteund. Eigenschappen met initialisatie-expressies zijn geïnitialiseerd voordat code wordt uitgevoerd in een constructor. Statische eigenschappen worden geïnitialiseerd voordat de hoofdtekst van een statische constructor en eigenschappen van objectexemplaar zijn geïnitialiseerd voordat de hoofdtekst van de niet-statische constructor. Er is momenteel geen syntaxis voor een constructor aanroept vanuit een andere constructor (zoals de C\# syntaxis ': this()"). De tijdelijke oplossing is voor het definiëren van een algemene Init-methode.

De volgende zijn manieren instantiëren van klassen in deze release.

Instantiëren met behulp van de standaardconstructor. Houd er rekening mee New-Object wordt niet ondersteund in deze release.

```powershell
$a = [MyClass]::new()
```

Aanroepen van een constructor met een parameter

```powershell
$b = [MyClass]::new(42)
```

Een matrix doorgeven aan een constructor met meerdere parameters
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

In deze release werkt New-Object niet met de klassen die zijn gedefinieerd in Windows PowerShell. Ook voor deze release is de typenaam alleen zichtbaar lexically, wat betekent dat het is niet zichtbaar zijn buiten de module of het script dat de klasse definieert. Functies exemplaren van een klasse is gedefinieerd in Windows PowerShell kunnen terugkeren en exemplaren werken goed buiten de module of het script.

`Get-Member -Static` Geeft een lijst constructors, zodat u overloads zoals een andere methode kunt bekijken. De prestaties van deze syntaxis werkt ook aanzienlijk sneller dan New-Object.

De pseudo statische methode met de naam **nieuwe** werkt met .NET-typen, zoals wordt weergegeven in het volgende voorbeeld.

```powershell
[hashtable]::new()
```

U kunt nu zien constructor overloads met Get-lid of zoals in dit voorbeeld wordt weergegeven:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a>Methoden

De methode van een Windows PowerShell-klasse wordt geïmplementeerd als een ScriptBlock met alleen een end-blok. Alle methoden zijn openbaar. Hieronder vindt u een voorbeeld van het definiëren van een methode met de naam **DoeIets**.

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

De methodeaanroep:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Overbelaste methoden--dat wil zeggen, die hetzelfde zijn als een bestaande methode met de naam, maar met de opgegeven waarden--onderscheiden worden ook ondersteund.

## <a name="properties"></a>Eigenschappen

Alle eigenschappen zijn openbaar. Eigenschappen vereisen een nieuwe regel of een puntkomma. Als er geen objecttype is opgegeven, is het eigenschapstype-object.

Eigenschappen die validatie kenmerken of argument transformatie kenmerken worden gebruikt (bijvoorbeeld `[ValidateSet("aaa")]`) werkt zoals verwacht.

## <a name="hidden"></a>Verborgen

Een nieuw trefwoord **Hidden**, is toegevoegd. **Verborgen** kunnen worden toegepast op eigenschappen en methoden (inclusief constructors).

Verborgen leden zijn openbaar, maar worden niet weergegeven in de uitvoer van Get-lid, tenzij de - Force parameter wordt toegevoegd.

Verborgen leden zijn niet opgenomen wanneer tabblad voltooien of met behulp van Intellisense tenzij de voltooiing van deze gebeurtenis treedt op in de klasse voor het definiëren van het verborgen lid.

Een nieuw kenmerk **System.Management.Automation.HiddenAttribute** is toegevoegd zodat C#-code dezelfde betekenis in Windows PowerShell hebben kunt.

## <a name="return-types"></a>Retourtypen

Retourtype is een contract; de retourwaarde wordt geconverteerd naar het verwachte type. Als er geen retourtype is opgegeven, is het retourtype void. Er is geen streaming-objecten. objecten kunnen niet worden geschreven naar de pijplijn opzettelijk of per ongeluk.

## <a name="attributes"></a>Kenmerken

Twee nieuwe kenmerken **DscResource** en **DscProperty** zijn toegevoegd.

## <a name="lexical-scoping-of-variables"></a>Lexicale bereik van variabelen

De volgende toont een voorbeeld van hoe lexicale bereik werken in deze release.

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

## <a name="end-to-end-example"></a>End-to-End-voorbeeld

Het volgende voorbeeld maakt diverse nieuwe, aangepaste klassen voor het implementeren van een HTML-dynamische taal van het opmaakmodel (DSL).
Het voorbeeld wordt vervolgens hulpfuncties voor het maken van specifieke elementtypen als onderdeel van de elementklasse zoals kopstijlen en tabellen, omdat de typen kunnen niet worden gebruikt buiten het bereik van een module.

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
# These are required because types aren’t visible outside of the module.
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
        TR (-join $Properties.Foreach{ TD ($row.$\_) } )
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