---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Scripts schrijven en uitvoeren in Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 4b8a9c0c3a710f3b3b9b6077c3c84e174a141db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="0ef90-103">Scripts schrijven en uitvoeren in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0ef90-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="0ef90-104">In dit onderwerp wordt beschreven hoe maken, bewerken, uitvoeren en scripts in het deelvenster Script opslaat.</span><span class="sxs-lookup"><span data-stu-id="0ef90-104">This topic describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="0ef90-105">Het maken en scripts uitvoeren</span><span class="sxs-lookup"><span data-stu-id="0ef90-105">How to create and run scripts</span></span>

<span data-ttu-id="0ef90-106">U kunt openen en bewerken van Windows PowerShell-bestanden in het scriptvenster.</span><span class="sxs-lookup"><span data-stu-id="0ef90-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="0ef90-107">Specifieke bestandstypen van belang zijn in Windows PowerShell zijn scriptbestanden (.ps1), gegevens scriptbestanden (.psd1) en module scriptbestanden (.psm1).</span><span class="sxs-lookup"><span data-stu-id="0ef90-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="0ef90-108">Deze bestandstypen zijn syntaxis in de editor scriptvenster gekleurd.</span><span class="sxs-lookup"><span data-stu-id="0ef90-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="0ef90-109">Andere veelvoorkomende bestandstypen die u in het scriptvenster openen kunt zijn configuratiebestanden (.ps1xml), XML-bestanden en tekstbestanden.</span><span class="sxs-lookup"><span data-stu-id="0ef90-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="0ef90-110">De Windows PowerShell-uitvoeringsbeleid bepaalt of u kunt scripts uitvoeren en Windows PowerShell-profielen en configuratiebestanden laden.</span><span class="sxs-lookup"><span data-stu-id="0ef90-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="0ef90-111">Het standaarduitvoeringsbeleid beperkt, wordt voorkomen dat alle scripts uitgevoerd en voorkomt u dat bij het laden profielen.</span><span class="sxs-lookup"><span data-stu-id="0ef90-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="0ef90-112">Als u wilt wijzigen van het uitvoeringsbeleid zodat profielen worden geladen en worden gebruikt, Zie [Set-ExecutionPolicy [PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) en [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span><span class="sxs-lookup"><span data-stu-id="0ef90-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) and [about_Signing [v4]](https://technet.microsoft.com/library/fcbdd3b9-0b9f-4734-b5c7-e0dcc304fa1d).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="0ef90-113">Voor het maken van een script</span><span class="sxs-lookup"><span data-stu-id="0ef90-113">To create a new script file</span></span>

<span data-ttu-id="0ef90-114">Klik op de werkbalk op **nieuw** , of op de **bestand** menu, klikt u op **nieuw**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-114">On the toolbar, click **New** , or on the **File** menu, click **New**.</span></span> <span data-ttu-id="0ef90-115">Het bestand wordt weergegeven in een nieuw tabblad bestand onder het huidige PowerShell-tabblad. Vergeet niet de tabbladen PowerShell zijn alleen zichtbaar als er meer dan één.</span><span class="sxs-lookup"><span data-stu-id="0ef90-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="0ef90-116">Standaard wordt een bestand van het type script (.ps1) gemaakt, maar deze kan worden opgeslagen met een nieuwe naam en extensie.</span><span class="sxs-lookup"><span data-stu-id="0ef90-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="0ef90-117">Meerdere scriptbestanden kunnen worden gemaakt op hetzelfde tabblad PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0ef90-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="0ef90-118">Een bestaand script openen</span><span class="sxs-lookup"><span data-stu-id="0ef90-118">To open an existing script</span></span>

<span data-ttu-id="0ef90-119">Klik op de werkbalk op **Open**, of op de **bestand** menu, klikt u op **Open**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="0ef90-120">In de **openen** dialoogvenster Selecteer het bestand dat u wilt openen.</span><span class="sxs-lookup"><span data-stu-id="0ef90-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="0ef90-121">Het geopende bestand wordt weergegeven in een nieuw tabblad.</span><span class="sxs-lookup"><span data-stu-id="0ef90-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="0ef90-122">Een script tabblad sluiten</span><span class="sxs-lookup"><span data-stu-id="0ef90-122">To close a script tab</span></span>

<span data-ttu-id="0ef90-123">Klik op het tabblad script van het script dat u wilt sluiten en voer vervolgens een van de volgende handelingen uit:</span><span class="sxs-lookup"><span data-stu-id="0ef90-123">Click the script tab of the script you want to close, then do one of the following:</span></span>

1. <span data-ttu-id="0ef90-124">Klik op de **sluiten** pictogram (X) op het tabblad script.</span><span class="sxs-lookup"><span data-stu-id="0ef90-124">Click the **Close** icon (X) on the script tab.</span></span>

2. <span data-ttu-id="0ef90-125">Op de **bestand** menu, klikt u op **sluiten**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-125">On the **File** menu, click **Close**.</span></span>

<span data-ttu-id="0ef90-126">Als het bestand is gewijzigd sinds het laatst is opgeslagen, wordt u gevraagd op te slaan of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="0ef90-126">If the file has been altered since it was last saved, you are prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="0ef90-127">Het bestandspad weergeven</span><span class="sxs-lookup"><span data-stu-id="0ef90-127">To display the file path</span></span>

<span data-ttu-id="0ef90-128">Wijs de bestandsnaam op het tabblad bestand.</span><span class="sxs-lookup"><span data-stu-id="0ef90-128">On the file tab, point to the file name.</span></span> <span data-ttu-id="0ef90-129">Het volledig gekwalificeerde pad naar het scriptbestand wordt weergegeven in knopinfo.</span><span class="sxs-lookup"><span data-stu-id="0ef90-129">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="0ef90-130">Een script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="0ef90-130">To run a script</span></span>

<span data-ttu-id="0ef90-131">Klik op de werkbalk op **-Script uitvoeren**, of op de **bestand** menu, klikt u op **uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-131">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="0ef90-132">Een gedeelte van een script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="0ef90-132">To run a portion of a script</span></span>

1. <span data-ttu-id="0ef90-133">Selecteer in het scriptvenster een deel van een script.</span><span class="sxs-lookup"><span data-stu-id="0ef90-133">In the Script Pane, select a portion of a script.</span></span>

2. <span data-ttu-id="0ef90-134">Op de **bestand** menu, klikt u op **selectie uitvoeren**, of klik op de werkbalk op **selectie uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-134">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="0ef90-135">Stoppen van een script wordt uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="0ef90-135">To stop a running script</span></span>

<span data-ttu-id="0ef90-136">Klik op de werkbalk op **bewerking stoppen**, druk op CTRL + BREAK of op de **bestand** menu, klikt u op **bewerking stoppen**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-136">On the toolbar, click **Stop Operation**, press CTRL+BREAK, or on the **File** menu, click **Stop Operation**.</span></span> <span data-ttu-id="0ef90-137">Drukken **CTRL + C** werkt ook tenzij tekst momenteel is geselecteerd, in welk geval **CTRL + C** wordt toegewezen aan de functie kopiëren voor de geselecteerde tekst.</span><span class="sxs-lookup"><span data-stu-id="0ef90-137">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="0ef90-138">Het schrijven en tekst in het scriptvenster bewerken</span><span class="sxs-lookup"><span data-stu-id="0ef90-138">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="0ef90-139">Gebruik de volgende stappen uit om tekst in het scriptvenster te bewerken.</span><span class="sxs-lookup"><span data-stu-id="0ef90-139">Use the following steps to edit text in the Script Pane.</span></span> <span data-ttu-id="0ef90-140">U kunt kopiëren, knippen, plakken, zoeken en vervangen tekst.</span><span class="sxs-lookup"><span data-stu-id="0ef90-140">You can copy, cut, paste, find, and replace text.</span></span> <span data-ttu-id="0ef90-141">U kunt ook ongedaan maken en herstellen van de laatste actie die u zojuist hebt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0ef90-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="0ef90-142">De sneltoetsen voor het uitvoeren van deze acties zijn hetzelfde als die worden gebruikt voor alle Windows-toepassingen.</span><span class="sxs-lookup"><span data-stu-id="0ef90-142">The keyboard shortcuts for performing these actions are the same as those used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="0ef90-143">Tekst invoeren in het scriptvenster</span><span class="sxs-lookup"><span data-stu-id="0ef90-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="0ef90-144">De cursor naar het scriptvenster verplaatsen door te klikken op in het scriptvenster of door te klikken op **gaat u naar scriptvenster** in de **weergave** menu.</span><span class="sxs-lookup"><span data-stu-id="0ef90-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>

2. <span data-ttu-id="0ef90-145">Een script maken.</span><span class="sxs-lookup"><span data-stu-id="0ef90-145">Create a script.</span></span> <span data-ttu-id="0ef90-146">Van de syntaxiskleuren en tab-Aanvulling Maak hiervan een rijkere ervaring in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0ef90-146">Syntax coloring and tab completion make this a richer experience in Windows PowerShell ISE.</span></span>

3. <span data-ttu-id="0ef90-147">Zie [hoe gebruik Tab-aanvulling in het scriptvenster en consolevenster](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) voor meer informatie over het gebruik van de functie van de voltooiing tabblad te helpen bij het te typen.</span><span class="sxs-lookup"><span data-stu-id="0ef90-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="0ef90-148">Tekst zoeken in het scriptvenster</span><span class="sxs-lookup"><span data-stu-id="0ef90-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="0ef90-149">Druk overal tekst zoeken op **CTRL + F** of Ga naar de **bewerken** menu, klikt u op **niet vinden in het Script**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>

2. <span data-ttu-id="0ef90-150">Druk tekst zoeken na de cursor op **F3** of Ga naar de **bewerken** menu, klikt u op **volgende zoeken in Script**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>

3. <span data-ttu-id="0ef90-151">Tekst wilt vinden voordat de cursor, drukt u op **SHIFT + F3** of Ga naar de **bewerken** menu, klikt u op **vorige in Script**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="0ef90-152">Voor tekst in het scriptvenster zoeken en vervangen</span><span class="sxs-lookup"><span data-stu-id="0ef90-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="0ef90-153">Druk op **CTRL + H** of Ga naar de **bewerken** menu, klikt u op **vervangen in Script**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="0ef90-154">Geef zowel de tekst die u wilt zoeken en de tekst die u wilt vervangen, en druk vervolgens op **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-154">Enter both the text you want to find and the text with which you want to replace it, and then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="0ef90-155">Naar een bepaalde regel tekst in het scriptvenster</span><span class="sxs-lookup"><span data-stu-id="0ef90-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="0ef90-156">Druk in het scriptvenster op **CTRL + G** of Ga naar de **bewerken** menu, klikt u op **gaat u naar regel**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="0ef90-157">Voer een getal van de regel.</span><span class="sxs-lookup"><span data-stu-id="0ef90-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="0ef90-158">Tekst in het scriptvenster kopiëren</span><span class="sxs-lookup"><span data-stu-id="0ef90-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="0ef90-159">Selecteer in het scriptvenster de tekst die u wilt kopiëren.</span><span class="sxs-lookup"><span data-stu-id="0ef90-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="0ef90-160">Druk op **CTRL + C** of klik op de werkbalk op de **kopie** pictogram, of op de **bewerken** menu, klikt u op **kopie**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="0ef90-161">Tekst in het scriptvenster knippen</span><span class="sxs-lookup"><span data-stu-id="0ef90-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="0ef90-162">Selecteer in het scriptvenster de tekst die u wilt knippen.</span><span class="sxs-lookup"><span data-stu-id="0ef90-162">In the Script Pane, select the text that you want to cut.</span></span>

2. <span data-ttu-id="0ef90-163">Druk op **CTRL + X** of klik op de werkbalk op de **Knippen** pictogram, of op de **bewerken** menu, klikt u op **Knippen**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="0ef90-164">Tekst in het scriptvenster plakken</span><span class="sxs-lookup"><span data-stu-id="0ef90-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="0ef90-165">Druk op **CTRL + V** of klik op de werkbalk op de **plakken** pictogram, of op de **bewerken** menu, klikt u op **plakken**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="0ef90-166">Een bewerking in het scriptvenster ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="0ef90-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="0ef90-167">Druk op **CTRL + Z** of klik op de werkbalk op de **ongedaan** pictogram, of op de **bewerken** menu, klikt u op **ongedaan maken**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="0ef90-168">Een bewerking in het scriptvenster opnieuw uitvoeren</span><span class="sxs-lookup"><span data-stu-id="0ef90-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="0ef90-169">Druk op **CTRL + Y** of klik op de werkbalk op de **opnieuw** pictogram, of op de **bewerken** menu, klikt u op **opnieuw**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="0ef90-170">Het opslaan van een script</span><span class="sxs-lookup"><span data-stu-id="0ef90-170">How to save a script</span></span>

<span data-ttu-id="0ef90-171">Gebruik de volgende stappen uit om te slaan en de naam van een script.</span><span class="sxs-lookup"><span data-stu-id="0ef90-171">Use the following steps to save and name a script.</span></span> <span data-ttu-id="0ef90-172">Een asterisk weergegeven naast de naam van de scriptopdracht markeren van een bestand dat niet opgeslagen is omdat dit werd gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="0ef90-172">An asterisk appears next to the script name to mark a file that has not been saved since it was altered.</span></span> <span data-ttu-id="0ef90-173">Het sterretje verdwijnt wanneer het bestand wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="0ef90-173">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="0ef90-174">Opslaan van een script</span><span class="sxs-lookup"><span data-stu-id="0ef90-174">To save a script</span></span>

<span data-ttu-id="0ef90-175">Druk op **CTRL + S** of klik op de werkbalk op de **opslaan** pictogram, of op de **bestand** menu, klikt u op **opslaan**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-175">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="0ef90-176">Voor opslaan en de naam van een script</span><span class="sxs-lookup"><span data-stu-id="0ef90-176">To save and name a script</span></span>

1. <span data-ttu-id="0ef90-177">Op de **bestand** menu, klikt u op **OpslaanAls**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-177">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="0ef90-178">De **OpslaanAls** dialoogvenster wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="0ef90-178">The **Save As** dialog box will appear.</span></span>

2. <span data-ttu-id="0ef90-179">In de **bestandsnaam** Voer een naam voor het bestand.</span><span class="sxs-lookup"><span data-stu-id="0ef90-179">In the **File name** box, enter a name for the file.</span></span>

3. <span data-ttu-id="0ef90-180">In de **opslaan als type** Selecteer een bestandstype.</span><span class="sxs-lookup"><span data-stu-id="0ef90-180">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="0ef90-181">Bijvoorbeeld, in de **opslaan als type** de optie ' œPowerShell Scripts (\* .ps1)'.</span><span class="sxs-lookup"><span data-stu-id="0ef90-181">For example, in the **Save as type** box, select 'œPowerShell Scripts (\* .ps1)'.</span></span>

4. <span data-ttu-id="0ef90-182">Klik op **Opslaan**.</span><span class="sxs-lookup"><span data-stu-id="0ef90-182">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="0ef90-183">Voor het opslaan van een script in ASCII-codering</span><span class="sxs-lookup"><span data-stu-id="0ef90-183">To save a script in ASCII encoding</span></span>

<span data-ttu-id="0ef90-184">Standaard slaat Windows PowerShell ISE nieuwe scriptbestanden (.ps1), gegevens scriptbestanden (.psd1) en module scriptbestanden (.psm1) als Unicode (BigEndianUnicode) standaard. Â Sla een script in een andere codering, zoals ASCII (ANSI), gebruikt u de **opslaan** of **SaveAs** methoden op de [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span><span class="sxs-lookup"><span data-stu-id="0ef90-184">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](https://technet.microsoft.com/en-us/library/bc3300e4-9c17-4f00-a621-c8867126e3b3#CurrentFile) object.</span></span>

<span data-ttu-id="0ef90-185">De volgende opdracht slaat een nieuw script als Mijnscript.ps1 ASCII-codering.</span><span class="sxs-lookup"><span data-stu-id="0ef90-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="0ef90-186">De volgende opdracht uit vervangen het huidige scriptbestand door een bestand met dezelfde naam, maar met ASCII-codering.</span><span class="sxs-lookup"><span data-stu-id="0ef90-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="0ef90-187">De volgende opdracht haalt de codering van het huidige bestand.</span><span class="sxs-lookup"><span data-stu-id="0ef90-187">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="0ef90-188">Windows PowerShell ISE ondersteunt de volgende opties voor codering: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 en standaard.</span><span class="sxs-lookup"><span data-stu-id="0ef90-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 and Default.</span></span> <span data-ttu-id="0ef90-189">De waarde van de standaardoptie verschillen afhankelijk van het systeem.</span><span class="sxs-lookup"><span data-stu-id="0ef90-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="0ef90-190">Windows PowerShell ISE niet verandert de codering van scripts die zijn gemaakt door in een andere editor, zelfs wanneer u gebruikt de opslaan of OpslaanAls opdrachten in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="0ef90-190">Windows PowerShell ISE does not change the encoding of scripts that were created by in other editors, even when you use the Save or Save As commands in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ef90-191">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0ef90-191">See Also</span></span>

- [<span data-ttu-id="0ef90-192">Kennismaking met Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0ef90-192">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)