---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: e1680e5ad182051bce217efd6f1eb48d44798146
ms.sourcegitcommit: 366304d096c1caf52f0e17962f6ed23d20f86e7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2021
ms.locfileid: "107543837"
---
# <span data-ttu-id="eab84-103">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="eab84-103">ForEach-Object</span></span>

## <span data-ttu-id="eab84-104">Synopsis</span><span class="sxs-lookup"><span data-stu-id="eab84-104">Synopsis</span></span>
<span data-ttu-id="eab84-105">Voert een bewerking uit op elk item in een verzameling invoerobjecten.</span><span class="sxs-lookup"><span data-stu-id="eab84-105">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="eab84-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="eab84-106">Syntax</span></span>

### <span data-ttu-id="eab84-107">ScriptBlockSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="eab84-107">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="eab84-108">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="eab84-108">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="eab84-109">ParallelParameterSet</span><span class="sxs-lookup"><span data-stu-id="eab84-109">ParallelParameterSet</span></span>

```
ForEach-Object -Parallel <scriptblock> [-InputObject <PSObject>] [-ThrottleLimit <int>]
[-UseNewRunspace] [-TimeoutSeconds <int>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="eab84-110">Description</span><span class="sxs-lookup"><span data-stu-id="eab84-110">Description</span></span>

<span data-ttu-id="eab84-111">De `ForEach-Object` cmdlet voert een bewerking uit op elk item in een verzameling invoerobjecten.</span><span class="sxs-lookup"><span data-stu-id="eab84-111">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="eab84-112">De invoerobjecten kunnen worden doorgegeven aan de cmdlet of worden opgegeven met behulp van de **parameter InputObject.**</span><span class="sxs-lookup"><span data-stu-id="eab84-112">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="eab84-113">Vanaf Windows PowerShell 3.0 zijn er twee verschillende manieren om een opdracht te `ForEach-Object` maken.</span><span class="sxs-lookup"><span data-stu-id="eab84-113">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="eab84-114">**Scriptblok.**</span><span class="sxs-lookup"><span data-stu-id="eab84-114">**Script block**.</span></span> <span data-ttu-id="eab84-115">U kunt een scriptblok gebruiken om de bewerking op te geven.</span><span class="sxs-lookup"><span data-stu-id="eab84-115">You can use a script block to specify the operation.</span></span> <span data-ttu-id="eab84-116">Gebruik in het scriptblok de variabele `$_` om het huidige object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="eab84-116">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="eab84-117">Het scriptblok is de waarde van de **procesparameter.**</span><span class="sxs-lookup"><span data-stu-id="eab84-117">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="eab84-118">Het scriptblok kan elk PowerShell-script bevatten.</span><span class="sxs-lookup"><span data-stu-id="eab84-118">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="eab84-119">Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap **ProcessName** van elk proces op de computer opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="eab84-119">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="eab84-120">`ForEach-Object` ondersteunt de `begin` blokken , en zoals `process` `end` beschreven in [about_functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="eab84-120">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="eab84-121">De scriptblokken worden uitgevoerd in het bereik van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="eab84-121">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="eab84-122">Daarom hebben de blokken toegang tot variabelen in dat bereik en kunnen nieuwe variabelen worden gemaakt die in dat bereik blijven bestaan nadat de cmdlet is voltooid.</span><span class="sxs-lookup"><span data-stu-id="eab84-122">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="eab84-123">**Bewerkings-instructie**.</span><span class="sxs-lookup"><span data-stu-id="eab84-123">**Operation statement**.</span></span> <span data-ttu-id="eab84-124">U kunt ook een bewerkingsverklaring schrijven, die veel meer lijkt op natuurlijke taal.</span><span class="sxs-lookup"><span data-stu-id="eab84-124">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="eab84-125">U kunt de bewerkings-instructie gebruiken om een eigenschapswaarde op te geven of een methode aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="eab84-125">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="eab84-126">Bewerkingsverklaringen zijn geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="eab84-126">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="eab84-127">Met de volgende opdracht wordt bijvoorbeeld ook de waarde van de eigenschap **ProcessName** van elk proces op de computer opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="eab84-127">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

- <span data-ttu-id="eab84-128">**Parallel uitvoerend scriptblok**.</span><span class="sxs-lookup"><span data-stu-id="eab84-128">**Parallel running script block**.</span></span> <span data-ttu-id="eab84-129">Vanaf PowerShell 7.0 is er een derde parameterset beschikbaar die elk scriptblok parallel wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eab84-129">Beginning with PowerShell 7.0, a third parameter set is available that runs each script block in parallel.</span></span> <span data-ttu-id="eab84-130">Met **de parameter ThrottleLimit** beperkt u het aantal parallelle scripts dat tegelijk wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eab84-130">The **ThrottleLimit** parameter limits the number of parallel scripts running at a time.</span></span> <span data-ttu-id="eab84-131">Net als voorheen gebruikt u de `$_` variabele om het huidige invoerobject in het scriptblok weer te geven.</span><span class="sxs-lookup"><span data-stu-id="eab84-131">As before, use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="eab84-132">Gebruik het `$using:` trefwoord om variabeleverwijzingen door te geven aan het script dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eab84-132">Use the `$using:` keyword to pass variable references to the running script.</span></span>

  <span data-ttu-id="eab84-133">In PowerShell 7 wordt voor elke lus-iteratie een nieuwe runspace gemaakt om maximale isolatie te garanderen.</span><span class="sxs-lookup"><span data-stu-id="eab84-133">In PowerShell 7, a new runspace is created for each loop iteration to ensure maximum isolation.</span></span>
  <span data-ttu-id="eab84-134">Dit kan een grote prestatie- en resource-hit zijn als het werk dat u doet klein is in vergelijking met het maken van nieuwe runspaces of als er veel iteraties zijn die aanzienlijk werk verrichten.</span><span class="sxs-lookup"><span data-stu-id="eab84-134">This can be a large performance and resource hit if the work you are doing is small compared to creating new runspaces or if there are a lot of iterations performing significant work.</span></span> <span data-ttu-id="eab84-135">Vanaf PowerShell 7.1 worden runspaces uit een runspacegroep standaard opnieuw gebruikt.</span><span class="sxs-lookup"><span data-stu-id="eab84-135">As of PowerShell 7.1, runspaces from a runspace pool are reused by default.</span></span> <span data-ttu-id="eab84-136">De grootte van de runspacegroep wordt opgegeven door de parameter **ThrottleLimit.**</span><span class="sxs-lookup"><span data-stu-id="eab84-136">The runspace pool size is specified by the **ThrottleLimit** parameter.</span></span> <span data-ttu-id="eab84-137">De standaardgrootte van de runspacegroep is 5.</span><span class="sxs-lookup"><span data-stu-id="eab84-137">The default runspace pool size is 5.</span></span> <span data-ttu-id="eab84-138">U kunt nog steeds een nieuwe runspace maken voor elke iteratie met behulp van **de switch UseNewRunspace.**</span><span class="sxs-lookup"><span data-stu-id="eab84-138">You can still create a new runspace for each iteration using the **UseNewRunspace** switch.</span></span>

  <span data-ttu-id="eab84-139">De parallelle scriptblokkeringen gebruiken standaard de huidige werkmap van de aanroeper die de parallelle taken heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="eab84-139">By default, the parallel scriptblocks use the current working directory of the caller that started the parallel tasks.</span></span>

  <span data-ttu-id="eab84-140">Niet-beëindigingsfouten worden naar de foutstroom van de cmdlet geschreven wanneer deze zich voordoen in parallelle scriptblokkeringen.</span><span class="sxs-lookup"><span data-stu-id="eab84-140">Non-terminating errors are written to the cmdlet error stream as they occur in parallel running scriptblocks.</span></span> <span data-ttu-id="eab84-141">Omdat de uitvoeringsorder voor parallelle scriptblokkering niet kan worden bepaald, is de volgorde waarin fouten worden weergegeven in de foutstroom willekeurig.</span><span class="sxs-lookup"><span data-stu-id="eab84-141">Because parallel scriptblock execution order cannot be determined, the order in which errors appear in the error stream is random.</span></span> <span data-ttu-id="eab84-142">Berichten die naar andere gegevensstromen worden geschreven, zoals waarschuwing, uitgebreid of informatie, worden in een onbepaalde volgorde naar deze gegevensstromen geschreven.</span><span class="sxs-lookup"><span data-stu-id="eab84-142">Likewise, messages written to other data streams, like warning, verbose, or information are written to those data streams in an indeterminate order.</span></span>

  <span data-ttu-id="eab84-143">Het beëindigen van fouten, zoals uitzonderingen, beëindigt de afzonderlijke parallelle instantie van de scriptblokkeringen waarin ze optreden.</span><span class="sxs-lookup"><span data-stu-id="eab84-143">Terminating errors, such as exceptions, terminate the individual parallel instance of the scriptblocks in which they occur.</span></span> <span data-ttu-id="eab84-144">Een beëindigingsfout in één scriptblokkering veroorzaakt mogelijk niet de beëindiging van de `Foreach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eab84-144">A terminating error in one scriptblocks may not cause the termination of the `Foreach-Object` cmdlet.</span></span> <span data-ttu-id="eab84-145">De andere scriptblokkeringen, die parallel worden uitgevoerd, blijven actief, tenzij ze ook een beëindigingsfout tegenkomen.</span><span class="sxs-lookup"><span data-stu-id="eab84-145">The other scriptblocks, running in parallel, continue to run unless they also encounter a terminating error.</span></span> <span data-ttu-id="eab84-146">De eindfout wordt naar de foutgegevensstroom geschreven als een **ErrorRecord** met een **FullyQualifiedErrorId** van `PSTaskException` .</span><span class="sxs-lookup"><span data-stu-id="eab84-146">The terminating error is written to the error data stream as an **ErrorRecord** with a **FullyQualifiedErrorId** of `PSTaskException`.</span></span>
  <span data-ttu-id="eab84-147">Beëindigingsfouten kunnen worden geconverteerd naar niet-beëindigingsfouten met behulp van PowerShell-try-/catch- of trapblokken.</span><span class="sxs-lookup"><span data-stu-id="eab84-147">Terminating errors can be converted to non-terminating errors using PowerShell try/catch or trap blocks.</span></span>

