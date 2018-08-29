---
ms.date: 08/27/2018
keywords: PowerShell-cmdlet
title: Gedetailleerde Help-informatie verkrijgen
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 88f0357b935a7c75df07d667e3f2f2d0e493f89d
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134031"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="647dc-103">Gedetailleerde help-informatie verkrijgen</span><span class="sxs-lookup"><span data-stu-id="647dc-103">Getting detailed help information</span></span>

<span data-ttu-id="647dc-104">PowerShell bevat gedetailleerde Help-artikelen waarin wordt uitgelegd van de PowerShell-concepten en de PowerShell-taal.</span><span class="sxs-lookup"><span data-stu-id="647dc-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="647dc-105">Er zijn ook Help-artikelen voor elke cmdlet en de provider en voor veel functies en scripts.</span><span class="sxs-lookup"><span data-stu-id="647dc-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="647dc-106">U kunt deze Help-artikelen weergeven bij de opdrachtprompt of weergave de meest recente bijgewerkte versies van de volgende artikelen in de [PowerShell](/powershell/scripting/powershell-scripting) online documentatie.</span><span class="sxs-lookup"><span data-stu-id="647dc-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/powershell-scripting) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="647dc-107">Help-informatie voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="647dc-107">Getting help for cmdlets</span></span>

