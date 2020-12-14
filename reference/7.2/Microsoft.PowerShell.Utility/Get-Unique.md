---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: de827d956e6e813e84d87bb1578ee7d596fe2f15
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705930"
---
# <span data-ttu-id="35c88-102">Get-Unique</span><span class="sxs-lookup"><span data-stu-id="35c88-102">Get-Unique</span></span>

## <span data-ttu-id="35c88-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="35c88-103">SYNOPSIS</span></span>
<span data-ttu-id="35c88-104">Retourneert unieke items uit een gesorteerde lijst.</span><span class="sxs-lookup"><span data-stu-id="35c88-104">Returns unique items from a sorted list.</span></span>

## <span data-ttu-id="35c88-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="35c88-105">SYNTAX</span></span>

### <span data-ttu-id="35c88-106">AsString (standaard)</span><span class="sxs-lookup"><span data-stu-id="35c88-106">AsString (Default)</span></span>

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### <span data-ttu-id="35c88-107">UniqueByType</span><span class="sxs-lookup"><span data-stu-id="35c88-107">UniqueByType</span></span>

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## <span data-ttu-id="35c88-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="35c88-108">DESCRIPTION</span></span>

<span data-ttu-id="35c88-109">De `Get-Unique` cmdlet vergelijkt elk item in een gesorteerde lijst met het volgende item, elimineert dubbele waarden en retourneert slechts één exemplaar van elk item.</span><span class="sxs-lookup"><span data-stu-id="35c88-109">The `Get-Unique` cmdlet compares each item in a sorted list to the next item, eliminates duplicates, and returns only one instance of each item.</span></span> <span data-ttu-id="35c88-110">De lijst moet worden gesorteerd om de cmdlet goed te laten werken.</span><span class="sxs-lookup"><span data-stu-id="35c88-110">The list must be sorted for the cmdlet to work properly.</span></span>

<span data-ttu-id="35c88-111">`Get-Unique` is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="35c88-111">`Get-Unique` is case-sensitive.</span></span> <span data-ttu-id="35c88-112">Als gevolg hiervan worden teken reeksen die alleen in Character-hoofdletter verschillen, als uniek beschouwd.</span><span class="sxs-lookup"><span data-stu-id="35c88-112">As a result, strings that differ only in character casing are considered to be unique.</span></span>

## <span data-ttu-id="35c88-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="35c88-113">EXAMPLES</span></span>

### <span data-ttu-id="35c88-114">Voor beeld 1: unieke woorden in een tekst bestand ophalen</span><span class="sxs-lookup"><span data-stu-id="35c88-114">Example 1: Get unique words in a text file</span></span>

<span data-ttu-id="35c88-115">Met deze opdrachten wordt het aantal unieke woorden in een tekst bestand gevonden.</span><span class="sxs-lookup"><span data-stu-id="35c88-115">These commands find the number of unique words in a text file.</span></span>

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

<span data-ttu-id="35c88-116">Met de eerste opdracht wordt de inhoud van het File.txt bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="35c88-116">The first command gets the content of the File.txt file.</span></span> <span data-ttu-id="35c88-117">Hiermee wordt elke tekst regel geconverteerd naar kleine letters en vervolgens elk woord gesplitst op een afzonderlijke regel aan de spatie ("").</span><span class="sxs-lookup"><span data-stu-id="35c88-117">It converts each line of text to lowercase letters and then splits each word onto a separate line at the space (" ").</span></span> <span data-ttu-id="35c88-118">Vervolgens wordt de resulterende lijst alfabetisch gesorteerd (de standaard instelling) en wordt de `Get-Unique` cmdlet gebruikt voor het elimineren van dubbele woorden.</span><span class="sxs-lookup"><span data-stu-id="35c88-118">Then, it sorts the resulting list alphabetically (the default) and uses the `Get-Unique` cmdlet to eliminate any duplicate words.</span></span> <span data-ttu-id="35c88-119">De resultaten worden opgeslagen in de `$A` variabele.</span><span class="sxs-lookup"><span data-stu-id="35c88-119">The results are stored in the `$A` variable.</span></span>

<span data-ttu-id="35c88-120">De tweede opdracht maakt gebruik van de eigenschap **Count** van de verzameling teken reeksen in `$A` om te bepalen hoeveel items zich in bevinden `$A` .</span><span class="sxs-lookup"><span data-stu-id="35c88-120">The second command uses the **Count** property of the collection of strings in `$A` to determine how many items are in `$A`.</span></span>

### <span data-ttu-id="35c88-121">Voor beeld 2: unieke gehele getallen in een matrix ophalen</span><span class="sxs-lookup"><span data-stu-id="35c88-121">Example 2: Get unique integers in an array</span></span>

<span data-ttu-id="35c88-122">Met deze opdracht vindt u de unieke leden van de set met gehele getallen.</span><span class="sxs-lookup"><span data-stu-id="35c88-122">This command finds the unique members of the set of integers.</span></span>

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

