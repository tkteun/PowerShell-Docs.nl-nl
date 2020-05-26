---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Aangepaste typen maken met PowerShell-klassen
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810433"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="48327-103">Aangepaste typen maken met PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="48327-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="48327-104">Power shell 5,0 heeft de mogelijkheid om klassen en andere door de gebruiker gedefinieerde typen te definiëren met behulp van formele syntaxis en semantiek, zoals andere objectgeoriënteerd programmeer talen.</span><span class="sxs-lookup"><span data-stu-id="48327-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="48327-105">Het doel is om ontwikkel aars en IT-professionals in staat te stellen Power shell te gebruiken voor een breder scala aan gebruiks voorbeelden, het ontwikkelen van Power shell-artefacten (zoals DSC-resources) te vereenvoudigen en de dekking van management-Opper vlakken te versnellen.</span><span class="sxs-lookup"><span data-stu-id="48327-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="48327-106">Ondersteunde scenario's in deze release</span><span class="sxs-lookup"><span data-stu-id="48327-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="48327-107">DSC-resources en de bijbehorende typen definiëren met behulp van de Power shell-taal</span><span class="sxs-lookup"><span data-stu-id="48327-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="48327-108">Aangepaste typen in Power shell definiëren met behulp van vertrouwde object georiënteerde Programmeer constructies, zoals klassen, eigenschappen, methoden, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="48327-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="48327-109">Overname ondersteuning voor de klasse in Power shell en Class base DSC resource</span><span class="sxs-lookup"><span data-stu-id="48327-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="48327-110">Typen fout opsporing met behulp van de Power shell-taal</span><span class="sxs-lookup"><span data-stu-id="48327-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="48327-111">Uitzonde ringen genereren en verwerken met behulp van formele mechanismen en op het juiste niveau</span><span class="sxs-lookup"><span data-stu-id="48327-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

## <a name="declare-base-class"></a><span data-ttu-id="48327-112">Basisklasse declareren</span><span class="sxs-lookup"><span data-stu-id="48327-112">Declare Base Class</span></span>

<span data-ttu-id="48327-113">U kunt een Power shell-klasse declareren als basis type voor een andere Power shell-klasse.</span><span class="sxs-lookup"><span data-stu-id="48327-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

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

<span data-ttu-id="48327-114">U kunt ook bestaande .NET Framework typen als basis klassen gebruiken:</span><span class="sxs-lookup"><span data-stu-id="48327-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a><span data-ttu-id="48327-115">Klasseconstructor oproepbasis</span><span class="sxs-lookup"><span data-stu-id="48327-115">Call Base Class Constructor</span></span>

<span data-ttu-id="48327-116">Als u een basis klasse-constructor vanuit een subklasse wilt aanroepen, gebruikt u de **basis**sleutel woord:</span><span class="sxs-lookup"><span data-stu-id="48327-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="48327-117">Als een basis klasse een standaard-constructor (geen para meter) heeft, kunt u een expliciete aanroep van een constructor weglaten:</span><span class="sxs-lookup"><span data-stu-id="48327-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a><span data-ttu-id="48327-118">Klassemethode oproepbasis</span><span class="sxs-lookup"><span data-stu-id="48327-118">Call Base Class Method</span></span>

<span data-ttu-id="48327-119">U kunt bestaande methoden in subklassen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="48327-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="48327-120">Om dit te doen, declareert u methoden met dezelfde naam en hand tekening:</span><span class="sxs-lookup"><span data-stu-id="48327-120">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="48327-121">Voor het aanroepen van basis klassen methoden van overschreven implementaties, Casting naar de basis klasse ( `[baseClass]$this` ) op aanroepen:</span><span class="sxs-lookup"><span data-stu-id="48327-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

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

<span data-ttu-id="48327-122">Alle Power shell-methoden zijn virtueel.</span><span class="sxs-lookup"><span data-stu-id="48327-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="48327-123">U kunt niet-virtuele .NET-methoden in een subklasse verbergen door dezelfde syntaxis te gebruiken als voor een onderdrukking, door methoden te declareren met dezelfde naam en hand tekening.</span><span class="sxs-lookup"><span data-stu-id="48327-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

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

### <a name="declare-implemented-interface"></a><span data-ttu-id="48327-124">Geïmplementeerde interface declareren</span><span class="sxs-lookup"><span data-stu-id="48327-124">Declare Implemented Interface</span></span>

