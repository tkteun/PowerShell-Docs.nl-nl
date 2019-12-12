---
title: Visual Studio Code gebruiken voor externe bewerking en foutopsporing
description: Visual Studio Code gebruiken voor externe bewerking en foutopsporing
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67264025"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="10888-103">Visual Studio Code gebruiken voor externe bewerking en foutopsporing</span><span class="sxs-lookup"><span data-stu-id="10888-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="10888-104">Voor degenen die bekend zijn met de ISE, kunt u intrekken dat u `psedit file.ps1` kunt uitvoeren vanuit de geïntegreerde console om bestanden te openen-lokaal of extern-rechts in de ISE.</span><span class="sxs-lookup"><span data-stu-id="10888-104">For those of you that are familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="10888-105">Deze functie is ook beschikbaar in de Power shell-uitbrei ding voor VSCode.</span><span class="sxs-lookup"><span data-stu-id="10888-105">This feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="10888-106">In deze hand leiding wordt uitgelegd hoe u dit kunt doen.</span><span class="sxs-lookup"><span data-stu-id="10888-106">This guide shows you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10888-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="10888-107">Prerequisites</span></span>

<span data-ttu-id="10888-108">In deze hand leiding wordt ervan uitgegaan dat u het volgende hebt:</span><span class="sxs-lookup"><span data-stu-id="10888-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="10888-109">Een externe bron (bijvoorbeeld: een VM, een container) waartoe u toegang hebt</span><span class="sxs-lookup"><span data-stu-id="10888-109">A remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="10888-110">Power shell wordt uitgevoerd op deze computer en de hostmachine</span><span class="sxs-lookup"><span data-stu-id="10888-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="10888-111">VSCode en de Power shell-extensie voor VSCode</span><span class="sxs-lookup"><span data-stu-id="10888-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="10888-112">Deze functie werkt in Windows Power shell en Power shell core.</span><span class="sxs-lookup"><span data-stu-id="10888-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="10888-113">Deze functie werkt ook wanneer u verbinding maakt met een externe computer via WinRM, Power shell direct of SSH.</span><span class="sxs-lookup"><span data-stu-id="10888-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="10888-114">Als u SSH wilt gebruiken, maar Windows gebruikt, raadpleegt u de [Win32-versie van SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="10888-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10888-115">De opdrachten `Open-EditorFile` en `psedit` werken alleen in de **Power shell-geïntegreerde console** die is gemaakt met de Power shell-uitbrei ding voor VSCode.</span><span class="sxs-lookup"><span data-stu-id="10888-115">The `Open-EditorFile` and `psedit` commands only work in the **PowerShell Integrated Console** created by the PowerShell extension for VSCode.</span></span>

## <a name="usage-examples"></a><span data-ttu-id="10888-116">Gebruiks voorbeelden</span><span class="sxs-lookup"><span data-stu-id="10888-116">Usage examples</span></span>

