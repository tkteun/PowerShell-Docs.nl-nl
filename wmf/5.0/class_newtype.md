---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 9aa7e92632c671751020687ddbfc374eeda7148b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="70bf7-102">Nieuwe taalfuncties in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="70bf7-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="70bf7-103">PowerShell 5.0 introduceert de volgende nieuwe taalelementen in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="70bf7-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="70bf7-104">Klasse sleutelwoord</span><span class="sxs-lookup"><span data-stu-id="70bf7-104">Class keyword</span></span>

<span data-ttu-id="70bf7-105">De **klasse** sleutelwoord definieert een nieuwe klasse.</span><span class="sxs-lookup"><span data-stu-id="70bf7-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="70bf7-106">Dit is een echte .NET Framework-type.</span><span class="sxs-lookup"><span data-stu-id="70bf7-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="70bf7-107">Klasseleden zijn openbaar, maar alleen openbare binnen het modulebereik.</span><span class="sxs-lookup"><span data-stu-id="70bf7-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="70bf7-108">U mag niet verwijzen naar de typenaam als tekenreeks (bijvoorbeeld `New-Object` niet werkt), en in deze release kunt u een letterlijke waarde van het type niet gebruiken (bijvoorbeeld `[MyClass]`) buiten het scriptmodule /-bestand waarin de klasse is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="70bf7-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="70bf7-109">Enum-sleutelwoord en opsommingen</span><span class="sxs-lookup"><span data-stu-id="70bf7-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="70bf7-110">Ondersteuning voor de **enum** sleutelwoord is toegevoegd, waarbij nieuwe regel wordt gebruikt als scheidingsteken.</span><span class="sxs-lookup"><span data-stu-id="70bf7-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="70bf7-111">Huidige beperkingen: u kunt een enumerator in termen van zelf niet definiëren, maar u kunt een enum in termen van een andere enum initialiseren, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="70bf7-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="70bf7-112">Het basistype kan niet ook op dat moment worden opgegeven; het is altijd [int].</span><span class="sxs-lookup"><span data-stu-id="70bf7-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="70bf7-113">Een enumeratorwaarde moet een constante parse; u kunt deze niet instellen op het resultaat van een opdracht aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="70bf7-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="70bf7-114">Enums ondersteuning voor rekenkundige bewerkingen, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="70bf7-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="70bf7-115">Importeren DscResource</span><span class="sxs-lookup"><span data-stu-id="70bf7-115">Import-DscResource</span></span>

<span data-ttu-id="70bf7-116">**Importeren DscResource** is nu een waar dynamische sleutelwoord.</span><span class="sxs-lookup"><span data-stu-id="70bf7-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="70bf7-117">PowerShell parseert de opgegeven module root-module, zoeken naar klassen die bevatten de **DscResource** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="70bf7-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="70bf7-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="70bf7-118">ImplementingAssembly</span></span>

<span data-ttu-id="70bf7-119">Een nieuw veld **ImplementingAssembly**, is toegevoegd aan ModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="70bf7-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="70bf7-120">Het is ingesteld op de dynamische assembly voor een scriptmodule gemaakt als het script klassen gedefinieerd of de assembly geladen voor binaire modules.</span><span class="sxs-lookup"><span data-stu-id="70bf7-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="70bf7-121">Het is niet ingesteld als ModuleType = Manifest.</span><span class="sxs-lookup"><span data-stu-id="70bf7-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="70bf7-122">Na te denken over de **ImplementingAssembly** veld detecteert resources in een module.</span><span class="sxs-lookup"><span data-stu-id="70bf7-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="70bf7-123">Dit betekent dat u de resources die zijn geschreven in PowerShell of andere beheerde talen kunt detecteren.</span><span class="sxs-lookup"><span data-stu-id="70bf7-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="70bf7-124">De velden met initalisatiefuncties:</span><span class="sxs-lookup"><span data-stu-id="70bf7-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="70bf7-125">Statische ondersteund. Dit werkt als een kenmerk, evenals de typebeperkingen, zodat deze kan worden opgegeven in een willekeurige volgorde.</span><span class="sxs-lookup"><span data-stu-id="70bf7-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="70bf7-126">Een type is optioneel.</span><span class="sxs-lookup"><span data-stu-id="70bf7-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="70bf7-127">Alle leden zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="70bf7-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="70bf7-128">Constructors en instantiëring</span><span class="sxs-lookup"><span data-stu-id="70bf7-128">Constructors and instantiation</span></span>

