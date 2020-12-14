---
description: Hierin wordt beschreven hoe u klassen kunt gebruiken om uw eigen aangepaste typen te maken.
Locale: en-US
ms.date: 09/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes
ms.openlocfilehash: 15e56d00d607f7129be4ffd0a515bd237951f512
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706121"
---
# <a name="about-classes"></a><span data-ttu-id="e568e-103">Over klassen</span><span class="sxs-lookup"><span data-stu-id="e568e-103">About Classes</span></span>

## <a name="short-description"></a><span data-ttu-id="e568e-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="e568e-104">Short description</span></span>
<span data-ttu-id="e568e-105">Hierin wordt beschreven hoe u klassen kunt gebruiken om uw eigen aangepaste typen te maken.</span><span class="sxs-lookup"><span data-stu-id="e568e-105">Describes how you can use classes to create your own custom types.</span></span>

## <a name="long-description"></a><span data-ttu-id="e568e-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="e568e-106">Long description</span></span>

<span data-ttu-id="e568e-107">Power shell 5,0 voegt een formele syntaxis toe om klassen en andere door de gebruiker gedefinieerde typen te definiëren.</span><span class="sxs-lookup"><span data-stu-id="e568e-107">PowerShell 5.0 adds a formal syntax to define classes and other user-defined types.</span></span> <span data-ttu-id="e568e-108">Dankzij de toevoeging van klassen kunnen ontwikkel aars en IT-professionals Power shell gebruiken voor een groter aantal use cases.</span><span class="sxs-lookup"><span data-stu-id="e568e-108">The addition of classes enables developers and IT professionals to embrace PowerShell for a wider range of use cases.</span></span> <span data-ttu-id="e568e-109">Het vereenvoudigt de ontwikkeling van Power shell-artefacten en versnelt de dekking van beheer oppervlakken.</span><span class="sxs-lookup"><span data-stu-id="e568e-109">It simplifies development of PowerShell artifacts and accelerates coverage of management surfaces.</span></span>

<span data-ttu-id="e568e-110">Een klassen declaratie is een blauw druk die wordt gebruikt om exemplaren van objecten te maken tijdens de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="e568e-110">A class declaration is a blueprint used to create instances of objects at run time.</span></span> <span data-ttu-id="e568e-111">Wanneer u een klasse definieert, is de naam van de klasse de naam van het type.</span><span class="sxs-lookup"><span data-stu-id="e568e-111">When you define a class, the class name is the name of the type.</span></span> <span data-ttu-id="e568e-112">Als u bijvoorbeeld een klasse met de naam **apparaat** declareert en een variabele initialiseert `$dev` naar een nieuw exemplaar van **apparaat**, `$dev` is een object of een exemplaar van het type **apparaat**.</span><span class="sxs-lookup"><span data-stu-id="e568e-112">For example, if you declare a class named **Device** and initialize a variable `$dev` to a new instance of **Device**, `$dev` is an object or instance of type **Device**.</span></span> <span data-ttu-id="e568e-113">Elk exemplaar van het **apparaat** kan verschillende waarden in de eigenschappen hebben.</span><span class="sxs-lookup"><span data-stu-id="e568e-113">Each instance of **Device** can have different values in its properties.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="e568e-114">Ondersteunde scenario's</span><span class="sxs-lookup"><span data-stu-id="e568e-114">Supported scenarios</span></span>

- <span data-ttu-id="e568e-115">Definieer aangepaste typen in Power shell met behulp van bekende object georiënteerde programmeer semantiek zoals klassen, eigenschappen, methoden, overname, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="e568e-115">Define custom types in PowerShell using familiar object-oriented programming semantics like classes, properties, methods, inheritance, etc.</span></span>
- <span data-ttu-id="e568e-116">Typen fout opsporing met behulp van de Power shell-taal.</span><span class="sxs-lookup"><span data-stu-id="e568e-116">Debug types using the PowerShell language.</span></span>
- <span data-ttu-id="e568e-117">Met formele mechanismen uitzonde ringen genereren en verwerken.</span><span class="sxs-lookup"><span data-stu-id="e568e-117">Generate and handle exceptions using formal mechanisms.</span></span>
- <span data-ttu-id="e568e-118">DSC-resources en de bijbehorende typen definiëren met behulp van de Power shell-taal.</span><span class="sxs-lookup"><span data-stu-id="e568e-118">Define DSC resources and their associated types by using the PowerShell language.</span></span>

## <a name="syntax"></a><span data-ttu-id="e568e-119">Syntax</span><span class="sxs-lookup"><span data-stu-id="e568e-119">Syntax</span></span>

<span data-ttu-id="e568e-120">Klassen worden gedeclareerd met de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="e568e-120">Classes are declared using the following syntax:</span></span>

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

<span data-ttu-id="e568e-121">Klassen worden geïnstantieerd met een van de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="e568e-121">Classes are instantiated using either of the following syntaxes:</span></span>

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> <span data-ttu-id="e568e-122">Wanneer u de `[<class-name>]::new()` syntaxis gebruikt, zijn haakjes rond de naam van de klasse verplicht.</span><span class="sxs-lookup"><span data-stu-id="e568e-122">When using the `[<class-name>]::new()` syntax, brackets around the class name are mandatory.</span></span> <span data-ttu-id="e568e-123">De vier Kante haken geven een type definitie voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="e568e-123">The brackets signal a type definition for PowerShell.</span></span>

