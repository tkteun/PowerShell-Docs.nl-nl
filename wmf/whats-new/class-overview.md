---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Aangepaste typen maken met PowerShell-klassen
ms.openlocfilehash: 0dd5bbaca50abb746e15a7bb64a706c7eceee905
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856236"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="3ec88-103">Aangepaste typen maken met PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="3ec88-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="3ec88-104">PowerShell 5.0 de mogelijkheid voor het definiëren van klassen en andere door de gebruiker gedefinieerde typen met behulp van formele syntaxis en semantiek net als andere programmeertalen objectgeoriënteerde toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3ec88-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="3ec88-105">Het doel is om in te schakelen van ontwikkelaars en IT-professionals Profiteer van PowerShell voor een breder scala aan toepassingen, Vereenvoudig de ontwikkeling van PowerShell-artefacten (zoals DSC-resources) en de dekking van management oppervlakken versnellen.</span><span class="sxs-lookup"><span data-stu-id="3ec88-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="3ec88-106">Ondersteunde scenario's in deze release</span><span class="sxs-lookup"><span data-stu-id="3ec88-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="3ec88-107">DSC-resources en hun bijbehorende typen definiëren met behulp van de PowerShell-taal</span><span class="sxs-lookup"><span data-stu-id="3ec88-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="3ec88-108">Aangepaste typen definiëren in PowerShell met behulp van bekende objectgeoriënteerde programming-constructs, zoals klassen, eigenschappen, methoden, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="3ec88-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="3ec88-109">Ondersteuning voor overname van met de klasse in PowerShell en de klasse base DSC-resource</span><span class="sxs-lookup"><span data-stu-id="3ec88-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="3ec88-110">Fouten opsporen in typen met behulp van de PowerShell-taal</span><span class="sxs-lookup"><span data-stu-id="3ec88-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="3ec88-111">Genereren en uitzonderingen verwerken met behulp van formele mechanismen en op het juiste niveau</span><span class="sxs-lookup"><span data-stu-id="3ec88-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

# <a name="declare-base-class"></a><span data-ttu-id="3ec88-112">Basisklasse declareren</span><span class="sxs-lookup"><span data-stu-id="3ec88-112">Declare Base Class</span></span>

<span data-ttu-id="3ec88-113">Als een basistype op voor een andere PowerShell-klasse kunt u een PowerShell-klasse declareren.</span><span class="sxs-lookup"><span data-stu-id="3ec88-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

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

<span data-ttu-id="3ec88-114">U kunt ook bestaande .NET Framework-typen gebruiken als basisklassen:</span><span class="sxs-lookup"><span data-stu-id="3ec88-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

# <a name="call-base-class-constructor"></a><span data-ttu-id="3ec88-115">Klasseconstructor oproepbasis</span><span class="sxs-lookup"><span data-stu-id="3ec88-115">Call Base Class Constructor</span></span>

<span data-ttu-id="3ec88-116">Als u wilt een oproepbasis aanroepen vanuit een subklasse, gebruikt u het sleutelwoord **basis**:</span><span class="sxs-lookup"><span data-stu-id="3ec88-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="3ec88-117">Als een basisklasse heeft een standaardconstructor (Er is geen parameter), kunt u een expliciete constructoraanroep weglaten:</span><span class="sxs-lookup"><span data-stu-id="3ec88-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

# <a name="call-base-class-method"></a><span data-ttu-id="3ec88-118">Klassemethode oproepbasis</span><span class="sxs-lookup"><span data-stu-id="3ec88-118">Call Base Class Method</span></span>

<span data-ttu-id="3ec88-119">U kunt bestaande methoden in subklassen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="3ec88-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="3ec88-120">U doet dit door methoden met behulp van dezelfde naam en handtekening te declareren:</span><span class="sxs-lookup"><span data-stu-id="3ec88-120">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="3ec88-121">Voor het aanroepen van methoden van de basisklasse van overschreven-implementaties, geconverteerd naar de basisklasse (`[baseClass]$this`) op voor aanroepen:</span><span class="sxs-lookup"><span data-stu-id="3ec88-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

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

<span data-ttu-id="3ec88-122">Alle methoden voor PowerShell zijn virtueel.</span><span class="sxs-lookup"><span data-stu-id="3ec88-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="3ec88-123">U kunt niet-virtuele .NET-methoden in een subklasse verbergen met behulp van dezelfde syntaxis als voor een onderdrukking, door op te geven van methoden met dezelfde naam en handtekening.</span><span class="sxs-lookup"><span data-stu-id="3ec88-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

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

# <a name="declare-implemented-interface"></a><span data-ttu-id="3ec88-124">Geïmplementeerde interface declareren</span><span class="sxs-lookup"><span data-stu-id="3ec88-124">Declare Implemented Interface</span></span>