<span data-ttu-id="35c88-123">De eerste opdracht neemt een matrix van gehele getallen op op de opdracht regel, stuurt deze door naar de `Sort-Object` cmdlet die moet worden gesorteerd en sluizen deze naar `Get-Unique` , waardoor dubbele vermeldingen worden geëlimineerd.</span><span class="sxs-lookup"><span data-stu-id="35c88-123">The first command takes an array of integers typed at the command line, pipes them to the `Sort-Object` cmdlet to be sorted, and then pipes them to `Get-Unique`, which eliminates duplicate entries.</span></span>

### <span data-ttu-id="35c88-124">Voor beeld 3: unieke object typen in een directory ophalen</span><span class="sxs-lookup"><span data-stu-id="35c88-124">Example 3: Get unique object types in a directory</span></span>

<span data-ttu-id="35c88-125">Met deze opdracht wordt de `Get-ChildItem` cmdlet gebruikt om de inhoud van de lokale map op te halen, inclusief bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="35c88-125">This command uses the `Get-ChildItem` cmdlet to retrieve the contents of the local directory, which includes files and directories.</span></span>

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

<span data-ttu-id="35c88-126">De pijplijn operator (|) verzendt de resultaten naar de `Sort-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="35c88-126">The pipeline operator (|) sends the results to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="35c88-127">`$_.GetType()`Met de instructie wordt de **gettype** -methode toegepast op elk bestand of elke map.</span><span class="sxs-lookup"><span data-stu-id="35c88-127">The `$_.GetType()` statement applies the **GetType** method to each file or directory.</span></span> <span data-ttu-id="35c88-128">Vervolgens worden `Sort-Object` de items gesorteerd op type.</span><span class="sxs-lookup"><span data-stu-id="35c88-128">Then, `Sort-Object` sorts the items by type.</span></span> <span data-ttu-id="35c88-129">Een andere pijplijn operator stuurt de resultaten naar `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="35c88-129">Another pipeline operator sends the results to `Get-Unique`.</span></span> <span data-ttu-id="35c88-130">De **OnType** para meter direct `Get-Unique` retourneert slechts één object van elk type.</span><span class="sxs-lookup"><span data-stu-id="35c88-130">The **OnType** parameter directs `Get-Unique` to return only one object of each type.</span></span>

### <span data-ttu-id="35c88-131">Voor beeld 4: unieke processen ophalen</span><span class="sxs-lookup"><span data-stu-id="35c88-131">Example 4: Get unique processes</span></span>

<span data-ttu-id="35c88-132">Met deze opdracht worden de namen opgehaald van processen die op de computer worden uitgevoerd, waarbij duplicaten worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="35c88-132">This command gets the names of processes running on the computer with duplicates eliminated.</span></span>

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

<span data-ttu-id="35c88-133">`Get-Process`Met de opdracht worden alle processen op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="35c88-133">The `Get-Process` command gets all of the processes on the computer.</span></span> <span data-ttu-id="35c88-134">Met de pijplijn operator (|) wordt het resultaat door gegeven aan `Sort-Object` , dat standaard de processen alfabetisch op procesnaam sorteert.</span><span class="sxs-lookup"><span data-stu-id="35c88-134">The pipeline operator (|) passes the result to `Sort-Object`, which, by default, sorts the processes alphabetically by ProcessName.</span></span> <span data-ttu-id="35c88-135">De resultaten worden door gegeven aan de `Select-Object` cmdlet, waarmee alleen de waarden van de eigenschap proces naam van elk object worden geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="35c88-135">The results are piped to the `Select-Object` cmdlet, which selects only the values of the ProcessName property of each object.</span></span> <span data-ttu-id="35c88-136">De resultaten worden vervolgens gepiped om `Get-Unique` dubbele waarden te elimineren.</span><span class="sxs-lookup"><span data-stu-id="35c88-136">The results are then piped to `Get-Unique` to eliminate duplicates.</span></span>

<span data-ttu-id="35c88-137">De para meter **AsString** geeft `Get-Unique` aan dat de **Procesnaam** waarden moeten worden behandeld als teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="35c88-137">The **AsString** parameter tells `Get-Unique` to treat the **ProcessName** values as strings.</span></span>
<span data-ttu-id="35c88-138">Zonder deze para meter worden `Get-Unique` de waarden van de **proces** naam als objecten behandeld en wordt slechts één exemplaar van het object geretourneerd, dat wil zeggen, de eerste proces naam in de lijst.</span><span class="sxs-lookup"><span data-stu-id="35c88-138">Without this parameter, `Get-Unique` treats the **ProcessName** values as objects and returns only one instance of the object, that is, the first process name in the list.</span></span>

## <span data-ttu-id="35c88-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="35c88-139">PARAMETERS</span></span>

