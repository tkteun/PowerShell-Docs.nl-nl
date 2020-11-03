---
description: Hiermee wordt het huidige bereik afgesloten, wat een functie, script of script blok kan zijn.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: c0c5b60163870e9352f0c3aa750d5603f29a81b1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252907"
---
# <a name="about-return"></a><span data-ttu-id="29efe-104">Over retour neren</span><span class="sxs-lookup"><span data-stu-id="29efe-104">About Return</span></span>

## <a name="short-description"></a><span data-ttu-id="29efe-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="29efe-105">Short description</span></span>

<span data-ttu-id="29efe-106">Hiermee wordt het huidige bereik afgesloten, wat een functie, script of script blok kan zijn.</span><span class="sxs-lookup"><span data-stu-id="29efe-106">Exits the current scope, which can be a function, script, or script block.</span></span>

## <a name="long-description"></a><span data-ttu-id="29efe-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="29efe-107">Long description</span></span>

<span data-ttu-id="29efe-108">Met het `return` sleutel woord wordt een functie, script of script blok afgesloten.</span><span class="sxs-lookup"><span data-stu-id="29efe-108">The `return` keyword exits a function, script, or script block.</span></span> <span data-ttu-id="29efe-109">Het kan worden gebruikt om een scope af te sluiten op een specifiek punt, om een waarde te retour neren of om aan te geven dat het einde van de scope is bereikt.</span><span class="sxs-lookup"><span data-stu-id="29efe-109">It can be used to exit a scope at a specific point, to return a value, or to indicate that the end of the scope has been reached.</span></span>

<span data-ttu-id="29efe-110">Gebruikers die bekend zijn met talen als C of C, \# willen mogelijk het `return` tref woord gebruiken om de logica te maken van het expliciet hebben van een bereik.</span><span class="sxs-lookup"><span data-stu-id="29efe-110">Users who are familiar with languages like C or C\# might want to use the `return` keyword to make the logic of leaving a scope explicit.</span></span>

<span data-ttu-id="29efe-111">In Power shell worden de resultaten van elke instructie geretourneerd als uitvoer, zelfs zonder een instructie die het sleutel woord Return bevat.</span><span class="sxs-lookup"><span data-stu-id="29efe-111">In PowerShell, the results of each statement are returned as output, even without a statement that contains the Return keyword.</span></span> <span data-ttu-id="29efe-112">Talen zoals C of C \# retour neren alleen de waarde of waarden die zijn opgegeven met het `return` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="29efe-112">Languages like C or C\# return only the value or values that are specified by the `return` keyword.</span></span>

> [!NOTE]
> <span data-ttu-id="29efe-113">Vanaf Power shell 5,0, Power shell toegevoegde taal voor het definiëren van klassen, met behulp van formele syntaxis.</span><span class="sxs-lookup"><span data-stu-id="29efe-113">Beginning in PowerShell 5.0, PowerShell added language for defining classes, by using formal syntax.</span></span>  <span data-ttu-id="29efe-114">In de context van een Power shell-klasse is er geen uitvoer van een methode, behalve wat u opgeeft met behulp van een- `return` instructie.</span><span class="sxs-lookup"><span data-stu-id="29efe-114">In the context of a PowerShell class, nothing is output from a method except what you specify using a `return` statement.</span></span> <span data-ttu-id="29efe-115">Meer informatie over Power shell-klassen vindt u in [about_Classes](about_Classes.md).</span><span class="sxs-lookup"><span data-stu-id="29efe-115">You can read more about PowerShell classes in [about_Classes](about_Classes.md).</span></span>

### <a name="syntax"></a><span data-ttu-id="29efe-116">Syntax</span><span class="sxs-lookup"><span data-stu-id="29efe-116">Syntax</span></span>

<span data-ttu-id="29efe-117">De syntaxis voor het `return` sleutel woord is als volgt:</span><span class="sxs-lookup"><span data-stu-id="29efe-117">The syntax for the `return` keyword is as follows:</span></span>

```
return [<expression>]
```

<span data-ttu-id="29efe-118">Het `return` tref woord kan alleen worden weer gegeven of kan als volgt worden gevolgd door een waarde of expressie:</span><span class="sxs-lookup"><span data-stu-id="29efe-118">The `return` keyword can appear alone, or it can be followed by a value or expression, as follows:</span></span>

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a><span data-ttu-id="29efe-119">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="29efe-119">Examples</span></span>

