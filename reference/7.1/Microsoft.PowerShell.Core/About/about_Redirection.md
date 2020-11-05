---
description: Hierin wordt uitgelegd hoe u de uitvoer omleidt van Power shell naar tekst bestanden.
keywords: Power shell, cmdlet
Locale: en-US
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: 1a532aeacf6347023c95905c82aa1f221835a729
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253048"
---
# <a name="about-redirection"></a><span data-ttu-id="9b182-104">Over omleiding</span><span class="sxs-lookup"><span data-stu-id="9b182-104">About Redirection</span></span>

## <a name="short-description"></a><span data-ttu-id="9b182-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="9b182-105">Short description</span></span>
<span data-ttu-id="9b182-106">Hierin wordt uitgelegd hoe u de uitvoer omleidt van Power shell naar tekst bestanden.</span><span class="sxs-lookup"><span data-stu-id="9b182-106">Explains how to redirect output from PowerShell to text files.</span></span>

## <a name="long-description"></a><span data-ttu-id="9b182-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="9b182-107">Long description</span></span>

<span data-ttu-id="9b182-108">Power shell verzendt standaard uitvoer naar de Power shell-host.</span><span class="sxs-lookup"><span data-stu-id="9b182-108">By default, PowerShell sends output to the PowerShell host.</span></span> <span data-ttu-id="9b182-109">Doorgaans is dit de console toepassing.</span><span class="sxs-lookup"><span data-stu-id="9b182-109">Usually this is the console application.</span></span> <span data-ttu-id="9b182-110">U kunt de uitvoer echter door sturen naar een tekst bestand en u kunt de fout uitvoer omleiden naar de normale uitvoer stroom.</span><span class="sxs-lookup"><span data-stu-id="9b182-110">However, you can direct the output to a text file, and you can redirect error output to the regular output stream.</span></span>

<span data-ttu-id="9b182-111">U kunt de volgende methoden gebruiken om uitvoer om te leiden:</span><span class="sxs-lookup"><span data-stu-id="9b182-111">You can use the following methods to redirect output:</span></span>

- <span data-ttu-id="9b182-112">Gebruik de `Out-File` cmdlet, waarmee de uitvoer van de opdracht wordt verzonden naar een tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="9b182-112">Use the `Out-File` cmdlet, which sends command output to a text file.</span></span>
  <span data-ttu-id="9b182-113">Normaal gesp roken gebruikt u de `Out-File` cmdlet wanneer u de para meters, zoals de `Encoding` ,, `Force` `Width` of `NoClobber` para meters, moet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9b182-113">Typically, you use the `Out-File` cmdlet when you need to use its parameters, such as the `Encoding`, `Force`, `Width`, or `NoClobber` parameters.</span></span>

- <span data-ttu-id="9b182-114">Gebruik de `Tee-Object` cmdlet, waarmee de uitvoer van de opdracht naar een tekst bestand wordt verzonden en vervolgens naar de pijp lijn wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="9b182-114">Use the `Tee-Object` cmdlet, which sends command output to a text file and then sends it to the pipeline.</span></span>

- <span data-ttu-id="9b182-115">Gebruik de omleidings operatoren voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="9b182-115">Use the PowerShell redirection operators.</span></span> <span data-ttu-id="9b182-116">Het gebruik van de omleidings operator met een bestands doel is functioneel equivalent aan leidingen zonder `Out-File` extra para meters.</span><span class="sxs-lookup"><span data-stu-id="9b182-116">Using the redirection operator with a file target is functionally equivalent to piping to `Out-File` with no extra parameters.</span></span>

<span data-ttu-id="9b182-117">Zie [about_Output_Streams](about_Output_Streams.md)voor meer informatie over stromen.</span><span class="sxs-lookup"><span data-stu-id="9b182-117">For more information about streams, see [about_Output_Streams](about_Output_Streams.md).</span></span>

### <a name="redirectable-output-streams"></a><span data-ttu-id="9b182-118">Omgeleide uitvoer stromen</span><span class="sxs-lookup"><span data-stu-id="9b182-118">Redirectable output streams</span></span>

