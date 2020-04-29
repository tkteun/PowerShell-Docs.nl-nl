---
ms.date: 08/27/2018
keywords: Power shell, cmdlet
title: Gedetailleerde Help-informatie verkrijgen
ms.openlocfilehash: e722eb8a0ca13e3d2de864314775a0a9fa578390
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "74417657"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="89b88-103">Gedetailleerde Help-informatie verkrijgen</span><span class="sxs-lookup"><span data-stu-id="89b88-103">Getting detailed help information</span></span>

<span data-ttu-id="89b88-104">Power shell bevat gedetailleerde Help-artikelen waarin Power shell-concepten en de Power shell-taal worden uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="89b88-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="89b88-105">Er zijn ook Help-artikelen voor elke cmdlet en provider en voor veel functies en scripts.</span><span class="sxs-lookup"><span data-stu-id="89b88-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="89b88-106">U kunt deze Help-artikelen weer geven via de opdracht prompt of de meest recent bijgewerkte versies van deze artikelen weer geven in de [Power shell](/powershell/scripting/overview) -documentatie online.</span><span class="sxs-lookup"><span data-stu-id="89b88-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="89b88-107">Hulp krijgen voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="89b88-107">Getting help for cmdlets</span></span>

<span data-ttu-id="89b88-108">Gebruik de cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) voor meer informatie over Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="89b88-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="89b88-109">Als u bijvoorbeeld hulp voor de `Get-ChildItem` cmdlet wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="89b88-110">of</span><span class="sxs-lookup"><span data-stu-id="89b88-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="89b88-111">U kunt zelfs hulp krijgen bij de cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="89b88-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="89b88-112">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="89b88-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="89b88-113">Als u een lijst wilt weer geven met alle Help-artikelen over cmdlets in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="89b88-114">Als u per keer één pagina van elk Help-artikel wilt weer geven `help` , gebruikt u de `man`functie of de alias.</span><span class="sxs-lookup"><span data-stu-id="89b88-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="89b88-115">Als u bijvoorbeeld de Help voor de `Get-ChildItem` cmdlet wilt weer geven, typt u</span><span class="sxs-lookup"><span data-stu-id="89b88-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="89b88-116">of</span><span class="sxs-lookup"><span data-stu-id="89b88-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="89b88-117">Als u gedetailleerde informatie wilt weer geven **Detailed** , gebruikt u de `Get-Help` para meter detail van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="89b88-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="89b88-118">Als u bijvoorbeeld gedetailleerde informatie over de `Get-ChildItem` cmdlet wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="89b88-119">Als u alle inhoud in het Help-artikel wilt weer **Full** geven, gebruikt u `Get-Help` de volledige para meter van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="89b88-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="89b88-120">Als u bijvoorbeeld alle inhoud in het Help-artikel voor de `Get-ChildItem` cmdlet wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="89b88-121">Voor gedetailleerde informatie over de para meters van een cmdlet gebruikt u **Parameter** de para meter parameter `Get-Help` van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="89b88-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="89b88-122">Als u bijvoorbeeld gedetailleerde Help wilt ophalen voor alle para meters van de `Get-ChildItem` cmdlet, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="89b88-123">Als u alleen de voor beelden in een Help-artikel wilt weer geven, gebruikt `Get-Help`u de para meter **voor beelden** van de.</span><span class="sxs-lookup"><span data-stu-id="89b88-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="89b88-124">Als u bijvoorbeeld alleen de voor beelden in het Help-artikel voor de `Get-ChildItem` cmdlet wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="89b88-125">Zie de [Help bij cmdlet schrijven](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)voor meer informatie over het schrijven van Help-artikelen voor de cmdlets die u schrijft.</span><span class="sxs-lookup"><span data-stu-id="89b88-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="89b88-126">Conceptuele hulp krijgen</span><span class="sxs-lookup"><span data-stu-id="89b88-126">Getting conceptual help</span></span>

<span data-ttu-id="89b88-127">De `Get-Help` cmdlet geeft ook informatie weer over conceptuele artikelen in Power shell, inclusief artikelen over de Power shell-taal.</span><span class="sxs-lookup"><span data-stu-id="89b88-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="89b88-128">Conceptuele Help-artikelen beginnen met het voor voegsel ' about_ ', zoals about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="89b88-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="89b88-129">(De naam van het conceptuele artikel moet worden ingevoerd in het Engels, zelfs op niet-Engelse versies van Power shell.)</span><span class="sxs-lookup"><span data-stu-id="89b88-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="89b88-130">Als u een lijst met conceptuele artikelen wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="89b88-131">Als u een bepaald Help-artikel wilt weer geven, typt u de artikel naam, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="89b88-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="89b88-132">De `Get-Help`para meters van, zoals **gedetailleerde**, **para meters**en **voor beelden**, hebben geen effect op de weer gave van conceptuele Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="89b88-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="89b88-133">Hulp krijgen bij providers</span><span class="sxs-lookup"><span data-stu-id="89b88-133">Getting help about providers</span></span>

