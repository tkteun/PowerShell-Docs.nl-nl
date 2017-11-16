---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Gegevens met Out Cmdlets omleiden
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: e570ca1c2c665a4a5d23abb50d4102a012b160e9
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="16495-103">Gegevens met Out - omleiden * Cmdlets</span><span class="sxs-lookup"><span data-stu-id="16495-103">Redirecting Data with Out-* Cmdlets</span></span>
<span data-ttu-id="16495-104">Windows PowerShell biedt diverse cmdlets waarmee die u gegevens uitvoer rechtstreeks beheren.</span><span class="sxs-lookup"><span data-stu-id="16495-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="16495-105">Deze cmdlets kunt u twee belangrijke kenmerken delen.</span><span class="sxs-lookup"><span data-stu-id="16495-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="16495-106">Eerst transformeren ze doorgaans gegevens naar een vorm van tekst.</span><span class="sxs-lookup"><span data-stu-id="16495-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="16495-107">Dit wordt gedaan omdat ze de gegevens naar de onderdelen van het systeem waarvoor tekstinvoer uitvoer.</span><span class="sxs-lookup"><span data-stu-id="16495-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="16495-108">Dit betekent dat ze nodig hebben om weer te geven van de objecten als tekst.</span><span class="sxs-lookup"><span data-stu-id="16495-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="16495-109">De tekst is daarom opgemaakt als u deze in het venster Windows PowerShell-console bekijken.</span><span class="sxs-lookup"><span data-stu-id="16495-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="16495-110">Deze cmdlets gebruik vervolgens de Windows PowerShell-opdracht **uit** omdat ze gegevens uit vanuit Windows PowerShell op een andere locatie verzonden.</span><span class="sxs-lookup"><span data-stu-id="16495-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="16495-111">De **uitgaande Host** cmdlet vormt daarop geen uitzondering: de weergave in de host bevindt zich buiten het Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16495-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="16495-112">Dit is belangrijk omdat wanneer gegevens worden verzonden buiten Windows PowerShell, wordt dit daadwerkelijk verwijderd.</span><span class="sxs-lookup"><span data-stu-id="16495-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="16495-113">U kunt dit zien als u probeert te maken van een pijplijn die pagina's gegevens naar het hostvenster en vervolgens probeert te formatteren als een lijst als volgt te werk:</span><span class="sxs-lookup"><span data-stu-id="16495-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```
PS> Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="16495-114">U kunt de opdracht uit om de pagina's van de procesinformatie weergeven in lijstindeling zou verwachten.</span><span class="sxs-lookup"><span data-stu-id="16495-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="16495-115">In plaats daarvan wordt de standaardlijst in tabelvorm weergegeven:</span><span class="sxs-lookup"><span data-stu-id="16495-115">Instead, it displays the default tabular list:</span></span>

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="16495-116">De **uitgaande Host** cmdlet verzendt de gegevens rechtstreeks naar de console, zodat de **lijst indelen** opdracht ontvangt nooit iets te formatteren.</span><span class="sxs-lookup"><span data-stu-id="16495-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="16495-117">De juiste manier structuur van deze opdracht is te plaatsen de **uitgaande Host** cmdlet aan het einde van de pijplijn zoals hieronder wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="16495-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="16495-118">Dit zorgt ervoor dat de gegevens over het installatieproces worden ingedeeld in een lijst voordat wordt wisselbaar en weergegeven.</span><span class="sxs-lookup"><span data-stu-id="16495-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="16495-119">Dit geldt voor alle van de **uit** cmdlets.</span><span class="sxs-lookup"><span data-stu-id="16495-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="16495-120">Een **uit** cmdlet moet altijd worden weergegeven aan het einde van de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="16495-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="16495-121">Alle de **uit** cmdlets uitvoer weergegeven als tekst met de opmaak van kracht voor het consolevenster, met inbegrip van lengtebeperkingen regel.</span><span class="sxs-lookup"><span data-stu-id="16495-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

