---
title: Alles wat u wilt weten over PSCustomObject
description: PSCustomObject is een eenvoudige manier om gestructureerde gegevens te maken.
ms.date: 07/29/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 52620fd628d03f62db574210a2a5758c3bf29135
ms.sourcegitcommit: a1886ba2cf35aebd650aafb3e5d7437c4e381781
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90804777"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a><span data-ttu-id="e24d2-103">Alles wat u wilt weten over PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="e24d2-103">Everything you wanted to know about PSCustomObject</span></span>

<span data-ttu-id="e24d2-104">`PSCustomObject`s zijn een uitstekend hulp programma om toe te voegen aan de band van uw Power shell-tool.</span><span class="sxs-lookup"><span data-stu-id="e24d2-104">`PSCustomObject`s are a great tool to add into your PowerShell tool belt.</span></span> <span data-ttu-id="e24d2-105">Laten we beginnen met de basis principes en werken op onze manier in de meer geavanceerde functies.</span><span class="sxs-lookup"><span data-stu-id="e24d2-105">Let's start with the basics and work our way into the more advanced features.</span></span> <span data-ttu-id="e24d2-106">Het idee van het gebruik van a `PSCustomObject` is een eenvoudige manier om gestructureerde gegevens te maken.</span><span class="sxs-lookup"><span data-stu-id="e24d2-106">The idea behind using a `PSCustomObject` is to have a simple way to create structured data.</span></span> <span data-ttu-id="e24d2-107">Bekijk het eerste voor beeld en u hebt een beter idee van wat dat betekent.</span><span class="sxs-lookup"><span data-stu-id="e24d2-107">Take a look at the first example and you'll have a better idea of what that means.</span></span>