<span data-ttu-id="29efe-120">In het volgende voor beeld wordt het `return` sleutel woord gebruikt om een functie op een specifiek punt af te sluiten als aan een voorwaardelijke waarde is voldaan.</span><span class="sxs-lookup"><span data-stu-id="29efe-120">The following example uses the `return` keyword to exit a function at a specific point if a conditional is met.</span></span> <span data-ttu-id="29efe-121">Oneven getallen worden niet vermenigvuldigd omdat de instructie return wordt afgesloten voordat die instructie kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="29efe-121">Odd numbers are not multiplied because the return statement exits before that statement can execute.</span></span>

```powershell
function MultiplyEven
{
    param($number)

    if ($number % 2) { return "$number is not even" }
    $number * 2
}

1..10 | ForEach-Object {MultiplyEven -Number $_}
```

```output
1 is not even
4
3 is not even
8
5 is not even
12
7 is not even
16
9 is not even
20
```

<span data-ttu-id="29efe-122">In Power shell kunnen waarden worden geretourneerd, zelfs als het `return` sleutel woord niet wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="29efe-122">In PowerShell, values can be returned even if the `return` keyword is not used.</span></span>
<span data-ttu-id="29efe-123">De resultaten van elke instructie worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="29efe-123">The results of each statement are returned.</span></span> <span data-ttu-id="29efe-124">Met de volgende instructies wordt bijvoorbeeld de waarde van de `$a` variabele geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="29efe-124">For example, the following statements return the value of the `$a` variable:</span></span>

```powershell
$a
return
```

<span data-ttu-id="29efe-125">De volgende instructie retourneert ook de waarde `$a` :</span><span class="sxs-lookup"><span data-stu-id="29efe-125">The following statement also returns the value of `$a`:</span></span>

```powershell
return $a
```

<span data-ttu-id="29efe-126">Het volgende voor beeld bevat een instructie die is bedoeld om de gebruiker te laten weten dat de functie een berekening uitvoert:</span><span class="sxs-lookup"><span data-stu-id="29efe-126">The following example includes a statement intended to let the user know that the function is performing a calculation:</span></span>

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

<span data-ttu-id="29efe-127">Het wacht even.</span><span class="sxs-lookup"><span data-stu-id="29efe-127">The "Please wait.</span></span> <span data-ttu-id="29efe-128">Bezig met berekenen... ' de teken reeks wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="29efe-128">Working on calculation..." string is not displayed.</span></span> <span data-ttu-id="29efe-129">In plaats daarvan wordt deze toegewezen aan de `$a` variabele, zoals in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="29efe-129">Instead, it is assigned to the `$a` variable, as in the following example:</span></span>

```
PS> $a
Please wait. Working on calculation...
87
```

<span data-ttu-id="29efe-130">Zowel de informatielijke teken reeks als het resultaat van de berekening worden geretourneerd door de functie en toegewezen aan de `$a` variabele.</span><span class="sxs-lookup"><span data-stu-id="29efe-130">Both the informational string and the result of the calculation are returned by the function and assigned to the `$a` variable.</span></span>

<span data-ttu-id="29efe-131">Als u een bericht binnen uw functie wilt weer geven, vanaf Power shell 5,0, kunt u de stream gebruiken `Information` .</span><span class="sxs-lookup"><span data-stu-id="29efe-131">If you would like to display a message within your function, beginning in PowerShell 5.0, you can use the `Information` stream.</span></span> <span data-ttu-id="29efe-132">De onderstaande code corrigeert het bovenstaande voor beeld met behulp `Write-Information` van de cmdlet met een `InformationAction` van de **door** gaande.</span><span class="sxs-lookup"><span data-stu-id="29efe-132">The code below corrects the above example using the `Write-Information` cmdlet with a `InformationAction` of **Continue**.</span></span>

```powershell
function calculation {
    param ($value)

    Write-Information "Please wait. Working on calculation..." -InformationAction Continue
    $value += 73
    return $value
}

$a = calculation 14
```

```output
Please wait. Working on calculation...
C:\PS> $a
87
```

### <a name="return-values-and-the-pipeline"></a><span data-ttu-id="29efe-133">Retour waarden en de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="29efe-133">Return values and the Pipeline</span></span>