<span data-ttu-id="9b182-119">Power shell ondersteunt omleiding van de volgende uitvoer stromen.</span><span class="sxs-lookup"><span data-stu-id="9b182-119">PowerShell supports redirection of the following output streams.</span></span>

| <span data-ttu-id="9b182-120">Bitsnelheid #</span><span class="sxs-lookup"><span data-stu-id="9b182-120">Stream #</span></span> |      <span data-ttu-id="9b182-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9b182-121">Description</span></span>       | <span data-ttu-id="9b182-122">Geïntroduceerd in</span><span class="sxs-lookup"><span data-stu-id="9b182-122">Introduced in</span></span>  |    <span data-ttu-id="9b182-123">Cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="9b182-123">Write Cmdlet</span></span>     |
| -------- | ---------------------- | -------------- | ------------------- |
| <span data-ttu-id="9b182-124">1</span><span class="sxs-lookup"><span data-stu-id="9b182-124">1</span></span>        | <span data-ttu-id="9b182-125">**Geslaagd** Bitsnelheid</span><span class="sxs-lookup"><span data-stu-id="9b182-125">**Success** Stream</span></span>     | <span data-ttu-id="9b182-126">Power Shell 2,0</span><span class="sxs-lookup"><span data-stu-id="9b182-126">PowerShell 2.0</span></span> | `Write-Output`      |
| <span data-ttu-id="9b182-127">2</span><span class="sxs-lookup"><span data-stu-id="9b182-127">2</span></span>        | <span data-ttu-id="9b182-128">**Fout** Bitsnelheid</span><span class="sxs-lookup"><span data-stu-id="9b182-128">**Error** Stream</span></span>       | <span data-ttu-id="9b182-129">Power Shell 2,0</span><span class="sxs-lookup"><span data-stu-id="9b182-129">PowerShell 2.0</span></span> | `Write-Error`       |
| <span data-ttu-id="9b182-130">3</span><span class="sxs-lookup"><span data-stu-id="9b182-130">3</span></span>        | <span data-ttu-id="9b182-131">**Waarschuwing** Bitsnelheid</span><span class="sxs-lookup"><span data-stu-id="9b182-131">**Warning** Stream</span></span>     | <span data-ttu-id="9b182-132">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="9b182-132">PowerShell 3.0</span></span> | `Write-Warning`     |
| <span data-ttu-id="9b182-133">4</span><span class="sxs-lookup"><span data-stu-id="9b182-133">4</span></span>        | <span data-ttu-id="9b182-134">**Uitgebreid** Bitsnelheid</span><span class="sxs-lookup"><span data-stu-id="9b182-134">**Verbose** Stream</span></span>     | <span data-ttu-id="9b182-135">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="9b182-135">PowerShell 3.0</span></span> | `Write-Verbose`     |
| <span data-ttu-id="9b182-136">5</span><span class="sxs-lookup"><span data-stu-id="9b182-136">5</span></span>        | <span data-ttu-id="9b182-137">**Fouten opsporen** Bitsnelheid</span><span class="sxs-lookup"><span data-stu-id="9b182-137">**Debug** Stream</span></span>       | <span data-ttu-id="9b182-138">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="9b182-138">PowerShell 3.0</span></span> | `Write-Debug`       |
| <span data-ttu-id="9b182-139">6</span><span class="sxs-lookup"><span data-stu-id="9b182-139">6</span></span>        | <span data-ttu-id="9b182-140">**Gegevens** Bitsnelheid</span><span class="sxs-lookup"><span data-stu-id="9b182-140">**Information** Stream</span></span> | <span data-ttu-id="9b182-141">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9b182-141">PowerShell 5.0</span></span> | `Write-Information` |
| *        | <span data-ttu-id="9b182-142">Alle streams</span><span class="sxs-lookup"><span data-stu-id="9b182-142">All Streams</span></span>            | <span data-ttu-id="9b182-143">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="9b182-143">PowerShell 3.0</span></span> |                     |

