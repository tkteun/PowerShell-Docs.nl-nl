---
description: Hierin wordt beschreven hoe u hash-tabellen maakt, gebruikt en sorteert in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: 1e8845e54b96fc3facf8a5b1a19ff52a5293921c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252794"
---
# <a name="about-hash-tables"></a><span data-ttu-id="642f2-104">Hash-tabellen</span><span class="sxs-lookup"><span data-stu-id="642f2-104">About Hash Tables</span></span>

## <a name="short-description"></a><span data-ttu-id="642f2-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="642f2-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="642f2-106">Hierin wordt beschreven hoe u hash-tabellen maakt, gebruikt en sorteert in Power shell.</span><span class="sxs-lookup"><span data-stu-id="642f2-106">Describes how to create, use, and sort hash tables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="642f2-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="642f2-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="642f2-108">Een hash-tabel, ook wel een woorden lijst of associatieve matrix genoemd, is een compacte gegevens structuur waarin een of meer sleutel-waardeparen worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="642f2-108">A hash table, also known as a dictionary or associative array, is a compact data structure that stores one or more key/value pairs.</span></span> <span data-ttu-id="642f2-109">Een hash-tabel kan bijvoorbeeld een reeks IP-adressen en computer namen bevatten, waarbij de IP-adressen de sleutels zijn en de computer namen de waarden zijn, of andersom.</span><span class="sxs-lookup"><span data-stu-id="642f2-109">For example, a hash table might contain a series of IP addresses and computer names, where the IP addresses are the keys and the computer names are the values, or vice versa.</span></span>

<span data-ttu-id="642f2-110">Elke hash-tabel in Power shell is een hashtabel-object (System. Collections. hashtabel).</span><span class="sxs-lookup"><span data-stu-id="642f2-110">In PowerShell, each hash table is a Hashtable (System.Collections.Hashtable) object.</span></span> <span data-ttu-id="642f2-111">U kunt de eigenschappen en methoden van hashtabel-objecten in Power shell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="642f2-111">You can use the properties and methods of Hashtable objects in PowerShell.</span></span>

<span data-ttu-id="642f2-112">Vanaf Power Shell 3,0 kunt u het kenmerk [gelastd] gebruiken om een geordende woorden lijst (System. Collections. specialist. OrderedDictionary) in Power shell te maken.</span><span class="sxs-lookup"><span data-stu-id="642f2-112">Beginning in PowerShell 3.0, you can use the [ordered] attribute to create an ordered dictionary (System.Collections.Specialized.OrderedDictionary) in PowerShell.</span></span>

<span data-ttu-id="642f2-113">Geordende woorden boeken verschillen van hash-tabellen in dat de sleutels altijd worden weer gegeven in de volg orde waarin u ze opvermeldt.</span><span class="sxs-lookup"><span data-stu-id="642f2-113">Ordered dictionaries differ from hash tables in that the keys always appear in the order in which you list them.</span></span> <span data-ttu-id="642f2-114">De volg orde van de sleutels in een hash-tabel is niet bepaald.</span><span class="sxs-lookup"><span data-stu-id="642f2-114">The order of keys in a hash table is not determined.</span></span>

<span data-ttu-id="642f2-115">De sleutels en waarde in hash-tabellen zijn ook .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="642f2-115">The keys and value in hash tables are also .NET objects.</span></span> <span data-ttu-id="642f2-116">Ze zijn meestal teken reeksen of gehele getallen, maar ze kunnen elk object type hebben.</span><span class="sxs-lookup"><span data-stu-id="642f2-116">They are most often strings or integers, but they can have any object type.</span></span> <span data-ttu-id="642f2-117">U kunt ook geneste hash-tabellen maken, waarbij de waarde van een sleutel een andere hash-tabel is.</span><span class="sxs-lookup"><span data-stu-id="642f2-117">You can also create nested hash tables, in which the value of a key is another hash table.</span></span>

<span data-ttu-id="642f2-118">Hash-tabellen worden vaak gebruikt, omdat ze zeer efficiënt zijn voor het zoeken en ophalen van gegevens.</span><span class="sxs-lookup"><span data-stu-id="642f2-118">Hash tables are frequently used because they are very efficient for finding and retrieving data.</span></span> <span data-ttu-id="642f2-119">U kunt hash-tabellen gebruiken om lijsten op te slaan en berekende eigenschappen in Power shell te maken.</span><span class="sxs-lookup"><span data-stu-id="642f2-119">You can use hash tables to store lists and to create calculated properties in PowerShell.</span></span> <span data-ttu-id="642f2-120">En Power Shell heeft een cmdlet, ConvertFrom-StringData, waarmee teken reeksen naar een hash-tabel worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="642f2-120">And, PowerShell has a cmdlet, ConvertFrom-StringData, that converts strings to a hash table.</span></span>

