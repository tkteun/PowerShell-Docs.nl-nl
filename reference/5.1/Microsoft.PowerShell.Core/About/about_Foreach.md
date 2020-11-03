---
description: Beschrijft een taal opdracht die u kunt gebruiken om alle items in een verzameling items te door lopen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach
ms.openlocfilehash: f1f00df8b0f07dd945994860897584d883ef2ce4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252621"
---
# <a name="about-foreach"></a><span data-ttu-id="d3e6a-104">Over ForEach</span><span class="sxs-lookup"><span data-stu-id="d3e6a-104">About ForEach</span></span>

## <a name="short-description"></a><span data-ttu-id="d3e6a-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="d3e6a-105">Short description</span></span>
<span data-ttu-id="d3e6a-106">Beschrijft een taal opdracht die u kunt gebruiken om alle items in een verzameling items te door lopen.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-106">Describes a language command you can use to traverse all the items in a collection of items.</span></span>

## <a name="long-description"></a><span data-ttu-id="d3e6a-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="d3e6a-107">Long description</span></span>

<span data-ttu-id="d3e6a-108">De `Foreach` instructie (ook wel een `Foreach` lus genoemd) is een taal constructie voor het stapsgewijs door lopen van een reeks waarden in een verzameling items.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-108">The `Foreach` statement (also known as a `Foreach` loop) is a language construct for stepping through (iterating) a series of values in a collection of items.</span></span>

<span data-ttu-id="d3e6a-109">Het eenvoudigste en meest gang bare type verzameling dat u kunt door bladeren, is een matrix.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-109">The simplest and most typical type of collection to traverse is an array.</span></span>
<span data-ttu-id="d3e6a-110">Binnen een `Foreach` lus is het gebruikelijk om een of meer opdrachten uit te voeren voor elk item in een matrix.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-110">Within a `Foreach` loop, it is common to run one or more commands against each item in an array.</span></span>

## <a name="syntax"></a><span data-ttu-id="d3e6a-111">Syntax</span><span class="sxs-lookup"><span data-stu-id="d3e6a-111">Syntax</span></span>

<span data-ttu-id="d3e6a-112">Hieronder ziet u de `ForEach` syntaxis:</span><span class="sxs-lookup"><span data-stu-id="d3e6a-112">The following shows the `ForEach` syntax:</span></span>

```
foreach ($<item> in $<collection>){<statement list>}
```

<span data-ttu-id="d3e6a-113">Het deel van de `ForEach` instructie tussen haakjes vertegenwoordigt een variabele en een verzameling die moet worden herhaald.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-113">The part of the `ForEach` statement enclosed in parenthesis represents a variable and a collection to iterate.</span></span> <span data-ttu-id="d3e6a-114">Power Shell maakt de variabele `$<item>` automatisch wanneer de `Foreach` lus wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-114">PowerShell creates the variable `$<item>` automatically when the `Foreach` loop runs.</span></span> <span data-ttu-id="d3e6a-115">Vóór elke iteratie door de lus wordt de variabele ingesteld op een waarde in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-115">Prior to each iteration through the loop, the variable is set to a value in the collection.</span></span>
<span data-ttu-id="d3e6a-116">Het blok dat volgt `Foreach` op een instructie `{<statement list>}` bevat een reeks opdrachten die moeten worden uitgevoerd voor elk item in een verzameling.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-116">The block following a `Foreach` statement `{<statement list>}` contains a set of commands to execute against each item in a collection.</span></span>

### <a name="examples"></a><span data-ttu-id="d3e6a-117">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="d3e6a-117">Examples</span></span>

<span data-ttu-id="d3e6a-118">`Foreach`Met de lus in het volgende voor beeld worden de waarden in de matrix weer gegeven `$letterArray` .</span><span class="sxs-lookup"><span data-stu-id="d3e6a-118">For example, the `Foreach` loop in the following example displays the values in the `$letterArray` array.</span></span>

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

<span data-ttu-id="d3e6a-119">In dit voor beeld `$letterArray` wordt de matrix gemaakt en geïnitialiseerd met de teken reeks waarden `"a"` , `"b"` , `"c"` en `"d"` .</span><span class="sxs-lookup"><span data-stu-id="d3e6a-119">In this example, the `$letterArray` array is created and initialized with the string values `"a"`, `"b"`, `"c"`, and `"d"`.</span></span> <span data-ttu-id="d3e6a-120">De eerste keer `Foreach` dat de instructie wordt uitgevoerd, wordt de `$letter` variabele ingesteld op het eerste item in `$letterArray` ( `"a"` ).</span><span class="sxs-lookup"><span data-stu-id="d3e6a-120">The first time the `Foreach` statement runs, it sets the `$letter` variable equal to the first item in `$letterArray` (`"a"`).</span></span> <span data-ttu-id="d3e6a-121">Vervolgens wordt de cmdlet gebruikt `Write-Host` om de letter a weer te geven.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-121">Then, it uses the `Write-Host` cmdlet to display the letter a.</span></span> <span data-ttu-id="d3e6a-122">De volgende keer door de lus, `$letter` is ingesteld op `"b"` , enzovoort.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-122">The next time through the loop, `$letter` is set to `"b"`, and so on.</span></span> <span data-ttu-id="d3e6a-123">Wanneer de `Foreach` lus de letter d weergeeft, wordt de lus door Power shell afgesloten.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-123">After the `Foreach` loop displays the letter d, PowerShell exits the loop.</span></span>