<span data-ttu-id="48327-125">U kunt geïmplementeerde interfaces na basis typen of direct na een dubbele punt (:) declareren als er geen basis type is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="48327-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="48327-126">Scheid alle type namen met behulp van komma's.</span><span class="sxs-lookup"><span data-stu-id="48327-126">Separate all type names by using commas.</span></span> <span data-ttu-id="48327-127">Het is vergelijkbaar met de syntaxis van C#.</span><span class="sxs-lookup"><span data-stu-id="48327-127">It's similar to C# syntax.</span></span>

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

## <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="48327-128">Nieuwe taal functies in Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="48327-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="48327-129">Power shell 5,0 introduceert de volgende nieuwe taal elementen in Power shell:</span><span class="sxs-lookup"><span data-stu-id="48327-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="48327-130">Tref woord klasse</span><span class="sxs-lookup"><span data-stu-id="48327-130">Class keyword</span></span>

<span data-ttu-id="48327-131">Het `class` sleutel woord definieert een nieuwe klasse.</span><span class="sxs-lookup"><span data-stu-id="48327-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="48327-132">Dit is een True .NET Framework type.</span><span class="sxs-lookup"><span data-stu-id="48327-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="48327-133">Klasse-leden zijn openbaar, maar alleen openbaar binnen het module bereik.</span><span class="sxs-lookup"><span data-stu-id="48327-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="48327-134">U kunt niet naar de type naam verwijzen als een teken reeks (bijvoorbeeld `New-Object` niet werkt), en in deze release kunt u geen letterlijke type waarde (bijvoorbeeld) gebruiken `[MyClass]` buiten het script of module bestand waarin de klasse is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="48327-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="48327-135">Tref woord en opsommingen inventariseren</span><span class="sxs-lookup"><span data-stu-id="48327-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="48327-136">Ondersteuning voor het `enum` tref woord is toegevoegd. Dit maakt gebruik van een nieuwe regel als scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="48327-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="48327-137">Op dit moment kunt u geen enumerator definiëren in termen van zichzelf.</span><span class="sxs-lookup"><span data-stu-id="48327-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="48327-138">U kunt echter een Enum initialiseren in termen van een andere Enum, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="48327-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="48327-139">Het basis type kan ook niet worden opgegeven. het is altijd `[int]` .</span><span class="sxs-lookup"><span data-stu-id="48327-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="48327-140">Een enumerator-waarde moet een geparseerd tijd constante zijn.</span><span class="sxs-lookup"><span data-stu-id="48327-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="48327-141">U kunt deze niet instellen op het resultaat van een aangeroepen opdracht.</span><span class="sxs-lookup"><span data-stu-id="48327-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="48327-142">Opsommingen bieden ondersteuning voor reken kundige bewerkingen, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="48327-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="48327-143">Import-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="48327-143">Import-DscResource</span></span>

<span data-ttu-id="48327-144">`Import-DscResource`is nu een echt dynamisch sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="48327-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="48327-145">Power shell parseert de hoofd module van de opgegeven module. er wordt gezocht naar klassen die het kenmerk **dscresource bieden** bevatten.</span><span class="sxs-lookup"><span data-stu-id="48327-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="48327-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="48327-146">ImplementingAssembly</span></span>

<span data-ttu-id="48327-147">Er is een nieuw veld, **ImplementingAssembly**, toegevoegd aan **ModuleInfo**.</span><span class="sxs-lookup"><span data-stu-id="48327-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="48327-148">Deze wordt ingesteld op de dynamische assembly die is gemaakt voor een script module als het script klassen definieert, of de geladen assembly voor binaire modules.</span><span class="sxs-lookup"><span data-stu-id="48327-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="48327-149">Het is niet ingesteld wanneer **module type** is **manifest**.</span><span class="sxs-lookup"><span data-stu-id="48327-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="48327-150">Reflectie in het veld **ImplementingAssembly** detecteert bronnen in een module.</span><span class="sxs-lookup"><span data-stu-id="48327-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="48327-151">Dit betekent dat u resources kunt detecteren die in Power shell of andere beheerde talen zijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="48327-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="48327-152">Velden met initialisatie functies:</span><span class="sxs-lookup"><span data-stu-id="48327-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="48327-153">`Static`wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="48327-153">`Static` is supported.</span></span> <span data-ttu-id="48327-154">Het werkt als een kenmerk, zoals de type beperkingen.</span><span class="sxs-lookup"><span data-stu-id="48327-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="48327-155">Dit kan in een wille keurige volg orde worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="48327-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="48327-156">Een type is optioneel.</span><span class="sxs-lookup"><span data-stu-id="48327-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="48327-157">Alle leden zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="48327-157">All members are public.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="48327-158">Constructors en instantiëring</span><span class="sxs-lookup"><span data-stu-id="48327-158">Constructors and instantiation</span></span>

