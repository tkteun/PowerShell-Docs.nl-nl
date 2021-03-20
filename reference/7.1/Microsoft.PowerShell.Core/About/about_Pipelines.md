---
description: Opdrachten in de Power shell combi neren in pijp lijnen
Locale: en-US
ms.date: 03/18/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: 91c0d5f1f7b05b8c8536bf27a443c3894da01347
ms.sourcegitcommit: 16a02ae47d1a85b01692101aa0aa6e91e1ba398e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104726414"
---
# <a name="about-pipelines"></a><span data-ttu-id="50836-103">Over pijp lijnen</span><span class="sxs-lookup"><span data-stu-id="50836-103">About Pipelines</span></span>

## <a name="short-description"></a><span data-ttu-id="50836-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="50836-104">Short description</span></span>

<span data-ttu-id="50836-105">Opdrachten in de Power shell combi neren in pijp lijnen</span><span class="sxs-lookup"><span data-stu-id="50836-105">Combining commands into pipelines in the PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="50836-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="50836-106">Long description</span></span>

<span data-ttu-id="50836-107">Een pijp lijn is een reeks opdrachten die zijn verbonden door pijplijn operators ( `|` ) (ASCII 124).</span><span class="sxs-lookup"><span data-stu-id="50836-107">A pipeline is a series of commands connected by pipeline operators (`|`) (ASCII 124).</span></span> <span data-ttu-id="50836-108">Elke pijplijn operator verzendt de resultaten van de voor gaande opdracht naar de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="50836-108">Each pipeline operator sends the results of the preceding command to the next command.</span></span>

<span data-ttu-id="50836-109">De uitvoer van de eerste opdracht kan worden verzonden voor verwerking als invoer voor de tweede opdracht.</span><span class="sxs-lookup"><span data-stu-id="50836-109">The output of the first command can be sent for processing as input to the second command.</span></span> <span data-ttu-id="50836-110">En die uitvoer kan naar nog een andere opdracht worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="50836-110">And that output can be sent to yet another command.</span></span> <span data-ttu-id="50836-111">Het resultaat is een complexe opdracht reeks of- _pijp lijn_ die bestaat uit een reeks eenvoudige opdrachten.</span><span class="sxs-lookup"><span data-stu-id="50836-111">The result is a complex command chain or _pipeline_ that is composed of a series of simple commands.</span></span>

<span data-ttu-id="50836-112">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="50836-112">For example,</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="50836-113">In dit voor beeld worden de objecten `Command-1` verzonden naar `Command-2` .</span><span class="sxs-lookup"><span data-stu-id="50836-113">In this example, the objects that `Command-1` emits are sent to `Command-2`.</span></span>
<span data-ttu-id="50836-114">`Command-2` Hiermee worden de objecten verwerkt en verzonden naar `Command-3` .</span><span class="sxs-lookup"><span data-stu-id="50836-114">`Command-2` processes the objects and sends them to `Command-3`.</span></span> <span data-ttu-id="50836-115">`Command-3` de objecten worden verwerkt en verzonden naar de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="50836-115">`Command-3` processes the objects and send them down the pipeline.</span></span> <span data-ttu-id="50836-116">Omdat er geen opdrachten meer in de pijp lijn staan, worden de resultaten weer gegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="50836-116">Because there are no more commands in the pipeline, the results are displayed at the console.</span></span>

<span data-ttu-id="50836-117">In een pijp lijn worden de opdrachten verwerkt in volg orde van links naar rechts.</span><span class="sxs-lookup"><span data-stu-id="50836-117">In a pipeline, the commands are processed in order from left to right.</span></span> <span data-ttu-id="50836-118">De verwerking wordt verwerkt als één bewerking en de uitvoer wordt weer gegeven wanneer deze wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="50836-118">The processing is handled as a single operation and output is displayed as it's generated.</span></span>

<span data-ttu-id="50836-119">Hier volgt een eenvoudig voor beeld.</span><span class="sxs-lookup"><span data-stu-id="50836-119">Here is a simple example.</span></span> <span data-ttu-id="50836-120">Met de volgende opdracht wordt het klad blok proces opgehaald en vervolgens gestopt.</span><span class="sxs-lookup"><span data-stu-id="50836-120">The following command gets the Notepad process and then stops it.</span></span>

<span data-ttu-id="50836-121">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="50836-121">For example,</span></span>

```powershell
Get-Process notepad | Stop-Process
```

<span data-ttu-id="50836-122">Met de eerste opdracht wordt de `Get-Process` cmdlet gebruikt om een object op te halen dat het klad blok-proces vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="50836-122">The first command uses the `Get-Process` cmdlet to get an object representing the Notepad process.</span></span> <span data-ttu-id="50836-123">Er wordt een pijplijn operator ( `|` ) gebruikt om het proces object naar de cmdlet te verzenden `Stop-Process` , waardoor het klad blok-proces wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="50836-123">It uses a pipeline operator (`|`) to send the process object to the `Stop-Process` cmdlet, which stops the Notepad process.</span></span> <span data-ttu-id="50836-124">U ziet dat de `Stop-Process` opdracht geen **naam** of **id-** para meter heeft om het proces op te geven, omdat het opgegeven proces via de pijp lijn wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="50836-124">Notice that the `Stop-Process` command doesn't have a **Name** or **ID** parameter to specify the process, because the specified process is submitted through the pipeline.</span></span>

