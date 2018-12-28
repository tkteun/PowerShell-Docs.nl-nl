---
ms.date: 08/14/2018
keywords: PowerShell-cmdlet
title: Scripts schrijven en uitvoeren in Windows PowerShell ISE
ms.assetid: 62f916d9-b3a1-484a-bdfb-41f57112c22b
ms.openlocfilehash: 61db5e18f05e8e334cd9ba6dab2cf15dee7390cc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403990"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="d4e40-103">Scripts schrijven en uitvoeren in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d4e40-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="d4e40-104">Dit artikel wordt beschreven hoe u kunt maken, bewerken, uitvoeren en opslaan van scripts in het scriptvenster.</span><span class="sxs-lookup"><span data-stu-id="d4e40-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="d4e40-105">Over het maken en uitvoeren van scripts</span><span class="sxs-lookup"><span data-stu-id="d4e40-105">How to create and run scripts</span></span>

<span data-ttu-id="d4e40-106">U kunt openen en bewerken van Windows PowerShell-bestanden in het scriptvenster.</span><span class="sxs-lookup"><span data-stu-id="d4e40-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="d4e40-107">Bepaalde bestandstypen van belang zijn in Windows PowerShell zijn scriptbestanden (.ps1), data-scriptbestanden (.psd1) en module scriptbestanden (.psm1).</span><span class="sxs-lookup"><span data-stu-id="d4e40-107">Specific file types of interest in Windows PowerShell are script files (.ps1), script data files (.psd1), and script module files (.psm1).</span></span> <span data-ttu-id="d4e40-108">Deze bestandstypen zijn gekleurd in de editor scriptvenster syntaxis.</span><span class="sxs-lookup"><span data-stu-id="d4e40-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="d4e40-109">Andere algemene bestandstypen die u in het scriptvenster openen kunt zijn configuratiebestanden (.ps1xml), XML-bestanden en tekstbestanden.</span><span class="sxs-lookup"><span data-stu-id="d4e40-109">Other common file types you may open in the Script Pane are configuration files (.ps1xml), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="d4e40-110">De Windows PowerShell-uitvoeringsbeleid bepaalt of u kunt uitvoeren van scripts en Windows PowerShell-profielen en -configuratiebestanden worden geladen.</span><span class="sxs-lookup"><span data-stu-id="d4e40-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="d4e40-111">Het standaardbeleid worden uitgevoerd met beperkte toegang, voorkomt u dat alle scripts die worden uitgevoerd en wordt voorkomen dat het laden van profielen.</span><span class="sxs-lookup"><span data-stu-id="d4e40-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="d4e40-112">Als u wilt wijzigen van het uitvoeringsbeleid om toe te staan profielen die moeten worden geladen en worden gebruikt, Zie [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) en [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="d4e40-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="d4e40-113">Een nieuwe scriptbestand maken</span><span class="sxs-lookup"><span data-stu-id="d4e40-113">To create a new script file</span></span>

<span data-ttu-id="d4e40-114">Klik op de werkbalk op **nieuw**, of op de **bestand** menu, klikt u op **nieuw**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="d4e40-115">Het bestand wordt weergegeven in een nieuw tabblad van het bestand onder de huidige PowerShell-tabblad. Houd er rekening mee dat de PowerShell-tabbladen alleen zichtbaar zijn als er meer dan één.</span><span class="sxs-lookup"><span data-stu-id="d4e40-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="d4e40-116">Standaard wordt een bestand van het type script (.ps1) gemaakt, maar deze kan worden opgeslagen met een nieuwe naam en extensie.</span><span class="sxs-lookup"><span data-stu-id="d4e40-116">By default a file of type script (.ps1) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="d4e40-117">Meerdere scriptbestanden kunnen worden gemaakt in de dezelfde PowerShell-tabblad.</span><span class="sxs-lookup"><span data-stu-id="d4e40-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="d4e40-118">Een bestaand script openen</span><span class="sxs-lookup"><span data-stu-id="d4e40-118">To open an existing script</span></span>

<span data-ttu-id="d4e40-119">Klik op de werkbalk op **Open**, of op de **bestand** menu, klikt u op **Open**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="d4e40-120">In de **Open** dialoogvenster vak, selecteert u het bestand dat u wilt openen.</span><span class="sxs-lookup"><span data-stu-id="d4e40-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="d4e40-121">Het geopende bestand wordt weergegeven in een nieuw tabblad.</span><span class="sxs-lookup"><span data-stu-id="d4e40-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="d4e40-122">Om een script tabblad te sluiten</span><span class="sxs-lookup"><span data-stu-id="d4e40-122">To close a script tab</span></span>

<span data-ttu-id="d4e40-123">Klik op de **sluiten** pictogram (X) van het tabblad bestand dat u wilt sluiten of Selecteer de **bestand** en klik op **sluiten**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-123">Click the **Close** icon (X) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="d4e40-124">Als het bestand is gewijzigd sinds het laatst is opgeslagen, wordt u gevraagd op te slaan of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="d4e40-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="d4e40-125">Om weer te geven van het bestandspad</span><span class="sxs-lookup"><span data-stu-id="d4e40-125">To display the file path</span></span>

<span data-ttu-id="d4e40-126">Op het tabblad bestand, wijst u de bestandsnaam.</span><span class="sxs-lookup"><span data-stu-id="d4e40-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="d4e40-127">De volledig gekwalificeerde pad naar het scriptbestand wordt weergegeven in de knopinfo.</span><span class="sxs-lookup"><span data-stu-id="d4e40-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="d4e40-128">Een script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="d4e40-128">To run a script</span></span>

<span data-ttu-id="d4e40-129">Klik op de werkbalk op **-Script uitvoeren**, of op de **bestand** menu, klikt u op **uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="d4e40-130">Een gedeelte van een script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="d4e40-130">To run a portion of a script</span></span>

1. <span data-ttu-id="d4e40-131">Selecteer in het scriptvenster een gedeelte van een script.</span><span class="sxs-lookup"><span data-stu-id="d4e40-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="d4e40-132">Op de **bestand** menu, klikt u op **selectie uitvoeren**, of klik op de werkbalk op **selectie uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="d4e40-133">Stoppen van een script uit te voeren</span><span class="sxs-lookup"><span data-stu-id="d4e40-133">To stop a running script</span></span>

<span data-ttu-id="d4e40-134">Er zijn verschillende manieren om te stoppen van een script uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d4e40-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="d4e40-135">Klik op **stoppen bewerking** op de werkbalk</span><span class="sxs-lookup"><span data-stu-id="d4e40-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="d4e40-136">Druk op CTRL + BREAK</span><span class="sxs-lookup"><span data-stu-id="d4e40-136">Press CTRL+BREAK</span></span>
- <span data-ttu-id="d4e40-137">Selecteer de **bestand** en klik op **stoppen bewerking**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="d4e40-138">Drukken **CTRL + C** werkt ook, tenzij de tekst is geselecteerd, in welk geval **CTRL + C** wordt toegewezen aan de functie kopiëren voor de geselecteerde tekst.</span><span class="sxs-lookup"><span data-stu-id="d4e40-138">Pressing **CTRL+C** also works unless some text is currently selected, in which case **CTRL+C** maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="d4e40-139">Het schrijven en tekst in het scriptvenster bewerken</span><span class="sxs-lookup"><span data-stu-id="d4e40-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="d4e40-140">U kunt kopiëren, knippen, plakken, zoeken en vervangen tekst in het scriptvenster.</span><span class="sxs-lookup"><span data-stu-id="d4e40-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="d4e40-141">U kunt ook ongedaan maken en herstellen van de laatste actie die u zojuist hebt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d4e40-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="d4e40-142">De sneltoetsen voor deze acties zijn dezelfde snelkoppelingen die wordt gebruikt voor alle Windows-toepassingen.</span><span class="sxs-lookup"><span data-stu-id="d4e40-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="d4e40-143">Tekst invoeren in het scriptvenster</span><span class="sxs-lookup"><span data-stu-id="d4e40-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="d4e40-144">De cursor naar het scriptvenster verplaatsen door te klikken op een willekeurige plaats in het scriptvenster of door te klikken op **gaat u naar scriptvenster** in de **weergave** menu.</span><span class="sxs-lookup"><span data-stu-id="d4e40-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="d4e40-145">Een script maken.</span><span class="sxs-lookup"><span data-stu-id="d4e40-145">Create a script.</span></span> <span data-ttu-id="d4e40-146">Syntaxiskleuren en tab-Aanvulling bieden een rijkere bewerken in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d4e40-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="d4e40-147">Zie [hoe u de Tab-aanvulling gebruiken in het scriptvenster en consolevenster](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) voor meer informatie over het gebruik van het tabblad voltooiing-functie om te helpen bij het typen.</span><span class="sxs-lookup"><span data-stu-id="d4e40-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="d4e40-148">Tekst zoeken in het scriptvenster</span><span class="sxs-lookup"><span data-stu-id="d4e40-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="d4e40-149">Als u wilt zoeken overal tekst, drukt u op **CTRL + F** of Ga naar de **bewerken** menu, klikt u op **niet vinden in het Script**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-149">To find text anywhere, press **CTRL+F** or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="d4e40-150">Om te zoeken tekst na de cursor, drukt u op **F3** of Ga naar de **bewerken** menu, klikt u op **volgende zoeken in Script**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-150">To find text after the cursor, press **F3** or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="d4e40-151">Om te zoeken tekst vóór de cursor, drukt u op **SHIFT + F3** of Ga naar de **bewerken** menu, klikt u op **vorige in Script**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-151">To find text before the cursor, press **SHIFT+F3** or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="d4e40-152">Om te zoeken en vervangen tekst in het scriptvenster</span><span class="sxs-lookup"><span data-stu-id="d4e40-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="d4e40-153">Druk op **CTRL + H** of Ga naar de **bewerken** menu, klikt u op **vervangen in Script**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-153">Press **CTRL+H** or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="d4e40-154">Voer de tekst die u wilt zoeken en de nieuwe tekst, drukt u vervolgens op **ENTER**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-154">Enter the text you want to find and the replacement text, then press **ENTER**.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="d4e40-155">Naar een bepaalde regel tekst in het scriptvenster</span><span class="sxs-lookup"><span data-stu-id="d4e40-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="d4e40-156">Druk in het scriptvenster op **CTRL + G** of Ga naar de **bewerken** menu, klikt u op **gaat u naar de regel**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-156">In the Script Pane, press **CTRL+G** or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="d4e40-157">Voer een getal van de regel.</span><span class="sxs-lookup"><span data-stu-id="d4e40-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="d4e40-158">Tekst in het scriptvenster kopiëren</span><span class="sxs-lookup"><span data-stu-id="d4e40-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="d4e40-159">Selecteer in het scriptvenster de tekst die u wilt kopiëren.</span><span class="sxs-lookup"><span data-stu-id="d4e40-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="d4e40-160">Druk op **CTRL + C** of klik op de werkbalk op de **kopie** pictogram, of op de **bewerken** menu, klikt u op **kopie**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-160">Press **CTRL+C** or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="d4e40-161">Tekst in het scriptvenster knippen</span><span class="sxs-lookup"><span data-stu-id="d4e40-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="d4e40-162">Selecteer in het scriptvenster de tekst die u wilt knippen.</span><span class="sxs-lookup"><span data-stu-id="d4e40-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="d4e40-163">Druk op **CTRL + X** of klik op de werkbalk op de **Knippen** pictogram, of op de **bewerken** menu, klikt u op **Knippen**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-163">Press **CTRL+X** or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="d4e40-164">Tekst in het scriptvenster plakken</span><span class="sxs-lookup"><span data-stu-id="d4e40-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="d4e40-165">Druk op **CTRL + V** of klik op de werkbalk op de **plakken** pictogram, of op de **bewerken** menu, klikt u op **plakken**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-165">Press **CTRL+V** or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="d4e40-166">Een bewerking in het scriptvenster ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="d4e40-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="d4e40-167">Druk op **CTRL + Z** of klik op de werkbalk op de **ongedaan** pictogram, of op de **bewerken** menu, klikt u op **ongedaan maken**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-167">Press **CTRL+Z** or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="d4e40-168">Een bewerking in het scriptvenster opnieuw uitvoeren</span><span class="sxs-lookup"><span data-stu-id="d4e40-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="d4e40-169">Druk op **CTRL + Y** of klik op de werkbalk op de **opnieuw** pictogram, of op de **bewerken** menu, klikt u op **opnieuw**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-169">Press **CTRL+Y** or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="d4e40-170">Het opslaan van een script</span><span class="sxs-lookup"><span data-stu-id="d4e40-170">How to save a script</span></span>

<span data-ttu-id="d4e40-171">Er verschijnt een sterretje naast de naam van het script naar een bestand dat niet is opgeslagen, omdat deze is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="d4e40-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="d4e40-172">Het sterretje verdwijnt wanneer het bestand wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="d4e40-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="d4e40-173">Een script opslaan</span><span class="sxs-lookup"><span data-stu-id="d4e40-173">To save a script</span></span>

<span data-ttu-id="d4e40-174">Druk op **CTRL + S** of klik op de werkbalk op de **opslaan** pictogram, of op de **bestand** menu, klikt u op **opslaan**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-174">Press **CTRL+S** or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="d4e40-175">Opslaan en de naam van een script</span><span class="sxs-lookup"><span data-stu-id="d4e40-175">To save and name a script</span></span>

1. <span data-ttu-id="d4e40-176">Op de **bestand** menu, klikt u op **OpslaanAls**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="d4e40-177">De **OpslaanAls** in het dialoogvenster wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d4e40-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="d4e40-178">In de **bestandsnaam** voert u een naam voor het bestand.</span><span class="sxs-lookup"><span data-stu-id="d4e40-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="d4e40-179">In de **opslaan als** vak, selecteert u een bestandstype.</span><span class="sxs-lookup"><span data-stu-id="d4e40-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="d4e40-180">Bijvoorbeeld, in de **opslaan als** Schakel ' PowerShell-Scripts (\*.ps1)'.</span><span class="sxs-lookup"><span data-stu-id="d4e40-180">For example, in the **Save as type** box, select 'PowerShell Scripts (\*.ps1)'.</span></span>
4. <span data-ttu-id="d4e40-181">Klik op **Opslaan**.</span><span class="sxs-lookup"><span data-stu-id="d4e40-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="d4e40-182">Voor het opslaan van een script in ASCII-codering</span><span class="sxs-lookup"><span data-stu-id="d4e40-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="d4e40-183">Standaard Windows PowerShell ISE Hiermee slaat u nieuwe scriptbestanden (.ps1), data-scriptbestanden (.psd1) en module scriptbestanden (.psm1) als Unicode (BigEndianUnicode) standaard. (C) als u wilt opslaan een script in een andere codering, zoals ASCII (ANSI), gebruiken de **opslaan** of **opslaan** methoden op de [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span><span class="sxs-lookup"><span data-stu-id="d4e40-183">By default, Windows PowerShell ISE saves new script files (.ps1), script data files (.psd1), and script module files (.psm1) as Unicode (BigEndianUnicode) by default.Â To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="d4e40-184">De volgende opdracht wordt een nieuw script opgeslagen als Mijnscript.ps1 met ASCII-codering.</span><span class="sxs-lookup"><span data-stu-id="d4e40-184">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="d4e40-185">De volgende opdracht vervangt het huidige scriptbestand met een bestand met dezelfde naam maar met de ASCII-codering.</span><span class="sxs-lookup"><span data-stu-id="d4e40-185">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="d4e40-186">De volgende opdracht wordt de codering van het huidige bestand.</span><span class="sxs-lookup"><span data-stu-id="d4e40-186">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="d4e40-187">Windows PowerShell ISE ondersteunt de volgende opties voor encoding: ASCII-, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 en standaard.</span><span class="sxs-lookup"><span data-stu-id="d4e40-187">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="d4e40-188">De waarde van de standaardoptie is afhankelijk van het systeem.</span><span class="sxs-lookup"><span data-stu-id="d4e40-188">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="d4e40-189">Windows PowerShell ISE verandert niet met de codering van scriptbestanden wanneer u de opslaan of OpslaanAls opdrachten.</span><span class="sxs-lookup"><span data-stu-id="d4e40-189">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4e40-190">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d4e40-190">See Also</span></span>

- [<span data-ttu-id="d4e40-191">Kennismaking met Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d4e40-191">Exploring the Windows PowerShell ISE</span></span>](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
