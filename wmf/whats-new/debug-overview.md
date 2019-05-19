---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Verbeteringen in foutopsporing voor PowerShell-scripts
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856173"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="63783-103">Verbeteringen in foutopsporing voor PowerShell-scripts</span><span class="sxs-lookup"><span data-stu-id="63783-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="63783-104">PowerShell 5.0 bevat verschillende verbeteringen die het opsporen van fouten.</span><span class="sxs-lookup"><span data-stu-id="63783-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="63783-105">Alle verbreken</span><span class="sxs-lookup"><span data-stu-id="63783-105">Break All</span></span>

<span data-ttu-id="63783-106">De PowerShell-console en de PowerShell ISE nu kunt u in het foutopsporingsprogramma opsplitsen voor het uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="63783-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="63783-107">Dit werkt in zowel lokale als externe sessies.</span><span class="sxs-lookup"><span data-stu-id="63783-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="63783-108">In de console, drukt u op <kbd>Ctrl</kbd>+<kbd>verbreken</kbd>.</span><span class="sxs-lookup"><span data-stu-id="63783-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="63783-109">In ISE, drukt u op <kbd>Ctrl</kbd>+<kbd>B</kbd>, of gebruik de **Debug -> alle opsplitsen** -opdracht.</span><span class="sxs-lookup"><span data-stu-id="63783-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="63783-110">Foutopsporing op afstand en extern bestand bewerken in PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="63783-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="63783-111">PowerShell ISE kunt u nu bestanden openen en bewerken in een externe sessie met de opdracht PSEdit.</span><span class="sxs-lookup"><span data-stu-id="63783-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="63783-112">U kunt bijvoorbeeld een bestand vanaf de opdrachtregel bewerken in een externe sessie als volgt openen:</span><span class="sxs-lookup"><span data-stu-id="63783-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="63783-113">Bovendien kunt u nu bewerken en opslaan van wijzigingen in een extern bestand dat automatisch wordt geopend in PowerShell ISE wanneer u een onderbrekingspunt bereikt.</span><span class="sxs-lookup"><span data-stu-id="63783-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="63783-114">U kunt nu, fouten opsporen in een scriptbestand wordt uitgevoerd op een externe computer, het bestand te herstellen van een fout en voer het gewijzigde script bewerken.</span><span class="sxs-lookup"><span data-stu-id="63783-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="63783-115">Geavanceerde Script opsporen van fouten</span><span class="sxs-lookup"><span data-stu-id="63783-115">Advanced Script Debugging</span></span>

<span data-ttu-id="63783-116">Er zijn nieuwe, geavanceerde foutopsporing functies waarmee u kunnen koppelen aan een lokale computer-proces dat PowerShell is geladen en fouten opsporen in willekeurige runspaces in het proces.</span><span class="sxs-lookup"><span data-stu-id="63783-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="63783-117">Runspace foutopsporing</span><span class="sxs-lookup"><span data-stu-id="63783-117">Runspace Debugging</span></span>

<span data-ttu-id="63783-118">Er zijn nieuwe cmdlets zijn toegevoegd waarmee u de lijst met huidige runspaces in een proces en de PowerShell-console of de PowerShell ISE foutopsporingsprogramma koppelen aan deze runspace voor foutopsporing voor scripts kunt:</span><span class="sxs-lookup"><span data-stu-id="63783-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="63783-119">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="63783-119">Get-Runspace</span></span>
- <span data-ttu-id="63783-120">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="63783-120">Debug-Runspace</span></span>
- <span data-ttu-id="63783-121">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="63783-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="63783-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="63783-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="63783-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="63783-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="63783-124">Koppelen aan het proces voor het hosten van PowerShell</span><span class="sxs-lookup"><span data-stu-id="63783-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="63783-125">U kunt nu koppelen aan het proces voor elke computer met PowerShell geladen.</span><span class="sxs-lookup"><span data-stu-id="63783-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="63783-126">U doen dit door te voeren in een interactieve sessie met het hostproces.</span><span class="sxs-lookup"><span data-stu-id="63783-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="63783-127">Zie voor meer informatie</span><span class="sxs-lookup"><span data-stu-id="63783-127">For more information, see:</span></span>

- [<span data-ttu-id="63783-128">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="63783-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="63783-129">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="63783-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