<span data-ttu-id="48327-159">Power shell-klassen kunnen constructors hebben.</span><span class="sxs-lookup"><span data-stu-id="48327-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="48327-160">Ze hebben dezelfde naam als hun klasse.</span><span class="sxs-lookup"><span data-stu-id="48327-160">They have the same name as their class.</span></span> <span data-ttu-id="48327-161">Constructors kunnen overbelast zijn.</span><span class="sxs-lookup"><span data-stu-id="48327-161">Constructors can be overloaded.</span></span> <span data-ttu-id="48327-162">Statische Constructors worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="48327-162">Static constructors are supported.</span></span> <span data-ttu-id="48327-163">Eigenschappen met initialisatie-expressies worden geïnitialiseerd voordat code in een constructor wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="48327-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="48327-164">Statische eigenschappen worden geïnitialiseerd voordat de hoofd tekst van een statische constructor, en instantie-eigenschappen worden geïnitialiseerd vóór de hoofd tekst van de niet-statische constructor.</span><span class="sxs-lookup"><span data-stu-id="48327-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="48327-165">Op dit moment is er geen syntaxis voor het aanroepen van een constructor vanuit een andere constructor (zoals de C- \# syntaxis ": This ()").</span><span class="sxs-lookup"><span data-stu-id="48327-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="48327-166">De tijdelijke oplossing is het definiëren van een algemene `Init()` methode.</span><span class="sxs-lookup"><span data-stu-id="48327-166">The workaround is to define a common `Init()` method.</span></span>

#### <a name="creating-instances"></a><span data-ttu-id="48327-167">Instanties maken</span><span class="sxs-lookup"><span data-stu-id="48327-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="48327-168">In Power shell 5,0 `New-Object` werkt niet met klassen die in Power shell zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="48327-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="48327-169">De type naam is ook op een lexicale zicht bare locatie, wat betekent dat deze niet zichtbaar is buiten de module of het script waarmee de klasse wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="48327-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="48327-170">Functies kunnen exemplaren retour neren van een klasse die is gedefinieerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="48327-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="48327-171">Deze instanties werken buiten de module of het script.</span><span class="sxs-lookup"><span data-stu-id="48327-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="48327-172">Instantiëren met behulp van de standaardconstructor.</span><span class="sxs-lookup"><span data-stu-id="48327-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="48327-173">Een constructor met een para meter aanroepen</span><span class="sxs-lookup"><span data-stu-id="48327-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="48327-174">Een matrix wordt door gegeven aan een constructor met meerdere para meters.</span><span class="sxs-lookup"><span data-stu-id="48327-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="48327-175">De pseudo-statische methode `new()` werkt met .net-typen, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="48327-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a><span data-ttu-id="48327-176">Constructors detecteren</span><span class="sxs-lookup"><span data-stu-id="48327-176">Discovering constructors</span></span>

<span data-ttu-id="48327-177">U kunt nu overbelasting van constructor zien met `Get-Member` , of zoals in dit voor beeld wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="48327-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="48327-178">`Get-Member -Static`Hierin worden constructors weer gegeven, zodat u Overloads kunt bekijken, zoals een andere methode.</span><span class="sxs-lookup"><span data-stu-id="48327-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="48327-179">De prestaties van deze syntaxis zijn ook aanzienlijk sneller dan `New-Object` .</span><span class="sxs-lookup"><span data-stu-id="48327-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

### <a name="methods"></a><span data-ttu-id="48327-180">Methoden</span><span class="sxs-lookup"><span data-stu-id="48327-180">Methods</span></span>

<span data-ttu-id="48327-181">Een Power shell-klassen methode wordt geïmplementeerd als een **script Block** die alleen een eind blok heeft.</span><span class="sxs-lookup"><span data-stu-id="48327-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="48327-182">Alle methoden zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="48327-182">All methods are public.</span></span> <span data-ttu-id="48327-183">Hieronder ziet u een voor beeld van het definiëren van een methode met de naam **DoSomething**.</span><span class="sxs-lookup"><span data-stu-id="48327-183">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="48327-184">Aanroep methode:</span><span class="sxs-lookup"><span data-stu-id="48327-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="48327-185">Overbelaste methoden worden ook ondersteund.</span><span class="sxs-lookup"><span data-stu-id="48327-185">Overloaded methods are also supported.</span></span>