<span data-ttu-id="89b88-134">De `Get-Help` cmdlet geeft informatie weer over Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="89b88-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="89b88-135">Voor hulp bij een provider, typt `Get-Help` u gevolgd door de naam van de provider.</span><span class="sxs-lookup"><span data-stu-id="89b88-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="89b88-136">Als u bijvoorbeeld hulp wilt krijgen voor de register provider, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="89b88-137">Als u een lijst wilt weer geven met alle Help-artikelen van de provider in uw sessie, typt u</span><span class="sxs-lookup"><span data-stu-id="89b88-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="89b88-138">De `Get-Help`para meters van, zoals **gedetailleerde**, **para meters**en **voor beelden**, hebben geen effect op de weer gave van de Help-artikelen van de provider.</span><span class="sxs-lookup"><span data-stu-id="89b88-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="89b88-139">Hulp krijgen over scripts en functies</span><span class="sxs-lookup"><span data-stu-id="89b88-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="89b88-140">Veel scripts en functies in Power Shell hebben Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="89b88-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="89b88-141">Gebruik de `Get-Help` cmdlet om de Help-artikelen voor scripts en functies weer te geven.</span><span class="sxs-lookup"><span data-stu-id="89b88-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="89b88-142">Als u de Help voor een functie wilt weer `Get-Help` geven, typt u gevolgd door de naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="89b88-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="89b88-143">Als u bijvoorbeeld hulp voor de `Disable-PSRemoting` functie wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="89b88-144">Als u de Help voor een script wilt weer geven, typt u het pad naar het script bestand.</span><span class="sxs-lookup"><span data-stu-id="89b88-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="89b88-145">Als het script zich niet bevindt in een pad dat wordt vermeld in de omgevings variabele PATH, moet u het volledig gekwalificeerde pad gebruiken.</span><span class="sxs-lookup"><span data-stu-id="89b88-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="89b88-146">Als u bijvoorbeeld een script met de naam ' TestScript. ps1 ' in de map C:\\PS-test, om het Help-artikel voor het script weer te geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="89b88-147">De para meters die zijn ontworpen voor het weer geven van cmdlet Help, werken ook voor de Help van script en functie.</span><span class="sxs-lookup"><span data-stu-id="89b88-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="89b88-148">Help voor functies en scripts wordt echter niet weer gegeven wanneer u uitvoert `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="89b88-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="89b88-149">Raadpleeg de volgende artikelen voor informatie over het schrijven van Help-artikelen voor uw functies en scripts:</span><span class="sxs-lookup"><span data-stu-id="89b88-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="89b88-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="89b88-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="89b88-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="89b88-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="89b88-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="89b88-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="89b88-153">Online hulp krijgen</span><span class="sxs-lookup"><span data-stu-id="89b88-153">Getting help online</span></span>

<span data-ttu-id="89b88-154">De Help-artikelen online bekijken is een van de beste manieren om hulp te krijgen.</span><span class="sxs-lookup"><span data-stu-id="89b88-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="89b88-155">Online artikelen kunnen gemakkelijker worden bijgewerkt en bieden de meest actuele inhoud.</span><span class="sxs-lookup"><span data-stu-id="89b88-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="89b88-156">Gebruik de **online** -para meter van de `Get-Help` cmdlet om online hulp te krijgen.</span><span class="sxs-lookup"><span data-stu-id="89b88-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="89b88-157">Alle Help-artikelen die worden geleverd met Power shell, inclusief Help-artikelen voor de provider Help en conceptuele informatie, zijn online beschikbaar in de [Power shell](/powershell/scripting/powershell-scripting) -documentatie.</span><span class="sxs-lookup"><span data-stu-id="89b88-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="89b88-158">U kunt de para meter **online** niet gebruiken met conceptuele\*(About_) of de Help-artikelen van de provider.</span><span class="sxs-lookup"><span data-stu-id="89b88-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="89b88-159">Online-Help is optioneel en werkt daarom niet voor elke cmdlet, functie of script.</span><span class="sxs-lookup"><span data-stu-id="89b88-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="89b88-160">Als u bijvoorbeeld de online versie van het Help-artikel over de `Get-ChildItem` cmdlet wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="89b88-161">Power shell opent het artikel in de standaard browser.</span><span class="sxs-lookup"><span data-stu-id="89b88-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="89b88-162">Als online-Help wordt ondersteund voor een Help-artikel, kunt u ook de URL van het Help-artikel weer geven.</span><span class="sxs-lookup"><span data-stu-id="89b88-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="89b88-163">De URL wordt weer gegeven in de sectie verwante koppelingen van een Help-artikel.</span><span class="sxs-lookup"><span data-stu-id="89b88-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="89b88-164">Als u bijvoorbeeld de URL voor de online versie van de cmdlet Add-computer wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="89b88-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="89b88-165">De eerste regel in de sectie verwante koppelingen van het artikel wordt hieronder weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="89b88-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: https://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="89b88-166">Zie [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)voor meer informatie over het bieden van online ondersteuning voor uw Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="89b88-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="89b88-167">Zie ook</span><span class="sxs-lookup"><span data-stu-id="89b88-167">See also</span></span>

- [<span data-ttu-id="89b88-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="89b88-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="89b88-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="89b88-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="89b88-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="89b88-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="89b88-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="89b88-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
