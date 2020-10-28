---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen in foutopsporing voor PowerShell-scripts
description: WMF 5,0 voegt nieuwe functies voor fout opsporing toe aan Windows PoowerShell.
ms.openlocfilehash: 5703343e1b85024931638e8b04a09f7208ea123c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646736"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="a24ff-104">Verbeteringen in foutopsporing voor PowerShell-scripts</span><span class="sxs-lookup"><span data-stu-id="a24ff-104">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="a24ff-105">Power shell 5,0 bevat verschillende verbeteringen voor het verbeteren van de fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="a24ff-105">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="a24ff-106">Alles onderbreken</span><span class="sxs-lookup"><span data-stu-id="a24ff-106">Break All</span></span>

<span data-ttu-id="a24ff-107">Met de Power shell-console en Power shell ISE kunt u nu opdelen in het fout opsporingsprogramma voor het uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="a24ff-107">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="a24ff-108">Dit werkt in zowel lokale als externe sessies.</span><span class="sxs-lookup"><span data-stu-id="a24ff-108">This works in both local and remote sessions.</span></span>

<span data-ttu-id="a24ff-109">Druk op <kbd>CTRL</kbd>- + <kbd>afbreek</kbd>punt in de-console.</span><span class="sxs-lookup"><span data-stu-id="a24ff-109">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="a24ff-110">Druk in ISE op <kbd>CTRL</kbd> + <kbd>B</kbd>, of gebruik de opdracht **debug-> Restore all** menu.</span><span class="sxs-lookup"><span data-stu-id="a24ff-110">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="a24ff-111">Externe fout opsporing en externe bestands bewerking in Power shell ISE</span><span class="sxs-lookup"><span data-stu-id="a24ff-111">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="a24ff-112">Met Power shell ISE kunt u nu bestanden in een externe sessie openen en bewerken door de opdracht PSEdit uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="a24ff-112">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="a24ff-113">U kunt bijvoorbeeld een bestand openen voor bewerking vanaf de opdracht regel in een externe sessie als volgt:</span><span class="sxs-lookup"><span data-stu-id="a24ff-113">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="a24ff-114">Daarnaast kunt u nu wijzigingen bewerken en opslaan in een extern bestand dat automatisch wordt geopend in Power shell ISE wanneer u een onderbrekings punt bereikt.</span><span class="sxs-lookup"><span data-stu-id="a24ff-114">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="a24ff-115">U kunt nu fouten opsporen in een script bestand dat wordt uitgevoerd op een externe computer, het bestand bewerken om een fout op te lossen en vervolgens het gewijzigde script opnieuw uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="a24ff-115">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="a24ff-116">Geavanceerde script fout opsporing</span><span class="sxs-lookup"><span data-stu-id="a24ff-116">Advanced Script Debugging</span></span>

<span data-ttu-id="a24ff-117">Er zijn nieuwe geavanceerde functies voor fout opsporing waarmee u kunt koppelen aan elk lokaal computer proces dat Power Shell heeft geladen en waarmee wille keurige runspaces in dat proces worden opgespoord.</span><span class="sxs-lookup"><span data-stu-id="a24ff-117">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="a24ff-118">Fout opsporing runs Pace</span><span class="sxs-lookup"><span data-stu-id="a24ff-118">Runspace Debugging</span></span>

<span data-ttu-id="a24ff-119">Er zijn nieuwe cmdlets toegevoegd waarmee u de huidige runspaces in een proces kunt weer geven en de Power shell-console of Power shell ISE-fout opsporingsprogramma kunt koppelen aan die runs Pace voor fout opsporing in scripts:</span><span class="sxs-lookup"><span data-stu-id="a24ff-119">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="a24ff-120">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="a24ff-120">Get-Runspace</span></span>
- <span data-ttu-id="a24ff-121">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="a24ff-121">Debug-Runspace</span></span>
- <span data-ttu-id="a24ff-122">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="a24ff-122">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="a24ff-123">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="a24ff-123">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="a24ff-124">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="a24ff-124">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="a24ff-125">Koppelen aan proces hosting-Power shell</span><span class="sxs-lookup"><span data-stu-id="a24ff-125">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="a24ff-126">U kunt nu koppelen aan elk computer proces dat Power Shell heeft geladen.</span><span class="sxs-lookup"><span data-stu-id="a24ff-126">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="a24ff-127">U doet dit door in te voeren in een interactieve sessie met het hostproces.</span><span class="sxs-lookup"><span data-stu-id="a24ff-127">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="a24ff-128">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="a24ff-128">For more information, see:</span></span>

- [<span data-ttu-id="a24ff-129">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="a24ff-129">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="a24ff-130">Afsluiten-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="a24ff-130">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