### <a name="syntax"></a><span data-ttu-id="642f2-121">Syntax</span><span class="sxs-lookup"><span data-stu-id="642f2-121">Syntax</span></span>

<span data-ttu-id="642f2-122">De syntaxis van een hash-tabel is als volgt:</span><span class="sxs-lookup"><span data-stu-id="642f2-122">The syntax of a hash table is as follows:</span></span>

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="642f2-123">De syntaxis van een geordende woorden lijst is als volgt:</span><span class="sxs-lookup"><span data-stu-id="642f2-123">The syntax of an ordered dictionary is as follows:</span></span>

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="642f2-124">Het kenmerk [gelastd] is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="642f2-124">The [ordered] attribute was introduced in PowerShell 3.0.</span></span>

### <a name="creating-hash-tables"></a><span data-ttu-id="642f2-125">Hash-tabellen maken</span><span class="sxs-lookup"><span data-stu-id="642f2-125">Creating Hash Tables</span></span>

<span data-ttu-id="642f2-126">Als u een hash-tabel wilt maken, volgt u deze richt lijnen:</span><span class="sxs-lookup"><span data-stu-id="642f2-126">To create a hash table, follow these guidelines:</span></span>

- <span data-ttu-id="642f2-127">Begin de hash-tabel met een apen staartje (@).</span><span class="sxs-lookup"><span data-stu-id="642f2-127">Begin the hash table with an at sign (@).</span></span>
- <span data-ttu-id="642f2-128">Plaats de hash-tabel tussen accolades ( {} ).</span><span class="sxs-lookup"><span data-stu-id="642f2-128">Enclose the hash table in braces ({}).</span></span>
- <span data-ttu-id="642f2-129">Voer een of meer sleutel-waardeparen in voor de inhoud van de hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="642f2-129">Enter one or more key/value pairs for the content of the hash table.</span></span>
- <span data-ttu-id="642f2-130">Gebruik een gelijkteken (=) als scheidings teken voor elke sleutel van de waarde.</span><span class="sxs-lookup"><span data-stu-id="642f2-130">Use an equal sign (=) to separate each key from its value.</span></span>
- <span data-ttu-id="642f2-131">Gebruik een punt komma (;) of een regel-afbreek punt om de sleutel/waarde-paren van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="642f2-131">Use a semicolon (;) or a line break to separate the key/value pairs.</span></span>
- <span data-ttu-id="642f2-132">De sleutel die spaties bevat moet tussen aanhalings tekens worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="642f2-132">Key that contains spaces must be enclosed in quotation marks.</span></span> <span data-ttu-id="642f2-133">De waarden moeten geldige Power shell-expressies zijn.</span><span class="sxs-lookup"><span data-stu-id="642f2-133">Values must be valid PowerShell expressions.</span></span> <span data-ttu-id="642f2-134">Teken reeksen moeten tussen aanhalings tekens worden weer gegeven, zelfs als ze geen spaties bevatten.</span><span class="sxs-lookup"><span data-stu-id="642f2-134">Strings must appear in quotation marks, even if they do not include spaces.</span></span>
- <span data-ttu-id="642f2-135">Als u de hash-tabel wilt beheren, slaat u deze op in een variabele.</span><span class="sxs-lookup"><span data-stu-id="642f2-135">To manage the hash table, save it in a variable.</span></span>
- <span data-ttu-id="642f2-136">Wanneer u een geordende hash-tabel aan een variabele toewijst, plaatst u het kenmerk [gelastd] vóór het @-teken.</span><span class="sxs-lookup"><span data-stu-id="642f2-136">When assigning an ordered hash table to a variable, place the [ordered] attribute before the "@" symbol.</span></span> <span data-ttu-id="642f2-137">Als u deze voor de naam van de variabele plaatst, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="642f2-137">If you place it before the variable name, the command fails.</span></span>

<span data-ttu-id="642f2-138">Als u een lege hash-tabel wilt maken in de waarde van $hash, typt u:</span><span class="sxs-lookup"><span data-stu-id="642f2-138">To create an empty hash table in the value of $hash, type:</span></span>