<span data-ttu-id="d3e6a-124">De volledige `Foreach` instructie moet op één regel worden weer gegeven om deze uit te voeren als een opdracht in de Power shell-opdracht prompt.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-124">The entire `Foreach` statement must appear on a single line to run it as a command at the PowerShell command prompt.</span></span> <span data-ttu-id="d3e6a-125">De volledige `Foreach` instructie hoeft niet op één regel te worden weer gegeven als u in plaats daarvan de opdracht in een. ps1-script bestand plaatst.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-125">The entire `Foreach` statement does not have to appear on a single line if you place the command in a .ps1 script file instead.</span></span>

<span data-ttu-id="d3e6a-126">`Foreach` instructies kunnen ook worden gebruikt in combi natie met cmdlets die een verzameling items retour neren.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-126">`Foreach` statements can also be used together with cmdlets that return a collection of items.</span></span> <span data-ttu-id="d3e6a-127">In het volgende voor beeld wordt de instructie foreach stapsgewijs door de lijst met items weer gegeven die door de cmdlet worden geretourneerd `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="d3e6a-127">In the following example, the Foreach statement steps through the list of items that is returned by the `Get-ChildItem` cmdlet.</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

<span data-ttu-id="d3e6a-128">U kunt het voor beeld verfijnen met behulp van een `If` instructie om de geretourneerde resultaten te beperken.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-128">You can refine the example by using an `If` statement to limit the results that are returned.</span></span> <span data-ttu-id="d3e6a-129">In het volgende voor beeld `Foreach` voert de instructie dezelfde herhalings bewerking uit als in het vorige voor beeld, maar wordt een `If` instructie toegevoegd om de resultaten te beperken tot bestanden die groter zijn dan 100 KB (KB):</span><span class="sxs-lookup"><span data-stu-id="d3e6a-129">In the following example, the `Foreach` statement performs the same looping operation as the previous example, but it adds an `If` statement to limit the results to files that are greater than 100 kilobytes (KB):</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

<span data-ttu-id="d3e6a-130">In dit voor beeld `Foreach` gebruikt de lus een eigenschap van de `$file` variabele om een vergelijkings bewerking () uit te voeren `$file.length -gt 100KB` .</span><span class="sxs-lookup"><span data-stu-id="d3e6a-130">In this example, the `Foreach` loop uses a property of the `$file` variable to perform a comparison operation (`$file.length -gt 100KB`).</span></span> <span data-ttu-id="d3e6a-131">De `$file` variabele bevat alle eigenschappen in het object dat door de cmdlet wordt geretourneerd `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="d3e6a-131">The `$file` variable contains all the properties in the object that is returned by the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="d3e6a-132">Daarom kunt u meer dan alleen een bestands naam retour neren.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-132">Therefore, you can return more than just a file name.</span></span>
<span data-ttu-id="d3e6a-133">In het volgende voor beeld retourneert Power shell de lengte en de tijd van laatste toegang in de instructie lijst:</span><span class="sxs-lookup"><span data-stu-id="d3e6a-133">In the next example, PowerShell returns the length and the last access time inside the statement list:</span></span>

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
    Write-Host $file.length
    Write-Host $file.lastaccesstime
  }
}
```

<span data-ttu-id="d3e6a-134">In dit voor beeld bent u niet beperkt tot het uitvoeren van één opdracht in een instructie lijst.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-134">In this example, you are not limited to running a single command in a statement list.</span></span>

<span data-ttu-id="d3e6a-135">U kunt ook een variabele buiten een `Foreach` lus gebruiken en de variabele in de lus ophogen.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-135">You can also use a variable outside a `Foreach` loop and increment the variable inside the loop.</span></span> <span data-ttu-id="d3e6a-136">In het volgende voor beeld worden bestanden geteld met een grootte van 100 KB:</span><span class="sxs-lookup"><span data-stu-id="d3e6a-136">The following example counts files over 100 KB in size:</span></span>

```powershell
$i = 0
foreach ($file in Get-ChildItem) {
  if ($file.length -gt 100KB) {
    Write-Host $file "file size:" ($file.length / 1024).ToString("F0") KB
    $i = $i + 1
  }
}

if ($i -ne 0) {
  Write-Host
  Write-Host $i " file(s) over 100 KB in the current directory."
}
else {
  Write-Host "No files greater than 100 KB in the current directory."
}
```

