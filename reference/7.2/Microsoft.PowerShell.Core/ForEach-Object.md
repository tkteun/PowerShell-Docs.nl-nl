---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: ee7b72d99c66023ca173e8a61fedda18ba9e2bc5
ms.sourcegitcommit: 366304d096c1caf52f0e17962f6ed23d20f86e7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2021
ms.locfileid: "107543775"
---
# <span data-ttu-id="9c70c-102">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="9c70c-102">ForEach-Object</span></span>

## <span data-ttu-id="9c70c-103">Synopsis</span><span class="sxs-lookup"><span data-stu-id="9c70c-103">Synopsis</span></span>
<span data-ttu-id="9c70c-104">Voert een bewerking uit op elk item in een verzameling invoerobjecten.</span><span class="sxs-lookup"><span data-stu-id="9c70c-104">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="9c70c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9c70c-105">Syntax</span></span>

### <span data-ttu-id="9c70c-106">ScriptBlockSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="9c70c-106">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9c70c-107">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="9c70c-107">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9c70c-108">ParallelParameterSet</span><span class="sxs-lookup"><span data-stu-id="9c70c-108">ParallelParameterSet</span></span>

```
ForEach-Object -Parallel <scriptblock> [-InputObject <PSObject>] [-ThrottleLimit <int>]
[-UseNewRunspace] [-TimeoutSeconds <int>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9c70c-109">Description</span><span class="sxs-lookup"><span data-stu-id="9c70c-109">Description</span></span>

<span data-ttu-id="9c70c-110">De `ForEach-Object` cmdlet voert een bewerking uit op elk item in een verzameling invoerobjecten.</span><span class="sxs-lookup"><span data-stu-id="9c70c-110">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="9c70c-111">De invoerobjecten kunnen worden doorgegeven aan de cmdlet of worden opgegeven met behulp van de **Parameter InputObject.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-111">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="9c70c-112">Vanaf Windows PowerShell 3.0 zijn er twee verschillende manieren om een opdracht te `ForEach-Object` maken.</span><span class="sxs-lookup"><span data-stu-id="9c70c-112">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="9c70c-113">**Scriptblok.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-113">**Script block**.</span></span> <span data-ttu-id="9c70c-114">U kunt een scriptblok gebruiken om de bewerking op te geven.</span><span class="sxs-lookup"><span data-stu-id="9c70c-114">You can use a script block to specify the operation.</span></span> <span data-ttu-id="9c70c-115">Gebruik in het scriptblok de variabele `$_` om het huidige object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9c70c-115">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="9c70c-116">Het scriptblok is de waarde van de **procesparameter.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-116">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="9c70c-117">Het scriptblok kan elk PowerShell-script bevatten.</span><span class="sxs-lookup"><span data-stu-id="9c70c-117">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="9c70c-118">Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap **ProcessName** van elk proces op de computer opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-118">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="9c70c-119">`ForEach-Object` ondersteunt de `begin` blokken , en zoals `process` `end` beschreven in [about_functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="9c70c-119">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="9c70c-120">De scriptblokken worden uitgevoerd in het bereik van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="9c70c-120">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="9c70c-121">De blokken hebben daarom toegang tot variabelen in dat bereik en kunnen nieuwe variabelen maken die in dat bereik blijven bestaan nadat de cmdlet is voltooid.</span><span class="sxs-lookup"><span data-stu-id="9c70c-121">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="9c70c-122">**Bewerkings instructie**.</span><span class="sxs-lookup"><span data-stu-id="9c70c-122">**Operation statement**.</span></span> <span data-ttu-id="9c70c-123">U kunt ook een bewerkingsverklaring schrijven, die veel meer lijkt op natuurlijke taal.</span><span class="sxs-lookup"><span data-stu-id="9c70c-123">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="9c70c-124">U kunt de instructie operation gebruiken om een eigenschapswaarde op te geven of een methode aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-124">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="9c70c-125">Bewerkingsverklaringen zijn geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="9c70c-125">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="9c70c-126">Met de volgende opdracht wordt bijvoorbeeld ook de waarde van de eigenschap **ProcessName** van elk proces op de computer opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-126">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

- <span data-ttu-id="9c70c-127">**Scriptblok parallel wordt uitgevoerd.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-127">**Parallel running script block**.</span></span> <span data-ttu-id="9c70c-128">Vanaf PowerShell 7.0 is er een derde parameterset beschikbaar die elk scriptblok parallel wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-128">Beginning with PowerShell 7.0, a third parameter set is available that runs each script block in parallel.</span></span> <span data-ttu-id="9c70c-129">De **parameter ThrottleLimit** beperkt het aantal parallelle scripts dat tegelijk wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-129">The **ThrottleLimit** parameter limits the number of parallel scripts running at a time.</span></span> <span data-ttu-id="9c70c-130">Gebruik net als voorheen de `$_` variabele om het huidige invoerobject in het scriptblok weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9c70c-130">As before, use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="9c70c-131">Gebruik het `$using:` trefwoord om variabelenverwijzingen door te geven aan het script dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-131">Use the `$using:` keyword to pass variable references to the running script.</span></span>

  <span data-ttu-id="9c70c-132">In PowerShell 7 wordt voor elke lus-iteratie een nieuwe runspace gemaakt om maximale isolatie te garanderen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-132">In PowerShell 7, a new runspace is created for each loop iteration to ensure maximum isolation.</span></span>
  <span data-ttu-id="9c70c-133">Dit kan een grote prestatie- en resource-hit zijn als het werk dat u doet klein is in vergelijking met het maken van nieuwe runspaces of als er veel iteraties zijn die aanzienlijk werk verrichten.</span><span class="sxs-lookup"><span data-stu-id="9c70c-133">This can be a large performance and resource hit if the work you are doing is small compared to creating new runspaces or if there are a lot of iterations performing significant work.</span></span> <span data-ttu-id="9c70c-134">Vanaf PowerShell 7.1 worden runspaces uit een runspacegroep standaard opnieuw gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-134">As of PowerShell 7.1, runspaces from a runspace pool are reused by default.</span></span> <span data-ttu-id="9c70c-135">De grootte van de runspacepool wordt opgegeven met de parameter **ThrottleLimit.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-135">The runspace pool size is specified by the **ThrottleLimit** parameter.</span></span> <span data-ttu-id="9c70c-136">De standaardgrootte van de runspacepool is 5.</span><span class="sxs-lookup"><span data-stu-id="9c70c-136">The default runspace pool size is 5.</span></span> <span data-ttu-id="9c70c-137">U kunt nog steeds een nieuwe runspace maken voor elke iteratie met behulp van **de switch UseNewRunspace.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-137">You can still create a new runspace for each iteration using the **UseNewRunspace** switch.</span></span>

  <span data-ttu-id="9c70c-138">De parallelle scriptblokkeringen gebruiken standaard de huidige werkmap van de aanroeper die de parallelle taken heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="9c70c-138">By default, the parallel scriptblocks use the current working directory of the caller that started the parallel tasks.</span></span>

  <span data-ttu-id="9c70c-139">Niet-beëindigingsfouten worden naar de foutstroom van de cmdlet geschreven wanneer deze zich voordoen in parallelle scriptblokkeringen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-139">Non-terminating errors are written to the cmdlet error stream as they occur in parallel running scriptblocks.</span></span> <span data-ttu-id="9c70c-140">Omdat parallelle scriptblokkeringsuitvoeringsorder niet kan worden bepaald, is de volgorde waarin fouten worden weergegeven in de foutstroom willekeurig.</span><span class="sxs-lookup"><span data-stu-id="9c70c-140">Because parallel scriptblock execution order cannot be determined, the order in which errors appear in the error stream is random.</span></span> <span data-ttu-id="9c70c-141">Berichten die naar andere gegevensstromen worden geschreven, zoals waarschuwing, uitgebreide informatie of informatie, worden in een onbepaalde volgorde naar deze gegevensstromen geschreven.</span><span class="sxs-lookup"><span data-stu-id="9c70c-141">Likewise, messages written to other data streams, like warning, verbose, or information are written to those data streams in an indeterminate order.</span></span>

  <span data-ttu-id="9c70c-142">Het beëindigen van fouten, zoals uitzonderingen, beëindigt het afzonderlijke parallelle exemplaar van de scriptblokkeringen waarin ze optreden.</span><span class="sxs-lookup"><span data-stu-id="9c70c-142">Terminating errors, such as exceptions, terminate the individual parallel instance of the scriptblocks in which they occur.</span></span> <span data-ttu-id="9c70c-143">Een beëindigingsfout in één scriptblokkering veroorzaakt mogelijk niet de beëindiging van de `Foreach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c70c-143">A terminating error in one scriptblocks may not cause the termination of the `Foreach-Object` cmdlet.</span></span> <span data-ttu-id="9c70c-144">De andere scriptblokkeringen, die parallel worden uitgevoerd, blijven actief, tenzij er ook een beëindigingsfout wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="9c70c-144">The other scriptblocks, running in parallel, continue to run unless they also encounter a terminating error.</span></span> <span data-ttu-id="9c70c-145">De beëindigingsfout wordt naar de gegevensstroom van de fout geschreven als **een ErrorRecord** met **een FullyQualifiedErrorId** van `PSTaskException` .</span><span class="sxs-lookup"><span data-stu-id="9c70c-145">The terminating error is written to the error data stream as an **ErrorRecord** with a **FullyQualifiedErrorId** of `PSTaskException`.</span></span>
  <span data-ttu-id="9c70c-146">Beëindigingsfouten kunnen worden geconverteerd naar niet-beëindigingsfouten met behulp van PowerShell-try/catch- of trapblokken.</span><span class="sxs-lookup"><span data-stu-id="9c70c-146">Terminating errors can be converted to non-terminating errors using PowerShell try/catch or trap blocks.</span></span>