### <a name="example-syntax-and-usage"></a><span data-ttu-id="e568e-124">Voorbeeld syntaxis en-gebruik</span><span class="sxs-lookup"><span data-stu-id="e568e-124">Example syntax and usage</span></span>

<span data-ttu-id="e568e-125">In dit voor beeld ziet u de minimale syntaxis die nodig is om een bruikbare klasse te maken.</span><span class="sxs-lookup"><span data-stu-id="e568e-125">This example shows the minimum syntax needed to create a usable class.</span></span>

```powershell
class Device {
    [string]$Brand
}

$dev = [Device]::new()
$dev.Brand = "Microsoft"
$dev
```

```Output
Brand
-----
Microsoft
```

## <a name="class-properties"></a><span data-ttu-id="e568e-126">Klasse-eigenschappen</span><span class="sxs-lookup"><span data-stu-id="e568e-126">Class properties</span></span>

<span data-ttu-id="e568e-127">Eigenschappen zijn variabelen die worden gedeclareerd bij een klasse-bereik.</span><span class="sxs-lookup"><span data-stu-id="e568e-127">Properties are variables declared at class scope.</span></span> <span data-ttu-id="e568e-128">Een eigenschap kan van een ingebouwd type of een exemplaar van een andere klasse zijn.</span><span class="sxs-lookup"><span data-stu-id="e568e-128">A property may be of any built-in type or an instance of another class.</span></span> <span data-ttu-id="e568e-129">Klassen hebben geen beperkingen voor het aantal eigenschappen dat ze hebben.</span><span class="sxs-lookup"><span data-stu-id="e568e-129">Classes have no restriction in the number of properties they have.</span></span>

### <a name="example-class-with-simple-properties"></a><span data-ttu-id="e568e-130">Voorbeeld klasse met eenvoudige eigenschappen</span><span class="sxs-lookup"><span data-stu-id="e568e-130">Example class with simple properties</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

$device = [Device]::new()
$device.Brand = "Microsoft"
$device.Model = "Surface Pro 4"
$device.VendorSku = "5072641000"

$device
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-complex-types-in-class-properties"></a><span data-ttu-id="e568e-131">Voor beelden van complexe typen in klasse-eigenschappen</span><span class="sxs-lookup"><span data-stu-id="e568e-131">Example complex types in class properties</span></span>

<span data-ttu-id="e568e-132">In dit voor beeld wordt een lege **rack** klasse gedefinieerd met behulp **van de apparaatklasse** .</span><span class="sxs-lookup"><span data-stu-id="e568e-132">This example defines an empty **Rack** class using the **Device** class.</span></span> <span data-ttu-id="e568e-133">Hieronder ziet u hoe u apparaten aan het rek kunt toevoegen en hoe u begint met een vooraf geladen rek.</span><span class="sxs-lookup"><span data-stu-id="e568e-133">The examples, following this one, show how to add devices to the rack and how to start with a pre-loaded rack.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

class Rack {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new(8)

}

$rack = [Rack]::new()

$rack
```

```Output

Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, $null, $null...}


```

## <a name="class-methods"></a><span data-ttu-id="e568e-134">Klasse-methoden</span><span class="sxs-lookup"><span data-stu-id="e568e-134">Class methods</span></span>

<span data-ttu-id="e568e-135">Met methoden worden de acties gedefinieerd die een klasse kan uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="e568e-135">Methods define the actions that a class can perform.</span></span> <span data-ttu-id="e568e-136">Methoden kunnen para meters hebben die invoer gegevens opgeven.</span><span class="sxs-lookup"><span data-stu-id="e568e-136">Methods may take parameters that provide input data.</span></span> <span data-ttu-id="e568e-137">De methoden kunnen uitvoer retour neren.</span><span class="sxs-lookup"><span data-stu-id="e568e-137">Methods can return output.</span></span> <span data-ttu-id="e568e-138">Gegevens die door een methode worden geretourneerd, kunnen elk gedefinieerd gegevens type zijn.</span><span class="sxs-lookup"><span data-stu-id="e568e-138">Data returned by a method can be any defined data type.</span></span>

<span data-ttu-id="e568e-139">Wanneer u een methode voor een klasse definieert, verwijst u naar het huidige klassen object met behulp van de `$this` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="e568e-139">When defining a method for a class, you reference the current class object by using the `$this` automatic variable.</span></span> <span data-ttu-id="e568e-140">Hiermee krijgt u toegang tot eigenschappen en andere methoden die in de huidige klasse zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e568e-140">This allows you to access properties and other methods defined in the current class.</span></span>

### <a name="example-simple-class-with-properties-and-methods"></a><span data-ttu-id="e568e-141">Voor beeld van een eenvoudige klasse met eigenschappen en methoden</span><span class="sxs-lookup"><span data-stu-id="e568e-141">Example simple class with properties and methods</span></span>

<span data-ttu-id="e568e-142">De **rack** klasse uitbreiden om apparaten toe te voegen aan of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e568e-142">Extending the **Rack** class to add and remove devices to or from it.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    [string]ToString(){
        return ("{0}|{1}|{2}" -f $this.Brand, $this.Model, $this.VendorSku)
    }
}

class Rack {
    [int]$Slots = 8
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void]RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }

    [int[]] GetAvailableSlots(){
        [int]$i = 0
        return @($this.Devices.foreach{ if($_ -eq $null){$i}; $i++})
    }
}

$rack = [Rack]::new()

$surface = [Device]::new()
$surface.Brand = "Microsoft"
$surface.Model = "Surface Pro 4"
$surface.VendorSku = "5072641000"

$rack.AddDevice($surface, 2)

$rack
$rack.GetAvailableSlots()
```