```powershell
$hash = @{}
```

<span data-ttu-id="642f2-139">U kunt ook sleutels en waarden aan een hash-tabel toevoegen wanneer u deze maakt.</span><span class="sxs-lookup"><span data-stu-id="642f2-139">You can also add keys and values to a hash table when you create it.</span></span> <span data-ttu-id="642f2-140">Met de volgende instructie maakt u bijvoorbeeld een hash-tabel met drie sleutels.</span><span class="sxs-lookup"><span data-stu-id="642f2-140">For example, the following statement creates a hash table with three keys.</span></span>

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a><span data-ttu-id="642f2-141">Geordende woorden lijsten maken</span><span class="sxs-lookup"><span data-stu-id="642f2-141">Creating Ordered Dictionaries</span></span>

<span data-ttu-id="642f2-142">U kunt een geordende woorden lijst maken door een object van het type OrderedDictionary toe te voegen, maar de eenvoudigste manier om een geordende woorden lijst te maken, is het kenmerk [besteld] te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="642f2-142">You can create an ordered dictionary by adding an object of the OrderedDictionary type, but the easiest way to create an ordered dictionary is use the [Ordered] attribute.</span></span>

<span data-ttu-id="642f2-143">Het kenmerk [gelastd] is geïntroduceerd in Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="642f2-143">The [ordered] attribute is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="642f2-144">Plaats het kenmerk direct voor het @-teken.</span><span class="sxs-lookup"><span data-stu-id="642f2-144">Place the attribute immediately before the "@" symbol.</span></span>

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

<span data-ttu-id="642f2-145">U kunt geordende woorden lijsten op dezelfde manier gebruiken als voor het gebruik van hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="642f2-145">You can use ordered dictionaries in the same way that you use hash tables.</span></span>
<span data-ttu-id="642f2-146">Een van beide typen kan worden gebruikt als de waarde van para meters die een hash-tabel of-woorden lijst (iDictionary) maken.</span><span class="sxs-lookup"><span data-stu-id="642f2-146">Either type can be used as the value of parameters that take a hash table or dictionary (iDictionary).</span></span>

<span data-ttu-id="642f2-147">U kunt het kenmerk [gelastd] niet gebruiken om een hash-tabel te converteren of te casten.</span><span class="sxs-lookup"><span data-stu-id="642f2-147">You cannot use the [ordered] attribute to convert or cast a hash table.</span></span> <span data-ttu-id="642f2-148">Als u het kenmerk besteld vóór de naam van de variabele plaatst, mislukt de opdracht met het volgende fout bericht.</span><span class="sxs-lookup"><span data-stu-id="642f2-148">If you place the ordered attribute before the variable name, the command fails with the following error message.</span></span>

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

<span data-ttu-id="642f2-149">Verplaats het kenmerk [gelastd] om de expressie te corrigeren.</span><span class="sxs-lookup"><span data-stu-id="642f2-149">To correct the expression, move the [ordered] attribute.</span></span>

```powershell
PS C:\> $hash = [ordered]@{}
```

<span data-ttu-id="642f2-150">U kunt een geordende woorden lijst converteren naar een hash-tabel, maar u kunt het bestelde kenmerk niet herstellen, zelfs niet als u de variabele wist en nieuwe waarden opgeeft.</span><span class="sxs-lookup"><span data-stu-id="642f2-150">You can cast an ordered dictionary to a hash table, but you cannot recover the ordered attribute, even if you clear the variable and enter new values.</span></span> <span data-ttu-id="642f2-151">Als u de volg orde wilt herstellen, moet u de variabele verwijderen en opnieuw maken.</span><span class="sxs-lookup"><span data-stu-id="642f2-151">To re-establish the order, you must remove and recreate the variable.</span></span>

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a><span data-ttu-id="642f2-152">Hash-tabellen weer geven</span><span class="sxs-lookup"><span data-stu-id="642f2-152">Displaying Hash Tables</span></span>

<span data-ttu-id="642f2-153">Als u een hash-tabel wilt weer geven die is opgeslagen in een variabele, typt u de naam van de variabele.</span><span class="sxs-lookup"><span data-stu-id="642f2-153">To display a hash table that is saved in a variable, type the variable name.</span></span>
<span data-ttu-id="642f2-154">Standaard worden hash-tabellen weer gegeven als een tabel met één kolom voor sleutels en één voor waarden.</span><span class="sxs-lookup"><span data-stu-id="642f2-154">By default, a hash tables is displayed as a table with one column for keys and one for values.</span></span>

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