## <span data-ttu-id="eab84-148">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="eab84-148">Examples</span></span>

### <span data-ttu-id="eab84-149">Voorbeeld 1: Gehele getallen in een matrix delen</span><span class="sxs-lookup"><span data-stu-id="eab84-149">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="eab84-150">In dit voorbeeld wordt een matrix van drie gehele getallen gebruikt en wordt elk van deze door 1024 verdeeld.</span><span class="sxs-lookup"><span data-stu-id="eab84-150">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="eab84-151">Voorbeeld 2: de lengte van alle bestanden in een map op te halen</span><span class="sxs-lookup"><span data-stu-id="eab84-151">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="eab84-152">In dit voorbeeld worden de bestanden en mappen in de PowerShell-installatiemap `$PSHOME` verwerkt.</span><span class="sxs-lookup"><span data-stu-id="eab84-152">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="eab84-153">Als het object geen map is, haalt het scriptblok de naam van het bestand op, deelt de waarde van de eigenschap **Length** door 1024 en voegt een spatie ("") toe om het te scheiden van de volgende vermelding.</span><span class="sxs-lookup"><span data-stu-id="eab84-153">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="eab84-154">De cmdlet gebruikt de **eigenschap PSISContainer** om te bepalen of een object een map is.</span><span class="sxs-lookup"><span data-stu-id="eab84-154">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="eab84-155">Voorbeeld 3: Werken met de meest recente systeemgebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="eab84-155">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="eab84-156">In dit voorbeeld worden de 1000 meest recente gebeurtenissen uit het systeemgebeurtenislogboek naar een tekstbestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="eab84-156">This example writes the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="eab84-157">De huidige tijd wordt weergegeven voor en na het verwerken van de gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="eab84-157">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="eab84-158">`Get-EventLog` haalt de 1000 meest recente gebeurtenissen uit het gebeurtenislogboek van het systeem op en slaat deze op in de `$Events` variabele .</span><span class="sxs-lookup"><span data-stu-id="eab84-158">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="eab84-159">`$Events` wordt vervolgens doorspijpt naar `ForEach-Object` de cmdlet .</span><span class="sxs-lookup"><span data-stu-id="eab84-159">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="eab84-160">De **begin** parameter geeft de huidige datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="eab84-160">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="eab84-161">Vervolgens gebruikt de parameter **Process** de cmdlet om een tekstbestand met de naam events.txt te maken en slaat de bericht-eigenschap van elk van de gebeurtenissen `Out-File` in dat bestand op.</span><span class="sxs-lookup"><span data-stu-id="eab84-161">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="eab84-162">Ten laatste wordt de parameter **End** gebruikt om de datum en tijd weer te geven nadat alle verwerking is voltooid.</span><span class="sxs-lookup"><span data-stu-id="eab84-162">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="eab84-163">Voorbeeld 4: De waarde van een registersleutel wijzigen</span><span class="sxs-lookup"><span data-stu-id="eab84-163">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="eab84-164">In dit voorbeeld wordt de waarde van de **RemotePath-registerinvoer** in alle subsleutels onder de sleutel gewijzigd in `HKCU:\Network` hoofdletters.</span><span class="sxs-lookup"><span data-stu-id="eab84-164">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="eab84-165">U kunt deze indeling gebruiken om het formulier of de inhoud van een registerinvoerwaarde te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="eab84-165">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="eab84-166">Elke subsleutel in de **netwerksleutel** vertegenwoordigt een gekoppeld netwerkstation dat opnieuw verbinding maakt bij aanmelding.</span><span class="sxs-lookup"><span data-stu-id="eab84-166">Each subkey in the **Network** key represents a mapped network drive that reconnects at sign on.</span></span> <span data-ttu-id="eab84-167">De **vermelding RemotePath** bevat het UNC-pad van het verbonden station.</span><span class="sxs-lookup"><span data-stu-id="eab84-167">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="eab84-168">Als u bijvoorbeeld het E:-station toe wijst aan , wordt `\\Server\Share` er een **E-subsleutel** gemaakt in met de `HKCU:\Network` **registerwaarde RemotePath** ingesteld op `\\Server\Share` .</span><span class="sxs-lookup"><span data-stu-id="eab84-168">For example, if you map the E: drive to `\\Server\Share`, an **E** subkey is created in `HKCU:\Network` with the **RemotePath** registry value set to `\\Server\Share`.</span></span>