```Output

Slots     : 8
Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, Microsoft|Surface Pro 4|5072641000, $null...}

0
1
3
4
5
6
7

```

## <a name="output-in-class-methods"></a><span data-ttu-id="e568e-143">Uitvoer in klasse-methoden</span><span class="sxs-lookup"><span data-stu-id="e568e-143">Output in class methods</span></span>

<span data-ttu-id="e568e-144">Voor methoden moet een retour type zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e568e-144">Methods should have a return type defined.</span></span> <span data-ttu-id="e568e-145">Als een methode geen uitvoer retourneert, moet het uitvoer type zijn `[void]` .</span><span class="sxs-lookup"><span data-stu-id="e568e-145">If a method doesn't return output, then the output type should be `[void]`.</span></span>

<span data-ttu-id="e568e-146">Bij klassen methoden worden er geen objecten verzonden naar de pijp lijn, behalve die in de `return` instructie vermeld.</span><span class="sxs-lookup"><span data-stu-id="e568e-146">In class methods, no objects get sent to the pipeline except those mentioned in the `return` statement.</span></span> <span data-ttu-id="e568e-147">Er is geen onbedoelde uitvoer van de code naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="e568e-147">There's no accidental output to the pipeline from the code.</span></span>

> [!NOTE]
> <span data-ttu-id="e568e-148">Dit wijkt fundamenteel af van de manier waarop Power shell-functies uitvoer afhandelen, waarbij alles naar de pijp lijn gaat.</span><span class="sxs-lookup"><span data-stu-id="e568e-148">This is fundamentally different from how PowerShell functions handle output, where everything goes to the pipeline.</span></span>

<span data-ttu-id="e568e-149">Niet-afsluit fouten die naar de fout stroom zijn geschreven vanuit een klassen methode, worden niet door gegeven.</span><span class="sxs-lookup"><span data-stu-id="e568e-149">Non-terminating errors written to the error stream from inside a class method are not passed through.</span></span> <span data-ttu-id="e568e-150">U moet gebruiken `throw` om een afsluitende fout op te halen.</span><span class="sxs-lookup"><span data-stu-id="e568e-150">You must use `throw` to surface a terminating error.</span></span>
<span data-ttu-id="e568e-151">Met de `Write-*` cmdlets kunt u nog steeds vanuit een klassen methode naar de uitvoer stromen van Power shell schrijven.</span><span class="sxs-lookup"><span data-stu-id="e568e-151">Using the `Write-*` cmdlets, you can still write to PowerShell's output streams from within a class method.</span></span> <span data-ttu-id="e568e-152">Dit moet echter worden vermeden, zodat de methode objecten alleen verzendt met behulp van de- `return` instructie.</span><span class="sxs-lookup"><span data-stu-id="e568e-152">However, this should be avoided so that the method emits objects using only the `return` statement.</span></span>

### <a name="method-output"></a><span data-ttu-id="e568e-153">Methode-uitvoer</span><span class="sxs-lookup"><span data-stu-id="e568e-153">Method output</span></span>

<span data-ttu-id="e568e-154">In dit voor beeld ziet u geen onbedoelde uitvoer naar de pijp lijn vanuit klassen methoden, behalve op de- `return` instructie.</span><span class="sxs-lookup"><span data-stu-id="e568e-154">This example demonstrates no accidental output to the pipeline from class methods, except on the `return` statement.</span></span>

```powershell
class FunWithIntegers
{
    [int[]]$Integers = 0..10

    [int[]]GetOddIntegers(){
        return $this.Integers.Where({ ($_ % 2) })
    }

    [void] GetEvenIntegers(){
        # this following line doesn't go to the pipeline
        $this.Integers.Where({ ($_ % 2) -eq 0})
    }

    [string]SayHello(){
        # this following line doesn't go to the pipeline
        "Good Morning"

        # this line goes to the pipeline
        return "Hello World"
    }
}

$ints = [FunWithIntegers]::new()
$ints.GetOddIntegers()
$ints.GetEvenIntegers()
$ints.SayHello()
```

```Output
1
3
5
7
9
Hello World

```

## <a name="constructor"></a><span data-ttu-id="e568e-155">Constructor</span><span class="sxs-lookup"><span data-stu-id="e568e-155">Constructor</span></span>

<span data-ttu-id="e568e-156">Met constructors kunt u standaard waarden instellen en object logica valideren op het moment dat u het exemplaar van de klasse maakt.</span><span class="sxs-lookup"><span data-stu-id="e568e-156">Constructors enable you to set default values and validate object logic at the moment of creating the instance of the class.</span></span> <span data-ttu-id="e568e-157">Constructors hebben dezelfde naam als de klasse.</span><span class="sxs-lookup"><span data-stu-id="e568e-157">Constructors have the same name as the class.</span></span> <span data-ttu-id="e568e-158">Constructors kunnen argumenten hebben om de gegevens leden van het nieuwe object te initialiseren.</span><span class="sxs-lookup"><span data-stu-id="e568e-158">Constructors might have arguments, to initialize the data members of the new object.</span></span>

