---
ms.date: 08/27/2018
keywords: Power shell, cmdlet
title: Gedetailleerde Help-informatie verkrijgen
ms.openlocfilehash: e722eb8a0ca13e3d2de864314775a0a9fa578390
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417657"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="f6e26-103">Gedetailleerde Help-informatie verkrijgen</span><span class="sxs-lookup"><span data-stu-id="f6e26-103">Getting detailed help information</span></span>

<span data-ttu-id="f6e26-104">Power shell bevat gedetailleerde Help-artikelen waarin Power shell-concepten en de Power shell-taal worden uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="f6e26-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="f6e26-105">Er zijn ook Help-artikelen voor elke cmdlet en provider en voor veel functies en scripts.</span><span class="sxs-lookup"><span data-stu-id="f6e26-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="f6e26-106">U kunt deze Help-artikelen weer geven via de opdracht prompt of de meest recent bijgewerkte versies van deze artikelen weer geven in de [Power shell](/powershell/scripting/overview) -documentatie online.</span><span class="sxs-lookup"><span data-stu-id="f6e26-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="f6e26-107">Hulp krijgen voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="f6e26-107">Getting help for cmdlets</span></span>

<span data-ttu-id="f6e26-108">Gebruik de cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) voor meer informatie over Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="f6e26-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="f6e26-109">Als u bijvoorbeeld hulp wilt krijgen voor de cmdlet `Get-ChildItem`, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="f6e26-110">of</span><span class="sxs-lookup"><span data-stu-id="f6e26-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="f6e26-111">U kunt zelfs hulp krijgen bij de cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="f6e26-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="f6e26-112">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f6e26-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="f6e26-113">Als u een lijst wilt weer geven met alle Help-artikelen over cmdlets in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="f6e26-114">Als u per keer één pagina van elk Help-artikel wilt weer geven, gebruikt u de functie `help` of de alias `man`.</span><span class="sxs-lookup"><span data-stu-id="f6e26-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="f6e26-115">Als u bijvoorbeeld de Help voor de cmdlet `Get-ChildItem` wilt weer geven, typt u</span><span class="sxs-lookup"><span data-stu-id="f6e26-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="f6e26-116">of</span><span class="sxs-lookup"><span data-stu-id="f6e26-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="f6e26-117">Als u gedetailleerde informatie wilt weer geven, gebruikt u de para meter **Details** van de cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="f6e26-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="f6e26-118">Als u bijvoorbeeld gedetailleerde informatie over de cmdlet `Get-ChildItem` wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="f6e26-119">Als u alle inhoud in het Help-artikel wilt weer geven, gebruikt u de **volledige** para meter van de cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="f6e26-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="f6e26-120">Als u bijvoorbeeld alle inhoud wilt weer geven in het Help-artikel voor de cmdlet `Get-ChildItem`, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="f6e26-121">Voor gedetailleerde informatie over de para meters van een cmdlet gebruikt u de para meter **parameter** van de cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="f6e26-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="f6e26-122">Als u bijvoorbeeld gedetailleerde Help wilt ophalen voor alle para meters van de cmdlet `Get-ChildItem`, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="f6e26-123">Als u alleen de voor beelden in een Help-artikel wilt weer geven, gebruikt u de para meter **voor beelden** van de `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="f6e26-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="f6e26-124">Als u bijvoorbeeld alleen de voor beelden in het Help-artikel voor de cmdlet `Get-ChildItem` wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="f6e26-125">Zie de [Help bij cmdlet schrijven](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)voor meer informatie over het schrijven van Help-artikelen voor de cmdlets die u schrijft.</span><span class="sxs-lookup"><span data-stu-id="f6e26-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="f6e26-126">Conceptuele hulp krijgen</span><span class="sxs-lookup"><span data-stu-id="f6e26-126">Getting conceptual help</span></span>

<span data-ttu-id="f6e26-127">De cmdlet `Get-Help` bevat ook informatie over conceptuele artikelen in Power shell, inclusief artikelen over de Power shell-taal.</span><span class="sxs-lookup"><span data-stu-id="f6e26-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="f6e26-128">Conceptuele Help-artikelen beginnen met het voor voegsel ' about_ ', zoals about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="f6e26-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="f6e26-129">(De naam van het conceptuele artikel moet worden ingevoerd in het Engels, zelfs op niet-Engelse versies van Power shell.)</span><span class="sxs-lookup"><span data-stu-id="f6e26-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="f6e26-130">Als u een lijst met conceptuele artikelen wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="f6e26-131">Als u een bepaald Help-artikel wilt weer geven, typt u de artikel naam, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f6e26-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="f6e26-132">De para meters van `Get-Help`, zoals **gedetailleerde**, **para meters**en **voor beelden**, hebben geen effect op de weer gave van conceptuele Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="f6e26-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="f6e26-133">Hulp krijgen bij providers</span><span class="sxs-lookup"><span data-stu-id="f6e26-133">Getting help about providers</span></span>

