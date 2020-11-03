---
description: Opdrachten in de Power shell combi neren in pijp lijnen
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: 651ba1f42743d83958d6711cff01fec030fa9a02
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253168"
---
# <a name="about-pipelines"></a><span data-ttu-id="15b0b-104">Over pijp lijnen</span><span class="sxs-lookup"><span data-stu-id="15b0b-104">About Pipelines</span></span>

## <a name="short-description"></a><span data-ttu-id="15b0b-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="15b0b-105">Short description</span></span>

<span data-ttu-id="15b0b-106">Opdrachten in de Power shell combi neren in pijp lijnen</span><span class="sxs-lookup"><span data-stu-id="15b0b-106">Combining commands into pipelines in the PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="15b0b-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="15b0b-107">Long description</span></span>

<span data-ttu-id="15b0b-108">Een pijp lijn is een reeks opdrachten die zijn verbonden door pijplijn operators ( `|` ) (ASCII 124).</span><span class="sxs-lookup"><span data-stu-id="15b0b-108">A pipeline is a series of commands connected by pipeline operators (`|`) (ASCII 124).</span></span> <span data-ttu-id="15b0b-109">Elke pijplijn operator verzendt de resultaten van de voor gaande opdracht naar de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="15b0b-109">Each pipeline operator sends the results of the preceding command to the next command.</span></span>

<span data-ttu-id="15b0b-110">De uitvoer van de eerste opdracht kan worden verzonden voor verwerking als invoer voor de tweede opdracht.</span><span class="sxs-lookup"><span data-stu-id="15b0b-110">The output of the first command can be sent for processing as input to the second command.</span></span> <span data-ttu-id="15b0b-111">En die uitvoer kan naar nog een andere opdracht worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="15b0b-111">And that output can be sent to yet another command.</span></span> <span data-ttu-id="15b0b-112">Het resultaat is een complexe opdracht reeks of- _pijp lijn_ die bestaat uit een reeks eenvoudige opdrachten.</span><span class="sxs-lookup"><span data-stu-id="15b0b-112">The result is a complex command chain or _pipeline_ that is composed of a series of simple commands.</span></span>

<span data-ttu-id="15b0b-113">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15b0b-113">For example,</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="15b0b-114">In dit voor beeld worden de objecten `Command-1` verzonden naar `Command-2` .</span><span class="sxs-lookup"><span data-stu-id="15b0b-114">In this example, the objects that `Command-1` emits are sent to `Command-2`.</span></span>
<span data-ttu-id="15b0b-115">`Command-2` Hiermee worden de objecten verwerkt en verzonden naar `Command-3` .</span><span class="sxs-lookup"><span data-stu-id="15b0b-115">`Command-2` processes the objects and sends them to `Command-3`.</span></span> <span data-ttu-id="15b0b-116">`Command-3` de objecten worden verwerkt en verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="15b0b-116">`Command-3` processes the objects and send them down the pipeline.</span></span> <span data-ttu-id="15b0b-117">Omdat er geen opdrachten meer in de pijp lijn staan, worden de resultaten weer gegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="15b0b-117">Because there are no more commands in the pipeline, the results are displayed at the console.</span></span>

<span data-ttu-id="15b0b-118">In een pijp lijn worden de opdrachten verwerkt in volg orde van links naar rechts.</span><span class="sxs-lookup"><span data-stu-id="15b0b-118">In a pipeline, the commands are processed in order from left to right.</span></span> <span data-ttu-id="15b0b-119">De verwerking wordt verwerkt als één bewerking en de uitvoer wordt weer gegeven wanneer deze wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="15b0b-119">The processing is handled as a single operation and output is displayed as it's generated.</span></span>

<span data-ttu-id="15b0b-120">Hier volgt een eenvoudig voor beeld.</span><span class="sxs-lookup"><span data-stu-id="15b0b-120">Here is a simple example.</span></span> <span data-ttu-id="15b0b-121">Met de volgende opdracht wordt het klad blok proces opgehaald en vervolgens gestopt.</span><span class="sxs-lookup"><span data-stu-id="15b0b-121">The following command gets the Notepad process and then stops it.</span></span>

<span data-ttu-id="15b0b-122">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15b0b-122">For example,</span></span>

```powershell
Get-Process notepad | Stop-Process
```

<span data-ttu-id="15b0b-123">Met de eerste opdracht wordt de `Get-Process` cmdlet gebruikt om een object op te halen dat het klad blok-proces vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="15b0b-123">The first command uses the `Get-Process` cmdlet to get an object representing the Notepad process.</span></span> <span data-ttu-id="15b0b-124">Er wordt een pijplijn operator ( `|` ) gebruikt om het proces object naar de cmdlet te verzenden `Stop-Process` , waardoor het klad blok-proces wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="15b0b-124">It uses a pipeline operator (`|`) to send the process object to the `Stop-Process` cmdlet, which stops the Notepad process.</span></span> <span data-ttu-id="15b0b-125">U ziet dat de `Stop-Process` opdracht geen **naam** of **id-** para meter heeft om het proces op te geven, omdat het opgegeven proces via de pijp lijn wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="15b0b-125">Notice that the `Stop-Process` command doesn't have a **Name** or **ID** parameter to specify the process, because the specified process is submitted through the pipeline.</span></span>