<span data-ttu-id="e568e-159">Er kunnen geen of meer constructors zijn gedefinieerd voor de klasse.</span><span class="sxs-lookup"><span data-stu-id="e568e-159">The class can have zero or more constructors defined.</span></span> <span data-ttu-id="e568e-160">Als er geen constructor is gedefinieerd, krijgt de klasse een standaard parameterloze constructor.</span><span class="sxs-lookup"><span data-stu-id="e568e-160">If no constructor is defined, the class is given a default parameterless constructor.</span></span> <span data-ttu-id="e568e-161">Deze constructor initialiseert alle leden op hun standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="e568e-161">This constructor initializes all members to their default values.</span></span> <span data-ttu-id="e568e-162">Object typen en teken reeksen krijgen Null-waarden.</span><span class="sxs-lookup"><span data-stu-id="e568e-162">Object types and strings are given null values.</span></span> <span data-ttu-id="e568e-163">Wanneer u een constructor definieert, wordt er geen standaard parameterloze constructor gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e568e-163">When you define constructor, no default parameterless constructor is created.</span></span> <span data-ttu-id="e568e-164">Maak een parameterloze constructor als deze nodig is.</span><span class="sxs-lookup"><span data-stu-id="e568e-164">Create a parameterless constructor if one is needed.</span></span>

### <a name="constructor-basic-syntax"></a><span data-ttu-id="e568e-165">Basis syntaxis van constructor</span><span class="sxs-lookup"><span data-stu-id="e568e-165">Constructor basic syntax</span></span>

<span data-ttu-id="e568e-166">In dit voor beeld wordt de apparaatklasse gedefinieerd met eigenschappen en een constructor.</span><span class="sxs-lookup"><span data-stu-id="e568e-166">In this example, the Device class is defined with properties and a constructor.</span></span>
<span data-ttu-id="e568e-167">Als u deze klasse wilt gebruiken, moet de gebruiker waarden opgeven voor de para meters die worden weer gegeven in de constructor.</span><span class="sxs-lookup"><span data-stu-id="e568e-167">To use this class, the user is required to provide values for the parameters listed in the constructor.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$surface
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-with-multiple-constructors"></a><span data-ttu-id="e568e-168">Voor beeld met meerdere Constructors</span><span class="sxs-lookup"><span data-stu-id="e568e-168">Example with multiple constructors</span></span>

<span data-ttu-id="e568e-169">In dit voor beeld wordt **de apparaatklasse** gedefinieerd met eigenschappen, een standaardconstructor en een constructor om het exemplaar te initialiseren.</span><span class="sxs-lookup"><span data-stu-id="e568e-169">In this example, the **Device** class is defined with properties, a default constructor, and a constructor to initialize the instance.</span></span>

