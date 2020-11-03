---
description: Beschrijft het koppelen van pijp lijnen met `&&` de `||` Opera tors en in Power shell.
ms.date: 09/30/2019
schema: 2.0.0
Locale: en-US
keywords: powershell,cmdlet
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: 38895ff9acda9ead031c9be58904ac132364a584
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252436"
---
# <a name="about-pipeline-chain-operators"></a><span data-ttu-id="14daa-104">Over pijplijn keten operators</span><span class="sxs-lookup"><span data-stu-id="14daa-104">About Pipeline Chain Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="14daa-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="14daa-105">Short description</span></span>

<span data-ttu-id="14daa-106">Beschrijft het koppelen van pijp lijnen met `&&` de `||` Opera tors en in Power shell.</span><span class="sxs-lookup"><span data-stu-id="14daa-106">Describes chaining pipelines with the `&&` and `||` operators in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="14daa-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="14daa-107">Long description</span></span>

<span data-ttu-id="14daa-108">Vanaf Power shell 7 implementeert Power shell de `&&` `||` Opera tors en om pijp lijnen voorwaardelijk te koppelen.</span><span class="sxs-lookup"><span data-stu-id="14daa-108">Beginning in PowerShell 7, PowerShell implements the `&&` and `||` operators to conditionally chain pipelines.</span></span> <span data-ttu-id="14daa-109">Deze opera tors zijn bekend in Power shell als *Opera tors voor pipeline-ketens* en zijn vergelijkbaar met [en-of-lijsten](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) in POSIX-shells zoals bash, zsh en sh, evenals [voorwaardelijke verwerkings symbolen](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) in de Windows-opdracht shell (cmd.exe).</span><span class="sxs-lookup"><span data-stu-id="14daa-109">These operators are known in PowerShell as *pipeline chain operators* , and are similar to [AND-OR lists](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) in POSIX shells like bash, zsh and sh, as well as [conditional processing symbols](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) in the Windows Command Shell (cmd.exe).</span></span>

<span data-ttu-id="14daa-110">De `&&` operator voert de rechter pijplijn uit, als de pijplijn is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="14daa-110">The `&&` operator executes the right-hand pipeline, if the left-hand pipeline succeeded.</span></span> <span data-ttu-id="14daa-111">De operator voert daarentegen `||` de rechter pijp lijn uit als de linker pijp lijn is mislukt.</span><span class="sxs-lookup"><span data-stu-id="14daa-111">Conversely, the `||` operator executes the right-hand pipeline if the left-hand pipeline failed.</span></span>

<span data-ttu-id="14daa-112">Deze opera tors gebruiken `$?` de `$LASTEXITCODE` variabelen en om te bepalen of een pijp lijn is mislukt.</span><span class="sxs-lookup"><span data-stu-id="14daa-112">These operators use the `$?` and `$LASTEXITCODE` variables to determine if a pipeline failed.</span></span> <span data-ttu-id="14daa-113">Hierdoor kunt u ze gebruiken met systeem eigen opdrachten en niet alleen met cmdlets of functies.</span><span class="sxs-lookup"><span data-stu-id="14daa-113">This allows you to use them with native commands and not just with cmdlets or functions.</span></span> <span data-ttu-id="14daa-114">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="14daa-114">For example:</span></span>

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a><span data-ttu-id="14daa-115">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="14daa-115">Examples</span></span>

#### <a name="two-successful-commands"></a><span data-ttu-id="14daa-116">Twee geslaagde opdrachten</span><span class="sxs-lookup"><span data-stu-id="14daa-116">Two successful commands</span></span>

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a><span data-ttu-id="14daa-117">Eerste opdracht mislukt, waardoor de tweede niet wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="14daa-117">First command fails, causing second not to be executed</span></span>

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a><span data-ttu-id="14daa-118">De eerste opdracht is geslaagd, waardoor de tweede opdracht niet wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="14daa-118">First command succeeds, so the second command is not executed</span></span>

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a><span data-ttu-id="14daa-119">De eerste opdracht mislukt, dus de tweede opdracht wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="14daa-119">First command fails, so the second command is executed</span></span>

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