> [!NOTE]
> <span data-ttu-id="9b182-144">Er is ook een **voortgangs** stroom in Power shell, maar de omleiding wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9b182-144">There is also a **Progress** stream in PowerShell, but it does not support redirection.</span></span>

### <a name="powershell-redirection-operators"></a><span data-ttu-id="9b182-145">Omleidings operatoren voor Power shell</span><span class="sxs-lookup"><span data-stu-id="9b182-145">PowerShell redirection operators</span></span>

<span data-ttu-id="9b182-146">De Power shell-omleidings operatoren zijn als volgt, waarbij `n` het stroom nummer wordt aangeduid.</span><span class="sxs-lookup"><span data-stu-id="9b182-146">The PowerShell redirection operators are as follows, where `n` represents the stream number.</span></span> <span data-ttu-id="9b182-147">De **geslaagde** stroom ( `1` ) is de standaard waarde als er geen stroom is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9b182-147">The **Success** stream ( `1` ) is the default if no stream is specified.</span></span>

| <span data-ttu-id="9b182-148">Operator</span><span class="sxs-lookup"><span data-stu-id="9b182-148">Operator</span></span> |                         <span data-ttu-id="9b182-149">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9b182-149">Description</span></span>                         | <span data-ttu-id="9b182-150">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b182-150">Syntax</span></span> |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | <span data-ttu-id="9b182-151">De opgegeven stroom naar een bestand verzenden.</span><span class="sxs-lookup"><span data-stu-id="9b182-151">Send specified stream to a file.</span></span>                            | `n>`   |
| `>>`     | <span data-ttu-id="9b182-152">De opgegeven stroom aan een bestand **toevoegen** .</span><span class="sxs-lookup"><span data-stu-id="9b182-152">**Append** specified stream to a file.</span></span>                      | `n>>`  |
| `>&1`    | <span data-ttu-id="9b182-153">_Leidt_ de opgegeven stroom om naar de **succes** stroom.</span><span class="sxs-lookup"><span data-stu-id="9b182-153">_Redirects_ the specified stream to the **Success** stream.</span></span> | `n>&1` |

> [!NOTE]
> <span data-ttu-id="9b182-154">In tegens telling tot sommige UNIX-shells kunt u alleen andere streams omleiden naar de stroom van **slagen** .</span><span class="sxs-lookup"><span data-stu-id="9b182-154">Unlike some Unix shells, you can only redirect other streams to the **Success** stream.</span></span>

## <a name="examples"></a><span data-ttu-id="9b182-155">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="9b182-155">Examples</span></span>

### <a name="example-1-redirect-errors-and-output-to-a-file"></a><span data-ttu-id="9b182-156">Voor beeld 1: fouten omleiden en uitvoer naar een bestand</span><span class="sxs-lookup"><span data-stu-id="9b182-156">Example 1: Redirect errors and output to a file</span></span>

<span data-ttu-id="9b182-157">Dit voor beeld wordt uitgevoerd `dir` op één item dat slaagt en dat een fout bevat.</span><span class="sxs-lookup"><span data-stu-id="9b182-157">This example runs `dir` on one item that will succeed, and one that will error.</span></span>

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

<span data-ttu-id="9b182-158">De functie wordt gebruikt `2>&1` om de **fout** stroom om te leiden naar de stroom die is **gelukt** en `>` om de resulterende **geslaagde** stroom te verzenden naar een bestand met de naam `dir.log`</span><span class="sxs-lookup"><span data-stu-id="9b182-158">It uses `2>&1` to redirect the **Error** stream to the **Success** stream, and `>` to send the resultant **Success** stream to a file called `dir.log`</span></span>

### <a name="example-2-send-all-success-stream-data-to-a-file"></a><span data-ttu-id="9b182-159">Voor beeld 2: alle geslaagde stroom gegevens naar een bestand verzenden</span><span class="sxs-lookup"><span data-stu-id="9b182-159">Example 2: Send all Success stream data to a file</span></span>