<span data-ttu-id="50836-125">In dit voor beeld van de pijp lijn worden de tekst bestanden in de huidige map opgehaald, worden alleen de bestanden geselecteerd die meer dan 10.000 bytes lang zijn, worden gesorteerd op lengte en worden de naam en de lengte van elk bestand in een tabel weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="50836-125">This pipeline example gets the text files in the current directory, selects only the files that are more than 10,000 bytes long, sorts them by length, and displays the name and length of each file in a table.</span></span>

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

<span data-ttu-id="50836-126">Deze pijp lijn bestaat uit vier opdrachten in de opgegeven volg orde.</span><span class="sxs-lookup"><span data-stu-id="50836-126">This pipeline consists of four commands in the specified order.</span></span> <span data-ttu-id="50836-127">In de volgende afbeelding ziet u de uitvoer van elke opdracht die wordt door gegeven aan de volgende opdracht in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="50836-127">The following illustration shows the output from each command as it's passed to the next command in the pipeline.</span></span>

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

## <a name="using-pipelines"></a><span data-ttu-id="50836-128">Pijp lijnen gebruiken</span><span class="sxs-lookup"><span data-stu-id="50836-128">Using pipelines</span></span>

<span data-ttu-id="50836-129">De meeste Power shell-cmdlets zijn ontworpen ter ondersteuning van pijp lijnen.</span><span class="sxs-lookup"><span data-stu-id="50836-129">Most PowerShell cmdlets are designed to support pipelines.</span></span> <span data-ttu-id="50836-130">In de meeste _gevallen kunt u_ de resultaten van een **Get** -cmdlet door geven aan een andere cmdlet van hetzelfde zelfstandig naam woord.</span><span class="sxs-lookup"><span data-stu-id="50836-130">In most cases, you can _pipe_ the results of a **Get** cmdlet to another cmdlet of the same noun.</span></span>
<span data-ttu-id="50836-131">U kunt bijvoorbeeld de uitvoer van de cmdlet door sluizen `Get-Service` naar de `Start-Service` `Stop-Service` cmdlets of.</span><span class="sxs-lookup"><span data-stu-id="50836-131">For example, you can pipe the output of the `Get-Service` cmdlet to the `Start-Service` or `Stop-Service` cmdlets.</span></span>

<span data-ttu-id="50836-132">In deze voorbeeld pijplijn wordt de WMI-service op de computer gestart:</span><span class="sxs-lookup"><span data-stu-id="50836-132">This example pipeline starts the WMI service on the computer:</span></span>

```powershell
Get-Service wmi | Start-Service
```

<span data-ttu-id="50836-133">Een ander voor beeld: u kunt de uitvoer van `Get-Item` of `Get-ChildItem` binnen de Power shell-register provider door geven aan de `New-ItemProperty` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="50836-133">For another example, you can pipe the output of `Get-Item` or `Get-ChildItem` within the PowerShell registry provider to the `New-ItemProperty` cmdlet.</span></span> <span data-ttu-id="50836-134">In dit voor beeld wordt een nieuwe register vermelding, **NoOfEmployees**, met de waarde **8124**, toegevoegd aan de register sleutel **mijn bedrijf** .</span><span class="sxs-lookup"><span data-stu-id="50836-134">This example adds a new registry entry, **NoOfEmployees**, with a value of **8124**, to the **MyCompany** registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

<span data-ttu-id="50836-135">Veel van de cmdlets van het hulp programma, zoals,,, `Get-Member` `Where-Object` `Sort-Object` `Group-Object` en `Measure-Object` worden bijna uitsluitend in pijp lijnen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="50836-135">Many of the utility cmdlets, such as `Get-Member`, `Where-Object`, `Sort-Object`, `Group-Object`, and `Measure-Object` are used almost exclusively in pipelines.</span></span> <span data-ttu-id="50836-136">U kunt elk object type door sluizen naar deze cmdlets.</span><span class="sxs-lookup"><span data-stu-id="50836-136">You can pipe any object type to these cmdlets.</span></span> <span data-ttu-id="50836-137">In dit voor beeld ziet u hoe alle processen op de computer worden gesorteerd op het aantal geopende ingangen in elk proces.</span><span class="sxs-lookup"><span data-stu-id="50836-137">This example shows how to sort all the processes on the computer by the number of open handles in each process.</span></span>

```powershell
Get-Process | Sort-Object -Property handles
```