<span data-ttu-id="e568e-170">De standaardconstructor stelt het **merk** in op **ongedefinieerd** en verlaat het **model** en de **leverancier-SKU** met Null-waarden.</span><span class="sxs-lookup"><span data-stu-id="e568e-170">The default constructor sets the **brand** to **Undefined**, and leaves **model** and **vendor-sku** with null values.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(){
        $this.Brand = 'Undefined'
    }

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$somedevice = [Device]::new()
[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$somedevice
$surface
```

```Output
Brand       Model           VendorSku
-----       -----           ---------
Undefined
Microsoft   Surface Pro 4   5072641000
```

## <a name="hidden-attribute"></a><span data-ttu-id="e568e-171">Verborgen kenmerk</span><span class="sxs-lookup"><span data-stu-id="e568e-171">Hidden attribute</span></span>

<span data-ttu-id="e568e-172">Het `hidden` kenmerk verbergt een eigenschap of methode.</span><span class="sxs-lookup"><span data-stu-id="e568e-172">The `hidden` attribute hides a property or method.</span></span> <span data-ttu-id="e568e-173">De eigenschap of methode is nog steeds toegankelijk voor de gebruiker en is beschikbaar in alle bereiken waarin het object beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="e568e-173">The property or method is still accessible to the user and is available in all scopes in which the object is available.</span></span> <span data-ttu-id="e568e-174">Verborgen leden worden verborgen in de `Get-Member` cmdlet en kunnen niet worden weer gegeven met Tab-aanvulling of IntelliSense buiten de klassedefinitie.</span><span class="sxs-lookup"><span data-stu-id="e568e-174">Hidden members are hidden from the `Get-Member` cmdlet and can't be displayed using tab completion or IntelliSense outside the class definition.</span></span>

<span data-ttu-id="e568e-175">Zie [About_hidden](About_hidden.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e568e-175">For more information, see [About_hidden](About_hidden.md).</span></span>

### <a name="example-using-hidden-attributes"></a><span data-ttu-id="e568e-176">Voor beeld met verborgen kenmerken</span><span class="sxs-lookup"><span data-stu-id="e568e-176">Example using hidden attributes</span></span>

<span data-ttu-id="e568e-177">Wanneer een **rek** -object wordt gemaakt, is het aantal sleuven voor apparaten een vaste waarde die op geen enkel moment mag worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="e568e-177">When a **Rack** object is created, the number of slots for devices is a fixed value that shouldn't be changed at any time.</span></span> <span data-ttu-id="e568e-178">Deze waarde is bekend tijdens het maken.</span><span class="sxs-lookup"><span data-stu-id="e568e-178">This value is known at creation time.</span></span>

<span data-ttu-id="e568e-179">Met behulp van het kenmerk Hidden kan de ontwikkelaar het aantal sleuven verbergen en wordt voor komen dat onbedoeld de grootte van het rek wijzigt.</span><span class="sxs-lookup"><span data-stu-id="e568e-179">Using the hidden attribute allows the developer to keep the number of slots hidden and prevents unintentional changes the size of the rack.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    [int] hidden $Slots = 8
    [string]$Brand
    [string]$Model
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)
    }
}

[Rack]$r1 = [Rack]::new("Microsoft", "Surface Pro 4", 16)

$r1
$r1.Devices.Length
$r1.Slots
```

```Output
Brand     Model         Devices
-----     -----         -------
Microsoft Surface Pro 4 {$null, $null, $null, $null...}
16
16
```

<span data-ttu-id="e568e-180">De eigenschap voor de **sleuf** wordt niet weer gegeven in de `$r1` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e568e-180">Notice **Slots** property isn't shown in `$r1` output.</span></span> <span data-ttu-id="e568e-181">De grootte is echter gewijzigd door de constructor.</span><span class="sxs-lookup"><span data-stu-id="e568e-181">However, the size was changed by the constructor.</span></span>

## <a name="static-attribute"></a><span data-ttu-id="e568e-182">Statisch kenmerk</span><span class="sxs-lookup"><span data-stu-id="e568e-182">Static attribute</span></span>

<span data-ttu-id="e568e-183">Het `static` kenmerk definieert een eigenschap of een methode die voor komt in de klasse en waarvoor geen exemplaar is vereist.</span><span class="sxs-lookup"><span data-stu-id="e568e-183">The `static` attribute defines a property or a method that exists in the class and needs no instance.</span></span>

<span data-ttu-id="e568e-184">Een statische eigenschap is altijd beschikbaar, onafhankelijk van klasse-instantiëring.</span><span class="sxs-lookup"><span data-stu-id="e568e-184">A static property is always available, independent of class instantiation.</span></span> <span data-ttu-id="e568e-185">Een statische eigenschap wordt gedeeld in alle instanties van de klasse.</span><span class="sxs-lookup"><span data-stu-id="e568e-185">A static property is shared across all instances of the class.</span></span> <span data-ttu-id="e568e-186">Een statische methode is altijd beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="e568e-186">A static method is available always.</span></span> <span data-ttu-id="e568e-187">Alle statische eigenschappen Live voor de hele sessie duur.</span><span class="sxs-lookup"><span data-stu-id="e568e-187">All static properties live for the entire session span.</span></span>

### <a name="example-using-static-attributes-and-methods"></a><span data-ttu-id="e568e-188">Voor beeld van het gebruik van statische kenmerken en methoden</span><span class="sxs-lookup"><span data-stu-id="e568e-188">Example using static attributes and methods</span></span>

<span data-ttu-id="e568e-189">Ga ervan uit dat de racks die hier worden geïnstantieerd, zich in uw Data Center bevinden.</span><span class="sxs-lookup"><span data-stu-id="e568e-189">Assume the racks instantiated here exist in your data center.</span></span> <span data-ttu-id="e568e-190">Daarom wilt u de rekken in uw code bijhouden.</span><span class="sxs-lookup"><span data-stu-id="e568e-190">So, you would like to keep track of the racks in your code.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    hidden [int] $Slots = 8
    static [Rack[]]$InstalledRacks = @()
    [string]$Brand
    [string]$Model
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [string]$id, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.AssetId = $id
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)

        ## add rack to installed racks
        [Rack]::InstalledRacks += $this
    }

    static [void]PowerOffRacks(){
        foreach ($rack in [Rack]::InstalledRacks) {
            Write-Warning ("Turning off rack: " + ($rack.AssetId))
        }
    }
}
```

### <a name="testing-static-property-and-method-exist"></a><span data-ttu-id="e568e-191">Statische eigenschap en methode voor testen bestaan</span><span class="sxs-lookup"><span data-stu-id="e568e-191">Testing static property and method exist</span></span>

```
PS> [Rack]::InstalledRacks.Length
0

PS> [Rack]::PowerOffRacks()

PS> (1..10) | ForEach-Object {
>>   [Rack]::new("Adatum Corporation", "Standard-16",
>>     $_.ToString("Std0000"), 16)
>> } > $null

PS> [Rack]::InstalledRacks.Length
10

PS> [Rack]::InstalledRacks[3]
Brand              Model       AssetId Devices
-----              -----       ------- -------
Adatum Corporation Standard-16 Std0004 {$null, $null, $null, $null...}

PS> [Rack]::PowerOffRacks()
WARNING: Turning off rack: Std0001
WARNING: Turning off rack: Std0002
WARNING: Turning off rack: Std0003
WARNING: Turning off rack: Std0004
WARNING: Turning off rack: Std0005
WARNING: Turning off rack: Std0006
WARNING: Turning off rack: Std0007
WARNING: Turning off rack: Std0008
WARNING: Turning off rack: Std0009
WARNING: Turning off rack: Std0010
```

<span data-ttu-id="e568e-192">U ziet dat het aantal racks telkens wordt verhoogd wanneer u dit voor beeld uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e568e-192">Notice that the number of racks increases each time you run this example.</span></span>

## <a name="property-validation-attributes"></a><span data-ttu-id="e568e-193">Kenmerken van eigenschappen validatie</span><span class="sxs-lookup"><span data-stu-id="e568e-193">Property validation attributes</span></span>

<span data-ttu-id="e568e-194">Met validatie kenmerken kunt u testen of waarden die zijn gegeven aan eigenschappen voldoen aan gedefinieerde vereisten.</span><span class="sxs-lookup"><span data-stu-id="e568e-194">Validation attributes allow you to test that values given to properties meet defined requirements.</span></span> <span data-ttu-id="e568e-195">Validatie wordt geactiveerd zodra de waarde is toegewezen.</span><span class="sxs-lookup"><span data-stu-id="e568e-195">Validation is triggered the moment that the value is assigned.</span></span> <span data-ttu-id="e568e-196">Zie [about_functions_advanced_parameters](about_functions_advanced_parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e568e-196">See [about_functions_advanced_parameters](about_functions_advanced_parameters.md).</span></span>

### <a name="example-using-validation-attributes"></a><span data-ttu-id="e568e-197">Voor beeld met validatie kenmerken</span><span class="sxs-lookup"><span data-stu-id="e568e-197">Example using validation attributes</span></span>

```powershell
class Device {
    [ValidateNotNullOrEmpty()][string]$Brand
    [ValidateNotNullOrEmpty()][string]$Model
}

