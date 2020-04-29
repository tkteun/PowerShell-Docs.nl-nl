---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen in foutopsporing voor PowerShell-scripts
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71145178"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="66d57-103">Verbeteringen in foutopsporing voor PowerShell-scripts</span><span class="sxs-lookup"><span data-stu-id="66d57-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="66d57-104">Power shell 5,0 bevat verschillende verbeteringen voor het verbeteren van de fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="66d57-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="66d57-105">Alles onderbreken</span><span class="sxs-lookup"><span data-stu-id="66d57-105">Break All</span></span>

<span data-ttu-id="66d57-106">Met de Power shell-console en Power shell ISE kunt u nu opdelen in het fout opsporingsprogramma voor het uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="66d57-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="66d57-107">Dit werkt in zowel lokale als externe sessies.</span><span class="sxs-lookup"><span data-stu-id="66d57-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="66d57-108">Druk op <kbd>CTRL</kbd>+-<kbd>afbreek</kbd>punt in de-console.</span><span class="sxs-lookup"><span data-stu-id="66d57-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="66d57-109">Druk in ISE op <kbd>CTRL</kbd>+<kbd>B</kbd>, of gebruik de opdracht **debug-> Restore all** menu.</span><span class="sxs-lookup"><span data-stu-id="66d57-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="66d57-110">Externe fout opsporing en externe bestands bewerking in Power shell ISE</span><span class="sxs-lookup"><span data-stu-id="66d57-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="66d57-111">Met Power shell ISE kunt u nu bestanden in een externe sessie openen en bewerken door de opdracht PSEdit uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="66d57-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="66d57-112">U kunt bijvoorbeeld een bestand openen voor bewerking vanaf de opdracht regel in een externe sessie als volgt:</span><span class="sxs-lookup"><span data-stu-id="66d57-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="66d57-113">Daarnaast kunt u nu wijzigingen bewerken en opslaan in een extern bestand dat automatisch wordt geopend in Power shell ISE wanneer u een onderbrekings punt bereikt.</span><span class="sxs-lookup"><span data-stu-id="66d57-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="66d57-114">U kunt nu fouten opsporen in een script bestand dat wordt uitgevoerd op een externe computer, het bestand bewerken om een fout op te lossen en vervolgens het gewijzigde script opnieuw uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="66d57-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="66d57-115">Geavanceerde script fout opsporing</span><span class="sxs-lookup"><span data-stu-id="66d57-115">Advanced Script Debugging</span></span>

<span data-ttu-id="66d57-116">Er zijn nieuwe geavanceerde functies voor fout opsporing waarmee u kunt koppelen aan elk lokaal computer proces dat Power Shell heeft geladen en waarmee wille keurige runspaces in dat proces worden opgespoord.</span><span class="sxs-lookup"><span data-stu-id="66d57-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="66d57-117">Fout opsporing runs Pace</span><span class="sxs-lookup"><span data-stu-id="66d57-117">Runspace Debugging</span></span>

<span data-ttu-id="66d57-118">Er zijn nieuwe cmdlets toegevoegd waarmee u de huidige runspaces in een proces kunt weer geven en de Power shell-console of Power shell ISE-fout opsporingsprogramma kunt koppelen aan die runs Pace voor fout opsporing in scripts:</span><span class="sxs-lookup"><span data-stu-id="66d57-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="66d57-119">Get-runs Pace</span><span class="sxs-lookup"><span data-stu-id="66d57-119">Get-Runspace</span></span>
- <span data-ttu-id="66d57-120">Fout opsporing-runs Pace</span><span class="sxs-lookup"><span data-stu-id="66d57-120">Debug-Runspace</span></span>
- <span data-ttu-id="66d57-121">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="66d57-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="66d57-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="66d57-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="66d57-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="66d57-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="66d57-124">Koppelen aan proces hosting-Power shell</span><span class="sxs-lookup"><span data-stu-id="66d57-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="66d57-125">U kunt nu koppelen aan elk computer proces dat Power Shell heeft geladen.</span><span class="sxs-lookup"><span data-stu-id="66d57-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="66d57-126">U doet dit door in te voeren in een interactieve sessie met het hostproces.</span><span class="sxs-lookup"><span data-stu-id="66d57-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="66d57-127">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="66d57-127">For more information, see:</span></span>

- [<span data-ttu-id="66d57-128">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="66d57-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="66d57-129">Afsluiten-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="66d57-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