## <span data-ttu-id="9c70c-147">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="9c70c-147">Examples</span></span>

### <span data-ttu-id="9c70c-148">Voorbeeld 1: Gehele getallen in een matrix delen</span><span class="sxs-lookup"><span data-stu-id="9c70c-148">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="9c70c-149">In dit voorbeeld wordt een matrix van drie gehele getallen gebruikt en wordt elk van deze door 1024 verdeeld.</span><span class="sxs-lookup"><span data-stu-id="9c70c-149">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="9c70c-150">Voorbeeld 2: de lengte van alle bestanden in een map op halen</span><span class="sxs-lookup"><span data-stu-id="9c70c-150">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="9c70c-151">In dit voorbeeld worden de bestanden en mappen in de Installatiemap van PowerShell `$PSHOME` verwerkt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-151">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="9c70c-152">Als het object geen map is, haalt het scriptblok de naam van het bestand op, deelt de waarde van de eigenschap **Length** door 1024 en voegt het een spatie ("") toe om het te scheiden van de volgende vermelding.</span><span class="sxs-lookup"><span data-stu-id="9c70c-152">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="9c70c-153">De cmdlet gebruikt de **eigenschap PSISContainer** om te bepalen of een object een map is.</span><span class="sxs-lookup"><span data-stu-id="9c70c-153">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="9c70c-154">Voorbeeld 3: De meest recente systeemgebeurtenissen gebruiken</span><span class="sxs-lookup"><span data-stu-id="9c70c-154">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="9c70c-155">In dit voorbeeld worden de 1000 meest recente gebeurtenissen uit het gebeurtenislogboek van Systeem naar een tekstbestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="9c70c-155">This example writes the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="9c70c-156">De huidige tijd wordt weergegeven voor en na het verwerken van de gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-156">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="9c70c-157">`Get-EventLog` haalt de 1000 meest recente gebeurtenissen uit het gebeurtenislogboek van systeem op en slaat deze op in de `$Events` variabele .</span><span class="sxs-lookup"><span data-stu-id="9c70c-157">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="9c70c-158">`$Events` wordt vervolgens doorspijpt naar `ForEach-Object` de cmdlet .</span><span class="sxs-lookup"><span data-stu-id="9c70c-158">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="9c70c-159">De **begin** parameter geeft de huidige datum en tijd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-159">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="9c70c-160">Vervolgens gebruikt de parameter **Process** de cmdlet om een tekstbestand met de naam events.txt te maken en slaat de bericht-eigenschap van elk van de gebeurtenissen `Out-File` in dat bestand op.</span><span class="sxs-lookup"><span data-stu-id="9c70c-160">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="9c70c-161">Ten laatste wordt de parameter **End** gebruikt om de datum en tijd weer te geven nadat alle verwerking is voltooid.</span><span class="sxs-lookup"><span data-stu-id="9c70c-161">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="9c70c-162">Voorbeeld 4: de waarde van een registersleutel wijzigen</span><span class="sxs-lookup"><span data-stu-id="9c70c-162">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="9c70c-163">In dit voorbeeld wordt de waarde van de **remotePath-registerinvoer** in alle subsleutels onder de sleutel gewijzigd in `HKCU:\Network` hoofdletters.</span><span class="sxs-lookup"><span data-stu-id="9c70c-163">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="9c70c-164">U kunt deze indeling gebruiken om het formulier of de inhoud van een registerinvoerwaarde te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-164">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="9c70c-165">Elke subsleutel in de **netwerksleutel** vertegenwoordigt een gekoppeld netwerkstation dat opnieuw verbinding maakt bij het aanmelden.</span><span class="sxs-lookup"><span data-stu-id="9c70c-165">Each subkey in the **Network** key represents a mapped network drive that reconnects at sign on.</span></span> <span data-ttu-id="9c70c-166">De **vermelding RemotePath** bevat het UNC-pad van het verbonden station.</span><span class="sxs-lookup"><span data-stu-id="9c70c-166">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="9c70c-167">Als u bijvoorbeeld het E:-station toe wijst aan , wordt `\\Server\Share` er een **E-subsleutel** gemaakt in met de `HKCU:\Network` **registerwaarde RemotePath** ingesteld op `\\Server\Share` .</span><span class="sxs-lookup"><span data-stu-id="9c70c-167">For example, if you map the E: drive to `\\Server\Share`, an **E** subkey is created in `HKCU:\Network` with the **RemotePath** registry value set to `\\Server\Share`.</span></span>