<span data-ttu-id="eab84-169">De opdracht gebruikt de cmdlet om alle subsleutels van de netwerksleutel op te halen en de cmdlet om de waarde van de `Get-ItemProperty`  `Set-ItemProperty` **RemotePath-registerinvoer** in elke sleutel te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="eab84-169">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="eab84-170">In de `Set-ItemProperty` opdracht is het pad de waarde van de eigenschap **PSPath** van de registersleutel.</span><span class="sxs-lookup"><span data-stu-id="eab84-170">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="eab84-171">Dit is een eigenschap van het Microsoft .NET Framework-object dat de registersleutel vertegenwoordigt, niet een registerinvoer.</span><span class="sxs-lookup"><span data-stu-id="eab84-171">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="eab84-172">De opdracht maakt gebruik **van de methode ToUpper()** van de **waarde RemotePath.** Dit is een tekenreeks (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="eab84-172">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="eab84-173">Omdat `Set-ItemProperty` de eigenschap van elke sleutel verandert, is de `ForEach-Object` cmdlet vereist voor toegang tot de eigenschap .</span><span class="sxs-lookup"><span data-stu-id="eab84-173">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="eab84-174">Voorbeeld 5: de automatische $Null gebruiken</span><span class="sxs-lookup"><span data-stu-id="eab84-174">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="eab84-175">In dit voorbeeld ziet u het effect van het doorspitten van `$Null` de automatische variabele naar de `ForEach-Object` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="eab84-175">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="eab84-176">Omdat PowerShell null als een expliciete tijdelijke aanduiding behandelt, genereert de cmdlet een waarde voor , net als voor andere objecten die u er `ForEach-Object` naar doorspijpt. `$Null`</span><span class="sxs-lookup"><span data-stu-id="eab84-176">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="eab84-177">Voorbeeld 6: eigenschapswaarden op halen</span><span class="sxs-lookup"><span data-stu-id="eab84-177">Example 6: Get property values</span></span>

<span data-ttu-id="eab84-178">In dit voorbeeld wordt de waarde van de **eigenschap Path** van alle geïnstalleerde PowerShell-modules met behulp van de **parameter MemberName** van de `ForEach-Object` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="eab84-178">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="eab84-179">De tweede opdracht is gelijk aan de eerste.</span><span class="sxs-lookup"><span data-stu-id="eab84-179">The second command is equivalent to the first.</span></span> <span data-ttu-id="eab84-180">Hierbij wordt de alias van de cmdlet gebruikt en wordt de naam van de `Foreach` `ForEach-Object` parameter **MemberName** weglaat, wat optioneel is.</span><span class="sxs-lookup"><span data-stu-id="eab84-180">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="eab84-181">De cmdlet is handig voor het verkrijgen van eigenschapswaarden, omdat deze de waarde krijgt zonder het type te wijzigen, in tegenstelling tot de cmdlets Format of `ForEach-Object` de cmdlet , waarmee het waardetype van de eigenschap wordt  `Select-Object` gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="eab84-181">The `ForEach-Object` cmdlet is useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="eab84-182">Voorbeeld 7: Modulenamen splitsen in onderdeelnamen</span><span class="sxs-lookup"><span data-stu-id="eab84-182">Example 7: Split module names into component names</span></span>

<span data-ttu-id="eab84-183">In dit voorbeeld ziet u drie manieren om twee modulenamen met punten te splitsen in de onderdeelnamen.</span><span class="sxs-lookup"><span data-stu-id="eab84-183">This example shows three ways to split two dot-separated module names into their component names.</span></span>

```powershell
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object {$_.Split(".")}
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | ForEach-Object -MemberName Split -ArgumentList "."
"Microsoft.PowerShell.Core", "Microsoft.PowerShell.Host" | Foreach Split "."
```

```Output
Microsoft
PowerShell
Core
Microsoft
PowerShell
Host
```

<span data-ttu-id="eab84-184">Met de opdrachten wordt de **methode Split van** tekenreeksen aanroepen.</span><span class="sxs-lookup"><span data-stu-id="eab84-184">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="eab84-185">De drie opdrachten gebruiken een andere syntaxis, maar ze zijn gelijkwaardig en uitwisselbaar.</span><span class="sxs-lookup"><span data-stu-id="eab84-185">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="eab84-186">De eerste opdracht maakt gebruik van de traditionele syntaxis, die een scriptblok en de huidige objectoperator `$_` bevat.</span><span class="sxs-lookup"><span data-stu-id="eab84-186">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="eab84-187">Er wordt gebruikgemaakt van de puntsyntaxis om de methode en haakjes op te geven om het scheidingsteken te omsluiten.</span><span class="sxs-lookup"><span data-stu-id="eab84-187">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="eab84-188">De tweede opdracht maakt gebruik van de **parameter MemberName** om de methode **Split** en de parameter **ArgumentName** op te geven om de punt (".") te identificeren als het scheidingsteken voor splitsen.</span><span class="sxs-lookup"><span data-stu-id="eab84-188">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="eab84-189">De derde opdracht maakt gebruik van de **Foreach-alias** van de cmdlet en laat de namen van de `ForEach-Object` parameters **MemberName** en **ArgumentList** weg, die optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="eab84-189">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="eab84-190">Voorbeeld 8: Een ForEach-Object twee scriptblokken gebruiken</span><span class="sxs-lookup"><span data-stu-id="eab84-190">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="eab84-191">In dit voorbeeld geven we twee scriptblokken positioneel door.</span><span class="sxs-lookup"><span data-stu-id="eab84-191">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="eab84-192">Alle scriptblokken worden aan de parameter **Process** binden.</span><span class="sxs-lookup"><span data-stu-id="eab84-192">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="eab84-193">Ze worden echter behandeld alsof ze zijn doorgegeven aan de **parameters Begin** **en Process.**</span><span class="sxs-lookup"><span data-stu-id="eab84-193">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="eab84-194">Voorbeeld 9: Een ForEach-Object meer dan twee scriptblokken gebruiken</span><span class="sxs-lookup"><span data-stu-id="eab84-194">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="eab84-195">In dit voorbeeld geven we twee scriptblokken positioneel door.</span><span class="sxs-lookup"><span data-stu-id="eab84-195">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="eab84-196">Alle scriptblokken worden aan de parameter **Process** binden.</span><span class="sxs-lookup"><span data-stu-id="eab84-196">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="eab84-197">Ze worden echter behandeld alsof ze zijn doorgegeven aan de parameters **Begin,** **Process** en **End.**</span><span class="sxs-lookup"><span data-stu-id="eab84-197">However, they are treated as if they had been passed to the **Begin**, **Process**, and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process A' }  { 'process B' }  { 'end' }
```

```Output
begin
process A
process B
process A
process B
end
```

> [!NOTE]
> <span data-ttu-id="eab84-198">Het eerste scriptblok wordt altijd aan het blok toegesneden, het laatste blok is aan het blok en de blokken ertussen worden allemaal aan het `begin` `end` blok `process` toegesneden.</span><span class="sxs-lookup"><span data-stu-id="eab84-198">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="eab84-199">Voorbeeld 10: Meerdere scriptblokken uitvoeren voor elk pijplijnitem</span><span class="sxs-lookup"><span data-stu-id="eab84-199">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="eab84-200">Zoals u in het vorige voorbeeld kunt zien, worden meerdere scriptblokken die zijn doorgegeven met behulp van de parameter **Process,** aan de parameters **Begin** en **End** doorgegeven.</span><span class="sxs-lookup"><span data-stu-id="eab84-200">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="eab84-201">Als u deze toewijzing wilt voorkomen, moet u expliciete waarden opgeven voor de parameters **Begin** **en End.**</span><span class="sxs-lookup"><span data-stu-id="eab84-201">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

```powershell
1..2 | ForEach-Object -Begin $null -Process { 'one' }, { 'two' }, { 'three' } -End $null
```

```Output
one
two
three
one
two
three
```

### <span data-ttu-id="eab84-202">Voorbeeld 11: Langzaam script uitvoeren in parallelle batches</span><span class="sxs-lookup"><span data-stu-id="eab84-202">Example 11: Run slow script in parallel batches</span></span>

<span data-ttu-id="eab84-203">In dit voorbeeld wordt een eenvoudig scriptblok uitgevoerd dat een tekenreeks evalueert en één seconde in de slaapstand gaat.</span><span class="sxs-lookup"><span data-stu-id="eab84-203">This example runs a simple script block that evaluates a string and sleeps for one second.</span></span>

```powershell
$Message = "Output:"

1..8 | ForEach-Object -Parallel {
    "$using:Message $_"
    Start-Sleep 1
} -ThrottleLimit 4
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
```

<span data-ttu-id="eab84-204">De **parameterwaarde ThrottleLimit** is ingesteld op 4, zodat de invoer wordt verwerkt in batches van vier.</span><span class="sxs-lookup"><span data-stu-id="eab84-204">The **ThrottleLimit** parameter value is set to 4 so that the input is processed in batches of four.</span></span>
<span data-ttu-id="eab84-205">Het `$using:` trefwoord wordt gebruikt om de variabele `$Message` door te geven aan elk parallel scriptblok.</span><span class="sxs-lookup"><span data-stu-id="eab84-205">The `$using:` keyword is used to pass the `$Message` variable into each parallel script block.</span></span>

### <span data-ttu-id="eab84-206">Voorbeeld 12: Logboekgegevens parallel ophalen</span><span class="sxs-lookup"><span data-stu-id="eab84-206">Example 12: Retrieve log entries in parallel</span></span>

<span data-ttu-id="eab84-207">In dit voorbeeld worden 50.000 logboekgegevens opgehaald uit 5 systeemlogboeken op een lokale Windows-computer.</span><span class="sxs-lookup"><span data-stu-id="eab84-207">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine.</span></span>

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count
```

```Output
50000
```

<span data-ttu-id="eab84-208">De **parameter Parallel** geeft het scriptblok aan dat parallel wordt uitgevoerd voor elke naam van het invoerlogboek.</span><span class="sxs-lookup"><span data-stu-id="eab84-208">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span> <span data-ttu-id="eab84-209">De **parameter ThrottleLimit** zorgt ervoor dat alle vijf scriptblokken tegelijkertijd worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eab84-209">The **ThrottleLimit** parameter ensures that all five script blocks run at the same time.</span></span>

### <span data-ttu-id="eab84-210">Voorbeeld 13: Parallel uitvoeren als een taak</span><span class="sxs-lookup"><span data-stu-id="eab84-210">Example 13: Run in parallel as a job</span></span>

<span data-ttu-id="eab84-211">In dit voorbeeld wordt een eenvoudig scriptblok parallel uitgevoerd, waardoor er twee achtergrondtaken tegelijk worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="eab84-211">This example runs a simple script block in parallel, creating two background jobs at a time.</span></span>

```powershell
$job = 1..10 | ForEach-Object -Parallel {
    "Output: $_"
    Start-Sleep 1
} -ThrottleLimit 2 -AsJob

$job | Receive-Job -Wait
```

```Output
Output: 1
Output: 2
Output: 3
Output: 4
Output: 5
Output: 6
Output: 7
Output: 8
Output: 9
Output: 10
```

<span data-ttu-id="eab84-212">De `$job` variabele ontvangt het taakobject dat uitvoergegevens verzamelt en de status van de uitvoer bewaakt.</span><span class="sxs-lookup"><span data-stu-id="eab84-212">the `$job` variable receives the job object that collects output data and monitors running state.</span></span>
<span data-ttu-id="eab84-213">Het taakobject wordt doorspijpt `Receive-Job` naar met de parameter **Wait** switch.</span><span class="sxs-lookup"><span data-stu-id="eab84-213">The job object is piped to `Receive-Job` with the **Wait** switch parameter.</span></span> <span data-ttu-id="eab84-214">En deze streamt uitvoer naar de console, alsof `ForEach-Object -Parallel` deze is uitgevoerd zonder **AsJob**.</span><span class="sxs-lookup"><span data-stu-id="eab84-214">And this streams output to the console, just as if `ForEach-Object -Parallel` was run without **AsJob**.</span></span>

### <span data-ttu-id="eab84-215">Voorbeeld 14: Verwijzingen naar veilige threadvariabelen gebruiken</span><span class="sxs-lookup"><span data-stu-id="eab84-215">Example 14: Using thread safe variable references</span></span>

<span data-ttu-id="eab84-216">In dit voorbeeld worden scriptblokken parallel aanroepen om unieke procesobjecten te verzamelen.</span><span class="sxs-lookup"><span data-stu-id="eab84-216">This example invokes script blocks in parallel to collect uniquely named Process objects.</span></span>

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
Get-Process | ForEach-Object -Parallel {
    $dict = $using:threadSafeDictionary
    $dict.TryAdd($_.ProcessName, $_)
}

$threadSafeDictionary["pwsh"]
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     82    82.87     130.85      15.55    2808   2 pwsh
```

<span data-ttu-id="eab84-217">Er wordt één exemplaar van een **ConcurrentDictionary-object** doorgegeven aan elk scriptblok om de objecten te verzamelen.</span><span class="sxs-lookup"><span data-stu-id="eab84-217">A single instance of a **ConcurrentDictionary** object is passed to each script block to collect the objects.</span></span> <span data-ttu-id="eab84-218">Omdat **concurrentDictionary thread-veilig** is, is het veilig om te worden gewijzigd door elk parallel script.</span><span class="sxs-lookup"><span data-stu-id="eab84-218">Since the **ConcurrentDictionary** is thread safe, it is safe to be modified by each parallel script.</span></span> <span data-ttu-id="eab84-219">Een niet-thread-veilig object, zoals **System.Collections.Generic.Dictionary,** is hier niet veilig te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="eab84-219">A non-thread-safe object, such as **System.Collections.Generic.Dictionary**, would not be safe to use here.</span></span>

> [!NOTE]
> <span data-ttu-id="eab84-220">Dit voorbeeld is een zeer inefficiënt gebruik van **de parameter Parallel.**</span><span class="sxs-lookup"><span data-stu-id="eab84-220">This example is a very inefficient use of **Parallel** parameter.</span></span> <span data-ttu-id="eab84-221">Het script voegt gewoon het invoerobject toe aan een gelijktijdig woordenboekobject.</span><span class="sxs-lookup"><span data-stu-id="eab84-221">The script simply adds the input object to a concurrent dictionary object.</span></span> <span data-ttu-id="eab84-222">Het is eenvoudig en de overhead van het aanroepen van elk script in een afzonderlijke thread niet waard.</span><span class="sxs-lookup"><span data-stu-id="eab84-222">It is trivial and not worth the overhead of invoking each script in a separate thread.</span></span> <span data-ttu-id="eab84-223">Normaal `ForEach-Object` uitvoeren zonder de **parallelle** switch is veel efficiënter en sneller.</span><span class="sxs-lookup"><span data-stu-id="eab84-223">Running `ForEach-Object` normally without the **Parallel** switch is much more efficient and faster.</span></span> <span data-ttu-id="eab84-224">Dit voorbeeld is alleen bedoeld om te laten zien hoe u thread-veilige variabelen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="eab84-224">This example is only intended to demonstrate how to use thread safe variables.</span></span>

### <span data-ttu-id="eab84-225">Voorbeeld 15: Fouten schrijven met parallelle uitvoering</span><span class="sxs-lookup"><span data-stu-id="eab84-225">Example 15: Writing errors with parallel execution</span></span>

<span data-ttu-id="eab84-226">In dit voorbeeld wordt parallel naar de foutstroom geschreven, waarbij de volgorde van geschreven fouten willekeurig is.</span><span class="sxs-lookup"><span data-stu-id="eab84-226">This example writes to the error stream in parallel, where the order of written errors is random.</span></span>

```powershell
1..3 | ForEach-Object -Parallel {
    Write-Error "Error: $_"
}
```

```Output
Write-Error: Error: 1
Write-Error: Error: 3
Write-Error: Error: 2
```

### <span data-ttu-id="eab84-227">Voorbeeld 16: Fouten bij parallelle uitvoering beëindigen</span><span class="sxs-lookup"><span data-stu-id="eab84-227">Example 16: Terminating errors in parallel execution</span></span>

<span data-ttu-id="eab84-228">In dit voorbeeld wordt een beëindigingsfout in één parallel uitgevoerd scriptblok gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="eab84-228">This example demonstrates a terminating error in one parallel running scriptblock.</span></span>

```powershell
1..5 | ForEach-Object -Parallel {
    if ($_ -eq 3)
    {
        throw "Terminating Error: $_"
    }

    Write-Output "Output: $_"
}
```

```Output
Exception: Terminating Error: 3
Output: 1
Output: 4
Output: 2
Output: 5
```

<span data-ttu-id="eab84-229">`Output: 3` wordt nooit geschreven omdat het parallelle scriptblok voor die iteratie is beëindigd.</span><span class="sxs-lookup"><span data-stu-id="eab84-229">`Output: 3` is never written because the parallel scriptblock for that iteration was terminated.</span></span>

### <span data-ttu-id="eab84-230">Voorbeeld 17: Variabelen doorgeven in genest parallel script ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="eab84-230">Example 17: Passing variables in nested parallel script ScriptBlockSet</span></span>

<span data-ttu-id="eab84-231">U kunt een variabele buiten een `Foreach-Object -Parallel` scoped scriptblock maken en deze gebruiken in het scriptblok met het trefwoord `$using` .</span><span class="sxs-lookup"><span data-stu-id="eab84-231">You can create a variable outside a `Foreach-Object -Parallel` scoped scriptblock and use it inside the scriptblock with the `$using` keyword.</span></span>

```powershell
$test1 = 'TestA'
1..2 | Foreach-Object -Parallel {
    $using:test1
}
```

```Output
TestA
TestA
```

```powershell
# You CANNOT create a variable inside a scoped scriptblock
# to be used in a nested foreach parallel scriptblock.
$test1 = 'TestA'
1..2 | Foreach-Object -Parallel {
    $using:test1
    $test2 = 'TestB'
    1..2 | Foreach-Object -Parallel {
        $using:test2
    }
}
```

```Output
Line |
   2 |  1..2 | Foreach-Object -Parallel {
     |         ~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The value of the using variable '$using:test2' cannot be retrieved because it has not been set in the local session.
```

<span data-ttu-id="eab84-232">Het geneste scriptblok heeft geen toegang tot de `$test2` variabele en er wordt een foutmelding weergegeven.</span><span class="sxs-lookup"><span data-stu-id="eab84-232">The nested scriptblock can't access the `$test2` variable and an error is thrown.</span></span>

## <span data-ttu-id="eab84-233">Parameters</span><span class="sxs-lookup"><span data-stu-id="eab84-233">Parameters</span></span>

### <span data-ttu-id="eab84-234">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="eab84-234">-ArgumentList</span></span>

<span data-ttu-id="eab84-235">Hiermee geeft u een matrix van argumenten op voor een methode-aanroep.</span><span class="sxs-lookup"><span data-stu-id="eab84-235">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="eab84-236">Zie voor meer informatie over het gedrag van **ArgumentList** [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="eab84-236">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="eab84-237">Deze parameter is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="eab84-237">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: PropertyAndMethodSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-238">-Begin</span><span class="sxs-lookup"><span data-stu-id="eab84-238">-Begin</span></span>

<span data-ttu-id="eab84-239">Hiermee geeft u een scriptblok op dat wordt uitgevoerd voordat deze cmdlet invoerobjecten verwerkt.</span><span class="sxs-lookup"><span data-stu-id="eab84-239">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="eab84-240">Dit scriptblok wordt slechts één keer uitgevoerd voor de hele pijplijn.</span><span class="sxs-lookup"><span data-stu-id="eab84-240">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="eab84-241">Zie voor meer informatie `begin` over het [blok about_Functions.](about/about_functions.md#piping-objects-to-functions)</span><span class="sxs-lookup"><span data-stu-id="eab84-241">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-242">-End</span><span class="sxs-lookup"><span data-stu-id="eab84-242">-End</span></span>

<span data-ttu-id="eab84-243">Hiermee geeft u een scriptblok op dat wordt uitgevoerd nadat deze cmdlet alle invoerobjecten verwerkt.</span><span class="sxs-lookup"><span data-stu-id="eab84-243">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="eab84-244">Dit scriptblok wordt slechts één keer uitgevoerd voor de hele pijplijn.</span><span class="sxs-lookup"><span data-stu-id="eab84-244">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="eab84-245">Zie voor meer informatie over het `end` [blok about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="eab84-245">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-246">-InputObject</span><span class="sxs-lookup"><span data-stu-id="eab84-246">-InputObject</span></span>

<span data-ttu-id="eab84-247">Hiermee geeft u de invoerobjecten.</span><span class="sxs-lookup"><span data-stu-id="eab84-247">Specifies the input objects.</span></span> <span data-ttu-id="eab84-248">`ForEach-Object` voert het scriptblok of de bewerkingsin instructie uit op elk invoerobject.</span><span class="sxs-lookup"><span data-stu-id="eab84-248">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="eab84-249">Voer een variabele in die de objecten bevat of typ een opdracht of expressie die de objecten op haalt.</span><span class="sxs-lookup"><span data-stu-id="eab84-249">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="eab84-250">Wanneer u de **parameter InputObject** gebruikt met , in plaats van opdrachtresultaten door te spitten naar , wordt de `ForEach-Object` waarde `ForEach-Object` **InputObject** behandeld als één object.</span><span class="sxs-lookup"><span data-stu-id="eab84-250">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="eab84-251">Dit geldt zelfs als de waarde een verzameling is die het resultaat is van een opdracht, zoals `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="eab84-251">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="eab84-252">Omdat **InputObject** geen afzonderlijke eigenschappen van een matrix of verzameling objecten kan retourneren, raden we u aan om in de pijplijn te gebruiken om bewerkingen uit te voeren op een verzameling objecten voor objecten die specifieke waarden in gedefinieerde eigenschappen hebben, zoals wordt weergegeven in de voorbeelden `ForEach-Object` in dit `ForEach-Object` onderwerp.</span><span class="sxs-lookup"><span data-stu-id="eab84-252">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="eab84-253">-MemberName</span><span class="sxs-lookup"><span data-stu-id="eab84-253">-MemberName</span></span>

<span data-ttu-id="eab84-254">Hiermee geeft u de eigenschap op die moet worden get of de methode die moet worden aanroepen.</span><span class="sxs-lookup"><span data-stu-id="eab84-254">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="eab84-255">Jokertekens zijn toegestaan, maar werken alleen als de resulterende tekenreeks wordt opgelost naar een unieke waarde.</span><span class="sxs-lookup"><span data-stu-id="eab84-255">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="eab84-256">Als u bijvoorbeeld gebruikt, komt het jokertekenpatroon overeen met meer dan één lid, waardoor `Get-Process | ForEach -MemberName *Name` de opdracht mislukt.</span><span class="sxs-lookup"><span data-stu-id="eab84-256">For example, if you run `Get-Process | ForEach -MemberName *Name`, the wildcard pattern matches more than one member causing the command to fail.</span></span>

<span data-ttu-id="eab84-257">Deze parameter is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="eab84-257">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: PropertyAndMethodSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="eab84-258">-Proces</span><span class="sxs-lookup"><span data-stu-id="eab84-258">-Process</span></span>

<span data-ttu-id="eab84-259">Hiermee geeft u de bewerking die wordt uitgevoerd op elk invoerobject.</span><span class="sxs-lookup"><span data-stu-id="eab84-259">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="eab84-260">Dit scriptblok wordt uitgevoerd voor elk object in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="eab84-260">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="eab84-261">Zie voor meer informatie over het `process` [blok about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="eab84-261">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="eab84-262">Wanneer u meerdere scriptblokken aan de parameter **Process** opgeeft, wordt het eerste scriptblok altijd aan het blok `begin` doorgegeven.</span><span class="sxs-lookup"><span data-stu-id="eab84-262">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="eab84-263">Als er slechts twee scriptblokken zijn, wordt het tweede blok aan het blok `process` toegesneden.</span><span class="sxs-lookup"><span data-stu-id="eab84-263">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="eab84-264">Als er drie of meer scriptblokken zijn, wordt het eerste scriptblok altijd aan het blok toe te staan, wordt het laatste blok aan het blok toe te staan en worden de blokken daartussen allemaal aan het blok `begin` `end` `process` toegesneden.</span><span class="sxs-lookup"><span data-stu-id="eab84-264">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-265">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="eab84-265">-RemainingScripts</span></span>

<span data-ttu-id="eab84-266">Hiermee geeft u alle scriptblokken op die niet worden gebruikt door de parameter **Process.**</span><span class="sxs-lookup"><span data-stu-id="eab84-266">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="eab84-267">Deze parameter is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="eab84-267">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock[]
Parameter Sets: ScriptBlockSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-268">-Parallel</span><span class="sxs-lookup"><span data-stu-id="eab84-268">-Parallel</span></span>

<span data-ttu-id="eab84-269">Hiermee geeft u het scriptblok moet worden gebruikt voor parallelle verwerking van invoerobjecten.</span><span class="sxs-lookup"><span data-stu-id="eab84-269">Specifies the script block to be used for parallel processing of input objects.</span></span> <span data-ttu-id="eab84-270">Voer een scriptblok in dat de bewerking beschrijft.</span><span class="sxs-lookup"><span data-stu-id="eab84-270">Enter a script block that describes the operation.</span></span>

<span data-ttu-id="eab84-271">Deze parameter is geïntroduceerd in PowerShell 7.0.</span><span class="sxs-lookup"><span data-stu-id="eab84-271">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ParallelParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-272">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="eab84-272">-ThrottleLimit</span></span>

<span data-ttu-id="eab84-273">Hiermee geeft u het aantal scriptblokken op dat parallel wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eab84-273">Specifies the number of script blocks that in parallel.</span></span> <span data-ttu-id="eab84-274">Invoerobjecten worden geblokkeerd totdat het aantal blokkeringen van lopende scripts onder **throttleLimit valt.**</span><span class="sxs-lookup"><span data-stu-id="eab84-274">Input objects are blocked until the running script block count falls below the **ThrottleLimit**.</span></span> <span data-ttu-id="eab84-275">De standaardwaarde is `5`.</span><span class="sxs-lookup"><span data-stu-id="eab84-275">The default value is `5`.</span></span>

<span data-ttu-id="eab84-276">Deze parameter is geïntroduceerd in PowerShell 7.0.</span><span class="sxs-lookup"><span data-stu-id="eab84-276">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-277">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="eab84-277">-TimeoutSeconds</span></span>

<span data-ttu-id="eab84-278">Hiermee geeft u het aantal seconden op dat moet worden gewacht totdat alle invoer parallel wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="eab84-278">Specifies the number of seconds to wait for all input to be processed in parallel.</span></span> <span data-ttu-id="eab84-279">Na de opgegeven time-outtijd worden alle scripts gestopt die worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eab84-279">After the specified timeout time, all running scripts are stopped.</span></span> <span data-ttu-id="eab84-280">En alle resterende invoerobjecten die moeten worden verwerkt, worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="eab84-280">And any remaining input objects to be processed are ignored.</span></span> <span data-ttu-id="eab84-281">De standaardwaarde `0` van schakelt de time-out uit en `ForEach-Object -Parallel` kan voor onbepaalde tijd worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eab84-281">Default value of `0` disables the timeout, and `ForEach-Object -Parallel` can run indefinitely.</span></span> <span data-ttu-id="eab84-282">Als <kbd>u Ctrl</kbd> + <kbd>C op</kbd> de opdrachtregel typt, wordt een lopende opdracht `ForEach-Object -Parallel` gestopt.</span><span class="sxs-lookup"><span data-stu-id="eab84-282">Typing <kbd>Ctrl</kbd>+<kbd>C</kbd> at the command line stops a running `ForEach-Object -Parallel` command.</span></span> <span data-ttu-id="eab84-283">Deze parameter kan niet worden gebruikt samen met de **AsJob** parameter.</span><span class="sxs-lookup"><span data-stu-id="eab84-283">This parameter cannot be used along with the **AsJob** parameter.</span></span>

<span data-ttu-id="eab84-284">Deze parameter is geïntroduceerd in PowerShell 7.0.</span><span class="sxs-lookup"><span data-stu-id="eab84-284">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-285">-UseNewRunspace</span><span class="sxs-lookup"><span data-stu-id="eab84-285">-UseNewRunspace</span></span>

<span data-ttu-id="eab84-286">Zorgt ervoor dat de parallelle aanroep een nieuwe runspace maakt voor elke herhaling van lussen in plaats van runspaces uit de runspace-pool opnieuw te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="eab84-286">Causes the parallel invocation to create a new runspace for every loop iteration instead of reusing runspaces from the runspace pool.</span></span>

<span data-ttu-id="eab84-287">Deze parameter is geïntroduceerd in PowerShell 7.1</span><span class="sxs-lookup"><span data-stu-id="eab84-287">This parameter was introduced in PowerShell 7.1</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-288">-AsJob</span><span class="sxs-lookup"><span data-stu-id="eab84-288">-AsJob</span></span>

<span data-ttu-id="eab84-289">Zorgt ervoor dat de parallelle aanroep wordt uitgevoerd als een PowerShell-taak.</span><span class="sxs-lookup"><span data-stu-id="eab84-289">Causes the parallel invocation to run as a PowerShell job.</span></span> <span data-ttu-id="eab84-290">Er wordt één taakobject geretourneerd in plaats van uitvoer van de lopende scriptblokken.</span><span class="sxs-lookup"><span data-stu-id="eab84-290">A single job object is returned instead of output from the running script blocks.</span></span> <span data-ttu-id="eab84-291">Het taakobject bevat onderliggende taken voor elk parallel scriptblok dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eab84-291">The job object contains child jobs for each parallel script block that runs.</span></span> <span data-ttu-id="eab84-292">Het taakobject kan worden gebruikt door alle PowerShell-taak-cmdlets om de status van de lopende taak te bewaken en gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="eab84-292">The job object can be used by all PowerShell job cmdlets, to monitor running state and retrieve data.</span></span>

<span data-ttu-id="eab84-293">Deze parameter is geïntroduceerd in PowerShell 7.0.</span><span class="sxs-lookup"><span data-stu-id="eab84-293">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-294">-Confirm</span><span class="sxs-lookup"><span data-stu-id="eab84-294">-Confirm</span></span>

<span data-ttu-id="eab84-295">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="eab84-295">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-296">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="eab84-296">-WhatIf</span></span>

<span data-ttu-id="eab84-297">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="eab84-297">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="eab84-298">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="eab84-298">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eab84-299">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eab84-299">CommonParameters</span></span>

<span data-ttu-id="eab84-300">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="eab84-300">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="eab84-301">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="eab84-301">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="eab84-302">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="eab84-302">Inputs</span></span>

### <span data-ttu-id="eab84-303">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="eab84-303">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="eab84-304">U kunt elk object doorseen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eab84-304">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="eab84-305">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="eab84-305">Outputs</span></span>

### <span data-ttu-id="eab84-306">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="eab84-306">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="eab84-307">Deze cmdlet retourneert objecten die worden bepaald door de invoer.</span><span class="sxs-lookup"><span data-stu-id="eab84-307">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="eab84-308">Notities</span><span class="sxs-lookup"><span data-stu-id="eab84-308">Notes</span></span>

- <span data-ttu-id="eab84-309">De `ForEach-Object` cmdlet werkt op dezelfde als de **Foreach-instructie,** behalve dat u geen invoer kunt doorspijpen naar een **Foreach-instructie.**</span><span class="sxs-lookup"><span data-stu-id="eab84-309">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="eab84-310">Zie voor meer informatie over de **Foreach-instructie** [about_Foreach.](./About/about_Foreach.md)</span><span class="sxs-lookup"><span data-stu-id="eab84-310">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="eab84-311">Vanaf PowerShell 4.0 zijn er methoden toegevoegd voor `Where` `ForEach` gebruik met verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="eab84-311">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="eab84-312">Meer informatie over deze nieuwe methoden vindt u [hier about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="eab84-312">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

- <span data-ttu-id="eab84-313">De `ForEach-Object -Parallel` parameterset maakt gebruik van de interne API van PowerShell om elk scriptblok uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="eab84-313">The `ForEach-Object -Parallel` parameter set uses PowerShell's internal API to run each script block.</span></span> <span data-ttu-id="eab84-314">Dit is aanzienlijk meer overhead dan normaal `ForEach-Object` uitvoeren met sequentiële verwerking.</span><span class="sxs-lookup"><span data-stu-id="eab84-314">This is significantly more overhead than running `ForEach-Object` normally with sequential processing.</span></span> <span data-ttu-id="eab84-315">Het is belangrijk om Parallel te **gebruiken,** waarbij de overhead van het parallel uitvoeren klein is in vergelijking met het werk dat het scriptblok uitvoert.</span><span class="sxs-lookup"><span data-stu-id="eab84-315">It is important to use **Parallel** where the overhead of running in parallel is small compared to work the script block performs.</span></span> <span data-ttu-id="eab84-316">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="eab84-316">For example:</span></span>

  - <span data-ttu-id="eab84-317">Rekenintensieve scripts op computers met meerdere kernen</span><span class="sxs-lookup"><span data-stu-id="eab84-317">Compute intensive scripts on multi-core machines</span></span>
  - <span data-ttu-id="eab84-318">Scripts die tijd besteden aan het wachten op resultaten of het uitvoeren van bestandsbewerkingen</span><span class="sxs-lookup"><span data-stu-id="eab84-318">Scripts that spend time waiting for results or doing file operations</span></span>

  <span data-ttu-id="eab84-319">Het gebruik **van de** parameter Parallel kan ertoe leiden dat scripts veel langzamer worden uitgevoerd dan normaal.</span><span class="sxs-lookup"><span data-stu-id="eab84-319">Using the **Parallel** parameter can cause scripts to run much slower than normal.</span></span> <span data-ttu-id="eab84-320">Met name als de parallelle scripts eenvoudig zijn.</span><span class="sxs-lookup"><span data-stu-id="eab84-320">Especially if the parallel scripts are trivial.</span></span> <span data-ttu-id="eab84-321">Experimenteer **met Parallel** om te ontdekken waar het nuttig kan zijn.</span><span class="sxs-lookup"><span data-stu-id="eab84-321">Experiment with **Parallel** to discover where it can be beneficial.</span></span>

- <span data-ttu-id="eab84-322">[Veelvoorkomende parametervariabelen voor PipelineVariable](About/about_CommonParameters.md) worden niet ondersteund in  `Foreach-Object -Parallel` scenario's, zelfs niet met het `$using:` trefwoord .</span><span class="sxs-lookup"><span data-stu-id="eab84-322">[PipelineVariable](About/about_CommonParameters.md) common parameter variables are _not_ supported in `Foreach-Object -Parallel` scenarios even with the `$using:` keyword.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="eab84-323">Met `ForEach-Object -Parallel` de parameterset worden scriptblokken parallel uitgevoerd op afzonderlijke procesthreads.</span><span class="sxs-lookup"><span data-stu-id="eab84-323">The `ForEach-Object -Parallel` parameter set runs script blocks in parallel on separate process threads.</span></span> <span data-ttu-id="eab84-324">Met `$using:` het trefwoord kunnen variabelenverwijzingen van de cmdlet-aanroepthread worden doorgeven aan elke thread met het lopende scriptblok.</span><span class="sxs-lookup"><span data-stu-id="eab84-324">The `$using:` keyword allows passing variable references from the cmdlet invocation thread to each running script block thread.</span></span> <span data-ttu-id="eab84-325">Omdat de scriptblokken worden uitgevoerd in verschillende threads, moeten de objectvariabelen die worden doorgegeven door verwijzing veilig worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="eab84-325">Since the script blocks run in different threads, the object variables passed by reference must be used safely.</span></span> <span data-ttu-id="eab84-326">Over het algemeen is het veilig om te lezen van objecten waarnaar wordt verwezen en die niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="eab84-326">Generally it is safe to read from referenced objects that don't change.</span></span> <span data-ttu-id="eab84-327">Maar als de objecttoestand wordt gewijzigd, moet u thread-veilige objecten gebruiken, zoals .NET **System.Collection.Concurrent-typen** (zie voorbeeld 11).</span><span class="sxs-lookup"><span data-stu-id="eab84-327">But if the object state is being modified then you must used thread safe objects, such as .Net **System.Collection.Concurrent** types (See Example 11).</span></span>

## <span data-ttu-id="eab84-328">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="eab84-328">Related links</span></span>

[<span data-ttu-id="eab84-329">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="eab84-329">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="eab84-330">Where-Object</span><span class="sxs-lookup"><span data-stu-id="eab84-330">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="eab84-331">Group-Object</span><span class="sxs-lookup"><span data-stu-id="eab84-331">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="eab84-332">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="eab84-332">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="eab84-333">New-Object</span><span class="sxs-lookup"><span data-stu-id="eab84-333">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="eab84-334">Select-Object</span><span class="sxs-lookup"><span data-stu-id="eab84-334">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="eab84-335">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="eab84-335">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="eab84-336">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="eab84-336">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