<span data-ttu-id="642f2-155">Hash-tabellen hebben eigenschappen van sleutels en waarden.</span><span class="sxs-lookup"><span data-stu-id="642f2-155">Hash tables have Keys and Values properties.</span></span> <span data-ttu-id="642f2-156">Gebruik de punt notatie om alle sleutels of alle waarden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="642f2-156">Use dot notation to display all of the keys or all of the values.</span></span>

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

<span data-ttu-id="642f2-157">Elke sleutel naam is ook een eigenschap van de hash-tabel en de waarde ervan is de waarde van de eigenschap key-name.</span><span class="sxs-lookup"><span data-stu-id="642f2-157">Each key name is also a property of the hash table, and its value is the value of the key-name property.</span></span> <span data-ttu-id="642f2-158">Gebruik de volgende indeling om de eigenschaps waarden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="642f2-158">Use the following format to display the property values.</span></span>

```powershell
$hashtable.<key>
<value>
```

<span data-ttu-id="642f2-159">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="642f2-159">For example:</span></span>

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

<span data-ttu-id="642f2-160">Als de naam van de sleutel conflicteert met een van de eigenschaps namen van het type hash-tabel, kunt u gebruiken `PSBase` om toegang te krijgen tot die eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="642f2-160">If the key name collides with one of the property names of the HashTable type, you can use `PSBase` to access those properties.</span></span> <span data-ttu-id="642f2-161">Als de naam van de sleutel bijvoorbeeld is `keys` en u de verzameling sleutels wilt retour neren, gebruikt u de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="642f2-161">For example, if the key name is `keys` and you want to return the collection of Keys, use this syntax:</span></span>

```powershell
$hashtable.PSBase.Keys
```

<span data-ttu-id="642f2-162">Hash-tabellen hebben een eigenschap Count die het aantal sleutel-waardeparen in de hash-tabel aangeeft.</span><span class="sxs-lookup"><span data-stu-id="642f2-162">Hash tables have a Count property that indicates the number of key-value pairs in the hash table.</span></span>

```powershell
C:\PS> $hash.count
3
```

<span data-ttu-id="642f2-163">Hash-tabel tabellen zijn geen matrices. Daarom kunt u geen geheel getal als een index in de hashtabel gebruiken, maar wel een sleutel naam gebruiken om in de hashtabel te indexeren.</span><span class="sxs-lookup"><span data-stu-id="642f2-163">Hash table tables are not arrays, so you cannot use an integer as an index into the hash table, but you can use a key name to index into the hash table.</span></span>
<span data-ttu-id="642f2-164">Als de sleutel een teken reeks waarde is, plaatst u de sleutel naam tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="642f2-164">If the key is a string value, enclose the key name in quotation marks.</span></span>

<span data-ttu-id="642f2-165">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="642f2-165">For example:</span></span>

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a><span data-ttu-id="642f2-166">Sleutels en waarden toevoegen en verwijderen</span><span class="sxs-lookup"><span data-stu-id="642f2-166">Adding and Removing Keys and Values</span></span>

<span data-ttu-id="642f2-167">Als u sleutels en waarden wilt toevoegen aan een hash-tabel, gebruikt u de volgende opdracht indeling.</span><span class="sxs-lookup"><span data-stu-id="642f2-167">To add keys and values to a hash table, use the following command format.</span></span>

```powershell
$hash["<key>"] = "<value>"
```

<span data-ttu-id="642f2-168">Als u bijvoorbeeld een ' tijd sleutel ' met de waarde ' Now ' wilt toevoegen aan de hash-tabel, gebruikt u de volgende instructie indeling.</span><span class="sxs-lookup"><span data-stu-id="642f2-168">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash["Time"] = "Now"
```

<span data-ttu-id="642f2-169">U kunt ook sleutels en waarden toevoegen aan een hash-tabel met behulp van de methode Add van het object System. Collections. hashtabel.</span><span class="sxs-lookup"><span data-stu-id="642f2-169">You can also add keys and values to a hash table by using the Add method of the System.Collections.Hashtable object.</span></span> <span data-ttu-id="642f2-170">De methode Add heeft de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="642f2-170">The Add method has the following syntax:</span></span>

```powershell
Add(Key, Value)
```

<span data-ttu-id="642f2-171">Als u bijvoorbeeld een ' tijd sleutel ' met de waarde ' Now ' wilt toevoegen aan de hash-tabel, gebruikt u de volgende instructie indeling.</span><span class="sxs-lookup"><span data-stu-id="642f2-171">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash.Add("Time", "Now")
```