<span data-ttu-id="f6e26-134">De cmdlet `Get-Help` geeft informatie weer over Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="f6e26-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="f6e26-135">Als u hulp wilt krijgen voor een provider, typt u `Get-Help` gevolgd door de naam van de provider.</span><span class="sxs-lookup"><span data-stu-id="f6e26-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="f6e26-136">Als u bijvoorbeeld hulp wilt krijgen voor de register provider, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="f6e26-137">Als u een lijst wilt weer geven met alle Help-artikelen van de provider in uw sessie, typt u</span><span class="sxs-lookup"><span data-stu-id="f6e26-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="f6e26-138">De para meters van `Get-Help`, zoals **gedetailleerde**, **para meters**en **voor beelden**, hebben geen invloed op de weer gave van de Help-artikelen van de provider.</span><span class="sxs-lookup"><span data-stu-id="f6e26-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="f6e26-139">Hulp krijgen over scripts en functies</span><span class="sxs-lookup"><span data-stu-id="f6e26-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="f6e26-140">Veel scripts en functies in Power Shell hebben Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="f6e26-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="f6e26-141">Gebruik de cmdlet `Get-Help` om de Help-artikelen voor scripts en functies weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f6e26-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="f6e26-142">Als u de Help voor een functie wilt weer geven, typt u `Get-Help` gevolgd door de naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="f6e26-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="f6e26-143">Als u bijvoorbeeld hulp wilt krijgen voor de functie `Disable-PSRemoting`, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="f6e26-144">Als u de Help voor een script wilt weer geven, typt u het pad naar het script bestand.</span><span class="sxs-lookup"><span data-stu-id="f6e26-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="f6e26-145">Als het script zich niet bevindt in een pad dat wordt vermeld in de omgevings variabele PATH, moet u het volledig gekwalificeerde pad gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f6e26-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="f6e26-146">Als u bijvoorbeeld een script met de naam ' TestScript. ps1 ' in de map C:\\PS-test, om het Help-artikel voor het script weer te geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="f6e26-147">De para meters die zijn ontworpen voor het weer geven van cmdlet Help, werken ook voor de Help van script en functie.</span><span class="sxs-lookup"><span data-stu-id="f6e26-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="f6e26-148">Help voor functies en scripts wordt echter niet weer gegeven wanneer u `Get-Help *`uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f6e26-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="f6e26-149">Raadpleeg de volgende artikelen voor informatie over het schrijven van Help-artikelen voor uw functies en scripts:</span><span class="sxs-lookup"><span data-stu-id="f6e26-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="f6e26-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="f6e26-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="f6e26-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="f6e26-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="f6e26-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="f6e26-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="f6e26-153">Online hulp krijgen</span><span class="sxs-lookup"><span data-stu-id="f6e26-153">Getting help online</span></span>

<span data-ttu-id="f6e26-154">De Help-artikelen online bekijken is een van de beste manieren om hulp te krijgen.</span><span class="sxs-lookup"><span data-stu-id="f6e26-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="f6e26-155">Online artikelen kunnen gemakkelijker worden bijgewerkt en bieden de meest actuele inhoud.</span><span class="sxs-lookup"><span data-stu-id="f6e26-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="f6e26-156">Gebruik de para meter **online** van de cmdlet `Get-Help` om online hulp te krijgen.</span><span class="sxs-lookup"><span data-stu-id="f6e26-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="f6e26-157">Alle Help-artikelen die worden geleverd met Power shell, inclusief Help-artikelen voor de provider Help en conceptuele informatie, zijn online beschikbaar in de [Power shell](/powershell/scripting/powershell-scripting) -documentatie.</span><span class="sxs-lookup"><span data-stu-id="f6e26-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="f6e26-158">U kunt de para meter **online** niet gebruiken met de conceptuele (about_\*) of de Help-artikelen van de provider.</span><span class="sxs-lookup"><span data-stu-id="f6e26-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="f6e26-159">Online-Help is optioneel en werkt daarom niet voor elke cmdlet, functie of script.</span><span class="sxs-lookup"><span data-stu-id="f6e26-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="f6e26-160">Als u bijvoorbeeld de online versie van het Help-artikel over de cmdlet `Get-ChildItem` wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="f6e26-161">Power shell opent het artikel in de standaard browser.</span><span class="sxs-lookup"><span data-stu-id="f6e26-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="f6e26-162">Als online-Help wordt ondersteund voor een Help-artikel, kunt u ook de URL van het Help-artikel weer geven.</span><span class="sxs-lookup"><span data-stu-id="f6e26-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="f6e26-163">De URL wordt weer gegeven in de sectie verwante koppelingen van een Help-artikel.</span><span class="sxs-lookup"><span data-stu-id="f6e26-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="f6e26-164">Als u bijvoorbeeld de URL voor de online versie van de cmdlet Add-computer wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="f6e26-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="f6e26-165">De eerste regel in de sectie verwante koppelingen van het artikel wordt hieronder weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f6e26-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: https://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="f6e26-166">Zie [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)voor meer informatie over het bieden van online ondersteuning voor uw Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="f6e26-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6e26-167">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f6e26-167">See also</span></span>

- [<span data-ttu-id="f6e26-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="f6e26-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="f6e26-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="f6e26-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="f6e26-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="f6e26-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="f6e26-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="f6e26-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