<span data-ttu-id="647dc-108">Als u Help-informatie over PowerShell-cmdlets, gebruikt de [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="647dc-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="647dc-109">Als u bijvoorbeeld ondersteuning voor de `Get-ChildItem` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="647dc-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="647dc-110">of</span><span class="sxs-lookup"><span data-stu-id="647dc-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="647dc-111">U kunt ook hulp krijgen over de cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="647dc-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="647dc-112">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="647dc-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="647dc-113">Als u een lijst met alle van de cmdlet Help-artikelen in uw sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="647dc-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="647dc-114">Als u een pagina van de Help-artikel weergeven op een tijdstip, gebruiken de `help` functie of de alias `man`.</span><span class="sxs-lookup"><span data-stu-id="647dc-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="647dc-115">Bijvoorbeeld, om de Help voor weer te geven de `Get-ChildItem` cmdlet, type</span><span class="sxs-lookup"><span data-stu-id="647dc-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="647dc-116">of</span><span class="sxs-lookup"><span data-stu-id="647dc-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="647dc-117">Als u gedetailleerde informatie weergeven, gebruiken de **gedetailleerd** parameter van de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="647dc-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="647dc-118">Bijvoorbeeld, voor gedetailleerde informatie over de `Get-ChildItem` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="647dc-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="647dc-119">Als u alle inhoud weergeven in het Help-artikel, gebruiken de **volledige** parameter van de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="647dc-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="647dc-120">Bijvoorbeeld, om weer te geven van alle inhoud in het Help-artikel voor de `Get-ChildItem` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="647dc-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="647dc-121">Informatie ophalen over over de parameters van een cmdlet, gebruik de **Parameter** parameter van de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="647dc-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="647dc-122">Bijvoorbeeld, om op te halen gedetailleerde Help-informatie voor alle van de parameters van de `Get-ChildItem` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="647dc-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="647dc-123">Als u alleen de voorbeelden weergeven in een Help-artikel, gebruiken de **voorbeelden** parameter van de `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="647dc-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="647dc-124">Bijvoorbeeld, om weer te geven alleen de voorbeelden in het Help-artikel voor de `Get-ChildItem `cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="647dc-124">For example, to display only the examples in the Help article for the `Get-ChildItem `cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="647dc-125">Zie voor meer informatie over het schrijven van Help-artikelen voor de cmdlets die u schrijft [schrijven Cmdlet helpen](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="647dc-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="647dc-126">Algemene hulp</span><span class="sxs-lookup"><span data-stu-id="647dc-126">Getting conceptual help</span></span>

<span data-ttu-id="647dc-127">De `Get-Help` cmdlet ook informatie over conceptuele artikelen in PowerShell, met inbegrip van de artikelen over de PowerShell-taal weergegeven.</span><span class="sxs-lookup"><span data-stu-id="647dc-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="647dc-128">Algemene Help artikelen met het voorvoegsel 'about_', zoals about_line_editing beginnen.</span><span class="sxs-lookup"><span data-stu-id="647dc-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="647dc-129">(De naam van het conceptueel artikel moet worden ingevoerd in het Engels zelfs op niet-Engelse versies van PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="647dc-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="647dc-130">Als een lijst van de conceptuele artikelen weergeven, typt u:</span><span class="sxs-lookup"><span data-stu-id="647dc-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="647dc-131">Als een bepaalde Help-artikel weergeven, typt u de artikelnaam, bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="647dc-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="647dc-132">De parameters van `Get-Help`, zoals **gedetailleerd**, **Parameter**, en **voorbeelden**, hebben geen effect op de weergave van de conceptuele Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="647dc-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="647dc-133">Help opvragen over providers</span><span class="sxs-lookup"><span data-stu-id="647dc-133">Getting help about providers</span></span>

<span data-ttu-id="647dc-134">De `Get-Help` cmdlet geeft informatie weer over de PowerShell-providers.</span><span class="sxs-lookup"><span data-stu-id="647dc-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="647dc-135">Typ voor hulp bij een provider, `Get-Help` gevolgd door de naam van de provider.</span><span class="sxs-lookup"><span data-stu-id="647dc-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="647dc-136">Bijvoorbeeld, als u de Help voor de provider register, typt u:</span><span class="sxs-lookup"><span data-stu-id="647dc-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="647dc-137">Als u een lijst met alle van de provider Help-artikelen in uw sessie, typt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="647dc-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="647dc-138">De parameters van `Get-Help`, zoals **gedetailleerd**, **Parameter**, en **voorbeelden**, hebben geen effect op de weergave van de provider Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="647dc-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="647dc-139">Help opvragen over scripts en functies</span><span class="sxs-lookup"><span data-stu-id="647dc-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="647dc-140">Veel scripts en functies in PowerShell hebben de Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="647dc-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="647dc-141">Gebruik de `Get-Help` cmdlet om de Help-artikelen voor scripts en functies weer te geven.</span><span class="sxs-lookup"><span data-stu-id="647dc-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="647dc-142">Als u de Help voor een functie, typt `Get-Help` gevolgd door de naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="647dc-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="647dc-143">Als u bijvoorbeeld ondersteuning voor de `Disable-PSRemoting` functie, typ:</span><span class="sxs-lookup"><span data-stu-id="647dc-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="647dc-144">Als de Help voor een script weergeven, typt u het pad naar het scriptbestand.</span><span class="sxs-lookup"><span data-stu-id="647dc-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="647dc-145">Als het script zich niet in een pad dat is opgenomen in de omgevingsvariabele Path, moet u de volledig gekwalificeerde pad gebruiken.</span><span class="sxs-lookup"><span data-stu-id="647dc-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="647dc-146">Bijvoorbeeld, als u een script met de naam 'TestScript.ps1' op uw C: hebt\\PS-/ Test-directory, om weer te geven van het Help-artikel voor het script, type:</span><span class="sxs-lookup"><span data-stu-id="647dc-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="647dc-147">De parameters die zijn ontworpen voor het weergeven van de cmdlet Help werken voor het script en de functie helpen te.</span><span class="sxs-lookup"><span data-stu-id="647dc-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="647dc-148">Help voor functies en scripts wordt echter niet weergegeven tijdens het uitvoeren van `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="647dc-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="647dc-149">Zie de volgende artikelen voor meer informatie over het schrijven van Help-artikelen voor de functies en -scripts:</span><span class="sxs-lookup"><span data-stu-id="647dc-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="647dc-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="647dc-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="647dc-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="647dc-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="647dc-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="647dc-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="647dc-153">Online hulp</span><span class="sxs-lookup"><span data-stu-id="647dc-153">Getting help online</span></span>

<span data-ttu-id="647dc-154">Voor het weergeven van de Help-artikelen online is een van de beste manieren om hulp te krijgen.</span><span class="sxs-lookup"><span data-stu-id="647dc-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="647dc-155">Online artikelen zijn gemakkelijker te werken en geef de meest recente inhoud.</span><span class="sxs-lookup"><span data-stu-id="647dc-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="647dc-156">Als u online Help, gebruikt u de **Online** parameter van de `Get-Help` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="647dc-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="647dc-157">Alle Help-artikelen die worden geleverd met PowerShell, met inbegrip van provider Help en conceptuele (Help-artikelen over) zijn online beschikbaar in de [PowerShell](/powershell/scripting/powershell-scripting) documentatie.</span><span class="sxs-lookup"><span data-stu-id="647dc-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="647dc-158">U kunt geen gebruiken de **Online** parameter met de conceptuele (about_ \*) of provider Help-artikelen.</span><span class="sxs-lookup"><span data-stu-id="647dc-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="647dc-159">Online-help is optioneel, zodat deze niet voor elke cmdlet, een functie of een script werkt.</span><span class="sxs-lookup"><span data-stu-id="647dc-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="647dc-160">Bijvoorbeeld, om op te halen van de online versie van het Help-artikel over de `Get-ChildItem` cmdlet, type:</span><span class="sxs-lookup"><span data-stu-id="647dc-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="647dc-161">PowerShell wordt het artikel in de standaardbrowser geopend.</span><span class="sxs-lookup"><span data-stu-id="647dc-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="647dc-162">Als online-Help wordt ondersteund voor een Help-artikel, kunt u ook de URL van het Help-artikel weergeven.</span><span class="sxs-lookup"><span data-stu-id="647dc-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="647dc-163">De URL wordt weergegeven in de sectie Verwante koppelingen van een Help-artikel.</span><span class="sxs-lookup"><span data-stu-id="647dc-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="647dc-164">Bijvoorbeeld, als u wilt zien van de URL voor de online versie van de cmdlet Add-Computer, typt u:</span><span class="sxs-lookup"><span data-stu-id="647dc-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="647dc-165">Hieronder ziet u de eerste regel in de sectie Verwante koppelingen van het artikel.</span><span class="sxs-lookup"><span data-stu-id="647dc-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="647dc-166">Zie voor meer informatie over hoe u online om ondersteuning te bieden voor de Help-artikelen [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="647dc-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="647dc-167">Zie ook</span><span class="sxs-lookup"><span data-stu-id="647dc-167">See also</span></span>

- [<span data-ttu-id="647dc-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="647dc-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="647dc-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="647dc-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="647dc-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="647dc-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="647dc-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="647dc-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
