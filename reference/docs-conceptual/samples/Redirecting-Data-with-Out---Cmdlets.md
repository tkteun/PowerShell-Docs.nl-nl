---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Gegevens omleiden met Out-cmdlets
ms.openlocfilehash: d4cc14e26bdef0f973f948177d0c1e68929605fa
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030076"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="18d9a-103">Gegevens omleiden met Out-\* Cmdlets</span><span class="sxs-lookup"><span data-stu-id="18d9a-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="18d9a-104">Windows PowerShell biedt verschillende cmdlets waarmee die u gegevens rechtstreeks uitvoer beheren.</span><span class="sxs-lookup"><span data-stu-id="18d9a-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="18d9a-105">Deze cmdlets delen twee belangrijke kenmerken.</span><span class="sxs-lookup"><span data-stu-id="18d9a-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="18d9a-106">Eerst, ze algemeen gegevens transformeren naar een vorm van tekst.</span><span class="sxs-lookup"><span data-stu-id="18d9a-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="18d9a-107">Ze doen dit omdat ze de gegevens naar de onderdelen van het systeem waarvoor tekstinvoer uitvoer.</span><span class="sxs-lookup"><span data-stu-id="18d9a-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="18d9a-108">Dit betekent dat ze nodig hebben om weer te geven van de objecten als tekst.</span><span class="sxs-lookup"><span data-stu-id="18d9a-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="18d9a-109">De tekst is daarom opgemaakt als u deze in de Windows PowerShell-consolevenster bekijken.</span><span class="sxs-lookup"><span data-stu-id="18d9a-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="18d9a-110">Deze cmdlets gebruik vervolgens de Windows PowerShell-opdracht **uit** omdat ze gegevens vanuit Windows PowerShell op een andere locatie verzenden.</span><span class="sxs-lookup"><span data-stu-id="18d9a-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="18d9a-111">De **uitgaande hosten** cmdlet vormt daar geen uitzondering: de weergave in de host is buiten Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="18d9a-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="18d9a-112">Dit is belangrijk omdat wanneer gegevens uit de Windows PowerShell wordt verzonden, wordt deze daadwerkelijk verwijderd.</span><span class="sxs-lookup"><span data-stu-id="18d9a-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="18d9a-113">U kunt dit zien als u probeert te maken van een pijplijn die gegevens van de pagina's naar het hostvenster van de, en vervolgens probeert om deze als een lijst, zoals hier wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="18d9a-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="18d9a-114">U kunt de opdracht voor het weergeven van pagina's van de procesinformatie in lijstindeling had verwacht.</span><span class="sxs-lookup"><span data-stu-id="18d9a-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="18d9a-115">In plaats daarvan wordt de lijst in tabelvorm met weergegeven:</span><span class="sxs-lookup"><span data-stu-id="18d9a-115">Instead, it displays the default tabular list:</span></span>