<span data-ttu-id="9b182-160">In dit voor beeld worden alle **geslaagde** stroom gegevens verzonden naar een bestand met de naam `script.log` .</span><span class="sxs-lookup"><span data-stu-id="9b182-160">This example sends all **Success** stream data to a file called `script.log`.</span></span>

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a><span data-ttu-id="9b182-161">Voor beeld 3: geslaagde, waarschuwings-en fout stromen naar een bestand verzenden</span><span class="sxs-lookup"><span data-stu-id="9b182-161">Example 3: Send Success, Warning, and Error streams to a file</span></span>

<span data-ttu-id="9b182-162">Dit voor beeld laat zien hoe u omleidings operatoren kunt combi neren om een gewenst resultaat te krijgen.</span><span class="sxs-lookup"><span data-stu-id="9b182-162">This example shows how you can combine redirection operators to achieve a desired result.</span></span>

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > P:\Temp\redirection.log
```

- <span data-ttu-id="9b182-163">`3>&1` leidt de **waarschuwing** over naar de stroom voor **geslaagde** gegevens.</span><span class="sxs-lookup"><span data-stu-id="9b182-163">`3>&1` redirects the **Warning** stream to the **Success** stream.</span></span>
- <span data-ttu-id="9b182-164">`2>&1` Hiermee wordt de **fout** stroom omgeleid naar de stroom voor **geslaagde** verzen ding (die nu alle **waarschuwingen** voor de gegevens stroom bevat)</span><span class="sxs-lookup"><span data-stu-id="9b182-164">`2>&1` redirects the **Error** stream to the **Success** stream (which also now includes all **Warning** stream data)</span></span>
- <span data-ttu-id="9b182-165">`>` Hiermee wordt de stroom voor het **slagen** (die nu zowel **waarschuwings** -als **fout** stromen bevat) omgeleid naar een bestand met `C:\temp\redirection.log` de naam.</span><span class="sxs-lookup"><span data-stu-id="9b182-165">`>` redirects the **Success** stream (which now contains both **Warning** and **Error** streams) to a file called `C:\temp\redirection.log`)</span></span>

### <a name="example-4-redirect-all-streams-to-a-file"></a><span data-ttu-id="9b182-166">Voor beeld 4: alle streams omleiden naar een bestand</span><span class="sxs-lookup"><span data-stu-id="9b182-166">Example 4: Redirect all streams to a file</span></span>

<span data-ttu-id="9b182-167">In dit voor beeld wordt alle stromen uitvoer verzonden vanuit een script dat wordt aangeroepen `script.ps1` naar een bestand met de naam `script.log`</span><span class="sxs-lookup"><span data-stu-id="9b182-167">This example sends all streams output from a script called `script.ps1` to a file called `script.log`</span></span>

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a><span data-ttu-id="9b182-168">Voor beeld 5: alle Write-Host-en informatie stroom gegevens onderdrukken</span><span class="sxs-lookup"><span data-stu-id="9b182-168">Example 5: Suppress all Write-Host and Information stream data</span></span>

<span data-ttu-id="9b182-169">In dit voor beeld worden alle gegevens streamgegevens onderdrukt.</span><span class="sxs-lookup"><span data-stu-id="9b182-169">This example suppresses all information stream data.</span></span> <span data-ttu-id="9b182-170">Zie [Write-host](xref:Microsoft.PowerShell.Utility.Write-Host) en [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information) (Engelstalig) voor meer informatie over de **gegevens** stroom-cmdlets</span><span class="sxs-lookup"><span data-stu-id="9b182-170">To read more about **Information** stream cmdlets, see [Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host) and [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)</span></span>

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a><span data-ttu-id="9b182-171">Voor beeld 6: het effect van actie voorkeuren weer geven</span><span class="sxs-lookup"><span data-stu-id="9b182-171">Example 6: Show the effect of Action Preferences</span></span>

<span data-ttu-id="9b182-172">Voor keur variabelen en-para meters voor acties kunnen veranderen wat naar een bepaalde stroom wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="9b182-172">Action Preference variables and parameters can change what gets written to a particular stream.</span></span> <span data-ttu-id="9b182-173">Het script in dit voor beeld laat zien hoe de waarde van `$ErrorActionPreference` invloed heeft op wat **er** naar de fout stroom wordt geschreven.</span><span class="sxs-lookup"><span data-stu-id="9b182-173">The script in this example shows how the value of `$ErrorActionPreference` affects what gets written to the **Error** stream.</span></span>

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

<span data-ttu-id="9b182-174">Wanneer het script wordt uitgevoerd, ontvangt u een melding wanneer `$ErrorActionPreference` is ingesteld op `Inquire` .</span><span class="sxs-lookup"><span data-stu-id="9b182-174">When we run this script we get prompted when `$ErrorActionPreference` is set to `Inquire`.</span></span>

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

<span data-ttu-id="9b182-175">Wanneer we het logboek bestand onderzoeken, zien we het volgende:</span><span class="sxs-lookup"><span data-stu-id="9b182-175">When we examine the log file we see the following:</span></span>

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a><span data-ttu-id="9b182-176">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9b182-176">Notes</span></span>

<span data-ttu-id="9b182-177">De omleidings operatoren die geen gegevens toevoegen ( `>` en `n>` ) overschrijven de huidige inhoud van het opgegeven bestand zonder waarschuwing.</span><span class="sxs-lookup"><span data-stu-id="9b182-177">The redirection operators that do not append data (`>` and `n>`) overwrite the current contents of the specified file without warning.</span></span>

<span data-ttu-id="9b182-178">Als het bestand echter een alleen-lezen, verborgen of systeem bestand is, **mislukt** de omleiding.</span><span class="sxs-lookup"><span data-stu-id="9b182-178">However, if the file is a read-only, hidden, or system file, the redirection **fails**.</span></span> <span data-ttu-id="9b182-179">De Opera tors voor omleidingen ( `>>` en `n>>` ) worden niet naar een alleen-lezen bestand geschreven, maar ze voegen inhoud toe aan een systeem of een verborgen bestand.</span><span class="sxs-lookup"><span data-stu-id="9b182-179">The append redirection operators (`>>` and `n>>`) do not write to a read-only file, but they append content to a system or hidden file.</span></span>

<span data-ttu-id="9b182-180">Als u de omleiding van inhoud wilt afdwingen naar een alleen-lezen, verborgen of systeem bestand, gebruikt u de `Out-File` cmdlet met de `Force` para meter.</span><span class="sxs-lookup"><span data-stu-id="9b182-180">To force the redirection of content to a read-only, hidden, or system file, use the `Out-File` cmdlet with its `Force` parameter.</span></span>

<span data-ttu-id="9b182-181">Wanneer u naar bestanden schrijft, gebruiken de omleidings operatoren `UTF8NoBOM` code ring.</span><span class="sxs-lookup"><span data-stu-id="9b182-181">When you are writing to files, the redirection operators use `UTF8NoBOM` encoding.</span></span> <span data-ttu-id="9b182-182">Als het bestand een andere code ring heeft, is de uitvoer mogelijk niet correct ingedeeld.</span><span class="sxs-lookup"><span data-stu-id="9b182-182">If the file has a different encoding, the output might not be formatted correctly.</span></span> <span data-ttu-id="9b182-183">Als u naar bestanden met een andere code ring wilt schrijven, gebruikt u de `Out-File` cmdlet met de `Encoding` para meter.</span><span class="sxs-lookup"><span data-stu-id="9b182-183">To write to files with a different encoding, use the `Out-File` cmdlet with its `Encoding` parameter.</span></span>

### <a name="potential-confusion-with-comparison-operators"></a><span data-ttu-id="9b182-184">Mogelijke Verwar ring met vergelijkings operatoren</span><span class="sxs-lookup"><span data-stu-id="9b182-184">Potential confusion with comparison operators</span></span>

<span data-ttu-id="9b182-185">De `>` operator kan niet worden verward met de vergelijkings operator [groter dan](about_Comparison_Operators.md#-gt) (vaak aangeduid als `>` in andere programmeer talen).</span><span class="sxs-lookup"><span data-stu-id="9b182-185">The `>` operator is not to be confused with the [Greater-than](about_Comparison_Operators.md#-gt) comparison operator (often denoted as `>` in other programming languages).</span></span>

<span data-ttu-id="9b182-186">Afhankelijk van de objecten die worden vergeleken, is het mogelijk dat de uitvoer met de juiste indeling wordt `>` weer gegeven (omdat 36 niet groter is dan 42).</span><span class="sxs-lookup"><span data-stu-id="9b182-186">Depending on the objects being compared, the output using `>` can appear to be correct (because 36 is not greater than 42).</span></span>

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

<span data-ttu-id="9b182-187">Een controle van het lokale bestands systeem kan echter zien dat een bestand `42` met de naam is geschreven, met de inhoud `36` .</span><span class="sxs-lookup"><span data-stu-id="9b182-187">However, a check of the local filesystem can see that a file called `42` was written, with the contents `36`.</span></span>

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

<span data-ttu-id="9b182-188">Er wordt geprobeerd om de omgekeerde vergelijking `<` (kleiner dan) te gebruiken, wat een systeem fout levert:</span><span class="sxs-lookup"><span data-stu-id="9b182-188">Attempting to use the reverse comparison `<` (less than), yields a system error:</span></span>

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : RedirectionNotSupported
```