[Device]$dev = [Device]::new()

Write-Output "Testing dev"
$dev

$dev.Brand = ""
```

```Output
Testing dev

Brand Model
----- -----

Exception setting "Brand": "The argument is null or empty. Provide an
argument that is not null or empty, and then try the command again."
At C:\tmp\Untitled-5.ps1:11 char:1
+ $dev.Brand = ""
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], SetValueInvocationException
    + FullyQualifiedErrorId : ExceptionWhenSetting
```

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="e568e-198">Overname in Power shell-klassen</span><span class="sxs-lookup"><span data-stu-id="e568e-198">Inheritance in PowerShell classes</span></span>

<span data-ttu-id="e568e-199">U kunt een klasse uitbreiden door een nieuwe klasse te maken die van een bestaande klasse is afgeleid.</span><span class="sxs-lookup"><span data-stu-id="e568e-199">You can extend a class by creating a new class that derives from an existing class.</span></span> <span data-ttu-id="e568e-200">De afgeleide klasse neemt de eigenschappen van de basis klasse over.</span><span class="sxs-lookup"><span data-stu-id="e568e-200">The derived class inherits the properties of the base class.</span></span> <span data-ttu-id="e568e-201">U kunt methoden en eigenschappen indien nodig toevoegen of onderdrukken.</span><span class="sxs-lookup"><span data-stu-id="e568e-201">You can add or override methods and properties as required.</span></span>

<span data-ttu-id="e568e-202">Power shell biedt geen ondersteuning voor meerdere overname.</span><span class="sxs-lookup"><span data-stu-id="e568e-202">PowerShell does not support multiple inheritance.</span></span> <span data-ttu-id="e568e-203">Klassen kunnen niet overnemen van meer dan een klasse.</span><span class="sxs-lookup"><span data-stu-id="e568e-203">Classes cannot inherit from more than one class.</span></span> <span data-ttu-id="e568e-204">U kunt echter wel interfaces voor dat doel gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e568e-204">However, you can use interfaces for that purpose.</span></span>

<span data-ttu-id="e568e-205">Overname-implementatie wordt gedefinieerd door de `:` operator; wat betekent dat deze klasse moet worden uitgebreid of dat deze interfaces worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="e568e-205">Inheritance implementation is defined by the `:` operator; which means to extend this class or implements these interfaces.</span></span> <span data-ttu-id="e568e-206">De afgeleide klasse moet altijd links in de klassen declaratie staan.</span><span class="sxs-lookup"><span data-stu-id="e568e-206">The derived class should always be leftmost in the class declaration.</span></span>

### <a name="example-using-simple-inheritance-syntax"></a><span data-ttu-id="e568e-207">Voor beeld van eenvoudige overname syntaxis</span><span class="sxs-lookup"><span data-stu-id="e568e-207">Example using simple inheritance syntax</span></span>

<span data-ttu-id="e568e-208">In dit voor beeld ziet u de eenvoudige syntaxis van Power shell-klassen overname.</span><span class="sxs-lookup"><span data-stu-id="e568e-208">This example shows the simple PowerShell class inheritance syntax.</span></span>

```powershell
Class Derived : Base {...}
```

<span data-ttu-id="e568e-209">In dit voor beeld ziet u overname met een interface declaratie die afkomstig is van de basis klasse.</span><span class="sxs-lookup"><span data-stu-id="e568e-209">This example shows inheritance with an interface declaration coming after the base class.</span></span>

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a><span data-ttu-id="e568e-210">Voor beeld van eenvoudige overname in Power shell-klassen</span><span class="sxs-lookup"><span data-stu-id="e568e-210">Example of simple inheritance in PowerShell classes</span></span>

<span data-ttu-id="e568e-211">In dit voor beeld zijn de **rack** -en **apparaatklassen** die in de voor gaande voor beelden worden gebruikt, beter gedefinieerd voor: Vermijd het gebruik van herhalingen van eigenschappen, het beter uitlijnen van algemene eigenschappen en het opnieuw gebruiken van algemene bedrijfs logica.</span><span class="sxs-lookup"><span data-stu-id="e568e-211">In this example the **Rack** and **Device** classes used in the previous examples are better defined to: avoid property repetitions, better align common properties, and reuse common business logic.</span></span>

<span data-ttu-id="e568e-212">De meeste objecten in het Data Center zijn bedrijfs middelen, wat zinvol is om ze te volgen als activa.</span><span class="sxs-lookup"><span data-stu-id="e568e-212">Most objects in the data center are company assets, which makes sense to start tracking them as assets.</span></span> <span data-ttu-id="e568e-213">Apparaattypen worden gedefinieerd door de `DeviceType` opsomming. zie [about_Enum](about_Enum.md) voor meer informatie over inventarisaties.</span><span class="sxs-lookup"><span data-stu-id="e568e-213">Device types are defined by the `DeviceType` enumeration, see [about_Enum](about_Enum.md) for details on enumerations.</span></span>

<span data-ttu-id="e568e-214">In ons voor beeld worden alleen `Rack` `ComputeServer` de uitbrei dingen voor de klasse gedefinieerd `Device` .</span><span class="sxs-lookup"><span data-stu-id="e568e-214">In our example, we're only defining `Rack` and `ComputeServer`; both extensions to the `Device` class.</span></span>

```powershell
enum DeviceType {
    Undefined = 0
    Compute = 1
    Storage = 2
    Networking = 4
    Communications = 8
    Power = 16
    Rack = 32
}

