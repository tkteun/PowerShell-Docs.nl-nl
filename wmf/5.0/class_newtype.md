---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: a96a4a58dafa01fb43f5bdffb52ef833816148e7
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587292"
---
# <a name="new-language-features-in-powershell-50"></a>Nieuwe taalfuncties in PowerShell 5.0

PowerShell 5.0 introduceert de volgende nieuwe taalelementen in Windows PowerShell:

## <a name="class-keyword"></a>Klasse trefwoord

De **klasse** sleutelwoord definieert een nieuwe klasse. Dit is een echte .NET Framework-type.
Klasseleden zijn openbaar, maar alleen openbaar binnen het modulebereik.
U mag niet verwijzen naar de naam van het als een tekenreeks (bijvoorbeeld `New-Object` niet werkt), en in deze release kunt u een letterlijke type niet gebruiken (bijvoorbeeld `[MyClass]`) buiten de scriptmodule /-bestand waarin de klasse is gedefinieerd.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Enum sleutelwoord en opsommingen

Ondersteuning voor de **enum** sleutelwoord is toegevoegd, waarbij nieuwe regel wordt gebruikt als het scheidingsteken.
Huidige beperkingen: u kunt een enumerator voor wat betreft zelf niet definiëren, maar kunt u een enum-waarde in termen van een andere enum initialiseren, zoals wordt weergegeven in het volgende voorbeeld.
Het basistype kan niet ook op dat moment worden opgegeven; het is altijd [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Een enumerator voor de waarde moet een constante parseren; u kunt deze niet instellen op het resultaat van een aangeroepen opdracht.

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

## <a name="import-dscresource"></a>Sleutelwoorden import-dscresource bieden

**Sleutelwoorden import-dscresource bieden** is nu een waar dynamische trefwoord.
PowerShell parseert basismodule van de opgegeven module, zoeken naar klassen die bevatten de **sleutelwoorden dscresource bieden** kenmerk.

## <a name="implementingassembly"></a>ImplementingAssembly

Een nieuw veld **ImplementingAssembly**, is toegevoegd aan ModuleInfo. Deze waarde is ingesteld op de dynamische verzameling voor een scriptmodule gemaakt als het script klassen definieert, of de geladen assembly voor binaire modules. Het is niet ingesteld als ModuleType = Manifest.

Na te denken over de **ImplementingAssembly** veld resources in een module heeft gedetecteerd. Dit betekent dat u kunt de resources die zijn geschreven in PowerShell of andere beheerde talen detecteren.

Velden met initializers:

```powershell
[int] $i = 5
```

Statische ondersteund. het werkt als een kenmerk, zoals de typebeperkingen, dat wel doet, zodat deze kan worden opgegeven in een willekeurige volgorde.

```powershell
static [int] $count = 0
```

Een type is optioneel.

```powershell
$s = "hello"
```

Alle leden van de zijn openbaar.

## <a name="constructors-and-instantiation"></a>Constructors en instantiëring

Windows PowerShell-klassen kunnen constructors; hebben ze hebben dezelfde naam als de klasse. Constructors kunnen worden overbelast. Statische constructors worden ondersteund. Eigenschappen met expressies voor objectinitialisatie geïnitialiseerd voordat u code uitvoert in een constructor. Statische eigenschappen worden geïnitialiseerd voordat de hoofdtekst van een statische constructor en instantie-eigenschappen zijn geïnitialiseerd voordat de hoofdtekst van de niet-statische-constructor. Er is momenteel geen syntaxis voor het aanroepen van een constructor vanuit een andere constructor (zoals de C\# syntaxis ': this()"). De tijdelijke oplossing is voor het definiëren van een algemene Init-methode.

De volgende zijn manieren van het instantiëren van klassen in deze release.

Instantiëren met behulp van de standaardconstructor. Houd er rekening mee dat New-Object niet wordt ondersteund in deze release.

```powershell
$a = [MyClass]::new()
```

Aanroepen van een constructor met een parameter

```powershell
$b = [MyClass]::new(42)
```

Een matrix wordt doorgegeven aan de constructor met meerdere parameters
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

In deze release werkt het New-Object niet met klassen die zijn gedefinieerd in Windows PowerShell. Ook voor deze release is de typenaam alleen zichtbaar lexicaal, wat betekent dat deze zijn niet zichtbaar is buiten de module of het script dat de klasse definieert. Functies kunnen retourneren exemplaren van een klasse is gedefinieerd in Windows PowerShell en exemplaren werken ook buiten de module of het script.

`Get-Member -Static` Geeft een lijst van constructors, zodat u overloads, zoals een andere methode kunt bekijken. De prestaties van deze syntaxis is ook aanzienlijk sneller dan New-Object.

De pseudo statische methode met de naam **nieuwe** werkt met .NET-typen, zoals wordt weergegeven in het volgende voorbeeld.

```powershell
[hashtable]::new()
```

U ziet nu de constructor overloads met Get-Member, of als in dit voorbeeld wordt weergegeven:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a>Methoden

Een Windows PowerShell-methode de klasse wordt geïmplementeerd als een ScriptBlock waarvoor alleen een end-blok. Alle methoden zijn openbaar. De volgende toont een voorbeeld van het definiëren van een methode met de naam **DoeIets**.

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

Overbelaste methoden, dat wil zeggen, die met de naam van een bestaande methode, maar met de opgegeven waarden--onderscheiden worden ook ondersteund.

## <a name="properties"></a>Eigenschappen

Alle eigenschappen zijn openbaar. Eigenschappen van vereist een nieuwe regel of door puntkomma's. Als er geen objecttype is opgegeven, is het type object.

Eigenschappen die gebruikmaken van validatie kenmerken of argument transformatie kenmerken (bijvoorbeeld `[ValidateSet("aaa")]`) werkt zoals verwacht.

## <a name="hidden"></a>Verborgen

Een nieuw sleutelwoord, **verborgen**, is toegevoegd. **Verborgen** kan worden toegepast op eigenschappen en methoden (met inbegrip van constructors).

Verborgen leden openbaar zijn, maar worden niet weergegeven in de uitvoer van Get-Member, tenzij de - Force parameter is toegevoegd.

Verborgen leden zijn niet opgenomen wanneer tabblad voltooien of met behulp van Intellisense, tenzij de voltooiing vindt plaats in de klasse voor het definiëren van het verborgen lid.

Een nieuw kenmerk **System.Management.Automation.HiddenAttribute** is toegevoegd zodat C#-code dezelfde semantiek in Windows PowerShell hebben kunt.

## <a name="return-types"></a>Typen retourneren

Retourtype is een overeenkomst; de geretourneerde waarde wordt geconverteerd naar het verwachte type. Als er geen retourtype is opgegeven, is het retourtype is ongeldig. Er is geen streaming met objecten. objecten kunnen niet worden geschreven naar de pijplijn opzettelijk of per ongeluk.

## <a name="attributes"></a>Kenmerken

Twee nieuwe kenmerken, **sleutelwoorden dscresource bieden** en **DscProperty** zijn toegevoegd.

## <a name="lexical-scoping-of-variables"></a>Lexicale bereik van variabelen

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

Het volgende voorbeeld wordt de diverse nieuwe, aangepaste klassen voor het implementeren van een HTML-dynamische taal van het opmaakmodel (DSL).
Het voorbeeld wordt vervolgens ondersteunende functies voor het maken van specifieke elementtypen als onderdeel van de elementklasse, zoals opmaakprofielen en tabellen, omdat de typen kunnen niet worden gebruikt buiten het bereik van een module.

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