<span data-ttu-id="9c70c-168">De opdracht gebruikt de cmdlet om alle subsleutels van de netwerksleutel op te halen en de cmdlet om de waarde van de `Get-ItemProperty`  `Set-ItemProperty` **RemotePath-registerinvoer** in elke sleutel te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-168">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="9c70c-169">In de `Set-ItemProperty` opdracht is het pad de waarde van de eigenschap **PSPath** van de registersleutel.</span><span class="sxs-lookup"><span data-stu-id="9c70c-169">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="9c70c-170">Dit is een eigenschap van het Microsoft .NET Framework-object dat de registersleutel vertegenwoordigt, niet een registerinvoer.</span><span class="sxs-lookup"><span data-stu-id="9c70c-170">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="9c70c-171">De opdracht maakt gebruik **van de methode ToUpper()** van de **RemotePath-waarde.** Dit is een tekenreeks (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="9c70c-171">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="9c70c-172">Omdat `Set-ItemProperty` de eigenschap van elke sleutel wordt veranderd, is de `ForEach-Object` cmdlet vereist voor toegang tot de eigenschap .</span><span class="sxs-lookup"><span data-stu-id="9c70c-172">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="9c70c-173">Voorbeeld 5: De automatische $Null gebruiken</span><span class="sxs-lookup"><span data-stu-id="9c70c-173">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="9c70c-174">In dit voorbeeld ziet u het effect van het doorspijpen van `$Null` de automatische variabele naar de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c70c-174">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="9c70c-175">Omdat PowerShell null als een expliciete tijdelijke aanduiding behandelt, genereert de cmdlet een waarde voor , net als voor andere objecten die u er naar `ForEach-Object` doorspijpt. `$Null`</span><span class="sxs-lookup"><span data-stu-id="9c70c-175">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="9c70c-176">Voorbeeld 6: Eigenschapswaarden op halen</span><span class="sxs-lookup"><span data-stu-id="9c70c-176">Example 6: Get property values</span></span>

<span data-ttu-id="9c70c-177">In dit voorbeeld wordt de waarde van de **eigenschap Path** van alle geïnstalleerde PowerShell-modules met behulp van de parameter **MemberName** van de `ForEach-Object` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="9c70c-177">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="9c70c-178">De tweede opdracht is gelijk aan de eerste.</span><span class="sxs-lookup"><span data-stu-id="9c70c-178">The second command is equivalent to the first.</span></span> <span data-ttu-id="9c70c-179">Hierbij wordt de alias van de cmdlet gebruikt en wordt de naam van de `Foreach` `ForEach-Object` parameter **MemberName** weglaat, wat optioneel is.</span><span class="sxs-lookup"><span data-stu-id="9c70c-179">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="9c70c-180">De cmdlet is handig voor het verkrijgen van eigenschapswaarden, omdat deze de waarde krijgt zonder het type te wijzigen, in tegenstelling tot de cmdlets Format of `ForEach-Object` de cmdlet , waarmee het waardetype van de eigenschap wordt  `Select-Object` gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-180">The `ForEach-Object` cmdlet is useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="9c70c-181">Voorbeeld 7: Modulenamen splitsen in onderdeelnamen</span><span class="sxs-lookup"><span data-stu-id="9c70c-181">Example 7: Split module names into component names</span></span>

<span data-ttu-id="9c70c-182">In dit voorbeeld ziet u drie manieren om twee modulenamen met punten te splitsen in de onderdeelnamen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-182">This example shows three ways to split two dot-separated module names into their component names.</span></span>

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