<span data-ttu-id="15b0b-126">In dit voor beeld van de pijp lijn worden de tekst bestanden in de huidige map opgehaald, worden alleen de bestanden geselecteerd die meer dan 10.000 bytes lang zijn, worden gesorteerd op lengte en worden de naam en de lengte van elk bestand in een tabel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="15b0b-126">This pipeline example gets the text files in the current directory, selects only the files that are more than 10,000 bytes long, sorts them by length, and displays the name and length of each file in a table.</span></span>

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

<span data-ttu-id="15b0b-127">Deze pijp lijn bestaat uit vier opdrachten in de opgegeven volg orde.</span><span class="sxs-lookup"><span data-stu-id="15b0b-127">This pipeline consists of four commands in the specified order.</span></span> <span data-ttu-id="15b0b-128">In de volgende afbeelding ziet u de uitvoer van elke opdracht die wordt door gegeven aan de volgende opdracht in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="15b0b-128">The following illustration shows the output from each command as it's passed to the next command in the pipeline.</span></span>

```
Get-ChildItem -Path *.txt
| (FileInfo objects for *.txt)
V
Where-Object {$_.length -gt 10000}
| (FileInfo objects for *.txt)
| (      Length > 10000      )
V
Sort-Object -Property Length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
V
Format-Table -Property name, length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
| (   Formatted in a table   )
V

Name                       Length
----                       ------
tmp1.txt                    82920
tmp2.txt                   114000
tmp3.txt                   114000
```

## <a name="using-pipelines"></a><span data-ttu-id="15b0b-129">Pijp lijnen gebruiken</span><span class="sxs-lookup"><span data-stu-id="15b0b-129">Using pipelines</span></span>

<span data-ttu-id="15b0b-130">De meeste Power shell-cmdlets zijn ontworpen ter ondersteuning van pijp lijnen.</span><span class="sxs-lookup"><span data-stu-id="15b0b-130">Most PowerShell cmdlets are designed to support pipelines.</span></span> <span data-ttu-id="15b0b-131">In de meeste _gevallen kunt u_ de resultaten van een **Get** -cmdlet door geven aan een andere cmdlet van hetzelfde zelfstandig naam woord.</span><span class="sxs-lookup"><span data-stu-id="15b0b-131">In most cases, you can _pipe_ the results of a **Get** cmdlet to another cmdlet of the same noun.</span></span>
<span data-ttu-id="15b0b-132">U kunt bijvoorbeeld de uitvoer van de cmdlet door sluizen `Get-Service` naar de `Start-Service` `Stop-Service` cmdlets of.</span><span class="sxs-lookup"><span data-stu-id="15b0b-132">For example, you can pipe the output of the `Get-Service` cmdlet to the `Start-Service` or `Stop-Service` cmdlets.</span></span>

<span data-ttu-id="15b0b-133">In deze voorbeeld pijplijn wordt de WMI-service op de computer gestart:</span><span class="sxs-lookup"><span data-stu-id="15b0b-133">This example pipeline starts the WMI service on the computer:</span></span>

```powershell
Get-Service wmi | Start-Service
```

<span data-ttu-id="15b0b-134">Een ander voor beeld: u kunt de uitvoer van `Get-Item` of `Get-ChildItem` binnen de Power shell-register provider door geven aan de `New-ItemProperty` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15b0b-134">For another example, you can pipe the output of `Get-Item` or `Get-ChildItem` within the PowerShell registry provider to the `New-ItemProperty` cmdlet.</span></span> <span data-ttu-id="15b0b-135">In dit voor beeld wordt een nieuwe register vermelding, **NoOfEmployees** , met de waarde **8124** , toegevoegd aan de register sleutel **mijn bedrijf** .</span><span class="sxs-lookup"><span data-stu-id="15b0b-135">This example adds a new registry entry, **NoOfEmployees** , with a value of **8124** , to the **MyCompany** registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

<span data-ttu-id="15b0b-136">Veel van de cmdlets van het hulp programma, zoals,,, `Get-Member` `Where-Object` `Sort-Object` `Group-Object` en `Measure-Object` worden bijna uitsluitend in pijp lijnen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="15b0b-136">Many of the utility cmdlets, such as `Get-Member`, `Where-Object`, `Sort-Object`, `Group-Object`, and `Measure-Object` are used almost exclusively in pipelines.</span></span> <span data-ttu-id="15b0b-137">U kunt elk object type door sluizen naar deze cmdlets.</span><span class="sxs-lookup"><span data-stu-id="15b0b-137">You can pipe any object type to these cmdlets.</span></span> <span data-ttu-id="15b0b-138">In dit voor beeld ziet u hoe alle processen op de computer worden gesorteerd op het aantal geopende ingangen in elk proces.</span><span class="sxs-lookup"><span data-stu-id="15b0b-138">This example shows how to sort all the processes on the computer by the number of open handles in each process.</span></span>

