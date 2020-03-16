---
ms.date: 01/02/2020
keywords: Power shell, cmdlet
title: Scripts schrijven en uitvoeren in Windows PowerShell ISE
ms.openlocfilehash: 2e3122a3b436ba878d2c5f9d72d4f9e024d4d031
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79406977"
---
# <a name="how-to-write-and-run-scripts-in-the-windows-powershell-ise"></a><span data-ttu-id="168c3-103">Scripts schrijven en uitvoeren in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="168c3-103">How to Write and Run Scripts in the Windows PowerShell ISE</span></span>

<span data-ttu-id="168c3-104">In dit artikel wordt beschreven hoe u scripts maakt, bewerkt, uitvoert en opslaat in het Script-venster.</span><span class="sxs-lookup"><span data-stu-id="168c3-104">This article describes how to create, edit, run, and save scripts in the Script Pane.</span></span>

## <a name="how-to-create-and-run-scripts"></a><span data-ttu-id="168c3-105">Scripts maken en uitvoeren</span><span class="sxs-lookup"><span data-stu-id="168c3-105">How to create and run scripts</span></span>

<span data-ttu-id="168c3-106">U kunt Windows Power Shell-bestanden openen en bewerken in het Script-venster.</span><span class="sxs-lookup"><span data-stu-id="168c3-106">You can open and edit Windows PowerShell files in the Script Pane.</span></span> <span data-ttu-id="168c3-107">Specifieke bestands typen die van belang zijn in Windows Power shell zijn script bestanden (`.ps1`), script-gegevens bestanden (`.psd1`) en script module bestanden (`.psm1`).</span><span class="sxs-lookup"><span data-stu-id="168c3-107">Specific file types of interest in Windows PowerShell are script files (`.ps1`), script data files (`.psd1`), and script module files (`.psm1`).</span></span> <span data-ttu-id="168c3-108">Deze bestands typen zijn syntaxis gekleurd in de Script-Editor.</span><span class="sxs-lookup"><span data-stu-id="168c3-108">These file types are syntax colored in the Script Pane editor.</span></span> <span data-ttu-id="168c3-109">Andere algemene bestands typen die u kunt openen in het deel venster script zijn configuratie bestanden (`.ps1xml`), XML-bestanden en tekst bestanden.</span><span class="sxs-lookup"><span data-stu-id="168c3-109">Other common file types you may open in the Script Pane are configuration files (`.ps1xml`), XML files, and text files.</span></span>