<span data-ttu-id="9c70c-183">Met de opdrachten wordt de **methode Splitsen van** tekenreeksen aanroepen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-183">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="9c70c-184">Voor de drie opdrachten wordt een andere syntaxis gebruikt, maar deze zijn gelijkwaardig en uitwisselbaar.</span><span class="sxs-lookup"><span data-stu-id="9c70c-184">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="9c70c-185">De eerste opdracht maakt gebruik van de traditionele syntaxis, die een scriptblok en de huidige objectoperator `$_` bevat.</span><span class="sxs-lookup"><span data-stu-id="9c70c-185">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="9c70c-186">Er wordt gebruikgemaakt van de puntsyntaxis om de methode en haakjes op te geven om het scheidingstekenargument om te zetten.</span><span class="sxs-lookup"><span data-stu-id="9c70c-186">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="9c70c-187">De tweede opdracht gebruikt de **parameter MemberName** om de methode **Split** en de parameter **ArgumentName** op te geven om de punt (".") te identificeren als het scheidingsteken voor splitsen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-187">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="9c70c-188">De derde opdracht maakt gebruik van de **Foreach-alias** van de cmdlet en laat de namen van de `ForEach-Object` parameters **MemberName** en **ArgumentList** weg, die optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="9c70c-188">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="9c70c-189">Voorbeeld 8: Een ForEach-Object twee scriptblokken gebruiken</span><span class="sxs-lookup"><span data-stu-id="9c70c-189">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="9c70c-190">In dit voorbeeld geven we twee scriptblokken positioneel door.</span><span class="sxs-lookup"><span data-stu-id="9c70c-190">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="9c70c-191">Alle scriptblokken worden aan de **procesparameter** binden.</span><span class="sxs-lookup"><span data-stu-id="9c70c-191">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="9c70c-192">Ze worden echter behandeld alsof ze zijn doorgegeven aan de **parameters Begin** **en Process.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-192">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="9c70c-193">Voorbeeld 9: ForEach-Object gebruiken met meer dan twee scriptblokken</span><span class="sxs-lookup"><span data-stu-id="9c70c-193">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="9c70c-194">In dit voorbeeld geven we twee scriptblokken positioneel door.</span><span class="sxs-lookup"><span data-stu-id="9c70c-194">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="9c70c-195">Alle scriptblokken worden aan de **procesparameter** binden.</span><span class="sxs-lookup"><span data-stu-id="9c70c-195">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="9c70c-196">Ze worden echter behandeld alsof ze zijn doorgegeven aan de parameters **Begin,** **Process** en **End.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-196">However, they are treated as if they had been passed to the **Begin**, **Process**, and **End** parameters.</span></span>

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
> <span data-ttu-id="9c70c-197">Het eerste scriptblok wordt altijd aan het blok toegesneden, het laatste blok wordt aan het blok en de blokken ertussen zijn allemaal aan `begin` het blok toe te `end` `process` staan.</span><span class="sxs-lookup"><span data-stu-id="9c70c-197">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="9c70c-198">Voorbeeld 10: Meerdere scriptblokken uitvoeren voor elk pijplijnitem</span><span class="sxs-lookup"><span data-stu-id="9c70c-198">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="9c70c-199">Zoals u in het vorige voorbeeld kunt zien, worden meerdere scriptblokken die zijn doorgegeven met behulp van de parameter **Process,** aan de parameters **Begin** en **End** doorgegeven.</span><span class="sxs-lookup"><span data-stu-id="9c70c-199">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="9c70c-200">Als u deze toewijzing wilt voorkomen, moet u expliciete waarden opgeven voor de parameters **Begin** **en End.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-200">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

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

### <span data-ttu-id="9c70c-201">Voorbeeld 11: Langzaam script uitvoeren in parallelle batches</span><span class="sxs-lookup"><span data-stu-id="9c70c-201">Example 11: Run slow script in parallel batches</span></span>

<span data-ttu-id="9c70c-202">In dit voorbeeld wordt een eenvoudig scriptblok uitgevoerd dat een tekenreeks evalueert en één seconde in de slaapstand gaat.</span><span class="sxs-lookup"><span data-stu-id="9c70c-202">This example runs a simple script block that evaluates a string and sleeps for one second.</span></span>

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

<span data-ttu-id="9c70c-203">De **parameterwaarde ThrottleLimit** is ingesteld op 4, zodat de invoer wordt verwerkt in batches van vier.</span><span class="sxs-lookup"><span data-stu-id="9c70c-203">The **ThrottleLimit** parameter value is set to 4 so that the input is processed in batches of four.</span></span>
<span data-ttu-id="9c70c-204">Het `$using:` trefwoord wordt gebruikt om de variabele `$Message` door te geven aan elk parallel scriptblok.</span><span class="sxs-lookup"><span data-stu-id="9c70c-204">The `$using:` keyword is used to pass the `$Message` variable into each parallel script block.</span></span>

### <span data-ttu-id="9c70c-205">Voorbeeld 12: Logboekgegevens parallel ophalen</span><span class="sxs-lookup"><span data-stu-id="9c70c-205">Example 12: Retrieve log entries in parallel</span></span>

<span data-ttu-id="9c70c-206">In dit voorbeeld worden 50.000 logboekgegevens opgehaald uit 5 systeemlogboeken op een lokale Windows-computer.</span><span class="sxs-lookup"><span data-stu-id="9c70c-206">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine.</span></span>

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

<span data-ttu-id="9c70c-207">De **parameter Parallel** geeft het scriptblok aan dat parallel wordt uitgevoerd voor elke naam van het invoerlogboek.</span><span class="sxs-lookup"><span data-stu-id="9c70c-207">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span> <span data-ttu-id="9c70c-208">De **parameter ThrottleLimit** zorgt ervoor dat alle vijf scriptblokken tegelijkertijd worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-208">The **ThrottleLimit** parameter ensures that all five script blocks run at the same time.</span></span>

### <span data-ttu-id="9c70c-209">Voorbeeld 13: Parallel uitvoeren als een taak</span><span class="sxs-lookup"><span data-stu-id="9c70c-209">Example 13: Run in parallel as a job</span></span>

<span data-ttu-id="9c70c-210">In dit voorbeeld wordt een eenvoudig scriptblok parallel uitgevoerd, waardoor er twee achtergrondtaken tegelijk worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-210">This example runs a simple script block in parallel, creating two background jobs at a time.</span></span>

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