<span data-ttu-id="50836-138">U kunt objecten door sluizen naar de indelings-, export-en uitvoer-cmdlets, zoals `Format-List` ,, `Format-Table` `Export-Clixml` , `Export-CSV` en `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="50836-138">You can pipe objects to the formatting, export, and output cmdlets, such as `Format-List`, `Format-Table`, `Export-Clixml`, `Export-CSV`, and `Out-File`.</span></span>

<span data-ttu-id="50836-139">In dit voor beeld ziet u hoe u de `Format-List` cmdlet gebruikt om een lijst met eigenschappen voor een proces object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="50836-139">This example shows how to use the `Format-List` cmdlet to display a list of properties for a process object.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="50836-140">U kunt ook de uitvoer van systeem eigen opdrachten door sluizen naar Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="50836-140">You can also pipe the output of native commands to PowerShell cmdlets.</span></span> <span data-ttu-id="50836-141">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="50836-141">For example:</span></span>

```powershell
PS> ipconfig.exe | Select-String -Pattern 'IPv4'

   IPv4 Address. . . . . . . . . . . : 172.24.80.1
   IPv4 Address. . . . . . . . . . . : 192.168.1.45
   IPv4 Address. . . . . . . . . . . : 100.64.108.37
```

> [!IMPORTANT]
> <span data-ttu-id="50836-142">De **slagen** -en **fout** stromen zijn vergelijkbaar met de stdin-en stderr-streams van andere shells.</span><span class="sxs-lookup"><span data-stu-id="50836-142">The **Success** and **Error** streams are similar to the stdin and stderr streams of other shells.</span></span> <span data-ttu-id="50836-143">Stdin is echter niet verbonden met de Power shell-pijp lijn voor invoer.</span><span class="sxs-lookup"><span data-stu-id="50836-143">However, stdin is not connected to the PowerShell pipeline for input.</span></span> <span data-ttu-id="50836-144">Zie [about_Redirection](about_Redirection.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="50836-144">For more information, see [about_Redirection](about_Redirection.md).</span></span>

<span data-ttu-id="50836-145">Met een beetje van de praktijk zult u zien dat het combi neren van eenvoudige opdrachten in pijp lijnen tijd en typen bespaart en uw scripting efficiënter maakt.</span><span class="sxs-lookup"><span data-stu-id="50836-145">With a bit of practice, you'll find that combining simple commands into pipelines saves time and typing, and makes your scripting more efficient.</span></span>

## <a name="how-pipelines-work"></a><span data-ttu-id="50836-146">Hoe pijp lijnen werken</span><span class="sxs-lookup"><span data-stu-id="50836-146">How pipelines work</span></span>

<span data-ttu-id="50836-147">In deze sectie wordt uitgelegd hoe invoer objecten zijn gebonden aan cmdlet-para meters en verwerkt tijdens de uitvoering van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="50836-147">This section explains how input objects are bound to cmdlet parameters and processed during pipeline execution.</span></span>

### <a name="accepts-pipeline-input"></a><span data-ttu-id="50836-148">Invoer van pijp lijn accepteren</span><span class="sxs-lookup"><span data-stu-id="50836-148">Accepts pipeline input</span></span>

<span data-ttu-id="50836-149">Voor de ondersteuning van pipelining moet de ontvangende cmdlet een para meter hebben die de invoer van de pijp lijn accepteert.</span><span class="sxs-lookup"><span data-stu-id="50836-149">To support pipelining, the receiving cmdlet must have a parameter that accepts pipeline input.</span></span> <span data-ttu-id="50836-150">Gebruik de `Get-Help` opdracht met de opties **Full** of **para meter** om te bepalen welke para meters van een cmdlet pijplijn invoer accepteren.</span><span class="sxs-lookup"><span data-stu-id="50836-150">Use the `Get-Help` command with the **Full** or **Parameter** options to determine which parameters of a cmdlet accept pipeline input.</span></span>

<span data-ttu-id="50836-151">Als u bijvoorbeeld wilt bepalen welke para meters van de `Start-Service` cmdlet pijplijn invoer accepteren, typt u:</span><span class="sxs-lookup"><span data-stu-id="50836-151">For example, to determine which of the parameters of the `Start-Service` cmdlet accepts pipeline input, type:</span></span>

```powershell
Get-Help Start-Service -Full
```

<span data-ttu-id="50836-152">of</span><span class="sxs-lookup"><span data-stu-id="50836-152">or</span></span>

```powershell
Get-Help Start-Service -Parameter *
```

<span data-ttu-id="50836-153">In de Help voor de `Start-Service` cmdlet ziet u dat alleen de **input object** -en **name** -para meters pijplijn invoer accepteren.</span><span class="sxs-lookup"><span data-stu-id="50836-153">The help for the `Start-Service` cmdlet shows that only the **InputObject** and **Name** parameters accept pipeline input.</span></span>

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

<span data-ttu-id="50836-154">Wanneer u objecten via de pijp lijn verzendt naar `Start-Service` , probeert Power shell de objecten te koppelen aan de para meters **input object** en **name** .</span><span class="sxs-lookup"><span data-stu-id="50836-154">When you send objects through the pipeline to `Start-Service`, PowerShell attempts to associate the objects with the **InputObject** and **Name** parameters.</span></span>

### <a name="methods-of-accepting-pipeline-input"></a><span data-ttu-id="50836-155">Methoden voor het accepteren van pijp lijn invoer</span><span class="sxs-lookup"><span data-stu-id="50836-155">Methods of accepting pipeline input</span></span>

<span data-ttu-id="50836-156">Cmdlets-para meters kunnen de invoer van de pijp lijn op twee verschillende manieren accepteren:</span><span class="sxs-lookup"><span data-stu-id="50836-156">Cmdlets parameters can accept pipeline input in one of two different ways:</span></span>

- <span data-ttu-id="50836-157">**ByValue**: de para meter accepteert waarden die overeenkomen met het verwachte .net-type of die kunnen worden geconverteerd naar dat type.</span><span class="sxs-lookup"><span data-stu-id="50836-157">**ByValue**: The parameter accepts values that match the expected .NET type or that can be converted to that type.</span></span>

  <span data-ttu-id="50836-158">De para meter **name** van accepteert de `Start-Service` invoer van de pijp lijn op waarde.</span><span class="sxs-lookup"><span data-stu-id="50836-158">For example, the **Name** parameter of `Start-Service` accepts pipeline input by value.</span></span> <span data-ttu-id="50836-159">Het kan teken reeks objecten of objecten accepteren die kunnen worden geconverteerd naar teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="50836-159">It can accept string objects or objects that can be converted to strings.</span></span>

- <span data-ttu-id="50836-160">**ByPropertyName**: de para meter accepteert alleen invoer wanneer het invoer object een eigenschap heeft met dezelfde naam als de para meter.</span><span class="sxs-lookup"><span data-stu-id="50836-160">**ByPropertyName**: The parameter accepts input only when the input object has a property of the same name as the parameter.</span></span>

  <span data-ttu-id="50836-161">De para meter name van kan bijvoorbeeld `Start-Service` objecten accepteren die een eigenschap **naam** hebben.</span><span class="sxs-lookup"><span data-stu-id="50836-161">For example, the Name parameter of `Start-Service` can accept objects that have a **Name** property.</span></span> <span data-ttu-id="50836-162">Als u de eigenschappen van een object wilt weer geven, pipet u het naar `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="50836-162">To list the properties of an object, pipe it to `Get-Member`.</span></span>

