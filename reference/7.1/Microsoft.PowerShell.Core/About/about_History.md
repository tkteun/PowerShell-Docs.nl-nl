---
description: Hierin wordt beschreven hoe u opdrachten kunt ophalen en uitvoeren in de opdracht geschiedenis.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: 8a79690cc409919286d0f14130df72a7fe278010
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252151"
---
# <a name="about-history"></a><span data-ttu-id="01b89-104">Over geschiedenis</span><span class="sxs-lookup"><span data-stu-id="01b89-104">About History</span></span>

## <a name="short-description"></a><span data-ttu-id="01b89-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="01b89-105">Short Description</span></span>
<span data-ttu-id="01b89-106">Hierin wordt beschreven hoe u opdrachten kunt ophalen en uitvoeren in de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="01b89-106">Describes how to get and run commands in the command history.</span></span>

## <a name="long-description"></a><span data-ttu-id="01b89-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="01b89-107">Long Description</span></span>

<span data-ttu-id="01b89-108">Wanneer u een opdracht bij de opdracht prompt invoert, slaat Power shell de opdracht op in de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="01b89-108">When you enter a command at the command prompt, PowerShell saves the command in the command history.</span></span> <span data-ttu-id="01b89-109">U kunt de opdrachten in de geschiedenis gebruiken als een record van uw werk.</span><span class="sxs-lookup"><span data-stu-id="01b89-109">You can use the commands in the history as a record of your work.</span></span> <span data-ttu-id="01b89-110">En u kunt de opdrachten intrekken en uitvoeren vanuit de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="01b89-110">And, you can recall and run the commands from the command history.</span></span>

<span data-ttu-id="01b89-111">Power Shell heeft twee verschillende geschiedenis providers: de ingebouwde geschiedenis en de geschiedenis die worden beheerd door de **PSReadLine** -module.</span><span class="sxs-lookup"><span data-stu-id="01b89-111">PowerShell has two different history providers: the built-in history and the history managed by the **PSReadLine** module.</span></span> <span data-ttu-id="01b89-112">De geschiedenis wordt afzonderlijk beheerd, maar beide geschiedenissen zijn beschikbaar in sessies waarin **PSReadLine** wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="01b89-112">The histories are managed separately, but both histories are available in sessions where **PSReadLine** is loaded.</span></span>

## <a name="using-the-psreadline-history"></a><span data-ttu-id="01b89-113">De PSReadLine-geschiedenis gebruiken</span><span class="sxs-lookup"><span data-stu-id="01b89-113">Using the PSReadLine history</span></span>