> [!NOTE]
> <span data-ttu-id="e24d2-108">De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="e24d2-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="e24d2-109">Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="e24d2-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="e24d2-110">Raadpleeg zijn blog op [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="e24d2-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="creating-a-pscustomobject"></a><span data-ttu-id="e24d2-111">Een PSCustomObject maken</span><span class="sxs-lookup"><span data-stu-id="e24d2-111">Creating a PSCustomObject</span></span>

<span data-ttu-id="e24d2-112">Ik ben gek `[PSCustomObject]` op het gebruik van Power shell.</span><span class="sxs-lookup"><span data-stu-id="e24d2-112">I love using `[PSCustomObject]` in PowerShell.</span></span> <span data-ttu-id="e24d2-113">Het maken van een bruikbaar object is nog nooit zo eenvoudig geweest.</span><span class="sxs-lookup"><span data-stu-id="e24d2-113">Creating a usable object has never been easier.</span></span>
<span data-ttu-id="e24d2-114">Daarom ga ik over op alle andere manieren om een object te maken, maar ik moet vermelden dat de meeste van deze voor beelden Power shell v 3.0 en hoger zijn.</span><span class="sxs-lookup"><span data-stu-id="e24d2-114">Because of that, I'm going to skip over all the other ways you can create an object but I need to mention that most of these examples are PowerShell v3.0 and newer.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

<span data-ttu-id="e24d2-115">Deze methode werkt goed voor mij omdat ik hashtabellen gebruik voor vrijwel alles.</span><span class="sxs-lookup"><span data-stu-id="e24d2-115">This method works well for me because I use hashtables for just about everything.</span></span> <span data-ttu-id="e24d2-116">Er zijn echter momenten waarop Power shell hashtabellen meer lijkt te behandelen als een object.</span><span class="sxs-lookup"><span data-stu-id="e24d2-116">But there are times when I would like PowerShell to treat hashtables more like an object.</span></span> <span data-ttu-id="e24d2-117">De eerste plaats die u ziet, is het verschil wanneer u wilt gebruiken `Format-Table` of `Export-CSV` en u beseft dat een hashtabel alleen een verzameling sleutel-waardeparen is.</span><span class="sxs-lookup"><span data-stu-id="e24d2-117">The first place you notice the difference is when you want to use `Format-Table` or `Export-CSV` and you realize that a hashtable is just a collection of key/value pairs.</span></span>

<span data-ttu-id="e24d2-118">U kunt de waarden vervolgens openen en gebruiken, net zoals u een normaal object zou doen.</span><span class="sxs-lookup"><span data-stu-id="e24d2-118">You can then access and use the values like you would a normal object.</span></span>

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a><span data-ttu-id="e24d2-119">Een hashtabel converteren</span><span class="sxs-lookup"><span data-stu-id="e24d2-119">Converting a hashtable</span></span>

<span data-ttu-id="e24d2-120">Wist u dat u het onderwerp hebt, maar u hebt wel de volgende handelingen uitgevoerd:</span><span class="sxs-lookup"><span data-stu-id="e24d2-120">While I am on the topic, did you know you could do this:</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

<span data-ttu-id="e24d2-121">Ik wil het object nu vanuit het begin maken, maar er zijn tijden dat u eerst met een hashtabel moet werken.</span><span class="sxs-lookup"><span data-stu-id="e24d2-121">I do prefer to create the object from the start but there are times you have to work with a hashtable first.</span></span> <span data-ttu-id="e24d2-122">Dit voor beeld werkt omdat de constructor een hashtabel voor de object eigenschappen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e24d2-122">This example works because the constructor takes a hashtable for the object properties.</span></span> <span data-ttu-id="e24d2-123">Een belang rijke opmerking is dat hoewel deze methode werkt, het geen exacte equivalent is.</span><span class="sxs-lookup"><span data-stu-id="e24d2-123">One important note is that while this method works, it isn't an exact equivalent.</span></span> <span data-ttu-id="e24d2-124">Het grootste verschil is dat de volg orde van de eigenschappen niet wordt behouden.</span><span class="sxs-lookup"><span data-stu-id="e24d2-124">The biggest difference is that the order of the properties isn't preserved.</span></span>

### <a name="legacy-approach"></a><span data-ttu-id="e24d2-125">Verouderde aanpak</span><span class="sxs-lookup"><span data-stu-id="e24d2-125">Legacy approach</span></span>

<span data-ttu-id="e24d2-126">U hebt misschien gezien dat mensen `New-Object` aangepaste objecten kunnen maken.</span><span class="sxs-lookup"><span data-stu-id="e24d2-126">You may have seen people use `New-Object` to create custom objects.</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

<span data-ttu-id="e24d2-127">Op deze manier is het heel wat langzamer, maar dit is mogelijk de beste optie voor vroege versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="e24d2-127">This way is quite a bit slower but it may be your best option on early versions of PowerShell.</span></span>

### <a name="saving-to-a-file"></a><span data-ttu-id="e24d2-128">Opslaan naar een bestand</span><span class="sxs-lookup"><span data-stu-id="e24d2-128">Saving to a file</span></span>

<span data-ttu-id="e24d2-129">Ik vind de beste manier om een hashtabel op te slaan in een bestand om het op te slaan als JSON.</span><span class="sxs-lookup"><span data-stu-id="e24d2-129">I find the best way to save a hashtable to a file is to save it as JSON.</span></span> <span data-ttu-id="e24d2-130">U kunt deze weer importeren in een `[PSCustomObject]`</span><span class="sxs-lookup"><span data-stu-id="e24d2-130">You can import it back into a `[PSCustomObject]`</span></span>

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

<span data-ttu-id="e24d2-131">Ik vind meer manieren voor het opslaan van objecten in een bestand in mijn artikel op [de vele manieren om bestanden te lezen en te schrijven][].</span><span class="sxs-lookup"><span data-stu-id="e24d2-131">I cover more ways to save objects to a file in my article on [The many ways to read and write to files][].</span></span>

## <a name="working-with-properties"></a><span data-ttu-id="e24d2-132">Werken met eigenschappen</span><span class="sxs-lookup"><span data-stu-id="e24d2-132">Working with properties</span></span>

### <a name="adding-properties"></a><span data-ttu-id="e24d2-133">Eigenschappen toevoegen</span><span class="sxs-lookup"><span data-stu-id="e24d2-133">Adding properties</span></span>

<span data-ttu-id="e24d2-134">U kunt nog steeds nieuwe eigenschappen toevoegen aan uw `PSCustomObject` met `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="e24d2-134">You can still add new properties to your `PSCustomObject` with `Add-Member`.</span></span>

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a><span data-ttu-id="e24d2-135">Eigenschappen verwijderen</span><span class="sxs-lookup"><span data-stu-id="e24d2-135">Remove properties</span></span>

<span data-ttu-id="e24d2-136">U kunt de eigenschappen van een object ook verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e24d2-136">You can also remove properties off of an object.</span></span>

```powershell
$myObject.psobject.properties.remove('ID')
```

<span data-ttu-id="e24d2-137">De `psobject` is een verborgen eigenschap waarmee u toegang krijgt tot de meta gegevens van het basis object.</span><span class="sxs-lookup"><span data-stu-id="e24d2-137">The `psobject` is a hidden property that gives you access to base object metadata.</span></span>

### <a name="enumerating-property-names"></a><span data-ttu-id="e24d2-138">Eigenschaps namen opsommen</span><span class="sxs-lookup"><span data-stu-id="e24d2-138">Enumerating property names</span></span>

<span data-ttu-id="e24d2-139">Soms hebt u een lijst nodig van alle eigenschapnamen van een object.</span><span class="sxs-lookup"><span data-stu-id="e24d2-139">Sometimes you need a list of all the property names on an object.</span></span>

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

<span data-ttu-id="e24d2-140">Deze lijst kan ook worden opgehaald van de `psobject` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="e24d2-140">We can get this same list off of the `psobject` property too.</span></span>

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a><span data-ttu-id="e24d2-141">Eigenschappen dynamisch gebruiken</span><span class="sxs-lookup"><span data-stu-id="e24d2-141">Dynamically accessing properties</span></span>

<span data-ttu-id="e24d2-142">Ik heb al aangegeven dat u rechtstreeks toegang hebt tot eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="e24d2-142">I already mentioned that you can access property values directly.</span></span>

```powershell
$myObject.Name
```

<span data-ttu-id="e24d2-143">U kunt een teken reeks gebruiken voor de naam van de eigenschap. deze blijft echter wel werken.</span><span class="sxs-lookup"><span data-stu-id="e24d2-143">You can use a string for the property name and it will still work.</span></span>

```powershell
$myObject.'Name'
```

<span data-ttu-id="e24d2-144">We kunnen een extra stap uitvoeren en een variabele voor de naam van de eigenschap gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e24d2-144">We can take this one more step and use a variable for the property name.</span></span>

```powershell
$property = 'Name'
$myObject.$property
```

<span data-ttu-id="e24d2-145">Ik weet dat dat vreemd lijkt, maar het werkt.</span><span class="sxs-lookup"><span data-stu-id="e24d2-145">I know that looks strange, but it works.</span></span>

### <a name="convert-pscustomobject-into-a-hashtable"></a><span data-ttu-id="e24d2-146">PSCustomObject naar een hashtabel converteren</span><span class="sxs-lookup"><span data-stu-id="e24d2-146">Convert PSCustomObject into a hashtable</span></span>

<span data-ttu-id="e24d2-147">Als u wilt door gaan met de laatste sectie, kunt u de eigenschappen dynamisch door lopen en een hashtabel maken.</span><span class="sxs-lookup"><span data-stu-id="e24d2-147">To continue on from the last section, you can dynamically walk the properties and create a hashtable from them.</span></span>

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a><span data-ttu-id="e24d2-148">Testen op Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="e24d2-148">Testing for properties</span></span>

<span data-ttu-id="e24d2-149">Als u wilt weten of een eigenschap bestaat, kunt u gewoon controleren of de eigenschap een waarde heeft.</span><span class="sxs-lookup"><span data-stu-id="e24d2-149">If you need to know if a property exists, you could just check for that property to have a value.</span></span>

```powershell
if( $null -ne $myObject.ID )
```

<span data-ttu-id="e24d2-150">Maar als de waarde zou kunnen zijn `$null` en u deze nog steeds moet controleren, kunt u de `psobject.properties` voor IT controleren.</span><span class="sxs-lookup"><span data-stu-id="e24d2-150">But if the value could be `$null` and you still need to check for it, you can check the `psobject.properties` for it.</span></span>

```powershell
if( $myobject.psobject.properties.match('ID') )
```

## <a name="adding-object-methods"></a><span data-ttu-id="e24d2-151">Object methoden toevoegen</span><span class="sxs-lookup"><span data-stu-id="e24d2-151">Adding object methods</span></span>

<span data-ttu-id="e24d2-152">Als u een script methode moet toevoegen aan een object, kunt u dit doen met `Add-Member` en een `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="e24d2-152">If you need to add a script method to an object, you can do it with `Add-Member` and a `ScriptBlock`.</span></span> <span data-ttu-id="e24d2-153">U moet de `this` automatische variabelen referentie het huidige object gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e24d2-153">You have to use the `this` automatic variable reference the current object.</span></span> <span data-ttu-id="e24d2-154">Hier is een `scriptblock` om een object in een hashtabel in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="e24d2-154">Here is a `scriptblock` to turn an object into a hashtable.</span></span> <span data-ttu-id="e24d2-155">(dezelfde code vormen het laatste voor beeld)</span><span class="sxs-lookup"><span data-stu-id="e24d2-155">(same code form the last example)</span></span>

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

<span data-ttu-id="e24d2-156">Vervolgens voegen we het toe aan ons object als een script eigenschap.</span><span class="sxs-lookup"><span data-stu-id="e24d2-156">Then we add it to our object as a script property.</span></span>

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

<span data-ttu-id="e24d2-157">Vervolgens kunnen we onze functie als volgt aanroepen:</span><span class="sxs-lookup"><span data-stu-id="e24d2-157">Then we can call our function like this:</span></span>

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a><span data-ttu-id="e24d2-158">Objecten versus waardetypen</span><span class="sxs-lookup"><span data-stu-id="e24d2-158">Objects vs Value types</span></span>

<span data-ttu-id="e24d2-159">Met objecten en waardetypen worden variabelen toewijzingen niet op dezelfde manier afgehandeld.</span><span class="sxs-lookup"><span data-stu-id="e24d2-159">Objects and value types don't handle variable assignments the same way.</span></span> <span data-ttu-id="e24d2-160">Als u waardetypen aan elkaar toewijst, wordt alleen de waarde opgehaald die wordt gekopieerd naar de nieuwe variabele.</span><span class="sxs-lookup"><span data-stu-id="e24d2-160">If you assign value types to each other, only the value get copied to the new variable.</span></span>

```powershell
$first = 1
$second = $first
$second = 2
```

<span data-ttu-id="e24d2-161">In dit geval `$first` is 1 en `$second` 2.</span><span class="sxs-lookup"><span data-stu-id="e24d2-161">In this case, `$first` is 1 and `$second` is 2.</span></span>

<span data-ttu-id="e24d2-162">Object variabelen bevatten een verwijzing naar het daad werkelijke object.</span><span class="sxs-lookup"><span data-stu-id="e24d2-162">Object variables hold a reference to the actual object.</span></span> <span data-ttu-id="e24d2-163">Wanneer u één object toewijst aan een nieuwe variabele, verwijzen ze nog steeds naar hetzelfde object.</span><span class="sxs-lookup"><span data-stu-id="e24d2-163">When you assign one object to a new variable, they still reference the same object.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

<span data-ttu-id="e24d2-164">Omdat `$third` en `$fourth` naar hetzelfde exemplaar van een object verwijst, `$third.key` zijn beide en `$fourth.Key` 4.</span><span class="sxs-lookup"><span data-stu-id="e24d2-164">Because `$third` and `$fourth` reference the same instance of an object, both `$third.key` and `$fourth.Key` are 4.</span></span>

### <a name="psobjectcopy"></a><span data-ttu-id="e24d2-165">psobject. Copy ()</span><span class="sxs-lookup"><span data-stu-id="e24d2-165">psobject.copy()</span></span>

<span data-ttu-id="e24d2-166">Als u een echt exemplaar van een object nodig hebt, kunt u dit klonen.</span><span class="sxs-lookup"><span data-stu-id="e24d2-166">If you need a true copy of an object, you can clone it.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

<span data-ttu-id="e24d2-167">Met de kloon maakt u een bestaand exemplaar van het object.</span><span class="sxs-lookup"><span data-stu-id="e24d2-167">Clone creates a shallow copy of the object.</span></span> <span data-ttu-id="e24d2-168">Ze hebben nu verschillende exemplaren en zijn `$third.key` 3 en `$fourth.Key` 4 in dit voor beeld.</span><span class="sxs-lookup"><span data-stu-id="e24d2-168">They have different instances now and `$third.key` is 3 and `$fourth.Key` is 4 in this example.</span></span>

<span data-ttu-id="e24d2-169">Ik roep dit een inkomend exemplaar aan omdat als u geneste objecten hebt.</span><span class="sxs-lookup"><span data-stu-id="e24d2-169">I call this a shallow copy because if you have nested objects.</span></span> <span data-ttu-id="e24d2-170">(waarbij de eigenschappen andere objecten bevatten).</span><span class="sxs-lookup"><span data-stu-id="e24d2-170">(where the properties contain other objects).</span></span> <span data-ttu-id="e24d2-171">Alleen de waarden op het hoogste niveau worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="e24d2-171">Only the top-level values are copied.</span></span> <span data-ttu-id="e24d2-172">De onderliggende objecten verwijzen naar elkaar.</span><span class="sxs-lookup"><span data-stu-id="e24d2-172">The child objects will reference each other.</span></span>

### <a name="pstypename-for-custom-object-types"></a><span data-ttu-id="e24d2-173">PSTypeName voor aangepaste object typen</span><span class="sxs-lookup"><span data-stu-id="e24d2-173">PSTypeName for custom object types</span></span>

<span data-ttu-id="e24d2-174">Nu we een object hebben, zijn er nog enkele dingen die u kunt doen. Dit kan bijna niet zo duidelijk zijn.</span><span class="sxs-lookup"><span data-stu-id="e24d2-174">Now that we have an object, there are a few more things we can do with it that may not be nearly as obvious.</span></span> <span data-ttu-id="e24d2-175">Het eerste wat u moet doen, is een `PSTypeName` .</span><span class="sxs-lookup"><span data-stu-id="e24d2-175">First thing we need to do is give it a `PSTypeName`.</span></span> <span data-ttu-id="e24d2-176">Dit is de meest voorkomende manier waarop ik mensen kan zien:</span><span class="sxs-lookup"><span data-stu-id="e24d2-176">This is the most common way I see people do it:</span></span>

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

<span data-ttu-id="e24d2-177">Ik heb onlangs een andere manier ontdekt om dit te doen vanuit dit [bericht door/u/markekraus][].</span><span class="sxs-lookup"><span data-stu-id="e24d2-177">I recently discovered another way to do this from this [post by /u/markekraus][].</span></span> <span data-ttu-id="e24d2-178">Ik heb een beetje Blijf spitten en meer posts over het idee van [Adam Bertram][] en [Mike Shepard][] , waar ze over deze aanpak praten, zodat u deze inline kunt definiëren.</span><span class="sxs-lookup"><span data-stu-id="e24d2-178">I did a little digging and more posts about the idea from [Adam Bertram][] and [Mike Shepard][] where they talk about this approach that allows you to define it inline.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

<span data-ttu-id="e24d2-179">Ik ben geweldig hoe mooi dit precies in de taal past.</span><span class="sxs-lookup"><span data-stu-id="e24d2-179">I love how nicely this just fits into the language.</span></span> <span data-ttu-id="e24d2-180">Nu we een object met de juiste type naam hebben, kunnen we meer dingen doen.</span><span class="sxs-lookup"><span data-stu-id="e24d2-180">Now that we have an object with a proper type name, we can do some more things.</span></span>

> [!NOTE]
> <span data-ttu-id="e24d2-181">U kunt ook aangepaste Power shell-typen maken met behulp van Power shell-klassen.</span><span class="sxs-lookup"><span data-stu-id="e24d2-181">You can also create custom PowerShell types using PowerShell classes.</span></span> <span data-ttu-id="e24d2-182">Zie [overzicht van Power shell-klassen](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e24d2-182">For more information, see [PowerShell Class Overview](/powershell/module/Microsoft.PowerShell.Core/About/about_Classes).</span></span>

## <a name="using-defaultpropertyset-the-long-way"></a><span data-ttu-id="e24d2-183">DefaultPropertySet gebruiken (de lange manier)</span><span class="sxs-lookup"><span data-stu-id="e24d2-183">Using DefaultPropertySet (the long way)</span></span>

<span data-ttu-id="e24d2-184">Power Shell heeft voor ons besloten welke eigenschappen standaard moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e24d2-184">PowerShell decides for us what properties to display by default.</span></span> <span data-ttu-id="e24d2-185">Veel van de systeem eigen opdrachten hebben een `.ps1xml` [Opmaak bestand][] dat het hoge aantal opheffen.</span><span class="sxs-lookup"><span data-stu-id="e24d2-185">A lot of the native commands have a `.ps1xml` [formatting file][] that does all the heavy lifting.</span></span> <span data-ttu-id="e24d2-186">Vanuit dit [bericht van BOE-proxy][]is het een andere manier om dit te doen voor ons aangepaste object met behulp van alleen Power shell.</span><span class="sxs-lookup"><span data-stu-id="e24d2-186">From this [post by Boe Prox][], there's another way for us to do this on our custom object using just PowerShell.</span></span> <span data-ttu-id="e24d2-187">We kunnen het een voor stel geven `MemberSet` om het te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e24d2-187">We can give it a `MemberSet` for it to use.</span></span>

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet(‘DefaultDisplayPropertySet’,[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

<span data-ttu-id="e24d2-188">Nu wanneer mijn object net in de shell is ingedeeld, worden deze eigenschappen standaard alleen weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e24d2-188">Now when my object just falls to the shell, it will only show those properties by default.</span></span>

### <a name="update-typedata-with-defaultpropertyset"></a><span data-ttu-id="e24d2-189">Update-TypeData met DefaultPropertySet</span><span class="sxs-lookup"><span data-stu-id="e24d2-189">Update-TypeData with DefaultPropertySet</span></span>

<span data-ttu-id="e24d2-190">Dit is leuk, maar ik heb onlangs een betere manier gezien wanneer [Power shell is ontkoppeld 2016 met Jeffrey Snover & Daan Jansen][psunplugged].</span><span class="sxs-lookup"><span data-stu-id="e24d2-190">This is nice but I recently saw a better way when watching [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged].</span></span> <span data-ttu-id="e24d2-191">Jeffrey heeft [Update-TypeData][] gebruikt om de standaard eigenschappen op te geven.</span><span class="sxs-lookup"><span data-stu-id="e24d2-191">Jeffrey was using [Update-TypeData][] to specify the default properties.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

<span data-ttu-id="e24d2-192">Dat is zo eenvoudig dat ik dit niet kan onthouden als ik dit bericht niet had als snelle verwijzing.</span><span class="sxs-lookup"><span data-stu-id="e24d2-192">That is simple enough that I could almost remember it if I didn't have this post as a quick reference.</span></span> <span data-ttu-id="e24d2-193">Ik kan nu eenvoudig objecten met veel eigenschappen maken en deze toch een fraaie, overzichtelijke weer gave geven bij het bekijken van de shell.</span><span class="sxs-lookup"><span data-stu-id="e24d2-193">Now I can easily create objects with lots of properties and still give it a nice clean view when looking at it from the shell.</span></span> <span data-ttu-id="e24d2-194">Als ik de andere eigenschappen moet openen of bekijken, zijn ze nog steeds beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="e24d2-194">If I need to access or see those other properties, they're still there.</span></span>

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a><span data-ttu-id="e24d2-195">Update-TypeData met ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="e24d2-195">Update-TypeData with ScriptProperty</span></span>

<span data-ttu-id="e24d2-196">Iets anders heb ik van deze video bezig met het maken van script eigenschappen voor objecten.</span><span class="sxs-lookup"><span data-stu-id="e24d2-196">Something else I got out of that video was creating script properties for your objects.</span></span> <span data-ttu-id="e24d2-197">Dit is een goed moment om te wijzen dat dit ook voor bestaande objecten werkt.</span><span class="sxs-lookup"><span data-stu-id="e24d2-197">This would be a good time to point out that this works for existing objects too.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

<span data-ttu-id="e24d2-198">U kunt dit doen voordat het object wordt gemaakt of wanneer het nog steeds wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e24d2-198">You can do this before your object is created or after and it will still work.</span></span> <span data-ttu-id="e24d2-199">Zo maakt u dit anders met `Add-Member` een script eigenschap.</span><span class="sxs-lookup"><span data-stu-id="e24d2-199">This is what makes this different then using `Add-Member` with a script property.</span></span> <span data-ttu-id="e24d2-200">Wanneer u `Add-Member` de verwijzing eerder gebruikt, bestaat deze alleen op die specifieke instantie van het object.</span><span class="sxs-lookup"><span data-stu-id="e24d2-200">When you use `Add-Member` the way I referenced earlier, it only exists on that specific instance of the object.</span></span> <span data-ttu-id="e24d2-201">Dit geldt voor alle objecten met deze naam `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="e24d2-201">This one applies to all objects with this `TypeName`.</span></span>

## <a name="function-parameters"></a><span data-ttu-id="e24d2-202">Functie parameters</span><span class="sxs-lookup"><span data-stu-id="e24d2-202">Function parameters</span></span>

<span data-ttu-id="e24d2-203">U kunt deze aangepaste typen nu gebruiken voor para meters in uw functies en scripts.</span><span class="sxs-lookup"><span data-stu-id="e24d2-203">You can now use these custom types for parameters in your functions and scripts.</span></span> <span data-ttu-id="e24d2-204">U kunt deze aangepaste objecten met één functie maken en vervolgens door geven aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="e24d2-204">You can have one function create these custom objects and then pass them into other functions.</span></span>

```powershell
param( [PSTypeName('My.Object')]$Data )
```

<span data-ttu-id="e24d2-205">Voor Power shell is vereist dat het object het type is dat u hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="e24d2-205">PowerShell requires that the object is the type you specified.</span></span> <span data-ttu-id="e24d2-206">Er wordt een validatie fout gegenereerd als het type niet automatisch overeenkomt met het opslaan van de stap van de test in uw code.</span><span class="sxs-lookup"><span data-stu-id="e24d2-206">It throws a validation error if the type doesn't match automatically to save you the step of testing for it in your code.</span></span> <span data-ttu-id="e24d2-207">Een goed voor beeld van Power shell om te laten zien wat het beste werkt.</span><span class="sxs-lookup"><span data-stu-id="e24d2-207">A great example of letting PowerShell do what it does best.</span></span>

### <a name="function-outputtype"></a><span data-ttu-id="e24d2-208">Functie output type</span><span class="sxs-lookup"><span data-stu-id="e24d2-208">Function OutputType</span></span>

<span data-ttu-id="e24d2-209">U kunt ook een `OutputType` voor uw geavanceerde functies definiëren.</span><span class="sxs-lookup"><span data-stu-id="e24d2-209">You can also define an `OutputType` for your advanced functions.</span></span>

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

<span data-ttu-id="e24d2-210">De waarde van het kenmerk **output** type is alleen een documentatie opmerking.</span><span class="sxs-lookup"><span data-stu-id="e24d2-210">The **OutputType** attribute value is only a documentation note.</span></span> <span data-ttu-id="e24d2-211">Het is niet afgeleid van de functie code of vergeleken met de daad werkelijke functie-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="e24d2-211">It isn't derived from the function code or compared to the actual function output.</span></span>

<span data-ttu-id="e24d2-212">De belangrijkste reden voor het gebruik van een uitvoer type is dat meta gegevens over uw functie uw bedoelingen kunnen weer spie gelen.</span><span class="sxs-lookup"><span data-stu-id="e24d2-212">The main reason you would use an output type is so that meta information about your function reflects your intentions.</span></span> <span data-ttu-id="e24d2-213">Wat `Get-Command` `Get-Help` u kunt doen met uw ontwikkel omgeving.</span><span class="sxs-lookup"><span data-stu-id="e24d2-213">Things like `Get-Command` and `Get-Help` that your development environment can take advantage of.</span></span> <span data-ttu-id="e24d2-214">Als u meer informatie wilt, raadpleegt u de Help voor IT: [about_Functions_OutputTypeAttribute][].</span><span class="sxs-lookup"><span data-stu-id="e24d2-214">If you want more information, then take a look at the help for it: [about_Functions_OutputTypeAttribute][].</span></span>

<span data-ttu-id="e24d2-215">Als u een functie voor het testen van uw functies gebruikt, is het een goed idee om de uitvoer objecten te valideren die overeenkomen met uw **output**type.</span><span class="sxs-lookup"><span data-stu-id="e24d2-215">With that said, if you're using Pester to unit test your functions then it would be a good idea to validate the output objects match your **OutputType**.</span></span> <span data-ttu-id="e24d2-216">Dit kan ertoe leiden dat variabelen die net tot de pipe vallen, worden onderschept wanneer dat niet het geval is.</span><span class="sxs-lookup"><span data-stu-id="e24d2-216">This could catch variables that just fall to the pipe when they shouldn't.</span></span>

## <a name="closing-thoughts"></a><span data-ttu-id="e24d2-217">Afsluitende ideeën</span><span class="sxs-lookup"><span data-stu-id="e24d2-217">Closing thoughts</span></span>

<span data-ttu-id="e24d2-218">De context van dit was alles `[PSCustomObject]` , maar een groot aantal van deze informatie is van toepassing op objecten in het algemeen.</span><span class="sxs-lookup"><span data-stu-id="e24d2-218">The context of this was all about `[PSCustomObject]`, but a lot of this information applies to objects in general.</span></span>

<span data-ttu-id="e24d2-219">Ik heb de meeste van deze functies in de door gave gezien, maar u hebt deze nooit gezien als een verzameling gegevens over `PSCustomObject` .</span><span class="sxs-lookup"><span data-stu-id="e24d2-219">I have seen most of these features in passing before but never saw them presented as a collection of information on `PSCustomObject`.</span></span> <span data-ttu-id="e24d2-220">Alleen deze afgelopen week heb ik stumbled bij een ander abonnement en was het verbaasd dat ik het nog niet had gezien.</span><span class="sxs-lookup"><span data-stu-id="e24d2-220">Just this last week I stumbled upon another one and was surprised that I had not seen it before.</span></span> <span data-ttu-id="e24d2-221">Ik wilde al deze ideeën samen stellen, zodat u de foto groter kunt zien en weet wanneer u de mogelijkheid hebt om ze te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e24d2-221">I wanted to pull all these ideas together so you can hopefully see the bigger picture and be aware of them when you have an opportunity to use them.</span></span> <span data-ttu-id="e24d2-222">Ik hoop dat u iets hebt geleerd en een manier kunt vinden om dit in uw scripts te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e24d2-222">I hope you learned something and can find a way to work this into your scripts.</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[original version]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[post by BOE-proxy]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[post by Boe Prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[Opmaak bestand]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[formatting file]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[De vele manieren om bestanden te lezen en te schrijven]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[The many ways to read and write to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[post by/u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[post by /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam-Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