<span data-ttu-id="642f2-172">En u kunt sleutels en waarden toevoegen aan een hash-tabel met behulp van de operator voor optellen (+) om een hash-tabel toe te voegen aan een bestaande hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="642f2-172">And, you can add keys and values to a hash table by using the addition operator (+) to add a hash table to an existing hash table.</span></span> <span data-ttu-id="642f2-173">De volgende instructie voegt bijvoorbeeld een ' time '-sleutel met de waarde ' Now ' toe aan de hash-tabel in de variabele $hash.</span><span class="sxs-lookup"><span data-stu-id="642f2-173">For example, the following statement adds a "Time" key with a value of "Now" to the hash table in the $hash variable.</span></span>

```powershell
$hash = $hash + @{Time="Now"}
```

<span data-ttu-id="642f2-174">U kunt ook waarden toevoegen die zijn opgeslagen in variabelen.</span><span class="sxs-lookup"><span data-stu-id="642f2-174">You can also add values that are stored in variables.</span></span>

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

<span data-ttu-id="642f2-175">U kunt een operator voor aftrekken niet gebruiken om een sleutel/waarde-paar uit een hashtabel te verwijderen, maar met de methode Remove van het object hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="642f2-175">You cannot use a subtraction operator to remove a key/value pair from a hash table, but you can use the Remove method of the Hashtable object.</span></span> <span data-ttu-id="642f2-176">De methode Remove neemt de sleutel als waarde.</span><span class="sxs-lookup"><span data-stu-id="642f2-176">The Remove method takes the key as its value.</span></span>

<span data-ttu-id="642f2-177">De methode Remove heeft de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="642f2-177">The Remove method has the following syntax:</span></span>

```
Remove(Key)
```

<span data-ttu-id="642f2-178">Als u bijvoorbeeld de tijd = nu sleutel/waarde-paar uit de hash-tabel wilt verwijderen in de waarde van de variabele $hash, typt u:</span><span class="sxs-lookup"><span data-stu-id="642f2-178">For example, to remove the Time=Now key/value pair from the hash table in the value of the $hash variable, type:</span></span>

```powershell
$hash.Remove("Time")
```

<span data-ttu-id="642f2-179">U kunt alle eigenschappen en methoden van hashtabel-objecten in Power shell gebruiken, inclusief contains, Clear, clone en CopyTo.</span><span class="sxs-lookup"><span data-stu-id="642f2-179">You can use all of the properties and methods of Hashtable objects in PowerShell, including Contains, Clear, Clone, and CopyTo.</span></span> <span data-ttu-id="642f2-180">Zie ' System. Collections. hashtabel ' op MSDN voor meer informatie over Hashtable-objecten.</span><span class="sxs-lookup"><span data-stu-id="642f2-180">For more information about Hashtable objects, see "System.Collections.Hashtable" on MSDN.</span></span>

### <a name="object-types-in-hashtables"></a><span data-ttu-id="642f2-181">Object typen in hashtabellen</span><span class="sxs-lookup"><span data-stu-id="642f2-181">Object Types in HashTables</span></span>

<span data-ttu-id="642f2-182">De sleutels en waarden in een hash-tabel kunnen elk .NET-object type hebben en een enkele hash-tabel kan sleutels en waarden van meerdere typen hebben.</span><span class="sxs-lookup"><span data-stu-id="642f2-182">The keys and values in a hash table can have any .NET object type, and a single hash table can have keys and values of multiple types.</span></span>

<span data-ttu-id="642f2-183">Met de volgende instructie maakt u een hash-tabel met proces naam reeksen en proces object waarden en slaat u deze op in de \$ variabele p.</span><span class="sxs-lookup"><span data-stu-id="642f2-183">The following statement creates a hash table of process name strings and process object values and saves it in the \$p variable.</span></span>

```powershell
$p = @{"PowerShell" = (get-process PowerShell);
"Notepad" = (get-process notepad)}
```