<span data-ttu-id="50836-163">Sommige para meters kunnen objecten accepteren op basis van waarde of eigenschaps naam, waardoor het gemakkelijker wordt om invoer uit de pijp lijn te halen.</span><span class="sxs-lookup"><span data-stu-id="50836-163">Some parameters can accept objects by both value or property name, making it easier to take input from the pipeline.</span></span>

### <a name="parameter-binding"></a><span data-ttu-id="50836-164">Parameter binding</span><span class="sxs-lookup"><span data-stu-id="50836-164">Parameter binding</span></span>

<span data-ttu-id="50836-165">Wanneer u objecten van de ene opdracht naar een andere opdracht Pipet, probeert Power shell de pijp lijn objecten te koppelen aan een para meter van de ontvangende cmdlet.</span><span class="sxs-lookup"><span data-stu-id="50836-165">When you pipe objects from one command to another command, PowerShell attempts to associate the piped objects with a parameter of the receiving cmdlet.</span></span>

<span data-ttu-id="50836-166">Het onderdeel parameter binding van Power shell koppelt de invoer objecten aan cmdlet-para meters op basis van de volgende criteria:</span><span class="sxs-lookup"><span data-stu-id="50836-166">PowerShell's parameter binding component associates the input objects with cmdlet parameters according to the following criteria:</span></span>

- <span data-ttu-id="50836-167">De para meter moet invoer van een pijp lijn accepteren.</span><span class="sxs-lookup"><span data-stu-id="50836-167">The parameter must accept input from a pipeline.</span></span>
- <span data-ttu-id="50836-168">De para meter moet het type object accepteren dat wordt verzonden of een type dat kan worden geconverteerd naar het verwachte type.</span><span class="sxs-lookup"><span data-stu-id="50836-168">The parameter must accept the type of object being sent or a type that can be converted to the expected type.</span></span>
- <span data-ttu-id="50836-169">De para meter wordt niet gebruikt in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="50836-169">The parameter wasn't used in the command.</span></span>

