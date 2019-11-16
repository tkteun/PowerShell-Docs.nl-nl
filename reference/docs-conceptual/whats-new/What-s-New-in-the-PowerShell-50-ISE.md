---
ms.date: 09/06/2019
keywords: Power shell, cmdlet
title: Wat is er nieuw in de Power shell 5,0 ISE
ms.openlocfilehash: f687c409a1a4b0e6b872863e9f132f7cf5baff20
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117510"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="8ce67-103">Wat is er nieuw in de Windows Power shell 5,0 ISE</span><span class="sxs-lookup"><span data-stu-id="8ce67-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="8ce67-104">In dit onderwerp worden de nieuwe en bijgewerkte functies beschreven die zijn geïntroduceerd in versies van Windows Power shell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="8ce67-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="8ce67-105">Functiebeschrijving</span><span class="sxs-lookup"><span data-stu-id="8ce67-105">Feature description</span></span>

<span data-ttu-id="8ce67-106">De Windows PowerShell ISE is een hosttoepassing waarmee u scripts en modules in een grafische en intuïtieve omgeving kunt schrijven, uitvoeren en testen.</span><span class="sxs-lookup"><span data-stu-id="8ce67-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="8ce67-107">Belang rijke functies zoals syntaxis kleuren, tabblad aanvulling, visuele fout opsporing, Unicode-compatibiliteit en context gevoelige Help bieden een rijke script ervaring.</span><span class="sxs-lookup"><span data-stu-id="8ce67-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="8ce67-108">Zie [Inleiding tot de Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8ce67-108">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="8ce67-109">De volgende tabel bevat de nieuwe en gewijzigde functies voor deze versie van Windows PowerShell ISE in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="8ce67-109">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="8ce67-110">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="8ce67-110">IntelliSense</span></span>

> <span data-ttu-id="8ce67-111">Toegevoegd in ISE 3,0</span><span class="sxs-lookup"><span data-stu-id="8ce67-111">Added in ISE 3.0</span></span>

<span data-ttu-id="8ce67-112">IntelliSense is een functie voor het automatisch volt ooien van hulp die deel uitmaakt van Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8ce67-112">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="8ce67-113">IntelliSense bevat een klikable menu met mogelijk overeenkomende cmdlets, para meters, parameter waarden, bestanden of mappen die u typt.</span><span class="sxs-lookup"><span data-stu-id="8ce67-113">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="8ce67-114">**Welke waarde voegt deze wijziging toe?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-114">**What value does this change add?**</span></span>

<span data-ttu-id="8ce67-115">Met het toevoegen van IntelliSense, is het eenvoudiger om cmdlets en syntaxis te ontdekken wanneer u Windows PowerShell ISE gebruikt om scripts te maken.</span><span class="sxs-lookup"><span data-stu-id="8ce67-115">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="8ce67-116">U kunt ook Windows PowerShell ISE gebruiken om Windows Power shell te leren wanneer u nieuwe scripts maakt.</span><span class="sxs-lookup"><span data-stu-id="8ce67-116">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="8ce67-117">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-117">**What works differently?**</span></span>

<span data-ttu-id="8ce67-118">Wanneer u cmdlets in de Windows PowerShell ISE typt, wordt een schuif bare menu venster weer gegeven, zodat u de juiste opdrachten kunt door bladeren en selecteren.</span><span class="sxs-lookup"><span data-stu-id="8ce67-118">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="8ce67-119">fragmenten</span><span class="sxs-lookup"><span data-stu-id="8ce67-119">Snippets</span></span>

> <span data-ttu-id="8ce67-120">Toegevoegd in ISE 3,0</span><span class="sxs-lookup"><span data-stu-id="8ce67-120">Added in ISE 3.0</span></span>

<span data-ttu-id="8ce67-121">*Fragmenten* zijn korte secties van Windows Power shell-code die u kunt invoegen in de scripts die u maakt in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8ce67-121">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="8ce67-122">Windows PowerShell ISE wordt geleverd met een standaardset fragmenten.</span><span class="sxs-lookup"><span data-stu-id="8ce67-122">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="8ce67-123">U kunt fragmenten toevoegen met behulp van de cmdlet `New-Snippet` terwijl u aan het werk bent in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8ce67-123">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="8ce67-124">**Welke waarde voegt deze wijziging toe?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-124">**What value does this change add?**</span></span>

<span data-ttu-id="8ce67-125">U kunt met behulp van fragmenten snel scripts verzamelen en maken om uw omgeving te automatiseren.</span><span class="sxs-lookup"><span data-stu-id="8ce67-125">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="8ce67-126">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-126">**What works differently?**</span></span>

<span data-ttu-id="8ce67-127">Als u fragmenten wilt gebruiken in Windows Power Shell 3,0 of hoger, klikt u in het menu **bewerken** op **fragmenten starten**of drukt u op <kbd>CTRL</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8ce67-127">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="8ce67-128">Invoeg toepassingen</span><span class="sxs-lookup"><span data-stu-id="8ce67-128">Add-on tools</span></span>

> <span data-ttu-id="8ce67-129">Toegevoegd in Power Shell 3,0</span><span class="sxs-lookup"><span data-stu-id="8ce67-129">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8ce67-130">Windows PowerShell ISE ondersteunt nu invoeg toepassingen met het object model.</span><span class="sxs-lookup"><span data-stu-id="8ce67-130">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="8ce67-131">Deze invoeg toepassingen zijn Windows Presentation Foundation (WPF)-besturings elementen die worden weer gegeven als een verticaal of horizon taal deel venster in de-console.</span><span class="sxs-lookup"><span data-stu-id="8ce67-131">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="8ce67-132">Meerdere invoeg toepassingen in een deel venster worden weer gegeven als besturings element met tabbladen.</span><span class="sxs-lookup"><span data-stu-id="8ce67-132">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="8ce67-133">U kunt ook invoeg toepassingen toevoegen of verwijderen die door niet-micro soft-partijen worden geproduceerd.</span><span class="sxs-lookup"><span data-stu-id="8ce67-133">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="8ce67-134">Zie [het doel van het Windows PowerShell ISE scripting object model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8ce67-134">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="8ce67-135">**Welke waarde voegt deze wijziging toe?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-135">**What value does this change add?**</span></span>

<span data-ttu-id="8ce67-136">Invoeg toepassingen bieden u de mogelijkheid om Windows PowerShell ISE uit te breiden en aan te passen met hulpprogram ma's waarmee functionaliteit wordt toegevoegd en uw script ervaring wordt verbeterd.</span><span class="sxs-lookup"><span data-stu-id="8ce67-136">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="8ce67-137">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-137">**What works differently?**</span></span>

<span data-ttu-id="8ce67-138">Windows PowerShell ISE 3,0 en hoger wordt geleverd met de invoeg toepassing- **opdrachten** .</span><span class="sxs-lookup"><span data-stu-id="8ce67-138">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="8ce67-139">Met de invoeg toepassing **opdrachten** kunt u door cmdlets bladeren en toegang krijgen tot de cmdlets naast de **script** -en **console** venster.</span><span class="sxs-lookup"><span data-stu-id="8ce67-139">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="8ce67-140">Aanvullende invoeg toepassingen kunt u vinden met behulp van de opdracht **invoeg toepassing openen** in het menu **invoeg toepassingen** .</span><span class="sxs-lookup"><span data-stu-id="8ce67-140">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="8ce67-141">Beheer opnieuw starten en automatisch opslaan</span><span class="sxs-lookup"><span data-stu-id="8ce67-141">Restart manager and auto-save</span></span>

> <span data-ttu-id="8ce67-142">Toegevoegd in Power Shell 3,0</span><span class="sxs-lookup"><span data-stu-id="8ce67-142">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8ce67-143">Windows PowerShell ISE worden nu automatisch elke twee minuten uw geopende scripts opgeslagen op een andere locatie.</span><span class="sxs-lookup"><span data-stu-id="8ce67-143">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="8ce67-144">Wanneer Windows PowerShell ISE opnieuw wordt opgestart na een onverwachte crash of opnieuw opstarten, worden scripts hersteld die in de laatste sessie zijn geopend, zelfs als de scripts niet zijn opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="8ce67-144">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="8ce67-145">Als u het interval voor automatisch opslaan wilt wijzigen, voert u de volgende opdracht uit in het console venster: `$psise.Options.AutoSaveMinuteInterval`.</span><span class="sxs-lookup"><span data-stu-id="8ce67-145">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="8ce67-146">**Welke waarde voegt deze wijziging toe?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-146">**What value does this change add?**</span></span>

<span data-ttu-id="8ce67-147">U kunt nu binnen Windows PowerShell ISE weten dat uw geopende scripts automatisch worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="8ce67-147">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="8ce67-148">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-148">**What works differently?**</span></span>

<span data-ttu-id="8ce67-149">De scripts worden niet automatisch door Windows PowerShell ISE 2,0 opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="8ce67-149">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="8ce67-150">Meest recent gebruikte lijst</span><span class="sxs-lookup"><span data-stu-id="8ce67-150">Most-recently used list</span></span>

> <span data-ttu-id="8ce67-151">Toegevoegd in Power Shell 3,0</span><span class="sxs-lookup"><span data-stu-id="8ce67-151">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8ce67-152">Windows PowerShell ISE hebt nu een meest recent gebruikte lijst voor bestanden.</span><span class="sxs-lookup"><span data-stu-id="8ce67-152">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="8ce67-153">Wanneer u een bestand opent in Windows PowerShell ISE, wordt het bestand toegevoegd aan de lijst met meest recent gebruikte bestanden in het menu **bestand** .</span><span class="sxs-lookup"><span data-stu-id="8ce67-153">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="8ce67-154">Als u het standaard aantal bestanden in de meest recent gebruikte lijst wilt wijzigen, voert u de volgende opdracht uit in het console venster: `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="8ce67-154">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="8ce67-155">**Welke waarde voegt deze wijziging toe?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-155">**What value does this change add?**</span></span>

<span data-ttu-id="8ce67-156">U kunt nu de meest recent gebruikte lijst gebruiken om eenvoudig toegang te krijgen tot uw veelgebruikte bestanden.</span><span class="sxs-lookup"><span data-stu-id="8ce67-156">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="8ce67-157">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-157">**What works differently?**</span></span>

<span data-ttu-id="8ce67-158">Windows PowerShell ISE 2,0 heeft geen meest recent gebruikte lijst.</span><span class="sxs-lookup"><span data-stu-id="8ce67-158">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="8ce67-159">Console venster</span><span class="sxs-lookup"><span data-stu-id="8ce67-159">Console Pane</span></span>

> <span data-ttu-id="8ce67-160">Toegevoegd in Power Shell 3,0</span><span class="sxs-lookup"><span data-stu-id="8ce67-160">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8ce67-161">De afzonderlijke opdracht-en uitvoer deel Vensters die beschikbaar waren in de eerste versie van Windows PowerShell ISE, zijn gecombineerd in één console venster.</span><span class="sxs-lookup"><span data-stu-id="8ce67-161">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="8ce67-162">Het console venster is vergelijkbaar met de functie en het uiterlijk van een typische Windows Power shell-console, maar bevat de volgende verbeteringen:</span><span class="sxs-lookup"><span data-stu-id="8ce67-162">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="8ce67-163">Syntaxis kleuren voor invoer tekst (niet uitvoer tekst), met inbegrip van XML-syntaxis</span><span class="sxs-lookup"><span data-stu-id="8ce67-163">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="8ce67-164">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="8ce67-164">IntelliSense</span></span>
- <span data-ttu-id="8ce67-165">Accolades vergelijken</span><span class="sxs-lookup"><span data-stu-id="8ce67-165">Brace matching</span></span>
- <span data-ttu-id="8ce67-166">Fout melding</span><span class="sxs-lookup"><span data-stu-id="8ce67-166">Error indication</span></span>
- <span data-ttu-id="8ce67-167">Volledige Unicode-ondersteuning</span><span class="sxs-lookup"><span data-stu-id="8ce67-167">Full Unicode support</span></span>
- <span data-ttu-id="8ce67-168">Context afhankelijke Help van <kbd>F1</kbd></span><span class="sxs-lookup"><span data-stu-id="8ce67-168"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="8ce67-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context gevoelige weer gave-opdracht</span><span class="sxs-lookup"><span data-stu-id="8ce67-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="8ce67-170">Ondersteuning voor complex schrift en van rechts naar links</span><span class="sxs-lookup"><span data-stu-id="8ce67-170">Complex script and right-to-left support</span></span>
- <span data-ttu-id="8ce67-171">Lettertype ondersteuning</span><span class="sxs-lookup"><span data-stu-id="8ce67-171">Font support</span></span>
- <span data-ttu-id="8ce67-172">Zoom</span><span class="sxs-lookup"><span data-stu-id="8ce67-172">Zoom</span></span>
- <span data-ttu-id="8ce67-173">Lijn-selecteren en blok keren-selectie modi</span><span class="sxs-lookup"><span data-stu-id="8ce67-173">Line-select and block-select modes</span></span>
- <span data-ttu-id="8ce67-174">Behoud van getypte inhoud op de opdracht regel wanneer u op de <kbd>pijl-omlaag</kbd> drukt om de geschiedenis in de-console weer te geven</span><span class="sxs-lookup"><span data-stu-id="8ce67-174">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="8ce67-175">**Welke waarde voegt deze wijziging toe?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-175">**What value does this change add?**</span></span>

<span data-ttu-id="8ce67-176">De toevoeging van deze wijzigingen in het console venster biedt een script ervaring die consistent is met de interface van de console.</span><span class="sxs-lookup"><span data-stu-id="8ce67-176">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="8ce67-177">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-177">**What works differently?**</span></span>

<span data-ttu-id="8ce67-178">Windows PowerShell ISE 2,0 heeft afzonderlijke opdracht-en uitvoer deel Vensters.</span><span class="sxs-lookup"><span data-stu-id="8ce67-178">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="8ce67-179">Opdracht regel opties</span><span class="sxs-lookup"><span data-stu-id="8ce67-179">Command-line switches</span></span>

> <span data-ttu-id="8ce67-180">Toegevoegd in Power Shell 3,0</span><span class="sxs-lookup"><span data-stu-id="8ce67-180">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8ce67-181">Als u Windows PowerShell ISE start vanaf de opdracht regel (door **powershell_ise. exe**te typen), kunt u de volgende nieuwe opdracht regel opties toevoegen.</span><span class="sxs-lookup"><span data-stu-id="8ce67-181">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="8ce67-182">`-NoProfile`: er wordt Windows PowerShell ISE gestart zonder dat `$profile` wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="8ce67-182">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="8ce67-183">`-Help`: Hiermee wordt een Help-venster weer gegeven</span><span class="sxs-lookup"><span data-stu-id="8ce67-183">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="8ce67-184">`-mta`: de Windows PowerShell ISE wordt gestart in de modus voor meerdere threads.</span><span class="sxs-lookup"><span data-stu-id="8ce67-184">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="8ce67-185">De standaard bewerkings modus voor Windows PowerShell ISE is modus met één thread of `-sta`.</span><span class="sxs-lookup"><span data-stu-id="8ce67-185">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="8ce67-186">**Welke waarde voegt deze wijziging toe?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-186">**What value does this change add?**</span></span>

<span data-ttu-id="8ce67-187">Met deze opdracht regel opties kunt u de omgeving bepalen waarin de Windows PowerShell ISE wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8ce67-187">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="8ce67-188">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-188">**What works differently?**</span></span>

<span data-ttu-id="8ce67-189">Windows PowerShell ISE 2,0 herkent deze opdracht regel opties niet.</span><span class="sxs-lookup"><span data-stu-id="8ce67-189">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="8ce67-190">Nieuwe editor functies</span><span class="sxs-lookup"><span data-stu-id="8ce67-190">New editor features</span></span>

> <span data-ttu-id="8ce67-191">Toegevoegd in Power Shell 3,0</span><span class="sxs-lookup"><span data-stu-id="8ce67-191">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8ce67-192">Andere functies voor het bewerken van Windows PowerShell ISE zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="8ce67-192">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="8ce67-193">**XML-syntaxis kleuren** -Windows PowerShell ISE nu kleuren XML-syntaxis op dezelfde manier als de Windows Power shell-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="8ce67-193">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="8ce67-194">**Vergeleken met accolades** : Windows PowerShell ISE omvatten accolades en markeringen en kunnen op de volgende manieren worden gebruikt: (als u bijvoorbeeld de opdracht **Go to Match** of <kbd>CTRL</kbd>+<kbd>]</kbd> zoekt, wordt de accolade gesloten als u een openings accolade hebt geselecteerd).</span><span class="sxs-lookup"><span data-stu-id="8ce67-194">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="8ce67-195">**Overzichts weergave** Het deel venster script ondersteunt overzichten, waarmee u gedeelten van code kunt samen vouwen of uitvouwen door te klikken op een plus teken of minteken in de linkermarge.</span><span class="sxs-lookup"><span data-stu-id="8ce67-195">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="8ce67-196">U kunt accolades of de `#region`-en `#endregion`-Tags gebruiken om het begin of einde van een inklap bare sectie te markeren.</span><span class="sxs-lookup"><span data-stu-id="8ce67-196">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="8ce67-197">Als u alle regio's wilt uitvouwen of samen vouwen, drukt u op <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8ce67-197">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="8ce67-198">**Slepen en neerzetten van tekst** -Windows PowerShell ISE ondersteunt nu slepen en neerzetten van tekst.</span><span class="sxs-lookup"><span data-stu-id="8ce67-198">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="8ce67-199">U kunt elk wille keurig blok tekst selecteren en deze tekst naar een andere locatie in de editor of de-console slepen om de tekst te verplaatsen.</span><span class="sxs-lookup"><span data-stu-id="8ce67-199">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="8ce67-200">Als u de <kbd>CTRL</kbd> -toets ingedrukt houdt terwijl u de geselecteerde tekst sleept, wordt de tekst gekopieerd naar de nieuwe locatie wanneer u de muis knop loslaat.</span><span class="sxs-lookup"><span data-stu-id="8ce67-200">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="8ce67-201">In deze versie van Windows PowerShell ISE, wanneer u bestanden naar Windows PowerShell ISE sleept en neerzet, Windows PowerShell ISE het bestand wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="8ce67-201">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="8ce67-202">**Fout weer geven bij parseren** -parseren van fouten worden aangeduid met rode onderstrepingen.</span><span class="sxs-lookup"><span data-stu-id="8ce67-202">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="8ce67-203">Wanneer u de muis aanwijzer over een aangegeven fout beweegt, wordt in de tekst van de knop Info het probleem weer gegeven dat in de code is gevonden.</span><span class="sxs-lookup"><span data-stu-id="8ce67-203">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="8ce67-204">**Zoom** -het zoom percentage van de inhoud van de console kan worden ingesteld met behulp van de schuif regelaar in-en uitzoomen (in de rechter benedenhoek van Windows PowerShell ISE venster) of door de opdracht `$psise.options.Zoom` in het console venster in te voeren.</span><span class="sxs-lookup"><span data-stu-id="8ce67-204">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="8ce67-205">**RTF kopiëren en plakken** kopiëren naar het klem bord in Windows PowerShell ISE behoudt het letter type, de grootte en de kleur gegevens van de oorspronkelijke selectie.</span><span class="sxs-lookup"><span data-stu-id="8ce67-205">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="8ce67-206">**Selectie blok keren** : u kunt een blok tekst selecteren door de <kbd>Alt</kbd> -toets ingedrukt te houden terwijl u tekst in het Script venster met de muis selecteert, of door op <kbd>Alt</kbd>+<kbd>SHIFT</kbd>+<kbd>pijl</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="8ce67-206">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="8ce67-207">**Welke waarde voegt deze wijziging toe?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-207">**What value does this change add?**</span></span>

<span data-ttu-id="8ce67-208">De aanvullende bewerkings functies bieden een consistente en krachtige bewerkings omgeving.</span><span class="sxs-lookup"><span data-stu-id="8ce67-208">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="8ce67-209">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-209">**What works differently?**</span></span>

<span data-ttu-id="8ce67-210">Deze bewerkings uitbreidingen zijn niet aanwezig in Windows PowerShell ISE 2,0.</span><span class="sxs-lookup"><span data-stu-id="8ce67-210">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="8ce67-211">Nieuw Help viewer-venster</span><span class="sxs-lookup"><span data-stu-id="8ce67-211">New Help viewer window</span></span>

> <span data-ttu-id="8ce67-212">Toegevoegd in Power Shell 3,0</span><span class="sxs-lookup"><span data-stu-id="8ce67-212">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8ce67-213">Als u op <kbd>F1</kbd> drukt wanneer uw cursor zich in een cmdlet bevindt of als u een deel van een cmdlet hebt gemarkeerd, opent de nieuwe Help-viewer context gevoelige Help-informatie over de gemarkeerde cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ce67-213">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="8ce67-214">Als u de Help van Windows Power **Shell wilt weer** geven, typt u `operators` in het console venster en drukt u vervolgens op <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8ce67-214">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="8ce67-215">Voordat u deze functie gebruikt, downloadt u de meest recente versie van de Help-onderwerpen voor Windows Power shell op de website van micro soft.</span><span class="sxs-lookup"><span data-stu-id="8ce67-215">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="8ce67-216">De eenvoudigste methode voor het downloaden van de Help-onderwerpen is het uitvoeren van de `Update-Help`-cmdlet in het console venster wanneer u Windows PowerShell ISE als beheerder uitvoert.</span><span class="sxs-lookup"><span data-stu-id="8ce67-216">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="8ce67-217">U kunt wijzigen waar de <kbd>F1</kbd> -toets naar Help zoekt.</span><span class="sxs-lookup"><span data-stu-id="8ce67-217">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="8ce67-218">In het menu **extra**/**Opties** , op het tabblad **algemene instellingen** onder **andere instellingen**, kunt u het selectie vakje **lokale Help-inhoud gebruiken in plaats van online inhoud**in-of uitschakelen.</span><span class="sxs-lookup"><span data-stu-id="8ce67-218">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="8ce67-219">Als u dit selectie vakje inschakelt, zoekt de client naar de Help van de cmdlet in de gedownloade Help die in de map modules is gevonden.</span><span class="sxs-lookup"><span data-stu-id="8ce67-219">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="8ce67-220">Als het selectie vakje is uitgeschakeld, zoekt de client online naar Help.</span><span class="sxs-lookup"><span data-stu-id="8ce67-220">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="8ce67-221">**Welke waarde voegt deze wijziging toe?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-221">**What value does this change add?**</span></span>

<span data-ttu-id="8ce67-222">Context gevoelige Help zonder uw huidige cmdlet of script te verlaten biedt een geïntegreerde leer ervaring.</span><span class="sxs-lookup"><span data-stu-id="8ce67-222">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="8ce67-223">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-223">**What works differently?**</span></span>

<span data-ttu-id="8ce67-224">Als u op <kbd>F1</kbd> drukt in vorige versies van Windows PowerShell ISE hebt u het Help-bestand op de lokale computer geopend.</span><span class="sxs-lookup"><span data-stu-id="8ce67-224">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="8ce67-225">In Windows PowerShell ISE 3,0 en hoger wordt een venster geopend met de Help voor de cmdlet die kan worden doorzocht en geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="8ce67-225">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="8ce67-226">Deze Help-ervaring is nieuw voor Windows PowerShell ISE 3,0 en de bijwerk bare Help is nieuw voor Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ce67-226">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="8ce67-227">Show-opdracht-cmdlet</span><span class="sxs-lookup"><span data-stu-id="8ce67-227">Show-Command cmdlet</span></span>

> <span data-ttu-id="8ce67-228">Toegevoegd in Power Shell 3,0</span><span class="sxs-lookup"><span data-stu-id="8ce67-228">Added in PowerShell 3.0</span></span>

<span data-ttu-id="8ce67-229">Met de cmdlet `Show-Command` kunt u een cmdlet of functie samen stellen of uitvoeren door een grafisch formulier in te vullen.</span><span class="sxs-lookup"><span data-stu-id="8ce67-229">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="8ce67-230">Met het formulier kunnen gebruikers werken met Windows Power shell in een grafische omgeving.</span><span class="sxs-lookup"><span data-stu-id="8ce67-230">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="8ce67-231">met `Show-Command` kunt u ook geavanceerde scripters een snelle, op Windows Power shell gebaseerde gebruikers interface maken.</span><span class="sxs-lookup"><span data-stu-id="8ce67-231">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="8ce67-232">**Welke waarde voegt deze wijziging toe?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-232">**What value does this change add?**</span></span>

<span data-ttu-id="8ce67-233">Met behulp van `Show-Command` in uw Windows Power shell-scripts kunt u uw gebruikers voorzien van de grafische omgeving waarmee ze bekend zijn.</span><span class="sxs-lookup"><span data-stu-id="8ce67-233">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="8ce67-234">`Show-Command` kan de inleidende gebruikers ook helpen bij het leren van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="8ce67-234">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="8ce67-235">**Wat werkt er anders?**</span><span class="sxs-lookup"><span data-stu-id="8ce67-235">**What works differently?**</span></span>

<span data-ttu-id="8ce67-236">`Show-Command` is nieuw Windows PowerShell ISE 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ce67-236">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ce67-237">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8ce67-237">See also</span></span>

<span data-ttu-id="8ce67-238">Zie [de Windows Power shell Integrated Scripting Environment verkennen](../components/ise/exploring-the-windows-powershell-ise.md)voor meer informatie over het gebruik van Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8ce67-238">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../components/ise/exploring-the-windows-powershell-ise.md).</span></span>
