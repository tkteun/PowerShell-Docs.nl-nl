---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 09/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ForEach-Object
ms.openlocfilehash: c54efeb79f4129b55e078a1ccf9d46afc2e754ab
ms.sourcegitcommit: fb9bafd041e3615b9dc9fb77c9245581b705cd02
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725167"
---
# <span data-ttu-id="b641a-103">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="b641a-103">ForEach-Object</span></span>

## <span data-ttu-id="b641a-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="b641a-104">Synopsis</span></span>
<span data-ttu-id="b641a-105">Hiermee wordt een bewerking uitgevoerd voor elk item in een verzameling invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="b641a-105">Performs an operation against each item in a collection of input objects.</span></span>

## <span data-ttu-id="b641a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b641a-106">Syntax</span></span>

### <span data-ttu-id="b641a-107">ScriptBlockSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="b641a-107">ScriptBlockSet (Default)</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-Begin <ScriptBlock>] [-Process] <ScriptBlock[]>
 [-End <ScriptBlock>] [-RemainingScripts <ScriptBlock[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b641a-108">PropertyAndMethodSet</span><span class="sxs-lookup"><span data-stu-id="b641a-108">PropertyAndMethodSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] [-MemberName] <String> [-ArgumentList <Object[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b641a-109">ParallelParameterSet</span><span class="sxs-lookup"><span data-stu-id="b641a-109">ParallelParameterSet</span></span>

```
ForEach-Object [-InputObject <PSObject>] -Parallel <ScriptBlock> [-ThrottleLimit <Int32>]
 [-TimeoutSeconds <Int32>] [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b641a-110">Description</span><span class="sxs-lookup"><span data-stu-id="b641a-110">Description</span></span>

<span data-ttu-id="b641a-111">`ForEach-Object`Met de cmdlet wordt een bewerking uitgevoerd op elk item in een verzameling invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="b641a-111">The `ForEach-Object` cmdlet performs an operation on each item in a collection of input objects.</span></span> <span data-ttu-id="b641a-112">De invoer objecten kunnen worden gesluizen naar de cmdlet of worden opgegeven met behulp van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="b641a-112">The input objects can be piped to the cmdlet or specified by using the **InputObject** parameter.</span></span>

<span data-ttu-id="b641a-113">Vanaf Windows Power Shell 3,0 zijn er twee verschillende manieren om een opdracht te maken `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="b641a-113">Starting in Windows PowerShell 3.0, there are two different ways to construct a `ForEach-Object` command.</span></span>

- <span data-ttu-id="b641a-114">**Script blok**.</span><span class="sxs-lookup"><span data-stu-id="b641a-114">**Script block**.</span></span> <span data-ttu-id="b641a-115">U kunt een script blok gebruiken om de bewerking op te geven.</span><span class="sxs-lookup"><span data-stu-id="b641a-115">You can use a script block to specify the operation.</span></span> <span data-ttu-id="b641a-116">In het-script blok gebruikt `$_` u de variabele om het huidige object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="b641a-116">Within the script block, use the `$_` variable to represent the current object.</span></span> <span data-ttu-id="b641a-117">Het script blok is de waarde van de para meter **process** .</span><span class="sxs-lookup"><span data-stu-id="b641a-117">The script block is the value of the **Process** parameter.</span></span> <span data-ttu-id="b641a-118">Het script blok kan elk Power shell-script bevatten.</span><span class="sxs-lookup"><span data-stu-id="b641a-118">The script block can contain any PowerShell script.</span></span>

  <span data-ttu-id="b641a-119">Met de volgende opdracht wordt bijvoorbeeld de waarde van de eigenschap **proces** naam van elk proces op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b641a-119">For example, the following command gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object {$_.ProcessName}`

  <span data-ttu-id="b641a-120">`ForEach-Object` ondersteunt de `begin` , `process` , en `end` blokken zoals beschreven in [about_functions](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="b641a-120">`ForEach-Object` supports the `begin`, `process`, and `end` blocks as described in [about_functions](about/about_functions.md#piping-objects-to-functions).</span></span>

  > [!NOTE]
  > <span data-ttu-id="b641a-121">De script blokken worden uitgevoerd in het bereik van de aanroeper.</span><span class="sxs-lookup"><span data-stu-id="b641a-121">The script blocks run in the caller's scope.</span></span> <span data-ttu-id="b641a-122">De blokken hebben daarom toegang tot variabelen in dat bereik en kunnen nieuwe variabelen maken die in dat bereik behouden blijven nadat de cmdlet is voltooid.</span><span class="sxs-lookup"><span data-stu-id="b641a-122">Therefore the blocks have access to variables in that scope and can create new variables that persist in that scope after the cmdlet completes.</span></span>

- <span data-ttu-id="b641a-123">**Bewerkings instructie**.</span><span class="sxs-lookup"><span data-stu-id="b641a-123">**Operation statement**.</span></span> <span data-ttu-id="b641a-124">U kunt ook een bewerkings instructie schrijven die veel meer lijkt op natuurlijke taal.</span><span class="sxs-lookup"><span data-stu-id="b641a-124">You can also write an operation statement, which is much more like natural language.</span></span> <span data-ttu-id="b641a-125">U kunt de bewerkings instructie gebruiken om een eigenschaps waarde op te geven of een methode aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="b641a-125">You can use the operation statement to specify a property value or call a method.</span></span> <span data-ttu-id="b641a-126">Er zijn bewerkings instructies geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b641a-126">Operation statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="b641a-127">Met de volgende opdracht wordt ook de waarde van de eigenschap **proces** naam van elk proces op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b641a-127">For example, the following command also gets the value of the **ProcessName** property of each process on the computer.</span></span>

  `Get-Process | ForEach-Object ProcessName`

- <span data-ttu-id="b641a-128">**Parallel uitgevoerd script blok**.</span><span class="sxs-lookup"><span data-stu-id="b641a-128">**Parallel running script block**.</span></span> <span data-ttu-id="b641a-129">Vanaf Power shell 7,0 is een derde parameterset beschikbaar die elk script blok parallel uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b641a-129">Beginning with PowerShell 7.0, a third parameter set is available that runs each script block in parallel.</span></span> <span data-ttu-id="b641a-130">De para meter **ThrottleLimit** beperkt het aantal parallelle scripts dat op een bepaald moment wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-130">The **ThrottleLimit** parameter limits the number of parallel scripts running at a time.</span></span> <span data-ttu-id="b641a-131">Net als voorheen kunt u met de `$_` variabele het huidige invoer object weer geven in het-script blok.</span><span class="sxs-lookup"><span data-stu-id="b641a-131">As before, use the `$_` variable to represent the current input object in the script block.</span></span> <span data-ttu-id="b641a-132">Gebruik het `$using:` sleutel woord om variabele verwijzingen door te geven aan het script dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-132">Use the `$using:` keyword to pass variable references to the running script.</span></span>

  <span data-ttu-id="b641a-133">In Power shell 7 wordt een nieuwe runs Pace voor elke lus-iteratie gemaakt om de maximale isolatie te garanderen.</span><span class="sxs-lookup"><span data-stu-id="b641a-133">In PowerShell 7, a new runspace is created for each loop iteration to ensure maximum isolation.</span></span>
  <span data-ttu-id="b641a-134">Dit kan een grote prestatie en een bron zijn als het werk dat u uitvoert klein is in vergelijking met het maken van nieuwe runspaces of als er veel iteraties zijn die een aanzienlijke hoeveelheid werk uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b641a-134">This can be a large performance and resource hit if the work you are doing is small compared to creating new runspaces or if there are a lot of iterations performing significant work.</span></span>

  <span data-ttu-id="b641a-135">Standaard gebruikt de parallelle scriptblocks de huidige werkmap van de aanroeper die de parallelle taken heeft gestart.</span><span class="sxs-lookup"><span data-stu-id="b641a-135">By default, the parallel scriptblocks use the current working directory of the caller that started the parallel tasks.</span></span>

  <span data-ttu-id="b641a-136">Niet-afsluit fouten worden naar de cmdlet-fout stroom geschreven, zoals deze optreden in parallelle uitvoering van scriptblocks.</span><span class="sxs-lookup"><span data-stu-id="b641a-136">Non-terminating errors are written to the cmdlet error stream as they occur in parallel running scriptblocks.</span></span> <span data-ttu-id="b641a-137">Omdat de volg orde van de parallelle script Block niet kan worden bepaald, is de volg orde waarin fouten worden weer gegeven in de fout stroom wille keurig.</span><span class="sxs-lookup"><span data-stu-id="b641a-137">Because parallel scriptblock execution order cannot be determined, the order in which errors appear in the error stream is random.</span></span> <span data-ttu-id="b641a-138">Op dezelfde manier worden berichten die zijn geschreven naar andere gegevens stromen, zoals waarschuwing, uitgebreide gegevens of informatie, naar deze gegevens stromen geschreven in een onbepaalde volg orde.</span><span class="sxs-lookup"><span data-stu-id="b641a-138">Likewise, messages written to other data streams, like warning, verbose, or information are written to those data streams in an indeterminate order.</span></span>

  <span data-ttu-id="b641a-139">Als u fouten afsluit, zoals uitzonde ringen, beëindigt u de afzonderlijke parallelle instantie van de scriptblocks waarin deze zich voordoen.</span><span class="sxs-lookup"><span data-stu-id="b641a-139">Terminating errors, such as exceptions, terminate the individual parallel instance of the scriptblocks in which they occur.</span></span> <span data-ttu-id="b641a-140">Een afsluit fout in één scriptblocks veroorzaakt mogelijk geen beëindiging van de `Foreach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b641a-140">A terminating error in one scriptblocks may not cause the termination of the `Foreach-Object` cmdlet.</span></span> <span data-ttu-id="b641a-141">De andere scriptblocks, die parallel worden uitgevoerd, blijven worden uitgevoerd, tenzij er ook een afsluit fout optreedt.</span><span class="sxs-lookup"><span data-stu-id="b641a-141">The other scriptblocks, running in parallel, continue to run unless they also encounter a terminating error.</span></span> <span data-ttu-id="b641a-142">De afsluit fout wordt naar de gegevens stroom van de fout geschreven als een **ErrorRecord** met een **FullyQualifiedErrorId** van `PSTaskException` .</span><span class="sxs-lookup"><span data-stu-id="b641a-142">The terminating error is written to the error data stream as an **ErrorRecord** with a **FullyQualifiedErrorId** of `PSTaskException`.</span></span>
  <span data-ttu-id="b641a-143">Het beëindigen van fouten kan worden geconverteerd naar niet-afsluit fouten met behulp van Power shell-try/catch-of trap-blokken.</span><span class="sxs-lookup"><span data-stu-id="b641a-143">Terminating errors can be converted to non-terminating errors using PowerShell try/catch or trap blocks.</span></span>

## <span data-ttu-id="b641a-144">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="b641a-144">Examples</span></span>

### <span data-ttu-id="b641a-145">Voor beeld 1: gehele getallen in een matrix delen</span><span class="sxs-lookup"><span data-stu-id="b641a-145">Example 1: Divide integers in an array</span></span>

<span data-ttu-id="b641a-146">In dit voor beeld wordt een matrix van drie gehele getallen gebruikt en worden elke reeks gedeeld door 1024.</span><span class="sxs-lookup"><span data-stu-id="b641a-146">This example takes an array of three integers and divides each one of them by 1024.</span></span>

```powershell
30000, 56798, 12432 | ForEach-Object -Process {$_/1024}
```

```Output
29.296875
55.466796875
12.140625
```

### <span data-ttu-id="b641a-147">Voor beeld 2: de lengte van alle bestanden in een map ophalen</span><span class="sxs-lookup"><span data-stu-id="b641a-147">Example 2: Get the length of all the files in a directory</span></span>

<span data-ttu-id="b641a-148">In dit voor beeld worden de bestanden en mappen in de installatie directory van Power shell verwerkt `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="b641a-148">This example processes the files and directories in the PowerShell installation directory `$PSHOME`.</span></span>

```powershell
Get-ChildItem $PSHOME |
  ForEach-Object -Process {if (!$_.PSIsContainer) {$_.Name; $_.Length / 1024; " " }}
```

<span data-ttu-id="b641a-149">Als het object geen map is, wordt de naam van het bestand door het script blok opgehaald, wordt de waarde van de eigenschap **Length** gedeeld door 1024 en wordt een spatie ("") toegevoegd om het te scheiden van de volgende vermelding.</span><span class="sxs-lookup"><span data-stu-id="b641a-149">If the object is not a directory, the script block gets the name of the file, divides the value of its **Length** property by 1024, and adds a space (" ") to separate it from the next entry.</span></span> <span data-ttu-id="b641a-150">De cmdlet gebruikt de eigenschap **PSISContainer** om te bepalen of een object een directory is.</span><span class="sxs-lookup"><span data-stu-id="b641a-150">The cmdlet uses the **PSISContainer** property to determine whether an object is a directory.</span></span>

### <span data-ttu-id="b641a-151">Voor beeld 3: uitvoeren op de meest recente systeem gebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="b641a-151">Example 3: Operate on the most recent System events</span></span>

<span data-ttu-id="b641a-152">In dit voor beeld worden de 1000 meest recente gebeurtenissen van het systeem gebeurtenis logboek naar een tekst bestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="b641a-152">This example writes the 1000 most recent events from the System event log to a text file.</span></span> <span data-ttu-id="b641a-153">De huidige tijd wordt weer gegeven vóór en na de verwerking van de gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="b641a-153">The current time is displayed before and after processing the events.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$events | ForEach-Object -Begin {Get-Date} -Process {Out-File -FilePath Events.txt -Append -InputObject $_.Message} -End {Get-Date}
```

<span data-ttu-id="b641a-154">`Get-EventLog` Hiermee worden de 1000 meest recente gebeurtenissen van het systeem gebeurtenis logboek opgehaald en opgeslagen in de `$Events` variabele.</span><span class="sxs-lookup"><span data-stu-id="b641a-154">`Get-EventLog` gets the 1000 most recent events from the System event log and stores them in the `$Events` variable.</span></span> <span data-ttu-id="b641a-155">`$Events` wordt vervolgens door gegeven aan de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b641a-155">`$Events` is then piped to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="b641a-156">Met de para meter **begin** worden de huidige datum en tijd weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b641a-156">The **Begin** parameter displays the current date and time.</span></span> <span data-ttu-id="b641a-157">Vervolgens gebruikt de para meter **process** de `Out-File` cmdlet om een tekst bestand te maken met de naam events.txt en wordt de bericht eigenschap van elk van de gebeurtenissen in dat bestand opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b641a-157">Next, the **Process** parameter uses the `Out-File` cmdlet to create a text file that is named events.txt and stores the message property of each of the events in that file.</span></span> <span data-ttu-id="b641a-158">De laatste para meter **End** wordt gebruikt om de datum en tijd weer te geven nadat alle verwerking is voltooid.</span><span class="sxs-lookup"><span data-stu-id="b641a-158">Last, the **End** parameter is used to display the date and time after all of the processing has completed.</span></span>

### <span data-ttu-id="b641a-159">Voor beeld 4: de waarde van een register sleutel wijzigen</span><span class="sxs-lookup"><span data-stu-id="b641a-159">Example 4: Change the value of a Registry key</span></span>

<span data-ttu-id="b641a-160">In dit voor beeld wordt de waarde van de register vermelding **remotepath** in alle subsleutels onder de sleutel gewijzigd in `HKCU:\Network` hoofd letters.</span><span class="sxs-lookup"><span data-stu-id="b641a-160">This example changes the value of the **RemotePath** registry entry in all of the subkeys under the `HKCU:\Network` key to uppercase text.</span></span>

```powershell
Get-ItemProperty -Path HKCU:\Network\* |
  ForEach-Object {Set-ItemProperty -Path $_.PSPath -Name RemotePath -Value $_.RemotePath.ToUpper();}
```

<span data-ttu-id="b641a-161">U kunt deze indeling gebruiken om het formulier of de inhoud van een register vermelding te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b641a-161">You can use this format to change the form or content of a registry entry value.</span></span>

<span data-ttu-id="b641a-162">Elke subsleutel in de **netwerk** sleutel vertegenwoordigt een toegewezen netwerk station waarmee opnieuw verbinding wordt gemaakt bij het aanmelden.</span><span class="sxs-lookup"><span data-stu-id="b641a-162">Each subkey in the **Network** key represents a mapped network drive that reconnects at sign on.</span></span> <span data-ttu-id="b641a-163">De vermelding **remotepath** bevat het UNC-pad van het verbonden station.</span><span class="sxs-lookup"><span data-stu-id="b641a-163">The **RemotePath** entry contains the UNC path of the connected drive.</span></span> <span data-ttu-id="b641a-164">Als u bijvoorbeeld het station E: toewijst aan `\\Server\Share` , wordt er een **e** -subsleutel gemaakt in `HKCU:\Network` met de register waarde **remotepath** ingesteld op `\\Server\Share` .</span><span class="sxs-lookup"><span data-stu-id="b641a-164">For example, if you map the E: drive to `\\Server\Share`, an **E** subkey is created in `HKCU:\Network` with the **RemotePath** registry value set to `\\Server\Share`.</span></span>

<span data-ttu-id="b641a-165">De opdracht gebruikt de `Get-ItemProperty` cmdlet om alle subsleutels van de **netwerk** sleutel en de `Set-ItemProperty` cmdlet te verkrijgen om de waarde van de register **vermelding remotepath** in elke sleutel te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b641a-165">The command uses the `Get-ItemProperty` cmdlet to get all of the subkeys of the **Network** key and the `Set-ItemProperty` cmdlet to change the value of the **RemotePath** registry entry in each key.</span></span>
<span data-ttu-id="b641a-166">In de `Set-ItemProperty` opdracht is het pad de waarde van de eigenschap **PSPath** van de register sleutel.</span><span class="sxs-lookup"><span data-stu-id="b641a-166">In the `Set-ItemProperty` command, the path is the value of the **PSPath** property of the registry key.</span></span> <span data-ttu-id="b641a-167">Dit is een eigenschap van het Microsoft .NET Framework-object dat de register sleutel vertegenwoordigt, niet een register vermelding.</span><span class="sxs-lookup"><span data-stu-id="b641a-167">This is a property of the Microsoft .NET Framework object that represents the registry key, not a registry entry.</span></span> <span data-ttu-id="b641a-168">De opdracht maakt gebruik van de methode **ToUpper ()** van de **remotepath** -waarde. Dit is een teken reeks (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="b641a-168">The command uses the **ToUpper()** method of the **RemotePath** value, which is a string (REG_SZ).</span></span>

<span data-ttu-id="b641a-169">Omdat `Set-ItemProperty` de eigenschap van elke sleutel wordt gewijzigd, `ForEach-Object` is de cmdlet vereist voor toegang tot de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b641a-169">Because `Set-ItemProperty` is changing the property of each key, the `ForEach-Object` cmdlet is required to access the property.</span></span>

### <span data-ttu-id="b641a-170">Voor beeld 5: de $Null automatische variabele gebruiken</span><span class="sxs-lookup"><span data-stu-id="b641a-170">Example 5: Use the $Null automatic variable</span></span>

<span data-ttu-id="b641a-171">In dit voor beeld ziet u het effect van de `$Null` Automatische variabele voor de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b641a-171">This example shows the effect of piping the `$Null` automatic variable to the `ForEach-Object` cmdlet.</span></span>

```powershell
1, 2, $null, 4 | ForEach-Object {"Hello"}
```

```Output
Hello
Hello
Hello
Hello
```

<span data-ttu-id="b641a-172">Omdat in Power shell NULL wordt behandeld als een expliciete tijdelijke aanduiding, `ForEach-Object` genereert de cmdlet een waarde voor `$Null` , net zoals voor andere objecten die u naar de pipet.</span><span class="sxs-lookup"><span data-stu-id="b641a-172">Because PowerShell treats null as an explicit placeholder, the `ForEach-Object` cmdlet generates a value for `$Null`, just as it does for other objects that you pipe to it.</span></span>

### <span data-ttu-id="b641a-173">Voor beeld 6: eigenschaps waarden ophalen</span><span class="sxs-lookup"><span data-stu-id="b641a-173">Example 6: Get property values</span></span>

<span data-ttu-id="b641a-174">In dit voor beeld wordt de waarde van de eigenschap **Path** van alle geïnstalleerde Power shell-modules opgehaald met behulp van de para meter **membernaam** van de `ForEach-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b641a-174">This example gets the value of the **Path** property of all installed PowerShell modules by using the **MemberName** parameter of the `ForEach-Object` cmdlet.</span></span>

```powershell
Get-Module -ListAvailable | ForEach-Object -MemberName Path
Get-Module -ListAvailable | Foreach Path
```

<span data-ttu-id="b641a-175">De tweede opdracht is gelijk aan de eerste.</span><span class="sxs-lookup"><span data-stu-id="b641a-175">The second command is equivalent to the first.</span></span> <span data-ttu-id="b641a-176">Het gebruikt de `Foreach` alias van de `ForEach-Object` cmdlet en laat de naam van de para meter **lidnaam** , die optioneel is.</span><span class="sxs-lookup"><span data-stu-id="b641a-176">It uses the `Foreach` alias of the `ForEach-Object` cmdlet and omits the name of the **MemberName** parameter, which is optional.</span></span>

<span data-ttu-id="b641a-177">De `ForEach-Object` cmdlet is handig voor het ophalen van eigenschaps waarden, omdat deze de waarde ophaalt zonder het type te wijzigen, in tegens telling tot de **notatie** -cmdlets of de `Select-Object` cmdlet, waarmee het type eigenschaps waarde wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b641a-177">The `ForEach-Object` cmdlet is useful for getting property values, because it gets the value without changing the type, unlike the **Format** cmdlets or the `Select-Object` cmdlet, which change the property value type.</span></span>

### <span data-ttu-id="b641a-178">Voor beeld 7: module namen splitsen in onderdeel namen</span><span class="sxs-lookup"><span data-stu-id="b641a-178">Example 7: Split module names into component names</span></span>

<span data-ttu-id="b641a-179">In dit voor beeld ziet u drie manieren om twee punt-gescheiden module namen te splitsen in hun onderdeel namen.</span><span class="sxs-lookup"><span data-stu-id="b641a-179">This example shows three ways to split two dot-separated module names into their component names.</span></span>

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

<span data-ttu-id="b641a-180">Met de opdrachten wordt de **Splits** methode van teken reeksen aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b641a-180">The commands call the **Split** method of strings.</span></span> <span data-ttu-id="b641a-181">De drie opdrachten gebruiken een andere syntaxis, maar ze zijn gelijkwaardig en kunnen worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b641a-181">The three commands use different syntax, but they are equivalent and interchangeable.</span></span>

<span data-ttu-id="b641a-182">De eerste opdracht maakt gebruik van de traditionele syntaxis, die een script blok en de huidige object operator bevat `$_` .</span><span class="sxs-lookup"><span data-stu-id="b641a-182">The first command uses the traditional syntax, which includes a script block and the current object operator `$_`.</span></span> <span data-ttu-id="b641a-183">De punt notatie wordt gebruikt om de methode en haakjes op te geven voor het argument scheidings teken.</span><span class="sxs-lookup"><span data-stu-id="b641a-183">It uses the dot syntax to specify the method and parentheses to enclose the delimiter argument.</span></span>

<span data-ttu-id="b641a-184">De tweede opdracht gebruikt de para meter **lidnaam** om de **Split** -methode en de para meter **argumentnaam** op te geven om de punt (".") als scheidings teken te identificeren.</span><span class="sxs-lookup"><span data-stu-id="b641a-184">The second command uses the **MemberName** parameter to specify the **Split** method and the **ArgumentName** parameter to identify the dot (".") as the split delimiter.</span></span>

<span data-ttu-id="b641a-185">De derde opdracht maakt gebruik van de **foreach** -alias van de `ForEach-Object` cmdlet en laat de namen van de para meters **lidnaam** en **argument List** , die optioneel zijn.</span><span class="sxs-lookup"><span data-stu-id="b641a-185">The third command uses the **Foreach** alias of the `ForEach-Object` cmdlet and omits the names of the **MemberName** and **ArgumentList** parameters, which are optional.</span></span>

### <span data-ttu-id="b641a-186">Voor beeld 8: ForEach-Object gebruiken met twee script blokken</span><span class="sxs-lookup"><span data-stu-id="b641a-186">Example 8: Using ForEach-Object with two script blocks</span></span>

<span data-ttu-id="b641a-187">In dit voor beeld worden twee script blokken positioneel door gegeven.</span><span class="sxs-lookup"><span data-stu-id="b641a-187">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="b641a-188">Alle script blokken binden aan de **proces** parameter.</span><span class="sxs-lookup"><span data-stu-id="b641a-188">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="b641a-189">Ze worden echter behandeld alsof ze zijn door gegeven aan de **begin** -en **proces** parameters.</span><span class="sxs-lookup"><span data-stu-id="b641a-189">However, they are treated as if they had been passed to the **Begin** and **Process** parameters.</span></span>

```powershell
1..2 | ForEach-Object { 'begin' } { 'process' }
```

```Output
begin
process
process
```

### <span data-ttu-id="b641a-190">Voor beeld 9: ForEach-Object gebruiken met meer dan twee script blokken</span><span class="sxs-lookup"><span data-stu-id="b641a-190">Example 9: Using ForEach-Object with more than two script blocks</span></span>

<span data-ttu-id="b641a-191">In dit voor beeld worden twee script blokken positioneel door gegeven.</span><span class="sxs-lookup"><span data-stu-id="b641a-191">In this example, we pass two script blocks positionally.</span></span> <span data-ttu-id="b641a-192">Alle script blokken binden aan de **proces** parameter.</span><span class="sxs-lookup"><span data-stu-id="b641a-192">All the script blocks bind to the **Process** parameter.</span></span> <span data-ttu-id="b641a-193">Ze worden echter behandeld alsof ze zijn door gegeven aan de **begin**-, **proces**-en **End** -para meters.</span><span class="sxs-lookup"><span data-stu-id="b641a-193">However, they are treated as if they had been passed to the **Begin**, **Process**, and **End** parameters.</span></span>

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
> <span data-ttu-id="b641a-194">Het eerste script blok wordt altijd toegewezen aan het `begin` blok, het laatste blok wordt toegewezen aan het `end` blok en de blokken tussen zijn allemaal toegewezen aan het blok `process` .</span><span class="sxs-lookup"><span data-stu-id="b641a-194">The first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

### <span data-ttu-id="b641a-195">Voor beeld 10: meerdere script blokken uitvoeren voor elk pijplijn item</span><span class="sxs-lookup"><span data-stu-id="b641a-195">Example 10: Run multiple script blocks for each pipeline item</span></span>

<span data-ttu-id="b641a-196">Zoals weer gegeven in het vorige voor beeld, worden er meerdere script blokken door gegeven met behulp van de **proces** parameter Get toegewezen aan de **begin** -en **End** -para meters.</span><span class="sxs-lookup"><span data-stu-id="b641a-196">As shown in the previous example, multiple script blocks passed using the **Process** parameter get mapped to the **Begin** and **End** parameters.</span></span> <span data-ttu-id="b641a-197">Om deze toewijzing te vermijden, moet u expliciete waarden opgeven voor de **begin** -en **eind** parameters.</span><span class="sxs-lookup"><span data-stu-id="b641a-197">To avoid this mapping, you must provide explicit values for the **Begin** and **End** parameters.</span></span>

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

### <span data-ttu-id="b641a-198">Voor beeld 11: een langzaam script uitvoeren in parallelle batches</span><span class="sxs-lookup"><span data-stu-id="b641a-198">Example 11: Run slow script in parallel batches</span></span>

<span data-ttu-id="b641a-199">In dit voor beeld wordt een eenvoudig script blok uitgevoerd waarmee een teken reeks en slaap stand gedurende één seconde worden geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-199">This example runs a simple script block that evaluates a string and sleeps for one second.</span></span>

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

<span data-ttu-id="b641a-200">De waarde van de para meter **ThrottleLimit** is ingesteld op 4 zodat de invoer wordt verwerkt in batches van vier.</span><span class="sxs-lookup"><span data-stu-id="b641a-200">The **ThrottleLimit** parameter value is set to 4 so that the input is processed in batches of four.</span></span>
<span data-ttu-id="b641a-201">Het `$using:` sleutel woord wordt gebruikt om de variabele door te geven aan `$Message` elk parallel-script blok.</span><span class="sxs-lookup"><span data-stu-id="b641a-201">The `$using:` keyword is used to pass the `$Message` variable into each parallel script block.</span></span>

### <span data-ttu-id="b641a-202">Voor beeld 12: logboek vermeldingen parallel ophalen</span><span class="sxs-lookup"><span data-stu-id="b641a-202">Example 12: Retrieve log entries in parallel</span></span>

<span data-ttu-id="b641a-203">In dit voor beeld worden 50.000 logboek vermeldingen van 5 systeem logboeken op een lokale Windows-computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b641a-203">This example retrieves 50,000 log entries from 5 system logs on a local Windows machine.</span></span>

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

<span data-ttu-id="b641a-204">Met de **parallelle** para meter wordt het script blok opgegeven dat parallel wordt uitgevoerd voor elke invoer logboek naam.</span><span class="sxs-lookup"><span data-stu-id="b641a-204">The **Parallel** parameter specifies the script block that is run in parallel for each input log name.</span></span> <span data-ttu-id="b641a-205">De para meter **ThrottleLimit** zorgt ervoor dat alle vijf de script blokken tegelijk worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-205">The **ThrottleLimit** parameter ensures that all five script blocks run at the same time.</span></span>

### <span data-ttu-id="b641a-206">Voor beeld 13: parallel uitvoeren als een taak</span><span class="sxs-lookup"><span data-stu-id="b641a-206">Example 13: Run in parallel as a job</span></span>

<span data-ttu-id="b641a-207">In dit voor beeld wordt een eenvoudig script blok parallel uitgevoerd, waarbij twee achtergrond taken tegelijk worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b641a-207">This example runs a simple script block in parallel, creating two background jobs at a time.</span></span>

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

<span data-ttu-id="b641a-208">de `$job` variabele ontvangt het taak object waarmee uitvoer gegevens worden verzameld en de status van monitors wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-208">the `$job` variable receives the job object that collects output data and monitors running state.</span></span>
<span data-ttu-id="b641a-209">Het taak object wordt gepiped `Receive-Job` met de para meter **wait** switch.</span><span class="sxs-lookup"><span data-stu-id="b641a-209">The job object is piped to `Receive-Job` with the **Wait** switch parameter.</span></span> <span data-ttu-id="b641a-210">En deze streams worden uitgevoerd naar de-console, net zoals bij het `ForEach-Object -Parallel` uitvoeren zonder **AsJob**.</span><span class="sxs-lookup"><span data-stu-id="b641a-210">And this streams output to the console, just as if `ForEach-Object -Parallel` was run without **AsJob**.</span></span>

### <span data-ttu-id="b641a-211">Voor beeld 14: met behulp van thread safe-verwijzingen naar variabelen</span><span class="sxs-lookup"><span data-stu-id="b641a-211">Example 14: Using thread safe variable references</span></span>

<span data-ttu-id="b641a-212">In dit voor beeld worden script blokken parallel aangeroepen om unieke benoemde proces objecten te verzamelen.</span><span class="sxs-lookup"><span data-stu-id="b641a-212">This example invokes script blocks in parallel to collect uniquely named Process objects.</span></span>

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

<span data-ttu-id="b641a-213">Er wordt één exemplaar van een **ConcurrentDictionary** -object door gegeven aan elk script blok om de objecten te verzamelen.</span><span class="sxs-lookup"><span data-stu-id="b641a-213">A single instance of a **ConcurrentDictionary** object is passed to each script block to collect the objects.</span></span> <span data-ttu-id="b641a-214">Omdat de **ConcurrentDictionary** thread-safe is, is het veilig om door elk parallel schrift te worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b641a-214">Since the **ConcurrentDictionary** is thread safe, it is safe to be modified by each parallel script.</span></span> <span data-ttu-id="b641a-215">Een niet-thread-veilig object, zoals **System. Collections. generic. Dictionary**, is hier niet veilig te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b641a-215">A non-thread-safe object, such as **System.Collections.Generic.Dictionary**, would not be safe to use here.</span></span>

> [!NOTE]
> <span data-ttu-id="b641a-216">Dit voor beeld is een zeer inefficiënt gebruik van een **parallelle** para meter.</span><span class="sxs-lookup"><span data-stu-id="b641a-216">This example is a very inefficient use of **Parallel** parameter.</span></span> <span data-ttu-id="b641a-217">Het script voegt eenvoudigweg het invoer object toe aan een object met een gelijktijdig woorden lijst.</span><span class="sxs-lookup"><span data-stu-id="b641a-217">The script simply adds the input object to a concurrent dictionary object.</span></span> <span data-ttu-id="b641a-218">Het is lastig en niet de overhead van het aanroepen van elk script in een afzonderlijke thread.</span><span class="sxs-lookup"><span data-stu-id="b641a-218">It is trivial and not worth the overhead of invoking each script in a separate thread.</span></span> <span data-ttu-id="b641a-219">`ForEach-Object`Normaal gesp roken werkt **zonder parallelle** switch veel efficiënter en sneller.</span><span class="sxs-lookup"><span data-stu-id="b641a-219">Running `ForEach-Object` normally without the **Parallel** switch is much more efficient and faster.</span></span> <span data-ttu-id="b641a-220">Dit voor beeld is alleen bedoeld om te laten zien hoe u thread-safe variabelen kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b641a-220">This example is only intended to demonstrate how to use thread safe variables.</span></span>

### <span data-ttu-id="b641a-221">Voor beeld 15: fouten schrijven met parallelle uitvoering</span><span class="sxs-lookup"><span data-stu-id="b641a-221">Example 15: Writing errors with parallel execution</span></span>

<span data-ttu-id="b641a-222">In dit voor beeld wordt de fout stroom parallel geschreven, waarbij de volg orde van de geschreven fouten wille keurig is.</span><span class="sxs-lookup"><span data-stu-id="b641a-222">This example writes to the error stream in parallel, where the order of written errors is random.</span></span>

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

### <span data-ttu-id="b641a-223">Voor beeld 16: fouten bij parallelle uitvoering beëindigen</span><span class="sxs-lookup"><span data-stu-id="b641a-223">Example 16: Terminating errors in parallel execution</span></span>

<span data-ttu-id="b641a-224">In dit voor beeld wordt een afsluit fout in één parallel uitgevoerde script Block gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-224">This example demonstrates a terminating error in one parallel running scriptblock.</span></span>

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

<span data-ttu-id="b641a-225">`Output: 3` is nooit geschreven, omdat de parallelle script Block voor die herhaling is beëindigd.</span><span class="sxs-lookup"><span data-stu-id="b641a-225">`Output: 3` is never written because the parallel scriptblock for that iteration was terminated.</span></span>

## <span data-ttu-id="b641a-226">Parameters</span><span class="sxs-lookup"><span data-stu-id="b641a-226">Parameters</span></span>

### <span data-ttu-id="b641a-227">-Argument List</span><span class="sxs-lookup"><span data-stu-id="b641a-227">-ArgumentList</span></span>

<span data-ttu-id="b641a-228">Hiermee geeft u een matrix op met argumenten voor een methode aanroep.</span><span class="sxs-lookup"><span data-stu-id="b641a-228">Specifies an array of arguments to a method call.</span></span> <span data-ttu-id="b641a-229">Zie [about_Splatting](about/about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="b641a-229">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="b641a-230">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b641a-230">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="b641a-231">-Begin</span><span class="sxs-lookup"><span data-stu-id="b641a-231">-Begin</span></span>

<span data-ttu-id="b641a-232">Hiermee geeft u een script blok op dat wordt uitgevoerd voordat deze cmdlet invoer objecten verwerkt.</span><span class="sxs-lookup"><span data-stu-id="b641a-232">Specifies a script block that runs before this cmdlet processes any input objects.</span></span> <span data-ttu-id="b641a-233">Dit script blok wordt slechts één keer uitgevoerd voor de volledige pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b641a-233">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="b641a-234">Zie about_Functions voor meer informatie over het `begin` blok [](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="b641a-234">For more information about the `begin` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

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

### <span data-ttu-id="b641a-235">-End</span><span class="sxs-lookup"><span data-stu-id="b641a-235">-End</span></span>

<span data-ttu-id="b641a-236">Hiermee geeft u een script blok op dat wordt uitgevoerd nadat deze cmdlet alle invoer objecten heeft verwerkt.</span><span class="sxs-lookup"><span data-stu-id="b641a-236">Specifies a script block that runs after this cmdlet processes all input objects.</span></span> <span data-ttu-id="b641a-237">Dit script blok wordt slechts één keer uitgevoerd voor de volledige pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b641a-237">This script block is only run once for the entire pipeline.</span></span> <span data-ttu-id="b641a-238">Zie about_Functions voor meer informatie over het `end` blok [](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="b641a-238">For more information about the `end` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

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

### <span data-ttu-id="b641a-239">-Input object</span><span class="sxs-lookup"><span data-stu-id="b641a-239">-InputObject</span></span>

<span data-ttu-id="b641a-240">Hiermee worden de invoer objecten opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b641a-240">Specifies the input objects.</span></span> <span data-ttu-id="b641a-241">`ForEach-Object` Hiermee wordt het script blok of de bewerkings instructie voor elk invoer object uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-241">`ForEach-Object` runs the script block or operation statement on each input object.</span></span> <span data-ttu-id="b641a-242">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b641a-242">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="b641a-243">Wanneer u de para meter **input object** gebruikt in `ForEach-Object` plaats van de resultaten van de pijpleiding opdracht, `ForEach-Object` wordt de waarde van **input object** behandeld als een enkel object.</span><span class="sxs-lookup"><span data-stu-id="b641a-243">When you use the **InputObject** parameter with `ForEach-Object`, instead of piping command results to `ForEach-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="b641a-244">Dit geldt ook als de waarde een verzameling is die het resultaat is van een opdracht, zoals `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="b641a-244">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span>
<span data-ttu-id="b641a-245">Omdat **input object** geen individuele eigenschappen van een matrix of verzameling van objecten kan retour neren, raden we u aan dat als u gebruikt `ForEach-Object` om bewerkingen uit te voeren op een verzameling objecten voor objecten met specifieke waarden in gedefinieerde eigenschappen, u `ForEach-Object` in de pijp lijn gebruikt, zoals wordt weer gegeven in de voor beelden in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="b641a-245">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that if you use `ForEach-Object` to perform operations on a collection of objects for those objects that have specific values in defined properties, you use `ForEach-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="b641a-246">-Lidnaam</span><span class="sxs-lookup"><span data-stu-id="b641a-246">-MemberName</span></span>

<span data-ttu-id="b641a-247">Hiermee geeft u de eigenschap op die moet worden opgehaald of de methode die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b641a-247">Specifies the property to get or the method to call.</span></span>

<span data-ttu-id="b641a-248">Joker tekens zijn toegestaan, maar werken alleen als de resulterende teken reeks wordt omgezet in een unieke waarde.</span><span class="sxs-lookup"><span data-stu-id="b641a-248">Wildcard characters are permitted, but work only if the resulting string resolves to a unique value.</span></span>
<span data-ttu-id="b641a-249">Als u bijvoorbeeld uitvoert `Get-Process | ForEach -MemberName *Name` , komt het Joker teken patroon overeen met meer dan één lid waardoor de opdracht mislukt.</span><span class="sxs-lookup"><span data-stu-id="b641a-249">For example, if you run `Get-Process | ForEach -MemberName *Name`, the wildcard pattern matches more than one member causing the command to fail.</span></span>

<span data-ttu-id="b641a-250">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b641a-250">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="b641a-251">-Proces</span><span class="sxs-lookup"><span data-stu-id="b641a-251">-Process</span></span>

<span data-ttu-id="b641a-252">Hiermee geeft u de bewerking op die op elk invoer object wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-252">Specifies the operation that is performed on each input object.</span></span> <span data-ttu-id="b641a-253">Dit script blok wordt uitgevoerd voor elk object in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="b641a-253">This script block is run for every object in the pipeline.</span></span> <span data-ttu-id="b641a-254">Zie about_Functions voor meer informatie over het `process` blok [](about/about_functions.md#piping-objects-to-functions).</span><span class="sxs-lookup"><span data-stu-id="b641a-254">For more information about the `process` block, see [about_Functions](about/about_functions.md#piping-objects-to-functions).</span></span>

<span data-ttu-id="b641a-255">Wanneer u meerdere script blokken voor de para meter **process** opgeeft, wordt het eerste script blok altijd toegewezen aan het `begin` blok.</span><span class="sxs-lookup"><span data-stu-id="b641a-255">When you provide multiple script blocks to the **Process** parameter, the first script block is always mapped to the `begin` block.</span></span> <span data-ttu-id="b641a-256">Als er slechts twee script blokken zijn, wordt het tweede blok toegewezen aan het `process` blok.</span><span class="sxs-lookup"><span data-stu-id="b641a-256">If there are only two script blocks, the second block is mapped to the `process` block.</span></span> <span data-ttu-id="b641a-257">Als er drie of meer script blokken zijn, wordt het eerste script blok altijd toegewezen aan het `begin` blok, wordt het laatste blok toegewezen aan het `end` blok en worden de blokken tussen beide toegewezen aan het `process` blok.</span><span class="sxs-lookup"><span data-stu-id="b641a-257">If there are three or more script blocks, first script block is always mapped to the `begin` block, the last block is mapped to the `end` block, and the blocks in between are all mapped to the `process` block.</span></span>

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

### <span data-ttu-id="b641a-258">-RemainingScripts</span><span class="sxs-lookup"><span data-stu-id="b641a-258">-RemainingScripts</span></span>

<span data-ttu-id="b641a-259">Hiermee geeft u alle script blokken op die niet worden gebruikt door de **proces** parameter.</span><span class="sxs-lookup"><span data-stu-id="b641a-259">Specifies all script blocks that are not taken by the **Process** parameter.</span></span>

<span data-ttu-id="b641a-260">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="b641a-260">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="b641a-261">-Parallel</span><span class="sxs-lookup"><span data-stu-id="b641a-261">-Parallel</span></span>

<span data-ttu-id="b641a-262">Hiermee geeft u het script blok op dat moet worden gebruikt voor parallelle verwerking van invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="b641a-262">Specifies the script block to be used for parallel processing of input objects.</span></span> <span data-ttu-id="b641a-263">Voer een script blok in dat de bewerking beschrijft.</span><span class="sxs-lookup"><span data-stu-id="b641a-263">Enter a script block that describes the operation.</span></span>

<span data-ttu-id="b641a-264">Deze para meter is geïntroduceerd in Power shell 7,0.</span><span class="sxs-lookup"><span data-stu-id="b641a-264">This parameter was introduced in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="b641a-265">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b641a-265">-ThrottleLimit</span></span>

<span data-ttu-id="b641a-266">Hiermee geeft u het aantal script blokken op dat parallel is.</span><span class="sxs-lookup"><span data-stu-id="b641a-266">Specifies the number of script blocks that in parallel.</span></span> <span data-ttu-id="b641a-267">Invoer objecten worden geblokkeerd totdat het aantal actieve script blokken onder het **ThrottleLimit** valt.</span><span class="sxs-lookup"><span data-stu-id="b641a-267">Input objects are blocked until the running script block count falls below the **ThrottleLimit**.</span></span> <span data-ttu-id="b641a-268">De standaardwaarde is `5`.</span><span class="sxs-lookup"><span data-stu-id="b641a-268">The default value is `5`.</span></span>

<span data-ttu-id="b641a-269">Deze para meter is geïntroduceerd in Power shell 7,0.</span><span class="sxs-lookup"><span data-stu-id="b641a-269">This parameter was introduced in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="b641a-270">-TimeoutSeconds</span><span class="sxs-lookup"><span data-stu-id="b641a-270">-TimeoutSeconds</span></span>

<span data-ttu-id="b641a-271">Hiermee geeft u het aantal seconden op dat moet worden gewacht totdat alle invoer parallel wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="b641a-271">Specifies the number of seconds to wait for all input to be processed in parallel.</span></span> <span data-ttu-id="b641a-272">Na de opgegeven time-outperiode worden alle actieve scripts gestopt.</span><span class="sxs-lookup"><span data-stu-id="b641a-272">After the specified timeout time, all running scripts are stopped.</span></span> <span data-ttu-id="b641a-273">En alle resterende invoer objecten die moeten worden verwerkt, worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-273">And any remaining input objects to be processed are ignored.</span></span> <span data-ttu-id="b641a-274">De standaard waarde van `0` de time-out uitschakelen en `ForEach-Object -Parallel` kan oneindig worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-274">Default value of `0` disables the timeout, and `ForEach-Object -Parallel` can run indefinitely.</span></span> <span data-ttu-id="b641a-275">Als u <kbd>CTRL</kbd> + <kbd>C</kbd> op de opdracht regel typt, wordt een uitvoering van de `ForEach-Object -Parallel` opdracht gestopt.</span><span class="sxs-lookup"><span data-stu-id="b641a-275">Typing <kbd>Ctrl</kbd>+<kbd>C</kbd> at the command line stops a running `ForEach-Object -Parallel` command.</span></span> <span data-ttu-id="b641a-276">Deze para meter kan niet worden gebruikt in combi natie met de para meter **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="b641a-276">This parameter cannot be used along with the **AsJob** parameter.</span></span>

<span data-ttu-id="b641a-277">Deze para meter is geïntroduceerd in Power shell 7,0.</span><span class="sxs-lookup"><span data-stu-id="b641a-277">This parameter was introduced in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="b641a-278">-AsJob</span><span class="sxs-lookup"><span data-stu-id="b641a-278">-AsJob</span></span>

<span data-ttu-id="b641a-279">Zorgt ervoor dat de parallelle aanroep als een Power shell-taak wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-279">Causes the parallel invocation to run as a PowerShell job.</span></span> <span data-ttu-id="b641a-280">Er wordt één taak object geretourneerd in plaats van uitvoer van de actieve script blokken.</span><span class="sxs-lookup"><span data-stu-id="b641a-280">A single job object is returned instead of output from the running script blocks.</span></span> <span data-ttu-id="b641a-281">Het taak object bevat onderliggende taken voor elk parallel-script blok dat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-281">The job object contains child jobs for each parallel script block that runs.</span></span> <span data-ttu-id="b641a-282">Het taak object kan worden gebruikt door alle Power shell-taak-cmdlets, om de uitvoerings status te controleren en gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="b641a-282">The job object can be used by all PowerShell job cmdlets, to monitor running state and retrieve data.</span></span>

<span data-ttu-id="b641a-283">Deze para meter is geïntroduceerd in Power shell 7,0.</span><span class="sxs-lookup"><span data-stu-id="b641a-283">This parameter was introduced in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="b641a-284">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b641a-284">-Confirm</span></span>

<span data-ttu-id="b641a-285">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b641a-285">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b641a-286">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b641a-286">-WhatIf</span></span>

<span data-ttu-id="b641a-287">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b641a-287">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b641a-288">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-288">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b641a-289">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b641a-289">CommonParameters</span></span>

<span data-ttu-id="b641a-290">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b641a-290">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b641a-291">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b641a-291">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b641a-292">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="b641a-292">Inputs</span></span>

### <span data-ttu-id="b641a-293">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b641a-293">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b641a-294">U kunt elk object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b641a-294">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="b641a-295">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="b641a-295">Outputs</span></span>

### <span data-ttu-id="b641a-296">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b641a-296">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b641a-297">Deze cmdlet retourneert objecten die worden bepaald door de invoer.</span><span class="sxs-lookup"><span data-stu-id="b641a-297">This cmdlet returns objects that are determined by the input.</span></span>

## <span data-ttu-id="b641a-298">Notities</span><span class="sxs-lookup"><span data-stu-id="b641a-298">Notes</span></span>

- <span data-ttu-id="b641a-299">De `ForEach-Object` cmdlet werkt op dezelfde manier als de **foreach** -instructie, behalve dat u invoer niet kunt door sluizen naar een **foreach** -instructie.</span><span class="sxs-lookup"><span data-stu-id="b641a-299">The `ForEach-Object` cmdlet works much like the **Foreach** statement, except that you cannot pipe input to a **Foreach** statement.</span></span> <span data-ttu-id="b641a-300">Zie [about_Foreach](./About/about_Foreach.md)voor meer informatie over de instructie **foreach** .</span><span class="sxs-lookup"><span data-stu-id="b641a-300">For more information about the **Foreach** statement, see [about_Foreach](./About/about_Foreach.md).</span></span>

- <span data-ttu-id="b641a-301">Vanaf Power Shell 4,0 `Where` en `ForEach` methoden zijn toegevoegd voor gebruik met verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="b641a-301">Starting in PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span> <span data-ttu-id="b641a-302">U kunt hier meer lezen over deze nieuwe methoden [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="b641a-302">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

- <span data-ttu-id="b641a-303">De `ForEach-Object -Parallel` para meter set gebruikt de interne API van Power shell om elk script blok uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b641a-303">The `ForEach-Object -Parallel` parameter set uses PowerShell's internal API to run each script block.</span></span> <span data-ttu-id="b641a-304">Dit is aanzienlijk meer overhead dan `ForEach-Object` normaal uitvoeren met sequentiële verwerking.</span><span class="sxs-lookup"><span data-stu-id="b641a-304">This is significantly more overhead than running `ForEach-Object` normally with sequential processing.</span></span> <span data-ttu-id="b641a-305">Het is belang rijk om **parallel** te gebruiken waarbij de overhead van parallelle uitvoering klein is in vergelijking met het werk dat door het script blok wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b641a-305">It is important to use **Parallel** where the overhead of running in parallel is small compared to work the script block performs.</span></span> <span data-ttu-id="b641a-306">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b641a-306">For example:</span></span>

  - <span data-ttu-id="b641a-307">Computerintensieve scripts op multicore-computers</span><span class="sxs-lookup"><span data-stu-id="b641a-307">Compute intensive scripts on multi-core machines</span></span>
  - <span data-ttu-id="b641a-308">Scripts die tijd wachten op resultaten of het uitvoeren van bestands bewerkingen</span><span class="sxs-lookup"><span data-stu-id="b641a-308">Scripts that spend time waiting for results or doing file operations</span></span>

  <span data-ttu-id="b641a-309">Het gebruik van de **parallelle** para meter kan ertoe leiden dat scripts veel langzamer worden uitgevoerd dan normaal.</span><span class="sxs-lookup"><span data-stu-id="b641a-309">Using the **Parallel** parameter can cause scripts to run much slower than normal.</span></span> <span data-ttu-id="b641a-310">Met name als de parallelle scripts trivial zijn.</span><span class="sxs-lookup"><span data-stu-id="b641a-310">Especially if the parallel scripts are trivial.</span></span> <span data-ttu-id="b641a-311">Experimenteer met **parallel** om te ontdekken waar het nuttig kan zijn.</span><span class="sxs-lookup"><span data-stu-id="b641a-311">Experiment with **Parallel** to discover where it can be beneficial.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="b641a-312">`ForEach-Object -Parallel`Met de parameterset worden script blokken parallel uitgevoerd in afzonderlijke proces threads.</span><span class="sxs-lookup"><span data-stu-id="b641a-312">The `ForEach-Object -Parallel` parameter set runs script blocks in parallel on separate process threads.</span></span> <span data-ttu-id="b641a-313">Met het `$using:` sleutel woord kunnen variabelen verwijzingen door geven van de aanroep thread van de cmdlet naar elke actieve script blok thread.</span><span class="sxs-lookup"><span data-stu-id="b641a-313">The `$using:` keyword allows passing variable references from the cmdlet invocation thread to each running script block thread.</span></span> <span data-ttu-id="b641a-314">Aangezien de script blokken worden uitgevoerd in verschillende threads, moeten de object variabelen die worden door gegeven door verwijzing, veilig worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b641a-314">Since the script blocks run in different threads, the object variables passed by reference must be used safely.</span></span> <span data-ttu-id="b641a-315">Over het algemeen is het veilig om te lezen van objecten waarnaar wordt verwezen en die niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b641a-315">Generally it is safe to read from referenced objects that don't change.</span></span> <span data-ttu-id="b641a-316">Maar als de object status wordt gewijzigd, moet u de beveiligde objecten van de thread gebruiken, zoals .net **System. verzameling. gelijktijdige** typen (Zie voor beeld 11).</span><span class="sxs-lookup"><span data-stu-id="b641a-316">But if the object state is being modified then you must used thread safe objects, such as .Net **System.Collection.Concurrent** types (See Example 11).</span></span>

## <span data-ttu-id="b641a-317">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="b641a-317">Related links</span></span>

[<span data-ttu-id="b641a-318">Compare-object</span><span class="sxs-lookup"><span data-stu-id="b641a-318">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="b641a-319">Where-object</span><span class="sxs-lookup"><span data-stu-id="b641a-319">Where-Object</span></span>](Where-Object.md)

[<span data-ttu-id="b641a-320">Groep-object</span><span class="sxs-lookup"><span data-stu-id="b641a-320">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="b641a-321">Meting object</span><span class="sxs-lookup"><span data-stu-id="b641a-321">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="b641a-322">New-Object</span><span class="sxs-lookup"><span data-stu-id="b641a-322">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="b641a-323">Select-Object</span><span class="sxs-lookup"><span data-stu-id="b641a-323">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="b641a-324">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="b641a-324">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="b641a-325">T-object</span><span class="sxs-lookup"><span data-stu-id="b641a-325">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