<span data-ttu-id="d3e6a-137">In het vorige voor beeld `$i` is de variabele ingesteld op `0` buiten de lus en wordt de variabele in de lus verhoogd voor elk gevonden bestand dat groter is dan 100 kB.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-137">In the preceding example, the `$i` variable is set to `0` outside the loop, and the variable is incremented inside the loop for each file that is found that is larger than 100 KB.</span></span> <span data-ttu-id="d3e6a-138">Wanneer de lus wordt afgesloten, wordt `If` met een instructie de waarde van het `$i` aantal bestanden in 100 KB weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-138">When the loop exits, an `If` statement evaluates the value of `$i` to display a count of all the files over 100 KB.</span></span> <span data-ttu-id="d3e6a-139">Of er wordt een bericht weer gegeven waarin wordt vermeld dat er geen bestanden meer dan 100 KB zijn gevonden.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-139">Or, it displays a message stating that no files over 100 KB were found.</span></span>

<span data-ttu-id="d3e6a-140">In het vorige voor beeld ziet u ook hoe u de bestands lengte kunt indelen:</span><span class="sxs-lookup"><span data-stu-id="d3e6a-140">The previous example also demonstrates how to format the file length results:</span></span>

```powershell
($file.length / 1024).ToString("F0")
```

<span data-ttu-id="d3e6a-141">De waarde wordt gedeeld door 1.024 voor het weer geven van de resultaten in kB in plaats van bytes, en de resulterende waarde wordt vervolgens opgemaakt met de specificatie van de vaste-komma indeling om decimale waarden uit het resultaat te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-141">The value is divided by 1,024 to show the results in kilobytes rather than bytes, and the resulting value is then formatted using the fixed-point format specifier to remove any decimal values from the result.</span></span> <span data-ttu-id="d3e6a-142">Met de 0 wordt de indelings aanduiding geen decimale posities weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-142">The 0 makes the format specifier show no decimal places.</span></span>

<span data-ttu-id="d3e6a-143">In het volgende voor beeld worden met de gedefinieerde functie Power shell-scripts en script modules geparseerd en wordt de locatie van de functies die zijn opgenomen in.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-143">In the following example, the function defined parses PowerShell scripts and script modules and returns the location of functions contained within.</span></span> <span data-ttu-id="d3e6a-144">In het voor beeld ziet u hoe u de `MoveNext` methode (die `skip X` op een lus werkt `For` ) en de `Current` eigenschap van de `$foreach` variabele binnen een foreach-script blok gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-144">The example demonstrates how to use the `MoveNext` method (which works similarly to `skip X` on a `For` loop) and the `Current` property of the `$foreach` variable inside of a foreach script block.</span></span> <span data-ttu-id="d3e6a-145">De functie voor beeld kan functies vinden in een script, zelfs als er sprake is van ongebruikelijke of niet-consistente functie definities die meerdere regels omvatten.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-145">The example function can find functions in a script even if there are unusually- or inconsistently-spaced function definitions that span multiple lines.</span></span>

<span data-ttu-id="d3e6a-146">Zie [using enumeraties](about_Automatic_Variables.md#using-enumerators)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d3e6a-146">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators).</span></span>

```powershell
function Get-FunctionPosition {
  [CmdletBinding()]
  [OutputType('FunctionPosition')]
  param(
    [Parameter(Position = 0, Mandatory,
      ValueFromPipeline, ValueFromPipelineByPropertyName)]
    [ValidateNotNullOrEmpty()]
    [Alias('PSPath')]
    [System.String[]]
    $Path
  )

  process {
    try {
      $filesToProcess = if ($_ -is [System.IO.FileSystemInfo]) {
        Write-Verbose "From pipeline"
        $_
      } else {
        Write-Verbose "From parameter, $Path"
        Get-Item -Path $Path
      }
      $parser = [System.Management.Automation.Language.Parser]
      Write-Verbose "lets start the foreach loop on `$filesToProcess with $($filesToProcess.count) as count"
      foreach ($item in $filesToProcess) {
        Write-Verbose "$item"
        if ($item.PSIsContainer -or
            $item.Extension -notin @('.ps1', '.psm1')) {
          continue
        }
        $tokens = $errors = $null
        $parser::ParseFile($item.FullName, ([REF]$tokens),
          ([REF]$errors)) | Out-Null
        if ($errors) {
          $msg = "File '{0}' has {1} parser errors." -f $item.FullName,
            $errors.Count
          Write-Warning $msg
        }
        :tokenLoop foreach ($token in $tokens) {
          if ($token.Kind -ne 'Function') {
            continue
          }
          $position = $token.Extent.StartLineNumber
          do {
            if (-not $foreach.MoveNext()) {
              break tokenLoop
            }
            $token = $foreach.Current
          } until ($token.Kind -in @('Generic', 'Identifier'))
          $functionPosition = [pscustomobject]@{
            Name       = $token.Text
            LineNumber = $position
            Path       = $item.FullName
          }
          Add-Member -InputObject $functionPosition `
            -TypeName FunctionPosition -PassThru
        }
      }
    }
    catch {
      throw
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="d3e6a-147">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="d3e6a-147">SEE ALSO</span></span>

[<span data-ttu-id="d3e6a-148">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="d3e6a-148">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="d3e6a-149">about_If</span><span class="sxs-lookup"><span data-stu-id="d3e6a-149">about_If</span></span>](about_If.md)

[<span data-ttu-id="d3e6a-150">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="d3e6a-150">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