<span data-ttu-id="50836-170">De `Start-Service` cmdlet heeft bijvoorbeeld een groot aantal para meters, maar slechts twee hiervan, de **naam** en **input object** accepteren pijplijn invoer.</span><span class="sxs-lookup"><span data-stu-id="50836-170">For example, the `Start-Service` cmdlet has many parameters, but only two of them, **Name** and **InputObject** accept pipeline input.</span></span> <span data-ttu-id="50836-171">De para meter **name** heeft teken reeksen en de para meter **input object** maakt gebruik van service objecten.</span><span class="sxs-lookup"><span data-stu-id="50836-171">The **Name** parameter takes strings and the **InputObject** parameter takes service objects.</span></span> <span data-ttu-id="50836-172">Daarom kunt u teken reeksen, service objecten en objecten pipet met eigenschappen die kunnen worden geconverteerd naar teken reeks-of service objecten.</span><span class="sxs-lookup"><span data-stu-id="50836-172">Therefore, you can pipe strings, service objects, and objects with properties that can be converted to string or service objects.</span></span>

<span data-ttu-id="50836-173">Power shell beheert de parameter binding zo efficiënt mogelijk.</span><span class="sxs-lookup"><span data-stu-id="50836-173">PowerShell manages parameter binding as efficiently as possible.</span></span> <span data-ttu-id="50836-174">U kunt de Power shell niet om te koppelen aan een specifieke para meter Voorst Ellen of afdwingen.</span><span class="sxs-lookup"><span data-stu-id="50836-174">You can't suggest or force the PowerShell to bind to a specific parameter.</span></span> <span data-ttu-id="50836-175">De opdracht mislukt als Power shell de objecten in de pijp lijn niet kan binden.</span><span class="sxs-lookup"><span data-stu-id="50836-175">The command fails if PowerShell can't bind the piped objects.</span></span>

