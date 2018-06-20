---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 9ead27fd5d4f146e9062488c1c8cc22a073b922e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187099"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="378a1-102">Verbeteringen in foutopsporing voor PowerShell-scripts</span><span class="sxs-lookup"><span data-stu-id="378a1-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="378a1-103">Een aantal verbeteringen aangebracht in PowerShell 5.0 om de foutopsporing ervaring te verbeteren:</span><span class="sxs-lookup"><span data-stu-id="378a1-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="378a1-104">Alle opsplitsen</span><span class="sxs-lookup"><span data-stu-id="378a1-104">Break All</span></span>

<span data-ttu-id="378a1-105">De PowerShell-console en de Windows PowerShell ISE kunt u nu onderbreken met foutopsporing voor het uitvoeren van scripts.</span><span class="sxs-lookup"><span data-stu-id="378a1-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="378a1-106">Dit werkt in zowel lokale als externe sessies.</span><span class="sxs-lookup"><span data-stu-id="378a1-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="378a1-107">In de console, drukt u op **Ctrl + Break**.</span><span class="sxs-lookup"><span data-stu-id="378a1-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="378a1-108">In de ISE, drukt u op **Ctrl + B**, of gebruik de **Debug -> alle opsplitsen** menuopdracht.</span><span class="sxs-lookup"><span data-stu-id="378a1-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="378a1-109">Foutopsporing op afstand en extern bestand bewerken in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="378a1-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="378a1-110">Windows PowerShell ISE nu kunt u bestanden openen en bewerken in een externe sessie met de opdracht PSEdit.</span><span class="sxs-lookup"><span data-stu-id="378a1-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="378a1-111">U kunt bijvoorbeeld een bestand vanaf de opdrachtregel bewerken in een externe sessie als volgt openen:</span><span class="sxs-lookup"><span data-stu-id="378a1-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="378a1-112">Bovendien kunt u nu bewerken en opslaan van wijzigingen in een extern bestand dat automatisch wordt geopend in Windows PowerShell ISE wanneer u een onderbrekingspunt.</span><span class="sxs-lookup"><span data-stu-id="378a1-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="378a1-113">Nu kunt u fouten opsporen in een scriptbestand dat wordt uitgevoerd op een externe computer, het bestand bewerken als een fout corrigeren en voer het gewijzigde script.</span><span class="sxs-lookup"><span data-stu-id="378a1-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="378a1-114">Foutopsporing in geavanceerde scripts</span><span class="sxs-lookup"><span data-stu-id="378a1-114">Advanced Script Debugging</span></span>

<span data-ttu-id="378a1-115">Er zijn nieuwe, geavanceerde foutopsporing functies waarmee u kunnen koppelen aan een proces voor lokale computer die Windows PowerShell geladen en willekeurige runspaces in het proces voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="378a1-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="378a1-116">Runspace foutopsporing</span><span class="sxs-lookup"><span data-stu-id="378a1-116">Runspace Debugging</span></span>

<span data-ttu-id="378a1-117">Nieuwe cmdlets er zijn toegevoegd waarmee u een lijst met huidige runspaces in een proces en de Windows PowerShell-console of de ISE-foutopsporingsprogramma koppelen aan die runspace voor foutopsporing in scripts kunt:</span><span class="sxs-lookup"><span data-stu-id="378a1-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="378a1-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="378a1-118">Get-Runspace</span></span>
-   <span data-ttu-id="378a1-119">Foutopsporing Runspace</span><span class="sxs-lookup"><span data-stu-id="378a1-119">Debug-Runspace</span></span>
-   <span data-ttu-id="378a1-120">Schakel RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="378a1-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="378a1-121">Schakel RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="378a1-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="378a1-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="378a1-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="378a1-123">Koppelen aan een proces voor het hosten van PowerShell</span><span class="sxs-lookup"><span data-stu-id="378a1-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="378a1-124">U kunt nu koppelen aan het proces voor elke computer met Windows PowerShell geladen.</span><span class="sxs-lookup"><span data-stu-id="378a1-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="378a1-125">U doen dit door te voeren in een interactieve sessie met het proces, net zoals bij hoe u in een interactieve externe sessie invoeren door de Enter-PSSession cmdlet:</span><span class="sxs-lookup"><span data-stu-id="378a1-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="378a1-126">Voer PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="378a1-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="378a1-127">Exit PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="378a1-127">Exit-PSHostProcess</span></span>