```powershell
Get-Process | Sort-Object -Property handles
```

<span data-ttu-id="15b0b-139">U kunt objecten door sluizen naar de indelings-, export-en uitvoer-cmdlets, zoals `Format-List` ,, `Format-Table` `Export-Clixml` , `Export-CSV` en `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="15b0b-139">You can pipe objects to the formatting, export, and output cmdlets, such as `Format-List`, `Format-Table`, `Export-Clixml`, `Export-CSV`, and `Out-File`.</span></span>

<span data-ttu-id="15b0b-140">In dit voor beeld ziet u hoe u de `Format-List` cmdlet gebruikt om een lijst met eigenschappen voor een proces object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="15b0b-140">This example shows how to use the `Format-List` cmdlet to display a list of properties for a process object.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="15b0b-141">Met een beetje van de praktijk zult u zien dat het combi neren van eenvoudige opdrachten in pijp lijnen tijd en typen bespaart en uw scripting efficiënter maakt.</span><span class="sxs-lookup"><span data-stu-id="15b0b-141">With a bit of practice, you'll find that combining simple commands into pipelines saves time and typing, and makes your scripting more efficient.</span></span>

## <a name="how-pipelines-work"></a><span data-ttu-id="15b0b-142">Hoe pijp lijnen werken</span><span class="sxs-lookup"><span data-stu-id="15b0b-142">How pipelines work</span></span>

<span data-ttu-id="15b0b-143">In deze sectie wordt uitgelegd hoe invoer objecten zijn gebonden aan cmdlet-para meters en verwerkt tijdens de uitvoering van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="15b0b-143">This section explains how input objects are bound to cmdlet parameters and processed during pipeline execution.</span></span>

### <a name="accepts-pipeline-input"></a><span data-ttu-id="15b0b-144">Invoer van pijp lijn accepteren</span><span class="sxs-lookup"><span data-stu-id="15b0b-144">Accepts pipeline input</span></span>

<span data-ttu-id="15b0b-145">Voor de ondersteuning van pipelining moet de ontvangende cmdlet een para meter hebben die de invoer van de pijp lijn accepteert.</span><span class="sxs-lookup"><span data-stu-id="15b0b-145">To support pipelining, the receiving cmdlet must have a parameter that accepts pipeline input.</span></span> <span data-ttu-id="15b0b-146">Gebruik de `Get-Help` opdracht met de opties **Full** of **para meter** om te bepalen welke para meters van een cmdlet pijplijn invoer accepteren.</span><span class="sxs-lookup"><span data-stu-id="15b0b-146">Use the `Get-Help` command with the **Full** or **Parameter** options to determine which parameters of a cmdlet accept pipeline input.</span></span>

<span data-ttu-id="15b0b-147">Als u bijvoorbeeld wilt bepalen welke para meters van de `Start-Service` cmdlet pijplijn invoer accepteren, typt u:</span><span class="sxs-lookup"><span data-stu-id="15b0b-147">For example, to determine which of the parameters of the `Start-Service` cmdlet accepts pipeline input, type:</span></span>

```powershell
Get-Help Start-Service -Full
```

<span data-ttu-id="15b0b-148">of</span><span class="sxs-lookup"><span data-stu-id="15b0b-148">or</span></span>

```powershell
Get-Help Start-Service -Parameter *
```

<span data-ttu-id="15b0b-149">In de Help voor de `Start-Service` cmdlet ziet u dat alleen de **input object** -en **name** -para meters pijplijn invoer accepteren.</span><span class="sxs-lookup"><span data-stu-id="15b0b-149">The help for the `Start-Service` cmdlet shows that only the **InputObject** and **Name** parameters accept pipeline input.</span></span>

```Output
-InputObject <ServiceController[]>
Specifies ServiceController objects representing the services to be started.
Enter a variable that contains the objects, or type a command or expression
that gets the objects.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByValue)
Accept wildcard characters?  false

-Name <String[]>
Specifies the service names for the service to be started.

