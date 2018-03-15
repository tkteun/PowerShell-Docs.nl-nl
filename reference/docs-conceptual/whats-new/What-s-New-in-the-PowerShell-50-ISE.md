---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Welke s die nieuw is in de 50 van de PowerShell ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 9fd25a4759602bebf2b5df2c17d0c816a15e5e2b
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a><span data-ttu-id="b867a-103">Wat&#39;s die nieuw is in de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b867a-103">What&#39;s New in the Windows PowerShell ISE</span></span>
<span data-ttu-id="b867a-104">Dit onderwerp worden de nieuwe en bijgewerkte functies die zijn geïntroduceerd in versies van Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="b867a-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell  Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="b867a-105">Functiebeschrijving</span><span class="sxs-lookup"><span data-stu-id="b867a-105">Feature description</span></span>
<span data-ttu-id="b867a-106">De Windows PowerShell ISE is een hosttoepassing waarmee u kunt schrijven, uitvoeren en scripts en modules in een grafische en intuïtieve omgeving testen.</span><span class="sxs-lookup"><span data-stu-id="b867a-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="b867a-107">Belangrijkste functies zoals syntaxis-kleuren, tabblad voltooiing, visuele foutopsporing, Unicode-compatibiliteit en Help-onderwerpen bieden een rijke ervaring voor het uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="b867a-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="b867a-108">Zie voor een overzicht van Windows PowerShell ISE [overzicht van Windows PowerShell Integrated Scripting Environment](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span><span class="sxs-lookup"><span data-stu-id="b867a-108">For an overview of Windows PowerShell ISE, see [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span></span>

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a><span data-ttu-id="b867a-109">Nieuwe en gewijzigde functionaliteit in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="b867a-109">New and changed functionality in Windows PowerShell ISE</span></span>
<span data-ttu-id="b867a-110">De volgende tabel bevat de nieuwe en gewijzigde functies voor deze versie van Windows PowerShell ISE in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b867a-110">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

|<span data-ttu-id="b867a-111">Onderdeel/functionaliteit</span><span class="sxs-lookup"><span data-stu-id="b867a-111">Feature/functionality</span></span>|<span data-ttu-id="b867a-112">Windows PowerShell ISE 4.0</span><span class="sxs-lookup"><span data-stu-id="b867a-112">Windows PowerShell ISE 4.0</span></span>|<span data-ttu-id="b867a-113">Windows PowerShell ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="b867a-113">Windows PowerShell ISE 3.0</span></span>|<span data-ttu-id="b867a-114">Windows PowerShell ISE 2.0</span><span class="sxs-lookup"><span data-stu-id="b867a-114">Windows PowerShell ISE 2.0</span></span>|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|<span data-ttu-id="b867a-115">**[IntelliSense](#intellisense)**</span><span class="sxs-lookup"><span data-stu-id="b867a-115">**[IntelliSense](#intellisense)**</span></span>|<span data-ttu-id="b867a-116">X</span><span class="sxs-lookup"><span data-stu-id="b867a-116">X</span></span>|<span data-ttu-id="b867a-117">X</span><span class="sxs-lookup"><span data-stu-id="b867a-117">X</span></span>||
|<span data-ttu-id="b867a-118">**[Codefragmenten](#snippets)**</span><span class="sxs-lookup"><span data-stu-id="b867a-118">**[Snippets](#snippets)**</span></span>|<span data-ttu-id="b867a-119">X</span><span class="sxs-lookup"><span data-stu-id="b867a-119">X</span></span>|<span data-ttu-id="b867a-120">X</span><span class="sxs-lookup"><span data-stu-id="b867a-120">X</span></span>||
|<span data-ttu-id="b867a-121">**[Extra hulpprogramma 's](#add-on-tools)**</span><span class="sxs-lookup"><span data-stu-id="b867a-121">**[Add-on Tools](#add-on-tools)**</span></span>|<span data-ttu-id="b867a-122">X</span><span class="sxs-lookup"><span data-stu-id="b867a-122">X</span></span>|<span data-ttu-id="b867a-123">X</span><span class="sxs-lookup"><span data-stu-id="b867a-123">X</span></span>||
|<span data-ttu-id="b867a-124">**[Opnieuw opstarten van de Manager en automatisch moeten worden opgeslagen](#restart-manager-and-auto-save)**</span><span class="sxs-lookup"><span data-stu-id="b867a-124">**[Restart Manager and Auto-save](#restart-manager-and-auto-save)**</span></span>|<span data-ttu-id="b867a-125">X</span><span class="sxs-lookup"><span data-stu-id="b867a-125">X</span></span>|<span data-ttu-id="b867a-126">X</span><span class="sxs-lookup"><span data-stu-id="b867a-126">X</span></span>||
|<span data-ttu-id="b867a-127">**[Recent gebruikte](#most-recently-used-list)**</span><span class="sxs-lookup"><span data-stu-id="b867a-127">**[Most-recently used list](#most-recently-used-list)**</span></span>|<span data-ttu-id="b867a-128">X</span><span class="sxs-lookup"><span data-stu-id="b867a-128">X</span></span>|<span data-ttu-id="b867a-129">X</span><span class="sxs-lookup"><span data-stu-id="b867a-129">X</span></span>||
|<span data-ttu-id="b867a-130">**[Consolevenster](#console-pane)**</span><span class="sxs-lookup"><span data-stu-id="b867a-130">**[Console Pane](#console-pane)**</span></span>|<span data-ttu-id="b867a-131">X</span><span class="sxs-lookup"><span data-stu-id="b867a-131">X</span></span>|<span data-ttu-id="b867a-132">X</span><span class="sxs-lookup"><span data-stu-id="b867a-132">X</span></span>||
|<span data-ttu-id="b867a-133">**[Opdrachtregelopties](#command-line-switches)**</span><span class="sxs-lookup"><span data-stu-id="b867a-133">**[Command-line switches](#command-line-switches)**</span></span>|<span data-ttu-id="b867a-134">X</span><span class="sxs-lookup"><span data-stu-id="b867a-134">X</span></span>|<span data-ttu-id="b867a-135">X</span><span class="sxs-lookup"><span data-stu-id="b867a-135">X</span></span>||
|<span data-ttu-id="b867a-136">**[Nieuwe functies van de editor](#new-editor-features)**</span><span class="sxs-lookup"><span data-stu-id="b867a-136">**[New editor features](#new-editor-features)**</span></span>|<span data-ttu-id="b867a-137">X</span><span class="sxs-lookup"><span data-stu-id="b867a-137">X</span></span>|<span data-ttu-id="b867a-138">X</span><span class="sxs-lookup"><span data-stu-id="b867a-138">X</span></span>||
|<span data-ttu-id="b867a-139">**[Nieuwe Help-venster](#new-help-viewer-window)**</span><span class="sxs-lookup"><span data-stu-id="b867a-139">**[New Help viewer window](#new-help-viewer-window)**</span></span>|<span data-ttu-id="b867a-140">X</span><span class="sxs-lookup"><span data-stu-id="b867a-140">X</span></span>|<span data-ttu-id="b867a-141">X</span><span class="sxs-lookup"><span data-stu-id="b867a-141">X</span></span>||
|<span data-ttu-id="b867a-142">**[De cmdlet opdracht weergeven](#show-command-cmdlet)**</span><span class="sxs-lookup"><span data-stu-id="b867a-142">**[Show-Command cmdlet](#show-command-cmdlet)**</span></span>|<span data-ttu-id="b867a-143">X</span><span class="sxs-lookup"><span data-stu-id="b867a-143">X</span></span>|<span data-ttu-id="b867a-144">X</span><span class="sxs-lookup"><span data-stu-id="b867a-144">X</span></span>||

### <a name="intellisense"></a><span data-ttu-id="b867a-145">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="b867a-145">IntelliSense</span></span>
<span data-ttu-id="b867a-146">**In de ISE 3.0 toegevoegd**</span><span class="sxs-lookup"><span data-stu-id="b867a-146">**Added in ISE 3.0**</span></span>

<span data-ttu-id="b867a-147">IntelliSense is een automatische voltooiing hulp-functie die deel uitmaakt van Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b867a-147">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span> <span data-ttu-id="b867a-148">IntelliSense geeft klikbaar menu's met overeenkomende mogelijk cmdlets, parameters, parameterwaarden, bestanden of mappen terwijl u typt.</span><span class="sxs-lookup"><span data-stu-id="b867a-148">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="b867a-149">**Welke toegevoegde waarde van deze wijziging?**</span><span class="sxs-lookup"><span data-stu-id="b867a-149">**What value does this change add?**</span></span>

<span data-ttu-id="b867a-150">Met de toevoeging van IntelliSense is het eenvoudiger voor het detecteren van de cmdlet en syntaxis als u Windows PowerShell ISE gebruiken om scripts te maken.</span><span class="sxs-lookup"><span data-stu-id="b867a-150">With the addition of IntelliSense, it is easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="b867a-151">U kunt ook Windows PowerShell ISE voor meer informatie over Windows PowerShell bij het maken van nieuwe scripts gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b867a-151">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="b867a-152">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="b867a-152">**What works differently?**</span></span>

<span data-ttu-id="b867a-153">Wanneer u cmdlets in Windows PowerShell ISE 3.0 of hoger typt, een schuifbare en klikbaar menu wordt weergegeven, zodat u kunt bladeren en selecteer de juiste opdrachten.</span><span class="sxs-lookup"><span data-stu-id="b867a-153">When you type cmdlets in the Windows PowerShell ISE 3.0 or later, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

### <a name="snippets"></a><span data-ttu-id="b867a-154">Codefragmenten</span><span class="sxs-lookup"><span data-stu-id="b867a-154">Snippets</span></span>
<span data-ttu-id="b867a-155">**In de ISE 3.0 toegevoegd**</span><span class="sxs-lookup"><span data-stu-id="b867a-155">**Added in ISE 3.0**</span></span>

<span data-ttu-id="b867a-156">*Codefragmenten* korte gedeelten van Windows PowerShell-code die u in de scripts die u in Windows PowerShell ISE maakt kunt invoegen.</span><span class="sxs-lookup"><span data-stu-id="b867a-156">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="b867a-157">Windows PowerShell ISE wordt geleverd met een standaardset codefragmenten.</span><span class="sxs-lookup"><span data-stu-id="b867a-157">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="b867a-158">U kunt codefragmenten toevoegen met behulp van de **nieuw codefragment** cmdlet terwijl u werkt in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b867a-158">You can add snippets by using the **New-Snippet** cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="b867a-159">**Welke toegevoegde waarde van deze wijziging?**</span><span class="sxs-lookup"><span data-stu-id="b867a-159">**What value does this change add?**</span></span>

<span data-ttu-id="b867a-160">U kunt snel samenstellen en maken van scripts voor uw omgeving te automatiseren met behulp van codefragmenten.</span><span class="sxs-lookup"><span data-stu-id="b867a-160">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="b867a-161">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="b867a-161">**What works differently?**</span></span>

<span data-ttu-id="b867a-162">Codefragmenten op in Windows PowerShell 3.0 of hoger, gebruiken de **bewerken** menu, klikt u op **Start codefragmenten**, of druk op **Ctrl J**.</span><span class="sxs-lookup"><span data-stu-id="b867a-162">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press **Ctrl-J**.</span></span>

### <a name="add-on-tools"></a><span data-ttu-id="b867a-163">Extra hulpprogramma 's</span><span class="sxs-lookup"><span data-stu-id="b867a-163">Add-on tools</span></span>
<span data-ttu-id="b867a-164">**Toegevoegd in PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="b867a-164">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="b867a-165">Windows PowerShell ISE ondersteunt nu de invoegtoepassingen die Windows Presentation Foundation (WPF)-besturingselementen die worden toegevoegd met behulp van het objectmodel zijn.</span><span class="sxs-lookup"><span data-stu-id="b867a-165">Windows PowerShell ISE now supports add-on tools, which are Windows Presentation Foundation (WPF) controls that are added by using the object model.</span></span> <span data-ttu-id="b867a-166">Extra hulpprogramma's kunnen worden weergegeven als een verticale of horizontale venster in de console.</span><span class="sxs-lookup"><span data-stu-id="b867a-166">Add-on tools can be displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="b867a-167">Meerdere invoegtoepassingen in een deelvenster worden weergegeven als een besturingselement met tabbladen.</span><span class="sxs-lookup"><span data-stu-id="b867a-167">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="b867a-168">U kunt ook toevoegen of verwijderen van de invoegtoepassing-hulpprogramma's die worden geproduceerd door niet-Microsoft partijen.</span><span class="sxs-lookup"><span data-stu-id="b867a-168">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="b867a-169">Zie voor meer informatie over het importeren of te verwijderen van de invoegtoepassing extra [bewerkingen in het Windows PowerShell ISE](http://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="b867a-169">For more information about how to import or remove add-on tools, see [Windows PowerShell ISE Operations](http://technet.microsoft.com/library/cc732148.aspx).</span></span>

<span data-ttu-id="b867a-170">**Welke toegevoegde waarde van deze wijziging?**</span><span class="sxs-lookup"><span data-stu-id="b867a-170">**What value does this change add?**</span></span>

<span data-ttu-id="b867a-171">Invoegtoepassingen toestaan u uitbreiden en aanpassen van Windows PowerShell ISE met hulpprogramma's die u kunnen uw scripting ervaring te verbeteren of functionaliteit toevoegen aan Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b867a-171">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that can enhance your scripting experience or add functionality to Windows PowerShell ISE.</span></span>

<span data-ttu-id="b867a-172">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="b867a-172">**What works differently?**</span></span>

<span data-ttu-id="b867a-173">Windows PowerShell ISE 3.0 en hoger worden geleverd met de **opdrachten** invoegtoepassing.</span><span class="sxs-lookup"><span data-stu-id="b867a-173">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="b867a-174">De **opdrachten** invoegtoepassing kunt u bladeren cmdlets en help-informatie over de cmdlets side-by-side met toegang tot de **Script** en **Console** deelvensters.</span><span class="sxs-lookup"><span data-stu-id="b867a-174">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="b867a-175">Extra invoegtoepassingen kunnen worden gevonden met behulp van de **Open-invoegtoepassing voor extra Website** opdracht op de **invoegtoepassingen** menu.</span><span class="sxs-lookup"><span data-stu-id="b867a-175">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

### <a name="restart-manager-and-auto-save"></a><span data-ttu-id="b867a-176">Opnieuw opstarten van de manager en automatisch moeten worden opgeslagen</span><span class="sxs-lookup"><span data-stu-id="b867a-176">Restart manager and auto-save</span></span>
<span data-ttu-id="b867a-177">**Toegevoegd in PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="b867a-177">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="b867a-178">Windows PowerShell ISE nu automatisch opgeslagen open scripts elke twee minuten op een andere locatie.</span><span class="sxs-lookup"><span data-stu-id="b867a-178">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span>  <span data-ttu-id="b867a-179">Als Windows PowerShell ISE werkt niet, of als het besturingssysteem opnieuw wordt opgestart, nadat Windows PowerShell ISE opnieuw is opgestart, herstelt openen scripts die zijn in de laatste sessie, zelfs als de scripts zijn niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b867a-179">If Windows PowerShell ISE stops working, or if the operating system is restarted, after Windows PowerShell ISE restarts, it recovers scripts that were open in the last session, even if the scripts were not saved.</span></span>

<span data-ttu-id="b867a-180">De automatische opslaan als interval wilt wijzigen, kunt u de volgende opdracht uitvoeren in het consolevenster: **$psise. Options.AutoSaveMinuteInterval**.</span><span class="sxs-lookup"><span data-stu-id="b867a-180">To change the automatic saving interval, run the following command in the Console pane: **$psise.Options.AutoSaveMinuteInterval**.</span></span>

<span data-ttu-id="b867a-181">**Welke toegevoegde waarde van deze wijziging?**</span><span class="sxs-lookup"><span data-stu-id="b867a-181">**What value does this change add?**</span></span>

<span data-ttu-id="b867a-182">U kunt nu werken in Windows PowerShell ISE weten dat uw open scripts automatisch worden opgeslagen in het geval van een onverwacht opnieuw opgestart.</span><span class="sxs-lookup"><span data-stu-id="b867a-182">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved in the event of an unexpected restart.</span></span>

<span data-ttu-id="b867a-183">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="b867a-183">**What works differently?**</span></span>

<span data-ttu-id="b867a-184">De scripts automatisch opnieuw opstarten in geval van een Windows PowerShell ISE 2.0 niet opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b867a-184">Windows PowerShell ISE 2.0 does not save the scripts automatically in the event of a restart.</span></span>

### <a name="most-recently-used-list"></a><span data-ttu-id="b867a-185">Recent gebruikte</span><span class="sxs-lookup"><span data-stu-id="b867a-185">Most-recently used list</span></span>
<span data-ttu-id="b867a-186">**Toegevoegd in PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="b867a-186">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="b867a-187">Windows PowerShell ISE heeft nu een lijst met recent zijn gebruikt voor bestanden.</span><span class="sxs-lookup"><span data-stu-id="b867a-187">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="b867a-188">Wanneer u een bestand in Windows PowerShell ISE opent, het bestand wordt toegevoegd aan de lijst met recent zijn gebruikt op de **bestand** menu.</span><span class="sxs-lookup"><span data-stu-id="b867a-188">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="b867a-189">Als u wilt wijzigen van het aantal bestanden in de lijst met recent zijn gebruikt, kunt u de volgende opdracht uitvoeren in het consolevenster: **$psise. Options.MruCount**.</span><span class="sxs-lookup"><span data-stu-id="b867a-189">To change the default number of files in the most-recently used list, run the following command in the Console Pane: **$psise.Options.MruCount**.</span></span>

<span data-ttu-id="b867a-190">**Welke toegevoegde waarde van deze wijziging?**</span><span class="sxs-lookup"><span data-stu-id="b867a-190">**What value does this change add?**</span></span>

<span data-ttu-id="b867a-191">U kunt nu de meest recentelijk gebruikte lijst eenvoudig toegang tot uw bestanden vaak gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b867a-191">You can now use the most-recently used list to easily access your frequently-used files.</span></span>

<span data-ttu-id="b867a-192">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="b867a-192">**What works differently?**</span></span>

<span data-ttu-id="b867a-193">Windows PowerShell ISE 2.0 beschikt niet over een lijst met recent zijn gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b867a-193">Windows PowerShell ISE 2.0 does not have a most-recently used list.</span></span>

### <a name="console-pane"></a><span data-ttu-id="b867a-194">Consolevenster</span><span class="sxs-lookup"><span data-stu-id="b867a-194">Console Pane</span></span>
<span data-ttu-id="b867a-195">**Toegevoegd in PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="b867a-195">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="b867a-196">De afzonderlijke opdracht en de uitvoer deelvensters die beschikbaar in de eerste versie van Windows PowerShell ISE waren zijn gecombineerd in één Console deelvenster.</span><span class="sxs-lookup"><span data-stu-id="b867a-196">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="b867a-197">Het consolevenster lijkt in functie en het uiterlijk aan een typische Windows PowerShell-console, maar deze bevat de volgende verbeteringen (de meeste worden beschreven in dit onderwerp).</span><span class="sxs-lookup"><span data-stu-id="b867a-197">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements (most are described in this topic).</span></span>

- <span data-ttu-id="b867a-198">Kleur van de syntaxis voor de ingevoerde tekst (geen uitvoertekst), met inbegrip van XML-syntaxis</span><span class="sxs-lookup"><span data-stu-id="b867a-198">Syntax coloring for input text (not output text), including XML syntax</span></span>

- <span data-ttu-id="b867a-199">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="b867a-199">IntelliSense</span></span>

- <span data-ttu-id="b867a-200">Overeenkomende accolade</span><span class="sxs-lookup"><span data-stu-id="b867a-200">Brace matching</span></span>

- <span data-ttu-id="b867a-201">Fout-vermelding</span><span class="sxs-lookup"><span data-stu-id="b867a-201">Error indication</span></span>

- <span data-ttu-id="b867a-202">Volledige ondersteuning voor Unicode</span><span class="sxs-lookup"><span data-stu-id="b867a-202">Full Unicode support</span></span>

- <span data-ttu-id="b867a-203">**F1** contextgevoelige help</span><span class="sxs-lookup"><span data-stu-id="b867a-203">**F1** context-sensitive help</span></span>

- <span data-ttu-id="b867a-204">**CTRL + F1** opdracht contextgevoelige weergeven</span><span class="sxs-lookup"><span data-stu-id="b867a-204">**Ctrl+F1** context-sensitive Show-Command</span></span>

- <span data-ttu-id="b867a-205">Complexe script en ondersteuning van rechts naar links</span><span class="sxs-lookup"><span data-stu-id="b867a-205">Complex script and right-to-left support</span></span>

- <span data-ttu-id="b867a-206">Lettertype-ondersteuning</span><span class="sxs-lookup"><span data-stu-id="b867a-206">Font support</span></span>

- <span data-ttu-id="b867a-207">Uitzoomen</span><span class="sxs-lookup"><span data-stu-id="b867a-207">Zoom</span></span>

- <span data-ttu-id="b867a-208">Modi van regel selecteren en blok selecteren</span><span class="sxs-lookup"><span data-stu-id="b867a-208">Line-select and block-select modes</span></span>

- <span data-ttu-id="b867a-209">Behoud van getypeerde inhoud op de opdrachtregel als u op de **Up** pijl geschiedenis weergeven in de console</span><span class="sxs-lookup"><span data-stu-id="b867a-209">Preservation of typed content at the command line when you press the **Up** arrow to view history in the console</span></span>

<span data-ttu-id="b867a-210">**Welke toegevoegde waarde van deze wijziging?**</span><span class="sxs-lookup"><span data-stu-id="b867a-210">**What value does this change add?**</span></span>

<span data-ttu-id="b867a-211">Het toevoegen van deze wijzigingen consolevenster biedt een scripting-ervaring die consistenter met de console-interface.</span><span class="sxs-lookup"><span data-stu-id="b867a-211">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="b867a-212">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="b867a-212">**What works differently?**</span></span>

<span data-ttu-id="b867a-213">Windows PowerShell ISE 2.0 heeft afzonderlijke opdracht en uitvoer deelvensters.</span><span class="sxs-lookup"><span data-stu-id="b867a-213">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

### <a name="command-line-switches"></a><span data-ttu-id="b867a-214">Opdrachtregelopties</span><span class="sxs-lookup"><span data-stu-id="b867a-214">Command-line switches</span></span>
<span data-ttu-id="b867a-215">**Toegevoegd in PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="b867a-215">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="b867a-216">Als u Windows PowerShell ISE vanaf de opdrachtregel starten (door te typen **powershell_ise.exe**), kunt u de volgende nieuwe schakelopties toevoegen.</span><span class="sxs-lookup"><span data-stu-id="b867a-216">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="b867a-217">*-NoProfile*: Start Windows PowerShell ISE zonder uitgevoerd **$profile**</span><span class="sxs-lookup"><span data-stu-id="b867a-217">*-NoProfile*: Starts Windows PowerShell ISE without running **$profile**</span></span>

- <span data-ttu-id="b867a-218">*-Help*: een Help-venster wordt weergegeven</span><span class="sxs-lookup"><span data-stu-id="b867a-218">*-Help*: Displays a Help window</span></span>

- <span data-ttu-id="b867a-219">*-mta*: Start Windows PowerShell ISE in meerdere threads apartment-modus.</span><span class="sxs-lookup"><span data-stu-id="b867a-219">*-mta*: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="b867a-220">De standaardmodus voor de bewerking voor Windows PowerShell ISE is single thread apartment-modus, of *- sta*.</span><span class="sxs-lookup"><span data-stu-id="b867a-220">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or *-sta*.</span></span>

<span data-ttu-id="b867a-221">**Welke toegevoegde waarde van deze wijziging?**</span><span class="sxs-lookup"><span data-stu-id="b867a-221">**What value does this change add?**</span></span>

<span data-ttu-id="b867a-222">Het toevoegen van deze opdrachtregelopties kunt u bepalen van de omgeving waarin de Windows PowerShell ISE wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b867a-222">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="b867a-223">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="b867a-223">**What works differently?**</span></span>

<span data-ttu-id="b867a-224">Deze opdrachtregelparameters worden niet herkend door Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="b867a-224">Windows PowerShell ISE 2.0 does not recognize these command-line switches.</span></span>

### <a name="new-editor-features"></a><span data-ttu-id="b867a-225">Nieuwe functies van de editor</span><span class="sxs-lookup"><span data-stu-id="b867a-225">New editor features</span></span>
<span data-ttu-id="b867a-226">**Toegevoegd in PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="b867a-226">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="b867a-227">Andere functies van Windows PowerShell ISE-bewerken:</span><span class="sxs-lookup"><span data-stu-id="b867a-227">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="b867a-228">**XML-syntaxiskleuren**XML-syntaxis Windows PowerShell ISE nu kleuren op dezelfde manier als het Windows PowerShell-syntaxis kleuren.</span><span class="sxs-lookup"><span data-stu-id="b867a-228">**XML syntax coloring**Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>

- <span data-ttu-id="b867a-229">**Overeenkomende accolade** Windows PowerShell ISE omvat overeenkomende accolade en is gemarkeerd en kan worden gebruikt in de volgende manieren: (bijvoorbeeld met behulp van de **gaat u naar de overeenkomst** opdracht of **Ctrl +]** zoekt de haakje sluiten, hebt u een openingsaccolade geselecteerd).</span><span class="sxs-lookup"><span data-stu-id="b867a-229">**Brace matching** Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or **Ctrl + ]** locates the closing brace, if you have an opening brace selected).</span></span>

- <span data-ttu-id="b867a-230">**Overzichtsweergave** het scriptvenster ondersteunt overzicht, waarmee samenvouwen of stukjes code door te klikken op plus of min uitvouwen in de linkermarge zich aanmeldt.</span><span class="sxs-lookup"><span data-stu-id="b867a-230">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="b867a-231">U kunt de accolades gebruiken of de **#region** en **#endregion** labels markeert het begin of einde van een samenvouwbare sectie.</span><span class="sxs-lookup"><span data-stu-id="b867a-231">You can use braces or the **#region** and **#endregion** tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="b867a-232">Als u wilt uitvouwen of samenvouwen alle regio's, drukt u op **Ctrl + M**.</span><span class="sxs-lookup"><span data-stu-id="b867a-232">To expand or collapse all regions, press **Ctrl + M**.</span></span>

- <span data-ttu-id="b867a-233">**Slepen en neerzetten tekstbewerking**Windows PowerShell ISE nu ondersteunt slepen en neerzetten van tekst bewerken.</span><span class="sxs-lookup"><span data-stu-id="b867a-233">**Drag and drop text editing**Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="b867a-234">U kunt elk blok tekst selecteren en sleept u deze tekst naar een andere locatie in de editor of de console om de tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="b867a-234">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="b867a-235">Als u Houd Ctrl ingedrukt terwijl u de geselecteerde tekst sleept, wanneer u de muisknop loslaat wordt de tekst wordt gekopieerd naar de nieuwe locatie.</span><span class="sxs-lookup"><span data-stu-id="b867a-235">If you hold down the Ctrl key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="b867a-236">In deze versie van Windows PowerShell ISE, evenals de vorige versie van Windows PowerShell ISE, als u slepen en neerzetten van bestanden naar de Windows PowerShell ISE Windows PowerShell ISE opent u het bestand.</span><span class="sxs-lookup"><span data-stu-id="b867a-236">In this version of Windows PowerShell ISE, as well as the previous version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>

- <span data-ttu-id="b867a-237">**Parseren van de weergave van fouten** Parse fouten worden aangegeven met een rode onderstreping.</span><span class="sxs-lookup"><span data-stu-id="b867a-237">**Parse error display** Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="b867a-238">Wanneer u de muisaanwijzer op een fout aangegeven, wordt het probleem dat is gevonden in de code weergegeven in knopinfo.</span><span class="sxs-lookup"><span data-stu-id="b867a-238">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>

- <span data-ttu-id="b867a-239">**Zoomen** het zoompercentage van de console'™ s inhoud kan worden ingesteld met behulp van de schuifregelaar Inzoomen (in de rechterbenedenhoek van Windows PowerShell ISE-venster) of met de opdracht **$psise.options.Zoom** in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="b867a-239">**Zoom** The zoom percentage of the console'™s content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command **$psise.options.Zoom** in the Console Pane.</span></span>

- <span data-ttu-id="b867a-240">**Rich text kopiëren en plakken** kopiëren naar het Klembord in Windows PowerShell ISE gehandhaafd het lettertype, grootte en kleurinformatie van de oorspronkelijke selectie.</span><span class="sxs-lookup"><span data-stu-id="b867a-240">**Rich text copy and paste** Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>

- <span data-ttu-id="b867a-241">**Blok selecteren** kunt u een blok tekst door de ALT-toets ingedrukt te houden bij het selecteren van tekst in het deelvenster Script met de muis of door op **Alt + Shift + pijl**.</span><span class="sxs-lookup"><span data-stu-id="b867a-241">**Block selection** You can select a block of text by holding down the ALT key while selecting text in the Script Pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

<span data-ttu-id="b867a-242">**Welke toegevoegde waarde van deze wijziging?**</span><span class="sxs-lookup"><span data-stu-id="b867a-242">**What value does this change add?**</span></span>

<span data-ttu-id="b867a-243">De aanvullende functies bieden een consistentere en krachtige omgeving voor het bewerken.</span><span class="sxs-lookup"><span data-stu-id="b867a-243">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="b867a-244">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="b867a-244">**What works differently?**</span></span>

<span data-ttu-id="b867a-245">Deze bewerking uitbreidingen zijn niet aanwezig in Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="b867a-245">These editing enhancements were not present in Windows PowerShell ISE 2.0.</span></span>

### <a name="new-help-viewer-window"></a><span data-ttu-id="b867a-246">Nieuwe Help-venster</span><span class="sxs-lookup"><span data-stu-id="b867a-246">New Help viewer window</span></span>
<span data-ttu-id="b867a-247">**Toegevoegd in PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="b867a-247">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="b867a-248">Als u op **F1** wanneer de cursor zich in een cmdlet of deel uitmaken van een cmdlet gemarkeerd hebt, de nieuwe Help-viewer Help-onderwerpen over de gemarkeerde cmdlet geopend.</span><span class="sxs-lookup"><span data-stu-id="b867a-248">If you press **F1** when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="b867a-249">Typ het volgende Windows PowerShell over Help-informatie **operators** in het consolevenster, en druk **F1**.</span><span class="sxs-lookup"><span data-stu-id="b867a-249">To display Windows PowerShell About help, type  **operators** in the console pane, and then press **F1**.</span></span>

<span data-ttu-id="b867a-250">Voordat u deze functie gebruiken, moet u de meest recente versie van Windows PowerShell Help-onderwerpen downloaden van de website van Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b867a-250">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="b867a-251">De eenvoudigste methode voor het downloaden van de Help-onderwerpen is om uit te voeren de **Update-Help** cmdlet in het consolevenster bij het uitvoeren van Windows PowerShell ISE als beheerder.</span><span class="sxs-lookup"><span data-stu-id="b867a-251">The simplest method for downloading the Help topics is to run the **Update-Help** cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="b867a-252">U kunt wijzigen waar de **F1** sleutel wordt gezocht naar Help.</span><span class="sxs-lookup"><span data-stu-id="b867a-252">You can alter where the **F1** key looks for Help.</span></span> <span data-ttu-id="b867a-253">In de **extra**/**opties** menu op de **algemene instellingen** tabblad onder **overige instellingen**, kunt u instellen of schakel de selectievakje **lokale help-inhoud gebruiken in plaats van online inhoud**.</span><span class="sxs-lookup"><span data-stu-id="b867a-253">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="b867a-254">Als dit selectievakje inschakelt, zoekt vervolgens naar de client de cmdlet Help in de gedownloade Help gevonden in de map modules.</span><span class="sxs-lookup"><span data-stu-id="b867a-254">If checked, then the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span>  <span data-ttu-id="b867a-255">Als het selectievakje is uitgeschakeld, klikt u vervolgens zoekt de client op de TechNet-bibliotheek voor de help van cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b867a-255">If the checkbox is cleared, then the client looks on the TechNet library for the cmdlet help.</span></span>

<span data-ttu-id="b867a-256">**Welke toegevoegde waarde van deze wijziging?**</span><span class="sxs-lookup"><span data-stu-id="b867a-256">**What value does this change add?**</span></span>

<span data-ttu-id="b867a-257">Contextgevoelige Help zonder uw huidige cmdlet of script biedt een naadloze learning-ervaring.</span><span class="sxs-lookup"><span data-stu-id="b867a-257">Context-sensitive Help without leaving your current cmdlet or script provides a seamless learning experience.</span></span>

<span data-ttu-id="b867a-258">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="b867a-258">**What works differently?**</span></span>

<span data-ttu-id="b867a-259">Het help-bestand op de lokale computer op F1 drukt in eerdere versies van Windows PowerShell ISE worden geopend.</span><span class="sxs-lookup"><span data-stu-id="b867a-259">Pressing F1 in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="b867a-260">In Windows PowerShell ISE 3.0 en hoger, wordt er een venster geopend waarin de help voor de cmdlet die doorzoekbaar en kunnen worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="b867a-260">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="b867a-261">Deze Help-ervaring is er nieuw voor Windows PowerShell ISE 3.0 en bij te werken Help is er nieuw voor Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="b867a-261">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

### <a name="show-command-cmdlet"></a><span data-ttu-id="b867a-262">De cmdlet opdracht weergeven</span><span class="sxs-lookup"><span data-stu-id="b867a-262">Show-Command cmdlet</span></span>
<span data-ttu-id="b867a-263">**Toegevoegd in PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="b867a-263">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="b867a-264">De **opdracht weergeven** cmdlet kunt u samenstellen of een cmdlet of functie uitvoeren door een grafische formulier invullen.</span><span class="sxs-lookup"><span data-stu-id="b867a-264">The **Show-Command** cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="b867a-265">Het formulier kan gebruikers die werken met Windows PowerShell in een grafische omgeving.</span><span class="sxs-lookup"><span data-stu-id="b867a-265">The form lets users work with Windows PowerShell in a graphical environment.</span></span> <span data-ttu-id="b867a-266">**Opdracht weergeven** ook schakelt geavanceerde scripttalen voor het maken van een snelle GUI op basis van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b867a-266">**Show-Command** also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="b867a-267">**Welke toegevoegde waarde van deze wijziging?**</span><span class="sxs-lookup"><span data-stu-id="b867a-267">**What value does this change add?**</span></span>

<span data-ttu-id="b867a-268">Met behulp van **opdracht weergeven** in uw Windows PowerShell-scripts, kunt u uw gebruikers opgeven met de grafische omgeving waaraan die bekend zijn.</span><span class="sxs-lookup"><span data-stu-id="b867a-268">By using **Show-Command** in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they are familiar.</span></span> <span data-ttu-id="b867a-269">**Opdracht weergeven** kunt inleidende gebruikers meer informatie over Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b867a-269">**Show-Command** can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="b867a-270">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="b867a-270">**What works differently?**</span></span>

<span data-ttu-id="b867a-271">Opdracht weergeven is een nieuwe Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="b867a-271">Show-Command is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="b867a-272">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b867a-272">See also</span></span>
<span data-ttu-id="b867a-273">Zie de volgende koppelingen voor meer informatie over het gebruik van Windows PowerShell ISE in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b867a-273">For more information about using Windows PowerShell ISE in Windows PowerShell, see the following links.</span></span>

- [<span data-ttu-id="b867a-274">De Windows PowerShell Integrated Scripting Environment verkennen</span><span class="sxs-lookup"><span data-stu-id="b867a-274">Exploring the Windows PowerShell Integrated Scripting Environment</span></span>](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [<span data-ttu-id="b867a-275">ISE op de TechNet-Wiki</span><span class="sxs-lookup"><span data-stu-id="b867a-275">ISE on the TechNet Wiki</span></span>](http://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [<span data-ttu-id="b867a-276">Script Center</span><span class="sxs-lookup"><span data-stu-id="b867a-276">Script Center</span></span>](http://technet.microsoft.com/scriptcenter/default)