<span data-ttu-id="3ec88-125">U kunt geïmplementeerde interfaces aangeven na basistypen of onmiddellijk nadat een dubbele punt (:), als er geen basistype dat is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3ec88-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="3ec88-126">Alle namen worden gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="3ec88-126">Separate all type names by using commas.</span></span> <span data-ttu-id="3ec88-127">Het is vergelijkbaar met C# syntaxis.</span><span class="sxs-lookup"><span data-stu-id="3ec88-127">It's similar to C# syntax.</span></span>

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

# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="3ec88-128">Nieuwe taalfuncties in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3ec88-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="3ec88-129">PowerShell 5.0 introduceert de volgende nieuwe taalelementen in PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3ec88-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="3ec88-130">Klasse trefwoord</span><span class="sxs-lookup"><span data-stu-id="3ec88-130">Class keyword</span></span>

<span data-ttu-id="3ec88-131">De `class` sleutelwoord definieert een nieuwe klasse.</span><span class="sxs-lookup"><span data-stu-id="3ec88-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="3ec88-132">Dit is een echte .NET Framework-type.</span><span class="sxs-lookup"><span data-stu-id="3ec88-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="3ec88-133">Klasseleden zijn openbaar, maar alleen openbaar binnen het modulebereik.</span><span class="sxs-lookup"><span data-stu-id="3ec88-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="3ec88-134">U mag niet verwijzen naar de naam van het als een tekenreeks (bijvoorbeeld `New-Object` niet werkt), en in deze release kunt u een letterlijke type niet gebruiken (bijvoorbeeld `[MyClass]`) buiten het script of een module-bestand waarin de klasse is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="3ec88-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="3ec88-135">Enum sleutelwoord en opsommingen</span><span class="sxs-lookup"><span data-stu-id="3ec88-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="3ec88-136">Ondersteuning voor de `enum` sleutelwoord is toegevoegd, waarbij nieuwe regel wordt gebruikt als het scheidingsteken.</span><span class="sxs-lookup"><span data-stu-id="3ec88-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="3ec88-137">U kunt geen op dit moment een enumerator voor wat betreft zelf definiëren.</span><span class="sxs-lookup"><span data-stu-id="3ec88-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="3ec88-138">U kunt echter een enum-waarde in termen van een andere enum initialiseren, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="3ec88-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="3ec88-139">Bovendien kan het basistype kan niet worden opgegeven; het is altijd `[int]`.</span><span class="sxs-lookup"><span data-stu-id="3ec88-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="3ec88-140">De enumeratorwaarde van een moet een constante parseren.</span><span class="sxs-lookup"><span data-stu-id="3ec88-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="3ec88-141">U kunt deze niet instellen op het resultaat van een aangeroepen opdracht.</span><span class="sxs-lookup"><span data-stu-id="3ec88-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="3ec88-142">Enum-waarden ondersteunt rekenkundige bewerkingen, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="3ec88-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="3ec88-143">Sleutelwoorden import-dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="3ec88-143">Import-DscResource</span></span>

<span data-ttu-id="3ec88-144">`Import-DscResource` is nu een waar dynamische trefwoord.</span><span class="sxs-lookup"><span data-stu-id="3ec88-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="3ec88-145">PowerShell parseert basismodule van de opgegeven module, zoeken naar klassen die bevatten de **sleutelwoorden dscresource bieden** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="3ec88-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="3ec88-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="3ec88-146">ImplementingAssembly</span></span>

<span data-ttu-id="3ec88-147">Een nieuw veld **ImplementingAssembly**, is toegevoegd aan **ModuleInfo**.</span><span class="sxs-lookup"><span data-stu-id="3ec88-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="3ec88-148">Deze waarde is ingesteld op de dynamische verzameling voor een scriptmodule gemaakt als het script klassen definieert, of de geladen assembly voor binaire modules.</span><span class="sxs-lookup"><span data-stu-id="3ec88-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="3ec88-149">Het is niet ingesteld als **ModuleType** is **Manifest**.</span><span class="sxs-lookup"><span data-stu-id="3ec88-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="3ec88-150">Na te denken over de **ImplementingAssembly** veld resources in een module heeft gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="3ec88-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="3ec88-151">Dit betekent dat u kunt de resources die zijn geschreven in PowerShell of andere beheerde talen detecteren.</span><span class="sxs-lookup"><span data-stu-id="3ec88-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="3ec88-152">Velden met initializers:</span><span class="sxs-lookup"><span data-stu-id="3ec88-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="3ec88-153">`Static` wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3ec88-153">`Static` is supported.</span></span> <span data-ttu-id="3ec88-154">Het werkt als een kenmerk, zoals de typebeperkingen dat wel doet.</span><span class="sxs-lookup"><span data-stu-id="3ec88-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="3ec88-155">Deze kan in willekeurige volgorde worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3ec88-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="3ec88-156">Een type is optioneel.</span><span class="sxs-lookup"><span data-stu-id="3ec88-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="3ec88-157">Alle leden van de zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="3ec88-157">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="3ec88-158">Constructors en instantiëring</span><span class="sxs-lookup"><span data-stu-id="3ec88-158">Constructors and instantiation</span></span>