<span data-ttu-id="70bf7-129">Windows PowerShell-klassen kunnen hebben constructors; ze hebben dezelfde naam als de klasse.</span><span class="sxs-lookup"><span data-stu-id="70bf7-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="70bf7-130">Constructors kunnen overbelast.</span><span class="sxs-lookup"><span data-stu-id="70bf7-130">Constructors can be overloaded.</span></span> <span data-ttu-id="70bf7-131">Statische constructors worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="70bf7-131">Static constructors are supported.</span></span> <span data-ttu-id="70bf7-132">Eigenschappen met initialisatie-expressies zijn geïnitialiseerd voordat code wordt uitgevoerd in een constructor.</span><span class="sxs-lookup"><span data-stu-id="70bf7-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="70bf7-133">Statische eigenschappen worden geïnitialiseerd voordat de hoofdtekst van een statische constructor en eigenschappen van objectexemplaar zijn geïnitialiseerd voordat de hoofdtekst van de niet-statische constructor.</span><span class="sxs-lookup"><span data-stu-id="70bf7-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="70bf7-134">Er is momenteel geen syntaxis voor een constructor aanroept vanuit een andere constructor (zoals de C\# syntaxis ': this()").</span><span class="sxs-lookup"><span data-stu-id="70bf7-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="70bf7-135">De tijdelijke oplossing is voor het definiëren van een algemene Init-methode.</span><span class="sxs-lookup"><span data-stu-id="70bf7-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="70bf7-136">De volgende zijn manieren instantiëren van klassen in deze release.</span><span class="sxs-lookup"><span data-stu-id="70bf7-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="70bf7-137">Instantiëren met behulp van de standaardconstructor.</span><span class="sxs-lookup"><span data-stu-id="70bf7-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="70bf7-138">Houd er rekening mee New-Object wordt niet ondersteund in deze release.</span><span class="sxs-lookup"><span data-stu-id="70bf7-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="70bf7-139">Aanroepen van een constructor met een parameter</span><span class="sxs-lookup"><span data-stu-id="70bf7-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="70bf7-140">Een matrix doorgeven aan een constructor met meerdere parameters</span><span class="sxs-lookup"><span data-stu-id="70bf7-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="70bf7-141">In deze release werkt New-Object niet met de klassen die zijn gedefinieerd in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70bf7-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="70bf7-142">Ook voor deze release is de typenaam alleen zichtbaar lexically, wat betekent dat het is niet zichtbaar zijn buiten de module of het script dat de klasse definieert.</span><span class="sxs-lookup"><span data-stu-id="70bf7-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="70bf7-143">Functies exemplaren van een klasse is gedefinieerd in Windows PowerShell kunnen terugkeren en exemplaren werken goed buiten de module of het script.</span><span class="sxs-lookup"><span data-stu-id="70bf7-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="70bf7-144">`Get-Member -Static` Geeft een lijst constructors, zodat u overloads zoals een andere methode kunt bekijken.</span><span class="sxs-lookup"><span data-stu-id="70bf7-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="70bf7-145">De prestaties van deze syntaxis werkt ook aanzienlijk sneller dan New-Object.</span><span class="sxs-lookup"><span data-stu-id="70bf7-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="70bf7-146">De pseudo statische methode met de naam **nieuwe** werkt met .NET-typen, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="70bf7-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="70bf7-147">U kunt nu zien constructor overloads met Get-lid of zoals in dit voorbeeld wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="70bf7-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="70bf7-148">Methoden</span><span class="sxs-lookup"><span data-stu-id="70bf7-148">Methods</span></span>

<span data-ttu-id="70bf7-149">De methode van een Windows PowerShell-klasse wordt geïmplementeerd als een ScriptBlock met alleen een end-blok.</span><span class="sxs-lookup"><span data-stu-id="70bf7-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="70bf7-150">Alle methoden zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="70bf7-150">All methods are public.</span></span> <span data-ttu-id="70bf7-151">Hieronder vindt u een voorbeeld van het definiëren van een methode met de naam **DoeIets**.</span><span class="sxs-lookup"><span data-stu-id="70bf7-151">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="70bf7-152">De methodeaanroep:</span><span class="sxs-lookup"><span data-stu-id="70bf7-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="70bf7-153">Overbelaste methoden--dat wil zeggen, die hetzelfde zijn als een bestaande methode met de naam, maar met de opgegeven waarden--onderscheiden worden ook ondersteund.</span><span class="sxs-lookup"><span data-stu-id="70bf7-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="70bf7-154">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="70bf7-154">Properties</span></span>