<span data-ttu-id="9b182-189">Als numerieke vergelijking de vereiste bewerking is, `-lt` en deze `-gt` moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9b182-189">If numeric comparison is the required operation, `-lt` and `-gt` should be used.</span></span> <span data-ttu-id="9b182-190">Zie: [ `-gt` vergelijkings operator](about_Comparison_Operators.md#-gt)</span><span class="sxs-lookup"><span data-stu-id="9b182-190">See: [`-gt` Comparison Operator](about_Comparison_Operators.md#-gt)</span></span>

## <a name="see-also"></a><span data-ttu-id="9b182-191">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9b182-191">See also</span></span>

- [<span data-ttu-id="9b182-192">Out-file</span><span class="sxs-lookup"><span data-stu-id="9b182-192">Out-File</span></span>](xref:Microsoft.PowerShell.Utility.Out-File)
- [<span data-ttu-id="9b182-193">T-object</span><span class="sxs-lookup"><span data-stu-id="9b182-193">Tee-Object</span></span>](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [<span data-ttu-id="9b182-194">Schrijf fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="9b182-194">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="9b182-195">Schrijf fout</span><span class="sxs-lookup"><span data-stu-id="9b182-195">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)
- [<span data-ttu-id="9b182-196">Write-host</span><span class="sxs-lookup"><span data-stu-id="9b182-196">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)
- [<span data-ttu-id="9b182-197">Write-Information</span><span class="sxs-lookup"><span data-stu-id="9b182-197">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)
- [<span data-ttu-id="9b182-198">Write-output</span><span class="sxs-lookup"><span data-stu-id="9b182-198">Write-Output</span></span>](xref:Microsoft.PowerShell.Utility.Write-Output)
- [<span data-ttu-id="9b182-199">Schrijf voortgang</span><span class="sxs-lookup"><span data-stu-id="9b182-199">Write-Progress</span></span>](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [<span data-ttu-id="9b182-200">Write-verbose</span><span class="sxs-lookup"><span data-stu-id="9b182-200">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [<span data-ttu-id="9b182-201">Waarschuwing voor schrijven</span><span class="sxs-lookup"><span data-stu-id="9b182-201">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [<span data-ttu-id="9b182-202">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="9b182-202">about_Output_Streams</span></span>](about_Output_Streams.md)
- [<span data-ttu-id="9b182-203">about_Operators</span><span class="sxs-lookup"><span data-stu-id="9b182-203">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="9b182-204">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="9b182-204">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="9b182-205">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="9b182-205">about_Path_Syntax</span></span>](about_Path_Syntax.md)