<span data-ttu-id="642f2-184">U kunt de hash-tabel weer geven in \$ p en de eigenschappen van de sleutel naam gebruiken om de waarden weer te geven.</span><span class="sxs-lookup"><span data-stu-id="642f2-184">You can display the hash table in \$p and use the key-name properties to display the values.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

<span data-ttu-id="642f2-185">De sleutels in een hash-tabel kunnen ook elk .NET-type zijn.</span><span class="sxs-lookup"><span data-stu-id="642f2-185">The keys in a hash table can also be any .NET type.</span></span> <span data-ttu-id="642f2-186">De volgende instructie voegt een sleutel/waarde-paar toe aan de hash-tabel in de \$ variabele p.</span><span class="sxs-lookup"><span data-stu-id="642f2-186">The following statement adds a key/value pair to the hash table in the \$p variable.</span></span> <span data-ttu-id="642f2-187">De sleutel is een service object dat de WinRM-service vertegenwoordigt en de waarde is de huidige status van de service.</span><span class="sxs-lookup"><span data-stu-id="642f2-187">The key is a Service object that represents the WinRM service, and the value is the current status of the service.</span></span>

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

<span data-ttu-id="642f2-188">U kunt het nieuwe sleutel/waardepaar weer geven en openen met behulp van dezelfde methoden die u voor andere paren in de hash-tabel gebruikt.</span><span class="sxs-lookup"><span data-stu-id="642f2-188">You can display and access the new key/value pair by using the same methods that you use for other pairs in the hash table.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

<span data-ttu-id="642f2-189">De sleutels en waarden in een hash-tabel kunnen ook hash-objecten zijn.</span><span class="sxs-lookup"><span data-stu-id="642f2-189">The keys and values in a hash table can also be Hashtable objects.</span></span> <span data-ttu-id="642f2-190">De volgende instructie voegt een sleutel/waarde-paar toe aan de hash-tabel in de \$ p-variabele waarin de sleutel een teken reeks, Hash2 en de waarde is een hash-tabel met drie sleutel-waardeparen.</span><span class="sxs-lookup"><span data-stu-id="642f2-190">The following statement adds key/value pair to the hash table in the \$p variable in which the key is a string, Hash2, and the value is a hash table with three key/value pairs.</span></span>

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

<span data-ttu-id="642f2-191">U kunt de nieuwe waarden weer geven en openen met behulp van dezelfde methoden.</span><span class="sxs-lookup"><span data-stu-id="642f2-191">You can display and access the new values by using the same methods.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a><span data-ttu-id="642f2-192">Sleutels en waarden sorteren</span><span class="sxs-lookup"><span data-stu-id="642f2-192">Sorting Keys and Values</span></span>

<span data-ttu-id="642f2-193">De items in een hash-tabel zijn niet in de juiste volg orde.</span><span class="sxs-lookup"><span data-stu-id="642f2-193">The items in a hash table are intrinsically unordered.</span></span> <span data-ttu-id="642f2-194">De sleutel-waardeparen kunnen elke keer dat u ze weer geven in een andere volg orde worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="642f2-194">The key/value pairs might appear in a different order each time that you display them.</span></span>

<span data-ttu-id="642f2-195">Hoewel u een hashtabel kunt niet sorteren, kunt u de GetEnumerator-methode van hash-tabellen gebruiken om de sleutels en waarden op te sommen en vervolgens de cmdlet Sort-Object gebruiken om de opgesomde waarden voor weer gave te sorteren.</span><span class="sxs-lookup"><span data-stu-id="642f2-195">Although you cannot sort a hash table, you can use the GetEnumerator method of hash tables to enumerate the keys and values, and then use the Sort-Object cmdlet to sort the enumerated values for display.</span></span>

<span data-ttu-id="642f2-196">Met de volgende opdrachten worden bijvoorbeeld de sleutels en waarden in de hash-tabel in de \$ variabele p opgesomd en vervolgens de sleutels in alfabetische volg orde gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="642f2-196">For example, the following commands enumerate the keys and values in the hash table in the \$p variable and then sort the keys in alphabetical order.</span></span>

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

<span data-ttu-id="642f2-197">De volgende opdracht maakt gebruik van dezelfde procedure om de hash-waarden in aflopende volg orde te sorteren.</span><span class="sxs-lookup"><span data-stu-id="642f2-197">The following command uses the same procedure to sort the hash values in descending order.</span></span>

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a><span data-ttu-id="642f2-198">Objecten maken op basis van hash-tabellen</span><span class="sxs-lookup"><span data-stu-id="642f2-198">Creating Objects from Hash Tables</span></span>

