---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gegevens omleiden met Out-cmdlets
description: In dit artikel wordt beschreven hoe u de-cmdlets gebruikt die uitvoer in Power shell beheren.
ms.openlocfilehash: 3a9e3b1ac06f5be4e6f3bbc52a15c4afb5b12cef
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500212"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="c9ab6-104">Gegevens omleiden met out-\*-cmdlets</span><span class="sxs-lookup"><span data-stu-id="c9ab6-104">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="c9ab6-105">Windows Power shell biedt verschillende cmdlets waarmee u gegevens uitvoer rechtstreeks kunt beheren.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-105">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="c9ab6-106">Deze cmdlets delen twee belang rijke kenmerken.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-106">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="c9ab6-107">Eerst transformeren ze gegevens naar een vorm van tekst.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-107">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="c9ab6-108">Ze doen dit omdat ze de gegevens uitvoeren naar systeem onderdelen waarvoor tekst invoer is vereist.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-108">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="c9ab6-109">Dit betekent dat de objecten als tekst moeten worden aangeduid.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-109">This means they need to represent the objects as text.</span></span> <span data-ttu-id="c9ab6-110">Daarom wordt de tekst opgemaakt zoals deze wordt weer gegeven in het Windows Power shell-console venster.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-110">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="c9ab6-111">Ten tweede gebruiken deze cmdlets het Windows Power shell-werk woord **uit** , omdat ze informatie vanuit Windows Power shell naar een andere locatie verzenden.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-111">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="c9ab6-112">De cmdlet **out-host** is geen uitzonde ring: het venster host wordt weer gegeven buiten Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-112">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="c9ab6-113">Dit is belang rijk omdat wanneer gegevens vanuit Windows Power shell worden verzonden, ze daad werkelijk worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-113">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="c9ab6-114">U kunt dit zien als u probeert een pijp lijn te maken die pagina's met gegevens naar het venster host en vervolgens probeert te Format teren als een lijst, zoals hier wordt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-114">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="c9ab6-115">U kunt de opdracht voor het weer geven van pagina's met proces gegevens in de lijst indeling verwachten.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-115">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="c9ab6-116">In plaats daarvan wordt de standaard lijst in tabel vorm weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-116">Instead, it displays the default tabular list:</span></span>

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

<span data-ttu-id="c9ab6-117">De cmdlet **out-host** verzendt de gegevens rechtstreeks naar de-console, waardoor de opdracht voor het **Format teren** van de lijst nooit wordt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-117">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="c9ab6-118">De juiste manier om deze opdracht te structureren, is door de cmdlet **out-host** aan het einde van de pijp lijn te plaatsen, zoals hieronder wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-118">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="c9ab6-119">Dit zorgt ervoor dat de proces gegevens in een lijst worden opgemaakt voordat ze worden gewisseld en weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-119">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

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

<span data-ttu-id="c9ab6-120">Dit geldt voor alle **out** -cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-120">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="c9ab6-121">Een **out** -cmdlet moet altijd aan het einde van de pijp lijn worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-121">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="c9ab6-122">Alle **out** -cmdlets genereren uitvoer als tekst, met behulp van de opmaak van het console venster, met inbegrip van de limieten voor de regel lengte.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-122">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

## <a name="paging-console-output-out-host"></a><span data-ttu-id="c9ab6-123">Uitvoer van de console pagineren (out-host)</span><span class="sxs-lookup"><span data-stu-id="c9ab6-123">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="c9ab6-124">Standaard worden gegevens door Windows Power shell naar het venster host verzonden. Dit is precies wat de Out-Host-cmdlet doet.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-124">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="c9ab6-125">Het primaire gebruik voor de Out-Host-cmdlet is het pagineren van gegevens zoals eerder is beschreven.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-125">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="c9ab6-126">Met de volgende opdracht wordt bijvoorbeeld Out-Host op pagina de uitvoer van de Get-Command cmdlet:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-126">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="c9ab6-127">U kunt ook de functie **meer** gebruiken voor pagina gegevens.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-127">You can also use the **more** function to page data.</span></span> <span data-ttu-id="c9ab6-128">In Windows Power shell is **meer** een functie waarmee u **out-host-paging**aanroept.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-128">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="c9ab6-129">De volgende opdracht laat zien hoe u met behulp van de functie **meer** op pagina de uitvoer van Get-opdracht kunt gebruiken:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-129">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="c9ab6-130">Als u een of meer bestands namen als argumenten voor de functie meer opneemt, worden de opgegeven bestanden en de inhoud van de functie naar de host gelezen:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-130">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a><span data-ttu-id="c9ab6-131">Uitvoer verwijderen (out-null)</span><span class="sxs-lookup"><span data-stu-id="c9ab6-131">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="c9ab6-132">De **out-null-** cmdlet is ontworpen voor het direct negeren van de invoer die wordt ontvangen.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-132">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="c9ab6-133">Dit is handig voor het verwijderen van overbodige gegevens die u krijgt als een neven effect van het uitvoeren van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-133">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="c9ab6-134">Wanneer u de volgende opdracht typt, haalt u niets terug van de opdracht:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-134">When type the following command, you do not get anything back from the command:</span></span>