<span data-ttu-id="01b89-114">De PSReadLine-geschiedenis registreert de opdrachten die worden gebruikt in alle Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="01b89-114">The PSReadLine history tracks the commands used in all PowerShell sessions.</span></span>
<span data-ttu-id="01b89-115">De geschiedenis wordt per host naar een centraal bestand geschreven.</span><span class="sxs-lookup"><span data-stu-id="01b89-115">The history is written to a central file per host.</span></span> <span data-ttu-id="01b89-116">Dat geschiedenis bestand is beschikbaar voor alle sessies en bevat alle eerdere geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="01b89-116">That history file is available to all sessions and contains all past history.</span></span> <span data-ttu-id="01b89-117">De geschiedenis wordt niet verwijderd wanneer de sessie wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="01b89-117">The history is not deleted when the session ends.</span></span> <span data-ttu-id="01b89-118">Deze geschiedenis kan ook niet worden beheerd door de- `*-History` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="01b89-118">Also, that history cannot be managed by the `*-History` cmdlets.</span></span> <span data-ttu-id="01b89-119">Zie [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="01b89-119">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

## <a name="using-the-built-in-session-history"></a><span data-ttu-id="01b89-120">De ingebouwde sessie geschiedenis gebruiken</span><span class="sxs-lookup"><span data-stu-id="01b89-120">Using the built-in session history</span></span>

<span data-ttu-id="01b89-121">Met de ingebouwde geschiedenis worden alleen de opdrachten bijgehouden die in de huidige sessie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="01b89-121">The built-in history only tracks the commands used in the current session.</span></span> <span data-ttu-id="01b89-122">De geschiedenis is niet beschikbaar voor andere sessies en wordt verwijderd wanneer de sessie wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="01b89-122">The history is not available to other sessions and is deleted when the session ends.</span></span>

### <a name="history-cmdlets"></a><span data-ttu-id="01b89-123">Geschiedenis-cmdlets</span><span class="sxs-lookup"><span data-stu-id="01b89-123">History Cmdlets</span></span>

<span data-ttu-id="01b89-124">Power Shell heeft een set cmdlets die de opdracht Geschiedenis beheren.</span><span class="sxs-lookup"><span data-stu-id="01b89-124">PowerShell has a set of cmdlets that manage the command history.</span></span>

| <span data-ttu-id="01b89-125">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="01b89-125">Cmdlet</span></span>           | <span data-ttu-id="01b89-126">Alias</span><span class="sxs-lookup"><span data-stu-id="01b89-126">Alias</span></span>  | <span data-ttu-id="01b89-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="01b89-127">Description</span></span>                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | <span data-ttu-id="01b89-128">Hiermee haalt u de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="01b89-128">Gets the command history.</span></span>                  |
| `Invoke-History` | `r`    | <span data-ttu-id="01b89-129">Hiermee voert u een opdracht uit in de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="01b89-129">Runs a command in the command history.</span></span>     |
| `Add-History`    |        | <span data-ttu-id="01b89-130">Hiermee voegt u een opdracht toe aan de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="01b89-130">Adds a command to the command history.</span></span>     |
| `Clear-History`  | `clhy` | <span data-ttu-id="01b89-131">Hiermee verwijdert u opdrachten uit de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="01b89-131">Deletes commands from the command history.</span></span> |

### <a name="keyboard-shortcuts-for-managing-history"></a><span data-ttu-id="01b89-132">Sneltoetsen voor het beheren van de geschiedenis</span><span class="sxs-lookup"><span data-stu-id="01b89-132">Keyboard Shortcuts for Managing History</span></span>

<span data-ttu-id="01b89-133">In de Power shell-console kunt u de volgende snelkoppelingen gebruiken om de opdracht geschiedenis te beheren.</span><span class="sxs-lookup"><span data-stu-id="01b89-133">In the PowerShell console, you can use the following shortcuts to manage the command history.</span></span>

- <span data-ttu-id="01b89-134"><kbd>Pijl-omhoog</kbd> : Hiermee wordt de vorige opdracht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="01b89-134"><kbd>UpArrow</kbd> - Displays the previous command.</span></span>
- <span data-ttu-id="01b89-135"><kbd>DownArrow</kbd> : de volgende opdracht wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="01b89-135"><kbd>DownArrow</kbd> - Displays the next command.</span></span>
- <span data-ttu-id="01b89-136"><kbd>F7</kbd> : Hiermee wordt de opdracht geschiedenis weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="01b89-136"><kbd>F7</kbd> - Displays the command history.</span></span>
- <span data-ttu-id="01b89-137"><kbd>ESC</kbd> : om de geschiedenis te verbergen.</span><span class="sxs-lookup"><span data-stu-id="01b89-137"><kbd>ESC</kbd> - To hide the history.</span></span>
- <span data-ttu-id="01b89-138"><kbd>F8</kbd> : Hiermee vindt u een opdracht.</span><span class="sxs-lookup"><span data-stu-id="01b89-138"><kbd>F8</kbd> - Finds a command.</span></span> <span data-ttu-id="01b89-139">Typ een of meer tekens en druk vervolgens op <kbd>F8</kbd>.</span><span class="sxs-lookup"><span data-stu-id="01b89-139">Type one or more characters then press <kbd>F8</kbd>.</span></span> <span data-ttu-id="01b89-140">Druk nogmaals op <kbd>F8</kbd> het volgende exemplaar.</span><span class="sxs-lookup"><span data-stu-id="01b89-140">Press <kbd>F8</kbd> again the next instance.</span></span>
- <span data-ttu-id="01b89-141"><kbd>F9</kbd> : een opdracht zoeken op geschiedenis-id.</span><span class="sxs-lookup"><span data-stu-id="01b89-141"><kbd>F9</kbd> - Find a command by history ID.</span></span> <span data-ttu-id="01b89-142">Typ de geschiedenis-ID en druk vervolgens op <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="01b89-142">Type the history ID then press <kbd>F9</kbd>.</span></span> <span data-ttu-id="01b89-143">Druk op <kbd>F7</kbd> om de id te vinden.</span><span class="sxs-lookup"><span data-stu-id="01b89-143">Press <kbd>F7</kbd> to find the ID.</span></span>
- <span data-ttu-id="01b89-144"><kbd>#</kbd>`<string>`</kbd><kbd>Tabblad</kbd> : Zoek de geschiedenis voor `*<string>*` en retourneert de meest recente overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="01b89-144"><kbd>#</kbd>`<string>`</kbd><kbd>Tab</kbd> - Search the history for `*<string>*` and returns the most recent match.</span></span> <span data-ttu-id="01b89-145">Als u herhaaldelijk op <kbd>Tab</kbd> drukt, worden de overeenkomende items in uw geschiedenis door lopen.</span><span class="sxs-lookup"><span data-stu-id="01b89-145">If you press <kbd>Tab</kbd> repeatedly, it cycles through the matching items in your history.</span></span>

> [!NOTE]
> <span data-ttu-id="01b89-146">Deze sleutel bindingen worden geïmplementeerd door de host-toepassing van de console.</span><span class="sxs-lookup"><span data-stu-id="01b89-146">These key bindings are implemented by the console host application.</span></span> <span data-ttu-id="01b89-147">Andere toepassingen, zoals Visual Studio code of Windows Terminal, kunnen verschillende sleutel bindingen hebben.</span><span class="sxs-lookup"><span data-stu-id="01b89-147">Other applications, such as Visual Studio Code or Windows Terminal, can have different key bindings.</span></span> <span data-ttu-id="01b89-148">De bindingen kunnen worden overschreven door de PSReadLine-module.</span><span class="sxs-lookup"><span data-stu-id="01b89-148">The bindings can be overridden by the PSReadLine module.</span></span> <span data-ttu-id="01b89-149">PSReadLine wordt automatisch geladen wanneer u een Power shell-sessie start.</span><span class="sxs-lookup"><span data-stu-id="01b89-149">PSReadLine loads automatically when you start a PowerShell session.</span></span>
> <span data-ttu-id="01b89-150">Als PSReadLine is geladen, zijn <kbd>F7</kbd> en <kbd>F9</kbd> niet gebonden aan een functie.</span><span class="sxs-lookup"><span data-stu-id="01b89-150">With PSReadLine loaded, <kbd>F7</kbd> and <kbd>F9</kbd> are not bound to any function.</span></span> <span data-ttu-id="01b89-151">PSReadLine biedt geen vergelijk bare functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="01b89-151">PSReadLine does not provide equivalent functionality.</span></span> <span data-ttu-id="01b89-152">Zie [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="01b89-152">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

### <a name="maximumhistorycount"></a><span data-ttu-id="01b89-153">MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="01b89-153">MaximumHistoryCount</span></span>

<span data-ttu-id="01b89-154">De `$MaximumHistoryCount` Voorkeurs variabele bepaalt het maximum aantal opdrachten dat door Power shell wordt opgeslagen in de opdracht geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="01b89-154">The `$MaximumHistoryCount` preference variable determines the maximum number of commands that PowerShell saves in the command history.</span></span> <span data-ttu-id="01b89-155">De standaardwaarde is </span><span class="sxs-lookup"><span data-stu-id="01b89-155">The default value is</span></span>
4096.

<span data-ttu-id="01b89-156">Met de volgende opdracht wordt bijvoorbeeld de 100- `$MaximumHistoryCount` opdrachten verkort:</span><span class="sxs-lookup"><span data-stu-id="01b89-156">For example, the following command lowers the `$MaximumHistoryCount` to 100 commands:</span></span>

```powershell
$MaximumHistoryCount = 100
```

<span data-ttu-id="01b89-157">Als u de instelling wilt Toep assen, start u Power shell opnieuw.</span><span class="sxs-lookup"><span data-stu-id="01b89-157">To apply the setting, restart PowerShell.</span></span>

<span data-ttu-id="01b89-158">Als u de nieuwe waarde voor de variabele wilt opslaan voor alle Power shell-sessies, voegt u de toewijzings instructie toe aan een Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="01b89-158">To save the new variable value for all your PowerShell sessions, add the assignment statement to a PowerShell profile.</span></span> <span data-ttu-id="01b89-159">Zie [about_Profiles](about_Profiles.md)voor meer informatie over profielen.</span><span class="sxs-lookup"><span data-stu-id="01b89-159">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="01b89-160">Zie about_Preference_Variables voor meer informatie over de `$MaximumHistoryCount` Voorkeurs variabele [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="01b89-160">For more information about the `$MaximumHistoryCount` preference variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="order-of-commands-in-the-history"></a><span data-ttu-id="01b89-161">Volg orde van opdrachten in de geschiedenis</span><span class="sxs-lookup"><span data-stu-id="01b89-161">Order of Commands in the History</span></span>

<span data-ttu-id="01b89-162">Opdrachten worden toegevoegd aan de geschiedenis wanneer de opdracht wordt uitgevoerd, niet wanneer de opdracht wordt ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="01b89-162">Commands are added to the history when the command finishes executing, not when the command is entered.</span></span> <span data-ttu-id="01b89-163">Als opdrachten enige tijd in beslag nemen of als de opdrachten worden uitgevoerd in een geneste prompt, worden de opdrachten mogelijk niet in de juiste volg orde weer gegeven in de geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="01b89-163">If commands take some time to be completed, or if the commands are executing in a nested prompt, the commands might appear to be out of order in the history.</span></span> <span data-ttu-id="01b89-164">Opdrachten die in een geneste prompt worden uitgevoerd, worden alleen uitgevoerd wanneer u het prompt niveau verlaat.</span><span class="sxs-lookup"><span data-stu-id="01b89-164">Commands that are executing in a nested prompt are completed only when you exit the prompt level.</span></span>

## <a name="see-also"></a><span data-ttu-id="01b89-165">Zie ook</span><span class="sxs-lookup"><span data-stu-id="01b89-165">See Also</span></span>

- [<span data-ttu-id="01b89-166">about_Line_Editing</span><span class="sxs-lookup"><span data-stu-id="01b89-166">about_Line_Editing</span></span>](about_Line_Editing.md)
- [<span data-ttu-id="01b89-167">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="01b89-167">about_Preference_Variables</span></span>](about_Preference_Variables.md)
- [<span data-ttu-id="01b89-168">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="01b89-168">about_Profiles</span></span>](about_Profiles.md)
- [<span data-ttu-id="01b89-169">about_Variables</span><span class="sxs-lookup"><span data-stu-id="01b89-169">about_Variables</span></span>](about_Variables.md)
- [<span data-ttu-id="01b89-170">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="01b89-170">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)