<span data-ttu-id="9c70c-211">de `$job` variabele ontvangt het taakobject dat uitvoergegevens verzamelt en de status van de uitvoer bewaakt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-211">the `$job` variable receives the job object that collects output data and monitors running state.</span></span>
<span data-ttu-id="9c70c-212">Het taakobject wordt doorspijpt `Receive-Job` naar met de parameter **Wait** switch.</span><span class="sxs-lookup"><span data-stu-id="9c70c-212">The job object is piped to `Receive-Job` with the **Wait** switch parameter.</span></span> <span data-ttu-id="9c70c-213">En deze streamt uitvoer naar de console, alsof `ForEach-Object -Parallel` deze is uitgevoerd zonder **AsJob**.</span><span class="sxs-lookup"><span data-stu-id="9c70c-213">And this streams output to the console, just as if `ForEach-Object -Parallel` was run without **AsJob**.</span></span>

### <span data-ttu-id="9c70c-214">Voorbeeld 14: Verwijzingen naar veilige threadvariabelen gebruiken</span><span class="sxs-lookup"><span data-stu-id="9c70c-214">Example 14: Using thread safe variable references</span></span>

<span data-ttu-id="9c70c-215">In dit voorbeeld worden scriptblokken parallel aanroepen om unieke benoemde Procesobjecten te verzamelen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-215">This example invokes script blocks in parallel to collect uniquely named Process objects.</span></span>

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

<span data-ttu-id="9c70c-216">Er wordt één exemplaar van een **ConcurrentDictionary-object** doorgegeven aan elk scriptblok om de objecten te verzamelen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-216">A single instance of a **ConcurrentDictionary** object is passed to each script block to collect the objects.</span></span> <span data-ttu-id="9c70c-217">Omdat **concurrentDictionary thread-veilig** is, is het veilig om te worden gewijzigd door elk parallel script.</span><span class="sxs-lookup"><span data-stu-id="9c70c-217">Since the **ConcurrentDictionary** is thread safe, it is safe to be modified by each parallel script.</span></span> <span data-ttu-id="9c70c-218">Een niet-thread-veilig object, zoals **System.Collections.Generic.Dictionary,** is hier niet veilig te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9c70c-218">A non-thread-safe object, such as **System.Collections.Generic.Dictionary**, would not be safe to use here.</span></span>

> [!NOTE]
> <span data-ttu-id="9c70c-219">Dit voorbeeld is een zeer inefficiënt gebruik van **de parameter Parallel.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-219">This example is a very inefficient use of **Parallel** parameter.</span></span> <span data-ttu-id="9c70c-220">Het script voegt gewoon het invoerobject toe aan een gelijktijdig woordenboekobject.</span><span class="sxs-lookup"><span data-stu-id="9c70c-220">The script simply adds the input object to a concurrent dictionary object.</span></span> <span data-ttu-id="9c70c-221">Het is eenvoudig en de overhead van het aanroepen van elk script in een afzonderlijke thread niet waard.</span><span class="sxs-lookup"><span data-stu-id="9c70c-221">It is trivial and not worth the overhead of invoking each script in a separate thread.</span></span> <span data-ttu-id="9c70c-222">Normaal `ForEach-Object` uitvoeren zonder de **parallelle** switch is veel efficiënter en sneller.</span><span class="sxs-lookup"><span data-stu-id="9c70c-222">Running `ForEach-Object` normally without the **Parallel** switch is much more efficient and faster.</span></span> <span data-ttu-id="9c70c-223">Dit voorbeeld is alleen bedoeld om te laten zien hoe u thread-veilige variabelen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-223">This example is only intended to demonstrate how to use thread safe variables.</span></span>

### <span data-ttu-id="9c70c-224">Voorbeeld 15: Fouten schrijven met parallelle uitvoering</span><span class="sxs-lookup"><span data-stu-id="9c70c-224">Example 15: Writing errors with parallel execution</span></span>

<span data-ttu-id="9c70c-225">In dit voorbeeld wordt parallel naar de foutstroom geschreven, waarbij de volgorde van geschreven fouten willekeurig is.</span><span class="sxs-lookup"><span data-stu-id="9c70c-225">This example writes to the error stream in parallel, where the order of written errors is random.</span></span>

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

### <span data-ttu-id="9c70c-226">Voorbeeld 16: Fouten bij parallelle uitvoering beëindigen</span><span class="sxs-lookup"><span data-stu-id="9c70c-226">Example 16: Terminating errors in parallel execution</span></span>

<span data-ttu-id="9c70c-227">In dit voorbeeld wordt een beëindigingsfout in één parallel uitgevoerd scriptblok gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-227">This example demonstrates a terminating error in one parallel running scriptblock.</span></span>

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

<span data-ttu-id="9c70c-228">`Output: 3` wordt nooit geschreven omdat het parallelle scriptblok voor die iteratie is beëindigd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-228">`Output: 3` is never written because the parallel scriptblock for that iteration was terminated.</span></span>

> [!NOTE]
> <span data-ttu-id="9c70c-229">[Veelvoorkomende parametervariabelen voor PipelineVariable](About/about_CommonParameters.md) worden niet ondersteund in _scenario's,_ `Foreach-Object -Parallel` zelfs niet met het `$using:` trefwoord .</span><span class="sxs-lookup"><span data-stu-id="9c70c-229">[PipelineVariable](About/about_CommonParameters.md) common parameter variables are _not_ supported in `Foreach-Object -Parallel` scenarios even with the `$using:` keyword.</span></span>

## <span data-ttu-id="9c70c-230">Parameters</span><span class="sxs-lookup"><span data-stu-id="9c70c-230">Parameters</span></span>

### <span data-ttu-id="9c70c-231">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="9c70c-231">-ArgumentList</span></span>