### <a name="properties"></a><span data-ttu-id="48327-186">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="48327-186">Properties</span></span>

<span data-ttu-id="48327-187">Alle eigenschappen zijn openbaar.</span><span class="sxs-lookup"><span data-stu-id="48327-187">All properties are public.</span></span> <span data-ttu-id="48327-188">Eigenschappen vereisen een nieuwe regel of een punt komma.</span><span class="sxs-lookup"><span data-stu-id="48327-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="48327-189">Als er geen object type is opgegeven, is het eigenschaps type object.</span><span class="sxs-lookup"><span data-stu-id="48327-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="48327-190">Eigenschappen die gebruikmaken van validatie-of argument transformatie kenmerken (zoals `[ValidateSet("aaa")]` ) werken zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="48327-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

### <a name="hidden"></a><span data-ttu-id="48327-191">Verborgen</span><span class="sxs-lookup"><span data-stu-id="48327-191">Hidden</span></span>

<span data-ttu-id="48327-192">Er is een nieuw tref woord, `Hidden` , toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="48327-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="48327-193">`Hidden`kan worden toegepast op Eigenschappen en methoden (inclusief constructors).</span><span class="sxs-lookup"><span data-stu-id="48327-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="48327-194">Verborgen leden zijn openbaar, maar worden niet weer gegeven in de uitvoer van `Get-Member` tenzij de `-Force` para meter is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="48327-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the `-Force` parameter is added.</span></span> <span data-ttu-id="48327-195">Verborgen leden worden niet opgenomen wanneer het tabblad wordt voltooid of gebruikmaakt van IntelliSense, tenzij de voltooiing plaatsvindt in de klasse die het verborgen lid definieert.</span><span class="sxs-lookup"><span data-stu-id="48327-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="48327-196">Er is een nieuw kenmerk, **System. Management. Automation. HiddenAttribute** toegevoegd, zodat \# de C-code dezelfde semantiek kan hebben in Power shell.</span><span class="sxs-lookup"><span data-stu-id="48327-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

### <a name="return-types"></a><span data-ttu-id="48327-197">Retour typen</span><span class="sxs-lookup"><span data-stu-id="48327-197">Return types</span></span>

<span data-ttu-id="48327-198">Retour type is een contract.</span><span class="sxs-lookup"><span data-stu-id="48327-198">Return type is a contract.</span></span> <span data-ttu-id="48327-199">De geretourneerde waarde wordt geconverteerd naar het verwachte type.</span><span class="sxs-lookup"><span data-stu-id="48327-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="48327-200">Als er geen retour type is opgegeven, is het retour type **void**.</span><span class="sxs-lookup"><span data-stu-id="48327-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="48327-201">Er zijn geen streaming van-objecten.</span><span class="sxs-lookup"><span data-stu-id="48327-201">There is no streaming of objects.</span></span> <span data-ttu-id="48327-202">Objecten kunnen niet opzettelijk of per ongeluk naar de pijp lijn worden geschreven.</span><span class="sxs-lookup"><span data-stu-id="48327-202">Objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="attributes"></a><span data-ttu-id="48327-203">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="48327-203">Attributes</span></span>

<span data-ttu-id="48327-204">Er zijn twee nieuwe kenmerken, **dscresource bieden** en **DscProperty** toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="48327-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="48327-205">Lexicale bereik van variabelen</span><span class="sxs-lookup"><span data-stu-id="48327-205">Lexical scoping of variables</span></span>

<span data-ttu-id="48327-206">Hieronder ziet u een voor beeld van hoe lexicale scoping werkt in deze release.</span><span class="sxs-lookup"><span data-stu-id="48327-206">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="48327-207">End-to-end-voor beeld</span><span class="sxs-lookup"><span data-stu-id="48327-207">End-to-End Example</span></span>

<span data-ttu-id="48327-208">In het volgende voor beeld worden een aantal aangepaste klassen gemaakt voor het implementeren van een HTML Dynamic style sheet-taal (DSL).</span><span class="sxs-lookup"><span data-stu-id="48327-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="48327-209">Vervolgens voegt het voor beeld hulp functies toe om specifieke element typen te maken als onderdeel van de klasse element, zoals kopstijlen en tabellen, omdat typen niet buiten het bereik van een module kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="48327-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
