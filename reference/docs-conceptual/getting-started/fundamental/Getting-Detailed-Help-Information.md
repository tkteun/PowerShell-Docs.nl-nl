---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Gedetailleerde Help-informatie ophalen
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: c786ce089073abccdf186dc1d9e8ee383f83655d
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/31/2017
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="e2807-103">Gedetailleerde Help-informatie ophalen</span><span class="sxs-lookup"><span data-stu-id="e2807-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="e2807-104">Windows PowerShell bevat gedetailleerde Help-onderwerpen waarin wordt uitgelegd concepten voor Windows PowerShell en de Windows PowerShell-taal.</span><span class="sxs-lookup"><span data-stu-id="e2807-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="e2807-105">Er zijn ook Help-onderwerpen voor elke cmdlet en de provider en Help-onderwerpen voor veel functies en scripts.</span><span class="sxs-lookup"><span data-stu-id="e2807-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="e2807-106">U kunt de meest recente versies van de volgende onderwerpen in de Microsoft TechNet Library weergeven of deze Help-onderwerpen bij de opdrachtprompt weer.</span><span class="sxs-lookup"><span data-stu-id="e2807-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="e2807-107">Veel programma's die als host fungeren van Windows PowerShell, zoals Windows PowerShell Integrated Scripting Environment, bieden extra hulp-functies, zoals contextgevoelige Help en gecompileerde Help-bestand (.chm).</span><span class="sxs-lookup"><span data-stu-id="e2807-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="e2807-108">Help bij Cmdlets voor ophalen</span><span class="sxs-lookup"><span data-stu-id="e2807-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="e2807-109">Als u Help-informatie over Windows PowerShell-cmdlets, gebruikt de [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e2807-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="e2807-110">Als u bijvoorbeeld ondersteuning voor de [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="e2807-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="e2807-111">of</span><span class="sxs-lookup"><span data-stu-id="e2807-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="e2807-112">U kunt zelfs Help-informatie ophalen over de cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e2807-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="e2807-113">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e2807-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="e2807-114">Als u een lijst met de cmdlet Help-onderwerpen in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="e2807-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="e2807-115">Gebruiken om een pagina te openen van elke Help-onderwerp op een tijdstip, de **help** functie of de alias **man**.</span><span class="sxs-lookup"><span data-stu-id="e2807-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="e2807-116">Typ bijvoorbeeld als Help wilt weergeven voor de cmdlet Get-ChildItem,</span><span class="sxs-lookup"><span data-stu-id="e2807-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="e2807-117">of</span><span class="sxs-lookup"><span data-stu-id="e2807-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="e2807-118">Gedetailleerde informatie over een cmdlet, een functie of een script, met inbegrip van beschrijvingen van de parameters en voorbeelden van het gebruik ervan, gebruiken de *gedetailleerd* parameter van de cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e2807-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="e2807-119">Bijvoorbeeld, als u gedetailleerde informatie over de cmdlet Get-ChildItem, typt u:</span><span class="sxs-lookup"><span data-stu-id="e2807-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="e2807-120">U kunt alle inhoud weergeven in het Help-onderwerp gebruiken de *volledige* parameter van de cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e2807-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="e2807-121">Bijvoorbeeld, als u wilt weergeven van alle inhoud in de Help-onderwerp voor de cmdlet Get-ChildItem, typt u:</span><span class="sxs-lookup"><span data-stu-id="e2807-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="e2807-122">Gedetailleerde ophalen Help-informatie over de parameters van een cmdlet, gebruik de *Parameter* parameter van de cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e2807-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="e2807-123">Bijvoorbeeld, om op te halen gedetailleerde Help voor alle parameters van de cmdlet Get-ChildItem, type:</span><span class="sxs-lookup"><span data-stu-id="e2807-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="e2807-124">Gebruikt u alleen de voorbeelden in een Help-onderwerp weergeven door de *voorbeeld* parameter van de Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e2807-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="e2807-125">Typ bijvoorbeeld het volgende zodat alleen de voorbeelden in het Help-onderwerp voor de cmdlet Get-ChildItem:</span><span class="sxs-lookup"><span data-stu-id="e2807-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="e2807-126">Zie voor meer informatie over het schrijven van Help-onderwerpen voor de cmdlets die u schrijft [schrijven Cmdlet helpen](https://go.microsoft.com/fwlink/?LinkID=123415) in de MSDN-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="e2807-126">For information about how to write Help topics for the cmdlets that you write, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="e2807-127">Conceptuele Help opvragen</span><span class="sxs-lookup"><span data-stu-id="e2807-127">Getting Conceptual Help</span></span>
<span data-ttu-id="e2807-128">De cmdlet Get-Help bevat ook informatie over conceptuele onderwerpen in Windows PowerShell, met inbegrip van onderwerpen over de Windows PowerShell-taal.</span><span class="sxs-lookup"><span data-stu-id="e2807-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="e2807-129">Conceptuele Help-onderwerpen beginnen met het voorvoegsel 'about_', zoals about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="e2807-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="e2807-130">(De naam van het conceptuele onderwerp moet worden ingevoerd in het Engels zelfs op niet-Engelse versies van Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="e2807-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="e2807-131">Als een lijst met algemene onderwerpen weergeven, typt u:</span><span class="sxs-lookup"><span data-stu-id="e2807-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="e2807-132">Als u wilt een bepaalde Help-onderwerp weergeven, typt u bijvoorbeeld de naam van het onderwerp:</span><span class="sxs-lookup"><span data-stu-id="e2807-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="e2807-133">De parameters van Get-Help, zoals *gedetailleerd*, *Parameter*, en *voorbeelden*, hebben geen effect op de weergave van de conceptuele Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="e2807-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="e2807-134">Help-informatie over Providers</span><span class="sxs-lookup"><span data-stu-id="e2807-134">Getting Help About Providers</span></span>
<span data-ttu-id="e2807-135">De cmdlet Get-Help bevat informatie over Windows PowerShell-providers.</span><span class="sxs-lookup"><span data-stu-id="e2807-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="e2807-136">Als u de Help voor een provider, typ 'Get-Help"gevolgd door de naam van de provider.</span><span class="sxs-lookup"><span data-stu-id="e2807-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="e2807-137">Bijvoorbeeld, als u de Help voor de Register-provider, typt u:</span><span class="sxs-lookup"><span data-stu-id="e2807-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="e2807-138">Als u een lijst van alle provider Help-onderwerpen in uw sessie, typt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="e2807-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="e2807-139">De parameters van Get-Help, zoals *gedetailleerd*, *Parameter*, en *voorbeelden*, hebben geen effect op de weergave van de provider Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="e2807-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="e2807-140">Help opvragen over Scripts en functies</span><span class="sxs-lookup"><span data-stu-id="e2807-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="e2807-141">Veel scripts en functies in Windows PowerShell beschikken over de Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="e2807-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="e2807-142">Gebruik de cmdlet Get-Help om Help-onderwerpen voor scripts en functies weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e2807-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="e2807-143">Als u de Help voor een functie, typt u 'get-help"gevolgd door de naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="e2807-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="e2807-144">Bijvoorbeeld, als u de Help voor de functie Disable-PSRemoting, typt u:</span><span class="sxs-lookup"><span data-stu-id="e2807-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="e2807-145">Typ de volledig gekwalificeerde pad naar het scriptbestand de Help-informatie voor een script.</span><span class="sxs-lookup"><span data-stu-id="e2807-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="e2807-146">Als het script in een pad dat wordt vermeld in de omgevingsvariabele Path is, kunt u het pad van de opdracht weglaten.</span><span class="sxs-lookup"><span data-stu-id="e2807-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="e2807-147">Bijvoorbeeld, als er een script met de naam 'TestScript.ps1' in uw C:\\PS-Test directory, zodat het Help-onderwerp voor het script, type:</span><span class="sxs-lookup"><span data-stu-id="e2807-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="e2807-148">De parameters die zijn ontworpen voor het weergeven van de cmdlet Help zoals *gedetailleerd*, *volledige*, *voorbeelden*, en *Parameter*, voor script Help-informatie en hulp nodig hebt, te werken.</span><span class="sxs-lookup"><span data-stu-id="e2807-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="e2807-149">Echter, wanneer u alle Help weergeven door in te voeren ' get-help \*', Help voor functies en scripts niet wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="e2807-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="e2807-150">Zie voor meer informatie over het schrijven van Help-onderwerpen voor de functies en scripts [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), en [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span><span class="sxs-lookup"><span data-stu-id="e2807-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="e2807-151">Help-informatie Online</span><span class="sxs-lookup"><span data-stu-id="e2807-151">Getting Help Online</span></span>
<span data-ttu-id="e2807-152">Als u met het Internet verbonden bent, is een van de aanbevolen manieren om hulp te krijgen om de Help-onderwerpen online weer te geven.</span><span class="sxs-lookup"><span data-stu-id="e2807-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="e2807-153">Omdat online-onderwerpen gemakkelijk om bij te werken, zijn ze waarschijnlijk de meest actuele informatie bieden.</span><span class="sxs-lookup"><span data-stu-id="e2807-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="e2807-154">Als u online Help, probeert de *Online* parameter van de cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e2807-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="e2807-155">De *Online* parameter van de Get-Help cmdlet werkt alleen voor cmdlet Help Help functioneren en Help script.</span><span class="sxs-lookup"><span data-stu-id="e2807-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="e2807-156">U kunt geen gebruiken de *Online* parameter met de conceptuele (over) onderwerpen of provider Help-onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="e2807-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="e2807-157">Bovendien omdat deze functie optioneel is, werkt het niet voor elke cmdlet, een functie of een script Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="e2807-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="e2807-158">Echter alle Help-onderwerpen die worden geleverd met Windows PowerShell, met inbegrip van provider Help en conceptuele (over) Help-onderwerpen zijn online beschikbaar de [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) sectie van de Microsoft TechNet Library.</span><span class="sxs-lookup"><span data-stu-id="e2807-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="e2807-159">Gebruik de *Online* parameter van de cmdlet Get-Help, gebruik de volgende notatie voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="e2807-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="e2807-160">Bijvoorbeeld, als u de online versie van het Help-onderwerp over de cmdlet Get-ChildItem, typt u:</span><span class="sxs-lookup"><span data-stu-id="e2807-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="e2807-161">Als een onlineversie van het Help-onderwerp beschikbaar is, wordt deze in de standaardbrowser geopend.</span><span class="sxs-lookup"><span data-stu-id="e2807-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="e2807-162">Als de online-Help wordt ondersteund voor een Help-onderwerp, kunt u ook het internetadres (URL) van het Help-onderwerp weergeven.</span><span class="sxs-lookup"><span data-stu-id="e2807-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="e2807-163">Het internetadres wordt weergegeven in de sectie Verwante koppelingen van een Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="e2807-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="e2807-164">Bijvoorbeeld, als u wilt zien van de URL voor de online versie van de cmdlet Add-Computer, typt u:</span><span class="sxs-lookup"><span data-stu-id="e2807-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="e2807-165">De eerste regel in het gedeelte Verwante koppelingen van het onderwerp worden hieronder weergegeven.</span><span class="sxs-lookup"><span data-stu-id="e2807-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="e2807-166">Zie voor meer informatie over het online ondersteuning bieden voor uw Help-onderwerpen [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), en zien [schrijven Cmdlet helpen](https://go.microsoft.com/fwlink/?LinkID=123415) in de MSDN-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="e2807-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2807-167">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e2807-167">See Also</span></span>
- <span data-ttu-id="e2807-168">[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)</span><span class="sxs-lookup"><span data-stu-id="e2807-168">[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)</span></span>
- [<span data-ttu-id="e2807-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="e2807-169">about_Scripts</span></span>](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="e2807-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="e2807-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- <span data-ttu-id="e2807-171">[Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span><span class="sxs-lookup"><span data-stu-id="e2807-171">[Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span></span>