class Asset {
    [string]$Brand
    [string]$Model
}

class Device : Asset {
    hidden [DeviceType]$devtype = [DeviceType]::Undefined
    [string]$Status

    [DeviceType] GetDeviceType(){
        return $this.devtype
    }
}

class ComputeServer : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Compute
    [string]$ProcessorIdentifier
    [string]$Hostname
}

class Rack : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Rack
    hidden [int]$Slots = 8

    [string]$Datacenter
    [string]$Location
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack (){
        ## Just create the default rack with 8 slots
    }

    Rack ([int]$s){
        ## Add argument validation logic here
        $this.Devices = [Device[]]::new($s)
    }

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void] RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }
}

$FirstRack = [Rack]::new(16)
$FirstRack.Status = "Operational"
$FirstRack.Datacenter = "PNW"
$FirstRack.Location = "F03R02.J10"

(0..15).ForEach({
    $ComputeServer = [ComputeServer]::new()
    $ComputeServer.Brand = "Fabrikam, Inc."       ## Inherited from Asset
    $ComputeServer.Model = "Fbk5040"              ## Inherited from Asset
    $ComputeServer.Status = "Installed"           ## Inherited from Device
    $ComputeServer.ProcessorIdentifier = "x64"    ## ComputeServer
    $ComputeServer.Hostname = ("r1s" + $_.ToString("000")) ## ComputeServer
    $FirstRack.AddDevice($ComputeServer, $_)
  })

$FirstRack
$FirstRack.Devices
```

```Output
Datacenter : PNW
Location   : F03R02.J10
Devices    : {r1s000, r1s001, r1s002, r1s003...}
Status     : Operational
Brand      :
Model      :

ProcessorIdentifier : x64
Hostname            : r1s000
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

ProcessorIdentifier : x64
Hostname            : r1s001
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

<... content truncated here for brevity ...>

ProcessorIdentifier : x64
Hostname            : r1s015
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040
```

### <a name="calling-base-class-constructors"></a><span data-ttu-id="e568e-215">Opbouw functie voor basis klassen aanroepen</span><span class="sxs-lookup"><span data-stu-id="e568e-215">Calling base class constructors</span></span>

<span data-ttu-id="e568e-216">Als u een basis klasse-constructor wilt aanroepen vanuit een subklasse, voegt u het `base` tref woord toe.</span><span class="sxs-lookup"><span data-stu-id="e568e-216">To invoke a base class constructor from a subclass, add the `base` keyword.</span></span>

```powershell
class Person {
    [int]$Age

    Person([int]$a)
    {
        $this.Age = $a
    }
}

class Child : Person
{
    [string]$School

    Child([int]$a, [string]$s ) : base($a) {
        $this.School = $s
    }
}

[Child]$littleone = [Child]::new(10, "Silver Fir Elementary School")

$littleone.Age
```

```Output

10
```

### <a name="invoke-base-class-methods"></a><span data-ttu-id="e568e-217">Methoden van basis klasse aanroepen</span><span class="sxs-lookup"><span data-stu-id="e568e-217">Invoke base class methods</span></span>

<span data-ttu-id="e568e-218">Als u bestaande methoden in subklassen wilt overschrijven, declareert u methoden met dezelfde naam en hand tekening.</span><span class="sxs-lookup"><span data-stu-id="e568e-218">To override existing methods in subclasses, declare methods using the same name and signature.</span></span>

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
}

[ChildClass1]::new().days()
```

```Output

2
```

<span data-ttu-id="e568e-219">Als u basis klassen methoden wilt aanroepen vanuit overschreven implementaties, moet u een cast-conversie uitvoeren naar de basis klasse ([baseclass] $this) bij het aanroepen.</span><span class="sxs-lookup"><span data-stu-id="e568e-219">To call base class methods from overridden implementations, cast to the base class ([baseclass]$this) on invocation.</span></span>

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
    [int]basedays() {return ([BaseClass]$this).days()}
}

[ChildClass1]::new().days()
[ChildClass1]::new().basedays()
```

```Output

