---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Inzicht in de Windows PowerShell-Pipeline
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 6d152e52d2fcfb9dd592eb9ac40500615f2186cb
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="understanding-the-windows-powershell-pipeline"></a><span data-ttu-id="c3c94-103">Inzicht in de Windows PowerShell-Pipeline</span><span class="sxs-lookup"><span data-stu-id="c3c94-103">Understanding the Windows PowerShell Pipeline</span></span>
<span data-ttu-id="c3c94-104">Piping werkt vrijwel overal in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3c94-104">Piping works virtually everywhere in Windows PowerShell.</span></span> <span data-ttu-id="c3c94-105">Hoewel u tekst op het scherm ziet, wordt in Windows PowerShell tekst tussen opdrachten niet pipe.</span><span class="sxs-lookup"><span data-stu-id="c3c94-105">Although you see text on the screen, Windows PowerShell does not pipe text between commands.</span></span> <span data-ttu-id="c3c94-106">In plaats daarvan doorgesluisd deze objecten.</span><span class="sxs-lookup"><span data-stu-id="c3c94-106">Instead, it pipes objects.</span></span>

<span data-ttu-id="c3c94-107">De notatie die wordt gebruikt voor pijplijnen is vergelijkbaar met die in andere houders gebruikt, dus op het eerste gezicht het niet altijd duidelijk is Windows PowerShell introduceert een nieuwe.</span><span class="sxs-lookup"><span data-stu-id="c3c94-107">The notation used for pipelines is similar to that used in other shells, so at first glance, it may not be apparent that Windows PowerShell introduces something new.</span></span> <span data-ttu-id="c3c94-108">Als u bijvoorbeeld de **uitgaande Host** cmdlet om af te dwingen van een weergave per pagina van de uitvoer van een andere opdracht, de uitvoer ziet er net zoals de normale tekst die wordt weergegeven op het scherm, opgedeeld in pagina's:</span><span class="sxs-lookup"><span data-stu-id="c3c94-108">For example, if you use the **Out-Host** cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="c3c94-109">De Out-Host-paginering opdracht is een nuttig pipeline-element wanneer u langdurige uitvoer die u wilt weergeven aan de trage kant.</span><span class="sxs-lookup"><span data-stu-id="c3c94-109">The Out-Host -Paging command is a useful pipeline element whenever you have lengthy output that you would like to display slowly.</span></span> <span data-ttu-id="c3c94-110">Dit is vooral nuttig als de bewerking het CPU-intensief is.</span><span class="sxs-lookup"><span data-stu-id="c3c94-110">It is especially useful if the operation is very CPU-intensive.</span></span> <span data-ttu-id="c3c94-111">Omdat de verwerking wordt overgebracht naar de cmdlet uitgaande Host wanneer er een volledige pagina Gereed om weer te geven, cmdlets die worden voorafgegaan door het in de pijplijn bewerking onderbroken totdat de volgende pagina van de uitvoer beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="c3c94-111">Because processing is transferred to the Out-Host cmdlet when it has a complete page ready to display, cmdlets that precede it in the pipeline halt operation until the next page of output is available.</span></span> <span data-ttu-id="c3c94-112">U kunt dit zien als u Windows Taakbeheer om te controleren van de CPU en geheugen gebruikt door Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3c94-112">You can see this if you use the Windows Task Manager to monitor CPU and memory use by Windows PowerShell.</span></span>

<span data-ttu-id="c3c94-113">Voer de volgende opdracht: **Get-ChildItem C:\\Windows-Recurse**.</span><span class="sxs-lookup"><span data-stu-id="c3c94-113">Run the following command: **Get-ChildItem C:\\Windows -Recurse**.</span></span> <span data-ttu-id="c3c94-114">Vergelijk de CPU- en geheugengebruik op deze opdracht: **Get-ChildItem C:\\Windows-Recurse | Uitgaande Host-Paging**.</span><span class="sxs-lookup"><span data-stu-id="c3c94-114">Compare the CPU and memory usage to this command: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span></span> <span data-ttu-id="c3c94-115">Wat u ziet in het scherm is tekst, maar dat is omdat het is nodig om objecten te vertegenwoordigen als tekst in een consolevenster.</span><span class="sxs-lookup"><span data-stu-id="c3c94-115">What you see on the screen is text, but that is because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="c3c94-116">Dit is alleen een weergave van wat er echt dat op in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3c94-116">This is just a representation of what is really going on inside Windows PowerShell.</span></span> <span data-ttu-id="c3c94-117">Bijvoorbeeld, u kunt de cmdlet Get-locatie.</span><span class="sxs-lookup"><span data-stu-id="c3c94-117">For example, consider the Get-Location cmdlet.</span></span> <span data-ttu-id="c3c94-118">Als u typt **Get-Location** terwijl uw huidige locatie de hoofdmap van station C is, ziet u de volgende uitvoer:</span><span class="sxs-lookup"><span data-stu-id="c3c94-118">If you type **Get-Location** while your current location is the root of the C drive, you would see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="c3c94-119">Als u Windows PowerShell gebruikt in een pijplijn tekst, waarop u een opdracht zoals **Get-Location | Uitgaande Host**, zou doorgeven van **Get-Location** naar **uitgaande Host** een reeks tekens in de volgorde waarin ze worden weergegeven op het scherm.</span><span class="sxs-lookup"><span data-stu-id="c3c94-119">If Windows PowerShell pipelined text, issuing a command such as **Get-Location | Out-Host**, would pass from **Get-Location** to **Out-Host** a set of characters in the order they are displayed onscreen.</span></span> <span data-ttu-id="c3c94-120">Met andere woorden, als u de informatie van de kop negeren **uitgaande Host** zou ontvangen van het teken '**C'**, klikt u vervolgens het teken '**:'**, klikt u vervolgens het teken ' **\\'**.</span><span class="sxs-lookup"><span data-stu-id="c3c94-120">In other words, if you were to ignore the heading information, **Out-Host** would first receive the character '**C'**, then the character '**:'**, then the character '**\\'**.</span></span> <span data-ttu-id="c3c94-121">De **uitgaande Host** cmdlet kan niet worden bepaald welke betekenis koppelen aan de uitvoer van de tekens door de **Get-Location** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c3c94-121">The **Out-Host** cmdlet could not determine what meaning to associate with the characters output by the **Get-Location** cmdlet.</span></span>

