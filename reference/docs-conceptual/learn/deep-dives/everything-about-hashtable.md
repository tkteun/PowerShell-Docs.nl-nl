---
title: Alles wat u wilt weten over hashtabellen
description: Hashtabellen zijn heel belang rijk in Power shell, zodat het goed is om een duidelijker beeld te krijgen.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 60a5172485b9caf6343f54194563cd048648206e
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149857"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a><span data-ttu-id="da19e-103">Alles wat u wilt weten over hashtabellen</span><span class="sxs-lookup"><span data-stu-id="da19e-103">Everything you wanted to know about hashtables</span></span>

<span data-ttu-id="da19e-104">Ik wil een stap terugnemen en praten over [hashtabellen][].</span><span class="sxs-lookup"><span data-stu-id="da19e-104">I want to take a step back and talk about [hashtables][].</span></span> <span data-ttu-id="da19e-105">Ik gebruik deze nu altijd.</span><span class="sxs-lookup"><span data-stu-id="da19e-105">I use them all the time now.</span></span> <span data-ttu-id="da19e-106">Ik ben van de afgelopen avond een studie over de gebruikers groep, en ik heb een andere uitverwar ring gehad over hen.</span><span class="sxs-lookup"><span data-stu-id="da19e-106">I was teaching someone about them after our user group meeting last night and I realized I had the same confusion about them as he had.</span></span> <span data-ttu-id="da19e-107">Hashtabellen zijn heel belang rijk in Power shell, zodat het goed is om een duidelijker beeld te krijgen.</span><span class="sxs-lookup"><span data-stu-id="da19e-107">Hashtables are really important in PowerShell so it's good to have a solid understanding of them.</span></span>

