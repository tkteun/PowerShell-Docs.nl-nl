---
description: Hiermee wordt het huidige bereik afgesloten, wat een functie, script of script blok kan zijn.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: 032f3c694096e11e2800be941eb76b1f442b5088
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706223"
---
# <a name="about-return"></a><span data-ttu-id="92a0c-103">Over retour neren</span><span class="sxs-lookup"><span data-stu-id="92a0c-103">About Return</span></span>

## <a name="short-description"></a><span data-ttu-id="92a0c-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="92a0c-104">Short description</span></span>

<span data-ttu-id="92a0c-105">Hiermee wordt het huidige bereik afgesloten, wat een functie, script of script blok kan zijn.</span><span class="sxs-lookup"><span data-stu-id="92a0c-105">Exits the current scope, which can be a function, script, or script block.</span></span>

## <a name="long-description"></a><span data-ttu-id="92a0c-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="92a0c-106">Long description</span></span>

<span data-ttu-id="92a0c-107">Met het `return` sleutel woord wordt een functie, script of script blok afgesloten.</span><span class="sxs-lookup"><span data-stu-id="92a0c-107">The `return` keyword exits a function, script, or script block.</span></span> <span data-ttu-id="92a0c-108">Het kan worden gebruikt om een scope af te sluiten op een specifiek punt, om een waarde te retour neren of om aan te geven dat het einde van de scope is bereikt.</span><span class="sxs-lookup"><span data-stu-id="92a0c-108">It can be used to exit a scope at a specific point, to return a value, or to indicate that the end of the scope has been reached.</span></span>

<span data-ttu-id="92a0c-109">Gebruikers die bekend zijn met talen als C of C, \# willen mogelijk het `return` tref woord gebruiken om de logica te maken van het expliciet hebben van een bereik.</span><span class="sxs-lookup"><span data-stu-id="92a0c-109">Users who are familiar with languages like C or C\# might want to use the `return` keyword to make the logic of leaving a scope explicit.</span></span>

<span data-ttu-id="92a0c-110">In Power shell worden de resultaten van elke instructie geretourneerd als uitvoer, zelfs zonder een instructie die het sleutel woord Return bevat.</span><span class="sxs-lookup"><span data-stu-id="92a0c-110">In PowerShell, the results of each statement are returned as output, even without a statement that contains the Return keyword.</span></span> <span data-ttu-id="92a0c-111">Talen zoals C of C \# retour neren alleen de waarde of waarden die zijn opgegeven met het `return` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="92a0c-111">Languages like C or C\# return only the value or values that are specified by the `return` keyword.</span></span>

> [!NOTE]
> <span data-ttu-id="92a0c-112">Vanaf Power shell 5,0, Power shell toegevoegde taal voor het definiëren van klassen, met behulp van formele syntaxis.</span><span class="sxs-lookup"><span data-stu-id="92a0c-112">Beginning in PowerShell 5.0, PowerShell added language for defining classes, by using formal syntax.</span></span>  <span data-ttu-id="92a0c-113">In de context van een Power shell-klasse is er geen uitvoer van een methode, behalve wat u opgeeft met behulp van een- `return` instructie.</span><span class="sxs-lookup"><span data-stu-id="92a0c-113">In the context of a PowerShell class, nothing is output from a method except what you specify using a `return` statement.</span></span> <span data-ttu-id="92a0c-114">Meer informatie over Power shell-klassen vindt u in [about_Classes](about_Classes.md).</span><span class="sxs-lookup"><span data-stu-id="92a0c-114">You can read more about PowerShell classes in [about_Classes](about_Classes.md).</span></span>

### <a name="syntax"></a><span data-ttu-id="92a0c-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="92a0c-115">Syntax</span></span>

<span data-ttu-id="92a0c-116">De syntaxis voor het `return` sleutel woord is als volgt:</span><span class="sxs-lookup"><span data-stu-id="92a0c-116">The syntax for the `return` keyword is as follows:</span></span>

```
return [<expression>]
```

