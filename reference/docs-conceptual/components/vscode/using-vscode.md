---
title: Visual Studio code for Power Shell Development gebruiken
description: Visual Studio code for Power Shell Development gebruiken
ms.date: 11/07/2019
ms.openlocfilehash: 86739970b58460bef9686a75bf0604d0605d4888
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082443"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="7078a-103">Visual Studio code for Power Shell Development gebruiken</span><span class="sxs-lookup"><span data-stu-id="7078a-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="7078a-104">[Visual Studio code](https://code.visualstudio.com/) is een cross-platform (Windows, MacOS en Linux) script editor van micro soft.</span><span class="sxs-lookup"><span data-stu-id="7078a-104">[Visual Studio Code](https://code.visualstudio.com/) is a cross-platform (Windows, macOS, and Linux) script editor by Microsoft.</span></span> <span data-ttu-id="7078a-105">Samen met de [Power shell-extensie](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell)biedt het een uitgebreide en interactieve script bewerking, waardoor het eenvoudiger is om betrouw bare Power shell-scripts te schrijven.</span><span class="sxs-lookup"><span data-stu-id="7078a-105">Together with the [the PowerShell extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span>

<span data-ttu-id="7078a-106">Visual Studio code met de Power shell-extensie is de aanbevolen editor voor het schrijven van Power shell-scripts.</span><span class="sxs-lookup"><span data-stu-id="7078a-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>
<span data-ttu-id="7078a-107">Het ondersteunt de volgende Power shell-versies:</span><span class="sxs-lookup"><span data-stu-id="7078a-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="7078a-108">Power shell 7 en up</span><span class="sxs-lookup"><span data-stu-id="7078a-108">PowerShell 7 and up</span></span>
- <span data-ttu-id="7078a-109">Power shell Core 6</span><span class="sxs-lookup"><span data-stu-id="7078a-109">PowerShell Core 6</span></span>
- <span data-ttu-id="7078a-110">Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="7078a-110">Windows PowerShell 5.1</span></span>

<span data-ttu-id="7078a-111">Controleer voordat u begint of Power shell op het systeem bestaat.</span><span class="sxs-lookup"><span data-stu-id="7078a-111">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="7078a-112">Raadpleeg de volgende koppelingen voor moderne werk belastingen op Windows, macOS en Linux:</span><span class="sxs-lookup"><span data-stu-id="7078a-112">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="7078a-113">[Installing PowerShell Core on Linux][install-pscore-linux] (PowerShell Core installeren in Linux)</span><span class="sxs-lookup"><span data-stu-id="7078a-113">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="7078a-114">[Installing PowerShell Core on macOS][install-pscore-macos] (PowerShell Core installeren in macOS)</span><span class="sxs-lookup"><span data-stu-id="7078a-114">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="7078a-115">[Power shell Core installeren in Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="7078a-115">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="7078a-116">Zie [Windows Power Shell installeren][install-winps]voor traditionele workloads van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="7078a-116">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!NOTE]
> <span data-ttu-id="7078a-117">Visual Studio code is niet hetzelfde als [Visual Studio](https://visualstudio.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="7078a-117">Visual Studio Code is not the same as [Visual Studio](https://visualstudio.microsoft.com/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7078a-118">De [Windows PowerShell ISE][ise] is ook nog steeds beschikbaar voor Windows, maar is niet langer in het ontwikkelen van actieve functies en werkt niet met Power shell 7 en up of Power shell Core 6.</span><span class="sxs-lookup"><span data-stu-id="7078a-118">The [Windows PowerShell ISE][ise] is also still available for Windows, however, it is no longer in active feature development and does not work with PowerShell 7 and up or PowerShell Core 6.</span></span>
> <span data-ttu-id="7078a-119">Als onderdeel van Windows-verzen ding wordt het officieel ondersteund voor beveiligings updates en onderhoud met hoge prioriteit.</span><span class="sxs-lookup"><span data-stu-id="7078a-119">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span> <span data-ttu-id="7078a-120">Er zijn momenteel geen abonnementen om de ISE van Windows te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="7078a-120">We currently have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="7078a-121">Bewerken met Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="7078a-121">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="7078a-122">Installeer Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="7078a-122">Install Visual Studio Code.</span></span> <span data-ttu-id="7078a-123">Zie voor meer informatie het overzicht instellen [van Visual Studio code](https://code.visualstudio.com/Docs/setup/setup-overview).</span><span class="sxs-lookup"><span data-stu-id="7078a-123">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

    <span data-ttu-id="7078a-124">Er zijn installatie-instructies voor elk platform:</span><span class="sxs-lookup"><span data-stu-id="7078a-124">There are installation instructions for each platform:</span></span>

    - <span data-ttu-id="7078a-125">**Windows**: Volg de installatie-instructies op de pagina [Visual Studio code uitvoeren op Windows](https://code.visualstudio.com/docs/setup/windows) .</span><span class="sxs-lookup"><span data-stu-id="7078a-125">**Windows**: follow the installation instructions on the [Running Visual Studio Code on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>
    - <span data-ttu-id="7078a-126">**macOS**: Volg de installatie-instructies op de pagina [Visual Studio code uitvoeren op MacOS](https://code.visualstudio.com/docs/setup/mac) .</span><span class="sxs-lookup"><span data-stu-id="7078a-126">**macOS**: follow the installation instructions on the [Running Visual Studio Code on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>
    - <span data-ttu-id="7078a-127">**Linux**: Volg de installatie-instructies op de pagina [Visual Studio code uitvoeren op Linux](https://code.visualstudio.com/docs/setup/linux) .</span><span class="sxs-lookup"><span data-stu-id="7078a-127">**Linux**: follow the installation instructions on the [Running Visual Studio Code on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>

1. <span data-ttu-id="7078a-128">Installeer de Power shell-extensie.</span><span class="sxs-lookup"><span data-stu-id="7078a-128">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="7078a-129">Start de app Visual Studio code door `code` te typen in een-console of `code-insiders` als u Visual Studio code insiders hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7078a-129">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="7078a-130">Start **snel openen** in Windows of Linux door op <kbd>CTRL</kbd>+<kbd>P</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="7078a-130">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="7078a-131">Druk in macOS op <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7078a-131">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="7078a-132">Typ `ext install powershell` in snel openen en druk op **Enter**.</span><span class="sxs-lookup"><span data-stu-id="7078a-132">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="7078a-133">De weer gave **extensies** wordt weer gegeven op de balk aan de zijkant.</span><span class="sxs-lookup"><span data-stu-id="7078a-133">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="7078a-134">Selecteer de Power shell-extensie van micro soft.</span><span class="sxs-lookup"><span data-stu-id="7078a-134">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="7078a-135">Er wordt een Visual Studio-code scherm weer gegeven dat vergelijkbaar is met de volgende afbeelding:</span><span class="sxs-lookup"><span data-stu-id="7078a-135">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. <span data-ttu-id="7078a-137">Klik op de knop **installeren** in de Power shell-extensie van micro soft.</span><span class="sxs-lookup"><span data-stu-id="7078a-137">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="7078a-138">Als u na de installatie de knop **installeren** ziet, klikt u **op opnieuw** **laden**.</span><span class="sxs-lookup"><span data-stu-id="7078a-138">After the install, if you see the **Install** button turn into **Reload**, Click on **Reload**.</span></span>
   1. <span data-ttu-id="7078a-139">Nadat Visual Studio code opnieuw is geladen, bent u klaar om te bewerken.</span><span class="sxs-lookup"><span data-stu-id="7078a-139">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="7078a-140">Als u bijvoorbeeld een nieuw bestand wilt maken, klikt u op **bestand > nieuw**.</span><span class="sxs-lookup"><span data-stu-id="7078a-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="7078a-141">Als u deze wilt opslaan, klikt u op **bestand > opslaan** en geeft u een bestands naam op, zoals `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="7078a-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="7078a-142">Als u het bestand wilt sluiten, klikt u op de `X` naast de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="7078a-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="7078a-143">Als u Visual Studio code wilt afsluiten, wordt het **bestand > sluiten**.</span><span class="sxs-lookup"><span data-stu-id="7078a-143">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="7078a-144">De Power shell-uitbrei ding installeren op beperkte systemen</span><span class="sxs-lookup"><span data-stu-id="7078a-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="7078a-145">Sommige systemen zijn zodanig ingesteld dat alle code handtekeningen moeten worden gecontroleerd en hiervoor moeten de services van Power shell-editor hand matig worden goedgekeurd om te worden uitgevoerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="7078a-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="7078a-146">Een groepsbeleid update die het uitvoerings beleid wijzigt, is waarschijnlijk een mogelijke oorzaak als u de Power shell-uitbrei ding hebt geïnstalleerd, maar er wordt een fout bericht ontvangen zoals:</span><span class="sxs-lookup"><span data-stu-id="7078a-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="7078a-147">Open een Power shell-prompt en voer de volgende opdracht uit om de Power shell editor-Services en de Power shell-extensie voor Visual Studio code hand matig goed te keuren:</span><span class="sxs-lookup"><span data-stu-id="7078a-147">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="7078a-148">U wordt gevraagd of **u software van deze niet-vertrouwde uitgever wilt uitvoeren?**</span><span class="sxs-lookup"><span data-stu-id="7078a-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span>
<span data-ttu-id="7078a-149">Typ `A` om het bestand uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="7078a-149">Type `A` to run the file.</span></span> <span data-ttu-id="7078a-150">Open vervolgens Visual Studio code en controleer of de Power shell-extensie goed werkt.</span><span class="sxs-lookup"><span data-stu-id="7078a-150">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="7078a-151">Als u nog steeds problemen ondervindt, laat het ons dan weten op [github](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="7078a-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

> [!NOTE]
> <span data-ttu-id="7078a-152">De Power shell-extensie voor Visual Studio code biedt geen ondersteuning voor uitvoering in een modus met beperkte taal.</span><span class="sxs-lookup"><span data-stu-id="7078a-152">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="7078a-153">Raadpleeg de GitHub voor het [bijhouden van problemen die ondersteuning biedt](https://github.com/PowerShell/vscode-powershell/issues/606) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7078a-153">Please see the [GitHub issue tracking that support](https://github.com/PowerShell/vscode-powershell/issues/606) for more information.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="7078a-154">Een oudere versie van de Power shell-uitbrei ding voor Windows Power Shell v3 en v4 gebruiken</span><span class="sxs-lookup"><span data-stu-id="7078a-154">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="7078a-155">Hoewel de huidige Power shell-uitbrei ding het [ondersteunen van v3 en v4 heeft gestopt](https://github.com/PowerShell/vscode-powershell/issues/1310), kunt u nog steeds de laatste versie van de uitbrei ding gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7078a-155">Although the current PowerShell extension [stopped supporting v3 and v4](https://github.com/PowerShell/vscode-powershell/issues/1310), you can still use the last version of the extension that did.</span></span>

> [!NOTE]
> <span data-ttu-id="7078a-156">Er zijn geen aanvullende oplossingen voor deze oudere versie van de uitbrei ding.</span><span class="sxs-lookup"><span data-stu-id="7078a-156">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="7078a-157">Het wordt weer gegeven als IS, maar is beschikbaar voor u als u nog steeds Windows Power Shell v3 en Windows Power shell v4 gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7078a-157">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="7078a-158">Open eerst het deel venster uitbrei ding en zoek naar `PowerShell`.</span><span class="sxs-lookup"><span data-stu-id="7078a-158">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="7078a-159">Klik vervolgens op het vistuig en selecteer **een andere versie installeren...** .</span><span class="sxs-lookup"><span data-stu-id="7078a-159">Then click the gear and select **Install another version...**.</span></span>

![Een andere versie installeren...](media/using-vscode/install-another-version.png)

<span data-ttu-id="7078a-161">Selecteer vervolgens de **`2020.1.0`** versie.</span><span class="sxs-lookup"><span data-stu-id="7078a-161">Then select the **`2020.1.0`** version.</span></span> <span data-ttu-id="7078a-162">Deze versie van de uitbrei ding is de laatste versie voor de ondersteuning van v3 en v4.</span><span class="sxs-lookup"><span data-stu-id="7078a-162">This version of the extension was the last version to support v3 and v4.</span></span>

<span data-ttu-id="7078a-163">Voeg ook de volgende instelling toe zodat uw extensie versie niet automatisch wordt bijgewerkt:</span><span class="sxs-lookup"><span data-stu-id="7078a-163">Also, add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="7078a-164">Hoewel dit in de forseeable toekomst werkt, kan Visual Studio code een wijziging implementeren waardoor deze versie van de uitbrei ding wordt verbroken.</span><span class="sxs-lookup"><span data-stu-id="7078a-164">Although this will work in the forseeable future, Visual Studio Code could implement a change that breaks this version of the extension.</span></span>
<span data-ttu-id="7078a-165">Als gevolg van deze en het ontbreken van ondersteuning raden wij u ten zeerste aan:</span><span class="sxs-lookup"><span data-stu-id="7078a-165">Because of this, and lack of support, we highly recommend either:</span></span>

- <span data-ttu-id="7078a-166">Power shell 7 downloaden: dit is een side-by-side installatie van Windows Power shell en werkt het beste met de Power shell-extensie</span><span class="sxs-lookup"><span data-stu-id="7078a-166">Downloading PowerShell 7 - which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>
- <span data-ttu-id="7078a-167">Upgraden naar Windows Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="7078a-167">Upgrading to Windows PowerShell 5.1</span></span>

<span data-ttu-id="7078a-168">De sectie [Editing with Visual Studio code](#editing-with-visual-studio-code) in dit artikel is een koppeling naar waar u deze kunt installeren.</span><span class="sxs-lookup"><span data-stu-id="7078a-168">The [Editing with Visual Studio Code](#editing-with-visual-studio-code) section in this article links to where to install these.</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="7078a-169">Een versie van Power shell kiezen die moet worden gebruikt met de extensie</span><span class="sxs-lookup"><span data-stu-id="7078a-169">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="7078a-170">Met Power shell core die naast Windows Power shell wordt geïnstalleerd, is het nu mogelijk om een bepaalde versie van Power shell te gebruiken met de Power shell-extensie.</span><span class="sxs-lookup"><span data-stu-id="7078a-170">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="7078a-171">Gebruik de volgende stappen om de versie te kiezen:</span><span class="sxs-lookup"><span data-stu-id="7078a-171">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="7078a-172">Open het **opdracht palet** in Windows of Linux met <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7078a-172">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="7078a-173">In macOS, gebruikt u <kbd>Cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7078a-173">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="7078a-174">Zoek naar de **sessie**.</span><span class="sxs-lookup"><span data-stu-id="7078a-174">Search for **Session**.</span></span>
1. <span data-ttu-id="7078a-175">Klik op **Power shell: menu sessie weer geven**.</span><span class="sxs-lookup"><span data-stu-id="7078a-175">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="7078a-176">Kies de versie van Power shell die u wilt gebruiken in de lijst, bijvoorbeeld: **Power shell core**.</span><span class="sxs-lookup"><span data-stu-id="7078a-176">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7078a-177">Deze functie bekijkt enkele bekende paden op verschillende besturings systemen om installatie locaties van Power shell te detecteren.</span><span class="sxs-lookup"><span data-stu-id="7078a-177">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="7078a-178">Als u Power shell hebt geïnstalleerd op een niet-typische locatie, wordt deze mogelijk niet eerst weer gegeven in het menu sessie.</span><span class="sxs-lookup"><span data-stu-id="7078a-178">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="7078a-179">U kunt het menu sessie uitbreiden door [uw eigen aangepaste paden toe te voegen](#adding-your-own-powershell-paths-to-the-session-menu) , zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="7078a-179">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="7078a-180">Er is een andere manier om naar het menu sessie te gaan.</span><span class="sxs-lookup"><span data-stu-id="7078a-180">There's another way to get to the session menu.</span></span> <span data-ttu-id="7078a-181">Wanneer een Power shell-bestand is geopend in uw editor, ziet u een groen versie nummer in de rechter benedenhoek.</span><span class="sxs-lookup"><span data-stu-id="7078a-181">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="7078a-182">Als u op dit versie nummer klikt, gaat u naar het menu sessie.</span><span class="sxs-lookup"><span data-stu-id="7078a-182">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="7078a-183">Uw eigen Power shell-paden toevoegen aan het menu sessie</span><span class="sxs-lookup"><span data-stu-id="7078a-183">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="7078a-184">U kunt andere uitvoer bare Power shell-paden toevoegen aan het menu sessie via de [code-instelling van Visual Studio](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span><span class="sxs-lookup"><span data-stu-id="7078a-184">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="7078a-185">Voeg een item toe aan de lijst `powershell.powerShellAdditionalExePaths` of maak een lijst als deze niet bestaat in uw `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="7078a-185">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

<span data-ttu-id="7078a-186">Elk item moet het volgende bevatten:</span><span class="sxs-lookup"><span data-stu-id="7078a-186">Each item must have:</span></span>

- <span data-ttu-id="7078a-187">`exePath`: het pad naar de `pwsh` of `powershell` uitvoer bare bestand.</span><span class="sxs-lookup"><span data-stu-id="7078a-187">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="7078a-188">`versionName`: de tekst die wordt weer gegeven in het menu van de sessie.</span><span class="sxs-lookup"><span data-stu-id="7078a-188">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="7078a-189">U kunt de standaard-Power shell-versie instellen op het gebruik van de `powershell.powerShellDefaultVersion` instelling door dit in te stellen op de tekst die wordt weer gegeven in het menu sessie (ook wel bekend als de `versionName` in de laatste instelling):</span><span class="sxs-lookup"><span data-stu-id="7078a-189">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

<span data-ttu-id="7078a-190">Nadat u deze instelling hebt geconfigureerd, start u Visual Studio code opnieuw of laadt u het huidige venster Visual Studio-code opnieuw vanuit het **opdracht palet**, typt u **ontwikkelaar: venster opnieuw laden**.</span><span class="sxs-lookup"><span data-stu-id="7078a-190">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="7078a-191">Als u het menu sessie opent, ziet u nu uw extra Power shell-versies!</span><span class="sxs-lookup"><span data-stu-id="7078a-191">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="7078a-192">Als u Power shell bouwt vanaf een bron, is dit een fantastische manier om uw lokale build van Power shell te testen.</span><span class="sxs-lookup"><span data-stu-id="7078a-192">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="7078a-193">Configuratie-instellingen voor Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="7078a-193">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="7078a-194">Als u niet bekend bent met het wijzigen van instellingen in Visual Studio code, raden we u aan [de documentatie van de Visual Studio code-instellingen](https://code.visualstudio.com/docs/getstarted/settings)te raadplegen.</span><span class="sxs-lookup"><span data-stu-id="7078a-194">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend looking at [Visual Studio Code's settings documentation](https://code.visualstudio.com/docs/getstarted/settings).</span></span>

<span data-ttu-id="7078a-195">U kunt met behulp van de stappen in de vorige alinea configuratie-instellingen toevoegen in `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="7078a-195">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="7078a-196">Als u niet wilt dat deze instellingen van invloed zijn op alle bestands typen, kunt u met Visual Studio code ook configuraties per taal instellen.</span><span class="sxs-lookup"><span data-stu-id="7078a-196">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="7078a-197">Maak een taalspecifieke instelling door instellingen in een `[<language-name>]` veld in te voeren.</span><span class="sxs-lookup"><span data-stu-id="7078a-197">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="7078a-198">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7078a-198">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="7078a-199">Zie [informatie over bestands codering](understanding-file-encoding.md)voor meer informatie over het coderen van bestanden in Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="7078a-199">For more information about file encoding in Visual Studio Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>
>
> <span data-ttu-id="7078a-200">Lees ook de [informatie over het repliceren van de ISE-ervaring in Visual Studio code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) voor andere tips over het configureren van Visual Studio code voor het bewerken van Power shell.</span><span class="sxs-lookup"><span data-stu-id="7078a-200">Also check out the [How to replicate the ISE experience in Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md) for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="7078a-201">Fout opsporing met Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="7078a-201">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="7078a-202">Geen-werk ruimte: fout opsporing</span><span class="sxs-lookup"><span data-stu-id="7078a-202">No-workspace debugging</span></span>

<span data-ttu-id="7078a-203">Vanaf Visual Studio code versie 1,9 kunt u fouten opsporen in Power shell-scripts zonder de map met het Power shell-script te openen.</span><span class="sxs-lookup"><span data-stu-id="7078a-203">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="7078a-204">Open het Power shell-script bestand met het **bestand > bestand openen...** , stel een onderbrekings punt in op een regel, druk op <kbd>F9</kbd>en druk vervolgens op <kbd>F5</kbd> om de fout opsporing te starten.</span><span class="sxs-lookup"><span data-stu-id="7078a-204">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="7078a-205">Het deel venster acties voor fout opsporing wordt weer gegeven, waarin u de fout opsporing kunt opdelen, stap, CV en stoppen.</span><span class="sxs-lookup"><span data-stu-id="7078a-205">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="7078a-206">Fout opsporing voor werk ruimten</span><span class="sxs-lookup"><span data-stu-id="7078a-206">Workspace debugging</span></span>

<span data-ttu-id="7078a-207">Fout opsporing voor werk ruimten verwijst naar fout opsporing in de context van een map die u hebt geopend in Visual Studio code vanuit het menu **bestand** met **open map...** . De map die u opent, is doorgaans uw Power shell-projectmap en/of de hoofdmap van uw Git-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="7078a-207">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="7078a-208">Zelfs in deze modus kunt u de fout opsporing van het momenteel geselecteerde Power shell-script starten door op <kbd>F5</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="7078a-208">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="7078a-209">Met fout opsporing in werk ruimten kunt u echter meerdere debug-configuraties definiëren, anders dan alleen fouten opsporen in het bestand dat momenteel is geopend.</span><span class="sxs-lookup"><span data-stu-id="7078a-209">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="7078a-210">We gaan alles op dit moment.</span><span class="sxs-lookup"><span data-stu-id="7078a-210">We'll get to those in a moment.</span></span>

<span data-ttu-id="7078a-211">Voer de volgende stappen uit om het configuratie bestand voor fout opsporing te maken:</span><span class="sxs-lookup"><span data-stu-id="7078a-211">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="7078a-212">Open de weer gave **fout opsporing** op Windows of Linux door op <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>te drukken.</span><span class="sxs-lookup"><span data-stu-id="7078a-212">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="7078a-213">Druk in macOS op <kbd>Cmd</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="7078a-213">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="7078a-214">Klik op de koppeling ' een launch. JSON-bestand maken '.</span><span class="sxs-lookup"><span data-stu-id="7078a-214">Click the "create a launch.json file" link.</span></span>
  1. <span data-ttu-id="7078a-215">Visual Studio code vraagt u om **omgeving te selecteren**.</span><span class="sxs-lookup"><span data-stu-id="7078a-215">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="7078a-216">Kies **Power shell**.</span><span class="sxs-lookup"><span data-stu-id="7078a-216">Choose **PowerShell**.</span></span>
  1. <span data-ttu-id="7078a-217">Kies ten slotte het type fout opsporing dat u wilt gebruiken:</span><span class="sxs-lookup"><span data-stu-id="7078a-217">Lastly, choose the type of debugging you'd like to use:</span></span>

- <span data-ttu-id="7078a-218">Het **huidige bestand starten** -starten en fouten opsporen in het bestand in het huidige venster van de editor</span><span class="sxs-lookup"><span data-stu-id="7078a-218">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
- <span data-ttu-id="7078a-219">**Script starten** : starten en fouten opsporen in opgegeven bestand of opdracht</span><span class="sxs-lookup"><span data-stu-id="7078a-219">**Launch Script** - Launch and debug the specified file or command</span></span>
- <span data-ttu-id="7078a-220">**Interactieve sessie** -opdrachten voor fout opsporing in de geïntegreerde console</span><span class="sxs-lookup"><span data-stu-id="7078a-220">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
- <span data-ttu-id="7078a-221">Het fout **opsporingsprogramma koppelen aan** een actief Power shell-hostproces</span><span class="sxs-lookup"><span data-stu-id="7078a-221">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="7078a-222">Het resultaat is dat Visual Studio code een map en een bestand `.vscode\launch.json` maakt in de hoofdmap van de map met de werk ruimte.</span><span class="sxs-lookup"><span data-stu-id="7078a-222">The result is that Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="7078a-223">Deze locatie is waar de configuratie van de fout opsporing wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="7078a-223">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="7078a-224">Als uw bestanden zich in een Git-opslag plaats bevinden, wilt u meestal het `launch.json` bestand door voeren.</span><span class="sxs-lookup"><span data-stu-id="7078a-224">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="7078a-225">De inhoud van het `launch.json` bestand zijn:</span><span class="sxs-lookup"><span data-stu-id="7078a-225">The contents of the `launch.json` file are:</span></span>

```json
{
  "version": "0.2.0",
  "configurations": [
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Launch (current file)",
          "script": "${file}",
          "args": [],
          "cwd": "${file}"
      },
      {
          "type": "PowerShell",
          "request": "attach",
          "name": "PowerShell Attach to Host Process",
          "processId": "${command.PickPSHostProcess}",
          "runspaceId": 1
      },
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Interactive Session",
          "cwd": "${workspaceRoot}"
      }
  ]
}
```

<span data-ttu-id="7078a-226">Dit bestand vertegenwoordigt de veelvoorkomende scenario's voor fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="7078a-226">This file represents the common debug scenarios.</span></span> <span data-ttu-id="7078a-227">Wanneer u dit bestand in de editor opent, ziet u een knop **Configuratie toevoegen...** .</span><span class="sxs-lookup"><span data-stu-id="7078a-227">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="7078a-228">U kunt op deze knop klikken om meer configuratie van Power Shell-fout opsporing toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="7078a-228">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="7078a-229">Een van de handig te toevoegen configuratie is **Power shell: script starten**.</span><span class="sxs-lookup"><span data-stu-id="7078a-229">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="7078a-230">Met deze configuratie kunt u een bestand opgeven met optionele argumenten die moeten worden gestart wanneer u op <kbd>F5</kbd> drukt, ongeacht welk bestand momenteel actief is in de editor.</span><span class="sxs-lookup"><span data-stu-id="7078a-230">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="7078a-231">Nadat de configuratie van de fout opsporing is ingesteld, kunt u selecteren welke configuratie u tijdens een foutopsporingssessie wilt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7078a-231">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="7078a-232">Selecteer een configuratie in de vervolg keuzelijst debug Configuration in de werk balk van de weer gave van de **fout opsporing** .</span><span class="sxs-lookup"><span data-stu-id="7078a-232">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="7078a-233">Er zijn enkele blogs die handig kunnen zijn om aan de slag te gaan met Power shell-extensie voor Visual Studio code:</span><span class="sxs-lookup"><span data-stu-id="7078a-233">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="7078a-234">[Power shell-uitbrei ding][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="7078a-234">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="7078a-235">[Power shell-scripts schrijven en fouten opsporen in Visual Studio code][debug]</span><span class="sxs-lookup"><span data-stu-id="7078a-235">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="7078a-236">[Fout opsporing van Visual Studio code guidance][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="7078a-236">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="7078a-237">[Fout opsporing in Power shell in Visual Studio code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="7078a-237">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="7078a-238">[Aan de slag met Power shell-ontwikkeling in Visual Studio code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="7078a-238">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="7078a-239">[Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="7078a-239">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="7078a-240">[Visual Studio code editing-functies voor Power shell-ontwikkeling-deel 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="7078a-240">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="7078a-241">[Fout opsporing voor Power shell-script in Visual Studio code – deel 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="7078a-241">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="7078a-242">[Fout opsporing voor Power shell-script in Visual Studio code – deel 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="7078a-242">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="7078a-243">Power shell-extensie voor Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="7078a-243">PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="7078a-244">De bron code van de Power shell-extensie vindt u op [github](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="7078a-244">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>

<span data-ttu-id="7078a-245">Als u geïnteresseerd bent in bijdragen, worden pull-aanvragen aanzienlijk gewaardeerd.</span><span class="sxs-lookup"><span data-stu-id="7078a-245">If you're interested in contributing, Pull Request are greatly appreciated.</span></span> <span data-ttu-id="7078a-246">Volg samen met de [documentatie voor ontwikkel aars op github](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) om aan de slag te gaan.</span><span class="sxs-lookup"><span data-stu-id="7078a-246">Follow along with the [developer documentation on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) to get started.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="7078a-247">Problemen met de Power shell-extensie voor Visual Studio code oplossen</span><span class="sxs-lookup"><span data-stu-id="7078a-247">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="7078a-248">Als u problemen ondervindt met het gebruik van Visual Studio code voor het ontwikkelen van Power shell-scripts, raadpleegt u de [hand leiding voor probleem oplossing op github](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span><span class="sxs-lookup"><span data-stu-id="7078a-248">If you experience any issues using Visual Studio Code for PowerShell script development, please take a look at the [troubleshooting guide on GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)</span></span>