```output
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

<span data-ttu-id="18d9a-116">De **uitgaande hosten** cmdlet verzendt die gegevens rechtstreeks naar de console, zodat de **lijst indeling** opdracht ontvangt nooit iets te formatteren.</span><span class="sxs-lookup"><span data-stu-id="18d9a-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="18d9a-117">De juiste manier te structureren met deze opdracht is te plaatsen de **uitgaande hosten** cmdlet aan het einde van de pijplijn, zoals hieronder weergegeven.</span><span class="sxs-lookup"><span data-stu-id="18d9a-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="18d9a-118">Dit zorgt ervoor dat de gegevens verwerken is opgemaakt in een lijst voordat deze wordt gewisseld en weergegeven.</span><span class="sxs-lookup"><span data-stu-id="18d9a-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

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

<span data-ttu-id="18d9a-119">Dit geldt voor alle van de **uit** cmdlets.</span><span class="sxs-lookup"><span data-stu-id="18d9a-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="18d9a-120">Een **uit** cmdlet moet altijd worden weergegeven aan het einde van de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="18d9a-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="18d9a-121">Alle de **uit** cmdlets uitvoer weergegeven als tekst, met behulp van de opmaak van kracht voor het consolevenster, met inbegrip van regel lengtebeperkingen.</span><span class="sxs-lookup"><span data-stu-id="18d9a-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

## <a name="paging-console-output-out-host"></a><span data-ttu-id="18d9a-122">Console-uitvoer voor het wisselbestand (uitgaande Host)</span><span class="sxs-lookup"><span data-stu-id="18d9a-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="18d9a-123">Standaard Windows PowerShell verzendt gegevens naar het hostvenster, dat precies wat is de uitgaande hosten cmdlet is.</span><span class="sxs-lookup"><span data-stu-id="18d9a-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="18d9a-124">Het primaire gebruik voor het hosten van uitgaande cmdlet zijn gepagineerde gegevens zoals we eerder is besproken.</span><span class="sxs-lookup"><span data-stu-id="18d9a-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="18d9a-125">De volgende opdracht gebruikt Host bijvoorbeeld uitgaande pagina van de uitvoer van de cmdlet Get-opdracht:</span><span class="sxs-lookup"><span data-stu-id="18d9a-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="18d9a-126">U kunt ook de **meer** functie waarmee u kunt paginagegevens.</span><span class="sxs-lookup"><span data-stu-id="18d9a-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="18d9a-127">In Windows PowerShell, **meer** is een functie die worden aangeroepen **uitgaande Host-Wisselgeheugengebruik**.</span><span class="sxs-lookup"><span data-stu-id="18d9a-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="18d9a-128">De volgende opdracht ziet u hoe de **meer** functie op de pagina van de uitvoer van Get-opdracht:</span><span class="sxs-lookup"><span data-stu-id="18d9a-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="18d9a-129">Als u een of meer namen van bestanden als argumenten voor de functie meer opgeeft, wordt de functie de opgegeven bestanden lezen en pagina van de inhoud ervan op de host:</span><span class="sxs-lookup"><span data-stu-id="18d9a-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a><span data-ttu-id="18d9a-130">Uitvoer verwijderen (uitgaande Null)</span><span class="sxs-lookup"><span data-stu-id="18d9a-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="18d9a-131">De **uitgaande Null** cmdlet is ontworpen om onmiddellijk negeren invoer wordt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="18d9a-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="18d9a-132">Dit is handig voor het verwijderen van onnodige gegevens die u als een neveneffect krijgt van het uitvoeren van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="18d9a-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="18d9a-133">Wanneer Typ de volgende opdracht uit, er iets terug vanaf de opdrachtregel:</span><span class="sxs-lookup"><span data-stu-id="18d9a-133">When type the following command, you do not get anything back from the command:</span></span>

```powershell
Get-Command | Out-Null
```

<span data-ttu-id="18d9a-134">De **uitgaande Null** cmdlet foutuitvoer komt niet te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="18d9a-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="18d9a-135">Bijvoorbeeld, als u de volgende opdracht invoert, een bericht weergegeven waarin wordt gemeld dat Windows PowerShell-Is-NotACommand' wordt niet herkend:</span><span class="sxs-lookup"><span data-stu-id="18d9a-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a><span data-ttu-id="18d9a-136">Gegevens voor afdrukken (Out-Printer)</span><span class="sxs-lookup"><span data-stu-id="18d9a-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="18d9a-137">U kunt gegevens afdrukken met behulp van de **Out-Printer** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="18d9a-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="18d9a-138">De **Out-Printer** cmdlet wordt de standaardprinter gebruiken als u de naam van een printer niet opgeeft.</span><span class="sxs-lookup"><span data-stu-id="18d9a-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="18d9a-139">U kunt een printer op basis van Windows gebruiken door de weergavenaam op te geven.</span><span class="sxs-lookup"><span data-stu-id="18d9a-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="18d9a-140">Er is niet nodig voor elk soort printer poorttoewijzing of zelfs een echt fysiek printer.</span><span class="sxs-lookup"><span data-stu-id="18d9a-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="18d9a-141">Bijvoorbeeld, als u de Microsoft Office-document replicatiehulpprogramma's geïnstalleerd hebt, kunt u de gegevens verzenden naar een afbeeldingbestand door te typen:</span><span class="sxs-lookup"><span data-stu-id="18d9a-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a><span data-ttu-id="18d9a-142">Opslaan van gegevens (out-File)</span><span class="sxs-lookup"><span data-stu-id="18d9a-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="18d9a-143">U kunt uitvoer ook verzenden naar een bestand in plaats van het consolevenster met behulp van de **out-File** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="18d9a-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="18d9a-144">De volgende opdrachtregel stuurt een lijst van processen naar het bestand **C:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="18d9a-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="18d9a-145">De resultaten van het gebruik van de **out-File** cmdlet mogelijk niet wat u verwacht als u worden gebruikt voor omleiding van traditionele uitvoer.</span><span class="sxs-lookup"><span data-stu-id="18d9a-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="18d9a-146">Voor meer informatie over het gedrag, moet u op de hoogte van de context waarin de **out-File** cmdlet werkt.</span><span class="sxs-lookup"><span data-stu-id="18d9a-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="18d9a-147">Standaard de **out-File** met de cmdlet maakt een Unicode-bestand.</span><span class="sxs-lookup"><span data-stu-id="18d9a-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="18d9a-148">Dit is de aanbevolen standaardwaarde op de lange termijn, maar dit betekent dat hulpprogramma's die u kunt ASCII-bestanden verwachten niet goed met de indeling van de standaard-uitvoer werken wordt.</span><span class="sxs-lookup"><span data-stu-id="18d9a-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="18d9a-149">U kunt de standaarduitvoerindeling op ASCII wijzigen met behulp van de **Encoding** parameter:</span><span class="sxs-lookup"><span data-stu-id="18d9a-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="18d9a-150">**Out-File** indelingen bestandsinhoud zodat het eruitziet als console-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="18d9a-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="18d9a-151">Dit zorgt ervoor dat de uitvoer moet worden afgekapt, net zoals het in een consolevenster weergegeven in de meeste gevallen.</span><span class="sxs-lookup"><span data-stu-id="18d9a-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="18d9a-152">Bijvoorbeeld, als u de volgende opdracht uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="18d9a-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="18d9a-153">De uitvoer ziet er als volgt:</span><span class="sxs-lookup"><span data-stu-id="18d9a-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="18d9a-154">Als u uitvoer die niet regel terugloopt hoeft zodat deze overeenkomen met de schermbreedte, kunt u de **breedte** parameter opgeven voor lijnbreedte.</span><span class="sxs-lookup"><span data-stu-id="18d9a-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="18d9a-155">Omdat **breedte** is een 32-bits geheel getal-parameter, de maximale waarde kan hebben is 2147483647.</span><span class="sxs-lookup"><span data-stu-id="18d9a-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="18d9a-156">Typ het volgende om in te stellen van de breedte van de aan deze maximumwaarde:</span><span class="sxs-lookup"><span data-stu-id="18d9a-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="18d9a-157">De **out-File** cmdlet is vooral nuttig zijn wanneer u opslaan uitvoer wilt zoals deze zou hebben weergegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="18d9a-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="18d9a-158">Voor betere controle over de indeling van uitvoer moet u meer geavanceerde hulpprogramma's.</span><span class="sxs-lookup"><span data-stu-id="18d9a-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="18d9a-159">We kijken die in het volgende hoofdstuk, samen met details over het bewerken van het object.</span><span class="sxs-lookup"><span data-stu-id="18d9a-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>