<span data-ttu-id="92a0c-117">Het `return` tref woord kan alleen worden weer gegeven of kan als volgt worden gevolgd door een waarde of expressie:</span><span class="sxs-lookup"><span data-stu-id="92a0c-117">The `return` keyword can appear alone, or it can be followed by a value or expression, as follows:</span></span>

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a><span data-ttu-id="92a0c-118">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="92a0c-118">Examples</span></span>

<span data-ttu-id="92a0c-119">In het volgende voor beeld wordt het `return` sleutel woord gebruikt om een functie op een specifiek punt af te sluiten als aan een voorwaardelijke waarde is voldaan.</span><span class="sxs-lookup"><span data-stu-id="92a0c-119">The following example uses the `return` keyword to exit a function at a specific point if a conditional is met.</span></span> <span data-ttu-id="92a0c-120">Oneven getallen worden niet vermenigvuldigd omdat de instructie return wordt afgesloten voordat die instructie kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="92a0c-120">Odd numbers are not multiplied because the return statement exits before that statement can execute.</span></span>

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

<span data-ttu-id="92a0c-121">In Power shell kunnen waarden worden geretourneerd, zelfs als het `return` sleutel woord niet wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="92a0c-121">In PowerShell, values can be returned even if the `return` keyword is not used.</span></span>
<span data-ttu-id="92a0c-122">De resultaten van elke instructie worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="92a0c-122">The results of each statement are returned.</span></span> <span data-ttu-id="92a0c-123">Met de volgende instructies wordt bijvoorbeeld de waarde van de `$a` variabele geretourneerd:</span><span class="sxs-lookup"><span data-stu-id="92a0c-123">For example, the following statements return the value of the `$a` variable:</span></span>

```powershell
$a
return
```

<span data-ttu-id="92a0c-124">De volgende instructie retourneert ook de waarde `$a` :</span><span class="sxs-lookup"><span data-stu-id="92a0c-124">The following statement also returns the value of `$a`:</span></span>

```powershell
return $a
```

<span data-ttu-id="92a0c-125">Het volgende voor beeld bevat een instructie die is bedoeld om de gebruiker te laten weten dat de functie een berekening uitvoert:</span><span class="sxs-lookup"><span data-stu-id="92a0c-125">The following example includes a statement intended to let the user know that the function is performing a calculation:</span></span>

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

<span data-ttu-id="92a0c-126">Het wacht even.</span><span class="sxs-lookup"><span data-stu-id="92a0c-126">The "Please wait.</span></span> <span data-ttu-id="92a0c-127">Bezig met berekenen... ' de teken reeks wordt niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="92a0c-127">Working on calculation..." string is not displayed.</span></span> <span data-ttu-id="92a0c-128">In plaats daarvan wordt deze toegewezen aan de `$a` variabele, zoals in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="92a0c-128">Instead, it is assigned to the `$a` variable, as in the following example:</span></span>

```
PS> $a
Please wait. Working on calculation...
87
```

<span data-ttu-id="92a0c-129">Zowel de informatielijke teken reeks als het resultaat van de berekening worden geretourneerd door de functie en toegewezen aan de `$a` variabele.</span><span class="sxs-lookup"><span data-stu-id="92a0c-129">Both the informational string and the result of the calculation are returned by the function and assigned to the `$a` variable.</span></span>

<span data-ttu-id="92a0c-130">Als u een bericht binnen uw functie wilt weer geven, vanaf Power shell 5,0, kunt u de stream gebruiken `Information` .</span><span class="sxs-lookup"><span data-stu-id="92a0c-130">If you would like to display a message within your function, beginning in PowerShell 5.0, you can use the `Information` stream.</span></span> <span data-ttu-id="92a0c-131">De onderstaande code corrigeert het bovenstaande voor beeld met behulp `Write-Information` van de cmdlet met een `InformationAction` van de **door** gaande.</span><span class="sxs-lookup"><span data-stu-id="92a0c-131">The code below corrects the above example using the `Write-Information` cmdlet with a `InformationAction` of **Continue**.</span></span>

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

