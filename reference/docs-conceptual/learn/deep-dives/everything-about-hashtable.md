---
title: Alles wat u wilt weten over hashtabellen
description: Hashtabellen zijn heel belang rijk in Power shell, zodat het goed is om een duidelijker beeld te krijgen.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: a471c0fe2c48820d6c1d152e2850b1e431d28f23
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101686063"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a><span data-ttu-id="aae8b-103">Alles wat u wilt weten over hashtabellen</span><span class="sxs-lookup"><span data-stu-id="aae8b-103">Everything you wanted to know about hashtables</span></span>

<span data-ttu-id="aae8b-104">Ik wil een stap terugnemen en praten over [hashtabellen][].</span><span class="sxs-lookup"><span data-stu-id="aae8b-104">I want to take a step back and talk about [hashtables][].</span></span> <span data-ttu-id="aae8b-105">Ik gebruik deze nu altijd.</span><span class="sxs-lookup"><span data-stu-id="aae8b-105">I use them all the time now.</span></span> <span data-ttu-id="aae8b-106">Ik ben van de afgelopen avond een studie over de gebruikers groep, en ik heb een andere uitverwar ring gehad over hen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-106">I was teaching someone about them after our user group meeting last night and I realized I had the same confusion about them as he had.</span></span> <span data-ttu-id="aae8b-107">Hashtabellen zijn heel belang rijk in Power shell, zodat het goed is om een duidelijker beeld te krijgen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-107">Hashtables are really important in PowerShell so it's good to have a solid understanding of them.</span></span>