2
1
```

### <a name="inheriting-from-interfaces"></a><span data-ttu-id="e568e-220">Overnemen van interfaces</span><span class="sxs-lookup"><span data-stu-id="e568e-220">Inheriting from interfaces</span></span>

<span data-ttu-id="e568e-221">Power shell-klassen kunnen een interface implementeren met dezelfde overname syntaxis die wordt gebruikt om basis klassen uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="e568e-221">PowerShell classes can implement an interface using the same inheritance syntax used to extend base classes.</span></span> <span data-ttu-id="e568e-222">Omdat interfaces meerdere overname toestaan, kan een Power shell-klasse die een interface implementeert, overnemen van meerdere typen door de type namen na de dubbele punt () te scheiden door `:` komma's ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="e568e-222">Because interfaces allow multiple inheritance, a PowerShell class implementing an interface may inherit from multiple types, by separating the type names after the colon (`:`) with commas (`,`).</span></span> <span data-ttu-id="e568e-223">Een Power shell-klasse die een interface implementeert, moet alle leden van die interface implementeren.</span><span class="sxs-lookup"><span data-stu-id="e568e-223">A PowerShell class that implements an interface must implement all the members of that interface.</span></span> <span data-ttu-id="e568e-224">Als u de implementatie-interface leden weglaat, treedt er een parseringsfout op in het script.</span><span class="sxs-lookup"><span data-stu-id="e568e-224">Omitting the implemention interface members causes a parse-time error in the script.</span></span>

> [!NOTE]
> <span data-ttu-id="e568e-225">Power shell biedt momenteel geen ondersteuning voor het declareren van nieuwe interfaces in het Power shell-script.</span><span class="sxs-lookup"><span data-stu-id="e568e-225">PowerShell does not currently support declaring new interfaces in PowerShell script.</span></span>

```powershell
class MyComparable : System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="importing-classes-from-a-powershell-module"></a><span data-ttu-id="e568e-226">Klassen importeren uit een Power shell-module</span><span class="sxs-lookup"><span data-stu-id="e568e-226">Importing classes from a PowerShell module</span></span>

<span data-ttu-id="e568e-227">`Import-Module` en de `#requires` instructie importeren alleen de module functies, aliassen en variabelen, zoals gedefinieerd door de module.</span><span class="sxs-lookup"><span data-stu-id="e568e-227">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="e568e-228">Klassen zijn niet geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="e568e-228">Classes are not imported.</span></span> <span data-ttu-id="e568e-229">`using module`Met de instructie worden de klassen geïmporteerd die in de module zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e568e-229">The `using module` statement imports the classes defined in the module.</span></span> <span data-ttu-id="e568e-230">Als de module niet in de huidige sessie is geladen, `using` mislukt de instructie.</span><span class="sxs-lookup"><span data-stu-id="e568e-230">If the module isn't loaded in the current session, the `using` statement fails.</span></span> <span data-ttu-id="e568e-231">Zie about_Using voor meer informatie over de `using` - [](about_Using.md)instructie.</span><span class="sxs-lookup"><span data-stu-id="e568e-231">For more information about the `using` statement, see [about_Using](about_Using.md).</span></span>

## <a name="the-psreference-type-is-not-supported-with-class-members"></a><span data-ttu-id="e568e-232">Het PSReference-type wordt niet ondersteund voor klasse-leden</span><span class="sxs-lookup"><span data-stu-id="e568e-232">The PSReference type is not supported with class members</span></span>

<span data-ttu-id="e568e-233">Het gebruik `[ref]` van het type cast met een klassetype is op de achtergrond mislukt.</span><span class="sxs-lookup"><span data-stu-id="e568e-233">Using the `[ref]` type-cast with a class member silently fails.</span></span> <span data-ttu-id="e568e-234">Api's die gebruikmaken `[ref]` van para meters kunnen niet worden gebruikt met klassen leden.</span><span class="sxs-lookup"><span data-stu-id="e568e-234">APIs that use `[ref]` parameters cannot be used with class members.</span></span> <span data-ttu-id="e568e-235">De **PSReference** is ontworpen voor de ondersteuning van COM-objecten.</span><span class="sxs-lookup"><span data-stu-id="e568e-235">The **PSReference** was designed to support COM objects.</span></span> <span data-ttu-id="e568e-236">COM-objecten bevatten gevallen waarin u een waarde in moet door geven.</span><span class="sxs-lookup"><span data-stu-id="e568e-236">COM objects have cases where you need to pass a value in by reference.</span></span>

<span data-ttu-id="e568e-237">`[ref]`Zie [PSReference-klasse](/dotnet/api/system.management.automation.psreference)voor meer informatie over het type.</span><span class="sxs-lookup"><span data-stu-id="e568e-237">For more information about the `[ref]` type, see [PSReference Class](/dotnet/api/system.management.automation.psreference).</span></span>

## <a name="see-also"></a><span data-ttu-id="e568e-238">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e568e-238">See also</span></span>

- [<span data-ttu-id="e568e-239">About_hidden</span><span class="sxs-lookup"><span data-stu-id="e568e-239">About_hidden</span></span>](About_hidden.md)
- [<span data-ttu-id="e568e-240">about_Enum</span><span class="sxs-lookup"><span data-stu-id="e568e-240">about_Enum</span></span>](about_Enum.md)
- [<span data-ttu-id="e568e-241">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="e568e-241">about_Language_Keywords</span></span>](about_language_keywords.md)
- [<span data-ttu-id="e568e-242">about_Methods</span><span class="sxs-lookup"><span data-stu-id="e568e-242">about_Methods</span></span>](about_methods.md)
- [<span data-ttu-id="e568e-243">about_Using</span><span class="sxs-lookup"><span data-stu-id="e568e-243">about_Using</span></span>](about_using.md)