### <a name="return-values-and-the-pipeline"></a><span data-ttu-id="92a0c-132">Retour waarden en de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="92a0c-132">Return values and the Pipeline</span></span>

<span data-ttu-id="92a0c-133">Wanneer u een verzameling uit het script blok of de-functie retourneert, worden de leden automatisch door Power shell opgeheven en door de pijp lijn per keer door gegeven.</span><span class="sxs-lookup"><span data-stu-id="92a0c-133">When you return a collection from your script block or function, PowerShell automatically unrolls the members and passes them one at a time through the pipeline.</span></span> <span data-ttu-id="92a0c-134">Dit wordt veroorzaakt door de eenmalige verwerking van Power shell.</span><span class="sxs-lookup"><span data-stu-id="92a0c-134">This is due to PowerShell's one-at-a-time processing.</span></span> <span data-ttu-id="92a0c-135">Zie [about_pipelines](about_pipelines.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="92a0c-135">For more information, see [about_pipelines](about_pipelines.md).</span></span>

<span data-ttu-id="92a0c-136">Dit concept wordt geïllustreerd door de volgende voorbeeld functie waarmee een matrix met getallen wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="92a0c-136">This concept is illustrated by the following sample function that returns an array of numbers.</span></span> <span data-ttu-id="92a0c-137">De uitvoer van de functie wordt door gegeven aan de `Measure-Object` cmdlet waarmee het aantal objecten in de pijp lijn wordt geteld.</span><span class="sxs-lookup"><span data-stu-id="92a0c-137">The output from the function is piped to the `Measure-Object` cmdlet which counts the number of objects in the pipeline.</span></span>

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

<span data-ttu-id="92a0c-138">Gebruik een van de volgende twee methoden om een script blok of functie te dwingen om de verzameling te retour neren als één object naar de pijp lijn:</span><span class="sxs-lookup"><span data-stu-id="92a0c-138">To force a script block or function to return collection as a single object to the pipeline, use one of the following two methods:</span></span>

- <span data-ttu-id="92a0c-139">Expressie voor unaire matrix</span><span class="sxs-lookup"><span data-stu-id="92a0c-139">Unary array expression</span></span>

  <span data-ttu-id="92a0c-140">Als u een unaire expressie gebruikt, kunt u de retour waarde naar de pijp lijn verzenden als een enkel object, zoals wordt geïllustreerd door het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="92a0c-140">Utilizing a unary expression you can send your return value down the pipeline as a single object as illustrated by the following example.</span></span>

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

- <span data-ttu-id="92a0c-141">`Write-Output` met de para meter ' niet **opsommen** '.</span><span class="sxs-lookup"><span data-stu-id="92a0c-141">`Write-Output` with **NoEnumerate** parameter.</span></span>

  <span data-ttu-id="92a0c-142">U kunt de cmdlet ook gebruiken `Write-Output` met de para meter voor de **opsomming** .</span><span class="sxs-lookup"><span data-stu-id="92a0c-142">You can also use the `Write-Output` cmdlet with the **NoEnumerate** parameter.</span></span> <span data-ttu-id="92a0c-143">In het volgende voor beeld wordt de `Measure-Object` cmdlet gebruikt om de objecten te tellen die vanuit de voorbeeld functie naar de pijp lijn worden verzonden met het `return` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="92a0c-143">The example below uses the `Measure-Object` cmdlet to count the objects sent to the pipeline from the sample function by the `return` keyword.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="92a0c-144">Zie ook</span><span class="sxs-lookup"><span data-stu-id="92a0c-144">See also</span></span>

[<span data-ttu-id="92a0c-145">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="92a0c-145">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="92a0c-146">about_Functions</span><span class="sxs-lookup"><span data-stu-id="92a0c-146">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="92a0c-147">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="92a0c-147">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="92a0c-148">about_Classes</span><span class="sxs-lookup"><span data-stu-id="92a0c-148">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="92a0c-149">Write-Information</span><span class="sxs-lookup"><span data-stu-id="92a0c-149">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)

[<span data-ttu-id="92a0c-150">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="92a0c-150">about_Script_Blocks</span></span>](about_Script_Blocks.md)