<span data-ttu-id="70bf7-155">Alle eigenschappen zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="70bf7-155">All properties are public.</span></span> <span data-ttu-id="70bf7-156">Eigenschappen vereisen een nieuwe regel of een puntkomma.</span><span class="sxs-lookup"><span data-stu-id="70bf7-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="70bf7-157">Als er geen objecttype is opgegeven, is het eigenschapstype-object.</span><span class="sxs-lookup"><span data-stu-id="70bf7-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="70bf7-158">Eigenschappen die validatie kenmerken of argument transformatie kenmerken worden gebruikt (bijvoorbeeld `[ValidateSet("aaa")]`) werkt zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="70bf7-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="70bf7-159">Verborgen</span><span class="sxs-lookup"><span data-stu-id="70bf7-159">Hidden</span></span>

<span data-ttu-id="70bf7-160">Een nieuw trefwoord **Hidden**, is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="70bf7-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="70bf7-161">**Verborgen** kunnen worden toegepast op eigenschappen en methoden (inclusief constructors).</span><span class="sxs-lookup"><span data-stu-id="70bf7-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="70bf7-162">Verborgen leden zijn openbaar, maar worden niet weergegeven in de uitvoer van Get-lid, tenzij de - Force parameter wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="70bf7-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="70bf7-163">Verborgen leden zijn niet opgenomen wanneer tabblad voltooien of met behulp van Intellisense tenzij de voltooiing van deze gebeurtenis treedt op in de klasse voor het definiëren van het verborgen lid.</span><span class="sxs-lookup"><span data-stu-id="70bf7-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="70bf7-164">Een nieuw kenmerk **System.Management.Automation.HiddenAttribute** is toegevoegd zodat C#-code dezelfde betekenis in Windows PowerShell hebben kunt.</span><span class="sxs-lookup"><span data-stu-id="70bf7-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="70bf7-165">Retourtypen</span><span class="sxs-lookup"><span data-stu-id="70bf7-165">Return types</span></span>

<span data-ttu-id="70bf7-166">Retourtype is een contract; de retourwaarde wordt geconverteerd naar het verwachte type.</span><span class="sxs-lookup"><span data-stu-id="70bf7-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="70bf7-167">Als er geen retourtype is opgegeven, is het retourtype void.</span><span class="sxs-lookup"><span data-stu-id="70bf7-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="70bf7-168">Er is geen streaming-objecten. objecten kunnen niet worden geschreven naar de pijplijn opzettelijk of per ongeluk.</span><span class="sxs-lookup"><span data-stu-id="70bf7-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="70bf7-169">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="70bf7-169">Attributes</span></span>

<span data-ttu-id="70bf7-170">Twee nieuwe kenmerken **DscResource** en **DscProperty** zijn toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="70bf7-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="70bf7-171">Lexicale bereik van variabelen</span><span class="sxs-lookup"><span data-stu-id="70bf7-171">Lexical scoping of variables</span></span>

<span data-ttu-id="70bf7-172">De volgende toont een voorbeeld van hoe lexicale bereik werken in deze release.</span><span class="sxs-lookup"><span data-stu-id="70bf7-172">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="70bf7-173">End-to-End-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="70bf7-173">End-to-End Example</span></span>

<span data-ttu-id="70bf7-174">Het volgende voorbeeld maakt diverse nieuwe, aangepaste klassen voor het implementeren van een HTML-dynamische taal van het opmaakmodel (DSL).</span><span class="sxs-lookup"><span data-stu-id="70bf7-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="70bf7-175">Het voorbeeld wordt vervolgens hulpfuncties voor het maken van specifieke elementtypen als onderdeel van de elementklasse zoals kopstijlen en tabellen, omdat de typen kunnen niet worden gebruikt buiten het bereik van een module.</span><span class="sxs-lookup"><span data-stu-id="70bf7-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