#### <a name="paging-console-output-out-host"></a><span data-ttu-id="16495-122">Console-uitvoer van het wisselbestand (uitgaande Host)</span><span class="sxs-lookup"><span data-stu-id="16495-122">Paging Console Output (Out-Host)</span></span>
<span data-ttu-id="16495-123">Standaard Windows PowerShell gegevens verzendt naar het hostvenster precies wat is de uitgaande hosten cmdlet heeft.</span><span class="sxs-lookup"><span data-stu-id="16495-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="16495-124">Het primaire gebruik voor de uitgaande hosten cmdlet is paginering gegevens, zoals eerder is besproken.</span><span class="sxs-lookup"><span data-stu-id="16495-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="16495-125">Bijvoorbeeld de volgende opdracht gebruikt uitgaande als host optreden voor de uitvoer van de cmdlet Get-Command pagina:</span><span class="sxs-lookup"><span data-stu-id="16495-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```
PS> Get-Command | Out-Host -Paging
```

<span data-ttu-id="16495-126">U kunt ook de **meer** functioneren op de paginagegevens.</span><span class="sxs-lookup"><span data-stu-id="16495-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="16495-127">In Windows PowerShell **meer** is een functie die aanroept **uitgaande Host-Paging**.</span><span class="sxs-lookup"><span data-stu-id="16495-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="16495-128">De volgende opdracht wordt gedemonstreerd met behulp van de **meer** functioneren op de pagina van de uitvoer van Get-opdracht:</span><span class="sxs-lookup"><span data-stu-id="16495-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```
PS> Get-Command | more
```

<span data-ttu-id="16495-129">Als u een of meer bestandsnamen als argumenten voor de functie meer opneemt, wordt de functie de opgegeven bestanden lezen en wordt de inhoud naar de host pagina:</span><span class="sxs-lookup"><span data-stu-id="16495-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

#### <a name="discarding-output-out-null"></a><span data-ttu-id="16495-130">Een van de uitvoer (uitgaande Null)</span><span class="sxs-lookup"><span data-stu-id="16495-130">Discarding Output (Out-Null)</span></span>
<span data-ttu-id="16495-131">De **uitgaande Null** cmdlet is ontworpen om onmiddellijk negeren invoer ontvangen.</span><span class="sxs-lookup"><span data-stu-id="16495-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="16495-132">Dit is handig voor het negeren van onnodige gegevens die u als gevolg krijgt van een opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="16495-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="16495-133">Wanneer Typ de volgende opdracht, er iets terug van de opdracht:</span><span class="sxs-lookup"><span data-stu-id="16495-133">When type the following command, you do not get anything back from the command:</span></span>

```
PS> Get-Command | Out-Null
```

<span data-ttu-id="16495-134">De **uitgaande Null** cmdlet heeft geen foutuitvoer negeren.</span><span class="sxs-lookup"><span data-stu-id="16495-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="16495-135">Bijvoorbeeld, als u de volgende opdracht invoert, een bericht weergegeven waarin wordt gemeld dat Windows PowerShell 'Is NotACommand' wordt niet herkend:</span><span class="sxs-lookup"><span data-stu-id="16495-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

#### <a name="printing-data-out-printer"></a><span data-ttu-id="16495-136">Gegevens voor afdrukken (Out-Printer)</span><span class="sxs-lookup"><span data-stu-id="16495-136">Printing Data (Out-Printer)</span></span>
<span data-ttu-id="16495-137">U kunt gegevens afdrukken met behulp van de **Out-Printer** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="16495-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="16495-138">De **Out-Printer** cmdlet standaardprinter wordt gebruikt als u de naam van een printer niet opgeeft.</span><span class="sxs-lookup"><span data-stu-id="16495-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="16495-139">U kunt een printer op basis van Windows gebruiken door op te geven van de weergavenaam.</span><span class="sxs-lookup"><span data-stu-id="16495-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="16495-140">Er is niet nodig voor elk soort printer poorttoewijzing of zelfs een echte fysieke printer.</span><span class="sxs-lookup"><span data-stu-id="16495-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="16495-141">Bijvoorbeeld, als u de Microsoft Office-document replicatiehulpprogramma's geïnstalleerd hebt, kunt u de gegevens verzenden naar een afbeeldingbestand door te typen:</span><span class="sxs-lookup"><span data-stu-id="16495-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```
PS> Get-Command Get-Command | Out-Printer -Name "Microsoft Office Document Image Writer"
```

#### <a name="saving-data-out-file"></a><span data-ttu-id="16495-142">Opslaan van gegevens (out-File)</span><span class="sxs-lookup"><span data-stu-id="16495-142">Saving Data (Out-File)</span></span>
<span data-ttu-id="16495-143">U kunt uitvoer naar een bestand in plaats van het consolevenster verzenden met behulp van de **out-File** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="16495-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="16495-144">De volgende opdrachtregel zendt een lijst van processen naar het bestand **C:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="16495-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="16495-145">De resultaten van het gebruik van de **out-File** cmdlet is wat u verwacht als u worden gebruikt voor traditionele uitvoeromleiding niet mogelijk.</span><span class="sxs-lookup"><span data-stu-id="16495-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="16495-146">Om het gedrag te begrijpen, moet u rekening houden met de context waarin de **out-File** cmdlet werkt.</span><span class="sxs-lookup"><span data-stu-id="16495-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="16495-147">Standaard de **out-File** cmdlet maakt een Unicode-bestand.</span><span class="sxs-lookup"><span data-stu-id="16495-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="16495-148">Dit is de aanbevolen standaardwaarde op de lange termijn, maar het betekent dat hulpprogramma's die ASCII-bestanden verwacht niet correct met de indeling van de standaard-uitvoer werken wordt.</span><span class="sxs-lookup"><span data-stu-id="16495-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="16495-149">U kunt de standaardindeling van uitvoer in ASCII wijzigen met behulp van de **codering** parameter:</span><span class="sxs-lookup"><span data-stu-id="16495-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```
PS> Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="16495-150">**Out-File** indelingen bestand inhoud eruitzien zoals bij console-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="16495-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="16495-151">Dit zorgt ervoor dat de uitvoer moet net als in een consolevenster in de meeste gevallen worden afgekapt.</span><span class="sxs-lookup"><span data-stu-id="16495-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="16495-152">Bijvoorbeeld, als u de volgende opdracht uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="16495-152">For example, if you run the following command:</span></span>