<span data-ttu-id="642f2-199">Vanaf Power Shell 3,0 kunt u een object maken op basis van een hash-tabel met eigenschappen en eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="642f2-199">Beginning in PowerShell 3.0, you can create an object from a hash table of properties and property values.</span></span>

<span data-ttu-id="642f2-200">De syntaxis is als volgt:</span><span class="sxs-lookup"><span data-stu-id="642f2-200">The syntax is as follows:</span></span>

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

<span data-ttu-id="642f2-201">Deze methode werkt alleen voor klassen die een null-constructor hebben, dat wil zeggen een constructor zonder para meters.</span><span class="sxs-lookup"><span data-stu-id="642f2-201">This method works only for classes that have a null constructor, that is, a constructor that has no parameters.</span></span> <span data-ttu-id="642f2-202">De object eigenschappen moeten openbaar en instelbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="642f2-202">The object properties must be public and settable.</span></span>

<span data-ttu-id="642f2-203">Zie [about_Object_Creation](about_Object_Creation.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="642f2-203">For more information, see [about_Object_Creation](about_Object_Creation.md).</span></span>

### <a name="convertfrom-stringdata"></a><span data-ttu-id="642f2-204">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="642f2-204">ConvertFrom-StringData</span></span>

<span data-ttu-id="642f2-205">`ConvertFrom-StringData`Met de cmdlet wordt een teken reeks of hier een teken reeks van sleutel-waardeparen geconverteerd naar een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="642f2-205">The `ConvertFrom-StringData` cmdlet converts a string or a here-string of key/value pairs into a hash table.</span></span> <span data-ttu-id="642f2-206">U kunt de `ConvertFrom-StringData` cmdlet veilig gebruiken in het gedeelte gegevens van een script en u kunt deze met de cmdlet gebruiken `Import-LocalizedData` om gebruikers berichten weer te geven in de gebruikers interface cultuur (UI) van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="642f2-206">You can use the `ConvertFrom-StringData` cmdlet safely in the Data section of a script, and you can use it with the `Import-LocalizedData` cmdlet to display user messages in the user-interface (UI) culture of the current user.</span></span>

<span data-ttu-id="642f2-207">Hier-teken reeksen zijn vooral handig wanneer de waarden in de hash-tabel aanhalings tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="642f2-207">Here-strings are especially useful when the values in the hash table include quotation marks.</span></span> <span data-ttu-id="642f2-208">Zie [about_Quoting_Rules](about_Quoting_Rules.md)voor meer informatie over hier teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="642f2-208">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="642f2-209">In het volgende voor beeld ziet u hoe u een hier-reeks maakt van de gebruikers berichten in het vorige voor beeld en hoe u deze kunt gebruiken `ConvertFrom-StringData` om ze te converteren van een teken reeks naar een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="642f2-209">The following example shows how to create a here-string of the user messages in the previous example and how to use `ConvertFrom-StringData` to convert them from a string into a hash table.</span></span>

<span data-ttu-id="642f2-210">Met de volgende opdracht maakt u een teken reeks van de sleutel-waardeparen en slaat u deze op in de \$ teken reeks variabele.</span><span class="sxs-lookup"><span data-stu-id="642f2-210">The following command creates a here-string of the key/value pairs and then saves it in the \$string variable.</span></span>

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

<span data-ttu-id="642f2-211">Met deze opdracht wordt gebruikgemaakt van de cmdlet ConvertFrom-StringData om de hier-teken reeks te converteren naar een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="642f2-211">This command uses the ConvertFrom-StringData cmdlet to convert the here-string into a hash table.</span></span>

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

<span data-ttu-id="642f2-212">Zie [about_Quoting_Rules](about_Quoting_Rules.md)voor meer informatie over hier teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="642f2-212">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="642f2-213">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="642f2-213">SEE ALSO</span></span>

[<span data-ttu-id="642f2-214">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="642f2-214">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="642f2-215">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="642f2-215">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="642f2-216">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="642f2-216">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="642f2-217">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="642f2-217">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="642f2-218">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="642f2-218">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="642f2-219">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="642f2-219">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[<span data-ttu-id="642f2-220">System. Collections. hashtabel</span><span class="sxs-lookup"><span data-stu-id="642f2-220">System.Collections.Hashtable</span></span>](/dotnet/api/system.collections.hashtable)