<span data-ttu-id="14daa-120">Pijp lijn geslaagd wordt gedefinieerd door de waarde van de `$?` variabele, die Power shell automatisch instelt nadat een pijp lijn is uitgevoerd op basis van de uitvoerings status.</span><span class="sxs-lookup"><span data-stu-id="14daa-120">Pipeline success is defined by the value of the `$?` variable, which PowerShell automatically sets after executing a pipeline based on its execution status.</span></span>
<span data-ttu-id="14daa-121">Dit betekent dat de Opera tors voor pijplijn keten de volgende gelijkwaardigheid hebben:</span><span class="sxs-lookup"><span data-stu-id="14daa-121">This means that pipeline chain operators have the following equivalence:</span></span>

```powershell
Test-Command '1' && Test-Command '2'
```

<span data-ttu-id="14daa-122">werkt hetzelfde als</span><span class="sxs-lookup"><span data-stu-id="14daa-122">works the same as</span></span>

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

<span data-ttu-id="14daa-123">en</span><span class="sxs-lookup"><span data-stu-id="14daa-123">and</span></span>

```powershell
Test-Command '1' || Test-Command '2'
```

<span data-ttu-id="14daa-124">werkt hetzelfde als</span><span class="sxs-lookup"><span data-stu-id="14daa-124">works the same as</span></span>

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a><span data-ttu-id="14daa-125">Toewijzing van pijp lijn ketens</span><span class="sxs-lookup"><span data-stu-id="14daa-125">Assignment from pipeline chains</span></span>

<span data-ttu-id="14daa-126">Wanneer u een variabele toewijst vanuit een pijplijn keten, neemt de samen voeging van alle pijp lijnen in de keten toe:</span><span class="sxs-lookup"><span data-stu-id="14daa-126">Assigning a variable from a pipeline chain takes the concatenation of all the pipelines in the chain:</span></span>

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

<span data-ttu-id="14daa-127">Als er een fout optreedt tijdens het beëindigen van een script tijdens toewijzing vanuit een pijplijn keten, mislukt de toewijzing:</span><span class="sxs-lookup"><span data-stu-id="14daa-127">If a script-terminating error occurs during assignment from a pipeline chain, the assignment does not succeed:</span></span>

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a><span data-ttu-id="14daa-128">Operator syntaxis en prioriteit</span><span class="sxs-lookup"><span data-stu-id="14daa-128">Operator syntax and precedence</span></span>

<span data-ttu-id="14daa-129">In tegens telling tot andere opera tors `&&` en `||` op pijp lijnen, in plaats van op expressies zoals `+` of `-and` , bijvoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="14daa-129">Unlike other operators, `&&` and `||` operate on pipelines, rather than on expressions like `+` or `-and`, for example.</span></span>

<span data-ttu-id="14daa-130">`&&` en `||` hebben een lagere prioriteit dan sluizen ( `|` ) of omleiding ( `>` ), maar een hogere prioriteit dan de taak operators ( `&` ), de toewijzing ( `=` ) of een punt komma ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="14daa-130">`&&` and `||` have a lower precedence than piping (`|`) or redirection (`>`), but a higher precedence than job operators (`&`), assignment (`=`) or semicolons (`;`).</span></span> <span data-ttu-id="14daa-131">Dit betekent dat pijp lijnen in een pijplijn keten afzonderlijk kunnen worden omgeleid en dat volledige pijplijn ketens kunnen worden geachtergrondd, toegewezen aan variabelen of gescheiden als-instructies.</span><span class="sxs-lookup"><span data-stu-id="14daa-131">This means that pipelines within a pipeline chain can be individually redirected, and that entire pipeline chains can be backgrounded, assigned to variables, or separated as statements.</span></span>

<span data-ttu-id="14daa-132">Als u de syntaxis met een lagere prioriteit wilt gebruiken in een pijplijn keten, overweeg dan het gebruik van haakjes `(...)` .</span><span class="sxs-lookup"><span data-stu-id="14daa-132">To use lower precedence syntax within a pipeline chain, consider the use of parentheses `(...)`.</span></span>
<span data-ttu-id="14daa-133">Als u een instructie wilt insluiten in een pijplijn keten, kunt u ook een subexpressie `$(...)` gebruiken.</span><span class="sxs-lookup"><span data-stu-id="14daa-133">Similarly, to embed a statement within a pipeline chain, a subexpression `$(...)` can be used.</span></span>
<span data-ttu-id="14daa-134">Dit kan handig zijn voor het combi neren van systeem eigen opdrachten met controle stroom:</span><span class="sxs-lookup"><span data-stu-id="14daa-134">This can be useful for combining native commands with control flow:</span></span>

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