```
PS> Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="16495-153">De uitvoer ziet er als volgt:</span><span class="sxs-lookup"><span data-stu-id="16495-153">The output will look like this:</span></span>

```
CommandType     Name                            Definition                     
-----------     ----                            ----------                     
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="16495-154">Als u uitvoer die u hoeft niet regel terugloopt overeenkomen met de schermbreedte, kunt u de **breedte** lijnbreedte van de parameter.</span><span class="sxs-lookup"><span data-stu-id="16495-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="16495-155">Omdat **breedte** een 32-bits geheel getal-parameter is de maximale waarde kan hebben is 2147483647.</span><span class="sxs-lookup"><span data-stu-id="16495-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="16495-156">Typ het volgende om in te stellen van de breedte van de aan deze maximumwaarde:</span><span class="sxs-lookup"><span data-stu-id="16495-156">Type the following to set the line width to this maximum value:</span></span>

```
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="16495-157">De **out-File** cmdlet is handig wanneer u opslaan uitvoer wilt zoals deze zou hebben weergegeven op de console.</span><span class="sxs-lookup"><span data-stu-id="16495-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="16495-158">Voor een betere controle over de indeling van uitvoer moet u meer geavanceerde hulpprogramma's.</span><span class="sxs-lookup"><span data-stu-id="16495-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="16495-159">Laten we zien die in het volgende hoofdstuk, samen met een aantal details van het object bewerken.</span><span class="sxs-lookup"><span data-stu-id="16495-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>