<span data-ttu-id="29efe-134">Wanneer u een verzameling uit het script blok of de-functie retourneert, worden de leden automatisch door Power shell opgeheven en door de pijp lijn per keer door gegeven.</span><span class="sxs-lookup"><span data-stu-id="29efe-134">When you return a collection from your script block or function, PowerShell automatically unrolls the members and passes them one at a time through the pipeline.</span></span> <span data-ttu-id="29efe-135">Dit wordt veroorzaakt door de eenmalige verwerking van Power shell.</span><span class="sxs-lookup"><span data-stu-id="29efe-135">This is due to PowerShell's one-at-a-time processing.</span></span> <span data-ttu-id="29efe-136">Zie [about_pipelines](about_pipelines.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="29efe-136">For more information, see [about_pipelines](about_pipelines.md).</span></span>

<span data-ttu-id="29efe-137">Dit concept wordt geïllustreerd door de volgende voorbeeld functie waarmee een matrix met getallen wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="29efe-137">This concept is illustrated by the following sample function that returns an array of numbers.</span></span> <span data-ttu-id="29efe-138">De uitvoer van de functie wordt door gegeven aan de `Measure-Object` cmdlet waarmee het aantal objecten in de pijp lijn wordt geteld.</span><span class="sxs-lookup"><span data-stu-id="29efe-138">The output from the function is piped to the `Measure-Object` cmdlet which counts the number of objects in the pipeline.</span></span>

```powershell
function Test-Return
{
    $array = 1,2,3
    return $array
}
Test-Return | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

<span data-ttu-id="29efe-139">Gebruik een van de volgende twee methoden om een script blok of functie te dwingen om de verzameling te retour neren als één object naar de pijp lijn:</span><span class="sxs-lookup"><span data-stu-id="29efe-139">To force a script block or function to return collection as a single object to the pipeline, use one of the following two methods:</span></span>

- <span data-ttu-id="29efe-140">Expressie voor unaire matrix</span><span class="sxs-lookup"><span data-stu-id="29efe-140">Unary array expression</span></span>

  <span data-ttu-id="29efe-141">Als u een unaire expressie gebruikt, kunt u de retour waarde naar de pijp lijn verzenden als een enkel object, zoals wordt geïllustreerd door het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="29efe-141">Utilizing a unary expression you can send your return value down the pipeline as a single object as illustrated by the following example.</span></span>

  ```powershell
  function Test-Return
  {
      $array = 1,2,3
      return (, $array)
  }
  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

- <span data-ttu-id="29efe-142">`Write-Output` met de para meter ' niet **opsommen** '.</span><span class="sxs-lookup"><span data-stu-id="29efe-142">`Write-Output` with **NoEnumerate** parameter.</span></span>

  <span data-ttu-id="29efe-143">U kunt de cmdlet ook gebruiken `Write-Output` met de para meter voor de **opsomming** .</span><span class="sxs-lookup"><span data-stu-id="29efe-143">You can also use the `Write-Output` cmdlet with the **NoEnumerate** parameter.</span></span> <span data-ttu-id="29efe-144">In het volgende voor beeld wordt de `Measure-Object` cmdlet gebruikt om de objecten te tellen die vanuit de voorbeeld functie naar de pijp lijn worden verzonden met het `return` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="29efe-144">The example below uses the `Measure-Object` cmdlet to count the objects sent to the pipeline from the sample function by the `return` keyword.</span></span>

  ```powershell
  function Test-Return
  {
      $array = 1, 2, 3
      return Write-Output -NoEnumerate $array
  }

  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

## <a name="see-also"></a><span data-ttu-id="29efe-145">Zie ook</span><span class="sxs-lookup"><span data-stu-id="29efe-145">See also</span></span>

[<span data-ttu-id="29efe-146">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="29efe-146">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="29efe-147">about_Functions</span><span class="sxs-lookup"><span data-stu-id="29efe-147">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="29efe-148">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="29efe-148">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="29efe-149">about_Classes</span><span class="sxs-lookup"><span data-stu-id="29efe-149">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="29efe-150">Write-Information</span><span class="sxs-lookup"><span data-stu-id="29efe-150">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)

[<span data-ttu-id="29efe-151">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="29efe-151">about_Script_Blocks</span></span>](about_Script_Blocks.md)