### <span data-ttu-id="35c88-140">-AsString</span><span class="sxs-lookup"><span data-stu-id="35c88-140">-AsString</span></span>

<span data-ttu-id="35c88-141">Geeft aan dat deze cmdlet de gegevens als een teken reeks gebruikt.</span><span class="sxs-lookup"><span data-stu-id="35c88-141">Indicates that this cmdlet uses the data as a string.</span></span> <span data-ttu-id="35c88-142">Als u deze para meter niet opgeeft, worden gegevens behandeld als een object, dus wanneer u een verzameling objecten van hetzelfde type verzendt naar `Get-Unique` , bijvoorbeeld een verzameling bestanden, wordt er slechts één (de eerste) geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="35c88-142">Without this parameter, data is treated as an object, so when you submit a collection of objects of the same type to `Get-Unique`, such as a collection of files, it returns just one (the first).</span></span> <span data-ttu-id="35c88-143">U kunt deze para meter gebruiken om de unieke waarden van object eigenschappen, zoals de bestands namen, te vinden.</span><span class="sxs-lookup"><span data-stu-id="35c88-143">You can use this parameter to find the unique values of object properties, such as the file names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35c88-144">-Input object</span><span class="sxs-lookup"><span data-stu-id="35c88-144">-InputObject</span></span>

<span data-ttu-id="35c88-145">Hiermee geeft u de invoer voor `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="35c88-145">Specifies input for `Get-Unique`.</span></span> <span data-ttu-id="35c88-146">Voer een variabele in die de objecten bevat of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="35c88-146">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="35c88-147">Met deze cmdlet wordt de invoer behandeld die is verzonden met behulp van **input object** als een-verzameling.</span><span class="sxs-lookup"><span data-stu-id="35c88-147">This cmdlet treats the input submitted by using **InputObject** as a collection.</span></span> <span data-ttu-id="35c88-148">Er worden geen afzonderlijke items in de verzameling opgesomd.</span><span class="sxs-lookup"><span data-stu-id="35c88-148">it does not enumerate individual items in the collection.</span></span> <span data-ttu-id="35c88-149">Omdat de verzameling één item is, wordt de invoer die is verzonden met behulp van **input object** altijd ongewijzigd geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="35c88-149">Because the collection is a single item, input submitted by using **InputObject** is always returned unchanged.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="35c88-150">-OnType</span><span class="sxs-lookup"><span data-stu-id="35c88-150">-OnType</span></span>

<span data-ttu-id="35c88-151">Geeft aan dat deze cmdlet slechts één object van elk type retourneert.</span><span class="sxs-lookup"><span data-stu-id="35c88-151">Indicates that this cmdlet returns only one object of each type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="35c88-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="35c88-152">CommonParameters</span></span>

<span data-ttu-id="35c88-153">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="35c88-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="35c88-154">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="35c88-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="35c88-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="35c88-155">INPUTS</span></span>

### <span data-ttu-id="35c88-156">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="35c88-156">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="35c88-157">U kunt elk type object door sluizen naar `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="35c88-157">You can pipe any type of object to `Get-Unique`.</span></span>

## <span data-ttu-id="35c88-158">UITVOER</span><span class="sxs-lookup"><span data-stu-id="35c88-158">OUTPUTS</span></span>

### <span data-ttu-id="35c88-159">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="35c88-159">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="35c88-160">Het type van het object dat wordt `Get-Unique` geretourneerd, wordt bepaald door de invoer.</span><span class="sxs-lookup"><span data-stu-id="35c88-160">The type of object that `Get-Unique` returns is determined by the input.</span></span>

## <span data-ttu-id="35c88-161">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="35c88-161">NOTES</span></span>

<span data-ttu-id="35c88-162">U kunt ook verwijzen naar `Get-Unique` de ingebouwde alias `gu` .</span><span class="sxs-lookup"><span data-stu-id="35c88-162">You can also refer to `Get-Unique` by its built-in alias, `gu`.</span></span> <span data-ttu-id="35c88-163">Zie [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="35c88-163">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="35c88-164">Als u een lijst wilt sorteren, gebruikt u sorteer-object.</span><span class="sxs-lookup"><span data-stu-id="35c88-164">To sort a list, use Sort-Object.</span></span> <span data-ttu-id="35c88-165">U kunt ook de **unieke** para meter van gebruiken `Sort-Object` om de unieke items in een lijst te vinden.</span><span class="sxs-lookup"><span data-stu-id="35c88-165">You can also use the **Unique** parameter of `Sort-Object` to find the unique items in a list.</span></span>

## <span data-ttu-id="35c88-166">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="35c88-166">RELATED LINKS</span></span>

[<span data-ttu-id="35c88-167">Select-Object</span><span class="sxs-lookup"><span data-stu-id="35c88-167">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="35c88-168">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="35c88-168">Sort-Object</span></span>](Sort-Object.md)