```powershell
Get-Command | Out-Null
```

<span data-ttu-id="c9ab6-135">De uitzonderings **-Null** -cmdlet verwijdert geen fout uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-135">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="c9ab6-136">Als u bijvoorbeeld de volgende opdracht opgeeft, wordt er een bericht weer gegeven waarin wordt gemeld dat Windows Power shell ' is-NotACommand ' niet herkent:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-136">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a><span data-ttu-id="c9ab6-137">Gegevens afdrukken (niet-printer)</span><span class="sxs-lookup"><span data-stu-id="c9ab6-137">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="c9ab6-138">U kunt gegevens afdrukken met behulp van de **out-printer-** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-138">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="c9ab6-139">De **out-printer** cmdlet gebruikt uw standaard printer als u geen printer naam opgeeft.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-139">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="c9ab6-140">U kunt elke op Windows gebaseerde printer gebruiken door de bijbehorende weergave naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-140">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="c9ab6-141">Er is geen soort printer poort toewijzing nodig of zelfs een echte fysieke printer.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-141">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="c9ab6-142">Als u bijvoorbeeld de Microsoft Office document imaging-hulpprogram ma's hebt geïnstalleerd, kunt u de gegevens naar een afbeeldings bestand verzenden door het volgende te typen:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-142">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a><span data-ttu-id="c9ab6-143">Gegevens opslaan (out-file)</span><span class="sxs-lookup"><span data-stu-id="c9ab6-143">Saving Data (Out-File)</span></span>

<span data-ttu-id="c9ab6-144">U kunt uitvoer naar een bestand verzenden in plaats van via het console venster met de **out-file-** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-144">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="c9ab6-145">De volgende opdracht regel verzendt een lijst met processen naar het bestand **C: \\ temp \\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-145">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="c9ab6-146">De resultaten van het gebruik van de **out-file** cmdlet zijn mogelijk niet wat u verwacht als u gebruikt voor traditionele uitvoer omleiding.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-146">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="c9ab6-147">Om het gedrag ervan te begrijpen, moet u rekening houden met de context waarin de **out-file-** cmdlet werkt.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-147">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="c9ab6-148">Standaard maakt de cmdlet **out-file** een Unicode-bestand.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-148">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="c9ab6-149">Dit is de beste standaard waarde in de lange uitvoering, maar dit betekent dat de hulpprogram ma's die ASCII-bestanden verwachten, niet goed werken met de standaard uitvoer indeling.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-149">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="c9ab6-150">U kunt de standaard uitvoer indeling wijzigen in ASCII met behulp van de para meter **Encoding** :</span><span class="sxs-lookup"><span data-stu-id="c9ab6-150">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="c9ab6-151">**Out-bestands** indelingen bestands inhoud die eruitziet als console-uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-151">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="c9ab6-152">Dit zorgt ervoor dat de uitvoer wordt afgekapt net zoals deze in de meeste omstandigheden in een console venster wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-152">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="c9ab6-153">Als u bijvoorbeeld de volgende opdracht uitvoert:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-153">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="c9ab6-154">De uitvoer ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-154">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="c9ab6-155">U kunt de para meter **width** gebruiken om de lijn breedte op te geven om de uitvoer op te halen die niet voldoet aan de scherm breedte.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-155">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="c9ab6-156">Omdat **width** een 32-bits integer-para meter is, kan de maximum waarde zijn 2147483647.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-156">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="c9ab6-157">Typ het volgende om de lijn breedte in te stellen op deze maximum waarde:</span><span class="sxs-lookup"><span data-stu-id="c9ab6-157">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="c9ab6-158">De **out-file** cmdlet is het handigst wanneer u de uitvoer wilt opslaan zoals deze zou worden weer gegeven op de-console.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-158">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="c9ab6-159">Voor een nauw keurige controle over de indeling van de uitvoer hebt u meer geavanceerde hulp middelen nodig.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-159">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="c9ab6-160">We kijken naar die in het volgende hoofd stuk, samen met enkele details over het bewerken van objecten.</span><span class="sxs-lookup"><span data-stu-id="c9ab6-160">We will look at those in the next chapter, along with some details about object manipulation.</span></span>