> [!NOTE]
> <span data-ttu-id="da19e-108">De [oorspronkelijke versie][] van dit artikel is gepubliceerd op de blog geschreven door [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="da19e-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="da19e-109">Het Power shell-team hartelijk dank voor het delen van deze inhoud met ons.</span><span class="sxs-lookup"><span data-stu-id="da19e-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="da19e-110">Raadpleeg zijn blog op [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="da19e-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="hashtable-as-a-collection-of-things"></a><span data-ttu-id="da19e-111">Hashtabel als een verzameling dingen</span><span class="sxs-lookup"><span data-stu-id="da19e-111">Hashtable as a collection of things</span></span>

<span data-ttu-id="da19e-112">Ik wil dat u eerst een **hashtabel** als een verzameling in de traditionele definitie van een hashtabel ziet.</span><span class="sxs-lookup"><span data-stu-id="da19e-112">I want you to first see a **Hashtable** as a collection in the traditional definition of a hashtable.</span></span> <span data-ttu-id="da19e-113">Deze definitie biedt u een basis kennis van hoe ze werken wanneer ze later worden gebruikt voor meer geavanceerde dingen.</span><span class="sxs-lookup"><span data-stu-id="da19e-113">This definition gives you a fundamental understanding of how they work when they get used for more advanced stuff later.</span></span> <span data-ttu-id="da19e-114">Het overs laan van deze inzichten is vaak een bron van Verwar ring.</span><span class="sxs-lookup"><span data-stu-id="da19e-114">Skipping this understanding is often a source of confusion.</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="da19e-115">Wat is een matrix?</span><span class="sxs-lookup"><span data-stu-id="da19e-115">What is an array?</span></span>

<span data-ttu-id="da19e-116">Voordat ik naar wat een **hashtabel** gaat, moet ik eerst de [matrixen][] vermelden.</span><span class="sxs-lookup"><span data-stu-id="da19e-116">Before I jump into what a **Hashtable** is, I need to mention [arrays][] first.</span></span> <span data-ttu-id="da19e-117">Voor het doel van deze discussie is een matrix een lijst of verzameling waarden of objecten.</span><span class="sxs-lookup"><span data-stu-id="da19e-117">For the purpose of this discussion, an array is a list or collection of values or objects.</span></span>

```powershell
$array = @(1,2,3,5,7,11)
```

<span data-ttu-id="da19e-118">Zodra u uw items in een matrix hebt, kunt u gebruiken `foreach` om de lijst te herhalen of een index te gebruiken voor toegang tot afzonderlijke elementen in de matrix.</span><span class="sxs-lookup"><span data-stu-id="da19e-118">Once you have your items into an array, you can either use `foreach` to iterate over the list or use an index to access individual elements in the array.</span></span>

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

<span data-ttu-id="da19e-119">Op dezelfde manier kunt u ook waarden bijwerken met behulp van een index.</span><span class="sxs-lookup"><span data-stu-id="da19e-119">You can also update values using an index in the same way.</span></span>

```powershell
$array[2] = 13
```

<span data-ttu-id="da19e-120">Ik heb gewoon het Opper vlak op matrices kwijt, maar dat zou ze in de juiste context moeten zetten terwijl ik op hashtabellen ga.</span><span class="sxs-lookup"><span data-stu-id="da19e-120">I just scratched the surface on arrays but that should put them into the right context as I move onto hashtables.</span></span>

## <a name="what-is-a-hashtable"></a><span data-ttu-id="da19e-121">Wat is een hashtabel?</span><span class="sxs-lookup"><span data-stu-id="da19e-121">What is a hashtable?</span></span>

<span data-ttu-id="da19e-122">Ik ga aan de slag met een eenvoudige technische beschrijving van wat hashtabellen in het algemeen zinvol zijn, voordat ik de andere manieren in Power shell gebruik.</span><span class="sxs-lookup"><span data-stu-id="da19e-122">I'm going to start with a basic technical description of what hashtables are, in the general sense, before I shift into the other ways PowerShell uses them.</span></span>

<span data-ttu-id="da19e-123">Een hashtabel is een gegevens structuur die vergelijkbaar is met een matrix, behalve dat u elke waarde (object) opslaat met behulp van een sleutel.</span><span class="sxs-lookup"><span data-stu-id="da19e-123">A hashtable is a data structure, much like an array, except you store each value (object) using a key.</span></span> <span data-ttu-id="da19e-124">Het is een basis sleutel/waarde-archief.</span><span class="sxs-lookup"><span data-stu-id="da19e-124">It's a basic key/value store.</span></span> <span data-ttu-id="da19e-125">Eerst maken we een lege hashtabel.</span><span class="sxs-lookup"><span data-stu-id="da19e-125">First, we create an empty hashtable.</span></span>

```powershell
$ageList = @{}
```

<span data-ttu-id="da19e-126">U ziet dat accolades in plaats van haakjes worden gebruikt voor het definiëren van een hashtabel.</span><span class="sxs-lookup"><span data-stu-id="da19e-126">Notice that braces, instead of parentheses, are used to define a hashtable.</span></span> <span data-ttu-id="da19e-127">Vervolgens voegen we een item toe met behulp van een sleutel als volgt:</span><span class="sxs-lookup"><span data-stu-id="da19e-127">Then we add an item using a key like this:</span></span>

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

<span data-ttu-id="da19e-128">De naam van de persoon is de sleutel en de leeftijd is de waarde die ik wil opslaan.</span><span class="sxs-lookup"><span data-stu-id="da19e-128">The person's name is the key and their age is the value that I want to save.</span></span>

## <a name="using-the-brackets-for-access"></a><span data-ttu-id="da19e-129">De vier Kante haken gebruiken voor toegang</span><span class="sxs-lookup"><span data-stu-id="da19e-129">Using the brackets for access</span></span>

<span data-ttu-id="da19e-130">Zodra u uw waarden aan de hashtabel hebt toegevoegd, kunt u ze weer gebruiken met dezelfde sleutel (in plaats van een numerieke index zoals u voor een matrix zou gebruiken).</span><span class="sxs-lookup"><span data-stu-id="da19e-130">Once you add your values to the hashtable, you can pull them back out using that same key (instead of using a numeric index like you would have for an array).</span></span>

```powershell
$ageList['Kevin']
$ageList['Alex']
```

<span data-ttu-id="da19e-131">Wanneer ik de leeftijd van Kevin wil, gebruik ik dan de naam ervan om deze te openen.</span><span class="sxs-lookup"><span data-stu-id="da19e-131">When I want Kevin's age, I use his name to access it.</span></span> <span data-ttu-id="da19e-132">U kunt deze methode gebruiken om ook waarden toe te voegen of bij te werken in de hashtabel.</span><span class="sxs-lookup"><span data-stu-id="da19e-132">We can use this approach to add or update values into the hashtable too.</span></span> <span data-ttu-id="da19e-133">Dit is net als het gebruik van de `add()` bovenstaande functie.</span><span class="sxs-lookup"><span data-stu-id="da19e-133">This is just like using the `add()` function above.</span></span>

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

<span data-ttu-id="da19e-134">Er is een andere syntaxis die u kunt gebruiken voor toegang tot en het bijwerken van waarden die ik in een latere sectie bevindt.</span><span class="sxs-lookup"><span data-stu-id="da19e-134">There's another syntax you can use for accessing and updating values that I'll cover in a later section.</span></span> <span data-ttu-id="da19e-135">Als u vanuit een andere taal naar Power shell gaat, moeten deze voor beelden passen in met de manier waarop u hashtabellen al eerder hebt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="da19e-135">If you're coming to PowerShell from another language, these examples should fit in with how you may have used hashtables before.</span></span>

### <a name="creating-hashtables-with-values"></a><span data-ttu-id="da19e-136">Hashtabellen maken met waarden</span><span class="sxs-lookup"><span data-stu-id="da19e-136">Creating hashtables with values</span></span>

<span data-ttu-id="da19e-137">Tot nu toe heb ik een lege hashtabel gemaakt voor deze voor beelden.</span><span class="sxs-lookup"><span data-stu-id="da19e-137">So far I've created an empty hashtable for these examples.</span></span> <span data-ttu-id="da19e-138">U kunt de sleutels en waarden vooraf invullen wanneer u ze maakt.</span><span class="sxs-lookup"><span data-stu-id="da19e-138">You can pre-populate the keys and values when you create them.</span></span>

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a><span data-ttu-id="da19e-139">Als opzoek tabel</span><span class="sxs-lookup"><span data-stu-id="da19e-139">As a lookup table</span></span>

<span data-ttu-id="da19e-140">De werkelijke waarde van dit type van een hashtabel is dat u ze als opzoek tabel kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="da19e-140">The real value of this type of a hashtable is that you can use them as a lookup table.</span></span> <span data-ttu-id="da19e-141">Hier volgt een eenvoudig voor beeld.</span><span class="sxs-lookup"><span data-stu-id="da19e-141">Here is a simple example.</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

<span data-ttu-id="da19e-142">In dit voor beeld geeft u een omgeving voor de `$env` variabele op en wordt de juiste server gekozen.</span><span class="sxs-lookup"><span data-stu-id="da19e-142">In this example, you specify an environment for the `$env` variable and it will pick the correct server.</span></span> <span data-ttu-id="da19e-143">U kunt een `switch($env){...}` voor een selectie zoals deze gebruiken, maar een hashtabel is een mooie optie.</span><span class="sxs-lookup"><span data-stu-id="da19e-143">You could use a `switch($env){...}` for a selection like this but a hashtable is a nice option.</span></span>

<span data-ttu-id="da19e-144">Dit wordt nog beter wanneer u de opzoek tabel dynamisch bouwt om deze later te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="da19e-144">This gets even better when you dynamically build the lookup table to use it later.</span></span> <span data-ttu-id="da19e-145">Denk dus na over het gebruik van deze aanpak wanneer u naar iets moet verwijzen.</span><span class="sxs-lookup"><span data-stu-id="da19e-145">So think about using this approach when you need to cross reference something.</span></span> <span data-ttu-id="da19e-146">Ik denk dat dit zelfs meer zou worden weer gegeven als Power shell niet zo goed kan worden gefilterd op de pipe met `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="da19e-146">I think we would see this even more if PowerShell wasn't so good at filtering on the pipe with `Where-Object`.</span></span> <span data-ttu-id="da19e-147">Als u ooit een situatie hebt waarbij de prestaties van belang zijn, moet u rekening houden met deze aanpak.</span><span class="sxs-lookup"><span data-stu-id="da19e-147">If you're ever in a situation where performance matters, this approach needs to be considered.</span></span>

<span data-ttu-id="da19e-148">Ik zeg niet dat het sneller is, maar wel in het geval van [prestatie][]problemen.</span><span class="sxs-lookup"><span data-stu-id="da19e-148">I won't say that it's faster, but it does fit into the rule of [If performance matters, test it][].</span></span>

#### <a name="multiselection"></a><span data-ttu-id="da19e-149">Multiselectie</span><span class="sxs-lookup"><span data-stu-id="da19e-149">Multiselection</span></span>

<span data-ttu-id="da19e-150">Over het algemeen kunt u een hashtabel beschouwen als een sleutel/waarde-paar, waarbij u één sleutel opgeeft en één waarde ophaalt.</span><span class="sxs-lookup"><span data-stu-id="da19e-150">Generally, you think of a hashtable as a key/value pair, where you provide one key and get one value.</span></span> <span data-ttu-id="da19e-151">Met Power shell kunt u een matrix met sleutels opgeven om meerdere waarden te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="da19e-151">PowerShell allows you to provide an array of keys to get multiple values.</span></span>

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

<span data-ttu-id="da19e-152">In dit voor beeld gebruiken we dezelfde overeenkomende hashtabel en bieden ze drie verschillende matrix stijlen om de overeenkomsten op te halen.</span><span class="sxs-lookup"><span data-stu-id="da19e-152">In this example, I use the same lookup hashtable from above and provide three different array styles to get the matches.</span></span> <span data-ttu-id="da19e-153">Dit is een verborgen edelsteen in Power shell waarmee de meeste mensen niet op de hoogte zijn.</span><span class="sxs-lookup"><span data-stu-id="da19e-153">This is a hidden gem in PowerShell that most people aren't aware of.</span></span>

## <a name="iterating-hashtables"></a><span data-ttu-id="da19e-154">Hashtabellen herhalen</span><span class="sxs-lookup"><span data-stu-id="da19e-154">Iterating hashtables</span></span>

<span data-ttu-id="da19e-155">Omdat een hashtabel bestaat uit een verzameling sleutel-waardeparen, voert u een andere sequentie in dan die voor een matrix of een normale lijst met items.</span><span class="sxs-lookup"><span data-stu-id="da19e-155">Because a hashtable is a collection of key/value pairs, you iterate over it differently than you do for an array or a normal list of items.</span></span>

<span data-ttu-id="da19e-156">Het eerste dat u moet nadoen, is dat als u de hashtabel bewaart, de pipe als één object beschouwt.</span><span class="sxs-lookup"><span data-stu-id="da19e-156">The first thing to notice is that if you pipe your hashtable, the pipe treats it like one object.</span></span>

```powershell
PS> $ageList | Measure-Object
count : 1
```

<span data-ttu-id="da19e-157">Hoewel de `.count` eigenschap vertelt u hoeveel waarden deze bevat.</span><span class="sxs-lookup"><span data-stu-id="da19e-157">Even though the `.count` property tells you how many values it contains.</span></span>

```powershell
PS> $ageList.count
2
```

<span data-ttu-id="da19e-158">U kunt dit probleem omzeilen door de `.values` eigenschap te gebruiken als u alleen de waarden hoeft op te geven.</span><span class="sxs-lookup"><span data-stu-id="da19e-158">You get around this issue by using the `.values` property if all you need is just the values.</span></span>

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

<span data-ttu-id="da19e-159">Het is vaak handiger om de sleutels te inventariseren en gebruiken om toegang te krijgen tot de waarden.</span><span class="sxs-lookup"><span data-stu-id="da19e-159">It's often more useful to enumerate the keys and use them to access the values.</span></span>

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

<span data-ttu-id="da19e-160">Hier volgt een voor beeld met een `foreach(){...}` lus.</span><span class="sxs-lookup"><span data-stu-id="da19e-160">Here is the same example with a `foreach(){...}` loop.</span></span>

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

<span data-ttu-id="da19e-161">Elke sleutel in de hashtabel wordt door lopen en vervolgens gebruikt om toegang te krijgen tot de waarde.</span><span class="sxs-lookup"><span data-stu-id="da19e-161">We are walking each key in the hashtable and then using it to access the value.</span></span> <span data-ttu-id="da19e-162">Dit is een algemeen patroon wanneer u met hashtabellen werkt als een verzameling.</span><span class="sxs-lookup"><span data-stu-id="da19e-162">This is a common pattern when working with hashtables as a collection.</span></span>

### <a name="getenumerator"></a><span data-ttu-id="da19e-163">GetEnumerator ()</span><span class="sxs-lookup"><span data-stu-id="da19e-163">GetEnumerator()</span></span>

<span data-ttu-id="da19e-164">Dit zorgt ervoor dat we de `GetEnumerator()` hashtabel kunnen herhalen.</span><span class="sxs-lookup"><span data-stu-id="da19e-164">That brings us to `GetEnumerator()` for iterating over our hashtable.</span></span>

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

<span data-ttu-id="da19e-165">De enumerator geeft u elk sleutel/waarde-paar op één na andere.</span><span class="sxs-lookup"><span data-stu-id="da19e-165">The enumerator gives you each key/value pair one after another.</span></span> <span data-ttu-id="da19e-166">Het is specifiek ontworpen voor deze use-case.</span><span class="sxs-lookup"><span data-stu-id="da19e-166">It was designed specifically for this use case.</span></span> <span data-ttu-id="da19e-167">Hartelijk dank dat u [Kraus markeert](https://get-PowerShellblog.blogspot.com) om dit te onthouden.</span><span class="sxs-lookup"><span data-stu-id="da19e-167">Thank you to [Mark Kraus](https://get-PowerShellblog.blogspot.com) for reminding me of this one.</span></span>

### <a name="badenumeration"></a><span data-ttu-id="da19e-168">BadEnumeration</span><span class="sxs-lookup"><span data-stu-id="da19e-168">BadEnumeration</span></span>

<span data-ttu-id="da19e-169">Een van de belang rijke details is dat u een hashtabel niet kunt wijzigen tijdens het inventariseren.</span><span class="sxs-lookup"><span data-stu-id="da19e-169">One important detail is that you can't modify a hashtable while it's being enumerated.</span></span> <span data-ttu-id="da19e-170">Als we beginnen met het basis `$environments` voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="da19e-170">If we start with our basic `$environments` example:</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

<span data-ttu-id="da19e-171">En het instellen van elke sleutel op dezelfde server waarde mislukt.</span><span class="sxs-lookup"><span data-stu-id="da19e-171">And trying to set every key to the same server value fails.</span></span>

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

<span data-ttu-id="da19e-172">Dit kan ook gebeuren, zelfs als het lijkt alsof het ook goed is:</span><span class="sxs-lookup"><span data-stu-id="da19e-172">This will also fail even though it looks like it should also be fine:</span></span>

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

<span data-ttu-id="da19e-173">De truc van deze situatie is het klonen van de sleutels voordat u de inventarisatie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="da19e-173">The trick to this situation is to clone the keys before doing the enumeration.</span></span>

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a><span data-ttu-id="da19e-174">Hashtabel als een verzameling eigenschappen</span><span class="sxs-lookup"><span data-stu-id="da19e-174">Hashtable as a collection of properties</span></span>

<span data-ttu-id="da19e-175">Tot nu toe was het type van de objecten die we in onze hashtabel hebben geplaatst, allemaal hetzelfde type object.</span><span class="sxs-lookup"><span data-stu-id="da19e-175">So far the type of objects we placed in our hashtable were all the same type of object.</span></span> <span data-ttu-id="da19e-176">Ik heb in al deze voor beelden leeftijden gebruikt en de sleutel is de naam van de persoon.</span><span class="sxs-lookup"><span data-stu-id="da19e-176">I used ages in all those examples and the key was the person's name.</span></span> <span data-ttu-id="da19e-177">Dit is een uitstekende manier om ernaar te kijken wanneer uw verzameling objecten elk een naam heeft.</span><span class="sxs-lookup"><span data-stu-id="da19e-177">This is a great way to look at it when your collection of objects each have a name.</span></span> <span data-ttu-id="da19e-178">Een andere gang bare manier om hashtabellen te gebruiken in Power shell is een verzameling eigenschappen te bewaren waarbij de sleutel de naam van de eigenschap is.</span><span class="sxs-lookup"><span data-stu-id="da19e-178">Another common way to use hashtables in PowerShell is to hold a collection of properties where the key is the name of the property.</span></span> <span data-ttu-id="da19e-179">Ik Step Into dat idee in dit volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="da19e-179">I'll step into that idea in this next example.</span></span>

### <a name="property-based-access"></a><span data-ttu-id="da19e-180">Toegang op basis van eigenschappen</span><span class="sxs-lookup"><span data-stu-id="da19e-180">Property-based access</span></span>

<span data-ttu-id="da19e-181">Het gebruik van op eigenschappen gebaseerde toegang wijzigt de dynamiek van hashtabellen en hoe u deze kunt gebruiken in Power shell.</span><span class="sxs-lookup"><span data-stu-id="da19e-181">The use of property-based access changes the dynamics of hashtables and how you can use them in PowerShell.</span></span> <span data-ttu-id="da19e-182">Hieronder ziet u een voor beeld van de bovenstaande sleutels als eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="da19e-182">Here is our usual example from above treating the keys as properties.</span></span>

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

<span data-ttu-id="da19e-183">Net als in de bovenstaande voor beelden voegt u in dit voor beeld deze sleutels toe als ze al in de hashtabel aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="da19e-183">Just like the examples above, this example adds those keys if they don't exist in the hashtable already.</span></span> <span data-ttu-id="da19e-184">Afhankelijk van hoe u uw sleutels hebt gedefinieerd en wat uw waarden zijn, is dit een beetje vreemde of een perfecte keuze.</span><span class="sxs-lookup"><span data-stu-id="da19e-184">Depending on how you defined your keys and what your values are, this is either a little strange or a perfect fit.</span></span> <span data-ttu-id="da19e-185">Het voor beeld van de leeftijds lijst is tot dit punt goed gewerkt.</span><span class="sxs-lookup"><span data-stu-id="da19e-185">The age list example has worked great up until this point.</span></span> <span data-ttu-id="da19e-186">We hebben een nieuw voor beeld nodig om aan de slag te gaan.</span><span class="sxs-lookup"><span data-stu-id="da19e-186">We need a new example for this to feel right going forward.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="da19e-187">En we kunnen op deze manier kenmerken toevoegen en er toegang toe krijgen `$person` .</span><span class="sxs-lookup"><span data-stu-id="da19e-187">And we can add and access attributes on the `$person` like this.</span></span>

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

<span data-ttu-id="da19e-188">Het enige wat een plotselinge hash van deze hashtabel is, lijkt een object te zijn.</span><span class="sxs-lookup"><span data-stu-id="da19e-188">All of a sudden this hashtable starts to feel and act like an object.</span></span> <span data-ttu-id="da19e-189">Er is nog steeds een verzameling dingen, dus alle bovenstaande voor beelden zijn nog steeds van toepassing.</span><span class="sxs-lookup"><span data-stu-id="da19e-189">It's still a collection of things, so all the examples above still apply.</span></span> <span data-ttu-id="da19e-190">We benadert dit gewoon vanuit een ander weergave punt.</span><span class="sxs-lookup"><span data-stu-id="da19e-190">We just approach it from a different point of view.</span></span>

### <a name="checking-for-keys-and-values"></a><span data-ttu-id="da19e-191">Controleren op sleutels en waarden</span><span class="sxs-lookup"><span data-stu-id="da19e-191">Checking for keys and values</span></span>

<span data-ttu-id="da19e-192">In de meeste gevallen kunt u gewoon testen op de waarde, wat er ongeveer als volgt uitziet:</span><span class="sxs-lookup"><span data-stu-id="da19e-192">In most cases, you can just test for the value with something like this:</span></span>

```powershell
if( $person.age ){...}
```

<span data-ttu-id="da19e-193">Het is eenvoudig, maar is de bron van veel fouten voor mij, omdat er een belang rijke details in mijn logica worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="da19e-193">It's simple but has been the source of many bugs for me because I was overlooking one important detail in my logic.</span></span> <span data-ttu-id="da19e-194">Ik ben begonnen met het gebruik ervan om te testen of er een sleutel aanwezig was.</span><span class="sxs-lookup"><span data-stu-id="da19e-194">I started to use it to test if a key was present.</span></span> <span data-ttu-id="da19e-195">Als de waarde is `$false` of nul, zou deze instructie `$false` onverwacht worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="da19e-195">When the value was `$false` or zero, that statement would return `$false` unexpectedly.</span></span>

```powershell
if( $person.age -ne $null ){...}
```

<span data-ttu-id="da19e-196">Dit werkt rond het probleem voor nulwaarden, maar niet $null versus niet-bestaande sleutels.</span><span class="sxs-lookup"><span data-stu-id="da19e-196">This works around that issue for zero values but not $null vs non-existent keys.</span></span> <span data-ttu-id="da19e-197">In de meeste gevallen hoeft u dit onderscheid niet te maken, maar er zijn functies voor wanneer u dat doet.</span><span class="sxs-lookup"><span data-stu-id="da19e-197">Most of the time you don't need to make that distinction but there are functions for when you do.</span></span>

```powershell
if( $person.ContainsKey('age') ){...}
```

<span data-ttu-id="da19e-198">We hebben ook een `ContainsValue()` voor de situatie waarin u moet testen op een waarde zonder de sleutel te weten of de hele verzameling te herhalen.</span><span class="sxs-lookup"><span data-stu-id="da19e-198">We also have a `ContainsValue()` for the situation where you need to test for a value without knowing the key or iterating the whole collection.</span></span>

### <a name="removing-and-clearing-keys"></a><span data-ttu-id="da19e-199">Sleutels verwijderen en wissen</span><span class="sxs-lookup"><span data-stu-id="da19e-199">Removing and clearing keys</span></span>

<span data-ttu-id="da19e-200">U kunt sleutels verwijderen met de `.Remove()` functie.</span><span class="sxs-lookup"><span data-stu-id="da19e-200">You can remove keys with the `.Remove()` function.</span></span>

```powershell
$person.remove('age')
```

<span data-ttu-id="da19e-201">Als u een waarde toewijst, `$null` hoeft u alleen een sleutel met een waarde op te geven `$null` .</span><span class="sxs-lookup"><span data-stu-id="da19e-201">Assigning them a `$null` value just leaves you with a key that has a `$null` value.</span></span>

<span data-ttu-id="da19e-202">Een gemeen schappelijke manier om een hashtabel te wissen, is om deze eenvoudigweg te initialiseren naar een lege hashtabel.</span><span class="sxs-lookup"><span data-stu-id="da19e-202">A common way to clear a hashtable is to just initialize it to an empty hashtable.</span></span>

```powershell
$person = @{}
```

<span data-ttu-id="da19e-203">Probeer `clear()` in plaats daarvan de functie te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="da19e-203">While that does work, try to use the `clear()` function instead.</span></span>

```powershell
$person.clear()
```

<span data-ttu-id="da19e-204">Dit is een van deze gevallen waarbij het gebruik van de functie zelf-document code maakt en de bedoelingen van de code zeer helder maakt.</span><span class="sxs-lookup"><span data-stu-id="da19e-204">This is one of those instances where using the function creates self-documenting code and it makes the intentions of the code very clean.</span></span>

## <a name="all-the-fun-stuff"></a><span data-ttu-id="da19e-205">Alle leuke dingen</span><span class="sxs-lookup"><span data-stu-id="da19e-205">All the fun stuff</span></span>

### <a name="ordered-hashtables"></a><span data-ttu-id="da19e-206">Besteld hashtabellen</span><span class="sxs-lookup"><span data-stu-id="da19e-206">Ordered hashtables</span></span>

<span data-ttu-id="da19e-207">Hashtabellen zijn standaard niet gerangschikt (of gesorteerd).</span><span class="sxs-lookup"><span data-stu-id="da19e-207">By default, hashtables aren't ordered (or sorted).</span></span> <span data-ttu-id="da19e-208">In de traditionele context is de volg orde niet belang rijk wanneer u altijd een sleutel gebruikt om toegang te krijgen tot waarden.</span><span class="sxs-lookup"><span data-stu-id="da19e-208">In the traditional context, the order doesn't matter when you always use a key to access values.</span></span> <span data-ttu-id="da19e-209">Mogelijk wilt u dat de eigenschappen in de volg orde blijven staan waarin u ze definieert.</span><span class="sxs-lookup"><span data-stu-id="da19e-209">You may find that you want the properties to stay in the order that you define them.</span></span> <span data-ttu-id="da19e-210">Gelukkig, er is een manier om dat te doen met het `ordered` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="da19e-210">Thankfully, there's a way to do that with the `ordered` keyword.</span></span>

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="da19e-211">Wanneer u de sleutels en waarden nu opsomt, blijven ze in die volg orde.</span><span class="sxs-lookup"><span data-stu-id="da19e-211">Now when you enumerate the keys and values, they stay in that order.</span></span>

### <a name="inline-hashtables"></a><span data-ttu-id="da19e-212">Inline-hashtabellen</span><span class="sxs-lookup"><span data-stu-id="da19e-212">Inline hashtables</span></span>

<span data-ttu-id="da19e-213">Wanneer u een hashtabel op één regel definieert, kunt u de sleutel-waardeparen scheiden met een punt komma.</span><span class="sxs-lookup"><span data-stu-id="da19e-213">When you're defining a hashtable on one line, you can separate the key/value pairs with a semicolon.</span></span>

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

<span data-ttu-id="da19e-214">Dit kan handig zijn als u ze op de pipe maakt.</span><span class="sxs-lookup"><span data-stu-id="da19e-214">This will come in handy if you're creating them on the pipe.</span></span>

### <a name="custom-expressions-in-common-pipeline-commands"></a><span data-ttu-id="da19e-215">Aangepaste expressies in algemene pijplijn opdrachten</span><span class="sxs-lookup"><span data-stu-id="da19e-215">Custom expressions in common pipeline commands</span></span>

<span data-ttu-id="da19e-216">Er zijn enkele cmdlets die ondersteuning bieden voor het gebruik van hashtabellen om aangepaste of berekende eigenschappen te maken.</span><span class="sxs-lookup"><span data-stu-id="da19e-216">There are a few cmdlets that support the use of hashtables to create custom or calculated properties.</span></span> <span data-ttu-id="da19e-217">U ziet dit meestal met `Select-Object` en `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="da19e-217">You commonly see this with `Select-Object` and `Format-Table`.</span></span> <span data-ttu-id="da19e-218">De hashtabellen hebben een speciale syntaxis die er als volgt uitziet wanneer deze volledig is uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="da19e-218">The hashtables have a special syntax that looks like this when fully expanded.</span></span>

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

<span data-ttu-id="da19e-219">De `name` is wat de cmdlet zou labelen.</span><span class="sxs-lookup"><span data-stu-id="da19e-219">The `name` is what the cmdlet would label that column.</span></span> <span data-ttu-id="da19e-220">Het `expression` is een script blok dat wordt uitgevoerd, waarbij `$_` de waarde van het object op de pipe is.</span><span class="sxs-lookup"><span data-stu-id="da19e-220">The `expression` is a script block that is executed where `$_` is the value of the object on the pipe.</span></span> <span data-ttu-id="da19e-221">Dit is het script in actie:</span><span class="sxs-lookup"><span data-stu-id="da19e-221">Here is that script in action:</span></span>

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Properties name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

<span data-ttu-id="da19e-222">Ik heb dat in een variabele geplaatst, maar dit kan gemakkelijk inline worden gedefinieerd, en u kunt de kortings functie voor u verkorten `name` `n` `expression` `e` .</span><span class="sxs-lookup"><span data-stu-id="da19e-222">I placed that in a variable but it could easily be defined inline and you can shorten `name` to `n` and `expression` to `e` while you're at it.</span></span>

```powershell
$drives | Select-Object -properties name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

<span data-ttu-id="da19e-223">Ik weet niet hoe lang het duurt om opdrachten uit te geven. het bevordert vaak een slecht gedrag dat daar niet aan is.</span><span class="sxs-lookup"><span data-stu-id="da19e-223">I personally don't like how long that makes commands and it often promotes some bad behaviors that I won't get into.</span></span> <span data-ttu-id="da19e-224">Ik wil waarschijnlijk een nieuwe hashtabel maken of `pscustomobject` met alle velden en eigenschappen die ik wil gebruiken in plaats van deze benadering in scripts.</span><span class="sxs-lookup"><span data-stu-id="da19e-224">I'm more likely to create a new hashtable or `pscustomobject` with all the fields and properties that I want instead of using this approach in scripts.</span></span> <span data-ttu-id="da19e-225">Maar er is wel een groot aantal Program meren waarmee u op de hoogte zou zijn.</span><span class="sxs-lookup"><span data-stu-id="da19e-225">But there's a lot of code out there that does this so I wanted you to be aware of it.</span></span> <span data-ttu-id="da19e-226">Ik vind iets over het maken `pscustomobject` van een latere versie.</span><span class="sxs-lookup"><span data-stu-id="da19e-226">I talk about creating a `pscustomobject` later on.</span></span>

### <a name="custom-sort-expression"></a><span data-ttu-id="da19e-227">Aangepaste Sorteer expressie</span><span class="sxs-lookup"><span data-stu-id="da19e-227">Custom sort expression</span></span>

<span data-ttu-id="da19e-228">Het is eenvoudig om een verzameling te sorteren als de objecten de gegevens bevatten waarop u wilt sorteren.</span><span class="sxs-lookup"><span data-stu-id="da19e-228">It's easy to sort a collection if the objects have the data that you want to sort on.</span></span> <span data-ttu-id="da19e-229">U kunt de gegevens toevoegen aan het object voordat u het sorteert of een aangepaste expressie maakt voor `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="da19e-229">You can either add the data to the object before you sort it or create a custom expression for `Sort-Object`.</span></span>

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

<span data-ttu-id="da19e-230">In dit voor beeld maken we een lijst met gebruikers en gebruiken we een aangepaste cmdlet om meer informatie te krijgen voor de sorteer bewerking.</span><span class="sxs-lookup"><span data-stu-id="da19e-230">In this example I'm taking a list of users and using some custom cmdlet to get additional information just for the sort.</span></span>

#### <a name="sort-a-list-of-hashtables"></a><span data-ttu-id="da19e-231">Een lijst met hashtabellen sorteren</span><span class="sxs-lookup"><span data-stu-id="da19e-231">Sort a list of Hashtables</span></span>

<span data-ttu-id="da19e-232">Als u een lijst met hashtabellen hebt die u wilt sorteren, zult u zien dat de `Sort-Object` sleutels niet worden behandeld als eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="da19e-232">If you have a list of hashtables that you want to sort, you'll find that the `Sort-Object` doesn't treat your keys as properties.</span></span> <span data-ttu-id="da19e-233">We kunnen een afronding krijgen met behulp van een aangepaste Sorteer expressie.</span><span class="sxs-lookup"><span data-stu-id="da19e-233">We can get a round that by using a custom sort expression.</span></span>

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

## <a name="splatting-hashtables-at-cmdlets"></a><span data-ttu-id="da19e-234">Splatting hashtabellen bij cmdlets</span><span class="sxs-lookup"><span data-stu-id="da19e-234">Splatting hashtables at cmdlets</span></span>

<span data-ttu-id="da19e-235">Dit is een van mijn favoriete dingen over hashtabellen die veel mensen niet vroeg ontdekken.</span><span class="sxs-lookup"><span data-stu-id="da19e-235">This is one of my favorite things about hashtables that many people don't discover early on.</span></span>
<span data-ttu-id="da19e-236">Het idee is dat u in plaats van alle eigenschappen een cmdlet op één regel moet opgeven, maar u kunt ze eerst in een hashtabel inpakken.</span><span class="sxs-lookup"><span data-stu-id="da19e-236">The idea is that instead of providing all the properties to a cmdlet on one line, you can instead pack them into a hashtable first.</span></span> <span data-ttu-id="da19e-237">U kunt de hashtabel vervolgens op een speciale manier aan de functie toewijzen.</span><span class="sxs-lookup"><span data-stu-id="da19e-237">Then you can give the hashtable to the function in a special way.</span></span>
<span data-ttu-id="da19e-238">Hier volgt een voor beeld van het maken van een DHCP-scope op de normale manier.</span><span class="sxs-lookup"><span data-stu-id="da19e-238">Here is an example of creating a DHCP scope the normal way.</span></span>

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

<span data-ttu-id="da19e-239">Als [splatting][]niet wordt gebruikt, moeten al deze dingen op één regel worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="da19e-239">Without using [splatting][], all those things need to be defined on a single line.</span></span> <span data-ttu-id="da19e-240">Er wordt een schuif balk van het scherm weer gegeven of er wordt gewikkeld waar ooit het lijkt.</span><span class="sxs-lookup"><span data-stu-id="da19e-240">It either scrolls off the screen or will wrap where ever it feels like.</span></span> <span data-ttu-id="da19e-241">Vergelijk nu met een opdracht die gebruikmaakt van splatting.</span><span class="sxs-lookup"><span data-stu-id="da19e-241">Now compare that to a command that uses splatting.</span></span>

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

<span data-ttu-id="da19e-242">Het gebruik van het `@` teken in plaats van de `$` is het aanroepen van de splat-bewerking.</span><span class="sxs-lookup"><span data-stu-id="da19e-242">The use of the `@` sign instead of the `$` is what invokes the splat operation.</span></span>

<span data-ttu-id="da19e-243">Neem even de tijd om te weten hoe eenvoudig het voor beeld is te lezen.</span><span class="sxs-lookup"><span data-stu-id="da19e-243">Just take a moment to appreciate how easy that example is to read.</span></span> <span data-ttu-id="da19e-244">Ze zijn exact dezelfde opdracht met dezelfde waarden.</span><span class="sxs-lookup"><span data-stu-id="da19e-244">They are the exact same command with all the same values.</span></span> <span data-ttu-id="da19e-245">De tweede is gemakkelijker te begrijpen en verder te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="da19e-245">The second one is easier to understand and maintain going forward.</span></span>

<span data-ttu-id="da19e-246">Ik gebruik splatting altijd wanneer de opdracht te lang wordt.</span><span class="sxs-lookup"><span data-stu-id="da19e-246">I use splatting anytime the command gets too long.</span></span> <span data-ttu-id="da19e-247">Er wordt te lang gedefinieerd, waardoor mijn venster naar rechts schuift.</span><span class="sxs-lookup"><span data-stu-id="da19e-247">I define too long as causing my window to scroll right.</span></span> <span data-ttu-id="da19e-248">Als ik drie eigenschappen voor een functie raak, zijn conflicteert dat ik deze herschrijft met behulp van een splatted hashtabel.</span><span class="sxs-lookup"><span data-stu-id="da19e-248">If I hit three properties for a function, odds are that I'll rewrite it using a splatted hashtable.</span></span>

### <a name="splatting-for-optional-parameters"></a><span data-ttu-id="da19e-249">Splatting voor optionele para meters</span><span class="sxs-lookup"><span data-stu-id="da19e-249">Splatting for optional parameters</span></span>

<span data-ttu-id="da19e-250">Een van de meest voorkomende manieren om splatting te gebruiken, is door te omgaan met optionele para meters die afkomstig zijn van andere plaatsen in mijn script.</span><span class="sxs-lookup"><span data-stu-id="da19e-250">One of the most common ways I use splatting is to deal with optional parameters that come from some place else in my script.</span></span> <span data-ttu-id="da19e-251">Stel dat ik een functie heb waarmee een `Get-CIMInstance` aanroep met een optioneel argument wordt ingepakt `$Credential` .</span><span class="sxs-lookup"><span data-stu-id="da19e-251">Let's say I have a function that wraps a `Get-CIMInstance` call that has an optional `$Credential` argument.</span></span>

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

<span data-ttu-id="da19e-252">U begint met het maken van mijn hashtabel met algemene para meters.</span><span class="sxs-lookup"><span data-stu-id="da19e-252">I start by creating my hashtable with common parameters.</span></span> <span data-ttu-id="da19e-253">Vervolgens voeg ik de toe `$Credential` als deze bestaat.</span><span class="sxs-lookup"><span data-stu-id="da19e-253">Then I add the `$Credential` if it exists.</span></span>
<span data-ttu-id="da19e-254">Omdat ik splatting hier gebruik, hoeft ik alleen maar `Get-CIMInstance` één keer naar mijn code te bellen.</span><span class="sxs-lookup"><span data-stu-id="da19e-254">Because I'm using splatting here, I only need to have the call to `Get-CIMInstance` in my code once.</span></span> <span data-ttu-id="da19e-255">Dit ontwerp patroon is zeer helder en kan veel optionele para meters eenvoudig verwerken.</span><span class="sxs-lookup"><span data-stu-id="da19e-255">This design pattern is very clean and can handle lots of optional parameters easily.</span></span>

<span data-ttu-id="da19e-256">Als u eerlijk wilt zijn, kunt u uw opdrachten schrijven om `$null` waarden voor para meters toe te staan.</span><span class="sxs-lookup"><span data-stu-id="da19e-256">To be fair, you could write your commands to allow `$null` values for parameters.</span></span> <span data-ttu-id="da19e-257">U hebt gewoon niet altijd de controle over de andere opdrachten die u aanroept.</span><span class="sxs-lookup"><span data-stu-id="da19e-257">You just don't always have control over the other commands you're calling.</span></span>

### <a name="multiple-splats"></a><span data-ttu-id="da19e-258">Meerdere splats</span><span class="sxs-lookup"><span data-stu-id="da19e-258">Multiple splats</span></span>

<span data-ttu-id="da19e-259">U kunt meerdere hashtabellen naar dezelfde cmdlet splat.</span><span class="sxs-lookup"><span data-stu-id="da19e-259">You can splat multiple hashtables to the same cmdlet.</span></span> <span data-ttu-id="da19e-260">Als we ons oorspronkelijke splatting-voor beeld bekijken:</span><span class="sxs-lookup"><span data-stu-id="da19e-260">If we revisit our original splatting example:</span></span>

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

<span data-ttu-id="da19e-261">Ik gebruik deze methode wanneer ik een gemeen schappelijke set para meters heb die ik aan een groot aantal opdrachten kan door geven.</span><span class="sxs-lookup"><span data-stu-id="da19e-261">I'll use this method when I have a common set of parameters that I'm passing to lots of commands.</span></span>

### <a name="splatting-for-clean-code"></a><span data-ttu-id="da19e-262">Splatting voor schone code</span><span class="sxs-lookup"><span data-stu-id="da19e-262">Splatting for clean code</span></span>

<span data-ttu-id="da19e-263">Er is niets mis met het splatting van een enkele para meter als u code kunt opschonen.</span><span class="sxs-lookup"><span data-stu-id="da19e-263">There's nothing wrong with splatting a single parameter if makes you code cleaner.</span></span>

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a><span data-ttu-id="da19e-264">Splatting uitvoer bare bestanden</span><span class="sxs-lookup"><span data-stu-id="da19e-264">Splatting executables</span></span>

<span data-ttu-id="da19e-265">Splatting werkt ook voor sommige uitvoer bare bestanden die gebruikmaken van een `/param:value` syntaxis.</span><span class="sxs-lookup"><span data-stu-id="da19e-265">Splatting also works on some executables that use a `/param:value` syntax.</span></span> <span data-ttu-id="da19e-266">`Robocopy.exe`heeft bijvoorbeeld een aantal para meters zoals deze.</span><span class="sxs-lookup"><span data-stu-id="da19e-266">`Robocopy.exe`, for example, has some parameters like this.</span></span>

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

<span data-ttu-id="da19e-267">Ik weet niet dat dit nuttig is, maar ik heb het interessant vond.</span><span class="sxs-lookup"><span data-stu-id="da19e-267">I don't know that this is all that useful, but I found it interesting.</span></span>

## <a name="adding-hashtables"></a><span data-ttu-id="da19e-268">Hashtabellen toevoegen</span><span class="sxs-lookup"><span data-stu-id="da19e-268">Adding hashtables</span></span>

<span data-ttu-id="da19e-269">Hashtabellen ondersteunen de operator voor optellen om twee hashtabellen te combi neren.</span><span class="sxs-lookup"><span data-stu-id="da19e-269">Hashtables support the addition operator to combine two hashtables.</span></span>

```powershell
$person += @{Zip = '78701'}
```

<span data-ttu-id="da19e-270">Dit werkt alleen als de twee hashtabellen geen sleutel delen.</span><span class="sxs-lookup"><span data-stu-id="da19e-270">This only works if the two hashtables don't share a key.</span></span>

## <a name="nested-hashtables"></a><span data-ttu-id="da19e-271">Geneste hashtabellen</span><span class="sxs-lookup"><span data-stu-id="da19e-271">Nested hashtables</span></span>

<span data-ttu-id="da19e-272">We kunnen hashtabellen gebruiken als waarden binnen een hashtabel.</span><span class="sxs-lookup"><span data-stu-id="da19e-272">We can use hashtables as values inside a hashtable.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

<span data-ttu-id="da19e-273">Ik heb een basis-hashtabel met twee sleutels gestart.</span><span class="sxs-lookup"><span data-stu-id="da19e-273">I started with a basic hashtable containing two keys.</span></span> <span data-ttu-id="da19e-274">Ik heb een sleutel `location` met de naam met een lege hashtabel toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="da19e-274">I added a key called `location` with an empty hashtable.</span></span> <span data-ttu-id="da19e-275">Vervolgens zijn de laatste twee items toegevoegd aan die `location` hashtabel.</span><span class="sxs-lookup"><span data-stu-id="da19e-275">Then I added the last two items to that `location` hashtable.</span></span> <span data-ttu-id="da19e-276">We kunnen dit ook doen.</span><span class="sxs-lookup"><span data-stu-id="da19e-276">We can do this all inline too.</span></span>

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

<span data-ttu-id="da19e-277">Hiermee maakt u dezelfde hashtabel die we hierboven hebben gezien en toegang hebben tot de eigenschappen op dezelfde manier.</span><span class="sxs-lookup"><span data-stu-id="da19e-277">This creates the same hashtable that we saw above and can access the properties the same way.</span></span>

```powershell
$person.location.city
Austin
```powershell

There are many ways to approach the structure of your objects. Here is a second way to look at a
nested hashtable.

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

<span data-ttu-id="da19e-278">Dit is een combi Naties van het concept van het gebruik van hashtabellen als een verzameling objecten en een verzameling eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="da19e-278">This mixes the concept of using hashtables as a collection of objects and a collection of properties.</span></span> <span data-ttu-id="da19e-279">De waarden zijn nog steeds eenvoudig te benaderen, zelfs wanneer ze zijn genest met een wille keurige benadering.</span><span class="sxs-lookup"><span data-stu-id="da19e-279">The values are still easy to access even when they're nested using whatever approach you prefer.</span></span>

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

<span data-ttu-id="da19e-280">Ik gebruik de punt eigenschap vaak wanneer ik deze wil behandelen als een eigenschap.</span><span class="sxs-lookup"><span data-stu-id="da19e-280">I tend to use the dot property when I'm treating it like a property.</span></span> <span data-ttu-id="da19e-281">Dit zijn doorgaans de dingen die ik statisch heb gedefinieerd in mijn code en ik weet dat ze zich op de bovenkant van mijn hoofd bevinden.</span><span class="sxs-lookup"><span data-stu-id="da19e-281">Those are generally things I've defined statically in my code and I know them off the top of my head.</span></span> <span data-ttu-id="da19e-282">Als ik de lijst wil door lopen of op een programmatische manier toegang wil krijgen tot de toetsen, gebruik ik de vier Kante haken om de naam van de sleutel op te geven.</span><span class="sxs-lookup"><span data-stu-id="da19e-282">If I need to walk the list or programmatically access the keys, I use the brackets to provide the key name.</span></span>

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

<span data-ttu-id="da19e-283">Met de mogelijkheid om hashtabellen te nesten, hebt u veel flexibiliteit en opties.</span><span class="sxs-lookup"><span data-stu-id="da19e-283">Having the ability to nest hashtables gives you a lot of flexibility and options.</span></span>

### <a name="looking-at-nested-hashtables"></a><span data-ttu-id="da19e-284">Geneste hashtabellen bekijken</span><span class="sxs-lookup"><span data-stu-id="da19e-284">Looking at nested hashtables</span></span>

<span data-ttu-id="da19e-285">Zodra u begint met het nesten van hashtabellen, hebt u een eenvoudige manier nodig om ze te bekijken vanuit de-console.</span><span class="sxs-lookup"><span data-stu-id="da19e-285">As soon as you start nesting hashtables, you're going to need an easy way to look at them from the console.</span></span> <span data-ttu-id="da19e-286">Als ik deze laatste hashtabel, krijg ik een uitvoer die er als volgt uitziet en zo dieper gaat:</span><span class="sxs-lookup"><span data-stu-id="da19e-286">If I take that last hashtable, I get an output that looks like this and it only goes so deep:</span></span>

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

<span data-ttu-id="da19e-287">Mijn ga naar opdracht voor het bekijken van deze dingen is `ConvertTo-JSON` omdat deze zeer schoon is en dat ik regel matig JSON op andere zaken zou gebruiken.</span><span class="sxs-lookup"><span data-stu-id="da19e-287">My go to command for looking at these things is `ConvertTo-JSON` because it's very clean and I frequently use JSON on other things.</span></span>

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

<span data-ttu-id="da19e-288">Zelfs als u geen JSON kent, kunt u zien wat u zoekt.</span><span class="sxs-lookup"><span data-stu-id="da19e-288">Even if you don't know JSON, you should be able to see what you're looking for.</span></span> <span data-ttu-id="da19e-289">Er is een `Format-Custom` opdracht voor gestructureerde gegevens, zoals deze, maar de JSON-weer gave is beter.</span><span class="sxs-lookup"><span data-stu-id="da19e-289">There's a `Format-Custom` command for structured data like this but I still like the JSON view better.</span></span>

## <a name="creating-objects"></a><span data-ttu-id="da19e-290">Objecten maken</span><span class="sxs-lookup"><span data-stu-id="da19e-290">Creating objects</span></span>

<span data-ttu-id="da19e-291">Soms hoeft u alleen maar een object te hebben en een hashtabel te gebruiken om eigenschappen te bewaren, maar wordt de taak niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="da19e-291">Sometimes you just need to have an object and using a hashtable to hold properties just isn't getting the job done.</span></span> <span data-ttu-id="da19e-292">Doorgaans wilt u de sleutels zien als kolom namen.</span><span class="sxs-lookup"><span data-stu-id="da19e-292">Most commonly you want to see the keys as column names.</span></span> <span data-ttu-id="da19e-293">Een `pscustomobject` maakt dat eenvoudig.</span><span class="sxs-lookup"><span data-stu-id="da19e-293">A `pscustomobject` makes that easy.</span></span>

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

<span data-ttu-id="da19e-294">Zelfs als u deze niet `pscustomobject` in eerste instantie maakt, kunt u deze altijd later opnieuw casten wanneer dat nodig is.</span><span class="sxs-lookup"><span data-stu-id="da19e-294">Even if you don't create it as a `pscustomobject` initially, you can always cast it later when needed.</span></span>

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

<span data-ttu-id="da19e-295">Ik heb al een gedetailleerde write-up voor [pscustomobject][] die je na deze versie moet lezen.</span><span class="sxs-lookup"><span data-stu-id="da19e-295">I already have detailed write-up for [pscustomobject][] that you should go read after this one.</span></span> <span data-ttu-id="da19e-296">Het is gebaseerd op een groot aantal dingen die hier worden geleerd.</span><span class="sxs-lookup"><span data-stu-id="da19e-296">It builds on a lot of the things learned here.</span></span>

## <a name="reading-and-writing-hashtables-to-file"></a><span data-ttu-id="da19e-297">Hashtabellen lezen en schrijven naar bestand</span><span class="sxs-lookup"><span data-stu-id="da19e-297">Reading and writing hashtables to file</span></span>

### <a name="saving-to-csv"></a><span data-ttu-id="da19e-298">Opslaan in CSV</span><span class="sxs-lookup"><span data-stu-id="da19e-298">Saving to CSV</span></span>

<span data-ttu-id="da19e-299">Lastig met het ophalen van een hashtabel om op te slaan in een CSV, is een van de problemen waarnaar wordt verwezen.</span><span class="sxs-lookup"><span data-stu-id="da19e-299">Struggling with getting a hashtable to save to a CSV is one of the difficulties that I was referring to above.</span></span> <span data-ttu-id="da19e-300">Converteer uw hashtabel naar een `pscustomobject` en wordt op de juiste manier opgeslagen in CSV.</span><span class="sxs-lookup"><span data-stu-id="da19e-300">Convert your hashtable to a `pscustomobject` and it will save correctly to CSV.</span></span> <span data-ttu-id="da19e-301">Zo kunt u beginnen met een `pscustomobject` zodat de volg orde van de kolommen behouden blijft.</span><span class="sxs-lookup"><span data-stu-id="da19e-301">It helps if you start with a `pscustomobject` so the column order is preserved.</span></span> <span data-ttu-id="da19e-302">Maar u kunt deze `pscustomobject` indien nodig naar een inline casten.</span><span class="sxs-lookup"><span data-stu-id="da19e-302">But you can cast it to a `pscustomobject` inline if needed.</span></span>

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

<span data-ttu-id="da19e-303">Ga opnieuw naar mijn write-up met behulp van een [pscustomobject][].</span><span class="sxs-lookup"><span data-stu-id="da19e-303">Again, check out my write-up on using a [pscustomobject][].</span></span>

### <a name="saving-a-nested-hashtable-to-file"></a><span data-ttu-id="da19e-304">Een geneste hashtabel opslaan in een bestand</span><span class="sxs-lookup"><span data-stu-id="da19e-304">Saving a nested hashtable to file</span></span>

<span data-ttu-id="da19e-305">Als ik een geneste hashtabel moet opslaan in een bestand en deze vervolgens weer kan lezen, moet ik de JSON-cmdlets gebruiken om het te doen.</span><span class="sxs-lookup"><span data-stu-id="da19e-305">If I need to save a nested hashtable to a file and then read it back in again, I use the JSON cmdlets to do it.</span></span>

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

<span data-ttu-id="da19e-306">Er zijn twee belang rijke punten over deze methode.</span><span class="sxs-lookup"><span data-stu-id="da19e-306">There are two important points about this method.</span></span> <span data-ttu-id="da19e-307">Ten eerste is de JSON wegge schreven, zodat ik de optie moet gebruiken `-Raw` om deze weer in één teken reeks te lezen.</span><span class="sxs-lookup"><span data-stu-id="da19e-307">First is that the JSON is written out multiline so I need to use the `-Raw` option to read it back into a single string.</span></span> <span data-ttu-id="da19e-308">Ten tweede is het geïmporteerde object niet meer een `[hashtable]` .</span><span class="sxs-lookup"><span data-stu-id="da19e-308">The Second is that the imported object is no longer a `[hashtable]`.</span></span> <span data-ttu-id="da19e-309">Het is nu a `[pscustomobject]` en dat kan problemen veroorzaken als u deze niet verwacht.</span><span class="sxs-lookup"><span data-stu-id="da19e-309">It's now a `[pscustomobject]` and that can cause issues if you don't expect it.</span></span>

<span data-ttu-id="da19e-310">Als u wilt dat deze bij het `[hashtable]` importeren moet worden, moet u de `Export-CliXml` opdrachten en gebruiken `Import-CliXml` .</span><span class="sxs-lookup"><span data-stu-id="da19e-310">If you need it to be a `[hashtable]` on import, then you need to use the `Export-CliXml` and `Import-CliXml` commands.</span></span>

### <a name="converting-json-to-hashtable"></a><span data-ttu-id="da19e-311">JSON converteren naar hashtabel</span><span class="sxs-lookup"><span data-stu-id="da19e-311">Converting JSON to Hashtable</span></span>

<span data-ttu-id="da19e-312">Als u JSON naar a moet converteren `[hashtable]` , is er een manier waarop u deze kunt doen met de [JavaScriptSerializer][] in .net.</span><span class="sxs-lookup"><span data-stu-id="da19e-312">If you need to convert JSON to a `[hashtable]`, there's one way that I know of to do it with the [JavaScriptSerializer][] in .NET.</span></span>

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

### <a name="reading-directly-from-a-file"></a><span data-ttu-id="da19e-313">Rechtstreeks vanuit een bestand lezen</span><span class="sxs-lookup"><span data-stu-id="da19e-313">Reading directly from a file</span></span>

<span data-ttu-id="da19e-314">Als u een bestand hebt dat een hashtabel met een Power shell-syntaxis bevat, is het een manier om deze rechtstreeks te importeren.</span><span class="sxs-lookup"><span data-stu-id="da19e-314">If you have a file that contains a hashtable using PowerShell syntax, there's a way to import it directly.</span></span>

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

<span data-ttu-id="da19e-315">De inhoud van het bestand wordt geïmporteerd in een `scriptblock` , waarna wordt gecontroleerd of er geen andere Power shell-opdrachten aanwezig zijn voordat deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="da19e-315">It imports the contents of the file into a `scriptblock`, then checks to make sure it doesn't have any other PowerShell commands in it before it executes it.</span></span>

<span data-ttu-id="da19e-316">Wist u dat een module manifest (het psd1-bestand) alleen een hashtabel is?</span><span class="sxs-lookup"><span data-stu-id="da19e-316">On that note, did you know that a module manifest (the psd1 file) is just a hashtable?</span></span>

## <a name="keys-are-just-strings"></a><span data-ttu-id="da19e-317">Sleutels zijn alleen teken reeksen</span><span class="sxs-lookup"><span data-stu-id="da19e-317">Keys are just strings</span></span>

<span data-ttu-id="da19e-318">Ik wil geen eerdere versie van deze tangens uitschakelen, maar de sleutels zijn alleen teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="da19e-318">I didn't want to go off on this tangent earlier, but the keys are just strings.</span></span> <span data-ttu-id="da19e-319">Daarom kunnen we aanhalings tekens maken en deze een eigen sleutel geven.</span><span class="sxs-lookup"><span data-stu-id="da19e-319">So we can put quotes around anything and make it a key.</span></span>

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

<span data-ttu-id="da19e-320">U kunt oneven dingen doen die u mogelijk niet hebt gerealiseerd.</span><span class="sxs-lookup"><span data-stu-id="da19e-320">You can do some odd things that you may not have realized you could do.</span></span>

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

<span data-ttu-id="da19e-321">Maar omdat u iets kunt doen, betekent dit niet dat u moet.</span><span class="sxs-lookup"><span data-stu-id="da19e-321">Just because you can do something, it doesn't mean that you should.</span></span> <span data-ttu-id="da19e-322">Het laatste lijkt erop dat er een fout is opgetreden die in de wacht staat en dat de code eenvoudig te begrijpen is.</span><span class="sxs-lookup"><span data-stu-id="da19e-322">That last one just looks like a bug waiting to happen and would be easily misunderstood by anyone reading your code.</span></span>

<span data-ttu-id="da19e-323">Technisch uw sleutel hoeft geen teken reeks te zijn, maar ze zijn gemakkelijker te zien als u alleen teken reeksen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="da19e-323">Technically your key doesn't have to be a string but they're easier to think about if you only use strings.</span></span>

## <a name="use-in-automatic-variables"></a><span data-ttu-id="da19e-324">Gebruiken in automatische variabelen</span><span class="sxs-lookup"><span data-stu-id="da19e-324">Use in automatic variables</span></span>

### <a name="psboundparameters"></a><span data-ttu-id="da19e-325">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="da19e-325">$PSBoundParameters</span></span>

<span data-ttu-id="da19e-326">[$PSBoundParameters] [] is een automatische variabele die alleen in de context van een functie bestaat.</span><span class="sxs-lookup"><span data-stu-id="da19e-326">[$PSBoundParameters][] is an automatic variable that only exists inside the context of a function.</span></span> <span data-ttu-id="da19e-327">Het bevat alle para meters waarmee de functie is aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="da19e-327">It contains all the parameters that the function was called with.</span></span> <span data-ttu-id="da19e-328">Dit is niet precies een hashtabel, maar bijna genoeg zodat u deze kunt behandelen als één.</span><span class="sxs-lookup"><span data-stu-id="da19e-328">This isn't exactly a hashtable but close enough that you can treat it like one.</span></span>

<span data-ttu-id="da19e-329">Dit omvat het verwijderen van sleutels en het splatting aan andere functies.</span><span class="sxs-lookup"><span data-stu-id="da19e-329">That includes removing keys and splatting it to other functions.</span></span> <span data-ttu-id="da19e-330">Als u een proxy functie hebt gevonden, kunt u deze beter bekijken.</span><span class="sxs-lookup"><span data-stu-id="da19e-330">If you find yourself writing proxy functions, take a closer look at this one.</span></span>

<span data-ttu-id="da19e-331">Zie [about_Automatic_Variables][] voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="da19e-331">See [about_Automatic_Variables][] for more details.</span></span>

### <a name="psboundparameters-gotcha"></a><span data-ttu-id="da19e-332">PSBoundParameters gotcha</span><span class="sxs-lookup"><span data-stu-id="da19e-332">PSBoundParameters gotcha</span></span>

<span data-ttu-id="da19e-333">Een belang rijke ding die u moet onthouden is dat dit alleen de waarden bevat die worden door gegeven als para meters.</span><span class="sxs-lookup"><span data-stu-id="da19e-333">One important thing to remember is that this only includes the values that are passed in as parameters.</span></span> <span data-ttu-id="da19e-334">Als u ook para meters met standaard waarden hebt, maar deze niet worden door gegeven door de aanroeper, `$PSBoundParameters` bevatten deze waarden niet.</span><span class="sxs-lookup"><span data-stu-id="da19e-334">If you also have parameters with default values but aren't passed in by the caller, `$PSBoundParameters` doesn't contain those values.</span></span> <span data-ttu-id="da19e-335">Dit wordt meestal gezien.</span><span class="sxs-lookup"><span data-stu-id="da19e-335">This is commonly overlooked.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="da19e-336">$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="da19e-336">$PSDefaultParameterValues</span></span>

<span data-ttu-id="da19e-337">Met deze automatische variabele kunt u standaard waarden toewijzen aan elke cmdlet zonder de cmdlet te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="da19e-337">This automatic variable lets you assign default values to any cmdlet without changing the cmdlet.</span></span>
<span data-ttu-id="da19e-338">Bekijk dit voor beeld.</span><span class="sxs-lookup"><span data-stu-id="da19e-338">Take a look at this example.</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

<span data-ttu-id="da19e-339">Hiermee voegt u een vermelding toe aan de `$PSDefaultParameterValues` hashtabel die wordt ingesteld `UTF8` als de standaard waarde voor de `Out-File -Encoding` para meter.</span><span class="sxs-lookup"><span data-stu-id="da19e-339">This adds an entry to the `$PSDefaultParameterValues` hashtable that sets `UTF8` as the default value for the `Out-File -Encoding` parameter.</span></span> <span data-ttu-id="da19e-340">Dit is een specifieke sessie, zodat u deze in uw kunt plaatsen `$profile` .</span><span class="sxs-lookup"><span data-stu-id="da19e-340">This is session-specific so you should place it in your `$profile`.</span></span>

<span data-ttu-id="da19e-341">Ik gebruik dit regel matig om waarden vooraf toe te wijzen die ik regel matig Typ.</span><span class="sxs-lookup"><span data-stu-id="da19e-341">I use this often to pre-assign values that I type quite often.</span></span>

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

<span data-ttu-id="da19e-342">Er worden ook joker tekens geaccepteerd zodat u waarden in bulk kunt instellen.</span><span class="sxs-lookup"><span data-stu-id="da19e-342">This also accepts wildcards so you can set values in bulk.</span></span> <span data-ttu-id="da19e-343">Hier volgen enkele manieren waarop u deze kunt gebruiken:</span><span class="sxs-lookup"><span data-stu-id="da19e-343">Here are some ways you can use that:</span></span>

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

<span data-ttu-id="da19e-344">Zie dit fantastische artikel over [automatische standaard instellingen][] door [Michael Sorens][]voor een uitgebreidere uitsplitsing.</span><span class="sxs-lookup"><span data-stu-id="da19e-344">For a more in-depth breakdown, see this great article on [Automatic Defaults][] by [Michael Sorens][].</span></span>

## <a name="regex-matches"></a><span data-ttu-id="da19e-345">Regex $Matches</span><span class="sxs-lookup"><span data-stu-id="da19e-345">Regex $Matches</span></span>

<span data-ttu-id="da19e-346">Wanneer u de `-match` operator gebruikt, wordt een automatische variabele `$matches` met de naam gemaakt met de resultaten van de overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="da19e-346">When you use the `-match` operator, an automatic variable called `$matches` is created with the results of the match.</span></span> <span data-ttu-id="da19e-347">Als u sub-expressies in uw regex hebt, worden deze subtreffers ook weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="da19e-347">If you have any sub expressions in your regex, those sub matches are also listed.</span></span>

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a><span data-ttu-id="da19e-348">Benoemde overeenkomsten</span><span class="sxs-lookup"><span data-stu-id="da19e-348">Named matches</span></span>

<span data-ttu-id="da19e-349">Dit is een van mijn favoriete functies die de meeste mensen niet kennen.</span><span class="sxs-lookup"><span data-stu-id="da19e-349">This is one of my favorite features that most people don't know about.</span></span> <span data-ttu-id="da19e-350">Als u een benoemde regex match gebruikt, hebt u toegang tot die overeenkomst op naam op basis van de overeenkomsten.</span><span class="sxs-lookup"><span data-stu-id="da19e-350">If you use a named regex match, then you can access that match by name on the matches.</span></span>

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

<span data-ttu-id="da19e-351">In het bovenstaande voor beeld `(?<Name>.*)` is de een benoemde subexpression.</span><span class="sxs-lookup"><span data-stu-id="da19e-351">In the example above, the `(?<Name>.*)` is a named sub expression.</span></span> <span data-ttu-id="da19e-352">Deze waarde wordt vervolgens in de `$Matches.Name` eigenschap geplaatst.</span><span class="sxs-lookup"><span data-stu-id="da19e-352">This value is then placed in the `$Matches.Name` property.</span></span>

## <a name="group-object--ashashtable"></a><span data-ttu-id="da19e-353">Groep-object-AsHashtable</span><span class="sxs-lookup"><span data-stu-id="da19e-353">Group-Object -AsHashtable</span></span>

<span data-ttu-id="da19e-354">Een weinig bekende functie van `Group-Object` is dat deze gegevens sets kan omzetten in een hashtabel voor u.</span><span class="sxs-lookup"><span data-stu-id="da19e-354">One little known feature of `Group-Object` is that it can turn some datasets into a hashtable for you.</span></span>

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

<span data-ttu-id="da19e-355">Hiermee wordt elke rij toegevoegd aan een hashtabel en wordt de opgegeven eigenschap gebruikt als de sleutel voor toegang tot de tabel.</span><span class="sxs-lookup"><span data-stu-id="da19e-355">This will add each row into a hashtable and use the specified property as the key to access it.</span></span>

## <a name="copying-hashtables"></a><span data-ttu-id="da19e-356">Hashtabellen kopiëren</span><span class="sxs-lookup"><span data-stu-id="da19e-356">Copying Hashtables</span></span>

<span data-ttu-id="da19e-357">Een belang rijke ding die u moet weten, is dat hashtabellen objecten zijn.</span><span class="sxs-lookup"><span data-stu-id="da19e-357">One important thing to know is that hashtables are objects.</span></span> <span data-ttu-id="da19e-358">En elke variabele is alleen een verwijzing naar een object.</span><span class="sxs-lookup"><span data-stu-id="da19e-358">And each variable is just a reference to an object.</span></span> <span data-ttu-id="da19e-359">Dit betekent dat het meer werk nodig heeft om een geldige kopie van een hashtabel te maken.</span><span class="sxs-lookup"><span data-stu-id="da19e-359">This means that it takes more work to make a valid copy of a hashtable.</span></span>

### <a name="assigning-reference-types"></a><span data-ttu-id="da19e-360">Verwijzings typen toewijzen</span><span class="sxs-lookup"><span data-stu-id="da19e-360">Assigning reference types</span></span>

<span data-ttu-id="da19e-361">Wanneer u één hashtabel hebt en deze toewijst aan een tweede variabele, wijzen beide variabelen naar dezelfde hashtabel.</span><span class="sxs-lookup"><span data-stu-id="da19e-361">When you have one hashtable and assign it to a second variable, both variables point to the same hashtable.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="da19e-362">Dit markeert dat ze hetzelfde zijn omdat het wijzigen van de waarden in een ook de waarden in de andere wijzigt.</span><span class="sxs-lookup"><span data-stu-id="da19e-362">This highlights that they're the same because altering the values in one will also alter the values in the other.</span></span> <span data-ttu-id="da19e-363">Dit geldt ook voor het door geven van hashtabellen in andere functies.</span><span class="sxs-lookup"><span data-stu-id="da19e-363">This also applies when passing hashtables into other functions.</span></span> <span data-ttu-id="da19e-364">Als deze functies wijzigingen aanbrengen in de hashtabel, wordt het origineel ook gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="da19e-364">If those functions make changes to that hashtable, your original is also altered.</span></span>

### <a name="shallow-copies-single-level"></a><span data-ttu-id="da19e-365">Recente kopieën, één niveau</span><span class="sxs-lookup"><span data-stu-id="da19e-365">Shallow copies, single level</span></span>

<span data-ttu-id="da19e-366">Als we een eenvoudige hashtabel hebben, zoals in het bovenstaande voor beeld, kunnen we gebruiken om een inkomend `.Clone()` exemplaar te maken.</span><span class="sxs-lookup"><span data-stu-id="da19e-366">If we have a simple hashtable like our example above, we can use `.Clone()` to make a shallow copy.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

<span data-ttu-id="da19e-367">Hierdoor kunnen we enkele eenvoudige wijzigingen aanbrengen die niet van invloed zijn op de andere.</span><span class="sxs-lookup"><span data-stu-id="da19e-367">This will allow us to make some basic changes to one that don't impact the other.</span></span>

### <a name="shallow-copies-nested"></a><span data-ttu-id="da19e-368">Recente kopieën, genest</span><span class="sxs-lookup"><span data-stu-id="da19e-368">Shallow copies, nested</span></span>

<span data-ttu-id="da19e-369">De reden waarom het een begrootte kopie wordt genoemd, is dat alleen de eigenschappen van het basis niveau worden gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="da19e-369">The reason why it's called a shallow copy is because it only copies the base level properties.</span></span> <span data-ttu-id="da19e-370">Als een van deze eigenschappen een verwijzings type is (zoals een andere hashtabel), zullen die geneste objecten nog steeds naar elkaar wijzen.</span><span class="sxs-lookup"><span data-stu-id="da19e-370">If one of those properties is a reference type (like another hashtable), then those nested objects will still point to each other.</span></span>

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

<span data-ttu-id="da19e-371">Zo kunt u zien dat hoewel de hashtabel is gekloond, de verwijzing naar niet is `person` gekloond.</span><span class="sxs-lookup"><span data-stu-id="da19e-371">So you can see that even though I cloned the hashtable, the reference to `person` wasn't cloned.</span></span> <span data-ttu-id="da19e-372">We moeten een diepe kopie maken om echt een tweede hashtabel te hebben die niet is gekoppeld aan de eerste.</span><span class="sxs-lookup"><span data-stu-id="da19e-372">We need to make a deep copy to truly have a second hashtable that isn't linked to the first.</span></span>

### <a name="deep-copies"></a><span data-ttu-id="da19e-373">Uitgebreide kopieën</span><span class="sxs-lookup"><span data-stu-id="da19e-373">Deep copies</span></span>

<span data-ttu-id="da19e-374">Op het moment van schrijven, weet ik niet of er slimme manieren zijn om alleen een diepe kopie van een hashtabel te maken (en deze als een hashtabel te behouden).</span><span class="sxs-lookup"><span data-stu-id="da19e-374">At the time of writing this, I'm not aware of any clever ways to just make a deep copy of a hashtable (and keep it as a hashtable).</span></span> <span data-ttu-id="da19e-375">Dat is slechts een van de dingen die iemand nodig heeft om te schrijven.</span><span class="sxs-lookup"><span data-stu-id="da19e-375">That's just one of those things that someone needs to write.</span></span>
<span data-ttu-id="da19e-376">Hier volgt een snelle methode om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="da19e-376">Here is a quick method to do that.</span></span>

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

<span data-ttu-id="da19e-377">Er worden geen andere verwijzings typen of-matrices verwerkt, maar dit is een goed uitgangs punt.</span><span class="sxs-lookup"><span data-stu-id="da19e-377">It doesn't handle any other reference types or arrays, but it's a good starting point.</span></span>

## <a name="anything-else"></a><span data-ttu-id="da19e-378">Nog iets?</span><span class="sxs-lookup"><span data-stu-id="da19e-378">Anything else?</span></span>

<span data-ttu-id="da19e-379">Ik heb veel moeite gedekt.</span><span class="sxs-lookup"><span data-stu-id="da19e-379">I covered a lot of ground quickly.</span></span> <span data-ttu-id="da19e-380">Ik hoop dat u er geen zorgen meer meer over hebt, of dat u deze beter kunt zien wanneer u dit leest.</span><span class="sxs-lookup"><span data-stu-id="da19e-380">My hope is that you walk away leaning something new or understanding it better every time you read this.</span></span> <span data-ttu-id="da19e-381">Omdat ik het volledige spectrum van deze functie heb gezien, zijn er aspecten die alleen op u nu mogelijk niet van toepassing zijn.</span><span class="sxs-lookup"><span data-stu-id="da19e-381">Because I covered the full spectrum of this feature, there are aspects that just may not apply to you right now.</span></span> <span data-ttu-id="da19e-382">Dat is heel goed en de verwachte soort is afhankelijk van hoeveel u met Power shell werkt.</span><span class="sxs-lookup"><span data-stu-id="da19e-382">That is perfectly OK and is kind of expected depending on how much you work with PowerShell.</span></span>

<span data-ttu-id="da19e-383">Hier volgt een overzicht van alles wat we hebben behandeld in geval van een back-up naar iets.</span><span class="sxs-lookup"><span data-stu-id="da19e-383">Here is a list of everything we covered in case you want to jump back up to something.</span></span> <span data-ttu-id="da19e-384">Normaal gesp roken gaat dit aan het begin, maar dit is van boven naar beneden geschreven met voor beelden die zijn gebaseerd op alles wat eerder werd geleverd.</span><span class="sxs-lookup"><span data-stu-id="da19e-384">Normally, this would go at the beginning but this was written from top to bottom with examples that build on everything that came before it.</span></span>

<!-- link references -->
[oorspronkelijke versie]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[original version]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[hashtabellen]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[hashtables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[matrices]: /powershell/module/microsoft.powershell.core/about/about_arrays
[arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Als u prestatie problemen hebt, test u deze]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best%20Practices/Performance.md
[If performance matters, test it]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best%20Practices/Performance.md
[splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[Automatische standaard waarden]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Automatic Defaults]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