The parameter name is optional. You can use Name or its alias, ServiceName,
or you can omit the parameter name.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByPropertyName, ByValue)
Accept wildcard characters?  false
```

<span data-ttu-id="15b0b-150">Wanneer u objecten via de pijp lijn verzendt naar `Start-Service` , probeert Power shell de objecten te koppelen aan de para meters **input object** en **name** .</span><span class="sxs-lookup"><span data-stu-id="15b0b-150">When you send objects through the pipeline to `Start-Service`, PowerShell attempts to associate the objects with the **InputObject** and **Name** parameters.</span></span>

### <a name="methods-of-accepting-pipeline-input"></a><span data-ttu-id="15b0b-151">Methoden voor het accepteren van pijp lijn invoer</span><span class="sxs-lookup"><span data-stu-id="15b0b-151">Methods of accepting pipeline input</span></span>

<span data-ttu-id="15b0b-152">Cmdlets-para meters kunnen de invoer van de pijp lijn op twee verschillende manieren accepteren:</span><span class="sxs-lookup"><span data-stu-id="15b0b-152">Cmdlets parameters can accept pipeline input in one of two different ways:</span></span>

- <span data-ttu-id="15b0b-153">**ByValue** : de para meter accepteert waarden die overeenkomen met het verwachte .net-type of die kunnen worden geconverteerd naar dat type.</span><span class="sxs-lookup"><span data-stu-id="15b0b-153">**ByValue** : The parameter accepts values that match the expected .NET type or that can be converted to that type.</span></span>

  <span data-ttu-id="15b0b-154">De para meter **name** van accepteert de `Start-Service` invoer van de pijp lijn op waarde.</span><span class="sxs-lookup"><span data-stu-id="15b0b-154">For example, the **Name** parameter of `Start-Service` accepts pipeline input by value.</span></span> <span data-ttu-id="15b0b-155">Het kan teken reeks objecten of objecten accepteren die kunnen worden geconverteerd naar teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="15b0b-155">It can accept string objects or objects that can be converted to strings.</span></span>

- <span data-ttu-id="15b0b-156">**ByPropertyName** : de para meter accepteert alleen invoer wanneer het invoer object een eigenschap heeft met dezelfde naam als de para meter.</span><span class="sxs-lookup"><span data-stu-id="15b0b-156">**ByPropertyName** : The parameter accepts input only when the input object has a property of the same name as the parameter.</span></span>

  <span data-ttu-id="15b0b-157">De para meter name van kan bijvoorbeeld `Start-Service` objecten accepteren die een eigenschap **naam** hebben.</span><span class="sxs-lookup"><span data-stu-id="15b0b-157">For example, the Name parameter of `Start-Service` can accept objects that have a **Name** property.</span></span> <span data-ttu-id="15b0b-158">Als u de eigenschappen van een object wilt weer geven, pipet u het naar `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="15b0b-158">To list the properties of an object, pipe it to `Get-Member`.</span></span>

<span data-ttu-id="15b0b-159">Sommige para meters kunnen objecten accepteren op basis van waarde of eigenschaps naam, waardoor het gemakkelijker wordt om invoer uit de pijp lijn te halen.</span><span class="sxs-lookup"><span data-stu-id="15b0b-159">Some parameters can accept objects by both value or property name, making it easier to take input from the pipeline.</span></span>

### <a name="parameter-binding"></a><span data-ttu-id="15b0b-160">Parameter binding</span><span class="sxs-lookup"><span data-stu-id="15b0b-160">Parameter binding</span></span>

<span data-ttu-id="15b0b-161">Wanneer u objecten van de ene opdracht naar een andere opdracht Pipet, probeert Power shell de pijp lijn objecten te koppelen aan een para meter van de ontvangende cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15b0b-161">When you pipe objects from one command to another command, PowerShell attempts to associate the piped objects with a parameter of the receiving cmdlet.</span></span>

<span data-ttu-id="15b0b-162">Het onderdeel parameter binding van Power shell koppelt de invoer objecten aan cmdlet-para meters op basis van de volgende criteria:</span><span class="sxs-lookup"><span data-stu-id="15b0b-162">PowerShell's parameter binding component associates the input objects with cmdlet parameters according to the following criteria:</span></span>

- <span data-ttu-id="15b0b-163">De para meter moet invoer van een pijp lijn accepteren.</span><span class="sxs-lookup"><span data-stu-id="15b0b-163">The parameter must accept input from a pipeline.</span></span>
- <span data-ttu-id="15b0b-164">De para meter moet het type object accepteren dat wordt verzonden of een type dat kan worden geconverteerd naar het verwachte type.</span><span class="sxs-lookup"><span data-stu-id="15b0b-164">The parameter must accept the type of object being sent or a type that can be converted to the expected type.</span></span>
- <span data-ttu-id="15b0b-165">De para meter wordt niet gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="15b0b-165">The parameter wasn't used in the command.</span></span>

<span data-ttu-id="15b0b-166">De `Start-Service` cmdlet heeft bijvoorbeeld een groot aantal para meters, maar slechts twee hiervan, de **naam** en **input object** accepteren pijplijn invoer.</span><span class="sxs-lookup"><span data-stu-id="15b0b-166">For example, the `Start-Service` cmdlet has many parameters, but only two of them, **Name** and **InputObject** accept pipeline input.</span></span> <span data-ttu-id="15b0b-167">De para meter **name** heeft teken reeksen en de para meter **input object** maakt gebruik van service objecten.</span><span class="sxs-lookup"><span data-stu-id="15b0b-167">The **Name** parameter takes strings and the **InputObject** parameter takes service objects.</span></span> <span data-ttu-id="15b0b-168">Daarom kunt u teken reeksen, service objecten en objecten pipet met eigenschappen die kunnen worden geconverteerd naar teken reeks-of service objecten.</span><span class="sxs-lookup"><span data-stu-id="15b0b-168">Therefore, you can pipe strings, service objects, and objects with properties that can be converted to string or service objects.</span></span>