<span data-ttu-id="c3c94-122">In plaats van via SMS-opdrachten in een pijplijn te laten communiceren, objecten maakt gebruik van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3c94-122">Instead of using text to let commands in a pipeline communicate, Windows PowerShell uses objects.</span></span> <span data-ttu-id="c3c94-123">Vanuit het oogpunt van een gebruiker, objecten verwante informatie in een formulier dat het makkelijker wordt om te bewerken van de gegevens als eenheid van het pakket en extraheren van specifieke items die u nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="c3c94-123">From the standpoint of a user, objects package related information into a form that makes it easier to manipulate the information as a unit, and extract specific items that you need.</span></span>

<span data-ttu-id="c3c94-124">De **Get-Location** opdracht geen waarde retourneert tekst met het huidige pad.</span><span class="sxs-lookup"><span data-stu-id="c3c94-124">The **Get-Location** command does not return text that contains the current path.</span></span> <span data-ttu-id="c3c94-125">Deze retourneert een reeks informatie aangeroepen een **PathInfo** -object dat het huidige pad samen met andere informatie bevat.</span><span class="sxs-lookup"><span data-stu-id="c3c94-125">It returns a package of information called a **PathInfo** object that contains the current path along with some other information.</span></span> <span data-ttu-id="c3c94-126">De **uitgaande Host** cmdlet vervolgens verzendt **PathInfo** object naar het scherm en Windows PowerShell beslist wat gegevens om weer te geven en hoe weer te geven op basis van de regels voor opmaak.</span><span class="sxs-lookup"><span data-stu-id="c3c94-126">The **Out-Host** cmdlet then sends this **PathInfo** object to the screen, and Windows PowerShell decides what information to display and how to display it based on its formatting rules.</span></span>

<span data-ttu-id="c3c94-127">In feite de informatie van de kop uitvoeren door de **Get-Location** cmdlet alleen aan het einde van het proces wordt toegevoegd als onderdeel van het proces van de opmaak van de gegevens worden weergegeven op het scherm.</span><span class="sxs-lookup"><span data-stu-id="c3c94-127">In fact, the heading information output by the **Get-Location** cmdlet is added only at the end of the process, as part of the process of formatting the data for onscreen display.</span></span> <span data-ttu-id="c3c94-128">Wat u ziet op het scherm wordt een samenvatting van gegevens en niet een volledige weergave van het object uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c3c94-128">What you see onscreen is a summary of information, and not a complete representation of the output object.</span></span>

<span data-ttu-id="c3c94-129">Gezien het feit dat er mogelijk meer informatie de uitvoer van een Windows PowerShell opdracht dan zien we in het consolevenster weergegeven hoe kunt u de niet-zichtbare elementen ophalen?</span><span class="sxs-lookup"><span data-stu-id="c3c94-129">Given that there may be more information output from a Windows PowerShell command than what we see displayed in the console window, how can you retrieve the non-visible elements?</span></span> <span data-ttu-id="c3c94-130">Hoe bekijkt u de extra gegevens?</span><span class="sxs-lookup"><span data-stu-id="c3c94-130">How do you view the extra data?</span></span> <span data-ttu-id="c3c94-131">En wat gebeurt er als u wilt weergeven van de gegevens in een indeling die anders dan een Windows PowerShell normaal gesproken gebruikt?</span><span class="sxs-lookup"><span data-stu-id="c3c94-131">And what if you want to view the data in a format different than the one Windows PowerShell normally uses?</span></span>

<span data-ttu-id="c3c94-132">De rest van dit hoofdstuk wordt beschreven hoe u kunt detecteren de structuur van de specifieke Windows PowerShell-objecten selecteren van specifieke items en opmaak ze gemakkelijker weergegeven en hoe deze gegevens worden verzonden naar alternatieve uitvoerlocaties, zoals bestanden en printers.</span><span class="sxs-lookup"><span data-stu-id="c3c94-132">The rest of this chapter discusses how you can discover the structure of specific Windows PowerShell objects, selecting specific items and formatting them for easier display, and how to send this information to alternative output locations such as files and printers.</span></span>