<span data-ttu-id="10888-117">In deze voor beelden ziet u het op afstand bewerken en fout opsporing van een MacBook Pro naar een Ubuntu VM die in azure wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="10888-117">These examples show remote editing and debugging from a MacBook Pro to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="10888-118">Het proces is identiek in Windows.</span><span class="sxs-lookup"><span data-stu-id="10888-118">The process is identical on Windows.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="10888-119">Lokaal bestand bewerken met open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="10888-119">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="10888-120">Met de Power shell-extensie voor VSCode gestart en de Power shell-geïntegreerde console geopend, kunnen we `Open-EditorFile foo.ps1`-of `psedit foo.ps1` om het lokale bestand foo. ps1 rechtstreeks in de editor te openen.</span><span class="sxs-lookup"><span data-stu-id="10888-120">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo. ps1 werkt lokaal](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> <span data-ttu-id="10888-122">De bestands `foo.ps1` moet al bestaan.</span><span class="sxs-lookup"><span data-stu-id="10888-122">The file `foo.ps1` must already exist.</span></span>

<span data-ttu-id="10888-123">Vanaf daar kunnen we het volgende doen:</span><span class="sxs-lookup"><span data-stu-id="10888-123">From there, we can:</span></span>

- <span data-ttu-id="10888-124">Onderbrekings punten toevoegen aan de rugmarge</span><span class="sxs-lookup"><span data-stu-id="10888-124">Add breakpoints to the gutter</span></span>

  ![onderbrekings punt toevoegen aan rugmarge](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- <span data-ttu-id="10888-126">Druk op F5 om fouten op te sporen in het Power shell-script.</span><span class="sxs-lookup"><span data-stu-id="10888-126">Hit F5 to debug the PowerShell script.</span></span>

  ![fout opsporing van het lokale Power shell-script](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

<span data-ttu-id="10888-128">Tijdens het opsporen van fouten kunt u communiceren met de console fout opsporing, de variabelen in het bereik aan de linkerkant bekijken en alle andere standaardfout opsporingsprogramma's.</span><span class="sxs-lookup"><span data-stu-id="10888-128">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="10888-129">Externe bestands bewerking met open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="10888-129">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="10888-130">Nu gaan we externe bestanden bewerken en fouten opsporen.</span><span class="sxs-lookup"><span data-stu-id="10888-130">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="10888-131">De stappen zijn bijna hetzelfde, maar u moet eerst onze Power shell-sessie uitvoeren op de externe server.</span><span class="sxs-lookup"><span data-stu-id="10888-131">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="10888-132">Er is een cmdlet voor om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="10888-132">There's a cmdlet for to do so.</span></span> <span data-ttu-id="10888-133">Het wordt `Enter-PSSession`genoemd.</span><span class="sxs-lookup"><span data-stu-id="10888-133">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="10888-134">De niet-bevochtigde uitleg van de cmdlet is:</span><span class="sxs-lookup"><span data-stu-id="10888-134">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="10888-135">`Enter-PSSession -ComputerName foo` start een sessie via WinRM</span><span class="sxs-lookup"><span data-stu-id="10888-135">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="10888-136">een sessie `Enter-PSSession -ContainerId foo` en `Enter-PSSession -VmId foo` via Power shell direct</span><span class="sxs-lookup"><span data-stu-id="10888-136">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="10888-137">`Enter-PSSession -HostName foo` start een sessie via SSH</span><span class="sxs-lookup"><span data-stu-id="10888-137">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="10888-138">Zie de documentatie voor [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="10888-138">For more information, see the documentation for [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span></span>

<span data-ttu-id="10888-139">Omdat we vanuit macOS naar een Ubuntu-VM in azure gaan, gebruiken we SSH voor externe communicatie.</span><span class="sxs-lookup"><span data-stu-id="10888-139">Since we are going from macOS to an Ubuntu VM in Azure, we are using SSH for remoting.</span></span>

<span data-ttu-id="10888-140">Voer eerst in de geïntegreerde console het `Enter-PSSession`uit.</span><span class="sxs-lookup"><span data-stu-id="10888-140">First, in the Integrated Console, run `Enter-PSSession`.</span></span> <span data-ttu-id="10888-141">U bent verbonden met de externe sessie wanneer `[<hostname>]` links van uw prompt wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="10888-141">You're connected to the remote session when `[<hostname>]` shows up to the left of your prompt.</span></span>

![Het aanroepen van ENTER-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

<span data-ttu-id="10888-143">Nu kunnen we dezelfde stappen uitvoeren als voor het bewerken van een lokaal script.</span><span class="sxs-lookup"><span data-stu-id="10888-143">Now, we can do the same steps as if we are editing a local script.</span></span>

1. <span data-ttu-id="10888-144">Voer `Open-EditorFile test.ps1` of `psedit test.ps1` uit om het externe `test.ps1`-bestand te openen</span><span class="sxs-lookup"><span data-stu-id="10888-144">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file</span></span>

  ![Open-EditorFile het bestand test. ps1](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. <span data-ttu-id="10888-146">Het bestand of de set onderbrekings punten bewerken</span><span class="sxs-lookup"><span data-stu-id="10888-146">Edit the file/set breakpoints</span></span>

   ![onderbrekings punten bewerken en instellen](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. <span data-ttu-id="10888-148">Fout opsporing starten (F5) het externe bestand</span><span class="sxs-lookup"><span data-stu-id="10888-148">Start debugging (F5) the remote file</span></span>

   ![fout opsporing van het externe bestand](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

<span data-ttu-id="10888-150">Als u problemen hebt, kunt u problemen openen in de [github-opslag plaats](https://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="10888-150">If you have any problems, you can open issues in the [GitHub repo](https://github.com/powershell/vscode-powershell).</span></span>