<span data-ttu-id="3ec88-159">PowerShell-klassen kunnen constructors hebben.</span><span class="sxs-lookup"><span data-stu-id="3ec88-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="3ec88-160">Ze hebben dezelfde naam als de klasse.</span><span class="sxs-lookup"><span data-stu-id="3ec88-160">They have the same name as their class.</span></span> <span data-ttu-id="3ec88-161">Constructors kunnen worden overbelast.</span><span class="sxs-lookup"><span data-stu-id="3ec88-161">Constructors can be overloaded.</span></span> <span data-ttu-id="3ec88-162">Statische constructors worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3ec88-162">Static constructors are supported.</span></span> <span data-ttu-id="3ec88-163">Eigenschappen met expressies voor objectinitialisatie geïnitialiseerd voordat u code uitvoert in een constructor.</span><span class="sxs-lookup"><span data-stu-id="3ec88-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="3ec88-164">Statische eigenschappen worden geïnitialiseerd voordat de hoofdtekst van een statische constructor en instantie-eigenschappen zijn geïnitialiseerd voordat de hoofdtekst van de niet-statische-constructor.</span><span class="sxs-lookup"><span data-stu-id="3ec88-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="3ec88-165">Er is momenteel geen syntaxis voor het aanroepen van een constructor vanuit een andere constructor (zoals de C\# syntaxis ': this()").</span><span class="sxs-lookup"><span data-stu-id="3ec88-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="3ec88-166">De tijdelijke oplossing is voor het definiëren van een algemene `Init()` methode.</span><span class="sxs-lookup"><span data-stu-id="3ec88-166">The workaround is to define a common `Init()` method.</span></span>

### <a name="creating-instances"></a><span data-ttu-id="3ec88-167">Het maken van instanties</span><span class="sxs-lookup"><span data-stu-id="3ec88-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="3ec88-168">In PowerShell 5.0 `New-Object` werkt niet met klassen die zijn gedefinieerd in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ec88-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="3ec88-169">De naam van het is ook alleen zichtbaar lexicaal, wat betekent dat deze zijn niet zichtbaar is buiten de module of het script dat de klasse definieert.</span><span class="sxs-lookup"><span data-stu-id="3ec88-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="3ec88-170">Functies kunnen exemplaren van een klasse is gedefinieerd in PowerShell retourneren.</span><span class="sxs-lookup"><span data-stu-id="3ec88-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="3ec88-171">Deze instanties werken buiten de module of het script.</span><span class="sxs-lookup"><span data-stu-id="3ec88-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="3ec88-172">Instantiëren met behulp van de standaardconstructor.</span><span class="sxs-lookup"><span data-stu-id="3ec88-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="3ec88-173">Aanroepen van een constructor met een parameter</span><span class="sxs-lookup"><span data-stu-id="3ec88-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="3ec88-174">Een matrix doorgegeven aan een constructor met meerdere parameters.</span><span class="sxs-lookup"><span data-stu-id="3ec88-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="3ec88-175">De pseudo statische methode `new()` werkt met .NET-typen, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="3ec88-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

### <a name="discovering-constructors"></a><span data-ttu-id="3ec88-176">Detectie van constructors</span><span class="sxs-lookup"><span data-stu-id="3ec88-176">Discovering constructors</span></span>

<span data-ttu-id="3ec88-177">U ziet nu de constructor overloads met `Get-Member`, of zoals in dit voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="3ec88-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="3ec88-178">`Get-Member -Static` Geeft een lijst van constructors, zodat u overloads, zoals een andere methode kunt bekijken.</span><span class="sxs-lookup"><span data-stu-id="3ec88-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="3ec88-179">De prestaties van deze syntaxis werkt ook aanzienlijk sneller dan `New-Object`.</span><span class="sxs-lookup"><span data-stu-id="3ec88-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

## <a name="methods"></a><span data-ttu-id="3ec88-180">Methoden</span><span class="sxs-lookup"><span data-stu-id="3ec88-180">Methods</span></span>

<span data-ttu-id="3ec88-181">Een PowerShell-methode de klasse wordt geïmplementeerd als een **ScriptBlock** waarvoor alleen een end-blok.</span><span class="sxs-lookup"><span data-stu-id="3ec88-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="3ec88-182">Alle methoden zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="3ec88-182">All methods are public.</span></span> <span data-ttu-id="3ec88-183">De volgende toont een voorbeeld van het definiëren van een methode met de naam **DoeIets**.</span><span class="sxs-lookup"><span data-stu-id="3ec88-183">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="3ec88-184">Aanroepen van de methode:</span><span class="sxs-lookup"><span data-stu-id="3ec88-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="3ec88-185">Overbelaste methoden worden ook ondersteund.</span><span class="sxs-lookup"><span data-stu-id="3ec88-185">Overloaded methods are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="3ec88-186">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="3ec88-186">Properties</span></span>

<span data-ttu-id="3ec88-187">Alle eigenschappen zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="3ec88-187">All properties are public.</span></span> <span data-ttu-id="3ec88-188">Eigenschappen van vereist een nieuwe regel of door puntkomma's.</span><span class="sxs-lookup"><span data-stu-id="3ec88-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="3ec88-189">Als er geen objecttype is opgegeven, is het type object.</span><span class="sxs-lookup"><span data-stu-id="3ec88-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="3ec88-190">Eigenschappen die validatie of argument transformatie-kenmerken worden gebruikt (zoals `[ValidateSet("aaa")]`) werkt zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="3ec88-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="3ec88-191">Verborgen</span><span class="sxs-lookup"><span data-stu-id="3ec88-191">Hidden</span></span>

<span data-ttu-id="3ec88-192">Een nieuw sleutelwoord, `Hidden`, is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3ec88-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="3ec88-193">`Hidden` kan worden toegepast op eigenschappen en methoden (met inbegrip van constructors).</span><span class="sxs-lookup"><span data-stu-id="3ec88-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="3ec88-194">Verborgen leden openbaar zijn, maar worden niet weergegeven in de uitvoer van `Get-Member` , tenzij de - Force parameter is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3ec88-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the -Force parameter is added.</span></span> <span data-ttu-id="3ec88-195">Verborgen leden zijn niet opgenomen wanneer tabblad voltooien of met behulp van Intellisense, tenzij de voltooiing vindt plaats in de klasse voor het definiëren van het verborgen lid.</span><span class="sxs-lookup"><span data-stu-id="3ec88-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="3ec88-196">Een nieuw kenmerk **System.Management.Automation.HiddenAttribute** is toegevoegd, die C\# code kan hebben dezelfde semantiek in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ec88-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="3ec88-197">Typen retourneren</span><span class="sxs-lookup"><span data-stu-id="3ec88-197">Return types</span></span>

<span data-ttu-id="3ec88-198">Retourtype is een contract.</span><span class="sxs-lookup"><span data-stu-id="3ec88-198">Return type is a contract.</span></span> <span data-ttu-id="3ec88-199">De geretourneerde waarde wordt geconverteerd naar het verwachte type.</span><span class="sxs-lookup"><span data-stu-id="3ec88-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="3ec88-200">Als er geen retourtype is opgegeven, wordt het retourtype is **void**.</span><span class="sxs-lookup"><span data-stu-id="3ec88-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="3ec88-201">Er is geen streaming-objecten.</span><span class="sxs-lookup"><span data-stu-id="3ec88-201">There is no streaming of objects.</span></span> <span data-ttu-id="3ec88-202">Bbjects kan niet worden geschreven naar de pijplijn opzettelijk of per ongeluk.</span><span class="sxs-lookup"><span data-stu-id="3ec88-202">Bbjects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="3ec88-203">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="3ec88-203">Attributes</span></span>

<span data-ttu-id="3ec88-204">Twee nieuwe kenmerken, **sleutelwoorden dscresource bieden** en **DscProperty** zijn toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="3ec88-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="3ec88-205">Lexicale bereik van variabelen</span><span class="sxs-lookup"><span data-stu-id="3ec88-205">Lexical scoping of variables</span></span>

<span data-ttu-id="3ec88-206">Hieronder ziet u een voorbeeld van hoe lexicale scoping werken in deze release.</span><span class="sxs-lookup"><span data-stu-id="3ec88-206">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="3ec88-207">Voorbeeld van de end-to-End</span><span class="sxs-lookup"><span data-stu-id="3ec88-207">End-to-End Example</span></span>

<span data-ttu-id="3ec88-208">Het volgende voorbeeld wordt een aangepaste klassen voor het implementeren van een HTML-dynamische taal van het opmaakmodel (DSL).</span><span class="sxs-lookup"><span data-stu-id="3ec88-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="3ec88-209">Het voorbeeld wordt vervolgens ondersteunende functies voor het maken van specifieke elementtypen als onderdeel van de elementklasse, zoals opmaakprofielen en tabellen, omdat de typen kunnen niet worden gebruikt buiten het bereik van een module.</span><span class="sxs-lookup"><span data-stu-id="3ec88-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