> [!NOTE]
> <span data-ttu-id="aae8b-108">De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="aae8b-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="aae8b-109">Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="aae8b-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="aae8b-110">Raadpleeg zijn blog op [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="aae8b-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="hashtable-as-a-collection-of-things"></a><span data-ttu-id="aae8b-111">Hashtabel als een verzameling dingen</span><span class="sxs-lookup"><span data-stu-id="aae8b-111">Hashtable as a collection of things</span></span>

<span data-ttu-id="aae8b-112">Ik wil dat u eerst een **hashtabel** als een verzameling in de traditionele definitie van een hashtabel ziet.</span><span class="sxs-lookup"><span data-stu-id="aae8b-112">I want you to first see a **Hashtable** as a collection in the traditional definition of a hashtable.</span></span> <span data-ttu-id="aae8b-113">Deze definitie biedt u een basis kennis van hoe ze werken wanneer ze later worden gebruikt voor meer geavanceerde dingen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-113">This definition gives you a fundamental understanding of how they work when they get used for more advanced stuff later.</span></span> <span data-ttu-id="aae8b-114">Het overs laan van deze inzichten is vaak een bron van Verwar ring.</span><span class="sxs-lookup"><span data-stu-id="aae8b-114">Skipping this understanding is often a source of confusion.</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="aae8b-115">Wat is een matrix?</span><span class="sxs-lookup"><span data-stu-id="aae8b-115">What is an array?</span></span>

<span data-ttu-id="aae8b-116">Voordat ik naar wat een **hashtabel** gaat, moet ik eerst de [matrixen][] vermelden.</span><span class="sxs-lookup"><span data-stu-id="aae8b-116">Before I jump into what a **Hashtable** is, I need to mention [arrays][] first.</span></span> <span data-ttu-id="aae8b-117">Voor het doel van deze discussie is een matrix een lijst of verzameling waarden of objecten.</span><span class="sxs-lookup"><span data-stu-id="aae8b-117">For the purpose of this discussion, an array is a list or collection of values or objects.</span></span>

```powershell
$array = @(1,2,3,5,7,11)
```

<span data-ttu-id="aae8b-118">Zodra u uw items in een matrix hebt, kunt u gebruiken `foreach` om de lijst te herhalen of een index te gebruiken voor toegang tot afzonderlijke elementen in de matrix.</span><span class="sxs-lookup"><span data-stu-id="aae8b-118">Once you have your items into an array, you can either use `foreach` to iterate over the list or use an index to access individual elements in the array.</span></span>

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

<span data-ttu-id="aae8b-119">Op dezelfde manier kunt u ook waarden bijwerken met behulp van een index.</span><span class="sxs-lookup"><span data-stu-id="aae8b-119">You can also update values using an index in the same way.</span></span>

```powershell
$array[2] = 13
```

<span data-ttu-id="aae8b-120">Ik heb gewoon het Opper vlak op matrices kwijt, maar dat zou ze in de juiste context moeten zetten terwijl ik op hashtabellen ga.</span><span class="sxs-lookup"><span data-stu-id="aae8b-120">I just scratched the surface on arrays but that should put them into the right context as I move onto hashtables.</span></span>

## <a name="what-is-a-hashtable"></a><span data-ttu-id="aae8b-121">Wat is een hashtabel?</span><span class="sxs-lookup"><span data-stu-id="aae8b-121">What is a hashtable?</span></span>

<span data-ttu-id="aae8b-122">Ik ga aan de slag met een eenvoudige technische beschrijving van wat hashtabellen in het algemeen zinvol zijn, voordat ik de andere manieren in Power shell gebruik.</span><span class="sxs-lookup"><span data-stu-id="aae8b-122">I'm going to start with a basic technical description of what hashtables are, in the general sense, before I shift into the other ways PowerShell uses them.</span></span>

<span data-ttu-id="aae8b-123">Een hashtabel is een gegevens structuur die vergelijkbaar is met een matrix, behalve dat u elke waarde (object) opslaat met behulp van een sleutel.</span><span class="sxs-lookup"><span data-stu-id="aae8b-123">A hashtable is a data structure, much like an array, except you store each value (object) using a key.</span></span> <span data-ttu-id="aae8b-124">Het is een basis sleutel/waarde-archief.</span><span class="sxs-lookup"><span data-stu-id="aae8b-124">It's a basic key/value store.</span></span> <span data-ttu-id="aae8b-125">Eerst maken we een lege hashtabel.</span><span class="sxs-lookup"><span data-stu-id="aae8b-125">First, we create an empty hashtable.</span></span>

```powershell
$ageList = @{}
```

<span data-ttu-id="aae8b-126">U ziet dat accolades in plaats van haakjes worden gebruikt voor het definiëren van een hashtabel.</span><span class="sxs-lookup"><span data-stu-id="aae8b-126">Notice that braces, instead of parentheses, are used to define a hashtable.</span></span> <span data-ttu-id="aae8b-127">Vervolgens voegen we een item toe met behulp van een sleutel als volgt:</span><span class="sxs-lookup"><span data-stu-id="aae8b-127">Then we add an item using a key like this:</span></span>

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

<span data-ttu-id="aae8b-128">De naam van de persoon is de sleutel en de leeftijd is de waarde die ik wil opslaan.</span><span class="sxs-lookup"><span data-stu-id="aae8b-128">The person's name is the key and their age is the value that I want to save.</span></span>

## <a name="using-the-brackets-for-access"></a><span data-ttu-id="aae8b-129">De vier Kante haken gebruiken voor toegang</span><span class="sxs-lookup"><span data-stu-id="aae8b-129">Using the brackets for access</span></span>

<span data-ttu-id="aae8b-130">Zodra u uw waarden aan de hashtabel hebt toegevoegd, kunt u ze weer gebruiken met dezelfde sleutel (in plaats van een numerieke index zoals u voor een matrix zou gebruiken).</span><span class="sxs-lookup"><span data-stu-id="aae8b-130">Once you add your values to the hashtable, you can pull them back out using that same key (instead of using a numeric index like you would have for an array).</span></span>

```powershell
$ageList['Kevin']
$ageList['Alex']
```

<span data-ttu-id="aae8b-131">Wanneer ik de leeftijd van Kevin wil, gebruik ik dan de naam ervan om deze te openen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-131">When I want Kevin's age, I use his name to access it.</span></span> <span data-ttu-id="aae8b-132">U kunt deze methode gebruiken om ook waarden toe te voegen of bij te werken in de hashtabel.</span><span class="sxs-lookup"><span data-stu-id="aae8b-132">We can use this approach to add or update values into the hashtable too.</span></span> <span data-ttu-id="aae8b-133">Dit is net als het gebruik van de `add()` bovenstaande functie.</span><span class="sxs-lookup"><span data-stu-id="aae8b-133">This is just like using the `add()` function above.</span></span>

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

<span data-ttu-id="aae8b-134">Er is een andere syntaxis die u kunt gebruiken voor toegang tot en het bijwerken van waarden die ik in een latere sectie bevindt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-134">There's another syntax you can use for accessing and updating values that I'll cover in a later section.</span></span> <span data-ttu-id="aae8b-135">Als u vanuit een andere taal naar Power shell gaat, moeten deze voor beelden passen in met de manier waarop u hashtabellen al eerder hebt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-135">If you're coming to PowerShell from another language, these examples should fit in with how you may have used hashtables before.</span></span>

### <a name="creating-hashtables-with-values"></a><span data-ttu-id="aae8b-136">Hashtabellen maken met waarden</span><span class="sxs-lookup"><span data-stu-id="aae8b-136">Creating hashtables with values</span></span>

<span data-ttu-id="aae8b-137">Tot nu toe heb ik een lege hashtabel gemaakt voor deze voor beelden.</span><span class="sxs-lookup"><span data-stu-id="aae8b-137">So far I've created an empty hashtable for these examples.</span></span> <span data-ttu-id="aae8b-138">U kunt de sleutels en waarden vooraf invullen wanneer u ze maakt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-138">You can pre-populate the keys and values when you create them.</span></span>

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a><span data-ttu-id="aae8b-139">Als opzoek tabel</span><span class="sxs-lookup"><span data-stu-id="aae8b-139">As a lookup table</span></span>

<span data-ttu-id="aae8b-140">De werkelijke waarde van dit type van een hashtabel is dat u ze als opzoek tabel kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-140">The real value of this type of a hashtable is that you can use them as a lookup table.</span></span> <span data-ttu-id="aae8b-141">Hier volgt een eenvoudig voor beeld.</span><span class="sxs-lookup"><span data-stu-id="aae8b-141">Here is a simple example.</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

<span data-ttu-id="aae8b-142">In dit voor beeld geeft u een omgeving voor de `$env` variabele op en wordt de juiste server gekozen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-142">In this example, you specify an environment for the `$env` variable and it will pick the correct server.</span></span> <span data-ttu-id="aae8b-143">U kunt een `switch($env){...}` voor een selectie zoals deze gebruiken, maar een hashtabel is een mooie optie.</span><span class="sxs-lookup"><span data-stu-id="aae8b-143">You could use a `switch($env){...}` for a selection like this but a hashtable is a nice option.</span></span>

<span data-ttu-id="aae8b-144">Dit wordt nog beter wanneer u de opzoek tabel dynamisch bouwt om deze later te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-144">This gets even better when you dynamically build the lookup table to use it later.</span></span> <span data-ttu-id="aae8b-145">Denk dus na over het gebruik van deze aanpak wanneer u naar iets moet verwijzen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-145">So think about using this approach when you need to cross reference something.</span></span> <span data-ttu-id="aae8b-146">Ik denk dat dit zelfs meer zou worden weer gegeven als Power shell niet zo goed kan worden gefilterd op de pipe met `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="aae8b-146">I think we would see this even more if PowerShell wasn't so good at filtering on the pipe with `Where-Object`.</span></span> <span data-ttu-id="aae8b-147">Als u ooit een situatie hebt waarbij de prestaties van belang zijn, moet u rekening houden met deze aanpak.</span><span class="sxs-lookup"><span data-stu-id="aae8b-147">If you're ever in a situation where performance matters, this approach needs to be considered.</span></span>

<span data-ttu-id="aae8b-148">Ik zeg niet dat het sneller is, maar wel in het geval van [prestatie][]problemen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-148">I won't say that it's faster, but it does fit into the rule of [If performance matters, test it][].</span></span>

#### <a name="multiselection"></a><span data-ttu-id="aae8b-149">Multiselectie</span><span class="sxs-lookup"><span data-stu-id="aae8b-149">Multiselection</span></span>

<span data-ttu-id="aae8b-150">Over het algemeen kunt u een hashtabel beschouwen als een sleutel/waarde-paar, waarbij u één sleutel opgeeft en één waarde ophaalt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-150">Generally, you think of a hashtable as a key/value pair, where you provide one key and get one value.</span></span> <span data-ttu-id="aae8b-151">Met Power shell kunt u een matrix met sleutels opgeven om meerdere waarden te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-151">PowerShell allows you to provide an array of keys to get multiple values.</span></span>

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

<span data-ttu-id="aae8b-152">In dit voor beeld gebruiken we dezelfde overeenkomende hashtabel en bieden ze drie verschillende matrix stijlen om de overeenkomsten op te halen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-152">In this example, I use the same lookup hashtable from above and provide three different array styles to get the matches.</span></span> <span data-ttu-id="aae8b-153">Dit is een verborgen edelsteen in Power shell waarmee de meeste mensen niet op de hoogte zijn.</span><span class="sxs-lookup"><span data-stu-id="aae8b-153">This is a hidden gem in PowerShell that most people aren't aware of.</span></span>

## <a name="iterating-hashtables"></a><span data-ttu-id="aae8b-154">Hashtabellen herhalen</span><span class="sxs-lookup"><span data-stu-id="aae8b-154">Iterating hashtables</span></span>

<span data-ttu-id="aae8b-155">Omdat een hashtabel bestaat uit een verzameling sleutel-waardeparen, voert u een andere sequentie in dan die voor een matrix of een normale lijst met items.</span><span class="sxs-lookup"><span data-stu-id="aae8b-155">Because a hashtable is a collection of key/value pairs, you iterate over it differently than you do for an array or a normal list of items.</span></span>

<span data-ttu-id="aae8b-156">Het eerste dat u moet nadoen, is dat als u de hashtabel bewaart, de pipe als één object beschouwt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-156">The first thing to notice is that if you pipe your hashtable, the pipe treats it like one object.</span></span>

```powershell
PS> $ageList | Measure-Object
count : 1
```

<span data-ttu-id="aae8b-157">Hoewel de `.count` eigenschap vertelt u hoeveel waarden deze bevat.</span><span class="sxs-lookup"><span data-stu-id="aae8b-157">Even though the `.count` property tells you how many values it contains.</span></span>

```powershell
PS> $ageList.count
2
```

<span data-ttu-id="aae8b-158">U kunt dit probleem omzeilen door de `.values` eigenschap te gebruiken als u alleen de waarden hoeft op te geven.</span><span class="sxs-lookup"><span data-stu-id="aae8b-158">You get around this issue by using the `.values` property if all you need is just the values.</span></span>

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

<span data-ttu-id="aae8b-159">Het is vaak handiger om de sleutels te inventariseren en gebruiken om toegang te krijgen tot de waarden.</span><span class="sxs-lookup"><span data-stu-id="aae8b-159">It's often more useful to enumerate the keys and use them to access the values.</span></span>

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

<span data-ttu-id="aae8b-160">Hier volgt een voor beeld met een `foreach(){...}` lus.</span><span class="sxs-lookup"><span data-stu-id="aae8b-160">Here is the same example with a `foreach(){...}` loop.</span></span>

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

<span data-ttu-id="aae8b-161">Elke sleutel in de hashtabel wordt door lopen en vervolgens gebruikt om toegang te krijgen tot de waarde.</span><span class="sxs-lookup"><span data-stu-id="aae8b-161">We are walking each key in the hashtable and then using it to access the value.</span></span> <span data-ttu-id="aae8b-162">Dit is een algemeen patroon wanneer u met hashtabellen werkt als een verzameling.</span><span class="sxs-lookup"><span data-stu-id="aae8b-162">This is a common pattern when working with hashtables as a collection.</span></span>

### <a name="getenumerator"></a><span data-ttu-id="aae8b-163">GetEnumerator ()</span><span class="sxs-lookup"><span data-stu-id="aae8b-163">GetEnumerator()</span></span>

<span data-ttu-id="aae8b-164">Dit zorgt ervoor dat we de `GetEnumerator()` hashtabel kunnen herhalen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-164">That brings us to `GetEnumerator()` for iterating over our hashtable.</span></span>

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

<span data-ttu-id="aae8b-165">De enumerator geeft u elk sleutel/waarde-paar op één na andere.</span><span class="sxs-lookup"><span data-stu-id="aae8b-165">The enumerator gives you each key/value pair one after another.</span></span> <span data-ttu-id="aae8b-166">Het is specifiek ontworpen voor deze use-case.</span><span class="sxs-lookup"><span data-stu-id="aae8b-166">It was designed specifically for this use case.</span></span> <span data-ttu-id="aae8b-167">Hartelijk dank dat u [Kraus markeert](https://get-PowerShellblog.blogspot.com) om dit te onthouden.</span><span class="sxs-lookup"><span data-stu-id="aae8b-167">Thank you to [Mark Kraus](https://get-PowerShellblog.blogspot.com) for reminding me of this one.</span></span>

### <a name="badenumeration"></a><span data-ttu-id="aae8b-168">BadEnumeration</span><span class="sxs-lookup"><span data-stu-id="aae8b-168">BadEnumeration</span></span>

<span data-ttu-id="aae8b-169">Een van de belang rijke details is dat u een hashtabel niet kunt wijzigen tijdens het inventariseren.</span><span class="sxs-lookup"><span data-stu-id="aae8b-169">One important detail is that you can't modify a hashtable while it's being enumerated.</span></span> <span data-ttu-id="aae8b-170">Als we beginnen met het basis `$environments` voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="aae8b-170">If we start with our basic `$environments` example:</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

<span data-ttu-id="aae8b-171">En het instellen van elke sleutel op dezelfde server waarde mislukt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-171">And trying to set every key to the same server value fails.</span></span>

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

<span data-ttu-id="aae8b-172">Dit kan ook gebeuren, zelfs als het lijkt alsof het ook goed is:</span><span class="sxs-lookup"><span data-stu-id="aae8b-172">This will also fail even though it looks like it should also be fine:</span></span>

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

<span data-ttu-id="aae8b-173">De truc van deze situatie is het klonen van de sleutels voordat u de inventarisatie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="aae8b-173">The trick to this situation is to clone the keys before doing the enumeration.</span></span>

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a><span data-ttu-id="aae8b-174">Hashtabel als een verzameling eigenschappen</span><span class="sxs-lookup"><span data-stu-id="aae8b-174">Hashtable as a collection of properties</span></span>

<span data-ttu-id="aae8b-175">Tot nu toe was het type van de objecten die we in onze hashtabel hebben geplaatst, allemaal hetzelfde type object.</span><span class="sxs-lookup"><span data-stu-id="aae8b-175">So far the type of objects we placed in our hashtable were all the same type of object.</span></span> <span data-ttu-id="aae8b-176">Ik heb in al deze voor beelden leeftijden gebruikt en de sleutel is de naam van de persoon.</span><span class="sxs-lookup"><span data-stu-id="aae8b-176">I used ages in all those examples and the key was the person's name.</span></span> <span data-ttu-id="aae8b-177">Dit is een uitstekende manier om ernaar te kijken wanneer uw verzameling objecten elk een naam heeft.</span><span class="sxs-lookup"><span data-stu-id="aae8b-177">This is a great way to look at it when your collection of objects each have a name.</span></span> <span data-ttu-id="aae8b-178">Een andere gang bare manier om hashtabellen te gebruiken in Power shell is een verzameling eigenschappen te bewaren waarbij de sleutel de naam van de eigenschap is.</span><span class="sxs-lookup"><span data-stu-id="aae8b-178">Another common way to use hashtables in PowerShell is to hold a collection of properties where the key is the name of the property.</span></span> <span data-ttu-id="aae8b-179">Ik Step Into dat idee in dit volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="aae8b-179">I'll step into that idea in this next example.</span></span>

### <a name="property-based-access"></a><span data-ttu-id="aae8b-180">Toegang op basis van eigenschappen</span><span class="sxs-lookup"><span data-stu-id="aae8b-180">Property-based access</span></span>

<span data-ttu-id="aae8b-181">Het gebruik van op eigenschappen gebaseerde toegang wijzigt de dynamiek van hashtabellen en hoe u deze kunt gebruiken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="aae8b-181">The use of property-based access changes the dynamics of hashtables and how you can use them in PowerShell.</span></span> <span data-ttu-id="aae8b-182">Hieronder ziet u een voor beeld van de bovenstaande sleutels als eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-182">Here is our usual example from above treating the keys as properties.</span></span>

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

<span data-ttu-id="aae8b-183">Net als in de bovenstaande voor beelden voegt u in dit voor beeld deze sleutels toe als ze al in de hashtabel aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="aae8b-183">Just like the examples above, this example adds those keys if they don't exist in the hashtable already.</span></span> <span data-ttu-id="aae8b-184">Afhankelijk van hoe u uw sleutels hebt gedefinieerd en wat uw waarden zijn, is dit een beetje vreemde of een perfecte keuze.</span><span class="sxs-lookup"><span data-stu-id="aae8b-184">Depending on how you defined your keys and what your values are, this is either a little strange or a perfect fit.</span></span> <span data-ttu-id="aae8b-185">Het voor beeld van de leeftijds lijst is tot dit punt goed gewerkt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-185">The age list example has worked great up until this point.</span></span> <span data-ttu-id="aae8b-186">We hebben een nieuw voor beeld nodig om aan de slag te gaan.</span><span class="sxs-lookup"><span data-stu-id="aae8b-186">We need a new example for this to feel right going forward.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="aae8b-187">En we kunnen op deze manier kenmerken toevoegen en er toegang toe krijgen `$person` .</span><span class="sxs-lookup"><span data-stu-id="aae8b-187">And we can add and access attributes on the `$person` like this.</span></span>

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

<span data-ttu-id="aae8b-188">Het enige wat een plotselinge hash van deze hashtabel is, lijkt een object te zijn.</span><span class="sxs-lookup"><span data-stu-id="aae8b-188">All of a sudden this hashtable starts to feel and act like an object.</span></span> <span data-ttu-id="aae8b-189">Er is nog steeds een verzameling dingen, dus alle bovenstaande voor beelden zijn nog steeds van toepassing.</span><span class="sxs-lookup"><span data-stu-id="aae8b-189">It's still a collection of things, so all the examples above still apply.</span></span> <span data-ttu-id="aae8b-190">We benadert dit gewoon vanuit een ander weergave punt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-190">We just approach it from a different point of view.</span></span>

### <a name="checking-for-keys-and-values"></a><span data-ttu-id="aae8b-191">Controleren op sleutels en waarden</span><span class="sxs-lookup"><span data-stu-id="aae8b-191">Checking for keys and values</span></span>

<span data-ttu-id="aae8b-192">In de meeste gevallen kunt u gewoon testen op de waarde, wat er ongeveer als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="aae8b-192">In most cases, you can just test for the value with something like this:</span></span>

```powershell
if( $person.age ){...}
```

<span data-ttu-id="aae8b-193">Het is eenvoudig, maar is de bron van veel fouten voor mij, omdat er een belang rijke details in mijn logica worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aae8b-193">It's simple but has been the source of many bugs for me because I was overlooking one important detail in my logic.</span></span> <span data-ttu-id="aae8b-194">Ik ben begonnen met het gebruik ervan om te testen of er een sleutel aanwezig was.</span><span class="sxs-lookup"><span data-stu-id="aae8b-194">I started to use it to test if a key was present.</span></span> <span data-ttu-id="aae8b-195">Als de waarde is `$false` of nul, zou deze instructie `$false` onverwacht worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="aae8b-195">When the value was `$false` or zero, that statement would return `$false` unexpectedly.</span></span>

```powershell
if( $person.age -ne $null ){...}
```

<span data-ttu-id="aae8b-196">Dit werkt rond het probleem voor nulwaarden, maar niet $null versus niet-bestaande sleutels.</span><span class="sxs-lookup"><span data-stu-id="aae8b-196">This works around that issue for zero values but not $null vs non-existent keys.</span></span> <span data-ttu-id="aae8b-197">In de meeste gevallen hoeft u dit onderscheid niet te maken, maar er zijn functies voor wanneer u dat doet.</span><span class="sxs-lookup"><span data-stu-id="aae8b-197">Most of the time you don't need to make that distinction but there are functions for when you do.</span></span>

```powershell
if( $person.ContainsKey('age') ){...}
```

<span data-ttu-id="aae8b-198">We hebben ook een `ContainsValue()` voor de situatie waarin u moet testen op een waarde zonder de sleutel te weten of de hele verzameling te herhalen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-198">We also have a `ContainsValue()` for the situation where you need to test for a value without knowing the key or iterating the whole collection.</span></span>

### <a name="removing-and-clearing-keys"></a><span data-ttu-id="aae8b-199">Sleutels verwijderen en wissen</span><span class="sxs-lookup"><span data-stu-id="aae8b-199">Removing and clearing keys</span></span>

<span data-ttu-id="aae8b-200">U kunt sleutels verwijderen met de `.Remove()` functie.</span><span class="sxs-lookup"><span data-stu-id="aae8b-200">You can remove keys with the `.Remove()` function.</span></span>

```powershell
$person.remove('age')
```

<span data-ttu-id="aae8b-201">Als u een waarde toewijst, `$null` hoeft u alleen een sleutel met een waarde op te geven `$null` .</span><span class="sxs-lookup"><span data-stu-id="aae8b-201">Assigning them a `$null` value just leaves you with a key that has a `$null` value.</span></span>

<span data-ttu-id="aae8b-202">Een gemeen schappelijke manier om een hashtabel te wissen, is om deze eenvoudigweg te initialiseren naar een lege hashtabel.</span><span class="sxs-lookup"><span data-stu-id="aae8b-202">A common way to clear a hashtable is to just initialize it to an empty hashtable.</span></span>

```powershell
$person = @{}
```

<span data-ttu-id="aae8b-203">Probeer `clear()` in plaats daarvan de functie te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-203">While that does work, try to use the `clear()` function instead.</span></span>

```powershell
$person.clear()
```

<span data-ttu-id="aae8b-204">Dit is een van deze gevallen waarbij het gebruik van de functie zelf-document code maakt en de bedoelingen van de code zeer helder maakt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-204">This is one of those instances where using the function creates self-documenting code and it makes the intentions of the code very clean.</span></span>

## <a name="all-the-fun-stuff"></a><span data-ttu-id="aae8b-205">Alle leuke dingen</span><span class="sxs-lookup"><span data-stu-id="aae8b-205">All the fun stuff</span></span>

### <a name="ordered-hashtables"></a><span data-ttu-id="aae8b-206">Besteld hashtabellen</span><span class="sxs-lookup"><span data-stu-id="aae8b-206">Ordered hashtables</span></span>

<span data-ttu-id="aae8b-207">Hashtabellen zijn standaard niet gerangschikt (of gesorteerd).</span><span class="sxs-lookup"><span data-stu-id="aae8b-207">By default, hashtables aren't ordered (or sorted).</span></span> <span data-ttu-id="aae8b-208">In de traditionele context is de volg orde niet belang rijk wanneer u altijd een sleutel gebruikt om toegang te krijgen tot waarden.</span><span class="sxs-lookup"><span data-stu-id="aae8b-208">In the traditional context, the order doesn't matter when you always use a key to access values.</span></span> <span data-ttu-id="aae8b-209">Mogelijk wilt u dat de eigenschappen in de volg orde blijven staan waarin u ze definieert.</span><span class="sxs-lookup"><span data-stu-id="aae8b-209">You may find that you want the properties to stay in the order that you define them.</span></span> <span data-ttu-id="aae8b-210">Gelukkig, er is een manier om dat te doen met het `ordered` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="aae8b-210">Thankfully, there's a way to do that with the `ordered` keyword.</span></span>

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="aae8b-211">Wanneer u de sleutels en waarden nu opsomt, blijven ze in die volg orde.</span><span class="sxs-lookup"><span data-stu-id="aae8b-211">Now when you enumerate the keys and values, they stay in that order.</span></span>

### <a name="inline-hashtables"></a><span data-ttu-id="aae8b-212">Inline-hashtabellen</span><span class="sxs-lookup"><span data-stu-id="aae8b-212">Inline hashtables</span></span>

<span data-ttu-id="aae8b-213">Wanneer u een hashtabel op één regel definieert, kunt u de sleutel-waardeparen scheiden met een punt komma.</span><span class="sxs-lookup"><span data-stu-id="aae8b-213">When you're defining a hashtable on one line, you can separate the key/value pairs with a semicolon.</span></span>

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

<span data-ttu-id="aae8b-214">Dit kan handig zijn als u ze op de pipe maakt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-214">This will come in handy if you're creating them on the pipe.</span></span>

### <a name="custom-expressions-in-common-pipeline-commands"></a><span data-ttu-id="aae8b-215">Aangepaste expressies in algemene pijplijn opdrachten</span><span class="sxs-lookup"><span data-stu-id="aae8b-215">Custom expressions in common pipeline commands</span></span>

<span data-ttu-id="aae8b-216">Er zijn enkele cmdlets die ondersteuning bieden voor het gebruik van hashtabellen om aangepaste of berekende eigenschappen te maken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-216">There are a few cmdlets that support the use of hashtables to create custom or calculated properties.</span></span> <span data-ttu-id="aae8b-217">U ziet dit meestal met `Select-Object` en `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="aae8b-217">You commonly see this with `Select-Object` and `Format-Table`.</span></span> <span data-ttu-id="aae8b-218">De hashtabellen hebben een speciale syntaxis die er als volgt uitziet wanneer deze volledig is uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-218">The hashtables have a special syntax that looks like this when fully expanded.</span></span>

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

<span data-ttu-id="aae8b-219">De `name` is wat de cmdlet zou labelen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-219">The `name` is what the cmdlet would label that column.</span></span> <span data-ttu-id="aae8b-220">Het `expression` is een script blok dat wordt uitgevoerd, waarbij `$_` de waarde van het object op de pipe is.</span><span class="sxs-lookup"><span data-stu-id="aae8b-220">The `expression` is a script block that is executed where `$_` is the value of the object on the pipe.</span></span> <span data-ttu-id="aae8b-221">Dit is het script in actie:</span><span class="sxs-lookup"><span data-stu-id="aae8b-221">Here is that script in action:</span></span>

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Property name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

<span data-ttu-id="aae8b-222">Ik heb dat in een variabele geplaatst, maar dit kan gemakkelijk inline worden gedefinieerd, en u kunt de kortings functie voor u verkorten `name` `n` `expression` `e` .</span><span class="sxs-lookup"><span data-stu-id="aae8b-222">I placed that in a variable but it could easily be defined inline and you can shorten `name` to `n` and `expression` to `e` while you're at it.</span></span>

```powershell
$drives | Select-Object -property name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

<span data-ttu-id="aae8b-223">Ik weet niet hoe lang het duurt om opdrachten uit te geven. het bevordert vaak een slecht gedrag dat daar niet aan is.</span><span class="sxs-lookup"><span data-stu-id="aae8b-223">I personally don't like how long that makes commands and it often promotes some bad behaviors that I won't get into.</span></span> <span data-ttu-id="aae8b-224">Ik wil waarschijnlijk een nieuwe hashtabel maken of `pscustomobject` met alle velden en eigenschappen die ik wil gebruiken in plaats van deze benadering in scripts.</span><span class="sxs-lookup"><span data-stu-id="aae8b-224">I'm more likely to create a new hashtable or `pscustomobject` with all the fields and properties that I want instead of using this approach in scripts.</span></span> <span data-ttu-id="aae8b-225">Maar er is wel een groot aantal Program meren waarmee u op de hoogte zou zijn.</span><span class="sxs-lookup"><span data-stu-id="aae8b-225">But there's a lot of code out there that does this so I wanted you to be aware of it.</span></span> <span data-ttu-id="aae8b-226">Ik vind iets over het maken `pscustomobject` van een latere versie.</span><span class="sxs-lookup"><span data-stu-id="aae8b-226">I talk about creating a `pscustomobject` later on.</span></span>

### <a name="custom-sort-expression"></a><span data-ttu-id="aae8b-227">Aangepaste Sorteer expressie</span><span class="sxs-lookup"><span data-stu-id="aae8b-227">Custom sort expression</span></span>

<span data-ttu-id="aae8b-228">Het is eenvoudig om een verzameling te sorteren als de objecten de gegevens bevatten waarop u wilt sorteren.</span><span class="sxs-lookup"><span data-stu-id="aae8b-228">It's easy to sort a collection if the objects have the data that you want to sort on.</span></span> <span data-ttu-id="aae8b-229">U kunt de gegevens toevoegen aan het object voordat u het sorteert of een aangepaste expressie maakt voor `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="aae8b-229">You can either add the data to the object before you sort it or create a custom expression for `Sort-Object`.</span></span>

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

<span data-ttu-id="aae8b-230">In dit voor beeld maken we een lijst met gebruikers en gebruiken we een aangepaste cmdlet om meer informatie te krijgen voor de sorteer bewerking.</span><span class="sxs-lookup"><span data-stu-id="aae8b-230">In this example I'm taking a list of users and using some custom cmdlet to get additional information just for the sort.</span></span>

#### <a name="sort-a-list-of-hashtables"></a><span data-ttu-id="aae8b-231">Een lijst met hashtabellen sorteren</span><span class="sxs-lookup"><span data-stu-id="aae8b-231">Sort a list of Hashtables</span></span>

<span data-ttu-id="aae8b-232">Als u een lijst met hashtabellen hebt die u wilt sorteren, zult u zien dat de `Sort-Object` sleutels niet worden behandeld als eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-232">If you have a list of hashtables that you want to sort, you'll find that the `Sort-Object` doesn't treat your keys as properties.</span></span> <span data-ttu-id="aae8b-233">We kunnen een afronding krijgen met behulp van een aangepaste Sorteer expressie.</span><span class="sxs-lookup"><span data-stu-id="aae8b-233">We can get a round that by using a custom sort expression.</span></span>

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a><span data-ttu-id="aae8b-234">Splatting hashtabellen bij cmdlets</span><span class="sxs-lookup"><span data-stu-id="aae8b-234">Splatting hashtables at cmdlets</span></span>

<span data-ttu-id="aae8b-235">Dit is een van mijn favoriete dingen over hashtabellen die veel mensen niet vroeg ontdekken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-235">This is one of my favorite things about hashtables that many people don't discover early on.</span></span>
<span data-ttu-id="aae8b-236">Het idee is dat u in plaats van alle eigenschappen een cmdlet op één regel moet opgeven, maar u kunt ze eerst in een hashtabel inpakken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-236">The idea is that instead of providing all the properties to a cmdlet on one line, you can instead pack them into a hashtable first.</span></span> <span data-ttu-id="aae8b-237">U kunt de hashtabel vervolgens op een speciale manier aan de functie toewijzen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-237">Then you can give the hashtable to the function in a special way.</span></span>
<span data-ttu-id="aae8b-238">Hier volgt een voor beeld van het maken van een DHCP-scope op de normale manier.</span><span class="sxs-lookup"><span data-stu-id="aae8b-238">Here is an example of creating a DHCP scope the normal way.</span></span>

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

<span data-ttu-id="aae8b-239">Als [splatting][]niet wordt gebruikt, moeten al deze dingen op één regel worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="aae8b-239">Without using [splatting][], all those things need to be defined on a single line.</span></span> <span data-ttu-id="aae8b-240">Er wordt een schuif balk van het scherm weer gegeven of er wordt gewikkeld waar ooit het lijkt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-240">It either scrolls off the screen or will wrap where ever it feels like.</span></span> <span data-ttu-id="aae8b-241">Vergelijk nu met een opdracht die gebruikmaakt van splatting.</span><span class="sxs-lookup"><span data-stu-id="aae8b-241">Now compare that to a command that uses splatting.</span></span>

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

<span data-ttu-id="aae8b-242">Het gebruik van het `@` teken in plaats van de `$` is het aanroepen van de splat-bewerking.</span><span class="sxs-lookup"><span data-stu-id="aae8b-242">The use of the `@` sign instead of the `$` is what invokes the splat operation.</span></span>

<span data-ttu-id="aae8b-243">Neem even de tijd om te weten hoe eenvoudig het voor beeld is te lezen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-243">Just take a moment to appreciate how easy that example is to read.</span></span> <span data-ttu-id="aae8b-244">Ze zijn exact dezelfde opdracht met dezelfde waarden.</span><span class="sxs-lookup"><span data-stu-id="aae8b-244">They are the exact same command with all the same values.</span></span> <span data-ttu-id="aae8b-245">De tweede is gemakkelijker te begrijpen en verder te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="aae8b-245">The second one is easier to understand and maintain going forward.</span></span>

<span data-ttu-id="aae8b-246">Ik gebruik splatting altijd wanneer de opdracht te lang wordt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-246">I use splatting anytime the command gets too long.</span></span> <span data-ttu-id="aae8b-247">Er wordt te lang gedefinieerd, waardoor mijn venster naar rechts schuift.</span><span class="sxs-lookup"><span data-stu-id="aae8b-247">I define too long as causing my window to scroll right.</span></span> <span data-ttu-id="aae8b-248">Als ik drie eigenschappen voor een functie raak, zijn conflicteert dat ik deze herschrijft met behulp van een splatted hashtabel.</span><span class="sxs-lookup"><span data-stu-id="aae8b-248">If I hit three properties for a function, odds are that I'll rewrite it using a splatted hashtable.</span></span>

### <a name="splatting-for-optional-parameters"></a><span data-ttu-id="aae8b-249">Splatting voor optionele para meters</span><span class="sxs-lookup"><span data-stu-id="aae8b-249">Splatting for optional parameters</span></span>

<span data-ttu-id="aae8b-250">Een van de meest voorkomende manieren om splatting te gebruiken, is door te omgaan met optionele para meters die afkomstig zijn van andere plaatsen in mijn script.</span><span class="sxs-lookup"><span data-stu-id="aae8b-250">One of the most common ways I use splatting is to deal with optional parameters that come from some place else in my script.</span></span> <span data-ttu-id="aae8b-251">Stel dat ik een functie heb waarmee een `Get-CIMInstance` aanroep met een optioneel argument wordt ingepakt `$Credential` .</span><span class="sxs-lookup"><span data-stu-id="aae8b-251">Let's say I have a function that wraps a `Get-CIMInstance` call that has an optional `$Credential` argument.</span></span>

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

<span data-ttu-id="aae8b-252">U begint met het maken van mijn hashtabel met algemene para meters.</span><span class="sxs-lookup"><span data-stu-id="aae8b-252">I start by creating my hashtable with common parameters.</span></span> <span data-ttu-id="aae8b-253">Vervolgens voeg ik de toe `$Credential` als deze bestaat.</span><span class="sxs-lookup"><span data-stu-id="aae8b-253">Then I add the `$Credential` if it exists.</span></span>
<span data-ttu-id="aae8b-254">Omdat ik splatting hier gebruik, hoeft ik alleen maar `Get-CIMInstance` één keer naar mijn code te bellen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-254">Because I'm using splatting here, I only need to have the call to `Get-CIMInstance` in my code once.</span></span> <span data-ttu-id="aae8b-255">Dit ontwerp patroon is zeer helder en kan veel optionele para meters eenvoudig verwerken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-255">This design pattern is very clean and can handle lots of optional parameters easily.</span></span>

<span data-ttu-id="aae8b-256">Als u eerlijk wilt zijn, kunt u uw opdrachten schrijven om `$null` waarden voor para meters toe te staan.</span><span class="sxs-lookup"><span data-stu-id="aae8b-256">To be fair, you could write your commands to allow `$null` values for parameters.</span></span> <span data-ttu-id="aae8b-257">U hebt gewoon niet altijd de controle over de andere opdrachten die u aanroept.</span><span class="sxs-lookup"><span data-stu-id="aae8b-257">You just don't always have control over the other commands you're calling.</span></span>

### <a name="multiple-splats"></a><span data-ttu-id="aae8b-258">Meerdere splats</span><span class="sxs-lookup"><span data-stu-id="aae8b-258">Multiple splats</span></span>

<span data-ttu-id="aae8b-259">U kunt meerdere hashtabellen naar dezelfde cmdlet splat.</span><span class="sxs-lookup"><span data-stu-id="aae8b-259">You can splat multiple hashtables to the same cmdlet.</span></span> <span data-ttu-id="aae8b-260">Als we ons oorspronkelijke splatting-voor beeld bekijken:</span><span class="sxs-lookup"><span data-stu-id="aae8b-260">If we revisit our original splatting example:</span></span>

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

<span data-ttu-id="aae8b-261">Ik gebruik deze methode wanneer ik een gemeen schappelijke set para meters heb die ik aan een groot aantal opdrachten kan door geven.</span><span class="sxs-lookup"><span data-stu-id="aae8b-261">I'll use this method when I have a common set of parameters that I'm passing to lots of commands.</span></span>

### <a name="splatting-for-clean-code"></a><span data-ttu-id="aae8b-262">Splatting voor schone code</span><span class="sxs-lookup"><span data-stu-id="aae8b-262">Splatting for clean code</span></span>

<span data-ttu-id="aae8b-263">Er is niets mis met het splatting van een enkele para meter als u code kunt opschonen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-263">There's nothing wrong with splatting a single parameter if makes you code cleaner.</span></span>

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a><span data-ttu-id="aae8b-264">Splatting uitvoer bare bestanden</span><span class="sxs-lookup"><span data-stu-id="aae8b-264">Splatting executables</span></span>

<span data-ttu-id="aae8b-265">Splatting werkt ook voor sommige uitvoer bare bestanden die gebruikmaken van een `/param:value` syntaxis.</span><span class="sxs-lookup"><span data-stu-id="aae8b-265">Splatting also works on some executables that use a `/param:value` syntax.</span></span> <span data-ttu-id="aae8b-266">`Robocopy.exe`heeft bijvoorbeeld een aantal para meters zoals deze.</span><span class="sxs-lookup"><span data-stu-id="aae8b-266">`Robocopy.exe`, for example, has some parameters like this.</span></span>

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

<span data-ttu-id="aae8b-267">Ik weet niet dat dit nuttig is, maar ik heb het interessant vond.</span><span class="sxs-lookup"><span data-stu-id="aae8b-267">I don't know that this is all that useful, but I found it interesting.</span></span>

## <a name="adding-hashtables"></a><span data-ttu-id="aae8b-268">Hashtabellen toevoegen</span><span class="sxs-lookup"><span data-stu-id="aae8b-268">Adding hashtables</span></span>

<span data-ttu-id="aae8b-269">Hashtabellen ondersteunen de operator voor optellen om twee hashtabellen te combi neren.</span><span class="sxs-lookup"><span data-stu-id="aae8b-269">Hashtables support the addition operator to combine two hashtables.</span></span>

```powershell
$person += @{Zip = '78701'}
```

<span data-ttu-id="aae8b-270">Dit werkt alleen als de twee hashtabellen geen sleutel delen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-270">This only works if the two hashtables don't share a key.</span></span>

## <a name="nested-hashtables"></a><span data-ttu-id="aae8b-271">Geneste hashtabellen</span><span class="sxs-lookup"><span data-stu-id="aae8b-271">Nested hashtables</span></span>

<span data-ttu-id="aae8b-272">We kunnen hashtabellen gebruiken als waarden binnen een hashtabel.</span><span class="sxs-lookup"><span data-stu-id="aae8b-272">We can use hashtables as values inside a hashtable.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

<span data-ttu-id="aae8b-273">Ik heb een basis-hashtabel met twee sleutels gestart.</span><span class="sxs-lookup"><span data-stu-id="aae8b-273">I started with a basic hashtable containing two keys.</span></span> <span data-ttu-id="aae8b-274">Ik heb een sleutel `location` met de naam met een lege hashtabel toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="aae8b-274">I added a key called `location` with an empty hashtable.</span></span> <span data-ttu-id="aae8b-275">Vervolgens zijn de laatste twee items toegevoegd aan die `location` hashtabel.</span><span class="sxs-lookup"><span data-stu-id="aae8b-275">Then I added the last two items to that `location` hashtable.</span></span> <span data-ttu-id="aae8b-276">We kunnen dit ook doen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-276">We can do this all inline too.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

<span data-ttu-id="aae8b-277">Hiermee maakt u dezelfde hashtabel die we hierboven hebben gezien en toegang hebben tot de eigenschappen op dezelfde manier.</span><span class="sxs-lookup"><span data-stu-id="aae8b-277">This creates the same hashtable that we saw above and can access the properties the same way.</span></span>

```powershell
$person.location.city
Austin
```

<span data-ttu-id="aae8b-278">Er zijn veel manieren om de structuur van uw objecten te benaderen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-278">There are many ways to approach the structure of your objects.</span></span> <span data-ttu-id="aae8b-279">Hier volgt een tweede manier om een geneste hashtabel te bekijken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-279">Here is a second way to look at a nested hashtable.</span></span>

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

<span data-ttu-id="aae8b-280">Dit is een combi Naties van het concept van het gebruik van hashtabellen als een verzameling objecten en een verzameling eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-280">This mixes the concept of using hashtables as a collection of objects and a collection of properties.</span></span> <span data-ttu-id="aae8b-281">De waarden zijn nog steeds eenvoudig te benaderen, zelfs wanneer ze zijn genest met een wille keurige benadering.</span><span class="sxs-lookup"><span data-stu-id="aae8b-281">The values are still easy to access even when they're nested using whatever approach you prefer.</span></span>

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

<span data-ttu-id="aae8b-282">Ik gebruik de punt eigenschap vaak wanneer ik deze wil behandelen als een eigenschap.</span><span class="sxs-lookup"><span data-stu-id="aae8b-282">I tend to use the dot property when I'm treating it like a property.</span></span> <span data-ttu-id="aae8b-283">Dit zijn doorgaans de dingen die ik statisch heb gedefinieerd in mijn code en ik weet dat ze zich op de bovenkant van mijn hoofd bevinden.</span><span class="sxs-lookup"><span data-stu-id="aae8b-283">Those are generally things I've defined statically in my code and I know them off the top of my head.</span></span> <span data-ttu-id="aae8b-284">Als ik de lijst wil door lopen of op een programmatische manier toegang wil krijgen tot de toetsen, gebruik ik de vier Kante haken om de naam van de sleutel op te geven.</span><span class="sxs-lookup"><span data-stu-id="aae8b-284">If I need to walk the list or programmatically access the keys, I use the brackets to provide the key name.</span></span>

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

<span data-ttu-id="aae8b-285">Met de mogelijkheid om hashtabellen te nesten, hebt u veel flexibiliteit en opties.</span><span class="sxs-lookup"><span data-stu-id="aae8b-285">Having the ability to nest hashtables gives you a lot of flexibility and options.</span></span>

### <a name="looking-at-nested-hashtables"></a><span data-ttu-id="aae8b-286">Geneste hashtabellen bekijken</span><span class="sxs-lookup"><span data-stu-id="aae8b-286">Looking at nested hashtables</span></span>

<span data-ttu-id="aae8b-287">Zodra u begint met het nesten van hashtabellen, hebt u een eenvoudige manier nodig om ze te bekijken vanuit de-console.</span><span class="sxs-lookup"><span data-stu-id="aae8b-287">As soon as you start nesting hashtables, you're going to need an easy way to look at them from the console.</span></span> <span data-ttu-id="aae8b-288">Als ik deze laatste hashtabel, krijg ik een uitvoer die er als volgt uitziet en zo dieper gaat:</span><span class="sxs-lookup"><span data-stu-id="aae8b-288">If I take that last hashtable, I get an output that looks like this and it only goes so deep:</span></span>

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

<span data-ttu-id="aae8b-289">Mijn ga naar opdracht voor het bekijken van deze dingen is `ConvertTo-JSON` omdat deze zeer schoon is en dat ik regel matig JSON op andere zaken zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-289">My go to command for looking at these things is `ConvertTo-JSON` because it's very clean and I frequently use JSON on other things.</span></span>

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

<span data-ttu-id="aae8b-290">Zelfs als u geen JSON kent, kunt u zien wat u zoekt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-290">Even if you don't know JSON, you should be able to see what you're looking for.</span></span> <span data-ttu-id="aae8b-291">Er is een `Format-Custom` opdracht voor gestructureerde gegevens, zoals deze, maar de JSON-weer gave is beter.</span><span class="sxs-lookup"><span data-stu-id="aae8b-291">There's a `Format-Custom` command for structured data like this but I still like the JSON view better.</span></span>

## <a name="creating-objects"></a><span data-ttu-id="aae8b-292">Objecten maken</span><span class="sxs-lookup"><span data-stu-id="aae8b-292">Creating objects</span></span>

<span data-ttu-id="aae8b-293">Soms hoeft u alleen maar een object te hebben en een hashtabel te gebruiken om eigenschappen te bewaren, maar wordt de taak niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aae8b-293">Sometimes you just need to have an object and using a hashtable to hold properties just isn't getting the job done.</span></span> <span data-ttu-id="aae8b-294">Doorgaans wilt u de sleutels zien als kolom namen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-294">Most commonly you want to see the keys as column names.</span></span> <span data-ttu-id="aae8b-295">Een `pscustomobject` maakt dat eenvoudig.</span><span class="sxs-lookup"><span data-stu-id="aae8b-295">A `pscustomobject` makes that easy.</span></span>

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="aae8b-296">Zelfs als u deze niet `pscustomobject` in eerste instantie maakt, kunt u deze altijd later opnieuw casten wanneer dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="aae8b-296">Even if you don't create it as a `pscustomobject` initially, you can always cast it later when needed.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="aae8b-297">Ik heb al een gedetailleerde write-up voor [pscustomobject][] die je na deze versie moet lezen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-297">I already have detailed write-up for [pscustomobject][] that you should go read after this one.</span></span> <span data-ttu-id="aae8b-298">Het is gebaseerd op een groot aantal dingen die hier worden geleerd.</span><span class="sxs-lookup"><span data-stu-id="aae8b-298">It builds on a lot of the things learned here.</span></span>

## <a name="reading-and-writing-hashtables-to-file"></a><span data-ttu-id="aae8b-299">Hashtabellen lezen en schrijven naar bestand</span><span class="sxs-lookup"><span data-stu-id="aae8b-299">Reading and writing hashtables to file</span></span>

### <a name="saving-to-csv"></a><span data-ttu-id="aae8b-300">Opslaan in CSV</span><span class="sxs-lookup"><span data-stu-id="aae8b-300">Saving to CSV</span></span>

<span data-ttu-id="aae8b-301">Lastig met het ophalen van een hashtabel om op te slaan in een CSV, is een van de problemen waarnaar wordt verwezen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-301">Struggling with getting a hashtable to save to a CSV is one of the difficulties that I was referring to above.</span></span> <span data-ttu-id="aae8b-302">Converteer uw hashtabel naar een `pscustomobject` en wordt op de juiste manier opgeslagen in CSV.</span><span class="sxs-lookup"><span data-stu-id="aae8b-302">Convert your hashtable to a `pscustomobject` and it will save correctly to CSV.</span></span> <span data-ttu-id="aae8b-303">Zo kunt u beginnen met een `pscustomobject` zodat de volg orde van de kolommen behouden blijft.</span><span class="sxs-lookup"><span data-stu-id="aae8b-303">It helps if you start with a `pscustomobject` so the column order is preserved.</span></span> <span data-ttu-id="aae8b-304">Maar u kunt deze `pscustomobject` indien nodig naar een inline casten.</span><span class="sxs-lookup"><span data-stu-id="aae8b-304">But you can cast it to a `pscustomobject` inline if needed.</span></span>

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

<span data-ttu-id="aae8b-305">Ga opnieuw naar mijn write-up met behulp van een [pscustomobject][].</span><span class="sxs-lookup"><span data-stu-id="aae8b-305">Again, check out my write-up on using a [pscustomobject][].</span></span>

### <a name="saving-a-nested-hashtable-to-file"></a><span data-ttu-id="aae8b-306">Een geneste hashtabel opslaan in een bestand</span><span class="sxs-lookup"><span data-stu-id="aae8b-306">Saving a nested hashtable to file</span></span>

<span data-ttu-id="aae8b-307">Als ik een geneste hashtabel moet opslaan in een bestand en deze vervolgens weer kan lezen, moet ik de JSON-cmdlets gebruiken om het te doen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-307">If I need to save a nested hashtable to a file and then read it back in again, I use the JSON cmdlets to do it.</span></span>

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

<span data-ttu-id="aae8b-308">Er zijn twee belang rijke punten over deze methode.</span><span class="sxs-lookup"><span data-stu-id="aae8b-308">There are two important points about this method.</span></span> <span data-ttu-id="aae8b-309">Ten eerste is de JSON wegge schreven, zodat ik de optie moet gebruiken `-Raw` om deze weer in één teken reeks te lezen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-309">First is that the JSON is written out multiline so I need to use the `-Raw` option to read it back into a single string.</span></span> <span data-ttu-id="aae8b-310">Ten tweede is het geïmporteerde object niet meer een `[hashtable]` .</span><span class="sxs-lookup"><span data-stu-id="aae8b-310">The Second is that the imported object is no longer a `[hashtable]`.</span></span> <span data-ttu-id="aae8b-311">Het is nu a `[pscustomobject]` en dat kan problemen veroorzaken als u deze niet verwacht.</span><span class="sxs-lookup"><span data-stu-id="aae8b-311">It's now a `[pscustomobject]` and that can cause issues if you don't expect it.</span></span>

<span data-ttu-id="aae8b-312">Kijk voor een diep geneste hashtabellen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-312">Watch for deeply-nested hashtables.</span></span> <span data-ttu-id="aae8b-313">Wanneer u deze converteert naar JSON, worden de verwachte resultaten mogelijk niet weer geven.</span><span class="sxs-lookup"><span data-stu-id="aae8b-313">When you convert it to JSON you might not get the results you expect.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

<span data-ttu-id="aae8b-314">Gebruik de para meter **Depth** om ervoor te zorgen dat u alle geneste hashtabellen hebt uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="aae8b-314">Use **Depth** parameter to ensure that you have expanded all the nested hashtables.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

<span data-ttu-id="aae8b-315">Als u wilt dat deze bij het `[hashtable]` importeren moet worden, moet u de `Export-CliXml` opdrachten en gebruiken `Import-CliXml` .</span><span class="sxs-lookup"><span data-stu-id="aae8b-315">If you need it to be a `[hashtable]` on import, then you need to use the `Export-CliXml` and `Import-CliXml` commands.</span></span>

### <a name="converting-json-to-hashtable"></a><span data-ttu-id="aae8b-316">JSON converteren naar hashtabel</span><span class="sxs-lookup"><span data-stu-id="aae8b-316">Converting JSON to Hashtable</span></span>

<span data-ttu-id="aae8b-317">Als u JSON naar a moet converteren `[hashtable]` , is er een manier waarop u deze kunt doen met de [JavaScriptSerializer][] in .net.</span><span class="sxs-lookup"><span data-stu-id="aae8b-317">If you need to convert JSON to a `[hashtable]`, there's one way that I know of to do it with the [JavaScriptSerializer][] in .NET.</span></span>

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

<span data-ttu-id="aae8b-318">Vanaf Power shell V6 maakt JSON-ondersteuning gebruik van de Newton Soft-JSON.NET en voegt hashtabel-ondersteuning toe.</span><span class="sxs-lookup"><span data-stu-id="aae8b-318">Beginning in PowerShell v6, JSON support uses the NewtonSoft JSON.NET and adds hashtable support.</span></span>

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

<span data-ttu-id="aae8b-319">Power shell 6,2 heeft de **Depth** -para meter toegevoegd aan `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="aae8b-319">PowerShell 6.2 added the **Depth** parameter to `ConvertFrom-Json`.</span></span> <span data-ttu-id="aae8b-320">De standaard **diepte** is 1024.</span><span class="sxs-lookup"><span data-stu-id="aae8b-320">The default **Depth** is 1024.</span></span>

### <a name="reading-directly-from-a-file"></a><span data-ttu-id="aae8b-321">Rechtstreeks vanuit een bestand lezen</span><span class="sxs-lookup"><span data-stu-id="aae8b-321">Reading directly from a file</span></span>

<span data-ttu-id="aae8b-322">Als u een bestand hebt dat een hashtabel met een Power shell-syntaxis bevat, is het een manier om deze rechtstreeks te importeren.</span><span class="sxs-lookup"><span data-stu-id="aae8b-322">If you have a file that contains a hashtable using PowerShell syntax, there's a way to import it directly.</span></span>

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

<span data-ttu-id="aae8b-323">De inhoud van het bestand wordt geïmporteerd in een `scriptblock` , waarna wordt gecontroleerd of er geen andere Power shell-opdrachten aanwezig zijn voordat deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aae8b-323">It imports the contents of the file into a `scriptblock`, then checks to make sure it doesn't have any other PowerShell commands in it before it executes it.</span></span>

<span data-ttu-id="aae8b-324">Wist u dat een module manifest (het psd1-bestand) alleen een hashtabel is?</span><span class="sxs-lookup"><span data-stu-id="aae8b-324">On that note, did you know that a module manifest (the psd1 file) is just a hashtable?</span></span>

## <a name="keys-can-be-any-object"></a><span data-ttu-id="aae8b-325">Sleutels kunnen elk wille keurig object zijn</span><span class="sxs-lookup"><span data-stu-id="aae8b-325">Keys can be any object</span></span>

<span data-ttu-id="aae8b-326">De meeste tijd zijn de sleutels alleen uit teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-326">Most of the time, the keys are just strings.</span></span> <span data-ttu-id="aae8b-327">Daarom kunnen we aanhalings tekens maken en deze een eigen sleutel geven.</span><span class="sxs-lookup"><span data-stu-id="aae8b-327">So we can put quotes around anything and make it a key.</span></span>

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

<span data-ttu-id="aae8b-328">U kunt oneven dingen doen die u mogelijk niet hebt gerealiseerd.</span><span class="sxs-lookup"><span data-stu-id="aae8b-328">You can do some odd things that you may not have realized you could do.</span></span>

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

<span data-ttu-id="aae8b-329">Maar omdat u iets kunt doen, betekent dit niet dat u moet.</span><span class="sxs-lookup"><span data-stu-id="aae8b-329">Just because you can do something, it doesn't mean that you should.</span></span> <span data-ttu-id="aae8b-330">Het laatste lijkt erop dat er een fout is opgetreden die in de wacht staat en dat de code eenvoudig te begrijpen is.</span><span class="sxs-lookup"><span data-stu-id="aae8b-330">That last one just looks like a bug waiting to happen and would be easily misunderstood by anyone reading your code.</span></span>

<span data-ttu-id="aae8b-331">Technisch uw sleutel hoeft geen teken reeks te zijn, maar ze zijn gemakkelijker te zien als u alleen teken reeksen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-331">Technically your key doesn't have to be a string but they're easier to think about if you only use strings.</span></span> <span data-ttu-id="aae8b-332">Indexering werkt echter niet goed met de complexe sleutels.</span><span class="sxs-lookup"><span data-stu-id="aae8b-332">However, indexing doesn't work well with the complex keys.</span></span>

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

<span data-ttu-id="aae8b-333">Het is niet altijd mogelijk om een waarde in de hashtabel te openen met de bijbehorende sleutel.</span><span class="sxs-lookup"><span data-stu-id="aae8b-333">Accessing a value in the hashtable by its key doesn't always work.</span></span> <span data-ttu-id="aae8b-334">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="aae8b-334">For example:</span></span>

```powershell
$key = $ht.keys[0]
$ht.$($key)
a
$ht[$key]
a
```

<span data-ttu-id="aae8b-335">Wanneer de sleutel een matrix is, moet u de `$key` variabele in een subexpressie laten teruglopen zodat deze kan worden gebruikt met de notatie member Access ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="aae8b-335">When the key is an array, you must wrap the `$key` variable in a subexpression so that it can be used with member access (`.`) notation.</span></span> <span data-ttu-id="aae8b-336">U kunt ook de notatie matrix index ( `[]` ) gebruiken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-336">Or, you can use array index (`[]`) notation.</span></span>

## <a name="use-in-automatic-variables"></a><span data-ttu-id="aae8b-337">Gebruiken in automatische variabelen</span><span class="sxs-lookup"><span data-stu-id="aae8b-337">Use in automatic variables</span></span>

### <a name="psboundparameters"></a><span data-ttu-id="aae8b-338">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="aae8b-338">$PSBoundParameters</span></span>

<span data-ttu-id="aae8b-339">[$PSBoundParameters] [] is een automatische variabele die alleen in de context van een functie bestaat.</span><span class="sxs-lookup"><span data-stu-id="aae8b-339">[$PSBoundParameters][] is an automatic variable that only exists inside the context of a function.</span></span>
<span data-ttu-id="aae8b-340">Het bevat alle para meters waarmee de functie is aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-340">It contains all the parameters that the function was called with.</span></span> <span data-ttu-id="aae8b-341">Dit is niet precies een hashtabel, maar bijna genoeg zodat u deze kunt behandelen als één.</span><span class="sxs-lookup"><span data-stu-id="aae8b-341">This isn't exactly a hashtable but close enough that you can treat it like one.</span></span>

<span data-ttu-id="aae8b-342">Dit omvat het verwijderen van sleutels en het splatting aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="aae8b-342">That includes removing keys and splatting it to other functions.</span></span> <span data-ttu-id="aae8b-343">Als u een proxy functie hebt gevonden, kunt u deze beter bekijken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-343">If you find yourself writing proxy functions, take a closer look at this one.</span></span>

<span data-ttu-id="aae8b-344">Zie [about_Automatic_Variables][] voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aae8b-344">See [about_Automatic_Variables][] for more details.</span></span>

### <a name="psboundparameters-gotcha"></a><span data-ttu-id="aae8b-345">PSBoundParameters gotcha</span><span class="sxs-lookup"><span data-stu-id="aae8b-345">PSBoundParameters gotcha</span></span>

<span data-ttu-id="aae8b-346">Een belang rijke ding die u moet onthouden is dat dit alleen de waarden bevat die worden door gegeven als para meters.</span><span class="sxs-lookup"><span data-stu-id="aae8b-346">One important thing to remember is that this only includes the values that are passed in as parameters.</span></span> <span data-ttu-id="aae8b-347">Als u ook para meters met standaard waarden hebt, maar deze niet worden door gegeven door de aanroeper, `$PSBoundParameters` bevatten deze waarden niet.</span><span class="sxs-lookup"><span data-stu-id="aae8b-347">If you also have parameters with default values but aren't passed in by the caller, `$PSBoundParameters` doesn't contain those values.</span></span> <span data-ttu-id="aae8b-348">Dit wordt meestal gezien.</span><span class="sxs-lookup"><span data-stu-id="aae8b-348">This is commonly overlooked.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="aae8b-349">$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="aae8b-349">$PSDefaultParameterValues</span></span>

<span data-ttu-id="aae8b-350">Met deze automatische variabele kunt u standaard waarden toewijzen aan elke cmdlet zonder de cmdlet te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-350">This automatic variable lets you assign default values to any cmdlet without changing the cmdlet.</span></span>
<span data-ttu-id="aae8b-351">Bekijk dit voor beeld.</span><span class="sxs-lookup"><span data-stu-id="aae8b-351">Take a look at this example.</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

<span data-ttu-id="aae8b-352">Hiermee voegt u een vermelding toe aan de `$PSDefaultParameterValues` hashtabel die wordt ingesteld `UTF8` als de standaard waarde voor de `Out-File -Encoding` para meter.</span><span class="sxs-lookup"><span data-stu-id="aae8b-352">This adds an entry to the `$PSDefaultParameterValues` hashtable that sets `UTF8` as the default value for the `Out-File -Encoding` parameter.</span></span> <span data-ttu-id="aae8b-353">Dit is een specifieke sessie, zodat u deze in uw kunt plaatsen `$profile` .</span><span class="sxs-lookup"><span data-stu-id="aae8b-353">This is session-specific so you should place it in your `$profile`.</span></span>

<span data-ttu-id="aae8b-354">Ik gebruik dit regel matig om waarden vooraf toe te wijzen die ik regel matig Typ.</span><span class="sxs-lookup"><span data-stu-id="aae8b-354">I use this often to pre-assign values that I type quite often.</span></span>

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

<span data-ttu-id="aae8b-355">Er worden ook joker tekens geaccepteerd zodat u waarden in bulk kunt instellen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-355">This also accepts wildcards so you can set values in bulk.</span></span> <span data-ttu-id="aae8b-356">Hier volgen enkele manieren waarop u deze kunt gebruiken:</span><span class="sxs-lookup"><span data-stu-id="aae8b-356">Here are some ways you can use that:</span></span>

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

<span data-ttu-id="aae8b-357">Zie dit fantastische artikel over [automatische standaard instellingen][] door [Michael Sorens][]voor een uitgebreidere uitsplitsing.</span><span class="sxs-lookup"><span data-stu-id="aae8b-357">For a more in-depth breakdown, see this great article on [Automatic Defaults][] by [Michael Sorens][].</span></span>

## <a name="regex-matches"></a><span data-ttu-id="aae8b-358">Regex $Matches</span><span class="sxs-lookup"><span data-stu-id="aae8b-358">Regex $Matches</span></span>

<span data-ttu-id="aae8b-359">Wanneer u de `-match` operator gebruikt, wordt een automatische variabele `$matches` met de naam gemaakt met de resultaten van de overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="aae8b-359">When you use the `-match` operator, an automatic variable called `$matches` is created with the results of the match.</span></span> <span data-ttu-id="aae8b-360">Als u sub-expressies in uw regex hebt, worden deze subtreffers ook weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aae8b-360">If you have any sub expressions in your regex, those sub matches are also listed.</span></span>

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a><span data-ttu-id="aae8b-361">Benoemde overeenkomsten</span><span class="sxs-lookup"><span data-stu-id="aae8b-361">Named matches</span></span>

<span data-ttu-id="aae8b-362">Dit is een van mijn favoriete functies die de meeste mensen niet kennen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-362">This is one of my favorite features that most people don't know about.</span></span> <span data-ttu-id="aae8b-363">Als u een benoemde regex match gebruikt, hebt u toegang tot die overeenkomst op naam op basis van de overeenkomsten.</span><span class="sxs-lookup"><span data-stu-id="aae8b-363">If you use a named regex match, then you can access that match by name on the matches.</span></span>

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

<span data-ttu-id="aae8b-364">In het bovenstaande voor beeld `(?<Name>.*)` is de een benoemde subexpression.</span><span class="sxs-lookup"><span data-stu-id="aae8b-364">In the example above, the `(?<Name>.*)` is a named sub expression.</span></span> <span data-ttu-id="aae8b-365">Deze waarde wordt vervolgens in de `$Matches.Name` eigenschap geplaatst.</span><span class="sxs-lookup"><span data-stu-id="aae8b-365">This value is then placed in the `$Matches.Name` property.</span></span>

## <a name="group-object--ashashtable"></a><span data-ttu-id="aae8b-366">Group-Object-AsHashtable</span><span class="sxs-lookup"><span data-stu-id="aae8b-366">Group-Object -AsHashtable</span></span>

<span data-ttu-id="aae8b-367">Een weinig bekende functie van `Group-Object` is dat deze gegevens sets kan omzetten in een hashtabel voor u.</span><span class="sxs-lookup"><span data-stu-id="aae8b-367">One little known feature of `Group-Object` is that it can turn some datasets into a hashtable for you.</span></span>

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

<span data-ttu-id="aae8b-368">Hiermee wordt elke rij toegevoegd aan een hashtabel en wordt de opgegeven eigenschap gebruikt als de sleutel voor toegang tot de tabel.</span><span class="sxs-lookup"><span data-stu-id="aae8b-368">This will add each row into a hashtable and use the specified property as the key to access it.</span></span>

## <a name="copying-hashtables"></a><span data-ttu-id="aae8b-369">Hashtabellen kopiëren</span><span class="sxs-lookup"><span data-stu-id="aae8b-369">Copying Hashtables</span></span>

<span data-ttu-id="aae8b-370">Een belang rijke ding die u moet weten, is dat hashtabellen objecten zijn.</span><span class="sxs-lookup"><span data-stu-id="aae8b-370">One important thing to know is that hashtables are objects.</span></span> <span data-ttu-id="aae8b-371">En elke variabele is alleen een verwijzing naar een object.</span><span class="sxs-lookup"><span data-stu-id="aae8b-371">And each variable is just a reference to an object.</span></span> <span data-ttu-id="aae8b-372">Dit betekent dat het meer werk nodig heeft om een geldige kopie van een hashtabel te maken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-372">This means that it takes more work to make a valid copy of a hashtable.</span></span>

### <a name="assigning-reference-types"></a><span data-ttu-id="aae8b-373">Verwijzings typen toewijzen</span><span class="sxs-lookup"><span data-stu-id="aae8b-373">Assigning reference types</span></span>

<span data-ttu-id="aae8b-374">Wanneer u één hashtabel hebt en deze toewijst aan een tweede variabele, wijzen beide variabelen naar dezelfde hashtabel.</span><span class="sxs-lookup"><span data-stu-id="aae8b-374">When you have one hashtable and assign it to a second variable, both variables point to the same hashtable.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="aae8b-375">Dit markeert dat ze hetzelfde zijn omdat het wijzigen van de waarden in een ook de waarden in de andere wijzigt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-375">This highlights that they're the same because altering the values in one will also alter the values in the other.</span></span> <span data-ttu-id="aae8b-376">Dit geldt ook voor het door geven van hashtabellen in andere functies.</span><span class="sxs-lookup"><span data-stu-id="aae8b-376">This also applies when passing hashtables into other functions.</span></span> <span data-ttu-id="aae8b-377">Als deze functies wijzigingen aanbrengen in de hashtabel, wordt het origineel ook gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="aae8b-377">If those functions make changes to that hashtable, your original is also altered.</span></span>

### <a name="shallow-copies-single-level"></a><span data-ttu-id="aae8b-378">Recente kopieën, één niveau</span><span class="sxs-lookup"><span data-stu-id="aae8b-378">Shallow copies, single level</span></span>

<span data-ttu-id="aae8b-379">Als we een eenvoudige hashtabel hebben, zoals in het bovenstaande voor beeld, kunnen we gebruiken om een inkomend `.Clone()` exemplaar te maken.</span><span class="sxs-lookup"><span data-stu-id="aae8b-379">If we have a simple hashtable like our example above, we can use `.Clone()` to make a shallow copy.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

<span data-ttu-id="aae8b-380">Hierdoor kunnen we enkele eenvoudige wijzigingen aanbrengen die niet van invloed zijn op de andere.</span><span class="sxs-lookup"><span data-stu-id="aae8b-380">This will allow us to make some basic changes to one that don't impact the other.</span></span>

### <a name="shallow-copies-nested"></a><span data-ttu-id="aae8b-381">Recente kopieën, genest</span><span class="sxs-lookup"><span data-stu-id="aae8b-381">Shallow copies, nested</span></span>

<span data-ttu-id="aae8b-382">De reden waarom het een begrootte kopie wordt genoemd, is dat alleen de eigenschappen van het basis niveau worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="aae8b-382">The reason why it's called a shallow copy is because it only copies the base level properties.</span></span> <span data-ttu-id="aae8b-383">Als een van deze eigenschappen een verwijzings type is (zoals een andere hashtabel), zullen die geneste objecten nog steeds naar elkaar wijzen.</span><span class="sxs-lookup"><span data-stu-id="aae8b-383">If one of those properties is a reference type (like another hashtable), then those nested objects will still point to each other.</span></span>

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="aae8b-384">Zo kunt u zien dat hoewel de hashtabel is gekloond, de verwijzing naar niet is `person` gekloond.</span><span class="sxs-lookup"><span data-stu-id="aae8b-384">So you can see that even though I cloned the hashtable, the reference to `person` wasn't cloned.</span></span> <span data-ttu-id="aae8b-385">We moeten een diepe kopie maken om echt een tweede hashtabel te hebben die niet is gekoppeld aan de eerste.</span><span class="sxs-lookup"><span data-stu-id="aae8b-385">We need to make a deep copy to truly have a second hashtable that isn't linked to the first.</span></span>

### <a name="deep-copies"></a><span data-ttu-id="aae8b-386">Uitgebreide kopieën</span><span class="sxs-lookup"><span data-stu-id="aae8b-386">Deep copies</span></span>

<span data-ttu-id="aae8b-387">Er zijn een aantal manieren om een diepe kopie van een hashtabel te maken (en deze als hash-tabel te gebruiken).</span><span class="sxs-lookup"><span data-stu-id="aae8b-387">There are a couple of ways to make a deep copy of a hashtable (and keep it as a hashtable).</span></span> <span data-ttu-id="aae8b-388">Hier volgt een functie voor het recursief maken van een diepe kopie met behulp van Power shell:</span><span class="sxs-lookup"><span data-stu-id="aae8b-388">Here's a function using PowerShell to recursively create a deep copy:</span></span>

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

<span data-ttu-id="aae8b-389">Er worden geen andere verwijzings typen of-matrices verwerkt, maar dit is een goed uitgangs punt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-389">It doesn't handle any other reference types or arrays, but it's a good starting point.</span></span>

<span data-ttu-id="aae8b-390">Een andere manier is om .net te gebruiken om deze te deserialiseren met **CliXml** zoals in deze functie:</span><span class="sxs-lookup"><span data-stu-id="aae8b-390">Another way is to use .Net to deserialize it using **CliXml** like in this function:</span></span>

```powershell
function Get-DeepClone
{
    param(
        $InputObject
    )
    $TempCliXmlString = [System.Management.Automation.PSSerializer]::Serialize($obj, [int32]::MaxValue)
    return [System.Management.Automation.PSSerializer]::Deserialize($TempCliXmlString)
}
```

<span data-ttu-id="aae8b-391">Voor extreem grote hashtabellen is de deserialisatie functie sneller wanneer deze wordt geschaald. Er zijn echter enkele zaken waarmee u rekening moet houden wanneer u deze methode gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-391">For extremely large hashtables, the deserializing function is faster as it scales out. However, there are some things to consider when using this method.</span></span> <span data-ttu-id="aae8b-392">Aangezien **CliXml** wordt gebruikt, is het geheugen intensief en als u grote hashtabellen klont, kan dit een probleem zijn.</span><span class="sxs-lookup"><span data-stu-id="aae8b-392">Since it uses **CliXml**, it's memory intensive and if you are cloning huge hashtables, that might be a problem.</span></span> <span data-ttu-id="aae8b-393">Een andere beperking van de **CliXml** is een diepte limiet van 48.</span><span class="sxs-lookup"><span data-stu-id="aae8b-393">Another limitation of the **CliXml** is there is a depth limitation of 48.</span></span> <span data-ttu-id="aae8b-394">Als u een hashtabel met 48 lagen van geneste hashtabellen hebt, mislukt het klonen en wordt er helemaal geen hash-uitvoer uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aae8b-394">Meaning, if you have a hashtable with 48 layers of nested hashtables, the cloning will fail and no hashtable will be output at all.</span></span>

## <a name="anything-else"></a><span data-ttu-id="aae8b-395">Nog iets?</span><span class="sxs-lookup"><span data-stu-id="aae8b-395">Anything else?</span></span>

<span data-ttu-id="aae8b-396">Ik heb veel moeite gedekt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-396">I covered a lot of ground quickly.</span></span> <span data-ttu-id="aae8b-397">Ik hoop dat u er geen zorgen meer meer over hebt, of dat u deze beter kunt zien wanneer u dit leest.</span><span class="sxs-lookup"><span data-stu-id="aae8b-397">My hope is that you walk away leaning something new or understanding it better every time you read this.</span></span> <span data-ttu-id="aae8b-398">Omdat ik het volledige spectrum van deze functie heb gezien, zijn er aspecten die alleen op u nu mogelijk niet van toepassing zijn.</span><span class="sxs-lookup"><span data-stu-id="aae8b-398">Because I covered the full spectrum of this feature, there are aspects that just may not apply to you right now.</span></span> <span data-ttu-id="aae8b-399">Dat is heel goed en de verwachte soort is afhankelijk van hoeveel u met Power shell werkt.</span><span class="sxs-lookup"><span data-stu-id="aae8b-399">That is perfectly OK and is kind of expected depending on how much you work with PowerShell.</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[original version]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[hashtabellen]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[hashtables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[matrices]: /powershell/module/microsoft.powershell.core/about/about_arrays
[arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Als u prestatie problemen hebt, test u deze]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[If performance matters, test it]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8&preserve-view=true
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[Automatische standaard waarden]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Automatic Defaults]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