<span data-ttu-id="15b0b-169">Power shell beheert de parameter binding zo efficiënt mogelijk.</span><span class="sxs-lookup"><span data-stu-id="15b0b-169">PowerShell manages parameter binding as efficiently as possible.</span></span> <span data-ttu-id="15b0b-170">U kunt de Power shell niet om te koppelen aan een specifieke para meter Voorst Ellen of afdwingen.</span><span class="sxs-lookup"><span data-stu-id="15b0b-170">You can't suggest or force the PowerShell to bind to a specific parameter.</span></span> <span data-ttu-id="15b0b-171">De opdracht mislukt als Power shell de objecten in de pijp lijn niet kan binden.</span><span class="sxs-lookup"><span data-stu-id="15b0b-171">The command fails if PowerShell can't bind the piped objects.</span></span>

<span data-ttu-id="15b0b-172">Zie voor meer informatie over het oplossen van verbindings fouten verderop in dit artikel [pijplijn fouten onderzoeken](#investigating-pipeline-errors) .</span><span class="sxs-lookup"><span data-stu-id="15b0b-172">For more information about troubleshooting binding errors, see [Investigating Pipeline Errors](#investigating-pipeline-errors) later in this article.</span></span>

### <a name="one-at-a-time-processing"></a><span data-ttu-id="15b0b-173">Een-op-een-verwerking</span><span class="sxs-lookup"><span data-stu-id="15b0b-173">One-at-a-time processing</span></span>

<span data-ttu-id="15b0b-174">Pijpleiding objecten naar een opdracht zijn vergelijkbaar met het gebruik van een para meter van de opdracht voor het indienen van de objecten.</span><span class="sxs-lookup"><span data-stu-id="15b0b-174">Piping objects to a command is much like using a parameter of the command to submit the objects.</span></span> <span data-ttu-id="15b0b-175">Laten we eens kijken naar een voor beeld van een pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="15b0b-175">Let's look at a pipeline example.</span></span> <span data-ttu-id="15b0b-176">In dit voor beeld gebruiken we een pijp lijn om een tabel met Service objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="15b0b-176">In this example, we use a pipeline to display a table of service objects.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="15b0b-177">Dit is functioneel, zoals het gebruik van de para meter **input object** van `Format-Table` om de object verzameling in te dienen.</span><span class="sxs-lookup"><span data-stu-id="15b0b-177">Functionally, this is like using the **InputObject** parameter of `Format-Table` to submit the object collection.</span></span>

<span data-ttu-id="15b0b-178">We kunnen bijvoorbeeld het verzamelen van services opslaan in een variabele die wordt door gegeven met behulp van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="15b0b-178">For example, we can save the collection of services to a variable that is passed using the **InputObject** parameter.</span></span>

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

<span data-ttu-id="15b0b-179">Of we kunnen de opdracht insluiten in de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="15b0b-179">Or we can embed the command in the **InputObject** parameter.</span></span>

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

<span data-ttu-id="15b0b-180">Er is echter een belang rijk verschil.</span><span class="sxs-lookup"><span data-stu-id="15b0b-180">However, there's an important difference.</span></span> <span data-ttu-id="15b0b-181">Wanneer u meerdere objecten naar een opdracht Pipet, verzendt Power shell de objecten een voor een naar de opdracht.</span><span class="sxs-lookup"><span data-stu-id="15b0b-181">When you pipe multiple objects to a command, PowerShell sends the objects to the command one at a time.</span></span> <span data-ttu-id="15b0b-182">Wanneer u een opdracht parameter gebruikt, worden de objecten als één matrix object verzonden.</span><span class="sxs-lookup"><span data-stu-id="15b0b-182">When you use a command parameter, the objects are sent as a single array object.</span></span> <span data-ttu-id="15b0b-183">Dit secundaire verschil heeft aanzienlijke gevolgen.</span><span class="sxs-lookup"><span data-stu-id="15b0b-183">This minor difference has significant consequences.</span></span>

<span data-ttu-id="15b0b-184">Bij het uitvoeren van een pijp lijn wordt door Power shell automatisch een wille keurig type geïnventariseerd dat de interface implementeert `IEnumerable` en de leden een voor een verzendt via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="15b0b-184">When executing a pipeline, PowerShell automatically enumerates any type that implements the `IEnumerable` interface and sends the members through the pipeline one at a time.</span></span> <span data-ttu-id="15b0b-185">De uitzonde ring is `[hashtable]` , waarvoor een aanroep naar de methode is vereist `GetEnumerator()` .</span><span class="sxs-lookup"><span data-stu-id="15b0b-185">The exception is `[hashtable]`, which requires a call to the `GetEnumerator()` method.</span></span>

<span data-ttu-id="15b0b-186">In de volgende voor beelden worden een matrix en een hashtabel door gegeven aan de `Measure-Object` cmdlet om het aantal ontvangen objecten van de pijp lijn te tellen.</span><span class="sxs-lookup"><span data-stu-id="15b0b-186">In the following examples, an array and a hashtable are piped to the `Measure-Object` cmdlet to count the number of objects received from the pipeline.</span></span> <span data-ttu-id="15b0b-187">De matrix heeft meerdere leden en de hashtabel heeft meerdere sleutel-waardeparen.</span><span class="sxs-lookup"><span data-stu-id="15b0b-187">The array has multiple members, and the hashtable has multiple key-value pairs.</span></span> <span data-ttu-id="15b0b-188">Alleen de matrix wordt een voor een opgesomd.</span><span class="sxs-lookup"><span data-stu-id="15b0b-188">Only the array is enumerated one at a time.</span></span>

```powershell
@(1,2,3) | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

```powershell
@{"One"=1;"Two"=2} | Measure-Object
```

```Output
Count    : 1
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

<span data-ttu-id="15b0b-189">En als u meerdere proces objecten van de `Get-Process` cmdlet naar de cmdlet pipet `Get-Member` , verzendt Power shell elk proces object, één per keer, naar `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="15b0b-189">Similarly, if you pipe multiple process objects from the `Get-Process` cmdlet to the `Get-Member` cmdlet, PowerShell sends each process object, one at a time, to `Get-Member`.</span></span> <span data-ttu-id="15b0b-190">`Get-Member` Hiermee worden de .NET-klasse (type) van de proces objecten en hun eigenschappen en methoden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="15b0b-190">`Get-Member` displays the .NET class (type) of the process objects, and their properties and methods.</span></span>

```powershell
Get-Process | Get-Member
```

```Output
TypeName: System.Diagnostics.Process

Name      MemberType     Definition
----      ----------     ----------
Handles   AliasProperty  Handles = Handlecount
Name      AliasProperty  Name = ProcessName
NPM       AliasProperty  NPM = NonpagedSystemMemorySize
...
```

> [!NOTE]
> <span data-ttu-id="15b0b-191">`Get-Member` elimineert dubbele items, dus als de objecten allemaal van hetzelfde type zijn, wordt slechts één object type weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="15b0b-191">`Get-Member` eliminates duplicates, so if the objects are all of the same type, it only displays one object type.</span></span>

<span data-ttu-id="15b0b-192">Als u echter de para meter **input object** van gebruikt `Get-Member` , `Get-Member` ontvangt deze een matrix van **System. Diagnostics. process** -objecten als één eenheid.</span><span class="sxs-lookup"><span data-stu-id="15b0b-192">However, if you use the **InputObject** parameter of `Get-Member`, then `Get-Member` receives an array of **System.Diagnostics.Process** objects as a single unit.</span></span> <span data-ttu-id="15b0b-193">De eigenschappen van een matrix met objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="15b0b-193">It displays the properties of an array of objects.</span></span> <span data-ttu-id="15b0b-194">(Noteer het matrix symbool ( `[]` ) na de naam van het type **System. object** .)</span><span class="sxs-lookup"><span data-stu-id="15b0b-194">(Note the array symbol (`[]`) after the **System.Object** type name.)</span></span>

<span data-ttu-id="15b0b-195">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15b0b-195">For example,</span></span>

```powershell
Get-Member -InputObject (Get-Process)
```

```Output
TypeName: System.Object[]

Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
Address            Method        System.Object& Address(Int32 )
Clone              Method        System.Object Clone()
...
```

<span data-ttu-id="15b0b-196">Dit resultaat is mogelijk niet geschikt voor u.</span><span class="sxs-lookup"><span data-stu-id="15b0b-196">This result might not be what you intended.</span></span> <span data-ttu-id="15b0b-197">Maar wanneer u het begrijpt, kunt u het gebruiken.</span><span class="sxs-lookup"><span data-stu-id="15b0b-197">But after you understand it, you can use it.</span></span> <span data-ttu-id="15b0b-198">Alle Matrix objecten hebben bijvoorbeeld een eigenschap **Count** .</span><span class="sxs-lookup"><span data-stu-id="15b0b-198">For example, all array objects have a **Count** property.</span></span> <span data-ttu-id="15b0b-199">U kunt dit gebruiken om het aantal processen te tellen dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="15b0b-199">You can use that to count the number of processes running on the computer.</span></span>

<span data-ttu-id="15b0b-200">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15b0b-200">For example,</span></span>

```powershell
(Get-Process).count
```

<span data-ttu-id="15b0b-201">Het is belang rijk om te onthouden dat objecten die via de pijp lijn zijn verzonden, een voor een worden bezorgd.</span><span class="sxs-lookup"><span data-stu-id="15b0b-201">It's important to remember that objects sent down the pipeline are delivered one at a time.</span></span>

## <a name="investigating-pipeline-errors"></a><span data-ttu-id="15b0b-202">Pijplijn fouten onderzoeken</span><span class="sxs-lookup"><span data-stu-id="15b0b-202">Investigating pipeline errors</span></span>

<span data-ttu-id="15b0b-203">Wanneer Power shell de objecten in de pipes niet kan koppelen aan een para meter van de ontvangende cmdlet, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="15b0b-203">When PowerShell can't associate the piped objects with a parameter of the receiving cmdlet, the command fails.</span></span>

<span data-ttu-id="15b0b-204">In het volgende voor beeld proberen we een register vermelding van de ene register sleutel naar een andere te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="15b0b-204">In the following example, we try to move a registry entry from one registry key to another.</span></span> <span data-ttu-id="15b0b-205">`Get-Item`Met de cmdlet wordt het doelpad opgehaald, dat vervolgens wordt doorgeleid naar de `Move-ItemProperty` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15b0b-205">The `Get-Item` cmdlet gets the destination path, which is then piped to the `Move-ItemProperty` cmdlet.</span></span> <span data-ttu-id="15b0b-206">De `Move-ItemProperty` opdracht geeft het huidige pad en de naam van de register vermelding die moet worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="15b0b-206">The `Move-ItemProperty` command specifies the current path and name of the registry entry to be moved.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

<span data-ttu-id="15b0b-207">De opdracht mislukt en in Power shell wordt het volgende fout bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="15b0b-207">The command fails and PowerShell displays the following error message:</span></span>

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

<span data-ttu-id="15b0b-208">Als u wilt onderzoeken, gebruikt u de `Trace-Command` cmdlet voor het traceren van het parameter bindings onderdeel van Power shell.</span><span class="sxs-lookup"><span data-stu-id="15b0b-208">To investigate, use the `Trace-Command` cmdlet to trace the parameter binding component of PowerShell.</span></span> <span data-ttu-id="15b0b-209">In het volgende voor beeld wordt de parameter binding tijdens de uitvoering van de pijp lijn traceren.</span><span class="sxs-lookup"><span data-stu-id="15b0b-209">The following example traces parameter binding while the pipeline is executing.</span></span> <span data-ttu-id="15b0b-210">De para meter **PSHost** geeft de tracerings resultaten in de-console en de **filepath** para meter de tracerings resultaten naar het `debug.txt` bestand verzenden voor latere referentie.</span><span class="sxs-lookup"><span data-stu-id="15b0b-210">The **PSHost** parameter displays the trace results in the console and the **FilePath** parameter send the trace results to the `debug.txt` file for later reference.</span></span>

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

<span data-ttu-id="15b0b-211">De resultaten van de tracering zijn lang, maar ze tonen de waarden die aan de cmdlet zijn gebonden `Get-Item` en vervolgens worden de benoemde waarden gebonden aan de `Move-ItemProperty` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15b0b-211">The results of the trace are lengthy, but they show the values being bound to the `Get-Item` cmdlet and then the named values being bound to the `Move-ItemProperty` cmdlet.</span></span>

```Output
...
BIND NAMED cmd line args [`Move-ItemProperty`]
BIND arg [HKLM:\Software\MyCompany\design] to parameter [Path]
...
BIND arg [product] to parameter [Name]
...
BIND POSITIONAL cmd line args [`Move-ItemProperty`]
...
```

<span data-ttu-id="15b0b-212">Ten slotte ziet u dat de poging om het pad te binden aan de para meter **Destination** van `Move-ItemProperty` failed.</span><span class="sxs-lookup"><span data-stu-id="15b0b-212">Finally, it shows that the attempt to bind the path to the **Destination** parameter of `Move-ItemProperty` failed.</span></span>

```Output
...
BIND PIPELINE object to parameters: [`Move-ItemProperty`]
PIPELINE object TYPE = [Microsoft.Win32.RegistryKey]
RESTORING pipeline parameter's original values
Parameter [Destination] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
Parameter [Credential] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
...
```

<span data-ttu-id="15b0b-213">Gebruik de `Get-Help` cmdlet om de kenmerken van de **doel** parameter weer te geven.</span><span class="sxs-lookup"><span data-stu-id="15b0b-213">Use the `Get-Help` cmdlet to view the attributes of the **Destination** parameter.</span></span>

```Output
Get-Help Move-ItemProperty -Parameter Destination

-Destination <String>
    Specifies the path to the destination location.

    Required?                    true
    Position?                    1
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  false
```

<span data-ttu-id="15b0b-214">De resultaten geven aan dat de **bestemming** alleen voor de invoer van de pijp lijn wordt gebruikt door de naam van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="15b0b-214">The results show that **Destination** takes pipeline input only "by property name".</span></span> <span data-ttu-id="15b0b-215">Daarom moet het object met pijp lijn een eigenschap met de naam **Destination** hebben.</span><span class="sxs-lookup"><span data-stu-id="15b0b-215">Therefore, the piped object must have a property named **Destination**.</span></span>

<span data-ttu-id="15b0b-216">Gebruiken `Get-Member` om de eigenschappen van het object weer te geven die afkomstig zijn van `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="15b0b-216">Use `Get-Member` to see the properties of the object coming from `Get-Item`.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

<span data-ttu-id="15b0b-217">In de uitvoer ziet u dat het item een **micro soft. Win32. RegistryKey** -object is dat geen **doel** eigenschap heeft.</span><span class="sxs-lookup"><span data-stu-id="15b0b-217">The output shows that the item is a **Microsoft.Win32.RegistryKey** object that doesn't have a **Destination** property.</span></span> <span data-ttu-id="15b0b-218">In dit artikel wordt uitgelegd waarom de opdracht is mislukt.</span><span class="sxs-lookup"><span data-stu-id="15b0b-218">That explains why the command failed.</span></span>

<span data-ttu-id="15b0b-219">De para meter **Path** accepteert de invoer van de pijp lijn op naam of op waarde.</span><span class="sxs-lookup"><span data-stu-id="15b0b-219">The **Path** parameter accepts pipeline input by name or by value.</span></span>

```Output
Get-Help Move-ItemProperty -Parameter Path

-Path <String[]>
    Specifies the path to the current location of the property. Wildcard
    characters are permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  true
```

<span data-ttu-id="15b0b-220">Als u de opdracht wilt herstellen, moet u het doel opgeven in de `Move-ItemProperty` cmdlet en gebruiken `Get-Item` om het **pad** op te halen van het item dat u wilt verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="15b0b-220">To fix the command, we must specify the destination in the `Move-ItemProperty` cmdlet and use `Get-Item` to get the **Path** of the item we want to move.</span></span>

<span data-ttu-id="15b0b-221">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15b0b-221">For example,</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a><span data-ttu-id="15b0b-222">Intrinsieke regel voortzetting</span><span class="sxs-lookup"><span data-stu-id="15b0b-222">Intrinsic line continuation</span></span>

<span data-ttu-id="15b0b-223">Zoals al besproken, is een pijp lijn een reeks opdrachten die zijn verbonden door pijplijn operators ( `|` ), die meestal op één regel zijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="15b0b-223">As already discussed, a pipeline is a series of commands connected by pipeline operators (`|`), usually written on a single line.</span></span> <span data-ttu-id="15b0b-224">Voor de Lees baarheid kunt u met Power shell echter de pijp lijn splitsen over meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="15b0b-224">However, for readability, PowerShell allows you to split the pipeline across multiple lines.</span></span>
<span data-ttu-id="15b0b-225">Wanneer een pipe-operator het laatste token op de regel is, voegt de Power shell-parser de volgende regel toe aan de huidige opdracht om door te gaan met de constructie van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="15b0b-225">When a pipe operator is the last token on the line, the PowerShell parser joins the next line to current command to continue the construction of the pipeline.</span></span>

<span data-ttu-id="15b0b-226">Bijvoorbeeld de volgende pijp lijn met één regel:</span><span class="sxs-lookup"><span data-stu-id="15b0b-226">For example, the following single-line pipeline:</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="15b0b-227">kan worden geschreven als:</span><span class="sxs-lookup"><span data-stu-id="15b0b-227">can be written as:</span></span>

```powershell
Command-1 |
  Command-2 |
    Command-3
```

<span data-ttu-id="15b0b-228">De voorloop spaties op de volgende regels zijn niet significant.</span><span class="sxs-lookup"><span data-stu-id="15b0b-228">The leading spaces on the subsequent lines are not significant.</span></span> <span data-ttu-id="15b0b-229">De inspringing verbetert de Lees baarheid.</span><span class="sxs-lookup"><span data-stu-id="15b0b-229">The indentation enhances readability.</span></span>

## <a name="see-also"></a><span data-ttu-id="15b0b-230">Zie ook</span><span class="sxs-lookup"><span data-stu-id="15b0b-230">See Also</span></span>

[<span data-ttu-id="15b0b-231">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="15b0b-231">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="15b0b-232">about_Objects</span><span class="sxs-lookup"><span data-stu-id="15b0b-232">about_Objects</span></span>](about_objects.md)

[<span data-ttu-id="15b0b-233">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="15b0b-233">about_Parameters</span></span>](about_parameters.md)

[<span data-ttu-id="15b0b-234">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="15b0b-234">about_Command_Syntax</span></span>](about_command_syntax.md)

[<span data-ttu-id="15b0b-235">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="15b0b-235">about_ForEach</span></span>](about_foreach.md)