<span data-ttu-id="50836-176">Zie voor meer informatie over het oplossen van verbindings fouten verderop in dit artikel [pijplijn fouten onderzoeken](#investigating-pipeline-errors) .</span><span class="sxs-lookup"><span data-stu-id="50836-176">For more information about troubleshooting binding errors, see [Investigating Pipeline Errors](#investigating-pipeline-errors) later in this article.</span></span>

### <a name="one-at-a-time-processing"></a><span data-ttu-id="50836-177">Een-op-een-verwerking</span><span class="sxs-lookup"><span data-stu-id="50836-177">One-at-a-time processing</span></span>

<span data-ttu-id="50836-178">Pijpleiding objecten naar een opdracht zijn vergelijkbaar met het gebruik van een para meter van de opdracht voor het indienen van de objecten.</span><span class="sxs-lookup"><span data-stu-id="50836-178">Piping objects to a command is much like using a parameter of the command to submit the objects.</span></span> <span data-ttu-id="50836-179">Laten we eens kijken naar een voor beeld van een pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="50836-179">Let's look at a pipeline example.</span></span> <span data-ttu-id="50836-180">In dit voor beeld gebruiken we een pijp lijn om een tabel met Service objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="50836-180">In this example, we use a pipeline to display a table of service objects.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="50836-181">Dit is functioneel, zoals het gebruik van de para meter **input object** van `Format-Table` om de object verzameling in te dienen.</span><span class="sxs-lookup"><span data-stu-id="50836-181">Functionally, this is like using the **InputObject** parameter of `Format-Table` to submit the object collection.</span></span>

<span data-ttu-id="50836-182">We kunnen bijvoorbeeld het verzamelen van services opslaan in een variabele die wordt door gegeven met behulp van de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="50836-182">For example, we can save the collection of services to a variable that is passed using the **InputObject** parameter.</span></span>

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

<span data-ttu-id="50836-183">Of we kunnen de opdracht insluiten in de para meter **input object** .</span><span class="sxs-lookup"><span data-stu-id="50836-183">Or we can embed the command in the **InputObject** parameter.</span></span>

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

<span data-ttu-id="50836-184">Er is echter een belang rijk verschil.</span><span class="sxs-lookup"><span data-stu-id="50836-184">However, there's an important difference.</span></span> <span data-ttu-id="50836-185">Wanneer u meerdere objecten naar een opdracht Pipet, verzendt Power shell de objecten een voor een naar de opdracht.</span><span class="sxs-lookup"><span data-stu-id="50836-185">When you pipe multiple objects to a command, PowerShell sends the objects to the command one at a time.</span></span> <span data-ttu-id="50836-186">Wanneer u een opdracht parameter gebruikt, worden de objecten als één matrix object verzonden.</span><span class="sxs-lookup"><span data-stu-id="50836-186">When you use a command parameter, the objects are sent as a single array object.</span></span> <span data-ttu-id="50836-187">Dit secundaire verschil heeft aanzienlijke gevolgen.</span><span class="sxs-lookup"><span data-stu-id="50836-187">This minor difference has significant consequences.</span></span>

<span data-ttu-id="50836-188">Bij het uitvoeren van een pijp lijn wordt door Power shell automatisch een wille keurig type geïnventariseerd dat de interface implementeert `IEnumerable` en de leden een voor een verzendt via de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="50836-188">When executing a pipeline, PowerShell automatically enumerates any type that implements the `IEnumerable` interface and sends the members through the pipeline one at a time.</span></span> <span data-ttu-id="50836-189">De uitzonde ring is `[hashtable]` , waarvoor een aanroep naar de methode is vereist `GetEnumerator()` .</span><span class="sxs-lookup"><span data-stu-id="50836-189">The exception is `[hashtable]`, which requires a call to the `GetEnumerator()` method.</span></span>

<span data-ttu-id="50836-190">In de volgende voor beelden worden een matrix en een hashtabel door gegeven aan de `Measure-Object` cmdlet om het aantal ontvangen objecten van de pijp lijn te tellen.</span><span class="sxs-lookup"><span data-stu-id="50836-190">In the following examples, an array and a hashtable are piped to the `Measure-Object` cmdlet to count the number of objects received from the pipeline.</span></span> <span data-ttu-id="50836-191">De matrix heeft meerdere leden en de hashtabel heeft meerdere sleutel-waardeparen.</span><span class="sxs-lookup"><span data-stu-id="50836-191">The array has multiple members, and the hashtable has multiple key-value pairs.</span></span> <span data-ttu-id="50836-192">Alleen de matrix wordt een voor een opgesomd.</span><span class="sxs-lookup"><span data-stu-id="50836-192">Only the array is enumerated one at a time.</span></span>

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

<span data-ttu-id="50836-193">En als u meerdere proces objecten van de `Get-Process` cmdlet naar de cmdlet pipet `Get-Member` , verzendt Power shell elk proces object, één per keer, naar `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="50836-193">Similarly, if you pipe multiple process objects from the `Get-Process` cmdlet to the `Get-Member` cmdlet, PowerShell sends each process object, one at a time, to `Get-Member`.</span></span> <span data-ttu-id="50836-194">`Get-Member` Hiermee worden de .NET-klasse (type) van de proces objecten en hun eigenschappen en methoden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="50836-194">`Get-Member` displays the .NET class (type) of the process objects, and their properties and methods.</span></span>

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
> <span data-ttu-id="50836-195">`Get-Member` elimineert dubbele items, dus als de objecten allemaal van hetzelfde type zijn, wordt slechts één object type weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="50836-195">`Get-Member` eliminates duplicates, so if the objects are all of the same type, it only displays one object type.</span></span>

<span data-ttu-id="50836-196">Als u echter de para meter **input object** van gebruikt `Get-Member` , `Get-Member` ontvangt deze een matrix van **System. Diagnostics. process** -objecten als één eenheid.</span><span class="sxs-lookup"><span data-stu-id="50836-196">However, if you use the **InputObject** parameter of `Get-Member`, then `Get-Member` receives an array of **System.Diagnostics.Process** objects as a single unit.</span></span> <span data-ttu-id="50836-197">De eigenschappen van een matrix met objecten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="50836-197">It displays the properties of an array of objects.</span></span> <span data-ttu-id="50836-198">(Noteer het matrix symbool ( `[]` ) na de naam van het type **System. object** .)</span><span class="sxs-lookup"><span data-stu-id="50836-198">(Note the array symbol (`[]`) after the **System.Object** type name.)</span></span>

<span data-ttu-id="50836-199">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="50836-199">For example,</span></span>

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

<span data-ttu-id="50836-200">Dit resultaat is mogelijk niet geschikt voor u.</span><span class="sxs-lookup"><span data-stu-id="50836-200">This result might not be what you intended.</span></span> <span data-ttu-id="50836-201">Maar wanneer u het begrijpt, kunt u het gebruiken.</span><span class="sxs-lookup"><span data-stu-id="50836-201">But after you understand it, you can use it.</span></span> <span data-ttu-id="50836-202">Alle Matrix objecten hebben bijvoorbeeld een eigenschap **Count** .</span><span class="sxs-lookup"><span data-stu-id="50836-202">For example, all array objects have a **Count** property.</span></span> <span data-ttu-id="50836-203">U kunt dit gebruiken om het aantal processen te tellen dat op de computer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="50836-203">You can use that to count the number of processes running on the computer.</span></span>

<span data-ttu-id="50836-204">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="50836-204">For example,</span></span>

```powershell
(Get-Process).count
```

<span data-ttu-id="50836-205">Het is belang rijk om te onthouden dat objecten die via de pijp lijn zijn verzonden, een voor een worden bezorgd.</span><span class="sxs-lookup"><span data-stu-id="50836-205">It's important to remember that objects sent down the pipeline are delivered one at a time.</span></span>

## <a name="investigating-pipeline-errors"></a><span data-ttu-id="50836-206">Pijplijn fouten onderzoeken</span><span class="sxs-lookup"><span data-stu-id="50836-206">Investigating pipeline errors</span></span>

<span data-ttu-id="50836-207">Wanneer Power shell de objecten in de pipes niet kan koppelen aan een para meter van de ontvangende cmdlet, mislukt de opdracht.</span><span class="sxs-lookup"><span data-stu-id="50836-207">When PowerShell can't associate the piped objects with a parameter of the receiving cmdlet, the command fails.</span></span>

<span data-ttu-id="50836-208">In het volgende voor beeld proberen we een register vermelding van de ene register sleutel naar een andere te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="50836-208">In the following example, we try to move a registry entry from one registry key to another.</span></span> <span data-ttu-id="50836-209">`Get-Item`Met de cmdlet wordt het doelpad opgehaald, dat vervolgens wordt doorgeleid naar de `Move-ItemProperty` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="50836-209">The `Get-Item` cmdlet gets the destination path, which is then piped to the `Move-ItemProperty` cmdlet.</span></span> <span data-ttu-id="50836-210">De `Move-ItemProperty` opdracht geeft het huidige pad en de naam van de register vermelding die moet worden verplaatst.</span><span class="sxs-lookup"><span data-stu-id="50836-210">The `Move-ItemProperty` command specifies the current path and name of the registry entry to be moved.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

<span data-ttu-id="50836-211">De opdracht mislukt en in Power shell wordt het volgende fout bericht weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="50836-211">The command fails and PowerShell displays the following error message:</span></span>

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

<span data-ttu-id="50836-212">Als u wilt onderzoeken, gebruikt u de `Trace-Command` cmdlet voor het traceren van het parameter bindings onderdeel van Power shell.</span><span class="sxs-lookup"><span data-stu-id="50836-212">To investigate, use the `Trace-Command` cmdlet to trace the parameter binding component of PowerShell.</span></span> <span data-ttu-id="50836-213">In het volgende voor beeld wordt de parameter binding tijdens de uitvoering van de pijp lijn traceren.</span><span class="sxs-lookup"><span data-stu-id="50836-213">The following example traces parameter binding while the pipeline is executing.</span></span> <span data-ttu-id="50836-214">De para meter **PSHost** geeft de tracerings resultaten in de-console en de **filepath** para meter de tracerings resultaten naar het `debug.txt` bestand verzenden voor latere referentie.</span><span class="sxs-lookup"><span data-stu-id="50836-214">The **PSHost** parameter displays the trace results in the console and the **FilePath** parameter send the trace results to the `debug.txt` file for later reference.</span></span>

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

<span data-ttu-id="50836-215">De resultaten van de tracering zijn lang, maar ze tonen de waarden die aan de cmdlet zijn gebonden `Get-Item` en vervolgens worden de benoemde waarden gebonden aan de `Move-ItemProperty` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="50836-215">The results of the trace are lengthy, but they show the values being bound to the `Get-Item` cmdlet and then the named values being bound to the `Move-ItemProperty` cmdlet.</span></span>

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

<span data-ttu-id="50836-216">Ten slotte ziet u dat de poging om het pad te binden aan de para meter **Destination** van `Move-ItemProperty` failed.</span><span class="sxs-lookup"><span data-stu-id="50836-216">Finally, it shows that the attempt to bind the path to the **Destination** parameter of `Move-ItemProperty` failed.</span></span>

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

<span data-ttu-id="50836-217">Gebruik de `Get-Help` cmdlet om de kenmerken van de **doel** parameter weer te geven.</span><span class="sxs-lookup"><span data-stu-id="50836-217">Use the `Get-Help` cmdlet to view the attributes of the **Destination** parameter.</span></span>

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

<span data-ttu-id="50836-218">De resultaten geven aan dat de **bestemming** alleen voor de invoer van de pijp lijn wordt gebruikt door de naam van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="50836-218">The results show that **Destination** takes pipeline input only "by property name".</span></span> <span data-ttu-id="50836-219">Daarom moet het object met pijp lijn een eigenschap met de naam **Destination** hebben.</span><span class="sxs-lookup"><span data-stu-id="50836-219">Therefore, the piped object must have a property named **Destination**.</span></span>

<span data-ttu-id="50836-220">Gebruiken `Get-Member` om de eigenschappen van het object weer te geven die afkomstig zijn van `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="50836-220">Use `Get-Member` to see the properties of the object coming from `Get-Item`.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

<span data-ttu-id="50836-221">In de uitvoer ziet u dat het item een **micro soft. Win32. RegistryKey** -object is dat geen **doel** eigenschap heeft.</span><span class="sxs-lookup"><span data-stu-id="50836-221">The output shows that the item is a **Microsoft.Win32.RegistryKey** object that doesn't have a **Destination** property.</span></span> <span data-ttu-id="50836-222">In dit artikel wordt uitgelegd waarom de opdracht is mislukt.</span><span class="sxs-lookup"><span data-stu-id="50836-222">That explains why the command failed.</span></span>

<span data-ttu-id="50836-223">De para meter **Path** accepteert de invoer van de pijp lijn op naam of op waarde.</span><span class="sxs-lookup"><span data-stu-id="50836-223">The **Path** parameter accepts pipeline input by name or by value.</span></span>

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

<span data-ttu-id="50836-224">Als u de opdracht wilt herstellen, moet u het doel opgeven in de `Move-ItemProperty` cmdlet en gebruiken `Get-Item` om het **pad** op te halen van het item dat u wilt verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="50836-224">To fix the command, we must specify the destination in the `Move-ItemProperty` cmdlet and use `Get-Item` to get the **Path** of the item we want to move.</span></span>

<span data-ttu-id="50836-225">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="50836-225">For example,</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a><span data-ttu-id="50836-226">Intrinsieke regel voortzetting</span><span class="sxs-lookup"><span data-stu-id="50836-226">Intrinsic line continuation</span></span>

<span data-ttu-id="50836-227">Zoals al besproken, is een pijp lijn een reeks opdrachten die zijn verbonden door pijplijn operators ( `|` ), die meestal op één regel zijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="50836-227">As already discussed, a pipeline is a series of commands connected by pipeline operators (`|`), usually written on a single line.</span></span> <span data-ttu-id="50836-228">Voor de Lees baarheid kunt u met Power shell echter de pijp lijn splitsen over meerdere regels.</span><span class="sxs-lookup"><span data-stu-id="50836-228">However, for readability, PowerShell allows you to split the pipeline across multiple lines.</span></span>
<span data-ttu-id="50836-229">Wanneer een pipe-operator het laatste token op de regel is, voegt de Power shell-parser de volgende regel toe aan de huidige opdracht om door te gaan met de constructie van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="50836-229">When a pipe operator is the last token on the line, the PowerShell parser joins the next line to current command to continue the construction of the pipeline.</span></span>

<span data-ttu-id="50836-230">Bijvoorbeeld de volgende pijp lijn met één regel:</span><span class="sxs-lookup"><span data-stu-id="50836-230">For example, the following single-line pipeline:</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="50836-231">kan worden geschreven als:</span><span class="sxs-lookup"><span data-stu-id="50836-231">can be written as:</span></span>

```powershell
Command-1 |
  Command-2 |
    Command-3
```

<span data-ttu-id="50836-232">De voorloop spaties op de volgende regels zijn niet significant.</span><span class="sxs-lookup"><span data-stu-id="50836-232">The leading spaces on the subsequent lines are not significant.</span></span> <span data-ttu-id="50836-233">De inspringing verbetert de Lees baarheid.</span><span class="sxs-lookup"><span data-stu-id="50836-233">The indentation enhances readability.</span></span>

<span data-ttu-id="50836-234">Power shell 7 voegt ondersteuning toe voor voortzetting van pijp lijnen met het pijp lijn teken aan het begin van een regel.</span><span class="sxs-lookup"><span data-stu-id="50836-234">PowerShell 7 adds support for continuation of pipelines with the pipeline character at the beginning of a line.</span></span> <span data-ttu-id="50836-235">In de volgende voor beelden ziet u hoe u deze nieuwe functionaliteit kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="50836-235">The following examples show how you could use this new functionality.</span></span>

```powershell
# Wrapping with a pipe at the beginning of a line (no backtick required)
Get-Process | Where-Object CPU | Where-Object Path
    | Get-Item | Where-Object FullName -match "AppData"
    | Sort-Object FullName -Unique

# Wrapping with a pipe on a line by itself
Get-Process | Where-Object CPU | Where-Object Path
    |
    Get-Item | Where-Object FullName -match "AppData"
    |
    Sort-Object FullName -Unique
```

> [!IMPORTANT]
> <span data-ttu-id="50836-236">Wanneer u interactief werkt in de shell, moet u code met pijp lijnen alleen aan het begin van een regel plakken wanneer u <kbd>CTRL</kbd> + <kbd>V</kbd> gebruikt om te plakken.</span><span class="sxs-lookup"><span data-stu-id="50836-236">When working interactively in the shell, pasting code with pipelines at the beginning of a line only when using <kbd>Ctrl</kbd>+<kbd>V</kbd> to paste.</span></span>
> <span data-ttu-id="50836-237">Klik met de rechter muisknop op plak bewerkingen Voeg de regels een voor een in.</span><span class="sxs-lookup"><span data-stu-id="50836-237">Right-click paste operations insert the lines one at a time.</span></span> <span data-ttu-id="50836-238">Omdat de regel niet eindigt met een pijp lijn teken, beschouwt Power shell de invoer als voltooid en wordt die regel uitgevoerd als ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="50836-238">Since the line does not end with a pipeline character, PowerShell considers the input to be complete and executes that line as entered.</span></span>

## <a name="see-also"></a><span data-ttu-id="50836-239">Zie ook</span><span class="sxs-lookup"><span data-stu-id="50836-239">See Also</span></span>

[<span data-ttu-id="50836-240">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="50836-240">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="50836-241">about_Objects</span><span class="sxs-lookup"><span data-stu-id="50836-241">about_Objects</span></span>](about_objects.md)

[<span data-ttu-id="50836-242">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="50836-242">about_Parameters</span></span>](about_parameters.md)

[<span data-ttu-id="50836-243">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="50836-243">about_Command_Syntax</span></span>](about_command_syntax.md)

[<span data-ttu-id="50836-244">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="50836-244">about_ForEach</span></span>](about_foreach.md)