<span data-ttu-id="9c70c-232">Hiermee geeft u een matrix van argumenten op voor een methode-aanroep.</span><span class="sxs-lookup"><span data-stu-id="9c70c-232">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="9c70c-233">Zie voor meer informatie over het gedrag van **ArgumentList** [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="9c70c-233">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="9c70c-234">Deze parameter is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="9c70c-234">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9c70c-235">-Begin</span><span class="sxs-lookup"><span data-stu-id="9c70c-235">-Begin</span></span>

<span data-ttu-id="9c70c-236">Hiermee geeft u een scriptblok op dat wordt uitgevoerd voordat deze cmdlet invoerobjecten verwerkt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-236">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="9c70c-237">Dit scriptblok wordt slechts één keer uitgevoerd voor de hele pijplijn.</span><span class="sxs-lookup"><span data-stu-id="9c70c-237">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="9c70c-238">Zie voor meer informatie `begin` over het [blok about_Functions.](about/about_functions.md#piping-objects-to-functions)</span><span class="sxs-lookup"><span data-stu-id="9c70c-238">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

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

### <span data-ttu-id="9c70c-239">-End</span><span class="sxs-lookup"><span data-stu-id="9c70c-239">-End</span></span>

<span data-ttu-id="9c70c-240">Hiermee geeft u een scriptblok op dat wordt uitgevoerd nadat deze cmdlet alle invoerobjecten verwerkt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-240">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="9c70c-241">Dit scriptblok wordt slechts één keer uitgevoerd voor de hele pijplijn.</span><span class="sxs-lookup"><span data-stu-id="9c70c-241">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="9c70c-242">Zie voor meer informatie `end` over het [blok about_Functions.](about/about_functions.md#piping-objects-to-functions)</span><span class="sxs-lookup"><span data-stu-id="9c70c-242">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

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

### <span data-ttu-id="9c70c-243">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9c70c-243">-InputObject</span></span>

<span data-ttu-id="9c70c-244">Hiermee geeft u de invoerobjecten.</span><span class="sxs-lookup"><span data-stu-id="9c70c-244">Specifies the input objects.</span></span> <span data-ttu-id="9c70c-245">`ForEach-Object` voert het scriptblok of de bewerkingsin instructie uit op elk invoerobject.</span><span class="sxs-lookup"><span data-stu-id="9c70c-245">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="9c70c-246">Voer een variabele in die de objecten bevat of typ een opdracht of expressie die de objecten op haalt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-246">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="9c70c-247">Wanneer u de **parameter InputObject** gebruikt met , in plaats van opdrachtresultaten door te spitten naar , wordt de `ForEach-Object` waarde `ForEach-Object` **InputObject** behandeld als één object.</span><span class="sxs-lookup"><span data-stu-id="9c70c-247">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="9c70c-248">Dit geldt zelfs als de waarde een verzameling is die het resultaat is van een opdracht, zoals `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="9c70c-248">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="9c70c-249">Omdat **InputObject** geen afzonderlijke eigenschappen van een matrix of verzameling objecten kan retourneren, raden we u aan om in de pijplijn te gebruiken om bewerkingen uit te voeren op een verzameling objecten voor objecten die specifieke waarden in gedefinieerde eigenschappen hebben, zoals wordt weergegeven in de voorbeelden `ForEach-Object` in dit `ForEach-Object` onderwerp.</span><span class="sxs-lookup"><span data-stu-id="9c70c-249">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="9c70c-250">-MemberName</span><span class="sxs-lookup"><span data-stu-id="9c70c-250">-MemberName</span></span>

<span data-ttu-id="9c70c-251">Hiermee geeft u de eigenschap op die moet worden get of de methode die moet worden aanroepen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-251">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="9c70c-252">Jokertekens zijn toegestaan, maar werken alleen als de resulterende tekenreeks wordt opgelost naar een unieke waarde.</span><span class="sxs-lookup"><span data-stu-id="9c70c-252">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="9c70c-253">Als u bijvoorbeeld gebruikt, komt het jokertekenpatroon overeen met meer dan één lid waardoor `Get-Process | ForEach -MemberName *Name` de opdracht mislukt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-253">For example, if you run `Get-Process | ForEach -MemberName *Name`, the wildcard pattern matches more than one member causing the command to fail.</span></span>

<span data-ttu-id="9c70c-254">Deze parameter is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="9c70c-254">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9c70c-255">-Proces</span><span class="sxs-lookup"><span data-stu-id="9c70c-255">-Process</span></span>

<span data-ttu-id="9c70c-256">Hiermee geeft u de bewerking die wordt uitgevoerd op elk invoerobject.</span><span class="sxs-lookup"><span data-stu-id="9c70c-256">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="9c70c-257">Dit scriptblok wordt uitgevoerd voor elk object in de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="9c70c-257">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="9c70c-258">Zie voor meer informatie over het `process` [blok about_Functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="9c70c-258">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="9c70c-259">Wanneer u meerdere scriptblokken aan de parameter **Process** opgeeft, wordt het eerste scriptblok altijd aan het blok `begin` doorgegeven.</span><span class="sxs-lookup"><span data-stu-id="9c70c-259">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="9c70c-260">Als er slechts twee scriptblokken zijn, wordt het tweede blok aan het blok `process` toegesneden.</span><span class="sxs-lookup"><span data-stu-id="9c70c-260">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="9c70c-261">Als er drie of meer scriptblokken zijn, wordt het eerste scriptblok altijd aan het blok toegesneden, wordt het laatste blok aan het blok en worden de blokken daartussen allemaal aan het blok `begin` `end` `process` toegesneden.</span><span class="sxs-lookup"><span data-stu-id="9c70c-261">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

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

### <span data-ttu-id="9c70c-262">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="9c70c-262">-RemainingScripts</span></span>

<span data-ttu-id="9c70c-263">Hiermee geeft u alle scriptblokken op die niet worden gebruikt door de parameter **Process.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-263">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="9c70c-264">Deze parameter is geïntroduceerd in Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="9c70c-264">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9c70c-265">-Parallel</span><span class="sxs-lookup"><span data-stu-id="9c70c-265">-Parallel</span></span>

<span data-ttu-id="9c70c-266">Hiermee geeft u het scriptblok moet worden gebruikt voor parallelle verwerking van invoerobjecten.</span><span class="sxs-lookup"><span data-stu-id="9c70c-266">Specifies the script block to be used for parallel processing of input objects.</span></span> <span data-ttu-id="9c70c-267">Voer een scriptblok in dat de bewerking beschrijft.</span><span class="sxs-lookup"><span data-stu-id="9c70c-267">Enter a script block that describes the operation.</span></span>

<span data-ttu-id="9c70c-268">Deze parameter is geïntroduceerd in PowerShell 7.0.</span><span class="sxs-lookup"><span data-stu-id="9c70c-268">This parameter was introduced in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="9c70c-269">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="9c70c-269">-ThrottleLimit</span></span>

<span data-ttu-id="9c70c-270">Hiermee geeft u het aantal scriptblokken op dat parallel wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-270">Specifies the number of script blocks that in parallel.</span></span> <span data-ttu-id="9c70c-271">Invoerobjecten worden geblokkeerd totdat het aantal blokkeringen van lopende scripts onder **throttleLimit valt.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-271">Input objects are blocked until the running script block count falls below the **ThrottleLimit**.</span></span> <span data-ttu-id="9c70c-272">De standaardwaarde is `5`.</span><span class="sxs-lookup"><span data-stu-id="9c70c-272">The default value is `5`.</span></span>

<span data-ttu-id="9c70c-273">Deze parameter is geïntroduceerd in PowerShell 7.0.</span><span class="sxs-lookup"><span data-stu-id="9c70c-273">This parameter was introduced in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="9c70c-274">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="9c70c-274">-TimeoutSeconds</span></span>

<span data-ttu-id="9c70c-275">Hiermee geeft u het aantal seconden op dat moet worden gewacht totdat alle invoer parallel wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-275">Specifies the number of seconds to wait for all input to be processed in parallel.</span></span> <span data-ttu-id="9c70c-276">Na de opgegeven time-outtijd worden alle scripts gestopt die worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-276">After the specified timeout time, all running scripts are stopped.</span></span> <span data-ttu-id="9c70c-277">En alle resterende invoerobjecten die moeten worden verwerkt, worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-277">And any remaining input objects to be processed are ignored.</span></span> <span data-ttu-id="9c70c-278">De standaardwaarde `0` van schakelt de time-out uit en `ForEach-Object -Parallel` kan voor onbepaalde tijd worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-278">Default value of `0` disables the timeout, and `ForEach-Object -Parallel` can run indefinitely.</span></span> <span data-ttu-id="9c70c-279">Als <kbd>u Ctrl</kbd> + <kbd>C op</kbd> de opdrachtregel typt, wordt een lopende opdracht `ForEach-Object -Parallel` gestopt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-279">Typing <kbd>Ctrl</kbd>+<kbd>C</kbd> at the command line stops a running `ForEach-Object -Parallel` command.</span></span> <span data-ttu-id="9c70c-280">Deze parameter kan niet worden gebruikt samen met de **AsJob** parameter.</span><span class="sxs-lookup"><span data-stu-id="9c70c-280">This parameter cannot be used along with the **AsJob** parameter.</span></span>

<span data-ttu-id="9c70c-281">Deze parameter is geïntroduceerd in PowerShell 7.0.</span><span class="sxs-lookup"><span data-stu-id="9c70c-281">This parameter was introduced in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="9c70c-282">-UseNewRunspace</span><span class="sxs-lookup"><span data-stu-id="9c70c-282">-UseNewRunspace</span></span>

<span data-ttu-id="9c70c-283">Zorgt ervoor dat de parallelle aanroep een nieuwe runspace maakt voor elke herhaling van lussen in plaats van runspaces uit de runspace-pool opnieuw te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="9c70c-283">Causes the parallel invocation to create a new runspace for every loop iteration instead of reusing runspaces from the runspace pool.</span></span>

<span data-ttu-id="9c70c-284">Deze parameter is geïntroduceerd in PowerShell 7.1</span><span class="sxs-lookup"><span data-stu-id="9c70c-284">This parameter was introduced in PowerShell 7.1</span></span>

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

### <span data-ttu-id="9c70c-285">-AsJob</span><span class="sxs-lookup"><span data-stu-id="9c70c-285">-AsJob</span></span>

<span data-ttu-id="9c70c-286">Zorgt ervoor dat de parallelle aanroep wordt uitgevoerd als een PowerShell-taak.</span><span class="sxs-lookup"><span data-stu-id="9c70c-286">Causes the parallel invocation to run as a PowerShell job.</span></span> <span data-ttu-id="9c70c-287">Er wordt één taakobject geretourneerd in plaats van uitvoer van de lopende scriptblokken.</span><span class="sxs-lookup"><span data-stu-id="9c70c-287">A single job object is returned instead of output from the running script blocks.</span></span> <span data-ttu-id="9c70c-288">Het taakobject bevat onderliggende taken voor elk parallel scriptblok dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-288">The job object contains child jobs for each parallel script block that runs.</span></span> <span data-ttu-id="9c70c-289">Het taakobject kan worden gebruikt door alle PowerShell-taak-cmdlets om de lopende status te bewaken en gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-289">The job object can be used by all PowerShell job cmdlets, to monitor running state and retrieve data.</span></span>

<span data-ttu-id="9c70c-290">Deze parameter is geïntroduceerd in PowerShell 7.0.</span><span class="sxs-lookup"><span data-stu-id="9c70c-290">This parameter was introduced in PowerShell 7.0.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: ParallelParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c70c-291">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9c70c-291">-Confirm</span></span>

<span data-ttu-id="9c70c-292">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9c70c-292">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c70c-293">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9c70c-293">-WhatIf</span></span>

<span data-ttu-id="9c70c-294">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9c70c-294">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9c70c-295">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-295">The cmdlet is not run.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c70c-296">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c70c-296">CommonParameters</span></span>

<span data-ttu-id="9c70c-297">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9c70c-297">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9c70c-298">Zie voor meer informatie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9c70c-298">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9c70c-299">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="9c70c-299">Inputs</span></span>

### <span data-ttu-id="9c70c-300">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="9c70c-300">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9c70c-301">U kunt elk object doorsleesen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c70c-301">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="9c70c-302">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="9c70c-302">Outputs</span></span>

### <span data-ttu-id="9c70c-303">System.Management.Automation.PSObject</span><span class="sxs-lookup"><span data-stu-id="9c70c-303">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9c70c-304">Deze cmdlet retourneert objecten die worden bepaald door de invoer.</span><span class="sxs-lookup"><span data-stu-id="9c70c-304">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="9c70c-305">Notities</span><span class="sxs-lookup"><span data-stu-id="9c70c-305">Notes</span></span>

- <span data-ttu-id="9c70c-306">De `ForEach-Object` cmdlet werkt net als de **Foreach-instructie,** behalve dat u geen invoer kunt doorspijpen naar een **Foreach-instructie.**</span><span class="sxs-lookup"><span data-stu-id="9c70c-306">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="9c70c-307">Zie voor meer informatie over de **Foreach-instructie** [about_Foreach](./About/about_Foreach.md).</span><span class="sxs-lookup"><span data-stu-id="9c70c-307">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="9c70c-308">Vanaf PowerShell 4.0 zijn er methoden toegevoegd voor `Where` `ForEach` gebruik met verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="9c70c-308">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="9c70c-309">Meer informatie over deze nieuwe methoden vindt u [hier about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="9c70c-309">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

- <span data-ttu-id="9c70c-310">De `ForEach-Object -Parallel` parameterset maakt gebruik van de interne API van PowerShell om elk scriptblok uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9c70c-310">The `ForEach-Object -Parallel` parameter set uses PowerShell's internal API to run each script block.</span></span> <span data-ttu-id="9c70c-311">Dit is aanzienlijk meer overhead dan normaal `ForEach-Object` uitvoeren met sequentiële verwerking.</span><span class="sxs-lookup"><span data-stu-id="9c70c-311">This is significantly more overhead than running `ForEach-Object` normally with sequential processing.</span></span> <span data-ttu-id="9c70c-312">Het is belangrijk om Parallel te **gebruiken,** waarbij de overhead van het parallel uitvoeren klein is in vergelijking met het werk dat het scriptblok uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9c70c-312">It is important to use **Parallel** where the overhead of running in parallel is small compared to work the script block performs.</span></span> <span data-ttu-id="9c70c-313">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9c70c-313">For example:</span></span>

  - <span data-ttu-id="9c70c-314">Rekenintensieve scripts op computers met meerdere kernen</span><span class="sxs-lookup"><span data-stu-id="9c70c-314">Compute intensive scripts on multi-core machines</span></span>
  - <span data-ttu-id="9c70c-315">Scripts die tijd besteden aan het wachten op resultaten of het uitvoeren van bestandsbewerkingen</span><span class="sxs-lookup"><span data-stu-id="9c70c-315">Scripts that spend time waiting for results or doing file operations</span></span>

  <span data-ttu-id="9c70c-316">Het gebruik **van de** parameter Parallel kan ertoe leiden dat scripts veel langzamer worden uitgevoerd dan normaal.</span><span class="sxs-lookup"><span data-stu-id="9c70c-316">Using the **Parallel** parameter can cause scripts to run much slower than normal.</span></span> <span data-ttu-id="9c70c-317">Met name als de parallelle scripts klein zijn.</span><span class="sxs-lookup"><span data-stu-id="9c70c-317">Especially if the parallel scripts are trivial.</span></span> <span data-ttu-id="9c70c-318">Experimenteer **met Parallel** om te ontdekken waar het nuttig kan zijn.</span><span class="sxs-lookup"><span data-stu-id="9c70c-318">Experiment with **Parallel** to discover where it can be beneficial.</span></span>

- <span data-ttu-id="9c70c-319">[Veelvoorkomende parametervariabelen voor PipelineVariable](About/about_CommonParameters.md) worden niet ondersteund in _scenario's,_ `Foreach-Object -Parallel` zelfs niet met het `$using:` trefwoord .</span><span class="sxs-lookup"><span data-stu-id="9c70c-319">[PipelineVariable](About/about_CommonParameters.md) common parameter variables are _not_ supported in `Foreach-Object -Parallel` scenarios even with the `$using:` keyword.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="9c70c-320">Met `ForEach-Object -Parallel` de parameterset worden scriptblokken parallel uitgevoerd op afzonderlijke procesthreads.</span><span class="sxs-lookup"><span data-stu-id="9c70c-320">The `ForEach-Object -Parallel` parameter set runs script blocks in parallel on separate process threads.</span></span> <span data-ttu-id="9c70c-321">Met `$using:` het trefwoord kunnen variabelenverwijzingen van de cmdlet-aanroepthread worden doorgeven aan elke lopende scriptblokthread.</span><span class="sxs-lookup"><span data-stu-id="9c70c-321">The `$using:` keyword allows passing variable references from the cmdlet invocation thread to each running script block thread.</span></span> <span data-ttu-id="9c70c-322">Omdat de scriptblokken worden uitgevoerd in verschillende threads, moeten de objectvariabelen die worden doorgegeven via verwijzing veilig worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9c70c-322">Since the script blocks run in different threads, the object variables passed by reference must be used safely.</span></span> <span data-ttu-id="9c70c-323">Over het algemeen is het veilig om te lezen van objecten waarnaar wordt verwezen en die niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="9c70c-323">Generally it is safe to read from referenced objects that don't change.</span></span> <span data-ttu-id="9c70c-324">Maar als de objecttoestand wordt gewijzigd, moet u thread-veilige objecten gebruiken, zoals .Net **System.Collection.Concurrent-typen** (zie voorbeeld 11).</span><span class="sxs-lookup"><span data-stu-id="9c70c-324">But if the object state is being modified then you must used thread safe objects, such as .Net **System.Collection.Concurrent** types (See Example 11).</span></span>

## <span data-ttu-id="9c70c-325">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="9c70c-325">Related links</span></span>

[<span data-ttu-id="9c70c-326">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="9c70c-326">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="9c70c-327">Where-Object</span><span class="sxs-lookup"><span data-stu-id="9c70c-327">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="9c70c-328">Groepsobject</span><span class="sxs-lookup"><span data-stu-id="9c70c-328">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="9c70c-329">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="9c70c-329">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="9c70c-330">New-Object</span><span class="sxs-lookup"><span data-stu-id="9c70c-330">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="9c70c-331">Select-Object</span><span class="sxs-lookup"><span data-stu-id="9c70c-331">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="9c70c-332">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="9c70c-332">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="9c70c-333">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="9c70c-333">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