<span data-ttu-id="14daa-135">Vanaf Power shell 7 is het gedrag van deze syntaxis gewijzigd, zodat het `$?` is ingesteld op verwachting als een opdracht is geslaagd of mislukt tussen haakjes of een subexpressie.</span><span class="sxs-lookup"><span data-stu-id="14daa-135">As of PowerShell 7, the behaviour of these syntaxes has been changed so that `$?` is set as expected when a command succeeds or fails within parentheses or a subexpression.</span></span>

<span data-ttu-id="14daa-136">Net als de meeste andere opera tors in Power shell `&&` en `||` zijn ook *links gekoppeld* , wat betekent dat ze aan de linkerkant worden gegroepeerd.</span><span class="sxs-lookup"><span data-stu-id="14daa-136">Like most other operators in PowerShell, `&&` and `||` are also *left-associative* , meaning they group from the left.</span></span> <span data-ttu-id="14daa-137">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="14daa-137">For example:</span></span>

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

<span data-ttu-id="14daa-138">wordt als volgt gegroepeerd:</span><span class="sxs-lookup"><span data-stu-id="14daa-138">will group as:</span></span>

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

<span data-ttu-id="14daa-139">komt overeen met:</span><span class="sxs-lookup"><span data-stu-id="14daa-139">being equivalent to:</span></span>

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a><span data-ttu-id="14daa-140">Fout interactie</span><span class="sxs-lookup"><span data-stu-id="14daa-140">Error interaction</span></span>

<span data-ttu-id="14daa-141">Opera tors voor pijplijn ketens nemen geen fouten op.</span><span class="sxs-lookup"><span data-stu-id="14daa-141">Pipeline chain operators do not absorb errors.</span></span> <span data-ttu-id="14daa-142">Wanneer een instructie in een pijplijn keten een script beëindigt, wordt de pijplijn keten beëindigd.</span><span class="sxs-lookup"><span data-stu-id="14daa-142">When a statement in a pipeline chain throws a script-terminating error, the pipeline chain is terminated.</span></span>

<span data-ttu-id="14daa-143">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="14daa-143">For example:</span></span>

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

<span data-ttu-id="14daa-144">Zelfs wanneer de fout is opgetreden, wordt de pipeline-keten nog steeds beëindigd:</span><span class="sxs-lookup"><span data-stu-id="14daa-144">Even when the error is caught, the pipeline chain is still terminated:</span></span>

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

<span data-ttu-id="14daa-145">Als een fout niet wordt beëindigd of als er alleen een pijp lijn wordt beëindigd, blijft de pijplijn keten de waarde van `$?` :</span><span class="sxs-lookup"><span data-stu-id="14daa-145">If an error is non-terminating, or only terminates a pipeline, the pipeline chain continues, respecting the value of `$?`:</span></span>

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a><span data-ttu-id="14daa-146">Pijp lijnen koppelen in plaats van opdrachten</span><span class="sxs-lookup"><span data-stu-id="14daa-146">Chaining pipelines rather than commands</span></span>

<span data-ttu-id="14daa-147">Pijplijn keten operators op basis van hun naam kunnen worden gebruikt voor het koppelen van pijp lijnen, in plaats van alleen op opdrachten.</span><span class="sxs-lookup"><span data-stu-id="14daa-147">Pipeline chain operators, by their name, can be used to chain pipelines, rather than just commands.</span></span> <span data-ttu-id="14daa-148">Dit komt overeen met het gedrag van andere shells, maar het *kan lastig zijn om het volgende te* bepalen:</span><span class="sxs-lookup"><span data-stu-id="14daa-148">This matches the behavior of other shells, but can make *success* harder to determine:</span></span>

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

<span data-ttu-id="14daa-149">Houd er rekening mee dat `Write-Output 'All done!'` niet wordt uitgevoerd, omdat er `Test-NotTwo` een fout is opgetreden bij het genereren van de niet-afsluit fouten.</span><span class="sxs-lookup"><span data-stu-id="14daa-149">Note that `Write-Output 'All done!'` is not executed, since `Test-NotTwo` is deemed to have failed after generating the non-terminating error.</span></span>

## <a name="see-also"></a><span data-ttu-id="14daa-150">Zie ook</span><span class="sxs-lookup"><span data-stu-id="14daa-150">See also</span></span>

- [<span data-ttu-id="14daa-151">about_Operators</span><span class="sxs-lookup"><span data-stu-id="14daa-151">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="14daa-152">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="14daa-152">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="14daa-153">about_pipelines</span><span class="sxs-lookup"><span data-stu-id="14daa-153">about_pipelines</span></span>](about_pipelines.md)