> [!NOTE]
> <span data-ttu-id="168c3-110">Het Windows Power shell-uitvoerings beleid bepaalt of u scripts kunt uitvoeren en Windows Power shell-profielen en-configuratie bestanden kan laden.</span><span class="sxs-lookup"><span data-stu-id="168c3-110">The Windows PowerShell execution policy determines whether you can run scripts and load Windows PowerShell profiles and configuration files.</span></span> <span data-ttu-id="168c3-111">Het standaard uitvoerings beleid, beperkt, voor komt dat alle scripts worden uitgevoerd en voor komt het laden van profielen.</span><span class="sxs-lookup"><span data-stu-id="168c3-111">The default execution policy, Restricted, prevents all scripts from running, and prevents loading profiles.</span></span> <span data-ttu-id="168c3-112">Zie [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) en [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)om het uitvoerings beleid te wijzigen zodat de profielen kunnen worden geladen en gebruikt.</span><span class="sxs-lookup"><span data-stu-id="168c3-112">To change the execution policy to allow profiles to load and be used, see [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) and [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

### <a name="to-create-a-new-script-file"></a><span data-ttu-id="168c3-113">Een nieuw script bestand maken</span><span class="sxs-lookup"><span data-stu-id="168c3-113">To create a new script file</span></span>

<span data-ttu-id="168c3-114">Klik op de werk balk op **Nieuw**of Klik in het menu **bestand** op **Nieuw**.</span><span class="sxs-lookup"><span data-stu-id="168c3-114">On the toolbar, click **New**, or on the **File** menu, click **New**.</span></span> <span data-ttu-id="168c3-115">Het gemaakte bestand wordt weer gegeven op het tabblad nieuw bestand onder het huidige Power shell-tabblad. Houd er rekening mee dat de Power shell-tabbladen alleen zichtbaar zijn wanneer er meer dan één.</span><span class="sxs-lookup"><span data-stu-id="168c3-115">The created file appears in a new file tab under the current PowerShell tab. Remember that the PowerShell tabs are only visible when there are more than one.</span></span> <span data-ttu-id="168c3-116">Standaard wordt een bestand met het type script (`.ps1`) gemaakt, maar dit kan worden opgeslagen met een nieuwe naam en extensie.</span><span class="sxs-lookup"><span data-stu-id="168c3-116">By default a file of type script (`.ps1`) is created, but it can be saved with a new name and extension.</span></span> <span data-ttu-id="168c3-117">Meerdere script bestanden kunnen worden gemaakt op hetzelfde Power shell-tabblad.</span><span class="sxs-lookup"><span data-stu-id="168c3-117">Multiple script files can be created in the same PowerShell tab.</span></span>

### <a name="to-open-an-existing-script"></a><span data-ttu-id="168c3-118">Een bestaand script openen</span><span class="sxs-lookup"><span data-stu-id="168c3-118">To open an existing script</span></span>

<span data-ttu-id="168c3-119">Klik op de werk balk op **openen**of Klik in het menu **bestand** op **openen**.</span><span class="sxs-lookup"><span data-stu-id="168c3-119">On the toolbar, click **Open**, or on the **File** menu, click **Open**.</span></span> <span data-ttu-id="168c3-120">Selecteer in het dialoog venster **openen** het bestand dat u wilt openen.</span><span class="sxs-lookup"><span data-stu-id="168c3-120">In the **Open** dialog box, select the file you want to open.</span></span> <span data-ttu-id="168c3-121">Het geopende bestand wordt weer gegeven op een nieuw tabblad.</span><span class="sxs-lookup"><span data-stu-id="168c3-121">The opened file appears in a new tab.</span></span>

### <a name="to-close-a-script-tab"></a><span data-ttu-id="168c3-122">Het tabblad Script sluiten</span><span class="sxs-lookup"><span data-stu-id="168c3-122">To close a script tab</span></span>

<span data-ttu-id="168c3-123">Klik op het pictogram **sluiten** (**X**) van het tabblad bestand dat u wilt sluiten of selecteer het menu **bestand** en klik op **sluiten**.</span><span class="sxs-lookup"><span data-stu-id="168c3-123">Click the **Close** icon (**X**) of the file tab you want to close or select the **File** menu and click **Close**.</span></span>

<span data-ttu-id="168c3-124">Als het bestand sinds de laatste keer dat het is opgeslagen, is gewijzigd, wordt u gevraagd dit op te slaan of te negeren.</span><span class="sxs-lookup"><span data-stu-id="168c3-124">If the file has been altered since it was last saved, you're prompted to save or discard it.</span></span>

### <a name="to-display-the-file-path"></a><span data-ttu-id="168c3-125">Het bestandspad weer geven</span><span class="sxs-lookup"><span data-stu-id="168c3-125">To display the file path</span></span>

<span data-ttu-id="168c3-126">Wijs op het tabblad bestand de naam van het bestand aan.</span><span class="sxs-lookup"><span data-stu-id="168c3-126">On the file tab, point to the file name.</span></span> <span data-ttu-id="168c3-127">Het volledig gekwalificeerde pad naar het script bestand wordt weer gegeven in de knop info.</span><span class="sxs-lookup"><span data-stu-id="168c3-127">The fully qualified path to the script file appears in a tooltip.</span></span>

### <a name="to-run-a-script"></a><span data-ttu-id="168c3-128">Een script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="168c3-128">To run a script</span></span>

<span data-ttu-id="168c3-129">Klik op de werk balk op **script uitvoeren**of Klik in het menu **bestand** op **uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="168c3-129">On the toolbar, click **Run Script**, or on the **File** menu, click **Run**.</span></span>

### <a name="to-run-a-portion-of-a-script"></a><span data-ttu-id="168c3-130">Een gedeelte van een script uitvoeren</span><span class="sxs-lookup"><span data-stu-id="168c3-130">To run a portion of a script</span></span>

1. <span data-ttu-id="168c3-131">Selecteer een gedeelte van een script in het Script-venster.</span><span class="sxs-lookup"><span data-stu-id="168c3-131">In the Script Pane, select a portion of a script.</span></span>
2. <span data-ttu-id="168c3-132">Klik in het menu **bestand** op **selectie uitvoeren**of klik op de werk balk op **selectie uitvoeren**.</span><span class="sxs-lookup"><span data-stu-id="168c3-132">On the **File** menu, click **Run Selection**, or on the toolbar, click **Run Selection**.</span></span>

### <a name="to-stop-a-running-script"></a><span data-ttu-id="168c3-133">Een actief script stoppen</span><span class="sxs-lookup"><span data-stu-id="168c3-133">To stop a running script</span></span>

<span data-ttu-id="168c3-134">Er zijn verschillende manieren om een actief script te stoppen.</span><span class="sxs-lookup"><span data-stu-id="168c3-134">There are several ways to stop a running script.</span></span>

- <span data-ttu-id="168c3-135">Klik op **Stop bewerking** op de werk balk</span><span class="sxs-lookup"><span data-stu-id="168c3-135">Click **Stop Operation** on the toolbar</span></span>
- <span data-ttu-id="168c3-136">Druk op <kbd>CTRL</kbd>+<kbd>afbreek</kbd> punt</span><span class="sxs-lookup"><span data-stu-id="168c3-136">Press <kbd>CTRL</kbd>+<kbd>BREAK</kbd></span></span>
- <span data-ttu-id="168c3-137">Selecteer het menu **bestand** en klik op **bewerking stoppen**.</span><span class="sxs-lookup"><span data-stu-id="168c3-137">Select the **File** menu and click **Stop Operation**.</span></span>

<span data-ttu-id="168c3-138">Het is ook mogelijk om op <kbd>ctrl</kbd>+<kbd>c</kbd> te drukken, tenzij er al een tekst is geselecteerd. in dat geval wordt <kbd>CTRL</kbd>+<kbd>C</kbd> toegewezen aan de kopieer functie voor de geselecteerde tekst.</span><span class="sxs-lookup"><span data-stu-id="168c3-138">Pressing <kbd>CTRL</kbd>+<kbd>C</kbd> also works unless some text is currently selected, in which case <kbd>CTRL</kbd>+<kbd>C</kbd> maps to the copy function for the selected text.</span></span>

## <a name="how-to-write-and-edit-text-in-the-script-pane"></a><span data-ttu-id="168c3-139">Tekst schrijven en bewerken in het Script-venster</span><span class="sxs-lookup"><span data-stu-id="168c3-139">How to write and edit text in the Script Pane</span></span>

<span data-ttu-id="168c3-140">U kunt tekst kopiëren, knippen, plakken, zoeken en vervangen in het Script-venster.</span><span class="sxs-lookup"><span data-stu-id="168c3-140">You can copy, cut, paste, find, and replace text in the Script Pane.</span></span> <span data-ttu-id="168c3-141">U kunt ook de laatste actie die u zojuist hebt uitgevoerd, ongedaan maken en opnieuw uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="168c3-141">You can also undo and redo the last action you just performed.</span></span> <span data-ttu-id="168c3-142">De sneltoetsen voor deze acties zijn dezelfde snelkoppelingen die worden gebruikt voor alle Windows-toepassingen.</span><span class="sxs-lookup"><span data-stu-id="168c3-142">The keyboard shortcuts for these actions are the same shortcuts used for all Windows applications.</span></span>

### <a name="to-enter-text-in-the-script-pane"></a><span data-ttu-id="168c3-143">Tekst in het Script-venster invoeren</span><span class="sxs-lookup"><span data-stu-id="168c3-143">To enter text in the Script Pane</span></span>

1. <span data-ttu-id="168c3-144">Verplaats de cursor naar het deel venster script door ergens in het Script venster te klikken of door te klikken op **naar script deel venster** in het menu **beeld** .</span><span class="sxs-lookup"><span data-stu-id="168c3-144">Move the cursor to the Script Pane by clicking anywhere in the Script Pane, or by clicking **Go to Script Pane** in the **View** menu.</span></span>
2. <span data-ttu-id="168c3-145">Een script maken.</span><span class="sxs-lookup"><span data-stu-id="168c3-145">Create a script.</span></span> <span data-ttu-id="168c3-146">Syntaxis kleuren en tabblad voltooiing bieden een uitgebreidere bewerkings ervaring in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="168c3-146">Syntax coloring and tab completion provide a richer editing experience in Windows PowerShell ISE.</span></span>
3. <span data-ttu-id="168c3-147">Zie [Tab-aanvulling gebruiken in het Script venster en console venster](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) voor meer informatie over het gebruik van de functie voor het volt ooien van tabs om te helpen bij het typen van.</span><span class="sxs-lookup"><span data-stu-id="168c3-147">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for details about using the tab completion feature to help in typing.</span></span>

### <a name="to-find-text-in-the-script-pane"></a><span data-ttu-id="168c3-148">Tekst in het Script-venster zoeken</span><span class="sxs-lookup"><span data-stu-id="168c3-148">To find text in the Script Pane</span></span>

1. <span data-ttu-id="168c3-149">Als u tekst overal wilt zoeken, drukt u op <kbd>CTRL</kbd>+<kbd>F</kbd> of klikt u in het menu **bewerken** op **Zoeken in script**.</span><span class="sxs-lookup"><span data-stu-id="168c3-149">To find text anywhere, press <kbd>CTRL</kbd>+<kbd>F</kbd> or, on the **Edit** menu, click **Find in Script**.</span></span>
2. <span data-ttu-id="168c3-150">Als u tekst na de cursor wilt zoeken, drukt u op <kbd>F3</kbd> of klikt u in het menu **bewerken** op **Volgende zoeken in script**.</span><span class="sxs-lookup"><span data-stu-id="168c3-150">To find text after the cursor, press <kbd>F3</kbd> or, on the **Edit** menu, click **Find Next in Script**.</span></span>
3. <span data-ttu-id="168c3-151">Als u tekst wilt zoeken vóór de cursor, drukt u op <kbd>SHIFT</kbd>+<kbd>F3</kbd> of klikt u in het menu **bewerken** op **Vorige zoeken in script**.</span><span class="sxs-lookup"><span data-stu-id="168c3-151">To find text before the cursor, press <kbd>SHIFT</kbd>+<kbd>F3</kbd> or, on the **Edit** menu, click **Find Previous in Script**.</span></span>

### <a name="to-find-and-replace-text-in-the-script-pane"></a><span data-ttu-id="168c3-152">Tekst in het Script-venster zoeken en vervangen</span><span class="sxs-lookup"><span data-stu-id="168c3-152">To find and replace text in the Script Pane</span></span>

<span data-ttu-id="168c3-153">Druk op <kbd>CTRL</kbd>+<kbd>H</kbd> of Klik in het menu **bewerken** op **vervangen in script**.</span><span class="sxs-lookup"><span data-stu-id="168c3-153">Press <kbd>CTRL</kbd>+<kbd>H</kbd> or, on the **Edit** menu, click **Replace in Script**.</span></span> <span data-ttu-id="168c3-154">Voer de tekst in die u wilt zoeken en de vervangende tekst en druk vervolgens op <kbd>Enter</kbd>.</span><span class="sxs-lookup"><span data-stu-id="168c3-154">Enter the text you want to find and the replacement text, then press <kbd>ENTER</kbd>.</span></span>

### <a name="to-go-to-a-particular-line-of-text-in-the-script-pane"></a><span data-ttu-id="168c3-155">Naar een bepaalde tekst regel in het Script-venster gaan</span><span class="sxs-lookup"><span data-stu-id="168c3-155">To go to a particular line of text in the Script Pane</span></span>

1. <span data-ttu-id="168c3-156">Druk in het deel venster script op <kbd>CTRL</kbd>+<kbd>G</kbd> of Klik in het menu **bewerken** op **Ga naar regel**.</span><span class="sxs-lookup"><span data-stu-id="168c3-156">In the Script Pane, press <kbd>CTRL</kbd>+<kbd>G</kbd> or, on the **Edit** menu, click **Go to Line**.</span></span>

2. <span data-ttu-id="168c3-157">Voer een regel nummer in.</span><span class="sxs-lookup"><span data-stu-id="168c3-157">Enter a line number.</span></span>

### <a name="to-copy-text-in-the-script-pane"></a><span data-ttu-id="168c3-158">Tekst in het Script venster kopiëren</span><span class="sxs-lookup"><span data-stu-id="168c3-158">To copy text in the Script Pane</span></span>

1. <span data-ttu-id="168c3-159">Selecteer in het deel venster script de tekst die u wilt kopiëren.</span><span class="sxs-lookup"><span data-stu-id="168c3-159">In the Script Pane, select the text that you want to copy.</span></span>

2. <span data-ttu-id="168c3-160">Druk op <kbd>CTRL</kbd>+<kbd>C</kbd> of klik op de werk balk op het pictogram **kopiëren** of Klik in het menu **bewerken** op **kopiëren**.</span><span class="sxs-lookup"><span data-stu-id="168c3-160">Press <kbd>CTRL</kbd>+<kbd>C</kbd> or, on the toolbar, click the **Copy** icon, or on the **Edit** menu, click **Copy**.</span></span>

### <a name="to-cut-text-in-the-script-pane"></a><span data-ttu-id="168c3-161">Tekst in het Script-venster knippen</span><span class="sxs-lookup"><span data-stu-id="168c3-161">To cut text in the Script Pane</span></span>

1. <span data-ttu-id="168c3-162">Selecteer in het deel venster script de tekst die u wilt knippen.</span><span class="sxs-lookup"><span data-stu-id="168c3-162">In the Script Pane, select the text that you want to cut.</span></span>
2. <span data-ttu-id="168c3-163">Druk op <kbd>CTRL</kbd>+<kbd>X</kbd> of Klik in de werk balk op het pictogram voor **knippen** of Klik in het menu **bewerken** op **knippen**.</span><span class="sxs-lookup"><span data-stu-id="168c3-163">Press <kbd>CTRL</kbd>+<kbd>X</kbd> or, on the toolbar, click the **Cut** icon, or on the **Edit** menu, click **Cut**.</span></span>

### <a name="to-paste-text-into-the-script-pane"></a><span data-ttu-id="168c3-164">Tekst in het Script-venster plakken</span><span class="sxs-lookup"><span data-stu-id="168c3-164">To paste text into the Script Pane</span></span>

<span data-ttu-id="168c3-165">Druk op <kbd>CTRL</kbd>+<kbd>V</kbd> of klik op de werk balk op het pictogram **Plakken** of Klik in het menu **bewerken** op **Plakken**.</span><span class="sxs-lookup"><span data-stu-id="168c3-165">Press <kbd>CTRL</kbd>+<kbd>V</kbd> or, on the toolbar, click the **Paste** icon, or on the **Edit** menu, click **Paste**.</span></span>

### <a name="to-undo-an-action-in-the-script-pane"></a><span data-ttu-id="168c3-166">Een actie in het Script venster ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="168c3-166">To undo an action in the Script Pane</span></span>

<span data-ttu-id="168c3-167">Druk op <kbd>CTRL</kbd>+<kbd>Z</kbd> of klik op de werk balk op het pictogram **ongedaan maken** of Klik in het menu **bewerken** op **ongedaan maken**.</span><span class="sxs-lookup"><span data-stu-id="168c3-167">Press <kbd>CTRL</kbd>+<kbd>Z</kbd> or, on the toolbar, click the **Undo** icon, or on the **Edit** menu, click **Undo**.</span></span>

### <a name="to-redo-an-action-in-the-script-pane"></a><span data-ttu-id="168c3-168">Een actie opnieuw uitvoeren in het deel venster script</span><span class="sxs-lookup"><span data-stu-id="168c3-168">To redo an action in the Script Pane</span></span>

<span data-ttu-id="168c3-169">Druk op <kbd>CTRL</kbd>+<kbd>Y</kbd> of klik op de werk balk op het pictogram **opnieuw uitvoeren** of Klik in het menu **bewerken** op **opnieuw**.</span><span class="sxs-lookup"><span data-stu-id="168c3-169">Press <kbd>CTRL</kbd>+<kbd>Y</kbd> or, on the toolbar, click the **Redo** icon, or on the **Edit** menu, click **Redo**.</span></span>

## <a name="how-to-save-a-script"></a><span data-ttu-id="168c3-170">Een script opslaan</span><span class="sxs-lookup"><span data-stu-id="168c3-170">How to save a script</span></span>

<span data-ttu-id="168c3-171">Er wordt een sterretje naast de naam van het script weer gegeven om een bestand te markeren dat niet is opgeslagen sinds het is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="168c3-171">An asterisk appears next to the script name to mark a file that hasn't been saved since it was changed.</span></span> <span data-ttu-id="168c3-172">Het sterretje verdwijnt wanneer het bestand wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="168c3-172">The asterisk disappears when the file is saved.</span></span>

### <a name="to-save-a-script"></a><span data-ttu-id="168c3-173">Een script opslaan</span><span class="sxs-lookup"><span data-stu-id="168c3-173">To save a script</span></span>

<span data-ttu-id="168c3-174">Druk op <kbd>CTRL</kbd>+<kbd>S</kbd> of klik op de werk balk op het pictogram **Opslaan** of Klik in het menu **bestand** op **Opslaan**.</span><span class="sxs-lookup"><span data-stu-id="168c3-174">Press <kbd>CTRL</kbd>+<kbd>S</kbd> or, on the toolbar, click the **Save** icon, or on the **File** menu, click **Save**.</span></span>

### <a name="to-save-and-name-a-script"></a><span data-ttu-id="168c3-175">Een script opslaan en een naam schrijven</span><span class="sxs-lookup"><span data-stu-id="168c3-175">To save and name a script</span></span>

1. <span data-ttu-id="168c3-176">Klik in het menu **bestand** op **Opslaan als**.</span><span class="sxs-lookup"><span data-stu-id="168c3-176">On the **File** menu, click **Save As**.</span></span> <span data-ttu-id="168c3-177">Het dialoog venster **Opslaan als** wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="168c3-177">The **Save As** dialog box will appear.</span></span>
2. <span data-ttu-id="168c3-178">Voer in het vak **Bestands naam** een naam in voor het bestand.</span><span class="sxs-lookup"><span data-stu-id="168c3-178">In the **File name** box, enter a name for the file.</span></span>
3. <span data-ttu-id="168c3-179">Selecteer een bestands type in het vak **Opslaan als type** .</span><span class="sxs-lookup"><span data-stu-id="168c3-179">In the **Save as type** box, select a file type.</span></span> <span data-ttu-id="168c3-180">Selecteer bijvoorbeeld Power shell-scripts (`*.ps1`) in het vak **Opslaan als type** .</span><span class="sxs-lookup"><span data-stu-id="168c3-180">For example, in the **Save as type** box, select 'PowerShell Scripts (`*.ps1`)'.</span></span>
4. <span data-ttu-id="168c3-181">Klik op **Opslaan**.</span><span class="sxs-lookup"><span data-stu-id="168c3-181">Click **Save**.</span></span>

### <a name="to-save-a-script-in-ascii-encoding"></a><span data-ttu-id="168c3-182">Een script in ASCII-code ring opslaan</span><span class="sxs-lookup"><span data-stu-id="168c3-182">To save a script in ASCII encoding</span></span>

<span data-ttu-id="168c3-183">Windows PowerShell ISE slaat standaard nieuwe script bestanden (`.ps1`), script gegevensbestand (`.psd1`) en script module bestanden (`.psm1`) standaard op als Unicode (BigEndianUnicode).</span><span class="sxs-lookup"><span data-stu-id="168c3-183">By default, Windows PowerShell ISE saves new script files (`.ps1`), script data files (`.psd1`), and script module files (`.psm1`) as Unicode (BigEndianUnicode) by default.</span></span> <span data-ttu-id="168c3-184">Als u een script wilt opslaan in een andere code ring, zoals ASCII (ANSI), gebruikt u de methoden **Save** of **SaveAs** in het object [$psISE. CurrentFile](object-model/the-ise-object-model-hierarchy.md) .</span><span class="sxs-lookup"><span data-stu-id="168c3-184">To save a script in another encoding, such as ASCII (ANSI), use the **Save** or **SaveAs** methods on the [$psISE.CurrentFile](object-model/the-ise-object-model-hierarchy.md) object.</span></span>

<span data-ttu-id="168c3-185">Met de volgende opdracht wordt een nieuw script opgeslagen als MyScript. ps1 met ASCII-code ring.</span><span class="sxs-lookup"><span data-stu-id="168c3-185">The following command saves a new script as MyScript.ps1 with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.SaveAs("MyScript.ps1", [System.Text.Encoding]::ASCII)
```

<span data-ttu-id="168c3-186">Met de volgende opdracht wordt het huidige script bestand vervangen door een bestand met dezelfde naam, maar met ASCII-code ring.</span><span class="sxs-lookup"><span data-stu-id="168c3-186">The following command replaces the current script file with a file with the same name, but with ASCII encoding.</span></span>

```powershell
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)
```

<span data-ttu-id="168c3-187">Met de volgende opdracht wordt de code ring van het huidige bestand opgehaald.</span><span class="sxs-lookup"><span data-stu-id="168c3-187">The following command gets the encoding of the current file.</span></span>

```powershell
$psISE.CurrentFile.encoding
```

<span data-ttu-id="168c3-188">Windows PowerShell ISE ondersteunt de volgende coderings opties: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8 en default.</span><span class="sxs-lookup"><span data-stu-id="168c3-188">Windows PowerShell ISE supports the following encoding options: ASCII, BigEndianUnicode, Unicode, UTF32, UTF7, UTF8, and Default.</span></span> <span data-ttu-id="168c3-189">De waarde van de standaard optie is afhankelijk van het systeem.</span><span class="sxs-lookup"><span data-stu-id="168c3-189">The value of the Default option varies with the system.</span></span>

<span data-ttu-id="168c3-190">Windows PowerShell ISE wijzigt de code ring van script bestanden niet wanneer u de opdrachten opslaan of opslaan als gebruikt.</span><span class="sxs-lookup"><span data-stu-id="168c3-190">Windows PowerShell ISE doesn't change the encoding of script files when you use the Save or Save As commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="168c3-191">Zie ook</span><span class="sxs-lookup"><span data-stu-id="168c3-191">See Also</span></span>

- [<span data-ttu-id="168c3-192">Kennismaking met Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="168c3-192">Exploring the Windows PowerShell ISE</span></span>](exploring-the-windows-powershell-ise.md)
